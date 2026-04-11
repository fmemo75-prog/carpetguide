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

<!-- Leaflet CSS & JS -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
    /* Genel Sayfa Tasarımı */
    #map { height: 600px; width: 100%; border-radius: 15px; border: 3px solid #8b0000; box-shadow: 0 10px 30px rgba(0,0,0,0.2); }
    .lang-box { text-align: center; margin: 20px 0; display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
    .lang-btn { padding: 8px 15px; cursor: pointer; border-radius: 50px; border: 1.5px solid #8b0000; background: white; font-weight: bold; font-size: 13px; transition: 0.3s; }
    .lang-btn.active { background: #8b0000; color: white; }
    
    /* MODAL (Açılır Pencere) STİLLERİ */
    .modal {
        display: none; 
        position: fixed; 
        z-index: 10000; 
        left: 0; top: 0;
        width: 100%; height: 100%;
        background-color: rgba(0,0,0,0.7); 
        backdrop-filter: blur(5px);
    }
    .modal-content {
        background-color: #fff;
        margin: 10% auto;
        padding: 0;
        border-radius: 20px;
        width: 90%;
        max-width: 600px;
        position: relative;
        box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        border-top: 10px solid #8b0000;
        animation: slideIn 0.3s ease-out;
        overflow: hidden;
    }
    @keyframes slideIn {
        from { transform: translateY(50px); opacity: 0; }
        to { transform: translateY(0); opacity: 1; }
    }
    .modal-header { padding: 20px; background: #fff; border-bottom: 1px solid #eee; }
    .modal-body { padding: 25px; max-height: 70vh; overflow-y: auto; }
    .close-btn {
        position: absolute;
        right: 20px;
        top: 15px;
        font-size: 30px;
        font-weight: bold;
        color: #8b0000;
        cursor: pointer;
        z-index: 10;
    }

    /* Bilgi Kartı İçeriği */
    .info-section { margin-bottom: 15px; padding-bottom: 10px; border-bottom: 1px dashed #ddd; }
    .info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 11px; display: block; }
    .whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 12px 25px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 10px; width: 100%; text-align: center; box-sizing: border-box; }
    #place-name { margin: 0; color: #8b0000; font-family: 'Georgia', serif; font-size: 24px; }
</style>

<div style="text-align: center; font-family: 'Georgia', serif; padding: 10px;">
    <h1 style="color: #8b0000;">🏺 Cappadocia Master Polyglot Guide</h1>
    <p><i>Insider Tips, VIP Contacts & Interactive Map</i></p>
</div>

<!-- DİL SEÇİCİ -->
<div class="lang-box">
    <button id="en-btn" class="lang-btn active" onclick="setLang('en')">🇺🇸 English</button>
    <button id="fr-btn" class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button>
    <button id="es-btn" class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button>
    <button id="it-btn" class="lang-btn" onclick="setLang('it')">🇮🇹 Italiano</button>
    <button id="ru-btn" class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button>
    <button id="zh-btn" class="lang-btn" onclick="setLang('zh')">🇨🇳 中文</button>
    <button id="ja-btn" class="lang-btn" onclick="setLang('ja')">🇯🇵 日本語</button>
</div>

<!-- HARİTA -->
<div id="map"></div>

<p style="text-align:center; color:#666; font-style: italic; margin-top: 10px;">📍 Click markers to see details and VIP contacts.</p>

<!-- MODAL BİLGİ PENCERESİ -->
<div id="infoModal" class="modal">
    <div class="modal-content">
        <span class="close-btn" onclick="closeModal()">&times;</span>
        <div class="modal-header">
            <h2 id="place-name"></h2>
        </div>
        <div class="modal-body">
            <div class="info-section">
                <span class="info-label" id="label-worth">Recommendation</span>
                <p id="worth-text" style="font-weight: bold; margin: 5px 0; color: #333;"></p>
            </div>

            <div class="info-section">
                <span class="info-label" id="label-see">Description</span>
                <p id="see-text" style="margin: 5px 0; line-height: 1.5;"></p>
            </div>

            <div id="contact-section" class="info-section" style="display:none; background: #f0fff4; padding: 15px; border-radius: 10px; border: 1px solid #25D366;">
                <span class="info-label">📱 Direct Contact</span>
                <p id="contact-name" style="margin: 5px 0; font-weight: bold;"></p>
                <a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 Chat on WhatsApp</a>
            </div>

            <div class="info-section" style="border-bottom:none;">
                <span class="info-label" id="label-secret">Insider Note</span>
                <p id="do-text" style="margin: 5px 0; font-style: italic; color: #555;"></p>
            </div>
        </div>
    </div>
</div>

<script>
var map = L.map('map').setView([38.65, 34.85], 11);
var currentLang = 'en';
var activePoint = null;

L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

// LOKASYON VERİLERİ
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
    },
    {
        coords: [38.6431, 34.8619],
        id: "goreme_oam",
        en: { n: "GÖREME OPEN AIR MUSEUM", w: "UNESCO World Heritage Site", s: "A complex of Byzantine-era rock-cut churches decorated with stunning frescoes. Dates back to the 10th century.", d: "Arrive before 9 AM to avoid crowds. Dark Church is a must-see." },
        fr: { n: "MUSÉE EN PLEIN AIR DE GÖREME", w: "Site UNESCO", s: "Églises rupestres byzantines avec fresques du Xe siècle.", d: "Arrivez avant 9h. L'Église Sombre est incontournable." },
        es: { n: "MUSEO AL AIRE LIBRE DE GÖREME", w: "Patrimonio UNESCO", s: "Iglesias bizantinas talladas en roca con frescos impresionantes.", d: "Llega antes de las 9 AM." },
        it: { n: "MUSEO ALL'APERTO DI GÖREME", w: "Patrimonio UNESCO", s: "Chiese rupestri bizantine con affreschi del X secolo.", d: "Arriva prima delle 9 per evitare la folla." },
        ru: { n: "МУЗЕЙ ГЁРЕМЕ", w: "ЮНЕСКО", s: "Византийские скальные церкви с фресками X века.", d: "Приходите до 9 утра." },
        zh: { n: "戈莱梅露天博物馆", w: "世界遗产", s: "10世纪的拜占庭岩石教堂群。", d: "建议9点前到达。" },
        ja: { n: "ギョレメ野外博物館", w: "世界遺産", s: "10世紀のビザンチン岩窟教会群。", d: "午前9時前がおすすめ。" }
    },
    {
        coords: [38.6289, 34.8053],
        id: "uchisar",
        en: { n: "UCHISAR CASTLE", w: "Highest Panoramic Point", s: "Ancient citadel carved into volcanic rock with 360° views.", d: "Best at sunset for the golden glow over the valley." },
        fr: { n: "CHÂTEAU D'UÇHISAR", w: "Point de vue panoramique", s: "Citadelle taillée dans le roc, vue à 360°.", d: "Sublime au coucher du soleil." },
        es: { n: "CASTILLO DE UÇHISAR", w: "Punto más alto", s: "Ciudadela tallada en roca volcánica.", d: "Mejor al atardecer." },
        it: { n: "CASTELLO DI UÇHISAR", w: "Punto panoramico più alto", s: "Cittadella scavata nella roccia.", d: "Bellissimo al tramonto." },
        ru: { n: "ЗАМОК УЧИСАР", w: "Высшая точка", s: "Крепость в скале с панорамным видом.", d: "Лучшее место для заката." },
        zh: { n: "乌奇萨尔城堡", w: "最高全景点", s: "火山岩中的古老堡垒。", d: "日落时分景色最美。" },
        ja: { n: "ユチヒサール城塞", w: "最高展望地点", s: "火山岩の要塞。360度の絶景。", d: "夕日の時間がベスト。" }
    },
    {
        coords: [38.3736, 34.7344],
        id: "derinkuyu",
        en: { n: "DERINKUYU UNDERGROUND CITY", w: "Deepest Underground City", s: "Multi-level subterranean city 85m deep. Once sheltered 20,000 people.", d: "Wear comfortable shoes; some passages are narrow." },
        fr: { n: "VILLE SOUTERRAINE DE DERINKUYU", w: "Plus profonde au monde", s: "Ville souterraine de 85m de profondeur.", d: "Déconseillé aux claustrophobes." },
        es: { n: "CIUDAD SUBTERRÁNEA DE DERINKUYU", w: "La más profunda", s: "Ciudad de 85 metros de profundidad.", d: "Pasadizos estrechos." },
        it: { n: "CITTÀ SOTTERRANEA DI DERINKUYU", w: "La più profonda", s: "Città sotterranea a 85 metri di profondità.", d: "Sconsigliata ai claustrofobici." },
        ru: { n: "ДЕРИНКУЮ", w: "Самый глубокий город", s: "Подземный город глубиной 85 метров.", d: "Не для клаустрофобов." },
        zh: { n: "德林库尤地下城", w: "世界最深地下城", s: "深达85米的地下迷宫。", d: "通道狭窄，注意安全。" },
        ja: { n: "デリンクユ地下都市", w: "世界最深の地下都市", s: "深さ85メートルの地下都市。", d: "狭い通路が多いので注意。" }
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

// İşaretçileri Haritaya Ekle
locations.forEach(function(loc) {
    var marker = L.marker(loc.coords).addTo(map);
    marker.on('click', function() {
        activePoint = loc;
        updateUI();
    });
});

function updateUI() {
    if(!activePoint) return;
    
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

    // MODALI AÇ
    document.getElementById('infoModal').style.display = "block";
}

function closeModal() {
    document.getElementById('infoModal').style.display = "none";
}

// Modal dışına tıklandığında kapat
window.onclick = function(event) {
    var modal = document.getElementById('infoModal');
    if (event.target == modal) {
        modal.style.display = "none";
    }
}

function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(lang + '-btn').classList.add('active');
    if (document.getElementById('infoModal').style.display === "block") {
        updateUI();
    }
}
</script>

<hr>

### 📱 Quick Access Contacts
- **Bülent Güler (Carpets):** [WhatsApp](https://wa.me/905367602165)
- **Hüseyin Özer (Antiques):** [WhatsApp](https://wa.me/905324970321)
- **Halil Koksal (Guide):** [WhatsApp](https://wa.me/905322478674)

---
[Return to Dashboard](../)

### 📱 Professional Contacts (Direct Access)
- **Bülent Güler (Goreme - Kervan):** [Chat via WhatsApp](https://wa.me/905367602165)
- **Hüseyin Özer (Ortahisar - Punto):** [Chat via WhatsApp](https://wa.me/905324970321)
- **Halil Koksal (Guide - FR/ES):** [Chat via WhatsApp](https://wa.me/905322478674)

---
[Return to Dashboard](../)



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
