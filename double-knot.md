<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Turkish Knot — Anatolian Rug Weaving</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Cinzel:wght@400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">

<style>
  :root {
    --cream:    #f5f0e8;
    --parchment:#ede4d0;
    --warm:     #c9b99a;
    --terracotta:#b85c38;
    --brick:    #8b3a22;
    --gold:     #c8971a;
    --gold-lt:  #e8c050;
    --ink:      #2c1a0e;
    --muted:    #7a6555;
    --warp:     #c8aa7a;
    --warp-dk:  #a07a45;
    --yarn:     #b85c38;
    --yarn-hl:  #e07a50;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background-color: var(--cream);
    background-image:
      radial-gradient(ellipse at 20% 10%, rgba(200,151,26,.12) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 90%, rgba(184,92,56,.10) 0%, transparent 50%),
      url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23c9b99a' fill-opacity='0.08'%3E%3Cpath d='M40 0 L80 40 L40 80 L0 40Z'/%3E%3C/g%3E%3C/svg%3E");
    color: var(--ink);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    min-height: 100vh;
    padding: 0;
    overflow-x: hidden;
  }

  /* ── HEADER ── */
  header {
    text-align: center;
    padding: 4rem 2rem 2.5rem;
    position: relative;
    border-bottom: 1px solid var(--warm);
  }
  .header-ornament {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 1.2rem;
  }
  .header-ornament::before,
  .header-ornament::after {
    content: '';
    flex: 1;
    max-width: 120px;
    height: 1px;
    background: linear-gradient(to right, transparent, var(--gold));
  }
  .header-ornament::after {
    background: linear-gradient(to left, transparent, var(--gold));
  }
  .origin-tag {
    font-family: 'Cinzel', serif;
    font-size: 0.65rem;
    letter-spacing: .25em;
    color: var(--gold);
    text-transform: uppercase;
  }
  h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2.8rem, 7vw, 5rem);
    font-weight: 300;
    letter-spacing: .04em;
    line-height: 1.05;
    color: var(--ink);
    margin-bottom: .6rem;
  }
  h1 em {
    font-style: italic;
    color: var(--brick);
  }
  .subtitle {
    font-family: 'DM Sans', sans-serif;
    font-size: .95rem;
    font-weight: 300;
    color: var(--muted);
    letter-spacing: .08em;
    margin-bottom: .3rem;
  }
  .aka {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1rem;
    font-style: italic;
    color: var(--muted);
  }

  /* ── MAIN LAYOUT ── */
  main {
    max-width: 1100px;
    margin: 0 auto;
    padding: 3rem 2rem 5rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem 4rem;
    align-items: start;
  }
  @media (max-width: 780px) {
    main { grid-template-columns: 1fr; gap: 2rem; }
  }

  /* ── LEFT: INTERACTIVE DIAGRAM ── */
  .diagram-panel {
    position: sticky;
    top: 2rem;
  }

  /* Step indicator */
  .step-tabs {
    display: flex;
    border-bottom: 1px solid var(--warm);
    margin-bottom: 1.5rem;
    gap: 0;
  }
  .step-tab {
    flex: 1;
    background: none;
    border: none;
    padding: .65rem .5rem;
    cursor: pointer;
    font-family: 'Cinzel', serif;
    font-size: .62rem;
    letter-spacing: .12em;
    color: var(--muted);
    border-bottom: 2px solid transparent;
    transition: all .25s;
    text-align: center;
    line-height: 1.3;
  }
  .step-tab:hover { color: var(--terracotta); }
  .step-tab.active {
    color: var(--terracotta);
    border-bottom-color: var(--terracotta);
  }
  .step-tab .tab-num {
    display: block;
    font-size: .55rem;
    color: var(--gold);
    margin-bottom: .15rem;
  }

  /* SVG container */
  .svg-wrap {
    background: var(--parchment);
    border: 1px solid var(--warm);
    border-radius: 4px;
    overflow: hidden;
    position: relative;
    aspect-ratio: 4/3;
  }
  .svg-wrap svg { width: 100%; height: 100%; display: block; }

  /* Description */
  .step-desc {
    margin-top: 1.2rem;
    padding: 1rem 1.25rem;
    background: rgba(200,151,26,.07);
    border-left: 3px solid var(--gold);
    border-radius: 0 4px 4px 0;
    font-size: .9rem;
    line-height: 1.75;
    color: var(--ink);
    min-height: 5rem;
  }
  .step-desc strong { color: var(--brick); font-weight: 500; }

  /* Nav buttons */
  .nav-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 1rem;
  }
  .nav-btn {
    background: none;
    border: 1px solid var(--warm);
    border-radius: 2px;
    padding: .5rem 1.2rem;
    font-family: 'Cinzel', serif;
    font-size: .65rem;
    letter-spacing: .12em;
    color: var(--muted);
    cursor: pointer;
    transition: all .2s;
  }
  .nav-btn:hover:not(:disabled) {
    border-color: var(--terracotta);
    color: var(--terracotta);
  }
  .nav-btn:disabled { opacity: .3; cursor: default; }

  .progress-dots {
    display: flex;
    gap: 8px;
  }
  .pdot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--warm);
    transition: background .3s, transform .3s;
  }
  .pdot.active {
    background: var(--terracotta);
    transform: scale(1.3);
  }

  /* ── RIGHT: CONTENT ── */
  .content-panel { padding-top: .5rem; }

  .section-label {
    font-family: 'Cinzel', serif;
    font-size: .6rem;
    letter-spacing: .3em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: .8rem;
    display: flex;
    align-items: center;
    gap: .75rem;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--warm), transparent);
  }

  h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 400;
    line-height: 1.2;
    margin-bottom: 1rem;
    color: var(--ink);
  }
  h2 em { font-style: italic; color: var(--brick); }

  p {
    font-size: .92rem;
    line-height: 1.85;
    color: var(--muted);
    margin-bottom: 1.1rem;
  }

  /* Fact strip */
  .fact-strip {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: .75rem;
    margin: 1.5rem 0;
  }
  .fact-card {
    background: var(--parchment);
    border: 1px solid var(--warm);
    border-radius: 4px;
    padding: .9rem 1rem;
  }
  .fact-card .fact-val {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.6rem;
    font-weight: 600;
    color: var(--terracotta);
    line-height: 1;
    margin-bottom: .2rem;
  }
  .fact-card .fact-lbl {
    font-size: .72rem;
    letter-spacing: .06em;
    color: var(--muted);
    font-weight: 300;
  }

  /* Comparison table */
  .compare-table {
    width: 100%;
    border-collapse: collapse;
    font-size: .85rem;
    margin: 1.5rem 0;
  }
  .compare-table thead tr {
    border-bottom: 1.5px solid var(--gold);
  }
  .compare-table th {
    font-family: 'Cinzel', serif;
    font-size: .6rem;
    letter-spacing: .15em;
    color: var(--gold);
    font-weight: 400;
    padding: .5rem .75rem;
    text-align: left;
  }
  .compare-table th:first-child { width: 40%; }
  .compare-table td {
    padding: .6rem .75rem;
    border-bottom: 1px solid rgba(201,185,154,.35);
    color: var(--muted);
    vertical-align: top;
    line-height: 1.5;
  }
  .compare-table td:first-child {
    color: var(--ink);
    font-weight: 400;
  }
  .compare-table .highlight td { background: rgba(184,92,56,.06); }
  .compare-table .highlight td:first-child { color: var(--brick); }

  /* Pull quote */
  .pull-quote {
    margin: 2rem 0;
    padding: 1.5rem 2rem;
    border-top: 1px solid var(--warm);
    border-bottom: 1px solid var(--warm);
    position: relative;
  }
  .pull-quote::before {
    content: '\201C';
    font-family: 'Cormorant Garamond', serif;
    font-size: 5rem;
    color: var(--gold);
    opacity: .25;
    position: absolute;
    top: -.5rem; left: 1rem;
    line-height: 1;
  }
  .pull-quote p {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.3rem;
    font-style: italic;
    line-height: 1.6;
    color: var(--ink);
    margin-bottom: .4rem;
  }
  .pull-quote cite {
    font-size: .75rem;
    letter-spacing: .1em;
    color: var(--muted);
  }

  /* Uses list */
  .uses-list {
    list-style: none;
    margin: .5rem 0 1.5rem;
  }
  .uses-list li {
    display: flex;
    align-items: baseline;
    gap: .75rem;
    font-size: .88rem;
    color: var(--muted);
    padding: .45rem 0;
    border-bottom: 1px solid rgba(201,185,154,.3);
    line-height: 1.5;
  }
  .uses-list li::before {
    content: '◆';
    font-size: .45rem;
    color: var(--gold);
    flex-shrink: 0;
    transform: translateY(-1px);
  }
  .uses-list strong { color: var(--ink); font-weight: 400; }

  /* Full-width anatomy diagram */
  .anatomy-section {
    grid-column: 1 / -1;
    padding-top: 2rem;
    border-top: 1px solid var(--warm);
  }
  .anatomy-section h2 {
    font-size: 1.6rem;
    text-align: center;
    margin-bottom: 2rem;
  }
  .anatomy-svg-wrap {
    background: var(--parchment);
    border: 1px solid var(--warm);
    border-radius: 4px;
    padding: 1rem;
  }

  /* Footer */
  footer {
    text-align: center;
    padding: 2rem;
    border-top: 1px solid var(--warm);
    font-size: .75rem;
    letter-spacing: .08em;
    color: var(--muted);
  }
  footer span { color: var(--gold); }

  /* Animations */
  @keyframes drawPath {
    from { stroke-dashoffset: var(--len); }
    to   { stroke-dashoffset: 0; }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(8px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .anim-path {
    stroke-dasharray: var(--len);
    stroke-dashoffset: var(--len);
  }
  .anim-path.run {
    animation: drawPath .85s cubic-bezier(.4,0,.2,1) forwards;
  }
  .fade-up { animation: fadeUp .4s ease forwards; }

  /* Responsive tweaks */
  @media (max-width: 500px) {
    h1 { font-size: 2.4rem; }
    .fact-strip { grid-template-columns: 1fr 1fr; }
    .step-tab { font-size: .55rem; }
  }
</style>
</head>
<body>

<!-- ═══════════════ HEADER ═══════════════ -->
<header>
  <div class="header-ornament"><span class="origin-tag">Anatolia · Traditional Craft</span></div>
  <h1>The <em>Turkish</em> Knot</h1>
  <p class="subtitle">An Interactive Guide to Anatolian Rug Weaving</p>
  <p class="aka">Also known as the Symmetrical Knot · Ghiordes Knot</p>
</header>

<!-- ═══════════════ MAIN ═══════════════ -->
<main>

  <!-- ──── LEFT: Interactive Diagram ──── -->
  <div class="diagram-panel">

    <div class="step-tabs">
      <button class="step-tab active" onclick="goTo(0)">
        <span class="tab-num">I</span>Setup
      </button>
      <button class="step-tab" onclick="goTo(1)">
        <span class="tab-num">II</span>First Loop
      </button>
      <button class="step-tab" onclick="goTo(2)">
        <span class="tab-num">III</span>Second Loop
      </button>
      <button class="step-tab" onclick="goTo(3)">
        <span class="tab-num">IV</span>Complete
      </button>
    </div>

    <div class="svg-wrap">
      <svg id="knotsvg" viewBox="0 0 400 300" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <marker id="ah" viewBox="0 0 10 10" refX="8" refY="5"
                  markerWidth="5" markerHeight="5" orient="auto-start-reverse">
            <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"
                  stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
          </marker>
          <!-- subtle linen texture pattern -->
          <pattern id="linen" width="4" height="4" patternUnits="userSpaceOnUse">
            <rect width="4" height="4" fill="none"/>
            <line x1="0" y1="2" x2="4" y2="2" stroke="#c9b99a" stroke-width=".3" opacity=".4"/>
            <line x1="2" y1="0" x2="2" y2="4" stroke="#c9b99a" stroke-width=".3" opacity=".3"/>
          </pattern>
        </defs>

        <!-- background linen -->
        <rect width="400" height="300" fill="url(#linen)"/>

        <!-- WARP THREADS (always visible) -->
        <!-- warp 1 shadow -->
        <rect x="153" y="20" width="14" height="260" rx="7" fill="var(--warp-dk)" opacity=".25"/>
        <!-- warp 1 -->
        <rect x="150" y="20" width="14" height="260" rx="7" fill="var(--warp)"/>
        <!-- warp 1 highlight -->
        <rect x="152" y="20" width="4" height="260" rx="2" fill="rgba(255,255,255,.3)"/>

        <!-- warp 2 shadow -->
        <rect x="233" y="20" width="14" height="260" rx="7" fill="var(--warp-dk)" opacity=".25"/>
        <!-- warp 2 -->
        <rect x="230" y="20" width="14" height="260" rx="7" fill="var(--warp)"/>
        <!-- warp 2 highlight -->
        <rect x="232" y="20" width="4" height="260" rx="2" fill="rgba(255,255,255,.3)"/>

        <!-- warp labels -->
        <text x="157" y="295" text-anchor="middle" font-family="Cinzel,serif" font-size="8" fill="#a07a45" letter-spacing="1">W1</text>
        <text x="237" y="295" text-anchor="middle" font-family="Cinzel,serif" font-size="8" fill="#a07a45" letter-spacing="1">W2</text>

        <!-- ── STEP 0: approaching thread ── -->
        <g id="s0">
          <path class="anim-path" style="--len:120"
                d="M 30,150 L 148,150"
                fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"
                marker-end="url(#ah)"/>
          <text x="85" y="138" text-anchor="middle"
                font-family="DM Sans,sans-serif" font-size="9.5" font-weight="300"
                fill="var(--terracotta)" letter-spacing=".5">wool thread</text>
        </g>

        <!-- ── STEP 1: loop around warp 1 ── -->
        <g id="s1" style="opacity:0">
          <path class="anim-path" style="--len:350"
                d="M 30,150 L 148,150
                   Q 128,150 128,120
                   Q 128,60 157,60
                   Q 190,60 190,100
                   L 190,280"
                fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
          <!-- label -->
          <rect x="42" y="65" width="80" height="34" rx="3"
                fill="rgba(237,228,208,.88)"/>
          <text x="82" y="79" text-anchor="middle"
                font-family="DM Sans,sans-serif" font-size="8.5" font-weight="400"
                fill="var(--ink)">wraps behind</text>
          <text x="82" y="91" text-anchor="middle"
                font-family="DM Sans,sans-serif" font-size="8.5" font-weight="300"
                fill="var(--muted)">first warp</text>
        </g>

        <!-- ── STEP 2: loop around warp 2 ── -->
        <g id="s2" style="opacity:0">
          <!-- first loop faded -->
          <path d="M 30,150 L 148,150 Q 128,150 128,120 Q 128,60 157,60
                   Q 190,60 190,100 L 190,160"
                fill="none" stroke="var(--yarn)" stroke-width="4"
                stroke-linecap="round" opacity=".25"/>
          <!-- crossover -->
          <path class="anim-path" style="--len:60"
                d="M 190,160 L 210,160"
                fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
          <!-- second loop -->
          <path id="loop2" class="anim-path" style="--len:320"
                d="M 210,160
                   Q 270,160 270,120
                   Q 270,58 237,58
                   Q 204,58 204,100
                   L 204,280"
                fill="none" stroke="var(--yarn)" stroke-width="5"
                stroke-linecap="round" opacity="0"/>
          <!-- symmetry brace -->
          <path id="sbrace" d="M 157,48 Q 197,38 237,48"
                fill="none" stroke="var(--gold)" stroke-width="1" stroke-dasharray="3 2"
                opacity="0"/>
          <text id="symtxt" x="197" y="32" text-anchor="middle"
                font-family="Cinzel,serif" font-size="7.5" fill="var(--gold)"
                letter-spacing=".5" opacity="0">symmetric</text>
        </g>

        <!-- ── STEP 3: complete knot ── -->
        <g id="s3" style="opacity:0">
          <!-- full top arc (both loops) -->
          <path class="anim-path" style="--len:700"
                d="M 30,155 L 148,155
                   Q 128,155 128,118
                   Q 128,56 157,56
                   Q 192,56 192,100
                   L 192,160
                   L 206,160
                   Q 270,160 270,118
                   Q 270,54 237,54
                   Q 202,54 202,100
                   L 202,155
                   L 370,155"
                fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
          <!-- left tail -->
          <path id="lt" class="anim-path" style="--len:120"
                d="M 192,160 L 192,285"
                fill="none" stroke="var(--yarn)" stroke-width="5"
                stroke-linecap="round" opacity="0"/>
          <!-- right tail -->
          <path id="rt" class="anim-path" style="--len:120"
                d="M 202,160 L 202,285"
                fill="none" stroke="var(--yarn)" stroke-width="5"
                stroke-linecap="round" opacity="0"/>

          <!-- pile label -->
          <g id="pileg" opacity="0">
            <rect x="162" y="268" width="68" height="18" rx="3"
                  fill="rgba(184,92,56,.12)" stroke="var(--terracotta)"
                  stroke-width=".5"/>
            <text x="196" y="281" text-anchor="middle"
                  font-family="Cinzel,serif" font-size="7.5" fill="var(--terracotta)"
                  letter-spacing=".5">pile / hav</text>
          </g>
          <!-- symmetry badge -->
          <g id="symbadge" opacity="0">
            <rect x="110" y="36" width="175" height="20" rx="3"
                  fill="rgba(200,151,26,.12)" stroke="var(--gold)" stroke-width=".5"/>
            <text x="197" y="50" text-anchor="middle"
                  font-family="Cinzel,serif" font-size="7.5" fill="var(--gold)"
                  letter-spacing=".5">symmetrical knot ✓</text>
          </g>
          <!-- right exit arrow -->
          <path d="M 272,155 L 368,155"
                fill="none" stroke="var(--yarn)" stroke-width="3"
                stroke-linecap="round" marker-end="url(#ah)" opacity=".4"/>
        </g>
      </svg>
    </div><!-- /.svg-wrap -->

    <!-- Description -->
    <div class="step-desc" id="descbox">
      <span id="desctext">Begin with two vertical <strong>warp threads</strong>. These are the structural backbone of the carpet — tightly strung and under constant tension on the loom.</span>
    </div>

    <div class="nav-row">
      <button class="nav-btn" id="prevbtn" onclick="prev()" disabled>← Prev</button>
      <div class="progress-dots" id="pdots">
        <div class="pdot active"></div>
        <div class="pdot"></div>
        <div class="pdot"></div>
        <div class="pdot"></div>
      </div>
      <button class="nav-btn" id="nextbtn" onclick="next()">Next →</button>
    </div>

  </div><!-- /.diagram-panel -->

  <!-- ──── RIGHT: Content ──── -->
  <div class="content-panel">

    <div class="section-label">Origins</div>
    <h2>A knot that has <em>outlasted</em> empires</h2>
    <p>
      The Turkish knot — known in academic literature as the <em>Ghiordes knot</em> after the weaving
      town of Gördes in western Anatolia — has been documented in Anatolian textiles since at least
      the 8th century BCE. It is the structural foundation of some of the world's most prized rugs.
    </p>
    <p>
      Unlike its Persian counterpart (the asymmetrical Senneh knot), the Turkish knot wraps
      symmetrically around both warp threads, creating a denser pile and a more durable structure —
      ideal for the hardwearing village rugs of Central Anatolia.
    </p>

    <div class="fact-strip">
      <div class="fact-card">
        <div class="fact-val">2 500+</div>
        <div class="fact-lbl">years of documented use</div>
      </div>
      <div class="fact-card">
        <div class="fact-val">400–900</div>
        <div class="fact-lbl">knots per dm² in fine work</div>
      </div>
      <div class="fact-card">
        <div class="fact-val">2</div>
        <div class="fact-lbl">warp threads per knot</div>
      </div>
      <div class="fact-card">
        <div class="fact-val">100%</div>
        <div class="fact-lbl">symmetrical — both sides equal</div>
      </div>
    </div>

    <div class="section-label">Structure</div>
    <h2>Turkish vs. <em>Persian</em></h2>

    <table class="compare-table">
      <thead>
        <tr>
          <th>Property</th>
          <th>Turkish (Ghiordes)</th>
          <th>Persian (Senneh)</th>
        </tr>
      </thead>
      <tbody>
        <tr class="highlight">
          <td>Symmetry</td>
          <td>Symmetrical — both warps</td>
          <td>Asymmetrical — one warp</td>
        </tr>
        <tr>
          <td>Pile density</td>
          <td>Lower — but thicker</td>
          <td>Higher — finer detail</td>
        </tr>
        <tr class="highlight">
          <td>Durability</td>
          <td>Very high — double anchor</td>
          <td>High — single anchor</td>
        </tr>
        <tr>
          <td>Origin regions</td>
          <td>Anatolia, Caucasus</td>
          <td>Iran, Central Asia</td>
        </tr>
        <tr class="highlight">
          <td>Pile direction</td>
          <td>Divided — exits centre</td>
          <td>Single direction</td>
        </tr>
      </tbody>
    </table>

    <div class="pull-quote">
      <p>The symmetry of the knot is not an accident — it is a philosophy. Both threads held equally, neither neglected.</p>
      <cite>— Attributed to traditional Anatolian weavers' practice</cite>
    </div>

    <div class="section-label">Applications</div>
    <h2>Where you find <em>this knot</em></h2>

    <ul class="uses-list">
      <li><strong>Village rugs (Köy halısı)</strong> — coarse wool, geometric motifs, high durability</li>
      <li><strong>Tribal kilims</strong> — flat-woven borders using Turkish knot pile sections</li>
      <li><strong>Hereke silk carpets</strong> — extraordinarily fine Turkish-knotted luxury work</li>
      <li><strong>Caucasian rugs</strong> — Kazak, Shirvan and Karabagh traditions</li>
      <li><strong>Contemporary restoration</strong> — museum conservators match original knot type</li>
    </ul>

  </div><!-- /.content-panel -->

  <!-- ──── FULL-WIDTH: Anatomy ──── -->
  <div class="anatomy-section">
    <div class="section-label" style="justify-content:center;max-width:300px;margin:0 auto 1rem">Anatomy</div>
    <h2 style="text-align:center">The completed knot — <em>labelled</em></h2>

    <div class="anatomy-svg-wrap">
      <svg viewBox="0 0 900 220" width="100%" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <marker id="ah2" viewBox="0 0 10 10" refX="8" refY="5"
                  markerWidth="5" markerHeight="5" orient="auto-start-reverse">
            <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"
                  stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
          </marker>
          <pattern id="linen2" width="4" height="4" patternUnits="userSpaceOnUse">
            <rect width="4" height="4" fill="none"/>
            <line x1="0" y1="2" x2="4" y2="2" stroke="#c9b99a" stroke-width=".3" opacity=".4"/>
            <line x1="2" y1="0" x2="2" y2="4" stroke="#c9b99a" stroke-width=".3" opacity=".3"/>
          </pattern>
        </defs>

        <rect width="900" height="220" fill="url(#linen2)"/>

        <!-- WARP 1 -->
        <rect x="375" y="10" width="12" height="200" rx="6" fill="var(--warp-dk)" opacity=".2"/>
        <rect x="372" y="10" width="12" height="200" rx="6" fill="var(--warp)"/>
        <rect x="374" y="10" width="3" height="200" rx="1.5" fill="rgba(255,255,255,.28)"/>
        <!-- WARP 2 -->
        <rect x="513" y="10" width="12" height="200" rx="6" fill="var(--warp-dk)" opacity=".2"/>
        <rect x="510" y="10" width="12" height="200" rx="6" fill="var(--warp)"/>
        <rect x="512" y="10" width="3" height="200" rx="1.5" fill="rgba(255,255,255,.28)"/>

        <!-- Full knot path (anatomy view) -->
        <!-- incoming left -->
        <path d="M 80,110 L 370,110" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
        <!-- loop 1 -->
        <path d="M 370,110 Q 350,110 350,85 Q 350,35 378,35 Q 410,35 410,72 L 410,125 L 488,125"
              fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
        <!-- loop 2 -->
        <path d="M 488,125 Q 545,125 545,85 Q 545,33 516,33 Q 486,33 486,72 L 486,110 L 820,110"
              fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
        <!-- left tail -->
        <path d="M 410,125 L 410,208" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>
        <!-- right tail -->
        <path d="M 486,125 L 486,208" fill="none" stroke="var(--yarn)" stroke-width="5" stroke-linecap="round"/>

        <!-- outgoing right -->
        <path d="M 820,110 L 870,110" fill="none" stroke="var(--yarn)" stroke-width="3"
              stroke-linecap="round" marker-end="url(#ah2)" opacity=".4"/>

        <!-- LABELS with leader lines -->
        <!-- Warp 1 -->
        <line x1="384" y1="10" x2="290" y2="8" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>
        <circle cx="384" cy="10" r="2" fill="var(--muted)"/>
        <text x="286" y="6" text-anchor="end" font-family="Cinzel,serif" font-size="9"
              fill="var(--muted)" letter-spacing=".5">Warp thread 1</text>

        <!-- Warp 2 -->
        <line x1="516" y1="10" x2="610" y2="8" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>
        <circle cx="516" cy="10" r="2" fill="var(--muted)"/>
        <text x="614" y="6" text-anchor="start" font-family="Cinzel,serif" font-size="9"
              fill="var(--muted)" letter-spacing=".5">Warp thread 2</text>

        <!-- Symmetry brace -->
        <path d="M 378,22 Q 448,14 516,22" fill="none" stroke="var(--gold)" stroke-width="1" stroke-dasharray="3 2"/>
        <text x="448" y="12" text-anchor="middle" font-family="Cinzel,serif" font-size="8.5"
              fill="var(--gold)" letter-spacing=".5">symmetrical wrap</text>

        <!-- Left loop -->
        <line x1="350" y1="72" x2="240" y2="60" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>
        <circle cx="350" cy="72" r="2" fill="var(--muted)"/>
        <text x="236" y="56" text-anchor="end" font-family="DM Sans,sans-serif" font-size="9.5"
              font-weight="300" fill="var(--ink)">Loop around</text>
        <text x="236" y="68" text-anchor="end" font-family="DM Sans,sans-serif" font-size="9.5"
              font-weight="300" fill="var(--ink)">warp 1</text>

        <!-- Right loop -->
        <line x1="545" y1="72" x2="650" y2="60" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>
        <circle cx="545" cy="72" r="2" fill="var(--muted)"/>
        <text x="654" y="56" text-anchor="start" font-family="DM Sans,sans-serif" font-size="9.5"
              font-weight="300" fill="var(--ink)">Loop around</text>
        <text x="654" y="68" text-anchor="start" font-family="DM Sans,sans-serif" font-size="9.5"
              font-weight="300" fill="var(--ink)">warp 2</text>

        <!-- Pile label -->
        <line x1="448" y1="175" x2="448" y2="210" stroke="var(--muted)" stroke-width=".7" stroke-dasharray="3 2"/>
        <circle cx="448" cy="175" r="2" fill="var(--muted)"/>
        <rect x="398" y="210" width="100" height="16" rx="3" fill="rgba(184,92,56,.1)"
              stroke="var(--terracotta)" stroke-width=".5"/>
        <text x="448" y="222" text-anchor="middle" font-family="Cinzel,serif" font-size="8.5"
              fill="var(--terracotta)" letter-spacing=".5">pile (hav)</text>

        <!-- Double-anchor text -->
        <rect x="358" y="130" width="180" height="20" rx="3"
              fill="rgba(200,151,26,.1)" stroke="var(--gold)" stroke-width=".5"/>
        <text x="448" y="144" text-anchor="middle" font-family="Cinzel,serif" font-size="7.5"
              fill="var(--gold)" letter-spacing=".5">double anchor point</text>
      </svg>
    </div>
  </div>

</main>

<!-- ═══════════════ FOOTER ═══════════════ -->
<footer>
  <span>◆</span> &nbsp; The Turkish Knot · Anatolian Weaving Education &nbsp; <span>◆</span>
</footer>

<!-- ═══════════════ SCRIPT ═══════════════ -->
<script>
const STEPS = [
  {
    desc: `Begin with two vertical <strong>warp threads</strong>. These are the structural backbone of the carpet — tightly strung and under constant tension on the loom. Every single knot in the rug will be tied around pairs of these threads.`
  },
  {
    desc: `The wool thread approaches from the left and <strong>wraps behind and around the first warp</strong>. It passes over the front, loops under, and the end hangs down below. This creates the first anchor of the knot.`
  },
  {
    desc: `The thread <strong>crosses between the two warps</strong> and mirrors the same motion on the second warp — wrapping behind and coming forward again. Both ends now exit downward through the centre gap.`
  },
  {
    desc: `The knot is <strong>complete and symmetric</strong>. The two hanging ends are cut to the desired pile height. This double-anchor structure — equal on both sides — is what gives Anatolian rugs their legendary durability, lasting centuries of heavy use.`
  }
];

let cur = 0;

function goTo(n) {
  const prev = cur;
  cur = n;

  // hide all step groups
  [0,1,2,3].forEach(i => {
    const el = document.getElementById('s' + i);
    el.style.opacity = i === n ? '1' : '0';
    el.style.transition = 'opacity .35s';
  });

  // re-trigger animations on current step
  const el = document.getElementById('s' + n);
  el.querySelectorAll('.anim-path').forEach(p => {
    const len = parseFloat(getComputedStyle(p).getPropertyValue('--len')) ||
                parseFloat(p.style.cssText.match(/--len:\s*([\d.]+)/)?.[1]) || 400;
    p.classList.remove('run');
    void p.offsetWidth;
    p.style.strokeDashoffset = len;
    setTimeout(() => {
      p.style.animation = `drawPath .9s cubic-bezier(.4,0,.2,1) forwards`;
      p.style.strokeDashoffset = 0;
    }, 30);
  });

  // Step 2 extras
  if (n === 2) {
    setTimeout(() => {
      const l2 = document.getElementById('loop2');
      l2.style.opacity = '1';
      l2.style.animation = 'none';
      void l2.offsetWidth;
      l2.style.strokeDashoffset = 320;
      l2.style.animation = 'drawPath .9s .25s cubic-bezier(.4,0,.2,1) forwards';
      document.getElementById('sbrace').style.opacity = '1';
      document.getElementById('symtxt').style.opacity = '1';
    }, 350);
  }

  // Step 3 extras
  if (n === 3) {
    setTimeout(() => {
      ['lt','rt'].forEach((id, i) => {
        const p = document.getElementById(id);
        p.style.opacity = '1';
        p.style.animation = 'none';
        void p.offsetWidth;
        p.style.strokeDashoffset = 120;
        p.style.animation = `drawPath .55s ${.65 + i * .12}s ease forwards`;
      });
      setTimeout(() => {
        document.getElementById('pileg').style.opacity = '1';
        document.getElementById('symbadge').style.opacity = '1';
      }, 1000);
    }, 100);
  }

  // Update tabs
  document.querySelectorAll('.step-tab').forEach((b, i) =>
    b.classList.toggle('active', i === n));

  // Update dots
  document.querySelectorAll('.pdot').forEach((d, i) =>
    d.classList.toggle('active', i === n));

  // Update buttons
  document.getElementById('prevbtn').disabled = n === 0;
  document.getElementById('nextbtn').disabled = n === STEPS.length - 1;

  // Update description
  const descEl = document.getElementById('desctext');
  descEl.parentElement.style.animation = 'none';
  void descEl.parentElement.offsetWidth;
  descEl.parentElement.style.animation = 'fadeUp .4s ease forwards';
  descEl.innerHTML = STEPS[n].desc;
}

function next() { if (cur < STEPS.length - 1) goTo(cur + 1); }
function prev() { if (cur > 0) goTo(cur - 1); }

// Keyboard navigation
document.addEventListener('keydown', e => {
  if (e.key === 'ArrowRight') next();
  if (e.key === 'ArrowLeft')  prev();
});

// Init
goTo(0);
</script>

</body>
</html>
