# FinTech Insights Blog

A modern financial technology blog built with Hugo and the Congo theme, exploring the latest trends, innovations, and insights in the fintech industry.

## 🚀 Quick Start

### Prerequisites

- Hugo Extended v0.148.0 or later (matches Netlify deployment)
- Go 1.24.2 or later (for Hugo modules)
- Node.js 22 or later (for modern features)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/gahoccode/blog.git
cd blog
```

2. Install Hugo modules:
```bash
hugo mod tidy
```

3. Start the development server:
```bash
hugo server
```

4. Open your browser and visit `http://localhost:1313`

## 📁 Project Structure

```
fintech-blog/
├── config/                    # Hugo configuration files
│   └── _default/             # Default configuration directory
│       ├── hugo.toml         # Main site configuration (title, baseURL, etc.)
│       ├── params.toml       # Theme parameters and features
│       ├── languages.en.toml # English language settings and site info
│       ├── menus.en.toml     # Navigation menu structure
│       ├── module.toml       # Hugo modules and theme imports
│       ├── markup.toml       # Markdown processing settings
│       └── taxonomies.toml   # Content categorization (tags, categories)
├── content/                   # All site content (Markdown files)
│   ├── posts/                # Blog posts directory
│   │   ├── _index.md         # Posts section page
│   │   ├── welcome-to-fintech-insights.md
│   │   ├── digital-banking-revolution.md
│   │   ├── ai-in-finance.md
│   │   ├── cryptocurrency-adoption-2024.md
│   │   └── regtech-compliance-automation.md
│   ├── _index.md             # Homepage content
│   ├── about.md              # About page
│   └── contact.md            # Contact page
├── static/                    # Static assets (images, CSS, JS)
│   └── img/                  # Images directory
├── public/                    # Generated site (created by Hugo)
├── resources/                 # Hugo processing cache
├── go.mod                     # Go modules dependencies
├── go.sum                     # Go modules checksums
├── README.md                  # Project documentation
└── CHANGELOG.md              # Project change history
```

### 📂 Directory Breakdown

#### `/config/_default/`
Contains all Hugo configuration files that control site behavior:

- **`hugo.toml`** - Core site settings (title, baseURL, language)
- **`params.toml`** - Theme-specific parameters and feature toggles
- **`languages.en.toml`** - Language-specific settings (title, description, author)
- **`menus.en.toml`** - Navigation menu structure and links
- **`module.toml`** - Hugo modules configuration and theme imports
- **`markup.toml`** - Markdown processing and syntax highlighting
- **`taxonomies.toml`** - Content categorization system

#### `/content/`
All website content written in Markdown:

- **`_index.md`** - Homepage content and layout
- **`posts/`** - Blog posts directory with section index
- **`about.md`** - About page content
- **`contact.md`** - Contact information page

#### `/static/`
Static assets served directly by the web server:

- Images, logos, favicons
- Custom CSS and JavaScript files
- Documents and downloads

#### Generated Directories
- **`public/`** - Built website (created by `hugo` command)
- **`resources/`** - Hugo's processing cache for optimization

## 🎨 Theme

This blog uses the [Congo theme](https://github.com/jpanther/congo) for Hugo, which provides:

- Modern, responsive design
- Dark/light mode toggle
- Search functionality
- SEO optimization
- Social media integration
- Multiple layout options

## ✍️ Creating and Managing Content

### 📝 Creating New Blog Posts

#### Method 1: Using Hugo CLI (Recommended)
```bash
# Create a new post with proper front matter
hugo new posts/my-new-post.md
```

#### Method 2: Manual Creation
1. Create a new `.md` file in `content/posts/`
2. Add the front matter template (see below)
3. Write your content in Markdown

### 🏷️ Front Matter Template

Every blog post must start with front matter (metadata) between `---` markers:

```yaml
---
title: "Your Post Title"
date: 2024-07-19T10:00:00+07:00
draft: false
description: "Brief description for SEO and social sharing"
tags: ["fintech", "banking", "technology"]
categories: ["Digital Banking"]
showDate: true
showAuthor: true
showReadingTime: true
showTableOfContents: true
showEdit: false
---
```

### 🔧 Built-in Parameters for Posts

#### Required Parameters
- **`title`** - Post title (appears in browser tab and headers)
- **`date`** - Publication date in ISO 8601 format
- **`draft`** - Set to `false` to publish, `true` to keep as draft

#### SEO and Social Parameters
- **`description`** - Meta description for search engines and social media
- **`tags`** - Array of relevant keywords for the post
- **`categories`** - Main topic categories for organization

#### Display Control Parameters
- **`showDate`** - Show/hide publication date (default: true)
- **`showAuthor`** - Show/hide author information (default: true)
- **`showReadingTime`** - Show/hide estimated reading time (default: true)
- **`showTableOfContents`** - Show/hide table of contents (default: true)
- **`showEdit`** - Show/hide edit link (default: false)
- **`showBreadcrumbs`** - Show/hide navigation breadcrumbs (default: true)
- **`showPagination`** - Show/hide next/previous post links (default: true)
- **`showComments`** - Show/hide comment section (default: false)

#### Advanced Parameters
- **`weight`** - Control post ordering (lower numbers appear first)
- **`aliases`** - Alternative URLs that redirect to this post
- **`images`** - Array of image URLs for social media sharing
- **`series`** - Group related posts together
- **`externalUrl`** - Link to external content instead of post content

### 📂 Content Categories

Use these predefined categories for consistency:

- **Digital Banking** - Neobanks, mobile banking, traditional banking evolution
- **Technology** - AI, blockchain, emerging technologies  
- **Payments** - Mobile payments, cryptocurrencies, payment processing
- **Investment** - Robo-advisors, trading platforms, wealth management
- **Regulation** - Compliance, RegTech, policy developments
- **General** - Industry news, trends, analysis

### 🏷️ Recommended Tags

Use specific, relevant tags to improve discoverability:

```yaml
# Technology tags
tags: ["artificial intelligence", "machine learning", "blockchain", "api", "mobile app"]

# Business tags  
tags: ["startup", "funding", "ipo", "merger", "partnership"]

# Financial services tags
tags: ["banking", "lending", "insurance", "wealth management", "trading"]

# Regulatory tags
tags: ["compliance", "kyc", "aml", "gdpr", "pci dss"]
```

### 📋 User Workflow for Creating Posts

#### Step 1: Create the Post
```bash
# Navigate to your project directory
cd fintech-blog

# Create new post (Hugo will generate front matter)
hugo new posts/your-post-title.md
```

#### Step 2: Edit Front Matter
Open the created file and customize the front matter:

```yaml
---
title: "The Future of Digital Payments"
date: 2024-07-19T14:30:00+07:00
draft: false
description: "Exploring emerging trends in digital payment technologies and their impact on consumer behavior."
tags: ["digital payments", "mobile payments", "fintech", "consumer behavior"]
categories: ["Payments"]
showTableOfContents: true
---
```

#### Step 3: Write Content
Add your content below the front matter using Markdown:

```markdown
# Introduction

Your introduction here...

## Key Trends

### Mobile-First Payments
Content about mobile payments...

### Cryptocurrency Integration  
Content about crypto payments...

## Conclusion

Your conclusion here...
```

#### Step 4: Preview and Test
```bash
# Start development server to preview
hugo server -D

# Visit http://localhost:1313 to see your post
```

#### Step 5: Publish
```bash
# Change draft: true to draft: false in front matter
# Or remove the draft parameter entirely
```

### 🧭 Updating Navigation Menu

#### Adding New Menu Items
Edit `config/_default/menus.en.toml`:

```toml
[[main]]
  name = "New Section"
  pageRef = "new-section"  # Points to content/new-section/
  weight = 40

# Or link to external URL
[[main]]
  name = "External Link"
  url = "https://example.com"
  weight = 50
  [main.params]
    target = "_blank"  # Open in new tab
```

#### Menu Item Parameters
- **`name`** - Display text for the menu item
- **`pageRef`** - Reference to internal page/section
- **`url`** - Direct URL (for external links)
- **`weight`** - Order in menu (lower numbers appear first)
- **`target`** - `"_blank"` to open in new tab

#### Creating New Sections
1. Create directory: `content/new-section/`
2. Add index file: `content/new-section/_index.md`
3. Add front matter to index file:

```yaml
---
title: "New Section"
description: "Description of this section"
---

# New Section

Content for the section landing page...
```

### 📁 Files to Modify for Customization

#### Site Identity and Branding
- **`config/_default/hugo.toml`** - Site title, baseURL
- **`config/_default/languages.en.toml`** - Site description, author info, copyright

#### Theme and Appearance  
- **`config/_default/params.toml`** - Color scheme, layout options, feature toggles

#### Navigation and Menu
- **`config/_default/menus.en.toml`** - Add/remove/reorder menu items

#### Content Organization
- **`config/_default/taxonomies.toml`** - Define custom categories and tags

#### Homepage Content
- **`content/_index.md`** - Homepage text and layout

#### Static Assets
- **`static/img/`** - Add logos, images, favicons
- **`static/css/`** - Custom CSS overrides

### 🔄 Complete Workflow Summary

1. **Create Post**: `hugo new posts/post-name.md`
2. **Edit Front Matter**: Set title, description, tags, categories
3. **Write Content**: Use Markdown below front matter
4. **Preview**: `hugo server -D` and visit localhost:1313
5. **Publish**: Set `draft: false` in front matter
6. **Update Menu** (if needed): Edit `config/_default/menus.en.toml`
7. **Add Assets** (if needed): Place images in `static/img/`
8. **Deploy**: Build with `hugo` and deploy `public/` directory

## 🛠️ Development

### Local Development

```bash
# Start development server with drafts
hugo server -D

# Start server on specific port
hugo server --port 1314

# Start server accessible from network
hugo server --bind 0.0.0.0
```

### Building for Production

```bash
# Build static site
hugo

# Build with minification
hugo --minify
```

### Updating the Theme

```bash
# Update Hugo modules
hugo mod get -u

# Clean module cache if needed
hugo mod clean
```

## 📊 Features

- ✅ Responsive design
- ✅ SEO optimized
- ✅ Fast loading
- ✅ Search functionality
- ✅ Social sharing
- ✅ Comment system ready
- ✅ Analytics ready
- ✅ Multi-language support
- ✅ Dark/light mode

## 🔧 Configuration

Key configuration files:

- `config/_default/hugo.toml` - Main Hugo configuration
- `config/_default/params.toml` - Theme-specific parameters
- `config/_default/languages.en.toml` - Site title, description, author info
- `config/_default/menus.en.toml` - Navigation menu structure

## 📱 Social Media & Analytics

The theme supports various analytics and social media platforms. Configure them in `config/_default/params.toml`:

- Google Analytics
- Plausible Analytics
- Umami Analytics
- Social media links
- Comment systems (Disqus, Giscus, etc.)

## 🚀 Deployment

### Netlify Continuous Deployment (Recommended)

This blog is configured for seamless continuous deployment on Netlify using the official Hugo documentation best practices.

#### 🔧 Pre-configured Setup

The repository includes optimized Netlify configuration:

- **`netlify.toml`** - Build settings and environment variables
- **`static/_redirects`** - URL redirection rules
- **`static/_headers`** - Security headers for enhanced protection

#### 📋 Netlify Deployment Steps

##### Step 1: Create Netlify Account
Sign up at [netlify.com](https://netlify.com) if you don't have an account.

##### Step 2: Import Repository
1. Log in to Netlify dashboard
2. Click "Add new site" → "Import an existing project"
3. Select GitHub as your Git provider
4. Authorize Netlify to access your GitHub account
5. Choose the `fintech-blog` repository

##### Step 3: Configure Build Settings
Netlify will automatically detect the configuration from `netlify.toml`:

```toml
[build]
  publish = "public"
  command = "git config core.quotepath false && hugo --gc --minify"

[build.environment]
  GO_VERSION = "1.24.2"
  HUGO_VERSION = "0.148.0"
  NODE_VERSION = "22"
  TZ = "UTC"
  HUGO_ENV = "production"
  HUGO_ENABLEGITINFO = "true"
```

##### Step 4: Deploy Site
1. Click "Deploy site"
2. Wait for the initial build (2-3 minutes)
3. Your site will be live at `https://[random-name].netlify.app`

#### 🔄 Continuous Deployment Workflow

Once configured, deployment is automatic:

1. **Make Changes**: Edit content, configuration, or code
2. **Commit & Push**: 
   ```bash
   git add .
   git commit -m "Add new blog post about [topic]"
   git push origin main
   ```
3. **Automatic Build**: Netlify detects changes and builds automatically
4. **Live Update**: Site updates within 1-2 minutes

#### 🔍 Build Process Details

Netlify executes the following optimized build process:

1. **Environment Setup**: Installs Hugo 0.148.0, Go 1.24.2, Node.js 22
2. **Git Configuration**: Sets `core.quotepath false` for proper character handling
3. **Module Download**: Downloads Hugo modules and dependencies
4. **Site Build**: Runs `hugo --gc --minify` for optimized output
5. **Deployment**: Publishes the `public/` directory to Netlify's global CDN

#### 🛡️ Security & Performance Features

**Security Headers** (configured in `static/_headers`):
- `X-Frame-Options: DENY`
- `X-XSS-Protection: 1; mode=block`
- `X-Content-Type-Options: nosniff`
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Content-Security-Policy` with strict rules
- `Strict-Transport-Security` for HTTPS enforcement

**Performance Optimizations**:
- Automatic minification with `--minify`
- Garbage collection with `--gc`
- Global CDN distribution
- Automatic image optimization
- Gzip compression

#### 🔧 Advanced Configuration

**Deploy Contexts** (automatically handled):
- **Production**: `main` branch → Live site
- **Deploy Previews**: Pull requests → Preview URLs
- **Branch Deploys**: Feature branches → Branch-specific URLs

**Custom Domain Setup**:
1. Go to Netlify dashboard → Site settings → Domain management
2. Add custom domain
3. Configure DNS records as instructed
4. SSL certificate is automatically provisioned

#### 🚨 Troubleshooting

**Build Failures**:
1. Check Netlify deploy logs in dashboard
2. Verify Hugo modules: `hugo mod get -u`
3. Test local build: `hugo --gc --minify`
4. Ensure `baseURL = "/"` in `config/_default/hugo.toml`

**Common Issues**:
- **Module errors**: Run `hugo mod tidy` locally and commit
- **Build timeouts**: Check for infinite loops in templates
- **Missing content**: Verify file paths and front matter syntax
- **Asset loading**: Ensure relative URLs in templates

#### 📊 Deployment Status

- ✅ **Netlify Configuration**: Optimized with official Hugo best practices
- ✅ **Environment Variables**: Hugo 0.148.0, Go 1.24.2, Node.js 22
- ✅ **Build Commands**: `git config core.quotepath false && hugo --gc --minify`
- ✅ **Security Headers**: Comprehensive protection enabled
- ✅ **Performance**: Minification and garbage collection active
- ✅ **SSL/HTTPS**: Automatic certificate provisioning
- ✅ **Global CDN**: Fast worldwide content delivery

### Alternative Deployment Options

While Netlify is recommended, the site can also be deployed to:

- **Vercel** - Import project for instant deployments
- **GitHub Pages** - Use GitHub Actions for automated builds
- **AWS S3** - Static site hosting with CloudFront CDN
- **Firebase Hosting** - Google's static hosting platform

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For questions or support, please open an issue in the repository or contact us at hello@fintechinsights.com.

---

Built with ❤️ using [Hugo](https://gohugo.io/) and the [Congo theme](https://github.com/jpanther/congo).
