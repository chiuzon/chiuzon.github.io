---
title:  ""
---

{% for post in site.posts %}
  <a href="{{post.url}}" class="row">
    <div class="col-4"> {{post.title}} </div>
    <div class="col-12">
      {{post.content | truncatewords: 20}}
    </div>
  </a>
{% endfor %}