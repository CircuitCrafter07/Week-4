# 🌍 RISC-V SoC Tapeout Program — VSD  
## ⚡ Velocity Saturation and CMOS Inverter VTC — Simulation Lab  

---

### 🧪 **Experiment 1: Ids–Vds for Short-Channel Device**

This experiment analyzes **drain current (Ids)** versus **drain-to-source voltage (Vds)** for a **short-channel NMOS transistor**, highlighting **velocity saturation effects**.

---

### ⚙️ **Step 1: Run ngspice Simulation**

Navigate to the design directory and execute the simulation file for the short-channel NMOS.

```bash
$ cd sky130CircuitDesignWorkshop/design/
$ ngspice day2_nfet_idvds_L015_W039.spice
```

---

### 📈 **Simulation Output**

The ngspice output displays the transistor’s behavior as **Vds** varies under different **Vgs** conditions.

![day2](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY2/Screenshot%20from%202025-10-17%2009-45-17.png)

---

### 🧮 **Step 2: Plot Ids vs Vds Curve**

Use the following command to visualize the drain current plot:

```bash
$ plot -vdd#branch
```

---

### 📊 **Graph Output**

The plotted curve demonstrates how **Ids** initially increases linearly with **Vds**, then gradually saturates due to **velocity saturation**.

![day2-1](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY2/Screenshot%20from%202025-10-16%2018-56-25.png)

---

### 🧪 **Experiment 2: Ids–Vds Without Vdd Sweep**

This test removes the **Vdd sweep** parameter to isolate the **Ids–Vds** dependence at fixed supply voltage conditions.

```bash
$ ngspice day2_nfet_idvgs_L015_W039.spice
```

---

### 📈 **Simulation Output**

The SPICE output file shows Ids–Vds characteristics under specific **Vgs** values for short-channel NMOS.

![day2](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY2/Screenshot%20from%202025-10-17%2009-46-14.png)

---

### 🧮 **Step 2: Plot Ids Curve (Fixed Vgs)**

Use the following command to generate the plot:

```bash
$ plot -vdd#branch
```

---

### 📊 **Graph Output**

This plot reveals that for short-channel devices:  
- **Current saturates early**, even at moderate **Vds** values.  
- The **saturation region** is limited by **carrier velocity** rather than channel pinch-off.  

![day2-2](https://github.com/CircuitCrafter07/Week-4/blob/main/DAY2/VT_0.77v.png)

---

### 🧭 **Analysis**

- **Velocity saturation** dominates at submicron dimensions, reducing current gain compared to long-channel MOSFETs.  
- The **Ids–Vds** relationship deviates from the quadratic law, indicating **nonlinear mobility** effects.  
- SPICE simulations help visualize **realistic short-channel behavior** beyond ideal models.

---

### ✅ **Conclusion**

This lab confirms that **velocity saturation** limits current in short-channel transistors, leading to deviation from ideal square-law behavior.  
Such effects are critical in **deep-submicron CMOS design**, impacting speed and power performance.

---

🧠 **Pro Tip:**  
Try modifying **L (channel length)** and **W (width)** parameters in the `.spice` files to observe how **velocity saturation onset** changes with geometry.

---
