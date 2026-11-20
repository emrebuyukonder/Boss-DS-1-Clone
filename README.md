# Boss DS-1 Distortion Clone (V1) — Deprecated

![Status](https://img.shields.io/badge/Status-Deprecated-red)
![Hardware](https://img.shields.io/badge/Hardware-PCB_Design-blue)
![Software](https://img.shields.io/badge/EDA-KiCad-green)

> [!WARNING]
> **This is the first version of the project and it has known design issues. Please do not use these files to build a pedal.**
>
> A redesigned and improved version is available here: **[Boss-DS-1-Clone-V2](https://github.com/emrebuyukonder/Boss-DS-1-Clone-V2)**
>
> This repository is kept online only as a record of the project's development history.

## Why V1 Is Deprecated

V1 was my first pass at this pedal. While building and testing it, I found several design problems that were fixed in V2. If you are planning to build this pedal, use the V2 files instead.

### Known Issues in V1

1. **Through-hole pads too small for wiring:** The potentiometers and jacks are wired directly to the PCB, but the selected through-hole footprints have holes that are too narrow for the hookup wire. Getting the wires into the pads during assembly is very difficult.
2. **Slide switch instead of a 3PDT footswitch:** At the time of the V1 build, 3PDT footswitches were out of stock locally, so a 6-pin slide switch was used. As a result, the pedal cannot be switched on and off with your foot, and since a 6-pin switch has no spare pole, there is no status LED to show when the effect is engaged.
3. **Reversed diode in the power supply section:** The diode in the power supply block is drawn backwards in the schematic, and the error carries over to the PCB layout. During assembly the diode had to be installed in the opposite orientation to the silkscreen marking.
4. **Mounting holes are not grounded:** The PCB mounting hole footprints have no GND pad, so the board cannot be grounded to a metal enclosure through its mounting screws. This means the enclosure does not act as a proper shield (Faraday cage) around the circuit.

### What Changed in V2

All of the issues above are fixed in V2:

* **Modular, solder-free off-board wiring (fixes #1):** All off-board parts (footswitch, potentiometers, audio jacks) connect to the PCB through JST connectors, so the board can be installed, serviced or modified without desoldering.
* **3PDT footswitch with status LED (fixes #2):** V2 uses a 3PDT 9-pin latching footswitch for true bypass, with a dedicated pole driving the status LED. A lug-by-lug wiring diagram is included.
* **Corrected power supply diode (fixes #3):** The diode orientation is corrected in both the schematic and the PCB layout.
* **Grounded mounting holes (fixes #4):** The mounting hole footprints include GND pads, so the PCB is grounded to a metal enclosure for proper shielding.

V2 also adds:

* **Enclosure fitting in Fusion 360:** PCB dimensions and component placement were checked against the enclosure before manufacturing.
* **Circuit simulation:** The gain, tone/level and transistor boost stages were simulated before the board was ordered (results are included in the V2 repository).

---

## Original V1 Documentation (Archived)

> [!NOTE]
> Everything below is the original V1 documentation, kept unchanged for reference. It describes the V1 design, including the issues listed above. The 3PDT footswitch and status LED mentioned below were the original plan; the actual V1 build used a 6-pin slide switch without an LED (see Known Issue #2).

### About The Project

This repository contains the schematic, PCB design files, and build documentation for a custom-built clone of the legendary Boss DS-1 Distortion pedal. Designed from the ground up using **KiCad**, this project aims to faithfully recreate the iconic hard-clipping distortion tone while implementing modern hardware practices such as True Bypass switching and optimized component routing.

### Key Features & Modifications

While the core audio path remains true to the original DS-1 architecture, several mechanical and component-level modifications were made based on the local availability of certain original components and hardware.

* **Custom Transistor Selection:** The original BC549C transistors were substituted with **JC2N3904S49 (NPN)** transistors for the input buffer (Q1), gain boost (Q2), and output buffer (Q3) stages. The PCB footprints were carefully matched to accommodate the E-B-C pinout of the 2N3904.
* **True Bypass Switching:** Unlike the original Boss buffered bypass, this build utilizes a **3PDT 9-Pin Latching Footswitch**. This ensures zero tone coloration when the pedal is disengaged and includes an independent pole for the status LED.
* **Smart Power Management:** Integrated a Stereo Input Jack to act as a ground-shunt switch. The 9V battery is completely disconnected from the circuit when the input cable is unplugged, preserving battery life.
* **Capacitor Accuracy:** High-quality film and ceramic capacitors are used throughout the tone stack and filtering stages (e.g., precise 100pF and 220pF ceramics for RF filtering in the op-amp feedback loop).

### Tools & Technologies Used

* **EDA Software:** KiCad (Schematic Capture & PCB Layout)
* **Testing & Measurement:** UNI-T UT33D+ Digital Multimeter
* **Audio Components:** 1/4" Mono/Stereo Jacks, Custom PCB.

### Hardware Wiring Guide

Proper off-board wiring is critical for a noise-free pedal. Here is the standard implementation used in this build:

* **Input Jack (Stereo):**
    * *Tip:* Routed to 3PDT Switch (Input).
    * *Ring:* Connected to the 9V Battery Negative (Black wire).
    * *Sleeve:* Connected to System Ground (Star Grounding).
* **Output Jack (Mono):**
    * *Tip:* Routed from 3PDT Switch (Output).
    * *Sleeve:* Connected to System Ground.

## Author

Designed and built by **Erdoğan Emre Büyükönder** (Music Producer / DJ).

As an Electrical-Electronics Engineering student and a music producer, this project bridges the gap between theoretical circuit analysis and practical, stage-ready audio equipment.

---
*Note: The "Boss" and "DS-1" names are trademarks of Roland Corporation. This project is strictly for educational purposes and personal use.*
