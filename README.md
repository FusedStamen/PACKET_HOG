# PACKET_HOG

10-node ESP32-C5 scanner carrier board. One master, a bank of scan nodes, single USB-C power in.

Status: **IN DEV** - V4 prototypes in testing. Nothing here is validated for production yet, and nothing is for sale.

## What it is

Packet Hog C5 is a carrier board built around the Seeed XIAO ESP32-C5. One master node coordinates a bank of scanner nodes over ESP-NOW, each scanning dual-band Wi-Fi (2.4/5 GHz) and BLE. The whole array runs off a single USB-C input.

Built deliberately barebones with power distribution, node bank, antenna breakout, nothing else. I aim to ensure the core idea gets proven before anything gets added on top of it.

## Version history

- **V1** — First routed prototype. Had a wiring mistake around the CH224K USB-C PD negotiation chip: on a "smart" PD-negotiating charger, the board could get handed the wrong voltage, which risked damaging the nodes. Safe with plain 5V "dumb" chargers only.
- **V4** — Current revision. CH224K removed entirely; replaced with 5.1kΩ pull-down resistors on CC1/CC2, forcing 5V-default behavior regardless of charger. Also added reverse-polarity protection, a fuse at the power input, bulk + per-node decoupling capacitors, and 10 edge-mounted SMA connectors for external antennas.

## Status of what's tested

| Component | Status |
|---|---|
| Power distribution (V4) | Tested |
| Single-node scanning | Tested (via other builds — Piglet C5, Signal Sleuth) |
| Multi-node coordination / firmware | In dev |

## Firmware

Firmware is not yet public. It will be added here once it's actually working end to end, not before.

## License

Licensed under **CC BY-NC 4.0** - see [LICENSE](./LICENSE) for full terms.

Short version: you're free to build one for yourself and modify it for personal, non-commercial use. Selling anything built from this design — boards, kits, or products — requires explicit permission from me first. See the LICENSE file for exactly what that means.

## Contact

- Discord: `Fusedstamen`
- GitHub: [github.com/FusedStamen](https://github.com/FusedStamen)

If you want to use this commercially, reach out through one of the above. Don't assume permission — wait for a yes.

## Name

"Packet Hog" - a reference to [Bilmuri](https://bilmuri.com), not a fork or rename of anyone else's project.
