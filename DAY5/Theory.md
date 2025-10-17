# ⚙️ RISC-V SoC Tapeout Program — VSD  
## 🪶 CMOS Power Supply & Device Variation Robustness — Lab Evaluation  

---

### 🧪 **1. Power Supply Variation**

#### 🧰 **Simulation Setup**
Run the following command to simulate inverter performance under **supply voltage variation**:

```bash
$ ngspice day5_inv_supplyvariation_Wp1_Wn036.spice
```

This experiment investigates the impact of **supply voltage (V<sub>DD</sub>)** changes on:
- Inverter transfer characteristics  
- Switching delay  
- Noise margins  
- Power efficiency  

#### 📸 **Waveform Results**
![5 -3](https://github.com/user-attachments/assets/9902e77e-99b2-41c8-85f2-3396a0e6ab4c)  
![5 -4](https://github.com/user-attachments/assets/b985560f-fadc-44df-bb26-d7e6047360db)

#### 📊 **Observations**
| Parameter | Behavior |
|------------|-----------|
| **Switching Threshold** | Shifts lower as supply voltage decreases |
| **Delay** | Increases at lower V<sub>DD</sub> due to weaker drive current |
| **Energy Consumption** | Reduces significantly at lower voltages |
| **Logic Robustness** | Slightly decreases as V<sub>DD</sub> approaches threshold voltage levels |

**Conclusion:**  
Reduced supply voltage enhances power efficiency but at the cost of speed and noise margin stability.

---

### ⚙️ **2. Device Variation**

#### 🧰 **Simulation Setup**
Run the following command to evaluate inverter behavior under **device geometry variation** (Wp/Wn ratio):

```bash
$ ngspice day5_inv_devicevariation_wp7_wn042.spice
```

This test studies how changing **transistor widths** affects:
- Voltage transfer characteristics (VTC)  
- Switching thresholds  
- Noise margins and signal stability  

#### 📸 **Waveform Results**
![5 -1](https://github.com/user-attachments/assets/f65f1741-498e-4a3f-ae23-c6011e6205ce)

To view the transfer characteristic, use:
```bash
$ plot out vs in
```

**Output:**
![5 -2](https://github.com/user-attachments/assets/b40c62ce-eb0a-4d49-97ba-25cc639f7497)

#### 📊 **Observations**
| Parameter | Effect of Device Variation |
|------------|----------------------------|
| **Threshold Voltage (V<sub>M</sub>)** | Shifts depending on PMOS/NMOS width ratio |
| **Noise Margins** | Improve when device sizing is balanced |
| **Switching Speed** | Faster with stronger NMOS or PMOS transistors |
| **Power Consumption** | Increases slightly with wider transistors |

**Conclusion:**  
Proper selection of **Wp/Wn ratio** helps balance speed, power, and noise margins — crucial for robust CMOS inverter design.

---

### 🔍 **3. Comparative Analysis**

| Parameter | Power Supply Variation | Device Variation |
|------------|------------------------|------------------|
| **VTC Shift** | Shifts downward with lower V<sub>DD</sub> | Controlled by geometry ratio |
| **Delay** | Increases as voltage drops | Decreases with wider NMOS |
| **Noise Margin** | Slightly reduced at low voltage | Improved with balanced sizing |
| **Power Efficiency** | Enhanced at lower voltage | Decreases with larger device sizes |

---

### 🧠 **4. Summary**

- **Supply voltage variation** influences switching speed, energy efficiency, and logic stability.  
- **Device geometry variation** affects drive strength and noise margins.  
- Together, these factors define the **robustness** and **reliability** of CMOS inverters in advanced **RISC-V SoC** fabrication.  

---

### 🚀 **5. Next Steps**
- Analyze **dynamic power vs. V<sub>DD</sub>** using parametric sweeps.  
- Evaluate **delay vs. transistor ratio** for optimal sizing.  
- Document **power-delay tradeoff curves** for final tapeout optimization.  

---

### 🧩 **Supporting Files**
- `day5_inv_supplyvariation_Wp1_Wn036.spice`  
- `day5_inv_devicevariation_wp7_wn042.spice`  

---

### 🏁 **Conclusion**
Understanding **power supply** and **device variation** effects is essential for designing energy-efficient and reliable digital circuits.  
This lab validates theoretical principles of CMOS inverter design and forms the foundation for **robust RISC-V SoC implementation**.

---
