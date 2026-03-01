# 🌍 World Radio

<div align="center">

![World Radio Banner](https://img.shields.io/badge/🌍_World_Radio-Stream_the_World-667eea?style=for-the-badge&labelColor=0a0e1a)

[![License](https://img.shields.io/badge/License-MIT-764ba2?style=flat-square)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Radio Browser API](https://img.shields.io/badge/API-Radio--Browser.info-11998e?style=flat-square)](https://www.radio-browser.info/)
[![PWA Ready](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=flat-square&logo=pwa&logoColor=white)]()
[![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-success?style=flat-square)]()
[![Responsive](https://img.shields.io/badge/Responsive-Mobile_First-blue?style=flat-square)]()

<br/>

> **Stream thousands of live radio stations worldwide — without installing a single dependency.**  
> Discover, play, and organize your favorite stations from every corner of the globe.

<br/>

[🎧 Live Demo](#) · [📖 Documentation](#documentation) · [🐛 Report a Bug](../../issues) · [💡 Request Feature](../../issues)

<br/>

![World Radio Screenshot](https://img.shields.io/badge/Screenshot-Coming_Soon-94a3b8?style=flat-square)

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🌍 **Global Coverage** | Browse stations from every country, sorted by popularity |
| 🔍 **Smart Search** | Search simultaneously by name, tag, or radio frequency (FM/AM/MHz) |
| 🎵 **Immersive Player** | Fixed bottom player with real-time audio visualizer |
| ⭐ **Favorites System** | Persist your favorite stations across sessions via `localStorage` |
| 📻 **Live Playlist** | Queue multiple stations and navigate with prev/next controls |
| 😴 **Sleep Timer** | Auto-stop music after 15 min → 2 hours, with live countdown |
| 🌙 **Dark / Light Theme** | Toggle between a dark cosmic theme and a clean light mode |
| 🔊 **Volume Control** | Smooth range slider with immediate audio feedback |
| 📊 **Quality Filtering** | Auto-filters dead streams, low-bitrate, and duplicate entries |
| 📱 **Fully Responsive** | Mobile-first design, works on all screen sizes |
| ⚡ **Zero Dependencies** | Pure HTML/CSS/JS — no Node.js, no npm, no build step |

---

## 🚀 Getting Started

### Prerequisites

- Any modern web browser (Chrome 80+, Firefox 75+, Safari 14+, Edge 80+)
- An internet connection (streams radio stations live)

### Installation

**Option 1 — Direct open (simplest)**
```bash
# Clone the repository
git clone https://github.com/FarTekTV/world-radio.git

# Navigate into the folder
cd world-radio

# Open directly in your browser
open index.html
```

**Option 2 — Local HTTP server (recommended for audio context)**
```bash
# Using Python 3
python3 -m http.server 8080

# Using Node.js (npx)
npx serve .

# Using PHP
php -S localhost:8080
```
Then visit `http://localhost:8080` in your browser.

**Option 3 — GitHub Pages / Netlify**

Simply push to a GitHub repository and enable **GitHub Pages** from the repo settings. No build process required.

---

## 🎮 Usage

### Browse by Country
1. Open the app — all countries are listed, sorted by number of available stations
2. Click on any country card to expand it and load its stations
3. Click **▶ Play** on any station to start streaming

### Search for a Station
- Type a station name (e.g., `NRJ`, `BBC`) in the search bar
- Or type a frequency (e.g., `103.5 FM`, `88 MHz`)
- Results are fetched live from the Radio Browser API and quality-filtered automatically

### Player Controls
| Control | Action |
|---|---|
| `▶ / ⏸` | Play / Pause the current stream |
| `⏮ ⏭` | Previous / Next station in your playlist |
| `🔊 Slider` | Adjust volume |
| `▼ Reduce` | Minimize the player to a compact bar |
| `✕ Close` | Stop playback and close the player |

### Favorites
1. Click `☆` on any station card to add it to your favorites
2. Click `⭐ Favorites` in the header to see your saved stations
3. Click a favorite to instantly start playing it
4. Favorites are saved in your browser and persist across sessions

### Sleep Timer
1. Click `😴 Sleep Timer` in the header
2. Choose a preset (15 min, 30 min, 1 hour…) or enter a custom duration
3. The countdown displays live — music stops automatically when time is up
4. Click **Stop Timer** at any time to cancel

---

## 🏗️ Architecture

```
world-radio/
│
├── index.html          # Single-file application (HTML + CSS + JS)
└── README.md           # This file
```

### Tech Stack

| Layer | Technology |
|---|---|
| **Structure** | HTML5 Semantic |
| **Styling** | CSS3 (Custom Properties, Grid, Flexbox, Animations) |
| **Logic** | Vanilla JavaScript (ES2020+) |
| **Audio** | Web Audio API (visualizer) + HTML5 `<audio>` |
| **Data** | [Radio Browser API](https://www.radio-browser.info/) — free, open, no key required |
| **Storage** | Browser `localStorage` (favorites persistence) |
| **Fonts** | Google Fonts — Inter |

### API Endpoints Used

```
https://de1.api.radio-browser.info/json/countries
  → Fetches all countries with station counts

https://de1.api.radio-browser.info/json/stations/search?country=X&limit=100
  → Fetches stations for a specific country

https://de1.api.radio-browser.info/json/stations/search?name=X&limit=100
  → Searches stations by name

https://de1.api.radio-browser.info/json/stations/search?tag=X&limit=100
  → Searches stations by tag / frequency
```

> **Note:** The Radio Browser API is community-maintained and free to use. No API key required.

### Quality Filtering Logic

Before displaying stations, the app applies the following filters:
- ✅ Must have a valid, resolved stream URL
- ✅ URL must not be a web page (`.html`, `.php`, `.asp`)
- ✅ Bitrate must be ≥ 32 kbps (if reported)
- ✅ Station must have a valid name (≥ 2 characters)
- ✅ `lastcheckok` must not be `0` (dead stream)
- ✅ Votes must be ≥ -5 (not flagged as invalid)
- ✅ Deduplication by `url_resolved`
- ✅ Sorted by composite score: `(votes × 10) + (bitrate / 10)`

---

## 🎨 Design System

### Color Palette (Dark Mode)

| Variable | Value | Usage |
|---|---|---|
| `--bg-dark` | `#0a0e1a` | Main background |
| `--bg-card-dark` | `#151b2e` | Card backgrounds |
| `--text-dark` | `#e2e8f0` | Body text |
| `--accent` | `#667eea → #764ba2` | Primary gradient |
| `--success` | `#11998e → #38ef7d` | Play buttons |
| `--warning` | `#f093fb → #f5576c` | Alerts, close buttons |
| `--fav` | `#ffd89b → #19547b` | Favorites |

### Quality Badges
- 🟢 **HD** — Bitrate ≥ 128 kbps
- 🔵 **HQ** — Bitrate ≥ 64 kbps

---

## ⚙️ Configuration

All configuration is embedded directly in `index.html`. Key constants:

```javascript
// API base URLs
const API = "https://de1.api.radio-browser.info/json/stations/search";
const API_COUNTRIES = "https://de1.api.radio-browser.info/json/countries";

// Quality filter thresholds
const MIN_BITRATE = 32;           // kbps
const MAX_STATIONS_PER_COUNTRY = 30;
const SEARCH_LIMIT = 100;
```

To add country flags for additional countries, extend the `countryFlags` object:

```javascript
const countryFlags = {
  'France': '🇫🇷',
  'Your Country': '🏳️',
  // ...
};
```

---

## 🌐 Browser Compatibility

| Browser | Version | Status |
|---|---|---|
| Chrome / Chromium | 80+ | ✅ Full support |
| Firefox | 75+ | ✅ Full support |
| Safari | 14+ | ✅ Full support |
| Edge | 80+ | ✅ Full support |
| Opera | 67+ | ✅ Full support |
| iOS Safari | 14+ | ⚠️ May require user gesture to start audio |
| Android Chrome | 80+ | ✅ Full support |

> **Note:** The Web Audio API visualizer requires a user interaction (click) to initialize, in compliance with browser autoplay policies.

---

## 🔒 Privacy & Security

- **No backend** — all data fetched directly from the public Radio Browser API
- **No tracking** — no analytics, no cookies, no user accounts
- **No data sent** — favorites are stored only in your browser's `localStorage`
- **CORS** — audio streams use `crossorigin="anonymous"` for Web Audio API compatibility
- **CSP-friendly** — no inline event handlers, no `eval()`

---

## 🤝 Contributing

Contributions are welcome! Here's how to contribute:

```bash
# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feature/amazing-feature

# 3. Commit your changes
git commit -m 'feat: add amazing feature'

# 4. Push to the branch
git push origin feature/amazing-feature

# 5. Open a Pull Request
```

### Commit Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

```
feat:     New feature
fix:      Bug fix
style:    CSS/design changes
refactor: Code refactoring
docs:     Documentation updates
perf:     Performance improvements
```

---

## 🐛 Known Limitations

- Some radio streams may fail to load due to CORS restrictions on the stream server side
- The audio visualizer requires a user interaction before initializing (browser policy)
- The Radio Browser API may occasionally return stale entries — the quality filter mitigates this
- Sleep timer uses `alert()` for notification — a custom modal would be more elegant in production

---

## 📋 Roadmap

- [ ] PWA support (Service Worker + manifest for offline/install)
- [ ] Station metadata display (current song via Icy-Metadata)
- [ ] Keyboard shortcuts for player controls
- [ ] Custom station URL input
- [ ] Export/import favorites (JSON)
- [ ] Station history (recently played)
- [ ] Equalizer / audio effects
- [ ] Multiple audio codec fallback

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- [Radio Browser](https://www.radio-browser.info/) — free, open radio station directory API
- [Google Fonts](https://fonts.google.com/) — Inter typeface
- All the radio stations and communities that keep live radio alive worldwide

---

<div align="center">

**© 2025 Rafael ISTE — FarTekTV. All rights reserved.**

Made with ❤️ and lots of 📻

[![FarTekTV](https://img.shields.io/badge/FarTekTV-YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](#)
[![GitHub](https://img.shields.io/badge/Rafael_ISTE-GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/FarTekTV)

</div>
