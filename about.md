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
  <source src="{{ '/assets/audio/alpha.ogg' | relative_url }}" type="audio/ogg">  
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

<script>
  const audio = document.getElementById('bgMusic');
  const playBtn = document.getElementById('playBtn');
  const muteBtn = document.getElementById('muteBtn');

  if (playBtn && audio) {
    playBtn.addEventListener('click', function() {
      // Check if the audio is actually ready to play
      if (audio.readyState < 2) {
        console.warn("Audio still loading, please wait a moment...");
        return; 
      }

      if (audio.paused) {
        // Set initial volume for fade-in
        audio.volume = 0;
        
        // Start playback and THEN handle the UI/Fade
        audio.play().then(() => {
          playBtn.innerHTML = '<i class="fas fa-pause"></i> <span>Pause</span>';
          
          // Smooth Fade-In Logic
          let fadeVolume = 0;
          const fadeIn = setInterval(() => {
            if (fadeVolume < 0.9) { 
              fadeVolume += 0.1;
              audio.volume = fadeVolume;
            } else { 
              audio.volume = 1; 
              clearInterval(fadeIn); 
            }
          }, 200);
        }).catch(error => {
          console.error("Playback blocked. Use a different browser or check the file path:", error);
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
      muteBtn.innerHTML = audio.muted ? 
        '<i class="fas fa-volume-mute"></i> <span>Unmute</span>' : 
        '<i class="fas fa-volume-up"></i> <span>Mute</span>';
    });
  }
</script>
{: .align-left}
![Zhang Wen Xi](/assets/images/me.png){:width="400px"}

## Analytical Geek. Data · AI · Enterprise DNA.

I started with logic and structure, learning how systems actually work under the hood. This was my primary passion. It led me to choose computer science as my first tertiary education after O levels. I continued to pursue a degree in computing with a major in systems development. I was thrilled with the delivery of bespoke applications in procurement and HR domains.

Then I spent years inside enterprise systems, learning how organisations run. SAP projects across supply chain, finance, and HR. Implementations in APAC, EMEA, and NA. Stakeholders who needed data they could trust, in a language they could act on. The insight that changed how I work: the data problem is almost never the data. It is the business process behind it. I have lived both sides. I build dashboards that get used. I run transformation programmes that land. I ship AI agents that run live. The enterprise depth is the advantage.

## What I deliver:

<span style="color:#F25270; font-weight:bold;">Analytics Engineering</span> 
dbt, BigQuery, Medallion architecture, Kimball star-schema
<br><span style="color:#F25270; font-weight:bold;">BI and Visualisation</span> 
Power BI, Tableau, QlikView, Streamlit dashboards
<br><span style="color:#F25270; font-weight:bold;">ML and AI</span> 
end-to-end MLOps, supply chain prediction, LLM-powered automation, CrewAI agents
<br><span style="color:#F25270; font-weight:bold;">Enterprise Systems</span> 
S/4HANA implementations across SCM, Finance and HR for clients in APAC, EMEA and NA

<h3 class="archive__subtitle">My Skills</h3>
{% include skills-grid.html %}
