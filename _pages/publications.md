---
layout: page
permalink: /publications/
title: Publications
description: publications by categories in reversed chronological order.
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<div class="publications">

{% bibliography %}

</div>


<!-- 
<div class="publications">

  ### Authored Publications
  {% bibliography --query @*[role!=contributor] %}

  <br>
  <hr style="margin: 2rem 0; border: none; border-top: 2.5px solid rgba(0, 0, 0, 0.5);">
  <br>

  ### Technical Contributions
  {% bibliography --query @*[role=contributor] %}

</div> -->