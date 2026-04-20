---
layout: default
title: Carpet Materials, Tools & Techniques
---

<style>
  body { font-family: Georgia, serif; }

  .page-hero { text-align: center; margin-bottom: 40px; }
  .page-hero h1 { color: #8b0000; font-size: 1.85em; margin-bottom: 8px; }
  .page-hero p  { color: #666; font-style: italic; font-size: 0.97em; max-width: 620px; margin: 0 auto; }

  /* SECTION */
  .mat-section { margin-bottom: 55px; }
  .mat-section h2 { color: #8b0000; border-bottom: 3px solid #d4af37; padding-bottom: 8px; margin-bottom: 24px; font-size: 1.45em; }
  .mat-section h3 { color: #8b4513; font-size: 1.05em; margin: 22px 0 8px; }
  .mat-section p  { color: #2c3e50; line-height: 1.85; font-size: 0.95em; margin-bottom: 12px; }

  /* MATERIAL CARD — resimli */
  .mat-card {
    display: flex; gap: 24px; align-items: flex-start;
    background: #fff; border-radius: 14px; padding: 22px;
    border: 1px solid #ede8df; box-shadow: 0 4px 14px rgba(0,0,0,0.07);
    margin-bottom: 22px;
  }
  .mat-card.reverse { flex-direction: row-reverse; }
  .mat-card-img {
    width: 200px; min-width: 200px; height: 180px;
    object-fit: cover; border-radius: 10px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.12);
  }
  .mat-card-body h3 { margin: 0 0 8px; color: #8b0000; font-size: 1.1em; }
  .mat-card-body p  { margin: 0 0 8px; font-size: 0.92em; color: #2c3e50; line-height: 1.8; }
  .mat-badge {
    display: inline-block; padding: 3px 12px; border-radius: 50px;
    font-size: 0.75em; font-weight: bold; margin: 0 4px 6px 0; color: white;
  }
  @media (max-width: 600px) {
    .mat-card, .mat-card.reverse { flex-direction: column; }
    .mat-card-img { width: 100%; min-width: unset; height: 200px; }
  }

  /* TOOL GRID */
  .tool-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 20px; margin-top: 16px; }
  .tool-card {
    background: #fff; border-radius: 14px; overflow: hidden;
    border: 1px solid #ede8df; box-shadow: 0 4px 14px rgba(0,0,0,0.07);
    display: flex; flex-direction: column;
  }
  .tool-card-img { width: 100%; height: 200px; object-fit: cover; }
  .tool-card-body { padding: 16px; flex: 1; }
  .tool-card-body h3 { margin: 0 0 6px; color: #8b0000; font-size: 1em; }
  .tool-card-name-tr { font-size: 0.8em; color: #8b4513; font-style: italic; margin-bottom: 8px; display: block; }
  .tool-card-body p  { margin: 0; font-size: 0.87em; color: #444; line-height: 1.7; }

  /* PROCESS STEPS */
  .process-steps { counter-reset: steps; list-style: none; padding: 0; margin: 20px 0; }
  .process-steps li {
    counter-increment: steps;
    display: flex; gap: 16px; align-items: flex-start;
    background: #fdf5e6; border-left: 4px solid #d4af37;
    border-radius: 0 10px 10px 0; padding: 14px 16px;
    margin-bottom: 10px; font-size: 0.93em; color: #2c3e50; line-height: 1.75;
  }
  .process-steps li::before {
    content: counter(steps);
    background: #8b0000; color: white;
    font-weight: bold; border-radius: 50%;
    min-width: 28px; height: 28px;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.85em; flex-shrink: 0;
  }

  /* LOOM TYPES */
  .loom-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 18px; margin-top: 16px; }
  .loom-card {
    background: linear-gradient(135deg, #fdf5e6, #fffbf0);
    border: 1px solid #d4af37; border-radius: 14px; padding: 18px 20px;
  }
  .loom-card h3 { color: #8b0000; margin: 0 0 8px; font-size: 1em; }
  .loom-card p  { margin: 0; font-size: 0.87em; color: #3d2000; line-height: 1.7; }

  /* DYE TABLE */
  .dye-table { width: 100%; border-collapse: collapse; margin: 16px 0; font-size: 0.9em; }
  .dye-table th { background: #8b0000; color: white; padding: 10px 14px; text-align: left; }
  .dye-table td { padding: 10px 14px; border-bottom: 1px solid #ede8df; color: #2c3e50; vertical-align: top; }
  .dye-table tr:nth-child(even) td { background: #fdf5e6; }

  .divider { border: none; border-top: 2px dashed #d4af37; margin: 40px 0; }

  /* KNOT COMPARISON */
  .knot-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 16px; }
  .knot-card {
    border-radius: 14px; padding: 20px;
    border: 1px solid #ede8df; text-align: center;
  }
  .knot-card.turkish { background: linear-gradient(135deg, #fff0f0, #fde8e8); border-top: 4px solid #8b0000; }
  .knot-card.persian { background: linear-gradient(135deg, #f0f0ff, #e8e8fd); border-top: 4px solid #1a2a6c; }
  .knot-card h3 { margin: 0 0 8px; font-size: 1.05em; }
  .knot-card.turkish h3 { color: #8b0000; }
  .knot-card.persian h3 { color: #1a2a6c; }
  .knot-card p { margin: 0; font-size: 0.87em; color: #444; line-height: 1.7; }
  @media (max-width: 500px) { .knot-grid { grid-template-columns: 1fr; } }
</style>

<!-- HERO -->
<div class="page-hero">
  <h1>🧵 Materials, Tools & Techniques</h1>
  <p>From raw wool on the hillside to a finished masterpiece on the loom — every step matters.</p>
</div>

<!-- ═══════════════════════════════ -->
<!-- 1. MALZEMELER                   -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>🐑 The Raw Materials</h2>

  <!-- YÜN -->
  <div class="mat-card">
    <img src="{{ site.baseurl }}/images/wool-spinning.jpg"
         onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/Wool_fleece.jpg/640px-Wool_fleece.jpg'"
         class="mat-card-img" alt="Wool">
    <div class="mat-card-body">
      <h3>🐑 Wool — Yün</h3>
      <span class="mat-badge" style="background:#8b4513;">Most Common</span>
      <span class="mat-badge" style="background:#2e8b57;">Natural Fibre</span>
      <p>Wool is the backbone of Anatolian carpet weaving. The finest quality comes from sheep raised at high altitude, where cold winters produce a dense, lustrous fleece with long, strong fibres. Wool holds natural dyes beautifully — colours often deepen and improve with age, a quality absent in synthetic fibres.</p>
      <p><strong>Kurk (Kırkım yünü):</strong> The highest grade — first spring shearing from the neck and belly. Silky, long-stapled, and luminous. Used in premium village carpets.<br>
      <strong>Ordinary wool:</strong> Later shearings — shorter fibre, more common in commercial production.</p>
      <p><strong>Best regions:</strong> Taurus mountain Yörük wool (Döşemealtı, Ayvacık), Kars highland wool.</p>
    </div>
  </div>

  <!-- İPEK -->
  <div class="mat-card reverse">
    <img src="{{ site.baseurl }}/images/silk-thread.jpg"
         onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Silk_thread.jpg/640px-Silk_thread.jpg'"
         class="mat-card-img" alt="Silk">
    <div class="mat-card-body">
      <h3>🥚 Silk — İpek</h3>
      <span class="mat-badge" style="background:#d4af37; color:#1a0a0a;">Luxury</span>
      <span class="mat-badge" style="background:#8b0000;">Hereke</span>
      <p>Silk is the most prestigious carpet fibre — fine enough to achieve over 2 million knots per square metre, yet stronger than steel for its weight. Silk carpets shimmer and change colour with viewing angle; no other material replicates this effect.</p>
      <p><strong>Source:</strong> Silkworm (Bombyx mori) cocoons, fed exclusively on mulberry leaves. A single cocoon yields up to 1,500 metres of continuous thread.<br>
      <strong>Silk on Silk:</strong> Both warp and pile are silk — maximum fineness, maximum cost.<br>
      <strong>Silk on Cotton:</strong> Cotton warp with silk pile — slightly less fine but more stable.</p>
      <p><strong>Primary centre:</strong> Hereke (Kocaeli). Also Kayseri for commercial silk blends.</p>
    </div>
  </div>

  <!-- PAMUK -->
  <div class="mat-card">
    <img src="{{ site.baseurl }}/images/cotton-warp.jpg"
         onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Cotton_plant.jpg/640px-Cotton_plant.jpg'"
         class="mat-card-img" alt="Cotton">
    <div class="mat-card-body">
      <h3>🌿 Cotton — Pamuk</h3>
      <span class="mat-badge" style="background:#1a2a6c;">Warp & Weft</span>
      <span class="mat-badge" style="background:#555;">Foundation</span>
      <p>Cotton is rarely used for pile but is widely used as the <strong>warp and weft foundation</strong> in town carpets (Kayseri, Isparta, Sivas). It provides a more stable, less elastic foundation than wool, enabling finer knotting. Cotton warps do not stretch with humidity like wool.</p>
      <p>Cotton pile appears in a few specific traditions — notably the white highlight knots in some Hereke and city carpets, where its bright, stable white cannot be replicated by wool.</p>
    </div>
  </div>

  <!-- KEÇI KILI -->
  <div class="mat-card reverse">
    <img src="{{ site.baseurl }}/images/goat-hair.jpg"
         onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Domestic_goat_kid_in_capeweed.jpg/640px-Domestic_goat_kid_in_capeweed.jpg'"
         class="mat-card-img" alt="Goat hair">
    <div class="mat-card-body">
      <h3>🐐 Goat Hair & Camel Hair</h3>
      <span class="mat-badge" style="background:#c0392b;">Tribal</span>
      <span class="mat-badge" style="background:#8b4513;">Nomadic</span>
      <p>Used primarily in tribal and nomadic weaving — flat-weaves, storage bags (heybe), tent dividers. Goat hair (kıl) is exceptionally strong and weather-resistant; it does not absorb moisture like wool.</p>
      <p><strong>Camel hair (deve tüyü):</strong> Prized for its natural golden-brown tones. Used in some Kayseri and eastern Anatolian carpets. Cannot be dyed — its natural colour is its beauty.</p>
      <p><strong>Found in:</strong> Kars kilims, Yörük weavings, Ayvacık tribal pieces.</p>
    </div>
  </div>

</div>

<hr class="divider">

<!-- ═══════════════════════════════ -->
<!-- 2. BOYALAR                      -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>🎨 Natural Dyes — Doğal Boyalar</h2>
  <p>For centuries, Anatolian weavers dyed their yarns exclusively with plants, insects, and minerals. These natural dyes do not fade uniformly — they develop a <strong>patina</strong> over time, colours deepening and harmonising in a way synthetic dyes never achieve. The DOBAG project (1981, Ayvacık) was the first modern initiative to revive 100% natural dye carpet weaving in Turkey.</p>

  <table class="dye-table">
    <thead>
      <tr><th>Plant / Source</th><th>Colour</th><th>Turkish Name</th><th>Notes</th></tr>
    </thead>
    <tbody>
      <tr><td>🌹 Madder root (Rubia tinctorum)</td><td>Red, orange, pink tones</td><td>Kökboya</td><td>The most important dye plant. Yağcıbedir reds are legendary for brightening with age.</td></tr>
      <tr><td>🔵 Indigo (Indigofera tinctoria)</td><td>Blue, navy, turquoise</td><td>Çivit</td><td>Used via vat dyeing. Combined with madder to produce purple.</td></tr>
      <tr><td>🌿 Weld (Reseda luteola)</td><td>Yellow, gold</td><td>Muhabbet çiçeği</td><td>Most common yellow dye plant. Also used in overdyeing for green (with indigo).</td></tr>
      <tr><td>🌰 Oak galls & iron</td><td>Black, dark brown</td><td>Mazı / Demir suyu</td><td>Iron mordant with tannin. Excess iron can weaken wool fibres over time — antique black areas often show corrosion.</td></tr>
      <tr><td>🧅 Onion skins</td><td>Golden yellow, orange</td><td>Soğan kabuğu</td><td>Widely available, easy to use. Produces warm golden tones.</td></tr>
      <tr><td>🌿 Pomegranate rind</td><td>Yellow-green, beige</td><td>Nar kabuğu</td><td>Also acts as a mordant. Common in Milas and Aegean weaving.</td></tr>
      <tr><td>🌲 Walnut shells / husks</td><td>Brown, khaki</td><td>Ceviz kabuğu</td><td>No mordant needed. Very lightfast and stable.</td></tr>
      <tr><td>🧪 Alum (mordant)</td><td>—</td><td>Şap</td><td>Most common mordant. Opens wool fibre to accept dye. Essential for madder and most plant dyes.</td></tr>
    </tbody>
  </table>

  <div style="background: #fdf5e6; border-left: 5px solid #8b0000; border-radius: 0 12px 12px 0; padding: 16px 20px; margin-top: 10px; font-size: 0.92em; color: #3d2000; line-height: 1.8;">
    <strong>Curator's Note:</strong> "The colour of a carpet tells you its age. Synthetic dyes (aniline, chrome) arrived in Anatolia around 1860–1880. Any carpet with perfectly uniform, bright colours and no patina is likely post-1880. The soft, complex hues of a pre-1880 carpet — where red is never simply red, but a hundred shades in one — come only from kökboya and çivit."
    <br><em>— Fatih Mehmet Canıtez</em>
  </div>
</div>

<hr class="divider">

<!-- ═══════════════════════════════ -->
<!-- 3. TEZGAH TÜRLERİ              -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>🏗️ Loom Types — Tezgah Çeşitleri</h2>
  <p>The loom (tezgah) is the fundamental structure that holds the warp threads under tension while the weaver ties knots. Different loom types suit different contexts — nomadic life, village workshops, or imperial factories.</p>

  <div class="loom-grid">
    <div class="loom-card">
      <h3>📐 Horizontal Ground Loom<br><small style="color:#8b4513;">Yatay Tezgah</small></h3>
      <p>The oldest and simplest type. Staked to the ground, low to the floor. Ideal for nomadic life — easily dismantled and transported. Produces relatively small rugs with slightly uneven tension. Found in tribal and Yörük weaving.</p>
    </div>
    <div class="loom-card">
      <h3>📐 Fixed Village Loom<br><small style="color:#8b4513;">Sabit Köy Tezgahı</small></h3>
      <p>Vertical loom with a fixed upper beam and movable lower beam. Tension maintained with wooden wedges. Weavers sit on a plank raised as work progresses. Standard in Anatolian village production.</p>
    </div>
    <div class="loom-card">
      <h3>📐 Roller Beam Loom<br><small style="color:#8b4513;">Döner Leventli Tezgah</small></h3>
      <p>Traditional Turkish village loom. Two movable beams with ratchet locks — completed work rolls onto the lower beam. Allows very long carpets. Used in Yağcıbedir, Döşemealtı, and many Anatolian centres.</p>
    </div>
    <div class="loom-card">
      <h3>📐 Tabriz / Bünyan Loom<br><small style="color:#8b4513;">Tabriz Tezgahı</small></h3>
      <p>Continuous warps pass around behind the loom. Carpet is pulled down and rolled as work progresses; weavers sit on a fixed seat. Used in professional workshops — Kayseri, Bünyan, Hereke. Enables very precise, uniform weaving.</p>
    </div>
  </div>
</div>

<hr class="divider">

<!-- ═══════════════════════════════ -->
<!-- 4. ARAÇ GEREÇLER               -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>🔧 Weaving Tools — Dokuma Araçları</h2>
  <p>Each tool in the weaver's hands has been refined over centuries. Together they form a complete system — from preparing the warp to finishing the pile.</p>

  <div class="tool-grid">

    <div class="tool-card">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/Weaving_loom.jpg/640px-Weaving_loom.jpg"
           onerror="this.src='{{ site.baseurl }}/images/loom.jpg'"
           class="tool-card-img" alt="Tezgah">
      <div class="tool-card-body">
        <h3>Loom</h3>
        <span class="tool-card-name-tr">Tezgah</span>
        <p>The main frame that holds warp threads under tension. The foundation of all carpet and kilim production. Can be horizontal (nomadic) or vertical (village/workshop). Size determines the maximum carpet dimensions.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/kirkit.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Carpet_weaving_tools.jpg/640px-Carpet_weaving_tools.jpg'"
           class="tool-card-img" alt="Kirkit">
      <div class="tool-card-body">
        <h3>Weaving Comb / Beater</h3>
        <span class="tool-card-name-tr">Kirkit</span>
        <p>A heavy comb-like tool — typically metal-toothed with a wooden or metal handle. After each row of knots is tied and the weft thread passed through, the kirkit is struck downward to pack the knots tightly together. The density of the blow determines the carpet's firmness and knot count. One of the most characteristic sounds of a carpet workshop.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/carpet-knife.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Rug_weaving_knife.jpg/640px-Rug_weaving_knife.jpg'"
           class="tool-card-img" alt="Bıçak">
      <div class="tool-card-body">
        <h3>Weaving Knife</h3>
        <span class="tool-card-name-tr">Dokuma Bıçağı</span>
        <p>A small hooked knife used to cut the yarn after each knot is tied around the warp threads. The hook allows quick cutting at a consistent length. Skilled weavers can tie and cut up to 10,000 knots per day. The sharpness of the knife directly affects pile uniformity.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/carpet-scissors.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/a/a9/Rug_shearing.jpg/640px-Rug_shearing.jpg'"
           class="tool-card-img" alt="Makas">
      <div class="tool-card-body">
        <h3>Pile Scissors</h3>
        <span class="tool-card-name-tr">Hav Makası</span>
        <p>Wide, adjustable scissors used to shear the pile to an even height after each completed row — and for the final finishing of the whole carpet. The pile height determines the carpet's texture: low pile gives crisp pattern definition; higher pile gives softness and warmth.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/spindle.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/1/12/Spindles_and_yarn.jpg/640px-Spindles_and_yarn.jpg'"
           class="tool-card-img" alt="İğ / İğlik">
      <div class="tool-card-body">
        <h3>Drop Spindle</h3>
        <span class="tool-card-name-tr">İğ / Kirmen</span>
        <p>A weighted stick used to spin raw wool fibre into yarn by hand. In traditional production, women spun all yarn by hand before weaving. The twist of the yarn (S-twist or Z-twist) affects the carpet's texture and light reflection. Hand-spun yarn has natural irregularities that give antique carpets their characteristic warmth.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/varagele.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Weaving_shed_stick.jpg/640px-Weaving_shed_stick.jpg'"
           class="tool-card-img" alt="Varagele">
      <div class="tool-card-body">
        <h3>Shed Stick / Heddle</h3>
        <span class="tool-card-name-tr">Varagele / Çerçeve</span>
        <p>A flat wooden stick or rod inserted between alternate warp threads to create the "shed" — the opening through which the weft thread passes. In kilim and flat-weave, the varagele is raised and lowered to alternate which warps are lifted, creating the interlocking weft patterns.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/warping-frame.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Warping_mill.jpg/640px-Warping_mill.jpg'"
           class="tool-card-img" alt="Çözgü">
      <div class="tool-card-body">
        <h3>Warping Frame</h3>
        <span class="tool-card-name-tr">Çözgü Levent / Tahar</span>
        <p>Used to prepare the warp — measuring and organising the warp threads to the correct length and density before they are stretched onto the loom. Proper warping is critical: uneven tension in the warp produces a distorted carpet that will not lie flat.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/dye-pot.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Natural_dye_pot.jpg/640px-Natural_dye_pot.jpg'"
           class="tool-card-img" alt="Boya Kazanı">
      <div class="tool-card-body">
        <h3>Dye Vat</h3>
        <span class="tool-card-name-tr">Boya Kazanı</span>
        <p>A large copper or iron cauldron used to dye yarn. Wool is first mordanted (usually in alum solution), then submerged in the dye bath. Temperature, duration, and mordant type all affect the final colour. Natural dyeing is an art requiring deep knowledge of plant chemistry.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/wool-comb.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Wool_cards.jpg/640px-Wool_cards.jpg'"
           class="tool-card-img" alt="Yün Tarağı">
      <div class="tool-card-body">
        <h3>Wool Cards / Comb</h3>
        <span class="tool-card-name-tr">Yün Tarağı / Tarama</span>
        <p>Flat paddles or combs with wire teeth used to align and clean raw wool fibres before spinning. Carding removes vegetable matter, loosens fibres, and aligns them for even spinning. Traditionally done by women by hand — a fundamental step that determines yarn quality.</p>
      </div>
    </div>

    <div class="tool-card">
      <img src="{{ site.baseurl }}/images/cartoon-paper.jpg"
           onerror="this.src='https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Carpet_design_cartoon.jpg/640px-Carpet_design_cartoon.jpg'"
           class="tool-card-img" alt="Desen Kartonu">
      <div class="tool-card-body">
        <h3>Design Cartoon</h3>
        <span class="tool-card-name-tr">Desen Kartonu / Nakış Kağıdı</span>
        <p>A graph-paper design drawn to scale, with each square representing one knot. The weaver follows this colour-coded chart row by row. In village and tribal weaving, patterns are memorised and passed down orally; the cartoon is used in workshop and palace production for complex designs.</p>
      </div>
    </div>

  </div>
</div>

<hr class="divider">

<!-- ═══════════════════════════════ -->
<!-- 5. DÜĞÜM TİPLERİ               -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>🪢 Knot Types — Düğüm Çeşitleri</h2>
  <p>The knot is the fundamental unit of a hand-knotted carpet. Each knot is a short length of pile yarn tied around one or two warp threads. The type, density, and direction of knots determine the carpet's quality, durability, and pattern sharpness.</p>

  <div class="knot-grid">
    <div class="knot-card turkish">
      <h3>🔴 Turkish Knot (Symmetrical)<br><small>Gördes Düğümü / Türk Düğümü</small></h3>
      <p>Yarn is looped around <strong>two adjacent warp threads</strong>, with both ends emerging between them. Produces a symmetrical, firm knot that stands upright. Stronger, more durable, and gives sharper geometric patterns. Standard in all Anatolian weaving from Gördes to Hereke.</p>
      <br>
      <p><em>Used in: Hereke, Gördes, Uşak, Bergama, Kayseri, and all major Turkish centres.</em></p>
    </div>
    <div class="knot-card persian">
      <h3>🔵 Persian Knot (Asymmetrical)<br><small>Sine Düğümü / İran Düğümü</small></h3>
      <p>Yarn loops around <strong>one warp thread</strong>, with one end tucked under the adjacent warp. Asymmetrical — can be open left or right. Allows higher knot density and very fine curved designs, but slightly less firm than the Turkish knot. Standard in Persian and some Central Asian weaving.</p>
      <br>
      <p><em>Used in: Some Hereke silk carpets at ultra-high density, Iranian-influenced pieces.</em></p>
    </div>
  </div>

  <h3>📊 Knot Density — What the Numbers Mean</h3>
  <table class="dye-table">
    <thead>
      <tr><th>Quality Level</th><th>Knots per dm²</th><th>Knots per m²</th><th>Typical Use</th></tr>
    </thead>
    <tbody>
      <tr><td>Village / Tribal</td><td>900–1,600</td><td>90,000–160,000</td><td>Yörük carpets, Döşemealtı, Çanakkale</td></tr>
      <tr><td>Good Commercial</td><td>1,600–2,500</td><td>160,000–250,000</td><td>Isparta, Kayseri commercial</td></tr>
      <tr><td>Fine Workshop</td><td>2,500–4,900</td><td>250,000–490,000</td><td>Sivas, Kayseri fine, Ladik</td></tr>
      <tr><td>Hereke Wool</td><td>3,600</td><td>360,000</td><td>Hereke wool — official standard (60×60)</td></tr>
      <tr><td>Hereke Silk</td><td>10,000+</td><td>1,000,000+</td><td>Hereke silk — standard (100×100)</td></tr>
      <tr><td>Hereke Ultra-Fine</td><td>22,500</td><td>2,250,000</td><td>Finest Hereke silk — museum quality</td></tr>
    </tbody>
  </table>
</div>

<hr class="divider">

<!-- ═══════════════════════════════ -->
<!-- 6. ÜRETİM SÜRECİ               -->
<!-- ═══════════════════════════════ -->
<div class="mat-section">
  <h2>⚙️ The Production Process — Üretim Aşamaları</h2>
  <p>From raw wool to finished carpet — a traditional Anatolian hand-knotted carpet passes through eight distinct stages, each requiring specialised knowledge.</p>

  <ol class="process-steps">
    <li><strong>Shearing (Kırkım):</strong> Wool is sheared from the sheep — ideally in spring for the finest kurk quality. The fleece is washed, sorted by fibre length and quality.</li>
    <li><strong>Carding (Tarama):</strong> Cleaned wool is combed with wire cards to align fibres, remove debris, and prepare for spinning.</li>
    <li><strong>Spinning (Eğirme):</strong> Fibres are twisted into yarn using a drop spindle (iğ) or spinning wheel. The twist direction (S or Z) and tightness affect the yarn's character and the carpet's sheen.</li>
    <li><strong>Mordanting (Mordan):</strong> Spun yarn is boiled in a mordant solution (usually alum/şap) to prepare it to accept dye. Different mordants shift the same dye to different colours.</li>
    <li><strong>Dyeing (Boyama):</strong> Mordanted yarn is submerged in the dye bath and simmered. Temperature, duration, and dye concentration are controlled by the dyer's experience. Yarn is then rinsed and hung to dry in the sun.</li>
    <li><strong>Warping (Çözgü):</strong> Warp threads are measured, tensioned, and mounted on the loom. Correct warping is critical — uneven tension produces a distorted carpet.</li>
    <li><strong>Knotting (Düğümleme):</strong> The weaver ties each knot individually around the warp threads, row by row, following the design. After each row: a weft thread is passed through, then the kirkit is used to beat the row firmly downward. Pile is trimmed with scissors to maintain even height.</li>
    <li><strong>Finishing (Bitirme):</strong> The completed carpet is cut from the loom. Ends are secured, the pile is sheared to final height and evenness, the carpet is washed in running water, and dried flat in the sun. The wash softens the wool and brings out the natural lustre of the dyes.</li>
  </ol>
</div>

<hr class="divider">

<!-- NAVIGATION -->
<div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center;">
  <a href="{{ site.baseurl }}/en/hereke"    style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🏰 Imperial Hereke →</a>
  <a href="{{ site.baseurl }}/en/kilim"     style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">📐 Kilim Guide →</a>
  <a href="{{ site.baseurl }}/carpet-map"   style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🗺️ Regional Map →</a>
  <a href="{{ site.baseurl }}/cleaning"     style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🧹 Care Guide →</a>
</div>
