# Week 4 – CMOS Inverter Characteristics & Robustness (Sky130 + Ngspice)

This week focuses on understanding **CMOS inverter behavior** using **theoretical concepts + Ngspice simulations on Sky130 PDK**.  
We explore **static and dynamic characteristics, switching behavior, noise margin, and robustness against supply/device variations.**

---

## ✅ Table of Contents

| Day | Topic | Key Focus |
|----|-------------------------------|-------------------------------|
| [Day1](./Day1 ) | NMOS Id–Vds Characteristics | Linear & Saturation regions, channel length modulation, SPICE simulation |
| [Day2](./Day2/Readme.md) | Velocity Saturation & Basic VTC | Short-channel effects, PMOS vs NMOS load line, CMOS VTC construction |
| [Day3](./Day3/Readme.md) | CMOS Switching Threshold & Dynamic Behavior | Vm calculation, delay analysis, rise/fall symmetry |
| [Day4](./Day4/Readme.md) | CMOS Noise Margin Evaluation | VOH, VOL, VIH, VIL, NML, NMH using VTC slope method |
| [Day5](./Day5/Readme.md) | Power Supply & Device Variation Robustness | VDD variation → gain, W/L variation → switching threshold shift |

---

## 🔍 What You Will Learn in Week 4

### ✅ Day1 – NMOS Drain Characteristics
- Id vs Vds (linear & saturation)
- First-order equation derivation
- Channel length modulation (λ)
- Sky130 NMOS SPICE simulation

### ✅ Day2 – Velocity Saturation & CMOS VTC
- Why short-channel devices deviate (VSAT)
- Load-line method (NMOS & PMOS)
- CMOS inverter VTC curve construction
- Vin vs Vout static behavior

### ✅ Day3 – Switching Threshold (Vm) & Delay
- Condition: Id_NMOS = Id_PMOS
- Vm = point where Vin = Vout
- Analytical Vm formula
- Rise/Fall delay comparison
- Balanced inverter design (Wp/Wn ratio)

### ✅ Day4 – Noise Margin
- VOH, VOL, VIH, VIL extraction
- dVout/dVin = –1 method
- NML & NMH calculation
- Effect of imbalance on noise immunity

### ✅ Day5 – Robustness Analysis
**(a) Power Supply Variation**
- VDD sweep
- Gain ∝ VDD
- Lower VDD → poor switching and noise margin

**(b) Device Size Variation**
- Changing Wp/Wn ratio
- Vm shift toward stronger device
- Balanced sizing → Vm ≈ VDD/2

---

## 🎯 Final Outcome

By the end of Week 4, you will be able to:

✅ Understand MOSFET behavior in-depth  
✅ Build and analyze a CMOS inverter using Sky130 models  
✅ Derive and simulate VTC, Vm, gain, noise margins  
✅ Evaluate design robustness under real-world variations  
✅ Apply these concepts in digital circuit design and timing optimization

---




