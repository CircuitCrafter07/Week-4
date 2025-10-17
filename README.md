# Week-4
# ⚙️ RISC-V SoC Tapeout Program — VSD Journey  
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
![Status](https://img.shields.io/badge/Progress-Completed-success)
![Platform](https://img.shields.io/badge/Platform-OpenSource%20EDA-lightgrey)
![Focus](https://img.shields.io/badge/Focus-RISC--V%20SoC%20Design-orange)

> A detailed documentation of my learning experience through the **VLSI System Design (VSD)** RISC-V SoC Design & Tapeout Program — focusing on transistor fundamentals, CMOS design, and system robustness for silicon-proven SoC implementation.

---

## 🧭 Table of Contents
- [Day 1 – Fundamentals of NMOS Characteristics](#-day-1--fundamentals-of-nmos-characteristics)
- [Day 2 – Velocity Saturation & CMOS Inverter VTC](#-day-2--velocity-saturation--cmos-inverter-vtc)
- [Day 3 – CMOS Switching Threshold & Dynamic Simulation](#-day-3--cmos-switching-threshold--dynamic-simulation)
- [Day 4 – CMOS Noise Margin & Robustness](#-day-4--cmos-noise-margin--robustness)
- [Day 5 – Power Supply & Process Variation Robustness](#-day-5--power-supply--process-variation-robustness)
- [Key Takeaways](#-key-takeaways)

---

## 🧩 **Day 1 – Fundamentals of NMOS Characteristics**

**Topic:** *Drain Current (I<sub>D</sub>) vs. Drain-to-Source Voltage (V<sub>DS</sub>)*  

- Explored **I–V characteristics** of an NMOS transistor.  
- Understood **operation regions** — *cutoff*, *linear*, and *saturation*.  
- Examined how **gate voltage (V<sub>GS</sub>)** affects channel formation and conduction.  
- Visualized transitions between regions through characteristic curves.  

🧠 *Key Insight:* Channel formation depends strongly on the gate voltage; higher V<sub>GS</sub> results in stronger inversion and higher current flow.

---

## ⚡ **Day 2 – Velocity Saturation & CMOS Inverter VTC**

**Topic:** *Short-Channel Effects and Voltage Transfer Characteristics*  

- Studied **carrier velocity saturation** in deep-submicron NMOS transistors.  
- Constructed and analyzed the **Voltage Transfer Characteristic (VTC)** of a CMOS inverter.  
- Investigated **logic levels**, **transition regions**, and **switching points**.  

📊 *Outcome:* Gained insight into how short-channel effects impact drain current and inverter transfer behavior.

---

## 🔁 **Day 3 – CMOS Switching Threshold & Dynamic Simulation**

**Topic:** *Transient Response and Delay Analysis*  

- Determined the **switching threshold voltage (V<sub>M</sub>)** of a CMOS inverter.  
- Performed **transient simulations** to observe **rise/fall times** and **propagation delays**.  
- Studied how **transistor sizing** and **load capacitance** affect circuit speed.  
- Correlated results with theoretical delay models.  

⏱️ *Observation:* Optimized transistor ratios improve switching symmetry and reduce delay.

---

## 🧠 **Day 4 – CMOS Noise Margin & Robustness**

**Topic:** *Static Noise Margin (SNM) Evaluation*  

- Calculated **Noise Margins (NM<sub>H</sub> and NM<sub>L</sub>)** from the inverter’s VTC curve.  
- Evaluated **logic robustness** and **noise immunity**.  
- Discussed **design considerations** for stable operation under external disturbances.  

🔒 *Conclusion:* Higher SNM ensures better immunity against power supply noise and cross-talk in digital systems.

---

## 🔋 **Day 5 – Power Supply & Process Variation Robustness**

**Topic:** *Reliability under Real-World Conditions*  

- Investigated the impact of **V<sub>DD</sub> variation** and **process mismatches** on inverter behavior.  
- Conducted **corner analysis** for typical, slow, and fast process corners.  
- Examined **design margins** ensuring performance stability under PVT (Process, Voltage, Temperature) variations.  

⚙️ *Key Learning:* Robust design requires accounting for parameter variability early in the SoC design flow.

---

## 🧠 **Key Takeaways**

✅ Built a strong foundation in **device-level behavior** and **CMOS design principles**.  
✅ Understood **timing**, **noise**, and **reliability** aspects critical to tapeout success.  
✅ Gained hands-on experience using **open-source EDA tools** for simulation and analysis.  
✅ Prepared for **advanced RISC-V SoC design, verification, and physical implementation**.

---

## 🧰 Tools & Technologies
| Tool / Concept | Purpose |
|----------------|----------|
| **ngspice / eSim** | Transistor-level simulation |
| **Sky130 PDK** | Open-source CMOS process |
| **VTC & Transient Analysis** | Timing and switching evaluation |
| **Corner Analysis** | Robustness validation |

---

### 👨‍💻 Author
**Harsh Shah**  
RISC-V SoC Design Enthusiast | Aspiring VLSI Engineer  
🔗 [LinkedIn](https://www.linkedin.com/in/harsh-shah-51a10521b/)  |  📧 harsh2004shah@gmail.com  

---

> *“Understanding transistor-level behavior is the first step toward reliable SoC design.”*  
> — *VSD Tapeout Program*
