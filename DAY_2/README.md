# RTL Design Workshop - Day 2

## Flip-Flops, Reset Behavior, and Module Hierarchy

---

## Index

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Design Description](#3-design-description)
4. [Reset Behavior](#4-reset-behavior)
5. [Hierarchy and Synthesis](#5-hierarchy-and-synthesis)
6. [Results](#6-results)
7. [Conclusion](#7-conclusion)
8. [Files](#files)
9. [Tools Used](#tools-used)
10. [Key Learnings](#key-learnings)

## 1. Introduction

Day 2 focuses on sequential RTL using D flip-flops, reset behavior, and hierarchical module organization. The examples compare asynchronous and synchronous reset implementations and show how hierarchy appears in a synthesized netlist.

## 2. Objective

- Understand how a D flip-flop stores data on a clock edge.
- Compare asynchronous and synchronous reset behavior.
- Organize RTL using multiple modules and submodules.
- Observe hierarchy before and after synthesis.

## 3. Design Description

The D flip-flop examples model state elements controlled by a clock and reset. The multiple-module examples demonstrate how a larger design can be built from reusable submodules.

## 4. Reset Behavior

An asynchronous reset can change the state independently of the clock, while a synchronous reset is sampled on the active clock edge. The waveform and reference images provide a visual comparison of these timing behaviors.

## 5. Hierarchy and Synthesis

The design hierarchy is represented through a top-level module and submodules. Synthesis can preserve or flatten this hierarchy when producing the implementation netlist, which is illustrated by the module and flattened-netlist references.

## 6. Results

- Asynchronous and synchronous reset timing are compared.
- The D flip-flop examples demonstrate clocked state storage.
- The hierarchical design is represented through multiple modules and a synthesized netlist.

## 7. Conclusion

This exercise builds the foundation for sequential RTL design and shows why reset semantics and module hierarchy matter during simulation and synthesis.

## Files

- [![Asynchronous reset reference](asynchronous.png)](asynchronous.png) - Asynchronous reset reference.
- [![GTKWave view of an asynchronously reset D flip-flop](dff_asy_gtk.png)](dff_asy_gtk.png) - GTKWave view of an asynchronously reset D flip-flop.
- [![Synchronously reset D flip-flop reference](dff_syncres.png)](dff_syncres.png) - Synchronously reset D flip-flop reference.
- [![Flattened synthesized netlist](flatten_netlist.png)](flatten_netlist.png) - Flattened synthesized netlist.
- [![Multi-module design reference](multiple_modules.png)](multiple_modules.png) - Multi-module design reference.
- [![Submodule reference](sub_module1.png)](sub_module1.png) - Submodule reference.

## Tools Used

- Verilog HDL / RTL
- RTL simulation
- Synthesis and netlist inspection
- GTKWave

## Key Learnings

- D flip-flop behavior
- Asynchronous versus synchronous reset
- Hierarchical RTL design
- Flattened synthesized netlists
