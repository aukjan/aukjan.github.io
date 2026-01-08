# Coding Conventions

## Code Style

### EditorConfig Settings
```
indent_style = space
indent_size = 2          # 4 for Python
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

## Naming Conventions

### Files
- **Blog posts**: `YYYY-MM-DD-Title-With-Hyphens.md`
- **CSS**: Lowercase, descriptive (`poole.css`, `lanyon.css`)
- **Layouts**: Lowercase, semantic (`default.html`, `page.html`)

### CSS Classes
- **Style**: Kebab-case
- **Pattern**: BEM-like (`.sidebar`, `.sidebar-item`, `.sidebar-nav`)
- **Examples**: `.post-title`, `.page-title`, `.masthead-title`

## Template Conventions

### Jekyll Front Matter
```yaml
---
layout: post           # or 'page', 'default'
title: "Post Title"
excerpt_separator: <!--more-->
---
```

### Liquid Templating
- **Variables**: `{{ site.title }}`, `{{ page.title }}`
- **Control flow**: `{% if %}`, `{% for %}`, `{% assign %}`
- **Includes**: `{% include head.html %}`
- **Comments**: `{% comment %}...{% endcomment %}`

## Content Conventions

### Blog Post Structure
1. YAML front matter
2. Opening paragraph
3. `<!--more-->` separator (optional)
4. Main content in Markdown
5. Code blocks with triple backticks
6. GitHub Gists: `{% gist [gist-id] %}`

### Markdown Style
- **Headers**: ATX-style (`#`, `##`, `###`)
- **Code blocks**: Triple backticks (```)
- **Links**: `[text](url)`
- **Lists**: Mixed ordered/unordered

## CSS Architecture

### Three-Layer Structure
1. **Poole** (427 lines) - Foundation
   - Typography, resets, basic layout
   - Responsive design
2. **Lanyon** (527 lines) - Theme
   - Sidebar, masthead, navigation
   - Slide effects
3. **Syntax** (66 lines) - Highlighting
   - Rouge/Pygments styles

## Configuration Patterns

### Jekyll Config (_config.yml)
```yaml
highlighter: rouge
permalink: pretty
paginate: 15
baseurl: '/'
```

## HTML Structure
- Semantic HTML5
- 2-space indentation
- Class-based styling
- Minimal inline styles

## Git Conventions

### Commit Messages
- Concise, descriptive
- Examples: "Added gist", "Added post on flakey WiFi connection"
- No strict conventional commits

### .gitignore Patterns
- Jekyll: `_site`, `_gh_pages`
- Editors: `.DS_Store`, `.idea`, `*.sublime-*`
- Temp: `*.log`, `*.swp`, `*~`

## Notable Patterns
- **No JavaScript** - Pure static HTML/CSS
- **Template inheritance** - Layout hierarchy
- **Include pattern** - Reusable partials
- **Convention over configuration** - Directory-based routing
- **Front matter metadata** - YAML in content files
