---
title: RISC-V CPU Architecture using Quartus & FPGA
date: 2024-04-26
# external_link: https://github.com/pratham280/Warehouse_management
tags:
  - Personal Project
---

Implemented a custom RISC-V CPU architecture on an Intel Altera Cyclone IV E FPGA for e-Yantra (AstroTinker theme). Designed core components in Verilog, simulated functionality with ModelSim, and validated execution of C programs compiled with a RISC-V toolchain.

<!--more-->
---

# 🖥️ RISC-V CPU Development – IIT Bombay e-Yantra Robotics Competition (eYRC)

As part of the **AstroTinker theme** in the **IIT Bombay e-Yantra Robotics Competition (eYRC)**,  
I worked on implementing a **RISC-V CPU architecture** on an **Intel Altera Cyclone IV E FPGA** using **Quartus Prime** and **ModelSim**.  
The project focused on designing a simplified yet functional **Reduced Instruction Set Computer (RISC)** processor and executing real programs compiled from C to binary.  

---

## ⚙️ Development Environment
- **FPGA Board**: Intel Altera Cyclone IV E  
- **Software Tools**: Quartus Prime (design & synthesis), ModelSim (simulation & waveform analysis)  
- **Compiler**: RISC-V C/C++ compiler toolchain  

---

## 🧩 CPU Architecture Components Implemented
The RISC-V CPU design followed a classic pipeline-inspired model with essential building blocks:  

- **Program Counter (PC)** – keeps track of the instruction address  
- **Instruction Memory** – stores the compiled binary instructions  
- **Control Unit** – decodes instructions and generates control signals  
- **Register File** – general-purpose registers for temporary storage  
- **ALU (Arithmetic Logic Unit)** – executes arithmetic and logical operations  
- **Data Memory** – handles load/store instructions  
- **Instruction Decoder** – interprets the opcode and directs data flow  
- **Multiplexers (MUX)** – manage data paths between CPU components  
- **Clock & Reset Logic** – synchronization and initialization of the system  

---

## 🔄 Workflow

### 1. **CPU Design in Quartus Prime**
- Implemented all CPU modules in Verilog on the FPGA.  
- Synthesized and tested the logic design using Quartus simulation tools.  

### 2. **Simulation with ModelSim**
- Exported Verilog design files from Quartus into ModelSim.  
- Created **testbenches** to feed instructions and verify CPU behavior.  
- Analyzed **waveforms** for PC updates, instruction decoding, ALU outputs, and memory transactions.  
- Validated that the datapath correctly executed the instruction cycle: **Fetch → Decode → Execute → Memory → Writeback**.  

### 3. **Program Compilation**
- Wrote C programs (arithmetic ops, loops, memory access).  
- Compiled using the **RISC-V GCC compiler** into machine code binaries.  

### 4. **Execution on FPGA**
- Loaded compiled instructions into the instruction memory.  
- Ran the program on the FPGA, validating outputs through LEDs, GPIOs, and serial debug.  

---

## 🚀 Outcome
- Successfully implemented and simulated a **custom RISC-V CPU** using Verilog + ModelSim.  
- Demonstrated program correctness via **simulation waveforms** before FPGA deployment.  
- Executed compiled C programs directly on the CPU running on Cyclone IV E.  

---

## 📌 Significance
This project bridged **computer architecture**, **FPGA design**, and **compiler toolchains**.  
Simulation in **ModelSim** ensured correctness at the micro-architectural level, while FPGA implementation validated real-world hardware execution.  
It highlighted the importance of **hardware–software co-design** for robotics and embedded applications.  

---

