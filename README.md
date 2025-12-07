<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XMONEY - NEXT LEVEL 3D</title>

<!-- THREE.JS CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<!-- GSAP + ScrollTrigger -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<style>
    body {
        margin: 0;
        background: black;
        font-family: Arial, sans-serif;
        overflow-x: hidden;
        color: white;
    }

    /* FULLSCREEN CANVAS */
    #canvas3d {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        z-index: -10;
    }

    /* LOGO TEXT */
    .logo {
        font-size: 90px;
        font-weight: 100;
        letter-spacing: 10px;
        text-align: center;
        margin-top: 120px;
        opacity: 0;
    }

    /* SUBTITLE */
    .subtitle {
        text-align: center;
        margin-top: 10px;
        font-size: 22px;
        opacity: 0;
    }

    /* CARDS */
    .cards {
        margin-top: 120px;
        display: flex;
        justify-content: center;
        gap: 40px;
        flex-wrap: wrap;
        padding: 20px;
    }

    .card {
        background: rgba(255,255,255,0.08);
        padding: 25px;
        width: 330px;
        border-radius: 20px;
        text-align: center;
        backdrop-filter: blur(6px);
        border: 1px solid rgba(255,255,255,0.15);
        transition: transform .4s ease;
    }

    .card:hover {
        transform: translateY(-15px) scale(1.05);
        box-shadow: 0 0 30px rgba(0,255,100,0.4);
    }

    .buy {
        display: inline-block;
        margin-top: 15px;
        padding: 12px 20px;
        background: red;
        border-radius: 10px;
        color: white;
        font-size: 18px;
        text-decoration: none;
        transition: .3s;
    }

    .buy:hover {
        background: #00cc44;
    }

    footer {
        text-align: center;
        margin-top: 100px;
        color: #aaa;
        padding-bottom: 60px;
    }
</style>
</head>
<body>

<canvas id="canvas3d"></canvas>

<h1 class="logo">XMONEY</h1>
<p class="subtitle">Helping Small Businesses Grow To Big Success</p>

<!-- CARDS -->
<div class="cards">
    <div class="card">
        <h2>2 Logos for Your Business</h2>
        <p>Premium, clean, beautiful design.</p>
        <p><strong>$5</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
        <h2>10 Business Ideas</h2>
        <p>Profitable & realistic ideas for fast growth.</p>
        <p><strong>$10</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
        <h2>1 Video Edit</h2>
        <p>High quality edit + unlimited clients.</p>
        <p><strong>$10</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank">BUY NOW</a>
    </div>
</div>

<footer>
    © 2025 XMONEY — Next Level Business Growth.
</footer>


<!-- THREE.JS 3D BACKGROUND -->
<script>
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, innerWidth/innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById("canvas3d"), alpha: true });
renderer.setSize(innerWidth, innerHeight);
camera.position.z = 5;

// CREATE 3D PARTICLE FIELD
const particles = new THREE.BufferGeometry();
const count = 2000;
const positions = new Float32Array(count * 3);

for (let i = 0; i < count * 3; i++) {
    positions[i] = (Math.random() - 0.5) * 15;
}

particles.setAttribute("position", new THREE.BufferAttribute(positions, 3));
const material = new THREE.PointsMaterial({ color: "#00ff88", size: 0.03 });
const particleMesh = new THREE.Points(particles, material);
scene.add(particleMesh);

// ANIMATION LOOP
function animate() {
    particleMesh.rotation.x += 0.0005;
    particleMesh.rotation.y += 0.001;

    renderer.render(scene, camera);
    requestAnimationFrame(animate);
}
animate();

// RESIZE FIX
addEventListener("resize", () => {
    renderer.setSize(innerWidth, innerHeight);
    camera.aspect = innerWidth / innerHeight;
    camera.updateProjectionMatrix();
});
</script>

<!-- GSAP ANIMATIONS -->
<script>
gsap.from(".logo", { y: -40, opacity: 0, duration: 1.5, ease: "power3.out" });
gsap.from(".subtitle", { y: 20, opacity: 0, duration: 1.5, delay: 0.5, ease: "power3.out" });

gsap.from(".card", {
    opacity: 0,
    y: 60,
    duration: 1.5,
    stagger: 0.2,
    ease: "power3.out",
    scrollTrigger: {
        trigger: ".cards",
        start: "top 90%"
    }
});
</script>

</body>
</html>
