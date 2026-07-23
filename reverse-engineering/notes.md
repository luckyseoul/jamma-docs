# Reverse Engineering Notes

- **Shizmob / shiz arcade-docs** (Codeberg): Best organized open collection of board-level details, pinouts, and manufacturer notes. Prefer this over scattered forum posts.
- MAME source code (drivers, machine configs) contains hard-won knowledge of undocumented registers, timing, and quirks.
- system16.com technical pages and photo documentation.
- Community: Arcade Projects, UKVAC, Arcade Otaku wiki, etc.

Common pitfalls:
- Non-standard JAMMA pin usage or missing video ground causing sync/color issues.
- High current draw on +5V exceeding cheap power supplies.
- JVS sense lines, addressing, and firmware differences between I/O boards.
- Extra harness requirements for multi-button games.
