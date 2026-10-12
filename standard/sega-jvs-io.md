# Sega JVS I/O boards

Sega shipped three I/O board generations on Naomi, Hikaru, Triforce, Chihiro, and Lindbergh. The protocol is JVS (see [`../jvs/overview.md`](../jvs/overview.md) and [`../files/jvs/JVST_VER3.pdf`](../files/jvs/JVST_VER3.pdf)). The connector maps below are the comments in MAME `src/mame/sega/naomi.cpp` (Guru's readme notes in that file, read 2026-10-12). Switches are active-low to ground. Where that file leaves a pin blank, this page leaves it blank.

The Naomi Universal cabinet manual on Arcade Otaku (`Sega_Naomi_Universal_Manual.pdf`) is the other common drawing. That file host returned an error on this pass, so it is not mirrored here.

## Type 1 — 837-13551

Stickers 837-13551-92 and 837-13551-93. Identify string: `SEGA ENTERPRISES,LTD.;I/O BD JVS;837-13551;Ver1.00;98/10`. JVS 2.0, command revision 1.1. Two players, 13 switch bits, 2 coin slots, 8 analog channels, 6 driver outputs. MCU is a Toshiba TMP90PH44 marked 315-6215.

The JVSCab2PC notes (2022) describe the Lindbergh-era Type 3 board, 837-14572, as using this same 60-pin header plus a 20-pin output connector. MAME does not list 837-14572, and neither source gives that 20-pin map, so those pins are not in the table.

### CN3, 60-pin digital

| Pins | Function | Pins | Function |
|------|----------|------|----------|
| 1–8 | +5 V | 33 | 1P SW4 |
| 9–15 | GND | 34 | 2P SW4 |
| 16 | NC | 35 | 1P SW5 |
| 17 | 1P Start | 36 | 2P SW5 |
| 18 | 2P Start | 37 | 1P SW6 |
| 19 | 1P Right | 38 | 2P SW6 |
| 20 | 2P Right | 39 | 1P SW7 |
| 21 | 1P Left | 40 | 2P SW7 |
| 22 | 2P Left | 41 | 1P Service |
| 23 | 1P Up | 42 | 2P Service |
| 24 | 2P Up | 43 | Test |
| 25 | 1P Down | 44 | Tilt |
| 26 | 2P Down | 45 | Coin SW1 |
| 27 | 1P SW1 | 46 | Coin SW2 |
| 28 | 2P SW1 | 47–48 | NC |
| 29 | 1P SW2 | 49–50 | Coin meter 1 and 2 |
| 30 | 2P SW2 | 51–56 | Output 1–6 |
| 31 | 1P SW3 | 57–60 | +12 V |
| 32 | 2P SW3 | | |

Coin inputs need the meters on pins 49 and 50, or +5 V tied to those pins through a resistor. Without that, test mode shows the coin switches stuck.

### CN6, 26-pin analog

| Pins | Function | Pins | Function |
|------|----------|------|----------|
| 1–2 | VCC | 15 | AD2 |
| 3 | AD0 | 16 | AD6 |
| 4 | AD4 | 17–18 | NC |
| 5–6 | GND | 19–20 | VCC |
| 7–8 | NC | 21 | AD3 |
| 9 | AD1 | 22 | AD7 |
| 10 | AD5 | 23–24 | GND |
| 11–14 | NC | 25–26 | NC |

### Power and JVS

| Connector | Function |
|-----------|----------|
| CN1 | 5-pin, +12 V in. 1–2 +12 V, 3 NC, 4–5 GND |
| CN2 | 5-pin, +12 V out. Same pin order |
| CN4 | USB-B |
| CN5 | USB-A |
| CN7 | 4-pin, +5 V in. 1–2 +5 V, 3–4 GND |
| CN8 | 4-pin, +5 V out. Same pin order |

## Type 2 — 837-13741 / 837-13844

Sticker 837-13844-02. Also 837-14645. The 60-pin digital header is split: a 40-pin input connector (CN8) and a 34-pin output connector (CN9). MAME marks most of those pins unknown. The rows below are only the pins that comment names.

Reported features: 2 players, 12 switch bits, 2 coin slots, 8 analog channels, 22 driver outputs. DIP switches 1–5 enable rotary, ELO touch, and printer commands. Used on F355 and Ghost Squad, among others.

### CN8, 40-pin inputs (partial)

| Pins | Function |
|------|----------|
| 3–5 | +5 V |
| 7–9 | GND |
| 13–14 | Coin SW1 / SW2 |
| 15 | Test |
| 17 | 1P Start |
| 18 | Service |
| 25 | 2P Start |
| 33–40 | RX1–RX8 |

Pins 19–24 and 31–32 are labeled only as "Switch" in that source.

### CN9, 34-pin outputs (partial)

| Pins | Function |
|------|----------|
| 1–4 | +5 V |
| 5–8 | GND |
| 9–10 | Coin meter 1 and 2 |
| 11–20 | Lamp |
| 21 | Coin LED |
| 25–32 | TX1–TX8 |
| 33–34 | +12 V |

Pins 22–24 are unmarked in that source.

### CN7, 26-pin (partial)

Named pins: 1, 7, 13, 19 are +5 V; 5, 11, 17, 23 are GND; 3, 9, 15, 21 are analog outputs. The rest of that header is blank in the MAME note.
