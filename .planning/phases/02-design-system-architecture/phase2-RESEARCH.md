# Phase 2 Research: Design System & Architecture

**Research conducted:** 2026-01-08
**Focus:** Modern design system approaches, executive portfolio trends, accessibility, CSS architecture for Jekyll

---

## Executive Summary

**Key Finding:** Modern executive portfolios in 2026 emphasize **structured storytelling** with case studies, **professional warmth** through typography contrasts, and **authenticity** over digital polish. CSS custom properties (design tokens) are the standard approach, with container queries enabling truly flexible component-based designs.

**Recommended Approach:**
1. CSS custom properties for design tokens (colors, spacing, typography)
2. Jekyll's native Sass organization (_sass directory with partials)
3. BEM or simple utility-based naming for components
4. Mobile-first responsive design with container queries
5. WCAG 2.1 AA compliance from the start (4.5:1 contrast for normal text)

---

## 1. Modern Design System Architecture

### CSS Custom Properties (Design Tokens)

**What they are:**
Design tokens are the smallest indivisible elements of a design system, representing individual design decisions as data (colors, typography, spacing, border radii). In CSS, they're implemented using CSS Custom Properties (CSS Variables).

**Best Practices for 2026:**

```css
/* Define global tokens in :root */
:root {
  /* Colors */
  --color-primary: #2563eb;
  --color-text: #1f2937;
  --color-background: #ffffff;

  /* Typography */
  --font-sans: 'Inter', system-ui, sans-serif;
  --font-serif: 'Merriweather', Georgia, serif;
  --text-base: 1rem;
  --text-lg: 1.125rem;

  /* Spacing */
  --space-xs: 0.5rem;
  --space-sm: 1rem;
  --space-md: 1.5rem;
  --space-lg: 2rem;
}
```

**Why this matters:**
- Native browser support (no build step required)
- Can be dynamically updated with JavaScript
- Easy to maintain and update globally
- Separates design decisions from implementation

**Tooling:**
Style Dictionary can transform tokens from JSON to CSS variables, but for a simple Jekyll site, hand-crafted CSS custom properties in :root are sufficient and maintainable.

**Sources:**
- [The developer's guide to design tokens and CSS variables](https://penpot.app/blog/the-developers-guide-to-design-tokens-and-css-variables/)
- [Using CSS custom properties (variables) - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties)
- [CSS Variables as Design Tokens](https://javascript.plainenglish.io/css-variables-as-design-tokens-your-frontends-best-friend-and-why-you-ll-wonder-how-you-lived-5cbc68dd6de8)

---

## 2. Executive Portfolio Design Trends (2025-2026)

### Key Trends for Professional Portfolios

**1. Structured Storytelling & Case Studies**
Modern platforms emphasize case studies that showcase not just what was built, but the strategic thinking behind it. For CTOs/CPOs, this means demonstrating:
- Problem-solving frameworks
- Technical leadership decisions
- Measurable outcomes
- Strategic impact

**2. Typography Contrasts**
Oversized text dominates layouts exuding confidence, while delicate, understated copy punctuates the design—a visual language of extremes that is both visually arresting and strategically communicative.

**Implementation for "Professional but Approachable":**
- Use contrast between bold headlines and readable body text
- Avoid overly formal fonts - conversational yet professional
- Large, confident headings with generous whitespace

**3. Nature-Distilled Aesthetics**
The "nature distilled" aesthetic features palettes that celebrate muted, earthy tones—skin, wood, soil—emphasizing subtle sophistication that brings warmth to screens.

**For your vision:** Instead of corporate grays, use warm neutrals and muted earth tones that feel sophisticated yet approachable.

**4. Authenticity Over Perfection**
The "Creative Process" trend rejects digital polish, favoring authenticity. For executive portfolios: room for personality, personal voice, and human elements without sacrificing professionalism.

**5. Card-Based Layouts**
"Card Play" is an evolution of grid systems where each card becomes a tactical module. Perfect for portfolio pieces, case studies, and project showcases.

**Credibility Signal:**
Over 72% of creative professionals say clients and recruiters evaluate portfolios primarily through personal websites rather than marketplaces or social platforms.

**Sources:**
- [Top 100 Most Creative and Unique Portfolio Websites of 2025](https://muz.li/blog/top-100-most-creative-and-unique-portfolio-websites-of-2025/)
- [19 Best Portfolio Design Trends (In 2026)](https://colorlib.com/wp/portfolio-design-trends/)
- [Best Portfolio Website Designs of 2025](https://www.designrush.com/best-designs/websites/portfolio)
- [Best design portfolio inspiration sites in 2026](https://www.adhamdannaway.com/blog/web-design/design-portfolio-inspiration)

---

## 3. Typography Systems: Professional & Approachable

### Recommended Font Pairings for Your Vision

**Top Choices for "Professional but Approachable":**

**1. Montserrat + Merriweather** ⭐ RECOMMENDED
- Creates "professional warmth" that feels confident yet human-centered
- Montserrat (sans-serif): clean, modern, geometric
- Merriweather (serif): warm, readable, approachable
- Perfect for corporate sites that want credibility with warmth

**2. Poppins + [Serif body]**
- Rounded edges feel friendly and non-intimidating
- Balances formality with creative edge
- Described as "professional but I also might have stickers on my laptop"

**3. Lato (various pairings)**
- Warm and elegant
- Ideal for conveying information in a friendly way
- Versatile, pairs well with many serif fonts

**4. Manrope**
- Geometric sans-serif
- Professional tone with friendly, modern feel
- Excellent for corporate websites wanting approachability

### General Principles

- **Limit to 2-3 fonts maximum** (often 2 is ideal)
- **Pairing structure:** Strong serif + clean sans-serif conveys professionalism and reliability
- **Hierarchy:** Use font size, weight, and contrast to create clear but natural hierarchy
- **Readability first:** Body text should be highly readable (16px minimum for body copy)

**Sources:**
- [Font Pairing Chart for Web design (2026)](https://elementor.com/blog/font-pairing-chart/)
- [20+ Beautiful Google Font Pairings For 2026 Websites](https://www.landingpageflow.com/post/google-font-pairings-for-websites)
- [24 Best Fonts for Websites in 2026](https://www.figma.com/resource-library/best-fonts-for-websites/)
- [The 40 Best Google Fonts—A Curated Collection for 2026](https://www.typewolf.com/google-fonts)

---

## 4. Accessibility: WCAG 2.1 AA Requirements

### Color Contrast Requirements

**Level AA Standards (Required):**

**Normal Text:**
- Minimum contrast ratio: **4.5:1** against background
- Applies to text under 18pt (or 14pt bold)

**Large Text:**
- Minimum contrast ratio: **3:1** against background
- "Large text" = 18pt+ (or 14pt bold+)
- Equivalent to 24px or 18.66px bold

**Non-Text Elements (WCAG 2.1):**
- UI components and graphical objects: **3:1** contrast ratio
- Applies to form borders, icons, graphical elements

### Use of Color (WCAG 1.4.1)

**Critical Rule:**
Color cannot be the ONLY visual means of conveying information. Always provide additional visual cues (icons, text labels, patterns).

**Example violations:**
- "Click the green button" (no text on button)
- Red/green status indicators without icons
- Links only distinguished by color

### Typography Specifications

**Absolute Requirements:**
- Large text threshold: 18.66px or 14pt bold (no flexibility)
- Text must be resizable up to 200% without loss of content
- Line height (leading) should be at least 1.5x font size
- Paragraph spacing should be at least 2x font size

### Testing Tools

**Recommended:**
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) - Quick online tool
- Colour Contrast Analyser (CCA) - Desktop app
- ANDI - Accessibility testing bookmarklet

**Timeline Context:**
State and local governments have compliance deadlines in 2026-2027 for WCAG 2.1 AA. Best practice is to build with compliance from the start.

**Sources:**
- [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/)
- [Understanding WCAG 2.1 A, AA, and AAA Guidelines for Color Contrast](https://www.accessibleresources.com/post/understanding-wcag-2-1-a-aa-and-aaa-guidelines-for-color-contrast)
- [WebAIM: Contrast and Color Accessibility](https://webaim.org/articles/contrast/)
- [Color Contrast Accessibility: Complete WCAG 2025 Guide](https://www.allaccessible.org/blog/color-contrast-accessibility-wcag-guide-2025)

---

## 5. CSS Architecture for Jekyll

### Jekyll Directory Structure for CSS

**Standard Organization:**

```
project-root/
├── _sass/                    # Sass partials (imported by main CSS)
│   ├── _base.scss           # Variables, mixins, resets
│   ├── _typography.scss     # Font definitions, text styles
│   ├── _layout.scss         # Layout utilities, grid
│   ├── _components.scss     # Component styles (cards, buttons, nav)
│   └── _utilities.scss      # Utility classes
├── assets/
│   └── css/
│       └── main.scss        # Main CSS file (imports from _sass)
├── public/                   # Static assets (current structure)
│   ├── css/
│   └── images/
```

**How it works:**
1. **_sass folder** contains Sass partials (files starting with `_`)
2. **assets/css/main.scss** imports partials using `@import 'base'`
3. Jekyll compiles main.scss → main.css automatically
4. Empty YAML front matter (`---`) tells Jekyll to process the file

**Best Practices:**

**1. Separation of Concerns**
```scss
// assets/css/main.scss
---
# Empty front matter tells Jekyll to process this file
---

@import 'base';       // Design tokens, variables, resets
@import 'typography'; // Font styles, text utilities
@import 'layout';     // Layout utilities, container, grid
@import 'components'; // Reusable components
@import 'utilities';  // Helper classes
```

**2. Avoid Inline Styles**
Define classes in separate CSS files, not in HTML. This maintains separation and reusability.

**3. Component Organization**
For larger projects, separate CSS by component purpose:
- Base layer: tokens, resets, global styles
- Layout layer: structure, containers, grids
- Component layer: buttons, cards, navigation
- Utility layer: spacing, display, text helpers

**4. BEM Naming Convention**
```css
/* Block */
.card { }

/* Element */
.card__title { }
.card__content { }

/* Modifier */
.card--featured { }
```

Or use simple semantic naming with utilities for one-off adjustments.

**Sources:**
- [Directory Structure | Jekyll](https://jekyllrb.com/docs/structure/)
- [Assets | Jekyll](https://jekyllrb.com/docs/step-by-step/07-assets/)
- [Jekyll Tips, Tricks, and Best Practices](https://jreel.github.io/jekyll-tips-tricks-and-best-practices/)

---

## 6. Modern CSS Features to Leverage

### Container Queries (2026 Standard)

**What they are:**
Container queries allow styling elements based on their parent container's size, not just the viewport. Huge win for component-based designs.

```css
.card-container {
  container-type: inline-size;
}

@container (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 1fr 2fr;
  }
}
```

**Why this matters:**
- Components adapt to their container, not the viewport
- True component-level responsiveness
- Cards can layout differently based on where they're placed

### Cascade Layers (Optional)

Allows defining clear specificity order for different parts of your CSS (base, components, utilities). Useful for larger systems but optional for this project.

### CSS @property (New in 2024)

Cross-browser support as of Firefox 128 (July 2024). Allows defining types, inheritance, and initial values for custom properties.

```css
@property --color-primary {
  syntax: '<color>';
  inherits: true;
  initial-value: #2563eb;
}
```

**Sources:**
- [State of CSS in 2025: Trends, Frameworks & New Features](https://designwithrehana.com/state-of-css-in-2025-trends-frameworks-new-features/)
- [CSS techniques every developer should know in 2025](https://dev.to/dimeloper/css-techniques-every-developer-should-know-in-2025-30p9)

---

## 7. Recommended Approach for Phase 2

### Implementation Strategy

**1. Design Tokens First**
Create `_sass/_tokens.scss` with CSS custom properties:
- Color palette (muted earth tones for warmth)
- Typography scale (Montserrat + Merriweather recommended)
- Spacing system (consistent rhythm)
- Border radii, shadows (subtle depth)

**2. Mobile-First Responsive**
Start with mobile layout, progressively enhance for larger screens. Use container queries for component-level responsiveness.

**3. Component Library**
Build reusable components in `_sass/_components.scss`:
- `.card` - for project showcases, case studies
- `.nav` - main navigation
- `.header` / `.footer` - site structure
- `.section` - content sections with consistent spacing

**4. Prototype Pages**
Create working Jekyll pages demonstrating the design:
- `_layouts/default.html` - base layout with new design
- `_layouts/page.html` - content page layout
- Example pages showing system in action

**5. Accessibility Built-In**
- Test color contrast from the start (WebAIM checker)
- Use semantic HTML (headings, landmarks)
- Ensure 4.5:1 contrast for normal text
- Don't rely on color alone for information

### What NOT to Hand-Roll

**Don't create custom:**
- CSS reset (use modern-normalize or simple reset)
- Responsive breakpoint system (use standard breakpoints)
- Grid system (use CSS Grid / Flexbox directly)
- Build tooling (Jekyll handles Sass compilation)

**DO hand-craft:**
- Design tokens (your specific color palette, typography)
- Component styles (unique to your brand)
- Layout templates (specific to your content)

---

## 8. Common Pitfalls to Avoid

### CSS Architecture Pitfalls

❌ **Don't:**
- Use deeply nested selectors (specificity wars)
- Mix presentation and content (inline styles)
- Create overly complex class names
- Build a framework (keep it simple)

✅ **Do:**
- Keep selectors flat and simple
- Use semantic class names
- Embrace CSS custom properties
- Build only what you need

### Design System Pitfalls

❌ **Don't:**
- Create too many variations (decision fatigue)
- Perfectionism on first iteration
- Build components you might need someday
- Copy trendy designs that don't fit your voice

✅ **Do:**
- Start with essential components only
- Iterate based on actual needs
- Build for your content (not generic)
- Maintain "professional but approachable" feel

### Accessibility Pitfalls

❌ **Common mistakes:**
- Low contrast text (especially gray on white)
- Color as only indicator (links, status)
- Tiny font sizes (<16px body text)
- Skipping semantic HTML

✅ **Best practices:**
- Test contrast early and often
- Provide multiple visual cues
- Use generous, readable text sizes
- Use proper heading hierarchy

---

## 9. Success Criteria

**You'll know Phase 2 is complete when:**

✅ Design system documented with design tokens
✅ Typography system established (fonts, scales, hierarchy)
✅ Color palette defined and WCAG AA compliant
✅ Component library created (cards, nav, header, footer)
✅ Base Jekyll layouts replaced Lanyon theme
✅ Prototype pages demonstrate the system working
✅ Mobile-first responsive design implemented
✅ Site feels "professional but approachable"
✅ Clear visual hierarchy without rigidity
✅ Room for personal touches and authenticity

**Visual test:**
Show the prototype to someone unfamiliar with the project. Do they see:
- Professional executive presence?
- Warmth and approachability?
- Clear, natural hierarchy?
- Space for personality?

If yes to all four, the design foundation is solid.

---

## 10. Next Steps

**Ready to plan:** Use this research to create detailed execution plans for Phase 2.

**Key decisions to make during planning:**
1. Exact color palette (specific hex codes)
2. Typography choices (which specific fonts)
3. Component priorities (build order)
4. Prototype page scope (which pages to design first)

**Recommended:** Break Phase 2 into 2-3 execution plans:
1. Design tokens + typography system
2. Component library + base layouts
3. Prototype pages + validation

---

*Research complete. This research provides ecosystem knowledge to inform quality, modern design system planning that aligns with 2026 best practices and your vision of "professional but approachable."*
