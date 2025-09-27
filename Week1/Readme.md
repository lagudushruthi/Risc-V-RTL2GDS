# 🖥️ Week 1: VSD Training – RTL Simulation & Synthesis

Welcome to **Week 1** of the VLSI System Design (VSD) training program.  
This folder contains **5 days of hands-on learning**, exploring RTL simulation, synthesis, standard cell libraries, optimizations, and gate-level verification.  


---

## 📂 Folder Structure

| Folder       | Description |
| ------------ | ----------- |
| `Day1`      | RTL simulation, testbench creation, basic synthesis with Yosys, fast vs slow cells |
| `Day2`      | Deep dive into `.lib` files, hierarchical vs flat synthesis, flip-flop coding styles, RTL optimizations |
| `Day3`      | Combinational & sequential logic optimizations, constant propagation, retiming, state reduction, cloning |
| `Day4`      | Gate-Level Simulation (GLS), synthesis-simulation mismatch analysis, best RTL coding practices |
| `Day5`      | incomplete if/else and case statements, For and loop constructs, Ripple carry adder |

---

## 📘 Day-wise Summary

### 🚀 [Day1: RTL Simulation & Synthesis](./Day1)
- Learned **RTL simulation** with `iverilog` + `GTKWave`  
- Created **design (`good_mux.v`)** and **testbench (`tb_good_mux.v`)**  
- Performed **synthesis with Yosys**, understanding netlist generation  
- Explored **.lib standard cells** and **fast vs slow cells**  
- Verified post-synthesis functionality

### 📚 [Day2: .lib Files, Hierarchy, Flip-Flops & RTL Optimizations](./Day2)
- Explored **.lib files** and PVT corners for robust design  
- Compared **hierarchical vs flat synthesis** in Yosys  
- Implemented **different flip-flop coding styles** (async/sync reset)  
- Learned RTL **optimization tricks** like power-of-two multiplication → shift-left

### 🌟 [Day3: Combinational & Sequential Optimizations](./Day3)
- Applied **constant propagation** and **Boolean simplification** in combinational circuits  
- Optimized sequential logic: **state reduction, retiming, cloning**  
- Ran labs (`opt_check*`, `diff_const*`, `counter_opt*`) to observe real hardware optimizations  
- Understood **unused port pruning** and area/power reduction

### 🛠️ [Day4: Gate-Level Simulation (GLS) & Synthesis-Simulation Mismatches](./Day4)
- Performed **GLS using netlist.v** and testbench with `.lib` files  
- Investigated common causes of simulation-synthesis mismatches:
  - Incomplete sensitivity lists (`always @(sel)` vs `always @(*)`)  
  - Blocking (`=`) vs non-blocking (`<=`) assignment misuse  
  - Non-standard Verilog constructs  
- Ran labs on muxes and sequential designs to verify correct functionality  
- Learned best practices for **synthesizable, simulation-consistent RTL**

### ⚡ [Day5: Optimization in Synthesis](./Day5)
- Learned how **incomplete if/else and case statements** cause **inferred latches**  
- Explored **nested if-else, case statements, and default conditions** to avoid latches  
- Implemented **for-loops** and **generate blocks** for scalable RTL design  
- Designed and verified:
  - **4:1 MUX** using for-loop  
  - **8:1 DEMUX** (case & for-loop versions)  
  - **8-bit Ripple Carry Adder (RCA)** using generate block  
- Performed **simulation, synthesis, and GLS** to confirm correctness and optimizations

---

## ⚙️ Tools Used

| Tool          | Purpose |
| ------------- | ------- |
| `iverilog`    | RTL simulation |
| `GTKWave`     | Waveform viewing |
| `Yosys`       | RTL synthesis and netlist generation |
| `.lib` files  | Standard cell definitions and PVT info |
| `.sdc` files  | Constraints for synthesis optimization |

---

## ✅ Key Takeaways

1. **Simulation first:** Always verify RTL functionality before synthesis.  
2. **Synthesis preserves functionality:** Map RTL to standard cells carefully.  
3. **Fast vs slow cells:** Understand trade-offs between speed, area, and power.  
4. **Hierarchical design:** Easier to debug and maintain complex designs.  
5. **GLS verification:** Ensure netlist matches RTL; watch for sensitivity list & assignment issues.
6. **Optimization:** Always provide **complete assignments** to avoid latch inference.

---


