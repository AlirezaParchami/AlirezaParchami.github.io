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


{% bibliography --query @*[role!=contributor] %}

<br>
<hr style="margin: 2rem 0; border: none; border-top: 3px solid rgba(0, 0, 0, 0.6);">
<br>

<h4 class="text-center" style="font-weight: 700;">Publications Based on My Research Software and Design</h4>

{% bibliography --query @*[role=contributor] %}

</div>

