# ⚙️ RISC-V SoC Tapeout Program — VSD  
### CMOS Switching Threshold & Dynamic Simulations  

---

## 📘 Table of Contents
1. [Overview](#overview)
2. [Part 1 — VTC Characteristics](#part-1--vtc-characteristics)
3. [Part 2 — Transient Analysis](#part-2--transient-analysis)
4. [Summary & Observations](#summary--observations)
5. [Tools & Notes](#tools--notes)

---

## 🧠 Overview

This lab explores the **Voltage Transfer Characteristics (VTC)** and **transient behavior** of a **CMOS inverter** using the **SkyWater 130nm PDK** and **Ngspice** simulator.  
Through this experiment, we aim to:

- Determine the **switching threshold voltage**  
- Evaluate **noise margins** for stable logic levels  
- Measure **propagation delay and waveform response**  

---

## 🔹 Part 1 — VTC Characteristics
<details>
<summary><b>🧩 Step-by-step Simulation</b></summary>

### 📁 Step 1: Navigate to the Design Directory
```bash
$ cd sky130CircuitDesignWorkshop/design/
```

### ▶️ Step 2: Run the SPICE Netlist
```bash
$ ngspice day3_inv_vtc_Wp084_Wn036.spice
```

**Inverter Configuration:**
- **PMOS width (Wp):** 0.84 µm  
- **NMOS width (Wn):** 0.36 µm  
- Balanced inverter for near-midpoint switching.

---

### 📈 Step 3: Plot the Voltage Transfer Curve (VTC)
```bash
$ plot out vs in
```

#### 🖼️ Output:
![VTC Graph](https://github.com/user-attachments/assets/3077606d-f1dd-4c13-bedd-5b8f4349d5f3)

**Interpretation:**
- The **VTC curve** displays how the output voltage changes with input.  
- Key parameters include:
  - **V<sub>M</sub> (Switching Threshold)**
  - **Noise Margins (NML, NMH)**
  - **Transition Region (High Gain)**

</details>

---

## ⚡ Part 2 — Transient Analysis
<details>
<summary><b>⚙️ Simulation Steps</b></summary>

### ▶️ Step 1: Run the Transient SPICE Simulation
```bash
$ ngspice day3_inv_tran_Wp084_Wn036.spice
```

This analysis captures **dynamic inverter response** under a square-wave input.

---

### 📊 Step 2: Plot Time-Domain Output
```bash
$ plot out vs time in
```

#### 🖼️ Output Waveforms:
![Transient Output 1](https://github.com/user-attachments/assets/324f4f5b-cdd9-4580-a177-1e4697cfc7a6)
![Transient Output 2](https://github.com/user-attachments/assets/0578767b-16db-4ac0-9f1a-f537d059bc34)

**Analysis:**
- **V<sub>in</sub>** (Input) vs **V<sub>out</sub>** (Output) shows logic inversion.  
- **Propagation delay (t<sub>pHL</sub>, t<sub>pLH</sub>)** indicates circuit switching speed.  
- Rise and fall times reveal how capacitive loading impacts timing performance.  

</details>

---

## 📊 Summary & Observations

| Parameter | Description | Typical Result |
|------------|--------------|----------------|
| **V<sub>M</sub>** | Switching threshold voltage | ≈ 0.9 V (for 1.8 V supply) |
| **Noise Margins** | Logic stability range | Sufficient for robust logic |
| **t<sub>pHL</sub> / t<sub>pLH</sub>** | Propagation delays | Few nanoseconds |
| **Output Waveform** | Logic inversion | Clean, sharp transitions |

✅ **Conclusion:**  
The CMOS inverter demonstrates strong logic integrity, good noise margins, and reliable switching — ideal for integration into SoC-level logic gates.

---

## 🧰 Tools & Notes

**Tools Used:**
- 🧠 *SkyWater 130nm PDK*  
- ⚡ *Ngspice Circuit Simulator*  
- 💻 *Linux Terminal / VS Code Environment*  

**Pro Tips:**
- Adjust **W<sub>p</sub> / W<sub>n</sub>** ratio to tweak the switching threshold.  
- Modify supply voltage (VDD) to study power-delay trade-offs.  
- Use finer time steps (`.tran 0.1n 50n`) for more detailed transient plots.

---

> 💡 **Experiment Further:**  
> Try cascading two inverters to visualize logic buffering and measure delay propagation through multiple stages.

---

**© 2025 — VLSI System Design (VSD) Lab**
