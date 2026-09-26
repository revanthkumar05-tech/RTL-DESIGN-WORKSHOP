
# MODULE 1 – Synthesis using OpenLane

## Introduction

This module focuses on understanding the RTL-to-gate-level synthesis flow using **OpenLane**, **Yosys**, **OpenSTA**, and the **Sky130 PDK**.

The **PicoRV32A** design is used to understand the different stages involved in synthesis and timing analysis.

---

## 1. OpenLane Directory Structure

The OpenLane directory contains the scripts, configuration files, design files, and supporting files required to run the RTL-to-GDSII flow.

The PicoRV32A design directory contains the required RTL source files, configuration files, and run directories.

---

## 2. PicoRV32A Design

PicoRV32A is a RISC-V based processor design used for this synthesis exercise.

The design contains the RTL source and configuration required to run the synthesis flow using OpenLane.

---

## 3. Design Configuration

The `config.tcl` file contains the main configuration parameters required by OpenLane.

Important parameters include:

- Design name
- RTL source files
- Clock port
- Clock period
- Clock net
- SDC file
- Synthesis parameters
- Floorplanning parameters

The configuration determines how the PicoRV32A design is processed through the OpenLane flow.

---

## 4. Sky130 Configuration

The Sky130 configuration files contain technology-specific settings used by OpenLane.

Some important parameters include:

- `GLB_RT_ADJUSTMENT`
- `SYNTH_MAX_FANOUT`
- `CLOCK_PERIOD`
- `FP_CORE_UTIL`
- `PL_TARGET_DENSITY`

These parameters influence synthesis, placement, routing, and timing.

---

## 5. OpenLane Interactive Mode

OpenLane can be started in interactive mode using:

bash
./flow.tcl -interactive

Interactive mode allows individual flow stages and commands to be executed and inspected.


---

## 6. Yosys Synthesis

Yosys is used during the synthesis stage to convert the RTL design into a gate-level representation.

The synthesis process includes:

RTL parsing

Logic optimization

Process conversion

Technology mapping

Flip-flop mapping

Standard-cell mapping


The output is a synthesized gate-level netlist.


---

## 7. Synthesis Statistics

Yosys provides synthesis statistics after processing the design.

The statistics include:

Number of wires

Number of wire bits

Number of cells

Number of memories

Number of processes

Flip-flop count

Logic-cell distribution


These statistics help in understanding the size and structure of the synthesized design.


---

## 8. Flop Ratio

The flop ratio can be calculated using the number of flip-flops and total number of cells.

Flop Ratio = Number of Flip-Flops / Total Number of Cells

The required values are obtained from the Yosys synthesis statistics.


---

## 9. Synthesized Netlist

After synthesis, the RTL is converted into a gate-level Verilog netlist.

The synthesized netlist contains:

Standard-cell instances

Wires

Ports

Gate-level connections


This netlist represents the synthesized implementation of the PicoRV32A design.


---

## 10. Synthesis Reports

OpenLane generates different reports during the synthesis flow.

These reports provide information about:

Synthesis statistics

Design checks

Flip-flops

Cell information

Timing

Slew

Minimum and maximum paths


The reports are useful for analyzing the synthesized design.


---

## 11. Static Timing Analysis using OpenSTA

OpenSTA is used to perform Static Timing Analysis on the synthesized design.

The timing reports provide information such as:

Startpoint

Endpoint

Clock

Fanout

Capacitance

Slew

Cell delay

Net delay

Arrival time

Required time

Slack


Timing paths between sequential elements can be analyzed to understand the timing behavior of the design.


---

## 12. Key Learning

Through this module, the following concepts are studied:

OpenLane flow

PicoRV32A synthesis

Sky130 configuration

Yosys synthesis

Synthesis statistics

Flop ratio

Gate-level netlist

Synthesis reports

OpenSTA

Static Timing Analysis

Timing-path analysis



---

Tools Used

OpenLane

Yosys

OpenSTA

Sky130 PDK

