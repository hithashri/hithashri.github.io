---
title: Blog
permalink: /blog/
---

# Blog

<p class="page-intro">Things I read, things I explored, things I want to remember.</p>

---

<div class="blog-grid">
{% for post in site.posts %}
  <a href="{{ post.url }}" class="blog-card">
    <span class="blog-card-date">{{ post.date | date: "%b %d, %Y" }}</span>
    <h3>{{ post.title }}</h3>
    <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    <span class="blog-card-read">Read →</span>
  </a>
{% endfor %}
</div>

{% if site.posts.size == 0 %}
<p>Nothing here yet. Check back soon.</p>
{% endif %}
