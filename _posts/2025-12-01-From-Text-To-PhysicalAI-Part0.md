---
layout: post
title: "From Text to Physical AI - An Overview"
date: 2025-12-01 08:00:00
description: "My journey on LLMs/VLMs/VLAs to get prepared for NVIDIA Interview"
tags: AI
categories: Science Blog
giscus_comments: false
related_posts: false
related_publications: false
thumbnail: assets/img/posts/2025-From-Text-To-PhysicalAI-Part0/foundation_model.jpg
---



After applying for some roles, I got an email from NVIDIA, stating that we are going to have an interview on a role, desining systems on various foundation models, including Vision Language Actions. By that time, the term was new to me, but it was interesting enough to make me curious. So, having knowledge on LLMs and VLMs, I started the path to learn about VLAs. This post is about an effective study journey, starting from text embedding and LLMs into the action and VLAs.

In this post, I have tried to provide an overview on the journey. It's broad, but still I tried to specify the underlying steps for each part. (In case i'd fine time, I will try to write about each part in more details too.)

As a quick note before we begin: the leap from chatbots that just generate text to physical robots that can understand their environment and make you a cup of coffee feels like pure magic. But beneath all these fancy new acronyms, it is really just a highly elegant evolution of **deep learning architectures** (which I’ll assume you have a basic grasp of for this post).

So, let's tear down this modern AI stack: We’ll start with the "Brain" (Large Language Models), add the "Eyes" (Vision-Language Models), and finally connect the "Muscles" (Vision-Language-Action Models). Whether you are an AI engineer or just technically curious, here is the blueprint of how modern Physical AI actually works.

Hope you'd find it useful :)


---

## Part 1: The Brain — Large Language Models (LLMs)

Before an AI can act, it must understand. The core of almost all modern AI is the LLM.

#### **The Decoder-Only Reality**
A common misconception is that models like GPT-4 or Llama 3 use Autoencoders or VAEs. They do not. Modern LLMs are **Decoder-only Transformers**.

Instead of having a separate "Encoder" to create a latent space, the **Embedding Layer** acts as the direct entry point. Text is converted into discrete tokens (via Byte-Pair Encoding, or BPE), mapped to dense vectors (e.g., 4096 dimensions), and processed autoregressively using **Masked Self-Attention**.

#### **The Training Pipeline**

Taking an LLM from a babbling text generator to a helpful assistant requires four distinct stages:

1. **Pre-training:** Minimizing the Negative Log-Likelihood (NLL), which is mathematically equivalent to minimizing the Kullback-Leibler (KL) Divergence. The model learns world knowledge by predicting the next token across trillions of words.
2. **Continuous Pre-Training (CPT):** Injecting heavy, domain-specific knowledge (like medical journals or code) before formatting the model.
3. **Supervised Fine-Tuning (SFT):** Training on high-quality `(prompt, response)` pairs to teach the model how to hold a conversation.
4. **Alignment (DPO over RLHF):** We want models to align with human preferences. Historically, Reinforcement Learning from Human Feedback (RLHF) via PPO was used, which required loading **4 massive models** into VRAM (Policy, Reference, Reward, Critic). Today, the industry prefers **Direct Preference Optimization (DPO)**. DPO analytically solves the RLHF objective, eliminating the need for Reward and Critic models, practically halving memory requirements.

#### **The Magic of RoPE (Rotary Positional Embeddings)**

Transformers process tokens in parallel, meaning they don't inherently know word order. Older models simply added an absolute position vector to the word embedding.

Modern models use **RoPE**. Instead of adding numbers, RoPE treats the Query ($Q$) and Key ($K$) vectors as complex numbers and rotates them by an angle proportional to their position. When the attention dot product is calculated, the absolute positions cancel out, leaving only the **relative distance**:

$$Attention \propto \text{Real}(q \cdot k \cdot e^{i(m-n)\theta})$$

This allows modern LLMs to extrapolate to massive context windows (128k+ tokens).


<hr style="margin: 1rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.3);">


## Part 2: The Eyes — Vision-Language Models (VLMs)

How do we teach a text-based brain to see? We don't use complex Cross-Attention layers anymore. We use a simpler, highly scalable trick: **Token Concatenation**.

#### **The VLM Pipeline (e.g., LLaVA)**

1. **The Vision Encoder (ViT):** An image is sliced into patches (e.g., $14 \times 14$ pixels). A frozen Vision Transformer (like CLIP or SigLIP) processes these patches into semantic feature vectors (e.g., 1024 dimensions). It doesn't output raw pixels; it outputs "meaning."
2. **The Projector (The Bridge):** The LLM expects 4096-dimensional vectors, but the ViT outputs 1024-dimensional vectors. A small 2-layer MLP (the Projector) translates the visual features into the LLM's native embedding space.
3. **Fusion:** We simply concatenate the lists. The input to the LLM becomes:
    `[Visual_Token_1, ..., Visual_Token_576, Text_Token_1, ...]`
4. **Attention:** The combined sequence flows into the Transformer blocks, where RoPE is applied dynamically. To the LLM, the image is just a "foreign language" paragraph at the start of the prompt.


<hr style="margin: 1rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.3);">


## Part 3: The Muscles — Vision-Language-Action (VLAs)

This is where AI touches the physical world. If a VLM can look at an apple and output the word "Apple," a VLA looks at an apple and outputs the motor commands to pick it up.

#### **Generation 1: Discretization (The RT-2 Approach)**

Early VLAs treated robot actions like a foreign language.

- **The Mechanism:** They binned the robot's continuous physical limits (e.g., an arm moving from 0m to 1m) into 256 discrete bins.
- **Vocabulary Surgery:** They added 256 new "action tokens" (e.g., `ACT_128`) to the LLM's **LM Head** (the final linear layer that maps thought vectors back to token probabilities).
- **Result:** The model autoregressively predicts actions the same way it predicts text. However, 256 bins result in jittery, imprecise robotic movement.

#### **Generation 2: Continuous Flow (The GR00T & Pi0 Approach)**

To achieve smooth, human-like motion, modern architectures (like NVIDIA's Isaac GR00T) abandon discrete tokens.
- **System 2 (The Brain):** A physics-aware model (like Cosmos-Reason) processes the video and prompt, generating a Chain-of-Thought (CoT) reasoning trace to ensure physical safety and logic.
- **System 1 (The Body):** Instead of an LM Head predicting discrete tokens, the architecture uses a **Diffusion Transformer (DiT)** head. It takes the "thought vectors" and uses flow matching to denoise random signals into highly precise, continuous floating-point motor commands.


<hr style="margin: 1rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.3);">


## Part 4: Under the Hood — Engineering for Production


Running these massive models requires architectural cleverness. Two crucial techniques include:

- **KV Caching (Inference):** During generation, we do not recalculate the Key ($K$) and Value ($V$) matrices for past tokens. We store them in VRAM to drastically reduce latency.
- **LoRA (Training):** Instead of updating all 16.7 million parameters of a massive dense layer ($W$), Low-Rank Adaptation (LoRA) freezes $W$ and injects two tiny matrices ($A$ and $B$) in parallel. $Output = Wx + BAx$. This reduces the trainable parameters to less than 1%, slashing VRAM requirements during fine-tuning    

#### A Note on Temperature

When deploying VLAs, **Sampling Temperature** is critical. While a high temperature ($T > 1$) makes a chatbot creative, it makes a robot dangerous. Physical AI almost exclusively relies on Greedy Decoding ($T = 0$) because precision is required; deviating to the "second most likely" action often results in physical failure.


<hr style="margin: 1rem 0; border: none; border-top: 2px solid rgba(0, 0, 0, 0.4);">


## Conclusion

The journey from standard LLMs to Physical AI is not about inventing completely alien neural networks. It is a story of clever formatting: using Projectors to turn images into "words," expanding the LM Head to treat actions as "words," and eventually fusing Transformers with Diffusion to achieve continuous grace. We are no longer just teaching AI to chat; we are teaching it to interact with the physical universe.


<hr style="margin: 1rem 0; border: none; border-top: 2px solid rgba(0, 0, 0, 0.5);">

thumbnail image is from Apple's Foundation Model logo