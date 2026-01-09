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

## Component Library

### Hero Section

Large, eye-catching hero section with gradient background for homepage prominence.

```html
<section class="hero">
  <div class="container">
    <div class="hero-content">
      <h1 class="hero-title">Your Name</h1>
      <p class="hero-subtitle">Title | Role | Expertise</p>
      <p class="hero-description">Brief value proposition</p>
    </div>
  </div>
</section>
```

**When to use:**
- Homepage only (creates focal point)
- Above-the-fold introduction
- Clear value proposition display

**Accessibility:**
- White text on gradient meets WCAG AAA (8:1+ contrast)
- Scales down on mobile (48px → 36px heading)

### Card Component

Primary content container with shadow, rounded corners, and hover effect.

```html
<div class="card">
  <h3 class="card-title">Card Title</h3>
  <p class="card-content">Card content goes here.</p>
</div>
```

**When to use:**
- Grouping related content
- Article previews in grids
- Expertise areas, features, or highlights

**Behavior:**
- Subtle lift on hover (2px translateY)
- Shadow increases on hover for depth
- Fully responsive (stacks on mobile)

### Button Component

Call-to-action buttons in primary and secondary styles.

```html
<a href="/page" class="btn btn-primary">Primary Action</a>
<a href="/page" class="btn btn-secondary">Secondary Action</a>
```

**When to use:**
- Primary: Main call-to-action (one per section)
- Secondary: Alternative actions, less emphasis

**Accessibility:**
- Minimum 44px touch target
- Clear focus-visible outline (3px)
- Adequate padding and contrast

### Badge/Tag

Small labels for categories or status indicators.

```html
<span class="badge">New</span>
```

**When to use:**
- Post categories or tags
- Status indicators
- Small labels

## Layout System

### Containers

Constrained-width containers for content.

```html
<div class="container">Full width (1024px max)</div>
<div class="container container-md">Medium (768px max)</div>
<div class="container container-sm">Small (640px max)</div>
```

**Responsive behavior:**
- Mobile: 24px horizontal padding
- Desktop (768px+): 32px horizontal padding
- Auto-centered with max-width constraints

### Sections

Consistent vertical spacing for page sections.

```html
<section class="section">
  <div class="container">
    <!-- Section content -->
  </div>
</section>
```

**Spacing:**
- Mobile: 64px top/bottom padding
- Desktop: 96px top/bottom padding

### Grid System

Responsive grid layout (mobile-first).

```html
<div class="grid grid-cols-2">
  <div>Column 1</div>
  <div>Column 2</div>
</div>

<div class="grid grid-cols-3">
  <div>Column 1</div>
  <div>Column 2</div>
  <div>Column 3</div>
</div>
```

**Responsive behavior:**
- Mobile: 1 column (automatic)
- Tablet+ (768px): 2 or 3 columns as specified
- 24px gap between items

## Page Layouts

### Default Layout

Base layout with header, main, footer landmarks.

```yaml
---
layout: default
title: Page Title
---

<!-- Your content here -->
```

**Includes:**
- Semantic HTML structure
- Site header with navigation
- Main content area
- Site footer

### Page Layout

Content page with centered article wrapper.

```yaml
---
layout: page
title: Page Title
subtitle: Optional Subtitle
---

## Your Content

Regular markdown content here.
```

**Features:**
- Centered content (768px max-width)
- Page header with title and optional subtitle
- Optimal reading width (70ch for text)
- Proper article semantics

### Post Layout

Blog post layout with metadata.

```yaml
---
layout: post
title: Post Title
date: 2024-01-08
---

Your post content here.
```

**Features:**
- Post header with title and date
- Reading-optimized content width
- Post metadata styling
- Image support with rounded corners

## Design Patterns

### Homepage Pattern

```html
<!-- Hero -->
<section class="hero">...</section>

<!-- Introduction -->
<section class="section">
  <div class="container container-md">
    <div class="intro-content">
      <h2>Section Title</h2>
      <p class="lead">Lead paragraph</p>
      <p>Regular content</p>
    </div>
  </div>
</section>

<!-- Card Grid -->
<section class="section" style="background-color: var(--color-background);">
  <div class="container">
    <h2 style="text-align: center; margin-bottom: var(--space-2xl);">
      Section Title
    </h2>
    <div class="grid grid-cols-3">
      <div class="card">...</div>
      <div class="card">...</div>
      <div class="card">...</div>
    </div>
  </div>
</section>

<!-- Call to Action -->
<section class="section">
  <div class="container container-sm" style="text-align: center;">
    <h2>Call to Action</h2>
    <p class="lead">Description</p>
    <div style="margin-top: var(--space-lg);">
      <a href="#" class="btn btn-primary">Primary Action</a>
      <a href="#" class="btn btn-secondary">Secondary Action</a>
    </div>
  </div>
</section>
```

### Article Archive Pattern

```html
{% if site.posts.size == 0 %}
  <div style="text-align: center; padding: var(--space-3xl) 0;">
    <p class="lead">Empty state message</p>
    <p>Additional context</p>
  </div>
{% else %}
  <div class="grid grid-cols-2">
    {% for post in site.posts %}
      <article class="card">
        <h3 class="card-title">
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h3>
        <div class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%B %d, %Y" }}
          </time>
        </div>
        <p class="card-content">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
        <a href="{{ post.url }}" class="btn btn-secondary">Read More →</a>
      </article>
    {% endfor %}
  </div>
{% endif %}
```

## Responsive Behavior

### Mobile-First Strategy

All components default to mobile layout and enhance for larger screens.

**Breakpoints:**
- Mobile: < 768px (default styles)
- Tablet+: >= 768px (enhanced layouts)

**Key Responsive Changes at 768px:**
- Grid: 1 column → 2-3 columns
- Container padding: 24px → 32px
- Section spacing: 64px → 96px
- Header: Column → Row layout

### Typography Scaling

Headings scale down on mobile for better fit:

```scss
.hero-title {
  font-size: var(--text-5xl); // 48px

  @media (max-width: 767px) {
    font-size: var(--text-4xl); // 36px
  }
}

.hero-subtitle {
  font-size: var(--text-2xl); // 24px

  @media (max-width: 767px) {
    font-size: var(--text-xl); // 20px
  }
}
```

## Accessibility Guidelines

### Focus States

All interactive elements have clear focus indicators:

```scss
.btn:focus-visible {
  outline: 3px solid var(--color-primary-light);
  outline-offset: 2px;
}

a:focus-visible {
  outline: 3px solid var(--color-primary-light);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
```

### Motion Preferences

Respects `prefers-reduced-motion` user preference:

```scss
@media (prefers-reduced-motion: reduce) {
  html {
    scroll-behavior: auto;
  }

  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

### WCAG 2.1 AA Compliance

✓ Color contrast: All combinations exceed 4.5:1 (most exceed 7:1 AAA)
✓ Keyboard navigation: All interactive elements accessible
✓ Focus indicators: Visible and clear (3px outline)
✓ Semantic HTML: Proper landmarks and heading hierarchy
✓ Touch targets: Minimum 44px for all interactive elements
✓ Motion preferences: Respects prefers-reduced-motion

## Design Decisions & Rationale

### Typography Pairing

**Montserrat + Merriweather**
- Montserrat (sans): Modern, geometric, confident for headings
- Merriweather (serif): Warm, readable, approachable for body
- Pairing creates professional warmth without sterility

### Color Palette

**Warm Earth Tones (Stone Palette)**
- Chosen over corporate grays for approachability
- Stone-800 (#292524) provides warmth in dark text
- Stone-50 (#fafaf9) creates soft, comfortable background
- Confident blue (#2563eb) adds trust and credibility

### Spacing System

**8px Base Unit (0.5rem increments)**
- Creates consistent vertical rhythm
- Easy mental math for spacing decisions
- Scales naturally with font-size changes
- Prevents arbitrary spacing values

### Component Patterns

**Cards as Primary Content Container**
- Provides clear content grouping
- Subtle shadow for depth without excess
- Hover effect adds interactivity
- Flexible for various content types

## Phase 2 Completion Status

✅ **Foundation (phase2-foundation):**
- Design tokens established (_tokens.scss)
- Typography system complete (_typography.scss)
- Base styles and reset implemented

✅ **Components (phase2-components):**
- Component library built (_components.scss)
- Layout system created (_layout.scss)
- All three layouts replaced (default, page, post)

✅ **Prototype (phase2-prototype):**
- Homepage redesigned with hero and cards
- About page updated with personality
- Archive page using card layout
- 404 page friendly and helpful
- Visual polish added (hover effects, smooth scroll)
- WCAG 2.1 AA accessibility verified
- Cross-browser compatibility confirmed
- Responsive design tested across breakpoints
- "Professional but approachable" aesthetic achieved

## Next Steps (Phase 3)

With Phase 2 complete, the design system is ready for:
- Core content pages (case studies, portfolio items)
- Additional content types and templates
- Blog post creation
- Advanced interactive components (if needed)
- Performance optimization

See `.planning/phases/03-core-pages-content/` for Phase 3 roadmap.
