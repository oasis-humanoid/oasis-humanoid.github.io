# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page academic project website for the paper **TextOp: Real-time Interactive
Text-Driven Humanoid Robot Motion Generation and Control**. It is a static GitHub Pages
site built from the [Nerfies](https://github.com/nerfies/nerfies.github.io) template
(Bulma CSS + jQuery + bulma-carousel/bulma-slider). There is no build step, package
manager, test suite, or backend — everything is plain HTML/CSS/JS served as-is.

All page content lives in a single file: `index.html`. The `static/` directory holds
vendored CSS/JS (`static/css`, `static/js`), images (`static/images`), videos
(`static/videos`), and the paper PDF (`static/pdf`).

## Developing

- **Preview locally:** open `index.html` directly in a browser, or serve the folder:
  `python3 -m http.server 8000` then visit `http://localhost:8000`. A server is needed
  for the `<video>` / iframe elements to load correctly.
- **Deploy:** push to `main` on the `oasis-humanoid/oasis-humanoid.github.io` remote;
  GitHub Pages publishes automatically. There is no CI.

## Important: asset references are currently out of sync

`index.html` points to many media files that do **not** exist in `static/`. Before
changing the page, verify that referenced paths resolve, and prefer fixing references to
match files actually present. Examples of paths referenced but missing:
- Images: `static/images/teaser-v2.png`, `static/images/method-v4.png`,
  `static/images/logo-small-nobg.png` (favicon)
- Videos: `static/videos/demo_big.mp4`, `static/videos/skill_*.mp4` (9 clips),
  `static/videos/robustness_*.mp4` (4 clips)

Files actually present include `static/images/方法图.png`, `static/images/封面.jpg`,
`static/videos/main_video.mp4`, and several Chinese-named subfolders under
`static/videos/` (e.g. `真机demo视频（压缩版）`, `teleop_video（压缩版）`,
`asset（压缩版）`). Some asset filenames contain non-ASCII (Chinese) characters and
parentheses — quote paths in shell commands and URL-encode them in HTML if linked.

## Editing conventions

- Page-specific styles are an inline `<style>` block in the `<head>` of `index.html`
  (e.g. `.grid-skills`, `.grid-robustness`, `.video-item`); the rest comes from vendored
  Bulma CSS. Add new layout rules to that block, not to the vendored `*.min.css`.
- Do not hand-edit vendored libraries (`bulma*.min.css/js`, `fontawesome.all.min.*`).
- Author/affiliation/links, abstract, method figure, video grids, and the BibTeX block
  are discrete sections in `index.html` — edit the relevant section in place.
- The page includes a Google Analytics tag (`gtag.js`, id `G-XXDZK5L5FH`) and links to
  arXiv, code, and Twitter that should be kept current with the publication.
