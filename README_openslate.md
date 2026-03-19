# OpenSlate

**A free, open-source filmmaking toolkit for writers and directors.**

[![Live](https://img.shields.io/badge/live-weopenslate.vercel.app-c9a84c?style=flat-square)](https://weopenslate.vercel.app)
[![License](https://img.shields.io/badge/license-MIT-c9a84c?style=flat-square)](LICENSE)
[![Built With](https://img.shields.io/badge/built%20with-HTML%20%2F%20Next.js-c9a84c?style=flat-square)]()
[![Part of OpenSlate](https://img.shields.io/badge/status-live-c9a84c?style=flat-square)]()

---

OpenSlate is a suite of professional filmmaking tools — built from scratch, deployed globally, and permanently free. Write your script, plan your shoot, frame your shots. No subscriptions. No paywalls. No excuses.

**[→ weopenslate.vercel.app](https://weopenslate.vercel.app)**

---

## The Suite

### [OpenWrite](https://github.com/kazim-45/openwrite) — Screenwriting Software
**[openwrite.vercel.app](https://openwrite.vercel.app)**

Professional screenplay editor that runs in a single HTML file. Zero dependencies, zero installation. Open a browser and start writing.

- Industry-standard WGA format — scene headings, action, character, dialogue, transitions
- Smart autocomplete for scene headings, character names, and transitions
- Real-time Script Doctor — flags formatting and pacing issues as you write
- Selection-based formatting toolbar — Bold, Italic, Underline
- Clean PDF export — no browser headers, no footers, just the screenplay
- Title page generator — separate from the editor, prepended on export
- Autosave to localStorage, dark/light mode, focus mode, revision mode
- Full mobile support — bottom element bar, drawer sidebars, swipe gestures

---

### [OpenFrame](https://github.com/kazim-45/openframe) — Pre-Production Suite
**[openframev1.vercel.app](https://openframev1.vercel.app)**

Complete pre-production tool built with Next.js. Everything you need from script breakdown to shoot day.

- Storyboard editor with four visual modes per panel: SVG templates, freehand drawing, reference upload, AI image generation
- Shot list auto-generated from storyboard data
- Character profiles, location records, mood board
- Full call sheet — shoot dates, crew list, production notes
- PDF exports for storyboard, shot list, and call sheet
- JSON project backup and restore
- Full mobile support

---

### OpenView — Viewfinder & Shot Planning *(Coming Soon)*

Virtual viewfinder, aspect ratio calculator, lens reference, shot size guide. The third tool in the OpenSlate suite.

---

## Philosophy

Professional filmmaking tools cost hundreds of dollars a year. WriterDuet, Celtx, Shot Designer, StudioBinder — all paywalled. OpenSlate exists because the tools shouldn't cost more than the film.

---

## Tech Stack

| Tool | Stack |
|---|---|
| OpenWrite | Vanilla HTML / CSS / JS |
| OpenFrame | Next.js 14 · Tailwind CSS |
| Landing Page | Vanilla HTML / CSS / JS |
| Hosting | Vercel |
| Storage | localStorage (no backend) |
| AI Images | Pollinations.ai (free, no key) |

---

## Roadmap

- [ ] Import script from OpenWrite into OpenFrame — one-click scene population
- [ ] Google authentication — NextAuth.js
- [ ] Cloud saves — Supabase per-user storage
- [ ] OpenView — viewfinder and shot planning tool
- [ ] SLATE — unified app merging all tools under one login
- [ ] Real-time collaboration
- [ ] Custom domain — `openslate.app`

---

## Repos

| Repo | Description |
|---|---|
| [kazim-45/openslate](https://github.com/kazim-45/openslate) | Landing page |
| [kazim-45/openwrite](https://github.com/kazim-45/openwrite) | Screenwriting tool |
| [kazim-45/openframe](https://github.com/kazim-45/openframe) | Pre-production suite |

---

## License

MIT — use it, fork it, ship it. Credit appreciated, not required.

---

## Author

Built by **Kazim** — 17-year-old developer and filmmaker from Lahore, Pakistan.

[GitHub](https://github.com/kazim-45) · [OpenSlate](https://weopenslate.vercel.app) · [OpenWrite](https://openwrite.vercel.app) · [OpenFrame](https://openframev1.vercel.app)

---

*From first word to final shot.*
