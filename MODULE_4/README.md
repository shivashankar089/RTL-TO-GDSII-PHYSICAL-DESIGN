# Module 4: Pre-Layout Timing Analysis and Clock Design

This module records the completed custom-cell integration, synthesis timing optimization, floorplanning, and placement work for the Sky130 `picorv32a` design. It also introduces the timing and clock-design topics planned for the remaining labs. The screenshots in this folder document work through placement; ideal-clock STA, clock-tree synthesis (CTS), and post-CTS timing analysis are not yet included as completed results.

## Objectives

- Understand how standard-cell timing models and delay tables are used before detailed routing.
- Relate placement-grid dimensions to routing-track dimensions.
- Create a custom Sky130 inverter layout and generate its LEF abstract.
- Integrate LEF and Liberty files into the OpenLane `picorv32a` flow.
- Compare synthesis timing and area before and after timing-oriented synthesis settings.
- Review a critical timing path and verify timing through floorplanning and placement.
- Study setup and hold timing, clock uncertainty, skew, crosstalk, and CTS in the remaining labs.

## Completed Workflow

### 1. SKY130_D4_SK1 - Timing Model and Custom Cell Integration

The first part creates a custom inverter standard cell and makes its physical and timing views available to OpenLane.

1. Open `sky130_inv.mag` in Magic using the `sky130A.tech` technology setup.
2. Set the layout grid to `grid 0.46um 0.34um 0.23um 0.17um` so the geometry can be considered against the intended track/grid dimensions.
3. Check the four cell terminals and their uses: `VPWR` is power, `VGND` is ground, `A` is a signal input, and `Y` is a signal output.
4. Write the abstract from Magic with `lef write`; this produces `sky130_inv.lef`.
5. Copy the LEF and the fast, slow, and typical Liberty files into `designs/picorv32a/src/`.
6. Update `config.tcl` with `EXTRA_LEFS`, `LIB_SYNTH`, `LIB_FASTEST`, `LIB_SLOWEST`, and `LIB_TYPICAL` so the flow can load the physical and timing views.
7. Run `prep -design picorv32a` and check that the custom-cell abstract is included in `merged_unpadded.lef`.

The LEF screenshot reports a `sky130_inv` macro size of 1.380 by 2.720 microns. The Magic screenshot shows the inverter layout and the selected mask layers used while checking its geometry and terminals.

### 2. Synthesis and Timing Investigation

Run synthesis once with the default strategy, inspect the timing report, then rerun with timing-oriented synthesis settings. The recorded settings for the second run are `SYNTH_STRATEGY "DELAY 0"`, `SYNTH_BUFFERING 1`, and `SYNTH_SIZING 1`.

The default run had negative timing slack. The OpenSTA screenshot captures a register-to-register maximum path in the `clk` path group. Its logic trace passes through several combinational cells, including OR gates; the lab notes identify a long OR-reduction chain as the main source of the reported critical path. Integrating a cell's LEF and Liberty views makes them available to the flow, but does not by itself guarantee that synthesis will select that cell for the mapped netlist.

After applying the timing-oriented settings, the recorded synthesis and placement reports show zero WNS and TNS. This comes with a larger synthesis-reported chip area, demonstrating the timing-versus-area tradeoff for this run.

### 3. Floorplan and Placement

Run `run_floorplan` and then `run_placement` on the timing-optimized design. The floorplan report gives a die boundary from `(0.0, 0.0)` to `(746.915, 757.635)` microns and a core boundary from `(5.52, 10.88)` to `(741.06, 745.28)` microns.

Placement reports 18,673 instances, 20,721 nets, 41% utilization (58% padded utilization), and 270 rows. The reported WNS and TNS remain zero after placement. OpenLane also emits a placement image of the design. The message `Cannot find any macros in this design` during basic macro placement is expected here: this `picorv32a` run contains no hard macros, so there is nothing for that step to place.

## Image-by-Image Guide

The list follows the work sequence represented by the screenshots. Each image is stored alongside this README.

### Custom Cell and OpenLane Setup

#### 1. `checking_inv_magic_layout.png` - Inspecting the inverter in Magic

The Magic window has `sky130_inv` loaded. The console's `what` checks identify the selected `nwell`, `poly`, `metal1`, `ndiff`, and `pdiff` mask layers. Use this image as the layout inspection evidence; the terminal labels and cell setup are part of checking the custom cell before abstract generation.

![Magic view of the custom inverter layout](checking_inv_magic_layout.png)

#### 2. `sky130_inv_lef.png` - Generated LEF abstract

This is the LEF text for macro `sky130_inv`. It declares the macro dimensions and the physical pin shapes/directions for signal pins such as `A` and `Y`, together with the power and ground pins. This is the abstract that the physical-design flow can use instead of reopening the full Magic layout.

![Generated sky130_inv LEF abstract](sky130_inv_lef.png)

#### 3. `config_tcl.png` - Original OpenLane design configuration

This screenshot records the `picorv32a` configuration before the extra custom-cell entries are added. It shows the design name, Verilog and SDC inputs, a 5.000 ns clock period, and `clk` as the clock port/net. It provides the baseline for the configuration update in the next screenshot.

![Original picorv32a OpenLane configuration](config_tcl.png)

#### 4. `config_extra_lefs_and_libs.png` - Adding LEF and Liberty views

The updated configuration adds an `EXTRA_LEFS` glob for the design's LEF files and points the synthesis and corner-specific library variables to the copied Sky130 Liberty files. These settings connect the custom physical abstract and the timing libraries to the OpenLane run.

![OpenLane configuration with extra LEF and libraries](config_extra_lefs_and_libs.png)

### Synthesis and Timing Evidence

#### 5. `synthesis_before_fix_stats.png` - Default synthesis statistics

This report is from the default synthesis run. Its reported chip area is `147712.9184`. The lab notes record this run's timing as WNS `-24.89` and TNS `-759.46`, so the design did not meet the timing target with the default strategy.

![Default synthesis statistics](synthesis_before_fix_stats.png)

#### 6. `opensta_rpt.png` - Critical maximum-delay path

The terminal is displaying the beginning of an OpenSTA report. It identifies a rising-edge register startpoint, a register endpoint, path group `clk`, and path type `max`, then lists cells and delays along the path. The visible logic includes OR-family cells; the accompanying lab analysis attributes the critical delay to a long OR-reduction chain. This is path-level evidence, not a full setup/hold summary.

![OpenSTA critical path report](opensta_rpt.png)

#### 7. `synthesis_after_fix_stats.png` - Timing-oriented synthesis result

This synthesis report records chip area `196832.528`. The run used `SYNTH_STRATEGY "DELAY 0"`, `SYNTH_BUFFERING 1`, and `SYNTH_SIZING 1`; the lab notes report WNS `0.00` and TNS `0.00` after this change. Compare with image 5: timing improved to the recorded target while area increased.

![Timing-oriented synthesis statistics](synthesis_after_fix_stats.png)

#### 8. `post_abc_mapped_statistics.png.png` - ABC-mapped cell statistics

This screenshot shows the Yosys statistics after ABC mapping, including mapped Sky130 standard-cell types and counts. It is useful for reviewing what the synthesis flow placed in the mapped netlist; the custom cell's presence in configuration or library files should not be confused with proof that ABC selected it.

![ABC-mapped synthesis statistics](post_abc_mapped_statistics.png.png)

### Floorplan and Placement Evidence

#### 9. `floorplan_die_core_area.png` - Die and core dimensions

The terminal prints the floorplan report coordinates. The die spans `0.0 0.0 746.915 757.635` microns, while the core spans `5.52 10.88 741.06 745.28` microns. These values describe the floorplan generated before placement.

![Floorplan die and core area reports](floorplan_die_core_area.png)

#### 10. `placement_design_stats.png` - Placement and design statistics

The OpenROAD output records the placed design's instance and net counts, utilization, row count, and placement analysis. It reports 18,673 instances, 20,721 nets, 41% utilization, 58% padded utilization, and 270 rows. The output also contains legalization and HPWL details and a non-fatal warning that no power special net was found in this captured step; interpret that warning in the context of the run configuration rather than as a placement failure.

![Placement design statistics](placement_design_stats.png)

#### 11. `picorv32a_placement_layout.png` - Rendered placement

This screenshot shows the generated `picorv32a.placement.def.png` opened after placement. It is the visual view of the placed standard-cell design and complements the textual statistics in image 10.

![Placed picorv32a design](picorv32a_placement_layout.png)

## Flow Summary

`Magic inverter layout` -> `LEF generation` -> `OpenLane LEF/Liberty setup` -> `synthesis timing optimization` -> `floorplan` -> `placement` -> `ideal-clock STA` -> `CTS` -> `post-CTS timing verification`

## Author

- **Name:** Nukala Shiva Shankar
- **Roll No.:** 24EG104E28
- **College:** Anurag University