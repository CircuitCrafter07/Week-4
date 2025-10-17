# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ Velocity Saturation and CMOS Inverter VTC  

---

### 🌶️ **SPICE Simulation for Velocity Saturation and Lower Technology Nodes**

<img width="2602" height="1730" alt="velocity-saturation" src="https://github.com/user-attachments/assets/97ce8575-fd6a-4071-b149-a3697ba50085" />  

This simulation demonstrates **velocity saturation** in short-channel MOSFETs and explores **CMOS inverter voltage transfer characteristics (VTC)**.  

---

### ⚙️ **MOSFET Operating Regions**

#### **1️⃣ Linear Region**
- MOSFET behaves as a **voltage-controlled resistor**.  
- **Condition:**  
  \[
  V_{DS} < V_{GS} - V_T
  \]
- **Current Equation:**  
  \[
  I_D = k_n \left[(V_{GS} - V_T)V_{DS} - \frac{V_{DS}^2}{2}\right]
  \]

---

#### **2️⃣ Saturation Region**
- MOSFET acts as a **current source**.  
- **Condition:**  
  \[
  V_{DS} \geq V_{GS} - V_T
  \]
- **Current Equation:**  
  \[
  I_D = \frac{k_n}{2} \frac{W}{L}(V_{GS} - V_T)^2 [1 + \lambda V_{DS}]
  \]

---

### 🧮 **Quadratic Dependence**

When \( V_{GS} \) exceeds the threshold voltage \( V_T \), an **inversion channel** forms under the gate.  
The current follows a **square-law dependence**:

\[
I_D \propto (V_{GS} - V_T)^2
\]

---

### ⚡ **Velocity Saturation**

At **deep submicron** technology nodes, the **carrier velocity** no longer increases linearly with electric field due to high field effects — a phenomenon called **velocity saturation**.

- **Effect:** Limits \( I_D \) below square-law prediction.  
- **Modified Saturation Current Equation:**

\[
I_{Dsat} = W C_{ox} (V_{GS} - V_T) v_{sat}
\]

where \( v_{sat} \) = carrier saturation velocity.  

---

### 🧩 **CMOS Inverter — Voltage Transfer Characteristics (VTC)**

The **CMOS inverter** consists of an **NMOS pull-down** and **PMOS pull-up** network.  
The **VTC** curve represents how output voltage \( V_{out} \) changes with input voltage \( V_{in} \).

---

#### 🔹 **NMOS as a Switch**
- **Cutoff:** \( V_{GS} < V_T \) → NMOS OFF → open switch (no current flow).  
- **Linear/Triode:** \( V_{GS} > V_T \), \( V_{DS} \) small → NMOS ON → low resistance conduction.  
Used in both **digital logic** and **analog switching**.

<img width="1342" height="585" alt="nmos-switch" src="https://github.com/user-attachments/assets/bcfadfa2-ff3f-4c10-9540-9a12d4259c5f" />

---

### ⚙️ **Standard MOS Parameters**

| Symbol | Parameter | Description |
|:-------|:-----------|:-------------|
| \( V_T \) | Threshold Voltage | Minimum gate voltage required for inversion |
| \( V_{GS} \) | Gate–Source Voltage | Controls channel formation and current flow |
| \( V_{DS} \) | Drain–Source Voltage | Determines operating region (Triode / Saturation) |
| \( I_D \) | Drain Current | Output current dependent on \( V_{GS} \) and \( V_{DS} \) |

<img width="1765" height="685" alt="mos-parameters" src="https://github.com/user-attachments/assets/403e35d2-9c9e-48c7-a6dc-9ea5ca1211b3" />  

---

### 🧩 **Steps to Derive CMOS VTC**

#### 🧠 **s1 — Convert PMOS Gate–Source Voltage to Input \( V_{in} \)**

For PMOS:  
\[
V_{SG} = V_{DD} - V_{in}
\]
- PMOS **ON:** \( V_{SG} > |V_{TP}| \Rightarrow V_{in} < V_{DD} - |V_{TP}| \)  
- PMOS **OFF:** \( V_{in} > V_{DD} - |V_{TP}| \)

<img width="1187" height="970" alt="pmos-vsg" src="https://github.com/user-attachments/assets/108ed63d-0af0-4b19-b573-fdd25c0f193f" />  

---

#### 🧠 **s2 — Convert PMOS Drain–Source Voltage to Output \( V_{out} \)**

For PMOS:  
\[
V_{SD} = V_{DD} - V_{out}
\]
- **Linear Region:** \( V_{SD} < V_{SG} - |V_{TP}| \)  
- **Saturation:** \( V_{SD} \geq V_{SG} - |V_{TP}| \)

---

#### 🧠 **s3 — Convert NMOS Drain–Source Voltage to Output \( V_{out} \)**

For NMOS:  
\[
V_{DS} = V_{out}
\]
- **Linear Region:** \( V_{DS} < V_{GS} - V_{TN} \)  
- **Saturation:** \( V_{DS} \geq V_{GS} - V_{TN} \)

<img width="1775" height="600" alt="nmos-vds" src="https://github.com/user-attachments/assets/c8fb15fa-4a12-455d-9dbc-4ba036aad5a4" />  

---

#### 🧩 **s4 — Merge Load Curves and Plot VTC**

- Plot **I–V curves** for both NMOS and PMOS transistors.  
- Find **intersections** where \( I_{DN} = I_{DP} \).  
- Extract \( (V_{in}, V_{out}) \) pairs from intersection points.  
- Draw the **VTC curve**, clearly showing **logic transition regions**.

<img width="1800" height="1000" alt="cmos-vtc" src="https://github.com/user-attachments/assets/b789b099-a8ca-4697-bcc5-f80a4aae6096" />  

---

### ✅ **Conclusion**

- **Velocity saturation** limits MOSFET drive current in **deep-submicron technologies**.  
- **CMOS inverter VTC** analysis helps understand **switching thresholds** and **noise margins**.  
- SPICE simulations confirm theoretical behavior for both **NMOS and PMOS** under velocity saturation effects.  

---

🧠 **Pro Tip:**  
Experiment with different **W/L ratios** and **supply voltages** in SPICE to observe how **VTC shape** and **gain** change with device scaling.  

---
