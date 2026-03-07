---
layout: archive
title: "About Me"
author: wenxi
author_profile: true
classes: wide
permalink: /about/
---
<!-- 1. Audio Element (No Autoplay) -->
<audio id="bgMusic" loop preload="auto">
  <source src="{{ '/assets/audio/AlphaMattCole.mp3' | relative_url }}" type="audio/mpeg">
</audio>

<!-- 2. Floating Controls Container -->
<div class="floating-audio-controls">
  <!-- Play/Pause Button -->
  <button id="playBtn" class="ctrl-btn">
    <i class="fas fa-play"></i> <span>Play</span>
  </button>

  <!-- Mute/Unmute Button -->
  <button id="muteBtn" class="ctrl-btn">
    <i class="fas fa-volume-up"></i> <span>Mute</span>
  </button>
</div>

<!-- 3. Floating Styles -->
<style>
  .floating-audio-controls {
    position: fixed;
    bottom: 25px;
    right: 25px;
    display: flex;
    gap: 12px;
    z-index: 9999; /* Ensure it stays on top */
    background: rgba(255, 255, 255, 0.8); 
    padding: 10px 15px;
    border-radius: 50px;
    box-shadow: 0 8px 32px rgba(0,0,0,0.15);
    backdrop-filter: blur(10px); /* Modern blur effect */
    border: 1px solid rgba(255, 255, 255, 0.3);
  }

  .ctrl-btn {
    padding: 8px 16px;
    cursor: pointer;
    border-radius: 30px;
    border: 1px solid #ddd;
    background: white;
    font-size: 14px;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: all 0.3s ease;
  }

  .ctrl-btn:hover {
    background: #f8f9fa;
    transform: translateY(-3px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }
</style>

<!-- 4. Logic Script (Fade-in + Toggles) -->
<script>
  const audio = document.getElementById('bgMusic');
  const playBtn = document.getElementById('playBtn');
  const muteBtn = document.getElementById('muteBtn');

  // Play/Pause Toggle with Fade-In
  if (playBtn && audio) {
    playBtn.addEventListener('click', function() {
      if (audio.paused) {
        // Start fade-in only if the music hasn't started yet
        if (audio.currentTime === 0) {
          audio.volume = 0;
          const fadeIn = setInterval(() => {
            if (audio.volume < 0.9) { audio.volume += 0.1; }
            else { audio.volume = 1; clearInterval(fadeIn); }
          }, 200);
        }
        
        audio.play().then(() => {
          playBtn.innerHTML = '<i class="fas fa-pause"></i> <span>Pause</span>';
        });
      } else {
        audio.pause();
        playBtn.innerHTML = '<i class="fas fa-play"></i> <span>Play</span>';
      }
    });
  }

  // Mute/Unmute Toggle
  if (muteBtn && audio) {
    muteBtn.addEventListener('click', function() {
      audio.muted = !audio.muted;
      if (audio.muted) {
        muteBtn.innerHTML = '<i class="fas fa-volume-mute"></i> <span>Unmute</span>';
      } else {
        muteBtn.innerHTML = '<i class="fas fa-volume-up"></i> <span>Mute</span>';
      }
    });
  }
</script>

{: .align-left}
![Zhang Wen Xi](/assets/images/me.png){:width="400px"}

## Enterprise Systems & AI Data Platform Specialist
I began my career as a software engineer before spending over a decade leading business intelligence solutions with Power BI and Tableau and orchestrating SAP S/4HANA implementations across SCM, Finance, and HR.

Today I design scalable data platforms that connect enterprise operations with modern analytics and AI. My current work includes developing an end to end EDA dashboard for job market profiling covering data cleaning, transformation, modeling, and visualization, and building a big data pipeline using MongoDB and Google BigQuery.

I transform enterprise ERPs into AI decision platforms via data engineering and product strategy.

<h3 class="archive__subtitle">My Skills</h3>

{% include skills-grid.html %}

