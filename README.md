<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Coming King Mission Worldwide</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;900&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --purple: #6B21A8; --purple-light: #A855F7; --purple-dark: #3B0764;
    --gold: #B8860B; --gold-light: #D4AF37; --gold-glow: #FFD700;
    --silver: #C0C0C0; --silver-light: #E8E8F0; --white: #FFFFFF; --bg: #F5F0FF;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Inter', sans-serif; background: var(--bg); color: #1a0533; overflow-x: hidden; }

  /* PAGE SYSTEM */
  .page { display: none; }
  .page.active { display: block; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    background: rgba(59,7,100,0.97); backdrop-filter: blur(12px);
    border-bottom: 2px solid var(--gold);
    padding: 0 5vw; display: flex; align-items: center; justify-content: space-between; height: 70px;
  }
  nav ul { list-style: none; display: flex; gap: 2rem; align-items: center; margin: 0; padding: 0; }
  .nav-logo { display: flex; align-items: center; gap: 0.75rem; cursor: pointer; }
  .nav-logo img { height: 48px; width: auto; }
  .nav-name { font-family: 'Cinzel', serif; font-size: 1rem; font-weight: 700; color: var(--gold-light); line-height: 1.2; }
  .nav-name span { display: block; font-size: 0.65rem; color: var(--silver); font-weight: 400; letter-spacing: 0.15em; text-transform: uppercase; }
  nav ul { list-style: none; display: flex; gap: 2rem; }
  nav ul a { text-decoration: none; color: #FFFFFF; font-size: 0.85rem; font-weight: 600; transition: color 0.2s; letter-spacing: 0.05em; cursor: pointer; text-shadow: 0 1px 4px rgba(0,0,0,0.5); }
  nav ul a:hover { color: var(--gold-glow); }
  .give-btn {
    background: linear-gradient(135deg, var(--gold), var(--gold-light));
    color: var(--purple-dark); border: none; cursor: pointer;
    padding: 0.5rem 1.25rem; border-radius: 100px;
    font-size: 0.85rem; font-weight: 700; font-family: 'Inter', sans-serif;
    transition: all 0.2s; letter-spacing: 0.05em;
  }
  .give-btn:hover { transform: scale(1.05); box-shadow: 0 0 16px rgba(212,175,55,0.5); }

  /* HERO */
  .hero {
    min-height: 100vh; display: flex; align-items: center;
    padding: 90px 6vw 60px;
    position: relative; overflow: hidden;
    background: linear-gradient(135deg, #1a0533 0%, #3B0764 50%, #1a0533 100%);
  }
  .hero-bg {
    position: absolute; inset: 0;
    background-image: url('https://i.ibb.co/6RNX3mgp/file-000000005724724380ba8b8ae201fa00.png');
    background-size: cover; background-position: center; opacity: 0.12;
  }
  .hero::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(26,5,51,0.92) 0%, rgba(59,7,100,0.85) 50%, rgba(26,5,51,0.92) 100%);
    z-index: 1;
  }
  .hero::after {
    content: ''; position: absolute; inset: 0;
    background: radial-gradient(ellipse at 20% 50%, rgba(212,175,55,0.08) 0%, transparent 60%),
                radial-gradient(ellipse at 80% 20%, rgba(168,85,247,0.1) 0%, transparent 50%);
    z-index: 1; animation: shimmer 6s ease-in-out infinite;
  }
  @keyframes shimmer { 0%,100%{opacity:0.6} 50%{opacity:1} }
  .hero-content { position: relative; z-index: 2; max-width: 600px; }
  .hero-logo { width: 120px; margin-bottom: 1.5rem; filter: drop-shadow(0 0 20px rgba(212,175,55,0.6)); animation: floatLogo 4s ease-in-out infinite; }
  @keyframes floatLogo { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-10px)} }
  .hero-tag {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: rgba(212,175,55,0.15); border: 1px solid var(--gold);
    color: var(--gold-light); padding: 0.35rem 1rem; border-radius: 100px;
    font-size: 0.78rem; font-weight: 600; letter-spacing: 0.1em;
    text-transform: uppercase; margin-bottom: 1.25rem;
  }
  .hero h1 { font-family: 'Cinzel', serif; font-size: clamp(2rem, 5vw, 3.8rem); font-weight: 900; line-height: 1.1; color: var(--white); margin-bottom: 0.5rem; }
  .hero h1 span { color: var(--gold-glow); }
  .hero-sub { font-family: 'Cinzel', serif; font-size: clamp(0.9rem, 2vw, 1.2rem); color: var(--silver); letter-spacing: 0.2em; text-transform: uppercase; margin-bottom: 1.5rem; }
  .hero p { font-size: 1rem; font-weight: 300; color: #D8B4FE; line-height: 1.8; margin-bottom: 2rem; max-width: 500px; }
  .hero-cta { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn-gold { background: linear-gradient(135deg, var(--gold), var(--gold-light)); color: var(--purple-dark); text-decoration: none; padding: 0.9rem 2rem; border-radius: 100px; font-weight: 700; font-size: 0.95rem; border: none; cursor: pointer; font-family: 'Inter', sans-serif; transition: all 0.2s; box-shadow: 0 4px 20px rgba(212,175,55,0.3); }
  .btn-gold:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(212,175,55,0.5); }
  .btn-outline-gold { background: transparent; color: var(--gold-light); text-decoration: none; padding: 0.9rem 2rem; border-radius: 100px; font-weight: 600; font-size: 0.95rem; border: 2px solid var(--gold); transition: all 0.2s; cursor: pointer; font-family: 'Inter', sans-serif; }
  .btn-outline-gold:hover { background: var(--gold); color: var(--purple-dark); transform: translateY(-2px); }
  .hero-visual { position: absolute; right: 0; bottom: 0; top: 70px; z-index: 2; width: 420px; max-width: 38vw; display: flex; align-items: flex-end; }
  .hero-visual img { width: 100%; height: 100%; object-fit: cover; object-position: top; -webkit-mask-image: linear-gradient(to left, rgba(0,0,0,0.9) 40%, transparent 100%); mask-image: linear-gradient(to left, rgba(0,0,0,0.9) 40%, transparent 100%); filter: drop-shadow(-10px 0 30px rgba(107,33,168,0.5)); }

  /* SERVICE BAR */
  .service-bar { background: linear-gradient(135deg, var(--gold), var(--gold-light), var(--gold)); padding: 1.25rem 6vw; display: flex; justify-content: center; gap: 4rem; flex-wrap: wrap; }
  .service-item { display: flex; align-items: center; gap: 0.6rem; color: var(--purple-dark); font-weight: 700; font-size: 0.9rem; }

  .section-label { font-size: 0.75rem; font-weight: 600; text-transform: uppercase; letter-spacing: 0.15em; color: var(--gold-light); margin-bottom: 0.5rem; }
  .section-title { font-family: 'Cinzel', serif; font-size: clamp(1.6rem, 3.5vw, 2.5rem); font-weight: 700; line-height: 1.2; }

  /* SLIDESHOW */
  .slideshow-section { padding: 5rem 6vw; background: linear-gradient(135deg, #1a0533, #3B0764); }
  .slideshow-section .section-title { color: var(--white); text-align: center; margin-bottom: 0.5rem; }
  .slideshow-section .section-label { text-align: center; }
  .slideshow-wrapper { position: relative; max-width: 900px; margin: 2.5rem auto 0; border-radius: 20px; overflow: hidden; box-shadow: 0 24px 60px rgba(0,0,0,0.5); border: 2px solid var(--gold); }
  .slide { display: none; position: relative; }
  .slide.active { display: block; }
  .slide img { width: 100%; height: 480px; object-fit: cover; }
  .slide-caption {
    position: absolute; bottom: 0; left: 0; right: 0;
    background: linear-gradient(to top, rgba(26,5,51,0.95) 0%, transparent 100%);
    padding: 2rem 1.5rem 1.5rem;
    font-family: 'Cinzel', serif; color: var(--gold-light);
    font-size: 1rem; font-weight: 600; text-align: center; letter-spacing: 0.08em;
  }
  .slide-controls { display: flex; justify-content: center; align-items: center; gap: 1rem; margin-top: 1.25rem; }
  .slide-btn {
    background: rgba(212,175,55,0.15); border: 1px solid var(--gold);
    color: var(--gold-light); width: 42px; height: 42px; border-radius: 50%;
    font-size: 1.2rem; cursor: pointer; transition: all 0.2s;
    display: flex; align-items: center; justify-content: center;
  }
  .slide-btn:hover { background: var(--gold); color: var(--purple-dark); }
  .slide-dots { display: flex; gap: 0.5rem; }
  .dot { width: 10px; height: 10px; border-radius: 50%; background: rgba(212,175,55,0.3); cursor: pointer; transition: background 0.2s; }
  .dot.active { background: var(--gold-light); }

  /* ABOUT */
  .about-section { padding: 6rem 6vw; background: linear-gradient(135deg, #F5F0FF 0%, #EDE9FE 100%); }
  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; max-width: 1100px; margin: 0 auto; }
  .about-text .section-title { color: var(--purple-dark); margin-bottom: 1.25rem; }
  .about-text p { color: #4C1D95; font-weight: 300; line-height: 1.9; font-size: 0.95rem; margin-bottom: 1rem; }
  .about-img { border-radius: 20px; overflow: hidden; box-shadow: 0 20px 60px rgba(107,33,168,0.35); position: relative; }
  .about-img img { width: 100%; height: 420px; object-fit: cover; object-position: center; }
  .about-img::before { content: ''; position: absolute; inset: 0; border-radius: 20px; border: 3px solid var(--gold-light); z-index: 2; pointer-events: none; }
  .about-img::after { content: 'Worship at Coming King Mission'; position: absolute; bottom: 0; left: 0; right: 0; background: linear-gradient(to top, rgba(59,7,100,0.92) 0%, transparent 100%); color: var(--gold-light); font-family: 'Cinzel', serif; font-size: 1rem; font-weight: 700; padding: 2rem 1.5rem 1.25rem; z-index: 2; letter-spacing: 0.08em; text-align: center; }

  /* MISSION & VISION */
  .mv-section { background: linear-gradient(135deg, #3B0764 0%, #1a0533 50%, #3B0764 100%); padding: 6rem 6vw; }
  .mv-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; max-width: 900px; margin: 3rem auto 0; }
  .mv-card { background: rgba(255,255,255,0.05); border: 1px solid rgba(212,175,55,0.3); border-radius: 20px; padding: 2.5rem; position: relative; overflow: hidden; transition: transform 0.25s, box-shadow 0.25s; }
  .mv-card:hover { transform: translateY(-4px); box-shadow: 0 20px 40px rgba(212,175,55,0.15); }
  .mv-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--gold), var(--gold-light)); }
  .mv-icon { font-size: 2.5rem; margin-bottom: 1rem; }
  .mv-card h3 { font-family: 'Cinzel', serif; color: var(--gold-light); font-size: 1.3rem; margin-bottom: 1rem; }
  .mv-card p { color: #D8B4FE; font-weight: 300; line-height: 1.8; font-size: 0.92rem; }

  /* PASTOR */
  .pastor-section { padding: 6rem 6vw; background: linear-gradient(135deg, #F5F0FF, #EDE9FE); text-align: center; }
  .pastor-card { max-width: 700px; margin: 3rem auto 0; background: white; border-radius: 24px; padding: 3rem; box-shadow: 0 20px 60px rgba(107,33,168,0.12); border: 1px solid rgba(212,175,55,0.3); position: relative; overflow: hidden; }
  .pastor-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 4px; background: linear-gradient(90deg, var(--purple), var(--gold), var(--purple)); }
  .pastor-avatar { width: 100px; height: 100px; border-radius: 50%; background: linear-gradient(135deg, var(--purple), var(--gold)); display: flex; align-items: center; justify-content: center; font-size: 2.5rem; margin: 0 auto 1.5rem; box-shadow: 0 8px 24px rgba(107,33,168,0.3); }
  .pastor-name { font-family: 'Cinzel', serif; font-size: 1.5rem; color: var(--purple-dark); font-weight: 700; }
  .pastor-title { color: var(--gold); font-size: 0.9rem; font-weight: 600; margin: 0.25rem 0 1rem; text-transform: uppercase; letter-spacing: 0.1em; }
  .pastor-card p { color: #4C1D95; font-weight: 300; line-height: 1.8; font-size: 0.92rem; }

  /* EVENTS PAGE */
  .events-page { padding: 100px 6vw 6rem; background: linear-gradient(135deg, #1a0533, #3B0764); min-height: 100vh; }
  .events-page .section-title { color: var(--white); text-align: center; margin-bottom: 0.5rem; }
  .events-page .section-label { text-align: center; }
  .events-page-intro { text-align: center; color: #D8B4FE; font-weight: 300; margin: 1rem 0 3rem; font-size: 0.95rem; }
  .events-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1.5rem; max-width: 1000px; margin: 0 auto; }
  .event-card { background: rgba(255,255,255,0.05); border: 1px solid rgba(212,175,55,0.3); border-radius: 20px; padding: 2rem; position: relative; overflow: hidden; transition: transform 0.25s, box-shadow 0.25s; }
  .event-card:hover { transform: translateY(-4px); box-shadow: 0 20px 40px rgba(212,175,55,0.15); }
  .event-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: linear-gradient(90deg, var(--gold), var(--gold-light)); }
  .event-date { background: linear-gradient(135deg, var(--gold), var(--gold-light)); color: var(--purple-dark); display: inline-block; padding: 0.3rem 0.9rem; border-radius: 100px; font-size: 0.78rem; font-weight: 700; margin-bottom: 1rem; letter-spacing: 0.05em; }
  .event-card h3 { font-family: 'Cinzel', serif; color: var(--gold-light); font-size: 1.1rem; margin-bottom: 0.75rem; }
  .event-card p { color: #D8B4FE; font-size: 0.88rem; font-weight: 300; line-height: 1.7; }
  .no-events { text-align: center; color: #D8B4FE; padding: 3rem; border: 2px dashed rgba(212,175,55,0.3); border-radius: 20px; max-width: 600px; margin: 0 auto; }
  .no-events div { font-size: 3rem; margin-bottom: 1rem; }
  .back-btn { display: inline-flex; align-items: center; gap: 0.5rem; background: rgba(212,175,55,0.15); border: 1px solid var(--gold); color: var(--gold-light); padding: 0.6rem 1.5rem; border-radius: 100px; font-size: 0.88rem; font-weight: 600; cursor: pointer; transition: all 0.2s; margin-bottom: 2rem; font-family: 'Inter', sans-serif; }
  .back-btn:hover { background: var(--gold); color: var(--purple-dark); }

  /* SOCIAL */
  .social-section { padding: 4rem 6vw; background: linear-gradient(135deg, #F5F0FF, #EDE9FE); text-align: center; }
  .social-section .section-title { color: var(--purple-dark); margin-bottom: 0.75rem; }
  .social-section > p { color: #6B21A8; font-weight: 300; margin-bottom: 2rem; }
  .social-links { display: flex; gap: 1.25rem; justify-content: center; flex-wrap: wrap; }
  .social-link { display: inline-flex; align-items: center; gap: 0.6rem; padding: 0.75rem 1.5rem; border-radius: 100px; font-weight: 600; font-size: 0.9rem; text-decoration: none; transition: all 0.2s; border: 2px solid; }
  .social-link.tiktok { background: #000; color: white; border-color: #000; }
  .social-link.tiktok:hover { background: #333; transform: translateY(-2px); }
  .social-link.twitter { background: #000; color: white; border-color: #000; }
  .social-link.twitter:hover { background: #333; transform: translateY(-2px); }

  /* CONTACT */
  .contact-section { padding: 5rem 6vw; background: linear-gradient(135deg, #3B0764 0%, #1a0533 100%); text-align: center; }
  .contact-section .section-title { color: var(--white); margin-bottom: 3rem; }
  .contact-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1.5rem; max-width: 900px; margin: 0 auto; }
  .contact-card { background: rgba(255,255,255,0.06); border: 1px solid rgba(212,175,55,0.25); border-radius: 16px; padding: 1.75rem; transition: transform 0.2s, box-shadow 0.2s; }
  .contact-card:hover { transform: translateY(-4px); box-shadow: 0 12px 30px rgba(212,175,55,0.1); }
  .contact-icon { font-size: 2rem; margin-bottom: 0.75rem; }
  .contact-card h4 { font-family: 'Cinzel', serif; color: var(--gold-light); font-size: 0.9rem; margin-bottom: 0.5rem; text-transform: uppercase; letter-spacing: 0.1em; }
  .contact-card p, .contact-card a { color: #D8B4FE; font-size: 0.88rem; font-weight: 300; line-height: 1.6; text-decoration: none; display: block; }
  .contact-card a:hover { color: var(--gold-light); }
  .wa-contact { display: inline-flex; align-items: center; gap: 0.4rem; background: #25D366; color: white; padding: 0.5rem 1.25rem; border-radius: 100px; font-size: 0.85rem; font-weight: 600; text-decoration: none; margin-top: 0.75rem; transition: background 0.2s; }
  .wa-contact:hover { background: #1ebe5d; }

  /* VERSE */
  .verse-banner { background: linear-gradient(135deg, var(--gold), var(--gold-light), var(--gold)); padding: 2rem 6vw; text-align: center; }
  .verse-banner p { font-family: 'Cinzel', serif; color: var(--purple-dark); font-size: clamp(0.9rem, 2vw, 1.2rem); font-weight: 600; font-style: italic; line-height: 1.6; }
  .verse-banner span { display: block; font-size: 0.8rem; margin-top: 0.4rem; font-style: normal; letter-spacing: 0.1em; }

  /* FOOTER */
  footer { background: #0D0021; padding: 2.5rem 6vw; text-align: center; color: #7C3AED; font-size: 0.82rem; border-top: 1px solid rgba(212,175,55,0.2); }
  footer .foot-logo { font-family: 'Cinzel', serif; color: var(--gold-light); font-size: 1rem; font-weight: 700; margin-bottom: 0.5rem; }
  footer p { font-weight: 300; line-height: 1.7; }
  footer a { color: var(--gold-light); text-decoration: none; }

  @media (max-width: 900px) {
    .hero-visual { display: none; }
    .about-grid { grid-template-columns: 1fr; }
    .mv-grid { grid-template-columns: 1fr; }
    nav ul { display: none; }
    .slide img { height: 280px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo" onclick="showPage('home')">
    <img src="https://i.ibb.co/gF4yxfkW/LOGO-WHITE-BACKGROUND-1.png" onerror="this.style.display='none'" alt="Coming King Mission Worldwide Logo">
    <div class="nav-name">Coming King Mission Worldwide<span>Preparing for the Return of Christ</span></div>
  </div>
  <ul>
    <li><a onclick="showPage('home')">Home</a></li>
    <li><a onclick="showPage('home'); scrollTo('#about')">About</a></li>
    <li><a onclick="showPage('events')">Upcoming Events</a></li>
    <li><a onclick="showPage('home'); scrollTo('#contact')">Contact</a></li>
  </ul>
  <button class="give-btn" onclick="window.open('https://wa.me/2349013546550?text=Hello%2C%20I%20would%20like%20to%20give%20an%20offering%20to%20Coming%20King%20Mission%20Worldwide.%20Please%20send%20me%20the%20account%20details.','_blank')">Give Online</button>
</nav>

<!-- HOME PAGE -->
<div class="page active" id="page-home">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <img class="hero-logo" src="https://i.ibb.co/gF4yxfkW/LOGO-WHITE-BACKGROUND-1.png" onerror="this.style.display='none'" alt="Coming King Mission Worldwide">
      <div class="hero-tag">✝ Preparing for the Return of Christ</div>
      <h1>Coming <span>King</span><br>Mission Worldwide</h1>
      <div class="hero-sub">Apostle & Rev'd Mrs. Phil Ihegazie</div>
      <p>A Christ-centered ministry dedicated to preparing people for the glorious return of our Lord and Savior, Jesus Christ — through the Word, Prayer, and the Holy Spirit.</p>
      <div class="hero-cta">
        <a href="#about" class="btn-gold" onclick="showPage('home')">About Our Church</a>
        <a class="btn-outline-gold" onclick="showPage('events')" style="cursor:pointer">Upcoming Events</a>
      </div>
    </div>
    <div class="hero-visual">
      <img src="https://i.ibb.co/Lzy7fjzX/file-00000000d07871f49f9c883b6dd0795b.png" onerror="this.style.display='none'" alt="Apostle Phil Ihegazie">
    </div>
  </section>

  <!-- SERVICE BAR -->
  <div class="service-bar">
    <div class="service-item"><strong>Sunday Service</strong> — Join Us Every Sunday</div>
    <div class="service-item"><strong>Monday Service</strong> — Join Us Every Monday</div>
    <div class="service-item">📍 <strong>Cooperative Market, Nike, Enugu</strong></div>
  </div>

  <!-- VERSE -->
  <div class="verse-banner">
    <p>"And the glory which thou gavest me I have given them; that they may be one, even as we are one."
      <span>— John 17:22</span>
    </p>
  </div>

  <!-- SLIDESHOW -->
  <section class="slideshow-section">
    <div class="section-label">Our Church Family</div>
    <h2 class="section-title">Life at Coming King Mission</h2>
    <div class="slideshow-wrapper">
      <div class="slide active">
        <img src="https://i.ibb.co/Lzy7fjzX/file-00000000d07871f49f9c883b6dd0795b.png" alt="Pastor Preaching">
        <div class="slide-caption">Apostle Phil Ihegazie — Ministering the Word</div>
      </div>
      <div class="slide">
        <img src="https://i.ibb.co/S4KVDT8h/file-000000007e3c71f4a17bf153ad4c91fc.png" alt="Church Family">
        <div class="slide-caption">Our Church Family — United in Christ</div>
      </div>
      <div class="slide">
        <img src="https://i.ibb.co/PsVxm18g/file-00000000bd60724390932a2cb44a8398.png" alt="Apostle Preaching">
        <div class="slide-caption">Proclaiming the Gospel with Power</div>
      </div>
      <div class="slide">
        <img src="https://i.ibb.co/6RNX3mgp/file-000000005724724380ba8b8ae201fa00.png" alt="Worship">
        <div class="slide-caption">Worship — Lifting Our Voices to God</div>
      </div>
    </div>
    <div class="slide-controls">
      <button class="slide-btn" onclick="changeSlide(-1)">&#8592;</button>
      <div class="slide-dots" id="dots"></div>
      <button class="slide-btn" onclick="changeSlide(1)">&#8594;</button>
    </div>
  </section>

  <!-- ABOUT -->
  <section class="about-section" id="about">
    <div class="about-grid">
      <div class="about-text">
        <div class="section-label">Who We Are</div>
        <h2 class="section-title" style="color:var(--purple-dark)">Welcome to<br>Coming King Mission Worldwide</h2>
        <p>Welcome to Coming King Mission Worldwide, a Christ-centered ministry dedicated to preparing people for the glorious return of our Lord and Savior, Jesus Christ.</p>
        <p>Founded upon the unchanging truth of God's Word, our mission is to equip believers through sound biblical teaching, discipleship, prayer, and spiritual growth.</p>
        <p>At Coming King Mission Worldwide, we are committed to proclaiming the Gospel of Jesus Christ, raising mature disciples, and empowering individuals to fulfill their God-given purpose.</p>
        <p>Our desire is to see men and women from every nation develop a deeper relationship with God, grow in spiritual maturity, and become effective ambassadors of Christ in their homes, communities, and the world.</p>
      </div>
      <div class="about-img">
        <img src="https://i.ibb.co/6RNX3mgp/file-000000005724724380ba8b8ae201fa00.png" alt="Worship at Coming King Mission Worldwide">
      </div>
    </div>
  </section>

  <!-- MISSION & VISION -->
  <section class="mv-section" id="mission">
    <div style="text-align:center">
      <div class="section-label" style="text-align:center">Our Foundation</div>
      <h2 class="section-title" style="color:var(--white);text-align:center">Mission & Vision</h2>
    </div>
    <div class="mv-grid">
      <div class="mv-card">
        <div class="mv-icon">🎯</div>
        <h3>Our Mission</h3>
        <p>To prepare people for the Coming of Jesus Christ through the teaching, preaching, and practical application of God's Word.</p>
      </div>
      <div class="mv-card">
        <div class="mv-icon">🔭</div>
        <h3>Our Vision</h3>
        <p>To raise a generation of believers who are spiritually mature, rooted in God's Word, empowered by the Holy Spirit, and ready for the return of Jesus Christ.</p>
      </div>
    </div>
  </section>

  <!-- PASTOR -->
  <section class="pastor-section">
    <div class="section-label">Our Leadership</div>
    <h2 class="section-title" style="color:var(--purple-dark)">Meet Our Pastor</h2>
    <div class="pastor-card">
      <div class="pastor-avatar">✝</div>
      <div class="pastor-name">Apostle & Rev'd Mrs. Phil Ihegazie</div>
      <div class="pastor-title">Senior Pastors — Coming King Mission Worldwide</div>
      <p>As we await the return of the Coming King, we remain steadfast in our commitment to spreading the message of salvation, encouraging holy living, and building a generation that is prepared to meet the Lord. Through our teachings, outreaches, conferences, and various ministry programs, we seek to transform lives by the power of God's Word and the work of the Holy Spirit.</p>
    </div>
  </section>

  <!-- SOCIAL -->
  <section class="social-section">
    <div class="section-label">Follow Us</div>
    <h2 class="section-title" style="color:var(--purple-dark)">Stay Connected</h2>
    <p>Follow us on social media for messages, updates, and inspiration.</p>
    <div class="social-links">
      <a class="social-link tiktok" href="https://tiktok.com/@allracewithrevphilmedia" target="_blank">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="white"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.27 6.27 0 00-.79-.05 6.34 6.34 0 00-6.34 6.34 6.34 6.34 0 006.34 6.34 6.34 6.34 0 006.33-6.34V8.69a8.18 8.18 0 004.77 1.52V6.78a4.85 4.85 0 01-1-.09z"/></svg>
        TikTok — @allracewithrevphilmedia
      </a>
      <a class="social-link twitter" href="https://x.com/allracewithphil" target="_blank">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="white"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        X (Twitter) — @allracewithphil
      </a>
    </div>
  </section>

  <!-- CONTACT -->
  <section class="contact-section" id="contact">
    <div class="section-label" style="text-align:center">Get in Touch</div>
    <h2 class="section-title" style="text-align:center">Contact Us</h2>
    <div class="contact-grid">
      <div class="contact-card">
        <div class="contact-icon">📍</div>
        <h4>Location</h4>
        <p>Cooperative Market, Agbalike Street by Ugbo-Paul Junction, Abapka Nike, Enugu State, Nigeria</p>
      </div>
      <div class="contact-card">
        <div class="contact-icon">📞</div>
        <h4>Phone</h4>
        <a href="tel:+2349013546550">09013546550</a>
        <a href="tel:+2347034529060">07034529060</a>
        <a class="wa-contact" href="https://wa.me/2349013546550" target="_blank">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
          WhatsApp Us
        </a>
      </div>
      <div class="contact-card">
        <div class="contact-icon">⛪</div>
        <h4>Service Days</h4>
        <p><strong style="color:var(--gold-light)">Sunday</strong> — Every Sunday</p>
        <p><strong style="color:var(--gold-light)">Monday</strong> — Every Monday</p>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="foot-logo">Coming King Mission Worldwide</div>
    <p>Preparing a generation for the return of Jesus Christ.<br>
    📍 Cooperative Market, Agbalike Street, Abapka Nike, Enugu State, Nigeria<br>
    <a href="tel:+2349013546550">09013546550</a> &nbsp;|&nbsp;
    <a href="tel:+2347034529060">07034529060</a></p>
    <p style="margin-top:1rem;opacity:0.5;font-size:0.75rem;">© 2026 Coming King Mission Worldwide. All rights reserved.</p>
  </footer>

</div><!-- END HOME PAGE -->

<!-- EVENTS PAGE -->
<div class="page" id="page-events">
  <section class="events-page">
    <button class="back-btn" onclick="showPage('home')">&#8592; Back to Home</button>
    <div class="section-label">What's Coming</div>
    <h2 class="section-title">Upcoming Events & Programs</h2>
    <p class="events-page-intro">Stay connected with all our upcoming services, conferences, outreaches, and special programs.</p>

    <!-- ADD EVENTS HERE — duplicate an event-card block for each new event -->
    <div class="no-events">
      <div>📅</div>
      <p>No upcoming events at this time.<br>Check back soon for conferences, outreaches, and special programs!</p>
      <a class="btn-gold" href="https://wa.me/2349013546550?text=Hello%2C%20I%20would%20like%20to%20know%20about%20upcoming%20events%20at%20Coming%20King%20Mission%20Worldwide." target="_blank" style="display:inline-block;margin-top:1rem;">WhatsApp Us for Info</a>
    </div>

    <!-- SAMPLE EVENT CARD — remove comment tags to activate when you have events
    <div class="events-grid">
      <div class="event-card">
        <div class="event-date">Sunday, August 3, 2026</div>
        <h3>Special Sunday Service</h3>
        <p>Join us for a powerful time of worship, the Word, and fellowship. All are welcome!</p>
      </div>
    </div>
    -->
  </section>
  <footer>
    <div class="foot-logo">Coming King Mission Worldwide</div>
    <p>© 2026 Coming King Mission Worldwide. All rights reserved.</p>
  </footer>
</div><!-- END EVENTS PAGE -->

<script>
  // PAGE NAVIGATION
  function showPage(page) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById('page-' + page).classList.add('active');
    window.scrollTo(0, 0);
  }

  // SLIDESHOW
  let currentSlide = 0;
  const slides = document.querySelectorAll('.slide');
  const dotsContainer = document.getElementById('dots');

  // Create dots
  slides.forEach((_, i) => {
    const dot = document.createElement('div');
    dot.className = 'dot' + (i === 0 ? ' active' : '');
    dot.onclick = () => goToSlide(i);
    dotsContainer.appendChild(dot);
  });

  function goToSlide(n) {
    slides[currentSlide].classList.remove('active');
    document.querySelectorAll('.dot')[currentSlide].classList.remove('active');
    currentSlide = (n + slides.length) % slides.length;
    slides[currentSlide].classList.add('active');
    document.querySelectorAll('.dot')[currentSlide].classList.add('active');
  }

  function changeSlide(dir) { goToSlide(currentSlide + dir); }

  // Auto-advance slideshow every 5 seconds
  setInterval(() => changeSlide(1), 5000);
</script>
</body>
</html>
