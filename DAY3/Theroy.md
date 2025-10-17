# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ CMOS Switching Threshold & Dynamic Simulations  

---

### 🧩 **Voltage Transfer Characteristics — SPICE Simulation**

#### ⚙️ What Is a SPICE Deck?

A **SPICE deck** defines the circuit and instructions for simulation. It typically includes:

- Circuit components and their interconnections  
- Type of analysis to perform (DC, AC, or transient)  
- Output commands (e.g., `.PRINT`, `.PLOT`, `.MEASURE`)  

<img width="1690" height="727" alt="spice-deck" src="https://github.com/user-attachments/assets/008b8888-2743-46c8-9525-88ee7ce1338f" />

---

### ⚙️ **Switching Threshold**

The **switching threshold** (trip point) is where the input and output voltages are equal:  
\[
V_{in} = V_{out}
\]

- Defines the transition point between logic ‘0’ and ‘1’.  
- Ideally set at \( V_{dd}/2 \) for **symmetrical switching**.  
- Determines the inverter’s **noise margin** and **robustness**.

---

### ⚡ **CMOS Inverter Robustness**

<img width="1765" height="750" alt="inverter-robustness" src="https://github.com/user-attachments/assets/919f1df2-1e5a-467a-b2f1-43d46bbd0231" />  

Robust CMOS design ensures stable switching even with variations in threshold voltage, temperature, or process.

---

### 🧮 **Current Equations**

\[
I_{dSN} = k_n \left[ (V_m - V_t) \cdot V_{dsatN} - \frac{V_{dsatN}^2}{2} \right]
\]

\[
I_{dSP} = k_p \left[ (V_m - V_{dd} - V_t) \cdot V_{dsatP} - \frac{V_{dsatP}^2}{2} \right]
\]

---

### ⚖️ **Current Matching Condition**

For balanced operation:

\[
k_n \left[ (V_m - V_t) \cdot V_{dsatN} - \frac{V_{dsatN}^2}{2} \right] =
k_p \left[ (-V_m + V_{dd} + V_t) \cdot V_{dsatP} - \frac{V_{dsatP}^2}{2} \right]
\]

---

### 📈 **Switching Threshold Equation**

\[
V_m = \frac{R \cdot V_{dd}}{1 + R}
\]

\[
R = \frac{k_p \cdot V_{dsatP}}{k_n \cdot V_{dsatN}} =
\frac{\left( \frac{W_P}{L_P} \right) k_p' V_{dsatP}}{\left( \frac{W_N}{L_N} \right) k_n' V_{dsatN}}
\]

---

### 🧠 **Aspect Ratio Design**

\[
\frac{\left( \frac{W_P}{L_P} \right)}{\left( \frac{W_N}{L_N} \right)} =
\frac{k_n' \cdot V_{dsatN} \cdot \left[(V_m - V_t) - \frac{V_{dsatN}}{2}\right]}
{k_p' \cdot V_{dsatP} \cdot \left[(-V_m + V_{dd} + V_t) - \frac{V_{dsatP}}{2}\right]}
\]

---

### 🌊 **Conclusions on PMOS & NMOS Sizing**

#### 🔹 **Optimal Clock Inverter Design**
- \( (W_p/L_p) = 2 \times (W_n/L_n) \)
- Produces balanced **rise/fall delays**  
- Used in **clock buffers** and **timing-critical paths**

---

#### 🔹 **Data Path Inverters**
- Use alternative sizing ratios for **signal propagation** or **power optimization**.  
- Commonly found in **data logic chains**.

---

### ⚙️ **Switching Threshold Characteristics**

\[
(W_p/L_p) = 2\times(W_n/L_n) \text{ or } 3\times(W_n/L_n) \Rightarrow \text{Small switching threshold}
\]

\[
(W_p/L_p) = 4\times(W_n/L_n) \text{ or } 5\times(W_n/L_n) \Rightarrow \text{Very small switching threshold}
\]

---

### ⚡ **PMOS Width Impact**

- Increasing \( W_p/L_p \) → reduces **rise delay**  
- Larger PMOS area allows more **charging current**  
- Improves **output capacitor charging** → faster transitions

---

### 🧩 **On-Resistance Relation**

\[
R_{on}(PMOS) \approx 2.5 \times R_{on}(NMOS)
\]

---

### 🕒 **Applications in STA & Clock Tree Design**

- **Static Timing Analysis (STA):**  
  CMOS inverters serve as **reference delay cells** for modeling rise/fall arcs and calculating setup/hold times.  

- **Clock Tree Synthesis (CTS):**  
  Used as **clock buffers** to regenerate signals, control skew, and maintain balanced timing across the chip.  

---

🧠 **Pro Tip:**  
Fine-tuning the **Wp/Wn ratio** can optimize inverter delay, reduce static power, and improve noise margins.

---
