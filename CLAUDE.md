# CLAUDE.md

## Project Overview

Personal academic portfolio for Carlos M. Ortiz Marrero, built with [Astro](https://astro.build) v5.

**Site**: https://cmortiz.github.io
**Deploy**: GitHub Pages via GitHub Actions on push to `master`

## Tech Stack

- **Framework**: Astro
- **TypeScript**: Strict mode (`astro/tsconfigs/strict`)
- **Styling**: Global CSS (`src/styles/global.css`)
- **Theme**: Gruvbox Dark (CSS custom properties in `:root`)
- **Font**: Fira Code (monospace everywhere, loaded from Google Fonts)
- **Deployment**: GitHub Pages (via GitHub Actions)

## Project Structure

```
/
├── public/              # Static assets (images, PDFs, favicons)
│   └── img/             # Image assets
├── src/
│   ├── components/      # Reusable Astro components
│   │   ├── Card.astro
│   │   ├── Footer.astro
│   │   └── Header.astro
│   ├── data/            # JSON data files
│   │   ├── articles.json
│   │   └── projects.json
│   ├── layouts/         # Page layouts
│   │   ├── BaseLayout.astro
│   │   └── BlogPost.astro
│   ├── pages/           # Route pages
│   │   ├── index.md
│   │   ├── articles.astro
│   │   └── projects.astro
│   └── styles/          # Global styles
│       └── global.css
├── .github/workflows/   # CI/CD configuration
│   └── deploy.yml
├── astro.config.mjs     # Astro configuration
├── package.json
└── tsconfig.json
```

## Key Files

- **Data Sources**: Articles and projects are defined in `src/data/articles.json` and `src/data/projects.json`
- **Base Layout**: `src/layouts/BaseLayout.astro` provides the HTML structure for all pages
- **Deployment**: `.github/workflows/deploy.yml` handles automatic deployment to GitHub Pages
- **Theming**: `src/styles/global.css` defines Gruvbox Dark color palette as CSS custom properties

## Adding Content

**New article**: Add an entry to `src/data/articles.json`. Required fields: `title`, `authors`, `venue`, `image`, `category`, `links`. Categories: `"Quantum Computation and Quantum Information"` or `"Data Science and Machine Learning"`.

**New project**: Add an entry to `src/data/projects.json`. Required fields: `title`, `role`, `image`, `links`.

**Static assets**: Place images, PDFs, and videos in `public/img/`. They are served from `/img/` at the root URL.

## Development Commands

```bash
bun install          # Install dependencies
bun run dev          # Start development server
bun run build        # Build for production
bun run preview      # Preview production build
```

## Conventions

- Pages use `.astro` or `.md` extensions in `src/pages/`
- Components are stored in `src/components/` as `.astro` files
- Static assets go in `public/` and are served from the root URL
- Data is stored as JSON in `src/data/`
- Use Gruvbox CSS variables (e.g., `var(--primary)`, `var(--accent-green)`) for colors; never hardcode hex values or introduce new color tokens
- Card component accepts: `title`, `subtitle?`, `details?`, `image?`, `links?`, `index?`
- **No client-side JavaScript**: Keep the site purely static Astro; no JS frameworks or runtime scripts
- **Do not modify** the Card component structure or grid layout without explicit approval
- Data-only changes (adding articles/projects) can be pushed directly; layout or style changes should be previewed locally first with `bun run dev`
