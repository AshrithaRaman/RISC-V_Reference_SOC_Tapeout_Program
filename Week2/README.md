# VSDBabySoC Project

This project focuses on designing a **compact open-source System on Chip (SoC)** using the **RVMYTH RISC-V processor core**.  
The SoC integrates a **Phase-Locked Loop (PLL)** for stable clock generation and a **10-bit Digital-to-Analog Converter (DAC)** for analog interfacing.  
The DAC allows BabySoC to convert digital outputs into analog signals, enabling interaction with analog-based devices such as mobile phones, audio systems, and televisions — making it possible to produce audio or video outputs.  

Built on the **Sky130 technology node**, this project provides a practical and educational platform for exploring the link between **digital design** and **analog systems**.

---

<details>
<summary>1. Understanding System on Chip (SoC)</summary>

A **System on a Chip (SoC)** integrates all major components of a computer system — CPU, memory, peripherals, and sometimes analog interfaces — onto a single silicon die.  
This miniaturization allows for faster communication between components, lower energy consumption, and compact device designs.

### Core Components of an SoC

- **CPU (Central Processing Unit)**  
  - Executes program instructions.  
  - Can include multiple cores for parallel processing.  
  - Supports instruction pipelining and branch prediction for performance optimization.
- **Memory**  
  - **RAM**: Fast, volatile storage for active processes.  
  - **ROM/Flash**: Non-volatile storage for firmware and bootloader.  
  - **Cache**: On-chip memory to reduce latency.
- **Input/Output (I/O) Interfaces**  
  - UART, SPI, I²C for peripherals.  
  - USB, HDMI, or Ethernet for external devices.
- **GPU (Graphics Processing Unit)**  
  - Handles image/video rendering.  
  - Supports video rendering and image processing.
- **DSP (Digital Signal Processor)**  
  - Optimized for audio, video, or sensor signal processing.  
  - Often used in mobile and audio devices.
- **Power Management Unit (PMU)**  
  - Controls voltage/frequency scaling for power efficiency.  
  - Manages sleep and low-power modes.
- **Connectivity & Security Units**  
  - Integrated Wi-Fi, Bluetooth, 5G modems.  
  - Encryption engines, secure boot, hardware random number generators.

### Advantages of SoCs

- Compact size  
- Power efficiency  
- High performance  
- Cost efficiency  
- Reliability

### Common Applications

- Smartphones & Tablets (Apple A-Series, Qualcomm Snapdragon, Samsung Exynos)  
- Wearable Devices (Smartwatches, Fitness Trackers)  
- IoT Systems (Smart Sensors, Home Automation)  
- Automotive Systems (ADAS, Infotainment)  
- Consumer Electronics (Smart TVs, Gaming Consoles, Drones)

### Limitations and Design Challenges

- Complex integration of digital and analog circuits  
- Thermal management and hotspots  
- Low flexibility for upgrades  
- High manufacturing cost for advanced nodes

</details>

<details>
<summary>2. Types of SoCs</summary>

SoCs can be classified based on their design purpose, processing capability, and application domain.

1. **Microcontroller-Based SoCs**  
   - Low-power, real-time control tasks.  
   - Examples: ARM Cortex-M, ESP32.  
   - Applications: IoT sensors, smart appliances, motor control.

2. **Microprocessor-Based SoCs**  
   - High-performance, multitasking operations.  
   - Examples: Raspberry Pi SoC, Apple M1.  
   - Applications: Laptops, smartphones, tablets.

3. **Application-Specific SoCs (ASICs)**  
   - Optimized for a particular task.  
   - Examples: Google TPU (AI), NVIDIA Jetson (vision/AI).  
   - High performance, low power for targeted applications.


</details>

<details>
<summary>3. SoC Design Flow</summary>


Specification → Architecture → RTL Design → Verification → Synthesis → Physical Design → Tape-Out → Post-Silicon Validation


- **Specification**: Define requirements and interfaces.  
- **Architecture**: Choose CPU cores, memory, peripherals.  
- **RTL Design**: Implement functionality in Verilog/SystemVerilog.  
- **Verification**: Test functionality using UVM/formal methods.  
- **Synthesis**: Convert RTL to gate-level netlist.  
- **Physical Design**: Floorplan, placement, routing, timing closure.  
- **Tape-Out**: Fabrication of the silicon chip.  
- **Post-Silicon Validation**: Test fabricated chip in real conditions.

</details>

<details>
<summary>4. Introduction to VSDBabySoC</summary>

The **VSDBabySoC** is a minimal, functional **RISC-V-based SoC** designed for learning, prototyping, and experimentation.  
It integrates:

- **RVMYTH CPU** – Executes RISC-V instructions  
- **PLL (Phase-Locked Loop)** – Ensures stable clock generation  
- **10-bit DAC** – Converts digital outputs to analog signals

  <img width="2270" height="1260" alt="image" src="https://github.com/user-attachments/assets/04970b7e-77f8-4b91-9819-b85bd99f2182" />


### Working Principle

**Clock Setup (PLL Activation)**

- PLL locks output frequency to a reference clock.  
- Reduces jitter and ensures synchronous operation.  
- Key metrics: phase noise, lock time, frequency stability.

**Data Handling by RVMYTH**

- CPU executes instructions from memory.  
- Generates digital values for DAC output.

**Analog Output (DAC Conversion)**

- 10-bit DAC → 1024 discrete levels.  
- Converts digital word to continuous voltage.  
- Applications: audio waveform generation, test signals, sensor emulation.

### Key Components

**RVMYTH CPU**

- 32-bit RISC-V core  
- Pipelined execution for throughput

**PLL (Phase-Locked Loop)**

- Phase Detector, Loop Filter, VCO, Frequency Divider  
- Synchronizes clocks for CPU and DAC
  
<img width="885" height="535" alt="image" src="https://github.com/user-attachments/assets/768dcabf-9488-47f9-9fc8-00eba4523115" />


**DAC (Digital-to-Analog Converter)**

- R-2R ladder for efficient design  
- Generates high-resolution analog output

### Educational Use-Cases

- RISC-V programming experiments  
- PLL design and clock management  
- Digital-to-analog conversion projects  
- Audio/video output prototypes

</details>

## Conclusion

The **VSDBabySoC** project demonstrates how a **compact SoC** can integrate digital computation and analog interfacing on a single chip.

**Key Takeaways:**

- Combines **RISC-V CPU, PLL, and DAC** in one minimal platform  
- Serves as an educational tool for **digital design, clock synchronization, and analog output**  
- Can be extended for small-scale **audio/video applications** or **IoT prototypes**  
- Provides a practical pathway from **RTL coding** to **physical SoC implementation**
