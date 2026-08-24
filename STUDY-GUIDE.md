# Study Guide — WS101 Personal Web Page

Every HTML tag, attribute, and CSS feature actually used in `260003GalaridoPortfolio.html` / `260003GalaridoStyle.css`, organized by what it does and where it shows up on the page. This is a reference for the code as it exists right now — not a general language reference (see `html-complete-reference.html` / `css-complete-reference.html` / `Web_Fundamentals_Mastery_Reference.html` for that).

## 1. Document Structure & Metadata

| Tag/Attribute | What it does | Where |
|---|---|---|
| `<!DOCTYPE html>` | Tells the browser "render this as modern HTML," not some legacy quirks mode | Line 1 |
| `<html lang="en">` | Declares the page's language — screen readers use this to pick the right pronunciation, browsers use it for spell-check/translate prompts | Root tag |
| `<meta charset="UTF-8">` | Character encoding — without this, special characters (the em dashes, curly quotes, non-English text) can render as garbage | `<head>` |
| `<meta name="viewport" ...>` | Tells mobile browsers to use the phone's real width instead of faking a zoomed-out desktop layout first | `<head>` |
| `<meta name="description" ...>` | The one-line summary search engines and link previews pull | `<head>` |
| `<title>` | The browser tab text — separate from anything visible in the page body | `<head>` |
| `<link rel="stylesheet" href="...">` | Connects the external CSS file — this is what makes it an *external* stylesheet rather than inline `<style>` | `<head>` |

## 2. Semantic Layout

| Tag | Used for | Why this over a `<div>` |
|---|---|---|
| `<header>` | The sticky top nav bar | Marks "introductory content for this page" |
| `<nav>` | The 4 section links inside the header | Tells assistive tech this block is for navigation |
| `<main>` | Everything between the nav and the footer | One per page — the primary content |
| `<section>` | Hero, About, Academics, Interests, Connect | Each is a distinct topic, each gets an `id` so nav links can jump to it |
| `<footer>` | The closing block with my name and the QCU seal | Semantically "closing content" for the page |

**The core idea:** semantic tags carry meaning a `<div>` doesn't. A screen reader announces "navigation" or "main content" from these tags alone — a `<div>` announces nothing.

## 3. Text Content & Semantics

- **`<h1>` / `<h2>` / `<h3>`** — one `<h1>` (my name, in the hero), `<h2>` per section title, `<h3>` for sub-labels inside a section (`Quick Facts`, `Student Organizations`, `Hobbies`). Headings nest by importance, not by font size — CSS handles how big they look.
- **`<p>`** — every ordinary paragraph of text.
- **`<strong>`** — bold with actual semantic weight (marks something as important), used inside the QCU Vision/Mission/Values box (`<strong>Vision:</strong>`). Different from just making text visually bold with CSS — `<strong>` means something to assistive tech too.
- **`<em>`** — emphasis with actual semantic weight, the italic equivalent of `<strong>`. Used once, in the bio paragraph (`<em>genuinely</em> curious`), the same way you'd naturally stress that word out loud.
- **`<blockquote>`** — a quotation set apart from the surrounding text. Used for my personal motto in About Me, styled as a pull-quote (left border, italic serif). Pulled from my own words in the bio paragraph right above it rather than inventing something new, since a motto should actually sound like me.
- **`<address>`** — the specific tag for "contact information belonging to whoever owns this page." Wraps the direct-links list in Connect (Gmail, GitHub, Facebook, X) instead of leaving it a bare `<ul>`. Browsers italicize `<address>` by default; I turned that off in the CSS since nothing else on the page uses italic that way.
- **`<abbr title="...">`** — wraps an abbreviation and gives it a hover tooltip with the full expansion. Used on:
  - `BSIT` → Bachelor of Science in Information Technology (hero)
  - `WS101` → Web Systems and Technologies 1 (hero tagline)
  - `NSTP` → National Service Training Program (About Me badge)
  - `ROTC` → Reserve Officers' Training Corps (About Me badge)
  - `QCU` → Quezon City University (campus photo caption)
- **`<span>`** — a generic inline wrapper with no meaning of its own, used only when I need to style a piece of text differently than the text around it (`.eyebrow`, `.fact-label`, `.fact-value`, `.status-tag`) and no more specific tag fits.

## 4. Lists — Two Kinds, Used On Purpose

- **`<ul>`** — used for the Quick Facts list, the Student Organizations pairs' outer container is actually a `<dl>` not `<ul>` (see below), and the Connect page's direct-links list. Unordered because nothing about the order carries meaning.
- **`<dl>` / `<dt>` / `<dd>`** — a description list: `<dt>` is a term, `<dd>` right after it is that term's description. Used for:
  - The Gaming hobby's full list of currently-playing games (`<dt>` = game name + link, `<dd>` = genre/publisher)
  - The Anime & Movies hobby's two real picks
  - The Student Organizations list in About Me (`<dt>` = org name + link + status tag, `<dd>` = one-line description)
  
  This is the correct tag here specifically because each item is a **name paired with a description**, not just a flat list of equal items — that pairing is exactly what `<dl>` exists to express.

No `<ol>` is used anywhere on the page currently — nothing in the content is inherently sequential/ordered in a way that would change meaning if reordered.

## 5. Tables — Real Tabular Data Only

`<table>` with `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `<th scope="col">`, and `<th scope="row">` is used **only** for the Grade 10/11/12 report cards, because that data genuinely has a row × column relationship (subject × quarter). Everywhere else on the page that might look list-like (hobbies, orgs, facts) uses `<ul>` or `<dl>` instead, because there's no real grid of rows and columns to represent — using a `<table>` there would be the wrong tag for the shape of the data.

- `scope="col"` / `scope="row"` — tells a screen reader which header a given cell belongs to, since sighted users get that from position alone but a screen reader can't "see" a column.
- `colspan="4"` — used on the `Core` / `Applied & Specialized` group-header rows so one cell visually spans the full table width.

## 6. Images & Captions

- **`<img src="..." alt="...">`** — every photo and seal on the page. `alt=""` (empty) is used deliberately on purely decorative images sitting right next to text that already says the same thing (the QCU seal in the badge, next to the word "Quezon City University") — an empty `alt` tells a screen reader to skip it, not that something's broken. Descriptive `alt` text is used everywhere the image itself carries information a screen reader user would otherwise miss (the profile photo, the school building photos).
- **`<figure>` / `<figcaption>`** — wraps the QCU campus photo, the College of Computer Studies seal, and the Grade 10/11 school photos. `<figure>` groups an image with content that explains it; `<figcaption>` is the specific tag for that caption text — using a plain `<p>` next to an image wouldn't tell a screen reader the two are connected, `<figcaption>` inside `<figure>` does.

## 7. Forms — Full Input Surface

The Connect section's form covers 9 distinct input types plus `<select>` and `<textarea>`:

| Type | Field | What makes it the right choice |
|---|---|---|
| `text` | Your Name | Plain free text, no format to validate |
| `email` | Your Email | Browser checks it looks like a real email before allowing submit |
| `url` | Your Website | Same idea as `email` — checks it looks like a real web address |
| `tel` | Your Phone | No format-checking (phone formats vary too much by country), but tells mobile browsers to show a numeric keypad |
| `date` | Best Date To Reach You | A real date picker instead of typed text — there's no wrong format to type |
| `radio` | Rain or Sunshine? | Only one answer possible — both options share `name="Weather preference"`, which is what groups them |
| `checkbox` | Best Way To Reach You Back | More than one can be true at once, so each has its own separate `name` instead of sharing one |
| `range` | Hype level (1–10) | A slider instead of typed text — `min`/`max`/`value` set the two ends and the starting point |
| `submit` | Send Message | Triggers form submission |

Other form elements:
- **`<label for="id">`** — paired to a matching input `id`; clicking the label focuses the input, and it's required for screen readers to announce what a field is for.
- **`<fieldset>` + `<legend>`** — the correct pair for "these inputs all belong to one question." `<legend>` is the question text, everything inside the `<fieldset>` is the set of possible answers. Used for the radio group and the checkbox group — a plain `<label>` isn't valid here since a *group* of radios has no single input to attach a label to.
- **`<select>` + `<option>`** — the dropdown for "How Do You Know Me?"
- **`<textarea>`** — the free-text message box.
- **`required`** — blocks submission until the field is filled (Name, Email).
- **`placeholder`** — the greyed-out example text shown before typing (Website, Phone, Message).
- **`action="mailto:..."` + `enctype="text/plain"`** — this page has no backend server, so instead of submitting to a server, the form opens the visitor's own email app with the fields pre-filled. That's the ceiling of what a static HTML form can do without something server-side behind it.

## 8. Zero-JavaScript Interactivity

**`<details>` / `<summary>`** is the one tag doing all of the page's "click to expand" behavior — the QCU Vision/Mission/Values box, all three grade-level report cards, and all five hobby boxes. The browser handles open/closed state entirely on its own; no JavaScript anywhere on this page.

## 9. Links

**`<a href="...">`** — two distinct patterns:
- **In-page navigation** (`href="#about"`) — jumps to the matching `id=""` further down the same page. Combined with `scroll-behavior: smooth` in the CSS, this animates instead of jumping instantly — that CSS line is the *only* reason it animates.
- **External links** (`target="_blank" rel="noopener"`) — every link that leaves the page (org Facebook pages, game official sites, GitHub, social links). `target="_blank"` opens a new tab; `rel="noopener"` is a security measure that stops the new tab from getting a reference back to this page.

## 10. CSS Architecture

- **Custom properties (`:root { --name: value; }`)** — every color defined once at the top, reused everywhere via `var(--name)`. The palette (`--navy`, `--navy-deep`, `--accent-blue`, `--accent-orange`) uses CSS's built-in named colors (`steelblue`, `midnightblue`, `royalblue`, `orangered`) chosen as the closest readable match to QCU's real brand blue/orange — a named color can't hit their exact hex value, but it reads as plain English right where it's defined instead of a hex code. Change a color once at the top, the whole page updates.
- **The universal reset (`* { box-sizing: border-box; margin: 0; padding: 0; }`)** — removes every browser's own default spacing so styling starts from a predictable blank slate, rather than fighting each browser's different defaults.
- **Flexbox (`display: flex`)** — used anywhere content sits in a single row or column and needs even spacing: the nav bar, the QCU/ROTC badges, the badge cards, the fact list rows, the radio/checkbox groups.
- **Grid (`display: grid`)** — used once, for the two-column Connect layout (form beside the link list), which collapses to one column under the phone-width media query.

## 11. Visual Details

- **`border-radius`** — rounds corners; `999px` specifically is a common trick for "however tall this element is, round it into a full pill/circle shape" (used on the mini-badges, status tags, and the profile photo).
- **`object-fit: cover`** — crops a photo to fill its box without squishing or stretching it out of proportion (profile photo, school photos).
- **`box-shadow`** — the soft drop shadow under the profile photo.
- **`position: sticky`** — keeps the top nav visible while scrolling, without needing JavaScript to track scroll position.
- **`:hover`** — the color/border changes on links, badges, and the submit button when a mouse points at them.
- **`:focus-visible`** — a visible outline on links, buttons, and form fields when navigated to by keyboard (Tab key) specifically — not on a mouse click. This is what makes the page usable without a mouse.
- **`transition`** — makes the `:hover` and `:focus-visible` changes ease smoothly instead of snapping instantly. Paired with `:hover`/`:focus-visible` everywhere those exist.
- **`:nth-child(even)`** — the alternating light-grey stripe on every other table row, done in pure CSS with no class needed on each row.

## 12. Responsive Design

One media query: `@media (max-width: 640px)` collapses the Connect section's two-column grid into one column on phone-width screens. Everything else on the page is already narrow (a single centered `.wrap` column, `max-width: 760px`), so this is the only breakpoint the layout actually needs.

## 13. Accessibility Details Worth Naming

- Empty `alt=""` vs. descriptive `alt="..."` — covered in section 6.
- `:focus-visible` outlines — covered in section 11.
- `<label for="">` on every form field — covered in section 7.
- `scope="col"` / `scope="row"` on table headers — covered in section 5.
- Semantic landmark tags (`header`, `nav`, `main`, `footer`) — covered in section 2.

---
*Compiled by KianoRoku18Ino*
