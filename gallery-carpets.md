---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 25px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; position: relative; display: flex; flex-direction: column; transition: 0.3s; }
  .tag { position: absolute; top: 12px; left: 12px; padding: 5px 12px; border-radius: 15px; font-size: 10px; font-weight: bold; color: white; text-transform: uppercase; z-index: 10; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
  
  .tag-bilo { background: #27ae60; }
  .tag-b { background: #8b4513; }
  .tag-g { background: #E1306C; }
  .tag-a { background: #1a2a6c; }
  .tag-bg { background: linear-gradient(to right, #8b4513, #E1306C); }
  .tag-ba { background: linear-gradient(to right, #8b4513, #1a2a6c); }
  .tag-none { background: #95a5a6; }

  .gallery-img { width: 100%; height: 320px; object-fit: cover; cursor: zoom-in; }
  .gallery-info { padding: 15px; text-align: center; font-size: 14px; background: #fdf5e6; flex-grow: 1; display: flex; align-items: center; justify-content: center; line-height: 1.5; flex-direction: column; }
  .map-btn { display: inline-block; margin-top: 10px; padding: 8px 18px; background: #fff; border: 1px solid #ddd; border-radius: 50px; text-decoration: none; color: #333; font-weight: bold; font-size: 11px; transition: 0.3s; }
  .map-btn:hover { background: #8b0000; color: #fff !important; }
</style>

# 🧶 Expert Curation: Organized Gallery
**Organized by Expertise, Provenance & Partnership**

<div class="gallery-grid">
  {% for item in site.data.descriptions %}
    <div class="gallery-item">
      <span class="tag tag-{{ item.type }}">{{ item.tag }}</span>
      <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" loading="lazy">
      <div class="gallery-info">
        <div>
          <p style="margin:0;">{{ item.text }}</p>
          {% if item.map %}
            <a href="{{ item.map }}" target="_blank" class="map-btn">📍 View Location</a>
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<div style="text-align: center;">
  <a href="./gallery" style="font-weight: bold; color: #8b0000; text-decoration: none;">⬅️ Back to All Collections</a>
</div>