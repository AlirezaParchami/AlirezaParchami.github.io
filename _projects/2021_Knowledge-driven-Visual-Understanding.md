---
layout: page
title: Teaching AI the Rules of the Road
description: EPFL Porject on Knowledge-driven Trajectory Prediction for Autonomous Vehicles
img: assets/img/projects/2021_Knowledge-driven-Visual-Understanding/negative_samples.png
importance: 4
category: Work
related_publications: false
---


### 📍 Research Internship @ EPFL

Predicting where a car will go is easy; predicting where it _should_ go while respecting the laws of physics and the rules of the road is the real challenge. During my 4-month research internship at the **EPFL VITA Lab**, I worked on "Knowledge-Aware Trajectory Prediction", a project dedicated to making autonomous systems safer by injecting human-like "domain knowledge" into neural networks.


---

### 🚗 The Challenge: Beyond Data-Driven Guesses

Traditional trajectory predictors are often purely data-driven. While they are great at following patterns, they lack "common sense." This leads to two critical failures:

1. **Collisions:** Overlapping with other vehicles or pedestrians.
    
2. **Off-Road Predictions:** Predicting paths that go onto sidewalks, grass, or through buildings.
    

My task was to move beyond simple pattern matching and teach the model to understand the **constraints** of its environment.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2021_Knowledge-driven-Visual-Understanding/negative_samples.png" title="Final Render" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">The negative samples where vehicle should avoid to predict the trajectory</div>
    </div>
</div>

---


### The Solution: Contrastive Learning

To solve this, we utilized **[Contrastive Learning](https://alirezaparchami.github.io/blog/2021/Contrastive-Learning/)** (specifically inspired by Social NCE \[1\]). Think of it as a "Carrot and Stick" approach for AI:

- **The Carrot (Positive Samples):** We pull the model toward the "Ground Truth"—the actual path a safe driver took.
    
- **The Stick (Negative Samples):** We push the model away from "forbidden" zones, like off-road areas or collision points.
    

##### **Negative Data Augmentation**

A key part of my research involved **Negative Sampling**. We developed a geometrical solution to detect off-road points from map data and generated "unpleasant" scenarios. By intentionally showing the model what a "bad" path looks like, we taught it to avoid those areas entirely.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2021_Knowledge-driven-Visual-Understanding/point_samples.png" title="Final Render" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Scene representation with data points, extracted from map data</div>
    </div>
</div>

---


### Implementation & Architecture

We integrated these concepts into the **SVG-Net** architecture \[2\]. By modifying the embedding space, we ensured that the model's internal representations of "safe" paths were mathematically distant from "unsafe" ones.

The core of this learning is governed by the **Contrastive Loss** function:

$$\mathcal{L}_C = -\log \frac{\exp(\text{sim}(f(Z), g(k^+)) / \tau)}{\sum_{n=0}^{N} \exp(\text{sim}(f(Z), g(k_n)) / \tau)}$$

_Where the model learns to maximize similarity with the positive sample ($k^+$) and minimize it for all negative samples ($k_n$)_.


---

### The Impact: Safer Predictions

The results were clear. By "injecting" knowledge into the baseline model, we saw significant improvements in how the AI respected road boundaries:

<div align="center">

| Metric | Improvement |
| :--- | :--- |
| **Total Off-Road Points** | **11% Reduction** |
| **Off-Road Samples** | **14.8% Reduction** |

</div>

These numbers represent more than just statistics; they represent a model that is fundamentally more aware of its surroundings and less likely to make dangerous, "illegal" maneuvers in a real-world setting.


---

References:

\[1\]: Social NCE: Contrastive Learning of Socially-aware Motion Representations, Y. Liu and Q. Yan and A. Alahi, 2021 
\[2\]: SVG-Net: An SVG-based Trajectory Prediction Model, M. Bahari, V. Zehtab, S. Khorasani, S. Ayromlou, S.Saadatnejad, A. Alahi 

<div class="row justify-content-center">
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2021_Knowledge-driven-Visual-Understanding/Logo_EPFL.png" title="Final Render" class="img-fluid rounded z-depth-1" %}
    </div>
</div>