<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain Sales | dubrent.com</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Space+Grotesk:wght@300;400;600;700&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Space Grotesk', sans-serif;
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
            gap: 60px;                
            padding: 20px;
            padding-bottom: 180px;
            box-sizing: border-box;
            pointer-events: none;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.05); 
            backdrop-filter: blur(8px); 
            -webkit-backdrop-filter: blur(8px);
            width: 570px; 
            padding: 60px; 
            border-radius: 40px;
            text-align: left;
            box-shadow: 0 30px 60px rgba(0,0,0,0.3);
            pointer-events: auto;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .badge-container {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
        }

        .badge {
            display: flex;
            align-items: center;
            gap: 6px;
            padding: 6px 14px;
            border-radius: 100px;
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .verified-badge { background: rgba(0, 242, 255, 0.15); color: #00f2ff; border: 1px solid rgba(0, 242, 255, 0.3); }
        .premium-badge { background: rgba(255, 215, 0, 0.15); color: #ffd700; border: 1px solid rgba(255, 215, 0, 0.3); }
        .badge span { font-size: 14px; }

        .glass-card h2 { color: #fff; font-size: 2rem; margin: 0 0 15px 0; font-weight: 600; letter-spacing: -0.5px; }
        .glass-card .domain-line { display: block; margin-bottom: 35px; }
        .glass-card .domain-name { color: rgba(255,255,255,0.8); font-weight: 300; font-size: 1.1rem; margin: 0 0 8px 0; }
        .glass-card .price { font-size: 1.8rem; font-weight: 700; color: #fff; margin: 0; letter-spacing: 0.5px; }

        .next-btn {
            display: block;
            width: 100%;
            padding: 20px;
            background: #fff;
            color: #000;
            text-decoration: none;
            font-weight: 600;
            border-radius: 20px;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            text-align: center;
            font-size: 1.1rem;
        }

        .next-btn:hover { background: rgba(255,255,255,0.9); transform: scale(0.98); }

        .contact-info { color: rgba(255,255,255,0.5); font-size: 0.9rem; margin-top: 40px; text-align: center; }
        .phone-link { color: #fff; text-decoration: none; font-size: 1.4rem; font-weight: 600; display: block; margin-top: 10px; }

        .info-panel { text-align: left; color: #fff; }
        .info-domain { font-family: 'Syncopate', sans-serif; font-size: 3.5rem; margin: 0; letter-spacing: 2px; text-transform: lowercase; text-shadow: 0 0 30px rgba(255,255,255,0.2); }
        .info-status { font-size: 1.6rem; font-weight: 300; opacity: 0.8; margin-top: 5px; margin-bottom: 40px; text-transform: uppercase; letter-spacing: 3px; }

        .trust-list { display: flex; flex-direction: column; gap: 20px; align-items: flex-start; }
        .trust-item { display: flex; align-items: center; gap: 15px; font-size: 1rem; color: rgba(255,255,255,0.8); font-weight: 300; }
        .trust-item span { font-size: 1.4rem; color: #00f2ff; }

        @media (max-width: 1000px) {
            .main-wrapper { flex-direction: column; gap: 40px; padding-bottom: 40px; }
            .info-panel { text-align: center; }
            .trust-list { align-items: center; }
            .glass-card { width: 90%; max-width: 570px; padding: 40px; }
            .info-domain { font-size: 2.5rem; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="main-wrapper">
        <div class="glass-card" id="target-card">
            <div class="badge-container">
                <div class="badge verified-badge"><span class="material-icons">verified</span> verified</div>
                <div class="badge premium-badge"><span class="material-icons">stars</span> premium domain</div>
            </div>

            <h2>Buy Now</h2>
            <div class="domain-line">
                <p class="domain-name">dubinv.com is for sale now</p>
                <p class="price">20,000 USD</p>
            </div>
            
            <a href="#" class="next-btn" id="btn-next">Next</a>
            
            <div class="contact-info" id="contact-text">
                Need help? Give us a call<br>
                <a href="tel:+389XXXXXXXXX" class="phone-link">+389 XX XXX XXX</a> 
            </div>
        </div>

        <div class="info-panel">
            <div class="info-domain">dubinv.com</div>
            <div class="info-status">is for sale!</div>
            <div class="trust-list">
                <div class="trust-item"><span class="material-icons">verified_user</span> Simple, secure purchase & transfer</div>
                <div class="trust-item"><span class="material-icons">public</span> Trusted by customers globally</div>
                <div class="trust-item"><span class="material-icons">support_agent</span> 24/7 dedicated support</div>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        const nextBtn = document.getElementById('btn-next');
        const contactArea = document.getElementById('contact-text');
        
        let width, height;
        function setCanvasSize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        setCanvasSize();
        window.addEventListener('resize', setCanvasSize);

        class Person {
            constructor(targetType) {
                this.targetType = targetType; // 'button' ose 'letter'
                this.init();
            }

            init() {
                this.x = Math.random() < 0.5 ? -50 : width + 50;
                this.y = height - 100 - Math.random() * 200;
                this.size = 20;
                this.color = `hsl(${Math.random() * 360}, 100%, 65%)`;
                this.state = 'approaching'; 
                this.waitStart = 0;
                this.legAngle = 0;
                this.opacity = 1;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.opacity;
                ctx.strokeStyle = this.color;
                ctx.lineWidth = 2.5;
                
                const headR = 6;
                const bodyH = 15;

                // Kokë e rrumbullakët
                ctx.beginPath();
                ctx.arc(this.x, this.y - bodyH - headR, headR, 0, Math.PI*2);
                ctx.stroke();

                // Trupi me vija
                ctx.beginPath();
                ctx.moveTo(this.x, this.y - bodyH);
                ctx.lineTo(this.x, this.y);
                ctx.stroke();

                if (this.state === 'sitting') {
                    // Këmbët e ulura
                    ctx.beginPath();
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x + 10, this.y + 5);
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x - 10, this.y + 5);
                    ctx.stroke();
                } else {
                    // Këmbët duke vrapuar ose rënë
                    let anim = Math.sin(this.legAngle) * 10;
                    ctx.beginPath();
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x - anim, this.y + 12);
                    ctx.moveTo(this.x, this.y); ctx.lineTo(this.x + anim, this.y + 12);
                    ctx.stroke();
                }
                ctx.restore();
            }

            update() {
                const targetRect = (this.targetType === 'button' ? nextBtn : contactArea).getBoundingClientRect();
                const targetX = targetRect.left + (this.targetType === 'button' ? targetRect.width/2 : 20);
                const targetY = targetRect.top;

                if (this.state === 'approaching') {
                    this.legAngle += 0.2;
                    this.x += (targetX - this.x) * 0.03;
                    this.y += (targetY - this.y) * 0.03;
                    if (Math.abs(this.x - targetX) < 5 && Math.abs(this.y - targetY) < 5) {
                        this.state = 'sitting';
                        this.waitStart = Date.now();
                    }
                } else if (this.state === 'sitting') {
                    this.x = targetX;
                    this.y = targetY;
                    if (Date.now() - this.waitStart > 2000) this.state = 'falling';
                } else if (this.state === 'falling') {
                    this.y += 8;
                    this.opacity -= 0.02;
                    if (this.y > height + 50 || this.opacity <= 0) this.init();
                }
            }
        }

        // --- Raketat çdo 3 sekonda ---
        class Firework {
            constructor() {
                this.x = Math.random() * width;
                this.y = height;
                this.targetY = Math.random() * (height * 0.4) + 50;
                this.velY = -Math.random() * 3 - 5;
                this.dead = false;
            }
            update() {
                this.y += this.velY;
                if (this.y <= this.targetY) { this.explode(); this.dead = true; }
            }
            draw() {
                ctx.fillStyle = "white";
                ctx.beginPath(); ctx.arc(this.x, this.y, 2, 0, Math.PI*2); ctx.fill();
            }
            explode() {
                const colors = ['#00f2ff', '#ffd700', '#ff0077', '#00ffaa'];
                const color = colors[Math.floor(Math.random()*colors.length)];
                for (let i = 0; i < 40; i++) particles.push(new Particle(this.x, this.y, color));
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x; this.y = y; this.color = color;
                this.vel = { x: (Math.random()-0.5)*10, y: (Math.random()-0.5)*10 };
                this.alpha = 1;
            }
            update() { this.x += this.vel.x; this.y += this.vel.y; this.alpha -= 0.02; }
            draw() {
                ctx.globalAlpha = this.alpha;
                ctx.fillStyle = this.color;
                ctx.beginPath(); ctx.arc(this.x, this.y, 2, 0, Math.PI*2); ctx.fill();
            }
        }

        let people = [new Person('button'), new Person('letter')];
        let fireworks = [];
        let particles = [];

        // Raketa çdo 3 sekonda (3-4 copë)
        setInterval(() => {
            for(let i=0; i<Math.floor(Math.random()*2)+3; i++) {
                setTimeout(() => fireworks.push(new Firework()), i * 300);
            }
        }, 3000);

        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.25)';
            ctx.fillRect(0, 0, width, height);
            
            fireworks.forEach((f, i) => { f.update(); f.draw(); if (f.dead) fireworks.splice(i, 1); });
            particles.forEach((p, i) => { p.update(); p.draw(); if (p.alpha <= 0) particles.splice(i, 1); });
            people.forEach(p => { p.update(); p.draw(); });

            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
