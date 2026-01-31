---
layout: default
title: Advisories (CVE)
nav_order: 2
has_toc: false

permalink: /advisories/
---

# Advisories

This section contains **security advisories associated with CVEs**.

{% assign adv_pages = site.pages
  | where_exp: "p", "p.dir == '/advisories/'"
  | where_exp: "p", "p.name != 'index.md'"
  | sort: "date"
  | reverse %}

{% if adv_pages.size == 0 %}
_No advisories published yet._
{% else %}

<table>
  <thead>
    <tr>
      <th>CVE</th>
      <th>Title</th>
      <th>Product</th>
      <th>CVSS</th>
    </tr>
  </thead>
  <tbody>
  {% for p in adv_pages %}
    <tr>
      <td>{{ p.cve | default: '—' }}</td>
      <td><a href="{{ p.url | relative_url }}">{{ p.short_title | default: p.title }}</a></td>
      <td>{{ p.product | default: '—' }}</td>
      <td>
        v3.1 {{ p.cvss31_score | default: '—' }}{% if p.cvss31_severity %} ({{ p.cvss31_severity }}){% endif %}
        /
        v4.0 {{ p.cvss40_score | default: '—' }}{% if p.cvss40_severity %} ({{ p.cvss40_severity }}){% endif %}
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>

{% endif %}
