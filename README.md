<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XSTORE | Auto Parts</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" rel="stylesheet">
    <style>
        /* Sfondi i Dyqanit (Background) */
        .store-front {
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.2)), url('https://images.unsplash.com/photo-1552519507-da3b142c6e3d?auto=format&fit=crop&q=80&w=2070');
            background-size: cover;
            background-position: center;
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        /* Tabelat e Dyqanit */
        .signboard {
            background: #1a1a1a;
            border: 4px solid #facc15;
            padding: 20px 50px;
            box-shadow: 0 0 30px rgba(250, 204, 21, 0.5);
        }

        .door-sign {
            background: #ef4444;
            color: white;
            padding: 5px 15px;
            font-size: 0.8rem;
            font-weight: bold;
            border-radius: 4px;
            margin-top: 10px;
            animation: pulse 2s infinite;
        }

        /* Katalogu Modal */
        #catalog-view {
            display: none;
            position: fixed;
            inset: 0;
            background: #0f172a;
            z-index: 50;
        }

        /* Notifikimi në mes */
        #exit-notification {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 0 50px rgba(0,0,0,0.5);
            z-index: 100;
            text-align: center;
            border-top: 10px solid #facc15;
        }

        .car-light {
            box-shadow: 0 0 20px 5px rgba(255, 255, 255, 0.8);
        }
    </style>
</head>
<body class="bg-black font-sans">

    <div id="main-store" class="store-front">
        
        <div class="signboard animate__animated animate__fadeInDown">
            <h1 class="text-6xl font-black text-white tracking-tighter">X<span class="text-yellow-400">STORE</span></h1>
        </div>

        <div class="mt-8 flex flex-col items-center">
            <div class="door-sign">OPEN 24/7</div>
            <button onclick="openStore()" class="mt-10 bg-white text-black px-10 py-4 rounded-full font-bold text-xl hover:bg-yellow-400 transition-all transform hover:scale-110 shadow-2xl">
                JOIN IN STORE
            </button>
        </div>

        <div class="absolute bottom-10 flex space-x-20">
            <div class="text-center opacity-80">
                <div class="h-10 w-24 bg-gray-700 rounded-t-lg car-light"></div>
                <p class="text-white text-xs mt-2 font-bold">PORSCHE</p>
            </div>
            <div class="text-center">
                <div class="h-10 w-24 bg-blue-900 rounded-t-lg car-light"></div>
                <p class="text-white text-xs mt-2 font-bold">GOLF 4 SPORT</p>
            </div>
            <div class="text-center opacity-80">
                <div class="h-10 w-24 bg-black rounded-t-lg car-light"></div>
                <p class="text-white text-xs mt-2 font-bold">BMW M4</p>
            </div>
        </div>
    </div>

    <div id="catalog-view" class="p-8">
        <div class="max-w-7xl mx-auto">
            <div class="flex justify-between items-center border-b border-gray-700 pb-5">
                <h2 class="text-3xl font-bold text-white">XSTORE <span class="text-gray-400 text-sm">CATALOG</span></h2>
                <div class="flex space-x-6 text-white items-center">
                    <button onclick="showInfo()" class="bg-blue-600 px-4 py-2 rounded text-sm font-bold">INFO</button>
                    <div class="text-sm">🛒 Korpa: <span class="text-yellow-400">0</span></div>
                    <div class="text-sm">📦 Orders: <span class="text-yellow-400">0</span></div>
                    <button onclick="exitStore()" class="bg-red-600 px-4 py-1 rounded text-sm font-bold">EXIT</button>
                </div>
            </div>

            <div class="mt-20 text-center border-2 border-dashed border-gray-800 p-40">
                <p class="text-gray-500 text-xl italic">Katalogu po ngarkohet...</p>
            </div>
        </div>
    </div>

    <div id="exit-notification" class="animate__animated animate__zoomIn">
        <h3 class="text-4xl font-black text-black mb-4">XSTORE</h3>
        <p class="text-xl text-gray-700 font-medium">Faleminderit që vizitove dyqanin tonë!</p>
        <button onclick="closeNotification()" class="mt-8 text-gray-400 text-sm underline">Mbyll</button>
    </div>

    <script>
        function openStore() {
            document.getElementById('catalog-view').style.display = 'block';
            document.getElementById('main-store').style.filter = 'blur(10px)';
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
