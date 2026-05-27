# Mingjun Wang Personal Homepage

This is a jemdoc-source personal homepage prepared for GitHub Pages. The content is based on `CVformingjun (21).pdf`, `main (1).tex`, and public publication records.

## Local Build

```bash
cd /data0/wangmingjun_homepage
python3 tools/render_jemdoc.py index.jemdoc
```

Open `index.html` in a browser, or serve the folder with any static server.

## Publish to GitHub Pages

1. Create a public repository named `xin-xi-xiao.github.io` for a user homepage, or use any repository and enable GitHub Pages from the repository settings.
2. Upload the full contents of this folder, including `index.jemdoc`, `index.html`, `assets/`, and `tools/`.
3. In GitHub, go to `Settings -> Pages`.
4. Set `Source` to `Deploy from a branch`, select the `main` branch and the root folder.
5. Wait for GitHub Pages to finish deployment. The user-homepage URL will be `https://xin-xi-xiao.github.io/`.

## Content Policy Used Here

The homepage includes accepted or publicly verifiable work only. Patent items and under-review submissions were intentionally excluded. Awards, education, service, projects, and skills were reorganized from the local CV files supplied in this directory.

## Public Sources Cross-Checked

- Google Scholar profile supplied by the owner: `https://scholar.google.com/citations?user=E9aUbvAAAAAJ`
- IEEE Xplore document `11523085`
- OpenReview / ICLR for CircuitNet 3.0
- PMLR / OpenReview for ICML 2025 RTLDistil
- DBLP and conference/program records for ITC-Asia 2024, ICCAD 2024, ASP-DAC 2025, ISEDA 2025, DAC 2025, ICCAD 2025, ASP-DAC 2026, DAC 2026, and ICML 2026
- CUHK research portal and Prof. Bei Yu's publication pages
