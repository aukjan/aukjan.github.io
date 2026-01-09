# Execution Plan: Phase 3.1 - Repositioning & Content

## Objective

Reposition the site from "cybersecurity innovation" to "startup/scaleup growth leadership" by updating homepage and about page content to emphasize bringing the right structure to growing organizations on both product and tech sides.

## Context

**Current state:**
- Homepage has hero section with "Driving global cybersecurity innovation..."
- About page exists with personality showcase
- Design system is complete and ready to use

**Target state:**
- Homepage emphasizes startup/scaleup growth expertise
- Clear positioning: bringing right-sized structure (product + tech)
- About page refined to tell growth leadership journey
- Cybersecurity mentioned only as historical context, not primary focus

**Success criteria:**
- Homepage hero and content clearly communicate new positioning
- About page narrative emphasizes startup/scaleup experience
- Professional but approachable tone maintained (per Phase 2)
- Content tells compelling story without portfolio details (Phase 4)

---

## Tasks

### 1. Update Homepage Hero Section
**What:** Rewrite hero copy to emphasize startup/scaleup growth leadership
**Why:** Hero is first impression - must communicate core value proposition
**How:**
- Update hero title (keep name, adjust tagline)
- Rewrite hero subtitle to emphasize CTO/CPO/CPTO for growing companies
- Adjust hero description to focus on bringing structure (not cybersecurity)
- Keep existing design/layout (Phase 2 components)

**Files:** `index.html`
**Verify:** Hero clearly states startup/scaleup growth focus

---

### 2. Refine Homepage Expertise Cards
**What:** Update 3 expertise cards to align with new positioning
**Why:** Cards currently emphasize general tech leadership - need growth focus
**How:**
- Card 1: Engineering Leadership → emphasize scaling teams in startups/scaleups
- Card 2: Product Vision & Strategy → emphasize right-sizing product structure
- Card 3: Cybersecurity Innovation → REPLACE with "Growth-Stage Structure" or similar
- Adjust copy to emphasize balance (not over/under-engineering)

**Files:** `index.html`
**Verify:** Cards reflect startup/scaleup expertise, not generic leadership

---

### 3. Update Homepage Introduction Section
**What:** Revise intro paragraph to support new positioning
**Why:** Currently says "global cybersecurity" - needs to emphasize growth leadership
**How:**
- Rewrite lead paragraph to focus on startup/scaleup transformation
- Emphasize dual strength: product AND tech
- Mention "right amount of structure" philosophy
- Keep mention of distributed teams, measurable impact

**Files:** `index.html`
**Verify:** Introduction supports hero positioning, no cybersecurity focus

---

### 4. Refine Homepage Call-to-Action
**What:** Review and potentially adjust CTA section
**Why:** Ensure CTAs align with new positioning
**How:**
- Review "Let's Connect" section copy
- Adjust if needed to emphasize growth/scaleup collaboration
- Ensure buttons use existing design system components
- Keep links to About and LinkedIn

**Files:** `index.html`
**Verify:** CTAs feel appropriate for startup/scaleup leadership positioning

---

### 5. Update About Page Opening
**What:** Revise about page introduction to lead with growth expertise
**Why:** About page should expand on homepage positioning
**How:**
- Update opening paragraph to emphasize startup/scaleup journey
- Lead with growth leadership, not cybersecurity background
- Maintain personality and authenticity (Phase 2 goal)
- Keep existing page structure and subtitle feature

**Files:** `about.md`
**Verify:** About page opening aligns with homepage positioning

---

### 6. Refine About Page Narrative
**What:** Adjust about page content to tell growth leadership story
**Why:** Need to emphasize bringing structure to growing companies
**How:**
- Review existing about content sections
- Reframe experience around startup/scaleup context
- Emphasize product + tech dual strength
- Mention cybersecurity only as domain expertise, not primary focus
- Keep "professional but approachable" tone

**Files:** `about.md`
**Verify:** Narrative emphasizes growth stage leadership journey

---

### 7. Review for Consistency
**What:** Read through all updated content to ensure cohesive narrative
**Why:** Content must work together to tell consistent story
**How:**
- Read homepage and about page as a visitor would
- Check that positioning is consistent across both pages
- Verify tone matches "professional but approachable"
- Ensure no conflicting messages about focus area

**Files:** `index.html`, `about.md`
**Verify:** Content tells coherent story with clear positioning

---

### 8. Verify Design System Compliance
**What:** Ensure all content changes use existing design components
**Why:** Phase 2 design system is complete - shouldn't need modifications
**How:**
- Confirm hero, cards, sections use existing classes
- No new CSS or component creation needed
- Content fits within established responsive containers
- Typography and spacing use design tokens

**Files:** `index.html`, `about.md`
**Verify:** No design system changes required, components used correctly

---

### 9. Commit Changes
**What:** Commit content repositioning updates
**Why:** Atomic commit for Phase 3.1 completion
**How:**
```bash
git add index.html about.md
git commit -m "feat(content): reposition from cybersecurity to startup/scaleup growth

- Update homepage hero to emphasize scaling organizations
- Refine expertise cards around bringing structure to growth-stage companies
- Adjust about page to lead with startup/scaleup journey
- Emphasize dual product + tech leadership strength
- Mention cybersecurity as domain expertise, not primary focus
- Maintain professional but approachable tone from Phase 2

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

**Files:** `index.html`, `about.md`
**Verify:** Changes committed with clear message

---

## Verification Checklist

After completing all tasks:

- [ ] Homepage hero clearly states startup/scaleup growth focus
- [ ] Expertise cards emphasize bringing structure to growing companies
- [ ] About page leads with growth leadership journey
- [ ] Cybersecurity mentioned only as background/domain expertise
- [ ] "Right amount of structure" philosophy comes through
- [ ] Dual product + tech strength emphasized
- [ ] Professional but approachable tone maintained
- [ ] No design system modifications needed
- [ ] Content is cohesive across homepage and about
- [ ] Changes committed with descriptive message

---

## Dependencies

**Requires:**
- Phase 2 complete (design system exists)
- Existing homepage and about page in place

**Enables:**
- Phase 3.2: New core pages can reference this positioning
- Phase 3.3: SEO meta tags can use new positioning keywords

---

## Estimated Scope

**Complexity:** Medium (content rewriting with clear direction)
**Files modified:** 2 (`index.html`, `about.md`)
**New files:** 0
**Estimated time:** 45-60 minutes

---

## Notes

- This is primarily a content exercise - no code/design changes
- Focus on clarity over cleverness in copy
- Keep existing structure and components from Phase 2
- This repositioning is foundational for all future content (Phase 4, 5)
- Be specific about startup/scaleup context (not generic "enterprise" or "business")

---

*Plan created: 2026-01-09*
*Part of: Phase 3 - Core Pages & Content Structure*
