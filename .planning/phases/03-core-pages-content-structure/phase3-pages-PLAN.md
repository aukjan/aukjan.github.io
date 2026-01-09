# Execution Plan: Phase 3.2 - New Core Pages

## Objective

Create two essential new pages: Expertise/Skills page (organized by Strategic/Tactical/Technical levels) and Contact/Connect page (open and accessible), using the existing design system and reflecting the startup/scaleup growth positioning.

## Context

**Current state:**
- Homepage and about page exist with refined positioning (Phase 3.1)
- Design system complete with page layouts, components (Phase 2)
- Navigation exists but doesn't include new pages yet

**Target state:**
- Expertise page showing capabilities across Strategic/Tactical/Technical levels
- Contact page with welcoming tone and multiple connection methods
- Both pages use existing design system components
- Content reflects startup/scaleup growth focus

**Success criteria:**
- Expertise page demonstrates multi-level operational capability
- Contact page feels open and accessible (not formal/distant)
- Both pages use Phase 2 design system correctly
- Content quality is "good enough" with clear structure

---

## Tasks

### 1. Create Expertise Page File
**What:** Create new Jekyll page for expertise/skills
**Why:** Need dedicated page to show multi-level capabilities
**How:**
- Create `expertise.md` in root directory
- Add YAML front matter (layout: page, title, subtitle)
- Use page layout from Phase 2 (semantic HTML5 structure)
- Set up initial structure for content sections

**Files:** `expertise.md` (new)
**Verify:** File created with proper front matter, uses page layout

---

### 2. Write Expertise Page Introduction
**What:** Create opening section explaining multi-level leadership approach
**Why:** Set context for Strategic/Tactical/Technical organization
**How:**
- Opening paragraph: Why multi-level capability matters for startups/scaleups
- Emphasize ability to operate from board room to code review
- Connect to "right amount of structure" philosophy
- Keep professional but approachable tone

**Files:** `expertise.md`
**Verify:** Introduction explains the multi-level framework clearly

---

### 3. Create Strategic Level Section
**What:** Document strategic capabilities (board/exec level)
**Why:** Show ability to operate at highest organizational levels
**How:**
- Section heading: "Strategic Leadership"
- List strategic capabilities:
  - Vision setting and technology strategy
  - Product roadmap and market positioning
  - Organizational design and team building
  - Board-level communication and stakeholder management
  - Budget planning and resource allocation
- Frame in startup/scaleup growth context
- Use existing design system typography/spacing

**Files:** `expertise.md`
**Verify:** Strategic section shows C-level capabilities for growing companies

---

### 4. Create Tactical Level Section
**What:** Document tactical capabilities (director/manager level)
**Why:** Show operational excellence in execution
**How:**
- Section heading: "Tactical Execution"
- List tactical capabilities:
  - Process design and workflow optimization
  - Team structure and hiring strategies
  - Sprint planning and delivery management
  - Stakeholder alignment and communication
  - Metrics definition and OKR frameworks
- Emphasize "right-sized" processes (not over-engineered)
- Use cards or structured lists (design system components)

**Files:** `expertise.md`
**Verify:** Tactical section demonstrates hands-on operational skills

---

### 5. Create Technical Level Section
**What:** Document technical capabilities (IC/hands-on level)
**Why:** Show credibility with technical depth
**How:**
- Section heading: "Technical Excellence"
- List technical skills and domains:
  - Software architecture and system design
  - Technology stack decisions (mention relevant technologies)
  - Code review and technical mentorship
  - Security architecture and best practices
  - Cloud infrastructure and DevOps
- Include specific technologies where relevant (but not exhaustive list)
- Frame as hands-on leadership, not just oversight

**Files:** `expertise.md`
**Verify:** Technical section shows genuine technical depth

---

### 6. Add Expertise Page Call-to-Action
**What:** Add closing section encouraging connection
**Why:** Give readers clear next step after reviewing expertise
**How:**
- Brief paragraph about collaboration opportunities
- Link to contact page (upcoming in Task 7)
- Use existing button components from design system
- Keep tone inviting and open

**Files:** `expertise.md`
**Verify:** CTA feels natural and uses design system components

---

### 7. Create Contact Page File
**What:** Create new Jekyll page for contact/connection
**Why:** Provide easy ways for people to reach out
**How:**
- Create `contact.md` in root directory
- Add YAML front matter (layout: page, title, subtitle optional)
- Use page layout from Phase 2
- Plan for welcoming, accessible tone

**Files:** `contact.md` (new)
**Verify:** File created with proper front matter

---

### 8. Write Contact Page Introduction
**What:** Create welcoming opening section
**Why:** Set open and accessible tone
**How:**
- Opening paragraph: Enthusiasm for connection and conversation
- Emphasize being approachable despite seniority
- Mention types of conversations (collaboration, speaking, networking, advice)
- Use warm but professional tone

**Files:** `contact.md`
**Verify:** Introduction feels inviting and accessible

---

### 9. Add Contact Methods Section
**What:** List ways to connect with links
**Why:** Provide multiple low-friction connection options
**How:**
- Create section with contact methods:
  - LinkedIn (primary professional network)
  - Email (professional email address)
  - Twitter/X (if applicable)
  - GitHub (if sharing code/open source)
  - Other relevant professional networks
- Use button components or structured list
- NO contact form (explicitly out of scope)
- Make all links open in new tab with proper rel attributes

**Files:** `contact.md`
**Verify:** Multiple connection methods listed, no form, links work

---

### 10. Add Response Expectations (Optional)
**What:** Set expectations about response time/availability
**Why:** Manage expectations while staying approachable
**How:**
- Brief note about response approach (e.g., "I read everything" or "typically respond within X")
- Keep it casual and human
- Optional: mention best topics/reasons to connect
- Don't make it too formal or bureaucratic

**Files:** `contact.md`
**Verify:** Sets expectations without being off-putting

---

### 11. Verify Design System Usage
**What:** Ensure both new pages use existing components correctly
**Why:** Phase 2 design system should handle all needs
**How:**
- Check page layout renders correctly
- Verify typography uses design tokens (headings, body, spacing)
- Ensure responsive containers work
- Test button components if used
- Confirm no custom CSS needed

**Files:** `expertise.md`, `contact.md`
**Verify:** Both pages use design system without modifications

---

### 12. Commit New Pages
**What:** Commit expertise and contact pages
**Why:** Atomic commit for Phase 3.2 completion
**How:**
```bash
git add expertise.md contact.md
git commit -m "feat(pages): add expertise and contact pages

- Create expertise page organized by Strategic/Tactical/Technical levels
- Demonstrate multi-level operational capability for startups/scaleups
- Create contact page with open, accessible tone
- Include multiple connection methods (LinkedIn, email, social)
- Use existing page layout and design system components
- No contact form (out of scope)

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

**Files:** `expertise.md`, `contact.md`
**Verify:** Changes committed with clear message

---

## Verification Checklist

After completing all tasks:

- [ ] `expertise.md` created with proper front matter
- [ ] Expertise page has intro explaining multi-level approach
- [ ] Strategic section shows C-level capabilities
- [ ] Tactical section demonstrates operational excellence
- [ ] Technical section proves hands-on technical depth
- [ ] All expertise content framed for startup/scaleup context
- [ ] `contact.md` created with proper front matter
- [ ] Contact page feels open and accessible
- [ ] Multiple connection methods listed (LinkedIn, email, etc.)
- [ ] NO contact form implemented
- [ ] Both pages use existing page layout correctly
- [ ] Design system components used properly (no custom CSS)
- [ ] Responsive design works on both pages
- [ ] Changes committed with descriptive message

---

## Dependencies

**Requires:**
- Phase 2 complete (page layout and components exist)
- Phase 3.1 complete (positioning established)

**Enables:**
- Phase 3.3: Navigation can link to these new pages
- Phase 3.3: SEO meta tags can describe new pages

---

## Estimated Scope

**Complexity:** Medium (new content creation with clear structure)
**Files modified:** 0
**New files:** 2 (`expertise.md`, `contact.md`)
**Estimated time:** 60-75 minutes

---

## Notes

- Focus on "good enough" content quality - can iterate later
- Expertise page demonstrates differentiation (multi-level capability rare in leaders)
- Contact page tone is key - must feel genuinely accessible
- Use simple markdown - let design system handle presentation
- Both pages should feel cohesive with homepage/about (Phase 3.1)
- No placeholder content - write actual substance
- Keep sections concise - not exhaustive lists

---

*Plan created: 2026-01-09*
*Part of: Phase 3 - Core Pages & Content Structure*
