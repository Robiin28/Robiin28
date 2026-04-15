<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Robel | Data Engineer & Backend Alchemist</title>
  <!-- Google Fonts + Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(circle at 10% 20%, #0a0f1e, #03060c);
      font-family: 'Inter', sans-serif;
      color: #eef5ff;
      line-height: 1.5;
      overflow-x: hidden;
      position: relative;
    }

    /* animated background particles (floating data nodes) */
    .particle-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }

    .main-container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 2rem 4rem;
      position: relative;
      z-index: 2;
      backdrop-filter: blur(0px);
    }

    /* Glassmorphic card style */
    .glass-card {
      background: rgba(15, 25, 45, 0.55);
      backdrop-filter: blur(12px);
      border-radius: 2rem;
      border: 1px solid rgba(72, 187, 255, 0.2);
      box-shadow: 0 20px 35px -12px rgba(0,0,0,0.5), 0 0 0 0.5px rgba(0, 255, 255, 0.1) inset;
      transition: transform 0.2s ease, border-color 0.2s;
    }

    .glass-card:hover {
      border-color: rgba(0, 212, 255, 0.5);
      box-shadow: 0 25px 40px -12px rgba(0, 200, 255, 0.2);
    }

    /* profile header with 3D image animation */
    .hero-section {
      text-align: center;
      padding: 2rem 1.5rem 1.8rem;
      margin-bottom: 2.5rem;
    }

    .avatar-frame {
      display: inline-block;
      margin-bottom: 1rem;
      perspective: 600px;
    }

    .floating-avatar {
      width: 140px;
      height: 140px;
      background: linear-gradient(135deg, #1e2a4a, #0b1120);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 4rem;
      font-weight: bold;
      color: #7bc5ff;
      box-shadow: 0 20px 30px -8px rgba(0,0,0,0.5), 0 0 0 3px rgba(0, 230, 250, 0.5);
      animation: floatImage 4s ease-in-out infinite, glitchFlicker 6s infinite alternate;
      transition: all 0.3s;
      border: 1px solid rgba(0, 255, 255, 0.7);
    }

    @keyframes floatImage {
      0% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-12px) rotate(2deg); }
      100% { transform: translateY(0px) rotate(0deg); }
    }

    @keyframes glitchFlicker {
      0% { text-shadow: 2px 0px 0px cyan, -2px 0px 0px magenta; box-shadow: 0 0 0 3px cyan; }
      100% { text-shadow: -1px 0px 0px cyan, 1px 0px 0px magenta; box-shadow: 0 0 0 4px magenta; }
    }

    h1 {
      font-size: 3.5rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #5bc0ff, #a57cff);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
      margin-bottom: 0.5rem;
    }

    .tagline {
      font-size: 1.25rem;
      font-weight: 400;
      background: rgba(0, 180, 255, 0.2);
      display: inline-block;
      padding: 0.4rem 1.2rem;
      border-radius: 60px;
      backdrop-filter: blur(4px);
      margin-top: 0.5rem;
    }

    .badge-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 1.8rem 0 0;
    }

    .badge {
      background: rgba(10, 20, 35, 0.7);
      padding: 0.6rem 1.2rem;
      border-radius: 40px;
      font-weight: 600;
      font-size: 0.85rem;
      backdrop-filter: blur(4px);
      transition: 0.2s;
      border-left: 2px solid cyan;
      transform: skew(-2deg);
    }

    .badge i {
      margin-right: 8px;
      color: cyan;
    }

    /* section styles */
    .section-title {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 1.2rem;
      display: flex;
      align-items: center;
      gap: 12px;
      border-left: 5px solid #0af;
      padding-left: 1rem;
    }

    .grid-2col {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 1.8rem;
      margin-bottom: 2.8rem;
    }

    .info-panel {
      padding: 1.5rem;
      transition: all 0.2s;
    }

    .info-panel p {
      margin: 1rem 0;
      font-size: 1rem;
      color: #cbd5f0;
    }

    .tech-stack {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      margin-top: 1rem;
    }

    .tech-tag {
      background: #0e1a2b;
      border-radius: 30px;
      padding: 0.4rem 1rem;
      font-size: 0.85rem;
      font-weight: 500;
      font-family: monospace;
      border: 1px solid #2c4b6e;
      transition: 0.2s;
    }

    .tech-tag:hover {
      background: #1c3f5c;
      transform: translateY(-3px);
      border-color: cyan;
      box-shadow: 0 4px 12px rgba(0,255,255,0.2);
    }

    .interest-list {
      list-style: none;
      margin-top: 0.5rem;
    }

    .interest-list li {
      margin: 0.8rem 0;
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: 1rem;
    }

    .interest-list li i {
      width: 28px;
      color: cyan;
      font-size: 1.2rem;
    }

    .contact-btn {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      background: linear-gradient(95deg, #0a2942, #001e3c);
      padding: 0.8rem 2rem;
      border-radius: 60px;
      font-weight: bold;
      font-size: 1.1rem;
      transition: 0.2s;
      border: 1px solid cyan;
      text-decoration: none;
      color: white;
    }

    .contact-btn:hover {
      background: #0e4b6e;
      transform: scale(1.03);
      box-shadow: 0 0 15px cyan;
      letter-spacing: 1px;
    }

    footer {
      text-align: center;
      margin-top: 3rem;
      font-size: 0.85rem;
      opacity: 0.7;
    }

    /* animated data stream effect */
    .data-stream {
      position: fixed;
      bottom: 20px;
      left: 0;
      width: 100%;
      font-size: 12px;
      font-family: monospace;
      color: cyan;
      opacity: 0.3;
      pointer-events: none;
      white-space: nowrap;
      overflow: hidden;
      z-index: 1;
    }

    @keyframes slideText {
      0% { transform: translateX(100%); }
      100% { transform: translateX(-200%); }
    }

    .marquee-stream {
      display: inline-block;
      animation: slideText 28s linear infinite;
      padding-left: 20px;
    }

    /* responsive */
    @media (max-width: 780px) {
      h1 { font-size: 2.4rem; }
      .main-container { padding: 1.2rem; }
    }
  </style>
</head>
<body>

<canvas class="particle-canvas" id="particleCanvas"></canvas>

<div class="data-stream">
  <div class="marquee-stream">
    ⚡ DATA PIPELINE • KAFKA STREAMS • SQL OPTIMIZATION • API INTEGRATION • ETL WORKFLOWS • REALTIME ANALYTICS • BACKEND RESILIENCE ⚡
  </div>
</div>

<div class="main-container">
  <!-- Hero with image animation and glitch style -->
  <div class="hero-section glass-card">
    <div class="avatar-frame">
      <div class="floating-avatar">
        <i class="fas fa-database fa-fw" style="font-size: 4rem; filter: drop-shadow(0 0 6px cyan);"></i>
      </div>
    </div>
    <h1>Hi 👋, I'm Robel</h1>
    <div class="tagline">
      <i class="fas fa-cogs"></i> Data Engineer | Backend Systems | API & Data Integration Enthusiast
    </div>
    <div class="badge-row">
      <div class="badge"><i class="fas fa-chart-line"></i> Data Engineering</div>
      <div class="badge"><i class="fas fa-server"></i> Backend APIs</div>
      <div class="badge"><i class="fas fa-code-branch"></i> SQL | PHP | Python</div>
      <div class="badge"><i class="fas fa-stream"></i> Kafka-ready</div>
    </div>
  </div>

  <!-- About Me + Tech mix -->
  <div class="grid-2col">
    <div class="glass-card info-panel">
      <div class="section-title" style="border-left-color: #0af; margin-bottom: 1rem;">
        <i class="fas fa-user-astronaut"></i> 👨‍💻 About Me
      </div>
      <p><i class="fas fa-database" style="margin-right: 8px; color: cyan;"></i> Data-focused engineer working on <strong>backend systems and data workflows</strong></p>
      <p><i class="fas fa-chart-simple"></i> Strong interest in <strong>scalable data pipelines and system design</strong></p>
      <p><i class="fas fa-check-circle"></i> Experienced in <strong>data validation, transformation, and integration</strong></p>
      <p><i class="fas fa-plug"></i> Comfortable working across <strong>backend, APIs, and data layers</strong></p>
      <p><i class="fas fa-heart"></i> Passionate about building <strong>reliable and clean data systems</strong></p>
    </div>

    <div class="glass-card info-panel">
      <div class="section-title" style="border-left-color: #0af;">
        <i class="fas fa-cubes"></i> 🛠️ Tech Stack
      </div>
      <div><strong>Languages</strong></div>
      <div class="tech-stack">
        <span class="tech-tag"><i class="fab fa-python"></i> Python</span>
        <span class="tech-tag"><i class="fas fa-database"></i> SQL</span>
        <span class="tech-tag"><i class="fab fa-php"></i> PHP (Laravel)</span>
      </div>
      <div style="margin-top: 1.2rem;"><strong>Data & Backend</strong></div>
      <div class="tech-stack">
        <span class="tech-tag"><i class="fas fa-cloud-upload-alt"></i> REST APIs</span>
        <span class="tech-tag"><i class="fab fa-apache"></i> Kafka</span>
        <span class="tech-tag"><i class="fas fa-random"></i> ETL/ELT</span>
        <span class="tech-tag"><i class="fas fa-broom"></i> Data Cleaning</span>
      </div>
      <div style="margin-top: 1.2rem;"><strong>Tools & Workflow</strong></div>
      <div class="tech-stack">
        <span class="tech-tag"><i class="fab fa-git-alt"></i> Git/GitHub</span>
        <span class="tech-tag"><i class="fas fa-flask"></i> Postman</span>
        <span class="tech-tag"><i class="fab fa-linux"></i> Linux</span>
        <span class="tech-tag"><i class="fab fa-jira"></i> Jira/Agile</span>
        <span class="tech-tag"><i class="fas fa-chart-bar"></i> Excel Advanced</span>
      </div>
    </div>
  </div>

  <!-- What I Work On + Interests with animated cards -->
  <div class="grid-2col">
    <div class="glass-card info-panel">
      <div class="section-title"><i class="fas fa-chalkboard-user"></i> 📊 What I Work On</div>
      <ul class="interest-list">
        <li><i class="fas fa-pipeline"></i> Designing and supporting <strong>data pipelines</strong></li>
        <li><i class="fas fa-bug"></i> Debugging and fixing <strong>data inconsistencies</strong></li>
        <li><i class="fas fa-plug"></i> Integrating and testing <strong>APIs</strong></li>
        <li><i class="fas fa-network-wired"></i> Working with backend teams on <strong>system reliability</strong></li>
        <li><i class="fas fa-chart-line"></i> Improving <strong>data quality and reporting accuracy</strong></li>
      </ul>
    </div>

    <div class="glass-card info-panel">
      <div class="section-title"><i class="fas fa-rocket"></i> 🚀 Interests</div>
      <ul class="interest-list">
        <li><i class="fas fa-dharmachakra"></i> Data engineering & distributed systems</li>
        <li><i class="fas fa-bolt"></i> Event-driven architecture (Kafka-style systems)</li>
        <li><i class="fas fa-tachometer-alt"></i> Backend optimization & APIs</li>
        <li><i class="fas fa-brain"></i> AI systems built on structured data (RAG, retrieval)</li>
        <li><i class="fas fa-chart-network"></i> Real-time stream processing</li>
      </ul>
    </div>
  </div>

  <!-- Extra unique animation: rotating data stats -->
  <div class="glass-card info-panel" style="margin-bottom: 2rem; text-align: center;">
    <div class="section-title" style="justify-content: center; border-left: none;">
      <i class="fas fa-chart-simple" style="animation: pulse 1.8s infinite;"></i> Live Data Pulse
    </div>
    <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;">
      <div class="stat-item">
        <i class="fas fa-database fa-2x" style="color: cyan;"></i>
        <div class="stat-number" id="rowsProcessed">0</div>
        <div>Rows Processed (sim)</div>
      </div>
      <div class="stat-item">
        <i class="fas fa-clock fa-2x" style="color: #0af;"></i>
        <div class="stat-number" id="apiCalls">0</div>
        <div>API Calls Simulated</div>
      </div>
      <div class="stat-item">
        <i class="fas fa-check-circle fa-2x" style="color: #4cff9e;"></i>
        <div class="stat-number" id="qualityScore">98.4</div>
        <div>Data Quality %</div>
      </div>
    </div>
    <p style="font-size: 0.7rem; margin-top: 1rem; opacity: 0.7;">✨ real-time animated metrics — stream heartbeat ✨</p>
  </div>

  <!-- Contact section with interactive hover and copy mail effect -->
  <div class="glass-card info-panel" style="text-align: center; margin-bottom: 2rem;">
    <div class="section-title" style="justify-content: center; border-left: none;">📫 Connect & Collaborate</div>
    <p style="margin-bottom: 1.2rem;">Let's build data systems that scale — reach out anytime!</p>
    <a href="mailto:robel.data@engineer.dev" class="contact-btn" id="contactBtn">
      <i class="fas fa-paper-plane"></i> robel.data@engineer.dev
    </a>
    <p style="margin-top: 1rem; font-size: 0.8rem;"><i class="fas fa-globe"></i> Based in Addis / Remote · Open for data talks</p>
  </div>

  <footer>
    <p>⚡ Building reliable systems through clean data and strong engineering principles ⚡</p>
    <p style="margin-top: 10px;"><i class="fas fa-code"></i> Unique animated portfolio | data-driven vibe</p>
  </footer>
</div>

<script>
  // 1) Canvas particle system - unique animated nodes that move like data streams
  const canvas = document.getElementById('particleCanvas');
  let ctx = canvas.getContext('2d');
  let width = window.innerWidth;
  let height = window.innerHeight;
  let particles = [];

  function resizeCanvas() {
    width = window.innerWidth;
    height = window.innerHeight;
    canvas.width = width;
    canvas.height = height;
  }

  class DataParticle {
    constructor(x, y, vx, vy, size, color) {
      this.x = x;
      this.y = y;
      this.vx = vx;
      this.vy = vy;
      this.size = size;
      this.color = color;
      this.alpha = Math.random() * 0.6 + 0.2;
    }
    update() {
      this.x += this.vx;
      this.y += this.vy;
      if (this.x > width + 20) this.x = -20;
      if (this.x < -20) this.x = width + 20;
      if (this.y > height + 20) this.y = -20;
      if (this.y < -20) this.y = height + 20;
    }
    draw() {
      ctx.beginPath();
      ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(${this.color.r}, ${this.color.g}, ${this.color.b}, ${this.alpha})`;
      ctx.fill();
      ctx.shadowBlur = 8;
      ctx.shadowColor = `rgba(0, 200, 255, 0.5)`;
    }
  }

  function initParticles() {
    particles = [];
    const colors = [
      {r:0, g:180, b:255}, {r:100, g:200, b:255}, {r:0, g:220, b:200}, {r:180, g:100, b:255}
    ];
    for (let i = 0; i < 110; i++) {
      let x = Math.random() * width;
      let y = Math.random() * height;
      let vx = (Math.random() - 0.5) * 0.6;
      let vy = (Math.random() - 0.5) * 0.5;
      let size = Math.random() * 3 + 1.5;
      let col = colors[Math.floor(Math.random() * colors.length)];
      particles.push(new DataParticle(x, y, vx, vy, size, col));
    }
  }

  function animateParticles() {
    if (!ctx) return;
    ctx.clearRect(0, 0, width, height);
    for (let p of particles) {
      p.update();
      p.draw();
    }
    // draw some connecting lines occasionally for network effect
    ctx.beginPath();
    ctx.strokeStyle = "rgba(0, 200, 255, 0.12)";
    for (let i = 0; i < particles.length; i++) {
      for (let j = i+1; j < particles.length; j++) {
        const dx = particles[i].x - particles[j].x;
        const dy = particles[i].y - particles[j].y;
        const dist = Math.hypot(dx, dy);
        if (dist < 70) {
          ctx.beginPath();
          ctx.moveTo(particles[i].x, particles[i].y);
          ctx.lineTo(particles[j].x, particles[j].y);
          ctx.stroke();
        }
      }
    }
    requestAnimationFrame(animateParticles);
  }

  window.addEventListener('resize', () => {
    resizeCanvas();
    initParticles();
  });
  resizeCanvas();
  initParticles();
  animateParticles();

  // 2) Live stats simulation (image animation feel + dynamic counters)
  let rows = 0;
  let apiCalls = 0;
  const rowsElement = document.getElementById('rowsProcessed');
  const apiElement = document.getElementById('apiCalls');

  function updateStats() {
    rows += Math.floor(Math.random() * 12) + 3;   // increment 3-14
    apiCalls += Math.floor(Math.random() * 5) + 1;
    if (rowsElement) rowsElement.innerText = rows.toLocaleString();
    if (apiElement) apiElement.innerText = apiCalls.toLocaleString();
    // fluctuating quality score between 97.2 and 99.6
    const qualitySpan = document.getElementById('qualityScore');
    if (qualitySpan) {
      let newQuality = 97.2 + Math.sin(Date.now() / 4000) * 1.2;
      qualitySpan.innerText = newQuality.toFixed(1);
    }
    setTimeout(updateStats, 2100);
  }
  updateStats();

  // 3) Hover glitch effect on avatar or mail copy alert simulation
  const avatarDiv = document.querySelector('.floating-avatar');
  if (avatarDiv) {
    avatarDiv.addEventListener('mouseenter', () => {
      avatarDiv.style.transform = 'scale(1.02) rotate(1deg)';
      avatarDiv.style.filter = 'drop-shadow(0 0 12px cyan)';
    });
    avatarDiv.addEventListener('mouseleave', () => {
      avatarDiv.style.transform = '';
      avatarDiv.style.filter = '';
    });
  }

  // 4) Email button subtle notification
  const contactBtn = document.getElementById('contactBtn');
  if (contactBtn) {
    contactBtn.addEventListener('click', (e) => {
      e.preventDefault();
      const mail = "robel.data@engineer.dev";
      navigator.clipboard.writeText(mail).then(() => {
        const originalText = contactBtn.innerHTML;
        contactBtn.innerHTML = '<i class="fas fa-check-circle"></i> Copied!';
        setTimeout(() => {
          contactBtn.innerHTML = originalText;
        }, 1800);
      }).catch(() => {
        alert("📧 " + mail);
      });
    });
  }

  // 5) Additional floating elements (CSS already includes glitch + stream), 
  // but we also add interactive stat cards pulse with intervals
  const statItems = document.querySelectorAll('.stat-item');
  statItems.forEach((item, idx) => {
    item.style.transition = "all 0.2s";
    item.addEventListener('mouseover', () => {
      item.style.transform = "translateY(-6px)";
      item.style.textShadow = "0 0 3px cyan";
    });
    item.addEventListener('mouseout', () => {
      item.style.transform = "translateY(0px)";
      item.style.textShadow = "none";
    });
  });

  // 6) background visual + custom cursor effect (optional)
  document.body.style.cursor = 'default';
  const style = document.createElement('style');
  style.innerHTML = `
    .stat-item {
      background: rgba(0, 20, 40, 0.7);
      padding: 0.8rem 1.4rem;
      border-radius: 2rem;
      text-align: center;
      min-width: 120px;
      backdrop-filter: blur(4px);
      border: 1px solid rgba(0,255,255,0.2);
      transition: 0.2s;
    }
    .stat-number {
      font-size: 1.8rem;
      font-weight: 800;
      font-family: monospace;
      background: linear-gradient(135deg, #eef, #0af);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }
    i.fa, i.fas, i.far {
      filter: drop-shadow(0 0 2px cyan);
    }
  `;
  document.head.appendChild(style);

  // extra marquee smoothness (data stream text)
  const marqueeDiv = document.querySelector('.marquee-stream');
  if (marqueeDiv) {
    marqueeDiv.style.whiteSpace = 'nowrap';
  }
</script>
</body>
</html>
