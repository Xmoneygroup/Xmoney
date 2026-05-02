<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>X-Stealth Night Rider | Ultra High Quality</title>
    <style>
        body { margin: 0; background: #000; overflow: hidden; font-family: 'Orbitron', sans-serif; cursor: none; }
        #game-ui { position: absolute; top: 20px; left: 20px; color: #fff; z-index: 10; pointer-events: none; }
        .score-val { font-size: 32px; font-weight: 900; text-shadow: 0 0 20px #00f2ff; }
        canvas { display: block; }
    </style>
</head>
<body>

    <div id="game-ui">
        <div style="letter-spacing: 3px; font-size: 12px; opacity: 0.7;">VELOCITY ASSET</div>
        <div class="score-val" id="score">0000</div>
    </div>

    <canvas id="renderCanvas"></canvas>

    <script>
        const canvas = document.getElementById('renderCanvas');
        const ctx = canvas.getContext('2d');
        const scoreEl = document.getElementById('score');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let score = 0;
        let frame = 0;
        let speed = 8;
        let gameActive = true;

        const mouse = { x: canvas.width / 2, y: canvas.height / 2 };

        // Krijo efektin e tunelit (Grid)
        const lines = [];
        for(let i = 0; i < 20; i++) {
            lines.push({ z: i * 50 });
        }

        const obstacles = [];

        function drawPlayer(x, y) {
            ctx.save();
            ctx.translate(x, y);
            ctx.strokeStyle = '#fff';
            ctx.lineWidth = 5;
            ctx.shadowBlur = 20;
            ctx.shadowColor = '#00f2ff';

            // Logoja jote X agresive
            ctx.beginPath();
            ctx.moveTo(-25, -25); ctx.lineTo(25, 25);
            ctx.moveTo(25, -25); ctx.lineTo(-25, 25);
            ctx.stroke();

            // Efekti i dritës poshtë logos (Underglow)
            ctx.globalAlpha = 0.3;
            ctx.fillStyle = '#00f2ff';
            ctx.beginPath();
            ctx.ellipse(0, 40, 30, 10, 0, 0, Math.PI * 2);
            ctx.fill();
            ctx.restore();
        }

        function animate() {
            if(!gameActive) return;
            frame++;
            ctx.fillStyle = '#000';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // 1. Vizato Tunelin Neon
            ctx.strokeStyle = 'rgba(0, 242, 255, 0.2)';
            ctx.lineWidth = 1;
            lines.forEach(l => {
                l.z -= speed;
                if(l.z <= 0) l.z = 1000;
                
                let scale = 400 / l.z;
                let size = 2000 * scale;
                ctx.strokeRect(canvas.width/2 - size/2, canvas.height/2 - size/2, size, size);
            });

            // 2. Menaxho Pengesat (Cyber Blocks)
            if(frame % 40 === 0) {
                obstacles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    z: 1000,
                    size: 50 + Math.random() * 100
                });
            }

            obstacles.forEach((o, i) => {
                o.z -= speed;
                let scale = 400 / o.z;
                let x = (o.x - canvas.width/2) * scale + canvas.width/2;
                let y = (o.y - canvas.height/2) * scale + canvas.height/2;
                let s = o.size * scale;

                if(o.z > 0) {
                    ctx.fillStyle = `rgba(255, 0, 85, ${1 - o.z/1000})`;
                    ctx.shadowBlur = 15;
                    ctx.shadowColor = '#ff0055';
                    ctx.fillRect(x - s/2, y - s/2, s, s);

                    // Kontrollo përplasjen kur pengesa është afër "kamerës"
                    if(o.z < 50 && Math.abs(x - mouse.x) < s/2 + 20 && Math.abs(y - mouse.y) < s/2 + 20) {
                        gameActive = false;
                        alert("X-SYSTEM CRASHED! SCORE: " + score);
                        location.reload();
                    }
                } else {
                    obstacles.splice(i, 1);
                    score += 100;
                    scoreEl.innerText = score.toString().padStart(4, '0');
                }
            });

            // 3. Vizato Lojtarin
            drawPlayer(mouse.x, mouse.y);

            speed += 0.001; // Rrit vështirësinë
            requestAnimationFrame(animate);
        }

        window.addEventListener('mousemove', e => {
            mouse.x = e.clientX;
            mouse.y = e.clientY;
        });

        animate();
    </script>
</body>
</html>
