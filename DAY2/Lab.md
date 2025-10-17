# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds) — Simulation Lab  

---

### 🧪 **Experiment: Id–Vds Simulation of an NMOS (nfet)**

This experiment demonstrates the **Id–Vds characteristics** of an **NMOS transistor** using **ngspice** simulations.  
It verifies the theoretical behavior across **linear** and **saturation regions**.

---

### ⚙️ **Step 1: Clone the Project Repository**

Clone the official **VSD Sky130 Circuit Design Workshop** GitHub repository to access design and SPICE simulation files.

```bash
$ git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
$ cd sky130CircuitDesignWorkshop/design/
```

---

### ⚙️ **Step 2: Run ngspice Simulation**

Use the provided `.spice` file to simulate **drain current (Id)** vs **drain-to-source voltage (Vds)**.

```bash
$ ngspice day1_nfet_idvds_L2_W5.spice
```

---

### 📈 **Simulation Output**

The simulation initializes ngspice, processes the circuit netlist, and generates the **I–V characteristics** of the NMOS device.

<img width="915" height="680" alt="ngspice-output" src="https://github.com/user-attachments/assets/2c1d8b44-4a66-4c26-8ee1-40b0fd9fa74c" />

---

### 🧮 **Step 3: Plot Id vs Vds Curve**

To visualize the transistor’s behavior, plot the drain current with respect to drain-to-source voltage.

```bash
$ plot -vdd#branch
```

---

### 📊 **Graph Output**

This plot shows how **Id** varies with **Vds** for different **Vgs** values — illustrating the transition between **linear** and **saturation** regions.

<img width="1422" height="845" alt="id-vds-plot" src="https://github.com/user-attachments/assets/1528836f-1060-4f95-9f94-81cb72179516" />

---

### 🧭 **Analysis**

- For **small Vds**, Id increases **linearly** → NMOS in **triode (linear)** region.  
- As **Vds** reaches \( V_{GS} - V_{th} \), **pinch-off** occurs, and Id saturates.  
- Beyond that, **current remains nearly constant**, confirming the **saturation** region of operation.  

---

### ✅ **Conclusion**

This simulation verifies that the **ngspice** environment accurately models NMOS device characteristics:  
- Id–Vds curve matches theoretical expectations.  
- The transition from **linear** to **saturation** operation is clearly visible.  
- This is a foundational step in understanding **MOSFET behavior** within analog and digital circuits.

---

🧠 **Pro Tip:**  
You can modify **W/L ratios** and **supply voltages** in the `.spice` file to explore how **device geometry** affects the transistor’s current characteristics.

---
