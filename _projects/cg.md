---
layout: page
title: Custom C++ Ray Tracer
description: The "Lonely Snowman" is the result of our Custom Ray-Tracing Renderer
img: assets/img/projects/2022_ComputerGraphics-FinalProject/image.png
importance: 1
category: Fun
related_publications: false
---

**TL;DR:** As part of my Computer Graphics coursework, I co-developed a custom multithreaded CPU ray tracing engine in **C++** to render a complex, stylized 3D scene. Extending a baseline framework, my teammate and I engineered core computer graphics and ray-tracing algorithms for spatial acceleration, light transport, and physically based rendering. 

Our final render, titled **"The Lonely Snowman,"** tells the story of the last snow globe left on a Christmas market shelf.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/image.png" title="Final Render" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Final Rendered Image from Our Custom Ray-Tracer</div>
    </div>
</div>

<hr style="margin: 2rem 0; border: none; border-top: 1px solid rgba(0, 0, 0, 0.2);">

### ⚙️ Core Engineering & Features

To achieve a photorealistic and cinematic result, we engineered custom logic to solve specific rendering challenges:

#### 1. Transmissive Light Transport ("Magic Glass")
Rendering the glass snow globe presented a complex challenge regarding shadow rays and transmissive materials. Standard glass primitives block shadow rays, creating unrealistic dark voids. 

We modified the `recraytrace` integrator so external light passes through the globe, while preventing internal point lights from casting false, enlarged shadows outside.

<div class="row justify-content-center">
    <div class="col-sm-4 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/insideShadows.png" title="Shadows from Inside" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Shadows from Inside</div>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/outsideShadows.png" title="No Outside Shadows" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">No Outside Shadows</div>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/illumination.png" title="Illumination from Outside" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Illumination from Outside</div>
    </div>
</div>

#### 2. Procedural Volumetrics (Double-Sided Primitives)
The confetti inside the globe was created by randomly sampling points within the sphere. However, our standard `Disc` primitive was one-sided, meaning rays hitting the back face returned black. We engineered custom double-sided normal calculations so rays hitting the "back" of the confetti still evaluate color correctly.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/discs.png" title="discs" class="img-fluid rounded z-depth-1" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Custom Double-Sided Discs</div>
    </div>
</div>

#### 3. Physically Based Camera (Depth of Field)
To give the render a cinematic feel and direct the viewer's eye to the snowman, we simulated a physical lens aperture and focal plane. This added natural Depth of Field, blurring the background lighting and shelves into realistic bokeh.

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/dof.png" title="DoF" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

#### 4. Surface Normal Perturbation (Bump Mapping)
To break up the flat CGI look, we implemented bump mapping. We applied noise-based and wood-grain bump maps to the walls and shelves, calculating surface normal modifications during the shading phase.

<div class="row justify-content-center">
    <div class="col-sm-3 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/1_no_bmp.png" title="Without Bump" class="img-fluid rounded z-depth-1 eq-height-img" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/1_bmp.png" title="With Bump" class="img-fluid rounded z-depth-1 eq-height-img" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/2_no_bmp.png" title="Without Bump" class="img-fluid rounded z-depth-1 eq-height-img" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/2_bmp.png" title="With Bump" class="img-fluid rounded z-depth-1 eq-height-img" %}
    </div>
</div>
<div class="caption mt-2 text-center" style="font-size: 0.85rem;">Comparisons of flat shading (left) vs. procedural bump mapping (right).</div>


#### 5. Performance & Optimization
* **Bounding Volume Hierarchy (BVH):** Implemented spatial acceleration to optimize ray-primitive intersection tests for the high-polygon imported snowman.
* **Mesh Instancing:** Expanded the engine's loading pipeline to support instancing, drastically reducing the memory footprint of duplicated 3D assets.

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/instancing.png" title="Instancing" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Instancing Objects</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/projects/2022_ComputerGraphics-FinalProject/bvh.png" title="BVH" class="img-fluid rounded z-depth-1 eq-height-img" %}
        <div class="caption mt-2" style="font-size: 0.85rem;">BVH Data Structure</div>
    </div>
</div>

<hr style="margin: 2rem 0; border: none; border-top: 1px solid rgba(0, 0, 0, 0.2);">

This project was a fantastic deep dive into rendering equations, spatial data structures, and the intersection of software engineering and digital art. It was completed as part of the Computer Graphics course offered by the [CG-Group of Saarland University](https://graphics.cg.uni-saarland.de/courses/cg1-2021/index.html).