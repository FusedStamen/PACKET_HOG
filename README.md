# PACKET_HOG

10-node ESP32-C5 scanner carrier board. One master, a bank of scan nodes, single USB-C power in.

Status: **AVAILABLE** - PacketHog-V1 is tested, assembled, and shipping. First batch of 8 for sale now. PacketHog-V2 (smaller, U.FL-based) is still in development and not yet for sale.

## What it is

Packet Hog C5 is a carrier board built around the Seeed XIAO ESP32-C5. One master node coordinates a bank of scanner nodes over ESP-NOW, each scanning dual-band Wi-Fi (2.4/5 GHz) and BLE. The whole array runs off a single USB-C input.

Built deliberately barebones with power distribution, node bank, antenna breakout, nothing else.

## Buy it

PacketHog-V1, fully assembled: **$100**, first batch of 8, shipping to the US only right now.

[fusedstamen.com/packethogv1](https://fusedstamen.com/packethogv1)

Modules (Seeed XIAO ESP32-C5) and antennas not included. Outside the US, message me on Discord and we'll figure it out.

**Note on the SMA connectors (J1-J10):** they're mounted to the board for physical support only — there's no PCB trace routing antenna signal to them. Each node module's signal reaches its SMA connector through a short U.FL-to-SMA pigtail from the module itself, not through the board's copper. Same setup as the Piglet, in case that's caused confusion before.

## Version history

- **Prototype 1** - First routed prototype. Had a wiring mistake around the CH224K USB-C PD negotiation chip: on a "smart" PD-negotiating charger, the board could get handed the wrong voltage, which risked damaging the nodes. Safe with plain 5V "dumb" chargers only.
- **Prototype 2** - CH224K removed entirely; replaced with 5.1kΩ pull-down resistors on CC1/CC2, forcing 5V-default behavior regardless of charger. Also added reverse-polarity protection, a fuse at the power input, bulk + per-node decoupling capacitors, and 10 edge-mounted SMA connectors for external antennas. Had a layout flaw: SMA connector mounts sat too close to the header pins, leaving insufficient clearance to hand-solder/route pigtail connections without crowding the header footprints. Also shipped without mounting holes, so boards couldn't be securely fastened into a case.
- **PacketHog-V1** - Current shipping revision. Fixes clearance flaw by widening the board (77.1mm → 121.1mm) to give proper spacing between the SMA connectors and the header rows. Added M3 mounting holes. Rounded board corners. SMA connectors remain hand-soldered (not PCBA-populated). Small batch (10 boards) ordered and built; tested and now shipping — see [Buy it](#buy-it) above.
- **PacketHog-V2** - Next planned revision. Reduce board size by adding on board (PCBA-populated) SMA connections utilizing U.FL jumper connections.
  
## Status of what's tested

| Component | Status |
|---|---|
| Power distribution | Tested |
| Fully populated board scanning | Tested |
| PacketHog-V1 board fab/assembly | Tested |
| Antenna path (module -> U.FL/SMA pigtail) | Tested |

## License

Licensed under **CC BY-NC 4.0** - see [LICENSE](./LICENSE) for full terms.

Short version: you're free to build one for yourself and modify it for personal, non-commercial use. Selling anything built from this design - boards, kits, or products - requires explicit permission from me first. See the LICENSE file for exactly what that means.

## Contact

- Discord: `Fusedstamen`
- GitHub: [github.com/FusedStamen](https://github.com/FusedStamen)

If you want to use this commercially, reach out through one of the above. Don't assume permission - wait for a yes.

## Name

"Packet Hog" - a reference to [Bilmuri](https://bilmuri.com), not a fork or rename of anyone else's project.
