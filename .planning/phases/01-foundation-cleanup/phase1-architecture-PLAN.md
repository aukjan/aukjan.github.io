# Phase 1 Plan 2: Architecture Resolution & Dependencies

## Objective

Resolve dual architecture confusion, establish single source of truth, and add proper dependency management (Gemfile).

## Execution Context

**Related Files:**
- @index.html (standalone modern portfolio page)
- @styles.css (standalone CSS)
- @_layouts/default.html (Jekyll layout)
- @_config.yml (Jekyll configuration)
- @preview.py (development server)
- @.editorconfig (code style)

**Codebase Context:**
- @.planning/codebase/CONCERNS.md (issue #6 - dual architecture)
- @.planning/codebase/STACK.md (dependencies)
- @.planning/codebase/ARCHITECTURE.md (structure)

## Context

**Current State:**
- Two competing architectures:
  1. Jekyll blog (Lanyon theme) with _layouts, _includes, _posts
  2. Standalone index.html with inline/separate styles.css
- No clear primary architecture
- No Gemfile for dependency management
- preview.py as development server

**Decision:** Keep Jekyll as primary architecture for entire site. Remove standalone index.html architecture (will rebuild homepage in Phase 3 using Jekyll). This maintains consistency and leverages existing Jekyll infrastructure.

## Tasks

### Task 1: Resolve Dual Architecture

**What:** Remove standalone architecture, establish Jekyll as single source of truth

**How:**
1. Backup current index.html content for reference (copy key sections to notes)
2. Replace index.html with Jekyll-based version:
   - Create simple temporary homepage that uses Jekyll layout
   - Use `layout: default` from existing _layouts/
   - Add basic content placeholder
   - Note: Full homepage redesign happens in Phase 3
3. Remove or relocate standalone styles.css:
   - Check if styles.css has unique styles not in public/css/
   - If unique styles exist, note them for Phase 2 (design system)
   - Remove styles.css from root
4. Update any references to standalone architecture

**Verification:**
- [ ] index.html uses Jekyll layout (has YAML front matter)
- [ ] No standalone HTML architecture remains
- [ ] Site still renders correctly

### Task 2: Create Gemfile for Dependency Management

**What:** Add Gemfile to pin Jekyll and plugin versions for reproducible builds

**How:**
1. Create Gemfile with:
   ```ruby
   source "https://rubygems.org"

   # GitHub Pages gem includes Jekyll and approved plugins
   gem "github-pages", "~> 231", group: :jekyll_plugins

   # Or specify Jekyll directly if not using github-pages gem:
   # gem "jekyll", "~> 3.9.3"

   # Plugins (these are included in github-pages gem)
   group :jekyll_plugins do
     gem "jekyll-paginate"
   end
   ```
2. Run `bundle install` to generate Gemfile.lock (if Ruby/Bundler available locally)
3. Add note in README or comments about installation
4. Verify _config.yml plugins list matches Gemfile

**Verification:**
- [ ] Gemfile exists with pinned versions
- [ ] Gemfile.lock generated (if possible)
- [ ] Dependencies match _config.yml plugins

### Task 3: Clean Up Development Utilities

**What:** Organize development tools and documentation

**How:**
1. Keep preview.py as development utility
2. Add preview.py to git if not already tracked
3. Update or create README.md with:
   - How to run locally (Jekyll or preview.py)
   - Dependency installation instructions
   - Build and deployment notes
4. Verify .gitignore covers Jekyll build artifacts (_site/, .jekyll-cache/)

**Verification:**
- [ ] preview.py tracked in git
- [ ] README.md has development instructions
- [ ] .gitignore properly configured

### Task 4: Verify Single Architecture

**What:** Ensure consistent Jekyll architecture throughout

**How:**
1. Check all HTML pages use Jekyll layouts:
   - index.html ✓
   - about.md (already uses Jekyll)
   - 404.html (check if uses layout)
2. Verify all pages inherit from _layouts/default.html
3. Remove any remnants of standalone architecture
4. Test that site builds with Jekyll

**Verification:**
- [ ] All pages use Jekyll layouts
- [ ] No standalone HTML files (except Jekyll-generated)
- [ ] Consistent architecture across site

### Task 5: Document Architecture Decision

**What:** Record decision in project documentation

**How:**
1. Update .planning/PROJECT.md Key Decisions table:
   - Add decision about single Jekyll architecture
   - Mark "Resolve dual architecture issue" as complete
2. Update .planning/STATE.md with progress
3. Commit all changes with clear message

**Verification:**
- [ ] Decision documented in PROJECT.md
- [ ] STATE.md updated
- [ ] Changes committed to git

## Verification

**Automated Checks:**
```bash
# Gemfile exists
test -f Gemfile && echo "✓ Gemfile exists"

# No standalone styles.css in root
! test -f styles.css && echo "✓ No standalone styles.css"

# index.html uses Jekyll (has front matter)
head -1 index.html | grep -q "^---$" && echo "✓ index.html uses Jekyll"

# Jekyll build works
bundle exec jekyll build --verbose 2>&1 | grep -q "done in" && echo "✓ Jekyll builds successfully"
```

**Manual Checks:**
- [ ] Site renders correctly with Jekyll
- [ ] No broken layouts or missing styles
- [ ] Navigation works across pages
- [ ] Local preview server (Jekyll or preview.py) works

## Success Criteria

- [ ] Single Jekyll architecture established (no standalone HTML)
- [ ] Gemfile created with pinned dependencies
- [ ] index.html uses Jekyll layout (temporary version for now)
- [ ] README.md has development instructions
- [ ] All changes documented in PROJECT.md and STATE.md
- [ ] Git history clean with clear commits
- [ ] Site builds successfully with Jekyll

## Output

**Created Files:**
- Gemfile (dependency management)
- Gemfile.lock (if generated)
- README.md (if doesn't exist) or updated

**Modified Files:**
- index.html (converted to Jekyll-based temporary homepage)
- .planning/PROJECT.md (document architecture decision)
- .planning/STATE.md (progress update)

**Removed Files:**
- styles.css (standalone, moved or removed)

**Git Commits:**
- Resolve dual architecture, establish Jekyll as primary
- Add Gemfile for dependency management
- Document architecture decisions

---

**Estimated Time:** 45-60 minutes
**Dependencies:** phase1-cleanup-PLAN.md (should complete first)
**Next Plan:** phase1-cicd-PLAN.md (GitHub Actions workflow)
