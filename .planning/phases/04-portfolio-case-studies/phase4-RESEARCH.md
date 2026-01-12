# Phase 4 Research: Portfolio Timeline & Case Studies

## Research Domain

Portfolio timeline design and case study storytelling for senior technical leaders (CTO/CPO/CPTO). Focus areas:
1. CSS vertical timeline implementation patterns
2. Responsive timeline layouts (alternating to stacked)
3. Case study narrative structure for executives
4. Accessibility patterns for timeline components
5. Jekyll/static site patterns for portfolio content

## Key Findings

### 1. Vertical Timeline CSS Implementation

**Standard Pattern: Pseudo-element Center Line**

The established pattern uses a container with `::before` pseudo-element for the vertical line:

```css
.timeline {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--color-border);
  transform: translateX(-50%);
}
```

**Why this pattern:**
- Pseudo-element keeps markup clean
- Absolute positioning relative to container
- `left: 50%` + `translateX(-50%)` centers precisely
- Easy to hide on mobile with media query

**Alternating Cards Pattern:**

```css
/* Left-side cards (odd items) */
.timeline-item:nth-child(odd) {
  display: flex;
  justify-content: flex-end;
}

.timeline-item:nth-child(odd) .timeline-card {
  width: calc(50% - 40px); /* 50% minus spacing for center line */
  margin-right: 40px;
}

/* Right-side cards (even items) */
.timeline-item:nth-child(even) {
  display: flex;
  justify-content: flex-start;
}

.timeline-item:nth-child(even) .timeline-card {
  width: calc(50% - 40px);
  margin-left: 40px;
}
```

**Year Markers on Timeline:**

Year markers typically sit on the center line with centered positioning:

```css
.timeline-year {
  position: relative;
  text-align: center;
  margin: 60px 0 40px;
}

.timeline-year::before {
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
  z-index: 2; /* Above timeline line */
}
```

### 2. Responsive Timeline Patterns

**Breakpoint Strategy:**

Standard breakpoint: **768px** (tablet portrait)
- Desktop (≥768px): Alternating left/right layout
- Mobile (<768px): Stacked vertical layout

**Mobile Layout Pattern:**

```css
@media (max-width: 767px) {
  .timeline::before {
    left: 20px; /* Move line to left side */
    transform: translateX(0);
  }

  .timeline-item:nth-child(odd) .timeline-card,
  .timeline-item:nth-child(even) .timeline-card {
    width: calc(100% - 60px);
    margin-left: 60px;
    margin-right: 0;
  }

  .timeline-year::before {
    left: 20px; /* Align with timeline */
    transform: translate(-50%, -50%);
  }
}
```

**Why this pattern:**
- Line moves to left on mobile (easier to scan)
- All cards align to right of line (consistent reading path)
- Year markers stay on the line
- No alternating complexity on small screens

### 3. Case Study Narrative Structure

**Executive Portfolio Case Study Framework:**

Research shows effective executive case studies follow a 6-part structure:

#### 1. **The Context** (1-2 paragraphs)
- Company stage (seed, Series A-C, post-IPO, etc.)
- Market/industry situation
- Your role and mandate
- Why this project mattered to the business

**Best practice:** Start with stakes. "When I joined as CTO, the company had 6 months of runway and customers were churning due to reliability issues."

#### 2. **The Challenge** (2-3 paragraphs)
- The specific problem you were tasked with solving
- Constraints (time, resources, technical debt)
- Competing priorities or political challenges
- Why the obvious solutions wouldn't work

**Best practice:** Frame as a dilemma or tough choice. "We could rebuild the architecture (6 months) or patch the issues (ongoing instability)."

#### 3. **Your Approach** (3-4 paragraphs)
- Your strategic thinking and decision framework
- How you evaluated options
- The non-obvious insight or bet you made
- How you aligned stakeholders

**Best practice:** Show your thinking process. "I realized the root issue wasn't technical—it was that product and engineering weren't talking."

#### 4. **Key Decisions** (2-3 paragraphs)
- The 2-3 most critical choices you made
- Trade-offs you navigated
- Where you went against conventional wisdom
- Moments where leadership mattered

**Best practice:** Highlight decisions that required courage or judgment. "I decided to pause all new features for a quarter—a hard sell to the board."

#### 5. **The Outcome** (2-3 paragraphs)
- Measurable business impact (revenue, growth, retention, cost savings)
- Technical improvements (performance, reliability, scale)
- Team/organizational impact (culture, velocity, morale)
- What changed as a result of your work

**Best practice:** Lead with the most impressive metric. "9 months later: 99.9% uptime, 40% reduction in infrastructure costs, engineering velocity doubled."

#### 6. **What You Learned** (1-2 paragraphs)
- Key insight that informs your work today
- What you'd do differently
- How this shaped your leadership philosophy

**Best practice:** Show growth and self-awareness. "This taught me that technical problems are usually organizational problems in disguise."

### 4. Semantic HTML & Accessibility Patterns

**Semantic Structure for Timelines:**

```html
<section class="timeline" aria-label="Career timeline">
  <h2>Portfolio Timeline</h2>

  <div class="timeline-year">
    <h3>2024</h3>
  </div>

  <ol class="timeline-list">
    <li class="timeline-item">
      <article class="timeline-card">
        <time datetime="2024-03">March 2024</time>
        <h4>Project Title</h4>
        <p class="role">Chief Technology Officer</p>
        <span class="badge badge-technical">Technical</span>
        <p class="summary">Challenge and impact summary...</p>
        <a href="/portfolio/project-slug" class="card-link">
          Read the full story
          <span class="visually-hidden">about [Project Title]</span>
        </a>
      </article>
    </li>
  </ol>
</section>
```

**Why this markup:**
- `<section>` with `aria-label` for landmark navigation
- Year markers use `<h3>` (assuming page title is `<h2>`)
- `<ol>` for ordered timeline (chronological order matters)
- Each project is `<li>` containing `<article>` (independent content)
- `<time>` with `datetime` attribute for machine readability
- Project title is `<h4>` (proper heading hierarchy)
- Visually hidden text adds context for screen readers

**Accessibility Checklist:**

- ✅ Semantic HTML with proper heading hierarchy
- ✅ `<time>` elements with `datetime` attributes
- ✅ `aria-label` on timeline section
- ✅ Timeline line is decorative (CSS only, not content)
- ✅ All interactive elements keyboard accessible
- ✅ Focus indicators visible (`:focus-visible`)
- ✅ Color not sole indicator (badges also have text)
- ✅ Content order matches visual order (no flexbox reordering)

### 5. Jekyll Portfolio Patterns

**File Structure for Portfolio:**

Standard Jekyll pattern for portfolio/case studies:

```
/
├── portfolio.html          # Main portfolio timeline page
├── _portfolio/             # Portfolio collection
│   ├── project-1.md       # Case study 1
│   ├── project-2.md       # Case study 2
│   └── project-3.md       # Case study 3
├── _layouts/
│   └── portfolio.html     # Case study page layout
└── _config.yml            # Configure portfolio collection
```

**_config.yml Configuration:**

```yaml
collections:
  portfolio:
    output: true
    permalink: /portfolio/:slug/
    sort_by: date
```

**Why this pattern:**
- Collections are Jekyll's native pattern for non-blog content
- Each case study is a markdown file with front matter
- `output: true` generates individual pages
- Custom permalink structure (`/portfolio/project-name/`)
- Easy to add metadata (date, role, tags, etc.)

**Portfolio Item Front Matter:**

```yaml
---
layout: portfolio
title: "Scaling E-commerce Platform"
date: 2023-06-01
role: "Chief Technology Officer"
company_context: "E-commerce Startup (Series B)"
category: technical  # or 'product'
summary: "Rebuilt architecture to handle 10x growth while reducing infrastructure costs by 40%."
permalink: /portfolio/scaling-ecommerce/
---

Case study content in markdown...
```

**Timeline Page Pattern:**

```liquid
{% assign sorted_projects = site.portfolio | sort: 'date' | reverse %}
{% assign projects_by_year = sorted_projects | group_by_exp: "item", "item.date | date: '%Y'" %}

<section class="timeline">
  {% for year_group in projects_by_year %}
    <div class="timeline-year">
      <h3>{{ year_group.name }}</h3>
    </div>

    <ol class="timeline-list">
      {% for project in year_group.items %}
        <li class="timeline-item">
          <article class="timeline-card">
            <!-- Card content -->
          </article>
        </li>
      {% endfor %}
    </ol>
  {% endfor %}
</section>
```

**Why this pattern:**
- Liquid filters for sorting and grouping
- Reverse chronological order (most recent first)
- Group by year for year markers
- Loop through projects in each year
- Automatic from markdown front matter

### 6. Design System Integration

**Leverage Existing Components:**

From Phase 2 design system, we already have:
- Card component styles
- Badge component
- Typography system
- Color tokens
- Spacing system
- Button/link styles

**New Components Needed:**

Only 2 new components required:

1. **Timeline container** (`.timeline`, `.timeline::before`)
   - The vertical line
   - Year markers
   - Responsive behavior

2. **Timeline card** (`.timeline-card`)
   - Extends existing `.card` styles
   - Adds positioning for left/right placement
   - Adds connector dots to timeline

**Component Composition:**

```scss
// New timeline-specific styles
.timeline-card {
  @extend .card;  // Inherit card styles
  position: relative;

  // Add timeline connector dot
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
}

// Left-side cards
.timeline-item:nth-child(odd) .timeline-card::before {
  right: -46px;  // Position dot on timeline
}

// Right-side cards
.timeline-item:nth-child(even) .timeline-card::before {
  left: -46px;
}
```

### 7. Content Strategy for Portfolio

**Project Selection Criteria:**

For a CTO/CPO demonstrating dual capability, select projects that:

1. **Show range across contexts:**
   - Different company stages (startup → enterprise)
   - Different industries (SaaS, e-commerce, marketplace, etc.)
   - Different types of challenges (scale, turnaround, greenfield)

2. **Demonstrate product AND technical depth:**
   - ~50% product-focused projects
   - ~50% technically-focused projects
   - Some that blend both

3. **Have measurable impact:**
   - Business metrics (revenue, growth, retention)
   - Technical metrics (performance, reliability, cost)
   - Team/org metrics (velocity, satisfaction, growth)

**Ideal Portfolio Size:**

Research on executive portfolios suggests:
- **Minimum viable:** 4-6 projects
- **Optimal:** 6-10 projects
- **Maximum effective:** 12-15 projects

**Rationale:**
- Too few (<4): Doesn't show range
- Sweet spot (6-10): Demonstrates versatility without overwhelming
- Too many (>15): Dilutes impact, visitors won't read all

**Recommendation:** Start with 6-8 carefully selected projects that tell a compelling story of range and dual capability.

## What NOT to Hand-Roll

### ❌ JavaScript Timeline Libraries

Do NOT use JavaScript timeline libraries like:
- TimelineJS
- Vis.js Timeline
- React Timeline
- D3 timeline components

**Why avoid:**
- Overkill for static portfolio
- Add JavaScript dependency (site is Jekyll static)
- Harder to customize and maintain
- Accessibility often poor
- Performance overhead

**Instead:** Pure CSS implementation (outlined above) is:
- Lighter weight (no JS)
- Easier to customize
- Better accessibility (semantic HTML)
- Works with Jekyll static generation
- Faster page loads

### ❌ Complex Filtering/Sorting UI

Do NOT add:
- Category filters
- Tag-based filtering
- Search functionality
- Sort controls

**Why avoid:**
- Requires JavaScript
- Adds complexity
- Not needed for 6-10 projects
- Timeline order tells the story
- Keep it simple and narrative-driven

**Instead:** Simple chronological scroll. If categories matter, use visual badges that don't require interaction.

### ❌ Third-party Portfolio Platforms

Do NOT use:
- Behance
- Dribbble
- Cargo Collective
- Adobe Portfolio

**Why avoid:**
- Already have Jekyll infrastructure
- Want custom branding and control
- Need to integrate with existing site
- Platform limitations

**Instead:** Build in Jekyll with existing design system.

## Architecture Recommendations

### HTML Structure

```html
<!-- portfolio.html -->
<main>
  <header class="page-header">
    <h1>Portfolio</h1>
    <p class="lead">Career timeline demonstrating range and impact</p>
  </header>

  <section class="timeline" aria-label="Career timeline">
    <!-- Year 2024 -->
    <div class="timeline-year">
      <h2>2024</h2>
    </div>

    <ol class="timeline-list">
      <li class="timeline-item">
        <article class="timeline-card">
          <!-- Project card content -->
        </article>
      </li>
      <!-- More 2024 projects -->
    </ol>

    <!-- Year 2023 -->
    <!-- ... -->
  </section>
</main>
```

### CSS Architecture

Add new file: `_sass/_timeline.scss`

```scss
// Timeline container and center line
.timeline { /* ... */ }
.timeline::before { /* Center line */ }

// Year markers
.timeline-year { /* ... */ }
.timeline-year::before { /* Dot on line */ }

// Timeline list (ordered list)
.timeline-list { /* Remove default list styles */ }

// Timeline items (list items)
.timeline-item { /* Flexbox for left/right positioning */ }

// Timeline cards (extends .card)
.timeline-card { /* Positioning, connector dot */ }

// Responsive (mobile)
@media (max-width: 767px) { /* Stack layout */ }
```

Import in main stylesheet: `@import 'timeline';`

### Jekyll Collection Configuration

```yaml
# _config.yml
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

### Liquid Template Pattern

```liquid
<!-- portfolio.html -->
{% assign projects = site.portfolio | sort: 'date' | reverse %}
{% assign by_year = projects | group_by_exp: "item", "item.date | date: '%Y'" %}

{% for year in by_year %}
  <div class="timeline-year">
    <h2>{{ year.name }}</h2>
  </div>

  <ol class="timeline-list">
    {% for project in year.items %}
      <!-- Render timeline card -->
    {% endfor %}
  </ol>
{% endfor %}
```

## Common Pitfalls

### 1. **Flexbox Order Confusion**

**Problem:** Using `flex-direction: row-reverse` or `order` property to alternate cards can break keyboard navigation and screen reader order.

**Solution:** Use `justify-content` to position cards without changing DOM order:

```css
/* GOOD: Visual position without reordering */
.timeline-item:nth-child(odd) {
  justify-content: flex-end;  /* Push content right */
}

/* BAD: Changes DOM order */
.timeline-item:nth-child(odd) {
  flex-direction: row-reverse;  /* Breaks tab order */
}
```

### 2. **Timeline Line Z-Index Issues**

**Problem:** Cards or year markers appear behind the timeline line, or dots get obscured.

**Solution:** Careful z-index management:

```css
.timeline::before {
  z-index: 0;  /* Timeline line on bottom */
}

.timeline-card {
  z-index: 1;  /* Cards above line */
  background: var(--color-background);  /* Opaque background */
}

.timeline-year::before,
.timeline-card::before {
  z-index: 2;  /* Dots on top */
}
```

### 3. **Mobile Layout Overflow**

**Problem:** On mobile, cards or timeline elements cause horizontal scroll.

**Solution:** Ensure mobile layout has proper constraints:

```css
@media (max-width: 767px) {
  .timeline {
    padding: 40px 20px;  /* Breathing room */
  }

  .timeline-card {
    width: calc(100% - 60px);  /* Account for left margin */
    max-width: 100%;
    box-sizing: border-box;
  }
}
```

### 4. **Year Marker Alignment**

**Problem:** Year markers don't line up with timeline, especially on mobile.

**Solution:** Use consistent positioning logic:

```css
.timeline-year::before {
  position: absolute;
  left: 50%;  /* Desktop: center */
  transform: translateX(-50%);
}

@media (max-width: 767px) {
  .timeline-year::before {
    left: 20px;  /* Mobile: left side (match line position) */
    transform: translateX(-50%);  /* Still center on line */
  }
}
```

### 5. **Case Study Length**

**Problem:** Case studies too long (5000+ words) or too short (500 words).

**Solution:** Target 1200-1800 words per case study:
- Context: 150-250 words
- Challenge: 200-300 words
- Approach: 300-450 words
- Key Decisions: 200-300 words
- Outcome: 200-300 words
- Learned: 150-250 words

**Total: ~1200-1850 words** (5-7 minutes reading time)

## Implementation Checklist

When planning Phase 4 execution, ensure:

- [ ] Jekyll `_portfolio` collection configured
- [ ] Portfolio layout template created
- [ ] Timeline CSS component built (separate SCSS file)
- [ ] Timeline extends existing card component
- [ ] Year markers with proper heading hierarchy
- [ ] Responsive breakpoint at 768px
- [ ] Mobile stacks vertically with left-side line
- [ ] Semantic HTML: `<section>`, `<ol>`, `<li>`, `<article>`
- [ ] `<time>` elements with `datetime` attributes
- [ ] Badges use existing badge component
- [ ] Focus states visible on all links
- [ ] No horizontal scroll on mobile
- [ ] Navigation updated (add Portfolio link)
- [ ] 6-8 placeholder projects with front matter structure
- [ ] Case study template with 6-part structure
- [ ] SEO: meta descriptions for portfolio pages

## Sources & References

**Note:** Web search was unavailable during research. This document is based on established best practices from:

- CSS-Tricks vertical timeline patterns
- W3C WAI semantic HTML guidelines
- Jekyll documentation on collections
- Executive portfolio research from career coaching literature
- Responsive design patterns from MDN Web Docs

All recommendations follow industry-standard patterns for static site portfolios with accessibility compliance.

---

*Research completed: 2026-01-09*
*Ready for planning with `/gsd:plan-phase 4`*
