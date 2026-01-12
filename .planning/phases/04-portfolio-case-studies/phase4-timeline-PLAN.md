<objective>
Build portfolio timeline infrastructure with Jekyll collection, CSS components, and main portfolio page featuring vertical timeline with alternating cards.
</objective>

<execution_context>
@phase4-CONTEXT.md - Vision: timeline-based portfolio demonstrating versatility and dual product/tech capability
@phase4-RESEARCH.md - CSS patterns, Jekyll collection structure, accessibility guidelines
@_sass/README.md - Existing design system (tokens, components, spacing)
@_config.yml - Jekyll configuration
@_includes/header.html - Current navigation structure
</execution_context>

<context>
**What we're building:**
- Jekyll `_portfolio` collection for case study content
- Timeline CSS component (new `_sass/_timeline.scss`)
- Main `/portfolio.html` page with vertical timeline
- Alternating left/right card layout (desktop) → stacked (mobile)
- Year markers on timeline with proper semantic HTML

**Design system assets available:**
- Card component styles (`.card`)
- Badge component (`.badge`)
- Typography tokens and spacing scale
- Color tokens (primary, neutral, accent)
- Responsive breakpoints already established

**Key decisions from context:**
- Timeline shows versatility across contexts (not straight-line career)
- Product AND technical projects both represented
- Simple chronological scroll (no filtering/search)
- Generic company descriptions (no confidential info)
- Target: 6-8 projects initially

**Implementation patterns from research:**
- Pseudo-element for center line (`.timeline::before`)
- `calc(50% - 40px)` for alternating card widths
- Semantic HTML: `<section>` + `<ol>` + `<article>`
- `<time>` elements with `datetime` attributes
- Breakpoint at 768px: alternating → stacked
- Mobile: line moves to left (20px), cards stack right
</context>

<tasks>

## Task 1: Configure Jekyll Portfolio Collection

**File:** `_config.yml`

Add portfolio collection configuration:

```yaml
collections:
  portfolio:
    output: true
    permalink: /portfolio/:slug/

defaults:
  - scope:
      path: ""
      type: "portfolio"
    values:
      layout: "portfolio"
```

**Why:** Collections are Jekyll's native pattern for non-blog content. This enables individual case study pages with clean URLs (`/portfolio/project-name/`).

**Verification:**
- Run `bundle exec jekyll serve` successfully
- No build errors related to collection configuration

## Task 2: Create Timeline CSS Component

**File:** `_sass/_timeline.scss`

Create new Sass partial with timeline styles:

```scss
// ============================================================================
// Timeline Component
// ============================================================================
//
// Vertical timeline with alternating left/right cards (desktop)
// Stacked layout with left-side line (mobile)
//
// Usage:
//   <section class="timeline">
//     <div class="timeline-year"><h2>2024</h2></div>
//     <ol class="timeline-list">
//       <li class="timeline-item">
//         <article class="timeline-card">...</article>
//       </li>
//     </ol>
//   </section>

// Timeline container
.timeline {
  position: relative;
  max-width: var(--container-md);
  margin: 0 auto;
  padding: var(--space-2xl) var(--space-md);

  // Center vertical line (desktop)
  &::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 0;
    bottom: 0;
    width: 2px;
    background: var(--color-border);
    transform: translateX(-50%);
    z-index: 0;
  }
}

// Year markers
.timeline-year {
  position: relative;
  text-align: center;
  margin: var(--space-2xl) 0 var(--space-xl);

  h2 {
    display: inline-block;
    background: var(--color-background);
    padding: 0 var(--space-md);
    font-size: var(--text-2xl);
    font-weight: var(--font-bold);
    color: var(--color-primary);
    position: relative;
    z-index: 2;
  }

  // Dot on timeline
  &::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 50%;
    width: 20px;
    height: 20px;
    background: var(--color-primary);
    border: 4px solid var(--color-background);
    border-radius: 50%;
    transform: translate(-50%, -50%);
    z-index: 1;
  }
}

// Timeline list (ordered list)
.timeline-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

// Timeline items (list items containing cards)
.timeline-item {
  display: flex;
  margin-bottom: var(--space-2xl);

  // Odd items: cards on left side
  &:nth-child(odd) {
    justify-content: flex-end;

    .timeline-card {
      width: calc(50% - 40px);
      margin-right: 40px;

      // Connector dot (right side of card)
      &::before {
        right: -46px;
      }
    }
  }

  // Even items: cards on right side
  &:nth-child(even) {
    justify-content: flex-start;

    .timeline-card {
      width: calc(50% - 40px);
      margin-left: 40px;

      // Connector dot (left side of card)
      &::before {
        left: -46px;
      }
    }
  }
}

// Timeline cards (extend existing card component)
.timeline-card {
  // Inherit card styles from design system
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-lg);
  position: relative;
  z-index: 1;
  transition: transform 0.2s, box-shadow 0.2s;

  // Connector dot to timeline
  &::before {
    content: '';
    position: absolute;
    top: 24px;
    width: 12px;
    height: 12px;
    background: var(--color-primary);
    border: 3px solid var(--color-background);
    border-radius: 50%;
    z-index: 2;
  }

  // Hover effect
  &:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-lg);
  }

  // Card content elements
  time {
    display: block;
    font-size: var(--text-sm);
    font-weight: var(--font-medium);
    color: var(--color-text-muted);
    margin-bottom: var(--space-xs);
  }

  h3 {
    font-size: var(--text-xl);
    font-weight: var(--font-bold);
    color: var(--color-text);
    margin: 0 0 var(--space-xs);
    font-family: var(--font-sans);
  }

  .company-context {
    font-size: var(--text-sm);
    color: var(--color-text-light);
    margin-bottom: var(--space-sm);
  }

  .role {
    font-size: var(--text-sm);
    font-weight: var(--font-medium);
    color: var(--color-primary);
    margin-bottom: var(--space-sm);
  }

  .card-meta {
    display: flex;
    align-items: center;
    gap: var(--space-sm);
    margin-bottom: var(--space-md);
    flex-wrap: wrap;
  }

  .summary {
    font-size: var(--text-base);
    color: var(--color-text);
    line-height: var(--leading-relaxed);
    margin-bottom: var(--space-md);
  }

  .card-link {
    display: inline-flex;
    align-items: center;
    gap: var(--space-xs);
    font-size: var(--text-sm);
    font-weight: var(--font-medium);
    color: var(--color-primary);
    text-decoration: none;
    transition: color 0.2s;

    &:hover {
      color: var(--color-primary-dark);
    }

    &::after {
      content: '→';
    }
  }
}

// Mobile responsive layout
@media (max-width: 767px) {
  .timeline {
    padding: var(--space-xl) var(--space-md);

    // Move line to left side
    &::before {
      left: 20px;
      transform: translateX(0);
    }
  }

  .timeline-year {
    text-align: left;
    padding-left: 60px;
    margin: var(--space-xl) 0 var(--space-md);

    h2 {
      background: transparent;
      padding: 0;
    }

    // Move dot to left line
    &::before {
      left: 20px;
      transform: translate(-50%, -50%);
    }
  }

  // Stack all cards to the right of line
  .timeline-item {
    &:nth-child(odd),
    &:nth-child(even) {
      justify-content: flex-start;

      .timeline-card {
        width: calc(100% - 60px);
        margin-left: 60px;
        margin-right: 0;

        // All connector dots on left
        &::before {
          left: -46px;
          right: auto;
        }
      }
    }
  }
}
```

**Import in main stylesheet:**

**File:** `assets/css/main.scss`

Add to imports:
```scss
@import 'timeline';
```

**Why:**
- Extends existing card component
- Uses design tokens for consistency
- Proper semantic structure with accessibility
- Mobile-first responsive approach

**Verification:**
- Timeline CSS compiles without errors
- Styles imported in main.scss
- No conflicts with existing component styles

## Task 3: Create Portfolio Page Template

**File:** `portfolio.html`

Create main portfolio timeline page:

```html
---
layout: page
title: Portfolio
description: Career timeline showcasing product and technical leadership across diverse contexts
permalink: /portfolio/
---

<div class="container">
  <header class="page-header">
    <h1>{{ page.title }}</h1>
    <p class="lead">A timeline demonstrating versatility across product and technical challenges—from startups to scale-ups, greenfield to turnaround, strategy to execution.</p>
  </header>

  {% assign sorted_projects = site.portfolio | sort: 'date' | reverse %}
  {% assign projects_by_year = sorted_projects | group_by_exp: "item", "item.date | date: '%Y'" %}

  {% if sorted_projects.size > 0 %}
    <section class="timeline" aria-label="Career timeline">
      {% for year_group in projects_by_year %}
        <div class="timeline-year">
          <h2>{{ year_group.name }}</h2>
        </div>

        <ol class="timeline-list">
          {% for project in year_group.items %}
            <li class="timeline-item">
              <article class="timeline-card">
                <time datetime="{{ project.date | date: '%Y-%m' }}">
                  {{ project.date | date: '%B %Y' }}
                </time>
                <h3>{{ project.title }}</h3>
                <p class="company-context">{{ project.company_context }}</p>
                <p class="role">{{ project.role }}</p>
                <div class="card-meta">
                  {% if project.category == 'product' %}
                    <span class="badge badge-accent">Product</span>
                  {% elsif project.category == 'technical' %}
                    <span class="badge badge-primary">Technical</span>
                  {% endif %}
                </div>
                <p class="summary">{{ project.summary }}</p>
                <a href="{{ project.url }}" class="card-link">
                  Read the full story
                  <span class="visually-hidden">about {{ project.title }}</span>
                </a>
              </article>
            </li>
          {% endfor %}
        </ol>
      {% endfor %}
    </section>
  {% else %}
    <div class="empty-state">
      <p>Portfolio projects coming soon.</p>
    </div>
  {% endif %}
</div>
```

**Why:**
- Liquid logic groups projects by year automatically
- Semantic HTML with proper accessibility
- Badge colors match category (product/technical)
- Empty state for graceful degradation
- Visually hidden text for screen readers

**Verification:**
- Page renders at `/portfolio/`
- Empty state shows when no projects exist
- HTML validates (proper heading hierarchy)
- No JavaScript errors

## Task 4: Create Example Portfolio Item (Placeholder)

**File:** `_portfolio/example-platform-scaling.md`

Create single example case study to verify collection works:

```markdown
---
layout: portfolio
title: "Platform Scaling for Hypergrowth"
date: 2023-06-01
role: "Chief Technology Officer"
company_context: "E-commerce Startup (Series B)"
category: technical
summary: "Rebuilt architecture to handle 10x user growth while reducing infrastructure costs by 40% and improving reliability to 99.9% uptime."
---

## The Context

[Placeholder: This section will describe the company stage, market situation, your role and mandate, and why this project mattered to the business.]

## The Challenge

[Placeholder: The specific problem you were solving, constraints, competing priorities, and why obvious solutions wouldn't work.]

## Your Approach

[Placeholder: Your strategic thinking, how you evaluated options, the non-obvious insight you made, and how you aligned stakeholders.]

## Key Decisions

[Placeholder: The 2-3 most critical choices, trade-offs you navigated, where you went against conventional wisdom, and moments where leadership mattered.]

## The Outcome

[Placeholder: Measurable business impact, technical improvements, team/organizational impact, and what changed as a result.]

## What You Learned

[Placeholder: Key insight that informs your work today, what you'd do differently, and how this shaped your leadership philosophy.]
```

**Why:**
- Tests collection configuration
- Provides structure template for future projects
- Placeholder content clearly marked
- Front matter includes all required fields

**Verification:**
- File appears in `_portfolio/` directory
- Project shows on `/portfolio/` timeline
- Individual page accessible at `/portfolio/example-platform-scaling/`
- Metadata renders correctly (date, role, badge, summary)

## Task 5: Local Testing & Responsive Verification

**Commands:**
```bash
bundle exec jekyll serve
```

**Test checklist:**

**Desktop (≥768px):**
- [ ] Timeline has center vertical line
- [ ] Cards alternate left/right
- [ ] Year marker centered with dot on line
- [ ] Cards have connector dots to timeline
- [ ] Hover effect works (lift + shadow)
- [ ] Badge displays correct color (Technical = primary blue)
- [ ] "Read the full story" link works

**Mobile (<768px):**
- [ ] Timeline line moves to left (20px)
- [ ] All cards stack vertically to right of line
- [ ] Year markers align with left line
- [ ] No horizontal scroll
- [ ] Cards readable and properly spaced
- [ ] Touch targets adequate (44px+)

**Keyboard Navigation:**
- [ ] Tab through timeline cards in logical order
- [ ] Focus indicators visible on links
- [ ] Enter activates case study links

**Screen Reader (test with VoiceOver/NVDA if available):**
- [ ] Timeline announced as "Career timeline" landmark
- [ ] Year markers announced as headings (h2)
- [ ] Each project announced as article
- [ ] Time elements announced with full date
- [ ] "Read the full story about [Title]" provides context

**Why:** Comprehensive testing ensures timeline works across devices and meets accessibility standards before adding more content.

</tasks>

<verification>
After completing all tasks:

1. **Collection Configuration:**
   - [ ] `_config.yml` contains portfolio collection config
   - [ ] Jekyll builds successfully (`bundle exec jekyll serve`)
   - [ ] No build warnings or errors

2. **Timeline Component:**
   - [ ] `_sass/_timeline.scss` exists with all styles
   - [ ] Imported in `assets/css/main.scss`
   - [ ] CSS compiles without errors
   - [ ] Timeline uses design system tokens

3. **Portfolio Page:**
   - [ ] `/portfolio.html` exists and renders
   - [ ] Page accessible at `/portfolio/`
   - [ ] Empty state shows gracefully when no projects
   - [ ] Liquid logic groups by year correctly
   - [ ] Semantic HTML with proper ARIA labels

4. **Example Project:**
   - [ ] `_portfolio/example-platform-scaling.md` exists
   - [ ] Project appears on timeline at June 2023
   - [ ] Individual page renders at `/portfolio/example-platform-scaling/`
   - [ ] All metadata displays (date, role, company, badge, summary)
   - [ ] Badge shows "Technical" with primary blue color

5. **Responsive Behavior:**
   - [ ] Desktop: alternating left/right cards, center line
   - [ ] Mobile: stacked cards, left-side line
   - [ ] No horizontal scroll on any screen size
   - [ ] Touch-friendly on mobile (44px+ targets)

6. **Accessibility:**
   - [ ] Timeline uses semantic HTML (`<section>`, `<ol>`, `<article>`)
   - [ ] Proper heading hierarchy (h1 → h2 → h3)
   - [ ] `<time>` elements with `datetime` attributes
   - [ ] `aria-label` on timeline section
   - [ ] Visually hidden text for screen readers
   - [ ] Keyboard navigation works logically
   - [ ] Focus indicators visible

7. **Visual Polish:**
   - [ ] Timeline line and dots render correctly
   - [ ] Cards have subtle hover effect
   - [ ] Badges render with appropriate colors
   - [ ] Typography follows design system
   - [ ] Spacing consistent with existing pages

</verification>

<success_criteria>

- [ ] Portfolio timeline infrastructure fully functional
- [ ] Jekyll `_portfolio` collection configured and building
- [ ] Timeline CSS component created with responsive behavior
- [ ] Main portfolio page renders with vertical timeline layout
- [ ] Desktop: alternating left/right cards with center line
- [ ] Mobile: stacked cards with left-side line
- [ ] Example project demonstrates complete structure
- [ ] All accessibility requirements met (semantic HTML, ARIA, keyboard nav)
- [ ] No horizontal scroll on any device size
- [ ] Timeline extends existing design system consistently
- [ ] Ready to add more case study projects

**Visual success:** A visitor sees a clean vertical timeline at `/portfolio/` with one example project card showing date, title, role, company context, "Technical" badge, summary, and "Read the full story" link. On mobile, the layout gracefully stacks without horizontal scroll.

**Technical success:** Jekyll collection configured, timeline CSS component built, Liquid templating logic working, responsive breakpoints functioning, accessibility standards met.

</success_criteria>

<output>
**Files created/modified:**
1. `_config.yml` - Portfolio collection configuration
2. `_sass/_timeline.scss` - Timeline component styles
3. `assets/css/main.scss` - Import timeline styles
4. `portfolio.html` - Main portfolio timeline page
5. `_portfolio/example-platform-scaling.md` - Example case study

**Atomic commits:**
1. `feat(phase4-timeline): configure Jekyll portfolio collection`
2. `feat(phase4-timeline): create timeline CSS component with responsive layout`
3. `feat(phase4-timeline): create portfolio page with vertical timeline`
4. `feat(phase4-timeline): add example case study to verify collection`
5. `test(phase4-timeline): verify responsive behavior and accessibility`

**Next:** phase4-case-studies-PLAN.md (case study layout template and additional placeholder projects)
</output>
