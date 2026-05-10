<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XKAPO | Authority</title>
    <style>
        /* RESET */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body, html { width: 100%; height: 100%; background-color: #000; color: #fff; font-family: 'Helvetica Neue', Arial, sans-serif; overflow: hidden; }

        /* Udhëzim për logon: Sigurohu që prapavija e fotos së logos të jetë e zezë fiks si #000 */
        #intro-splash {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-color: #000; /* E zeza e pastër */
            display: flex; justify-content: center; align-items: center;
            z-index: 10000; transition: opacity 0.8s ease;
        }

        .logo-anim {
            max-width: 300px; height: auto; opacity: 0;
            animation: mansoryFade 2s forwards;
        }

        @keyframes mansoryFade {
            0% { opacity: 0; transform: scale(0.95); }
            50% { opacity: 1; transform: scale(1); }
            100% { opacity: 0; transform: scale(1.05); }
        }

        /* NAVIGATION (MANSORY STYLE) */
        nav {
            position: fixed; top: 0; width: 100%; padding: 25px 60px;
            display: flex; justify-content: space-between; align-items: center;
            z-index: 2000; background: linear-gradient(to bottom, rgba(0,0,0,0.6), transparent);
            text-transform: uppercase; font-size: 11px; letter-spacing: 2px;
        }
        .nav-links { display: flex; gap: 30px; }
        .nav-links a { text-decoration: none; color: #fff; font-weight: 300; transition: opacity 0.3s; }
        .nav-links a:hover { opacity: 0.6; }
        .nav-logo { font-size: 22px; letter-spacing: 8px; font-weight: 400; }
        .contact-btn { border: 1px solid rgba(255,255,255,0.4); padding: 8px 20px; transition: 0.3s; text-decoration: none; color: #fff;}
        .contact-btn:hover { background: #fff; color: #000; border-color: #fff; }

        /* SLIDER SECTION */
        #home-content { opacity: 0; transition: opacity 1s ease; height: 100vh; width: 100%; position: relative;}
        .slider-container { width: 100%; height: 100%; position: relative; }
        .slide {
            position: absolute; width: 100%; height: 100%;
            background-size: cover; background-position: center;
            opacity: 0; transition: opacity 1.5s ease-in-out;
            z-index: 1;
        }
        .slide.active { opacity: 1; z-index: 2; }

        /* VIGNETTE OVERLAY */
        .overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle, transparent 20%, rgba(0,0,0,0.5) 100%);
            z-index: 5; pointer-events: none; }

        /* INDICATORS */
        .indicators { position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%); display: flex; gap: 15px; z-index: 1000; }
        .dot { width: 40px; height: 2px; background: rgba(255,255,255,0.3); transition: 0.3s; }
        .dot.active { background: #fff; }
    </style>
</head>
<body>

    <div id="intro-splash">
        <img src="logo.jpg" alt="XKAPO" class="logo-anim">
    </div>

    <div id="home-content">
        <nav>
            <div class="nav-links"><a>Models</a><a>Performance</a><a>Carbon</a></div>
            <div class="nav-logo">XKAPO</div>
            <div class="nav-links">
                <a href="tel:+389070878227" class="contact-btn">Contact Us</a>
            </div>
        </nav>

        <div class="slider-container">
            <div class="overlay"></div>
            
            <div class="slide active" style="background-image: url('car1.jpg');"></div>
            <div class="slide" style="background-image: url('car2.jpg');"></div>
            <div class="slide" style="background-image: url('car3.jpg');"></div>
            <div class="slide" style="background-image: url('car4.jpg');"></div>
            <div class="slide" style="background-image: url('car5.jpg');"></div>

            <div class="indicators">
                <div class="dot active"></div>
                <div class="dot"></div>
                <div class="dot"></div>
                <div class="dot"></div>
                <div class="dot"></div>
            </div>
        </div>
    </div>

    <script>
        // HANDLE INTRO AND SHOW HOME
        // Përdorim 'load' në vend të 'DOMContentLoaded' që të presim ngarkimin e plotë të fotove
        window.addEventListener('load', () => {
            const splash = document.getElementById('intro-splash');
            const home = document.getElementById('home-content');
            
            // Fillon slider-in menjëherë në prapavijë
            initMansorySlider();

            // Pas 2 sekondash, heqim splash screen
            setTimeout(() => {
                splash.style.opacity = '0';
                setTimeout(() => {
                    splash.style.display = 'none';
                    home.style.opacity = '1';
                }, 800); // Koha e tranzicionit të opacity
            }, 2000); // Koha e shfaqjes së logos
        });

        // SLIDER LOGIC (3.5 SECONDS)
        function initMansorySlider() {
            const slides = document.querySelectorAll('.slide');
            const dots = document.querySelectorAll('.dot');
            let current = 0;
            const totalSlides = slides.length;

            if (totalSlides === 0) return; // Siguresa nëse nuk ka foto

            setInterval(() => {
                // Heqim klasën 'active' nga fotoja dhe doti aktual
                slides[current].classList.remove('active');
                dots[current].classList.remove('active');
                
                // Llogarisim foton tjetër
                current = (current + 1) % totalSlides;
                
                // Shtojmë klasën 'active' te fotoja dhe doti i ri
                slides[current].classList.add('active');
                dots[current].classList.add('active');
            }, 3500); // Koha e qëndrimit të çdo fotoje
        }
    </script>
</body>
</html>
