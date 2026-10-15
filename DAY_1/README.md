# RTL Design Workshop - Day 1

## Multiplexer RTL Design and Verification

---

## Index

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Design Description](#3-design-description)
4. [Verification](#4-verification)
5. [Results](#5-results)
6. [Conclusion](#6-conclusion)
7. [Files](#files)
8. [Tools Used](#tools-used)
9. [Key Learnings](#key-learnings)

## 1. Introduction

Day 1 introduces combinational RTL design using a multiplexer. A multiplexer selects one of multiple data inputs according to a control signal and forwards the selected value to the output.

## 2. Objective

- Understand the operation of a multiplexer.
- Describe combinational logic using RTL.
- Verify the output for different select and input combinations.
- Inspect simulation behavior using waveform results.

## 3. Design Description

The `good_mux` design represents a functionally correct multiplexer implementation. Its output should follow the selected input while the select signal changes. Because the circuit is combinational, the output responds to input changes without storing state.

## 4. Verification

The multiplexer behavior is checked using simulation waveforms. The GTKWave reference shows the relationship between the input signals, select signal, and output signal over time.

## 5. Results

- The multiplexer implementation produces the selected input at the output.
- The waveform provides a visual check of the expected truth-table behavior.
- The combined reference presents the implementation and its verification result together.

## 6. Conclusion

This exercise establishes the basic RTL workflow: describe a combinational circuit, simulate it, and inspect the resulting waveforms.

## Files

- [![Combined multiplexer implementation and verification reference](good_mux_both.png)](good_mux_both.png) - Combined multiplexer implementation and verification reference.
- [![GTKWave waveform for the multiplexer](good_mux_gtk.png)](good_mux_gtk.png) - GTKWave waveform for the multiplexer.

## Tools Used

- Verilog HDL / RTL
- RTL simulation
- GTKWave

## Key Learnings

- Multiplexer data selection
- Combinational RTL modeling
- Simulation-based functional verification
- Reading digital waveforms
