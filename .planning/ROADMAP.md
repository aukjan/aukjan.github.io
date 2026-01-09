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

## Phase 3: Core Pages & Content Structure (3/3 plans)

**Goal:** Build essential pages with proper information architecture

**Why Now:** Design system established, can now create content structure

**Deliverables:**
- ✅ Repositioning from cybersecurity to startup/scaleup growth leadership
- Modern homepage with clear value proposition (emphasis on bringing structure)
- About/Bio page blending CTO and CPO perspectives (growth journey)
- Expertise & Skills page organized by Strategic/Tactical/Technical levels
- Contact/Connect page with open, accessible tone
- Comprehensive SEO: sitemap.xml, robots.txt, Open Graph, structured data
- Updated navigation and site structure

**Plans:**
- 📋 phase3-repositioning-PLAN.md (ready to execute)
- 📋 phase3-pages-PLAN.md (ready to execute)
- 📋 phase3-seo-PLAN.md (ready to execute)

**Context Captured:** ✅
- phase3-CONTEXT.md documents complete vision
- Key positioning shift identified and planned
- Multi-level expertise framework defined
- SEO strategy clarified (comprehensive, not minimal)

**Validation:**
- All core pages live and functional
- Clear startup/scaleup growth positioning
- Multi-level capability demonstrated
- SEO foundations in place (full optimization)
- Professional copy that reflects leadership positioning

---

## Phase 4: Portfolio & Case Studies

**Goal:** Showcase technical and product achievements

**Why Now:** Core pages provide context, now demonstrate capabilities

**Deliverables:**
- Portfolio page with project showcase
- Case study template with problem/solution/outcome structure
- 2-3 initial case studies linking technical execution to product outcomes
- Project cards with visual hierarchy
- Filterable/categorizable portfolio items

**Research Needed:** 🔍
- Effective case study storytelling for technical leaders
- Portfolio presentation best practices

**Validation:**
- Portfolio page showcases both technical and product work
- Case studies demonstrate strategic impact
- Content tells compelling story of leadership

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
