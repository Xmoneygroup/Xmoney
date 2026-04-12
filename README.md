<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Galaxy Premium 3D</title>

  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
      font-family: Arial, sans-serif;
      color: white;
    }

    canvas {
      display: block;
    }

    .overlay {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
    }

    h1 {
      font-size: 5rem;
      letter-spacing: 4px;
      background: linear-gradient(90deg, #fff, #aaa, #fff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    p {
      opacity: 0.6;
      margin-top: 10px;
    }

    .btn {
      margin-top: 30px;
      padding: 12px 30px;
      border: 1px solid rgba(255,255,255,0.3);
      background: transparent;
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }

    .btn:hover {
      background: white;
      color: black;
    }
  </style>
</head>
<body>

<div class="overlay">
  <h1>DOMAIN FOR SALE</h1>
  <p>Premium digital asset</p>
  <button class="btn">Contact</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>

<script>
  const scene = new THREE.Scene();

  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  );

  const renderer = new THREE.WebGLRenderer({ antialias: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.body.appendChild(renderer.domElement);

  // ⭐ Create stars
  const starGeometry = new THREE.BufferGeometry();
  const starCount = 8000;

  const positions = new Float32Array(starCount * 3);

  for (let i = 0; i < starCount * 3; i++) {
    positions[i] = (Math.random() - 0.5) * 1000;
  }

  starGeometry.setAttribute(
    'position',
    new THREE.BufferAttribute(positions, 3)
  );

  const starMaterial = new THREE.PointsMaterial({
    color: 0xffffff,
    size: 1
  });

  const stars = new THREE.Points(starGeometry, starMaterial);
  scene.add(stars);

  camera.position.z = 5;

  // 🎥 Mouse movement effect
  document.addEventListener("mousemove", (event) => {
    const x = (event.clientX / window.innerWidth - 0.5) * 2;
    const y = (event.clientY / window.innerHeight - 0.5) * 2;

    camera.position.x = x * 5;
    camera.position.y = -y * 5;
  });

  // 🔄 Animation loop
  function animate() {
    requestAnimationFrame(animate);

    stars.rotation.y += 0.0005;
    stars.rotation.x += 0.0002;

    renderer.render(scene, camera);
  }

  animate();

  // 📱 Responsive
  window.addEventListener("resize", () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
</script>

</body>
</html>
