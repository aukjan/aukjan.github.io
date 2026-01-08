# Phase 2 Plan 1: Design Foundation (Tokens, Typography, Colors)

## Objective

Establish the visual foundation for the site: design tokens (CSS custom properties), typography system, and color palette. Create the base CSS architecture replacing Lanyon/Poole with a modern, maintainable system that feels "professional but approachable."

## Execution Context

**Related Files:**
- @_sass/ (to create - Sass partial directory)
- @assets/css/ (to create - main CSS location)
- @public/css/lanyon.css (current theme - for reference)
- @public/css/poole.css (current base - for reference)

**Reference Materials:**
- @.planning/phases/02-design-system-architecture/phase2-RESEARCH.md (design system best practices)
- @.planning/phases/02-design-system-architecture/phase2-CONTEXT.md (user vision)
- @.planning/phases/02-design-system-architecture/design-notes.md (old design reference)

**Codebase Context:**
- @.planning/codebase/STACK.md (technology stack)

## Context

**Current State:**
- Using Lanyon theme (public/css/lanyon.css + poole.css)
- Dated 2013-era design with purple sidebar
- ~1154 lines of CSS across theme files
- No design system or design tokens
- Fixed, rigid layout

**Goal:**
Create modern CSS foundation with:
- Design tokens (CSS custom properties) for colors, typography, spacing
- Professional but approachable typography system (Montserrat + Merriweather recommended from research)
- Warm, muted color palette (not corporate gray - earth tones)
- Mobile-first responsive approach
- WCAG 2.1 AA accessibility baked in (4.5:1 contrast for normal text)

**Vision from Context:**
"Professional but approachable - warm and inviting while maintaining executive credibility. Readable typography, clear hierarchy without rigidity, room for authenticity."

**Constraint:** Keep Jekyll native - no build tools beyond Sass compilation.

## Tasks

### Task 1: Create Sass Directory Structure

**What:** Set up modern Jekyll Sass architecture

**How:**
1. Create `_sass/` directory at project root
2. Create initial Sass partials:
   - `_sass/_tokens.scss` - Design tokens (CSS custom properties)
   - `_sass/_reset.scss` - Minimal CSS reset
   - `_sass/_typography.scss` - Typography styles
   - `_sass/_base.scss` - Base HTML element styles
3. Create `assets/css/` directory
4. Create `assets/css/main.scss` with empty YAML front matter
5. In main.scss, import partials:
   ```scss
   ---
   # Empty front matter tells Jekyll to process
   ---

   @import 'reset';
   @import 'tokens';
   @import 'typography';
   @import 'base';
   ```

**Verification:**
- [ ] `_sass/` directory exists with 4 partials
- [ ] `assets/css/main.scss` exists with imports
- [ ] Empty front matter present (Jekyll processing indicator)
- [ ] Clean separation of concerns

### Task 2: Define Design Tokens

**What:** Create CSS custom properties for design system

**How:**
1. In `_sass/_tokens.scss`, define tokens in `:root`:

   **Color Palette** (warm, approachable, WCAG AA compliant):
   ```scss
   :root {
     /* Primary Colors - Professional warmth */
     --color-primary: #2563eb;      // Confident blue
     --color-primary-dark: #1e40af;
     --color-primary-light: #60a5fa;

     /* Neutral Colors - Warm earth tones, not corporate gray */
     --color-text: #292524;          // Warm near-black (stone-800)
     --color-text-light: #57534e;    // stone-600
     --color-text-muted: #78716c;    // stone-500
     --color-background: #fafaf9;    // stone-50
     --color-surface: #ffffff;
     --color-border: #e7e5e4;        // stone-200

     /* Accent Colors - Subtle personality */
     --color-accent: #f59e0b;        // Amber for highlights
     --color-success: #059669;       // Emerald
     --color-muted: #a8a29e;         // stone-400

     /* Typography Scale */
     --font-sans: 'Montserrat', system-ui, -apple-system, sans-serif;
     --font-serif: 'Merriweather', Georgia, serif;
     --font-mono: 'Courier New', monospace;

     /* Font Sizes - Fluid scale */
     --text-xs: 0.75rem;    // 12px
     --text-sm: 0.875rem;   // 14px
     --text-base: 1rem;     // 16px
     --text-lg: 1.125rem;   // 18px
     --text-xl: 1.25rem;    // 20px
     --text-2xl: 1.5rem;    // 24px
     --text-3xl: 1.875rem;  // 30px
     --text-4xl: 2.25rem;   // 36px
     --text-5xl: 3rem;      // 48px

     /* Font Weights */
     --font-normal: 400;
     --font-medium: 500;
     --font-semibold: 600;
     --font-bold: 700;

     /* Line Heights */
     --leading-none: 1;
     --leading-tight: 1.25;
     --leading-snug: 1.375;
     --leading-normal: 1.5;
     --leading-relaxed: 1.625;
     --leading-loose: 2;

     /* Spacing Scale - Consistent rhythm */
     --space-xs: 0.5rem;    // 8px
     --space-sm: 1rem;      // 16px
     --space-md: 1.5rem;    // 24px
     --space-lg: 2rem;      // 32px
     --space-xl: 3rem;      // 48px
     --space-2xl: 4rem;     // 64px
     --space-3xl: 6rem;     // 96px

     /* Container & Layout */
     --container-sm: 640px;
     --container-md: 768px;
     --container-lg: 1024px;
     --container-xl: 1280px;

     /* Border Radius */
     --radius-sm: 0.25rem;  // 4px
     --radius-md: 0.5rem;   // 8px
     --radius-lg: 0.75rem;  // 12px
     --radius-xl: 1rem;     // 16px

     /* Shadows - Subtle depth */
     --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
     --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
     --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);

     /* Transitions */
     --transition-fast: 150ms ease-in-out;
     --transition-base: 250ms ease-in-out;
     --transition-slow: 350ms ease-in-out;
   }
   ```

2. Add comment documentation explaining token purpose
3. Verify all colors meet WCAG AA contrast requirements (4.5:1 for normal text)

**Verification:**
- [ ] All design tokens defined in `:root`
- [ ] Color palette feels warm, not corporate
- [ ] Typography scale is fluid and readable
- [ ] Spacing system is consistent
- [ ] Comments explain token purpose
- [ ] Test primary text contrast (should be 4.5:1+ on background)

### Task 3: Implement Typography System

**What:** Set up Montserrat + Merriweather font pairing with professional hierarchy

**How:**
1. In `_sass/_typography.scss`:

   **Import Google Fonts:**
   ```scss
   /* Import Montserrat (sans-serif) and Merriweather (serif) */
   @import url('https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;1,400&family=Montserrat:wght@400;500;600;700&display=swap');
   ```

   **Base Typography:**
   ```scss
   /* Body text - readable, approachable */
   body {
     font-family: var(--font-serif);
     font-size: var(--text-base);
     line-height: var(--leading-relaxed);
     color: var(--color-text);
     font-weight: var(--font-normal);
   }

   /* Headings - confident, clear hierarchy */
   h1, h2, h3, h4, h5, h6 {
     font-family: var(--font-sans);
     font-weight: var(--font-bold);
     line-height: var(--leading-tight);
     color: var(--color-text);
     margin-bottom: var(--space-md);
   }

   h1 {
     font-size: var(--text-5xl);
     letter-spacing: -0.025em;
   }

   h2 {
     font-size: var(--text-4xl);
     letter-spacing: -0.025em;
   }

   h3 {
     font-size: var(--text-3xl);
   }

   h4 {
     font-size: var(--text-2xl);
   }

   h5 {
     font-size: var(--text-xl);
   }

   h6 {
     font-size: var(--text-lg);
     font-weight: var(--font-semibold);
   }

   /* Paragraphs - generous spacing */
   p {
     margin-bottom: var(--space-md);
   }

   /* Links - clear affordance */
   a {
     color: var(--color-primary);
     text-decoration: underline;
     text-decoration-thickness: 1px;
     text-underline-offset: 2px;
     transition: color var(--transition-fast);

     &:hover {
       color: var(--color-primary-dark);
     }
   }

   /* Lead text - introductions */
   .lead {
     font-size: var(--text-xl);
     font-family: var(--font-sans);
     font-weight: var(--font-normal);
     line-height: var(--leading-normal);
     color: var(--color-text-light);
   }

   /* Small text */
   small {
     font-size: var(--text-sm);
     color: var(--color-text-muted);
   }

   /* Strong emphasis */
   strong {
     font-weight: var(--font-bold);
   }
   ```

2. Create utility classes for typography variants:
   ```scss
   .text-sans { font-family: var(--font-sans); }
   .text-serif { font-family: var(--font-serif); }
   .text-muted { color: var(--color-text-muted); }
   ```

**Verification:**
- [ ] Google Fonts imported (Montserrat + Merriweather)
- [ ] Body uses serif (readable, approachable)
- [ ] Headings use sans-serif (confident, clear)
- [ ] Clear hierarchy established
- [ ] Links have clear affordance
- [ ] Text meets WCAG AA (4.5:1 contrast)

### Task 4: Create Minimal CSS Reset

**What:** Modern CSS reset for consistency

**How:**
1. In `_sass/_reset.scss`:
   ```scss
   /* Modern CSS Reset */
   *, *::before, *::after {
     box-sizing: border-box;
   }

   * {
     margin: 0;
     padding: 0;
   }

   html {
     -webkit-font-smoothing: antialiased;
     -moz-osx-font-smoothing: grayscale;
   }

   body {
     min-height: 100vh;
     text-rendering: optimizeLegibility;
   }

   img, picture, video, canvas, svg {
     display: block;
     max-width: 100%;
   }

   input, button, textarea, select {
     font: inherit;
   }

   p, h1, h2, h3, h4, h5, h6 {
     overflow-wrap: break-word;
   }
   ```

**Verification:**
- [ ] Box-sizing set to border-box
- [ ] Margins/padding reset
- [ ] Font smoothing enabled
- [ ] Images responsive by default

### Task 5: Define Base Styles

**What:** Base HTML element styles using tokens

**How:**
1. In `_sass/_base.scss`:
   ```scss
   /* Base HTML element styles */

   html {
     font-size: 16px; /* Base for rem calculations */
   }

   body {
     background-color: var(--color-background);
     color: var(--color-text);
   }

   /* Selection styling */
   ::selection {
     background-color: var(--color-primary-light);
     color: var(--color-surface);
   }

   /* Focus styles - accessibility */
   :focus-visible {
     outline: 2px solid var(--color-primary);
     outline-offset: 2px;
   }

   /* Lists */
   ul, ol {
     margin-bottom: var(--space-md);
     padding-left: var(--space-lg);
   }

   li {
     margin-bottom: var(--space-xs);
   }

   /* Horizontal rule */
   hr {
     border: none;
     border-top: 1px solid var(--color-border);
     margin: var(--space-xl) 0;
   }

   /* Code */
   code {
     font-family: var(--font-mono);
     font-size: 0.9em;
     background-color: var(--color-border);
     padding: 0.125rem 0.25rem;
     border-radius: var(--radius-sm);
   }

   pre {
     background-color: var(--color-text);
     color: var(--color-surface);
     padding: var(--space-md);
     border-radius: var(--radius-md);
     overflow-x: auto;
     margin-bottom: var(--space-md);

     code {
       background-color: transparent;
       padding: 0;
     }
   }

   /* Blockquote */
   blockquote {
     border-left: 4px solid var(--color-primary);
     padding-left: var(--space-md);
     margin-left: 0;
     margin-bottom: var(--space-md);
     font-style: italic;
     color: var(--color-text-light);
   }
   ```

**Verification:**
- [ ] Base HTML elements styled
- [ ] Focus styles for accessibility
- [ ] Selection color defined
- [ ] Code and blockquote styled
- [ ] All styles use design tokens

### Task 6: Update Head to Load New CSS

**What:** Update _includes/head.html to load new CSS

**How:**
1. Read current `_includes/head.html`
2. Replace CSS links:
   - Remove: `<link rel="stylesheet" href="/public/css/poole.css">`
   - Remove: `<link rel="stylesheet" href="/public/css/lanyon.css">`
   - Add: `<link rel="stylesheet" href="/assets/css/main.css">`
3. Keep syntax.css for now (code highlighting)
4. Ensure Google Fonts are loaded from typography.scss (already imported via @import)

**Verification:**
- [ ] New CSS link added to head
- [ ] Old theme CSS removed
- [ ] syntax.css preserved
- [ ] No broken links

### Task 7: Test Color Contrast for WCAG AA

**What:** Verify all color combinations meet accessibility standards

**How:**
1. Test primary color combinations:
   - `--color-text` on `--color-background` (should be 4.5:1+)
   - `--color-text-light` on `--color-background` (should be 4.5:1+)
   - `--color-primary` on `--color-surface` (for links)
2. Use WebAIM Contrast Checker or similar tool
3. Document results in task verification
4. Adjust colors if any fail (darken text or lighten background)

**Verification:**
- [ ] Text/background contrast: ≥ 4.5:1 (WCAG AA)
- [ ] Text-light/background contrast: ≥ 4.5:1
- [ ] Primary/surface contrast: ≥ 4.5:1
- [ ] All combinations documented and pass

### Task 8: Create Foundation Documentation

**What:** Document the design system foundation

**How:**
1. Create `_sass/README.md` with:
   - Overview of design token system
   - How to use CSS custom properties
   - Color palette with hex codes and purpose
   - Typography system overview
   - Spacing scale
   - How to add new tokens
   - Accessibility notes (WCAG AA compliance)

**Verification:**
- [ ] README.md created in _sass/
- [ ] Design tokens documented
- [ ] Usage examples provided
- [ ] Accessibility requirements noted

### Task 9: Commit Design Foundation

**What:** Commit all design foundation work

**How:**
1. Review all changes
2. Test that Jekyll compiles CSS (run `bundle exec jekyll build` or verify no errors)
3. Stage all new files:
   - `_sass/` directory and all partials
   - `assets/css/main.scss`
   - Updated `_includes/head.html`
   - `_sass/README.md`
4. Commit with message:
   ```
   feat(phase2-foundation): establish design system foundation

   Create modern CSS architecture with design tokens:
   - CSS custom properties for colors, typography, spacing
   - Montserrat + Merriweather typography pairing
   - Warm earth tone color palette (professional but approachable)
   - WCAG 2.1 AA accessible (4.5:1+ contrast)
   - Mobile-first responsive foundation
   - Jekyll Sass architecture (_sass/ partials)

   Replaces Lanyon/Poole theme with maintainable token-based system.

   Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
   ```

**Verification:**
- [ ] Jekyll compiles without errors
- [ ] All files staged
- [ ] Commit message follows convention
- [ ] Changes documented

## Verification

**Automated Checks:**
```bash
# Sass directory structure exists
test -d _sass && echo "✓ _sass directory exists"
test -f _sass/_tokens.scss && echo "✓ tokens partial exists"
test -f _sass/_typography.scss && echo "✓ typography partial exists"
test -f _sass/_reset.scss && echo "✓ reset partial exists"
test -f _sass/_base.scss && echo "✓ base partial exists"

# Main CSS exists
test -f assets/css/main.scss && echo "✓ main.scss exists"

# Jekyll processes CSS
bundle exec jekyll build && test -f _site/assets/css/main.css && echo "✓ CSS compiles"

# Documentation exists
test -f _sass/README.md && echo "✓ Design system documented"
```

**Manual Checks:**
- [ ] Site loads without CSS errors
- [ ] Typography feels professional but approachable
- [ ] Colors feel warm, not corporate
- [ ] Text is highly readable
- [ ] All design tokens work as expected
- [ ] WCAG AA contrast verified

## Success Criteria

- [ ] Modern Sass directory structure created
- [ ] Design tokens defined in CSS custom properties
- [ ] Typography system established (Montserrat + Merriweather)
- [ ] Warm, approachable color palette defined
- [ ] All colors meet WCAG 2.1 AA contrast (4.5:1+)
- [ ] Minimal CSS reset implemented
- [ ] Base HTML element styles defined
- [ ] Head updated to load new CSS
- [ ] Design system documented
- [ ] Jekyll compiles CSS without errors
- [ ] Foundation feels "professional but approachable"

## Output

**Created Files:**
- `_sass/_tokens.scss` - Design token definitions
- `_sass/_reset.scss` - Modern CSS reset
- `_sass/_typography.scss` - Typography system
- `_sass/_base.scss` - Base element styles
- `assets/css/main.scss` - Main CSS entry point
- `_sass/README.md` - Design system documentation

**Modified Files:**
- `_includes/head.html` - Updated CSS links

**Git Commits:**
- Design foundation with tokens, typography, colors

---

**Estimated Time:** 60-90 minutes
**Dependencies:** Phase 1 complete (foundation clean)
**Next Plan:** phase2-components-PLAN.md (component library)

**Notes:**
- This establishes the foundation - tokens and base styles
- No components yet - those come in next plan
- Site will look plain after this (expected) - adding structure, not polish yet
- Focus on getting tokens right - they'll be used everywhere
- Verify WCAG AA contrast for all color combinations
