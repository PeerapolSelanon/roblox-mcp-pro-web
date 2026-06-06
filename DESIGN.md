# Design

## Theme

Dark, warm near-black. A confident "pro builder tool" surface — quiet and precise, with a single
ember accent that carries the identity. Deliberately **not** the blue/purple-gradient dark-SaaS
reflex. The warm undertone is a subtle nod to Roblox's red heritage, kept adult and sharp.

Color strategy: **Committed-restrained** — neutral dark surface, one saturated accent at ~10–15% of
the surface (CTAs, key words, the live "command" highlights), accent never drenched.

## Color (OKLCH)

| Token | Value | Use |
|---|---|---|
| `--bg` | `oklch(0.165 0.012 45)` | page background, warm near-black |
| `--surface` | `oklch(0.205 0.014 45)` | raised panels |
| `--surface-2` | `oklch(0.245 0.016 45)` | nested/raised within panels |
| `--line` | `oklch(0.30 0.016 45)` | hairline borders |
| `--ink` | `oklch(0.96 0.008 70)` | primary text (warm off-white) |
| `--muted` | `oklch(0.74 0.014 55)` | secondary text (≥4.5:1 on `--bg`) |
| `--faint` | `oklch(0.60 0.012 55)` | tertiary/labels (large/secondary only) |
| `--accent` | `oklch(0.70 0.19 45)` | ember — CTAs, emphasis, highlights |
| `--accent-hi` | `oklch(0.77 0.18 55)` | accent hover/lighter |
| `--on-accent` | `oklch(0.18 0.02 45)` | text on accent fills (near-black) |
| `--ok` | `oklch(0.78 0.15 155)` | success ticks only (sparing) |

No gradient text anywhere. Emphasis via the solid accent color + weight, never `background-clip:text`.

## Typography

- **Display:** "Bricolage Grotesque" 700/800 — characterful, slightly "built", for headings.
- **Body:** "Hanken Grotesk" 400/500/600 — clean workhorse.
- **Mono:** "JetBrains Mono" 400/500 — tool names (`execute_luau`), code, the live command mock, small labels.
- Fluid `clamp()` scale, ratio ~1.3. Hero `clamp()` max ≤ 5rem. Display letter-spacing -0.02 to -0.03em.
- Line-height: body 1.6; headings 1.05–1.15. `text-wrap: balance` on h1–h3, `pretty` on prose.
- None of the three are on the reflex-reject list. Mono is used because the product literally runs code.

## Layout

- Max content width ~1080px; generous fluid section padding via `clamp()`, varied for rhythm.
- **Hero:** asymmetric — copy + CTA on one side, a crafted "agent → Studio" command mock on the other.
- **Capabilities:** not an identical icon-card grid. A bento/asymmetric set with mono tool-names + plain descriptions; varied cell sizes.
- **How it works:** the one place numbered markers are earned (a real 3-step ordered flow).
- **Pricing:** single focused $5/mo card. **FAQ:** `<details>` accordion. **Legal:** refund/privacy/terms inline. **Footer.**
- No per-section uppercase eyebrows. No side-stripe borders. Cards only where they're the right affordance.

## Components

- Buttons: `--accent` fill with `--on-accent` text (primary); hairline `--line` ghost (secondary). Radius 11px.
- Command mock: dark `--surface` panel, mono lines, ember highlights on tool calls, a small "result" chip.
- Pills/labels: mono, `--line` border, `--muted` text.

## Motion

- Page-load: hero copy + mock rise/fade with ease-out-expo, short stagger.
- Scroll: subtle reveal (IntersectionObserver) that **enhances already-visible content** (no visibility gating).
- Hover: accent shift + 1px lift on interactive elements.
- `@media (prefers-reduced-motion: reduce)`: all transitions become instant/crossfade; no transforms.
