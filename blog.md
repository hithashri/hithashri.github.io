---
title: Blog
permalink: /blog/
---

# Blog

<p class="page-intro">Things I read, things I explored, things I want to remember. No schedule, no pressure.</p>

---

{% for post in site.posts %}
<div class="blog-post-preview">
  <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
  <p class="meta">{{ post.date | date: "%B %d, %Y" }}{% if post.tags.size > 0 %} · {% for tag in post.tags %}<span class="badge">{{ tag }}</span> {% endfor %}{% endif %}</p>
  <p>{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
</div>
{% endfor %}

{% if site.posts.size == 0 %}
<p>Nothing here yet. Check back soon.</p>
{% endif %}
