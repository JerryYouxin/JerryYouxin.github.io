---
layout: default
title: "Publications"
permalink: /publications/
---

# Publications

A complete list of my publications.
<span style="color: var(--color-muted); font-size: 0.9rem;">(* denotes equal contribution)</span>

{%- assign pubs_by_year = site.data.publications | sort: "year" | reverse -%}
{%- assign current_year = "" -%}

{% for pub in pubs_by_year %}
  {% if pub.year != current_year %}
    {% unless forloop.first %}</div>{% endunless %}
    <h2 class="year-divider">{{ pub.year }}</h2>
    <div class="publications-year">
    {% assign current_year = pub.year %}
  {% endif %}

  <div class="publication">
    <div class="pub-title">{{ pub.title }}</div>
    <div class="pub-authors">
      {%- assign authors = pub.authors | split: ", " -%}
      {%- for a in authors -%}
        {%- if a == "me" -%}<span class="me">{{ site.author.name }}</span>{%- else -%}{{ a }}{%- endif -%}
        {%- unless forloop.last -%}, {% endunless -%}
      {%- endfor -%}
    </div>
    <div class="pub-venue">
      {{ pub.venue }}
      {%- if pub.type == "preprint" %} <span style="color: var(--color-muted);">(preprint)</span>{% endif -%}
      {%- if pub.ccf and pub.ccf != "" %} <span class="ccf-badge ccf-{{ pub.ccf | downcase }}">CCF-{{ pub.ccf }}</span>{% endif -%}
      {%- if pub.core and pub.core != "" %} <span class="ccf-badge core">CORE-{{ pub.core }}</span>{% endif -%}
      {%- if pub.note and pub.note != "" %} <em style="color: var(--color-accent);">· {{ pub.note }}</em>{% endif -%}
    </div>
    <div class="pub-links">
      {% if pub.pdf and pub.pdf != "" %}<a href="{{ pub.pdf }}">PDF</a>{% endif %}
      {% if pub.code and pub.code != "" %}<a href="{{ pub.code }}">Code</a>{% endif %}
      {% if pub.project and pub.project != "" %}<a href="{{ pub.project }}">Project</a>{% endif %}
      {% if pub.bibtex and pub.bibtex != "" %}<a href="{{ pub.bibtex }}">BibTeX</a>{% endif %}
    </div>
  </div>

  {% if forloop.last %}</div>{% endif %}
{% endfor %}
