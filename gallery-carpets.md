---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); grid-gap: 30px; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; position: relative; display: flex; flex-direction: column; }
  
  .tag-container { position: absolute; top: 12px; left: 12px; display: flex; flex-wrap: wrap; gap: 5px; z-index: 10; }
  .tag { padding: 4px 10px; border-radius: 15px; font-size: 10px; font-weight: bold; color: white; text-transform: uppercase; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
  .tag-curator { background: #8b4513; }
  .tag-ikman { background: #E1306C; }
  .tag-museum { background: #1a2a6c; }
  .tag-bilo { background: #27ae60; }

  .gallery-img { width: 100%; height: 320px; object-fit: cover; cursor: zoom-in; transition: 0.3s; }
  .gallery-info { padding: 20px; text-align: center; font-size: 14px; background: #fdf5e6; flex-grow: 1; display: flex; flex-direction: column; justify-content: center; }
  .btn-area { margin-top: 15px; display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; }
  .action-btn { padding: 6px 12px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 11px; border: 1px solid #ddd; background: #fff; color: #333; }
</style>

# 🧶 Expert Curation: Multimedia Gallery

<div class="gallery-grid">
  {% for item in site.data.descriptions %}
    <div class="gallery-item">
      <div class="tag-container">
        <!-- ÇOKLU ETİKET MANTIĞI -->
        {% if item.file contains 'bilo' %}<span class="tag tag-bilo">Bülent Güler</span>{% endif %}
        
        {% if item.file contains 'b' %}
          {% unless item.file contains 'bilo' %}<span class="tag tag-curator">Curator</span>{% endunless %}
        {% endif %}
        
        {% if item.file contains 'g' %}<span class="tag tag-ikman">Galerie Ikman</span>{% endif %}
        {% if item.file contains 'a' %}<span class="tag tag-museum">Museum Piece</span>{% endif %}
      </div>

      <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" loading="lazy">
      
      <div class="gallery-info">
        <p style="margin:0;">{{ item.text }}</p>
        
        <div class="btn-area">
          <!-- AKILLI BUTONLAR (Öncelik Sırasına Göre) -->
          {% if item.file contains 'g' %}
            <a href="https://maps.app.goo.gl/HqSgYhS5v6eB2Zq19" target="_blank" class="action-btn">📍 Ikman Maps</a>
          {% elsif item.file contains 'bilo' %}
            <a href="https://maps.app.goo.gl/ZisXv6iX3L6XG6y4A" target="_blank" class="action-btn">📍 Kervan Maps</a>
          {% elsif item.file contains 'a' %}
            <a href="https://maps.app.goo.gl/96uW6NfB9eK2Xq9A7" target="_blank" class="action-btn">📍 Museum Maps</a>
          {% else %}
            <a href="https://maps.app.goo.gl/96uW6NfB9eK2Xq9A7" target="_blank" class="action-btn">📍 Curator View</a>
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>