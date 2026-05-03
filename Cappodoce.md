---
layout: default
title: Cappadocia Complete Guide — Fatih Mehmet Canıtez
---

<!-- 1. HARİTA KÜTÜPHANELERİ -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
/* ── GENEL STİLLER ── */
body { font-family: Georgia, serif; color: #333; }
h2.section-title { color: #8b0000; border-left: 5px solid #8b0000; padding-left: 14px; margin: 40px 0 16px; font-size: 20px; }
.lang-box { text-align: center; margin: 20px 0; display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; }
.lang-btn { padding: 8px 16px; cursor: pointer; border-radius: 50px; border: 1.5px solid #8b0000; background: white; font-weight: bold; font-size: 12px; transition: 0.2s; }
.lang-btn.active, .lang-btn:hover { background: #8b0000; color: white; }

/* ── HARİTA VE BİLGİ KARTI ── */
#map-wrapper { position: relative; margin-bottom: 20px; }
#map { height: 560px; width: 100%; border-radius: 14px; border: 3px solid #8b0000; box-shadow: 0 8px 24px rgba(0,0,0,0.15); z-index: 1; }
#info-card {
    display: none; position: absolute; top: 15px; right: 15px;
    width: 280px; max-height: 500px; overflow-y: auto;
    background: #fff; padding: 20px; border-radius: 12px;
    border-top: 8px solid #8b0000; box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    z-index: 1000;
}
#info-card.visible { display: block; }
.info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 10px; display: block; margin-top: 10px; }
.whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 8px 15px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 10px; font-size: 12px; }

/* ── VIP KARTLARI ── */
.vip-card { background: #fff; border-radius: 13px; border-top: 7px solid #8b0000; box-shadow: 0 4px 18px rgba(0,0,0,0.1); overflow: hidden; }
.vip-header { background: #8b0000; padding: 15px; color: white; }
.vip-person { padding: 15px; border-bottom: 1px solid #eee; }
.vip-name { font-weight: bold; color: #8b0000; margin: 0; }

/* ── MEKTUP VE DİĞER KUTULAR ── */
.personal-note { background: #fdfaf6; border-left: 5px solid #8b0000; padding: 30px; border-radius: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.05); }
.town-card, .museum-card { flex: 1; min-width: 220px; background: #f9f9f9; padding: 20px; border-radius: 10px; border-left: 4px solid #d4af37; }

@media (max-width: 768px) {
    #info-card { position: fixed; top: auto; bottom: 0; left: 0; right: 0; width: 100%; max-height: 40%; border-radius: 20px 20px 0 0; }
}
</style>

<div style="text-align:center; padding: 20px 0;">
    <h1 style="color:#8b0000;">🏺 Cappadocia Complete Guide</h1>
    <p style="color:#888;"><i>Insider Tips · VIP Contacts · Interactive Map · 7 Languages</i></p>
</div>

<!-- DİL SEÇİMİ -->
<div class="lang-box">
    <button id="en-btn" class="lang-btn active" onclick="setLang('en')">🇺🇸 English</button>
    <button id="fr-btn" class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button>
    <button id="es-btn" class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button>
    <button id="it-btn" class="lang-btn" onclick="setLang('it')">🇮🇹 Italiano</button>
    <button id="ru-btn" class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button>
    <button id="zh-btn" class="lang-btn" onclick="setLang('zh')">🇨🇳 中文</button>
    <button id="ja-btn" class="lang-btn" onclick="setLang('ja')">🇯🇵 日本語</button>
</div>

<h2 class="section-title">🗺️ Interactive Map & Trusted Contacts</h2>

<div style="display:flex; gap:20px; flex-wrap:wrap; align-items:flex-start;">
    <!-- HARİTA ALANI -->
    <div style="flex:1 1 60%; min-width:300px;">
        <div id="map-wrapper">
            <div id="map"></div>
            <div id="info-card">
                <button onclick="closePanel()" style="float:right; border:none; background:none; font-size:20px; cursor:pointer;">✕</button>
                <h3 id="place-name" style="color:#8b0000; margin-top:0;"></h3>
                <span class="info-label" id="label-worth">Recommendation</span>
                <p id="worth-text" style="font-weight:bold;"></p>
                <span class="info-label" id="label-see">Description</span>
                <p id="see-text"></p>
                <div id="contact-section" style="display:none;">
                    <span class="info-label">Contact</span>
                    <a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
                </div>
                <span class="info-label" id="label-secret">Insider Note</span>
                <p id="do-text" style="font-style:italic; font-size:13px;"></p>
            </div>
        </div>
    </div>

    <!-- VIP LİSTESİ -->
    <div style="flex:1 1 30%; min-width:250px;">
        <div class="vip-card">
            <div class="vip-header">⭐ Trusted VIP Contacts</div>
            <div class="vip-person">
                <p class="vip-name">Bülent Güler</p>
                <p style="font-size:12px;">🏺 Kervan Carpet — Göreme</p>
                <a href="https://wa.me/905367602165" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            </div>
            <div class="vip-person">
                <p class="vip-name">Hüseyin ÖZER</p>
                <p style="font-size:12px;">🖼️ Punto Antique — Ortahisar</p>
                <a href="https://wa.me/905324970321" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            </div>
        </div>
    </div>
</div>

<h2 class="section-title">✍️ A Letter from Your Local Guide</h2>
<div class="personal-note">
    <p>Dear traveller, welcome to Cappadocia. My name is <strong>Fatih Mehmet Canıtez</strong>, and I have been living and guiding in this region for over 50 years.</p>
    <p>This map represents my life's work. The places I have marked are not random; they are people I trust and places I love. Slow down, ask questions, and let Cappadocia touch your heart.</p>
    <div style="text-align:right;"><strong>Fatih Mehmet Canıtez</strong><br>Teacher & Local Guide</div>
</div>

<script>
// HARİTA AYARLARI
var map, currentLang = 'en', activePoint = null;

window.onload = function() {
    map = L.map('map').setView([38.65, 34.85], 11);
    L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

    var locations = [
        {
            coords: [38.642, 34.829], wa: "905367602165",
            en: { n: "KERVAN CARPET", w: "Recommended for Shopping", s: "Fine hand-knotted carpets.", d: "Ask for Bülent personally." },
            fr: { n: "KERVAN CARPET", w: "Hautement recommandé", s: "Tapis noués à la main.", d: "Demandez Bülent." },
            tr: { n: "KERVAN HALI", w: "Alışveriş için Önerilir", s: "El dokuması halılar.", d: "Bülent Bey'i bulun." }
            // Diğer diller buraya eklenebilir...
        },
        {
            coords: [38.6431, 34.8619],
            en: { n: "GÖREME OPEN AIR MUSEUM", w: "UNESCO Site", s: "10th century rock churches.", d: "Arrive before 9 AM." },
            fr: { n: "MUSÉE DE GÖREME", w: "Patrimoine UNESCO", s: "Églises byzantines.", d: "Arrivez tôt." }
        },
        {
            coords: [38.6289, 34.8053],
            en: { n: "UCHISAR CASTLE", w: "Best View", s: "Highest point in the region.", d: "Perfect for sunset." },
            fr: { n: "CHÂTEAU D'UÇHISAR", w: "Meilleure vue", s: "Point culminant.", d: "Idéal pour le coucher du soleil." }
        }
    ];

    locations.forEach(function(loc) {
        var marker = L.marker(loc.coords).addTo(map);
        marker.on('click', function() {
            activePoint = loc;
            updateUI();
        });
    });

    window.setLang = function(lang) {
        currentLang = lang;
        document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
        document.getElementById(lang + '-btn').classList.add('active');
        if(activePoint) updateUI();
    };

    window.updateUI = function() {
        if(!activePoint) return;
        var d = activePoint[currentLang] || activePoint['en'];
        document.getElementById('place-name').innerText = d.n;
        document.getElementById('worth-text').innerText = d.w;
        document.getElementById('see-text').innerText = d.s;
        document.getElementById('do-text').innerText = d.d;
        
        if(activePoint.wa) {
            document.getElementById('contact-section').style.display = 'block';
            document.getElementById('wa-link').href = "https://wa.me/" + activePoint.wa;
        } else {
            document.getElementById('contact-section').style.display = 'none';
        }
        document.getElementById('info-card').classList.add('visible');
    };

    window.closePanel = function() {
        document.getElementById('info-card').classList.remove('visible');
    };

    setTimeout(() => { map.invalidateSize(); }, 500);
};
</script>
