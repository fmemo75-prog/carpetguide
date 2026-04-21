---
layout: default
title: "THE ANATOLIAN LEGACY: Full Print Version"
---

<style>
  /* Baskı Modu Ayarları */
  @media print {
    header, footer, .back-home-container, header, .translate-bar, #google_translate_element { display: none !important; }
    .container { width: 100% !important; max-width: 100% !important; border: none !important; box-shadow: none !important; margin: 0 !important; padding: 0 !important; }
    .page-break { page-break-before: always; }
  }
  .book-section { margin-bottom: 60px; padding: 20px; border: 1px solid #eee; border-radius: 10px; }
</style>

<div style="text-align: center; padding: 40px 0;">
  <h1>🏛️ THE ANATOLIAN LEGACY</h1>
  <h2>Carpets, Culture & Language</h2>
  <p><b>Curated by Fatih Mehmet Canıtez</b></p>
  <hr>
</div>

<div class="book-section">
  <h3>📖 Table of Contents (İçindekiler)</h3>
  <ul>
    <li>Cappadocia Guide</li>
    <li>Technical Weaving Analysis</li>
    <li>Imperial Hereke Collection</li>
    <li>Material World</li>
  </ul>
</div>

<!-- DİKKAT: Dosyaları çağırırken YAML hatası almamak için 
     eğer hala 404 alıyorsan aşağıdaki blokları tek tek ekleyerek dene -->

<div class="book-section">
  <div class="page-break"></div>
  <!-- Kapadokya Dosyası -->
  {% capture cap %}{% include_relative Cappodoce.md %}{% endcapture %}
  {{ cap | split: "---" | last }}
</div>

<div class="book-section">
  <div class="page-break"></div>
  <!-- Halı Teknikleri -->
  {% capture flat %}{% include_relative flat-viewing.md %}{% endcapture %}
  {{ flat | split: "---" | last }}
</div>

<div class="book-section">
  <div class="page-break"></div>
  <!-- Hereke Dosyası (en klasöründe) -->
  {% capture hereke %}{% include_relative en/hereke.md %}{% endcapture %}
  {{ hereke | split: "---" | last }}
</div>

<div style="text-align: center; color: #888; margin-top: 50px;">
  <p>*** End of Book Draft ***</p>
</div>