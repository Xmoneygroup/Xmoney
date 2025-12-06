
<!doctype html>
<html lang="sq">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Starfield Canvas Background</title>
<style>
  html,body{height:100%;margin:0}
  body{background:#030217;color:#fff;font-family:system-ui,Arial}
  canvas { position:fixed; inset:0; width:100%; height:100%; z-index:-1; display:block; }
  .ui { position:relative; z-index:1; display:flex; align-items:center; justify-content:center; height:100vh; }
  h1 { margin:0; font-size: clamp(1.5rem, 5vw, 3rem); text-align:center; }
</style>
</head>
<body>
  <canvas id="starfield"></canvas>
  <div class="ui">
    <h1>Starfield — Parallax</h1>
  </div>

<script>
(() => {
  const canvas = document.getElementById('starfield');
  const ctx = canvas.getContext('2d');
  let w, h, stars = [], cx = 0, cy = 0;
  const DPR = Math.min(window.devicePixelRatio || 1, 2);

  function resize() {
    w = canvas.clientWidth;
    h = canvas.clientHeight;
    canvas.width = Math.floor(w * DPR);
    canvas.height = Math.floor(h * DPR);
    ctx.setTransform(DPR, 0, 0, DPR, 0, 0);
    initStars();
  }

  function initStars() {
    stars = [];
    // density: approx 0.0008 stars per px^2 (adjustable)
    const area = w * h;
    const count = Math.round(Math.max(60, area * 0.0008));
    for (let i=0;i<count;i++){
      stars.push({
        x: Math.random() * w,
        y: Math.random() * h,
        z: Math.random() * 1, // depth 0..1 (closer = brighter)
        r: Math.random() * 1.6 + 0.4,
        twinkle: Math.random() * Math.PI * 2,
        speed: 0.02 + Math.random()*0.06
      });
    }
  }

  let last = 0;
  function draw(t) {
    const dt = Math.min(50, t - last);
    last = t;
    // gentle background gradient
    const g = ctx.createLinearGradient(0,0,0,h);
    g.addColorStop(0,'#040017');
    g.addColorStop(1,'#000010');
    ctx.fillStyle = g;
    ctx.fillRect(0,0,w,h);

    // small faint nebula blobs for depth
    ctx.globalCompositeOperation = 'lighter';
    ctx.save();
    ctx.fillStyle = 'rgba(30,10,80,0.06)';
    ctx.beginPath(); ctx.ellipse(w*0.15, h*0.2, w*0.35, h*0.24, 0,0,Math.PI*2); ctx.fill();
    ctx.beginPath(); ctx.ellipse(w*0.78, h*0.78, w*0.4, h*0.32, 0,0,Math.PI*2); ctx.fill();
    ctx.restore();

    // draw stars
    for (let i=0;i<stars.length;i++){
      const s = stars[i];
      // parallax offset depends on depth
      const px = (cx * (1 - s.z * 0.9));
      const py = (cy * (1 - s.z * 0.9));
      const x = (s.x + px * (0.05 + s.z*0.2)) % (w + 50);
      const y = (s.y + py * (0.05 + s.z*0.2)) % (h + 50);

      // twinkle
      s.twinkle += dt * 0.002 * s.speed;
      const flick = 0.6 + 0.4 * Math.sin(s.twinkle);
      const alpha = 0.3 + 0.7 * (1 - s.z) * flick;

      ctx.beginPath();
      ctx.fillStyle = `rgba(255,255,255,${alpha})`;
      ctx.arc(x < 0 ? x + w : x, y < 0 ? y + h : y, s.r * (1 + (1 - s.z)*0.6), 0, Math.PI*2);
      ctx.fill();
    }

    // subtle moving streaks (meteors) occasionally
    if (Math.random() < 0.01) {
      createMeteor();
    }

    updateMeteors(dt);
    requestAnimationFrame(draw);
  }

  // optional meteors
  const meteors = [];
  function createMeteor(){
    meteors.push({
      x: Math.random()*w,
      y: -20,
      vx: -2 - Math.random()*6,
      vy: 4 + Math.random()*6,
      len: 80 + Math.random()*140,
      life: 0
    });
  }
  function updateMeteors(dt){
    for (let i=meteors.length-1;i>=0;i--){
      const m = meteors[i];
      m.x += m.vx * (dt/16);
      m.y += m.vy * (dt/16);
      m.life += dt;
      ctx.beginPath();
      const grad = ctx.createLinearGradient(m.x, m.y, m.x - m.vx*2, m.y - m.vy*2);
      grad.addColorStop(0, 'rgba(255,255,255,0.95)');
      grad.addColorStop(1, 'rgba(255,255,255,0)');
      ctx.strokeStyle = grad;
      ctx.lineWidth = 1.5;
      ctx.moveTo(m.x, m.y);
      ctx.lineTo(m.x - m.vx * (m.len/20), m.y - m.vy * (m.len/20));
      ctx.stroke();

      if (m.x < -100 || m.y > h + 100 || m.life > 2500) meteors.splice(i,1);
    }
  }

  // mouse parallax
  window.addEventListener('mousemove', (e) => {
    const nx = (e.clientX / w - 0.5) * 2; // -1..1
    const ny = (e.clientY / h - 0.5) * 2;
    // subtle follow
    cx += (nx * 30 - cx) * 0.06;
    cy += (ny * 30 - cy) * 0.06;
  });

  // touch support
  window.addEventListener('touchmove', (e) => {
    if (e.touches && e.touches[0]) {
      const t = e.touches[0];
      const nx = (t.clientX / w - 0.5) * 2;
      const ny = (t.clientY / h - 0.5) * 2;
      cx += (nx * 30 - cx) * 0.08;
      cy += (ny * 30 - cy) * 0.08;
    }
  }, {passive:true});

  // visibility: pause when not visible to save battery
  let running = true;
  document.addEventListener('visibilitychange', () => {
    running = !document.hidden;
    if (running) { last = performance.now(); requestAnimationFrame(draw); }
  });

  // init
  window.addEventListener('resize', () => { resize(); });
  resize();
  requestAnimationFrame(draw);
})();
</script>
</body>
</html>

        body {
            margin: 0;
            padding: 0;
            font-family: 'Montserrat', sans-serif;
            background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
            color: #fff;
            text-align: center;
            overflow-x: hidden;
        }

        .overlay {
            background-color: rgba(0, 0, 0, 0.6);
            width: 100%;
            min-height: 100vh;
            padding: 60px 20px;
        }

        h1 {
            font-size: 50px;
            margin-bottom: 50px;
            font-weight: 700;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.7);
        }

        .cards {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 35px;
        }

        .card {
            background: rgba(255, 255, 255, 0.15);
            padding: 30px;
            width: 330px;
            border-radius: 18px;
            backdrop-filter: blur(12px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-12px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.7);
        }

        .card h2 {
            font-size: 26px;
            margin-bottom: 15px;
            color: #fff;
        }

        .card p {
            font-size: 16px;
            margin-bottom: 25px;
            color: #f0f0f0;
        }

        .btn {
            display: inline-block;
            padding: 15px 26px;
            background-color: #1B3FFF;
            color: white;
            text-decoration: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            transition: background 0.3s ease;
        }

        .btn:hover {
            background-color: #e64a19;
        }

        .section-text {
            margin-top: 50px;
            font-size: 22px;
            font-weight: 500;
            text-shadow: 1px 1px 5px rgba(0,0,0,0.6);
        }

        .premium-card {
            margin: 45px auto;
            width: 350px;
            background: rgba(255, 255, 255, 0.18);
            backdrop-filter: blur(14px);
            padding: 28px;
            border-radius: 20px;
            box-shadow: 0 12px 35px rgba(0,0,0,0.7);
            transition: transform 0.3s ease;
        }

        .premium-card:hover {
            transform: translateY(-10px);
        }

        .premium-card h3 {
            margin-bottom: 15px;
            font-size: 26px;
        }

        .premium-card p {
            margin-bottom: 22px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="overlay">

        <h1>Xmoney – The Key to Your Business Success</h1>

        <div class="cards">
            <!-- Card 1 -->
            <div class="card">
                <h2>2 Business Logos – $5</h2>
                <p>Get high-quality, professional logos for your brand.</p>
                <a class="btn" href="https://whop.com/checkout/plan_Bg7KX3vyIVGjk">BUY NOW</a>
            </div>

            <!-- Card 2 -->
            <div class="card">
                <h2>10 Business Growth Ideas – $10</h2>
                <p>Boost your business with creative and actionable strategies.</p>
                <a class="btn" href="https://whop.com/checkout/plan_w3oZUMd5R30D1">BUY NOW</a>
            </div>

            <!-- Card 3 -->
            <div class="card">
                <h2>1 Professional 30s Video – $10</h2>
                <p>Create a compelling video that attracts more clients.</p>
                <a class="btn" href="https://whop.com/checkout/plan_HglKg8iMbKz5I">BUY NOW</a>
            </div>
        </div>

        
        <div class="premium-card">
            <h3>Join the Premium Xmoney Membership</h3>
            <p>Price: $19.99</p>
            <a class="btn" href="https://whop.com/checkout/plan_HbwK4HOO0PteK">PAY NOW</a>
        </div>

       
