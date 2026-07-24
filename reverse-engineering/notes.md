# Reverse Engineering Notes

## Offline
- **shiz arcade-docs** (mirrored): [`files/vendor/arcade-docs/`](../files/vendor/arcade-docs/) — board-level details, pinouts, manufacturer notes by Sega, Capcom, Namco, Konami, Taito, etc.
- Local JVS protocol: [`files/jvs/jvs_wip.pdf`](../files/jvs/jvs_wip.pdf)

## Living external references (not bulk-mirrored)
- MAME source code (drivers, machine configs) — undocumented registers, timing, quirks
- system16.com technical pages and photo documentation
- Community: Arcade Projects, UKVAC, Arcade Otaku wiki

## Common pitfalls
- Non-standard JAMMA pin usage or missing video ground causing sync/color issues
- High current draw on +5V exceeding cheap power supplies
- JVS sense lines, addressing, and firmware differences between I/O boards
- Extra harness requirements for multi-button games
