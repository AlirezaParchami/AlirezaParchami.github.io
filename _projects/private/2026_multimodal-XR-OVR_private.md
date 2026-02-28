---
layout: page
title: R&D at Mercedes-Benz Tech Innovation
description: Multimodal AI Fusion, Spatial Computing, and In-Vehicle XR
permalink: /private/2026_multimodal-XR-OVR_private/
img: 
category: private
related_publications: false
---


> **Note:** This page is solely for specific people I have shared my CV to learn about some parts of my thesis project, until we publish it publically. Please do not share this link.


##### **Multimodal AI Fusion for Outside-the-Vehicle Referencing (OVR) using XR Inside the Moving Vehicle**
**Role:** XR Researcher (Master Thesis)  
**Organization:** Mercedes-Benz Tech Innovation, Stuttgart, Germany  
**Keywords:** `Spatial Computing`, `Sensor Fusion`, `Transformers`, `Digital Twins`, `Human-Computer Interaction`


> **TL;DR:** I engineered a real-time multimodal XR pipeline fusing user gaze and speech to solve the Outside-the-Vehicle Referencing (OVR) problem. By architecting a custom Transformer-based fusion network and pioneering a synchronized moving-car data pipeline, the system achieved state-of-the-art accuracy, earning endorsement from Mercedes-Benz for future production R&D.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2026_Multimodal-XR-OVR/augmented journey.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<hr style="margin: 1.3rem 0; border: none; border-top: 2px solid rgba(0, 0, 0, 0.4);">


### **The Challenge: Contextual Referencing in Dynamic Environments**
Traditional Extended Reality (XR) systems rely heavily on static environments or explicit pointing mechanisms (e.g., ray-casting via controllers). However, inside a moving vehicle, high-speed ego-motion and the cognitive load of passengers render explicit pointing unnatural. 

Meanwhile, using XR headsets for passengers has proved to be effective and useful, helping passengers gain information about physical buildings acting as their points of interest (POI). However, the core issue is that there is no robust way to accurately estimate a passenger's target POI in motion—a challenge known as **Outside-the-Vehicle Referencing (OVR)**.

The objective was to design a **frictionless, real-time spatial interaction paradigm**: allowing passengers to simply look at a building out the window, ask a natural language question (e.g., *"When was that church built?"*), and receive an accurate, context-aware response.

### **Core Engineering & Methodology**
To solve the OVR challenge without relying on obtrusive controllers, I developed an end-to-end data and machine learning pipeline optimized for real-time vehicular deployment.

* **Data Engineering & Digital Twins:** Pioneered a custom moving-car data acquisition study. I built a robust framework to strictly synchronize vehicle state telemetry (GNSS/INS trajectory) with continuous passenger head kinematics, mapping real-world motion into a high-fidelity 3D Digital Twin.
* **Multimodal Architecture:** Architected a low-latency neural network leveraging advanced semantic language encoders and custom Transformer-based cross-attention mechanisms. This allowed the model to dynamically align discrete natural language queries with continuous spatial gaze vectors.
* **Loss Optimization:** Engineered temporal aggregation strategies to stabilize the model's training dynamics against highly volatile, real-world motion data, effectively optimizing the precision-recall trade-off and mitigating probability polarization.


### **Results & Impact**
By exploiting the natural redundancy of human gaze and aligning it with semantic context, the final architecture represents a significant leap forward in automotive spatial computing. 

* **Performance:** Achieved highly robust Rank-1 Accuracy and F1-Scores, outperforming existing state-of-the-art baselines by over 10% in dynamic, in-vehicle contexts.
* **Industry Validation:** The methodology and spatial fusion framework were validated by Mercedes-Benz management as a highly viable candidate for integration into future production R&D pipelines.

***
*Tools & Technologies: PyTorch, Transformers, LLMs, Unity3D, Python, GNSS/INS Telemetry, Sensor Fusion.*