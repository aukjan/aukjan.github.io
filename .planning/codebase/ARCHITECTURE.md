# Architecture

## System Design
**Static Site Generator (Jekyll)** - Template-based content generation at build time.

## Architectural Pattern
**Layered Static Architecture**
```
Content Layer (Markdown + YAML)
       ↓
Template Layer (Liquid + HTML)
       ↓
Build Process (Jekyll)
       ↓
Static Output (HTML/CSS)
```

## Data Flow
1. **Content Creation**: Markdown files in _posts/ with YAML front matter
2. **Template Processing**: Liquid engine processes layouts and includes
3. **Build**: Jekyll compiles to static HTML in _site/ (git-ignored)
4. **Deployment**: GitHub Pages serves static files
5. **Delivery**: CDN delivers to browsers

## Design Patterns

### Template Hierarchy
- **Base Layout**: default.html (sidebar, masthead, structure)
- **Page Layout**: page.html (extends default)
- **Post Layout**: post.html (extends default, adds sharing)

### Component Model
- **Includes**: Reusable partials (head.html, sidebar.html)
- **Layouts**: Page templates with content injection
- **Front Matter**: Metadata embedded in content

### Content Organization
```
/
├── _config.yml          # Site configuration
├── _layouts/            # Template hierarchy
│   ├── default.html    # Base template
│   ├── page.html       # Static pages
│   └── post.html       # Blog posts
├── _includes/           # Partial components
│   ├── head.html       # <head> section
│   └── sidebar.html    # Navigation
├── _posts/              # Blog content (YYYY-MM-DD-title.md)
├── public/              # Static assets
│   ├── css/            # Stylesheets
│   └── img/            # Images
├── index.html           # Homepage
├── about.md             # About page
└── archive.md           # Blog archive
```

## Key Architectural Decisions

### 1. Static Generation
- **Why**: No backend needed, fast delivery, secure
- **Trade-off**: Dynamic features require rebuild

### 2. Dual Homepage Strategy
- **Issue**: Two competing architectures exist
  - Jekyll blog (Lanyon theme)
  - Standalone HTML (modern portfolio)
- **Concern**: Unclear which is primary

### 3. No JavaScript
- **Why**: Simplicity, performance, accessibility
- **Limitation**: No client-side interactivity

### 4. GitHub Pages Native
- **Why**: Free hosting, automatic builds
- **Limitation**: Restricted Jekyll plugins

## Rendering Flow
```
User Request → GitHub CDN → Static HTML
                              ↓
                         Browser renders
                              ↓
                         CSS applied
                              ↓
                    Google Fonts loaded
```

## Template Processing
```liquid
{% include head.html %}
{{ content }}
{% for post in site.posts %}
  {{ post.title }}
{% endfor %}
```

## Build Process
1. Jekyll reads _config.yml
2. Processes Liquid templates
3. Converts Markdown to HTML
4. Applies syntax highlighting (Rouge)
5. Generates pagination
6. Outputs to _site/

## Scalability Considerations
- **Content**: Unlimited blog posts (static generation)
- **Traffic**: CDN handles high load
- **Build Time**: Linear with content count
- **Storage**: Minimal (text files only)
