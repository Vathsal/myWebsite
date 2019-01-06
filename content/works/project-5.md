+++
title = "Motion Capture Interpolator"
date = "2015-09-17T13:47:08+02:00"
tags = ["go"]
categories = ["programming"]
+++

## Aim:

The aim of this project was to understand and evaluate the different interpolation schemes.
For the purpose of this project, we implemented `4 interpolation schemes`, namely:

* • Linear interpolation using Euler angles
* • Bezier interpolation using Euler angles
* • Spherical Linear interpolation using quaternions
* • Spherical Bezier interpolation using quaternions

## Procedure:

**Step 1 :**

To start with, we were given a bunch of `(ASF + AMC)` files corresponding to different motion capture sequences. We parse these files and load the data into a suitable data structure.

    ASF stands for `Acclaim Skeleton File`
    AMC stands for `Acclaim Motion Capture data`

    ASF files encode the skeleton data. Typically in an ASF file, a base pose is defined for the skeleton that is the starting point for the motion data. It also contains information such as length of bones, degrees of freedom etc.

    AMC files contain the motion data for the skeleton defined in the ASF file. It contains information such as translation of root node, rotation of root node, join angles etc.

**Step 2 :**

We selected one ASF+AMC file pair, and formed a subsequence by randomly dropping some frames from the file.
Step 3: We implemented the different interpolation schemes as mentioned above to compute the missing frames in the subsequence, so as to produce a sequence which is the same length as the original.

**Step 4:**

We then used an OpenGL based `Motion Capture Player` to render the skeleton data using the ASF file and played back the motion data using the AMC file.

**Step 5:**

 To compare the accuracy of the interpolation schemes, we played back the original AMC file juxtaposed upon the new AMC files.

## Inferences :
We found that `Spherical Bezier Interpolations using quaternions` gave the best results.


[go]: <http://golang.org/>
[gohtmltemplate]: <http://golang.org/pkg/html/template/>
