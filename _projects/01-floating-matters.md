---
layout: post
title: Floating marine debris
thumbnail-path: "/img/mr-exp.png"
short-description: Modeling the trajectory of floating objects at the surface of the ocean...
---

{:.center}
![]({{ site.baseurl }}/img/mr-exp.png)

## Problem
Assessing floating matter drift in the ocean is of importance for a number of key reasons. These range from improving search-and-rescue operations at sea; to better understanding the drift of flotsam of different nature including macroalgae such as Sargassum, airplane wreckage, tsunami debris, sea-ice pieces, larvae, and oil; to better interpreting 'Lagrangian' observations in the ocean. At present, largely piecemeal, ad-hoc approaches are taken to simulate the effects of ocean currents and winds on the drift of floating objects. A systematic approach ideally founded on first principles is needed.

## Development
Our group has been seeking a systematic approach by building on the Maxey–Riley set, the de-jure framework for the study of finites-size, buoyant or inertial particle dynamics in fluid mechanics. As is well-known in that field, inertial particles cannot instantaneously adjust their velocities to changes in the carrying fluid velocity. Thus their dynamics fundamentally differ from those of fluid or Lagrangian (i.e., infinitesimally small, neutrally buoyant) particles. Solving for the exact motion of inertial particles would involve solving the Navier–Stokes equation with moving boundaries. The Maxey–Riley framework provides an approximate solution to the ensuing highly complicated PDE problem through the resolution of an ODE.

Built on first principles, the Maxey–Riley is a classical mechanics second Newton's law for the motion of inertial particles immersed in a fluid in motion. We have extended the validity of Maxey–Riley set to finite-size particles that float at the air–sea interface accounting for the combined effects of ocean currents and wind drags. The resulting equation involves slow and fast variables, problem that can be analyzed using the Haller–Sapsis extension to nonautonomous systems of Fenichel's classic geometric singular perturbation theory. Investigating inertial dynamics on the slow manifold, a codimension-two manifold that attracts all solutions of the Maxey–Riley set, has enabled us to gain important insight. This includes the possible role of mesoscale eddies as attractors of flotsam or the tendency of the latter to develop large patches in the centers of the subtropical gyres.

## Equations
TODO, this is an example.

{% katex display %}
c = \pm\sqrt{a^2 + b^2}
{% endkatex %}

## Validation
Currently underway are the planning of field and lab experiments to test the Beron-Vera–Olascoaga–Miron (BOM) theory of inertial particle dynamics in the ocean and an extension of the latter to account for the motion of elastically interacting inertial particles as a minimal model for Sargassum drift.

## Publications
- P. Miron, M.J. Olascoaga, F.J. Beron-Vera, N.F. Putman, J. Triñanes, R. Lumpkin and G.J. Goni, How local winds and currents impact the trajectories of marine debris and Sargassum: Inertia-dependent clustering of floating material paths, Preprint, 2020
- M.J. Olascoaga, F.J. Beron-Vera, and P. Miron, Observation and quantification of inertial effects on the drift of floating objects at the ocean surface, Physics of Fluid, 2020, [link](https://doi.org/10.1063/1.5139045)
- F. J. Beron-Vera, M. J. Olascoaga and P. Miron, Building a Maxey–Riley framework for surface ocean inertial, Physics of Fluids, 2019, [link](https://doi.org/10.1063/1.5092132)
