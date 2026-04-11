
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XSTORE - Elevate Your Drive | Car Parts & Performance</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700;900&family=Roboto:wght@300;400;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"/>
    <style>
        /* Stilime të personalizuara që nuk mbulohen nga Tailwind */
        :root {
            --brand-red: #E31B23; /* Ngjyra e kuqe e XSTORE nga fotoja */
            --bg-dark: #0A0A0A;
        }
        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--bg-dark);
            color: white;
            overflow-x: hidden;
        }
        .font-header { font-family: 'Montserrat', sans-serif; }
        
        /* Sfondi Hero: Përdorim foton tuaj si sfond */
        .hero-bg {
            background-image: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.7)), url('xstore_hero.png');
            background-size: cover;
            background-position: center;
            background-attachment: fixed; /* Efekt Parallax i lehtë */
        }

        /* Stilimi i butonit Join in Store me efekt Glow */
        .btn-join {
            background-color: var(--brand-red);
            transition: all 0.3s ease-in-out;
            box-shadow: 0 4px 15px rgba(227, 27, 35, 0.4);
        }
        .btn-join:hover {
            box-shadow: 0 6px 25px rgba(227, 27, 35, 0.7);
            transform: translateY(-3px);
        }

        /* Overlay i Katalogut (i fshehur fillimisht) */
        #catalog-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background-color: rgba(0, 0, 0, 0.95);
            z-index: 100;
            overflow-y: auto;
        }
    </style>
</head>
<body>

    <nav class="fixed w-full z-50 bg-black/80 backdrop-blur-sm border-b border-gray-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <div class="flex-shrink-0 animate__animated animate__fadeIn">
                    <span class="font-header font-900 text-3xl tracking-tighter text-white">X<span style="color:var(--brand-red)">STORE</span></span>
                    <span class="block text-xs text-gray-400 font-light -mt-1 tracking-widest">Elevate Your Drive.</span>
                </div>
                <div class="hidden md:block animate__animated animate__fadeIn animate__delay-1s">
                    <div class="ml-10 flex items-baseline space-x-6 text-sm uppercase tracking-wider font-medium text-gray-300">
                        <a href="#" class="hover:text-white transition-colors">Car Parts</a>
                        <a href="#" class="hover:text-white transition-colors">Accessories</a>
                        <a href="#" class="hover:text-white transition-colors">Performance</a>
                        <a href="#" class="hover:text-white transition-colors">Services</a>
                        <a href="#" class="hover:text-white transition-colors">About Us</a>
                        <a href="#" class="hover:text-white transition-colors">Contact</a>
                    </div>
                </div>
                <div class="flex space-x-4 items-center animate__animated animate__fadeIn">
                    <button class="text-sm border border-gray-600 px-4 py-1.5 rounded hover:bg-gray-800 transition">LOGIN</button>
                    <button class="relative">
                        🛒 <span class="absolute -top-2 -right-2 bg-red-600 text-xs rounded-full h-4 w-4 flex items-center justify-center">0</span>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <div class="hero-bg h-screen w-full flex flex-col justify-center items-center text-center px-4 relative">
        <div class="hidden lg:block absolute left-10 top-1/4 bg-black/60 p-6 border border-gray-800 rounded-lg animate__animated animate__fadeInLeft animate__delay-1s">
            <div class="space-y-4 font-light text-gray-300 text-sm">
                <p><span class="font-bold text-xl text-white">10,000+</span> SALES</p>
                <p><span class="font-bold text-xl text-white">25,000+</span> HAPPY CUSTOMERS</p>
                <p><span class="font-bold text-xl text-white">20 YEARS</span> OF TRUST</p>
            </div>
        </div>

        <h1 class="font-header font-900 text-5xl md:text-7xl tracking-tighter text-white animate__animated animate__zoomIn">
            X<span style="color:var(--brand-red)">STORE</span>
        </h1>
        <p class="mt-4 text-xl md:text-2xl font-light text-gray-200 tracking-wide animate__animated animate__fadeIn animate__delay-1s">
            Premium Car Parts, Accessories & Performance.
        </p>

        <button id="btn-join-store" class="btn-join mt-12 px-12 py-4 rounded-full text-white font-bold text-lg uppercase tracking-widest animate__animated animate__fadeInUp animate__delay-2s">
            Join in Store
        </button>

        <div class="absolute bottom-10 right-10 text-right text-gray-400 font-light text-sm hidden md:block animate__animated animate__fadeIn animate__delay-2s">
            <p>• QUALITY</p>
            <p>• PASSION</p>
            <p>• TRUST</p>
            <p>• LEGACY</p>
        </div>
    </div>

    <div id="catalog-overlay" class="p-6 md:p-12">
        <div class="max-w-7xl mx-auto relative">
            <button id="btn-close-catalog" class="absolute top-0 right-0 text-gray-500 hover:text-white text-3xl">&times;</button>
            
            <div class="text-center mb-12">
                <h2 class="font-header font-900 text-4xl text-white">X<span style="color:var(--brand-red)">STORE</span> <span class="font-light text-3xl">Catalog</span></h2>
                <p class="mt-2 text-gray-400">Eksploroni gamën tonë pa fund (Produktet po ngarkohen...)</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                <template id="product-template">
                    <div class="bg-gray-900 border border-gray-800 rounded-lg p-4 animate__animated animate__fadeInUp">
                        <div class="aspect-square bg-gray-800 rounded mb-4 flex items-center justify-center text-gray-600">[FOTO PRODUKTI]</div>
                        <h4 class="font-medium text-white">Emri i Produktit</h4>
                        <p class="text-sm text-gray-400 mt-1">Përshkrimi i shkurtër teknik.</p>
                        <div class="flex justify-between items-center mt-4">
                            <span class="text-red-500 font-bold">€0.00</span>
                            <button class="text-xs text-gray-500 hover:text-white underline">Detaje</button>
                        </div>
                    </div>
                </template>
            </div>
            
            <div class="text-center mt-20 p-20 border-2 border-dashed border-gray-800 rounded-lg">
                <p class="text-gray-600 text-xl italic">Seksioni i katalogut është gati. Produktet do të shtohen së shpejti.</p>
            </div>

        </div>
    </div>

    <script>
        // DOM Elements
        const btnJoin = document.getElementById('btn-join-store');
        const btnClose = document.getElementById('btn-close-catalog');
        const catalogOverlay = document.getElementById('catalog-overlay');
        const heroSection = document.querySelector('.hero-bg');

        // Funksioni për të hapur Katalogun
        btnJoin.addEventListener('click', () => {
            catalogOverlay.style.display = 'block';
            catalogOverlay.classList.add('animate__animated', 'animate__fadeIn');
            document.body.style.overflow = 'hidden'; // Bllokon scroll-in e faqes së parë
            heroSection.classList.add('blur-sm'); // Shton blur-in te sfondi si në foto
        });

        // Funksioni për të mbyllur Katalogun
        btnClose.addEventListener('click', () => {
            catalogOverlay.classList.remove('animate__fadeIn');
            catalogOverlay.classList.add('animate__fadeOut');
            
            // Pret sa të mbarojë animacioni i mbylljes
            setTimeout(() => {
                catalogOverlay.style.display = 'none';
                catalogOverlay.classList.remove('animate__fadeOut');
                document.body.style.overflow = 'auto';
                heroSection.classList.remove('blur-sm');
            }, 500); // 500ms është kohëzgjatja e animacionit fadeOut
        });
    </script>
</body>
</html>
