<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RugVision — See It Before You Buy It</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --accent: #c0392b;
      --accent2: #e67e22;
      --bg: #0a0a0a;
      --panel: #141414;
      --border: rgba(255,255,255,0.08);
      --text: #f0ede8;
      --muted: #888;
      --gold: #c9a84c;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--bg);
      color: var(--text);
      overflow-x: hidden;
    }

    /* ─── NAV ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 900;
      display: flex; align-items: center; justify-content: space-between;
      padding: 20px 48px;
      background: linear-gradient(to bottom, rgba(0,0,0,0.7), transparent);
    }
    .logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 26px; font-weight: 300; letter-spacing: 4px;
      color: var(--gold); text-decoration: none;
    }
    .logo span { color: var(--text); }
    .nav-cta {
      padding: 10px 24px;
      background: var(--accent);
      color: white; border: none; border-radius: 3px;
      font-family: 'DM Sans', sans-serif; font-size: 13px;
      letter-spacing: 1px; cursor: pointer; transition: 0.2s;
      text-transform: uppercase;
    }
    .nav-cta:hover { background: #e74c3c; }

    /* ─── HERO / VIDEO ─── */
    .hero {
      position: relative; width: 100%; height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      overflow: hidden;
    }

    .video-bg {
      position: absolute; inset: 0;
      background: linear-gradient(135deg, #1a0a00 0%, #0a0a0a 40%, #0d0d1a 100%);
    }

    /* Animated rug pattern background */
    .video-bg::before {
      content: '';
      position: absolute; inset: 0;
      background-image:
        repeating-linear-gradient(45deg, rgba(192,57,43,0.03) 0px, rgba(192,57,43,0.03) 1px, transparent 1px, transparent 40px),
        repeating-linear-gradient(-45deg, rgba(201,168,76,0.03) 0px, rgba(201,168,76,0.03) 1px, transparent 1px, transparent 40px);
      animation: patternDrift 20s linear infinite;
    }
    @keyframes patternDrift { from { background-position: 0 0; } to { background-position: 80px 80px; } }

    .video-bg::after {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 80% 60% at 50% 50%, rgba(192,57,43,0.08) 0%, transparent 70%);
    }

    /* Fake video player */
    .video-player {
      position: relative; z-index: 2;
      width: min(860px, 90vw);
      border-radius: 6px;
      overflow: hidden;
      border: 1px solid rgba(201,168,76,0.2);
      box-shadow: 0 40px 120px rgba(0,0,0,0.8), 0 0 0 1px rgba(255,255,255,0.04);
    }

    .video-screen {
      position: relative;
      background: #0d0d0d;
      aspect-ratio: 16/9;
      display: flex; align-items: center; justify-content: center;
      cursor: pointer;
      overflow: hidden;
    }

    /* Rug mockup inside video */
    .video-room-art {
      width: 100%; height: 100%;
      background: linear-gradient(180deg, #1a1208 0%, #2d1f0e 40%, #3d2810 70%, #1a1208 100%);
      display: flex; align-items: flex-end; justify-content: center;
      padding-bottom: 12%;
    }
    .vr-floor {
      width: 80%; height: 40%;
      background: linear-gradient(180deg, #5c3a1e 0%, #3d2810 100%);
      border-radius: 2px;
      transform: perspective(400px) rotateX(30deg);
      position: relative;
    }
    .vr-rug {
      position: absolute;
      width: 60%; height: 65%;
      left: 50%; top: 20%;
      transform: translateX(-50%);
      background: linear-gradient(135deg, #8b1a1a 0%, #c0392b 25%, #8b1a1a 50%, #c0392b 75%, #8b1a1a 100%);
      border-radius: 3px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.5);
    }
    .vr-rug::before {
      content: '';
      position: absolute; inset: 6px;
      border: 2px solid rgba(201,168,76,0.4);
      border-radius: 2px;
    }
    .vr-rug::after {
      content: '';
      position: absolute; inset: 14px;
      background: repeating-linear-gradient(45deg, rgba(0,0,0,0.1) 0px, rgba(0,0,0,0.1) 2px, transparent 2px, transparent 8px);
    }
    .vr-sofa {
      position: absolute;
      width: 70%; height: 35%;
      left: 15%; bottom: 70%;
      background: linear-gradient(180deg, #2c2c2c 0%, #1a1a1a 100%);
      border-radius: 6px 6px 0 0;
    }

    .play-btn {
      position: absolute; z-index: 5;
      width: 72px; height: 72px;
      background: rgba(192,57,43,0.9);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      border: 2px solid rgba(255,255,255,0.2);
      transition: 0.3s; cursor: pointer;
    }
    .play-btn:hover { background: var(--accent); transform: scale(1.08); }
    .play-btn svg { width: 28px; height: 28px; fill: white; margin-left: 4px; }

    .video-label {
      position: absolute; bottom: 16px; left: 16px;
      font-size: 11px; letter-spacing: 2px; text-transform: uppercase;
      color: rgba(255,255,255,0.4); font-family: 'DM Sans';
    }

    /* Video controls bar */
    .video-bar {
      background: #111;
      padding: 12px 16px;
      display: flex; align-items: center; gap: 12px;
      border-top: 1px solid rgba(255,255,255,0.05);
    }
    .vb-btn { background: none; border: none; color: #666; cursor: pointer; font-size: 14px; transition: 0.2s; padding: 4px; }
    .vb-btn:hover { color: var(--gold); }
    .vb-progress { flex: 1; height: 3px; background: #2a2a2a; border-radius: 2px; cursor: pointer; }
    .vb-fill { width: 0%; height: 100%; background: var(--accent); border-radius: 2px; transition: width 0.1s; }
    .vb-time { font-size: 11px; color: #555; font-variant-numeric: tabular-nums; }

    /* ── POPUP TRIGGER STRIP (below video) ── */
    .popup-strip {
      position: relative; z-index: 2;
      width: min(860px, 90vw);
      margin-top: 0;
      background: linear-gradient(90deg, rgba(192,57,43,0.15), rgba(201,168,76,0.1), rgba(192,57,43,0.15));
      border: 1px solid rgba(192,57,43,0.35);
      border-top: none;
      border-radius: 0 0 6px 6px;
      padding: 18px 32px;
      display: flex; align-items: center; justify-content: space-between;
      gap: 20px;
      backdrop-filter: blur(4px);
    }

    .strip-text { font-size: 14px; color: rgba(255,255,255,0.75); }
    .strip-text strong { color: var(--gold); font-weight: 500; }

    .strip-cta {
      display: flex; align-items: center; gap: 10px;
      padding: 12px 28px;
      background: var(--accent);
      color: white; border: none; border-radius: 4px;
      font-family: 'DM Sans', sans-serif; font-size: 14px; font-weight: 500;
      cursor: pointer; transition: 0.25s; white-space: nowrap;
      letter-spacing: 0.3px;
    }
    .strip-cta:hover { background: #e74c3c; transform: translateY(-1px); }
    .strip-cta svg { width: 18px; height: 18px; fill: white; flex-shrink: 0; }

    /* ─── HERO COPY ─── */
    .hero-copy {
      position: relative; z-index: 2;
      text-align: center;
      margin-bottom: 36px;
    }
    .hero-tag {
      display: inline-block;
      font-size: 11px; letter-spacing: 4px; text-transform: uppercase;
      color: var(--gold); margin-bottom: 20px;
      border: 1px solid rgba(201,168,76,0.3);
      padding: 6px 16px; border-radius: 20px;
    }
    .hero-title {
      font-family: 'Cormorant Garamond', serif;
      font-size: clamp(42px, 6vw, 80px);
      font-weight: 300; line-height: 1.1;
      margin-bottom: 20px;
      letter-spacing: -1px;
    }
    .hero-title em { color: var(--gold); font-style: italic; }
    .hero-sub {
      font-size: 16px; color: var(--muted);
      max-width: 480px; margin: 0 auto;
      line-height: 1.7;
    }

    /* ─── FEATURES STRIP ─── */
    .features {
      padding: 100px 48px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 2px;
      background: var(--border);
      border-top: 1px solid var(--border);
    }
    .feat {
      background: var(--bg);
      padding: 48px 36px;
      position: relative;
    }
    .feat-num {
      font-family: 'Cormorant Garamond', serif;
      font-size: 64px; font-weight: 300;
      color: rgba(192,57,43,0.15);
      position: absolute; top: 24px; right: 24px;
      line-height: 1;
    }
    .feat-icon { font-size: 28px; margin-bottom: 20px; }
    .feat h3 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 22px; font-weight: 400; margin-bottom: 10px;
    }
    .feat p { font-size: 14px; color: var(--muted); line-height: 1.7; }

    /* ─── UPLOAD POPUP OVERLAY ─── */
    #popup-overlay {
      display: none;
      position: fixed; inset: 0; z-index: 1000;
      background: rgba(0,0,0,0.85);
      backdrop-filter: blur(8px);
      align-items: center; justify-content: center;
      animation: fadeIn 0.2s ease;
    }
    #popup-overlay.open { display: flex; }
    @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

    .popup-box {
      background: var(--panel);
      border: 1px solid rgba(201,168,76,0.2);
      border-radius: 8px;
      width: min(480px, 94vw);
      overflow: hidden;
      animation: slideUp 0.3s cubic-bezier(0.34,1.56,0.64,1);
      box-shadow: 0 60px 120px rgba(0,0,0,0.8);
    }
    @keyframes slideUp { from { opacity: 0; transform: translateY(30px) scale(0.96); } to { opacity: 1; transform: none; } }

    .popup-header {
      background: linear-gradient(135deg, #1a0800, #120d00);
      padding: 36px 36px 28px;
      border-bottom: 1px solid rgba(201,168,76,0.12);
      position: relative;
    }
    .popup-close {
      position: absolute; top: 16px; right: 16px;
      background: rgba(255,255,255,0.06); border: none;
      color: #888; width: 32px; height: 32px;
      border-radius: 50%; cursor: pointer; font-size: 16px;
      display: flex; align-items: center; justify-content: center;
      transition: 0.2s;
    }
    .popup-close:hover { background: rgba(255,255,255,0.12); color: white; }

    .popup-badge {
      display: inline-flex; align-items: center; gap: 6px;
      font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
      color: var(--gold); margin-bottom: 12px;
    }
    .popup-badge::before {
      content: '';
      width: 6px; height: 6px; background: var(--gold);
      border-radius: 50%; animation: pulse 2s infinite;
    }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }

    .popup-header h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 32px; font-weight: 300; line-height: 1.2;
      margin-bottom: 8px;
    }
    .popup-header p { font-size: 14px; color: var(--muted); line-height: 1.6; }

    .popup-body { padding: 32px 36px; }

    .upload-zone {
      border: 2px dashed rgba(201,168,76,0.25);
      border-radius: 6px;
      padding: 40px 20px;
      text-align: center;
      cursor: pointer;
      transition: 0.25s;
      background: rgba(255,255,255,0.01);
      position: relative;
    }
    .upload-zone:hover, .upload-zone.drag-over {
      border-color: var(--gold);
      background: rgba(201,168,76,0.04);
    }
    .upload-zone input {
      position: absolute; inset: 0; opacity: 0; cursor: pointer; width: 100%; height: 100%;
    }
    .upload-icon {
      width: 56px; height: 56px; margin: 0 auto 16px;
      background: rgba(192,57,43,0.12);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      border: 1px solid rgba(192,57,43,0.2);
    }
    .upload-icon svg { width: 24px; height: 24px; stroke: var(--accent); fill: none; stroke-width: 1.5; }
    .upload-zone h4 { font-size: 16px; font-weight: 400; margin-bottom: 6px; }
    .upload-zone p { font-size: 13px; color: var(--muted); }
    .upload-zone .formats { font-size: 11px; color: #555; margin-top: 10px; letter-spacing: 1px; text-transform: uppercase; }

    .popup-preview {
      display: none;
      margin-bottom: 20px;
      border-radius: 6px; overflow: hidden;
      border: 1px solid var(--border);
      position: relative;
    }
    .popup-preview img { width: 100%; max-height: 180px; object-fit: cover; display: block; }
    .preview-label {
      position: absolute; bottom: 10px; left: 10px;
      background: rgba(0,0,0,0.7); color: var(--gold);
      font-size: 11px; padding: 4px 10px; border-radius: 3px;
      letter-spacing: 1px; text-transform: uppercase;
    }
    .remove-btn {
      position: absolute; top: 8px; right: 8px;
      background: rgba(192,57,43,0.8); border: none;
      color: white; width: 28px; height: 28px;
      border-radius: 50%; cursor: pointer; font-size: 14px;
      display: flex; align-items: center; justify-content: center;
    }

    .popup-launch {
      width: 100%; padding: 16px;
      background: var(--accent);
      color: white; border: none; border-radius: 5px;
      font-family: 'DM Sans', sans-serif; font-size: 15px; font-weight: 500;
      cursor: pointer; transition: 0.25s; margin-top: 16px;
      display: flex; align-items: center; justify-content: center; gap: 10px;
      letter-spacing: 0.3px;
    }
    .popup-launch:hover { background: #e74c3c; transform: translateY(-1px); }
    .popup-launch:disabled { background: #333; color: #666; cursor: default; transform: none; }
    .popup-launch svg { width: 18px; height: 18px; fill: white; }

    .popup-note { font-size: 12px; color: #555; text-align: center; margin-top: 12px; line-height: 1.6; }

    /* ─── STUDIO PAGE ─── */
    #studio-page {
      display: none;
      position: fixed; inset: 0; z-index: 800;
      background: var(--bg);
      animation: fadeIn 0.3s ease;
    }

    .studio-nav {
      height: 50px;
      background: #0d0d0d;
      border-bottom: 1px solid rgba(255,255,255,0.06);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 20px;
      flex-shrink: 0;
    }
    .studio-logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 18px; color: var(--gold); letter-spacing: 3px;
    }
    .studio-back {
      background: none; border: 1px solid rgba(255,255,255,0.1);
      color: #888; padding: 6px 14px; border-radius: 3px;
      cursor: pointer; font-size: 12px; letter-spacing: 1px;
      text-transform: uppercase; transition: 0.2s;
    }
    .studio-back:hover { color: white; border-color: rgba(255,255,255,0.3); }

    .studio-body {
      display: flex;
      height: calc(100vh - 50px);
      overflow: hidden;
    }

    /* ── STUDIO SIDEBAR ── */
    .sidebar {
      width: 310px; min-width: 310px;
      background: #141414;
      padding: 20px;
      overflow-y: auto;
      border-right: 1px solid rgba(255,255,255,0.06);
    }
    .sidebar h2 {
      font-family: 'Cormorant Garamond', serif;
      font-size: 13px; letter-spacing: 3px; text-transform: uppercase;
      color: var(--gold); font-weight: 400;
      margin-bottom: 20px; padding-bottom: 12px;
      border-bottom: 1px solid rgba(255,255,255,0.06);
    }
    .input-box { margin-bottom: 14px; }
    label {
      display: block; font-size: 10px; text-transform: uppercase;
      margin-bottom: 5px; color: #666; letter-spacing: 1.5px;
    }
    select, input[type="file"] {
      width: 100%; padding: 10px 12px;
      background: #1e1e1e; border: 1px solid rgba(255,255,255,0.08);
      color: var(--text); border-radius: 4px; font-size: 13px;
      font-family: 'DM Sans', sans-serif;
    }
    select:focus { outline: none; border-color: var(--accent); }

    .btn-main {
      width: 100%; padding: 13px;
      background: var(--accent); color: white;
      border: none; border-radius: 4px; cursor: pointer;
      font-family: 'DM Sans', sans-serif; font-size: 13px;
      font-weight: 500; letter-spacing: 0.5px; transition: 0.2s; margin-top: 8px;
    }
    .btn-main:hover { background: #e74c3c; }

    .mode-toggle { display: flex; gap: 6px; margin-bottom: 14px; }
    .mode-btn {
      flex: 1; padding: 8px;
      background: #1e1e1e; border: 1px solid rgba(255,255,255,0.08);
      color: #777; border-radius: 4px; cursor: pointer;
      font-size: 11px; font-family: 'DM Sans'; transition: 0.2s;
    }
    .mode-btn.active { background: var(--accent); color: white; border-color: var(--accent); }

    .adjustment-panel {
      margin-top: 16px; background: #1a1a1a;
      padding: 14px; border-radius: 6px;
      border: 1px solid rgba(255,255,255,0.06);
    }
    .panel-title {
      font-size: 10px; text-transform: uppercase; letter-spacing: 2px;
      color: var(--gold); margin-bottom: 14px; font-weight: 400;
    }
    .slider-label {
      display: flex; justify-content: space-between;
      font-size: 11px; margin-bottom: 4px; color: #888;
    }
    .slider-label span:last-child { color: var(--text); font-variant-numeric: tabular-nums; }
    input[type="range"] {
      width: 100%; margin-bottom: 12px; cursor: pointer;
      accent-color: var(--accent); height: auto;
      background: none; border: none; padding: 0;
    }

    /* ── STUDIO MAIN VIEW ── */
    .main-view {
      flex: 1; background: #000;
      display: flex; align-items: center; justify-content: center;
      padding: 24px; position: relative;
    }
    #room-container {
      position: relative; display: inline-block;
      border-radius: 6px; overflow: hidden;
      max-width: 100%; max-height: 100%;
    }
    #room-img {
      max-width: 100%; max-height: calc(100vh - 100px);
      display: block; border-radius: 6px;
    }
    #rug-obj {
      position: absolute; z-index: 100;
      cursor: move; transform-origin: center bottom;
      touch-action: none; image-rendering: high-quality;
    }
    .rug-shadow {
      position: absolute; z-index: 99;
      pointer-events: none; border-radius: 50%;
      background: radial-gradient(ellipse, rgba(0,0,0,0.5) 0%, transparent 70%);
    }
    .floor-guide {
      position: absolute; bottom: 20%; left: 8%; right: 8%;
      height: 1px; border-top: 1px dashed rgba(201,168,76,0.4);
      pointer-events: none; z-index: 50; display: none;
    }
    .floor-guide::before {
      content: 'Floor Line';
      position: absolute; top: -16px; left: 50%;
      transform: translateX(-50%);
      font-size: 10px; color: rgba(201,168,76,0.6);
      white-space: nowrap; letter-spacing: 1px; text-transform: uppercase;
    }
    #loading {
      position: absolute; background: rgba(0,0,0,0.9);
      padding: 18px 28px; border-radius: 6px; display: none;
      z-index: 200; border: 1px solid rgba(192,57,43,0.4);
      color: var(--gold); font-size: 13px; letter-spacing: 1px;
      text-transform: uppercase;
    }

    /* ─── SCROLLING MARQUEE ─── */
    .marquee-wrap {
      overflow: hidden; border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      background: #0d0d0d; padding: 14px 0;
    }
    .marquee-inner {
      display: flex; gap: 0; white-space: nowrap;
      animation: marquee 25s linear infinite;
    }
    .marquee-item {
      font-size: 12px; letter-spacing: 3px; text-transform: uppercase;
      color: #444; padding: 0 40px;
    }
    .marquee-item span { color: var(--gold); margin-right: 40px; }
    @keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }
  </style>
</head>
<body>

<!-- ═══════════ LANDING PAGE ═══════════ -->
<div id="landing-page">

  <!-- Nav -->
  <nav>
    <a class="logo" href="#">RUG<span>VISION</span></a>
    <button class="nav-cta" onclick="openPopup()">Try Free Now</button>
  </nav>

  <!-- Hero -->
  <section class="hero">
    <div class="video-bg"></div>

    <div class="hero-copy">
      <div class="hero-tag">AI-Powered Rug Visualizer</div>
      <h1 class="hero-title">See Your Rug<br>in <em>Any Room</em></h1>
      <p class="hero-sub">Upload your product photo, pick a room, and watch it come to life — before a single order is placed.</p>
    </div>

    <!-- Video Player -->
    <div class="video-player">
      <div class="video-screen" onclick="openPopup()">
        <div class="video-room-art">
          <div class="vr-floor">
            <div class="vr-sofa"></div>
            <div class="vr-rug"></div>
          </div>
        </div>
        <div class="play-btn">
          <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>
        </div>
        <div class="video-label">RugVision Studio — Demo</div>
      </div>

      <!-- Video controls (decorative) -->
      <div class="video-bar">
        <button class="vb-btn">▶</button>
        <div class="vb-progress" id="vb-progress">
          <div class="vb-fill" id="vb-fill"></div>
        </div>
        <span class="vb-time" id="vb-time">0:00 / 2:34</span>
        <button class="vb-btn">🔊</button>
        <button class="vb-btn">⛶</button>
      </div>
    </div>

    <!-- Popup trigger strip — directly under video -->
    <div class="popup-strip">
      <p class="strip-text">
        <strong>Ready to visualize your own rug?</strong><br>
        Upload a product photo and see it in a real room in seconds.
      </p>
      <button class="strip-cta" onclick="openPopup()">
        <svg viewBox="0 0 24 24"><path d="M14 2H6c-1.1 0-2 .9-2 2v16c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V8l-6-6zm-1 7V3.5L18.5 9H13z"/></svg>
        Upload Your Rug
      </button>
    </div>

  </section>

  <!-- Marquee -->
  <div class="marquee-wrap">
    <div class="marquee-inner">
      <div class="marquee-item"><span>✦</span> AI Room Generator</div>
      <div class="marquee-item"><span>✦</span> Real-Time Perspective Fit</div>
      <div class="marquee-item"><span>✦</span> Runner &amp; Area Rug Modes</div>
      <div class="marquee-item"><span>✦</span> Drag &amp; Drop Placement</div>
      <div class="marquee-item"><span>✦</span> Multiple Room Types</div>
      <div class="marquee-item"><span>✦</span> AI Room Generator</div>
      <div class="marquee-item"><span>✦</span> Real-Time Perspective Fit</div>
      <div class="marquee-item"><span>✦</span> Runner &amp; Area Rug Modes</div>
      <div class="marquee-item"><span>✦</span> Drag &amp; Drop Placement</div>
      <div class="marquee-item"><span>✦</span> Multiple Room Types</div>
    </div>
  </div>

  <!-- Features -->
  <section class="features">
    <div class="feat">
      <div class="feat-num">01</div>
      <div class="feat-icon">🖼</div>
      <h3>AI Room Generation</h3>
      <p>Generate photorealistic rooms matching your style preferences — from luxury hallways to minimalist bedrooms.</p>
    </div>
    <div class="feat">
      <div class="feat-num">02</div>
      <div class="feat-icon">📐</div>
      <h3>Floor Perspective Fit</h3>
      <p>Smart tilt, scale and shadow controls let you lock your rug flat to the floor with pixel precision.</p>
    </div>
    <div class="feat">
      <div class="feat-num">03</div>
      <div class="feat-icon">↕</div>
      <h3>Runner Mode</h3>
      <p>Dedicated yolluk/runner mode automatically applies the correct narrow portrait aspect ratio for hallway rugs.</p>
    </div>
    <div class="feat">
      <div class="feat-num">04</div>
      <div class="feat-icon">✦</div>
      <h3>Instant &amp; Free</h3>
      <p>No login, no account. Upload, configure, visualize. Share the result with your customer in one click.</p>
    </div>
  </section>

</div><!-- /landing -->


<!-- ═══════════ UPLOAD POPUP ═══════════ -->
<div id="popup-overlay" role="dialog" aria-modal="true" aria-label="Upload your rug" onclick="handleOverlayClick(event)">
  <div class="popup-box">

    <div class="popup-header">
      <button class="popup-close" onclick="closePopup()" aria-label="Close">✕</button>
      <div class="popup-badge">Step 1 of 2</div>
      <h2>Upload Your Rug Photo</h2>
      <p>Choose a clear product image — transparent background works best, but any photo will do.</p>
    </div>

    <div class="popup-body">

      <!-- Preview (hidden until file chosen) -->
      <div class="popup-preview" id="popup-preview">
        <img id="preview-img" src="" alt="Rug preview">
        <div class="preview-label">Your Rug</div>
        <button class="remove-btn" onclick="removeFile()" title="Remove">✕</button>
      </div>

      <!-- Drop zone -->
      <div class="upload-zone" id="upload-zone">
        <input type="file" id="popup-file" accept="image/*" onchange="handlePopupFile(event)">
        <div class="upload-icon">
          <svg viewBox="0 0 24 24"><path d="M21 15v4a2 2 0 01-2 2H5a2 2 0 01-2-2v-4M17 8l-5-5-5 5M12 3v12"/></svg>
        </div>
        <h4>Drop your rug image here</h4>
        <p>or click to browse files</p>
        <div class="formats">JPG · PNG · WEBP · up to 20MB</div>
      </div>

      <button class="popup-launch" id="popup-launch-btn" disabled onclick="launchStudio()">
        <svg viewBox="0 0 24 24"><path d="M5 3l14 9-14 9V3z"/></svg>
        Open in Studio
      </button>

      <p class="popup-note">Your image is processed locally in the browser — never uploaded to any server.</p>

    </div>
  </div>
</div>


<!-- ═══════════ STUDIO PAGE ═══════════ -->
<div id="studio-page">

  <div class="studio-nav">
    <span class="studio-logo">RUGVISION STUDIO</span>
    <button class="studio-back" onclick="backToLanding()">← Back to Home</button>
  </div>

  <div class="studio-body">

    <div class="sidebar">
      <h2>Studio Config</h2>

      <div class="input-box">
        <label>Room Type</label>
        <select id="roomType">
          <option value="luxury entrance hallway">Entrance Hallway</option>
          <option value="modern spacious living room" selected>Living Room</option>
          <option value="minimalist master bedroom">Bedroom</option>
          <option value="modern dining room">Dining Room</option>
        </select>
      </div>

      <div class="input-box">
        <label>Furniture Color</label>
        <select id="sofaColor">
          <option value="Cream linen">Cream / Beige</option>
          <option value="Grey modern">Grey</option>
          <option value="Anthracite dark grey">Anthracite</option>
          <option value="Navy blue velvet">Navy Blue</option>
          <option value="Emerald green velvet">Emerald Green</option>
          <option value="Mustard yellow fabric">Mustard Yellow</option>
          <option value="Cognac leather">Cognac Leather</option>
          <option value="Terracotta warm">Terracotta</option>
          <option value="Pure white minimalist">White</option>
        </select>
      </div>

      <div class="input-box">
        <label>Room Size</label>
        <select id="roomSize">
          <option value="15">Small — 15 m²</option>
          <option value="25" selected>Medium — 25 m²</option>
          <option value="40">Large — 40 m²</option>
          <option value="60">Very Large — 60 m²</option>
        </select>
      </div>

      <div class="input-box">
        <label>Rug Type</label>
        <div class="mode-toggle">
          <button class="mode-btn active" id="btn-normal" onclick="setRugMode('normal')">▪ Area Rug</button>
          <button class="mode-btn" id="btn-runner" onclick="setRugMode('runner')">▬ Runner</button>
        </div>
      </div>

      <div class="input-box">
        <label>Replace Rug Image</label>
        <input type="file" id="rugFile" accept="image/*" onchange="loadRug(event)">
      </div>

      <button class="btn-main" onclick="generateRoom()">Generate AI Room</button>

      <div class="adjustment-panel">
        <div class="panel-title">Floor Placement Controls</div>

        <div class="slider-label"><span>Scale</span><span id="val-scale">1.00</span></div>
        <input type="range" id="scale" min="0.1" max="3.0" step="0.05" value="1" oninput="updateRug()">

        <div class="slider-label"><span>Floor Tilt</span><span id="val-tilt">62°</span></div>
        <input type="range" id="tilt" min="45" max="85" step="1" value="62" oninput="updateRug()">

        <div class="slider-label"><span>Rotation</span><span id="val-rotate">0°</span></div>
        <input type="range" id="rotate" min="-45" max="45" step="1" value="0" oninput="updateRug()">

        <div id="runner-controls" style="display:none;">
          <div class="slider-label"><span>Runner Length</span><span id="val-length">3.0×</span></div>
          <input type="range" id="runnerLength" min="1.5" max="6" step="0.1" value="3" oninput="updateRug()">
        </div>

        <div class="slider-label"><span>Shadow</span><span id="val-shadow">50</span></div>
        <input type="range" id="shadowStr" min="0" max="100" step="5" value="50" oninput="updateRug()">

        <button class="mode-btn" onclick="toggleGuide()" style="width:100%; margin-top:4px; font-size:11px;">
          Toggle Floor Guide
        </button>
      </div>
    </div>

    <div class="main-view">
      <div id="loading">Generating your room…</div>
      <div id="room-container">
        <img id="room-img" src="https://via.placeholder.com/1280x800/111/222?text=Click+%22Generate+AI+Room%22+to+begin" alt="Room preview">
        <div id="rug-shadow" class="rug-shadow"></div>
        <div class="floor-guide" id="floor-guide"></div>
        <img id="rug-obj" src="" alt="Your rug" style="display:none;">
      </div>
    </div>

  </div>
</div><!-- /studio-page -->


<script>
  /* ── DECORATIVE VIDEO PROGRESS ── */
  let vbPct = 0;
  const fill = document.getElementById('vb-fill');
  const timeEl = document.getElementById('vb-time');
  setInterval(() => {
    vbPct = (vbPct + 0.07) % 100;
    if(fill) fill.style.width = vbPct + '%';
    const total = 154, current = Math.floor(total * vbPct / 100);
    const m = Math.floor(current/60), s = current%60;
    if(timeEl) timeEl.textContent = `${m}:${s.toString().padStart(2,'0')} / 2:34`;
  }, 100);

  /* ── POPUP ── */
  let pendingRugSrc = null;

  function openPopup() {
    document.getElementById('popup-overlay').classList.add('open');
    document.body.style.overflow = 'hidden';
  }
  function closePopup() {
    document.getElementById('popup-overlay').classList.remove('open');
    document.body.style.overflow = '';
  }
  function handleOverlayClick(e) {
    if(e.target === document.getElementById('popup-overlay')) closePopup();
  }

  function handlePopupFile(e) {
    const file = e.target.files[0];
    if(!file) return;
    const url = URL.createObjectURL(file);
    pendingRugSrc = url;

    const preview = document.getElementById('popup-preview');
    const previewImg = document.getElementById('preview-img');
    previewImg.src = url;
    preview.style.display = 'block';
    document.getElementById('upload-zone').style.display = 'none';
    document.getElementById('popup-launch-btn').disabled = false;
  }

  function removeFile() {
    pendingRugSrc = null;
    document.getElementById('popup-preview').style.display = 'none';
    document.getElementById('upload-zone').style.display = 'block';
    document.getElementById('popup-launch-btn').disabled = true;
    document.getElementById('popup-file').value = '';
  }

  function launchStudio() {
    if(!pendingRugSrc) return;
    closePopup();
    document.getElementById('landing-page').style.display = 'none';
    document.getElementById('studio-page').style.display = 'block';

    // Pre-load the rug into the studio
    const rugImg = new Image();
    rugImg.onload = () => {
      rugNaturalW = rugImg.naturalWidth;
      rugNaturalH = rugImg.naturalHeight;
      const rugEl = document.getElementById('rug-obj');
      rugEl.src = pendingRugSrc;
      rugEl.style.display = 'block';
      rugPosX = 50; rugPosY = 75;
      updateRug();
      generateRoom(); // auto-generate room on launch
    };
    rugImg.src = pendingRugSrc;
  }

  function backToLanding() {
    document.getElementById('studio-page').style.display = 'none';
    document.getElementById('landing-page').style.display = 'block';
    document.body.style.overflow = '';
  }

  /* ── DRAG & DROP on upload zone ── */
  const zone = document.getElementById('upload-zone');
  zone.addEventListener('dragover', e => { e.preventDefault(); zone.classList.add('drag-over'); });
  zone.addEventListener('dragleave', () => zone.classList.remove('drag-over'));
  zone.addEventListener('drop', e => {
    e.preventDefault(); zone.classList.remove('drag-over');
    const file = e.dataTransfer.files[0];
    if(file && file.type.startsWith('image/')) {
      const dt = new DataTransfer(); dt.items.add(file);
      document.getElementById('popup-file').files = dt.files;
      handlePopupFile({ target: { files: dt.files } });
    }
  });

  /* ── STUDIO LOGIC ── */
  let rugMode = 'normal';
  let rugNaturalW = 1, rugNaturalH = 1;
  let rugPosX = 50, rugPosY = 75;

  function setRugMode(mode) {
    rugMode = mode;
    document.getElementById('btn-normal').classList.toggle('active', mode === 'normal');
    document.getElementById('btn-runner').classList.toggle('active', mode === 'runner');
    document.getElementById('runner-controls').style.display = mode === 'runner' ? 'block' : 'none';
    updateRug();
  }

  function generateRoom() {
    const type = document.getElementById('roomType').value;
    const sofa = document.getElementById('sofaColor').value;
    const size = document.getElementById('roomSize').value;
    const loading = document.getElementById('loading');
    const roomImg = document.getElementById('room-img');
    loading.style.display = 'block';
    roomImg.style.opacity = '0.15';
    const prompt = `A professional interior shot of a ${size} square meter ${type}. Premium ${sofa} sofa and furniture. Wide completely empty wooden floor in foreground. Bright natural lighting, cinematic photography, 8k, photorealistic.`;
    const seed = Math.floor(Math.random() * 100000);
    roomImg.onload = () => { loading.style.display = 'none'; roomImg.style.opacity = '1'; };
    roomImg.src = `https://image.pollinations.ai/prompt/${encodeURIComponent(prompt)}?width=1280&height=800&nologo=true&seed=${seed}&model=flux`;
  }

  function loadRug(event) {
    const file = event.target.files[0];
    if(!file) return;
    const img = new Image();
    img.onload = () => {
      rugNaturalW = img.naturalWidth; rugNaturalH = img.naturalHeight;
      const rugEl = document.getElementById('rug-obj');
      rugEl.src = img.src; rugEl.style.display = 'block';
      rugPosX = 50; rugPosY = 75; updateRug();
    };
    img.src = URL.createObjectURL(file);
  }

  function updateRug() {
    const rug = document.getElementById('rug-obj');
    const shadow = document.getElementById('rug-shadow');
    if(!rug.src || rug.style.display === 'none') return;

    const scale = parseFloat(document.getElementById('scale').value);
    const tilt = parseInt(document.getElementById('tilt').value);
    const rotate = parseInt(document.getElementById('rotate').value);
    const shadowStr = parseInt(document.getElementById('shadowStr').value) / 100;

    document.getElementById('val-scale').innerText = scale.toFixed(2);
    document.getElementById('val-tilt').innerText = tilt + '°';
    document.getElementById('val-rotate').innerText = rotate + '°';
    document.getElementById('val-shadow').innerText = Math.round(shadowStr * 100);

    const container = document.getElementById('room-container');
    const cw = container.offsetWidth || 800;
    let baseWidth = cw * 0.28 * scale;
    let aspectRatio = rugNaturalH / rugNaturalW;

    if(rugMode === 'runner') {
      const lm = parseFloat(document.getElementById('runnerLength').value);
      document.getElementById('val-length').innerText = lm.toFixed(1) + '×';
      baseWidth = cw * 0.12 * scale;
      aspectRatio = lm * (rugNaturalH / rugNaturalW);
    }

    const baseHeight = baseWidth * aspectRatio;
    const tiltRad = tilt * Math.PI / 180;
    const perspScaleY = Math.cos(tiltRad);

    rug.style.width = baseWidth + 'px';
    rug.style.height = baseHeight + 'px';
    rug.style.left = rugPosX + '%';
    rug.style.top = rugPosY + '%';
    rug.style.transformOrigin = 'center bottom';
    rug.style.transform = `translate(-50%,-100%) perspective(1400px) rotateX(${tilt}deg) rotateZ(${rotate}deg)`;

    const sw = baseWidth * 1.2, sh = (baseHeight * perspScaleY) * 0.4;
    shadow.style.width = sw + 'px'; shadow.style.height = sh + 'px';
    shadow.style.left = rugPosX + '%'; shadow.style.top = rugPosY + '%';
    shadow.style.transform = `translate(-50%, -${sh*0.2}px) rotateZ(${rotate}deg)`;
    shadow.style.opacity = shadowStr * 0.6;
    shadow.style.display = 'block';
  }

  function toggleGuide() {
    const g = document.getElementById('floor-guide');
    g.style.display = g.style.display === 'block' ? 'none' : 'block';
  }

  const rugEl = document.getElementById('rug-obj');
  let isDragging = false;
  function startDrag(e) { isDragging = true; e.preventDefault(); }
  function endDrag() { isDragging = false; }
  function move(e) {
    if(!isDragging) return;
    const c = document.getElementById('room-container').getBoundingClientRect();
    const cx = e.touches ? e.touches[0].clientX : e.clientX;
    const cy = e.touches ? e.touches[0].clientY : e.clientY;
    rugPosX = Math.max(5, Math.min(95, ((cx - c.left) / c.width) * 100));
    rugPosY = Math.max(10, Math.min(98, ((cy - c.top) / c.height) * 100));
    rugEl.style.left = rugPosX + '%'; rugEl.style.top = rugPosY + '%';
    const sh = document.getElementById('rug-shadow');
    sh.style.left = rugPosX + '%'; sh.style.top = rugPosY + '%';
  }
  rugEl.addEventListener('mousedown', startDrag);
  window.addEventListener('mousemove', move);
  window.addEventListener('mouseup', endDrag);
  rugEl.addEventListener('touchstart', startDrag, {passive:false});
  window.addEventListener('touchmove', move, {passive:false});
  window.addEventListener('touchend', endDrag);
</script>

</body>
</html>