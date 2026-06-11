# PRD: Migrate the Nordic IoT Hub (HI2OT) website to GitHub Pages

## 1. Context and goal

The **Nordic IoT Hub** is the website of **HI2OT — the Nordic University Hub on Industrial Internet of Things**, a research-and-education collaboration of five Nordic universities (DTU, NTNU, Aalto, Lund, KTH), supported by **NordForsk** under the Nordic University Hubs programme (**grant no. 86220**, 2018–2024). The site is currently a WordPress site live at https://www.nordic-iot.org.

The hub has finished, so this is a **one-time conversion of a frozen archive**. The task is to convert the **Simply Static export** in `/Users/paupo/Downloads/simply-static-1-1781191857/` into a **Markdown-based Jekyll site** in `~/git/nordic-iot.github.io/`, to be pushed to `github.com/nordic-iot/nordic-iot.github.io` and served by GitHub Pages. Content fidelity matters; the WordPress look and feel does not.

This mirrors the earlier FORA migration (same WordPress theme, `thbusiness`); reuse that approach and tooling.

### Owner decisions (already made — do not re-ask)

| Decision | Choice |
|---|---|
| Domain | Keep **www.nordic-iot.org** as canonical → include a `CNAME` file containing `www.nordic-iot.org`. Original URL paths must be **preserved** so existing links keep working (DNS will be pointed at GitHub Pages later). |
| Logo | Use the existing site logo `wp-content/uploads/2018/08/iiotlogo_small.png` → copy to `assets/iiot-logo.png`. |
| Framing | **Finished — preserve as a historical archive** (HI2OT ran 2018–2024). No present-tense calls to action; Admission/Events/News read as a record. |
| Template | **Minimal Jekyll, same as FORA**: one tiny custom layout (logo header, one-line text nav, NordForsk funding footer), one small stylesheet, no JavaScript, GitHub-Pages-safe (no plugins). Drop the WordPress theme/plugins entirely. |
| Calendar menu item | **Drop it** — the Events → Calendar menu item had no exported page. |

## 2. Source inventory

All content pages are `index.html` files (one per WordPress permalink). **21 pages**, all using the `thbusiness` theme — the same as FORA, so the FORA extraction logic applies (`div.entry-content` inside `article#post-...` inside `div#content`; title from `h1.entry-title` or `<title>` minus the `– Nordic IoT Hub` suffix).

| Source path | Page | Notes |
|---|---|---|
| `index.html` | Home | Root page; **custom widget/carousel layout, no `entry-content`** — handcraft it (see §4). |
| `about/index.html` | About | + child `about/nordic-university-hub-on-industrial-iot-hi2ot/` (HI2OT). |
| `admision/index.html` | Admission | Keep the misspelled slug `/admision/` for URL fidelity. |
| `events-page/index.html` | Events | + child `events-page/distinguished-lecturers/`. |
| `brokerage/index.html` | Brokerage | Top-level slug; appears under the Events menu. |
| `partners/index.html` + 5 | Partners | `partners/` index + `technical-university-of-denmark`, `norwegian-university-of-science-and-technology`, `aalto-university`, `lund-university`, `kth-royal-institute-of-technology`. |
| `doctoral-school/index.html` + 4 | R&D Projects | The section's **menu label is "R&D Projects"** (its `<title>` says "R&D Projects") though the slug is `/doctoral-school/`. Children: `list-of-affiliated-phds`, `phd-courses`, `list-of-affiliated-faculty`, `rd-facilities`. |
| `msc-student-projects-2/index.html` | MSc thesis projects | Keep slug `/msc-student-projects-2/`; appears under the R&D Projects menu. |
| `roadmap/index.html` | Roadmap | — |
| `news/index.html` | News | Self-contained listing (no separate date-based posts were exported). Convert as a single page. |
| `wp-content/uploads/...` | Assets | 58 jpg, 52 png, 12 jpeg, 2 svg, gif — plus **57 PDFs** (newsletters etc.), 1 `.pptx` (brokerage flyer), 1 `.zip`. Copy only files **referenced** by kept pages (see §6). |
| `wp-content/plugins`, `wp-content/themes`, `wp-includes/` | — | WordPress machinery. **Do not copy any of it.** |

## 3. Target structure

```
nordic-iot.github.io/
├── CNAME                    # www.nordic-iot.org
├── _config.yml
├── _layouts/default.html    # the ONE layout
├── assets/
│   ├── css/style.css
│   ├── iiot-logo.png        # from wp-content/uploads/2018/08/iiotlogo_small.png
│   ├── nordforsk-... (footer logo, optional)
│   └── uploads/...          # referenced images/PDFs (preserve YYYY/MM substructure)
├── index.md                 # handcrafted home (permalink /)
├── about.md  (+ about/nordic-university-hub-on-industrial-iot-hi2ot.md)
├── admision.md
├── events-page.md  (+ events-page/distinguished-lecturers.md)
├── brokerage.md
├── partners.md  (+ partners/<5 universities>.md)
├── doctoral-school.md  (+ doctoral-school/<4 children>.md)
├── msc-student-projects-2.md
├── roadmap.md
├── news.md
├── wp-content/uploads/...   # original-path copies of the PDFs/PPTX so old deep links work
└── README.md
```

### `_config.yml` (minimal)
```yaml
title: Nordic IoT Hub
description: "HI2OT — Nordic University Hub on Industrial Internet of Things (NordForsk grant 86220, 2018–2024)"
url: "https://www.nordic-iot.org"
markdown: kramdown
exclude: [README.md, PRD.md]
defaults:
  - scope: { path: "" }
    values: { layout: default }
```
No theme gem. GitHub-Pages-safe features only (zero CI config).

### `_layouts/default.html`
Minimal HTML5 layout (adapt FORA's): charset/viewport, `<title>{{ page.title }} – Nordic IoT Hub</title>`, link to `/assets/css/style.css`, **no JavaScript**. Header: the IIoT logo (`/assets/iiot-logo.png`, link to `/`, max-height ~70px). Nav — one line of plain text links (submenus flattened; Calendar dropped):

`Home · About · Admission · Events · Partners · R&D Projects · Roadmap · News`

linking to `/`, `/about/`, `/admision/`, `/events-page/`, `/partners/`, `/doctoral-school/`, `/roadmap/`, `/news/`. Then `<main>{{ content }}</main>`. Footer on every page:
> Nordic University Hub on Industrial Internet of Things (HI2OT). Supported by NordForsk under the Nordic University Hubs programme, grant no. 86220. The hub ran 2018–2024; this site is preserved as an archive.

### `assets/css/style.css`
Reuse FORA's stylesheet (~40–70 lines): centered column (`max-width: 50rem`), system font stack, readable line height, bordered collapsed tables, responsive images, modest link color. Pick a link/accent color from the site's palette (a Nordic blue/teal is fine).

## 4. The home page (handcrafted)

`index.html` has no `entry-content` — it's a carousel of the 5 partner universities plus intro text. Build `index.md` (permalink `/`) as a simple landing page:
- A short intro from the homepage text: *"The overall aim of HI2OT is to promote Nordic collaboration in Industrial IoT, which will increase the capacity of the participating organizations by creating a critical mass."* (and any other intro paragraphs visible on the homepage).
- The five partner universities as a list/logo row linking to their partner pages (`/partners/technical-university-of-denmark/`, …).
- An "Explore" list linking to About, Partners, R&D Projects, Roadmap, Events, News, Admission.
- Extract the homepage's visible body text (strip nav/sidebar/scripts) to recover any intro paragraphs and the NordForsk funding note.

## 5. URL preservation (critical — custom domain kept)

Every kept page must be reachable at its **original path** via `permalink` front matter, e.g.:
```yaml
---
title: "Aalto University"
permalink: /partners/aalto-university/
---
```
Rules:
1. `index.html` → `index.md`, `permalink: /`.
2. Every other page: `permalink:` = its source directory path with trailing slash (e.g., `doctoral-school/phd-courses/index.html` → `/doctoral-school/phd-courses/`). Preserve odd slugs verbatim (`/admision/`, `/msc-student-projects-2/`, `/events-page/`).
3. Internal links inside content → root-relative (`/partners/`, `/doctoral-school/phd-courses/`), stripping any `https://www.nordic-iot.org` / `http://nordic-iot.org` prefix.
4. Remove links to WordPress machinery (`/feed`, `/comments/feed`, `/xmlrpc.php`, `/wp-json/...`, `/wp-admin/...`, `?p=`, `?page_id=`, author/category/tag, date archives). Unwrap (keep the text) or drop the fragment.
5. `mailto:` and external links: keep unchanged.

## 6. Assets

1. Scan all kept pages for `/wp-content/uploads/...` references (`src`, `srcset`, `href`). Copy **only referenced files** to `assets/uploads/` preserving the `YYYY/MM/filename` substructure; rewrite references to `/assets/uploads/...`. Prefer the **original** over a resized `-WxH` variant when the original exists; drop `srcset`.
2. **Documents (PDF/PPTX/ZIP) must keep working at their old deep links**: additionally copy every referenced PDF/PPTX/ZIP to a top-level `wp-content/uploads/YYYY/MM/` path in the repo (Jekyll passes unknown dirs through as static files), so links like `/wp-content/uploads/2022/11/Newsletter_5_2022.pdf` resolve. There are ~57 PDFs (newsletters, etc.) — keep all that are referenced.
3. `iiotlogo_small.png` → `assets/iiot-logo.png`.
4. Copy nothing from `wp-content/plugins/`, `wp-content/themes/`, `wp-includes/`.

## 7. Conversion rules (HTML → Markdown)

Identical to the FORA migration:
1. One `.md` per kept page; front matter `title` + `permalink`; layout from `_config` default.
2. Convert `entry-content` to clean Markdown (headings demoted so the page H1 comes only from the layout — start body headings at `##`; the layout renders the title as the H1). Paragraphs, lists, links, images, bold/italic.
3. **Tables** (e.g., PhD lists, faculty lists, courses, roadmap): convert plain-text tables to Markdown tables; keep complex/link-heavy cells as clean inline HTML `<table>`. **Preserve every row** — never truncate.
4. **Linearize WordPress layout tables** (single-row, no-`<th>`) into stacked content so images/text in cells survive (this fixed FORA's profile tables).
5. Decode HTML entities to UTF-8; keep typographic quotes/dashes.
6. Remove theme cruft: sidebars (search, recent posts, dead social/Twitter widgets), share buttons, "Read More" teasers, post-meta lines, category/tag lists, comment markup, inline `style=` attributes, emoji/RSS/oEmbed `<head>` junk, "Proudly powered by WordPress" footer.
7. Do not invent or rephrase content — copy text verbatim apart from the structural cleanup.

## 8. Out of scope
- No search, comments, RSS, social feeds, contact forms, or the Calendar widget.
- No redesign or content editing beyond §7.
- No Jekyll plugins, Gemfile, or GitHub Actions workflow — stock GitHub Pages build only.
- DNS changes for www.nordic-iot.org are done by the owner separately; this task only adds the `CNAME` file.

## 9. Acceptance criteria
1. `~/git/nordic-iot.github.io/` contains the 21 content pages, `CNAME`, `_config.yml`, one layout, one stylesheet, the logo, and the referenced assets — and **zero** files from `wp-content/plugins`, `wp-content/themes`, or `wp-includes`.
2. `jekyll build` succeeds with stock GitHub Pages settings (use the local Homebrew Ruby + `~/.gem-jekyll` Jekyll, as for FORA/AEGIS).
3. Every original URL of a kept page resolves in `_site/` (spot-check `/`, `/about/`, `/partners/aalto-university/`, `/doctoral-school/phd-courses/`, `/admision/`, `/events-page/distinguished-lecturers/`).
4. No internal link or image in `_site/` is broken; no remaining references to `nordic-iot.org` hostnames, `/wp-admin/`, `/wp-json/`, `/feed`, or `wp-content/plugins`.
5. Tables (PhD lists, faculty, courses, roadmap) keep the same number of rows as the source.
6. Every page shows the IIoT logo header, the nav line, and the NordForsk funding footer.
7. The newsletters/PPTX open both at `/assets/uploads/...` and at their original `/wp-content/uploads/...` paths.

## 10. Suggested working order
1. Skeleton (`_config.yml`, layout, CSS, logo, `CNAME`); convert one simple page (`about`) end-to-end; `jekyll build` to validate.
2. Convert the remaining top-level pages, then the sections (partners ×5, doctoral-school ×4, events-page ×1) — template-like within each section.
3. Asset scan-and-copy pass (images + the ~57 PDFs dual-pathed), then the link-rewriting pass.
4. Handcraft `index.md` (home) and finalize `news.md`.
5. Run the §9 acceptance checks (reuse the FORA validator).
6. `git init`, commit; push to `git@github.com:nordic-iot/nordic-iot.github.io.git` only when the owner asks.
