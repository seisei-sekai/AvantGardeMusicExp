# Deployment Guide

This guide will help you deploy Benny Zhang's personal website to GitHub Pages or other hosting platforms.

## Table of Contents
- [GitHub Pages Deployment (Recommended)](#github-pages-deployment)
- [Local Testing](#local-testing)
- [Alternative Hosting Options](#alternative-hosting-options)
- [Custom Domain Setup](#custom-domain-setup)
- [Troubleshooting](#troubleshooting)

---

## GitHub Pages Deployment

### Prerequisites
- GitHub account
- Git installed on your computer
- This repository downloaded/cloned

### Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com) and log in
2. Click the **"+"** icon in the top right corner
3. Select **"New repository"**
4. Name your repository (e.g., `bennyzhang-website` or `Aesthetics`)
5. Set visibility to **Public** (required for free GitHub Pages)
6. **DO NOT** initialize with README, .gitignore, or license (we already have these)
7. Click **"Create repository"**

### Step 2: Push to GitHub

Open your terminal and navigate to this directory:

```bash
cd /Users/benz/Desktop/Stanford/SP26/Github/Aesthetics
```

Initialize and push (if not already done):

```bash
# Check current status
git status

# Add all files
git add .

# Commit the files
git commit -m "Initial commit: Complete website mirror from shichengzhang.web.illinois.edu"

# Add your GitHub repository as remote (replace with your actual URL)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **"Settings"** tab (near the top right)
3. Scroll down to **"Pages"** in the left sidebar
4. Under **"Build and deployment"**:
   - **Source:** Select "Deploy from a branch"
   - **Branch:** Select `main` (or `master`)
   - **Folder:** Select `/ (root)`
5. Click **"Save"**

### Step 4: Wait for Deployment

- GitHub will build and deploy your site (usually takes 1-5 minutes)
- You'll see a green checkmark when it's ready
- Your site will be available at: `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

### Step 5: Verify Deployment

Visit your site URL and check:
- ✅ Homepage loads correctly
- ✅ Navigation links work
- ✅ Images display properly
- ✅ CSS styling is applied
- ✅ Projects pages load
- ✅ Music pages load
- ✅ CV PDF downloads

---

## Local Testing

Before deploying, test the website locally:

### Option 1: Python HTTP Server (Recommended)

**Python 3:**
```bash
cd /Users/benz/Desktop/Stanford/SP26/Github/Aesthetics
python3 -m http.server 8000
```

**Python 2:**
```bash
cd /Users/benz/Desktop/Stanford/SP26/Github/Aesthetics
python -m SimpleHTTPServer 8000
```

Then open: `http://localhost:8000`

### Option 2: Node.js HTTP Server

If you have Node.js installed:

```bash
# Install http-server globally (one time)
npm install -g http-server

# Navigate to directory and serve
cd /Users/benz/Desktop/Stanford/SP26/Github/Aesthetics
http-server
```

Then open: `http://localhost:8080`

### Option 3: PHP Built-in Server

If you have PHP installed:

```bash
cd /Users/benz/Desktop/Stanford/SP26/Github/Aesthetics
php -S localhost:8000
```

Then open: `http://localhost:8000`

### Option 4: VS Code Live Server Extension

1. Install "Live Server" extension in VS Code
2. Open the Aesthetics folder in VS Code
3. Right-click on `index.html`
4. Select "Open with Live Server"

---

## Alternative Hosting Options

### Netlify

1. Go to [netlify.com](https://www.netlify.com/)
2. Sign up / Log in (can use GitHub account)
3. Click "Add new site" > "Deploy manually"
4. Drag and drop the entire `Aesthetics` folder
5. Your site will be live in seconds at a random URL
6. Optional: Customize the URL in site settings

**Advantages:**
- Faster deployment
- Free custom domains
- Automatic HTTPS
- Better performance

### Vercel

1. Go to [vercel.com](https://vercel.com/)
2. Sign up / Log in with GitHub
3. Click "Add New" > "Project"
4. Import your GitHub repository
5. Click "Deploy"

**Advantages:**
- Excellent performance
- Automatic deployments on git push
- Free SSL certificates

### GitHub User Pages (Special Setup)

For a URL like `https://YOUR-USERNAME.github.io/`:

1. Create a repository named exactly: `YOUR-USERNAME.github.io`
2. Push website files to root of this repository
3. Site will automatically be available at `https://YOUR-USERNAME.github.io/`
4. No additional configuration needed

---

## Custom Domain Setup

### GitHub Pages with Custom Domain

1. Purchase a domain from a registrar (Namecheap, GoDaddy, etc.)
2. In your repository: Settings > Pages > Custom domain
3. Enter your domain (e.g., `bennyzhang.com`)
4. Add DNS records at your domain registrar:

**For apex domain (bennyzhang.com):**
```
Type: A
Name: @
Value: 185.199.108.153
Value: 185.199.109.153
Value: 185.199.110.153
Value: 185.199.111.153
```

**For www subdomain:**
```
Type: CNAME
Name: www
Value: YOUR-USERNAME.github.io
```

5. Check "Enforce HTTPS" in GitHub Pages settings
6. Wait 24-48 hours for DNS propagation

---

## Troubleshooting

### Issue: 404 Page Not Found

**Cause:** GitHub Pages is looking for files in wrong location

**Solution:**
- Ensure `index.html` is in the root directory
- Check that you selected `/ (root)` folder in GitHub Pages settings
- Verify branch name is correct (`main` or `master`)

### Issue: CSS/Images Not Loading

**Cause:** Relative paths may need adjustment

**Solution:**
1. Check browser console for errors (F12)
2. Verify files exist in `wp-content` directories
3. If using subdirectory deployment, may need to update base paths

### Issue: Links Not Working

**Cause:** Some links use WordPress query parameters

**Solution:**
- Links should work as-is with downloaded structure
- If issues persist, consider creating redirect rules or updating links

### Issue: Slow Loading

**Cause:** Large image files

**Solution:**
```bash
# Install imagemagick for image optimization
brew install imagemagick  # macOS

# Compress images (run in Aesthetics directory)
find wp-content/uploads -name "*.jpg" -exec mogrify -quality 85 {} \;
find wp-content/uploads -name "*.png" -exec mogrify -quality 85 {} \;
```

### Issue: Music Files Not Playing

**Cause:** MP3 files may not be served with correct MIME type

**Solution:**
- GitHub Pages should handle this automatically
- For other hosts, ensure MP3 files have `audio/mpeg` MIME type
- Consider converting to OGG for better browser support

---

## Performance Optimization

### Enable Caching

Create a `_headers` file (for Netlify) or `.htaccess` (for Apache):

**Netlify (_headers):**
```
/*
  Cache-Control: public, max-age=3600
  
/wp-content/*
  Cache-Control: public, max-age=31536000
```

**Apache (.htaccess):**
```apache
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType text/css "access plus 1 year"
  ExpiresByType application/javascript "access plus 1 year"
</IfModule>
```

### Image Optimization

Consider using these tools:
- [TinyPNG](https://tinypng.com/) - Online compression
- [ImageOptim](https://imageoptim.com/) - macOS app
- [Squoosh](https://squoosh.app/) - Browser-based

### CDN Setup

For faster global delivery:
1. Use Cloudflare (free tier available)
2. Add your domain to Cloudflare
3. Update nameservers
4. Enable caching and optimization features

---

## Updating the Website

To update content after initial deployment:

```bash
# Make your changes to files

# Stage changes
git add .

# Commit with descriptive message
git commit -m "Update: Description of changes"

# Push to GitHub
git push origin main
```

GitHub Pages will automatically rebuild and deploy in 1-5 minutes.

---

## Security Considerations

1. **No Sensitive Data:** Ensure no passwords or API keys are in the repository
2. **Public Repository:** All code is visible, don't include private information
3. **HTTPS:** Always enable "Enforce HTTPS" in GitHub Pages settings
4. **Regular Updates:** Keep documentation current with any changes

---

## Monitoring & Analytics

### Add Google Analytics

1. Get your Google Analytics tracking ID
2. Edit `index.html` and other pages
3. Update the tracking ID in the analytics script section
4. The pages already have Google Analytics code, just update the ID

### GitHub Insights

- View traffic in: Repository > Insights > Traffic
- See visitor statistics and popular pages
- Track git clones and repository views

---

## Support Resources

- **GitHub Pages Documentation:** https://docs.github.com/en/pages
- **Netlify Docs:** https://docs.netlify.com/
- **Vercel Docs:** https://vercel.com/docs
- **HTML/CSS Help:** https://developer.mozilla.org/

---

## Summary Checklist

- [ ] Repository created on GitHub
- [ ] All files committed and pushed
- [ ] GitHub Pages enabled in settings
- [ ] Website accessible at GitHub Pages URL
- [ ] All pages load correctly
- [ ] Images and CSS working
- [ ] Links navigate properly
- [ ] CV PDF downloads successfully
- [ ] (Optional) Custom domain configured
- [ ] (Optional) HTTPS enforced
- [ ] (Optional) Analytics added

---

**Questions or Issues?**

Refer to the main [README.md](README.md) for additional information or consult the [SITEMAP.md](SITEMAP.md) for site structure details.

**Good luck with your deployment! 🚀**

