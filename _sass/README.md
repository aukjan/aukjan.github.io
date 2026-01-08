# Design System Documentation

## Overview

This design system provides a modern, maintainable CSS foundation for the site using CSS custom properties (design tokens). It replaces the dated Lanyon/Poole theme with a token-based approach that's both flexible and consistent.

**Philosophy:** Professional but approachable - warm and inviting while maintaining executive credibility.

## Architecture

The CSS is organized into modular Sass partials:

```
_sass/
├── _reset.scss      # Modern CSS reset for browser consistency
├── _tokens.scss     # Design tokens (CSS custom properties)
├── _typography.scss # Typography system (fonts, hierarchy)
└── _base.scss       # Base HTML element styles

assets/css/
└── main.scss        # Main entry point (imports all partials)
```

## Design Tokens

Design tokens are CSS custom properties defined in `_tokens.scss` and available globally via the `:root` selector.

### Usage

```scss
/* Use tokens in your CSS */
.element {
  color: var(--color-text);
  padding: var(--space-md);
  font-family: var(--font-sans);
}
```

### Color Palette

**Primary Colors** - Professional warmth
- `--color-primary: #2563eb` - Confident blue for links and actions
- `--color-primary-dark: #1e40af` - Darker shade for hover states
- `--color-primary-light: #60a5fa` - Lighter shade for backgrounds

**Neutral Colors** - Warm earth tones (not corporate gray)
- `--color-text: #292524` - Main body text (stone-800)
- `--color-text-light: #57534e` - Secondary text (stone-600)
- `--color-text-muted: #78716c` - Muted text (stone-500)
- `--color-background: #fafaf9` - Page background (stone-50)
- `--color-surface: #ffffff` - Card/surface backgrounds
- `--color-border: #e7e5e4` - Borders and dividers (stone-200)

**Accent Colors** - Subtle personality
- `--color-accent: #f59e0b` - Amber for highlights
- `--color-success: #059669` - Emerald for success states
- `--color-muted: #a8a29e` - Muted elements (stone-400)

**Accessibility:** All color combinations meet WCAG 2.1 Level AA standards (4.5:1+ contrast). See `.planning/phases/02-design-system-architecture/WCAG-CONTRAST-VERIFICATION.md` for details.

### Typography Scale

**Font Families**
- `--font-sans: 'Montserrat', system-ui, -apple-system, sans-serif`
- `--font-serif: 'Merriweather', Georgia, serif`
- `--font-mono: 'Courier New', monospace`

**Font Sizes** (fluid scale based on 16px root)
- `--text-xs: 0.75rem` (12px)
- `--text-sm: 0.875rem` (14px)
- `--text-base: 1rem` (16px)
- `--text-lg: 1.125rem` (18px)
- `--text-xl: 1.25rem` (20px)
- `--text-2xl: 1.5rem` (24px)
- `--text-3xl: 1.875rem` (30px)
- `--text-4xl: 2.25rem` (36px)
- `--text-5xl: 3rem` (48px)

**Font Weights**
- `--font-normal: 400`
- `--font-medium: 500`
- `--font-semibold: 600`
- `--font-bold: 700`

**Line Heights**
- `--leading-none: 1`
- `--leading-tight: 1.25` (headings)
- `--leading-snug: 1.375`
- `--leading-normal: 1.5`
- `--leading-relaxed: 1.625` (body text)
- `--leading-loose: 2`

### Spacing Scale

Consistent spacing rhythm based on 8px increments:
- `--space-xs: 0.5rem` (8px)
- `--space-sm: 1rem` (16px)
- `--space-md: 1.5rem` (24px)
- `--space-lg: 2rem` (32px)
- `--space-xl: 3rem` (48px)
- `--space-2xl: 4rem` (64px)
- `--space-3xl: 6rem` (96px)

### Layout Containers

Responsive breakpoints:
- `--container-sm: 640px`
- `--container-md: 768px`
- `--container-lg: 1024px`
- `--container-xl: 1280px`

### Border Radius

- `--radius-sm: 0.25rem` (4px)
- `--radius-md: 0.5rem` (8px)
- `--radius-lg: 0.75rem` (12px)
- `--radius-xl: 1rem` (16px)

### Shadows

Subtle depth for elevation:
- `--shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05)`
- `--shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1)`
- `--shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1)`

### Transitions

- `--transition-fast: 150ms ease-in-out`
- `--transition-base: 250ms ease-in-out`
- `--transition-slow: 350ms ease-in-out`

## Typography System

### Font Pairing

**Headings:** Montserrat (sans-serif) - Confident, clear hierarchy
**Body:** Merriweather (serif) - Readable, approachable

This pairing creates professional warmth while maintaining excellent readability.

### Hierarchy

- **h1:** 3rem (48px), tight leading, negative letter-spacing
- **h2:** 2.25rem (36px), tight leading, negative letter-spacing
- **h3:** 1.875rem (30px), tight leading
- **h4:** 1.5rem (24px), tight leading
- **h5:** 1.25rem (20px), tight leading
- **h6:** 1.125rem (18px), semibold weight

### Utility Classes

```scss
.lead { /* Large intro text (sans-serif, 20px) */ }
.text-sans { /* Override to sans-serif */ }
.text-serif { /* Override to serif */ }
.text-muted { /* Muted color for secondary text */ }
```

## Adding New Tokens

When adding design tokens:

1. **Define in `_tokens.scss`** under the appropriate section
2. **Use descriptive names** (e.g., `--color-text-muted` not `--gray-500`)
3. **Document in this README** with purpose and usage
4. **Test accessibility** if adding colors (4.5:1+ contrast for text)
5. **Follow naming conventions**:
   - Colors: `--color-{purpose}`
   - Typography: `--font-{property}` or `--text-{size}`
   - Spacing: `--space-{size}`
   - Layout: `--container-{size}`

### Example

```scss
// In _tokens.scss
:root {
  /* New color for warnings */
  --color-warning: #f59e0b;
  --color-warning-light: #fbbf24;
}

// In your component
.alert-warning {
  background-color: var(--color-warning-light);
  border-left: 4px solid var(--color-warning);
  padding: var(--space-md);
  border-radius: var(--radius-md);
}
```

## Accessibility

This design system prioritizes accessibility:

- **WCAG 2.1 Level AA compliant** - All text colors maintain 4.5:1+ contrast
- **Focus styles** - Clear visible focus indicators for keyboard navigation
- **Responsive by default** - Mobile-first approach with fluid typography
- **Semantic HTML** - Proper heading hierarchy and element usage
- **Text resizing** - Uses rem units for responsive scaling

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- CSS custom properties (IE11 not supported)
- No build tools required beyond Jekyll's built-in Sass compilation

## Migration Notes

This system replaces:
- `public/css/poole.css` (old base styles)
- `public/css/lanyon.css` (old theme)
- PT Serif/Sans fonts → Montserrat/Merriweather

Kept:
- `public/css/syntax.css` (code highlighting)

## Next Steps

This foundation enables:
- Component library (buttons, cards, navigation)
- Layout system (grid, containers)
- Responsive utilities
- Custom page templates

See `.planning/phases/02-design-system-architecture/` for roadmap.
