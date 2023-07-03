---
layout: page
permalink: /publications/
title: publications
description: publications by categories in reverse chronological order. 
years: [ 2023, 2022, 2021, 2020,2019,2015]
nav: true
nav_order: 4
---

An up-to-date list is available on <a href="https://scholar.google.com/citations?hl=en&user=UWWRHbcAAAAJ" title="scholar">Google Scholar.</a>


<!-- _pages/publications.md -->
<div class="publications">
{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
 