# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a bilingual (English/Vietnamese) personal research blog documenting investment and trading strategies. Built with Hugo static site generator using the Congo theme v2, the blog serves as a research notebook for interesting findings discovered through AI-assisted research (Perplexity) and manual exploration. Deployed on Netlify with automated continuous deployment.

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

- **English content**: `content/posts/post-name/index.md`
- **Vietnamese content**: `content/posts/post-name/index.vi.md`
- Language switching handled by Hugo's multilingual features
- Separate menu configurations per language: `menus.en.toml` and `menus.vi.toml`
- Posts use **page bundles** (directories) to organize content and images together

### Configuration Architecture
Hugo uses split configuration files in `config/_default/`:

- **`hugo.toml`** - Core site settings (baseURL, title, languages)
- **`params.toml`** - Congo theme parameters and feature toggles
- **`languages.en.toml`** / **`languages.vi.toml`** - Language-specific settings
- **`menus.en.toml`** / **`menus.vi.toml`** - Navigation menus per language
- **`module.toml`** - Hugo modules configuration (Congo theme import)
- **`markup.toml`** - Markdown rendering and syntax highlighting
- **`taxonomies.toml`** - Content categorization (tags, categories)

### Content Organization (Page Bundles)
```
content/
├── _index.md              # English homepage
├── _index.vi.md           # Vietnamese homepage
├── about.md / about.vi.md
├── contact.md / contact.vi.md
└── posts/
    ├── _index.md / _index.vi.md
    └── post-name/         # Page bundle directory
        ├── index.md       # English content
        ├── index.vi.md    # Vietnamese content
        ├── thumb.svg      # Thumbnail for listings
        └── cover.jpg      # Cover image (optional)
```

**Important:** All blog posts must use **page bundles** (directories) rather than standalone `.md` files. This allows Congo theme to:
- Automatically detect and display thumbnail images
- Co-locate images with post content
- Enable advanced Hugo features like resource processing

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

### Bilingual Workflow (Page Bundles)
1. Create page bundle directory: `mkdir content/posts/topic`
2. Create English version: `content/posts/topic/index.md`
3. Create Vietnamese version: `content/posts/topic/index.vi.md`
4. Add thumbnail image: `content/posts/topic/thumb.jpg` (or `.png`, `.svg`, `.webp`)
5. Hugo automatically links language versions within the same directory

**Note:** Hugo's `hugo new` command doesn't natively support page bundles, so create directories and files manually.

### Predefined Categories
Use these consistent categories across content:
- **Technology** - AI, blockchain, emerging tech
- **Digital Banking** - Neobanks, mobile banking
- **Payments** - Mobile payments, crypto, processing
- **Investment** - Trading, wealth management
- **Regulation** - Compliance, RegTech, policy

### Post Thumbnails and Images

The Congo theme automatically detects and displays images based on filename patterns:

**Thumbnail Images** (displayed in post listings):
- **Filename pattern:** Must contain `thumb` anywhere in the name
- **Valid examples:** `thumb.jpg`, `thumbnail.png`, `post-thumb.svg`, `thumb.webp`
- **Placement:** Same directory as `index.md` (page bundle root)
- **Aspect ratio:** Auto-cropped to 4:3 by Congo
- **Recommended size:** Minimum 1200x900px for quality

**Cover Images** (displayed at top of article page):
- **Filename pattern:** Must contain `cover` anywhere in the name
- **Valid examples:** `cover.jpg`, `header-cover.png`, `cover-image.webp`
- **Placement:** Same directory as `index.md`
- **Aspect ratio:** Any (automatically resized while maintaining aspect ratio)
- **Recommended size:** Minimum 1920x1080px

**Feature Images** (replaces both thumb and cover + social media):
- **Filename pattern:** Must contain `feature` anywhere in the name
- **Valid examples:** `feature.jpg`, `featured-image.png`
- **Priority:** Highest - overrides thumb and cover if present
- **Recommended size:** 1200x630px (optimal for social sharing)

**Image Formats:**
- Supported: JPG, PNG, WebP, SVG
- Congo automatically converts to WebP if `enableImageWebp = true` (default)
- SVG works great for placeholder thumbnails

**Example page bundle with images:**
```
content/posts/my-post/
├── index.md         # English content
├── index.vi.md      # Vietnamese content
├── thumb.svg        # Thumbnail (auto-detected)
├── cover.jpg        # Cover image (auto-detected)
└── diagram.png      # Other images referenced in post
```

**Accessibility:**
Add alt text in front matter:
```yaml
---
title: "Post Title"
featureAlt: "Description of feature image"
coverAlt: "Description of cover image"    # Inherits featureAlt if not set
thumbnailAlt: "Description of thumbnail"  # Inherits featureAlt if not set
coverCaption: "Photo credit or caption"
---
```

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

## Personal Branding & Contact Information

### Where to Update Personal Information

When you need to change personal details (name, bio, social media links, contact info), modify these files:

**Author Information & Social Links:**
1. **`config/_default/languages.en.toml`** - English author profile
   ```toml
   [params.author]
     name = "Your Name"              # Display name
     image = "img/author.jpg"        # Author photo
     headline = "Your Headline"       # Tagline/subtitle
     bio = "Your bio text..."        # Author bio
     links = [
       { linkedin = "https://linkedin.com/in/yourprofile" },
       { x-twitter = "https://twitter.com/yourhandle" },  # Optional
       { github = "https://github.com/yourhandle" },      # Optional
     ]
   ```

2. **`config/_default/languages.vi.toml`** - Vietnamese author profile
   - Same structure as English version
   - Translate name, headline, and bio to Vietnamese

**Contact Page:**
3. **`content/contact.md`** - English contact information
   - Update LinkedIn URL or other contact methods
   - Modify professional inquiry instructions

4. **`content/contact.vi.md`** - Vietnamese contact information
   - Mirror changes from English version

**About Page (Optional):**
5. **`content/about.md`** - Personal background and story
   - Update if you want to share more about yourself

6. **`content/about.vi.md`** - Vietnamese about page
   - Keep synchronized with English version

**Copyright:**
7. **`config/_default/languages.en.toml`** - Line with `copyright = "..."`
8. **`config/_default/languages.vi.toml`** - Same copyright line

### Quick Reference: Personal Info Files

| What to Change | Files to Modify |
|----------------|-----------------|
| **Name** | `languages.en.toml`, `languages.vi.toml` |
| **Bio/Headline** | `languages.en.toml`, `languages.vi.toml` |
| **Social Links** | `languages.en.toml`, `languages.vi.toml` |
| **Contact Info** | `contact.md`, `contact.vi.md` |
| **Author Photo** | Place image in `static/img/author.jpg`, reference in `languages.*.toml` |
| **Personal Story** | `about.md`, `about.vi.md` |
| **Copyright** | `languages.en.toml`, `languages.vi.toml` |

### Supported Social Media Links

Congo theme supports these social media platforms in `[params.author.links]`:
- `linkedin` - LinkedIn profile
- `x-twitter` - Twitter/X account
- `github` - GitHub profile
- `facebook` - Facebook page
- `instagram` - Instagram account
- `youtube` - YouTube channel
- `medium` - Medium profile
- `reddit` - Reddit profile
- `stackoverflow` - Stack Overflow profile
- `email` - Email address (displays as mailto link)

**Example with multiple platforms:**
```toml
links = [
  { linkedin = "https://linkedin.com/in/yourprofile" },
  { github = "https://github.com/yourhandle" },
  { x-twitter = "https://twitter.com/yourhandle" },
]
```

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
