# CMOS PUF Hardware Security

A Digital Integrated Circuits project focused on the design and evaluation of a reliable CMOS SRAM-based Physically Unclonable Function (PUF) for IoT hardware security.

The project studies whether a compact SRAM PUF can improve reliability without heavy error-correction hardware by combining a Schmitt-trigger-assisted readout with a lightweight unstable-bit detector.

## Project Overview

The proposed design is based on a conventional 6T SRAM PUF cell and adds:

- A Schmitt-trigger-assisted readout stage
- An output latch
- A dual-latch + XOR unstable-bit detector
- A 4×4 SRAM PUF array implementation

The unstable-bit detector identifies unreliable bits by comparing repeated samples and masking cells that are unstable.

## Key Results

Measured and simulated results include:

- Uniqueness: **49.8%**
- Uniformity: **45.9%**
- Baseline bit-error rate: **15.0%**
- Proposed bit-error rate after masking: **1.5%**
- Baseline reliability: **85.0%**
- Proposed reliability: **98.5%**
- Approximately **10× lower bit-error rate**
- 1-bit cell area overhead: **+31%**
- 4×4 array area overhead: **+52%**

The results show that the major reliability improvement comes from unstable-bit detection and masking, while the Schmitt trigger mainly improves read-noise immunity.

## Design Flow

The project includes:

- CMOS inverter
- 6T SRAM cell
- Schmitt trigger
- Precharge circuit
- Output latch
- XOR-based unstable-bit detector
- Baseline 1-bit PUF
- Proposed 1-bit PUF
- Baseline 4×4 PUF array
- Proposed 4×4 PUF array

## Tools and Technology

- Electric VLSI
- LTspice XVII
- AMIS C5 0.5 µm CMOS process
- BSIM3 device models
- Python for metrics analysis
- Monte-Carlo simulation
- CMOS layout and schematic verification

The design was evaluated at **VDD = 5 V**.

## Methodology

The main evaluation flow includes:

1. Capturing schematics and layouts in Electric VLSI
2. Simulating the circuits in LTspice
3. Generating SRAM fingerprints from power-up mismatch
4. Injecting threshold-voltage mismatch using Gaussian gate-offset sources
5. Running Monte-Carlo simulations across multiple virtual chips
6. Performing repeated noisy reads for reliability analysis
7. Comparing baseline and proposed architectures using PUF quality and hardware-cost metrics

## Repository Structure

```text
codes/
pictures/
CMOS_PUF_Presentation.pptx
IC_Project.jelib
Reliable_CMOS_PUF_Paper.pdf
README.md
```

### `codes/`

Contains simulation, analysis, and evaluation files used throughout the project, including:

- Baseline and proposed 1-bit PUF simulations
- Baseline and proposed 4×4 array simulations
- Monte-Carlo simulations
- Power and energy analysis
- Reliability / BER analysis
- Delay analysis
- Schmitt-trigger hysteresis analysis
- Metrics analysis scripts

### `pictures/`

Contains project figures and visual results grouped into:

```text
layout/
layout_simulation/
results/
schematic/
schematic_simulation/
```

### `IC_Project.jelib`

Electric VLSI library containing the implemented project cells and layouts.

### `Reliable_CMOS_PUF_Paper.pdf`

Project report describing the architecture, methodology, simulation setup, measurements, results, and limitations.

### `CMOS_PUF_Presentation.pptx`

Presentation summarizing the design, implementation, evaluation methodology, and measured results.

## Reliability Analysis

Reliability was evaluated using repeated noisy reads.

The baseline design achieved a bit-error rate of **15.0%**, corresponding to **85.0% reliability**.

After unstable cells were identified during enrollment and masked, the retained key achieved a bit-error rate of **1.5%**, corresponding to **98.5% reliability**.

This demonstrates the reliability-for-key-length trade-off introduced by unstable-bit masking.

## PUF Quality Metrics

The 4×4 PUF array was evaluated using standard PUF metrics:

- **Uniqueness** — measures the inter-chip Hamming distance
- **Uniformity** — measures the fraction of ones in the response
- **Bit-aliasing** — measures per-position bias
- **Bit-error rate (BER)** — measures response instability
- **Reliability** — calculated from BER

The measured uniqueness and uniformity were close to the ideal 50% target.

## Physical Design

Both baseline and proposed designs were implemented at the schematic and layout levels.

The project includes layouts for the main building blocks, 1-bit PUF cells, and 4×4 arrays.

All implemented cells and arrays were reported as DRC-clean and NCC-matched to their schematics.

## Scope and Limitations

The reported electrical results are based on schematic-level SPICE simulations.

The project does not include parasitic extraction, fabricated-silicon measurements, or a full digital decoder / selection network for the array.

The 4×4 array is driven directly through simulation stimulus signals.

## Authors

- Doaa Odeh
- Aseel Hamed
- Ahmad Salameh
- Anis DarHammouda

Department of Electrical and Computer Engineering  
Birzeit University

## Usage Notice

Copyright © 2026 Aseel Hamed and Project Team. All Rights Reserved.

This project is publicly available for viewing and portfolio purposes only.

Copying, reproducing, redistributing, modifying, or using any part of this project in another academic, personal, or commercial project without explicit permission from the authors is prohibited.

This repository is not open source and no license is granted for reuse of the source code.
