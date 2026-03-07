---
layout: home
classes: wide
author_profile: true
author : wenxi
---

{% assign current_time = site.time | date: '%s' | plus: 0 %}

<h2 class="title-greeting"> Hey, There!</h2>
<p> I'm Wen Xi, an Enterprise Systems & AI Data Platform Specialist who transforms complex ERPs into intelligent decision platforms, designing scalable data pipelines and analytics dashboards powered by modern AI. Check out My Work and My Writing to explore projects and insights.</p>

<!-- 1. FAVORITE PROJECTS -->
<h3 class="archive__subtitle">My Favorite Work</h3>
<div class="entries-grid">
    {% for post in site.posts %}
        {% if post.highlight_home and post.categories contains 'work' %}
            {% if post.expiry_date %}
                {% assign post_expiry = post.expiry_date | date: '%s' | plus: 0 %}
                {% if post_expiry > current_time %}
                    {% include archive-single.html type="grid" %}
                {% endif %}
            {% else %}
                {% comment %} No expiry date? Keep it here forever {% endcomment %}
                {% include archive-single.html type="grid" %}
            {% endif %}
        {% endif %}
    {% endfor %}
</div>

<!-- 2. FAVORITE ARTICLES -->
<h3 class="archive__subtitle">My Favorite Writing</h3>
<div class="entries-grid">
    {% for post in site.posts %}
        {% comment %} Changed 'article' to 'writing' to match your post file {% endcomment %}
        {% if post.highlight_home and post.categories contains 'writing' %}
            {% if post.expiry_date %}
                {% assign post_expiry = post.expiry_date | date: '%s' | plus: 0 %}
                {% if post_expiry > current_time %}
                    {% include archive-single.html type="grid" %}
                {% endif %}
            {% else %}
                {% include archive-single.html type="grid" %}
            {% endif %}
        {% endif %}
    {% endfor %}
</div>
<!-- 3. ARCHIVE (Only shows posts that HAVE an expiry date in the past) -->
<h3 class="archive__subtitle">Archive (Past Projects & Posts)</h3>

<div class="entries-grid">
    {% for post in site.posts %}
        {% if post.expiry_date %}
            {% assign post_expiry = post.expiry_date | date: '%s' | plus: 0 %}
            {% if post_expiry < current_time %}
                {% include archive-single.html type="grid" %}
            {% endif %}
        {% endif %}
    {% endfor %}
</div>

{% include paginator.html %}
