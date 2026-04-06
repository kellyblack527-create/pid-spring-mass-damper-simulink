# PID Controller - Spring-Mass-Damper System (Simulink)
 A PID controller built from scratch in Simulink, connected to a mass-spring-damper plant. No built-in PID block was used — the proportional, integral, and derivative terms were assembled manually using fundamental Simulink blocks.

## System Overview
 This model implements a closed-loop control system where a PID controller regulates the displacement of a mass-spring-damper system in the presence of an external sinusoidal disturbance force.
The error signal (setpoint minus measured displacement) feeds into the PID controller, which computes a control force. That force, combined with the external sine disturbance, acts on the plant. The resulting displacement feeds back to close the loop.

## System Parameters
|Parameter|Symbol|Value|Unit|
|---------|------|-----|----|
|Mass|m|1|kg|
|Spring stiffness|k|8|N/m|
|Damping coeff.|c|4|Ns/m|
|Setpoint|r|1|m|

##PID Gains (Untuned)
|Gain|Value|
|----|-----|
|Kp|1|
|Ki|1|
|Kd|1|

Gains are currently untuned. Tuning will be addressed in a future commit.

## External Disturbance
|Parameter|Value|Unit|
|---------|-----|----|
|Amplitude|1|N|
|Frequency|1|rad/s|
|Waveform|Sine|—|

## Simulink Model
<img width="1146" height="606" alt="Simulink_diagram" src="https://github.com/user-attachments/assets/11354400-6680-44af-b626-29d44e1841a0" />

The PID controller consists of:
- **Proportional path** — gain block (Kp)
- **Integral path** — gain block (Ki) feeding an integrator (1/s)
- **Derivative path** — gain block (Kd) feeding a derivative block
- Outputs summed and fed into the plant as the control force

---
## Results
<img width="693" height="491" alt="Score_output" src="https://github.com/user-attachments/assets/47f6ffe1-7efe-48ad-83a0-45baae6d935b" />
Top plot — Error signal: Shows the difference between the setpoint (1m) and the measured displacement over time. The error reduces progressively as the controller acts on the system.
Bottom plot — Displacement (x): Shows the system response under simultaneous PID control and external sine forcing. The oscillatory behavior reflects the sinusoidal disturbance acting on the plant throughout the simulation.

## Tools

- MATLAB/Simulink
- Continuous-time simulation

---
## What's Next

- Tune Kp, Ki, Kd for clean settling at setpoint with minimum overshoot
- Compare tuned vs untuned response
- Document the effect of each gain on system behavior



