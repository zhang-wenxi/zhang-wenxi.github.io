---
layout: home
classes: wide
author_profile: true
author: wenxi
header:
  teaser: "/assets/images/portfolio/banner.png" 
---

<!-- AOS CSS -->
<link rel="stylesheet" href="https://unpkg.com/aos@2.3.1/dist/aos.css">

<div class="custom-layout-wrapper"> 
  <div class="intro-container">
    <img src="/assets/images/me.png" class="avatar-main" data-aos="fade-in" data-aos-duration="800">    
    <div class="intro-text">

      <!-- Fly in from top -->
      <span class="title-greeting" data-aos="fade-down" data-aos-duration="700">Hey, There!</span>

      <!-- Fly in from top, slight delay -->
      <span class="intro-paragraph" data-aos="fade-down" data-aos-duration="800" data-aos-delay="200">
        I'm Wen Xi, an Enterprise Systems &amp; AI Data Platform Specialist who transforms complex ERPs into intelligent decision platforms, designing scalable data pipelines and analytics dashboards powered by modern AI.
      </span>

      <!-- Nav links: horizontal, alternating left/right -->
      <div class="intro-nav-links">
        <a href="#home-content" class="scroll-to-home" data-aos="fade-right" data-aos-duration="600" data-aos-delay="400">Home</a>
        <a href="/mywork/" data-aos="fade-left"  data-aos-duration="600" data-aos-delay="550">My Work</a>
        <a href="/mywriting/" data-aos="fade-right" data-aos-duration="600" data-aos-delay="700">Writing</a>
        <a href="/about/" data-aos="fade-left"  data-aos-duration="600" data-aos-delay="850">About Me</a>
      </div>

    </div>
  </div>
</div>

<!-- ANCHOR: Home link scrolls here -->
<div id="home-content"></div>

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
                {% include archive-single.html type="grid" %}
            {% endif %}
        {% endif %}
    {% endfor %}
</div>

<!-- 2. FAVORITE ARTICLES -->
<h3 class="archive__subtitle">My Favorite Writing</h3>
<div class="entries-grid">
    {% for post in site.posts %}
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

<!-- 3. ARCHIVE -->
<h3 class="archive__subtitle">Archive (Past Projects &amp; Posts)</h3>
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

<!-- AOS JS + smooth scroll -->
<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  AOS.init({ once: true, easing: 'ease-out-cubic' });

  // Smooth scroll for Home link
  document.querySelector('.scroll-to-home').addEventListener('click', function(e) {
    e.preventDefault();
    document.getElementById('home-content').scrollIntoView({ behavior: 'smooth' });
  });
</script>
