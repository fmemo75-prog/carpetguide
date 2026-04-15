---
layout: default
title: Expert Carpet Collection
---

<style>
  .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); grid-gap: 30px; }
  .gallery-item { background: #fff; border-radius: 15px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; position: relative; display: flex; flex-direction: column; transition: 0.3s; }
  .gallery-item:hover { transform: translateY(-5px); box-shadow: 0 10px 25px rgba(0,0,0,0.2); }
  
  /* AKILLI ETİKETLER */
  .tag-container { position: absolute; top: 12px; left: 12px; display: flex; flex-wrap: wrap; gap: 5px; z-index: 10; }
  .tag { padding: 4px 10px; border-radius: 15px; font-size: 10px; font-weight: bold; color: white; text-transform: uppercase; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
  .tag-b { background: #8b4513; } /* Curator (Kahve) */
  .tag-g { background: #E1306C; } /* Ikman (Pembe) */
  .tag-a { background: #1a2a6c; } /* Museum (Lacivert) */
  .tag-bilo { background: #27ae60; } /* Bilo (Yeşil) */

  .gallery-link { display: block; width: 100%; height: 320px; overflow: hidden; cursor: zoom-in; }
  .gallery-img { width: 100%; height: 100%; object-fit: cover; transition: 0.4s; }
  .gallery-link:hover .gallery-img { transform: scale(1.08); }
  
  .gallery-info { padding: 20px; text-align: center; font-size: 14px; background: #fdf5e6; flex-grow: 1; display: flex; flex-direction: column; justify-content: center; }
  .btn-area { margin-top: 15px; display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; }
  .action-btn { padding: 6px 12px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 11px; border: 1px solid #ddd; background: #fff; color: #333; transition: 0.2s; }
  .action-btn:hover { background: #f0f0f0; border-color: #bbb; }
  .wa-btn { border-color: #25D366; color: #25D366; }
  .wa-btn:hover { background: #eaffea; }
</style>

# 🧶 The Curator's Select: Halı & Kilim Collection
**Organized by Expertise, Provenance & Partnership**

<div class="gallery-grid">
  <!-- DÖNGÜ: descriptions.yml dosyasındaki sıralamayı takip eder -->
  {% for item in site.data.descriptions %}
    <div class="gallery-item">
      
      <!-- OTOMATİK ETİKET SİSTEMİ (Dosya ismindeki harflere bakar) -->
      <div class="tag-container">
        {% if item.file contains 'bilo' %}<span class="tag tag-bilo">Bülent Güler</span>{% endif %}
        
        <!-- Eğer isimde 'b' varsa ama 'bilo' değilse (Sizseniz) -->
        {% if item.file contains 'b' %}
            {% unless item.file contains 'bilo' %}
                <span class="tag tag-b">Curator</span>
            {% endunless %}
        {% endif %}

        {% if item.file contains 'g' %}<span class="tag tag-g">Galerie Ikman</span>{% endif %}
        {% if item.file contains 'a' %}<span class="tag tag-a">Museum</span>{% endif %}
      </div>

      <!-- Resim ve Zoom Linki -->
      <a href="{{ site.baseurl }}/images/{{ item.file }}" target="_blank" class="gallery-link">
        <img src="{{ site.baseurl }}/images/{{ item.file }}" class="gallery-img" alt="Carpet Masterpiece" loading="lazy">
      </a>
      
      <div class="gallery-info">
        <p style="margin:0; line-height:1.5; color: #2c3e50;">{{ item.text }}</p>

        <div class="btn-area">
          <!-- OTOMATİK KONUM VE WHATSAPP BUTONLARI -->
          
          {% if item.file contains 'bilo' %}
            <a href="https://maps.app.goo.gl/ZisXv6iX3L6XG6y4A" target="_blank" class="action-btn">📍 Kervan Maps</a>
            <a href="https://wa.me/905367602165" target="_blank" class="action-btn wa-btn">💬 WhatsApp</a>
          {% endif %}

          {% if item.file contains 'g' %}
            <a href="https://maps.app.goo.gl/HqSgYhS5v6eB2Zq19" target="_blank" class="action-btn">📍 Ikman Maps</a>
            <a href="https://www.instagram.com/galerieikman/" target="_blank" class="action-btn">📸 Instagram</a>
          {% endif %}

          {% if item.file contains 'a' %}
            <a href="https://maps.app.goo.gl/96uW6NfB9eK2Xq9A7" target="_blank" class="action-btn">📍 Museum</a>
          {% endif %}

          <!-- Eğer sadece sizin resminizse ve mağaza değilse müze konumu (sergi alanı) göster -->
          {% if item.file contains 'b' and item.file contains 'g' == false and item.file contains 'bilo' == false %}
            <a href="https://maps.app.goo.gl/96uW6NfB9eK2Xq9A7" target="_blank" class="action-btn">📍 View at Museum</a>
          {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<hr style="margin-top: 50px;">
<div style="text-align: center;">
  <a href="./gallery" style="font-weight: bold; color: #8b0000; text-decoration: none;">⬅️ Back to All Collections</a> | 
  <a href="./" style="font-weight: bold; color: #8b0000; text-decoration: none;">🏠 Home</a>
</div>