<style>
  .day-wrap { padding: 1.5rem 0; }
  .day-header { margin-bottom: 1.5rem; }
  .day-title { font-size: 20px; font-weight: 600; color: #8b0000; margin: 0 0 4px; }
  .day-sub { font-size: 13px; color: #888; margin: 0; }
  .timeline { display: flex; flex-direction: column; }
  .stop { display: grid; grid-template-columns: 72px 28px minmax(0,1fr); gap: 0 12px; align-items: stretch; }
  .stop-time { font-size: 12px; font-weight: 600; color: #888; text-align: right; padding-top: 14px; }
  .stop-line { display: flex; flex-direction: column; align-items: center; }
  .stop-dot { width: 14px; height: 14px; border-radius: 50%; flex-shrink: 0; margin-top: 14px; border: 2px solid; }
  .stop-connector { flex: 1; width: 2px; min-height: 16px; opacity: 0.3; }
  .stop-card { background: #fff; border: 1px solid #eee; border-radius: 12px; padding: 12px 14px; margin-bottom: 10px; }
  .stop-card-top { display: flex; align-items: center; gap: 8px; margin-bottom: 4px; }
  .stop-icon { font-size: 18px; line-height: 1; }
  .stop-name { font-size: 15px; font-weight: 600; color: #222; }
  .stop-desc { font-size: 13px; color: #555; line-height: 1.5; }
  .stop-badge { font-size: 11px; padding: 2px 8px; border-radius: 20px; font-weight: 600; margin-left: auto; white-space: nowrap; }
  .stop-tip { font-size: 12px; color: #999; font-style: italic; margin-top: 4px; }
  .badge-dawn { background: #FAEEDA; color: #633806; }
  .badge-morning { background: #E6F1FB; color: #0C447C; }
  .badge-midday { background: #EAF3DE; color: #27500A; }
  .badge-afternoon { background: #E1F5EE; color: #085041; }
  .badge-evening { background: #FAECE7; color: #712B13; }
  .badge-night { background: #EEEDFE; color: #3C3489; }
  .dot-dawn { border-color: #EF9F27; background: #FAEEDA; }
  .dot-morning { border-color: #378ADD; background: #E6F1FB; }
  .dot-midday { border-color: #639922; background: #EAF3DE; }
  .dot-afternoon { border-color: #1D9E75; background: #E1F5EE; }
  .dot-evening { border-color: #D85A30; background: #FAECE7; }
  .dot-night { border-color: #7F77DD; background: #EEEDFE; }
  .line-dawn { background: #EF9F27; }
  .line-morning { background: #378ADD; }
  .line-midday { background: #639922; }
  .line-afternoon { background: #1D9E75; }
  .line-evening { background: #D85A30; }
  .line-night { background: #7F77DD; }
</style>

<div class="day-wrap">
  <div class="day-header">
    <p class="day-title">🗓️ The "Perfect Day" Express Route</p>
    <p class="day-sub">One day · Göreme-centered · Local expert route</p>
  </div>
  <div class="timeline">
    <div class="stop">
      <div class="stop-time">05:30 AM</div>
      <div class="stop-line"><div class="stop-dot dot-dawn"></div><div class="stop-connector line-morning"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🎈</span><span class="stop-name">Balloon watch</span><span class="stop-badge badge-dawn">Dawn</span></div>
        <div class="stop-desc">Göreme Sunset Point (Aydın Kırağı) — watch dozens of balloons rise over the valleys as the sky turns gold.</div>
        <div class="stop-tip">💡 Arrive 10 min early for the best spot on the ridge.</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">08:30 AM</div>
      <div class="stop-line"><div class="stop-dot dot-morning"></div><div class="stop-connector line-midday"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🏛️</span><span class="stop-name">Göreme Open Air Museum</span><span class="stop-badge badge-morning">Morning</span></div>
        <div class="stop-desc">UNESCO rock-cut churches with 10th-century Byzantine frescoes — before the tour buses arrive.</div>
        <div class="stop-tip">💡 Don't skip the Dark Church (Karanlık Kilise) — best-preserved frescoes in the world.</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">11:00 AM</div>
      <div class="stop-line"><div class="stop-dot dot-midday"></div><div class="stop-connector line-midday"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🍄</span><span class="stop-name">Fairy chimneys</span><span class="stop-badge badge-midday">Midday</span></div>
        <div class="stop-desc">Drive to Pasabağ (Monks Valley) for three-headed chimneys, then Devrent Valley for surreal rock sculptures.</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">01:00 PM</div>
      <div class="stop-line"><div class="stop-dot dot-midday"></div><div class="stop-connector line-afternoon"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🏺</span><span class="stop-name">Avanos — art & lunch</span><span class="stop-badge badge-midday">Lunch</span></div>
        <div class="stop-desc">Pottery workshop at a Hittite atelier on the Red River, then lunch by the Kızılırmak waterfront.</div>
        <div class="stop-tip">💡 Try the Testi Kebab (pottery kebab) — it's cracked open at your table.</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">03:30 PM</div>
      <div class="stop-line"><div class="stop-dot dot-afternoon"></div><div class="stop-connector line-evening"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🥾</span><span class="stop-name">Pigeon Valley hike</span><span class="stop-badge badge-afternoon">Afternoon</span></div>
        <div class="stop-desc">Walk from Uçhisar Castle back to Göreme through cave pigeon houses and carved rock paths (~4 km, easy).</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">06:30 PM</div>
      <div class="stop-line"><div class="stop-dot dot-evening"></div><div class="stop-connector line-night"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🌅</span><span class="stop-name">Sunset at Rose Valley</span><span class="stop-badge badge-evening">Sunset</span></div>
        <div class="stop-desc">Rose Valley Viewpoint — watch the tuff rock turn deep crimson and pink as the sun drops behind the horizon.</div>
        <div class="stop-tip">💡 The #1 sunset spot in all of Cappadocia.</div>
      </div>
    </div>
    <div class="stop">
      <div class="stop-time">08:30 PM</div>
      <div class="stop-line"><div class="stop-dot dot-night"></div><div class="stop-connector" style="background:transparent;"></div></div>
      <div class="stop-card">
        <div class="stop-card-top"><span class="stop-icon">🍴</span><span class="stop-name">Dinner in Göreme</span><span class="stop-badge badge-night">Night</span></div>
        <div class="stop-desc">Traditional Pottery Kebab at a cave restaurant in Göreme center. End the day the Anatolian way.</div>
        <div class="stop-tip">💡 Dibek and Topdeck Cave Restaurant both have 4.5+ stars on Google.</div>
      </div>
    </div>
  </div>
</div>




 💡 


Expert Tips for a Perfect Experience (Insider Secrets)

<style>
  .tips-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 12px; margin-top: 16px; }
  .tip-card { background: #fff; border: 0.5px solid #eee; border-radius: 0 12px 12px 0; padding: 14px 16px; border-left: 4px solid; }
  .tip-top { display: flex; align-items: center; gap: 8px; margin-bottom: 6px; }
  .tip-num { font-size: 11px; font-weight: 600; padding: 2px 7px; border-radius: 20px; white-space: nowrap; }
  .tip-title { font-size: 14px; font-weight: 600; color: #222; }
  .tip-body { font-size: 13px; color: #555; line-height: 1.55; }
  .tip-body strong { font-weight: 600; color: #222; }
  .tip-highlight { margin-top: 8px; padding: 8px 10px; border-radius: 6px; font-size: 12px; line-height: 1.5; }
  .tip-list { margin: 6px 0 0; padding-left: 16px; font-size: 13px; color: #555; line-height: 1.7; }
  .c1 { border-color: #378ADD; } .c1 .tip-num { background:#E6F1FB; color:#0C447C; } .c1 .tip-highlight { background:#E6F1FB; color:#0C447C; }
  .c2 { border-color: #EF9F27; } .c2 .tip-num { background:#FAEEDA; color:#633806; } .c2 .tip-highlight { background:#FAEEDA; color:#633806; }
  .c3 { border-color: #D85A30; } .c3 .tip-num { background:#FAECE7; color:#712B13; } .c3 .tip-highlight { background:#FAECE7; color:#712B13; }
  .c4 { border-color: #7F77DD; } .c4 .tip-num { background:#EEEDFE; color:#3C3489; } .c4 .tip-highlight { background:#EEEDFE; color:#3C3489; }
  .c5 { border-color: #1D9E75; } .c5 .tip-num { background:#E1F5EE; color:#085041; } .c5 .tip-highlight { background:#E1F5EE; color:#085041; }
  .c6 { border-color: #639922; } .c6 .tip-num { background:#EAF3DE; color:#27500A; } .c6 .tip-highlight { background:#EAF3DE; color:#27500A; }
  .c7 { border-color: #888780; } .c7 .tip-num { background:#F1EFE8; color:#444441; } .c7 .tip-highlight { background:#F1EFE8; color:#444441; }
  .c8 { border-color: #378ADD; } .c8 .tip-num { background:#E6F1FB; color:#0C447C; } .c8 .tip-highlight { background:#E6F1FB; color:#0C447C; }
  .c9 { border-color: #D4537E; } .c9 .tip-num { background:#FBEAF0; color:#72243E; } .c9 .tip-highlight { background:#FBEAF0; color:#72243E; }
  .c10 { border-color: #1D9E75; } .c10 .tip-num { background:#E1F5EE; color:#085041; } .c10 .tip-highlight { background:#E1F5EE; color:#085041; }
</style>

<div class="tips-grid">
  <div class="tip-card c1">
    <div class="tip-top"><span style="font-size:18px;">🎫</span><span class="tip-title">Get the Museum Pass Cappadocia</span><span class="tip-num">01</span></div>
    <div class="tip-body">If you plan to visit Göreme Open Air Museum, Ihlara Valley, and at least one Underground City, buy the Museum Pass.</div>
    <div class="tip-highlight c1">Saves money <strong>and</strong> lets you skip the long ticket lines at every entrance.</div>
  </div>
  <div class="tip-card c2">
    <div class="tip-top"><span style="font-size:18px;">🎈</span><span class="tip-title">Don't book your balloon for the last day</span><span class="tip-num">02</span></div>
    <div class="tip-body">Flights are weather-dependent and get canceled when winds are strong.</div>
    <div class="tip-highlight c2"><strong>Book for your very first morning.</strong> If canceled, you still have 1–2 more mornings to retry. Not flying? Go to Göreme Sunset Point (Aydın Kırağı) at 05:30 AM to watch them rise.</div>
  </div>
  <div class="tip-card c3">
    <div class="tip-top"><span style="font-size:18px;">👟</span><span class="tip-title">Wear the right shoes</span><span class="tip-num">03</span></div>
    <div class="tip-body">Cappadocia's rocks are made of tuff (volcanic ash) — very slippery and crumbly underfoot.</div>
    <div class="tip-highlight c3">Leave flip-flops at the hotel. <strong>Hiking boots or deep-grip sneakers only.</strong> You'll thank yourself on Uçhisar Castle's steps.</div>
  </div>
  <div class="tip-card c4">
    <div class="tip-top"><span style="font-size:18px;">🧥</span><span class="tip-title">The layering rule</span><span class="tip-num">04</span></div>
    <div class="tip-body">Desert climate: <strong>very cold at sunrise, very hot at noon</strong> — even in July.</div>
    <div class="tip-highlight c4">Always carry a light jacket. At 5:00 AM you'll need it. By 11:00 AM you'll be in a t-shirt.</div>
  </div>
  <div class="tip-card c5">
    <div class="tip-top"><span style="font-size:18px;">🏺</span><span class="tip-title">Beyond the Pottery Kebab</span><span class="tip-num">05</span></div>
    <div class="tip-body">Everyone eats Testi Kebab. But locals eat:</div>
    <ul class="tip-list">
      <li><strong>Kuru Fasulye</strong> — clay-pot white beans in Ayvalı village</li>
      <li><strong>Kabak Çekirdeği</strong> — pumpkin seeds roasted in milk, from a local market</li>
      <li><strong>Local wine</strong> — visit Turasan or Kocabağ for a tasting; volcanic soil gives a unique mineral taste</li>
    </ul>
  </div>
  <div class="tip-card c6">
    <div class="tip-top"><span style="font-size:18px;">🗺️</span><span class="tip-title">Download offline maps</span><span class="tip-num">06</span></div>
    <div class="tip-body">Signal is weak in deep valleys like Meskendir or Red Valley.</div>
    <div class="tip-highlight c6">Download the region on <strong>Google Maps Offline</strong> or use <strong>Maps.me</strong> before you head out.</div>
  </div>
  <div class="tip-card c7">
    <div class="tip-top"><span style="font-size:18px;">🤫</span><span class="tip-title">Beat the crowds — the 8 AM rule</span><span class="tip-num">07</span></div>
    <div class="tip-body">Tour buses arrive at Göreme Open Air Museum around 10:30 AM.</div>
    <div class="tip-highlight c7">Be at the gate at <strong>08:00 AM (opening time)</strong>. You'll have the ancient churches entirely to yourself for at least an hour.</div>
  </div>
  <div class="tip-card c8">
    <div class="tip-top"><span style="font-size:18px;">💧</span><span class="tip-title">Stay hydrated</span><span class="tip-num">08</span></div>
    <div class="tip-body">The air is incredibly dry. You might not feel sweaty, but you are losing water fast.</div>
    <div class="tip-highlight c8">Always carry a <strong>reusable water bottle</strong> — refill it at your hotel every morning.</div>
  </div>
  <div class="tip-card c9">
    <div class="tip-top"><span style="font-size:18px;">💰</span><span class="tip-title">Cash is king in small villages</span><span class="tip-num">09</span></div>
    <div class="tip-body">Göreme center accepts cards, but smaller villages like <strong>Çavuşin</strong> and <strong>Mustafapaşa</strong> often don't.</div>
    <div class="tip-highlight c9">Carry some <strong>Turkish Lira (TRY)</strong> for local tea, handmade lace, and village markets.</div>
  </div>
  <div class="tip-card c10">
    <div class="tip-top"><span style="font-size:18px;">🐕</span><span class="tip-title">The friendly valley dogs</span><span class="tip-num">10</span></div>
    <div class="tip-body">You'll meet stray dogs while hiking. Most are very friendly and often "guide" tourists through the trails.</div>
    <div class="tip-highlight c10">They are the <strong>unofficial guardians of the valleys</strong>. Enjoy their company.</div>
  </div>
</div>

