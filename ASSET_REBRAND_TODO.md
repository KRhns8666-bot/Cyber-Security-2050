# Asset TODO

Tracks images, video and configuration the site needs. Updated 2 October 2026.

## Done

- [x] **Hero image** — futuristic 2050 megacity keyframe: `assets/hero-city.webp` (desktop,
  also the video poster), `assets/hero-city-mobile.webp` (mobile crop), `assets/hero-city.jpg`
  (fallback). Generated in Higgsfield; no characters.
- [x] **Scroll film** — `assets/city-scrub.mp4` / `.webm` (desktop, ~5 MB) and
  `assets/city-scrub-mobile.mp4` / `.webm` (~2.7 MB), re-encoded near all-intra from the
  Kling 3.0 (Higgsfield) city film: 10 s, silent, threats race through a 2050 megacity until
  a teal hexagonal shield dome closes over it. Fixed behind the whole homepage and driven by
  scroll; poster/reduced-motion/data-saver fallback is `assets/hero-city.webp`. Replaces the
  play-once `hero-city*.mp4/.webm`, which were removed.
- [x] **Space intro removed from the homepage** — the "One Credential" film no longer opens
  `index.html`; it stays on `one-credential-film.html` (`assets/one-credential*.mp4`).
- [x] **Mascot** — `assets/mascot-kaiguardian.webp` (Kai the lion, from the Higgsfield
  element), shown in the About section.
- [x] **YouTube** — all links use `@KaiGuardianAcademy`; the Watch and learn section uses
  four real channel videos (click-to-play).
- [x] **Guide PDFs** — `guides/scam-check-starter.pdf`, `guides/boss-scam.pdf`,
  `guides/family-scam-guide.pdf` (KaiGuardian branding).
- [x] **Social preview** — `assets/og-image.jpg` rebuilt from the futuristic city keyframe (teal/amber).
- [x] **Privacy notice** — `privacy.html`, contact kaichencyber@gmail.com.
- [x] **Favicon** — inline SVG, no brand text.

## Still needed

- [ ] **Paid guide** — the Complete Family Cyber Safety Guide needs a payment platform
  (e.g. Gumroad, Ko-fi). Do not commit the paid PDF to this public repository.

## Not applicable

- No analytics, cookies, JSON-LD, web manifest or RSS feed on the site.
