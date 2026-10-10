# AnyScan209 — AI Context Document

> **Purpose:** This file provides complete context about the AnyScan209 project for AI assistants,
> developers, translators, and content generators. Read this before working on any AnyScan209 task.

---

## 1. Project Identity

| Field | Value |
|---|---|
| **App Name** | AnyScan209 |
| **Package Name** | `any.scan_209` |
| **Latest Version** | 2.01 |
| **Release Date** | 2026-09-21 |
| **Platform** | Android |
| **Category** | ScienceApplication / Universal Sensor Data Visualizer |
| **Author / Publisher** | Saeid Moghadam |
| **Contact Email** | ssmqqmss@gmail.com |
| **Official Website** | https://soifgo.github.io/AnyScan209/ |
| **GitHub Repository** | https://github.com/soifgo/AnyScan209 |
| **Community Forum** | https://github.com/soifgo/AnyScan209/discussions |
| **License / Price** | 100% Free — No ads, no in-app purchases, no data collection |
| **Copyright** | ©2025–2026 AnyScan209 — Built by Saeid Moghadam |
| **Primary Language** | English (Persian also supported natively) |
| **Supported Languages (UI)** | 42 languages via translate.js (see §9) |

---

## 2. One-Line Summary

AnyScan209 is a **free Android app** that turns a smartphone into a **universal 2D/3D sensor visualizer** for four internal sensors (magnetometer, barometer/altimeter, light, sound) and any external **0–1024** sensor data (Arduino/ESP via Bluetooth HC-05), with export to **OBJ, STL, CSV, PLY**.

---

## 3. Core Concept — The 0–1024 Range

Everything in AnyScan209 revolves around a single normalized data range: **0 to 1024**.

- **512** = neutral / center / balance point (especially in magnetometer mode)
- All four internal sensors are mapped into this range
- All external sensor data **must be pre-scaled by the user** to 0–1024 before sending via Bluetooth
- 2D/3D visualization, color palettes, gain, and export all operate on this range

### Gain (Internal Sensors Only)
- Smartphone magnetometers are typically **16-bit** (raw range **0–65,535**)
- **Gain** factor maps raw → 0–1024
- **Default Gain = 10** → neutral point 512, max sensitivity (auto-balanced via Balancer ⚖️ icon)
- **Lower Gain (9 → 1)** → less sensitivity, wider coverage
- At **Gain = 1**, every **64 raw units** = **1 unit** in the 0–1024 range
- External mode applies **no internal gain** — user must pre-scale

---

## 4. Four Internal Sensor Modes

Switching sensors: **Long-press the sensor icon** on the **Settings** page → select from list.

### 4.1 🧲 Magnetometer (default)
- **Uses:** compass/magnetometer sensor
- **Applications:** geophysical surveys, cavity/void detection, geological exploration, magnetic field visualization, metal & wire detection, educational experiments
- **Users:** researchers, geophysicists, treasure hunters, DIY enthusiasts
- **Note:** AC magnetic fields cause bidirectional gauge movement; DC fields cause one-directional deflection

### 4.2 ⛰️ Barometer / Altimeter
- **Uses:** barometric pressure sensor
- **Applications:** altitude measurement, surface topography mapping, floor-level surveys, outdoor elevation mapping
- **⚠️ WARNING:** Not all phones have a real barometer. The option may appear but return constant/no readings on budget devices. Most flagship and mid-to-high-end phones include a real barometer.

### 4.3 💡 Light Sensor
- **Uses:** ambient light sensor
- **Applications:** light intensity surveying, lighting installation analysis, greenhouse/agricultural mapping, photography/studio lighting, architectural lighting design
- **Users:** lighting engineers, greenhouse operators, photographers

### 4.4 🔊 Sound / Noise Meter
- **Uses:** microphone (SPL meter)
- **Applications:** noise mapping, industrial noise analysis, acoustic environment surveying, soundproofing verification, machine diagnostics, environmental acoustics
- **Users:** acoustic engineers, safety inspectors, industrial technicians

---

## 5. External Sensor Mode

- **Connection:** Serial Bluetooth (HC-05 or any SPP-compatible module)
- **Data format:** Plain numeric values 0–1024, sent via `Serial.println()` (one value per line)
- **Baud rate:** Configurable; long-press the **Export icon** to open advanced baud configuration
- **Cell editing:** Manual cell editing (slider + Record button) is only allowed in **External mode** or when **Bluetooth is disconnected**
- **User responsibility:** Pre-scale sensor output to 0–1024 in firmware (Arduino/ESP code)

### Example Arduino/BASCOM Integration
The site provides a conversion example from **BASCOM AVR** to **Arduino C++**:
- Reads analog value from pin A1
- Sends value via `Serial.println(analogValue)`
- Original BASCOM uses `$regfile = "m8adef.dat"`, `$crystal = 8000000`, ADC on channel 1
- Arduino version available with and without `INPUT_PULLUP`
- Proteus project file downloadable: `Proteuse_file.zip`

---

## 6. Scan Workflow

### 6.1 Creating a Scan
- **Grid size:** 8×8 up to **100×100 points**
- **Entry point:** Bottom-right corner
- **Direction:** Always starts **vertically (bottom → top)**
- **Two scan modes:**
  - **One-Way (Go/Go):** bottom→top, return to bottom, next column
  - **Zigzag (Go/Return):** bottom→top, then top→bottom in next column (faster, recommended for large grids)

### 6.2 Scanning
- **Record (▶)** = save current measurement to cell
- **Long-press Record** = automatic timed recording
- Navigation buttons (back/forward) allow moving through cells **without recording**
- Save anytime; **cancel save** → rollback to last saved state

### 6.3 Save Options
- **Direct Save** — original raw data
- **Enhanced Save** — improved visualization processing

---

## 7. Visualization

### 7.1 2D View Features
- Smoothing (noise reduction)
- **43 color palettes**
- Amplification modes
- Noise reduction
- Grid display
- Zoom
- RGB channel removal
- Color shift
- Crop

### 7.2 3D View Features
- Rotation (long-press for auto-rotation)
- Movement / pan
- Depth adjustment
- Lighting control
- **Custom textures**
- 43 color palettes + textures
- RGB channel removal
- Amplify height
- Amplify colors
- Color shift
- Crop

---

## 8. Export & Transmission Formats

| Format | Best For | Resolution Variants | Color? |
|---|---|---|---|
| **OBJ** | 3D modeling / rendering | Low + High | — |
| **STL** | 3D printing (topographic relief) | Low + High | — |
| **CSV** | Spreadsheet / MATLAB / Voxler | Low + High | — |
| **PLY** | Color-preserving 3D data | Low + High | ✅ per-vertex color |
| **Bluetooth Serial** | Real-time 1:1 raw stream to custom receivers (Office macros, HTML scripts, 3rd-party mappers) | — | — |

**Pro tip:** Long-press the Export icon to configure baud rate for Bluetooth streaming.

---

## 9. Website / Documentation File

The file provided (`!DOCTYPE html.txt` / `index.html`) is the official **landing page + full documentation** for AnyScan209, hosted at:
**https://soifgo.github.io/AnyScan209/**

### 9.1 Key Structural Elements
- **Theme:** Light/Dark toggle (default follows system; persisted in `localStorage` key `anyscan209-theme`)
- **Language Switcher:** 42 languages, custom dropdown, uses `translate.js` CDN
- **Download Cards:** Uptodown + APKPure
- **Community Forum Banner:** GitHub Discussions with how-to-post instructions
- **Tutorial Video:** 36 min embedded from Mega.nz
- **Table of Contents:** 19 anchor links
- **Sections 1–18** covering all app features
- **FAQ:** 7 Q&A entries (also in JSON-LD FAQPage schema)
- **Footer:** email, privacy policy, GitHub, forum

### 9.2 SEO / Meta
- **Title:** "AnyScan209 – Free 4-in-1 Sensor Visualizer: Magnetometer, Altimeter, Light & Sound Mapper for Android"
- **Canonical:** https://soifgo.github.io/AnyScan209/
- **OG image:** https://soifgo.github.io/AnyScan209/og-banner.jpg (1200×630)
- **Schema.org:** SoftwareApplication + WebSite + WebPage + VideoObject + BreadcrumbList + FAQPage
- **hreflang:** x-default + en
- **Google verification:** `a_eyU1xDCfLVC4vCKrGpm0_cHHUaNBcgR4AWRieeOmI`

### 9.3 Download Links
- **Uptodown:** https://anyscan209.en.uptodown.com/android
- **APKPure:** https://apkpure.com/anyscan209/any.scan_209

### 9.4 CSS Theme Variables
```css
:root {
  --bg-color: #f8fafc;      --bg-card: #ffffff;
  --text-color: #334155;    --text-main: #0f172a;
  --text-muted: #64748b;    --accent-color: #2563eb;
  --accent-hover: #1d4ed8;  --border-color: #e2e8f0;
  --success-color: #16a34a; --success-hover: #22c55e;
  --apkpure-color: #00b36b; --apkpure-hover: #00c974;
}
html[data-theme="dark"] {
  --bg-color: #0f172a;      --bg-card: #1e293b;
  --text-color: #cbd5e1;    --text-main: #f1f5f9;
  --text-muted: #94a3b8;    --accent-color: #4f8cff;
  --accent-hover: #6aa0ff;  --border-color: #334155;
  --success-color: #22c55e; --success-hover: #4ade80;
  --apkpure-color: #00c974; --apkpure-hover: #00e085;
}
```

### 9.5 JavaScript Modules in the Page
1. **Theme initializer** (inline in `<head>`) — reads localStorage before paint to avoid flash
2. **Theme toggle** — button handler, updates icon ☀️/🌙, persists to localStorage
3. **Language switcher** — 42 languages, fallback channels, custom dropdown
4. **translate.js** — loaded from `https://cdn.staticfile.net/translate.js/3.18.66/translate.js`
   (note: CDN may be blocked in some regions; consider self-hosting for production)

### 9.6 Translation System Details
- **localStorage key:** `anyscan209-lang`
- **Fallback channels (in order):** `giteeAI` → `client.edge` → `siliconflow`
- **Default:** English (forced LTR when no saved lang; prevents auto-detect)
- **RTL languages:** Hebrew, Arabic, Persian, Urdu, Kurdish Sorani
- **Class `ignore`:** Elements with this class are skipped by the translation engine (used for brand names like "AnyScan209" and "Saeid Moghadam")
- **Timeout per channel:** 3000 ms

### 9.7 Language List (42 entries)
English, Spanish, French, Deutsch, Italian, Dutch, Portuguese, Polish, Swedish, Norwegian, Danish, Romanian, Czech, Slovak, Hungarian, Greek, Bulgarian, Russian, Ukrainian, Serbian, Hebrew, Chinese (Simplified), Japanese, Korean, Hindi, Bengali, Turkish, Arabic, Persian, Urdu, Kurdish Sorani, Azerbaijani, Armenian, Georgian, Indonesian, Malay, Filipino, Thai, Afrikaans, Vietnamese, Tamil.

---

## 10. Wire & Conduit Detection (Killer Feature)

### Two detection scenarios:
| Conduit Type | Requires Current? | Method |
|---|---|---|
| **PVC / non-metallic** | ✅ YES — need high-power load (heater, kettle) to generate AC field | Alternating magnetic field detection |
| **Metal (steel/galvanized)** | ❌ NO — detectable even with no current | Ferromagnetic disturbance of ambient field |

- **Detection depth:** A few centimeters (smartphone magnetometer limit)
- **Setup:** Internal Sensor mode → long-press sensor option → enable **Graph** + **Gauge** → select **Bipolar Gauge**
- **Gauge behavior:**
  - **AC fields** → bidirectional movement
  - **DC fields** → one-directional deflection

### Why flagship phones may perform worse than budget phones:
1. **Wireless charging coils** — permanent magnets create constant offset
2. **Metal bodies/frames** — ferromagnetic materials distort fields
3. **Sensor placement** — budget phones (e.g., Samsung A-series) often have cleaner magnetic environments
- **Bottom line:** Sensor chip is rarely the issue; installation environment matters most.

---

## 11. Supported Magnetometer Sensors (Sensor Guide)

| Manufacturer | Model | Sampling Rate | Resolution | Noise | Example Devices |
|---|---|---|---|---|---|
| MEMSIC | MMC5616WA | 1000 Hz | 0.00625 µT/LSB | Very Low | (check specs) |
| AKM | AK09973D | up to 2000 Hz | High sensitivity | Medium | Selected Samsung/Xiaomi/Sony |
| Yamaha | YAS537 | 200 Hz | 0.15 µT/LSB | Very Low | Galaxy S6/S7/Note |
| Yamaha | YAS539 | ~200 Hz | 0.12 µT/LSB | Very Low | Galaxy A series |
| Alps Alpine | HSCDTD015A | 200 Hz | 0.075 µT/LSB | Low | Modern smartphones |
| STMicroelectronics | LIS3MDL | 1000 Hz | Medium | Medium | Motorola/Nokia/LG |

**Tip:** To view your phone's magnetometer info → Settings → Update section → **Sensor internal : help**

---

## 12. Scanning Setup Tips
- Use a **smartphone holder or selfie stick** for stable movement
- Use a **Bluetooth remote controller** to trigger Record without touching the phone
- Ideal for systematic, consistent measurements

---

## 13. FAQ (Core Answers)

1. **Free?** — Yes, 100% free, no hidden fees, no IAP, no ads.
2. **External sensors?** — Yes, via HC-05 or any SPP Bluetooth module.
3. **Export formats?** — CSV (tables), OBJ/STL (3D), PLY (color-preserving 3D). All in low + high resolution.
4. **More than magnetic scanning?** — Yes, 4 internal sensors + any external 0–1024 data.
5. **Ads / data collection?** — None. All data stays on-device.
6. **Compatible devices?** — Any Android with a built-in magnetometer.
7. **Professional geophysics?** — Yes, designed for both education and professional field work.
8. **Gain feature?** — Adjusts 16-bit magnetometer (0–65535) sensitivity into 0–1024 range; default Gain=10; external mode requires pre-scaling.

---

## 14. Important Notes for AI Assistants

When generating content, code, or translations for AnyScan209:

1. **Always spell it "AnyScan209"** — capital A, S, and the number 209. Never "AnyScan 209" or "anyscan209" in prose (except in URLs/package names).
2. **The `ignore` class matters** — brand names wrapped in `<span class="ignore">` are intentionally NOT translated.
3. **The 0–1024 range is sacred** — never suggest alternative ranges without explaining the mapping.
4. **512 = neutral point** — critical for magnetometer explanations.
5. **Do not invent features** — stick to what's in this document.
6. **RTL support** — when editing HTML, respect `dir="rtl"` for Hebrew/Arabic/Persian/Urdu/Kurdish.
7. **Theme variables** — always use CSS custom properties (`var(--accent-color)` etc.), never hardcode colors.
8. **Author name** — Saeid Moghadam (not "Saeed" or "Said").
9. **Email** — ssmqqmss@gmail.com
10. **No ads, no tracking, no telemetry** — this is a core selling point; never contradict it.

---

## 15. Quick Reference — URLs

| Resource | URL |
|---|---|
| Website | https://soifgo.github.io/AnyScan209/ |
| Video page | https://soifgo.github.io/AnyScan209/video.html |
| Privacy policy | https://soifgo.github.io/AnyScan209/policy_anyscan209.html |
| Sitemap | https://soifgo.github.io/AnyScan209/sitemap.xml |
| GitHub | https://github.com/soifgo/AnyScan209 |
| Forum | https://github.com/soifgo/AnyScan209/discussions |
| Uptodown | https://anyscan209.en.uptodown.com/android |
| APKPure | https://apkpure.com/anyscan209/any.scan_209 |
| Tutorial video | https://mega.nz/file/7fIGRJob#ibuMQe_Vh0epI77NvD3hmXhMHo6pMgbrLLTMD4DjCxk |
| Video embed | https://mega.nz/embed/7fIGRJob#ibuMQe_Vh0epI77NvD3hmXhMHo6pMgbrLLTMD4DjCxk |
| OG banner | https://soifgo.github.io/AnyScan209/og-banner.jpg |

---

## 16. Video Metadata
- **Name:** AnyScan209 Tutorial - How to Use the 2D/3D Visualizer App
- **Duration:** PT36M55S (36 min 55 sec)
- **Upload date:** 2026-07-04
- **Thumbnail:** og-banner.jpg

---

## 17. Quick Start for AI Assistants

If you are an AI assistant asked to work on AnyScan209:

1. **Read §1–§3** for identity and the core 0–1024 concept.
2. **Read §4** if the task involves sensor modes.
3. **Read §5** if the task involves external sensors, Bluetooth, or Arduino/ESP.
4. **Read §6–§8** if the task involves scanning workflow, visualization, or export.
5. **Read §9** if the task involves the website, translation, or SEO.
6. **Read §10** if the task involves wire/conduit detection or magnetometer physics.
7. **Read §14** for style/accuracy rules before generating any output.

### Common Task Patterns
| Task | Sections to read |
|---|---|
| Translate the website | §9, §14 |
| Write a blog post about AnyScan209 | §1, §2, §4, §10, §13 |
| Generate Arduino code for external sensor | §5 |
| Explain magnetometer behavior | §3, §10, §11 |
| Add a new language to the site | §9.6, §9.7 |
| Write an FAQ answer | §13, §14 |
| Debug website CSS/JS | §9.4, §9.5 |

### Anti-Patterns (do NOT do)
- ❌ Do NOT claim the app has AI/ML features (it doesn't).
- ❌ Do NOT suggest it works on iOS (Android-only).
- ❌ Do NOT say it's on Google Play (it isn't — only Uptodown & APKPure).
- ❌ Do NOT recommend using it for medical, safety-critical, or legal purposes.
- ❌ Do NOT add emojis to the app name "AnyScan209".
- ❌ Do NOT suggest it has cloud sync, user accounts, or online storage (it doesn't).
- ❌ Do NOT describe it as an IoT platform or MQTT broker.
- ❌ Do NOT recommend paid alternatives when asked for a free option.

---

## 18. File Manifest (Referenced Assets)

Images / assets referenced in the HTML documentation:

| File | Purpose |
|---|---|
| `logo.png` | App logo (header) — should be 180×180 or 512×512 |
| `og-banner.jpg` | Open Graph / Twitter card image (1200×630) |
| `uptodown.png` | Uptodown button icon |
| `apkpure.png` | APKPure button icon |
| `menu1.jpg` – `menu8.jpg` | UI screenshots (main menu, scan screen, 2D, 3D, settings, external sensor, schematic, sensor selection) |
| `selfi.jpg` | Scanning setup (selfie stick / holder) |
| `set_01.jpg`, `set_02.jpg` | Sensor settings / metal conduit detection |
| `video.html` | Dedicated video page |
| `policy_anyscan209.html` | Privacy policy page |
| `Proteuse_file.zip` | Proteus project download |
| `sitemap.xml` | XML sitemap (3 URLs) |
| `robots.txt` | Robots file (limited on GitHub Pages) |

---

## 19. Glossary

| Term | Meaning in AnyScan209 context |
|---|---|
| **Balance / Balancer** | Auto-calibration to set neutral point (512) for internal sensors |
| **Bipolar Gauge** | Gauge display mode showing bidirectional deflection (AC fields) |
| **Direct Save** | Save raw scan data as-is |
| **Enhanced Save** | Save with improved visualization processing |
| **Gain** | Sensitivity multiplier mapping 16-bit raw → 0–1024 |
| **Go/Go** | One-way scan pattern (return to start of each column) |
| **Go/Return** | Zigzag scan pattern (continuous, faster) |
| **Grid** | Scan matrix, 8×8 to 100×100 points |
| **HC-05** | Common serial Bluetooth module for external sensors |
| **SPP** | Serial Port Profile (Bluetooth) |
| **SPL** | Sound Pressure Level (dB measurement) |
| **PLY** | Polygon File Format (stores per-vertex color) |
| **µT/LSB** | Microtesla per Least Significant Bit (sensor resolution) |
| **PWA** | Progressive Web App (not enabled on AnyScan209 — only APK) |
| **APK** | Android Package Kit (the app's distribution format) |

---

## 20. Changelog of This Document

| Version | Date | Changes |
|---|---|---|
| 1.0 | 2026-10-10 | Initial AI Context Document |
| 1.1 | 2026-10-10 | Added version 2.01, fixed FAQ count (7), removed video.html hreflang, added Anti-Patterns, added sitemap.xml & robots.txt to manifest, added PWA/APK glossary terms |

---

*End of AnyScan209 AI Context Document.*
*©2025–2026 AnyScan209 — Built by Saeid Moghadam*
