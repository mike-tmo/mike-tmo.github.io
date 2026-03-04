<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Wanderlust Guided Tours</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    :root {
      --cream: #FDF6EC; --warm-brown: #7C4A2D; --terracotta: #C2674B;
      --golden: #E8A838; --sage: #7A9E7E; --text-dark: #2E1A0E;
      --text-mid: #5C3D2B; --text-light: #9C7A68; --white: #FFFFFF;
    }
    html { scroll-behavior: smooth; }
    body { font-family: 'Georgia', serif; background: var(--cream); color: var(--text-dark); }
    nav { position: fixed; top: 0; width: 100%; z-index: 100; background: rgba(253,246,236,0.95); backdrop-filter: blur(8px); border-bottom: 1px solid rgba(124,74,45,0.12); padding: 0 5%; display: flex; align-items: center; justify-content: space-between; height: 68px; }
    .nav-logo { font-size: 1.4rem; font-weight: bold; color: var(--warm-brown); }
    .nav-logo span { color: var(--terracotta); }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a { text-decoration: none; color: var(--text-mid); font-family: 'Arial', sans-serif; font-size: 0.9rem; transition: color 0.2s; }
    .nav-links a:hover { color: var(--terracotta); }
    .nav-cta { background: var(--terracotta); color: var(--white); border: none; padding: 0.55rem 1.4rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-size: 0.9rem; cursor: pointer; }
    .hero { min-height: 100vh; background: linear-gradient(135deg, #3D1C08 0%, #7C4A2D 40%, #C2674B 100%); display: flex; align-items: center; justify-content: center; text-align: center; padding: 100px 5% 60px; }
    .hero-badge { display: inline-block; background: rgba(232,168,56,0.2); border: 1px solid rgba(232,168,56,0.5); color: var(--golden); padding: 0.35rem 1rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-size: 0.8rem; letter-spacing: 1.5px; text-transform: uppercase; margin-bottom: 1.5rem; }
    .hero h1 { font-size: clamp(2.4rem, 6vw, 4.2rem); color: var(--white); line-height: 1.2; margin-bottom: 1.2rem; max-width: 750px; margin-left: auto; margin-right: auto; }
    .hero h1 em { color: var(--golden); font-style: normal; }
    .hero p { font-family: 'Arial', sans-serif; font-size: 1.1rem; color: rgba(255,255,255,0.8); max-width: 520px; margin: 0 auto 2.5rem; line-height: 1.7; }
    .hero-btns { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
    .btn-primary { background: var(--golden); color: var(--text-dark); padding: 0.85rem 2rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-weight: bold; font-size: 1rem; border: none; cursor: pointer; text-decoration: none; display: inline-block; }
    .btn-outline { background: transparent; color: var(--white); padding: 0.85rem 2rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-size: 1rem; border: 2px solid rgba(255,255,255,0.5); cursor: pointer; text-decoration: none; display: inline-block; }
    .hero-stats { display: flex; gap: 3rem; justify-content: center; margin-top: 4rem; flex-wrap: wrap; }
    .stat-num { font-size: 2rem; font-weight: bold; color: var(--golden); }
    .stat-label { font-family: 'Arial', sans-serif; font-size: 0.8rem; color: rgba(255,255,255,0.6); letter-spacing: 1px; text-transform: uppercase; }
    section { padding: 90px 5%; }
    .section-label { font-family: 'Arial', sans-serif; font-size: 0.78rem; letter-spacing: 2.5px; text-transform: uppercase; color: var(--terracotta); margin-bottom: 0.6rem; }
    .section-title { font-size: clamp(1.8rem, 4vw, 2.6rem); color: var(--text-dark); line-height: 1.3; margin-bottom: 1rem; }
    .section-sub { font-family: 'Arial', sans-serif; font-size: 1rem; color: var(--text-light); max-width: 520px; line-height: 1.7; }
    .tours { background: var(--white); }
    .tours-header { text-align: center; margin-bottom: 3rem; }
    .tours-header .section-sub { margin: 0 auto; }
    .tours-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(290px, 1fr)); gap: 1.8rem; max-width: 1100px; margin: 0 auto; }
    .tour-card { background: var(--cream); border-radius: 16px; overflow: hidden; transition: transform 0.25s, box-shadow 0.25s; border: 1px solid rgba(124,74,45,0.1); }
    .tour-card:hover { transform: translateY(-6px); box-shadow: 0 16px 40px rgba(124,74,45,0.15); }
    .tour-img { height: 200px; display: flex; align-items: center; justify-content: center; font-size: 4rem; position: relative; }
    .tour-tag { position: absolute; top: 12px; right: 12px; background: var(--golden); color: var(--text-dark); font-family: 'Arial', sans-serif; font-size: 0.72rem; font-weight: bold; padding: 0.2rem 0.7rem; border-radius: 50px; text-transform: uppercase; }
    .tour-body { padding: 1.4rem; }
    .tour-body h3 { font-size: 1.2rem; color: var(--text-dark); margin-bottom: 0.4rem; }
    .tour-meta { display: flex; gap: 1rem; font-family: 'Arial', sans-serif; font-size: 0.82rem; color: var(--text-light); margin-bottom: 0.8rem; }
    .tour-body p { font-family: 'Arial', sans-serif; font-size: 0.92rem; color: var(--text-mid); line-height: 1.6; margin-bottom: 1.2rem; }
    .tour-footer { display: flex; align-items: center; justify-content: space-between; }
    .tour-price { font-size: 1.25rem; font-weight: bold; color: var(--terracotta); }
    .tour-price span { font-family: 'Arial', sans-serif; font-size: 0.78rem; color: var(--text-light); font-weight: normal; }
    .btn-tour { background: var(--warm-brown); color: white; border: none; padding: 0.5rem 1.2rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-size: 0.85rem; cursor: pointer; }
    .gallery { background: var(--cream); }
    .gallery-header { text-align: center; margin-bottom: 2.5rem; }
    .gallery-grid { display: grid; grid-template-columns: repeat(4, 1fr); grid-template-rows: 220px 220px; gap: 12px; max-width: 1100px; margin: 0 auto; border-radius: 16px; overflow: hidden; }
    .gallery-item { overflow: hidden; position: relative; display: flex; align-items: center; justify-content: center; font-size: 3.5rem; cursor: pointer; transition: transform 0.3s; }
    .gallery-item:hover { transform: scale(1.04); }
    .gallery-item:hover .gallery-overlay { opacity: 1; }
    .gallery-item:nth-child(1) { grid-column: span 2; grid-row: span 2; font-size: 5rem; }
    .gallery-item:nth-child(4) { grid-column: span 2; }
    .gallery-overlay { position: absolute; inset: 0; background: rgba(124,74,45,0.4); display: flex; align-items: center; justify-content: center; opacity: 0; transition: opacity 0.3s; }
    .gallery-overlay span { color: white; font-family: 'Arial', sans-serif; font-size: 0.85rem; background: rgba(0,0,0,0.4); padding: 0.4rem 1rem; border-radius: 50px; }
    .g1 { background: linear-gradient(135deg, #8B5E3C, #C2674B); }
    .g2 { background: linear-gradient(135deg, #4A7A5C, #7A9E7E); }
    .g3 { background: linear-gradient(135deg, #7C4A2D, #E8A838); }
    .g4 { background: linear-gradient(135deg, #3D5A3E, #6B8F71); }
    .g5 { background: linear-gradient(135deg, #C2674B, #E8A838); }
    .why { background: var(--warm-brown); }
    .why-inner { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; }
    .why-text .section-label { color: var(--golden); }
    .why-text .section-title { color: var(--white); }
    .why-text .section-sub { color: rgba(255,255,255,0.75); }
    .why-features { display: flex; flex-direction: column; gap: 1.4rem; margin-top: 2rem; }
    .feature-item { display: flex; gap: 1rem; align-items: flex-start; }
    .feature-icon { width: 44px; height: 44px; min-width: 44px; background: rgba(232,168,56,0.2); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.3rem; }
    .feature-text h4 { color: var(--white); font-size: 1rem; margin-bottom: 0.2rem; }
    .feature-text p { font-family: 'Arial', sans-serif; font-size: 0.88rem; color: rgba(255,255,255,0.65); line-height: 1.5; }
    .why-card { background: rgba(255,255,255,0.08); border: 1px solid rgba(255,255,255,0.15); border-radius: 20px; padding: 2.5rem; text-align: center; }
    .why-card-emoji { font-size: 4rem; margin-bottom: 1rem; }
    .why-card h3 { color: var(--golden); font-size: 1.4rem; margin-bottom: 0.8rem; }
    .why-card p { font-family: 'Arial', sans-serif; color: rgba(255,255,255,0.75); line-height: 1.7; }
    .why-card-stars { color: var(--golden); font-size: 1.3rem; margin-top: 1.5rem; }
    .testimonials { background: var(--white); }
    .testimonials-header { text-align: center; margin-bottom: 3rem; }
    .testimonials-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; max-width: 1100px; margin: 0 auto; }
    .testimonial-card { background: var(--cream); border-radius: 16px; padding: 1.8rem; border: 1px solid rgba(124,74,45,0.1); }
    .testimonial-stars { color: var(--golden); font-size: 1rem; margin-bottom: 0.8rem; }
    .testimonial-text { font-size: 0.97rem; color: var(--text-mid); line-height: 1.7; margin-bottom: 1.2rem; font-style: italic; }
    .testimonial-author { display: flex; align-items: center; gap: 0.8rem; }
    .author-avatar { width: 42px; height: 42px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; background: linear-gradient(135deg, var(--terracotta), var(--golden)); }
    .author-name { font-family: 'Arial', sans-serif; font-weight: bold; font-size: 0.9rem; color: var(--text-dark); }
    .author-trip { font-family: 'Arial', sans-serif; font-size: 0.78rem; color: var(--text-light); }
    .contact { background: var(--cream); }
    .contact-inner { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: 1fr 1.2fr; gap: 4rem; align-items: start; }
    .contact-detail { display: flex; align-items: center; gap: 0.9rem; margin-bottom: 1.2rem; margin-top: 1.5rem; }
    .contact-icon { width: 44px; height: 44px; min-width: 44px; background: var(--terracotta); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; }
    .contact-detail-text p { font-family: 'Arial', sans-serif; font-size: 0.88rem; color: var(--text-light); }
    .contact-detail-text strong { font-size: 0.95rem; color: var(--text-dark); }
    .contact-form { background: var(--white); border-radius: 20px; padding: 2.5rem; box-shadow: 0 4px 24px rgba(124,74,45,0.08); border: 1px solid rgba(124,74,45,0.1); }
    .contact-form h3 { font-size: 1.3rem; color: var(--text-dark); margin-bottom: 1.5rem; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
    .form-group { margin-bottom: 1.2rem; }
    .form-group label { display: block; font-family: 'Arial', sans-serif; font-size: 0.83rem; color: var(--text-mid); margin-bottom: 0.4rem; font-weight: bold; }
    .form-group input, .form-group select, .form-group textarea { width: 100%; padding: 0.75rem 1rem; border: 1.5px solid rgba(124,74,45,0.2); border-radius: 10px; font-family: 'Arial', sans-serif; font-size: 0.93rem; background: var(--cream); color: var(--text-dark); outline: none; }
    .form-group input:focus, .form-group select:focus, .form-group textarea:focus { border-color: var(--terracotta); }
    .form-group textarea { resize: vertical; min-height: 110px; }
    .btn-submit { width: 100%; background: var(--terracotta); color: white; border: none; padding: 0.95rem; border-radius: 50px; font-family: 'Arial', sans-serif; font-size: 1rem; font-weight: bold; cursor: pointer; }
    .form-note { font-family: 'Arial', sans-serif; font-size: 0.78rem; color: var(--text-light); text-align: center; margin-top: 0.8rem; }
    footer { background: var(--text-dark); color: rgba(255,255,255,0.7); padding: 3rem 5%; text-align: center; font-family: 'Arial', sans-serif; font-size: 0.88rem; }
    .footer-logo { font-family: 'Georgia', serif; font-size: 1.5rem; color: var(--golden); margin-bottom: 0.5rem; }
    .footer-links { display: flex; gap: 2rem; justify-content: center; margin: 1.2rem 0; flex-wrap: wrap; }
    .footer-links a { color: rgba(255,255,255,0.6); text-decoration: none; }
    .footer-links a:hover { color: var(--golden); }
    .toast { position: fixed; bottom: 2rem; right: 2rem; background: var(--sage); color: white; padding: 1rem 1.5rem; border-radius: 12px; font-family: 'Arial', sans-serif; font-size: 0.92rem; box-shadow: 0 8px 24px rgba(0,0,0,0.2); transform: translateY(100px); opacity: 0; transition: all 0.4s; z-index: 999; }
    .toast.show { transform: translateY(0); opacity: 1; }
    @media (max-width: 768px) { .why-inner, .contact-inner { grid-template-columns: 1fr; gap: 2rem; } .gallery-grid { grid-template-columns: repeat(2,1fr); grid-template-rows: auto; } .gallery-item:nth-child(1) { grid-column: span 2; } .gallery-item:nth-child(4) { grid-column: span 1; } .form-row { grid-template-columns: 1fr; } .nav-links { display: none; } }
  </style>
</head>
<body>
<nav>
  <div class="nav-logo">Wander<span>lust</span> Tours</div>
  <ul class="nav-links">
    <li><a href="#tours">Tours</a></li><li><a href="#gallery">Gallery</a></li><li><a href="#why">Why Us</a></li><li><a href="#testimonials">Reviews</a></li><li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book a Tour</button>
</nav>
<section class="hero">
  <div>
    <div class="hero-badge">✦ Est. 2008 · Award-Winning Guides</div>
    <h1>Discover the World<br>with <em>People Who Love It</em></h1>
    <p>Small-group guided tours led by passionate locals. We don't just show you the sights — we share the stories that make them unforgettable.</p>
    <div class="hero-btns">
      <a href="#tours" class="btn-primary">Explore Our Tours</a>
      <a href="#contact" class="btn-outline">Plan My Trip</a>
    </div>
    <div class="hero-stats">
      <div class="stat"><div class="stat-num">4,800+</div><div class="stat-label">Happy Travelers</div></div>
      <div class="stat"><div class="stat-num">38</div><div class="stat-label">Destinations</div></div>
      <div class="stat"><div class="stat-num">4.9★</div><div class="stat-label">Avg. Rating</div></div>
      <div class="stat"><div class="stat-num">15</div><div class="stat-label">Years Running</div></div>
    </div>
  </div>
</section>
<section class="tours" id="tours">
  <div class="tours-header">
    <div class="section-label">Our Experiences</div>
    <h2 class="section-title">Hand-Crafted Tours for Every Explorer</h2>
    <p class="section-sub">From half-day city walks to full-day adventures, each tour is designed for small groups and big memories.</p>
  </div>
  <div class="tours-grid">
    <div class="tour-card"><div class="tour-img g1"><span>🏛️</span><div class="tour-tag">Bestseller</div></div><div class="tour-body"><h3>Old Town Secrets Walk</h3><div class="tour-meta"><span>⏱ 3 hrs</span><span>👥 Max 10</span><span>🚶 Walking</span></div><p>Wander cobblestone alleys, hidden courtyards, and centuries-old architecture with a storytelling guide who knows every legend.</p><div class="tour-footer"><div class="tour-price">$49 <span>/ person</span></div><button class="btn-tour" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button></div></div></div>
    <div class="tour-card"><div class="tour-img g2"><span>🌿</span><div class="tour-tag">Nature</div></div><div class="tour-body"><h3>Valley Trails & Vistas</h3><div class="tour-meta"><span>⏱ Full Day</span><span>👥 Max 8</span><span>🥾 Hiking</span></div><p>Breathtaking mountain trails through wildflower meadows and panoramic viewpoints. Includes a local picnic lunch.</p><div class="tour-footer"><div class="tour-price">$89 <span>/ person</span></div><button class="btn-tour" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button></div></div></div>
    <div class="tour-card"><div class="tour-img g3"><span>🍷</span><div class="tour-tag">Food & Wine</div></div><div class="tour-body"><h3>Flavors & Markets Tour</h3><div class="tour-meta"><span>⏱ 4 hrs</span><span>👥 Max 12</span><span>🍽️ Culinary</span></div><p>Taste your way through vibrant local markets, family-run eateries, and a wine cellar with tastings included.</p><div class="tour-footer"><div class="tour-price">$65 <span>/ person</span></div><button class="btn-tour" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book Now</button></div></div></div>
  </div>
</section>
<section class="gallery" id="gallery">
  <div class="gallery-header">
    <div class="section-label">Photo Gallery</div>
    <h2 class="section-title">Moments From Our Tours</h2>
    <p class="section-sub" style="margin:0 auto;">A glimpse of the experiences and places waiting for you.</p>
  </div>
  <div class="gallery-grid">
    <div class="gallery-item g1"><span>🏔️</span><div class="gallery-overlay"><span>Mountain Trails</span></div></div>
    <div class="gallery-item g2"><span>🌸</span><div class="gallery-overlay"><span>Spring Gardens</span></div></div>
    <div class="gallery-item g3"><span>🏘️</span><div class="gallery-overlay"><span>Old Town Charm</span></div></div>
    <div class="gallery-item g4"><span>🌅</span><div class="gallery-overlay"><span>Sunset Views</span></div></div>
    <div class="gallery-item g5"><span>🍜</span><div class="gallery-overlay"><span>Local Flavors</span></div></div>
  </div>
</section>
<section class="why" id="why">
  <div class="why-inner">
    <div class="why-text">
      <div class="section-label">Why Choose Us</div>
      <h2 class="section-title">Tours Led With Heart, Not Just a Script</h2>
      <p class="section-sub">We're a small team of passionate locals who genuinely love sharing our home with curious travelers.</p>
      <div class="why-features">
        <div class="feature-item"><div class="feature-icon">🗺️</div><div class="feature-text"><h4>Expert Local Guides</h4><p>All guides are born-and-raised locals, trained in history, culture, and storytelling.</p></div></div>
        <div class="feature-item"><div class="feature-icon">👨‍👩‍👧</div><div class="feature-text"><h4>Small Groups Only</h4><p>We cap every tour at 12 people so you get a personal, unhurried experience.</p></div></div>
        <div class="feature-item"><div class="feature-icon">♿</div><div class="feature-text"><h4>Inclusive & Accessible</h4><p>We offer adapted routes and accommodate any accessibility needs.</p></div></div>
        <div class="feature-item"><div class="feature-icon">🌱</div><div class="feature-text"><h4>Sustainable Travel</h4><p>We partner with local businesses and offset emissions from every tour.</p></div></div>
      </div>
    </div>
    <div class="why-card">
      <div class="why-card-emoji">🏆</div>
      <h3>Award-Winning<br>Since 2015</h3>
      <p>Recognized as a Top Tour Operator by TripAdvisor, Lonely Planet, and the Regional Tourism Board for four consecutive years.</p>
      <div class="why-card-stars">★★★★★</div>
      <p style="margin-top:0.5rem;font-family:'Arial',sans-serif;font-size:0.82rem;color:rgba(255,255,255,0.6);">4.9 / 5 from 1,200+ reviews</p>
    </div>
  </div>
</section>
<section class="testimonials" id="testimonials">
  <div class="testimonials-header">
    <div class="section-label">Happy Travelers</div>
    <h2 class="section-title">Don't Just Take Our Word For It</h2>
    <p class="section-sub" style="margin:0 auto;">Real reviews from real explorers.</p>
  </div>
  <div class="testimonials-grid">
    <div class="testimonial-card"><div class="testimonial-stars">★★★★★</div><p class="testimonial-text">"The Old Town walk was the highlight of our entire trip. Our guide knew every hidden café, every legend, every nook. I've traveled a lot, and this was genuinely special."</p><div class="testimonial-author"><div class="author-avatar">👩</div><div><div class="author-name">Sarah M.</div><div class="author-trip">Old Town Secrets Walk</div></div></div></div>
    <div class="testimonial-card"><div class="testimonial-stars">★★★★★</div><p class="testimonial-text">"We booked the hiking tour for our anniversary and it exceeded every expectation. Intimate group, stunning scenery, and the picnic lunch was incredible. Already planning to return!"</p><div class="testimonial-author"><div class="author-avatar">👨</div><div><div class="author-name">James & Lena R.</div><div class="author-trip">Valley Trails & Vistas</div></div></div></div>
    <div class="testimonial-card"><div class="testimonial-stars">★★★★★</div><p class="testimonial-text">"The food tour was delicious and so much fun! Our guide took us to spots we never would have found on our own. Such a warm, wonderful experience."</p><div class="testimonial-author"><div class="author-avatar">👩</div><div><div class="author-name">Priya K.</div><div class="author-trip">Flavors & Markets Tour</div></div></div></div>
  </div>
</section>
<section class="contact" id="contact">
  <div class="contact-inner">
    <div class="contact-info">
      <div class="section-label">Get In Touch</div>
      <h2 class="section-title">Let's Plan Your Perfect Tour</h2>
      <p class="section-sub">Have questions or want a custom experience? We'd love to hear from you — we reply within 24 hours.</p>
      <div class="contact-detail"><div class="contact-icon">📍</div><div class="contact-detail-text"><strong>12 Cobblestone Lane, Old Quarter</strong><p>Find us near the central fountain</p></div></div>
      <div class="contact-detail"><div class="contact-icon">📞</div><div class="contact-detail-text"><strong>+1 (555) 012-3456</strong><p>Mon–Sat, 9am – 6pm</p></div></div>
      <div class="contact-detail"><div class="contact-icon">✉️</div><div class="contact-detail-text"><strong>hello@wanderlusttours.com</strong><p>We reply within 24 hours</p></div></div>
    </div>
    <div class="contact-form">
      <h3>Send Us a Message</h3>
      <div class="form-row">
        <div class="form-group"><label>First Name</label><input type="text" id="fname" placeholder="Maria" /></div>
        <div class="form-group"><label>Last Name</label><input type="text" id="lname" placeholder="Garcia" /></div>
      </div>
      <div class="form-group"><label>Email Address</label><input type="email" id="email" placeholder="maria@example.com" /></div>
      <div class="form-group"><label>Interested In</label><select id="tour-interest"><option value="">Select a tour...</option><option>Old Town Secrets Walk</option><option>Valley Trails & Vistas</option><option>Flavors & Markets Tour</option><option>Custom / Private Tour</option><option>Not sure yet</option></select></div>
      <div class="form-group"><label>Message</label><textarea id="message" placeholder="Tell us about your travel dates, group size, or any questions..."></textarea></div>
      <button class="btn-submit" onclick="handleSubmit()">Send My Message ✈️</button>
      <p class="form-note">🔒 We never share your info. No spam, ever.</p>
    </div>
  </div>
</section>
<footer>
  <div class="footer-logo">Wanderlust Tours</div>
  <p>Sharing the world's stories, one small group at a time.</p>
  <div class="footer-links"><a href="#tours">Tours</a><a href="#gallery">Gallery</a><a href="#why">About</a><a href="#testimonials">Reviews</a><a href="#contact">Contact</a></div>
  <p style="margin-top:1rem;font-size:0.78rem;color:rgba(255,255,255,0.35);">© 2026 Wanderlust Tours. All rights reserved.</p>
</footer>
<div class="toast" id="toast">🎉 Message sent! We'll be in touch within 24 hours.</div>
<script>
  function handleSubmit() {
    const fname = document.getElementById('fname').value.trim();
    const email = document.getElementById('email').value.trim();
    if (!fname || !email) { alert('Please fill in at least your name and email.'); return; }
    const toast = document.getElementById('toast');
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 4000);
    ['fname','lname','email','message'].forEach(id => document.getElementById(id).value = '');
    document.getElementById('tour-interest').value = '';
  }
</script>
</body>
</html>
