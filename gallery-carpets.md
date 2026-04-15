---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 25px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; position: relative; display: flex; flex-direction: column; }
  
  .tag { position: absolute; top: 12px; left: 12px; padding: 5px 12px; border-radius: 15px; font-size: 10px; font-weight: bold; color: white; text-transform: uppercase; z-index: 10; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
  
  /* RENK KODLARI */
  .tag-bilo { background: #27ae60; }   /* Bülent - Yeşil */
  .tag-b { background: #8b4513; }      /* Curator - Kahve */
  .tag-g { background: #E1306C; }      /* Ikman - Pembe */
  .tag-a { background: #1a2a6c; }      /* Museum - Lacivert */
  .tag-bg { background: linear-gradient(to right, #8b4513, #E1306C); } /* Hibrit b+g */
  .tag-ba { background: linear-gradient(to right, #8b4513, #1a2a6c); } /* Hibrit b+a */
  .tag-none { background: #95a5a6; }   /* Diğerleri - Gri */

  .gallery-img { width: 100%; height: 320px; object-fit: cover; cursor: zoom-in; }
  .gallery-info { padding: 15px; text-align: center; font-size: 14px; background: #fdf5e6; flex-grow: 1; display: flex; align-items: center; justify-content: center; line-height: 1.5; color: #2c3e50; }
  
  .map-link { display: inline-block; margin-top: 10px; padding: 5px 12px; background: #fff; border: 1px solid #ddd; border-radius: 50px; text-decoration: none; color: #333; font-weight: bold; font-size: 11px; }
</style>

# 🧶 Expert Curation: Halı & Kilim Collection

<div class="gallery-grid">
  {% for item in site.data.descriptions %}
    <div class="gallery-item">
      <!-- Otomatik Etiket -->
      <span class="tag tag-{{ item.type }}">{{ item.tag }}</span>

      <!-- Resim -->
      <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" loading="lazy">
      
      <!-- Detaylı Açıklama (Emeğin burası hocam!) -->
      <div class="gallery-info">
        <div>
          <p style="margin:0;">{{ item.text }}</p>
          
          <!-- Otomatik Konum Butonları -->
          {% if item.type contains 'bilo' %}
            <a href="https://maps.app.goo.gl/ZisXv6iX3L6XG6y4A" target="_blank" class="map-link">📍 Kervan Maps</a>
          {% elsif item.type contains 'g' %}
            <a href="https://maps.app.goo.gl/HqSgYhS5v6eB2Zq19" target="_blank" class="map-link">📍 Ikman Maps</a>
          {% else %}
            <a href="https://maps.app.goo.gl/96uW6NfB9eK2Xq9A7" target="_blank" class="map-link">📍 Exhibition Location</a>
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