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

        nav ul { 
            display: flex; 
            gap: 30px; 
            align-items: center;
        }
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

        .hero {
            height: 85vh;
            background: radial-gradient(circle at center, #1a2236 0%, var(--bg-dark) 70%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 100px 20px 0 20px;
            position: relative;
        }
        .hero::after {
            content: "";
            position: absolute; bottom: 0; left: 0; width: 100%; height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent-electric), transparent);
            box-shadow: 0 0 15px var(--accent-electric);
        }

        .hero h1 {
            font-size: 65px;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 5px;
            font-weight: 900;
            background: linear-gradient(to bottom, #fff, #bbb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .hero h1 span { -webkit-text-fill-color: var(--accent-electric); }
        .hero p { font-size: 18px; color: var(--text-muted); max-width: 650px; margin-bottom: 40px; }

        .services-dashboard {
            padding: 80px 50px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
            background-color: var(--bg-dark);
        }

        .service-panel {
            background-color: var(--bg-panel);
            border: 1px solid rgba(255,255,255,0.03);
            border-radius: 12px;
            padding: 40px;
            transition: 0.4s;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
        .service-panel:hover {
            border-color: var(--accent-electric);
            transform: translateY(-8px);
        }

        .service-panel h3 {
            font-size: 24px;
            text-transform: uppercase;
            color: var(--text-main);
            margin: 0 0 20px 0;
            font-weight: 800;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        .service-panel h3::before {
            content: ""; display: inline-block; width: 4px; height: 24px; background-color: var(--accent-electric);
        }

        .diagnostike-tech {
            background-color: var(--bg-panel);
            padding: 100px 50px;
            display: flex;
            align-items: center;
            gap: 60px;
            border-top: 1px solid rgba(255,255,255,0.03);
        }

        .diag-visual {
            flex: 1;
            background-color: rgba(0,0,0,0.2);
            border-radius: 12px;
            padding: 30px;
            height: 320px;
            border: 1px solid rgba(255,255,255,0.05);
            display: flex; align-items: center; justify-content: center;
        }
        .diag-visual svg { width: 100%; height: 100%; }

        .diag-text { flex: 1.2; }
        .diag-text h2 { text-transform: uppercase; color: var(--text-main); font-size: 36px; font-weight: 900; margin-bottom: 20px; }
        .diag-text h2 span { color: var(--accent-electric); }

        footer {
            background-color: var(--bg-dark);
            padding: 70px 50px;
            border-top: 1px solid rgba(255,255,255,0.03);
            text-align: center;
        }

        .contact-card {
            background-color: var(--bg-panel);
            padding: 40px;
            border-radius: 12px;
            display: inline-block;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .contact-name { font-size: 22px; font-weight: 800; color: var(--text-main); margin-bottom: 10px; }
        .contact-phone { font-size: 28px; color: var(--accent-electric); font-family: monospace; font-weight: bold; }

        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 15px; }
            .hero h1 { font-size: 38px; }
            .diagnostike-tech { flex-direction: column; text-align: center; }
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
        <h1>UNI<span>KEY</span></h1>
        <p>Specialistë të çertifikuar për kodimin e çelësave inteligjentë, diagnostikë kompjuterike dhe riparimin e bravave.</p>
        <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
    </section>

    <section id="sherbimet" class="services-dashboard">
        <div class="service-panel">
            <h3>Kodim Çelësash</h3>
            <p>Programim profesional i Smart Keys dhe telekomandave për të gjitha markat e makinave.</p>
            <a href="tel:+389070229348" style="color: var(--accent-electric); font-weight: bold;">Na kontaktoni →</a>
        </div>
        <div class="service-panel">
            <h3>Mekanizma</h3>
            <p>Riparim i mekanizmave të dritareve dhe bravave elektrike me garanci.</p>
            <a href="tel:+389070229348" style="color: var(--accent-electric); font-weight: bold;">Na kontaktoni →</a>
        </div>
        <div class="service-panel">
            <h3>Brava Makinash</h3>
            <p>Hapje emergjente pa dëmtim dhe ndërrim i bravave të sigurisë.</p>
            <a href="tel:+389070229348" style="color: var(--accent-electric); font-weight: bold;">Na kontaktoni →</a>
        </div>
    </section>

    <section id="diagnostike" class="diagnostike-tech">
        <div class="diag-visual">
            <svg viewBox="0 0 400 150" xmlns="http://www.w3.org/2000/svg">
                <path d="M0,75 L400,75" stroke="rgba(255,255,255,0.05)" stroke-width="1"/>
                <path d="M0,75 L50,75 L60,30 L70,120 L80,75 L150,75 L160,50 L170,100 L180,75 L250,75 L260,10 L270,140 L280,75 L350,75 L360,60 L370,90 L380,75 L400,75" 
                      stroke="#00f2fe" stroke-width="3" fill="none" stroke-linecap="round" stroke-linejoin="round">
                      <animate attributeName="stroke-dasharray" from="0,1000" to="1000,0" dur="3s" repeatCount="indefinite" />
                </path>
            </svg>
        </div>
        <div class="diag-text">
            <h2>Diagnostikë <span>Kompjuterike</span></h2>
            <p>Zbulim i gabimeve elektronike me pajisjet më të fundit diagnoistike në treg.</p>
        </div>
    </section>

    <footer id="kontakt">
        <div class="contact-card">
            <div class="contact-name">Muhamed Musli</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>
        <p style="margin-top: 40px; font-size: 12px; color: #444;">&copy; 2026 UNIKEY. All rights reserved.</p>
    </footer>

</body>
</html>
