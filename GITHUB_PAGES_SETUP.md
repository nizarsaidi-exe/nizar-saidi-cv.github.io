# GitHub Pages Deployment Guide

## Prerequisites
- GitHub account
- Git installed on your machine
- Domain name (optional - you can use GitHub Pages default domain)

## Setup Instructions

### 1. Push to GitHub
```bash
# Initialize git if not already done
git init
git add .
git commit -m "Initial commit - Portfolio website"

# Create a new repository on GitHub named: YOUR_USERNAME.github.io
# Then add the remote and push
git remote add origin https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io.git
git branch -M main
git push -u origin main
```

### 2. Update CNAME File
Edit `/public/CNAME` and replace `yourdomain.com` with your actual domain name:
```
yourdomain.com
```

### 3. Build and Deploy
```bash
# Build the project
npm run build

# Deploy to GitHub Pages
npm run deploy
```

### 4. Configure GitHub Pages Settings
1. Go to your repository on GitHub
2. Go to **Settings** → **Pages**
3. Under "Source", select **gh-pages** branch
4. Under "Custom domain", enter your domain name (e.g., yourdomain.com)
5. Check "Enforce HTTPS" (GitHub provides free SSL/HTTPS)

### 5. Configure DNS (for custom domain)
If using a custom domain, update your domain registrar DNS settings:

**Option A: Using CNAME record (recommended)**
- Add a CNAME record pointing to: `YOUR_USERNAME.github.io`

**Option B: Using A records**
- Add these A records pointing to GitHub's IP addresses:
  - 185.199.108.153
  - 185.199.109.153
  - 185.199.110.153
  - 185.199.111.153

### 6. Security & Best Practices
✅ HTTPS is automatically enabled by GitHub Pages
✅ The CNAME file ensures proper domain routing
✅ Run `npm audit fix` periodically to address vulnerabilities
✅ Keep dependencies updated: `npm update`

## Troubleshooting

**Domain not working after setup?**
- Wait 10-15 minutes for DNS propagation
- Check GitHub Pages settings show your domain

**HTTPS not appearing?**
- Go to Settings → Pages
- Uncheck and recheck "Enforce HTTPS"
- Wait a few minutes for SSL certificate to be issued

**Build errors?**
- Run `npm run build` locally to check for errors
- Ensure all dependencies are installed: `npm install`

## Remaining Vulnerabilities

There are 3 moderate vulnerabilities related to esbuild (used by Vite). These are non-critical development dependencies that don't affect your production build. To resolve:

```bash
npm audit fix --force  # (WARNING: may introduce breaking changes)
```

Or update when major versions are released. The site will still work securely.

## Next Steps
1. Update CNAME with your domain
2. Push all changes to GitHub
3. Run: `npm run deploy`
4. Configure GitHub Pages settings
5. Update your DNS records (if using custom domain)
