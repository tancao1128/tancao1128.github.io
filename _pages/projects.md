---
layout: page
title: projects
permalink: /projects/
description: Research projects on optimization, control, and variational analysis, plus undergraduate research ideas for AMS 487 and prospective students at SUNY Korea.
nav: true
nav_order: 3
display_categories: [research, undergraduate]
horizontal: false
---

{% assign meta = site.data.project_meta %}
{% assign all_projects = site.projects | sort: 'importance' %}
{% assign research = all_projects | where: 'category', 'research' %}
{% assign ug = all_projects | where: 'category', 'undergraduate' %}

<style>
  .pj-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin: 1rem 0 1.5rem;
  }
  .pj-chip {
    border: 1px solid var(--global-divider-color);
    border-radius: 999px;
    padding: 0.2rem 0.8rem;
    font-size: 0.85rem;
    color: var(--global-text-color);
    background: var(--global-card-bg-color);
    cursor: pointer;
  }
  .pj-chip:hover,
  .pj-chip.active {
    border-color: var(--global-theme-color);
    color: var(--global-theme-color);
  }
  .pj-section {
    margin-top: 2.5rem;
    padding-bottom: 0.4rem;
    border-bottom: 1px solid var(--global-divider-color);
  }
  .pj-section small {
    color: var(--global-text-color-light);
    font-weight: 400;
    font-size: 0.9rem;
    margin-left: 0.5rem;
  }
  .pj-card {
    display: flex;
    flex-direction: column;
    height: 100%;
    padding: 1rem 1.1rem;
    border: 1px solid var(--global-divider-color);
    border-left: 4px solid var(--pj-accent, var(--global-theme-color));
    border-radius: 6px;
    background: var(--global-card-bg-color);
    color: var(--global-text-color);
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease;
  }
  a:hover .pj-card {
    transform: translateY(-2px);
    box-shadow: 0 4px 14px rgba(0, 0, 0, 0.12);
  }
  .pj-card h3 {
    font-size: 1.05rem;
    margin: 0.35rem 0 0.4rem;
    line-height: 1.3;
  }
  .pj-card p {
    font-size: 0.9rem;
    margin-bottom: 0.7rem;
    color: var(--global-text-color);
  }
  .pj-meta {
    margin-top: auto;
    font-size: 0.8rem;
    color: var(--global-text-color-light);
    line-height: 1.5;
  }
  .pj-badges {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }
  .pj-badge {
    padding: 0.05rem 0.5rem;
    border-radius: 3px;
    border: 1px solid var(--global-divider-color);
    color: var(--global-text-color-light);
  }
  .pj-badge.level {
    color: var(--pj-accent);
    border-color: var(--pj-accent);
    font-weight: 600;
  }
  .pj-lvl-1 {
    --pj-accent: #2e9d6a;
  }
  .pj-lvl-2 {
    --pj-accent: #2f7fd1;
  }
  .pj-lvl-3 {
    --pj-accent: #c0662a;
  }
  .pj-research {
    --pj-accent: var(--global-theme-color);
  }
  .pj-grid > .col {
    margin-bottom: 1.2rem;
  }
  .pj-apply ul {
    margin-bottom: 0.5rem;
  }
</style>

<p class="lead mb-0">
  My research develops the variational analysis, optimal control, and numerical methods for
  systems with constraints and contact, and applies them to crowds, vehicles, and learning.
  The undergraduate projects below are entry points into the same ideas.
</p>

<div class="pj-chips">
  <a class="pj-chip" href="#research">Research ({{ research | size }})</a>
  <a class="pj-chip" href="#undergraduate">Undergraduate projects ({{ ug | size }})</a>
  <a class="pj-chip" href="#apply">How to apply</a>
  <a class="pj-chip" href="/undergraduate-research/">Preparation roadmap</a>
</div>

<h2 id="research" class="pj-section">Research <small>ongoing lines of work</small></h2>

<div class="row row-cols-1 row-cols-md-3 pj-grid mt-3">
  {% for project in research %}
    {% assign m = meta[project.slug] %}
    <div class="col">
      <a href="{{ project.url | relative_url }}" class="text-decoration-none">
        <div class="pj-card pj-research">
          <div class="pj-badges">
            <span class="pj-badge level">{{ m.status }}</span>
          </div>
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <div class="pj-meta">
            {{ m.tags | join: ' · ' }}
            {% if m.note %}<br>{{ m.note }}{% endif %}
          </div>
        </div>
      </a>
    </div>
  {% endfor %}
</div>

<h2 id="undergraduate" class="pj-section">
  Undergraduate projects <small>AMS 487, independent study, or a first research experience</small>
</h2>

<div class="pj-chips" id="pj-filters">
  <button type="button" class="pj-chip active" data-filter="all">All</button>
  {% for t in meta.tracks %}
    <button type="button" class="pj-chip" data-filter="{{ t[0] }}">{{ t[1] }}</button>
  {% endfor %}
</div>

<div class="row row-cols-1 row-cols-md-3 pj-grid" id="pj-ug-grid">
  {% for lvl in (1..3) %}
    {% for project in ug %}
      {% assign m = meta[project.slug] %}
      {% if m.level == lvl %}
        <div class="col" data-track="{{ m.track }}">
          <a href="{{ project.url | relative_url }}" class="text-decoration-none">
            <div class="pj-card pj-lvl-{{ lvl }}">
              <div class="pj-badges">
                <span class="pj-badge level">{{ meta.levels[lvl] }}</span>
                <span class="pj-badge">{{ meta.tracks[m.track] }}</span>
              </div>
              <h3>{{ project.title | remove_first: 'UG: ' }}</h3>
              <p>{{ project.description }}</p>
              <div class="pj-meta">
                <strong>Time:</strong> {{ m.time }}<br>
                <strong>Background:</strong> {{ m.prereq }}
              </div>
            </div>
          </a>
        </div>
      {% endif %}
    {% endfor %}
  {% endfor %}
</div>

<p class="text-muted small">
  Levels: <strong>Intro</strong> needs only first-year calculus and linear algebra.
  <strong>Core</strong> assumes one or two further courses. <strong>Advanced</strong> is the most
  programming- and prerequisite-heavy.
</p>

<h2 id="apply" class="pj-section">How to apply</h2>

<div class="pj-apply mt-3">
  <p>
    Not sure which project fits? Start with an <strong>Intro</strong> project and a short trial of
    four to six weeks. Email me (see the <a href="/">contact page</a>) with:
  </p>
  <ul>
    <li>your relevant courses in calculus, linear algebra, probability, optimization, and programming;</li>
    <li>one paragraph on why a project interests you;</li>
    <li>any prior experience in Python, statistics, or machine learning.</li>
  </ul>
  <p>
    No project requires prior research experience. Curiosity and follow-through matter most. The
    <a href="/undergraduate-research/">preparation roadmap</a> lists the courses and skills that help.
  </p>
</div>

<script>
  (function () {
    var bar = document.getElementById('pj-filters');
    var cards = document.querySelectorAll('#pj-ug-grid > .col');
    if (!bar) return;
    bar.addEventListener('click', function (e) {
      var b = e.target.closest('button[data-filter]');
      if (!b) return;
      var f = b.getAttribute('data-filter');
      bar.querySelectorAll('.pj-chip').forEach(function (x) {
        x.classList.toggle('active', x === b);
      });
      cards.forEach(function (c) {
        c.style.display = f === 'all' || c.getAttribute('data-track') === f ? '' : 'none';
      });
    });
  })();
</script>
