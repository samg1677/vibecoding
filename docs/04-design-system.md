# Stage 4 — Design system

**Version 0.3, 2026-11-11. Blue and red palette. Awaiting review.**

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

The site is a reference, so it looks like a well-set document: a near-white
page, dark ink, hairline rules, numbered sections, and two colours. It avoids
the usual marketing-site signals: no gradients, no stock photography of
students, no icon grids, no drop shadows, no scroll animation.

Three elements carry the identity:

1. **The status line.** Every regulatory page opens with the date its status
   was checked, the reviewer, and a source count, like a document header.
2. **The short answer.** A ruled block in serif type that answers the page's
   question in 40–70 words.
3. **The rule-status panel.** Current state of each rule, with a plain label
   (in effect, blocked, proposed).

## Colour

Two colours: **blue is primary, red is secondary.** Blue carries structure,
links and labels. Red is reserved for the action button and for cautions.

**Primary: blue**

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--blue-900` | `#053c5e` | Dark sections, link hover, "in effect" label | white on it 11.6:1 |
| `--blue-700` | `#0a5f94` | Links, small labels, rules, arrows | 6.6:1 on page, 6.0:1 on tint |
| `--blue-200` | `#bfdbf7` | Highlight, partner label, button on dark | ink on it 11.0:1 |
| `--blue-100` | `#d6e8fb` | Tag background | blue 900 on it 9.3:1 |
| `--blue-50` | `#e9f2fc` | Alternate sections, notes | — |
| `--blue-25` | `#f8fbfe` | Page background | — |

**Secondary: red**

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--red-700` | `#a31621` | Primary button, cautions, form errors | white on it 7.8:1 |
| `--red-500` | `#db222a` | Button hover, logo bar | white on it 4.9:1 |
| `--red-50` | `#fbe6e7` | Caution and error background | red 700 on it 6.5:1 |

**Neutrals**

| Token | Hex | Use | Contrast |
|---|---|---|---|
| `--color-ink` | `#0b2536` | Body text | 15.2:1 on page |
| `--color-ink-soft` | `#3c5263` | Secondary text | 7.8:1 on page |
| `--color-muted` | `#566b7b` | Captions, meta | 5.3:1 on page, 4.9:1 on tint |
| `--color-line` | `#c5d6e6` | Hairlines | decorative |
| `--color-line-strong` | `#6b8296` | Input borders | 3.9:1 on page |
| `--color-surface` | `#ffffff` | Cards, inputs | — |

`#053c5e`, `#bfdbf7`, `#a31621` and `#db222a` are used exactly as supplied.
`#0a5f94` is a lighter step of the same blue, added so links are
distinguishable from body text. The supplied teal `#1f7a8c` is not used.

All text pairs meet WCAG 2.2 AA (4.5:1). Ratios were computed, not estimated.

Components never reference the scales directly. They use role tokens
(`--color-accent`, `--color-action`, `--color-highlight`, `--color-deep` and
so on), so a later colour change is made in one place in `tokens.css`.

Known trade-off of a two-colour system: red means both "act" (the solid
button) and "caution" (tinted boxes, the "blocked" label, form errors). The
two are told apart by treatment, and every caution carries text.

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
