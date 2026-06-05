---
layout: page
title: "Punto Carpet - Headmaster Hüseyin Özer"
permalink: /punto/

photos:
  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101050.jpg"
    tag: "Punto Cappadocia"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "Punto Carpet's magnificent stone building in Ortahisar, Cappadocia. A unique center where traditional architecture meets the art of carpet weaving."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100752.jpg"
    tag: "Showroom"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "Punto's vast and impressive gallery. Hundreds of hand-woven masterpieces, each carrying the story of its region and weaver."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100851.jpg"
    tag: "Headmaster & Curator"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "Analyzing the quality, knot density, and patterns of rare pieces with Headmaster <b>Hüseyin Özer</b>."

  - file: "images/Punto/WhatsApp Image 2026-06-04 at 22.24.14 (3).jpeg"
    tag: "Silk Masterpiece"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "A Pure Silk (Hereke quality) prayer rug with tremendous craftsmanship. A flawless reflection of the Mihrab and Tree of Life motifs."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100929.jpg"
    tag: "Traditional Loom"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "A work of art woven knot by knot on a traditional loom. A beautiful example of the labor and patience of our female weavers."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101004.jpg"
    tag: "Workshop Detail"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "Colorful and tight knots emerging from the skillful hands of our master at the loom."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101129.png"
    tag: "Special Design"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    whatsapp: "905324970321"
    text: "A very special woven Eagle motif that resembles a painting, drawing attention with its fine details."
---

<style>
  .intro-box {
    background-color: #fdf8f5;
    border-left: 5px solid #b45309;
    padding: 20px;
    margin-bottom: 30px;
    border-radius: 4px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.05);
  }
  .intro-box p {
    margin: 0;
    font-size: 1.1em;
    line-height: 1.6;
    color: #444;
  }
  .intro-box strong {
    color: #b45309;
    font-size: 1.2em;
    display: block;
    margin-bottom: 8px;
  }
  .photo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 20px;
  }
  .photo-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    background: #fff;
  }
  .photo-card img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    display: block;
  }
  .photo-info {
    padding: 15px;
  }
  .photo-tag {
    display: inline-block;
    background: #b45309;
    color: white;
    padding: 3px 8px;
    border-radius: 4px;
    font-size: 0.8em;
    font-weight: bold;
    margin-bottom: 10px;
  }
  .photo-text {
    font-size: 0.95em;
    color: #333;
    margin-bottom: 15px;
    line-height: 1.4;
  }
  .photo-links {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }
  .social-btn {
    text-decoration: none !important;
    padding: 6px 12px;
    border-radius: 4px;
    font-size: 0.85em;
    color: white !important;
    font-weight: bold;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  .btn-ig { background: #E1306C; }
  .btn-wa { background: #25D366; }
  .btn-map { background: #4285F4; }
</style>

<!-- BİLGİ NOTU KISMI -->
<div class="intro-box">
  <p>
    <strong>Welcome to Punto Carpet Cappadocia!</strong>
    Standing out in the region with its extensive collection of antique and vintage rugs, Punto offers a unique cultural experience. You can visit our gallery completely free of charge and learn about Turkish carpet weaving and culture in multiple languages from our experts. You are always welcome—just come, visit, and immerse yourself in this ancient art!
  </p>
</div>

<!-- FOTOĞRAF GALERİSİ -->
<div class="photo-grid">
  {% for photo in page.photos %}
  <div class="photo-card">
    <img src="{{ site.baseurl }}/{{ photo.file }}" alt="{{ photo.tag }}">
    <div class="photo-info">
      <span class="photo-tag">{{ photo.tag }}</span>
      <p class="photo-text">{{ photo.text }}</p>
      <div class="photo-links">
        {% if photo.map and photo.map != 'none' %}
          <a href="{{ photo.map }}" target="_blank" class="social-btn btn-map">📍 Map</a>
        {% endif %}
        {% if photo.instagram %}
          <a href="{{ photo.instagram }}" target="_blank" class="social-btn btn-ig">📸 Instagram</a>
        {% endif %}
        {% if photo.whatsapp %}
          <a href="https://wa.me/{{ photo.whatsapp }}" target="_blank" class="social-btn btn-wa">🟢 WhatsApp</a>
        {% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
</div>