# Phase 4 Context: Portfolio & Case Studies

## Vision

A **timeline-based portfolio** that demonstrates versatility across domains and challenges. The narrative thread: you've successfully operated across very different contexts — startup to enterprise, product to infrastructure, B2B to B2C, turnaround to greenfield. You're not a one-trick pony; you adapt to whatever the business needs.

The essential takeaway: **You understand both product AND technology deeply.** This is dual-threat capability — genuinely rare. Some projects highlight product work (UX, roadmaps, market fit), others show technical depth (architecture, scale, reliability). You're not a CTO who can't code or a CPO who doesn't understand systems.

## How It Works

### Timeline Structure

**Vertical timeline with alternating left/right project cards.**

- Central vertical line down the page
- Year markers on the timeline
- Project cards alternate: left side, then right side, then left again
- Reverse chronological order (most recent first)
- Visually interesting, clearly shows progression over time
- Mobile: cards stack vertically (no alternating on small screens)

### Project Card Contents

Each card includes:

1. **Date/Year** — When the project happened
2. **Project title** — Brief, compelling name for the work
3. **Company context** — Generic description without revealing confidential info
   - Examples: "E-commerce Startup", "Enterprise SaaS Scale-up", "B2B Marketplace"
   - No actual company names or proprietary details
4. **Your role** — Shows progression over time
   - Examples: "Senior Engineer", "Engineering Manager", "Head of Product", "CTO", "CPTO"
5. **Product/Tech badge** — Visual indicator (colored badge/tag)
   - Badge shows: "Product" or "Technical" focus
   - Reinforces dual capability at a glance
6. **Challenge/Impact summary** — 1-2 sentences
   - Brief description of the problem and outcome
   - High-level, no implementation details
   - Enough to understand what was achieved
7. **Link to case study** — "Read the full story →" or similar CTA
   - Each card links to dedicated case study page
   - Clicking through gets you the deep narrative

### Case Study Pages

Each project has a dedicated case study page with structure:

- **The Context** — What was the situation? What stage was the company at?
- **The Challenge** — What problem were you solving?
- **Your Approach** — How did you think about it? What was your strategy?
- **Key Decisions** — What choices did you make and why?
- **The Outcome** — What happened? What changed?
- **What You Learned** — What did this teach you that informs your work today?

High-level storytelling. No deep technical walkthroughs, no code snippets, no architecture diagrams. Focus on thinking, decisions, and impact.

## What's Essential

For Phase 4 to succeed, these must be true:

1. **The timeline clearly shows versatility across contexts** — not a straight line career, but adaptability across different types of challenges
2. **Product and technical projects are both represented** — at a glance, visitors see you operate in both domains
3. **Each project tells a story without requiring deep domain knowledge** — a founder evaluating you shouldn't need to be an engineer to understand the impact
4. **The visual timeline is clean, professional, and mobile-friendly** — works beautifully on desktop and phone
5. **Case studies are narrative-driven, not technical documentation** — they're about your thinking and impact, not implementation details

## Explicitly Out of Scope

These are **NOT** part of Phase 4:

### ❌ Detailed Technical Implementation Walkthroughs

No deep code examples, architecture diagrams, or technical documentation. Keep it high-level: problem, approach, outcome. Save technical deep-dives for blog posts or actual conversations.

### ❌ Client/Company Names or Confidential Details

Projects described generically without revealing proprietary information or NDA-protected details. Use descriptors like "Enterprise SaaS startup" or "Consumer marketplace." Focus on the challenge and your approach, not specific business contexts.

### ❌ Every Project You've Ever Done

Not a comprehensive resume. Only include projects that demonstrate versatility OR dual product/tech capability. If it doesn't serve the narrative (showing range and dual-threat capability), it doesn't make the timeline. Quality over quantity.

### ❌ Interactive Filtering or Complex Navigation

Simple chronological scroll. No fancy filters, no search, no category toggles. The timeline tells the story in order — visitors just read down the page. Keep it simple and narrative-driven.

## Design Notes

### Components Needed

We'll need to create:

1. **Timeline component** — The vertical line with year markers
2. **Timeline card component** — Project cards that sit on left/right of timeline
3. **Badge component variations** — "Product" and "Technical" badges
4. **Case study page layout** — Template for individual project stories

Leverage existing design system (card styles, typography, colors, spacing). The timeline component will be the main new addition.

### Responsive Behavior

- **Desktop (1024px+)**: Alternating left/right cards, visible timeline line
- **Tablet (768px-1023px)**: Smaller cards, still alternating
- **Mobile (<768px)**: Cards stack vertically, timeline becomes a left sidebar or disappears

### Accessibility

- Semantic HTML: use `<ol>` for timeline (ordered list)
- Each card is a `<li>` with `<article>` element
- Year markers use proper heading hierarchy
- Timeline visuals are decorative (CSS), not content
- Keyboard navigation works naturally (tab through cards)
- Focus states visible on card links

## Success Looks Like

When Phase 4 is complete:

- A visitor lands on `/portfolio` and sees a beautiful vertical timeline
- They scroll down and see your career progression across diverse projects
- They notice the mix of product and technical badges — "Oh, they do both"
- They click into a case study and read a compelling story about your approach
- They walk away thinking: "This person has real range and deep expertise in both product and tech"
- The page works beautifully on their phone when they share it with a colleague

## Open Questions for Planning

When we move to planning this phase, we'll need to decide:

1. How many projects to include on the initial timeline?
   - Start with 6-8? More? Less?
   - Can always add more later
2. Which projects to start with?
   - Need to select initial set that demonstrates range
   - Mix of product and technical
   - Mix of company stages and contexts
3. Do we need placeholder content for case studies?
   - Or do we build the structure and you fill in real content later?
4. Navigation: does portfolio get a main nav link?
   - Already have: Home, About, Expertise, Contact, Articles
   - Add "Portfolio" to header nav?

---

*Context captured: 2026-01-09*
*Ready for planning with `/gsd:plan-phase 4`*
