---
layout: page
permalink: /repositories/
title: Repositories
description: This is some information about my GitHub profile, GitHub organzations where I contribute, and a short selection of repositories. 
nav: true
nav_order: 5
---

## GitHub user

{% if site.data.repositories.github_users %}
<div class="repo-grid">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.html user=user %}
  {% endfor %}
</div>
{% endif %}

## GitHub Organizations

I am currently developing [ODINN-SciML](https://github.com/ODINN-SciML) where we are working in developing ice flow models based on Universal Differential Equations in Julia. 
I am also part of [PolarWandering](https://github.com/PolarWandering), a collaboration for the development of statistical methods for paleomagnetic estimation. 

## GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repo-grid">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}
