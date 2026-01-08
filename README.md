# ESP32 IoT ECG Monitor

This project implements a standalone IoT-enabled ECG monitoring system using an ESP32 microcontroller. The system features Ag/AgCl electrodes to collect cardiac data and the waveform is displayed on an OLED display. Using the Blynk IoT platform, the waveform and the BPM is shown on a smartphone dashboard. 

The system is battery powered using a 3.7 V lithium-ion cell and a battery shield that amplifies the power to 5 V. 

---

## Project Features

- Real-time ECG waveform acquisition
- Heart-rate (BPM) calculation using R–R interval detection
- OLED display to view the waveform
- Wi-Fi connectivity using the ESP32
- ECG/BPM visualization through Blynk
  
---

## Power Architecture

The system is powered by a 3.7 V lithium-ion battery connected to a battery shield that boosts the voltage to 5 V for the ESP32. The ESP32’s onboard regulator supplies 3.3 V to the other components.

| Voltage | Devices Powered |
|-------|----------------|
| 3.7 V | Li-ion battery |
| 5 V | ESP32 input via battery shield boost converter |
| 3.3 V | AD8232 ECG module, OLED display |
| GND | Common reference for all modules |

---

## System Overview

- **ESP32 Microcontroller**
  - ECG acquisition and processes the cardiac activity
  - Performs R-peak detection and BPM calculation
  - Wi-Fi communication and streams data to Blynk
  - Supplies regulated 3.3 V power to all peripherals
 
- **Ag/AgCl Electrodes**
  - RA, LA, LL
  - Forms Einthoven's Triangle

- **AD8232 ECG Analog Front End**
  - Amplifies and filters low-amplitude cardiac signals

- **OLED Display (SSD1306)**
  - I²C controlled graphical display
  - Displays real time ECG waveform
 
- **Buzzer**
  - Indicates successful system power-up

- **Blynk IoT Platform**
  - Push notifications for abnormal BPM to user
  - Displays ECG waveform and BPM

---

## Cloud & App Configuration (Blynk)

### Datastreams

| Datastream | Virtual Pin | Type | Range |
|-----------|------------|------|-------|
| BPM | V0 | Integer | 1–160 |
| ECG | V1 | Integer | 0–4095 |

### App Widgets

- Gauge → BPM (V0)
- Label → BPM (V0)
- SuperChart → ECG waveform (V1)

---

## Pin Mapping

### ESP32

| Signal | GPIO |
|------|------|
| ECG Analog Input | GPIO 34 |
| Buzzer Output | GPIO 25 |
| OLED SDA | GPIO 21 |
| OLED SCL | GPIO 22 |
| 3.3 V | 3V3 |
| GND | GND |

### AD8232 ECG Module

| Module Pin | Connection |
|-----------|------------|
| +VS | 3.3 V |
| GND | GND |
| SIG | GPIO 34 |

---

## Pictures

**Version that incorporates perforated board and significantly more solder fumes is currently being made. Enjoy the breadboard prototype in the meantime.**

---

## Final Comments

- Not designed for clinical use. Cheap electronic parts from Amazon cannot replace the real ECG monitors :(

