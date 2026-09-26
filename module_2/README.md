# Floorplanning and Placement - PicoRV32a

This module documents the floorplanning, I/O placement, and standard-cell placement stages of the `picorv32a` RISC-V core using the OpenLane RTL-to-GDSII flow and Sky130 PDK.

Floorplanning defines the physical die and core structure, I/O placement assigns locations to design pins, and placement arranges the synthesized standard cells inside the core area.

## Workflow

The physical-design flow followed in this module is:

`config.tcl`
→ `Sky130 standard-cell configuration`
→ `Floorplan configuration`
→ `Floorplan Tcl settings`
→ `Floorplan DEF`
→ `I/O placement`
→ `Initial floorplan`
→ `I/O and boundary inspection`
→ `Standard-cell placement`
→ `Detailed placement`

## 1. Reviewing the Main Design Configuration

The main `config.tcl` identifies the design as `picorv32a` and specifies the Verilog source, SDC constraints, clock period, and clock port.

Important parameters include:

- `DESIGN_NAME`
- `VERILOG_FILES`
- `SDC_FILE`
- `CLOCK_PERIOD`
- `CLOCK_PORT`
- `CLOCK_NET`

These settings provide the basic information required by the OpenLane flow.

## 2. Sky130 Standard-Cell Configuration

The Sky130 standard-cell configuration contains technology- and library-specific settings.

Important parameters include:

- `GLB_RT_ADJUSTMENT`
- `SYNTH_MAX_FANOUT`
- `CLOCK_PERIOD`
- `FP_CORE_UTIL`
- `PL_TARGET_DENSITY`

These parameters influence synthesis, routing, core utilization, and placement density.

## 3. Floorplanning Configuration

The OpenLane floorplanning variables define the physical organization of the design.

Important options include:

- Core utilization
- Aspect ratio
- Relative or absolute floorplan sizing
- Horizontal and vertical I/O metal layers
- I/O placement mode
- Core margins
- Power-distribution settings
- I/O dimensions and spacing

These settings determine the die outline, core boundary, standard-cell rows, and power-grid arrangement.

## 4. Sky130 Floorplan Tcl Settings

The Sky130 floorplan configuration provides the default physical-design settings used during floorplanning.

It includes parameters related to:

- Core utilization
- Aspect ratio
- I/O metal layers
- Power-distribution network offsets and pitches
- I/O placement
- Core margins
- Halo regions
- Power-grid checks

These settings control how the synthesized design is converted into its initial physical structure.

## 5. Generating the Floorplan DEF

The floorplan stage generates a DEF representation of the physical design.

The DEF contains information such as:

- Design name
- Database units
- Die area
- Standard-cell rows
- Row orientations
- Physical placement regions

The generated rows provide legal locations where standard cells can later be placed.

## 6. Checking the I/O Placement Log

The OpenROAD I/O placement stage reads the technology LEF and floorplan DEF before placing the design pins.

The log provides information about:

- Technology layers
- Vias
- Library cells
- Pins
- Components
- Nets
- Connections

The I/O placement stage assigns physical locations to the design pins according to the configured placement mode.

## 7. Viewing the Initial Floorplan

The initial floorplan can be inspected using Magic.

At this stage, the design shows the die boundary, core region, standard-cell rows, and physical boundaries before the synthesized cells are densely placed.

This provides a visual check of the basic physical organization of the design.

## 8. Inspecting Floorplan I/O and Boundary Details

A detailed Magic view can be used to inspect the floorplan boundary and I/O regions.

This view allows inspection of:

- Technology layers
- Core boundaries
- Boundary cells
- I/O pins
- Named design nets

The I/O pins are positioned around the boundary before detailed cell placement and routing.

## 9. Viewing the Initial Standard-Cell Placement

After placement, the synthesized standard cells are arranged inside the previously generated rows.

The core becomes populated with logic cells while the row and boundary structures remain visible.

This represents the physical implementation of the synthesized netlist before detailed routing.

## 10. Inspecting a Detailed Placement Region

A zoomed Magic view allows individual Sky130 standard cells to be inspected.

The placement includes logic gates, multiplexers, flip-flop-related cells, and other physical cells.

This view verifies that standard cells have been assigned legal locations and orientations within the floorplan.

## Flow Summary

The complete Module 2 flow is:

`config.tcl`
→ `Sky130 configuration`
→ `Floorplan configuration`
→ `Floorplan`
→ `Floorplan DEF`
→ `I/O placement`
→ `Initial floorplan`
→ `I/O and boundary inspection`
→ `Standard-cell placement`
→ `Detailed placement`

## Conclusion

This module demonstrates how a synthesized RTL design is converted into an initial physical layout through floorplanning and placement.

The process establishes the die and core structure, places I/O pins, creates standard-cell rows, and finally places the synthesized standard cells inside the core area.

The generated layout views will be added separately as screenshots from our own execution.
