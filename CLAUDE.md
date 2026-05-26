# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

This repo is a **pkgdown-generated static documentation site** for the `mrgsolve` R package, served at `mrgsolve.org/docs`. All HTML, Markdown, and asset files here are build artifacts — do not edit them directly. The authoritative source is the main package repo at `metrumresearchgroup/mrgsolve`.

## How docs are generated

Docs are built by running `pkgdown::build_site()` (or the equivalent `make` target) inside the main `mrgsolve` package repo. The output is written directly into this directory and then committed and pushed here.

Commit messages follow the pattern: `make site for X.Y.Z` or `refresh docs for X.Y.Z`.

## Site structure

- `reference/` — per-function HTML and Markdown pages (generated from roxygen2 docs)
- `articles/` — vignettes; `articles/extra/` holds supplemental articles
- `news/` — changelog (`NEWS.md` rendered as HTML)
- `tutorials/` — tutorial pages (currently empty)
- `deps/` — vendored JS/CSS dependencies (Bootstrap, jQuery, etc.)
- `pkgdown.yml` — build metadata (pkgdown version, pandoc version, last built timestamp, article/URL mappings)
- `llms.txt` — machine-readable site index for LLM consumption
- `search.json` — search index

## When to edit files here

Almost never. The only legitimate direct edits are:

- `CLAUDE.md` — this file
- Static assets that are not auto-generated (e.g., `lightswitch.js`, `katex-auto.js`)
- `404.md` / `404.html` if the custom error page needs updating

For any content change (function docs, vignettes, changelog), make the edit in the main `mrgsolve` package repo and rebuild the site.
