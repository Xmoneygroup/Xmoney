<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Domain Portfolio | dubrent.com</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Inter:wght@300;400;600&family=Syncopate:wght@700&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Inter', sans-serif;
        }

        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .main-wrapper {
            position: relative;
            z-index: 10;
            width: 100%;
            height: 100vh;
            display: flex;
            flex-direction: row;
            justify-content: center; 
            align-items: center;     
            gap: 80px;                
            padding: 20px;
            padding-bottom: 120px;
            box-sizing: border-box;
            pointer-events: none;
        }

        /* PLLAKATA PREMIUM */
        .glass-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            width: 460px;
            padding: 50px;
            border-radius: 30px;
            text-align: left;
            box-shadow: 0 50px 100px rgba(0,0,0,0.8);
            pointer-events: auto;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.4s ease;
        }

        .glass-card h2 {
            color: #111;
            font-family: 'Playfair Display', serif;
            font-size: 2.2rem;
            margin: 0 0 20px 0;
            letter-spacing: -0.5px;
        }

        .domain-line {
            border-bottom: 1px solid rgba(0,0,0,0.08);
            padding-bottom: 25px;
            margin-bottom: 35px;
        }

        .domain-name {
            color: #666;
            font-weight: 300;
            font-size: 1rem;
            margin: 0 0 8px 0;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .price {
            font-family: 'Inter', sans-serif;
            font-size: 2rem;
            font-weight: 700;
            color: #B8860B; /* Dark Gold */
            margin: 0;
            display: flex;
            align-items: center;
        }

        .next-btn {
            display: block;
            width: 100%;
            padding: 22px;
            background: #000;
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            border-radius: 15px;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: none;
            cursor: pointer;
            text-align: center;
            font-size: 1.1rem;
            letter-spacing: 1px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .next-btn:hover {
            background: #B8860B;
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(184, 134, 11, 0.3);
        }

        .contact-info {
            color: #888;
            font-size: 0.9rem;
            margin-top: 40px;
            text-align: center;
        }

        .phone-link {
            color: #111;
            text-decoration: none;
            font-size: 1.4rem;
            font-weight: 600;
            display: block;
            margin-top: 10px;
            transition: color 0.3s;
        }

        .phone-link:hover { color: #B8860B; }

        /* INFO PANEL */
        .info-panel {
            text-align: left;
            color: #fff;
        }

        .info-domain {
            font-family: 'Syncopate', sans-serif;
            font-size: 4rem;
            margin: 0;
            letter-spacing: -2px;
            text-transform: lowercase;
            background: linear-gradient(to bottom, #fff, #888);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .info-status {
            font-size: 1.8rem;
            font-weight: 300;
            opacity: 0.6;
            margin: 10px 0 50px 0;
            letter-spacing: 4px;
            text-transform: uppercase;
        }

        .trust-list {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .trust-item {
            display: flex;
            align-items: center;
            gap: 20px;
            font-size: 1rem;
            color: rgba(255,255,255,0.7);
            font-weight: 300;
        }

        .trust-item span {
            font-size: 1.6rem;
            color: #B8860B;
        }

        @media (max-width: 1100px) {
            .main-wrapper { flex-direction: column; gap: 50px; padding-bottom: 50px; }
            .info-panel { text-align: center; }
            .trust-list { align-items: center; }
            .glass-card { width: 90%; max-width: 440px; }
            .info-domain { font-size: 2.8rem; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="main-wrapper">
        <div class="glass-card">
            <h2>Acquire Ownership</h2>
            <div class="domain-line">
                <p class="domain-name">Identity: dubrent.com</p>
                <p class="price">$20,000.00 USD</p>
            </div>
            
            <a href="LINKU_YT_KETU" class="next-btn">CONTINUE TO SECURE CHECKOUT</a>
            
            <div class="contact-info">
                Executive Support Available<br>
                <a href="tel:+389XXXXXXXXX" class="phone-link">+389 XX XXX XXX</a> 
            </div>
        </div>

        <div class="info-panel">
            <div class="info-domain">dubrent.com</div>
            <div class="info-status">Now Available</div>
            
            <div class="trust-list">
                <div class="trust-item">
                    <span class="material-icons">verified</span>
                    Instant ownership transfer protocol
                </div>
                <div class="trust-item">
                    <span class="material-icons">auto_awesome</span>
                    High-authority premium domain
                </div>
                <div class="trust-item">
                    <span class="material-icons">shield</span>
                    Fully escrow-secured transaction
                </div>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        class Firework {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = canvas.height;
                this.targetY = Math.random() * (canvas.height * 0.7) + 50;
                this.speed = 2.5 + Math.random() * 2;
                this.angle = -Math.PI / 2 + (Math.random() * 0.2 - 0.1);
                this.velocity = { x: Math.cos(this.angle) * this.speed, y: Math.sin(this.angle) * this.speed };
                const rand = Math.random();
                if (rand > 0.9) this.explosionSize = 180;
                else if (rand > 0.5) this.explosionSize = 100;
                else this.explosionSize = 50;
                this.dead = false;
                this.trail = [];
            }
            update() {
                this.trail.push({x: this.x, y: this.y});
                if (this.trail.length > 12) this.trail.shift();
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                if (this.y <= this.targetY) { this.explode(); this.dead = true; }
            }
            draw() {
                ctx.beginPath(); ctx.strokeStyle = "rgba(184, 134, 11, 0.2)"; ctx.lineWidth = 1;
                if(this.trail.length > 0) { ctx.moveTo(this.trail[0].x, this.trail[0].y); ctx.lineTo(this.x, this.y); ctx.stroke(); }
            }
            explode() {
                const luxuryColors = ['#B8860B', '#FFD700', '#FFFFFF', '#F0E68C', '#DAA520'];
                const color = luxuryColors[Math.floor(Math.random() * luxuryColors.length)];
                for (let i = 0; i < this.explosionSize; i++) { particles.push(new Particle(this.x, this.y, color)); }
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x; this.y = y; this.color = color;
                const angle = Math.random() * Math.PI * 2;
                const force = Math.random() * 8;
                this.velocity = { x: Math.cos(angle) * force, y: Math.sin(angle) * force };
                this.alpha = 1; this.friction = 0.95; this.gravity = 0.12; this.size = Math.random() * 2 + 0.5;
            }
            draw() {
                ctx.save(); ctx.globalAlpha = this.alpha; ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2); ctx.fillStyle = this.color;
                ctx.shadowBlur = 10; ctx.shadowColor = this.color; ctx.fill(); ctx.restore();
            }
            update() {
                this.velocity.x *= this.friction; this.velocity.y *= this.friction; this.velocity.y += this.gravity;
                this.x += this.velocity.x; this.y += this.velocity.y; this.alpha -= 0.008;
            }
        }

        let fireworks = []; let particles = [];
        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.15)'; ctx.fillRect(0, 0, canvas.width, canvas.height);
            if (Math.random() < 0.04) { fireworks.push(new Firework()); }
            fireworks.forEach((fw, index) => { fw.update(); fw.draw(); if (fw.dead) fireworks.splice(index, 1); });
            particles.forEach((p, index) => { p.update(); p.draw(); if (p.alpha <= 0) particles.splice(index, 1); });
            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
