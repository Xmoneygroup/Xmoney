/* ==========================================
   BACKGROUND LAYERED NEBULA + PARTICLE ANIMATION
========================================== */

body {
    margin: 0;
    padding: 0;
    font-family: 'Montserrat', sans-serif;
    overflow-x: hidden;
    color: #fff;
    background: #000;
    position: relative;
}

/* --- Nebula gradient i fuqishëm --- */
body::before {
    content: "";
    position: fixed;
    inset: 0;
    
    background:
        radial-gradient(circle at 25% 20%, rgba(120, 0, 255, 0.8), transparent 60%),
        radial-gradient(circle at 75% 80%, rgba(0, 120, 255, 0.7), transparent 70%),
        radial-gradient(circle at 50% 50%, rgba(255, 0, 100, 0.4), transparent 80%);
    
    filter: blur(90px);
    animation: nebulaMove 18s ease-in-out infinite alternate;
    z-index: -3;
}

@keyframes nebulaMove {
    0% { transform: scale(1) translate(0,0); }
    100% { transform: scale(1.4) translate(-80px, 60px); }
}

/* --- Yje të animuar (Particle Field) --- */
body::after {
    content: "";
    position: fixed;
    inset: 0;
    background-image: url("https://www.transparenttextures.com/patterns/stardust.png");
    opacity: 0.22;
    animation: starDrift 26s linear infinite;
    z-index: -1;
}

@keyframes starDrift {
    from { transform: translateY(0); }
    to   { transform: translateY(-500px); }
}

/* ==========================================
   TITULLI — WAVE NEON PULSE + CHROME STYLE
========================================== */

.hero-text {
    font-family: 'Cinzel', serif;
    font-size: 110px;
    font-weight: 900;
    letter-spacing: 4px;
    margin: 60px 0 0 50px;

    background: linear-gradient(90deg, #ffffff, #ad7cff, #7b2ff7, #ffffff);
    background-clip: text;
    -webkit-text-fill-color: transparent;

    filter: drop-shadow(0 0 20px #6a00ff) drop-shadow(0 0 45px #9d4edd);

    opacity: 0;
    transform: translateY(60px) scale(0.85);
    animation: heroIn 2s cubic-bezier(.17,.67,.83,.67) forwards,
               glowPulse 7s ease-in-out infinite alternate;
}

@keyframes heroIn {
    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }
}

@keyframes glowPulse {
    0% { filter: drop-shadow(0 0 20px #6a00ff); }
    100% { filter: drop-shadow(0 0 50px #c77dff); }
}

/* ==========================================
   SUBTEXT — SMOOTH FLOAT FADE
========================================== */

.subtext {
    font-size: 24px;
    font-weight: 300;
    max-width: 700px;
    margin: 25px 0 0 55px;
    opacity: 0;
    animation: subAppear 3.3s ease forwards 0.7s;
    transform: translateY(40px);
}

@keyframes subAppear {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ==========================================
   CARDS — ULTRA GLASS 3D PARALLAX
========================================== */

.cards {
    margin-top: 120px;
    display: flex;
    justify-content: center;
    gap: 40px;
}

.card {
    width: 330px;
    height: 330px;

    background: rgba(255, 255, 255, 0.10);
    border-radius: 20px;
    padding: 30px;

    backdrop-filter: blur(16px) saturate(180%);
    box-shadow: 0 0 25px rgba(0,0,0,0.6), inset 0 0 25px rgba(255,255,255,0.1);

    transform-style: preserve-3d;
    transition: 0.5s ease;
}

.card:hover {
    transform: rotateX(12deg) rotateY(-12deg) translateY(-20px) scale(1.03);
    box-shadow: 0 0 50px rgba(120,0,255,0.6),
                0 0 90px rgba(0,200,255,0.4);
}

/* ==========================================
   BUTTON — LASER NEON BEAM
========================================== */

.btn {
    margin-top: 20px;
    padding: 14px 0;
    width: 100%;
    text-decoration: none;
    border-radius: 10px;
    font-size: 18px;
    font-weight: 700;

    background: linear-gradient(90deg, #00ffcc, #00bfff);
    box-shadow: 0 0 12px #00e6b8, 0 0 32px #00e6ff;
    color: #000;

    transition: 0.33s ease;
}

.btn:hover {
    background: linear-gradient(90deg, #00ffe6, #52e0ff);
    box-shadow: 0 0 35px #00fff0, 0 0 70px #00ccff;
    transform: scale(1.08);
}
