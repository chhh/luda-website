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

<div class="tags">
  <a class="tag" href="{{ '/publications/' | relative_url }}?tag=PDEs">PDEs</a>
  <a class="tag" href="{{ '/publications/' | relative_url }}?tag=Functional+Analysis">Functional Analysis</a>
  <a class="tag" href="{{ '/publications/' | relative_url }}?tag=Harmonic+Analysis">Harmonic Analysis</a>
  <a class="tag" href="{{ '/publications/' | relative_url }}?tag=Metric+Measure+Spaces">Metric Measure Spaces</a>
</div>

{% assign pubs = site.data.publications | sort: "year" | reverse %}

<div id="pubs">
{% for pub in pubs %}
  <article class="pub" data-tags="{% for t in pub.tags %}{{ t }}{% unless forloop.last %},{% endunless %}{% endfor %}">
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
</div>

<script>
(function () {
  var params = new URLSearchParams(location.search);
  var tag = params.get('tag');
  if (!tag) return;
  var container = document.getElementById('pubs');
  if (!container) return;
  var pubs = Array.prototype.slice.call(container.querySelectorAll('.pub'));
  var matching = pubs.filter(function (p) {
    return (p.getAttribute('data-tags') || '').split(',').indexOf(tag) !== -1;
  });

  var sec = document.createElement('section');
  sec.className = 'tag-results';
  var h = document.createElement('h2');
  h.textContent = tag;
  sec.appendChild(h);
  if (matching.length) {
    matching.forEach(function (p) { sec.appendChild(p.cloneNode(true)); });
  } else {
    var none = document.createElement('p');
    none.textContent = 'No publications tagged "' + tag + '".';
    sec.appendChild(none);
  }

  var allH = document.createElement('h2');
  allH.textContent = 'All publications';
  container.innerHTML = '';
  container.appendChild(sec);
  container.appendChild(allH);
  pubs.forEach(function (p) { container.appendChild(p); });
})();
</script>