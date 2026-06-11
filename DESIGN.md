# Kai Cyber — Design Language

A single-page site about the permanent problems of security. Built to read the
same way in 2036 as it does today. Nothing here references a tool, a vendor, a
trend, or a year.

---

## 1. Principles

1. **Timeless over current.** No glassmorphism, no gradients-as-decoration, no
   borrowed dashboard aesthetics. If an element would identify the year it was
   built, it is removed.
2. **One accent.** A single restrained teal carries every signal: emphasis,
   interaction, compromise. Everything else is achromatic.
3. **Typography is the interface.** Hierarchy comes from scale, weight, and
   space — not from boxes, cards, or shadows.
4. **Whitespace is structural.** Sections breathe at viewport scale. Density is
   reserved for the one place it means something: the network.
5. **Calm authority.** Swiss poster discipline meets the quiet of a security
   operations floor at 3 a.m. The site never raises its voice.
6. **Nothing that can break.** One file. No requests beyond the document
   itself. No dependency that can rot, redirect, or disappear.

## 2. Palette

| Token        | Value                  | Use                                        |
| ------------ | ---------------------- | ------------------------------------------ |
| `--bg`       | `#0B0C0D`              | Page ground. Near-black, faintly warm-gray |
| `--bg-raise` | `#101214`              | Visualization field, subtle separation     |
| `--line`     | `#222628`              | Hairline rules, borders                    |
| `--ink`      | `#E7EAE9`              | Primary text                               |
| `--ink-dim`  | `#8C9492`              | Secondary text, labels                     |
| `--ink-faint`| `#565E5C`              | Tertiary: numerals, metadata               |
| `--accent`   | `#46B5A2`              | The one color. Links, focus, compromise    |
| `--accent-dim`| `#2C6E63`             | Accent at rest (edges, traces)             |

Rules:
- The accent never appears as a large fill outside the visualization.
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
- `prefers-reduced-motion`: reveals disabled; the cascade plays as discrete
  state changes — no easing, no pulses, no continuous motion. Same lesson,
  no movement.

## 6. The Centerpiece — “One Credential”

A canvas network of ~24 systems. One node holds a reused password. Pressing
**Run the breach** authenticates the attacker once, then walks trust
relationships node by node until everything is teal. Total runtime under 20
seconds. Captions (four, one sentence each) narrate the phases; a mono counter
tracks systems compromised. The closing line is the thesis: zero
vulnerabilities exploited.

- Safe node: dark fill, `--line` stroke. Compromised: `--accent` fill, single
  expanding pulse ring (canvas, not CSS).
- Edges at rest: barely visible. Traversed: `--accent-dim`, drawn as a moving
  trace.
- Deterministic layout (seeded), responsive to container width, crisp at any
  `devicePixelRatio`.
- Fully operable by keyboard: one real `<button>`, captions mirrored to an
  `aria-live` region, canvas carries a complete text alternative.

## 7. Craftsmanship Standards

- Single `index.html`. Zero external requests. Loads and renders in well under
  one second on any connection, because there is nothing to wait for.
- Semantic structure: one `h1`, ordered heading levels, `header/main/section/
  footer`, skip link, visible focus rings (2px accent outline, 3px offset).
- Keyboard: every interactive element reachable and operable; no traps.
- Responsive from 320px to 3440px+ with no horizontal scroll at any width.
- 60fps: animation work is transform/opacity/canvas only; the rAF loop does no
  allocation per frame and stops when idle or off-screen.
- Print: dark ground dropped, content legible. Even paper gets a design.
