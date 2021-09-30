---
layout: home
title: Hello World!
---

 {% for post in paginator.posts %}
    <li class="article__item">
        <a class="article__title" href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    <span class="article__date">{{ post.date | date_to_string }} </span>
    </li>
 {% endfor %}


 {% if paginator.total_pages > 1 %}
  <!-- 分页代码 -->

  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">上一页</a>
  {% endif %}

  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
      <span class="active">{{ page }}</span>
    {% elsif page == 1 %}
      <a href="{{ '/index.html' | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
    {% else %}
      <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  {% endfor %}

  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">下一页</a>
  {% endif %}
 {% endif %}
