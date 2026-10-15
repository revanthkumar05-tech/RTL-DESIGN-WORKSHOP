# RTL Design Workshop

This repository documents my VLSI training work, covering Verilog RTL design, simulation, synthesis, CMOS inverter characterization, timing analysis, floorplanning, placement, and physical design.

## Repository Structure

```text
RTL-DESIGN-WORKSHOP/
├── Day_1/
├── Day_2/
├── Day_3/
├── Day_4/
├── Day_5/
├── module_1/
├── module_2/
├── module_3/
├── module_4/
├── module_5/
└── OpenROAD-physical-Design-flow/
```

## Day-wise RTL Design

### Day 1 – 2:1 Multiplexer
- Designed and studied a 2:1 multiplexer using Verilog.
- Simulated the design using Icarus Verilog.
- Viewed waveforms using GTKWave.
- Explored synthesis using Yosys and mapping to Sky130 cells.

### Day 2 – Sequential Logic
- Studied flip-flops and sequential circuits.
- Explored synchronous and asynchronous resets.
- Worked with multiple Verilog modules and submodules.
- Examined hierarchy and flattening in Yosys.

### Day 3 – RTL Optimization
- Studied counter design and sequential logic.
- Explored constant propagation.
- Examined the removal of unnecessary logic during synthesis.
- Investigated how RTL optimization affects the resulting hardware.

### Day 4 – RTL Coding Styles
- Compared different Verilog coding styles for multiplexers.
- Studied good and problematic MUX implementations.
- Explored the ternary operator.
- Examined how coding style influences synthesis results.

### Day 5 – Conditional Statements and Latch Inference
- Studied incomplete `if` and `case` statements.
- Explored complete and partial assignments.
- Worked with MUX, DEMUX, and ripple-carry adder examples.
- Investigated latch inference using simulation and synthesis.

## Module-wise VLSI Design

### Module 1 – Synthesis Using OpenLane
- Worked with the PicoRV32A design and Sky130 configuration.
- Explored OpenLane synthesis.
- Examined synthesis statistics and flip-flop ratio.
- Inspected the gate-level netlist.
- Studied static timing analysis using OpenSTA.

### Module 2 – Floorplanning and Placement
- Explored floorplanning using OpenLane and Sky130.
- Studied core and die dimensions.
- Examined I/O placement.
- Investigated standard-cell placement and DEF outputs.

### Module 3 – CMOS Inverter Characterization
- Simulated CMOS inverter behavior using ngspice.
- Studied DC voltage-transfer characteristics and transient response.
- Explored transistor sizing and its effect on circuit behavior.
- Used Magic for layout creation and inspection.
- Studied design-rule checking and extracted-netlist simulation.

### Module 4 – Timing Analysis and Optimization
- Studied critical paths and timing optimization.
- Explored custom inverter integration using LEF and Liberty files.
- Learned setup time, hold time, clock uncertainty, and clock skew.
- Examined synthesis optimization settings.
- Studied the trade-off between timing and area.

### Module 5 – Physical Design
- Explored power-distribution network (PDN) planning.
- Studied global routing and detailed routing.
- Examined TritonRoute and design-rule checking.
- Reviewed physical-design reports and outputs.

## OpenROAD Physical-Design Flow

### VSDBabySoC – Sky130HD

This section documents the physical-design flow for VSDBabySoC using OpenROAD and the Sky130HD platform.

The flow covers:

1. Floorplanning
2. Standard-cell placement
3. Clock-tree synthesis (CTS)
4. Routing
5. Physical-design output and report inspection

The folder references the following stage images:

- `floorplan.png`
- `place.png`
- `cts.png`
- `routing.png`

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Verilog | RTL design |
| Icarus Verilog | RTL simulation |
| GTKWave | Waveform visualization |
| Yosys | Logic synthesis and optimization |
| OpenLane | RTL-to-physical-design flow |
| OpenSTA | Static timing analysis |
| ngspice | Circuit simulation |
| Magic | IC layout design and inspection |
| OpenROAD | Physical-design implementation |
| TritonRoute | Detailed routing |
| Sky130 / Sky130HD | Standard-cell technology platforms |

## Overall Design Workflow

```text
RTL Design using Verilog
          ↓
Functional Simulation
          ↓
Waveform Analysis
          ↓
Logic Synthesis
          ↓
Floorplanning
          ↓
Standard-Cell Placement
          ↓
Timing Analysis and CTS
          ↓
Power Planning and Routing
          ↓
Design Checks and Reports
```

## Key Learning Outcomes

- Understanding combinational and sequential digital logic.
- Writing and simulating Verilog RTL designs.
- Understanding synthesis and RTL optimization.
- Exploring CMOS inverter behavior and layout.
- Learning static timing analysis and timing constraints.
- Understanding floorplanning, placement, clock-tree synthesis, and routing.
- Connecting RTL design concepts with the physical-design flow.

## Conclusion

This workshop brings together digital design and VLSI implementation concepts, from Verilog RTL coding and simulation to synthesis, circuit characterization, timing analysis, and physical design. The day-wise and module-wise structure organizes the exercises into a progression through the major stages of the VLSI design workflow.
