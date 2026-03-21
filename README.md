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

        /* Base Styles */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #020202; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

        canvas { position: fixed; top: 0; left: 0; z-index: 0; pointer-events: none; }

        .hero {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 100px 20px;
            /* Subtle overlay to ensure text readability */
            background: radial-gradient(circle at center, rgba(0, 242, 255, 0.03) 0%, transparent 80%);
        }

        /* --- PROFESSIONAL TEXT ANIMATION --- */
        .title-wrapper { perspective: 1000px; margin-bottom: 30px; }
        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: clamp(60px, 15vw, 180px);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -5px;
            line-height: 0.8;
            background: linear-gradient(to bottom, #fff 40%, rgba(255,255,255,0.2) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 10px 30px rgba(0,0,0,0.5));
            animation: titleEntrance 1.8s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .manifesto-container {
            max-width: 750px;
            text-align: center;
            margin-bottom: 50px;
        }

        .manifesto-text {
            font-size: 17px;
            line-height: 1.6;
            color: rgba(255,255,255,0.7);
            margin-bottom: 24px;
            font-weight: 300;
            letter-spacing: 1.5px;
            opacity: 0;
            transform: translateY(30px) filter(blur(10px));
            animation: textReveal 1.2s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        .highlight-cyan { 
            color: var(--cyan); 
            font-weight: 600; 
            text-shadow: 0 0 15px rgba(0, 242, 255, 0.3);
        }

        /* --- ELITE VIP CARD --- */
        .vip-card {
            background: rgba(10, 10, 10, 0.6);
            border: 1px solid var(--border);
            padding: 50px;
            width: 95%;
            max-width: 480px;
            border-radius: 30px;
            backdrop-filter: blur(25px);
            position: relative;
            transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
            animation: cardEntrance 1.5s cubic-bezier(0.16, 1, 0.3, 1) 1s forwards; 
            opacity: 0;
            box-shadow: 0 40px 100px rgba(0,0,0,0.8);
        }

        .vip-card:hover {
            transform: translateY(-10px);
            border-color: rgba(0, 242, 255, 0.4);
            box-shadow: 0 20px 60px rgba(0, 242, 255, 0.1);
        }

        .features-list { list-style: none; text-align: center; margin-bottom: 35px; }
        .features-list li {
            padding: 18px 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            font-size: 13px;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: rgba(255,255,255,0.9);
            font-weight: 400;
        }

        .features-list li:last-child { border-bottom: none; }

        .join-btn {
            width: 100%;
            padding: 22px;
            background: #fff;
            color: #000;
            border: none;
            border-radius: 15px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            transition: 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            text-decoration: none;
            display: block;
            text-align: center;
            font-size: 14px;
        }

        .join-btn:hover {
            background: var(--cyan);
            transform: scale(0.97);
            box-shadow: 0 0 30px rgba(0, 242, 255, 0.4);
        }

        /* --- ANIMATIONS --- */
        @keyframes titleEntrance {
            0% { opacity: 0; transform: translateY(50px) scale(0.9); filter: blur(20px); }
            100% { opacity: 1; transform: translateY(0) scale(1); filter: blur(0); }
        }
        @keyframes textReveal {
            to { opacity: 1; transform: translateY(0); filter: blur(0); }
        }
        @keyframes cardEntrance {
            to { opacity: 1; transform: translateY(0); }
        }

        @media(max-width: 768px) {
            .title { font-size: 65px; letter-spacing: -2px; }
            .vip-card { padding: 30px; }
            .manifesto-text { font-size: 15px; }
        }
    </style>
</head>
<body>

<canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="title-wrapper">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text" style="animation-delay: 0.6s">
            The market has <span class="highlight-cyan">zero mercy</span> for anyone. Without discipline and a clear strategy, losses are inevitable.
        </p>
        <p class="manifesto-text" style="animation-delay: 0.9s">
            Our mission is to help you build a <span class="highlight-cyan">structured approach</span> through proper risk management and a precise trading strategy.
        </p>
        <p class="manifesto-text" style="animation-delay: 1.2s">
            If you are ready to elevate your trading and join the <span class="highlight-cyan">VIP ZONE</span>, act now. Do not wait until it is too late.
        </p>
    </div>

    <div class="vip-card">
        <ul class="features-list">
            <li>Signals + Strategy</li>
            <li>57% - 60% Guaranteed Win Rate</li>
            <li>3+ Daily Signals</li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Get Access Now</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    
    let stars = [];
    let nebulas = [];
    const starCount = 400;
    let mouse = { x: 0, y: 0, active: false };

    window.addEventListener('mousemove', (e) => {
        mouse.x = e.clientX;
        mouse.y = e.clientY;
        mouse.active = true;
    });

    function resize() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resize);
    resize();

    class Star {
        constructor() {
            this.x = (Math.random() - 0.5) * 2000;
            this.y = (Math.random() - 0.5) * 2000;
            this.z = Math.random() * 2000;
            this.size = 0.5 + Math.random() * 1.5;
        }

        update() {
            this.z -= 1.5; // Forward speed
            if (this.z <= 0) this.z = 2000;
        }

        draw() {
            // 3D projection
            let x = this.x / (this.z / 1000) + canvas.width / 2;
            let y = this.y / (this.z / 1000) + canvas.height / 2;
            let s = this.size * (1000 / this.z);

            // Parallax movement based on mouse
            let mx = (mouse.x - canvas.width / 2) * 0.05;
            let my = (mouse.y - canvas.height / 2) * 0.05;

            ctx.beginPath();
            ctx.arc(x + mx, y + my, s, 0, Math.PI * 2);
            ctx.fillStyle = `rgba(255, 255, 255, ${1 - this.z / 2000})`;
            ctx.fill();
        }
    }

    class Nebula {
        constructor() {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.r = Math.random() * 400 + 200;
            this.color = Math.random() > 0.5 ? 'rgba(0, 242, 255, 0.04)' : 'rgba(212, 175, 55, 0.02)';
        }
        draw() {
            let g = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.r);
            g.addColorStop(0, this.color);
            g.addColorStop(1, 'transparent');
            ctx.fillStyle = g;
            ctx.fillRect(0,0, canvas.width, canvas.height);
        }
    }

    function init() {
        stars = [];
        nebulas = [];
        for (let i = 0; i < starCount; i++) stars.push(new Star());
        for (let i = 0; i < 5; i++) nebulas.push(new Nebula());
    }

    function animate() {
        ctx.fillStyle = '#020202';
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        nebulas.forEach(n => n.draw());
        stars.forEach(s => {
            s.update();
            s.draw();
        });

        requestAnimationFrame(animate);
    }

    function joinVIP() {
        document.querySelector('.vip-card').style.transform = "scale(0.95)";
    }

    init();
    animate();
</script>

</body>
</html>
