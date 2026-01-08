# Codebase Structure

## Directory Layout
```
/Users/aj/Projects/private/aukjan.github.io/
├── _config.yml                 # Jekyll configuration
├── index.html                  # Standalone homepage (modern portfolio)
├── about.md                    # Executive profile page
├── archive.md                  # Blog post archive
├── atom.xml                    # RSS/Atom feed template
├── 404.html                    # Custom error page
├── preview.py                  # Local dev server (Python)
├── styles.css                  # Custom standalone styles
├── CNAME                       # Custom domain config
├── LICENSE.md                  # MIT License (Mark Otto)
├── keybase.txt                 # Identity verification
├── .editorconfig               # Code style rules
├── .gitignore                  # Git exclusions
│
├── _layouts/                   # Jekyll templates
│   ├── default.html           # Base layout (sidebar, structure)
│   ├── page.html              # Static page wrapper
│   └── post.html              # Blog post template
│
├── _includes/                  # Reusable components
│   ├── head.html              # <head> section
│   └── sidebar.html           # Navigation drawer
│
├── _posts/                     # Blog content (4 posts from 2016)
│   ├── 2016-02-21-Outlook-wont-start.md
│   ├── 2016-02-23-Ansible-inventory-from-Terraform.md
│   ├── 2016-10-21-OS-X-El-Capitan-WIFI-Inconsitent.md
│   └── 2016-12-21-OS-X-El-Capitain-WIFI-Woes.md
│
└── public/                     # Static assets
    ├── css/
    │   ├── poole.css          # Base styles (427 lines)
    │   ├── lanyon.css         # Theme styles (527 lines)
    │   └── syntax.css         # Code highlighting (66 lines)
    ├── img/
    │   ├── outlook_rebuild.png
    │   └── ping_to_google.png
    ├── favicon.ico
    └── apple-touch-icon-144-precomposed.png
```

## Module Organization

### Content Layer
- **_posts/**: Date-prefixed Markdown files (YYYY-MM-DD-title.md)
- **Root .md files**: Static pages processed by Jekyll
- **_config.yml**: Site-wide settings (title, URL, author, pagination)

### Presentation Layer
- **_layouts/**: Template hierarchy (default → page/post)
- **_includes/**: Partial components (DRY principle)

### Asset Layer
- **public/css/**: Three-tier CSS architecture
  - Poole (foundation)
  - Lanyon (theme)
  - Syntax (highlighting)
- **public/img/**: Blog post images
- **styles.css** (root): Orphaned standalone styles

### Configuration Files
- **.editorconfig**: 2-space indents, LF line endings, UTF-8
- **.gitignore**: Excludes _site/, editor files, temp files
- **CNAME**: aukjan.vanbelkum.nl

## File Naming Conventions

### Blog Posts
Pattern: `YYYY-MM-DD-Title-With-Hyphens.md`

### CSS Files
Descriptive, lowercase: `poole.css`, `lanyon.css`, `syntax.css`

### Layouts
Semantic, lowercase: `default.html`, `page.html`, `post.html`

## Key Characteristics

### Strengths
- Clear separation of concerns
- Logical directory structure
- Convention-based routing

### Concerns
- **Dual architecture**: Jekyll blog + standalone HTML
- **Missing dependencies**: No Gemfile or package.json
- **Untracked files**: preview.py, styles.css not committed
- **Modified files**: _config.yml, about.md, index.html uncommitted
- **Old content**: All posts from 2016

## Build Output
- **_site/**: Generated static files (git-ignored)
- Not present in repository
- Created during Jekyll build
