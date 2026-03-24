---
permalink: /
title: "Peining Zhang"
layout: home
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% assign home = site.data.homepage %}

<section id="about-me" class="home-hero anchor-target">
  <div class="home-hero__intro">
    <p class="home-hero__eyebrow">About Me</p>
    <h1 class="home-hero__title">Hi! I am Peining Zhang (William)</h1>

    {% for paragraph in home.about.paragraphs %}
    <p class="home-copy">{{ paragraph }}</p>
    {% endfor %}

    <div class="home-links">
      <a class="home-button home-button--primary" href="{{ '/files/CV.pdf' | relative_url }}">View CV</a>
    </div>
  </div>
</section>

<section id="research-interests" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Research Interests</h2>
  </div>

  <div class="home-card-grid">
    {% for item in home.research_interests %}
    <article class="home-card">
      <h3>{{ item.title }}</h3>
      <p>{{ item.description }}</p>
    </article>
    {% endfor %}
  </div>
</section>

<section id="news" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>News</h2>
  </div>

  {% if home.news and home.news.size > 0 %}
  <div class="home-stack">
    {% for item in home.news %}
    <article class="home-list-item">
      <p class="home-list-item__meta">{{ item.period }}</p>
      <p>{{ item.description }}</p>
    </article>
    {% endfor %}
  </div>
  {% else %}
  <p class="home-empty">Add news items in <code>_data/homepage.yml</code> to populate this section.</p>
  {% endif %}
</section>

<section id="work-experiences" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Work Experiences</h2>
  </div>

  <div class="home-timeline">
    {% for item in home.work_experiences %}
    <article class="home-timeline__item">
      <div class="home-timeline__marker"></div>
      <div class="home-timeline__content">
        <p class="home-timeline__meta">{{ item.period }}</p>
        <h3>{{ item.title }}</h3>
        <p class="home-timeline__org">{{ item.organization }}</p>
        <p>{{ item.description }}</p>
      </div>
    </article>
    {% endfor %}
  </div>
</section>

<section id="publications" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Publications</h2>
  </div>

  {% if site.publications and site.publications.size > 0 %}
  <div class="home-stack">
    {% for post in site.publications reversed %}
    <article class="home-list-item">
      <p class="home-list-item__meta">{{ post.year }}</p>
      <h3 class="home-list-item__title">
        {% if post.paperurl %}
        <a href="{{ post.paperurl }}">{{ post.title }}</a>
        {% else %}
        {{ post.title }}
        {% endif %}
      </h3>
      <p>{{ post.authors }}</p>
      <p><strong>{{ post.venue }}</strong>{% if post.volume %}, {{ post.volume }}{% endif %}{% if post.issue %}({{ post.issue }}){% endif %}{% if post.article_number %}, Article {{ post.article_number }}{% endif %}</p>
    </article>
    {% endfor %}
  </div>
  {% else %}
  <p class="home-empty">Add entries in <code>_publications</code> to populate this section.</p>
  {% endif %}
</section>

<section id="honors-and-awards" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Honors and Awards</h2>
  </div>

  {% if home.honors_and_awards and home.honors_and_awards.size > 0 %}
  <div class="home-stack">
    {% for item in home.honors_and_awards %}
    <article class="home-list-item">
      <p class="home-list-item__meta">{{ item.period }}</p>
      <h3 class="home-list-item__title">{{ item.title }}</h3>
      {% if item.organization %}<p class="home-list-item__org">{{ item.organization }}</p>{% endif %}
      {% if item.description %}<p>{{ item.description }}</p>{% endif %}
    </article>
    {% endfor %}
  </div>
  {% else %}
  <p class="home-empty">This section is ready. Add awards in <code>_data/homepage.yml</code> when you want them to appear.</p>
  {% endif %}
</section>

<section id="services" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Services</h2>
  </div>

  {% assign teaching_items = site.teaching | sort: "date" | reverse %}
  {% if home.services.size > 0 or teaching_items.size > 0 %}
  <div class="home-stack">
    {% for item in home.services %}
    <article class="home-list-item">
      <p class="home-list-item__meta">{{ item.period }}</p>
      <h3 class="home-list-item__title">{{ item.title }}</h3>
      <p class="home-list-item__org">{{ item.organization }}</p>
      <p>{{ item.description }}</p>
    </article>
    {% endfor %}

    {% for item in teaching_items %}
    {% if item.term %}
    {% assign service_period = item.term %}
    {% else %}
    {% assign service_period = item.date | date: "%Y" %}
    {% endif %}
    <article class="home-list-item">
      <p class="home-list-item__meta">{{ service_period }}</p>
      <h3 class="home-list-item__title">{{ item.role | default: item.title }}</h3>
      <p class="home-list-item__org">{{ item.title }}{% if item.institution %}, {{ item.institution }}{% endif %}</p>
      <p>{{ item.content | strip_html | strip_newlines }}</p>
    </article>
    {% endfor %}
  </div>
  {% else %}
  <p class="home-empty">Add service records in <code>_data/homepage.yml</code> to populate this section.</p>
  {% endif %}
</section>

<section id="educations" class="home-section anchor-target">
  <div class="home-section__header">
    <h2>Educations</h2>
  </div>

  <div class="home-timeline">
    {% for item in home.educations %}
    <article class="home-timeline__item">
      <div class="home-timeline__marker"></div>
      <div class="home-timeline__content">
        <p class="home-timeline__meta">{{ item.period }}</p>
        <h3>{{ item.degree }}</h3>
        <p class="home-timeline__org">{{ item.institution }}</p>
        {% if item.description %}
        <p>{{ item.description }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
