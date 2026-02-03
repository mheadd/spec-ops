# Website Asset Generation

This document explains the tooling and workflow for generating raster image assets for the SpecOps website.

## Overview

The SpecOps website (`docs/index.html`) uses high-quality SVG source files for branding and social media assets. To maximize compatibility across browsers, social platforms, and devices, we generate PNG raster versions using a Node.js build script.

## Source Files

The following SVG files serve as the source of truth for all website graphics:

- `docs/favicon.svg` — Primary favicon with gradient branding
- `docs/safari-pinned-tab.svg` — Monochrome icon for Safari pinned tabs
- `docs/og-image.svg` — Social media share card (1200×630)

## Generated Assets

Running the build script produces the following PNG files:

| File | Dimensions | Purpose |
|------|------------|---------|
| `docs/favicon-16.png` | 16×16 | Browser tab icon (legacy) |
| `docs/favicon-32.png` | 32×32 | Browser tab icon (retina) |
| `docs/icon-180.png` | 180×180 | Apple touch icon (iOS home screen) |
| `docs/og-image.png` | 1200×630 | Open Graph / Twitter Card image |

## Prerequisites

- Node.js 16+ (includes npm)
- The `sharp` library (installed automatically via `npm install`)

## Building Assets & Styles

### First-time setup

```bash
npm install
```

This installs the `sharp` image processing library as a dev dependency.

### Generate PNG assets

```bash
npm run build:assets
```

This executes `scripts/gen-assets.js`, which:
1. Reads SVG source files from `docs/`
2. Rasterizes them at high density for crisp output
3. Applies maximum PNG compression (level 9)
4. Writes output files to `docs/`

**When to regenerate:**
- After editing any SVG source file
- When deploying the website to production
- Before committing changes that affect branding

### Minify CSS

The website's shared stylesheet lives at `docs/styles.css`. A minified version (`docs/styles.min.css`) is produced for production using [csso](https://github.com/css/csso).

Run:

```bash
npm run build:css
```

This executes `scripts/minify-css.js`, which:
1. Reads `docs/styles.css`
2. Minifies it with structural optimizations
3. Writes `docs/styles.min.css`
4. Reports original vs minified size

Both `docs/index.html` and `docs/faq.html` reference the minified file:

```html
<link rel="stylesheet" href="./styles.min.css">
```

### Combined Build

You can run both asset generation and CSS minification with a single command:

```bash
npm run build
```

This sequentially runs:
1. `build:assets` – raster icons & OG image
2. `build:css` – stylesheet minification

Include this in deployment workflows to ensure fresh artifacts.

## The Build Script

`scripts/gen-assets.js` uses the [sharp](https://sharp.pixelplumbing.com/) library to convert SVGs to PNGs. Key implementation details:

- **High-density rendering** — Uses 512 DPI for small icons to prevent blurriness
- **Progressive optimization** — Maximum compression for smaller file sizes
- **Automated directory creation** — Creates output directories if missing
- **Error handling** — Exits with code 1 on failure for CI/CD compatibility

## Integration with HTML & CSS

The generated PNG assets are referenced in `docs/index.html`:

```html
<!-- Multi-format favicon stack -->
<link rel="icon" type="image/svg+xml" href="./favicon.svg">
<link rel="icon" type="image/png" sizes="32x32" href="./favicon-32.png">
<link rel="icon" type="image/png" sizes="16x16" href="./favicon-16.png">

<!-- iOS home screen icon -->
<link rel="apple-touch-icon" sizes="180x180" href="./icon-180.png">

<!-- Social media preview -->
<meta property="og:image" content="./og-image.png">
<meta name="twitter:image" content="./og-image.png">
```

This approach provides:
- Modern browsers get crisp SVG favicons
- Legacy browsers fall back to PNG
- Social platforms always receive optimized raster images
- iOS devices get proper home screen icons

## Troubleshooting

**"Cannot find module 'sharp'"**
Run `npm install` to install dependencies.

**"Asset generation failed: ENOENT"**
Ensure all SVG source files exist in `docs/` before running the build script.

**Output images look blurry**
Check that the density parameter in `gen-assets.js` is set sufficiently high (currently 512 for favicons, 144 for OG image).

## Future Enhancements

Potential improvements to the asset pipeline:

- **Dark mode variant** — Generate alternate OG image for `prefers-color-scheme: dark`
- **ICO bundle** — Create multi-resolution `.ico` file for maximum legacy support
- **Automated optimization** — Add `oxipng` or `pngquant` for further size reduction
- **CI integration** — Run asset generation and CSS minification automatically on pre-commit / CI
- **CSS splitting** — Separate critical CSS, inline above-the-fold styles
- **PWA manifest** — Generate `manifest.json` with icon references for installability

## Blog

The website includes a blog section at `docs/blog/`. Posts are stored as individual HTML files in subdirectories.

### Blog Structure

```
docs/blog/
├── index.html              # Blog listing page (shows all posts)
└── posts/
    ├── welcome/
    │   └── index.html      # Individual post
    ├── my-next-post/
    │   └── index.html
    └── ...
```

### Creating a New Post

1. **Create a subdirectory** under `docs/blog/posts/` with a URL-friendly slug:

   ```bash
   mkdir docs/blog/posts/my-new-post
   ```

2. **Copy an existing post** as a template:

   ```bash
   cp docs/blog/posts/welcome/index.html docs/blog/posts/my-new-post/index.html
   ```

3. **Edit the new post** — Update these key elements:

   - `<title>` — Post title for browser tab
   - `<meta name="description">` — Brief summary for SEO
   - `<meta property="og:title">` and `<meta property="og:description">` — Social sharing
   - `<meta property="article:published_time">` — Publication date (YYYY-MM-DD)
   - `<h1>` in header — Post title displayed on page
   - `<time datetime="...">` — Human-readable date
   - `<article class="post-content">` — Your post content (supports h2, p, ul, ol, a, strong, em)

4. **Add to the listing page** — Edit `docs/blog/index.html` and add a new card at the **top** of the `.blog-grid` div (newest posts first):

   ```html
   <a href="./posts/my-new-post/" class="blog-card">
       <time datetime="2026-02-15">February 15, 2026</time>
       <h2>My New Post Title</h2>
       <p>A brief excerpt or summary of the post content.</p>
       <span class="read-more">Read more →</span>
   </a>
   ```

### Post Template Reference

Each post uses this basic structure:

- **Header** — Gradient background with post title and date
- **Toolbar** — Navigation links back to blog listing and home
- **Main content** — White card with article content
- **Footer** — Standard site footer

Posts support standard HTML elements within `.post-content`:
- Headings: `<h2>`
- Paragraphs: `<p>`
- Lists: `<ul>`, `<ol>`, `<li>`
- Links: `<a href="...">`
- Emphasis: `<strong>`, `<em>`

## Related Documentation

- [README.md](README.md) — Project overview and philosophy
- [CONTRIBUTING.md](CONTRIBUTING.md) — Contribution guidelines
- [package.json](package.json) — Build scripts and dependencies
