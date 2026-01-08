# 75% ISO Hall-Effect Keyboard (Custom STM32 Design)
## Sponsor — PCBWay

This project was proudly sponsored by **PCBWay**, who provided free, high-quality PCBs for fabrication.

PCBWay made the entire process smooth and stress-free—from uploading designs to receiving professionally manufactured boards. Fast turnaround times, clear DFM feedback, and excellent board quality made it easy to iterate quickly and focus on the engineering.

If you're building hardware projects, prototyping PCBs, or refining a design, I highly recommend checking them out.

🔗 https://www.pcbway.com

This project started as an exploration into how far a keyboard can be pushed when it is treated like a real embedded system. Instead of relying on off-the-shelf controllers and digital switches, this keyboard is designed from the ground up around analog Hall-effect sensing, clean mixed-signal hardware, and firmware-driven behavior.

The result is a fully custom **75% ISO Hall-effect mechanical keyboard** built around an **STM32 microcontroller**, with per-key analog measurement, addressable RGB lighting, a rotary encoder, OLED support, and a **custom-designed case**. The project emphasizes correct power design, signal integrity, and manufacturability, and serves as both a functional keyboard and a deep embedded hardware learning platform.

---

## Features

- 75% ISO layout  
- Hall-effect key sensing (contactless, analog)  
- STM32F303 microcontroller (ARM Cortex-M4)  
- Per-key analog position measurement  
- SK6812 addressable RGB lighting  
- Rotary encoder with push switch  
- I²C OLED display support  
- USB connectivity via Unified Daughterboard (UDB)  
- Custom-designed keyboard case  
- ESD-protected external interfaces  
- Mixed-signal power architecture (separate digital and analog rails)

---

## System Overview

### Microcontroller
- STM32F303CBT6  
  - External crystal oscillator  
  - ADC for Hall-effect sensors  
  - Timers for RGB signal generation  
  - SWD programming and debugging  

### Hall-Effect Key Sensing
- Linear Hall-effect sensor per key  
- 74HC4067 analog multiplexers for channel expansion  
- ADC-based scanning by cycling multiplexer select lines  
- Clean analog supply (VDDA) for stable measurements  

### RGB Lighting
- SK6812 addressable RGB LEDs  
- Powered from the 5 V USB rail  
- Individual decoupling capacitors per LED  
- MOSFET power gating to fully disable RGB and reduce idle power  
- MCU-driven data line with timer-assisted waveform generation  

### Input Devices
- Rotary encoder  
  - Quadrature A/B outputs  
  - Integrated push button  
- DIP switch for hardware configuration and mode selection  

### Display
- I²C OLED header  
  - SDA / SCL  
  - 3.3 V logic  
- Intended for status information, layers, or debugging output  

---

## Power Architecture

- USB VBUS (5 V) input  
- LDO regulator generating 3.3 V  
- Separate power domains:
  - VDD for digital MCU logic  
  - VDDA for ADC, DAC, and analog peripherals  
- Ferrite bead isolation between digital and analog rails  
- Bulk and decoupling capacitors placed per STM32 datasheet recommendations  

---

## Signal Integrity and Protection

- ESD protection diode arrays on:
  - USB D+ / D−  
  - SWD programming interface  
  - I²C bus  
- Series resistors and jumpers for signal conditioning  
- Solid ground plane with via stitching  
- Dedicated power planes for GND and 3.3 V  

---

## Interfaces

- USB 2.0 Full-Speed via Unified Daughterboard  
- SWD header for programming and debugging  
- I²C header for OLED display  
- Modular, hierarchical schematic structure  

---

## Mechanical Design

- Custom keyboard case designed specifically for this PCB  
- Supports:
  - 75% ISO layout  
  - Rotary encoder  
  - OLED display window  
- PCB mounting holes matched to case geometry  
- Fiducials and tooling holes included for manufacturing and assembly  

---

## Firmware Link and Unified Daughterboard
- Analog Hall-effect sensors supporting adjustable actuation depth and rapid-trigger behavior
- Individually addressable per-key RGB lighting
- USB interface implemented through a [Unified Daughterboard](https://unified-daughterboard.github.io/#/)
- STM32-based embedded control platform
- Onboard buzzer for feedback and alerts
- 128×32 OLED display for status and diagnostics
- Rotary encoder with push-button input
- Firmware built on [QMK](https://github.com/RephlexZero/qmk_firmware/tree/adc_testing)


