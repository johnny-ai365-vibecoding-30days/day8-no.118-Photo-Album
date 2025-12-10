---
layout: single
title: "相簿"
permalink: /album/
classes: wide
description: "瀏覽新上傳的 Hololive 縮圖收藏。"
---

這裡整理了剛上傳的所有縮圖，點擊縮圖即可開啟原檔。

<ul class="gallery-grid">
  {% assign holo_images = site.static_files | where_exp: "file", "file.path contains '/assets/images/holo/'" | sort: "name" %}
  {% for image in holo_images %}
    {% assign base_name = image.name | remove: '_list_thumb' | split: '.' | first %}
    {% assign label = base_name | replace: '-', ' ' | replace: '_', ' ' %}
    <li>
      <figure>
        <a href="{{ image.path | relative_url }}">
          <img src="{{ image.path | relative_url }}" alt="{{ label }}" loading="lazy" />
          <figcaption>{{ label }}</figcaption>
        </a>
      </figure>
    </li>
  {% endfor %}
</ul>
