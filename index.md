---
layout: main-page
title: Home
order: 0
---

## Welcome 👋

I am Philippe Miron, an AI Engineer passionate about the ever-evolving world of artificial intelligence and how to automate processes and tackle complex tasks. At [Premera Blue Cross](https://www.premera.com) since Sep. 2024, I lead the design and implementation of the enterprise knowledge database used by scalable AI agents to enhance process efficiency across various applications.

From Jan. 2023 to Sep. 2024, I worked at [DTN](https://www.dtn.com)---a weather intelligence company. I was part of the Remote Sensing, DevOps and Data Science groups. My main responsibility was to lead the development of a state-of-the-art software as a service (SaaS). This involves processing real-time global remote sensing datasets and ensuring seamless delivery of subhourly updates to our clients. I have gained experience in building efficient containerized applications, optimizing Kubernetes resources and performance, writing infrastructure as code, training and serving Machine Learning models, developing pipelines, building monitoring tools, and documenting the whole process.

I come from an Academic background. During my Ph. D.---in Mechanical Engineering at Polytechnique Montréal---I study vortex dynamics using high speed cameras and large lasers. I learned a lot about hardware and had the opportunity to experiments with microcontrollers. It was an amazing opportunity to design and plan hardware for experiments as well as building the softwares to process large datasets. My interests then transition from fundamental Fluid Dynamics to Physical Oceanography, more precisely on the study nonlinear phenomena in geophysical flows with emphasis in ocean transport and mixing processes.

During this time, I engaged in various projects that allowed me to develop analytical skills and thinking, but more importantly, developing my curiosity to always learn new things, striving for continuous improvements---a philosophy rooted in the Kaizen (改善) mindset---while embracing new challenges.

When not in front of the computer, I can be found enjoying the beach, diving, running, cycling, or exploring new places.

## Tech stack 🤖🛠️

Throughout my career, I have gained extensive experience with a diverse set of tools and technologies:

- Programming Languages: Python, C/C++, Julia, Go
- Machine Learning & AI: TensorFlow, PyTorch, Dask, Scikit-learn, NeuralForecast, AWS Bedrock, Hugging Face Transformers
- Framework: FastAPI, Flask, Metaflow
- Data Validation: Pydantic
- Data Science: NumPy, Panda, SciPy, Matplotlib, Streamlit
- Cloud & DevOps: AWS, Azure, Docker, Kubernetes, Datadog
- Databases: PostgreSQL, MySQL
- CI/CD: GitHub, Gitlab, Azure DevOps
- Infrastructure as Code: Terraform, Helm, CloudFormation, Bicep

These tools have empowered me to build scalable AI solutions, optimize cloud resources, and ensure robust data pipelines.

## Tech posts 🧑‍💻️
{% assign posts_tech = site.posts | where: "category", "tech" %}
  {% for post in posts_tech %}
  - [{{ post.title }} [{{ post.date | date: "%B %-d, %Y" }}]]({{ post.url | prepend: site.baseurl }}): {{ post.excerpt | strip_html | strip_newlines | truncate: 120 }} [{{ site.theme_settings.str_continue_reading }}]({{ post.url | prepend: site.baseurl }}){% endfor %}

## Academic posts 🧑‍🔬️
{% assign posts_tech = site.posts | where: "category", "academia" %}
  {% for post in posts_tech %}
  - [{{ post.title }} [{{ post.date | date: "%B %-d, %Y" }}]]({{ post.url | prepend: site.baseurl }}): {{ post.excerpt | strip_html | strip_newlines | truncate: 120 }} [{{ site.theme_settings.str_continue_reading }}]({{ post.url | prepend: site.baseurl }}){% endfor %}
