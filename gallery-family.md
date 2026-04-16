---
layout: default
title: Family & Memories
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); grid-gap: 25px; padding: 20px 0; }
  .gallery-item { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; display: flex; flex-direction: column; transition: 0.3s; }
  .gallery-item:hover { transform: translateY(-5px); }
  .gallery-link { display: block; width: 100%; height: 300px; overflow: hidden; cursor: zoom-in; }
  .gallery-img { width: 100%; height: 100%; object-fit: cover; }
  .gallery-info { padding: 15px; text-align: center; font-size: 14px; color: #444; background: #fdf5e6; border-top: 1px solid #eee; flex-grow: 1; }
</style>

# 👨‍👩‍👧‍👦 Family, Friends & Memories
**The Personal Archive of Fatih Mehmet Canıtez**

Behind every expert is a lifetime of memories. This collection is dedicated to the people and moments that make life beautiful.

<div class="gallery-grid">
  {% assign all_files = site.static_files | sort: "path" %}
  {% for file in all_files %}
    <!-- SADECE 'aile-' İLE BAŞLAYANLARI FİLTRELE -->
    {% if file.path contains '/images/aile-' %}
        
        {% assign filename = file.path | split: "/" | last %}
        {% assign custom_caption = site.data.descriptions[filename] %}

        <div class="gallery-item">
          <a href="{{ site.baseurl }}{{ file.path }}" target="_blank" class="gallery-link">
            <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" alt="Family Memory" loading="lazy">
          </a>
          <div class="gallery-info">
            {{ custom_caption | default: "❤️ Special Moment <br> Click to enlarge" }}
          </div>
        </div>

    {% endif %}
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<div style="text-align: center;">
  <a href="./gallery" style="font-weight: bold; color: #8b0000;">⬅️ Back to All Collections</a> | 
  <a href="./" style="font-weight: bold; color: #8b0000;">🏠 Home</a>
</div>