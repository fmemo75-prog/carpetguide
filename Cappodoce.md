---
layout: default
title: Cappadocia Complete Guide — Fatih Mehmet Canıtez
---
### 🚀 [CLICK HERE: Where to Go & What to See in Cappadocia](./en/cappadocia-guide)

---

<p align="center"><i>"Explore the timeless beauty of the valleys."</i></p>

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />

&nbsp;

&nbsp;

&nbsp;

<style>
/* ── GENEL ─────────────────────────────────────────────────────────── */
body { font-family: Georgia, serif; color: #333; }
h2.section-title { color: #8b0000; border-left: 5px solid #8b0000; padding-left: 14px; margin: 40px 0 16px; font-size: 20px; }
hr.divider { border: none; border-top: 1px solid #e8d5c0; margin: 40px 0; }

/* ── DİL BUTONLARI ─────────────────────────────────────────────────── */
.lang-box { text-align: center; margin: 18px 0; display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; }
.lang-btn { padding: 7px 14px; cursor: pointer; border-radius: 50px; border: 1.5px solid #8b0000; background: white; font-weight: bold; font-size: 12px; transition: 0.2s; font-family: Georgia, serif; }
.lang-btn.active, .lang-btn:hover { background: #8b0000; color: white; }

/* ── HARİTA ────────────────────────────────────────────────────────── */
#map-wrapper { position: relative; }
#map { height: 560px; width: 100%; border-radius: 14px; border: 3px solid #8b0000; box-shadow: 0 8px 24px rgba(0,0,0,0.18); }

/* ── OVERLAY PANEL ─────────────────────────────────────────────────── */
#info-card {
    display: none;
    position: absolute;
    top: 12px; right: 12px;
    width: 300px; max-height: 530px;
    overflow-y: auto;
    background: #fff;
    padding: 18px;
    border-radius: 12px;
    border-top: 7px solid #8b0000;
    box-shadow: 0 6px 28px rgba(0,0,0,0.26);
    z-index: 1000;
    box-sizing: border-box;
}
#info-card.visible { display: block; }
#close-btn { position: absolute; top: 9px; right: 11px; background: none; border: none; font-size: 19px; cursor: pointer; color: #8b0000; line-height: 1; padding: 0; }
#close-btn:hover { color: #333; }
.info-section { margin-bottom: 9px; padding-bottom: 7px; border-bottom: 1px dashed #ddd; }
.info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 10px; display: block; margin-bottom: 2px; }
#place-name { margin: 0 22px 10px 0; color: #8b0000; font-size: 14px; line-height: 1.3; }
.whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 6px 13px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 6px; font-size: 12px; }

/* ── MOBİL PANEL ───────────────────────────────────────────────────── */
@media (max-width: 540px) {
    #info-card { top: auto; bottom: 10px; right: 8px; left: 8px; width: auto; max-height: 50%; }
}
/* ── MOBİL SCROLL HİNT ─────────────────────────────────────────────── */
#scroll-hint {
    display: none; position: absolute;
    bottom: 68px; left: 50%; transform: translateX(-50%);
    background: rgba(139,0,0,0.85); color: white;
    font-size: 12px; padding: 6px 15px; border-radius: 18px;
    white-space: nowrap; z-index: 1100; pointer-events: none;
    animation: bounceUp 1.4s ease-in-out infinite;
}
#scroll-hint.visible { display: block; }
@keyframes bounceUp { 0%,100%{transform:translateX(-50%) translateY(0)} 50%{transform:translateX(-50%) translateY(-5px)} }
@media (min-width: 541px) { #scroll-hint { display: none !important; } }

/* ── VIP TABLO KARTI ───────────────────────────────────────────────── */
.vip-card { background: #fff; border-radius: 13px; border-top: 7px solid #8b0000; box-shadow: 0 4px 18px rgba(0,0,0,0.11); overflow: hidden; }
.vip-header { background: #8b0000; padding: 13px 16px; }
.vip-header p { margin: 0; color: white; }
.vip-person { padding: 13px 16px; border-bottom: 1px solid #f0e0e0; }
.vip-person:last-child { border-bottom: none; }
.vip-name { margin: 0 0 2px; font-size: 14px; font-weight: bold; color: #8b0000; }
.vip-loc  { margin: 0 0 2px; font-size: 12px; color: #555; }
.vip-spec { margin: 0 0 8px; font-size: 11px; color: #888; font-style: italic; }
.btn-row  { display: flex; gap: 5px; flex-wrap: wrap; }
.btn-sm   { padding: 5px 11px; border-radius: 18px; text-decoration: none; font-size: 11px; font-weight: bold; color: white; }

/* ── BÖLÜM KUTULARI ────────────────────────────────────────────────── */
.info-box { background: #fffaf0; border: 1px dashed #c8a96e; border-radius: 10px; padding: 20px 22px; }
.town-card { flex: 1; min-width: 220px; background: #f9f9f9; padding: 16px; border-radius: 10px; }
.museum-card { flex: 1; min-width: 220px; background: #fdf5e6; border-radius: 10px; padding: 16px; }
.adventure-cell { flex: 1; min-width: 220px; background: #fff8f0; border-left: 4px solid #e67e22; border-radius: 8px; padding: 14px 16px; }

/* ── KİŞİSEL MEKTUP ────────────────────────────────────────────────── */
.personal-note {
    background: #fdfaf6; border: 1px solid #e0d5c5; border-left: 5px solid #8b0000;
    padding: 28px 32px; border-radius: 10px;
    box-shadow: 0 3px 12px rgba(0,0,0,0.06); position: relative; overflow: hidden;
}
.personal-note::before { content: "\201C"; position: absolute; top: 8px; left: 18px; font-size: 70px; color: #8b0000; opacity: 0.08; line-height: 1; }
.personal-note h2 { color: #8b0000; margin-top: 0; font-size: 20px; border-bottom: 1px solid #eee; padding-bottom: 10px; }
.personal-note p { line-height: 1.85; margin-bottom: 14px; font-style: italic; }
.signature { text-align: right; margin-top: 18px; }
.signature strong { color: #8b0000; font-size: 16px; }
.signature span { display: block; font-size: 13px; color: #777; font-style: normal; margin-top: 3px; }

/* ── FOOTER ────────────────────────────────────────────────────────── */
.footer-cta { text-align: center; background: #2c3e50; color: white; padding: 22px; border-radius: 10px; }
.footer-cta h3 { margin: 0 0 8px; }
.footer-cta p { margin: 0 0 12px; font-size: 14px; opacity: 0.85; }
.footer-cta a { color: #d4af37; font-weight: bold; text-decoration: none; }
</style>

&nbsp;

<div style="text-align:center; padding: 10px 0 4px;">
    <h1 style="color:#8b0000; margin-bottom:4px;">🏺 Cappadocia Complete Guide</h1>
    <p style="color:#888; font-size:14px; margin:0;"><i>Insider Tips · VIP Contacts · Interactive Map · 7 Languages</i></p>
</div>

<div class="lang-box">
    <button id="en-btn" class="lang-btn active" onclick="setLang('en')">🇺🇸 English</button><p></p>
    <button id="fr-btn" class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button><p></p>
    <button id="es-btn" class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button><p></p>
    <button id="it-btn" class="lang-btn" onclick="setLang('it')">🇮🇹 Italiano</button><p></p>
    <button id="ru-btn" class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button><p></p>
    <button id="zh-btn" class="lang-btn" onclick="setLang('zh')">🇨🇳 中文</button><p></p>
    <button id="ja-btn" class="lang-btn" onclick="setLang('ja')">🇯🇵 日本語</button><p></p>
</div>

&nbsp;

<h2 class="section-title">🗺️ Interactive Map &amp; Trusted Contacts</h2>

<div style="display:flex; gap:18px; align-items:flex-start; flex-wrap:wrap;">
<p><!-- Harita -->
</p><div style="flex:1 1 58%; min-width:280px;">
<div id="map-wrapper">
<div id="map"></div>
<div id="scroll-hint">👆 Scroll up to read more</div>
<div id="info-card">
<button id="close-btn" onclick="closePanel()">✕</button><p></p>
<h3 id="place-name"></h3>
<div class="info-section">
<span class="info-label" id="label-worth"></span>
<p id="worth-text" style="font-weight:bold; margin:4px 0; font-size:13px;"></p>
</div>
<div class="info-section">
<span class="info-label" id="label-see"></span>
<p id="see-text" style="margin:4px 0; font-size:13px;"></p>
</div>
<div id="contact-section" class="info-section" style="display:none; background:#f0fff4; padding:9px; border-radius:8px;">
<span class="info-label">📱 Direct Contact</span>
<p id="contact-name" style="margin:4px 0; font-weight:bold; font-size:12px;"></p>
<a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
<a id="ig-link" href="#" target="_blank" style="display:none; margin-left:6px; background:#E1306C; color:white; padding:6px 13px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:12px;">📸 Instagram</a>
<a id="maps-link" href="#" target="_blank" style="display:none; margin-left:6px; background:#4285F4; color:white; padding:6px 13px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:12px;">📍 Maps</a>
</div>
<div class="info-section" style="border-bottom:none;">
<span class="info-label" id="label-secret"></span>
<p id="do-text" style="margin:4px 0; font-style:italic; font-size:13px;"></p>
</div>
</div>
</div>
<p style="font-size:12px; color:#999; margin:6px 0 0; text-align:center;">📍 Click any marker for details, contacts &amp; directions</p>
</div><p></p>
<p><!-- VIP Tablo -->
</p><div style="flex:1 1 34%; min-width:240px;">
<div class="vip-card">
<div class="vip-header">
<p style="font-size:15px; font-weight:bold; letter-spacing:0.4px;">⭐ Trusted VIP Contacts</p>
<p style="font-size:11px; color:#ffcccc; margin-top:3px;">Personally recommended · 50 years of friendship</p>
</div>
<div class="vip-person">
<p class="vip-name">Bülent Güler</p>
<p class="vip-loc">🏺 Kervan Carpet — Göreme</p>
<p class="vip-spec">Hand-knotted carpets &amp; fine textiles</p>
<div class="btn-row">
<a href="https://wa.me/905367602165" target="_blank" class="btn-sm" style="background:#25D366;">💬 WhatsApp</a>
<a href="https://share.google/4EOqQF0v25v89O0XW" target="_blank" class="btn-sm" style="background:#4285F4;">📍 Maps</a>
</div>
</div>
<div class="vip-person">
<p class="vip-name">Headmaster Hüseyin ÖZER</p>
<p class="vip-loc">🖼️ Punto Antique Carpets — Ortahisar</p>
<p class="vip-spec">Rare antique &amp; collectible textiles</p>
<div class="btn-row">
<a href="https://wa.me/905324970321" target="_blank" class="btn-sm" style="background:#25D366;">💬 WhatsApp</a>
<a href="https://www.instagram.com/puntoofcappadocia/" target="_blank" class="btn-sm" style="background:#E1306C;">📸 Instagram</a>
</div>
</div>
<div class="vip-person">
<p class="vip-name">Halil KÖKSAL</p>
<p class="vip-loc">🗺️ VIP Cultural Guide — Göreme</p>
<p class="vip-spec">French &amp; Spanish specialist · Deep historian</p>
<div class="btn-row">
<a href="https://wa.me/905322478674" target="_blank" class="btn-sm" style="background:#25D366;">💬 WhatsApp</a>
</div>
</div>
</div>
</div><p></p>
</div>

&nbsp;

---

&nbsp;

<h2 class="section-title">✍️ A Letter from Your Local Guide</h2>

<div class="personal-note">
    <h2>My Cappadocia, My Life — The Triad of the Kızılırmak</h2>
    <p>
        Dear traveller, welcome to Cappadocia — one of the most extraordinary places on earth. My name is <strong>Fatih Mehmet Canıtez</strong>, and I have been living, teaching, and guiding in this region for over 50 years.
    </p>
    <p>
        My life follows the path of the <strong>Kızılırmak (Red River)</strong>, the longest river in Turkey. I was born in <strong>Bayramhacı</strong>, a village by the dam famous for its thermal springs, where I first learned the value of nature and healing waters. I grew up in <strong>Avanos</strong>, where the river's red clay shaped my childhood and my love for traditional craft. And I settled in <strong>Göreme</strong>, the heart of Cappadocia, where I now dedicate my days to sharing this extraordinary culture with visitors from every corner of the world.
    </p>
    <p>
        This map represents a 40-kilometre circle where I have spent my entire life — learning every valley, every stone, every knot of our culture. The places and people I have marked here are not random recommendations. They are the result of half a century of trust, personal experience, and genuine friendship. When I point you to a carpet dealer or a local expert, I do so as a friend who has sat at their table, drunk their tea, and watched them work with my own eyes.
    </p>
    <p>
        As a teacher by profession and a passionate guide by heart, I have one simple piece of advice: <em>slow down, ask questions, buy from people you trust, and let Cappadocia touch your heart the way it has touched mine.</em>
    </p>
    <div class="signature">
        <strong>Fatih Mehmet Canıtez</strong>
        <span>Teacher · Local Guide · Göreme, Cappadocia</span>
    </div>
</div>

&nbsp;

---

&nbsp;

<h2 class="section-title">🎈 The Hot Air Balloon — Everything You Need to Know</h2>

<div class="info-box">
    <p>The number one question every visitor asks. Here is the honest, complete answer.</p>
<p></p><p><strong>Why do prices change daily?</strong><br />
Think of it like a stock market. Prices depend on seasonality (May–October is peak) and the "backlog effect" — if flights are cancelled for 3 days in a row due to wind, prices on the 4th day spike sharply because hundreds of people are waiting. Book early and stay flexible with your dates.</p><p></p>
<p></p><p><strong>The Flag System — 🟢 Green / 🟡 Yellow / 🔴 Red</strong><br />
Each morning, the <strong>SHGM (Turkish Civil Aviation Authority)</strong> makes the final safety call.
🟢 Green means we fly. 🟡 Yellow means delay or standby. 🔴 Red means cancelled for everyone — no exceptions, regardless of price, agency, or luck. This is a safety rule. Respect it.</p><p></p>
<p></p><p><strong>What about refunds?</strong><br />
If the SHGM cancels the flight, you receive a <strong>100% full refund</strong>. No fees. Every legitimate company in Cappadocia follows this rule without question.</p><p></p>
<p></p><p style="margin-bottom:0;"><strong>💡 Free alternative:</strong> Drive to the <em>Göreme Panorama Viewpoint</em> at sunrise. Watching 80+ colourful balloons rise over the valleys with a cup of tea in hand is a memory for a lifetime — and it costs nothing.</p><p></p>
</div>

&nbsp;

---

&nbsp;

<h2 class="section-title">🏘️ Towns You Must Visit</h2>

<div style="display:flex; flex-wrap:wrap; gap:16px;">
    <div class="town-card" style="border-left:5px solid #d4af37;">
        <h4 style="margin:0 0 8px; color:#8b0000;">🌟 Ürgüp</h4>
        <p style="margin:0; font-size:14px; line-height:1.7;">The sophisticated side of Cappadocia. Excellent boutique hotels, restaurants, and wine bars. Don't miss the <em>Three Beauties</em> fairy chimneys, and try the local <strong>Emir</strong> white wine — unique to this volcanic terroir.</p>
    </div>
    <div class="town-card" style="border-left:5px solid #2e8b57;">
        <h4 style="margin:0 0 8px; color:#8b0000;">🎨 Avanos</h4>
        <p style="margin:0; font-size:14px; line-height:1.7;">My childhood home. Crossed by the Red River, this town has been a centre of pottery for over 4,000 years. Try the pottery wheel yourself — most workshops welcome visitors. Walk across the old bridge in the evening.</p>
    </div>
    <div class="town-card" style="border-left:5px solid #8b0000;">
        <h4 style="margin:0 0 8px; color:#8b0000;">⛪ Mustafapaşa</h4>
        <p style="margin:0; font-size:14px; line-height:1.7;">A hidden historical treasure. Formerly known as Sinasos, this quiet village holds some of the finest examples of 19th-century Greek-Ottoman stone architecture in Turkey. Almost no tourists — go on a weekday morning.</p>
    </div>
    <div class="town-card" style="border-left:5px solid #c0392b;">
        <h4 style="margin:0 0 8px; color:#8b0000;">♨️ Bayramhacı</h4>
        <p style="margin:0; font-size:14px; line-height:1.7;">My birthplace, by the dam. If you want a break from rocks and fairy chimneys, come here for the natural <strong>thermal springs</strong> and the calm of the reservoir. Almost unknown to foreign visitors — a genuine local secret.</p>
    </div>
</div>

&nbsp;

---

&nbsp;

<h2 class="section-title">🏛️ Museums &amp; Hidden Valleys</h2>

<div style="display:flex; flex-wrap:wrap; gap:16px;">
    <div class="museum-card">
        <p style="margin:0 0 6px; font-weight:bold; color:#8b0000;">Göreme Open Air Museum</p>
        <p style="margin:0; font-size:13px; line-height:1.7;">UNESCO World Heritage Site. The mandatory stop. Arrive before 9 AM — the <em>Dark Church</em> (Karanlık Kilise) requires a separate ticket but has the finest frescoes in the region.</p>
    </div>
    <div class="museum-card">
        <p style="margin:0 0 6px; font-weight:bold; color:#8b0000;">Zelve Open Air Museum</p>
        <p style="margin:0; font-size:13px; line-height:1.7;">Much larger and wilder than Göreme. A labyrinth of dwellings, cave churches, and passages. Great for hiking without large crowds. Half a day is enough — wear proper shoes.</p>
    </div>
    <div class="museum-card">
        <p style="margin:0 0 6px; font-weight:bold; color:#8b0000;">Ihlara Valley</p>
        <p style="margin:0; font-size:13px; line-height:1.7;">A 14 km canyon hike along the Melendiz River, with over 100 rock-cut churches in the walls. Cool, green, and beautiful. Combine with Selime Monastery at the northern end.</p>
    </div>
    <div class="museum-card">
        <p style="margin:0 0 6px; font-weight:bold; color:#8b0000;">Derinkuyu Underground City</p>
        <p style="margin:0; font-size:13px; line-height:1.7;">85 metres deep, 11 floors, capacity for 20,000 people. The world's deepest underground city. About 40 km south of Göreme. Allow 1.5 hours. Not suitable for claustrophobic visitors.</p>
    </div>
</div>

&nbsp;

---

&nbsp;

<h2 class="section-title">🐎 Adventure &amp; Outdoor Activities</h2>

<div style="display:flex; flex-wrap:wrap; gap:16px;">
    <div class="adventure-cell">
        <p style="margin:0 0 6px; font-weight:bold; font-size:15px;">🐎 Horseback Riding</p>
        <p style="margin:0; font-size:14px; line-height:1.7;">Cappadocia means <em>"Land of Beautiful Horses"</em> in Persian. Sunset rides through Rose Valley or Love Valley are pure magic. Book with a small local operator — the experience is far more personal than hotel packages.</p>
    </div>
    <div class="adventure-cell">
        <p style="margin:0 0 6px; font-weight:bold; font-size:15px;">🏍️ ATV / Quad Safari</p>
        <p style="margin:0; font-size:14px; line-height:1.7;">Best for Sword Valley and Love Valley. If you like dust, adrenaline, and extraordinary views — this is your activity. Go in the late afternoon for the golden light. Helmets are mandatory; take them seriously.</p>
    </div>
    <div class="adventure-cell">
        <p style="margin:0 0 6px; font-weight:bold; font-size:15px;">🥾 Valley Hiking</p>
        <p style="margin:0; font-size:14px; line-height:1.7;">The best free activity in Cappadocia. Pigeon Valley (Göreme to Uçhisar, 4 km), Rose Valley, and Red Valley are all walkable without a guide. Start early, carry water, and stop at the rock-carved tea house in Pigeon Valley.</p>
    </div>
</div>

&nbsp;

---

<div class="footer-cta">
    <h3>Need more local advice?</h3>
    <p>As a local teacher active in Göreme for 50 years, I am here to help you understand the true culture behind the fairy chimneys — beyond the tourist trail.</p>
    <a href="./me">Learn more about me &amp; my French courses →</a>
</div>

<p style="text-align:center; margin-top:24px; font-size:13px; color:#888;">
    <a href="./" style="color:#8b0000;">🏠 Return to Main Dashboard</a>
    &nbsp;|&nbsp;
    <a href="./en/handknotted" style="color:#8b0000;">🧶 Technical Carpet Guide</a>
</p>

&nbsp;

<script>
var map = L.map('map').setView([38.65, 34.85], 11);
var currentLang = 'en';
var activePoint = null;

L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

var locations = [
    /* ── DÜKKANLAR & UZMANLAR ─────────────────────────────────── */
    {
        coords: [38.642, 34.829], id: "kervan",
        wa: "905367602165", maps: "https://share.google/4EOqQF0v25v89O0XW",
        en: { n: "KERVAN CARPET (Bülent Güler)", w: "Highly Recommended for Shopping", s: "Located in Göreme. Fine selection of hand-knotted carpets and textiles.", d: "Ask for Bülent personally. He is a true gentleman of the craft." },
        fr: { n: "KERVAN CARPET (Bülent Güler)", w: "Hautement recommandé", s: "Situé à Göreme. Fine sélection de tapis noués à la main.", d: "Demandez Bülent personnellement. Un vrai maître de l'art." },
        es: { n: "ALFOMBRAS KERVAN (Bülent Güler)", w: "Muy recomendado", s: "Göreme. Gran selección de alfombras anudadas a mano.", d: "Pregunta por Bülent personalmente." },
        it: { n: "KERVAN CARPET (Bülent Güler)", w: "Altamente raccomandato", s: "Göreme. Selezione di tappeti annodati a mano.", d: "Chiedi di Bülent personalmente." },
        ru: { n: "КЕРВАН КОВРЫ (Бюлент Гюлер)", w: "Рекомендуется", s: "Гёреме. Лучший выбор ковров ручной работы.", d: "Спросите Бюлента лично." },
        zh: { n: "KERVAN 地毯 (Bülent Güler)", w: "强烈推荐", s: "格雷梅，精选手工编织地毯。", d: "亲自找 Bülent。" },
        ja: { n: "KERVAN 絨毯 (Bülent Güler)", w: "強くお勧め", s: "ギョレメ。手織り絨毯の精選。", d: "Bülentさんに直接声をかけてください。" }
    },
    {
        coords: [38.621, 34.856], id: "punto",
        wa: "905324970321", ig: "puntoofcappadocia",
        en: { n: "PUNTO ANTIQUE CARPETS", w: "VIP Antique Collection", s: "Ortahisar. Specialist in old and rare textile collections from across Anatolia.", d: "Ask for Headmaster Hüseyin ÖZER for a professional antique analysis." },
        fr: { n: "PUNTO TAPIS ANTIQUES", w: "Collection VIP Antique", s: "Ortahisar. Spécialiste des collections textiles rares d'Anatolie.", d: "Demandez le Directeur Hüseyin ÖZER pour une analyse professionnelle." },
        es: { n: "PUNTO ALFOMBRAS ANTIGUAS", w: "Colección VIP Antique", s: "Ortahisar. Especialista en piezas textiles raras de Anatolia.", d: "Pregunta por el Director Hüseyin ÖZER para análisis profesional." },
        it: { n: "PUNTO TAPPETI ANTICHI", w: "Collezione Antica VIP", s: "Ortahisar. Specialista in tessuti rari dell'Anatolia.", d: "Chiedi del Direttore Hüseyin ÖZER per un'analisi professionale." },
        ru: { n: "ПУНТО АНТИКВАРНЫЕ КОВРЫ", w: "VIP Антикварная коллекция", s: "Ортахисар. Редкие антикварные ковры Анатолии.", d: "Обратитесь к директору Хюсейн ОЗЕР для профессиональной экспертизы." },
        zh: { n: "PUNTO 古董地毯", w: "VIP古董收藏", s: "奥塔希萨尔，专注安纳托利亚稀有织物收藏。", d: "请找负责人 Hüseyin ÖZER 进行专业鉴定。" },
        ja: { n: "PUNTO アンティーク絨毯", w: "VIPアンティーク", s: "オルタヒサル。アナトリアの希少なアンティーク絨毯の専門店。", d: "ヘッドマスター Hüseyin ÖZER さんに専門鑑定をお願いしてください。" }
    },
    {
        coords: [38.645, 34.831], id: "ikman",
        en: { n: "IKMAN CARPET — Photography Spot", w: "The #1 Instagram Location in Göreme", s: "Famous for stunning traditional carpet photography setups. A colourful paradise.", d: "Best light in the morning. Very photogenic in all seasons." },
        fr: { n: "IKMAN CARPET — Photo", w: "Le spot Instagram n°1 à Göreme", s: "Célèbre pour ses mises en scène photographiques avec tapis traditionnels.", d: "Meilleure lumière le matin. Photogénique toute l'année." },
        es: { n: "IKMAN CARPET — Fotos", w: "Punto Instagram #1 en Göreme", s: "Famoso por sus escenografías fotográficas con alfombras tradicionales.", d: "Mejor luz por la mañana. Fotogénico todo el año." },
        it: { n: "IKMAN CARPET — Foto", w: "Spot Instagram #1 a Göreme", s: "Famoso per i set fotografici con tappeti tradizionali.", d: "Luce migliore al mattino. Fotogenico in tutte le stagioni." },
        ru: { n: "ИКМАН КОВРЫ — Фото", w: "Инстаграм спот №1 в Гёреме", s: "Знаменитое место для фотосессий с традиционными коврами.", d: "Лучший свет утром. Фотогенично круглый год." },
        zh: { n: "IKMAN 地毯 — 摄影", w: "格雷梅顶级打卡点", s: "传统地毯背景摄影圣地，色彩缤纷。", d: "早晨光线最佳，四季皆宜拍摄。" },
        ja: { n: "IKMAN 絨毯 — 写真", w: "ギョレメ最高インスタスポット", s: "伝統的な絨毯を使った写真撮影で有名な場所。", d: "午前中の光が最高。年間を通して絵になります。" }
    },
    {
        coords: [38.641, 34.832], id: "museum",
        en: { n: "ANATOLIAN ART MUSEUM", w: "Cultural Landmark", s: "Dedicated to the history of Anatolian weaving and carpet arts. A serious academic collection.", d: "Essential for understanding the depth and history behind every carpet you will see." },
        fr: { n: "MUSÉE D'ART ANATOLIEN", w: "Repère culturel", s: "Dédié à l'histoire du tissage anatolien. Collection académique sérieuse.", d: "Indispensable pour comprendre chaque tapis que vous verrez." },
        es: { n: "MUSEO DE ARTE ANATOLIO", w: "Hito cultural", s: "Dedicado a la historia del tejido anatolio. Colección académica seria.", d: "Esencial para entender cada alfombra que verás." },
        it: { n: "MUSEO D'ARTE ANATOLICA", w: "Punto culturale", s: "Dedicato alla storia della tessitura anatolica. Collezione accademica seria.", d: "Essenziale per capire ogni tappeto che vedrete." },
        ru: { n: "МУЗЕЙ АНАТОЛИЙСКОГО ИСКУССТВА", w: "Культурный центр", s: "История анатолийского ткачества. Серьёзная академическая коллекция.", d: "Необходимо для понимания каждого ковра, который вы увидите." },
        zh: { n: "安纳托利亚艺术博物馆", w: "文化地标", s: "致力于安纳托利亚编织艺术史，严肃的学术收藏。", d: "有助于理解您将看到的每一块地毯背后的历史。" },
        ja: { n: "アナトリア芸術博物館", w: "文化遺産", s: "アナトリアの織物・絨毯芸術の歴史。学術的なコレクション。", d: "これから見るすべての絨毯を理解するために不可欠。" }
    },
    {
        coords: [38.640, 34.825], id: "halil",
        wa: "905322478674",
        en: { n: "VIP GUIDE: Halil KÖKSAL", w: "Expert Cultural Guide — FR & ES", s: "Specialist in French and Spanish. Deep historical knowledge of Cappadocia, Anatolia, and Byzantine culture.", d: "Book Halil for a high-quality professional tour. In my 50 years, he is the best guide I know." },
        fr: { n: "GUIDE VIP : Halil KÖKSAL", w: "Conférencier Expert — FR & ES", s: "Spécialiste en Français et Espagnol. Connaissance approfondie de la Cappadoce et de la culture byzantine.", d: "Réservez Halil pour une visite de la plus haute qualité. En 50 ans, c'est le meilleur guide que je connaisse." },
        es: { n: "GUÍA VIP: Halil KÖKSAL", w: "Guía Experto — FR & ES", s: "Especialista en Francés y Español. Conocimiento profundo de Capadocia y la cultura bizantina.", d: "Reserva a Halil. En 50 años, es el mejor guía que conozco." },
        it: { n: "GUIDA VIP: Halil KÖKSAL", w: "Guida Esperta — FR & ES", s: "Parla Francese e Spagnolo. Conoscenza approfondita della Cappadocia e della cultura bizantina.", d: "Prenota Halil. In 50 anni, è la migliore guida che conosca." },
        ru: { n: "VIP ГИД: Халил КЁКСАЛ", w: "Профессиональный гид — FR & ES", s: "Специалист на французском и испанском. Глубокое знание Каппадокии и Византии.", d: "Закажите Халила. За 50 лет — лучший гид, которого я знаю." },
        zh: { n: "VIP 导游: Halil KÖKSAL", w: "专家文化导游 — FR & ES", s: "精通法语和西班牙语。深厚的卡帕多西亚和拜占庭文化知识。", d: "预订 Halil。50年来，他是我认识的最好导游。" },
        ja: { n: "VIPガイド: Halil KÖKSAL", w: "公認文化ガイド — FR & ES", s: "仏語・西語エキスパート。カッパドキアとビザンチン文化の深い知識。", d: "Halilさんを予約してください。50年間で知る最高のガイドです。" }
    },

    /* ── TARİHİ & DOĞAL ALANLAR ────────────────────────────────── */
    {
        coords: [38.6431, 34.8619], id: "goreme_oam",
        en: { n: "GÖREME OPEN AIR MUSEUM", w: "UNESCO World Heritage Site", s: "Byzantine rock-cut churches with stunning frescoes, dating to the 10th century. The Dark Church (Karanlık Kilise) has the finest preserved paintings in the region.", d: "Arrive before 9 AM. The Dark Church costs extra but is absolutely worth every lira." },
        fr: { n: "MUSÉE EN PLEIN AIR DE GÖREME", w: "Patrimoine Mondial UNESCO", s: "Églises rupestres byzantines avec fresques du Xe siècle. L'Église Sombre possède les peintures les mieux conservées.", d: "Arrivez avant 9h. L'Église Sombre vaut le billet supplémentaire." },
        es: { n: "MUSEO AL AIRE LIBRE DE GÖREME", w: "Patrimonio Mundial UNESCO", s: "Iglesias rupestres byzantinas con frescos del siglo X. La Iglesia Oscura tiene las pinturas mejor conservadas.", d: "Llega antes de las 9 AM. La Iglesia Oscura vale cada lira extra." },
        it: { n: "MUSEO ALL'APERTO DI GÖREME", w: "Patrimonio UNESCO", s: "Chiese rupestri bizantine con affreschi del X sec. La Chiesa Oscura ha le pitture meglio conservate.", d: "Arriva prima delle 9. La Chiesa Oscura vale il biglietto extra." },
        ru: { n: "МУЗЕЙ ГЁРЕМЕ", w: "Объект ЮНЕСКО", s: "Скальные церкви X века. Тёмная церковь — лучшие сохранившиеся фрески региона.", d: "Приходите до 9 утра. Тёмная церковь стоит отдельного билета." },
        zh: { n: "戈莱梅露天博物馆", w: "联合国教科文组织世界遗产", s: "10世纪拜占庭岩石教堂，壁画精美。黑暗教堂保存最完好。", d: "建议9点前到达。黑暗教堂值得单独购票。" },
        ja: { n: "ギョレメ野外博物館", w: "ユネスコ世界遺産", s: "10世紀のビザンチン岩窟教会群。暗闇教会のフレスコ画は必見。", d: "午前9時前到着を。暗闇教会は別料金でも絶対に価値あり。" }
    },
    {
        coords: [38.6289, 34.8053], id: "uchisar",
        en: { n: "UCHISAR CASTLE", w: "Highest Point — Best Panorama", s: "A 60-metre volcanic citadel with a 360° view of all Cappadocia. Used as a Byzantine watchtower against Arab raids.", d: "Best at sunset — golden fairy chimneys as far as the eye can see. Wear sturdy shoes for the steep climb." },
        fr: { n: "CHÂTEAU D'UÇHISAR", w: "Point le plus haut — Panorama 360°", s: "Citadelle volcanique de 60m. Vue à 360° sur toute la Cappadoce.", d: "Magnifique au coucher du soleil. Portez des chaussures solides." },
        es: { n: "CASTILLO DE UÇHISAR", w: "Punto más alto — Panorama 360°", s: "Ciudadela volcánica de 60m. Vista panorámica de 360°.", d: "Mejor al atardecer. Usa calzado resistente para la subida." },
        it: { n: "CASTELLO DI UÇHISAR", w: "Punto più alto — Panorama 360°", s: "Cittadella vulcanica di 60m. Vista a 360° su tutta la Cappadocia.", d: "Magnifico al tramonto. Indossa scarpe robuste." },
        ru: { n: "ЗАМОК УЧИСАР", w: "Высшая точка — Панорама 360°", s: "60-метровая крепость. Круговой обзор всей Каппадокии.", d: "Лучше всего на закате. Надевайте удобную обувь." },
        zh: { n: "乌奇萨尔城堡", w: "最高点——360°全景", s: "60米火山古堡，360°俯瞰整个卡帕多西亚。", d: "日落时分最美，请穿防滑鞋。" },
        ja: { n: "ユチヒサール城塞", w: "最高地点——360°パノラマ", s: "60mの火山岩要塞。カッパドキア全体を360°見渡せる。", d: "夕日の時間帯がベスト。滑りにくい靴で登ってください。" }
    },
    {
        coords: [38.3736, 34.7344], id: "derinkuyu",
        en: { n: "DERINKUYU UNDERGROUND CITY", w: "World's Deepest Underground City", s: "85 metres deep, 11 floors, built in the 8th century BC. Could shelter 20,000 people with stables, churches, wineries, and schools.", d: "About 40 km south of Göreme by bus or tour. Allow 1.5 hours. Not suitable for claustrophobic visitors — passages get very narrow." },
        fr: { n: "VILLE SOUTERRAINE DE DERINKUYU", w: "La plus profonde ville souterraine", s: "85m, 11 étages, VIIIe s. av. J.-C. Abritait 20 000 personnes.", d: "À 40 km au sud. Déconseillé aux claustrophobes." },
        es: { n: "CIUDAD SUBTERRÁNEA DE DERINKUYU", w: "La ciudad subterránea más profunda", s: "85m, 11 plantas, siglo VIII a.C. Albergaba 20.000 personas.", d: "A 40 km al sur. No recomendada para claustrofóbicos." },
        it: { n: "CITTÀ SOTTERRANEA DI DERINKUYU", w: "La città sotterranea più profonda", s: "85m, 11 livelli, VIII sec. a.C. Ospitava 20.000 persone.", d: "A 40 km a sud. Sconsigliata ai claustrofobici." },
        ru: { n: "ДЕРИНКУЮ — ПОДЗЕМНЫЙ ГОРОД", w: "Самый глубокий подземный город", s: "85 метров, 11 этажей, VIII в. до н.э. Вмещал 20 000 человек.", d: "40 км к югу от Гёреме. Не для клаустрофобов." },
        zh: { n: "德林库尤地下城", w: "世界最深地下城市", s: "深85米，11层，公元前8世纪建造，可容纳2万人。", d: "格雷梅以南约40公里。不建议幽闭恐惧症患者参观。" },
        ja: { n: "デリンクユ地下都市", w: "世界最深の地下都市", s: "深さ85m、11層。紀元前8世紀建造。2万人を収容可能。", d: "ギョレメから南へ約40km。閉所恐怖症の方は要注意。" }
    },
    {
        coords: [38.6836, 34.8478], id: "pasabag",
        en: { n: "PAŞABAĞ — MONKS VALLEY", w: "Best Fairy Chimneys Up Close", s: "The finest place to see triple-headed fairy chimneys up close. Some have monk cells and small chapels carved inside.", d: "Arrive before 9 AM to beat the tour buses. The triple-headed chimney is the star — it is unlike anything else on earth." },
        fr: { n: "PAŞABAĞ — VALLÉE DES MOINES", w: "Meilleures cheminées de fées de près", s: "Le meilleur endroit pour voir les cheminées à trois têtes de près.", d: "Arrivez avant 9h. La cheminée triple est la vedette." },
        es: { n: "PAŞABAĞ — VALLE DE LOS MONJES", w: "Mejores chimeneas de hadas de cerca", s: "El mejor lugar para ver las chimeneas de tres cabezas de cerca.", d: "Llega antes de las 9 AM. La chimenea triple es la estrella." },
        it: { n: "PAŞABAĞ — VALLE DEI MONACI", w: "Migliori ciminiere delle fate vicino", s: "Il posto migliore per vedere le ciminiere a tre teste da vicino.", d: "Arriva prima delle 9. La ciminiera tripla è la protagonista." },
        ru: { n: "ПАШАБАГ — ДОЛИНА МОНАХОВ", w: "Лучшие «трубы» вблизи", s: "Лучшее место для осмотра трёхголовых «каминных труб» вблизи.", d: "Приходите до 9 утра. Трёхголовая труба — главная звезда." },
        zh: { n: "帕夏贝/僧侣谷", w: "近距离仙女烟囱最佳", s: "近距离欣赏三头仙女烟囱的最佳地点。", d: "9点前到达以避开旅游大巴。三头烟囱是绝对明星。" },
        ja: { n: "パシャバー/僧侶の谷", w: "妖精の煙突を間近で見る", s: "3つ頭の妖精の煙突を間近で見る最高の場所。", d: "午前9時前に到着を。3つ頭の煙突は世界唯一の絶景。" }
    },
    {
        coords: [38.7181, 34.8486], id: "avanos",
        en: { n: "AVANOS — Pottery Town", w: "Living Craft Tradition · 4,000 Years", s: "On the banks of the Kızılırmak. The red clay has been used for pottery here for 4,000 years. Dozens of workshops welcome visitors.", d: "Try throwing a pot yourself — most ateliers offer sessions. Buy directly from the artisan for the best quality and price." },
        fr: { n: "AVANOS — Ville de la Poterie", w: "Tradition vivante · 4000 ans", s: "Sur les rives du Kızılırmak. L'argile rouge est utilisée depuis 4000 ans.", d: "Essayez le tour de potier. Achetez directement chez l'artisan." },
        es: { n: "AVANOS — Ciudad de la Cerámica", w: "Tradición viva · 4.000 años", s: "A orillas del Kızılırmak. La arcilla roja se usa desde hace 4.000 años.", d: "Prueba el torno tú mismo. Compra directamente al artesano." },
        it: { n: "AVANOS — Città della Ceramica", w: "Tradizione viva · 4000 anni", s: "Sulle rive del Kızılırmak. L'argilla rossa è usata da 4000 anni.", d: "Prova il tornio tu stesso. Acquista dall'artigiano direttamente." },
        ru: { n: "АВАНОС — Город Гончаров", w: "Живая традиция · 4000 лет", s: "На берегу Кызылырмак. Красная глина используется 4000 лет.", d: "Попробуйте на гончарном круге. Покупайте напрямую у мастера." },
        zh: { n: "阿瓦诺斯——陶器之城", w: "活着的传统 · 4000年", s: "克孜勒河畔，红陶工艺传承4000年，数十家工坊开放参观。", d: "亲自尝试拉坯体验。直接从工匠处购买品质最好。" },
        ja: { n: "アヴァノス——陶芸の街", w: "生きた伝統 · 4000年", s: "クズルウルマク川沿い。4000年の陶芸伝統。数十の工房が開放。", d: "陶芸体験を試してください。職人から直接購入がベスト。" }
    },
    {
        coords: [38.6353, 34.8232], id: "pigeon_valley",
        en: { n: "PIGEON VALLEY (Güvercinlik Vadisi)", w: "Best Free Hike in Cappadocia", s: "4 km trail between Göreme and Uçhisar, named after hundreds of dovecotes carved into the cliffs. Stunning views throughout.", d: "Walk downhill from Uçhisar Castle toward Göreme. Stop at the rock-carved tea house midway — a unique experience." },
        fr: { n: "VALLÉE DES PIGEONS", w: "Meilleure randonnée gratuite", s: "Sentier de 4 km entre Göreme et Uçhisar. Des centaines de pigeonholes dans les falaises.", d: "Descendez d'Uçhisar vers Göreme. Pause thé au jardin de thé rupestre." },
        es: { n: "VALLE DE LAS PALOMAS", w: "Mejor excursión gratuita", s: "Sendero de 4 km entre Göreme y Uçhisar. Cientos de palomares en los acantilados.", d: "Baja desde Uçhisar hacia Göreme. Para en el jardín de té rupestre." },
        it: { n: "VALLE DEI PICCIONI", w: "Miglior escursione gratuita", s: "Sentiero di 4 km tra Göreme e Uçhisar. Centinaia di colombaie nelle pareti.", d: "Scendi da Uçhisar verso Göreme. Fermati al giardino del tè rupestre." },
        ru: { n: "ГОЛУБИНАЯ ДОЛИНА", w: "Лучший бесплатный поход", s: "Тропа 4 км между Гёреме и Учисаром. Сотни голубятен в скалах.", d: "Идите от Учисара вниз к Гёреме. Остановитесь на чай в скальном саду." },
        zh: { n: "鸽子谷（Güvercinlik Vadisi）", w: "最佳免费徒步路线", s: "格雷梅与乌奇萨尔之间4公里步道，悬崖上数百个鸽巢。", d: "从乌奇萨尔下坡走向格雷梅。途中在岩石茶园小憩，体验独特。" },
        ja: { n: "鳩の谷（Güvercinlik Vadisi）", w: "カッパドキア最高の無料ハイク", s: "ギョレメとユチヒサール間4kmのトレイル。断崖に刻まれた鳩小屋が並ぶ。", d: "ユチヒサールからギョレメへ下りながら歩くのがベスト。岩を掘り抜いたお茶屋で一休みを。" }
    },
    {
        coords: [38.6473, 34.8281], id: "balloon",
        en: { n: "HOT AIR BALLOON — Launch Point", w: "Once-in-a-Lifetime Experience", s: "Sunrise flights over the fairy chimneys. Over 80 balloons fill the sky at dawn. The SHGM (Civil Aviation Authority) controls all flights for safety.", d: "Book 2+ days in advance. Full refund if SHGM cancels. Free alternative: Göreme Panorama Viewpoint at sunrise." },
        fr: { n: "MONTGOLFIÈRE — Point de lancement", w: "Expérience unique dans une vie", s: "Vols au lever du soleil. 80+ ballons à l'aube. Le SHGM contrôle la sécurité.", d: "Réservez 2+ jours à l'avance. Remboursement si annulation SHGM." },
        es: { n: "GLOBO AEROSTÁTICO — Punto de lanzamiento", w: "Experiencia única en la vida", s: "Vuelos al amanecer. 80+ globos al alba. El SHGM controla la seguridad.", d: "Reserva con 2+ días. Reembolso total si el SHGM cancela." },
        it: { n: "MONGOLFIERA — Punto di lancio", w: "Esperienza unica nella vita", s: "Voli all'alba. 80+ mongolfiere. Il SHGM controlla la sicurezza.", d: "Prenota 2+ giorni prima. Rimborso totale se annullato dal SHGM." },
        ru: { n: "ВОЗДУШНЫЙ ШАР — Точка старта", w: "Незабываемый опыт жизни", s: "Полёты на рассвете. 80+ шаров. Безопасность контролирует SHGM.", d: "Бронируйте за 2+ дня. Полный возврат при отмене SHGM." },
        zh: { n: "热气球——起飞点", w: "一生一次的体验", s: "日出时分飞越仙女烟囱，逾80只气球升空。SHGM负责飞行安全。", d: "提前2天以上预订。SHGM取消可全额退款。" },
        ja: { n: "熱気球——打ち上げポイント", w: "一生に一度の体験", s: "夜明けのフライト。80機以上のバルーン。SHGMが安全を管理。", d: "2日以上前に予約を。SHGM中止の場合は全額返金。" }
    },
    {
        coords: [38.6340, 34.9142], id: "urgup",
        en: { n: "ÜRGÜP — Wine & Boutique Town", w: "Best Dining, Wine & Accommodation", s: "Sophisticated base with boutique hotels in restored Ottoman stone houses. Famous for Emir and Öküzgözü wines unique to this volcanic soil.", d: "Visit the wine houses in the evening. The local Emir white wine is crisp and unlike anything else in Turkey." },
        fr: { n: "ÜRGÜP — Ville du Vin & Charme", w: "Meilleure gastronomie & hôtellerie", s: "Boutique hôtels dans des maisons ottomanes restaurées. Vins Emir et Öküzgözü uniques.", d: "Visitez les maisons de vin le soir. Le vin blanc Emir est exceptionnel." },
        es: { n: "ÜRGÜP — Vino & Encanto", w: "Mejor gastronomía & alojamiento", s: "Hoteles boutique en casas otomanas restauradas. Vinos Emir y Öküzgözü únicos.", d: "Visita las bodegas al atardecer. El Emir blanco es excepcional." },
        it: { n: "ÜRGÜP — Vino & Charme", w: "Migliore gastronomia & alloggio", s: "Boutique hotel in case ottomane restaurate. Vini Emir e Öküzgözü unici.", d: "Visita le cantine la sera. Il vino bianco Emir è eccezionale." },
        ru: { n: "УРГЮП — Вино и шарм", w: "Лучшая гастрономия и проживание", s: "Бутик-отели в отреставрированных османских домах. Вина Эмир и Окюзгёзю.", d: "Посетите винные дома вечером. Вино Эмир неповторимо." },
        zh: { n: "于尔居普——葡萄酒与魅力", w: "最佳餐饮、葡萄酒与住宿", s: "奥斯曼石屋精品酒店，埃米尔和厄屈兹格孜葡萄酒独一无二。", d: "傍晚参观酒庄。埃米尔白葡萄酒清爽独特。" },
        ja: { n: "ユルギュップ——ワインと魅力の街", w: "最高のグルメ・宿泊ハブ", s: "オスマン石造り精品ホテルが充実。エミル、オキュズゴズワインが名物。", d: "夕方にワイン蔵へ。エミル白ワインはトルコで唯一無二の味。" }
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
    marker.on('click', function() { activePoint = loc; updateUI(); });
});

function updateUI() {
    if (!activePoint) return;
    var d = activePoint[currentLang];
    var l = labels[currentLang];

    document.getElementById('place-name').innerText   = d.n;
    document.getElementById('worth-text').innerText   = d.w;
    document.getElementById('see-text').innerText     = d.s;
    document.getElementById('do-text').innerText      = d.d;
    document.getElementById('label-worth').innerText  = l.worth;
    document.getElementById('label-see').innerText    = l.see;
    document.getElementById('label-secret').innerText = l.secret;

    if (activePoint.wa) {
        document.getElementById('contact-section').style.display = 'block';
        document.getElementById('contact-name').innerText = d.n;
        document.getElementById('wa-link').href = "https://wa.me/" + activePoint.wa;
    } else {
        document.getElementById('contact-section').style.display = 'none';
    }
    var igEl = document.getElementById('ig-link');
    igEl.style.display = activePoint.ig ? 'inline-block' : 'none';
    if (activePoint.ig) igEl.href = "https://www.instagram.com/" + activePoint.ig + "/";

    var mpEl = document.getElementById('maps-link');
    mpEl.style.display = activePoint.maps ? 'inline-block' : 'none';
    if (activePoint.maps) mpEl.href = activePoint.maps;

    document.getElementById('info-card').classList.add('visible');
    document.getElementById('scroll-hint').classList.add('visible');
    setTimeout(function() {
        document.getElementById('scroll-hint').classList.remove('visible');
    }, 4000);
}

function closePanel() {
    document.getElementById('info-card').classList.remove('visible');
    document.getElementById('scroll-hint').classList.remove('visible');
    activePoint = null;
}

function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('.lang-btn').forEach(function(b) { b.classList.remove('active'); });
    document.getElementById(lang + '-btn').classList.add('active');
    updateUI();
}
</script>

&nbsp;