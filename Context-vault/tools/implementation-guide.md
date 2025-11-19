# Material Design 3 Implementation Guide

This guide provides step-by-step instructions for implementing the Material Design 3 system in your projects.

## Quick Start

### 1. Include the Design System

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My App</title>
  
  <!-- Material Design 3 Tokens -->
  <link rel="stylesheet" href="path/to/tokens/colors.css">
  <link rel="stylesheet" href="path/to/tokens/typography.css">
  <link rel="stylesheet" href="path/to/tokens/layout.css">
  
  <!-- Material Design 3 Components -->
  <link rel="stylesheet" href="path/to/components/buttons.css">
  <link rel="stylesheet" href="path/to/components/navigation.css">
  <link rel="stylesheet" href="path/to/components/forms.css">
  <link rel="stylesheet" href="path/to/components/cards-lists.css">
  
  <!-- Layout Patterns -->
  <link rel="stylesheet" href="path/to/patterns/layouts.css">
  
  <!-- Motion System -->
  <link rel="stylesheet" href="path/to/motion/animations.css">
</head>
<body>
  <!-- Your content here -->
</body>
</html>
```

### 2. Basic Page Structure

```html
<body class="md-layout">
  <!-- App Bar -->
  <header class="md-top-app-bar">
    <h1 class="md-top-app-bar__title">My Application</h1>
  </header>

  <!-- Main Content -->
  <main class="md-layout__container">
    <!-- Your content -->
  </main>

  <!-- FAB (optional) -->
  <button class="md-fab" style="position: fixed; bottom: 16px; right: 16px;">
    <svg class="md-fab__icon"><!-- Add icon --></svg>
  </button>
</body>
```

## Component Usage

### Buttons

```html
<!-- Primary Actions -->
<button class="md-button md-button--filled">Save</button>
<button class="md-button md-button--filled-tonal">Save Draft</button>

<!-- Secondary Actions -->
<button class="md-button md-button--outlined">Cancel</button>
<button class="md-button md-button--text">Skip</button>

<!-- With Icons -->
<button class="md-button md-button--filled md-button--icon">
  <svg class="md-button__icon md-button__icon--leading">...</svg>
  Add Item
</button>

<!-- Icon Buttons -->
<button class="md-icon-button" aria-label="More options">
  <svg class="md-icon-button__icon">...</svg>
</button>

<!-- Floating Action Button -->
<button class="md-fab">
  <svg class="md-fab__icon">...</svg>
</button>
```

### Cards

```html
<!-- Basic Card -->
<div class="md-card md-card--elevated">
  <div class="md-card__content">
    <h3 class="md-card__title">Card Title</h3>
    <p class="md-card__supporting-text">Card content goes here.</p>
  </div>
  <div class="md-card__actions">
    <button class="md-button md-button--text">Action</button>
  </div>
</div>

<!-- Card with Media -->
<div class="md-card md-card--filled">
  <img src="image.jpg" class="md-card__media" alt="Description">
  <div class="md-card__content">
    <h3 class="md-card__title">Media Card</h3>
    <h4 class="md-card__subtitle">Subtitle</h4>
    <p class="md-card__supporting-text">Description text.</p>
  </div>
</div>
```

### Forms

```html
<!-- Text Fields -->
<div class="md-text-field md-text-field--outlined">
  <input type="text" class="md-text-field__input" id="name" placeholder=" ">
  <label class="md-text-field__label" for="name">Name</label>
  <span class="md-text-field__supporting-text">Enter your full name</span>
</div>

<!-- Checkboxes -->
<div class="md-form-field">
  <div class="md-checkbox">
    <input type="checkbox" class="md-checkbox__input" id="agree">
    <div class="md-checkbox__background"></div>
    <svg class="md-checkbox__checkmark">...</svg>
  </div>
  <label class="md-form-field__label" for="agree">I agree to the terms</label>
</div>

<!-- Radio Buttons -->
<div class="md-form-field">
  <div class="md-radio">
    <input type="radio" class="md-radio__input" name="option" id="option1">
    <div class="md-radio__background"></div>
    <div class="md-radio__inner-circle"></div>
  </div>
  <label class="md-form-field__label" for="option1">Option 1</label>
</div>
```

### Navigation

```html
<!-- Top App Bar -->
<header class="md-top-app-bar">
  <button class="md-icon-button">
    <svg class="md-icon-button__icon"><!-- Menu icon --></svg>
  </button>
  <h1 class="md-top-app-bar__title">Page Title</h1>
  <div class="md-top-app-bar__trailing">
    <button class="md-icon-button">
      <svg class="md-icon-button__icon"><!-- Action icon --></svg>
    </button>
  </div>
</header>

<!-- Bottom Navigation -->
<nav class="md-bottom-navigation">
  <a href="/home" class="md-bottom-navigation__item md-bottom-navigation__item--active">
    <svg class="md-bottom-navigation__icon">...</svg>
    <span class="md-bottom-navigation__label">Home</span>
  </a>
  <a href="/search" class="md-bottom-navigation__item">
    <svg class="md-bottom-navigation__icon">...</svg>
    <span class="md-bottom-navigation__label">Search</span>
  </a>
</nav>
```

### Lists

```html
<ul class="md-list">
  <!-- One-line item -->
  <li class="md-list-item">
    <div class="md-list-item__leading">
      <svg class="md-list-item__icon">...</svg>
    </div>
    <div class="md-list-item__content">
      <div class="md-list-item__text">Item text</div>
    </div>
  </li>

  <!-- Two-line item -->
  <li class="md-list-item md-list-item--two-line">
    <div class="md-list-item__leading">
      <div class="md-list-item__avatar">A</div>
    </div>
    <div class="md-list-item__content">
      <div class="md-list-item__text">Primary text</div>
      <div class="md-list-item__supporting-text">Secondary text</div>
    </div>
    <div class="md-list-item__trailing">
      <button class="md-icon-button">
        <svg class="md-icon-button__icon">...</svg>
      </button>
    </div>
  </li>
</ul>
```

## Layout Patterns

### Supporting Panel Layout

```html
<div class="md-layout md-layout--supporting-panel">
  <header class="md-layout__header">
    <!-- Top app bar -->
  </header>
  
  <nav class="md-layout__navigation-rail">
    <!-- Navigation rail for medium screens -->
  </nav>
  
  <nav class="md-layout__navigation-drawer">
    <!-- Navigation drawer for large screens -->
  </nav>
  
  <main class="md-layout__main">
    <!-- Main content -->
  </main>
  
  <aside class="md-layout__panel">
    <!-- Supporting panel -->
  </aside>
  
  <nav class="md-layout__navigation">
    <!-- Bottom navigation for small screens -->
  </nav>
</div>
```

### List-Detail Layout

```html
<div class="md-layout md-layout--list-detail">
  <header class="md-layout__header">
    <!-- Top app bar -->
  </header>
  
  <nav class="md-layout__navigation-rail">
    <!-- Navigation rail -->
  </nav>
  
  <div class="md-layout__list">
    <!-- List of items -->
  </div>
  
  <main class="md-layout__detail">
    <!-- Detail view -->
  </main>
</div>
```

## Theming

### Custom Colors

```css
:root {
  /* Override primary color */
  --md-ref-palette-primary40: #your-brand-color;
  --md-ref-palette-primary80: #your-brand-color-light;
  --md-ref-palette-primary90: #your-brand-color-very-light;
  --md-ref-palette-primary10: #your-brand-color-dark;
  
  /* Or override system colors directly */
  --md-sys-color-primary: #your-brand-color;
  --md-sys-color-primary-container: #your-brand-container-color;
}
```

### Dark Theme Implementation

```javascript
// Theme toggle functionality
function setTheme(theme) {
  document.documentElement.setAttribute('data-theme', theme);
  localStorage.setItem('theme', theme);
}

function initTheme() {
  const savedTheme = localStorage.getItem('theme');
  const systemTheme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
  const theme = savedTheme || systemTheme;
  setTheme(theme);
}

// Initialize on page load
initTheme();

// Listen for system theme changes
window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (e) => {
  if (!localStorage.getItem('theme')) {
    setTheme(e.matches ? 'dark' : 'light');
  }
});
```

## Responsive Behavior

### Breakpoint-based Components

```css
/* Show different navigation based on screen size */
@media (max-width: 599px) {
  .md-navigation-rail { display: none; }
  .md-bottom-navigation { display: flex; }
}

@media (min-width: 600px) and (max-width: 839px) {
  .md-navigation-rail { display: flex; }
  .md-bottom-navigation { display: none; }
}

@media (min-width: 840px) {
  .md-navigation-drawer { position: static; }
  .md-navigation-rail { display: none; }
  .md-bottom-navigation { display: none; }
}
```

### Adaptive Grid

```html
<div class="md-grid">
  <div class="md-col-4 md-col-medium-8 md-col-expanded-6">
    <!-- Responsive column -->
  </div>
</div>
```

## Animation and Motion

### Basic Transitions

```css
/* Add smooth transitions to interactive elements */
.my-component {
  transition: all var(--md-sys-motion-duration-short3) var(--md-sys-motion-easing-standard);
}

/* Use motion classes for common animations */
.fade-in {
  animation: md-fade-in-up var(--md-sys-motion-duration-medium2) var(--md-sys-motion-easing-standard);
}
```

### Staggered Animations

```html
<div class="md-stagger-container">
  <div class="md-stagger-item">Item 1</div>
  <div class="md-stagger-item">Item 2</div>
  <div class="md-stagger-item">Item 3</div>
</div>
```

## Accessibility Best Practices

### Focus Management

```html
<!-- Ensure proper focus indicators -->
<button class="md-button md-focus-ring">Button with focus ring</button>

<!-- Provide descriptive labels -->
<button class="md-icon-button" aria-label="Delete item">
  <svg class="md-icon-button__icon">...</svg>
</button>
```

### Screen Reader Support

```html
<!-- Use semantic HTML -->
<main role="main" aria-labelledby="main-title">
  <h1 id="main-title">Page Title</h1>
</main>

<!-- Announce dynamic content -->
<div aria-live="polite" id="status-messages" class="md-sr-only"></div>

<!-- Describe form fields properly -->
<input type="email" 
       id="email"
       aria-describedby="email-help email-error"
       aria-invalid="false">
<div id="email-help">We'll use this to send you updates</div>
<div id="email-error" role="alert"></div>
```

## Performance Optimization

### Selective Loading

```html
<!-- Load only needed components -->
<link rel="stylesheet" href="tokens/colors.css">
<link rel="stylesheet" href="tokens/typography.css">
<link rel="stylesheet" href="components/buttons.css">
<!-- Don't load unnecessary components -->
```

### Critical CSS

```html
<!-- Inline critical styles -->
<style>
  /* Critical above-the-fold styles */
  :root { --md-sys-color-primary: #6750A4; }
  .md-button { /* essential button styles */ }
</style>

<!-- Load non-critical styles asynchronously -->
<link rel="preload" href="components/cards.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
```

## Browser Support

- **Modern browsers**: Full support for all features
- **IE 11**: Limited support (requires polyfills for CSS custom properties)
- **Safari 12+**: Full support
- **Chrome 60+**: Full support
- **Firefox 55+**: Full support

### Polyfills

```html
<!-- For older browsers -->
<script src="https://polyfill.io/v3/polyfill.min.js?features=css-custom-properties%2CIntersectionObserver"></script>
```

## Common Patterns

### Modal Dialog

```html
<div class="md-dialog" role="dialog" aria-modal="true">
  <div class="md-dialog__scrim"></div>
  <div class="md-dialog__container">
    <div class="md-dialog__content">
      <!-- Dialog content -->
    </div>
  </div>
</div>
```

### Loading States

```html
<!-- Button loading state -->
<button class="md-button md-button--filled" disabled>
  <div class="md-loading-spinner"></div>
  Loading...
</button>

<!-- Card loading state -->
<div class="md-card md-card--loading">
  <!-- Card content with shimmer effect -->
</div>
```

### Error States

```html
<!-- Form error state -->
<div class="md-text-field md-text-field--error">
  <input type="email" class="md-text-field__input" aria-invalid="true">
  <label class="md-text-field__label">Email</label>
  <span class="md-text-field__supporting-text md-text-field__error-text" role="alert">
    Please enter a valid email address
  </span>
</div>
```

## Tools and Resources

### Development Tools
- Browser DevTools for inspecting components
- Accessibility testing tools (axe, WAVE)
- Color contrast analyzers
- Responsive design testing

### Design Resources
- Material Design 3 Figma kit
- Icon libraries (Material Symbols)
- Color palette generators
- Typography scale calculators

## Troubleshooting

### Common Issues

**Components not styling correctly:**
- Check CSS import order
- Verify class names match exactly
- Ensure no conflicting styles

**Dark theme not working:**
- Check `data-theme` attribute is set
- Verify color tokens are properly defined
- Test media query for `prefers-color-scheme`

**Responsive layout issues:**
- Verify viewport meta tag
- Check breakpoint CSS is included
- Test on actual devices

**Accessibility issues:**
- Use proper semantic HTML
- Test with keyboard navigation
- Verify screen reader announcements
- Check color contrast ratios