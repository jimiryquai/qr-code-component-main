# Building a QR Code Component: Lessons in Modern CSS and Flexbox

## Introduction

After years away from CSS, I decided to jump back in with a Frontend Mentor challenge - building a QR code component. What seemed like a simple card layout turned into a valuable learning experience about modern CSS practices, flexbox layouts, and the importance of systematic approaches.

## The Challenge

The task was straightforward: create a responsive QR code component with:
- A card with rounded corners and shadow
- A QR code image
- Heading and body text
- An attribution footer
- Specific colors and typography from a style guide

## What I'm Most Proud Of

### 1. CSS Custom Properties System
I started by creating a comprehensive token system:

```css
:root {
  /* Colors */
  --color-slate-300: hsl(212.3, 44.8%, 88.6%);
  --color-slate-500: hsl(216, 15%, 48%);
  --color-slate-900: hsl(232.5, 43.6%, 21.6%);

  /* Typography */
  --font-family: "Outfit", sans-serif;
  --font-size-body: 1rem;
  --font-size-heading: 1.375rem;

  /* Spacing */
  --spacing-200: 1rem;
  --spacing-300: 1.5rem;
  --spacing-500: 2.5rem;
}
```

This made the entire project maintainable and scalable from day one.

### 2. BEM Naming Conventions
Following BEM methodology kept my CSS organized:
- `.card` - The block
- `.card__heading` - Elements within the card
- `.card__body-text` - Descriptive and clear

### 3. Minimal Modern CSS Reset
Instead of using a heavy reset library, I created a minimal one:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0;
}

img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
```

### 4. Accessibility
Added proper ARIA labels to the SVG QR code:
```html
<svg role="img" aria-label="QR code">
```

## Challenges and Solutions

### Challenge 1: Font Import Errors
**Problem:** Got MIME type errors trying to import fonts from node_modules:
```
Refused to apply style from 'http://127.0.0.1:5500/@fontsource/outfit/400.css'
because its MIME type ('text/html') is not a supported stylesheet MIME type
```

**Solution:** Switched to Google Fonts CDN - much simpler for static sites:
```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;700&display=swap');
```

### Challenge 2: Color Values Confusion
**Problem:** Background appeared transparent instead of light gray.

**Solution:** Discovered I had swapped the color values! The style guide's "Slate 300" was the lightest color, not the darkest. Always double-check naming conventions against actual values.

### Challenge 3: The Flexbox Layout Puzzle
This was the biggest learning experience. I needed:
- Card centered on screen
- Attribution at the bottom
- Proper spacing between them

## Understanding Flexbox: A Beginner's Guide

Here's what finally worked and why:

### The HTML Structure
```html
<body>
  <main class="main">
    <div class="card">
      <!-- card content -->
    </div>
  </main>
  <div class="attribution">
    <!-- attribution -->
  </div>
</body>
```

### The CSS Magic

#### Step 1: Body as Flex Container
```css
body {
  min-height: 100vh;      /* Full screen height */
  display: flex;          /* Enable flexbox */
  flex-direction: column; /* Stack children vertically */
  align-items: center;    /* Center horizontally */
}
```

Think of the body as a tall box that holds everything:
- `100vh` = 100% of viewport height
- `display: flex` = Children can be positioned smartly
- `flex-direction: column` = Stack like paragraphs

#### Step 2: Main Takes Available Space
```css
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;  /* The magic property! */
}
```

`flex: 1` tells the main element to grow and fill all available space. It's like a sandwich filling that expands!

#### Step 3: Attribution Sticks to Bottom (CUBE CSS Approach)

Initially, I put `margin-top: auto` directly on the `.attribution` class. But following CUBE CSS principles, layout should be handled by composition utilities, not components:

```css
/* Composition layer - Layout utilities */
.push-last > :last-child {
  margin-top: auto;
}

/* Block layer - Component styling only */
.attribution {
  font-size: 0.75rem;
  text-align: center;
}
```

Then in HTML:
```html
<body class="push-last">
```

This separation means:
- The `.push-last` utility handles layout (Composition layer)
- The `.attribution` only handles its appearance (Block layer)
- If we replace the attribution, the layout still works
- Components don't dictate their own spacing

`margin-top: auto` means "put ALL available margin above me."

### Visual Representation
```
┌─────────────────────┐
│      body (100vh)   │
│ ┌─────────────────┐ │
│ │   main (flex:1) │ │ ← Expands to fill
│ │   ┌─────────┐   │ │
│ │   │  card   │   │ │ ← Centered in main
│ │   └─────────┘   │ │
│ └─────────────────┘ │
│ ┌─────────────────┐ │
│ │   attribution   │ │ ← Pushed to bottom
│ └─────────────────┘ │
└─────────────────────┘
```

## What I Would Do Differently

1. **Start with the style guide** - I initially guessed at colors instead of checking the provided values
2. **Plan the layout first** - Sketching the flexbox structure would have saved debugging time
3. **Test font imports early** - Would have caught the node_modules issue sooner
4. **Use CSS Grid** - For this layout, Grid might be even cleaner than Flexbox

## Key Takeaways

1. **CSS Custom Properties are powerful** - They make maintenance and consistency much easier
2. **Flexbox isn't scary** - Once you understand `flex: 1` and auto margins, complex layouts become simple
3. **Check your assumptions** - My color naming issue was a simple misunderstanding that caused confusion
4. **Modern CSS is forgiving** - You don't need massive resets or complex frameworks for clean layouts
5. **Accessibility matters** - Small additions like ARIA labels make a big difference
6. **CUBE CSS principles improve code** - Separating composition (layout) from blocks (components) creates more maintainable, reusable CSS

## Conclusion

What started as a simple component challenge became a comprehensive review of modern CSS practices. The combination of custom properties, flexbox, and semantic HTML creates maintainable, accessible components.

The biggest lesson? When returning to CSS after time away, start with the fundamentals. Understanding core concepts like flexbox deeply is more valuable than knowing every new feature.

## Resources
- [Frontend Mentor Challenge](https://www.frontendmentor.io)
- [CSS Custom Properties Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [BEM Methodology](http://getbem.com/)

---

*This project reminded me that the best way to learn is by building, making mistakes, and understanding why things work the way they do.*