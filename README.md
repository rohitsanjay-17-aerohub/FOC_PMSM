🌀 FOC_PMSM
Field-Oriented Control Simulation for Interior Permanent Magnet Synchronous Motor (IPMSM)

🚀 Overview
This project demonstrates a simulation of Field-Oriented Control (FOC) applied to an Interior Permanent Magnet Synchronous Motor (IPMSM) using Simulink. FOC is a modern vector control technique that provides precise and dynamic control over electric motors by regulating current components in a rotating reference frame.

The system is configured to operate under no external load (torque = 0) and assumes Id = 0, making it representative of test stand conditions often used for validation and controller tuning.

⚙️ Simulation Objective
The primary control objective is to track a reference rotor speed using a cascaded FOC strategy. The system regulates motor phase currents to maintain speed, using:
- A Speed Controller to generate torque commands.
- Current Controllers to regulate the motor’s d–q axis currents.
- FOC Controller Gain blocks to define all controller parameters internally in Simulink.

🧠 What is Field-Oriented Control?
Field-Oriented Control (FOC), also known as vector control, transforms the motor’s three-phase currents into a rotating reference frame aligned with the rotor magnetic field. This decouples the control of:
- Id (Direct-axis current): Controls magnetic flux — set to 0 in this model for simplicity.
- Iq (Quadrature-axis current): Controls torque — dynamically adjusted by the controller to match the speed reference.
This transformation makes AC motor control behave like a simple DC system, enabling more intuitive and efficient control.

🧭 Controller Architecture
🔄 Outer Loop – Speed Controller
- Compares measured rotor speed with reference speed.
- Outputs desired torque current (Iq*).
- Implemented as a PI controller with gains set in the FOC Controller Gain block.

🔄 Inner Loop – Current Controllers
- Control Id and Iq to track reference values.
- Outputs are transformed into 3-phase voltages to drive the motor.
- Id = 0 throughout the simulation.

All control loop gains (for speed and current) are defined directly in Simulink FOC Gain Blocks, without external scripts.

📊 Key Assumptions
Motor: Interior PMSM
- No load torque applied (mimicking a test stand setup).
- Id = 0 (no reluctance torque utilized).
- No field weakening or MTPA – basic FOC only.

📁 Files Included
- FOC_Control_PMSM.slx – Simulink model implementing the control system.
- FOC_motor_params.m – Initializes motor and inverter parameters.
- README.md – Project documentation.
