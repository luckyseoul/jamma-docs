# JAMMA Arcade Documentation Repository

Curated collection of publicly available JAMMA (and successor JVS) arcade standards, pinouts, wiring guides, service manuals indexes, hardware overviews for major board generations/families, and reverse-engineering notes across manufacturers and eras.

**Primary Sources (Best Collections)**
- [Mike's Arcade](http://www.mikesarcade.com/) — Canonical community JAMMA pinouts, board lists, manuals, and conversion info.
- [ARCarc.xmission.com PDF Manuals & Schematics](http://arcarc.xmission.com/PDF_Arcade_Manuals_and_Schematics/) — Massive archive of operator/service manuals and schematics.
- [codeberg.org/shiz/arcade-docs](https://codeberg.org/shiz/arcade-docs) (ex-Shizmob/arcade-docs) — High-quality open RE notes organized by manufacturer (boards.md, pinouts, PCB details for Sega, Capcom, Namco, Konami, Taito, etc.).
- [system16.com](http://www.system16.com/) — Hardware museums with detailed board overviews, photos, and specs for Sega, Capcom, and others.
- [sega.bsnk.me JVS docs](https://sega.bsnk.me/ringedge/hardware/jvs/) + [daifukkat.su JVS English translation](http://daifukkat.su/files/jvs_wip.pdf) — Best public JVS protocol and structure references.
- [Sega Retro](https://segaretro.org/) — Sega system manuals, service docs, Naomi etc.
- [NeoGeo Development Wiki](http://wiki.neogeodev.org/) — MVS JAMMA specifics.
- [Arcade Museum / coinop.org](https://www.arcade-museum.com/) and related archives.
- MAME driver sources and comments for hardware quirks.

## The JAMMA Standard

JAMMA (Japanese Amusement Machine Manufacturers' Association) is the 56-pin edge connector standard (28 pins per side, 0.156" pitch) introduced ~1985 that unified power, video, audio, controls, and coinage wiring so cabinets could swap boards easily.

### Core Pinout (Standard)
See `standard/pinout.md` for full dual-side table (Parts Side 1–28 / Solder Side A–f).

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
- See `standard/variants.md`.

## JVS — JAMMA Video Standard (Successor)

JVS (also called JAMMA 2 in some contexts) is the digital serial I/O standard (typically RS-485) that replaced the analog edge connector for modern systems. Used heavily by Sega (Naomi, Chihiro, Triforce, Lindbergh, RingEdge, ALLS), Namco, Taito, and others.

- Protocol, packet structure, device addressing, and I/O board details: see `jvs/` and the daifukkat / sega.bsnk.me sources.
- Many JVS systems still provide a JAMMA edge via an I/O board for cabinet compatibility.
- Common Sega I/O boards: 838-xxxxx series.

## Major Board Families & Generations

### Sega (strong coverage)
- Early / System series: System 16, System 18, System 24, System C / C2, ST-V (Saturn-based, JAMMA)
- 3D era: Model 1, Model 2, Model 3
- JVS era: Naomi / Naomi 2, Chihiro, Triforce, Lindbergh, RingEdge / RingEdge 2, ALLS
- See `sega/` for overviews, pinouts where available, links to service manuals and architecture notes. ST-V links to dreamcast-docs where relevant.

### Capcom
- CPS-1, CPS-2, CPS-3 (JAMMA + Kick)
- See manufacturer notes and Shizmob/arcade-docs.

### SNK
- Neo-Geo MVS (multi-slot and single) — true JAMMA edge with specific pin usage. NeoGeoDev wiki is excellent.

### Namco, Konami, Taito, others
- System 11/12/22/246 etc. (Namco), various Konami boards, Taito F3 and later, IGS, etc.
- Covered via indexes to Shizmob, system16, ARCarc manuals.

## Hardware & Pinouts
- `standard/` — Core JAMMA pinout, power, video, wiring notes, variants.
- `jvs/` — Protocol overview, common I/O boards, conversion notes.
- `sega/` — Generation-by-generation Sega arcade systems.
- Manufacturer or board-family stubs as expanded.

## Reverse Engineering & Undocumented
- Shizmob/arcade-docs (Codeberg) is the modern gold standard for open RE.
- MAME sources, system16.com technical pages, community forums (Arcade Projects, UKVAC, etc.).
- Quirks: non-standard JAMMA implementations, video ground, sync polarity, extra power requirements, JVS addressing and sense lines.

See `reverse-engineering/`.

## Tools & Resources
- JAMMA harness testers, multi-game boards, JVS-to-JAMMA converters, I/O board firmware notes.
- Emulation: MAME (authoritative for many boards), Supermodel (Model 3), Flycast (Naomi/Dreamcast-related), etc.

## Coverage Note
This repository synthesizes the core standards (JAMMA + JVS), major public pinouts, indexes to service manuals/schematics, and high-quality RE collections. It prioritizes the standard itself and well-documented generations (especially Sega, Capcom, Neo-Geo) while pointing to the best external archives for exhaustive per-board manuals.

Binary PDFs and large manuals remain external links (size + copyright). Local Markdown provides indexes, clean pinout tables, summaries, and cross-references.

Structure intentionally mirrors the style of luckyseoul/saturn-docs and dreamcast-docs for consistency.

Last updated: Initial comprehensive curation (2026-07-23).
