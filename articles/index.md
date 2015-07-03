---
layout: page
title: Archive List
excerpt: "An archive of articles sorted by date."
search_omit: true
---

<ul class="post-list">
{% for post in site.categories.articles %}
  {% if post.sample and site.showSample != true %} {% continue %} {% endif %}
  <li>
    <article>
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }}
        <span class="entry-date">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
        </span>
        {% if post.excerpt %} <span class="excerpt">{{ post.excerpt }}</span>{% endif %}
      </a>
    </article>
  </li>
{% endfor %}
</ul>
