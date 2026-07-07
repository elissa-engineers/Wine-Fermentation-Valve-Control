# 🍷 Automated Valve Control for a Wine Fermentation Tank

## Overview

This project presents the design and implementation of an automated control system for a butterfly valve used in a wine fermentation tank.

The objective was to develop a safe and reliable system capable of automatically operating the valve while continuously monitoring process conditions and immediately reacting to abnormal situations.

The project combines instrumentation, embedded control, actuator selection, and industrial safety principles into a functional Arduino-based prototype. The project report details the system requirements, actuator comparison, hardware architecture, software design, prototype implementation, and evaluation.

---

## Project Objectives

- Automate the opening and closing of a butterfly valve
- Monitor the fermentation process using multiple sensors
- Detect abnormal operating conditions
- Implement emergency shutdown logic
- Compare industrial pneumatic and electric actuator solutions
- Build and validate a working prototype

---

## Industrial Design

For a real industrial installation, a **single-acting pneumatic quarter-turn actuator with spring return** was selected as the recommended solution because it guarantees a mechanical **fail-close** response during power or air supply failures.

For the prototype, an **Arduino Uno** and an **SG90 servo motor** were used to simulate the valve movement while maintaining the same control logic.

---

## Hardware

### Controller
- Arduino Uno

### Sensors
- NTC Thermistor (Temperature)
- HC-SR04 Ultrasonic Sensor (Liquid Level)
- HW-038 Water Level Sensor (Overflow Detection)
- Potentiometer (Simulated Pressure)
- Emergency Push Button

### Outputs
- SG90 Servo Motor
- 16×2 I2C LCD
- Green LED
- Red LED
- Buzzer

---

## Software Features

The control system is implemented as a **Finite State Machine (FSM)** with four operating states:

- IDLE
- OPEN
- CLOSE
- EMERGENCY

Any abnormal condition immediately:

- closes the valve
- activates visual and audible alarms
- locks the system in Emergency Mode
- requires manual acknowledgment before restarting

The software continuously monitors all sensors while maintaining a non-blocking architecture based on `millis()`. 

---

## Safety Logic

The prototype monitors:

- Temperature
- Liquid level
- Overflow
- Simulated pressure
- Emergency stop button

If any monitored parameter exceeds its safety threshold, the valve closes immediately and the system enters a locked emergency state until the fault has been cleared and manually acknowledged.

---

## Technologies Used

- Arduino Uno
- Arduino IDE (C++)
- Embedded Systems
- Instrumentation
- Industrial Automation
- Actuators
- Control Systems

---

## Authors

- Elissa Kastoun
- Jad Abdallah
- Lea Eid

Course: **ELEC 424 – Actuators**  
Faculty of Engineering II, Lebanese University  
Spring 2025–2026
