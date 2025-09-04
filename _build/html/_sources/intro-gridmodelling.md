---
title: Grid modelling
nav_order: 2
---

# Grid modelling

You are free to choose a country or region anywhere in the world. To ensure projects remain comparable, the selected area should cover approximately 40,000–60,000 km². Please adhere to this size range: a larger area would require more and longer transmission lines, potentially creating complications in your grid, while a smaller area may not offer enough complexity to make the analysis meaningful.

Regardless of the region’s actual electricity demand, we standardize the total demand to lie between 2 GW and 6 GW, distributed across the area in proportion to population density and industrial activity (see Demand modelling for details). This scaling is chosen to strike a balance between analytical depth and practical feasibility.

This initial modelling phase (we call this the *baseline model*) is primarily about making *reasonable assumptions* regarding the location and sizing of both demand and generation. These assumptions will serve as the foundation for your later analysis. You should follow the constraints outlined below, and whenever you need to make choices—such as the capacity of a power plant—you must provide clear reasoning. Your rationale can be based on economic, geographical, technological, or political considerations, but it should be consistent throughout the system. The goal is not to create a perfect replica of a real-world grid, but rather a realistic, yet simplified and plausible, system that could exist.

## Network

The grid will have two voltage levels: 132 kV and 400 kV. Generally speaking, 400 kV is more costly. Hence, whenever a connection can be made on the 132 kV level, this is preferred. However, for transferring large power volumes over longer distances, 400 kV lines might be necessary. Your network should have at least 15 nodes, around 20–25 nodes would be ideal, and they must be separated by at least 15 km.

To avoid confusion: a node in the grid can have two voltage levels by having two buses which are connected through a transformer (but remember that the PowerFactory license supports up to 50 buses). Another restriction is that loads and generation units should not connect to the same node. The rationale behind this is that large generation units are usually not directly connected to the same bus as the loads. For example, nuclear plants are not placed in city centers.

The 132 kV lines should be in total at least 200 km long (multiple circuits count only once). Furthermore, 100 km should be implemented as cables (combined length on the two voltage levels). As a reminder: minimize the length of 400 kV lines, i.e., avoid too much zigzagging and rather use some additional 132 kV lines due to the cost argument. To model the power exchange with another region, the grid will have one interconnection that can import or export 800 MW and 200 MVAr.

You may use component data from the provided examples for your project. You are welcome to include additional components (include references in the report), and PowerFactory also has several components in its library—feel free to use these if necessary. Unless otherwise stated, the following operational constraints must always be respected: (i) Components (lines and transformers) should not be loaded more than 80%, and (ii) voltage should remain between 0.95 pu and 1.05 pu in the load flow analyses.

## Demand Modelling

Demand modelling should approximately reflect the spatial distribution of the loads. Model 70% of the total load for each scenario as residential, with a power factor of cos φ = 0.98 (lagging), and distribute it approximately according to population density (e.g., of cities or smaller regions) across at least eight locations. If you wish to split a very large city into two separate nodes, place the nodes at least 15 km apart.

The remaining 30% of the load should be modelled as industrial demand, with a power factor of cos φ = 0.9 (lagging). Distribute this industrial load across at least four nodes, either equally or according to a distribution of your choice.

All loads can be modelled as general load elements and be connected to either the 132 kV or 400 kV grid. However, 132 kV connections are preferred for cost reasons when only small loads are served.

## Generation Modelling

As a guideline for plant sizing, consult existing power plants to get an idea of typical lower and upper capacity limits. These limits can vary depending on the type and location of the plant. For example, a 100 MW nuclear plant would be highly unrealistic from an investment perspective. Ideally, your plant sizes should be consistent with existing or planned facilities in the chosen country or region.

Power plants should be connected to the appropriate voltage level depending on their size: larger plants to the 400 kV grid and smaller ones to the 132 kV level. When deciding on your generation portfolio, consider reasonable utilization factors. If, for example, you have an average load of 1000 MW, installing a total of 8000 MW would lead to a very uneconomical power system.

In addition, the capability to regulate active and reactive power varies between technologies. Conventional synchronous generators must operate with a power factor no lower than cos φ = 0.9 (either lagging or leading). For modelling purposes in PowerFactory, use the **Synchronous Generator** model for conventional units, and the **Static Generator** model for solar and wind power. All generators should include appropriate reactive power control (either static or constant voltage) and must respect operational limits: lower output limits are 50% for nuclear, 40% for coal, 20% for gas and oil plants, and 10% for hyrdro, all expressed as percentages of their power rating.

Synchronous machines operate at a voltage level of 20 kV, so they must be connected to either the 132 kV or 400 kV grid via a transformer. For simplicity, you can assume the transformer's rated power is around 125% of the generator's apparent power rating.

## Reactive Power Compensation

To maintain voltage stability and minimize transmission losses, your grid design may include reactive power compensation equipment. This can consist of shunt capacitors, shunt reactors, synchronous condensers, or Static Var Compensators (SVCs) - Static VAR Systems in PowerFactory. These devices can be placed at buses where voltage support is necessary.

However, due to cost and system complexity, the use of reactive compensation should be limited. You are allowed to install up to five reactive power compensation devices in total across the network, each of maximum 50 MVA capacity.


## Summary of Requirements

| **Category** | **Requirement** |
|--------------|-----------------|
| **Network** | |
| Voltage Levels | 132 kV (preferred), 400 kV (costly, minimize use) |
| Nodes | 15–25 nodes, min. 15 km apart |
| Buses | Max. 50; dual-voltage nodes via transformer allowed |
| Line Length | ≥200 km (132 kV), ≥100 km as cable (all levels) |
| Connection Rules | Loads and generators on separate nodes |
| Interconnection | One link: ±800 MW, ±200 MVAr |
| Reactive Compensation | Max. 5 devices |
| Load Limits | Max. 80% loading for lines/transformers |
| Voltage Range | 0.95–1.05 pu |
| **Demand** | |
| Split | 70% residential (PF = 0.98), 30% industrial (PF = 0.9) |
| Distribution | Residential: ≥8 nodes; Industrial: ≥4 nodes |
| Node Spacing | Split cities: min. 15 km apart |
| Voltage Level | Connect to 132 or 400 kV (prefer 132 kV for small loads) |
| **Generation** | |
| Sizing | Use realistic plant sizes; avoid oversizing |
| Connection | Large plants: 400 kV; Small: 132 kV |
| Utilization | Match load realistically; avoid huge overcapacity |
| Tech Constraints | PF ≥ 0.9 (lag/lead); reactive power control required |
| Min. Output | Nuclear: 50%; Coal: 40%; Gas/Oil: 20%; Hydro: 10% |
| Voltage | Sync gens: 20 kV, connect via transformer |
| Transformer Size | 125% of generator rating |
| Models | Use `Synchronous Generator` (conv.), `Static Generator` (solar/wind) |