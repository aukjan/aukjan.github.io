<objective>
Integrate portfolio into site navigation, implement SEO for case studies, add final polish, and verify complete Phase 4 deliverables.
</objective>

<execution_context>
@phase4-CONTEXT.md - Portfolio should be prominent in navigation
@_includes/header.html - Current nav: Home, About, Expertise, Contact, Articles
@_includes/footer.html - Footer navigation structure
@_includes/head.html - SEO meta tags structure from Phase 3
</execution_context>

<context>
**What we're completing:**
- Add "Portfolio" to main navigation (header and footer)
- Implement SEO meta tags for portfolio pages
- Add JSON-LD structured data for case studies
- Final accessibility and responsive testing
- Documentation updates

**Current navigation:**
- Header: Home, About, Expertise, Contact, Articles
- Footer: Same as header + GitHub link

**SEO requirements:**
- Unique meta descriptions for portfolio page
- Individual meta descriptions for each case study
- Open Graph tags for social sharing
- JSON-LD WorkExample schema for case studies
- Portfolio page included in sitemap (automatic via jekyll-sitemap)

**Key decisions:**
- Portfolio goes in main nav (between Expertise and Contact)
- Case studies get WorkExample structured data
- Meta descriptions written for all 7 projects + main page
</context>

<tasks>

## Task 1: Add Portfolio to Header Navigation

**File:** `_includes/header.html`

Update navigation to include Portfolio link:

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
        <a href="/expertise" class="nav-link">Expertise</a>
        <a href="/portfolio" class="nav-link">Portfolio</a>
        <a href="/contact" class="nav-link">Contact</a>
        <a href="/archive" class="nav-link">Articles</a>
      </nav>
    </div>
  </div>
</header>
```

**Why:** Portfolio positioned between Expertise and Contact—logical flow from skills to demonstrated work to connection.

**Verification:**
- [ ] "Portfolio" link appears in header
- [ ] Link navigates to `/portfolio/`
- [ ] Active state styling works (if implemented)
- [ ] Navigation works on mobile (if responsive nav exists)

## Task 2: Add Portfolio to Footer Navigation

**File:** `_includes/footer.html`

Update footer navigation to include Portfolio:

```html
<footer class="site-footer">
  <div class="container">
    <nav class="footer-nav">
      <a href="/" class="footer-link">Home</a>
      <a href="/about" class="footer-link">About</a>
      <a href="/expertise" class="footer-link">Expertise</a>
      <a href="/portfolio" class="footer-link">Portfolio</a>
      <a href="/contact" class="footer-link">Contact</a>
      <a href="/archive" class="footer-link">Articles</a>
      <a href="{{ site.github.repo }}" target="_blank" rel="noopener noreferrer" class="footer-link">GitHub</a>
    </nav>
    <p class="footer-credit">
      &copy; {{ 'now' | date: '%Y' }} {{ site.author.name }}. Built with Jekyll.
    </p>
  </div>
</footer>
```

**Why:** Consistent navigation across header and footer improves usability.

**Verification:**
- [ ] "Portfolio" link appears in footer
- [ ] Link navigates to `/portfolio/`
- [ ] Footer navigation remains properly styled

## Task 3: Add SEO Meta Tags to Portfolio Page

**File:** `portfolio.html`

Update front matter with comprehensive SEO:

```yaml
---
layout: page
title: Portfolio
description: Career timeline showcasing product and technical leadership across diverse contexts. From scaling platforms to product pivots, security architecture to marketplace growth—demonstrating versatility and dual capability.
permalink: /portfolio/
---
```

**Why:** Meta description optimized for search engines and social sharing, highlighting key value proposition.

**Verification:**
- [ ] Meta description appears in HTML `<head>`
- [ ] Description under 160 characters
- [ ] Open Graph tags render (inherited from page layout)

## Task 4: Add SEO Meta Tags to Case Study Front Matter

Update each portfolio item front matter to include SEO fields:

**File:** `_portfolio/01-platform-scaling.md`

```yaml
---
layout: portfolio
title: "Platform Scaling for Hypergrowth"
description: "How I rebuilt an e-commerce platform architecture to handle 10x user growth while reducing infrastructure costs 40% and achieving 99.9% uptime."
date: 2023-06-01
role: "Chief Technology Officer"
company_context: "E-commerce Startup (Series B, 50-person team)"
category: technical
summary: "Rebuilt architecture to handle 10x user growth while reducing infrastructure costs by 40% and improving reliability to 99.9% uptime."
---
```

**Repeat for all 7 case studies:**

**02-security-architecture.md:**
```yaml
description: "Leading enterprise security transformation: achieving SOC 2 Type II certification and implementing zero-trust architecture across 50+ microservices."
```

**03-data-infrastructure.md:**
```yaml
description: "Building real-time data pipelines that reduced latency from hours to seconds while processing 10M+ daily events for customer analytics."
```

**04-technical-debt-turnaround.md:**
```yaml
description: "Systematically reducing technical debt 60% while maintaining product velocity, transforming a legacy codebase from liability to asset."
```

**05-product-market-fit-pivot.md:**
```yaml
description: "Leading product pivot that discovered new market segment, growing monthly active users 5x and achieving product-market fit in 6 months."
```

**06-ux-transformation.md:**
```yaml
description: "Redesigning complex enterprise product with user-centered design, reducing onboarding time 60% and increasing feature adoption 45%."
```

**07-marketplace-growth-strategy.md:**
```yaml
description: "Scaling marketplace supply side from 500 to 5,000 active sellers while maintaining quality through algorithmic scoring and seller success programs."
```

**Why:** Unique meta descriptions for each case study improve SEO and social sharing. Descriptions focus on outcomes and measurable impact.

**Verification:**
- [ ] All 7 case studies have `description` field
- [ ] Descriptions under 160 characters
- [ ] Descriptions highlight measurable outcomes
- [ ] No two descriptions are identical

## Task 5: Implement JSON-LD Structured Data for Case Studies

**File:** `_layouts/portfolio.html`

Add structured data script in the `<head>` section:

Update layout to include structured data:

```html
---
layout: default
---

<!-- JSON-LD Structured Data for Case Study -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "CreativeWork",
  "name": "{{ page.title }}",
  "description": "{{ page.description | default: page.summary }}",
  "author": {
    "@type": "Person",
    "name": "{{ site.author.name }}",
    "jobTitle": "{{ page.role }}",
    "url": "{{ site.url }}"
  },
  "datePublished": "{{ page.date | date: '%Y-%m-%d' }}",
  "about": {
    "@type": "Thing",
    "name": "{{ page.category | capitalize }} Leadership Case Study"
  },
  "keywords": "{{ page.category }}, leadership, {{ page.role | downcase }}, case study",
  "url": "{{ site.url }}{{ page.url }}"
}
</script>

<article class="portfolio-case-study">
  <div class="container container-narrow">
    <!-- ... rest of layout ... -->
  </div>
</article>
```

**Why:** Structured data helps search engines understand case study content and can enable rich results in search. CreativeWork schema appropriate for case studies.

**Verification:**
- [ ] JSON-LD script renders on case study pages
- [ ] Valid JSON (no syntax errors)
- [ ] All fields populated correctly
- [ ] Test with Google's Rich Results Test (https://search.google.com/test/rich-results)

## Task 6: Update Homepage to Feature Portfolio

**File:** `index.html`

Add portfolio CTA to homepage (add after Expertise section, before final CTA):

```html
<!-- Portfolio Section -->
<section class="section">
  <div class="container">
    <h2 class="section-title">Proven Track Record</h2>
    <p class="section-intro">
      From platform scaling to product pivots, security architecture to marketplace growth—see how I've brought the right amount of structure to growing organizations.
    </p>
    <div class="cta-group">
      <a href="/portfolio" class="btn btn-primary">View Portfolio Timeline</a>
    </div>
  </div>
</section>
```

**Why:** Homepage should drive traffic to portfolio. Simple CTA section increases portfolio visibility.

**Verification:**
- [ ] Portfolio section appears on homepage
- [ ] Section styling matches existing homepage design
- [ ] Button navigates to `/portfolio/`
- [ ] Copy emphasizes versatility and structure theme

## Task 7: Final Accessibility Testing

**Keyboard Navigation Test:**
```
Tab through portfolio timeline:
- [ ] All project cards focusable
- [ ] Focus indicators clearly visible
- [ ] Tab order logical (top to bottom, year by year)
- [ ] "Read full story" links activate with Enter
- [ ] Breadcrumb navigation accessible
```

**Screen Reader Test (VoiceOver/NVDA if available):**
```
Portfolio page:
- [ ] Timeline announced as landmark
- [ ] Year markers announced as headings
- [ ] Projects announced as articles
- [ ] Badge categories announced
- [ ] Time elements read correctly

Case study page:
- [ ] Breadcrumb navigation clear
- [ ] Heading hierarchy logical
- [ ] Content sections properly structured
- [ ] Footer CTAs accessible
```

**Color Contrast:**
- [ ] Timeline dots meet 3:1 contrast (non-text)
- [ ] All text meets 4.5:1 contrast (WCAG AA)
- [ ] Badge text legible on badge backgrounds
- [ ] Link colors meet contrast requirements

## Task 8: Responsive Testing Across Devices

**Desktop (≥1024px):**
- [ ] Timeline alternates left/right properly
- [ ] Cards don't exceed container width
- [ ] Year markers centered
- [ ] Hover effects work smoothly
- [ ] Typography scales appropriately

**Tablet (768px-1023px):**
- [ ] Timeline still alternates (smaller cards)
- [ ] Cards readable and well-spaced
- [ ] No layout breaking
- [ ] Touch targets adequate (44px+)

**Mobile (<768px):**
- [ ] Timeline line moves to left
- [ ] All cards stack vertically
- [ ] No horizontal scroll
- [ ] Year markers align with line
- [ ] Text remains readable
- [ ] Footer buttons stack properly

**Test on actual devices if possible:**
- [ ] iPhone Safari
- [ ] Android Chrome
- [ ] iPad Safari
- [ ] Desktop Chrome/Firefox/Safari

## Task 9: Update Site Documentation

**File:** `README.md`

Add Portfolio section to README:

```markdown
## Content Structure

### Portfolio

Portfolio case studies are managed as a Jekyll collection in `_portfolio/`.

**Adding a new case study:**

1. Create a markdown file in `_portfolio/`: `YYYY-project-slug.md`
2. Add front matter:
   ```yaml
   ---
   layout: portfolio
   title: "Project Title"
   description: "SEO description (under 160 chars)"
   date: YYYY-MM-DD
   role: "Your Role"
   company_context: "Generic company description"
   category: technical # or 'product'
   summary: "1-2 sentence summary with measurable outcome"
   ---
   ```
3. Follow 6-part case study structure:
   - The Context (1-2 paragraphs)
   - The Challenge (2-3 paragraphs)
   - Your Approach (3-4 paragraphs)
   - Key Decisions (2-3 paragraphs)
   - The Outcome (2-3 paragraphs)
   - What You Learned (1-2 paragraphs)
4. Target 1200-1800 words per case study
5. Build and test locally before committing

**Portfolio displays at:** `/portfolio/`
**Individual case studies at:** `/portfolio/project-slug/`
```

**File:** `_sass/README.md`

Add Timeline Component section:

```markdown
## Timeline Component

**File:** `_sass/_timeline.scss`

Vertical timeline for portfolio with alternating left/right cards (desktop) and stacked layout (mobile).

### Usage

```html
<section class="timeline" aria-label="Career timeline">
  <div class="timeline-year"><h2>2024</h2></div>
  <ol class="timeline-list">
    <li class="timeline-item">
      <article class="timeline-card">
        <time datetime="2024-03">March 2024</time>
        <h3>Project Title</h3>
        <!-- card content -->
      </article>
    </li>
  </ol>
</section>
```

### Key Classes

- `.timeline` - Container with center line (desktop) or left line (mobile)
- `.timeline-year` - Year marker with dot on timeline
- `.timeline-list` - Ordered list (`<ol>`) containing projects
- `.timeline-item` - List item with flexbox positioning
- `.timeline-card` - Project card extending base card component

### Responsive Behavior

- **Desktop (≥768px):** Alternating left/right, center line
- **Mobile (<768px):** Stacked right, left line at 20px

### Accessibility

- Semantic HTML: `<section>`, `<ol>`, `<article>`
- Proper heading hierarchy (year = h2, project = h3)
- ARIA label on timeline section
- Timeline line decorative (CSS only)
```

## Task 10: Final Verification Build

**Build and serve locally:**
```bash
bundle exec jekyll clean
bundle exec jekyll build
bundle exec jekyll serve
```

**Comprehensive verification:**

**Site-wide:**
- [ ] No Jekyll build warnings or errors
- [ ] All pages load successfully
- [ ] Navigation updated everywhere
- [ ] No broken links
- [ ] No 404 errors

**Portfolio page (`/portfolio/`):**
- [ ] Timeline renders correctly
- [ ] 7 projects displayed
- [ ] Chronological order correct
- [ ] Badges show correct colors
- [ ] All links functional

**Case study pages:**
- [ ] All 7 individual pages load
- [ ] Layout renders consistently
- [ ] Breadcrumb navigation works
- [ ] Structured data in HTML
- [ ] Meta descriptions present
- [ ] Footer buttons functional

**SEO verification:**
- [ ] View page source: meta tags present
- [ ] JSON-LD validates (Google Rich Results Test)
- [ ] Sitemap includes portfolio pages (`/sitemap.xml`)
- [ ] robots.txt allows portfolio pages

**Performance:**
- [ ] Page load times reasonable (<3s)
- [ ] Images optimized (if any added later)
- [ ] No console errors
- [ ] CSS compiled and minified

</tasks>

<verification>
After completing all tasks:

1. **Navigation Updates:**
   - [ ] Portfolio link in header (between Expertise and Contact)
   - [ ] Portfolio link in footer
   - [ ] Links navigate to `/portfolio/` correctly
   - [ ] Navigation styling consistent

2. **SEO Implementation:**
   - [ ] Portfolio page has meta description
   - [ ] All 7 case studies have unique descriptions
   - [ ] JSON-LD structured data on case study pages
   - [ ] All descriptions under 160 characters
   - [ ] Keywords relevant and strategic

3. **Homepage Integration:**
   - [ ] Portfolio CTA section added
   - [ ] Copy emphasizes versatility theme
   - [ ] Button navigates to portfolio
   - [ ] Section styling matches homepage

4. **Accessibility:**
   - [ ] Keyboard navigation works throughout
   - [ ] Focus indicators visible
   - [ ] Screen reader testing passed (if available)
   - [ ] Color contrast meets WCAG AA
   - [ ] Semantic HTML proper

5. **Responsive Design:**
   - [ ] Desktop layout correct (alternating)
   - [ ] Tablet layout correct
   - [ ] Mobile layout correct (stacked)
   - [ ] No horizontal scroll on any device
   - [ ] Touch targets adequate

6. **Documentation:**
   - [ ] README updated with portfolio section
   - [ ] Design system docs updated with timeline component
   - [ ] Clear instructions for adding case studies
   - [ ] Code examples provided

7. **Technical Quality:**
   - [ ] Jekyll builds without errors
   - [ ] All links functional
   - [ ] No console errors
   - [ ] Sitemap includes portfolio pages
   - [ ] Structured data validates

</verification>

<success_criteria>

- [ ] Portfolio fully integrated into site navigation
- [ ] Header and footer include Portfolio links
- [ ] SEO meta tags implemented for all portfolio pages
- [ ] JSON-LD structured data on case studies
- [ ] Homepage features portfolio CTA section
- [ ] All accessibility standards met (WCAG AA)
- [ ] Responsive design verified across devices
- [ ] Documentation updated comprehensively
- [ ] Jekyll builds cleanly without errors
- [ ] All links functional, no 404s
- [ ] Portfolio discoverable via sitemap

**Visual success:** Portfolio seamlessly integrated into site. Navigation clearly shows Portfolio option. Homepage drives traffic with compelling CTA. Timeline looks professional across all devices.

**Technical success:** SEO implementation complete. Structured data validates. Accessibility standards met. Documentation enables future content additions. Build process clean.

**Phase 4 Complete:** Portfolio & Case Studies phase fully delivered. Timeline infrastructure built, 7 placeholder case studies created, navigation integrated, SEO implemented, documentation updated. Site now showcases dual product/technical capability through career timeline.

</success_criteria>

<output>
**Files created/modified:**
1. `_includes/header.html` - Added Portfolio to navigation
2. `_includes/footer.html` - Added Portfolio to footer
3. `portfolio.html` - Added SEO meta description
4. `_portfolio/*.md` (7 files) - Added description fields for SEO
5. `_layouts/portfolio.html` - Added JSON-LD structured data
6. `index.html` - Added portfolio CTA section
7. `README.md` - Added portfolio documentation
8. `_sass/README.md` - Added timeline component docs

**Atomic commits:**
1. `feat(phase4-navigation): add Portfolio to header and footer navigation`
2. `feat(phase4-seo): implement meta descriptions for portfolio pages`
3. `feat(phase4-seo): add JSON-LD structured data for case studies`
4. `feat(phase4-integration): add portfolio CTA to homepage`
5. `docs(phase4-navigation): update README and design system docs`
6. `test(phase4-navigation): comprehensive accessibility and responsive testing`

**Phase 4 Status:** ✅ COMPLETE

Portfolio timeline showcases 7 diverse projects demonstrating versatility across product and technical domains. Infrastructure ready for real content replacement.
</output>
