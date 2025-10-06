# VSDBabySoC Project

This project focuses on designing a **compact open-source System on Chip (SoC)** using the **RVMYTH RISC-V processor core**.  
The SoC integrates a **Phase-Locked Loop (PLL)** for stable clock generation and a **10-bit Digital-to-Analog Converter (DAC)** for analog interfacing.  
The DAC allows BabySoC to convert digital outputs into analog signals, enabling interaction with analog-based devices such as mobile phones and televisions — making it possible to produce audio or video outputs.  

Built on the **Sky130 technology node**, this project provides a practical and educational platform for exploring the link between digital design and analog systems.

---

<details>
<summary>1. Understanding System on Chip (SoC)</summary>

<br>

A **System on a Chip (SoC)** is essentially a complete computer system fabricated on a single silicon chip. It integrates processing, memory, input/output, and often communication blocks — all within a compact area. This miniaturized integration helps achieve faster performance, low power consumption, and smaller device sizes.

### Core Components of an SoC

- **CPU (Central Processing Unit)**: Executes instructions, performs arithmetic operations, and manages tasks.
- **Memory**:
  - RAM stores temporary data.
  - ROM/Flash memory retains data permanently.
- **Input/Output (I/O) Interfaces**: Enable communication with external devices.
- **GPU (Graphics Processing Unit)**: Handles image/video rendering.
- **DSP (Digital Signal Processor)**: Processes signals in real-time.
- **Power Management Unit (PMU)**: Controls power distribution.
- **Connectivity & Security Units**: Wi-Fi, Bluetooth, or encryption modules.

### Advantages of SoCs

- Compact size
- Power efficiency
- High performance
- Cost efficiency
- Reliability

### Common Applications

- Smartphones & Tablets
- Wearable Devices
- IoT Systems
- Automotive Systems
- Consumer Electronics

### Popular SoCs

- Apple A-Series
- Qualcomm Snapdragon
- Samsung Exynos
- NVIDIA Tegra

### Limitations and Design Challenges

- Complex integration
- Thermal management
- Low flexibility

</details>

<details>
<summary>2. Types of SoCs</summary>

<br>

1. **Microcontroller-Based SoCs**  
   Designed for low-power and real-time operations, ideal for embedded systems and home automation.

2. **Microprocessor-Based SoCs**  
   Supports complex applications and multitasking; used in smartphones, tablets, and laptops.

3. **Application-Specific SoCs**  
   Customized for dedicated tasks such as AI, networking, or image processing.

### SoC Design Flow

Typically involves the following steps: specification → architecture → RTL design → verification → synthesis → physical design → tape-out.

</details>

<details>
<summary>3. Introduction to VSDBabySoC</summary>

<br>

The **VSDBabySoC** is a minimal yet functional RISC-V-based SoC designed for experimentation and education.  
It integrates **RVMYTH CPU**, **PLL**, and **10-bit DAC**, tested together on a single open-source platform.

### Working Principle

#### 1. Clock Setup (PLL Activation)
- PLL generates a stable and synchronized clock signal.
- Ensures DAC and RVMYTH CPU operate consistently, reducing skew and synchronization issues.

#### 2. Data Handling by RVMYTH
- RVMYTH computes data and updates internal registers.
- Generates new digital values periodically.

#### 3. Analog Output (DAC Conversion)
- DAC converts digital signals into analog form.
- Outputs can drive analog devices like TVs or audio systems.

### Components

- **RVMYTH (RISC-V Core)** – Processor executing instructions.
- **PLL (Phase-Locked Loop)** – Generates stable clocks.
- **DAC (Digital-to-Analog Converter)** – Converts digital outputs to analog.

### Phase-Locked Loop (PLL)

- Synchronizes output signal’s phase and frequency with a reference.
- Key blocks: Phase Detector, Loop Filter, VCO, Frequency Divider.

### Digital-to-Analog Converter (DAC)

- Converts binary digital data into continuous analog signals.
- Key architectures:
  - Weighted Resistor DAC
  - R-2R Ladder DAC
- In VSDBabySoC: 10-bit DAC provides high-resolution analog outputs suitable for waveform generation or audio output.

</details>

---

## Conclusion

This documentation provides an overview of **SoC concepts** and how the **VSDBabySoC** integrates core modules like **RVMYTH, PLL, and DAC**.  
It forms a strong foundation for exploring **digital design, clock management, and analog interfacing** in advanced SoC architectures.
