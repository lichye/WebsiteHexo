---
title: Software
---

## Tools

- **SMART** mines SystemVerilog assertions from Verilog designs and emits only the assertions it proves. The parallel mode is the MAPminer algorithm. [Repo](https://github.com/lichye/smartVerilog) · FMCAD 2025, CAV 2026

- **UCLID5** is UC Berkeley's model checker. I wrote its floating-point support and its symbolic evaluator. [Repo](https://github.com/uclid-org/uclid)

## Bugs found by formal verification

- **AMD Vitis HLS 2025.1**: confirmed miscompilation. The generated RTL can report completion right after reset, before it has done any work. [Reproducer](https://github.com/lichye/vitis-hls-reset-repro)

- **HW-CBMC**: confirmed soundness bugs in the Verilog frontend. [Issue](https://github.com/diffblue/hw-cbmc/issues/880)
