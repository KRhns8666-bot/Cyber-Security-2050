# Security Protocol — KaiGuardian (kaiguardian.org)

A practical, prioritized checklist for protecting this site. The site is
**static** (GitHub Pages + Cloudflare), which removes most classic risks — there
is no server, database, or login to breach. The real risks are: **DDoS**,
**DNS / domain hijacking**, **account takeover**, and **abuse of the contact
form**. This protocol covers each.

Work top-to-bottom. Do **Tier 1** first — it's the highest-value, lowest-effort
protection.

---

## Tier 1 — Do these now (essential)

### 1. Finish HTTPS correctly (order matters)
- [ ] Keep Cloudflare DNS records **grey (DNS-only)** until `https://kaiguardian.org`
      loads with a valid padlock. Proxying too early breaks GitHub's SSL issuance.
- [ ] In GitHub repo → **Settings → Pages**, confirm custom domain shows
      `kaiguardian.org` and tick **Enforce HTTPS** once available.

### 2. Turn on proxy + strict TLS (only after HTTPS works)
- [ ] Switch the 4 A records (and `www`) to **orange (Proxied)**.
- [ ] Cloudflare → **SSL/TLS → Overview**: set mode to **Full (strict)**.
      Never use "Flexible" (causes redirect loops / insecure origin).
- [ ] **SSL/TLS → Edge Certificates**: enable **Always Use HTTPS**,
      **Automatic HTTPS Rewrites**, and **HSTS** (start max-age 6 months).

### 3. Lock down the accounts (this is how static sites actually get taken over)
- [ ] Enable **2FA** on your **Cloudflare** account (authenticator app, not SMS).
- [ ] Enable **2FA** on your **GitHub** account.
- [ ] Confirm **Registrar Lock** is ON for kaiguardian.org (Cloudflare → the
      domain → registration settings). Prevents unauthorized transfers.
- [ ] Use a **unique, strong password** for each account (password manager).

### 4. Protect DNS integrity
- [ ] Enable **DNSSEC** (Cloudflare → DNS → Settings → DNSSEC → Enable).
      Prevents attackers from spoofing your DNS answers.

---

## Tier 2 — Do these this week (strong hardening)

### 5. Basic bot & DDoS defenses (free)
- [ ] Cloudflare → **Security → Bots**: enable **Bot Fight Mode**.
- [ ] Cloudflare → **Security → DDoS**: leave the managed HTTP DDoS ruleset on
      (default). Cloudflare absorbs volumetric attacks automatically.
- [ ] **Do NOT** leave **Under Attack Mode** on permanently — it challenges every
      visitor. Turn it on only *during* an active attack, then off again.

### 6. Email spoofing protection (protect your brand's name)
Even though the site sends no email, attackers can forge "from kaiguardian.org".
Add these DNS TXT records on kaiguardian.org:
- [ ] **SPF**: TXT `@` → `v=spf1 -all` (no one is authorized to send mail — use
      this if the domain never sends email; adjust if you add email later).
- [ ] **DMARC**: TXT `_dmarc` → `v=DMARC1; p=reject; rua=mailto:YOUR_EMAIL`
- [ ] (If you never use email on this domain) a null **MX**: `.` with priority 0,
      to signal the domain accepts no mail.

### 7. Contact form abuse
- [ ] The Web3Forms form already uses a **honeypot** field — keep it.
- [ ] If spam appears, add **Cloudflare Turnstile** (free CAPTCHA) or enable
      Web3Forms' built-in captcha.
- [ ] Never put secrets in client-side JS. The Web3Forms **access key is public
      by design** (it only routes to your inbox) — that is expected, not a leak.

### 8. Security response headers
Static hosts can't set headers directly, but once **proxied** you can add them
via Cloudflare → **Rules → Transform Rules → Modify Response Header** (or a
Workers snippet):
- [ ] `Strict-Transport-Security: max-age=15552000; includeSubDomains`
- [ ] `X-Content-Type-Options: nosniff`
- [ ] `Referrer-Policy: strict-origin-when-cross-origin`
- [ ] `X-Frame-Options: DENY` (or a `Content-Security-Policy: frame-ancestors 'none'`)
- [ ] A basic **Content-Security-Policy** if you have time (test carefully — the
      site loads a video, Web3Forms, and a public breach feed).

---

## Tier 3 — Good practice & ongoing

### 9. Repository hygiene
- [ ] Keep the repo's **branch protection** on `main` (require the deploy to pass).
- [ ] Never commit API keys, tokens, or private data. Run GitHub **secret
      scanning** (Settings → Code security).
- [ ] Review the **GitHub Pages** build source stays as intended.

### 10. Monitoring
- [ ] Set an **uptime monitor** (e.g. a free pinger) on `https://kaiguardian.org`.
- [ ] Watch Cloudflare → **Security → Events** occasionally for spikes.
- [ ] Set a **calendar reminder ~11 months out** to confirm domain auto-renew
      (a lapsed domain is the #1 way small sites get hijacked).

### 11. Retire the old domain securely (kaicyber.org)
Because the move off `kaicyber.org` is a legal requirement (no redirect):
- [ ] Remove kaicyber.org's site DNS records once kaiguardian.org is confirmed live.
- [ ] Turn **off auto-renew** / let it lapse per your legal guidance, OR keep it
      parked with a null MX + `v=spf1 -all` so it can't be used to spoof you while
      it winds down.
- [ ] Do not point it at the new site (that would still be "using" the old name).

---

## Quick reference — what NOT to do
- ❌ Don't proxy (orange) before HTTPS is confirmed working.
- ❌ Don't use SSL/TLS "Flexible" mode.
- ❌ Don't leave "Under Attack Mode" on all the time.
- ❌ Don't treat the Web3Forms public access key as a secret to rotate — it's public.
- ❌ Don't let the domain registration lapse unintentionally.

---

*This is a general hardening guide for a static site, not legal or professional
security-audit advice. For the trademark/legal matter driving the domain change,
follow your legal contact's specific instructions.*
