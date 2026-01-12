# Roadmap: Personal Branding Site

## Milestone 1.0: CPO/CTO/CPTO Portfolio Launch

Transform existing Jekyll blog into modern personal branding site.

---

## Phase 1: Foundation & Cleanup ✅ COMPLETE (3/3 plans)

**Goal:** Clean existing codebase, fix critical issues, establish solid foundation

**Why First:** Must resolve security issues and technical debt before building new features. Clean slate enables faster development.

**Deliverables:**
- ✅ Remove all 2016 blog content and outdated posts
- ✅ Fix critical security issues (HTTP→HTTPS, target="_blank" vulnerabilities)
- ✅ Update deprecated Jekyll configuration (gems → plugins)
- ✅ Resolve dual architecture issue (removed standalone index.html, established Jekyll as single architecture)
- ✅ Add Gemfile with pinned dependencies
- ✅ Create GitHub Actions CI/CD workflow

**Plans:**
- ✅ phase1-cleanup-PLAN.md (complete)
- ✅ phase1-architecture-PLAN.md (complete)
- ✅ phase1-cicd-PLAN.md (complete)

**Research Completed:** ✅
- ✅ GitHub Actions official Jekyll deployment workflow
- ✅ Modern Jekyll + GitHub Pages best practices
- ✅ Ruby 3.1 with bundler caching strategies

**Validation:**
- ✅ Git working directory clean
- ✅ No HTTP references in codebase
- ✅ Jekyll architecture unified (single system)
- ✅ Gemfile created for reproducible builds
- ✅ GitHub Actions workflow created and committed
- ⚠️ Manual: Configure GitHub Pages settings (Settings → Pages → GitHub Actions)
- ⚠️ Manual: Verify first workflow run succeeds after push

---

## Phase 2: Design System & Architecture ✅ COMPLETE (3/3 plans)

**Goal:** Create modern, professional design system and site architecture

**Why Now:** Foundation is clean, need design direction before building content pages

**Deliverables:**
- ✅ Modern color palette and typography system
- ✅ Professional CSS architecture (Sass partials, design tokens)
- ✅ WCAG 2.1 AA accessibility compliance (+ prefers-reduced-motion)
- ✅ Responsive layout framework (container system, grid, flexbox)
- ✅ Component library (hero, cards, buttons, badges, headers, footer)
- ✅ New base layout replacing Lanyon theme
- ✅ Mobile-first responsive design
- ✅ Working example pages demonstrating components
- ✅ Homepage with hero section and expertise cards
- ✅ About page with personality and structure
- ✅ Archive page with card-based layout
- ✅ 404 error page redesigned
- ✅ Visual polish (hover effects, smooth scrolling, focus states)
- ✅ Cross-browser compatibility verified
- ✅ Responsive design tested across all breakpoints
- ✅ "Professional but approachable" aesthetic achieved
- ✅ Comprehensive design system documentation

**Plans:**
- ✅ phase2-foundation-PLAN.md (complete)
- ✅ phase2-components-PLAN.md (complete)
- ✅ phase2-prototype-PLAN.md (complete)

**Research Completed:** ✅
- ✅ Design system best practices (CSS custom properties)
- ✅ Accessibility standards (WCAG 2.1 AA)
- ✅ Modern typography pairing (Montserrat + Merriweather)
- ✅ Contemporary design trends for executive portfolios

**Validation:**
- ✅ Design system documented (_sass/README.md with 420+ lines)
- ✅ WCAG AA color contrast verified (all exceed 4.5:1, most exceed 7:1 AAA)
- ✅ Token-based architecture established (87 CSS custom properties)
- ✅ Components created with 118+ token references
- ✅ Responsive design with 8+ media queries
- ✅ Lanyon theme completely removed
- ✅ Example pages demonstrate components in use
- ✅ Professional, modern aesthetic achieved
- ✅ All 11 prototype plan tasks completed
- ✅ 25 total commits across Phase 2 (foundation + components + prototype)

---

## Phase 3: Core Pages & Content Structure ✅ COMPLETE (3/3 plans)

**Goal:** Build essential pages with proper information architecture

**Why Now:** Design system established, can now create content structure

**Deliverables:**
- ✅ Repositioning from cybersecurity to startup/scaleup growth leadership
- ✅ Modern homepage with clear value proposition (emphasis on bringing structure)
- ✅ About/Bio page blending CTO and CPO perspectives (growth journey)
- ✅ Expertise & Skills page organized by Strategic/Tactical/Technical levels
- ✅ Contact/Connect page with open, accessible tone
- ✅ Comprehensive SEO: sitemap.xml, robots.txt, Open Graph, structured data
- ✅ Updated navigation and site structure

**Plans:**
- ✅ phase3-repositioning-PLAN.md (complete)
- ✅ phase3-pages-PLAN.md (complete)
- ✅ phase3-seo-PLAN.md (complete)

**Context Captured:** ✅
- phase3-CONTEXT.md documents complete vision
- Key positioning shift identified and planned
- Multi-level expertise framework defined
- SEO strategy clarified (comprehensive, not minimal)

**Research Completed:** ✅
- ✅ SEO best practices for professional portfolios
- ✅ Open Graph and Twitter Card implementation
- ✅ JSON-LD structured data (schema.org Person)
- ✅ Sitemap generation with jekyll-sitemap plugin

**Validation:**
- ✅ Homepage and about page repositioned (phase3-repositioning)
- ✅ Clear startup/scaleup growth positioning established
- ✅ "Right amount of structure" philosophy emphasized
- ✅ Dual product + tech strength highlighted
- ✅ Cybersecurity repositioned as domain expertise only
- ✅ Expertise page demonstrates multi-level leadership (Strategic/Tactical/Technical)
- ✅ Contact page provides accessible connection methods
- ✅ Both pages use existing design system components
- ✅ jekyll-sitemap plugin enabled in _config.yml
- ✅ robots.txt created with sitemap reference
- ✅ Comprehensive meta tags (description, keywords, author, canonical)
- ✅ Open Graph tags for social sharing (LinkedIn, Facebook)
- ✅ Twitter Card tags for Twitter/X sharing
- ✅ JSON-LD Person schema implemented
- ✅ Unique meta descriptions on all 5 core pages
- ✅ Header navigation updated: Home, About, Expertise, Contact, Articles
- ✅ Footer navigation updated to match header
- ✅ SEO verified with local Docker build
- ✅ All SEO elements render correctly
- ✅ 14 total commits across Phase 3 (repositioning + pages + seo)

---

## Phase 4: Portfolio & Case Studies ✅ COMPLETE (3/3 plans)

**Goal:** Showcase technical and product achievements

**Why Now:** Core pages provide context, now demonstrate capabilities

**Deliverables:**
- ✅ Portfolio page with vertical timeline layout at /portfolio/
- ✅ Case study template with 6-part narrative structure
- ✅ 7 placeholder case studies (4 technical, 3 product)
- ✅ Timeline component with alternating cards (desktop → stacked mobile)
- ✅ Jekyll collection infrastructure (_portfolio/) for portfolio content
- ✅ SEO implementation with structured data (JSON-LD CreativeWork)
- ✅ Navigation integration (header + footer + homepage CTA)
- ✅ Comprehensive accessibility testing (WCAG 2.1 AA)
- ✅ Responsive testing across all devices
- ✅ Complete documentation (README + design system)

**Plans:**
- ✅ phase4-timeline-PLAN.md (complete - infrastructure, CSS, Jekyll collection)
- ✅ phase4-case-studies-PLAN.md (complete - layout template, 7 placeholder projects)
- ✅ phase4-navigation-PLAN.md (complete - nav integration, SEO, documentation)

**Context Captured:** ✅
- phase4-CONTEXT.md documents timeline vision
- Timeline-based portfolio showing versatility across contexts
- Dual product/technical capability emphasized
- Simple chronological scroll (no filtering)

**Research Completed:** ✅
- ✅ CSS vertical timeline implementation patterns
- ✅ Executive case study narrative structure (6-part framework)
- ✅ Jekyll collections for portfolio content
- ✅ Accessibility patterns for timeline components
- ✅ Responsive timeline layouts (alternating to stacked)
- ✅ Schema.org structured data for case studies
- ✅ SEO best practices for portfolio pages

**Validation:**
- ✅ Portfolio page at /portfolio/ showcases both technical and product work
- ✅ Timeline demonstrates versatility across diverse contexts
- ✅ Case studies use narrative-driven structure (Context → Challenge → Approach → Decisions → Outcome → Learned)
- ✅ 7 projects span 2020-2023 showing career progression
- ✅ Product/technical split: 3/4 (43%/57%)
- ✅ Category badges (Technical/Product) with color coding
- ✅ Portfolio in header navigation (between Expertise and Contact)
- ✅ Portfolio in footer navigation (same position)
- ✅ Homepage portfolio CTA ("Proven Track Record" section)
- ✅ SEO meta descriptions on all 8 portfolio pages (under 160 chars)
- ✅ JSON-LD structured data on all 7 case studies
- ✅ Sitemap includes all portfolio pages
- ✅ Mobile responsive with no horizontal scroll
- ✅ Accessibility standards met (semantic HTML, ARIA, keyboard nav)
- ✅ All 85 verification tests passed
- ✅ Documentation complete (README + _sass/README.md)
- ✅ 16 total commits across Phase 4 (timeline + case studies + navigation)

---

## Phase 4.1: Fix CSS URL for Sub Pages ✅ COMPLETE (1/1 plan)

**Goal:** Fix CSS loading issue on sub pages (urgent bug fix)

**Why Now:** Discovered after Phase 4 completion - CSS paths not working correctly for pages in subdirectories

**Depends on:** Phase 4

**Deliverables:**
- ✅ Fixed CSS links in _includes/head.html to use relative_url filter
- ✅ Fixed icon/favicon links to use relative_url filter
- ✅ Audited all other asset references (none found needing fixes)
- ✅ Local build and testing verified (5 representative pages)
- ✅ Pushed to GitHub and verified on live site
- ✅ All nested pages now load CSS correctly (no more 404 errors)
- ✅ Portfolio case study pages now fully styled

**Plans:**
- ✅ phase4.1-fix-asset-urls-PLAN.md (complete)

**Root Cause:**
Direct `{{ site.baseurl }}` concatenation generated relative paths on nested pages, causing 404 errors. Solution: Use Jekyll's `relative_url` filter for absolute path generation.

**Validation:**
- ✅ All 4 asset references fixed (2 CSS, 2 icons)
- ✅ Generated HTML contains absolute paths on all pages
- ✅ 5 pages tested locally (root + nested depths)
- ✅ 5 pages verified on live site (https://aukjan.vanbelkum.nl/)
- ✅ CSS files load with HTTP 200 status
- ✅ Portfolio case studies now professionally styled
- ✅ Comprehensive SUMMARY.md documentation created
- ✅ 5 total commits (one per task)

---

## Phase 4.2: Align Homepage with LinkedIn Profile (1/1 plan)

**Goal:** Update homepage content to match current LinkedIn profile positioning

**Why Now:** LinkedIn profile is more current than site; need consistency before Phase 5/6

**Depends on:** Phase 4.1

**Deliverables:**
- Add "builder at heart" identity to hero section
- Include "22 years building products" experience
- Reference cybersecurity as domain expertise
- Add email contact (aukjan@vanbelkum.nl) prominently
- Warm up tone to match LinkedIn's approachable style
- Maintain Phase 3 startup/scaleup positioning

**Plans:**
- [ ] phase4.2-linkedin-alignment-PLAN.md

**Context Captured:**
- phase4.2-CONTEXT.md documents alignment vision
- phase4.2-RESEARCH.md identifies 6 alignment gaps

**Validation:**
- Builder identity present in hero/intro
- 22 years experience mentioned
- Cybersecurity domain visible (but secondary)
- Email visible and clickable
- Tone warmer and approachable
- Design system unchanged
- Responsive across all breakpoints

---

## Phase 5: Thought Leadership Platform

**Goal:** Create content platform for articles and insights

**Why Now:** Foundation, design, and portfolio complete; ready for ongoing content

**Deliverables:**
- Thought leadership section/blog structure
- Article template optimized for readability
- Archive and categorization system
- RSS/Atom feed for subscribers
- 1-2 initial articles on relevant topics
- Social sharing integration

**Research Needed:** None - leveraging existing Jekyll blog patterns

**Validation:**
- Article platform functional and easy to use
- Content publishing workflow smooth
- Articles demonstrate expertise and thought leadership

---

## Phase 6: Polish & Launch

**Goal:** Final optimizations and public launch

**Why Last:** All content and features complete, ready for final quality pass

**Deliverables:**
- Performance optimization (image optimization, CSS minification)
- Cross-browser testing and fixes
- Final accessibility audit and remediation
- Meta tags and Open Graph for social sharing
- Analytics setup (if decided to include)
- Final content review and polish
- Launch announcement plan

**Research Needed:** 🔍
- Launch strategy for personal branding sites
- Social media announcement best practices

**Validation:**
- Site passes Lighthouse audit (90+ scores)
- Works across all major browsers
- Meets WCAG 2.1 AA accessibility
- Ready for public launch and promotion

---

## Future Enhancements (Post-1.0)

- Newsletter signup integration
- Video content embedding
- Interactive elements (contact forms)
- Speaking engagements page
- Blog commenting system
- Advanced analytics
- A/B testing platform

---

**Total Phases:** 6
**Estimated Timeline:** 6-8 weeks (depending on content creation velocity)
**Current Status:** Planning

---

*Roadmap created: 2026-01-08*
