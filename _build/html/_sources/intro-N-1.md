---
title: N-1 Analysis
nav_order: 8
---

# N-1 analysis

## The Problem: Single-Element Parallel Modeling
PowerFactory allows you to model parallel equipment (like a double-circuit line or two generators) using a single element and setting the **Number of Parallel Elements** parameter (e.g., to “2”). You can of course use more than 2 parallel elements.

### Why it Fails N-1
The contingency solver treats this as **one single component** in the database. When the solver tests a contingency, it trips that single component, resulting in **both parallel circuits being removed at once**. It is then a matter of definition: does N-1 refer to losing the whole power station or one of its generators? In your project you can do both, but mind that losing your whole power station in the N-1 analysis (or all parallel circuits of a line) makes your design more challenging.

## The Solution: Explicit Modeling
To test the loss of just **one circuit (N-1)** or **one generator**, you can use:

- **Parallel Lines (`ElmLne`)**: Draw two or more separate `ElmLne` elements between the buses.  
- **Parallel Generators (`ElmGen`)**: Draw two or more separate `ElmGen` elements on the busbar.

By explicitly drawing each physical unit, you create **distinct database objects**. This allows the contingency tool to correctly select and trip only **Line_A** or **Line_B** (if you only have two lines), providing the desired **N-1 behavior**.

## Alternative Option
If you actually want to define contingencies at the level of **“entire asset out”** (e.g., tripping the whole double-circuit line at once), then you can stick with the single-element parallel definition. That setup effectively gives you a **“truly N-1 system”** — just at the **asset level** rather than the **circuit level**.

> ⚠️ Note: This approach makes your system design more difficult, but it is a valid option.

## Key Takeaway
- For **true circuit-level N-1**, you must **explicitly model each unit separately**.  
- If you want to keep things simple and don’t need circuit-level precision, you can **use the parallel approach** and treat the whole element as the tripped unit. This will make creating an N-1 secure system more challenging.

This way, you can **choose the level of detail**: we show how to set up explicit modeling for correct N-1 circuit analysis, but you can always fall back on the simpler parallel definition if that better fits your study.