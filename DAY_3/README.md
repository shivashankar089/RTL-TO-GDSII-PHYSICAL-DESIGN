# RTL Design Workshop - Day 3

## Constants, Counters, and Synthesis Optimization

---

## Index

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Constant-Driven Designs](#3-constant-driven-designs)
4. [Counter Design](#4-counter-design)
5. [Synthesis Optimization](#5-synthesis-optimization)
6. [Results](#6-results)
7. [Conclusion](#7-conclusion)
8. [Files](#files)
9. [Tools Used](#tools-used)
10. [Key Learnings](#key-learnings)

## 1. Introduction

Day 3 examines how constants and sequential logic are represented during simulation and synthesis. It also introduces a counter and uses optimization checks to compare RTL intent with the synthesized implementation.

## 2. Objective

- Understand constant-driven RTL behavior.
- Compare simulated waveforms with synthesized views.
- Study a counter implementation.
- Observe how synthesis removes or simplifies redundant logic.

## 3. Constant-Driven Designs

The constant-driven D flip-flop examples demonstrate how fixed values affect simulation and the resulting synthesized structure. The GTKWave images show behavior over time, while the Yosys images show the corresponding implementation view.

## 4. Counter Design

The counter example represents sequential state that changes with clock events. Its output can be used to verify that the expected counting behavior is preserved by the RTL implementation.

## 5. Synthesis Optimization

The optimization references illustrate successive checks of the synthesized design. Synthesis tools analyze constant propagation, redundant logic, and sequential behavior to produce a simpler implementation when possible.

## 6. Results

- Constant-driven D flip-flop examples are shown in simulation and synthesis views.
- The counter provides a sequential-logic reference.
- Multiple optimization checks document the effect of synthesis transformations.

## 7. Conclusion

This exercise demonstrates that synthesis is both a translation and an optimization process. Comparing GTKWave and Yosys views helps connect RTL behavior with implementation structure.

## Files

- [![Simulation of the second constant-driven example](deff_const2_gtk.png)](deff_const2_gtk.png) - Simulation of the second constant-driven example.
- [![Yosys view of the second constant-driven example](deff_const2_yosys.png)](deff_const2_yosys.png) - Yosys view of the second constant-driven example.
- [![Simulation of the third constant-driven example](deff_const3_gtk.png)](deff_const3_gtk.png) - Simulation of the third constant-driven example.
- [![Yosys view of the third constant-driven example](dff_const3_yosys.png)](dff_const3_yosys.png) - Yosys view of the third constant-driven example.
- [![Simulation of a constant-driven D flip-flop](dff_const_gtk.png)](dff_const_gtk.png) - Simulation of a constant-driven D flip-flop.
- [![Yosys view of the constant-driven D flip-flop](dff_const_yosys.png)](dff_const_yosys.png) - Yosys view of the constant-driven D flip-flop.
- [![Counter design reference](good_counter.png)](good_counter.png) - Counter design reference.
- [![First synthesis optimization check](opt_check.png)](opt_check.png) - First synthesis optimization check.
- [![Second synthesis optimization check](opt_check2.png)](opt_check2.png) - Second synthesis optimization check.
- [![Third synthesis optimization check](opt_check3.png)](opt_check3.png) - Third synthesis optimization check.

## Tools Used

- Verilog HDL / RTL
- RTL simulation
- GTKWave
- Yosys

## Key Learnings

- Constant propagation
- Counter design
- RTL-versus-netlist comparison
- Synthesis optimization
