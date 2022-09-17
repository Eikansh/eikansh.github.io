---
layout: default
---
# Hi, I'm Eikansh. 
## I'm Compiler Engineer at Qualcomm.
I love computers, and I am passionate to learn about them.

Apart from computers, I try to read from a variety of fields in my spare time. I also enjoy listening to podcasts and music, cooking, strength training, and anything that catches my attention.

Email : eikansh1 [at] iisc [dot] ac [dot] in

### **Recent posts:**
  {% assign posts = site.posts %}
  {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    <ul>
    {% assign i = 0 %}
    {%- for post in posts -%}
      {% assign i = i | plus:1 %}
      {% if i == 6 %}
        {% break %}
      {% endif %}
      <li>
        <h4>
          <a href="{{ post.url | relative_url }}"> {{ post.title | escape }}</a>
        </h4>
      </li>
    {%- endfor -%}
    </ul>
To view all post click [here](/archive.md).