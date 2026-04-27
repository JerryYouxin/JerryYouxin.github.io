---
layout: default
title: "About"
permalink: /
---

<section class="hero">
  <div class="hero-avatar">
    <img src="{{ site.author.avatar | relative_url }}" alt="{{ site.author.name }}"
         onerror="this.onerror=null;this.src='https://www.gravatar.com/avatar/?d=mp&s=320';">
  </div>
  <div class="hero-body">
    <h1>{{ site.author.name }}</h1>
    <p class="hero-title">{{ site.author.title }} · {{ site.author.affiliation }}</p>

    <p>
      I am <strong>{{ site.author.name }}</strong> (游心), a Lecturer at the School of
      Computer Science and Engineering, Beihang University. I received both my B.S. and
      Ph.D. in Computer Science from Beihang University, advised by
      <a href="https://thomas-hl-yang.github.io" target="_blank" rel="noopener">Prof. Hailong Yang</a>.
    </p>

    <p>
      My research lies at the intersection of <em>high-performance computing</em>,
      <em>performance analysis and tuning tools</em>, <em>deep learning systems</em>,
      and <em>training/inference systems for large language models</em>. I currently serve
      as a core member on several national-level projects, including the National Key R&amp;D
      Program of China and a Key Project of the National Natural Science Foundation of China (NSFC).
    </p>

    <p>
      I have published 40+ peer-reviewed papers, including 10 first-author papers at
      <strong>SC</strong>, <strong>ASPLOS</strong>, <strong>IEEE TC</strong>,
      <strong>ACM TACO</strong>, <strong>IPDPS</strong>, <strong>ICPP</strong>,
      and <strong>FCS</strong>. Feel free to reach out if you'd like to collaborate on HPC,
      systems performance, profiling tools, or LLM systems.
    </p>

    <div class="contact-links">
      {% if site.author.email %}<a href="mailto:{{ site.author.email }}">✉ Email</a>{% endif %}
      {% if site.author.github %}<a href="https://github.com/{{ site.author.github }}" target="_blank" rel="noopener">GitHub</a>{% endif %}
      {% if site.author.google_scholar != "" %}<a href="{{ site.author.google_scholar }}" target="_blank" rel="noopener">Google Scholar</a>{% endif %}
      {% if site.author.orcid != "" %}<a href="https://orcid.org/{{ site.author.orcid }}" target="_blank" rel="noopener">ORCID</a>{% endif %}
      {% if site.author.dblp != "" %}<a href="{{ site.author.dblp }}" target="_blank" rel="noopener">DBLP</a>{% endif %}
      {% if site.author.linkedin != "" %}<a href="{{ site.author.linkedin }}" target="_blank" rel="noopener">LinkedIn</a>{% endif %}
      {% if site.author.twitter != "" %}<a href="{{ site.author.twitter }}" target="_blank" rel="noopener">Twitter</a>{% endif %}
    </div>
  </div>
</section>

## Research Interests

- **High-performance computing** — systems and runtime optimization for large-scale scientific workloads.
- **Performance analysis and tuning tools** — profiling methodologies for diagnosing performance bottlenecks, variance, and inefficiencies (e.g., *GVARP*, *TrivialSpy*).
- **Deep learning systems** — training/inference optimization, elastic training, sparse embedding acceleration (e.g., *EasyScale*, *RecServe*).
- **Training & inference systems for large language models** — efficient LLM serving and training on heterogeneous hardware.

## Education

- **Ph.D.** in Computer Science, Beihang University — advisor: Prof. Hailong Yang
- **B.S.** in Computer Science, Beihang University

## Experience

- **Postdoc, Lecturer**, School of Computer Science and Engineering, Beihang University

## Awards & Honors

- **2025** · National Postdoctoral Innovation Talents Support Program (博士后创新人才支持计划)
- **2025** · ACM SIGHPC China Outstanding Ph.D. Dissertation Award (ACM SIGHPC 中国优秀博士论文)
- **2024** · CCF Architecture Ph.D. Dissertation Incentive Program (CCF 体系结构博士学位论文激励计划)

## Grants & Projects

Core member of multiple national-level research projects, including:

- National Key R&D Program of China (国家重点研发计划)
- NSFC Key Project (国家自然科学基金重点项目)

## Professional Service

- Reviewer, **IEEE Transactions on Parallel and Distributed Systems (TPDS)**
- Guest Editor, Special Issue of **CCF Transactions on High Performance Computing (CCF THPC)**

## News

<ul class="news-list">
  <li><span class="date">2026-04</span><span>Personal homepage launched.</span></li>
  <li><span class="date">2025</span><span>Selected for the National Postdoctoral Innovation Talents Support Program.</span></li>
  <li><span class="date">2025</span><span>Received the ACM SIGHPC China Outstanding Ph.D. Dissertation Award.</span></li>
  <li><span class="date">2024</span><span>Received the CCF Architecture Ph.D. Dissertation Incentive Award.</span></li>
  <li><span class="date">2024-11</span><span><em>GVARP</em> presented at SC'24 — detecting performance variance on large-scale heterogeneous systems.</span></li>
  <li><span class="date">2023-11</span><span><em>TrivialSpy</em> presented at SC'23 — fine-grained dataflow-based value profiling.</span></li>
</ul>

## Selected Publications

{% assign highlights = site.data.publications | where: "highlight", true %}
{% if highlights.size == 0 %}{% assign highlights = site.data.publications | slice: 0, 3 %}{% endif %}

{% for pub in highlights %}
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
    {{ pub.venue }}, {{ pub.year }}
    {%- if pub.ccf and pub.ccf != "" %} <span class="ccf-badge ccf-{{ pub.ccf | downcase }}">CCF-{{ pub.ccf }}</span>{% endif -%}
    {%- if pub.note and pub.note != "" %} <em style="color: var(--color-accent);">· {{ pub.note }}</em>{% endif -%}
  </div>
  <div class="pub-links">
    {% if pub.pdf and pub.pdf != "" %}<a href="{{ pub.pdf }}">PDF</a>{% endif %}
    {% if pub.code and pub.code != "" %}<a href="{{ pub.code }}">Code</a>{% endif %}
    {% if pub.project and pub.project != "" %}<a href="{{ pub.project }}">Project</a>{% endif %}
    {% if pub.bibtex and pub.bibtex != "" %}<a href="{{ pub.bibtex }}">BibTeX</a>{% endif %}
  </div>
</div>
{% endfor %}

<p style="margin-top: 14px;"><a href="{{ '/publications/' | relative_url }}">See all publications →</a></p>
