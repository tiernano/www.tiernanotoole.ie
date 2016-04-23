---
layout: page
title: Computers
sitemap:
    priority: 0.7
    changefreq: 'monthly'
    lastmod: 2015-09-15T16:30:00
---

# My Home Lab

This page is a link of some of the machines and network devices I have in house.

{% for computer in site.data.computers %}
  <li>
    <a href="{{ computer.url }}">{{ computer.name }}</a>.
        {% if computer.decommissioned %} Status: Is decommissioned
        {% elsif computer.inuse %} Status: Is in use
        {% else %}
        Status: Unknown
        {% endif %}
  </li>
{% endfor %}
