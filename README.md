# VSD-RISC-V-WEEK-2-

# 📘 Week 3: System-on-Chip Design & Simulation — Hands-On with BabySoC

## 🔧 **Overview**

This week’s focus was on reinforcing key digital design concepts through a guided simulation of the **VSDBabySoC platform**. The task centered around functional modeling and observing the interaction between components like a RISC-V core, PLL, and DAC — implemented and validated using open-source tools.
---
## 🎯 **Goals for the Week**

- Understand the purpose and structure of a basic educational SoC
- Learn how to convert TL-Verilog to synthesizable Verilog
- Perform simulation to verify the system’s digital and analog behavior
- Visualize signal waveforms and verify correct operation across components
---
## 🧩 **What Is BabySoC?**

**BabySoC (VSDBabySoC)** is a compact learning-oriented SoC that includes:

- **RISC-V CPU (RVMYTH)**: Processes instructions and generates digital output
- **PLL Block**: Creates a stable clock signal
- **10-bit DAC**: Converts digital output into analog signals

This integration mimics a real-world SoC at a smaller, manageable scale.

---
## 🛠️ **Simulation Flow: Steps Taken**

### ✅ **1. Repository Setup**

Cloned the base project to a local directory:

```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC

```

- [x]  Files downloaded successfully
- [x]  Directory structure verified

---
### ✅ **2. Environment Preparation**

Installed necessary Python tools to run the TL-Verilog to Verilog converter:

```bash
sudo apt update
sudo apt install python3-venv python3-pip
python3 -m venv sp_env
source sp_env/bin/activate
pip install pyyaml click sandpiper-saas

```

- [x]  Virtual environment created
- [x]  SandPiper-SaaS installed

---
### ✅ **3. TL-Verilog to Verilog Conversion**

Used the SandPiper tool to generate standard Verilog from TLV source files:

```bash
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/

```

- [x]  RVMYTH core converted to Verilog
- [x]  Output verified in the module folder

---
### ✅ **4. Running Pre-Synthesis Simulation**

Compiled and ran the testbench to simulate SoC behavior before synthesis:

```bash
mkdir -p output/pre_synth_sim
iverilog -o output/pre_synth_sim/pre_synth_sim.out \
    -DPRE_SYNTH_SIM \
    -I src/include \
    -I src/module \
    src/module/testbench.v

cd output/pre_synth_sim
./pre_synth_sim.out

```

- [x]  Simulation binary generated
- [x]  Simulation output file (`.vcd`) created successfully

---
### ✅ **5. Visualizing with GTKWave**

Launched GTKWave to observe the generated waveform from the simulation:

```bash
gtkwave output/pre_synth_sim/pre_synth_sim.vcd

```

- [x]  Digital signals verified (clock, reset, register values)
- [x]  Analog output from DAC observed in step format


---
## 🔬 **Waveform Analysis & Observations**

### ✅ **Clock Signal**

- Regular and clean waveform
- PLL correctly generated 8x clock from reference input

### ✅ **Reset Signal**

- Active at simulation start, then deactivated
- System transitioned from idle to operational state

### ✅ **RVMYTH Output (10-bit)**

- Register `r17` correctly updated over time
- Data successfully fed into DAC module

### ✅ **Analog Output**

- Staircase pattern evident in DAC signal
- Confirms proper digital-to-analog conversion

---

## 🧠 **Skills Practiced and Concepts Reinforced**

- [x]  TL-Verilog to Verilog transformation
- [x]  Functional modeling using Icarus Verilog
- [x]  GTKWave-based waveform analysis
- [x]  Working with mixed-signal systems
- [x]  Clock domain behavior and reset logic
- [x]  Data path verification from CPU to DAC

---

## 📌 **Completion Checklist**

### 🧠 Theory

- [x]  SoC design structure understood
- [x]  Internal architecture of RVMYTH explored
- [x]  Clock synchronization in SoC reviewed

### 🧪 Practical Work

- [x]  Environment setup complete
- [x]  TL-Verilog converted to Verilog
- [x]  Testbench compiled and executed
- [x]  Waveforms analyzed and behavior confirmed

### 🧰 Tool Usage

- [x]  Git & terminal workflow
- [x]  SandPiper for TLV conversion
- [x]  Icarus Verilog for simulation
- [x]  GTKWave for waveform viewing

---

## 🧭 **Summary**

This week was focused on applying theoretical knowledge in a controlled, testable environment. By simulating the BabySoC system, the connection between CPU logic, clock control, and analog signal output became clearer. The experience also highlighted the value of simulation tools in detecting and verifying design correctness before proceeding to synthesis.

---

## 🔮 **Next Steps**

- Implement post-synthesis simulation (GLS)
- Explore synthesis flow with Yosys
- Investigate timing analysis and hardware mapping
- Continue working on verification and physical design

---

## 🏁 **Week 3 Wrap-Up: All Objectives Achieved**

**Status**:

✅ Functional Simulation Done

✅ Toolchain Mastery Achieved

✅ SoC Component Understanding Improved
