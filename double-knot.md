<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>The Turkish Knot — Anatolian Rug Weaving</title>

<link rel="preconnect" href="https://fonts.googleapis.com">

<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400\&family=Cinzel:wght@400;600\&family=DM+Sans:wght@300;400;500\&display=swap" rel="stylesheet">



<style>

&#x20; :root {

&#x20;   --cream:    #f5f0e8;

&#x20;   --parchment:#ede4d0;

&#x20;   --warm:     #c9b99a;

&#x20;   --terracotta:#b85c38;

&#x20;   --brick:    #8b3a22;

&#x20;   --gold:     #c8971a;

&#x20;   --gold-lt:  #e8c050;

&#x20;   --ink:      #2c1a0e;

&#x20;   --muted:    #7a6555;

&#x20;   --warp:     #c8aa7a;

&#x20;   --warp-dk:  #a07a45;

&#x20;   --yarn:     #b85c38;

&#x20;   --yarn-hl:  #e07a50;

&#x20; }



&#x20; \*, \*::before, \*::after { box-sizing: border-box; margin: 0; padding: 0; }



&#x20; html { scroll-behavior: smooth; }



&#x20; body {

&#x20;   background-color: var(--cream);

&#x20;   background-image:

&#x20;     radial-gradient(ellipse at 20% 10%, rgba(200,151,26,.12) 0%, transparent 50%),

&#x20;     radial-gradient(ellipse at 80% 90%, rgba(184,92,56,.10) 0%, transparent 50%),

&#x20;     url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23c9b99a' fill-opacity='0.08'%3E%3Cpath d='M40 0 L80 40 L40 80 L0 40Z'/%3E%3C/g%3E%3C/svg%3E");

&#x20;   color: var(--ink);

&#x20;   font-family: 'DM Sans', sans-serif;

&#x20;   font-weight: 300;

&#x20;   min-height: 100vh;

&#x20;   padding: 0;

&#x20;   overflow-x: hidden;

&#x20; }



&#x20; /\* ── HEADER ── \*/

&#x20; header {

&#x20;   text-align: center;

&#x20;   padding: 4rem 2rem 2.5rem;

&#x20;   position: relative;

&#x20;   border-bottom: 1px solid var(--warm);

&#x20; }

&#x20; .header-ornament {

&#x20;   display: flex;

&#x20;   align-items: center;

&#x20;   justify-content: center;

&#x20;   gap: 1rem;

&#x20;   margin-bottom: 1.2rem;

&#x20; }

&#x20; .header-ornament::before,

&#x20; .header-ornament::after {

&#x20;   content: '';

&#x20;   flex: 1;

&#x20;   max-width: 120px;

&#x20;   height: 1px;

&#x20;   background: linear-gradient(to right, transparent, var(--gold));

&#x20; }

&#x20; .header-ornament::after {

&#x20;   background: linear-gradient(to left, transparent, var(--gold));

&#x20; }

&#x20; .origin-tag {

&#x20;   font-family: 'Cinzel', serif;

&#x20;   font-size: 0.65rem;

&#x20;   letter-spacing: .25em;

&#x20;   color: var(--gold);

&#x20;   text-transform: uppercase;

&#x20; }

&#x20; h1 {

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: clamp(2.8rem, 7vw, 5rem);

&#x20;   font-weight: 300;

&#x20;   letter-spacing: .04em;

&#x20;   line-height: 1.05;

&#x20;   color: var(--ink);

&#x20;   margin-bottom: .6rem;

&#x20; }

&#x20; h1 em {

&#x20;   font-style: italic;

&#x20;   color: var(--brick);

&#x20; }

&#x20; .subtitle {

&#x20;   font-family: 'DM Sans', sans-serif;

&#x20;   font-size: .95rem;

&#x20;   font-weight: 300;

&#x20;   color: var(--muted);

&#x20;   letter-spacing: .08em;

&#x20;   margin-bottom: .3rem;

&#x20; }

&#x20; .aka {

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: 1rem;

&#x20;   font-style: italic;

&#x20;   color: var(--muted);

&#x20; }



&#x20; /\* ── MAIN LAYOUT ── \*/

&#x20; main {

&#x20;   max-width: 1100px;

&#x20;   margin: 0 auto;

&#x20;   padding: 3rem 2rem 5rem;

&#x20;   display: grid;

&#x20;   grid-template-columns: 1fr 1fr;

&#x20;   gap: 3rem 4rem;

&#x20;   align-items: start;

&#x20; }

&#x20; @media (max-width: 780px) {

&#x20;   main { grid-template-columns: 1fr; gap: 2rem; }

&#x20; }



&#x20; /\* ── LEFT: INTERACTIVE DIAGRAM ── \*/

&#x20; .diagram-panel {

&#x20;   position: sticky;

&#x20;   top: 2rem;

&#x20; }



&#x20; /\* Step indicator \*/

&#x20; .step-tabs {

&#x20;   display: flex;

&#x20;   border-bottom: 1px solid var(--warm);

&#x20;   margin-bottom: 1.5rem;

&#x20;   gap: 0;

&#x20; }

&#x20; .step-tab {

&#x20;   flex: 1;

&#x20;   background: none;

&#x20;   border: none;

&#x20;   padding: .65rem .5rem;

&#x20;   cursor: pointer;

&#x20;   font-family: 'Cinzel', serif;

&#x20;   font-size: .62rem;

&#x20;   letter-spacing: .12em;

&#x20;   color: var(--muted);

&#x20;   border-bottom: 2px solid transparent;

&#x20;   transition: all .25s;

&#x20;   text-align: center;

&#x20;   line-height: 1.3;

&#x20; }

&#x20; .step-tab:hover { color: var(--terracotta); }

&#x20; .step-tab.active {

&#x20;   color: var(--terracotta);

&#x20;   border-bottom-color: var(--terracotta);

&#x20; }

&#x20; .step-tab .tab-num {

&#x20;   display: block;

&#x20;   font-size: .55rem;

&#x20;   color: var(--gold);

&#x20;   margin-bottom: .15rem;

&#x20; }



&#x20; /\* SVG container \*/

&#x20; .svg-wrap {

&#x20;   background: var(--parchment);

&#x20;   border: 1px solid var(--warm);

&#x20;   border-radius: 4px;

&#x20;   overflow: hidden;

&#x20;   position: relative;

&#x20;   aspect-ratio: 4/3;

&#x20; }

&#x20; .svg-wrap svg { width: 100%; height: 100%; display: block; }



&#x20; /\* Description \*/

&#x20; .step-desc {

&#x20;   margin-top: 1.2rem;

&#x20;   padding: 1rem 1.25rem;

&#x20;   background: rgba(200,151,26,.07);

&#x20;   border-left: 3px solid var(--gold);

&#x20;   border-radius: 0 4px 4px 0;

&#x20;   font-size: .9rem;

&#x20;   line-height: 1.75;

&#x20;   color: var(--ink);

&#x20;   min-height: 5rem;

&#x20; }

&#x20; .step-desc strong { color: var(--brick); font-weight: 500; }



&#x20; /\* Nav buttons \*/

&#x20; .nav-row {

&#x20;   display: flex;

&#x20;   align-items: center;

&#x20;   justify-content: space-between;

&#x20;   margin-top: 1rem;

&#x20; }

&#x20; .nav-btn {

&#x20;   background: none;

&#x20;   border: 1px solid var(--warm);

&#x20;   border-radius: 2px;

&#x20;   padding: .5rem 1.2rem;

&#x20;   font-family: 'Cinzel', serif;

&#x20;   font-size: .65rem;

&#x20;   letter-spacing: .12em;

&#x20;   color: var(--muted);

&#x20;   cursor: pointer;

&#x20;   transition: all .2s;

&#x20; }

&#x20; .nav-btn:hover:not(:disabled) {

&#x20;   border-color: var(--terracotta);

&#x20;   color: var(--terracotta);

&#x20; }

&#x20; .nav-btn:disabled { opacity: .3; cursor: default; }



&#x20; .progress-dots {

&#x20;   display: flex;

&#x20;   gap: 8px;

&#x20; }

&#x20; .pdot {

&#x20;   width: 7px; height: 7px;

&#x20;   border-radius: 50%;

&#x20;   background: var(--warm);

&#x20;   transition: background .3s, transform .3s;

&#x20; }

&#x20; .pdot.active {

&#x20;   background: var(--terracotta);

&#x20;   transform: scale(1.3);

&#x20; }



&#x20; /\* ── RIGHT: CONTENT ── \*/

&#x20; .content-panel { padding-top: .5rem; }



&#x20; .section-label {

&#x20;   font-family: 'Cinzel', serif;

&#x20;   font-size: .6rem;

&#x20;   letter-spacing: .3em;

&#x20;   color: var(--gold);

&#x20;   text-transform: uppercase;

&#x20;   margin-bottom: .8rem;

&#x20;   display: flex;

&#x20;   align-items: center;

&#x20;   gap: .75rem;

&#x20; }

&#x20; .section-label::after {

&#x20;   content: '';

&#x20;   flex: 1;

&#x20;   height: 1px;

&#x20;   background: linear-gradient(to right, var(--warm), transparent);

&#x20; }



&#x20; h2 {

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: 2rem;

&#x20;   font-weight: 400;

&#x20;   line-height: 1.2;

&#x20;   margin-bottom: 1rem;

&#x20;   color: var(--ink);

&#x20; }

&#x20; h2 em { font-style: italic; color: var(--brick); }



&#x20; p {

&#x20;   font-size: .92rem;

&#x20;   line-height: 1.85;

&#x20;   color: var(--muted);

&#x20;   margin-bottom: 1.1rem;

&#x20; }



&#x20; /\* Fact strip \*/

&#x20; .fact-strip {

&#x20;   display: grid;

&#x20;   grid-template-columns: 1fr 1fr;

&#x20;   gap: .75rem;

&#x20;   margin: 1.5rem 0;

&#x20; }

&#x20; .fact-card {

&#x20;   background: var(--parchment);

&#x20;   border: 1px solid var(--warm);

&#x20;   border-radius: 4px;

&#x20;   padding: .9rem 1rem;

&#x20; }

&#x20; .fact-card .fact-val {

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: 1.6rem;

&#x20;   font-weight: 600;

&#x20;   color: var(--terracotta);

&#x20;   line-height: 1;

&#x20;   margin-bottom: .2rem;

&#x20; }

&#x20; .fact-card .fact-lbl {

&#x20;   font-size: .72rem;

&#x20;   letter-spacing: .06em;

&#x20;   color: var(--muted);

&#x20;   font-weight: 300;

&#x20; }



&#x20; /\* Comparison table \*/

&#x20; .compare-table {

&#x20;   width: 100%;

&#x20;   border-collapse: collapse;

&#x20;   font-size: .85rem;

&#x20;   margin: 1.5rem 0;

&#x20; }

&#x20; .compare-table thead tr {

&#x20;   border-bottom: 1.5px solid var(--gold);

&#x20; }

&#x20; .compare-table th {

&#x20;   font-family: 'Cinzel', serif;

&#x20;   font-size: .6rem;

&#x20;   letter-spacing: .15em;

&#x20;   color: var(--gold);

&#x20;   font-weight: 400;

&#x20;   padding: .5rem .75rem;

&#x20;   text-align: left;

&#x20; }

&#x20; .compare-table th:first-child { width: 40%; }

&#x20; .compare-table td {

&#x20;   padding: .6rem .75rem;

&#x20;   border-bottom: 1px solid rgba(201,185,154,.35);

&#x20;   color: var(--muted);

&#x20;   vertical-align: top;

&#x20;   line-height: 1.5;

&#x20; }

&#x20; .compare-table td:first-child {

&#x20;   color: var(--ink);

&#x20;   font-weight: 400;

&#x20; }

&#x20; .compare-table .highlight td { background: rgba(184,92,56,.06); }

&#x20; .compare-table .highlight td:first-child { color: var(--brick); }



&#x20; /\* Pull quote \*/

&#x20; .pull-quote {

&#x20;   margin: 2rem 0;

&#x20;   padding: 1.5rem 2rem;

&#x20;   border-top: 1px solid var(--warm);

&#x20;   border-bottom: 1px solid var(--warm);

&#x20;   position: relative;

&#x20; }

&#x20; .pull-quote::before {

&#x20;   content: '\\201C';

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: 5rem;

&#x20;   color: var(--gold);

&#x20;   opacity: .25;

&#x20;   position: absolute;

&#x20;   top: -.5rem; left: 1rem;

&#x20;   line-height: 1;

&#x20; }

&#x20; .pull-quote p {

&#x20;   font-family: 'Cormorant Garamond', serif;

&#x20;   font-size: 1.3rem;

&#x20;   font-style: italic;

&#x20;   line-height: 1.6;

&#x20;   color: var(--ink);

&#x20;   margin-bottom: .4rem;

&#x20; }

&#x20; .pull-quote cite {

&#x20;   font-size: .75rem;

&#x20;   letter-spacing: .1em;

&#x20;   color: var(--muted);

&#x20; }



&#x20; /\* Uses list \*/

&#x20; .uses-list {

&#x20;   list-style: none;

&#x20;   margin: .5rem 0 1.5rem;

&#x20; }

&#x20; .uses-list li {

&#x20;   display: flex;

&#x20;   align-items: baseline;

&#x20;   gap: .75rem;

&#x20;   font-size: .88rem;

&#x20;   color: var(--muted);

&#x20;   padding: .45rem 0;

&#x20;   border-bottom: 1px solid rgba(201,185,154,.3);

&#x20;   line-height: 1.5;

&#x20; }

&#x20; .uses-list li::before {

&#x20;   content: '◆';

&#x20;   font-size: .45rem;

&#x20;   color: var(--gold);

&#x20;   flex-shrink: 0;

&#x20;   transform: translateY(-1px);

&#x20; }

&#x20; .uses-list strong { color: var(--ink); font-weight: 400; }



&#x20; /\* Full-width anatomy diagram \*/

&#x20; .anatomy-section {

&#x20;   grid-column: 1 / -1;

&#x20;   padding-top: 2rem;

&#x20;   border-top: 1px solid var(--warm);

&#x20; }

&#x20; .anatomy-section h2 {

&#x20;   font-size: 1.6rem;

&#x20;   text-align: center;

&#x20;   margin-bottom: 2rem;

&#x20; }

&#x20; .anatomy-svg-wrap {

&#x20;   background: var(--parchment);

&#x20;   border: 1px solid var(--warm);

&#x20;   border-radius: 4px;

&#x20;   padding: 1rem;

&#x20; }



&#x20; /\* Footer \*/

&#x20; footer {

&#x20;   text-align: center;

&#x20;   padding: 2rem;

&#x20;   border-top: 1px solid var(--warm);

&#x20;   font-size: .75rem;

&#x20;   letter-spacing: .08em;

&#x20;   color: var(--muted);

&#x20; }

&#x20; footer span { color: var(--gold); }



&#x20; /\* Animations \*/

&#x20; @keyframes drawPath {

&#x20;   from { stroke-dashoffset: var(--len); }

&#x20;   to   { stroke-dashoffset: 0; }

&#x20; }

&#x20; @keyframes fadeUp {

&#x20;   from { opacity: 0; transform: translateY(8px); }

&#x20;   to   { opacity: 1; transform: translateY(0); }

&#x20; }

&#x20; .anim-path {

&#x20;   stroke-dasharray: var(--len);

&#x20;   stroke-dashoffset: var(--len);

&#x20; }

&#x20; .anim-path.run {

&#x20;   animation: drawPath .85s cubic-bezier(.4,0,.2,1) forwards;

&#x20; }

&#x20; .fade-up { animation: fadeUp .4s ease forwards; }



&#x20; /\* Responsive tweaks \*/

&#x20; @media (max-width: 500px) {

&#x20;   h1 { font-size: 2.4rem; }

&#x20;   .fact-strip { grid-template-columns: 1fr 1fr; }

&#x20;   .step-tab { font-size: .55rem; }

&#x20; }

</style>

</head>

<body>



<!-- ═══════════════ HEADER ═══════════════ -->

<header>

&#x20; <div class="header-ornament"><span class="origin-tag">Anatolia · Traditional Craft</span></div>

&#x20; <h1>The <em>Turkish</em> Knot</h1>

&#x20; <p class="subtitle">An Interactive Guide to Anatolian Rug Weaving</p>

&#x20; <p class="aka">Also known as the Symmetrical Knot · Ghiordes Knot</p>

</header>



<!-- ═══════════════ MAIN ═══════════════ -->

<main>



&#x20; <!-- ──── LEFT: Interactive Diagram ──── -->

&#x20; <div class="diagram-panel">



&#x20;   <div class="step-tabs">

&#x20;     <button class="step-tab active" onclick="goTo(0)">

&#x20;       <span class="tab-num">I</span>Setup

&#x20;     </button>

&#x20;     <button class="step-tab" onclick="goTo(1)">

&#x20;       <span class="tab-num">II</span>First Loop

&#x20;     </button>

&#x20;     <button class="step-tab" onclick="goTo(2)">

&#x20;       <span class="tab-num">III</span>Second Loop

&#x20;     </button>

&#x20;     <button class="step-tab" onclick="goTo(3)">

&#x20;       <span class="tab-num">IV</span>Complete

&#x20;     </button>

&#x20;   </div>



&#x20;   <div class="svg-wrap">

&#x20;     <svg id="knotsvg" viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">

&#x20;       <defs>

&#x20;         <marker id="ah" viewBox="0 0 10 10" refX="8" refY="5"

&#x20;                 markerWidth="5" markerHeight="5" orient="auto-start-reverse">

&#x20;           <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"

&#x20;                 stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>

&#x20;         </marker>

&#x20;         <!-- subtle linen texture pattern -->

&#x20;         <pattern id="linen" width="4" height="4" patternUnits="userSpaceOnUse">

&#x20;           <rect width="4" height="4" fill="none"/>

&#x20;           <line x1="0" y1="2" x2="4" y2="2" stroke="#c9b99a" stroke-width=".3" opacity=".4"/>

&#x20;           <line x1="2" y1="0" x2="2" y2="4" stroke="#c9b99a" stroke-width=".3" opacity=".3"/>

&#x20;         </pattern>

&#x20;       </defs>



&#x20;       <!-- background linen -->

&#x20;       <rect width="400" height="300" fill="url(#linen)"/>



&#x20;       <!-- WARP THREADS (always visible) -->

&#x20;       <!-- warp 1 shadow -->

&#x20;       <rect x="153" y="20" width="14" height="260" rx="7" fill="var(--warp-dk)" opacity=".25"/>

&#x20;       <!-- warp 1 -->

&#x20;       <rect x="150" y="20" width="14" height="260" rx="7" fill="var(--warp)"/>

&#x20;       <!-- warp 1 highlight -->

&#x20;       <rect x="152" y="20" width="4" height="260" rx="2" fill="rgba(255,255,255,.3)"/>



&#x20;       <!-- warp 2 shadow -->

&#x20;       <rect x="233" y="20" width="14" height="260" rx="7" fill="var(--warp-dk)" opacity=".25"/>

&#x20;       <!-- warp 2 -->

&#x20;       <rect x="230" y="20" width="14" height="260" rx="7" fill="var(--warp)"/>

&#x20;       <!-- warp 2 highlight -->

&#x20;       <rect x="232" y="20" width="4" height="260" rx="2" fill="rgba(255,255,255,.3)"/>



&#x20;       <!-- warp labels -->

&#x20;       <text x="157" y="295" text-anchor="middle" font-family="Cinzel,serif" font-size="8" fill="#a07a45" letter-spacing="1">W1</text>

&#x20;       <text x="237" y="295" text-anchor="middle" font-family="Cinzel,serif" font-size="8" fill="#a07a45" letter-spacing="1">W2</text>



&#x20;       <!-- ── STEP 0: approaching thread ── -->

&#x20;       <g id="s0">

&#x20;         <path class="anim-path" style="--len:120"

&#x20;               d="M 30,150 L 148,150"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"

&#x20;               marker-end="url(#ah)"/>

&#x20;         <text x="85" y="138" text-anchor="middle"

&#x20;               font-family="DM Sans,sans-serif" font-size="9.5" font-weight="300"

&#x20;               fill="var(--terracotta)" letter-spacing=".5">wool thread</text>

&#x20;       </g>



&#x20;       <!-- ── STEP 1: loop around warp 1 ── -->

&#x20;       <g id="s1" style="opacity:0">

&#x20;         <path class="anim-path" style="--len:350"

&#x20;               d="M 30,150 L 148,150

&#x20;                  Q 128,150 128,120

&#x20;                  Q 128,60 157,60

&#x20;                  Q 190,60 190,100

&#x20;                  L 190,280"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;         <!-- label -->

&#x20;         <rect x="42" y="65" width="80" height="34" rx="3"

&#x20;               fill="rgba(237,228,208,.88)"/>

&#x20;         <text x="82" y="79" text-anchor="middle"

&#x20;               font-family="DM Sans,sans-serif" font-size="8.5" font-weight="400"

&#x20;               fill="var(--ink)">wraps behind</text>

&#x20;         <text x="82" y="91" text-anchor="middle"

&#x20;               font-family="DM Sans,sans-serif" font-size="8.5" font-weight="300"

&#x20;               fill="var(--muted)">first warp</text>

&#x20;       </g>



&#x20;       <!-- ── STEP 2: loop around warp 2 ── -->

&#x20;       <g id="s2" style="opacity:0">

&#x20;         <!-- first loop faded -->

&#x20;         <path d="M 30,150 L 148,150 Q 128,150 128,120 Q 128,60 157,60

&#x20;                  Q 190,60 190,100 L 190,160"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="4"

&#x20;               stroke-linecap="round" opacity=".25"/>

&#x20;         <!-- crossover -->

&#x20;         <path class="anim-path" style="--len:60"

&#x20;               d="M 190,160 L 210,160"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;         <!-- second loop -->

&#x20;         <path id="loop2" class="anim-path" style="--len:320"

&#x20;               d="M 210,160

&#x20;                  Q 270,160 270,120

&#x20;                  Q 270,58 237,58

&#x20;                  Q 204,58 204,100

&#x20;                  L 204,280"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5"

&#x20;               stroke-linecap="round" opacity="0"/>

&#x20;         <!-- symmetry brace -->

&#x20;         <path id="sbrace" d="M 157,48 Q 197,38 237,48"

&#x20;               fill="none" stroke="var(--gold)" stroke-width="1" stroke-dasharray="3 2"

&#x20;               opacity="0"/>

&#x20;         <text id="symtxt" x="197" y="32" text-anchor="middle"

&#x20;               font-family="Cinzel,serif" font-size="7.5" fill="var(--gold)"

&#x20;               letter-spacing=".5" opacity="0">symmetric</text>

&#x20;       </g>



&#x20;       <!-- ── STEP 3: complete knot ── -->

&#x20;       <g id="s3" style="opacity:0">

&#x20;         <!-- full top arc (both loops) -->

&#x20;         <path class="anim-path" style="--len:700"

&#x20;               d="M 30,155 L 148,155

&#x20;                  Q 128,155 128,118

&#x20;                  Q 128,56 157,56

&#x20;                  Q 192,56 192,100

&#x20;                  L 192,160

&#x20;                  L 206,160

&#x20;                  Q 270,160 270,118

&#x20;                  Q 270,54 237,54

&#x20;                  Q 202,54 202,100

&#x20;                  L 202,155

&#x20;                  L 370,155"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;         <!-- left tail -->

&#x20;         <path id="lt" class="anim-path" style="--len:120"

&#x20;               d="M 192,160 L 192,285"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5"

&#x20;               stroke-linecap="round" opacity="0"/>

&#x20;         <!-- right tail -->

&#x20;         <path id="rt" class="anim-path" style="--len:120"

&#x20;               d="M 202,160 L 202,285"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="5"

&#x20;               stroke-linecap="round" opacity="0"/>



&#x20;         <!-- pile label -->

&#x20;         <g id="pileg" opacity="0">

&#x20;           <rect x="162" y="268" width="68" height="18" rx="3"

&#x20;                 fill="rgba(184,92,56,.12)" stroke="var(--terracotta)"

&#x20;                 stroke-width=".5"/>

&#x20;           <text x="196" y="281" text-anchor="middle"

&#x20;                 font-family="Cinzel,serif" font-size="7.5" fill="var(--terracotta)"

&#x20;                 letter-spacing=".5">pile / hav</text>

&#x20;         </g>

&#x20;         <!-- symmetry badge -->

&#x20;         <g id="symbadge" opacity="0">

&#x20;           <rect x="110" y="36" width="175" height="20" rx="3"

&#x20;                 fill="rgba(200,151,26,.12)" stroke="var(--gold)" stroke-width=".5"/>

&#x20;           <text x="197" y="50" text-anchor="middle"

&#x20;                 font-family="Cinzel,serif" font-size="7.5" fill="var(--gold)"

&#x20;                 letter-spacing=".5">symmetrical knot ✓</text>

&#x20;         </g>

&#x20;         <!-- right exit arrow -->

&#x20;         <path d="M 272,155 L 368,155"

&#x20;               fill="none" stroke="var(--yarn)" stroke-width="3"

&#x20;               stroke-linecap="round" marker-end="url(#ah)" opacity=".4"/>

&#x20;       </g>

&#x20;     </svg>

&#x20;   </div><!-- /.svg-wrap -->



&#x20;   <!-- Description -->

&#x20;   <div class="step-desc" id="descbox">

&#x20;     <span id="desctext">Begin with two vertical <strong>warp threads</strong>. These are the structural backbone of the carpet — tightly strung and under constant tension on the loom.</span>

&#x20;   </div>



&#x20;   <div class="nav-row">

&#x20;     <button class="nav-btn" id="prevbtn" onclick="prev()" disabled>← Prev</button>

&#x20;     <div class="progress-dots" id="pdots">

&#x20;       <div class="pdot active"></div>

&#x20;       <div class="pdot"></div>

&#x20;       <div class="pdot"></div>

&#x20;       <div class="pdot"></div>

&#x20;     </div>

&#x20;     <button class="nav-btn" id="nextbtn" onclick="next()">Next →</button>

&#x20;   </div>



&#x20; </div><!-- /.diagram-panel -->



&#x20; <!-- ──── RIGHT: Content ──── -->

&#x20; <div class="content-panel">



&#x20;   <div class="section-label">Origins</div>

&#x20;   <h2>A knot that has <em>outlasted</em> empires</h2>

&#x20;   <p>

&#x20;     The Turkish knot — known in academic literature as the <em>Ghiordes knot</em> after the weaving

&#x20;     town of Gördes in western Anatolia — has been documented in Anatolian textiles since at least

&#x20;     the 8th century BCE. It is the structural foundation of some of the world's most prized rugs.

&#x20;   </p>

&#x20;   <p>

&#x20;     Unlike its Persian counterpart (the asymmetrical Senneh knot), the Turkish knot wraps

&#x20;     symmetrically around both warp threads, creating a denser pile and a more durable structure —

&#x20;     ideal for the hardwearing village rugs of Central Anatolia.

&#x20;   </p>



&#x20;   <div class="fact-strip">

&#x20;     <div class="fact-card">

&#x20;       <div class="fact-val">2 500+</div>

&#x20;       <div class="fact-lbl">years of documented use</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fact-val">400–900</div>

&#x20;       <div class="fact-lbl">knots per dm² in fine work</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fact-val">2</div>

&#x20;       <div class="fact-lbl">warp threads per knot</div>

&#x20;     </div>

&#x20;     <div class="fact-card">

&#x20;       <div class="fact-val">100%</div>

&#x20;       <div class="fact-lbl">symmetrical — both sides equal</div>

&#x20;     </div>

&#x20;   </div>



&#x20;   <div class="section-label">Structure</div>

&#x20;   <h2>Turkish vs. <em>Persian</em></h2>



&#x20;   <table class="compare-table">

&#x20;     <thead>

&#x20;       <tr>

&#x20;         <th>Property</th>

&#x20;         <th>Turkish (Ghiordes)</th>

&#x20;         <th>Persian (Senneh)</th>

&#x20;       </tr>

&#x20;     </thead>

&#x20;     <tbody>

&#x20;       <tr class="highlight">

&#x20;         <td>Symmetry</td>

&#x20;         <td>Symmetrical — both warps</td>

&#x20;         <td>Asymmetrical — one warp</td>

&#x20;       </tr>

&#x20;       <tr>

&#x20;         <td>Pile density</td>

&#x20;         <td>Lower — but thicker</td>

&#x20;         <td>Higher — finer detail</td>

&#x20;       </tr>

&#x20;       <tr class="highlight">

&#x20;         <td>Durability</td>

&#x20;         <td>Very high — double anchor</td>

&#x20;         <td>High — single anchor</td>

&#x20;       </tr>

&#x20;       <tr>

&#x20;         <td>Origin regions</td>

&#x20;         <td>Anatolia, Caucasus</td>

&#x20;         <td>Iran, Central Asia</td>

&#x20;       </tr>

&#x20;       <tr class="highlight">

&#x20;         <td>Pile direction</td>

&#x20;         <td>Divided — exits centre</td>

&#x20;         <td>Single direction</td>

&#x20;       </tr>

&#x20;     </tbody>

&#x20;   </table>



&#x20;   <div class="pull-quote">

&#x20;     <p>The symmetry of the knot is not an accident — it is a philosophy. Both threads held equally, neither neglected.</p>

&#x20;     <cite>— Attributed to traditional Anatolian weavers' practice</cite>

&#x20;   </div>



&#x20;   <div class="section-label">Applications</div>

&#x20;   <h2>Where you find <em>this knot</em></h2>



&#x20;   <ul class="uses-list">

&#x20;     <li><strong>Village rugs (Köy halısı)</strong> — coarse wool, geometric motifs, high durability</li>

&#x20;     <li><strong>Tribal kilims</strong> — flat-woven borders using Turkish knot pile sections</li>

&#x20;     <li><strong>Hereke silk carpets</strong> — extraordinarily fine Turkish-knotted luxury work</li>

&#x20;     <li><strong>Caucasian rugs</strong> — Kazak, Shirvan and Karabagh traditions</li>

&#x20;     <li><strong>Contemporary restoration</strong> — museum conservators match original knot type</li>

&#x20;   </ul>



&#x20; </div><!-- /.content-panel -->



&#x20; <!-- ──── FULL-WIDTH: Anatomy ──── -->

&#x20; <div class="anatomy-section">

&#x20;   <div class="section-label" style="justify-content:center;max-width:300px;margin:0 auto 1rem">Anatomy</div>

&#x20;   <h2 style="text-align:center">The completed knot — <em>labelled</em></h2>



&#x20;   <div class="anatomy-svg-wrap">

&#x20;     <svg viewBox="0 0 900 220" width="100%" xmlns="http://www.w3.org/2000/svg">

&#x20;       <defs>

&#x20;         <marker id="ah2" viewBox="0 0 10 10" refX="8" refY="5"

&#x20;                 markerWidth="5" markerHeight="5" orient="auto-start-reverse">

&#x20;           <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"

&#x20;                 stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>

&#x20;         </marker>

&#x20;         <pattern id="linen2" width="4" height="4" patternUnits="userSpaceOnUse">

&#x20;           <rect width="4" height="4" fill="none"/>

&#x20;           <line x1="0" y1="2" x2="4" y2="2" stroke="#c9b99a" stroke-width=".3" opacity=".4"/>

&#x20;           <line x1="2" y1="0" x2="2" y2="4" stroke="#c9b99a" stroke-width=".3" opacity=".3"/>

&#x20;         </pattern>

&#x20;       </defs>



&#x20;       <rect width="900" height="220" fill="url(#linen2)"/>



&#x20;       <!-- WARP 1 -->

&#x20;       <rect x="375" y="10" width="12" height="200" rx="6" fill="var(--warp-dk)" opacity=".2"/>

&#x20;       <rect x="372" y="10" width="12" height="200" rx="6" fill="var(--warp)"/>

&#x20;       <rect x="374" y="10" width="3" height="200" rx="1.5" fill="rgba(255,255,255,.28)"/>

&#x20;       <!-- WARP 2 -->

&#x20;       <rect x="513" y="10" width="12" height="200" rx="6" fill="var(--warp-dk)" opacity=".2"/>

&#x20;       <rect x="510" y="10" width="12" height="200" rx="6" fill="var(--warp)"/>

&#x20;       <rect x="512" y="10" width="3" height="200" rx="1.5" fill="rgba(255,255,255,.28)"/>



&#x20;       <!-- Full knot path (anatomy view) -->

&#x20;       <!-- incoming left -->

&#x20;       <path d="M 80,110 L 370,110" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;       <!-- loop 1 -->

&#x20;       <path d="M 370,110 Q 350,110 350,85 Q 350,35 378,35 Q 410,35 410,72 L 410,125 L 488,125"

&#x20;             fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;       <!-- loop 2 -->

&#x20;       <path d="M 488,125 Q 545,125 545,85 Q 545,33 516,33 Q 486,33 486,72 L 486,110 L 820,110"

&#x20;             fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;       <!-- left tail -->

&#x20;       <path d="M 410,125 L 410,208" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

&#x20;       <!-- right tail -->

&#x20;       <path d="M 486,125 L 486,208" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>



&#x20;       <!-- outgoing right -->

&#x20;       <path d="M 820,110 L 870,110" fill="none" stroke="var(--yarn)" stroke-width="3"

&#x20;             stroke-linecap="round" marker-end="url(#ah2)" opacity=".4"/>



&#x20;       <!-- LABELS with leader lines -->

&#x20;       <!-- Warp 1 -->

&#x20;       <line x1="384" y1="10" x2="290" y2="8" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="384" cy="10" r="2" fill="var(--muted)"/>

&#x20;       <text x="286" y="6" text-anchor="end" font-family="Cinzel,serif" font-size="9"

&#x20;             fill="var(--muted)" letter-spacing=".5">Warp thread 1</text>



&#x20;       <!-- Warp 2 -->

&#x20;       <line x1="516" y1="10" x2="610" y2="8" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="516" cy="10" r="2" fill="var(--muted)"/>

&#x20;       <text x="614" y="6" text-anchor="start" font-family="Cinzel,serif" font-size="9"

&#x20;             fill="var(--muted)" letter-spacing=".5">Warp thread 2</text>



&#x20;       <!-- Symmetry brace -->

&#x20;       <path d="M 378,22 Q 448,14 516,22" fill="none" stroke="var(--gold)" stroke-width="1" stroke-dasharray="3 2"/>

&#x20;       <text x="448" y="12" text-anchor="middle" font-family="Cinzel,serif" font-size="8.5"

&#x20;             fill="var(--gold)" letter-spacing=".5">symmetrical wrap</text>



&#x20;       <!-- Left loop -->

&#x20;       <line x1="350" y1="72" x2="240" y2="60" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="350" cy="72" r="2" fill="var(--muted)"/>

&#x20;       <text x="236" y="56" text-anchor="end" font-family="DM Sans,sans-serif" font-size="9.5"

&#x20;             font-weight="300" fill="var(--ink)">Loop around</text>

&#x20;       <text x="236" y="68" text-anchor="end" font-family="DM Sans,sans-serif" font-size="9.5"

&#x20;             font-weight="300" fill="var(--ink)">warp 1</text>



&#x20;       <!-- Right loop -->

&#x20;       <line x1="545" y1="72" x2="650" y2="60" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="545" cy="72" r="2" fill="var(--muted)"/>

&#x20;       <text x="654" y="56" text-anchor="start" font-family="DM Sans,sans-serif" font-size="9.5"

&#x20;             font-weight="300" fill="var(--ink)">Loop around</text>

&#x20;       <text x="654" y="68" text-anchor="start" font-family="DM Sans,sans-serif" font-size="9.5"

&#x20;             font-weight="300" fill="var(--ink)">warp 2</text>



&#x20;       <!-- Pile label -->

&#x20;       <line x1="448" y1="175" x2="448" y2="210" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>

&#x20;       <circle cx="448" cy="175" r="2" fill="var(--muted)"/>

&#x20;       <rect x="398" y="210" width="100" height="16" rx="3" fill="rgba(184,92,56,.1)"

&#x20;             stroke="var(--terracotta)" stroke-width=".5"/>

&#x20;       <text x="448" y="222" text-anchor="middle" font-family="Cinzel,serif" font-size="8.5"

&#x20;             fill="var(--terracotta)" letter-spacing=".5">pile (hav)</text>



&#x20;       <!-- Double-anchor text -->

&#x20;       <rect x="358" y="130" width="180" height="20" rx="3"

&#x20;             fill="rgba(200,151,26,.1)" stroke="var(--gold)" stroke-width=".5"/>

&#x20;       <text x="448" y="144" text-anchor="middle" font-family="Cinzel,serif" font-size="7.5"

&#x20;             fill="var(--gold)" letter-spacing=".5">double anchor point</text>

&#x20;     </svg>

&#x20;   </div>

&#x20; </div>



</main>



<!-- ═══════════════ FOOTER ═══════════════ -->

<footer>

&#x20; <span>◆</span> \&nbsp; The Turkish Knot · Anatolian Weaving Education \&nbsp; <span>◆</span>

</footer>



<!-- ═══════════════ SCRIPT ═══════════════ -->

<script>

const STEPS = \[

&#x20; {

&#x20;   desc: `Begin with two vertical <strong>warp threads</strong>. These are the structural backbone of the carpet — tightly strung and under constant tension on the loom. Every single knot in the rug will be tied around pairs of these threads.`

&#x20; },

&#x20; {

&#x20;   desc: `The wool thread approaches from the left and <strong>wraps behind and around the first warp</strong>. It passes over the front, loops under, and the end hangs down below. This creates the first anchor of the knot.`

&#x20; },

&#x20; {

&#x20;   desc: `The thread <strong>crosses between the two warps</strong> and mirrors the same motion on the second warp — wrapping behind and coming forward again. Both ends now exit downward through the centre gap.`

&#x20; },

&#x20; {

&#x20;   desc: `The knot is <strong>complete and symmetric</strong>. The two hanging ends are cut to the desired pile height. This double-anchor structure — equal on both sides — is what gives Anatolian rugs their legendary durability, lasting centuries of heavy use.`

&#x20; }

];



let cur = 0;



function goTo(n) {

&#x20; const prev = cur;

&#x20; cur = n;



&#x20; // hide all step groups

&#x20; \[0,1,2,3].forEach(i => {

&#x20;   const el = document.getElementById('s' + i);

&#x20;   el.style.opacity = i === n ? '1' : '0';

&#x20;   el.style.transition = 'opacity .35s';

&#x20; });



&#x20; // re-trigger animations on current step

&#x20; const el = document.getElementById('s' + n);

&#x20; el.querySelectorAll('.anim-path').forEach(p => {

&#x20;   const len = parseFloat(getComputedStyle(p).getPropertyValue('--len')) ||

&#x20;               parseFloat(p.style.cssText.match(/--len:\\s\*(\[\\d.]+)/)?.\[1]) || 400;

&#x20;   p.classList.remove('run');

&#x20;   void p.offsetWidth;

&#x20;   p.style.strokeDashoffset = len;

&#x20;   setTimeout(() => {

&#x20;     p.style.animation = `drawPath .9s cubic-bezier(.4,0,.2,1) forwards`;

&#x20;     p.style.strokeDashoffset = 0;

&#x20;   }, 30);

&#x20; });



&#x20; // Step 2 extras

&#x20; if (n === 2) {

&#x20;   setTimeout(() => {

&#x20;     const l2 = document.getElementById('loop2');

&#x20;     l2.style.opacity = '1';

&#x20;     l2.style.animation = 'none';

&#x20;     void l2.offsetWidth;

&#x20;     l2.style.strokeDashoffset = 320;

&#x20;     l2.style.animation = 'drawPath .9s .25s cubic-bezier(.4,0,.2,1) forwards';

&#x20;     document.getElementById('sbrace').style.opacity = '1';

&#x20;     document.getElementById('symtxt').style.opacity = '1';

&#x20;   }, 350);

&#x20; }



&#x20; // Step 3 extras

&#x20; if (n === 3) {

&#x20;   setTimeout(() => {

&#x20;     \['lt','rt'].forEach((id, i) => {

&#x20;       const p = document.getElementById(id);

&#x20;       p.style.opacity = '1';

&#x20;       p.style.animation = 'none';

&#x20;       void p.offsetWidth;

&#x20;       p.style.strokeDashoffset = 120;

&#x20;       p.style.animation = `drawPath .55s ${.65 + i \* .12}s ease forwards`;

&#x20;     });

&#x20;     setTimeout(() => {

&#x20;       document.getElementById('pileg').style.opacity = '1';

&#x20;       document.getElementById('symbadge').style.opacity = '1';

&#x20;     }, 1000);

&#x20;   }, 100);

&#x20; }



&#x20; // Update tabs

&#x20; document.querySelectorAll('.step-tab').forEach((b, i) =>

&#x20;   b.classList.toggle('active', i === n));



&#x20; // Update dots

&#x20; document.querySelectorAll('.pdot').forEach((d, i) =>

&#x20;   d.classList.toggle('active', i === n));



&#x20; // Update buttons

&#x20; document.getElementById('prevbtn').disabled = n === 0;

&#x20; document.getElementById('nextbtn').disabled = n === STEPS.length - 1;



&#x20; // Update description

&#x20; const descEl = document.getElementById('desctext');

&#x20; descEl.parentElement.style.animation = 'none';

&#x20; void descEl.parentElement.offsetWidth;

&#x20; descEl.parentElement.style.animation = 'fadeUp .4s ease forwards';

&#x20; descEl.innerHTML = STEPS\[n].desc;

}



function next() { if (cur < STEPS.length - 1) goTo(cur + 1); }

function prev() { if (cur > 0) goTo(cur - 1); }



// Keyboard navigation

document.addEventListener('keydown', e => {

&#x20; if (e.key === 'ArrowRight') next();

&#x20; if (e.key === 'ArrowLeft')  prev();

});



// Init

goTo(0);

</script>



</body>

</html>

