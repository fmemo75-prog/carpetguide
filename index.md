<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
    <title>RugVision — Global Carpet Guide & AI Studio</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        /* ── TEMEL AYARLAR ── */
        :root {
            --accent: #c0392b; --accent2: #e67e22; --bg: #faf8f5;
            --panel: #141414; --text: #2c2c2c; --gold: #c9a84c;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); overflow-x: hidden; }
        a { text-decoration: none; transition: 0.3s; }

        /* ── KİŞİSEL HERO (ÜST KISIM) ── */
        .personal-hero {
            background: linear-gradient(135deg, #1a0a0a 0%, #3d0000 45%, #6b0f0f 100%);
            padding: 60px 20px; border-radius: 0 0 30px 30px; color: white; text-align: center;
        }
        .avatar { width: 100px; height: 100px; border-radius: 50%; border: 3px solid var(--gold); object-fit: cover; margin-bottom: 20px; box-shadow: 0 5px 15px rgba(0,0,0,0.5); }
        .personal-hero h1 { font-family: 'Cormorant Garamond', serif; font-size: 32px; margin-bottom: 10px; }
        .personal-hero h1 span { color: var(--gold); display: block; font-size: 18px; margin-top: 5px; }
        .personal-hero p { color: rgba(255,255,255,0.8); max-width: 600px; margin: 0 auto 25px; line-height: 1.6; }
        
        .nav-btns { display: flex; justify-content: center; gap: 15px; flex-wrap: wrap; }
        .btn { padding: 12px 25px; border-radius: 50px; font-weight: bold; font-size: 14px; cursor: pointer; }
        .btn-gold { background: var(--gold); color: #1a0a0a; border: none; }
        .btn-outline { background: transparent; color: white; border: 1.5px solid rgba(255,255,255,0.5); }

        /* ── RUGVISION TANITIM (VİDEO ALTI BUTON) ── */
        .ai-banner { padding: 80px 20px; text-align: center; background: #0a0a0a; color: white; margin: 40px 0; border-radius: 20px; }
        .ai-banner h2 { font-family: 'Cormorant Garamond', serif; font-size: 48px; margin-bottom: 20px; }
        .ai-banner h2 em { color: var(--gold); font-style: italic; }
        .btn-launch { 
            background: var(--accent); color: white; padding: 20px 50px; border-radius: 5px; 
            font-size: 18px; font-weight: bold; border: none; cursor: pointer; display: inline-block;
        }
        .btn-launch:hover { transform: scale(1.05); background: #e74c3c; }

        /* ── KARTLAR VE İÇERİK ── */
        .sec-label { text-align: center; padding: 40px 20px; }
        .sec-label h2 { font-family: 'Cormorant Garamond', serif; font-size: 28px; color: #8b0000; }
        .card-grid { max-width: 1000px; margin: 0 auto; padding: 20px; display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; }
        .card { background: white; padding: 25px; border-radius: 15px; border: 1px solid #ede8df; transition: 0.3s; }
        .card:hover { transform: translateY(-50px); box-shadow: 0 10px 20px rgba(0,0,0,0.1); }
        .card h3 { font-size: 18px; margin: 10px 0; color: #333; }
        .card p { font-size: 13px; color: #777; line-height: 1.5; }

        /* ── STUDYOPAGE (TAM EKRAN PANEL) ── */
        #studio {
            display: none; position: fixed; inset: 0; z-index: 2000; background: #000;
            grid-template-columns: 320px 1fr; color: white;
        }
        .sidebar { background: #141414; padding: 25px; border-right: 1px solid #333; overflow-y: auto; }
        .main-view { position: relative; display: flex; align-items: center; justify-content: center; overflow: hidden; background: #000; }
        #room-img { max-width: 95%; max-height: 90vh; border-radius: 10px; }
        #rug-obj {
            position: absolute; width: 250px; z-index: 100; cursor: move;
            transform: translate(-50%, -50%) perspective(1200px) rotateX(60deg);
            filter: drop-shadow(0 15px 30px rgba(0,0,0,0.8));
            touch-action: none;
        }
        .controls { background: #1a1a1a; padding: 15px; border-radius: 10px; margin-top: 20px; }
        input[type="range"] { width: 100%; accent-color: var(--accent); margin: 10px 0; }
        .btn-exit { position: absolute; top: 20px; right: 20px; background: #333; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; }

        /* MOBİL UYUM */
        @media (max-width: 800px) {
            #studio { grid-template-columns: 1fr; }
            .sidebar { height: auto; position: absolute; bottom: 0; width: 100%; z-index: 1000; }
        }
    </style>
</head>
<body>

    <!-- ── ANA SAYFA İÇERİĞİ ── -->
    <div id="main-content">
        <!-- Kişisel Hero -->
        <div class="personal-hero">
            <img src="./carpet.jpeg" alt="Fatih Mehmet Canıtez" class="avatar">
            <h1>🧶 Global Carpet & Kilim Guide<span>by Fatih Mehmet Canıtez</span></h1>
            <p>French Language Educator · Expert Curator · 50 years of experience in the heart of Cappadocia, studying carpets, valleys, and culture.</p>
            <div class="nav-btns">
                <a href="./me" class="btn btn-gold">👤 Curator Profile</a>
                <a href="./Cappodoce" class="btn btn-outline">🌄 Cappadocia Guide</a>
            </div>
        </div>

        <!-- AI Studio Tanıtım -->
        <div class="ai-banner">
            <div style="color: var(--gold); letter-spacing: 4px; font-size: 12px; margin-bottom: 15px;">NEW AI FEATURE</div>
            <h2>See Your Rug <em>in Any Room</em></h2>
            <p style="color: #888; max-width: 600px; margin: 0 auto 30px;">Halılarınızı müşterinizin evinde hayal edin. Yapay zeka ile profesyonel sunum yapın.</p>
            <button class="btn-launch" onclick="toggleStudio(true)">START AI STUDIO NOW</button>
        </div>

        <!-- Kartlar -->
        <div class="sec-label">
            <h2>🏛️ Historical & Technical Deep-Dives</h2>
        </div>
        <div class="card-grid">
            <div class="card"><h3>🏰 Imperial Hereke</h3><p>The finest silk carpets ever woven for Ottoman palaces.</p></div>
            <div class="card"><h3>🏺 Pazyryk Analysis</h3><p>Exploring the world's oldest surviving 2,500-year-old carpet.</p></div>
            <div class="card"><h3>🌍 Carpet World</h3><p>Hand-knotted traditions from Anatolia to Central Asia.</p></div>
            <div class="card"><h3>📊 Techniques</h3><p>Wool, silk, dyes, and knot types explained in detail.</p></div>
        </div>
    </div>

    <!-- ── AI STUDIO PANELİ (GİZLİ BAŞLAR) ── -->
    <div id="studio">
        <button class="btn-exit" onclick="toggleStudio(false)">✕ EXIT STUDIO</button>
        
        <div class="sidebar">
            <h2 style="color:var(--gold); font-family: 'Cormorant Garamond';">Studio v2</h2>
            
            <div style="margin-bottom:20px;">
                <label style="font-size:10px; color:#666;">1. UPLOAD RUG PHOTO</label>
                <input type="file" accept="image/*" onchange="loadRug(event)" style="width:100%; padding:10px; background:#222; border:none; color:white; border-radius:5px;">
            </div>

            <div style="margin-bottom:20px;">
                <label style="font-size:10px; color:#666;">ROOM TYPE</label>
                <select id="roomType" style="width:100%; padding:10px; background:#222; color:white; border:none;">
                    <option value="modern spacious living room">Living Room (Salon)</option>
                    <option value="luxury entrance hallway">Entrance (Antre)</option>
                    <option value="minimalist bedroom">Bedroom (Yatak Odası)</option>
                </select>
            </div>

            <button class="btn-launch" style="width:100%; padding:12px; font-size:14px;" onclick="generateRoom()">2. GENERATE AI ROOM</button>

            <div class="controls">
                <label style="color:var(--gold); font-size:11px; font-weight:bold;">3. FLOOR ALIGNMENT</label>
                <div style="display:flex; justify-content:space-between; font-size:10px; margin-top:10px;"><span>Size</span><span id="v-scale">1.0</span></div>
                <input type="range" id="scale" min="0.1" max="2.5" step="0.05" value="1" oninput="updateRug()">
                
                <div style="display:flex; justify-content:space-between; font-size:10px;"><span>Floor Tilt</span><span id="v-tilt">60°</span></div>
                <input type="range" id="tilt" min="0" max="85" step="1" value="60" oninput="updateRug()">
            </div>
        </div>

        <div class="main-view">
            <div id="loader" style="position:absolute; z-index:500; display:none; color:var(--gold);">🎨 Drawing Room...</div>
            <div id="room-wrap" style="position:relative;">
                <img id="room-img" src="https://via.placeholder.com/1280x800/111/333?text=Studio+Area" alt="Oda">
                <img id="rug-obj" src="" style="display:none;">
            </div>
        </div>
    </div>

    <script>
        function toggleStudio(show) {
            document.getElementById('studio').style.display = show ? 'grid' : 'none';
            document.getElementById('main-content').style.display = show ? 'none' : 'block';
            if(show) window.scrollTo(0,0);
        }

        function generateRoom() {
            const type = document.getElementById('roomType').value;
            const loader = document.getElementById('loader');
            const roomImg = document.getElementById('room-img');
            loader.style.display = "block";
            roomImg.style.opacity = "0.2";
            
            const prompt = `Professional photography of a ${type}, empty wooden floor in foreground, cinematic lighting, 8k.`;
            roomImg.onload = () => { loader.style.display = "none"; roomImg.style.opacity = "1"; };
            roomImg.src = `https://image.pollinations.ai/prompt/${encodeURIComponent(prompt)}?width=1280&height=800&nologo=true&seed=${Math.random()}&model=flux`;
        }

        function loadRug(e) {
            const rug = document.getElementById('rug-obj');
            const file = e.target.files[0];
            if(file) {
                rug.src = URL.createObjectURL(file);
                rug.style.display = "block";
                rug.style.top = "70%"; rug.style.left = "50%";
                updateRug();
            }
        }

        function updateRug() {
            const rug = document.getElementById('rug-obj');
            const scale = document.getElementById('scale').value;
            const tilt = document.getElementById('tilt').value;
            document.getElementById('v-scale').innerText = scale;
            document.getElementById('v-tilt').innerText = tilt + "°";
            rug.style.transform = `translate(-50%, -50%) perspective(1200px) rotateX(${tilt}deg) scale(${scale})`;
        }

        // Sürükleme
        const rug = document.getElementById('rug-obj');
        let dragging = false;
        rug.onmousedown = () => dragging = true;
        window.onmousemove = (e) => {
            if (dragging) {
                const wrap = document.getElementById('room-wrap').getBoundingClientRect();
                rug.style.left = ((e.clientX - wrap.left) / wrap.width) * 100 + "%";
                rug.style.top = ((e.clientY - wrap.top) / wrap.height) * 100 + "%";
            }
        };
        window.onmouseup = () => dragging = false;
        
        rug.ontouchstart = () => dragging = true;
        window.ontouchmove = (e) => {
            if (dragging) {
                const wrap = document.getElementById('room-wrap').getBoundingClientRect();
                rug.style.left = ((e.touches[0].clientX - wrap.left) / wrap.width) * 100 + "%";
                rug.style.top = ((e.touches[0].clientY - wrap.top) / wrap.height) * 100 + "%";
            }
        };
        window.ontouchend = () => dragging = false;
    </script>
</body>
</html>
