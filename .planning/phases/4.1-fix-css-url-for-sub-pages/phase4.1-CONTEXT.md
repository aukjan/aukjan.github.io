# Phase 4.1 Context: Fix CSS URL for Sub Pages

**Created:** 2026-01-12
**Type:** Urgent insertion (bug fix)
**Depends on:** Phase 4 - Portfolio & Case Studies

---

## The Vision

Fix CSS loading issue discovered after Phase 4 completion where sub pages (like portfolio case studies) don't load CSS correctly. This is an urgent fix to ensure the site displays properly across all page hierarchies.

**Live site for validation:** https://aukjan.vanbelkum.nl/

---

## How It Works

**The Problem:**
CSS paths aren't working correctly for pages in subdirectories. Root pages load CSS fine, but nested pages (like `/portfolio/01-platform-scaling/`) likely fail to load stylesheets because they're trying relative paths instead of root-relative or absolute paths.

**The Fix:**
1. **Update `_includes/head.html`** to use proper Jekyll URL helpers
   - Use `{{ '/assets/css/main.css' | relative_url }}` or similar
   - Ensure paths work from any directory depth

2. **Check other asset types too** (not just CSS)
   - Images referenced in layouts/includes
   - JavaScript files (if any)
   - Font files
   - Any other assets that might have the same path issue

3. **Basic smoke test verification**
   - Test 3-5 representative pages to ensure CSS loads:
     - Root page (`/`)
     - Portfolio timeline (`/portfolio/`)
     - Case study example (`/portfolio/01-platform-scaling/`)
     - About page (`/about`)
     - One more nested page if applicable
   - Verify on local build AND live site

---

## What's Essential

**Core outcome:** CSS and all assets load correctly on every page, regardless of directory depth.

**Must have:**
- ✅ CSS loads on all pages (root and nested)
- ✅ Other assets (images, JS, fonts) checked and fixed if needed
- ✅ Basic smoke test verifying fix works on representative pages
- ✅ Verified on live site: https://aukjan.vanbelkum.nl/

**Nice to have (but not required for this phase):**
- Documentation of Jekyll URL helper pattern
- Explanation in README about asset paths

---

## What's Out of Scope

**Explicitly NOT this phase:**
- ❌ CSS optimization or minification (that's Phase 6: Polish & Launch)
- ❌ Alternative CSS architectures (Tailwind, CSS-in-JS, etc.)
- ❌ Comprehensive automated build checks (overkill for urgent fix)
- ❌ Visual regression testing (too complex for quick fix)
- ❌ Fixing unrelated CSS bugs or styling issues (only fix loading/paths)

**Keep it focused:** This is a surgical fix to ensure assets load correctly, not a broader refactoring.

---

## The Fix Pattern

**Likely solution (to be confirmed during planning):**

```liquid
<!-- Before (broken on sub pages): -->
<link rel="stylesheet" href="/assets/css/main.css">

<!-- After (works everywhere): -->
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">
```

Or with baseurl support:
```liquid
<link rel="stylesheet" href="{{ site.baseurl }}/assets/css/main.css">
```

**Where to fix:**
- `_includes/head.html` - CSS links
- Any layout files with direct asset references
- Check if images in `_includes/header.html` or `_includes/footer.html` need fixing

---

## Validation Strategy

**Testing approach:**
1. Fix the CSS URL in `_includes/head.html`
2. Check other asset references in includes and layouts
3. Build locally with Docker
4. Test 3-5 representative pages:
   - `/` (root)
   - `/portfolio/` (one level deep)
   - `/portfolio/01-platform-scaling/` (two levels deep)
   - `/about` (root)
   - `/archive` (root)
5. Push to GitHub and verify on live site: https://aukjan.vanbelkum.nl/
6. Check both desktop and mobile views

**Success criteria:**
- All pages display with proper styling
- No browser console errors about missing CSS
- Images and other assets load correctly
- Live site renders identically to local build

---

## Why This Matters

**User impact:** Portfolio case studies (Phase 4's main deliverable) are likely unstyled or broken on the live site. This is a critical user experience issue that needs immediate fixing.

**Urgency:** The site is live and potentially showing broken pages to visitors. This blocks any promotion or sharing of the portfolio work.

**Scope control:** Keep this focused on the asset loading issue. Don't get sidetracked by styling improvements, optimization, or other enhancements. Fix the loading, verify it works, ship it.

---

## Next Steps After Context

1. **Plan the phase:** `/gsd:plan-phase 4.1`
   - Should be 1 simple plan with 3-5 tasks
   - Estimated execution: 10-15 minutes

2. **Execute immediately:** This is urgent, plan and execute in same session if possible

3. **After fix:** Continue to Phase 5 (Thought Leadership Platform)

---

**Vision captured:** Fix CSS/asset loading on nested pages, verify with smoke test, get live site working properly.
