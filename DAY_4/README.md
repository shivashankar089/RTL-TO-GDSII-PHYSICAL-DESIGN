# RTL Design Workshop - Day 4

## Mux Coding Styles and Blocking-Assignment Caveats

---

## Index

1. [Introduction](#1-introduction)
2. [Objective](#2-objective)
3. [Mux Coding Styles](#3-mux-coding-styles)
4. [Blocking Assignments](#4-blocking-assignments)
5. [RTL and Synthesis Views](#5-rtl-and-synthesis-views)
6. [Results](#6-results)
7. [Conclusion](#7-conclusion)
8. [Files](#files)
9. [Tools Used](#tools-used)
10. [Key Learnings](#key-learnings)

## 1. Introduction

Day 4 studies how coding style affects combinational mux logic and the way that logic is interpreted during simulation and synthesis.

## 2. Objective

- Compare correct and problematic mux descriptions.
- Understand the effect of blocking assignments in RTL.
- Review ternary-operator mux coding.
- Compare waveform results with synthesized RTL views.

## 3. Mux Coding Styles

The `bad_mux` references provide comparison examples for a mux implementation whose behavior or inferred structure may not match the intended design. The ternary-operator references show a compact way to express a two-way selection.

## 4. Blocking Assignments

Blocking assignments execute immediately within a procedural block. Their use can affect the observed ordering of statements and may create simulation behavior that differs from the designer's intended combinational model. The blocking-assignment references document this caveat.

## 5. RTL and Synthesis Views

GTKWave references show simulated behavior, while Yosys references show the RTL or synthesized interpretation. Comparing both views helps identify whether the selected coding style produces the expected hardware.

## 6. Results

- Mux behavior is examined through both simulation and synthesis references.
- A blocking-assignment caveat is demonstrated.
- Ternary-operator RTL is compared with its synthesized view.

## 7. Conclusion

This exercise shows that clear combinational coding style is important for predictable simulation and synthesis results.

## Files

- [![GTKWave result for the mux comparison example](bad_mux_gtk.png)](bad_mux_gtk.png) - GTKWave result for the mux comparison example.
- [![Yosys view of the mux comparison example](bad_mux_yosys.png)](bad_mux_yosys.png) - Yosys view of the mux comparison example.
- [![Blocking-assignment simulation example](blocking_caveat_gtk.png)](blocking_caveat_gtk.png) - Blocking-assignment simulation example.
- [![Yosys view of the blocking-assignment example](blocking_caveat_yosys.png)](blocking_caveat_yosys.png) - Yosys view of the blocking-assignment example.
- [![RTL view of a ternary-operator mux](ternary_operator_mux_rtl.png)](ternary_operator_mux_rtl.png) - RTL view of a ternary-operator mux.
- [![Yosys RTL view of the ternary-operator mux](ternary_operator_mux_yoys_rtl.png)](ternary_operator_mux_yoys_rtl.png) - Yosys RTL view of the ternary-operator mux.

## Tools Used

- Verilog HDL / RTL
- RTL simulation
- GTKWave
- Yosys

## Key Learnings

- Mux coding styles
- Blocking-assignment ordering
- Combinational RTL intent
- RTL and synthesized-view comparison
