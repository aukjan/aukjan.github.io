# Phase 2 Plan 3: Prototype Pages & Design Validation

## Objective

Create working prototype pages demonstrating the design system in action. Update existing pages (index, about, archive) to use new components and validate that the design achieves "professional but approachable" aesthetic with room for personality and authenticity.

## Execution Context

**Related Files:**
- @index.html (homepage - to redesign)
- @about.md (about page - to update)
- @archive.md (articles listing - to update)
- @404.html (error page - to update)

**Reference Materials:**
- @.planning/phases/02-design-system-architecture/design-notes.md (old design structure)
- @.planning/phases/02-design-system-architecture/phase2-CONTEXT.md (design vision)
- @.planning/phases/02-design-system-architecture/phase2-RESEARCH.md (portfolio trends)

**Dependencies:**
- phase2-foundation-PLAN.md complete (design tokens)
- phase2-components-PLAN.md complete (components and layouts)

## Context

**Current State:**
- Design system foundation established (tokens, typography)
- Component library created (cards, buttons, layout)
- Layouts replaced (default, page, post)
- Existing pages use old structure

**Goal:**
Demonstrate design system working in practice:
- Modern, professional homepage with clear value proposition
- Updated about page showing personality and authenticity
- Clean article archive with card-based layout
- Validate "professional but approachable" feel
- Ensure design works with actual content

**Vision:**
"Working examples demonstrating the system in practice, ready to fill with content." Pages should feel structured but not sterile, with clear hierarchy that guides naturally.

## Tasks

### Task 1: Redesign Homepage

**What:** Create modern homepage showcasing executive presence

**How:**
1. Read current `index.html`
2. Replace with new structure using components:

   ```html
   ---
   layout: default
   title: Home
   ---

   <!-- Hero Section -->
   <section class="hero">
     <div class="container">
       <div class="hero-content">
         <h1 class="hero-title">Aukjan van Belkum</h1>
         <p class="hero-subtitle">Chief Technology Officer | Strategic Leader | Cybersecurity Visionary</p>
         <p class="hero-description">
           Driving global cybersecurity innovation through strategic leadership,
           technical excellence, and customer-centric product vision.
         </p>
       </div>
     </div>
   </section>

   <!-- Introduction -->
   <section class="section">
     <div class="container container-md">
       <div class="intro-content">
         <h2>Strategic Technology Leadership</h2>
         <p class="lead">
           Transforming complex technical challenges into business opportunities
           through a unique blend of CTO technical depth and CPO customer empathy.
         </p>
         <p>
           With extensive experience in global cybersecurity, I specialize in
           building scalable platforms, leading distributed teams, and aligning
           technology strategy with business objectives to drive measurable impact.
         </p>
       </div>
     </div>
   </section>

   <!-- Featured Areas (Cards) -->
   <section class="section" style="background-color: var(--color-background);">
     <div class="container">
       <h2 style="text-align: center; margin-bottom: var(--space-2xl);">
         Areas of Expertise
       </h2>
       <div class="grid grid-cols-3">
         <div class="card">
           <h3 class="card-title">Engineering Leadership</h3>
           <p class="card-content">
             Building and scaling high-performing engineering teams across
             multiple geographies, fostering innovation and technical excellence.
           </p>
         </div>
         <div class="card">
           <h3 class="card-title">Product Vision & Strategy</h3>
           <p class="card-content">
             Defining product roadmaps that balance customer needs, market
             opportunities, and technical feasibility for maximum impact.
           </p>
         </div>
         <div class="card">
           <h3 class="card-title">Cybersecurity Innovation</h3>
           <p class="card-content">
             Architecting secure, scalable platforms that protect organizations
             while enabling business growth and digital transformation.
           </p>
         </div>
       </div>
     </div>
   </section>

   <!-- Call to Action -->
   <section class="section">
     <div class="container container-sm" style="text-align: center;">
       <h2>Let's Connect</h2>
       <p class="lead">
         Interested in discussing technology leadership, cybersecurity strategy,
         or potential collaboration opportunities?
       </p>
       <div style="margin-top: var(--space-lg);">
         <a href="/about" class="btn btn-primary">Learn More About My Work</a>
         <a href="{{ site.author.url }}" class="btn btn-secondary" target="_blank" rel="noopener noreferrer">Connect on LinkedIn</a>
       </div>
     </div>
   </section>
   ```

3. Add hero styles to `_sass/_components.scss`:
   ```scss
   /* Hero Section */
   .hero {
     background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
     color: var(--color-surface);
     padding: var(--space-3xl) 0;
     text-align: center;
   }

   .hero-content {
     max-width: 800px;
     margin: 0 auto;
   }

   .hero-title {
     font-size: var(--text-5xl);
     font-weight: var(--font-bold);
     margin-bottom: var(--space-md);
     color: var(--color-surface);

     @media (max-width: 767px) {
       font-size: var(--text-4xl);
     }
   }

   .hero-subtitle {
     font-size: var(--text-2xl);
     font-weight: var(--font-medium);
     font-family: var(--font-sans);
     margin-bottom: var(--space-lg);
     color: rgba(255, 255, 255, 0.9);

     @media (max-width: 767px) {
       font-size: var(--text-xl);
     }
   }

   .hero-description {
     font-size: var(--text-lg);
     line-height: var(--leading-relaxed);
     color: rgba(255, 255, 255, 0.85);
     max-width: 600px;
     margin: 0 auto;
   }

   .intro-content {
     text-align: center;

     h2 {
       margin-bottom: var(--space-lg);
     }

     p {
       max-width: 70ch;
       margin-left: auto;
       margin-right: auto;
     }
   }
   ```

**Verification:**
- [ ] Homepage redesigned with modern structure
- [ ] Hero section with gradient background
- [ ] Clear value proposition
- [ ] Card-based expertise section
- [ ] Call to action with buttons
- [ ] Hero styles added

### Task 2: Update About Page

**What:** Update about.md to showcase personality

**How:**
1. Read current `about.md`
2. Update front matter and structure:
   ```markdown
   ---
   layout: page
   title: About
   subtitle: Blending Technical Depth with Customer Empathy
   ---

   ## Who I Am

   I'm a technology leader with a unique perspective shaped by dual roles as
   both CTO (Chief Technology Officer) and CPO (Chief Product Officer). This
   combination gives me the rare ability to bridge technical excellence with
   deep customer understanding.

   ### My Journey

   [Keep existing content but reformat with clear hierarchy]

   **Current Focus:**
   - Leading global cybersecurity platform development
   - Building and scaling distributed engineering teams
   - Driving product-market fit through data-driven decisions
   - Aligning technology strategy with business objectives

   ## What Drives Me

   I believe the best technology solutions come from understanding both the
   technical landscape AND the human needs behind them. This philosophy guides
   my approach to:

   - **Engineering Leadership**: Building teams that deliver excellence
   - **Product Strategy**: Creating solutions that users actually want
   - **Technical Innovation**: Architecting systems that scale and adapt
   - **Strategic Thinking**: Aligning technology with business goals

   ---

   *Want to connect? Find me on [LinkedIn]({{ site.author.url }}) or explore
   my [thought leadership articles](/archive).*
   ```

**Verification:**
- [ ] About page uses page layout
- [ ] Clear structure with headings
- [ ] Personality and authenticity present
- [ ] Professional yet approachable tone
- [ ] Call to action at end

### Task 3: Update Archive Page

**What:** Redesign article listing with cards

**How:**
1. Read current `archive.md`
2. Replace with card-based layout:
   ```html
   ---
   layout: page
   title: Thought Leadership
   subtitle: Articles on Technology, Product Strategy, and Leadership
   ---

   <div class="post-list">
     {% if site.posts.size == 0 %}
       <div style="text-align: center; padding: var(--space-3xl) 0;">
         <p class="lead">Coming soon.</p>
         <p>
           This section will feature articles on tech trends, product innovation,
           scaling teams, and strategic leadership.
         </p>
       </div>
     {% else %}
       <div class="grid grid-cols-2">
         {% for post in site.posts %}
           <article class="card">
             <h3 class="card-title">
               <a href="{{ post.url }}" style="text-decoration: none; color: inherit;">
                 {{ post.title }}
               </a>
             </h3>
             <div class="post-meta">
               <time datetime="{{ post.date | date_to_xmlschema }}">
                 {{ post.date | date: "%B %d, %Y" }}
               </time>
             </div>
             {% if post.excerpt %}
               <p class="card-content">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
             {% endif %}
             <a href="{{ post.url }}" class="btn btn-secondary" style="margin-top: var(--space-sm);">
               Read More →
             </a>
           </article>
         {% endfor %}
       </div>
     {% endif %}
   </div>
   ```

**Verification:**
- [ ] Archive uses card layout
- [ ] Empty state for no posts
- [ ] Post cards display title, date, excerpt
- [ ] Read more buttons included
- [ ] Grid layout responsive

### Task 4: Update 404 Error Page

**What:** Friendly 404 page with navigation

**How:**
1. Read current `404.html`
2. Update with modern structure:
   ```html
   ---
   layout: default
   title: "404: Page not found"
   permalink: /404.html
   ---

   <div class="section">
     <div class="container container-sm" style="text-align: center;">
       <h1 style="font-size: var(--text-5xl); margin-bottom: var(--space-md);">
         404
       </h1>
       <p class="lead">
         Sorry, we couldn't find that page.
       </p>
       <p style="color: var(--color-text-muted); margin-bottom: var(--space-xl);">
         The page you're looking for might have been moved or no longer exists.
       </p>
       <div style="margin-top: var(--space-lg);">
         <a href="/" class="btn btn-primary">Go Home</a>
         <a href="/archive" class="btn btn-secondary">View Articles</a>
       </div>
     </div>
   </div>
   ```

**Verification:**
- [ ] 404 page updated
- [ ] Clear, friendly message
- [ ] Navigation buttons provided
- [ ] Professional appearance

### Task 5: Add Visual Polish

**What:** Final touches to enhance professional feel

**How:**
1. Add subtle enhancements to `_sass/_components.scss`:

   ```scss
   /* Link Hover Effects - Subtle */
   a {
     transition: color var(--transition-fast);
   }

   /* Card Hover - Gentle lift */
   .card {
     transition: transform var(--transition-base), box-shadow var(--transition-base);

     &:hover {
       transform: translateY(-2px);
     }
   }

   /* Focus Styles - Accessibility */
   .btn:focus-visible {
     outline: 3px solid var(--color-primary-light);
     outline-offset: 2px;
   }

   /* Smooth Scroll */
   html {
     scroll-behavior: smooth;
   }
   ```

2. Verify all interactions feel smooth and intentional
3. Keep animations subtle (professional, not flashy)

**Verification:**
- [ ] Subtle hover effects added
- [ ] Card lift on hover
- [ ] Button focus styles clear
- [ ] Smooth scrolling enabled
- [ ] Animations feel professional

### Task 6: Accessibility Audit

**What:** Verify WCAG 2.1 AA compliance

**How:**
1. Test color contrast (all combinations):
   - Text on backgrounds
   - Links on backgrounds
   - Button text on button backgrounds
   - Use WebAIM Contrast Checker

2. Verify keyboard navigation:
   - Tab through all interactive elements
   - Focus indicators visible
   - Logical tab order

3. Check semantic HTML:
   - Proper heading hierarchy (h1 → h2 → h3)
   - Landmarks (<header>, <main>, <footer>, <nav>)
   - Alt text on images (if any added later)

4. Test with screen reader (if available):
   - Content makes sense when read aloud
   - Navigation is clear

5. Document any issues and fix immediately

**Verification:**
- [ ] All text meets 4.5:1 contrast (WCAG AA)
- [ ] Keyboard navigation works
- [ ] Focus indicators visible
- [ ] Heading hierarchy correct
- [ ] Landmarks properly used
- [ ] No accessibility blockers

### Task 7: Cross-Browser Testing

**What:** Ensure design works across browsers

**How:**
1. Test in multiple browsers:
   - Chrome/Edge (Chromium)
   - Firefox
   - Safari (if on macOS)

2. Check for:
   - CSS custom properties support (all modern browsers)
   - Layout consistency
   - Font rendering
   - Color accuracy
   - Responsive behavior

3. Fix any browser-specific issues

**Verification:**
- [ ] Works in Chrome/Edge
- [ ] Works in Firefox
- [ ] Works in Safari (if tested)
- [ ] No layout breaks
- [ ] Fonts render correctly

### Task 8: Responsive Testing

**What:** Verify mobile-first design across devices

**How:**
1. Test at multiple widths:
   - Mobile: 320px, 375px, 414px
   - Tablet: 768px, 1024px
   - Desktop: 1280px, 1920px

2. Verify:
   - Text remains readable (no tiny text)
   - Touch targets adequate (44px+ for buttons)
   - No horizontal scroll
   - Images scale properly
   - Navigation accessible at all sizes
   - Hero section works on mobile

3. Test actual devices if available

**Verification:**
- [ ] Mobile (320px+) works well
- [ ] Tablet layout appropriate
- [ ] Desktop optimal
- [ ] No horizontal scroll
- [ ] Touch targets adequate (44px+)
- [ ] Content readable at all sizes

### Task 9: Visual Design Validation

**What:** Confirm "professional but approachable" achieved

**How:**
1. Review each page against vision criteria:

   **Professional:**
   - [ ] Executive presence clear
   - [ ] Clean, organized layout
   - [ ] Consistent visual language
   - [ ] Credible, polished aesthetic

   **Approachable:**
   - [ ] Warm color palette (not corporate gray)
   - [ ] Readable, human-friendly typography
   - [ ] Room for personality and authenticity
   - [ ] Not sterile or rigid

   **Hierarchy:**
   - [ ] Clear without being rigid
   - [ ] Guides eye naturally
   - [ ] Important elements stand out
   - [ ] Content flows logically

2. If any criteria fails, adjust design
3. Get feedback if possible (show to someone)

**Verification:**
- [ ] Professional presence established
- [ ] Warm and approachable feel
- [ ] Clear, natural hierarchy
- [ ] Room for authenticity
- [ ] Overall aesthetic on target

### Task 10: Document Design System

**What:** Update design system documentation

**How:**
1. Update `_sass/README.md` with:
   - Component usage examples
   - Layout patterns
   - When to use each component
   - Accessibility notes
   - Responsive behavior guide

2. Add design decisions and rationale:
   - Why Montserrat + Merriweather
   - Color palette reasoning
   - Spacing system logic
   - Component patterns

**Verification:**
- [ ] README updated with components
- [ ] Usage examples provided
- [ ] Design decisions documented
- [ ] Accessibility guidance included

### Task 11: Commit Prototype Pages

**What:** Commit all prototype work

**How:**
1. Review all changes
2. Stage files:
   - Updated `index.html`
   - Updated `about.md`
   - Updated `archive.md`
   - Updated `404.html`
   - Updated `_sass/` files with hero and polish
   - Updated `_sass/README.md`

3. Commit:
   ```
   feat(phase2-prototype): create prototype pages demonstrating design

   Update existing pages with new design system:
   - Modern homepage with hero, expertise cards, clear CTA
   - Updated about page with personality and structure
   - Card-based archive for article listings
   - Friendly 404 error page
   - Subtle hover effects and polish
   - Complete accessibility audit (WCAG 2.1 AA compliant)
   - Cross-browser and responsive testing

   Design achieves "professional but approachable" aesthetic with
   warm colors, readable typography, and room for authenticity.

   Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
   ```

**Verification:**
- [ ] All files staged
- [ ] Commit message complete
- [ ] Site builds successfully
- [ ] Design validated

## Verification

**Automated Checks:**
```bash
# Pages updated
test -f index.html && grep -q "hero" index.html && echo "✓ homepage redesigned"
test -f about.md && grep -q "subtitle:" about.md && echo "✓ about page updated"
test -f archive.md && grep -q "card" archive.md && echo "✓ archive uses cards"

# Site builds
bundle exec jekyll build && echo "✓ site builds successfully"

# Accessibility
grep -r "focus-visible" _sass/ && echo "✓ focus styles present"
```

**Manual Checks:**
- [ ] Homepage feels modern and professional
- [ ] About page shows personality
- [ ] Archive layout is clean
- [ ] 404 page is friendly
- [ ] Design feels cohesive across pages
- [ ] "Professional but approachable" achieved
- [ ] WCAG 2.1 AA compliant
- [ ] Responsive across devices
- [ ] Cross-browser compatible

## Success Criteria

- [ ] Homepage redesigned with modern structure
- [ ] About page updated with personality
- [ ] Archive uses card-based layout
- [ ] 404 page friendly and helpful
- [ ] Subtle polish and hover effects
- [ ] WCAG 2.1 AA accessibility verified
- [ ] Cross-browser testing complete
- [ ] Responsive design validated
- [ ] "Professional but approachable" feel achieved
- [ ] Design system documented
- [ ] All pages use components and tokens
- [ ] Site ready for content creation (Phase 3)

## Output

**Modified Files:**
- `index.html` - Modern homepage
- `about.md` - Updated about page
- `archive.md` - Card-based archive
- `404.html` - Friendly error page
- `_sass/_components.scss` - Hero and polish styles
- `_sass/README.md` - Updated documentation

**Git Commits:**
- Prototype pages demonstrating design system

**Design Validation:**
- Professional executive presence ✓
- Warm and approachable feel ✓
- Clear, natural hierarchy ✓
- Room for personality ✓
- WCAG 2.1 AA compliant ✓

---

**Estimated Time:** 90-120 minutes
**Dependencies:** phase2-foundation-PLAN.md and phase2-components-PLAN.md complete
**Next Phase:** Phase 3 - Core Pages & Content Structure

**Notes:**
- This completes Phase 2 - design system fully demonstrated
- Site now has professional, modern aesthetic
- All pages use design tokens and components
- Ready to create new content pages in Phase 3
- Design is validated and documented
- Foundation is solid for scaling to more pages

---

## Phase 2 Complete! 🎉

When all three plans are executed:
- ✅ Design tokens and typography system established
- ✅ Component library built and documented
- ✅ Prototype pages demonstrate design in action
- ✅ Professional but approachable aesthetic achieved
- ✅ WCAG 2.1 AA accessible
- ✅ Responsive and cross-browser compatible
- ✅ Ready for Phase 3 content creation

**Manual Steps After Completion:**
- Review site visually
- Get feedback from others if possible
- Make any final tweaks to colors/spacing
- Push to GitHub and verify GitHub Actions builds successfully
