+++
title = "Simulating a Constrained Particle System"
tags = ["go"]
categories = ["programming"]
+++

## Aim:

The aim of the project was to use a particle system to model a simple deformable chain that moves along a ring and obeys :

* Newtons Laws
* Geometric Constraints

## Background :

For this system, we define three constraints, namely :

* **Rigid Edge Constraint** : This helps to keep the objects fixed in position and rotation relative to each other.
* **Pin Constraint** : This helps to prevent the chain from falling away under gravity.
* **Ring Constraint** : This ensures that the last particle in the chain lies on a ring and never falls off.


## Procedure:

**Step 1:**

We construct the constraint matrix `C` accounting for the 3 constraints mentioned above.
**You could write the 3 equations here**

**Step 2:**

We implemented a simple environment to observe the dynamics of the chain by modelling the chain with masses drawn as spheres and edges as cylinders. The chain was composed of N+1 point masses, `m = 1/(N+1) [Kg]`, at positions `x0,x1,....xN (in meters)` , with adjacent masses connected by rigid (inextensible) edges of length `h = 1/N [m]`. For this project, we considered `N = 11`, with the first sphere fixed in position and the last sphere contrained to always move along the circumference of the ring.

**Step 3:**

The cursor keys were implemented to interact with the model. Pressing the keys would apply an additional non zero translational acceleration `(a)` in addition to the gravitational acceleration `(g)`.

**Step 4:**

Using all this information above, we formulated the Lagrange equations for motion for the particle system and solve for the 2 unknowns: accelerations `(a)` and Lagrange multiplier `(λ)` using Euler integration and RK4 integration.

**Step 5:**

Once the acceleration `(a)` is obtained, we update the acceleration and solve for the velocity and positions of the particles.


[go]: <http://golang.org/>
[gohtmltemplate]: <http://golang.org/pkg/html/template/>
