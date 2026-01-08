# Personal Branding Site: CPO/CTO/CPTO Portfolio

## Vision

Transform existing Jekyll blog into a modern personal branding site that establishes professional presence as a CPO/CTO/CPTO leader. A polished, static site showcasing thought leadership, technical expertise, and product vision to attract employers, industry peers, and consulting/speaking opportunities.

## Problem

Current site is a dated technical blog from 2016 with outdated content (macOS WiFi fixes, Terraform/Ansible tutorials) that doesn't reflect current senior leadership positioning. The site has:
- Old blog posts (2016) about tactical technical issues
- Two competing architectures (Jekyll blog + standalone portfolio HTML)
- Unprofessional appearance for C-level executive
- No showcase of strategic leadership or product vision
- Missing personal branding elements

## Solution

Complete site transformation maintaining GitHub Pages infrastructure but reimagining content and design:

**Core Elements:**
1. **Thought Leadership** - Written articles on tech trends, product innovation, scaling, leadership, and aligning tech with business goals
2. **Portfolio** - Showcase both technical achievements (architecture, infrastructure) and product successes (roadmaps, UX improvements, market fit)
3. **Expertise & Skills** - Engineering leadership, system architecture, product vision, UX, data-driven decisions, market strategy
4. **About/Bio** - Journey blending technical depth (CTO) with customer empathy (CPO)
5. **Case Studies** - Deep dives linking technical execution to product outcomes
6. **Contact/Connect** - Easy access for opportunities, consulting, speaking engagements

**Target Audience:**
- Potential employers/recruiters seeking senior leadership
- Industry peers for networking and reputation building
- Conference organizers and consulting opportunities

**Core Focus:** Professional presence - a polished, modern site reflecting senior leadership credibility.

## Requirements

### Validated

- ✓ Static site generation with Jekyll — existing
- ✓ GitHub Pages hosting with custom domain (aukjan.vanbelkum.nl) — existing
- ✓ Markdown-based content authoring — existing
- ✓ Template-based architecture (layouts, includes, components) — existing
- ✓ Responsive CSS framework — existing
- ✓ Git version control — existing
- ✓ HTTPS custom domain configuration — existing

### Active

- [ ] Remove all existing 2016 blog content and outdated technical posts
- [ ] Design modern, professional homepage reflecting CPO/CTO/CPTO positioning
- [ ] Create thought leadership section with written article support
- [ ] Build portfolio section showcasing technical + product achievements
- [ ] Develop expertise & skills presentation
- [ ] Write compelling About/Bio section blending technical and product leadership
- [ ] Create case study template and initial case studies
- [ ] Add contact/connect section with professional links
- [ ] Resolve dual architecture issue (remove or integrate standalone index.html)
- [ ] Implement modern, professional design system
- [ ] Add GitHub Actions CI/CD for automated builds and deployments
- [ ] Fix critical security issues (HTTP→HTTPS, target="_blank" vulnerabilities)
- [ ] Update deprecated Jekyll configuration (gems → plugins)
- [ ] Add SEO optimization (sitemap.xml, robots.txt, meta tags)
- [ ] Ensure accessibility compliance (WCAG guidelines)

### Out of Scope

- Blog CMS or commenting system — Static content only, no WordPress/complex CMS
- Video content embedding or hosting — Written content focus for v1
- Interactive features — No contact forms, newsletters, or dynamic elements for v1
- Complex build tooling — Keep Jekyll-native, no webpack/Vite/etc.
- Third-party hosting — Must remain on GitHub Pages
- Authentication or user accounts — Public site only
- Analytics integration — Defer to future phase
- Mobile app or PWA features — Web-only for v1

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Keep Jekyll + GitHub Pages | Existing infrastructure works, free hosting, automatic builds, no migration complexity | ✅ Confirmed |
| Jekyll as single architecture | Removed standalone index.html/styles.css; maintains consistency, leverages existing infrastructure, enables template reuse | ✅ Complete (2026-01-08) |
| Written content only (no video) | Focus effort on core written thought leadership, video can be added later | — Pending |
| Static site, no CMS | Simplicity, security, performance; content updates via git/markdown sufficient for personal site | ✅ Confirmed |
| Modern design overhaul | Current Lanyon theme too dated for C-level branding, need contemporary professional look | — Pending |
| Remove all 2016 blog content | Old content damages credibility, start fresh with current positioning | ✅ Complete (2026-01-08) |
| GitHub Actions for CI | Stay within GitHub ecosystem constraint, modern approach vs legacy GitHub Pages auto-build | — Pending |
| Use Gemfile for dependencies | Reproducible builds, version pinning, better local development experience | ✅ Complete (2026-01-08) |

## Constraints

**Technical:**
- Must remain on GitHub Pages hosting (no additional hosting costs)
- CI/CD must use GitHub ecosystem (GitHub Actions)
- Keep Jekyll as static site generator (proven, maintainable)
- Maintain custom domain (aukjan.vanbelkum.nl)

**Design:**
- Must look modern and contemporary (not dated like current 2016 era design)
- Reflect senior leadership/C-level positioning
- Professional, polished aesthetic

**Operational:**
- Easy to maintain and update content without complex tools
- Simple content authoring workflow (Markdown + git)
- Fast build and deployment times

## Success Metrics

**Phase 1 (Launch):**
- Site reflects modern CPO/CTO/CPTO positioning
- All old 2016 content removed
- Professional homepage with clear value proposition
- At least 1-2 initial case studies or portfolio pieces
- All critical security issues resolved
- SEO foundations in place

**Phase 2 (Growth):**
- 5+ thought leadership articles published
- 3+ detailed case studies showcasing technical + product work
- Positive feedback from industry peers
- Inbound opportunities (recruiting, speaking, consulting)

## Open Questions

- Which specific projects/case studies to feature initially?
- Tone/voice for thought leadership content (technical depth vs accessibility)?
- Color palette and visual design direction?
- Blog post publishing frequency expectation?
- Should we preserve any of the existing technical content in an "archive"?

## Risks

- **Design scope creep**: Modern redesign could expand beyond MVP
- **Content creation bottleneck**: Portfolio and case studies require substantial writing
- **Jekyll limitations**: May hit constraints if future requirements need dynamic features
- **Time investment**: Content development and writing is time-intensive

---

*Last updated: 2026-01-08 after initialization*
