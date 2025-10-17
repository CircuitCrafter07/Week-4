# 🌍 RISC-V SoC Tapeout Program — VSD
## ⚙️ CMOS Noise Margin Robustness — Simulation Lab

---

### 🧠 Objective

This lab focuses on **evaluating the CMOS inverter’s noise margin** through SPICE simulations.  
We will analyze how the inverter behaves under noise conditions and how the output transitions respond to varying input voltages.

---

## 🧪 1. Simulation Overview

### 💻 Tool Used
**Software:** NGSpice  
**Purpose:** Analog circuit simulation for verifying inverter voltage transfer characteristics (VTC) and determining noise margins.

---

### ⚙️ Command: Running the Simulation

To simulate the inverter circuit defined in the file `day4_inv_noisemargin_wp1_wn036.spice`, run the following command:

```bash
$ ngspice day4_inv_noisemargin_wp1_wn036.spice
```

This command loads the SPICE netlist and executes the defined transient or DC sweep analysis to obtain the inverter’s input–output characteristics.

---

### 📊 2. Simulation Output

#### 🖼️ Output Graph (Initial Simulation)

<p align="center">
  <img width="800" src="https://github.com/CircuitCrafter07/Week-4/blob/main/DAY4/Screenshot%20from%202025-10-17%2011-50-31.png">
</p>

This plot represents the **output voltage vs. input voltage**, showcasing the CMOS inverter’s transition behavior.

---

## 📈 3. Visualizing the Inverter Transfer Curve

Once inside the NGSpice terminal, plot the inverter’s output (`out`) against its input (`in`) to visualize the **Voltage Transfer Characteristic (VTC)**:

```bash
$ plot out vs in
```

This command plots the transfer characteristic curve — a key step in determining the **noise margins (NM<sub>H</sub> and NM<sub>L</sub>)** and observing the slope of the transition region.

---

#### 🧩 Output Plot

<p align="center">
  <img width="800" src="https://github.com/CircuitCrafter07/Week-4/blob/main/DAY4/Screenshot%20from%202025-10-17%2011-50-24.png">
</p>

The curve demonstrates:
- The **steep transition region** between logic `0` and logic `1`.
- The **flat regions** corresponding to stable logic states.
- The **undefined region**, where voltage levels can be interpreted ambiguously.

---

## 📘 4. Interpretation & Analysis

- The **flat regions** on both sides of the curve indicate **strong logic levels** (`0` and `1`).
- The **slope of the transition region** is directly linked to the inverter’s **gain** and **noise immunity**.
- By analyzing the points:
  - V<sub>IL</sub> and V<sub>IH</sub> — we determine **input thresholds**.
  - V<sub>OL</sub> and V<sub>OH</sub> — we obtain **output voltage levels**.
- Using these, **Noise Margins** are calculated:
  \[
  NM_H = V_{OH} - V_{IH} \quad \text{and} \quad NM_L = V_{IL} - V_{OL}
  \]
- The wider the noise margins, the **more robust the inverter** is to voltage noise and switching disturbances.

---

## 🧭 5. Conclusion

This experiment successfully demonstrates:
- The **Voltage Transfer Characteristic (VTC)** of a CMOS inverter.
- Identification of **noise margin regions**.
- The use of **NGSpice** to evaluate circuit stability and signal integrity.

By examining the **input-output voltage curve**, we verify that the **CMOS inverter design exhibits stable noise margins**, validating its robustness for digital applications.

---

> 🧾 **Note:**  
> This lab is part of the *RISC-V SoC Tapeout Program (VSD)*, focusing on foundational CMOS circuit design and robustness verification at the transistor level.
