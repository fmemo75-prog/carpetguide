---
layout: default
title: Cappadocia Digital Gallery
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 20px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); transition: transform 0.3s ease; border: 1px solid #eee; }
  .gallery-item:hover { transform: translateY(-5px); box-shadow: 0 10px 25px rgba(0,0,0,0.2); }
  .gallery-img { width: 100%; height: 280px; object-fit: cover; display: block; cursor: zoom-in; }
  .gallery-info { padding: 12px; text-align: center; font-size: 14px; color: #444; background: #fdf5e6; border-top: 1px solid #eee; min-height: 40px; display: flex; align-items: center; justify-content: center; }
  .has-caption { color: #8b0000; font-weight: bold; } /* Özel açıklaması olanlar kırmızı/kalın görünsün */
</style>

# 📸 Cappadocia Through My Lens
**A Live Collection by Fatih Mehmet Canıtez**

<div class="gallery-grid">
  {% assign all_files = site.static_files | sort: "path" | reverse %}
  {% for file in all_files %}
    {% if file.path contains '/images/' %}
      {% if file.extname == '.jpg' or file.extname == '.png' or file.extname == '.jpeg' or file.extname == '.webp' %}
        {% unless file.path contains 'carpet.jpeg' or file.path contains 'loom.jpg' or file.path contains 'cappadocia-balloons.jpg' %}
        
        <!-- DOSYA ADINI YAKALA -->
        {% assign filename = file.path | split: "/" | last %}
        <!-- LİSTEDEN AÇIKLAMAYI ÇEK -->
        {% assign custom_caption = site.data.descriptions[filename] %}

        <div class="gallery-item">
          <a href="{{ site.baseurl }}{{ file.path }}" target="_blank">
            <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" alt="Cappadocia" loading="lazy">
            <div class="gallery-info">
              {% if custom_caption %}
                <span class="has-caption">{{ custom_caption }}</span>
              {% else %}
                <span>🔍 Click to Enlarge</span>
              {% endif %}
            </div>
          </a>
        </div>
        
        {% endunless %}
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<p style="text-align: center;"><a href="./" style="color: #8b0000; font-weight: bold; text-decoration: none;">🏠 Return to Main Dashboard</a></p>