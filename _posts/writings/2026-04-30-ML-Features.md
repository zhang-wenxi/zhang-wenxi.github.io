---
layout: posts
title: "Feature Engineering Drives More Improvement Than Hyperparameter Tuning"
author_profile: false
date:   2026-04-30 00:00:00 +0800
excerpt: "A case study from the DataCo Late Delivery Predictor."
categories: [writing]
header:
  overlay_image: "https://images.unsplash.com/photo-1666875753105-c63a6f3bdc86?q=80&w=1173&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
  overlay_color: "transparent"
  teaser: "https://images.unsplash.com/photo-1666875753105-c63a6f3bdc86?q=80&w=1173&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
  caption: "Photo credit: [Unsplash: Deng Xiang](https://unsplash.com/@dengxiangs)"
tags: ["Machine Learning", "Supply Chain", "MLOps"]
tagline: "Machine Learning"
highlight_home: true
---

The DataCo Late Delivery Predictor is an end-to-end MLOps pipeline trained on 180,000 shipment records. It predicts late deliveries before they ship.

| Metric | Value |
|---|---|
| F1-weighted score | 0.69 |
| Improvement vs. DummyClassifier baseline | +66% |
| Validation method | 37-month walk-forward backtest |
| Top SHAP driver | Shipping mode |

<h3 class="archive__subtitle">Why Feature Engineering Comes First</h3>

Feature engineering creates new signal. Hyperparameter tuning optimises within existing signal. If the signal is weak, tuning cannot rescue it.

In this dataset, shipping mode was the top driver of late deliveries according to [SHAP analysis](https://shap.readthedocs.io/en/latest/). That column existed raw in the data. Other derived features required construction. Days since last shipment per customer-supplier pair. Rolling average delay by route over 30-day windows. A port congestion flag derived from external weather and holiday data. Each derived feature added measurable lift. Hyperparameter tuning alone could not have discovered these patterns.

In this project, feature engineering on domain variables produced the majority of the lift. Hyperparameter tuning added incremental gains on top of that foundation.

<h3 class="archive__subtitle">What the Full Pipeline Includes</h3>

The project uses standard MLOps tooling for reproducibility. [ZenML](https://www.zenml.io/) handles pipeline orchestration. [MLflow](https://mlflow.org/) manages experiment tracking and the model registry. Validation uses a 37-month walk-forward backtest, not a cherry-picked holdout split. [SHAP](https://shap.readthedocs.io/en/latest/) provides model explainability. Evidently monitors for data drift with rollback capability. A Streamlit executive dashboard surfaces the business cost of each wrong prediction, because a false negative in late delivery has a real dollar figure attached to it.

Most ML demos stop at the notebook. This one does not.

The code is available on [GitHub](https://github.com/zhang-wenxi).

<h3 class="archive__subtitle">When to Tune Anyway</h3>

Hyperparameter tuning is not useless. It adds value after feature engineering is exhausted. The mistake is doing tuning first, or only.

| Priority | Activity | Impact |
|---|---|---|
| 1 | Feature engineering | High (primary driver of lift) |
| 2 | Hyperparameter tuning | Incremental (adds on top) |

<h3 class="archive__subtitle">The Decision Order Matters</h3>

Build the right features first. Then tune. The decision order matters. Not after the model is deployed.
