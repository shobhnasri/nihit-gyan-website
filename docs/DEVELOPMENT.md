# Development Guide

Comprehensive documentation for developing and maintaining the Nihit Gyan Advisory website.

## Table of Contents

- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Design System](#design-system)
- [Adding New Sections](#adding-new-sections)
- [Testing](#testing)
- [Deployment](#deployment)
- [Common Tasks](#common-tasks)
- [Performance Best Practices](#performance-best-practices)
- [Troubleshooting](#troubleshooting)
- [Git Workflow](#git-workflow)
- [Resources](#resources)

---

## Quick Start

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, or Edge)
- Text editor (VS Code, Sublime Text, etc.)
- Git for version control

### Local Development

#### Option 1: Python Server (Recommended)

```bash
# Navigate to project directory
cd /path/to/nihit-gyan

# Start Python 3 server
python3 -m http.server 8000

# Open in browser
# Visit: http://localhost:8000
```

#### Option 2: Node.js Server

```bash
# Install http-server globally (one-time setup)
npm install -g http-server

# Navigate to project directory
cd /path/to/nihit-gyan

# Start server
http-server -p 8000

# Open in browser
# Visit: http://localhost:8000
```

#### Option 3: VS Code Live Server

1. Install "Live Server" extension in VS Code
2. Right-click on `index.html`
3. Select "Open with Live Server"

### File Editing

1. Make changes to HTML, CSS, or JavaScript files
2. Save the file
3. Refresh browser to see changes (or auto-reload with Live Server)

---

## Project Structure

```
nihit-gyan/
├── index.html                  # Main entry point
├── README.md                   # Project overview
├── vercel.json                 # Vercel deployment configuration
├── .gitignore                  # Git ignore rules
│
├── src/                        # Source files
│   ├── styles/                 # CSS files
│   │   ├── main.css           # Main stylesheet (imports all others)
│   │   ├── design-system.css  # CSS custom properties (variables)
│   │   ├── reset.css          # Browser reset styles
│   │   ├── base.css           # Base HTML element styles
│   │   └── components/        # Component-specific styles
│   │       ├── buttons.css    # Button styles
│   │       ├── cards.css      # Card component styles
│   │       ├── navigation.css # Header and nav styles
│   │       └── footer.css     # Footer styles
│   │
│   └── scripts/               # JavaScript files
│       └── main.js            # Main JavaScript file
│
├── public/                    # Static assets
│   └── images/               # Images
│       ├── logos/            # Logo files (SVG, PNG)
│       └── icons/            # Favicon and icons
│
├── docs/                     # Documentation
│   ├── DEVELOPMENT.md        # This file
│   └── plans/                # Project planning documents
│
└── content/                  # Content files and status
    ├── CONTENT_STATUS.md     # Content implementation tracking
    └── REVIEW_SUMMARY.md     # Content review notes
```

### Key Files Explained

**index.html**
- Main HTML entry point
- Contains semantic HTML5 structure
- Includes meta tags for SEO and social sharing
- Links to stylesheets and scripts

**src/styles/main.css**
- Imports all other CSS files in correct order
- Only file that needs to be linked in HTML

**src/styles/design-system.css**
- Defines all CSS custom properties (variables)
- Contains color palette, typography, spacing, shadows
- Single source of truth for design tokens

**vercel.json**
- Deployment configuration for Vercel
- Sets up security headers
- Configures cache policies
- Defines URL rewrites

---

## Design System

### CSS Custom Properties

All design tokens are defined in `src/styles/design-system.css` as CSS custom properties.

#### Colors

```css
/* Primary Colors (Orange from logo) */
--color-primary: #FF5722;
--color-primary-dark: #E64A19;
--color-primary-light: #FF7043;

/* Secondary Colors (Charcoal) */
--color-secondary: #263238;
--color-secondary-light: #37474F;

/* Neutral Colors */
--color-white: #FFFFFF;
--color-gray-50: #F9FAFB;
--color-gray-100: #F3F4F6;
--color-gray-200: #E5E7EB;
/* ... more grays ... */
--color-gray-900: #111827;
--color-black: #000000;

/* Semantic Colors */
--color-success: #10B981;
--color-warning: #F59E0B;
--color-error: #EF4444;
--color-info: #3B82F6;
```

#### Typography

```css
/* Font Family */
--font-sans: -apple-system, BlinkMacSystemFont, 'Segoe UI', ...;

/* Font Sizes (responsive) */
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px - scales up on larger screens */
--text-3xl: 1.875rem;  /* 30px - scales up on larger screens */
--text-4xl: 2.25rem;   /* 36px - scales up on larger screens */
--text-5xl: 3rem;      /* 48px - scales up on larger screens */

/* Font Weights */
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;

/* Line Heights */
--leading-tight: 1.25;
--leading-normal: 1.5;
--leading-relaxed: 1.75;
```

#### Spacing System (4px base)

```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-5: 1.25rem;   /* 20px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-10: 2.5rem;   /* 40px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-20: 5rem;     /* 80px */
--space-24: 6rem;     /* 96px */
```

#### Shadows

```css
--shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
--shadow-base: 0 1px 3px 0 rgba(0, 0, 0, 0.1), ...;
--shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1), ...;
--shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), ...;
--shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1), ...;
```

#### Border Radius

```css
--radius-sm: 0.125rem;   /* 2px */
--radius-base: 0.25rem;  /* 4px */
--radius-md: 0.375rem;   /* 6px */
--radius-lg: 0.5rem;     /* 8px */
--radius-xl: 0.75rem;    /* 12px */
--radius-2xl: 1rem;      /* 16px */
--radius-full: 9999px;   /* Fully rounded */
```

#### Transitions

```css
--transition-fast: 150ms ease-in-out;
--transition-base: 250ms ease-in-out;
--transition-slow: 350ms ease-in-out;
```

#### Z-Index Scale

```css
--z-base: 0;
--z-dropdown: 1000;
--z-sticky: 1100;
--z-fixed: 1200;
--z-modal-backdrop: 1300;
--z-modal: 1400;
--z-popover: 1500;
--z-tooltip: 1600;
```

### Component Classes

#### Buttons

```html
<!-- Primary Button -->
<button class="btn btn-primary">Click Me</button>

<!-- Secondary Button -->
<button class="btn btn-secondary">Learn More</button>

<!-- Button Sizes -->
<button class="btn btn-primary btn-lg">Large Button</button>
<button class="btn btn-primary btn-sm">Small Button</button>

<!-- Full Width Button -->
<button class="btn btn-primary btn-block">Full Width</button>
```

#### Cards

```html
<div class="card">
  <div class="card-body">
    <h3 class="card-title">Card Title</h3>
    <p class="card-text">Card content goes here.</p>
  </div>
</div>
```

---

## Adding New Sections

### Step-by-Step Guide

#### 1. Create HTML Structure

Add new section to `index.html`:

```html
<section id="new-section" class="section">
  <div class="container">
    <h2 class="section-title">Section Title</h2>
    <p class="section-description">Section description</p>

    <!-- Section content -->
  </div>
</section>
```

#### 2. Create Component Styles (if needed)

Create new CSS file in `src/styles/components/`:

```bash
# Create new component file
touch src/styles/components/new-component.css
```

```css
/* src/styles/components/new-component.css */
.new-component {
  /* Use design system variables */
  padding: var(--space-8);
  background: var(--color-gray-50);
  border-radius: var(--radius-lg);
}

.new-component__title {
  color: var(--color-secondary);
  font-size: var(--text-2xl);
  margin-bottom: var(--space-4);
}
```

#### 3. Import Component Styles

Add import to `src/styles/main.css`:

```css
/* Add after other component imports */
@import './components/new-component.css';
```

#### 4. Add Navigation Link

Update navigation in `index.html`:

```html
<ul class="nav-links" role="menubar">
  <li role="none"><a href="#about" role="menuitem">About</a></li>
  <li role="none"><a href="#services" role="menuitem">Services</a></li>
  <li role="none"><a href="#new-section" role="menuitem">New Section</a></li>
  <li role="none"><a href="#contact" role="menuitem">Contact</a></li>
</ul>
```

Don't forget to update mobile menu as well!

#### 5. Test Responsiveness

- Test on mobile (320px - 767px)
- Test on tablet (768px - 1023px)
- Test on desktop (1024px+)

---

## Testing

### Browser Testing Checklist

Test website in multiple browsers:

- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

### Responsive Testing Checklist

Test at different viewport sizes:

- [ ] Mobile Small: 320px width
- [ ] Mobile Medium: 375px width
- [ ] Mobile Large: 425px width
- [ ] Tablet: 768px width
- [ ] Laptop: 1024px width
- [ ] Desktop: 1440px width
- [ ] Large Desktop: 1920px width

#### Tools for Responsive Testing

- Chrome DevTools Device Mode (F12 → Toggle Device Toolbar)
- Firefox Responsive Design Mode (Ctrl+Shift+M)
- [Responsively App](https://responsively.app/) (Desktop app)
- [BrowserStack](https://www.browserstack.com/) (Real devices)

### Performance Testing Checklist

- [ ] Run Google Lighthouse audit (Aim for 90+ scores)
- [ ] Test page load time (Should be under 3 seconds)
- [ ] Check Total Blocking Time (Should be under 300ms)
- [ ] Verify images are optimized
- [ ] Check CSS is minified for production
- [ ] Verify JavaScript is minified for production

#### Running Lighthouse

1. Open Chrome DevTools (F12)
2. Go to "Lighthouse" tab
3. Select categories to test
4. Click "Generate report"

### Accessibility Testing Checklist

- [ ] All images have alt text
- [ ] Proper heading hierarchy (h1 → h2 → h3, no skipping)
- [ ] Sufficient color contrast (4.5:1 minimum)
- [ ] Keyboard navigation works (Tab, Enter, Space)
- [ ] Focus indicators visible
- [ ] Screen reader friendly (use NVDA or VoiceOver)
- [ ] ARIA labels on interactive elements
- [ ] Skip to main content link present

#### Tools for Accessibility Testing

- Chrome Lighthouse Accessibility Audit
- [axe DevTools](https://www.deque.com/axe/devtools/) browser extension
- [WAVE](https://wave.webaim.org/) browser extension
- NVDA screen reader (Windows)
- VoiceOver (macOS - Cmd+F5)

### Manual Testing Checklist

- [ ] Navigation links work correctly
- [ ] Smooth scroll to sections works
- [ ] Mobile menu opens/closes properly
- [ ] All buttons are clickable
- [ ] Forms validate correctly (when added)
- [ ] External links open in new tabs
- [ ] No console errors
- [ ] No 404 errors in Network tab

---

## Deployment

### Deploying to Vercel

#### First-Time Deployment

1. **Install Vercel CLI** (optional)
   ```bash
   npm install -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy from Command Line**
   ```bash
   cd /path/to/nihit-gyan
   vercel
   ```

   Follow prompts:
   - Link to existing project? No (first time)
   - Project name: nihit-gyan
   - Directory: ./
   - Override settings? No

4. **Or Deploy via GitHub**
   - Push code to GitHub repository
   - Go to [vercel.com](https://vercel.com)
   - Click "Import Project"
   - Import from GitHub
   - Select repository
   - Configure project (usually auto-detected)
   - Click "Deploy"

#### Subsequent Deployments

**Automatic deployment (if connected to GitHub):**
- Push to main branch
- Vercel automatically deploys

**Manual deployment:**
```bash
vercel --prod
```

#### Custom Domain Setup

1. Go to Vercel Dashboard
2. Select your project
3. Go to "Settings" → "Domains"
4. Add custom domain (e.g., nihitgyan.co.uk)
5. Configure DNS records:
   - Type: A
   - Name: @
   - Value: 76.76.19.19

   And:
   - Type: CNAME
   - Name: www
   - Value: cname.vercel-dns.com

6. Wait for DNS propagation (can take up to 48 hours)

#### Environment Variables (if needed)

If you need environment variables:

1. Go to Vercel Dashboard → Project Settings → Environment Variables
2. Add variables (e.g., API keys)
3. Redeploy to apply changes

---

## Common Tasks

### Update Brand Colors

1. Open `src/styles/design-system.css`
2. Update color variables:
   ```css
   :root {
     --color-primary: #NEW_COLOR;
     --color-primary-dark: #NEW_DARK_COLOR;
     --color-primary-light: #NEW_LIGHT_COLOR;
   }
   ```
3. Save and test across all components

### Add New Button Style

1. Open `src/styles/components/buttons.css`
2. Add new button variant:
   ```css
   .btn-tertiary {
     background-color: var(--color-gray-100);
     color: var(--color-secondary);
     border-color: var(--color-gray-300);
   }

   .btn-tertiary:hover {
     background-color: var(--color-gray-200);
     border-color: var(--color-gray-400);
   }
   ```

### Optimize Images

1. **Use appropriate format:**
   - SVG for logos and icons (scalable, small file size)
   - PNG for images with transparency
   - JPG for photos
   - WebP for modern browsers (with fallback)

2. **Compress images:**
   ```bash
   # Using ImageOptim (macOS)
   # Drag and drop images into app

   # Using TinyPNG (online)
   # Visit https://tinypng.com/
   ```

3. **Responsive images:**
   ```html
   <img
     src="/public/images/photo.jpg"
     srcset="/public/images/photo-320w.jpg 320w,
             /public/images/photo-640w.jpg 640w,
             /public/images/photo-1024w.jpg 1024w"
     sizes="(max-width: 640px) 100vw, 640px"
     alt="Description"
     loading="lazy"
   >
   ```

### Add Google Analytics

1. Get your Google Analytics tracking ID
2. Add to `index.html` before closing `</head>`:
   ```html
   <!-- Google Analytics -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'GA_TRACKING_ID');
   </script>
   ```

### Add Calendly Integration

Already preconnected in HTML. To add widget:

```html
<!-- Calendly inline widget -->
<div
  class="calendly-inline-widget"
  data-url="https://calendly.com/your-username/meeting"
  style="min-width:320px;height:630px;">
</div>
<script
  type="text/javascript"
  src="https://assets.calendly.com/assets/external/widget.js"
  async>
</script>
```

---

## Performance Best Practices

### CSS Optimization

1. **Use CSS variables for consistency**
   - Reduces duplication
   - Easier to maintain
   - Better compression

2. **Minimize CSS specificity**
   - Use classes, not IDs
   - Avoid deep nesting
   - Keep selectors simple

3. **Load critical CSS inline**
   ```html
   <style>
     /* Critical above-the-fold CSS */
   </style>
   <link rel="stylesheet" href="/src/styles/main.css">
   ```

### JavaScript Optimization

1. **Defer non-critical JavaScript**
   ```html
   <script src="/src/scripts/main.js" defer></script>
   ```

2. **Use async for independent scripts**
   ```html
   <script src="analytics.js" async></script>
   ```

3. **Minimize DOM manipulation**
   - Batch DOM updates
   - Use DocumentFragment
   - Cache DOM queries

### Image Optimization

1. **Use appropriate dimensions**
   - Don't serve 2000px images for 400px display
   - Create multiple sizes for srcset

2. **Lazy load images**
   ```html
   <img src="image.jpg" alt="Description" loading="lazy">
   ```

3. **Use modern formats**
   - WebP (with fallback)
   - AVIF (for very modern browsers)

### Loading Performance

1. **Preconnect to third-party domains**
   ```html
   <link rel="preconnect" href="https://example.com">
   ```

2. **Preload critical resources**
   ```html
   <link rel="preload" href="/fonts/main.woff2" as="font" type="font/woff2" crossorigin>
   ```

3. **Use CDN for static assets**
   - Vercel provides CDN automatically
   - Consider Cloudflare for additional optimization

---

## Troubleshooting

### Styles Not Loading

**Problem:** CSS changes not visible

**Solutions:**
1. Hard refresh browser (Ctrl+Shift+R or Cmd+Shift+R)
2. Clear browser cache
3. Check CSS file path in `index.html`
4. Check browser console for 404 errors
5. Verify CSS syntax (missing semicolons, brackets)

### Mobile Menu Not Working

**Problem:** Hamburger menu doesn't open/close

**Solutions:**
1. Check JavaScript is loaded (look for errors in console)
2. Verify `main.js` is linked correctly
3. Check mobile-menu-toggle button class name
4. Ensure event listeners are attached

### Images Not Displaying

**Problem:** Images show broken icon

**Solutions:**
1. Check image path (case-sensitive on Linux/macOS)
2. Verify image exists in `/public/images/` directory
3. Check file permissions (should be readable)
4. Verify image format is supported (SVG, PNG, JPG, WebP)
5. Look for errors in browser console Network tab

### Layout Issues on Mobile

**Problem:** Layout looks broken on mobile devices

**Solutions:**
1. Add viewport meta tag (should already exist)
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```
2. Check CSS media queries are correct
3. Test with Chrome DevTools mobile emulation
4. Remove fixed widths, use max-width instead
5. Check for overflow issues (overflow-x: hidden may help)

### Fonts Look Different Across Browsers

**Problem:** Inconsistent font rendering

**Solutions:**
1. Use system font stack (already implemented)
2. Add font smoothing:
   ```css
   body {
     -webkit-font-smoothing: antialiased;
     -moz-osx-font-smoothing: grayscale;
   }
   ```
3. Ensure font weights are available
4. Check font-family fallbacks are working

### Vercel Deployment Fails

**Problem:** Deployment errors on Vercel

**Solutions:**
1. Check `vercel.json` syntax (valid JSON)
2. Verify all referenced files exist
3. Check build logs in Vercel dashboard
4. Ensure no sensitive files in repository
5. Try deploying to preview first: `vercel`

### Performance Score Low

**Problem:** Lighthouse performance score below 90

**Solutions:**
1. Optimize images (compress, resize, use WebP)
2. Minimize CSS/JS (for production)
3. Remove unused CSS
4. Defer non-critical JavaScript
5. Add lazy loading to images
6. Enable compression on server (Vercel does automatically)
7. Reduce third-party scripts

---

## Git Workflow

### Commit Message Conventions

Follow conventional commits format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, whitespace)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**

```bash
# Feature
git commit -m "feat(services): add services section with cards"

# Bug fix
git commit -m "fix(nav): resolve mobile menu closing issue"

# Documentation
git commit -m "docs: update README with setup instructions"

# Style
git commit -m "style(footer): improve spacing and alignment"

# Refactor
git commit -m "refactor(css): consolidate duplicate styles"

# Performance
git commit -m "perf(images): optimize hero image size"
```

### Branch Strategy

**Main Branch:**
- Always production-ready
- All changes via pull requests (if team)

**Feature Branches:**
```bash
# Create feature branch
git checkout -b feature/service-cards

# Make changes, then commit
git add .
git commit -m "feat(services): add service cards component"

# Merge back to main
git checkout main
git merge feature/service-cards
```

**Hotfix Branches:**
```bash
# For urgent production fixes
git checkout -b hotfix/nav-link-fix
# Make fix
git commit -m "fix(nav): correct contact section link"
git checkout main
git merge hotfix/nav-link-fix
```

### Common Git Commands

```bash
# Check status
git status

# Stage changes
git add .                    # All files
git add index.html          # Specific file
git add src/styles/*.css    # Pattern match

# Commit changes
git commit -m "commit message"

# Push to remote
git push origin main

# Pull latest changes
git pull origin main

# View commit history
git log --oneline
git log --graph --oneline --all

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Discard changes in file
git checkout -- filename.html

# Create and switch to branch
git checkout -b branch-name

# Switch branches
git checkout main

# Delete branch
git branch -d branch-name
```

### .gitignore

Current `.gitignore` includes:

```
# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.sublime-*

# Dependencies
node_modules/

# Environment variables
.env
.env.local

# Build output
dist/
build/

# Logs
*.log
```

---

## Resources

### Documentation

- **MDN Web Docs:** https://developer.mozilla.org/
  - HTML, CSS, JavaScript reference
  - Best practices and tutorials

- **CSS-Tricks:** https://css-tricks.com/
  - CSS techniques and solutions
  - Browser compatibility information

- **Can I Use:** https://caniuse.com/
  - Browser support tables for web technologies

### Accessibility

- **WCAG Guidelines:** https://www.w3.org/WAI/WCAG21/quickref/
  - Web Content Accessibility Guidelines

- **WebAIM:** https://webaim.org/
  - Accessibility articles and tools
  - WAVE accessibility evaluation tool

- **A11y Project:** https://www.a11yproject.com/
  - Accessibility checklist
  - Resources and patterns

### Performance

- **Google Lighthouse:** https://developers.google.com/web/tools/lighthouse
  - Performance, accessibility, SEO audits

- **WebPageTest:** https://www.webpagetest.org/
  - Detailed performance testing

- **PageSpeed Insights:** https://pagespeed.web.dev/
  - Google's performance analysis tool

### Deployment

- **Vercel Documentation:** https://vercel.com/docs
  - Deployment guides
  - Custom domains
  - Environment variables

- **Vercel CLI Reference:** https://vercel.com/docs/cli
  - Command-line deployment

### Design Resources

- **Google Fonts:** https://fonts.google.com/
  - Free web fonts

- **Unsplash:** https://unsplash.com/
  - Free high-quality images

- **SVG Repo:** https://www.svgrepo.com/
  - Free SVG icons

### Tools

- **Chrome DevTools:** Built into Chrome browser
  - Element inspector
  - Network monitoring
  - Performance profiling

- **Firefox Developer Tools:** Built into Firefox browser
  - Responsive design mode
  - CSS Grid/Flexbox inspector

- **VS Code:** https://code.visualstudio.com/
  - Recommended extensions:
    - Live Server
    - ESLint
    - Prettier
    - CSS Peek

### Communities

- **Stack Overflow:** https://stackoverflow.com/
  - Q&A for programming questions

- **Dev.to:** https://dev.to/
  - Developer community and articles

- **CSS-Tricks Forums:** https://css-tricks.com/forums/
  - CSS-specific discussions

---

## Need Help?

If you encounter issues not covered in this guide:

1. Check browser console for errors
2. Review this documentation
3. Search for similar issues online
4. Check project issues on GitHub (if applicable)
5. Reach out to project maintainers

---

**Last Updated:** February 8, 2026

**Version:** 1.0.0

**Maintained by:** Nihit Gyan Advisory Development Team
