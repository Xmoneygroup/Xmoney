<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MkdMap - Mobile Luxury Directory</title>
    <!-- Fonti luksoz Montserrat -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        /* --- 1. ANIMACIONI I RI DHE I PASTËR PËR TELEFON (SPLASH SCREEN) --- */
        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #060911;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 1;
            transition: opacity 0.5s ease-out;
            padding: 20px;
            box-sizing: border-box;
        }

        .splash-text {
            color: #ffffff;
            font-family: 'Montserrat', sans-serif;
            font-size: 1.3rem; /* Shkronja më e vogël që të mos ngjitet */
            font-weight: 400;
            text-transform: uppercase;
            text-align: center;
            letter-spacing: 2px; /* Hapësirë fillestare e pastër */
            opacity: 0;
            animation: textSpreadMobile 1.6s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        @keyframes textSpreadMobile {
            0% {
                opacity: 0;
                letter-spacing: 1px;
            }
            100% { 
                opacity: 1; 
                letter-spacing: 4px; /* Hapje elegante pa u ngjeshur */
            }
        }

        /* --- 2. DIZAJNI GLOBAL I LOKALIZUAR PËR CELULAR --- */
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            padding: 0;
            background: radial-gradient(circle at top, #111a2e 0%, #050811 100%);
            font-family: 'Montserrat', sans-serif;
            color: #f8fafc;
            overflow-x: hidden;
            min-height: 100vh;
            -webkit-tap-highlight-color: transparent;
        }

        #main-content {
            display: none; 
        }

        .container {
            width: 100%;
            padding: 25px 16px;
            text-align: center;
        }

        /* --- TITULLI NË CELULAR --- */
        header {
            margin-top: 5px;
            margin-bottom: 20px;
        }

        .main-title {
            margin: 0;
            font-size: 2.2rem;
            font-weight: 900;
            letter-spacing: 10px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #fff 30%, #d4af37 70%, #aa7c11 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* --- SELEKTORI I GJUHËVE --- */
        .lang-container {
            margin-bottom: 25px;
        }

        .lang-select {
            width: 100%;
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(212, 175, 55, 0.3);
            color: #ffffff;
            padding: 14px;
            border-radius: 15px;
            font-family: inherit;
            font-size: 0.95rem;
            font-weight: 600;
            letter-spacing: 0.5px;
            outline: none;
            backdrop-filter: blur(10px);
            appearance: none;
            -webkit-appearance: none;
            text-align: center;
        }

        /* --- KUTIA E KËRKIMIT VERTIKALE --- */
        .search-container {
            margin-bottom: 35px;
        }

        .search-box {
            display: flex;
            flex-direction: column;
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 12px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
            gap: 12px;
        }

        .search-box input {
            width: 100%;
            background: none;
            border: none;
            outline: none;
            color: #ffffff;
            font-size: 1rem;
            font-family: inherit;
            letter-spacing: 0.5px;
            padding: 10px 5px;
            text-align: center;
        }

        .search-box input::placeholder {
            color: #64748b;
        }

        .search-box button {
            width: 100%;
            background: #ffffff;
            border: none;
            color: #050811;
            font-weight: 700;
            padding: 15px;
            border-radius: 15px;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            font-size: 0.9rem;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .search-box button:active {
            background: linear-gradient(135deg, #d4af37, #aa7c11);
            color: #ffffff;
        }

        /* --- LISTA E BIZNESEVE --- */
        .results-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .business-card {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.05);
            padding: 22px;
            border-radius: 20px;
            text-align: left;
            position: relative;
            display: flex;
            flex-direction: column;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .biz-name {
            font-size: 1.3rem;
            font-weight: 700;
            color: #ffffff;
            margin: 0 0 10px 0;
            letter-spacing: 0.5px;
        }

        .biz-desc {
            color: #94a3b8;
            font-size: 0.9rem;
            margin: 0 0 22px 0;
            line-height: 1.5;
            font-weight: 300;
        }

        /* --- FOOTER-I I KARTELËS ME BUTONA SIKUR APLIKACION --- */
        .biz-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-top: 1px solid rgba(255, 255, 255, 0.06);
            padding-top: 15px;
            gap: 10px;
        }

        .biz-loc-link, .biz-phone-link {
            text-decoration: none;
            flex: 1;
            display: block;
        }

        .biz-loc {
            color: #d4af37;
            font-weight: 600;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            background: rgba(212, 175, 55, 0.05);
            border: 1px solid rgba(212, 175, 55, 0.2);
            padding: 12px 5px;
            border-radius: 12px;
            text-align: center;
        }

        .biz-phone {
            color: #ffffff;
            font-weight: 600;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 12px 5px;
            border-radius: 12px;
            text-align: center;
        }

        .biz-loc-link:active .biz-loc {
            background: rgba(212, 175, 55, 0.2);
            border-color: #d4af37;
        }

        .biz-phone-link:active .biz-phone {
            background: rgba(255, 255, 255, 0.15);
            border-color: #ffffff;
        }

        .no-results {
            color: #64748b;
            font-style: italic;
            margin-top: 20px;
            font-size: 0.95rem;
        }
    </style>
</head>
<body>

    <!-- 1. SPLASH SCREEN (I RREGULLUAR) -->
    <div id="splash-screen">
        <div class="splash-text">Welcome to Macedonia</div>
    </div>

    <!-- 2. MAIN CONTENT (CELULAR) -->
    <div id="main-content">
        <div class="container">
            <header>
                <h1 class="main-title">mkdmap</h1>
            </header>

            <!-- SELEKTORI I GJUHËVE -->
            <div class="lang-container">
                <select class="lang-select" id="language-picker" onchange="changeLanguage()">
                    <option value="en">🌐 English (EN)</option>
                    <option value="sq">🌐 Shqip (SQ)</option>
                    <option value="mk">🌐 Maqedonisht (MK)</option>
                    <option value="sr">🌐 Srpski (SR)</option>
                    <option value="tr">🌐 Türkçe (TR)</option>
                    <option value="de">🌐 Deutsch (DE)</option>
                </select>
            </div>

            <!-- KUTIA E KËRKIMIT -->
            <div class="search-container">
                <div class="search-box">
                    <input type="text" id="search-input" placeholder="What are you looking for? (e.g., mechanic, hotel)...">
                    <button id="search-btn" onclick="searchBusinesses()">Search</button>
                </div>
            </div>

            <!-- REZULTATET VERTIKALE -->
            <div class="results-container" id="results-box">
                <!-- Mbushet dinamikisht nga JS -->
            </div>
        </div>
    </div>

    <script>
        let currentLang = 'en';

        // Fjalor për ndryshimin e butonave sipas gjuhës
        const translations = {
            en: { searchPlace: "What are you looking for? (e.g., mechanic, hotel)...", searchBtn: "Search", callBtn: "📞 Call Now", noResults: "No businesses found." },
            sq: { searchPlace: "Çfarë po kërkoni? (psh., mekanik, vilë)...", searchBtn: "Kërko", callBtn: "📞 Telefono", noResults: "Nuk u gjet asnjë biznes." },
            mk: { searchPlace: "Што барате? (на пр. механичар, вила)...", searchBtn: "Пребарај", callBtn: "📞 Повикај", noResults: "Не се пронајдени бизниси." },
            sr: { searchPlace: "Šta tražite? (npr. mehaničar, vila)...", searchBtn: "Traži", callBtn: "📞 Pozovi", noResults: "Nuk u gjet asnjë biznes." },
            tr: { searchPlace: "Ne arıyorsunuz? (örn. tamirci, villa)...", searchBtn: "Ara", callBtn: "📞 Ara", noResults: "Sonuç bulunamadı." },
            de: { searchPlace: "Was suchen Sie? (z.B. Mechaniker, Villa)...", searchBtn: "Suche", callBtn: "📞 Anrufen", noResults: "Keine Ergebnisse gefunden." }
        };

        window.addEventListener("DOMContentLoaded", function() {
            showBusinesses(businesses);

            setTimeout(function() {
                var splash = document.getElementById("splash-screen");
                var mainContent = document.getElementById("main-content");
                
                splash.style.opacity = "0";
                mainContent.style.display = "block";
                
                setTimeout(function() {
                    splash.style.display = "none";
                }, 500); 
            }, 2500);
        });

        // DATABAZA E BIZNESEVE
        const businesses = [
            {
                phone: "+38970123456",
                phoneDisplay: "+389 70 123 456",
                mapUrl: "https://maps.google.com/?q=Mavrovo+Lake",
                tags: "villa hotel vilë vila вила хотел",
                en: { name: "Luxury Villa Mavrovo", location: "Mavrovo", desc: "Exclusive villa with mountain view and private pool." },
                sq: { name: "Vila Luksoze Mavrovë", location: "Mavrovë", desc: "Vilë ekskluzive me pamje spektakolare nga mali dhe pishinë private." },
                mk: { name: "Луксузна Вила Маврово", location: "Маврово", desc: "Ексклузивна вила со прекрасен поглед на планина и приватен базен." },
                sr: { name: "Luksuzna Vila Mavrovo", location: "Mavrovo", desc: "Ekskluzivna vila sa pogledom na planinu i privatnim bazenom." },
                tr: { name: "Lüks Villa Mavrovo", location: "Mavrovo", desc: "Dağ manzaralı ve özel havuzlu seçkin villa." },
                de: { name: "Luxusvilla Mavrovo", location: "Mavrovo", desc: "Exklusive Villa mit Bergblick und privatem Pool." }
            },
            {
                phone: "+38971999888",
                phoneDisplay: "+389 71 999 888",
                mapUrl: "https://maps.google.com/?q=Skopje+Center",
                tags: "mechanik mekanik service auto авто механичар",
                en: { name: "Skopje Auto Mechanic Pro", location: "Skopje", desc: "24/7 emergency car repair for tourists. English speaking support." },
                sq: { name: "Mekanik Auto Pro Shkup", location: "Shkup", desc: "Riparim urgjent i makinave 24/7 për turistët dhe vendasit. Flasim Shqip." },
                mk: { name: "Авто Механичар Про Скопје", location: "Скопје", desc: "24/7 итна поправка на возила за туристи. Зборуваме англиски." },
                sr: { name: "Auto Mehaničar Pro Skoplje", location: "Skoplje", desc: "24/7 hitna popravka automobila za turiste. Govorimo engleski." },
                tr: { name: "Üsküp Oto Tamir Pro", location: "Üsküp", desc: "Turistler için 24/7 acil araç tamiri. İngilizce destek mevcuttur." },
                de: { name: "Skopje Auto Mechaniker Pro", location: "Skopje", desc: "24/7 Notfall-Autoreparatur für Touristen. Englischsprachiger Support." }
            }
        ];

        function showBusinesses(list) {
            const box = document.getElementById("results-box");
            box.innerHTML = "";
            const langPack = translations[currentLang] || translations['en'];

            if(list.length === 0) {
                box.innerHTML = `<p class='no-results'>${langPack.noResults}</p>`;
                return;
            }

            list.forEach(biz => {
                // Merr tekstet në gjuhën e duhur automatikisht, ose kthehet tek 'en' nëse mungon
                const data = biz[currentLang] || biz['en']; 

                box.innerHTML += `
                    <div class="business-card">
                        <div class="biz-name">${data.name}</div>
                        <p class="biz-desc">${data.desc}</p>
                        
                        <div class="biz-footer">
                            <a href="${biz.mapUrl}" target="_blank" class="biz-loc-link">
                                <span class="biz-loc">📍 ${data.location}</span>
                            </a>
                            <a href="tel:${biz.phone}" class="biz-phone-link">
                                <span class="biz-phone">${langPack.callBtn}</span>
                            </a>
                        </div>
                    </div>
                `;
            });
        }

        // FUNKSIONI I PËRMIRËSUAR: NDRYSHON ÇDO TEKST AUTOMATIKISHT
        function changeLanguage() {
            currentLang = document.getElementById("language-picker").value;
            
            const input = document.getElementById("search-input");
            const btn = document.getElementById("search-btn");
            const langPack = translations[currentLang] || translations['en'];
            
            // Ndryshon kutinë e kërkimit dhe butonin automatikisht
            input.placeholder = langPack.searchPlace;
            btn.innerText = langPack.searchBtn;

            // Ridrejton kërkimin dhe përditëson tekstet e kartelave automatikisht
            searchBusinesses(); 
        }

        function searchBusinesses() {
            const query = document.getElementById("search-input").value.toLowerCase().trim();
            
            if(query === "") {
                showBusinesses(businesses);
                return;
            }

            const filtered = businesses.filter(biz => {
                // Kërkon në të gjitha gjuhët ekzistuese të biznesit
                return (biz.en && biz.en.name.toLowerCase().includes(query)) || 
                       (biz.sq && biz.sq.name.toLowerCase().includes(query)) || 
                       (biz.mk && biz.mk.name.toLowerCase().includes(query)) || 
                       (biz.sr && biz.sr.name.toLowerCase().includes(query)) || 
                       (biz.tr && biz.tr.name.toLowerCase().includes(query)) || 
                       (biz.de && biz.de.name.toLowerCase().includes(query)) || 
                       biz.tags.includes(query);
            });

            showBusinesses(filtered);
        }

        document.getElementById("search-input").addEventListener("keypress", function(event) {
            if (event.key === "Enter") {
                searchBusinesses();
            }
        });
    </script>
</body>
</html>
