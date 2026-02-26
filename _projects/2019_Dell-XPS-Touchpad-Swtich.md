---
layout: page
title: "The Missing Key: Touchpad Toggle Utility"
description: a C++ driver-level toggle to prevent accidental clicks while typing on XPS 13
img: assets/img/projects/2019_Dell-XPS-Touchpad-Swtich/cover2.png
importance: 2
category: Fun
related_publications: false
---

<!-- I was once sitting in library and developing some projects with my laptop and I fogot my mouse, so I was using touchpad!
During typing, I accirdentally touched the touchpad, mouse moved and clicked somewhere else, then my letters were suddently typied somewhere else! Extremely Annoying!
I couldn't de-activate the touchpad, because there was a foundamental lack in Dell XPS 13 design: there was no dedicated button on keyword to enable/disable touchpad. So, once I used touchpad to navigate to mouse settings and disable, I could no longer enable it. Odd yet Funny :D

I once decided to write a C++ application that could access to the touchpad driver, check the current status of the touchpad, and allows switching it through an application. and then, I defined a keyboard shortcut for running that application.

As F7 on the XPS keyboard was also unassigned, I assigned the shortcut trigger to F7.

I can toggle touchpad status easily through the keyboard, and compensate the lack of Touchpad key :)

It was fun, by the way. and a real problem of my daily tasks solved :D

If you have the same laptop and suffering from the same issue, feel free to download the repo and use the app. -->



<!-- ### The Missing Key: Dell XPS 13 Touchpad Toggle -->

While coding at the library without an external mouse, my palms kept brushing the trackpad. The cursor would jump, and suddenly I was typing code in a random paragraph. Extremely annoying!

I wanted to disable the touchpad in the system settings but there was a fundamental design flaw in the Dell XPS 13 (L322X): **it has no physical toggle key.**
This meant if I disabled the touchpad via software without an external mouse, I was trapped. I had no way to easily navigate back to turn it on! So, I would be only on keyboard then! Odd, yet hilariously frustrating.

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/2019_Dell-XPS-Touchpad-Swtich/keyboard.jpg" title="Keyboard Layout" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**The Solution**
To fix this, I engineered the missing feature myself. I wrote a lightweight **C++ application** that:
* Interfaces directly with the system's touchpad driver.
* Checks if the touchpad is currently enabled or disabled.
* Toggles the state programmatically.

Since the `F7` key on its keyboard was unassigned, I mapped a global shortcut (`Ctrl + Shift + F7`) to trigger the executable. Hooray! We now have a physical toggle key.

A highly irritating daily problem solved through a quick micro-project, and compensate the lack of Touchpad key :)
By the way, it was fun and a real problem of my daily tasks solved :D

### 🛠️ Suffer from the same issue?
If you're also rocking an older XPS 13 and battling accidental clicks, I've published this utility. Feel free to download the repository, follow the instructions, and type in peace!

[![GitHub Repository](https://img.shields.io/badge/GitHub-View_Source_Code-blue?logo=github)](https://github.com/AlirezaParchami/Dell-XPS13-Touchpad-Switch)