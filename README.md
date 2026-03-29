<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Specialist për Çelësa makinash</title>
    <style>
        :root {
            --bg-dark: #06090f; 
            --bg-panel: #0d1117; 
            --accent-blue: #007bff; 
            --accent-electric: #00f2fe; 
            --text-main: #ffffff;
            --text-muted: #8b949e;
            --font-main: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            font-family: var(--font-main);
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            line-height: 1.6;
        }

        a { text-decoration: none; color: inherit; transition: 0.3s; }
        ul { list-style: none; padding: 0; margin: 0; }

        header {
            background-color: rgba(13, 17, 23, 0.95);
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-sizing: border-box;
            border-bottom: 1px solid rgba(255,255,255,0.03);
            backdrop-filter: blur(5px);
        }

        .logo {
            font-size: 28px;
            font-weight: 900;
            color: var(--text-main);
            text-transform: uppercase;
            letter-spacing: 2px;
            font-style: italic;
        }
        .logo span { color: var(--accent-electric); }

        nav ul { display: flex; gap: 30px; align-items: center; }
        nav a { 
            font-size: 13px; 
            text-transform: uppercase; 
            color: var(--text-muted); 
            font-weight: 600; 
            letter-spacing: 1px;
        }
        nav a:hover { color: var(--accent-electric); }

        .contact-btn {
            background-color: var(--accent-blue);
            color: white;
            padding: 10px 25px;
            border-radius: 5px;
            font-weight: bold;
            font-size: 14px;
            text-transform: uppercase;
        }

        /* --- HERO ME PLLAKATËN MAJTAS --- */
        .hero {
            height: 90vh;
            background: radial-gradient(circle at center, #1a2236 0%, var(--bg-dark) 70%);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 100px 8% 0 8%;
            position: relative;
        }

        .hero-left-panel {
            background: rgba(255, 255, 255, 0.03);
            border-left: 3px solid var(--accent-electric);
            padding: 20px;
            max-width: 200px;
            backdrop-filter: blur(10px);
            border-radius: 0 8px 8px 0;
        }
        .hero-left-panel h4 { margin: 0; font-size: 12px; color: var(--accent-electric); text-transform: uppercase; }
        .hero-left-panel p { margin: 5px 0 0 0; font-size: 14px; color: white; font-weight: 600; }

        .hero-content { text-align: center; flex: 1; }
        .hero h1 {
            font-size: 70px;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 5px;
            font-weight: 900;
            background: linear-gradient(to bottom, #fff, #bbb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero h1 span { -webkit-text-fill-color: var(--accent-electric); }

        /* --- DIAGNOSTIKA ME LËVIZJE MODERNE --- */
        .diagnostike-tech {
            background-color: var(--bg-panel);
            padding: 100px 50px;
            display: flex;
            align-items: center;
            gap: 60px;
        }

        .diag-visual {
            flex: 1;
            height: 350px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            background: #05070a;
            border-radius: 15px;
            overflow: hidden;
            border: 1px solid rgba(0, 242, 254, 0.1);
        }

        .pulse-ring {
            position: absolute;
            width: 200px;
            height: 200px;
            border: 2px solid var(--accent-electric);
            border-radius: 50%;
            animation: pulse-animation 2s infinite;
            opacity: 0;
        }
        .pulse-ring:nth-child(2) { animation-delay: 0.5s; }
        .pulse-ring:nth-child(3) { animation-delay: 1s; }

        @keyframes pulse-animation {
            0% { transform: scale(0.5); opacity: 0.8; }
            100% { transform: scale(1.5); opacity: 0; }
        }

        .radar-line {
            position: absolute;
            width: 150px;
            height: 150px;
            background: conic-gradient(from 0deg, transparent, rgba(0, 242, 254, 0.4));
            border-radius: 50%;
            animation: rotate-radar 4s linear infinite;
        }

        @keyframes rotate-radar {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .diag-text h2 { font-size: 40px; text-transform: uppercase; font-weight: 900; }
        .diag-text span { color: var(--accent-electric); }

        /* --- FOOTER KORRIGJUAR --- */
        footer {
            background-color: var(--bg-dark);
            padding: 80px 50px;
            text-align: center;
            border-top: 1px solid rgba(255,255,255,0.03);
        }

        .contact-card {
            background-color: var(--bg-panel);
            padding: 40px;
            border-radius: 12px;
            display: inline-block;
            border: 1px solid rgba(0, 242, 254, 0.2);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .contact-name { font-size: 24px; font-weight: 800; color: white; margin-bottom: 5px; }
        .contact-phone { font-size: 28px; color: var(--accent-electric); font-weight: bold; }

        /* --- SERVICES --- */
        .services-dashboard {
            padding: 80px 50px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        .service-panel {
            background: var(--bg-panel);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: 0.3s;
        }
        .service-panel:hover { border-color: var(--accent-electric); transform: translateY(-5px); }

        @media (max-width: 768px) {
            .hero { flex-direction: column; text-align: center; padding-top: 150px; }
            .hero-left-panel { display: none; }
            .diagnostike-tech { flex-direction: column; }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">UNI<span>KEY</span></div>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#sherbimet">Shërbimet</a></li>
                <li><a href="#diagnostike">Diagnostikë</a></li>
                <li><a href="#kontakt">Kontakt</a></li>
            </ul>
        </nav>
        <a href="tel:+389070229348" class="contact-btn">TELEFONO</a>
    </header>

    <section id="home" class="hero">
        <div class="hero-left-panel">
            <h4>Teknologjia 2026</h4>
            <p>Sisteme inteligjente për çdo makinë</p>
        </div>
        
        <div class="hero-content">
            <h1>UNI<span>KEY</span></h1>
            <p style="max-width: 600px; margin: 0 auto 30px auto; color: var(--text-muted);">Specialistë të çertifikuar për kodimin e çelësave, diagnostikë dhe riparime moderne.</p>
            <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
        </div>

        <div style="width: 200px;"></div> <!-- Hapësirë për balancim -->
    </section>

    <section id="sherbimet" class="services-dashboard">
        <div class="service-panel">
            <h3>Kodim Çelësash</h3>
            <p>Programim profesional i Smart Keys dhe telekomandave për çdo model.</p>
        </div>
        <div class="service-panel">
            <h3>Mekanizma</h3>
            <p>Riparim i dritareve elektrike dhe brava kompjuterike.</p>
        </div>
        <div class="service-panel">
            <h3>Hapje Emergjente</h3>
            <p>Hapje e makinave të bllokuara pa asnjë dëmtim fizik.</p>
        </div>
    </section>

    <section id="diagnostike" class="diagnostike-tech">
        <div class="diag-visual">
            <div class="radar-line"></div>
            <div class="pulse-ring"></div>
            <div class="pulse-ring"></div>
            <div class="pulse-ring"></div>
            <div style="color: var(--accent-electric); font-weight: bold; z-index: 5;">SCANNING...</div>
        </div>
        <div class="diag-text">
            <h2>Diagnostikë <span>Kompjuterike</span></h2>
            <p>Zbulim i saktë i gabimeve elektronike me sistemet më të fundit në treg.</p>
        </div>
    </section>

    <footer id="kontakt">
        <div class="contact-card">
            <div class="logo" style="margin-bottom: 20px;">UNI<span>KEY</span></div>
            <div class="contact-name">Muhamed Musli</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>
        <p style="margin-top: 40px; font-size: 12px; color: #444;">&copy; 2026 UNIKEY. ALL RIGHTS RESERVED.</p>
    </footer>

</body>
</html>
