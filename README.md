<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bloom Valencia Tours</title>

<style>
html { scroll-behavior: smooth; }

body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(135deg, #ffd27f, #ff914d, #ff6a3d);
  background-size: 400% 400%;
  animation: glow 14s ease infinite;
  color: #4a2c1a;
}

@keyframes glow {
  0% {background-position: 0% 50%;}
  50% {background-position: 100% 50%;}
  100% {background-position: 0% 50%;}
}

nav {
  position: fixed;
  width: 100%;
  background: rgba(255,255,255,0.95);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 40px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  z-index: 1000;
}

.logo { font-weight: bold; font-size: 22px; color: #d35400; }

.menu { list-style: none; display: flex; gap: 25px; }

.menu li { position: relative; }

.menu a {
  text-decoration: none;
  color: #4a2c1a;
  font-weight: 500;
}

.dropdown {
  position: absolute;
  top: 30px;
  left: 0;
  background: white;
  border-radius: 12px;
  padding: 10px 0;
  display: none;
  min-width: 220px;
  box-shadow: 0 15px 35px rgba(0,0,0,0.1);
}

.dropdown a {
  display: block;
  padding: 10px 20px;
  color: #d35400;
}

.menu li:hover .dropdown { display: block; }

header {
  padding: 180px 20px 120px;
  text-align: center;
  color: white;
}

header h1 { font-size: 46px; }

.btn {
  display: inline-block;
  margin-top: 25px;
  padding: 14px 30px;
  background: white;
  color: #d35400;
  border-radius: 30px;
  text-decoration: none;
  font-weight: bold;
}

section {
  padding: 90px 20px;
  max-width: 1100px;
  margin: auto;
}

.card {
  background: rgba(255,255,255,0.95);
  padding: 35px;
  border-radius: 25px;
  margin-bottom: 40px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.08);
}

.price {
  font-size: 22px;
  color: #d35400;
  font-weight: bold;
  margin-top: 10px;
}

.availability {
  background: #ffe6cc;
  padding: 10px;
  border-radius: 10px;
  margin-top: 15px;
  font-weight: 500;
}

.button-row a {
  display: inline-block;
  margin: 10px 10px 0 0;
  padding: 10px 20px;
  border-radius: 20px;
  text-decoration: none;
  font-weight: bold;
}

.whatsapp { background: #25D366; color: white; }

.book { background: #d35400; color: white; }

.gallery img {
  width: 100%;
  border-radius: 20px;
  margin-top: 15px;
}

form input, form textarea {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px;
  border-radius: 10px;
  border: 1px solid #ccc;
}

form button {
  background: #d35400;
  color: white;
  padding: 12px 25px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
}

footer {
  text-align: center;
  padding: 40px;
  background: rgba(255,255,255,0.95);
}

@media(max-width:768px){
  nav { flex-direction: column; align-items: flex-start; }
  .menu { flex-direction: column; }
  .dropdown { position: static; box-shadow: none; }
}
</style>
</head>

<body>

<nav>
  <div class="logo">Valencia Sun & Culture</div>
  <ul class="menu">
    <li><a href="#home">Home</a></li>
    <li>
      <a href="#tours">Tours ▾</a>
      <div class="dropdown">
        <a href="#tapas">Tapas & Paella</a>
        <a href="#albufera">Bike & Boat Albufera</a>
      </div>
    </li>
    <li><a href="#contact">Book</a></li>
  </ul>
</nav>

<header id="home">
  <h1>Fun & Educational Cultural Adventures in Valencia</h1>
  <p>Authentic tapas, paella traditions, Mediterranean cycling and nature experiences in small groups.</p>
  <a href="#tours" class="btn">Explore Tours</a>
</header>

<section id="tours">

<div class="card" id="tapas">
  <h2>Tapas & Paella Tour</h2>
  <p>Discover Valencia through flavors — explore the Central Market, taste tapas, and learn the true story behind authentic paella.</p>
  <div class="price">From €55</div>
  <div class="availability">Available: Wednesday – Friday</div>
  <div class="button-row">
    <a href="https://wa.me/17176459295" class="whatsapp">WhatsApp</a>
    <a href="https://tourmeout.com/activity/tapas-and-paella-tour-valencia/" class="book">Book & Pay Online</a>
  </div>
  <div class="gallery">
    <img src="6_Vlc-Tapas-Tour.jpg">
  </div>
</div>

<div class="card" id="albufera">
  <h2>Bike & Boat Tour Albufera – A Rice Paradise</h2>
  <p>Cycle through Turia Gardens and rice fields before enjoying a peaceful boat ride inside Albufera Natural Park.</p>
  <div class="price">From €75</div>
  <div class="availability">Available: Saturday</div>
  <div class="button-row">
    <a href="https://wa.me/17176459295" class="whatsapp">WhatsApp</a>
    <a href="https://tourmeout.com/activity/bike-boat-tour-albufera-valencia/" class="book">Book & Pay Online</a>
  </div>
  <div class="gallery">
    <img src="albufera-valencia.jpg>
  </div>
</div>

</section>

<section id="contact">
  <h2>Request Private or Custom Booking</h2>
  <form action="mailto:michael@tmo.com.es" method="POST" enctype="text/plain">
    <input type="text" name="Name" placeholder="Your Name" required>
    <input type="email" name="Email" placeholder="Your Email" required>
    <textarea name="Message" placeholder="Which tour and date are you interested in?" required></textarea>
    <button type="submit">Send Booking Request</button>
  </form>
</section>

<footer>
  Small-group, sustainable experiences supporting local culture & nature 🌿  
  © 2026 Valencia Sun & Culture Tours
</footer>

</body>
</html>
