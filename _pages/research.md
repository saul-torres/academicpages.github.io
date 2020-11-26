---
layout: archive
title: "Investigación"
permalink: /research/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

En el primer enlace se pueden leer los diferentes proyectos en los que (en mayor o menor medida) he colaborado o participado.  
Los siguientes enlaces hacen referencia a las que considero mis publicaciones más relevantes.  
Se pueden consultar todas mis publicaciones en el link de Google Scholar que aparece en el menú de la izquierda.

### [Proyectos de investigación](https://saul-torres.github.io/research-projects/)

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
