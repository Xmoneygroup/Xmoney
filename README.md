<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Domain Offering</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Montserrat:wght@300;500&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000; 
        }

        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 1;
        }

        .content-wrapper {
            position: relative;
            z-index: 10;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            pointer-events: none;
        }

        /* PLLAKATA VIP TEJDUKSHME ME HIJE DINAMIKE */
        .luxury-card {
            text-align: center;
            padding: 50px 80px;
            background: rgba(255, 255, 255, 0.02); /* Super e tejdukshme */
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            backdrop-filter: blur(20px);
            
            /* Hija VIP që ndryshon ngjyrat */
            box-shadow: 0 0 50px rgba(212, 175, 55, 0.2);
            animation: vipShadowPulse 8s linear infinite;
        }

        .title {
            font-family: 'Cinzel', serif;
            font-size: 4rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 15px;
            margin: 0;
            background: linear-gradient(to bottom, #fff, #d4af37, #aa8c2e);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 10px rgba(212, 175, 55, 0.5));
        }

        .subtitle {
            font-family: 'Montserrat', sans-serif;
            color: #fff;
            font-size: 1.1rem;
            margin-top: 25px;
            letter-spacing: 4px;
            font-weight: 500;
            opacity: 0.9;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }

        /* ANIMACIONI I HIJES VIP (RGB GOLD/WHITE/PURPLE) */
        @keyframes vipShadowPulse {
            0% { box-shadow: 0 0 40px rgba(212, 175, 55, 0.3); border-color: rgba(212, 175, 55, 0.2); }
            33% { box-shadow: 0 0 60px rgba(255, 255, 255, 0.2); border-color: rgba(255, 255, 255, 0.2); }
            66% { box-shadow: 0 0 40px rgba(138, 43, 226, 0.2); border-color: rgba(138, 43, 226, 0.2); }
            100% { box-shadow: 0 0 40px rgba(212, 175, 55, 0.3); border-color: rgba(212, 175, 55, 0.2); }
        }

        @media (max-width: 768px) {
            .title { font-size: 2rem; letter-spacing: 5px; }
            .luxury-card { padding: 30px; margin: 20px; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="content-wrapper">
        <div class="luxury-card">
            <h1 class="title">Domain for Sale</h1>
            <div class="subtitle">This domain will be sold in a very short time</div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        let particlesArray;

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        class Particle {
            constructor(x, y, directionX, directionY, size) {
                this.x = x;
                this.y = y;
                this.directionX = directionX;
                this.directionY = directionY;
                this.size = size;
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2, false);
                ctx.fillStyle = '#fff';
                ctx.shadowBlur = 10; // Efekti i shkëlqimit për çdo pikë
                ctx.shadowColor = '#fff';
                ctx.fill();
            }
            update() {
                if (this.x > canvas.width || this.x < 0) this.directionX = -this.directionX;
                if (this.y > canvas.height || this.y < 0) this.directionY = -this.directionY;
                this.x += this.directionX;
                this.y += this.directionY;
                this.draw();
            }
        }

        function init() {
            particlesArray = [];
            let numberOfParticles = (canvas.height * canvas.width) / 15000;
            for (let i = 0; i < numberOfParticles; i++) {
                let size = Math.random() * 2;
                let x = Math.random() * innerWidth;
                let y = Math.random() * innerHeight;
                let directionX = (Math.random() * 0.5) - 0.25;
                let directionY = (Math.random() * 0.5) - 0.25;
                particlesArray.push(new Particle(x, y, directionX, directionY, size));
            }
        }

        function connect() {
            for (let a = 0; a < particlesArray.length; a++) {
                for (let b = a; b < particlesArray.length; b++) {
                    let distance = ((particlesArray[a].x - particlesArray[b].x) ** 2)
                                 + ((particlesArray[a].y - particlesArray[b].y) ** 2);
                    
                    if (distance < 150 * 150) {
                        let opacity = 1 - (distance / (150 * 150));
                        // VIJAT ME EFEKT NEON
                        ctx.strokeStyle = `rgba(255, 255, 255, ${opacity * 0.3})`;
                        ctx.lineWidth = 1;
                        ctx.shadowBlur = 5; // Shkëlqimi i vijave
                        ctx.shadowColor = 'rgba(212, 175, 55, 0.5)';
                        ctx.beginPath();
                        ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                        ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                        ctx.stroke();
                        ctx.shadowBlur = 0; // Reset shkëlqimin për performancë
                    }
                }
            }
        }

        function animate() {
            requestAnimationFrame(animate);
            ctx.clearRect(0,0, innerWidth, innerHeight);
            for (let i = 0; i < particlesArray.length; i++) {
                particlesArray[i].update();
            }
            connect();
        }

        init();
        animate();

        window.addEventListener('resize', () => {
            canvas.width = innerWidth;
            canvas.height = innerHeight;
            init();
        });
    </script>
</body>
</html>
