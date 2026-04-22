---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 25px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; position: relative; display: flex; flex-direction: column; }
  .tag { position: absolute; top: 12px; left: 12px; padding: 5px 12px; border-radius: 15px; font-size: 10px; font-weight: bold; color: white; text-transform: uppercase; z-index: 10; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
  .gallery-img { width: 100%; height: 300px; object-fit: cover; cursor: zoom-in; }
  .gallery-info { padding: 15px; text-align: center; font-size: 14px; background: #fdf5e6; flex-grow: 1; display: flex; align-items: center; justify-content: center; line-height: 1.5; flex-direction: column; color: #2c3e50; }
  .btn-group { display: flex; gap: 5px; flex-wrap: wrap; justify-content: center; margin-top: 10px; }
  .map-btn { display: inline-block; padding: 6px 12px; background: #fff; border: 1px solid #ddd; border-radius: 50px; text-decoration: none; color: #333; font-weight: bold; font-size: 11px; transition: 0.2s; }
  .ig-btn { border-color: #E1306C; color: #E1306C !important; }
  .wa-btn { border-color: #25D366; color: #25D366 !important; }
</style>

# 🧶 Expert Curation: Master Gallery

<div class="gallery-grid">
  {% for item in site.data.descriptions %}
    
    <!-- HALI KATEGORİSİNDEKİLERİ FİLTRELE -->
    {% if item.type == "b" or item.type == "g" or item.type == "a" or item.type == "bilo" or item.type == "bg" or item.type == "ba" %}
    
    <div class="gallery-item">
      <!-- Dinamik Etiket Belirleme -->
      {% if item.type == "bilo" %}
        <span class="tag" style="background: #27ae60;">Bülent Güler</span>
      {% elsif item.type == "g" %}
        <span class="tag" style="background: #E1306C;">Galerie Ikman</span>
      {% elsif item.type == "a" %}
        <span class="tag" style="background: #1a2a6c;">Museum Piece</span>
      {% elsif item.type == "b" %}
        <span class="tag" style="background: #8b4513;">Curator</span>
      {% elsif item.type == "bg" %}
        <span class="tag" style="background: linear-gradient(to right, #8b4513, #E1306C);">Curator & Ikman</span>
      {% elsif item.type == "ba" %}
        <span class="tag" style="background: linear-gradient(to right, #8b4513, #1a2a6c);">Curator & Museum</span>
      {% endif %}

      <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" loading="lazy">
      
      <div class="gallery-info">
        <p style="margin:0;">{{ item.text }}</p>
        
        <div class="btn-group">
          <!-- Butonları Manuel Kontrol Edelim (Hata payı sıfır) -->
          {% if item.type contains 'bilo' %}
            <a href="https://www.google.com/maps/search/?api=1&query=Kervan+Carpet+Goreme" target="_blank" class="map-btn">📍 Location</a>
            <a href="https://wa.me/905367602165" target="_blank" class="map-btn wa-btn">💬 WhatsApp</a>
          {% endif %}

          {% if item.type contains 'g' %}
            <a href="https://www.google.com/maps/search/?api=1&query=Galerie+Ikman+Goreme" target="_blank" class="map-btn">📍 Location</a>
            <a href="https://www.instagram.com/galerieikman/" target="_blank" class="map-btn ig-btn">📸 Instagram</a>
          {% endif %}

          {% if item.type contains 'a' %}
            <a href="https://www.google.com/maps/search/?api=1&query=Anatolian+Art+Museum+Goreme" target="_blank" class="map-btn">📍 Museum</a>
          {% endif %}

          {% if item.type == 'b' %}
            <a href="https://www.google.com/maps/search/?api=1&query=Goreme+Cappadocia" target="_blank" class="map-btn">📍 Curator View</a>
          {% endif %}
        </div>
      </div>
    </div>
    {% endif %}
  {% endfor %}
</div>