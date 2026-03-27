---
layout: about
title: About
permalink: /
subtitle: Research Engineer | Visual Computing and AI # <a href='#'>Affiliations</a>. Address. Contacts. Motto. Etc.

profile:
  align: right
  image: alireza3.jpg
  image_circular: false # crops the image to make it circular
  style: "border-radius: 20px;"

#  more_info: >


selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: false # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: false # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

<style>
  /* 1. Set the original RGB image as the hidden background */
  .profile {
    background-image: url('{{ "/assets/img/alireza3-orig.jpg" | relative_url }}');
    background-size: cover;
    background-position: center;
    border-radius: 20px; /* This matches your YAML style */
    overflow: hidden; /* Ensures the background stays inside the rounded corners */
  }

  /* 2. Add a smooth transition to the generated image */
  .profile img {
    transition: opacity 0.4s ease-in-out;
  }

  /* 3. On hover, fade out the generated image to reveal the original! */
  .profile:hover img {
    opacity: 0;
  }
</style>

<!-- Write your biography here. Tell the world about yourself. Link to your favorite [subreddit](https://www.reddit.com). You can put a picture in, too. The code is already in, just name your picture `prof_pic.jpg` and put it in the `img/` folder.

Put your address / P.O. box / other info right below your picture. You can also disable any of these elements by editing `profile` property of the YAML header of your `_pages/about.md`. Edit `_bibliography/papers.bib` and Jekyll will render your [publications page](/al-folio/publications/) automatically.

Link to your social media connections, too. This theme is set up to use [Font Awesome icons](https://fontawesome.com/) and [Academicons](https://jpswalsh.github.io/academicons/), like the ones below. Add your Facebook, Twitter, LinkedIn, Google Scholar, or just disable all of them. -->

{% comment %}
Hi, I'm Alireza &#x1F44B;&#xFE0F;

I'm a research engineer with 4+ years of experience in research and development, having worked with incredible teams at Disney Research, EPFL, Mercedes-Benz Tech Innovation (MBTI), and the Max Planck Institute for Informatics. I'm currently finalizing my Master's thesis under the supervision of [Prof. Jürgen Steimle](https://hci.cs.uni-saarland.de/people/juergen-steimle/), in collaboration with [Mercedes-Benz](https://www.mercedes-benz-techinnovation.com/en).

I love to create and innovate, which is why I am passionate about research and turning it into effective applications. For the same reason, I am highly drawn to image synthesis and rendering as it allows to create images that represent the world VISUALLY. You may now have an idea why I chose to study [M.Sc. Visual Computing](https://saarland-informatics-campus.de/en/msc-visual-computing/) at one of Europe's top universities in this field, [Saarland Informatics Campus](https://saarland-informatics-campus.de/en/).

I'm open to Research Engineer and R&D roles, as well as PhD opportunities, where I can contribute to projects in Computer Graphics, 3D Vision, Extended Reality, and AI. Beyond career opportunities, I always welcome the chance to connect with fellow researchers and students. If you have anything to chat, feel free to reach out :)
{% endcomment %}


Hello &#x1F44B;&#xFE0F;

I'm Alireza, a research engineer with 4+ years of R&D experience, having worked with incredible teams at Disney Research, EPFL, Mercedes-Benz Tech Innovation (MBTI), and the Max Planck Institute for Informatics. I'm currently finalizing my Master's thesis under the supervision of [Prof. Jürgen Steimle](https://hci.cs.uni-saarland.de/people/juergen-steimle/), in collaboration with [MBTI](https://www.mercedes-benz-techinnovation.com/en).

Driven by a passion for image synthesis and acquisition, I chose to pursue [M.Sc. Visual Computing](https://saarland-informatics-campus.de/en/msc-visual-computing/) at one of Europe's top institutions in the field, [Saarland Informatics Campus](https://saarland-informatics-campus.de/en/). My research lies at the intersection of computer graphics, rendering, and 3D computer vision, utilizing both AI-based and mathematical approaches.

I'm open to Research Engineer roles and PhD opportunities in CG, 3D Vision, HCI, and AI. Beyond career opportunities, I always welcome the chance to connect with fellow researchers and students. If you have anything to chat, feel free to reach out :)


<style>
  .affiliation-logo {
    max-height: 45px; /* Shrunk slightly so it doesn't overpower your text */
    width: auto; 
    object-fit: contain;
    mix-blend-mode: multiply; 
    /* filter: grayscale(100%) opacity(70%);  */
    /* transition: all 0.3s ease; */
    margin: 10px 1.5rem; /* This is the magic! It forces exactly 1.5rem of space between every logo */
  }
  
  .affiliation-logo:hover {
    filter: grayscale(0%) opacity(100%);
  }
</style>

<div class="d-flex flex-wrap justify-content-center align-items-center mt-4 mb-5">
    {% include figure.liquid loading="eager" path="assets/img/logos/disney.png" class="affiliation-logo" %}
    {% include figure.liquid loading="eager" path="assets/img/logos/uds.png" class="affiliation-logo" %}
    {% include figure.liquid loading="eager" path="assets/img/logos/epfl.png" class="affiliation-logo" %}
    {% include figure.liquid loading="eager" path="assets/img/logos/mbti.png" class="affiliation-logo" %}
    {% include figure.liquid loading="eager" path="assets/img/logos/mpi-inf.png" class="affiliation-logo" %}
</div>

