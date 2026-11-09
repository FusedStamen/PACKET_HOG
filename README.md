# PACKET_HOG

10-node ESP32-C5 scanner carrier board. One master, a bank of scan nodes, single USB-C power in.

Status: **PacketHog-V2 is available (limited run).** V1 (first batch of 8) is sold out. Every V2 board is assembled and checked before it ships.

## What it is

Packet Hog C5 is a carrier board built around the Seeed XIAO ESP32-C5. One master node coordinates a bank of scanner nodes over ESP-NOW, each scanning dual-band Wi-Fi (2.4/5 GHz) and BLE. The whole array runs off a single USB-C input.

Built deliberately barebones with power distribution, node bank, antenna breakout, nothing else.

Board size: 183.7mm x 121.1mm (7.23 x 4.77 in), 1.6mm thick. 
Standard case: 188.1mm x 125.5mm, about 29mm tall. 
Fan case: about 45.5mm tall.

## Buy it

PacketHog-V2: **$100**, limited run, shipping to the US only right now. Same price for every option.

[fusedstamen.com/packethogv2](https://fusedstamen.com/packethogv2)

Option at checkout: soldered RP-SMA connectors, or bare board (as received from assembly, SMA positions empty). Every board comes with the standard printed case. A case with a 30mm fan opening is available to print from this repo if you want one.

Modules (Seeed XIAO ESP32-C5), antennas and fan not included. Outside the US, message me on Discord first - import VAT, duties and carrier fees are paid by the buyer on delivery.

**Note on the RP-SMA connectors (J1-J10):** they're mounted to the board for physical support only - there's no PCB trace routing antenna signal to them. Each node module's signal reaches its SMA connector through a short U.FL-to-RP-SMA pigtail from the module itself, not through the board's copper. Same setup as the Piglet, in case that's caused confusion before.

**Mounting orientation:** every header position follows the same rule. Seat each XIAO module so its USB-C port faces the same side as the nearby capacitor (e.g. C11 sits next to the H1A/H1B pair) - that side matches the direction the onboard USB-C (J11) faces. The module's U.FL antenna pad ends up on the opposite side. Get this backwards and the module won't seat or power on correctly; double check before powering on.

## Version history

- **Prototype 1** - First routed prototype. Had a wiring mistake around the CH224K USB-C PD negotiation chip: on a "smart" PD-negotiating charger, the board could get handed the wrong voltage, which risked damaging the nodes. Safe with plain 5V "dumb" chargers only.
- **Prototype 2** - CH224K removed entirely; replaced with 5.1kΩ pull-down resistors on CC1/CC2, forcing 5V-default behavior regardless of charger. Also added reverse-polarity protection, a fuse at the power input, bulk + per-node decoupling capacitors, and 10 edge-mounted SMA connectors for external antennas. Had a layout flaw: SMA connector mounts sat too close to the header pins, leaving insufficient clearance to hand-solder/route pigtail connections without crowding the header footprints. Also shipped without mounting holes, so boards couldn't be securely fastened into a case.
- **PacketHog-V1** - Fixes the clearance flaw by widening the board (77.1mm to 121.1mm) to give proper spacing between the SMA connectors and the header rows. Added M3 mounting holes. Rounded board corners. SMA connectors hand-soldered (not PCBA-populated). First batch of 8 sold out.
- **PacketHog-V2** - Current revision. Power traces widened from 0.5mm to 1.0mm (the USB-C-to-fuse run is limited by the connector pad width). Added a 2-pin fan header (5V + GND, factory assembled). Added an AUX 5V/GND through-hole header, unpopulated, same pinout as the fan header (square pad GND, round pad +5V). Added 7 labelled test points: USB input voltage, between fuse and diode, 5V rail, far-end 5V, and 3x GND. Silkscreen cleanup; back label says V2. Power parts unchanged from V1. Still hand-soldered through-hole RP-SMA (mechanical only), plain USB-C 5V with no PD, 3A maximum (PTC fuse, fan counts against it).
- **Planned for V3** - Power switch, power LED, onboard U.FL plus edge SMA, battery input, possibly 4-layer.

**Known issue:** some nodes drop out with certain off-brand USB cables or power banks. Cause not yet measured; V2 does not claim to fix it. Use a decent USB-C cable and a supply that can deliver 5V at 3A.

## Status of what's tested

| Component | Status |
|---|---|
| Power distribution | Tested |
| Fully populated board scanning | Tested |
| PacketHog-V1 board fab/assembly | Tested |
| PacketHog-V2 board fab/assembly | Tested (each board checked before shipping) |
| Fan case (30mm) | Complete, files in this repo |
| Antenna path (module -> U.FL/SMA pigtail) | Tested |

## Thermal notes

I ran a thermal test on a V1 board in a closed case in a room at about 78F (25.5C). After 75+ minutes of running, the air inside the case levelled off around 96F (36C) and the nodes measured about 102-110F (39-43C) with a thermocouple. An IR thermometer read higher, 108-118F (42-48C), which is typical of IR on shiny surfaces, so treat the thermocouple numbers as the more reliable set. The test was on V1; V2 uses the same power parts with wider copper.

For reference, Espressif rates the ESP32-C5 modules for an operating ambient temperature of -40C to 85C (185F). The Seeed XIAO ESP32-C5 board is listed at 0C to 85C. Nodes ran well inside that range in my test, so I don't think a fan is necessary. The fan header and fan case are there if you want extra airflow or plan to run in a hot environment, such as a car parked in the sun. Those limits are ambient ratings, so a very hot environment leaves less margin.

Test data: [Packet_Hog-v1-Thermal_Testing.xlsx](./hardware/Packet_Hog-v1-Thermal_Testing.xlsx)

## License

Licensed under **CC BY-NC 4.0** - see [LICENSE](./LICENSE) for full terms.

Short version: you're free to build one for yourself and modify it for personal, non-commercial use. Selling anything built from this design - boards, kits, or products - requires explicit permission from me first. See the LICENSE file for exactly what that means.

## Contact

- Discord: `Fusedstamen`
- GitHub: [github.com/FusedStamen](https://github.com/FusedStamen)

If you want to use this commercially, reach out through one of the above. Don't assume permission - wait for a yes.

## Name

"Packet Hog" - a reference to [Bilmuri](https://bilmuri.com), not a fork or rename of anyone else's project.
