---
layout: post
title: Probabilistic dispersion
thumbnail-path: '/img/pf-prob.webp'
short-description: Markov Chain toolbox to analyze Lagrangian data sets of surface drifters and subsurface floats.
---

## Problem
There exists many large Lagrangian data sets such as the one maintained by the  [Global Drifter Program (GPD)](https://www.aoml.noaa.gov/phod/gdp) and the [WOCE Subsurface float Data Assembly Center](https://www.aoml.noaa.gov/phod/float_traj/data.php). For example, the following figure shows the trajectories of 152 RAFOS floats deployed at 1500 m (left) and 2500 m (right) during a 4-yr-long program in the Gulf of Mexico (Hamilton et al. 2016).

![]({{ site.baseurl }}/img/pf-trajectories.webp){:.center-image width='90%'}

With all those informations, how can we *forecast* the dispersion of a passive tracer at the surface of the ocean such as oil, plastics or larvae? and more importantly how can we extract information encoded into a Lagrangian data sets.

## Development
Probabilistic methods allows to combine the information contains in trajectories into a tool called the Transfer Operator. The discrete version of this operator is the transition matrix *P*, and each entry of the matrix *P<sub>ij</sub>* represents the probability of moving from bin *i* to bin *j* during the fixed transition time *T*. Acting as a Markov Chain of the underlying dynamics, this operator allows for the forecast of a system based *only* on current observations.

## Applications

As a first example, the *Sargassum* spreading across the Atlantic Ocean is obtained from a uniform distribution across the Atlantic Ocean between 7°S and 20°N using undrogued drifters from GDP (1992–2019).

![]({{ site.baseurl }}/img/pf-sargassum.gif){:.center-image width='90%'}

As a second example, the Markov-chain model is used to estimate the probabilistic description of the drift of marine debris from the infamous Malaysian Airlines flight MH370. En route from Kuala Lumpur to Beijing, MH370 mysteriously disappeared in the southeastern Indian Ocean on 8 March 2014, somewhere along the arc of the 7th ping ring around the Inmarsat-3F1 satellite position when the airplane lost contact. The transition matrix is constructed using undrogued satellite-tracked surface buoys (to approximate the dynamics of marine debris) from the global historical data bank. Then using Bayesian estimation, we estimate the most probable crash site around 25°S on the Inmarsat arc. This location maximizes the probabilities of finding the confirmed airplane debris at their reported time and location across the Indian Ocean coast ().

![]({{ site.baseurl }}/img/pf-examples.webp){:.center-image width='90%'}

## Open science
The **py**thon [**G**eophysical **T**ransition **M**atrix (**pygtm**)](https://github.com/philippemiron/pygtm) toolbox, as well as many examples and methodology presented in previous publications, are available to the community.

## Sources
- Hamilton, P., A. Bower, H. Furey, R. Leben, and P. Pérez-Brunius, Deep circulation in the Gulf of Mexico: A Lagrangian study, OCS Study BOEM 2016-081 Tech. Rep., Bureau of Ocean Energy Management, 2016, [link](https://permanent.fdlp.gov/gpo80279/5583%5b1%5d.pdf)
- See, [Prof. Amy Bower's project page](https://www2.whoi.edu/site/bower-lab/a-lagrangian-study-of-the-deep-circulation-in-the-gulf-of-mexico-2/) for a list of publications from the RAFOS experiment
- P. Miron, F.J. Beron-Vera, M.J. Olascoaga and P. Koltai, Markov-chain-inspired search for MH370, [link](https://doi.org/10.1063/1.5092132)
