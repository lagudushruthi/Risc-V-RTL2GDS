# Day 3: Combinational and Sequential Optimization

Welcome to Day 3 of this workshop! Today we discuss optimization of combinational and sequential circuits, introducing techniques to enhance efficiency and performance.

---

## Table of Contents

- [1. Constant Propagation](#1-constant-propagation)
- [2. State Optimization](#2-state-optimization)
- [3. Cloning](#3-cloning)
- [4. Retiming](#4-retiming)
- [5. Labs on Optimization](#5-labs-on-optimization)
  - [Combinational Optimization](#combinational-optimization)
  - [Sequential Optimization](#sequential-optimization)
  - [Optimization of unused ports](#optimization-of-unused-ports)

---

## 1. Constant Propagation

In VLSI design, constant propagation is a compiler optimization technique used to replace variables with their constant values during synthesis. This can simplify design and enhance performance.

**How it works:**  
Constant propagation analyzes the design code to identify variables with constant values. These are replaced directly, allowing tools to simplify logic and reduce circuit size.

**Benefits:**
- **Reduced Complexity:** Simpler logic, smaller circuit.
- **Performance Improvement:** Faster execution and reduced delays.
- **Resource Optimization:** Fewer gates or flip-flops required.

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/Constant_Propagation_Example.png" 
       alt="constant propagation" width="600"/>
</p>

---

## 2. State Optimization

State optimization refines finite state machines (FSMs) to improve efficiency in IC design. It reduces the number of states, optimizes encoding, and minimizes logic.

**How it is done:**
- **State Reduction:** Merge equivalent states using algorithms.
- **State Encoding:** Assign optimal codes to states.
- **Logic Minimization:** Use Boolean algebra or tools for compact equations.
- **Power Optimization:** Techniques like clock gating reduce dynamic power.

---

## 3. Cloning

Cloning duplicates a logic cell or module to optimize performance, reduce power, or improve timing by balancing load or reducing wire length.

**How it’s done:**
- Identify critical paths using analysis tools.
- Duplicate the target cell/module.
- Redistribute connections to balance load.
- Place and route the cloned cell.
- Verify improvement via timing and power analysis.

---

## 4. Retiming

Retiming is a design optimization technique that improves circuit performance by repositioning registers (flip-flops) without changing functionality.

**How it is done:**
1. **Graph Representation:** Model circuit as a directed graph.
2. **Register Repositioning:** Move registers to balance path delays.
3. **Constraints Analysis:** Maintain timing and functional equivalence.
4. **Optimization:** Adjust register positions to minimize clock period and optimize power.

---

## 5. Labs on Optimization

### Combinational Optimization

Below is the Verilog code for Lab 1:

```verilog
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```

**Explanation:**
- `assign y = a ? b : 0;` means:
  - If `a` is true, `y` is assigned the value of `b`.
  - If `a` is false, `y` is 0.

Follow the Yosys synthesis steps and add the following between `abc -liberty` and `synth -top`:
```shell
opt_clean -purge
```
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/opt_check_netlist.PNG" 
       alt="opt_check synthesis" width="600"/>
</p>


---


Verilog code:

```verilog
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

**Code Analysis:**
- Acts as a multiplexer:
  - `y = 1` if `a` is true.
  - `y = b` if `a` is false.

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/opt_check2_netlist.PNG" 
       alt="opt_check2 synthesis" width="600"/>
</p>

---


Verilog code:

```verilog
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

**Functionality:**  
2-to-1 multiplexer; `y = a ? 1 : b` (outputs `1` when `a` is true, otherwise `b`).

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/opt_check3_netlist.PNG" 
       alt="opt_check3 synthesis" width="600"/>
</p>
---


Verilog code:

```verilog
module opt_check4 (input a , input b , input c , output y);
 assign y = a?(b?(a & c ):c):(!c);
 endmodule
```

**Functionality:**
- Three inputs (`a`, `b`, `c`), output `y`.
- Nested ternary logic:
  - If `a = 1`, `y = c`.
  - If `a = 0`, `y = !c`.
- Logic simplifies to:  
  `y = a ? c : !c`

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/opt_check4_netlist.PNG" 
       alt="opt_check4 synthesis" width="600"/>
</p>

---

***Multiple module optimization:***

***Example1:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/multiple_module_opt.PNG" 
       alt="multiple module opt synthesis" width="600"/>
</p>

---

***Example2:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/multiple_module_opt2.PNG" 
       alt="multiple module opt2 synthesis" width="600"/>
</p>

---


### Sequential Optimization

Verilog code:

```verilog
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```

**Functionality:**
- D flip-flop with:
  - Asynchronous reset to 0
  - Loads constant `1` when not in reset
    
***Simulation***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const1.PNG" 
       alt="dff_const1 simulation" width="600"/>
</p>

***Synthesis:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const1_netlist.PNG" 
       alt="dff_const1 synthesis" width="600"/>
</p>

---


Verilog code:

```verilog
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```

**Functionality:**
- D flip-flop always sets output `q` to `1` (regardless of reset or clock).
  
***Simulation***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const2.PNG" 
       alt="dff_const2 simulation" width="600"/>
</p>

***Synthesis:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const2_netlist.PNG" 
       alt="dff_const2 synthesis" width="600"/>
</p>

---

***DFF_Const3:***

***Simulation***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const3.PNG" 
       alt="dff_const3 simulation" width="600"/>
</p>

***Synthesis:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const3_netlist.PNG" 
       alt="dff_const3 synthesis" width="600"/>
</p>

***DFF_Const4:***

***Simulation***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const4.PNG" 
       alt="dff_const4 simulation" width="600"/>
</p>

***Synthesis:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const4_netlist.PNG" 
       alt="dff_const4 synthesis" width="600"/>
</p>

***DFF_Const5:***

***Simulation***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const5.PNG" 
       alt="dff_const5 simulation" width="600"/>
</p>

***Synthesis:***

 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/dff_const5_netlist.PNG" 
       alt="dff_const5 synthesis" width="600"/>
</p>

### Optimization of unused ports:***
***Example1: 3-bit Counter which drives only 1 output***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/counter_opt_netlist.PNG" 
       alt="counter opt synthesis" width="600"/>
</p>

***Example2: 3-bit Counter which drives all the outputs***
 <p align="center">
  <img src="https://github.com/lagudushruthi/Risc-V-RTL2GDS/blob/main/Week1/Day3/counter_opt2_netlist.PNG" 
       alt="counter opt2 synthesis" width="600"/>
</p>


## Summary
- **Focus:** Optimization techniques for combinational and sequential circuits in digital design, with practical Verilog labs.
  
- **Topics Covered:**
  1. **Constant Propagation:** Replacing variables with constant values to simplify logic and improve circuit efficiency.
  2. **State Optimization:** Reducing states and optimizing encoding in finite state machines to use less logic and power.
  3. **Cloning:** Duplicating logic cells/modules to improve timing and balance load.
  4. **Retiming:** Repositioning registers in a circuit to enhance performance without altering its function.

- **Labs:** Optimization of combinational, sequential circuits, unused ports 
