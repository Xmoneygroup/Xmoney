<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xmoney | Private Wealth Group</title>
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Montserrat:wght@300;400;600;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #d4af37;
            --cyan: #00f2ff;
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { 
            background: #000; 
            color: white; 
            font-family: 'Montserrat', sans-serif; 
            overflow-x: hidden;
            cursor: crosshair;
        }

       <canvas id="neuralCanvas"></canvas>

<div class="hero">
    <div class="status-container">
        <div class="status-pill"><div class="dot"></div> PROTOCOL: LIVE</div>
        <div class="status-pill">X-ACCESS: GRANTED</div>
    </div>

    <div class="title-wrapper">
        <h1 class="title">Xmoney</h1>
    </div>
    
    <div class="manifesto-container">
        <p class="manifesto-text" style="animation-delay: 0.4s">
            The market has <span class="highlight-cyan">zero mercy</span>. Join the circle that controls the outcome.
        </p>
        <p class="manifesto-text" style="animation-delay: 0.6s">
            Access the <span class="highlight-cyan">VIP Terminal</span>. Real-time data, institutional strategy.
        </p>
    </div>

    <div class="vip-card" id="vipCard">
        <div class="verified-badge">Elite Membership</div>
        <ul class="features-list">
            <li><span>Daily Signals</span> <span class="highlight-cyan">3+ ALERTS</span></li>
            <li><span>Success Rate</span> <span class="highlight-cyan">60% VERIFIED</span></li>
            <li><span>Encryption</span> <span class="highlight-cyan">AES-256</span></li>
        </ul>
        <a href="https://whop.com/xmoney-1/xmoney-ed/" class="join-btn" onclick="joinVIP()">Instant Access</a>
    </div>
</div>

<script>
    const canvas = document.getElementById("neuralCanvas");
    const ctx = canvas.getContext("2d");
    let w, h;
    let particles = [];
    let tick = 0;
    
    // THE 4K DENSITY & INTERACTION SETUP
    const properties = {
        particleCount: 2000,    // Increased count for 4K feel
        highSpeed: 0.8,         // Fast drift
        lowSpeed: 0.05,         // Super Slow-Mo drift
        interactionRadius: 150, // Mouse push radius
        baseRadius: 1.2,        // Particle size
        colorCyan: "0, 242, 255",
        colorGold: "212, 175, 55"
    };
    
    // Control speed logic
    let targetSpeed = properties.highSpeed;
    let currentSpeed = properties.highSpeed;

    // INTERACTION LOGIC: The requested Special Slowdown
    const vipCard = document.getElementById("vipCard");
    
    vipCard.addEventListener("mouseenter", () => {
        // Drop to slow speed instantly
        targetSpeed = properties.lowSpeed;
    });
    
    vipCard.addEventListener("mouseleave", () => {
        // Return to fast speed instantly
        targetSpeed = properties.highSpeed;
    });

    // 4K & CANVAS LOGIC
    window.addEventListener("resize", resize);
    function resize() {
        // Handle High-DPI (Retina) displays for 4K look
        const scale = window.devicePixelRatio || 1;
        w = canvas.width = window.innerWidth * scale;
        h = canvas.height = window.innerHeight * scale;
        ctx.scale(scale, scale);
        // Normalize coordinates back to CSS pixels
        w /= scale;
        h /= scale;
        init();
    }

    class Particle {
        constructor() {
            this.init();
        }
        init() {
            this.x = Math.random() * w;
            this.y = Math.random() * h;
            this.vx = (Math.random() - 0.5);
            this.vy = (Math.random() - 0.5);
            this.radius = Math.random() * properties.baseRadius;
            this.color = Math.random() > 0.6 ? properties.colorGold : properties.colorCyan;
        }
        update(speed) {
            // Flow motion
            this.x += this.vx * speed;
            this.y += this.vy * speed;
            
            // Loop boundaries
            if (this.x < 0) this.x = w;
            if (this.x > w) this.x = 0;
            if (this.y < 0) this.y = h;
            if (this.y > h) this.y = 0;
        }
        draw(speedFactor) {
            ctx.beginPath();
            ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
            
            // Dynamic opacity: brighter when moving fast
            let opacity = speedFactor * 0.4 + 0.1;
            ctx.fillStyle = `rgba(${this.color}, ${opacity})`;
            ctx.fill();
        }
    }

    function init() {
        particles = [];
        for (let i = 0; i < properties.particleCount; i++) {
            particles.push(new Particle());
        }
    }

    function animate() {
        tick++;
        // Clear with a slightly lighter black to help trails
        ctx.fillStyle = "#010101";
        ctx.fillRect(0, 0, w, h);

        // Smooth speed interpolation (optional, if you want acceleration rather than instant snap)
        // currentSpeed += (targetSpeed - currentSpeed) * 0.05; // Uncomment for smooth transition
        currentSpeed = targetSpeed; // Keep instant snap for "Special" feel

        // Calculate speed factor for opacity/trail effects (0 to 1)
        const speedFactor = (currentSpeed - properties.lowSpeed) / (properties.highSpeed - properties.lowSpeed);

        particles.forEach(p => {
            p.update(currentSpeed);
            p.draw(speedFactor);
        });

        // Add occasional digital flashes (Light Leaks) for dynamism
        if (tick % 15 === 0 && targetSpeed > properties.lowSpeed) {
            ctx.fillStyle = `rgba(${properties.colorCyan}, 0.05)`;
            ctx.fillRect(0, Math.random() * h, w, 10);
        }

        requestAnimationFrame(animate);
    }

    // Preserve original function
    function joinVIP() { document.querySelector('.vip-card').style.transform = "scale(0.98)"; }
    
    resize();
    animate();
</script>

</body>
</html>

</body>
</html>
