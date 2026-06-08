

<p align="center">
  <img width="300" height="300" alt="AnyScan209 Icon" src="https://github.com/user-attachments/assets/1579986b-01d5-437d-9a16-009149290f95" />
</p>
 


# 🛰️ AnyScan209 — Geophysical 2D/3D Mapping Software


### 👨‍💻 Developer: Saeid Moghadam


**AnyScan209** is an advanced, independent geophysical software utility designed and developed by **Saeid Moghadam**. This professional-grade Android application is engineered to transform raw sensor data into real-time **2D and 3D subsurface visualization maps**, providing high-performance rendering for independent researchers, geologists, and exploration specialists worldwide.

Highly optimized for geophysical surveying, ground scanning, mineral exploration, and environmental mapping, AnyScan209 delivers precise data visualization without the need for expensive proprietary platforms.

---

## 🌐 Dual Operating Modes

### 1. Internal Magnetic Sensor Mode
* **Hardware-Free Scanning:** Utilizes your smartphone's built-in magnetometer to monitor, record, and map localized magnetic fields instantly.
* **Smart Isolation:** Perfect for quick field trials, baseline testing, and learning the scanning grid logic.

### 2. External Sensor Mode (Hardware-Ready)
* **Microcontroller Integration:** Receives raw analog or digital data packets (ranging from `0 to 1024`) via Bluetooth from external hardware (e.g., AVR/ATmega chips or dedicated magnetometer modules).
* **Versatile Data Processing:** Can visualize magnetic field strength, temperature, altitude, metal detection signals, or any telemetry data.

---

## 🛠️ Key Features & Architecture

* **Advanced Project Management:** Seamlessly create new exploration grids, organize scanning tasks, or open/analyze previously saved databases.
* **Real-Time 3D Rendering Page:** The core interface of the app, capable of generating immediate 3D surface topographical graphs and color-coded anomaly maps as you walk the grid.
* **Flexible Configuration & Color Theory:** Toggle between sensor modes, customize color gradients for better stratigraphy contrast, and tweak scanning steps to match your field environment.
* **Open-Source Initiative:** Built with transparency in mind, ensuring fast runtime execution, clean UI layout, and stable navigation.

---

## 🚀 Quick Start Guide

### How to Start a New Project:
1. **Define Your Grid:** Enter your desired scan size by setting the **Length** and **Width** (Steps per Line / Total Lines).
2. **Name Your Project:** Provide a unique filename to initialize the local storage database.
3. **Initialize:** Tap the **"Create / New"** icon to build your grid.
4. **Navigate:** Use the yellow back icon (or system back navigation) to jump directly into the active **Scan Page**.

### Bluetooth Operations (External Mode):
* **Connect:** Tap the **Bluetooth icon** to scan, discover, and pair with your external hardware module.
* **Disconnect/Reset:** Long-press the **Bluetooth icon** to safely drop the current connection or reset the serial stream.
* **Automated Stepping:** Each valid data packet received from your hardware automatically triggers a data point capture and advances the scanner one step forward on the grid.

---

## 🔐 Required Permissions
To ensure absolute stability, please grant the following permissions on the first launch:
* **Storage Access:** For saving structured project files, exporting maps, and reading database logs.
* **Bluetooth & Location:** Required by Android core layout to discover and connect to external hardware modules stably.

---

## 💡 Expert Operator Tips

> ⚠️ **Hardware Limitation:** Some smartphone models do not possess an internal magnetometer sensor. On these devices, AnyScan209 will automatically default to *External Sensor Mode*.

> 🎯 **Field Tip:** When using the *Internal Sensor Mode*, mount your smartphone on a **non-magnetic selfie stick** or fiberglass rod to isolate the internal sensor from your hand's interference. You can also pair a cheap Bluetooth remote shutter to trigger each scan step manually and wirelessly!

---

## 📥 Download AnyScan209

You can download the official, secure, and production-ready versions of AnyScan209 from the trusted distribution channels below:

* [Download via Uptodown](https://anyscan209.en.uptodown.com/android) 🚀
* [Download via APKPure](https://apkpure.com/anyscan209/any.scan_209/download/1.86) 📱

---

## ⚖️ License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**. 
Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications under the same license. Copyright and license notices must be preserved.

*Read the full [LICENSE](LICENSE) file for more details.*
