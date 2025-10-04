
# Day 3 - Combinational and Sequential Optimizations

## Welcome Message
Welcome to Day 3 of this workshop!  
Today’s focus is on **optimizing combinational and sequential circuits** to improve area, performance, and power.  
By the end of this session, you will understand optimization techniques and reinforce them through hands-on labs.

---

## Agenda
- Introduction to Optimizations  
- Combinational Logic Optimizations  
- Sequential Logic Optimizations  
- Sequential Optimizations for Unused Outputs  

---

## 1. Introduction to Optimizations
Optimization in digital design aims to **improve efficiency while preserving functionality**.

### Why Optimizations Are Needed
- **Reduce chip area** → lowers manufacturing cost  
- **Improve performance** → enables higher clock frequency  
- **Minimize power consumption** → better energy efficiency  
- **Meet timing/resource constraints** in complex designs  

### Types of Optimizations
- **Combinational Logic Optimization** → simplifies Boolean logic and gates.  
- **Sequential Logic Optimization** → improves registers, flip-flops, FSMs, and clocking.  

---

## 2. Combinational Logic Optimizations
Combinational optimizations reduce circuit complexity without altering functionality.

### Common Techniques
- **Boolean Simplification**: Apply Boolean laws to reduce expressions.  
  Example:  
Y = A·B + A·B' → Y = A
- **Constant Propagation**: Simplify logic with known constant inputs.  
Example:  
If A = 1, then Y = A & B → Y = B

---

### Labs on Combinational Optimization

#### Lab-1: Simple Ternary Optimization
**File:** [opt_check.v](./Verilog_Files/Day3/opt_check.v)  
- Code: `y = a ? b : 0`  
- Simplification: `y = a & b`  
- **Optimized Circuit:** AND gate  

#### Lab-2: Ternary with Constant 1
**File:** [opt_check2.v](./Verilog_Files/Day3/opt_check2.v)  
- Code: `y = a ? 1 : b`  
- Simplification: `y = a | b`  
- **Optimized Circuit:** OR gate  

#### Lab-3: Nested Ternary
**File:** [opt_check3.v](./Verilog_Files/Day3/opt_check3.v)    
- Step Simplification:  
- `c ? b : 0 → c & b`  
- `a ? (c & b) : 0 → a & c & b`  
- Final Logic: `y = a & b & c`  
- **Optimized Circuit:** 3-input AND gate  

#### Lab-4: Multi-Level Ternary with Inversion
**File:** [opt_check4.v](./Verilog_Files/Day3/opt_check4.v)   
- Original: `y = a ? (b ? (a & c) : c) : !c`  
- Simplification:  
- Inner reduces to `c`  
- Final: `y = a ? c : !c`  
- Equivalent to `y = ~(a ^ c)`  
- **Optimized Circuit:** XNOR gate  

---

## 3. Sequential Logic Optimizations
Sequential optimizations improve efficiency of registers, FSMs, and clocking.

### Goals
- Reduce flip-flop/register count  
- Balance timing paths for better performance  
- Minimize dynamic power  

### Techniques
- **Retiming:** Move flip-flops across logic to balance setup/hold.  
- **State Minimization:** Merge equivalent FSM states.  
- **Clock Gating:** Disable clock for unused registers.  
- **Register Sharing:** Reuse registers for mutually exclusive operations.  

---

### Labs on Sequential Optimization

#### Lab-1: Flip-Flop Driving Constant Value
**File:** [dff_const1.v](./Verilog_Files/Day3/dff_const1.v)    
- Behavior:  
- On reset → q = 0  
- After reset → q = 1 forever  
- Optimization:  
- Flip-flop unnecessary since output is always constant after reset.  
- **Tool ties `q` directly to VCC.**  

#### Lab-2: Flip-Flop Always Constant 1
**File:** [dff_const2.v](./Verilog_Files/Day3/dff_const2.v)    
- Behavior: q = 1 at all times (even during reset).  
- Optimization:  
- Flip-flop completely removed.  
- Output tied directly to VCC.  

---

## 4. Sequential Optimizations for Unused Outputs

### Lab-1: Counter with Only LSB Used
**File:** [counter_opt.v](./Verilog_Files/Day3/counter_opt.v)    
- 3-bit counter increments each clock cycle.  
- Only `count[0]` is used as output `q`.  
- **Optimization:** Higher bits (`count[1], count[2]`) are removed.  
- **Final Hardware:** A single toggle flip-flop remains.  

### Lab-2: Counter Compared to Constant
**File:** [counter_opt2.v](./Verilog_Files/Day3/counter_opt2.v)    
- 3-bit counter with output `q = (count == 3'b100)`.  
- All bits are required for the comparison.  
- **Optimization:** Counter remains 3 bits, but comparator is minimized.  

---
