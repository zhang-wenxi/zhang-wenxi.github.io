---
layout: splash
classes: wide
author_profile: false
author: wenxi
header:
  teaser: "/assets/images/portfolio/banner.png"
---

<link rel="stylesheet" href="https://unpkg.com/aos@2.3.1/dist/aos.css">

<div class="hero-section" style="background-image: linear-gradient(135deg, rgba(180,90,90,0.90) 0%, rgba(210,120,120,0.80) 40%, rgba(220,150,150,0.65) 70%, rgba(180,90,90,0.90) 100%), url('{{ '/assets/images/portfolio/banner.png' | relative_url }}'); background-size: cover, contain; background-repeat: no-repeat, no-repeat; background-position: center, center;">
  <div class="hero-inner">

    <img src="{{ '/assets/images/me.png' | relative_url }}" class="avatar-main"
         data-aos="fade-in" data-aos-duration="800">

    <span class="title-greeting"
          data-aos="fade-down" data-aos-duration="900" data-aos-delay="100">
      Hey, There!
    </span>

    <span class="intro-paragraph"
          data-aos="fade-down" data-aos-duration="900" data-aos-delay="300">
      I'm Wen Xi, an Enterprise Systems &amp; AI Data Platform Specialist
      who transforms complex ERPs into intelligent decision platforms,
      designing scalable data pipelines and analytics dashboards powered by modern AI.
    </span>

    <div class="intro-nav-links">
      <a href="#home-content" class="scroll-to-home"
         data-aos="fade-right" data-aos-duration="600" data-aos-delay="500">Home</a>
      <a href="/mywork/"
         data-aos="fade-left" data-aos-duration="600" data-aos-delay="620">My Work</a>
      <a href="/mywriting/"
         data-aos="fade-right" data-aos-duration="600" data-aos-delay="740">Writing</a>
      <a href="/about/"
         data-aos="fade-left" data-aos-duration="600" data-aos-delay="860">About Me</a>
    </div>

  </div>

  <div class="scroll-cue" onclick="document.getElementById('home-content').scrollIntoView({behavior:'smooth'})">
    <span>Scroll Down</span>
    <svg viewBox="0 0 24 24" fill="none" stroke-width="3" stroke-linecap="round" stroke-linejoin="round">
      <polyline points="6 9 12 15 18 9"/>
    </svg>
  </div>
</div>

<div id="home-content"></div>

{% assign current_time = 'now' | date: '%s' | plus: 0 %}

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">My Favorite Work</h3>
<div class="entries-grid" data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">
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

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">My Favorite Writing</h3>
<div class="entries-grid" data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">
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

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">Archive (Past Projects &amp; Posts)</h3>
<div class="entries-grid" data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">
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

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  AOS.init({ once: false, easing: 'ease-out-cubic', offset: 80 });
  document.querySelector('.scroll-to-home').addEventListener('click', function(e) {
    e.preventDefault();
    document.getElementById('home-content').scrollIntoView({ behavior: 'smooth' });
  });
</script>
