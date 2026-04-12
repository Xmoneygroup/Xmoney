<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Elite Domain</title>

<style>
body {
  margin: 0;
  overflow: hidden;
  background: black;
  font-family: -apple-system, BlinkMacSystemFont, sans-serif;
  color: white;
}

/* Glass Premium Panel */
.panel {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 50px 70px;
  border-radius: 25px;
  backdrop-filter: blur(25px);
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.1);
  text-align: center;
}

h1 {
  font-size: 4.5rem;
  letter-spacing: 4px;
}

p {
  opacity: 0.6;
}

.price {
  margin-top: 15px;
  font-size: 1.2rem;
  color: #00ccff;
}

button {
  margin-top: 25px;
  padding: 14px 35px;
  border-radius: 40px;
  border: none;
  font-size: 1rem;
  background: linear-gradient(90deg, #00ccff, #6600ff);
  color: white;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  transform: scale(1.1);
  box-shadow: 0 0 20px rgba(0,200,255,0.7);
}
</style>
</head>

<body>

<div class="panel">
  <h1>YOURDOMAIN.COM</h1>
  <p>Premium digital asset</p>
  <div class="price">$25,000</div>
  <button>Acquire Now</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>

<script>
const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  3000
);

const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 🌌 Galaxy + Black Hole
const particles = 20000;
const geometry = new THREE.BufferGeometry();
const positions = new Float32Array(particles * 3);

for (let i = 0; i < particles; i++) {
  const i3 = i * 3;

  const radius = Math.random() * 800;
  const angle = radius * 0.08;

  positions[i3] = Math.cos(angle) * radius;
  positions[i3 + 1] = (Math.random() - 0.5) * 80;
  positions[i3 + 2] = Math.sin(angle) * radius;
}

geometry.setAttribute("position", new THREE.BufferAttribute(positions, 3));

const material = new THREE.PointsMaterial({
  size: 1.2,
  color: 0xffffff
});

const galaxy = new THREE.Points(geometry, material);
scene.add(galaxy);

// 🕳️ Black hole (center sphere)
const holeGeometry = new THREE.SphereGeometry(20, 32, 32);
const holeMaterial = new THREE.MeshBasicMaterial({ color: 0x000000 });
const blackHole = new THREE.Mesh(holeGeometry, holeMaterial);
scene.add(blackHole);

camera.position.z = 300;

// 🖱️ Mouse depth
let mouseX = 0;
let mouseY = 0;

document.addEventListener("mousemove", (e) => {
  mouseX = (e.clientX - window.innerWidth / 2) * 0.0015;
  mouseY = (e.clientY - window.innerHeight / 2) * 0.0015;
});

// 🎬 Animation
function animate() {
  requestAnimationFrame(animate);

  galaxy.rotation.y += 0.001;
  galaxy.rotation.x += 0.0003;

  // camera cinematic movement
  camera.position.x += (mouseX * 80 - camera.position.x) * 0.04;
  camera.position.y += (-mouseY * 80 - camera.position.y) * 0.04;

  // subtle zoom breathing
  camera.position.z = 300 + Math.sin(Date.now() * 0.0005) * 20;

  camera.lookAt(scene.position);

  renderer.render(scene, camera);
}

animate();

// 📱 Resize
window.addEventListener("resize", () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
</script>

</body>
</html>
