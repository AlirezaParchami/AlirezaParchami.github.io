---
layout: page
title: FreeStyleGAN Dev
description: Engineering on GAN-Based Image Synthesis
img: assets/img/projects/FreeStyleGAN/cover.PNG
importance: 1
category: Work
related_publications: false
---




I joined the [Image Synthesis and Machine Learning research group (ISMaeL)](https://ismael.mpi-inf.mpg.de/) at Computer Graphics and Visual Computing Department (D4/D6) of Max Planck Institute for Informatics (MPI-Inf) to conduct research and engineering in GAN-based image synthesis.

---
<br/>


### About FreeStyleGAN

<div class="row justify-content-center">
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include video.liquid path="assets/img/projects/FreeStyleGAN/method.mp4" class="img-fluid rounded z-depth-1" controls=false autoplay=true loop=true muted=true %}
    </div>
</div>


**FreeStyleGAN** bridges generative AI and traditional 3D rendering to achieve **truly free-viewpoint rendering of realistic faces**. By mapping captured faces to a novel "GAN camera manifold," it overcomes the limited viewpoints of standard GANs.

**Key Capabilities:**
- **Precise 3D Camera Control:** Explicitly control pre-trained StyleGAN models with a 3D camera at interactive rates.
- **Seamless 3D Integration:** Readily insert synthesized faces into synthetic environments (e.g., stereoscopic rendering, path tracing).
- **Semantic Editing:** Retain StyleGAN’s high-quality editing to easily modify attributes like facial expressions or age.

<div class="row justify-content-center">
    <div class="col-sm-2 mt-3 mt-md-0">
        {% include video.liquid path="assets/img/projects/FreeStyleGAN/Free-view Camera Control.mp4" class="img-fluid rounded z-depth-1" controls=false autoplay=true loop=true muted=true %}
    </div>
    <div class="col-sm-2 mt-3 mt-md-0">
        {% include video.liquid path="assets/img/projects/FreeStyleGAN/View-consistent Editing.mp4" class="img-fluid rounded z-depth-1" controls=false autoplay=true loop=true muted=true %}
    </div>
</div>
---

* For more information on the project and methodology, visit the [Project Page](https://repo-sam.inria.fr/fungraph/freestylegan/).
* For applied contributions and implementation details, visit the [FreeStyleGAN Source Code](https://gitlab.inria.fr/fungraph/freestylegan).

---
<br/>

### Key Contributions

My work focused on optimizing the FreeStyleGAN pipeline for scale, accessibility, and speed. I effectively contributed to the project's core source code by:

1. **Developing a custom parser** to make the pipeline compatible with **COLMAP** for open-source 3D reconstruction.
2. **Engineering headless OpenGL support** via the **GLFW/EGL** framework to enable off-screen, **GPU-accelerated rendering** on Linux servers.
3. **Implementing batch rendering protocols** to maximize GPU utilization and accelerate synthesis throughput.

---
<br/>

### Contribution Details

##### 1. Open-Source Scene Reconstruction via COLMAP
In its initial stages, the pipeline relied heavily on proprietary Reality Capture software for Structure-from-Motion (SfM) and Multi-View Stereo (MVS) reconstruction. This hard dependency limited the project's accessibility and deployment flexibility. To democratize the toolset, I developed a custom Python parser designed specifically to process COLMAP outputs. While COLMAP's open-source algorithms yield slightly different reconstruction fidelity compared to commercial alternatives, this engineering effort successfully decoupled the project from paid licensing and provided researchers with a robust, highly reliable alternative for baseline 3D mesh generation.

##### 2. Headless OpenGL Support for Linux Servers
Originally, the project's rendering pipeline was strictly bound to Windows environments due to its underlying graphical dependencies and window-based rendering requirements. This created a bottleneck for scalable cloud computing. To resolve this, I engineered a headless rendering backend using OpenGL, GLFW, and EGL. This critical update allowed the system to perform off-screen, GPU-accelerated rendering directly on headless Linux servers, successfully bridging the gap between local workstation testing and large-scale computing clusters.

##### 3. High-Throughput Batch Rendering
The legacy pipeline was limited to sequential, single-image rendering. Generating free-viewpoint sequences across multiple camera angles was highly time-consuming, leaving server GPUs severely underutilized during execution. I designed and integrated a batch rendering protocol that processes multiple novel views concurrently. This optimization dynamically maximized GPU saturation, resulting in significantly accelerated data synthesis throughput for large-scale volumetric and multi-angle rendering tasks.

--- 

##### Project Video

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <!-- <iframe width="100%" height="400" src="https://youtu.be/MRWNBRa6EJ0?si=_wRjTBw8eRfNYMXe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="rounded z-depth-1"></iframe> -->
        <iframe width="100%" src="https://www.youtube.com/embed/MRWNBRa6EJ0?si=3kNe2viV4QMTZqkW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
</div>