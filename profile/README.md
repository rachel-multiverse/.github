# Rachel Multiverse

**One card game. Every platform ever made. Total madness.**

## What Is This?

We're implementing the Rachel card game on EVERY computing platform that exists. From the Fairchild Channel F (1976) to iOS. If it can compute, it must run Rachel.

## The Sacred Rules

- You must play if you can (no passing allowed)
- The protocol is 64 bytes
- Every platform behaves identically
- The cards are eternal

## Primary Projects

| Project | Repository | Status |
|---------|-----------|--------|
| iOS App | [rachel-ios](https://github.com/rachel-multiverse/rachel-ios) | 📱 Pre-launch |
| Marketing Site | [rachel-site](https://github.com/rachel-multiverse/rachel-site) | 🌐 [Live](https://rachel.stevehill.xyz) |
| Documentation | [docs](https://github.com/rachel-multiverse/docs) | 📖 Active |
| Go Server | [rachel-server](https://github.com/rachel-multiverse/rachel-server) | 🔧 In development |
| Phoenix Prototype | [rachel-phoenix](https://github.com/rachel-multiverse/rachel-phoenix) | ✅ Complete |

## Vintage Platforms

| Platform | Repository | CPU | Network |
|----------|-----------|-----|---------|
| ZX Spectrum | [rachel-zx-spectrum](https://github.com/rachel-multiverse/rachel-zx-spectrum) | Z80 | Spectranet |
| Commodore 64 | [rachel-c64](https://github.com/rachel-multiverse/rachel-c64) | 6502 | WiC64 |
| Commodore 128 | [rachel-c128](https://github.com/rachel-multiverse/rachel-c128) | 8502 | User Port |
| Commodore Plus/4 | [rachel-commodore-plus4](https://github.com/rachel-multiverse/rachel-commodore-plus4) | 7501 | User Port |
| VIC-20 | [rachel-vic20](https://github.com/rachel-multiverse/rachel-vic20) | 6502 | User Port |
| Amiga | [rachel-amiga](https://github.com/rachel-multiverse/rachel-amiga) | 68000 | TCP/IP |
| Atari ST | [rachel-atari-st](https://github.com/rachel-multiverse/rachel-atari-st) | 68000 | MIDI Net |
| Atari 800 | [rachel-atari8](https://github.com/rachel-multiverse/rachel-atari8) | 6502 | SIO Port |
| Apple II | [rachel-apple2](https://github.com/rachel-multiverse/rachel-apple2) | 6502 | Super Serial |
| BBC Micro | [rachel-bbc-micro](https://github.com/rachel-multiverse/rachel-bbc-micro) | 6502 | Econet |
| Acorn Electron | [rachel-electron](https://github.com/rachel-multiverse/rachel-electron) | 6502 | Serial |
| MSX | [rachel-msx](https://github.com/rachel-multiverse/rachel-msx) | Z80 | Modem Cart |
| Amstrad CPC | [rachel-amstrad-cpc](https://github.com/rachel-multiverse/rachel-amstrad-cpc) | Z80 | Serial |
| TRS-80 | [rachel-trs80](https://github.com/rachel-multiverse/rachel-trs80) | Z80 | RS-232 |
| TRS-80 CoCo | [rachel-coco](https://github.com/rachel-multiverse/rachel-coco) | 6809 | Serial |
| Dragon 32/64 | [rachel-dragon](https://github.com/rachel-multiverse/rachel-dragon) | 6809 | Serial |
| Oric | [rachel-oric](https://github.com/rachel-multiverse/rachel-oric) | 6502 | Serial |
| Enterprise 128 | [rachel-enterprise](https://github.com/rachel-multiverse/rachel-enterprise) | Z80 | Serial |
| SAM Coupé | [rachel-samcoupe](https://github.com/rachel-multiverse/rachel-samcoupe) | Z80 | Serial |
| Sinclair QL | [rachel-ql](https://github.com/rachel-multiverse/rachel-ql) | 68008 | Serial |
| TI-99/4A | [rachel-ti99](https://github.com/rachel-multiverse/rachel-ti99) | TMS9900 | Cassette |
| MS-DOS | [rachel-dos](https://github.com/rachel-multiverse/rachel-dos) | x86 | IPX/Serial |
| Classic Mac | [rachel-mac-classic](https://github.com/rachel-multiverse/rachel-mac-classic) | 68000 | LocalTalk |

## Consoles

| Console | Repository | CPU | Network |
|---------|-----------|-----|---------|
| NES | [rachel-nintendo-nes](https://github.com/rachel-multiverse/rachel-nintendo-nes) | 6502 | Four Score |
| Game Boy | [rachel-nintendo-gameboy](https://github.com/rachel-multiverse/rachel-nintendo-gameboy) | Z80-like | Link Cable |
| Game Boy Color | [rachel-nintendo-gameboycolor](https://github.com/rachel-multiverse/rachel-nintendo-gameboycolor) | Z80-like | Link Cable |
| Master System | [rachel-sega-mastersystem](https://github.com/rachel-multiverse/rachel-sega-mastersystem) | Z80 | Link Port |
| Genesis | [rachel-sega-genesis](https://github.com/rachel-multiverse/rachel-sega-genesis) | 68000 | Meganet |
| Game Gear | [rachel-sega-gamegear](https://github.com/rachel-multiverse/rachel-sega-gamegear) | Z80 | Gear-to-Gear |
| Atari Lynx | [rachel-lynx](https://github.com/rachel-multiverse/rachel-lynx) | 65C02 | ComLynx |
| Atari 7800 | [rachel-atari-7800](https://github.com/rachel-multiverse/rachel-atari-7800) | 6502C | Controller Port |
| PC Engine | [rachel-nec-pcengine](https://github.com/rachel-multiverse/rachel-nec-pcengine) | HuC6280 | Multitap |
| ColecoVision | [rachel-coleco-colecovision](https://github.com/rachel-multiverse/rachel-coleco-colecovision) | Z80 | Expansion |

## Statistics

```
Repositories:        39
Platforms Complete:  34
iOS App:             Pre-launch
Sanity Remaining:   -200
Regrets:             0
```

## The Protocol

RUBP (Rachel Universal Binary Protocol):
- 64 bytes, fixed size
- "RACH" magic header
- Platform-agnostic
- Works on 1KB RAM

See [PROTOCOL.md](https://github.com/rachel-multiverse/docs/blob/main/PROTOCOL.md)

## The Goal

Every computer that has ever existed should be able to play Rachel against every other computer. A ZX Spectrum from 1982 should be able to play against an iPhone 16. This is insane. We're doing it anyway.

## The Motto

> "You must play if you can.
> You must port if you can.
> The protocol is sacred.
> The cards are eternal."

## Links

- [Game Rules](https://github.com/rachel-multiverse/docs/blob/main/GAME_RULES.md)
- [Protocol Specification](https://github.com/rachel-multiverse/docs/blob/main/PROTOCOL.md)
- [Marketing Site](https://rachel.stevehill.xyz)

## License

MIT - Port it to everything.

---

*Started December 2024. Estimated completion: Heat death of universe.*

*Platform counter: 39 of ∞* 🚀

**LATEST**: iOS app approaching App Store launch. 34 retro platforms implemented.
