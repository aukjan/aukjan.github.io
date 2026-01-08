# Deployment Guide

## GitHub Actions CI/CD Pipeline

This site uses GitHub Actions for automated builds and deployment to GitHub Pages.

## Initial Setup

### 1. Configure GitHub Pages Source

**Required:** You must configure your repository to use GitHub Actions for deployment.

1. Navigate to your repository on GitHub
2. Go to **Settings** → **Pages** (under "Code and automation")
3. Under **Build and deployment**, find the **Source** dropdown
4. Change from "Deploy from a branch" to **"GitHub Actions"**
5. Save the changes

### 2. Verify Workflow Permissions

Ensure the workflow has the necessary permissions:

1. Go to **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Ensure "Read and write permissions" is selected
4. Save if you made any changes

## How It Works

### Automatic Deployments

The workflow (`.github/workflows/jekyll.yml`) automatically triggers on:

- **Push to master branch**: Every commit to master triggers a build and deployment
- **Manual trigger**: You can manually run the workflow from the Actions tab

### Build Process

1. **Checkout**: Code is checked out from the repository
2. **Setup Ruby**: Ruby 3.1 is installed with bundler caching for faster builds
3. **Setup Pages**: GitHub Pages environment is configured
4. **Build Jekyll**: Site is built with `bundle exec jekyll build`
5. **Upload artifact**: Built site is uploaded as an artifact
6. **Deploy**: Site is deployed to GitHub Pages (only on master branch)

### Workflow Features

- ✅ Ruby 3.1 with bundler caching (faster builds after first run)
- ✅ Separate build and deploy jobs
- ✅ Concurrency control (prevents overlapping deployments)
- ✅ Production environment configuration (`JEKYLL_ENV=production`)
- ✅ Proper permissions for GitHub Pages deployment

## Manual Deployment

To manually trigger a deployment:

1. Go to the **Actions** tab in your repository
2. Click on **"Deploy Jekyll site to Pages"** workflow
3. Click **"Run workflow"** button
4. Select the branch (master)
5. Click **"Run workflow"**

## Monitoring Builds

### View Build Status

1. Go to the **Actions** tab in your repository
2. Click on the latest workflow run
3. View the build and deploy logs
4. Check for any errors or warnings

### Build Badge

The README includes a build status badge showing the current build status:

[![Build Status](https://github.com/aukjan/aukjan.github.io/workflows/Deploy%20Jekyll%20site%20to%20Pages/badge.svg)](https://github.com/aukjan/aukjan.github.io/actions)

## Troubleshooting

### Build Fails

**Check the build logs:**
1. Go to Actions tab
2. Click the failed workflow run
3. Expand the failed step to see error details

**Common issues:**
- **Ruby gem errors**: Check Gemfile for version conflicts
- **Jekyll build errors**: Verify _config.yml syntax
- **Missing files**: Ensure all referenced files exist

### Deployment Fails

**Verify GitHub Pages settings:**
- Source must be set to "GitHub Actions"
- Workflow must have write permissions

**Check deployment logs:**
- Expand the "Deploy to GitHub Pages" step
- Look for permission or configuration errors

### Site Not Updating

**After a successful deployment:**
- GitHub Pages can take 1-2 minutes to update
- Clear your browser cache
- Verify the workflow completed both build AND deploy jobs

### Custom Domain Issues

**If using custom domain (aukjan.vanbelkum.nl):**
- CNAME file should be preserved automatically
- Verify DNS settings point to GitHub Pages
- Check HTTPS certificate status in Settings → Pages

## Local Testing

Before pushing, test your changes locally:

```bash
# Install dependencies
bundle install

# Build the site
bundle exec jekyll build

# Serve locally
bundle exec jekyll serve
```

Visit `http://localhost:4000` to preview changes.

## Workflow Configuration

The workflow configuration is located at `.github/workflows/jekyll.yml`.

**Key settings:**
- **Ruby version**: 3.1 (modern, stable)
- **Bundler caching**: Enabled (speeds up builds)
- **Trigger**: Push to master, manual dispatch
- **Permissions**: Contents (read), Pages (write), ID token (write)

## References

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Official Jekyll Actions Workflow](https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml)

---

**Need help?** Check the [GitHub Actions logs](https://github.com/aukjan/aukjan.github.io/actions) or [open an issue](https://github.com/aukjan/aukjan.github.io/issues).
