<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Specialist për Celsa Makinash</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #d4af37;
            --dark: #0a0a0a;
            --glass: rgba(255, 255, 255, 0.1);
        }

        body, html {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            background-color: var(--dark);
            color: white;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* Background Animacion 3D */
        #bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle, #1a1a1a 0%, #000 100%);
            overflow: hidden;
        }

        .car-logo {
            position: absolute;
            font-size: 2rem;
            color: rgba(212, 175, 55, 0.3);
            font-weight: bold;
            white-space: nowrap;
            animation: move linear infinite;
        }

        @keyframes move {
            0% { transform: translateY(110vh) rotate(0deg); }
            100% { transform: translateY(-10vh) rotate(360deg); }
        }

        /* Intro Speed Effect */
        .fast-start { animation-duration: 3s !important; }
        .slow-move { animation-duration: 20s !important; }

        /* Header & Translate */
        .top-bar {
            display: flex;
            justify-content: flex-end;
            padding: 20px;
        }

        .btn-translate {
            background: var(--gold);
            color: black;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            font-weight: bold;
            border-radius: 5px;
            transition: 0.3s;
        }

        /* Titulli Luxury */
        .container {
            max-width: 1000px;
            margin: auto;
            text-align: center;
            padding: 50px 20px;
        }

        h1.luxury-title {
            font-family: 'Cinzel', serif;
            font-size: 5rem;
            color: var(--gold);
            text-shadow: 0 0 20px rgba(212, 175, 55, 0.5);
            margin-bottom: 20px;
            animation: fadeIn 2s ease-in;
        }

        /* Nentitujt */
        .info-list {
            list-style: none;
            padding: 0;
            text-align: left;
            display: inline-block;
            background: var(--glass);
            padding: 30px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(212, 175, 55, 0.2);
        }

        .info-list li {
            font-size: 1.2rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
        }

        .info-list li::before {
            content: '🔑';
            margin-right: 15px;
        }

        /* Galeria e Fotove */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 50px;
        }

        .gallery img {
            width: 100%;
            border-radius: 10px;
            transition: 0.5s;
            border: 2px solid transparent;
        }

        .gallery img:hover {
            transform: scale(1.05);
            border-color: var(--gold);
        }

        /* Sistemi i Vlerësimit */
        .rating-section {
            margin-top: 80px;
            background: var(--glass);
            padding: 40px;
            border-radius: 15px;
        }

        .stars {
            font-size: 2rem;
            color: #555;
            cursor: pointer;
        }

        .stars span:hover, .stars span.active {
            color: var(--gold);
        }

        textarea {
            width: 100%;
            height: 100px;
            margin-top: 20px;
            background: rgba(0,0,0,0.5);
            color: white;
            border: 1px solid var(--gold);
            padding: 10px;
            border-radius: 5px;
        }

        .btn-submit {
            margin-top: 10px;
            background: var(--gold);
            border: none;
            padding: 10px 30px;
            font-weight: bold;
            cursor: pointer;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 600px) {
            h1.luxury-title { font-size: 3rem; }
        }
    </style>
</head>
<body>

    <div id="bg-animation"></div>

    <div class="top-bar">
        <button class="btn-translate" onclick="toggleLanguage()">Translate to English</button>
    </div>

    <div class="container">
        <h1 class="luxury-title">UNIKEY</h1>
        
        <ul class="info-list" id="content-list">
            <li data-sq="Kemi 17 vite që merremi me këtë profesion." data-en="We have 17 years of experience in this profession.">Kemi 17 vite që merremi me këtë profesion.</li>
            <li data-sq="Punojmë 6 ditët e javës nga e Hëna deri në diten e Shtunë, nga ora 9:30 deri në ora 19:00." data-en="We work 6 days a week, Monday to Saturday, from 9:30 AM to 7:00 PM.">Punojmë 6 ditët e javës nga e Hëna deri në diten e Shtunë, nga ora 9:30 deri në ora 19:00.</li>
            <li data-sq="Riparojmë Dyer te makinave (Brava), Mehanizma të dritareve, Qelsa duplikat, kodime, celsa shtëpish, Diagnostikë." data-en="We repair car doors (Locks), window mechanisms, duplicate keys, coding, house keys, and Diagnostics.">Riparojmë Dyer te makinave (Brava), Mehanizma të dritareve, Qelsa duplikat, kodime, celsa shtëpish, Diagnostikë.</li>
            <li data-sq="Lokacioni: Maqedoni, Gjorce Petrov. Na gjeni si 'UNIKKEY - Gjorce Petrov'." data-en="Location: Macedonia, Gjorce Petrov. Find us as 'UNIKKEY - Gjorce Petrov'.">Lokacioni: Maqedoni, Gjorce Petrov. Na gjeni si 'UNIKKEY - Gjorce Petrov'.</li>
            <li data-sq="Kontakt: Muhamet Musliu - +389 070 229 348" data-en="Contact: Muhamet Musliu - +389 070 229 348">Kontakt: Muhamet Musliu - +389 070 229 348</li>
        </ul>

        <!-- Galeria (Vendos fotot e tua këtu) -->
        <div class="gallery">
            <img src="foto1.jpg" alt="Unikey Work 1">
            <img src="foto2.jpg" alt="Unikey Work 2">
            <img src="foto3.jpg" alt="Unikey Work 3">
            <img src="foto4.jpg" alt="Unikey Work 4">
        </div>

        <!-- Vleresimet -->
        <div class="rating-section">
            <h3 id="rate-title">Vlerësoni Punën Tonë</h3>
            <div class="stars" id="star-container">
                <span onclick="rate(1)">★</span><span onclick="rate(2)">★</span><span onclick="rate(3)">★</span><span onclick="rate(4)">★</span><span onclick="rate(5)">★</span>
            </div>
            <textarea id="comment" placeholder="Lini komentin tuaj këtu..."></textarea>
            <button class="btn-submit" onclick="submitFeedback()">Dërgo Komentin</button>
        </div>
    </div>

    <script>
        // Krijimi i animacionit te background-it
        const bg = document.getElementById('bg-animation');
        const brands = ['LAMBORGHINI', 'FERRARI', 'PORSCHE', 'BMW', 'AUDI', 'MERCEDES', 'TOYOTA', 'VW'];
        
        function createLogo() {
            const logo = document.createElement('div');
            logo.className = 'car-logo fast-start';
            logo.innerText = brands[Math.floor(Math.random() * brands.length)];
            logo.style.left = Math.random() * 100 + 'vw';
            logo.style.opacity = Math.random();
            bg.appendChild(logo);

            // Ngadalesimi pas 3 sekondave
            setTimeout(() => {
                logo.classList.remove('fast-start');
                logo.classList.add('slow-move');
            }, 3000);

            // Hiqe kur mbaron
            setTimeout(() => { logo.remove(); }, 25000);
        }

        setInterval(createLogo, 1000);

        // Funksioni i perkthimit
        let currentLang = 'sq';
        function toggleLanguage() {
            const items = document.querySelectorAll('#content-list li');
            const btn = document.querySelector('.btn-translate');
            const rateTitle = document.getElementById('rate-title');
            
            if (currentLang === 'sq') {
                items.forEach(li => li.innerText = li.getAttribute('data-en'));
                btn.innerText = "Kthe në Shqip";
                rateTitle.innerText = "Rate Our Work";
                currentLang = 'en';
            } else {
                items.forEach(li => li.innerText = li.getAttribute('data-sq'));
                btn.innerText = "Translate to English";
                rateTitle.innerText = "Vlerësoni Punën Tonë";
                currentLang = 'sq';
            }
        }

        // Sistemi i yjeve
        function rate(n) {
            const spans = document.querySelectorAll('.stars span');
            spans.forEach((s, idx) => {
                s.classList.toggle('active', idx < n);
            });
        }

        function submitFeedback() {
            alert("Faleminderit për vlerësimin tuaj!");
            document.getElementById('comment').value = "";
        }
    </script>
</body>
</html>
