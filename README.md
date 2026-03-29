
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Professional Auto Locksmith</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #FFD700;
            --gold-glow: rgba(255, 215, 0, 0.4);
            --dark-bg: #020202;
            --glass: rgba(255, 255, 255, 0.03);
            --border-glass: rgba(255, 255, 255, 0.1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--dark-bg);
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* NEON FALLING KEYS BACKGROUND */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at 50% 50%, #0a0a0a 0%, #000 100%);
            overflow: hidden;
        }

        .falling-key {
            position: absolute;
            color: var(--gold);
            font-size: 25px;
            filter: drop-shadow(0 0 8px var(--gold));
            user-select: none;
            pointer-events: none;
            opacity: 0.6;
            animation: fallAndRotate linear forwards;
        }

        @keyframes fallAndRotate {
            0% { transform: translateY(-100px) rotate(0deg); opacity: 0; }
            10% { opacity: 0.6; }
            90% { opacity: 0.6; }
            100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
        }

        .header-nav {
            display: flex;
            justify-content: flex-end;
            padding: 25px 5%;
            position: relative;
            z-index: 10;
        }

        .btn-translate {
            background: rgba(0,0,0,0.5);
            color: var(--gold);
            border: 1px solid var(--gold);
            padding: 10px 25px;
            font-family: 'Orbitron', sans-serif;
            cursor: pointer;
            transition: 0.4s;
            letter-spacing: 2px;
            backdrop-filter: blur(5px);
        }

        .btn-translate:hover {
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 30px var(--gold-glow);
        }

        .main-wrapper {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
            text-align: center;
            position: relative;
        }

        .luxury-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(3.5rem, 12vw, 7rem);
            color: #fff;
            letter-spacing: 15px;
            margin-bottom: 40px;
            text-shadow: 0 10px 30px rgba(0,0,0,0.5);
            background: linear-gradient(to bottom, #fff 30%, var(--gold) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: titleGlow 3s infinite alternate;
        }

        @keyframes titleGlow {
            from { filter: drop-shadow(0 0 5px rgba(255,255,255,0.2)); }
            to { filter: drop-shadow(0 0 20px var(--gold-glow)); }
        }

        .info-card {
            background: var(--glass);
            border: 1px solid var(--border-glass);
            backdrop-filter: blur(20px);
            padding: 40px;
            text-align: left;
            margin-bottom: 50px;
            border-left: 5px solid var(--gold);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .info-list { list-style: none; }
        .info-list li {
            font-size: 1.3rem;
            margin-bottom: 25px;
            display: flex;
            align-items: flex-start;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            padding-bottom: 12px;
        }

        .info-list li::before {
            content: '✦';
            color: var(--gold);
            margin-right: 15px;
            text-shadow: 0 0 10px var(--gold);
        }

        /* RENDITJA 3 ME 3 */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr); 
            gap: 20px;
            margin-bottom: 60px;
        }

        @media (max-width: 768px) {
            .gallery-grid {
                grid-template-columns: 1fr;
            }
        }

        .img-box {
            height: 350px;
            background: #000;
            border: 1px solid var(--border-glass);
            overflow: hidden;
            position: relative;
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
        }

        .img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 1.2s cubic-bezier(0.2, 1, 0.3, 1);
            filter: grayscale(20%);
        }

        .img-box:hover img {
            transform: scale(1.1);
            filter: grayscale(0%);
        }

        .rating-container {
            background: rgba(10,10,10,0.8);
            border: 1px solid var(--border-glass);
            padding: 50px;
            backdrop-filter: blur(10px);
            border-top: 3px solid var(--gold);
        }

        .star { cursor: pointer; font-size: 3rem; color: #1a1a1a; transition: 0.3s; }
        .star.active { color: var(--gold); text-shadow: 0 0 20px var(--gold); }

        textarea {
            width: 100%;
            padding: 20px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-glass);
            color: white;
            margin-top: 25px;
            font-family: 'Rajdhani';
            font-size: 1.1rem;
            resize: none;
        }

        .btn-submit {
            background: linear-gradient(45deg, #B8860B, var(--gold));
            border: none;
            padding: 18px 50px;
            font-weight: bold;
            cursor: pointer;
            font-family: 'Orbitron';
            margin-top: 30px;
            letter-spacing: 3px;
            color: #000;
        }
    </style>
</head>
<body>

<div id="bg-canvas"></div>

<nav class="header-nav">
    <button class="btn-translate" onclick="toggleLanguage()">English Version</button>
</nav>

<div class="main-wrapper">
    <h1 class="luxury-title">UNIKEY</h1>

    <div class="info-card">
        <ul class="info-list" id="content-list">
            <li data-sq="17 vite eksperiencë profesionale." data-en="17 years of professional experience.">17 vite eksperiencë profesionale.</li>
            <li data-sq="E Hënë - E Shtunë | 09:30 - 19:00" data-en="Monday - Saturday | 09:30 - 19:00">E Hënë - E Shtunë | 09:30 - 19:00</li>
            <li data-sq="Brava makinash • Qelsa duplikat • Kodime • Diagnostikë" data-en="Car locks • Duplicate keys • Coding • Diagnostics">Brava makinash • Qelsa duplikat • Kodime • Diagnostikë</li>
            <li data-sq="Lokacioni: Gjorce Petrov, Maqedoni" data-en="Location: Gjorce Petrov, Macedonia">Lokacioni: Gjorce Petrov, Maqedoni</li>
            <li data-sq="Kontakt: Muhamet Musliu - +389 70 229 348" data-en="Contact: Muhamed Musliu - +389 70 229 348">Kontakt: Muhamet Musliu - +389 70 229 348</li>
        </ul>
    </div>

    <div class="gallery-grid">
        <div class="img-box"><img src="IMG_0534.jpg" alt="Unikey 1"></div>
        <div class="img-box"><img src="IMG_0535.jpg" alt="Unikey 2"></div>
        <div class="img-box"><img src="IMG_0537.jpg" alt="Unikey 3"></div>
        <div class="img-box"><img src="IMG_0536.jpg" alt="Unikey 4"></div>
        <div class="img-box"><img src="IMG_0539.jpg" alt="Unikey 5"></div>
        <div class="img-box"><img src="IMG_0540.jpg" alt="Unikey 6"></div>
        <div class="img-box"><img src="IMG_0541.jpg" alt="Unikey 7"></div>
        <div class="img-box"><img src="IMG_0542.jpg" alt="Unikey 8"></div>
        <div class="img-box"><img src="IMG_0543.jpg" alt="Unikey 9"></div>
    </div>

    <div class="rating-container">
        <h2 id="rate-title" style="font-family:'Orbitron'; color: var(--gold); letter-spacing: 3px;">VLERSONI SHERBIMIN TONË</h2>
        <div class="stars">
            <span class="star" onclick="setStar(1)">★</span>
            <span class="star" onclick="setStar(2)">★</span>
            <span class="star" onclick="setStar(3)">★</span>
            <span class="star" onclick="setStar(4)">★</span>
            <span class="star" onclick="setStar(5)">★</span>
        </div>
        <textarea id="feedback" rows="4" placeholder="Lini mbresat tuaja..."></textarea>
        <button class="btn-submit" onclick="alert('Faleminderit Muhamet!')">DËRGO</button>
    </div>
</div>

<script>
const canvas = document.getElementById('bg-canvas');
const keyIcons = ['🔑', '🗝️', '🏠', '🔓'];

// ANIMACIONI I CELsave QE BIEN
function createFallingKey() {
    const key = document.createElement('div');
    key.className = 'falling-key';
    key.innerText = keyIcons[Math.floor(Math.random() * keyIcons.length)];
    
    const startX = Math.random() * 100;
    const duration = Math.random() * 5 + 7; // 7-12 sekonda (avash)
    const size = Math.random() * 15 + 20; // 20-35px
    
    key.style.left = startX + 'vw';
    key.style.fontSize = size + 'px';
    key.style.animationDuration = duration + 's';
    
    canvas.appendChild(key);
    
    setTimeout(() => {
        key.remove();
    }, duration * 1000);
}

// Krijo nje celes cdo 600ms
setInterval(createFallingKey, 600);

let isEn = false;
function toggleLanguage() {
    isEn = !isEn;
    document.querySelectorAll('#content-list li').forEach(li => {
        li.innerText = isEn ? li.getAttribute('data-en') : li.getAttribute('data-sq');
    });
    document.querySelector('.btn-translate').innerText = isEn ? "Versioni Shqip" : "English Version";
}

function setStar(n) {
    document.querySelectorAll('.star').forEach((s, i) => {
        s.classList.toggle('active', i < n);
    });
}
</script>

</body>
</html>
