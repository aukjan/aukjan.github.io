# Phase 2 Plan 2: Component Library & Base Layouts

## Objective

Build reusable component library (navigation, header, footer, cards) and create new Jekyll base layouts replacing the Lanyon theme. Establish responsive container system and mobile-first layout framework.

## Execution Context

**Related Files:**
- @_sass/_components.scss (to create)
- @_sass/_layout.scss (to create)
- @_layouts/default.html (to replace)
- @_layouts/page.html (to update)
- @_includes/header.html (to create)
- @_includes/footer.html (to create)
- @_includes/nav.html (to create)
- @_includes/sidebar.html (current Lanyon - to remove)

**Reference Materials:**
- @.planning/phases/02-design-system-architecture/phase2-RESEARCH.md (component patterns)
- @.planning/phases/02-design-system-architecture/phase2-CONTEXT.md (user vision)
- @.planning/phases/02-design-system-architecture/design-notes.md (card patterns)

**Dependencies:**
- phase2-foundation-PLAN.md must be complete (design tokens exist)

## Context

**Current State:**
- Lanyon theme with sidebar navigation
- Fixed layout with toggle sidebar
- Purple accent colors (dated)
- No component system
- Design tokens now established (from Plan 1)

**Goal:**
Create modern component library:
- Card-based components for content
- Clean navigation header
- Professional footer
- Container/layout system
- Mobile-first responsive
- All components use design tokens

**Vision:**
"Card Play" trend from research - card-based layouts for project showcases. Clear hierarchy without rigidity. Components that feel structured but not sterile.

**Constraint:** Keep it simple - no complex animations or interactions (deferred to later).

## Tasks

### Task 1: Create Layout Sass Partial

**What:** Container and layout utilities

**How:**
1. Create `_sass/_layout.scss`
2. Define layout components:

   ```scss
   /* Container - constrained content width */
   .container {
     width: 100%;
     max-width: var(--container-lg);
     margin-left: auto;
     margin-right: auto;
     padding-left: var(--space-md);
     padding-right: var(--space-md);

     @media (min-width: 768px) {
       padding-left: var(--space-lg);
       padding-right: var(--space-lg);
     }
   }

   .container-sm {
     max-width: var(--container-sm);
   }

   .container-md {
     max-width: var(--container-md);
   }

   /* Section spacing */
   .section {
     padding-top: var(--space-2xl);
     padding-bottom: var(--space-2xl);

     @media (min-width: 768px) {
       padding-top: var(--space-3xl);
       padding-bottom: var(--space-3xl);
     }
   }

   /* Flex utilities */
   .flex {
     display: flex;
   }

   .flex-col {
     flex-direction: column;
   }

   .items-center {
     align-items: center;
   }

   .justify-between {
     justify-content: space-between;
   }

   .gap-sm { gap: var(--space-sm); }
   .gap-md { gap: var(--space-md); }
   .gap-lg { gap: var(--space-lg); }

   /* Grid utilities */
   .grid {
     display: grid;
     gap: var(--space-md);
   }

   .grid-cols-1 {
     grid-template-columns: repeat(1, 1fr);
   }

   @media (min-width: 768px) {
     .grid-cols-2 {
       grid-template-columns: repeat(2, 1fr);
     }

     .grid-cols-3 {
       grid-template-columns: repeat(3, 1fr);
     }
   }

   /* Spacing utilities */
   .mt-sm { margin-top: var(--space-sm); }
   .mt-md { margin-top: var(--space-md); }
   .mt-lg { margin-top: var(--space-lg); }
   .mt-xl { margin-top: var(--space-xl); }

   .mb-sm { margin-bottom: var(--space-sm); }
   .mb-md { margin-bottom: var(--space-md); }
   .mb-lg { margin-bottom: var(--space-lg); }
   .mb-xl { margin-bottom: var(--space-xl); }
   ```

3. Add to `assets/css/main.scss`:
   ```scss
   @import 'layout';
   ```

**Verification:**
- [ ] Layout partial created
- [ ] Container system defined
- [ ] Responsive grid utilities
- [ ] Spacing utilities available
- [ ] Imported in main.scss

### Task 2: Create Component Sass Partial

**What:** Reusable component styles

**How:**
1. Create `_sass/_components.scss`
2. Define components:

   **Card Component:**
   ```scss
   /* Card - primary content container */
   .card {
     background-color: var(--color-surface);
     border-radius: var(--radius-lg);
     padding: var(--space-lg);
     box-shadow: var(--shadow-md);
     transition: box-shadow var(--transition-base);

     &:hover {
       box-shadow: var(--shadow-lg);
     }
   }

   .card-title {
     font-size: var(--text-2xl);
     font-weight: var(--font-bold);
     margin-bottom: var(--space-sm);
     color: var(--color-text);
   }

   .card-content {
     color: var(--color-text-light);
     line-height: var(--leading-relaxed);
   }

   /* Button Component */
   .btn {
     display: inline-block;
     padding: var(--space-sm) var(--space-lg);
     font-family: var(--font-sans);
     font-weight: var(--font-semibold);
     text-decoration: none;
     border-radius: var(--radius-md);
     transition: all var(--transition-fast);
     cursor: pointer;
     border: none;
   }

   .btn-primary {
     background-color: var(--color-primary);
     color: var(--color-surface);

     &:hover {
       background-color: var(--color-primary-dark);
     }
   }

   .btn-secondary {
     background-color: transparent;
     color: var(--color-primary);
     border: 2px solid var(--color-primary);

     &:hover {
       background-color: var(--color-primary);
       color: var(--color-surface);
     }
   }

   /* Badge/Tag Component */
   .badge {
     display: inline-block;
     padding: var(--space-xs) var(--space-sm);
     font-size: var(--text-sm);
     font-weight: var(--font-medium);
     font-family: var(--font-sans);
     background-color: var(--color-primary-light);
     color: var(--color-primary-dark);
     border-radius: var(--radius-sm);
   }

   /* Page Title */
   .page-title {
     font-size: var(--text-5xl);
     font-weight: var(--font-bold);
     margin-bottom: var(--space-md);
     line-height: var(--leading-tight);

     @media (max-width: 767px) {
       font-size: var(--text-4xl);
     }
   }

   .page-subtitle {
     font-size: var(--text-xl);
     font-family: var(--font-sans);
     color: var(--color-text-light);
     margin-bottom: var(--space-xl);
   }
   ```

3. Add to `assets/css/main.scss`:
   ```scss
   @import 'components';
   ```

**Verification:**
- [ ] Components partial created
- [ ] Card component defined
- [ ] Button styles created
- [ ] Badge/tag component available
- [ ] Page title styles defined
- [ ] Imported in main.scss

### Task 3: Create Header Component

**What:** Site header with navigation

**How:**
1. Create `_includes/header.html`:
   ```html
   <header class="site-header">
     <div class="container">
       <div class="header-content">
         <div class="site-brand">
           <a href="/" class="site-title">{{ site.title }}</a>
           <p class="site-tagline">{{ site.tagline }}</p>
         </div>
         <nav class="site-nav">
           <a href="/" class="nav-link">Home</a>
           <a href="/about" class="nav-link">About</a>
           <a href="/archive" class="nav-link">Articles</a>
         </nav>
       </div>
     </div>
   </header>
   ```

2. Add header styles to `_sass/_components.scss`:
   ```scss
   /* Header */
   .site-header {
     background-color: var(--color-surface);
     border-bottom: 1px solid var(--color-border);
     padding: var(--space-lg) 0;
   }

   .header-content {
     display: flex;
     justify-content: space-between;
     align-items: center;
     gap: var(--space-md);

     @media (max-width: 767px) {
       flex-direction: column;
       align-items: flex-start;
     }
   }

   .site-brand {
     .site-title {
       font-size: var(--text-2xl);
       font-weight: var(--font-bold);
       font-family: var(--font-sans);
       color: var(--color-text);
       text-decoration: none;
       display: block;

       &:hover {
         color: var(--color-primary);
       }
     }

     .site-tagline {
       font-size: var(--text-sm);
       color: var(--color-text-muted);
       margin: 0;
       font-family: var(--font-sans);
     }
   }

   .site-nav {
     display: flex;
     gap: var(--space-lg);

     @media (max-width: 767px) {
       gap: var(--space-md);
     }
   }

   .nav-link {
     font-family: var(--font-sans);
     font-weight: var(--font-medium);
     color: var(--color-text);
     text-decoration: none;
     padding: var(--space-xs) 0;
     border-bottom: 2px solid transparent;
     transition: all var(--transition-fast);

     &:hover {
       color: var(--color-primary);
       border-bottom-color: var(--color-primary);
     }
   }
   ```

**Verification:**
- [ ] Header include created
- [ ] Clean, professional navigation
- [ ] Site title and tagline displayed
- [ ] Mobile-responsive
- [ ] Header styles added

### Task 4: Create Footer Component

**What:** Site footer with links and copyright

**How:**
1. Create `_includes/footer.html`:
   ```html
   <footer class="site-footer">
     <div class="container">
       <div class="footer-content">
         <div class="footer-info">
           <p class="footer-text">
             &copy; {{ site.time | date: '%Y' }} {{ site.author.name }}. All rights reserved.
           </p>
           <p class="footer-text">
             Built with <a href="https://jekyllrb.com">Jekyll</a> and hosted on <a href="https://pages.github.com">GitHub Pages</a>.
           </p>
         </div>
         <div class="footer-links">
           {% if site.author.url %}
           <a href="{{ site.author.url }}" class="footer-link" target="_blank" rel="noopener noreferrer">LinkedIn</a>
           {% endif %}
           <a href="/archive" class="footer-link">Articles</a>
           <a href="/about" class="footer-link">About</a>
         </div>
       </div>
     </div>
   </footer>
   ```

2. Add footer styles to `_sass/_components.scss`:
   ```scss
   /* Footer */
   .site-footer {
     background-color: var(--color-text);
     color: var(--color-surface);
     padding: var(--space-2xl) 0 var(--space-lg);
     margin-top: var(--space-3xl);
   }

   .footer-content {
     display: flex;
     justify-content: space-between;
     align-items: flex-start;
     gap: var(--space-xl);

     @media (max-width: 767px) {
       flex-direction: column;
       gap: var(--space-lg);
     }
   }

   .footer-info {
     flex: 1;
   }

   .footer-text {
     font-size: var(--text-sm);
     color: var(--color-muted);
     margin-bottom: var(--space-sm);

     a {
       color: var(--color-surface);
       text-decoration: underline;

       &:hover {
         color: var(--color-primary-light);
       }
     }
   }

   .footer-links {
     display: flex;
     gap: var(--space-lg);

     @media (max-width: 767px) {
       flex-direction: column;
       gap: var(--space-sm);
     }
   }

   .footer-link {
     color: var(--color-surface);
     text-decoration: none;
     font-weight: var(--font-medium);
     font-family: var(--font-sans);
     font-size: var(--text-sm);

     &:hover {
       color: var(--color-primary-light);
     }
   }
   ```

**Verification:**
- [ ] Footer include created
- [ ] Copyright and credits included
- [ ] Footer links functional
- [ ] Mobile-responsive
- [ ] Footer styles added

### Task 5: Create New Default Layout

**What:** Replace Lanyon default layout with modern structure

**How:**
1. Read current `_layouts/default.html`
2. Replace with new structure:
   ```html
   <!DOCTYPE html>
   <html lang="{{ site.lang | default: 'en-US' }}">
   {% include head.html %}
   <body>

     {% include header.html %}

     <main class="site-main">
       {{ content }}
     </main>

     {% include footer.html %}

   </body>
   </html>
   ```

3. Add main styles to `_sass/_layout.scss`:
   ```scss
   /* Main content area */
   .site-main {
     min-height: 60vh;
     padding: var(--space-2xl) 0;
   }
   ```

**Verification:**
- [ ] Default layout replaced
- [ ] Header included
- [ ] Footer included
- [ ] Main content area defined
- [ ] Clean, simple structure
- [ ] No sidebar references

### Task 6: Update Page Layout

**What:** Update page layout for content pages

**How:**
1. Read current `_layouts/page.html`
2. Update to use new components:
   ```html
   ---
   layout: default
   ---

   <article class="page">
     <div class="container container-md">
       <header class="page-header">
         <h1 class="page-title">{{ page.title }}</h1>
         {% if page.subtitle %}
         <p class="page-subtitle">{{ page.subtitle }}</p>
         {% endif %}
       </header>

       <div class="page-content">
         {{ content }}
       </div>
     </div>
   </article>
   ```

3. Add page styles to `_sass/_components.scss`:
   ```scss
   /* Page */
   .page {
     .page-header {
       margin-bottom: var(--space-xl);
       text-align: center;
     }

     .page-content {
       max-width: 70ch; /* Optimal reading width */
       margin: 0 auto;

       /* Generous spacing for content */
       > * + * {
         margin-top: var(--space-md);
       }

       h2 {
         margin-top: var(--space-2xl);
       }

       h3 {
         margin-top: var(--space-xl);
       }
     }
   }
   ```

**Verification:**
- [ ] Page layout updated
- [ ] Uses container system
- [ ] Centered content with optimal width
- [ ] Page header styled
- [ ] Content spacing generous

### Task 7: Update Post Layout

**What:** Update blog post layout

**How:**
1. Read current `_layouts/post.html`
2. Update to use new components:
   ```html
   ---
   layout: default
   ---

   <article class="post">
     <div class="container container-md">
       <header class="post-header">
         <h1 class="post-title">{{ page.title }}</h1>
         <div class="post-meta">
           <time datetime="{{ page.date | date_to_xmlschema }}">
             {{ page.date | date: "%B %d, %Y" }}
           </time>
         </div>
       </header>

       <div class="post-content">
         {{ content }}
       </div>
     </div>
   </article>
   ```

3. Add post styles to `_sass/_components.scss`:
   ```scss
   /* Post */
   .post {
     .post-header {
       margin-bottom: var(--space-xl);
     }

     .post-title {
       margin-bottom: var(--space-sm);
     }

     .post-meta {
       font-size: var(--text-sm);
       color: var(--color-text-muted);
       font-family: var(--font-sans);
     }

     .post-content {
       max-width: 70ch;
       margin: 0 auto;

       > * + * {
         margin-top: var(--space-md);
       }

       h2 {
         margin-top: var(--space-2xl);
       }

       h3 {
         margin-top: var(--space-xl);
       }

       img {
         border-radius: var(--radius-lg);
         margin-top: var(--space-lg);
         margin-bottom: var(--space-lg);
       }
     }
   }
   ```

**Verification:**
- [ ] Post layout updated
- [ ] Post metadata displayed
- [ ] Optimal reading width (70ch)
- [ ] Content spacing appropriate
- [ ] Images rounded

### Task 8: Remove Lanyon Sidebar

**What:** Remove old sidebar references

**How:**
1. Delete `_includes/sidebar.html` (no longer needed)
2. Search codebase for sidebar references:
   ```bash
   grep -r "sidebar" _layouts _includes 2>/dev/null
   ```
3. Remove any remaining sidebar classes or references
4. Remove `public/css/lanyon.css` and `public/css/poole.css` (replaced)

**Verification:**
- [ ] sidebar.html deleted
- [ ] No sidebar references in layouts
- [ ] Old theme CSS removed
- [ ] No broken references

### Task 9: Test Responsive Behavior

**What:** Verify mobile-first responsive design works

**How:**
1. Build site: `bundle exec jekyll build`
2. Serve locally: `bundle exec jekyll serve` or use preview.py
3. Test at different widths:
   - Mobile (320px - 767px): Single column, stacked nav
   - Tablet (768px - 1023px): Two columns where appropriate
   - Desktop (1024px+): Full layout, three columns where appropriate
4. Verify:
   - Header stacks on mobile
   - Navigation is accessible
   - Cards stack appropriately
   - Text remains readable
   - No horizontal scroll

**Verification:**
- [ ] Site builds without errors
- [ ] Mobile layout works (320px+)
- [ ] Tablet layout appropriate
- [ ] Desktop layout optimal
- [ ] No horizontal scroll at any width
- [ ] Touch targets adequate (44px+)

### Task 10: Commit Component Library

**What:** Commit all component work

**How:**
1. Review all changes
2. Stage files:
   - `_sass/_layout.scss`
   - `_sass/_components.scss`
   - `_includes/header.html`
   - `_includes/footer.html`
   - `_layouts/default.html`
   - `_layouts/page.html`
   - `_layouts/post.html`
   - Updated `assets/css/main.scss`
   - Deleted sidebar and old CSS
3. Commit:
   ```
   feat(phase2-components): build component library and layouts

   Create reusable component library replacing Lanyon theme:
   - Container and layout utilities (responsive grid, flexbox)
   - Card component for content showcases
   - Button and badge components
   - Header with clean navigation
   - Footer with links and credits
   - New default, page, and post layouts
   - Mobile-first responsive design
   - Remove Lanyon sidebar and old theme CSS

   All components use design tokens from phase2-foundation.

   Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
   ```

**Verification:**
- [ ] All files staged
- [ ] Commit message descriptive
- [ ] Site builds successfully
- [ ] Components functional

## Verification

**Automated Checks:**
```bash
# Component files exist
test -f _sass/_layout.scss && echo "✓ layout partial exists"
test -f _sass/_components.scss && echo "✓ components partial exists"
test -f _includes/header.html && echo "✓ header include exists"
test -f _includes/footer.html && echo "✓ footer include exists"

# Old theme removed
! test -f _includes/sidebar.html && echo "✓ sidebar removed"
! test -f public/css/lanyon.css && echo "✓ lanyon.css removed"

# Site builds
bundle exec jekyll build && echo "✓ site builds successfully"
```

**Manual Checks:**
- [ ] Site has modern, clean header
- [ ] Navigation is clear and accessible
- [ ] Footer is professional
- [ ] Components feel cohesive
- [ ] Layout is responsive across devices
- [ ] No references to old Lanyon theme
- [ ] Cards and components use design tokens

## Success Criteria

- [ ] Layout utilities created (container, grid, spacing)
- [ ] Component library established (cards, buttons, badges)
- [ ] Header component with navigation
- [ ] Footer component with links
- [ ] New default layout (no sidebar)
- [ ] Updated page and post layouts
- [ ] Lanyon theme completely removed
- [ ] Mobile-first responsive design works
- [ ] All components use design tokens
- [ ] Site builds without errors
- [ ] Professional, modern aesthetic achieved

## Output

**Created Files:**
- `_sass/_layout.scss` - Layout utilities
- `_sass/_components.scss` - Component library
- `_includes/header.html` - Site header
- `_includes/footer.html` - Site footer

**Modified Files:**
- `_layouts/default.html` - New base layout
- `_layouts/page.html` - Updated page layout
- `_layouts/post.html` - Updated post layout
- `assets/css/main.scss` - Import new partials

**Deleted Files:**
- `_includes/sidebar.html` - Lanyon sidebar
- `public/css/lanyon.css` - Lanyon theme
- `public/css/poole.css` - Poole base

**Git Commits:**
- Component library and layouts

---

**Estimated Time:** 90-120 minutes
**Dependencies:** phase2-foundation-PLAN.md complete
**Next Plan:** phase2-prototype-PLAN.md (working example pages)

**Notes:**
- Site now has structure but content pages need updating
- Components are functional but not polished (next plan)
- Focus on getting structure right
- Lanyon theme completely removed
- Modern, clean foundation established
