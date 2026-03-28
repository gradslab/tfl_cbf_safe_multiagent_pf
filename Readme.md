# Decentralized Safe Path Following for Multi-Quadrotor Systems

<p align="center">
  <img src="quad_anim_4.gif" alt="Four-quadrotor simulation animation" width="700">
</p>
This repository contains the simulation code used to reproduce the main results for the paper on decentralized safe path following for multiple quadrotors on intersecting paths.

The implementation simulates a team of quadrotors with:
- transverse feedback linearization style path-following constraints,
- roll and pitch safety constraints enforced through ECBF-style inequalities,
- pairwise collision avoidance enforced through decentralized ECBF constraints,
- a per-agent quadratic program solved at every time step.

The default example reproduces the four-quadrotor intersecting-path scenario and generates the main figures used in the paper.

## Repository contents

The code currently lives in a Jupyter notebook and includes:
- quadrotor dynamics simulation,
- agent and environment classes,
- decentralized QP controller,
- pairwise safety constraints,
- plotting utilities for trajectories, safety barriers, and tracking variables.

## Requirements

Install Python 3.10+ and the following packages:

```bash
pip install numpy cvxpy matplotlib