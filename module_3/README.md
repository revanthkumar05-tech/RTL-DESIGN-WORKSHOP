# Module 3: Design Library Cell Using Magic Layout and ngspice Characterization

## Overview

This module focuses on CMOS inverter characterization, physical layout design, and design rule checking using the Sky130 PDK. The experiments connect transistor-level circuit simulation with physical layout implementation and verification.

The module consists of three sections:

- **SKY130_D3_SK1:** SPICE deck creation and ngspice simulation
- **SKY130_D3_SK2:** Magic layout creation and extracted-netlist simulation
- **SKY130_D3_SK3:** Sky130 technology-file Design Rule Check (DRC) experiments

## Learning Objectives

- Understand CMOS inverter operation through transistor-level simulation.
- Create SPICE decks and perform DC and transient analyses using ngspice.
- Study the effects of transistor sizing on inverter characteristics.
- Design a CMOS inverter layout using Magic.
- Extract a SPICE netlist from the physical layout and simulate it.
- Understand design rules associated with polysilicon and nwell layers.
- Analyze DRC results and identify layout rule violations.

---

## 1. SKY130_D3_SK1: SPICE Deck Creation and ngspice Simulation

### Introduction

A CMOS inverter is a fundamental digital circuit consisting of a PMOS transistor and an NMOS transistor. It produces an output that is the logical complement of its input.

In this experiment, SPICE decks are created to simulate an inverter using Sky130 transistor models. Two transistor-sizing configurations are considered to study how transistor dimensions affect circuit behavior.

### Case 1: Initial Inverter Configuration

The first configuration uses the following transistor widths:

- PMOS width (Wp): 0.84 µm
- NMOS width (Wn): 0.36 µm

A SPICE deck is prepared with transistor models, circuit connections, input sources, and simulation commands.

**DC Analysis**

A DC sweep is performed by varying the input voltage and observing the output voltage. The resulting Voltage Transfer Characteristic (VTC) illustrates how the inverter output changes from logic HIGH to logic LOW as the input voltage increases.

**Transient Analysis**

A pulsed input signal is applied to the inverter. The input and output waveforms are observed to study the inverter's switching behavior and time-domain response.

### Case 2: Modified Inverter Configuration

In the second configuration, the PMOS transistor width is increased while the NMOS transistor width remains unchanged.

- PMOS width (Wp): 2.1 µm
- NMOS width (Wn): 0.36 µm

DC and transient analyses are performed again using the modified configuration.

The results are compared with those of the first configuration to understand how changing the relative transistor drive strengths affects the voltage-transfer characteristic and switching response.

### Observations

- The inverter output is complementary to its input.
- DC analysis helps identify the transition region and switching characteristics.
- Transient analysis demonstrates the inverter's response over time.
- Increasing the PMOS width changes its pull-up strength and can affect the output transition behavior.
- The actual differences between the configurations are evaluated using the simulation results.

---

## 2. SKY130_D3_SK2: Magic Layout and Extracted-Netlist Simulation

### Introduction

After transistor-level characterization, the next step is to create the physical layout of the CMOS inverter using Magic and the Sky130 technology setup.

Physical layout represents the arrangement of transistors and interconnections required to implement the circuit.

### Layout Creation

The CMOS inverter layout is created in Magic using the appropriate Sky130 technology files.

The layout includes transistor structures, interconnections, input and output connections, and power and ground connections.

### Layout Extraction

Once the layout is completed, the circuit information is extracted using Magic. The extracted representation can be converted into a SPICE netlist for electrical simulation.

Typical extraction commands include:

```text
extract all
ext2spice
```

The generated netlist represents the circuit derived from the physical layout. Depending on the extraction settings, it may also include parasitic information.

### Extracted-Netlist Simulation

The extracted SPICE netlist is simulated using ngspice with a pulsed input signal.

The resulting waveforms are examined to verify that the extracted circuit retains the expected inverter behavior.

### Observations

- Magic is used to create and inspect the physical layout.
- Extraction connects the physical implementation to transistor-level simulation.
- The extracted netlist can be used to verify circuit behavior after layout creation.
- Parasitic effects, when included, may influence the simulated response.

---

## 3. SKY130_D3_SK3: Sky130 Technology-File DRC Labs

### Introduction

Design Rule Checking (DRC) is an important physical verification step in integrated circuit design. It checks whether layout geometries satisfy the design rules defined by the fabrication technology.

This experiment examines test layouts involving polysilicon and nwell geometries using Magic and the Sky130 technology files.

### Poly DRC Experiment

A test layout containing polysilicon geometries is opened in Magic and checked against the applicable technology rules.

The DRC output is inspected to understand reported conditions, including relevant width, spacing, overhang, and other applicable checks.

The reported messages are correlated with the corresponding layout shapes to understand why a rule is triggered.

### Nwell DRC Experiment

A separate test layout containing nwell geometries is analyzed using Magic's DRC functionality.

The results are examined to understand the technology rules associated with well geometry, including applicable width, spacing, and overlap checks.

### Observations

- DRC identifies layout geometries that violate applicable technology rules.
- The layout view helps explain the geometric context of reported violations.
- Poly and nwell checks demonstrate different categories of physical design constraints.
- DRC results must be interpreted alongside the layout and the applicable technology rules.

---

## Overall Workflow

The experiments follow this sequence:

1. Prepare SPICE decks for the CMOS inverter.
2. Run DC and transient simulations using ngspice.
3. Compare the two transistor-sizing configurations.
4. Create the inverter layout in Magic.
5. Extract the layout netlist and simulate it.
6. Open the poly and nwell test layouts.
7. Run DRC and examine the reported results.

## Conclusion

Module 3 demonstrates the relationship between transistor-level simulation, physical layout design, netlist extraction, and layout verification using the Sky130 technology.

The inverter experiments help explain how transistor sizing influences circuit behavior. The Magic layout and extraction experiments connect electrical simulation to physical implementation, while the poly and nwell DRC experiments introduce the importance of following fabrication design rules.

Together, these activities provide practical experience with CMOS inverter characterization and fundamental physical verification concepts in an open-source VLSI design environment.
