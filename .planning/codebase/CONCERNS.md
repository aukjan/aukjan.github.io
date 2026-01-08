# Technical Concerns

## Critical Issues

### 1. Mixed HTTP/HTTPS Content (CRITICAL)
**Locations:**
- _config.yml:11,17 - `url: http://aukjan.github.io`
- _includes/head.html:2,20 - `http://fonts.googleapis.com`
- atom.xml - Multiple HTTP references

**Risk:** Mixed content warnings, MITM attacks, SEO penalties, security warnings

**Fix:** Change all HTTP → HTTPS

### 2. Broken Code Example (CRITICAL)
**Location:** _posts/2016-02-23-Ansible-inventory-from-Terraform.md:58

**Issue:** References `ansible_hosts` instead of `ansible_inventory`

**Impact:** Blog post code doesn't work, damages credibility

### 3. Target="_blank" Without Security (HIGH)
**Locations:**
- _layouts/post.html:11,13
- index.html:145

**Risk:** Tabnabbing vulnerability, performance issues, privacy leak

**Fix:** Add `rel="noopener noreferrer"` to all external links

### 4. Deprecated Jekyll Config (HIGH)
**Location:** _config.yml:27

**Issue:** Using `gems:` instead of `plugins:`

**Risk:** Will break in future Jekyll versions

## Configuration Issues

### 5. Missing Dependency Management (HIGH)
**Issue:** No Gemfile or Gemfile.lock

**Impact:**
- Cannot reproduce builds
- Jekyll version not pinned
- Difficult for contributors
- GitHub Pages compatibility unclear

### 6. Dual Architecture Confusion (HIGH)
**Issue:** Two competing site architectures:
- Jekyll blog (Lanyon theme)
- Standalone HTML (modern portfolio)

**Impact:** Maintenance confusion, unclear primary purpose, wasted resources

## SEO & Discoverability

### 7. Missing robots.txt (MEDIUM)
**Impact:** No crawler control, cannot guide to sitemap

### 8. Missing sitemap.xml (MEDIUM)
**Impact:** Harder for search engines to discover content

### 9. Incomplete Atom Feed (MEDIUM)
**Location:** atom.xml:15

**Issue:** References `site.author.email` but not configured

**Impact:** Invalid feed structure

## Content Quality

### 10. Multiple Typos (LOW-MEDIUM)
**Examples:**
- "consitently" → "consistently"
- "alwasy" → "always"
- "follwing" → "following"
- "wrappes" → "wrapped"

**Impact:** Unprofessional for CTO portfolio

### 11. Stale Content (LOW)
**Issue:** All blog posts from 2016 (8 years old)

**Impact:** Site appears abandoned, outdated

## Security Concerns

### 12. No Security Headers (MEDIUM)
**Missing:**
- Content-Security-Policy
- X-Frame-Options
- X-Content-Type-Options

**Risk:** XSS vulnerability, clickjacking, MIME-sniffing

## Accessibility

### 13. Missing Alt Text (MEDIUM)
**Issue:** Images likely lack alt attributes

**Impact:** Fails WCAG guidelines, poor screen reader experience

## Performance

### 14. Unoptimized Font Loading (LOW-MEDIUM)
**Issue:**
- No `display=swap`
- HTTP instead of HTTPS
- No preconnect hints

**Impact:** FOIT (Flash of Invisible Text), slower load

### 15. No Asset Minification (LOW)
**Impact:** Larger files, slower load times

## Repository Hygiene

### 16. Uncommitted Changes (MEDIUM)
**Git Status:**
- M _config.yml
- M about.md
- M index.html

**Impact:** Unclear state, risky for deployment

### 17. Untracked Files (LOW)
- preview.py
- styles.css

**Impact:** Unclear which files are intentional

## Priority Actions

### Immediate
1. Fix all HTTP → HTTPS
2. Add `rel="noopener noreferrer"` to external links
3. Fix broken Terraform code example

### High Priority
4. Decide on single architecture
5. Update `gems:` to `plugins:`
6. Commit or revert modified files

### Medium Priority
7. Add Gemfile with pinned versions
8. Add robots.txt and sitemap.xml
9. Fix content typos
10. Configure author email for feed

### Low Priority
11. Optimize font loading
12. Add alt text to images
13. Consider content refresh
