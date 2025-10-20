# Changelog

All notable changes to the FinTech Insights blog project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.7] - 2025-10-20

### Changed
- 🔄 **Visual appearance configuration** - Updated `config/_default/params.toml` with 7 parameter changes

**TOML Parameter Changes:**

1. `colorScheme = "sapphire"` (was "congo") - Line 8
2. `[homepage] layout = "profile"` (was "page") - Line 34
3. `[article] showTaxonomies = true` (was false) - Line 52
4. `[article] sharingLinks = ["linkedin", "x-twitter", "reddit", "email", "facebook", "threads", "pinterest"]` (was commented) - Line 55
5. `[list] showSummary = true` (was false) - Line 59
6. `[list] showTaxonomies = true` (was false) - Line 61
7. `[list] groupByYear = true` (was false) - Line 62

### Added
- ✅ **Visual Customization & Appearance** section in CLAUDE.md documenting all appearance settings

## [1.0.6] - 2025-10-19

### Added
- ✅ **Page bundle structure** for all blog posts to support images and resources
- ✅ **Thumbnail images** for all posts using SVG placeholders with unique gradients
- ✅ **Post Thumbnails and Images documentation** in CLAUDE.md with comprehensive guidelines
- ✅ **Automatic image detection** via Congo theme's filename pattern matching

### Changed
- 🔄 **Content structure migration** - Converted all standalone `.md` files to page bundles
  - `ai-in-finance.md` → `ai-in-finance/index.md`
  - `cryptocurrency-adoption-2024.md` → `cryptocurrency-adoption-2024/index.md`
  - `n8n-automation.md` → `n8n-automation/index.md`
  - `last-puff.md` + `last-puff.vi.md` → `last-puff/index.md` + `last-puff/index.vi.md`
  - `monte-carlo.md` → `monte-carlo/index.md`
  - `welcome-to-fintech-insights.md` + `.vi.md` → `welcome-to-fintech-insights/index.md` + `index.vi.md`
- 🔄 **CLAUDE.md structure** - Updated content organization examples to reflect page bundles
- 🔄 **Bilingual workflow** - Updated to use page bundles instead of standalone files

### Scope of Impact

**Files Restructured:**
- All 6 blog posts converted from standalone files to page bundle directories
- Each page bundle contains `index.md` (and `index.vi.md` for bilingual posts)
- SVG thumbnail added to each page bundle

**New Files Created:**
- `content/posts/ai-in-finance/thumb.svg` - Blue/purple gradient
- `content/posts/cryptocurrency-adoption-2024/thumb.svg` - Pink/red gradient
- `content/posts/n8n-automation/thumb.svg` - Cyan/blue gradient
- `content/posts/last-puff/thumb.svg` - Pink/yellow gradient
- `content/posts/monte-carlo/thumb.svg` - Teal/dark blue gradient
- `content/posts/welcome-to-fintech-insights/thumb.svg` - Multi-color pastel gradient

**Documentation Updated:**
- `CLAUDE.md` - Added comprehensive "Post Thumbnails and Images" section
- `CLAUDE.md` - Updated "Content Organization" to show page bundle structure
- `CLAUDE.md` - Updated "Bilingual Workflow" for page bundles

**Functionality Impacted:**
- Post listings now display thumbnail images next to titles
- Thumbnails auto-cropped to 4:3 aspect ratio by Congo theme
- Page bundles enable co-location of post content with images
- Hugo resource processing features now available for all posts
- Bilingual posts share thumbnails within same directory

**Technical Details:**
- Congo theme automatically detects images based on filename patterns (`thumb`, `cover`, `feature`)
- No configuration changes required - works out of the box
- SVG format used for placeholders (can be replaced with JPG/PNG/WebP)
- Recommended thumbnail size: 1200x900px (4:3 ratio)
- All images automatically converted to WebP by Congo if `enableImageWebp = true`

**User Impact:**
- Improved visual presentation in post listings
- Better UX with recognizable post thumbnails
- Easier to identify posts at a glance
- SVG placeholders ready for replacement with custom images

## [1.0.5] - 2025-10-19

### Added
- ✅ **KaTeX support documentation** in CLAUDE.md with proper usage guidelines
- ✅ **Mathematical notation rendering** enabled for all blog posts with formulas

### Fixed
- 🐛 **LaTeX rendering** - Added `{{< katex >}}` shortcode to posts with mathematical notation
  - Fixed `content/posts/last-puff.md` - Added shortcode and corrected inline math delimiters
  - Fixed `content/posts/last-puff.vi.md` - Added shortcode and corrected inline math delimiters
  - Fixed `content/posts/monte-carlo.md` - Added shortcode and corrected inline math delimiters
- 🐛 **Inline math delimiter correction** - Changed incorrect `$$` to `\(` and `\)` for inline formulas
  - Line 161 in last-puff.md: `$$(100 - 70)/10 = \$3$$` → `\((100 - 70)/10 = \$3\)`
  - Line 173 in last-puff.vi.md: `$$(100 - 70)/10 = \$3$$` → `\((100 - 70)/10 = \$3\)`
  - Line 39 in monte-carlo.md: `$$\mathcal{O}(1/\sqrt{n})$$` → `\(\mathcal{O}(1/\sqrt{n})\)`
  - Line 43 in monte-carlo.md: `$$\Omega(\epsilon)$$` and `$$\mathcal{O}(\epsilon^3)$$` → `\(\Omega(\epsilon)\)` and `\(\mathcal{O}(\epsilon^3)\)`

### Changed
- 📝 **Documentation enhancement** - Added comprehensive KaTeX usage section to CLAUDE.md

### Scope of Impact
**Files Modified:**
- `CLAUDE.md` - Added "Mathematical Notation with KaTeX" section
- `content/posts/last-puff.md` - Added KaTeX shortcode, fixed inline math syntax
- `content/posts/last-puff.vi.md` - Added KaTeX shortcode, fixed inline math syntax
- `content/posts/monte-carlo.md` - Added KaTeX shortcode, fixed inline math syntax

**Functionality Impacted:**
- Mathematical formulas now render correctly using KaTeX
- Block equations display as centered, standalone elements
- Inline equations render properly within text flow

**Technical Details:**
- Congo theme's built-in KaTeX support activated via shortcode
- No configuration changes required in `params.toml`
- On-demand asset loading maintains performance

## [1.0.4] - 2025-07-19

### Added
- ✅ **Vietnamese language support** with full translations
- ✅ **Bilingual menu configuration** (English/Vietnamese)
- ✅ **Vietnamese content structure** ready for localization

### Changed
- 🔄 **Language configuration** simplified to English and Vietnamese only
- 🔄 **Menu translations** updated for Vietnamese interface

### Removed
- ❌ **Unnecessary language files** (German, Spanish, Japanese, Chinese)
- ❌ **Corresponding menu files** for removed languages

## [1.0.3] - 2025-07-19

### Added
- ✅ **Netlify deployment configuration** with netlify.toml
- ✅ **Security headers** for enhanced site protection
- ✅ **Redirect rules** for proper URL handling

### Changed
- 🔄 **Site baseURL** updated for Netlify compatibility
- 🔄 **Removed GitHub Pages** deployment in favor of Netlify

### Fixed
- 🐛 **URL structure** optimized for Netlify hosting

## [1.0.2] - 2024-07-19

### Added
- ✅ **GitHub Actions workflow** for automated deployment to GitHub Pages
- ✅ **Deployment configuration** with Hugo modules support
- ✅ **Production baseURL** updated for GitHub Pages
- ✅ **Manual deployment trigger** option in GitHub Actions

### Changed
- 🔄 **Site baseURL** updated from localhost to https://gahoccode.github.io/blog/

## [1.0.1] - 2024-07-19

### Added
- ✅ **GitHub repository** created at https://github.com/gahoccode/blog
- ✅ **Version control** initialized with Git
- ✅ **Initial commit** with all project files
- ✅ **Repository documentation** updated with correct clone URL

## [1.0.0] - 2024-07-19

### Added
- ✅ **Initial Hugo site setup** with Congo theme v2.12.2
- ✅ **Hugo modules configuration** for modern theme management
- ✅ **Complete site branding** as "FinTech Insights"
- ✅ **5 comprehensive blog posts** covering key fintech topics:
  - Welcome to FinTech Insights (introduction)
  - Digital Banking Revolution (neobanks and challenger banks)
  - AI in Finance (machine learning and automation)
  - Cryptocurrency Adoption 2024 (digital currency trends)
  - RegTech Revolution (compliance automation)
- ✅ **Essential pages**:
  - Homepage with welcome content and overview
  - About page with mission and team information
  - Contact page with communication channels
  - Posts index page
- ✅ **Navigation menu** with Posts, About, and Contact links
- ✅ **Multi-language support** (EN, ES, JA, ZH-Hans, DE)
- ✅ **Search functionality** enabled
- ✅ **Responsive design** with dark/light mode toggle
- ✅ **SEO optimization** with proper meta tags and descriptions
- ✅ **Hot reload development server** for immediate change reflection
- ✅ **Comprehensive README.md** with setup and usage instructions

### Fixed
- 🔧 **Hugo modules initialization** - Added proper go.mod configuration
- 🔧 **Congo theme installation** - Resolved module dependency issues
- 🔧 **Theme loading problem** - Fixed missing `[[imports]]` in module.toml
- 🔧 **Site title display** - Corrected configuration hierarchy
- 🔧 **Page Not Found errors** - Resolved theme layout loading issues
- 🔧 **Configuration conflicts** - Cleaned up legacy settings
- 🔧 **Cache issues** - Implemented proper cache clearing procedures

### Changed
- 🔄 **Homepage layout** from "custom" to "page" for better content display
- 🔄 **Main sections** from "samples" to "posts" for blog content
- 🔄 **Site language** from "en-AU" to "en-US"
- 🔄 **Author information** customized for FinTech Insights team
- 🔄 **Menu structure** replaced default items with relevant pages
- 🔄 **Edit functionality** disabled (no GitHub repository yet)

### Removed
- ❌ **Default Hugo content** and placeholder text
- ❌ **Congo example configuration** references
- ❌ **Unused menu items** (Users, GitHub links)
- ❌ **Legacy theme directive** (replaced with modules)

## Technical Implementation Details

### Hugo Configuration Structure
```
config/
└── _default/
    ├── hugo.toml          # Main site configuration
    ├── params.toml        # Theme parameters and features
    ├── languages.en.toml  # English language settings
    ├── menus.en.toml      # Navigation menu structure
    ├── module.toml        # Hugo modules configuration
    ├── markup.toml        # Markdown processing settings
    └── taxonomies.toml    # Content categorization
```

### Content Organization
```
content/
├── _index.md              # Homepage content
├── about.md               # About page
├── contact.md             # Contact information
├── posts/
│   ├── _index.md          # Posts section index
│   ├── welcome-to-fintech-insights.md
│   ├── digital-banking-revolution.md
│   ├── ai-in-finance.md
│   ├── cryptocurrency-adoption-2024.md
│   └── regtech-compliance-automation.md
```

### Key Configuration Changes

#### 1. Hugo Modules Setup
- **File**: `config/_default/module.toml`
- **Change**: Added `[[imports]] path = "github.com/jpanther/congo/v2"`
- **Impact**: Enables proper theme loading via Hugo modules

#### 2. Site Identity
- **File**: `config/_default/hugo.toml`
- **Changes**:
  - `baseURL = "http://localhost:1313/"`
  - `title = "FinTech Insights"`
  - Commented out legacy theme directive

#### 3. Language Configuration
- **File**: `config/_default/languages.en.toml`
- **Changes**:
  - `title = "FinTech Insights"`
  - `copyright = "&copy; 2024 FinTech Insights"`
  - `mainSections = ["posts"]`
  - Updated author information and site description

#### 4. Theme Parameters
- **File**: `config/_default/params.toml`
- **Changes**:
  - `[homepage] layout = "page"`
  - `showEdit = false`
  - Enabled search, code copy, image optimization
  - Configured article display options

#### 5. Navigation Menu
- **File**: `config/_default/menus.en.toml`
- **Changes**:
  - Added "Posts" menu item
  - Added "About" menu item
  - Added "Contact" menu item
  - Removed default Congo example items

### Development Server Configuration
- **Command**: `hugo server --port 1313 --bind 0.0.0.0 --disableFastRender --watch`
- **Features**:
  - Hot reload enabled
  - Full rebuilds for accuracy
  - Network accessible
  - File watching active

### Troubleshooting Steps Performed

#### Issue 1: "Page Not Found" Error
- **Cause**: Missing theme imports in module configuration
- **Solution**: Added `[[imports]]` section to `module.toml`
- **Result**: Theme layouts now load properly

#### Issue 2: Site Title Not Updating
- **Cause**: Configuration caching and hierarchy issues
- **Solution**: Cache clearing and proper config structure
- **Result**: "FinTech Insights" displays correctly

#### Issue 3: Theme Assets Not Loading
- **Cause**: Hugo modules not properly initialized
- **Solution**: Reinstalled theme with `hugo mod get github.com/jpanther/congo/v2`
- **Result**: All theme assets and styling work correctly

### Performance Metrics
- **Build Time**: ~20ms for incremental builds
- **Pages Generated**: 25 pages across 5 languages
- **Theme Version**: Congo v2.12.2
- **Hugo Version**: v0.148.1+extended

### Next Steps
- [ ] Set up GitHub repository for version control
- [ ] Configure deployment pipeline (Netlify/Vercel)
- [ ] Add more blog content and categories
- [ ] Implement comment system
- [ ] Set up analytics tracking
- [ ] Add social media integration
- [ ] Create custom logo and favicon
- [ ] Optimize images and assets

---

**Project Status**: ✅ **COMPLETE** - Fully functional FinTech blog with modern Hugo setup

**Last Updated**: July 19, 2024  
**Maintainer**: FinTech Insights Team
