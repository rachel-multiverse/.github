# Rachel Multiverse

**One card game. Every platform we can get an emulator for. One CPU at a time.**

## What Is This?

We're implementing the Rachel card game across vintage computers and consoles, with the same 64-byte binary protocol (RUBP) on every one — so a Dragon 32 and an Amiga build byte-identical messages on the wire. It is an absurd amount of hand-written assembly. We're doing it anyway.

## The Sacred Rules

- You must play if you can (no passing allowed)
- The protocol is 64 bytes
- Every platform speaks identical RUBP on the wire
- The cards are eternal

## Status, Honestly

**Networked play is working in tested configurations.** The native iOS and Android apps have completed Go-hosted games alongside C64 Ultimate emulation, including reconnect and an Android process restart. These runs used mobile simulators and emulators. The C64 and VIC-20 also have offline solo engines.

Evidence is specific to a build, machine and transport. A codec check proves wire encoding; an emulator run proves that emulated configuration. Physical hardware testing and a public game server remain outstanding. See each repository's verification records and the public [hardware evidence guide](https://github.com/rachel-multiverse/protocol/blob/main/HARDWARE_TESTING.md).

Platforms without an emulator yet have been parked (and their stub repos removed) until a core exists to test them against. No more imaginary checkmarks.

## Primary Projects

| Project | Repository | Status |
|---------|-----------|--------|
| iOS App | Private source | Native Apple client |
| Marketing Site | [rachel-site](https://github.com/rachel-multiverse/rachel-site) | 🌐 [Live](https://rachel.stevehill.xyz) |
| Protocol and porting guides | [protocol](https://github.com/rachel-multiverse/protocol) | Public specification and fixtures |
| Android App | Private source | Native Kotlin / Compose client |
| Go Server | Private source | Tested locally; public hosting pending |
| Phoenix Prototype | [rachel-phoenix](https://github.com/rachel-multiverse/rachel-phoenix) | 📦 Archived (reference) |

## Platforms

| Platform | Repository | CPU |
|----------|-----------|-----|
| NES | [rachel-nintendo-nes](https://github.com/rachel-multiverse/rachel-nintendo-nes) | 6502 |
| Commodore 64 | [rachel-commodore-64](https://github.com/rachel-multiverse/rachel-commodore-64) | 6502 |
| ZX Spectrum | [rachel-sinclair-zx-spectrum](https://github.com/rachel-multiverse/rachel-sinclair-zx-spectrum) | Z80 |
| Dragon 32/64 | [rachel-dragon-32](https://github.com/rachel-multiverse/rachel-dragon-32) | 6809 |
| Amiga | [rachel-commodore-amiga](https://github.com/rachel-multiverse/rachel-commodore-amiga) | 68000 |
| BBC Micro | [rachel-acorn-bbc](https://github.com/rachel-multiverse/rachel-acorn-bbc) | 6502 |
| Acorn Electron | [rachel-acorn-electron](https://github.com/rachel-multiverse/rachel-acorn-electron) | 6502 |
| Atari 800/XL | [rachel-atari-800](https://github.com/rachel-multiverse/rachel-atari-800) | 6502 |
| Atari 7800 | [rachel-atari-7800](https://github.com/rachel-multiverse/rachel-atari-7800) | 6502 |
| VIC-20 | [rachel-commodore-vic20](https://github.com/rachel-multiverse/rachel-commodore-vic20) | 6502 |
| Oric-1/Atmos | [rachel-oric](https://github.com/rachel-multiverse/rachel-oric) | 6502 |
| MSX | [rachel-msx](https://github.com/rachel-multiverse/rachel-msx) | Z80 |
| Master System | [rachel-sega-mastersystem](https://github.com/rachel-multiverse/rachel-sega-mastersystem) | Z80 |
| Game Gear | [rachel-sega-gamegear](https://github.com/rachel-multiverse/rachel-sega-gamegear) | Z80 |
| ColecoVision | [rachel-coleco-colecovision](https://github.com/rachel-multiverse/rachel-coleco-colecovision) | Z80 |
| Game Boy | [rachel-nintendo-gameboy](https://github.com/rachel-multiverse/rachel-nintendo-gameboy) | SM83 |

## Evidence and releases

The 16 vintage repositories span codec conformance, build checks and playable emulator configurations. Use [the ports page](https://rachel.stevehill.xyz/ports) and each repository's current status for release and transport details. Physical hardware support requires a recorded test on the named machine and adapter.

## The Protocol

RUBP (Rachel Unified Binary Protocol):
- 64 bytes, fixed size
- "RACH" magic header
- Big-endian, platform-agnostic
- Designed for constrained vintage clients

See [PROTOCOL.md](https://github.com/rachel-multiverse/protocol/blob/main/PROTOCOL.md). The canonical raw TCP port is **6502**; TLS uses **443**.

## The Goal

The goal is every machine playing every other machine — a ZX Spectrum from 1982 against an iPhone. Cross-platform games already run in tested native and emulator configurations. The remaining work is to extend that coverage, make recovery reliable and prove physical adapter support one configuration at a time.

## The Motto

> "You must play if you can.
> You must port if you can find an emulator.
> The protocol is sacred.
> The cards are eternal."

## Links

- [Rules and porting requirements](https://github.com/rachel-multiverse/protocol/blob/main/COMPLETE_CLIENT_PORT.md)
- [Protocol Specification](https://github.com/rachel-multiverse/protocol/blob/main/PROTOCOL.md)
- [Marketing Site](https://rachel.stevehill.xyz)

## License

MIT — port it to everything (that has an emulator).

---

*Started December 2024. Now with fewer imaginary platforms.*
