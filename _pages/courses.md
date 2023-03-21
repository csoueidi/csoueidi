---
layout: page
permalink: /teaching/
title: teaching
description: my teaching engagements. 
nav: true
nav_order: 3
---

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js"></script>


 <style>
  /* .card-title{
    font-family: 'JetBrains Mono', monospace;
  } */
  .courses h5{
    font-weight: bolder;
    font-size: 1.1rem;
  }
    .courses .card-body{   
   padding-bottom: 1rem;
    padding-top: 1rem;
     border-bottom: 1px solid var(--global-divider-color) ;  
 
  
  }

  .courses .card-text{
  
  }
  </style>

  {% assign sorted_data = site.data.courses | sort: 'year' | reverse %}
  {% assign grouped_data = sorted_data | group_by: 'type' %}
  


 
  

<div class="container">
  <ul class="nav nav-tabs nav-fill" id="myTab" role="tablist">
      <li class="nav-item">
      <a class="nav-link active card-title" id="courses-tab" data-bs-toggle="tab" href="#courses" role="tab" aria-controls="courses" aria-selected="true">Courses</a>
    </li>

    <li class="nav-item">
      <a class="nav-link card-title" id="lectures-tab" data-bs-toggle="tab" href="#lectures" role="tab" aria-controls="lectures" aria-selected="false">Lectures</a>
    </li>

         <li class="nav-item">
      <a class="nav-link card-title" id="training-tab" data-bs-toggle="tab" href="#training" role="tab" aria-controls="training" aria-selected="false">Trainings</a>
    </li>
 
  </ul>
  <div class="tab-content courses" id="myTabContent">
    <div class="tab-pane fade" id="lectures" role="tabpanel" aria-labelledby="lectures-tab">    
    {% for group in grouped_data %}
    <div class="row">
      {% for item in group.items %}
        {% if item.type == 'Lectures'  %}
          <div class="col-md-12">
            <div class="">
              <div class="card-body">
                <h5 class="title">{{ item.title }}</h5>
                <p class="subtitle mb-1 text-muted">Event: {{ item.lecture }} on {{ item.date }} | Audience: {{ item.attendees }}</p>
                <p class="card-text">{{ item.details }}  {% if item.url %}
                   <a class="news-title" href="{{ item.url | relative_url }}">(link)</a>
                {% endif %}</p>
                
              </div>
            </div>
          </div>
      {% endif %}
      {% endfor %}
    </div>
  {% endfor %}
   </div>
      <div class="tab-pane fade" id="training" role="tabpanel" aria-labelledby="training-tab">    
        {% for group in grouped_data %}
    <div class="row">
      {% for item in group.items %}
        {% if item.type == 'Training' %}
          <div class="col-md-12">
            <div class="">
              <div class="card-body">
                <h5 class="card-title"  >{{ item.title }}</h5>
                <p class="card-subtitle mb-1 text-muted">{{ item.with }} |  {{ item.date }} | Audience: {{ item.attendees }}</p>
                <!-- {% if item.event %}
                <p class="card-subtitle mb-2 text-muted"><strong>Event:</strong>  {{ item.lecture }}</p>
                {% endif %}                -->
                <p class="card-subtitle mb-1 text-muted">{{ item.role }}</p>
                <!-- <p class="card-subtitle mb-2 text-muted"><strong>With:</strong>  {{ item.with }}  </p>
                {% if item.attendees %}
                <p class="card-subtitle mb-2 text-muted"><strong>Attendees:</strong> </p>
                {% endif %}                -->
                <p class="card-text">{{ item.details }}  {% if item.url %}
                   <a class="news-title" href="{{ item.url | relative_url }}">Link</a>
                {% endif %}</p>
                
              </div>
            </div>
          </div>
      {% endif %}
      {% endfor %}
    </div>
  {% endfor %}   
      </div>
      <div class="tab-pane fade  show active" id="courses" role="tabpanel" aria-labelledby="courses-tab">  
      {% for group in grouped_data %}
    <div class="row">
      {% for item in group.items %}
        {% if item.type == 'Courses'%}
          <div class="col-md-12">
            <div class="">
              <div class="card-body">
                <h5 class="card-title">{{ item.course }} -- {{ item.title }}</h5>
                <p class="card-subtitle mb-1 text-muted">{{ item.with }} | {{ item.semester }}</p>
                <!-- <p class="card-subtitle mb-2"><strong>Date :</strong>  {{ item.semester }}</p>            -->
                {% if item.role == 'TA and co-lecturer' %}
                <p class="card-subtitle mb-1 text-muted"> TA and Co-Lecturer</p>
                {% else %}
                <p class="card-subtitle mb-1"><em>{{ item.role }}</em></p>
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


  </div> 
</div>




 


<!--  

  {% for group in grouped_data %}
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
   -->
