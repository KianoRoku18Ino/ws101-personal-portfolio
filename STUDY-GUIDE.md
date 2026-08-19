# Study Guide — WS101 Activity 1 (Personal Web Page)

Every HTML tag and CSS concept actually used in `260003GalaridoPortfolio.html` / `260003GalaridoStyle.css`, grouped by where it appears on the page. Meant for reviewing before a quiz or a walkthrough defense — not a full language reference (see `html-complete-reference.html` / `css-complete-reference.html` for that).

## 1. Document Structure

| Tag | Used for | Why this tag and not a `<div>` |
|---|---|---|
| `<header>` | The sticky top nav | Semantically "introductory content for this page" |
| `<nav>` | The 5 section links inside the header | Tells assistive tech "this is a navigation block" |
| `<main>` | Wraps every section between nav and footer | One per page — marks the primary content, skip-link target |
| `<section>` | About, Academics, Projects, Media, Connect | Each is a distinct thematic block, each gets an `id` for anchor-linking |
| `<footer>` | Page footer | Semantically "closing content," not just "the last div" |
| `<article>` | Each project card | Content that would still make sense standing alone (a single project) |

**Key idea to be able to explain out loud:** semantic tags (`header`/`nav`/`main`/`section`/`footer`/`article`) exist so a screen reader or a search engine understands the *role* of each block, not just its box shape. A `<div>` carries zero meaning — it's a fallback for when nothing semantic fits.

## 2. Navigation Without JavaScript

- `<a href="#about">` — jumps to `<section id="about">`. Plain browser anchor behavior.
- `scroll-behavior: smooth;` on `html` (CSS) — the only reason the jump *animates* instead of snapping instantly. Remove that one line and the links still work, just abruptly.
- `.skip-link` — an `<a href="#main-content">` that's positioned off-screen (`left: -999px`) until it receives keyboard focus (`:focus`), then jumps on-screen. Standard accessibility pattern for keyboard users to bypass the nav.

## 3. The Hero's Sunburst — Pure CSS, No Image File

`repeating-conic-gradient(var(--gold) 0deg 8deg, transparent 8deg 24deg)` on a `::before` pseudo-element, spun with `@keyframes` + `animation`. Study angle: a conic gradient sweeps color around a center point (like a color wheel), so alternating opaque/transparent 8°/24° slices produce ray shapes with no actual image asset needed.

## 4. Lists vs. Tables — the Distinction the Whole Page Is Built On

- **`<ul>`/`<li>`** used for: nav links, hobby cards, game chips, the About "fact list", link cards. All of these are just *label/value pairs or unordered items* — no real row/column relationship.
- **`<table>`** used for: the Grade 10/11/12 report cards. This *is* real tabular data (subject × quarter grid), so `<table>` with `<thead>`/`<tbody>`/`<tfoot>`, `<caption>`, and `<th scope="col">` / `<th scope="row">` is the correct, accessible choice.
- **`<ol>`** used for: the academic timeline (`Grade 10 → 11 → 12`). An ordered list is correct here specifically because chronological order carries meaning — swap the order and the content is wrong, unlike the hobby grid where order doesn't matter.

## 5. Zero-JavaScript Interactivity

| Feature | Native element/property doing the work |
|---|---|
| Expand/collapse grade tables | `<details>` + `<summary>` — the browser handles open/closed state |
| Custom "+" → "✕" toggle icon | `details[open] summary::after { transform: rotate(45deg); }` — an attribute selector reacting to the `open` attribute the browser itself toggles |
| Hover-lift on hobby cards | `:hover` + `transform: translateY(-3px)` + `transition` |
| Keyboard focus ring | `:focus-visible` (not plain `:focus` — this only shows for keyboard users, not mouse clicks) |
| "Send" button on the contact form | `<form action="mailto:...">` — opens the visitor's email client; there's no backend, so this is the honest ceiling of what static HTML can do |

## 6. Forms & Input Validation

- `type="email"` — browser checks the format before allowing submit, no JS needed.
- `required` attribute — blocks submission until filled.
- `<select>` + `<option>` — dropdown for "How do you know me?"
- `<input type="radio">` grouped by shared `name` — only one can be selected per group.
- `<label for="id">` paired to each input's matching `id` — clicking the label focuses the input; also required for screen readers to announce what a field is for.

## 7. Media Embedding — Two Different Techniques on Purpose

- `<iframe>` — the real YouTube song + video embeds. Correct tag for embedding another site's player.
- `<audio>`/`<video>` with multiple `<source>` children — a *separate* demo of the format-fallback technique (browser plays the first `<source>` it supports, ignores the rest). Kept visually separate (`.demo-callout`) so it doesn't get mistaken for the actual content — and it currently has no real files behind it (see README's "Known Gap").

## 8. CSS Architecture

- **Custom properties (`:root { --name: value; }`)** — every color/font/spacing value defined once, reused via `var(--name)`. Change a hex code in one place, the whole site updates.
- **Flexbox** (`display: flex`) — used for the nav bar, badge rows, chip lists, form radio groups: anywhere items sit in a single row/column and need even spacing (`gap`).
- **CSS Grid** (`display: grid`, `grid-template-columns: repeat(auto-fit, minmax(...))`) — used for the About two-column split, the hobby card grid, the badge row: anywhere content needs to wrap into a responsive multi-column layout without media-query breakpoints doing all the work.
- **`clamp(min, preferred, max)`** — used on heading `font-size`. One line replaces "one font-size for desktop + a separate override in the phone media query."
- **`aspect-ratio: 16/9`** — keeps the YouTube iframe's shape correct at any width without JS recalculating on resize.

## 9. Accessibility Details Worth Being Able to Name

- Empty `alt=""` on purely decorative images (seals sitting next to text that already says the same thing) vs. descriptive `alt="Photo of..."` on meaningful images — empty alt tells a screen reader to skip it, not that it's an error.
- `aria-hidden="true"` on decorative emoji icons (🎮, 🎬, etc.) — the emoji is visual flavor, not information; the text label next to it already carries the meaning.
- `aria-label="Page sections"` on the `<nav>` — disambiguates this nav from any other nav that might exist on a page with more than one.
- `prefers-reduced-motion` media query — turns off the sunburst spin, hover-lift transition, and smooth scroll for anyone with that OS-level accessibility setting on.

## 10. The One Media Query

`@media (max-width: 640px)` — a single phone breakpoint collapses the two-column grids to one column and tightens spacing. Everything above 640px shares one layout; nothing in between has special-cased rules.

---
*Compiled by KianoRoku18Ino*
