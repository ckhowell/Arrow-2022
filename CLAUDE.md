# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Jekyll static site for Arrow Executive Sales (arrowexec.com.au), built on the Silicon Bootstrap 5 template. B2B sales consulting firm — recruitment, training, enablement.

**Stack:** Jekyll 4.2, Bootstrap 5.3, SCSS/Sass, Rollup (JS bundler), PostCSS, Node build scripts.

## Commands

```bash
# Install dependencies (both required)
npm install
bundle install

# Development (compiles assets + starts file watcher)
npm run dev

# Production build → _site/
npm run build

# Lint SCSS only
npm run lint:scss
```

`npm run dev` does NOT start the Jekyll server — run `bundle exec jekyll serve` separately or rely on the watch task to rebuild files while Jekyll serves.

## Architecture

**Jekyll layer:**
- `_layouts/` — 9 layout templates (`default.html`, `home.html`, `post.html`, `recruit.html`, `training-lp.html`, etc.)
- `_includes/` — 117+ HTML partials composed via Liquid `{% include %}`
- `_pages/` — 32 static pages (HTML with front matter)
- `_posts/` — 23 blog posts as `YY-MM-DD-slug.md` → rendered at `/articles/:title/`
- `_config.yml` — Jekyll config (site URL, analytics, permalink pattern, plugins)

**Asset pipeline:**
- `src/scss/theme.scss` → compiled → `assets/css/theme.min.css`
- `src/js/theme.js` → bundled via Rollup → `assets/js/theme.min.js`
- `assets/vendor/` — copied from `node_modules` by `build/vendor.js`
- `build/` — Node scripts for styles (Sass → PostCSS → cssnano), scripts (ESLint → Rollup → Terser), and validation

**SCSS structure:**
- `src/scss/_variables.scss` — Bootstrap 5 variable overrides (colors, typography, spacing)
- `src/scss/_variables-dark.scss` — Dark mode palette
- `src/scss/_user-variables.scss` / `_user.scss` — Custom variables and styles (edit these for site-specific changes)
- `src/scss/components/` — 28 component partials

**JS structure:**
- `src/js/theme.js` — imports Bootstrap + 19 component modules
- `src/js/components/` — individual feature modules (carousel, gallery, sticky-navbar, parallax, etc.)

## Key Conventions

- **SCSS changes**: Edit `_user-variables.scss` for variable overrides, `_user.scss` for custom styles. Avoid editing Bootstrap or Silicon template partials directly.
- **New includes**: Add to `_includes/`, reference with `{% include filename.html %}` in layouts/pages.
- **Blog posts**: Filename format `YY-MM-DD-slug.md` in `_posts/`. Front matter requires `layout: post`.
- **Images**: Organized in `assets/img/` subdirectories by category (articles, avatars, services, team, etc.).
- **Compiled assets**: `assets/css/theme.min.css` and `assets/js/theme.min.js` are build outputs — edit source in `src/`, not compiled files.
- **Code style**: 2-space indent, no semicolons, single quotes (enforced by Prettier + ESLint).
