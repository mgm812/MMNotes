---
layout: page
title: 归档
---

<table>
    <thead>
        <tr>
            <th>日期</th>
            <th>文章</th>
        </tr>
    </thead>
    <tbody>
        {% for post in site.posts %}
        <tr>
            <td>{{ post.date | date_to_string }}</td>
            <td><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></td>
        </tr>
        {% endfor %}
    </tbody>
</table>


