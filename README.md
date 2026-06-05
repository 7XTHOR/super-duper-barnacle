<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kerala Backwaters — Boat Timings</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Nunito:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --teal-deep: #0a3d3a;
    --teal-mid: #0f5c56;
    --teal-light: #1a8c82;
    --gold: #c9a84c;
    --gold-light: #e8c97a;
    --cream: #fdf6e3;
    --cream-dark: #f5ead0;
    --brown: #6b4c2a;
    --white: #ffffff;
    --text-dark: #1a2e2d;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--cream);
    color: var(--text-dark);
    overflow-x: hidden;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: var(--teal-deep);
  }

  /* Layered SVG water scene */
  .hero-bg {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
  }

  /* Animated water ripple */
  .water-layer {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 200%;
    height: 45%;
    background: linear-gradient(180deg, transparent 0%, #0f5c5680 30%, #0a3d3a 100%);
    animation: waveDrift 14s linear infinite;
  }
  .water-layer::after {
    content: '';
    position: absolute;
    inset: 0;
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 120'%3E%3Cpath d='M0,60 C200,20 400,100 600,60 C800,20 1000,100 1200,60 L1200,120 L0,120Z' fill='%230f5c5640'/%3E%3C/svg%3E") repeat-x bottom/600px 60px;
    animation: waveDrift 8s linear infinite reverse;
  }
  @keyframes waveDrift {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  /* Sky gradient */
  .sky-gradient {
    position: absolute;
    inset: 0;
    background: linear-gradient(180deg,
      #0d2b3e 0%,
      #1a4a5a 25%,
      #2a6b6a 50%,
      #0f5c56 75%,
      #0a3d3a 100%
    );
    z-index: 0;
  }

  /* Palm tree SVG left */
  .palm-left {
    position: absolute;
    bottom: 30%;
    left: -2%;
    width: clamp(100px, 22vw, 220px);
    z-index: 2;
    opacity: 0.9;
    transform-origin: bottom center;
    animation: sway 6s ease-in-out infinite;
  }
  /* Palm tree SVG right */
  .palm-right {
    position: absolute;
    bottom: 28%;
    right: -1%;
    width: clamp(80px, 18vw, 180px);
    z-index: 2;
    opacity: 0.85;
    transform-origin: bottom center;
    animation: sway 7s ease-in-out infinite reverse;
  }
  @keyframes sway {
    0%,100% { transform: rotate(-3deg); }
    50%      { transform: rotate(3deg); }
  }

  /* Houseboat SVG */
  .houseboat {
    position: absolute;
    bottom: 32%;
    left: 50%;
    transform: translateX(-50%);
    width: clamp(180px, 50vw, 420px);
    z-index: 3;
    animation: boatFloat 5s ease-in-out infinite;
  }
  @keyframes boatFloat {
    0%,100% { transform: translateX(-50%) translateY(0px); }
    50%      { transform: translateX(-50%) translateY(-8px); }
  }

  /* Stars */
  .stars {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 55%;
    z-index: 1;
    pointer-events: none;
  }
  .star {
    position: absolute;
    width: 2px; height: 2px;
    background: white;
    border-radius: 50%;
    animation: twinkle 3s ease-in-out infinite;
  }
  @keyframes twinkle {
    0%,100% { opacity: 0.2; transform: scale(1); }
    50%      { opacity: 1; transform: scale(1.5); }
  }

  /* Lotuses / lily pads floating */
  .lotus-strip {
    position: absolute;
    bottom: 26%;
    width: 100%;
    z-index: 4;
    display: flex;
    justify-content: space-around;
    padding: 0 5%;
  }

  /* Hero text */
  .hero-content {
    position: relative;
    z-index: 5;
    text-align: center;
    padding: 0 20px;
    margin-top: -10vh;
  }
  .hero-eyebrow {
    font-family: 'Nunito', sans-serif;
    font-weight: 300;
    letter-spacing: 0.35em;
    font-size: clamp(10px, 2.5vw, 13px);
    color: var(--gold-light);
    text-transform: uppercase;
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 1s ease 0.3s forwards;
  }
  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-size: clamp(38px, 8vw, 80px);
    line-height: 1.05;
    color: var(--white);
    margin-bottom: 14px;
    opacity: 0;
    animation: fadeUp 1s ease 0.6s forwards;
  }
  .hero-title em {
    font-style: italic;
    color: var(--gold-light);
  }
  .hero-subtitle {
    font-family: 'Cormorant Garamond', serif;
    font-weight: 300;
    font-style: italic;
    font-size: clamp(14px, 3vw, 20px);
    color: rgba(255,255,255,0.7);
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 1s ease 0.9s forwards;
  }
  .scroll-cue {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    color: var(--gold-light);
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    opacity: 0;
    animation: fadeUp 1s ease 1.3s forwards;
    cursor: pointer;
  }
  .scroll-cue .arrow {
    width: 20px; height: 20px;
    border-right: 2px solid var(--gold);
    border-bottom: 2px solid var(--gold);
    transform: rotate(45deg);
    animation: bounce 2s ease-in-out infinite;
  }
  @keyframes bounce {
    0%,100% { transform: rotate(45deg) translateY(0); }
    50%      { transform: rotate(45deg) translateY(5px); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── DECORATIVE DIVIDER ── */
  .divider {
    text-align: center;
    padding: 50px 20px 10px;
    position: relative;
  }
  .divider-line {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
    margin-bottom: 10px;
  }
  .divider-line::before,
  .divider-line::after {
    content: '';
    flex: 1;
    max-width: 120px;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }
  .divider-lotus {
    font-size: 22px;
    color: var(--gold);
  }
  .section-label {
    font-family: 'Nunito', sans-serif;
    font-weight: 300;
    letter-spacing: 0.3em;
    font-size: 11px;
    color: var(--teal-mid);
    text-transform: uppercase;
  }
  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(28px, 5vw, 44px);
    font-weight: 300;
    color: var(--teal-deep);
    margin-top: 8px;
  }
  .section-title em {
    font-style: italic;
    color: var(--teal-light);
  }

  /* ── TIMINGS SECTION ── */
  .timings-section {
    padding: 20px 20px 60px;
    max-width: 900px;
    margin: 0 auto;
  }

  .route-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 28px;
    margin-top: 40px;
  }
  @media(max-width: 600px) {
    .route-cards { grid-template-columns: 1fr; }
  }

  .route-card {
    background: white;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 8px 40px rgba(10,61,58,0.12);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  .route-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 16px 60px rgba(10,61,58,0.2);
  }

  .card-header {
    padding: 28px 28px 20px;
    position: relative;
    overflow: hidden;
  }
  .card-header-kottayam {
    background: linear-gradient(135deg, var(--teal-deep) 0%, var(--teal-mid) 100%);
  }
  .card-header-alleppey {
    background: linear-gradient(135deg, #1a5c40 0%, #2a8a5a 100%);
  }
  .card-header::before {
    content: '';
    position: absolute;
    bottom: -30px; right: -30px;
    width: 100px; height: 100px;
    background: rgba(255,255,255,0.06);
    border-radius: 50%;
  }
  .card-header::after {
    content: '';
    position: absolute;
    top: -20px; right: 20px;
    width: 60px; height: 60px;
    background: rgba(255,255,255,0.04);
    border-radius: 50%;
  }

  .route-icon {
    font-size: 28px;
    margin-bottom: 10px;
    display: block;
  }
  .route-from {
    font-family: 'Nunito', sans-serif;
    font-weight: 300;
    font-size: 11px;
    letter-spacing: 0.25em;
    color: rgba(255,255,255,0.6);
    text-transform: uppercase;
    margin-bottom: 4px;
  }
  .route-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(22px, 4vw, 30px);
    font-weight: 400;
    color: white;
    line-height: 1.2;
  }
  .route-jetty {
    font-family: 'Nunito', sans-serif;
    font-weight: 300;
    font-size: 12px;
    color: var(--gold-light);
    margin-top: 6px;
    font-style: italic;
  }

  .timings-list {
    padding: 24px 28px;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .timing-item {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 12px 14px;
    border-radius: 10px;
    transition: background 0.2s ease;
    cursor: default;
  }
  .timing-item:hover {
    background: var(--cream-dark);
  }

  .time-dot {
    width: 8px; height: 8px;
    background: var(--gold);
    border-radius: 50%;
    flex-shrink: 0;
    box-shadow: 0 0 6px var(--gold);
  }

  .time-value {
    font-family: 'Cormorant Garamond', serif;
    font-size: 26px;
    font-weight: 400;
    color: var(--teal-deep);
    letter-spacing: 0.02em;
    flex: 1;
  }

  .time-period {
    font-family: 'Nunito', sans-serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.15em;
    padding: 3px 10px;
    border-radius: 20px;
    text-transform: uppercase;
  }
  .period-am {
    background: #e8f4f0;
    color: var(--teal-mid);
  }
  .period-pm {
    background: #fff4d6;
    color: #8a6200;
  }

  .timing-divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--cream-dark), transparent);
    margin: 4px 14px;
  }

  /* ── PHOTO GALLERY STRIP ── */
  .gallery-section {
    background: var(--teal-deep);
    padding: 60px 0 50px;
    overflow: hidden;
  }
  .gallery-section .divider { padding-top: 0; }
  .gallery-section .divider-line::before,
  .gallery-section .divider-line::after {
    background: linear-gradient(90deg, transparent, var(--gold-light), transparent);
  }
  .gallery-section .section-label { color: rgba(255,255,255,0.5); }
  .gallery-section .section-title { color: var(--white); }
  .gallery-section .section-title em { color: var(--gold-light); }

  .photo-strip {
    display: flex;
    gap: 16px;
    padding: 30px 20px 10px;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scrollbar-width: none;
    max-width: 900px;
    margin: 0 auto;
  }
  .photo-strip::-webkit-scrollbar { display: none; }

  .photo-card {
    flex: 0 0 clamp(200px, 60vw, 260px);
    height: 320px;
    border-radius: 16px;
    overflow: hidden;
    scroll-snap-align: start;
    position: relative;
    background: var(--teal-mid);
  }
  .photo-card svg {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .photo-card-caption {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    padding: 16px;
    background: linear-gradient(transparent, rgba(0,0,0,0.7));
    color: white;
    font-family: 'Cormorant Garamond', serif;
    font-size: 15px;
    font-style: italic;
    text-align: center;
  }

  /* ── NOTES SECTION ── */
  .notes-section {
    padding: 50px 20px 70px;
    max-width: 900px;
    margin: 0 auto;
    text-align: center;
  }
  .notes-box {
    background: white;
    border-radius: 20px;
    padding: 36px 32px;
    box-shadow: 0 4px 30px rgba(10,61,58,0.08);
    border-left: 4px solid var(--gold);
    text-align: left;
    margin-top: 30px;
  }
  .notes-box p {
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    font-weight: 300;
    color: var(--brown);
    line-height: 1.8;
    margin-bottom: 10px;
  }
  .notes-box p:last-child { margin-bottom: 0; }
  .notes-box strong { color: var(--teal-deep); font-weight: 600; }

  /* ── FOOTER ── */
  footer {
    background: var(--teal-deep);
    text-align: center;
    padding: 30px 20px;
  }
  footer p {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    color: rgba(255,255,255,0.4);
    font-size: 14px;
  }
  footer .lotus-footer {
    color: var(--gold);
    font-size: 20px;
    margin-bottom: 8px;
    display: block;
  }
</style>
</head>
<body>

<!-- ══════════════ HERO ══════════════ -->
<section class="hero">
  <div class="sky-gradient"></div>

  <!-- Twinkling stars -->
  <div class="stars" id="stars"></div>

  <!-- Water shimmer -->
  <div class="water-layer"></div>

  <!-- Palm trees (inline SVG) -->
  <svg class="palm-left" viewBox="0 0 120 260" fill="none" xmlns="http://www.w3.org/2000/svg">
    <!-- trunk -->
    <path d="M58 260 C55 200 50 150 52 100 C53 80 60 60 62 40" stroke="#5a3e1b" stroke-width="8" stroke-linecap="round"/>
    <!-- fronds -->
    <path d="M62 40 C40 20 10 30 0 50" stroke="#1a6b40" stroke-width="5" stroke-linecap="round"/>
    <path d="M62 40 C80 10 110 15 120 35" stroke="#1a6b40" stroke-width="5" stroke-linecap="round"/>
    <path d="M62 40 C50 5 60 -15 75 0" stroke="#1a6b40" stroke-width="5" stroke-linecap="round"/>
    <path d="M62 40 C35 50 15 70 20 90" stroke="#228B40" stroke-width="4" stroke-linecap="round"/>
    <path d="M62 40 C90 55 105 75 98 95" stroke="#228B40" stroke-width="4" stroke-linecap="round"/>
    <!-- coconuts -->
    <circle cx="63" cy="45" r="5" fill="#8B4513"/>
    <circle cx="56" cy="42" r="4" fill="#6B3410"/>
  </svg>

  <svg class="palm-right" viewBox="0 0 120 240" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M65 240 C67 185 70 140 68 95 C67 75 60 55 58 35" stroke="#5a3e1b" stroke-width="7" stroke-linecap="round"/>
    <path d="M58 35 C40 15 12 22 2 42" stroke="#1a6b40" stroke-width="4.5" stroke-linecap="round"/>
    <path d="M58 35 C76 8 108 12 118 32" stroke="#1a6b40" stroke-width="4.5" stroke-linecap="round"/>
    <path d="M58 35 C48 2 58 -18 72 -2" stroke="#1a6b40" stroke-width="4.5" stroke-linecap="round"/>
    <path d="M58 35 C32 45 12 65 18 85" stroke="#228B40" stroke-width="3.5" stroke-linecap="round"/>
    <path d="M58 35 C86 50 100 70 94 90" stroke="#228B40" stroke-width="3.5" stroke-linecap="round"/>
    <circle cx="59" cy="40" r="4.5" fill="#8B4513"/>
    <circle cx="53" cy="37" r="3.5" fill="#6B3410"/>
  </svg>

  <!-- Houseboat SVG illustration -->
  <svg class="houseboat" viewBox="0 0 420 160" fill="none" xmlns="http://www.w3.org/2000/svg">
    <!-- water reflection shimmer -->
    <ellipse cx="210" cy="140" rx="190" ry="14" fill="rgba(15,92,86,0.4)"/>
    <!-- hull -->
    <path d="M30 115 L390 115 L370 135 L50 135 Z" fill="#4a2c0a"/>
    <path d="M50 135 L370 135 L360 148 L60 148 Z" fill="#3a1f05"/>
    <!-- deck -->
    <rect x="40" y="100" width="340" height="18" rx="3" fill="#6b3e10"/>
    <!-- main cabin -->
    <rect x="55" y="45" width="240" height="58" rx="4" fill="#c8a96e"/>
    <!-- cabin darker stripe -->
    <rect x="55" y="45" width="240" height="8" rx="2" fill="#b8955a"/>
    <!-- windows row -->
    <rect x="70"  y="60" width="35" height="25" rx="4" fill="#87ceeb" opacity="0.8"/>
    <rect x="118" y="60" width="35" height="25" rx="4" fill="#87ceeb" opacity="0.8"/>
    <rect x="166" y="60" width="35" height="25" rx="4" fill="#87ceeb" opacity="0.75"/>
    <rect x="214" y="60" width="35" height="25" rx="4" fill="#87ceeb" opacity="0.7"/>
    <!-- window glare -->
    <rect x="72" y="62" width="10" height="6" rx="1" fill="rgba(255,255,255,0.5)"/>
    <rect x="120" y="62" width="10" height="6" rx="1" fill="rgba(255,255,255,0.5)"/>
    <rect x="168" y="62" width="10" height="6" rx="1" fill="rgba(255,255,255,0.5)"/>
    <rect x="216" y="62" width="10" height="6" rx="1" fill="rgba(255,255,255,0.5)"/>
    <!-- rear cabin -->
    <rect x="300" y="55" width="80" height="48" rx="3" fill="#b89050"/>
    <rect x="310" y="65" width="25" height="22" rx="3" fill="#87ceeb" opacity="0.75"/>
    <rect x="345" y="65" width="25" height="22" rx="3" fill="#87ceeb" opacity="0.7"/>
    <!-- roof -->
    <path d="M45 48 L295 48 L310 45 L295 25 L55 25 L40 45 Z" fill="#8b4513"/>
    <path d="M45 48 L55 25 L295 25 L295 48 Z" fill="#a0522d"/>
    <!-- chimney -->
    <rect x="200" y="12" width="10" height="16" rx="2" fill="#6b3410"/>
    <!-- flag -->
    <line x1="205" y1="12" x2="205" y2="-2" stroke="#4a2c0a" stroke-width="1.5"/>
    <path d="M205 -2 L220 4 L205 9 Z" fill="#e63946"/>
    <!-- ropes -->
    <line x1="30" y1="115" x2="10" y2="145" stroke="#8B6914" stroke-width="1.5"/>
    <line x1="390" y1="115" x2="410" y2="145" stroke="#8B6914" stroke-width="1.5"/>
    <!-- motor tail -->
    <path d="M370 128 C385 122 400 125 410 130 C405 134 395 134 385 132" fill="#4a2c0a"/>
  </svg>

  <!-- Lotus strip -->
  <div class="lotus-strip">
    <svg width="36" height="36" viewBox="0 0 36 36" fill="none">
      <ellipse cx="18" cy="30" rx="14" ry="5" fill="#1a7a70" opacity="0.7"/>
      <path d="M18 28 C14 18 8 14 10 8 C14 6 18 14 18 14 C18 14 22 6 26 8 C28 14 22 18 18 28Z" fill="#e8a0b0"/>
      <path d="M18 22 C15 15 10 12 12 7" stroke="#f0c0cc" stroke-width="1"/>
    </svg>
    <svg width="28" height="28" viewBox="0 0 36 36" fill="none" opacity="0.6">
      <ellipse cx="18" cy="30" rx="14" ry="5" fill="#1a7a70" opacity="0.7"/>
      <path d="M18 28 C14 18 8 14 10 8 C14 6 18 14 18 14 C18 14 22 6 26 8 C28 14 22 18 18 28Z" fill="#c8e0f0"/>
    </svg>
    <svg width="32" height="32" viewBox="0 0 36 36" fill="none" opacity="0.8">
      <ellipse cx="18" cy="30" rx="14" ry="5" fill="#1a7a70" opacity="0.7"/>
      <path d="M18 28 C14 18 8 14 10 8 C14 6 18 14 18 14 C18 14 22 6 26 8 C28 14 22 18 18 28Z" fill="#f0d0b0"/>
    </svg>
  </div>

  <!-- Text content -->
  <div class="hero-content">
    <p class="hero-eyebrow">God's Own Country</p>
    <h1 class="hero-title">Kerala <em>Backwaters</em></h1>
    <p class="hero-subtitle">Ferry & Boat Service Timings</p>
    <div class="scroll-cue" onclick="document.getElementById('timings').scrollIntoView()">
      <span>View Timings</span>
      <div class="arrow"></div>
    </div>
  </div>
</section>

<!-- ══════════════ TIMINGS ══════════════ -->
<section id="timings">
  <div class="divider">
    <div class="divider-line"><span class="divider-lotus">🪷</span></div>
    <p class="section-label">Public Ferry Schedule</p>
    <h2 class="section-title">Daily <em>Boat Timings</em></h2>
  </div>

  <div class="timings-section">
    <div class="route-cards">

      <!-- Kottayam Card -->
      <div class="route-card">
        <div class="card-header card-header-kottayam">
          <span class="route-icon">⛵</span>
          <p class="route-from">Departures From</p>
          <h3 class="route-name">Kottayam</h3>
          <p class="route-jetty">Kodimatha Boat Jetty</p>
        </div>
        <ul class="timings-list">
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">6:45</span>
            <span class="time-period period-am">AM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">11:30</span>
            <span class="time-period period-am">AM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">1:00</span>
            <span class="time-period period-pm">PM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">3:30</span>
            <span class="time-period period-pm">PM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">5:15</span>
            <span class="time-period period-pm">PM</span>
          </li>
        </ul>
      </div>

      <!-- Alleppey Card -->
      <div class="route-card">
        <div class="card-header card-header-alleppey">
          <span class="route-icon">🚢</span>
          <p class="route-from">Departures From</p>
          <h3 class="route-name">Alleppey</h3>
          <p class="route-jetty">Alappuzha Boat Jetty</p>
        </div>
        <ul class="timings-list">
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">7:15</span>
            <span class="time-period period-am">AM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">9:35</span>
            <span class="time-period period-am">AM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">11:30</span>
            <span class="time-period period-am">AM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">2:30</span>
            <span class="time-period period-pm">PM</span>
          </li>
          <div class="timing-divider"></div>
          <li class="timing-item">
            <div class="time-dot"></div>
            <span class="time-value">5:15</span>
            <span class="time-period period-pm">PM</span>
          </li>
        </ul>
      </div>

    </div>
  </div>
</section>

<!-- ══════════════ GALLERY STRIP ══════════════ -->
<section class="gallery-section">
  <div class="divider">
    <div class="divider-line"><span class="divider-lotus">🌿</span></div>
    <p class="section-label">The Backwater Life</p>
    <h2 class="section-title">Scenes of <em>Kerala</em></h2>
  </div>

  <div class="photo-strip">

    <!-- Card 1: Houseboat scene -->
    <div class="photo-card">
      <svg viewBox="0 0 260 320" xmlns="http://www.w3.org/2000/svg">
        <!-- Sky -->
        <defs>
          <linearGradient id="sky1" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#87ceeb"/>
            <stop offset="100%" stop-color="#b0e0f5"/>
          </linearGradient>
          <linearGradient id="water1" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#2a8a7a"/>
            <stop offset="100%" stop-color="#1a5c50"/>
          </linearGradient>
        </defs>
        <rect width="260" height="320" fill="url(#sky1)"/>
        <!-- Clouds -->
        <ellipse cx="60" cy="40" rx="40" ry="15" fill="white" opacity="0.8"/>
        <ellipse cx="90" cy="35" rx="30" ry="12" fill="white" opacity="0.7"/>
        <ellipse cx="190" cy="55" rx="35" ry="12" fill="white" opacity="0.7"/>
        <!-- Water -->
        <rect x="0" y="190" width="260" height="130" fill="url(#water1)"/>
        <!-- Water ripples -->
        <ellipse cx="130" cy="220" rx="100" ry="8" fill="rgba(255,255,255,0.1)"/>
        <ellipse cx="80" cy="250" rx="60" ry="5" fill="rgba(255,255,255,0.07)"/>
        <ellipse cx="180" cy="260" rx="50" ry="4" fill="rgba(255,255,255,0.07)"/>
        <!-- Tree line -->
        <rect x="0" y="155" width="260" height="40" fill="#0f4a30"/>
        <ellipse cx="20" cy="155" rx="22" ry="35" fill="#1a6b40"/>
        <ellipse cx="50" cy="148" rx="18" ry="30" fill="#228B40"/>
        <ellipse cx="80" cy="152" rx="20" ry="32" fill="#1a7a38"/>
        <ellipse cx="200" cy="150" rx="22" ry="34" fill="#1a6b40"/>
        <ellipse cx="230" cy="155" rx="18" ry="28" fill="#228B40"/>
        <ellipse cx="250" cy="158" rx="15" ry="25" fill="#1a7a38"/>
        <!-- Houseboat -->
        <rect x="55" y="165" width="150" height="30" rx="3" fill="#c8a96e"/>
        <rect x="55" y="163" width="150" height="6" rx="2" fill="#b8955a"/>
        <path d="M50 162 L210 162 L205 148 L55 148 Z" fill="#a0522d"/>
        <path d="M55 148 L205 148 L200 138 L60 138 Z" fill="#8b4513"/>
        <!-- Boat hull -->
        <path d="M45 195 L215 195 L205 210 L55 210 Z" fill="#4a2c0a"/>
        <!-- Windows -->
        <rect x="70" y="152" width="25" height="16" rx="3" fill="#87ceeb"/>
        <rect x="108" y="152" width="25" height="16" rx="3" fill="#87ceeb"/>
        <rect x="146" y="152" width="25" height="16" rx="3" fill="#87ceeb"/>
        <!-- Reflection -->
        <rect x="55" y="210" width="150" height="25" rx="2" fill="rgba(74,44,10,0.3)"/>
        <!-- Sun -->
        <circle cx="220" cy="60" r="20" fill="#ffd700" opacity="0.9"/>
        <circle cx="220" cy="60" r="15" fill="#ffa500"/>
        <!-- Sun rays -->
        <line x1="220" y1="35" x2="220" y2="28" stroke="#ffd700" stroke-width="2" opacity="0.6"/>
        <line x1="237" y1="43" x2="242" y2="38" stroke="#ffd700" stroke-width="2" opacity="0.6"/>
        <line x1="245" y1="60" x2="252" y2="60" stroke="#ffd700" stroke-width="2" opacity="0.6"/>
      </svg>
      <div class="photo-card-caption">Kettuvallam on the backwaters</div>
    </div>

    <!-- Card 2: Lotus pond -->
    <div class="photo-card">
      <svg viewBox="0 0 260 320" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="sky2" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#4a90a0"/>
            <stop offset="60%" stop-color="#7ec8d0"/>
            <stop offset="100%" stop-color="#2a7a6a"/>
          </linearGradient>
        </defs>
        <rect width="260" height="320" fill="url(#sky2)"/>
        <!-- Water surface -->
        <rect x="0" y="160" width="260" height="160" fill="#1a6a5a"/>
        <!-- Lily pads -->
        <ellipse cx="50" cy="200" rx="28" ry="12" fill="#2a8a40" opacity="0.9"/>
        <ellipse cx="130" cy="220" rx="32" ry="14" fill="#228B40" opacity="0.85"/>
        <ellipse cx="200" cy="195" rx="24" ry="10" fill="#2a8a40" opacity="0.9"/>
        <ellipse cx="90" cy="260" rx="20" ry="8" fill="#1a7a30" opacity="0.8"/>
        <ellipse cx="170" cy="270" rx="26" ry="10" fill="#228B40" opacity="0.8"/>
        <!-- Lotuses -->
        <!-- Lotus 1 -->
        <g transform="translate(50,185)">
          <path d="M0 12 C-6 2 -10 -6 -5 -14 C-2 -18 0 -8 0 -8 C0 -8 2 -18 5 -14 C10 -6 6 2 0 12Z" fill="#ff9eb5"/>
          <path d="M0 12 C-8 5 -14 0 -12 -8 C-8 -14 0 -8 0 -8" fill="#ffb5c5"/>
          <path d="M0 12 C8 5 14 0 12 -8 C8 -14 0 -8 0 -8" fill="#ff9eb5"/>
          <circle cx="0" cy="-5" r="3" fill="#ffd700"/>
        </g>
        <!-- Lotus 2 -->
        <g transform="translate(130,204)">
          <path d="M0 14 C-7 2 -12 -8 -6 -16 C-2 -20 0 -10 0 -10 C0 -10 2 -20 6 -16 C12 -8 7 2 0 14Z" fill="#ffb5c5"/>
          <path d="M0 14 C-10 6 -16 0 -13 -10 C-9 -16 0 -10 0 -10" fill="#ffc8d5"/>
          <path d="M0 14 C10 6 16 0 13 -10 C9 -16 0 -10 0 -10" fill="#ffb5c5"/>
          <circle cx="0" cy="-6" r="3.5" fill="#ffec40"/>
        </g>
        <!-- Lotus 3 -->
        <g transform="translate(200,180)">
          <path d="M0 10 C-5 2 -9 -5 -4 -12 C-1 -16 0 -7 0 -7 C0 -7 1 -16 4 -12 C9 -5 5 2 0 10Z" fill="#e8d0f0"/>
          <circle cx="0" cy="-4" r="2.5" fill="#ffd700"/>
        </g>
        <!-- Coconut palms -->
        <path d="M10 160 C12 120 15 80 14 40" stroke="#5a3e1b" stroke-width="7" stroke-linecap="round"/>
        <path d="M14 40 C-5 20 -20 28 -18 48" stroke="#1a6b40" stroke-width="4" stroke-linecap="round"/>
        <path d="M14 40 C32 14 50 20 48 40" stroke="#1a6b40" stroke-width="4" stroke-linecap="round"/>
        <path d="M14 40 C10 10 18 -8 28 5" stroke="#228B40" stroke-width="3.5" stroke-linecap="round"/>
        <!-- Birds -->
        <path d="M80 80 C85 75 92 75 97 80" stroke="white" stroke-width="1.5" fill="none"/>
        <path d="M110 65 C115 60 122 60 127 65" stroke="white" stroke-width="1.5" fill="none"/>
        <path d="M140 85 C144 80 150 80 154 85" stroke="white" stroke-width="1.5" fill="none"/>
      </svg>
      <div class="photo-card-caption">Lotus blooms in still waters</div>
    </div>

    <!-- Card 3: Village sunset -->
    <div class="photo-card">
      <svg viewBox="0 0 260 320" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="sunset" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#1a0a3a"/>
            <stop offset="35%" stop-color="#8b1a4a"/>
            <stop offset="65%" stop-color="#e06030"/>
            <stop offset="85%" stop-color="#f0a040"/>
            <stop offset="100%" stop-color="#c85020"/>
          </linearGradient>
          <linearGradient id="water3" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#8b3020"/>
            <stop offset="100%" stop-color="#1a2a40"/>
          </linearGradient>
        </defs>
        <rect width="260" height="320" fill="url(#sunset)"/>
        <!-- Sun / glow -->
        <circle cx="130" cy="175" r="35" fill="#ffd700" opacity="0.9"/>
        <circle cx="130" cy="175" r="28" fill="#ffa500"/>
        <circle cx="130" cy="175" r="20" fill="#ff8c00"/>
        <!-- Glow halo -->
        <circle cx="130" cy="175" r="55" fill="rgba(255,160,0,0.15)"/>
        <circle cx="130" cy="175" r="75" fill="rgba(255,120,0,0.08)"/>
        <!-- Water -->
        <rect x="0" y="210" width="260" height="110" fill="url(#water3)"/>
        <!-- Sun reflection on water -->
        <path d="M110 210 L150 210 L170 320 L90 320 Z" fill="rgba(255,180,0,0.25)"/>
        <!-- Water ripples -->
        <ellipse cx="130" cy="230" rx="80" ry="6" fill="rgba(255,140,0,0.15)"/>
        <ellipse cx="130" cy="255" rx="60" ry="4" fill="rgba(255,140,0,0.1)"/>
        <!-- Silhouette - land/trees -->
        <path d="M0 200 L30 185 L50 195 L70 172 L90 182 L120 168 L140 175 L160 165 L185 178 L200 168 L220 180 L240 172 L260 180 L260 210 L0 210 Z" fill="#0a1a10"/>
        <!-- Church/temple silhouette -->
        <rect x="100" y="148" width="20" height="20" fill="#0a1a10"/>
        <path d="M105 148 L110 138 L115 148 Z" fill="#0a1a10"/>
        <line x1="110" y1="138" x2="110" y2="132" stroke="#0a1a10" stroke-width="2"/>
        <!-- Boat silhouette on water -->
        <path d="M60 220 L120 215 L130 225 L50 228 Z" fill="#0a1a10"/>
        <rect x="80" y="206" width="30" height="12" rx="2" fill="#0a1a10"/>
        <!-- Stars -->
        <circle cx="30" cy="30" r="1.5" fill="white" opacity="0.8"/>
        <circle cx="70" cy="15" r="1" fill="white" opacity="0.7"/>
        <circle cx="50" cy="55" r="1.5" fill="white" opacity="0.6"/>
        <circle cx="200" cy="25" r="1" fill="white" opacity="0.8"/>
        <circle cx="220" cy="60" r="1.5" fill="white" opacity="0.7"/>
        <circle cx="180" cy="45" r="1" fill="white" opacity="0.6"/>
      </svg>
      <div class="photo-card-caption">Sunset over Vembanad Lake</div>
    </div>

    <!-- Card 4: Canoe / local boat -->
    <div class="photo-card">
      <svg viewBox="0 0 260 320" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="sky4" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#6ab8c8"/>
            <stop offset="100%" stop-color="#a0d8e8"/>
          </linearGradient>
          <linearGradient id="water4" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#1a7a6a"/>
            <stop offset="100%" stop-color="#0a4a40"/>
          </linearGradient>
        </defs>
        <rect width="260" height="320" fill="url(#sky4)"/>
        <!-- Background greenery -->
        <rect x="0" y="140" width="260" height="60" fill="#0f4a30"/>
        <ellipse cx="0" cy="140" rx="40" ry="50" fill="#1a6b40"/>
        <ellipse cx="40" cy="135" rx="35" ry="45" fill="#228B40"/>
        <ellipse cx="80" cy="138" rx="30" ry="40" fill="#1a7a38"/>
        <ellipse cx="180" cy="136" rx="35" ry="48" fill="#1a6b40"/>
        <ellipse cx="220" cy="140" rx="30" ry="42" fill="#228B40"/>
        <ellipse cx="255" cy="138" rx="25" ry="38" fill="#1a7a38"/>
        <!-- Water -->
        <rect x="0" y="185" width="260" height="135" fill="url(#water4)"/>
        <!-- Water reflections -->
        <ellipse cx="130" cy="210" rx="110" ry="10" fill="rgba(255,255,255,0.08)"/>
        <ellipse cx="80" cy="240" rx="70" ry="6" fill="rgba(255,255,255,0.06)"/>
        <ellipse cx="190" cy="260" rx="55" ry="5" fill="rgba(255,255,255,0.06)"/>
        <!-- Traditional canoe/boat -->
        <path d="M30 215 Q130 205 230 215 Q220 235 130 240 Q40 238 30 215 Z" fill="#6b3e10"/>
        <path d="M35 215 Q130 208 225 215" stroke="#8b5a20" stroke-width="2" fill="none"/>
        <!-- Person silhouette with paddle -->
        <circle cx="130" cy="200" r="8" fill="#1a1a10"/>
        <rect x="126" y="208" width="8" height="20" fill="#1a1a10"/>
        <!-- Paddle -->
        <line x1="110" y1="195" x2="150" y2="220" stroke="#5a3e1b" stroke-width="3"/>
        <ellipse cx="108" cy="193" rx="5" ry="10" fill="#6b4e2b" transform="rotate(-30 108 193)"/>
        <!-- Coconut palm overhanging -->
        <path d="M260 185 C250 150 242 110 244 70" stroke="#5a3e1b" stroke-width="8" stroke-linecap="round"/>
        <path d="M244 70 C220 50 200 58 198 78" stroke="#1a6b40" stroke-width="5" stroke-linecap="round"/>
        <path d="M244 70 C260 42 280 48 278 68" stroke="#1a6b40" stroke-width="5" stroke-linecap="round"/>
        <path d="M244 70 C238 38 248 18 260 32" stroke="#228B40" stroke-width="4" stroke-linecap="round"/>
        <circle cx="245" cy="76" r="5" fill="#8B4513"/>
        <!-- Kingfisher bird -->
        <g transform="translate(70,150)">
          <ellipse cx="0" cy="0" rx="8" ry="4" fill="#1a5a8a"/>
          <circle cx="6" cy="-2" r="4" fill="#1a5a8a"/>
          <path d="M10 -2 L16 -1 L10 1 Z" fill="#ff6600"/>
          <circle cx="7" cy="-3" r="1" fill="white"/>
          <rect x="-4" y="3" width="2" height="6" fill="#ff8800" rx="1"/>
          <rect x="0" y="3" width="2" height="6" fill="#ff8800" rx="1"/>
        </g>
      </svg>
      <div class="photo-card-caption">A fisherman rows at dawn</div>
    </div>

  </div>
</section>

<!-- ══════════════ NOTES ══════════════ -->
<section>
  <div class="divider">
    <div class="divider-line"><span class="divider-lotus">🌴</span></div>
    <p class="section-label">Traveller's Tips</p>
    <h2 class="section-title">Before You <em>Board</em></h2>
  </div>

  <div class="notes-section">
    <div class="notes-box">
      <p>🕐 <strong>Arrive early</strong> — Jetties can get busy, especially the 6:45 AM and 5:15 PM services. Plan to arrive 15 minutes before departure.</p>
      <p>🎟️ <strong>Tickets</strong> — Tokens are available at the jetty counter. The Kottayam–Alleppey backwater route is operated by SWTD (State Water Transport Department).</p>
      <p>🌧️ <strong>Monsoon season</strong> — Services may be affected during heavy rain (June–August). Check with the jetty on the day of travel.</p>
      <p>📸 <strong>Photography</strong> — The early morning and evening services offer magical light over the backwaters. Bring a camera!</p>
      <p>🐦 <strong>Wildlife</strong> — Watch for kingfishers, cormorants, and otters along the canal banks during the journey.</p>
    </div>
  </div>
</section>

<!-- ══════════════ FOOTER ══════════════ -->
<footer>
  <span class="lotus-footer">🪷</span>
  <p>Kottayam ↔ Alleppey Backwater Ferry — God's Own Country</p>
</footer>

<script>
  // Generate twinkling stars
  const starsContainer = document.getElementById('stars');
  for (let i = 0; i < 60; i++) {
    const star = document.createElement('div');
    star.className = 'star';
    star.style.cssText = `
      left: ${Math.random() * 100}%;
      top: ${Math.random() * 100}%;
      animation-delay: ${Math.random() * 4}s;
      animation-duration: ${2 + Math.random() * 3}s;
      width: ${Math.random() > 0.7 ? 3 : 2}px;
      height: ${Math.random() > 0.7 ? 3 : 2}px;
      opacity: ${0.2 + Math.random() * 0.4};
    `;
    starsContainer.appendChild(star);
  }

  // Animate timing cards on scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.route-card').forEach((card, i) => {
    card.style.opacity = '0';
    card.style.transform = 'translateY(30px)';
    card.style.transition = `opacity 0.6s ease ${i * 0.15}s, transform 0.6s ease ${i * 0.15}s, box-shadow 0.3s ease`;
    observer.observe(card);
  });
</script>

</body>
</html>
