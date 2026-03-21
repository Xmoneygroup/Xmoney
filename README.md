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
            background: #020202; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

        canvas { position: fixed; top: 0; left: 0; z-index: 0; pointer-events: none; }

        /* --- MARKET TICKER --- */
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
            animation: ticker 40s linear infinite;
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

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            perspective: 2000px;
        }

        /* --- CRAZY GLITCH TITLE --- */
        .title-container {
            position: relative;
            margin-bottom: 40px;
            transform-style: preserve-3d;
            transition: transform 0.1s ease-out;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(70px, 18vw, 220px);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -10px;
            line-height: 0.8;
            position: relative;
            /* Metallic Gradient */
            background: linear-gradient(to bottom, #fff 20%, #666 50%, #eee 80%, #333 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 20px rgba(255,255,255,0.1));
            animation: mainReveal 1.5s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
            z-index: 2;
        }

        /* Glitch Layer 1 (Cyan) */
        .title::before {
            content: 'Xmoney';
            position: absolute;
            left: -3px;
            top: 0;
            width: 100%;
            height: 100%;
            background: transparent;
            -webkit-text-stroke: 1px var(--cyan);
            -webkit-text-fill-color: transparent;
            opacity: 0.4;
            z-index: -1;
            animation: glitch1 3s infinite linear alternate-reverse;
        }

        /* Glitch Layer 2 (Gold) */
        .title::after {
            content: 'Xmoney';
            position: absolute;
            left: 3px;
            top: 0;
            width: 100%;
            height: 100%;
            background: transparent;
            -webkit-text-stroke: 1px var(--gold);
            -webkit-text-fill-color: transparent;
            opacity: 0.4;
            z-index: -1;
            animation: glitch2 2.5s infinite linear alternate-reverse;
        }

        @keyframes mainReveal {
            0% { transform: scale(0.5) translateZ(-500px); opacity: 0; letter-spacing: 50px; }
            100% { transform: scale(1) translateZ(0); opacity: 1; letter-spacing: -10px; }
        }

        @keyframes glitch1 {
            0% { transform: translate(0); }
            20% { transform: translate(-4px, 2px); }
            40% { transform: translate(-4px, -2px); }
            60% { transform: translate(4px, 2px); }
            80% { transform: translate(4px, -2px); }
            100% { transform: translate(0); }
        }

        @keyframes glitch2 {
            0% { transform: translate(0); }
            25% { transform: translate(4px, -2px); }
            50% { transform: translate(-4px, 2px); }
            75% { transform: translate(4px, 2px); }
            100% { transform: translate(0); }
        }

        .manifesto-container { max-width: 800px; text-align: center; margin-bottom: 50px; }
        .manifesto-text {
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 5px;
            color: rgba(255,255,255,0.4);
            font-weight: 400;
            opacity: 0;
            animation: fadeIn 1s forwards 1.2s;
        }

        .highlight-cyan { color: var(--cyan); text-shadow: 0 0 10px var(--cyan); }

        /* --- VIP CARD --- */
        .vip-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.05) 0%, rgba(0,0,0,0.95) 100%);
            border: 1px solid var(--border);
            padding: 40px;
            width: 100%;
            max-width: 450px;
            border-radius: 30px;
            backdrop-filter: blur(40px);
            opacity: 0;
            transform: translateY(40px);
            animation: fadeIn 1.5s forwards 1.5s;
            box-shadow: 0 40px 100px rgba(0,0,0,0.9);
            transition: border 0.3s, transform 0.3s;
        }

        .vip-card:hover {
            border-color: rgba(0, 242, 255, 0.5);
            transform: translateY(-5px);
        }

        .features-list { list-style: none; margin-bottom: 30px; }
        .features-list li {
            padding: 18px 0;
            border-bottom: 1px solid rgba(255,255,255,0.03);
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: flex;
            justify-content: space-between;
        }

        .join-btn {
            width: 100%;
            padding: 24px;
            background: #fff;
            color: #000;
            border-radius: 15px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 4px;
            cursor: pointer;
            text-decoration: none;
            display: block;
            text-align: center;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .join-btn:hover {
            background: var(--cyan);
            box-shadow: 0 0 50px rgba(0, 242, 255, 0.4);
            letter-spacing: 6px;
        }

        @keyframes fadeIn { to { opacity: 1; transform: translateY(0); } }

        @media(max-width: 768px) { .title { font-size: 80px; letter-spacing: -2px; } }
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
        <span class="ticker-item">ETH/USD <span class="up">$3,452.10 (+1.8%)</span></span>
        <span class="ticker-item">XAU/USD <span class="down">$2,341.05 (-0.4%)</span></span>
        <span class="ticker-item">EUR/USD <span class="up">1.0842 (+0.1%)</span></span>
    </div>
</div>

<canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="title-container" id="title3D">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text">
            Institutional <span class="highlight-cyan">Liquidity</span> & Intelligence
        </p>
    </div>

    <div class="vip-card" id="vipCard">
        <ul class="features-list">
            <li><span>Market Signals</span> <span class="highlight-cyan">DAILY</span></li>
            <li><span>Success Rate</span> <span class="highlight-cyan">88% AVG</span></li>
            <li><span>Status</span> <span class="highlight-cyan">PRIVATE ACCESS</span></li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Enter Terminal</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let frame = 0;

    function resize() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
    window.addEventListener("resize", resize);
    resize();

    // 3D Title Movement
    const title3D = document.getElementById('title3D');
    document.addEventListener('mousemove', (e) => {
        let x = (window.innerWidth / 2 - e.pageX) / 20;
        let y = (window.innerHeight / 2 - e.pageY) / 20;
        title3D.style.transform = `rotateY(${x}deg) rotateX(${y}deg)`;
    });

    function drawBackground() {
        ctx.strokeStyle = 'rgba(0, 242, 255, 0.03)';
        const spacing = 60;
        
        // Dynamic Grid
        ctx.lineWidth = 1;
        for(let i = -10; i < 20; i++) {
            let z = (i * spacing) + (frame % spacing);
            let alpha = 1 - (z / canvas.height);
            ctx.strokeStyle = `rgba(212, 175, 55, ${alpha * 0.1})`;
            
            ctx.beginPath();
            ctx.moveTo(0, z + canvas.height/2);
            ctx.lineTo(canvas.width, z + canvas.height/2);
            ctx.stroke();
        }

        // Perspective Lines
        for(let i = -10; i < 10; i++) {
            ctx.strokeStyle = 'rgba(0, 242, 255, 0.05)';
            ctx.beginPath();
            ctx.moveTo(canvas.width / 2, canvas.height / 2);
            ctx.lineTo(canvas.width / 2 + (i * 600), canvas.height);
            ctx.stroke();
        }
    }

    function animate() {
        ctx.fillStyle = '#020202';
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        frame += 0.8;
        drawBackground();

        // High-speed Particles
        for(let i=0; i<40; i++) {
            let x = (Math.tan(i + frame*0.005) * canvas.width/2) + canvas.width/2;
            let y = (Math.sin(i + frame*0.01) * canvas.height/2) + canvas.height/2;
            ctx.fillStyle = i % 2 === 0 ? 'rgba(0, 242, 255, 0.3)' : 'rgba(212, 175, 55, 0.3)';
            ctx.beginPath();
            ctx.arc(x, y, 1, 0, Math.PI*2);
            ctx.fill();
        }

        requestAnimationFrame(animate);
    }

    function joinVIP() { 
        const card = document.getElementById('vipCard');
        card.style.transform = "scale(0.95) translateZ(-50px)";
        setTimeout(() => { card.style.transform = "scale(1) translateZ(0)"; }, 200);
    }

    animate();
</script>

</body>
</html>
