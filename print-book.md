---
layout: default
title: "THE ANATOLIAN LEGACY: Complete Edition"
---

<style>
  /* BASKI AYARLARI */
  @media print {
    header, footer, .back-home-container, .translate-bar, #google_translate_element { display: none !important; }
    .container { width: 100% !important; max-width: 100% !important; border: none !important; box-shadow: none !important; margin: 0 !important; padding: 10mm !important; }
    .page-break { page-break-before: always; display: block; height: 0; }
    img { max-width: 100% !important; height: auto !important; page-break-inside: avoid !important; display: block; margin: 10px auto; }
    h1, h2, h3 { page-break-after: avoid; color: #8b0000 !important; }
    a { text-decoration: none; color: black !important; }
  }
  
  /* EKRAN GÖRÜNÜMÜ */
  .book-content img { width: 100%; max-width: 800px; border-radius: 8px; margin: 20px 0; }
  .book-section { border-bottom: 2px solid #eee; padding-bottom: 40px; margin-bottom: 40px; }
  .book-title-page { text-align: center; padding: 100px 0; border: 5px double #8b0000; border-radius: 20px; margin-bottom: 50px; }
</style>

<!-- KİTAP KAPAK SAYFASI -->
<div class="book-title-page">
  <h1 style="font-size: 48px; margin-bottom: 10px;">🏛️ THE ANATOLIAN LEGACY</h1>
  <h2 style="font-size: 24px; color: #555;">History, Weaving Techniques & Cappadocia</h2>
  <br><br>
  <p style="font-size: 20px;">Curated by <b>Fatih Mehmet Canıtez</b></p>
  <p><i>Official Guide and Expert Analysis</i></p>
</div>

<div class="page-break"></div>

<div class="book-content">

  <!-- BÖLÜM 1: KAPADOKYA REHBERİ -->
  <div class="book-section">
    <h1 style="color: #8b0000; text-align: center;">PART I: CAPPADOCIA GUIDE</h1>
    {% capture cap %}{% include_relative Cappodoce.md %}{% endcapture %}
    {{ cap | markdownify | split: "---" | last }}
  </div>

  <div class="page-break"></div>

  <!-- BÖLÜM 2: HALI TEKNİKLERİ -->
  <div class="book-section">
    <h1 style="color: #8b0000; text-align: center;">PART II: WEAVING TECHNIQUES</h1>
    {% capture flat %}{% include_relative flat-viewing.md %}{% endcapture %}
    {{ flat | markdownify | split: "---" | last }}
  </div>

  <div class="page-break"></div>

  <!-- BÖLÜM 3: HEREKE VE MALZEMELER -->
  <div class="book-section">
    <h1 style="color: #8b0000; text-align: center;">PART III: IMPERIAL HERITAGE</h1>
    {% capture hereke %}{% include_relative en/hereke.md %}{% endcapture %}
    {{ hereke | markdownify | split: "---" | last }}
  </div>

</div>

<div style="text-align: center; color: #aaa; margin-top: 100px;">
  <p>© 2024 Fatih Mehmet Canıtez - All Rights Reserved.</p>
</div>