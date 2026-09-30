# Asset TODO

Tracks images, video and configuration the site needs. Updated 30 September 2026.

## Done

- [x] **Hero image** — futuristic 2050 megacity keyframe: `assets/hero-city.webp` (desktop,
  also the video poster), `assets/hero-city-mobile.webp` (mobile crop), `assets/hero-city.jpg`
  (fallback). Generated in Higgsfield; no characters.
- [x] **Mascot** — `assets/mascot-kaiguardian.webp` (Kai the lion, from the Higgsfield
  element), shown in the About section.
- [x] **YouTube** — all links use `@KaiGuardianAcademy`; the Watch and learn section uses
  four real channel videos (click-to-play).
- [x] **Guide PDFs** — `guides/scam-check-starter.pdf`, `guides/boss-scam.pdf`,
  `guides/family-scam-guide.pdf` (KaiGuardian branding).
- [x] **Social preview** — `assets/og-image.jpg` rebuilt from the futuristic city keyframe (teal/amber).
- [x] **Favicon** — inline SVG, no brand text.

## Still needed

- [ ] **Hero background video (optional).** A short, muted loop (about 8–15 s, under
  ~4 MB, no essential words in the footage), e.g. a suspicious message arriving on a
  phone → Maya pausing before tapping → a subtle shield → a calm family scene with Kai
  and Maya. Save as `assets/hero-family.mp4` and set `data-src="assets/hero-family.mp4"`
  on `#gh-video` in `index.html`. Until then the hero shows the poster image.
- [ ] **Privacy notice contact email.** `privacy.html` shows a placeholder
  (`[contact email to be added]`). Note: kaiguardian.org is set up to send and receive
  no email (null MX + `v=spf1 -all`), so use an address on another domain, or set up
  email for the domain first. **Must be filled in before publishing.**
- [ ] **Paid guide** — the Complete Family Cyber Safety Guide needs a payment platform
  (e.g. Gumroad, Ko-fi). Do not commit the paid PDF to this public repository.

## Not applicable

- No analytics, cookies, JSON-LD, web manifest or RSS feed on the site.
