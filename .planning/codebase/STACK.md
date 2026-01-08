# Technology Stack

## Overview
Jekyll-based static website (GitHub Pages) using the Lanyon theme built on Poole framework. Pure static site with no JavaScript, backend, or database.

## Languages
- **HTML** - Templates and layouts (Liquid templating)
- **CSS** - Styling (1020 lines across 3 files)
- **Markdown** - Content files (blog posts)
- **Python 3** - Development preview server only

## Primary Framework
**Jekyll** - Static site generator
- Version: Unknown (no Gemfile)
- Hosted on GitHub Pages
- Rouge syntax highlighter
- jekyll-paginate plugin

## CSS Framework
**Lanyon Theme** (based on Poole)
- poole.css (427 lines) - Base styles
- lanyon.css (527 lines) - Theme styles
- syntax.css (66 lines) - Code highlighting
- Custom styles.css (232 lines) - Portfolio styles

## Typography
- **Google Fonts**: PT Serif, PT Sans
- **Roboto** (for modern homepage)

## Development Tools
- **preview.py** - Python SimpleHTTPServer on port 8000
- **EditorConfig** - Code style enforcement

## Deployment
- **GitHub Pages** - Static hosting
- **Custom Domain**: aukjan.vanbelkum.nl (via CNAME)

## Key Dependencies
- Jekyll (no version pinned)
- Rouge (syntax highlighting)
- jekyll-paginate (pagination)
- No package manager files (Gemfile missing)

## Notable Absences
- No JavaScript
- No build tools (webpack, gulp, grunt)
- No CSS preprocessors
- No package.json or Gemfile
- No testing frameworks
