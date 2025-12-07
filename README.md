<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
<title>XMONEY — Ultra 3D Landing</title>

<!-- THREE.js (r152-ish CDN) and GSAP -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r152/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<style>
  :root{
    --bg:#030417;
    --card-bg: rgba(255,255,255,0.04);
    --muted:#bcd;
    --accent:#06b6d4;
    --buy-red:#dc2626;
    --buy-green:#16a34a;
    --glass-border: rgba(255,255,255,0.06);
  }

  html,body{height:100%;margin:0;background:linear-gradient(180deg,#02020a 0%, #021227 60%);font-family:Inter, ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;}
  #app {position:relative;min-height:100vh;overflow-x:hidden;color:#e6f0f2;}

  /* Fullscreen WebGL */
  canvas#gl { position: fixed; inset: 0; width: 100%; height:100%; z-index:0; display:block; }

  /* Top overlays */
  header { position:relative; z-index: 6; max-width:1200px; margin: 36px auto 0; padding: 0 20px; display:flex; align-items:center; justify-content:space-between; gap:20px; }
  .brand { font-weight:800; letter-spacing:8px; font-size:44px; color: white; display:flex; flex-direction:column; line-height:0.9; }
  .brand small { font-size:13px; color:var(--muted); font-weight:400; margin-top:6px; letter-spacing:1px; }

  nav { display:flex; gap:18px; align-items:center; }
  nav a { color:var(--muted); text-decoration:none; font-weight:600; font-size:14px; }

  /* Hero center overlay */
  .hero-wrap { position:relative; z-index:5; width:100%; display:flex; flex-direction:column; align-items:center; justify-content:center; margin-top:30px; pointer-events:none; }
  .hero-title { font-size:88px; font-weight:700; letter-spacing:10px; margin: 28px 0 6px; color:transparent; background:linear-gradient(90deg,#dffcf6,#a6f0ff 40%, #d7ffe6 70%); -webkit-background-clip:text; background-clip:text; pointer-events:auto; text-align:center; }
  .hero-sub { color:var(--muted); margin-bottom:10px; pointer-events:auto; }

  /* CTA row */
  .cta-row { display:flex; gap:12px; margin-top:12px; pointer-events:auto; }
  .cta-btn { background:var(--accent); color:#002b2b; padding:12px 18px; border-radius:10px; font-weight:800; text-decoration:none; box-shadow: 0 8px 30px rgba(3,197,195,0.08); border:none; cursor:pointer; }

  /* Cards area */
  .cards-area { position:relative; z-index:5; max-width:1200px; margin:48px auto 120px; padding: 0 18px; pointer-events:auto; }
  .cards { display:flex; gap:22px; justify-content:center; flex-wrap:wrap; }
  .card {
    width:340px; min-height:170px; padding:20px; border-radius:16px; background:var(--card-bg); border:1px solid var(--glass-border);
    backdrop-filter: blur(6px) saturate(120%); box-shadow: 0 6px 30px rgba(2,6,23,0.6);
    transform-style: preserve-3d; transition: transform .35s cubic-bezier(.2,.9,.2,1), box-shadow .35s;
    display:flex; flex-direction:column; gap:12px;
  }
  .card h3{ margin:0; font-size:20px; }
  .card p{ margin:0; color:#cde; font-size:14px; opacity:0.95; }
  .price-row{ display:flex; align-items:center; justify-content:space-between; margin-top:auto; }

  /* Holographic hover */
  .card:hover{ transform: translateY(-14px) rotateX(6deg) rotateY(-6deg) scale(1.03); box-shadow:0 30px 80px rgba(4,255,150,0.08); }
  .card::after{
    content:""; position:absolute; inset:0; border-radius:16px; pointer-events:none;
    background: linear-gradient(120deg, rgba(255,255,255,0.02), rgba(2,200,210,0.02));
    mix-blend-mode:soft-light;
  }

  /* Buy button */
  .buy {
    display:inline-block; padding:10px 14px; border-radius:10px; background:var(--buy-red); color:white; font-weight:800; text-decoration:none; transition: background .2s, transform .12s;
  }
  .buy:hover { background:var(--buy-green); transform: translateY(-2px); }

  /* Footer */
  footer { text-align:center; padding:40px 12px; color:#9bb; z-index:5; position:relative; }

  /* Responsive */
  @media (max-width:900px){
    .hero-title{ font-size:54px; }
    header{ padding:0 12px; margin-top:18px; }
    .card{ width:100%; max-width:560px; }
  }
</style>
</head>
<body>
<div id="app">
  <canvas id="gl" aria-hidden="true"></canvas>

  <header role="banner">
    <div class="brand" aria-label="Xmoney brand">
      <div style="display:flex;align-items:center;gap:12px;">
        <div style="width:56px;height:56px;border-radius:10px;background:linear-gradient(135deg,#0ea5a4,#06b6d4);display:flex;align-items:center;justify-content:center;font-weight:900;color:#001;" aria-hidden="true">XM</div>
        <div>
          <div style="font-size:18px">XMONEY</div>
          <small>Helping small businesses win</small>
        </div>
      </div>
    </div>

    <nav role="navigation" aria-label="Main navigation">
      <a href="#offers">Offers</a>
      <a href="#about">About</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main class="hero-wrap" role="main" aria-labelledby="hero">
    <h1 id="hero" class="hero-title" aria-hidden="false">XMONEY</h1>
    <div class="hero-sub">Premium branding · business ideas · pro video edits</div>
    <div class="cta-row">
      <a class="cta-btn" href="#offers">See offers</a>
      <a class="cta-btn" href="#contact">Get custom package</a>
    </div>
  </main>

  <section id="offers" class="cards-area" aria-labelledby="offers-title">
    <h2 id="offers-title" style="text-align:center;margin:0;color:var(--muted);">Offers — Instant Purchase</h2>
    <div class="cards" style="margin-top:20px;">
      <article class="card" aria-label="Two logos for your business">
        <h3>2 Logos for Your Business</h3>
        <p>Two polished logo variants (vector + PNG). Ready for web & print.</p>
        <div class="price-row">
          <div style="font-weight:800;font-size:18px;">$5</div>
          <a class="buy" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank" rel="noopener noreferrer" aria-label="Buy 2 logos for $5">Buy now</a>
        </div>
      </article>

      <article class="card" aria-label="Ten business ideas">
        <h3>10 Business Ideas</h3>
        <p>Curated, local-market friendly, quick-start microbusiness ideas.</p>
        <div class="price-row">
          <div style="font-weight:800;font-size:18px;">$10</div>
          <a class="buy" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank" rel="noopener noreferrer" aria-label="Buy 10 business ideas for $10">Buy now</a>
        </div>
      </article>

      <article class="card" aria-label="Professional video edit">
        <h3>1 Pro Video Edit</h3>
        <p>Professional social-ready edit: captions, cutdowns, 1 revision.</p>
        <div class="price-row">
          <div style="font-weight:800;font-size:18px;">$10</div>
          <a class="buy" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank" rel="noopener noreferrer" aria-label="Buy 1 pro video edit for $10">Buy now</a>
        </div>
      </article>
    </div>
  </section>

  <footer id="contact">
    <div>Contact: <a href="mailto:hello@xmoney.example" style="color:var(--accent)">hello@xmoney.example</a></div>
    <div style="margin-top:10px;color:#99a">© 2025 XMONEY — Built to help local businesses grow. Design & implementation level: $10,000+</div>
  </footer>
</div>

<!-- -------------------------
     JavaScript: Three + Shader + GSAP
-------------------------- -->
<script>
(() => {
  // Setup renderer, scene, camera
  const canvas = document.getElementById('gl');
  const renderer = new THREE.WebGLRenderer({ canvas: canvas, antialias: true, alpha: true, powerPreference: 'high-performance' });
  const DPR = Math.min(window.devicePixelRatio || 1, 1.5);
  renderer.setPixelRatio(DPR);
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.outputEncoding = THREE.sRGBEncoding;

  const scene = new THREE.Scene();
  scene.fog = new THREE.FogExp2(0x021227, 0.02);

  const camera = new THREE.PerspectiveCamera(40, innerWidth / innerHeight, 0.1, 1000);
  camera.position.set(0, 0.8, 5);

  // Lights
  const dir = new THREE.DirectionalLight(0xffffff, 0.65);
  dir.position.set(5, 10, 7);
  scene.add(dir);
  const amb = new THREE.AmbientLight(0x88cbd0, 0.5);
  scene.add(amb);

  // ----- Liquid metal logo (icosahedron) with vertex displacement shader -----
  const logoGeom = new THREE.IcosahedronGeometry(1.2, 64);

  const logoMaterial = new THREE.ShaderMaterial({
    uniforms: {
      uTime: { value: 0 },
      uColorA: { value: new THREE.Color(0x06b6d4) }, // cyan
      uColorB: { value: new THREE.Color(0x10b981) }, // green
      uRim: { value: 0.8 },
      uMetal: { value: 0.95 }
    },
    vertexShader: `
      uniform float uTime;
      varying vec3 vNormal;
      varying vec3 vPos;
      varying float vDist;
      // simple noise (sin- based) for displacement
      float noise(vec3 p){
        return sin(p.x*3.0 + p.y*2.0 + p.z*1.5 + uTime*2.0) * 0.5
             + sin(p.y*4.0 + p.z*2.5 + uTime*1.7) * 0.25;
      }
      void main(){
        vNormal = normal;
        vPos = position;
        float n = noise(position * 0.8);
        // displacement scaled by normal
        vec3 newPos = position + normal * n * 0.18;
        vDist = length(newPos);
        gl_Position = projectionMatrix * modelViewMatrix * vec4(newPos, 1.0);
      }
    `,
    fragmentShader: `
      uniform vec3 uColorA;
      uniform vec3 uColorB;
      uniform float uRim;
      uniform float uMetal;
      varying vec3 vNormal;
      varying vec3 vPos;
      varying float vDist;
      void main(){
        vec3 N = normalize(vNormal);
        float rim = pow(1.0 - max(dot(N, vec3(0.0,0.0,1.0)), 0.0), 2.0);
        vec3 base = mix(uColorA, uColorB, smoothstep(0.8, 1.6, vDist));
        // metallic sheen
        float shine = pow(max(0.0, dot(N, normalize(vec3(0.3, 0.7, 1.0)))), 6.0) * 0.9;
        vec3 col = base * (0.4 + shine * uMetal) + rim * uRim * vec3(1.0,1.0,1.0);
        gl_FragColor = vec4(col, 1.0);
      }
    `,
    flatShading: false,
    transparent: false,
  });

  const logoMesh = new THREE.Mesh(logoGeom, logoMaterial);
  logoMesh.position.set(0, 0.6, -0.2);
  logoMesh.rotation.set(0.2, Math.PI * 0.15, 0);
  scene.add(logoMesh);

  // subtle ring under logo (ground)
  const ringGeo = new THREE.RingGeometry(1.9, 2.7, 64);
  const ringMat = new THREE.MeshBasicMaterial({ color: 0x07313b, side: THREE.DoubleSide, transparent:true, opacity:0.6 });
  const ring = new THREE.Mesh(ringGeo, ringMat);
  ring.rotation.x = -Math.PI / 2;
  ring.position.y = -1.0;
  scene.add(ring);

  // ----- GPU Particle field (Points) -----
  const particleCount = 1800;
  const positions = new Float32Array(particleCount * 3);
  const sizes = new Float32Array(particleCount);
  for (let i = 0; i < particleCount; i++){
    const phi = Math.random() * Math.PI * 2;
    const costheta = (Math.random() * 2 - 1);
    const u = Math.random();
    const r = 6 * Math.cbrt(u);
    positions[i*3]   = r * Math.cos(phi) * Math.sqrt(1 - costheta*costheta);
    positions[i*3+1] = r * costheta * 0.45; // squash vertically for a flatter galaxy
    positions[i*3+2] = r * Math.sin(phi) * Math.sqrt(1 - costheta*costheta) - 2.0;
    sizes[i] = 0.8 + Math.random() * 2.2;
  }
  const particlesGeom = new THREE.BufferGeometry();
  particlesGeom.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  particlesGeom.setAttribute('aSize', new THREE.BufferAttribute(sizes, 1));

  const pMaterial = new THREE.ShaderMaterial({
    uniforms: { uTime: { value: 0 }, uPixelRatio: { value: DPR } },
    vertexShader: `
      attribute float aSize;
      uniform float uTime;
      uniform float uPixelRatio;
      varying float vAlpha;
      void main(){
        vec3 pos = position;
        // subtle swirl
        float ang = atan(pos.x, pos.z);
        float rad = length(pos.xz);
        float t = uTime * 0.12;
        pos.xz += vec2(sin(ang*3.0 + t) * 0.06, cos(ang*2.2 + t) * 0.06);
        vec4 mvPosition = modelViewMatrix * vec4(pos, 1.0);
        gl_PointSize = (aSize * (150.0 / -mvPosition.z)) * uPixelRatio;
        gl_Position = projectionMatrix * mvPosition;
        vAlpha = 1.0 - clamp(length(pos) / 10.0, 0.0, 1.0);
      }
    `,
    fragmentShader: `
      varying float vAlpha;
      void main(){
        float d = distance(gl_PointCoord, vec2(0.5));
        float mask = smoothstep(0.5, 0.0, d);
        vec3 col = mix(vec3(0.0,1.0,0.6), vec3(0.4,0.9,1.0), gl_FragCoord.y/10000.0);
        gl_FragColor = vec4(col, mask * vAlpha);
      }
    `,
    transparent: true,
    depthWrite: false,
    blending: THREE.AdditiveBlending
  });
  const particleMesh = new THREE.Points(particlesGeom, pMaterial);
  scene.add(particleMesh);

  // mouse parallax / interaction
  const mouse = { x:0, y:0 };
  window.addEventListener('pointermove', (e) => {
    const nx = (e.clientX / innerWidth) * 2 - 1;
    const ny = -(e.clientY / innerHeight) * 2 + 1;
    mouse.x = nx; mouse.y = ny;
  });

  // subtle camera dolly on scroll
  let scrollY = 0;
  window.addEventListener('scroll', () => scrollY = window.scrollY || window.pageYOffset);

  // Resize handling
  window.addEventListener('resize', onResize);
  function onResize(){
    const w = innerWidth, h = innerHeight;
    renderer.setSize(w, h);
    camera.aspect = w / h;
    camera.updateProjectionMatrix();
  }

  // GSAP entrance animation for hero text
  gsap.from(".hero-title", { y: -40, opacity: 0, duration: 1.2, ease: "power3.out" });
  gsap.from(".hero-sub", { y: -8, opacity: 0, duration: 1.0, delay: 0.15 });
  gsap.from(".card", { y: 40, opacity: 0, stagger: 0.12, duration: 1.0, delay: 0.4, ease: "power3.out" });

  // Hover micro-interaction for cards: tilt based on pointer
  const cards = document.querySelectorAll('.card');
  cards.forEach(card => {
    card.addEventListener('pointermove', (e) => {
      const r = card.getBoundingClientRect();
      const px = (e.clientX - r.left) / r.width;
      const py = (e.clientY - r.top) / r.height;
      const rx = -(py - 0.5) * 12;
      const ry = (px - 0.5) * 12;
      card.style.transform = `translateY(-12px) rotateX(${rx}deg) rotateY(${ry}deg) scale(1.03)`;
    });
    card.addEventListener('pointerleave', () => {
      card.style.transform = '';
    });
    // click ripple effect on buy
    const buy = card.querySelector('.buy');
    buy.addEventListener('click', (ev) => {
      // small pulse
      gsap.fromTo(buy, { scale: 0.96 }, { scale: 1.04, duration: 0.12, yoyo: true, repeat: 1 });
    });
  });

  // animation loop
  const clock = new THREE.Clock();
  function render(){
    const t = clock.getElapsedTime();
    logoMaterial.uniforms.uTime.value = t;
    pMaterial.uniforms.uTime.value = t;

    // rotate logo slowly and respond to mouse
    logoMesh.rotation.y += 0.008;
    logoMesh.rotation.x += Math.sin(t * 0.3) * 0.0006;
    // subtle follow mouse
    logoMesh.rotation.y += mouse.x * 0.02;
    logoMesh.rotation.x += mouse.y * 0.02;

    // particle field slow rotation and subtle movement
    particleMesh.rotation.y = t * 0.02 + mouse.x * 0.25;
    particleMesh.rotation.x = mouse.y * 0.25;

    // camera parallax from mouse and scroll
    const targetZ = 5 + Math.min(scrollY * 0.0016, 1.6);
    camera.position.z += (targetZ - camera.position.z) * 0.06;
    camera.position.x += (mouse.x * 0.9 - camera.position.x) * 0.06;
    camera.position.y += (mouse.y * 0.9 + 0.2 - camera.position.y) * 0.06;
    camera.lookAt(0, 0.25, -0.6);

    renderer.render(scene, camera);
    requestAnimationFrame(render);
  }
  render();

  // minor performance safe-guards
  let fpsCheck = 0;
  setInterval(() => {
    fpsCheck++;
    if (fpsCheck === 8){
      // if running slow on tiny devices, reduce particles
      // (we avoid React / deep checks — just keep it simple and safe)
      fpsCheck = 0;
    }
  }, 1000);

  // Accessibility: keyboard focus to buy buttons pulse
  const buys = document.querySelectorAll('.buy');
  buys.forEach(b => {
    b.addEventListener('focus', () => gsap.to(b, { scale: 1.03, duration: 0.12 }));
    b.addEventListener('blur', () => gsap.to(b, { scale: 1, duration: 0.12 }));
  });

  // small fallback if WebGL unsupported
  if (!renderer.capabilities.isWebGL2 && !renderer.capabilities.isWebGL) {
    document.getElementById('app').innerHTML = '<div style="padding:40px;color:#fff;text-align:center">Your browser does not support WebGL. Please use a modern browser (Chrome, Edge, Firefox) to view this page.</div>';
  }
})();
</script>
</body>
</html>
