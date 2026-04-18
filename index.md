---
layout: default
title: Global Carpet & Kilim Guide — Fatih Mehmet Canıtez
---
<div style="text-align: center; margin: 30px 0;">
  <a href="./gallery" style="background: #8b0000; color: white !important; padding: 15px 30px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 1.2em; box-shadow: 0 5px 15px rgba(139,0,0,0.3);">
    📸 View My Personal Photo Gallery
  </a>
</div>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">

<style>
/* ── RESET — Facebook in-app browser'da güvenli ───────────── */
* { box-sizing: border-box; -webkit-box-sizing: border-box; margin: 0; padding: 0; }
html { -webkit-text-size-adjust: 100%; text-size-adjust: 100%; }
body { font-family: Georgia, 'Times New Roman', serif; background: #faf8f5; color: #2c2c2c; -webkit-font-smoothing: antialiased; overflow-x: hidden; }
a { text-decoration: none; -webkit-tap-highlight-color: rgba(139,0,0,0.15); }
img { max-width: 100%; height: auto; display: block; }

/* ── HERO ──────────────────────────────────────────────────── */
.hero {
    width: 100%;
    background: #3d0000;
    background: -webkit-linear-gradient(135deg, #1a0a0a 0%, #3d0000 45%, #6b0f0f 100%);
    background: linear-gradient(135deg, #1a0a0a 0%, #3d0000 45%, #6b0f0f 100%);
    border-radius: 0 0 24px 24px;
    padding: 44px 20px 40px;
    /* inset yerine top/right/bottom/left — FB uyumu */
}
/* FB browser ::before pseudo-element desteği kısıtlı olabilir,
   arka plan görseli doğrudan hero'ya taşıdık */
.hero-bg-overlay {
    /* JS ile yüklenen görsel için placeholder — script aşağıda */
    position: absolute;
    display: none; /* JS açacak */
}
.hero-inner {
    max-width: 860px;
    margin: 0 auto;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    gap: 24px;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
}
.hero-avatar {
    width: 90px; height: 90px;
    border-radius: 50%;
    border: 3px solid #d4af37;
    object-fit: cover;
    -webkit-flex-shrink: 0;
    flex-shrink: 0;
    box-shadow: 0 4px 16px rgba(0,0,0,0.5);
}
.hero-text { -webkit-box-flex: 1; flex: 1; min-width: 180px; }
.hero-text h1 {
    font-size: 22px;
    color: #fff;
    line-height: 1.25;
    margin-bottom: 8px;
}
.hero-text h1 span { color: #d4af37; display: block; font-size: 17px; margin-top: 3px; }
.hero-text p {
    color: rgba(255,255,255,0.72);
    font-size: 14px;
    line-height: 1.6;
    margin-bottom: 20px;
}
.hero-btns {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    gap: 10px;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
}

/* ── BUTONLAR — min 44px dokunma alanı (Apple/Google HIG) ─── */
.btn-gold {
    display: inline-block;
    background: #d4af37;
    color: #1a0a0a !important;
    padding: 13px 22px;
    border-radius: 50px;
    font-weight: bold;
    font-size: 14px;
    min-height: 44px;
    line-height: 1.2;
    -webkit-appearance: none;
    box-shadow: 0 3px 10px rgba(212,175,55,0.4);
}
.btn-outline {
    display: inline-block;
    background: transparent;
    color: white !important;
    padding: 12px 22px;
    border-radius: 50px;
    font-weight: bold;
    font-size: 14px;
    min-height: 44px;
    line-height: 1.2;
    border: 1.5px solid rgba(255,255,255,0.5);
}

/* ── LOOM BANNER ───────────────────────────────────────────── */
.loom-banner { padding: 28px 16px 0; max-width: 960px; margin: 0 auto; }
.loom-banner img { width: 100%; border-radius: 16px; box-shadow: 0 6px 24px rgba(0,0,0,0.12); }

/* ── FEATURED CARD (Cappadocia) ────────────────────────────── */
.featured-wrap { padding: 28px 16px 0; max-width: 960px; margin: 0 auto; }
.featured-card {
    background: #4a0000;
    background: -webkit-linear-gradient(120deg, #3d0000 0%, #6b1414 100%);
    background: linear-gradient(120deg, #3d0000 0%, #6b1414 100%);
    border-radius: 16px;
    padding: 26px 22px;
    box-shadow: 0 6px 24px rgba(139,0,0,0.3);
}
.featured-card h3 { color: #d4af37; font-size: 18px; margin-bottom: 10px; }
.featured-card p  { color: rgba(255,255,255,0.78); font-size: 14px; line-height: 1.65; margin-bottom: 18px; }
.featured-btns {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    gap: 10px;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
}
.btn-featured-primary {
    display: inline-block;
    background: #d4af37;
    color: #1a0a0a !important;
    padding: 13px 20px;
    border-radius: 50px;
    font-weight: bold;
    font-size: 14px;
    min-height: 44px;
    line-height: 1.2;
    text-align: center;
    box-shadow: 0 3px 10px rgba(212,175,55,0.35);
    -webkit-appearance: none;
}
.btn-featured-outline {
    display: inline-block;
    background: transparent;
    color: white !important;
    padding: 12px 20px;
    border-radius: 50px;
    font-weight: bold;
    font-size: 14px;
    min-height: 44px;
    line-height: 1.2;
    text-align: center;
    border: 1.5px solid rgba(255,255,255,0.4);
}

/* ── SECTION LABEL ─────────────────────────────────────────── */
.sec-label { text-align: center; padding: 36px 16px 18px; max-width: 960px; margin: 0 auto; }
.sec-label-bar {
    width: 50px; height: 3px;
    background: #8b0000; border-radius: 2px;
    margin: 0 auto 12px;
}
.sec-label h2 { font-size: 17px; color: #8b0000; }
.sec-label p  { font-size: 13px; color: #999; margin-top: 5px; }
.sec-label.green .sec-label-bar { background: #2e8b57; }
.sec-label.green h2 { color: #2e8b57; }

/* ── CARD GRID ─────────────────────────────────────────────── */
.card-grid {
    max-width: 960px; margin: 0 auto;
    padding: 0 16px;
    display: -ms-grid;
    display: grid;
    /* Mobilde 2 sütun, masaüstünde 4 */
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
}
@media (min-width: 600px) {
    .card-grid { grid-template-columns: repeat(4, 1fr); }
}
.card {
    background: #fff;
    border-radius: 14px;
    padding: 18px 15px;
    border: 1px solid #ede8df;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    gap: 7px;
    /* Aktif durumu — hover yerine active (FB/mobil uyumu) */
    -webkit-tap-highlight-color: rgba(139,0,0,0.08);
}
.card:active { background: #fdf5ef; border-color: #c8a06e; }
.card.green:active { background: #f0faf4; border-color: #2e8b57; }
.card-icon { font-size: 24px; line-height: 1; }
.card-title { font-size: 13px; font-weight: bold; color: #2c2c2c; line-height: 1.3; }
.card-desc  { font-size: 12px; color: #999; line-height: 1.5; -webkit-box-flex: 1; flex: 1; }
.card-link  { font-size: 12px; font-weight: bold; color: #8b0000; margin-top: 4px; }
.card.green .card-link { color: #2e8b57; }

/* ── FOOTER ────────────────────────────────────────────────── */
.site-footer {
    max-width: 960px; margin: 40px auto 0;
    padding: 24px 16px 32px;
    border-top: 1px solid #ede8df;
    text-align: center;
}
.footer-name { font-size: 14px; color: #555; margin-bottom: 14px; }
.footer-name strong { color: #8b0000; display: block; font-size: 15px; margin-bottom: 3px; }
.footer-name span { font-size: 12px; color: #aaa; }
.footer-profile {
    display: inline-block;
    border: 1.5px solid #c8a06e;
    color: #8b0000 !important;
    padding: 11px 22px;
    border-radius: 50px;
    font-size: 13px;
    font-weight: bold;
    min-height: 44px;
    line-height: 1.2;
}
.footer-profile:active { background: #8b0000; color: white !important; }

/* ── TAM MOBİL (max 480px) ─────────────────────────────────── */
@media (max-width: 480px) {
    .hero { padding: 36px 16px 34px; }
    .hero-inner {
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
        -ms-flex-direction: column;
        flex-direction: column;
        text-align: center;
    }
    .hero-btns {
        -webkit-box-pack: center;
        -ms-flex-pack: center;
        justify-content: center;
    }
    .hero-text h1 { font-size: 20px; }
    .featured-btns {
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
        -ms-flex-direction: column;
        flex-direction: column;
    }
    .btn-featured-primary,
    .btn-featured-outline { width: 100%; }
}

/* ── FB IN-APP BROWSER ÖZEL DÜZELTMELERİ ──────────────────── */
/* FB bazı transform ve transition'ları engeller — kullanmıyoruz */
/* position:fixed yok sayılır — kullanmıyoruz */
/* vh units hatalı — min-height yerine padding kullandık */
/* CSS vars desteği kısıtlı — tüm renkler hardcode */
</style>


<!-- ════════════════════════════════════════════════════════ -->
<!--  HERO                                                    -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="hero">
    <div class="hero-inner">
        <img src="./carpet.jpeg" alt="Fatih Mehmet Canıtez" class="hero-avatar">
        <div class="hero-text">
            <h1>
                🧶 Global Carpet &amp; Kilim Guide
                <span>by Fatih Mehmet Canıtez</span>
            </h1>
            <p>French Language Educator · Expert Curator · 50 years living and studying the carpets, valleys, and culture of Cappadocia.</p>
            <div class="hero-btns">
                <a href="./me" class="btn-gold">👤 Curator Profile</a>
                <a href="./Cappodoce" class="btn-outline">🌄 Cappadocia Guide</a>
            </div>
        </div>
    </div>
</div>


<!-- ════════════════════════════════════════════════════════ -->
<!--  LOOM IMAGE                                              -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="loom-banner">
    <img src="./loom.jpg" alt="Traditional Anatolian Loom" loading="lazy">
</div>

<!-- HISTORY SHORTCUT - ELEGANT MINI CARD -->
<div style="text-align: center; margin-top: 20px;">
  <a href="{{ site.baseurl }}/history-carpet" style="display: inline-flex; align-items: center; background: #fffcf5; border: 1px solid #d4af37; padding: 10px 20px; border-radius: 50px; text-decoration: none; transition: 0.3s; box-shadow: 0 4px 15px rgba(212, 175, 55, 0.1); max-width: 280px;">
    
    <!-- Simge: Antik bir mühür veya parşömen hissi -->
    <span style="font-size: 22px; margin-right: 12px;">🏛️</span>
    
    <div style="text-align: left;">
      <div style="color: #8b4513; font-weight: bold; font-size: 13px; letter-spacing: 0.5px; text-transform: uppercase;">Carpet History</div>
      <div style="color: #998542; font-size: 10px; font-style: italic;">From Pazyryk to Palaces</div>
    </div>

    <!-- Küçük Ok Simgesi -->
    <span style="color: #d4af37; margin-left: 15px; font-size: 12px;">➔</span>
  </a>
</div>

<!-- ════════════════════════════════════════════════════════ -->
<!--  CAPPADOCIA FEATURED                                     -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="featured-wrap">
    <div class="featured-card">
        <h3>🌄 My Cappadocia Insider Guide</h3>
        <p>50 years of walking these valleys, visiting workshops, and building genuine friendships. Interactive map, VIP contacts, balloon tips, and a personal letter — in 7 languages.</p>
        <div class="featured-btns">
            <a href="/carpetguide/Cappodoce.html#interactive-map" class="btn-featured-primary">🗺️ Open Interactive Map</a>
            <a href="./Cappodoce" class="btn-featured-outline">📖 Full Guide</a>
        </div>
    </div>
</div>


<!-- ════════════════════════════════════════════════════════ -->
<!--  HISTORICAL & TECHNICAL                                  -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="sec-label">
    <div class="sec-label-bar"></div>
    <h2>🏛️ Historical &amp; Technical Deep-Dives</h2>
    <p>From imperial looms to ancient techniques — the academic side of the craft</p>
</div>

<div class="card-grid">
    <a href="./en/hereke" class="card">
        <div class="card-icon">🏰</div>
        <div class="card-title">Imperial Hereke</div>
        <div class="card-desc">The finest silk carpets ever woven — made for Ottoman palaces.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/" class="card">
        <div class="card-icon">🏺</div>
        <div class="card-title">Pazyryk Analysis</div>
        <div class="card-desc">The world's oldest surviving carpet. 2,500 years old.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/handknotted" class="card">
        <div class="card-icon">🌍</div>
        <div class="card-title">Carpet World</div>
        <div class="card-desc">Hand-knotted traditions from Persia, Anatolia, Central Asia.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/materials" class="card">
        <div class="card-icon">📊</div>
        <div class="card-title">Materials &amp; Techniques</div>
        <div class="card-desc">Wool, silk, dyes, knot types and density explained.</div>
        <div class="card-link">Explore →</div>
    </a>
</div>

<!-- INTERACTIVE TECHNICAL GUIDE SECTION -->
<div style="text-align: center; margin: 30px 0; padding: 25px; background: #fdf5e6; border: 2px solid #2e8b57; border-radius: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);">
  <h3 style="color: #2e8b57; margin-top: 0; font-family: 'Georgia', serif;">🌍 Master the Art of Weaving</h3>
  <p style="font-size: 15px; color: #444;">Explore our detailed analysis of ancient methods.</p>
  <a href="./flat-viewing" style="...">🔍 Interactive Kilim & Double Knot Techniques</a>
 

<!-- ════════════════════════════════════════════════════════ -->
<!--  KILIM & FLAT-WEAVE                                      -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="sec-label green">
    <div class="sec-label-bar"></div>
    <h2>📐 Kilim &amp; Flat-Weave Masterpieces</h2>
    <p>The woven language of Anatolia — symbols, structure, and soul</p>
</div>

<div class="card-grid">
    <a href="./en/kilim" class="card green">
        <div class="card-icon">📐</div>
        <div class="card-title">Kilim Guide</div>
        <div class="card-desc">Anatolian flat-weave — regions, motifs, how to read them.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/cicim" class="card green">
        <div class="card-icon">🌸</div>
        <div class="card-title">Cicim Style</div>
        <div class="card-desc">Embroidery on kilim — a delicate supplementary weft technique.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/sumak" class="card green">
        <div class="card-icon">🌀</div>
        <div class="card-title">Sumak Technique</div>
        <div class="card-desc">Wrap-weave without knots — dense, reversible, complex.</div>
        <div class="card-link">Explore →</div>
    </a>
    <a href="./en/zili" class="card green">
        <div class="card-icon">🏗️</div>
        <div class="card-title">Zili Technique</div>
        <div class="card-desc">Bold geometric float-weave of the Caucasus.</div>
        <div class="card-link">Explore →</div>
    </a>
</div>


<!-- ════════════════════════════════════════════════════════ -->
<!--  FOOTER                                                  -->
<!-- ════════════════════════════════════════════════════════ -->
<div class="site-footer">
    <div class="footer-name">
        <strong>Fatih Mehmet Canıtez</strong>
        <span>French Language Educator · Expert Carpet Curator · Göreme, Cappadocia</span>
    </div>
    <a href="./me" class="footer-profile">👤 Curator Profile &amp; French Lessons →</a>
</div>
<!-- MOBILE-FIRST VIDEO POPUP -->
<div id="videoPopup" style="display: none; position: fixed; z-index: 10000; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.85); align-items: center; justify-content: center; backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px);">
  
  <div style="position: relative; width: 85%; max-width: 340px; background: #fff; border-radius: 30px; overflow: hidden; box-shadow: 0 25px 50px rgba(0,0,0,0.6); animation: popupAnim 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);">
    
    <!-- KAPATMA BUTONU (Mobil için büyük ve kolay erişilir) -->
    <button onclick="closeVideo()" style="position: absolute; top: 15px; right: 15px; background: #b22222; color: #fff; border: none; border-radius: 50%; width: 44px; height: 44px; font-size: 24px; cursor: pointer; z-index: 11; display: flex; align-items: center; justify-content: center; box-shadow: 0 4px 12px rgba(0,0,0,0.3); -webkit-tap-highlight-color: transparent;">✕</button>

    <!-- YOUTUBE VİDEO (Dikey format optimized) -->
    <div style="position: relative; padding-bottom: 177%; height: 0; overflow: hidden; background: #000;">
      <iframe id="heroVideo" 
              src="https://www.youtube.com/embed/O46EivpT9gI?autoplay=1&mute=1&loop=1&playlist=O46EivpT9gI&controls=0&modestbranding=1&rel=0&playsinline=1" 
              style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none;" 
              allow="autoplay; encrypted-media" 
              allowfullscreen>
      </iframe>
    </div>

    <!-- MOBİL BİLGİ ALANI -->
    <div style="padding: 15px 20px 20px; text-align: center; background: #fff;">
      <div style="width: 40px; height: 4px; background: #ddd; border-radius: 10px; margin: 0 auto 15px;"></div>
      <h3 style="margin: 0; font-size: 16px; color: #8b4513; font-family: sans-serif;">The Double Knot</h3>
      <p style="margin: 5px 0 0; font-size: 12px; color: #666;">The secret behind 100 years of durability.</p>
    </div>
  </div>
</div>

<style>
  /* Mobilde giriş animasyonu */
  @keyframes popupAnim {
    from { transform: scale(0.8) translateY(50px); opacity: 0; }
    to { transform: scale(1) translateY(0); opacity: 1; }
  }
</style>

<script>
  // Mobil performansı için 2 saniye bekleyip aç (sayfa önce bir otursun)
  window.addEventListener('load', function() {
    setTimeout(function() {
      document.getElementById('videoPopup').style.display = 'flex';
    }, 2000);
  });

  function closeVideo() {
    var popup = document.getElementById('videoPopup');
    var iframe = document.getElementById('heroVideo');
    popup.style.display = 'none';
    iframe.src = ""; // Videoyu tamamen öldür (kaynak tüketmesin)
  }

  // Boşluğa tıklayınca da kapansın (Mobil kullanıcı alışkanlığı)
  document.getElementById('videoPopup').onclick = function(e) {
    if (e.target == this) closeVideo();
  };
</script>