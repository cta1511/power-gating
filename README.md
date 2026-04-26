# Power Gating

This project contains Cadence/OpenAccess circuit designs and simulations for logic circuits that use power gating techniques.

The repository stores schematic cells, symbols, testbenches, and supporting documentation for studying power gating on basic logic blocks such as NAND, XOR, BUFFER, DFF, and FULL ADDER circuits.

## Overview

- Designs for basic logic gates.
- Comparisons between regular circuits, power-gated circuits, and dual/diode variants.
- Cadence/OpenAccess schematic, symbol, and testbench databases.
- A Word document with notes and observations related to the Vhold signal path.

## Repository Structure

| Path | Description |
| --- | --- |
| `LogicGates/` | Basic logic gates: AND, OR, NOT, XOR, and BUFFER. |
| `Power_gating/` | Initial power gating design. |
| `Power_gating_ver2/` | Second version of the power gating design, including the `Ver2` cell. |
| `Power_gating_ver3/` | Third version of the power gating design, including schematic and symbol views. |
| `Tatcamach_1/` | NAND, FULL ADDER, DFF, and 1MOS/3MOS circuit variants. |
| `Tatcamach_2/` | Extended design set with BUFFER, NAND, XOR, DFF, FULL ADDER, and power gating variants. |
| `CUOI_KY_SYMBOL/` | Top-level cells, symbols, and testbenches used for final integration/report work. |
| `TEST/` | Test cells and testbenches for NAND/XOR circuits. |
| `vhold-signal-notes.docx` | Notes related to the Vhold signal path. |

## Data Format

This project follows the Cadence/OpenAccess library directory structure. Important file types include:

- `sch.oa`: schematic data.
- `symbol.oa`: symbol data.
- `master.tag`: view metadata for a cell.
- `data.dm`, `.oalib`, `cdsinfo.tag`: library/cell metadata.
- `thumbnail_128x128.png`: preview image for a schematic or symbol view.

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/cta1511/power-gating.git
   ```

2. Open the project in a Cadence Virtuoso/OpenAccess environment.

3. Load the required libraries from directories such as `LogicGates`, `Power_gating_ver3`, `Tatcamach_2`, and `CUOI_KY_SYMBOL`.

4. Open schematic cells or testbenches from Library Manager to inspect, edit, and run simulations.

## Naming Notes

The Word document was renamed to an English, repository-friendly filename: `vhold-signal-notes.docx`.

Cadence/OpenAccess library and cell directory names are intentionally kept unchanged. Renaming those directories directly in Git can break schematic references and library metadata, so any future library/cell rename should be done inside Cadence Virtuoso first and then committed to Git.

## Notes For Updates

The repository ignores local system files, temporary files, and Cadence lock files, including:

- `.DS_Store`
- `*.cdslck*`
- `sch.oa.cadence.*.tmp.*`
- temporary `.tmpADEDir` result directories
- Microsoft Office temporary files matching `~$*`

When committing new changes, only include design files, symbols, schematics, testbenches, and documents that should be preserved.

## Author

This project was created for designing and studying power gating circuits.
