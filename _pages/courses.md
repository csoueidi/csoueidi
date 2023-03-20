---
layout: page
permalink: /teaching/
title: teaching
description: my teaching engagements. 
nav: true
nav_order: 5
---
 <style>
  .card{
    font-family: 'JetBrains Mono', monospace;
  }
  </style>

<div class="container">
  
 
  {% assign sorted_data = site.data.courses | sort: 'year' | reverse %}
  {% assign grouped_data = sorted_data | group_by: 'type' %}
  
  {% for group in grouped_data %}
    <h3>{{ group.name | capitalize}}</h3>
    <div class="row">
      {% for item in group.items %}
        {% if item.type == 'Lectures' or item.type == 'Misc'  or item.type == 'Training' %}
          <div class="col-md-12 mb-4">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">{{ item.title }}</h5>
                <p class="card-subtitle mb-2 text-muted"><strong>Date:</strong>   {{ item.date }}</p>
                {% if item.event %}
                <p class="card-subtitle mb-2 text-muted"><strong>Event:</strong>  {{ item.lecture }}</p>
                {% endif %}
                {% if item.role == 'TA and co-lecturer' %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> TA and Co-Lecturer</code></p>
                {% else %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> {{ item.role }}</code></p>
                {% endif %}
                <p class="card-subtitle mb-2 text-muted"><strong>With:</strong>  {{ item.with }}  </p>
                {% if item.attendees %}
                <p class="card-subtitle mb-2 text-muted"><strong>Attendees:</strong> {{ item.attendees }}</p>
                {% endif %}               
                <p class="card-text">{{ item.details }}</p>
                 {% if item.url %}
                   <a class="news-title" href="{{ item.url | relative_url }}">Link</a>
                {% endif %}
              </div>
            </div>
          </div>
        {% elsif item.type == 'Courses'%}
          <div class="col-md-12 mb-4">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">{{ item.course }} -- {{ item.title }}</h5>
                <p class="card-subtitle mb-2 text-muted"><strong>University :</strong> {{ item.with }}</p>
                <p class="card-subtitle mb-2 text-muted"><strong>Date :</strong>  {{ item.semester }}</p>           
                {% if item.role == 'TA and co-lecturer' %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> TA and Co-Lecturer</code></p>
                {% else %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> {{ item.role }}</code></p>
                {% endif %}
                {% if item.details %}
                <p class="card-text">{{ item.details }}</p>
                {% endif %}
              </div>
            </div>
          </div>   
        {% elsif item.type == 'Workshops' %}
        <div class="col-md-12 mb-4">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">{{ item.title }}</h5>
              <p class="card-subtitle mb-2 text-muted"><strong>Date:</strong>   {{ item.date }}</p>
              <p class="card-subtitle mb-2 text-muted">{{ item.lecture }}</p>
              <p class="card-subtitle mb-2 text-muted"><strong>With:</strong> {{ item.with }}</p>
                {% if item.role == 'TA and co-lecturer' %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> TA and Co-Lecturer</code></p>
                {% else %}
                <p class="card-subtitle mb-2 text-muted"><strong>Role :</strong><code> {{ item.role }}</code></p>
                {% endif %}
              {% if item.attendees %}
              <p class="card-subtitle mb-2 text-muted"><strong>Attendees:</strong> {{ item.attendees }}</p>
              {% endif %}
              <p class="card-text">{{ item.details }}</p>
            </div>
          </div>
        </div>
      {% endif %}
      {% endfor %}
    </div>
  {% endfor %}
  
</div>
