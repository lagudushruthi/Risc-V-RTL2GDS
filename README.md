# 🖥️ RISC-V Reference SoC Tapeout Program VSD
<div align="center">

[![RISC-V](https://img.shields.io/badge/RISC--V-SoC%20Tapeout-blue?style=for-the-badge&logo=riscv)](https://riscv.org/)
[![VSD](https://img.shields.io/badge/VSD-Program-orange?style=for-the-badge)](https://vsdiat.vlsisystemdesign.com/)
![Participants](https://img.shields.io/badge/Participants-3500+-success?style=for-the-badge)
![India](https://img.shields.io/badge/Made%20in-India-saffron?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHJlY3Qgd2lkdGg9IjI0IiBoZWlnaHQ9IjgiIGZpbGw9IiNGRjk5MzMiLz4KPHJlY3QgeT0iOCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjgiIGZpbGw9IiNGRkZGRkYiLz4KPHJlY3QgeT0iMTYiIHdpZHRoPSIyNCIgaGVpZ2h0PSI4IiBmaWxsPSIjMTM4ODA4Ii8+Cjwvc3ZnPgo=)

</div>


Welcome to my journey through the **SoC Tapeout Program VSD**!  
This repository documents my **week-by-week progress** with tasks inside each week.  

"In this program, we learn to design a System-on-Chip (SoC) from basic RTL to GDSII using open-source tools. Part of India’s largest collaborative RISC-V tapeout initiative, empowering 3500+ participants to build silicon and advance the nation’s semiconductor ecosystem

---

## 📅 Week 0 — Setup & Tools

| Task | Description | Status |
|------|-------------|---------|
| [**Task 0**](week0) | 🛠️ [Tools Installation](week0/assets/readme.md) — Installed **Iverilog**, **Yosys**, and **gtkWave** | ✅ Done |



### 🌟 Key Learnings from Week 0
- Installed and verified **open-source EDA tools** successfully.  
- Learned about **basic environment setup** for RTL design and synthesis.  
- Prepared the system for upcoming **RTL → GDSII flow experiments**.

## 📅 Week 1 — RTL Synthesis & Gate-Level Simulation (GLS)

| Task       | Description                                                                 | Status |
| ---------- | --------------------------------------------------------------------------- | ------ |
| [**Day1**]([RTL Simulation & Synthesis](./Day1)) | MUX synthesis in Yosys, Sky130 mapping, GLS netlist generation         | ✅ Done |
| [**Day2**]([.lib Files, Hierarchy, Flip-Flops & RTL Optimizations](./Day2)) | Constant DFF mapping + GLS validation          | ✅ Done |
| [**Day3**]([Combinational & Sequential Optimizations](./Day3)) | MUX using `for-generate`, RTL vs GLS verification                       | ✅ Done |
| [**Day4**]([Gate-Level Simulation & Synthesis-Simulation Mismatches](./Day4))| DEMUX using `generate`, RTL vs GLS verification                         | ✅ Done |
| [**Day5**]([Optimization in Synthesis](./Day5)) | Ripple Carry Adder synthesis & GLS validation                           | ✅ Done |


## 📅 Week 2 — Fundamentals of SoC Design

| Task       | Description | Status |
| ---------- | ----------- | ------ |
| [**Task 1**](Week2) | 📘 Write-up on SoC fundamentals | ✅ Done |
| [**Task 2**](Week2) | 📝 VSDBabySoC Pre synthesis Waveform  & explanations  | ✅ Done |

## 📅 Week 3 — BabySoC Synthesis and Timing Analysis

| Task   | Description                                                                                                                    | Status    |
| ------ | ------------------------------------------------------------------------------------------------------------------------------ | --------- |
| [**Task1**](Week3) | ⚡ Pre- and Post-Synthesis Simulation for BabySoC using **Sky130 PDK**; compared RTL vs gate-level waveforms                    | ✅ Done    |
| [**Task2**](Week3) | 📝 Short note on **Static Timing Analysis (STA)** and **OpenROAD** flow                                                        | ✅ Done    |
| [**Task3**](Week3) | 📊 Corner timing analysis with **Sky130 PDK corners** (TT, SS, FF); plotted WNS, TNS, worst slack, worst hold, and setup slack | ✅ Done    |

### 🌟 Key Learnings from Week 3

* Successfully verified **functional consistency** between RTL and gate-level netlists using **pre- and post-synthesis simulations**, ensuring correct BabySoC operation after technology mapping.
* Gained a practical understanding of **Static Timing Analysis (STA)** and the **OpenROAD flow**, including timing constraints, optimization, and automated ASIC design processes.
* Performed **corner timing analysis** across multiple PDK corners (TT, SS, FF), extracting and interpreting metrics like **WNS, TNS, worst slack, worst hold, and setup slack**, providing insights into timing robustness of the design.

## 🙏 Acknowledgment  

I am thankful to [**Kunal Ghosh**](https://github.com/kunalg123) and Team **[VLSI System Design (VSD)](https://vsdiat.vlsisystemdesign.com/)** for the opportunity to participate in the ongoing **RISC-V SoC Tapeout Program**.  

I also acknowledge the support of **RISC-V International**, **India Semiconductor Mission (ISM)**, **VLSI Society of India (VSI)**, and [**Efabless**](https://github.com/efabless) for making this initiative possible.  

## 📈 **Weekly Progress Tracker**

[![Week0](https://img.shields.io/badge/Week%200-Tools%20Setup-success?style=flat-square)](week0)
![Week 1](https://img.shields.io/badge/Week%201-Coming%20Soon-lightgrey?style=flat-square)(Week1)
![Week 2](https://img.shields.io/badge/Week%202-Upcoming-lightgrey?style=flat-square)(Week2)



**🔗 Program Links:**
[![VSD Website](https://img.shields.io/badge/VSD-Official%20Website-blue?style=flat-square)](https://vsdiat.vlsisystemdesign.com/)
[![RISC-V](https://img.shields.io/badge/RISC--V-International-green?style=flat-square)](https://riscv.org/)
[![Efabless](https://img.shields.io/badge/Efabless-Platform-orange?style=flat-square)](https://efabless.com/)





---
