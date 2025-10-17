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

![day2-3](https://github.com/user-attachments/assets/299475e2-6646-4808-83a4-99cfd85c66fd)

---

### 🧮 **Step 2: Plot Ids vs Vds Curve**

Use the following command to visualize the drain current plot:

```bash
$ plot -vdd#branch
```

---

### 📊 **Graph Output**

The plotted curve demonstrates how **Ids** initially increases linearly with **Vds**, then gradually saturates due to **velocity saturation**.

![day2-1](https://github.com/user-attachments/assets/4160a1ef-7983-4cef-8599-45cffdd656a6)

---

### 🧪 **Experiment 2: Ids–Vds Without Vdd Sweep**

This test removes the **Vdd sweep** parameter to isolate the **Ids–Vds** dependence at fixed supply voltage conditions.

```bash
$ ngspice day2_nfet_idvgs_L015_W039.spice
```

---

### 📈 **Simulation Output**

The SPICE output file shows Ids–Vds characteristics under specific **Vgs** values for short-channel NMOS.

![day2-4](https://github.com/user-attachments/assets/21c84e62-de8e-4882-aed8-d9dd557eeef9)

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

![day2-2](https://github.com/user-attachments/assets/00f2e170-de56-42b8-b7c4-0025dfd1680d)

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
