# Kai Cyber

**Live at [kaicyber.org](https://kaicyber.org)**

A scam-awareness site for the Asia-Pacific region — free field guides,
an interactive phishing lab, a live "Scam Atlas" threat radar, and
country-level scam intelligence sourced from official government data.
Built by [@KaiCyberAcademy](https://www.youtube.com/@KaiCyberAcademy).

## What's here

| Path | What it is |
| --- | --- |
| `index.html` | The main site: cinematic hero, the six permanent security problems, a live breach demo, case files, a phishing simulator, APAC Scam Watch, Scam Atlas country data, free-guide email capture, and the About section. |
| `radar/index.html` | **Scam Atlas Live Radar** — a self-contained scam-intelligence dashboard: a canvas-drawn 3D threat globe, a live (clearly-labelled simulated) scam feed, country heat and scam-type breakdowns, a scam-of-the-day, and an in-browser message/link checker. |
| `one-credential.html`, `one-credential-film.html` | Standalone proof-of-concept pages exploring the scroll-driven cinematic hero used on the homepage. |
| `assets/` | Images, the hero video, and the social preview card. |
| `guides/` | Downloadable PDF guides offered through the free-guides opt-in. |
| `robots.txt`, `sitemap.xml`, `CNAME` | Deployment and crawler config for the custom domain. |

## Stack

Plain HTML, CSS, and vanilla JavaScript. **No framework, no build step, no
dependencies.** Every page is a single file that renders on its own —
open it in a browser and it works. This is a deliberate constraint: a
static site has nothing to build, nothing to break in a supply chain,
and nothing to go out of date.

Interactive pieces (the breach demo, the phishing lab, the threat globe,
the message checker) are hand-written canvas and DOM code — no charting
or 3D library.

## Deployment

Hosted on GitHub Pages via the workflow in `.github/workflows/pages.yml`
— every push to `main` deploys automatically. The custom domain
(`kaicyber.org`) is configured through the `CNAME` file plus DNS records
at the registrar; see `CNAME` for the current domain.

## Design

See [`DESIGN.md`](./DESIGN.md) for the site's typography, layout, and
motion principles.
