# Phase 4.2 Execution Plan: Align Homepage with LinkedIn Profile

## Objective

Update homepage content to align with current LinkedIn profile positioning while maintaining existing design system and startup/scaleup growth focus.

## Execution Context

**Phase Context:**
@.planning/phases/4.2-update-site-to-only-show-first-page/phase4.2-CONTEXT.md

**Research Findings:**
@.planning/phases/4.2-update-site-to-only-show-first-page/phase4.2-RESEARCH.md

**Target File:**
- index.html (homepage content)

**LinkedIn Profile:**
- https://www.linkedin.com/in/aukjan/

**Key Alignment Gaps Identified:**
1. Missing "builder at heart" identity (LinkedIn: "technologist and builder at heart, 22 years building products")
2. Current employer/context not mentioned (LinkedIn: Pandora Intelligence, threat intelligence)
3. Cybersecurity domain expertise hidden (LinkedIn: key expertise area)
4. Email not visible (aukjan@vanbelkum.nl)
5. Tone mismatch (LinkedIn: humble, light-hearted vs homepage: corporate/strategic)
6. Product certifications not mentioned

## Context

### Current Homepage Structure

```
<!-- Hero Section -->
- Title: "Aukjan van Belkum"
- Subtitle: "CTO | CPO | CPTO for Startups & Scaleups"
- Description: "Bringing the right amount of structure..."

<!-- Introduction -->
- Heading: "Helping Startups & Scaleups Grow Without Chaos"
- Lead paragraph
- Supporting paragraph

<!-- Featured Areas (3 Cards) -->
1. Scaling Engineering Teams
2. Product Vision & Strategy
3. Growth-Stage Structure

<!-- Portfolio Section -->
- "Proven Track Record" CTA

<!-- Call to Action -->
- "Let's Connect"
- Buttons: About, LinkedIn
```

### Design Constraints

- Keep existing HTML structure
- Maintain design system (no CSS changes)
- Preserve Phase 3's startup/scaleup positioning
- Work within current section layout

### Content Strategy

**Add:**
- "Builder" identity and hands-on language
- "22 years building products" credential
- Cybersecurity domain expertise mention
- Email contact (aukjan@vanbelkum.nl)
- Warmer, more approachable tone

**Maintain:**
- "CTO | CPO | CPTO for Startups & Scaleups" headline
- Startup/scaleup growth as primary positioning
- "Right amount of structure" philosophy
- Three-card expertise structure

**Avoid:**
- Diluting Phase 3's repositioning (cybersecurity secondary, not primary)
- Over-emphasizing current employer (keep professional, not resume-like)
- Breaking existing responsive design
- Adding new HTML sections/components

## Tasks

### Task 1: Update Hero Section - Add Builder Identity

**Action:** Modify hero description to include builder language

**Current:**
```html
<p class="hero-description">
  Bringing the right amount of structure to growing organizations—
  balancing product vision with technical excellence to scale without over-engineering.
</p>
```

**Updated (Option A - Prepend):**
```html
<p class="hero-description">
  A technologist and builder at heart.
  Bringing the right amount of structure to growing organizations—
  balancing product vision with technical excellence to scale without over-engineering.
</p>
```

**Updated (Option B - Integrate):**
```html
<p class="hero-description">
  Technologist and builder bringing the right amount of structure to growing organizations—
  balancing product vision with technical excellence to scale without over-engineering.
</p>
```

**Decision:** Use Option B (more concise, integrates naturally)

**Verification:**
- [ ] "Technologist and builder" language present in hero
- [ ] Existing structure messaging preserved
- [ ] Character count reasonable (not too long)

### Task 2: Update Introduction - Add 22 Years + Cybersecurity

**Action:** Revise intro section to add experience depth and domain expertise

**Current Lead:**
```html
<p class="lead">
  Bringing the right amount of structure to fast-growing organizations
  through a unique blend of CTO technical depth and CPO customer empathy.
</p>
```

**Updated Lead (warmer tone + builder identity):**
```html
<p class="lead">
  As a builder at heart, I've spent 22 years creating products and growing teams—
  bringing the right amount of structure to fast-growing organizations
  through a unique blend of CTO technical depth and CPO customer empathy.
</p>
```

**Current Supporting:**
```html
<p>
  I specialize in helping startups and scaleups navigate critical growth
  stages—introducing product and engineering structures that scale without
  over-engineering, building distributed teams that deliver, and aligning
  technology strategy with business objectives to drive measurable impact.
</p>
```

**Updated Supporting (add domain context):**
```html
<p>
  With deep roots in cybersecurity and B2B platforms, I specialize in helping
  startups and scaleups navigate critical growth stages—introducing product and
  engineering structures that scale without over-engineering, building distributed
  teams that deliver, and aligning technology strategy with business objectives
  to drive measurable impact.
</p>
```

**Verification:**
- [ ] "22 years" experience mentioned
- [ ] "Builder at heart" language added
- [ ] Cybersecurity domain referenced (but not primary focus)
- [ ] Tone warmer and more personal
- [ ] Startup/scaleup positioning maintained

### Task 3: Add Email to CTA Section

**Action:** Add email contact prominently in the "Let's Connect" section

**Current CTA:**
```html
<section class="section">
  <div class="container container-sm" style="text-align: center;">
    <h2>Let's Connect</h2>
    <p class="lead">
      Growing a startup or scaleup and need help bringing structure to
      your product and engineering organization?
    </p>
    <div style="margin-top: var(--space-lg);">
      <a href="/about" class="btn btn-primary">Learn More About My Work</a>
      <a href="{{ site.author.url }}" class="btn btn-secondary" target="_blank" rel="noopener noreferrer">Connect on LinkedIn</a>
    </div>
  </div>
</section>
```

**Updated CTA (add email before buttons):**
```html
<section class="section">
  <div class="container container-sm" style="text-align: center;">
    <h2>Let's Connect</h2>
    <p class="lead">
      Growing a startup or scaleup and need help bringing structure to
      your product and engineering organization?
    </p>
    <p style="margin-top: var(--space-md); font-size: var(--font-size-lg);">
      <strong>Email:</strong> <a href="mailto:aukjan@vanbelkum.nl">aukjan@vanbelkum.nl</a>
    </p>
    <div style="margin-top: var(--space-lg);">
      <a href="/about" class="btn btn-primary">Learn More About My Work</a>
      <a href="{{ site.author.url }}" class="btn btn-secondary" target="_blank" rel="noopener noreferrer">Connect on LinkedIn</a>
    </div>
  </div>
</section>
```

**Verification:**
- [ ] Email (aukjan@vanbelkum.nl) visible in CTA section
- [ ] Clickable mailto link present
- [ ] Email text is copy-able
- [ ] Styling uses existing design tokens
- [ ] Mobile responsive (no overflow)

### Task 4: Verify Local Build & Responsive Design

**Action:** Test changes locally and verify responsive behavior

**Steps:**
1. Build Jekyll site locally:
   ```bash
   bundle exec jekyll serve
   ```

2. Open http://localhost:4000 in browser

3. Test responsive breakpoints:
   - Mobile (320px-767px): Content readable, no horizontal scroll
   - Tablet (768px-1023px): Layout adapts properly
   - Desktop (1024px+): Full design visible

4. Verify specific elements:
   - Hero description reads naturally
   - Intro paragraphs flow well
   - Email is visible and clickable
   - No broken layouts
   - All sections render correctly

**Verification:**
- [ ] Local build succeeds without errors
- [ ] Homepage loads at http://localhost:4000
- [ ] Mobile responsive (tested 320px, 375px, 414px widths)
- [ ] Tablet responsive (tested 768px, 1024px widths)
- [ ] Desktop layout correct (1280px+ width)
- [ ] No horizontal scroll on any breakpoint
- [ ] Email mailto link works
- [ ] All text is readable

### Task 5: Side-by-Side LinkedIn Comparison

**Action:** Manually verify alignment with LinkedIn profile

**Comparison Checklist:**

**Identity & Tone:**
- [ ] "Builder" identity present on both platforms
- [ ] "22 years" experience mentioned (LinkedIn: "22 years building products")
- [ ] Tone feels consistent (humble, approachable)
- [ ] Professional yet personable on both

**Expertise:**
- [ ] Startup/scaleup growth primary on homepage (LinkedIn: current focus)
- [ ] Cybersecurity visible as domain expertise (LinkedIn: key area)
- [ ] Product + technical dual strength clear (LinkedIn: product certs + technical work)

**Contact:**
- [ ] Email visible on homepage (per requirements)
- [ ] LinkedIn connection option present (both platforms)

**Continuity Test:**
- [ ] Read LinkedIn about section
- [ ] Visit homepage
- [ ] Verify: Same person, same voice, same positioning

**Verification:**
- [ ] All comparison checklist items checked
- [ ] No disconnect between platforms
- [ ] Visitor from LinkedIn would recognize same professional

### Task 6: Commit Changes

**Action:** Create atomic commit with alignment updates

**Commit Message:**
```
feat(homepage): align content with LinkedIn profile

- Add "builder at heart" identity to hero section
- Include "22 years building products" in intro
- Reference cybersecurity domain expertise
- Add email contact (aukjan@vanbelkum.nl) to CTA
- Warm up tone to match LinkedIn's approachable style

Maintains Phase 3 startup/scaleup positioning while ensuring
consistency for visitors arriving from LinkedIn profile.

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>
```

**Verification:**
- [ ] Git status shows only index.html modified
- [ ] Commit message follows conventional format
- [ ] Changes are atomic and focused
- [ ] Co-authored-by tag present

### Task 7: Push to GitHub & Verify Live Site

**Action:** Deploy changes and verify on production

**Steps:**
1. Push changes to GitHub:
   ```bash
   git push origin master
   ```

2. Wait for GitHub Actions build (~2-3 minutes)

3. Verify live site at https://aukjan.vanbelkum.nl/

4. Test on live site:
   - Homepage loads correctly
   - All content changes visible
   - Email link works
   - Responsive on mobile (test with DevTools)
   - No CSS loading issues

**Verification:**
- [ ] Changes pushed to GitHub successfully
- [ ] GitHub Actions workflow completes (green checkmark)
- [ ] Live site updated at https://aukjan.vanbelkum.nl/
- [ ] All content changes visible on live site
- [ ] Email visible and clickable on live site
- [ ] Responsive design works on live site
- [ ] No 404 errors or broken links

## Verification

### Content Alignment Verification

**Builder Identity:**
- [ ] "Technologist and builder" or "builder at heart" appears in hero or intro
- [ ] Language feels natural, not forced

**Experience Depth:**
- [ ] "22 years" mentioned in intro section
- [ ] Matches LinkedIn's experience framing

**Domain Expertise:**
- [ ] Cybersecurity referenced as domain expertise
- [ ] Positioned as background/context, not primary focus
- [ ] Doesn't conflict with Phase 3 startup/scaleup positioning

**Contact:**
- [ ] aukjan@vanbelkum.nl visible on homepage
- [ ] Email is clickable (mailto link)
- [ ] Easy to find in CTA section

**Tone:**
- [ ] More approachable and warm than before
- [ ] Still professional and credible
- [ ] Matches LinkedIn's "humble, light-hearted" style

### Technical Verification

**Design System:**
- [ ] No CSS changes made
- [ ] Design tokens used for spacing/typography
- [ ] Existing component structure maintained

**Responsive:**
- [ ] Mobile (320px+): No horizontal scroll, content readable
- [ ] Tablet (768px+): Layout adapts properly
- [ ] Desktop (1024px+): Full design displays correctly

**Build:**
- [ ] Jekyll build succeeds locally
- [ ] GitHub Actions build succeeds
- [ ] Live site loads without errors

### Alignment Verification

**LinkedIn → Homepage Continuity:**
- [ ] Same positioning (startup/scaleup growth)
- [ ] Same tone (approachable, humble, professional)
- [ ] Same expertise areas visible
- [ ] Contact information matches

**Six Original Gaps Closed:**
1. [ ] ✅ Builder identity now present
2. [ ] ✅ Domain expertise (cybersecurity) visible
3. [ ] ✅ Email contact prominent
4. [ ] ✅ Tone warmed up
5. [ ] ✅ 22 years experience mentioned
6. [ ] ✅ Maintains Phase 3 positioning (no conflict)

## Success Criteria

### Required Outcomes

- [ ] Hero section includes "builder" identity language
- [ ] Intro mentions "22 years building products" or similar
- [ ] Cybersecurity domain expertise referenced subtly
- [ ] Email (aukjan@vanbelkum.nl) visible and clickable in CTA
- [ ] Tone is warmer and more approachable than before
- [ ] Design system unchanged (no CSS modifications)
- [ ] Responsive design maintained across all breakpoints
- [ ] Local build succeeds without errors
- [ ] Changes committed and pushed to GitHub
- [ ] Live site verified at https://aukjan.vanbelkum.nl/

### Quality Checks

- [ ] Someone reading LinkedIn profile then homepage feels continuity
- [ ] Phase 3 positioning (startup/scaleup growth) is maintained
- [ ] Cybersecurity is visible but secondary (per Phase 3 decision)
- [ ] No new HTML sections/components added
- [ ] Content reads naturally (not awkward or forced)

### Documentation

- [ ] This PLAN.md has all checkboxes marked
- [ ] Commit message clearly describes changes
- [ ] If issues encountered, documented for future reference

## Output

Upon completion:
1. **Updated Homepage:** index.html with LinkedIn-aligned content
2. **Verification Results:** All checkboxes in this plan marked complete
3. **Live Site:** Changes deployed to https://aukjan.vanbelkum.nl/
4. **Ready for:** Phase 5 (Thought Leadership Platform) planning

## Notes

**Phase 3 Respect:** This phase maintains Phase 3's deliberate repositioning from cybersecurity to startup/scaleup growth. Cybersecurity is mentioned as domain expertise (background credibility) but not as primary positioning.

**Minimal Scope:** Content-only updates. No design system changes, no new components, no structural modifications.

**Tone Balance:** Aim for "warm but professional" - approachable like LinkedIn while maintaining executive credibility.

---

*Plan created: 2026-01-12*
*Estimated execution: 1-2 hours*
