# PID-Motor-Control

# Speed Control of a DC Motor Using a PI Controller

## 📌 Project Overview
This project focuses on the design, simulation, and hardware implementation of a closed-loop control system to regulate the speed of a DC motor. The system utilizes a **Proportional-Integral (PI) Controller** to achieve precise speed tracking, eliminate steady-state error, and maintain robustness against physical load variations.

The workflow spans from **System Identification** (modeling the plant) to **Real-Time Deployment** using Arduino and Simulink.

---

## 🛠️ System Architecture
The control system is built on a feedback loop where the motor's actual speed is measured and compared against a desired setpoint.

* **Controller:** Discrete-time PI Controller.
* **Plant:** DC Motor (modeled as a second-order system).
* **Feedback:** Rotary Encoder / Speed sensing.
* **Actuator:** L298N H-Bridge Motor Driver.
* **Processor:** Arduino Uno.

---

## 🚀 Key Features & Methodology

### 1. System Identification
To design an effective controller, we first derived the mathematical model of the DC motor:
* Performed **Open-Loop Step Response** tests.
* Analyzed the resulting curve to determine the gain ($K$) and time constant ($\tau$).
* Derived the **Transfer Function** representing the motor's physical behavior.

### 2. Controller Design & Tuning
We evaluated several control strategies (P, PI, PID) in **MATLAB/Simulink**:
* **P-Control:** Fast response but suffered from significant steady-state error.
* **PI-Control (Selected):** Achieved the target speed with zero steady-state error and controlled overshoot.
* **Tuning:** Parameters ($K_p$ and $K_i$) were tuned using the Simulink PID Tuner and refined through manual iteration to balance rise time and stability.

### 3. Hardware Implementation
* Converted the continuous-time controller to **Discrete-Time** using the **Tustin (Bilinear) transformation** for digital execution.
* Integrated Arduino Uno with Simulink for real-time data logging and parameter adjustment.

---

## 📈 Results & Observations
* **Accuracy:** The system demonstrated high tracking accuracy across various setpoints.
* **Steady-State Error:** Successfully reduced to 0% due to the integral action.
* **Saturation Effects:** Observed at full-scale input, highlighting the practical limitations of the 12V power supply vs. the theoretical model.

---

## 📂 Project Structure
```text
├── Simulink/      # .slx files for block diagrams and controller simulation
├── Arduino/       # C++/Ino source code for hardware deployment
└── Docs/          # Full Technical Report (PDF) and supporting documentation
