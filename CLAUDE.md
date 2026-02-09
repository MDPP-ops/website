# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **M-DPP** (Molecular-level Digital Product Passports) website — a research project focused on digital product passports for the textile industry and ESPR (EU Ecodesign for Sustainable Products Regulation) compliance. The site is hosted at **m-dpp.nl**.

## Tech Stack

- **Jekyll** static site generator with the **Minima** theme
- **Kramdown** markdown engine
- **Bootstrap 5.3.3** via CDN for layout/components
- **GitHub Pages** for hosting, deployed via GitHub Actions on push to `main`

## Development Commands

```bash
bundle install                    # Install dependencies
bundle exec jekyll serve          # Local dev server at http://localhost:4000
bundle exec jekyll build          # Build to _site/
```

There is no Gemfile checked in — the project relies on GitHub Pages' built-in Jekyll environment. No test suite exists.

## Architecture

**Layout chain:** `_layouts/default.html` → includes `_includes/header.html` (sticky Bootstrap navbar) and `_includes/footer.html`. All content pages use this single layout.

**Content pages** are Markdown files with YAML frontmatter in the root directory:
- `index.md` — Landing page (hero, value props, process, validation, CTA)
- `about.md` — ESPR regulatory context and project overview
- `work.md` — Work streams
- `output.md` — Publications/deliverables
- `contact.md` — Contact information

Navigation order is defined in `_config.yml` under `header_pages`.

**Styling:** `assets/css/site.css` contains the full design system — CSS custom properties define the color palette (primary blue `#1d4ed8`, accent teal `#0f766e`, scientific/software tone). Key component classes: `.soft-card`, `.icon-badge`, `.section-kicker`. Mobile breakpoint at 576px.

## Deployment

Automatic via `.github/workflows/jekyll-gh-pages.yml` — pushes to `main` trigger a Jekyll build and deploy to GitHub Pages. Custom domain configured via `CNAME` file (m-dpp.nl).
