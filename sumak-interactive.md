---
layout: default
title: 
---

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sumak — The Wrapped Flatweave</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,300;1,9..144,400&family=Outfit:wght@200;300;400;500&family=Libre+Baskerville:ital@1&display=swap" rel="stylesheet">

<style>
:root {
  --bg:         #f8f7f5;
  --bg2:        #f0eeeb;
  --bg3:        #e8e5e0;
  --line:       #d4d0c8;
  --line2:      #c0bbb2;
  --ink:        #1a1916;
  --ink2:       #4a4740;
  --ink3:       #7a7770;
  --warp:       #9a9590;
  --warp-lt:    #bcb8b2;
  --warp-hl:    rgba(255,255,255,.4);
  /* accent per technique */
  --acc-a:      #1a1916;   /* near-black — basic */
  --acc-b:      #c0392b;   /* red — countered */
  --acc-c:      #1a5276;   /* steel blue — double */
  --acc-a-lt:   #4a4740;
  --acc-b-lt:   #e74c3c;
  --acc-c-lt:   #2980b9;
}

*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}

body{
  background:var(--bg);
  background-image:
    url("data:image/svg+xml,%3Csvg width='20' height='20' viewBox='0 0 20 20' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='1' cy='1' r='.6' fill='%23c0bbb2' fill-opacity='.35'/%3E%3C/svg%3E");
  color:var(--ink);
  font-family:'Outfit',sans-serif;
  font-weight:300;
  min-height:100vh;
  overflow-x:hidden;
}

/* ═══ HEADER ═══ */
header{
  text-align:center;
  padding:3.5rem 1.5rem 2.5rem;
  border-bottom:1px solid var(--line);
}
@media(max-width:500px){header{padding:2rem 1rem 1.5rem}}

.header-eyebrow{
  font-family:'Outfit',sans-serif;
  font-size:.68rem;font-weight:400;
  letter-spacing:.35em;text-transform:uppercase;
  color:var(--ink3);margin-bottom:1.6rem;
}

/* animated wrap strip */
.wrap-strip{
  display:flex;justify-content:center;
  margin:0 auto 1.4rem;width:fit-content;
}

h1{
  font-family:'Fraunces',serif;
  font-size:clamp(2.6rem,6.5vw,5rem);
  font-weight:300;letter-spacing:.01em;line-height:1.06;
  color:var(--ink);margin-bottom:.55rem;
}
h1 em{font-style:italic;color:var(--ink2)}

.subtitle{
  font-size:.92rem;font-weight:200;letter-spacing:.08em;
  color:var(--ink3);margin-bottom:.25rem;
}
.aka{
  font-family:'Libre Baskerville',serif;
  font-size:.92rem;font-style:italic;color:var(--ink3);
}

/* ═══ MAIN ═══ */
main{
  max-width:1120px;margin:0 auto;
  padding:3rem 2rem 5rem;
  display:grid;grid-template-columns:1fr 1fr;
  gap:3rem 4.5rem;align-items:start;
}
@media(max-width:800px){
  main{grid-template-columns:1fr;gap:2rem;padding:1.5rem 1rem 3rem}
}

/* ═══ DIAGRAM PANEL ═══ */
.diagram-panel{position:sticky;top:2rem}
@media(max-width:800px){.diagram-panel{position:static}}

/* Technique tabs — minimal underline style */
.tech-tabs{
  display:flex;border-bottom:1.5px solid var(--line);
  margin-bottom:1.4rem;
}
.tech-tab{
  flex:1;background:none;border:none;
  padding:.6rem .5rem;
  font-family:'Outfit',sans-serif;
  font-size:.7rem;font-weight:400;
  letter-spacing:.12em;text-transform:uppercase;
  color:var(--ink3);
  border-bottom:2.5px solid transparent;
  margin-bottom:-1.5px;
  cursor:pointer;transition:all .2s;text-align:center;
}
.tech-tab:hover{color:var(--ink2)}
.tech-tab.active{color:var(--ink);border-bottom-color:var(--ink)}
.tech-tab.tab-b.active{color:var(--acc-b);border-bottom-color:var(--acc-b)}
.tech-tab.tab-c.active{color:var(--acc-c);border-bottom-color:var(--acc-c)}
.tech-tab.tab-b:hover{color:var(--acc-b)}
.tech-tab.tab-c:hover{color:var(--acc-c)}

/* Step pills */
.step-pills{
  display:flex;gap:.35rem;flex-wrap:wrap;
  margin-bottom:1.1rem;
}
.step-pill{
  background:none;
  border:1px solid var(--line);
  border-radius:2px;
  padding:.28rem .75rem;
  font-family:'Outfit',sans-serif;
  font-size:.62rem;font-weight:400;
  letter-spacing:.1em;text-transform:uppercase;
  color:var(--ink3);cursor:pointer;transition:all .2s;
}
.step-pill:hover{border-color:var(--line2);color:var(--ink2)}
.step-pill.active{
  background:var(--ink);border-color:var(--ink);
  color:var(--bg);
}
.step-pill.active-b{background:var(--acc-b);border-color:var(--acc-b);color:#fff}
.step-pill.active-c{background:var(--acc-c);border-color:var(--acc-c);color:#fff}

/* SVG canvas */
.svg-wrap{
  background:var(--bg2);
  border:1px solid var(--line);
  border-radius:3px;
  overflow:hidden;aspect-ratio:4/3;
}
.svg-wrap svg{width:100%;height:100%;display:block}

/* Description */
.step-desc{
  margin-top:1.1rem;
  padding:1rem 1.15rem;
  background:var(--bg2);
  border-left:2px solid var(--line2);
  font-size:.88rem;line-height:1.82;
  color:var(--ink2);min-height:4.5rem;
  transition:border-color .25s;
}
.step-desc strong{color:var(--ink);font-weight:500}
.desc-b{border-left-color:var(--acc-b)}
.desc-c{border-left-color:var(--acc-c)}

/* Nav */
.nav-row{
  display:flex;align-items:center;
  justify-content:space-between;margin-top:.9rem;
}
.nav-btn{
  background:none;border:1px solid var(--line);
  border-radius:2px;padding:.42rem .95rem;
  font-family:'Outfit',sans-serif;font-size:.65rem;
  font-weight:400;letter-spacing:.12em;text-transform:uppercase;
  color:var(--ink3);cursor:pointer;transition:all .2s;
}
.nav-btn:hover:not(:disabled){border-color:var(--line2);color:var(--ink)}
.nav-btn:disabled{opacity:.25;cursor:default}

.progress-bar{
  flex:1;height:2px;background:var(--line);
  margin:0 1rem;position:relative;border-radius:1px;
  overflow:hidden;
}
.progress-fill{
  position:absolute;top:0;left:0;height:100%;
  background:var(--ink);border-radius:1px;
  transition:width .35s cubic-bezier(.4,0,.2,1);
}
.fill-b{background:var(--acc-b)}
.fill-c{background:var(--acc-c)}
.step-counter{
  font-size:.65rem;font-weight:400;letter-spacing:.1em;
  color:var(--ink3);white-space:nowrap;
}

.tech-panel{display:none}
.tech-panel.active{display:block}

/* ═══ CONTENT PANEL ═══ */
.content-panel{padding-top:.4rem}

.section-label{
  font-family:'Outfit',sans-serif;
  font-size:.62rem;font-weight:500;
  letter-spacing:.3em;text-transform:uppercase;
  color:var(--ink3);margin-bottom:.9rem;
  display:flex;align-items:center;gap:.8rem;
}
.section-label::after{
  content:'';flex:1;height:1px;
  background:linear-gradient(to right,var(--line),transparent);
}

h2{
  font-family:'Fraunces',serif;
  font-size:1.9rem;font-weight:300;line-height:1.2;
  margin-bottom:1rem;color:var(--ink);
}
h2 em{font-style:italic;color:var(--ink2)}

p{font-size:.9rem;line-height:1.9;color:var(--ink2);margin-bottom:1rem}
p strong{color:var(--ink);font-weight:400}

/* Fact strip */
.fact-strip{
  display:grid;grid-template-columns:1fr 1fr;
  gap:.65rem;margin:1.5rem 0;
}
.fact-card{
  background:var(--bg2);border:1px solid var(--line);
  border-radius:3px;padding:.85rem .95rem;
}
.fact-card .fv{
  font-family:'Fraunces',serif;
  font-size:1.5rem;font-weight:400;
  color:var(--ink);line-height:1;margin-bottom:.2rem;
}
.fact-card .fl{font-size:.7rem;letter-spacing:.06em;color:var(--ink3);font-weight:300}

/* Technique summary cards */
.tech-cards{display:flex;flex-direction:column;gap:.65rem;margin:1.4rem 0}
.tc{
  display:grid;grid-template-columns:3px 1fr;
  gap:0 1rem;
  background:var(--bg2);border:1px solid var(--line);
  border-radius:3px;overflow:hidden;
}
.tc-stripe{background:var(--ink)}
.tc-stripe-b{background:var(--acc-b)}
.tc-stripe-c{background:var(--acc-c)}
.tc-body{padding:.85rem 1rem .85rem 0}
.tc-name{
  font-family:'Outfit',sans-serif;
  font-size:.68rem;font-weight:500;
  letter-spacing:.12em;text-transform:uppercase;
  color:var(--ink);margin-bottom:.35rem;
}
.tc-b .tc-name{color:var(--acc-b)}
.tc-c .tc-name{color:var(--acc-c)}
.tc-desc{font-size:.83rem;line-height:1.72;color:var(--ink2)}

/* Compare table */
.table-scroll{
  width:100%;overflow-x:auto;
  -webkit-overflow-scrolling:touch;
  margin:1.4rem 0;
  border:1px solid var(--line);border-radius:3px;
}
.compare-table{
  width:100%;min-width:400px;
  border-collapse:collapse;font-size:.83rem;
}
.compare-table thead tr{border-bottom:1px solid var(--line2)}
.compare-table th{
  font-family:'Outfit',sans-serif;
  font-size:.6rem;font-weight:500;
  letter-spacing:.18em;text-transform:uppercase;
  color:var(--ink3);
  padding:.55rem .85rem;text-align:left;
  white-space:nowrap;background:var(--bg2);
}
.compare-table td{
  padding:.55rem .85rem;
  border-bottom:1px solid var(--line);
  color:var(--ink2);vertical-align:top;line-height:1.55;
}
.compare-table td:first-child{color:var(--ink);font-weight:400;white-space:nowrap}
.compare-table tr:last-child td{border-bottom:none}
.compare-table .hi td{background:var(--bg2)}

/* Pull quote */
.pull-quote{
  margin:1.8rem 0;padding:1.4rem 1.8rem;
  border-top:1px solid var(--line);
  border-bottom:1px solid var(--line);
  position:relative;
}
.pull-quote::before{
  content:'\201C';
  font-family:'Fraunces',serif;
  font-size:5rem;color:var(--line2);
  position:absolute;top:-.6rem;left:.7rem;line-height:1;
}
.pull-quote p{
  font-family:'Fraunces',serif;
  font-size:1.2rem;font-style:italic;line-height:1.65;
  color:var(--ink);margin-bottom:.4rem;
}
.pull-quote cite{font-size:.7rem;letter-spacing:.1em;color:var(--ink3)}

/* Uses list */
.uses-list{list-style:none;margin:.4rem 0 1.4rem}
.uses-list li{
  display:flex;align-items:baseline;gap:.7rem;
  font-size:.86rem;color:var(--ink2);
  padding:.42rem 0;border-bottom:1px solid var(--line);line-height:1.55;
}
.uses-list li::before{
  content:'';
  display:inline-block;width:4px;height:4px;
  border-radius:50%;background:var(--line2);flex-shrink:0;
  transform:translateY(-1px);
}
.uses-list strong{color:var(--ink);font-weight:400}

/* ═══ ANATOMY ═══ */
.anatomy-section{
  grid-column:1/-1;padding-top:2.5rem;
  border-top:1px solid var(--line);
}
.anatomy-section h2{
  text-align:center;font-size:1.6rem;margin-bottom:1.6rem;
}

.anatomy-tabs{
  display:flex;justify-content:center;gap:.4rem;
  margin-bottom:1.5rem;flex-wrap:wrap;
}
.atab{
  background:none;border:1px solid var(--line);border-radius:2px;
  padding:.38rem 1.1rem;
  font-family:'Outfit',sans-serif;font-size:.65rem;
  font-weight:400;letter-spacing:.14em;text-transform:uppercase;
  color:var(--ink3);cursor:pointer;transition:all .2s;
}
.atab:hover{border-color:var(--line2);color:var(--ink2)}
.atab.active{background:var(--ink);border-color:var(--ink);color:var(--bg)}
.atab.atab-b.active{background:var(--acc-b);border-color:var(--acc-b);color:#fff}
.atab.atab-c.active{background:var(--acc-c);border-color:var(--acc-c);color:#fff}
.atab.atab-b:hover{color:var(--acc-b);border-color:var(--acc-b)}
.atab.atab-c:hover{color:var(--acc-c);border-color:var(--acc-c)}

.anatomy-view{display:none}
.anatomy-view.active{display:block}
.anatomy-wrap{
  background:var(--bg2);border:1px solid var(--line);
  border-radius:3px;padding:1rem;overflow-x:auto;
}
.anat-mobile{display:none}
.anatomy-labels{list-style:none;margin-top:.8rem}
.anatomy-labels li{
  display:flex;gap:.65rem;align-items:baseline;
  font-size:.83rem;line-height:1.68;color:var(--ink2);
  padding:.42rem 0;border-bottom:1px solid var(--line);
}
.alabel{
  font-family:'Outfit',sans-serif;font-size:.62rem;
  font-weight:500;letter-spacing:.1em;text-transform:uppercase;
  color:var(--ink);white-space:nowrap;flex-shrink:0;
}
.alabel-b{color:var(--acc-b)}
.alabel-c{color:var(--acc-c)}

footer{
  text-align:center;padding:2.5rem 1rem;
  border-top:1px solid var(--line);
  font-size:.72rem;letter-spacing:.1em;color:var(--ink3);
}

/* Animations */
@keyframes drawPath{from{stroke-dashoffset:var(--len)}to{stroke-dashoffset:0}}
@keyframes fadeUp{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
.anim-path{stroke-dasharray:var(--len);stroke-dashoffset:var(--len)}

@media(max-width:500px){
  h1{font-size:2.2rem}
  h2{font-size:1.5rem}
  p,.step-desc{font-size:.84rem}
  .fact-card .fv{font-size:1.3rem}
  .tech-tab{font-size:.6rem;padding:.55rem .3rem}
  .step-pill{font-size:.56rem;padding:.24rem .6rem}
  .pull-quote{padding:1rem 1rem 1rem 1.4rem}
  .pull-quote p{font-size:1.05rem}
  .anatomy-section h2{font-size:1.3rem}
}
</style>
</head>
<body>

<!-- ═══ HEADER ═══ -->
<header>
  <p class="header-eyebrow">Caucasus · Anatolian Flatweave</p>

  <!-- Sumak wrap diagram strip -->
  <div class="wrap-strip">
    <svg viewBox="0 0 300 32" width="300" height="32" xmlns="http://www.w3.org/2000/svg">
      <rect width="300" height="32" fill="var(--bg2)" rx="2"/>
      <!-- warps -->
      <line x1="30"  y1="0" x2="30"  y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="72"  y1="0" x2="72"  y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="114" y1="0" x2="114" y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="156" y1="0" x2="156" y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="198" y1="0" x2="198" y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="240" y1="0" x2="240" y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <line x1="282" y1="0" x2="282" y2="32" stroke="var(--warp)"    stroke-width="2.5"/>
      <!-- basic wrap zigzag — ink -->
      <polyline
        points="0,9 30,9 30,23 72,23 72,9 114,9 114,23 156,23 156,9 198,9 198,23 240,23 240,9 282,9 282,23 300,23"
        fill="none" stroke="var(--ink)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <!-- back thread dashed -->
      <line x1="0" y1="16" x2="300" y2="16" stroke="var(--ink3)" stroke-width="1" stroke-dasharray="5 3" opacity=".5"/>
    </svg>
  </div>

  <h1><em>Sumak</em> Weaving</h1>
  <p class="subtitle">An Interactive Guide to the Wrapped Flatweave</p>
  <p class="aka">Soumak · Sumach · A flatweave with structural depth</p>
</header>

<!-- ═══ MAIN ═══ -->
<main>

  <!-- ──── LEFT: Diagram ──── -->
  <div class="diagram-panel">

    <div class="tech-tabs">
      <button class="tech-tab active"  onclick="switchTech('basic')">Basic</button>
      <button class="tech-tab tab-b"   onclick="switchTech('counter')">Countered</button>
      <button class="tech-tab tab-c"   onclick="switchTech('double')">Double</button>
    </div>

    <!-- ── A: Basic Wrap ── -->
    <div class="tech-panel active" id="panel-basic">
      <div class="step-pills" id="pills-basic">
        <button class="step-pill active" onclick="goTo('basic',0)">I · Warps</button>
        <button class="step-pill"        onclick="goTo('basic',1)">II · First Wrap</button>
        <button class="step-pill"        onclick="goTo('basic',2)">III · Full Row</button>
        <button class="step-pill"        onclick="goTo('basic',3)">IV · Back Thread</button>
      </div>

      <div class="svg-wrap">
        <svg viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <marker id="arA" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
              <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
            </marker>
            <pattern id="bgA" width="20" height="20" patternUnits="userSpaceOnUse">
              <circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".5"/>
            </pattern>
          </defs>
          <rect width="400" height="300" fill="url(#bgA)"/>

          <!-- Warps -->
          <g id="basic-warps">
            <rect x="44"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="46"  y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="94"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="96"  y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="144" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="146" y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="194" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="196" y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="244" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="246" y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="294" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="296" y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <rect x="344" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="346" y="14" width="3"  height="272" rx="1.5" fill="var(--warp-hl)"/>
            <text x="49"  y="294" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7.5" fill="var(--ink3)" letter-spacing=".4" font-weight="400">W1</text>
            <text x="349" y="294" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7.5" fill="var(--ink3)" letter-spacing=".4" font-weight="400">W7</text>
          </g>

          <!-- Step 0 -->
          <g id="bs0">
            <path class="anim-path" style="--len:100"
              d="M 8,140 L 42,140"
              fill="none" stroke="var(--acc-a)" stroke-width="3.5" stroke-linecap="round" marker-end="url(#arA)"/>
            <text x="200" y="282" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">7 warp threads — held under loom tension</text>
          </g>

          <!-- Step 1: first single wrap -->
          <g id="bs1" style="opacity:0">
            <path d="M 8,128 L 44,128" fill="none" stroke="var(--acc-a)" stroke-width="3" stroke-linecap="round" opacity=".2"/>
            <path class="anim-path" style="--len:300"
              d="M 44,128
                 Q 37,128 37,110 Q 37,92 49,92
                 Q 104,92 104,110 Q 104,128 94,128
                 Q 82,128 82,110 Q 82,92 94,92"
              fill="none" stroke="var(--acc-a)" stroke-width="4.5" stroke-linecap="round"/>
            <!-- callout -->
            <rect x="116" y="78" width="152" height="32" rx="2"
              fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>
            <text x="192" y="92" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".08em">FORWARD OVER 2 WARPS</text>
            <text x="192" y="104" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8" font-weight="300" fill="var(--ink3)">then step back under 1</text>
          </g>

          <!-- Step 2: full row -->
          <g id="bs2" style="opacity:0">
            <path class="anim-path" style="--len:820"
              d="M 8,125
                 L 44,125 Q 37,125 37,107 Q 37,89 49,89 Q 104,89 104,107 Q 104,125 94,125
                 Q 82,125 82,107 Q 82,89 94,89
                 L 144,89 Q 154,89 154,107 Q 154,125 144,125
                 Q 132,125 132,107 Q 132,89 144,89
                 L 194,89 Q 204,89 204,107 Q 204,125 194,125
                 Q 182,125 182,107 Q 182,89 194,89
                 L 244,89 Q 254,89 254,107 Q 254,125 244,125
                 Q 232,125 232,107 Q 232,89 244,89
                 L 294,89 Q 304,89 304,107 Q 304,125 294,125
                 Q 282,125 282,107 Q 282,89 294,89
                 L 344,89 Q 354,89 354,107 Q 354,125 344,125
                 L 392,125"
              fill="none" stroke="var(--acc-a)" stroke-width="4.5" stroke-linecap="round"/>
            <text x="200" y="160" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="var(--ink3)" letter-spacing=".04em">each wrap — 2 forward · 1 back — across full width</text>
          </g>

          <!-- Step 3: back thread -->
          <g id="bs3" style="opacity:0">
            <path d="M 8,125 L 392,125" fill="none" stroke="var(--acc-a)" stroke-width="4" stroke-linecap="round" opacity=".2"/>
            <path class="anim-path" style="--len:400"
              d="M 392,152 L 8,152"
              fill="none" stroke="var(--acc-a)" stroke-width="2.5" stroke-dasharray="7 4" stroke-linecap="round"/>
            <!-- label -->
            <rect x="110" y="163" width="180" height="22" rx="2"
              fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>
            <text x="200" y="177" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".08em">BACK THREAD — locks all wraps</text>
          </g>
        </svg>
      </div>

      <div class="step-desc" id="desc-basic-box"><span id="desc-basic"></span></div>
      <div class="nav-row">
        <button class="nav-btn" id="prev-basic" onclick="prev('basic')" disabled>← Prev</button>
        <div class="progress-bar"><div class="progress-fill" id="fill-basic" style="width:25%"></div></div>
        <span class="step-counter" id="ctr-basic">1 / 4</span>
        <button class="nav-btn" id="next-basic" onclick="next('basic')">Next →</button>
      </div>
    </div>

    <!-- ── B: Countered ── -->
    <div class="tech-panel" id="panel-counter">
      <div class="step-pills" id="pills-counter">
        <button class="step-pill active-b" onclick="goTo('counter',0)">I · Setup</button>
        <button class="step-pill"          onclick="goTo('counter',1)">II · Row A →</button>
        <button class="step-pill"          onclick="goTo('counter',2)">III · Row B ←</button>
        <button class="step-pill"          onclick="goTo('counter',3)">IV · Herringbone</button>
      </div>

      <div class="svg-wrap">
        <svg viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <marker id="arB" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
              <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
            </marker>
            <pattern id="bgB" width="20" height="20" patternUnits="userSpaceOnUse">
              <circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".5"/>
            </pattern>
          </defs>
          <rect width="400" height="300" fill="url(#bgB)"/>
          <!-- Warps -->
          <g>
            <rect x="44"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="94"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="144" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="194" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="244" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="294" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="344" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
          </g>

          <!-- Step 0: two shuttles -->
          <g id="cs0">
            <rect x="8"   y="118" width="58" height="16" rx="2" fill="var(--bg)" stroke="var(--acc-b)" stroke-width="1"/>
            <text x="37" y="129" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="7.5" font-weight="500" fill="var(--acc-b)" letter-spacing=".05em">ROW A →</text>
            <rect x="334" y="152" width="58" height="16" rx="2" fill="var(--bg)" stroke="var(--acc-b)" stroke-width="1" opacity=".5"/>
            <text x="363" y="163" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="7.5" font-weight="400" fill="var(--acc-b)" opacity=".5" letter-spacing=".05em">ROW B ←</text>
            <path class="anim-path" style="--len:80"
              d="M 66,126 L 120,126"
              fill="none" stroke="var(--acc-b)" stroke-width="3" stroke-linecap="round" marker-end="url(#arB)"/>
            <path class="anim-path" style="--len:80"
              d="M 334,160 L 278,160"
              fill="none" stroke="var(--acc-b)" stroke-width="2" stroke-dasharray="5 3" stroke-linecap="round" marker-end="url(#arB)" opacity=".5"/>
            <text x="200" y="200" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">two rows — opposite directions, no back thread</text>
          </g>

          <!-- Step 1: Row A L→R -->
          <g id="cs1" style="opacity:0">
            <path class="anim-path" style="--len:820"
              d="M 8,112
                 L 44,112 Q 37,112 37,94 Q 37,76 49,76 Q 104,76 104,94 Q 104,112 94,112
                 Q 82,112 82,94 Q 82,76 94,76
                 L 144,76 Q 154,76 154,94 Q 154,112 144,112
                 Q 132,112 132,94 Q 132,76 144,76
                 L 194,76 Q 204,76 204,94 Q 204,112 194,112
                 Q 182,112 182,94 Q 182,76 194,76
                 L 244,76 Q 254,76 254,94 Q 254,112 244,112
                 Q 232,112 232,94 Q 232,76 244,76
                 L 294,76 Q 304,76 304,94 Q 304,112 294,112
                 Q 282,112 282,94 Q 282,76 294,76
                 L 344,76 Q 354,76 354,94 Q 354,112 344,112
                 L 392,112"
              fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round"/>
            <text x="200" y="148" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="var(--acc-b)">Row A — diagonal ridges angle →</text>
          </g>

          <!-- Step 2: Row B R→L -->
          <g id="cs2" style="opacity:0">
            <path d="M 8,112 L 392,112" fill="none" stroke="var(--acc-b)" stroke-width="4" stroke-linecap="round" opacity=".18"/>
            <path class="anim-path" style="--len:820"
              d="M 392,148
                 L 354,148 Q 361,148 361,166 Q 361,184 349,184 Q 294,184 294,166 Q 294,148 304,148
                 Q 316,148 316,166 Q 316,184 304,184
                 L 254,184 Q 244,184 244,166 Q 244,148 254,148
                 Q 266,148 266,166 Q 266,184 254,184
                 L 204,184 Q 194,184 194,166 Q 194,148 204,148
                 Q 216,148 216,166 Q 216,184 204,184
                 L 154,184 Q 144,184 144,166 Q 144,148 154,148
                 Q 166,148 166,166 Q 166,184 154,184
                 L 104,184 Q 94,184 94,166 Q 94,148 104,148
                 Q 116,148 116,166 Q 116,184 104,184
                 L 54,184 Q 44,184 44,166 Q 44,148 54,148
                 L 8,148"
              fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round" opacity=".6"/>
            <text x="200" y="212" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="var(--acc-b)" opacity=".8">Row B — ridges angle ← (reversed)</text>
          </g>

          <!-- Step 3: herringbone -->
          <g id="cs3" style="opacity:0">
            <path d="M 8,70  L 392,70"  fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round"/>
            <path d="M 8,98  L 392,98"  fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round" opacity=".6"/>
            <path d="M 8,126 L 392,126" fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round"/>
            <path d="M 8,154 L 392,154" fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round" opacity=".6"/>
            <path d="M 8,182 L 392,182" fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round"/>
            <!-- warp overlays -->
            <rect x="44"  y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="94"  y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="144" y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="194" y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="244" y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="294" y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="344" y="68" width="10" height="116" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <!-- chevron indicators -->
            <path d="M 100,68 L 116,84 L 100,100" fill="none" stroke="var(--bg)" stroke-width="1.5" stroke-linecap="round" opacity=".6"/>
            <path d="M 100,100 L 84,116 L 100,132"  fill="none" stroke="var(--bg)" stroke-width="1.5" stroke-linecap="round" opacity=".6"/>
            <path d="M 200,68 L 216,84 L 200,100" fill="none" stroke="var(--bg)" stroke-width="1.5" stroke-linecap="round" opacity=".6"/>
            <path d="M 200,100 L 184,116 L 200,132" fill="none" stroke="var(--bg)" stroke-width="1.5" stroke-linecap="round" opacity=".6"/>
            <!-- label -->
            <rect x="108" y="200" width="184" height="20" rx="2"
              fill="var(--bg)" stroke="var(--acc-b)" stroke-width=".8"/>
            <text x="200" y="213" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--acc-b)" letter-spacing=".06em">HERRINGBONE — opposing chevrons</text>
          </g>
        </svg>
      </div>

      <div class="step-desc desc-b" id="desc-counter-box"><span id="desc-counter"></span></div>
      <div class="nav-row">
        <button class="nav-btn" id="prev-counter" onclick="prev('counter')" disabled>← Prev</button>
        <div class="progress-bar"><div class="progress-fill fill-b" id="fill-counter" style="width:25%"></div></div>
        <span class="step-counter" id="ctr-counter">1 / 4</span>
        <button class="nav-btn" id="next-counter" onclick="next('counter')">Next →</button>
      </div>
    </div>

    <!-- ── C: Double Sumak ── -->
    <div class="tech-panel" id="panel-double">
      <div class="step-pills" id="pills-double">
        <button class="step-pill active-c" onclick="goTo('double',0)">I · Concept</button>
        <button class="step-pill"          onclick="goTo('double',1)">II · Front Wrap</button>
        <button class="step-pill"          onclick="goTo('double',2)">III · Back Wrap</button>
        <button class="step-pill"          onclick="goTo('double',3)">IV · Result</button>
      </div>

      <div class="svg-wrap">
        <svg viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <marker id="arC" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
              <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
            </marker>
            <pattern id="bgC" width="20" height="20" patternUnits="userSpaceOnUse">
              <circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".5"/>
            </pattern>
          </defs>
          <rect width="400" height="300" fill="url(#bgC)"/>
          <!-- Warps -->
          <g>
            <rect x="44"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="94"  y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="144" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="194" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="244" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="294" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
            <rect x="344" y="14" width="10" height="272" rx="5" fill="var(--warp-lt)"/>
          </g>

          <!-- Step 0 -->
          <g id="ds0">
            <path class="anim-path" style="--len:120"
              d="M 8,112 L 115,112"
              fill="none" stroke="var(--acc-c)" stroke-width="4.5" stroke-linecap="round" marker-end="url(#arC)"/>
            <path class="anim-path" style="--len:120"
              d="M 8,155 L 115,155"
              fill="none" stroke="var(--acc-c)" stroke-width="2.5" stroke-dasharray="6 4" stroke-linecap="round" marker-end="url(#arC)"/>
            <rect x="126" y="100" width="108" height="18" rx="2" fill="var(--bg)" stroke="var(--acc-c)" stroke-width=".8"/>
            <text x="180" y="112" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="7.5" font-weight="500" fill="var(--acc-c)" letter-spacing=".08em">FRONT THREAD</text>
            <rect x="126" y="144" width="120" height="18" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>
            <text x="186" y="156" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="7.5" font-weight="300" fill="var(--ink3)" letter-spacing=".08em">BACK THREAD (same)</text>
            <text x="200" y="200" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">one continuous yarn wraps both faces</text>
          </g>

          <!-- Step 1: front wrap -->
          <g id="ds1" style="opacity:0">
            <path class="anim-path" style="--len:820"
              d="M 8,108
                 L 44,108 Q 37,108 37,90 Q 37,72 49,72 Q 104,72 104,90 Q 104,108 94,108
                 Q 82,108 82,90 Q 82,72 94,72
                 L 144,72 Q 154,72 154,90 Q 154,108 144,108
                 Q 132,108 132,90 Q 132,72 144,72
                 L 194,72 Q 204,72 204,90 Q 204,108 194,108
                 Q 182,108 182,90 Q 182,72 194,72
                 L 244,72 Q 254,72 254,90 Q 254,108 244,108
                 Q 232,108 232,90 Q 232,72 244,72
                 L 294,72 Q 304,72 304,90 Q 304,108 294,108
                 Q 282,108 282,90 Q 282,72 294,72
                 L 344,72 Q 354,72 354,90 Q 354,108 344,108
                 L 392,108"
              fill="none" stroke="var(--acc-c)" stroke-width="4.5" stroke-linecap="round"/>
            <text x="200" y="145" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="var(--acc-c)">front face — standard sumak wrap →</text>
          </g>

          <!-- Step 2: back wrap -->
          <g id="ds2" style="opacity:0">
            <path d="M 8,108 L 392,108" fill="none" stroke="var(--acc-c)" stroke-width="4" stroke-linecap="round" opacity=".25"/>
            <path class="anim-path" style="--len:820"
              d="M 392,152
                 L 354,152 Q 361,152 361,170 Q 361,188 349,188 Q 294,188 294,170 Q 294,152 304,152
                 Q 316,152 316,170 Q 316,188 304,188
                 L 254,188 Q 244,188 244,170 Q 244,152 254,152
                 Q 266,152 266,170 Q 266,188 254,188
                 L 204,188 Q 194,188 194,170 Q 194,152 204,152
                 Q 216,152 216,170 Q 216,188 204,188
                 L 154,188 Q 144,188 144,170 Q 144,152 154,152
                 Q 166,152 166,170 Q 166,188 154,188
                 L 104,188 Q 94,188 94,170 Q 94,152 104,152
                 Q 116,152 116,170 Q 116,188 104,188
                 L 54,188 Q 44,188 44,170 Q 44,152 54,152
                 L 8,152"
              fill="none" stroke="var(--acc-c)" stroke-width="4.5" stroke-dasharray="9 3" stroke-linecap="round"/>
            <text x="200" y="215" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8.5" font-weight="300" fill="var(--acc-c)">back face — same yarn returns ←</text>
          </g>

          <!-- Step 3: result -->
          <g id="ds3" style="opacity:0">
            <rect x="8"  y="62" width="384" height="18" rx="2" fill="var(--acc-c)" opacity=".85"/>
            <rect x="8"  y="88" width="384" height="18" rx="2" fill="var(--acc-c)" opacity=".6"/>
            <rect x="8"  y="114" width="384" height="18" rx="2" fill="var(--acc-c)" opacity=".85"/>
            <rect x="8"  y="140" width="384" height="18" rx="2" fill="var(--acc-c)" opacity=".6"/>
            <rect x="8"  y="166" width="384" height="18" rx="2" fill="var(--acc-c)" opacity=".85"/>
            <!-- warp overlays -->
            <rect x="44"  y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="94"  y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="144" y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="194" y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="244" y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="294" y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <rect x="344" y="60" width="10" height="126" rx="4" fill="var(--warp-lt)" opacity=".3"/>
            <!-- thickness indicator -->
            <line x1="397" y1="62"  x2="397" y2="184" stroke="var(--acc-c)" stroke-width="1" opacity=".5"/>
            <line x1="394" y1="62"  x2="400" y2="62"  stroke="var(--acc-c)" stroke-width="1" opacity=".5"/>
            <line x1="394" y1="184" x2="400" y2="184" stroke="var(--acc-c)" stroke-width="1" opacity=".5"/>
            <text x="400" y="126" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--acc-c)"> 2×</text>
            <!-- badge -->
            <rect x="92" y="200" width="216" height="20" rx="2"
              fill="var(--bg)" stroke="var(--acc-c)" stroke-width=".8"/>
            <text x="200" y="213" text-anchor="middle"
              font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--acc-c)" letter-spacing=".06em">DOUBLE THICKNESS — REVERSIBLE</text>
          </g>
        </svg>
      </div>

      <div class="step-desc desc-c" id="desc-double-box"><span id="desc-double"></span></div>
      <div class="nav-row">
        <button class="nav-btn" id="prev-double" onclick="prev('double')" disabled>← Prev</button>
        <div class="progress-bar"><div class="progress-fill fill-c" id="fill-double" style="width:25%"></div></div>
        <span class="step-counter" id="ctr-double">1 / 4</span>
        <button class="nav-btn" id="next-double" onclick="next('double')">Next →</button>
      </div>
    </div>

  </div><!-- /.diagram-panel -->

  <!-- ──── RIGHT: Content ──── -->
  <div class="content-panel">

    <div class="section-label">Origins</div>
    <h2>Not woven, not knotted — <em>wrapped</em></h2>
    <p>
      Sumak is a flatweave in which the weft yarn <strong>wraps around warp threads</strong> rather
      than simply interlacing through them. The wrapping motion — forward over two warps, back under
      one — creates a characteristic diagonal texture on the front face, while loose threads float
      across the back.
    </p>
    <p>
      Named after the Azerbaijani town of <strong>Shemakha</strong>, the technique spans the Caucasus,
      eastern Anatolia, and northwestern Iran. Its three main variants each produce a distinct
      structural character: basic sumak for directional ridges, countered for herringbone,
      double for full reversibility.
    </p>

    <div class="fact-strip">
      <div class="fact-card">
        <div class="fv">2 + 1</div>
        <div class="fl">warps forward, one back — per wrap</div>
      </div>
      <div class="fact-card">
        <div class="fv">3</div>
        <div class="fl">structural variants</div>
      </div>
      <div class="fact-card">
        <div class="fv">1 000+</div>
        <div class="fl">years of documented production</div>
      </div>
      <div class="fact-card">
        <div class="fv">2-faced</div>
        <div class="fl">double sumak — identical both sides</div>
      </div>
    </div>

    <div class="section-label">Three Techniques</div>
    <h2>Each variant, <em>explained</em></h2>

    <div class="tech-cards">
      <div class="tc">
        <div class="tc-stripe"></div>
        <div class="tc-body">
          <div class="tc-name">Basic Sumak</div>
          <div class="tc-desc">The weft wraps forward over 2 warps, steps back under 1, then advances again. A plain "back thread" locks each row on the return pass. Front shows diagonal ridges; back shows floating yarns.</div>
        </div>
      </div>
      <div class="tc tc-b">
        <div class="tc-stripe tc-stripe-b"></div>
        <div class="tc-body">
          <div class="tc-name tc-b">Countered Sumak</div>
          <div class="tc-desc">Adjacent rows wrap in opposite directions. Where the opposing diagonals meet they produce a herringbone or chevron pattern — no back thread is needed between rows.</div>
        </div>
      </div>
      <div class="tc tc-c">
        <div class="tc-stripe tc-stripe-c"></div>
        <div class="tc-body">
          <div class="tc-name tc-c">Double Sumak</div>
          <div class="tc-desc">One continuous yarn wraps the front face on the forward pass, then wraps the back face on the return. Fully reversible, twice as thick, and the most labour-intensive of the three.</div>
        </div>
      </div>
    </div>

    <div class="section-label">Comparison</div>
    <h2>Sumak vs. <em>other flatweaves</em></h2>
    <div class="table-scroll">
      <table class="compare-table">
        <thead>
          <tr><th>Property</th><th>Sumak</th><th>Kilim</th><th>Pile rug</th></tr>
        </thead>
        <tbody>
          <tr class="hi"><td>Weft action</td><td>Wraps around warps</td><td>Over / under only</td><td>Knotted + weft rows</td></tr>
          <tr><td>Back face</td><td>Floating threads</td><td>Identical to front</td><td>Plain backing</td></tr>
          <tr class="hi"><td>Thickness</td><td>Medium–heavy</td><td>Thin and flat</td><td>Thick — pile height</td></tr>
          <tr><td>Reversible</td><td>Double sumak only</td><td>Always</td><td>Never</td></tr>
          <tr class="hi"><td>Surface texture</td><td>Diagonal ridges</td><td>Flat, smooth</td><td>Soft raised pile</td></tr>
          <tr><td>Durability</td><td>Very high</td><td>High</td><td>Pile wears over time</td></tr>
        </tbody>
      </table>
    </div>

    <div class="pull-quote">
      <p>In sumak the thread does not merely pass — it embraces the warp, locks it, and becomes part of its structure.</p>
      <cite>— Principle of Caucasian weaving tradition</cite>
    </div>

    <div class="section-label">Uses</div>
    <h2>Where sumak <em>is found</em></h2>
    <ul class="uses-list">
      <li><strong>Floor rugs</strong> — primary use; structurally durable for heavy daily traffic</li>
      <li><strong>Bags &amp; saddlebags (heybe, çuval)</strong> — the wrap's grip creates strong seams</li>
      <li><strong>Tent bands (yük yüzü)</strong> — long narrow sumak-woven structural belts</li>
      <li><strong>Mafrash (bedding bags)</strong> — Caucasian dowry chests woven in sumak</li>
      <li><strong>Wall hangings</strong> — especially double sumak for full reversibility</li>
      <li><strong>Contemporary upholstery</strong> — sumak texture in modern furnishing fabrics</li>
    </ul>

  </div><!-- /.content-panel -->

  <!-- ──── ANATOMY ──── -->
  <div class="anatomy-section">
    <div class="section-label" style="justify-content:center;max-width:280px;margin:0 auto 1rem">Structure</div>
    <h2>Anatomy of the sumak wrap — <em>labelled</em></h2>

    <div class="anatomy-tabs">
      <button class="atab active"  onclick="switchAnat('basic')">Basic</button>
      <button class="atab atab-b"  onclick="switchAnat('counter')">Countered</button>
      <button class="atab atab-c"  onclick="switchAnat('double')">Double</button>
    </div>

    <!-- Anatomy A -->
    <div class="anatomy-view active" id="anat-basic">
      <div class="anatomy-wrap">
        <svg class="anat-desktop" viewBox="0 0 900 230" width="100%" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg5" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="900" height="230" fill="url(#bg5)"/>
          <!-- Warps -->
          <rect x="200" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <rect x="270" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <rect x="340" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <rect x="410" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <rect x="480" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <rect x="550" y="10" width="10" height="210" rx="5" fill="var(--warp-lt)"/>
          <!-- Sumak row -->
          <path d="M 130,95 L 200,95 Q 193,95 193,77 Q 193,59 205,59 Q 270,59 270,77 Q 270,95 260,95 Q 248,95 248,77 Q 248,59 260,59 L 340,59 Q 350,59 350,77 Q 350,95 340,95 Q 328,95 328,77 Q 328,59 340,59 L 410,59 Q 420,59 420,77 Q 420,95 410,95 Q 398,95 398,77 Q 398,59 410,59 L 480,59 Q 490,59 490,77 Q 490,95 480,95 Q 468,95 468,77 Q 468,59 480,59 L 550,59 Q 560,59 560,77 Q 560,95 550,95 L 700,95"
            fill="none" stroke="var(--acc-a)" stroke-width="5" stroke-linecap="round"/>
          <!-- Back thread -->
          <path d="M 700,122 L 130,122"
            fill="none" stroke="var(--acc-a)" stroke-width="2.5" stroke-dasharray="7 4" stroke-linecap="round" opacity=".5"/>
          <!-- Labels -->
          <line x1="205" y1="10" x2="110" y2="8" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="205" cy="10" r="2" fill="var(--ink3)"/>
          <text x="107" y="7" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="400" fill="var(--ink3)" letter-spacing=".06em">Warp thread</text>

          <line x1="193" y1="77" x2="90" y2="60" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="193" cy="77" r="2" fill="var(--ink3)"/>
          <text x="87" y="57" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Forward over 2 warps</text>
          <text x="87" y="70" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">the advancing motion</text>

          <line x1="248" y1="77" x2="90" y2="108" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="248" cy="77" r="2" fill="var(--ink3)"/>
          <text x="87" y="105" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Back under 1 warp</text>
          <text x="87" y="118" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">locks the diagonal</text>

          <line x1="700" y1="122" x2="748" y2="122" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="700" cy="122" r="2" fill="var(--ink3)"/>
          <text x="752" y="126" text-anchor="start" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Back (return) thread</text>
          <text x="752" y="139" text-anchor="start" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">anchors all wraps in position</text>

          <line x1="553" y1="59" x2="720" y2="46" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="553" cy="59" r="2" fill="var(--ink3)"/>
          <text x="724" y="43" text-anchor="start" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Diagonal ridge</text>
          <text x="724" y="56" text-anchor="start" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">characteristic sumak surface texture</text>

          <rect x="310" y="178" width="260" height="18" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>
          <text x="440" y="191" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".1em">2 FORWARD · 1 BACK · BACK THREAD RETURNS</text>
        </svg>
        <svg class="anat-mobile" viewBox="0 0 300 240" width="100%" style="display:none" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg5m" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="300" height="240" fill="url(#bg5m)"/>
          <rect x="38"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="88"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="138" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="188" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="238" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <path d="M 8,97 L 38,97 Q 32,97 32,79 Q 32,62 42,62 Q 97,62 97,79 Q 97,97 88,97 Q 78,97 78,79 Q 78,62 88,62 L 138,62 Q 147,62 147,79 Q 147,97 138,97 Q 128,97 128,79 Q 128,62 138,62 L 188,62 Q 197,62 197,79 Q 197,97 188,97 Q 178,97 178,79 Q 178,62 188,62 L 238,62 Q 247,62 247,79 Q 247,97 238,97 L 292,97"
            fill="none" stroke="var(--acc-a)" stroke-width="4.5" stroke-linecap="round"/>
          <path d="M 292,122 L 8,122" fill="none" stroke="var(--acc-a)" stroke-width="2" stroke-dasharray="6 4" stroke-linecap="round" opacity=".5"/>
          <rect x="52" y="152" width="90" height="16" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
          <text x="97" y="163" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="500" fill="var(--ink)" letter-spacing=".06em">WRAP ROW</text>
          <rect x="155" y="132" width="110" height="16" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
          <text x="210" y="143" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="300" fill="var(--ink3)" letter-spacing=".06em">BACK THREAD</text>
        </svg>
        <ul class="anatomy-labels anat-labels" style="display:none">
          <li><span class="alabel">Forward wrap</span> The yarn passes over 2 warps, looping around them at a diagonal angle.</li>
          <li><span class="alabel">Back step</span> Returns under 1 warp before advancing — this locks the diagonal orientation in place.</li>
          <li><span class="alabel">Back thread</span> A plain weft thread on the return pass anchors all wraps and prevents unravelling.</li>
          <li><span class="alabel">Diagonal ridge</span> The accumulated wraps form a slanted surface texture characteristic of sumak.</li>
        </ul>
      </div>
    </div>

    <!-- Anatomy B -->
    <div class="anatomy-view" id="anat-counter">
      <div class="anatomy-wrap">
        <svg class="anat-desktop" viewBox="0 0 900 240" width="100%" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg6" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="900" height="240" fill="url(#bg6)"/>
          <rect x="225" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <rect x="295" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <rect x="365" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <rect x="435" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <rect x="505" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <rect x="575" y="10" width="10" height="220" rx="5" fill="var(--warp-lt)"/>
          <!-- Row A -->
          <path d="M 155,72 L 225,72 Q 218,72 218,54 Q 218,36 230,36 Q 295,36 295,54 Q 295,72 285,72 Q 273,72 273,54 Q 273,36 285,36 L 365,36 Q 375,36 375,54 Q 375,72 365,72 Q 353,72 353,54 Q 353,36 365,36 L 435,36 Q 445,36 445,54 Q 445,72 435,72 Q 423,72 423,54 Q 423,36 435,36 L 505,36 Q 515,36 515,54 Q 515,72 505,72 Q 493,72 493,54 Q 493,36 505,36 L 575,36 Q 585,36 585,54 Q 585,72 575,72 L 700,72"
            fill="none" stroke="var(--acc-b)" stroke-width="5" stroke-linecap="round"/>
          <!-- Row B -->
          <path d="M 700,122 L 575,122 Q 585,122 585,140 Q 585,158 575,158 Q 505,158 505,140 Q 505,122 515,122 Q 527,122 527,140 Q 527,158 515,158 L 435,158 Q 425,158 425,140 Q 425,122 435,122 Q 447,122 447,140 Q 447,158 435,158 L 365,158 Q 355,158 355,140 Q 355,122 365,122 Q 377,122 377,140 Q 377,158 365,158 L 295,158 Q 285,158 285,140 Q 285,122 295,122 Q 307,122 307,140 Q 307,158 295,158 L 225,158 Q 215,158 215,140 Q 215,122 225,122 L 155,122"
            fill="none" stroke="var(--acc-b)" stroke-width="5" stroke-linecap="round" opacity=".55"/>
          <!-- Labels -->
          <line x1="155" y1="72"  x2="80" y2="58"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="155" cy="72" r="2" fill="var(--ink3)"/>
          <text x="77" y="55" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Row A →</text>
          <text x="77" y="68" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">wraps left to right</text>

          <line x1="155" y1="122" x2="80" y2="128" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="155" cy="122" r="2" fill="var(--ink3)"/>
          <text x="77" y="125" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Row B ←</text>
          <text x="77" y="138" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">wraps right to left</text>

          <line x1="435" y1="72"  x2="750" y2="52" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="435" cy="72" r="2" fill="var(--ink3)"/>
          <text x="754" y="49" text-anchor="start" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Opposing wraps meet here</text>
          <text x="754" y="62" text-anchor="start" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">herringbone forms automatically</text>

          <rect x="290" y="186" width="280" height="18" rx="2" fill="var(--bg)" stroke="var(--acc-b)" stroke-width=".8"/>
          <text x="430" y="199" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--acc-b)" letter-spacing=".08em">TWO ROWS · OPPOSING DIRECTIONS · HERRINGBONE</text>
        </svg>
        <svg class="anat-mobile" viewBox="0 0 300 240" width="100%" style="display:none" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg6m" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="300" height="240" fill="url(#bg6m)"/>
          <rect x="38"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="88"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="138" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="188" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="238" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <path d="M 8,72 L 38,72 Q 32,72 32,55 Q 32,37 42,37 Q 97,37 97,55 Q 97,72 88,72 Q 78,72 78,55 Q 78,37 88,37 L 138,37 Q 147,37 147,55 Q 147,72 138,72 Q 128,72 128,55 Q 128,37 138,37 L 188,37 Q 197,37 197,55 Q 197,72 188,72 Q 178,72 178,55 Q 178,37 188,37 L 238,37 Q 247,37 247,55 Q 247,72 238,72 L 292,72"
            fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round"/>
          <path d="M 292,118 L 238,118 Q 247,118 247,136 Q 247,153 238,153 Q 188,153 188,136 Q 188,118 197,118 Q 208,118 208,136 Q 208,153 188,153 L 138,153 Q 128,153 128,136 Q 128,118 138,118 Q 150,118 150,136 Q 150,153 138,153 L 88,153 Q 78,153 78,136 Q 78,118 88,118 Q 100,118 100,136 Q 100,153 88,153 L 38,153 Q 28,153 28,136 Q 28,118 38,118 L 8,118"
            fill="none" stroke="var(--acc-b)" stroke-width="4.5" stroke-linecap="round" opacity=".55"/>
          <rect x="30"  y="170" width="80" height="16" rx="2" fill="var(--bg)" stroke="var(--acc-b)" stroke-width=".7"/>
          <text x="70"  y="181" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="500" fill="var(--acc-b)" letter-spacing=".05em">ROW A →</text>
          <rect x="188" y="170" width="80" height="16" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
          <text x="228" y="181" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="400" fill="var(--acc-b)" opacity=".6" letter-spacing=".05em">ROW B ←</text>
        </svg>
        <ul class="anatomy-labels anat-labels" style="display:none">
          <li><span class="alabel alabel-b">Row A →</span> Wraps travel left to right — diagonal ridges angle in one direction across the fabric.</li>
          <li><span class="alabel alabel-b">Row B ←</span> The next row wraps right to left — ridges angle the opposite way.</li>
          <li><span class="alabel alabel-b">Herringbone</span> Where opposing wraps meet, a V-shaped chevron emerges from the structure automatically.</li>
          <li><span class="alabel alabel-b">No back thread</span> Countered rows lock each other — no additional plain-weave row is needed.</li>
        </ul>
      </div>
    </div>

    <!-- Anatomy C -->
    <div class="anatomy-view" id="anat-double">
      <div class="anatomy-wrap">
        <svg class="anat-desktop" viewBox="0 0 900 250" width="100%" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg7" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="900" height="250" fill="url(#bg7)"/>
          <rect x="215" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <rect x="285" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <rect x="355" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <rect x="425" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <rect x="495" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <rect x="565" y="10" width="10" height="225" rx="5" fill="var(--warp-lt)"/>
          <!-- Front wrap -->
          <path d="M 140,72 L 215,72 Q 208,72 208,54 Q 208,36 220,36 Q 285,36 285,54 Q 285,72 275,72 Q 263,72 263,54 Q 263,36 275,36 L 355,36 Q 365,36 365,54 Q 365,72 355,72 Q 343,72 343,54 Q 343,36 355,36 L 425,36 Q 435,36 435,54 Q 435,72 425,72 Q 413,72 413,54 Q 413,36 425,36 L 495,36 Q 505,36 505,54 Q 505,72 495,72 Q 483,72 483,54 Q 483,36 495,36 L 565,36 Q 575,36 575,54 Q 575,72 565,72 L 700,72"
            fill="none" stroke="var(--acc-c)" stroke-width="5" stroke-linecap="round"/>
          <!-- Back wrap -->
          <path d="M 700,128 L 565,128 Q 575,128 575,146 Q 575,164 565,164 Q 495,164 495,146 Q 495,128 505,128 Q 517,128 517,146 Q 517,164 505,164 L 425,164 Q 415,164 415,146 Q 415,128 425,128 Q 437,128 437,146 Q 437,164 425,164 L 355,164 Q 345,164 345,146 Q 345,128 355,128 Q 367,128 367,146 Q 367,164 355,164 L 285,164 Q 275,164 275,146 Q 275,128 285,128 Q 297,128 297,146 Q 297,164 285,164 L 215,164 Q 205,164 205,146 Q 205,128 215,128 L 140,128"
            fill="none" stroke="var(--acc-c)" stroke-width="5" stroke-dasharray="9 3" stroke-linecap="round"/>
          <!-- Thickness brace -->
          <line x1="720" y1="36"  x2="720" y2="164" stroke="var(--acc-c)" stroke-width="1" opacity=".4"/>
          <line x1="717" y1="36"  x2="723" y2="36"  stroke="var(--acc-c)" stroke-width="1" opacity=".4"/>
          <line x1="717" y1="164" x2="723" y2="164" stroke="var(--acc-c)" stroke-width="1" opacity=".4"/>
          <!-- Labels -->
          <line x1="220" y1="10" x2="118" y2="8"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="220" cy="10" r="2" fill="var(--ink3)"/>
          <text x="115" y="7" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="400" fill="var(--ink3)" letter-spacing=".06em">Warp</text>

          <line x1="140" y1="72"  x2="62" y2="58"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="140" cy="72" r="2" fill="var(--ink3)"/>
          <text x="59" y="55" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Front face</text>
          <text x="59" y="68" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">forward wraps →</text>

          <line x1="140" y1="128" x2="62" y2="136" stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>
          <circle cx="140" cy="128" r="2" fill="var(--ink3)"/>
          <text x="59" y="133" text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Back face</text>
          <text x="59" y="146" text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">same yarn returns ←</text>

          <text x="736" y="104" font-family="Outfit,sans-serif" font-size="9" font-weight="500" fill="var(--acc-c)"> 2×</text>
          <text x="736" y="116" font-family="Outfit,sans-serif" font-size="7.5" font-weight="300" fill="var(--ink3)">thick</text>

          <rect x="305" y="195" width="270" height="18" rx="2" fill="var(--bg)" stroke="var(--acc-c)" stroke-width=".8"/>
          <text x="440" y="208" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--acc-c)" letter-spacing=".08em">ONE YARN · TWO FACES · DOUBLE THICKNESS</text>
        </svg>
        <svg class="anat-mobile" viewBox="0 0 300 240" width="100%" style="display:none" xmlns="http://www.w3.org/2000/svg">
          <defs><pattern id="bg7m" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>
          <rect width="300" height="240" fill="url(#bg7m)"/>
          <rect x="38"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="88"  y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="138" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="188" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <rect x="238" y="10" width="9" height="215" rx="4.5" fill="var(--warp-lt)"/>
          <path d="M 8,72 L 38,72 Q 32,72 32,55 Q 32,37 42,37 Q 97,37 97,55 Q 97,72 88,72 Q 78,72 78,55 Q 78,37 88,37 L 138,37 Q 147,37 147,55 Q 147,72 138,72 Q 128,72 128,55 Q 128,37 138,37 L 188,37 Q 197,37 197,55 Q 197,72 188,72 Q 178,72 178,55 Q 178,37 188,37 L 238,37 Q 247,37 247,55 Q 247,72 238,72 L 292,72"
            fill="none" stroke="var(--acc-c)" stroke-width="4.5" stroke-linecap="round"/>
          <path d="M 292,118 L 238,118 Q 247,118 247,136 Q 247,153 238,153 Q 188,153 188,136 Q 188,118 197,118 Q 208,118 208,136 Q 208,153 188,153 L 138,153 Q 128,153 128,136 Q 128,118 138,118 Q 150,118 150,136 Q 150,153 138,153 L 88,153 Q 78,153 78,136 Q 78,118 88,118 Q 100,118 100,136 Q 100,153 88,153 L 38,153 Q 28,153 28,136 Q 28,118 38,118 L 8,118"
            fill="none" stroke="var(--acc-c)" stroke-width="4.5" stroke-dasharray="8 3" stroke-linecap="round"/>
          <rect x="28"  y="172" width="88" height="16" rx="2" fill="var(--bg)" stroke="var(--acc-c)" stroke-width=".7"/>
          <text x="72"  y="183" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="500" fill="var(--acc-c)" letter-spacing=".05em">FRONT FACE</text>
          <rect x="182" y="172" width="88" height="16" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>
          <text x="226" y="183" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="400" fill="var(--acc-c)" opacity=".7" letter-spacing=".05em">BACK FACE</text>
        </svg>
        <ul class="anatomy-labels anat-labels" style="display:none">
          <li><span class="alabel alabel-c">Front face</span> The yarn advances left to right, wrapping warps in the standard 2-forward-1-back motion.</li>
          <li><span class="alabel alabel-c">Back face</span> The same uncut yarn returns right to left, wrapping the underside of the same warps.</li>
          <li><span class="alabel alabel-c">Double thickness</span> Both faces wrapped means the fabric is roughly twice as thick as basic sumak.</li>
          <li><span class="alabel alabel-c">Reversible</span> Front and back show the same pattern — there is no "wrong side" to the fabric.</li>
        </ul>
      </div>
    </div>

  </div><!-- /.anatomy-section -->

</main>

<footer>
  Sumak · Caucasian &amp; Anatolian Flatweave Education
</footer>

<script>
const DATA = {
  basic: {
    cur: 0,
    descs: [
      `The loom is strung with <strong>vertical warp threads</strong> held under constant tension. In sumak, warps are spaced slightly wider than in kilim, giving the wrapping yarn room to grip each thread firmly before advancing.`,
      `The weft yarn <strong>wraps forward over 2 warps</strong>, then steps back under 1. This "2 forward, 1 back" action is the defining motion of sumak — it binds the thread diagonally around each warp pair and creates the signature angled ridge.`,
      `The wrapping repeats across the <strong>full width of the loom</strong>. Every pair of warps receives the same motion, building a continuous diagonal row. The front face shows clean angular texture; the back shows loose floating threads.`,
      `On the return pass, a <strong>plain back thread</strong> travels straight across all warps. This thread locks every wrap in position and is structurally essential — without it, the entire row would shift. The same or a contrasting yarn may be used.`
    ]
  },
  counter: {
    cur: 0,
    descs: [
      `Countered sumak uses <strong>two rows worked in opposite directions</strong>. Row A travels left to right; Row B immediately follows traveling right to left. Neither row is a plain thread — both are full wrapping rows.`,
      `<strong>Row A wraps left to right</strong>. Each wrap advances over 2 warps then steps back under 1, producing diagonal ridges that angle from lower-left to upper-right across the full width of the fabric.`,
      `<strong>Row B wraps in the opposite direction</strong> — right to left — with ridges angling the other way. The two rows lock each other: no separate back thread is needed between them, making the structure more compact.`,
      `Where the opposing rows meet, their diagonal ridges form a <strong>herringbone or chevron pattern</strong>. This is not drawn by the weaver — it emerges automatically from the structure, creating complex geometry from a simple technique.`
    ]
  },
  double: {
    cur: 0,
    descs: [
      `Double sumak uses a <strong>single continuous yarn to wrap both faces</strong> of the fabric. The thread advances across the front, wrapping warps in the standard sumak motion, then returns across the back, wrapping them again.`,
      `The <strong>front face is completed first</strong> — the yarn travels across wrapping 2 warps forward, 1 back, creating the diagonal ridges and pattern visible from the top side of the finished textile.`,
      `Without cutting the thread, the <strong>same yarn continues back</strong> across the underside. It wraps the back of the same warps in the reverse direction, producing an identical mirror pattern on the second face.`,
      `The result is a <strong>fully reversible fabric with double thickness</strong>. Front and back carry the same pattern. Double sumak is the most labour-intensive of the three variants and produces the most structurally substantial textiles.`
    ]
  }
};

function goTo(tech, n) {
  DATA[tech].cur = n;
  const prefix = tech === 'basic' ? 'bs' : tech === 'counter' ? 'cs' : 'ds';
  const svg = document.querySelector(`#panel-${tech} svg`);
  [0,1,2,3].forEach(i => {
    const el = svg.querySelector(`#${prefix}${i}`);
    if (el) { el.style.transition = 'opacity .3s'; el.style.opacity = i === n ? '1' : '0'; }
  });
  const cur = svg.querySelector(`#${prefix}${n}`);
  if (cur) {
    cur.querySelectorAll('.anim-path').forEach(p => {
      const m = p.style.cssText.match(/--len:\s*([\d.]+)/);
      const len = m ? parseFloat(m[1]) : 400;
      p.style.animation = 'none'; void p.offsetWidth;
      p.style.strokeDasharray = len; p.style.strokeDashoffset = len;
      setTimeout(() => {
        p.style.animation = 'drawPath .9s cubic-bezier(.4,0,.2,1) forwards';
        p.style.strokeDashoffset = 0;
      }, 30);
    });
  }
  // pills
  const activeClass = tech === 'counter' ? 'active-b' : tech === 'double' ? 'active-c' : 'active';
  document.querySelectorAll(`#pills-${tech} .step-pill`).forEach((b, i) => {
    b.className = 'step-pill';
    if (i === n) b.classList.add(activeClass);
  });
  // progress bar + counter
  document.getElementById(`fill-${tech}`).style.width = `${(n + 1) * 25}%`;
  document.getElementById(`ctr-${tech}`).textContent = `${n + 1} / 4`;
  // buttons
  document.getElementById(`prev-${tech}`).disabled = n === 0;
  document.getElementById(`next-${tech}`).disabled = n === 3;
  // desc
  const box = document.getElementById(`desc-${tech}-box`);
  box.style.animation = 'none'; void box.offsetWidth;
  box.style.animation = 'fadeUp .38s ease forwards';
  document.getElementById(`desc-${tech}`).innerHTML = DATA[tech].descs[n];
}

function next(t) { const d = DATA[t]; if (d.cur < 3) goTo(t, d.cur + 1); }
function prev(t) { const d = DATA[t]; if (d.cur > 0) goTo(t, d.cur - 1); }

function switchTech(tech) {
  document.querySelectorAll('.tech-panel').forEach(p => p.classList.remove('active'));
  document.getElementById(`panel-${tech}`).classList.add('active');
  document.querySelectorAll('.tech-tab').forEach((b, i) => {
    b.classList.toggle('active', ['basic','counter','double'][i] === tech);
  });
}

function switchAnat(id) {
  document.querySelectorAll('.anatomy-view').forEach(v => v.classList.remove('active'));
  document.querySelectorAll('.atab').forEach((b, i) => {
    b.classList.toggle('active', ['basic','counter','double'][i] === id);
  });
  document.getElementById(`anat-${id}`).classList.add('active');
}

function updateAnatomy() {
  const mob = window.innerWidth <= 600;
  document.querySelectorAll('.anat-desktop').forEach(el => el.style.display = mob ? 'none' : 'block');
  document.querySelectorAll('.anat-mobile').forEach(el  => el.style.display = mob ? 'block' : 'none');
  document.querySelectorAll('.anat-labels').forEach(el  => el.style.display = mob ? 'block' : 'none');
}
updateAnatomy();
window.addEventListener('resize', updateAnatomy);

document.addEventListener('keydown', e => {
  const active = document.querySelector('.tech-panel.active');
  const tech = active ? active.id.replace('panel-','') : 'basic';
  if (e.key === 'ArrowRight') next(tech);
  if (e.key === 'ArrowLeft')  prev(tech);
});

goTo('basic',   0);
goTo('counter', 0);
goTo('double',  0);
</script>
</body>
</html>