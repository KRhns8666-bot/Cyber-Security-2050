# Domain Migration — kaicyber.org → kaiguardian.org

**Reason:** legal requirement to stop using the "Kai Cyber" name. The domain
`kaicyber.org` itself contains the name, so it must be **fully retired** — this
is a clean break, **not** a redirect.

**Trade-off accepted:** existing links, bookmarks, QR codes, and any Google
ranking on `kaicyber.org` will stop working once the old domain is taken down.
This is unavoidable when the name must be dropped entirely.

---

## Status

- [x] **Code updated** to `kaiguardian.org` (this branch): `CNAME`, all
  `canonical` / `og:url` / `og:image` / `twitter:image` URLs on every page,
  `sitemap.xml`, `robots.txt`, form `source` labels, `README.md`.
- [ ] **Register `kaiguardian.org`** (owner) — WHOIS shows it currently
  unregistered/available; confirm at checkout.
- [ ] **Add DNS for kaiguardian.org** in Cloudflare (owner) — records below.
- [ ] **Deploy** (merge this branch to `main`) — GitHub Pages picks up the new
  domain from the `CNAME` file; Let's Encrypt SSL issues automatically.
- [ ] **Take down kaicyber.org** (owner) — remove its site DNS records, then
  let the registration lapse / delete the zone.
- [ ] **Rename the YouTube channel** off `@KaiCyberAcademy` and update the 4
  marked links (see `ASSET_REBRAND_TODO.md`).

---

## Step 1 — Register the domain (owner)

Register **`kaiguardian.org`** — recommended at **Cloudflare** (Dashboard →
Domain Registration → Register Domains), since DNS is already on Cloudflare.

> Before paying, confirm "KaiGuardian" is not itself trademarked by another
> security company, ideally with whoever raised the current legal issue.

## Step 2 — Deploy the code (automated)

Merge this branch to `main`. The push updates the GitHub Pages custom domain
(via the `CNAME` file now containing `kaiguardian.org`). **Do this only after
Step 3's DNS is in place**, so the site is reachable the moment it switches.

## Step 3 — DNS for kaiguardian.org (owner, in Cloudflare)

Add these records on the new `kaiguardian.org` zone, all **DNS-only (grey
cloud)** — identical to how kaicyber.org was pointed at GitHub Pages:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `krhns8666-bot.github.io` |

Then in the repo **Settings → Pages**, confirm the custom domain shows
`kaiguardian.org` and tick **Enforce HTTPS** once the cert has issued (can take
a few minutes to an hour).

## Step 4 — Retire kaicyber.org (owner — the "stop using it" part)

Because there is **no redirect**:

1. In Cloudflare, on the `kaicyber.org` zone, **delete the A/AAAA/CNAME records**
   that point at GitHub Pages. The old site stops serving immediately.
2. **Do not renew** `kaicyber.org` at its next expiry (or delete the zone /
   cancel the registration if you want it gone sooner). Confirm with your
   legal contact whether immediate cancellation is required or letting it lapse
   is acceptable.
3. Optionally tighten email DNS (SPF/DMARC) on the old domain to prevent
   spoofing while it winds down.

## Notes

- A GitHub Pages site can only have **one** custom domain, so kaicyber.org and
  kaiguardian.org cannot both be served — which is exactly what a full
  retirement wants.
- No email/forms break from the domain change: the Web3Forms endpoint is
  independent of the domain; only the internal `source` labels were updated for
  accuracy.
