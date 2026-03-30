---
layout: project_page
permalink: /

title: Decentralized Safe Path Following for Multiple Quadrotors on Intersecting Paths
authors:
  - Hamza Tariq, Adeel Akhtar
affiliations:
  - GRaDS-Lab / New Jersey Institute of Technology
paper:
video:
code: https://github.com/gradslab/safe_multiquad_pf
data:
---

<div class="columns is-centered" style="margin-top: -6.5rem;">
  <div class="column is-four-fifths has-text-centered">
    <div class="buttons is-centered" style="margin-top: 0.5rem; margin-bottom: 1.5rem;">
      <a class="button is-link is-medium" href="#sinusoidal-simulation">
        Sinusoidal Path Simulation
      </a>
      <a class="button is-link is-medium" href="#circular-simulation">
        Circular Path Simulation
      </a>
    </div>
  </div>
</div>


## Abstract

This paper studies decentralized safe path following for multiple quadrotors on intersecting paths, where safety requires both collision avoidance and strict adherence to pre-assigned routes. The proposed controller reformulates transverse feedback linearization as a constrained quadratic program with four equality constraints: two enforce convergence to and strict adherence on the path, and two prescribe the desired speed and orientation. Safety is achieved by relaxing only the speed and orientation constraints. Under the stated assumptions, the controller guarantees that all agents converge to their assigned paths, remain on them for all time, avoid collisions, and operate away from attitude singularities.



<div class="columns is-centered is-variable is-5">
  <div class="column is-three-fifths">
    <div class="box" style="border-radius: 14px;">
      <figure class="image" style="margin: -10;">
        <img
          src="./static/image/traj_xy_sine_anim.gif"
          alt="2D sinusoidal-path animation"
          style="border-radius: 10px; width: 100%; display: block;"
        >
      </figure>
    </div>
  </div>

  <div class="column is-two-fifths">
    <div class="box" style="border-radius: 14px;">
      <figure class="image" style="margin: -10;">
        <img
          src="./static/image/traj_xy_circle.gif"
          alt="2D circular-path animation"
          style="border-radius: 10px; width: 100%; display: block;"
        >
      </figure>
    </div>
  </div>
</div>

---



---

## Controller overview

The key idea is to separate the control objectives into two parts. The **transversal dynamics** drive each quadrotor to its prescribed path and keep it there, while the **tangential dynamics** regulate motion along the path. This structure makes it possible to preserve path invariance exactly and intervene only on speed and yaw when safety constraints become active.

The resulting per-agent QP enforces:
- two hard equality constraints for path convergence and path invariance,
- two relaxable equality constraints for tangential speed and orientation,
- ECBF constraints for pairwise collision avoidance,
- ECBF constraints that keep the closed-loop system away from roll/pitch singularities.

This page shows both the intersecting circular-path case emphasized in the paper and additional sinusoidal-path simulations included with the code base.

---

## Simulation results

### <span id="sinusoidal-simulation">Intersecting sinusoidal paths</span>


<div class="columns is-centered">
  <div class="column is-five-fifths">
    <div class="box" style="border-radius: 14px;">
      <figure class="image">
        <img src="./static/image/traj_3d_anim.gif" alt="3D sinusoidal-path animation" style="border-radius: 10px;">
      </figure>
      <p class="has-text-centered" style="margin-top: 0.0rem;">
        <strong>Two quadrotors following intersecting sinosoidal paths while avoiding collision</strong> 
      </p>
    </div>
  </div>
</div>

### <span id="circular-simulation">2. Intersecting circular paths</span>


<div class="columns is-centered">
  <div class="column is-five-fifths">
    <div class="box" style="border-radius: 14px;">
      <figure class="image">
        <img src="./static/image/traj_3d_circle.gif" alt="3D circular-path animation" style="border-radius: 10px;">
      </figure>
      <p class="has-text-centered" style="margin-top: 0.0rem;">
        <strong>Four quadrotors following interseting circular paths and avoiding collisions</strong> 
      </p>
    </div>
  </div>
</div>

---

## What the animations show

Both simulations, one on open path and the other on closed path show that

- **each quadrotor avoids collision with eavery other quadrotor** 
- **each quadrotor stays on its given path once converging on it for all time** 


---

## Repository contents

The repository includes:
- quadrotor dynamics simulation,
- decentralized QP-based safe path-following control,
- ECBF-based collision-avoidance constraints,
- ECBF-based attitude-safety constraints,
- 2D and 3D visualization utilities,
- animated simulation results for sinusoidal and circular-path environments.

---

## Requirements

```bash
pip install numpy cvxpy matplotlib