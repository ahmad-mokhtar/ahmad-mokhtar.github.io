# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Ahmad Mokhtar's academic homepage (https://ahmad-mokhtar.github.io), a Jekyll site built on an older version of the [al-folio](https://github.com/alshedivat/al-folio) theme. `README.md` is the upstream al-folio README, not project-specific documentation. Most day-to-day changes are content edits (news, talks, papers, teaching, CV), not code.

## Commands

- Local dev server (Docker, prebuilt image; serves on http://localhost:8080 with livereload):
  `docker compose up`
- Local dev without Docker: `bundle install && bundle exec jekyll serve`
- Production build check: `bundle exec jekyll build` (output goes to `_site/`, which is gitignored)
- Pre-commit hooks (`.pre-commit-config.yaml`): trailing-whitespace, end-of-file-fixer, check-yaml, check-added-large-files.

There are no tests. Deployment is automatic: `.github/workflows/deploy.yml` runs `bin/deploy` on every push to `master`, which builds the site and pushes it to the `gh-pages` branch. Never edit `gh-pages` or `_site/` by hand.

## Where content lives

Several sections are **hand-written HTML in `_includes/`**, not data-driven. This is a customization on top of al-folio, and you need to know it to edit them:

- **Talks**: `_includes/talks.html` (an `<li>` list, newest first). It is rendered both on `/talks/` (`_pages/talks.md`) and on the home page (`_layouts/about.html` when `talks: true` is set in `_pages/about.md`). Slides go in `assets/pdf/slides/` and are linked via `{{ '/assets/pdf/slides/<file>.pdf' | relative_url }}`.
- **Posters**: `_includes/posters.html`, with PDFs in `assets/pdf/posters/`.
- **Teaching**: `_includes/teaching.html`. It has a "current" list at the top and a "past teaching positions" list below it.
- **News**: one Markdown file per item in `_news/` (a Jekyll collection; `news_limit: 5` in `_config.yml`). Front matter is `layout: post`, `date:`, `inline: true`. `news-archive/` and `posts-archive/` sit outside any collection, so they are parked or unpublished content.
- **Publications**: `_bibliography/papers.bib`, rendered by jekyll-scholar. `selected={true}` puts a paper on the home page. `_pages/publications.md` has an explicit `years: [...]` list, so **add a new year there** when a paper from a new year is added, or that paper will not show up.
- **CV**: `_pages/cv.md` renders `_data/cv.yml` and links the PDF at `assets/pdf/cv.pdf` (via `cv_pdf`).
- **Home/about page**: `_pages/about.md` (bio, profile picture `assets/img/prof-pic.jpg`, address block, and the toggles `news`, `selected_papers`, `talks`).
- **gradieNTAG seminar**: `_pages/gradieNTAG.md` builds a table from `_data/gradientag.yml` (`headings` + `talks`, with an optional `abstract` shown as a collapsible row). `_data/gradientag-csv.csv` is an older copy of the same data and is not rendered.
- **Code packages**: `_pages/codes.md`, with files in `assets/codes/magma/`.

Navbar entries are pages in `_pages/` with `nav: true`, ordered by `nav_order`. The blog (`_pages/blog.md`, "geoblog") has `nav: false` and `_posts/` is empty.

Site-wide settings (name, contact note, social IDs, feature flags such as `enable_math` and `enable_darkmode`, jekyll-scholar config) are in `_config.yml`. Changes to `_config.yml` need a server restart to take effect.
