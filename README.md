<canvas id="neuralCanvas"></canvas>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    
    let stars = [];
    let nebulas = [];
    const starCount = 400;
    let mouse = { x: canvas.width / 2, y: canvas.height / 2, active: false };

    window.addEventListener('mousemove', (e) => {
        mouse.x = e.x;
        mouse.y = e.y;
        mouse.active = true;
    });

    function resize() {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        init();
    }
    window.addEventListener("resize", resize);

    class Star {
        constructor() {
            this.reset();
        }
        reset() {
            this.x = (Math.random() - 0.5) * canvas.width * 2;
            this.y = (Math.random() - 0.5) * canvas.height * 2;
            this.z = Math.random() * canvas.width;
            this.pz = this.z;
            this.color = Math.random() > 0.8 ? '#00f2ff' : '#ffffff';
        }
        update() {
            let speed = mouse.active ? 3 : 1;
            this.z -= speed;
            if (this.z < 1) {
                this.reset();
                this.pz = this.z;
            }
        }
        draw() {
            let sx = ((this.x / this.z) * canvas.width/2) + canvas.width/2;
            let sy = ((this.y / this.z) * canvas.height/2) + canvas.height/2;
            let r = (1 - this.z / canvas.width) * 2.5;

            let px = ((this.x / this.pz) * canvas.width/2) + canvas.width/2;
            let py = ((this.y / this.pz) * canvas.height/2) + canvas.height/2;

            ctx.beginPath();
            ctx.strokeStyle = this.color;
            ctx.lineWidth = r;
            ctx.lineCap = 'round';
            ctx.moveTo(px, py);
            ctx.lineTo(sx, sy);
            ctx.stroke();
            
            this.pz = this.z;
        }
    }

    class Nebula {
        constructor(color) {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.r = Math.random() * 300 + 200;
            this.color = color;
            this.vx = (Math.random() - 0.5) * 0.5;
            this.vy = (Math.random() - 0.5) * 0.5;
        }
        update() {
            this.x += this.vx;
            this.y += this.vy;
            if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
            if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
        }
        draw() {
            let gradient = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.r);
            gradient.addColorStop(0, this.color);
            gradient.addColorStop(1, 'transparent');
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, canvas.width, canvas.height);
        }
    }

    function init() {
        stars = [];
        for (let i = 0; i < starCount; i++) stars.push(new Star());
        nebulas = [
            new Nebula('rgba(0, 242, 255, 0.07)'),
            new Nebula('rgba(212, 175, 55, 0.04)'),
            new Nebula('rgba(0, 242, 255, 0.05)')
        ];
    }

    function animate() {
        // Clear with slight motion blur
        ctx.fillStyle = '#050505';
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        // Draw Ambient Nebulas
        ctx.globalCompositeOperation = 'screen';
        nebulas.forEach(n => {
            n.update();
            n.draw();
        });

        // Draw 3D Stars
        stars.forEach(s => {
            s.update();
            s.draw();
        });

        requestAnimationFrame(animate);
    }

    function joinVIP() {
        document.querySelector('.vip-card').style.transform = "scale(0.95)";
    }

    resize();
    animate();
</script>
