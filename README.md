# 🚗 STM32 Obstacle Avoidance & Path-Following Robot

An autonomous mobile robot built using the STM32F103C8T6 microcontroller that combines **line following** and **obstacle avoidance** in a single system. The robot intelligently switches between behaviors to navigate safely and efficiently in dynamic environments.

---

## 🧠 Overview

This project implements a hybrid navigation system:

- **Path Following Mode** → Uses IR sensors to track a line
- **Obstacle Avoidance Mode** → Uses an ultrasonic sensor to detect and react to obstacles

The robot continuously prioritizes obstacle detection over path following to ensure safe operation.

---

## ⚙️ Features

- 🚦 Dual-mode navigation (Line Following + Obstacle Avoidance)
- 📏 Real-time distance measurement using ultrasonic sensor
- 🔍 Line tracking using IR sensors
- ⚡ PWM motor control using Timer 3
- 🧮 PID-based speed adjustment for obstacle handling
- 🔌 Direct register-level programming (no HAL)

---

## 🛠️ Hardware Components

- STM32F103C8T6 (Blue Pill)
- Ultrasonic Sensor (HC-SR04)
- 2x IR Sensors (Line tracking)
- L298N H-Bridge Motor Driver
- 2x DC Motors
- Robot Chassis + Power Supply

---

## 🔌 Pin Configuration

| Component            | STM32 Pin |
|---------------------|----------|
| Left Motor PWM      | PA6 (TIM3_CH1) |
| Right Motor PWM     | PA7 (TIM3_CH2) |
| Motor Direction     | PA0, PA1, PA2, PA3 |
| Ultrasonic Trigger  | PB10 |
| Ultrasonic Echo     | PB11 |
| IR Sensor (Left)    | PB0 |
| IR Sensor (Right)   | PB1 |
| H-Bridge Enable     | PB12 |

---

## 🔄 System Behavior

### 1. Path Following
- Reads IR sensor values
- Adjusts motor speeds:
  - Turn left/right based on sensor input
  - Move forward when aligned
  - Stop if path is lost

### 2. Obstacle Avoidance
- Measures distance using ultrasonic sensor
- If obstacle is too close:
  - Stops the robot
- Otherwise:
  - Uses PID control to maintain a safe distance

---

## 🧮 Control Algorithm

A simple PID controller is used:

- **Kp = 2**
- **Ki = 0**
- **Kd = 0**

This allows proportional adjustment of motor speed based on distance error.

---

## 🚀 Getting Started

### Requirements
- STM32CubeIDE / Keil / PlatformIO
- ST-Link Programmer

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
