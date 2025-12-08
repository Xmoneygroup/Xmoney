
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>XMONEY — 3D Business Landing</title>

<!-- Three.js + GSAP -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r152/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

<style>
  :root{
    --accent:#06b6d4;
    --buy-red:#dc2626;
    --buy-green:#16a34a;
  }

  body,html{
    margin:0;
    padding:0;
    height:100%;
    overflow-x:hidden;
    font-family:Inter, sans-serif;
    background:#020617;
    color:white;
  }

  canvas#gl{
    position:fixed;
    inset:0;
    width:100%;
    height:100%;
    z-index:0;
  }

  header{
    position:relative;
    z-index:10;
    padding:30px;
    text-align:center;
  }

  .hero-title{
    font-size:80px;
    font-weight:900;
    letter-spacing:10px;
    color:white;
    margin-top:20px;
    z-index:10;
    position:relative;
  }

  /* CARDS SECTION */
  .cards-area{
    position:relative;
    z-index:10;
    max-width:1200px;
    margin:120px auto;
    padding:20px;
  }

  .cards{
    display:flex;
    gap:24px;
    justify-content:center;
    flex-nowwrap;
  }

  .card{
    width:330px;
    padding:22px;
    border-radius:20px;
    background:rgba(255,255,255,0.05);
    border:1px solid rgba(255,255,255,0.1);
    backdrop-filter:blur(8px);
    box-shadow:0 10px 40px rgba(0,0,0,0.4);
    transition:0.3s;
  }

  .card:hover{
    transform:translateY(-10px) scale(1.03);
    box-shadow:0 20px 60px rgba(0,255,180,0.2);
  }

  .card h3{
    font-size:22px;
    margin-bottom:12px;
  }

  .price{
    font-size:22px;
    font-weight:800;
    margin-top:6px;
  }

  .buy-btn{
    display:inline-block;
    margin-top:14px;
    padding:12px 18px;
    background:var(--buy-red);
    color:white;
    font-weight:700;
    border-radius:10px;
    text-decoration:none;
    transition:0.25s;
  }

  .buy-btn:hover{
    background:var(--buy-green);
    transform:translateY(-3px);
  }
</style>
</head>

<body>
<canvas id="gl"></canvas>

<header>
  <div class="hero-title">XMONEY</div>
</header>

<section class="cards-area">
  <div class="cards">

    <!-- CARD 1 -->
    <div class="card">
      <h3>2 Logo Për Biznesin Tuaj</h3>
      <p>Krijojmë dy logo profesionale me cilësi të lartë.</p>
      <div class="price">$5</div>
      <a class="buy-btn" target="_blank" href="https://whop.com/xmoney-1/xmoney-1c/">BUY NOW</a>
    </div>

    <!-- CARD 2 -->
    <div class="card">
      <h3>10 Ide Për Biznesin Tuaj</h3>
      <p>Marr praktikisht 10 ide të sakta dhe të gatshme për nisje.</p>
      <div class="price">$10</div>
      <a class="buy-btn" target="_blank" href="https://whop.com/xmoney-1/xmoney-7e/">BUY NOW</a>
    </div>

    <!-- CARD 3 -->
    <div class="card">
      <h3>1 Video Editim Pro</h3>
      <p>Kualitet maksimal + klient të pafund për biznesin tuaj.</p>
      <div class="price">$10</div>
      <a class="buy-btn" target="_blank" href="https://whop.com/xmoney-1/xmoney-b1/">BUY NOW</a>
    </div>

  </div>
</section>

<!-- ===========================
     THREE.JS 3D BACKGROUND
=========================== -->
<script>
(() => {
  const canvas = document.getElementById("gl");
  const renderer = new THREE.WebGLRenderer({
    canvas,
    antialias:true,
    alpha:true
  });

  const DPR = Math.min(window.devicePixelRatio, 1.5);
  renderer.setPixelRatio(DPR);
  renderer.setSize(innerWidth, innerHeight);

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(40, innerWidth/innerHeight, 0.1, 1000);
  camera.position.set(0,0,5);

  const light = new THREE.DirectionalLight(0xffffff,1);
  light.position.set(5,5,5);
  scene.add(light);
  scene.add(new THREE.AmbientLight(0x66ffff,0.4));

  // 3D Object (Icosahedron)
  const geo = new THREE.IcosahedronGeometry(1.3,30);
  const mat = new THREE.MeshStandardMaterial({
    color:0x06b6d4,
    metalness:0.8,
    roughness:0.2
  });

  const mesh = new THREE.Mesh(geo,mat);
  mesh.position.y = 0.6;
  scene.add(mesh);

  // Particles
  const particles = new THREE.BufferGeometry();
  const count = 1800;
  const pos = new Float32Array(count*3);

  for(let i=0;i<count;i++){
    pos[i*3] = (Math.random()*2-1)*7;
    pos[i*3+1] = (Math.random()*2-1)*4;
    pos[i*3+2] = (Math.random()*2-1)*7;
  }

  particles.setAttribute("position", new THREE.BufferAttribute(pos,3));

  const particleMat = new THREE.PointsMaterial({
    size:0.045,
    color:0x00fff5,
    transparent:true,
    opacity:0.7
  });

  const particleSystem = new THREE.Points(particles, particleMat);
  scene.add(particleSystem);

  const clock = new THREE.Clock();
  function animate(){
    const t = clock.getElapsedTime();

    mesh.rotation.y += 0.008;
    mesh.rotation.x = Math.sin(t*0.6)*0.2;

    particleSystem.rotation.y = t*0.04;

    renderer.render(scene,camera);
    requestAnimationFrame(animate);
  }
  animate();

  window.addEventListener("resize",()=>{
    renderer.setSize(innerWidth,innerHeight);
    camera.aspect = innerWidth/innerHeight;
    camera.updateProjectionMatrix();
  });
})();
</script>

</body>
</html>
