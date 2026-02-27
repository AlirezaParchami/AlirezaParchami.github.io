---
layout: page
title: Live-Action to Stylized 2D Animation
description: Using GenAI and Custom Shaders for Rendering 2D Animation out of Videos.
img: assets/img/projects/2025_Animation_GenAI/cover.png
importance: 1
category: Work
related_publications: false
---



{% comment %}
I joined [Disney Research](https://studios.disneyresearch.com/) to work on a highly interesting project, at the start of Video Neural Generation era, when researches tend to work on smooth and temporally-consistent video generation using neural rendering.

The concept of my project at Disney went even beyond this matter: We didn't only intend to generate ANY video, we intended to generate consistent videos according to a reference video but to apply geometry modification on characters and customize the shading effects so that the video looks as a 2D animation.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/style.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<hr style="margin: 1.3rem 0; border: none; border-top: 2px solid rgba(0, 0, 0, 0.4);">


### My Key Contributions
{% endcomment %}


At [Disney Research Studios](https://studios.disneyresearch.com/), I spearheaded R&D on automated animation pipelines to transform live-action film into highly stylized 2D cartoons. By engineering a dual-track approach of custom Toon shaders (Blender/Unity) and cutting-edge Generative AI (Stable Diffusion, AnimateDiff), I tackled the frontiers of temporally-consistent video synthesis, character geometry modification, and production-quality style transfer.

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/style.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">2D Animated Scene with Cartoony Characters</div>
    </div>
</div>


### 🎬 The Vision & The Challenge
At the start of the Video Neural Generation era, most research focused on generating *any* temporally smooth video. Our goal at Disney went much further: we needed to take live-action reference footage, completely alter the character geometry to match a highly stylized 2D aesthetic, and maintain strict temporal consistency and production quality. 

To solve this, I researched, prototyped, and evaluated two parallel technical pipelines:

<hr style="margin: 1.5rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.4);">

### Track 1: 3D Engineering & Procedural Shading
Shaders are essential keys! They power the whole shading effects on a frame, meaning that can create various light and visual effects. In various cases, by only using a correct shader, you can completely change the dynamics, atmosphere, and style of an image, video, or video game.

As an easy catch, you can see how instantly "Outline Shader" feels like a 2D sketch due to its outlines, compared to mix or painterly shaders:

<div class="row justify-content-center">
    <div class="col-sm-2 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/cel_shader.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Cel Shader</div>
    </div>
    <div class="col-sm-2 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/Outlines_shader.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Outlines Shader</div>
    </div>
    <div class="col-sm-2 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/Painterly_shader.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Painterly Shader</div>
    </div>
    <div class="col-sm-2 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/Screen-tone_shader.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Screen-tone Shader</div>
    </div>
    <div class="col-sm-2 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/mix_shader.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Mix (Custom) Shader</div>
    </div>
</div>

**My Contribution:**
* **Custom Toon & Cel Shaders:** Designed and tested custom shaders to drastically reduce lighting complexity, bridging the gap between physically based 3D rendering and stylized 2D cartoon aesthetics. 
* **Advanced Rigging:** Investigated and implemented advanced rigging concepts, such as **Bendy Bones**, to enable the flexible, exaggerated "squash and stretch" movements typical of classic 2D animation.

While shaders are powerful in changing lighting effects and make an image look 2D by reducing level of shades, they cannot perform any modification in geometry of objects. That remain a key issue for using shaders to map a real person into a cantoony character!


<hr style="margin: 1.5rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.4);">


### Track 2: Generative AI & Video-to-Video Synthesis
To achieve the final highly stylized look, I developed and trained advanced Generative AI workflows, testing the absolute limits of AI for production-quality character generation, at the early stage of video model in 2024.

* **Advanced ComfyUI Workflows:** Architected complex Video-to-Video generation pipelines utilizing **Stable Diffusion**, **AnimateDiff**, and **LoRA** (Low-Rank Adaptation). Implemented advanced masking and denoising strategies to enforce temporal consistency, stlye matching, and geometry modification.
* **State-of-the-Art Model Evaluation:** Evaluated and benchmarked cutting-edge models (e.g., *AnyV2V, UniAnimate, Animate Anyone*) for robust character swapping and motion transfer from live-action to stylized characters.
* **Targeted Style Transfer & Training:** Created curated datasets and preprocessing scripts for rigorous patch tuning. I specifically focused on notoriously difficult generation areas (like hand regions) and trained models to flawlessly translate rendered 3D content into the target 2D artistic style.

Image samples below can show how the geometry, lighting, and shading style have changed in each generated style:

<div class="row justify-content-center">
    <div class="col-sm-5 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/orig.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Original Frame</div>
    </div>
    <div class="col-sm-5 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/genai1.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Generated Style 1</div>
    </div>
</div>

<div class="row justify-content-center">
    <div class="col-sm-5 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/genai2.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Generated Style 2</div>
    </div>
    <div class="col-sm-5 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2025_Animation_GenAI/genai3.png" title="" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Generated Style 3</div>
    </div>
</div>

<hr style="margin: 1.5rem 0; border: none; border-top: 1.5px solid rgba(0, 0, 0, 0.4);">


### 📊 Strategic Outcomes
Ultimately, I delivered a comprehensive comparative analysis of 2D vs. 3D animation pipelines regarding feasibility, scalability, and quality. I documented the exact limitations of AI-based solutions for character generation and provided core architectural recommendations for the future of Disney's automated animation pipelines.


<!-- Note: Due to the NDA and Walt Disney policy, I cannot share visual outcomes and our references publically. In case of request, more technical talk can be carried out in a video call, without compromising company data. Please feel free to reach out. -->

**🔒 A Note on Visuals and Data:** Because this was an internal project at Disney Research, I cannot post final stylized videos or reference footage publicly due to the NDA and The Walt Disney Company policies. That said, I'd love to talk through the context, architecture, and technical problem-solving on a call, without compromising company IP. In case you're interested, let's connect!