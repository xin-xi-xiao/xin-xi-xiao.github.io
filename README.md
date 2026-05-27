# Mingjun Wang Academic Homepage

This is a single-page academic homepage prepared for GitHub Pages. The source is `index.jemdoc`, rendered by `tools/render_jemdoc.py` into `index.html`, with custom styling in `assets/main.css`.

The page combines Bei Yu-style academic information structure with Yao Lai-style modern publication cards, compact typography, school-logo education rows, and a responsive layout.

For the complete maintenance guide, including file roles, CV updates, local preview, debugging, and deployment, see [`HOMEPAGE_MAINTENANCE.md`](HOMEPAGE_MAINTENANCE.md).

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

## Content Policy Used Here

The homepage includes accepted or publicly verifiable research outputs only. Intellectual-property records and non-accepted manuscripts were intentionally omitted. Awards, education, service, projects, and skills were reorganized from the local CV files supplied in this directory.

The public CV PDF is intentionally not included at the moment. The webpage keeps the link target `assets/cv.pdf` as a stable upload slot. To publish a CV later, place the latest PDF at `assets/cv.pdf`, rebuild `index.html`, commit, and push.

## Public Sources Cross-Checked

- Google Scholar profile supplied by the owner: `https://scholar.google.com/citations?user=E9aUbvAAAAAJ`
- IEEE Xplore document `11523085`
- OpenReview / ICLR for CircuitNet 3.0
- PMLR / OpenReview for ICML 2025 RTLDistil
- DBLP and conference/program records for ITC-Asia 2024, ICCAD 2024, ASP-DAC 2025, ISEDA 2025, DAC 2025, ICCAD 2025, ASP-DAC 2026, DAC 2026, and ICML 2026
- CUHK research portal and Prof. Bei Yu's publication pages
- Local CUHK, ICT/CAS, and PKU logo files supplied in this directory
