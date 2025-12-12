<!DOCTYPE html>
<html lang="en">
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Premium Xmoney - Business Success</title>
<style>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700&family=Cinzel:wght@600;700&display=swap');

    body {
        margin: 0;
        padding: 0;
        font-family: 'Montserrat', sans-serif;
        background: radial-gradient(circle at 20% 20%, #3a0ca3, #1a0933 40%, #000000 80%),
                    radial-gradient(circle at 80% 80%, #4361ee, #1b1b2f 50%, #000000 90%);
        background-blend-mode: screen;
        background-attachment: fixed;
        position: relative;
        color: #fff;
        overflow-x: hidden;
    }

    body::before {
        content: "";
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: url("https://www.transparenttextures.com/patterns/stardust.png");
        opacity: 0.25;
        pointer-events: none;
    }

    .hero-text {
        font-family: 'Cinzel', serif;
        font-size: 90px;
        font-weight: 700;
        margin: 40px 0 0 50px;
        color: #ffffff;
        text-shadow:
            0 0 12px #637bff,
            0 0 30px #4c5bff,
            0 0 45px #3a0ca3,
            0 0 70px #3a0ca3;
        opacity: 0;
        animation: glowAppear 1.3s ease-out forwards, glowPulse 3s infinite ease-in-out;
        position: relative;
    }

    @keyframes glowAppear {
        0% { opacity: 0; transform: translateY(-40px) scale(0.85); }
        100% { opacity: 1; transform: translateY(0) scale(1); }
    }

    @keyframes glowPulse {
        0%, 100% {
            text-shadow:
                0 0 12px #637bff,
                0 0 30px #4c5bff,
                0 0 45px #3a0ca3,
                0 0 70px #3a0ca3;
        }
        50% {
            text-shadow:
                0 0 18px #7d8dff,
                0 0 40px #6c7cff,
                0 0 65px #5b4cff,
                0 0 90px #4a2acc;
        }
    }

    .hero-text::after {
        content: "";
        position: absolute;
        top: 0;
        left: -120%;
        width: 120%;
        height: 100%;
        background: linear-gradient(120deg, transparent, rgba(255,255,255,0.5), transparent);
        transform: skewX(-25deg);
        animation: shine 3.5s ease-in-out infinite;
    }

    @keyframes shine {
        0% { left: -120%; }
        60% { left: 120%; }
        100% { left: 120%; }
    }

    .subtext {
        font-size: 22px;
        font-weight: 300;
        max-width: 700px;
        margin: 20px 0 0 55px;
        line-height: 1.6;
        opacity: 0;
        transform: translateX(-120px);
        animation: fadeText 5s ease-out forwards;
    }

    @keyframes fadeText {
        0% { opacity: 0; transform: translateX(-120px); }
        100% { opacity: 1; transform: translateX(0); }
    }

    .cards {
        display: flex;
        justify-content: center;
        gap: 35px;
        margin-top: 100px;
        flex-wrap: nowrap;
    }

    .card {
        background: rgba(255, 255, 255, 0.15);
        padding: 30px;
        width: 330px;
        height: 300px;
        border-radius: 18px;
        backdrop-filter: blur(12px);
        box-shadow: 0 10px 30px rgba(0,0,0,0.6);
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
    }

    .card:hover {
        transform: translateY(-12px);
        box-shadow: 0 15px 35px rgba(0,0,0,0.7);
    }

    .btn {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        padding: 15px 0;
        background-color: #28a745;
        color: white;
        text-decoration: none;
        border-radius: 10px;
        font-size: 16px;
        font-weight: bold;
        transition: background 0.3s ease;
    }

    .btn:hover {
        background-color: #218838;
    }

    /* --- INSTAGRAM BUTTON SUPER I VOGEL + ANIMACION --- */
    .insta-btn {
        position: fixed;
        top: 20px;
        right: 25px;
        width: 45px;
        height: 45px;
        background: transparent; /* heq ngjyrën e kuqe */
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: none; /* heq glow-in e kuqe */
        transition: transform 0.3s ease;
        animation: fadeInButton 1.5s ease-out;
        cursor: pointer;
    }

    .insta-btn:hover {
        transform: scale(1.18);
        box-shadow: 0 0 18px rgba(255, 0, 120, 1);
    }

    @keyframes pulseInsta {
        0%, 100% { box-shadow: 0 0 12px rgba(255, 0, 120, 0.7); }
        50% { box-shadow: 0 0 22px rgba(255, 0, 120, 1); }
    }

    .insta-btn img {
        width: 60%;
        filter: brightness(0) invert(1);
    }
</style>

<body>

    <!-- BUTONI I INSTAGRAMIT -->
    <a class="insta-btn" href="https://www.instagram.com/xmoney.s?igsh=bnR6d2x2dTJ0bG5s&utm_source=qr" target="_blank">
        <img src="https://cdn-icons-png.flaticon.com/512/174/174855.png" style="width:70%; filter: invert(1);" />
    </a>

    <div class="hero-text">Xmoney</div>

    <div class="subtext">
        We have dominated the market for nearly 5 years and have the potential to bring many clients through these 3 options. Options 2 and 3 are the key to your business success.
    </div>

    <div class="cards">
        <div class="card">
            <h2>2 Business Logos – $5</h2>
            <p>Get high-quality, professional logos for your brand.</p>
            <a class="btn" href="https://whop.com/checkout/plan_Bg7KX3vyIVGjk">BUY NOW</a>
        </div>

        <div class="card">
            <h2>10 Business Growth Ideas – $10</h2>
            <p>Boost your business with creative and actionable strategies.</p>
            <a class="btn" href="https://whop.com/checkout/plan_w3oZUMd5R30D1">BUY NOW</a>
        </div>

        <div class="card">
            <h2>1 Professional 30s Video – $10</h2>
            <p>Create a compelling video that attracts more clients.</p>
            <a class="btn" href="https://whop.com/checkout/plan_HglKg8iMbKz5I">BUY NOW</a>
        </div>
    </div>

</body>
</html>
