# Regulated 5 V Power Supply PCB (eSim Task 7)

A regulated 5 V power supply board with an LED indicator, designed in eSim 2.5 (KiCad-based) as Task 7 of the FOSSEE eSim Semester Long Internship, Autumn 2026. The design was submitted to the upstream repository as [PR #4](https://github.com/FOSSEE/eSim_PCB_Design_Project_Files) and merged into `main`.

## Overview

- **Project:** PowerSuplyBoardDem
- **Tools:** eSim 2.5 (eSchema for the schematic, KiCad PCB Editor for layout)
- **Input / output:** unregulated DC in, regulated 5 V DC out
- **Board:** two copper layers, all through-hole components, 33 track segments across 6 nets
- **Verification:** DRC run with 0 errors and 0 warnings, plus 3D viewer check
- **Upstream:** [FOSSEE/eSim_PCB_Design_Project_Files](https://github.com/FOSSEE/eSim_PCB_Design_Project_Files)

## Circuit

| Ref | Part | Purpose |
|---|---|---|
| D1 to D4 | eSim_Diode | Diode stage that conditions the incoming supply before regulation |
| C1 | 1000 µF electrolytic | Input filtering, reduces ripple |
| U1 | LM7805 (LM7805C_PSPICE model) | Linear regulator, fixed 5 V output |
| R1 | 330 Ω | Limits current through the LED |
| D5 | eSim_LED | Shows the 5 V output is present |

## Repository contents

| File | Description |
|---|---|
| `PowerSuplyBoardDem.kicad_sch` | Schematic |
| `PowerSuplyBoardDem.kicad_pcb` | PCB layout |
| `PowerSuplyBoardDem.kicad_pro` | KiCad project file |
| `PowerSuplyBoardDem.kicad_prl` | KiCad project local settings |
| `PowerSuplyBoardDem.proj` | eSim project file |
| `fp-info-cache` | KiCad footprint info cache |
| `eSim_Task7_PCB_Design_Report.pdf` | Full design report |
| `LICENSE` | GNU GPL v3 |

## How to open the design

1. Install [eSim](https://esim.fossee.in/) (it includes KiCad), or install KiCad on its own.
2. Clone or download this repository.
3. Open `PowerSuplyBoardDem.kicad_pro` in KiCad, or open `PowerSuplyBoardDem.proj` from eSim.
4. Open the schematic (`.kicad_sch`) or the PCB layout (`.kicad_pcb`) from the project window.

## Design notes

- This was my first PCB design. I kept the circuit simple so I could learn the full workflow: schematic capture, footprint assignment, Sch-to-PCB update, routing, DRC and 3D view.
- Through-hole footprints are used throughout (radial capacitor, TO-220-style regulator, axial diodes and resistor). Their pads connect across both copper layers, so two-layer routing needed no vias.
- Nets were first routed on F.Cu. The R1 to D5 connection was then re-routed on B.Cu to use both copper layers.
- The board outline (Edge.Cuts) is a rectangle with margin around all components.
- DRC was run repeatedly during the work, not just at the end, which helped catch issues such as an orphaned trace early.

## Report

Schematic, PCB layout, routing, DRC and 3D view screenshots are in `eSim_Task7_PCB_Design_Report.pdf`.

## Author

**Akash Goyal**
Computer Engineering, PCCOE Pune
GitHub: [@akash2042goyal](https://github.com/akash2042goyal)

## License

This project is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details.

## Acknowledgements

FOSSEE, IIT Bombay, for the eSim PCB Design project.
