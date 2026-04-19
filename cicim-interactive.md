
---
layout: default

title: Sayfa Başlığı (Opsiyonel)
---



<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Cicim — Embroidered Flatweave</title>

<link rel="preconnect" href="https://fonts.googleapis.com">

<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,300;1,9..144,400\&family=Outfit:wght@200;300;400;500\&family=Libre+Baskerville:ital@1\&display=swap" rel="stylesheet">



<style>

:root {

&#x20; --bg:       #f7f6f3;

&#x20; --bg2:      #efede8;

&#x20; --bg3:      #e6e3dc;

&#x20; --line:     #d8d4cb;

&#x20; --line2:    #bdb9b0;

&#x20; --ink:      #1c1b18;

&#x20; --ink2:     #4a4840;

&#x20; --ink3:     #7c7970;

&#x20; --warp:     #a8a39c;

&#x20; --warp-lt:  #c8c4bc;

&#x20; --base-weft:#7c7970;

&#x20; /\* cicim accent — the embroidery thread \*/

&#x20; --emb:      #1c1b18;

&#x20; --emb2:     #4a4840;

&#x20; /\* motif palette — restrained, editorial \*/

&#x20; --mot-a:    #2c4a6e;   /\* slate blue \*/

&#x20; --mot-b:    #6e2c2c;   /\* deep red \*/

&#x20; --mot-c:    #2c6e4a;   /\* forest green \*/

&#x20; --mot-d:    #6e5a2c;   /\* warm ochre \*/

&#x20; --mot-e:    #4a2c6e;   /\* plum \*/

}



\*,\*::before,\*::after{box-sizing:border-box;margin:0;padding:0}

html{scroll-behavior:smooth}

body{

&#x20; background:var(--bg);

&#x20; background-image:url("data:image/svg+xml,%3Csvg width='24' height='24' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='1' cy='1' r='.55' fill='%23c8c4bc' fill-opacity='.35'/%3E%3C/svg%3E");

&#x20; color:var(--ink);

&#x20; font-family:'Outfit',sans-serif;

&#x20; font-weight:300;

&#x20; min-height:100vh;

&#x20; overflow-x:hidden;

}



/\* ═══ HEADER ═══ \*/

header{

&#x20; text-align:center;

&#x20; padding:3.5rem 1.5rem 2.5rem;

&#x20; border-bottom:1px solid var(--line);

}

@media(max-width:500px){header{padding:2rem 1rem 1.5rem}}



.eyebrow{

&#x20; font-size:.65rem;font-weight:400;

&#x20; letter-spacing:.35em;text-transform:uppercase;

&#x20; color:var(--ink3);margin-bottom:1.6rem;

}



/\* Cicim pattern strip — embroidery diamonds on base weave \*/

.cicim-strip{display:flex;justify-content:center;margin:0 auto 1.4rem;width:fit-content}



h1{

&#x20; font-family:'Fraunces',serif;

&#x20; font-size:clamp(2.6rem,6.5vw,5rem);

&#x20; font-weight:300;letter-spacing:.01em;line-height:1.06;

&#x20; color:var(--ink);margin-bottom:.55rem;

}

h1 em{font-style:italic;color:var(--ink2)}

.subtitle{font-size:.92rem;font-weight:200;letter-spacing:.08em;color:var(--ink3);margin-bottom:.25rem}

.aka{font-family:'Libre Baskerville',serif;font-size:.92rem;font-style:italic;color:var(--ink3)}



/\* ═══ LAYOUT ═══ \*/

main{

&#x20; max-width:1120px;margin:0 auto;

&#x20; padding:3rem 2rem 5rem;

&#x20; display:grid;grid-template-columns:1fr 1fr;

&#x20; gap:3rem 4.5rem;align-items:start;

}

@media(max-width:800px){main{grid-template-columns:1fr;gap:2rem;padding:1.5rem 1rem 3rem}}



/\* ═══ DIAGRAM PANEL ═══ \*/

.diagram-panel{position:sticky;top:2rem}

@media(max-width:800px){.diagram-panel{position:static}}



/\* Tabs \*/

.main-tabs{

&#x20; display:flex;border-bottom:1.5px solid var(--line);

&#x20; margin-bottom:1.4rem;

}

.main-tab{

&#x20; flex:1;background:none;border:none;

&#x20; padding:.65rem .5rem;

&#x20; font-family:'Outfit',sans-serif;

&#x20; font-size:.68rem;font-weight:400;

&#x20; letter-spacing:.14em;text-transform:uppercase;

&#x20; color:var(--ink3);

&#x20; border-bottom:2.5px solid transparent;

&#x20; margin-bottom:-1.5px;

&#x20; cursor:pointer;transition:all .2s;text-align:center;

}

.main-tab:hover{color:var(--ink2)}

.main-tab.active{color:var(--ink);border-bottom-color:var(--ink)}



/\* Step pills \*/

.step-pills{display:flex;gap:.32rem;flex-wrap:wrap;margin-bottom:1.1rem}

.step-pill{

&#x20; background:none;border:1px solid var(--line);border-radius:2px;

&#x20; padding:.26rem .72rem;

&#x20; font-family:'Outfit',sans-serif;font-size:.6rem;

&#x20; font-weight:400;letter-spacing:.1em;text-transform:uppercase;

&#x20; color:var(--ink3);cursor:pointer;transition:all .2s;

}

.step-pill:hover{border-color:var(--line2);color:var(--ink2)}

.step-pill.sp-active{background:var(--ink);border-color:var(--ink);color:var(--bg)}



/\* SVG canvas \*/

.svg-wrap{

&#x20; background:var(--bg2);border:1px solid var(--line);

&#x20; border-radius:3px;overflow:hidden;aspect-ratio:4/3;

}

.svg-wrap svg{width:100%;height:100%;display:block}



/\* Description \*/

.step-desc{

&#x20; margin-top:1.1rem;padding:1rem 1.15rem;

&#x20; background:var(--bg2);border-left:2px solid var(--line2);

&#x20; font-size:.88rem;line-height:1.82;color:var(--ink2);min-height:4.5rem;

}

.step-desc strong{color:var(--ink);font-weight:500}



/\* Nav \*/

.nav-row{display:flex;align-items:center;justify-content:space-between;margin-top:.9rem}

.nav-btn{

&#x20; background:none;border:1px solid var(--line);border-radius:2px;

&#x20; padding:.42rem .95rem;

&#x20; font-family:'Outfit',sans-serif;font-size:.65rem;

&#x20; font-weight:400;letter-spacing:.12em;text-transform:uppercase;

&#x20; color:var(--ink3);cursor:pointer;transition:all .2s;

}

.nav-btn:hover:not(:disabled){border-color:var(--line2);color:var(--ink)}

.nav-btn:disabled{opacity:.25;cursor:default}

.progress-bar{flex:1;height:2px;background:var(--line);margin:0 1rem;position:relative;border-radius:1px;overflow:hidden}

.progress-fill{position:absolute;top:0;left:0;height:100%;background:var(--ink);border-radius:1px;transition:width .35s cubic-bezier(.4,0,.2,1)}

.step-counter{font-size:.65rem;font-weight:400;letter-spacing:.1em;color:var(--ink3);white-space:nowrap}



.panel{display:none}

.panel.active{display:block}



/\* ═══ MOTIF GRID (inside diagram panel panel-motifs) ═══ \*/

.motif-grid{

&#x20; display:grid;grid-template-columns:1fr 1fr;

&#x20; gap:.75rem;margin-top:.2rem;

}

.motif-card{

&#x20; background:var(--bg2);border:1px solid var(--line);border-radius:3px;

&#x20; overflow:hidden;cursor:pointer;transition:border-color .2s;

}

.motif-card:hover{border-color:var(--line2)}

.motif-card.selected{border-color:var(--ink)}

.motif-svg{width:100%;aspect-ratio:1;display:block;background:var(--bg2)}

.motif-label{

&#x20; padding:.5rem .7rem;

&#x20; font-family:'Outfit',sans-serif;font-size:.65rem;

&#x20; font-weight:500;letter-spacing:.1em;text-transform:uppercase;

&#x20; color:var(--ink2);border-top:1px solid var(--line);

}

/\* Motif detail panel \*/

.motif-detail{

&#x20; margin-top:1rem;padding:1rem 1.15rem;

&#x20; background:var(--bg2);border-left:2px solid var(--line2);

&#x20; font-size:.88rem;line-height:1.82;color:var(--ink2);

&#x20; min-height:4rem;

}

.motif-detail strong{color:var(--ink);font-weight:500}

.motif-detail .mot-name{

&#x20; font-family:'Outfit',sans-serif;font-size:.65rem;

&#x20; font-weight:500;letter-spacing:.14em;text-transform:uppercase;

&#x20; color:var(--ink3);margin-bottom:.4rem;

}



/\* ═══ CONTENT PANEL ═══ \*/

.content-panel{padding-top:.4rem}



.section-label{

&#x20; font-family:'Outfit',sans-serif;font-size:.62rem;font-weight:500;

&#x20; letter-spacing:.3em;text-transform:uppercase;color:var(--ink3);

&#x20; margin-bottom:.9rem;display:flex;align-items:center;gap:.8rem;

}

.section-label::after{content:'';flex:1;height:1px;background:linear-gradient(to right,var(--line),transparent)}



h2{font-family:'Fraunces',serif;font-size:1.9rem;font-weight:300;line-height:1.2;margin-bottom:1rem;color:var(--ink)}

h2 em{font-style:italic;color:var(--ink2)}



p{font-size:.9rem;line-height:1.9;color:var(--ink2);margin-bottom:1rem}

p strong{color:var(--ink);font-weight:400}



.fact-strip{display:grid;grid-template-columns:1fr 1fr;gap:.65rem;margin:1.5rem 0}

.fact-card{background:var(--bg2);border:1px solid var(--line);border-radius:3px;padding:.85rem .95rem}

.fact-card .fv{font-family:'Fraunces',serif;font-size:1.5rem;font-weight:400;color:var(--ink);line-height:1;margin-bottom:.2rem}

.fact-card .fl{font-size:.7rem;letter-spacing:.06em;color:var(--ink3);font-weight:300}



/\* Distinction box — cicim vs zili \*/

.distinction-box{

&#x20; display:grid;grid-template-columns:1fr 1fr;

&#x20; gap:.65rem;margin:1.4rem 0;

}

.dist-col{

&#x20; background:var(--bg2);border:1px solid var(--line);

&#x20; border-radius:3px;padding:.9rem 1rem;

}

.dist-col:first-child{border-top:2px solid var(--ink)}

.dist-col:last-child{border-top:2px solid var(--line2)}

.dist-head{

&#x20; font-family:'Outfit',sans-serif;font-size:.65rem;font-weight:500;

&#x20; letter-spacing:.14em;text-transform:uppercase;color:var(--ink);

&#x20; margin-bottom:.6rem;

}

.dist-col:last-child .dist-head{color:var(--ink3)}

.dist-item{

&#x20; font-size:.82rem;line-height:1.6;color:var(--ink2);

&#x20; padding:.28rem 0;border-bottom:1px solid var(--line);

}

.dist-item:last-child{border-bottom:none}

.dist-item::before{content:'· ';color:var(--ink3)}



/\* Compare table \*/

.table-scroll{width:100%;overflow-x:auto;-webkit-overflow-scrolling:touch;margin:1.4rem 0;border:1px solid var(--line);border-radius:3px}

.compare-table{width:100%;min-width:380px;border-collapse:collapse;font-size:.83rem}

.compare-table thead tr{border-bottom:1px solid var(--line2)}

.compare-table th{

&#x20; font-family:'Outfit',sans-serif;font-size:.6rem;font-weight:500;

&#x20; letter-spacing:.18em;text-transform:uppercase;color:var(--ink3);

&#x20; padding:.55rem .85rem;text-align:left;white-space:nowrap;background:var(--bg2);

}

.compare-table td{padding:.55rem .85rem;border-bottom:1px solid var(--line);color:var(--ink2);vertical-align:top;line-height:1.55}

.compare-table td:first-child{color:var(--ink);font-weight:400;white-space:nowrap}

.compare-table tr:last-child td{border-bottom:none}

.compare-table .hi td{background:var(--bg2)}



.pull-quote{margin:1.8rem 0;padding:1.4rem 1.8rem;border-top:1px solid var(--line);border-bottom:1px solid var(--line);position:relative}

.pull-quote::before{content:'\\201C';font-family:'Fraunces',serif;font-size:5rem;color:var(--line2);position:absolute;top:-.6rem;left:.7rem;line-height:1}

.pull-quote p{font-family:'Fraunces',serif;font-size:1.2rem;font-style:italic;line-height:1.65;color:var(--ink);margin-bottom:.4rem}

.pull-quote cite{font-size:.7rem;letter-spacing:.1em;color:var(--ink3)}



.uses-list{list-style:none;margin:.4rem 0 1.4rem}

.uses-list li{display:flex;align-items:baseline;gap:.7rem;font-size:.86rem;color:var(--ink2);padding:.42rem 0;border-bottom:1px solid var(--line);line-height:1.55}

.uses-list li::before{content:'';display:inline-block;width:4px;height:4px;border-radius:50%;background:var(--line2);flex-shrink:0;transform:translateY(-1px)}

.uses-list strong{color:var(--ink);font-weight:400}



/\* ═══ ANATOMY ═══ \*/

.anatomy-section{grid-column:1/-1;padding-top:2.5rem;border-top:1px solid var(--line)}

.anatomy-section h2{text-align:center;font-size:1.6rem;margin-bottom:1.8rem}

.anatomy-wrap{background:var(--bg2);border:1px solid var(--line);border-radius:3px;padding:1rem;overflow-x:auto}

.anat-mobile{display:none}

.anatomy-labels{list-style:none;margin-top:.8rem}

.anatomy-labels li{display:flex;gap:.65rem;align-items:baseline;font-size:.83rem;line-height:1.68;color:var(--ink2);padding:.42rem 0;border-bottom:1px solid var(--line)}

.alabel{font-family:'Outfit',sans-serif;font-size:.62rem;font-weight:500;letter-spacing:.1em;text-transform:uppercase;color:var(--ink);white-space:nowrap;flex-shrink:0}



footer{text-align:center;padding:2.5rem 1rem;border-top:1px solid var(--line);font-size:.72rem;letter-spacing:.1em;color:var(--ink3)}



/\* Animations \*/

@keyframes drawPath{from{stroke-dashoffset:var(--len)}to{stroke-dashoffset:0}}

@keyframes fadeUp{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}

@keyframes popIn{from{opacity:0;transform:scale(.94)}to{opacity:1;transform:scale(1)}}

.anim-path{stroke-dasharray:var(--len);stroke-dashoffset:var(--len)}



@media(max-width:500px){

&#x20; h1{font-size:2.2rem} h2{font-size:1.5rem}

&#x20; p,.step-desc,.motif-detail{font-size:.84rem}

&#x20; .fact-card .fv{font-size:1.3rem}

&#x20; .main-tab{font-size:.6rem;padding:.55rem .3rem}

&#x20; .step-pill{font-size:.56rem;padding:.22rem .6rem}

&#x20; .motif-grid{grid-template-columns:1fr 1fr}

&#x20; .distinction-box{grid-template-columns:1fr}

&#x20; .anatomy-section h2{font-size:1.3rem}

}

</style>

</head>

<body>



<!-- ═══ HEADER ═══ -->

<header>

&#x20; <p class="eyebrow">Anatolia · Embroidered Flatweave</p>



&#x20; <!-- Cicim decorative strip: base weft + embroidery diamonds on top -->

&#x20; <div class="cicim-strip">

&#x20;   <svg viewBox="0 0 300 36" width="300" height="36" xmlns="http://www.w3.org/2000/svg">

&#x20;     <rect width="300" height="36" fill="var(--bg2)" rx="2"/>

&#x20;     <!-- base weft bands -->

&#x20;     <rect y="0"  width="300" height="6"  fill="var(--warp-lt)" opacity=".6"/>

&#x20;     <rect y="7"  width="300" height="5"  fill="var(--warp)"    opacity=".5"/>

&#x20;     <rect y="13" width="300" height="10" fill="var(--bg2)"/>

&#x20;     <rect y="24" width="300" height="5"  fill="var(--warp)"    opacity=".5"/>

&#x20;     <rect y="30" width="300" height="6"  fill="var(--warp-lt)" opacity=".6"/>

&#x20;     <!-- embroidery diamonds overlaid -->

&#x20;     <polygon points="30,18 38,10 46,18 38,26"  fill="var(--mot-a)" opacity=".85"/>

&#x20;     <polygon points="70,18 78,10 86,18 78,26"  fill="var(--mot-b)" opacity=".85"/>

&#x20;     <polygon points="110,18 118,10 126,18 118,26" fill="var(--mot-c)" opacity=".85"/>

&#x20;     <polygon points="150,18 158,10 166,18 158,26" fill="var(--mot-d)" opacity=".85"/>

&#x20;     <polygon points="190,18 198,10 206,18 198,26" fill="var(--mot-a)" opacity=".85"/>

&#x20;     <polygon points="230,18 238,10 246,18 238,26" fill="var(--mot-e)" opacity=".85"/>

&#x20;     <polygon points="270,18 278,10 286,18 278,26" fill="var(--mot-b)" opacity=".85"/>

&#x20;     <!-- connecting stitch line -->

&#x20;     <line x1="10" y1="18" x2="290" y2="18" stroke="var(--ink3)" stroke-width=".8" stroke-dasharray="3 5" opacity=".4"/>

&#x20;   </svg>

&#x20; </div>



&#x20; <h1><em>Cicim</em> Weaving</h1>

&#x20; <p class="subtitle">An Interactive Guide to Anatolian Embroidered Flatweave</p>

&#x20; <p class="aka">A flatweave enriched by supplementary embroidery thread</p>

</header>



<!-- ═══ MAIN ═══ -->

<main>



&#x20; <!-- ──── LEFT: Diagram ──── -->

&#x20; <div class="diagram-panel">



&#x20;   <div class="main-tabs">

&#x20;     <button class="main-tab active" onclick="switchMain('technique')">Technique</button>

&#x20;     <button class="main-tab"        onclick="switchMain('motifs')">Motifs</button>

&#x20;   </div>



&#x20;   <!-- ── PANEL: Technique ── -->

&#x20;   <div class="panel active" id="panel-technique">

&#x20;     <div class="step-pills" id="pills-tech">

&#x20;       <button class="step-pill sp-active" onclick="goToTech(0)">I · Base</button>

&#x20;       <button class="step-pill"           onclick="goToTech(1)">II · Shed</button>

&#x20;       <button class="step-pill"           onclick="goToTech(2)">III · Embroider</button>

&#x20;       <button class="step-pill"           onclick="goToTech(3)">IV · Pattern</button>

&#x20;       <button class="step-pill"           onclick="goToTech(4)">V · Complete</button>

&#x20;     </div>



&#x20;     <div class="svg-wrap">

&#x20;       <svg id="tech-svg" viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">

&#x20;         <defs>

&#x20;           <marker id="arT" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">

&#x20;             <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>

&#x20;           </marker>

&#x20;           <pattern id="bgT" width="20" height="20" patternUnits="userSpaceOnUse">

&#x20;             <circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".45"/>

&#x20;           </pattern>

&#x20;         </defs>

&#x20;         <rect width="400" height="300" fill="url(#bgT)"/>



&#x20;         <!-- Shared: warp threads -->

&#x20;         <g id="t-warps">

&#x20;           <rect x="36"  y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="37"  y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="86"  y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="87"  y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="136" y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="137" y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="186" y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="187" y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="236" y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="237" y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="286" y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="287" y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <rect x="336" y="14" width="8" height="272" rx="4" fill="var(--warp-lt)"/>

&#x20;           <rect x="337" y="14" width="2" height="272" rx="1" fill="rgba(255,255,255,.4)"/>

&#x20;           <text x="40"  y="294" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" fill="var(--ink3)" letter-spacing=".3" font-weight="400">W</text>

&#x20;           <text x="340" y="294" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" fill="var(--ink3)" letter-spacing=".3" font-weight="400">W</text>

&#x20;         </g>



&#x20;         <!-- Step 0: base weave — weft bands -->

&#x20;         <g id="t0">

&#x20;           <path class="anim-path" style="--len:400"

&#x20;             d="M 8,100 L 392,100"

&#x20;             fill="none" stroke="var(--base-weft)" stroke-width="5" stroke-linecap="round"/>

&#x20;           <path class="anim-path" style="--len:400"

&#x20;             d="M 392,120 L 8,120"

&#x20;             fill="none" stroke="var(--base-weft)" stroke-width="5" stroke-linecap="round" opacity="0"/>

&#x20;           <path class="anim-path" style="--len:400"

&#x20;             d="M 8,140 L 392,140"

&#x20;             fill="none" stroke="var(--base-weft)" stroke-width="5" stroke-linecap="round" opacity="0"/>

&#x20;           <text x="200" y="175" text-anchor="middle" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">plain weft rows form the base fabric</text>

&#x20;         </g>



&#x20;         <!-- Step 1: shed opening -->

&#x20;         <g id="t1" style="opacity:0">

&#x20;           <!-- base weft bands (faded) -->

&#x20;           <rect x="8" y="95"  width="384" height="10" rx="2" fill="var(--base-weft)" opacity=".3"/>

&#x20;           <rect x="8" y="115" width="384" height="10" rx="2" fill="var(--base-weft)" opacity=".3"/>

&#x20;           <rect x="8" y="135" width="384" height="10" rx="2" fill="var(--base-weft)" opacity=".3"/>

&#x20;           <!-- shed gap indicator between two weft rows -->

&#x20;           <rect x="8" y="109" width="384" height="8" rx="1" fill="var(--bg)" stroke="var(--line2)" stroke-width=".6" stroke-dasharray="4 3"/>

&#x20;           <!-- shed arrow -->

&#x20;           <path class="anim-path" style="--len:60"

&#x20;             d="M 200,88 L 200,106"

&#x20;             fill="none" stroke="var(--ink)" stroke-width="2.5" stroke-linecap="round" marker-end="url(#arT)"/>

&#x20;           <!-- label -->

&#x20;           <rect x="215" y="78" width="140" height="22" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>

&#x20;           <text x="285" y="92" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".06em">SHED OPENS</text>

&#x20;           <text x="285" y="104" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7.5" font-weight="300" fill="var(--ink3)">gap between weft rows</text>

&#x20;           <text x="200" y="175" text-anchor="middle" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">the cicim needle passes through this opening</text>

&#x20;         </g>



&#x20;         <!-- Step 2: embroidery thread passes through shed -->

&#x20;         <g id="t2" style="opacity:0">

&#x20;           <!-- base rows -->

&#x20;           <rect x="8" y="95"  width="384" height="10" rx="2" fill="var(--base-weft)" opacity=".3"/>

&#x20;           <rect x="8" y="135" width="384" height="10" rx="2" fill="var(--base-weft)" opacity=".3"/>

&#x20;           <!-- embroidery thread through shed — bold, contrasting -->

&#x20;           <path class="anim-path" style="--len:420"

&#x20;             d="M 8,113 L 392,113"

&#x20;             fill="none" stroke="var(--mot-a)" stroke-width="5" stroke-linecap="round"/>

&#x20;           <!-- needle shape at start -->

&#x20;           <ellipse cx="18" cy="113" rx="10" ry="4" fill="var(--bg2)" stroke="var(--line2)" stroke-width=".8"/>

&#x20;           <circle cx="12" cy="113" r="2" fill="var(--line2)"/>

&#x20;           <!-- label -->

&#x20;           <rect x="100" y="126" width="200" height="22" rx="2" fill="var(--bg)" stroke="var(--mot-a)" stroke-width=".7"/>

&#x20;           <text x="200" y="140" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--mot-a)" letter-spacing=".06em">EMBROIDERY THREAD</text>

&#x20;           <text x="200" y="175" text-anchor="middle" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">supplementary weft — sits on top of base fabric</text>

&#x20;         </g>



&#x20;         <!-- Step 3: pattern row — thread skips warps to create motif -->

&#x20;         <g id="t3" style="opacity:0">

&#x20;           <!-- base rows -->

&#x20;           <rect x="8" y="75"  width="384" height="8" rx="2" fill="var(--base-weft)" opacity=".25"/>

&#x20;           <rect x="8" y="115" width="384" height="8" rx="2" fill="var(--base-weft)" opacity=".25"/>

&#x20;           <rect x="8" y="135" width="384" height="8" rx="2" fill="var(--base-weft)" opacity=".25"/>

&#x20;           <!-- embroidery thread skipping warps for motif shape -->

&#x20;           <!-- segment 1: over 3 warps (float) -->

&#x20;           <path class="anim-path" style="--len:500"

&#x20;             d="M 8,95

&#x20;                L 36,95

&#x20;                L 86,95 L 136,95

&#x20;                L 136,85 L 186,85 L 186,95

&#x20;                L 236,95 L 286,95

&#x20;                L 286,85 L 336,85 L 336,95

&#x20;                L 392,95"

&#x20;             fill="none" stroke="var(--mot-b)" stroke-width="5" stroke-linecap="round" stroke-linejoin="round"/>

&#x20;           <!-- float indicator brackets -->

&#x20;           <rect x="136" y="82" width="50" height="3" rx="1.5" fill="var(--mot-b)" opacity=".35"/>

&#x20;           <rect x="286" y="82" width="50" height="3" rx="1.5" fill="var(--mot-b)" opacity=".35"/>

&#x20;           <line x1="136" y1="82" x2="136" y2="88" stroke="var(--mot-b)" stroke-width=".8" opacity=".6"/>

&#x20;           <line x1="186" y1="82" x2="186" y2="88" stroke="var(--mot-b)" stroke-width=".8" opacity=".6"/>

&#x20;           <line x1="286" y1="82" x2="286" y2="88" stroke="var(--mot-b)" stroke-width=".8" opacity=".6"/>

&#x20;           <line x1="336" y1="82" x2="336" y2="88" stroke="var(--mot-b)" stroke-width=".8" opacity=".6"/>

&#x20;           <!-- float label -->

&#x20;           <text x="161" y="78" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7.5" font-weight="500" fill="var(--mot-b)" letter-spacing=".06em">FLOAT</text>

&#x20;           <text x="200" y="175" text-anchor="middle" font-family="Outfit,sans-serif" font-size="9" font-weight="300" fill="var(--ink3)">floats over selected warps to create motif shapes</text>

&#x20;         </g>



&#x20;         <!-- Step 4: complete — base + embroidery together -->

&#x20;         <g id="t4" style="opacity:0">

&#x20;           <!-- full base fabric -->

&#x20;           <rect x="8" y="60"  width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;           <rect x="8" y="72"  width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".45"/>

&#x20;           <rect x="8" y="84"  width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;           <rect x="8" y="96"  width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".45"/>

&#x20;           <rect x="8" y="108" width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;           <rect x="8" y="120" width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".45"/>

&#x20;           <rect x="8" y="132" width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;           <rect x="8" y="144" width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".45"/>

&#x20;           <rect x="8" y="156" width="384" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;           <!-- embroidery motif rows — diamond shape using floats -->

&#x20;           <!-- row 1: 1 float centre -->

&#x20;           <rect x="183" y="64" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <!-- row 2: wider -->

&#x20;           <rect x="133" y="76" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="183" y="76" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="233" y="76" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <!-- row 3: widest -->

&#x20;           <rect x="83"  y="88" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="133" y="88" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="183" y="88" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="233" y="88" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="283" y="88" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <!-- row 4: mirror of 2 -->

&#x20;           <rect x="133" y="100" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="183" y="100" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <rect x="233" y="100" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <!-- row 5: mirror of 1 -->

&#x20;           <rect x="183" y="112" width="34" height="9" rx="1.5" fill="var(--mot-a)" opacity=".9"/>

&#x20;           <!-- warp overlays -->

&#x20;           <rect x="36"  y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="86"  y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="136" y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="186" y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="236" y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="286" y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <rect x="336" y="58" width="8" height="110" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;           <!-- badge -->

&#x20;           <rect x="92" y="183" width="216" height="20" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>

&#x20;           <text x="200" y="196" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".08em">DIAMOND MOTIF — floats on base weave</text>

&#x20;         </g>

&#x20;       </svg>

&#x20;     </div>



&#x20;     <div class="step-desc" id="desc-tech-box"><span id="desc-tech"></span></div>

&#x20;     <div class="nav-row">

&#x20;       <button class="nav-btn" id="prev-tech" onclick="prevTech()" disabled>← Prev</button>

&#x20;       <div class="progress-bar"><div class="progress-fill" id="fill-tech" style="width:20%"></div></div>

&#x20;       <span class="step-counter" id="ctr-tech">1 / 5</span>

&#x20;       <button class="nav-btn" id="next-tech" onclick="nextTech()">Next →</button>

&#x20;     </div>

&#x20;   </div>



&#x20;   <!-- ── PANEL: Motifs ── -->

&#x20;   <div class="panel" id="panel-motifs">

&#x20;     <p style="font-size:.82rem;color:var(--ink3);margin-bottom:.9rem;line-height:1.6">

&#x20;       Select a motif to read its symbolic meaning in Anatolian tradition.

&#x20;     </p>



&#x20;     <div class="motif-grid" id="motif-grid">

&#x20;       <!-- cards injected by JS -->

&#x20;     </div>



&#x20;     <div class="motif-detail" id="motif-detail">

&#x20;       <div class="mot-name" id="motif-name"></div>

&#x20;       <span id="motif-text">Click any motif above to learn its symbolic meaning.</span>

&#x20;     </div>

&#x20;   </div>



&#x20; </div><!-- /.diagram-panel -->



&#x20; <!-- ──── RIGHT: Content ──── -->

&#x20; <div class="content-panel">



&#x20;   <div class="section-label">Origins</div>

&#x20;   <h2>A flatweave <em>painted</em> with thread</h2>

&#x20;   <p>

&#x20;     Cicim (pronounced <em>jih-jeem</em>) is an Anatolian flatweave in which a <strong>supplementary

&#x20;     embroidery thread</strong> is passed through the shed of a completed or partially completed

&#x20;     plain-weave base fabric. Unlike sumak or kilim, where pattern and structure are inseparable,

&#x20;     cicim separates them: the base weave provides the structure; the cicim thread provides the decoration.

&#x20;   </p>

&#x20;   <p>

&#x20;     The cicim thread <strong>floats over selected warp threads</strong> to create geometric motifs —

&#x20;     diamonds, stars, hooks, ram's horns — that sit visibly on the surface. Between float rows,

&#x20;     the thread dips back through the shed, remaining invisible on the back face.

&#x20;   </p>



&#x20;   <div class="fact-strip">

&#x20;     <div class="fact-card">

&#x20;       <div class="fv">2-layer</div>

&#x20;       <div class="fl">base weave + supplementary embroidery</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fv">float</div>

&#x20;       <div class="fl">the defining structural element</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fv">100+</div>

&#x20;       <div class="fl">documented Anatolian motif types</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fv">visible</div>

&#x20;       <div class="fl">embroidery on front only — hidden reverse</div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <div class="section-label">Distinction</div>

&#x20;   <h2>Cicim vs. <em>Zili</em></h2>

&#x20;   <p>Cicim is often confused with its close relative zili. Both use supplementary weft on a plain-weave base, but they differ in how the float is structured.</p>



&#x20;   <div class="distinction-box">

&#x20;     <div class="dist-col">

&#x20;       <div class="dist-head">Cicim</div>

&#x20;       <div class="dist-item">Short floats — typically 2–4 warps</div>

&#x20;       <div class="dist-item">Irregular float lengths create fine detail</div>

&#x20;       <div class="dist-item">Thread passes through shed between motifs</div>

&#x20;       <div class="dist-item">Embroidery appears raised on surface</div>

&#x20;       <div class="dist-item">Central Anatolia — Konya, Afyon</div>

&#x20;     </div>

&#x20;     <div class="dist-col">

&#x20;       <div class="dist-head" style="color:var(--ink3)">Zili</div>

&#x20;       <div class="dist-item">Longer floats — often 4–8 warps</div>

&#x20;       <div class="dist-item">Regular repeat pattern, bolder coverage</div>

&#x20;       <div class="dist-item">Float rows often cover full width</div>

&#x20;       <div class="dist-item">Flatter surface, closer to kilim appearance</div>

&#x20;       <div class="dist-item">Eastern Anatolia — Erzurum, Kars</div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <div class="section-label">Comparison</div>

&#x20;   <h2>Cicim vs. <em>other techniques</em></h2>

&#x20;   <div class="table-scroll">

&#x20;     <table class="compare-table">

&#x20;       <thead>

&#x20;         <tr><th>Property</th><th>Cicim</th><th>Kilim</th><th>Sumak</th></tr>

&#x20;       </thead>

&#x20;       <tbody>

&#x20;         <tr class="hi"><td>Structure</td><td>Base weave + float</td><td>Interlaced weft only</td><td>Wrapped weft</td></tr>

&#x20;         <tr><td>Pattern method</td><td>Supplementary thread floats</td><td>Colour changes in weft</td><td>Wrap direction \&amp; colour</td></tr>

&#x20;         <tr class="hi"><td>Reversible</td><td>No — floats visible front only</td><td>Yes — always</td><td>Double sumak only</td></tr>

&#x20;         <tr><td>Texture</td><td>Raised embroidery on flat base</td><td>Completely flat</td><td>Diagonal ridges</td></tr>

&#x20;         <tr class="hi"><td>Motif freedom</td><td>High — float length varies</td><td>Limited by slit geometry</td><td>Limited by wrap angle</td></tr>

&#x20;         <tr><td>Production speed</td><td>Slow — two-layer process</td><td>Fast</td><td>Medium</td></tr>

&#x20;       </tbody>

&#x20;     </table>

&#x20;   </div>



&#x20;   <div class="pull-quote">

&#x20;     <p>The cicim needle does not weave — it embroiders. The loom provides the canvas; the weaver provides the story.</p>

&#x20;     <cite>— Principle of Anatolian cicim tradition</cite>

&#x20;   </div>



&#x20;   <div class="section-label">Uses</div>

&#x20;   <h2>Where cicim <em>is found</em></h2>

&#x20;   <ul class="uses-list">

&#x20;     <li><strong>Prayer rugs (seccade)</strong> — cicim mihrab niches surrounded by motif borders</li>

&#x20;     <li><strong>Pillow covers (yastık)</strong> — small cicim panels as decorative cushion faces</li>

&#x20;     <li><strong>Saddlebags (heybe)</strong> — cicim-decorated bags for nomadic transport</li>

&#x20;     <li><strong>Storage bags (çuval)</strong> — large sacks with cicim pattern panels</li>

&#x20;     <li><strong>Floor coverings</strong> — runner and room-size cicim flatweave rugs</li>

&#x20;     <li><strong>Wall textiles</strong> — hung as decorative panels in Anatolian homes</li>

&#x20;   </ul>



&#x20; </div><!-- /.content-panel -->



&#x20; <!-- ──── ANATOMY ──── -->

&#x20; <div class="anatomy-section">

&#x20;   <div class="section-label" style="justify-content:center;max-width:280px;margin:0 auto 1rem">Structure</div>

&#x20;   <h2>Cross-section of a cicim row — <em>labelled</em></h2>



&#x20;   <div class="anatomy-wrap">

&#x20;     <!-- Desktop -->

&#x20;     <svg class="anat-desktop" viewBox="0 0 900 240" width="100%" xmlns="http://www.w3.org/2000/svg">

&#x20;       <defs>

&#x20;         <pattern id="bgAN" width="20" height="20" patternUnits="userSpaceOnUse">

&#x20;           <circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/>

&#x20;         </pattern>

&#x20;       </defs>

&#x20;       <rect width="900" height="240" fill="url(#bgAN)"/>



&#x20;       <!-- Warps -->

&#x20;       <rect x="170" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="240" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="310" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="380" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="450" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="520" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>

&#x20;       <rect x="590" y="10" width="10" height="215" rx="5" fill="var(--warp-lt)"/>



&#x20;       <!-- Base weft rows (grey) -->

&#x20;       <rect x="100" y="55"  width="640" height="11" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="100" y="80"  width="640" height="11" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="100" y="105" width="640" height="11" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="100" y="130" width="640" height="11" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="100" y="155" width="640" height="11" rx="2" fill="var(--base-weft)" opacity=".5"/>



&#x20;       <!-- Embroidery thread row — floats over selected warps -->

&#x20;       <!-- passes through shed at start -->

&#x20;       <rect x="100" y="68" width="72" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <!-- float over 3 warps -->

&#x20;       <rect x="240" y="68" width="150" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <!-- through shed again -->

&#x20;       <rect x="380" y="68" width="72" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <!-- float over 3 warps -->

&#x20;       <rect x="520" y="68" width="150" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <!-- through shed to end -->

&#x20;       <rect x="668" y="68" width="72" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>



&#x20;       <!-- warp overlays on fabric area -->

&#x20;       <rect x="170" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="240" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="310" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="380" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="450" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="520" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="590" y="53" width="10" height="115" rx="4" fill="var(--warp-lt)" opacity=".2"/>



&#x20;       <!-- Labels -->

&#x20;       <!-- Warp -->

&#x20;       <line x1="175" y1="10" x2="90"  y2="8"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="175" cy="10" r="2" fill="var(--ink3)"/>

&#x20;       <text x="87"  y="7"  text-anchor="end" font-family="Outfit,sans-serif" font-size="9" font-weight="400" fill="var(--ink3)" letter-spacing=".06em">Warp</text>



&#x20;       <!-- Base weft -->

&#x20;       <line x1="740" y1="60"  x2="800" y2="55"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="740" cy="60" r="2" fill="var(--ink3)"/>

&#x20;       <text x="804" y="52"  text-anchor="start" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Base weft row</text>

&#x20;       <text x="804" y="65"  text-anchor="start" font-family="Outfit,sans-serif" font-size="9"   font-weight="300" fill="var(--ink3)">plain weave foundation</text>



&#x20;       <!-- Float -->

&#x20;       <line x1="390" y1="68"  x2="390" y2="44"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="390" cy="68" r="2" fill="var(--ink3)"/>

&#x20;       <text x="290" y="40"  text-anchor="middle" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Embroidery float</text>

&#x20;       <text x="290" y="52"  text-anchor="middle" font-family="Outfit,sans-serif" font-size="9"   font-weight="300" fill="var(--ink3)">sits on top of base weave</text>



&#x20;       <!-- Through shed -->

&#x20;       <line x1="245" y1="68"  x2="170" y2="45"  stroke="var(--line2)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="245" cy="68" r="2" fill="var(--ink3)"/>

&#x20;       <text x="85"  y="42"  text-anchor="end" font-family="Outfit,sans-serif" font-size="9.5" font-weight="300" fill="var(--ink)">Through shed</text>

&#x20;       <text x="85"  y="55"  text-anchor="end" font-family="Outfit,sans-serif" font-size="9"   font-weight="300" fill="var(--ink3)">hidden on back face</text>



&#x20;       <!-- Summary badge -->

&#x20;       <rect x="280" y="190" width="340" height="18" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".8"/>

&#x20;       <text x="450" y="202" text-anchor="middle" font-family="Outfit,sans-serif" font-size="8" font-weight="500" fill="var(--ink)" letter-spacing=".08em">FLOAT ON SURFACE · HIDDEN IN SHED BETWEEN MOTIFS</text>

&#x20;     </svg>



&#x20;     <!-- Mobile SVG -->

&#x20;     <svg class="anat-mobile" viewBox="0 0 300 240" width="100%" style="display:none" xmlns="http://www.w3.org/2000/svg">

&#x20;       <defs><pattern id="bgANm" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="1" cy="1" r=".5" fill="var(--line)" opacity=".4"/></pattern></defs>

&#x20;       <rect width="300" height="240" fill="url(#bgANm)"/>

&#x20;       <!-- Warps -->

&#x20;       <rect x="38"  y="10" width="8" height="215" rx="4" fill="var(--warp-lt)"/>

&#x20;       <rect x="88"  y="10" width="8" height="215" rx="4" fill="var(--warp-lt)"/>

&#x20;       <rect x="138" y="10" width="8" height="215" rx="4" fill="var(--warp-lt)"/>

&#x20;       <rect x="188" y="10" width="8" height="215" rx="4" fill="var(--warp-lt)"/>

&#x20;       <rect x="238" y="10" width="8" height="215" rx="4" fill="var(--warp-lt)"/>

&#x20;       <!-- Base weft rows -->

&#x20;       <rect x="8" y="55"  width="284" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="8" y="78"  width="284" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="8" y="101" width="284" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <rect x="8" y="124" width="284" height="9" rx="2" fill="var(--base-weft)" opacity=".5"/>

&#x20;       <!-- Embroidery float row -->

&#x20;       <rect x="8"   y="65" width="32" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <rect x="88"  y="65" width="102" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <rect x="238" y="65" width="54" height="9" rx="2" fill="var(--mot-a)" opacity=".9"/>

&#x20;       <!-- warp overlays -->

&#x20;       <rect x="38"  y="53" width="8" height="83" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="88"  y="53" width="8" height="83" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="138" y="53" width="8" height="83" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="188" y="53" width="8" height="83" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <rect x="238" y="53" width="8" height="83" rx="3" fill="var(--warp-lt)" opacity=".2"/>

&#x20;       <!-- labels -->

&#x20;       <rect x="10" y="148" width="105" height="16" rx="2" fill="var(--bg)" stroke="var(--line2)" stroke-width=".7"/>

&#x20;       <text x="62" y="159" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="400" fill="var(--ink3)" letter-spacing=".05em">BASE WEFT</text>

&#x20;       <rect x="168" y="148" width="115" height="16" rx="2" fill="var(--bg)" stroke="var(--mot-a)" stroke-width=".7"/>

&#x20;       <text x="226" y="159" text-anchor="middle" font-family="Outfit,sans-serif" font-size="7" font-weight="500" fill="var(--mot-a)" letter-spacing=".05em">EMB. FLOAT</text>

&#x20;     </svg>



&#x20;     <!-- Mobile labels -->

&#x20;     <ul class="anatomy-labels anat-labels" style="display:none">

&#x20;       <li><span class="alabel">Warp</span> Vertical structural threads under loom tension — the same as in kilim or sumak.</li>

&#x20;       <li><span class="alabel">Base weft</span> Plain-weave horizontal rows that form the foundation fabric — typically a single neutral colour.</li>

&#x20;       <li><span class="alabel">Embroidery float</span> The cicim thread passes over several warps without interlacing — this visible "float" creates the motif shape on the surface.</li>

&#x20;       <li><span class="alabel">Through shed</span> Between float segments, the cicim thread dips back through the gap (shed) between weft rows — invisible on the reverse face.</li>

&#x20;     </ul>

&#x20;   </div>

&#x20; </div>



</main>



<footer>Cicim · Anatolian Embroidered Flatweave Education</footer>



<!-- ═══ SCRIPTS ═══ -->

<script>

/\* ── Technique steps ── \*/

const TECH\_STEPS = \[

&#x20; `The cicim process begins by weaving a complete <strong>plain-weave base fabric</strong>. Horizontal weft threads pass over and under alternating warp threads, row by row, building a sturdy, flat foundation. This base is usually a single neutral colour.`,

&#x20; `Between any two adjacent weft rows, a narrow <strong>shed</strong> — a gap — can be opened. This is the channel through which the cicim embroidery needle will travel. The shed is the structural gateway that makes cicim possible without disrupting the base fabric.`,

&#x20; `A separate, often brightly coloured <strong>embroidery thread</strong> is threaded onto a flat needle and passed horizontally through the shed. At this stage it travels the full width invisibly — the pattern comes in the next step when it is selectively raised.`,

&#x20; `The embroidery thread is pulled upward over <strong>selected warp threads</strong>, creating "floats" that sit visibly on the surface. The length and position of each float is chosen by the weaver to build the motif — a diamond, star, or ram's horn — row by row.`,

&#x20; `As rows accumulate, the <strong>complete motif emerges</strong> from the interplay of floats. The base weave remains visible in the gaps between floats; the embroidery thread dips back through the shed wherever no float is needed. Front face shows the motif; reverse shows only the base weave.`

];



let techCur = 0;

const TECH\_MAX = 4;



function goToTech(n) {

&#x20; techCur = n;

&#x20; const svg = document.getElementById('tech-svg');

&#x20; \[0,1,2,3,4].forEach(i => {

&#x20;   const el = svg.querySelector(`#t${i}`);

&#x20;   if (el) { el.style.transition = 'opacity .3s'; el.style.opacity = i === n ? '1' : '0'; }

&#x20; });

&#x20; const cur = svg.querySelector(`#t${n}`);

&#x20; if (cur) {

&#x20;   cur.querySelectorAll('.anim-path').forEach(p => {

&#x20;     const m = p.style.cssText.match(/--len:\\s\*(\[\\d.]+)/);

&#x20;     const len = m ? parseFloat(m\[1]) : 400;

&#x20;     p.style.animation = 'none'; void p.offsetWidth;

&#x20;     p.style.strokeDasharray = len; p.style.strokeDashoffset = len;

&#x20;     // restore opacity=0 elements

&#x20;     if (p.getAttribute('opacity') === '0') p.style.opacity = '0';

&#x20;     setTimeout(() => {

&#x20;       p.style.animation = 'drawPath .9s cubic-bezier(.4,0,.2,1) forwards';

&#x20;       p.style.strokeDashoffset = 0;

&#x20;       // delayed second path for step 0

&#x20;       if (n === 0) {

&#x20;         const paths = cur.querySelectorAll('.anim-path');

&#x20;         paths.forEach((pp, i) => {

&#x20;           if (i > 0) {

&#x20;             pp.style.opacity = '0';

&#x20;             setTimeout(() => {

&#x20;               pp.style.opacity = '1';

&#x20;               pp.style.animation = 'none'; void pp.offsetWidth;

&#x20;               pp.style.strokeDasharray = 400; pp.style.strokeDashoffset = 400;

&#x20;               pp.style.animation = `drawPath .8s ${i \* .3}s cubic-bezier(.4,0,.2,1) forwards`;

&#x20;               pp.style.strokeDashoffset = 0;

&#x20;             }, 400 + i \* 300);

&#x20;           }

&#x20;         });

&#x20;       }

&#x20;     }, 30);

&#x20;   });

&#x20; }

&#x20; // pills

&#x20; document.querySelectorAll('#pills-tech .step-pill').forEach((b, i) => {

&#x20;   b.className = 'step-pill' + (i === n ? ' sp-active' : '');

&#x20; });

&#x20; document.getElementById('fill-tech').style.width = `${(n + 1) \* 20}%`;

&#x20; document.getElementById('ctr-tech').textContent  = `${n + 1} / 5`;

&#x20; document.getElementById('prev-tech').disabled = n === 0;

&#x20; document.getElementById('next-tech').disabled = n === TECH\_MAX;

&#x20; const box = document.getElementById('desc-tech-box');

&#x20; box.style.animation = 'none'; void box.offsetWidth;

&#x20; box.style.animation = 'fadeUp .38s ease forwards';

&#x20; document.getElementById('desc-tech').innerHTML = TECH\_STEPS\[n];

}

function nextTech() { if (techCur < TECH\_MAX) goToTech(techCur + 1); }

function prevTech() { if (techCur > 0)        goToTech(techCur - 1); }



/\* ── Motifs ── \*/

const MOTIFS = \[

&#x20; {

&#x20;   id: 'diamond', label: 'Diamond', color: '#2c4a6e',

&#x20;   name: 'The Diamond (Elibelinde / Muska)',

&#x20;   desc: `The diamond is the most common cicim motif. It represents <strong>protection</strong> — diamond shapes were historically sewn into clothing as amulets (muska). In cicim, a diamond border around a prayer niche is thought to shield the worshipper during prayer. It also symbolises <strong>femininity and fertility</strong> in many Anatolian tribal traditions.`

&#x20; },

&#x20; {

&#x20;   id: 'ramhorn', label: 'Ram\\'s Horn', color: '#6e2c2c',

&#x20;   name: 'Ram\\'s Horn (Koçboynuzu)',

&#x20;   desc: `The ram's horn (koçboynuzu) is a bold S-curve or spiral motif found across Anatolian, Caucasian, and Turkmen weaving. It symbolises <strong>strength, heroism, and male power</strong>. In tribal contexts it also represented <strong>wealth</strong>, as flocks of sheep were the primary measure of prosperity. Two opposing horns side by side represent a <strong>pair, marriage, or union</strong>.`

&#x20; },

&#x20; {

&#x20;   id: 'star', label: 'Star / Sun', color: '#2c6e4a',

&#x20;   name: 'Star and Sun (Yıldız)',

&#x20;   desc: `Eight-pointed stars and sun discs are ancient Anatolian symbols of <strong>divine light and cosmic order</strong>. In cicim they appear as central medallions or border repeats. The eight points correspond to the eight directions of the universe in pre-Islamic Anatolian cosmology. They are also read as <strong>good fortune and guidance</strong> — a star to navigate by in an uncertain world.`

&#x20; },

&#x20; {

&#x20;   id: 'hook', label: 'Running Hook', color: '#6e5a2c',

&#x20;   name: 'Running Hook (S-Hook / Çengel)',

&#x20;   desc: `The running hook or S-hook is one of the oldest motifs in Anatolian textile tradition, appearing on textiles as early as the Bronze Age. It is believed to represent <strong>protection against the evil eye</strong>. Chains of hooks along a border act as a continuous apotropaic barrier. In some regions the hook is also read as a <strong>snake</strong> — another protective symbol — or as the <strong>letter S for "saglik" (health)</strong>.`

&#x20; },

&#x20; {

&#x20;   id: 'hands', label: 'Hands on Hips', color: '#4a2c6e',

&#x20;   name: 'Hands on Hips (Elibelinde)',

&#x20;   desc: `The elibelinde — literally "hands on hips" — is a stylised human figure with arms raised or akimbo. It is one of the oldest and most distinctly <strong>female</strong> symbols in Anatolian weaving, associated with the <strong>mother goddess</strong> and feminine creative power. It appears frequently in cicim as a central field motif and is thought to bring <strong>fertility and prosperity</strong> to the household.`

&#x20; },

&#x20; {

&#x20;   id: 'comb', label: 'Comb', color: '#3a6a6a',

&#x20;   name: 'Comb (Tarak)',

&#x20;   desc: `The comb motif represents <strong>cleanliness, order, and preparation for marriage</strong>. In Anatolian custom, a bride's trousseau items were often decorated with comb motifs — including the very flatweaves woven as part of the dowry. The comb's teeth are a <strong>symbol of readiness</strong>: teeth aligned, all things in order, a life prepared. It also appears as a <strong>tree of life</strong> variant in some regional traditions.`

&#x20; }

];



function drawMotifSVG(motif) {

&#x20; const c = motif.color;

&#x20; const w = 100, h = 100;

&#x20; let shapes = '';



&#x20; if (motif.id === 'diamond') {

&#x20;   shapes = `<polygon points="50,15 85,50 50,85 15,50" fill="${c}" opacity=".85"/>

&#x20;             <polygon points="50,28 72,50 50,72 28,50" fill="var(--bg2)" opacity=".9"/>

&#x20;             <polygon points="50,38 62,50 50,62 38,50" fill="${c}" opacity=".7"/>`;

&#x20; } else if (motif.id === 'ramhorn') {

&#x20;   shapes = `<path d="M 30,70 Q 20,50 35,35 Q 50,20 65,35 Q 75,45 65,55 Q 55,62 45,55 Q 38,48 45,40 Q 52,33 58,38" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>

&#x20;             <path d="M 70,30 Q 80,50 65,65 Q 50,80 35,65 Q 25,55 35,45 Q 45,38 55,45 Q 62,52 55,60 Q 48,67 42,62" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>`;

&#x20; } else if (motif.id === 'star') {

&#x20;   shapes = `<polygon points="50,12 56,38 80,25 67,48 93,50 67,52 80,75 56,62 50,88 44,62 20,75 33,52 7,50 33,48 20,25 44,38" fill="${c}" opacity=".85"/>

&#x20;             <circle cx="50" cy="50" r="10" fill="var(--bg2)" opacity=".9"/>`;

&#x20; } else if (motif.id === 'hook') {

&#x20;   shapes = `<path d="M 20,30 Q 20,20 30,20 Q 40,20 40,30 Q 40,42 28,48 Q 16,54 16,65 Q 16,78 28,78 Q 40,78 44,68" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>

&#x20;             <path d="M 80,70 Q 80,80 70,80 Q 60,80 60,70 Q 60,58 72,52 Q 84,46 84,35 Q 84,22 72,22 Q 60,22 56,32" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>`;

&#x20; } else if (motif.id === 'hands') {

&#x20;   shapes = `<ellipse cx="50" cy="28" rx="10" ry="12" fill="${c}" opacity=".85"/>

&#x20;             <rect x="40" y="38" width="20" height="30" rx="4" fill="${c}" opacity=".85"/>

&#x20;             <path d="M 40,48 Q 25,42 20,52 Q 18,62 28,64" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>

&#x20;             <path d="M 60,48 Q 75,42 80,52 Q 82,62 72,64" fill="none" stroke="${c}" stroke-width="5" stroke-linecap="round"/>

&#x20;             <rect x="43" y="68" width="6" height="18" rx="3" fill="${c}" opacity=".85"/>

&#x20;             <rect x="51" y="68" width="6" height="18" rx="3" fill="${c}" opacity=".85"/>`;

&#x20; } else if (motif.id === 'comb') {

&#x20;   shapes = `<rect x="20" y="65" width="60" height="10" rx="3" fill="${c}" opacity=".85"/>

&#x20;             <rect x="26" y="28" width="7" height="38" rx="3" fill="${c}" opacity=".85"/>

&#x20;             <rect x="38" y="20" width="7" height="46" rx="3" fill="${c}" opacity=".85"/>

&#x20;             <rect x="50" y="24" width="7" height="42" rx="3" fill="${c}" opacity=".85"/>

&#x20;             <rect x="62" y="28" width="7" height="38" rx="3" fill="${c}" opacity=".85"/>`;

&#x20; }



&#x20; return `<svg viewBox="0 0 100 100" width="100%" class="motif-svg" xmlns="http://www.w3.org/2000/svg">

&#x20;   <rect width="100" height="100" fill="var(--bg2)"/>

&#x20;   <rect width="100" height="100" fill="url(#bgT)" opacity=".5"/>

&#x20;   ${shapes}

&#x20; </svg>`;

}



function buildMotifGrid() {

&#x20; const grid = document.getElementById('motif-grid');

&#x20; grid.innerHTML = MOTIFS.map((m, i) => `

&#x20;   <div class="motif-card" id="mc-${m.id}" onclick="selectMotif('${m.id}')">

&#x20;     ${drawMotifSVG(m)}

&#x20;     <div class="motif-label">${m.label}</div>

&#x20;   </div>

&#x20; `).join('');

}



function selectMotif(id) {

&#x20; const motif = MOTIFS.find(m => m.id === id);

&#x20; if (!motif) return;

&#x20; document.querySelectorAll('.motif-card').forEach(c => c.classList.remove('selected'));

&#x20; document.getElementById(`mc-${id}`).classList.add('selected');

&#x20; const detail = document.getElementById('motif-detail');

&#x20; detail.style.animation = 'none'; void detail.offsetWidth;

&#x20; detail.style.animation = 'fadeUp .35s ease forwards';

&#x20; detail.style.borderLeftColor = motif.color;

&#x20; document.getElementById('motif-name').textContent = motif.name;

&#x20; document.getElementById('motif-text').innerHTML = motif.desc;

}



function switchMain(panel) {

&#x20; document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));

&#x20; document.getElementById(`panel-${panel}`).classList.add('active');

&#x20; document.querySelectorAll('.main-tab').forEach((b, i) => {

&#x20;   b.classList.toggle('active', (i === 0 \&\& panel === 'technique') || (i === 1 \&\& panel === 'motifs'));

&#x20; });

}



/\* ── Anatomy mobile switch ── \*/

function updateAnatomy() {

&#x20; const mob = window.innerWidth <= 600;

&#x20; document.querySelectorAll('.anat-desktop').forEach(el => el.style.display = mob ? 'none' : 'block');

&#x20; document.querySelectorAll('.anat-mobile').forEach(el  => el.style.display = mob ? 'block' : 'none');

&#x20; document.querySelectorAll('.anat-labels').forEach(el  => el.style.display = mob ? 'block' : 'none');

}

updateAnatomy();

window.addEventListener('resize', updateAnatomy);



/\* ── Keyboard nav ── \*/

document.addEventListener('keydown', e => {

&#x20; if (document.getElementById('panel-technique').classList.contains('active')) {

&#x20;   if (e.key === 'ArrowRight') nextTech();

&#x20;   if (e.key === 'ArrowLeft')  prevTech();

&#x20; }

});



/\* ── Init ── \*/

buildMotifGrid();

goToTech(0);

</script>

</body>

</html>

