<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Domain Offering | Liquid Blue</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Montserrat:wght@300;600&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #000; /* Baza */
        }

        /* SFONDI I RI ABSTRAKT (VALË MËNDAFSHI) */
        .liquid-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            z-index: 1;
            /* Gradient kompleks që simulon lëvizjen e lëngut */
            background: linear-gradient(125deg, #000000 0%, #000000 40%, #051937 60%, #004d7a 80%, #008793 100%);
            background-size: 400% 400%;
            animation: oceanWave 15s ease infinite;
        }

        #canvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 2; /* Pikat mbi sfondin likuid */
            /* Zvobëlojmë pak dukshmërinë e pikave që të dominojë sfondi */
            opacity: 0.6; 
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

        /* PLLAKATA PLOTËSISHT E TEJDUKSHME (PA NGJYRË) */
        .luxury-card {
            text-align: center;
            padding: 60px 90px;
            /* Pa ngjyrë background-i, vetëm xham dhe kornizë */
            background: rgba(255, 255, 255, 0.0); 
            border: 1px solid rgba(0, 255, 255, 0.2); /* Kornizë e kaltër e hapur */
            border-radius: 5px; /* Kthesa minimale VIP */
            backdrop-filter: blur(15px); /* Efekti xham mbi valë */
            
            /* Hije e kaltër elektrike */
            box-shadow: 0 0 50px rgba(0, 238, 255, 0.15);
            animation: neonBreathe 4s ease-in-out infinite alternate;
        }

        .title {
            font-family: 'Cinzel', serif;
            font-size: 4.5rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 18px;
            margin: 0;
            /* Gradient Platinum/Argjend */
            background: linear-gradient(to bottom, #ffffff 0%, #a2abb3 50%, #ffffff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.4));
        }

        .subtitle {
            font-family: 'Montserrat', sans-serif;
            color: #fff;
            font-size: 1rem;
            margin-top: 30px;
            letter-spacing: 10px;
            font-weight: 300;
            text-transform: uppercase;
            opacity: 0.8;
            text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
        }

        /* ANIMACIONET */
        @keyframes oceanWave {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes neonBreathe {
            from { 
                box-shadow: 0 0 40px rgba(0, 238, 255, 0.1);
                border-color: rgba(0, 255, 255, 0.1);
            }
            to { 
                box-shadow: 0 0 60px rgba(0, 238, 255, 0.25);
                border-color: rgba(0, 255, 255, 0.3);
            }
        }

        @media (max-width: 768px) {
            .title { font-size: 2.2rem; letter-spacing: 6px; }
            .luxury-card { padding: 30px; margin: 20px; }
            .subtitle { font-size: 0.8rem; letter-spacing: 5px; }
        }
    </style>
</head>
<body>

    <div class="liquid-background"></div>

    <canvas id="canvas"></canvas>

    <div class="content-wrapper">
        <div class="luxury-card">
            <h1 class="title">Domain for Sale</h1>
            <div class="subtitle">This Domain is for Sale</div>
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
                ctx.fillStyle = 'rgba(0, 255, 255, 0.7)'; // Pikat me të kaltra
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
            // Reduktuar numrin e pikave për t'ia lënë skenën sfondit likuid
            let numberOfParticles = (canvas.height * canvas.width) / 20000;
            for (let i = 0; i < numberOfParticles; i++) {
                let size = Math.random() * 1.5;
                let x = Math.random() * innerWidth;
                let y = Math.random() * innerHeight;
                let directionX = (Math.random() * 0.3) - 0.15;
                let directionY = (Math.random() * 0.3) - 0.15;
                particlesArray.push(new Particle(x, y, directionX, directionY, size));
            }
        }

        function connect() {
            for (let a = 0; a < particlesArray.length; a++) {
                for (let b = a; b < particlesArray.length; b++) {
                    let distance = ((particlesArray[a].x - particlesArray[b].x) ** 2)
                                 + ((particlesArray[a].y - particlesArray[b].y) ** 2);
                    
                    if (distance < 180 * 180) {
                        let opacity = 1 - (distance / (180 * 180));
                        // VIJAT ME NGJYRE TE KALTER Elektrike
                        ctx.strokeStyle = `rgba(0, 238, 255, ${opacity * 0.4})`;
                        ctx.lineWidth = 0.8;
                        ctx.shadowBlur = 8; // Shkëlqim Cyan Neon
                        ctx.shadowColor = 'rgba(0, 238, 255, 0.5)';
                        ctx.beginPath();
                        ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                        ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                        ctx.stroke();
                        ctx.shadowBlur = 0;
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
