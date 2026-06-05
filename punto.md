---
layout: page
title: "Punto Carpet - Hüseyin Özer"
permalink: /punto/

photos:
  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101050.jpg"
    tag: "Punto Kapadokya"
    map: "https://www.google.com/maps/search/?api=1&query=Punto+Carpet+Cappadocia"
    text: "Punto Carpet'in Kapadokya Ortahisar'daki muazzam taş binası. Geleneksel mimariyle halı sanatının buluştuğu eşsiz bir merkez."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100752.jpg"
    tag: "Showroom"
    text: "Punto'nun geniş ve etkileyici galerisi. Yüzlerce el dokuması şaheser, her biri kendi yöresinin ve dokumacısının hikayesini taşıyor."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100851.jpg"
    tag: "Hüseyin Özer & Küratör"
    text: "Değerli Hüseyin Özer ile birlikte nadide parçaların kalite, düğüm sıklığı ve desen analizi yapılırken."

  - file: "images/Punto/WhatsApp Image 2026-06-04 at 22.24.14 (3).jpeg"
    tag: "İpek Şaheser"
    text: "Muazzam bir işçiliğe sahip Saf İpek (Hereke kalitesinde) seccade. Mihrap ve Hayat Ağacı motiflerinin kusursuz bir yansıması."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 100929.jpg"
    tag: "Dokuma Tezgahı"
    text: "Geleneksel tezgahta ilmek ilmek dokunan bir sanat eseri. Kadın dokumacılarımızın emeği ve sabrının en güzel örneği."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101004.jpg"
    tag: "Atölye Detay"
    text: "Tezgah başındaki ustamızın maharetli ellerinden çıkan renkli ve sıkı düğümler."

  - file: "images/Punto/Ekran görüntüsü 2026-06-05 101129.png"
    tag: "Özel Tasarım"
    text: "Adeta bir tabloyu andıran, ince detaylarıyla dikkat çeken çok özel dokuma Kartal motifi."
---

<style>
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

<div class="photo-grid">
  {% for photo in page.photos %}
  <div class="photo-card">
    <img src="{{ site.baseurl }}/{{ photo.file }}" alt="{{ photo.tag }}">
    <div class="photo-info">
      <span class="photo-tag">{{ photo.tag }}</span>
      <p class="photo-text">{{ photo.text }}</p>
      <div class="photo-links">
        {% if photo.map and photo.map != 'none' %}
          <a href="{{ photo.map }}" target="_blank" class="social-btn btn-map">📍 Harita</a>
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
