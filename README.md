# nordic-iot.github.io

Archived website of the **Nordic IoT Hub — HI2OT (Nordic University Hub on Industrial Internet of Things)**, supported by NordForsk under the Nordic University Hubs programme (grant no. 86220, 2018–2024).

This is a static [Jekyll](https://jekyllrb.com/) site served by GitHub Pages. It was migrated from the original WordPress site (`www.nordic-iot.org`) and is preserved as a read-only archive. See `PRD.md` for the migration spec.

## Structure
- `index.md`, `*.md` — content pages (one per original WordPress permalink, set via `permalink:` front matter)
- `_layouts/default.html` — the single layout (logo header, nav, NordForsk funding footer)
- `assets/css/style.css` — minimal stylesheet · `assets/iiot-logo.png` — site logo · `assets/uploads/` — referenced images/PDFs
- `wp-content/uploads/` — original-path copies of the newsletters/PDFs so old deep links keep working
- `CNAME` — custom domain (`www.nordic-iot.org`)

## Run locally
```sh
gem install bundler jekyll
jekyll serve   # http://localhost:4000
```

## Deploy
Push to `main`; GitHub Pages builds automatically. To use the custom domain, point a DNS `CNAME` record for `www.nordic-iot.org` at `nordic-iot.github.io`.
