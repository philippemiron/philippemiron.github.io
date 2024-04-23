---
layout: page
title: Academia
permalink: academia
order: 1
---

## Archived projects (2016–2023)

I thought about creating another site for Academia, but I decided to keep everything in here for simplicity.

{% for project in site.projects %}
### [{{project.title}}]({{project.url}})
![]({{ site.baseurl }}{{project.thumbnail-path}}){:.center-image width="60%"}
{{project.short-description}}, [{{ site.theme_settings.str_continue_reading }}]({{ project.url | prepend: site.baseurl }})
&nbsp;<br>
&nbsp;<br>
{% endfor %}