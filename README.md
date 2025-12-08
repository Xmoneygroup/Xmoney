<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XMONEY — Premium Services</title>

<style>
  body, html {
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    color: white;
    height: 100%;
    overflow-x: hidden;
    background: #000;
  }

  header {
    text-align: center;
    padding-top: 70px;
    position: relative;
    z-index: 10;
  }

  header h1 {
    font-size: 70px;
    letter-spacing: 8px;
    font-weight: 900;
    color: #00ff95;
    text-shadow: 0 0 20px #00ff95;
  }

  .cards-wrapper {
    max-width: 1200px;
    margin: 120px auto;
    padding: 20px;
    position: relative;
    z-index: 10;
  }

  .cards {
    display: flex;
    gap: 30px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .card {
    width: 330px;
    padding: 25px;
    border-radius: 18px;
    background: rgba(0, 0, 0, 0.45);
    border: 1px solid rgba(0,255,120,0.25);
    backdrop-filter: blur(12px);
    box-shadow: 0 0 25px rgba(0,255,130,0.25);
    transition: 0.3s;
  }

  .card:hover {
    transform: translateY(-10px) scale(1.03);
    box-shadow: 0 0 35px rgba(0,255,140,0.55);
  }

  .card h3 {
    font-size: 22px;
    color: #00ff95;
    text-shadow: 0 0 10px #00ff95;
  }

  .price {
    margin-top: 8px;
    font-size: 20px;
    font-weight: 700;
  }

  .buy-btn {
    display: inline-block;
    margin-top: 18px;
    padding: 12px 20px;
    background: #00ff95;
    color: black;
    font-weight: 700;
    text-decoration: none;
    border-radius: 10px;
    transition: 0.25s;
  }

  .buy-btn:hover {
    background: white;
    transform: translateY(-4px);
  }

  footer {
    text-align: center;
    padding: 40px 20px;
    font-size: 18px;
    color: #00ff95;
    text-shadow: 0 0 10px #00ff95;
    position: relative;
    z-index: 10;
  }

  /* Fullscreen canvas */
  canvas#bgCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    display: block;
  }
</style>
</head>

<body>

<canvas id="bgCanvas"></canvas>

<header>
  <h1>XMONEY</h1>
</header>

<section class="cards-wrapper">
  <div class="cards">
    <div class="card">
      <h3>2 Professional Business Logos</h3>
      <p>Get two unique, modern, high-quality business logo designs tailored to your brand.</p>
      <div class="price">$5</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
      <h3>10 Business Ideas Pack</h3>
      <p>Receive ten powerful, profitable business ideas ready to launch immediately.</p>
      <div class="price">$10</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
      <h3>1 Premium Video Edit</h3>
      <p>A high-quality video edit designed to attract clients and boost your brand presence.</p>
      <div class="price">$10</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank">BUY NOW</a>
    </div>
  </div>
</section>

<footer>
  XMONEY — Empowering Businesses Globally
</footer>

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r152/three.min.js"></script>
<script>
  const canvas = document.getElementById('bgCanvas');
  const renderer = new THREE.WebGLRenderer({canvas, antialias:true});
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
  camera.position.z = 5;

  const ambientLight = new THREE.AmbientLight(0x00ff95, 0.5);
  scene.add(ambientLight);

  const directionalLight = new THREE.DirectionalLight(0x00ff95, 1);
  directionalLight.position.set(5,5,5);
  scene.add(directionalLight);

  // Extreme moving particle field
  const particles = new THREE.BufferGeometry();
  const particleCount = 5000;
  const positions = new Float32Array(particleCount*3);

  for(let i=0;i<particleCount;i++){
    positions[i*3] = (Math.random()*2 -1) * 25;
    positions[i*3+1] = (Math.random()*2 -1) * 15;
    positions[i*3+2] = (Math.random()*2 -1) * 25;
  }

  particles.setAttribute('position', new THREE.BufferAttribute(positions,3));

  const particleMaterial = new THREE.PointsMaterial({
    color: 0x00ff00,
    size: 0.06,
    transparent: true,
    opacity: 0.7
  });

  const particleSystem = new THREE.Points(particles, particleMaterial);
  scene.add(particleSystem);

  const clock = new THREE.Clock();

  function animate(){
    const t = clock.getElapsedTime();
    particleSystem.rotation.y = t*0.05;
    particleSystem.rotation.x = Math.sin(t*0.2)*0.1;
    renderer.render(scene, camera);
    requestAnimationFrame(animate);
  }
  animate();

  window.addEventListener('resize', ()=>{
    renderer.setSize(window.innerWidth, window.innerHeight);
    camera.aspect = window.innerWidth/window.innerHeight;
    camera.updateProjectionMatrix();
  });
</script>

</body>
</html>
