# Kai Cyber — Design Language

A site about the permanent problems of security, and about spotting the scams
that exploit them. Nothing here references a tool, a vendor, a trend, or a
year — the six problems, and the tells that expose a scam, don't age.

> **Note on this document's history:** the site launched with a single-accent
> teal palette and a canvas-only hero. It has since moved to a red/navy
> palette and a cinematic video-scrubbed hero, and grown a second page (the
> Scam Atlas live radar). The principles below — typography, layout rhythm,
> motion discipline — held through that evolution and still govern the
> current site; the palette table and the absolute "one file" claims in
> §8 are updated to match what's actually deployed today.

---

## 1. Principles

1. **Timeless over current.** No glassmorphism, no gradients-as-decoration, no
   borrowed dashboard aesthetics. If an element would identify the year it was
   built, it is removed.
2. **One accent, one warning.** A single dominant accent carries brand,
   emphasis, and interaction; a second color is reserved strictly for
   "this is safe / correct" so the two are never confused. Everything else is
   achromatic.
3. **Typography is the interface.** Hierarchy comes from scale, weight, and
   space — not from boxes, cards, or shadows.
4. **Whitespace is structural.** Sections breathe at viewport scale. Density is
   reserved for the one place it means something: the network.
5. **Calm authority.** Swiss poster discipline meets the quiet of a security
   operations floor at 3 a.m. The site never raises its voice.
6. **Nothing that can break.** Static HTML, CSS, and vanilla JS. No build
   step, no framework, no dependency that can rot, redirect, or disappear.

## 2. Palette

| Token          | Value       | Use                                         |
| -------------- | ----------- | -------------------------------------------- |
| `--bg`         | `#07090F`   | Page ground. Near-black navy                 |
| `--bg-raise`   | `#0D1120`   | Cards, visualization field, subtle separation|
| `--line`       | `#1C2238`   | Hairline rules, borders                      |
| `--ink`        | `#F2F4F8`   | Primary text                                 |
| `--ink-dim`    | `#8A96B0`   | Secondary text, labels                       |
| `--ink-faint`  | `#48536A`   | Tertiary: numerals, metadata                 |
| `--accent`     | `#E3001B`   | The dominant color. Brand, links, focus, compromise |
| `--accent-dim` | `#8C0010`   | Accent at rest (edges, traces)               |
| `--safe`       | `#00C853`   | Reserved exclusively for "correct / safe" states (e.g. the phishing lab's right answers) — never used for brand or emphasis |

Rules:
- The accent never appears as a large fill outside the visualization or a CTA.
- `--safe` (green) and `--accent` (red) are never both used to mean the same
  thing — green always means safe, red always means danger or brand.
- No pure white (`#FFF`) and no pure black (`#000`) anywhere.
- Contrast: body text ≥ 12:1, secondary text ≥ 5:1, accent on bg ≥ 5:1.

## 3. Typography

**Stack (grotesque):**
`-apple-system, "Helvetica Neue", Helvetica, "Arial Nova", Arial, sans-serif`

**Stack (mono, for labels and figures):**
`ui-monospace, "SF Mono", Menlo, Consolas, "Liberation Mono", monospace`

**Scale (fluid, clamp-based):**

| Role      | Size                          | Weight | Leading | Tracking  |
| --------- | ----------------------------- | ------ | ------- | --------- |
| Display   | `clamp(2.6rem, 8vw, 6.5rem)`  | 600    | 1.02    | `-0.035em`|
| Headline  | `clamp(1.8rem, 4vw, 3.25rem)` | 600    | 1.08    | `-0.025em`|
| Lede      | `clamp(1.15rem, 1.8vw, 1.5rem)`| 400   | 1.45    | `-0.01em` |
| Body      | `clamp(1rem, 1.05vw, 1.125rem)`| 400   | 1.65    | 0         |
| Label     | `0.78rem` mono, uppercase     | 500    | 1       | `0.14em`  |
| Numeral   | `clamp(3rem, 6vw, 5rem)` mono | 400    | 1       | `-0.02em` |

Rules:
- Measure: body text never exceeds ~62ch.
- Section numerals (`01`–`06`) set in mono, `--ink-faint`, as structural marks.
- No italics. Emphasis is accent color or weight, never slant.

## 4. Layout & Rhythm

- Content column: `min(1080px, 100% − 2 × clamp(20px, 5vw, 64px))`, centered.
- Vertical rhythm: section spacing `clamp(7rem, 18vh, 13rem)`; intra-section
  spacing on an 8px base scale (8 / 16 / 24 / 40 / 64).
- Principles set as a strict left-aligned ledger: hairline rule, numeral,
  title, paragraph. Two-column (numeral gutter + text) above 720px.
- Hairline rules (`1px`, `--line`) are the only dividers. No cards, no boxes.
- Ultrawide: content column holds; the visualization field alone may stretch
  to `1280px`. Nothing ever spans raw viewport width except rules and ground.

## 5. Motion

- **Permitted:** CSS `transform` + `opacity` transitions; canvas drawn inside
  `requestAnimationFrame`. Nothing else animates. No layout-affecting
  properties, ever.
- Reveal-on-scroll: 12px rise + fade, 600ms, `cubic-bezier(.22,.61,.36,1)`,
  triggered once via `IntersectionObserver`. Subtle enough to miss.
- The visualization renders only while on screen and only while running.
- Ledger rows entering together stagger by 70ms; the rise is 16px over 700ms.
- While the visualization is idle, faint probe dots wander the graph — the
  scanning never stops. Max three concurrent, ~35% peak alpha, killed the
  moment the canvas leaves the viewport.
- Case-file numerals count up once on entry (1.1s, cubic ease-out, rAF).
- `prefers-reduced-motion`: reveals disabled; the cascade plays as discrete
  state changes — no easing, no pulses, no idle noise, no ticker scroll, no
  counter animation. Same lesson, no movement.

## 6. The Centerpiece — “One Credential”

A canvas network of ~24 systems. One node holds a reused password. Pressing
**Run the breach** authenticates the attacker once, then walks trust
relationships node by node until everything is teal. Total runtime under 20
seconds. Captions (four, one sentence each) narrate the phases; a mono counter
tracks systems compromised. The closing line is the thesis: zero
vulnerabilities exploited.

A second button, **Run it segmented**, replays the identical attack against
the same network partitioned into three zones (dashed boundary walls; severed
cross-zone edges fade to near-nothing). The cascade takes the first zone and
dies at the wall — contained at 8 of 24. Demonstration and counter-
demonstration: the attack is a property of the architecture, not the attacker.

- Safe node: dark fill, `--line` stroke. Compromised: `--accent` fill, single
  expanding pulse ring (canvas, not CSS).
- Edges at rest: barely visible. Traversed: `--accent-dim`, drawn as a moving
  trace.
- Deterministic layout (seeded), responsive to container width, crisp at any
  `devicePixelRatio`.
- Fully operable by keyboard: one real `<button>`, captions mirrored to an
  `aria-live` region, canvas carries a complete text alternative.

## 7. Case Files & the Live Wire

The record keeps the page from being abstract. Six exhibits, one per problem,
each a famous breach told in two sentences with a single mono numeral as its
headline stat. Vendors are never named — exhibits are identified by what they
were (“a credit bureau, 2017”), because the lesson outlives the brand.

Each exhibit opens. The title is a real `<button>` (aria-expanded, animated
“+” that rotates to “×”); the dossier expands beneath in the ledger’s own
geometry with three columns — **Anatomy** (the kill chain in four numbered
steps), **The bill** (three label/figure lines), and **This problem, today**
(up to three current vulnerability disclosures from a keyless public advisory
feed, keyword-matched to the problem, linking out to the full record). A
closing **lesson** line ties the exhibit back to its problem, and each of the
six problems cross-links to its case file, which opens on arrival.

The live wire is a single horizontal ticker of recently disclosed breaches,
fed by one keyless public endpoint, fetched after load with a hard 6-second
timeout. **Live data is garnish, never load-bearing**: it renders nothing the
page depends on, it sanitizes everything it shows (text nodes only, never
markup), and when the feed is unreachable or dead it degrades to one line —
“Feed unreachable. The breaches continue regardless.” The page must be whole
with the network cable cut.

## 8. Craftsmanship Standards

- No framework, no build step, no npm dependency. Every page — `index.html`,
  `radar/index.html`, the standalone demo pages — is hand-written HTML, CSS,
  and vanilla JS that runs as-is, with no compile or bundle step between the
  source and what ships.
- The critical text and layout render with zero blocking external requests.
  The homepage's video hero, the Scam Atlas live radar, the email-capture
  forms (posted to Web3Forms), and the live breach-advisory wire are each
  optional enhancements layered on top: every one of them fails silently and
  leaves the page fully usable if it can't load — the site never depends on
  the network being kind.
- Semantic structure: one `h1` per page, ordered heading levels, `header/main/
  section/footer`, skip link, visible focus rings (2px accent outline, 3px
  offset).
- Keyboard: every interactive element reachable and operable; no traps.
- Responsive from 320px to 3440px+ with no horizontal scroll at any width.
- 60fps: animation work is transform/opacity/canvas only; the rAF loop does no
  allocation per frame and stops when idle or off-screen.
- Print: dark ground dropped, content legible. Even paper gets a design.
