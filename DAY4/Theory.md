# 🌍 RISC-V SoC Tapeout Program — VSD
## ⚙️ CMOS Noise Margin & Robustness Evaluation

---

### 🧠 Overview
In CMOS digital design, **noise margin** is a key indicator of circuit robustness — it defines how resistant a logic gate is to unwanted electrical noise or voltage variations.  
This document evaluates the **noise margin robustness** of a CMOS inverter, exploring both **theoretical** and **practical** behaviors under varying transistor ratios.

---

## ⚡ CMOS Inverter: Ideal vs. Practical Behavior

### 🧩 Ideal Input–Output Characteristics

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/3ce81861-b05d-4d44-b75c-6ccc0cc21903" alt="Ideal CMOS inverter curve">
</p>

The **ideal inverter** sharply transitions between logic `0` and logic `1`.  
There is no undefined region, and the output switches instantaneously.

---

### ⚙️ Realistic Input–Output Characteristics (Finite Slope)

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/0d1a17c6-bdc0-45ad-800a-fc96dbdf4d31" alt="Real CMOS inverter finite slope">
</p>

In practice, the transition between logic levels is **gradual**, producing a finite slope that introduces **uncertainty regions** and defines **noise margins**.

---

## 📘 Key Terminology

| Symbol | Description | Typical Range | Logical Meaning |
|:--:|:--|:--|:--|
| **V<sub>IL</sub>** | Input Low Voltage | ≈ V<sub>DD</sub>/4 | Input ≤ V<sub>IL</sub> → Logic ‘0’ |
| **V<sub>IH</sub>** | Input High Voltage | ≈ 3V<sub>DD</sub>/4 | Input ≥ V<sub>IH</sub> → Logic ‘1’ |
| **V<sub>OL</sub>** | Output Low Voltage | 0 ≤ V<sub>OL</sub> < V<sub>IL</sub> | Output → Logic ‘0’ |
| **V<sub>OH</sub>** | Output High Voltage | V<sub>IH</sub> < V<sub>OH</sub> ≤ V<sub>DD</sub> | Output → Logic ‘1’ |

---

## 🧮 Noise Margin Analysis

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/203a0ff6-5f27-4c7b-877c-1547d8c22981" alt="Noise margin diagram">
</p>

### 🔹 Definitions

- **NM<sub>H</sub> (High Noise Margin):**  
  The maximum noise voltage tolerated when the output is at logic ‘1’.
  \[
  NM_H = V_{OH} - V_{IH}
  \]

- **NM<sub>L</sub> (Low Noise Margin):**  
  The maximum noise voltage tolerated when the output is at logic ‘0’.
  \[
  NM_L = V_{IL} - V_{OL}
  \]

- **Undefined Region:**  
  Voltage levels between V<sub>IL</sub> and V<sub>IH</sub> where the logic state cannot be clearly determined.

---

## 🔍 Noise Behavior under Disturbances

### 📈 Noise-Induced Bump Characteristics

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/7082a473-0e39-4e47-b8bb-daee1f02a067" alt="Noise bump graph">
</p>

### ⚠️ Noise Margin Behavior Categories

| Type | Voltage Range | Interpretation |
|:--|:--|:--|
| **Safe Glitch** | Bump between V<sub>OL</sub> and V<sub>IL</sub> | Still read as Logic ‘0’ |
| **Potentially Hazardous** | Bump in undefined region (V<sub>IL</sub>–V<sub>IH</sub>) | Unclear logic level |
| **Critical Glitch** | Bump between V<sub>IH</sub> and V<sub>OH</sub> | Interpreted as Logic ‘1’ — may cause logic errors |

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/36abf805-027b-43a7-b40c-69516e620520" alt="Noise bump classification">
</p>

---

## 🔧 Design Insights and Observations

| Ratio (Wp/Lp : Wn/Ln) | Effect on NM<sub>H</sub> | Effect on NM<sub>L</sub> | Remarks |
|:--|:--|:--|:--|
| **2 : 1** | Rise in NM<sub>H</sub> | Stable | PMOS holds charge effectively |
| **4 : 1** | Drop in NM<sub>L</sub> | Slight degradation | NMOS becomes weaker |
| **5 : 1** | NM<sub>H</sub> stabilizes | Stable | Optimal balance reached |

### 🧾 Overall Summary
- NM<sub>L</sub> remains **mostly stable** across ratios.  
- NM<sub>H</sub> **increases by ≈120 mV**, enhancing inverter robustness.  
- The **ratio tuning** between PMOS and NMOS significantly affects inverter reliability.  

---

## 🧭 Conclusion
A well-balanced CMOS inverter design ensures **high noise immunity** and **stable logic transitions**.  
By tuning the width-to-length ratio (Wp/Lp : Wn/Ln), designers can optimize for robustness against noise and ensure reliable operation across process variations and temperature ranges.

---

> 📘 **Note:** This study forms part of the RISC-V SoC Tapeout Program (VSD) and contributes to understanding transistor-level design robustness in CMOS circuits.
