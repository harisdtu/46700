---
title: Transformer Modelling Guidelines
nav_order: 3
---

# Transformer Modelling Guidelines

To simplify your system design, help you focus on the key design decisions, and enable better operational control, certain simplifications are necessary when incorporating transformers. Additionally, the 50-node limit imposes further constraints. Very large transformers—around 1000 MVA—are uncommon in practice; instead, multiple smaller transformers are typically connected in parallel.

Below, we outline the main transformer parameters and explain their significance. You can define different transformers; if you do so, provide a relevant reference.

### Vector Group

The **vector group** describes the winding connections and phase displacement between the high-voltage (HV) and low-voltage (LV) sides of a transformer. One commonly used vector group is **YNd1**:
- **Y** = star-connected HV winding
- **N** = neutral point of the HV winding is brought out
- **d** = delta-connected LV winding
- **1** = LV voltage phasor is at the **1 o'clock position** relative to the HV phasor (30° phase displacement)

**Transformer vector-group notation:** In transformer vector-group notation, the first letter refers to the HV winding and the second letter to the LV winding. Uppercase letters are used for the HV side and lowercase letters for the LV side. The symbols N and n indicate that the neutral point is accessible on the HV and LV side, respectively.

**Note:** The first letter always refers to the HV winding and the second letter to the LV winding, regardless of how the transformer voltages are written. For example, in YNd1, the HV winding is star-connected with a neutral brought out (YN) and the LV winding is delta-connected (d), whether the transformer is labelled/referred to as 400/20 kV or 20/400 kV.

### Zero Sequence and Use of Neutrals

In balanced three-phase operation, zero-sequence currents are absent because the sum of the phase currents is zero and there is no return path for zero-sequence components. Consequently, the transformer's and line's zero-sequence impedance parameters (X₀, R₀) do not influence steady-state voltages or currents under balanced conditions.

This means that when performing balanced load flow or steady-state analysis, you can often ignore zero-sequence parameters and neutral connections without impacting the results. However, these parameters are crucial for modelling unbalanced faults, earth faults, and protection studies where zero-sequence currents flow.

### Positive Sequence Impedance (Z₁)

Positive sequence impedance represents the transformer’s impedance to **balanced, three-phase currents** (normal operation and symmetrical faults). It mainly consists of the winding resistance (R₁) and leakage reactance (X₁) due to magnetic flux leakage. Positive sequence impedance determines voltage drops under load and influences short-circuit current magnitude. It is typically expressed as a percentage of rated voltage (%Uk) or in per unit.

### Zero Sequence Impedance (Z₀)

Zero sequence impedance represents the transformer’s impedance to **zero-sequence currents**, which occur during **ground faults** or unbalanced conditions. It strongly depends on the transformer’s winding connections and grounding method. In a YNd transformer, zero-sequence currents can flow through the star (Y) side neutral but are blocked on the delta (D) side, resulting in zero-sequence impedance values different from positive sequence impedance. Zero sequence impedance is usually higher than positive sequence impedance and is critical for accurate earth fault and protection analysis.

### Tap Changers
For all transformers below, you can select tap settings in 10 steps of ±1.25%, covering a range from -12.5% to +12.5%.

### Transformer Parameters incl. Neutrals and Zero Sequence

#### Transformer Parameters (300 MVA, 400/132 kV YNd1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 400/132 kV| HV/LV nominal voltage                      |
| Vector Group             | YNd1      | YN (400 kV) – d (132 kV), 30° phase shift  |
| Neutral (N)              | Yes       | 400 kV side grounded                       |
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.003 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.12 pu   | Reactance seen by zero-sequence currents   |
| Zero seq resistance, R₀  | 0.003 pu  | Resistance seen by zero-sequence currents  |

#### Transformer Parameters (300 MVA, 400/132 kV YNyn0)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 400/132 kV| HV/LV nominal voltage                      |
| Vector Group             | YNyn0     | YN (400 kV) – yn (132 kV), 0° phase shift  |
| Neutral (N)              | Yes       | Both sides grounded                        |
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.003 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.12 pu   | Reactance seen by zero-sequence currents   |
| Zero seq resistance, R₀  | 0.003 pu  | Resistance seen by zero-sequence currents  |

#### Transformer Parameters (300 MVA, 400/20 kV YNd1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 400/20 kV | HV/LV nominal voltage                      |
| Vector Group             | YNd1      | YN (400 kV) – d (20 kV), 30° phase shift   |
| Neutral (N)              | Yes       | 400 kV side grounded                       |
| Pos seq reactance, X₁    | 0.15 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.003 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.15 pu   | Reactance seen by zero-sequence currents   |
| Zero seq resistance, R₀  | 0.003 pu  | Resistance seen by zero-sequence currents  |

#### Transformer Parameters (150 MVA, 132/20 kV YNd1)

| Parameter                | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 150 MVA   | Rated apparent power                       |
| Voltage                  | 132/20 kV | HV/LV nominal voltage                      |
| Vector Group             | YNd1      | YN (132 kV) – d (20 kV), 30° phase shift   |
| Neutral (N)              | Yes       | 132 kV side grounded                       |
| Pos seq reactance, X₁    | 0.11 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.002 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.11 pu   | Reactance seen by zero-sequence currents   |
| Zero seq resistance, R₀  | 0.002 pu  | Resistance seen by zero-sequence currents  |