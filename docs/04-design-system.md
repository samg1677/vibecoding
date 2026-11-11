# Stage 4 — Design system

**Version 0.2, 2026-11-11. Awaiting a palette decision.**

A new, independent brand for Day 1 CPT Programs. It shares nothing visual with
EduConnect USA (no purple, orange, teal or Arial). EduConnect's voice, claims
policy and compliance lines still apply.

## Where things are

| File | Purpose |
|---|---|
| `design-system/css/tokens.css` | Every colour, type size, space and shape value |
| `design-system/css/site.css` | Base styles, layout and components |
| `design-system/fonts/` | Two self-hosted variable fonts and their licenses |
| `design-system/styleguide.html` | All tokens and components on one page |
| `design-system/sample-home.html` | Home page sample |
| `design-system/sample-guide.html` | Guide page sample ("What is Day 1 CPT?") |

Open the HTML files directly in a browser; they need no server. Sample copy is
illustrative and unreviewed. Striped text marks facts that must be supplied.

## Direction

The site is a reference, so it looks like a well-set document: warm paper,
dark ink, hairline rules, numbered sections, and one accent colour. It avoids
the usual marketing-site signals: no gradients, no stock photography of
students, no icon grids, no drop shadows, no scroll animation.

Three elements carry the identity:

1. **The status line.** Every regulatory page opens with the date its status
   was checked, the reviewer, and a source count, like a document header.
2. **The short answer.** A ruled block in serif type that answers the page's
   question in 40–70 words.
3. **The rule-status panel.** Current state of each rule, with a plain label
   (in effect, blocked, proposed).

## Palette options under review

Colour tokens are named by role (accent, action, highlight, deep), so a
palette is one small override file loaded after `tokens.css`. Three exist:

| Option | File | Sample pages |
|---|---|---|
| Original: evergreen on warm paper | `tokens.css` defaults | `sample-home.html`, `sample-guide.html` |
| A: navy, teal and red | `css/palette-a.css` | `sample-home-palette-a.html`, `sample-guide-palette-a.html` |
| B: single-hue blue scale | `css/palette-b.css` | `sample-home-palette-b.html`, `sample-guide-palette-b.html` |

**Palette A** (`#053c5e` `#1f7a8c` `#a31621` `#db222a` `#bfdbf7`)

| Role | Colour | Note |
|---|---|---|
| Dark sections, link hover | `#053c5e` | as supplied; white on it 11.1:1 |
| Primary button | `#a31621`, hover `#db222a` | as supplied; white on them 7.8:1 and 4.9:1 |
| Rules, markers, arrows | `#1f7a8c` | as supplied, non-text use |
| Links and small labels | `#186878` | **darkened** from `#1f7a8c`, which is 4.4:1 on the light-blue sections |
| Highlight, partner label | `#bfdbf7` | as supplied; ink on it 11.0:1 |
| Section tint | `#e9f2fc` | lightened `#bfdbf7` |
| Body text | `#0b2536` | darker navy derived from `#053c5e` |

**Palette B** (`#e3f2fd` to `#0d47a1`)

| Role | Colour | Note |
|---|---|---|
| Dark sections, hover | `#0d47a1` | as supplied; white on it 8.6:1 |
| Links, primary button | `#1565c0` | as supplied; white on it 5.8:1. `#1976d2` is 4.6:1; `#1e88e5` and lighter fail with white text |
| Rules, markers | `#2196f3` | as supplied, non-text use |
| Highlight, partner label | `#90caf9` | as supplied |
| Section tint, hairlines | `#e3f2fd`, `#bbdefb` | as supplied |
| Input borders | `#5a86b8` | **added**: the scale has no step that reaches 3:1 on white |
| Body text | `#0b1f3f` | darker than `#0d47a1` |
| "In effect" status | `#1b5e3a` on `#e1f1e8` | **added**: status labels need a second hue |

Once one is chosen it replaces the defaults in `tokens.css`, the other files
are deleted, and the table below is rewritten for it.

## Colour (original option)

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--color-ink` | `#14211f` | Text, dark sections | 15.6:1 on paper |
| `--color-ink-soft` | `#44524f` | Secondary text | 7.7:1 on paper |
| `--color-muted` | `#5b6966` | Captions, meta | 5.4:1 on paper, 4.8:1 on sand |
| `--color-paper` | `#fbf8f3` | Page background | — |
| `--color-surface` | `#ffffff` | Cards, inputs | — |
| `--color-sand` | `#f1ebe0` | Alternate sections | — |
| `--color-line` | `#d9d0c1` | Hairlines | decorative |
| `--color-line-strong` | `#8c8576` | Input borders | 3.5:1 on paper |
| `--color-accent`, `--color-action` | `#0b5345` | Links, primary buttons | 8.5:1 on paper; white on it 9.0:1 |
| `--color-accent-dark`, `--color-action-hover` | `#083d33` | Hover | white on it 12.2:1 |
| `--color-highlight` | `#f4d35e` | Highlighter, partner label, button on dark | ink on it 11.3:1 |
| `--color-caution` | `#8a4b08` | "Blocked", cautions | 5.8:1 on its tint |
| `--color-info` | `#274c77` | "Proposed" | 7.4:1 on its tint |
| `--color-danger` | `#9b2c2c` | Form errors | 7.5:1 on white |

All text pairs meet WCAG 2.2 AA (4.5:1). Ratios were computed, not estimated.
The highlighter yellow is a background only and is never used as a text colour.

## Type

| Role | Family | Size |
|---|---|---|
| Headings (H1–H3) | Source Serif 4, weight 600 | H1 34–52px, H2 26–34px, H3 20–23px |
| Body and interface | Public Sans | 16–17px, line height 1.6 |
| Lead paragraph | Public Sans | 18–21px |
| Labels and tags | Public Sans, weight 700, uppercase | 13px |

Sizes scale fluidly between phone and desktop with `clamp()`. Body text never
drops below 16px. Both fonts are open-licensed (SIL OFL 1.1), self-hosted,
Latin subset, and load with `font-display: swap`: 27 KB and 51 KB.

## Space and layout

- Spacing uses a nine-step scale on a 4px base (4, 8, 12, 16, 24, 32, 48, 64,
  96). Components use only these steps.
- Page width is 1120px; the reading column is 704px.
- Corners are 4px. Borders are 1px hairlines, or 2px ink for emphasis.
- Layout breakpoints: 640px and 992px. Checked at 390px and 1440px with no
  horizontal scroll.

## Components

| Component | Class | Notes |
|---|---|---|
| Header and navigation | `c-header`, `c-nav`, `c-menu` | Mobile menu is a native `<details>` element, so it works without JavaScript |
| Buttons | `c-button`, `--secondary`, `--on-ink` | 44px minimum height |
| Arrow link | `c-arrow-link` | "Go deeper" actions |
| Tags | `c-tag`, `--in-effect`, `--blocked`, `--proposed`, `--partner` | Rule status and listing labels |
| Breadcrumb | `c-breadcrumb` | |
| Status line | `c-status-line` | Status date, reviewer, source count |
| Short answer | `c-answer` | Direct answer block |
| Key facts | `c-facts` | A `<dl>`; each value can carry a source reference |
| Prose | `c-prose` | CMS body; numbers each H2 automatically |
| Steps | `c-steps` | Ordered process |
| Table | `c-table` | Scrolls sideways inside its frame on small screens |
| Callout | `c-callout`, `--caution` | |
| Contents list | `c-toc` | Sticky on desktop, above the content on mobile |
| FAQ | `c-faq` | Open list: every answer is visible, none collapsed |
| Sources and review | `c-sources`, `c-review` | |
| Path list | `c-paths` | "Start from your situation" |
| Card | `c-card` | Guide index |
| Rule status and tracker | `c-rules`, `c-timeline` | |
| Featured partner | `c-partner` | Label, facts, and a disclosure strip that cannot be omitted |
| Other university row | `c-school` | No recommendation label, no inquiry button |
| Form | `c-form`, `c-field`, `c-input`, `c-check` | Visible labels, error text tied to the field |
| Consultation band | `c-cta` | |
| Footer | `c-footer` | Operator disclosure and compliance lines |

## Accessibility

- Semantic landmarks, one H1, headings in order, skip link.
- Visible 3px focus outline on every interactive element.
- Links are always underlined; colour is never the only signal.
- Status tags carry text, not just colour.
- Motion is limited to one 120ms arrow nudge, removed under
  `prefers-reduced-motion`.
- Tap targets measured at 44px or more.

Not yet tested: screen readers and keyboard-only walkthroughs of real pages.
That belongs to stage 9.

## Performance

| Asset | Size |
|---|---|
| CSS (tokens + site), gzipped | about 6 KB |
| Fonts | 78 KB, two files |
| JavaScript | none |
| Images | none required by any component |

Core Web Vitals have not been measured; that needs the running application
(stage 8).

## How this becomes the Java application

The CSS and fonts move unchanged into the Spring Boot static resources. Each
component becomes one Thymeleaf fragment, and each page type in the stage 3
document becomes one template that assembles those fragments.

## Open items

1. **Logo.** The calendar-leaf mark and wordmark are a placeholder, pending
   the final brand name.
2. **Photography.** None is used. If wanted later, it needs real, consented
   images.
3. **Alliant block.** Layout is final; every fact in it waits on the approved
   facts sheet.
