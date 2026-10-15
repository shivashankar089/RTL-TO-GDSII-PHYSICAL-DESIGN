# RTL Design and ASIC Physical-Design Portfolio

This repository documents a practical digital-design learning path, beginning with small Verilog RTL examples and simulation-based verification and extending through synthesis, standard-cell layout, floorplanning, placement, clock-tree synthesis (CTS), detailed routing, and static timing analysis (STA).

The material is organized as two complementary tracks:

1. **Days 1–7** build RTL and verification fundamentals using examples such as multiplexers, flip-flops, counters, conditional logic, arithmetic, and a sequence detector.
2. **Modules 1–5 and the VSDBabySoC post-route STA work** apply those digital-design ideas to ASIC implementation flows with Sky130, OpenLane, OpenROAD, Magic, ngspice, Yosys, and OpenSTA.

Each topic folder has its own README with step-by-step notes and image links. Use this page as the map of the full project; follow the topic links for the detailed walkthroughs and evidence.

## At a Glance

| Track | Scope | Main focus |
|---|---|---|
| RTL design and verification | Day 1–7 | Combinational and sequential RTL, simulation, waveforms, synthesis views, and design behavior |
| Sky130 ASIC implementation | Module 1–5 | `picorv32a` synthesis through detailed routing, plus custom-cell and timing experiments |
| VSDBabySoC physical design and STA | Separate post-route folder | Floorplanning, placement, CTS, routing evidence, and pre-/post-route 16-corner reports |

The two physical-design examples should be read as separate project records: Modules 1–5 focus primarily on `picorv32a`, while the post-route STA folder documents a VSDBabySoC run. Their screenshots and timing reports are evidence for their respective designs and stages, not one continuous run.

## RTL Design and Verification: Day 1–7

The daily exercises move from simple combinational logic toward sequential behavior and synthesis interpretation. They show how RTL descriptions, simulated waveforms, and synthesized structures relate, and why completeness and coding intent matter.

### Day-by-Day Guide

| Day | Concepts and work | Detailed guide |
|---|---|---|
| **Day 1** | Describe a combinational multiplexer, check its selected output for changing inputs, and inspect its waveform. | [Day 1 README](DAY_1/README.md) |
| **Day 2** | Model D flip-flops; compare synchronous and asynchronous reset behavior; organize designs into modules and inspect hierarchy and flattening. | [Day 2 README](DAY_2/README.md) |
| **Day 3** | Compare constant-driven sequential examples in simulation and Yosys, inspect a counter, and observe synthesis optimization. | [Day 3 README](DAY_3/README.md) |
| **Day 4** | Examine mux coding styles, ternary operators, and blocking-assignment behavior by comparing simulation with Yosys views. | [Day 4 README](DAY_4/README.md) |
| **Day 5** | Study complete and incomplete `case`/`if` assignments, generated mux/demux structures, gate-level and synthesis views, and a ripple-carry adder. | [Day 5 README](DAY_5/README.md) |
| **Day 6** | Compare design representations before and after synthesis to see the transition from RTL to implementation-oriented logic. | [Day 6 README](DAY_6/README.md) |
| **Day 7** | Follow a sequence detector through simulation waveforms, output behavior, and a synthesized schematic. | [Day 7 README](DAY_7/README.md) |

### What the RTL Exercises Demonstrate

- **Combinational intent:** A mux should select the intended input without inferring storage; complete assignments help avoid unintended latch behavior.
- **Sequential state and reset:** Flip-flops introduce state, and synchronous and asynchronous reset styles produce different timing behavior.
- **Hierarchy and optimization:** Designs can be composed from submodules, flattened, and simplified through synthesis; simulation and netlist views provide complementary evidence.
- **Coding style and behavior:** `if`, `case`, ternary operators, blocking assignments, and generate constructs affect how logic is described and interpreted.
- **Arithmetic and finite-state behavior:** The counter, ripple-carry adder, and sequence detector illustrate designs whose behavior must be followed across clock events and verified over time.

## Sky130 ASIC Implementation: Modules 1–5

These modules document a physical-design learning path centered on the Sky130 PDK and `picorv32a`. The path starts with synthesis and timing reports, builds through floorplanning and placement, explores a custom inverter cell and timing optimization, and then follows clock-tree synthesis and routing.

### Module Guide

| Module | Main stage | Detailed guide |
|---|---|---|
| **Module 1 — Synthesis** | Explore the OpenLane setup, configure `picorv32a`, inspect Yosys synthesis statistics and the synthesized netlist, calculate the flip-flop ratio, and review OpenSTA timing reports. | [Module 1 README](MODULE_1/README.md) |
| **Module 2 — Floorplanning and placement** | Review design and floorplan settings, generate the floorplan DEF, inspect I/O placement, and view the floorplan and standard-cell placement in Magic. | [Module 2 README](MODULE_2/README.md) |
| **Module 3 — Cell design and characterization** | Use ngspice to compare two CMOS inverter sizing cases, inspect their DC transfer and transient responses, create a Magic layout, simulate an extracted netlist, and examine poly/nwell DRC examples. | [Module 3 README](MODULE_3/README.md) |
| **Module 4 — Timing and clock design** | Integrate a custom inverter LEF/Liberty view, compare default and timing-oriented synthesis, inspect critical paths, and follow floorplanning, placement, CTS, and post-CTS STA. | [Module 4 README](MODULE_4/README.md) |
| **Module 5 — Routing and post-route review** | Inspect post-CTS STA setup, TritonRoute iterations and completion, routing violation checks, timing evidence, and routed geometry at chip and cell scale. | [Module 5 README](MODULE_5/README.md) |

### How the Physical-Design Work Connects

1. **Synthesize and establish a baseline.** OpenLane/Yosys translate RTL into a mapped netlist. Cell statistics, the flop-ratio calculation, and OpenSTA reports provide structural and timing evidence for the synthesized design.
2. **Define the physical context.** Floorplanning settings determine the die/core arrangement and I/O strategy. The floorplan DEF and Magic views make the physical boundary, rows, and pin placement inspectable.
3. **Relate a circuit to its physical and timing models.** Module 3 characterizes an inverter with ngspice, creates its layout in Magic, and studies extracted behavior and DRC rules. Module 4 takes this further by preparing a custom inverter's LEF and Liberty views for use in the `picorv32a` flow.
4. **Investigate timing tradeoffs.** Module 4 records a default synthesis result with negative slack and a timing-oriented synthesis configuration that reaches the recorded zero WNS/TNS at increased area. The notes also review ideal-clock STA, clock-tree insertion, skew, and post-CTS timing.
5. **Route and inspect the implementation.** Module 5 documents routing optimization, completion, violation checks, post-route timing evidence, and full-chip/local views of the routed layout.

These steps expose the connection between logical behavior and physical implementation: synthesis choices affect area and timing, floorplan and placement create the physical context for clock distribution, and routing adds further physical effects that require post-route review.

## VSDBabySoC: Post-Route Physical Design and STA

The [VSDBabySoC post-route README](POSTROUTE_STA_VSDBabySoC/README.md) documents a separate implementation record. Its images show floorplanning, placement, CTS, routing, and OpenROAD timing views. The folder also includes both a pre-route and post-route 16-corner STA report:

- [Pre-route 16-corner STA report](POSTROUTE_STA_VSDBabySoC/PRE_STA_16_CORNERS_REPORT.pdf)
- [Post-route 16-corner STA report](POSTROUTE_STA_VSDBabySoC/POST_STA_16_CORNERS_REPORT.pdf)

The screenshots preserve intermediate states as well as later results. For example, the initial global-routing capture shows congestion, while the detailed-routing completion capture reports zero net and pin violations in that run. For cross-stage timing comparison, consult the pre-route and post-route reports directly; do not treat an intermediate GUI chart or a different project's report as a substitute for the corner-specific STA evidence.

## Overall Learning Path

```text
RTL fundamentals and coding styles (Days 1–5)
                    |
                    v
         Synthesis comparison (Day 6)
                    |
                    v
      Sequential design verification (Day 7)
                    |
                    v
   OpenLane synthesis and timing (Module 1)
                    |
                    v
 Floorplanning and placement (Module 2)
                    |
                    v
 Circuit characterization and layout (Module 3)
                    |
                    v
 Timing optimization, CTS, and post-CTS STA (Module 4)
                    |
                    v
     Detailed routing and post-route review (Module 5)

 VSDBabySoC: independent floorplan-to-route record
             + pre-/post-route 16-corner STA
```

The diagram describes the conceptual progression of the material. Individual folders record specific exercises, runs, and evidence; it does not imply that every day or module uses the same design or forms one uninterrupted tool run.

## Tools and Artifacts

The documented work uses tools and artifacts from several parts of the digital-design flow:

- **RTL and logic:** Verilog HDL, Yosys, and gate-level/synthesis views.
- **Simulation and waveform inspection:** RTL simulation, GTKWave, and ngspice.
- **Cell layout and rule inspection:** Magic and Sky130 technology/DRC files.
- **ASIC implementation:** Sky130 PDK, OpenLane, and OpenROAD, including floorplanning, placement, CTS, and routing.
- **Timing analysis:** OpenSTA and setup/hold, slack, skew, and corner-report evidence.
- **Project evidence:** README walkthroughs, linked screenshots, terminal output, layout views, netlists, and STA PDF reports.

The images are linked from their respective folders so that the explanation stays next to the evidence. Each detailed README describes what its screenshots show and, where relevant, distinguishes intermediate results from final run summaries.

## Suggested Reading Order

1. Read [Days 1–7](DAY_1/README.md) in order to follow the RTL, simulation, and synthesis concepts.
2. Start the ASIC-flow record with [Module 1](MODULE_1/README.md), then follow [Module 2](MODULE_2/README.md) through floorplanning and placement.
3. Read [Module 3](MODULE_3/README.md) for inverter-level characterization, layout, extraction, and DRC.
4. Continue with [Module 4](MODULE_4/README.md) for custom-cell integration, timing optimization, CTS, and post-CTS analysis, followed by [Module 5](MODULE_5/README.md) for routing and post-route review.
5. Read the separate [VSDBabySoC post-route guide](POSTROUTE_STA_VSDBabySoC/README.md) alongside its two 16-corner STA reports.
