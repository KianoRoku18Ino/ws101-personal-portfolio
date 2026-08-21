# WS101 Activity 1 — Personal Web Page

A hand-written HTML + CSS personal web page built for **Web Systems and Technologies 1 (WS101)**, Quezon City University. No frameworks, no build tools, no JavaScript — every show/hide box, smooth nav scroll, and form validation runs on plain HTML and CSS the browser already supports natively.

## Live Demo

https://kianoroku18ino.github.io/ws101-personal-portfolio/

## Sections

| Section | What's in it |
|---|---|
| Hero | Name, program, profile photo |
| About Me | Bio, QCU/ROTC links, QCU Vision/Mission/Shared Values (collapsible), quick facts, student orgs I'm applying to (honestly tagged "Interviewing," not claimed as membership) |
| Academics | Honor cards + Grade 10→12 report cards, each inside a `<details>` box, with real school photos |
| Interests | Five hobbies, each its own `<details>` box — Gaming expands into a full currently-playing list (`<dl>`, each title linking to its own official site); Anime & Movies holds my two real movie picks; Music is a placeholder for a future Spotify-style song/artist list |
| Connect | A `mailto:` contact form (text, email, url, radio, checkbox, range, select, textarea) and direct links (Gmail, GitHub, Facebook, X) |

## File Structure

Two matching pairs — same content, different filenames, because GitHub Pages needs `index.html` to auto-serve while the assignment needs the required naming convention:

```
260003GalaridoPortfolio.html   — the page (assignment naming convention)
260003GalaridoStyle.css        — its stylesheet
index.html                     — identical copy, for GitHub Pages
style.css                      — identical copy, for GitHub Pages
assets/images/                 — profile photo, QCU/ROTC seals, QCU campus + school photos
```

## Tech

Plain HTML5 + CSS3. Google Fonts (Spectral, Public Sans). Color palette pulled from QCU's own site (navy `#004E98`, accent blue `#2B6CB0`, accent orange `#FF6700`). No JavaScript, no build step — open either HTML file directly in a browser to view.

---
*Compiled by KianoRoku18Ino*
