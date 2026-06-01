# NES-DEV-CART

Open-source FPGA development cartridge for the Nintendo Entertainment System. **v4.1** — now with 8MB onboard PSRAM.

Plugs into a real NES. Programs over USB-C. Debug via UART. Full NES bus access. 39 SMT components, professionally assembled.

## What Is It

NES-DEV-CART is a cartridge-shaped PCB that replaces the ROM chip with a modern FPGA. It gives your FPGA bidirectional access to every signal on the NES 72-pin cartridge connector — CPU bus, PPU bus, CIC, expansion port — all level-shifted between 5V and 3.3V.

An onboard FT2232HL provides USB-C JTAG programming and UART debug console. No external programmer needed.

## Specs

| | |
|---|---|
| **FPGA** | Sipeed Tang Primer 25K (Gowin GW5A-25, 25K LUTs) |
| **ROM Storage** | 8MB SPI PSRAM |
| **USB** | FT2232HL — Ch.A: JTAG, Ch.B: UART debug |
| **Level Shifting** | 4x 74ALVC164245DGG (bidirectional 5V-3.3V) |
| **NES Signals** | CPU A0-A14, D0-D7, PPU A0-A13, D0-D7, CIC, IRQ, EXP |
| **PCB** | 4-layer, 1.6mm, ENIG, gold fingers, L-shaped |
| **Connector** | 72-pin NES edge connector (30-degree bevel) |
| **FPGA Connection** | 2x DF40C-60DS 0.4mm B2B connectors |

## What You Can Build

- **Homebrew games** — test on real hardware, not emulators
- **Custom mappers** — design mapper chips in Verilog that never existed
- **Flash cartridge** — load ROMs from USB, run on real NES
- **Bus analyzer** — sniff CPU/PPU traffic in real time via UART
- **Expansion audio** — VRC6, Sunsoft 5B style audio hardware
- **Hardware research** — study NES bus behavior at the signal level

## Repository Structure

```
hardware/
├── nes-dev-cart.kicad_pcb      KiCad PCB layout
├── nes-dev-cart.kicad_sch      KiCad schematic
├── nes-dev-cart.kicad_pro      KiCad project
├── footprints/                 Custom footprint libraries
└── production/
    ├── nes-dev-cart-gerbers.zip    Fabrication-ready gerbers
    ├── nes-dev-cart-bom.csv        BOM with LCSC part numbers
    ├── nes-dev-cart-cpl-jlcpcb.csv Component placement list
    ├── README-assembly.md          Assembly instructions
    ├── nes-dev-cart-render-*.png   Board renders (top/bottom)
    └── gerbers/                    Individual gerber files

website/                        Product website (nesos.dev)
├── index.html
├── style.css
└── success.html
```

## Ordering PCBs

Upload `hardware/production/nes-dev-cart-gerbers.zip` to JLCPCB:

- Layers: 4
- Thickness: 1.6mm
- Surface finish: ENIG
- Gold fingers: Yes, 30-degree bevel
- Assembly: Both sides (DF40 connectors on bottom)

Upload `nes-dev-cart-bom.csv` and `nes-dev-cart-cpl-jlcpcb.csv` for SMT assembly. See `production/README-assembly.md` for details.

## Requirements

- NES front-loader console (NES-001)
- Sipeed Tang Primer 25K module
- USB-C cable
- Gowin IDE or Yosys/nextpnr for FPGA development

## License

Hardware: GPL-3.0

NES-DEV-CART is an independent project not affiliated with or endorsed by Nintendo.

## Links

- Website: https://nesos.dev
