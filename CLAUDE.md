# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a bilingual (English/Vietnamese) FinTech blog built with Hugo static site generator using the Congo theme v2. The blog is deployed on Netlify with automated continuous deployment.

## Essential Commands

### Development
```bash
# Start development server
hugo server

# Start server with drafts visible
hugo server -D

# Start server on custom port
hugo server --port 1314

# Start server accessible from network
hugo server --bind 0.0.0.0
```

### Building
```bash
# Build production site (outputs to public/)
hugo

# Build with minification (production-ready)
hugo --minify

# Build with garbage collection and minification (Netlify command)
hugo --gc --minify
```

### Content Management
```bash
# Create new blog post (automatically adds front matter)
hugo new posts/your-post-title.md

# Create Vietnamese version of post
hugo new posts/your-post-title.vi.md

# Update Hugo modules
hugo mod get -u

# Tidy Hugo modules
hugo mod tidy

# Clean module cache
hugo mod clean
```

## Architecture Overview

### Bilingual Content Strategy
This site supports English (default) and Vietnamese translations:

- **English content**: `content/posts/post-name.md`
- **Vietnamese content**: `content/posts/post-name.vi.md`
- Language switching handled by Hugo's multilingual features
- Separate menu configurations per language: `menus.en.toml` and `menus.vi.toml`

### Configuration Architecture
Hugo uses split configuration files in `config/_default/`:

- **`hugo.toml`** - Core site settings (baseURL, title, languages)
- **`params.toml`** - Congo theme parameters and feature toggles
- **`languages.en.toml`** / **`languages.vi.toml`** - Language-specific settings
- **`menus.en.toml`** / **`menus.vi.toml`** - Navigation menus per language
- **`module.toml`** - Hugo modules configuration (Congo theme import)
- **`markup.toml`** - Markdown rendering and syntax highlighting
- **`taxonomies.toml`** - Content categorization (tags, categories)

### Content Organization
```
content/
├── _index.md              # English homepage
├── _index.vi.md           # Vietnamese homepage
├── about.md / about.vi.md
├── contact.md / contact.vi.md
└── posts/
    ├── _index.md / _index.vi.md
    ├── post-name.md       # English version
    └── post-name.vi.md    # Vietnamese version
```

### Hugo Modules vs Traditional Themes
This project uses Hugo modules (modern approach) rather than git submodules:
- Theme is imported in `module.toml` with `path = "github.com/jpanther/congo/v2"`
- Theme files are cached in `_vendor/` directory (auto-generated)
- Updates managed via `hugo mod get -u`

## Creating Bilingual Content

### Required Front Matter
Every blog post must include these parameters:

```yaml
---
title: "Your Post Title"
date: 2024-07-19T10:00:00+07:00
draft: false
description: "SEO-friendly description"
tags: ["tag1", "tag2", "tag3"]
categories: ["Category"]
---
```

### Bilingual Workflow
1. Create English version: `hugo new posts/topic.md`
2. Create Vietnamese version: `hugo new posts/topic.vi.md`
3. Ensure both files have matching slugs (filename before extension)
4. Hugo automatically links language versions

### Predefined Categories
Use these consistent categories across content:
- **Technology** - AI, blockchain, emerging tech
- **Digital Banking** - Neobanks, mobile banking
- **Payments** - Mobile payments, crypto, processing
- **Investment** - Trading, wealth management
- **Regulation** - Compliance, RegTech, policy

### Mathematical Notation with KaTeX

The Congo theme has built-in KaTeX support for rendering mathematical formulas. To enable it:

**1. Add the KaTeX shortcode** (once per article, anywhere in content):
```markdown
{{< katex >}}
```

**2. Use proper delimiters:**
- **Block equations** (centered, standalone): Use `$$` delimiters
  ```markdown
  $$
  f(x) = x^2 + 2x + 1
  $$
  ```

- **Inline equations** (within text): Use `\(` and `\)` delimiters
  ```markdown
  The complexity is \(\mathcal{O}(n \log n)\) for this algorithm.
  ```

**Important:**
- Never use `$$` for inline math (common mistake) - always use `\(` and `\)`
- The shortcode must be present for any math to render
- No configuration needed in `params.toml` - KaTeX is built into Congo theme
- Assets load on-demand only when shortcode is used (performance optimized)

## Deployment Configuration

### Netlify Setup
The site is configured for Netlify in `netlify.toml`:
- **Hugo version**: 0.148.0
- **Go version**: 1.24.2
- **Node version**: 22
- **Build command**: `git config core.quotepath false && hugo --gc --minify`
- **Publish directory**: `public`

### Deploy Contexts
- **Production**: Builds from `main` branch
- **Deploy previews**: Automatic builds for pull requests
- **Branch deploys**: Custom branch URLs

### Security Headers
Netlify serves all pages with security headers defined in `netlify.toml`:
- X-Frame-Options, X-XSS-Protection, X-Content-Type-Options
- Content-Security-Policy with strict rules
- Referrer-Policy for privacy

## Important Notes

### When Creating Content
- Always set `draft: false` to publish (or omit the draft parameter)
- Use ISO 8601 date format with timezone: `2024-07-19T10:00:00+07:00`
- Keep descriptions concise (150-160 characters for SEO)
- Tags should be lowercase and specific
- Include both English and Vietnamese versions for bilingual support

### When Modifying Configuration
- Changes to `config/_default/` files require server restart to take effect
- After modifying `module.toml`, run `hugo mod tidy`
- Clear Hugo cache with `hugo mod clean` if seeing unexpected behavior
- Never modify files in `_vendor/` (auto-generated from theme)

### When Updating Theme
- Update Congo theme: `hugo mod get -u github.com/jpanther/congo/v2`
- Review Congo documentation for breaking changes
- Test thoroughly as theme updates may affect layout/functionality

### Scope of Impact Analysis
When making changes, always document in CHANGELOG.md:
- List all modified configuration files
- Note any new or changed content files
- Specify impacted features or functionality
- Categorize changes as Added/Changed/Fixed/Removed

## Common Issues

### "Page Not Found" Errors
- Ensure `module.toml` has `[[imports]] path = "github.com/jpanther/congo/v2"`
- Run `hugo mod tidy` to refresh modules
- Check that content files have valid front matter

### Multilingual Issues
- Verify language codes match in `hugo.toml` (en, vi)
- Ensure language-specific config files exist for both languages
- Check that content file extensions match language codes (.vi.md)

### Build Failures on Netlify
- Verify Hugo version matches `netlify.toml` (0.148.0)
- Check that `baseURL = "/"` in `hugo.toml` for Netlify compatibility
- Ensure all content files have valid front matter
- Review Netlify deploy logs for specific error messages

## Version Information
- **Hugo**: v0.148.0 extended (required for Sass/SCSS)
- **Go**: 1.24.2 (for Hugo modules)
- **Node**: 22 (for modern features)
- **Congo Theme**: v2.12.2 (via Hugo modules)
