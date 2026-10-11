# Module 4: Pre-Layout Timing Analysis and Clock Design

## Overview

Module 4 focuses on custom standard-cell integration, synthesis timing optimization, floorplanning, and placement using the Sky130 technology and OpenLane flow.

The experiments demonstrate how a custom inverter layout can be integrated into a digital design flow using LEF and Liberty files. They also explore timing reports, critical-path analysis, and the trade-off between timing performance and chip area.

## Objectives

- Understand standard-cell timing models and Liberty files.
- Study layout grids and routing-track dimensions.
- Create a custom inverter layout using Magic.
- Generate a LEF abstract for the custom inverter.
- Integrate custom LEF and Liberty files into the OpenLane flow.
- Analyze synthesis timing reports and critical paths.
- Apply timing-oriented synthesis settings.
- Understand floorplanning, placement, and design utilization.
- Study setup time, hold time, clock uncertainty, clock skew, and clock-tree synthesis concepts.

---

## 1. SKY130_D4_SK1: Timing Model and Custom Cell Integration

### Introduction

Standard-cell libraries provide the logical, physical, and timing information required to implement digital circuits.

The Liberty file describes the electrical and timing characteristics of a cell, while the LEF file describes its physical dimensions, pins, and routing information.

In this experiment, a custom CMOS inverter is created and integrated into the Sky130-based OpenLane design flow.

### Custom Inverter Layout

The inverter layout is opened in Magic using the Sky130 technology setup.

The layout is examined to identify the transistor layers, interconnections, and cell terminals. The grid dimensions are also considered to understand how the layout geometry relates to the intended routing grid.

The inverter contains the following terminals:

- `VPWR`: Power supply
- `VGND`: Ground
- `A`: Input signal
- `Y`: Output signal

### LEF Generation

A LEF abstract is generated from the custom inverter layout using Magic.

The LEF file contains the physical information needed by the place-and-route flow, including macro dimensions and pin geometry.

The generated LEF and the corresponding Liberty files are placed in the design's source directory.

### OpenLane Configuration

The OpenLane configuration is updated to include the custom inverter's physical and timing information.

The relevant configuration variables include:

- `EXTRA_LEFS`
- `LIB_SYNTH`
- `LIB_FASTEST`
- `LIB_SLOWEST`
- `LIB_TYPICAL`

The design is prepared using the updated configuration, and the merged LEF is checked to verify that the custom cell's physical abstract is included.

### Observations

- Magic is used to create and inspect the custom inverter layout.
- LEF provides the physical abstract of the standard cell.
- Liberty provides timing and electrical characteristics.
- Both physical and timing information must be configured correctly for integration into the design flow.

---

## 2. Synthesis and Timing Analysis

### Introduction

Logic synthesis converts RTL descriptions into a network of standard cells. Timing analysis evaluates whether the mapped circuit can operate within the specified timing constraints.

In this experiment, synthesis reports are examined before and after applying timing-oriented synthesis settings.

### Default Synthesis

The design is synthesized using the default configuration.

The synthesis statistics and timing reports are inspected to identify timing violations and critical paths.

The default run exhibits negative timing slack, indicating that the design does not satisfy the target timing constraint.

### Critical-Path Analysis

The critical timing path is examined using OpenSTA.

The report identifies the startpoint, endpoint, path group, and delays of the cells along the path.

The recorded analysis identifies a long OR-reduction logic chain as a major contributor to the critical-path delay.

This demonstrates how the structure and depth of combinational logic influence overall timing performance.

### Timing-Oriented Synthesis

Timing-oriented synthesis settings are applied to improve the implementation.

The recorded configuration uses the following settings:

```text
SYNTH_STRATEGY "DELAY 0"
SYNTH_BUFFERING 1
SYNTH_SIZING 1
```

The design is synthesized again, and the resulting timing and area statistics are compared with the default implementation.

The recorded results show improved timing, with WNS and TNS reported as zero after the optimization. However, the synthesis-reported chip area increases.

### Observations

- The default synthesis run exhibits negative timing slack.
- Critical-path analysis helps identify logic responsible for excessive delay.
- Timing-oriented synthesis can improve timing performance.
- Buffering and cell sizing can increase area while improving timing.
- Synthesis optimization involves a trade-off between area and timing.

---

## 3. Floorplanning and Placement

### Introduction

Floorplanning and placement are important stages in physical design.

Floorplanning defines the die and core regions, while placement determines the locations of standard cells within the available core area.

The timing-optimized design is carried forward into the floorplanning and placement stages.

### Floorplanning

The floorplan is generated using the OpenLane flow.

The die boundary and core boundary are examined to understand the available physical area.

The recorded floorplan reports the following dimensions:

- Die boundary: `(0.0, 0.0)` to `(746.915, 757.635)` µm
- Core boundary: `(5.52, 10.88)` to `(741.06, 745.28)` µm

These dimensions describe the generated floorplan before placement.

### Placement

The standard cells are placed within the core region while satisfying placement constraints.

The placement report is examined for the number of instances, nets, utilization, and placement rows.

The recorded placement statistics are:

- Instances: 18,673
- Nets: 20,721
- Utilization: 41%
- Padded utilization: 58%
- Placement rows: 270

The recorded WNS and TNS remain zero after placement.

The placement output also provides a visual representation of the standard-cell arrangement across the design.

### Observations

- Floorplanning defines the physical boundaries of the design.
- Placement assigns physical locations to standard cells.
- Utilization indicates how much of the available core area is occupied.
- Timing and area statistics help evaluate the quality of the implementation.
- The placement stage builds upon the timing-optimized synthesis result.

---

## 4. Timing and Clock Design Concepts

### Setup Time

Setup time is the minimum period for which data must remain stable before the active clock edge at a sequential element.

A setup violation occurs when data arrives too late to be captured reliably.

### Hold Time

Hold time is the minimum period for which data must remain stable after the active clock edge.

A hold violation occurs when data changes too soon after the clock edge.

### Clock Uncertainty

Clock uncertainty represents timing margins associated with variations and inaccuracies in clock arrival times and other clock-related effects.

It is included in timing constraints to ensure reliable operation under the specified conditions.

### Clock Skew

Clock skew is the difference in clock arrival times between sequential elements.

Depending on its direction and magnitude, skew can affect both setup and hold timing.

### Clock-Tree Synthesis

Clock-tree synthesis (CTS) builds a clock distribution network to deliver the clock to sequential elements while managing clock latency and skew.

Post-CTS timing analysis evaluates the design using the implemented clock network.

These concepts provide the foundation for the clock-design and timing-verification stages that follow placement.

---

## Overall Workflow

1. Create and inspect the custom inverter layout in Magic.
2. Generate the inverter's LEF abstract.
3. Integrate the LEF and Liberty files into OpenLane.
4. Run synthesis and inspect timing reports.
5. Analyze the critical timing path.
6. Apply timing-oriented synthesis settings.
7. Compare timing and area statistics.
8. Perform floorplanning and placement.
9. Review the setup, hold, and clock-design concepts relevant to subsequent stages.

## Conclusion

Module 4 demonstrates how custom-cell integration, timing optimization, floorplanning, and placement contribute to the physical implementation of a digital design.

The custom inverter experiment connects layout design with LEF and Liberty integration. The synthesis experiments demonstrate the importance of critical-path analysis and the trade-off between timing and area. Finally, floorplanning and placement establish the physical organization of the design.

Together, these experiments provide practical insight into pre-layout timing analysis and the early stages of an RTL-to-physical-design flow using Sky130 and OpenLane.
