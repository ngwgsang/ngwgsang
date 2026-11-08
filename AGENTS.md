# AGENTS.md

Guidance for AI coding agents working in this repository.

## What this repo is

This is the GitHub **profile repository** for [@ngwgsang](https://github.com/ngwgsang) (Sang Quang Nguyen).
GitHub renders `README.md` at the top of the profile page at `https://github.com/ngwgsang`.
There is no build step, no package manager, and no tests: the "product" is the rendered README.

## Layout

```
.
├── README.md     # The profile page. Everything visible on GitHub lives here.
├── AGENTS.md     # This file.
└── assets/       # Static files referenced by README.md (images, SVGs, GIFs, banners).
    ├── social/   # Square 64×64 profile-link icons in the hero (rendered at 36×36).
    └── tech/     # Square 64×64 tech-stack icons used in the "Tech stack" section.
```

## Working on README.md

- **Rendering target is GitHub-flavored Markdown on github.com.** GitHub sanitizes HTML:
  no `<script>`, no `<style>` blocks, no `class`/`style` attributes, no JS. Allowed tags include
  `<div align>`, `<p align>`, `<picture>`, `<source media>`, `<img width height>`, `<a>`, `<br>`, `<details>`, `<summary>`.
- **Support both light and dark themes.** Use `<picture>` with
  `<source media="(prefers-color-scheme: dark)">`, or
  GitHub's `#gh-dark-mode-only` / `#gh-light-mode-only` URL fragments.
- **Keep the existing section order and tone:** header → About me → Publications → Building → Tech stack → Certifications.
  Writing is first person, concise, and factual. Do not invent metrics, publications, awards, or links.
- **Badges:** tech stack uses the square icons in `assets/tech/` (see below); stars use `img.shields.io` `style=flat`,
  `style=for-the-badge` for certifications. Icons are local square SVG tiles (see "Working with assets/").
- **Links:** use full `https://` URLs for external links; relative paths (`assets/...`) for files in this repo.
- Preserve the blank lines around HTML blocks — GitHub needs them to switch back to Markdown parsing.

## Working with assets/

- Put every image or media file the README uses here, then reference it with a relative path:
  `<img src="assets/banner.svg" alt="..." />` or `![alt](assets/banner.png)`.
- File names: lowercase, kebab-case, descriptive (`header-dark.svg`, `vwen-demo.gif`).
  For theme variants, use `-light` / `-dark` suffixes.
- Prefer **SVG** for graphics and diagrams, **WebP/PNG** for screenshots, and keep GIFs small
  (aim for < 5 MB; GitHub's camo proxy is slow with large files).
- SVGs must be self-contained: no external fonts or scripts (GitHub serves them as images, so they won't load).
  Convert text to paths or use system font stacks.
- Always give images meaningful `alt` text.
- **Icons (`assets/tech/`, `assets/social/`):** square 64×64 SVG tiles — a `rx="14"` rounded rect in the brand color
  with the [Simple Icons](https://simpleicons.org) glyph (24×24 path) placed via `transform="translate(14 14) scale(1.5)"`.
  If a brand has no Simple Icon, use a bold text label instead (see `agno.svg`, `trl.svg`). Include a `<title>`.
  In the README, render them at `width="40" height="40"` with matching `alt` and `title`.
- **Tech stack layout:** an HTML `<table>`, one row per group (ML & LLMs, Data, Testing, Backend, Frontend, DevOps):
  bold label in the first cell, icons in the second. Add new tools to the matching row, or add a new group row.

## Checking changes

There is no local preview tool configured. To verify:
- Preview the Markdown in an editor with GitHub-flavored rendering (e.g. VS Code preview), or
- Push to a branch and view the file on github.com, or use `gh markdown-preview` if installed.
Check both light and dark themes before finishing.

## Git

- Default branch: `main`. Commit only when the user asks.
- Write short, descriptive commit messages (e.g. `Add Vwen demo GIF to Building section`) rather than `Update README.md`.
