---
layout: splash
classes: wide
author_profile: false
author: wenxi
header:
  teaser: "/assets/images/portfolio/banner.png"
---

<link rel="stylesheet" href="https://unpkg.com/aos@2.3.1/dist/aos.css">

<div class="hero-section">
  <div class="hero-inner">

    <img src="{{ '/assets/images/me.png' | relative_url }}" class="avatar-main"
         data-aos="fade-in" data-aos-duration="800">

    <span class="title-greeting"
          data-aos="fade-down" data-aos-duration="900" data-aos-delay="100">
      Hey, There!
    </span>
 <span class="intro-paragraph"
      data-aos="fade-down" data-aos-duration="900" data-aos-delay="300">
  I turn enterprise complexity into decisions that land.
  <br><br>
  I have worked across SAP, BI, data analytics, and AI. I understand business process because I lived inside transformation projects. I built the data pipelines and delivered dashboard insights.
  <br><br>
  SAP. BI. Data analytics. AI. Delivery across supply chain, finance, HR, and retail.
  <br><br>
  PMP certified. SAP S/4HANA certified. CRISC trained.
</span>
    <div class="intro-nav-links">
      <a href="#home-content" class="scroll-to-home"
         data-aos="fade-right" data-aos-duration="600" data-aos-delay="500">Home</a>
      <a href="/mywork/"
         data-aos="fade-left" data-aos-duration="600" data-aos-delay="620">My Work</a>
      <a href="/mytoolbox/"
         data-aos="fade-right" data-aos-duration="600" data-aos-delay="740">Toolbox</a>
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

{% assign current_time = site.time | date: '%s' | plus: 0 %}

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">My Work</h3>
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

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">My Tookbox</h3>
<div class="entries-grid" data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">
  {% for post in site.posts %}
    {% if post.highlight_home and post.categories contains 'toolbox' %}
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

<h3 class="archive__subtitle" data-aos="fade-up" data-aos-duration="600">My Writing</h3>
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
  AOS.init({ once: true, easing: 'ease-out-cubic', offset: 80 });
  document.querySelector('.scroll-to-home').addEventListener('click', function(e) {
    e.preventDefault();
    document.getElementById('home-content').scrollIntoView({ behavior: 'smooth' });
  });
</script>
