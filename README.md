<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Specialist për Çelësa makinash</title>
    <style>
        /* --- STILI GLOBAL 'DARK TECH' --- */
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

        /* --- HEADER --- */
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
        nav a { font-size: 13px; text-transform: uppercase; color: var(--text-muted); font-weight: 600; letter-spacing: 1px; }
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

        /* --- HERO --- */
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
        .hero h1 span { -webkit-text-fill-color: var(--accent-electric); text-shadow: 0 0 20px rgba(0,242,254,0.5); }
        .hero p { font-size: 18px; color: var(--text-muted); max-width: 650px; margin-bottom: 40px; }

        /* --- SERVICES --- */
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
        .service-panel:hover { border-color: var(--accent-electric); transform: translateY(-8px); }
        .service-panel h3 { font-size: 24px; text-transform: uppercase; color: var(--text-main); margin-bottom: 20px; display: flex; align-items: center; gap: 15px; }
        .service-panel h3::before { content: ""; width: 4px; height: 24px; background-color: var(--accent-electric); }

        /* --- DIAGNOSTIKA --- */
        .diagnostike-tech {
            background-color: var(--bg-panel);
            padding: 100px 50px;
            display: flex;
            align-items: center;
            gap: 60px;
        }
        .diag-visual { flex: 1; height: 320px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.05); display: flex; align-items: center; justify-content: center; }

        /* --- GOOGLE MAPS SECTION --- */
        .map-section {
            padding: 80px 50px;
            background-color: var(--bg-dark);
            text-align: center;
        }
        .map-container {
            max-width: 1000px;
            margin: 0 auto;
            border-radius: 15px;
            overflow: hidden;
            border: 2px solid rgba(0, 242, 254, 0.2);
            box-shadow: 0 0 20px rgba(0, 242, 254, 0.1);
            filter: grayscale(0.5) invert(0.9) contrast(1.2); /* I jep hartes pamje tech/dark */
            transition: 0.5s;
        }
        .map-container:hover { filter: grayscale(0) invert(0) contrast(1); border-color: var(--accent-electric); }
        .map-section h2 { text-transform: uppercase; margin-bottom: 30px; letter-spacing: 2px; }
        .map-section h2 span { color: var(--accent-electric); }

        /* --- FOOTER --- */
        footer {
            background-color: var(--bg-dark);
            padding: 70px 50px 40px 50px;
            border-top: 1px solid rgba(255,255,255,0.03);
            text-align: center;
        }
        .contact-card { background-color: var(--bg-panel); padding: 40px; border-radius: 12px; display: inline-block; border: 1px solid rgba(255,255,255,0.05); }
        .contact-phone { font-size: 28px; color: var(--accent-electric); font-family: monospace; font-weight: bold; }

        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 15px; }
            .hero h1 { font-size: 38px; }
            .map-section { padding: 40px 20px; }
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
        <a href="tel:+389070229348" class="contact-btn">TELEFONO TANI</a>
    </header>

    <section id="home" class="hero">
        <h1>UNI<span>KEY</span></h1>
        <p>Specialistë të çertifikuar për kodimin e çelësave inteligjentë, diagnostikë kompjuterike dhe riparimin e bravave për makina moderne.</p>
        <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
    </section>

    <section id="sherbimet" class="services-dashboard">
        <div class="service-panel">
            <h3>Kodim Çelësash</h3>
            <p>Programim profesional i çelësave inteligjentë (Smart Keys) për të gjitha markat e makinave.</p>
            <a href="tel:+389070229348" style="color:var(--accent-electric)">Kontakto →</a>
        </div>
        <div class="service-panel">
            <h3>Mekanizma Dritareve</h3>
            <p>Riparim dhe ndërrim i mekanizmave elektrikë të dritareve me garanci.</p>
            <a href="tel:+389070229348" style="color:var(--accent-electric)">Kontakto →</a>
        </div>
        <div class="service-panel">
            <h3>Brava Makinash</h3>
            <p>Hapje emergjente pa dëmtim dhe riparim i bravave të dyerve apo ndezjes.</p>
            <a href="tel:+389070229348" style="color:var(--accent-electric)">Kontakto →</a>
        </div>
    </section>

    <section id="diagnostike" class="diagnostike-tech">
        <div class="diag-visual">
            <svg viewBox="0 0 400 150" xmlns="http://www.w3.org/2000/svg">
                <path d="M0,75 L400,75" stroke="rgba(255,255,255,0.05)" stroke-width="1"/>
                <path d="M0,75 L50,75 L60,30 L70,120 L80,75 L150,75 L160,50 L170,100 L180,75 L250,75 L260,10 L270,140 L280,75 L350,75 L360,60 L370,90 L380,75 L400,75" 
                      stroke="#00f2fe" stroke-width="3" fill="none">
                      <animate attributeName="stroke-dasharray" from="0,1000" to="1000,0" dur="3s" repeatCount="indefinite" />
                </path>
            </svg>
        </div>
        <div class="diag-text">
            <h2>Diagnostikë <span>Kompjuterike</span></h2>
            <p>Zbulimi i saktë i problemeve elektronike me pajisjet më të fundit në treg.</p>
        </div>
    </section>

    <!-- SECTION: GOOGLE MAPS -->
    <section class="map-section">
        <h2>Ku ndodhemi <span>ne</span></h2>
        <div class="map-container">
            <!-- Ky iframe tregon UNIKEY në Gjorçe Petrov -->
            <iframe 
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m12!1m3!1d2965.1234567890!2d21.35!3d42.01!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDLCsDAwJzM2LjAiTiAyMcKwMjEnMDAuMCJF!5e0!3m2!1ssq!2s!4v1700000000000!5m2!1ssq!2s" 
                width="100%" 
                height="450" 
                style="border:0;" 
                allowfullscreen="" 
                loading="lazy" 
                referrerpolicy="no-referrer-when-downgrade">
            </iframe>
        </div>
    </section>

    <footer id="kontakt">
        <div class="contact-card">
            <div class="contact-name">Muhamed Musli</div>
            <div class="contact-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
            <p style="color:var(--text-muted); margin-top:10px;">Gjorçe Petrov, Maqedonia e Veriut</p>
        </div>
        <div class="copyright">
            &copy; 2026 UNIKEY. All rights reserved.
        </div>
    </footer>

</body>
</html>
