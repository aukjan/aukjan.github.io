<objective>
Create case study page layout template and populate portfolio with 6-8 placeholder projects demonstrating product/technical versatility across diverse contexts.
</objective>

<execution_context>
@phase4-CONTEXT.md - Case study structure: Context, Challenge, Approach, Decisions, Outcome, Learned
@phase4-RESEARCH.md - Executive case study framework (6-part structure, 1200-1800 words target)
@_layouts/page.html - Existing page layout for reference
@_portfolio/example-platform-scaling.md - Example front matter structure
</execution_context>

<context>
**What we're building:**
- Portfolio layout template (`_layouts/portfolio.html`)
- 6-8 placeholder case studies with proper front matter
- Mix of product and technical projects (~50/50 split)
- Generic company contexts (no confidential info)
- Placeholder content with clear 6-part structure

**Case study structure (from research):**
1. **The Context** (1-2 paragraphs, 150-250 words)
2. **The Challenge** (2-3 paragraphs, 200-300 words)
3. **Your Approach** (3-4 paragraphs, 300-450 words)
4. **Key Decisions** (2-3 paragraphs, 200-300 words)
5. **The Outcome** (2-3 paragraphs, 200-300 words)
6. **What You Learned** (1-2 paragraphs, 150-250 words)

**Target:** 1200-1800 words per case study (5-7 min reading time)

**Project selection criteria:**
- Show range across contexts (startup → enterprise, different industries)
- Demonstrate product AND technical depth
- Mix of company stages and challenge types
- Have measurable impact potential

**Key decisions:**
- Start with 7 projects (3 product-focused, 4 technical-focused)
- Placeholder content clearly marked for future replacement
- Front matter structure consistent across all projects
- No company names or confidential details
</context>

<tasks>

## Task 1: Create Portfolio Case Study Layout Template

**File:** `_layouts/portfolio.html`

Create layout template for individual case study pages:

```html
---
layout: default
---

<article class="portfolio-case-study">
  <div class="container container-narrow">
    <header class="case-study-header">
      <nav class="breadcrumb" aria-label="Breadcrumb">
        <a href="/portfolio">← Back to Portfolio</a>
      </nav>

      <div class="case-study-meta">
        <time datetime="{{ page.date | date: '%Y-%m' }}">{{ page.date | date: '%B %Y' }}</time>
        {% if page.category == 'product' %}
          <span class="badge badge-accent">Product</span>
        {% elsif page.category == 'technical' %}
          <span class="badge badge-primary">Technical</span>
        {% endif %}
      </div>

      <h1>{{ page.title }}</h1>

      <div class="case-study-intro">
        <p class="role"><strong>Role:</strong> {{ page.role }}</p>
        <p class="company-context"><strong>Context:</strong> {{ page.company_context }}</p>
        <p class="lead">{{ page.summary }}</p>
      </div>
    </header>

    <div class="case-study-content">
      {{ content }}
    </div>

    <footer class="case-study-footer">
      <a href="/portfolio" class="btn btn-primary">← Back to Portfolio</a>
      <a href="/contact" class="btn btn-secondary">Get in Touch</a>
    </footer>
  </div>
</article>
```

**File:** `_sass/_components.scss`

Add case study-specific styles (append to existing file):

```scss
// ============================================================================
// Portfolio Case Study Styles
// ============================================================================

.portfolio-case-study {
  padding: var(--space-2xl) 0;
}

.case-study-header {
  margin-bottom: var(--space-2xl);
  padding-bottom: var(--space-xl);
  border-bottom: 1px solid var(--color-border);
}

.breadcrumb {
  margin-bottom: var(--space-md);

  a {
    font-size: var(--text-sm);
    color: var(--color-text-light);
    text-decoration: none;
    transition: color 0.2s;

    &:hover {
      color: var(--color-primary);
    }
  }
}

.case-study-meta {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  margin-bottom: var(--space-md);
  font-size: var(--text-sm);
  color: var(--color-text-muted);
}

.case-study-intro {
  margin-top: var(--space-lg);

  .role,
  .company-context {
    font-size: var(--text-base);
    color: var(--color-text-light);
    margin-bottom: var(--space-xs);
  }

  .lead {
    font-size: var(--text-lg);
    line-height: var(--leading-relaxed);
    color: var(--color-text);
    margin-top: var(--space-md);
    font-weight: var(--font-medium);
  }
}

.case-study-content {
  h2 {
    font-size: var(--text-2xl);
    font-weight: var(--font-bold);
    color: var(--color-text);
    margin-top: var(--space-2xl);
    margin-bottom: var(--space-md);
    font-family: var(--font-sans);
  }

  h3 {
    font-size: var(--text-xl);
    font-weight: var(--font-semibold);
    color: var(--color-text);
    margin-top: var(--space-xl);
    margin-bottom: var(--space-sm);
    font-family: var(--font-sans);
  }

  p {
    font-size: var(--text-base);
    line-height: var(--leading-relaxed);
    color: var(--color-text);
    margin-bottom: var(--space-md);
  }

  ul, ol {
    margin: var(--space-md) 0;
    padding-left: var(--space-xl);

    li {
      margin-bottom: var(--space-sm);
      line-height: var(--leading-relaxed);
    }
  }

  blockquote {
    border-left: 4px solid var(--color-primary);
    padding-left: var(--space-lg);
    margin: var(--space-xl) 0;
    font-style: italic;
    color: var(--color-text-light);
  }
}

.case-study-footer {
  display: flex;
  gap: var(--space-md);
  align-items: center;
  margin-top: var(--space-2xl);
  padding-top: var(--space-xl);
  border-top: 1px solid var(--color-border);
}

// Responsive
@media (max-width: 767px) {
  .case-study-footer {
    flex-direction: column;
    align-items: stretch;

    .btn {
      width: 100%;
      text-align: center;
    }
  }
}
```

**Why:**
- Clean, focused reading experience
- Breadcrumb navigation for easy return
- Prominent display of role, context, summary
- Typography optimized for long-form reading
- Footer CTAs for portfolio and contact

**Verification:**
- Layout renders with proper styling
- Breadcrumb link works
- Badge colors match category
- Content area has good typography
- Footer buttons functional

## Task 2: Create Technical Project Placeholders (4 projects)

**File:** `_portfolio/01-platform-scaling.md`

```markdown
---
layout: portfolio
title: "Platform Scaling for Hypergrowth"
date: 2023-06-01
role: "Chief Technology Officer"
company_context: "E-commerce Startup (Series B, 50-person team)"
category: technical
summary: "Rebuilt architecture to handle 10x user growth while reducing infrastructure costs by 40% and improving reliability to 99.9% uptime."
---

## The Context

[Placeholder: Describe joining an e-commerce startup experiencing rapid growth. Company had just closed Series B, user base growing 20% month-over-month, but infrastructure couldn't keep up. Frequent outages affecting revenue and customer trust. Board pressuring for reliability while maintaining growth trajectory.]

## The Challenge

[Placeholder: Monolithic architecture hitting scaling limits. Database becoming bottleneck. Infrastructure costs growing faster than revenue. Engineering team spending 60% of time on incidents vs. new features. Pressure to scale quickly without massive rewrite that would stall product development for 6+ months.]

## Your Approach

[Placeholder: Decided on incremental modernization strategy rather than full rewrite. Identified critical bottlenecks through data analysis. Prioritized high-impact, low-risk improvements. Split monolith gradually using strangler fig pattern. Implemented observability first to make informed decisions. Aligned engineering and product on delivery cadence during transition.]

## Key Decisions

[Placeholder: Key decision 1 - Chose managed services (RDS, ElastiCache) over self-hosting to reduce operational burden. Key decision 2 - Implemented feature flags and progressive rollouts to mitigate risk. Key decision 3 - Paused non-critical features for one quarter to focus team on platform stability—hard sell to stakeholders but necessary.]

## The Outcome

[Placeholder: 9 months later - 99.9% uptime achieved, infrastructure costs reduced 40% through optimization, page load times improved 60%, engineering velocity doubled, team morale significantly improved, positioned company for next stage of growth.]

## What You Learned

[Placeholder: Technical problems are usually organizational problems in disguise. Alignment between engineering and product is critical. Incremental progress beats big-bang rewrites. Observability enables good decisions. Sometimes you have to slow down to speed up.]
```

**File:** `_portfolio/02-security-architecture.md`

```markdown
---
layout: portfolio
title: "Enterprise Security Architecture Overhaul"
date: 2022-03-01
role: "Head of Engineering"
company_context: "Enterprise SaaS Company (Series C, 200-person team)"
category: technical
summary: "Led security transformation achieving SOC 2 Type II certification while implementing zero-trust architecture across 50+ microservices."
---

## The Context

[Placeholder: Enterprise SaaS company needed to move upmarket to enterprise customers. Security posture inadequate for enterprise deals. Sales losing deals due to security concerns. Board mandated SOC 2 compliance within 12 months. Existing architecture built for speed, not enterprise security requirements.]

## The Challenge

[Placeholder: 50+ microservices with inconsistent security practices. No centralized identity management. Audit logs scattered across systems. Compliance requirements affecting every team. Engineering resistance to "slowing down" for security. Need to achieve certification without grinding product development to halt.]

## Your Approach

[Placeholder: Formed dedicated security working group with representatives from each team. Conducted comprehensive security audit to identify gaps. Built centralized authentication and authorization system. Implemented gradual migration path with clear milestones. Created security champions program within engineering teams. Made security part of definition of done.]

## Key Decisions

[Placeholder: Key decision 1 - Invested in security tooling and automation vs. manual processes. Key decision 2 - Made security a product requirement, not a separate workstream. Key decision 3 - Hired fractional CISO to guide certification process rather than learning as we go.]

## The Outcome

[Placeholder: SOC 2 Type II certified in 10 months. Zero-trust architecture implemented across all services. Security incident response time reduced 80%. Enterprise sales pipeline grew 3x post-certification. Created repeatable security patterns for future services. Team learned security is everyone's responsibility.]

## What You Learned

[Placeholder: Security can't be bolted on—it must be built in from the start. Compliance certifications accelerate good engineering practices. Culture change requires both top-down mandate and bottom-up champions. Investment in tooling pays for itself quickly. Security and velocity aren't opposites when done right.]
```

**File:** `_portfolio/03-data-infrastructure.md`

```markdown
---
layout: portfolio
title: "Real-Time Data Infrastructure"
date: 2021-09-01
role: "Engineering Manager"
company_context: "B2B SaaS Platform (Series A, 30-person team)"
category: technical
summary: "Built real-time data pipeline enabling customer analytics dashboards, reducing data latency from hours to seconds while processing 10M+ events daily."
---

## The Context

[Placeholder: B2B SaaS platform generating massive event data but unable to provide real-time insights. Customers requesting live analytics dashboards for their business decisions. Existing batch ETL processes running nightly, 12+ hour data lag. Competitive pressure from platforms offering real-time capabilities.]

## The Challenge

[Placeholder: Legacy batch processing inadequate for real-time needs. No streaming infrastructure in place. Small team with no prior experience building data pipelines. Budget constraints limiting infrastructure spending. Need to maintain existing analytics while building new system. Can't afford data loss during migration.]

## Your Approach

[Placeholder: Evaluated streaming platforms (Kafka, Kinesis, Pub/Sub). Started with managed services to minimize operational burden. Built event schema registry for data consistency. Implemented dual-write pattern for safe migration. Created self-service dashboard builder for customers. Phased rollout starting with non-critical data streams.]

## Key Decisions

[Placeholder: Key decision 1 - Chose managed cloud services (AWS Kinesis) over self-hosted Kafka to focus team on business logic. Key decision 2 - Built abstractions allowing pipeline logic changes without customer impact. Key decision 3 - Invested in monitoring and alerting from day one.]

## The Outcome

[Placeholder: Real-time analytics platform launched in 5 months. Processing 10M+ events per day with <5 second latency. Customer satisfaction scores improved 35%. New feature became key differentiator in sales. Platform scaled to 50M+ events/day without major changes. Team gained valuable distributed systems experience.]

## What You Learned

[Placeholder: Managed services accelerate delivery for small teams. Clear schemas and contracts prevent data quality issues. Monitoring is not optional for distributed systems. Phased rollouts reduce risk significantly. Build for the scale you need tomorrow, not 10x beyond it.]
```

**File:** `_portfolio/04-technical-debt-turnaround.md`

```markdown
---
layout: portfolio
title: "Technical Debt Turnaround"
date: 2020-11-01
role: "Senior Engineering Lead"
company_context: "Legacy Software Company (Post-acquisition integration)"
category: technical
summary: "Systematically reduced technical debt by 60% while maintaining product velocity, transforming codebase from liability to asset."
---

## The Context

[Placeholder: Joined company post-acquisition to integrate acquired legacy product. Codebase accumulated 8+ years of technical debt. Test coverage below 20%. Deployment process manual and error-prone. Engineering morale low due to constant firefighting. New parent company considering sunset vs. modernization.]

## The Challenge

[Placeholder: Massive technical debt across infrastructure, code quality, and processes. Business pressure to integrate with parent company systems quickly. Engineering team burned out and skeptical of "yet another improvement initiative." No clear inventory of debt or prioritization framework. Can't stop feature development to fix everything.]

## Your Approach

[Placeholder: Conducted comprehensive technical debt audit with team input. Created debt inventory with business impact scoring. Implemented "boy scout rule"—leave code better than you found it. Allocated 20% of every sprint to debt reduction. Automated high-pain manual processes first. Celebrated small wins to build momentum and morale.]

## Key Decisions

[Placeholder: Key decision 1 - Focus on incremental improvement vs. big-bang rewrite. Key decision 2 - Make technical debt visible to product and business stakeholders. Key decision 3 - Implement automated testing as prerequisite for any new feature work.]

## The Outcome

[Placeholder: 18 months later - Test coverage improved to 75%. Deployment time reduced from 4 hours to 15 minutes. Production incidents decreased 70%. Team velocity actually increased despite debt paydown. Engineering satisfaction scores improved significantly. Product chosen for continued investment vs. sunset.]

## What You Learned

[Placeholder: Technical debt is a business problem, not just an engineering problem. Visibility and measurement enable prioritization. Small consistent improvements beat heroic efforts. Team morale affects everything—fix culture alongside code. Automation is force multiplier for small teams.]
```

## Task 3: Create Product Project Placeholders (3 projects)

**File:** `_portfolio/05-product-market-fit-pivot.md`

```markdown
---
layout: portfolio
title: "Product-Market Fit Pivot"
date: 2022-10-01
role: "Head of Product"
company_context: "Consumer Marketplace (Seed stage, 15-person team)"
category: product
summary: "Led product pivot discovering new market segment, growing monthly active users 5x and achieving product-market fit within 6 months."
---

## The Context

[Placeholder: Consumer marketplace struggling with user acquisition and retention. Burn rate concerning investors. Initial target market (college students) not converting. User research showing different segment finding unexpected value. 6 months runway remaining—pivot or perish decision time.]

## The Challenge

[Placeholder: Core product assumption wrong—students wanted marketplace but weren't willing to pay. Different user segment (young professionals) using product in unintended way with higher engagement. Fear of alienating existing small user base. Engineering had just built features for college market. Need to move fast but validate before full pivot.]

## Your Approach

[Placeholder: Conducted intensive user research with high-engagement users. Built minimal feature set targeting new segment. Ran controlled experiment with both markets simultaneously. Used data to validate assumptions quickly. Aligned team and investors on pivot rationale. Created phased transition plan minimizing disruption.]

## Key Decisions

[Placeholder: Key decision 1 - Made data-driven bet on young professional segment vs. original college market. Key decision 2 - Deprecated features serving original market to focus resources. Key decision 3 - Repriced product for new segment's willingness to pay (3x higher).]

## The Outcome

[Placeholder: 6 months post-pivot - Monthly active users grew 5x. Revenue per user increased 4x. Retention improved from 15% to 60% month-over-month. Raised Series A on strength of new traction. Product-market fit metrics achieved. Team energized by clear direction and growth.]

## What You Learned

[Placeholder: Product-market fit is discovered, not designed. Watch what users do, not what they say. Kill your darlings—features serving old market prevented focus. Speed of validation matters more than perfection. Clear metrics enable confident pivots. Team alignment requires transparent data sharing.]
```

**File:** `_portfolio/06-ux-transformation.md`

```markdown
---
layout: portfolio
title: "UX Transformation for Enterprise Adoption"
date: 2021-05-01
role: "VP of Product"
company_context: "B2B SaaS Platform (Series B, 80-person team)"
category: product
summary: "Redesigned complex enterprise product reducing user onboarding time 60% and increasing feature adoption 45% through user-centered design."
---

## The Context

[Placeholder: Enterprise B2B product powerful but notoriously difficult to use. Customers requesting extensive training for new users. High support ticket volume related to UI confusion. Competitive products gaining ground with better UX. Customer churn analysis showed poor initial experience driving cancellations.]

## The Challenge

[Placeholder: Complex product built incrementally over 5 years without UX vision. Different features designed by different teams with inconsistent patterns. Resistance from power users who mastered current interface. Engineering skeptical of "just cosmetic changes." Need to modernize without disrupting existing workflows.]

## Your Approach

[Placeholder: Hired first dedicated UX researcher to understand user journeys. Conducted extensive usability testing with new and experienced users. Created unified design system across product. Implemented progressive disclosure for advanced features. Built onboarding flow based on user research. Rolled out changes gradually with opt-in beta period.]

## Key Decisions

[Placeholder: Key decision 1 - Invested in proper UX research vs. designing based on assumptions. Key decision 2 - Created design system before rebuilding features to ensure consistency. Key decision 3 - Gave power users early access and incorporated feedback to prevent backlash.]

## The Outcome

[Placeholder: 9 months later - New user onboarding time reduced 60% (4 hours → 90 minutes). Feature adoption increased 45%. Support ticket volume decreased 35%. Customer satisfaction scores improved significantly. Design system enabled faster feature development. Sales using improved UX as competitive advantage.]

## What You Learned

[Placeholder: UX debt compounds like technical debt. User research prevents expensive mistakes. Design systems pay dividends beyond initial investment. Change management matters—bring users along journey. Good UX isn't cosmetic, it's fundamental to product success.]
```

**File:** `_portfolio/07-marketplace-growth-strategy.md`

```markdown
---
layout: portfolio
title: "Marketplace Growth Strategy"
date: 2020-06-01
role: "Head of Product & Growth"
company_context: "B2C Marketplace (Series A, 40-person team)"
category: product
summary: "Designed and launched supply-side growth strategy scaling marketplace from 500 to 5,000 active sellers while maintaining quality standards."
---

## The Context

[Placeholder: Two-sided marketplace with healthy demand but supply-constrained. Buyer wait times increasing due to seller shortage. Competitive marketplaces aggressively recruiting sellers. Quality concerns preventing opening floodgates. Need 10x seller growth without compromising marketplace quality or trust.]

## The Challenge

[Placeholder: Classic chicken-and-egg marketplace problem tilted toward supply shortage. Vetting process manual and slow. No clear onboarding path for new sellers. Seller acquisition cost too high for unit economics. Existing sellers had inconsistent success—some thriving, many churning. Quality vs. quantity tension.]

## Your Approach

[Placeholder: Analyzed successful vs. churned sellers to identify success patterns. Built seller scorecard and quality framework. Automated portions of vetting process. Created self-service onboarding with progressive trust levels. Designed seller success playbook based on top performers. Implemented referral program incentivizing quality sellers to bring peers.]

## Key Decisions

[Placeholder: Key decision 1 - Built algorithmic quality scoring vs. manual review for scale. Key decision 2 - Created tiered seller system (bronze/silver/gold) with progressive benefits. Key decision 3 - Invested in seller education and success tooling vs. just acquisition.]

## The Outcome

[Placeholder: 12 months later - Active sellers grew 10x (500 → 5,000). Average seller revenue increased 30% through better tooling. Buyer satisfaction remained stable despite 10x supply growth. Seller acquisition cost reduced 50% through referral program. Quality scoring system became platform differentiator. Marketplace liquidity dramatically improved.]

## What You Learned

[Placeholder: Marketplace growth requires both sides—supply without demand fails. Quality frameworks enable sustainable scale. Seller success drives marketplace success. Automation enables scale, but human judgment still matters. Network effects compound when both sides thrive.]
```

## Task 3: Verify Collection and Metadata

**Verification checklist:**

**Front matter consistency:**
- [ ] All 7 projects have consistent front matter structure
- [ ] Dates span 2020-2023 showing career progression
- [ ] 4 technical projects, 3 product projects (~57/43 split)
- [ ] Roles show progression (Engineer → Lead → Manager → VP → CTO)
- [ ] Company contexts vary (startup/scale-up, seed/Series A/B/C)
- [ ] Summaries are 1-2 sentences with measurable outcomes
- [ ] No company names or confidential information

**Timeline display:**
- [ ] Projects grouped by year (2020, 2021, 2022, 2023)
- [ ] Most recent (2023) appears first
- [ ] Badges correctly show Product (accent) vs Technical (primary)
- [ ] All project cards render with proper styling
- [ ] Links to individual case studies work

**Case study pages:**
- [ ] All 7 projects have individual pages
- [ ] Layout template renders consistently
- [ ] Breadcrumb navigation works
- [ ] 6-part structure clearly visible with placeholders
- [ ] Footer buttons functional
- [ ] Typography readable and well-spaced

## Task 4: Build and Test Locally

**Commands:**
```bash
bundle exec jekyll serve
open http://localhost:4000/portfolio/
```

**Test each project:**
1. Platform Scaling (Technical, 2023-06)
2. Security Architecture (Technical, 2022-03)
3. Data Infrastructure (Technical, 2021-09)
4. Technical Debt (Technical, 2020-11)
5. Product Pivot (Product, 2022-10)
6. UX Transformation (Product, 2021-05)
7. Marketplace Growth (Product, 2020-06)

**Verify:**
- [ ] All 7 projects appear on timeline
- [ ] Correct chronological order (2023 → 2020)
- [ ] Year markers show: 2023, 2022, 2021, 2020
- [ ] 4 "Technical" badges (blue), 3 "Product" badges (amber)
- [ ] All "Read the full story" links work
- [ ] Individual pages render with placeholder content
- [ ] Back buttons return to timeline

</tasks>

<verification>
After completing all tasks:

1. **Portfolio Layout Template:**
   - [ ] `_layouts/portfolio.html` exists and renders
   - [ ] Case study styles in `_sass/_components.scss`
   - [ ] Breadcrumb navigation functional
   - [ ] Meta information displays correctly
   - [ ] Content area has proper typography
   - [ ] Footer CTAs work (Back to Portfolio, Get in Touch)

2. **Technical Projects (4):**
   - [ ] Platform Scaling (CTO, 2023, Technical)
   - [ ] Security Architecture (Head of Eng, 2022, Technical)
   - [ ] Data Infrastructure (Eng Manager, 2021, Technical)
   - [ ] Technical Debt (Senior Lead, 2020, Technical)
   - [ ] All in `_portfolio/` directory
   - [ ] All have complete front matter
   - [ ] All use 6-part placeholder structure

3. **Product Projects (3):**
   - [ ] Product Pivot (Head of Product, 2022, Product)
   - [ ] UX Transformation (VP Product, 2021, Product)
   - [ ] Marketplace Growth (Head Product/Growth, 2020, Product)
   - [ ] All in `_portfolio/` directory
   - [ ] All have complete front matter
   - [ ] All use 6-part placeholder structure

4. **Timeline Display:**
   - [ ] 7 projects visible on `/portfolio/` page
   - [ ] Grouped by year: 2023 (1), 2022 (2), 2021 (2), 2020 (2)
   - [ ] Alternating left/right layout (desktop)
   - [ ] Stacked layout (mobile)
   - [ ] Badges show correct colors
   - [ ] Timeline demonstrates range and versatility

5. **Content Quality:**
   - [ ] Placeholder content clearly marked [Placeholder: ...]
   - [ ] Each section shows expected word count guidance
   - [ ] 6-part structure consistent across all projects
   - [ ] No company names or confidential info
   - [ ] Generic contexts show variety (startup, scale-up, enterprise)
   - [ ] Roles show career progression

6. **Narrative Arc:**
   - [ ] Projects demonstrate versatility across contexts
   - [ ] Mix of company stages (seed → Series C)
   - [ ] Mix of challenge types (scale, security, debt, pivot, UX, growth)
   - [ ] Product and technical both represented
   - [ ] Progression visible (IC → manager → executive)

</verification>

<success_criteria>

- [ ] Portfolio layout template created and functional
- [ ] 7 placeholder case studies created (4 technical, 3 product)
- [ ] All projects have complete, consistent front matter
- [ ] Timeline shows career progression from 2020-2023
- [ ] Projects demonstrate versatility across diverse contexts
- [ ] 6-part case study structure template established
- [ ] Placeholder content clearly marked for future replacement
- [ ] No confidential information or company names
- [ ] All individual case study pages render correctly
- [ ] Breadcrumb navigation works on all pages
- [ ] Portfolio demonstrates both product AND technical depth

**Visual success:** Portfolio timeline shows 7 projects spanning 2020-2023, alternating product and technical focus, demonstrating range across startup/scaleup contexts. Clicking any project shows well-structured case study page with placeholders ready for real content.

**Content success:** Project selection tells story of versatile leader who operates across contexts—technical scaling, security, data infrastructure, debt management, product pivots, UX transformation, marketplace growth. Mix of IC to executive roles showing progression.

</success_criteria>

<output>
**Files created/modified:**
1. `_layouts/portfolio.html` - Case study page layout template
2. `_sass/_components.scss` - Case study styles (appended)
3. `_portfolio/01-platform-scaling.md` - Technical project (CTO, 2023)
4. `_portfolio/02-security-architecture.md` - Technical project (Head Eng, 2022)
5. `_portfolio/03-data-infrastructure.md` - Technical project (Eng Manager, 2021)
6. `_portfolio/04-technical-debt-turnaround.md` - Technical project (Senior Lead, 2020)
7. `_portfolio/05-product-market-fit-pivot.md` - Product project (Head Product, 2022)
8. `_portfolio/06-ux-transformation.md` - Product project (VP Product, 2021)
9. `_portfolio/07-marketplace-growth-strategy.md` - Product project (Head Product, 2020)

**Atomic commits:**
1. `feat(phase4-case-studies): create portfolio layout template`
2. `feat(phase4-case-studies): add technical project placeholders (4 projects)`
3. `feat(phase4-case-studies): add product project placeholders (3 projects)`
4. `docs(phase4-case-studies): verify project diversity and narrative arc`

**Next:** phase4-navigation-PLAN.md (add Portfolio to nav, SEO, final polish)
</output>
