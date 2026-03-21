<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xmoney | Private Wealth Group</title>
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Montserrat:wght@300;400;600;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #d4af37;
            --cyan: #00f2ff;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #000; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

        canvas { position: fixed; top: 0; left: 0; z-index: 0; pointer-events: none; }

        /* --- FAKE MARKET TICKER --- */
        .ticker-wrap {
            position: fixed;
            top: 0;
            width: 100%;
            overflow: hidden;
            height: 35px;
            background: rgba(0, 0, 0, 0.9);
            border-bottom: 1px solid var(--border);
            z-index: 999;
            display: flex;
            align-items: center;
        }

        .ticker {
            display: flex;
            white-space: nowrap;
            animation: ticker 30s linear infinite;
        }

        .ticker-item {
            padding: 0 30px;
            font-size: 10px;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: 600;
        }

        .up { color: #00ff88; }
        .down { color: #ff3e3e; }

        @keyframes ticker {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* --- LIVE STATUS BADGE --- */
        .status-container {
            position: absolute;
            top: 60px;
            display: flex;
            gap: 20px;
            animation: fadeInUp 1s forwards;
        }

        .status-pill {
            background: rgba(255,255,255,0.05);
            border: 1px solid var(--border);
            padding: 6px 15px;
            border-radius: 50px;
            font-size: 9px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .dot { width: 6px; height: 6px; background: #00ff88; border-radius: 50%; box-shadow: 0 0 10px #00ff88; animation: pulse 1.5s infinite; }

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 100px 20px;
        }

        .title-wrapper { perspective: 1000px; margin-bottom: 30px; text-align: center; }
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(50px, 12vw, 150px);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -2px;
            background: linear-gradient(to bottom, #fff 40%, #444 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: titleEntrance 1.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .manifesto-container { max-width: 750px; text-align: center; margin-bottom: 50px; }
        .manifesto-text {
            font-size: 16px;
            line-height: 1.6;
            color: rgba(255,255,255,0.6);
            margin-bottom: 24px;
            font-weight: 300;
            letter-spacing: 1px;
            opacity: 0;
            animation: textReveal 1.2s forwards;
        }

        .highlight-cyan { color: var(--cyan); font-weight: 600; }

        .vip-card {
            background: rgba(5, 5, 5, 0.9);
            border: 1px solid var(--border);
            padding: 40px;
            width: 100%;
            max-width: 450px;
            border-radius: 20px;
            backdrop-filter: blur(20px);
            opacity: 0;
            transform: translateY(40px);
            animation: cardEntrance 1.5s forwards 0.8s;
            box-shadow: 0 50px 100px rgba(0,0,0,0.9);
            position: relative;
        }

        .verified-badge {
            position: absolute;
            top: -15px;
            right: 20px;
            background: var(--cyan);
            color: black;
            font-size: 9px;
            font-weight: 900;
            padding: 5px 12px;
            border-radius: 4px;
            text-transform: uppercase;
        }

        .features-list { list-style: none; margin-bottom: 30px; }
        .features-list li {
            padding: 15px 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            justify-content: space-between;
        }

        .join-btn {
            width: 100%;
            padding: 20px;
            background: white;
            color: black;
            border: none;
            border-radius: 10px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            text-decoration: none;
            display: block;
            text-align: center;
            transition: 0.3s;
        }

        .join-btn:hover { background: var(--cyan); box-shadow: 0 0 30px rgba(0, 242, 255, 0.4); }

        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }
        @keyframes textReveal { to { opacity: 1; transform: translateY(0); } }
        @keyframes cardEntrance { to { opacity: 1; transform: translateY(0); } }

        @media(max-width: 768px) { .title { font-size: 60px; } }
    </style>
</head>
<body>

<div class="ticker-wrap">
    <div class="ticker">
        <span class="ticker-item">BTC/USD <span class="up">$64,231.12 (+2.4%)</span></span>
        <span class="ticker-item">ETH/USD <span class="up">$3,452.10 (+1.8%)</span></span>
        <span class="ticker-item">XAU/USD <span class="down">$2,341.05 (-0.4%)</span></span>
        <span class="ticker-item">EUR/USD <span class="up">1.0842 (+0.1%)</span></span>
        <span class="ticker-item">BTC/USD <span class="up">$64,231.12 (+2.4%)</span></span>
    </div>
</div>

<canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="status-container">
        <div class="status-pill"><div class="dot"></div> PROTOCOL: LIVE</div>
        <div class="status-pill">X-ACCESS: GRANTED</div>
    </div>

    <div class="title-wrapper">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text" style="animation-delay: 0.4s">
            The market has <span class="highlight-cyan">zero mercy</span>. Join the circle that controls the outcome.
        </p>
        <p class="manifesto-text" style="animation-delay: 0.6s">
            Access the <span class="highlight-cyan">VIP Terminal</span>. Real-time data, institutional strategy.
        </p>
    </div>

    <div class="vip-card">
        <div class="verified-badge">Elite Membership</div>
        <ul class="features-list">
            <li><span>Daily Signals</span> <span class="highlight-cyan">3+ ALERTS</span></li>
            <li><span>Success Rate</span> <span class="highlight-cyan">60% VERIFIED</span></li>
            <li><span>Encryption</span> <span class="highlight-cyan">AES-256</span></li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Instant Access</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let w, h;
    let frame = 0;

    function resize() {
        w = canvas.width = window.innerWidth;
        h = canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resize);
    resize();

    function drawHex(x, y, size, color, alpha) {
        ctx.beginPath();
        for (let i = 0; i < 6; i++) {
            ctx.lineTo(x + size * Math.cos(i * Math.PI / 3), y + size * Math.sin(i * Math.PI / 3));
        }
        ctx.closePath();
        ctx.strokeStyle = `rgba(${color}, ${alpha})`;
        ctx.lineWidth = 1;
        ctx.stroke();
    }

    function animate() {
        frame++;
        ctx.fillStyle = "black";
        ctx.fillRect(0, 0, w, h);

        const centerX = w / 2;
        const centerY = h / 2;
        const count = 25;

        for (let i = 0; i < count; i++) {
            // Perspective logic: Rings that scale up as they move toward the screen
            let z = (i * 80 + frame * 3) % (count * 80);
            let size = z * 1.5;
            let alpha = 1 - (z / (count * 80));
            let color = i % 2 === 0 ? "0, 242, 255" : "212, 175, 55";

            ctx.save();
            ctx.translate(centerX, centerY);
            ctx.rotate(z * 0.001); // Slight spin
            drawHex(0, 0, size, color, alpha * 0.5);
            ctx.restore();
        }

        // Random Digital "Glitches" (Horizontal Light Strips)
        if (frame % 10 === 0) {
            ctx.fillStyle = `rgba(0, 242, 255, ${Math.random() * 0.1})`;
            ctx.fillRect(0, Math.random() * h, w, 2);
        }

        requestAnimationFrame(animate);
    }

    function joinVIP() { document.querySelector('.vip-card').style.transform = "scale(0.98)"; }
    animate();
</script>

</body>
</html>
