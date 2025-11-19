# Material Design 3 - Accessibility Guidelines

This document outlines comprehensive accessibility standards and implementation guidelines for the Material Design 3 system, ensuring WCAG 2.1 AA compliance and inclusive design practices.

## Table of Contents

1. [Core Principles](#core-principles)
2. [Color and Contrast](#color-and-contrast)
3. [Typography and Readability](#typography-and-readability)
4. [Focus Management](#focus-management)
5. [Keyboard Navigation](#keyboard-navigation)
6. [Screen Reader Support](#screen-reader-support)
7. [Touch Targets](#touch-targets)
8. [Motion and Animation](#motion-and-animation)
9. [Component-Specific Guidelines](#component-specific-guidelines)
10. [Testing and Validation](#testing-and-validation)

## Core Principles

### 1. Perceivable
- Information must be presentable in ways users can perceive
- Provide text alternatives for images
- Ensure sufficient color contrast
- Support text scaling up to 200%

### 2. Operable
- Interface components must be operable by all users
- Make all functionality keyboard accessible
- Provide users enough time to read content
- Design content that doesn't cause seizures

### 3. Understandable
- Information and UI operation must be understandable
- Make text readable and understandable
- Make content appear and operate predictably
- Help users avoid and correct mistakes

### 4. Robust
- Content must be robust enough for various assistive technologies
- Maximize compatibility with screen readers
- Follow semantic HTML practices
- Ensure graceful degradation

## Color and Contrast

### Contrast Requirements
- **Normal text**: Minimum 4.5:1 contrast ratio
- **Large text** (18pt/14pt bold+): Minimum 3:1 contrast ratio
- **Graphics and UI components**: Minimum 3:1 contrast ratio
- **Non-text elements**: Minimum 3:1 for meaningful graphics

### Implementation
```css
/* High contrast mode support */
@media (prefers-contrast: high) {
  .md-button {
    border-width: 2px;
    font-weight: 600;
  }
  
  .md-text-field {
    border-width: 2px;
  }
}

/* Ensure focus indicators are visible */
.md-focus-visible {
  outline: 3px solid var(--md-sys-color-primary);
  outline-offset: 2px;
}
```

### Color Independence
- Never rely solely on color to convey information
- Use icons, text labels, or patterns alongside color
- Provide alternative indicators for status/states

## Typography and Readability

### Font Guidelines
- **Minimum font size**: 12px (0.75rem) for body text
- **Recommended body size**: 16px (1rem)
- **Line height**: Minimum 1.5x font size
- **Character spacing**: Default or slightly increased
- **Line length**: 45-75 characters per line

### Text Scaling Support
```css
/* Support for user font size preferences */
@media (min-resolution: 1.5dppx) {
  body {
    font-size: calc(1rem + 0.1vw);
  }
}

/* Ensure text scales properly */
.md-typescale-body-large {
  font-size: clamp(1rem, 2.5vw, 1.125rem);
}
```

### Language Support
- Support for right-to-left (RTL) languages
- Proper line breaking for different scripts
- Cultural considerations for spacing and layout

## Focus Management

### Focus Indicators
- Must be visible with minimum 3:1 contrast
- Should clearly outline the focused element
- Must not be hidden by other elements

### Focus Order
- Logical tab sequence following content flow
- Skip links for main content navigation
- Focus traps in modal dialogs

```css
/* Focus indicator styles */
.md-focus-ring {
  outline: none;
  position: relative;
}

.md-focus-ring:focus-visible::after {
  content: '';
  position: absolute;
  inset: -2px;
  border: 2px solid var(--md-sys-color-primary);
  border-radius: inherit;
  pointer-events: none;
}
```

## Keyboard Navigation

### Essential Patterns
- **Tab**: Move forward through interactive elements
- **Shift+Tab**: Move backward through interactive elements
- **Enter/Space**: Activate buttons and links
- **Arrow keys**: Navigate within components (lists, menus)
- **Escape**: Close dialogs, menus, or cancel operations
- **Home/End**: Jump to first/last items in lists

### Component-Specific Navigation
- **Tabs**: Arrow keys for tab selection, Enter/Space to activate
- **Menus**: Arrow keys for navigation, Enter to select, Escape to close
- **Lists**: Arrow keys or Tab for navigation
- **Forms**: Tab between fields, arrow keys for radio groups

## Screen Reader Support

### Semantic HTML
```html
<!-- Use proper heading hierarchy -->
<h1>Page Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>

<!-- Use lists for related items -->
<ul role="list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<!-- Use buttons for actions, links for navigation -->
<button type="button" aria-label="Close dialog">×</button>
<a href="/page" aria-label="Learn more about our products">Learn more</a>
```

### ARIA Labels and Descriptions
```html
<!-- Descriptive labels -->
<input type="email" 
       id="email" 
       aria-label="Email address"
       aria-describedby="email-help"
       required>
<div id="email-help">We'll use this to send you important updates</div>

<!-- State announcements -->
<button aria-expanded="false" 
        aria-controls="menu-1"
        aria-haspopup="true">
  Menu
</button>

<!-- Progress indicators -->
<div role="progressbar" 
     aria-label="Upload progress" 
     aria-valuenow="25" 
     aria-valuemin="0" 
     aria-valuemax="100">
  25% complete
</div>
```

### Live Regions
```html
<!-- Status updates -->
<div aria-live="polite" id="status-messages" class="md-sr-only"></div>

<!-- Error messages -->
<div aria-live="assertive" id="error-messages" class="md-sr-only"></div>

<!-- Dynamic content updates -->
<div aria-live="polite" aria-atomic="true" id="search-results">
  <!-- Results populated dynamically -->
</div>
```

## Touch Targets

### Minimum Sizes
- **Touch targets**: Minimum 48x48px (44x44px on iOS)
- **Spacing**: Minimum 8px between adjacent targets
- **Dense layouts**: Minimum 40x40px with 8px spacing

### Implementation
```css
/* Ensure minimum touch target size */
.md-button,
.md-icon-button,
.md-checkbox,
.md-radio {
  min-width: 48px;
  min-height: 48px;
}

/* Add safe spacing between targets */
.md-button-group .md-button:not(:last-child) {
  margin-right: 8px;
}
```

## Motion and Animation

### Reduced Motion Support
```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Safe Animation Guidelines
- Avoid flashing content (no more than 3 flashes per second)
- Provide pause controls for auto-playing content
- Ensure essential information isn't conveyed through motion alone
- Use animation to enhance, not replace, static content

## Component-Specific Guidelines

### Buttons
```html
<!-- Standard button -->
<button class="md-button md-button--filled" type="button">
  Save Changes
</button>

<!-- Icon button with accessible name -->
<button class="md-icon-button" 
        type="button"
        aria-label="Add to favorites">
  <svg class="md-icon" aria-hidden="true">
    <use href="#icon-heart"></use>
  </svg>
</button>

<!-- Toggle button -->
<button class="md-button md-button--outlined" 
        type="button"
        aria-pressed="false"
        aria-label="Bold text">
  <strong>B</strong>
</button>
```

### Forms
```html
<!-- Text field with proper labeling -->
<div class="md-text-field">
  <input type="text" 
         id="full-name"
         class="md-text-field__input"
         aria-describedby="name-help"
         required>
  <label for="full-name" class="md-text-field__label">
    Full Name
  </label>
  <div id="name-help" class="md-text-field__supporting-text">
    Enter your first and last name
  </div>
</div>

<!-- Error state -->
<div class="md-text-field md-text-field--error">
  <input type="email" 
         id="email"
         class="md-text-field__input"
         aria-describedby="email-error"
         aria-invalid="true"
         value="invalid-email">
  <label for="email" class="md-text-field__label">
    Email Address
  </label>
  <div id="email-error" 
       class="md-text-field__supporting-text md-text-field__error-text"
       role="alert">
    Please enter a valid email address
  </div>
</div>
```

### Navigation
```html
<!-- App bar with proper heading structure -->
<header class="md-top-app-bar" role="banner">
  <button class="md-icon-button" 
          type="button"
          aria-label="Open navigation menu"
          aria-expanded="false"
          aria-controls="nav-menu">
    <svg class="md-icon" aria-hidden="true">
      <use href="#icon-menu"></use>
    </svg>
  </button>
  <h1 class="md-top-app-bar__title">Page Title</h1>
</header>

<!-- Navigation with proper semantics -->
<nav class="md-navigation-drawer" 
     id="nav-menu"
     role="navigation"
     aria-label="Main navigation">
  <ul class="md-list" role="list">
    <li>
      <a href="/home" 
         class="md-navigation-drawer__item"
         aria-current="page">
        <svg class="md-icon" aria-hidden="true">
          <use href="#icon-home"></use>
        </svg>
        <span>Home</span>
      </a>
    </li>
    <!-- More nav items -->
  </ul>
</nav>
```

### Dialogs
```html
<!-- Modal dialog -->
<div class="md-dialog" 
     role="dialog" 
     aria-modal="true"
     aria-labelledby="dialog-title"
     aria-describedby="dialog-content">
  <div class="md-dialog__container">
    <h2 id="dialog-title" class="md-dialog__title">
      Confirm Delete
    </h2>
    <div id="dialog-content" class="md-dialog__content">
      <p>Are you sure you want to delete this item? This action cannot be undone.</p>
    </div>
    <div class="md-dialog__actions">
      <button class="md-button md-button--text" type="button">
        Cancel
      </button>
      <button class="md-button md-button--filled" type="button">
        Delete
      </button>
    </div>
  </div>
</div>
```

## Testing and Validation

### Automated Testing Tools
- **Wave**: Web accessibility evaluation
- **axe**: Automated accessibility testing
- **Lighthouse**: Built-in Chrome accessibility audit
- **Pa11y**: Command-line accessibility testing

### Manual Testing
1. **Keyboard navigation**: Test all interactions using only keyboard
2. **Screen reader**: Test with NVDA, JAWS, or VoiceOver
3. **High contrast mode**: Test in Windows High Contrast mode
4. **Color blindness**: Test with color blindness simulators
5. **Zoom**: Test at 200% and 400% zoom levels

### Testing Checklist
- [ ] All interactive elements are keyboard accessible
- [ ] Focus indicators are visible and clear
- [ ] Color contrast meets WCAG AA standards
- [ ] All images have appropriate alt text
- [ ] Form fields have proper labels and error messages
- [ ] Headings create logical document structure
- [ ] Screen reader announces all important information
- [ ] Motion respects reduced motion preferences
- [ ] Touch targets meet minimum size requirements
- [ ] Error messages are descriptive and helpful

### Accessibility Statement Template
```markdown
## Accessibility Statement

We are committed to ensuring digital accessibility for people with disabilities. 
We are continually improving the user experience for everyone and applying the 
relevant accessibility standards.

### Conformance Status
This website aims to conform to WCAG 2.1 AA standards.

### Feedback
We welcome your feedback on the accessibility of this site. If you encounter 
any accessibility barriers, please contact us at [accessibility@company.com].
```

## Resources and References

### Specifications
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
- [Material Design Accessibility](https://m3.material.io/foundations/accessible-design)

### Testing Tools
- [Wave Web Accessibility Evaluator](https://wave.webaim.org/)
- [axe DevTools](https://www.deque.com/axe/devtools/)
- [Colour Contrast Analyser](https://www.tpgi.com/color-contrast-checker/)

### Screen Readers
- [NVDA](https://www.nvaccess.org/) (Windows)
- [JAWS](https://www.freedomscientific.com/products/software/jaws/) (Windows)
- [VoiceOver](https://www.apple.com/accessibility/vision/) (macOS/iOS)
- [Orca](https://wiki.gnome.org/Projects/Orca) (Linux)