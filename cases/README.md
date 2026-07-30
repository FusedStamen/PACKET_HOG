# StamenScan Case Hardware Guide

This document lists the fasteners and hardware needed to assemble the 3D-printed
cases for the StamenScan V5 and V6 carrier boards. Standoffs and mounting bosses
are printed as part of the case; everything below is hardware you need to source
separately.

---

## V1 Case (board-mounted SMA version)

The V1 case mounts the **lid straight through the board** into the same
standoffs that hold the board down — one screw per corner does both jobs.
The board itself has no independent fastener; it's held in place by the SMA
connector friction fit plus the tight (0.2mm) case-to-board clearance.

| Item | Spec | Qty | Notes |
|---|---|---|---|
| Standoff insert | M3 × D5 × L4 heat-set insert | 4 | Presses into the 4 printed standoff bosses (9mm OD boss, sized for this insert) |
| Combined mounting screw | M3, ~8-10mm length | 4 | Passes through lid → through board → into the standoff insert |

**Case details:**
- Wall thickness: 2mm
- PCB-to-wall clearance: 0.2mm (tight fit, benchmarked against a reference design)
- 10 SMA ports (5 per side) with a shallow 1mm filleted relief around each hole for connector/nut clearance
- USB-C cutout: 7mm × 14mm
- Lid includes 10 small tab plugs that seat into the open tops of the SMA slots when closed

> **Screw length note:** the combined screw needs to span the lid (2mm) + PCB
> (~1.5mm) + insert engagement (4mm) ≈ 7.5mm minimum. An 8mm screw is the
> practical minimum; 10mm gives more thread engagement margin. Verify against
> your actual printed parts before ordering in bulk.

