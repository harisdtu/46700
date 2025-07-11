---
title: Transformer Modelling Guidelines
nav_order: 4
---

# Transformer Modelling Guidelines

To simplify your system design, help you focus on the key design decisions, and enable better operational control, certain simplifications are necessary when incorporating transformers. Additionally, the 50-node limit imposes further constraints. Very large transformers—around 1000 MVA—are uncommon in practice; instead, multiple smaller transformers are typically connected in parallel.

Below, we outline the main transformer parameters and explain their significance. You can define different transformers; if you do so, provide a relevant reference.

### Vector group

The **vector group** describes the winding connections and phase displacement between the high voltage (HV) and low voltage (LV) sides of a transformer. For a 400/132 kV transformer, a common choice is **DYn1**:
- **D** = delta connection on the HV side
- **Y** = star connection on the LV side
- **n** = neutral brought out on the star (LV) side
- **1** = 30° phase shift between HV and LV windings

### Positive Sequence Impedance (Z₁)

Positive sequence impedance represents the transformer’s impedance to **balanced, three-phase currents** (normal operation and symmetrical faults). It mainly consists of the winding resistance (R₁) and leakage reactance (X₁) due to magnetic flux leakage. Positive sequence impedance determines voltage drops under load and influences short-circuit current magnitude. It is typically expressed as a percentage of rated voltage (%Uk) or in per unit.

### Zero Sequence Impedance (Z₀)

Zero sequence impedance represents the transformer’s impedance to **zero-sequence currents**, which occur during **ground faults** or unbalanced conditions. It strongly depends on the transformer’s winding connections and grounding method. In a YNd transformer, zero-sequence currents can flow through the star (Y) side neutral but are blocked on the delta (D) side, resulting in zero-sequence impedance values different from positive sequence impedance. Zero sequence impedance is usually higher than positive sequence impedance and is critical for accurate earth fault and protection analysis.

### Tap changers
For all transformers below, you can select tap settings in 10 steps of ±1.25%, covering a range from -12.5% to +12.5%.

### Transformer Parameters (300 MVA, 400/132 kV DYn1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 400/132 kV| HV/LV nominal voltage                      |
| Vector Group             | DYn1      | Delta (HV) - Star (LV) with N, 30° shift   |
| Separate Neutral (N)     | Yes       | Neutral solidly grounded on LV side only   |
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.03 pu   | Winding resistance                         |
| Zero seq reactance, X₀   | 0.30 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.07 pu   | Zero sequence copper losses                |

### Transformer Parameters (300 MVA, 20/400 kV YNd1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 20/400 kV | LV/HV nominal voltage                      |
| Vector Group             | YNd1      | Star (HV) with N – Delta (LV), 30° shift   |
| Separate Neutral (N)     | Yes       | Neutral solidly grounded on HV side only   |
| Pos seq reactance, X₁    | 0.13 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.02 pu   | Winding resistance                         |
| Zero seq reactance, X₀   | 0.35 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.05 pu   | Zero sequence copper losses                |

### Transformer Parameters (300 MVA, 20/132 kV YNd1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 20/132 kV | LV/HV nominal voltage                      |
| Vector Group             | YNd1      | Star (HV) with N – Delta (LV), 30° shift   |
| Separate Neutral (N)     | Yes       | Neutral solidly grounded on HV side only   |
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.025 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.30 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.06 pu   | Zero sequence copper losses                |