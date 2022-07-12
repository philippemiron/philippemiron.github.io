---
layout: post
title:  Caribbean Marine Litter & ParticleViz
thumbnail-path: '/img/caribbean-ml.webp'
short-description: Lagrangian simulation of marine litter in the Caribbean.
---

<!-- ## Problem -->

## Project

In collaboration with the United Nations, we are developing Lagrangian simulations to help visualize the distribution of marine litter in the Caribbean, identify hot spots in the region, and evaluate the seasonality of the results. The particles, distributed following estimated mismanaged plastic waste density are advected with OceanParcels using ocean surface velocity from HYCOM GOFS3.1, a wind drag coefficient of 1% of the 10 m wind from JRA55, and a small random walk component with a uniform horizontal turbulent diffusion coefficient of Kh = 1 m^2/s representing unresolved turbulent motions in the ocean.

Simultaneously, with main developer [Olmo Zavala](https://olmozavala.com/), we are releasing [ParticleViz](https://olmozavala.github.io/particleviz/), an Open Source software to animate large number of particles inside dynamic web maps. The application is developed specially for Geoscience scientists that simulate different processes using Lagrangian models, and requires no web design knowledge!

![]({{ site.baseurl }}/img/carribbean-pviz.webp){:.center-image width='60%'}

## Publications

- Simulation and postprocessing source codes are available on [Github](https://github.com/philippemiron/marine-litter-caribbean)
- Overview presentation (work in progress) [link](https://bit.ly/carrlitter)
- ParticleViz ([GitHub](https://github.com/olmozavala/particleviz)) conference at OSM 2020 [link](https://www.youtube.com/watch?v=7Xk0DxRMPjQ&t=289s)
