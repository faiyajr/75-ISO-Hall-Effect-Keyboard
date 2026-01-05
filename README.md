# 75-ISO-Hall-Effect-Keyboard
75% ISO Hall-Effect Keyboard (Custom STM32 Design)

This project started as an exploration into how far a keyboard can be pushed when you treat it like a real embedded system. Instead of relying on off-the-shelf controllers and digital switches, this keyboard is designed from the ground up around analog Hall-effect sensing, clean mixed-signal hardware, and firmware-driven behavior.

The result is a fully custom 75% ISO Hall-effect mechanical keyboard built around an STM32 microcontroller, with per-key analog measurement, addressable RGB lighting, a rotary encoder, OLED support, and a custom-designed case. The project emphasizes correct power design, signal integrity, and manufacturability, and serves as both a functional keyboard and a deep embedded hardware learning platform.

Features

75% ISO layout

Hall-effect key sensing (contactless, analog)

STM32F303 microcontroller (ARM Cortex-M4)

Per-key analog position measurement

SK6812 addressable RGB lighting

Rotary encoder with push switch

I²C OLED display support

USB connectivity via Unified Daughterboard (UDB)

Custom-designed keyboard case

ESD-protected external interfaces

Mixed-signal power architecture (separate digital and analog rails)

System Overview
Microcontroller

STM32F303CBT6

External crystal oscillator

ADC for Hall-effect sensors

Timers for RGB signal generation

SWD programming and debugging

Hall-Effect Key Sensing

Linear Hall-effect sensor per key

74HC4067 analog multiplexers for channel expansion

ADC-based scanning by cycling multiplexer select lines

Clean analog supply (VDDA) for stable measurements

RGB Lighting

SK6812 addressable RGB LEDs

Powered from the 5 V USB rail

Individual decoupling capacitors per LED

MOSFET power gating to fully disable RGB and reduce idle power

MCU-driven data line with timer-assisted waveform generation

Input Devices

Rotary encoder

Quadrature A/B outputs

Integrated push button

DIP switch for hardware configuration and mode selection

Display

I²C OLED header

SDA / SCL

3.3 V logic

Intended for status information, layers, or debugging output

Power Architecture

USB VBUS (5 V) input

LDO regulator generating 3.3 V

Separate power domains:

VDD for digital MCU logic

VDDA for ADC, DAC, and analog peripherals

Ferrite bead isolation between digital and analog rails

Bulk and decoupling capacitors placed per STM32 datasheet recommendations

Signal Integrity and Protection

ESD protection diode arrays on:

USB D+ / D−

SWD programming interface

I²C bus

Series resistors and jumpers for signal conditioning

Solid ground plane with via stitching

Dedicated power planes for GND and 3.3 V

Interfaces

USB 2.0 Full-Speed via Unified Daughterboard

SWD header for programming and debugging

I²C header for OLED display

Modular, hierarchical schematic structure

Mechanical Design

Custom keyboard case designed specifically for this PCB

Supports:

75% ISO layout

Rotary encoder

OLED display window

PCB mounting holes matched to case geometry

Fiducials and tooling holes included for manufacturing and assembly

Firmware Status

Planned and in progress:

ADC-based Hall sensor scanning

Per-key calibration and adjustable actuation points

RGB control and power management

Encoder and OLED integration

USB HID keyboard firmware

Manufacturing Notes

Designed for standard PCB assembly (JLCPCB-compatible)

SK6812 LEDs powered from 5 V rail

Proper decoupling and power-plane usage

ESD protection on all user-accessible interfaces

Modular schematic organization for future revisions

Project Goals

Apply mixed-signal PCB design best practices

Implement reliable analog Hall-effect key sensing

Build a complete custom keyboard hardware ecosystem

Emphasize clean power, signal integrity, and manufacturability

Serve as a strong hardware and embedded systems portfolio project

License

Open-source hardware project.
License to be added.
