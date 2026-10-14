# RTL Design Workshop

This repository documents a hands-on digital-design learning path, from RTL coding and simulation to Sky130 standard-cell design and physical implementation. Each folder contains its own notes, screenshots, and workflow details.

## RTL Design and Verification

- [Day 1](DAY_1/README.md) — Multiplexer RTL and waveform verification.
- [Day 2](DAY_2/README.md) — Flip-flops, reset behavior, and module hierarchy.
- [Day 3](DAY_3/README.md) — Constant-driven logic, counters, and synthesis optimization.
- [Day 4](DAY_4/README.md) — Mux coding styles and blocking-assignment behavior.
- [Day 5](DAY_5/README.md) — `case`/`if` logic, incomplete assignments, muxes, demuxes, and a ripple-carry adder.
- [Day 6](DAY_6/README.md) — Pre- and post-synthesis design comparison.
- [Day 7](DAY_7/README.md) — Sequence-detector simulation and synthesized schematic inspection.

## Sky130 ASIC Implementation

- [Module 1](MODULE_1/README.md) — OpenLane synthesis, netlist generation, design statistics, and timing reports for `picorv32a`.
- [Module 2](MODULE_2/README.md) — Floorplanning, I/O placement, and standard-cell placement.
- [Module 3](MODULE_3/README.md) — CMOS inverter simulation, Magic layout, extracted-netlist simulation, and DRC experiments.
- [Module 4](MODULE_4/README.md) — Custom-cell integration, timing optimization, placement, CTS, and post-CTS analysis.
- [Module 5](MODULE_5/README.md) — Detailed routing, violation checks, post-route timing, and routed-layout inspection.

## Learning Flow

`RTL design and simulation` -> `synthesis and timing analysis` -> `cell characterization and layout` -> `floorplanning and placement` -> `CTS and post-CTS verification` -> `detailed routing and post-route review`

The implementation modules use the Sky130 PDK and OpenLane/OpenROAD tools with the `picorv32a` design where applicable. See each module README for its step-by-step workflow and evidence.
