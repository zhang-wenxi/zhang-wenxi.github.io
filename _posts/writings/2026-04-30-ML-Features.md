---
layout: posts
title: "Why better features will always beat better tuning"
author_profile: false
date:   2026-04-30
excerpt: "Why better features will always beat better tuning."
categories: [writing]
header:
  overlay_image: "https://images.unsplash.com/photo-1666875753105-c63a6f3bdc86?q=80&w=1173&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" # This shows in the grid
  overlay_color: "transparent" 
  teaser: "[/assets/images/articles/windsurf/teaser.png](https://images.unsplash.com/photo-1666875753105-c63a6f3bdc86?q=80&w=1173&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D")" # This shows in the grid
tags: ["Machine Learning"] # Or whatever name you want for the blue bar
tagline: "Machine Learning"
highlight_home: true     # Must be true to show on the homepage
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Source+Serif+4:ital,opsz,wght@0,8..60,400;0,8..60,600;1,8..60,400&display=swap');
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Source Serif 4',serif;color:var(--color-text-primary);line-height:1.75}
.article{max-width:680px;padding:2rem 0}
.kicker{font-size:11px;letter-spacing:0.15em;text-transform:uppercase;color:var(--color-text-secondary);font-family:var(--font-sans);margin-bottom:0.75rem}
h1{font-family:'Playfair Display',serif;font-size:36px;font-weight:700;line-height:1.2;margin-bottom:1rem}
.deck{font-size:18px;color:var(--color-text-secondary);line-height:1.6;margin-bottom:1.5rem;font-style:italic}
.byline{font-size:13px;color:var(--color-text-secondary);font-family:var(--font-sans);border-top:0.5px solid var(--color-border-tertiary);border-bottom:0.5px solid var(--color-border-tertiary);padding:0.6rem 0;margin-bottom:2rem}
.drop-cap::first-letter{font-family:'Playfair Display',serif;font-size:64px;font-weight:700;float:left;line-height:0.85;margin-right:8px;margin-top:6px;color:var(--color-text-primary)}
p{font-size:17px;margin-bottom:1.25rem;line-height:1.8}
.pullquote{border-left:3px solid var(--color-border-primary);padding:0.5rem 1.5rem;margin:2rem 0;font-family:'Playfair Display',serif;font-size:22px;font-style:italic;line-height:1.45;color:var(--color-text-primary)}
h2{font-family:'Playfair Display',serif;font-size:24px;font-weight:700;margin:2rem 0 0.75rem}
.stat-row{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:2rem 0}
.stat{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:1rem;text-align:center}
.stat-num{font-family:'Playfair Display',serif;font-size:28px;font-weight:700;display:block;margin-bottom:4px}
.stat-label{font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans);text-transform:uppercase;letter-spacing:0.08em}
.callout{background:var(--color-background-secondary);border-radius:var(--border-radius-lg);padding:1.25rem 1.5rem;margin:2rem 0;border:0.5px solid var(--color-border-tertiary)}
.callout-title{font-family:var(--font-sans);font-size:11px;text-transform:uppercase;letter-spacing:0.12em;color:var(--color-text-secondary);margin-bottom:0.75rem}
.pipeline-list{list-style:none;padding:0}
.pipeline-list li{font-size:15px;padding:6px 0;border-bottom:0.5px solid var(--color-border-tertiary);display:flex;gap:10px;font-family:var(--font-sans)}
.pipeline-list li:last-child{border-bottom:none}
.pipeline-list li span.tool{font-weight:500;min-width:160px;color:var(--color-text-primary)}
.pipeline-list li span.desc{color:var(--color-text-secondary)}
.verdict{margin:2.5rem 0;padding:1.5rem;border-radius:var(--border-radius-lg);border:0.5px solid var(--color-border-tertiary);background:var(--color-background-primary)}
.verdict-label{font-family:var(--font-sans);font-size:11px;text-transform:uppercase;letter-spacing:0.12em;color:var(--color-text-secondary);margin-bottom:0.5rem}
.verdict p{font-size:16px;margin-bottom:0}
.compare{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:2rem 0}
.compare-col{background:var(--color-background-secondary);border-radius:var(--border-radius-lg);padding:1.25rem;border:0.5px solid var(--color-border-tertiary)}
.compare-col.highlight{border-color:var(--color-border-secondary)}
.compare-col h3{font-family:var(--font-sans);font-size:13px;font-weight:500;text-transform:uppercase;letter-spacing:0.1em;margin-bottom:0.75rem;color:var(--color-text-secondary)}
.compare-col ul{list-style:none;padding:0}
.compare-col ul li{font-size:14px;font-family:var(--font-sans);padding:4px 0;color:var(--color-text-primary);line-height:1.5}
.compare-col ul li::before{content:"→ ";color:var(--color-text-secondary)}
.tag{display:inline-block;font-family:var(--font-sans);font-size:11px;background:var(--color-background-secondary);border:0.5px solid var(--color-border-tertiary);border-radius:20px;padding:3px 10px;margin-right:6px;color:var(--color-text-secondary)}
.tags{margin-bottom:1rem}
</style>
<div class="article">
  <div class="tags"><span class="tag">MLOps</span><span class="tag">Feature Engineering</span><span class="tag">Supply Chain</span></div>
  <div class="kicker">Data & Machine Learning</div>
  <h1>Why better features will always beat better tuning</h1>
  <p class="deck">The shipments were going late in completely predictable ways. Nobody caught the patterns — until we stopped rushing past the data.</p>
  <div class="byline">By Wen Xi Zhang &nbsp;·&nbsp; DataCo Late Delivery Predictor</div>

  <p class="drop-cap">In my past work, I saw shipments go late in ways that were completely predictable. Not weather. Not port strikes. Just patterns sitting quietly in the data that nobody caught before the parcel was already on the wrong truck. That frustration built this project.</p>

  <p>The DataCo Late Delivery Predictor is an end-to-end MLOps pipeline trained on 180,000 real shipment records — built to answer one question: can we flag a late delivery before it ever ships?</p>

  <div class="stat-row">
    <div class="stat"><span class="stat-num">180K</span><span class="stat-label">shipment records</span></div>
    <div class="stat"><span class="stat-num">0.69</span><span class="stat-label">F1-weighted score</span></div>
    <div class="stat"><span class="stat-num">66%</span><span class="stat-label">above baseline</span></div>
  </div>

  <p>Yes. At 0.69 F1-weighted score, 66% above a DummyClassifier baseline. But honestly? Before any model got built, EDA had to come first.</p>

  <div class="pullquote">"Get the EDA right. Everything else becomes clearer."</div>

  <h2>The step people rush — and why you shouldn't</h2>

  <p>EDA wasn't just data cleaning. It was how I got the scope right. It was how I discovered that shipping mode wasn't just another column — it turned out to be the number one SHAP driver of late deliveries.</p>

  <p>If I had skipped past that, I would have spent weeks tuning a model built on the wrong foundation. No amount of Optuna search or additional CV folds rescues a model that is missing the signal that matters most.</p>

  <div class="compare">
    <div class="compare-col">
      <h3>Hyperparameter tuning</h3>
      <ul>
        <li>Marginal gains at the edges</li>
        <li>Requires compute budget</li>
        <li>Works within the existing signal</li>
        <li>Faster to execute</li>
      </ul>
    </div>
    <div class="compare-col highlight">
      <h3>Feature engineering</h3>
      <ul>
        <li>Unlocks entirely new signal</li>
        <li>Requires domain knowledge</li>
        <li>Changes what the model can learn</li>
        <li>Needs business collaboration</li>
      </ul>
    </div>
  </div>

  <h2>What the full pipeline includes</h2>

  <div class="callout">
    <div class="callout-title">Pipeline components</div>
    <ul class="pipeline-list">
      <li><span class="tool">ZenML</span><span class="desc">Orchestrated, reproducible pipelines</span></li>
      <li><span class="tool">MLflow</span><span class="desc">Experiment tracking and model registry</span></li>
      <li><span class="tool">37-month backtest</span><span class="desc">Walk-forward validation, not a cherry-picked holdout</span></li>
      <li><span class="tool">SHAP explainability</span><span class="desc">Understand what the model actually learned</span></li>
      <li><span class="tool">Data drift monitoring</span><span class="desc">With rollback capability</span></li>
      <li><span class="tool">Executive dashboard</span><span class="desc">Shows the cost of every wrong prediction</span></li>
    </ul>
  </div>

  <p>Most ML demos stop at the notebook. This one doesn't. The executive Streamlit dashboard surfaces the business cost of each wrong prediction — because a false negative in late delivery has a real dollar figure attached to it.</p>

  <h2>The real unlock is new data</h2>

  <p>Yes, you can improve with lower thresholds, more CV folds, and broader Optuna hyperparameter search. Those help at the margins. You have to weigh your resources and be creative about where you spend them.</p>

  <div class="pullquote">"The real unlock is new data — and that conversation has to happen between business and data together."</div>

  <p>What derived features are we missing? What domain knowledge never made it into a column? That conversation is where the model actually gets better. And that means sitting down as a team and asking what we should be collecting next.</p>

  <div class="verdict">
    <div class="verdict-label">The honest take</div>
    <p>Every iteration throws up new ideas. The model keeps testing your imagination and then asks you to be honest about what is actually buildable. That back and forth between ambition and reality is where the real learning happens.</p>
  </div>

</div>
