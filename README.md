<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Asset | Domain for Sale</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Montserrat:wght@300&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #020202; 
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

        .luxury-card {
            text-align: center;
            padding: 60px;
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(212, 175, 55, 0.15); /* Kornizë e hollë ari */
            border-radius: 2px; /* Kthesa minimale për pamje më serioze */
            backdrop-filter: blur(15px);
            box-shadow: 0 40px 100px rgba(0,0,0,0.8);
            animation: fadeInCard 3s ease-out;
        }

        .title {
            font-family: 'Cinzel', serif; /* Font mbretëror */
            font-size: 4.5rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 18px;
            margin: 0;
            /* Gradient ari i pasur */
            background: linear-gradient(to bottom, #ffffff 0%, #d4af37 50%, #8a6d3b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px rgba(212, 175, 55, 0.3));
            animation: luxuryGlow 4s ease-in-out infinite alternate;
        }

        .subtitle {
            font-family: 'Montserrat', sans-serif;
            color: rgba(255, 255, 255, 0.4);
            font-size: 0.9rem;
            margin-top: 20px;
            letter-spacing: 12px;
            text-transform: uppercase;
            font-weight: 300;
        }

        @keyframes luxuryGlow {
            from { filter: drop-shadow(0 0 15px rgba(212, 175, 55, 0.2)); }
            to { filter: drop-shadow(0 0 30px rgba(212, 175, 55, 0.5)); }
        }

        @keyframes fadeInCard {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 768px) {
            .title { font-size: 2.2rem; letter-spacing: 8px; }
            .luxury-card { padding: 30px; margin: 20px; }
        }
    </style>
</head>
<body>

    <canvas id="canvas"></canvas>

    <div class="content-wrapper">
        <div class="luxury-card">
            <h1 class="title">Domain is for Sale</h1>
            <div class="subtitle">Premium Digital Real Estate</div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        let particlesArray;
        let lineReach = 0; // Përdoret për animacionin e vijave në fillim

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
                ctx.fillStyle = 'rgba(212, 175, 55, 0.5)';
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
            // Reduktuar numrin e pikave për më shumë elegancë
            let numberOfParticles = (canvas.height * canvas.width) / 18000; 
            for (let i = 0; i < numberOfParticles; i++) {
                let size = (Math.random() * 1.5) + 0.5;
                let x = Math.random() * innerWidth;
                let y = Math.random() * innerHeight;
                let directionX = (Math.random() * 0.4) - 0.2;
                let directionY = (Math.random() * 0.4) - 0.2;
                particlesArray.push(new Particle(x, y, directionX, directionY, size));
            }
        }

        function connect() {
            // Animacioni i rritjes së distancës së vijave (lindja e rrjetës)
            if (lineReach < 160) lineReach += 0.5; 

            for (let a = 0; a < particlesArray.length; a++) {
                for (let b = a; b < particlesArray.length; b++) {
                    let distance = ((particlesArray[a].x - particlesArray[b].x) ** 2)
                                 + ((particlesArray[a].y - particlesArray[b].y) ** 2);
                    
                    if (distance < lineReach * lineReach) {
                        let opacity = 1 - (distance / (lineReach * lineReach));
                        ctx.strokeStyle = `rgba(212, 175, 55, ${opacity * 0.2})`;
                        ctx.lineWidth = 0.5;
                        ctx.beginPath();
                        ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                        ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                        ctx.stroke();
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
