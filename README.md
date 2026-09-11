<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday, Alfita ✨</title>

  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet" />

  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            inter: ['Inter', 'sans-serif'],
            playfair: ['"Playfair Display"', 'serif'],
          },
          animation: {
            'fade-up':  'fadeUp 1.2s ease forwards',
            'fade-in':  'fadeIn 1.5s ease forwards',
            'float':    'float 6s ease-in-out infinite',
            'shimmer':  'shimmer 4s linear infinite',
          },
          keyframes: {
            fadeUp:  { '0%': { opacity:'0', transform:'translateY(30px)' }, '100%': { opacity:'1', transform:'translateY(0)' } },
            fadeIn:  { '0%': { opacity:'0' }, '100%': { opacity:'1' } },
            float:   { '0%,100%': { transform:'translateY(0px)' }, '50%': { transform:'translateY(-12px)' } },
            shimmer: { '0%': { backgroundPosition:'-200% center' }, '100%': { backgroundPosition:'200% center' } },
          },
        },
      },
    };
  </script>

  <style>
    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #fff0f6 0%, #fce4ec 30%, #fdf2f8 60%, #fff5fb 100%);
      min-height: 100vh;
      color: #1e293b;
      overflow-x: hidden;
    }

    /* ── Shimmer text ── */
    .shimmer-text {
      background: linear-gradient(90deg, #f9a8d4, #ec4899, #f9a8d4, #fbcfe8, #ec4899, #f9a8d4);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: shimmer 4s linear infinite;
    }

    /* ── Glass card ── */
    .glass {
      background: rgba(255,240,248,0.6);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      border: 1px solid rgba(249,168,212,0.35);
      box-shadow: 0 8px 32px rgba(236,72,153,0.08), 0 2px 8px rgba(0,0,0,0.04);
    }

    /* ── Photo cards ── */
    .photo-card {
      overflow: hidden;
      border-radius: 16px;
      border: 1px solid rgba(249,168,212,0.3);
      transition: transform 0.4s cubic-bezier(.22,1,.36,1), box-shadow 0.4s ease;
      background: rgba(255,240,248,0.7);
      box-shadow: 0 4px 20px rgba(236,72,153,0.07);
      position: relative;
      cursor: pointer;
    }
    .photo-card:hover {
      transform: translateY(-8px) scale(1.02);
      box-shadow: 0 16px 40px rgba(236,72,153,0.16);
    }
    .photo-card img {
      width:100%; height:100%;
      object-fit:cover;
      transition: transform 0.5s ease;
      display:block;
    }
    .photo-card:hover img { transform: scale(1.07); }

    /* ── Edit overlay on photo ── */
    .photo-card .edit-overlay {
      position: absolute; inset: 0;
      background: rgba(15,23,42,0.45);
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      opacity: 0;
      transition: opacity 0.3s ease;
      border-radius: 16px;
      gap: 6px;
    }
    .photo-card:hover .edit-overlay { opacity: 1; }
    .edit-overlay span {
      color: #fff;
      font-family: 'Inter', sans-serif;
      font-size: 0.72rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-top: 4px;
    }

    /* ── CTA Button ── */
    .btn-primary {
      background: linear-gradient(135deg, #ec4899 0%, #f472b6 100%);
      color: #fff; border: none;
      padding: 14px 36px; border-radius: 50px;
      font-family: 'Inter', sans-serif; font-weight: 500;
      font-size: 0.95rem; letter-spacing: 0.04em;
      cursor: pointer; position: relative; overflow: hidden;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
      box-shadow: 0 4px 20px rgba(236,72,153,0.35);
    }
    .btn-primary::before {
      content:''; position:absolute; inset:0;
      background: linear-gradient(135deg, rgba(255,255,255,0.18) 0%, transparent 100%);
      opacity:0; transition: opacity 0.2s;
    }
    .btn-primary:hover { transform:translateY(-2px); box-shadow:0 8px 28px rgba(236,72,153,0.45); }
    .btn-primary:hover::before { opacity:1; }
    .btn-primary:active { transform:translateY(0); }

    /* ── Music button ── */
    #musicBtn {
      width:48px; height:48px; border-radius:50%;
      background:rgba(255,255,255,0.7); backdrop-filter:blur(10px);
      border:1px solid rgba(148,163,184,0.35);
      cursor:pointer; display:flex; align-items:center; justify-content:center;
      transition:all 0.3s ease; box-shadow:0 4px 12px rgba(0,0,0,0.08); outline:none;
    }
    #musicBtn:hover { background:rgba(255,255,255,0.9); box-shadow:0 6px 18px rgba(236,72,153,0.2); transform:scale(1.08); }

    /* ── Confetti ── */
    .confetti-particle {
      position:fixed; border-radius:2px; pointer-events:none;
      z-index:9999; animation:confettiFall linear forwards;
    }
    @keyframes confettiFall {
      0%   { transform:translateY(0) rotate(0deg);    opacity:1; }
      100% { transform:translateY(100vh) rotate(720deg); opacity:0; }
    }

    /* ── Secret overlay ── */
    #secretMsg {
      display:none; position:fixed; inset:0;
      background:rgba(80,10,40,0.45); backdrop-filter:blur(6px);
      z-index:1000; align-items:center; justify-content:center;
    }
    #secretMsg.show { display:flex; }
    #secretMsg .msg-box {
      background:rgba(255,240,248,0.96); border-radius:24px;
      padding:40px 36px; max-width:420px; width:90%;
      text-align:center; border:1px solid rgba(249,168,212,0.4);
      box-shadow:0 20px 60px rgba(236,72,153,0.15);
      animation:fadeUp 0.5s ease forwards;
    }

    /* ── Orbs ── */
    .orb {
      position:fixed; border-radius:50%; filter:blur(60px);
      opacity:0.35; pointer-events:none; z-index:0;
    }

    /* ── Scroll reveal ── */
    .reveal { opacity:0; transform:translateY(28px); transition:opacity 0.8s ease, transform 0.8s ease; }
    .reveal.visible { opacity:1; transform:translateY(0); }

    /* ── Divider ── */
    .divider {
      width:60px; height:2px;
      background:linear-gradient(90deg, transparent, #f9a8d4, transparent);
      margin:0 auto;
    }

    /* ── Countdown ── */
    .countdown-box {
      background:rgba(255,240,248,0.6);
      border:1px solid rgba(249,168,212,0.3); border-radius:12px;
      padding:14px 18px 10px; min-width:70px; text-align:center;
      backdrop-filter:blur(8px);
    }
    .countdown-box .digit { font-family:'Playfair Display',serif; font-size:2rem; font-weight:700; color:#9d174d; line-height:1; }
    .countdown-box .label { font-size:0.65rem; letter-spacing:0.1em; color:#be185d; text-transform:uppercase; margin-top:4px; }

    /* ══════════════════════════════════════════
       BINTANG BERJATUHAN
    ══════════════════════════════════════════ */
    #starCanvas {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    /* ── Toast notif ganti foto ── */
    #photoToast {
      position: fixed; bottom: 28px; left: 50%; transform: translateX(-50%);
      background: rgba(30,58,95,0.92); color: #fff;
      font-family: 'Inter', sans-serif; font-size: 0.82rem;
      padding: 10px 22px; border-radius: 50px;
      opacity: 0; transition: opacity 0.4s ease;
      pointer-events: none; z-index: 9999;
      white-space: nowrap;
    }
    #photoToast.show { opacity: 1; }
  </style>
</head>
<body class="relative">

  <!-- Canvas bintang -->
  <canvas id="starCanvas"></canvas>

  <!-- Background orbs -->
  <div class="orb w-96 h-96 bg-pink-200 top-[-120px] left-[-100px]"></div>
  <div class="orb w-80 h-80 bg-rose-200 bottom-[10%] right-[-80px]"></div>
  <div class="orb w-64 h-64 bg-fuchsia-100 top-[40%] left-[30%]"></div>

  <!-- Toast notifikasi -->
  <div id="photoToast">✓ Foto berhasil diganti!</div>

  <!-- Input file tersembunyi untuk ganti foto -->
  <input type="file" id="fileInput" accept="image/*" style="display:none" />

  <!-- ── Tombol Musik ── -->
  <div class="fixed top-5 right-5 z-50 flex flex-col items-center gap-1">
    <button id="musicBtn" title="Play / Mute music" aria-label="Toggle music">
      <svg id="iconPlay" xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#ec4899" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon><path d="M15.54 8.46a5 5 0 0 1 0 7.07"></path><path d="M19.07 4.93a10 10 0 0 1 0 14.14"></path></svg>
      <svg id="iconMute" xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#94a3b8" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="display:none"><polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"></polygon><line x1="23" y1="9" x2="17" y2="15"></line><line x1="17" y1="9" x2="23" y2="15"></line></svg>
    </button>
    <span class="text-[10px] text-slate-400 tracking-widest font-inter">MUSIC</span>
  </div>

  <!-- YouTube IFrame API untuk background musik -->
  <!-- Video ID: Znw0tQCVFfk — "lagu birthday" yang dipilih -->
  <div id="ytPlayerWrapper" style="position:fixed;bottom:-9999px;left:-9999px;width:1px;height:1px;overflow:hidden;pointer-events:none;z-index:-1;">
    <div id="ytPlayer"></div>
  </div>


  <!-- ════════════════════════════════════════
       HERO
  ════════════════════════════════════════ -->
  <section class="relative z-10 min-h-screen flex flex-col items-center justify-center text-center px-6 py-20">

    <p class="animate-fade-in opacity-0" style="animation-delay:0.2s;animation-fill-mode:forwards;">
      <span class="inline-block text-xs tracking-[0.25em] text-slate-400 uppercase font-inter border border-slate-200 rounded-full px-4 py-1.5 bg-white/60 backdrop-blur-sm">
        <!-- ★ GANTI TANGGAL ★ -->
        Hari Spesialmu
      </span>
    </p>

    <h1 class="font-playfair text-5xl sm:text-7xl lg:text-8xl font-bold mt-6 leading-tight animate-fade-up opacity-0" style="animation-delay:0.5s;animation-fill-mode:forwards;">
      <span class="shimmer-text">Happy Birthday</span>
    </h1>

    <h2 class="font-playfair italic text-4xl sm:text-6xl lg:text-7xl text-slate-700 mt-2 animate-fade-up opacity-0" style="animation-delay:0.8s;animation-fill-mode:forwards;">
      Mbak Alfita
    </h2>

    <p class="font-inter font-light text-slate-500 text-base sm:text-lg max-w-md mt-5 leading-relaxed animate-fade-up opacity-0" style="animation-delay:1.1s;animation-fill-mode:forwards;">
      Semoga hari ini menjadi awal dari bab paling indah dalam hidupmu. 🌸
    </p>

    <div class="mt-14 animate-float opacity-70">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#f9a8d4" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="7 13 12 18 17 13"></polyline><polyline points="7 6 12 11 17 6"></polyline></svg>
    </div>
  </section>


  <!-- ════════════════════════════════════════
       COUNTDOWN
  ════════════════════════════════════════ -->
  <section class="relative z-10 py-16 px-6">
    <div class="max-w-xl mx-auto reveal">
      <p class="text-center text-xs tracking-[0.2em] text-slate-400 uppercase font-inter mb-6">Countdown to next birthday</p>
      <div id="countdown" class="flex justify-center gap-3 sm:gap-5 flex-wrap"></div>
      <p id="birthdayMsg" class="hidden text-center font-playfair italic text-2xl text-blue-500 mt-4">
        🎂 Selamat Ulang Tahun, Mbak Alfita!
      </p>
    </div>
  </section>


  <!-- ════════════════════════════════════════
       KARTU UCAPAN
  ════════════════════════════════════════ -->
  <section class="relative z-10 py-20 px-6">
    <div class="max-w-2xl mx-auto reveal">
      <div class="glass rounded-3xl p-10 sm:p-14 text-center">
        <div class="text-2xl mb-4 animate-float inline-block">✦</div>
        <div class="divider mb-8"></div>

        <p class="font-playfair italic text-2xl sm:text-3xl text-slate-700 leading-relaxed mb-6">
          "Di hari yang istimewa ini, semoga setiap langkah yang kamu ambil diterangi cahaya kebahagiaan."
        </p>

        <div class="divider mb-8"></div>

        <p class="font-inter text-slate-500 text-sm sm:text-base leading-7 mb-8">
          Mbak Alfita, kamu adalah sosok yang selalu menginspirasi dan memberi semangat bagi orang-orang di sekitarmu.
          Terima kasih sudah ada, sudah berjuang, dan sudah menjadi dirimu yang luar biasa.
          Semoga tahun ini membawa lebih banyak tawa, kesuksesan, dan momen tak terlupakan. 🤍
        </p>

        <p class="font-playfair text-slate-400 text-sm tracking-widest">— With love, CLAMPER 25</p>
      </div>
    </div>
  </section>


  <!-- ════════════════════════════════════════
       GALERI FOTO
       Klik foto → pilih dari device untuk menggantinya
  ════════════════════════════════════════ -->
  <section class="relative z-10 py-20 px-6">
    <div class="max-w-5xl mx-auto">

      <div class="text-center mb-6 reveal">
        <p class="text-xs tracking-[0.2em] text-slate-400 uppercase font-inter mb-3">Memories</p>
        <h3 class="font-playfair text-3xl sm:text-4xl text-slate-700">Momen Berharga</h3>
      </div>

      <!-- Petunjuk edit foto -->
      <p class="text-center text-xs text-slate-400 font-inter mb-8 reveal">
        💡 <strong>Klik foto mana saja</strong> untuk menggantinya dengan foto dari perangkatmu
      </p>

      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-4 reveal" id="photoGrid">

        <!-- FOTO 1 -->
        <div class="photo-card aspect-[3/4]" data-index="0">
          <img src="foto1.jpeg" alt="Foto Mbak Alfita 1" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 2 -->
        <div class="photo-card aspect-[3/4]" data-index="1">
          <img src="foto2.png" alt="Foto Mbak Alfita 2" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 3 -->
        <div class="photo-card aspect-square" data-index="2">
          <img src="foto3.png" alt="Foto Mbak Alfita 3" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 4 -->
        <div class="photo-card aspect-[3/4]" data-index="3">
          <img src="foto4.png" alt="Foto Mbak Alfita 4" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 5 (wide) -->
        <div class="photo-card aspect-[4/3] col-span-2" data-index="4">
          <img src="foto5.png" alt="Foto Mbak Alfita 5" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 6 -->
        <div class="photo-card aspect-square" data-index="5">
          <img src="foto6.jpeg" alt="Foto Mbak Alfita 6" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 7 -->
        <div class="photo-card aspect-[3/4]" data-index="6">
          <img src="foto7.jpeg" alt="Foto Mbak Alfita 7" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 8 -->
        <div class="photo-card aspect-square" data-index="7">
          <img src="foto8.jpeg" alt="Foto Mbak Alfita 8" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 9 -->
        <div class="photo-card aspect-[3/4]" data-index="8">
          <img src="foto11.jpeg" alt="Foto Mbak Alfita 9" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 10 -->
        <div class="photo-card aspect-square" data-index="9">
          <img src="foto12.jpeg" alt="Foto Mbak Alfita 10" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 11 (wide) -->
        <div class="photo-card aspect-[4/3] col-span-2" data-index="10">
          <img src="foto13.jpeg" alt="Foto Mbak Alfita 11" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 12 -->
        <div class="photo-card aspect-[3/4]" data-index="11">
          <img src="foto14.jpeg" alt="Foto Mbak Alfita 12" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

        <!-- FOTO 13 -->
        <div class="photo-card aspect-square" data-index="12">
          <img src="foto15.jpeg" alt="Foto Mbak Alfita 13" loading="lazy" />
          <div class="edit-overlay">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
            <span>Ganti Foto</span>
          </div>
        </div>

      </div><!-- /grid -->
    </div>
  </section>


  <!-- ════════════════════════════════════════
       CTA
  ════════════════════════════════════════ -->
  <section class="relative z-10 py-20 px-6 text-center reveal">
    <p class="font-inter text-slate-400 text-sm tracking-widest uppercase mb-6">A little surprise for you</p>
    <button class="btn-primary" id="surpriseBtn">
      ✨ &nbsp; Buka Hadiah Spesialmu
    </button>
  </section>


  <!-- ════════════════════════════════════════
       FOOTER
  ════════════════════════════════════════ -->
  <footer class="relative z-10 text-center py-10 px-6">
    <div class="divider mb-6"></div>
    <p class="font-playfair italic text-slate-400 text-sm">Made with 💙 for Mbak Alfita · CLAMPER 25</p>
    <p class="font-inter text-slate-300 text-xs mt-2 tracking-widest">✦ ✦ ✦</p>
  </footer>


  <!-- ════════════════════════════════════════
       OVERLAY PESAN TERSEMBUNYI
  ════════════════════════════════════════ -->
  <div id="secretMsg" role="dialog" aria-modal="true" aria-label="Pesan rahasia">
    <div class="msg-box">
      <div class="text-4xl mb-4 animate-float inline-block">🎁</div>
      <h3 class="font-playfair text-2xl text-slate-700 mb-3">Hei Mbak Alfita, ini untukmu!</h3>
      <p class="font-inter text-slate-500 text-sm leading-7 mb-6">
        Setiap kali kamu tersenyum, dunia menjadi tempat yang sedikit lebih baik.
        Teruslah bersinar, karena cahayamu menginspirasi banyak orang di sekitarmu.
        Selamat ulang tahun — semoga ini menjadi tahun terbaikmu! 🌟
        <br /><br />
        <span class="font-playfair italic text-slate-400">— Dengan penuh sayang, CLAMPER 25</span>
      </p>
      <button onclick="closeSecret()" class="btn-primary text-sm px-8 py-3">Tutup &nbsp; ✕</button>
    </div>
  </div>


  <!-- ════════════════════════════════════════
       JAVASCRIPT
  ════════════════════════════════════════ -->
  <script>
    /* ─── KONFIGURASI TANGGAL LAHIR ─── */
    // ★ Ganti BIRTH_MONTH (1–12) dan BIRTH_DAY sesuai ulang tahun Mbak Alfita ★
    const BIRTH_MONTH = 9;
    const BIRTH_DAY   = 11;

    /* ══════════════════════════════════════
       BINTANG BERJATUHAN (Canvas)
    ══════════════════════════════════════ */
    (function () {
      const canvas = document.getElementById('starCanvas');
      const ctx    = canvas.getContext('2d');
      let stars    = [];
      const COUNT  = 60; // jumlah bintang — naikkan untuk lebih banyak

      function resize() {
        canvas.width  = window.innerWidth;
        canvas.height = window.innerHeight;
      }
      resize();
      window.addEventListener('resize', resize);

      // Bentuk bintang ✦ 4-titik
      function drawStar(cx, cy, r, alpha) {
        ctx.save();
        ctx.globalAlpha = alpha;
        ctx.fillStyle   = '#fda4af';   // pink soft
        ctx.shadowColor = '#fb7185';
        ctx.shadowBlur  = 8;
        ctx.beginPath();
        for (let i = 0; i < 8; i++) {
          const angle  = (i * Math.PI) / 4;
          const radius = i % 2 === 0 ? r : r * 0.45;
          const x = cx + radius * Math.cos(angle - Math.PI / 2);
          const y = cy + radius * Math.sin(angle - Math.PI / 2);
          i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
        }
        ctx.closePath();
        ctx.fill();
        ctx.restore();
      }

      function createStar() {
        return {
          x:     Math.random() * window.innerWidth,
          y:     -20,
          r:     Math.random() * 5 + 2,       // ukuran 2–7px
          speed: Math.random() * 1.2 + 0.4,   // kecepatan jatuh
          drift: (Math.random() - 0.5) * 0.6, // gerak kiri/kanan
          alpha: Math.random() * 0.6 + 0.4,
          rot:   0,
          rotSpeed: (Math.random() - 0.5) * 0.04,
        };
      }

      // Isi awal
      for (let i = 0; i < COUNT; i++) {
        const s = createStar();
        s.y = Math.random() * window.innerHeight; // sebar vertikal agar tidak muncul serentak
        stars.push(s);
      }

      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        stars.forEach((s, idx) => {
          s.y   += s.speed;
          s.x   += s.drift;
          s.rot += s.rotSpeed;
          drawStar(s.x, s.y, s.r, s.alpha);

          // Respawn jika keluar layar
          if (s.y > canvas.height + 20) {
            stars[idx] = createStar();
          }
        });
        requestAnimationFrame(animate);
      }
      animate();
    })();


    /* ══════════════════════════════════════
       COUNTDOWN
    ══════════════════════════════════════ */
    function getNextBirthday() {
      const now  = new Date();
      const year = now.getFullYear();
      let next   = new Date(year, BIRTH_MONTH - 1, BIRTH_DAY, 0, 0, 0);
      if (now >= next) next = new Date(year + 1, BIRTH_MONTH - 1, BIRTH_DAY, 0, 0, 0);
      return next;
    }

    function isToday() {
      const now = new Date();
      return now.getMonth() + 1 === BIRTH_MONTH && now.getDate() === BIRTH_DAY;
    }

    function renderCountdown() {
      const cdEl  = document.getElementById('countdown');
      const msgEl = document.getElementById('birthdayMsg');
      if (isToday()) { cdEl.classList.add('hidden'); msgEl.classList.remove('hidden'); return; }

      const diff  = getNextBirthday() - new Date();
      const days  = Math.floor(diff / 86400000);
      const hours = Math.floor((diff % 86400000) / 3600000);
      const mins  = Math.floor((diff % 3600000) / 60000);
      const secs  = Math.floor((diff % 60000) / 1000);

      cdEl.innerHTML = [
        { v: days, l: 'Hari' }, { v: hours, l: 'Jam' },
        { v: mins,  l: 'Menit' }, { v: secs,  l: 'Detik' },
      ].map(u => `
        <div class="countdown-box">
          <div class="digit">${String(u.v).padStart(2,'0')}</div>
          <div class="label">${u.l}</div>
        </div>`).join('');
    }
    renderCountdown();
    setInterval(renderCountdown, 1000);


    /* ══════════════════════════════════════
       GANTI FOTO — klik foto → upload dari device
    ══════════════════════════════════════ */
    const fileInput  = document.getElementById('fileInput');
    const photoToast = document.getElementById('photoToast');
    let   targetCard = null;
    let   toastTimer = null;

    document.querySelectorAll('.photo-card').forEach(card => {
      card.addEventListener('click', () => {
        targetCard = card;
        fileInput.value = ''; // reset agar bisa pilih file yang sama
        fileInput.click();
      });
    });

    fileInput.addEventListener('change', () => {
      if (!fileInput.files || !fileInput.files[0] || !targetCard) return;
      const reader = new FileReader();
      reader.onload = (e) => {
        const img = targetCard.querySelector('img');
        img.src = e.target.result;
        // Animasi flash
        img.style.transition = 'opacity 0.3s';
        img.style.opacity = '0';
        setTimeout(() => { img.style.opacity = '1'; }, 100);
        // Tampilkan toast
        clearTimeout(toastTimer);
        photoToast.classList.add('show');
        toastTimer = setTimeout(() => photoToast.classList.remove('show'), 2500);
        targetCard = null;
      };
      reader.readAsDataURL(fileInput.files[0]);
    });


    /* ══════════════════════════════════════
       CONFETTI
    ══════════════════════════════════════ */
    const CONF_COLORS = ['#fda4af','#f9a8d4','#fbcfe8','#fce7f3','#f472b6','#ffffff','#fdf2f8','#ec4899'];

    function spawnConfetti(count = 130) {
      for (let i = 0; i < count; i++) {
        setTimeout(() => {
          const p    = document.createElement('div');
          p.className = 'confetti-particle';
          const size  = Math.random() * 8 + 4;
          p.style.cssText = `
            left:${Math.random()*100}vw; top:-10px;
            width:${size}px; height:${size}px;
            background:${CONF_COLORS[Math.floor(Math.random()*CONF_COLORS.length)]};
            border-radius:${Math.random()>0.5?'50%':'2px'};
            animation-duration:${2+Math.random()*2.5}s;
            animation-delay:${Math.random()*0.4}s;
          `;
          document.body.appendChild(p);
          p.addEventListener('animationend', () => p.remove());
        }, i * 18);
      }
    }


    /* ══════════════════════════════════════
       SURPRISE BUTTON
    ══════════════════════════════════════ */
    document.getElementById('surpriseBtn').addEventListener('click', () => {
      spawnConfetti(150);
      document.getElementById('secretMsg').classList.add('show');
    });

    function closeSecret() {
      document.getElementById('secretMsg').classList.remove('show');
    }
    document.getElementById('secretMsg').addEventListener('click', function(e) {
      if (e.target === this) closeSecret();
    });
    document.addEventListener('keydown', e => { if (e.key === 'Escape') closeSecret(); });


    /* ══════════════════════════════════════
       MUSIK — YouTube IFrame API
       Video ID: Znw0tQCVFfk
    ══════════════════════════════════════ */
    const YT_VIDEO_ID = 'Znw0tQCVFfk';

    const musicBtn = document.getElementById('musicBtn');
    const iconPlay = document.getElementById('iconPlay');
    const iconMute = document.getElementById('iconMute');
    let   ytPlayer  = null;
    let   musicOn   = false;
    let   ytReady   = false;

    // Load YouTube IFrame API
    const ytScript  = document.createElement('script');
    ytScript.src    = 'https://www.youtube.com/iframe_api';
    document.head.appendChild(ytScript);

    // Callback dipanggil otomatis oleh YouTube API
    window.onYouTubeIframeAPIReady = function () {
      ytPlayer = new YT.Player('ytPlayer', {
        videoId: YT_VIDEO_ID,
        playerVars: {
          autoplay: 0,
          controls: 0,
          loop: 1,
          playlist: YT_VIDEO_ID,  // diperlukan agar loop bekerja
          mute: 0,
          enablejsapi: 1,
          origin: window.location.origin || '*',
        },
        events: {
          onReady: () => { ytReady = true; },
          onError: (e) => {
            console.warn('YT Player error:', e.data);
            // Fallback pesan jika video tidak bisa diputar
            if (musicOn) showMusicError();
          },
        },
      });
    };

    function showMusicError() {
      const toast = document.getElementById('photoToast');
      toast.textContent = '⚠️ Musik tidak dapat diputar. Coba buka di browser lain.';
      toast.classList.add('show');
      setTimeout(() => {
        toast.textContent = '✓ Foto berhasil diganti!';
        toast.classList.remove('show');
      }, 3500);
    }

    musicBtn.addEventListener('click', () => {
      if (!ytReady || !ytPlayer) {
        // Beri feedback jika API belum siap
        const toast = document.getElementById('photoToast');
        toast.textContent = '⏳ Memuat musik, coba lagi sebentar...';
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 2000);
        return;
      }

      musicOn = !musicOn;

      if (musicOn) {
        ytPlayer.playVideo();
        ytPlayer.setVolume(70); // volume 70% — ubah sesuai selera (0–100)
        iconPlay.style.display = 'none';
        iconMute.style.display = 'block';
      } else {
        ytPlayer.pauseVideo();
        iconPlay.style.display = 'block';
        iconMute.style.display = 'none';
      }
    });


    /* ══════════════════════════════════════
       SCROLL REVEAL
    ══════════════════════════════════════ */
    const observer = new IntersectionObserver(
      entries => entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); }),
      { threshold: 0.15 }
    );
    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  </script>

</body>
</html>
