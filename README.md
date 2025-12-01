# Pursuit–Evasion MATLAB Simulation

## Overview

This project implements a 2D pursuit–evasion game using non-holonomic (unicycle) vehicle dynamics for both the pursuer and evader. The simulation models realistic motion constraints, turning limits, and capture conditions. The evader can be controlled manually or through autonomous logic, while the pursuer uses a pursuit strategy.

---

## Features

* Non-holonomic kinematic motion model
* Continuous-time equations discretized for MATLAB
* Pursuer strategy based on line-of-sight pursuit
* Evader control (keyboard/autonomous)
* Capture detection using Euclidean distance
* Real-time visualization of agent trajectories

---

## Mathematical Model

### State Representation

Each agent is represented as:

```
s = [x; y; theta]
```

### Kinematic Equations (Continuous)

```
dx/dt = v*cos(theta)
dy/dt = v*sin(theta)
dtheta/dt = u
```

### Discrete Update (Used in MATLAB)

```
x(k+1) = x(k) + v*dt*cos(theta(k))
y(k+1) = y(k) + v*dt*sin(theta(k))
theta(k+1) = theta(k) + u*dt
```

### Constraints

```
|u| <= u_max
0 <= v <= v_max
```

### Capture Condition

```
D = sqrt((xp - xe)^2 + (yp - ye)^2)
Capture if D <= r_c
```

### Relative Geometry

```
d = [xe - xp; ye - yp]
phi = atan2(ye - yp, xe - xp)
beta = phi - theta_p
```

---

## MATLAB Instructions

1. Set parameters (dt, speeds, turn limits)
2. Initialize pursuer and evader states
3. Use loop to update motion using discrete equations
4. Apply pursuit strategy to compute `u_p`
5. Optionally apply keyboard or autonomous control to evader
6. Update positions, plot results, and check for capture

---

## File Structure

```
├── pursuit_sim.m       # main simulation
├── controller.m        # pursuit strategy
├── readme.md           # project documentation
```

---

## How to Run

1. Open MATLAB
2. Add the project folder to your path
3. Run:

```
pursuit_sim
```

4. Observe real-time pursuit animation

---

## Future Improvements

* Multiple pursuers / evaders
* Optimal control strategies
* Obstacle avoidance
* Reinforcement learning policies

---

## Author

Your Name
