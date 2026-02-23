---
layout: default
title: "Portfolio"
section: portfolio
---
# Portfolio

{% assign samples = site.samples %}
{% if samples == nil %}
{% assign samples = "" | split: "" %}
{% endif %}
{% assign samples = samples | sort: "order" %}

<div class="portfolio-grid">
  {% for sample in samples %}
  <article class="portfolio-card">
    <a class="portfolio-card__media" href="{{ sample.url | relative_url }}" aria-label="View {{ sample.title }}">
      {% if sample.thumbnail %}
      <img src="{{ sample.thumbnail | relative_url }}" alt="{{ sample.thumbnail_alt | default: sample.title }}">
      {% else %}
      <div class="portfolio-card__placeholder">{{ sample.card_label | default: "Portfolio Sample" }}</div>
      {% endif %}
    </a>

    <div class="portfolio-card__body">
      <h2 class="portfolio-card__title">
        <a href="{{ sample.url | relative_url }}">{{ sample.title }}</a>
      </h2>

      {% if sample.summary %}
      <p class="portfolio-card__summary">{{ sample.summary }}</p>
      {% endif %}

      {% if sample.roles %}
      <p class="portfolio-card__meta"><strong>Roles:</strong> {{ sample.roles }}</p>
      {% endif %}

      <div class="portfolio-card__actions">
        <a class="button" href="{{ sample.url | relative_url }}">View project</a>
      </div>
    </div>
  </article>
  {% endfor %}
</div>
