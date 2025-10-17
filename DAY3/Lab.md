# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ CMOS Switching Threshold & Dynamic Simulations — Theory  

---

### 🧩 **Voltage Transfer Characteristics (VTC) — SPICE Simulation**

The **Voltage Transfer Characteristic (VTC)** of a CMOS inverter describes how the output voltage (**Vout**) changes with input voltage (**Vin**).  
SPICE simulations help determine the **switching threshold**, **noise margins**, and **signal behavior** in different operating regions.

---

### ⚙️ **SPICE Deck Overview**

A **SPICE deck** is the input file used for circuit simulation.  
It defines the device models, connections, and simulation commands.

A SPICE deck typically includes:

- Circuit component descriptions and connectivity  
- Simulation types: `.DC`, `.AC`, `.TRAN`, etc.  
- Output directives like `.PRINT`, `.PLOT`, or `.MEASURE`

<img width="1690" height="727" alt="spice-deck" src="https://github.com/user-attachments/assets/008b8888-2743-46c8-9525-88ee7ce1338f" />

---

### ⚡ **Switching Threshold**

The **switching threshold (Vm)** is the input voltage at which:

\[
V_{in} = V_{out}
\]

- Also called the **trip point** or **metastable point**  
- For symmetric CMOS inverters, it’s ideally around \( V_{dd}/2 \)  
- Defines the inverter’s **logic transition region**

---

### 🧠 **CMOS Inverter Robustness**

A CMOS inverter is robust when its transfer characteristics remain stable under variations in **process, voltage,** and **temperature (PVT)**.

<img width="1765" height="750" alt="inverter-robustness" src="https://github.com/user-attachments/assets/919f1df2-1e5a-467a-b2f1-43d46bbd0231" />  

---

### 🧮 **Current Equations**

The drain currents in NMOS and PMOS during switching are given by:

\[
I_{dSN} = k_n \left[(V_m - V_t)V_{dsatN} - \frac{V_{dsatN}^2}{2}\right]
\]

\[
I_{dSP} = k_p \left[(V_m - V_{dd} - V_t)V_{dsatP} - \frac{V_{dsatP}^2}{2}\right]
\]

---

### ⚖️ **Current Matching Condition**

At equilibrium (trip point), NMOS and PMOS currents are equal:

\[
k_n \left[(V_m - V_t)V_{dsatN} - \frac{V_{dsatN}^2}{2}\right] =
k_p \left[(-V_m + V_{dd} + V_t)V_{dsatP} - \frac{V_{dsatP}^2}{2}\right]
\]

---

### 📈 **Switching Threshold Equation**

\[
V_m = \frac{R \cdot V_{dd}}{1 + R}
\]

\[
R = \frac{k_p \cdot V_{dsatP}}{k_n \cdot V_{dsatN}} =
\frac{\left(\frac{W_P}{L_P}\right)k_p' V_{dsatP}}{\left(\frac{W_N}{L_N}\right)k_n' V_{dsatN}}
\]

---

### 🧠 **Aspect Ratio Design**

To balance rise and fall transitions, the ratio of transistor widths is tuned using:

\[
\frac{\left(\frac{W_P}{L_P}\right)}{\left(\frac{W_N}{L_N}\right)} =
\frac{k_n' V_{dsatN} \left[(V_m - V_t) - \frac{V_{dsatN}}{2}\right]}
{k_p' V_{dsatP} \left[(-V_m + V_{dd} + V_t) - \frac{V_{dsatP}}{2}\right]}
\]

---

### 🌊 **Design Insights from PMOS & NMOS Sizing**

#### 🔹 **Clock Inverter Design**
- \( (W_p/L_p) = 2 \times (W_n/L_n) \)
- Produces nearly equal **rise and fall times**  
- Used in **clock buffers** and **critical timing paths**

---

#### 🔹 **Data Path Inverters**
- Designed with different aspect ratios to optimize **speed** or **power**.  
- Used in **logic gates** and **combinational circuits**.

---

### ⚙️ **Switching Threshold Trends**

\[
(W_p/L_p) = 2\times(W_n/L_n) \text{ or } 3\times(W_n/L_n) \Rightarrow \text{Moderate threshold}
\]

\[
(W_p/L_p) = 4\times(W_n/L_n) \text{ or } 5\times(W_n/L_n) \Rightarrow \text{Lower threshold (faster switching)}
\]

---

### ⚡ **PMOS Width Impact**

- Increasing \( W_p/L_p \) reduces **rise delay**  
- Larger PMOS area delivers more **charging current**  
- Faster output transition and improved performance  

---

### 🧩 **On-Resistance Relationship**

\[
R_{on}(PMOS) \approx 2.5 \times R_{on}(NMOS)
\]

This indicates that PMOS must be **wider** than NMOS for balanced rise and fall times.

---

### 🕒 **Applications in STA and Clock Tree Synthesis**

- **Static Timing Analysis (STA):**  
  Inverters serve as **reference delay cells** for setup/hold timing calculations.  

- **Clock Tree Synthesis (CTS):**  
  Used as **clock buffers** for signal restoration, skew balancing, and delay control.

---

### ✅ **Conclusion**

- The **switching threshold (Vm)** defines the logic transition region.  
- Balanced **Wp/Wn sizing** ensures symmetrical delay and improved noise margins.  
- SPICE simulations validate theoretical analysis of **static CMOS inverter characteristics**.  

---

🧠 **Pro Tip:**  
Adjust **Wp/Wn ratio** and **Vdd** in SPICE simulations to observe how **trip voltage** and **transition slope** change.

---
