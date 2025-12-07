<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XMONEY</title>

<style>
    body {
        margin: 0;
        font-family: Arial, sans-serif;
        background: #000;
        color: white;
        overflow-x: hidden;
    }

    /* 3D BACKGROUND (Parallax Layers) */
    .layer {
        position: fixed;
        width: 200%;
        height: 200%;
        top: -50%;
        left: -50%;
        z-index: -5;
        pointer-events: none;
    }

    .layer img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.12;
        animation: float 18s infinite alternate ease-in-out;
    }

    @keyframes float {
        0% { transform: scale(1) translate(0,0); }
        100% { transform: scale(1.2) translate(40px, 40px); }
    }

    /* LOGO */
    h1 {
        text-align: center;
        margin-top: 90px;
        font-size: 75px;
        font-weight: 100;
        letter-spacing: 8px;
        opacity: 0;
        transform: translateY(-40px);
        animation: fadeIn 1.5s forwards ease-out;
    }

    @keyframes fadeIn {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* CARDS */
    .cards {
        margin-top: 70px;
        display: flex;
        justify-content: center;
        gap: 30px;
        flex-wrap: wrap;
        padding: 20px;
    }

    .card {
        background: rgba(255,255,255,0.08);
        padding: 25px;
        width: 300px;
        border-radius: 15px;
        text-align: center;
        border: 1px solid rgba(255,255,255,0.1);
        backdrop-filter: blur(5px);
        transition: 0.5s;
        transform-style: preserve-3d;
    }

    .card:hover {
        transform: translateY(-10px) rotateX(8deg) rotateY(8deg);
        box-shadow: 0 0 25px rgba(0,255,100,0.4);
    }

    /* BUY BUTTON */
    .buy {
        display: inline-block;
        margin-top: 18px;
        padding: 12px 20px;
        background: red;
        color: white;
        font-size: 18px;
        border-radius: 10px;
        text-decoration: none;
        transition: 0.3s;
    }

    .buy:hover {
        background: #00cc44;
    }

    footer {
        text-align: center;
        margin-top: 80px;
        padding: 40px;
        color: #bbb;
    }
</style>
</head>
<body>

<!-- 3D LAYERS (BUSINESS-THEMED) -->
<div class="layer"><img src="https://images.unsplash.com/photo-1520607162513-77705c0f0d4a" /></div>
<div class="layer"><img src="https://images.unsplash.com/photo-1556761175-4b46a572b786" /></div>
<div class="layer"><img src="https://images.unsplash.com/photo-1521791136064-7986c2920216" /></div>

<!-- LOGO -->
<h1>XMONEY</h1>

<!-- CARDS -->
<div class="cards">

    <div class="card">
        <h2>2 Logos for Your Business</h2>
        <p>Clean, professional, premium design.</p>
        <p><strong>$5</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
        <h2>10 Business Ideas</h2>
        <p>Profitable and realistic ideas to start instantly.</p>
        <p><strong>$10</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank">BUY NOW</a>
    </div>

    <div class="card">
        <h2>1 Business Video Edit</h2>
        <p>High-quality edit + unlimited clients.</p>
        <p><strong>$10</strong></p>
        <a class="buy" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank">BUY NOW</a>
    </div>

</div>

<footer>
    © 2025 XMONEY — Helping small businesses grow.
</footer>

<!-- PARALLAX MOUSE 3D MOVEMENT -->
<script>
document.addEventListener("mousemove", (e) => {
    const layers = document.querySelectorAll(".layer");
    layers.forEach((layer, index) => {
        let speed = (index + 1) * 0.015;
        let x = (window.innerWidth / 2 - e.clientX) * speed;
        let y = (window.innerHeight / 2 - e.clientY) * speed;
        layer.style.transform = `translate(${x}px, ${y}px)`;
    });
});
</script>

</body>
</html>
