# Nihit Gyan Advisory Website

Professional advisory website for Nihit Gyan Advisory, providing consulting services in strategic planning, business development, and organizational growth.

## Project Overview

This is a modern, static website built with a focus on performance, accessibility, and user experience. The site showcases advisory services, client testimonials, and provides easy contact options for potential clients.

## Tech Stack

- **HTML5**: Semantic markup for content structure
- **CSS3**: Modern styling with custom properties and responsive design
- **JavaScript**: Vanilla JS for interactive components and form handling
- **Vercel**: Deployment platform with edge network CDN
- **Git**: Version control

## Project Structure

```
nihit-gyan/
├── public/
│   ├── images/
│   │   ├── logos/      # Company logos and branding
│   │   └── icons/      # UI icons and graphics
│   └── fonts/          # Custom web fonts
├── src/
│   ├── styles/         # CSS stylesheets
│   └── scripts/        # JavaScript files
├── index.html          # Main landing page
├── vercel.json         # Vercel configuration
├── .gitignore          # Git ignore rules
└── README.md           # This file
```

## Development Instructions

### Prerequisites

- Git installed on your machine
- A modern web browser (Chrome, Firefox, Safari, Edge)
- Text editor or IDE (VS Code recommended)
- Node.js (optional, for local dev server)

### Getting Started

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd nihit-gyan
   ```

2. **Open the project**
   - Simply open `index.html` in your browser for basic viewing
   - Or use a local development server for better development experience

3. **Using a local dev server** (optional but recommended)
   ```bash
   # Using Python 3
   python -m http.server 8000

   # Using Node.js
   npx serve

   # Using PHP
   php -S localhost:8000
   ```

4. **Make changes**
   - Edit HTML files in the root directory
   - Modify styles in `src/styles/`
   - Update scripts in `src/scripts/`
   - Add images to `public/images/`

### Development Workflow

1. Create a new branch for your feature/fix
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. Make your changes and test locally

3. Commit your changes
   ```bash
   git add .
   git commit -m "type: description"
   ```

4. Push to remote
   ```bash
   git push origin feature/your-feature-name
   ```

## Deployment

### Vercel Deployment

This site is configured for deployment on Vercel with optimized settings for performance and security.

#### Initial Setup

1. Install Vercel CLI (optional)
   ```bash
   npm i -g vercel
   ```

2. Deploy to Vercel
   ```bash
   vercel
   ```

#### Automatic Deployments

- **Production**: Automatic deployment on push to `main` branch
- **Preview**: Automatic preview deployments for all branches

#### Configuration

The `vercel.json` file includes:
- Security headers (X-Content-Type-Options, X-Frame-Options, X-XSS-Protection)
- Caching strategies for static assets
- Routing rules and redirects

### Manual Deployment

1. Build the project (if using build tools)
2. Upload to your hosting provider
3. Configure web server settings for optimal caching

## Performance Targets

The site is optimized to meet the following performance benchmarks:

- **Lighthouse Performance Score**: 90+
- **First Contentful Paint (FCP)**: < 1.5s
- **Largest Contentful Paint (LCP)**: < 2.5s
- **Time to Interactive (TTI)**: < 3.5s
- **Cumulative Layout Shift (CLS)**: < 0.1
- **First Input Delay (FID)**: < 100ms

### Performance Optimization Strategies

- Minified CSS and JavaScript
- Optimized and compressed images (WebP format where supported)
- Lazy loading for images below the fold
- Critical CSS inlining
- Browser caching via Cache-Control headers
- CDN delivery through Vercel's edge network
- Preconnect to external domains
- Font display optimization

## Browser Support

- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes with clear messages
4. Push to the branch
5. Create a Pull Request

## Commit Message Convention

Follow the conventional commits specification:

- `feat:` New features
- `fix:` Bug fixes
- `docs:` Documentation changes
- `style:` Code style changes (formatting, etc.)
- `refactor:` Code refactoring
- `perf:` Performance improvements
- `test:` Adding or updating tests
- `chore:` Maintenance tasks

## License

All rights reserved. This project is proprietary software for Nihit Gyan Advisory.

## Contact

For questions or support, please contact Nihit Gyan Advisory.
