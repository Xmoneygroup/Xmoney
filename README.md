<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Domain Offering</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Montserrat:wght@300&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000; /* Fillimi i zi */
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

        /* KONTEJNERI I TEKSTIT */
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
            padding: 40px 60px;
            background: rgba(255, 255, 255, 0.01);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            
            /* Vonesa prej 2 sekondash për shfaqjen */
            opacity: 0;
            transform: translateY(30px);
            animation: showContent 1.5s ease-out forwards 2s;
        }

        .title {
            font-family: 'Syncopate', sans-serif;
            font-size: 3.5rem;
            color: #fff;
            letter-spacing: 15px;
            text-transform: uppercase;
            margin: 0;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.4);
        }

        .subtitle {
            color: #00d2ff;
            letter-spacing: 8px;
            text-transform: uppercase;
            margin-top: 20px;
            font-weight: 300;
        }

        /* ANIMACIONI I SHFAQJES */
        @keyframes showContent {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* MOBILE OPTIMIZATION */
        @media (max-width: 768px) {
            .title { font-size: 1.5rem; letter-spacing: 5px; }
            .subtitle { font-size: 0.7rem; letter-spacing: 4px; }
            .glass-card { padding: 30px 20px; width: 80%; }
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
                this.x = canvas.width / 2; // Fillon nga mesi poshtë
                this.y = canvas.height;
                this.targetY = Math.random() * (canvas.height * 0.5); // Plaset në gjysmën e sipërme
                this.speed = 3 + Math.random() * 3;
                this.angle = Math.atan2(this.targetY - this.y, (canvas.width / 2) - this.x);
                this.velocity = {
                    x: Math.cos(this.angle) * this.speed,
                    y: Math.sin(this.angle) * this.speed
                };
                this.particles = [];
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
                const colors = ['#00f2ff', '#00ffaa', '#ff00ee', '#ffff00', '#ff3300'];
                const color = colors[Math.floor(Math.random() * colors.length)];
                for (let i = 0; i < 50; i++) {
                    this.particles.push(new Particle(this.x, this.y, color));
                }
            }
        }

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.velocity = {
                    x: (Math.random() - 0.5) * 8,
                    y: (Math.random() - 0.5) * 8
                };
                this.alpha = 1;
                this.friction = 0.95;
            }

            draw() {
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 10;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.globalAlpha = 1;
                ctx.shadowBlur = 0;
            }

            update() {
                this.velocity.x *= this.friction;
                this.velocity.y *= this.friction;
                this.x += this.velocity.x;
                this.y += this.velocity.y;
                this.alpha -= 0.01;
            }
        }

        let fireworks = [];
        let particles = [];

        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.15)'; // Efekti trail i zi
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            if (Math.random() < 0.05) { // Frekuenca e fishekzjarrëve
                fireworks.push(new Firework());
            }

            fireworks.forEach((fw, index) => {
                fw.update();
                fw.draw();
                if (fw.dead) {
                    particles.push(...fw.particles);
                    fireworks.splice(index, 1);
                }
            });

            particles.forEach((p, index) => {
                p.update();
                p.draw();
                if (p.alpha <= 0) {
                    particles.splice(index, 1);
                }
            });

            requestAnimationFrame(animate);
        }

        // Fillon animacionin pas 2 sekondash (bashkë me tekstin)
        setTimeout(() => {
            animate();
        }, 500); // Fishekzjarrët fillojnë pak më herët se teksti për efekt skenik

    </script>
</body>
</html>
