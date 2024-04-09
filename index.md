---
layout: main-page
title: Home
order: 0
---

## Welcome 👋

I'm Philippe Miron, a Senior Scientific Engineer (at the intersection of a data scientist and a DevOps) passionate about the ever-evolving world of machine learning and artificial intelligence to automate processes and tackle complex challenges. Currently, I'm working at [DTN](https://www.dtn.com/), in the Remote Sensing and the Grain Intelligence teams.

Since joining DTN in January 2023, I've been part of the DevOps and the Data Science group, additionally my main responsibility is to lead the development of a  state-of-the-art software as a service (SaaS). This involves processing real-time global remote sensing datasets and ensuring seamless delivery of multiple updates to our clients each day. I've gained experience in building efficient containerized applications, optimizing Kubernetes resources and performance, writing infrastructure as code, training and serving Machine Learning models, developing pipelines, building monitoring tools, and documenting the whole process.

I come from an Academic background. During my Ph. D.---in Mechanical Engineering at Polytechnique Montréal---I study vortex dynamics using high speed cameras and large lasers. I learned a lot about hardware and had the opportunity to experiments with microcontrollers. It was an amazing opportunity to design and plan hardware for experiments as well as building the softwares to process large datasets. My interests then transition from fundamental Fluid Dynamics to Physical Oceanography, more precisely on the study nonlinear phenomena in geophysical flows with emphasis in ocean transport and mixing processes.

During this time, I engaged in various projects that allowed me to develop analytical skills and thinking, but more importantly, developing my curiosity to always learn new things, striving for continuous improvements---a philosophy rooted in the Kaizen (改善) mindset---while embracing new challenges.

When not in front of the computer, I can be found enjoying the beach, diving, running, cycling, or exploring new places.

## Tech posts 🧑‍💻️
{% assign posts_tech = site.posts | where: "category", "tech" %}
  {% for post in posts_tech %}
  - [{{ post.title }} [{{ post.date | date: "%B %-d, %Y" }}]]({{ post.url | prepend: site.baseurl }}): {{ post.excerpt | strip_html | strip_newlines | truncate: 120 }} [{{ site.theme_settings.str_continue_reading }}]({{ post.url | prepend: site.baseurl }}){% endfor %}

## Academic posts 🧑‍🔬️
{% assign posts_tech = site.posts | where: "category", "academia" %}
  {% for post in posts_tech %}
  - [{{ post.title }} [{{ post.date | date: "%B %-d, %Y" }}]]({{ post.url | prepend: site.baseurl }}): {{ post.excerpt | strip_html | strip_newlines | truncate: 120 }} [{{ site.theme_settings.str_continue_reading }}]({{ post.url | prepend: site.baseurl }}){% endfor %}