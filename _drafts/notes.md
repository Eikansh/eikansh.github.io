---
layout: default
title: Notes
permalink: /notes/
---
<header class="post-header">
    <h1 class="post-title">{{ page.title | escape }}</h1>
</header>

This page contains notes from the books I read.  

My [Goodreads profile](https://www.goodreads.com/eikansh)

<ul class="post-list">
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
      {%- for note in site.notes reversed -%}
      <li>
        <span class="post-meta">{{ note.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ note.url | relative_url }}">
            {{ note.title | escape }}
          </a>
        </h3>
      </li>
      {%- endfor -%}
</ul>
