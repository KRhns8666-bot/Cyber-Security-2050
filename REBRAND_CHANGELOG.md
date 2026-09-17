# Rebrand Changelog — Kai Cyber → KaiGuardian

**Scope:** Public-facing brand migration from **Kai Cyber / Kai Cyber Academy**
to **KaiGuardian** on the existing site. **The domain `kaicyber.org` is kept
unchanged** (free rebrand — brand name only, no new domain, no redirects).

**Method:** Full audit and per-occurrence classification first, then targeted
edits. No blind global search/replace. Functionality, SEO structure, forms,
downloads, tracking IDs, external attributions, and factual/statistical content
were all preserved.

---

## Brand mappings applied

| Old | New |
| --- | --- |
| Kai Cyber / Kai Cyber Academy | KaiGuardian |
| KAI·CYBER (wordmark) | KAI·GUARDIAN |
| Primary descriptor | Digital Safety for Every Family |

Sub-brands (unchanged names, updated attribution):
- **Scam Atlas** → attribution "a KaiGuardian project"
- **Kai Check** → display copy "KaiGuardian Check" (URL `kai-check` kept)
- **CyberKid** → "CyberKid by KaiGuardian" (name + URL kept)
- **Phish Lab** → unchanged
- Government / agency names → unchanged

---

## Files changed

| File | What changed |
| --- | --- |
| `index.html` | Head meta (title, description, og:*/twitter:* site name + titles + image alt); header wordmark `KAI·GUARDIAN`; Resources section copy + card titles; Atlas note; **About section** (heading "About KaiGuardian" + two new body paragraphs, mission callout, handle, links); footer credit + link display; Web3Forms subject/from_name labels. |
| `radar/index.html` | Head meta (title "Scam Atlas — Live Scam Radar \| KaiGuardian", description, og:site_name); wordmark; back-nav "← KaiGuardian"; footer "a KaiGuardian project". |
| `404.html` | `<title>` and "← Back to KaiGuardian" link. |
| `one-credential.html` | Meta description, og:site_name, og:title, og:description, twitter:title, back link, HUD wordmark → KaiGuardian. |
| `one-credential-film.html` | Same six brand strings + HUD wordmark → KaiGuardian. |
| `README.md` | Title `# KaiGuardian`; "Built by KaiGuardian" (YouTube URL kept + TODO). |
| `DESIGN.md` | Title `# KaiGuardian — Design Language`. |
| `assets/og-image.jpg` | Regenerated 1200×630 social card with KAI·GUARDIAN wordmark, "Digital Safety for Every Family" headline, and updated supporting copy. |

## SEO changes

- Homepage `<title>`: **KaiGuardian — Digital Safety for Every Family**
- Homepage meta description: *Practical scam awareness, phishing training,
  family digital-safety guides and APAC scam intelligence for children, adults
  and seniors.*
- Scam Atlas `<title>`: **Scam Atlas — Live Scam Radar | KaiGuardian**
- Canonical URLs, `og:url`, `og:image` URLs: **unchanged** (`kaicyber.org`).

## Domain

**Unchanged — `kaicyber.org` retained everywhere.** No new domain, no
redirects, no CNAME/sitemap/robots.txt changes required. (A future domain move
would be a separate, server-side 301 via Cloudflare — not part of this rebrand.)

## Content NOT touched (per operating rules)

- Scam statistics, government-source data, case-study facts, dates, citations.
- External attributions.
- Tracking / form IDs: Web3Forms access key `8a96adea-…` and form `source:`
  strings (`kaicyber.org free guides` / `kaicyber.org family guide interest`)
  kept — the domain is unchanged so these stay accurate.

## Remaining old-name strings, and why they remain

| Occurrence | Reason kept |
| --- | --- |
| `kaicyber.org` (canonical, og:url, og:image, sitemap.xml, robots.txt, CNAME, README, form `source`) | **Domain is intentionally unchanged.** Not a brand string. |
| `@KaiCyberAcademy` YouTube hrefs (index.html ×3, README ×1) | **Functional URL** — channel not yet renamed. Display text already says "KaiGuardian"; each href carries a `TODO` comment to update to `@NEW_HANDLE` once the channel is renamed by the owner. |
| `kai-check` URL path (index.html) | **Functional URL** kept; display copy updated to "KaiGuardian Check". |

## QA performed

- Repo-wide grep for `kai·?cyber` / `KaiCyberAcademy`: only the intentional
  keeps above remain; **no brand copy left unconverted**.
- `index.html` inline JS (6 blocks) syntax-checked with `node --check` — clean.
- `radar/index.html` JS syntax-checked — clean.
- Backup branch `backup/pre-kaiguardian` created before edits.
