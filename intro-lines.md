---
title: Line Modelling Guidelines
nav_order: 5
---

# Line Modelling Guidelines

As with the case of transformers, you will need to introduce/define line elements yourselves. Again, you may need to consider multiple parallel lines, as typical lines may not have the capability of transferring the amount of power you want. 

Below, we outline the main line parameters and explain their significance. You can define different lines; if you do so, provide a relevant reference.

> **Note:** **Neutral conductors are not required**, and **zero-sequence impedance or admittance values can be omitted**. This is because the study assumes **balanced, steady-state conditions** with no ground faults or asymmetrical operating scenarios. Under such conditions, only the **positive-sequence network** is used for power flow and voltage calculations, making zero-sequence parameters irrelevant.

## Main Line Parameters

- **Voltage level**: Nominal line-to-line voltage. Defines insulation level and equipment compatibility.

- **Type**: Overhead line (OHL), land cable, or sea cable. Each type has different thermal and electrical characteristics.

- **Ampacity \([A]\)**: Maximum continuous current the line can carry without exceeding its thermal limits. Determined by conductor type, bundling, and cooling conditions.

- **Resistance \([Ω/km]\)**: Series resistance per unit length. Affects I²R losses and voltage drop.

- **Reactance \([Ω/km]\)**: Series inductive reactance per unit length. Influences reactive power flow and voltage stability.

- **Admittance \([μS/km]\)**: Shunt admittance per unit length. Reflects capacitive charging due to line-to-ground insulation, especially significant for cables.

## Line Parameters

The following table summarizes typical overhead line and cable parameters for 400 kV and 132 kV systems. These values are per kilometer and represent positive-sequence parameters, suitable for balanced load flow studies.

> **Note:** Neutral conductors are not required, and zero-sequence values can be ignored. This is because we assume **balanced, steady-state conditions**, where only the **positive-sequence network** is used for power flow and voltage calculations.

| Voltage (kV) | Type              | Ampacity (A) | Resistance (Ω/km) | Reactance (Ω/km) | Susceptance (μS/km) |
|--------------|-------------------|---------------|--------------------|-------------------|----------------------|
| 400          | OHL               | 3400          | 0.023              | 0.311             | 3.68                 |
| 400          | Land cable        | 880           | 0.020              | 0.268             | 81.6                 |
| 400          | Sea cable         | 1240          | 0.042              | 0.076             | 72.3                 |
| 132          | OHL, Bluebird     | 2050          | 0.031              | 0.367             | 3.16                 |
| 132          | OHL, Curlew       | 1150          | 0.061              | 0.389             | 2.98                 |
| 132          | Land cable, Cu    | 1465          | 0.011              | 0.148             | 118.8                |
| 132          | Land cable, Al    | 765           | 0.026              | 0.177             | 78.5                 |
| 132          | Sea cable         | 835           | 0.104              | 0.129             | 66.0                 |