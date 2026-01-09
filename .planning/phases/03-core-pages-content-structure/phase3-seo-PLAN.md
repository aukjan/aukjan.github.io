# Execution Plan: Phase 3.3 - SEO & Navigation

## Objective

Implement comprehensive SEO foundations (sitemap, robots.txt, rich meta tags, Open Graph, structured data) and update site navigation to include all pages, making the site discoverable and complete.

## Context

**Current state:**
- Homepage, about, expertise, contact pages exist (Phase 3.1 & 3.2)
- Archive page exists from earlier
- Navigation has: Home, About, Articles
- No sitemap.xml or robots.txt
- Basic meta tags in head.html

**Target state:**
- Automated sitemap.xml generation
- Proper robots.txt configuration
- Rich meta tags on all pages
- Open Graph tags for social sharing
- JSON-LD structured data for professional profile
- Navigation updated to include Expertise and Contact
- Site optimized for "CTO startup growth", "CPO scaleup" searches

**Success criteria:**
- Complete technical SEO implementation
- Navigation includes all core pages
- Meta tags describe startup/scaleup growth positioning
- Site structure supports discoverability

---

## Tasks

### 1. Enable Jekyll Sitemap Plugin
**What:** Configure Jekyll to automatically generate sitemap.xml
**Why:** Search engines need sitemap to discover and index pages
**How:**
- Check `_config.yml` for plugins list
- Add `jekyll-sitemap` to plugins (if not already present)
- Verify github-pages gem includes this plugin
- No manual sitemap creation needed - fully automated

**Files:** `_config.yml`
**Verify:** sitemap.xml will be generated automatically on build

---

### 2. Create robots.txt
**What:** Add robots.txt to control search engine crawling
**Why:** Define crawling rules and link to sitemap
**How:**
- Create `robots.txt` in root directory
- Allow all crawlers: `User-agent: * / Allow: /`
- Link to sitemap: `Sitemap: https://aukjan.github.io/sitemap.xml`
- No disallow rules needed (want everything indexed)

**Files:** `robots.txt` (new)
**Verify:** robots.txt has proper syntax, references sitemap

---

### 3. Update Base Meta Tags in Head
**What:** Enhance meta tags in head.html for better SEO
**Why:** Current meta tags may be generic/incomplete
**How:**
- Review existing meta tags in `_includes/head.html`
- Ensure charset, viewport, description present
- Add keywords meta tag with startup/scaleup terms
- Verify title tag uses page.title and site.title correctly
- Keep existing structure, enhance what's there

**Files:** `_includes/head.html`
**Verify:** Base meta tags complete and descriptive

---

### 4. Add Open Graph Meta Tags
**What:** Implement Open Graph tags for social sharing
**Why:** Control how pages appear when shared on LinkedIn, Twitter, etc.
**How:**
- Add to `_includes/head.html`:
  - og:title (use page title or site title)
  - og:description (use page description or site description)
  - og:type (website for homepage, article for posts, profile for about)
  - og:url (canonical page URL)
  - og:image (if site has logo/image, otherwise optional for now)
  - og:site_name (site title)
- Use Liquid conditionals to handle different page types

**Files:** `_includes/head.html`
**Verify:** Open Graph tags present, populate correctly per page

---

### 5. Add Twitter Card Meta Tags
**What:** Implement Twitter Card tags for Twitter/X sharing
**Why:** Optimize appearance on Twitter when pages are shared
**How:**
- Add to `_includes/head.html`:
  - twitter:card (summary or summary_large_image)
  - twitter:title (page/site title)
  - twitter:description (page/site description)
  - twitter:creator (if Twitter handle available)
  - twitter:site (if site Twitter handle available)
- Keep simple - summary card type sufficient

**Files:** `_includes/head.html`
**Verify:** Twitter Card tags present

---

### 6. Add JSON-LD Structured Data
**What:** Implement Person schema for professional profile
**Why:** Help search engines understand this is a professional portfolio
**How:**
- Add JSON-LD script tag to `_includes/head.html`
- Use Person schema type
- Include:
  - name, jobTitle (CTO/CPO/CPTO for Startups & Scaleups)
  - description (startup/scaleup growth expertise)
  - url (site URL)
  - sameAs (array of social profile URLs: LinkedIn, GitHub, etc.)
- Follow schema.org/Person specification

**Files:** `_includes/head.html`
**Verify:** JSON-LD validates with schema.org validator

---

### 7. Add Page-Specific Descriptions
**What:** Add description front matter to all core pages
**Why:** Each page needs unique, descriptive meta description
**How:**
- Add `description:` to front matter of:
  - `index.html`: Emphasize startup/scaleup growth leadership
  - `about.md`: Personal journey bringing structure to growing companies
  - `expertise.md`: Multi-level capabilities (strategic/tactical/technical)
  - `contact.md`: Open and accessible connection opportunities
  - `archive.md`: Review existing or add description
- Keep descriptions 120-160 characters
- Include relevant keywords naturally

**Files:** `index.html`, `about.md`, `expertise.md`, `contact.md`, `archive.md`
**Verify:** All pages have unique, descriptive meta descriptions

---

### 8. Update Site Navigation - Header
**What:** Add Expertise and Contact links to site navigation
**Why:** New pages need to be discoverable from navigation
**How:**
- Edit `_includes/header.html`
- Current nav: Home, About, Articles
- New nav: Home, About, Expertise, Contact, Articles
- Ensure navigation responsive (design system handles this)
- Verify links point to correct pages (/expertise, /contact)
- Test on mobile breakpoint

**Files:** `_includes/header.html`
**Verify:** Navigation includes all core pages, links work

---

### 9. Update Site Navigation - Footer
**What:** Update footer navigation to match header
**Why:** Footer should reflect complete site structure
**How:**
- Edit `_includes/footer.html`
- Add Expertise and Contact links if footer has navigation
- Keep consistent with header navigation
- Verify footer layout still looks good with additional links
- Ensure responsive design maintained

**Files:** `_includes/footer.html`
**Verify:** Footer navigation complete and responsive

---

### 10. Verify Canonical URLs
**What:** Ensure canonical link tags are properly set
**Why:** Prevent duplicate content issues
**How:**
- Check `_includes/head.html` for canonical link tag
- Should use `{{ site.url }}{{ page.url }}` or similar
- Verify works correctly on GitHub Pages with custom domain
- Add if missing

**Files:** `_includes/head.html`
**Verify:** Canonical URLs set correctly for all pages

---

### 11. Test SEO Implementation Locally
**What:** Build site and verify SEO elements render correctly
**Why:** Catch errors before committing
**How:**
- Run `docker-compose up` (from Docker setup)
- Visit all pages and view source
- Verify meta tags render with correct content
- Check sitemap.xml is generated (if Jekyll builds locally)
- Validate structured data with schema.org validator

**Files:** N/A (testing)
**Verify:** All SEO elements render correctly

---

### 12. Commit SEO and Navigation Updates
**What:** Commit all SEO and navigation changes
**Why:** Atomic commit for Phase 3.3 completion
**How:**
```bash
git add _config.yml robots.txt _includes/head.html _includes/header.html _includes/footer.html index.html about.md expertise.md contact.md archive.md
git commit -m "feat(seo): implement comprehensive SEO and update navigation

- Enable jekyll-sitemap plugin for automated sitemap generation
- Add robots.txt with sitemap reference
- Implement Open Graph meta tags for social sharing
- Add Twitter Card meta tags for Twitter/X
- Add JSON-LD structured data (Person schema)
- Add unique meta descriptions to all core pages
- Update header navigation: Home, About, Expertise, Contact, Articles
- Update footer navigation to match header
- Verify canonical URLs set correctly
- Optimize for 'CTO startup growth' and 'CPO scaleup' searches

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

**Files:** Multiple (see above)
**Verify:** Changes committed with clear message

---

## Verification Checklist

After completing all tasks:

- [ ] jekyll-sitemap plugin enabled in _config.yml
- [ ] robots.txt created with sitemap reference
- [ ] Base meta tags complete in head.html
- [ ] Open Graph tags implemented for all pages
- [ ] Twitter Card tags added
- [ ] JSON-LD Person schema implemented
- [ ] All core pages have unique meta descriptions
- [ ] Descriptions emphasize startup/scaleup growth positioning
- [ ] Header navigation includes: Home, About, Expertise, Contact, Articles
- [ ] Footer navigation updated to match
- [ ] Navigation works on mobile breakpoint
- [ ] Canonical URLs set correctly
- [ ] SEO elements render correctly (tested locally)
- [ ] Changes committed with descriptive message

---

## Dependencies

**Requires:**
- Phase 2 complete (header/footer components exist)
- Phase 3.1 complete (repositioned content provides SEO keywords)
- Phase 3.2 complete (new pages to add to navigation)

**Enables:**
- Site ready for deployment and indexing
- Complete Phase 3 (all deliverables met)
- Foundation for Phase 4 (portfolio pages will inherit SEO structure)

---

## Estimated Scope

**Complexity:** Medium-High (technical SEO configuration)
**Files modified:** ~9 (config, includes, all core pages)
**New files:** 1 (`robots.txt`)
**Estimated time:** 60-90 minutes

---

## Notes

- This is primarily technical SEO - no content writing
- Open Graph/Twitter Cards improve social sharing appearance
- JSON-LD structured data helps Google understand professional context
- Navigation update is straightforward - design system handles responsive
- sitemap.xml generation is automatic (Jekyll plugin)
- Focus on proper implementation - don't over-optimize
- Target keywords: "CTO startup growth", "CPO scaleup", "product engineering leadership"
- GitHub Pages + custom domain (aukjan.vanbelkum.nl) already configured

---

## SEO Keywords Target

**Primary keywords:**
- CTO startup growth
- CPO scaleup
- Product and engineering leadership
- Startup structure
- Scaleup leadership

**Secondary keywords:**
- Technical product leadership
- Engineering and product strategy
- Growth stage CTO
- Startup product architecture

**Use naturally in:**
- Meta descriptions
- Page titles
- Structured data
- Open Graph descriptions

---

*Plan created: 2026-01-09*
*Part of: Phase 3 - Core Pages & Content Structure*
