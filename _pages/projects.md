---
layout: page
permalink: /projects/
title: selected projects
nav: true
nav_order: 5
description: some of the honorable projects I have worked on.
---

 <style>
  .image-margin {
  margin: 10px;
}

.card{
  display: table;
}
  </style>

  
  

<div class="container">
  {% assign project_types = site.data.projects | group_by: "project-type" %}
  {% for project_type in project_types %}
  <h3 >{{ project_type.name }}</h3>
  <div class="row">
    {% for project in project_type.items %}
    <div class="col-md-12 mb-4">
      <div class="card">
        {% if project.image %}
        <img src="{{ site.url }}/{{ site.baseurl }}/{{ project.image }}" class="card-img-top float-right mr-3 mb-3 image-margin" alt="{{ project.title }}" style="width:80px;">
        {% endif %}
        <div class="card-body">
          <h4 class="card-title">{{ project.title }}</h4>
          <h5 class="card-subtitle mb-2">{{ project.role }}</h5>
             <h6 class="card-subtitle mb-2">{{ project.year }}</h6>
             <!-- <div class="year mb-2">Year: {{ project.year }}</div>          -->
 
          <p class="card-text">{{ project.description }}</p>
        </div>
        <div class="card-footer"> 
           <div class="mt-2">
            {% assign tags = project.tags | split: ", " %}
            {% for tag in tags %}
            <code>{{ tag }}</code>
            {% endfor %}
          </div>
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
  {% endfor %}
</div>
 