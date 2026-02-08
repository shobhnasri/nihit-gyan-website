# Technical Specification - Nihit Gyan Advisory Website

**Project**: Nihit Gyan Advisory Website  
**Date**: February 8, 2026  
**Status**: Ready for Development (Phase 2)

---

## Project Overview

Building a professional advisory website for Nihit Gyan Advisory, a technology consulting firm focused on engineering leadership, platform scaling, and team transformation for startups and scale-ups.

**Website**: nihitgyan.co.uk (primary), nihitgyan.co.in (redirect)  
**Structure**: Hybrid - Single-page scroll with future expansion for blog/case studies  
**Target Launch**: February 28, 2026

---

## Tech Stack

### Hosting & Deployment
- **Platform**: Vercel (free tier)
- **Domain**: nihitgyan.co.uk (already owned)
- **DNS**: Configure to point to Vercel
- **SSL**: Automatic via Vercel

### Frontend
- **Framework**: HTML/CSS/JavaScript (static site) OR Next.js/React (if preferred)
- **Styling**: CSS with design system
- **Responsive**: Mobile-first approach
- **Browser Support**: Last 2 versions of Chrome, Firefox, Safari, Edge

### Integrations
- **Booking**: Calendly (embed iframe)
- **Forms**: Formspree or Web3Forms (Vercel has no built-in forms)
- **Analytics**: Google Analytics or Plausible

### Performance Targets
- **Lighthouse Score**: 90+ (all categories)
- **First Contentful Paint**: < 1.5s
- **Time to Interactive**: < 3.5s
- **Cumulative Layout Shift**: < 0.1

---

## Design System

### Colors
```css
/* Primary (from logo) */
--color-primary: #FF5722; /* Orange */
--color-primary-dark: #E64A19;
--color-primary-light: #FF8A65;

/* Secondary */
--color-secondary: #263238; /* Dark navy/charcoal */
--color-secondary-light: #37474F;

/* Neutrals */
--color-gray-50: #FAFAFA;
--color-gray-100: #F5F5F5;
--color-gray-200: #EEEEEE;
--color-gray-600: #757575;
--color-gray-900: #212121;

/* Semantic */
--color-bg: #FFFFFF;
--color-text: #212121;
--color-text-secondary: #757575;
```

### Typography
```css
/* Font Stack */
--font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;

/* Scale */
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px */
--text-3xl: 1.875rem;  /* 30px */
--text-4xl: 2.25rem;   /* 36px */
--text-5xl: 3rem;      /* 48px */

/* Weights */
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

### Spacing
```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-24: 6rem;     /* 96px */
```

### Breakpoints
```css
/* Mobile first */
--bp-sm: 640px;   /* Small devices */
--bp-md: 768px;   /* Tablets */
--bp-lg: 1024px;  /* Desktops */
--bp-xl: 1280px;  /* Large desktops */
```

---

## Site Structure

### Pages (Phase 1 - Single Page Scroll)
- **/** (Home) - All content on one page with smooth scroll navigation
  - Hero
  - Challenge (3 pain points)
  - Solution (intro + 3 differentiators)
  - Services (4 services)
  - About
  - Process
  - Contact

### Future Pages (Phase 4)
- **/case-studies/** - Individual case study pages
- **/blog/** - Blog posts
- **/resources/** - Downloadable resources

---

## Component Structure

### Hero Section
- Full-height or 80vh
- Headline: "Transform Your Engineering Team. Scale Your Platform. Deliver Results That Last."
- Subheadline
- Primary CTA button (Book Discovery Call → Calendly)
- Trust indicators (20+ years, metrics, company logos)

### Challenge Section
- 3 cards/columns (responsive to single column on mobile)
- Card 1: Team Performance, Alignment & Scale
- Card 2: Platform Scaling & Architecture
- Card 3: Modern Tech Without the Hype

### Solution Section
- Introduction paragraph
- 3 differentiators (cards or simple layout):
  - The Rare Balance
  - The Partnership Approach
  - Changes That Last

### Services Section
- 4 service cards with:
  - Title
  - "What It Is"
  - "When You Need It" (collapsible/expandable?)
  - "How I Help" (collapsible/expandable?)
  - "Expected Outcomes" (collapsible/expandable?)
- Consider accordion or expand/collapse for mobile

### About Section
- Personal intro
- "Why Nihit Gyan" explanation
- 4 philosophy points (cards or list)
- Career highlights (timeline or cards)
- Education credentials

### Process Section
- 4 steps visualization
- Step 1: Discovery Call (30 min, free)
- Step 2: Scoping & Proposal
- Step 3: Engagement & Collaboration
- Step 4: Outcomes & Iteration

### Contact Section
- Prominent CTA: "Book Your Free Discovery Call"
- Value prop bullets (what you get)
- Calendly embed or link
- Alternative contact: Email, LinkedIn

### Navigation
- Sticky header on scroll (optional)
- Links: Home | About | Services | Contact
- Logo in header (clickable to top)
- Mobile: Hamburger menu

### Footer
- Company name + tagline
- Service list (links to sections)
- Contact info (email, LinkedIn)
- Copyright

---

## Assets

### Logo Files
**Location**: `/home/shobhna/Documents/Claude/projects/nihit-gyan/Logo Files/`

**For Website Use**:
- `svg/Color logo - no background.svg` (primary - light backgrounds)
- `svg/White logo - no background.svg` (dark sections)
- `Favicons/browser.png` (favicon)

**Sizes Needed**:
- Header logo: max-height 40-50px
- Footer logo: max-height 30px
- Favicon: 32x32, 64x64

### Content
**Location**: `/home/shobhna/Documents/Claude/projects/nihit-gyan/content/homepage-draft-v1.md`

All website copy is complete and approved.

### Images Needed
- Professional headshot of Shobhna (optional but recommended)
- Abstract/metaphorical imagery (optional):
  - Team collaboration
  - Architecture/platforms
  - Growth/scaling concepts
- Can use free stock from Unsplash if needed

---

## Integrations

### Calendly
- **Account**: Created and configured
- **Event**: "30-Minute Discovery Call"
- **Calendars Connected**: 3 Google Calendars (checks for conflicts)
- **Implementation**: Embed iframe or popup link
- **Booking Link**: [To be provided by Shobhna]

Example embed:
```html
<div class="calendly-inline-widget" 
     data-url="https://calendly.com/[username]/discovery-call" 
     style="min-width:320px;height:700px;">
</div>
<script type="text/javascript" src="https://assets.calendly.com/assets/external/widget.js" async></script>
```

### Contact Form (Alternative/Backup)
- **Service**: Formspree or Web3Forms
- **Fields**: Name, Email, Company (optional), Message
- **Action**: Email to shobhna.s@proton.me
- **Validation**: Client-side + server-side

### Analytics
- **Service**: Google Analytics (or Plausible for privacy-focused)
- **Events to Track**:
  - Discovery call booking clicks
  - Email link clicks
  - Service section views
  - Contact form submissions

---

## Development Setup

### Project Structure
```
nihit-gyan-website/
├── public/
│   ├── images/
│   │   ├── logo-color.svg
│   │   ├── logo-white.svg
│   │   └── favicon.png
│   └── ...
├── src/
│   ├── styles/
│   │   ├── reset.css
│   │   ├── design-system.css
│   │   └── main.css
│   ├── scripts/
│   │   └── main.js
│   └── index.html
├── .gitignore
├── package.json (if using build tools)
├── vercel.json (config)
└── README.md
```

### Git Repository
- Initialize git in project root
- Push to GitHub (private or public)
- Connect to Vercel for automatic deployments

### Environment Variables (if needed)
```
NEXT_PUBLIC_CALENDLY_URL=https://calendly.com/[username]/discovery-call
NEXT_PUBLIC_GA_ID=G-XXXXXXXXXX
FORM_ENDPOINT=https://formspree.io/f/[form-id]
```

---

## Accessibility Requirements

### WCAG 2.1 Level AA Compliance
- Semantic HTML5 elements
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text for all images
- Color contrast ratio ≥ 4.5:1 for text
- Keyboard navigation support
- Focus indicators visible
- ARIA labels where needed
- Skip to main content link

### Testing
- Test with screen reader (NVDA or VoiceOver)
- Test keyboard-only navigation
- Run Lighthouse accessibility audit
- Check color contrast with tools

---

## SEO Requirements

### Meta Tags
```html
<!-- Primary -->
<title>Nihit Gyan Advisory | Engineering Leadership & Platform Scaling</title>
<meta name="description" content="Transform your engineering team, scale your platform, and deliver results that last. Expert advisory for tech startups and scale-ups.">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://nihitgyan.co.uk/">
<meta property="og:title" content="Nihit Gyan Advisory | Engineering Leadership & Platform Scaling">
<meta property="og:description" content="Transform your engineering team, scale your platform, and deliver results that last.">
<meta property="og:image" content="https://nihitgyan.co.uk/images/og-image.png">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:url" content="https://nihitgyan.co.uk/">
<meta name="twitter:title" content="Nihit Gyan Advisory | Engineering Leadership & Platform Scaling">
<meta name="twitter:description" content="Transform your engineering team, scale your platform, and deliver results that last.">
<meta name="twitter:image" content="https://nihitgyan.co.uk/images/twitter-image.png">
```

### Structured Data (Schema.org)
```json
{
  "@context": "https://schema.org",
  "@type": "ProfessionalService",
  "name": "Nihit Gyan Advisory",
  "description": "Engineering leadership and platform scaling advisory for tech startups and scale-ups",
  "url": "https://nihitgyan.co.uk",
  "telephone": "+44-7999-590194",
  "email": "shobhna.s@proton.me",
  "founder": {
    "@type": "Person",
    "name": "Shobhna Srivastava",
    "jobTitle": "Founder & Engineering Advisor"
  }
}
```

### Sitemap & Robots
- Generate sitemap.xml
- Create robots.txt
- Submit to Google Search Console and Bing Webmaster Tools

---

## Performance Optimization

### Images
- Use WebP format with PNG/JPG fallbacks
- Lazy load below-the-fold images
- Optimize all images (compress, resize)
- Serve responsive images (srcset)

### CSS
- Inline critical CSS for above-the-fold
- Defer non-critical CSS
- Minify CSS for production

### JavaScript
- Minimize JS usage (prefer CSS animations)
- Defer non-critical JS
- Minify and bundle JS

### Fonts
- Use system font stack (no custom fonts = faster)
- OR load 1-2 weights max of single font family
- Use font-display: swap

### Caching
- Set appropriate cache headers via Vercel
- Use service worker for offline support (optional)

---

## Testing Checklist

### Browser Testing
- [ ] Chrome (desktop)
- [ ] Firefox (desktop)
- [ ] Safari (desktop)
- [ ] Edge (desktop)
- [ ] Safari (iOS mobile)
- [ ] Chrome (Android mobile)

### Device Testing
- [ ] Desktop (1920x1080, 1440x900)
- [ ] Laptop (1366x768)
- [ ] Tablet (iPad, 768x1024)
- [ ] Mobile (iPhone 12/13, 390x844)
- [ ] Mobile (Samsung Galaxy, 360x800)

### Functionality Testing
- [ ] Navigation links work
- [ ] Smooth scroll to sections
- [ ] Calendly embed loads and works
- [ ] Contact form submits successfully
- [ ] Email links open mail client
- [ ] LinkedIn link opens in new tab
- [ ] All images load correctly
- [ ] Logo displays on all backgrounds
- [ ] Mobile menu works

### Performance Testing
- [ ] Lighthouse score 90+ (all categories)
- [ ] Page load < 2 seconds
- [ ] No layout shifts
- [ ] Smooth animations

### Accessibility Testing
- [ ] Screen reader navigation
- [ ] Keyboard-only navigation
- [ ] Color contrast passes
- [ ] Focus indicators visible
- [ ] Alt text present

---

## Deployment

### Vercel Setup
1. Connect GitHub repository to Vercel
2. Configure project settings:
   - Framework: Next.js or Static HTML
   - Build command: (if needed)
   - Output directory: `public` or `dist`
3. Add environment variables (if any)
4. Configure custom domain: nihitgyan.co.uk
5. Set up domain redirect: nihitgyan.co.in → nihitgyan.co.uk

### Domain Configuration
1. In domain registrar (where nihitgyan.co.uk is registered):
   - Add A record: @ → 76.76.21.21 (Vercel)
   - Add CNAME record: www → cname.vercel-dns.com
2. For nihitgyan.co.in:
   - Add 301 redirect to nihitgyan.co.uk

### Pre-Launch Checklist
- [ ] All content proofread
- [ ] All links tested
- [ ] Calendly link correct
- [ ] Analytics tracking code added
- [ ] Favicon displays correctly
- [ ] SSL certificate active
- [ ] Meta tags correct
- [ ] Sitemap generated
- [ ] robots.txt configured

---

## Maintenance & Updates

### Regular Updates
- Security patches (if using framework)
- Content updates (future blog posts, case studies)
- Dependency updates (quarterly)

### Monitoring
- Analytics review (weekly)
- Uptime monitoring (Vercel provides)
- Performance monitoring (Lighthouse monthly)
- Broken link checks (quarterly)

---

## Notes for Developer

### Key Considerations
1. **Content is final** - All copy in `content/homepage-draft-v1.md` is approved
2. **Mobile-first** - Start with mobile layout, scale up
3. **Performance critical** - Site must load fast, target Lighthouse 90+
4. **Accessibility critical** - Must be keyboard and screen-reader friendly
5. **Simple is better** - Don't over-engineer, clean and fast
6. **One minor tweak** - "The Rare Balance" differentiator may need small revision later

### Development Priorities
1. Set up project structure and design system
2. Build Hero section (most important, sets tone)
3. Build Challenge and Solution sections
4. Build Services section (most complex)
5. Build About, Process, Contact
6. Add navigation and footer
7. Integrate Calendly
8. Polish animations and interactions
9. Test thoroughly
10. Deploy

### Questions to Resolve
- [ ] Calendly booking link (Shobhna to provide)
- [ ] LinkedIn profile URL (Shobhna to provide)
- [ ] Professional headshot available? (optional)
- [ ] Preference on contact form service? (Formspree vs Web3Forms)
- [ ] Preference on analytics? (Google Analytics vs Plausible)

---

**Ready for development!**

**Next Steps**: 
1. Set up local development environment
2. Initialize git repository
3. Create basic project structure
4. Build design system
5. Start with Hero section

---

**Last Updated**: February 8, 2026
