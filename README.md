<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XMONEY</title>

<style>
/* ---------- GENERAL STYLES ---------- */
body {
    margin: 0;
    font-family: Arial, sans-serif;
    color: white;
    background: #000;
    overflow-x: hidden;
}

/* ---------- MOVING BACKGROUND ---------- */
.bg {
    position: fixed;
    top: 0; left: 0;
    width: 200%;
    height: 100%;
    background: linear-gradient(120deg, #0e0f29, #001f1f, #0a1a43);
    animation: moveBg 25s linear infinite;
    z-index: -10;
}

@keyframes moveBg {
    0% { transform: translateX(0); }
    50% { transform: translateX(-40%); }
    100% { transform: translateX(0); }
}

/* ---------- LOGO ---------- */
.logo {
    text-align: center;
    font-size: 70px;
    font-weight: 100;
    letter-spacing: 5px;
    margin-top: 70px;
    animation: fadeIn 1.4s ease forwards;
}

@keyframes fadeIn {
    0% { opacity: 0; transform: translateY(-20px); }
    100% { opacity: 1; transform: translateY(0); }
}

/* ---------- CARDS ---------- */
.cards {
    display: flex;
    justify-content: center;
    gap: 25px;
    flex-wrap: wrap;
    margin-top: 50px;
    padding: 20px;
}

.card {
    width: 300px;
    background: rgba(255,255,255,0.08);
    padding: 25px;
    border-radius: 15px;
    text-align: center;
    backdrop-filter: blur(5px);
    border: 1px solid rgba(255,255,255,0.15);
    transition: 0.3s;
}

.card:hover {
    transform: scale(1.05);
    box-shadow: 0 0 20px rgba(0,255,100,0.3);
}

/* ---------- BUY BUTTON ---------- */
.buy-btn {
    display: inline-block;
    margin-top: 20px;
    padding: 12px 20px;
    background: red;
    color: white;
    text-decoration: none;
    font-size: 17px;
    border-radius: 10px;
    transition: 0.3s;
}

.buy-btn:hover {
    background: #00cc44;
}

/* ---------- FOOTER ---------- */
footer {
    text-align: center;
    padding: 30px;
    color: #ccc;
    margin-top: 40px;
}
</style>
</head>

<body>

<div class="bg"></div>

<!-- LOGO -->
<h1 class="logo">XMONEY</h1>

<!-- CARDS -->
<div class="cards">

    <!-- CARD 1 -->
    <div class="card">
        <h2>2 Logos for Your Business</h2>
        <p style="opacity: 0.8;">Professional and clean logo designs.</p>
        <p><strong>Price: $5</strong></p>
        <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank">BUY NOW</a>
    </div>

    <!-- CARD 2 -->
    <div class="card">
        <h2>10 Business Ideas</h2>
        <p style="opacity: 0.8;">Realistic, profitable, ready-to-start ideas.</p>
        <p><strong>Price: $10</strong></p>
        <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank">BUY NOW</a>
    </div>

    <!-- CARD 3 -->
    <div class="card">
        <h2>1 Video Edit</h2>
        <p style="opacity: 0.8;">High quality editing + unlimited clients.</p>
        <p><strong>Price: $10</strong></p>
        <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank">BUY NOW</a>
    </div>

</div>

<footer>
    © 2025 XMONEY — Helping small businesses grow.
</footer>

</body>
</html>
