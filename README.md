<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain Sales | dubrent.com</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Syncopate:wght@700&family=Space+Grotesk:wght@300;400;600;700&display=swap');

        /* STYLE PËR PRELOADER */
        #preloader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.8s ease, visibility 0.8s;
        }

        .loader-text {
            font-family: 'Syncopate', sans-serif;
            color: #fff;
            font-size: 1.5rem;
            letter-spacing: 5px;
            text-transform: lowercase;
            margin-bottom: 20px;
            animation: pulse-glow 2s infinite ease-in-out;
        }

        .loader-bar {
            width: 200px;
            height: 2px;
            background: rgba(255,255,255,0.1);
            position: relative;
            overflow: hidden;
            border-radius: 10px;
        }

        .loader-progress {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, #00f2ff, transparent);
            animation: loading-scan 1.5s infinite ease;
        }

        @keyframes pulse-glow {
            0%, 100% { opacity: 0.5; text-shadow: 0 0 10px rgba(0,242,255,0); }
            50% { opacity: 1; text-shadow: 0 0 20px rgba(0,242,255,0.5); }
        }

        @keyframes loading-scan {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .preloader-hidden {
            opacity: 0;
            visibility: hidden;
        }

        /* STILI EKZISTUES */
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

        .glass-card h2 { color: #fff; font-size: 2rem; margin: 0 0 15px 0; font-weight: 600; }
        .glass-card .domain-line { display: block; margin-bottom: 35px; }
        .glass-card .domain-name { color: rgba(255,255,255,0.8); font-size: 1.1rem; }
        .glass-card .price { font-size: 1.8rem; font-weight: 700; color: #fff; }

        .next-btn {
            display: block; width: 100%; padding: 20px; background: #fff; color: #000;
            text-decoration: none; font-weight: 600; border-radius: 20px;
            transition: all 0.3s ease; text-align: center;
        }

        .contact-info { color: rgba(255,255,255,0.5); font-size: 0.9rem; margin-top: 40px; text-align: center; }
        .phone-link { color: #fff; text-decoration: none; font-size: 1.4rem; font-weight: 600; display: block; margin-top: 10px; }

        .info-panel { text-align: left; color: #fff; }
        .info-domain { font-family: 'Syncopate', sans-serif; font-size: 3.5rem; text-transform: lowercase; }
        .info-status { font-size: 1.6rem; opacity: 0.8; letter-spacing: 3px; }

        .trust-list { display: flex; flex-direction: column; gap: 20px; margin-top: 20px; }
        .trust-item { display: flex; align-items: center; gap: 15px; color: rgba(255,255,255,0.8); }
        .trust-item span { color: #00f2ff; }

        @media (max-width: 1000px) {
            .main-wrapper { flex-direction: column; gap: 40px; padding-bottom: 40px; }
            .info-panel { text-align: center; }
            .glass-card { width: 90%; padding: 40px; }
        }
    </style>
</head>
<body>

    <div id="preloader">
        <div class="loader-text">dubinv.com</div>
        <div class="loader-bar">
            <div class="loader-progress"></div>
        </div>
    </div>

    <canvas id="canvas"></canvas>

    <div class="main-wrapper">
        <div class="glass-card">
            <div class="badge-container">
                <div class="badge verified-badge"><span class="material-icons">verified</span> verified</div>
                <div class="badge premium-badge"><span class="material-icons">stars</span> premium domain</div>
            </div>

            <h2>Buy Now</h2>
            <div class="domain-line">
                <p class="domain-name">dubinv.com is for sale now</p>
                <p class="price">20,000 USD</p>
            </div>
            
            <a href="VENDO_LINKUN_TËND" class="next-btn">Next</a>
            
            <div class="contact-info">
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
        // SCRIPT PËR PRELOADER
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('preloader').classList.add('preloader-hidden');
            }, 1500); // Faqja hapet pas 1.5 sekondash
        });

        // SCRIPT PËR CANVAS (3D BUBBLES)
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            init();
        });

        class Bubble {
            constructor() { this.init(); }
            init() {
                this.radius = Math.random() * 80 + 20;
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.vx = (Math.random() - 0.5) * 0.5;
                this.vy = (Math.random() - 0.5) * 0.5;
                this.opacity = Math.random() * 0.15 + 0.05;
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                const g = ctx.createRadialGradient(this.x-this.radius/3, this.y-this.radius/3, this.radius/10, this.x, this.y, this.radius);
                g.addColorStop(0, `rgba(255, 255, 255, ${this.opacity + 0.1})`);
                g.addColorStop(1, 'rgba(255, 255, 255, 0.01)');
                ctx.fillStyle = g;
                ctx.fill();
            }
            update() {
                this.x += this.vx; this.y += this.vy;
                if (this.x < -this.radius) this.x = canvas.width + this.radius;
                if (this.x > canvas.width + this.radius) this.x = -this.radius;
                if (this.y < -this.radius) this.y = canvas.height + this.radius;
                if (this.y > canvas.height + this.radius) this.y = -this.radius;
            }
        }

        const bubbles = [];
        function init() {
            bubbles.length = 0;
            for (let i = 0; i < 15; i++) { bubbles.push(new Bubble()); }
        }
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            bubbles.forEach(b => { b.update(); b.draw(); });
            requestAnimationFrame(animate);
        }
        init();
        animate();
    </script>
</body>
</html>
