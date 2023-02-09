---
layout: page
title: Publications
permalink: /publications/
---
	
{% for pub in site.publications %}
  <h2><a href='{{pub.permalink}}'> {{ pub.title }}</a></h2>
{% endfor %}
