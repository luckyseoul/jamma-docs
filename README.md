# JAMMA Arcade Documentation Repository

Curated collection of publicly available JAMMA (and successor JVS) arcade standards, pinouts, wiring guides, manufacturer RE notes, and offline document mirrors under [`files/`](files/).

## Local Primary Sources

| Source | Local path |
|--------|------------|
| daifukkat JVS English translation (WIP) | [`files/jvs/jvs_wip.pdf`](files/jvs/jvs_wip.pdf) |
| sega.bsnk.me JVS page (HTML snapshot) | [`files/jvs/sega-bsnk-jvs.html`](files/jvs/sega-bsnk-jvs.html) |
| shiz/arcade-docs (Codeberg) full mirror | [`files/vendor/arcade-docs/`](files/vendor/arcade-docs/) |

### Vendor arcade-docs highlights
- [`files/vendor/arcade-docs/sega/boards.md`](files/vendor/arcade-docs/sega/boards.md)
- [`files/vendor/arcade-docs/konami/boards.md`](files/vendor/arcade-docs/konami/boards.md)
- [`files/vendor/arcade-docs/taito/boards.md`](files/vendor/arcade-docs/taito/boards.md)
- Konami I/O & JAMMA wiring under `files/vendor/arcade-docs/konami/io/`

### Not mirrored in-git (size / live indexes)
These remain useful live indexes; pinout tables and RE content that matter most are already offline in this repo + vendor tree:
- Mike's Arcade — board lists / conversion notes (site is a large dynamic catalog)
- ARCarc PDF manuals archive — multi-GB operator manuals; pull individual games as needed into `files/manuals/`
- system16.com hardware museum
- Arcade Museum / coinop.org
- NeoGeo Development Wiki (MVS JAMMA specifics)
- Sega Retro (Naomi / service manuals index)

## The JAMMA Standard

JAMMA (Japanese Amusement Machine Manufacturers' Association) is the 56-pin edge connector standard (28 pins per side, 0.156" pitch) introduced ~1985 that unified power, video, audio, controls, and coinage wiring so cabinets could swap boards easily.

### Core Pinout (Standard)
See [`standard/pinout.md`](standard/pinout.md) for full dual-side table (Parts Side 1–28 / Solder Side A–f).

Key groups:
- Power: +5V, +12V, -5V, multiple GND
- Video: RGB analog + composite sync + video GND
- Audio: Speaker +/-
- Controls: P1/P2 Start, Joystick (Up/Down/Left/Right), Buttons 1–3 (often extended)
- Coin: Coin A/B, Coin Counters, Lockout, Service, Test, Tilt

Many boards use only a subset. Extra buttons/controls use additional harnesses or JAMMA+ extensions.

### Variants & Extensions
- **JAMMA+ / Kick harnesses**: Extra edge or ribbon connectors for 4–6 buttons per player (Capcom Street Fighter style, Midway, etc.).
- Non-standard power or video on some early boards.
- See [`standard/variants.md`](standard/variants.md).

## JVS — JAMMA Video Standard (Successor)

JVS is the digital serial I/O standard (typically RS-485) that replaced the analog edge connector for modern systems.

- **Local protocol PDF**: [`files/jvs/jvs_wip.pdf`](files/jvs/jvs_wip.pdf)
- **Local HTML**: [`files/jvs/sega-bsnk-jvs.html`](files/jvs/sega-bsnk-jvs.html)
- Technical summary: [`jvs/overview.md`](jvs/overview.md)

## Major Board Families & Generations

### Sega
See [`sega/overview.md`](sega/overview.md) and [`files/vendor/arcade-docs/sega/`](files/vendor/arcade-docs/sega/).

### Capcom / SNK / Namco / Konami / Taito
Board notes and I/O details under [`files/vendor/arcade-docs/`](files/vendor/arcade-docs/) (manufacturer folders).

## Reverse Engineering

See [`reverse-engineering/notes.md`](reverse-engineering/notes.md) and the offline shiz arcade-docs tree.

## Silent Hill THE ARCADE (GHL)

Konami PC light-gun title (product **GHL**, board sticker **B10**):
- Dossier: [`files/vendor/arcade-docs/konami/product/GHL.md`](files/vendor/arcade-docs/konami/product/GHL.md)
- Operator manual: [`files/manuals/konami/Silent_Hill_The_Arcade_Operators_Manual_GKGHL-EA.pdf`](files/manuals/konami/Silent_Hill_The_Arcade_Operators_Manual_GKGHL-EA.pdf)


## Coverage Note

Pinouts, JVS protocol, and manufacturer RE markdown are offline. Exhaustive per-game service manuals (ARCarc-scale) are intentionally not bulk-imported; add individual PDFs under `files/manuals/<mfr>/<game>.pdf` as needed.

Last updated: 2026-07-24 — offline harvest; primary URLs replaced with `files/` paths.
