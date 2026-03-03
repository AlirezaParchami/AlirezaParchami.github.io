---
layout: post
title: Contrastive Learning
date: 2021-11-10 08:00:00
description: Teaching AI to Understand the World Through Comparisons
tags: AI
categories: Science Blog
giscus_comments: false
related_posts: false
related_publications: false
thumbnail: assets/img/posts/2021-11-10-Contrastive-Learning/data_setup.png
---

Traditionally, teaching a neural network to recognize a "dog" meant feeding it a million manually labeled images. But humans don't learn that way. A toddler figures out what a dog is by seeing one, then seeing a cat, and intuitively realizing: *"These two are different, but that other dog I saw earlier is similar to the first one."*

**Contrastive Learning** is the mathematical formulation of this exact intuition. Heavily used in self-supervised learning, it teaches models to understand the world not by memorizing static labels, but by measuring similarities and differences.

Here is a look at how this works under the hood, from the data setup down to the vector math.

### The Setup: Anchors, Positives, and Negatives

To teach a model by comparison, we need to build a learning environment that doesn't rely on human-annotated labels. We do this by generating three types of data points from our unlabeled dataset:

1. **The Anchor ($x$):** Our reference image.
2. **The Positive Sample ($x^+$):** An image that *should* mean the same thing as the anchor. In computer vision, we usually create this by heavily augmenting the anchor (e.g., random cropping, color jittering, or blurring). 
3. **The Negative Samples ($x_i^-$):** Completely different images chosen from the dataset, usually just other random images sitting in the same training batch.


<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/posts/2021-11-10-Contrastive-Learning/data_setup.png" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">The data setup in a contrastive learning framework. The anchor and positive are augmented views of the same golden retriever. The negatives are different images. Notice the rightmost negative—it's another dog! This is known as a "hard negative" and forces the model to learn fine-grained, semantic differences.</div>
    </div>
</div>


*The data setup in a contrastive learning framework (like SimCLR). Notice the rightmost negative—it's another dog. This is a "hard negative" that forces the model to learn fine-grained differences.*

By setting up the data this way, the task becomes clear: The neural network must learn to recognize that $x$ and $x^+$ contain the same core semantic information, despite the pixel-level distortions caused by the data augmentation.

### The Geometry of the Latent Space (Pushing and Pulling)

When we pass these images through a neural network (like a ResNet or Vision Transformer), the model outputs a high-dimensional vector for each image, known as an **embedding**. 

The entire goal of Contrastive Learning is to sculpt this high-dimensional embedding space. We want representations of similar things to cluster tightly together, and different things to repel each other.


<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/posts/2021-11-10-Contrastive-Learning/latent_space.png" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">A 2D visualization of the latent embedding space. Left: Before optimization, the Query is scattered randomly. Right: After applying contrastive loss, the Query vector is pulled tightly toward the Positive Sample and pushed away from the Negatives.</div>
    </div>
</div>

*Left: Before optimization, the Query (anchor) is scattered randomly. Right: After applying contrastive loss, the Query vector is pulled tightly toward the Positive Sample and pushed away from the Negatives.*

Mathematically, we measure the distance between these vectors using **Cosine Similarity**. If $q$ is the vector for our query/anchor and $k$ is the vector for another image, the similarity is simply the dot product of their normalized vectors:

$$sim(q, k) = \frac{q \cdot k}{||q|| ||k||}$$

Our optimization goal is straightforward: Maximize $sim(q, k^+)$ while minimizing $sim(q, k_i^-)$.

### The Math: InfoNCE Loss

How do we actually update the network's weights to achieve this pushing and pulling? We use a loss function. The most standard one in this field is the **InfoNCE** (Information Noise-Contrastive Estimation) loss, also known as NT-Xent. 

It is essentially a Softmax function applied to vector similarities:

$$\mathcal{L}_{q} = -\log \frac{\exp(\text{sim}(q, k^+) / \tau)}{\exp(\text{sim}(q, k^+) / \tau) + \sum_{i=1}^{K} \exp(\text{sim}(q, k_i^-) / \tau)}$$

Here is why this formula works so well in practice:
* **The Numerator (The Pull):** $\exp(\text{sim}(q, k^+))$ represents the similarity between our anchor and the positive sample. The network updates its weights to make this value as high as possible.
* **The Denominator (The Push):** This sums up the similarity of the anchor to the positive sample *and* all $K$ negative samples. To make the overall fraction close to 1 (which drives the overall loss toward 0), the similarities to the negatives $\text{sim}(q, k_i^-)$ must be driven down to zero.
* **The Temperature Parameter ($\tau$):** Tuning $\tau$ is critical. A smaller temperature makes the model hyper-sensitive to "hard negatives" (like the other dog in the first image). It forces the network to look closer and learn finer details to separate items that look broadly similar but aren't.

### Why This Changed the Game

Contrastive Learning was a massive paradigm shift for AI engineering. 

Instead of being bottlenecked by expensive human labeling, we can now take millions of unlabeled images, apply programmatic augmentations, and force a model to map out a highly structured, semantically meaningful latent space entirely on its own. 

This self-supervised pre-training creates incredibly robust foundation models. When you later fine-tune these models on a tiny labeled dataset for a specific task, they drastically outperform models trained from scratch. In fact, this exact "contrastive" math is the beating heart of multi-modal titans like OpenAI's **CLIP**, which aligns text and image vectors using the exact same principles.