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
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Döşemealtı Carpets | Global Carpet Guide</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,300;1,9..144,400&family=Outfit:wght@200;300;400;500&display=swap" rel="stylesheet">

<style>
:root {
  --bg:      #f7f6f3;
  --bg2:     #efede8;
  --bg3:     #e6e3dc;
  --line:    #d8d4cb;
  --line2:   #bdb9b0;
  --ink:     #1c1b18;
  --ink2:    #4a4840;
  --ink3:    #7c7970;
  --gold:    #b8900a;
  --gold-lt: #d4aa30;
  --accent:  #5a3e2b;
}

*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}

body{
  background:var(--bg);
  background-image:url("data:image/svg+xml,%3Csvg width='24' height='24' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='1' cy='1' r='.55' fill='%23c8c4bc' fill-opacity='.32'/%3E%3C/svg%3E");
  color:var(--ink);
  font-family:'Outfit',sans-serif;
  font-weight:300;
  min-height:100vh;
  overflow-x:hidden;
}

/* ── NAV ── */
nav{
  background:var(--ink);
  padding:.75rem 2rem;
  display:flex;align-items:center;gap:1.5rem;
  flex-wrap:wrap;
}
.nav-logo{
  font-family:'Fraunces',serif;
  font-size:1rem;font-weight:400;
  color:#f0e8d5;letter-spacing:.04em;
  text-decoration:none;margin-right:auto;
}
.nav-link{
  font-size:.68rem;font-weight:400;
  letter-spacing:.12em;text-transform:uppercase;
  color:rgba(240,232,213,.6);text-decoration:none;
  transition:color .2s;
}
.nav-link:hover{color:#f0e8d5}
.nav-link.active{color:var(--gold-lt)}
@media(max-width:600px){nav{padding:.65rem 1rem;gap:1rem}}

/* ── HEADER ── */
header{
  text-align:center;
  padding:3.5rem 1.5rem 2.5rem;
  border-bottom:1px solid var(--line);
  position:relative;overflow:hidden;
}
header::before{
  content:'';position:absolute;top:0;left:0;right:0;bottom:0;
  background:radial-gradient(ellipse at 50% 0%,rgba(184,144,10,.08) 0%,transparent 65%);
  pointer-events:none;
}
@media(max-width:500px){header{padding:2rem 1rem 1.5rem}}

.breadcrumb{
  font-size:.65rem;font-weight:400;
  letter-spacing:.2em;text-transform:uppercase;
  color:var(--ink3);margin-bottom:1.4rem;
  display:flex;align-items:center;justify-content:center;gap:.5rem;
}
.breadcrumb a{color:var(--ink3);text-decoration:none;transition:color .2s}
.breadcrumb a:hover{color:var(--ink2)}
.breadcrumb span{color:var(--line2)}

/* decorative strip */
.deco-strip{
  display:flex;justify-content:center;margin:0 auto 1.4rem;
  width:fit-content;
}

h1{
  font-family:'Fraunces',serif;
  font-size:clamp(2.4rem,6vw,4.6rem);
  font-weight:300;letter-spacing:.01em;line-height:1.06;
  color:var(--ink);margin-bottom:.55rem;
}
h1 em{font-style:italic;color:var(--accent)}
.subtitle{font-size:.92rem;font-weight:200;letter-spacing:.08em;color:var(--ink3);margin-bottom:.25rem}
.aka{font-family:'Fraunces',serif;font-size:.92rem;font-style:italic;color:var(--ink3)}

/* ── MAIN ── */
main{
  max-width:1100px;margin:0 auto;
  padding:3rem 2rem 5rem;
}
@media(max-width:700px){main{padding:1.5rem 1rem 3rem}}

/* ── INTRO ── */
.intro-grid{
  display:grid;grid-template-columns:1fr 1fr;
  gap:2.5rem 4rem;align-items:start;
  margin-bottom:3.5rem;
}
@media(max-width:700px){.intro-grid{grid-template-columns:1fr;gap:1.5rem}}

.section-label{
  font-family:'Outfit',sans-serif;font-size:.62rem;font-weight:500;
  letter-spacing:.3em;text-transform:uppercase;color:var(--ink3);
  margin-bottom:.9rem;display:flex;align-items:center;gap:.8rem;
}
.section-label::after{content:'';flex:1;height:1px;background:linear-gradient(to right,var(--line),transparent)}

h2{
  font-family:'Fraunces',serif;
  font-size:1.85rem;font-weight:300;line-height:1.2;
  margin-bottom:1rem;color:var(--ink);
}
h2 em{font-style:italic;color:var(--accent)}

p{font-size:.9rem;line-height:1.9;color:var(--ink2);margin-bottom:1rem}
p strong{color:var(--ink);font-weight:400}

/* fact strip */
.fact-strip{display:grid;grid-template-columns:1fr 1fr;gap:.65rem;margin:1.5rem 0}
.fact-card{background:var(--bg2);border:1px solid var(--line);border-radius:3px;padding:.85rem .95rem}
.fact-card .fv{font-family:'Fraunces',serif;font-size:1.5rem;font-weight:400;color:var(--ink);line-height:1;margin-bottom:.2rem}
.fact-card .fl{font-size:.7rem;letter-spacing:.06em;color:var(--ink3);font-weight:300}

/* ── PHOTO ANALYSIS CARDS ── */
.analysis-section{margin-bottom:3.5rem}

.analysis-section > h2{
  text-align:center;font-size:1.6rem;margin-bottom:.5rem;
}
.analysis-section > .section-label{
  justify-content:center;max-width:300px;margin:0 auto 2rem;
}
.analysis-section > .section-label::after{display:none}
.analysis-section > .section-label::before{
  content:'';flex:1;height:1px;background:linear-gradient(to left,var(--line),transparent)
}

.photo-cards{
  display:grid;grid-template-columns:1fr 1fr;
  gap:2rem;
}
@media(max-width:700px){.photo-cards{grid-template-columns:1fr;gap:1.5rem}}

.photo-card{
  background:var(--bg2);border:1px solid var(--line);border-radius:4px;
  overflow:hidden;
  transition:border-color .2s;
}
.photo-card:hover{border-color:var(--line2)}

/* photo placeholder / real image */
.photo-wrap{
  width:100%;aspect-ratio:4/3;
  overflow:hidden;position:relative;
  background:var(--bg3);
  cursor:zoom-in;
}
.photo-wrap img{
  width:100%;height:100%;object-fit:cover;
  display:block;transition:transform .4s ease;
}
.photo-wrap:hover img{transform:scale(1.04)}
.photo-wrap .zoom-hint{
  position:absolute;bottom:.6rem;right:.6rem;
  background:rgba(28,27,24,.6);color:rgba(240,232,213,.85);
  font-size:.6rem;font-weight:400;letter-spacing:.1em;text-transform:uppercase;
  padding:.25rem .55rem;border-radius:2px;pointer-events:none;
  opacity:0;transition:opacity .2s;
}
.photo-wrap:hover .zoom-hint{opacity:1}

.card-body{padding:1.2rem 1.25rem 1.4rem}

.card-title{
  font-family:'Fraunces',serif;
  font-size:1.3rem;font-weight:400;
  color:var(--ink);margin-bottom:.3rem;line-height:1.2;
}
.card-subtitle{
  font-size:.68rem;font-weight:500;letter-spacing:.15em;text-transform:uppercase;
  color:var(--ink3);margin-bottom:1rem;
}

.card-desc{font-size:.87rem;line-height:1.85;color:var(--ink2);margin-bottom:1.1rem}
.card-desc strong{color:var(--ink);font-weight:400}

/* motif list inside card */
.motif-list{list-style:none;margin:0;border-top:1px solid var(--line);padding-top:.9rem}
.motif-list li{
  display:grid;grid-template-columns:auto 1fr;
  gap:.6rem .75rem;
  padding:.45rem 0;
  border-bottom:1px solid var(--line);
  font-size:.84rem;line-height:1.55;
  align-items:baseline;
}
.motif-list li:last-child{border-bottom:none}
.motif-dot{
  width:8px;height:8px;border-radius:50%;
  background:var(--accent);margin-top:.35rem;flex-shrink:0;
}
.motif-name{color:var(--ink);font-weight:400}
.motif-name + span{display:block;color:var(--ink3);font-size:.8rem;line-height:1.5;margin-top:.1rem}

/* tech note */
.tech-note{
  margin-top:.9rem;padding:.75rem 1rem;
  background:var(--bg);border:1px solid var(--line);border-radius:3px;
  font-size:.8rem;line-height:1.7;color:var(--ink3);
  font-style:italic;
}
.tech-note strong{color:var(--ink2);font-style:normal;font-weight:400}

/* ── STEP DIAGRAM ── */
.technique-section{
  margin-bottom:3.5rem;
  border-top:1px solid var(--line);padding-top:3rem;
}
.technique-section > h2{text-align:center;margin-bottom:.5rem}
.technique-section > p{text-align:center;max-width:600px;margin:0 auto 2rem}

/* step tabs */
.step-pills{display:flex;gap:.32rem;flex-wrap:wrap;margin-bottom:1.2rem;justify-content:center}
.step-pill{
  background:none;border:1px solid var(--line);border-radius:2px;
  padding:.28rem .8rem;
  font-family:'Outfit',sans-serif;font-size:.62rem;font-weight:400;
  letter-spacing:.1em;text-transform:uppercase;
  color:var(--ink3);cursor:pointer;transition:all .2s;
}
.step-pill:hover{border-color:var(--line2);color:var(--ink2)}
.step-pill.sp-active{background:var(--ink);border-color:var(--ink);color:var(--bg)}

.diagram-wrap{
  max-width:640px;margin:0 auto;
}
.svg-wrap{
  background:var(--bg2);border:1px solid var(--line);border-radius:3px;
  overflow:hidden;aspect-ratio:16/9;
}
.svg-wrap svg{width:100%;height:100%;display:block}
.step-desc{
  margin-top:1rem;padding:.95rem 1.1rem;
  background:var(--bg2);border-left:2px solid var(--line2);
  font-size:.88rem;line-height:1.82;color:var(--ink2);min-height:4rem;
}
.step-desc strong{color:var(--ink);font-weight:500}
.nav-row{display:flex;align-items:center;justify-content:space-between;margin-top:.9rem}
.nav-btn{
  background:none;border:1px solid var(--line);border-radius:2px;
  padding:.42rem .95rem;font-family:'Outfit',sans-serif;font-size:.65rem;
  font-weight:400;letter-spacing:.12em;text-transform:uppercase;
  color:var(--ink3);cursor:pointer;transition:all .2s;
}
.nav-btn:hover:not(:disabled){border-color:var(--line2);color:var(--ink)}
.nav-btn:disabled{opacity:.25;cursor:default}
.progress-bar{flex:1;height:2px;background:var(--line);margin:0 1rem;border-radius:1px;overflow:hidden;position:relative}
.progress-fill{position:absolute;top:0;left:0;height:100%;background:var(--ink);border-radius:1px;transition:width .35s cubic-bezier(.4,0,.2,1)}
.step-counter{font-size:.65rem;font-weight:400;letter-spacing:.1em;color:var(--ink3);white-space:nowrap}

/* ── COMPARE TABLE ── */
.compare-section{border-top:1px solid var(--line);padding-top:3rem;margin-bottom:3.5rem}
.compare-section > h2{text-align:center;margin-bottom:.5rem}
.compare-section > p{text-align:center;max-width:560px;margin:0 auto 2rem;font-size:.88rem}
.table-scroll{width:100%;overflow-x:auto;-webkit-overflow-scrolling:touch;border:1px solid var(--line);border-radius:3px}
.compare-table{width:100%;min-width:440px;border-collapse:collapse;font-size:.83rem}
.compare-table thead tr{border-bottom:1px solid var(--line2)}
.compare-table th{
  font-family:'Outfit',sans-serif;font-size:.6rem;font-weight:500;
  letter-spacing:.18em;text-transform:uppercase;color:var(--ink3);
  padding:.55rem .85rem;text-align:left;white-space:nowrap;background:var(--bg2);
}
.compare-table td{padding:.55rem .85rem;border-bottom:1px solid var(--line);color:var(--ink2);vertical-align:top;line-height:1.55}
.compare-table td:first-child{color:var(--ink);font-weight:400;white-space:nowrap}
.compare-table tr:last-child td{border-bottom:none}
.compare-table .hi td{background:var(--bg2)}

/* pull quote */
.pull-quote{
  margin:2rem 0;padding:1.4rem 1.8rem;
  border-top:1px solid var(--line);border-bottom:1px solid var(--line);position:relative;
}
.pull-quote::before{content:'\201C';font-family:'Fraunces',serif;font-size:5rem;color:var(--line2);position:absolute;top:-.6rem;left:.7rem;line-height:1}
.pull-quote p{font-family:'Fraunces',serif;font-size:1.15rem;font-style:italic;line-height:1.65;color:var(--ink);margin-bottom:.4rem}
.pull-quote cite{font-size:.7rem;letter-spacing:.1em;color:var(--ink3)}

/* lightbox */
.lightbox{
  display:none;position:fixed;inset:0;z-index:1000;
  background:rgba(28,27,24,.9);
  align-items:center;justify-content:center;padding:2rem;
}
.lightbox.open{display:flex}
.lightbox img{max-width:90vw;max-height:85vh;object-fit:contain;border-radius:3px}
.lightbox-close{
  position:absolute;top:1.5rem;right:1.5rem;
  background:none;border:1px solid rgba(240,232,213,.3);border-radius:2px;
  color:rgba(240,232,213,.8);font-size:.75rem;font-weight:400;
  letter-spacing:.12em;text-transform:uppercase;
  padding:.45rem 1rem;cursor:pointer;transition:all .2s;
  font-family:'Outfit',sans-serif;
}
.lightbox-close:hover{border-color:rgba(240,232,213,.8);color:#f0e8d5}
.lightbox-caption{
  position:absolute;bottom:1.5rem;left:50%;transform:translateX(-50%);
  font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;
  color:rgba(240,232,213,.55);font-family:'Outfit',sans-serif;
}

/* footer */
footer{
  text-align:center;padding:2.5rem 1rem;
  border-top:1px solid var(--line);
  font-size:.72rem;letter-spacing:.1em;color:var(--ink3);
}

/* animations */
@keyframes drawPath{from{stroke-dashoffset:var(--len)}to{stroke-dashoffset:0}}
@keyframes fadeUp{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
.anim-path{stroke-dasharray:var(--len);stroke-dashoffset:var(--len)}
</style>
</head>
<body>

<!-- ── NAV ── -->
<nav>
  <a class="nav-logo" href="https://fmemo75-prog.github.io/carpetguide/">🌍 Global Carpet Guide</a>
  <a class="nav-link" href="https://fmemo75-prog.github.io/carpetguide/">Home</a>
  <a class="nav-link" href="https://fmemo75-prog.github.io/carpetguide/flat-viewing">Weaving Techniques</a>
  <a class="nav-link active" href="#">Döşemealtı</a>
  <a class="nav-link" href="https://fmemo75-prog.github.io/carpetguide/en/materials">Materials</a>
  <a class="nav-link" href="https://fmemo75-prog.github.io/carpetguide/en/hereke">Imperial Hereke</a>
</nav>

<!-- ── HEADER ── -->
<header>
  <div class="breadcrumb">
    <a href="https://fmemo75-prog.github.io/carpetguide/">Home</a>
    <span>/</span>
    <a href="https://fmemo75-prog.github.io/carpetguide/en/handknotted">Hand-Knotted</a>
    <span>/</span>
    Döşemealtı
  </div>

  <!-- decorative strip: döşemealtı geometric motif pattern -->
  <div class="deco-strip">
    <svg viewBox="0 0 320 28" width="320" height="28" xmlns="http://www.w3.org/2000/svg">
      <rect width="320" height="28" fill="var(--bg2)" rx="2"/>
      <!-- base rows -->
      <rect y="0"  width="320" height="5" fill="#c8aa7a" opacity=".4"/>
      <rect y="23" width="320" height="5" fill="#c8aa7a" opacity=".4"/>
      <!-- geometric hook border -->
      <polyline points="0,14 20,6 40,14 60,6 80,14 100,6 120,14 140,6 160,14 180,6 200,14 220,6 240,14 260,6 280,14 300,6 320,14"
        fill="none" stroke="#5a3e2b" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity=".75"/>
      <!-- dots at peaks -->
      <circle cx="20"  cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="60"  cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="100" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="140" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="180" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="220" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="260" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
      <circle cx="300" cy="6"  r="2.5" fill="#b8900a" opacity=".8"/>
    </svg>
  </div>

  <h1><em>Döşemealtı</em> Carpets</h1>
  <p class="subtitle">Village Rugs of the Taurus Mountain Foothills · Antalya Region</p>
  <p class="aka">Hand-knotted · Wool on Wool · Living tribal tradition</p>
</header>

<!-- ── MAIN ── -->
<main>

  <!-- ── INTRO ── -->
  <div class="intro-grid">
    <div>
      <div class="section-label">Origins</div>
      <h2>Where the <em>Taurus meets</em> the Mediterranean</h2>
      <p>
        Döşemealtı carpets come from a cluster of villages on the slopes of the western Taurus mountains,
        just north of Antalya. The name literally means <strong>"under the floor stones"</strong> — a
        reference to the rugged mountain terrain that shaped the weavers' world.
      </p>
      <p>
        Woven by Yörük semi-nomadic communities, these carpets preserve an unbroken lineage of
        <strong>geometric tribal design</strong> stretching back several centuries. Unlike the urban
        workshop carpets of İznik or Uşak, Döşemealtı rugs are domestic objects: woven by women for
        their own households, carrying personal and communal symbolism in every row.
      </p>
    </div>

    <div>
      <div class="fact-strip">
        <div class="fact-card">
          <div class="fv">Wool/Wool</div>
          <div class="fl">warp, weft and pile all hand-spun wool</div>
        </div>
        <div class="fact-card">
          <div class="fv">Turkish</div>
          <div class="fl">symmetrical (Ghiordes) knot throughout</div>
        </div>
        <div class="fact-card">
          <div class="fv">30–80</div>
          <div class="fl">knots per dm² — medium-coarse pile</div>
        </div>
        <div class="fact-card">
          <div class="fv">Natural</div>
          <div class="fl">plant and mineral dyes — madder, indigo, oak gall</div>
        </div>
      </div>

      <div class="pull-quote" style="margin-top:1.5rem">
        <p>A Döşemealtı carpet is not made for the market — it is made for the home.</p>
        <cite>— Traditional Yörük weaving principle</cite>
      </div>
    </div>
  </div>

  <!-- ── PHOTO ANALYSIS ── -->
  <div class="analysis-section">
    <div class="section-label" style="justify-content:center;max-width:320px;margin:0 auto .5rem">
      Carpet Analysis
    </div>
    <h2 style="text-align:center">Two <em>examples</em> examined</h2>
    <p style="text-align:center;max-width:540px;margin:.6rem auto 2rem;font-size:.88rem;color:var(--ink3)">
      Each piece below is analysed for its design structure, key motifs, and technical character.
    </p>

    <div class="photo-cards">

      <!-- ── CARD 1 ── -->
      <div class="photo-card">
        <div class="photo-wrap" onclick="openLightbox('photo1.jpg','Example 1 — Döşemealtı Village Carpet')">
          <img src="photo1.jpg" alt="Döşemealtı carpet example 1 — geometric field design"
               onerror="this.parentElement.style.background='var(--bg3)';this.style.display='none'"/>
          <span class="zoom-hint">Click to enlarge</span>
        </div>
        <div class="card-body">
          <div class="card-subtitle">Example 1</div>
          <h3 class="card-title">The Geometric Field</h3>
          <p class="card-desc">
            A classic Döşemealtı field composition built entirely from <strong>geometric repeat units</strong>.
            The bold central field is enclosed by a triple-border system — the characteristic framing
            device of the Taurus village tradition.
          </p>

          <ul class="motif-list">
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Central Medallion (Madalyon)</span>
                <span>The stepped octagonal medallion is the compositional anchor of the piece. Its sharp angles — characteristic of wool-on-wool weaving — represent <strong>tribal identity and territorial belonging</strong>.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Running Hook Border (Çengel)</span>
                <span>The inner border carries a continuous chain of S-shaped hooks — an ancient apotropaic symbol used to <strong>protect the household from the evil eye</strong>.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Madder Red Field</span>
                <span>The dominant field colour is obtained from the <em>Rubia tinctorum</em> root (madder). In Döşemealtı tradition, deep madder red signals <strong>strength and vitality</strong> and is the most prized dye colour.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Corner Pieces (Köşebent)</span>
                <span>Quarter-medallion forms fill the field corners, completing the visual symmetry. These also carry small <strong>stylised flower or diamond</strong> sub-motifs specific to Döşemealtı village identity.</span>
              </div>
            </li>
          </ul>

          <div class="tech-note">
            <strong>Technical note:</strong> Medium pile height with hand-spun local wool gives this piece
            the characteristic slightly irregular surface that distinguishes authentic village weaving from
            workshop production. Asymmetric selvedge width is common and accepted in the tradition.
          </div>
        </div>
      </div>

      <!-- ── CARD 2 ── -->
      <div class="photo-card">
        <div class="photo-wrap" onclick="openLightbox('photo2.jpg','Example 2 — Döşemealtı Prayer Rug')">
          <img src="photo2.jpg" alt="Döşemealtı carpet example 2 — prayer rug composition"
               onerror="this.parentElement.style.background='var(--bg3)';this.style.display='none'"/>
          <span class="zoom-hint">Click to enlarge</span>
        </div>
        <div class="card-body">
          <div class="card-subtitle">Example 2</div>
          <h3 class="card-title">The Prayer Format</h3>
          <p class="card-desc">
            The <em>seccade</em> (prayer rug) format requires the weaver to place a <strong>mihrab
            arch</strong> — a stylised niche pointing toward Mecca — as the central compositional element.
            In Döşemealtı hands, the arch takes on boldly angular, geometric character.
          </p>

          <ul class="motif-list">
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Mihrab Arch (Mihrap)</span>
                <span>The stepped niche arch dominates the field. Unlike the rounded arches of Ottoman court carpets, the Döşemealtı mihrab is <strong>angular and jagged</strong> — a direct result of the coarser wool-on-wool knotting grid.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Lamp (Kandil) Motif</span>
                <span>A pendant hanging from the apex of the arch represents the <strong>divine light of the mosque lamp</strong>. This is one of the most consistent motifs across all Anatolian prayer rug traditions.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Tree of Life (Hayat Ağacı)</span>
                <span>Stylised trees or branching forms inside the niche field represent the <strong>connection between earth and paradise</strong>. In Döşemealtı prayer rugs these are geometricised into stacked diamond or lozenge forms.</span>
              </div>
            </li>
            <li>
              <div class="motif-dot"></div>
              <div>
                <span class="motif-name">Indigo Spandrels</span>
                <span>The triangular field areas flanking the arch are filled with <strong>indigo blue</strong> — derived from <em>Indigofera tinctoria</em>. Indigo in this context represents <strong>sky, divinity, and spiritual aspiration</strong>.</span>
              </div>
            </li>
          </ul>

          <div class="tech-note">
            <strong>Technical note:</strong> Prayer rugs typically have a lower knot count than field
            carpets, as the central niche requires large colour fields rather than fine detail. The
            Döşemealtı tradition uses the Turkish (symmetrical) knot exclusively — consistent with
            the wider Anatolian village weaving practice.
          </div>
        </div>
      </div>

    </div><!-- /.photo-cards -->
  </div><!-- /.analysis-section -->

  <!-- ── TECHNIQUE DIAGRAM ── -->
  <div class="technique-section">
    <div class="section-label" style="justify-content:center;max-width:300px;margin:0 auto .5rem">Process</div>
    <h2>How a Döşemealtı carpet <em>is made</em></h2>
    <p>The five-stage hand-knotting process — from loom setup to finishing.</p>

    <div class="diagram-wrap">
      <div class="step-pills" id="step-pills">
        <button class="step-pill sp-active" onclick="goTo(0)">I · Loom</button>
        <button class="step-pill"           onclick="goTo(1)">II · Warp</button>
        <button class="step-pill"           onclick="goTo(2)">III · Knot</button>
        <button class="step-pill"           onclick="goTo(3)">IV · Weft</button>
        <button class="step-pill"           onclick="goTo(4)">V · Finish</button>
      </div>

      <div class="svg-wrap">
        <svg id="diag-svg" viewBox="0 0 560 315" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <marker id="arr" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
              <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
            </marker>
            <pattern id="bgD" width="20" height="20" patternUnits="userSpaceOnUse">
              <circle cx="1" cy="1" r=".5" fill="#d8d4cb" opacity=".4"/>
            </pattern>
          </defs>
          <rect width="560" height="315" fill="url(#bgD)"/>

          <!-- Warp threads (always visible) -->
          <g id="d-warps">
            <rect x="60"  y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="61"  y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="115" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="116" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="170" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="171" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="225" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="226" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="280" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="281" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="335" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="336" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="390" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="391" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <rect x="445" y="20" width="9" height="275" rx="4.5" fill="#c8c4bc"/>
            <rect x="446" y="20" width="2.5" height="275" rx="1.2" fill="rgba(255,255,255,.4)"/>
            <text x="64"  y="304" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" fill="#9a9590" letter-spacing=".3" font-weight="400">W1</text>
            <text x="449" y="304" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" fill="#9a9590" letter-spacing=".3" font-weight="400">W8</text>
          </g>

          <!-- Step 0: loom frame -->
          <g id="d0">
            <!-- top beam -->
            <rect x="40" y="15" width="430" height="12" rx="4" fill="#7c7970" opacity=".7"/>
            <!-- bottom beam -->
            <rect x="40" y="283" width="430" height="12" rx="4" fill="#7c7970" opacity=".7"/>
            <!-- side uprights -->
            <rect x="30" y="12" width="12" height="286" rx="4" fill="#7c7970" opacity=".5"/>
            <rect x="468" y="12" width="12" height="286" rx="4" fill="#7c7970" opacity=".5"/>
            <!-- label -->
            <rect x="170" y="135" width="170" height="22" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
            <text x="255" y="149" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8.5" font-weight="500" fill="var(--ink)" letter-spacing=".08em">VERTICAL LOOM (AYAKLI TEZGAH)</text>
          </g>

          <!-- Step 1: warps strung -->
          <g id="d1" style="opacity:0">
            <path class="anim-path" style="--len:300"
              d="M 40,32 L 480,32"
              fill="none" stroke="#5a3e2b" stroke-width="3" stroke-linecap="round" marker-end="url(#arr)"/>
            <rect x="155" y="45" width="210" height="20" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
            <text x="260" y="58" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".07em">WARPS STRUNG VERTICALLY</text>
            <text x="260" y="84" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="#7c7970">hand-spun wool · under constant tension</text>
          </g>

          <!-- Step 2: Turkish knot on two warps -->
          <g id="d2" style="opacity:0">
            <!-- existing weft rows -->
            <rect x="40" y="200" width="430" height="9" rx="2" fill="#9a9590" opacity=".4"/>
            <rect x="40" y="215" width="430" height="9" rx="2" fill="#9a9590" opacity=".4"/>
            <!-- Turkish knot around W4+W5 -->
            <path class="anim-path" style="--len:300"
              d="M 225,180
                 Q 218,180 218,162 Q 218,144 230,144
                 Q 289,144 289,162 Q 289,180 280,180
                 Q 268,180 268,162 Q 268,144 280,144"
              fill="none" stroke="#5a3e2b" stroke-width="5" stroke-linecap="round"/>
            <!-- pile ends -->
            <path id="pile1" d="M 225,180 L 225,230" fill="none" stroke="#5a3e2b" stroke-width="4.5" stroke-linecap="round" opacity="0"/>
            <path id="pile2" d="M 289,180 L 289,230" fill="none" stroke="#5a3e2b" stroke-width="4.5" stroke-linecap="round" opacity="0"/>
            <!-- label -->
            <rect x="310" y="146" width="158" height="36" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
            <text x="389" y="160" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".07em">TURKISH KNOT</text>
            <text x="389" y="173" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7.5" font-weight="300" fill="#7c7970">2 forward · symmetric</text>
          </g>

          <!-- Step 3: weft rows after knot row -->
          <g id="d3" style="opacity:0">
            <!-- knot row faded -->
            <path d="M 225,160 Q 257,140 289,160" fill="none" stroke="#5a3e2b" stroke-width="4" stroke-linecap="round" opacity=".2"/>
            <path d="M 225,185 L 225,210 M 289,185 L 289,210" fill="none" stroke="#5a3e2b" stroke-width="4" stroke-linecap="round" opacity=".2"/>
            <!-- two weft rows -->
            <path class="anim-path" style="--len:450"
              d="M 15,175 L 495,175"
              fill="none" stroke="#7c7970" stroke-width="5" stroke-linecap="round"/>
            <path class="anim-path" style="--len:450"
              d="M 495,188 L 15,188"
              fill="none" stroke="#7c7970" stroke-width="5" stroke-linecap="round" opacity="0"/>
            <rect x="155" y="200" width="250" height="20" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
            <text x="280" y="213" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".07em">2 WEFT ROWS LOCK EACH KNOT ROW</text>
          </g>

          <!-- Step 4: finished fabric section -->
          <g id="d4" style="opacity:0">
            <!-- fabric bands — alternating knot rows + weft -->
            <rect x="40" y="80"  width="430" height="10" rx="2" fill="#5a3e2b" opacity=".75"/>
            <rect x="40" y="92"  width="430" height="7"  rx="1" fill="#9a9590" opacity=".45"/>
            <rect x="40" y="101" width="430" height="10" rx="2" fill="#5a3e2b" opacity=".6"/>
            <rect x="40" y="113" width="430" height="7"  rx="1" fill="#9a9590" opacity=".45"/>
            <rect x="40" y="122" width="430" height="10" rx="2" fill="#5a3e2b" opacity=".75"/>
            <rect x="40" y="134" width="430" height="7"  rx="1" fill="#9a9590" opacity=".45"/>
            <rect x="40" y="143" width="430" height="10" rx="2" fill="#5a3e2b" opacity=".6"/>
            <rect x="40" y="155" width="430" height="7"  rx="1" fill="#9a9590" opacity=".45"/>
            <rect x="40" y="164" width="430" height="10" rx="2" fill="#5a3e2b" opacity=".75"/>
            <!-- warp overlays -->
            <rect x="60"  y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="115" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="170" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="225" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="280" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="335" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="390" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <rect x="445" y="78" width="9" height="98" rx="3" fill="#c8c4bc" opacity=".22"/>
            <!-- scissors / shearing indicator -->
            <line x1="40" y1="195" x2="480" y2="195" stroke="#b8900a" stroke-width="1.2" stroke-dasharray="6 3" opacity=".6"/>
            <text x="280" y="215" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="#7c7970">pile sheared to even height — finishing complete</text>
            <rect x="136" y="228" width="288" height="18" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
            <text x="280" y="241" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".08em">KNOT ROW · WEFT · KNOT ROW · WEFT · SHEAR</text>
          </g>
        </svg>
      </div><!-- /.svg-wrap -->

      <div class="step-desc" id="desc-box"><span id="desc-text"></span></div>

      <div class="nav-row">
        <button class="nav-btn" id="prev-btn" onclick="prevStep()" disabled>← Prev</button>
        <div class="progress-bar"><div class="progress-fill" id="prog-fill" style="width:20%"></div></div>
        <span class="step-counter" id="step-ctr">1 / 5</span>
        <button class="nav-btn" id="next-btn" onclick="nextStep()">Next →</button>
      </div>
    </div>
  </div>

  <!-- ── COMPARE ── -->
  <div class="compare-section">
    <div class="section-label" style="justify-content:center;max-width:300px;margin:0 auto .5rem">Context</div>
    <h2>Döşemealtı vs. <em>other Anatolian traditions</em></h2>
    <p>How Döşemealtı sits within the broader landscape of Turkish carpet-weaving.</p>

    <div class="table-scroll">
      <table class="compare-table">
        <thead>
          <tr>
            <th>Characteristic</th>
            <th>Döşemealtı</th>
            <th>Uşak / Oushak</th>
            <th>Hereke</th>
            <th>Kayseri</th>
          </tr>
        </thead>
        <tbody>
          <tr class="hi"><td>Origin type</td><td>Village / tribal</td><td>Urban workshop</td><td>Imperial court</td><td>Mixed urban/village</td></tr>
          <tr><td>Structure</td><td>Wool on wool</td><td>Wool on cotton</td><td>Silk or wool on silk</td><td>Wool on cotton or silk</td></tr>
          <tr class="hi"><td>Knot</td><td>Turkish (symmetrical)</td><td>Turkish</td><td>Turkish or Persian</td><td>Turkish</td></tr>
          <tr><td>Knot density</td><td>30–80 / dm²</td><td>40–80 / dm²</td><td>900–3600 / dm²</td><td>80–400 / dm²</td></tr>
          <tr class="hi"><td>Design character</td><td>Bold geometric tribal</td><td>Curvilinear floral</td><td>Ultra-fine curvilinear</td><td>Geometric or floral</td></tr>
          <tr><td>Dyes</td><td>Natural — madder, indigo</td><td>Natural or synthetic</td><td>Natural (finest)</td><td>Natural or synthetic</td></tr>
          <tr class="hi"><td>Pile height</td><td>Medium–high</td><td>Medium, soft hand</td><td>Very low, dense</td><td>Low–medium</td></tr>
          <tr><td>Weaver</td><td>Village women, home</td><td>Workshop artisans</td><td>Court/workshop masters</td><td>Workshop artisans</td></tr>
        </tbody>
      </table>
    </div>
  </div>

</main>

<!-- ── LIGHTBOX ── -->
<div class="lightbox" id="lightbox" onclick="closeLightbox()">
  <button class="lightbox-close" onclick="closeLightbox()">Close ✕</button>
  <img id="lb-img" src="" alt=""/>
  <div class="lightbox-caption" id="lb-cap"></div>
</div>

<footer>
  <a href="https://fmemo75-prog.github.io/carpetguide/" style="color:inherit;text-decoration:none">🌍 Global Carpet Guide</a>
  &nbsp;·&nbsp; Curator: Fatih Mehmet Canıtez &nbsp;·&nbsp; © 2026
</footer>

<script>
/* ── Diagram steps ── */
const STEPS = [
  `The Döşemealtı weaver works on a <strong>vertical ground loom</strong> (ayaklı tezgah). The loom frame is built from local timber; its width determines the carpet's width. Vertical looms are traditional in Anatolian village weaving and allow the weaver to work seated on a plank that rises row by row.`,
  `<strong>Warp threads</strong> of hand-spun wool are stretched vertically between the top and bottom beams under strong tension. In Döşemealtı tradition both warp and weft are wool — the "wool on wool" structure that gives these carpets their characteristic thick, warm hand.`,
  `The weaver ties a <strong>Turkish (symmetrical / Ghiordes) knot</strong> around each pair of adjacent warp threads. The yarn wraps forward over two warps, with both ends exiting downward through the centre. Each knot is hand-cut to length. A row of knots across the full width creates one line of pile.`,
  `After each knot row, <strong>two weft threads</strong> are passed horizontally through alternating sheds and beaten down firmly with a weaving comb. These weft rows lock the knots in position and build the structural body of the carpet. The alternating shed prevents the pile from shifting.`,
  `When the carpet reaches full length it is cut from the loom and the pile is <strong>sheared to an even height</strong>. Döşemealtı tradition favours a medium pile height — giving a robust, tactile surface suited to the demanding Taurus mountain household environment. Ends are finished with a hand-knotted fringe.`
];

let cur = 0;
const MAX = 4;

function goTo(n) {
  cur = n;
  const svg = document.getElementById('diag-svg');
  [0,1,2,3,4].forEach(i => {
    const el = svg.querySelector(`#d${i}`);
    if (el) { el.style.transition = 'opacity .3s'; el.style.opacity = i === n ? '1' : '0'; }
  });
  const el = svg.querySelector(`#d${n}`);
  if (el) {
    el.querySelectorAll('.anim-path').forEach(p => {
      const m = p.style.cssText.match(/--len:\s*([\d.]+)/);
      const len = m ? parseFloat(m[1]) : 400;
      p.style.animation = 'none'; void p.offsetWidth;
      p.style.strokeDasharray = len; p.style.strokeDashoffset = len;
      setTimeout(() => {
        p.style.animation = 'drawPath .9s cubic-bezier(.4,0,.2,1) forwards';
        p.style.strokeDashoffset = 0;
      }, 30);
    });
    // step 2 — delayed pile ends
    if (n === 2) {
      setTimeout(() => {
        ['pile1','pile2'].forEach((id, i) => {
          const p = document.getElementById(id);
          p.style.opacity = '1';
          p.style.animation = 'none'; void p.offsetWidth;
          p.style.strokeDasharray = '60'; p.style.strokeDashoffset = '60';
          p.style.animation = `drawPath .5s ${.5 + i * .1}s ease forwards`;
          p.style.strokeDashoffset = '0';
        });
      }, 500);
    }
    // step 3 — delayed return weft
    if (n === 3) {
      setTimeout(() => {
        const ret = el.querySelectorAll('.anim-path')[1];
        if (ret) {
          ret.style.opacity = '1';
          ret.style.animation = 'none'; void ret.offsetWidth;
          ret.style.strokeDasharray = '450'; ret.style.strokeDashoffset = '450';
          ret.style.animation = 'drawPath .8s .45s cubic-bezier(.4,0,.2,1) forwards';
          ret.style.strokeDashoffset = '0';
        }
      }, 200);
    }
  }

  // pills
  document.querySelectorAll('#step-pills .step-pill').forEach((b, i) => {
    b.className = 'step-pill' + (i === n ? ' sp-active' : '');
  });
  document.getElementById('prog-fill').style.width = `${(n + 1) * 20}%`;
  document.getElementById('step-ctr').textContent  = `${n + 1} / 5`;
  document.getElementById('prev-btn').disabled = n === 0;
  document.getElementById('next-btn').disabled = n === MAX;
  const box = document.getElementById('desc-box');
  box.style.animation = 'none'; void box.offsetWidth;
  box.style.animation = 'fadeUp .38s ease forwards';
  document.getElementById('desc-text').innerHTML = STEPS[n];
}

function nextStep() { if (cur < MAX) goTo(cur + 1); }
function prevStep() { if (cur > 0)   goTo(cur - 1); }

/* ── Lightbox ── */
function openLightbox(src, caption) {
  document.getElementById('lb-img').src = src;
  document.getElementById('lb-cap').textContent = caption;
  document.getElementById('lightbox').classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeLightbox() {
  document.getElementById('lightbox').classList.remove('open');
  document.body.style.overflow = '';
}

/* ── Keyboard nav ── */
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeLightbox();
  if (e.key === 'ArrowRight') nextStep();
  if (e.key === 'ArrowLeft')  prevStep();
});

/* ── Init ── */
goTo(0);
</script>
</body>
</html>
