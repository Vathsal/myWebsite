+++
title = "Simulating a Jello cube"
tags = ["go"]
categories = ["programming"]
+++

## Aim:

The aim of this project was to understand the application of `3D mass-spring network` in physically based modelling.
To achieve this, we programmed a physically-based simulation of a jello cube which was modelled using a 3D mass spring network. The jello cube was modelled to be made of elastic material, i.e., when the jello cube is stretched, it will try to contract and when the jello cube is squeezed, it will try to inflate back to the original shape. We also implemented collision detection and response for the jello cube hitting any of the six walls of the bounding box.

**Have a picture of a jello cube inside a bounding box showing the structural shear and spring forces.**


## Background:


## Procedure:

**Step 1:**

 We modelled the cube to be of dimensions (1m x 1m x 1m) using (8*8*8 = 512) discrete mass points(surface points), all of equal mass, held together by springs. In the undeformed position, the mass points were positioned to form a uniform grid covering the volume of the cube. The rest length of the springs holding these masses were also uniform giving us the shape of the cube at start.

**Step 2:**

 The cube was initially enclosed inside a bounding box of size (4m x 4m x 4m).

**Step 3:**

 The movement of the cube was simulated. At the start of the simulation, the cube was in some prescribed ‘deformed’ position with some initial velocities which was read from the `world file` (called so because they describe the initial world (state) of the jello cube ). Over time, the initial velocities would propel the cube to move and deform. Some world files also had an external force field specified, which would further propel the movement of the cube.

The movement of the cube was modelled by numerically solving a system of ODE which accounts for

 * Newton’s 2nd law `F = ma`
 * Hook’s linear model of elasticity `F = Kx`
 * Linear damping `F = -KV`

Later, `Euler` and `RK4` methods were used to solve this system of ODE’s and the solution to these ODE’s was an array of acceleration values that were applied to the 512 mass points, thus simulating the movement of the cube.

Also, the mass points were held together by springs composed of `structural springs`, `shear springs` and `bend springs`. Hence, as the cube deforms, the points change positions giving the deformed shape at any point in time. Then the spring forces act to restore the mass points back to the undeformed shape. Thus the cube could stretch, contract, oscillate, change velocity and bounce off the walls of the bounding box while still holding its shape.


[go]: <http://golang.org/>
[gohtmltemplate]: <http://golang.org/pkg/html/template/>
