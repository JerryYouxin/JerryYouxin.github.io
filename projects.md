---
layout: default
title: "Projects"
permalink: /projects/
---

# Projects

A selection of research and open-source projects I've worked on.

<div class="project-grid">
{% for proj in site.data.projects %}
  <div class="project-card">
    {% if proj.image and proj.image != "" %}
    <img src="{{ proj.image | relative_url }}" alt="{{ proj.name }}"
         onerror="this.style.display='none';">
    {% endif %}
    <div class="body">
      <h3>
        {% if proj.url and proj.url != "" %}
          <a href="{{ proj.url }}" target="_blank" rel="noopener">{{ proj.name }}</a>
        {% else %}
          {{ proj.name }}
        {% endif %}
      </h3>
      <p>{{ proj.description }}</p>
      {% if proj.tags and proj.tags.size > 0 %}
      <div class="tags">
        {% for t in proj.tags %}<span>{{ t }}</span>{% endfor %}
      </div>
      {% endif %}
      <div class="pub-links" style="margin-top: 10px;">
        {% if proj.url and proj.url != "" %}<a href="{{ proj.url }}" target="_blank" rel="noopener">Code</a>{% endif %}
        {% if proj.demo and proj.demo != "" %}<a href="{{ proj.demo }}" target="_blank" rel="noopener">Demo</a>{% endif %}
        {% if proj.paper and proj.paper != "" %}<a href="{{ proj.paper }}" target="_blank" rel="noopener">Paper</a>{% endif %}
      </div>
    </div>
  </div>
{% endfor %}
</div>
