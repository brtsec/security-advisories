---
layout: default
title: Advisories (CVE)
nav_order: 2
---

# Advisories

This section contains **security advisories associated with CVEs**

{% assign adv_pages = site.pages
  | where_exp: "p", "p.dir == '/advisories/'"
  | where_exp: "p", "p.name != 'index.md'"
  | sort: "date"
  | reverse %}
  
{% if adv_pages.size == 0 %}
_No advisories published yet._
{% else %}

| CVE | Title | Product | CVSS |
| --- | --- | --- | --- |
{% for p in adv_pages %}
| {{ p.cve | default: '—' }} | [{{ p.short_title | default: p.title }}]({{ p.url | relative_url }}) | {{ p.product | default: '—' }} | v3.1 {{ p.cvss31_score | default: '—' }} / v4.0 {{ p.cvss40_severity | default: '—' }} |
{% endfor %}

{% endif %}
