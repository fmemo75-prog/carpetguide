\---

layout: default

title: Family \& Memories Gallery

\---



<style>

&#x20; .gallery-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); grid-gap: 20px; padding: 20px 0; }

&#x20; .gallery-item { background: #fff; border-radius: 12px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #eee; display: flex; flex-direction: column; transition: 0.3s; }

&#x20; .gallery-item:hover { transform: translateY(-5px); }

&#x20; .gallery-link { display: block; width: 100%; height: 260px; overflow: hidden; cursor: zoom-in; }

&#x20; .gallery-img { width: 100%; height: 100%; object-fit: cover; }

&#x20; .gallery-info { padding: 12px; text-align: center; font-size: 13px; color: #666; background: #fdf5e6; border-top: 1px solid #eee; }

</style>



\# 👨‍👩‍👧‍👦 Family, Friends \& Memories

\*\*The Personal Archive of Fatih Mehmet Canıtez\*\*



<div class="gallery-grid">

&#x20; <!-- OTOMATİK DÖNGÜ: images klasöründeki 'aile-' ön ekli resimleri çeker -->

&#x20; {% assign all\_files = site.static\_files | sort: "path" | reverse %}

&#x20; {% for file in all\_files %}

&#x20;   {% if file.path contains '/images/aile-' %}

&#x20;       <div class="gallery-item">

&#x20;         <a href="{{ site.baseurl }}{{ file.path }}" target="\_blank" class="gallery-link">

&#x20;           <img src="{{ site.baseurl }}{{ file.path }}" class="gallery-img" alt="Family Moment" loading="lazy">

&#x20;         </a>

&#x20;         <div class="gallery-info">

&#x20;           ❤️ Special Moment

&#x20;         </div>

&#x20;       </div>

&#x20;   {% endif %}

&#x20; {% endfor %}

</div>



<hr style="margin-top: 50px;">

<div style="text-align: center;">

&#x20; <a href="./gallery" style="font-weight: bold; color: #8b0000; text-decoration: none;">⬅️ Back to All Collections</a> | 

&#x20; <a href="./" style="font-weight: bold; color: #8b0000; text-decoration: none;">🏠 Home</a>

</div>

