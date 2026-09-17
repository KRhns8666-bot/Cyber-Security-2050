# Asset Rebrand TODO

Tracks non-code assets and external integrations that carry brand identity and
may still need owner action after the KaiGuardian rebrand.

## Done

- [x] **`assets/og-image.jpg`** — regenerated (1200×630) with KAI·GUARDIAN
  wordmark, "Digital Safety for Every Family" headline, and updated supporting
  copy. Live social preview will refresh once scrapers re-crawl (or via each
  platform's cache-refresh / debugger tool).
- [x] **Favicon** — inline SVG (red dot, no text). No brand text, no change
  needed.

## Owner action needed

- [ ] **YouTube channel rename.** Display text across the site now reads
  "KaiGuardian", but the links still point to `@KaiCyberAcademy` (still the
  live, working channel). Once you rename the channel to the new handle:
  - Replace `https://www.youtube.com/@KaiCyberAcademy` with the new
    `https://www.youtube.com/@NEW_HANDLE` in:
    - `index.html` (3 places — Resources card, About link, footer link)
    - `README.md` (1 place)
  - Each spot has a `<!-- TODO ... -->` comment marking it.

## Verify visually (no code change expected)

- [ ] **Downloadable guide PDFs** in `guides/` — open each and confirm no
  "Kai Cyber" wordmark is baked into the cover/artwork. If any show the old
  brand, they'll need to be re-exported (source files live outside this repo).
- [ ] **Hero video / other images in `assets/`** — confirm no old wordmark is
  visible in-frame.

## Not applicable

- No analytics property, JSON-LD, web manifest, or RSS feed in the repo carries
  a brand string.
- Domain unchanged (`kaicyber.org`) — no DNS, redirect, or email (SPF/DMARC)
  changes required for this rebrand.
