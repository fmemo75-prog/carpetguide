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
#map-wrapper { position: relative; width: 100%; }
#map { height: 560px; width: 100%; border-radius: 14px; border: 3px solid #8b0000; box-shadow: 0 8px 24px rgba(0,0,0,0.18); z-index: 1; }
#info-card {
    display: none; position: absolute; top: 12px; right: 12px;
    width: 300px; max-height: 530px; overflow-y: auto;
    background: #fff; padding: 18px; border-radius: 12px;
    border-top: 7px solid #8b0000; box-shadow: 0 6px 28px rgba(0,0,0,0.26);
    z-index: 1000;
}
#info-card.visible { display: block; }
.info-section { margin-bottom: 9px; padding-bottom: 7px; border-bottom: 1px dashed #ddd; }
.info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 10px; display: block; margin-bottom: 2px; }
.whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 6px 13px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 6px; font-size: 12px; }

/* ── VIP KARTLARI ── */
.vip-card { background: #fff; border-radius: 13px; border-top: 7px solid #8b0000; box-shadow: 0 4px 18px rgba(0,0,0,0.11); overflow: hidden; }
.vip-header { background: #8b0000; padding: 13px 16px; color: white; font-weight: bold; }
.vip-person { padding: 13px 16px; border-bottom: 1px solid #f0e0e0; }
.vip-name { font-weight: bold; color: #8b0000; margin: 0; }

/* ── BİLGİ KUTULARI ── */
.info-box { background: #fffaf0; border: 1px dashed #c8a96e; border-radius: 10px; padding: 20px; margin: 20px 0; }
.town-card, .museum-card { flex: 1; min-width: 220px; background: #f9f9f9; padding: 16px; border-radius: 10px; border-left: 4px solid #d4af37; }
.personal-note { background: #fdfaf6; border-left: 5px solid #8b0000; padding: 28px; border-radius: 10px; box-shadow: 0 3px 12px rgba(0,0,0,0.06); }

@media (max-width: 768px) {
    #info-card { position: fixed; top: auto; bottom: 0; left: 0; right: 0; width: 100%; max-height: 45%; border-radius: 20px 20px 0 0; }
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

<div style="display:flex; gap:18px; flex-wrap:wrap; align-items:flex-start;">
    <!-- HARİTA -->
    <div style="flex:1 1 58%; min-width:280px;">
        <div id="map-wrapper">
            <div id="map"></div>
            <div id="info-card">
                <button onclick="closePanel()" style="float:right; border:none; background:none; font-size:20px; cursor:pointer; color:#8b0000;">✕</button>
                <h3 id="place-name" style="color:#8b0000; margin-top:0;"></h3>
                <div class="info-section">
                    <span class="info-label" id="label-worth">Expert Recommendation</span>
                    <p id="worth-text" style="font-weight:bold; margin:4px 0; font-size:13px;"></p>
                </div>
                <div class="info-section">
                    <span class="info-label" id="label-see">Description</span>
                    <p id="see-text" style="margin:4px 0; font-size:13px;"></p>
                </div>
                <div id="contact-section" class="info-section" style="display:none; background:#f0fff4; padding:9px; border-radius:8px;">
                    <span class="info-label">📱 Direct Contact</span>
                    <a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
                </div>
                <div class="info-section" style="border-bottom:none;">
                    <span class="info-label" id="label-secret">Insider Note</span>
                    <p id="do-text" style="margin:4px 0; font-style:italic; font-size:13px;"></p>
                </div>
            </div>
        </div>
    </div>

    <!-- VIP TABLO -->
    <div style="flex:1 1 34%; min-width:240px;">
        <div class="vip-card">
            <div class="vip-header">⭐ Trusted VIP Contacts</div>
            <div class="vip-person">
                <p class="vip-name">Bülent Güler</p>
                <p style="font-size:12px; margin:2px 0;">🏺 Kervan Carpet — Göreme</p>
                <a href="https://wa.me/905367602165" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            </div>
            <div class="vip-person">
                <p class="vip-name">Hüseyin ÖZER</p>
                <p style="font-size:12px; margin:2px 0;">🖼️ Punto Antique — Ortahisar</p>
                <a href="https://wa.me/905324970321" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            </div>
            <div class="vip-person">
                <p class="vip-name">Halil KÖKSAL</p>
                <p style="font-size:12px; margin:2px 0;">🗺️ VIP Cultural Guide — Göreme</p>
                <a href="https://wa.me/905322478674" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            </div>
        </div>
    </div>
</div>

<h2 class="section-title">✍️ A Letter from Your Local Guide</h2>
<div class="personal-note">
    <h3>My Cappadocia, My Life — The Triad of the Kızılırmak</h3>
    <p>Dear traveller, welcome to Cappadocia. My name is <strong>Fatih Mehmet Canıtez</strong>, and I have been living, teaching, and guiding in this region for over 50 years.</p>
    <p>My life follows the path of the <strong>Kızılırmak (Red River)</strong>. I was born in Bayramhacı, grew up in Avanos, and settled in Göreme. This map represents a 40-kilometre circle where I have spent my entire life — learning every stone, every knot of our culture.</p>
    <p>The places and people I have marked here are result of half a century of trust and genuine friendship. <em>Slow down, ask questions, and let Cappadocia touch your heart.</em></p>
    <div style="text-align:right; margin-top:15px;"><strong>Fatih Mehmet Canıtez</strong><br><small>Teacher · Local Guide · Göreme</small></div>
</div>

<h2 class="section-title">🎈 The Hot Air Balloon — Insider Facts</h2>
<div class="info-box">
    <p><strong>Why do prices change?</strong> Prices depend on seasonality and the "backlog effect".Eğer rüzgar nedeniyle uçuşlar 3 gün iptal edilirse, 4. gün fiyatlar tavan yapar çünkü herkes beklemektedir.</p>
    <p><strong>Flag System:</strong> 🟢 Green (Fly), 🟡 Yellow (Standby), 🔴 Red (Cancelled). Bu kararı Sivil Havacılık (SHGM) verir, şirketler değil.</p>
    <p><strong>Refunds:</strong> Eğer uçuş hava durumu nedeniyle iptal edilirse, <strong>%100 tam iade</strong> alırsınız. Bu bir kuraldır.</p>
</div>

<h2 class="section-title">🏘️ Towns & Kasabalar</h2>
<div style="display:flex; flex-wrap:wrap; gap:16px;">
    <div class="town-card">
        <h4 style="margin:0; color:#8b0000;">Ürgüp</h4>
        <p style="font-size:13px;">Boutique hotels and local wine (Emir white wine).</p>
    </div>
    <div class="town-card">
        <h4 style="margin:0; color:#8b0000;">Avanos</h4>
        <p style="font-size:13px;">Centre of pottery for 4,000 years. Try the pottery wheel!</p>
    </div>
    <div class="town-card">
        <h4 style="margin:0; color:#8b0000;">Bayramhacı</h4>
        <p style="font-size:13px;">Natural thermal springs and the calm of the dam.</p>
    </div>
</div>

<script>
var map, currentLang = 'en', activePoint = null;

window.onload = function() {
    map = L.map('map').setView([38.65, 34.85], 11);
    L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

    var locations = [
        {
            coords: [38.642, 34.829], id: "kervan", wa: "905367602165",
            en: { n: "KERVAN CARPET (Bülent Güler)", w: "Highly Recommended", s: "Göreme. Fine hand-knotted carpets.", d: "Ask for Bülent personally." },
            fr: { n: "KERVAN CARPET (Bülent Güler)", w: "Hautement recommandé", s: "Tapis noués à la main.", d: "Demandez Bülent." },
            zh: { n: "KERVAN 地毯", w: "强烈推荐", s: "精选手工编织地毯。", d: "亲自找 Bülent。" }
        },
        {
            coords: [38.621, 34.856], id: "punto", wa: "905324970321",
            en: { n: "PUNTO ANTIQUE CARPETS", w: "VIP Antique Collection", s: "Ortahisar. Rare textile collections.", d: "Ask for Hüseyin ÖZER." },
            fr: { n: "PUNTO TAPIS ANTIQUES", w: "Collection VIP Antique", s: "Textiles rares.", d: "Demandez Hüseyin ÖZER." }
        },
        {
            coords: [38.6431, 34.8619], id: "goreme_oam",
            en: { n: "GÖREME OPEN AIR MUSEUM", w: "UNESCO World Heritage", s: "Byzantine rock-cut churches.", d: "Arrive before 9 AM." },
            fr: { n: "MUSÉE DE GÖREME", w: "Patrimoine UNESCO", s: "Églises rupestres.", d: "Arrivez tôt." }
        }
    ];

    locations.forEach(function(loc) {
        var marker = L.marker(loc.coords).addTo(map);
        marker.on('click', function() { activePoint = loc; updateUI(); });
    });

    window.setLang = function(lang) {
        currentLang = lang;
        document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
        document.getElementById(lang + '-btn').classList.add('active');
        if(activePoint) updateUI();
    };

    window.updateUI = function() {
        if (!activePoint) return;
        var d = activePoint[currentLang] || activePoint['en'];
        document.getElementById('place-name').innerText = d.n;
        document.getElementById('worth-text').innerText = d.w;
        document.getElementById('see-text').innerText = d.s;
        document.getElementById('do-text').innerText = d.d;
        document.getElementById('contact-section').style.display = activePoint.wa ? 'block' : 'none';
        if(activePoint.wa) document.getElementById('wa-link').href = "https://wa.me/" + activePoint.wa;
        document.getElementById('info-card').classList.add('visible');
    };

    window.closePanel = function() { document.getElementById('info-card').classList.remove('visible'); };
    setTimeout(() => { map.invalidateSize(); }, 500);
};
</script>