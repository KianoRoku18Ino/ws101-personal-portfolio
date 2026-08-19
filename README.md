# WS101 Activity 1 — Personal Web Page

A hand-written HTML + CSS personal web page built for **Web Systems and Technologies 1 (WS101)**, Quezon City University. No frameworks, no build tools, no JavaScript — every interactive-feeling piece (smooth nav scroll, expandable grade tables, hover lifts) is done with plain HTML and CSS features the browser already supports natively.

## Live Demo

Not yet deployed. Once GitHub Pages is turned on for this repo (Settings → Pages → Deploy from branch → `main` / `root`), the link goes here.

## Sections

| Section | What's in it |
|---|---|
| Hero | Name, program, a pure-CSS rotating sunburst behind the profile photo |
| About Me | Bio, QCU/ROTC badges, hobby cards, currently-playing games |
| Academics | Honor badges + a Grade 10→12 report-card timeline using native `<details>` |
| Projects | Cards linking out to three of my real GitHub repos + their live demos |
| Media | A real YouTube embed, plus a small demo of the `<audio>`/`<video>` multi-`<source>` fallback technique |
| Connect | A `mailto:` contact form and direct links (Gmail, GitHub, Facebook) |

## File Structure

```
260003GalaridoPortfolio.html   — the page
260003GalaridoStyle.css        — all styling (external stylesheet, per the assignment's naming rule)
assets/
  images/                      — profile photo, QCU/ROTC/school seals
  audio/, video/                — placeholders for the format-fallback demo (see note below)
STUDY-GUIDE.md                 — a tag-by-tag / property-by-property breakdown of every HTML & CSS concept used here, for reviewing before an exam or quiz
```

## Known Gap

The `<audio>`/`<video>` fallback demo in the Media section references clip files under `assets/audio/` and `assets/video/` that don't exist yet — it's there to demonstrate the multi-`<source>` technique, not to be the real content. Drop a short clip in (`rain-clip.mp3`/`.ogg` and `rain-clip.mp4`/`.webm`, or rename the `<source>` paths in the HTML to something else, e.g. a short morning-prayer clip) before submitting if the activity requires it to actually play something.

## Tech

Plain HTML5 + CSS3. Google Fonts (Spectral, Public Sans, JetBrains Mono). No JavaScript, no build step — open `260003GalaridoPortfolio.html` directly in a browser to view.

---
*Compiled by KianoRoku18Ino*
