---
title: Large Scale 3D Printer   
date: 2024-09-26
# external_link: https://github.com/pratham280/Mars_Rover
tags:
  - Freelancing
---

A custom-designed large-scale 3D printer with a 2×2x2 meter print bed, built for printing large prototypes and parts. It uses a Raspberry Pi for high-level control, paired with an Octopus v1.1 board for precise motion control and coordination.

<!--more-->
---

# 🏗️ Large-Scale 3D Printer Development – 3D Wizard Printing Farm

This project involved the **design and development of a custom large-scale 3D printer** for a professional 3D printing farm named **3D Wizard**.  
The printer was engineered to handle industrial-scale prints with a **2 × 2 × 2 meter build volume**, using a **custom pellet-fed extrusion system** and a robust motion architecture.  

---

## ⚙️ Mechanical Design
- **Build Volume**: 2000 × 2000 × 2000 mm  
- **Frame**: Custom room-sized enclosure built from **aluminum profiles** and **aluminum-reinforced polymer sheets** for rigidity and safety.  
- **Z-Axis**: 4× ball screws, each driven by a **NEMA stepper motor**, ensuring synchronized and stable vertical motion.  
- **X–Y Axis**: Heavy-duty linear guides with a custom extruder system.  
- **Extrusion System**:  
  - **10 mm nozzle size**  
  - **Pellet-fed system** using **PPF plastic pellets**  
  - Integrated **screw conveyor system** for feeding plastic into the extruder  

---

## 🔌 Control System
- **Motor Drivers**: TB6600 stepper motor drivers for reliable high-torque operation.  
- **Main Controller**: **Octopus v1.1 control board**, responsible for executing G-code.  
- **Wireless Capability**:  
  - **Raspberry Pi 3B+** running **Klipper firmware**  
  - **Mainsail web interface** hosted on Pi for wireless control and telemetry  

---

## 📡 Telemetry & Remote Management
Through **Mainsail + Klipper integration**, the system provided:  
- Homing & positioning control  
- Real-time printing status  
- Print history and logs  
- Live telemetry (temperatures, positions, system state)  
- Remote G-code upload and execution  

---

## 🚀 Outcome
- Delivered a **fully functional industrial-scale 3D printer** tailored for **3D Wizard’s printing farm**.  
- Achieved stable motion across a large build volume with synchronized Z-axis mechanics.  
- Implemented a **wireless control and monitoring system**, enabling efficient remote operation.  
- Validated extrusion of **PPF pellets** with a custom screw-fed extruder and large-diameter nozzle.  

---

## 📌 Significance
This project demonstrated the integration of **mechanical engineering, control systems, and IoT-based monitoring** in large-format additive manufacturing.  
It enabled **3D Wizard** to expand capabilities in **large-scale prototyping and manufacturing** using a reliable, custom-built platform.  

---

