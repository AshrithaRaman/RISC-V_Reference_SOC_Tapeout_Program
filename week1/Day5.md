# 🧠 Day 5 – Optimization in Synthesis

## 🎯 Objective
Explore how **Verilog coding style** affects synthesis optimization, area, and timing.  
Learn how incomplete conditionals cause **latch inference**, and how `for` / `generate` loops make designs **efficient and scalable**.

---

## ⚙️ 1️⃣ What is Optimization in Synthesis?

When RTL code is converted to gates, the synthesis tool tries to make it:
- **Smaller (area)**
- **Faster (timing)**
- **Lower power**

### 🧩 Goals of Optimization

| Goal | Description |
|------|--------------|
| **Area** | Reduce gate count and resource usage |
| **Speed** | Improve timing and reduce critical path delay |
| **Power** | Reduce switching and static power |

### ⚠️ Poor Coding Causes
- Unwanted latches  
- Extra logic and slower timing  
- Simulation vs synthesis mismatches

✅ **Good RTL coding** → predictable, latch-free, optimized hardware.

---

## 2️⃣ `if` and `case` Constructs

### 🟢 `if` Statements
- Synthesized as **priority logic**
- Always assign outputs for **all paths**

if (cond1)
    y = 2'b01;
else if (cond2)
    y = 2'b10;
else
    y = 2'b00;   // ✅ covers all cases

🔴 Incomplete if (latch inferred)
always @(*) begin
    if (enable)
        y = data;   // ❌ no else → latch
end

✅ Corrected:
always @(*) begin
    if (enable)
        y = data;
    else
        y = 0;
end
🟣 case Statements

- Synthesized as multiplexers
- Always use default to cover all possibilities

case(sel)
  2'b00: y = a;
  2'b01: y = b;
  2'b10: y = c;
  default: y = d; // ✅ avoids latch
endcase


⚠️ Missing default = latch
⚠️ Overlapping cases = simulation mismatch

3️⃣ Lab 1 – Incomplete if

## Code

always @(*) begin
    if (i0)
        y = i1;   // ❌ no else
end


## Behavior

# Phase	Observation
- RTL Simulation	y appears to “hold” previous value
- Gate-Level (GLS)	Actual latch is inferred → glitches visible

✅ Add an else or give default assignment.

4️⃣ Lab 2 – Incomplete if-else-if
always @(*) begin
    if (i0)
        y = i1;
    else if (i2)
        y = i3;
    // ❌ no else → latch when i0=0 & i2=0
end

# Condition	Result
i0=1	y = i1
i0=0, i2=1	y = i3
i0=0, i2=0	❌ no assignment → latch

✅ Both RTL & GLS seem to hold value,
- but only GLS has real latch hardware, causing hazards.

5️⃣ Lab 3 – Complete Case Statement
always @(*) begin
    case(sel)
      2'b00: y = i0;
      2'b01: y = i1;
      default: y = i2;  // ✅ all cases handled
    endcase
end


🟢 Synthesizes as a clean 3-to-1 MUX
- No latches, no glitches.

6️⃣ Lab 4 – Overlapping Wildcard Case
always @(*) begin
    case(sel)
      2'b00: y = i0;
      2'b01: y = i1;
      2'b10: y = i2;
      2'b1?: y = i3;   // ❌ overlaps with 2'b10
    endcase
end


⚠️ 2’b10 matches both 2’b10 and 2’b1?
→ Different tools may resolve differently → simulation mismatch

✅ Avoid overlapping wildcards or ensure exclusivity.

7️⃣ Lab 5 – Partial Assignment Inside Case
case(sel)
  2'b00: begin
      y = i0;
      x = i2;
  end
  2'b01: y = i1;     // ❌ x not assigned
  default: begin
      x = i1;
      y = i2;
  end
endcase


🧠 When sel=01, x has no assignment → Latch inferred for x.

✅ Always assign all outputs in every path.

8️⃣ for Loops and generate Loops
🔹 for inside always

- Used for combinational or sequential repetition (unrolled by synthesizer).

🔹 generate for

Used for module instantiation repetition at compile time.

9️⃣ Lab 6 – for Loop Example
wire [3:0] i_int = {i3, i2, i1, i0};
integer k;

always @(*) begin
    for (k=0; k<4; k=k+1)
        if (k == sel)
            y = i_int[k];
end


🟢 Synthesizes to same 4-to-1 MUX as case version.
- Clean, compact, and scalable.

🔟 Lab 7 – Demux Using case and for

# Case Implementation

always @(*) begin
    y_int = 8'b0;
    case(sel)
      3'b000: y_int[0] = i;
      ...
      3'b111: y_int[7] = i;
    endcase
end


# For-Loop Implementation

always @(*) begin
    y_int = 8'b0;
    for (k=0; k<8; k=k+1)
        if (k == sel)
            y_int[k] = i;
end


✅ Both create identical hardware → 8-bit demux.
- Prefer for for cleaner, reusable code.

🔟➕1 Lab 8 – Generate-For (Ripple Carry Adder)
genvar i;
generate
  for (i=0; i<8; i=i+1) begin
      fa u_fa (
        .a(num1[i]), .b(num2[i]),
        .cin(carry[i]),
        .sum(sum[i]),
        .cout(carry[i+1])
      );
  end
endgenerate


🧠 Each loop instantiates one full adder.
- Synthesis unrolls into 8 actual FAs → real hardware replication.

✅ Summary
- Concept	Problem	Solution
- Incomplete if/case	Latch inferred	Add else / default
- Overlapping wildcard	Simulation mismatch	Avoid or ensure exclusivity
- Partial signal assignment	Unwanted latch	Assign all signals every time
- for / generate usage	Manual repetition	Simplify, scale, and optimize
✨ Takeaway

- Synthesis optimization starts with clean RTL.
- Always define complete logic, avoid ambiguous constructs,and leverage loops/generates for efficient and scalable hardware.


---
