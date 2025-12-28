---
layout: default
title: Publications
---

{% assign pubs = site.data.publications | sort: "year" | reverse %}

<p class="muted">
A selected list of publications and preprints. (Sorted by year.)
</p>

{% for p in pubs %}
<div class="card">
  <div><strong>{{ p.title }}</strong></div>

  {% if p.authors %}
  <div class="muted">{{ p.authors }}</div>
  {% endif %}

  <div>
    {% if p.venue %}{{ p.venue }}{% endif %}
    {% if p.year %}{% if p.venue %} · {% endif %}{{ p.year }}{% endif %}
    {% if p.type %} · {{ p.type }}{% endif %}
  </div>

  {% if p.note %}
  <div class="muted"><small>{{ p.note }}</small></div>
  {% endif %}

  <div style="margin-top:8px;">
    {% if p.link %}<a href="{{ p.link }}">Link</a>{% endif %}
    {% if p.pdf %}{% if p.link %} · {% endif %}<a href="{{ p.pdf }}">PDF</a>{% endif %}
    {% if p.code %}{% if p.link or p.pdf %} · {% endif %}<a href="{{ p.code }}">Code</a>{% endif %}
  </div>
</div>
{% endfor %}
