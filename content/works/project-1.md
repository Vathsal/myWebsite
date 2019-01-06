+++
title = "Pose transfer of an Armadillo using eigen functions"
tags = ["go"]
categories = ["programming"]
+++

## Aim:
* The aim of this project is to understand the role of eigenfunctions in pose estimation

## Background:
**What are Eigenfunctions and why we are using them ?**


Now that we understand the value of eigenfunctions and their usage. Let’s see how these can be applied to mesh deformation.

## Procedure:
Consider 2 poses that you would like to do the pose transfer between. Let us consider `Pose-A` as the source mesh and `Pose-B` as the destination mesh.

**Step 1:**

First, we compute the surface-laplacian and basis functions of the source mesh (Pose-A).

You may ask why are we computing the surface laplacian and basis functions?

Laplace transform is a convenient way of turning a calculus into algebra. I.e it transforms sin/cos/exp functions into rational polynomials, differentiation into multiplication and integration into subtraction, thus making them faster to solve as a whole.

    Calculus ------> Algebra

In layman terms it can be explained as below:

    Assume that you have a problem and it is hard to solve it in your world. So, you travel to another world (Laplace Transform) where you could do the calculations on much simpler things and then come back to your world (Inverse Laplace Transform) with the solution.

**Insert the analogy here :**

**Step 2 :**

We then compute the weights for each eigenfunction by projecting the source mesh onto its own basis functions. Let’s call these weights as `WA`.

**Step 3 :**

We then repeat steps 1 & 2 for the destination mesh (Pose-B). This yield s a set of weights for each eigen function. Let’s call these weights as `WB`.

          WA = {a1, a2… an-1, an}
          WB = {b1, b2… bn-1, bn}

**Step 4:**

 We now interpolate between these weight values to infer the intermediate poses of the armadillo. As we know, the lowest eigen functions defines the pose of the subject and the highest eigen functions defines the details. Here, since we want the final form from the destination pose and the details from the source pose, we use the weights WB (from the destination pose) for the lowest eigenfunctions and the weights WA (from the source pose) for the highest eigenfunctions to obtain a successful pose transfer.

**Step 5:**

Finally we performed this for multiple source-destination pose pairs and compiled the results resulting a little armadillo dance.

    Note: For the purposes of this project, we have used an ‘armadillo’ as our subject. But, this algorithm would work just as fine with any other mesh as well.


[go]: <http://golang.org/>
[gohtmltemplate]: <http://golang.org/pkg/html/template/>
