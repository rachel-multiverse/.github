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

**Nothing plays over a network yet.** No emulated vintage machine has a working transport, so there's no cross-platform play today. What we *do* have is **wire-codec conformance**: each client's real assembly runs on its real CPU under a headless emulator, and the RUBP messages it builds and parses are checked — byte-for-byte — against the golden fixtures shared with the iOS reference and the Go server.

- ✅ **Conformant** — codec verified against the golden RUBP vectors on the real machine
- 🔬 **Emulator ready** — client and emulator both exist; conformance pass not yet run

Platforms without an emulator yet have been parked (and their stub repos removed) until a core exists to test them against. No more imaginary checkmarks.

## Primary Projects

| Project | Repository | Status |
|---------|-----------|--------|
| iOS App | [rachel-ios](https://github.com/rachel-multiverse/rachel-ios) | 📱 Pre-launch |
| Marketing Site | [rachel-site](https://github.com/rachel-multiverse/rachel-site) | 🌐 [Live](https://rachel.stevehill.xyz) |
| Documentation | [docs](https://github.com/rachel-multiverse/docs) | 📖 Active |
| Go Server | [rachel-server](https://github.com/rachel-multiverse/rachel-server) | 🔧 In development |
| Phoenix Prototype | [rachel-phoenix](https://github.com/rachel-multiverse/rachel-phoenix) | 📦 Archived (reference) |

## Platforms

| Platform | Repository | CPU | RUBP |
|----------|-----------|-----|------|
| NES | [rachel-nintendo-nes](https://github.com/rachel-multiverse/rachel-nintendo-nes) | 6502 | ✅ Conformant |
| Commodore 64 | [rachel-commodore-64](https://github.com/rachel-multiverse/rachel-commodore-64) | 6502 | ✅ Conformant |
| ZX Spectrum | [rachel-sinclair-zx-spectrum](https://github.com/rachel-multiverse/rachel-sinclair-zx-spectrum) | Z80 | ✅ Conformant |
| Dragon 32/64 | [rachel-dragon-32](https://github.com/rachel-multiverse/rachel-dragon-32) | 6809 | ✅ Conformant |
| Amiga | [rachel-commodore-amiga](https://github.com/rachel-multiverse/rachel-commodore-amiga) | 68000 | ✅ Conformant |
| BBC Micro | [rachel-acorn-bbc](https://github.com/rachel-multiverse/rachel-acorn-bbc) | 6502 | 🔬 Emulator ready |
| Acorn Electron | [rachel-acorn-electron](https://github.com/rachel-multiverse/rachel-acorn-electron) | 6502 | 🔬 Emulator ready |
| Atari 800/XL | [rachel-atari-800](https://github.com/rachel-multiverse/rachel-atari-800) | 6502 | 🔬 Emulator ready |
| Atari 7800 | [rachel-atari-7800](https://github.com/rachel-multiverse/rachel-atari-7800) | 6502 | 🔬 Emulator ready |
| VIC-20 | [rachel-commodore-vic20](https://github.com/rachel-multiverse/rachel-commodore-vic20) | 6502 | 🔬 Emulator ready |
| Oric-1/Atmos | [rachel-oric](https://github.com/rachel-multiverse/rachel-oric) | 6502 | 🔬 Emulator ready |
| MSX | [rachel-msx](https://github.com/rachel-multiverse/rachel-msx) | Z80 | 🔬 Emulator ready |
| Master System | [rachel-sega-mastersystem](https://github.com/rachel-multiverse/rachel-sega-mastersystem) | Z80 | 🔬 Emulator ready |
| Game Gear | [rachel-sega-gamegear](https://github.com/rachel-multiverse/rachel-sega-gamegear) | Z80 | 🔬 Emulator ready |
| ColecoVision | [rachel-coleco-colecovision](https://github.com/rachel-multiverse/rachel-coleco-colecovision) | Z80 | 🔬 Emulator ready |
| Game Boy | [rachel-nintendo-gameboy](https://github.com/rachel-multiverse/rachel-nintendo-gameboy) | SM83 | 🔬 Emulator ready |

## Statistics

```
Platform repos:        16
RUBP-conformant:        5   (NES, C64, Spectrum, Dragon, Amiga)
Emulator-ready:        11
Networked cross-play:   0   (the dream)
Sanity Remaining:    -200
Regrets:                0
```

## The Protocol

RUBP (Rachel Universal Binary Protocol):
- 64 bytes, fixed size
- "RACH" magic header
- Big-endian, platform-agnostic
- Runs on 1KB of RAM

See [PROTOCOL.md](https://github.com/rachel-multiverse/docs/blob/main/PROTOCOL.md)

## The Goal

The dream is every machine playing every other machine — a ZX Spectrum from 1982 against an iPhone. We are nowhere near that. Right now we're proving the wire format is genuinely identical on real silicon, one CPU at a time, and building the emulator coverage to test the rest. The dream is insane. We chip at it anyway.

## The Motto

> "You must play if you can.
> You must port if you can find an emulator.
> The protocol is sacred.
> The cards are eternal."

## Links

- [Game Rules](https://github.com/rachel-multiverse/docs/blob/main/GAME_RULES.md)
- [Protocol Specification](https://github.com/rachel-multiverse/docs/blob/main/PROTOCOL.md)
- [Marketing Site](https://rachel.stevehill.xyz)

## License

MIT — port it to everything (that has an emulator).

---

*Started December 2024. Now with fewer imaginary platforms.*
