---
layout: page
permalink: /publications/
title: publications
description: publications in reverse chronological order.
years: [2024, 2023, 2022, 2020, 2019, 2015]
nav: true
nav_order: 4
---

You can also check my publications on <a href="https://scholar.google.com/citations?hl=en&user=UWWRHbcAAAAJ" title="scholar">Google Scholar.</a>

<!-- _pages/publications.md -->
<div class="publications">
{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
