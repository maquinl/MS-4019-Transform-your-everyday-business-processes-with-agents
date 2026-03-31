---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

This page lists exercises associated with Microsoft skilling content on [Microsoft Learn](https://learn.microsoft.com/en-us/training/courses/ms-4019)

<hr>
{%- assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" | where_exp:"page", "page.lab.title" | sort: "url" -%}
{%- assign current_module = "" -%}
{%- for activity in labs -%}
{%- assign relative_url = activity.url | remove: "/Instructions/Labs/" -%}
{%- assign module_folder = relative_url | split: "/" | first -%}
{%- if module_folder != current_module -%}
{%- assign current_module = module_folder %}

### {{ module_folder }}

| Lab | Level | Duration |
| --- | --- | --- |
| [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) | {{ activity.lab.level }} | {{ activity.lab.duration }} |
{%- else %}
| [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) | {{ activity.lab.level }} | {{ activity.lab.duration }} |
{%- endif -%}
{%- endfor %}
