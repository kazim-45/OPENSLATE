# OPENSLATE

[![Live](https://img.shields.io/badge/live-weopenslate.vercel.app-c9a84c?style=flat-square)](https://weopenslate.vercel.app)
[![License](https://img.shields.io/badge/license-MIT-c9a84c?style=flat-square)](LICENSE)
[![Built With](https://img.shields.io/badge/built%20with-HTML%20%2F%20Next.js-c9a84c?style=flat-square)]()
[![Part of OpenSlate](https://img.shields.io/badge/status-live-c9a84c?style=flat-square)]()


> **Free, open, browser-based filmmaking tools for independent creators.**

OPENSLATE is a suite of professional-grade tools built for filmmakers who shouldn't need to pay industry prices to work at an industry standard. Every tool runs entirely in the browser — no installs, no subscriptions, no accounts required.

```
weopenslate.vercel.app          ← Suite landing page
```

---

## The Suite

| Tool | Live URL | Purpose |
|---|---|---|
| **OPENWRITE** | [openwrite.vercel.app](https://openwrite.vercel.app) | Screenplay writing & formatting |
| **OPENFRAME** | [openframev1.vercel.app](https://openframev1.vercel.app) | Storyboarding & pre-production |
| **OPENVIEW** | [openview.vercel.app](https://openview.vercel.app) | Digital viewfinder & shot reference |

Each tool is independently deployable, shares the same visual language (dark grey / black + neon blue `#00CFFF`), and is built on the same stack.

---

## Stack (All Tools)

| Layer | Choice |
|---|---|
| Framework | Next.js 14 (App Router, static export) |
| Language | TypeScript |
| Styling | Tailwind CSS + CSS custom properties |
| Fonts | Bebas Neue (display) · JetBrains Mono (UI/code) |
| Deployment | Vercel (zero-config, all static) |
| Storage | IndexedDB / localStorage (client-only, no backend) |

---

---

## OPENWRITE

**Screenplay writing with industry-standard formatting — in the browser.**

```
openwrite.vercel.app
```

### What it does

OPENWRITE formats screenplays to the Hollywood standard automatically as you type. Scene headings, action lines, character cues, dialogue, transitions — the correct formatting is applied based on context, so writers can focus on story rather than margins.

### Features

| Feature | Details |
|---|---|
| **Auto-formatting** | Detects and applies scene headings, action, character, dialogue, parenthetical, and transition elements |
| **Keyboard-driven** | Tab / Enter flow matches professional tools like Final Draft |
| **Dark writing mode** | Distraction-free full-screen editor with minimal chrome |
| **Export** | PDF export with print-ready margins and Courier Prime font |
| **Local persistence** | Script saves to `localStorage` automatically |
| **Word / page count** | Live page estimate (1 page ≈ 1 minute screen time) |

### Folder Structure

```
openwrite/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── components/
│   ├── Editor.tsx          # Core screenplay editor
│   ├── ElementToolbar.tsx  # Scene / action / char selector
│   └── ExportButton.tsx    # PDF generation
└── lib/
    └── formatting.ts       # Auto-format logic
```

---

---

## OPENFRAME

**Storyboard creation and pre-production planning — no drawing skill required.**

```
openframev1.vercel.app
```

### What it does

OPENFRAME is the visual pre-production layer of OPENSLATE. Directors and cinematographers use it to plan shots before stepping on set — building storyboards from SVG panel templates, free-hand sketches, and AI-generated reference images, then exporting the whole board as a PDF.

### Features

| Feature | Details |
|---|---|
| **SVG panel templates** | Preset shot compositions (close-up, wide, two-shot, POV, etc.) |
| **Freehand canvas** | Draw directly on panels with pressure-sensitive brush strokes |
| **AI image generation** | Text-to-image via [Pollinations.ai](https://pollinations.ai) — free, no API key |
| **PDF export** | Full storyboard exported as a print-ready PDF |
| **Shot notes** | Per-panel text annotations for director's notes, lens, action description |
| **Panel reordering** | Drag-and-drop panel sequence |
| **Local persistence** | Board state saves to `localStorage` |

### AI Image Generation

OPENFRAME uses **Pollinations.ai** for zero-cost, zero-signup AI image generation. Type a shot description ("extreme close-up of hands loading a revolver, film noir lighting") and a reference image generates directly into the panel.

```
https://image.pollinations.ai/prompt/{encoded_prompt}
```

No API key. No rate limit for reasonable use.

### Folder Structure

```
openframe/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
├── components/
│   ├── Board.tsx            # Panel grid + drag-drop
│   ├── Panel.tsx            # Individual storyboard panel
│   ├── DrawCanvas.tsx       # Freehand drawing layer
│   ├── AIImageGen.tsx       # Pollinations.ai integration
│   └── ExportPDF.tsx        # jsPDF export
└── lib/
    └── templates.ts         # SVG panel compositions
```

---

---

## OPENVIEW

**A professional digital viewfinder for the filmmaker's phone.**

```
openview.vercel.app
```

### What it does

OPENVIEW turns any smartphone into a director's viewfinder. Select a lens and aspect ratio, frame the shot with overlay guides, drop marks on blocking positions, capture reference photos with overlays baked in, and compare live view against those references — all before a camera ever rolls.

### Features

#### Camera

| Feature | Details |
|---|---|
| **Rear camera priority** | Requests `facingMode: environment`, falls back to front |
| **HTTPS aware** | Handles iOS Safari's HTTPS requirement; prompts on user gesture not page load |
| **Permission denied** | Full error screen with per-browser recovery instructions (iOS / Android / Desktop) |
| **Mock mode** | Continue without a camera for desktop use |
| **60fps stream** | No memory leaks — tracks stopped on component unmount |

#### Lens Simulation

Simulates field-of-view crop via `transform: scale` on the live video element. Scales are mapped to real FOV ratios relative to 50mm on a full-frame sensor.

| Lens | Scale | Equivalent |
|---|---|---|
| 24mm | ×0.72 | Wide angle |
| 35mm | ×0.88 | Semi-wide |
| 50mm | ×1.00 | Normal (reference) |
| 85mm | ×1.35 | Portrait |
| 135mm | ×1.90 | Telephoto |

Switching lenses triggers a 600ms spring-eased scale transition and a 2-second HUD label flash.

#### Aspect Ratio Guides

Black letterbox bars animate in/out with CSS transitions to enforce the selected ratio.

| Ratio | Use case |
|---|---|
| 16:9 | Standard broadcast / streaming |
| 2.39:1 | Anamorphic / CinemaScope |
| 1.85:1 | Flat theatrical |
| 4:3 | Classic / archival |
| 1:1 | Square / social |

#### Framing Overlays

Rendered every frame on a `<canvas>` element positioned above the video via `requestAnimationFrame`. All toggleable.

| Overlay | Details |
|---|---|
| **Rule of Thirds** | 2×2 grid with intersection dots |
| **Crosshair** | Dashed center lines + 30×30px square center mark |
| **Golden Spiral** | Polar-coordinate Fibonacci spiral, drawn by stepping 720° with exponential radius growth (`r = maxR × 1.0055^i`) |

#### Angle Presets

Visual overlay guides (no camera movement — the user physically repositions):

| Preset | Guide |
|---|---|
| Eye Level | Single horizontal line across center |
| High Angle | Upward arrow SVG |
| Low Angle | Downward arrow SVG |
| Dutch Tilt | Three rotating lines at −12° |
| Bird's Eye | Concentric circle target |
| Worm's Eye | Vertical perspective lines |

#### Director's Marks

Enable **Mark Mode** in the settings panel, then tap anywhere on the live view to drop a coloured dot labelled A, B, C… Marks are colour-coded (red, amber, blue, green, orange, purple), show a floating label, and are removable by tapping the dot. Haptic feedback on drop via `navigator.vibrate(20)`.

#### Capture & Reference Library

| Step | What happens |
|---|---|
| Tap capture | Composites video frame + overlay canvas onto a hidden `<canvas>` |
| Download | PNG saved to device downloads / photos |
| Library | Shot saved to **IndexedDB** with lens, aspect ratio, angle metadata |
| Persistence | Library survives page reloads |
| Recall | Tap a library shot → restores its lens / aspect / angle settings + starts compare mode |
| Delete | Per-item delete with immediate IndexedDB sync |

#### Compare Mode

Tap a library shot to overlay it semi-transparently on the live view using `mix-blend-mode: overlay`. Useful for matching framing between setups or across shooting days.

#### Exposure Meter

Every animation frame, the live video is drawn onto a hidden 32×18 canvas. Average luminance is computed from raw pixel data using the standard perceptual weighting (`R×0.299 + G×0.587 + B×0.114`), then smoothed with a 93% exponential moving average:

```
brightness = brightness × 0.93 + sample × 0.07
```

Meter renders as a 60px bar in the top HUD. Turns amber when overexposed.

#### Depth-of-Field Simulation

On 85mm and 135mm lenses, a radial CSS `backdrop-filter: blur(4px)` activates over a mask that leaves the centre clear and blurs the edges — simulating shallow DoF bokeh falloff.

#### UX Details

| Detail | Behaviour |
|---|---|
| **Auto-hide chrome** | All UI fades after 3.5s of inactivity; tap anywhere to restore |
| **Shutter sound** | Synthesised white-noise burst with exponential decay via Web Audio API — no audio file, respects silent mode |
| **Haptics** | `navigator.vibrate(20)` on Director's Mark drop |
| **Animated lens switch** | 600ms `cubic-bezier(0.16, 1, 0.3, 1)` spring |
| **Animated drawers** | Bottom drawers slide up with the same spring curve |
| **Safe area** | `env(safe-area-inset-bottom)` padding on toolbar for notch devices |
| **Touch targets** | All buttons minimum 44×44px |
| **PWA** | `manifest.json` enables Add to Home Screen (full-screen, no browser chrome) |

### Folder Structure

```
openview/
├── app/
│   ├── layout.tsx          # Font loading, viewport meta, PWA tags
│   ├── page.tsx            # Dynamic import (disables SSR for camera)
│   └── globals.css         # All styles — variables, animations, component CSS
├── components/
│   └── OpenView.tsx        # Entire viewfinder (~500 lines)
│                           #   Camera init + cleanup
│                           #   Overlay canvas render loop
│                           #   Lens / aspect / angle state
│                           #   Director's marks
│                           #   Capture + IndexedDB library
│                           #   All drawers + modals
├── public/
│   └── manifest.json       # PWA manifest
├── next.config.js          # Static export config
├── tailwind.config.js
└── README.md
```

### Local Development

```bash
npm install
npm run dev
# → http://localhost:3000
```

> Camera requires HTTPS on real devices. For on-device testing, deploy to Vercel (free) or use `ngrok http 3000`.

### Deploy

```bash
npm run build       # Static export → /out
vercel deploy       # Or: push to GitHub → import at vercel.com
```

---

---

## Design System

All three tools share the same visual identity.

### Colours

| Token | Hex | Use |
|---|---|---|
| `--film-black` | `#090909` | Page background |
| `--film-dark` | `#111111` | Surface |
| `--film-panel` | `#161616` | Drawers, modals |
| `--film-border` | `#252525` | Borders, dividers |
| `--film-blue` | `#00CFFF` | Primary accent, interactive |
| `--film-blue-dim` | `#0099BB` | Hover states |
| `--film-blue-glow` | `rgba(0,207,255,0.15)` | Selected backgrounds |
| `--film-red` | `#FF3D5A` | Destructive actions |
| `--film-amber` | `#FFB800` | Warnings, overexposure |
| `--film-text` | `#C8C8C8` | Body text |
| `--film-muted` | `#555555` | Placeholder, secondary text |

### Typography

| Role | Font | Weight |
|---|---|---|
| Display / headings | Bebas Neue | 400 |
| UI labels, body | JetBrains Mono | 300–600 |

### Motion

All transitions use the same spring curve: `cubic-bezier(0.16, 1, 0.3, 1)` — fast out, smooth settle. Duration 350–600ms depending on element size.

---

## Philosophy

Industry filmmaking software costs hundreds of dollars a year and locks features behind paywalls that independent filmmakers — especially those outside the US and Europe — simply can't afford. OPENSLATE exists because the tools to tell a story should be free.

Every tool in this suite is:
- **100% client-side** — no server, no database, no account
- **Open to deploy** — fork, self-host, modify freely
- **Mobile-first** — built for the phone in your pocket on set
- **Progressively enhanced** — works without optional features (camera, AI) if unavailable

---

## Roadmap

| Tool | Planned |
|---|---|
| OPENWRITE | Collaboration mode (WebRTC), revision tracking, fountain import |
| OPENFRAME | Shot list export, timeline view, multi-board projects |
| OPENVIEW | Gyroscope-assisted horizon lock, multiple camera support, shot data export to OPENFRAME |
| Suite | Unified project format linking script scenes → storyboard panels → reference shots |

---

## Author

Built by **Kazim** · [github.com/kazim-45](https://github.com/kazim-45)

> *"Make industry-grade tools freely accessible."*
