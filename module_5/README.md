# Module 5: Final Physical Design Steps

## Overview

Module 5 focuses on the final stages of the Sky130 RTL-to-GDSII physical-design flow. It covers routing, design-rule checking (DRC), power-distribution network generation, global routing, detailed routing, and TritonRoute analysis.

These stages connect the placed standard cells and clock network, establish power and ground connectivity, and prepare the design for final physical verification.

## Objectives

- Understand maze routing and Lee's routing algorithm.
- Study routing constraints and design-rule checking.
- Understand the power-distribution network (PDN).
- Review global routing and detailed routing.
- Understand the role of TritonRoute in detailed routing.
- Analyze routing reports and physical-design results.
- Collect final implementation reports and verification evidence.

---

## 1. SKY130_D5_SK1: Routing and Design-Rule Checking

### Introduction

Routing is the physical-design stage in which electrical connections are created between standard cells, clock-network elements, power connections, and I/O pins.

The routing process must satisfy technology-specific constraints while connecting the required nets. Design-rule checking is used to identify physical violations in the routed layout.

### Maze Routing

Maze routing is a routing technique that searches for a valid path between two connection points through available routing resources.

The routing process considers obstacles, routing layers, and design-rule constraints when determining a path.

### Lee's Routing Algorithm

Lee's algorithm is a grid-based maze-routing algorithm used to find a path between a source and a destination.

The algorithm expands through neighboring grid locations until the destination is reached. Once a path is found, the route is traced back from the destination to the source.

The algorithm provides a systematic way to find a valid path, although the resulting route may not always be the most area-efficient solution.

### Design-Rule Checking

Design Rule Checking (DRC) verifies whether the routed layout satisfies the applicable technology rules.

The checks can identify issues related to spacing, width, connectivity, and other physical constraints.

### Workflow

1. Review the maze-routing concept.
2. Study the operation of Lee's routing algorithm.
3. Run the routing and verification steps required by the flow.
4. Examine the DRC report.
5. Identify and analyze any reported violations.

### Observations

- Routing connects the required electrical nets in the physical layout.
- Maze routing searches for feasible paths through available routing resources.
- Lee's algorithm systematically explores possible paths.
- DRC identifies layout violations that must be investigated and resolved.

---

## 2. SKY130_D5_SK2: Power Distribution Network

### Introduction

The Power Distribution Network (PDN) delivers supply voltage and ground connections to the standard cells and other required components of an integrated circuit.

A properly constructed power network helps provide reliable power distribution throughout the design.

### Components of the Power Network

The power-distribution network can include:

- Power and ground rails
- Power straps
- Power rings
- Connections to power pads or ports
- Connections to standard-cell power pins

The exact structure depends on the floorplan, technology rules, and configuration of the physical-design flow.

### PDN Generation

The power network is generated using the configured physical-design flow.

The resulting layout is inspected to understand how power and ground connections are distributed across the core.

The generated network is also checked for connectivity and compliance with the applicable physical constraints.

### Workflow

1. Review the power-grid configuration.
2. Generate the power-distribution network.
3. Inspect the power rails, straps, and other generated structures.
4. Check the connectivity of the power and ground network.
5. Review the generated files and verification results.

### Observations

- The PDN distributes power and ground throughout the design.
- Power rails and straps provide connections to the standard-cell rows.
- Power connectivity must be checked as part of physical verification.
- The generated power network must comply with the applicable technology rules.

---

## 3. SKY130_D5_SK3: TritonRoute Flow

### Introduction

TritonRoute is used for detailed routing in the OpenROAD physical-design flow.

Global routing determines approximate routing paths and assigns routing resources, while detailed routing creates the actual physical interconnections using the available routing layers and tracks.

Detailed routing must connect the required nets while satisfying technology-specific routing constraints.

### Global Routing

Global routing establishes approximate routes for the design's nets.

It helps determine the routing resources required and identifies potential congestion in different regions of the layout.

### Detailed Routing

Detailed routing converts the approximate routes into physical wires and vias.

The router considers the available routing tracks, obstacles, design rules, and connectivity requirements while constructing the final routes.

### TritonRoute Analysis

The TritonRoute stage is examined to understand its routing process and output reports.

The routing results are reviewed for connectivity, routing completion, wire and via information, and reported design-rule violations.

### Workflow

1. Review the global-routing results.
2. Examine the detailed-routing process.
3. Run the configured TritonRoute stage.
4. Inspect the routed layout and routing report.
5. Review the wire and via counts, if reported.
6. Analyze the DRC results and any remaining routing violations.

### Observations

- Global routing plans approximate routes and routing-resource usage.
- Detailed routing creates the physical connections between pins.
- TritonRoute performs detailed routing while considering technology rules.
- Routing reports help identify congestion, incomplete routes, and physical violations.
- The final routed layout must be checked before the design is considered complete.

---

## Final Physical-Design Workflow

The major stages covered in this module are:

1. Review routing concepts and design-rule constraints.
2. Generate and verify the power-distribution network.
3. Perform global routing.
4. Perform detailed routing using TritonRoute.
5. Inspect the final routing report.
6. Run design-rule checks and investigate violations.
7. Collect the final layout and implementation reports.

## Final Checklist

- [ ] Power-distribution network generated and checked.
- [ ] Global routing completed.
- [ ] Detailed routing completed.
- [ ] TritonRoute results reviewed.
- [ ] DRC report collected and analyzed.
- [ ] Routing report collected.
- [ ] Final layout inspected.
- [ ] Final timing and area results recorded.

## Conclusion

Module 5 covers the final physical-design stages required to transform a placed digital design into a routed implementation.

Routing establishes the electrical connections between cells, the power-distribution network provides supply and ground connectivity, and TritonRoute performs detailed routing while considering the technology constraints.

The final routing reports and DRC checks help evaluate the physical implementation and identify issues that require attention before final design delivery.

These activities provide practical understanding of routing, power distribution, and physical verification in a Sky130 RTL-to-GDSII flow.
