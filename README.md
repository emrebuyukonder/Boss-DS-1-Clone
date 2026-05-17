# Boss DS-1 Distortion Clone (Custom Build)

![Hardware](https://img.shields.io/badge/Hardware-PCB_Design-blue)
![Software](https://img.shields.io/badge/EDA-KiCad-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## About The Project

This repository contains the schematic, PCB design files, and build documentation for a custom-built clone of the legendary Boss DS-1 Distortion pedal. Designed from the ground up using **KiCad**, this project aims to faithfully recreate the iconic hard-clipping distortion tone while implementing modern hardware practices such as True Bypass switching and optimized component routing.

## Key Features & Modifications

While the core audio path remains true to the original DS-1 architecture, several mechanical and component-level modifications were made based on the local availability of certain original components and hardware.

* **Custom Transistor Selection:** The original BC549C transistors were substituted with **JC2N3904S49 (NPN)** transistors for the input buffer (Q1), gain boost (Q2), and output buffer (Q3) stages. The PCB footprints were carefully matched to accommodate the E-B-C pinout of the 2N3904.
* **True Bypass Switching:** Unlike the original Boss buffered bypass, this build utilizes a **3PDT 9-Pin Latching Footswitch**. This ensures zero tone coloration when the pedal is disengaged and includes an independent pole for the status LED.
* **Smart Power Management:** Integrated a Stereo Input Jack to act as a ground-shunt switch. The 9V battery is completely disconnected from the circuit when the input cable is unplugged, preserving battery life.
* **Capacitor Accuracy:** High-quality film and ceramic capacitors are used throughout the tone stack and filtering stages (e.g., precise 100pF and 220pF ceramics for RF filtering in the op-amp feedback loop).

## Tools & Technologies Used

* **EDA Software:** KiCad (Schematic Capture & PCB Layout)
* **Testing & Measurement:** UNI-T UT33D+ Digital Multimeter
* **Audio Components:** 1/4" Mono/Stereo Jacks, Custom PCB.

## Hardware Wiring Guide

Proper off-board wiring is critical for a noise-free pedal. Here is the standard implementation used in this build:

* **Input Jack (Stereo):**
   * *Tip:* Routed to 3PDT Switch (Input).
    * *Ring:* Connected to the 9V Battery Negative (Black wire).
    * *Sleeve:* Connected to System Ground (Star Grounding).
* **Output Jack (Mono):**
    * *Tip:* Routed from 3PDT Switch (Output).
    * *Sleeve:* Connected to System Ground.

## Author

Designed and built by **Erdoğan Emre Büyükönder** (Music Producer / Composer under the pseudonym *Magnus Dux*). 

As an Electrical-Electronics Engineering student and a music producer, this project bridges the gap between theoretical circuit analysis and practical, stage-ready audio equipment.

---
*Note: The "Boss" and "DS-1" names are trademarks of Roland Corporation. This project is strictly for educational purposes and personal use.*
