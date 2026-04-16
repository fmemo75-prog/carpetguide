---
layout: default
title: Family & Memories
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); grid-gap: 20px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; display: flex; flex-direction: column; }
  .gallery-img { width: 100%; height: 260px; object-fit: cover; cursor: zoom-in; }
  .gallery-info { padding: 12px; text-align: center; font-size: 13px; background: #fdf5e6; }
</style>

# 👨‍👩‍👧‍👦 Family & Memories

<div class="gallery-grid">
  {% for file in site.static_files %}
    {% if file.path contains '/images/aile-' %}
      <div class="gallery-item">
        <a href="{{ site.baseurl }}{{ file.path }}" target="_blank">
          <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" loading="lazy">
        </a>
        <div class="gallery-info">❤️ Memory</div>
      </div>
    {% endif %}
  {% endfor %}
</div>

<hr>
<p style="text-align: center;"><a href="./gallery">⬅️ Back to Collections</a></p>