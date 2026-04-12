---
layout: default
title: Cappadocia Digital Gallery
---

<style>
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    grid-gap: 20px;
    padding: 20px 0;
  }
  .gallery-item {
    background: #fff;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
    border: 1px solid #eee;
  }
  .gallery-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 25px rgba(0,0,0,0.2);
  }
  .gallery-img {
    width: 100%;
    height: 280px;
    object-fit: cover; /* Resimleri bozmadan kutuya sığdırır */
    display: block;
    cursor: zoom-in;
  }
  .gallery-info {
    padding: 10px;
    text-align: center;
    font-size: 13px;
    color: #8b0000;
    font-weight: bold;
    background: #fdf5e6;
  }
</style>

# 📸 Cappadocia Through My Lens
**A Professional Collection by Fatih Mehmet Canıtez**

Welcome to my live archive. Every photo you see here was captured by me across the valleys and villages of Cappadocia. The gallery updates automatically as I add new captures to my collection.

<div class="gallery-grid">
  <!-- AKILLI DÖNGÜ: images klasöründeki tüm resimleri otomatik bulur -->
  {% assign all_files = site.static_files | sort: "path" | reverse %}
  {% for file in all_files %}
    {% if file.path contains '/images/' %}
      {% if file.extname == '.jpg' or file.extname == '.png' or file.extname == '.jpeg' or file.extname == '.webp' %}
        
        <!-- Bazı sistem resimlerini (Logo, profil vb.) galeride göstermemek için filtre -->
        {% unless file.path contains 'carpet.jpeg' or file.path contains 'loom.jpg' or file.path contains 'cappadocia-balloons.jpg' %}
        <div class="gallery-item">
          <a href="{{ site.baseurl }}{{ file.path }}" target="_blank" title="Click to view full size">
            <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" alt="Cappadocia View" loading="lazy">
            <div class="gallery-info">
              🔍 Click to Enlarge
            </div>
          </a>
        </div>
        {% endunless %}
        
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

<hr style="margin-top: 50px;">

<div style="text-align: center;">
  <a href="./Cappodoce" style="color: #8b0000; font-weight: bold; text-decoration: none;">⬅️ Back to Cappadocia Guide</a> | 
  <a href="./" style="color: #8b0000; font-weight: bold; text-decoration: none;">🏠 Return to Main Dashboard</a>
</div>