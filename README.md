
# Design of Folded Cascode Operational Amplifier with CMFB

This project involves reproducing and simulating a research paper on the design of a Folded-Cascode Operational Amplifier with Common-Mode Feedback (CMFB) using eSim.

The original design was implemented using the Silterra 0.13 µm CMOS process in Cadence. As part of the FOSSEE Research Migration Project, I migrated the circuit to eSim (KiCad + Ngspice 46) using the open-source 130nm_bulk.pm transistor model library.

The main objective was to study the performance of a folded-cascode amplifier with a double-detection CMFB circuit and compare the simulation results with those reported in the original research paper.

## Project Overview

The design consists of two main circuit blocks:

### 1. Folded-Cascode Operational Amplifier

A single-stage folded-cascode amplifier was designed using an NMOS differential input pair and a low-voltage cascode network.

The main circuit includes:
- NMOS differential input pair (M9 and M10).
- Cascode transistors (M3–M8).
- DC biasing transistors (M1 and M2).
- Tail current source (M11).
- 1 pF load capacitor.

The folded-cascode topology provides high output impedance, voltage gain, and a wide input common-mode range.

### 2. Common-Mode Feedback (CMFB)

A double-detection CMFB circuit was implemented to stabilize the output common-mode voltage of the fully differential amplifier.

Its main components include:
- M13 and M14: Sense the two differential output voltages.
- M15: Provides the reference voltage.
- M12: Provides the feedback path to the main amplifier.
- M16: Acts as the CMFB tail current source.

This double-detection approach helps regulate the output common-mode voltage and improve common-mode rejection.

## Project Files

| File | Description |
|---|---|
| [CMFB.sch](CMFB.sch) | Schematic of the double-detection common-mode feedback circuit. |
| [Folded_Cascode_OTA.sch](Folded_Cascode_OTA.sch) | Main folded-cascode operational amplifier schematic. |
| [Folded_Cascode_OTA.cir](Folded_Cascode_OTA.cir) | SPICE circuit file used for simulation. |
| [Folded_Cascode_OTA.net](Folded_Cascode_OTA.net) | Generated netlist containing the circuit connections and component information. |
| [Folded_Cascode_OTA.proj](Folded_Cascode_OTA.proj) | eSim project file. |
| [130nm_bulk.pm](130nm_bulk.pm) | MOSFET model library used for transistor-level simulation. |
| [Folded_Cascode_OTA_Previous_Values.xml](Folded_Cascode_OTA_Previous_Values.xml) | XML file containing previously saved schematic values. |

## Technology & Simulation Setup

| Parameter | Value |
|---|---|
| EDA Tool | eSim (KiCad + Ngspice) |
| Simulator | Ngspice 46 |
| Technology | 130 nm Bulk CMOS |
| Model Library | 130nm_bulk.pm |
| Original Technology | Silterra 0.13 µm CMOS |
| Supply Voltage | 1.8 V |
| Load Capacitor | 1 pF |

## Simulation & Analysis

The circuit was simulated in eSim using Ngspice. The following analyses were performed:

### 1. AC Analysis
- Frequency sweep: 100 Hz to 1 GHz.
- Analysed DC gain and frequency response.
- Studied gain roll-off and phase behaviour.
- Examined unity-gain bandwidth and phase margin.

### 2. Transient Analysis
- Simulation duration: 0–300 ns.
- Applied a differential pulse input.
- Observed the differential output response.
- Analysed slew-rate behaviour and settling characteristics.

### 3. DC Operating Point Analysis
- Verified transistor bias conditions.
- Examined the operating points of the MOSFETs.
- Checked the circuit operation at a 1.8 V supply voltage.

## Simulation Results

The eSim simulation results were compared with the original research paper to evaluate the performance of the migrated circuit.

| Parameter | Original Research Paper | eSim Results |
|---|---:|---:|
| DC Gain | 62.69 dB | ~33–34 dB |
| Phase Margin | 68.36° | Not directly measurable |
| Unity Gain Bandwidth | 133.1 MHz | ~1–10 MHz (estimated) |
| Slew Rate | 22.6 V/µs | ~21–22 V/µs |
| Supply Voltage | 1.8 V | 1.8 V |
| Load Capacitor | 1 pF | 1 pF |
| Power Dissipation | 0.3 mW | Not measured |

**Key Observations:**

- The simulated DC gain was approximately 33–34 dB, lower than the 62.69 dB reported in the original paper.
- The slew rate was approximately 21–22 V/µs, which was close to the reference value of 22.6 V/µs.
- The phase response showed a dominant-pole trend, but a direct phase-margin measurement was not possible because the gain did not cross 0 dB within the observed response.
- The transient output exhibited slew-limited behaviour rather than a clean step-and-settle response.

The differences in gain and bandwidth are primarily attributed to the difference between the original proprietary Silterra transistor models and the open-source 130nm_bulk.pm library used in eSim.

## Reference Research Paper

**Title:** Design of Folded Cascode Operational Amplifier (Op-Amp) with Common-Mode Feedback (CMFB) for Pipeline ADC.

**Authors:** Izatul Syafina Ishak, Sohiful Anuar Zainol Murad, Mohd Fairus Ahmad and Neoh Siew Chin.

**Conference:** Malaysian Technical Universities Conference on Engineering & Technology (MUCET), 2013.

## About

This project was completed as part of the FOSSEE Research Migration Project at IIT Bombay.

Working on this project helped me understand transistor-level analog circuit design, folded-cascode architecture, common-mode feedback, and the use of SPICE model libraries in analog simulations.

It also gave me practical experience in migrating an existing research design from a proprietary EDA environment to an open-source simulation workflow and analysing the differences between the original and migrated results.

---

**Author:** Areeb Jamal

**GitHub:** [@AreebJamal](https://github.com/AreebJamal)
