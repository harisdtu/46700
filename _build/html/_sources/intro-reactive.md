---
title: Voltage Control Guidelines
nav_order: 5
---

# Voltage Control Guidelines

While designing your system it is very likely that you will encounter voltage problems: either very low values during high-load conditions, or very high values in low-loaded lines. You have three main ways to handle voltage:

- **Reactive power compensation**
- **Tap changers**
- **Voltage setpoint adjustment**

## Reactive power compensation

You can use shunt elements or synchronous condensers, but the most flexible solution is a Static VAR System. This grid element can produce or consume reactive power and therefore increase or decrease voltage depending on your needs.

You can add an SVS element and configure it as follows under Basic Data. Choose the max MVAr that can be consumed (TCR) or produced (TSC). 
![Voltage Control](./images/SVS1.png)

In the Load Flow view below, you can set the control mode. "Voltage Control" will try to maintain voltage to the "Voltage setpoint" of your choice (1 p.u. in the case shown below). The SVS will adjust its reactive power output to maintain voltage as close to the setpoint as possible, but it may not be able to achieve that. In that case it will set the output to the max allowed value.

Alternatively, if you select to use the manual control mode, you may also set the outcome of the SVS manually. For example to 10 MVAr or -20 MVAr. However, this requires more manual tuning in your system.
You may also manually set the outcome of the SVS to e.g., 10 MVAr or -20 MVAr, if you use the other control modes. However, this requires more manual tuning in your system.
![Voltage Control](./images/SVS2.png)

## Tap changers

Voltage can be regulated by taking advantage of the tap-changing capabilities of your transformers. This can be done manually (where you set the position of the tap changers) or automatically. When done automatically, you can adjust the voltage setpoint, i.e., the voltage that PF will try to achieve at one side of the transformer by adjusting the ratio.

There are a few different things to consider when doing so, and are covered in the following video.

[Tap changers in PF](https://panopto.dtu.dk/Panopto/Pages/Viewer.aspx?id=42b74e14-6ff4-4826-b02e-b31b00a6b5fe).