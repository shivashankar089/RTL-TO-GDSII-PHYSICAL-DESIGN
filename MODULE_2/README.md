# Floorplanning and Placement - Picorv32a

This directory documents the floorplanning, I/O placement, and initial placement stages of the `picorv32a` RISC-V core using the **OpenLane** RTL-to-GDSII flow and the **Sky130** process design kit (PDK). Floorplanning converts the synthesized design into a physical die and core arrangement. I/O placement assigns locations to the design pins, and placement arranges the standard cells inside the core area.

## Workflow

The screenshots below are arranged in the order in which the physical-design flow executes. They are not listed alphabetically.

### 1. Reviewing the Main Design Configuration (`config.tcl`)

**Explanation:** This configuration identifies the design as `picorv32a`, points OpenLane to the Verilog and SDC files, sets the clock period to 5 ns, and defines `clk` as the clock port. It also loads the standard-cell-library configuration when that file exists. This is the starting point for the physical-design run because the later stages need the design name, source files, and timing information.

![Main picorv32a OpenLane configuration](config_tcl.png)

### 2. Reviewing the Sky130 Standard-Cell Configuration

**Explanation:** This file contains technology- and library-specific settings for the `sky130_fd_sc_hd` library. The displayed values include routing adjustment, synthesis fanout, clock period, core utilization, and target placement density. These values influence how much area is reserved for the core and how densely cells may be placed.

![Sky130 standard-cell library configuration](sky130A_sky130_fd_sc_hd_config_tcl.png)

### 3. Checking the Floorplanning Configuration Options

**Explanation:** This reference view lists the OpenLane floorplanning variables. Important controls include `FP_CORE_UTIL` for core utilization, `FP_ASPECT_RATIO` for the height-to-width relationship, `FP_SIZING` for relative or absolute sizing, the horizontal and vertical I/O metals, I/O placement mode, power-distribution settings, and the core margins. These options determine the die outline, core boundary, I/O layers, and power-grid arrangement.

![OpenLane floorplanning configuration options](floorplan_configuration.png)

### 4. Inspecting the Floorplan Tcl Configuration

**Explanation:** The Sky130 floorplan defaults are applied here. The configuration selects metal 3 for vertical I/O pins and metal 4 for horizontal I/O pins, uses relative sizing with 50% core utilization and an aspect ratio of 1, and sets power-distribution offsets and pitches. It also enables power rails and power-grid node checks, selects random equidistant I/O placement, sets I/O dimensions, and defines the core margins and halo values used during floorplanning.

![Sky130 floorplan Tcl settings](floorplan_tcl.png)

### 5. Generating and Inspecting the Floorplan DEF

**Explanation:** This DEF output is the physical description generated after the floorplan stage. It identifies the `picorv32a` design, its database units, die area, and standard-cell rows. The alternating row orientations (`FS` and `N`) provide legal placement orientations for standard cells. The repeated rows establish the locations in which cells can be placed inside the core.

![Floorplan DEF with die area and standard-cell rows](floorplan_def.png)

### 6. Checking the I/O Placer Log

**Explanation:** This log shows OpenROAD reading the technology LEF and the floorplan DEF before placing the design pins. It reports the created technology layers, vias, library cells, pins, components, nets, and connections. The final messages confirm that random pin placement was used in even-spacing mode, matching the floorplan configuration.

![OpenROAD I/O placer log](ioPlacer_log.png)

### 7. Viewing the Initial Floorplan Layout

**Explanation:** This Magic view shows the large-scale floorplan after the die and standard-cell rows have been created. The repeated row structure and boundary markers are visible across the core. At this stage the view primarily confirms the physical outline and row organization before the synthesized cells are densely placed.

![Initial floorplan layout in Magic](.%20layout1.png)

### 8. Inspecting the Floorplan I/O and Boundary Details

**Explanation:** This closer Magic view makes the floorplan boundary structures and I/O regions easier to inspect. It shows the technology layers and physical boundary cells around the core, along with named I/O nets such as `io[24]`, `pcpi_rs1[10]`, and `mem_la_data[24]`. These pins are positioned around the boundary before detailed cell placement and routing.

![Floorplan I/O pins and boundary details in Magic](.%20layout2.png)

### 9. Viewing the Initial Standard-Cell Placement

**Explanation:** This view shows the result after standard cells have been placed inside the previously generated rows. The core is now densely populated with logic cells, while the row and boundary structures remain visible around the design. This is the physical implementation of the synthesized netlist before detailed routing.

![Initial standard-cell placement](placement1.png)

### 10. Inspecting a Detailed Placement Region

**Explanation:** This zoomed Magic view shows individual placed Sky130 cells, including logic gates, multiplexers, flip-flop-related cells, tap or well-related cells, and their physical row alignment. It demonstrates that the standard cells have been assigned legal locations and orientations within the floorplan, completing the documented floorplanning and placement flow.

![Detailed standard-cell placement region](placement2.png)

## Flow Summary

The complete sequence is:

`config.tcl` -> Sky130 library configuration -> floorplan options -> floorplan Tcl settings -> floorplan DEF -> I/O placement log -> initial floorplan layout -> I/O and boundary view -> standard-cell placement -> detailed placement view

## Author

- **Name     :** Nukala Shiva Shankar
- **Roll No. :** 24EG104E28
- **College  :** Anurag University
