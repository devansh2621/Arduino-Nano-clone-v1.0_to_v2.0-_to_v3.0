# Arduino Nano Clone — Bare CH340G Design (v1.0 → v2.0 → v3.0)

A Nano-compatible board designed using ATmega328P-AU and a bare CH340G USB–UART IC, 
focused on power architecture clarity, USB-C correctness, and layout-driven learning.

## Design Intent

This project intentionally avoids pre-assembled USB–UART modules and instead uses a bare CH340G IC.
The goal was not feature expansion, but system-level understanding: power-path behavior, USB enumeration,
reset reliability, and layout-dependent failures.  
Each revision (v1.0 → v3.0) reflects a concrete architectural or layout lesson rather than cosmetic change.

## Key Characteristics

- ATmega328P-AU (Nano-compatible)
- Bare CH340G USB–UART (no module)
- USB Type-C (USB 2.0, 12-pin)
- Dual power support: USB 5V / external 5V
- Explicit power-path control (SS14 Schottky)
- Two-layer PCB with stitched ground planes

- ## Revision History

### v1.0 — Initial Implementation
- Split power domains (USB → CH340G, external 5V → MCU)
- Electrically functional but behavior depended on usage mode
- Increased complexity and non-reference behavior

### v2.0 — Power Architecture Correction
- Single shared 5V rail for entire board
- USB used for programming, external 5V prioritized in operation
- Eliminated back-feeding and ambiguous states

### v3.0 — Layout-Driven Redesign
- Component placement optimized before routing
- Ground poured early with fabrication-aware clearance
- Short return paths for decoupling, crystals, and USB signals
- DRC-clean, predictable routing and grounding

- ## Layout Learnings

### What Failed in v2.0
- Routing started without placement strategy
- Fabrication constraints considered too late
- Ground pour became non-viable due to clearance violations

### What Changed in v3.0
- Placement-first approach
- Early ground pour with known clearance
- Short, via-less critical paths
- Ground stitching to reduce return impedance

- ## Status

This project is complete at the schematic and layout level.
Future work will focus on higher-sensitivity and precision-oriented designs
where power integrity, grounding, and noise dominate behavior.
