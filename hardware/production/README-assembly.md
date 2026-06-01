# NES-DEV-CART v4.1 — JLCPCB Production & Assembly

## Board Specifications

| Parameter | Value |
|-----------|-------|
| Layers | 4 |
| Thickness | 1.6mm |
| Finish | ENIG (required for edge connector) |
| Min trace/space | 0.15mm / 0.15mm |
| Min via | 0.4mm pad / 0.2mm drill |
| Board dimensions | 100mm x 110mm (L-shaped) |
| Edge connector | Bevelled, 30-degree, bottom side |

## JLCPCB Order Settings

- **PCB**: Upload `nes-dev-cart-gerbers.zip`
- **Layers**: 4
- **PCB Thickness**: 1.6mm
- **Surface Finish**: ENIG
- **Gold Fingers**: Yes, 30-degree bevel
- **Remove Order Number**: Specify location or "Yes"

## SMT Assembly

### Assembly Type: Both Sides

- **Top side**: 36 components (passives, ICs, USB-C, crystal, LED, switch, PSRAM)
- **Bottom side**: 2 components (DF40 B2B connectors)
- **Total**: 38 SMT assembled (+ 1 card edge connector = 39 SMT pads on BOM)

### Files to Upload

| File | Purpose |
|------|---------|
| `nes-dev-cart-bom.csv` | Bill of Materials with LCSC part numbers |
| `nes-dev-cart-cpl-jlcpcb.csv` | Component Placement List (pick & place) |

### Component Summary (39 SMT parts)

| Qty | Designator | Part | LCSC | Notes |
|-----|-----------|------|------|-------|
| 15 | C1-C8,C11-C14,C16,C18,C19 | 100nF 0805 X7R | C49678 | Basic part |
| 2 | C9,C10 | 27pF 0805 NP0 | C107113 | Crystal load caps |
| 2 | C15,C17 | 4.7uF 0805 X5R | C1779 | Basic part |
| 1 | R1 | 2.2k 0805 | C17520 | Basic part |
| 1 | R2 | 10k 0805 | C17414 | Basic part |
| 2 | R3,R4 | 5.1k 0805 | C27834 | USB-C CC pull-downs |
| 1 | R5 | 330R 0805 | C17630 | LED current limit |
| 4 | U1-U4 | 74ALVC164245DGG TSSOP-48 | C5531 | Level shifters |
| 1 | U5 | FT2232HL LQFP-64 | C27882 | USB-JTAG/UART |
| 1 | Y1 | 12MHz 3225 crystal | C390764 | FT2232HL clock |
| 1 | FB1 | Ferrite 600R 0805 | C21286 | USB VBUS filter |
| 1 | D1 | Green LED 0805 | C2297 | Power indicator |
| 1 | D2 | 1N5817W SOD-123 | C571353 | Power OR diode |
| 1 | J4 | USB-C HRO TYPE-C-31-M-12 | C165948 | USB connector |
| 2 | J2,J3 | DF40C-60DS-0.4V(51) | C597938 | B2B receptacles (BOTTOM) |
| 1 | SW1 | PTS645SM43SMTR92LFS | C221880 | Reset button |
| 1 | U6 | APS6404L-3SQR-SN SOIC-8 | C5333729 | 8MB SPI PSRAM |
| 1 | C20 | 10uF 0805 X5R | C15850 | PSRAM bulk decoupling |

### NOT Assembled by JLCPCB (hand-solder)

| Designator | Part | Notes |
|-----------|------|-------|
| J5 | 2x5 pin header 2.54mm | JTAG — solder after SMT |
| J6 | 2x5 pin header 2.54mm | Expansion power header — solder after SMT |
| J1 | — | Card edge connector (no component, part of PCB) |

### Rotation Check

JLCPCB may apply rotation offsets during review. Verify orientation of:
- U1-U4 (TSSOP-48 at 90 degrees — pin 1 dot should face left)
- U5 (LQFP-64 — pin 1 dot at top-left)
- J4 (USB-C — opening faces board edge at Y=85.5)
- J2,J3 (DF40 — pin 1 at left side)
- D2 (SOD-123 — cathode band orientation)

## Post-Assembly

1. **Visual inspection** under magnification — check DF40 solder joints especially
2. **Solder J5, J6** pin headers by hand
3. **Plug in Tang Primer 25K** via DF40 connectors
4. **Connect USB-C** and verify FT2232HL enumerates (should appear as dual serial port)
5. **Program FPGA** via JTAG header or FT2232HL
