---
title: SMART Invited to Formal Methods in System Design
date: 2026-11-17
---

Our FMCAD 2025 paper, "Unlocking Hardware Verification with Oracle Guided Synthesis", was invited for a journal version in *Formal Methods in System Design* (FMSD).
The journal version is under revision now.
I am working on the journal version with my co-authors Yixuan Li, Guy Frankel, Jianyi Cheng and Elizabeth Polgreen, all at the University of Edinburgh.

Formal verification needs specifications, and writing them by hand is the expensive part of verifying hardware.
SMART is the tool from our FMCAD 2025 paper.
SMART mines SystemVerilog assertions from a Verilog design with no hand-written assertion templates, and every assertion it emits is proved against the design.

SMART runs a loop that combines simulation traces, syntax-guided synthesis and model checking.
It proposes candidate assertions from simulation traces by syntax-guided synthesis.
A model checker tests each candidate against the Verilog design and returns counterexamples for wrong candidates.
SMART uses those counterexamples and negative examples to refine the next candidates.

The journal version builds on the FMCAD 2025 paper in two ways.
Its main addition is support for bounded temporal properties.
It also explains the mining algorithm in more detail, setting out the three sources of diversity that make the mined assertions useful:

- Random variable subsets
- Random negative examples
- Counterexample refinement

In our evaluation, we run SMART on real-world Verilog benchmarks and test whether the mined assertions detect injected hardware mutations.
Across those benchmarks, the mined assertions detect a high proportion of the injected mutations.

SMART is open source at [github.com/lichye/smartVerilog](https://github.com/lichye/smartVerilog).
