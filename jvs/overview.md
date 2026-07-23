# JVS — JAMMA Video Standard

Self-contained technical summary of the JAMMA Video Standard (JVS), the digital I/O successor to the classic analog JAMMA edge connector. Used by Sega Naomi family, Chihiro, Triforce, Lindbergh, RingEdge, many Namco, Taito, and later PC-based arcade systems.

This file contains the core protocol data so the repository is usable offline.

## Physical Layer

- Serial: EIA/TIA RS-485, half-duplex, multi-drop
- Connectors: USB Type-A (host/outgoing) and USB Type-B (device/incoming) for daisy-chaining I/O boards
- Signaling: differential DATA+ / DATA-
- Sense line: used for automatic node addressing during initialization (pull-down sense)
- Baud rate: 115200, 8 data bits, no parity, 1 stop bit (8N1)
- Typical cable: USB-A to USB-B with the four wires mapped to Sense, DATA-, DATA+, GND

## Packet Structure

Every frame begins with the SYNC byte.

```
SYNC (0xE0) | Node Address | Byte Count | Data / Commands ... | SUM
```

- **SYNC**: 0xE0
- **Escape**: If a data byte is 0xE0 or 0xD0 it is escaped with MARK 0xD0 followed by the inverted/ specially coded byte (0xDF for original 0xE0, 0xCF for original 0xD0).
- **Node Address**: 0x00 = master, 0x01–0x1F = slaves, 0xFF = broadcast
- **Byte Count**: number of bytes that follow (including the SUM), excluding SYNC
- **SUM**: 8-bit checksum of all bytes after SYNC (modulo 256)

Master initiates all communication. Slaves reply with status + report bytes.

## Initialization Sequence

1. Master sends Reset command (0xF0 0xD9) twice.
2. Master broadcasts Set Address (0xF1) while Sense line propagates through the daisy chain so each board receives a unique address from farthest to nearest.
3. Master can then query Identify, Feature Check, etc.

## Key Commands (selected)

### Global / Init
- 0xF0 0xD9 : Reset
- 0xF1 addr : Set Address
- 0xF2 : Change communication method / baud (broadcast)

### Identification & Features
- 0x10 : I/O Identify (returns ASCII string: maker, board, version)
- 0x11 : Command Revision
- 0x12 : JVS Revision
- 0x13 : Communication Version
- 0x14 : Feature Check (returns list of supported functions: switches, coin, analog, outputs, etc.)

### Inputs
- 0x20 : Switch Inputs (digital buttons / sticks, bitmapped)
- 0x21 : Coin Inputs (counts + status)
- 0x22 : Analog Inputs (10-bit values packed)
- 0x23 : Rotary / Encoder
- 0x24 : Keycode
- 0x25 : Screen Position (light gun style)
- 0x26 : Misc switches

### Outputs
- 0x30 : Coin Counter Decrease
- 0x31 : Payout Increase
- 0x32 / 0x37 / 0x38 : Generic digital outputs
- 0x33 : Analog outputs
- 0x34 : Character / LED display output

Manufacturer-specific extensions exist (Taito Type X, Namco, etc.).

## Status / Report Codes

- Status 0x01 : Normal
- 0x02 : Unknown command
- 0x03 : Checksum error
- 0x04 : Busy / overflow / parameter error

Report codes follow a similar pattern (0x01 normal, 0x02 parameter error).

## Power & Connectors (JVS systems)

JVS systems typically use separate connectors:
- Power: JST-VL style with +5 V, +3.3 V, +12 V, GND (sequencing important: 3.3 V before 5 V on some boards)
- Video: HD-15 (VGA pinout) for RGBHV or RGBS
- Audio: Stereo RCA
- I/O: the USB-style JVS cable

Many cabinets still provide a classic JAMMA edge via the I/O board for compatibility with older PCBs or for simple wiring.

## Common Sega I/O Boards

Sega 838-xxxxx series (various revisions for Naomi, Chihiro, etc.). Namco, Taito, and third-party I/O boards also exist. Daisy-chaining allows multi-player or multi-I/O setups.

## Conversion Notes

- JVS ↔ JAMMA adapters / I/O boards are common for running JVS systems in classic cabinets or vice-versa.
- Sense line must be handled correctly for addressing.
- Some systems require specific I/O board firmware or DIP settings.

## Sources for This Summary

Compiled from public reverse-engineering and the widely circulated English translation of the JVS 3rd Edition (trap15 / daifukkat.su), sega.bsnk.me notes, OpenJVS implementations, and community documentation. For the full formal text see the linked PDF; the tables and structure above are sufficient for most practical work and implementations.

Expand with specific board pinouts or command traces as needed.
