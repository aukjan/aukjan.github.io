# Roadmap: Personal Branding Site

## Milestone 1.0: CPO/CTO/CPTO Portfolio Launch

Transform existing Jekyll blog into modern personal branding site.

---

## Phase 1: Foundation & Cleanup

**Goal:** Clean existing codebase, fix critical issues, establish solid foundation

**Why First:** Must resolve security issues and technical debt before building new features. Clean slate enables faster development.

**Deliverables:**
- Remove all 2016 blog content and outdated posts
- Fix critical security issues (HTTP→HTTPS, target="_blank" vulnerabilities)
- Update deprecated Jekyll configuration (gems → plugins)
- Resolve dual architecture issue (remove standalone index.html or integrate)
- Add Gemfile with pinned dependencies
- Create GitHub Actions CI/CD workflow

**Research Needed:** 🔍
- Best practices for GitHub Actions with Jekyll
- Modern Jekyll plugin ecosystem and GitHub Pages compatibility

**Validation:**
- All git status shows clean working directory
- No HTTP references in codebase
- Jekyll builds successfully with modern config
- GitHub Actions workflow runs and deploys

---

## Phase 2: Design System & Architecture

**Goal:** Create modern, professional design system and site architecture

**Why Now:** Foundation is clean, need design direction before building content pages

**Deliverables:**
- Modern color palette and typography system
- Responsive layout framework
- Component library (cards, headers, navigation, footer)
- New base layout replacing Lanyon theme
- Mobile-first responsive design
- Professional CSS architecture

**Research Needed:** 🔍
- Contemporary design trends for executive portfolios
- Accessibility best practices (WCAG 2.1 AA)

**Validation:**
- Design system documented
- Components render correctly across devices
- Passes accessibility audit
- Professional, modern aesthetic achieved

---

## Phase 3: Core Pages & Content Structure

**Goal:** Build essential pages with proper information architecture

**Why Now:** Design system established, can now create content structure

**Deliverables:**
- Modern homepage with clear value proposition
- About/Bio page blending CTO and CPO perspectives
- Expertise & Skills page with categorized capabilities
- Contact/Connect page with professional links
- Sitemap.xml and robots.txt for SEO
- Updated navigation and site structure

**Research Needed:** 🔍
- Effective personal branding copy strategies
- SEO optimization for personal sites

**Validation:**
- All core pages live and functional
- Clear information hierarchy
- SEO foundations in place
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
