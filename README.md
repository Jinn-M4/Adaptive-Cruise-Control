🚗 Adaptive Cruise Control (ACC) Simulation
📌 Overview

This project implements an Adaptive Cruise Control (ACC) system using a simulation-based approach in Python.
The system controls the ego vehicle's speed while maintaining a safe distance from a lead vehicle.

The controller dynamically switches between:

Cruise Mode (speed tracking)
Distance Mode (safe distance keeping)

This project demonstrates fundamental concepts used in modern Advanced Driver Assistance Systems (ADAS).

🎯 Features
🚘 Adaptive Cruise Control logic
🔄 Mode switching (Cruise ↔ Distance)
⏱️ Time-gap based safety distance policy
🚨 Cut-in scenario handling
⚡ Acceleration saturation (realistic constraint)
🎬 Simulation animation (GIF)

🧠 System Architecture
Lead Vehicle ──► Distance Calculation ──► ACC Controller ──► Ego Vehicle
                          │
                          ▼
                  Mode Switching Logic

⚙️ Mathematical Model
Vehicle Dynamics

Longitudinal motion model:

dv/dt = a
dx/dt = v

Safe Distance Policy (Time Gap)
d_safe = d0 + T * v
Control Law
a = k_v (v_ref - v) + k_d (d - d_safe)

🧪 Simulation Scenarios
1. Normal Driving
Ego vehicle tracks the desired speed
2. Lead Vehicle Braking
Lead vehicle slows down after 20 seconds
3. Cut-in Scenario
A vehicle suddenly appears in front of the ego vehicle

🧑‍💻Code Design

The project is structured using object-oriented design:

Vehicle
Handles vehicle dynamics (position, velocity)
ACCController
Computes acceleration
Implements mode switching logic
Simulation
Runs scenarios
Logs results
Generates plots and animation

🚀 How to Run
Option 1: Google Colab
Open the notebook in Google Colab
Run all cells
The GIF will be generated automatically
Option 2: Local Environment
pip install numpy matplotlib
python acc_simulation.py

💡 Key Insights
Simple PID-based control can be extended to real-world ACC logic
Mode switching is essential for safe and robust behavior
Time-gap policy provides intuitive and stable distance control
