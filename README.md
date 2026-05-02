<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <title>X-Gold Runner | Stealth Game</title>
    <style>
        body { margin: 0; background: #000; color: #ffd700; font-family: 'Arial', sans-serif; overflow: hidden; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; }
        canvas { border: 2px solid #ffd700; background: #050505; box-shadow: 0 0 20px rgba(255, 215, 0, 0.2); cursor: none; }
        .stats { position: absolute; top: 20px; font-size: 24px; letter-spacing: 2px; text-shadow: 0 0 10px #ffd700; }
        .instructions { position: absolute; bottom: 20px; color: #444; font-size: 14px; }
    </style>
</head>
<body>

    <div class="stats">GOLD COLLECTED: <span id="score">0</span></div>
    <canvas id="gameCanvas"></canvas>
    <div class="instructions">Lëviz mausin për të kontrolluar "X". Mblidh Arin, shmang të Kuqet!</div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const scoreElement = document.getElementById('score');

        canvas.width = 800;
        canvas.height = 500;

        let score = 0;
        let gameActive = true;

        const player = { x: 400, y: 450, size: 40 };
        const items = [];

        // Krijo objektet (Ar ose Rrezik)
        function createItem() {
            const isGold = Math.random() > 0.3;
            items.push({
                x: Math.random() * (canvas.width - 20),
                y: -20,
                size: isGold ? 15 : 25,
                speed: 3 + Math.random() * 4,
                color: isGold ? '#ffd700' : '#ff0000',
                type: isGold ? 'gold' : 'danger'
            });
        }

        // Vizato logon "X" agresive (si te screenshot-i yt)
        function drawPlayer(x, y) {
            ctx.strokeStyle = "white";
            ctx.lineWidth = 4;
            ctx.beginPath();
            ctx.moveTo(x - 20, y - 20);
            ctx.lineTo(x + 20, y + 20);
            ctx.moveTo(x + 20, y - 20);
            ctx.lineTo(x - 20, y + 20);
            ctx.stroke();
            // Shkëlqimi Neon
            ctx.shadowBlur = 15;
            ctx.shadowColor = "white";
        }

        function update() {
            if (!gameActive) return;

            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawPlayer(player.x, player.y);

            items.forEach((item, index) => {
                item.y += item.speed;
                
                // Vizato objektet
                ctx.fillStyle = item.color;
                ctx.shadowBlur = 10;
                ctx.shadowColor = item.color;
                ctx.beginPath();
                ctx.arc(item.x, item.y, item.size / 2, 0, Math.PI * 2);
                ctx.fill();

                // Kontrollo përplasjen
                const dist = Math.hypot(player.x - item.x, player.y - item.y);
                if (dist < player.size / 2 + item.size / 2) {
                    if (item.type === 'gold') {
                        score += 10;
                        scoreElement.innerText = score;
                        items.splice(index, 1);
                    } else {
                        gameActive = false;
                        alert("GAME OVER! Pite ari të mbledhura: " + score);
                        location.reload();
                    }
                }

                // Hiqi nese dalin jashte
                if (item.y > canvas.height) items.splice(index, 1);
            });

            if (Math.random() < 0.05) createItem();
            requestAnimationFrame(update);
        }

        window.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            player.x = e.clientX - rect.left;
            player.y = e.clientY - rect.top;
        });

        update();
    </script>
</body>
</html>
