# Mingjun Wang Homepage Maintenance Guide

This document explains how the homepage is organized, how each file is used, and how to update, preview, debug, and deploy the site.

## 1. Repository Purpose

This repository is the GitHub Pages source for:

```text
https://xin-xi-xiao.github.io/
```

The site is a pure static, single-page academic homepage. It is written in a jemdoc-like source file and rendered to plain HTML, so GitHub Pages can serve it directly without a build server.

## 2. Important Paths

```text
/data0/wangmingjun_homepage/
├── index.jemdoc              # Main editable homepage source
├── index.html                # Generated homepage served by GitHub Pages
├── assets/
│   ├── main.css              # All visual styling and responsive layout rules
│   ├── photo.jpg             # Processed portrait used in the hero area
│   ├── cuhk.png              # CUHK logo
│   ├── ict.svg               # ICT/CAS logo
│   ├── pku.png               # Peking University logo
│   └── cv.pdf                # Reserved CV upload slot; currently intentionally absent
├── tools/
│   └── render_jemdoc.py      # Renderer: converts index.jemdoc to index.html
├── README.md                 # Short repository overview
├── design_analysis.md        # Design rationale based on Bei Yu and Yao Lai pages
└── HOMEPAGE_MAINTENANCE.md   # This maintenance guide
```

## 3. What To Edit

Edit `index.jemdoc` for content:

- Hero name, title, tagline, bio, links
- About section
- News entries
- Research interest cards
- Education rows
- Selected Publications
- Research Experience
- Honors & Awards
- Leadership & Service
- Skills
- Contact and footer

Edit `assets/main.css` for appearance:

- Page width, fonts, colors, spacing
- Portrait size and shape
- Logo alignment
- Publication cards
- Awards table
- Mobile responsive behavior

Edit `tools/render_jemdoc.py` only when changing generated HTML structure, metadata, or how jemdoc blocks are converted.

Do not edit `index.html` by hand. It is generated from `index.jemdoc`.

## 4. Current Content Rules

The homepage intentionally includes only accepted or publicly verifiable academic content.

Keep:

- Accepted conference papers
- Accepted journal papers
- Publicly visible Early Access journal papers
- Confirmed awards, education, service, skills, and project experience

Exclude:

- Patents
- Under-review papers
- Manuscripts not yet accepted
- Duplicate awards
- Overly promotional claims not supported by the CV or public sources

## 5. Current Research Narrative

The homepage foregrounds:

```text
AI4EDA · 3D IC Design Automation · Circuit Representation Learning · Fault Simulation
```

The intended emphasis is:

1. AI4EDA
2. 3D IC design automation and industrial-grade 3D IC EDA design flows
3. Circuit representation learning and multi-modal circuit data
4. Fault simulation and functional safety

Fault simulation remains visible because it is an important foundation in the publication record and industry/research experience. The site now presents it as a strong supporting thread rather than the only central identity.

## 6. CV PDF Policy

The public CV file is currently intentionally removed. The webpage keeps a stable interface:

```text
assets/cv.pdf
```

This means the CV links and buttons already point to the correct future location. Until a file is added there, the CV link will return a missing-file page.

To publish or update the CV:

```bash
cd /data0/wangmingjun_homepage
cp "/path/to/latest_cv.pdf" assets/cv.pdf
python3 tools/render_jemdoc.py index.jemdoc
git add -A
git commit -m "docs: update public cv"
git push -u origin main
```

Use the exact filename `cv.pdf` so the existing links continue to work.

If the browser still opens an older CV after deployment, add a cache version in `index.jemdoc`, for example:

```html
href="assets/cv.pdf?v=20260601"
```

Then rebuild and push.

## 7. Image and Logo Updates

Portrait:

```text
assets/photo.jpg
```

The current portrait is displayed as a compact rounded rectangle, not a circle. The CSS class is:

```css
.portrait-card
```

Affiliation logos:

```text
assets/cuhk.png
assets/ict.svg
assets/pku.png
```

The hero-area logos are wrapped in equal-size `.logo-frame` boxes so that CUHK, ICT/CAS, and PKU align visually even if the source image canvases differ.

If replacing a logo, keep the filename unchanged or update both `index.jemdoc` and any relevant documentation.

## 8. Publication Updates

Each publication card is in `index.jemdoc` inside:

```html
<section id="publications">
```

Each paper should include:

- Venue badge, such as `ICML 2025` or `IEEE TCAD 2025`
- Type badge: `Conference` or `Journal`
- Title
- Authors, with `<strong>Mingjun Wang</strong>`
- Metadata line starting with `Conference paper · ...` or `Journal article · ...`
- Short factual description
- Public links when available

For co-first-author papers, use:

```html
<span class="award-badge">Co-first †</span>
```

and keep the note:

```text
† Equal contribution.
```

Recommended publication ordering:

1. Year descending
2. Within the same year, first-author/co-first AI4EDA and 3D IC papers first
3. Journal papers remain clearly visible, especially IEEE TCAD
4. Fault simulation and functional-safety papers remain included as the foundation thread

## 9. Award Updates

Awards are in `index.jemdoc` inside:

```html
<section id="awards">
```

Use the table columns:

```text
Award | Venue / Organization | Year
```

Recommended ordering:

1. Year descending
2. Within the same year, public EDA/AI competition awards first
3. Scholarships and institutional awards after competition awards
4. Avoid duplicates

The EDA² Integrated Circuit Elite Challenge 2023 award should appear only once.

## 10. Research Experience Ordering

Research Experience is ordered to support the current academic identity:

1. AI4EDA, multi-modal circuit data, and 3D IC EDA flow automation
2. Fault Simulation Research at ICT/CAS
3. Industrial Experience at CASTEST
4. PKU undergraduate thesis

The required fixed date corrections are:

```text
Fault Simulation Research: Jul. 2023 — Mar. 2025
Industrial Experience:     Sep. 2021 — Jan. 2025
```

## 11. Build

Render the homepage:

```bash
cd /data0/wangmingjun_homepage
python3 tools/render_jemdoc.py index.jemdoc
```

Expected output:

```text
generated index.html
```

## 12. Local Preview

Start a local static server:

```bash
cd /data0/wangmingjun_homepage
python3 -m http.server 8000
```

Open:

```text
http://127.0.0.1:8000/
```

Check at least:

- Desktop width
- Tablet width
- Mobile width around 375px
- Hero portrait shape and logo alignment
- Navigation anchors
- Publication labels: Conference / Journal
- CV link behavior
- Research Experience dates

Stop the server with `Ctrl+C`.

## 13. Debug Checklist

If content changes do not appear:

1. Rebuild with `python3 tools/render_jemdoc.py index.jemdoc`.
2. Hard refresh the browser.
3. If CSS or images are cached, update the query string in `index.jemdoc`, for example:

```text
assets/main.css?v=20260528e
assets/photo.jpg?v=20260528e
```

If the portrait becomes circular again:

1. Check `assets/main.css`.
2. Confirm `.portrait-card` has `border-radius: var(--radius-card) !important;`.
3. Confirm there is no old inline style such as `border-radius:50%`.
4. Rebuild `index.html`.

If logos look inconsistent:

1. Check the hero logo HTML uses `.logo-frame`.
2. Check `.logo-frame` has fixed width and height.
3. Check `.logo-frame img` uses `max-width` and `max-height`, not custom per-logo widths.

If GitHub Pages does not update:

1. Confirm changes are committed and pushed to `main`.
2. Wait one or two minutes for GitHub Pages to rebuild.
3. Open the browser in a private window or hard refresh.
4. Check repository settings: Pages should serve from the root of the `main` branch.

## 14. Deployment

After editing:

```bash
cd /data0/wangmingjun_homepage
python3 tools/render_jemdoc.py index.jemdoc
git status
git add -A
git commit -m "fix: refine homepage layout and research narrative"
git push -u origin main
```

After pushing, visit:

```text
https://xin-xi-xiao.github.io/
```

## 15. Recommended Update Workflow

For normal content updates:

```bash
cd /data0/wangmingjun_homepage
git pull --ff-only
edit index.jemdoc
python3 tools/render_jemdoc.py index.jemdoc
python3 -m http.server 8000
git status
git add -A
git commit -m "docs: update homepage content"
git push -u origin main
```

For style-only updates:

```bash
edit assets/main.css
python3 tools/render_jemdoc.py index.jemdoc
git add -A
git commit -m "style: refine homepage layout"
git push -u origin main
```

For CV updates:

```bash
cp "/path/to/latest_cv.pdf" assets/cv.pdf
python3 tools/render_jemdoc.py index.jemdoc
git add -A
git commit -m "docs: update public cv"
git push -u origin main
```

## 16. Final Quality Checklist

Before pushing, confirm:

- `index.html` is regenerated.
- Portrait is rectangular and compact.
- Hero logos are visually aligned.
- AI4EDA and 3D IC design automation are prominent.
- Industrial-grade 3D IC EDA flow appears in the research narrative.
- Fault simulation remains visible.
- ICT/CAS education lists Prof. Xiaowei Li and Prof. Huawei Li.
- Publications have Conference or Journal labels.
- No patents or under-review papers are included.
- Awards contain no duplicate EDA² 2023 item.
- Research Experience dates are correct.
- The CV file is either intentionally absent or placed at `assets/cv.pdf`.
- `git status` is clean after commit.
