# Transformer Modelling Guidelines

To simplify the design of your system, allow you to focus on the main design choices, and better control the operation of the system, some simplifications are required when adding transformers. Also, the 50-node limit adds additional constraints. Very large transformers in the order of 1000 MVA are not very common. In practice, several smaller transformers will be connected in parallel. Below we provide some typical parameters for a 20/400 kV and a 132/400 kV transformer equipped with on-load tap changers. You need to define those elements in PowerFactory as they don't exist. You are free to modify the size of the transformer by reasonable amounts, e.g., 50 MVA more or less than 300 MVA. If you want to use very different component sizes then provide some reference for your choice of parameters.

The **vector group** describes the winding connections and phase displacement between the high voltage (HV) and low voltage (LV) sides of a transformer. For a 132/400 kV transformer, a common choice is **YNd1**:
- **Y** = star connection on the HV side, usually grounded (neutral available)
- **D** = delta connection on the LV side, no neutral
- **1** = 30° phase shift between HV and LV windings

### Positive Sequence Impedance (Z₁)

Positive sequence impedance represents the transformer’s impedance to **balanced, three-phase currents** (normal operation and symmetrical faults). It mainly consists of the winding resistance (R₁) and leakage reactance (X₁) due to magnetic flux leakage. Positive sequence impedance determines voltage drops under load and influences short-circuit current magnitude. It is typically expressed as a percentage of rated voltage (%Uk) or in per unit.

### Zero Sequence Impedance (Z₀)

Zero sequence impedance represents the transformer’s impedance to **zero-sequence currents**, which occur during **ground faults** or unbalanced conditions. It strongly depends on the transformer’s winding connections and grounding method. In a YNd transformer, zero-sequence currents can flow through the star (Y) side neutral but are blocked on the delta (D) side, resulting in zero-sequence impedance values different from positive sequence impedance. Zero sequence impedance is usually higher than positive sequence impedance and is critical for accurate earth fault and protection analysis.

### Transformer Parameters (300 MVA, 400/132 kV YNd1)

| Parameter                 | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 400/132 kV| HV/LV nominal voltage                      |
| Vector Group             | YNd1      | Star (HV) - Delta (LV) with 30° phase shift|
| Separate Neutral (N)     | Yes       | Neutral brought on HV side, solidly grounded|
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.03 pu   | Winding resistance                         |
| Zero seq reactance, X₀   | 0.30 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.07 pu   | Zero sequence copper losses                |

### Transformer Parameters (300 MVA, 20/400 kV YNd1)

| Parameter                 | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 20/400 kV | HV/LV nominal voltage                      |
| Vector Group             | YNd1      | Star (HV) - Delta (LV) with 30° phase shift|
| Separate Neutral (N)     | Yes       | Neutral brought on HV side, solidly grounded|
| Pos seq reactance, X₁    | 0.13 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.02 pu   | Winding resistance                         |
| Zero seq reactance, X₀   | 0.35 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.05 pu   | Zero sequence copper losses                |

### Transformer Parameters (300 MVA, 20/132 kV YNd1)

| Parameter                 | Value     | Notes                                      |
|--------------------------|-----------|--------------------------------------------|
| Rating                   | 300 MVA   | Rated apparent power                       |
| Voltage                  | 20/132 kV | HV/LV nominal voltage                      |
| Vector Group             | YNd1      | Star (HV) - Delta (LV) with 30° phase shift|
| Separate Neutral (N)     | Yes       | Neutral brought on HV side, solidly grounded|
| Pos seq reactance, X₁    | 0.12 pu   | Leakage reactance                          |
| Pos seq resistance, R₁   | 0.025 pu  | Winding resistance                         |
| Zero seq reactance, X₀   | 0.30 pu   | Includes grounding and delta path          |
| Zero seq resistance, R₀  | 0.06 pu   | Zero sequence copper losses                |