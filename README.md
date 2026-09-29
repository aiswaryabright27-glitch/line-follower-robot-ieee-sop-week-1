#  IR Line Following Robot

An autonomous line-following robot built for the **IEEE CASS / RAS Summer of Projects 2026** at **BMSIT**.

---

##  Overview

This robot uses two IR line sensors to detect a dark line on a light surface and an **ESP32-S3-CAM** controller to navigate the track autonomously without external control. 

This project covers practical applications in sensor calibration, motor control, hardware integration, and embedded programming.

---

##  Objectives

* Build a fully functional, autonomous line-following robot.
* Interface IR sensors with the ESP32-S3-CAM microcontroller.
* Drive DC gear motors using the **L298N motor driver** with PWM speed control.
* Implement closed-loop logic where sensor inputs directly drive physical actuators.
* Gain real-world hardware troubleshooting and debugging experience.

---

##  Hardware Components

* **Microcontroller:** ESP32-S3-CAM
* **Motor Driver:** L298N Dual H-Bridge Motor Driver
* **Sensors:** 2 × IR Line Sensor Modules (LM393 comparator-based)
* **Motors & Chassis:** 2 × DC Gear Motors, Caster Wheel, Robot Chassis
* **Power & Wiring:** 7–12V Battery Pack, Jumper Wires

---

##  How It Works

Two forward-facing IR sensors detect line contrast. The ESP32 reads these sensor states and dynamically signals the L298N driver to adjust motor direction and speed.

### Control Logic Table

| Left Sensor | Right Sensor | Robot Action |
| :---: | :---: | :--- |
| **OFF** (Light) | **OFF** (Light) | Move Straight |
| **ON** (Dark) | **OFF** (Light) | Turn Left |
| **OFF** (Light) | **ON** (Dark) | Turn Right |
| **ON** (Dark) | **ON** (Dark) | Stop |

---

##  Circuit Connections

![Circuit Connections](media/connections.jpeg)

### ESP32-S3-CAM to L298N Motor Driver

| ESP32 Pin | L298N Pin | Function |
| :---: | :---: | :--- |
| **GPIO1** | ENA | Left Motor PWM |
| **GPIO2** | IN1 | Left Motor Direction |
| **GPIO21** | IN2 | Left Motor Direction |
| **GPIO47** | ENB | Right Motor PWM |
| **GPIO48** | IN3 | Right Motor Direction |
| **GPIO41** | IN4 | Right Motor Direction |

### ESP32-S3-CAM to IR Sensors

| ESP32 Pin | Sensor Connection |
| :---: | :--- |
| **GPIO42** | Left IR Sensor Output |
| **GPIO40** | Right IR Sensor Output |
| **5V** | VCC (Both Sensors) |
| **GND** | GND (Both Sensors) |

---

##  Software & Stack

* **Language:** Embedded C / C++
* **IDE:** Arduino IDE (with ESP32 board support package)
* **Techniques:** GPIO Configuration, PWM Speed Control, Digital Signal Processing

---

## Gallery & Media

| Robot Build | Testing Setup | Final Hardware |
| :---: | :---: | :---: |
| ![Robot Photo 1](media/robo1.1.jpg) | ![Robot Photo 2](media/robo1.2.jpeg) | ![Robot Photo 3](media/robo1.3.png) |

### Demo Video
[![Watch Demo Video](https://img.shields.io/badge/Video-Watch_Demo_mp4-blue?style=for-the-badge&logo=playstation)](media/demo.mp4)

---

##  Challenges & Troubleshooting

1. **Turning Speed Tuning:** Finding the right balance between turn speed and track retention required repeated PWM tuning iterations.
2. **Surface Variations:** Rough or uneven floor textures caused erratic wheels-to-surface traction and inconsistent sensor ground clearance.
3. **Tape Detection Consistency:** Reflectivity differences across different black tape types caused occasional miss-readings.
4. **Sensor Positioning:** Height and distance spacing between the two front IR modules heavily influenced turning sensitivity.

---

## 💡Key Learnings

* Interfacing hardware modules with microcontrollers via GPIO and PWM.
* Real-world sensor calibration and adjusting threshold potentiometers.
* The critical impact of subtle physical parameters (sensor height, weight distribution) on robot stability.
* Iterative testing methodologies for quick hardware debugging.

---

##  Results & Achievements

**IEEE RAS Summer of Projects 2026 – Week 1 Winner**

Our team successfully completed the track and took 1st place in the Week 1 challenge!

| Leaderboard | Participating Teams |
| :---: | :---: |
| ![Leaderboard](media/leaderboard.jpeg) | ![Teams](media/teams.jpeg) |

### Certificate of Achievement
![Week 1 Certificate](media/week-1-certificate.jpg)

---

##  Future Improvements

* Implement **PID Control** for smoother steering adjustments instead of simple threshold logic.
* Add an array of **multi-channel IR sensors** for enhanced line tracking at higher speeds.
* Optimize power regulation for uniform motor output as battery levels decline.

---


## 📜 License

This repository is maintained for educational and demonstration purposes.
