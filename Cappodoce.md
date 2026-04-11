<!-- SECTION: THE CURATOR'S ROOTS -->
<h2 style="color: #8b0000;">🏠 My Cappadocia: The Triad of My Life</h2>

<table border="0" style="width:100%; background-color: #fdf5e6; border-radius: 15px; padding: 20px; border-collapse: collapse;">
  <tr>
    <!-- SOL SÜTUN: KİŞİSEL HİKAYE -->
    <td style="width: 50%; vertical-align: top; padding-right: 20px;">
      <p>Cappadocia is not just a destination for me; it is my timeline. As you can see on the map, my life follows the path of the <strong>Kızılırmak (Red River)</strong>.</p>
      
      <ul style="line-height: 1.8;">
        <li><strong>Bayramhacı (The Source):</strong> My birthplace. Located by the dam, it's famous for its thermal springs. This is where I learned the value of nature and healing waters.</li>
        <li><strong>Avanos (The Mold):</strong> Where I grew up. The river's red clay shaped my childhood. It's the center of pottery and traditional Turkish handicrafts.</li>
        <li><strong>Göreme (The Heart):</strong> My current home and professional center. The pinnacle of rock-cut history where I now guide visitors as a local expert.</li>
      </ul>
      <p><i>This map shows the 40km circle where I have spent my life, learning every valley and every knot of our culture.</i></p>
    </td>
---
layout: default
title: Global Cappadocia Guide - Polyglot Edition
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
    #map { height: 600px; width: 100%; border-radius: 15px; border: 3px solid #8b0000; box-shadow: 0 10px 30px rgba(0,0,0,0.2); }
    .lang-box { text-align: center; margin: 20px 0; display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
    .lang-btn { padding: 8px 15px; cursor: pointer; border-radius: 50px; border: 1.5px solid #8b0000; background: white; font-weight: bold; font-size: 13px; transition: 0.3s; }
    .lang-btn.active { background: #8b0000; color: white; }
    
    .info-card { background: #fff; padding: 25px; border-radius: 15px; border-top: 10px solid #8b0000; margin-top: 20px; box-shadow: 0 5px 20px rgba(0,0,0,0.15); min-height: 350px; position: relative; }
    .info-section { margin-bottom: 12px; padding-bottom: 8px; border-bottom: 1px dashed #ddd; }
    .info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 11px; display: block; }
    .whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 10px 20px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 10px; }
    #place-name { margin-top: 0; color: #8b0000; font-family: 'Georgia', serif; }
</style>

<div style="text-align: center; font-family: 'Georgia', serif; padding: 10px;">
    <h1 style="color: #8b0000;">🏺 Cappadocia Master Polyglot Guide</h1>
    <p><i>Insider Tips, VIP Contacts & Interactive Map</i></p>
</div>

<!-- ÇOK DİLLİ SEÇİCİ -->
<div class="lang-box">
    <button id="en-btn" class="lang-btn active" onclick="setLang('en')">🇺🇸 English</button>
    <button id="fr-btn" class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button>
    <button id="es-btn" class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button>
    <button id="it-btn" class="lang-btn" onclick="setLang('it')">🇮🇹 Italiano</button>
    <button id="ru-btn" class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button>
    <button id="zh-btn" class="lang-btn" onclick="setLang('zh')">🇨🇳 中文</button>
    <button id="ja-btn" class="lang-btn" onclick="setLang('ja')">🇯🇵 日本語</button>
</div>

<div id="map"></div>

<div id="info-card" class="info-card">
    <div id="default-msg">
        <h3 style="text-align:center; color:#8b0000;">📍 Select a Location or VIP Expert</h3>
        <p style="text-align:center;">Click markers for history, shops, and direct WhatsApp contacts.</p>
    </div>
    
    <div id="content-area" style="display:none;">
        <h2 id="place-name"></h2>
        
        <div class="info-section">
            <span class="info-label" id="label-worth">Expert Recommendation</span>
            <p id="worth-text" style="font-weight: bold; margin: 5px 0;"></p>
        </div>

        <div class="info-section">
            <span class="info-label" id="label-see">Description</span>
            <p id="see-text" style="margin: 5px 0;"></p>
        </div>

        <div id="contact-section" class="info-section" style="display:none; background: #f0fff4; padding: 10px; border-radius: 10px;">
            <span class="info-label">📱 Direct Contact</span>
            <p id="contact-name" style="margin: 5px 0; font-weight: bold;"></p>
            <a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 Chat on WhatsApp</a>
        </div>

        <div class="info-section" style="border-bottom:none;">
            <span class="info-label" id="label-secret">Insider Note</span>
            <p id="do-text" style="margin: 5px 0; font-style: italic;"></p>
        </div>
    </div>
</div>

<script>
var map = L.map('map').setView([38.65, 34.85], 11);
var currentLang = 'en';
var activePoint = null;

L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

// LOKASYON VERİLERİ (Genişletilmiş ve Çok Dilli)
var locations = [
    {
        coords: [38.642, 34.829],
        id: "kervan",
        wa: "905367602165",
        en: { n: "KERVAN CARPET (Bülent Güler)", w: "Highly Recommended for Shopping", s: "Located in Goreme. Fine selection of hand-knotted carpets.", d: "Ask for Bülent. He is a true gentleman of the craft." },
        fr: { n: "KERVAN CARPET (Bülent Güler)", w: "Hautement recommandé", s: "Situé à Göreme. Fine sélection de tapis noués à la main.", d: "Demandez Bülent. Un vrai maître de l'art." },
        es: { n: "ALFOMBRAS KERVAN", w: "Muy recomendado", s: "Ubicado en Goreme. Gran selección de alfombras.", d: "Pregunta por Bülent." },
        it: { n: "KERVAN CARPET", w: "Altamente raccomandato", s: "Selezione di tappeti fatti a mano.", d: "Chiedi di Bülent." },
        ru: { n: "КЕРВАН КОВРЫ", w: "Рекомендуется", s: "Лучший выбор ковров в Гёреме.", d: "Спросите Бюлента." },
        zh: { n: "KERVAN 地毯", w: "强烈推荐", s: "位于格雷梅，精选手工毯。", d: "找 Bülent。" },
        ja: { n: "KERVAN 絨毯", w: "強くお勧めします", s: "ギョレメにある手織り絨毯店。", d: "Bülentさんを訪ねてください。" }
    },
    {
        coords: [38.621, 34.856],
        id: "punto",
        wa: "905324970321",
        en: { n: "PUNTO ANTIQUE CARPETS (Hüseyin Özer)", w: "VIP Antique Collection", s: "Located in Ortahisar. Specialist in old and rare textile collections.", d: "Ask for Hüseyin Özer for professional antique analysis." },
        fr: { n: "PUNTO TAPIS ANTIQUES", w: "Collection VIP Antique", s: "Situé à Ortahisar. Spécialiste des collections textiles rares.", d: "Demandez Hüseyin Özer." },
        es: { n: "PUNTO ALFOMBRAS ANTIGUAS", w: "Colección VIP", s: "Ortahisar. Especialista en piezas raras.", d: "Hüseyin Özer." },
        it: { n: "PUNTO TAPPETI ANTICHI", w: "Collezione Antica VIP", s: "Specialista in tessuti rari.", d: "Chiedi di Hüseyin Özer." },
        ru: { n: "ПУНТО АНТИКВАРНЫЕ КОВРЫ", w: "VIP Коллекция", s: "Ортахисар. Редкие ковры.", d: "Хюсейн Озер." },
        zh: { n: "PUNTO 古董地毯", w: "VIP古董收藏", s: "位于奥塔希萨尔，稀有收藏。", d: "找 Hüseyin Özer。" },
        ja: { n: "PUNTO アンティーク絨毯", w: "VIPアンティーク", s: "希少なアンティーク絨毯の専門店。", d: "Hüseyin Özerさんまで。" }
    },
    {
        coords: [38.645, 34.831],
        id: "ikman",
        en: { n: "IKMAN CARPET (Photography)", w: "The #1 Instagram Spot", s: "Famous for traditional carpet photography setups.", d: "A colorful paradise for photographers." },
        fr: { n: "TAPIS IKMAN (Photographie)", w: "Le spot Instagram n°1", s: "Célèbre pour les séances photo traditionnelles.", d: "Paradis pour photographes." },
        es: { n: "ALFOMBRAS IKMAN (Fotos)", w: "Punto Instagram", s: "Famoso por sus fotos con alfombras.", d: "Paraíso fotográfico." },
        it: { n: "IKMAN CARPET (Foto)", w: "Spot Instagram", s: "Famoso per set fotografici.", d: "Paradiso dei fotografi." },
        ru: { n: "ИКМАН КОВРЫ (Фото)", w: "Инстаграм спот", s: "Знаменитое место для фотосессий.", d: "Рай для фотографов." },
        zh: { n: "IKMAN 地毯 (摄影)", w: "顶级网红打卡点", s: "传统地毯背景摄影。", d: "摄影师的天堂。" },
        ja: { n: "IKMAN 絨毯 (写真)", w: "インスタ映えスポット", s: "絨毯に囲まれた有名な写真スポット。", d: "フォトグラファーのパラダイス。" }
    },
    {
        coords: [38.641, 34.832],
        id: "museum",
        en: { n: "ANATOLIAN ART MUSEUM", w: "Cultural Landmark", s: "Museum dedicated to the history of Anatolian weaving and arts.", d: "A must-visit for academic understanding of the art." },
        fr: { n: "MUSÉE D'ART ANATOLIEN", w: "Repère culturel", s: "Musée dédié à l'histoire du tissage anatolien.", d: "Indispensable pour la culture académique." },
        es: { n: "MUSEO DE ARTE ANATOLIO", w: "Hito cultural", s: "Dedicado a la historia del tejido.", d: "Visita obligatoria." },
        it: { n: "MUSEO D'ARTE ANATOLICA", w: "Punto culturale", s: "Dedicato alla storia della tessitura.", d: "Visita accademica." },
        ru: { n: "МУЗЕЙ АНАТОЛИЙСКОГО ИСКУССТВА", w: "Культурный центр", s: "История анатолийского ткачества.", d: "Обязательно к посещению." },
        zh: { n: "安纳托利亚艺术博物馆", w: "文化地标", s: "致力于安纳托利亚编织历史。", d: "学术了解艺术必看。" },
        ja: { n: "アナトリア芸術博物館", w: "文化遺産", s: "アナトリアの織物歴史博物館。", d: "芸術を学ぶなら必見。" }
    },
    {
        coords: [38.640, 34.825],
        id: "halil",
        wa: "905322478674",
        en: { n: "VIP GUIDE: HALİL KÖKSAL", w: "Expert Language Guide", s: "Specialist in French & Spanish languages. Deep historical knowledge.", d: "Book Halil for a high-quality, professional cultural tour." },
        fr: { n: "GUIDE VIP : HALİL KÖKSAL", w: "Expert Conférencier", s: "Spécialiste en Français et Espagnol.", d: "Réservez Halil pour une visite culturelle de haute qualité." },
        es: { n: "GUÍA VIP: HALİL KÖKSAL", w: "Guía Experto", s: "Especialista en Francés y Español.", d: "Reserva a Halil para un tour profesional." },
        it: { n: "GUIDA VIP: HALİL KÖKSAL", w: "Guida Esperta", s: "Parla Francese e Spagnolo.", d: "Prenota Halil per tour professionali." },
        ru: { n: "VIP ГИД: ХАЛИЛ КЁКСАЛ", w: "Профессиональный гид", s: "Специалист по истории на французском и испанском.", d: "Закажите Халила для тура высшего класса." },
        zh: { n: "VIP 导游: HALİL KÖKSAL", w: "专家语言导游", s: "精通法语和西班牙语，深厚的历史知识。", d: "预订 Halil 提供高质量文化之旅。" },
        ja: { n: "VIPガイド: HALİL KÖKSAL", w: "公認ガイド", s: "フランス語とスペイン語のエキスパート。", d: "プロの文化ツアーならHalilさんを。" }
    }
];

var labels = {
    en: { worth: "Expert Recommendation", see: "Description", secret: "Insider Note" },
    fr: { worth: "Recommandation d'expert", see: "Description", secret: "Note locale" },
    es: { worth: "Recomendación experta", see: "Descripción", secret: "Nota interna" },
    it: { worth: "Raccomandazione", see: "Descrizione", secret: "Nota locale" },
    ru: { worth: "Рекомендация", see: "Описание", secret: "Заметка" },
    zh: { worth: "专家推荐", see: "描述", secret: "业内提示" },
    ja: { worth: "専門家の推奨", see: "説明", secret: "インサイダーノート" }
};

locations.forEach(function(loc) {
    var marker = L.marker(loc.coords).addTo(map);
    marker.on('click', function() {
        activePoint = loc;
        updateUI();
    });
});

function updateUI() {
    if(!activePoint) return;
    document.getElementById('default-msg').style.display = 'none';
    document.getElementById('content-area').style.display = 'block';
    
    var d = activePoint[currentLang];
    var l = labels[currentLang];
    
    document.getElementById('place-name').innerText = d.n;
    document.getElementById('worth-text').innerText = d.w;
    document.getElementById('see-text').innerText = d.s;
    document.getElementById('do-text').innerText = d.d;
    
    document.getElementById('label-worth').innerText = l.worth;
    document.getElementById('label-see').innerText = l.see;
    document.getElementById('label-secret').innerText = l.secret;
    
    if(activePoint.wa) {
        document.getElementById('contact-section').style.display = 'block';
        document.getElementById('contact-name').innerText = d.n;
        document.getElementById('wa-link').href = "https://wa.me/" + activePoint.wa;
    } else {
        document.getElementById('contact-section').style.display = 'none';
    }
}

function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(lang + '-btn').classList.add('active');
    updateUI();
}
</script>

<hr>

### 📱 Professional Contacts (Direct Access)
- **Bülent Güler (Goreme - Kervan):** [Chat via WhatsApp](https://wa.me/905367602165)
- **Hüseyin Özer (Ortahisar - Punto):** [Chat via WhatsApp](https://wa.me/905324970321)
- **Halil Koksal (Guide - FR/ES):** [Chat via WhatsApp](https://wa.me/905322478674)

---
[Return to Dashboard](../)
    <!-- SAĞ SÜTUN: HARİTA GÖRSELİ -->
    <td style="width: 50%; text-align: center; vertical-align: middle;">
      <a href="./ben_.jpg" target="_blank" title="Click to enlarge my life map">
        <img src="./ben_.jpg" alt="Fatih's Cappadocia Map" style="width: 100%; border-radius: 10px; border: 2px solid #d4af37; box-shadow: 0 8px 15px rgba(0,0,0,0.2); cursor: zoom-in;">
      </a>
      <br>
      <small style="color: #666;">(Click map to see full details of my region)</small>
    </td>
  </tr>
</table>

<hr style="margin: 40px 0;">
---
layout: default
title: Cappadocia Map
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<div style="text-align: center; padding: 20px;">
    <h2 style="color: #8b0000;">Cappadocia Interactive Map</h2>
    <p>Click on the pins to see details in English and French.</p>
</div>



<!-- SECTION 1: LOGISTICS & DISTANCES -->
<h2 style="color: #1a2a6c;">✈️ Getting Here & Around</h2>
<p>Göreme is the "center of the puzzle." Here is how you reach us and the distances you need to know:</p>

<table border="1" style="width:100%; border-collapse: collapse; text-align: left; border-color: #eee;">
  <tr style="background-color: #1a2a6c; color: white;">
    <th style="padding: 10px;">Destination</th>
    <th style="padding: 10px;">Distance from Göreme</th>
    <th style="padding: 10px;">Travel Time / Tip</th>
  </tr>
  <tr>
    <td style="padding: 10px;"><strong>Nevşehir Airport (NAV)</strong></td>
    <td style="padding: 10px;">~40 km</td>
    <td style="padding: 10px;">45 min. Best for domestic flights from Istanbul.</td>
  </tr>
  <tr>
    <td style="padding: 10px;"><strong>Kayseri Airport (ASR)</strong></td>
    <td style="padding: 10px;">~75 km</td>
    <td style="padding: 10px;">1 hour. More international connections.</td>
  </tr>
  <tr>
    <td style="padding: 10px;"><strong>Ürgüp Center</strong></td>
    <td style="padding: 10px;">~10 km</td>
    <td style="padding: 10px;">12 min. The hub for nightlife and wine tasting.</td>
  </tr>
  <tr>
    <td style="padding: 10px;"><strong>Avanos (My Town)</strong></td>
    <td style="padding: 10px;">~12 km</td>
    <td style="padding: 10px;">15 min. Famous for pottery and the Red River.</td>
  </tr>
  <tr>
    <td style="padding: 10px;"><strong>Mustafapaşa (Sinasos)</strong></td>
    <td style="padding: 10px;">~15 km</td>
    <td style="padding: 10px;">20 min. An old Greek village with amazing architecture.</td>
  </tr>
</table>
<p><i>*Pro Tip: Always book an <b>Airport Shuttle</b> in advance. Taxis are very expensive for airport transfers.</i></p>

<hr>

<!-- SECTION 2: THE BALLOON BIBLE -->
<h2 style="color: #8b0000;">🎈 The Hot Air Balloon Bible</h2>
<p>The #1 question everyone asks. Let's be honest about how it works:</p>

<table border="0" style="width:100%; background-color: #fffaf0; border: 1px dashed #8b0000; padding: 20px; border-radius: 10px;">
  <tr>
    <td>
      <h3>Why do prices change daily?</h3>
      <p>Think of it like a stock market. Prices depend on: 
      1. Seasonality (May-Oct is peak). 
      2. The "Backlog" (If flights were canceled for 3 days, the 4th day will be very expensive because everyone is waiting).</p>
      
      <h3>The "Flag" System (Red/Yellow/Green)</h3>
      <p>The <strong>SHGM (Civil Aviation Authority)</strong> decides if we fly. 
      - 🟢 <b>Green:</b> We fly! 
      - 🟡 <b>Yellow:</b> Delay/Standby. 
      - 🔴 <b>Red:</b> Canceled. If it's red, no one flies. No exceptions for money or luck.</p>
      
      <h3>Refunds?</h3>
      <p>If the flight is canceled by SHGM, you get a <b>100% full refund</b>. No cancellation fee. Period.</p>
    </td>
  </tr>
</table>

<hr>

<!-- SECTION 3: LOCAL CITIES & VILLAGES -->
<h2 style="color: #2e8b57;">🏘️ Towns You Must Visit</h2>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-top: 20px;">
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #d4af37;">
    <h4>🌟 Ürgüp</h4>
    <p>The "sophisticated" Cappadocia. Great for dining, high-end boutique hotels, and seeing the "Three Beauties" fairy chimneys.</p>
  </div>
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #2e8b57;">
    <h4>🎨 Avanos</h4>
    <p>My childhood home. Crossed by the Red River. You must try the pottery wheel and walk across the swinging bridge.</p>
  </div>
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #8b0000;">
    <h4>⛪ Mustafapaşa</h4>
    <p>A hidden historical treasure. Formerly known as Sinasos, it holds the best examples of 19th-century Greek masonry.</p>
  </div>
</div>

<hr>
<hr style="margin: 40px 0;">

<!-- SECTION: COMPREHENSIVE CULTURAL MAP -->
<div style="text-align: center; background-color: #fffaf0; padding: 30px; border-radius: 20px; border: 1px solid #d4af37;">
  <h2 style="color: #8b0000; margin-top: 0;">🗺️ Cappadocia: Cultural & Activity Roadmap</h2>
  <p style="font-size: 16px; color: #555; max-width: 800px; margin: 10px auto 25px auto;">
    This illustrative map highlights the essential "Cultural Nodes" of our region. From the pottery wheels of <b>Avanos</b> to the underground mysteries of <b>Derinkuyu</b>, every icon represents a thousand-year-old tradition.
  </p>

  <!-- Haritaya tıklandığında tam boyutta yeni sekmede açılır -->
  <a href="./map_.jpg" target="_blank" title="Click to view full-size cultural map">
    <img src="./map_.jpg" alt="Cappadocia Cultural Map" style="width: 100%; max-width: 900px; border-radius: 15px; box-shadow: 0 12px 25px rgba(0,0,0,0.25); cursor: zoom-in;" loading="lazy">
  </a>

  <div style="margin-top: 20px; display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">🏺 <b>Artisan Workshops</b></span>
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">⛪ <b>Historical Sites</b></span>
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">🐎 <b>Outdoor Adventure</b></span>
  </div>
  
  <p style="margin-top: 15px; font-size: 13px; color: #8b0000;">
    <strong>💡 Insider Tip:</strong> Click on the map to enlarge and see the specific locations of carpet workshops and secret valleys.
  </p>
</div>

<hr style="margin: 40px 0;">
<!-- SECTION 4: MUSEUMS & HIDDEN GEMS -->
<h2 style="color: #d4af37;">🏛️ Museums & Valleys</h2>
<ul>
  <li><strong>Göreme Open Air Museum:</strong> The mandatory stop for rock-cut churches and frescoes.</li>
  <li><strong>Zelve Open Air Museum:</strong> Much larger and more "wild" than Göreme. Great for hiking without huge crowds.</li>
  <li><strong>Bayramhacı (Curator's Choice):</strong> My birthplace. If you want a break from rocks, come here for the natural hot springs and thermal healing.</li>
  <li><strong>Ihlara Valley:</strong> A 14km hike through a lush canyon with 100+ churches.</li>
</ul>

<hr>

<!-- SECTION 5: ADVENTURE -->
<h2 style="color: #e67e22;">🐎 Adventure Tours</h2>
<p>If you have extra time, try these:</p>
<table border="0" style="width:100%;">
  <tr>
    <td style="width: 50%; padding: 10px;">
      <b>Horseback Riding:</b> Cappadocia means "Land of Beautiful Horses." Sunset tours in the valleys are magic.
    </td>
    <td style="width: 50%; padding: 10px;">
      <b>ATV / Quad Safari:</b> Best for the "Sword Valley" and "Love Valley" trails if you like adrenaline and dust!
    </td>
  </tr>
</table>

<hr>

<div style="text-align: center; background-color: #2c3e50; color: white; padding: 20px; border-radius: 10px;">
  <h3>Need more local advice?</h3>
  <p>As a local active in Göreme, I'm here to help you understand the true culture behind the fairy chimneys.</p>
  <a href="./me" style="color: #d4af37; font-weight: bold;">Learn more about me & my French courses</a>
</div>

<p style="text-align: center; margin-top: 30px;">
  <a href="./">🏠 Return to Main Dashboard</a> | <a href="./en/handknotted">🧶 Technical Carpet Guide</a>
</p>
