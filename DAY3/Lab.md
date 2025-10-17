# ⚙️ RISC-V SoC Tapeout Program — VSD  
## CMOS Switching Threshold & Dynamic Simulations  

This lab focuses on **analyzing the Voltage Transfer Characteristics (VTC)** and **transient behavior** of a CMOS inverter using the **Sky130 PDK** and **Ngspice simulator**.  
The goal is to understand inverter switching thresholds, noise margins, and propagation delays through simulation.

---

## 🧩 Part 1: VTC Characteristics of CMOS Inverter

### 📂 Navigate to Design Directory
```bash
$ cd sky130CircuitDesignWorkshop/design/
```

### ▶️ Run the SPICE Simulation
```bash
$ ngspice day3_inv_vtc_Wp084_Wn036.spice

```
![imporatnce](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY3/Screenshot%20from%202025-10-17%2009-43-45.png)
This command executes the SPICE netlist that defines a CMOS inverter circuit with:
- **PMOS width (Wp)** = 0.84 µm  
- **NMOS width (Wn)** = 0.36 µm  

These parameters help maintain a balanced switching threshold near mid-supply voltage.

---

### 📈 View the Voltage Transfer Curve (VTC)
After launching Ngspice, plot the output voltage versus input voltage:

```bash
$ plot out vs in
```

#### **Simulation Output:**

![VTC Graph](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY3/Screenshot%20from%202025-10-17%2009-35-27.png)

This plot shows the **VTC curve**, which highlights:
- The **switching threshold voltage (V<sub>M</sub>)**
- The **noise margins** for logic HIGH and LOW
- The **region of high gain** around the transition point

---

## ⚡ Part 2: Transient Analysis of CMOS Inverter

### ▶️ Run the Transient Simulation
```bash
$ ngspice day3_inv_tran_Wp084_Wn036.spice
```
![Transient Output 1](https://github.com/user-attachments/assets/324f4f5b-cdd9-4580-a177-1e4697cfc7a6)
This simulation analyzes the **dynamic response** of the inverter when subjected to a time-varying input (e.g., square wave).

---

### 📊 Plot the Transient Waveform
Inside Ngspice, run:
```bash
$ plot out vs time in
```

#### **Simulation Output:**


![Transient Output 2](https://github.com/user-attachments/assets/0578767b-16db-4ac0-9f1a-f537d059bc34)

These waveforms show:
- **Input (Vin)** and **Output (Vout)** signals over time  
- The **propagation delay (t<sub>pHL</sub> / t<sub>pLH</sub>)** of the inverter  
- The **rise/fall time characteristics**, which are critical for digital speed and power analysis  

---

## 🧠 Summary

| Parameter | Description | Typical Observation |
|------------|--------------|---------------------|
| V<sub>M</sub> | Switching threshold voltage | ≈ 0.9V (for 1.8V supply) |
| Noise Margin (High/Low) | Logic level tolerance | Sufficient for stable logic |
| t<sub>pHL</sub> / t<sub>pLH</sub> | Propagation delay | In the nanosecond range |

**Conclusion:**  
The CMOS inverter demonstrates sharp switching, stable noise margins, and predictable delay — essential characteristics for reliable digital logic design in SoC implementations.

---

**🧪 Tools Used:**  
- SkyWater 130nm PDK  
- Ngspice Simulator  
- Linux Terminal / VS Code  

---

> 💡 *Tip:* You can experiment by modifying transistor widths or supply voltage in the `.spice` file to observe their impact on the VTC and transient response.
