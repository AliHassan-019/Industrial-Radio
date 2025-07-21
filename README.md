


# Industrial Radio

<p align="center">
  <b>Solar-Powered, Wireless, Industrial Current Monitoring System</b><br>
  <i>Non-intrusive, IoT-enabled, and robust for harsh environments</i>
</p>

<p align="center">
  <a href="#features"><img src="https://img.shields.io/badge/Features-Complete-blue?style=flat-square"></a>
  <a href="#license"><img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"></a>
  <a href="#contributing"><img src="https://img.shields.io/badge/Contributions-Welcome-blueviolet?style=flat-square"></a>
</p>

---



## 📑 Table of Contents

- [🚀 Project Overview](#project-overview)
- [✨ Features](#features)
- [🏗️ System Architecture](#system-architecture)
- [🖥️ Block Diagram](#block-diagram)
- [🛠️ Hardware Details](#hardware-details)
  - [Rogowski Coil Interface](#rogowski-coil-interface)
  - [Microcontroller Unit (MCU)](#microcontroller-unit-mcu)
  - [Display Module](#display-module)
  - [Power Management](#power-management)
  - [Communication Modules](#communication-modules)
  - [Additional Components](#additional-components)
- [💾 Firmware Overview](#firmware-overview)
- [🖼️ Mechanical Design](#mechanical-design)
  - [Overall Product Design](#overall-product-design)
  - [2-Layer Mechanical Design (Front and Back Views)](#2-layer-mechanical-design-front-and-back-views)
  - [Internal Design (Device Render/Image)](#internal-design-device-renderimage)
- [🖼️ PCB Design](#pcb-design)
  - [Schematic Diagram](#schematic-diagram)
  - [Top PCB Layer](#top-pcb-layer)
  - [Bottom PCB Layer](#bottom-pcb-layer)
  - [Top 3D View](#top-3d-view)
  - [Bottom 3D View](#bottom-3d-view)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)


---


## 🚀 Project Overview

**Industrial Radio** is a next-generation, solar-powered, wireless current monitoring system designed for industrial and harsh environments. It uses a Rogowski coil for non-intrusive AC current measurement, an ESP32 microcontroller for advanced processing, and supports both LoRa and GSM for long-range, reliable data transmission. The system is ideal for:

- Remote monitoring of electrical assets
- Predictive maintenance and fault logging
- Industrial automation and energy management
- Smart grid and IoT deployments

**Key Benefits:**
- Non-intrusive, safe installation
- Wireless, long-range communication
- Solar-powered, maintenance-free operation
- Real-time data, alerts, and GPS-based event logging

---


## ✨ Features

- **Non-intrusive AC current measurement** using Rogowski coil
- **Real-time OLED display** (0.96" SSD1306)
- **Solar-powered** with LiPo battery backup
- **Long-range wireless communication** (LoRa, optional GSM)
- **GPS-based location logging**
- **Data logging and system alerts**
- **Environmental and system parameter monitoring**
- **Over-voltage and reverse polarity protection**
- **Modular, robust enclosure and PCB design**
- **Open-source firmware and hardware**

---


## 🏗️ System Architecture

The Industrial Radio system is built from the following main blocks:
- **Rogowski Coil Interface:** Senses AC current and outputs a voltage proportional to the current.
- **MCU (ESP32):** Processes sensor data, manages communication, and controls the system.
- **Display:** Shows real-time data and system status.
- **Power Management:** Solar panel, battery, charging, and voltage regulation.
- **Communication:** LoRa (RFM95) and optional GSM (SIM800L) modules.
- **Additional Components:** GPS, environmental sensors, and protection circuits.

---


## 🖥️ Block Diagram

```text
+-------------------+
|   Rogowski Coil   |
+--------+----------+
         |
         v
+-------------------+
| Integrator Circuit|
+--------+----------+
         |
         v
+-------------------+
|      ESP32 MCU    |
|  +-------------+  |
|  | LoRa Module |  |
|  | GSM Module  |  |
|  | GPS Module  |  |
|  | OLED Display|  |
+--------+----------+
         |
         v
+-------------------+
| Power Management  |
| (Solar, Battery,  |
|  Charging, Boost) |
+-------------------+
```

---


## 🛠️ Hardware Details

### Rogowski Coil Interface
- **Input:** Rogowski coil terminals
- **Integrator Circuit:** RC integrator using op-amp (e.g., TLV2372), resistor, and capacitor
- **Purpose:** Converts di/dt output to voltage proportional to current for accurate AC measurement

### Microcontroller Unit (MCU)
- **Type:** ESP32 (dual-core, WiFi, Bluetooth)
- **Functions:**
  - High-speed signal processing
  - Wireless communication (LoRa/GSM)
  - Data logging, control, and power management

### Display Module
- **Type:** 0.96" OLED (SSD1306)
- **Interface:** I2C
- **Purpose:** Real-time current, system status, alerts, and diagnostics

### Power Management
- **Solar Panel:** 5V, 100–500 mA
- **Battery:** 3.7V LiPo, 1000–1500 mAh
- **Charging Circuit:** TP4056 or CN3791
- **Voltage Regulation:** Boost converter (MT3608) for stable 5V output

### Communication Modules
- **LoRa:** RFM95 (SPI, long-range, low-power)
- **GSM (Optional):** SIM800L (UART, cellular fallback)

### Additional Components
- **GPS:** NEO-6M (UART, location for event logging)
- **Sensors:** Environmental (temperature, humidity, etc.)
- **Protection:** Diodes, fuses, TVS diodes for surge and reverse polarity

---


## 💾 Firmware Overview

- **Language:** C++ (Arduino framework for ESP32)
- **Key Libraries:**
  - Adafruit_SSD1306 (OLED display)
  - LoRa (Sandeep Mistry)
  - TinyGPS++ (GPS)
  - HTTPClient (GSM data upload)
- **Main Functions:**
  - Rogowski coil signal acquisition and integration
  - Real-time display and system status
  - LoRa/GSM data transmission
  - GPS event logging
  - Power management and deep sleep
  - Data logging and alerting

---

## Installation & Setup
1. **Hardware Assembly**
   - Connect Rogowski coil to integrator circuit
   - Connect integrator output to ESP32 ADC
   - Wire OLED, LoRa, GSM, GPS modules to ESP32
   - Connect solar panel, battery, and charging circuit
   - Ensure all protection circuits are in place
2. **Firmware Upload**
   - Install Arduino IDE and ESP32 board support
   - Install required libraries
   - Upload firmware to ESP32
3. **Configuration**
   - Set LoRa frequency and keys
   - Configure GSM APN (if used)
   - Set data logging intervals

---

## Usage
- Power on the device (solar or battery)
- OLED displays real-time current and system status
- Data is transmitted via LoRa/GSM
- GPS logs location for each event
- System enters sleep mode to save power when idle

---

## Troubleshooting
- **No Display**: Check OLED wiring and I2C address
- **No Data Transmission**: Verify LoRa/GSM module connections and configuration
- **No Power**: Check solar panel, battery, and charging circuit
- **Incorrect Readings**: Calibrate integrator circuit and check Rogowski coil orientation

---

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request. For major changes, open an issue first to discuss your ideas.

---

## License
This project is licensed under the MIT License.

---






## 🖼️ Mechanical Design

### Overall Product Design
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/over%20all%20design.png" alt="Overall Product Design" width="400"/>

A comprehensive view of the fully assembled Industrial Radio device, showing enclosure, display, and all external features as it will appear in the field.

### 2-Layer Mechanical Design (Front and Back Views)
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/2%20layer%20design.png" alt="2-Layer Mechanical Design (Front and Back Views)" width="400"/>

Front and back enclosure views, showing user interface, display, mounting, and cable entry.

### Internal Design (Device Render/Image)
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/image.png" alt="Device Render or Photograph" width="400"/>

High-quality render or photograph of the device, highlighting the internal build, connectors, and user interface. Useful for understanding internal layout and assembly.

---

## 🖼️ PCB Design

### Schematic Diagram
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/Schematics.png" alt="Schematic" width="400"/>

Complete electrical schematic, showing all interconnections, protections, and signal flow.

### Top PCB Layer
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/Top_Layer.png" alt="Top Layer" width="400"/>

Shows the top copper layer, component placement, and signal routing. Highlights analog/digital separation and EMI control.

### Bottom PCB Layer
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/Bottom_Layer.png" alt="Bottom Layer" width="400"/>

Bottom copper layer for ground fills, passives, and mechanical support. Shows return paths and low-priority routing.

### Top 3D View
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/3D_Top_View.png" alt="Top 3D View" width="400"/>

3D render of the assembled PCB from the top. Visualizes component heights, connectors, and fit.

### Bottom 3D View
<img src="https://github.com/AliHassan-019/Industrial-Radio/blob/main/Reference%20Images/3D_Bottom_View.png" alt="Bottom 3D View" width="400"/>

3D render from the bottom, showing SMD passives, vias, and mounting clearance.

---



## 📝 Mechanical Design Guide

1. **2-Layer Mechanical Design (Front and Back Views):**
   - Familiarize yourself with the device's external appearance. The front view shows the display and user-accessible features; the back view reveals mounting and cable management. Use for installation planning and enclosure fit.
2. **Internal Design (Device Render/Image):**
   - Use this render or photograph to understand the internal layout, wiring, and assembly of the device. This is helpful for troubleshooting, upgrades, and maintenance.
3. **Overall Mechanical Design:**
   - Visualize how all modules fit inside the enclosure. Check for correct positioning, wiring space, and airflow. Useful for presentations and technical documentation.

---

## 🙋‍♂️ Support & Contact

For questions, technical support, or to report issues, please open an issue on the [GitHub repository](https://github.com/AliHassan-019/Industrial-Radio) or contact the project maintainer at [Ali Hassan](mailto:alihassan.pk019@gmail.com).

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome! To contribute:

1. Fork the repository
2. Create a new branch for your feature or fix
3. Commit your changes with clear messages
4. Open a pull request describing your changes

For major changes, please open an issue first to discuss your ideas.

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <b>Thank you for using and supporting Industrial Radio!</b><br>
  <i>Empowering industrial IoT with robust, wireless, and solar-powered monitoring solutions.</i>
</p>
