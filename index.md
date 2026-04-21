<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RugVision Pro — Cappadocia Edition</title>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;600&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --accent: #c0392b;
            --bg: #0a0a0a;
            --panel: #141414;
            --text: #f0ede8;
            --gold: #c9a84c;
        }

        body, html { margin: 0; padding: 0; font-family: 'DM Sans', sans-serif; background: var(--bg); color: var(--text); overflow-x: hidden; }

        /* ─── LANDING PAGE (GİRİŞ) ─── */
        .hero {
            height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center;
            background: radial-gradient(circle at center, #1a0a0a 0%, #0a0a0a 100%);
            text-align: center; padding: 20px;
        }
        h1 { font-family: 'Cormorant Garamond', serif; font-size: clamp(40px, 8vw, 80px); margin-bottom: 10px; font-weight: 300; }
        h1 em { color: var(--gold); font-style: italic; }
        .sub { color: #888; max-width: 600px; margin-bottom: 40px; line-height: 1.6; }

        /* VİDEO ALANI */
        .video-box {
            width: min(800px, 90vw); aspect-ratio: 16/9; background: #000; border: 1px solid var(--gold);
            border-radius: 12px; box-shadow: 0 20px 50px rgba(0,0,0,0.8); display: flex; align-items: center; justify-content: center; position: relative;
        }
        .play-overlay { position: absolute; color: var(--gold); font-size: 14px; letter-spacing: 2px; }

        /* BUTON (VİDEO ALTI) */
        .cta-container { margin-top: 30px; }
        .btn-launch {
            background: var(--accent); color: white; padding: 18px 40px; border: none; border-radius: 4px;
            font-size: 16px; font-weight: bold; cursor: pointer; transition: 0.3s; letter-spacing: 1px;
        }
        .btn-launch:hover { background: #e74c3c; transform: scale(1.05); }

        /* ─── STUDIO PAGE (STUDYO) ─── */
        #studio {
            display: none; position: fixed; inset: 0; z-index: 1000; background: var(--bg);
            grid-template-columns: 320px 1fr;
        }
        .sidebar {
            background: var(--panel); border-right: 1px solid #333; padding: 25px; overflow-y: auto;
        }
        .main-view {
            background: #000; position: relative; display: flex; align-items: center; justify-content: center; overflow: hidden;
        }

        .sidebar h2 { font-family: 'Cormorant Garamond'; color: var(--gold); font-size: 24px; margin-bottom: 20px; }
        .input-box { margin-bottom: 20px; }
        label { display: block; font-size: 11px; color: #666; text-transform: uppercase; margin-bottom: 8px; }
        select, input { width: 100%; padding: 12px; background: #222; border: 1px solid #444; color: white; border-radius: 6px; }

        /* HALI AYARLARI (YAPIŞTIRMA ÇUBUKLARI) */
        .control-group { background: #1a1a1a; padding: 15px; border-radius: 10px; border: 1px solid #333; margin-top: 20px; }
        input[type="range"] { accent-color: var(--accent); margin: 10px 0; }
        .val-text { float: right; color: var(--gold); }

        /* HALI NESNESİ */
        #room-img { max-width: 95%; max-height: 90vh; border-radius: 8px; }
        #rug-obj {
            position: absolute; width: 250px; z-index: 100; cursor: move;
            filter: drop-shadow(0 15px 30px rgba(0,0,0,0.8));
            transform-origin: center;
            /* YAPIŞMA EFEKTİ BURADA */
            transform: translate(-50%, -50%) perspective(1000px) rotateX(65deg);
        }

        .btn-close { position: absolute; top: 20px; right: 20px; background: #333; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; z-index: 1001; }
        #loader { position: absolute; color: var(--gold); background: rgba(0,0,0,0.9); padding: 20px; border-radius: 10px; display: none; border: 1px solid var(--accent); }
    </style>
</head>
<body>

    <!-- GİRİŞ SAYFASI -->
    <div id="landing">
        <section class="hero">
            <div style="font-size: 11px; letter-spacing: 4px; color: var(--gold); margin-bottom: 15px;">AI-POWERED STUDIO</div>
            <h1>See Your Rug <em>in Any Room</em></h1>
            <p class="sub">Halıyı dükkanda değil, müşterinizin evindeymiş gibi gösterin. AI ile oda tasarlayın ve halınızı zemine saniyeler içinde "yapıştırın".</p>
            
            <div class="video-box">
                <div class="play-overlay">STUDIO PREVIEW MOVIE</div>
            </div>

            <div class="cta-container">
                <button class="btn-launch" onclick="openStudio()">LAUNCH STUDIO NOW</button>
            </div>
        </section>
    </div>

    <!-- STUDIO SAYFASI -->
    <div id="studio">
        <button class="btn-close" onclick="closeStudio()">✕ EXIT</button>
        
        <div class="sidebar">
            <h2>Configurator</h2>
            
            <div class="input-box">
                <label>1. Upload Your Rug</label>
                <input type="file" id="rugInput" accept="image/*" onchange="loadRug(event)">
            </div>

            <div class="input-box">
                <label>Room Type</label>
                <select id="roomType">
                    <option value="luxury entrance hallway">Entrance (Antre)</option>
                    <option value="modern spacious living room">Living Room (Salon)</option>
                    <option value="cozy master bedroom">Bedroom (Yatak Odası)</option>
                </select>
            </div>

            <div class="input-box">
                <label>Furniture Color</label>
                <select id="sofaColor">
                    <option value="Cream boucle">Cream (Krem)</option>
                    <option value="Anthracite grey">Grey (Antrasit)</option>
                    <option value="Emerald green velvet">Green (Yeşil)</option>
                    <option value="Cognac leather">Leather (Deri)</option>
                </select>
            </div>

            <button class="btn-launch" style="width:100%;" onclick="generateRoom()">2. GENERATE AI ROOM</button>

            <div class="control-group">
                <label style="color:var(--gold)">3. Floor Alignment (Yapıştırma)</label>
                
                <label>Size <span class="val-text" id="v-scale">1.0</span></label>
                <input type="range" id="scale" min="0.1" max="2.5" step="0.05" value="1" oninput="updateRug()">

                <label>Floor Tilt (Yatırma) <span class="val-text" id="v-tilt">65°</span></label>
                <input type="range" id="tilt" min="0" max="88" step="1" value="65" oninput="updateRug()">

                <label>Rotate <span class="val-text" id="v-rotate">0°</span></label>
                <input type="range" id="rotate" min="-180" max="180" step="1" value="0" oninput="updateRug()">
            </div>
        </div>

        <div class="main-view">
            <div id="loader">🎨 AI is drawing the room...</div>
            <div id="room-wrap" style="position:relative;">
                <img id="room-img" src="https://via.placeholder.com/1200x800/111/444?text=AI+Room+Area" alt="Room">
                <img id="rug-obj" src="" style="display:none;">
            </div>
        </div>
    </div>

    <script>
        function openStudio() {
            document.getElementById('landing').style.display = 'none';
            document.getElementById('studio').style.display = 'grid';
        }

        function closeStudio() {
            document.getElementById('landing').style.display = 'block';
            document.getElementById('studio').style.display = 'none';
        }

        // AI ODA OLUŞTURMA
        function generateRoom() {
            const type = document.getElementById('roomType').value;
            const sofa = document.getElementById('sofaColor').value;
            const loader = document.getElementById('loader');
            const roomImg = document.getElementById('room-img');

            loader.style.display = "block";
            roomImg.style.opacity = "0.2";

            const prompt = `Professional photography of a ${type} with ${sofa} furniture, large windows, completely empty wooden floor in the foreground, 8k resolution.`;
            const seed = Math.floor(Math.random() * 100000);
            
            roomImg.onload = () => {
                loader.style.display = "none";
                roomImg.style.opacity = "1";
            };
            roomImg.src = `https://image.pollinations.ai/prompt/${encodeURIComponent(prompt)}?width=1280&height=800&nologo=true&seed=${seed}&model=flux`;
        }

        // HALI YÜKLEME
        function loadRug(event) {
            const rug = document.getElementById('rug-obj');
            const file = event.target.files[0];
            if (file) {
                rug.src = URL.createObjectURL(file);
                rug.style.display = "block";
                rug.style.top = "75%";
                rug.style.left = "50%";
                updateRug();
            }
        }

        // ZEMİNE YAPIŞTIRMA (HASSAS PERSPEKTİF)
        function updateRug() {
            const rug = document.getElementById('rug-obj');
            const scale = document.getElementById('scale').value;
            const tilt = document.getElementById('tilt').value;
            const rotate = document.getElementById('rotate').value;

            document.getElementById('v-scale').innerText = scale;
            document.getElementById('v-tilt').innerText = tilt + "°";
            document.getElementById('v-rotate').innerText = rotate + "°";

            // Halıyı zemine "stick" (mıhlayan) asıl kod:
            rug.style.transform = `translate(-50%, -50%) perspective(1200px) rotateX(${tilt}deg) rotateZ(${rotate}deg) scale(${scale})`;
        }

        // SÜRÜKLEME
        const rug = document.getElementById('rug-obj');
        let dragging = false;

        rug.onmousedown = () => dragging = true;
        window.onmousemove = (e) => {
            if (dragging) {
                const wrap = document.getElementById('room-wrap').getBoundingClientRect();
                let x = ((e.clientX - wrap.left) / wrap.width) * 100;
                let y = ((e.clientY - wrap.top) / wrap.height) * 100;
                rug.style.left = x + "%";
                rug.style.top = y + "%";
            }
        };
        window.onmouseup = () => dragging = false;

        // Dokunmatik (Tablet) desteği
        rug.ontouchstart = () => dragging = true;
        window.ontouchmove = (e) => {
            if (dragging) {
                const wrap = document.getElementById('room-wrap').getBoundingClientRect();
                let x = ((e.touches[0].clientX - wrap.left) / wrap.width) * 100;
                let y = ((e.touches[0].clientY - wrap.top) / wrap.height) * 100;
                rug.style.left = x + "%";
                rug.style.top = y + "%";
            }
        };
        window.ontouchend = () => dragging = false;
    </script>
</body>
</html>