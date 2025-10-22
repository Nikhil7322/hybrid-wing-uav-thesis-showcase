# 🛩️ Hybrid-Wing Electric UAV: Modeling and Transition Control

### M.Tech Thesis Showcase   
**Author:** Nikhil  
**Institution:** Indian Institute of Technology, Bombay  
**Supervisor:** Dr. Hemendra Arya  
**Year:** 2025

---

## 🧩 Overview

This repository presents a **high-level summary and visual showcase** of my M.Tech thesis project, which focused on the **design, modeling, and control of a hybrid-wing electric UAV**. This repository contains the end-to-end design, modeling, and control tools developed for an electric hybrid-wing UAV that integrates an X-configuration quadrotor VTOL module onto a fixed-wing Aerosonde airframe. The project includes battery sizing, additional Aerodynamic Drag prediction, a combined 6-DoF Simulink model, and four transition control strategies. Key simulation results show a 20% reduction in altitude error during forward transition compared to baseline, stable cruise establishment within 13 s, and controlled backward transition with altitude error under 1.6 m. The work demonstrates that a physical design change, gain-scheduled cascaded PID architecture can produce smooth and reliable VTOL↔cruise transitions with low implementation complexity.


The work involved:
- Full 6-DoF Simulink model combining quadrotor + fixed-wing dynamics.
- Structural and propulsion sizing using FlyEval.
- Four transition-control strategies implemented and compared (descriptions and code included).
- Cascaded PID controllers tuned for hover, transition, and cruise regimes.
- SIL validation pipeline and mission-profile simulations.
- Analysis scripts (MATLAB/Python) to reproduce plots, metrics, and animations.

**Note:**  
This repository is a **non-confidential summary** intended for public viewing.  
The complete thesis, detailed models, and code are not included due to institutional and IP restrictions.

---

## ⚙️ Key Features

- ✈️ Hybrid-wing UAV architecture (VTOL + fixed-wing)  
- 🧮 Physics-based 6-DoF modeling approach (Simulink)  
- 🔄 Transition control between hover and cruise regimes  
- 🕹️ Cascaded PID control structure  
- 📊 Simulation-based performance evaluation  

---

## 🧠 System Architecture (Conceptual Diagram)
High-level components:
- **Airframe & Propulsion:** Aerosonde baseline with quadrotor module (X-configuration).
- **Dynamics:** Separate quadrotor & fixed-wing subsystem models merged into a combined 6-DoF model.
- **Control Stack:** Inner-loop attitude PID, outer-loop position/guidance, and transition manager (four architectures).
- **Validation:** Simulation-in-the-loop (SIL) → data analysis → visualization (plots + animations).
- **Toolchain:** MATLAB & Simulink (models), FlyEval (sizing), SolidWorks (CAD/visuals), MATLAB (post-processing & plots).


```plaintext
+--------------------------------------------+
|          Hybrid-Wing UAV Framework         |
+--------------------------------------------+
| 1. Airframe & Propulsion Sizing (FlyEval)  |
| 2. Dynamic Modeling (6-DoF Equations)      |
| 3. Controller Design (Cascaded PID Loops)  |
| 4. Transition Strategy Evaluation          |
| 5. Simulation and Analysis                 |
+--------------------------------------------+
```
---


##  ⚙️ Methodology
1. **Sizing & Configuration**
   - Use FlyEval to perform structural sizing.
   - Use **iterative optimization algorithm** for **Li-Po** battery sizing.
   - Select X-configuration quadrotor optimized for thrust, endurance, and reduced aerodynamic interference.


2. **Modeling:**  
   - Built independent 6-DoF models for quadrotor and fixed-wing in *Simulink*  
   - Combined them into a unified hybrid-wing UAV model  
   - Incorporated actuator dynamics, aerodynamic couplings, and thrust allocation

3. **Control Design**
   - Design cascaded PID controllers for hover, forward **&** backward transition, and cruise.
   - Implement four transition-control strategies:
     1. Dual-controller attitude sharing with thrust augmentation
     2. PID blending with fixed incidence
     3. Gain-scheduled PID (decoupled)
     4. Hybrid blending with feedforward compensation
   - Tuned using step-response analysis and Control System tuner application in MATLAB 

4. **Validation**
   - Execute waypoint-driven mission profiles in SIL.
   - Compare metrics: altitude error, time-to-cruise, transition stability, failure/crash rate.
   
5. **Analysis**
   - Quantitative results (metrics & plots).
   - Visual validation (flight path, Simulink scopes).

---

## 📊 Simulation Results
- **Altitude error:** 20% reduction during forward transition (vs baseline).
- **Time-to-cruise:** Stable cruise achieved within **13 seconds** after forward transition.
- **Backward transition:** Controlled within **< 1.6 m** altitude error.

| Metric | Achieved Value | Improvement |
|:-------|:---------------:|:------------|
| Altitude Error (Forward Transition) | ↓ 20% | Reduced overshoot |
| Cruise Establishment | 13 s | Faster steady-state |
| Backward Transition Altitude Error | < 1.6 m | Stable control |
| Controller Architecture | Gain-scheduled PID | Low complexity, reliable |

- Additional results available as plots and animations in `/results/`:- `images/transition_altitude_error.png` → altitude vs. time  
  - `images/flightpath_3d.png` → 3D trajectory of hybrid UAV  
  - `images/control_response_comparison.png` → PID response plots  
  - `images/flight_animation.gif` → VTOL → Cruise → Hover sequence  

---
## 🚀 Future Work
- Integration with onboard autopilot (e.g., ArduPilot SITL)
- Real-world flight testing and system identification
- Optimization of control blending under turbulent conditions
- Adaptive or learning-based control transition schemes


---
## 💻 Installation & Usage
### Requirements
- MATLAB R2023a or later  
- Simulink Aerospace Blockset  
- Python 3.9+ (for Battery sizing algorithm)  
- Libraries: `numpy`, `matplotlib`, `pandas`



