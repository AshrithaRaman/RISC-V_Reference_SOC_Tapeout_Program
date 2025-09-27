

# **WEEK 1 – DAY 1**

**Topic:** Introduction to Verilog RTL Design And Synthesis

---

## **1. Concepts**

### **Simulator**

* A simulator checks whether the RTL design works according to the given specification.
* It applies input changes and evaluates outputs accordingly.

**Working principle:**

* If an input signal changes, the simulator re-evaluates the output.
* If no input changes, the output remains unchanged.
* Hence, simulation is event-driven.

---

### **Design**

* The design is the actual Verilog code (or set of codes).
* It implements the intended functionality to meet specifications.

---

### **Testbench (TB)**

* A testbench is not a real hardware design but a verification environment.
* It generates stimulus (test vectors) and applies them to the DUT (Design Under Test).
* Unlike the design:

  * Design has primary inputs/outputs.
  * Testbench does not have primary inputs/outputs; it only drives and checks the DUT.

![Testbench Block Diagram](Images/Day1_Images/testbench.png)
---

## **2. Tools Used**

* iverilog → Simulator used to compile and simulate Verilog designs.
* gtkwave → Waveform viewer used to analyze simulation outputs.

![Testbench Block Diagram](Images/Day1_Images/iverilog_based_simulation_flow.png)
---

## **3. Lab Setup**

1. Create project folder:
   mkdir ~/VLSI
   cd ~/VLSI

2. Clone the course repository:
   git clone <repository_link>
   (This creates the folder SkyRTLDesignAndSynthesisWorkshop)

3. Folder structure inside the repo:

   * my_lib/lib → Sky130 standard cell library files used for synthesis.
   * my_lib/verilog_model → Verilog models of the standard cells.
   * verilogfiles/ → Contains all Verilog source and testbench files.

![Testbench Block Diagram](Images/Day1_Images/lab1intro_1.png)
![Testbench Block Diagram](Images/Day1_Images/lab1intro_2.png)
---

## **4. Labs**

### **Lab 1 – Introduction**

* Explore the folder structure and understand library + Verilog files.

---

### **Lab 2 – Using iverilog and gtkwave**

Steps:

1. Go to verilogfiles directory:
   cd SkyRTLDesignAndSynthesisWorkshop/verilogfiles

2. Each design file has a corresponding testbench named tb_<designname>.v

3. Compile design and testbench:
   iverilog designfile.v tb_designfile.v
   (This generates an executable file a.out)

4. Run the simulation:
   ./a.out
   (This produces a VCD file)

5. View the waveform:
   gtkwave dump.vcd

   * A waveform window opens.
   * On the left panel, you can see design, uut (unit under test), and signals.
   * Drag and drop signals to the waveform area.
   * The --> arrows represent transitions in the signals.
![Testbench Block Diagram](Images/Day1_Images/lab2_1.png)
![Testbench Block Diagram](Images/Day1_Images/lab2_2.png)

---

### **Lab 3 – Observing Design and Testbench**

* Open both the design and its corresponding testbench file.
* Observe:

![Testbench Block Diagram](Images/Day1_Images/lab3_1.png)
![Testbench Block Diagram](Images/Day1_Images/lab3_2.png)
  * The design has primary inputs and outputs.
  * The testbench generates inputs, connects them to the design, and monitors outputs.

---


