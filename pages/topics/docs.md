---
layout: page
title: Documentation
description: Contents
permalink: /docs/
---

# Documentation

Welcome to the {{ site.title }} documentation pages! Here you can quickly jump to a 
particular page.


<div class="section-index">
    <hr class="panel-line">

    {% assign folder_categories = 'project,dataset' | split: ',' %}
    {% assign sorted_docs = site.docs | sort: 'path' %}
    {% assign sorted_docs_custom = "" | split: "," %}

    {% for folder_category in folder_categories %}
        {% assign docs_in_folder = sorted_docs | where_exp: "doc", "doc.categories contains folder_category" %}
        {% assign sorted_docs_custom = sorted_docs_custom | concat: docs_in_folder %}
    {% endfor %}

    {% for docs_post in sorted_docs_custom %}
        <div class="entry">
            <h5><a href="{{ docs_post.url | prepend: site.baseurl }}">{{ docs_post.title }}</a></h5>
            <p>{{ docs_post.description }}</p>
        </div>
    {% endfor %}

</div>
