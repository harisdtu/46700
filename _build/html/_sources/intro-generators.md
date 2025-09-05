---
title: Generators Guidelines
nav_order: 6
---

# Generators Guidelines

As a guideline for plant sizing, consult existing power plants to get an idea of typical lower and upper capacity limits.  
These limits can vary depending on the type and location of the plant.  
For example, a 100 MW nuclear plant would be highly unrealistic from an investment perspective.  
Ideally, your plant sizes should be consistent with existing or planned facilities in the chosen country or region.

Power plants should be connected to the appropriate voltage level depending on their size:  
larger plants to the 400 kV grid and smaller ones to the 132 kV level.  
When deciding on your generation portfolio, consider reasonable utilization factors.  
If, for example, you have an average load of 1000 MW, installing a total of 8000 MW would lead to a very uneconomical power system.

In addition, the capability to regulate active and reactive power varies between technologies.  
Conventional synchronous generators must operate with a power factor no lower than **cos φ = 0.9** (either lagging or leading).  
For modeling purposes in PowerFactory:
- Use the **Synchronous Generator** model for conventional units.
- Use the **Static Generator** model for solar and wind power.

All generators should include appropriate reactive power control (either static or constant voltage) and must respect operational limits, as covered in the tutorial:  
- Lower output limits are:
  - **50%** for nuclear  
  - **40%** for coal  
  - **20%** for gas and oil plants
  - **10\%^** for hydro  
  *(all expressed as percentages of their power rating).*

Synchronous machines operate at a voltage level of **20 kV**, so they must be connected to either the **132 kV** or **400 kV** grid via a transformer.  
For simplicity, you can assume the transformer's rated power is **125%** of the generator's apparent power rating.