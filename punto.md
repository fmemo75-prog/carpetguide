\---

layout: page

title: "Punto Carpet - Hüseyin Özer"

permalink: /punto/



photos:

&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 101050.jpg"

&#x20;   tag: "Punto Kapadokya"

&#x20;   map: "https://www.google.com/maps/search/?api=1\&query=Punto+Carpet+Cappadocia"

&#x20;   text: "Punto Carpet'in Kapadokya Ortahisar'daki muazzam taş binası. Geleneksel mimariyle halı sanatının buluştuğu eşsiz bir merkez."



&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 100752.jpg"

&#x20;   tag: "Showroom"

&#x20;   text: "Punto'nun geniş ve etkileyici galerisi. Yüzlerce el dokuması şaheser, her biri kendi yöresinin ve dokumacısının hikayesini taşıyor."



&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 100851.jpg"

&#x20;   tag: "Hüseyin Özer \& Küratör"

&#x20;   text: "Değerli Hüseyin Özer ile birlikte nadide parçaların kalite, düğüm sıklığı ve desen analizi yapılırken."



&#x20; - file: "images/Punto/WhatsApp Image 2026-06-04 at 22.24.14 (3).jpeg"

&#x20;   tag: "İpek Şaheser"

&#x20;   text: "Muazzam bir işçiliğe sahip Saf İpek (Hereke kalitesinde) seccade. Mihrap ve Hayat Ağacı motiflerinin kusursuz bir yansıması."



&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 100929.jpg"

&#x20;   tag: "Dokuma Tezgahı"

&#x20;   text: "Geleneksel tezgahta ilmek ilmek dokunan bir sanat eseri. Kadın dokumacılarımızın emeği ve sabrının en güzel örneği."



&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 101004.jpg"

&#x20;   tag: "Atölye Detay"

&#x20;   text: "Tezgah başındaki ustamızın maharetli ellerinden çıkan renkli ve sıkı düğümler."



&#x20; - file: "images/Punto/Ekran görüntüsü 2026-06-05 101129.png"

&#x20;   tag: "Özel Tasarım"

&#x20;   text: "Adeta bir tabloyu andıran, ince detaylarıyla dikkat çeken çok özel dokuma Kartal motifi."

\---



<style>

&#x20; .photo-grid {

&#x20;   display: grid;

&#x20;   grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));

&#x20;   gap: 20px;

&#x20;   margin-top: 20px;

&#x20; }

&#x20; .photo-card {

&#x20;   border: 1px solid #ddd;

&#x20;   border-radius: 8px;

&#x20;   overflow: hidden;

&#x20;   box-shadow: 0 4px 8px rgba(0,0,0,0.1);

&#x20;   background: #fff;

&#x20; }

&#x20; .photo-card img {

&#x20;   width: 100%;

&#x20;   height: 300px;

&#x20;   object-fit: cover;

&#x20;   display: block;

&#x20; }

&#x20; .photo-info {

&#x20;   padding: 15px;

&#x20; }

&#x20; .photo-tag {

&#x20;   display: inline-block;

&#x20;   background: #b45309; /\* Punto için prestijli Altın/Bakır tonu \*/

&#x20;   color: white;

&#x20;   padding: 3px 8px;

&#x20;   border-radius: 4px;

&#x20;   font-size: 0.8em;

&#x20;   font-weight: bold;

&#x20;   margin-bottom: 10px;

&#x20; }

&#x20; .photo-text {

&#x20;   font-size: 0.95em;

&#x20;   color: #333;

&#x20;   margin-bottom: 15px;

&#x20;   line-height: 1.4;

&#x20; }

&#x20; .photo-links {

&#x20;   display: flex;

&#x20;   gap: 10px;

&#x20;   flex-wrap: wrap;

&#x20; }

&#x20; .social-btn {

&#x20;   text-decoration: none !important;

&#x20;   padding: 6px 12px;

&#x20;   border-radius: 4px;

&#x20;   font-size: 0.85em;

&#x20;   color: white !important;

&#x20;   font-weight: bold;

&#x20;   display: flex;

&#x20;   align-items: center;

&#x20;   gap: 5px;

&#x20; }

&#x20; .btn-ig { background: #E1306C; }

&#x20; .btn-wa { background: #25D366; }

&#x20; .btn-map { background: #4285F4; }

</style>



<div class="photo-grid">

&#x20; {% for photo in page.photos %}

&#x20; <div class="photo-card">

&#x20;   <img src="{{ site.baseurl }}/{{ photo.file }}" alt="{{ photo.tag }}">

&#x20;   <div class="photo-info">

&#x20;     <span class="photo-tag">{{ photo.tag }}</span>

&#x20;     <p class="photo-text">{{ photo.text }}</p>

&#x20;     <div class="photo-links">

&#x20;       {% if photo.map and photo.map != 'none' %}

&#x20;         <a href="{{ photo.map }}" target="\_blank" class="social-btn btn-map">📍 Harita</a>

&#x20;       {% endif %}

&#x20;       {% if photo.instagram %}

&#x20;         <a href="{{ photo.instagram }}" target="\_blank" class="social-btn btn-ig">📸 Instagram</a>

&#x20;       {% endif %}

&#x20;       {% if photo.whatsapp %}

&#x20;         <a href="https://wa.me/{{ photo.whatsapp }}" target="\_blank" class="social-btn btn-wa">🟢 WhatsApp</a>

&#x20;       {% endif %}

&#x20;     </div>

&#x20;   </div>

&#x20; </div>

&#x20; {% endfor %}

</div>

