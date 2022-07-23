---
layout: page
title: CV
permalink: /contributions/
---
## Education
+ 2012–2016, Ph. D., Experimental Fluid Dynamics, Mechanical Engineering, Polytechnique Montréal
+ 2010–2012, M. Sc. A, Numerical Fluid Dynamics, Mechanical Engineering, Polytechnique Montréal
+ 2007–2008, B. Ing, Industrial Engineering, Universidad Politécnica de Madrid, Madrid
+ 2005–2009, B. Ing., Mechanical Engineering, Polytechnique Montréal

## Academic Employment
+ 2021–    , Assistant Research Faculty, Physical Oceanography, Florida State University (COAPS)
+ 2020–2021, Assistant Scientist, Physical Oceanography, University of Miami (RSMAS)
+ 2016–2020, Postdoctoral Associate, Physical Oceanography, University of Miami (RSMAS)

## Fundings
{% for funding in site.data.fundings %}
+ {{funding.id}}, {{funding.pis}}, {{funding.title}}, {{funding.amount}}, {{funding.date}}{% if funding.link %}, [link]({{ funding.link }}){% endif %}{% endfor %}

## Preprint Articles
{% for paper in site.data.preprint %}
+ {{paper.authors}}, {{paper.title}}, {{paper.journal}}, {{paper.year}}{% if paper.doi %}, [link]({{ paper.doi }}){% endif %}{% endfor %}

## Peer-reviewed Articles
{% for paper in site.data.publications %}
+ {{paper.authors}}, {{paper.title}}, {{paper.journal}}, {{paper.year}}{% if paper.doi %}, [link]({{ paper.doi }}){% endif %}{% endfor %}

## Talks
{% for talk in site.data.talks %}
+ {{talk.authors}}, {{talk.title}}, {{talk.event}}, {{talk.location}}, {{talk.date}}{% if talk.doi %}, [link]({{ talk.doi }}){% endif %}{% if talk.path %}, [pdf]({{ talk.path }}) {% endif %}{% endfor %}

## Posters
{% for poster in site.data.posters %}
+ {{poster.authors}}, {{poster.title}}, {{poster.event}}, {{poster.location}}, {{poster.date}}{% if poster.doi %}, [link]({{ poster.doi }}){% endif %}{% if poster.path %}, [pdf]({{ poster.path }}) {% endif %}{% endfor %}

## Teaching experiences
+ Fluid dynamics (5 semesters)
+ Finite element in Thermofluids (4 semesters)
+ Introduction to MATLAB programming (1 semesters)
+ Design and manufacture assisted by computer

## Research Committee
+ 2022, Jeanne Maingot-Lépée, Influence of ENSO on larvae recruitment in French Polynesia, Master studies project
+ 2020, Samantha Medina, Influence of buoyancy on the velocity of floating objects affected by wind and current, Undergraduate thesis

## Fieldworks
+ April 30–May 4 2018, [AOML South Florida Program](https://www.aoml.noaa.gov/phod/sfp), South Florida
+ April 15–May 6, 2017, [Splash Experiment](http://carthe.org/splash/), Louisiana
+ September 12, 2016, [Bay Drift Project](http://carthe.org/baydrift/), Miami

## Outreach
+ 2017–2021 [Canes on Canes](https://hurricanes.rsmas.miami.edu/outreach/index.html), bring awareness to the South Florida community about hurricanes and the impacts of climate change.
+ 2018–2019 [Ocean Kids](https://www.rsmas.miami.edu/community-and-giving/outreach/ocean-kids/index.html), sharing love for science and ocean conservation with children from underserved Greater Miami communities.

## Skills
+ Scientific communication
    + Conferences
    + Data visualization and presentation (LaTeX, Matplotlib, TikZ, Tecplot, Paraview)
+ Computational
  - Finite Element Method
  - Lagrangian Analysis
  - Post-processing techniques
+ Experimental
  - Particle image velocimetry
  - Laser doppler velocimetry
  - Hot wire anemometer
  - Polarographic method
+ Programming
  - Python
  - C/C++
  - Arduino
+ Technical softwares
  - Catia/Solidworks

## Languages
+ French (native)
+ English (excellent knowledge)
+ Spanish (good knowledge)
+ Portuguese (beginner)
