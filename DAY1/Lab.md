# ⚙️ RISC-V SoC Tapeout Program — VSD Journey  
### 🧪 Lab: NMOS Drain Current (I<sub>D</sub>) vs. Drain-to-Source Voltage (V<sub>DS</sub>) Simulation  

> This lab demonstrates the practical simulation of **I<sub>D</sub>–V<sub>DS</sub> characteristics** of an **n-channel MOSFET (nfet)** using **Ngspice** and **Sky130 open-source PDK**.  
> The goal is to visualize transistor behavior across different operating regions — **cutoff, linear,** and **saturation** — and understand how gate voltage controls current flow.

---

## 🧰 Prerequisites

Before running the simulation, ensure you have the following tools and repositories set up:

| Tool / Resource | Description |
|------------------|-------------|
| **Ngspice** | Open-source SPICE simulator for analog/digital circuits |
| **Sky130 PDK** | Process Design Kit for open-source CMOS fabrication |
| **Git** | To clone and access the VSD workshop repository |

---

## ⚡ Step 1 — Clone the VSD Sky130 Workshop Repository

This repository contains pre-built SPICE netlists for various transistor-level experiments.

```bash
$ git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
$ cd sky130CircuitDesignWorkshop/design/
```

---

## 🧩 Step 2 — Run the NMOS I<sub>D</sub>–V<sub>DS</sub> Simulation

Use **Ngspice** to simulate the transistor behavior using the provided `.spice` file:

```bash
$ ngspice day1_nfet_idvds_L2_W5.spice
```

📘 *Here,*  
- `L2` → channel length = 2 µm  
- `W5` → channel width = 5 µm  
These parameters directly influence the transistor’s **current-driving capability** (I<sub>D</sub> ∝ W/L).

---

## 🖥️ Step 3 — Simulation Output

When the simulation runs successfully, Ngspice outputs the **drain current characteristics** for multiple gate voltages (V<sub>GS</sub>).

### ✅ Example Output Window:
<img width="915" height="680" alt="Ngspice output" src="https://github.com/user-attachments/assets/2c1d8b44-4a66-4c26-8ee1-40b0fd9fa74c" />

---

## 📈 Step 4 — Plot I<sub>D</sub> vs. V<sub>DS</sub>

To visualize how the drain current changes with increasing drain-to-source voltage, use the **plot command** in Ngspice:

```bash
plot -vdd#branch
```

This command plots the **current through the VDD source branch**, which represents **I<sub>D</sub>**, against **V<sub>DS</sub>**.

---

### 🧩 Output Plot

<img width="1422" height="845" alt="Id vs Vds plot" src="https://github.com/user-attachments/assets/1528836f-1060-4f95-9f94-81cb72179516" />

---

## 🔍 Analysis of the I<sub>D</sub>–V<sub>DS</sub> Characteristics

The simulated curve helps identify key MOSFET operating regions:

| Region | Condition | Behavior |
|--------|------------|-----------|
| **Cutoff** | V<sub>GS</sub> < V<sub>T</sub> | Transistor OFF, no conduction |
| **Linear (Triode)** | V<sub>DS</sub> < (V<sub>GS</sub> – V<sub>T</sub>) | Acts as a voltage-controlled resistor |
| **Saturation** | V<sub>DS</sub> ≥ (V<sub>GS</sub> – V<sub>T</sub>) | Channel pinches off; I<sub>D</sub> saturates |

### 🔹 Key Observations:
- Increasing **V<sub>GS</sub>** enhances the channel’s electron density, leading to higher **I<sub>D</sub>**.  
- The slope of the I–V curve reduces as the device enters **saturation**, indicating limited current increase despite higher V<sub>DS</sub>.  
- At **V<sub>DS</sub> = V<sub>GS</sub> – V<sub>T</sub>**, the **pinch-off point** occurs — marking the boundary between linear and saturation regions.

---

## 📏 Step 5 — Extracting Threshold Voltage (V<sub>T</sub>) from Simulation Data

Ngspice allows users to extract the **threshold voltage** by analyzing the point where the **drain current (I<sub>D</sub>)** begins to rise significantly with **V<sub>GS</sub>**.

### 🔧 Method:
1. Perform a DC sweep for **V<sub>GS</sub>** while keeping **V<sub>DS</sub> constant**.
2. Use the `.dc` directive in the SPICE file, e.g.:
   ```spice
   .dc Vgs 0 3 0.01
   ```
3. Run Ngspice and plot:
   ```bash
   plot i(vdd)
   ```
4. The point at which the current curve sharply increases indicates **V<sub>T</sub>** (typically 0.6–0.8 V for NMOS in Sky130).

### 🧮 Example Calculation:
For Sky130 NMOS device:  
If current rises noticeably around **V<sub>GS</sub> ≈ 0.7 V**,  
then → **Threshold Voltage (V<sub>T</sub>) ≈ 0.7 V**.

---

## 📘 Summary

✅ Simulated NMOS **I<sub>D</sub>–V<sub>DS</sub>** behavior using **Ngspice** and **Sky130 PDK**  
✅ Identified operating regions and observed **pinch-off** behavior  
✅ Extracted **threshold voltage (V<sub>T</sub>)** from simulation data  
✅ Strengthened correlation between **theory and practical verification**  

---

> *“Simulation bridges theory and silicon — transforming equations into waveforms and insights.”*  
> — *VSD RISC-V SoC Tapeout Program*
