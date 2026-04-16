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

# 🧶 Expert Select: Master Gallery

<div class="gallery-grid">
  {% for item in site.data.descriptions %}
    <!-- Profil bilgisini tipine göre çekiyoruz -->
    {% assign p = site.data.profiles[item.type] %}
    
    <div class="gallery-item">
      <!-- Etiket (Rengi ve İsmi Otomatik) -->
      <span class="tag" style="background: {{ p.color }};">{{ p.name }}</span>

      <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" loading="lazy">
      
      <div class="gallery-info">
        <p style="margin:0;">{{ item.text }}</p>
        
        <div class="btn-group">
          {% if p.map %}<a href="{{ p.map }}" target="_blank" class="map-btn">📍 Location</a>{% endif %}
          {% if p.instagram %}<a href="{{ p.instagram }}" target="_blank" class="map-btn ig-btn">📸 Instagram</a>{% endif %}
          {% if p.whatsapp %}<a href="https://wa.me/{{ p.whatsapp }}" target="_blank" class="map-btn wa-btn">💬 WhatsApp</a>{% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>