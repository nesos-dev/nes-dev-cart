# NES-DEV-CART Roadmap

## Current Status: v4.0 — Hardware Complete

The PCB design is fabrication-ready. Gerbers, BOM, and assembly files are generated. DRC clean.

## v4.1 — SPI PSRAM (In Progress)

Adding 8MB SPI PSRAM for full ROM storage beyond the FPGA's internal block RAM.

### Hardware
- [ ] Add PSRAM to PCB
- [ ] Update gerbers
- [ ] Order prototype PCBs

### FPGA Firmware
- [ ] QSPI PSRAM controller
- [ ] NES bus interface (address decode, tristate data bus)
- [ ] NROM mapper (mapper 0)
- [ ] UxROM mapper (mapper 2)
- [ ] MMC1 mapper (mapper 1)
- [ ] MMC3 mapper (mapper 4)
- [ ] CIC bypass

### Host Software
- [ ] ROM upload via UART
- [ ] Debug console
- [ ] Bus analyzer
- [ ] JTAG programming

### Documentation
- [ ] Hardware pinout reference
- [ ] Signal timing diagrams
- [ ] Mapper development guide

## Timeline

| Milestone | Target |
|-----------|--------|
| v4.1 hardware ordered | June 2026 |
| First game on real NES | July 2026 |
| Host tools + 4 mappers | August 2026 |
| Documentation + launch | September 2026 |
