# SuwandiNotes.com Deployment Guide

## Current Setup

### Site Framework
- **Framework**: Hugo (v0.145.0 extended)
- **Theme**: hugo-xmin (customized)
- **Content**: Markdown files in the `content/` directory
- **Custom Layouts**: In the `layouts/` directory
- **Custom CSS**: In the `static/css/` directory

### Repository Structure
- **GitHub Repository**: https://github.com/weeargh/suwandinotes
- **Branch**: main

### Customizations
1. **Typography**:
   - Body text: Inter (sans-serif)
   - Headings, titles, and footer: Lora (serif)
   - Custom CSS file: `static/css/custom.css`

2. **Layout Customizations**:
   - Custom header with improved alignment: `layouts/partials/header.html`
   - Featured post with yellow background: `layouts/_default/list.html`

3. **Build Configuration**:
   - Default publish directory: `public/` (standard Hugo output)

## Netlify Deployment

### Netlify Configuration
The site is configured for Netlify deployment using a `netlify.toml` file at the root of the repository:

```toml
[build]
  command = "hugo"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.145.0"  # Extended version matching local
  HUGO_EXTENDED = "true"
```

This configuration tells Netlify to:
- Use the `hugo` command to build the site
- Publish the `public` directory
- Use Hugo version 0.145.0 (extended version)

### Deployment Process

1. **Local Development**:
   - Make changes to content, layouts, or styles
   - Test locally using `hugo server -D`
   - Build the site using `hugo`

2. **Deployment**:
   - Commit changes to the repository:
     ```
     git add .
     git commit -m "Description of changes"
     ```
   - Push to GitHub:
     ```
     git push origin main
     ```
   - Netlify automatically detects the push and triggers a new build
   - The site is deployed to your Netlify domain (suwandinotes.netlify.app)

3. **Monitoring Deployment**:
   - Check the Netlify dashboard for build status and logs
   - If needed, trigger a manual deployment from the Netlify dashboard

### Troubleshooting

If deployment fails, check:
1. Netlify build logs for specific errors
2. Ensure the `netlify.toml` configuration is correct
3. Verify that the Hugo version in `netlify.toml` matches your local version
4. Make sure all theme files are properly included in the repository

## Local Development Workflow

1. Start the Hugo development server:
   ```
   hugo server -D
   ```

2. View the site at http://localhost:1313/

3. Make changes to content, layouts, or styles

4. The browser will automatically refresh to show changes

5. When satisfied, build the site:
   ```
   hugo
   ```

6. Commit and push changes to deploy

## Important Notes

- The site uses a custom domain configuration in Netlify
- Custom fonts are loaded from Google Fonts
- The theme files are directly included in the repository (not as a Git submodule)
- Environment variables are configured in the Netlify dashboard
