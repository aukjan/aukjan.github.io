<objective>
Fix CSS and asset loading issue on sub pages by using Jekyll's relative_url filter instead of direct baseurl concatenation.

**Root cause identified:** `{{ site.baseurl }}assets/css/main.css` generates relative paths on nested pages, causing 404 errors. Need to use `{{ '/assets/css/main.css' | relative_url }}` for proper absolute path generation.

**Live site validation:** https://aukjan.vanbelkum.nl/
</objective>

<execution_context>
@phase4.1-CONTEXT.md - Full vision and validation strategy
@_includes/head.html - Contains all asset references that need fixing
@_config.yml - Baseurl configuration (currently '/')
</execution_context>

<context>
**Issue discovered:** After Phase 4 completion, portfolio case study pages and other sub pages are completely unstyled.

**Browser console error:**
```
GET https://aukjan.vanbelkum.nl/about/public/css/syntax.css
net::ERR_ABORTED 404 (Not Found)
```

**Current broken code** (_includes/head.html lines 62-67):
```html
<link rel="stylesheet" href="{{ site.baseurl }}assets/css/main.css">
<link rel="stylesheet" href="{{ site.baseurl }}public/css/syntax.css">
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="{{ site.baseurl }}public/apple-touch-icon-144-precomposed.png">
<link rel="shortcut icon" href="{{ site.baseurl }}public/favicon.ico">
```

**Why it fails:**
- With `baseurl: '/'` in _config.yml, Jekyll treats `/` as empty
- This generates relative paths: `href="public/css/syntax.css"` (no leading `/`)
- On root page (`/`): loads `/public/css/syntax.css` ✅ Works
- On `/about/`: tries to load `/about/public/css/syntax.css` ❌ 404!
- On `/portfolio/01-platform-scaling/`: tries to load `/portfolio/01-platform-scaling/public/css/syntax.css` ❌ 404!

**The fix:**
Use Jekyll's `relative_url` filter which properly handles baseurl and always generates correct absolute paths:
```html
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">
```

**Scope:**
- Fix all 4 asset references in _includes/head.html
- Verify no other asset references exist in layouts/includes
- Test on 5 representative pages (root + nested)
- Deploy and verify on live site
</context>

<tasks>

## Task 1: Fix CSS Links in _includes/head.html

**File:** `_includes/head.html` (lines 62-63)

Update both CSS links to use `relative_url` filter:

**Before:**
```html
<!-- CSS -->
<link rel="stylesheet" href="{{ site.baseurl }}assets/css/main.css">
<link rel="stylesheet" href="{{ site.baseurl }}public/css/syntax.css">
```

**After:**
```html
<!-- CSS -->
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">
<link rel="stylesheet" href="{{ '/public/css/syntax.css' | relative_url }}">
```

**Why this works:**
- `relative_url` filter properly handles baseurl configuration
- Always generates absolute paths from site root
- Works correctly regardless of page directory depth

**Verification:**
- [ ] Both CSS links updated with `| relative_url` filter
- [ ] Leading `/` present in the path string (critical!)
- [ ] Syntax is correct (no typos in filter name)

## Task 2: Fix Icon Links in _includes/head.html

**File:** `_includes/head.html` (lines 66-67)

Update icon/favicon links to use `relative_url` filter:

**Before:**
```html
<!-- Icons -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="{{ site.baseurl }}public/apple-touch-icon-144-precomposed.png">
<link rel="shortcut icon" href="{{ site.baseurl }}public/favicon.ico">
```

**After:**
```html
<!-- Icons -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="{{ '/public/apple-touch-icon-144-precomposed.png' | relative_url }}">
<link rel="shortcut icon" href="{{ '/public/favicon.ico' | relative_url }}">
```

**Why this matters:**
- Same issue affects icons/favicons
- Ensures all assets load correctly from any page depth

**Verification:**
- [ ] Apple touch icon link updated
- [ ] Favicon link updated
- [ ] Both use `| relative_url` filter with leading `/`

## Task 3: Audit Other Asset References

**Check for other asset references** that might have the same issue:

**Files to check:**
- `_includes/header.html` - Logo or images?
- `_includes/footer.html` - Images or icons?
- `_layouts/default.html` - Any asset references?
- `_layouts/page.html` - Any asset references?
- `_layouts/post.html` - Any asset references?
- `_layouts/portfolio.html` - Any asset references?

**What to look for:**
```bash
# Search for asset references
grep -r "src=\"" _includes/ _layouts/
grep -r "href=\"" _includes/ _layouts/ | grep -E "\.(css|js|png|jpg|svg|ico|woff)"
```

**If found:**
- Apply same fix pattern: use `{{ '/path/to/asset' | relative_url }}`
- Document what was fixed

**If not found:**
- Document that no other asset references need fixing
- All assets are properly referenced

**Verification:**
- [ ] All includes checked for asset references
- [ ] All layouts checked for asset references
- [ ] Any found references updated with `| relative_url` filter
- [ ] Or confirmed: no other asset references exist

## Task 4: Local Build and Test 5 Representative Pages

**Build locally:**
```bash
docker-compose down
docker-compose up --build
```

Or if Docker unavailable:
```bash
bundle exec jekyll clean
bundle exec jekyll build
bundle exec jekyll serve
```

**Test these 5 pages** (covering different directory depths):

1. **Root page:** http://localhost:4000/
   - [ ] Page loads with full styling
   - [ ] No browser console errors about missing CSS
   - [ ] Header, footer, and content styled correctly

2. **About page:** http://localhost:4000/about
   - [ ] Page loads with full styling
   - [ ] No 404 errors for CSS/assets
   - [ ] Typography and colors render correctly

3. **Portfolio timeline:** http://localhost:4000/portfolio/
   - [ ] Timeline component styled correctly
   - [ ] Cards, badges, and layout render properly
   - [ ] No missing CSS errors

4. **Case study (nested):** http://localhost:4000/portfolio/01-platform-scaling/
   - [ ] Case study page fully styled
   - [ ] Breadcrumb, header, content sections all styled
   - [ ] This was completely unstyled before - should be fixed now

5. **Archive page:** http://localhost:4000/archive
   - [ ] Article cards styled correctly
   - [ ] Page loads without CSS errors

**Browser console check:**
- [ ] Open dev tools (F12) on each page
- [ ] Check Network tab → CSS filter
- [ ] Verify all CSS files load with 200 status
- [ ] Verify paths are absolute (start with `/`)

**Visual verification:**
- [ ] All pages look identical to how root page looked before
- [ ] No unstyled content (plain HTML)
- [ ] Colors, fonts, spacing all correct
- [ ] Mobile responsive check (resize browser)

## Task 5: Push and Verify on Live Site

**Commit the fix:**
```bash
git add _includes/head.html
git commit -m "fix(phase4.1): use relative_url filter for asset paths

Fixes CSS loading issue on sub pages where relative paths were
being generated instead of absolute paths. Portfolio case studies
and other nested pages were completely unstyled.

Browser was trying to load:
- /about/public/css/syntax.css (404)

Now correctly loads:
- /public/css/syntax.css (200)

Uses Jekyll's relative_url filter for:
- CSS files (main.css, syntax.css)
- Icons (apple-touch-icon, favicon)

Verified on:
- Root page (/)
- About (/about)
- Portfolio (/portfolio/)
- Case study (/portfolio/01-platform-scaling/)
- Archive (/archive)

All pages now load CSS correctly."
```

**Push to GitHub:**
```bash
git push origin master
```

**Wait for GitHub Actions:**
- Go to https://github.com/aukjan/aukjan.github.io/actions
- Watch the Jekyll build workflow
- Wait for deployment to complete (~2-3 minutes)

**Verify on live site:** https://aukjan.vanbelkum.nl/

Test the same 5 pages:
1. [ ] https://aukjan.vanbelkum.nl/ - Root page styled
2. [ ] https://aukjan.vanbelkum.nl/about - About page styled
3. [ ] https://aukjan.vanbelkum.nl/portfolio/ - Portfolio styled
4. [ ] https://aukjan.vanbelkum.nl/portfolio/01-platform-scaling/ - Case study styled (was broken!)
5. [ ] https://aukjan.vanbelkum.nl/archive - Archive styled

**Live verification checklist:**
- [ ] All 5 pages load with full styling
- [ ] Browser console shows no 404 errors for CSS
- [ ] Network tab shows CSS loading from correct paths
- [ ] Visual appearance matches local build
- [ ] Mobile view works correctly (test on phone or resize browser)

**Final check:**
- [ ] Open browser dev tools on case study page
- [ ] Network tab → filter by CSS
- [ ] Verify URL is https://aukjan.vanbelkum.nl/public/css/syntax.css (NOT /portfolio/.../public/css/syntax.css)
- [ ] Status code: 200 OK

</tasks>

<verification>

After completing all tasks:

**Asset References:**
- [ ] All 4 asset links in _includes/head.html use `| relative_url` filter
- [ ] All asset paths have leading `/` in the string
- [ ] No other asset references found needing fixing

**Local Testing:**
- [ ] 5 representative pages tested locally
- [ ] All pages load CSS correctly
- [ ] No browser console errors
- [ ] Visual appearance consistent across all pages

**Live Deployment:**
- [ ] Changes committed with descriptive message
- [ ] Pushed to GitHub successfully
- [ ] GitHub Actions build completed successfully
- [ ] 5 pages verified on live site
- [ ] All pages styled correctly on https://aukjan.vanbelkum.nl/
- [ ] Browser console clean (no CSS 404 errors)

**Critical Success Indicator:**
- [ ] Portfolio case study page (https://aukjan.vanbelkum.nl/portfolio/01-platform-scaling/) is now fully styled (was completely broken before)

</verification>

<success_criteria>

**Primary goal achieved:**
- ✅ CSS loads correctly on all pages (root and nested)
- ✅ No more 404 errors for `/about/public/css/syntax.css` or similar
- ✅ Portfolio case studies display with proper styling

**Technical criteria:**
- All asset references use `{{ '/path' | relative_url }}` pattern
- Asset paths generate as absolute URLs from site root
- Works correctly regardless of page directory depth
- Compatible with current baseurl configuration

**Validation criteria:**
- 5 representative pages tested (different directory depths)
- Local build verified
- Live site verified (https://aukjan.vanbelkum.nl/)
- No browser console errors
- Visual appearance consistent

**User impact:**
- Site now usable and shareable
- Portfolio work (Phase 4 deliverable) now properly visible
- Professional appearance maintained across all pages
- Ready to continue to Phase 5

**What success looks like:**
User can visit any page on the live site and see consistent, professional styling. Portfolio case studies that were completely unstyled are now fully rendered with the timeline component, typography, colors, and layout working correctly.

</success_criteria>

<output>
**Files modified:**
1. `_includes/head.html` - Fixed 4 asset references (2 CSS, 2 icons)

**Atomic commit:**
```
fix(phase4.1): use relative_url filter for asset paths
```

**Verification:**
- 5 pages tested locally
- 5 pages verified on live site
- No CSS 404 errors
- All styling intact

**Phase 4.1 Status:** ✅ COMPLETE

**Next:** Continue to Phase 5 - Thought Leadership Platform
</output>
