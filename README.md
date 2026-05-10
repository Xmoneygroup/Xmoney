<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>XKAPO | Authority</title>
    <style>
        /* RESET TOTAL & BASE */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body, html { 
            width: 100%; height: 100%; 
            background-color: #000; 
            overflow: hidden; 
            position: fixed; 
            font-family: 'Helvetica Neue', Arial, sans-serif;
        }

        /* 1. INTRO LOGO (NUK PREKET) */
        #intro-splash {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-color: #000;
            display: flex; justify-content: center; align-items: center;
            z-index: 10000;
            transition: opacity 0.8s ease;
        }

        .logo-anim {
            max-width: 250px; 
            height: auto;
            opacity: 0;
            transform: scale(0.98);
            animation: logoFlash 2s forwards;
        }

        @keyframes logoFlash {
            0% { opacity: 0; transform: scale(0.98); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(1.02); }
        }

        /* 2. NAVIGATION (NUK PREKET) */
        nav {
            position: fixed; top: 0; width: 100%; padding: 25px 40px;
            display: flex; justify-content: space-between; align-items: center;
            z-index: 2000;
            background: linear-gradient(to bottom, rgba(0,0,0,0.8), transparent);
            color: white;
            text-transform: uppercase; letter-spacing: 3px;
        }
        
        .nav-logo { font-size: 20px; font-weight: bold; letter-spacing: 6px; }
        
        .contact-btn { 
            border: 1px solid #fff; padding: 10px 20px; 
            text-decoration: none; color: #fff; font-size: 11px;
            transition: 0.3s; 
        }
        .contact-btn:hover { background: #fff; color: #000; }

        /* 3. NEON BACKGROUND - E SHTUAR RE RE */
        #neon-ambient {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: 1; /* Qëndron pas çdo gjëje */
            pointer-events: none; /* Nuk pengon klikimet */
            opacity: 0; /* Shfaqet pas intros */
            transition: opacity 2s ease;
        }

        .neon-glow {
            position: absolute;
            border-radius: 50%;
            filter: blur(100px); /* Krijon shkëlqimin neon */
            animation: moveNeon 15s infinite ease-in-out;
        }

        /* Ngjyrat e Neonit */
        .neon-glow.one {
            width: 300px; height: 300px;
            background: rgba(0, 255, 255, 0.2); /* Neon Blue */
            top: -100px; left: -100px;
        }

        .neon-glow.two {
            width: 400px; height: 400px;
            background: rgba(255, 0, 255, 0.1); /* Neon Magenta */
            bottom: -200px; right: -100px;
            animation-delay: -5s;
        }

        .neon-glow.three {
            width: 250px; height: 250px;
            background: rgba(0, 255, 0, 0.15); /* Neon Green */
            top: 40%; right: 20%;
            animation-delay: -10s;
        }

        @keyframes moveNeon {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(50px, -30px) rotate(5deg); }
            50% { transform: translate(20px, 50px) rotate(-3deg); }
            75% { transform: translate(-30px, 20px) rotate(2deg); }
        }

        /* 4. HOME PAGE & SLIDER (NUK PREKET) */
        #home-content { opacity: 0; width: 100%; height: 100%; position: relative; transition: opacity 1s; z-index: 5;}
        .slider-container { width: 100%; height: 100%; position: relative; z-index: 5; }
        
        .slide {
            position: absolute; width: 100%; height: 100%;
            background-size: cover; 
            background-position: center;
            background-repeat: no-repeat;
            opacity: 0;
            transition: opacity 1.5s ease-in-out;
            z-index: 10;
        }
        
        .slide.active { opacity: 1; z-index: 20; } 

        /* OVERLAY PREMIUM LEHTË (Z-INDEX AKTUALIZUAR) */
        .overlay { 
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle, transparent 30%, rgba(0,0,0,0.6) 100%);
            z-index: 25; /* Mbi fotot */
            pointer-events: none; 
        }
    </style>
</head>
<body>

    <div id="intro-splash">
        <img src="9BA7D80D-DB0A-4D39-9C65-6FD915BCF247.jpg" alt="XKAPO" class="logo-anim">
    </div>

    <div id="neon-ambient">
        <div class="neon-glow one"></div>
        <div class="neon-glow two"></div>
        <div class="neon-glow three"></div>
    </div>

    <div id="home-content">
        <nav>
            <div class="nav-logo">XKAPO</div>
            <a href="tel:+389070878227" class="contact-btn">CONTACT</a>
        </nav>

        <div class="slider-container">
            <div class="overlay"></div>
            
            <div class="slide active" style="background-image: url('IMG_1022.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1024.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1025.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1026.jpg');"></div>
            <div class="slide" style="background-image: url('IMG_1027.jpg');"></div>
        </div>
    </div>

    <script>
        // TRANZICIONI NGA LOGO TE HOME (PËRDITËSUAR PËR NEON)
        window.addEventListener('load', () => {
            const splash = document.getElementById('intro-splash');
            const home = document.getElementById('home-content');
            const neon = document.getElementById('neon-ambient'); // RE RE
            
            initMansorySlider();

            setTimeout(() => {
                splash.style.opacity = '0'; // Zbehet logoja
                neon.style.opacity = '1'; // Shfaqet Neoni lehtë (RE RE)
                
                setTimeout(() => {
                    splash.style.display = 'none'; // Zhduket logoja
                    home.style.opacity = '1'; // Shfaqet Home Page
                }, 800); 
            }, 2000); // 2 sekonda shfaqet logoja
        });

        // MANSORY STYLE SLIDER (FADE) - 3.5 SEKONDA (NUK PREKET)
        function initMansorySlider() {
            const slides = document.querySelectorAll('.slide');
            let current = 0;
            const totalSlides = slides.length;

            if (totalSlides === 0) return; 

            setInterval(() => {
                slides[current].classList.remove('active'); 
                current = (current + 1) % totalSlides;
                slides[current].classList.add('active'); 
            }, 3500);
        }
    </script>
</body>
</html>
