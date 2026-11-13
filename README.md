# Over/Under Voltage Protection Device

**Electrical & Electronics Engineering · Graduation Project**  
**Proteus simulation · Circuit design · PCB layout · Manufacturing · Custom enclosure**

An adjustable voltage-protection circuit designed to disconnect a connected load when the AC supply falls outside a selected operating range.

> **Project status:** Simulated protection behavior and a manufactured, populated PCB in a custom enclosure are documented. Full powered protection testing of the finished physical device is **not established by the supplied report**.

## Project overview

This project progressed from theoretical analysis and circuit design to schematic simulation, PCB layout, fabrication, soldering, checks, and enclosure design.

![Assembled over/under voltage protection prototype](images/01-finished-prototype.jpg)

*Physical PCB and transformer positioned inside the custom 3D enclosure.*

**[Browse all 14 project photographs and diagrams](docs/gallery.md)**

| Parameter | Design / reported value |
| --- | --- |
| Nominal AC input | 220 V, 50 Hz |
| Transformer | 220 V AC → 24 V AC |
| Control supply | 12 V DC, 7812 regulator |
| Normal operating window used in simulation | Approximately 200–240 V AC |
| Detection | Upper- and lower-limit comparator stages |
| Output control | Logic, driver and relay / contactor |
| Adjustment | Potentiometers controlling thresholds |
| Design software | Proteus / Proteus ARES |
| Enclosure software | Shapr3D |
| PCB manufacturing | Toner transfer + chemical etching; later CNC machining/drilling |

## Functional architecture

```mermaid
flowchart LR
    A["220 V AC"] --> B["Step-down transformer"]
    B --> C["Rectifier / filter"]
    C --> D["12 V regulation"]
    C --> E["Voltage sensing"]
    E --> F["Upper / lower comparators"]
    F --> G["Control logic and relay driver"]
    D --> G
    G --> H["Load-switching relay"]
```

*Functional block diagram only; use the native schematic to verify circuit-level connections.*

## Engineering workflow

1. **Analysis and schematic:** Selected components, calculated circuit parameters and designed the protection circuit.
2. **Simulation:** Evaluated the power supply and load switching under normal, low and high input voltage in Proteus.
3. **PCB design:** Placed components and routed the board in Proteus ARES, including a custom potentiometer footprint.
4. **Manufacturing iteration:** Attempted toner-transfer / chemical etching; improved board fabrication with CNC tooling after trace and drilling problems.
5. **Assembly:** Populated and soldered the board, checked component orientation, continuity and shorts.
6. **Enclosure:** Designed an enclosure with separate space for the PCB and transformer in Shapr3D.

## Project images

| Full schematic | PCB routing layout |
| --- | --- |
| ![Protection circuit schematic](images/03-complete-schematic.jpg) | ![Proteus ARES PCB routing](images/05-pcb-layout.jpg) |

| Physical board | 3D PCB model |
| --- | --- |
| ![Assembled circuit board](images/02-assembled-pcb.jpg) | ![Three-dimensional PCB layout](images/06-pcb-3d-model.jpg) |

### PCB manufacturing: two approaches

| Chemical etching | CNC production |
| --- | --- |
| ![PCB after chemical etching](images/08-chemical-etching.jpg) | ![PCB manufactured with CNC](images/09-cnc-manufacturing.jpg) |

The initial manufacturing method had difficulties with fine traces and drill-hole placement; CNC machining provided a more accurate board for assembly.

### Enclosure and simulation

| 3D enclosure CAD | Simulated power supply waveforms |
| --- | --- |
| ![Custom 3D enclosure model](images/10-enclosure-cad.jpg) | ![Proteus virtual oscilloscope output](images/11-power-supply-waveforms.jpg) |

See the [complete visual gallery](docs/gallery.md) for the comparator circuit, custom potentiometer footprint, and normal / under / over-voltage simulation screenshots.

## Example results from the report

| Simulated input | Reported load state |
| --- | --- |
| 195 V | OFF (undervoltage) |
| 200 V | ON |
| 220 V | ON |
| 240 V | ON |
| 245 V | OFF (overvoltage) |

These examples are **reported simulation/test-table results, not verified physical prototype trip measurements**. The report uses slightly differing threshold descriptions, so a hardware-calibrated threshold is not claimed. See [verification notes](docs/verification.md).

## Technical documentation

- [Project image gallery (14 images)](docs/gallery.md)
- [System design and components](docs/system-design.md)
- [PCB design and fabrication](docs/pcb-and-manufacturing.md)
- [Simulation and verification](docs/verification.md)
- [Enclosure design](docs/enclosure.md)
- [Team attribution and contributions](docs/contributions.md)
- [Original project files checklist](docs/source-files.md)

## Gallery and native source files

**Native Proteus source:** [over.and.under.voltage.device.pdsprj](./over.and.under.voltage.device.pdsprj) (uploaded in the repository root). The archive includes `ROOT.DSN` (schematic) and `ROOT.LYT` (PCB layout). Full-resolution project images, Gerber exports and native Shapr3D files may be added later.

## Notion portfolio

[View the public Engineering Portfolio on Notion](https://guttural-galliform-d52.notion.site/Engineering-Portfolio-414920417b9d8034a902d6caa11becf1) — visual project presentation with photos, diagrams and development notes.

## Safety

Academic proof-of-concept only. **Not a certified mains protection device.** Live electrical use requires suitable insulation, protective devices, enclosure design and supervised verification.

---

*Based on the supplied university graduation project report. The report describes a group project; see [attribution](docs/contributions.md) for accurate credit.*
