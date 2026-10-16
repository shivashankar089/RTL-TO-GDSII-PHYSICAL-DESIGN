# Course Video: VLSI Chip Design (RTL to Physical Design)

A ~16-minute walkthrough of what I learned in this course, using open-source tools, from writing RTL to the physical design flow.

## Watch the video

## Watch the video

### [👉 Click here to see the video](https://drive.google.com/file/d/1_lTXPXBqyxhfqN1JfvPyDH_VFePVhd-Z/view?usp=sharing)

| | |
|---|---|
| **Duration** | ~16 minutes |
| **Format** | MP4 (about 585 MB) |
| **Hosted on** | Google Drive |


---

## What the video covers

### Part 1: RTL Design (Day 1 to Day 7)
Writing hardware in Verilog, simulating it, and synthesizing it, always comparing what I wrote with the hardware that comes out.

| Day | Topic | Key idea |
|---|---|---|
| 1 | Multiplexer | The basic flow: RTL → simulation → synthesis |
| 2 | Flip-flops, resets, hierarchy | Async vs sync reset changes the hardware; hierarchy gets flattened |
| 3 | Constants, counter, optimization | Synthesis removes redundant logic |
| 4 | Coding styles, blocking assignments | Simulation and synthesis can disagree |
| 5 | `case` / `if`, generate, ripple-carry adder | Incomplete assignments create unwanted latches |
| 6 | VSDBabySoC (RISC-V, PLL, DAC) | Pre-synthesis vs post-synthesis behaviour |
| 7 | Sequence detector | A complete FSM from RTL to netlist |

### Part 2: Physical Design (Module 1 to Module 5)
Taking a synthesized netlist and turning it into a chip layout using the OpenLane / OpenROAD flow.

1. **Synthesis and flow introduction:** from RTL to a gate-level netlist
2. **Floorplanning and placement:** die and core size, I/O and macro placement, standard-cell placement
3. **Cell design:** standard cells at layout and SPICE level (Magic, ngspice)
4. **Pre-layout timing and clock tree synthesis:** static timing analysis with OpenSTA
5. **Power distribution and routing:** PDN, detailed routing, parasitics (SPEF)

---

## Tools used

| Stage | Tool |
|---|---|
| RTL simulation | iVerilog |
| Waveform viewing | GTKWave |
| Logic synthesis | Yosys |
| Layout | Magic |
| Circuit validation | ngspice |
| Timing analysis | OpenSTA |
| RTL-to-GDS flow | OpenLane / OpenROAD |
| Standard cell library | SkyWater sky130 |

---

## Key takeaways

- **Write RTL that maps to the hardware you intend.** A missing branch becomes a latch.
- **Never trust a single view.** Simulate before synthesis and after it (gate-level simulation).
- **Synthesis is optimization, not just translation.** It simplifies constants and redundant logic.
- **Physical design is a chain.** Floorplan, place, build the clock tree, route, and check timing at each step.

---

*Thank you!*