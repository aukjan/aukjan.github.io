# Phase 1 Plan 3: GitHub Actions CI/CD Setup

## Objective

Create modern GitHub Actions workflow for automated Jekyll builds and GitHub Pages deployments. Replace legacy auto-build with explicit CI/CD pipeline.

## Execution Context

**Related Files:**
- @.github/workflows/ (to create)
- @_config.yml (Jekyll config)
- @Gemfile (dependencies from previous plan)

**Reference Materials:**
- GitHub Actions documentation for Jekyll
- GitHub Pages deployment best practices
- Jekyll build optimization

**Codebase Context:**
- @.planning/codebase/STACK.md (deployment info)

## Context

**Current State:**
- Relying on GitHub Pages automatic Jekyll builds
- No explicit CI/CD pipeline
- No control over build process
- Cannot add custom build steps
- Limited visibility into build status

**Goal:** Modern CI/CD with GitHub Actions for:
- Explicit build control
- Ability to add custom steps (linting, testing, etc.)
- Better build visibility and debugging
- Foundation for future automation (tests, performance checks)

**Constraint:** Must stay within GitHub ecosystem (GitHub Actions + GitHub Pages)

## Tasks

### Task 1: Research GitHub Actions Jekyll Patterns

**What:** Quick research on modern Jekyll + GitHub Pages deployment

**How:**
1. Check GitHub's official Jekyll deployment action documentation
2. Review jekyll/jekyll-action or similar official actions
3. Identify best practices:
   - Recommended Ruby version
   - Caching strategies for bundle/gems
   - Build artifact handling
   - Deployment to gh-pages branch or GitHub Pages

**Verification:**
- [ ] Understand GitHub Pages deployment options
- [ ] Know recommended Ruby version for Jekyll
- [ ] Identified any gotchas or common issues

### Task 2: Create GitHub Actions Workflow

**What:** Create .github/workflows/jekyll.yml for automated builds

**How:**
1. Create directory structure: `.github/workflows/`
2. Create `jekyll.yml` with workflow:
   - Trigger on push to main/master branch
   - Trigger on pull requests
   - Use appropriate Ruby version (3.1 or later)
   - Install dependencies with bundle
   - Build Jekyll site
   - Deploy to GitHub Pages (if on master branch)
   - Add caching for gems to speed up builds
3. Example structure:
   ```yaml
   name: Build and Deploy Jekyll Site

   on:
     push:
       branches: [ master ]
     pull_request:
       branches: [ master ]

   permissions:
     contents: read
     pages: write
     id-token: write

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
         - uses: ruby/setup-ruby@v1
           with:
             ruby-version: '3.1'
             bundler-cache: true
         - name: Build Jekyll
           run: bundle exec jekyll build
         - name: Upload artifact
           uses: actions/upload-pages-artifact@v3

     deploy:
       needs: build
       if: github.ref == 'refs/heads/master'
       runs-on: ubuntu-latest
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       steps:
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v4
   ```

**Verification:**
- [ ] Workflow file created with correct syntax
- [ ] Triggers configured for push and PR
- [ ] Ruby and bundle setup correct
- [ ] Build and deploy steps defined

### Task 3: Configure GitHub Pages Settings

**What:** Update repository settings for Actions deployment

**How:**
1. Document required GitHub repository settings:
   - Settings → Pages → Source: "GitHub Actions"
   - Permissions for workflows
2. Note: User must manually update these in GitHub UI
3. Create checklist or instructions file

**Verification:**
- [ ] Documentation created for GitHub settings
- [ ] Clear instructions for enabling Actions deployment

### Task 4: Test Workflow Locally (Optional)

**What:** Validate workflow syntax and Jekyll build

**How:**
1. Use `act` tool or GitHub CLI to test locally (if available)
2. Or simply validate YAML syntax
3. Test Jekyll build manually: `bundle exec jekyll build`
4. Verify _site/ directory generates correctly

**Verification:**
- [ ] Workflow YAML is valid
- [ ] Jekyll build succeeds locally
- [ ] Build artifacts look correct

### Task 5: Add Build Status Badge (Optional)

**What:** Add build status badge to README.md

**How:**
1. Add GitHub Actions badge to README.md:
   ```markdown
   [![Build Status](https://github.com/aukjan/aukjan.github.io/workflows/Build%20and%20Deploy%20Jekyll%20Site/badge.svg)](https://github.com/aukjan/aukjan.github.io/actions)
   ```
2. Update README with deployment information
3. Document CI/CD process

**Verification:**
- [ ] Badge added to README
- [ ] Badge links to Actions page
- [ ] Documentation updated

### Task 6: Create Deployment Instructions

**What:** Document deployment process and troubleshooting

**How:**
1. Create or update docs with:
   - How CI/CD works
   - Required GitHub settings
   - How to trigger manual deployments
   - Troubleshooting common issues
   - How to view build logs
2. Add to README.md or separate DEPLOYMENT.md

**Verification:**
- [ ] Deployment process documented
- [ ] Troubleshooting guide available
- [ ] Clear instructions for setup

### Task 7: Commit and Push Workflow

**What:** Commit workflow and trigger first build

**How:**
1. Review all changes
2. Commit .github/workflows/jekyll.yml
3. Update documentation
4. Push to trigger first workflow run
5. Monitor Actions tab for build success
6. Verify site deploys correctly

**Verification:**
- [ ] Workflow committed and pushed
- [ ] First build runs successfully
- [ ] Site deploys to GitHub Pages
- [ ] No build errors or warnings

## Verification

**Automated Checks:**
```bash
# Workflow file exists
test -f .github/workflows/jekyll.yml && echo "✓ Workflow file exists"

# Valid YAML syntax (if yamllint available)
command -v yamllint >/dev/null && yamllint .github/workflows/jekyll.yml

# Jekyll builds successfully
bundle exec jekyll build && echo "✓ Jekyll builds"

# GitHub Pages configuration reminder
echo "⚠ Remember to set GitHub Pages source to 'GitHub Actions' in repository settings"
```

**Manual Checks:**
- [ ] GitHub Actions workflow runs on push
- [ ] Build completes successfully
- [ ] Site deploys to GitHub Pages
- [ ] Custom domain (aukjan.vanbelkum.nl) still works
- [ ] HTTPS certificate valid
- [ ] No broken links or missing assets

## Success Criteria

- [ ] GitHub Actions workflow created and committed
- [ ] Workflow builds Jekyll successfully
- [ ] Workflow deploys to GitHub Pages
- [ ] Build runs automatically on push to master
- [ ] Build status visible in Actions tab
- [ ] Documentation updated with CI/CD info
- [ ] Site accessible and functioning correctly
- [ ] Custom domain configuration preserved

## Output

**Created Files:**
- .github/workflows/jekyll.yml (CI/CD workflow)
- DEPLOYMENT.md or updated README.md (deployment docs)

**Modified Files:**
- README.md (build badge, instructions)

**GitHub Configuration:**
- Repository settings → Pages → Source: GitHub Actions
- Workflow permissions configured

**Git Commits:**
- Add GitHub Actions workflow for Jekyll
- Document deployment process

---

**Estimated Time:** 45-60 minutes
**Dependencies:** phase1-architecture-PLAN.md (Gemfile must exist)
**Next Phase:** Phase 2 - Design System & Architecture

**Notes:**
- First workflow run will require GitHub Pages settings update in repo
- Monitor Actions tab for build success
- Custom domain (CNAME file) should be preserved automatically
- May need to configure workflow permissions in repo settings
