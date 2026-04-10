<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY | Mansory Style Professional</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Montserrat:wght@300;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #c5a059;
            --dark: #0a0a0a;
        }

        body, html {
            margin: 0; padding: 0;
            background-color: var(--dark);
            color: white;
            font-family: 'Montserrat', sans-serif;
            scroll-behavior: smooth;
        }

        /* NAVBAR */
        nav {
            position: fixed; top: 0; width: 100%;
            display: flex; justify-content: space-between; align-items: center;
            padding: 20px 60px; z-index: 1000;
            background: rgba(0,0,0,0.8);
            border-bottom: 1px solid var(--gold);
            box-sizing: border-box;
        }

        .brand { font-family: 'Cinzel', serif; font-size: 1.8rem; color: var(--gold); letter-spacing: 4px; }
        
        .lang-switch button {
            background: none; border: 1px solid var(--gold); color: var(--gold);
            padding: 5px 12px; cursor: pointer; font-size: 12px;
        }

        /* SEKSIONET ME FOTO (SI NE FOTO) */
        .full-section {
            height: 100vh;
            width: 100%;
            display: flex;
            align-items: center;
            background-size: cover;
            background-position: center;
            background-attachment: fixed; /* Efekti Parallax */
            position: relative;
        }

        /* Ngjyra e zezë sipër fotos që teksti të duket mirë */
        .full-section::before {
            content: "";
            position: absolute; inset: 0;
            background: linear-gradient(to right, rgba(0,0,0,0.9) 20%, transparent 80%);
        }

        .content {
            position: relative;
            z-index: 10;
            padding-left: 10%;
            max-width: 600px;
        }

        .content h1, .content h2 {
            font-family: 'Cinzel', serif;
            font-size: 4rem;
            color: var(--gold);
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .content p {
            font-size: 1.3rem;
            letter-spacing: 1px;
            line-height: 1.5;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .btn-gold {
            padding: 15px 40px;
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold);
            font-family: 'Cinzel';
            font-size: 1.1rem;
            cursor: pointer;
            transition: 0.3s;
            text-decoration: none;
        }

        .btn-gold:hover {
            background: var(--gold);
            color: black;
            box-shadow: 0 0 20px var(--gold);
        }

        /* BACKGROUNDET E SECILIT SEKSION */
        #hero { background-image: url('https://images.unsplash.com/photo-1614162692292-7ac56d7f7f1e?q=80&w=2070&auto=format&fit=crop'); }
        #keys { background-image: url('https://images.unsplash.com/photo-1622353100523-868cc9031940?q=80&w=2070&auto=format&fit=crop'); }
        #locks { background-image: url('https://images.unsplash.com/photo-1517524008410-b44c6659bc95?q=80&w=2070&auto=format&fit=crop'); }
        #diag { background-image: url('https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?q=80&w=2070&auto=format&fit=crop'); }

        /* FOOTER */
        footer {
            padding: 80px 10%;
            background: #050505;
            text-align: center;
            border-top: 3px solid var(--gold);
        }

        footer h2 { font-family: 'Cinzel'; font-size: 3rem; color: var(--gold); }
        .footer-info { font-size: 1.2rem; margin: 20px 0; color: #aaa; }
        .tel { font-size: 2.5rem; color: var(--gold); text-decoration: none; font-weight: 800; display: block; }

    </style>
</head>
<body>

    <nav>
        <div class="brand">UNIKEY</div>
        <div class="lang-switch">
            <button onclick="changeL('sq')">ALB</button>
            <button onclick="changeL('en')">ENG</button>
        </div>
    </nav>

    <section class="full-section" id="hero">
        <div class="content">
            <h1 id="h1">Teknologjia e Çelsave</h1>
            <p id="p1">RIPARIM DHE KODIM PROFESIONAL PËR ÇDO MARKË MAKINASH</p>
            <a href="tel:+389070229348" class="btn-gold" id="b1">KONTAKTO TANI</a>
        </div>
    </section>

    <section class="full-section" id="keys">
        <div class="content">
            <h2 id="h2">DUPLIKAT ÇELSASH</h2>
            <p id="p2">Saktësi milimetrike në çdo prerje. Ne krijojmë kopjen tuaj perfekte brenda pak minutave me teknologji lazer.</p>
        </div>
    </section>

    <section class="full-section" id="locks">
        <div class="content">
            <h2 id="h3">RIPARIM BRAVASH</h2>
            <p id="p3">Siguri dhe funksionalitet maksimal. Riparojmë bravat e derës dhe mekanizmat e dritareve të çdo automjeti.</p>
        </div>
    </section>

    <section class="full-section" id="diag">
        <div class="content">
            <h2 id="h4">DIAGNOSTIKË</h2>
            <p id="p4">Skanim i moduleve elektronike dhe fshirje e gabimeve (Check Engine, Airbag, etj) me sistemet më të fundit.</p>
        </div>
    </section>

    <footer>
        <div class="footer-title"><h2>UNIKEY</h2></div>
        <div class="footer-info">
            <p id="f1">Mbi 15 Vite Eksperiencë në Teknologjinë Auto</p>
            <p id="f2">Hapur: 09:30 - 19:00 (E hënë - E shtunë)</p>
            <a href="tel:+389070229348" class="tel">+389 070 229 348</a>
        </div>
    </footer>

    <script>
        const texts = {
            sq: {
                h1: "Teknologjia e Çelsave", p1: "RIPARIM DHE KODIM PROFESIONAL PËR ÇDO MARKË MAKINASH", b1: "KONTAKTO TANI",
                h2: "DUPLIKAT ÇELSASH", p2: "Saktësi milimetrike në çdo prerje. Ne krijojmë kopjen tuaj perfekte brenda pak minutave.",
                h3: "RIPARIM BRAVASH", p3: "Siguri dhe funksionalitet maksimal. Riparojmë bravat dhe mekanizmat e dritareve.",
                h4: "DIAGNOSTIKË", p4: "Skanim i moduleve elektronike dhe fshirje e gabimeve me sistemet më të fundit.",
                f1: "Mbi 15 Vite Eksperiencë në Teknologjinë Auto", f2: "Hapur: 09:30 - 19:00 (E hënë - E shtunë)"
            },
            en: {
                h1: "Key Technology", p1: "PROFESSIONAL REPAIR AND CODING FOR EVERY CAR BRAND", b1: "CONTACT NOW",
                h2: "KEY DUPLICATION", p2: "Millimetric precision in every cut. We create your perfect copy within minutes.",
                h3: "LOCK REPAIR", p3: "Maximum security and functionality. We repair door locks and window mechanisms.",
                h4: "DIAGNOSTICS", p4: "Electronic module scanning and error clearing with the latest systems.",
                f1: "Over 15 Years of Experience in Auto Tech", f2: "Open: 09:30 - 19:00 (Monday - Saturday)"
            }
        };

        function changeL(l) {
            document.getElementById('h1').innerText = texts[l].h1;
            document.getElementById('p1').innerText = texts[l].p1;
            document.getElementById('b1').innerText = texts[l].b1;
            document.getElementById('h2').innerText = texts[l].h2;
            document.getElementById('p2').innerText = texts[l].p2;
            document.getElementById('h3').innerText = texts[l].h3;
            document.getElementById('p3').innerText = texts[l].p3;
            document.getElementById('h4').innerText = texts[l].h4;
            document.getElementById('p4').innerText = texts[l].p4;
            document.getElementById('f1').innerText = texts[l].f1;
            document.getElementById('f2').innerText = texts[l].f2;
        }
    </script>
</body>
</html>
