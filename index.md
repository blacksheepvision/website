---
layout: default
---

# $ cat posts.txt
{:id="posts"}

<ul>
{% for post in site.categories.posts %}

{% if post.en %}
<li>{{ post.title }} :: <a href="{{ post.url }}" title="{{ post.description }}">Read article</a></li>
{% endif %}

{% endfor %}
</ul>
