# JAMMA Variants & Extensions

- **Standard JAMMA**: 3 buttons per player on the 56-pin edge. Full table in [`pinout.md`](pinout.md).
- **JAMMA+ / kick harness**: a second connector for buttons 4–6. The pinout is not one standard. Capcom CPS-2 and CPS-3 use a 34-pin Hirose DF1B. CPS-1, Neo Geo MVS, Taito F3, and ST-V do not share that map.
- Some boards put non-standard signals on unused edge pins or require higher current on +5V/+12V.
- Early pre-JAMMA or proprietary edges converted via adapters.

See manufacturer-specific notes under [`files/vendor/arcade-docs/`](../files/vendor/arcade-docs/).

## Capcom CPS-2 / CPS-3 kick harness

Local sheet: [`files/manuals/capcom/CAPCOM-H2.pdf`](../files/manuals/capcom/CAPCOM-H2.pdf) (Mike's Arcade P/N CAPCOM-H2, one page). Connector is the 34-pin CPS-2/CPS-III "A" board plug. Buttons are active-low. The two black wires are the kick commons (grounds), not a single shared ground pin.

| Pin | Wire | Function |
|-----|------|----------|
| 9 | Purple | P2 heavy kick |
| 15 | Orange | P1 heavy kick |
| 17 | Red | P1 medium kick |
| 19 | Blue | P1 light kick |
| 21 | Gray | P2 light kick |
| 23 | Yellow | P2 medium kick |
| 29 | Brown | Volume up |
| 30 | Green | Volume down |
| 31 | White | Volume common |
| 33 | Black | P2 kick common |
| 34 | Black | P1 kick common |

Pins 1–8, 10–14, 16, 18, 20, 22, and 24–28 are unused on this harness. Other write-ups (Hardware Book, Arcade Otaku) number the same housing differently or list different wire colors. Wire from this sheet, then confirm with a meter.

## Other kick connectors

| System | Connector | Notes |
|--------|-----------|-------|
| Capcom CPS-1 | 12-pin | Different map from CPS-2. SF2 Champion Edition / Turbo. |
| SNK Neo Geo MVS | 15-pin | Not CPS-compatible. |
| Taito F3 | 14-pin | Taito harness. |
| Sega ST-V | Per game | Check the cart adapter. |
