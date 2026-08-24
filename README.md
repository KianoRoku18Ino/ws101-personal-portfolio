# WS101 Activity 1 — Personal Web Page

A hand-written HTML + CSS personal web page built for **Web Systems and Technologies 1 (WS101)**, Quezon City University. No frameworks, no build tools, no JavaScript — every show/hide box, smooth nav scroll, and form validation runs on plain HTML and CSS the browser already supports natively.

## Live Demo

https://kianoroku18ino.github.io/ws101-personal-portfolio/

## Sections

| Section   | What's in it                                                                                                                                                                                                                                                                                      |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hero      | Name, program, profile photo                                                                                                                                                                                                                                                                      |
| About Me  | Bio, QCU/ROTC/CCS links and photos, QCU Vision/Mission/Shared Values (collapsible), the QCU Hymn (YouTube embed, credited), the Philippine National Anthem (local audio, credited), quick facts, and student orgs I'm interested in joining                                                       |
| Academics | Honor cards + Grade 10→12 report cards, each inside a `<details>` box, with real school photos (all captioned with `<figure>`/`<figcaption>`)                                                                                                                                                     |
| Interests | Five hobbies, each its own `<details>` box, several split into sub-groups with `<h4>` — Gaming (currently-playing list + genres I enjoy), Anime & Movies (two real favorites + genres watched), Reading (books, light novels, manga, manhwa by genre), Music (artists I've listened to, by genre) |
| Connect   | A `mailto:` contact form (text, email, url, tel, date, radio, checkbox, range, select, textarea) and direct links (Gmail, GitHub, Facebook, X)                                                                                                                                                    |

## Study Guide

`STUDY-GUIDE.md` — a full tag-by-tag, attribute-by-attribute breakdown of everything used in this project and why, for reviewing before a quiz or a walkthrough defense.

## File Structure

Two matching pairs — same content, different filenames, because GitHub Pages needs `index.html` to auto-serve while the assignment needs the required naming convention:

```
260003GalaridoPortfolio.html   — the page (assignment naming convention)
260003GalaridoStyle.css        — its stylesheet
index.html                     — identical copy, for GitHub Pages
style.css                      — identical copy, for GitHub Pages
assets/images/                 — profile photo, QCU/ROTC/CCS seals, QCU campus + school photos
assets/audio/                  — Philippine National Anthem MP3 recording
```

## Tech

Plain HTML5 + CSS3. Google Fonts (Spectral, Public Sans). Color palette uses CSS named colors (`steelblue`, `midnightblue`, `royalblue`, `orangered`, `bisque`) chosen as the closest readable approximations of QCU's actual brand blue/orange — not exact hex matches, but each color is a plain English word right where it's defined instead of a hex code. No JavaScript, no build step — open either HTML file directly in a browser to view.

---

_Compiled by KianoRoku18Ino_
