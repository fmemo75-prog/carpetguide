---
layout: default
title: Cappadocia Digital Gallery
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 25px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; display: flex; flex-direction: column; }
  
  /* Resim alanı */
  .gallery-link { display: block; width: 100%; height: 280px; overflow: hidden; cursor: zoom-in; }
  .gallery-img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.3s ease; }
  .gallery-link:hover .gallery-img { transform: scale(1.05); }

  /* Açıklama alanı */
  .gallery-info { padding: 15px; text-align: center; font-size: 14px; color: #444; background: #fdf5e6; border-top: 1px solid #eee; flex-grow: 1; line-height: 1.5; }
  .has-caption { color: #333; }
  .gallery-info a { color: #8b0000; text-decoration: none; }
  .gallery-info a:hover { text-decoration: underline; }
</style>

# 📸 Cappadocia Through My Lens
**A Private Collection by Fatih Mehmet Canıtez**

<div class="gallery-grid">
  {% assign all_files = site.static_files | sort: "path" | reverse %}
  {% for file in all_files %}
    {% if file.path contains '/images/' %}
      {% if file.extname == '.jpg' or file.extname == '.png' or file.extname == '.jpeg' or file.extname == '.webp' %}
        {% unless file.path contains 'carpet.jpeg' or file.path contains 'loom.jpg' or file.path contains 'cappadocia-balloons.jpg' %}
        
        {% assign filename = file.path | split: "/" | last %}
        {% assign custom_caption = site.data.descriptions[filename] %}

        <div class="gallery-item">
          <!-- Sadece resim tıklanınca büyür -->
          <a href="{{ site.baseurl }}{{ file.path }}" target="_blank" class="gallery-link">
            <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" alt="Cappadocia" loading="lazy">
          </a>
          
          <!-- Açıklama alanı ve linkler burada aktif olur -->
          <div class="gallery-info">
            {% if custom_caption %}
              <span class="has-caption">{{ custom_caption }}</span>
            {% else %}
              <span style="color:#999;">🔍 Click image to enlarge</span>
            {% endif %}
          </div>
        </div>
        
        {% endunless %}
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<p style="text-align: center;"><a href="./" style="color: #8b0000; font-weight: bold; text-decoration: none;">🏠 Return to Main Dashboard</a></p>