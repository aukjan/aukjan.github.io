# Phase 1 Plan 1: Content Cleanup & Security Fixes

## Objective

Remove outdated 2016 blog content and fix critical security vulnerabilities (HTTP→HTTPS, target="_blank" issues). Clean slate for site transformation.

## Execution Context

**Related Files:**
- @_posts/*.md (all 2016 blog posts to remove)
- @_config.yml (HTTP references, deprecated gems config)
- @_includes/head.html (HTTP font loading)
- @_layouts/post.html (target="_blank" without security)
- @index.html (target="_blank" without security)
- @atom.xml (HTTP references)
- @about.md (uncommitted changes)
- @archive.md (blog archive page)

**Codebase Context:**
- @.planning/codebase/CONCERNS.md (issues #1-4, #16-17)
- @.planning/codebase/STRUCTURE.md (file organization)

## Context

**Current State:**
- 4 blog posts from 2016 with outdated technical content
- HTTP references in _config.yml, _includes/head.html, atom.xml
- target="_blank" links missing rel="noopener noreferrer" security attributes
- Deprecated `gems:` config in _config.yml (should be `plugins:`)
- Uncommitted changes in _config.yml, about.md, index.html
- Untracked files: preview.py, styles.css

**Decision:** Remove ALL 2016 blog content - starting fresh with CPO/CTO/CPTO positioning. Keep Jekyll blog infrastructure for future thought leadership articles.

## Tasks

### Task 1: Remove Outdated Blog Content

**What:** Delete all 2016 blog posts and clean up blog-related pages

**How:**
1. Delete all files in _posts/ directory (4 posts from 2016)
2. Keep _posts/ directory structure for future content
3. Remove or update archive.md (blog archive page)
4. Remove blog post images from public/img/ (outlook_rebuild.png, ping_to_google.png)

**Verification:**
- [ ] _posts/ directory is empty
- [ ] No references to old blog posts remain
- [ ] archive.md removed or updated to placeholder

### Task 2: Fix HTTP→HTTPS Security Issues

**What:** Replace all HTTP references with HTTPS

**How:**
1. Update _config.yml:
   - Line 11: Change `url: http://aukjan.github.io` → `https://aukjan.github.io`
   - Line 17: Update any HTTP references in author/github URLs
2. Update _includes/head.html:
   - Line 20: Change `http://fonts.googleapis.com` → `https://fonts.googleapis.com`
   - Line 2: Update any other HTTP references
3. Update atom.xml:
   - Replace all HTTP references with HTTPS
4. Search entire codebase for remaining `http://` (excluding localhost/127.0.0.1)

**Verification:**
- [ ] No HTTP URLs remain (grep for 'http://' excluding localhost)
- [ ] Site loads without mixed content warnings
- [ ] All external resources load over HTTPS

### Task 3: Fix target="_blank" Security Vulnerabilities

**What:** Add rel="noopener noreferrer" to all external links with target="_blank"

**How:**
1. Update _layouts/post.html:
   - Line 11: Add `rel="noopener noreferrer"` to Twitter share link
   - Line 13: Add `rel="noopener noreferrer"` to Twitter profile link
2. Update index.html:
   - Line 145: Add `rel="noopener noreferrer"` to LinkedIn link
3. Search for any other `target="_blank"` instances

**Verification:**
- [ ] All external links with target="_blank" have security attributes
- [ ] No tabnabbing vulnerabilities remain

### Task 4: Update Deprecated Jekyll Configuration

**What:** Replace deprecated `gems:` with `plugins:` in _config.yml

**How:**
1. Open _config.yml
2. Find line 27 with `gems:` array
3. Replace `gems:` with `plugins:`
4. Verify syntax is correct

**Verification:**
- [ ] _config.yml uses `plugins:` instead of `gems:`
- [ ] Jekyll can parse configuration (test with local build if available)

### Task 5: Clean Up Uncommitted Changes

**What:** Review and commit or discard uncommitted changes

**How:**
1. Review changes in _config.yml (already fixed in previous tasks)
2. Review changes in about.md - decide to keep or discard
3. Review changes in index.html (already fixed in previous tasks)
4. Decide on untracked files:
   - preview.py: Add to git (development utility)
   - styles.css: Review if needed, add or remove
5. Commit all intentional changes

**Verification:**
- [ ] Git working directory is clean (no uncommitted changes to tracked files)
- [ ] All untracked files either committed or intentionally excluded

## Verification

**Automated Checks:**
```bash
# No HTTP references (excluding localhost)
! grep -r "http://" --include="*.html" --include="*.yml" --include="*.md" --include="*.xml" . | grep -v localhost | grep -v "127.0.0.1"

# All target="_blank" have security attributes
! grep -r 'target="_blank"' --include="*.html" . | grep -v 'rel="noopener noreferrer"'

# No gems: in config
! grep "^gems:" _config.yml

# Clean working directory
git status --porcelain | wc -l | grep "^0$"
```

**Manual Checks:**
- [ ] Browse site locally and verify no browser warnings
- [ ] All external links work correctly
- [ ] Site still builds with Jekyll

## Success Criteria

- [ ] All 2016 blog posts removed from _posts/
- [ ] All HTTP URLs changed to HTTPS
- [ ] All target="_blank" links have rel="noopener noreferrer"
- [ ] Jekyll config uses `plugins:` instead of `gems:`
- [ ] Git working directory is clean
- [ ] No security warnings in browser console
- [ ] Site builds successfully with Jekyll

## Output

**Modified Files:**
- _config.yml (HTTPS URLs, plugins config, clean commits)
- _includes/head.html (HTTPS fonts)
- _layouts/post.html (secure external links)
- index.html (secure external links)
- atom.xml (HTTPS URLs)
- about.md (clean commits)
- archive.md (updated or removed)

**Deleted Files:**
- _posts/2016-02-21-Outlook-wont-start.md
- _posts/2016-02-23-Ansible-inventory-from-Terraform.md
- _posts/2016-10-21-OS-X-El-Capitan-WIFI-Inconsitent.md
- _posts/2016-12-21-OS-X-El-Capitain-WIFI-Woes.md
- public/img/outlook_rebuild.png
- public/img/ping_to_google.png

**Git Commits:**
- Security fixes (HTTP→HTTPS, target="_blank")
- Remove outdated blog content
- Update Jekyll configuration

---

**Estimated Time:** 30-45 minutes
**Dependencies:** None (first plan in phase)
**Next Plan:** phase1-architecture-PLAN.md (resolve dual architecture, add Gemfile)
