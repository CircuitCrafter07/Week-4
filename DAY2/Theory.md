# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ Fundamentals of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)

---

### ✨ **Introduction to Circuit Design & SPICE Simulations**

#### 🔹 Why Do We Need SPICE Simulations?

**SPICE (Simulation Program with Integrated Circuit Emphasis)** is an essential tool for **designing and analyzing electronic circuits** before physical implementation.  
It allows engineers to:

- Predict real-world circuit behavior  
- Identify design flaws early  
- Optimize device performance  
- Avoid costly and time-consuming prototyping  

SPICE supports **analog, digital, and mixed-signal** simulations — enabling accurate prediction of voltage, current, power, and timing characteristics under various conditions.

---

### ⚛️ **NMOS Device Overview**

**n-Channel Metal-Oxide Semiconductor (NMOS)** is a type of MOSFET where current is carried by **electrons**.  

#### 📘 Structure and Key Components
1. **Source (S) & Drain (D):**  
   Two heavily doped *n+ regions* that enable electron flow when the device is ON.

2. **Gate (G):**  
   The control terminal — typically made of **polycrystalline silicon (Poly-Si)** — where input voltage is applied.

3. **Gate Oxide (SiO₂):**  
   A thin insulating layer separating gate and substrate. It forms the **electric field** that controls the channel without allowing DC conduction.

4. **Body (B):**  
   The **p-type substrate**, acting as the foundation and influencing the **threshold voltage (Vₜ)**.

<br>

![NMOS Structure](https://github.com/user-attachments/assets/e1dc65f1-f637-4230-8f70-9f466bdd5edb)

---

### ⚙️ **Working Principle of NMOS**

1. At **VGS = 0**, all terminals are grounded — no current flows.  
2. The p-type substrate forms **reverse-biased p–n junctions** (body-to-source and body-to-drain).  
3. The **source–drain resistance** is extremely high.  
4. When a **positive VGS** is applied:  
   - Electrons accumulate under the gate.  
   - A conducting **n-channel** forms (known as **inversion**).  
5. The **threshold voltage (Vt)** is the gate voltage at which this strong inversion occurs.  
6. Increasing VGS beyond Vt → enhances conductivity.  
7. Electrons flow from **source → drain**, and the **gate voltage controls current magnitude**.

![NMOS Channel Formation](https://github.com/user-attachments/assets/fc3b4477-4da4-4077-8856-bed78b2d588f)

---

### ⚡ **Threshold Voltage & Body Effect**

Applying a **positive body bias (VSB > 0)** widens the depletion region, requiring a higher gate voltage to achieve inversion — this increases **Vt** (body effect).

![Body Effect](https://github.com/user-attachments/assets/12fe3143-1d80-4a28-b343-d2fca1e98e98)

#### 🧮 Threshold Voltage Equation

\[
V_t = V_{t0} + \gamma \left( \sqrt{|{-2\phi_F + V_{SB}}|} - \sqrt{|{-2\phi_F}|} \right)
\]

---

### 📘 **Important Concepts**

#### 🔹 Strong Inversion  
Occurs when **VGS > Vt** and a dense **electron channel** forms, allowing substantial current flow.

#### 🔹 Subthreshold Conduction  
When **VGS < Vt**, a small leakage current flows due to **minority carrier diffusion** — increasing exponentially as VGS approaches Vt.

---

### ⚙️ **Regions of Operation**

#### 🧩 NMOS in Triode (Linear) Region

When \( V_{DS} \ll (V_{GS} - V_{th}) \), the transistor behaves as a **voltage-controlled resistor**.

\[
I_D = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th}) V_{DS}
\]

#### ⚙️ Effective On-Resistance

\[
R_{on} = \frac{1}{\mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})}
\]

---

### 🌊 **Drift Current Theory**

**Drift current** is caused by the movement of charge carriers under an **electric field**.

- Channel current at any point \( x \):  
  \[
  I_D = -v_n(x) \cdot Q_i(x) \cdot W
  \]
- Electron drift velocity:  
  \[
  v_d = \mu E
  \]

![Drain Current Model](https://github.com/user-attachments/assets/050a70cc-4e19-4975-a2e4-9d956de0c41d)

---

### ⚡ **Saturation (Pinch-Off) Region**

At **pinch-off**, the channel narrows near the drain and current saturates.  
This marks the transition from **linear** to **saturation** operation.

\[
V_{DS(sat)} = V_{GS} - V_{th}
\]

![Pinch-Off](https://github.com/user-attachments/assets/41e6c87f-22f0-425f-838f-12a6d427a0b4)

---

### 🧨 **SPICE Simulations**

SPICE is used to **numerically solve** circuit equations and produce characteristic **I–V curves** and **waveforms** based on device parameters.

![SPICE Overview](https://github.com/user-attachments/assets/7b85e4be-2f63-4ceb-a994-bd513d441bc3)

#### 🧩 Common NMOS SPICE Parameters
| Parameter | Description |
|------------|-------------|
| VTO | Threshold Voltage |
| KP | Transconductance Parameter |
| GAMMA | Body Effect Coefficient |
| μn | Electron Mobility |
| Cox | Oxide Capacitance per Unit Area |
| W/L | Width-to-Length Ratio |
| λ | Channel Length Modulation |

---

### 💻 Example: SPICE Netlist

SPICE netlists describe the circuit elements and connections for simulation.

![SPICE Netlist Diagram](https://github.com/user-attachments/assets/4fc554e4-fb2b-4eba-963f-4a7fdfa938b1)

```bash
* Generated SPICE Netlist for NMOS Circuit

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
