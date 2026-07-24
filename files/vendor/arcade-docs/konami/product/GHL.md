# `GHL` — Silent Hill THE ARCADE

サイレントヒルアーケード / **Silent Hill: The Arcade** (2007)

Dedicated **PC-based** Konami light-gun cabinet (not classic JAMMA edge PCB). Horror rail shooter developed by **Polygon Magic**, published by **Konami Digital Entertainment**.

| | |
|--|--|
| **Game code** | `GHL` |
| **Release** | JP 2007-07-25 · EU / SEA 2008 |
| **Genre** | 1–2 player rail light-gun shooter |
| **Network** | Konami **e-Amusement** (optional rankings + pass progress) |
| **Home port** | None official |

## Hardware (game PC)

Main board RE (arcade-docs Konami PC family):

| Item | Spec |
|------|------|
| **Assembly** | [`FAB-e945-KN210`](../boards.md#fab-e945-kn210) |
| **Sticker** | **B10** |
| **CPU** | Intel **Celeron D 341** @ **2.93 GHz** |
| **GPU** | **ATI Radeon X1300** |
| **RAM** | **2 × 512 MB** (documented as “?” in some notes; matches sibling FAB-e945 configs) |
| **I/O** | Product notes: **IO(serial?)** — gun / button path is **not** the later USBIO2-class BEMANI stack |
| **Storage** | HDD (ROM CHECK = hard disk integrity) |
| **OS class** | Windows XP Embedded era (typical; ~3 min boot to attract after power-on) |

Sibling FAB-e945 systems in the same generation often use ATX-class PSUs (~450 W), SATA HDDs (e.g. 80 GB class on related stickers), and discrete ATI PCIe GPUs — useful for cab service even when not GHL-exact.

### Conflicting secondary claims

Some forum posts list **Pentium 4 2.4 GHz + GeForce4 MX 440 + 256 MB**. That matches **generic** System16 “Konami PC / Longhorn” tables used for multiple titles. Prefer **B10 / Celeron D + Radeon X1300** unless a specific cab is photographed open.

## Product / media identifiers

| Code | Role |
|------|------|
| `GHL` | Product family |
| `GNGHL-JA` | JP assembly / cab variant |
| `GKGHL-EA` | EU/export **software kit** (operator manual title block) |
| `GHL JA A01` / `GHL AA A01` | System disc |
| `GHL JA B02` … `B05` | Application discs 1–4 |
| `GHL AA B06` | Application disc 5 |

See also [software/GHL.md](../software/GHL.md).

## Cabinet / player I/O

From official **Operator’s Manual** (software kit; not a full mechanical cab drawing set):

| Subsystem | Detail |
|-----------|--------|
| Players | 1 or 2 (P2 can join mid-game as the other character) |
| Controls | Dual **light gun** units with **recoil**; off-screen reload |
| Start | P1 / P2 start buttons |
| Coin | Coin mech + **coin blocker** (MECHANISM CHECK) |
| Card | **e-Amusement PASS** IC reader (optional) |
| Security | **e-Amusement / security plug** (dongle-class) |
| Audio | Speaker channel setup in test mode; field cabs often 5.1 surround |
| Display | SCREEN CHECK for size/calibration (cab-dependent CRT/LCD) |

### Test mode (MAIN MENU highlights)

- **I/O CHECK** — INPUT / GUN CHECK (calibration) / MECHANISM CHECK  
- **SCREEN CHECK** · **SOUND OPTIONS** · **ROM CHECK** (HDD)  
- **IC CARD CHECK*** · **NETWORK OPTIONS*** (e-Amusement ON/OFF, shop area/name, connectivity)  
- **BOOKKEEPING** · **CLOCK** · **SYSTEM INFORMATION**  
- Game options: coin/credit, continue, difficulty-class settings  

\* Present when relevant hardware / e-Amusement path is available.

Boot: self-test on power-on; attract/demo after ~**3 minutes**.

### Error code families (operator manual)

| Prefix | Class |
|--------|--------|
| `5-1502-*` | OOM / I/O (button + IC card PCB) |
| `5-1503-*` | Gun connectors / gun control board / **I/O board** |
| `5-1512` / `5-1520-*` | **Security / e-Amusement plug** |
| `5-1550` / `5-1555` / `5-1556-*` | Executable / app / AC data damage → reinstall |
| `5-2000-*` | VPN router / center server / registration / online period / LAN |
| `5-2551-*` | Test data / ranking / bookkeeping / **gun cal unset** / clock / speaker |
| `5-350x-*` | Settings initialized / e-Amusement or speaker change |

## Gameplay summary

- On-rails stages through Silent Hill; alternate routes and **multiple endings**  
- Protagonists **Eric** and **Tina** (Occult Club); supporting plot around Emilie / Hanna / *Little Baroness* (SH2 memo lore)  
- Weak-point shooting; limited shotgun/rifle pickups; health items  
- Score: silver/gold coins, hit-streak combos  
- Locations heavily reuse/polish sets from SH2/SH3/SH4 (Brookhaven, Toluca Prison, Lakeside, etc.)  
- Music: Akira Yamaoka material (e.g. Theme of Laura, Promise, Hometown)  
- Joke/UFO-style endings (incl. Gradius bit)

## Preservation / play

| Path | Notes |
|------|--------|
| Official home port | **None** |
| Emulation | **TeknoParrot** (PC arcade stack) is the usual dump path |
| Unofficial Windows port | Community “Assemblr” era (~2014); flaky on modern OS |
| Modern light guns | Community guides (e.g. Sinden wiki “Silent Hill Arcade”) |

Not a classic discrete PCB → **no standard MAME driver** like Hornet/Python.

## Local documents

| File | Description |
|------|-------------|
| [Silent_Hill_The_Arcade_Operators_Manual_GKGHL-EA.pdf](../../../../manuals/konami/Silent_Hill_The_Arcade_Operators_Manual_GKGHL-EA.pdf) | Official operator manual, **GKGHL-EA**, 51 pp, Konami 2007-10 (GNGHL-HD/TB) |

## Cross-references

- Board: [boards.md — FAB-e945-KN210 / B10](../boards.md#fab-e945-kn210)  
- Index entry: [products.md — GHL](../products.md)  
- Software media: [software/GHL.md](../software/GHL.md)

## External references

- Wikipedia: Silent Hill: The Arcade  
- Hardcore Gaming 101 — design / e-Amusement / TeknoParrot notes  
- System16 Konami PC hardware tables (generic; cross-check only)  
- Auction / photo dumps for disc labels (`GHL *A01`, `B02`–`B06`) listed under products.md tags  

## Gaps (public)

- Full gun I/O + serial I/O **schematics**  
- Exact HDD image layout / encryption  
- Factory display resolution/refresh (cab-dependent)  
- Full mechanical cab dimensions / weight / power-draw drawing set  

_Compiled 2026-07-24 from arcade-docs RE, operator manual GKGHL-EA, and public secondary sources._
