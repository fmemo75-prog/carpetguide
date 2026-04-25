---
layout: default
title: Turkey Carpet & Kilim Map — Regional Guide
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
  body { font-family: Georgia, serif; }

  .map-page-title { text-align: center; margin-bottom: 8px; }
  .map-page-title h1 { color: #8b0000; font-size: 1.8em; margin-bottom: 6px; }
  .map-page-title p  { color: #666; font-style: italic; font-size: 0.95em; }

  /* LEGEND */
  .legend { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; margin: 16px 0 20px; }
  .legend-item { display: flex; align-items: center; gap: 6px; font-size: 0.82em; color: #444; }
  .legend-dot { width: 14px; height: 14px; border-radius: 50%; flex-shrink: 0; border: 2px solid rgba(0,0,0,0.2); }

  /* MAP */
  #map-wrapper { position: relative; }
  #carpet-map {
    height: 520px; width: 100%;
    border-radius: 14px;
    border: 3px solid #8b0000;
    box-shadow: 0 8px 24px rgba(0,0,0,0.18);
  }

  /* INFO CARD */
  #info-card {
    display: none;
    position: absolute;
    top: 12px; right: 12px;
    width: 290px; max-height: 500px;
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
  #close-btn { position: absolute; top: 9px; right: 11px; background: none; border: none; font-size: 19px; cursor: pointer; color: #8b0000; }
  #region-name { margin: 0 22px 8px 0; color: #8b0000; font-size: 1.1em; font-weight: bold; }
  .info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 10px; letter-spacing: 0.5px; display: block; margin: 10px 0 3px; }
  .info-text  { font-size: 0.88em; color: #2c3e50; line-height: 1.65; }
  .type-badge {
    display: inline-block; padding: 3px 10px; border-radius: 50px;
    font-size: 0.75em; font-weight: bold; margin: 2px 2px 6px 0; color: white;
  }

  @media (max-width: 540px) {
    #info-card { top: auto; bottom: 10px; right: 8px; left: 8px; width: auto; max-height: 48%; }
    #carpet-map { height: 420px; }
  }

  /* REGION CARDS BELOW MAP */
  .region-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 16px; margin-top: 30px; }
  .region-card {
    background: #fff; border-radius: 12px; padding: 16px 18px;
    border: 1px solid #ede8df; box-shadow: 0 3px 10px rgba(0,0,0,0.06);
    border-left: 5px solid #ccc;
  }
  .region-card h3 { margin: 0 0 6px; font-size: 1em; }
  .region-card p  { margin: 0; font-size: 0.85em; color: #555; line-height: 1.6; }
</style>

<div class="map-page-title">
  <h1>🗺️ Turkey Carpet & Kilim Regions</h1>
  <p>Click any marker to discover the weaving traditions of each region</p>
</div>

<!-- LEGEND -->
<div class="legend">
  <div class="legend-item"><div class="legend-dot" style="background:#d4af37;"></div> Imperial / Palace</div>
  <div class="legend-item"><div class="legend-dot" style="background:#8b0000;"></div> Hand-knotted Carpet</div>
  <div class="legend-item"><div class="legend-dot" style="background:#2e8b57;"></div> Kilim / Flat-weave</div>
  <div class="legend-item"><div class="legend-dot" style="background:#1a2a6c;"></div> Mixed Tradition</div>
  <div class="legend-item"><div class="legend-dot" style="background:#c0392b;"></div> Tribal / Yörük</div>
</div>

<!-- MAP -->
<div id="map-wrapper">
  <div id="carpet-map"></div>

  <!-- INFO PANEL -->
  <div id="info-card">
    <button id="close-btn" onclick="closeCard()">✕</button>
    <div id="region-name"></div>
    <div id="region-badges"></div>
    <span class="info-label">📍 Province</span>
    <div class="info-text" id="region-province"></div>
    <span class="info-label">🧵 Type</span>
    <div class="info-text" id="region-type"></div>
    <span class="info-label">🎨 Characteristics</span>
    <div class="info-text" id="region-desc"></div>
    <span class="info-label">🌿 Materials</span>
    <div class="info-text" id="region-materials"></div>
    <div id="region-link-wrap" style="margin-top:12px;"></div>
  </div>
</div>

<script>
const map = L.map('carpet-map').setView([39.0, 35.5], 6);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
  attribution: '© OpenStreetMap contributors',
  maxZoom: 12
}).addTo(map);

// Renk → marker ikonu
function makeIcon(color) {
  const svg = `<svg xmlns="http://www.w3.org/2000/svg" width="28" height="36" viewBox="0 0 28 36">
    <path d="M14 0C6.27 0 0 6.27 0 14c0 9.6 14 22 14 22S28 23.6 28 14C28 6.27 21.73 0 14 0z" fill="${color}" stroke="white" stroke-width="2"/>
    <circle cx="14" cy="14" r="5" fill="white" opacity="0.85"/>
  </svg>`;
  return L.divIcon({
    html: svg, className: '', iconSize: [28, 36], iconAnchor: [14, 36], popupAnchor: [0, -36]
  });
}

const COLORS = {
  imperial: '#d4af37',
  carpet:   '#8b0000',
  kilim:    '#2e8b57',
  mixed:    '#1a2a6c',
  tribal:   '#c0392b'
};

const regions = [
  {
    name: "Hereke",
    lat: 40.80, lng: 29.63,
    province: "Kocaeli (İzmit)",
    category: "imperial",
    types: ["Silk Carpet", "Wool Carpet"],
    desc: "The pinnacle of Ottoman weaving. Founded as the Imperial Factory in 1843 by Sultan Abdülmecid I. Silk-on-silk carpets with up to 2.25 million knots/m². Gift of choice for visiting royalty.",
    materials: "Pure silk, fine wool, occasionally gold & silver thread",
    link: "./en/hereke"
  },
  {
    name: "Uşak",
    lat: 38.68, lng: 29.41,
    province: "Uşak",
    category: "carpet",
    types: ["Medallion Carpet", "Star Carpet"],
    desc: "One of Turkey's oldest and most prestigious carpet centres. Famous for Medallion and Star Uşak carpets seen in Renaissance paintings (Holbein, Lotto). Production spans 500+ years.",
    materials: "Wool on wool, natural dyes (madder, indigo)",
    link: null
  },
  {
    name: "Gördes (Ghiordes)",
    lat: 38.93, lng: 28.28,
    province: "Manisa",
    category: "carpet",
    types: ["Prayer Rug", "Gördes Knot"],
    desc: "Birthplace of the Gördes (Turkish/Symmetrical) double knot — the most fundamental technique in Anatolian carpet weaving. Famous for its distinctive prayer rugs with double-ended niches.",
    materials: "Wool, cotton warp, vegetable dyes",
    link: null
  },
  {
    name: "Bergama",
    lat: 39.12, lng: 27.18,
    province: "İzmir",
    category: "carpet",
    types: ["Geometric Carpet", "Tribal"],
    desc: "Bold geometric designs rooted in ancient Anatolian tradition. Strong primary colours — red, blue, ivory. Among the oldest carpet-making centres in western Anatolia.",
    materials: "Wool on wool, natural dyes",
    link: null
  },
  {
    name: "Yağcıbedir",
    lat: 39.24, lng: 28.13,
    province: "Balıkesir (Sındırgı / Bigadiç)",
    category: "tribal",
    types: ["Tribal Carpet", "Yörük"],
    desc: "Woven by Yağcıbedir Yörüks — nomadic Oğuz Turks. Only 4 colours used: navy, red, white, and rarely black. Motifs are bold, sparse, and symbolic. Kökboya (madder) gives the legendary red.",
    materials: "100% wool, madder red, indigo navy, mineral dyes",
    link: null
  },
  {
    name: "Kula",
    lat: 38.55, lng: 28.65,
    province: "Manisa",
    category: "carpet",
    types: ["Floral Carpet", "Prayer Rug"],
    desc: "Known as 'Mazarlik (Cemetery) Carpets' — featuring architectural motifs, cypress trees, and floral fields. Soft, faded colours. Highly sought by collectors.",
    materials: "Wool, soft vegetable dyes",
    link: null
  },
  {
    name: "Ladik",
    lat: 37.35, lng: 32.90,
    province: "Konya",
    category: "carpet",
    types: ["Prayer Rug", "Medallion"],
    desc: "Famous for elegant prayer rugs with a distinctive tulip border. Ladik masters were among those summoned to Hereke in 1891 to establish the Imperial carpet tradition.",
    materials: "Wool on wool, madder, indigo",
    link: null
  },
  {
    name: "Konya",
    lat: 37.87, lng: 32.49,
    province: "Konya",
    category: "mixed",
    types: ["Seljuk Carpet", "Kilim", "Prayer Rug"],
    desc: "Capital of Seljuk carpet tradition. The oldest surviving Anatolian carpets (13th century) were found in Konya's Alaeddin Mosque. Strong geometric tradition, kilim and carpet.",
    materials: "Wool, natural dyes, goat hair",
    link: null
  },
  {
    name: "Kayseri",
    lat: 38.73, lng: 35.49,
    province: "Kayseri",
    category: "carpet",
    types: ["Commercial Carpet", "Fine Weave"],
    desc: "Major commercial carpet production centre. Known for fine-quality wool carpets and silk blends. Bünyan (nearby) produces distinctive commercial carpets with floral Ottoman patterns.",
    materials: "Wool, silk blends, synthetic and natural dyes",
    link: null
  },
  {
    name: "Sivas",
    lat: 39.75, lng: 37.02,
    province: "Sivas",
    category: "carpet",
    types: ["Şal Carpet", "Prison Carpet"],
    desc: "Home of the legendary Sivas Şal carpet with fine floral designs. Also famous for the Sivas Prison carpet — inmates weaved Hereke-style carpets of extraordinary quality. Sivas masters helped establish Hereke in 1891.",
    materials: "Wool, silk, natural and synthetic dyes",
    link: null
  },
  {
    name: "Isparta",
    lat: 37.76, lng: 30.55,
    province: "Isparta",
    category: "carpet",
    types: ["Commercial Carpet", "Export Quality"],
    desc: "Turkey's largest commercial carpet production centre. Western floral designs, rose motifs (Isparta is Turkey's rose capital). Major exporter to European markets.",
    materials: "Wool on cotton, synthetic dyes for commercial, natural for premium",
    link: null
  },
  {
    name: "Döşemealtı",
    lat: 37.05, lng: 30.55,
    province: "Antalya",
    category: "tribal",
    types: ["Yörük Carpet", "Tribal Kilim"],
    desc: "Woven by Yörük nomads of the Taurus mountains. Bold geometric designs in strong reds and blues. Döşemealtı is also famous as a restoration centre — carpets from across Turkey are brought here for washing, repair, and sun-bleaching in open fields.",
    materials: "Wool on wool, natural vegetable dyes, kökboya",
    link: null
  },
  {
    name: "Milas",
    lat: 37.31, lng: 27.79,
    province: "Muğla",
    category: "carpet",
    types: ["Prayer Rug", "Floral"],
    desc: "Distinctive for its soft pastel palette — unique among Anatolian carpets. Milas prayer rugs feature a characteristic yellow-gold ground with floral borders. Prized by collectors for their unusual colour harmony.",
    materials: "Wool, soft natural dyes (saffron, pomegranate)",
    link: null
  },
  {
    name: "Çanakkale / Ezine",
    lat: 40.15, lng: 26.41,
    province: "Çanakkale",
    category: "tribal",
    types: ["Tribal Carpet", "Yörük"],
    desc: "Thick-pile tribal carpets with bold geometric designs. Strong reds and blues. Çanakkale carpets are among the most robust Anatolian tribal pieces — woven for hard use, not display.",
    materials: "Coarse wool, madder, indigo, natural dyes",
    link: null
  },
  {
    name: "Niğde / Taşpınar",
    lat: 37.97, lng: 34.68,
    province: "Niğde",
    category: "carpet",
    types: ["Fine Carpet", "Medallion"],
    desc: "Taşpınar (near Niğde) produces fine-quality carpets with distinctive medallion designs and a unique warm colour palette. Less well-known internationally but highly regarded by specialists.",
    materials: "Wool, natural dyes",
    link: null
  },
  {
    name: "Kırşehir",
    lat: 39.14, lng: 34.16,
    province: "Kırşehir",
    category: "carpet",
    types: ["Prayer Rug", "Runner"],
    desc: "Known for prayer rugs and long runners (yolluk). Kırşehir carpets have a characteristic soft wool and warm red-green palette. Often found in religious settings.",
    materials: "Wool on wool, madder red, natural dyes",
    link: null
  },
  {
    name: "Kars",
    lat: 40.60, lng: 43.09,
    province: "Kars",
    category: "mixed",
    types: ["Kilim", "Sumak", "Zili", "Çiği"],
    desc: "A livestock region with a rich flat-weave tradition: kilim, sumak, zili, çerim, and çiği kilim are all produced here. Caucasian and Turkish motifs blend in bold geometric patterns. Strong animal husbandry means excellent raw wool.",
    materials: "Wool, goat hair, natural dyes",
    link: "./en/sumak"
  },
  {
    name: "Şarkışla / Şirvan",
    lat: 39.35, lng: 37.49,
    province: "Sivas",
    category: "kilim",
    types: ["Kilim", "Şarkışla Kilim"],
    desc: "Famous for Şarkışla kilims — bold geometric designs with strong primary colours. The Şirvan style (also found in Azerbaijan) features intricate diamond and medallion compositions in flat-weave.",
    materials: "Wool, natural and synthetic dyes",
    link: "./en/kilim"
  },
  {
    name: "Yahyalı",
    lat: 38.10, lng: 36.06,
    province: "Kayseri",
    category: "carpet",
    types: ["Geometric Carpet", "Village"],
    desc: "Village carpets with strong geometric designs and vibrant colours. Yahyalı carpets are known for their durable construction and bold, uncompromising patterns.",
    materials: "Wool on wool, natural dyes",
    link: null
  },
  {
    name: "Ayvacık",
    lat: 39.59, lng: 26.40,
    province: "Çanakkale",
    category: "tribal",
    types: ["Tribal", "Natural Dye Project"],
    desc: "Home of the DOBAG project (1981) — the first initiative to revive 100% natural dye carpet weaving in Turkey. Ayvacık carpets are internationally recognised for their authentic vegetable dyes and traditional Yörük patterns.",
    materials: "100% natural-dyed wool, traditional vegetable dyes only",
    link: null
  }
];

// Markerları ekle
regions.forEach(r => {
  const color = COLORS[r.category];
  const marker = L.marker([r.lat, r.lng], { icon: makeIcon(color) }).addTo(map);
  marker.on('click', () => showCard(r));
});

function showCard(r) {
  document.getElementById('region-name').textContent = '📍 ' + r.name;
  document.getElementById('region-province').textContent = r.province;
  document.getElementById('region-type').textContent = r.types.join(' · ');
  document.getElementById('region-desc').textContent = r.desc;
  document.getElementById('region-materials').textContent = r.materials;

  // Badges
  const badgeEl = document.getElementById('region-badges');
  const color = COLORS[r.category];
  const labels = { imperial:'Imperial', carpet:'Carpet', kilim:'Kilim', mixed:'Mixed', tribal:'Tribal / Yörük' };
  badgeEl.innerHTML = `<span class="type-badge" style="background:${color}">${labels[r.category]}</span>`;

  // Link
  const linkWrap = document.getElementById('region-link-wrap');
  if (r.link) {
    linkWrap.innerHTML = `<a href="{{ site.baseurl }}${r.link}" style="display:inline-block; background:#8b0000; color:white; padding:8px 18px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.85em;">Explore ${r.name} →</a>`;
  } else {
    linkWrap.innerHTML = '';
  }

  document.getElementById('info-card').classList.add('visible');
}

function closeCard() {
  document.getElementById('info-card').classList.remove('visible');
}
</script>

<!-- REGION CARDS -->
<div style="margin-top: 40px;">
  <h2 style="color: #8b0000; border-bottom: 3px solid #d4af37; padding-bottom: 8px; font-family: Georgia, serif;">🧶 All Weaving Regions at a Glance</h2>
  <div class="region-grid">

    <div class="region-card" style="border-left-color: #d4af37;">
      <h3 style="color:#8b6914;">🏰 Hereke — Kocaeli</h3>
      <p>Imperial silk carpets. Founded 1843 by Sultan Abdülmecid. Up to 2.25M knots/m². The finest carpets ever woven.</p>
    </div>
    <div class="region-card" style="border-left-color: #8b0000;">
      <h3 style="color:#8b0000;">🔴 Uşak</h3>
      <p>500 years of Medallion & Star carpets. Seen in Renaissance paintings. Major Ottoman export.</p>
    </div>
    <div class="region-card" style="border-left-color: #8b0000;">
      <h3 style="color:#8b0000;">🔴 Gördes (Ghiordes)</h3>
      <p>Birthplace of the Turkish double knot. Famous prayer rugs with double-ended niches.</p>
    </div>
    <div class="region-card" style="border-left-color: #c0392b;">
      <h3 style="color:#c0392b;">🟤 Yağcıbedir — Balıkesir</h3>
      <p>Only 4 colours: navy, red, white, black. Yörük tribal carpets. Madder-dyed reds that brighten with age.</p>
    </div>
    <div class="region-card" style="border-left-color: #c0392b;">
      <h3 style="color:#c0392b;">🟤 Döşemealtı — Antalya</h3>
      <p>Taurus mountain Yörüks. Bold geometric designs. Also Turkey's carpet washing & restoration capital.</p>
    </div>
    <div class="region-card" style="border-left-color: #1a2a6c;">
      <h3 style="color:#1a2a6c;">🔵 Kars</h3>
      <p>Rich flat-weave tradition: kilim, sumak, zili, çiği. Caucasian + Turkish motifs. Excellent raw wool.</p>
    </div>
    <div class="region-card" style="border-left-color: #2e8b57;">
      <h3 style="color:#2e8b57;">🟢 Şarkışla / Şirvan — Sivas</h3>
      <p>Bold geometric kilims. Şirvan medallion style. Strong primary colours in flat-weave.</p>
    </div>
    <div class="region-card" style="border-left-color: #8b0000;">
      <h3 style="color:#8b0000;">🔴 Milas — Muğla</h3>
      <p>Unique pastel palette. Saffron-gold prayer rugs. Prized by collectors for unusual colour harmony.</p>
    </div>
    <div class="region-card" style="border-left-color: #8b0000;">
      <h3 style="color:#8b0000;">🔴 Niğde / Taşpınar</h3>
      <p>Fine medallion carpets. Warm colour palette. Specialist favourite, less known internationally.</p>
    </div>
    <div class="region-card" style="border-left-color: #c0392b;">
      <h3 style="color:#c0392b;">🟤 Ayvacık — Çanakkale</h3>
      <p>Home of the DOBAG natural dye revival project (1981). 100% vegetable-dyed Yörük carpets.</p>
    </div>
    <div class="region-card" style="border-left-color: #8b0000;">
      <h3 style="color:#8b0000;">🔴 Sivas</h3>
      <p>Şal carpets & legendary Prison carpets. Sivas masters helped found Hereke in 1891.</p>
    </div>
    <div class="region-card" style="border-left-color: #1a2a6c;">
      <h3 style="color:#1a2a6c;">🔵 Konya</h3>
      <p>Oldest surviving Anatolian carpets (13th c., Seljuk). Mixed kilim and carpet tradition.</p>
    </div>

  </div>
</div>

<hr style="border: none; border-top: 2px dashed #d4af37; margin: 40px 0;">

<div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center;">
  <a href="{{ site.baseurl }}/en/hereke"   style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🏰 Imperial Hereke →</a>
  <a href="{{ site.baseurl }}/en/kilim"    style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">📐 Kilim Guide →</a>
  <a href="{{ site.baseurl }}/en/sumak"    style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🌀 Sumak Technique →</a>
  <a href="{{ site.baseurl }}/cleaning"    style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🧹 Care Guide →</a>
</div>

