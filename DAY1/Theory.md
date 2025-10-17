# ⚙️ RISC-V SoC Tapeout Program — VSD Journey  
### 📘 Module: Basics of NMOS Drain Current (I<sub>D</sub>) vs. Drain-to-Source Voltage (V<sub>DS</sub>)

> A detailed exploration of NMOS transistor operation, current–voltage characteristics, and SPICE simulations — forming the foundation of CMOS circuit behavior and device-level understanding.

---

## ⚡ Introduction to Circuit Design & SPICE Simulations

### 🧠 Why Do We Need SPICE Simulations?
**SPICE (Simulation Program with Integrated Circuit Emphasis)** is essential for **analyzing and validating circuit behavior** before physical fabrication. It allows engineers to:
- Predict **voltage, current, and power** characteristics accurately.
- Test **analog, digital, and mixed-signal circuits**.
- Detect **design flaws** early and optimize device performance.
- Reduce the **cost and time** of prototyping through virtual analysis.

---

## ⚛ NMOS Device Structure

**n-Channel Metal–Oxide–Semiconductor (NMOS)** transistors form the building blocks of digital logic.

**Key Components:**
1. **Source & Drain** → Heavily doped *n+* regions enabling electron flow.
2. **Gate Electrode** → A control terminal made of **polycrystalline silicon (Poly-Si)** that modulates channel formation.
3. **Gate Oxide (SiO₂)** → A thin insulating layer separating gate and substrate, enabling electric-field control without DC conduction.
4. **Body (B)** → A *p-type* substrate acting as the foundation; affects **threshold voltage (V<sub>T</sub>)**.

<br>
<img width="3662" height="1453" alt="NMOS structure" src="https://github.com/user-attachments/assets/e1dc65f1-f637-4230-8f70-9f466bdd5edb" />

---

## ⚙️ Working Principle of NMOS

1. Initially, when **V<sub>GS</sub> = 0**, no channel forms → no current flows.  
2. The **p–n junctions** between bulk-source and bulk-drain are reverse-biased → device is OFF.  
3. Applying **positive V<sub>GS</sub>** attracts electrons under the gate → forms an **inversion layer**.  
4. Once **V<sub>GS</sub> ≥ V<sub>T</sub>**, a conducting **n-channel** forms.  
5. Increasing V<sub>GS</sub> enhances channel conductivity and current.  
6. Electrons flow from **Source → Drain**, controlled by **V<sub>GS</sub>**.

![Working NMOS](https://github.com/user-attachments/assets/fc3b4477-4da4-4077-8856-bed78b2d588f)

---

## 🧩 Threshold Voltage & Body Effect

When a **positive substrate bias (V<sub>SB</sub>)** is applied, the depletion region widens, requiring a higher gate voltage to form strong inversion — known as the **Body Effect**.

📐 **Threshold Voltage Equation:**

$$
V_t = V_{t0} + \gamma \left( \sqrt{|{-2\phi_F + V_{SB}}|} - \sqrt{|{-2\phi_F}|} \right)
$$

<img width="1772" height="912" alt="Threshold voltage diagram" src="https://github.com/user-attachments/assets/e8d51a86-8a7b-4854-9266-20ef361b8a4c" />

---

## 🔍 Important Terms

### 🔸 Strong Inversion
Occurs when **V<sub>GS</sub> > V<sub>T</sub>**, forming a well-defined **n-channel** under the oxide that allows significant conduction.

### 🔸 Subthreshold Conduction
A small **leakage current** flows even when **V<sub>GS</sub> < V<sub>T</sub>**, due to minority carrier diffusion — increases exponentially as V<sub>GS</sub> approaches threshold.

---

## 🧮 NMOS Operation Regions

### 🟢 **Triode (Resistive) Region**
NMOS acts as a **voltage-controlled resistor**.  
For **small V<sub>DS</sub>**:

$$
I_D \approx \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th}) V_{DS}
$$

**Effective Resistance:**

$$
R_{on} = \frac{1}{\mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})}
$$

---

### 🔵 **Saturation (Active) Region**
When the channel is **pinched off** near the drain:

$$
V_{DS} = V_{GS} - V_{th}
$$

At this point, current saturates:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2
$$

<img width="1672" height="887" alt="Saturation region" src="https://github.com/user-attachments/assets/41e6c87f-22f0-425f-838f-12a6d427a0b4" />

---

## 🌊 Drift Current Theory

Drift current represents the **motion of charge carriers** under an applied electric field.

At any point `x` along the channel:

$$
I_D = -v_n(x) \cdot Q_i(x) \cdot W
$$

And **carrier drift velocity**:

$$
v_d = \mu E
$$

<img width="637" height="922" alt="Drain current model" src="https://github.com/user-attachments/assets/050a70cc-4e19-4975-a2e4-9d956de0c41d" />

---

## 🧨 SPICE Simulation Overview

**SPICE (Simulation Program with Integrated Circuit Emphasis)** is a standard tool for analyzing circuit behavior through mathematical modeling.

<img width="1740" height="900" alt="SPICE simulation flow" src="https://github.com/user-attachments/assets/7b85e4be-2f63-4ceb-a994-bd513d441bc3" />

### Key Parameters:
| Symbol | Parameter | Description |
|---------|------------|-------------|
| V<sub>t0</sub> | Threshold voltage | Device turn-on point |
| k<sub>n</sub> | Transconductance constant | Current-driving capability |
| γ | Body effect coefficient | Threshold variation with body bias |
| μ<sub>n</sub> | Electron mobility | Carrier speed in channel |
| C<sub>ox</sub> | Oxide capacitance per unit area | Determines gate control strength |
| W/L | Width-to-length ratio | Impacts current capacity |
| λ | Channel-length modulation | Slope of I–V curve in saturation |

---

### 🧰 Example SPICE Netlist

Below is the SPICE netlist used for NMOS characteristic simulation:

```bash
* NMOS Characteristic Simulation
M1 vdd n1 0 0 nmos W=1.8u L=1.2u
R1 in n1 55
Vdd vdd 0 DC 2.5  
Vin in 0 DC 2.5

.MODEL nmos NMOS (VTO=0.7 KP=120U GAMMA=0.5)
.OP
.DC Vin 0 2.5 0.01
.PRINT DC V(n1) I(R1)
.END
EOF
