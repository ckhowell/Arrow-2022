# Arrow Executive Sales - Jekyll Site Project Context

## Project Overview

This is a **Jekyll-based static website** for Arrow Executive Sales, a B2B sales consulting firm specializing in sales recruitment, training, and enablement. The site is built on the **Silicon Bootstrap 5 Template** by Createx Studio.

**Primary Technologies:**
- **Framework**: Jekyll 4.2.x (static site generator)
- **CSS Framework**: Bootstrap 5.3.x
- **Build Tools**: Gulp, Sass, Rollup, PostCSS
- **JavaScript**: Vanilla ES6+ modules
- **UI Libraries**: Boxicons, Swiper, lightGallery, noUiSlider
- **Hosting**: Likely Netlify/Vercel or traditional web hosting

**Site**: https://arrowexec.com.au

---

## Project Structure

```
/
├── _includes/                 # Reusable HTML partials (117+ includes)
│   ├── nav.html
│   ├── footer.html
│   ├── hero.html
│   ├── testimonials.html
│   └── ... (various components)
├── _layouts/                  # Jekyll layout templates
│   ├── default.html          # Base layout
│   ├── home.html             # Homepage layout
│   ├── post.html             # Blog post layout
│   ├── recruit.html          # Recruitment page layout
│   └── training-lp.html      # Training landing page
├── _pages/                    # Additional pages (32 pages)
│   ├── about-recruit.html
│   ├── articles.html
│   ├── contact.html
│   ├── sales-training.html
│   └── ...
├── _posts/                    # Blog posts (23 Markdown files)
│   └── YY-MM-DD-slug.md
├── _site/                     # Generated Jekyll output
├── assets/
│   ├── css/                   # Compiled CSS
│   ├── js/                    # Compiled JavaScript
│   ├── vendor/                # Third-party libraries
│   ├── img/                   # Images (organized by category)
│   ├── favicon/               # Favicon files
│   └── scss/                  # Source SCSS files
├── src/
│   ├── js/                    # Source JavaScript
│   │   ├── theme.js          # Main theme entry point
│   │   └── components/       # JS modules
│   └── scss/                  # Source SCSS
│       ├── theme.scss        # Main stylesheet
│       ├── _variables.scss   # Bootstrap overrides
│       ├── _components.scss  # Custom components
│       └── ...
├── build/                     # Build scripts
│   ├── styles.js             # SCSS compilation
│   ├── scripts.js            # JS bundling
│   ├── vendor.js             # Vendor dependencies
│   └── config.js             # Build configuration
├── _config.yml               # Jekyll configuration
├── package.json              # Node.js dependencies
├── Gemfile                   # Ruby/Jekyll dependencies
└── QWEN.md
```

---

## Building and Running

### Development

```bash
# Install Node.js dependencies
npm install

# Install Ruby dependencies
bundle install

# Start development server with hot reload
npm run dev
# This runs: npm-run-all styles scripts vendor && watch mode

# Jekyll serve (alternative)
bundle exec jekyll serve
```

### Production Build

```bash
# Build production site to ./_site/
npm run build
# This runs: styles, scripts, vendor, validate, then jekyll build

# Or using Jekyll directly
bundle exec jekyll build
```

### Build Scripts Breakdown

| Script | Description |
|--------|-------------|
| `npm run styles` | Compile SCSS → CSS, then minify |
| `npm run scripts` | Bundle JS with Rollup, then minify |
| `npm run vendor` | Copy vendor dependencies to assets |
| `npm run validate` | HTML validation with html-validate |
| `npm run watch` | Watch for file changes |

---

## Design System

### Bootstrap 5 Foundation

Built on Bootstrap 5.3.x with custom overrides in:
- `src/scss/_variables.scss` - Bootstrap variable overrides
- `src/scss/_variables-dark.scss` - Dark mode color scheme
- `src/scss/_user-variables.scss` - Custom variables
- `src/scss/_user.scss` - Custom styles

### Custom SCSS Architecture

```scss
// src/scss/theme.scss (main entry)
@import 'variables';
@import 'variables-dark';
@import 'user-variables';
@import 'bootstrap';
@import 'reboot';
@import 'root';
@import 'components';
@import 'user';
@import 'utilities';
```

### Key Dependencies

**JavaScript Libraries:**
- `swiper` ^11.2.6 - Carousels/sliders
- `lightgallery` ^2.8.3 - Image galleries
- `boxicons` ^2.1.4 - Icon library
- `nouislider` ^15.8.1 - Range sliders
- `smooth-scroll` ^16.1.3 - Smooth scrolling
- `jarallax` ^2.2.1 - Parallax effects
- `shufflejs` ^6.1.1 - Grid filtering/sorting
- `prismjs` ^1.30.0 - Code highlighting
- `cleave.js` ^1.6.0 - Input formatting

**Lottie Animations:**
- `@lottiefiles/lottie-player` ^2.0.12

---

## Jekyll Configuration

### _config.yml

```yaml
title: Arrow Executive Sales
email: hello@arrowexec.com.au
phone: 1300 903 527
url: https://arrowexec.com.au
google_analytics: UA-165678042-1

permalink: /articles/:title/

plugins:
  - jekyll-feed

include:
  - _pages
  - _redirects
```

### Front Matter Templates

**Blog Posts** (`_posts/*.md`):
```markdown
---
layout: post
title: Proven Programs to Drive New Business Opportunities
author: Jason Howes
author-contact: mailto:jason@arrowexec.com.au
avatar: assets/img/avatar/jason-howes-avatar.png
image: /assets/img/articles/onboarding.png
category: Sales
include_video: false
---
```

**Pages** (`_pages/*.html`):
```html
---
layout: home
title: Arrow Executive Sales | B2B Sales Consulting
description: Need B2B sales consulting...
nav: bg-light sm-shadow
logo: logo.svg
---

{% include hero.html %}
{% include challenges.html %}
...
```

---

## Development Conventions

### File Naming

- **Includes**: kebab-case (`sales-recruitment.html`)
- **Pages**: kebab-case (`sales-training.html`)
- **Layouts**: lowercase with hyphens (`training-lp.html`)
- **Blog posts**: `YY-MM-DD-slug.md`
- **SCSS partials**: underscore prefix (`_components.scss`)

### Include Patterns

Reusable components included via Liquid:

```liquid
{% include hero.html %}
{% include testimonials.html %}
{% include cta.html %}
```

### Layout Usage

```liquid
---
layout: default
---

{{ content }}
```

### Image Organization

```
assets/img/
├── articles/       # Blog post images
├── avatar/         # Author avatars
├── book/           # Book-related images
├── icons/          # Custom icons
├── partners/       # Client logos
├── services/       # Service illustrations
├── team/           # Team photos
├── training/       # Training images
└── ...
```

---

## Key Architectural Patterns

### Component-Based Includes

117+ reusable includes organized by function:

**Navigation & Layout:**
- `nav.html`, `footer.html`, `head.html`
- `page-title.html`, `breadcrumb.html`

**Hero Sections:**
- `hero.html`, `hero-diy.html`

**Content Blocks:**
- `about-tabs.html`, `accordian.html`, `features-text-recruit.html`
- `recruitment-cards.html`, `services-grid.html`

**Calls-to-Action:**
- `cta.html`, `cta_find-a-job.html`, `exit-intent-modal.html`

**Social Proof:**
- `testimonials.html`, `testimonials-recruitment.html`, `partners.html`

### JavaScript Module System

ES6 modules bundled with Rollup:

```javascript
// src/js/theme.js
import 'bootstrap/dist/js/bootstrap.bundle'
import 'smooth-scroll/dist/smooth-scroll.polyfills'
import './components/sticky-navbar'
import './components/carousel'
import './components/form-validation'
// ... more components
```

### Build Pipeline

1. **SCSS**: Sass compilation → PostCSS (autoprefixer) → cssnano (minify)
2. **JavaScript**: Rollup bundling → Terser (minify)
3. **Vendor**: Copy node_modules to assets/vendor
4. **Jekyll**: Process Liquid templates → static HTML
5. **Validate**: HTML validation with html-validate

---

## Content Management

### Blog Posts

23 blog posts in `_posts/` covering:
- Sales effectiveness
- Recruitment strategies
- Sales training
- Onboarding
- Market conditions

### Landing Pages

Multiple landing page variants for A/B testing:
- `recruitment-lp.html`, `recruitment-lp-chatgpt.html`
- `training-lp.html`
- Multiple `landing-*.html` test variants

### Static Assets

PDFs and downloadable resources:
- `ARROW_SALES_COMPENSATION_GUIDE.pdf`
- `Sample_Sales_Insights.pdf`

---

## Build Configuration

### build/config.js

```javascript
const config = {
  path: {
    html: ['./'],
    scss: 'src/scss',
    src_js: 'src/js',
    js: 'assets/js',
    css: 'assets/css',
    vendor: 'assets/vendor',
  },
  fileNames: {
    css: 'theme',
    js: 'theme',
  },
}
```

### Stylelint Configuration

SCSS linting via `.stylelintrc.json` with:
- `stylelint-config-standard`
- `stylelint-config-twbs-bootstrap`

### Prettier & ESLint

Code formatting and JavaScript linting:
- `.prettierrc`, `.prettierrc`
- `eslint.config.js`

---

## SEO & Performance

- **Google Analytics**: UA-165678042-1
- **Favicon**: Complete set in `assets/favicon/`
- **Open Graph**: `og.html` include for social sharing
- **Structured Data**: `structured_data.html` for schema.org
- **Page Loading**: Spinner animation during page load
- **Asset Optimization**: Minified CSS/JS in production

---

## Special Features

### Page Loading Animation

Custom loading spinner with fade-out transition:

```html
<div class="page-loading active">
  <div class="page-loading-inner">
    <div class="page-spinner"></div>
    <span>Loading...</span>
  </div>
</div>
```

### Exit Intent Modal

Lead capture modal triggered on exit intent (`exit-intent-modal.html`).

### Video Integration

- Lottie animations for lightweight vector animations
- lightGallery for video lightboxes
- Jarallax for video backgrounds

### Form Validation

Bootstrap 5 form validation with custom JavaScript handlers.

---

## Common Tasks

### Adding a New Page

1. Create file in `_pages/page-name.html`
2. Add front matter with layout, title, description
3. Include relevant components via `{% include %}`
4. Add to navigation if needed

### Adding a Blog Post

1. Create `_posts/YY-MM-DD-slug.md`
2. Add front matter (layout: post, title, author, image, category)
3. Write Markdown content
4. Add featured image to `assets/img/articles/`

### Adding a New Include

1. Create `_includes/component-name.html`
2. Use Liquid templating for dynamic content
3. Include in pages/layouts as needed

### Updating Styles

1. Modify `src/scss/_user.scss` for custom styles
2. Update `src/scss/_variables.scss` for Bootstrap overrides
3. Run `npm run styles` or `npm run dev`

### Adding JavaScript

1. Add to `src/js/components/` as module
2. Import in `src/js/theme.js`
3. Run `npm run scripts` or `npm run dev`

---

## Dependencies Summary

### Node.js (package.json)

**Dev Dependencies:**
- `sass` ^1.80.3 - SCSS compilation
- `rollup` ^4.24.0 - JavaScript bundling
- `browser-sync` ^3.0.3 - Live reload
- `stylelint` ^16.21.1 - SCSS linting
- `eslint` ^9.13.0 - JavaScript linting
- `prettier` ^3.3.3 - Code formatting
- `html-validate` ^8.24.2 - HTML validation
- `autoprefixer`, `postcss`, `cssnano` - CSS processing

**Runtime Dependencies:**
- `bootstrap` ^5.3.6
- `boxicons` ^2.1.4
- `swiper` ^11.2.6
- `lightgallery` ^2.8.3
- Plus 12+ UI libraries

### Ruby (Gemfile)

- `jekyll` ~4.2.2
- `jekyll-feed` ~0.12
- `jekyll-paginate`
- `webrick` ~1.8 (development server)

---

## Notes

- **Template Base**: Silicon v1.7.0 by Createx Studio
- **Australian Business**: Content tailored for Australian B2B sales market
- **Multi-Purpose**: Supports recruitment, training, and consulting content
- **A/B Testing**: Multiple landing page variants for testing
- **Legacy Code**: Some files may reference older build tools (Gulp) alongside modern npm scripts
- **Docker Support**: Includes `Dockerfile` and `docker-compose.yml` for containerized development
