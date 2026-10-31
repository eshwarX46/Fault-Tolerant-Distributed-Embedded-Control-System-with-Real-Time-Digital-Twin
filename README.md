# 🚀 Fault-Tolerant Distributed Embedded Control System

**Four-Node CAN Network with Real-Time Digital Twin Visualization**

![Controllers](https://img.shields.io/badge/Controllers-Arduino%20%7C%20ESP32-blue)
![Communication](https://img.shields.io/badge/Communication-CAN%20Bus-orange)
![Bitrate](https://img.shields.io/badge/CAN%20Bitrate-250%20kbps-success)
![Display](https://img.shields.io/badge/Display-2.8%22%20TFT-purple)

---

## 📌 Project Overview

A four-node distributed embedded control system using **CAN bus communication at 250 kbps**, with sensor acquisition, actuator control, supervision, and real-time **Digital Twin visualization on a TFT display**.

| Node | Controller | Role | Connected devices |
| --- | --- | --- | --- |
| Node 1 | Arduino UNO | Sensor hub | MPU6050, ACS712, two DS18B20 sensors |
| Node 2 | Arduino Nano | Actuator controller | L298N motor driver, DC motor, two relays |
| Node 3 | ESP32 | Supervisor | LEDs, buzzer, reset button |
| Node 4 | ESP32 | Gateway and visualization | 2.8-inch TFT display |

## 📸 Project Image

<img src="https://github.com/user-attachments/assets/27eca356-02b4-4b28-945e-a14aa29a6754" alt="Four-node CAN-based distributed embedded control system prototype" width="900" />

## 📡 CAN Protocol

**Bus bitrate:** 250 kbps.

| CAN ID | Sender | Payload | Transmission interval |
| --- | --- | --- | --- |
| `0x101` | Node 1 | Temperature 1, temperature 2, current, X-axis acceleration | Every 2 s |
| `0x200` | Node 2 | Motor speed, direction, relay 1 state, relay 2 state | Every 2 s |
| `0x303` | Node 3 | Heartbeat | Every 2 s |
| `0x304` | Node 4 | Heartbeat | Every 2 s |
| `0x401` | Node 3 | Commands to Node 2 | Every 10 s |

### Command Codes

Command codes below are shown in decimal.

| Code | Command | Value |
| --- | --- | --- |
| `10` | Set motor speed | `0–255` |
| `12` | Set motor direction | `0` = reverse; `1` = forward |
| `13` | Control relay 1 | `0` = OFF; `1` = ON |
| `14` | Control relay 2 | `0` = OFF; `1` = ON |
| `20` | Emergency stop | `0` |
| `21` | Clear emergency | `0` |

## 🔌 CAN Bus Wiring

### Wire Colors

The following wire colors identify the connections used in this prototype.

| Connection | Wire color |
| --- | --- |
| CAN H | 🟡 Yellow |
| CAN L | 🟢 Green |
| GND | ⚫ Black |

### Bus Termination

Use a **120 Ω termination resistor at each physical end of the CAN bus**. In the documented layout, Node 1 and Node 4 are the end nodes.

| Node | 120 Ω termination |
| --- | --- |
| Node 1 | Enabled |
| Node 2 | Disabled |
| Node 3 | Disabled |
| Node 4 | Enabled |

## 🛠️ Hardware Components

| Component | Quantity |
| --- | ---: |
| Arduino UNO R3 | 1 |
| Arduino Nano | 1 |
| ESP32 development board | 2 |
| MCP2515 CAN module | 2 |
| TJA1050 CAN transceiver | 2 |
| MPU6050 accelerometer | 1 |
| ACS712 5 A current sensor | 1 |
| DS18B20 temperature sensor | 2 |
| L298N motor driver | 1 |
| 300 RPM DC motor | 1 |
| 5 V two-channel relay module | 1 |
| 2.8-inch SPI TFT display | 1 |
| 12 V, 2 A adapter | 1 |
| LM2596 buck converter | 1 |

## 💻 Software Setup

### Required Libraries

Install the libraries required by each node's sketch.

| Library or header | Purpose |
| --- | --- |
| `CAN.h` — Sandeep Mistry | ESP32 CAN communication |
| `TFT_eSPI` — Bodmer | TFT display interface |
| `MPU6050` — Electronic Cats | Accelerometer interface |
| `OneWire` | OneWire communication for DS18B20 sensors |
| `DallasTemperature` — Miles Burton and contributors | DS18B20 temperature readings |
| MCP2515 library matching the sketch's header and API | External CAN controller interface on Arduino nodes |

**MCP2515 library selection:** Match the library to the firmware's `#include` statement. A sketch using `mcp2515.h` needs a library that supplies that header; do not assume it is interchangeable with a library using `mcp_can.h`.

## 🔧 Troubleshooting

| Problem | Checks |
| --- | --- |
| CAN bus is not communicating | Check CAN H, CAN L, common ground, matching bitrate, and termination at the two physical ends. |
| TFT display is blank | Check display power and the CS, DC, RST, MOSI, and SCK connections against the display configuration. |
| DS18B20 readings are missing | Check sensor wiring and the 4.7 kΩ pull-up on the OneWire data line. |
| Other sensor readings are missing | Check the affected sensor's power, wiring, and interface configuration. |
| Motor is not moving | Check the 12 V motor supply, common ground, driver connections, and commanded motor state. |

## 🎥 Demonstration Video

[▶ Watch the project demonstration on YouTube](https://youtu.be/R3NE2LGSu5U)

## 👤 Author

**Eshwar Prasad Y**

## 📧 Contact

- **Email:** [eshwargowda313@gmail.com](mailto:eshwargowda313@gmail.com)
- **LinkedIn:** [Eshwar Prasad Y](https://www.linkedin.com/in/eshwar-prasad-y-a3043b370/)

## 🙏 Acknowledgments

Thanks to the open-source library developers and communities supporting this project.

---

**Arduino UNO · Arduino Nano · ESP32 · CAN Bus · Distributed Control · TFT Visualization**
