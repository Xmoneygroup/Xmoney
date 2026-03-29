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
        }

        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }

        a { text-decoration: none; color: inherit; }
        ul { list-style: none; padding: 0; margin: 0; }

        /* MENUJA LART - E rregulluar drejt */
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
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .logo {
            font-size: 24px;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 2px;
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
            font-weight: 700;
            transition: 0.3s;
        }
        nav a:hover { color: var(--accent-electric); }

        /* TITULLI KRYESOR - Pa vijë të bardhë poshtë */
        .hero {
            height: 80vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding-top: 80px;
        }

        .hero h1 {
            font-size: 70px;
            margin: 0;
            text-transform: uppercase;
            font-weight: 900;
            letter-spacing: 5px;
        }
        .hero h1 span { color: var(--accent-electric); }

        .hero p {
            font-size: 16px;
            color: var(--text-muted);
            max-width: 550px;
            margin-top: 20px;
            margin-bottom: 30px;
        }

        .contact-btn {
            background-color: var(--accent-blue);
            color: white;
            padding: 12px 25px;
            border-radius: 4px;
            font-weight: bold;
            text-transform: uppercase;
        }

        /* DIAGNOSTIKA */
        .diag-section {
            padding: 80px 50px;
            background-color: var(--bg-panel);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 40px;
        }

        .radar-box {
            width: 250px;
            height: 150px;
            border: 1px solid var(--accent-electric);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .diag-text h2 { font-size: 30px; text-transform: uppercase; }
        .diag-text span { color: var(--accent-electric); }

        /* FOOTER */
        footer {
            padding: 60px 20px;
            text-align: center;
        }

        .contact-card {
            background: #0d1117;
            padding: 30px;
            border-radius: 10px;
            display: inline-block;
            border: 1px solid rgba(255,255,255,0.05);
        }

        .c-name { font-size: 22px; font-weight: 800; margin-bottom: 10px; }
        .c-phone { font-size: 26px; color: var(--accent-electric); font-weight: bold; }

        @media (max-width: 768px) {
            header { padding: 15px; flex-direction: column; }
            .hero h1 { font-size: 40px; }
            .diag-section { flex-direction: column; }
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
        <a href="tel:+389070229348" class="contact-btn" style="font-size: 12px; padding: 8px 15px;">TELEFONO</a>
    </header>

    <section id="home" class="hero">
        <h1>UNI<span>KEY</span></h1>
        <p>Specialistë të çertifikuar për kodimin e çelësave inteligjentë dhe diagnostikë kompjuterike për makina moderne.</p>
        <a href="#sherbimet" class="contact-btn">SHIKO SHËRBIMET</a>
    </section>

    <section id="diagnostike" class="diag-section">
        <div class="radar-box">
            <span style="color: var(--accent-electric); font-weight: bold;">SCANNING...</span>
        </div>
        <div class="diag-text">
            <h2>Diagnostikë <span>Kompjuterike</span></h2>
            <p style="color: var(--text-muted);">Zbulim i saktë i problemeve elektronike.</p>
        </div>
    </section>

    <footer id="kontakt">
        <div class="contact-card">
            <div class="c-name">Muhamed Musli</div>
            <div class="c-phone"><a href="tel:+389070229348">+389 070 229 348</a></div>
        </div>
        <p style="margin-top: 30px; color: #222; font-size: 10px;">&copy; 2026 UNIKEY. ALL RIGHTS RESERVED.</p>
    </footer>

</body>
</html>
