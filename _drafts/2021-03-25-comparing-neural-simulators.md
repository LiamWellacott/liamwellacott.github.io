---
title: "Comparing neuron libraries"
date: 2021-03-25
categories: 
  - 
modified:
description:
tags: 
  - Spiking Neural Network
header:
  image: /assets
---

# notes

I have tried NEST and nengo, maybe I can provide some insight on these that would be useful.

points of comparison:
- How are they implemented (language), what are the implications for performance
- How do the APIs compare
- What is the support for integrating into robot controllers? 
    - More generally are their generic bindings or must you use python
- Documentation and training
- graphical interface

## nengo

- core is written in python, this will have an impact on performance
- some sort of deep learning integration and various other projects to make it easy to adopt... FPGA, Keras, SPA, DL(acutally just runs the simulation using Tensorflow, so maybe get a speed up), Loihi (intel neuromorphic chip), interfaces (airsim, mujoco)
