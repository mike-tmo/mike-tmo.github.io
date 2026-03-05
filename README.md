<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tour Me Out</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --amber:    #E8831A;
      --gold:     #D4A847;
      --gold-lt:  #F0C96A;
      --bloom:    #C8502A;
      --petal:    #E8C4A0;
      --cream:    #FBF5EC;
      --warm-off: #F5EDE0;
      --bark:     #3A1F0D;
      --mahogany: #6B2D0E;
      --copper:   #B5602A;
      --text:     #2A1505;
      --muted:    #7A5535;
      --white:    #FFFDF8;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--cream);
      color: var(--text);
      overflow-x: hidden;
    }

    /* ── BLOOM PETALS DECORATION ── */
    .bloom-deco {
      position: absolute; pointer-events: none; z-index: 0;
      font-size: 5rem; opacity: 0.07; user-select: none;
    }

    /* ── NAV ── */
    nav {
      position: sticky; top: 0; z-index: 200;
      background: rgba(251,245,236,0.94);
      backdrop-filter: blur(14px);
      border-bottom: 1px solid rgba(212,168,71,0.25);
      padding: 0 5%;
      display: flex; align-items: center; justify-content: space-between;
      height: 72px;
    }
    .nav-logo img { height: 44px; width: auto; object-fit: contain; }
    .nav-links { display: flex; gap: 2.2rem; list-style: none; }
    .nav-links a {
      text-decoration: none; color: var(--muted);
      font-family: 'DM Sans', sans-serif; font-size: 0.85rem;
      letter-spacing: 0.06em; text-transform: uppercase;
      transition: color 0.25s;
    }
    .nav-links a:hover { color: var(--amber); }
    .nav-cta {
      background: linear-gradient(135deg, var(--amber), var(--bloom));
      color: var(--white); border: none;
      padding: 0.6rem 1.6rem; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-size: 0.85rem;
      letter-spacing: 0.05em; cursor: pointer;
      transition: opacity 0.2s, transform 0.2s; box-shadow: 0 4px 16px rgba(232,131,26,0.35);
    }
    .nav-cta:hover { opacity: 0.88; transform: translateY(-1px); }

    /* ── HERO ── */
    .hero {
      min-height: 96vh;
      background:
        radial-gradient(ellipse 80% 60% at 70% 30%, rgba(212,168,71,0.18) 0%, transparent 60%),
        radial-gradient(ellipse 60% 80% at 10% 80%, rgba(200,80,42,0.14) 0%, transparent 55%),
        linear-gradient(160deg, #1A0800 0%, #3A1508 35%, #6B2D0E 65%, #B5602A 100%);
      display: flex; align-items: center; justify-content: center;
      text-align: center; padding: 80px 5% 60px;
      position: relative; overflow: hidden;
    }
    /* subtle bloom pattern overlay */
    .hero::before {
      content: '🌸🌺🌼🌸🌺🌼🌸🌺🌼🌸🌺🌼🌸🌺🌼';
      position: absolute; inset: 0;
      font-size: 2.5rem; line-height: 3.5rem;
      letter-spacing: 1.5rem;
      opacity: 0.04; z-index: 0;
      display: flex; align-items: center; justify-content: center;
      flex-wrap: wrap; overflow: hidden; padding: 2rem;
    }
    .hero-inner { position: relative; z-index: 1; }

    .hero-badge {
      display: inline-flex; align-items: center; gap: 0.7rem;
      background: rgba(255,253,248,0.1);
      border: 1px solid rgba(212,168,71,0.45);
      backdrop-filter: blur(8px);
      padding: 0.5rem 1.2rem; border-radius: 100px;
      margin-bottom: 2rem;
    }
    .hero-badge img {
      height: 36px; width: 36px; border-radius: 50%;
      object-fit: cover; border: 2px solid var(--gold);
    }
    .hero-badge span {
      font-family: 'DM Sans', sans-serif; font-size: 0.78rem;
      letter-spacing: 0.12em; text-transform: uppercase;
      color: var(--gold-lt);
    }

    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.6rem, 6vw, 5rem);
      font-weight: 600; line-height: 1.12;
      color: var(--white);
      margin-bottom: 1.4rem;
      max-width: 820px; margin-left: auto; margin-right: auto;
    }
    .hero h1 em {
      color: var(--gold-lt); font-style: italic;
    }
    .hero-sub {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.25rem; font-weight: 300;
      color: rgba(255,253,248,0.78);
      max-width: 540px; margin: 0 auto 2.8rem;
      line-height: 1.8; font-style: italic;
    }
    .hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
    .btn-gold {
      background: linear-gradient(135deg, var(--gold), var(--gold-lt));
      color: var(--bark); padding: 0.9rem 2.2rem; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-weight: 500; font-size: 0.92rem;
      letter-spacing: 0.05em; border: none; cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
      text-decoration: none; display: inline-block;
      box-shadow: 0 6px 20px rgba(212,168,71,0.4);
    }
    .btn-gold:hover { transform: translateY(-2px); box-shadow: 0 10px 28px rgba(212,168,71,0.5); }
    .btn-ghost {
      background: transparent; color: var(--white);
      padding: 0.9rem 2.2rem; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-size: 0.92rem; letter-spacing: 0.05em;
      border: 1.5px solid rgba(255,253,248,0.4); cursor: pointer;
      transition: border-color 0.2s, background 0.2s;
      text-decoration: none; display: inline-block;
    }
    .btn-ghost:hover { border-color: var(--gold-lt); background: rgba(255,253,248,0.07); }

    /* stats row */
    .hero-stats {
      display: flex; gap: 0; justify-content: center;
      margin-top: 4.5rem; flex-wrap: wrap;
    }
    .stat {
      text-align: center; padding: 0 2.4rem;
      border-right: 1px solid rgba(212,168,71,0.3);
    }
    .stat:last-child { border-right: none; }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.2rem; font-weight: 700;
      color: var(--gold-lt); line-height: 1;
    }
    .stat-label {
      font-family: 'DM Sans', sans-serif; font-size: 0.72rem;
      color: rgba(255,253,248,0.55); letter-spacing: 0.12em;
      text-transform: uppercase; margin-top: 0.3rem;
    }

    /* ── DIVIDER ── */
    .bloom-divider {
      text-align: center; padding: 1.2rem 0;
      font-size: 1.4rem; letter-spacing: 0.8rem; opacity: 0.5;
      color: var(--gold); background: var(--cream);
    }

    /* ── TOURS ── */
    .tours { background: var(--white); padding: 90px 5%; }
    .tours-header { text-align: center; margin-bottom: 3.5rem; }
    .eyebrow {
      font-family: 'DM Sans', sans-serif; font-size: 0.72rem;
      letter-spacing: 0.22em; text-transform: uppercase;
      color: var(--amber); margin-bottom: 0.7rem;
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 600; color: var(--bark); line-height: 1.2;
      margin-bottom: 1rem;
    }
    .section-title em { font-style: italic; color: var(--copper); }
    .section-sub {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.15rem; font-style: italic;
      color: var(--muted); max-width: 500px;
      line-height: 1.8;
    }
    .tours-header .section-sub { margin: 0 auto; }

    .tours-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(300px,1fr));
      gap: 2rem; max-width: 1140px; margin: 0 auto;
    }
    .tour-card {
      background: var(--cream); border-radius: 20px; overflow: hidden;
      border: 1px solid rgba(212,168,71,0.2);
      transition: transform 0.3s, box-shadow 0.3s;
      position: relative;
    }
    .tour-card::after {
      content: ''; position: absolute; inset: 0;
      border-radius: 20px;
      box-shadow: inset 0 0 0 1px rgba(212,168,71,0);
      transition: box-shadow 0.3s;
    }
    .tour-card:hover { transform: translateY(-7px); box-shadow: 0 20px 50px rgba(58,31,13,0.14); }
    .tour-card:hover::after { box-shadow: inset 0 0 0 1.5px rgba(212,168,71,0.5); }

    .tour-img {
      height: 210px; display: flex; align-items: center; justify-content: center;
      font-size: 4rem; position: relative; overflow: hidden;
    }
    .tour-img::after {
      content: ''; position: absolute; bottom: 0; left: 0; right: 0;
      height: 60px;
      background: linear-gradient(to top, var(--cream), transparent);
    }
    .tour-tag {
      position: absolute; top: 14px; left: 14px;
      background: linear-gradient(135deg, var(--amber), var(--gold));
      color: var(--white); font-family: 'DM Sans', sans-serif;
      font-size: 0.68rem; font-weight: 500;
      padding: 0.25rem 0.85rem; border-radius: 100px;
      letter-spacing: 0.1em; text-transform: uppercase;
      box-shadow: 0 2px 10px rgba(232,131,26,0.45);
    }
    .tour-body { padding: 1.6rem 1.8rem 1.8rem; }
    .tour-body h3 {
      font-family: 'Playfair Display', serif;
      font-size: 1.2rem; color: var(--bark);
      margin-bottom: 0.55rem; line-height: 1.3;
    }
    .tour-meta {
      display: flex; gap: 0.7rem; flex-wrap: wrap;
      font-family: 'DM Sans', sans-serif; font-size: 0.78rem;
      color: var(--muted); margin-bottom: 0.9rem;
    }
    .tour-meta span {
      background: rgba(212,168,71,0.12);
      padding: 0.2rem 0.65rem; border-radius: 100px;
      border: 1px solid rgba(212,168,71,0.25);
    }
    .tour-body p {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.02rem; color: var(--muted);
      line-height: 1.75; margin-bottom: 1.4rem;
    }
    .tour-footer { display: flex; align-items: center; justify-content: space-between; }
    .tour-price {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem; font-weight: 700; color: var(--amber);
    }
    .tour-price small {
      font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem; color: var(--muted); font-weight: 400;
    }
    .btn-book {
      background: var(--bark); color: var(--gold-lt);
      border: none; padding: 0.55rem 1.4rem; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-size: 0.82rem;
      letter-spacing: 0.05em; cursor: pointer;
      transition: background 0.2s, transform 0.15s;
    }
    .btn-book:hover { background: var(--bloom); transform: translateY(-1px); }

    /* tour image gradients */
    .tg1 { background: linear-gradient(145deg, #7C3100, #C2571A, #E89030); }
    .tg2 { background: linear-gradient(145deg, #2C5C1A, #5A9E3A, #9ECF60); }
    .tg3 { background: linear-gradient(145deg, #8B1A1A, #C84A1A, #E8A030); }

    /* ── GALLERY ── */
    .gallery {
      background: var(--warm-off); padding: 90px 5%;
      position: relative; overflow: hidden;
    }
    .gallery-header { text-align: center; margin-bottom: 3rem; }
    .gallery-header .section-sub { margin: 0 auto; }
    .gallery-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      grid-template-rows: 230px 230px;
      gap: 10px; max-width: 1140px; margin: 0 auto;
      border-radius: 20px; overflow: hidden;
    }
    .g-item {
      position: relative; display: flex;
      align-items: center; justify-content: center;
      font-size: 3.5rem; overflow: hidden; cursor: pointer;
    }
    .g-item:first-child { grid-row: span 2; font-size: 5rem; }
    .g-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(to top, rgba(58,31,13,0.65) 0%, transparent 55%);
      opacity: 0; transition: opacity 0.35s;
      display: flex; align-items: flex-end; padding: 1.2rem;
    }
    .g-item:hover .g-overlay { opacity: 1; }
    .g-overlay span {
      font-family: 'Cormorant Garamond', serif;
      font-style: italic; color: var(--white);
      font-size: 1rem;
    }
    .ga { background: linear-gradient(145deg, #7C3100, #C2571A); }
    .gb { background: linear-gradient(145deg, #2C5530, #4A8A50); }
    .gc { background: linear-gradient(145deg, #5C3A10, #C8881A); }
    .gd { background: linear-gradient(145deg, #3A1A5C, #8A4A9C); }
    .ge { background: linear-gradient(145deg, #1A3C5C, #3A7A9C); }

    /* ── WHY US ── */
    .why {
      background: linear-gradient(160deg, var(--bark) 0%, #5A2010 60%, #8B3A14 100%);
      padding: 90px 5%; position: relative; overflow: hidden;
    }
    .why::before {
      content: '🌸'; position: absolute;
      font-size: 18rem; opacity: 0.04;
      top: -4rem; right: -4rem; z-index: 0;
    }
    .why-inner {
      max-width: 1140px; margin: 0 auto;
      display: grid; grid-template-columns: 1.1fr 1fr; gap: 5rem;
      align-items: center; position: relative; z-index: 1;
    }
    .why .eyebrow { color: var(--gold-lt); }
    .why .section-title { color: var(--white); }
    .why .section-sub { color: rgba(255,253,248,0.65); font-size: 1.1rem; margin-top: 0.5rem; }
    .features { display: flex; flex-direction: column; gap: 1.5rem; margin-top: 2.2rem; }
    .feat {
      display: flex; gap: 1.1rem; align-items: flex-start;
      background: rgba(255,253,248,0.05); border: 1px solid rgba(212,168,71,0.18);
      padding: 1.1rem 1.3rem; border-radius: 14px;
      transition: background 0.25s;
    }
    .feat:hover { background: rgba(212,168,71,0.1); }
    .feat-icon {
      font-size: 1.5rem; width: 44px; height: 44px; min-width: 44px;
      background: rgba(212,168,71,0.15); border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
    }
    .feat-text h4 {
      font-family: 'Playfair Display', serif;
      color: var(--gold-lt); font-size: 0.98rem; margin-bottom: 0.2rem;
    }
    .feat-text p {
      font-family: 'DM Sans', sans-serif; font-size: 0.83rem;
      color: rgba(255,253,248,0.6); line-height: 1.55;
    }
    .award-card {
      background: rgba(255,253,248,0.06); border: 1px solid rgba(212,168,71,0.3);
      border-radius: 22px; padding: 3rem 2.5rem; text-align: center;
      backdrop-filter: blur(4px);
    }
    .award-card .big-emoji { font-size: 4rem; margin-bottom: 1.2rem; display: block; }
    .award-card h3 {
      font-family: 'Playfair Display', serif; font-style: italic;
      color: var(--gold-lt); font-size: 1.5rem; line-height: 1.3; margin-bottom: 0.9rem;
    }
    .award-card p {
      font-family: 'Cormorant Garamond', serif; font-style: italic;
      color: rgba(255,253,248,0.7); font-size: 1.05rem; line-height: 1.75;
    }
    .stars { color: var(--gold-lt); font-size: 1.3rem; margin-top: 1.5rem; letter-spacing: 0.2rem; }

    /* ── TESTIMONIALS ── */
    .testimonials { background: var(--white); padding: 90px 5%; }
    .testimonials-header { text-align: center; margin-bottom: 3.5rem; }
    .testimonials-header .section-sub { margin: 0 auto; }
    .testi-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(280px,1fr));
      gap: 1.6rem; max-width: 1140px; margin: 0 auto;
    }
    .testi-card {
      background: var(--cream); border-radius: 18px;
      padding: 2rem; border: 1px solid rgba(212,168,71,0.2);
      position: relative; overflow: hidden;
    }
    .testi-card::before {
      content: '"'; font-family: 'Playfair Display', serif;
      position: absolute; top: -0.5rem; right: 1.5rem;
      font-size: 8rem; color: rgba(212,168,71,0.1); line-height: 1;
    }
    .testi-stars { color: var(--gold); font-size: 0.9rem; margin-bottom: 0.9rem; letter-spacing: 0.1rem; }
    .testi-text {
      font-family: 'Cormorant Garamond', serif; font-style: italic;
      font-size: 1.05rem; color: var(--muted); line-height: 1.8;
      margin-bottom: 1.4rem; position: relative; z-index: 1;
    }
    .testi-author { display: flex; align-items: center; gap: 0.9rem; }
    .testi-avatar {
      width: 44px; height: 44px; border-radius: 50%;
      background: linear-gradient(135deg, var(--amber), var(--gold-lt));
      display: flex; align-items: center; justify-content: center; font-size: 1.2rem;
    }
    .testi-name {
      font-family: 'DM Sans', sans-serif; font-weight: 500;
      font-size: 0.9rem; color: var(--bark);
    }
    .testi-tour {
      font-family: 'DM Sans', sans-serif; font-size: 0.75rem; color: var(--copper);
    }

    /* ── CONTACT ── */
    .contact { background: var(--warm-off); padding: 90px 5%; }
    .contact-inner { max-width: 1140px; margin: 0 auto; display: grid; grid-template-columns: 1fr 1.3fr; gap: 5rem; align-items: start; }
    .contact-info .section-sub { margin-top: 0.5rem; }
    .c-detail { display: flex; align-items: flex-start; gap: 1rem; margin-top: 1.6rem; }
    .c-icon {
      width: 46px; height: 46px; min-width: 46px;
      background: linear-gradient(135deg, var(--amber), var(--bloom));
      border-radius: 12px; display: flex; align-items: center;
      justify-content: center; font-size: 1.1rem;
      box-shadow: 0 4px 14px rgba(232,131,26,0.3);
    }
    .c-text strong {
      font-family: 'DM Sans', sans-serif; font-size: 0.92rem; color: var(--bark);
      display: block; margin-bottom: 0.1rem;
    }
    .c-text span { font-family: 'DM Sans', sans-serif; font-size: 0.82rem; color: var(--muted); }
    .c-form {
      background: var(--white); border-radius: 22px;
      padding: 2.6rem; border: 1px solid rgba(212,168,71,0.2);
      box-shadow: 0 8px 40px rgba(58,31,13,0.07);
    }
    .c-form h3 {
      font-family: 'Playfair Display', serif; font-size: 1.4rem;
      color: var(--bark); margin-bottom: 1.6rem;
    }
    .f-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
    .f-group { margin-bottom: 1.1rem; }
    .f-group label {
      display: block; font-family: 'DM Sans', sans-serif;
      font-size: 0.75rem; letter-spacing: 0.08em; text-transform: uppercase;
      color: var(--muted); margin-bottom: 0.45rem; font-weight: 500;
    }
    .f-group input, .f-group select, .f-group textarea {
      width: 100%; padding: 0.75rem 1.1rem;
      border: 1.5px solid rgba(58,31,13,0.14); border-radius: 12px;
      font-family: 'DM Sans', sans-serif; font-size: 0.9rem;
      background: var(--cream); color: var(--text); outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
    }
    .f-group input:focus, .f-group select:focus, .f-group textarea:focus {
      border-color: var(--amber); box-shadow: 0 0 0 3px rgba(232,131,26,0.1);
    }
    .f-group textarea { resize: vertical; min-height: 105px; }
    .btn-send {
      width: 100%;
      background: linear-gradient(135deg, var(--amber) 0%, var(--bloom) 100%);
      color: var(--white); border: none; padding: 1rem; border-radius: 100px;
      font-family: 'DM Sans', sans-serif; font-size: 0.95rem; font-weight: 500;
      letter-spacing: 0.05em; cursor: pointer;
      transition: opacity 0.2s, transform 0.15s;
      box-shadow: 0 6px 20px rgba(232,131,26,0.4);
    }
    .btn-send:hover { opacity: 0.88; transform: translateY(-1px); }
    .f-note {
      font-family: 'DM Sans', sans-serif; font-size: 0.74rem;
      color: var(--muted); text-align: center; margin-top: 0.8rem;
    }

    /* ── FOOTER ── */
    footer {
      background: var(--bark); padding: 3.5rem 5%;
      text-align: center; font-family: 'DM Sans', sans-serif;
    }
    .footer-logo img { height: 40px; opacity: 0.9; margin-bottom: 0.8rem; }
    footer p {
      font-family: 'Cormorant Garamond', serif; font-style: italic;
      color: rgba(255,253,248,0.5); font-size: 1rem; margin-bottom: 1.4rem;
    }
    .footer-links { display: flex; gap: 2rem; justify-content: center; flex-wrap: wrap; margin-bottom: 1.5rem; }
    .footer-links a {
      color: rgba(255,253,248,0.5); text-decoration: none;
      font-size: 0.8rem; letter-spacing: 0.1em; text-transform: uppercase;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--gold-lt); }
    .footer-copy { font-size: 0.75rem; color: rgba(255,253,248,0.25); }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 2rem; right: 2rem;
      background: linear-gradient(135deg, var(--amber), var(--bloom));
      color: white; padding: 1.1rem 1.8rem; border-radius: 14px;
      font-family: 'DM Sans', sans-serif; font-size: 0.9rem;
      box-shadow: 0 10px 30px rgba(58,31,13,0.3);
      transform: translateY(120px); opacity: 0; transition: all 0.4s; z-index: 999;
    }
    .toast.show { transform: translateY(0); opacity: 1; }

    /* ── RESPONSIVE ── */
    @media (max-width: 800px) {
      .why-inner, .contact-inner { grid-template-columns: 1fr; gap: 2.5rem; }
      .gallery-grid { grid-template-columns: 1fr 1fr; grid-template-rows: auto; }
      .g-item:first-child { grid-row: span 1; }
      .f-row { grid-template-columns: 1fr; }
      .nav-links { display: none; }
      .stat { padding: 0 1.2rem; }
    }

    /* entry animations */
    @keyframes fadeUp { from { opacity:0; transform:translateY(30px); } to { opacity:1; transform:translateY(0); } }
    .hero-inner > * { animation: fadeUp 0.8s ease both; }
    .hero-inner > *:nth-child(1) { animation-delay: 0.1s; }
    .hero-inner > *:nth-child(2) { animation-delay: 0.25s; }
    .hero-inner > *:nth-child(3) { animation-delay: 0.4s; }
    .hero-inner > *:nth-child(4) { animation-delay: 0.55s; }
    .hero-inner > *:nth-child(5) { animation-delay: 0.7s; }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">
    <img src="https://tourmeout.com/wp-content/uploads/2024/07/tmo-logo-cotton.svg" alt="Tour Me Out" onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
    <span style="display:none; font-family:'Playfair Display',serif; font-size:1.3rem; color:var(--bark); font-weight:600;">Tour Me Out</span>
  </div>
  <ul class="nav-links">
    <li><a href="#tours">Tours</a></li>
    <li><a href="#gallery">Gallery</a></li>
    <li><a href="#why">About</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book a Tour</button>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-inner">
    <div class="hero-badge">
      <img src="https://ranxosesroques.com/wp-content/uploads/sites/8233/2025/12/travellers-choice-2025.jpg?w=1000&h=1000" alt="Travellers Choice 2025" onerror="this.style.display='none'">
      <span>Travellers' Choice 2025 &nbsp;·&nbsp; Award-Winning Guides</span>
    </div>
    <h1>Discover Valencia<br>with <em>People Who Love It</em></h1>
    <p class="hero-sub">Small-group guided tours led by passionate locals. We don't just show you the sights — we share the stories that make them unforgettable.</p>
    <div class="hero-btns">
      <a href="#tours" class="btn-gold">Explore Our Tours</a>
      <a href="#contact" class="btn-ghost">Plan My Trip</a>
    </div>
    <div class="hero-stats">
      <div class="stat"><div class="stat-num">1,552+</div><div class="stat-label">Happy Travelers</div></div>
      <div class="stat"><div class="stat-num">2</div><div class="stat-label">Destinations</div></div>
      <div class="stat"><div class="stat-num">4.9★</div><div class="stat-label">Avg. Rating</div></div>
      <div class="stat"><div class="stat-num">14</div><div class="stat-label">Years Running</div></div>
    </div>
  </div>
</section>

<div class="bloom-divider">✿ ❁ ✿ ❁ ✿</div>

<!-- TOURS -->
<section class="tours" id="tours">
  <div class="tours-header">
    <div class="eyebrow">Our Experiences</div>
    <h2 class="section-title">Tours Crafted for <em>Every Explorer</em></h2>
    <p class="section-sub">Intimate small-group tours woven with local knowledge, great food, and genuine warmth.</p>
  </div>
  <div class="tours-grid">
    <div class="tour-card">
      <div class="tour-img tg1"><span>🏛️</span><div class="tour-tag">Bestseller</div></div>
      <div class="tour-body">
        <h3>Old Town Secrets Walk</h3>
        <div class="tour-meta"><span>⏱ 2.5 hrs</span><span>👥 Max 10</span><span>🚶 Walking</span></div>
        <p>Wander cobblestone alleys, hidden courtyards, and centuries-old architecture with a storytelling guide who knows every legend.</p>
        <div class="tour-footer">
          <div class="tour-price">$110 <small>/ person</small></div>
          <button class="btn-book" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button>
        </div>
      </div>
    </div>
    <div class="tour-card">
      <div class="tour-img tg2"><span>🌾</span><div class="tour-tag">Nature</div></div>
      <div class="tour-body">
        <h3>Albufera Natural Park — A Rice Paradise</h3>
        <div class="tour-meta"><span>⏱ Half Day 5h</span><span>👥 Max 15</span><span>🚲 Biking</span><span>🚣 Boat Trip</span></div>
        <p>Discover the origins of Paella at La Albufera. Spain's largest freshwater lagoon has been the center of rice production for centuries. Explore this scenic wonder and migratory bird paradise on our bike and boat tour!</p>
        <div class="tour-footer">
          <div class="tour-price">$60 <small>/ person</small></div>
          <button class="btn-book" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button>
        </div>
      </div>
    </div>
    <div class="tour-card">
      <div class="tour-img tg3"><span>🥘</span><div class="tour-tag">Food & Wine</div></div>
      <div class="tour-body">
        <h3>The Flavors of Valencia: Tapas & Paella Tour</h3>
        <div class="tour-meta"><span>⏱ 3 hrs</span><span>👥 Max 12</span><span>🍽️ Culinary</span></div>
        <p>Eat your way through Valencia's charming old town with a local guide leading you through centuries of culinary history. Everyone's heard of Paella — but there's so much more to Valencian dining. Try the too-often overlooked classics of Valencian gastronomy!</p>
        <div class="tour-footer">
          <div class="tour-price">$60 <small>/ person</small></div>
          <button class="btn-book" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GALLERY -->
<section class="gallery" id="gallery">
  <div class="gallery-header">
    <div class="eyebrow">Photo Gallery</div>
    <h2 class="section-title">A Glimpse of <em>Valencia</em></h2>
    <p class="section-sub">Moments of colour, culture and warmth from our tours.</p>
  </div>
  <div class="gallery-grid">
    <div class="g-item ga"><span>🏛️</span><div class="g-overlay"><span>Old Town Valencia</span></div></div>
    <div class="g-item gb"><span>🌾</span><div class="g-overlay"><span>Albufera Lagoon</span></div></div>
    <div class="g-item gc"><span>🥘</span><div class="g-overlay"><span>Paella Heritage</span></div></div>
    <div class="g-item gd"><span>🌸</span><div class="g-overlay"><span>Fallas Blooms</span></div></div>
    <div class="g-item ge"><span>🚲</span><div class="g-overlay"><span>Bike & Boat</span></div></div>
  </div>
</section>

<!-- WHY US -->
<section class="why" id="why">
  <div class="why-inner">
    <div>
      <div class="eyebrow">Why Tour Me Out</div>
      <h2 class="section-title">Led With Heart,<br><em>Not Just a Script</em></h2>
      <p class="section-sub">We're a small team of passionate Valencians who love sharing our city's soul with curious travellers.</p>
      <div class="features">
        <div class="feat"><div class="feat-icon">🗺️</div><div class="feat-text"><h4>Expert Local Guides</h4><p>Born-and-raised Valencians, trained in history, culture and storytelling.</p></div></div>
        <div class="feat"><div class="feat-icon">👨‍👩‍👧</div><div class="feat-text"><h4>Small Groups Only</h4><p>We cap every tour so you get a personal, unhurried experience every time.</p></div></div>
        <div class="feat"><div class="feat-icon">🌱</div><div class="feat-text"><h4>Sustainable Travel</h4><p>We partner with local businesses and care deeply about Valencia's future.</p></div></div>
        <div class="feat"><div class="feat-icon">♿</div><div class="feat-text"><h4>Inclusive & Accessible</h4><p>Adapted routes and full support for any accessibility needs.</p></div></div>
      </div>
    </div>
    <div class="award-card">
      <span class="big-emoji">🏆</span>
      <h3>Travellers' Choice<br>Award Winner 2025</h3>
      <p>Recognised by TripAdvisor, Lonely Planet and the Regional Tourism Board as one of Valencia's most beloved tour operators.</p>
      <div class="stars">★ ★ ★ ★ ★</div>
      <p style="font-size:0.82rem; margin-top:0.5rem; font-style:normal; font-family:'DM Sans',sans-serif;">4.9 / 5 from 1,200+ reviews</p>
    </div>
  </div>
</section>

<div class="bloom-divider" style="background:var(--white);">✿ ❁ ✿ ❁ ✿</div>

<!-- TESTIMONIALS -->
<section class="testimonials" id="testimonials">
  <div class="testimonials-header">
    <div class="eyebrow">Happy Travellers</div>
    <h2 class="section-title">Don't Just Take <em>Our Word</em> For It</h2>
    <p class="section-sub">Real words from real explorers who fell in love with Valencia.</p>
  </div>
  <div class="testi-grid">
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The Old Town walk was the highlight of our entire trip. Our guide knew every hidden café, every legend, every nook. I've traveled a lot — this was genuinely special."</p>
      <div class="testi-author"><div class="testi-avatar">👩</div><div><div class="testi-name">Sarah M.</div><div class="testi-tour">Old Town Secrets Walk</div></div></div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The Albufera tour was breathtaking. Cycling through rice fields then gliding across the lagoon at golden hour — I'll never forget it. The guide's passion made it magical."</p>
      <div class="testi-author"><div class="testi-avatar">👨</div><div><div class="testi-name">James & Lena R.</div><div class="testi-tour">Albufera Natural Park</div></div></div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The tapas tour opened my eyes to real Valencian food. So much more than paella! Our guide took us to spots only locals know. Warm, delicious, and unforgettable."</p>
      <div class="testi-author"><div class="testi-avatar">👩</div><div><div class="testi-name">Priya K.</div><div class="testi-tour">Flavors of Valencia Tour</div></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="contact-inner">
    <div class="contact-info">
      <div class="eyebrow">Get In Touch</div>
      <h2 class="section-title">Let's Plan Your<br><em>Perfect Tour</em></h2>
      <p class="section-sub">Questions or want something bespoke? We reply within 24 hours and love hearing from curious travellers.</p>
      <div class="c-detail"><div class="c-icon">📍</div><div class="c-text"><strong>Valencia, Spain</strong><span>Meeting points shared on booking</span></div></div>
      <div class="c-detail"><div class="c-icon">✉️</div><div class="c-text"><strong>hello@tourmeout.com</strong><span>We reply within 24 hours</span></div></div>
      <div class="c-detail"><div class="c-icon">🌐</div><div class="c-text"><strong>tourmeout.com</strong><span>Book directly on our website</span></div></div>
    </div>
    <div class="c-form">
      <h3>Send a Message 🌸</h3>
      <div class="f-row">
        <div class="f-group"><label>First Name</label><input type="text" id="fname" placeholder="Maria"></div>
        <div class="f-group"><label>Last Name</label><input type="text" id="lname" placeholder="Garcia"></div>
      </div>
      <div class="f-group"><label>Email Address</label><input type="email" id="email" placeholder="maria@example.com"></div>
      <div class="f-group">
        <label>Interested In</label>
        <select id="tour-sel">
          <option value="">Choose a tour…</option>
          <option>Old Town Secrets Walk — $110</option>
          <option>Albufera Natural Park — $60</option>
          <option>Flavors of Valencia — $60</option>
          <option>Custom / Private Tour</option>
          <option>Not sure yet</option>
        </select>
      </div>
      <div class="f-group"><label>Message</label><textarea id="msg" placeholder="Tell us your travel dates, group size, or any questions…"></textarea></div>
      <button class="btn-send" onclick="sendMsg()">Send Message ✈️</button>
      <p class="f-note">🔒 Your info stays private. No spam, ever.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">
    <img src="https://tourmeout.com/wp-content/uploads/2024/07/tmo-logo-cotton.svg" alt="Tour Me Out" onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
    <span style="display:none; font-family:'Playfair Display',serif; font-size:1.4rem; color:var(--gold-lt);">Tour Me Out</span>
  </div>
  <p>Sharing Valencia's stories, one small group at a time.</p>
  <div class="footer-links">
    <a href="#tours">Tours</a><a href="#gallery">Gallery</a><a href="#why">About</a><a href="#testimonials">Reviews</a><a href="#contact">Contact</a>
  </div>
  <p class="footer-copy">© 2026 Tour Me Out. All rights reserved. · Valencia, Spain</p>
</footer>

<div class="toast" id="toast">🎉 Message sent! We'll be in touch within 24 hours.</div>

<script>
  function sendMsg() {
    const fname = document.getElementById('fname').value.trim();
    const email = document.getElementById('email').value.trim();
    if (!fname || !email) { alert('Please enter your name and email.'); return; }
    const t = document.getElementById('toast');
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 4000);
    ['fname','lname','email','msg'].forEach(id => document.getElementById(id).value = '');
    document.getElementById('tour-sel').value = '';
  }
</script>
</body>
</html>
