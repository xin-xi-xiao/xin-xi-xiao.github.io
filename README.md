# Mingjun Wang Academic Homepage

This is a single-page academic homepage prepared for GitHub Pages. The source is `index.jemdoc`, rendered by `tools/render_jemdoc.py` into `index.html`, with custom styling in `assets/main.css`.

The page combines Bei Yu-style academic information structure with Yao Lai-style modern publication cards, compact typography, school-logo education rows, and a responsive layout.

For the complete maintenance guide, including file roles, CV updates, local preview, debugging, and deployment, see [`HOMEPAGE_MAINTENANCE.md`](HOMEPAGE_MAINTENANCE.md).

For the optional synchronized mirror at `https://wang-mingjun.github.io/`, including organization creation, least-privilege token setup, automatic synchronization, verification, and rollback, see [`HOMEPAGE_MIRROR_SETUP.md`](HOMEPAGE_MIRROR_SETUP.md).

## Local Build

```bash
cd /data0/wangmingjun_homepage
python3 tools/render_jemdoc.py index.jemdoc
```

Open `index.html` in a browser, or serve the folder with any static server:

```bash
python3 -m http.server 8000
```

## Publish to GitHub Pages

```bash
git add -A
git commit -m "refactor: redesign academic homepage"
git push -u origin main
```

For the user-homepage repository `xin-xi-xiao/xin-xi-xiao.github.io`, GitHub Pages serves the root of the `main` branch at `https://xin-xi-xiao.github.io/`.

The renderer keeps that URL as the default canonical address. To prepare a build for a verified replacement domain, set `HOMEPAGE_URL` when rendering:

```bash
HOMEPAGE_URL=https://www.example.com/ python3 tools/render_jemdoc.py index.jemdoc
```

Do not change the canonical URL or add a `CNAME` file until the target GitHub account or custom domain is under your control. See the alternate-address section in [`HOMEPAGE_MAINTENANCE.md`](HOMEPAGE_MAINTENANCE.md).

## Content Policy Used Here

The homepage includes accepted or publicly verifiable research outputs only. Intellectual-property records and non-accepted manuscripts were intentionally omitted. Awards, education, service, projects, and skills were reorganized from the local CV files supplied in this directory.

The public CV is stored at `assets/cv.pdf`. Replace that file with the latest PDF, update the cache version in `index.jemdoc`, rebuild `index.html`, commit, and push.

The compact `WM` chip/AI mark is used as the navigation brand and browser/device icon. The normalized master is `assets/brand-mark-512.png`; smaller files in `assets/` are purpose-sized so the browser does not download the original high-resolution artwork for a 28 px or 32 px display.

## Public Sources Cross-Checked

- Google Scholar profile supplied by the owner: `https://scholar.google.com/citations?user=E9aUbvAAAAAJ`
- IEEE Xplore document `11523085`
- OpenReview / ICLR for CircuitNet 3.0
- PMLR / OpenReview for ICML 2025 RTLDistil
- DBLP and conference/program records for ITC-Asia 2024, ICCAD 2024, ASP-DAC 2025, ISEDA 2025, DAC 2025, ICCAD 2025, ASP-DAC 2026, DAC 2026, and ICML 2026
- CUHK research portal and Prof. Bei Yu's publication pages
- Local CUHK, ICT/CAS, and PKU logo files supplied in this directory
