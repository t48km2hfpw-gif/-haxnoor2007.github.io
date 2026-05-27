<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
 <meta name="description" content="Martian Technologies - Pioneering autonomous drones for interplanetary exploration and advanced aerial intelligence. Futuristic UAV solutions.">
 <title>Martian Technologies | Next-Gen Drones</title>
 <!-- Google Fonts & Font Awesome -->
 <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=Orbitron:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
 <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
 <style>
 * {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
 }

 body {
 background-color: #05070f;
 font-family: 'Inter', sans-serif;
 color: #eef5ff;
 line-height: 1.5;
 scroll-behavior: smooth;
 overflow-x: hidden;
 }

 /* futuristic animated gradient background */
 .bg-gradient {
 position: fixed;
 top: 0;
 left: 0;
 width: 100%;
 height: 100%;
 z-index: -2;
 background: radial-gradient(circle at 20% 30%, #0a0f1f, #020408);
 }

 .bg-gradient::before {
 content: '';
 position: absolute;
 width: 200%;
 height: 200%;
 top: -50%;
 left: -50%;
 background: radial-gradient(circle, rgba(0, 242, 255, 0.08) 0%, transparent 70%);
 animation: slowDrift 28s infinite alternate;
 z-index: -1;
 }

 @keyframes slowDrift {
 0% { transform: translate(0%, 0%) rotate(0deg); opacity: 0.4; }
 100% { transform: translate(10%, 8%) rotate(5deg); opacity: 0.8; }
 }

 /* custom scrollbar */
 ::-webkit-scrollbar {
 width: 8px;
 }
 ::-webkit-scrollbar-track {
 background: #0f121f;
 }
 ::-webkit-scrollbar-thumb {
 background: #00ccff;
 border-radius: 10px;
 }

 /* container & utilities */
 .container {
 max-width: 1280px;
 margin: 0 auto;
 padding: 0 28px;
 }

 /* glassmorphism navigation */
 .navbar {
 display: flex;
 justify-content: space-between;
 align-items: center;
 flex-wrap: wrap;
 padding: 20px 0;
 border-bottom: 1px solid rgba(0, 242, 255, 0.2);
 backdrop-filter: blur(4px);
 }

 .logo {
 display: flex;
 align-items: center;
 gap: 12px;
 font-family: 'Orbitron', monospace;
 font-weight: 700;
 font-size: 1.7rem;
 letter-spacing: -0.5px;
 background: linear-gradient(135deg, #fff, #00e0ff);
 -webkit-background-clip: text;
 background-clip: text;
 color: transparent;
 }

 .logo i {
 font-size: 2rem;
 color: #00f2ff;
 background: none;
 -webkit-background-clip: unset;
 background-clip: unset;
 color: #0af;
 }

 .nav-links {
 display: flex;
 gap: 2rem;
 flex-wrap: wrap;
 }

 .nav-links a {
 text-decoration: none;
 color: #ccddf8;
 font-weight: 500;
 transition: 0.2s ease;
 font-size: 1rem;
 letter-spacing: 0.5px;
 }

 .nav-links a:hover {
 color: #0af;
 text-shadow: 0 0 6px #00ccff;
 }

 /* buttons */
 .btn {
 display: inline-block;
 padding: 12px 28px;
 border-radius: 40px;
 font-weight: 600;
 text-decoration: none;
 transition: all 0.25s ease;
 font-family: 'Inter', sans-serif;
 letter-spacing: 0.5px;
 backdrop-filter: blur(4px);
 cursor: pointer;
 border: none;
 }

 .btn-primary {
 background: linear-gradient(95deg, #0077ff, #00ccff);
 color: #010101;
 box-shadow: 0 8px 20px rgba(0, 187, 255, 0.25);
 }

 .btn-primary:hover {
 transform: translateY(-3px);
 box-shadow: 0 15px 30px rgba(0, 180, 255, 0.4);
 background: linear-gradient(95deg, #0088ff, #00d4ff);
 }

 .btn-outline {
 border: 1.5px solid #0af;
 background: rgba(0, 170, 255, 0.05);
 color: #0af;
 }

 .btn-outline:hover {
 background: rgba(0, 170, 255, 0.2);
 box-shadow: 0 0 12px rgba(0, 170, 255, 0.5);
 transform: translateY(-2px);
 }

 /* hero section */
 .hero {
 padding: 80px 0 100px;
 display: flex;
 flex-wrap: wrap;
 align-items: center;
 justify-content: space-between;
 gap: 40px;
 }

 .hero-content {
 flex: 1;
 min-width: 280px;
 }

 .hero-badge {
 font-family: 'Orbitron', monospace;
 background: rgba(0, 170, 255, 0.2);
 padding: 6px 18px;
 border-radius: 40px;
 display: inline-block;
 font-size: 0.8rem;
 letter-spacing: 1px;
 backdrop-filter: blur(5px);
 margin-bottom: 20px;
 border-left: 2px solid #0af;
 }

 .hero-content h1 {
 font-size: 3.5rem;
 font-weight: 800;
 font-family: 'Orbitron', monospace;
 line-height: 1.2;
 background: linear-gradient(to right, #ffffff, #7ac7ff, #00e0ff);
 -webkit-background-clip: text;
 background-clip: text;
 color: transparent;
 margin-bottom: 20px;
 }

 .hero-content p {
 font-size: 1.2rem;
 color: #b9d0ff;
 margin-bottom: 32px;
 max-width: 550px;
 }

 .hero-buttons {
 display: flex;
 gap: 18px;
 flex-wrap: wrap;
 }

 .hero-graphic {
 flex: 1;
 display: flex;
 justify-content: center;
 align-items: center;
 }

 .drone-icon-3d {
 font-size: 14rem;
 filter: drop-shadow(0 0 18px #00ccff66);
 animation: hoverFloat 3s infinite ease-in-out;
 color: #0af;
 }

 @keyframes hoverFloat {
 0% { transform: translateY(0px); }
 50% { transform: translateY(-12px); }
 100% { transform: translateY(0px); }
 }

 /* section titles */
 .section-title {
 font-size: 2.5rem;
 font-family: 'Orbitron', monospace;
 text-align: center;
 margin-bottom: 1rem;
 }
 .section-sub {
 text-align: center;
 color: #9ab3e0;
 margin-bottom: 60px;
 max-width: 700px;
 margin-left: auto;
 margin-right: auto;
 }

 /* drone cards */
 .drone-grid {
 display: grid;
 grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
 gap: 32px;
 margin: 50px 0 40px;
 }

 .drone-card {
 background: rgba(12, 20, 35, 0.65);
 backdrop-filter: blur(12px);
 border-radius: 32px;
 padding: 1.8rem;
 border: 1px solid rgba(0, 200, 255, 0.25);
 transition: all 0.3s ease;
 box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.5);
 }

 .drone-card:hover {
 transform: translateY(-8px);
 border-color: #0af;
 box-shadow: 0 25px 40px -12px #00aaff30;
 }

 .drone-img {
 width: 100%;
 height: 200px;
 object-fit: cover;
 border-radius: 24px;
 margin-bottom: 20px;
 transition: 0.3s;
 box-shadow: 0 8px 20px rgba(0,0,0,0.4);
 }

 .drone-card h3 {
 font-size: 1.8rem;
 font-family: 'Orbitron', monospace;
 margin-bottom: 10px;
 }

 .drone-spec {
 font-size: 0.85rem;
 color: #8bb9fe;
 margin: 12px 0;
 display: flex;
 gap: 18px;
 }

 .drone-card p {
 color: #cbddf5;
 margin: 14px 0;
 }

 .price-tag {
 font-weight: 700;
 font-size: 1.5rem;
 color: #0ef;
 margin: 15px 0 12px;
 }

 /* features section */
 .features-grid {
 display: grid;
 grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
 gap: 30px;
 margin: 50px 0 60px;
 }

 .feature-item {
 background: rgba(255, 255, 255, 0.02);
 border-radius: 28px;
 padding: 28px 20px;
 text-align: center;
 backdrop-filter: blur(8px);
 border: 1px solid rgba(0, 242, 255, 0.2);
 transition: 0.2s;
 }

 .feature-item i {
 font-size: 3rem;
 color: #0af;
 margin-bottom: 20px;
 }

 .feature-item h4 {
 font-size: 1.5rem;
 margin-bottom: 12px;
 font-weight: 600;
 }

 /* stats */
 .stats-row {
 display: flex;
 justify-content: space-around;
 flex-wrap: wrap;
 background: rgba(0, 30, 50, 0.5);
 border-radius: 70px;
 padding: 40px 20px;
 margin: 70px 0;
 border: 1px solid #00ccff30;
 }
 .stat {
 text-align: center;
 padding: 0 20px;
 }
 .stat-number {
 font-size: 2.7rem;
 font-weight: 800;
 font-family: 'Orbitron', monospace;
 color: #0ef;
 }

 /* contact form */
 .contact-section {
 background: rgba(5, 15, 25, 0.7);
 border-radius: 48px;
 padding: 50px 40px;
 margin: 50px 0 60px;
 border: 1px solid #0af33;
 }
 .form-group {
 margin-bottom: 20px;
 }
 input, textarea {
 width: 100%;
 padding: 15px 20px;
 background: #0a111f;
 border: 1px solid #2a4670;
 border-radius: 28px;
 color: white;
 font-family: 'Inter', sans-serif;
 transition: 0.2s;
 }
 input:focus, textarea:focus {
 outline: none;
 border-color: #0af;
 box-shadow: 0 0 12px #0af5;
 }
 .contact-grid {
 display: grid;
 grid-template-columns: 1fr 1fr;
 gap: 40px;
 }
 @media (max-width: 800px) {
 .contact-grid {
 grid-template-columns: 1fr;
 }
 .hero-content h1 {
 font-size: 2.5rem;
 }
 .drone-icon-3d {
 font-size: 9rem;
 }
 }
 .footer {
 border-top: 1px solid rgba(0, 200, 255, 0.2);
 padding: 40px 0 30px;
 margin-top: 60px;
 display: flex;
 justify-content: space-between;
 flex-wrap: wrap;
 gap: 20px;
 }
 .social-icons a {
 color: #b0ceff;
 font-size: 1.5rem;
 margin-left: 20px;
 transition: 0.2s;
 }
 .social-icons a:hover {
 color: #0af;
 }

 @keyframes glowPulse {
 0% { text-shadow: 0 0 2px #0af;}
 100% { text-shadow: 0 0 12px #0af;}
 }
 button:active {
 transform: scale(0.97);
 }
 a, button {
 cursor: pointer;
 }
 </style>
</head>
<body>
<div class="bg-gradient"></div>

<div class="container">
 <!-- Navigation -->
 <nav class="navbar">
 <div class="logo">
 <i class="fas fa-drone"></i>
 <span>MARTIAN TECH</span>
 </div>
 <div class="nav-links">
 <a href="#home">HOME</a>
 <a href="#drones">DRONES</a>
 <a href="#features">TECH</a>
 <a href="#contact">CONTACT</a>
 </div>
 </nav>

 <!-- Hero Section -->
 <section id="home">
 <div class="hero">
 <div class="hero-content">
 <span class="hero-badge"><i class="fas fa-microchip"></i> MARS-READY AUTONOMY</span>
 <h1>Martian Technologies<br>Beyond Horizon Drones</h1>
 <p>AI-driven UAVs engineered for Mars exploration, extreme environments, and next-gen aerial intelligence. From terraforming scouts to urban logistic drones — the future flies with Martian Tech.</p>
 <div class="hero-buttons">
 <a href="#drones" class="btn btn-primary"><i class="fas fa-rocket"></i> Explore Fleet</a>
 <a href="#contact" class="btn btn-outline"><i class="fas fa-chevron-circle-right"></i> Contact Sales</a>
 </div>
 </div>
 <div class="hero-graphic">
 <i class="fas fa-drone drone-icon-3d"></i>
 </div>
 </div>
 </section>

 <!-- Featured Drones -->
 <section id="drones">
 <h2 class="section-title"> INTERPLANETARY DRONES </h2>
 <div class="section-sub">Autonomous • Quantum-resistant navigation • Solar & nuclear hybrid power</div>
 <div class="drone-grid">
 <!-- Drone 1 -->
 <div class="drone-card">
 <img class="drone-img" src="https://images.unsplash.com/photo-1507582020474-9a35b7d455d9?w=500&h=300&fit=crop" alt="Martian X1 Stratos Drone" loading="lazy">
 <h3>MARTIAN X1</h3>
 <div class="drone-spec"><span><i class="fas fa-bolt"></i> 120 min flight</span><span><i class="fas fa-satellite"></i> 50km range</span></div>
 <p>Flagship tactical drone with LiDAR mapping, AI swarm logic, and Mars-grade thermal shielding.</p>
 <div class="price-tag">$3,899 <span style="font-size: 0.9rem;">/ unit</span></div>
 <a href="#" class="btn-outline" style="display: inline-block; padding: 8px 20px;">Pre-order <i class="fas fa-arrow-right"></i></a>
 </div>
 <!-- Drone 2 -->
 <div class="drone-card">
 <img class="drone-img" src="https://images.unsplash.com/photo-1527977966376-1c8408f9f108?w=500&h=300&fit=crop" alt="Red Horizon Drone" loading="lazy">
 <h3>RED HORIZON</h3>
 <div class="drone-spec"><span><i class="fas fa-tachometer-alt"></i> Mach 0.8</span><span><i class="fas fa-eye"></i> 8K EO/IR</span></div>
 <p>High-altitude reconnaissance drone, operates in low-pressure CO₂ atmosphere. Mars simulation tested.</p>
 <div class="price-tag">$5,490</div>
 <a href="#" class="btn-outline" style="display: inline-block; padding: 8px 20px;">Configure <i class="fas fa-arrow-right"></i></a>
 </div>
 <!-- Drone 3 -->
 <div class="drone-card">
 <img class="drone-img" src="https://images.unsplash.com/photo-1558981403-c5f9899a28bc?w=500&h=300&fit=crop" alt="Aether MK-II Cargo Drone" loading="lazy">
 <h3>AETHER MK-II</h3>
 <div class="drone-spec"><span><i class="fas fa-cubes"></i> 25kg payload</span><span><i class="fas fa-charging-station"></i> Wireless charge</span></div>
 <p>Logistics & sample-return drone with foldable rotors, ultra-durable carbon composite frame.</p>
 <div class="price-tag">$7,250</div>
 <a href="#" class="btn-outline" style="display: inline-block; padding: 8px 20px;">Learn More <i class="fas fa-arrow-right"></i></a>
 </div>
 </div>
 </section>

 <!-- Tech Features -->
 <section id="features">
 <h2 class="section-title">⟡ QUANTUM EDGE TECHNOLOGY ⟡</h2>
 <div class="section-sub">Redefining drone autonomy with Martian-grade innovation</div>
 <div class="features-grid">
 <div class="feature-item"><i class="fas fa-brain"></i><h4>Neural AI Core</h4><p>Real-time adaptive navigation in GPS-denied environments. Swarm intelligence & collision avoidance.</p></div>
 <div class="feature-item"><i class="fas fa-shield-alt"></i><h4>Quantum Encryption</h4><p>Military-grade secure data links & anti-jamming protocols for sensitive missions.</p></div>
 <div class="feature-item"><i class="fas fa-solar-panel"></i><h4>Ion-Hybrid Power</h4><p>Solar-Nuclear battery backup → 6h+ flight endurance on extreme terrains.</p></div>
 <div class="feature-item"><i class="fas fa-globe-americas"></i><h4>Mars Climate Adapt</h4><p>Radiation hardened electronics & -120°C to +70°C operational range.</p></div>
 </div>
 </section>

 <!-- Stats Section -->
 <div class="stats-row">
 <div class="stat"><div class="stat-number">350+</div><div>Missions Completed</div></div>
 <div class="stat"><div class="stat-number">14</div><div>Planetary Prototypes</div></div>
 <div class="stat"><div class="stat-number">50+</div><div>Patents & Innovations</div></div>
 <div class="stat"><div class="stat-number">100%</div><div>AI-Powered Fleet</div></div>
 </div>

 <!-- About / Martian Mission Statement -->
 <div style="margin: 40px 0; text-align: center; background: linear-gradient(145deg, #07121e, #01060e); border-radius: 48px; padding: 40px 25px;">
 <i class="fas fa-mars" style="font-size: 3rem; color: #ff7b5c;"></i>
 <h3 style="font-size: 2rem; font-family: 'Orbitron'; margin: 15px 0;">Mars is just the beginning</h3>
 <p style="max-width: 800px; margin: 0 auto; color: #bbddff;">Martian Technologies fuses aerospace engineering with advanced AI to build drones that redefine exploration. Our fleet supports NASA, ESA, and commercial partners, pushing the boundaries of autonomous flight – from red deserts to future smart cities.</p>
 </div>

 <!-- Contact & Newsletter -->
 <section id="contact">
 <div class="contact-section">
 <h2 class="section-title" style="text-align: left;"> Connect with Martian Tech</h2>
 <div class="contact-grid">
 <div>
 <p style="margin-bottom: 25px; font-size: 1.1rem;">Request a demo, inquire about bulk orders, or join our early access for the next-gen drone ecosystem.</p>
 <div style="margin-bottom: 30px;"><i class="fas fa-envelope"></i> hello@martiantech.space<br><i class="fas fa-phone-alt"></i> +1 (800) 874-3827<br><i class="fas fa-map-marker-alt"></i> Mars Innovation Hub, Mojave Base, CA</div>
 <div class="social-icons">
 <a href="#"><i class="fab fa-twitter"></i></a>
 <a href="#"><i class="fab fa-linkedin-in"></i></a>
 <a href="#"><i class="fab fa-github"></i></a>
 <a href="#"><i class="fab fa-discord"></i></a>
 </div>
 </div>
 <div>
 <form id="contactForm">
 <div class="form-group"><input type="text" placeholder="Full Name" id="name" required></div>
 <div class="form-group"><input type="email" placeholder="Email Address" id="email" required></div>
 <div class="form-group"><textarea rows="3" placeholder="Tell us about your drone requirements..." id="message"></textarea></div>
 <button type="submit" class="btn btn-primary" style="width: 100%;"><i class="fas fa-paper-plane"></i> Send Message</button>
 </form>
 <p id="formStatus" style="margin-top: 15px; font-size: 0.8rem; color: #0af;"></p>
 </div>
 </div>
 </div>
 </section>

 <!-- Footer -->
 <footer class="footer">
 <div>© 2026 MARTIAN TECHNOLOGIES — Forging the Future of Flight | All trademarks belong to their respective owners.</div>
 <div><i class="fas fa-drone"></i> <span style="letter-spacing: 2px;">AEROSPACE DIVISION</span></div>
 </footer>
</div>

<script>
 // Simple interactive contact form with futuristic feedback
 const contactForm = document.getElementById('contactForm');
 const statusMsg = document.getElementById('formStatus');

 contactForm.addEventListener('submit', (e) => {
 e.preventDefault();
 const name = document.getElementById('name').value.trim();
 const email = document.getElementById('email').value.trim();
 const message = document.getElementById('message').value.trim();

 if (!name || !email || !message) {
 statusMsg.innerHTML = '<i class="fas fa-exclamation-triangle"></i> Please fill all fields.';
 statusMsg.style.color = "#ff8060";
 setTimeout(() => { statusMsg.innerHTML = ''; }, 3000);
 return;
 }
 if (!email.includes('@') || !email.includes('.')) {
 statusMsg.innerHTML = '<i class="fas fa-times-circle"></i> Enter valid email address.';
 statusMsg.style.color = "#ff8060";
 setTimeout(() => { statusMsg.innerHTML = ''; }, 3000);
 return;
 }
 // mock success
 statusMsg.innerHTML = '<i class="fas fa-check-circle"></i> Transmission received! Martian team will contact you soon.';
 statusMsg.style.color = "#0ef";
 contactForm.reset();
 setTimeout(() => { statusMsg.innerHTML = ''; }, 4000);
 });

 // smooth scrolling for anchor links
 document.querySelectorAll('.nav-links a, .hero-buttons a, .btn-outline').forEach(anchor => {
 anchor.addEventListener('click', function(e) {
 const hash = this.getAttribute('href');
 if (hash && hash.startsWith('#') && hash !== '#') {
 e.preventDefault();
 const target = document.querySelector(hash);
 if(target) {
 target.scrollIntoView({ behavior: 'smooth', block: 'start' });
 }
 }
 });
 });

 // Additional pre-order / dummy buttons not to cause reload
 const allDemoBtns = document.querySelectorAll('.drone-card .btn-outline');
 allDemoBtns.forEach(btn => {
 btn.addEventListener('click', (e) => {
 e.preventDefault();
 alert(' Martian Technologies: This product will be available for order soon. Stay tuned for interplanetary delivery options!');
 });
 });

 // Add tiny parallax hover for drone-icon (cosmetic)
 const droneIcon = document.querySelector('.drone-icon-3d');
 if(droneIcon) {
 document.addEventListener('mousemove', (e) => {
 const xAxis = (window.innerWidth / 2 - e.pageX) / 35;
 const yAxis = (window.innerHeight / 2 - e.pageY) / 35;
 droneIcon.style.transform = `translateY(${yAxis * -0.5}px) rotateX(${yAxis * 0.2}deg) rotateY(${xAxis * 0.2}deg)`;
 });
 }
</script>
</body>
</html>
