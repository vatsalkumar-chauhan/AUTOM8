# AUTOM8 — Stair-Climbing Campus Delivery Robot (Proof of Concept)

## Overview
AUTOM8 is a stair-climbing campus delivery robot designed and fabricated 
as a final year B.Tech project in Robotics and Automation Engineering at 
Parul University, Vadodara (2023–2024). The robot is intended to perform 
last-mile delivery tasks across multi-floor campus buildings, navigating 
flat terrain and climbing staircases.

The project addresses a real gap — no low-cost stair-capable delivery 
robot exists for Indian institutional deployment. Total prototype cost: 
approximately ₹33,000 (~€370), entirely self-funded.

**University Grade: O — Outstanding (10/10)**

---

## Team
- Vatsal Chauhan (200305123901)
- Ketul Luhar (210305123705)
- Prathamesh Mhaske (210305123701)
- Aniket Sharma (200305123025)

**Guided by:** Prof. Dr. Prince Jain | Prof. Jagdish Pampania

---

## Robot Architecture — Three-Body Segmented Chassis
The robot consists of three independent aluminium extrusion boxes — 
front, middle, and back — each 20cm wide and 36cm tall, fabricated from 
20×20mm T-slot and V-slot aluminium profiles. The three boxes are 
connected by four GT2 belt-driven V-slot carriage assemblies.

---

## Key Engineering Feature — Sequential Gantry Lift Mechanism
The central technical contribution is the sequential gantry lift 
mechanism for stair climbing.

Four 100 RPM Johnson DC gantry motors mounted on the middle box drive 
GT2 belt and V-slot carriage assemblies to lift the front and back boxes 
independently onto successive stair treads. The three boxes are elevated 
in sequence through a six-phase control loop, allowing the robot to 
climb one full stair per cycle.

**Compatible stair geometry:**
- Tread depth: 280–400mm
- Riser height: 150–220mm
- Covers full NBC IS 1644 range for Indian educational buildings

**Control approach development:**
The stair-climbing trigger logic was developed through three successive 
stages — timing-based control, IR sensor triggering, and HC-SR04 
ultrasonic sensor triggering. IR sensors were found unsuitable due to 
ambient lighting sensitivity.

The final implementation uses timing-based control — since stair 
dimensions are fixed and uniform throughout the campus, precise timing 
sequences reliably trigger each phase without sensor dependency. 
HC-SR04 ultrasonic triggering was also fully developed and can be 
activated when the robot encounters staircases of unknown or varying 
dimensions outside the campus environment.

**Observed limitations:**
- Sensor response delay at phase transitions
- Middle box tilt during constraint-reaction lift phase
- GT2 belt elongation after repeated cycles

---

## Flat Terrain Navigation
- Eight 200 RPM Johnson DC wheel motors for drive
- Encoder-based pre-programmed path execution between delivery waypoints
- MPU-6050 IMU for real-time heading correction during motion

---

## Obstacle Detection
- Three HC-SR04 ultrasonic sensors on front box
- Robot halts and activates buzzer when obstruction detected within range
- Resumes automatically once path is clear

---

## Hardware Specifications

| Component | Specification |
|---|---|
| Microcontroller | Arduino Mega 2560 |
| Gantry motors | 4 × 100 RPM Johnson DC |
| Wheel motors | 8 × 200 RPM Johnson DC |
| Motor driver | L298N |
| Distance/stair sensors | HC-SR04 ultrasonic |
| IMU | MPU-6050 |
| Drive system | GT2 belt, V-slot gantry rails |
| Battery | Custom 3S4P Li-ion, 11.1V nominal, 8800mAh |
| Chassis | 20×20mm T-slot and V-slot aluminium extrusion |
| Payload capacity | Under 7 kg (governed by GT2 belt tensile limit) |
| Torque safety factor | Minimum 7.5× across all lifting phases |
| Total cost | ~₹33,000 (~€370), self-funded |

---

## Scope and Limitations
All subsystems — stair climbing, obstacle detection, heading correction, 
encoder navigation — were individually developed and validated. Full 
integrated end-to-end testing is identified as the immediate next step.

This is a proof-of-concept prototype. Fully autonomous dynamic path 
planning, SLAM, and mobile app integration are identified as future work.

---

## Future Work (Proposed)
- Closed-loop gantry position control
- MPU-6050 yaw integration during stair climbing
- Dual encoder for improved odometry
- Upgraded motor drivers
- Payload compartment enclosure
- Autonomous docking charging station
