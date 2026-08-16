---
layout: default
title: Publications
---

<p class="eyebrow">Research</p>
<h1>Publications</h1>

<div class="measure">
  <p class="lead">
    Regularity theory for degenerate elliptic operators, Sobolev and
    Orlicz–Sobolev inequalities, and the doubling condition.
  </p>
</div>

{% assign pubs = site.data.publications | sort: "year" | reverse %}

{% for pub in pubs %}
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
  </p>
  {% if pub.abstract %}
  <details>
    <summary class="abstract-toggle">abstract</summary>
    <div class="abstract">{{ pub.abstract }}</div>
  </details>
  {% endif %}
</article>
{% endfor %}
