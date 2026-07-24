# JVS — JAMMA Video Standard

Self-contained technical summary of the JAMMA Video Standard (JVS), the digital I/O successor to the classic analog JAMMA edge connector. Used by Sega Naomi family, Chihiro, Triforce, Lindbergh, RingEdge, many Namco, Taito, and later PC-based arcade systems.

## Local primary documents
- English WIP translation: [`files/jvs/jvs_wip.pdf`](../files/jvs/jvs_wip.pdf)
- HTML snapshot (sega.bsnk.me): [`files/jvs/sega-bsnk-jvs.html`](../files/jvs/sega-bsnk-jvs.html)

This file also contains the core protocol data so the repository is usable offline without those PDFs.

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
- **Escape**: If a data byte is 0xE0 or 0xD0 it is escaped with MARK 0xD0 followed by the inverted/specially coded byte (0xDF for original 0xE0, 0xCF for original 0xD0).
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
See [`files/jvs/jvs_wip.pdf`](../files/jvs/jvs_wip.pdf) for the full English command tables, report formats, and I/O board feature bits. This Markdown summary intentionally stays compact; the PDF is the offline authority for edge cases.
