---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); grid-gap: 30px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; display: flex; flex-direction: column; }
  .gallery-link { display: block; width: 100%; height: 320px; overflow: hidden; cursor: zoom-in; }
  .gallery-img { width: 100%; height: 100%; object-fit: cover; transition: 0.3s; }
  .gallery-link:hover .gallery-img { transform: scale(1.05); }
  .gallery-info { padding: 20px; text-align: center; font-size: 14px; color: #333; background: #fdf5e6; border-top: 1px solid #eee; flex-grow: 1; line-height: 1.6; }
  .section-title { background: #8b0000; color: white; padding: 10px 20px; border-radius: 50px; display: inline-block; margin: 40px 0 20px 0; font-size: 1.1em; }
</style>

# 🧶 The Curator's Select: Halı & Kilim Collection

<p>This gallery is organized by provenance and expertise. Follow the links below for locations and professional contacts.</p>

<div class="gallery-grid">
  <!-- SIRALI DÖNGÜ: descriptions.yml dosyasındaki sırayla döner -->
  {% for item in site.data.descriptions %}
    {% assign filename = item[0] %}
    {% assign custom_caption = item[1] %}
    
    {% if filename contains 'hali-' %}
    <div class="gallery-item">
      <a href="{{ site.baseurl }}/images/{{ filename }}" target="_blank" class="gallery-link">
        <img src="{{ site.baseurl }}/images/{{ filename }}" class="gallery-img" alt="Carpet Masterpiece" loading="lazy">
      </a>
      <div class="gallery-info">
        {{ custom_caption }}
      </div>
    </div>
    {% endif %}
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<div style="text-align: center;">
  <a href="./gallery" style="font-weight: bold; color: #8b0000; text-decoration: none;">⬅️ Back to All Collections</a>
</div>