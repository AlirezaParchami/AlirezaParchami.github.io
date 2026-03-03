---
layout: post
title: "From Text to Physical AI - Part 0: Overview"
date: 2025-12-01 08:00:00
description: Notes on my study journey to prepare for NVIDIA Interview
tags: AI
categories: Science Blog
giscus_comments: false
related_posts: false
related_publications: false
thumbnail:
---


## Part 2: The Eyes — Vision-Language Models (VLMs)

How do we teach a text-based brain to see? We don't use complex Cross-Attention layers anymore. We use a simpler, highly scalable trick: **Token Concatenation**.

#### **The VLM Pipeline (e.g., LLaVA)**

1. **The Vision Encoder (ViT):** An image is sliced into patches (e.g., $14 \times 14$ pixels). A frozen Vision Transformer (like CLIP or SigLIP) processes these patches into semantic feature vectors (e.g., 1024 dimensions). It doesn't output raw pixels; it outputs "meaning."
2. **The Projector (The Bridge):** The LLM expects 4096-dimensional vectors, but the ViT outputs 1024-dimensional vectors. A small 2-layer MLP (the Projector) translates the visual features into the LLM's native embedding space.
3. **Fusion:** We simply concatenate the lists. The input to the LLM becomes:
    `[Visual_Token_1, ..., Visual_Token_576, Text_Token_1, ...]`
4. **Attention:** The combined sequence flows into the Transformer blocks, where RoPE is applied dynamically. To the LLM, the image is just a "foreign language" paragraph at the start of the prompt.


---

## Part 3: The Muscles — Vision-Language-Action (VLAs)

This is where AI touches the physical world. If a VLM can look at an apple and output the word "Apple," a VLA looks at an apple and outputs the motor commands to pick it up.

#### **Generation 1: Discretization (The RT-2 Approach)**

Early VLAs treated robot actions like a foreign language.