# 🌀 FOC_PMSM  
**Field-Oriented Control Simulation for Interior Permanent Magnet Synchronous Motor (IPMSM)**

---

## 🚀 Overview  
This project demonstrates a simulation of **Field-Oriented Control (FOC)** applied to an **Interior Permanent Magnet Synchronous Motor (IPMSM)** using Simulink.  
FOC is a modern vector control technique that provides precise and dynamic control over electric motors by regulating current components in a rotating reference frame.

The system is configured to operate under:
- **No external load** (torque = 0)
- **Id = 0** (no flux control)

This setup mimics a **test stand environment** commonly used for validation and tuning.

---

## ⚙️ Simulation Objective  
The main control goal is to track a **reference rotor speed** using a cascaded FOC structure. The controller works as follows:
- A **Speed Controller** generates torque commands (Iq*).
- **Current Controllers** regulate the motor’s d–q axis currents.
- All control gains are defined **inside Simulink’s FOC Controller Gain blocks**, without using external scripts.

---

## 🧠 What is Field-Oriented Control?  
Field-Oriented Control (FOC), or **vector control**, transforms the motor’s 3-phase currents into a rotating reference frame aligned with the rotor's magnetic field. This enables decoupled control of:

- **Id (Direct-axis current)** → Controls magnetic flux  
  *(Set to 0 in this simulation for simplicity)*  
- **Iq (Quadrature-axis current)** → Controls torque  
  *(Adjusted dynamically to match the speed reference)*

This transformation simplifies AC motor control into a DC-like problem, allowing for smoother and more efficient control.

---

## 🧭 Controller Architecture  

### 🔄 Outer Loop – Speed Controller
- Compares the actual rotor speed to a reference.
- Outputs the desired **Iq\*** (torque-producing current).
- Implemented as a **PI controller** with gains set in the **FOC Controller Gain block**.

### 🔄 Inner Loop – Current Controllers
- Regulate both **Id** and **Iq** currents.
- Generate voltage references (**Vd**, **Vq**) which are transformed back to 3-phase voltages.
- **Id is fixed at 0** in this simulation to ignore reluctance torque.

All controller parameters are set using **Simulink blocks**, ensuring easy integration and tuning.

---

## 📊 Key Assumptions  
**Motor:** Interior PMSM  
- No load torque applied (test stand setup)  
- **Id = 0** (no reluctance torque contribution)  
- No field weakening or MTPA  
- Closed-loop speed control only

---

## 📁 Files Included  
- `FOC_Control_PMSM.slx` – Simulink model implementing the FOC strategy  
- `FOC_motor_params.m` – MATLAB script initializing motor and inverter parameters
- `Motor Control Plot.png` - Speed Control Plot
- `README.md` – Project documentation

---
