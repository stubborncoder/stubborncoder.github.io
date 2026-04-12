# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Personal portfolio and blog for David Díaz (stubborncoder) — freelance AI engineer with SAP Finance background. Static Astro site deployed to GitHub Pages at stubborncoder.github.io.

## Commands

- `npm run dev` — Start dev server (default port 4321)
- `npm run build` — Build static site to `dist/`
- `npm run preview` — Preview production build locally
- Push to `main` triggers GitHub Actions deploy to GitHub Pages

## Architecture

**Pages are standalone .astro files**, not content collections. Blog posts live in `src/pages/blog/` as individual `.astro` files — each post is hand-crafted with its own hero image, layout sections, and resource links.

**Single layout** (`src/layouts/BaseLayout.astro`) wraps every page: loads fonts (Google Fonts: Iosevka + Libre Baskerville), global CSS, Nav, Footer, ThemeToggle, and the scroll-reveal IntersectionObserver script.

**Theme system**: Dark/light toggle via `data-theme` attribute on `<html>`. Default is **light**. Preference persists in `localStorage`. The `ThemeToggle` component runs an inline script (before paint) to avoid flash of wrong theme.

## Design System — "Terminal Ember"

All styling flows from CSS custom properties in `src/styles/global.css`. Key tokens:

- **Accent colors**: `--ember` (primary orange), `--gold` (secondary/hover), `--ash` (muted teal)
- **Surfaces**: `--bg`, `--bg-raised`, `--bg-card` (three-tier depth)
- **Typography**: Iosevka (monospace body), Libre Baskerville (serif for headings and article prose)
- **Logo**: `~/stubborncoder` — the `~/` uses `--ember`, rest uses `--text-hi`

Do not introduce new colors or fonts without explicit approval. The site's palette is intentionally aligned with the user's AI agent dashboards.

## Blog Post Pattern

Each post page follows a consistent structure:
1. **Hero section** with blurred background image (`filter: blur(8px)`), gradient overlay fading to solid, back-link, meta (date, read time, source badges), title with `.em` span for ember-colored emphasis, subtitle, tags
2. **Article body** at `max-width: 720px` — uses Libre Baskerville for prose, with styled `blockquote`, `code`, comparison cards, takeaway boxes
3. **Resource links** — LinkedIn, SAP Community, and GitHub links in the article footer
4. **"More writing" section** — cross-links to other posts

Hero background images are loaded from Unsplash URLs with `w=1920&q=80` parameters. Each post uses a different image.

## Landing Page Structure

- Hero: left side has headline + bio + links; right side has a Mac-style terminal window with typing cursor animation
- Section 01 "Writing": list of blog post links with date and source
- Section 02 "Projects": project cards with tags and GitHub/external links
- Writing comes before Projects (intentional ordering)

## Key Conventions

- Blog post pages duplicate shared CSS (hero, article, footer styles) in component `<style>` blocks rather than using shared stylesheets — this is the current pattern, maintain it for consistency
- Theme-aware selectors for child components use `:global([data-theme="light"])` in scoped styles
- Scroll-reveal uses `.reveal` class + IntersectionObserver in BaseLayout
- External links (LinkedIn, SAP Community, GitHub) open in new tabs with `target="_blank"`
