# Frontend Mentor - QR code component solution

This is a solution to the [QR code component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/qr-code-component-iux_sIO_H). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### Screenshot

![QR Code Component Screenshot](./preview.jpg)

### Links

- Solution URL: [GitHub Repository](https://github.com/jimiryquai/qr-code-component-main)
- Live Site URL: [GitHub Pages](https://jimiryquai.github.io/qr-code-component-main/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow
- BEM naming convention
- CUBE CSS principles

### What I learned

This project was a valuable learning experience in modern CSS practices. Here are the key takeaways:

1. **CSS Custom Properties Organization** - Created a comprehensive token system for colors, typography, and spacing:

```css
:root {
  /* Colors */
  --color-slate-300: hsl(212.3, 44.8%, 88.6%);
  --color-slate-500: hsl(216, 15%, 48%);
  --color-slate-900: hsl(232.5, 43.6%, 21.6%);
}
```

2. **Flexbox Layout with CUBE CSS** - Learned how to properly center content while keeping footer at bottom:

```css
/* Composition layer - Layout utilities */
.push-last > :last-child {
  margin-top: auto;
}

.main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1;
}
```

3. **Accessibility** - Added proper ARIA labels to SVG elements:

```html
<svg role="img" aria-label="QR code">
```

### Continued development

Areas I want to focus on in future projects:

- CSS Grid for more complex layouts
- Advanced custom property patterns (calculated values, fallbacks)
- Performance optimization for images and fonts
- More sophisticated responsive design patterns

### Useful resources

- [Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) - Essential for understanding flexbox behaviors
- [CUBE CSS](https://cube.fyi/) - Helped me think about CSS architecture differently
- [BEM Methodology](http://getbem.com/) - For consistent naming conventions
- [MDN Web Docs](https://developer.mozilla.org/) - Always helpful for CSS property details

## Author

- Frontend Mentor - [@jimiryquai](https://www.frontendmentor.io/profile/jimiryquai)
- GitHub - [@jimiryquai](https://github.com/jimiryquai)