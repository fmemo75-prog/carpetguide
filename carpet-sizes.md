---
layout: default
title: Carpet Size Guide — How to Choose the Right Size
---

<style>
  .page-hero { text-align: center; margin-bottom: 32px; }
  .page-hero h1 { color: #8b0000; font-size: 1.85em; margin-bottom: 8px; font-family: Georgia, serif; }
  .page-hero p  { color: #666; font-style: italic; font-size: 0.97em; max-width: 600px; margin: 0 auto; }
  * { box-sizing: border-box; }
  .size-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(170px, 1fr)); gap: 10px; margin-bottom: 1.5rem; }
  .size-btn {
    background: #fff;
    border: 1px solid #ede8df;
    border-radius: 10px;
    padding: 10px 14px;
    cursor: pointer;
    text-align: left;
    font-family: Georgia, serif;
    transition: border-color 0.15s;
  }
  .size-btn:hover { border-color: #8b0000; }
  .size-btn.active { border: 2px solid #8b0000; background: #fff8f5; }
  .size-btn .label { font-size: 13px; font-weight: bold; color: #2c3e50; }
  .size-btn .sub { font-size: 11px; color: #888; margin-top: 2px; }
  .size-btn .use { font-size: 11px; color: #8b0000; margin-top: 4px; font-weight: bold; }
  .room-wrap {
    background: #fdf5e6;
    border-radius: 14px;
    border: 1px solid #ede8df;
    padding: 1.5rem;
    display: flex; gap: 2rem; align-items: flex-start; flex-wrap: wrap;
  }
  .room-visual { flex: 1; min-width: 260px; }
  .room-info { flex: 1; min-width: 200px; font-family: Georgia, serif; }
  .room-info h3 { font-size: 1.1em; color: #8b0000; margin-bottom: 12px; }
  .info-row { display: flex; justify-content: space-between; padding: 7px 0; border-bottom: 1px dashed #ede8df; font-size: 0.88em; }
  .info-row .k { color: #888; }
  .info-row .v { font-weight: bold; color: #2c3e50; }
  .tip { margin-top: 14px; font-size: 0.85em; color: #3d2000; line-height: 1.7; background: #fff; border-radius: 8px; padding: 12px 14px; border-left: 4px solid #8b0000; font-style: italic; }
  svg text { font-family: Georgia, serif; }
  @media (max-width: 600px) { .room-wrap { flex-direction: column; } }
</style>

<div class="page-hero">
  <h1>📐 Carpet Size Guide</h1>
  <p>Select a size to see how it fits in a room — with measurements in both metric and imperial.</p>
</div>

<div class="size-grid" id="btns"></div>

<div class="room-wrap">
  <div class="room-visual">
    <svg id="room-svg" width="100%" viewBox="0 0 320 260" xmlns="http://www.w3.org/2000/svg"></svg>
  </div>
  <div class="room-info">
    <h3 id="info-title"></h3>
    <div class="info-row"><span class="k">Metric</span><span class="v" id="info-metric"></span></div>
    <div class="info-row"><span class="k">Imperial</span><span class="v" id="info-imperial"></span></div>
    <div class="info-row"><span class="k">Room type</span><span class="v" id="info-room"></span></div>
    <div class="info-row"><span class="k">Ideal use</span><span class="v" id="info-use"></span></div>
    <div class="info-row"><span class="k">Furniture</span><span class="v" id="info-furn"></span></div>
    <div class="tip" id="info-tip"></div>
  </div>
</div>

<div style="margin-top: 32px; background: #fff; border: 1px solid #ede8df; border-radius: 14px; padding: 20px 24px; font-family: Georgia, serif;">
  <h3 style="color: #8b0000; margin-bottom: 14px; font-size: 1.05em;">📏 The Golden Rules of Carpet Sizing</h3>
  <ul style="list-style: none; padding: 0; margin: 0; font-size: 0.9em; color: #2c3e50; line-height: 1.9;">
    <li>✦ <strong>Living room:</strong> All front legs of sofas and chairs should rest on the carpet — never float beside it.</li>
    <li>✦ <strong>Dining room:</strong> Add at least 60 cm (24") to each side of the table — chairs must stay on the rug when pulled out.</li>
    <li>✦ <strong>Bedroom:</strong> The carpet should extend at least 45 cm (18") beyond each side of the bed.</li>
    <li>✦ <strong>Corridor runner:</strong> Leave 5–10 cm of bare floor visible on each side for a clean, intentional look.</li>
    <li>✦ <strong>General rule:</strong> When in doubt, go one size larger — a carpet that is too small is the most common decorating mistake.</li>
  </ul>
</div>

<hr style="border: none; border-top: 2px dashed #d4af37; margin: 36px 0;">

<div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center;">
  <a href="{{ site.baseurl }}/materials" style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🧵 Materials Guide →</a>
  <a href="{{ site.baseurl }}/cleaning" style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🧹 Care Guide →</a>
  <a href="{{ site.baseurl }}/carpet-map" style="background:#fdf5e6; border:1px solid #d4af37; color:#8b4513; padding:10px 20px; border-radius:50px; text-decoration:none; font-weight:bold; font-size:0.9em;">🗺️ Regional Map →</a>
</div>

<script>
const sizes = [
  {
    id: 'doormat', label: 'Doormat',
    metric: '60 × 90 cm', imperial: "2' × 3'",
    room: 'Entrance / Bathroom', use: 'Door front, sink area', furn: 'None',
    tip: 'Place just inside the front door or in front of the bathroom sink. Protects floors and defines the entry zone.',
    rw: 60, rh: 90, cw: 60, ch: 90, cx: 0, cy: 0, roomLabel: 'Entrance', furniture: []
  },
  {
    id: 'bedside', label: 'Bedside / Hall',
    metric: '80 × 150 cm', imperial: "2'6\" × 5'",
    room: 'Bedroom / Corridor', use: 'Beside bed, hallway', furn: 'Partial under bed',
    tip: 'Place lengthwise beside the bed so your feet land on it when you wake up. In corridors, use as a runner.',
    rw: 160, rh: 220, cw: 80, ch: 150, cx: 40, cy: 35, roomLabel: 'Bedroom',
    furniture: [
      { x: 0, y: 0, w: 160, h: 30, label: '', fill: '#ccc' },
      { x: 20, y: 30, w: 120, h: 90, label: 'Bed', fill: '#b8c8e8' },
      { x: 0, y: 125, w: 35, h: 35, label: 'Table', fill: '#d4b896' },
      { x: 125, y: 125, w: 35, h: 35, label: 'Table', fill: '#d4b896' },
    ]
  },
  {
    id: 'small', label: 'Small living room',
    metric: '120 × 180 cm', imperial: "4' × 6'",
    room: 'Living room (small)', use: 'Coffee table only', furn: 'Under coffee table',
    tip: 'Front legs of sofa may rest on the carpet. Coffee table sits fully on the rug. Good for compact spaces.',
    rw: 260, rh: 220, cw: 120, ch: 180, cx: 70, cy: 20, roomLabel: 'Living room',
    furniture: [
      { x: 0, y: 0, w: 260, h: 20, label: '', fill: '#ccc' },
      { x: 10, y: 20, w: 240, h: 55, label: 'Sofa', fill: '#b8c8e8' },
      { x: 85, y: 95, w: 90, h: 55, label: 'Coffee table', fill: '#d4b896' },
      { x: 10, y: 155, w: 55, h: 55, label: 'Armchair', fill: '#b8c8e8' },
      { x: 195, y: 155, w: 55, h: 55, label: 'Armchair', fill: '#b8c8e8' },
    ]
  },
  {
    id: 'standard', label: 'Standard living room',
    metric: '160 × 230 cm', imperial: "5'3\" × 7'6\"",
    room: 'Living room', use: 'Full seating group', furn: 'Front legs on rug',
    tip: 'The most popular size. All front legs of the sofa and chairs rest on the rug. Coffee table sits fully on it.',
    rw: 280, rh: 240, cw: 160, ch: 230, cx: 60, cy: 5, roomLabel: 'Living room',
    furniture: [
      { x: 0, y: 0, w: 280, h: 20, label: '', fill: '#ccc' },
      { x: 10, y: 20, w: 260, h: 55, label: 'Sofa', fill: '#b8c8e8' },
      { x: 95, y: 95, w: 90, h: 55, label: 'Coffee table', fill: '#d4b896' },
      { x: 10, y: 160, w: 55, h: 60, label: 'Armchair', fill: '#b8c8e8' },
      { x: 215, y: 160, w: 55, h: 60, label: 'Armchair', fill: '#b8c8e8' },
    ]
  },
  {
    id: 'large', label: 'Large living room',
    metric: '200 × 300 cm', imperial: "6'6\" × 10'",
    room: 'Large salon / Dining', use: 'Full group + dining', furn: 'All legs on rug',
    tip: 'All furniture legs sit fully on the rug. Ideal for open-plan spaces. Under a dining table, chairs stay on rug even when pulled out.',
    rw: 300, rh: 260, cw: 200, ch: 240, cx: 50, cy: 10, roomLabel: 'Salon',
    furniture: [
      { x: 0, y: 0, w: 300, h: 20, label: '', fill: '#ccc' },
      { x: 10, y: 20, w: 280, h: 55, label: 'Sofa', fill: '#b8c8e8' },
      { x: 100, y: 95, w: 100, h: 55, label: 'Coffee table', fill: '#d4b896' },
      { x: 10, y: 160, w: 65, h: 65, label: 'Armchair', fill: '#b8c8e8' },
      { x: 225, y: 160, w: 65, h: 65, label: 'Armchair', fill: '#b8c8e8' },
    ]
  },
  {
    id: 'xlarge', label: 'Extra large',
    metric: '250 × 350 cm', imperial: "8'2\" × 11'6\"",
    room: 'Grand salon', use: 'Palace / showroom', furn: 'All fully on rug',
    tip: 'Statement piece for large open-plan rooms. All furniture sits fully on the carpet — the rug defines the room.',
    rw: 310, rh: 260, cw: 250, ch: 240, cx: 30, cy: 10, roomLabel: 'Grand salon',
    furniture: [
      { x: 0, y: 0, w: 310, h: 20, label: '', fill: '#ccc' },
      { x: 5, y: 20, w: 300, h: 55, label: 'Sofa', fill: '#b8c8e8' },
      { x: 105, y: 95, w: 100, h: 55, label: 'Coffee table', fill: '#d4b896' },
      { x: 5, y: 160, w: 70, h: 70, label: 'Armchair', fill: '#b8c8e8' },
      { x: 235, y: 160, w: 70, h: 70, label: 'Armchair', fill: '#b8c8e8' },
    ]
  },
  {
    id: 'square', label: 'Square',
    metric: '200 × 200 cm', imperial: "6'6\" × 6'6\"",
    room: 'Sitting area', use: 'Symmetrical layout', furn: 'Centred group',
    tip: 'Works beautifully under a square coffee table or in a square room. Creates a balanced, symmetrical look.',
    rw: 260, rh: 260, cw: 200, ch: 200, cx: 30, cy: 30, roomLabel: 'Sitting room',
    furniture: [
      { x: 0, y: 0, w: 260, h: 20, label: '', fill: '#ccc' },
      { x: 10, y: 20, w: 240, h: 55, label: 'Sofa', fill: '#b8c8e8' },
      { x: 85, y: 95, w: 90, h: 55, label: 'Coffee table', fill: '#d4b896' },
      { x: 10, y: 165, w: 55, h: 65, label: 'Armchair', fill: '#b8c8e8' },
      { x: 195, y: 165, w: 55, h: 65, label: 'Armchair', fill: '#b8c8e8' },
    ]
  },
  {
    id: 'runner', label: 'Runner',
    metric: '80 × 300 cm', imperial: "2'6\" × 10'",
    room: 'Corridor / Stairway', use: 'Hallway, kitchen', furn: 'None',
    tip: 'Leave 5–10 cm of floor exposed on each side of the corridor. In the kitchen, use in front of the counter or between island and cabinets.',
    rw: 300, rh: 120, cw: 300, ch: 80, cx: 0, cy: 20, roomLabel: 'Corridor',
    furniture: [
      { x: 0, y: 0, w: 300, h: 20, label: '', fill: '#ccc' },
      { x: 0, y: 100, w: 300, h: 20, label: '', fill: '#ccc' },
    ]
  },
  {
    id: 'dining', label: 'Dining room',
    metric: '200 × 290 cm', imperial: "6'6\" × 9'6\"",
    room: 'Dining room', use: 'Under dining table', furn: 'Chairs stay on rug',
    tip: 'Rule: add 60 cm (24") to each side of the table. When guests pull chairs out, all four legs stay on the rug.',
    rw: 280, rh: 260, cw: 200, ch: 230, cx: 40, cy: 15, roomLabel: 'Dining room',
    furniture: [
      { x: 80, y: 55, w: 120, h: 150, label: 'Dining table', fill: '#d4b896' },
      { x: 82, y: 20, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 127, y: 20, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 168, y: 20, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 82, y: 205, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 127, y: 205, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 168, y: 205, w: 30, h: 35, label: '', fill: '#b8c8e8' },
      { x: 40, y: 80, w: 38, h: 30, label: '', fill: '#b8c8e8' },
      { x: 40, y: 150, w: 38, h: 30, label: '', fill: '#b8c8e8' },
      { x: 202, y: 80, w: 38, h: 30, label: '', fill: '#b8c8e8' },
      { x: 202, y: 150, w: 38, h: 30, label: '', fill: '#b8c8e8' },
    ]
  },
];

const btnsEl = document.getElementById('btns');

sizes.forEach(s => {
  const b = document.createElement('button');
  b.className = 'size-btn';
  b.dataset.id = s.id;
  b.innerHTML = `<div class="label">${s.label}</div><div class="sub">${s.metric} &nbsp;·&nbsp; ${s.imperial}</div><div class="use">${s.room}</div>`;
  b.addEventListener('click', () => select(s));
  btnsEl.appendChild(b);
});

function select(s) {
  document.querySelectorAll('.size-btn').forEach(b => b.classList.toggle('active', b.dataset.id === s.id));
  document.getElementById('info-title').textContent = s.label;
  document.getElementById('info-metric').textContent = s.metric;
  document.getElementById('info-imperial').textContent = s.imperial;
  document.getElementById('info-room').textContent = s.room;
  document.getElementById('info-use').textContent = s.use;
  document.getElementById('info-furn').textContent = s.furn;
  document.getElementById('info-tip').textContent = s.tip;
  drawRoom(s);
}

function drawRoom(s) {
  const svg = document.getElementById('room-svg');
  const VW = 320, VH = 260;
  const scale = Math.min((VW - 20) / s.rw, (VH - 20) / s.rh);
  const offX = (VW - s.rw * scale) / 2;
  const offY = (VH - s.rh * scale) / 2;
  let html = '';
  html += `<rect x="${offX}" y="${offY}" width="${s.rw*scale}" height="${s.rh*scale}" fill="#f5f0e8" stroke="#bbb" stroke-width="1" rx="2"/>`;
  html += `<rect x="${offX+s.cx*scale}" y="${offY+s.cy*scale}" width="${s.cw*scale}" height="${s.ch*scale}" fill="rgba(139,0,0,0.18)" stroke="#8b0000" stroke-width="1.5" rx="2"/>`;
  s.furniture.forEach(f => {
    html += `<rect x="${offX+f.x*scale}" y="${offY+f.y*scale}" width="${f.w*scale}" height="${f.h*scale}" fill="${f.fill}" stroke="#999" stroke-width="0.5" rx="1"/>`;
    if (f.label && f.w*scale > 40) html += `<text x="${offX+(f.x+f.w/2)*scale}" y="${offY+(f.y+f.h/2)*scale+4}" text-anchor="middle" font-size="9" fill="#555">${f.label}</text>`;
  });
  const cx = offX+(s.cx+s.cw/2)*scale, cy = offY+(s.cy+s.ch/2)*scale;
  html += `<text x="${cx}" y="${cy}" text-anchor="middle" font-size="10" fill="#8b0000" font-weight="bold">${s.metric}</text>`;
  html += `<text x="${cx}" y="${cy+13}" text-anchor="middle" font-size="9" fill="#8b0000">${s.imperial}</text>`;
  const rx1 = offX+s.cx*scale, ry1 = offY+(s.cy+s.ch)*scale+8;
  html += `<line x1="${rx1}" y1="${ry1}" x2="${rx1+s.cw*scale}" y2="${ry1}" stroke="#8b0000" stroke-width="0.8"/>`;
  html += `<line x1="${rx1}" y1="${ry1-3}" x2="${rx1}" y2="${ry1+3}" stroke="#8b0000" stroke-width="0.8"/>`;
  html += `<line x1="${rx1+s.cw*scale}" y1="${ry1-3}" x2="${rx1+s.cw*scale}" y2="${ry1+3}" stroke="#8b0000" stroke-width="0.8"/>`;
  html += `<text x="${offX+4}" y="${offY+s.rh*scale-4}" font-size="9" fill="#888">${s.roomLabel}</text>`;
  svg.innerHTML = html;
}

select(sizes[3]);
</script>
