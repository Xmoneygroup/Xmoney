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
    overflow: hidden;
    background: #000;
  }

  canvas#bgCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
  }

  header {
    text-align: center;
    padding-top: 60px;
    position: relative;
    z-index: 10;
  }

  header h1 {
    font-size: 80px;
    font-weight: 900;
    color: #00ff95;
    text-shadow: 0 0 20px #00ff95;
    animation: glowTitle 2s infinite alternate;
  }

  @keyframes glowTitle {
    0% { text-shadow: 0 0 15px #00ff95, 0 0 25px #00ff95; }
    100% { text-shadow: 0 0 25px #00ff95, 0 0 50px #00ff95; }
  }

  .cards-wrapper {
    max-width: 1200px;
    margin: 150px auto;
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
    border-radius: 20px;
    background: rgba(0,0,0,0.5);
    border: 1px solid rgba(0,255,150,0.3);
    backdrop-filter: blur(15px);
    box-shadow: 0 0 25px rgba(0,255,150,0.35);
    transition: 0.3s;
    cursor: pointer;
  }

  .card:hover {
    transform: translateY(-10px) scale(1.05);
    box-shadow: 0 0 40px rgba(0,255,150,0.6);
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
  // Ultra futuristic 3D particle network
  const canvas = document.getElementById('bgCanvas');
  const renderer = new THREE.WebGLRenderer({canvas, antialias:true});
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
  camera.position.z = 6;

  const ambientLight = new THREE.AmbientLight(0x00ff95, 0.5);
  scene.add(ambientLight);

  const directionalLight = new THREE.DirectionalLight(0x00ff95, 1);
  directionalLight.position.set(5,5,5);
  scene.add(directionalLight);

  // Particle system as network
  const particles = 5000;
  const positions = [];
  const velocities = [];
  const geometry = new THREE.BufferGeometry();

  for(let i=0;i<particles;i++){
    positions.push((Math.random()*2-1)*20);
    positions.push((Math.random()*2-1)*15);
    positions.push((Math.random()*2-1)*20);
    velocities.push((Math.random()-0.5)*0.002);
    velocities.push((Math.random()-0.5)*0.002);
    velocities.push((Math.random()-0.5)*0.002);
  }

  geometry.setAttribute('position', new THREE.Float32BufferAttribute(positions,3));

  const material = new THREE.PointsMaterial({
    color: 0x00ff95,
    size: 0.05,
    transparent: true,
    opacity: 0.7
  });

  const points = new THREE.Points(geometry, material);
  scene.add(points);

  // Connect lines
  const lineMaterial = new THREE.LineBasicMaterial({color:0x00ff95,opacity:0.05,transparent:true});
  const lineGeometry = new THREE.BufferGeometry();
  const linePositions = new Float32Array(particles*particles*3);
  const lineMesh = new THREE.LineSegments(lineGeometry,lineMaterial);
  scene.add(lineMesh);

  const clock = new THREE.Clock();
  function animate(){
    const t = clock.getElapsedTime();
    const positionsAttr = geometry.attributes.position.array;

    for(let i=0;i<particles;i++){
      positionsAttr[i*3]+=velocities[i*3];
      positionsAttr[i*3+1]+=velocities[i*3+1];
      positionsAttr[i*3+2]+=velocities[i*3+2];

      if(positionsAttr[i*3]>20 || positionsAttr[i*3]<-20) velocities[i*3]*=-1;
      if(positionsAttr[i*3+1]>15 || positionsAttr[i*3+1]<-15) velocities[i*3+1]*=-1;
      if(positionsAttr[i*3+2]>20 || positionsAttr[i*3+2]<-20) velocities[i*3+2]*=-1;
    }

    geometry.attributes.position.needsUpdate = true;
    points.rotation.y = t*0.02;
    renderer.render(scene,camera);
    requestAnimationFrame(animate);
  }
  animate();

  window.addEventListener('resize',()=>{
    renderer.setSize(window.innerWidth,window.innerHeight);
    camera.aspect = window.innerWidth/window.innerHeight;
    camera.updateProjectionMatrix();
  });

</script>

</body>
</html>
