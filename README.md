<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XSTORE NEON MODE</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --neon-blue: #00f3ff;
            --neon-pink: #ff0055;
            --neon-yellow: #facc15;
            --bg-dark: #080808;
        }

        body {
            background-color: var(--bg-dark);
            overflow: hidden;
            color: white;
            font-family: 'Courier New', Courier, monospace;
        }

        /* --- EFEKTI GLOW NEON (Baza) --- */
        .neon-border {
            box-shadow: 0 0 10px rgba(0, 243, 255, 0.5), 0 0 20px rgba(0, 243, 255, 0.3);
            border: 2px solid var(--neon-blue);
        }

        .neon-text-blue {
            color: var(--neon-blue);
            text-shadow: 0 0 5px var(--neon-blue), 0 0 10px var(--neon-blue), 0 0 20px var(--neon-blue);
        }

        .neon-text-pink {
            color: var(--neon-pink);
            text-shadow: 0 0 5px var(--neon-pink), 0 0 10px var(--neon-pink), 0 0 20px var(--neon-pink);
        }

        /* --- ANIMACIONE PËR PULSIM --- */
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        @keyframes scanline {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }

        .flicker { animation: blink 3s infinite; }
        .fast-flicker { animation: blink 0.2s infinite; }

        /* --- STRUKTURA E DYQANIT (Vizatimi me Kod) --- */
        .store-front {
            position: relative;
            width: 80%;
            height: 60vh;
            border: 4px solid var(--neon-blue);
            box-shadow: 0 0 20px var(--neon-blue), inset 0 0 20px rgba(0, 243, 255, 0.2);
            margin: 50px auto;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            padding-top: 20px;
        }

        /* Pllakata Lart */
        .signboard {
            padding: 15px 40px;
            border: 2px solid var(--neon-yellow);
            box-shadow: 0 0 15px var(--neon-yellow);
            margin-bottom: 30px;
        }

        /* Dera */
        .door {
            width: 100px;
            height: 180px;
            border: 2px solid var(--neon-blue);
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .open-sign {
            font-size: 0.7rem;
            font-weight: bold;
            color: var(--neon-pink);
            text-shadow: 0 0 5px var(--neon-pink);
            transform: rotate(-10deg);
            animation: blink 1.5s infinite;
        }

        /* --- MAKINAT NEON (Vizatimi me SVG) --- */
        .car-container {
            position: absolute;
            bottom: 20px;
            width: 100%;
            display: flex;
            justify-content: space-around;
            padding: 0 50px;
        }

        .neon-car {
            width: 150px;
            height: auto;
            opacity: 0.8;
        }

        .car-headlights {
            filter: drop-shadow(0 0 10px white);
        }

        /* --- KATALOGU (Brenda Dyqanit) --- */
        #catalog-view {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(8, 8, 8, 0.95);
            z-index: 50;
            border: 10px solid var(--neon-blue);
            box-shadow: 0 0 50px var(--neon-blue);
        }

        /* Notifikimi i Daljes */
        #exit-notification {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: var(--bg-dark);
            padding: 50px;
            border: 4px solid var(--neon-yellow);
            box-shadow: 0 0 30px var(--neon-yellow);
            z-index: 100;
            text-align: center;
        }

    </style>
</head>
<body>

    <div id="main-store" class="h-screen w-screen flex flex-col items-center">
        
        <div class="store-front">
            <div class="signboard flicker">
                <h1 class="text-5xl font-black text-white tracking-tighter neon-text-blue">X<span class="neon-text-pink">STORE</span></h1>
            </div>

            <button onclick="openStore()" class="mt-20 neon-border neon-text-blue px-8 py-3 rounded text-lg font-bold hover:bg-cyan-950 transition-all">
                JOIN IN STORE
            </button>

            <div class="door">
                <div class="open-sign">Open 24/7</div>
            </div>
        </div>

        <div class="car-container">
            <svg class="neon-car flicker" viewBox="0 0 120 50">
                <path d="M10,40 L110,40 L100,20 L80,15 L40,15 L20,20 Z" fill="none" stroke="#00f3ff" stroke-width="2"/>
                <circle cx="30" cy="40" r="8" fill="none" stroke="#ff0055" stroke-width="2"/>
                <circle cx="90" cy="40" r="8" fill="none" stroke="#ff0055" stroke-width="2"/>
                <light class="car-headlights" x="105" y="25" width="10" height="10" fill="white" opacity="0.8"/>
            </svg>
            <svg class="neon-car fast-flicker" viewBox="0 0 120 50">
                <path d="M10,40 L110,40 L110,25 L90,20 L30,20 L10,25 Z" fill="none" stroke="#facc15" stroke-width="2"/>
                <circle cx="30" cy="40" r="8" fill="none" stroke="#facc15" stroke-width="2"/>
                <circle cx="90" cy="40" r="8" fill="none" stroke="#facc15" stroke-width="2"/>
                <rect class="car-headlights" x="105" y="28" width="5" height="5" fill="white" opacity="0.8"/>
            </svg>
            <svg class="neon-car" viewBox="0 0 120 50">
                <path d="M10,40 L110,40 L105,25 L85,18 L35,18 L15,25 Z" fill="none" stroke="#ff0055" stroke-width="2"/>
                <circle cx="30" cy="40" r="8" fill="none" stroke="#00f3ff" stroke-width="2"/>
                <circle cx="90" cy="40" r="8" fill="none" stroke="#00f3ff" stroke-width="2"/>
                <light class="car-headlights" x="108" y="22" width="8" height="8" fill="white" opacity="0.8"/>
            </svg>
        </div>
    </div>

    <div id="catalog-view" class="p-8">
        <div class="max-w-7xl mx-auto">
            <div class="flex justify-between items-center border-b-2 border-dashed border-cyan-800 pb-5">
                <h2 class="text-3xl font-bold neon-text-blue">XSTORE <span class="text-gray-600 text-sm">NEON_CATALOG_V1</span></h2>
                <div class="flex space-x-6 text-white items-center">
                    <button onclick="showInfo()" class="neon-border px-4 py-2 rounded text-sm font-bold neon-text-pink hover:bg-pink-950">INFO</button>
                    <div class="text-sm">🛒 Korpa: <span class="neon-text-yellow">0</span></div>
                    <div class="text-sm">📦 Orders: <span class="neon-text-yellow">0</span></div>
                    <button onclick="exitStore()" class="neon-border px-4 py-1 rounded text-sm font-bold text-gray-400 hover:bg-gray-800">EXIT</button>
                </div>
            </div>

            <div class="mt-20 text-center border-2 border-dashed border-gray-800 p-40">
                <p class="text-gray-700 text-xl italic tracking-widest neon-text-yellow flickering">LOADING_CORE_DATA...</p>
            </div>
        </div>
    </div>

    <div id="exit-notification">
        <h3 class="text-5xl font-black neon-text-pink mb-4 flicker">XSTORE</h3>
        <p class="text-xl text-white font-medium tracking-tight">FALEMINDERIT QË VIZITOVE<br>DYQANIN TONË NEON!</p>
        <button onclick="closeNotification()" class="mt-8 neon-text-yellow text-sm underline flicker">Mbyll</button>
    </div>

    <script>
        function openStore() {
            document.getElementById('catalog-view').style.display = 'block';
            document.getElementById('main-store').style.filter = 'blur(15px) contrast(150%)';
        }

        function exitStore() {
            document.getElementById('catalog-view').style.display = 'none';
            document.getElementById('main-store').style.filter = 'none';
            document.getElementById('exit-notification').style.display = 'block';
        }

        function closeNotification() {
            document.getElementById('exit-notification').style.display = 'none';
        }

        function showInfo() {
            alert("ℹ️ INFO: Dergojmë vetëm porosi në Europë.\n⏱️ Koha: 7 - 18 ditë.");
        }
    </script>
</body>
</html>
