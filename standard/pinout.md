# JAMMA Standard Pinout

The JAMMA (Japanese Amusement Machine Manufacturers' Association) connector is a 56-pin (28 pins per side) 3.96 mm (0.156") pitch edge connector. The male edge is on the PCB; the female harness is in the cabinet.

**Orientation**: When looking at the component/parts side of the PCB with the connector edge facing you, Parts Side pins are numbered 1–28 (right side in many diagrams), Solder Side lettered A–f (left side). There is a key slot (missing pin) at position 7/H to prevent reverse insertion.

This table is compiled from community-standard references (Mike's Arcade, Arcade Museum, common harness diagrams). Always cross-check the specific game board, as some use non-standard assignments or require additional harnesses.

## Full Dual-Side Pinout

| Solder Side | Function                  | Parts Side | Function                  |
|-------------|---------------------------|------------|---------------------------|
| A           | GND                       | 1          | GND                       |
| B           | GND                       | 2          | GND                       |
| C           | +5V                       | 3          | +5V                       |
| D           | +5V                       | 4          | +5V                       |
| E           | -5V                       | 5          | -5V                       |
| F           | +12V                      | 6          | +12V                      |
| H           | Key (no pin)              | 7          | Key (no pin)              |
| J           | Coin Counter 2            | 8          | Coin Counter 1            |
| K           | Coin Lockout              | 9          | Coin Lockout              |
| L           | Speaker (-)               | 10         | Speaker (+)               |
| M           | NC (or unused)            | 11         | NC (or unused)            |
| N           | Video Green               | 12         | Video Red                 |
| P           | Video Composite Sync      | 13         | Video Blue                |
| R           | Service Switch            | 14         | Video Ground              |
| S           | Tilt / Slam               | 15         | Test                      |
| T           | Coin B                    | 16         | Coin A                    |
| U           | Player 2 Start            | 17         | Player 1 Start            |
| V           | Player 2 Up               | 18         | Player 1 Up               |
| W           | Player 2 Down             | 19         | Player 1 Down             |
| X           | Player 2 Left             | 20         | Player 1 Left             |
| Y           | Player 2 Right            | 21         | Player 1 Right            |
| Z           | Player 2 Button 1         | 22         | Player 1 Button 1         |
| a           | Player 2 Button 2         | 23         | Player 1 Button 2         |
| b           | Player 2 Button 3         | 24         | Player 1 Button 3         |
| c           | Player 2 Button 4 (ext)   | 25         | NC / Player 1 Button 4    |
| d           | Player 2 Button 5 (ext)   | 26         | NC / Player 1 Button 5    |
| e           | GND / Player 2 Button 6   | 27         | GND / Player 1 Button 6   |
| f           | GND                       | 28         | GND                       |

Notes on the table:
- Buttons 4–6 and some NC pins are frequently used for extra controls on non-standard or “JAMMA+” boards / via Kick harness. Classic pure JAMMA only guarantees Buttons 1–3.
- Some later Chinese multi-game boards remap e/27 for additional inputs instead of pure GND.
- Trackball / spinner games often replace the direction pins (V–Y / 18–21) with X/Y data and clock lines.

## Power Requirements (Typical)

- **+5 V**: Main logic. High current (often 5–10 A or more depending on board). Multiple pins paralleled for capacity. Must be well regulated.
- **+12 V**: Often for audio amplifiers, coin meters, or certain analog sections. Lower current.
- **-5 V**: Used by some older analog video or sound circuitry. Many modern / multi boards do not require it (can leave unconnected if board does not use it).
- **GND**: Multiple pins; connect all for low resistance return path. Critical for video and digital noise.

Use a proper switching arcade power supply. Never reverse the connector.

## Video

- Analog RGB (0.7 Vpp typical into 75 Ω) + composite sync (or separate H/V on some non-standard).
- Video Ground is important for clean signal; do not rely solely on power GND.
- Standard arcade monitors are 15 kHz (standard resolution). VGA or higher requires a converter or specific board support.

## Audio

- Mono speaker differential (Speaker + / Speaker -). Many boards put a small amplifier on-board; others expect the cabinet amp. Some stereo boards use additional connectors.

## Controls & Coinage

- Active-low digital inputs (buttons/joysticks pull to GND when pressed; board has pull-ups).
- Coin meters / lockouts are typically open-collector or similar outputs that pulse or enable.
- Service / Test / Tilt are inputs, usually active low.

## Common Pitfalls

1. Missing or weak GND connections → video noise, random resets, bad controls.
2. Insufficient +5 V current capacity or poor regulation → crashes, especially on multi-boards.
3. Assuming -5 V is always needed (or always present).
4. Forgetting the Kick / extra harness for 6-button games.
5. Sync polarity or missing video ground.
6. On JVS systems converted to JAMMA edge, sense line and proper I/O board configuration are required.

## Sources / References (for verification)

- Mike's Arcade JAMMA Standard Pinout Class
- Arcade Museum / coinop.org pinout database
- Common JAMMA harness wiring diagrams (community PDFs from The Geek Pub and others)
- Board-specific manuals (cross-check always)

This file is intended as a self-contained reference. Expand with color-coded harness diagrams or board-specific deviations as needed.
