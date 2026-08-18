---
layout: default
title: "Publications — Luda Korobenko"
description: "Published papers by Lyudmila (Luda) Korobenko on degenerate elliptic equations, hypoellipticity, Sobolev and Orlicz–Sobolev inequalities, and harmonic analysis."
permalink: /publications/
---

<p class="eyebrow">Research</p>
<h1>Publications</h1>

<div class="quicklinks">
  <a href="https://arxiv.org/search/?searchtype=author&query=Korobenko%2C+L">arXiv author search</a>
</div>

{% assign pubs = site.data.publications %}
{% assign current_group = "" %}

{% for pub in pubs %}
{% if pub.group != current_group %}
{% assign current_group = pub.group %}
<h2>{{ current_group }}</h2>
{% endif %}

<article class="pub">
    <span class="year">{{ pub.year }}</span>
    <h3 class="title">{{ pub.title }}</h3>
    <p class="authors">
      {% assign names = pub.authors | split: ", " %}
      {% for name in names %}
        {% if name == "Lyudmila Korobenko" %}<strong>{{ name }}</strong>{% else %}{{ name }}{% endif %}{% unless forloop.last %}, {% endunless %}
      {% endfor %}
      {% if pub.journal %} · <span class="journal">{{ pub.journal }}</span>{% endif %}
    </p>
    <p class="links">
      {% if pub.pdf %}<a href="{{ pub.pdf | relative_url }}">PDF</a>{% endif %}
      {% if pub.arxiv %}<a href="https://arxiv.org/abs/{{ pub.arxiv }}">arXiv</a>{% endif %}
      {% if pub.doi %}<a href="https://doi.org/{{ pub.doi }}">DOI</a>{% endif %}
    </p>
    {% if pub.abstract %}
    <details>
      <summary class="abstract-toggle">abstract</summary>
      <div class="abstract">{{ pub.abstract }}</div>
    </details>
    {% endif %}
  </article>
{% endfor %}
