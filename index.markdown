---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default     # use your custom layout, not the theme’s “home”
title: Home
---

<!-- ███  HERO / PROFILE  ███ -->
<header class="profile-hero">
  <img class="avatar" src="{{ site.avatar | relative_url }}" alt="{{ site.title }}">
  <div class="intro">
    <h1>{{ site.title }}</h1>
    <p>{{ site.description }}</p>
    <a class="btn" href="/about">About&nbsp;Me</a>
    <a class="btn outline" href="{{ '/assets/CV.pdf' | relative_url }}" target="_blank" rel="noopener">CV</a>
  </div>
</header>

{% comment %}
  Liquid collections
{% endcomment %}
{% assign highlights = site.posts | where_exp:'p','p.highlight == true' | sort:'date' | reverse %}
{% assign recent     = site.posts | where_exp:'p','p.highlight != true' | sort:'date' | reverse %}

<!-- ███  SHOWCASE  ███ -->
{% if highlights.size > 0 %}
<section class="highlight">
  <h2 class="section-title">Showcase</h2>
  <div class="cards showcase-cards">
    {% for post in highlights limit:4 %}
      {% include card.html post=post compact=false %}
    {% endfor %}
  </div>
</section>
{% endif %}

<!-- ███  MOST-RECENT  ███ -->
{% if recent.size > 0 %}
<section class="recent">
  <h2 class="section-title">Recent Posts</h2>
  <div class="cards">
    {% for post in recent limit:8 %}
      {% include card.html post=post compact=true %}
    {% endfor %}
  </div>
</section>
{% endif %}
