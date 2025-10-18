# Day 5 – CMOS Power Supply and Device Variation Robustness Evaluation

In real digital circuits, CMOS inverters must remain reliable even when power supply or transistor parameters vary due to fabrication and operating conditions. In this session, we analyze how **power supply variation** and **device sizing variation** affect inverter robustness.

---

## 1. Power Supply Variation (VDD Sweep) and Its Effect on Gain

### Why VDD Variation Matters
In practical circuits, VDD is not perfectly constant. It can drop or fluctuate due to IR drop, noise, or switching activity. Changing VDD directly affects inverter behavior.

### Impact of VDD on VTC and Gain

| Parameter | When VDD Increases | When VDD Decreases |
|-----------|---------------------|---------------------|
| Drain current (Id) | Increases | Decreases |
| VTC slope | Steeper | Flatter |
| Gain (dVout/dVin) | Higher | Lower |
| Noise margins | Better | Worse |

- At **higher VDD**, the inverter switches more sharply (higher gain), offering better noise immunity.
- At **lower VDD**, the transition region becomes wider, the slope decreases, and the inverter becomes less robust.

### Key Result
**Inverter gain is directly proportional to VDD.**
Higher gain = sharper switching = better noise margin.

---

<p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day5 supply variation terminal.png" 
       alt="day5 supply variation terminal" width="600"/>
</p>

<p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day 5 sv graph.png" 
       alt="day5 sv" width="600"/>
</p>

<p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day5 sv gain.png" 
       alt="day5 sv gain" width="600"/>
</p>


## 2. Device Variation (Transistor Sizing) and Its Effect on Switching Threshold (Vm)

### Why Device Variation Matters
During fabrication, the effective **W/L of PMOS or NMOS can change**, causing imbalance between pull-up and pull-down strengths. This shifts the switching threshold Vm of the inverter.

### Conceptual Behavior

- If **PMOS is stronger (larger W/L)** → Output is pulled high more easily → **Vm shifts lower**
- If **NMOS is stronger (larger W/L)** → Output is pulled low more easily → **Vm shifts higher**
- If **PMOS and NMOS are balanced** → **Vm ≈ VDD / 2** (ideal case)

### Importance of Vm
The switching threshold Vm determines:
- Inverter logic decision point
- Symmetry of VTC curve
- Balance between rise and fall delay
- Noise margin on both logic levels

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day5 device variation terminal.png" 
       alt="day5 device variation terminal" width="600"/>
</p> 

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day5 dv graph.png" 
       alt="day5 dv graph" width="600"/>
</p>

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week4/Day5/day5 dv switching threshold.png" 
       alt="day5 switching threshold" width="600"/>
</p> 

### Optimal Design
For a **balanced inverter**:
- Choose Wp/Wn such that pull-up ≈ pull-down strength
- This makes Vm ≈ VDD/2
- Rise delay ≈ Fall delay
- Noise margins are symmetric

---

## 3. Summary Comparison

| Variation Type | Affects | Key Parameter |
|----------------|--------|----------------|
| Power Supply (VDD) | Gain & Noise Margin | VTC Slope |
| Device Sizing (W/L) | Switching Threshold | Vm |

---

## 4. Key Takeaways

- **Power supply variation** changes **gain** and **noise margin**.
- **Lower VDD** → lower gain → poor noise immunity.
- **Device sizing variation** shifts **switching threshold (Vm)**.
- **Stronger PMOS or NMOS skews Vm**, causing logic imbalance.
- **Best design = Balanced inverter**:
  - Vm ≈ VDD/2
  - Rise delay ≈ Fall delay
  - Good noise margins
  - Stable operation across variations

---

## 5. Why This Is Important in Real Chips

In fabricated chips:
- VDD fluctuates due to IR drop and transient current.
- Device dimensions vary due to process variations.

Therefore:
**Robust CMOS design must tolerate both supply and device variation.**
This forms the foundation of **PVT (Process-Voltage-Temperature) analysis** used in industry.

---


