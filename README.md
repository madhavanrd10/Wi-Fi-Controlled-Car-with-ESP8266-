# Wi-Fi-Controlled-Car-with-ESP8266-

# 🚗 Wi-Fi Controlled Car with ESP8266 & L298N

A lightweight, browser-controlled robotic car powered by an ESP8266 microcontroller and L298N motor driver.  
Control directions and speed seamlessly over a local Wi-Fi access point — no external server, no cloud latency.

---

## 📦 Components

| Component        | Details / Example                             |
| ---------------- | ---------------------------------------------- |
| ESP8266 Board    | NodeMCU or similar                            |
| Motor Driver     | L298N Dual H-Bridge                            |
| Motors           | 2 or 4 DC motors (geared recommended)         |
| Power Supply     | Battery pack (6V–12V, depends on motors)      |
| Smartphone       | Acts as remote control via web browser       |
| Wires & Chassis  | Standard robot car frame & jumper wires      |

---

## ⚙ Features

✅ ESP8266 in AP mode — no router needed  
✅ Control forward, backward, left, right, diagonal moves  
✅ Real-time speed control (0–9 levels)  
✅ Simple HTTP GET commands for control  
✅ Fully browser-controlled: no mobile app required

---

## 🧩 Pin Mapping (ESP8266 ➜ L298N)

| Function         | ESP8266 Pin (GPIO) | L298N Pin                |
| ---------------- | -----------------: | -----------------------: |
| ENA (Right motors speed) | GPIO14 (D5) | ENA |
| ENB (Left motors speed)  | GPIO12 (D6) | ENB |
| IN1 (Right motor dir 1)  | GPIO15 (D8) | IN1 |
| IN2 (Right motor dir 2)  | GPIO13 (D7) | IN2 |
| IN3 (Left motor dir 1)   | GPIO2 (D4)  | IN3 |
| IN4 (Left motor dir 2)   | GPIO0 (D3)  | IN4 |

---

## 📡 How It Works

- ESP8266 creates a Wi-Fi access point named **`GABY`**.
- A built-in HTTP server listens on port `80`.
- Phone connects directly to this AP.
- Send commands via HTTP GET requests, e.g.:

| Command        | HTTP GET `?State=` | Action                        |
| -------------- | -----------------: | ----------------------------: |
| Forward        | `F`                | Go forward                    |
| Backward       | `B`                | Go backward                   |
| Left           | `L`                | Turn left                     |
| Right          | `R`                | Turn right                    |
| Stop           | `S`                | Stop motors                   |
| Speed 0–9      | `0` to `9`         | Adjust speed (400–1023 PWM)   |

Example:
http://192.168.4.1/?State=F
