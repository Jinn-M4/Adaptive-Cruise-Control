# Adaptive Cruise Control (ACC) Simulation

> Implemented a distance-based Adaptive Cruise Control system that dynamically adjusts vehicle speed to maintain a safe following distance under realistic driving scenarios.

---

## Overview

Adaptive Cruise Control (ACC) is a core function in modern driver assistance systems.
This project simulates an ACC system that:

* Maintains a target speed in free-driving conditions
* Adjusts speed based on the distance to a lead vehicle
* Handles dynamic scenarios such as **sudden deceleration** and **cut-in events**

---

## Simulation

![ACC Simulation](ACC_simulation.gif)

---

## System Design

The controller switches between two modes:

### 1. Cruise Mode

* Activated when the distance is larger than the safe distance
* Vehicle tracks a reference speed

### 2. Distance Control Mode

* Activated when the vehicle is too close to the lead vehicle
* Controller regulates speed to maintain a safe distance

---

## Control Logic

The control input is based on both:

* **Speed error**
* **Distance error**

[
a = k_v (v_{ref} - v) + k_d (d - d_{safe})
]

Where:

* ( v_{ref} ): target speed
* ( d ): actual distance
* ( d_{safe} = d_0 + T_{gap} \cdot v )

This ensures:

* Smooth speed tracking in free flow
* Safe distance maintenance in traffic

---

## Simulation Scenarios

The system is tested under realistic driving conditions:

* **Lead Vehicle Deceleration**

  * Sudden speed drop after 20 seconds

* **Cut-in Scenario**

  * A new vehicle merges into the lane

These scenarios test the controller’s ability to react to dynamic changes.

---

## Results

* The vehicle maintains a stable following distance
* Speed is adjusted smoothly without excessive oscillation
* The system successfully handles abrupt changes in traffic conditions

The visualization highlights:

* Real-time distance vs safe distance
* Mode switching behavior
* Control error evolution

---

## ⚠️ Challenges

### 1. Balancing Speed Tracking and Distance Safety

Designing a controller that simultaneously tracks a target speed while maintaining a safe distance required careful tuning.

* High speed gain → fast response but unsafe distance
* High distance gain → safe but sluggish behavior

Finding a stable balance between the two was a key challenge.

---

### 2. Mode Switching Stability

The transition between Cruise Mode and Distance Control Mode introduced discontinuities.

* Abrupt switching can cause oscillations
* Smooth transition required careful condition design

---

### 3. Realistic Scenario Modeling

Simulating real-world driving scenarios (deceleration, cut-in) without causing unrealistic artifacts (e.g., discontinuities in position) required refining the simulation logic.

---

## 🐞 Issues & Fixes

### 1. Lead Vehicle "Teleportation"

* Issue: The lead vehicle position was abruptly reassigned during the cut-in scenario, causing unrealistic jumps in distance.
* Fix: Replaced direct position assignment with velocity-based transitions to maintain continuity.

---

### 2. Time-Step Misalignment in Visualization

* Issue: Mixing updated ego position with previous distance values caused visual overlap between vehicles.
* Fix: Logged lead vehicle position (`x_lead_hist`) separately to ensure time consistency.

---

### 3. Poor Visualization of Control Behavior

* Issue: Initial animation only showed vehicle motion, making it difficult to interpret control performance.
* Fix: Added safe distance visualization, error metrics, and time-series plots.

---


## Limitations

### 1. Simplified Vehicle Dynamics

The model assumes a simple kinematic update:

* No drag, tire dynamics, or actuator delay
* Real vehicles exhibit nonlinear behavior

---

### 2. No Sensor Noise or Delay

The system assumes perfect perception:

* Real ACC systems rely on radar/camera fusion
* Measurement noise and delay are not considered

---

### 3. Basic Linear Controller

The controller uses a proportional structure:

* No integral or derivative terms
* Performance may degrade in more complex scenarios

---

### 4. Single-Lane Scenario

The simulation does not consider:

* Lane changes
* Multi-vehicle interactions
* Complex traffic environments



## Key Takeaways

* Implemented a **time-gap based distance policy** used in real ACC systems
* Designed a **mode-switching control structure**
* Visualized system behavior to analyze control performance
* Improved simulation realism by handling dynamic driving scenarios

---


