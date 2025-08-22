---
title: Quasi Direct Drive Design and FOC
date: 2025-04-26
# external_link: https://github.com/pratham280/Omni_bot
tags:
  - Personal Project
---

A quasi-direct drive actuator designed for quadruped robots, utilizing a NEMA motor paired with cycloidal gears to achieve high torque transmission with minimal backlash. The actuator was developed as part of research to enhance efficiency, precision, and robustness in legged locomotion.

<!--more-->

---
# QDD Cycloidal Actuator (NEMA Stepper) — Project README

> **Objective:** Engineer a compact, low-backlash **Quasi-Direct-Drive (QDD)** actuator using a **cycloidal gearbox** driven by a **NEMA stepper motor**, fully 3D-printed in **PETG** for robust prototyping. Designed in **Fusion 360** with a research runway toward **FOC** control and deployment in a **quadruped robot**.

---

## Executive Summary
- **Why Cycloidal + QDD:** Cycloidal drives deliver **high reduction ratios in small envelopes** with **inherent shock tolerance** and **low effective backlash**—aligned with QDD’s requirement for high torque density and joint transparency.
- **Why NEMA Stepper:** Readily available, cost-efficient torque source with simple drive electronics; can be advanced toward **FOC** for smoother torque and higher dynamic fidelity.
- **Material:** All structural components 3D-printed in **PETG** to optimize stiffness/impact resistance vs. PLA while remaining production-feasible on consumer printers.
- **Status:** Hardware validated at bench scale; **controls research (FOC on stepper + state estimation)** in flight to unlock legged-locomotion-grade performance.

---

## System Architecture
- **Prime mover:** NEMA-series stepper motor (e.g., NEMA-17 or NEMA-23).
- **Transmission:** Single-stage **cycloidal reducer** (target ratio 20:1–40:1).
- **Output:** Hollow or solid shaft with radial/axial bearing stack.
- **Sensing (research track):**  
  - Motor phase current sensing for FOC  
  - Incremental/Magnetic encoder on output (and/or motor) for closed-loop torque/position  
- **Controller (research track):** MCU with FOC capability (e.g., STM32, ESP32), ROS 2 interface for quadruped integration.

---

## Design Rationale (QDD + Cycloidal)
- **High Ratio, Small Footprint:** Cycloidal stage achieves **30:1** in compact geometry where spur or planetary would be bulkier.
- **Low Backlash:** Preloaded lobes + compliant PETG flexure allow **near-zero effective backlash** under normal loads.
- **Shock Load Capacity:** Rolling contact and distributed tooth engagement handle impact events typical in legged robots.
- **Transmission Transparency:** Moderate ratio (20–40:1) preserves **backdrivability** critical for terrain interaction (QDD ethos).

---

## Mechanical Design (Fusion 360)
- **Key Parts:** Eccentric input shaft, cycloidal disk(s), ring gear housing, output pins/rollers, carrier plate, bearing stack, motor adapter.
- **Tolerances:** PETG shrinkage compensated; fit classes:  
  - **Press:** bearings in housing (−0.05 to −0.10 mm)  
  - **Slip:** rollers on pins (+0.05 to +0.10 mm)  
- **Bearings:**  
  - Input: 2× 608/6000-series (supports eccentric)  
  - Output: 1× thin-section radial + 1× thrust (or a single tapered pair)
- **Fasteners:** M3/M4 socket heads; use metal pins or dowels for roller posts.

---

## Manufacturing (PETG)
- **Orientation:** Load-bearing features aligned to maximize layer-parallel strength.  
- **Infill:** 40–60% gyroid/cubic; walls 4–6 perimeters.  
- **Temperature:** Nozzle 235–245 °C; Bed 75–85 °C; enclosure preferred.  
- **Post-Processing:** Deburr, light ream, graphite/PTFE dry lube on cycloidal track.

---

## Control & Electronics (Research Track)
- **Baseline:** Open-loop microstepping → closed-loop step/dir with encoder.  
- **FOC Study:** Run the 2-phase stepper as a PMSM equivalent with **Field-Oriented Control** (id/iq regulation), enabling:  
  - smoother torque at speed,  
  - reduced acoustic noise,  
  - better utilization of supply voltage,  
  - compliant control modes (impedance/torque).  
- **Targets:**  
  - **Torque control** bandwidth ≥ 50–100 Hz at output,  
  - **Position control** with friction/backlash compensation,  
  - ROS 2 joint interface for the quadruped stack.

---

## Parameters & Symbols

| Symbol | Description | Example |
|---|---|---|
| \( G \) | Gear ratio (output:input speed) | 30 |
| \( \eta \) | Gearbox mechanical efficiency | 0.80 (PETG cycloidal, well-lubed) |
| \( \tau_m \) | Motor torque (under-load, not holding) | 0.45 N·m (NEMA-17 typical) |
| \( \omega_m \) | Motor speed (rad/s) | 600 rpm = 62.83 rad/s |
| \( \tau_o \) | Output torque | — |
| \( \omega_o \) | Output speed (rad/s) | — |
| \( P_{in} \) | Input mechanical power | — |
| \( P_{out} \) | Output mechanical power | — |

---

## Core Equations

**Kinematics**
\[
\omega_o = \frac{\omega_m}{G}
\]

**Torque Transformation**
\[
\tau_o = \tau_m \cdot G \cdot \eta
\]

**Power**
\[
P_{in} = \tau_m \cdot \omega_m,\quad
P_{out} = \tau_o \cdot \omega_o = \eta \cdot P_{in}
\]

**Backdrivability Threshold (rule-of-thumb)**
\[
\tau_{bd} \approx \tau_c \cdot G
\]
where \( \tau_c \) is combined coulomb friction at motor side. Choose \( G \) to keep \( \tau_{bd} \) below desired compliance torque.

---

## Worked Example (Using Example Values)

- Given: \( \tau_m = 0.45\,\text{N.m},\ \omega_m = 600\,\text{rpm} = 62.83\,\text{rad/s},\ G = 30,\ \eta = 0.80 \)

**Input Power**
\[
P_{in} = 0.45 \times 62.83 \approx 28.27\,\text{W}
\]

**Output Speed**
\[
\omega_o = \frac{62.83}{30} \approx 2.094\,\text{rad/s} \quad(= 20\,\text{rpm})
\]

**Output Torque**
\[
\tau_o = 0.45 \times 30 \times 0.80 = 10.8\,\text{N.m}
\]

**Output Power**
\[
P_{out} = \tau_o \cdot \omega_o = 10.8 \times 2.094 \approx 22.6\,\text{W}
\]

**Implied Efficiency Check**
\[
\frac{P_{out}}{P_{in}} \approx \frac{22.6}{28.27} \approx 0.80
\]

---

## Cycloidal Geometry Notes (for Fusion 360)
- **Reduction:** \( G = \dfrac{N_r - N_c}{N_c} \) where \( N_r \) = ring pins count, \( N_c \) = cycloid lobes.  
  - Example: \( N_r = 31,\ N_c = 30 \Rightarrow G \approx 30:1 \)
- **Eccentricity:** Set by eccentric bearing offset \( e \); balance dynamic forces with **dual-disk** mirrored phasing for reduced ripple.
- **Output Carrier:** Use **roller pins** (metal dowels + bushings) to minimize sliding friction on PETG lobes.

---

## Bill of Materials (Prototype)
- NEMA-17/23 stepper (select for current/torque headroom)  
- Motor driver (baseline: step/dir; research: FOC-capable MCU + gate driver)  
- 2× input bearings (608/6000)  
- Output bearing stack (1× radial + 1× thrust or tapered pair)  
- Metal dowel pins / shoulder screws for rollers  
- Magnets/Encoder (AS5600/AS5047 or incremental encoder)  
- Fasteners M3/M4, heat-set inserts, PETG filament

---

## Controls Research Plan (FOC & Quadruped Integration)
1. **Electrical Characterization (stepper as PMSM):**  
   Measure \( R_s, L_d, L_q, K_e \) → parameterize FOC.  
2. **FOC Bring-Up:**  
   Clarke/Park transforms, PI loops on \( i_d, i_q \), SVPWM; enforce \( i_d \approx 0 \) for max torque per amp.  
3. **Observers:**  
   Back-EMF or encoder-aided rotor angle; extend to **disturbance observer** for friction/torque ripple compensation.  
4. **Torque Mode:**  
   Map \( i_q \to \tau_m \) via calibration; expose **ROS 2 control** interface (`sensor_msgs/JointState`, `ros2_control`).  
5. **Impedance Control:**  
   \( \tau_{cmd} = K(\theta_{ref}-\theta) + D(\dot{\theta}_{ref}-\dot{\theta}) \) at the **output** using gearbox model.  
6. **Gait Integration:**  
   Validate stance/swing phases on benchtop leg rig; iterate for bandwidth and thermal limits.

---

## Validation & KPIs
- **Static torque @ output (continuous / peak)**  
- **Transmission efficiency \( \eta \)** vs. speed & load  
- **Effective backlash** (loaded/unloaded)  
- **Torque bandwidth** (closed-loop)  
- **Thermal rise** at motor and bearings (10-min and 30-min duty)  
- **Acoustic noise** vs. control mode (microstep vs. FOC)

---

## Risk & Mitigation
- **Torque Ripple / Resonance:** Address with FOC + dual-cycloid phasing; add output inertia if needed.  
- **Wear on PETG Tracks:** Use rollers, dry lube, periodic inspection; migrate to nylon/filled polymers for production.  
- **Backdrivability Loss at High \( G \):** Keep \( G \le 40 \) for leg joints requiring compliance.

---

## Quick Start Checklist
- [ ] Print PETG parts with specified wall/infill  
- [ ] Press-fit bearings; verify concentricity and endplay  
- [ ] Assemble cycloid with preloaded rollers; check smooth backdrive  
- [ ] Motor driver bring-up; current limit within motor spec  
- [ ] Encoder alignment and calibration  
- [ ] Run no-load sweep → incremental load tests → log \(\tau,\ \omega,\ P\)

---

## License & Attribution
- **Design:** Fusion 360 native + neutral STEP included (internal).  
- **Manufacturing:** 100% PETG prototype path.  
- Cite this README when re-using the design in derivative works.

---

## Appendix A — Editable Calculation Template

Plug in your measured values:

```text
Given:
  tau_m  = ______ N·m
  omega_m_rpm = ______ rpm
  G      = ______
  eta    = ______ (0.70–0.90 typical for tuned cycloidal)
Convert:
  omega_m = omega_m_rpm * 2π/60  [rad/s]

Compute:
  P_in  = tau_m * omega_m
  omega_o = omega_m / G
  tau_o = tau_m * G * eta
  P_out = tau_o * omega_o
Check:
  efficiency = P_out / P_in  (should ≈ eta)
```
---

## Appendix B — Tuning Notes (Stepper → FOC)

- Start with **low bus voltage**, validate current sensing, then scale up.  
- Identify **dead-time** and calibrate phase advance.  
- Map **i<sub>q</sub>-to-torque** experimentally with a lever arm + load cell.  
- Implement **current-loop anti-windup** and **rate limits** to avoid chatter through the gearbox.  

---

**Bottom line:**  
This QDD cycloidal actuator leverages a stepper for accessible torque, a high-ratio low-backlash reducer for compact power density, and a forward-leaning FOC roadmap. It’s production-conscious (**PETG**), simulation-friendly (**Fusion 360**), and architected for **quadruped deployment** once controls research lands.
