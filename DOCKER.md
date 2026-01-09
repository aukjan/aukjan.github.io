# Docker Development Guide

This guide explains how to use Docker for local Jekyll development, matching the exact Ruby 3.1 environment used by GitHub Actions.

## Why Docker?

- **Consistency**: Same Ruby 3.1 environment as GitHub Actions
- **No local Ruby setup**: Works regardless of your system's Ruby version
- **Clean environment**: No conflicts with other Ruby projects
- **Fast setup**: One command to get started

## Prerequisites

- Docker Desktop installed ([download here](https://www.docker.com/products/docker-desktop))
- Docker Compose (included with Docker Desktop)

## Quick Start

### 1. Start the Development Server

```bash
docker-compose up
```

This will:
- Build the Docker image (first time only, ~2-3 minutes)
- Install all Ruby dependencies
- Start Jekyll with LiveReload
- Watch for file changes

**Your site will be available at:**
- Main site: http://localhost:4000
- LiveReload: Automatic browser refresh on changes

### 2. Stop the Server

Press `Ctrl+C` in the terminal, or run:

```bash
docker-compose down
```

## Common Tasks

### Build Site (No Server)

```bash
docker-compose run --rm jekyll bundle exec jekyll build
```

Output will be in `_site/` directory.

### Serve Without LiveReload

```bash
docker-compose run --rm -p 4000:4000 jekyll bundle exec jekyll serve --host 0.0.0.0
```

### Rebuild After Gemfile Changes

If you modify `Gemfile`:

```bash
docker-compose up --build
```

This rebuilds the image with updated dependencies.

### Run Shell Inside Container

```bash
docker-compose run --rm jekyll bash
```

Useful for debugging or running commands inside the container.

### Install New Gem

1. Add gem to `Gemfile`
2. Rebuild:
   ```bash
   docker-compose up --build
   ```

## File Structure

```
.
├── Dockerfile           # Container definition (Ruby 3.1)
├── docker-compose.yml   # Service configuration
├── .dockerignore        # Files excluded from Docker build
└── Gemfile             # Ruby dependencies
```

## Troubleshooting

### Port 4000 Already in Use

If port 4000 is busy, change the port in `docker-compose.yml`:

```yaml
ports:
  - "4001:4000"  # Use localhost:4001 instead
```

### Changes Not Reflecting

1. Check that LiveReload is enabled (default with `docker-compose up`)
2. Some files require full rebuild (`_config.yml`, Sass partials)
3. Hard refresh browser: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows/Linux)

### Container Won't Start

1. Check Docker Desktop is running
2. Verify no port conflicts: `lsof -i :4000`
3. Remove old containers: `docker-compose down -v`
4. Rebuild: `docker-compose up --build`

### Build Fails

If bundle install fails:

```bash
# Remove bundle cache and rebuild
docker-compose down -v
docker-compose up --build
```

## Performance Notes

### First Build
- Takes 2-3 minutes to download Ruby base image and install dependencies
- Subsequent builds use cached layers (much faster)

### Volume Caching
- Bundle dependencies are cached in a Docker volume (`bundle_cache`)
- Speeds up subsequent `docker-compose up` commands

### File Watching
- Docker Desktop for Mac/Windows uses file sharing
- Large projects may have slower file watching than native
- Performance is acceptable for this site size

## Comparison: Docker vs Native Ruby

| Aspect | Docker | Native Ruby 3.1+ |
|--------|--------|------------------|
| Setup time | 2-3 min (first time) | 15-30 min (rbenv/rvm setup) |
| Consistency | ✅ Exact GitHub Actions env | ⚠️ Depends on local Ruby version |
| Ruby 2.6 compatible | ✅ Yes | ❌ No (can't install gems) |
| File watching | ⚠️ Slightly slower | ✅ Fastest |
| Isolation | ✅ No conflicts | ⚠️ Shared gem environment |
| Disk usage | ~500MB Docker image | ~200MB rbenv/gems |

## What's Inside the Container?

- **Base**: `ruby:3.1-slim` (Debian Bookworm)
- **Installed**: build-essential, git, bundler, github-pages gem
- **Working dir**: `/site` (your project root mounted here)
- **Exposed ports**: 4000 (Jekyll), 35729 (LiveReload)

## Docker Commands Reference

```bash
# Start server with LiveReload
docker-compose up

# Start in background (detached)
docker-compose up -d

# View logs
docker-compose logs -f

# Stop server
docker-compose down

# Build only (no server)
docker-compose run --rm jekyll bundle exec jekyll build

# Clean build (remove _site/)
docker-compose run --rm jekyll bundle exec jekyll clean

# Check Jekyll version
docker-compose run --rm jekyll bundle exec jekyll --version

# Update dependencies
docker-compose run --rm jekyll bundle update

# Rebuild image from scratch
docker-compose build --no-cache
```

## Integration with CI/CD

This Docker setup mirrors your GitHub Actions environment:

**Local (Docker)**:
- Ruby 3.1
- Bundler cache
- github-pages gem

**GitHub Actions**:
- Ruby 3.1 (`.github/workflows/jekyll.yml`)
- Bundler cache enabled
- github-pages gem

Changes that work locally in Docker will work in CI/CD.

## Next Steps

1. **Start developing**: `docker-compose up`
2. **Make changes**: Edit files, see instant updates
3. **Commit**: Changes tested in production-like environment
4. **Push**: Confident that GitHub Actions will build successfully

## Additional Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [GitHub Pages Documentation](https://docs.github.com/pages)
