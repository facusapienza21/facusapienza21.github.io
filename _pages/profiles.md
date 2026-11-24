---
layout: profiles
permalink: /people/
title: People
description: I am building a new research group at the Institute of Environmental Geosciences (IGE), Université Grenoble Alpes. I am also grateful to the incredible mentors I have worked with along the way.
nav: true
nav_order: 2
profiles_title: Former Mentors

profiles:
  # if you want to include more than one profile, just replicate the following block
  # and create one content file for each profile inside _pages/
  - align: left
    image: Yao.jpg
    content: about_yao.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: fernando.jpg
    content: about_fernando.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: jonathan.jpg
    content: about_jonathan.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: patu.jpg
    content: about_patu.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: matt.jpg
    content: about_matt.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: augusto.jpg
    content: about_augusto.md
    image_circular: false # crops the image to make it circular
  - align: left
    image: leo.jpg
    content: about_leo.md
    image_circular: false # crops the image to make it circular
---
<h2 class="category">Open Positions</h2>

I am recruiting a PhD student and a postdoctoral researcher to join my group in Grenoble, working at the intersection of physics-informed machine learning, differentiable programming and the geosciences.

<div class="row">
  <div class="col-12 mb-4">
    <div class="card">
      <div class="card-body p-4">
        <h3 class="card-title">PhD Position</h3>
        <p class="card-text">
          A PhD position on physics-informed machine learning for modelling mass balance processes in Andean glaciers.
          The PhD student will be part of the <a href="https://odinn-group.org" target="_blank">ODINN group</a>.
          The PhD will be supervised by Facundo Sapienza (main supervisor), with <a href="https://jordibolibar.wordpress.com/" target="_blank">Jordi Bolibar</a> and <a href="https://www.ige-grenoble.fr/Antoine-Rabatel" target="_blank">Antoine Rabatel</a> as co-advisors.
          <!-- TODO: add start date, duration and a short description of the topic -->
        </p>
        <ul class="position-links">
          {% comment %} Shown automatically once assets/pdf/phd_position.pdf exists {% endcomment %}
          {% assign phd_description = site.static_files | where: "path", "/assets/pdf/phd_position.pdf" | first %}
          {% if phd_description %}
          <li>
            <i class="material-icons">article</i>
            <span><a href="{{ '/phd-position/' | relative_url }}">Job description</a>: read it before applying</span>
          </li>
          {% endif %}
          <li>
            <i class="material-icons">description</i>
            <span><a href="{{ '/phd-application/' | relative_url }}">Application form</a>: view it online or download it as a PDF</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <div class="col-12 mb-4">
    <div class="card">
      <div class="card-body p-4">
        <h3 class="card-title">Postdoc Position</h3>
        <p class="card-text">
          A postdoctoral position on physics-informed machine learning and differentiable programming for the geosciences.
          <!-- TODO: add start date, duration, a short description of the topic and how to apply -->
          More information to come soon!
        </p>
      </div>
    </div>
  </div>
</div>

<h2 class="category mt-5">Former Students</h2>

<h3>Master Students</h3>

<ul>
  <li>
    <strong>Francisco Valdez</strong> (University of Buenos Aires, co-director: <a href="https://mate.dm.uba.ar/~pgroisma" target="_blank">Pablo Groisman</a>), 03/2026–07/2026<br>
    Thesis: <em>Machine learning with stochastic differential equations with applications to paleomagnetism</em>
  </li>
</ul>
