# Aukjan van Belkum - Professional Portfolio

[![Deploy Jekyll site to Pages](https://github.com/aukjan/aukjan.github.io/workflows/Deploy%20Jekyll%20site%20to%20Pages/badge.svg)](https://github.com/aukjan/aukjan.github.io/actions)

Personal branding site for CPO/CTO/CPTO leadership portfolio. Built with Jekyll and hosted on GitHub Pages.

## About

This site showcases executive leadership experience, thought leadership, and strategic achievements in global cybersecurity and technology innovation.

## Development

### Option 1: Docker (Recommended)

**Prerequisites:** Docker and Docker Compose

Docker provides the exact Ruby 3.1 environment used by GitHub Actions, ensuring consistency.

1. **Build and start the container:**
   ```bash
   docker-compose up
   ```

2. **Site will be available at:**
   - Main site: `http://localhost:4000`
   - LiveReload: Automatic browser refresh on file changes

3. **Rebuild after Gemfile changes:**
   ```bash
   docker-compose up --build
   ```

4. **Stop the container:**
   ```bash
   docker-compose down
   ```

5. **One-off commands:**
   ```bash
   # Build site only (no server)
   docker-compose run --rm jekyll bundle exec jekyll build

   # Run without LiveReload
   docker-compose run --rm -p 4000:4000 jekyll bundle exec jekyll serve --host 0.0.0.0
   ```

### Option 2: Native Ruby

**Prerequisites:** Ruby 3.0+ and Bundler

⚠️ **Note:** Local Ruby 2.6 cannot install required gems. Use Docker or upgrade to Ruby 3.1+.

1. Install dependencies:
   ```bash
   bundle install
   ```

2. Run Jekyll locally:
   ```bash
   bundle exec jekyll serve --livereload
   ```

   Site will be available at `http://localhost:4000`

### Project Structure

```
├── _config.yml           # Jekyll configuration
├── _layouts/             # Page templates
├── _includes/            # Reusable components
├── _posts/               # Blog posts (Markdown)
├── public/               # Static assets (CSS, images)
├── .planning/            # Project planning docs (GSD workflow)
└── Gemfile               # Ruby dependencies
```

## Deployment

Automated deployment via GitHub Actions to GitHub Pages:
- Push to `master` branch triggers automated build and deployment
- Manual deployment available via Actions tab
- Custom domain: aukjan.vanbelkum.nl
- HTTPS enabled
- Build status visible in badge above

**Setup required:** See [DEPLOYMENT.md](DEPLOYMENT.md) for initial GitHub Pages configuration instructions.

**Monitor builds:** [View Actions](https://github.com/aukjan/aukjan.github.io/actions)

## Project Status

🚧 **In Development** - Phase 1: Foundation & Cleanup

Currently transforming from legacy blog to modern executive portfolio.

## License

Content © 2026 Aukjan van Belkum. All rights reserved.

Theme originally based on Lanyon (MIT License).
