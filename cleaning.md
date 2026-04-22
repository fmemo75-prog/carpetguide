---
layout: default
title: Carpet & Kilim Care Guide
---

<style>
  .care-intro { max-width: 860px; margin: 0 auto 40px; font-family: 'Georgia', serif; }
  .care-intro p { color: #2c3e50; line-height: 1.85; font-size: 0.97em; margin-bottom: 14px; }

  /* SECTION HEADER */
  .care-section { max-width: 860px; margin: 0 auto 50px; }
  .care-section h2 { color: #8b0000; border-bottom: 3px solid #d4af37; padding-bottom: 8px; margin-bottom: 22px; font-size: 1.45em; font-family: 'Georgia', serif; }
  .care-section h3 { color: #8b4513; font-size: 1.05em; margin: 24px 0 8px; font-family: 'Georgia', serif; }
  .care-section p  { color: #2c3e50; line-height: 1.85; font-size: 0.95em; margin-bottom: 12px; }

  /* MATERIAL TABS */
  .material-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 18px; margin: 20px 0; }
  .material-card {
    border-radius: 14px; padding: 20px;
    border: 1px solid #ede8df;
    box-shadow: 0 3px 10px rgba(0,0,0,0.06);
    font-family: 'Georgia', serif;
  }
  .material-card.silk   { background: linear-gradient(135deg, #fffbf0, #fdf5e6); border-top: 4px solid #d4af37; }
  .material-card.wool   { background: linear-gradient(135deg, #f5f0ea, #ede5d8); border-top: 4px solid #8b4513; }
  .material-card.kilim  { background: linear-gradient(135deg, #f0f5f0, #e8f0e8); border-top: 4px solid #2e8b57; }
  .material-card h3 { margin: 0 0 10px; font-size: 1.05em; }
  .material-card.silk  h3 { color: #8b6914; }
  .material-card.wool  h3 { color: #8b4513; }
  .material-card.kilim h3 { color: #2e8b57; }
  .material-card ul { padding-left: 18px; margin: 0; font-size: 0.88em; color: #3d3020; line-height: 1.8; }

  /* STAIN EMERGENCY */
  .emergency-box {
    background: linear-gradient(135deg, #3d0000, #6b0f0f);
    border-radius: 14px; padding: 26px 28px; color: white; margin: 20px 0;
    font-family: 'Georgia', serif;
  }
  .emergency-box h3 { color: #d4af37; margin: 0 0 14px; font-size: 1.15em; }
  .emergency-steps { counter-reset: steps; list-style: none; padding: 0; margin: 0; }
  .emergency-steps li {
    counter-increment: steps;
    display: flex; gap: 14px; align-items: flex-start;
    margin-bottom: 12px; font-size: 0.93em; line-height: 1.7; color: rgba(255,255,255,0.9);
  }
  .emergency-steps li::before {
    content: counter(steps);
    background: #d4af37; color: #1a0a0a;
    font-weight: bold; border-radius: 50%;
    min-width: 24px; height: 24px;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.85em; flex-shrink: 0; margin-top: 2px;
  }

  /* NEVER DO */
  .never-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 14px; margin: 20px 0; }
  .never-item {
    background: #fff5f5; border: 1px solid #f5c0c0; border-radius: 12px;
    padding: 14px 16px; font-size: 0.88em; color: #5a1a1a;
    font-family: 'Georgia', serif; line-height: 1.6;
    display: flex; gap: 10px; align-items: flex-start;
  }
  .never-icon { font-size: 1.3em; flex-shrink: 0; }

  /* DO LIST */
  .do-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 14px; margin: 20px 0; }
  .do-item {
    background: #f0faf0; border: 1px solid #b0d8b0; border-radius: 12px;
    padding: 14px 16px; font-size: 0.88em; color: #1a3a1a;
    font-family: 'Georgia', serif; line-height: 1.6;
    display: flex; gap: 10px; align-items: flex-start;
  }
  .do-icon { font-size: 1.3em; flex-shrink: 0; }

  /* STORAGE */
  .storage-steps { list-style: none; padding: 0; margin: 0; counter-reset: store; }
  .storage-steps li {
    counter-increment: store;
    background: #fdf5e6; border-left: 4px solid #d4af37;
    border-radius: 0 10px 10px 0; padding: 12px 16px;
    margin-bottom: 10px; font-size: 0.92em; color: #2c3e50;
    line-height: 1.75; font-family: 'Georgia', serif;
    display: flex; gap: 14px; align-items: flex-start;
  }
  .storage-steps li::before {
    content: counter(store);
    background: #8b0000; color: white;
    font-weight: bold; border-radius: 50%;
    min-width: 26px; height: 26px;
    display: flex; align-items: center; justify-content: center;
    font-size: 0.85em; flex-shrink: 0;
  }

  /* CURATOR NOTE */
  .curator-note {
    background: #fdf5e6; border-left: 5px solid #8b0000;
    border-radius: 0 14px 14px 0; padding: 20px 24px;
    margin: 30px 0; font-style: italic; color: #3d2000;
    font-size: 0.96em; line-height: 1.85; font-family: 'Georgia', serif;
  }
  .curator-note cite { display: block; margin-top: 10px; font-style: normal; font-weight: bold; color: #8b0000; font-size: 0.88em; }

  /* FREQUENCY TABLE */
  .freq-table { width: 100%; border-collapse: collapse; margin: 20px 0; font-family: 'Georgia', serif; font-size: 0.9em; }
  .freq-table th { background: #8b0000; color: white; padding: 10px 14px; text-align: left; }
  .freq-table td { padding: 10px 14px; border-bottom: 1px solid #ede8df; color: #2c3e50; vertical-align: top; }
  .freq-table tr:nth-child(even) td { background: #fdf5e6; }

  /* DIVIDER */
  .section-divider { border: none; border-top: 2px dashed #d4af37; margin: 40px 0; }
</style>

<!-- HERO BAŞLIK -->
<div style="text-align: center; margin-bottom: 40px;">
  <h1 style="color: #8b0000; font-family: 'Georgia', serif; font-size: 2em; margin-bottom: 10px;">🧹 Carpet & Kilim Care Guide</h1>
  <p style="color: #666; font-size: 1em; font-style: italic; max-width: 600px; margin: 0 auto;">A hand-knotted carpet is a living textile. Treat it well, and it will outlast you by centuries.</p>
</div>

<!-- GİRİŞ -->
<div class="care-intro">
  <p>
    Anatolian carpets and kilims are not simply floor coverings — they are woven archives of culture, labour, and artistry. A single square metre of a Hereke silk carpet may contain over a million hand-tied knots, each one placed with precision by a master weaver. A village kilim may have taken months to complete, its motifs carrying meanings passed down through generations.
  </p>
  <p>
    Caring for these pieces is not complicated, but it requires understanding the material you are working with. The rules for a silk Hereke are quite different from those for a robust village wool kilim. This guide, written from 50 years of experience in Cappadocia's carpet workshops, gives you the practical knowledge to keep your piece beautiful for decades to come.
  </p>
</div>

<hr class="section-divider">

<!-- MALZEMEYE GÖRE BAKIM -->
<div class="care-section">
  <h2>🧵 Care by Material Type</h2>
  <p>Before anything else, identify what your carpet is made of — the fibre determines everything.</p>

  <div class="material-grid">

    <div class="material-card silk">
      <h3>🥚 Silk Carpets</h3>
      <ul>
        <li>Never vacuum with a beater bar or powerhead</li>
        <li>Use dry cleaning method only for home care</li>
        <li>Club soda for fresh spills — blot, never rub</li>
        <li>Never soak: silk absorbs moisture and will stretch permanently</li>
        <li>No hot water, no steam cleaning</li>
        <li>Always professional cleaning for stains</li>
        <li>Baking soda to neutralise odours — leave 1 hour, vacuum gently</li>
      </ul>
    </div>

    <div class="material-card wool">
      <h3>🐑 Wool Carpets</h3>
      <ul>
        <li>Vacuum both sides monthly — low suction, no beater bar</li>
        <li>Avoid alkaline detergents and bleach</li>
        <li>Use pH-neutral, wool-specific cleaner for washing</li>
        <li>Avoid hot water — lukewarm only</li>
        <li>Dry flat in shade, never in direct strong sun</li>
        <li>Rotate every 3–6 months for even wear</li>
        <li>Professional deep clean every 3–5 years</li>
      </ul>
    </div>

    <div class="material-card kilim">
      <h3>📐 Kilims & Flat-Weaves</h3>
      <ul>
        <li>Shake outdoors every few weeks to remove debris</li>
        <li>Vacuum both sides on low suction — never the fringes</li>
        <li>Clean fringes separately with a soft brush</li>
        <li>Vegetable-dyed kilims: test a hidden spot before any wet cleaning</li>
        <li>Home washing possible if colourfast — gentle brush, minimal water</li>
        <li>Dry completely flat before rolling or storing</li>
        <li>Professional clean every 5–10 years</li>
      </ul>
    </div>

  </div>
</div>

<hr class="section-divider">

<!-- ACİL LEKE MÜDAHALESİ -->
<div class="care-section">
  <h2>🚨 Stain Emergency: First 5 Minutes</h2>
  <p>Speed matters more than anything. The longer a spill sits, the harder it becomes to remove — especially on natural dyes.</p>

  <div class="emergency-box">
    <h3>⚡ Immediate Response Protocol</h3>
    <ol class="emergency-steps">
      <li>If solids are present, scoop them up with a spoon first — do not press them into the fibres.</li>
      <li>Blot (do not rub) with absorbent paper towels or a clean white cloth. Work from the outside of the stain toward the centre to prevent spreading.</li>
      <li>Also blot the floor or underlay beneath the carpet — moisture travels downward.</li>
      <li>Place a shallow tray under the stained area, then pass a small amount of clean cold water through it to dilute what remains.</li>
      <li>Blot again repeatedly until no more colour transfers to your cloth.</li>
      <li>Allow to dry completely flat in a ventilated area — never fold or roll while damp.</li>
    </ol>
  </div>

  <h3>Common Stain Types</h3>
  <table class="freq-table">
    <thead>
      <tr><th>Stain</th><th>First Action</th><th>Notes</th></tr>
    </thead>
    <tbody>
      <tr><td>☕ Coffee / Tea / Wine</td><td>Blot immediately, cold water rinse</td><td>For vegetable-dyed kilims, wet generously before blotting. Sparkling water works well.</td></tr>
      <tr><td>🫒 Grease / Oil</td><td>Sprinkle corn starch or baking soda, leave 30 min, brush off</td><td>Follow with ox gall soap on wool. Silk: professional only.</td></tr>
      <tr><td>🐾 Pet Accidents</td><td>Blot, then rinse with enzyme cleaner formulated for wool</td><td>Act fast — pet acid damages wool fibres quickly.</td></tr>
      <tr><td>🩸 Blood</td><td>Cold water only — never warm</td><td>Warm water sets protein stains permanently.</td></tr>
      <tr><td>🖊️ Ink</td><td>Do not rub — professional cleaner immediately</td><td>Home treatment risks spreading and setting the stain.</td></tr>
    </tbody>
  </table>
</div>

<hr class="section-divider">

<!-- YAPILACAKLAR / YAPILMAYACAKLAR -->
<div class="care-section">
  <h2>✅ Do's & ❌ Don'ts</h2>

  <h3>✅ Always Do</h3>
  <div class="do-grid">
    <div class="do-item"><span class="do-icon">🔄</span>Rotate your carpet every 3–6 months for even wear and sun exposure.</div>
    <div class="do-item"><span class="do-icon">🛏️</span>Use a quality rug pad underneath — reduces dirt penetration and prevents slipping.</div>
    <div class="do-item"><span class="do-icon">🌬️</span>Air your carpet outdoors in indirect light 1–2 times per year.</div>
    <div class="do-item"><span class="do-icon">🧹</span>Vacuum both sides regularly — dust settles in the backing.</div>
    <div class="do-item"><span class="do-icon">🧪</span>Always test any cleaning solution on a hidden corner first.</div>
    <div class="do-item"><span class="do-icon">🌿</span>Dry completely flat before storing or rolling.</div>
  </div>

  <h3 style="margin-top: 28px;">❌ Never Do</h3>
  <div class="never-grid">
    <div class="never-item"><span class="never-icon">🚫</span>Never put a hand-knotted carpet or kilim in a washing machine — permanent damage guaranteed.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never use bleach or alkaline household detergents — they destroy natural dyes and weaken fibres.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never vacuum the fringes with a beater bar — they will unravel.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never dry in strong direct sunlight — UV fades natural dyes irreversibly.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never rub a stain — always blot. Rubbing spreads and sets it deeper.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never use steam cleaning on silk — heat and moisture permanently stretch silk fibres.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never take a valuable piece to a general dry cleaner — they use chemicals harmful to natural dyes.</div>
    <div class="never-item"><span class="never-icon">🚫</span>Never fold a damp carpet — mildew forms within hours.</div>
  </div>
</div>

<hr class="section-divider">

<!-- UZUN SÜRELİ SAKLAMA -->
<div class="care-section">
  <h2>📦 Long-Term Storage</h2>
  <p>If you need to store your carpet for a season or longer, preparation is everything. Improper storage is one of the most common causes of permanent damage.</p>

  <ol class="storage-steps">
    <li><strong>Clean thoroughly first.</strong> Never store a dirty carpet — stains set permanently over time, and any food residue attracts moths and insects.</li>
    <li><strong>Ensure it is completely dry.</strong> Even slight residual moisture causes mildew. Air the carpet outdoors for several hours before storing.</li>
    <li><strong>Roll, never fold.</strong> Folding creates permanent creases that crack the foundation. Roll lengthwise, pile inward, around an acid-free tube if possible.</li>
    <li><strong>Wrap in breathable material.</strong> Use cotton muslin or acid-free paper — never plastic, which traps moisture and encourages mould.</li>
    <li><strong>Store horizontally.</strong> Never stand a rolled carpet upright — the weight crushes the lower fibres over time.</li>
    <li><strong>Use cedar blocks or lavender sachets</strong> to deter moths. Avoid chemical mothballs — the smell is difficult to remove and the chemicals can affect dyes.</li>
    <li><strong>Check every 3–6 months.</strong> Unroll briefly to air and inspect for any moth activity or moisture.</li>
  </ol>
</div>

<hr class="section-divider">

<!-- PROFESYONELİ NE ZAMAN ARAYIN -->
<div class="care-section">
  <h2>🏪 When to Call a Professional</h2>

  <table class="freq-table">
    <thead>
      <tr><th>Situation</th><th>Action</th></tr>
    </thead>
    <tbody>
      <tr><td>Silk carpet of any value</td><td>Professional cleaning only — always</td></tr>
      <tr><td>Antique or collector kilim</td><td>Professional conservator, not a general cleaner</td></tr>
      <tr><td>Persistent stain after first aid</td><td>Professional immediately — delay makes it harder</td></tr>
      <tr><td>Colour bleeding during home wash</td><td>Stop immediately, blot excess water, professional cleaner</td></tr>
      <tr><td>Moth damage or insect activity</td><td>Professional treatment + storage review</td></tr>
      <tr><td>Routine deep clean — wool carpet</td><td>Every 3–5 years</td></tr>
      <tr><td>Routine deep clean — kilim</td><td>Every 5–10 years</td></tr>
      <tr><td>Structural damage (unravelling, tears)</td><td>Specialist restorer — not a cleaner</td></tr>
    </tbody>
  </table>

  <div class="curator-note">
    "In Cappadocia, I have seen carpets ruined not by time, but by well-meaning owners who scrubbed too hard, used the wrong soap, or left them rolled in plastic for a summer. A carpet that has survived 100 years of use asks for very little — just the right kind of care at the right moment."
    <cite>— Fatih Mehmet Canıtez, Carpet Curator, Göreme</cite>
  </div>
</div>

<hr class="section-divider">

<!-- NAVİGASYON -->
<div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center; margin-top: 10px;">
  <a href="{{ site.baseurl }}/en/kilim" style="background: #fdf5e6; border: 1px solid #d4af37; color: #8b4513; padding: 10px 20px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 0.9em;">📐 Kilim Guide →</a>
  <a href="{{ site.baseurl }}/en/materials" style="background: #fdf5e6; border: 1px solid #d4af37; color: #8b4513; padding: 10px 20px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 0.9em;">🧵 Materials & Techniques →</a>
  <a href="{{ site.baseurl }}/en/hereke" style="background: #fdf5e6; border: 1px solid #d4af37; color: #8b4513; padding: 10px 20px; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 0.9em;">🏰 Imperial Hereke →</a>
</div>
