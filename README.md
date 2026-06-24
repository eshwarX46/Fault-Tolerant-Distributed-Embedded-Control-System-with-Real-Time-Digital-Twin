
# 🚀 Fault-Tolerant Distributed Embedded Control System with Real-Time Digital Twin

## 📌 Project Overview

A 4-node fault-tolerant distributed embedded control system using **CAN bus** communication at **250 KBPS** with real-time **Digital Twin** visualization on a TFT display.

- **Node 1 (Arduino UNO)** - Sensor Hub (MPU6050, ACS712, 2xDS18B20)
- **Node 2 (Arduino Nano)** - Actuator Controller (L298N Motor, 2xRelays)
- **Node 3 (ESP32)** - Supervisor (LEDs, Buzzer, Reset Button)
- **Node 4 (ESP32)** - Gateway + 2.8" TFT Display

---

## 📡 CAN Protocol

| CAN ID | Sender | Data | Frequency |
|--------|--------|------|-----------|
| `0x101` | Node 1 | Temp1, Temp2, Current, AccelX | Every 2s |
| `0x200` | Node 2 | Speed, Direction, Relay1, Relay2 | Every 2s |
| `0x303` | Node 3 | Heartbeat | Every 2s |
| `0x304` | Node 4 | Heartbeat | Every 2s |
| `0x401` | Node 3 | Commands to Node 2 | Every 10s |

### Command Codes

| Code | Command | Value |
|------|---------|-------|
| 10 | Set Motor Speed | 0-255 |
| 12 | Set Direction | 0=Reverse, 1=Forward |
| 13 | Relay 1 | 0=OFF, 1=ON |
| 14 | Relay 2 | 0=OFF, 1=ON |
| 20 | Emergency Stop | 0 |
| 21 | Clear Emergency | 0 |

---

## 🔌 Pin Connections

### CAN Bus (All Nodes)

| Wire | Color |
|------|-------|
| CAN H | 🟡 Yellow |
| CAN L | 🟢 Green |
| GND | ⚫ Black |

### Termination

| Node | 120Ω |
|------|------|
| Node 1 | ✅ ON |
| Node 2 | ❌ OFF |
| Node 3 | ❌ OFF |
| Node 4 | ✅ ON |

---

## 🛠️ Hardware Components

| Component | Quantity |
|-----------|----------|
| Arduino UNO R3 | 1 |
| Arduino Nano | 1 |
| ESP32 Dev Board | 2 |
| MCP2515 CAN Module | 2 |
| TJA1050 CAN Transceiver | 2 |
| MPU6050 Accelerometer | 1 |
| ACS712 5A Current Sensor | 1 |
| DS18B20 Temperature Sensor | 2 |
| L298N Motor Driver | 1 |
| 300 RPM DC Motor | 1 |
| 5V 2-Channel Relay | 1 |
| 2.8" SPI TFT Display | 1 |
| 12V 2A Adapter | 1 |
| LM2596 Buck Converter | 1 |

---

## 💻 Software Setup

### Required Libraries
1. CAN.h by Sandeep Mistry

2. TFT_eSPI by Bodmer

3. MPU6050 by Electronic Cats

4. OneWire by Jim Studt

5. DallasTemperature by Miles Burton

6. mcp2515.h by Cory J. Fowler

---

## 🔧 Troubleshooting

| Problem | Solution |
|---------|----------|
| CAN Bus not working | Check 120Ω termination resistors |
| TFT display blank | Check CS, DC, RST, MOSI, SCK |
| No sensor readings | Check 4.7kΩ pull-up resistors |
| Motor not moving | Check 12V power supply |

---

##  Demonstration Video
https://youtu.be/ZFuNHuojE9w

---
## 👤 Author

**Eshwar Prasad Y**  

---

## 🙏 Acknowledgments

- Project Guide for guidance
- Open-source libraries and communities

---

## 📧 Contact

Email:eshwargowda313@gmail.com  
LinkedIn: linkedin.com/in/eshwar-prasad-y-a3043b370

---
