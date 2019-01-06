+++
title = "Simulating a Roller Coaster using Splines"
tags = ["go"]
categories = ["programming"]
+++

## Aim :
Having been introduced to splines and OpenGL programming, the aim of this project was to understand the `application of splines`. For this, we modelled a roller coaster using `Catmull-Rom splines` and then simulated a first person view of a person riding the roller coaster in an immersive environment using OpenGL lighting and texture mapping.

## Background :

![Kiku]( img1.png )

**Why choose catmul rom splines ?**

Catmull-Rom splines are a family of cubic interpolating splines such that the tangent at each point is calculated using the next and the previous position on the spline. They have C0 continuity, C1 continuity, local control and interpolation.

## Procedure:
Firstly, we were provided with various `track file`, which are nothing but text files with a list of control points defining various track shapes.

An example of this can be found below :

This track file represents the shape as shown below:



**Step 1:**

 We rendered a spline sequence which represents the entire length of the track as described in the track files above. In order to do so, we implemented a spline function which takes in four control points (p0 through p3) and a floating point value (u) from 0 to 1 , and computes the corresponding position on the spline segment defined by these four control points. We repeated this for all the controls points specified in the corresponding “track file”. Joining them all gives an elaborate curve of the coaster.

**Step 2:**

Once the roller coasters were modelled, we added a ground plane and textured it to simulate the effect of a terrain of our choice.

**Step 3:**

We then added a skybox to simulate the virtual environment that the roller coaster was in.

**Step 4:**

We then wrote logic to implement the ability to ride the coaster. We achieved this by moving the camera at a constant speed (in u) along the spline.

[go]: <http://golang.org/>
[gohtmltemplate]: <http://golang.org/pkg/html/template/>
