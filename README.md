# Power Gating Circuit Design Project

This repository contains a Cadence Virtuoso/OpenAccess project for designing and comparing CMOS logic circuits with and without power gating techniques. The project focuses on reducing leakage power in inactive logic blocks while observing how different gating structures affect circuit behavior, static power, dynamic power, and state-retention related signals such as `Vhold`.

The database includes 62 schematic views, 16 symbol views, testbench cells, top-level integration cells, and a short Word note file for project observations.

## Project Objectives

- Build baseline CMOS logic circuits for reference measurements.
- Add power gating structures to selected circuits and compare them with the baseline versions.
- Study different gating styles, including single-gate, dual-gate, diode-assisted, and 1MOS/3MOS variants.
- Create reusable symbol views for top-level testing and final project integration.
- Prepare testbench schematics for simulation and result comparison in Cadence Virtuoso/ADE.

## Circuit Scope

The project covers the following circuit groups:

| Circuit Group | Included Designs |
| --- | --- |
| Basic gates | AND, OR, NOT, XOR, BUFFER |
| NAND | Standard NAND, transmission-style NAND, enable-only NAND, dual NAND, diode-assisted dual NAND, 1MOS/3MOS variants |
| XOR | Standard XOR, enable-only XOR, dual XOR, 1MOS/3MOS variants, HVT 3MOS variant |
| FULL ADDER | Standard FULL ADDER, power-gated FULL ADDER, dual FULL ADDER, 1MOS/3MOS variants |
| DFF | Standard DFF, DFF-only version, power-gated DFF, dual DFF |
| Power gating block | Multiple versions of the reusable power-gating cell |

## Repository Structure

| Path | Purpose |
| --- | --- |
| `LogicGates/` | Baseline logic gate library containing AND, OR, NOT, XOR, and BUFFER schematic cells. |
| `Power_gating/` | First version of the reusable power-gating schematic. |
| `Power_gating_ver2/` | Second power-gating iteration, including the `Ver2` schematic cell. |
| `Power_gating_ver3/` | Third power-gating iteration with schematic and symbol views, plus a test schematic. |
| `Tatcamach_1/` | Early circuit set for NAND, FULL ADDER, and DFF experiments, including 1MOS/3MOS variants. |
| `Tatcamach_2/` | Extended circuit set for BUFFER, NAND, XOR, DFF, FULL ADDER, and power-gating variants. |
| `CUOI_KY_SYMBOL/` | Final top-level cells, symbols, and testbenches used for project integration and reporting. |
| `TEST/` | Additional test cells and testbenches for NAND/XOR enable and dual-gate experiments. |
| `vhold-signal-notes.docx` | Short project notes related to the `Vhold` signal and power measurements. |

## Important Cell Sets

### Final Top-Level Cells

The `CUOI_KY_SYMBOL/` library contains final top-level schematic/symbol cells and their matching testbenches:

- `NAND_top`, `NAND_PG_top`, `NAND_DUAL_top`, `NAND_DUAL_DIODE_top`
- `FA_top`, `FA_PG_top`, `FA_DUAL_top`
- `DFF_top`, `DFF_PG_top`, `DFF_DUAL_top`, `DFF_only_top`
- Matching `_tb` cells for simulation testbenches

These cells are the most useful entry points when reviewing the complete design variants.

### Experimental Circuit Libraries

`Tatcamach_1/` and `Tatcamach_2/` contain earlier and extended experiment versions. They are useful for tracing the design evolution from baseline CMOS gates to power-gated implementations.

Examples:

- `NAND`, `NAND#2b1MOS`, `NAND#2b3MOS`
- `FULLADDER`, `FULLADDER#2b1MOS`, `FULLADDER#2b3MOS`
- `XOR`, `XOR#2b1MOS`, `XOR#2b3MOS`, `XOR#2b3MOShvt`
- `DFF`, `DFF_PG`, `DFF_only`
- `BUFFER`, `BUFFER#2b1MOS`, `BUFFER#2b3MOS`

The `#2b` sequence is preserved from the Cadence/OpenAccess database naming. These folders should be renamed from inside Cadence Virtuoso if a cleaner cell name is needed.

## Naming Convention

| Name Pattern | Meaning |
| --- | --- |
| `_top` | Top-level cell intended for integration or final comparison. |
| `_tb` | Testbench schematic for simulation. |
| `_PG` | Power-gated circuit variant. |
| `_DUAL` | Dual-gate or dual-structure comparison variant. |
| `_DIODE` | Diode-assisted variant. |
| `_EN_ONLY` | Enable-only variant used for comparison. |
| `1MOS` / `3MOS` | Variants that modify the gating structure with 1MOS or 3MOS configurations. |
| `hvt` | High-threshold-voltage related variant. |

## Cadence/OpenAccess Data Format

This repository follows the standard Cadence/OpenAccess library structure. Important files include:

- `sch.oa`: schematic database.
- `symbol.oa`: symbol database.
- `master.tag`: Cadence view metadata.
- `data.dm`, `.oalib`, `cdsinfo.tag`: library and cell metadata.
- `thumbnail_128x128.png`: schematic/symbol preview image.
- `data.sdb`: ADE/analysis database file where present.

Most design files are Cadence database files, so GitHub may not show a programming language breakdown for this repository. That is expected because GitHub Linguist does not classify OpenAccess database files as source code languages.

## Recommended Workflow

1. Clone the repository:

   ```bash
   git clone https://github.com/cta1511/power-gating.git
   ```

2. Open Cadence Virtuoso with the required PDK and technology setup for the project environment.

3. Add or attach the OpenAccess libraries from the repository directories, especially:

   - `LogicGates`
   - `Power_gating_ver3`
   - `Tatcamach_2`
   - `CUOI_KY_SYMBOL`
   - `TEST`

4. Start from the final top-level cells in `CUOI_KY_SYMBOL/` when reviewing the finished project.

5. Open the matching `_tb` cells to run simulations and compare baseline, power-gated, dual, and diode-assisted variants.

6. Record simulation results such as static power, dynamic power, delay, and hold behavior in a separate report or notes file.

## What To Compare In The Project

The main comparison points are:

- Baseline circuit power versus power-gated circuit power.
- Static/leakage power reduction when a circuit is inactive.
- Dynamic power behavior when the circuit switches.
- Impact of 1MOS, 3MOS, dual, and diode-assisted gating structures.
- Whether `Vhold` or related retention behavior remains valid during the sleep/hold state.
- Functional correctness of each circuit variant under the provided testbenches.

## Notes For Updating The Repository

The following local or temporary files are intentionally ignored:

- `.DS_Store`
- `*.cdslck*`
- `sch.oa.cadence.*.tmp.*`
- temporary `.tmpADEDir` result directories
- Microsoft Office temporary files matching `~$*`

When committing updates, include only design files, schematic/symbol databases, testbenches, and project documents that should be preserved. Avoid committing Cadence lock files, temporary ADE result directories, or machine-specific setup files.

## Naming Safety

Cadence/OpenAccess library and cell directory names are intentionally kept unchanged in Git. Renaming those directories directly in the filesystem can break schematic references, symbol links, or library metadata. If a cell or library must be renamed, rename it inside Cadence Virtuoso first, verify that all references still resolve, and then commit the resulting database changes.

## Author

Cao Thanh An, GitHub: [cta1511](https://github.com/cta1511)
