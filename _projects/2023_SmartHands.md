---
layout: page
title: SmartHands
description: Immersive VR & Haptics for Medical Education
img: assets/img/projects/2023_SmartHands/cover.PNG
importance: 4
category: Work
related_publications: false
---

**Role:** R&D Engineer (VR Scene Design/Developer & Haptic Integration)  
**Hardware Tech:** Oculus VR, SenseGlove (Force Feedback & Vibration)  
**Funding:** Federal Ministry of Education and Research (BMBF)  

<div class="row justify-content-center">
    <div class="col-sm-9 mt-3 mt-md-0 text-center">
        {% include video.liquid path="assets/img/projects/2023_SmartHands/demo.mp4" class="img-fluid rounded z-depth-1" controls=false autoplay=true loop=true muted=true %}
        <div class="caption mt-2" style="font-size: 0.85rem;">Demonstrating the VR spinal palpation scene, where users receive real-time force feedback and vibration via SenseGlove haptic wearables.</div>
    </div>
</div>

## Project Context & The Challenge
The SmartHands project was initiated to enable the innovative use of digital media through media pedagogical training on the use of smart-device-based digital media, such as VR/AR glasses and wearables, within the health sector. The primary goal is to establish these technologies as standardized tools in future teaching.

Historically, vocational education in healthcare has faced a critical gap: there are no validated teaching scenarios for integrating digital media into existing learning and examination formats. Addressing training and further education staff, the project pilots a teaching concept to promote professional and methodological skills using targeted scenarios in manual medicine (MM) and manual therapy (MT). The overarching system forms a fully integrated learning path that alternates between phases of self-study and attendance phases using smart devices.

## ⚙️ My Contribution: Engineering the Sense of Touch
While the foundational project established a robust eLearning web solution, teaching *manual* therapy in a purely visual digital space lacks the most critical element of the profession: physical touch. To bridge this gap, I led the design and technical integration of an advanced, haptic-enabled VR module.


* **Immersive VR Scene Architecture:** Designed and developed a complete Oculus VR training environment from scratch, dropping the user into a clinical room with a virtual patient.
* **SenseGlove Haptic Integration:** Programmed the real-time integration of SenseGlove haptic exoskeletons directly into the immersion scene. When users interact with the targeted spinal points, the system processes their hand positioning and triggers precise force feedback and vibration. 
* **Mathematical Animation via B-Splines:** Implemented B-spline curves to calculate and generate mathematically smooth, continuous locomotion paths for the virtual patient. This computer graphics technique ensures highly realistic spatial movement and natural interactions with virtual objects in the room, breaking the stiffness often seen in standard VR avatars.
* **Voice-Controlled Animation Blending:** Engineered a responsive interaction system allowing the user to guide the virtual patient via voice commands (e.g., instructing the patient to *"turn your head to the left"*). The system dynamically triggers and blends smooth animations in real-time, simulating a lifelike clinical examination.
<div class="row justify-content-center">
    <div class="col-sm-5 mt-3 mt-md-0 text-center">
        {% include video.liquid path="assets/img/projects/2023_SmartHands/move-command.mp4" class="img-fluid rounded z-depth-1" controls=false autoplay=true loop=true muted=true %}
    </div>
</div>

* **Interactive Spinal Anatomy Mapping:** Engineered the core digital learning mechanic. The system dynamically highlights specific anatomical points on the virtual patient's spine, requiring the user to physically reach out, navigate the anatomy, and learn their exact placement on the human body.
* **Sensorimotor Learning Loop:** By combining voice interaction, realistic avatar movement, and simulated physical resistance upon touching the virtual spine, the scene successfully transforms a purely visual task into a highly effective, multi-sensory learning experience.
* **Physics-Based Diagnostic Interactions:** Engineered advanced collider control and intersection algorithms to allow users' virtual hands to physically grab, support, and rotate the virtual patient's head. This highly realistic hand-to-avatar physics interaction enables users to manually diagnose cervical mobility issues just as they would in a real clinic.

---
*Note: This sub-project was part of a larger €330,000 funded initiative. My specific focus was on pushing the boundaries of the attendance phases through experimental haptic R&D.*