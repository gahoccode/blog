---
description: Continuous deployment on Netlify
---

# FinTech Insights Blog Deployment on Netlify

This workflow explains how to deploy the FinTech Insights Hugo blog to Netlify for continuous deployment.

## 🚀 Automatic Deployment

The blog uses Netlify for automatic deployment. Every push to the `main` branch triggers a new deployment.

### Steps for Initial Netlify Setup:

1. **Create a Netlify account** at [netlify.com](https://netlify.com) if you don't have one
2. **Connect your GitHub repository**:
   - Go to Netlify dashboard → "Add new site" → "Import an existing project"
   - Select GitHub and authenticate
   - Choose the `fintech-blog` repository
3. **Configure build settings**:
   - Build command: `hugo --minify`
   - Publish directory: `public`
   - Advanced build settings → New variable:
     - Key: `HUGO_VERSION`
     - Value: `0.110.0`
4. **Deploy your site**:
   - Click "Deploy site"
   - Wait for the initial build to complete

### Continuous Deployment Workflow:

1. **Make your changes** to content, configuration, or code
2. **Commit and push** to the main branch:
   ```bash
   git add .
   git commit -m "Your descriptive commit message"
   git push origin main
   ```
3. **Netlify automatically**:
   - Detects changes in the repository
   - Builds the Hugo site with the configuration in `netlify.toml`
   - Deploys to your Netlify domain
   - Runs any post-processing (minification, image optimization)

## 🔧 Manual Deployment

If you need to trigger a manual deployment:

1. **Go to Netlify dashboard**:
   - Select your site
   - Navigate to "Deploys" tab
   - Click "Trigger deploy" → "Deploy site"

## 📋 Deployment Checklist

- [ ] Repository connected to Netlify
- [ ] Build settings properly configured
- [ ] `netlify.toml` file in repository root
- [ ] `_redirects` and `_headers` files in static directory
- [ ] Site builds successfully
- [ ] Custom domain configured (if applicable)
- [ ] HTTPS enabled
- [ ] Site loads correctly on Netlify URL

## 🔍 Troubleshooting

**If deployment fails**:
1. Check Netlify deploy logs in dashboard
2. Verify Hugo modules are up to date: `hugo mod get -u`
3. Test local build: `hugo --minify`
4. Check baseURL in `config/_default/hugo.toml` (should be `/`)

**Common Issues**:
- Module download failures → Run `hugo mod tidy`
- Build errors → Check Hugo version compatibility
- Missing content → Verify file paths and front matter
- CSS/JS not loading → Check for absolute URLs in templates
