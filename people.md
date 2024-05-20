---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|gradstudent|postbacc|undergrad|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Fellows</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigator</h3>
 {% elsif role == 'gradstudent' %}
<h3>Graduate Students</h3>
 {% elsif role == 'postbacc' %}
<h3>Post-bacc</h3>
 {% elsif role == 'undergrad' %}
<h3>Undergraduate Students</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni and Former Trainees</h3>
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/douglas-fir.png"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>

{% else %}

<br>

| Who | When | Next destination |
| :------------- |:-------------| :-----------|
| Jonathan Wood (co-advised with Susanne Morton) | PhD student (2018-2023) | Postdoc at Moss Rehabilitation Institute | 
| [Jonathan Tsay](https://www.tsaylab.com/contact) (primary advisor: Rich Ivry) | PhD student (2018-2023) | Starting as Asst. Professor at Carnegie Mellon University in 2024 |
| John Buggeln | PhD student (2022-2023) | PhD student in Cashaback Lab at University of Delaware |
| Amanda Arteaga | Undergraduate RA (2024) |       |
| Rebecca Niven | Post-bacc RA (2023-2024) |       |
| Joie Tang | Undergraduate RA and lab manager (2019-2023) | DPT student at University of Delaware |
| Heran Yosef | Undergraduate RA and lab manager (2020-2022) | Med school student at Thomas Jefferson University |
| Nicholas Sekulski | Undergraduate RA (2021-2022) | Master's student in Biopharmaceutical Sciences at University of Delaware |
| [Kaneel Senevirathne](https://www.linkedin.com/in/kaneel123) | Master's student (2020-2021) | AI/ML Researcher at Johns Hopkins University |
| Megan Phillips | Summer rotation student (2020) | Undergraduate Psych student at Wayne State University |
| Gabby Kowalski | Lab manager (2020) | OTD student at The Ohio State University |
| Chanel Smith | Undergraduate RA (2019-2020) | Quality Control Microbiologist at AGC |


{% endif %}
{% endfor %}
