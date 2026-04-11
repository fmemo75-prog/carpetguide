<!-- SECTION: THE CURATOR'S ROOTS -->
<h2 style="color: #8b0000;">🏠 My Cappadocia: The Triad of My Life</h2>

<table border="0" style="width:100%; background-color: #fdf5e6; border-radius: 15px; padding: 20px; border-collapse: collapse;">
  <tr>
    <!-- SOL SÜTUN: KİŞİSEL HİKAYE -->
    <td style="width: 50%; vertical-align: top; padding-right: 20px;">
      <p>Cappadocia is not just a destination for me; it is my timeline. As you can see on the map, my life follows the path of the <strong>Kızılırmak (Red River)</strong>.</p>
      
      <ul style="line-height: 1.8;">
        <li><strong>Bayramhacı (The Source):</strong> My birthplace. Located by the dam, it's famous for its thermal springs. This is where I learned the value of nature and healing waters.</li>
        <li><strong>Avanos (The Mold):</strong> Where I grew up. The river's red clay shaped my childhood. It's the center of pottery and traditional Turkish handicrafts.</li>
        <li><strong>Göreme (The Heart):</strong> My current home and professional center. The pinnacle of rock-cut history where I now guide visitors as a local expert.</li>
      </ul>
      <p><i>This map shows the 40km circle where I have spent my life, learning every valley and every knot of our culture.</i></p>
    </td>
<style>
    .welcome-letter {
        background: #fdfaf6; /* Hafif parşömen rengi */
        border: 1px solid #e0d5c5;
        border-left: 5px solid #8b0000;
        padding: 30px;
        margin: 20px auto;
        max-width: 800px;
        border-radius: 8px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        font-family: 'Georgia', serif;
        line-height: 1.8;
        color: #444;
        position: relative;
    }

    .welcome-letter::before {
        content: "“";
        position: absolute;
        top: 10px;
        left: 20px;
        font-size: 60px;
        color: #8b0000;
        opacity: 0.1;
    }

    .welcome-letter h2 {
        color: #8b0000;
        margin-top: 0;
        font-size: 22px;
        border-bottom: 1px solid #eee;
        padding-bottom: 10px;
    }

    .welcome-letter p {
        margin-bottom: 15px;
        font-style: italic;
    }

    .signature {
        text-align: right;
        margin-top: 20px;
        font-weight: bold;
        color: #8b0000;
    }

    .signature span {
        display: block;
        font-size: 14px;
        color: #666;
        font-weight: normal;
    }
</style>


        <span>50 Years of Cappadocia Experience</span>
    </div>
</div>
---
---
layout: default
title: Global Cappadocia Guide - Polyglot Edition
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
    #map-wrapper { position: relative; }
    #map { height: 600px; width: 100%; border-radius: 15px; border: 3px solid #8b0000; box-shadow: 0 10px 30px rgba(0,0,0,0.2); }
    .lang-box { text-align: center; margin: 20px 0; display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
    .lang-btn { padding: 8px 15px; cursor: pointer; border-radius: 50px; border: 1.5px solid #8b0000; background: white; font-weight: bold; font-size: 13px; transition: 0.3s; }
    .lang-btn.active { background: #8b0000; color: white; }

    /* Harita üstü overlay panel */
    #info-card {
        display: none;
        position: absolute;
        top: 12px;
        right: 12px;
        width: 320px;
        max-height: 570px;
        overflow-y: auto;
        background: #fff;
        padding: 20px;
        border-radius: 14px;
        border-top: 8px solid #8b0000;
        box-shadow: 0 8px 32px rgba(0,0,0,0.28);
        z-index: 1000;
        box-sizing: border-box;
    }
    #info-card.visible { display: block; }

    /* Kapatma butonu */
    #close-btn {
        position: absolute;
        top: 10px;
        right: 12px;
        background: none;
        border: none;
        font-size: 20px;
        cursor: pointer;
        color: #8b0000;
        line-height: 1;
        padding: 0;
    }
    #close-btn:hover { color: #333; }

    .info-section { margin-bottom: 10px; padding-bottom: 8px; border-bottom: 1px dashed #ddd; }
    .info-label { font-weight: bold; color: #8b0000; text-transform: uppercase; font-size: 10px; display: block; }
    .whatsapp-btn { display: inline-block; background: #25D366; color: white !important; padding: 8px 16px; border-radius: 50px; text-decoration: none; font-weight: bold; margin-top: 8px; font-size: 13px; }
    #place-name { margin-top: 0; margin-right: 20px; color: #8b0000; font-family: 'Georgia', serif; font-size: 15px; line-height: 1.3; }

    /* Mobil: panel tam genişlik, haritanın alt kısmına yapışır */
    @media (max-width: 520px) {
        #info-card {
            top: auto;
            bottom: 12px;
            right: 8px;
            left: 8px;
            width: auto;
            max-height: 52%;
        }
    }

    /* Mobil kaydır hatırlatıcısı */
    #scroll-hint {
        display: none;
        position: absolute;
        bottom: 70px;
        left: 50%;
        transform: translateX(-50%);
        background: rgba(139,0,0,0.82);
        color: white;
        font-size: 12px;
        font-family: Georgia, serif;
        padding: 7px 16px;
        border-radius: 20px;
        white-space: nowrap;
        z-index: 1100;
        pointer-events: none;
        animation: bounceUp 1.4s ease-in-out infinite;
    }
    #scroll-hint.visible { display: block; }
    @keyframes bounceUp {
        0%, 100% { transform: translateX(-50%) translateY(0); }
        50%       { transform: translateX(-50%) translateY(-5px); }
    }
    @media (min-width: 521px) {
        #scroll-hint { display: none !important; }
    }
</style>

<div style="text-align: center; font-family: 'Georgia', serif; padding: 10px;">
    <h1 id="interactive-map" style="color: #8b0000;">🏺 Cappadocia Master Polyglot Guide</h1>
    <p><i>Insider Tips, VIP Contacts & Interactive Map</i></p>
</div>

<!-- ÇOK DİLLİ SEÇİCİ -->
<div class="lang-box">
    <button id="en-btn" class="lang-btn active" onclick="setLang('en')">🇺🇸 English</button>
    <button id="fr-btn" class="lang-btn" onclick="setLang('fr')">🇫🇷 Français</button>
    <button id="es-btn" class="lang-btn" onclick="setLang('es')">🇪🇸 Español</button>
    <button id="it-btn" class="lang-btn" onclick="setLang('it')">🇮🇹 Italiano</button>
    <button id="ru-btn" class="lang-btn" onclick="setLang('ru')">🇷🇺 Русский</button>
    <button id="zh-btn" class="lang-btn" onclick="setLang('zh')">🇨🇳 中文</button>
    <button id="ja-btn" class="lang-btn" onclick="setLang('ja')">🇯🇵 日本語</button>
</div>

<div style="background: linear-gradient(135deg, #fff8f0 0%, #fff 100%); border-left: 5px solid #8b0000; border-radius: 12px; padding: 22px 26px; margin-bottom: 22px; box-shadow: 0 3px 14px rgba(139,0,0,0.08); font-family: Georgia, serif;">
    <p style="margin: 0 0 10px 0; font-size: 15px; color: #8b0000; font-weight: bold; letter-spacing: 0.5px;">✍️ A Personal Note</p>
    <p style="margin: 0; font-size: 15px; color: #333; line-height: 1.85;">
        Dear traveller, welcome to Cappadocia — one of the most extraordinary places on earth.<br><br>
        I have been walking these valleys, visiting these workshops, and sharing this land with visitors from every corner of the world for over <strong>50 years</strong>. As a teacher by profession and a passionate guide by heart, I have seen what makes a journey here truly memorable — and what leads people astray.<br><br>
        The places and people I have marked on this map are not random recommendations. They are the result of half a century of friendship, trust, and personal experience. When I point you to a carpet shop or a local expert, I do so as a friend who has sat at their table, drunk their tea, and watched them work with my own eyes.<br><br>
        <em>Explore with curiosity, shop with confidence, and let Cappadocia touch your heart the way it has touched mine.</em>
      Fatih Mehmet CANITEZ
    </p>
</div>

<div id="map-wrapper">
    <div id="map"></div>
    <div id="scroll-hint">👆 Scroll up to read more</div>

    <div id="info-card">
        <button id="close-btn" onclick="closePanel()">✕</button>
        <h2 id="place-name"></h2>

        <div class="info-section">
            <span class="info-label" id="label-worth">Expert Recommendation</span>
            <p id="worth-text" style="font-weight: bold; margin: 5px 0; font-size:13px;"></p>
        </div>

        <div class="info-section">
            <span class="info-label" id="label-see">Description</span>
            <p id="see-text" style="margin: 5px 0; font-size:13px;"></p>
        </div>

        <div id="contact-section" class="info-section" style="display:none; background: #f0fff4; padding: 10px; border-radius: 10px;">
            <span class="info-label">📱 Direct Contact</span>
            <p id="contact-name" style="margin: 5px 0; font-weight: bold; font-size:13px;"></p>
            <a id="wa-link" href="#" target="_blank" class="whatsapp-btn">💬 WhatsApp</a>
            <a id="ig-link" href="#" target="_blank" style="display:none; margin-left:8px; background:#E1306C; color:white; padding:8px 16px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:13px;">📸 Instagram</a>
            <a id="maps-link" href="#" target="_blank" style="display:none; margin-left:8px; background:#4285F4; color:white; padding:8px 16px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:13px;">📍 Google Maps</a>
        </div>

        <div class="info-section" style="border-bottom:none;">
            <span class="info-label" id="label-secret">Insider Note</span>
            <p id="do-text" style="margin: 5px 0; font-style: italic; font-size:13px;"></p>
        </div>
    </div>
</div>

<script>
var map = L.map('map').setView([38.65, 34.85], 11);
var currentLang = 'en';
var activePoint = null;

L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png').addTo(map);

// LOKASYON VERİLERİ (Genişletilmiş ve Çok Dilli)
var locations = [
    // ── MEVCUT LOKASYONLAR ──────────────────────────────────────────────
    {
        coords: [38.642, 34.829],
        id: "kervan",
        wa: "905367602165",
        maps: "https://share.google/4EOqQF0v25v89O0XW",
        en: { n: "KERVAN CARPET (Bülent Güler)", w: "Highly Recommended for Shopping", s: "Located in Goreme. Fine selection of hand-knotted carpets.", d: "Ask for Bülent. He is a true gentleman of the craft." },
        fr: { n: "KERVAN CARPET (Bülent Güler)", w: "Hautement recommandé", s: "Situé à Göreme. Fine sélection de tapis noués à la main.", d: "Demandez Bülent. Un vrai maître de l'art." },
        es: { n: "ALFOMBRAS KERVAN", w: "Muy recomendado", s: "Ubicado en Goreme. Gran selección de alfombras.", d: "Pregunta por Bülent." },
        it: { n: "KERVAN CARPET", w: "Altamente raccomandato", s: "Selezione di tappeti fatti a mano.", d: "Chiedi di Bülent." },
        ru: { n: "КЕРВАН КОВРЫ", w: "Рекомендуется", s: "Лучший выбор ковров в Гёреме.", d: "Спросите Бюлента." },
        zh: { n: "KERVAN 地毯", w: "强烈推荐", s: "位于格雷梅，精选手工毯。", d: "找 Bülent。" },
        ja: { n: "KERVAN 絨毯", w: "強くお勧めします", s: "ギョレメにある手織り絨毯店。", d: "Bülentさんを訪ねてください。" }
    },
    {
        coords: [38.621, 34.856],
        id: "punto",
        wa: "905324970321",
        ig: "puntoofcappadocia",
        en: { n: "PUNTO ANTIQUE CARPETS", w: "VIP Antique Collection", s: "Located in Ortahisar. Specialist in old and rare textile collections.", d: "Ask for Headmaster Hüseyin ÖZER for professional antique analysis." },
        fr: { n: "PUNTO TAPIS ANTIQUES", w: "Collection VIP Antique", s: "Situé à Ortahisar. Spécialiste des collections textiles rares.", d: "Demandez le Directeur Hüseyin ÖZER pour une analyse antique professionnelle." },
        es: { n: "PUNTO ALFOMBRAS ANTIGUAS", w: "Colección VIP", s: "Ortahisar. Especialista en piezas raras.", d: "Pregunta por el Director Hüseyin ÖZER para análisis profesional." },
        it: { n: "PUNTO TAPPETI ANTICHI", w: "Collezione Antica VIP", s: "Specialista in tessuti rari.", d: "Chiedi del Direttore Hüseyin ÖZER per un'analisi antiquaria professionale." },
        ru: { n: "ПУНТО АНТИКВАРНЫЕ КОВРЫ", w: "VIP Коллекция", s: "Ортахисар. Редкие ковры.", d: "Обратитесь к директору Хюсейн ОЗЕР для профессиональной антикварной экспертизы." },
        zh: { n: "PUNTO 古董地毯", w: "VIP古董收藏", s: "位于奥塔希萨尔，稀有收藏。", d: "请找负责人 Hüseyin ÖZER 进行专业古董鉴定。" },
        ja: { n: "PUNTO アンティーク絨毯", w: "VIPアンティーク", s: "希少なアンティーク絨毯の専門店。", d: "専門鑑定はヘッドマスター Hüseyin ÖZER さんにお声がけください。" }
    },
    {
        coords: [38.645, 34.831],
        id: "ikman",
        en: { n: "IKMAN CARPET (Photography)", w: "The #1 Instagram Spot", s: "Famous for traditional carpet photography setups.", d: "A colorful paradise for photographers." },
        fr: { n: "TAPIS IKMAN (Photographie)", w: "Le spot Instagram n°1", s: "Célèbre pour les séances photo traditionnelles.", d: "Paradis pour photographes." },
        es: { n: "ALFOMBRAS IKMAN (Fotos)", w: "Punto Instagram", s: "Famoso por sus fotos con alfombras.", d: "Paraíso fotográfico." },
        it: { n: "IKMAN CARPET (Foto)", w: "Spot Instagram", s: "Famoso per set fotografici.", d: "Paradiso dei fotografi." },
        ru: { n: "ИКМАН КОВРЫ (Фото)", w: "Инстаграм спот", s: "Знаменитое место для фотосессий.", d: "Рай для фотографов." },
        zh: { n: "IKMAN 地毯 (摄影)", w: "顶级网红打卡点", s: "传统地毯背景摄影。", d: "摄影师的天堂。" },
        ja: { n: "IKMAN 絨毯 (写真)", w: "インスタ映えスポット", s: "絨毯に囲まれた有名な写真スポット。", d: "フォトグラファーのパラダイス。" }
    },
    {
        coords: [38.641, 34.832],
        id: "museum",
        en: { n: "ANATOLIAN ART MUSEUM", w: "Cultural Landmark", s: "Museum dedicated to the history of Anatolian weaving and arts.", d: "A must-visit for academic understanding of the art." },
        fr: { n: "MUSÉE D'ART ANATOLIEN", w: "Repère culturel", s: "Musée dédié à l'histoire du tissage anatolien.", d: "Indispensable pour la culture académique." },
        es: { n: "MUSEO DE ARTE ANATOLIO", w: "Hito cultural", s: "Dedicado a la historia del tejido.", d: "Visita obligatoria." },
        it: { n: "MUSEO D'ARTE ANATOLICA", w: "Punto culturale", s: "Dedicato alla storia della tessitura.", d: "Visita accademica." },
        ru: { n: "МУЗЕЙ АНАТОЛИЙСКОГО ИСКУССТВА", w: "Культурный центр", s: "История анатолийского ткачества.", d: "Обязательно к посещению." },
        zh: { n: "安纳托利亚艺术博物馆", w: "文化地标", s: "致力于安纳托利亚编织历史。", d: "学术了解艺术必看。" },
        ja: { n: "アナトリア芸術博物館", w: "文化遺産", s: "アナトリアの織物歴史博物館。", d: "芸術を学ぶなら必見。" }
    },
    {
        coords: [38.640, 34.825],
        id: "halil",
        wa: "905322478674",
        en: { n: "VIP GUIDE: HALİL KÖKSAL", w: "Expert Language Guide", s: "Specialist in French & Spanish languages. Deep historical knowledge.", d: "Book Halil for a high-quality, professional cultural tour." },
        fr: { n: "GUIDE VIP : HALİL KÖKSAL", w: "Expert Conférencier", s: "Spécialiste en Français et Espagnol.", d: "Réservez Halil pour une visite culturelle de haute qualité." },
        es: { n: "GUÍA VIP: HALİL KÖKSAL", w: "Guía Experto", s: "Especialista en Francés y Español.", d: "Reserva a Halil para un tour profesional." },
        it: { n: "GUIDA VIP: HALİL KÖKSAL", w: "Guida Esperta", s: "Parla Francese e Spagnolo.", d: "Prenota Halil per tour professionali." },
        ru: { n: "VIP ГИД: ХАЛИЛ КЁКСАЛ", w: "Профессиональный гид", s: "Специалист по истории на французском и испанском.", d: "Закажите Халила для тура высшего класса." },
        zh: { n: "VIP 导游: HALİL KÖKSAL", w: "专家语言导游", s: "精通法语和西班牙语，深厚的历史知识。", d: "预订 Halil 提供高质量文化之旅。" },
        ja: { n: "VIPガイド: HALİL KÖKSAL", w: "公認ガイド", s: "フランス語とスペイン語のエキスパート。", d: "プロの文化ツアーならHalilさんを。" }
    },

    // ── YENİ EKLENEN LOKASYONLAR ─────────────────────────────────────────

    // 1. Göreme Açık Hava Müzesi
    {
        coords: [38.6431, 34.8619],
        id: "goreme_oam",
        en: { n: "GÖREME OPEN AIR MUSEUM", w: "UNESCO World Heritage Site", s: "A complex of Byzantine-era rock-cut churches decorated with stunning frescoes. Dates back to the 10th century. Home to the famous Dark Church (Karanlık Kilise) with perfectly preserved paintings.", d: "Arrive before 9 AM to avoid crowds. The Dark Church requires a separate ticket but is absolutely worth it." },
        fr: { n: "MUSÉE EN PLEIN AIR DE GÖREME", w: "Site du Patrimoine Mondial UNESCO", s: "Complexe d'églises rupestres byzantines ornées de fresques éblouissantes datant du Xe siècle. Abrite la célèbre Église Sombre aux peintures remarquablement conservées.", d: "Arrivez avant 9h pour éviter la foule. L'Église Sombre nécessite un billet séparé, mais en vaut absolument la peine." },
        es: { n: "MUSEO AL AIRE LIBRE DE GÖREME", w: "Patrimonio Mundial UNESCO", s: "Complejo de iglesias rupestres bizantinas adornadas con frescos del siglo X. Alberga la famosa Iglesia Oscura con pinturas perfectamente conservadas.", d: "Llega antes de las 9 AM para evitar las multitudes. La Iglesia Oscura requiere entrada aparte pero vale cada lira." },
        it: { n: "MUSEO ALL'APERTO DI GÖREME", w: "Patrimonio UNESCO", s: "Complesso di chiese rupestri bizantine con affreschi del X secolo. La celebre Chiesa Oscura conserva pitture straordinarie.", d: "Arriva prima delle 9 per evitare la folla. La Chiesa Oscura richiede biglietto separato ma ne vale la pena." },
        ru: { n: "МУЗЕЙ ПОД ОТКРЫТЫМ НЕБОМ ГЁРЕМЕ", w: "Объект Всемирного наследия ЮНЕСКО", s: "Комплекс византийских скальных церквей X века с потрясающими фресками. Знаменитая Тёмная церковь хранит идеально сохранившиеся росписи.", d: "Приходите до 9 утра, чтобы избежать толп. Тёмная церковь — отдельный билет, но того стоит." },
        zh: { n: "戈莱梅露天博物馆", w: "联合国教科文组织世界遗产", s: "拜占庭时期岩石教堂群，装饰着精美壁画，可追溯至10世纪。著名的黑暗教堂保存着完好无损的绘画作品。", d: "建议9点前到达以避开人群。黑暗教堂需要单独购票，但绝对值得。" },
        ja: { n: "ギョレメ野外博物館", w: "ユネスコ世界遺産", s: "10世紀のビザンチン時代の岩窟教会群。見事なフレスコ画が残る暗闇教会（カランルック・キリセ）は必見。", d: "混雑を避けるため午前9時前に到着を。暗闇教会は別料金ですが絶対に価値あり。" }
    },

    // 2. Uçhisar Kalesi
    {
        coords: [38.6289, 34.8053],
        id: "uchisar",
        en: { n: "UCHISAR CASTLE", w: "Highest Panoramic Point in Cappadocia", s: "A 60-meter tall ancient citadel carved into volcanic rock, offering the most breathtaking 360° panoramic view of the entire region. Used as a fortress in Byzantine times to spot enemy attacks.", d: "Best visited at sunset — the view of the fairy chimneys bathed in golden light is unforgettable. Wear sturdy shoes for the climb." },
        fr: { n: "CHÂTEAU D'UÇHISAR", w: "Point panoramique le plus haut de Cappadoce", s: "Citadelle de 60 mètres taillée dans le roc volcanique, offrant la vue à 360° la plus spectaculaire de la région. Utilisé comme forteresse byzantine pour surveiller les attaques ennemies.", d: "À visiter au coucher du soleil — la vue sur les cheminées de fées baignées de lumière dorée est inoubliable. Portez des chaussures solides." },
        es: { n: "CASTILLO DE UÇHISAR", w: "El punto más alto de Capadocia", s: "Ciudadela de 60 metros tallada en roca volcánica con la vista panorámica de 360° más impresionante de la región. Fue fortaleza bizantina para avistar ataques enemigos.", d: "Mejor al atardecer — las chimeneas de hadas bañadas en luz dorada son inolvidables. Usa calzado resistente para subir." },
        it: { n: "CASTELLO DI UÇHISAR", w: "Il punto panoramico più alto della Cappadocia", s: "Cittadella di 60 metri scavata nella roccia vulcanica con la vista panoramica a 360° più mozzafiato della regione. Utilizzata come fortezza bizantina.", d: "Da visitare al tramonto — le ciminiere delle fate nella luce dorata sono indimenticabili. Indossa scarpe robuste per la salita." },
        ru: { n: "ЗАМОК УЧИСАР", w: "Наивысшая панорамная точка Каппадокии", s: "60-метровая крепость в вулканической скале с лучшим круговым обзором региона. В Byzantine эпоху служила дозорной башней против вражеских набегов.", d: "Лучше всего приходить на закате — вид на «каминные трубы» в золотом свете незабываем. Надевайте удобную обувь." },
        zh: { n: "乌奇萨尔城堡", w: "卡帕多西亚最高全景点", s: "60米高的火山岩古堡，提供整个地区最壮观的360°全景视野。拜占庭时代曾作为要塞用于侦测敌袭。", d: "日落时分前往最佳——金色光芒下的仙女烟囱令人难忘。登顶需穿防滑鞋。" },
        ja: { n: "ユチヒサール城塞", w: "カッパドキア最高の展望地点", s: "火山岩を削って造られた高さ60mの古代要塞。地域全体を見渡せる360°の絶景パノラマを誇る。ビザンチン時代には敵の侵攻を監視する砦として機能。", d: "夕日の時間帯がベスト。金色の光に包まれた奇岩群は一生の思い出に。滑りにくい靴で訪れてください。" }
    },

    // 3. Derinkuyu Yeraltı Şehri
    {
        coords: [38.3736, 34.7344],
        id: "derinkuyu",
        en: { n: "DERINKUYU UNDERGROUND CITY", w: "The Deepest Underground City in the World", s: "An extraordinary multi-level subterranean city reaching 85 meters deep with 11 floors. Built by the Phrygians around the 8th century BC and expanded by Byzantine Christians. Could shelter over 20,000 people including livestock.", d: "Located ~40 km south of Göreme, reachable by bus or tour. Allow 1–1.5 hours inside. Not recommended for claustrophobic visitors." },
        fr: { n: "VILLE SOUTERRAINE DE DERINKUYU", w: "La ville souterraine la plus profonde du monde", s: "Ville souterraine extraordinaire à plusieurs niveaux atteignant 85 mètres de profondeur sur 11 étages. Construite par les Phrygiens au VIIIe siècle av. J.-C., elle pouvait abriter plus de 20 000 personnes.", d: "À ~40 km au sud de Göreme, accessible en bus ou en circuit. Comptez 1 à 1h30 sur place. Déconseillé aux claustrophobes." },
        es: { n: "CIUDAD SUBTERRÁNEA DE DERINKUYU", w: "La ciudad subterránea más profunda del mundo", s: "Extraordinaria ciudad subterránea de 11 pisos y 85 metros de profundidad. Construida por los frigios en el siglo VIII a.C., podía albergar a más de 20.000 personas.", d: "A ~40 km al sur de Göreme, accesible en autobús o tour. Reserva 1–1,5 horas. No recomendada para personas claustrofóbicas." },
        it: { n: "CITTÀ SOTTERRANEA DI DERINKUYU", w: "La città sotterranea più profonda del mondo", s: "Straordinaria città sotterranea a 11 livelli, profonda 85 metri. Costruita dai Frigi nell'VIII sec. a.C., poteva ospitare oltre 20.000 persone.", d: "A ~40 km a sud di Göreme, raggiungibile in bus o tour. Concedi 1–1,5 ore. Sconsigliata ai claustrofobici." },
        ru: { n: "ПОДЗЕМНЫЙ ГОРОД ДЕРИНКУЮ", w: "Самый глубокий подземный город в мире", s: "Многоуровневый подземный город глубиной 85 метров (11 этажей). Построен фригийцами в VIII веке до н.э., вмещал более 20 000 человек вместе со скотом.", d: "В ~40 км к югу от Гёреме. Выделите 1–1,5 часа. Не рекомендуется людям с клаустрофобией." },
        zh: { n: "德林库尤地下城", w: "世界最深的地下城市", s: "拥有11层、深达85米的非凡地下城市。约公元前8世纪由弗里吉亚人建造，可容纳2万余人及其牲畜避难。", d: "位于格雷梅以南约40公里处，可乘巴士或参团前往。建议预留1至1.5小时。不建议幽闭恐惧症患者参观。" },
        ja: { n: "デリンクユ地下都市", w: "世界最深の地下都市", s: "深さ85メートル、11層にわたる驚異の地下都市。紀元前8世紀頃にフリギア人が建造し、2万人以上を収容可能。ビザンチン時代のキリスト教徒が避難場所として使用。", d: "ギョレメから南へ約40km。内部見学に1〜1.5時間確保を。閉所恐怖症の方にはお勧めしません。" }
    },

    // 4. Paşabağ / Peribacaları Vadisi
    {
        coords: [38.6836, 34.8478],
        id: "pasabag",
        en: { n: "PAŞABAĞ — MONKS VALLEY", w: "Best Fairy Chimneys Up Close", s: "One of the finest places in Cappadocia to see the iconic fairy chimneys at close range. Some chimneys have monk cells and small chapels carved inside them. A short walk from the parking area.", d: "Arrive before 9 AM to beat the tour buses. The triple-headed fairy chimney is the star attraction — don't miss it." },
        fr: { n: "PAŞABAĞ — VALLÉE DES MOINES", s: "L'un des meilleurs endroits pour voir de près les cheminées de fées iconiques. Certaines ont des cellules de moines et des chapelles sculptées à l'intérieur.", w: "Les meilleures cheminées de fées en gros plan", d: "Arrivez avant 9h pour devancer les bus. La cheminée triple est la vedette — ne la ratez pas." },
        es: { n: "PAŞABAĞ — VALLE DE LOS MONJES", w: "Las mejores chimeneas de hadas de cerca", s: "Uno de los mejores lugares para ver las chimeneas de hadas de cerca. Algunas tienen celdas de monjes y capillas talladas en su interior.", d: "Llega antes de las 9 AM para adelantarte a los autobuses. La chimenea triple es la estrella del lugar." },
        it: { n: "PAŞABAĞ — VALLE DEI MONACI", w: "Le migliori ciminiere delle fate da vicino", s: "Uno dei migliori luoghi per ammirare le ciminiere delle fate da vicino. Alcune hanno celle di monaci e cappelle scolpite all'interno.", d: "Arriva prima delle 9 per precedere i pullman. La ciminiera a tre teste è l'attrazione principale." },
        ru: { n: "ПАШАБАГ — ДОЛИНА МОНАХОВ", w: "Лучшие «каминные трубы» вблизи", s: "Одно из лучших мест Каппадокии для осмотра знаменитых «каминных труб» вблизи. В некоторых выбиты кельи монахов и небольшие часовни.", d: "Приходите до 9 утра, чтобы опередить туристические автобусы. Трёхголовая «труба» — главная звезда места." },
        zh: { n: "帕夏贝/僧侣谷", w: "近距离欣赏仙女烟囱的最佳地点", s: "卡帕多西亚最佳仙女烟囱观赏地之一，部分烟囱内部雕凿有僧侣石室和小礼拜堂。", d: "建议9点前到达以避开旅游大巴。三头仙女烟囱是最大亮点，切勿错过。" },
        ja: { n: "パシャバー/僧侶の谷", w: "妖精の煙突を間近で見る最高の場所", s: "カッパドキアの象徴「妖精の煙突」を間近で見られる最良スポット。一部の煙突内部には修道士の住居や礼拝堂が彫られている。", d: "観光バスが来る前の午前9時前がおすすめ。3つ頭の妖精の煙突が名物。" }
    },

    // 5. Avanos
    {
        coords: [38.7181, 34.8486],
        id: "avanos",
        en: { n: "AVANOS — POTTERY TOWN", w: "Living Craft Tradition", s: "A charming town on the banks of the Kızılırmak River, Turkey's longest river. Famous for its centuries-old pottery tradition using the river's distinctive red clay. Dozens of workshops welcome visitors.", d: "Try throwing a pot yourself — most workshops offer hands-on sessions. Buy directly from the artisan for the best prices and authenticity." },
        fr: { n: "AVANOS — VILLE DE LA POTERIE", w: "Tradition artisanale vivante", s: "Ville charmante sur les rives du Kızılırmak, le plus long fleuve de Turquie. Réputée pour sa tradition séculaire de poterie à l'argile rouge du fleuve. Des dizaines d'ateliers accueillent les visiteurs.", d: "Essayez de tourner vous-même — la plupart des ateliers proposent des sessions pratiques. Achetez directement chez l'artisan pour les meilleurs prix." },
        es: { n: "AVANOS — CIUDAD DE LA CERÁMICA", w: "Tradición artesanal viva", s: "Encantadora ciudad a orillas del río Kızılırmak, el más largo de Turquía. Famosa por su tradición centenaria de cerámica con arcilla roja del río.", d: "Prueba a tornear tú mismo — la mayoría de talleres ofrecen sesiones prácticas. Compra directamente al artesano para mejores precios." },
        it: { n: "AVANOS — CITTÀ DELLA CERAMICA", w: "Tradizione artigianale viva", s: "Affascinante cittadina sulle rive del Kızılırmak, il fiume più lungo della Turchia. Famosa per la sua tradizione secolare di ceramica con argilla rossa del fiume.", d: "Prova a plasmare tu stesso — la maggior parte dei laboratori offre sessioni pratiche. Acquista direttamente dall'artigiano per i migliori prezzi." },
        ru: { n: "АВАНОС — ГОРОД ГОНЧАРОВ", w: "Живая ремесленная традиция", s: "Очаровательный городок на берегу реки Кызылырмак — самой длинной реки Турции. Знаменит вековой традицией гончарного дела из красной речной глины.", d: "Попробуйте сами — большинство мастерских предлагают мастер-классы. Покупайте напрямую у мастера для лучших цен." },
        zh: { n: "阿瓦诺斯——陶器之城", w: "活着的手工艺传统", s: "位于土耳其最长河流克孜勒河畔的迷人小镇，以数百年历史的红陶工艺闻名，数十家工坊欢迎游客参观。", d: "建议亲自尝试拉坯——大多数工坊提供亲身体验课程。直接从工匠处购买可获得最佳价格。" },
        ja: { n: "アヴァノス——陶芸の街", w: "生きた伝統工芸", s: "トルコ最長の川クズルウルマク川沿いの魅力的な町。川の赤い粘土を使った数百年の陶芸の伝統で有名。数十の工房が観光客を歓迎。", d: "ほとんどの工房で陶芸体験ができます。職人から直接購入するとお得で本物が手に入ります。" }
    },

    // 6. Güvercinlik Vadisi
    {
        coords: [38.6353, 34.8232],
        id: "pigeon_valley",
        en: { n: "PIGEON VALLEY (Güvercinlik Vadisi)", w: "Best Hiking Trail in Cappadocia", s: "A scenic valley stretching between Göreme and Uçhisar, named after the hundreds of dovecotes (pigeon houses) carved into the cliff faces. The 4 km trail takes about 1–2 hours and offers stunning rock formation views.", d: "Walk from Uçhisar Castle down to Göreme for the best downhill experience. Stop for tea at the unique rock-carved tea garden midway." },
        fr: { n: "VALLÉE DES PIGEONS", w: "Le meilleur sentier de randonnée de Cappadoce", s: "Vallée pittoresque entre Göreme et Uçhisar, nommée d'après les centaines de pigeonholes taillés dans les falaises. Le sentier de 4 km prend 1 à 2 heures.", d: "Marchez d'Uçhisar vers Göreme pour la meilleure expérience en descente. Pause thé au jardin de thé sculpté dans la roche." },
        es: { n: "VALLE DE LAS PALOMAS", w: "La mejor ruta de senderismo en Capadocia", s: "Valle pintoresco entre Göreme y Uçhisar, con cientos de palomares tallados en los acantilados. El sendero de 4 km tarda 1–2 horas.", d: "Camina de Uçhisar hacia Göreme cuesta abajo para la mejor experiencia. Para a tomar té en el jardín de té esculpido en la roca." },
        it: { n: "VALLE DEI PICCIONI", w: "Il miglior sentiero escursionistico della Cappadocia", s: "Valle panoramica tra Göreme e Uçhisar, con centinaia di colombaie scolpite nelle pareti. Il sentiero di 4 km richiede 1–2 ore.", d: "Cammina da Uçhisar verso Göreme in discesa. Fermati per un tè nel giardino scavato nella roccia a metà strada." },
        ru: { n: "ГОЛУБИНАЯ ДОЛИНА", w: "Лучший пешеходный маршрут Каппадокии", s: "Живописная долина между Гёреме и Учисаром с сотнями голубятен, вырубленных в скалах. Тропа длиной 4 км занимает 1–2 часа.", d: "Идите от Учисара вниз к Гёреме — так проще. Остановитесь на чай в уникальном чайном саду, вырубленном в скале." },
        zh: { n: "鸽子谷（Güvercinlik Vadisi）", w: "卡帕多西亚最佳徒步路线", s: "格雷梅与乌奇萨尔之间的景色如画山谷，因悬崖上数百个鸽巢而得名。4公里徒步路线需1-2小时。", d: "从乌奇萨尔城堡走向格雷梅，享受下坡体验。途中在岩石中雕凿的茶园小憩品茶。" },
        ja: { n: "鳩の谷（ギュヴェルジンリク・ヴァディシ）", w: "カッパドキア最高のハイキングコース", s: "ギョレメとユチヒサールの間に広がる景勝の谷。断崖に刻まれた数百の鳩小屋から名付けられた。4kmのトレイルで1〜2時間。", d: "ユチヒサール城塞からギョレメへ下りながら歩くのが最適。途中の岩を掘り抜いたお茶屋で一休みを。" }
    },

    // 7. Göreme Balon Noktası (Sıcak Hava Balonu)
    {
        coords: [38.6473, 34.8281],
        id: "balloon",
        en: { n: "HOT AIR BALLOON — GÖREME LAUNCH POINT", w: "Once-in-a-Lifetime Experience", s: "Cappadocia's most iconic activity: a sunrise hot air balloon flight over the fairy chimneys and valleys. Dozens of colorful balloons fill the sky at dawn, creating a magical spectacle.", d: "Book at least 2 days in advance. If your flight is cancelled due to wind, you get a full refund. Watching from Göreme Sunset Point is a free alternative if you can't afford a ticket." },
        fr: { n: "BALLON À AIR CHAUD — POINT DE LANCEMENT", w: "Une expérience unique dans une vie", s: "L'activité la plus emblématique de Cappadoce : un vol en montgolfière au lever du soleil au-dessus des cheminées de fées. Des dizaines de ballons colorés illuminent l'aube.", d: "Réservez au moins 2 jours à l'avance. En cas d'annulation pour vent, remboursement complet. Vous pouvez aussi admirer gratuitement depuis le Göreme Sunset Point." },
        es: { n: "GLOBO AEROSTÁTICO — PUNTO DE LANZAMIENTO", w: "Una experiencia única en la vida", s: "La actividad más icónica de Capadocia: un vuelo al amanecer sobre las chimeneas de hadas. Decenas de globos coloridos llenan el cielo al alba.", d: "Reserva con al menos 2 días de antelación. Reembolso total si se cancela por viento. También puedes verlos gratis desde el Göreme Sunset Point." },
        it: { n: "MONGOLFIERA — PUNTO DI LANCIO GÖREME", w: "Un'esperienza unica nella vita", s: "L'attività più iconica della Cappadocia: un volo in mongolfiera all'alba sulle ciminiere delle fate. Decine di palloni colorati illuminano l'orizzonte.", d: "Prenota almeno 2 giorni prima. Rimborso totale in caso di vento. Puoi anche guardare gratuitamente dal Göreme Sunset Point." },
        ru: { n: "ВОЗДУШНЫЙ ШАР — ТОЧКА СТАРТА ГЁРЕМЕ", w: "Незабываемый опыт всей жизни", s: "Самое культовое занятие в Каппадокии: полёт на воздушном шаре на рассвете над «каминными трубами». Десятки разноцветных шаров расцвечивают небо на заре.", d: "Бронируйте минимум за 2 дня. При отмене из-за ветра — полный возврат средств. Можно бесплатно наблюдать с Göreme Sunset Point." },
        zh: { n: "热气球——格雷梅起飞点", w: "一生一次的体验", s: "卡帕多西亚最标志性的活动：在日出时乘热气球飞越仙女烟囱和峡谷。黎明时分，数十个彩色热气球将天空点缀得如梦似幻。", d: "至少提前2天预订。因风取消可全额退款。如预算有限，可在格雷梅日落观景台免费欣赏气球升空。" },
        ja: { n: "熱気球——ギョレメ打ち上げポイント", w: "一生に一度の体験", s: "カッパドキア最大の名物アクティビティ。夜明けに妖精の煙突の上を飛ぶ熱気球。色とりどりのバルーンが夜明けの空を彩る光景は圧巻。", d: "少なくとも2日前に予約を。風による欠航は全額返金。気球を地上から眺めるならギョレメ・サンセットポイントが無料でおすすめ。" }
    },

    // 8. Ürgüp
    {
        coords: [38.6340, 34.9142],
        id: "urgup",
        en: { n: "ÜRGÜP — WINE & BOUTIQUE TOWN", w: "Best Food, Wine & Accommodation Hub", s: "A charming town with some of the best boutique hotels, restaurants, and wine bars in Cappadocia. The region produces excellent local wines from Emir and Öküzgözü grapes. Ottoman-era stone houses line the streets.", d: "Visit the Ürgüp wine houses in the evening after your day tours. The local Emir white wine is crisp and unique to this volcanic terroir." },
        fr: { n: "ÜRGÜP — VILLE DU VIN & DU CHARME", w: "Meilleur hub gastronomique et hôtelier", s: "Ville charmante avec les meilleures boutique hôtels, restaurants et bars à vins de Cappadoce. La région produit d'excellents vins locaux à base de raisins Emir et Öküzgözü.", d: "Visitez les maisons de vin d'Ürgüp le soir après vos excursions. Le vin blanc Emir local est frais et unique à ce terroir volcanique." },
        es: { n: "ÜRGÜP — VINO Y ENCANTO", w: "Mejor centro gastronómico y hotelero", s: "Encantadora ciudad con los mejores hoteles boutique, restaurantes y bares de vinos de Capadocia. La región produce excelentes vinos locales de uvas Emir y Öküzgözü.", d: "Visita las casas de vino de Ürgüp por la tarde. El vino blanco Emir es fresco y único de este terruño volcánico." },
        it: { n: "ÜRGÜP — VINO E CHARME", w: "Il miglior hub gastronomico e alberghiero", s: "Affascinante città con i migliori boutique hotel, ristoranti e wine bar della Cappadocia. La regione produce ottimi vini locali da uve Emir e Öküzgözü.", d: "Visita le cantine di Ürgüp la sera. Il vino bianco Emir è fresco e unico di questo terroir vulcanico." },
        ru: { n: "УРГЮП — ВИНО И ШАРМ", w: "Лучший гастрономический и отельный центр", s: "Очаровательный городок с лучшими бутик-отелями, ресторанами и винными барами Каппадокии. Регион производит отличные местные вина из сортов Эмир и Окюзгёзю.", d: "Посетите винные дома Ургюпа вечером. Местное белое вино Эмир — освежающее и уникальное для вулканического терруара." },
        zh: { n: "于尔居普——葡萄酒与精品小镇", w: "最佳美食、葡萄酒与住宿中心", s: "拥有卡帕多西亚最好的精品酒店、餐厅和酒吧的迷人小镇。该地区出产由埃米尔和厄屈兹格孜葡萄酿制的优质本地葡萄酒。", d: "日间游览结束后，傍晚探访于尔居普酒庄。当地埃米尔白葡萄酒清爽独特，正是这片火山土地的馈赠。" },
        ja: { n: "ユルギュップ——ワインと魅力の街", w: "最高のグルメ・宿泊ハブ", s: "カッパドキア最高のブティックホテル、レストラン、ワインバーが揃う魅力的な街。エミル種やオキュズゴズ種のブドウから作られる地元ワインは絶品。", d: "日中の観光後、夕方にユルギュップのワイン蔵へ。エミル白ワインは火山土壌ならではのさわやかな味わい。" }
    }
];

var labels = {
    en: { worth: "Expert Recommendation", see: "Description", secret: "Insider Note" },
    fr: { worth: "Recommandation d'expert", see: "Description", secret: "Note locale" },
    es: { worth: "Recomendación experta", see: "Descripción", secret: "Nota interna" },
    it: { worth: "Raccomandazione", see: "Descrizione", secret: "Nota locale" },
    ru: { worth: "Рекомендация", see: "Описание", secret: "Заметка" },
    zh: { worth: "专家推荐", see: "描述", secret: "业内提示" },
    ja: { worth: "専門家の推奨", see: "説明", secret: "インサイダーノート" }
};

locations.forEach(function(loc) {
    var marker = L.marker(loc.coords).addTo(map);
    marker.on('click', function() {
        activePoint = loc;
        updateUI();
    });
});

function updateUI() {
    if(!activePoint) return;

    var d = activePoint[currentLang];
    var l = labels[currentLang];

    document.getElementById('place-name').innerText = d.n;
    document.getElementById('worth-text').innerText = d.w;
    document.getElementById('see-text').innerText = d.s;
    document.getElementById('do-text').innerText = d.d;

    document.getElementById('label-worth').innerText = l.worth;
    document.getElementById('label-see').innerText = l.see;
    document.getElementById('label-secret').innerText = l.secret;

    if(activePoint.wa) {
        document.getElementById('contact-section').style.display = 'block';
        document.getElementById('contact-name').innerText = d.n;
        document.getElementById('wa-link').href = "https://wa.me/" + activePoint.wa;
    } else {
        document.getElementById('contact-section').style.display = 'none';
    }

    var igLink = document.getElementById('ig-link');
    if(activePoint.ig) {
        igLink.href = "https://www.instagram.com/" + activePoint.ig + "/";
        igLink.style.display = 'inline-block';
    } else {
        igLink.style.display = 'none';
    }

    var mapsLink = document.getElementById('maps-link');
    if(activePoint.maps) {
        mapsLink.href = activePoint.maps;
        mapsLink.style.display = 'inline-block';
    } else {
        mapsLink.style.display = 'none';
    }

    document.getElementById('info-card').classList.add('visible');
    document.getElementById('scroll-hint').classList.add('visible');
    setTimeout(function() {
        document.getElementById('scroll-hint').classList.remove('visible');
    }, 4000);
}

function closePanel() {
    document.getElementById('info-card').classList.remove('visible');
    document.getElementById('scroll-hint').classList.remove('visible');
    activePoint = null;
}

function setLang(lang) {
    currentLang = lang;
    document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
    document.getElementById(lang + '-btn').classList.add('active');
    updateUI();
}
</script>

<hr>



<!-- SECTION 2: THE BALLOON BIBLE -->
<h2 style="color: #8b0000;">🎈 The Hot Air Balloon Bible</h2>
<p>The #1 question everyone asks. Let's be honest about how it works:</p>

<table border="0" style="width:100%; background-color: #fffaf0; border: 1px dashed #8b0000; padding: 20px; border-radius: 10px;">
  <tr>
    <td>
      <h3>Why do prices change daily?</h3>
      <p>Think of it like a stock market. Prices depend on: 
      1. Seasonality (May-Oct is peak). 
      2. The "Backlog" (If flights were canceled for 3 days, the 4th day will be very expensive because everyone is waiting).</p>
      
      <h3>The "Flag" System (Red/Yellow/Green)</h3>
      <p>The <strong>SHGM (Civil Aviation Authority)</strong> decides if we fly. 
      - 🟢 <b>Green:</b> We fly! 
      - 🟡 <b>Yellow:</b> Delay/Standby. 
      - 🔴 <b>Red:</b> Canceled. If it's red, no one flies. No exceptions for money or luck.</p>
      
      <h3>Refunds?</h3>
      <p>If the flight is canceled by SHGM, you get a <b>100% full refund</b>. No cancellation fee. Period.</p>
    </td>
  </tr>
</table>

<hr>

<!-- SECTION 3: LOCAL CITIES & VILLAGES -->
<h2 style="color: #2e8b57;">🏘️ Towns You Must Visit</h2>

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-top: 20px;">
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #d4af37;">
    <h4>🌟 Ürgüp</h4>
    <p>The "sophisticated" Cappadocia. Great for dining, high-end boutique hotels, and seeing the "Three Beauties" fairy chimneys.</p>
  </div>
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #2e8b57;">
    <h4>🎨 Avanos</h4>
    <p>My childhood home. Crossed by the Red River. You must try the pottery wheel and walk across the swinging bridge.</p>
  </div>
  <div style="flex: 1; min-width: 250px; background: #f9f9f9; padding: 15px; border-radius: 10px; border-left: 5px solid #8b0000;">
    <h4>⛪ Mustafapaşa</h4>
    <p>A hidden historical treasure. Formerly known as Sinasos, it holds the best examples of 19th-century Greek masonry.</p>
  </div>
</div>

<hr>
<hr style="margin: 40px 0;">

<!-- SECTION: COMPREHENSIVE CULTURAL MAP -->
<div style="text-align: center; background-color: #fffaf0; padding: 30px; border-radius: 20px; border: 1px solid #d4af37;">
  <h2 style="color: #8b0000; margin-top: 0;">🗺️ Cappadocia: Cultural & Activity Roadmap</h2>
  <p style="font-size: 16px; color: #555; max-width: 800px; margin: 10px auto 25px auto;">
    This illustrative map highlights the essential "Cultural Nodes" of our region. From the pottery wheels of <b>Avanos</b> to the underground mysteries of <b>Derinkuyu</b>, every icon represents a thousand-year-old tradition.
  </p>

  <!-- Haritaya tıklandığında tam boyutta yeni sekmede açılır -->
  <a href="./map_.jpg" target="_blank" title="Click to view full-size cultural map">
    <img src="./map_.jpg" alt="Cappadocia Cultural Map" style="width: 100%; max-width: 900px; border-radius: 15px; box-shadow: 0 12px 25px rgba(0,0,0,0.25); cursor: zoom-in;" loading="lazy">
  </a>

  <div style="margin-top: 20px; display: flex; justify-content: center; gap: 20px; flex-wrap: wrap;">
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">🏺 <b>Artisan Workshops</b></span>
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">⛪ <b>Historical Sites</b></span>
    <span style="background: #fdf5e6; padding: 5px 15px; border-radius: 50px; font-size: 14px; border: 1px solid #eee;">🐎 <b>Outdoor Adventure</b></span>
  </div>
  
  <p style="margin-top: 15px; font-size: 13px; color: #8b0000;">
    <strong>💡 Insider Tip:</strong> Click on the map to enlarge and see the specific locations of carpet workshops and secret valleys.
  </p>
</div>

<hr style="margin: 40px 0;">
<!-- SECTION 4: MUSEUMS & HIDDEN GEMS -->
<h2 style="color: #d4af37;">🏛️ Museums & Valleys</h2>
<ul>
  <li><strong>Göreme Open Air Museum:</strong> The mandatory stop for rock-cut churches and frescoes.</li>
  <li><strong>Zelve Open Air Museum:</strong> Much larger and more "wild" than Göreme. Great for hiking without huge crowds.</li>
  <li><strong>Bayramhacı (Curator's Choice):</strong> My birthplace. If you want a break from rocks, come here for the natural hot springs and thermal healing.</li>
  <li><strong>Ihlara Valley:</strong> A 14km hike through a lush canyon with 100+ churches.</li>
</ul>

<hr>

<!-- SECTION 5: ADVENTURE -->
<h2 style="color: #e67e22;">🐎 Adventure Tours</h2>
<p>If you have extra time, try these:</p>
<table border="0" style="width:100%;">
  <tr>
    <td style="width: 50%; padding: 10px;">
      <b>Horseback Riding:</b> Cappadocia means "Land of Beautiful Horses." Sunset tours in the valleys are magic.
    </td>
    <td style="width: 50%; padding: 10px;">
      <b>ATV / Quad Safari:</b> Best for the "Sword Valley" and "Love Valley" trails if you like adrenaline and dust!
    </td>
  </tr>
</table>

<hr>

<div style="text-align: center; background-color: #2c3e50; color: white; padding: 20px; border-radius: 10px;">
  <h3>Need more local advice?</h3>
  <p>As a local active in Göreme, I'm here to help you understand the true culture behind the fairy chimneys.</p>
  <a href="./me" style="color: #d4af37; font-weight: bold;">Learn more about me & my French courses</a>
</div>

<p style="text-align: center; margin-top: 30px;">
  <a href="./">🏠 Return to Main Dashboard</a> | <a href="./en/handknotted">🧶 Technical Carpet Guide</a>
</p>
