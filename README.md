<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain | Grand Sale</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Montserrat:wght@300;600&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000;
            font-family: 'Montserrat', sans-serif;
        }

        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .content {
            position: relative;
            z-index: 10;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            pointer-events: none;
        }

        .glass-card {
            padding: 50px 70px;
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 2px; /* Stil arkitektural */
            opacity: 0;
            transform: scale(0.8);
            animation: showContent 1.2s cubic-bezier(0.17, 0.67, 0.83, 0.67) forwards 2s;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 4rem;
            color: #fff;
            letter-spacing: 20px;
            text-transform: uppercase;
            margin: 0;
            background: linear-gradient(to right, #fff, #00d2ff, #fff);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shine 4s linear infinite;
        }

        .subtitle {
            color: rgba(255, 255, 255, 0.8);
            letter-spacing: 10px;
            text-transform: uppercase;
            margin-top: 25px;
            font-weight: 600;
            font-size: 1.1rem;
        }

        @keyframes showContent {
            to { opacity: 1; transform: scale(1); }
        }

        @keyframes shine {
            to { background-position: 200% center; }
        }

        @media (max-width: 768px) {
            .title { font-size: 1.6rem; letter-spacing: 6px; }
            .subtitle { font-size: 0.7rem; letter-spacing: 4px; }
            .glass-card { padding: 40px 20px; width: 85%; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="content">
        <div class="glass-card">
            <h1 class="title">DOMAIN SALE</h1>
            <p class="subtitle">This domain is for sale...</p>
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
                // Niset nga çdo pikë në fund të ekranit
                this.x = Math.random() * canvas.width;
                this.y = canvas.height;
                // Shënjestra në lartësi të ndryshme
                this.targetY = Math.random() * (canvas.height * 0.6);
                this.speed = 2 + Math.random() * 4;
                this.angle = -Math.PI / 2 + (Math.random() * 0.4 - 0.2); // Pothuajse drejt lart
                this.velocity = {
                    x: Math.cos(this.angle) * this.speed,
                    y: Math.sin(this.angle) * this.speed
                };
                // Madhësia e shpërthimit (disa shumë të mëdha, disa mesatare)
                this.explosionSize = Math.random() > 0.8 ? 100 : 40 + Math.random() * 40;
                this.dead = false;
            }

            update() {
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                if (this.y <= this.targetY) {
                    this.explode();
                    this.dead = true;
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = "#fff";
                ctx.fill();
            }

            explode() {
                const neonColors = ['#00f2ff', '#00ffaa', '#ff00ee', '#ffff00', '#ff3300', '#4d4dff'];
                const color = neonColors[Math.floor(Math.random() * neonColors.length)];
                for (let i = 0; i < this.explosionSize; i++) {
                    particles.push(new Particle(this.x, this.y, color));
                }
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                const angle = Math.random() * Math.PI * 2;
                const force = Math.random() * 10; // Shpërthim më i fuqishëm
                this.velocity = {
                    x: Math.cos(angle) * force,
                    y: Math.sin(angle) * force
                };
                this.alpha = 1;
                this.friction = 0.94;
                this.gravity = 0.15;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2.5, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 15;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.restore();
            }

            update() {
                this.velocity.x *= this.friction;
                this.velocity.y *= this.friction;
                this.velocity.y += this.gravity;
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                this.alpha -= 0.012;
            }
        }

        let fireworks = [];
        let particles = [];

        function animate() {
            // Efekti trail që lejon dritat të mbeten pak në ekran
            ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            if (Math.random() < 0.08) { // Më shumë fishekzjarrë
                fireworks.push(new Firework());
            }

            fireworks.forEach((fw, index) => {
                fw.update();
                fw.draw();
                if (fw.dead) fireworks.splice(index, 1);
            });

            particles.forEach((p, index) => {
                p.update();
                p.draw();
                if (p.alpha <= 0) particles.splice(index, 1);
            });

            requestAnimationFrame(animate);
        }

        // Fillon spektakli
        animate();
    </script>
</body>
</html>
