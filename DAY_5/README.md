# RTL Design Workshop - Day 5

## Conditional RTL, Generate Constructs, and Ripple-Carry Addition

---

## Index

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Case and If Statements](#3-case-and-if-statements)
4. [Generated Muxes and Demuxes](#4-generated-muxes-and-demuxes)
5. [Ripple-Carry Adder](#5-ripple-carry-adder)
6. [Results](#6-results)
7. [Conclusion](#7-conclusion)
8. [Files](#files)
9. [Tools Used](#tools-used)
10. [Key Learnings](#key-learnings)

## 1. Introduction

Day 5 focuses on conditional combinational RTL, generated structures, and a ripple-carry adder. The examples show how incomplete assignments can lead to unintended hardware and why all combinational outputs need a defined value for every relevant condition.

## 2. Objective

- Understand complete and incomplete `case` statements.
- Compare `if` examples with and without complete assignments.
- Build muxes and demuxes using `case` and generate constructs.
- Review gate-level simulation and synthesis results.
- Observe a ripple-carry adder waveform.

## 3. Case and If Statements

The `case` and `if` examples compare complete and incomplete combinational descriptions. The GTKWave, Yosys, and gate-level references help show the behavioral and structural consequences of missing assignments or branches.

## 4. Generated Muxes and Demuxes

The generated mux and demux examples demonstrate how repeated hardware can be described structurally. The simulation and synthesis references show the resulting selection and routing logic.

## 5. Ripple-Carry Adder

The RCA example represents addition through multiple carry-propagating stages. Its waveform provides a reference for checking multi-stage arithmetic behavior.

## 6. Results

- Complete and incomplete conditional assignments are compared.
- Mux and demux structures are represented using both procedural and generated RTL.
- Gate-level and RTL-oriented synthesis views are included.
- The ripple-carry adder waveform documents arithmetic behavior.

## 7. Conclusion

This exercise reinforces the importance of complete combinational assignments and introduces structural repetition and multi-stage arithmetic design.

## Files

- [![Gate-level simulation of the incomplete `case` example](bad_case_gls.png)](bad_case_gls.png) - Gate-level simulation of the incomplete `case` example.
- [![GTKWave result for the bad `case` example](bad_case_gtk.png)](bad_case_gtk.png) - GTKWave result for the bad `case` example.
- [![Yosys view for the bad `case` example](bad_case_yosys.png)](bad_case_yosys.png) - Yosys view for the bad `case` example.
- [![Yosys view of a complete `case` implementation](comp_case_yosys.png)](comp_case_yosys.png) - Yosys view of a complete `case` implementation.
- [![GTKWave view of a `case`-based demux](demux_case_gtk.png)](demux_case_gtk.png) - GTKWave view of a `case`-based demux.
- [![GTKWave view of a generated demux](demux_generate_gtk.png)](demux_generate_gtk.png) - GTKWave view of a generated demux.
- [![GTKWave result for an incomplete `case`](incomp_case_gtk.png)](incomp_case_gtk.png) - GTKWave result for an incomplete `case`.
- [![Yosys view for an incomplete `case`](incomp_case_yosys.png)](incomp_case_yosys.png) - Yosys view for an incomplete `case`.
- [![GTKWave result for an incomplete `if`](incomp_if.v_gtk.png)](incomp_if.v_gtk.png) - GTKWave result for an incomplete `if`.
- [![GTKWave result for a second incomplete `if` example](incomp_if2_gtk.png)](incomp_if2_gtk.png) - GTKWave result for a second incomplete `if` example.
- [![Yosys view for the second incomplete `if` example](incomp_if2_yosys.png)](incomp_if2_yosys.png) - Yosys view for the second incomplete `if` example.
- [![Yosys view for the incomplete `if` example](incomp_if_yosys.png)](incomp_if_yosys.png) - Yosys view for the incomplete `if` example.
- [![GTKWave view of a generated mux](mux_generate_gtk.png)](mux_generate_gtk.png) - GTKWave view of a generated mux.
- [![Yosys view of the generated mux](mux_generate_yosys.png)](mux_generate_yosys.png) - Yosys view of the generated mux.
- [![Yosys view of partial `case` assignments](partial_case_assign_yosys.png)](partial_case_assign_yosys.png) - Yosys view of partial `case` assignments.
- [![GTKWave view of the ripple-carry adder](rca.v_gtk.png)](rca.v_gtk.png) - GTKWave view of the ripple-carry adder.

## Tools Used

- Verilog HDL / RTL
- RTL and gate-level simulation
- GTKWave
- Yosys

## Key Learnings

- Complete combinational assignments
- `case` and `if` coding
- Generate constructs
- Mux and demux structures
- Ripple-carry addition
