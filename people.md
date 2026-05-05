---
layout: page
title: People
permalink: /people/
---

<div class="people-grid">

{%- assign people = site.people | where_exp: "p", "p.team != 'past'" -%}
{%- assign with_order = people | where_exp: "p", "p.order" | sort: "order" -%}
{%- assign without_order = people | where_exp: "p", "p.order == nil" | sort: "name" -%}
{%- assign members = with_order | concat: without_order -%}

{%- for p in members -%}
<article class="person-card">
  <a class="person-photo" href="{{ p.url | relative_url }}" {% if p.photo %}style="background-image:url('{{ p.photo | relative_url }}');"{% endif %} aria-label="{{ p.name }}"></a>

  <h3 class="person-name"><a href="{{ p.url | relative_url }}">{{ p.name }}</a></h3>
  {% if p.role %}<div class="person-role">{{ p.role }}</div>{% endif %}

        {%- if p.social -%}
        <div class="avatar-social">
            {% if p.social.bluesky %}
            <a href="{{ p.social.bluesky }}" aria-label="Bluesky" title="Bluesky" target="_blank" rel="noopener">
              <i class="fa-brands fa-bluesky fa"></i>
            </a>
            {% endif %}

          {%- if p.social.orcid -%}
          <a href="{{ p.social.orcid }}" aria-label="ORCID" title="ORCID" target="_blank" rel="noopener">
            <i class="fa-brands fa-orcid fa"></i>
          </a>
          {%- endif -%}

          {%- if p.social.linkedin -%}
          <a href="{{ p.social.linkedin }}" aria-label="LinkedIn" title="LinkedIn" target="_blank" rel="noopener">
            <i class="fa-brands fa-linkedin-in fa"></i>
          </a>
          {%- endif -%}

          {%- if p.social.github -%}
          <a href="{{ p.social.github }}" aria-label="GitHub" title="GitHub" target="_blank" rel="noopener">
            <i class="fa-brands fa-github fa"></i>
          </a>
          {%- endif -%}

          {%- if p.social.google_scholar -%}
          <a href="{{ p.social.google_scholar }}" aria-label="Google Scholar" title="Google Scholar" target="_blank" rel="noopener">
            <i class="fa-solid fa-graduation-cap"></i>
          </a>
          {%- endif -%}
        </div>
        {%- endif -%}
</article>
{%- endfor -%}
</div>

<h2>Past Members</h2>

<div class="people-grid">

{%- assign past = site.people | where: "status", "past" -%}
{%- assign with_order = past | where_exp: "p", "p.order" | sort: "order" -%}
{%- assign without_order = past | where_exp: "p", "p.order == nil" | sort: "name" -%}
{%- assign members = with_order | concat: without_order -%}

{%- for p in members -%}
<article class="person-card">
  <a class="person-photo" href="{{ p.url | relative_url }}"
     {% if p.photo %}
     style="background-image:url('{{ p.photo | relative_url }}');"
     {% endif %}
     aria-label="{{ p.name }}">
  </a>

  <h3 class="person-name">
    <a href="{{ p.url | relative_url }}">{{ p.name }}</a>
  </h3>

  {% if p.role %}
    <div class="person-role">{{ p.role }}</div>
  {% endif %}

  {%- if p.social -%}
  <div class="avatar-social">

    {% if p.social.bluesky %}
    <a href="{{ p.social.bluesky }}" target="_blank" rel="noopener">
      <i class="fa-brands fa-bluesky fa"></i>
    </a>
    {% endif %}

    {% if p.social.orcid %}
    <a href="{{ p.social.orcid }}" target="_blank" rel="noopener">
      <i class="fa-brands fa-orcid fa"></i>
    </a>
    {% endif %}

    {% if p.social.linkedin %}
    <a href="{{ p.social.linkedin }}" target="_blank" rel="noopener">
      <i class="fa-brands fa-linkedin-in fa"></i>
    </a>
    {% endif %}

    {% if p.social.github %}
    <a href="{{ p.social.github }}" target="_blank" rel="noopener">
      <i class="fa-brands fa-github fa"></i>
    </a>
    {% endif %}

    {% if p.social.google_scholar %}
    <a href="{{ p.social.google_scholar }}" target="_blank" rel="noopener">
      <i class="fa-solid fa-graduation-cap"></i>
    </a>
    {% endif %}

  </div>
  {%- endif -%}

</article>
{%- endfor -%}

</div>
