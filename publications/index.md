---
layout: default
title: Publications
---

{% assign pubs = site.data.publications | sort: "year" | reverse %}
{% assign n_total = pubs | size %}

{% for p in pubs %}
{% assign num = n_total | minus: forloop.index0 %}

{% assign authors_bold = p.authors
  | replace: "Yunteng Cao#", "<strong>Yunteng Cao</strong>#"
  | replace: "Yunteng Cao", "<strong>Yunteng Cao</strong>"
%}

<div class="card">
  <div><strong>[{{ num }}]</strong> <strong>{{ p.title }}</strong></div>

  {% if p.authors %}
  <div class="muted">{{ authors_bold }}</div>
  {% endif %}

  <div>
    {% if p.journal %}{{ p.journal }}{% endif %}
    {% if p.details %}{% if p.journal %} · {% endif %}{{ p.details }}{% endif %}
    {% if p.year %}{% if p.journal or p.details %} · {% endif %}{{ p.year }}{% endif %}
    {% if p.type %} · {{ p.type }}{% endif %}
  </div>

  {% if p.note %}
  <div class="muted"><small>{{ p.note }}</small></div>
  {% endif %}

  <div style="margin-top:8px;">
    {% if p.url %}<a href="{{ p.url }}">Link</a>{% endif %}
    {% if p.doi %}{% if p.url %} · {% endif %}<a href="https://doi.org/{{ p.doi }}">DOI</a>{% endif %}
    {% if p.pdf %}{% if p.url or p.doi %} · {% endif %}<a href="{{ p.pdf }}">PDF</a>{% endif %}
    {% if p.code %}{% if p.url or p.doi or p.pdf %} · {% endif %}<a href="{{ p.code }}">Code</a>{% endif %}
  </div>
</div>
{% endfor %}
