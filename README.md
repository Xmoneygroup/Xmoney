<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY | Mansory Edition Professional Services</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Montserrat:wght@300;600;800&display=swap" rel="stylesheet">

    <style>
        :root {
            --gold: #c5a059; /* Ngjyra Gold Mansory */
            --dark: #0a0a0a;
            --carbon: #121212;
        }

        body, html {
            margin: 0; padding: 0;
            background-color: var(--dark);
            color: white;
            font-family: 'Montserrat', sans-serif;
            overflow-x: hidden;
        }

        /* CARBON BACKGROUND EFFECT */
        .carbon-bg {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                linear-gradient(45deg, #111 25%, transparent 25%), 
                linear-gradient(-45deg, #111 25%, transparent 25%), 
                linear-gradient(45deg, transparent 75%, #111 75%), 
                linear-gradient(-45deg, transparent 75%, #111 75%);
            background-size: 4px 4px;
            background-color: #0d0d0d;
            z-index: -2; opacity: 0.5;
        }

        /* INTRO MANSORY STYLE */
        #loader {
            position: fixed; inset: 0; background: #000;
            display: flex; justify-content: center; align-items: center; z-index: 10000;
        }

        .unikey-logo-intro {
            font-family: 'Cinzel', serif;
            font-size: 8vw; color: var(--gold);
            letter-spacing: 20px; filter: drop-shadow(0 0 20px rgba(197, 160, 89, 0.5));
            opacity: 0;
        }

        /* NAVBAR */
        nav {
            position: fixed; top: 0; width: 100%;
            display: flex; justify-content: space-between; align-items: center;
            padding: 30px 60px; z-index: 1000;
            background: linear-gradient(to bottom, rgba(0,0,0,0.8), transparent);
        }

        .brand { font-family: 'Cinzel', serif; font-size: 2rem; color: var(--gold); letter-spacing: 5px; }
        
        .lang-switch button {
            background: none; border: 1px solid var(--gold); color: var(--gold);
            padding: 5px 15px; cursor: pointer; font-family: 'Montserrat'; font-weight: 600;
            transition: 0.3s;
        }
        .lang-switch button:hover { background: var(--gold); color: black; }

        /* HERO SECTION */
        .hero {
            height: 100vh; display: flex; flex-direction: column;
            justify-content: center; align-items: center; text-align: center;
            background: radial-gradient(circle, rgba(197,160,89,0.1) 0%, transparent 70%);
        }

        .hero h1 {
            font-family: 'Cinzel', serif; font-size: 5rem; margin: 0;
            text-transform: uppercase; letter-spacing: 10px;
        }

        .hero p { font-size: 1.2rem; letter-spacing: 5px; opacity: 0.7; margin-top: 10px; }

        .btn-main {
            margin-top: 40px; padding: 15px 40px;
            background: none; border: 1px solid var(--gold);
            color: var(--gold); font-family: 'Cinzel'; font-size: 1.2rem;
            cursor: pointer; transition: 0.5s; position: relative; overflow: hidden;
        }
        .btn-main:hover { background: var(--gold); color: black; box-shadow: 0 0 30px var(--gold); }

        /* SECTIONS */
        section {
            height: 100vh; display: flex; align-items: center;
            padding: 0 10%; position: relative;
            border-bottom: 1px solid rgba(197, 160, 89, 0.1);
        }

        .content-box {
            max-width: 500px; z-index: 10;
            background: rgba(0, 0, 0, 0.6); padding: 40px;
            border: 1px solid rgba(197, 160, 89, 0.3);
            backdrop-filter: blur(10px);
        }

        h2 { font-family: 'Cinzel', serif; font-size: 2.5rem; color: var(--gold); margin: 0; }
        p { font-size: 1.1rem; line-height: 1.6; margin-top: 20px; font-weight: 300; }

        .canvas-container {
            position: absolute; right: 0; top: 0; width: 60vw; height: 100%; z-index: 1;
        }

        /* FOOTER */
        footer {
            padding: 100px 10%; background: #050505; text-align: center;
            border-top: 2px solid var(--gold);
        }

        .footer-title { font-family: 'Cinzel', serif; font-size: 4rem; color: var(--gold); }
        .contact-info { margin-top: 30px; font-size: 1.5rem; }
        .contact-info a { color: var(--gold); text-decoration: none; font-weight: 800; font-size: 2.5rem; display: block; margin-top: 10px; }

    </style>
</head>
<body>

    <div id="loader">
        <div class="unikey-logo-intro">UNIKEY</div>
    </div>

    <div class="carbon-bg"></div>

    <nav>
        <div class="brand">UNIKEY</div>
        <div class="lang-switch">
            <button onclick="translate('sq')">ALB</button>
            <button onclick="translate('en')">ENG</button>
        </div>
    </nav>

    <main>
        <section class="hero">
            <h1 id="h1">Teknologjia e Çelsave</h1>
            <p id="p1">RIPARIM DHE KODIM PËR ÇDO MARKË MAKINASH</p>
            <button class="btn-main" id="b1" onclick="window.location.href='tel:+389070229348'">KONTAKTO TANI</button>
        </section>

        <section>
            <div class="content-box">
                <h2 id="t2">DUPLIKAT ÇELSASH</h2>
                <p id="d2">Saktësi milimetrike në çdo prerje dhe kodim. Përdorim teknologjinë më të fundit për çelsa inteligjentë dhe mekanikë.</p>
            </div>
            <div class="canvas-container" id="c1"></div>
        </section>

        <section>
            <div class="canvas-container" style="left:0;" id="c2"></div>
            <div class="content-box" style="margin-left: auto;">
                <h2 id="t3">RIPARIM BRAVASH</h2>
                <p id="d3">Siguri dhe funksionalitet. Riparojmë bravat e derës dhe mekanizmat e dritareve sikur të ishin të reja.</p>
            </div>
        </section>

        <section>
            <div class="content-box">
                <h2 id="t4">DIAGNOSTIKË</h2>
                <p id="d4">Gjejmë dhe zgjidhim çdo gabim elektronik. Skanim i plotë i moduleve të makinës tuaj.</p>
            </div>
            <div class="canvas-container" id="c3"></div>
        </section>
    </main>

    <footer>
        <div class="footer-title">UNIKEY</div>
        <div class="contact-info">
            <p id="exp">Mbi 15 Vite Eksperiencë</p>
            <p id="hours">Hapur: 09:30 - 19:00 (Hënë - Shtunë)</p>
            <a href="tel:+389070229348">+389 070 229 348</a>
        </div>
    </footer>

    <script>
        // LOGJIKA E PËRKTHIMIT
        const langData = {
            sq: {
                h1: "Teknologjia e Çelsave", p1: "RIPARIM DHE KODIM PËR ÇDO MARKË MAKINASH", b1: "KONTAKTO TANI",
                t2: "DUPLIKAT ÇELSASH", d2: "Saktësi milimetrike në çdo prerje dhe kodim. Përdorim teknologjinë më të fundit.",
                t3: "RIPARIM BRAVASH", d3: "Siguri dhe funksionalitet. Riparojmë bravat dhe mekanizmat e dritareve.",
                t4: "DIAGNOSTIKË", d4: "Gjejmë dhe zgjidhim çdo gabim elektronik. Skanim i plotë i moduleve.",
                exp: "Mbi 15 Vite Eksperiencë", hours: "Hapur: 09:30 - 19:00 (Hënë - Shtunë)"
            },
            en: {
                h1: "Key Technology", p1: "REPAIR AND CODING FOR EVERY CAR BRAND", b1: "CONTACT NOW",
                t2: "KEY DUPLICATION", d2: "Millimetric precision in every cut and coding. We use the latest technology.",
                t3: "LOCK REPAIR", d3: "Security and functionality. We repair door locks and window mechanisms.",
                t4: "DIAGNOSTICS", d4: "We find and solve every electronic error. Full scanning of your car modules.",
                exp: "Over 15 Years of Experience", hours: "Open: 09:30 - 19:00 (Mon - Sat)"
            }
        };

        function translate(l) {
            Object.keys(langData[l]).forEach(id => {
                document.getElementById(id).innerText = langData[l][id];
            });
        }

        // ANIMACIONET
        gsap.registerPlugin(ScrollTrigger);
        window.addEventListener('load', () => {
            const tl = gsap.timeline();
            tl.to(".unikey-logo-intro", { opacity: 1, letterSpacing: "10px", duration: 1.5, ease: "power4.out" })
              .to("#loader", { y: "-100%", duration: 1, ease: "expo.inOut" });
        });

        // 3D ENGINE (MANSORY EDITION)
        function init3D(id, color) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, 1, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            const container = document.getElementById(id);
            renderer.setSize(container.offsetWidth, container.offsetHeight);
            container.appendChild(renderer.domElement);

            const group = new THREE.Group();
            const pieces = [];

            // Pjesë "Gold & Carbon"
            for(let i=0; i<40; i++) {
                const geo = i % 2 === 0 ? new THREE.TorusGeometry(0.3, 0.05, 16, 100) : new THREE.BoxGeometry(0.4, 0.4, 0.4);
                const mat = new THREE.MeshStandardMaterial({ 
                    color: i % 5 === 0 ? 0xc5a059 : 0x333333, 
                    metalness: 1, roughness: 0.1 
                });
                const mesh = new THREE.Mesh(geo, mat);
                pieces.push(mesh);
                group.add(mesh);
            }
            scene.add(group);
            const light = new THREE.PointLight(0xffffff, 2, 50);
            light.position.set(5, 5, 5);
            scene.add(light);
            scene.add(new THREE.AmbientLight(0xffffff, 0.5));
            camera.position.z = 5;

            // Efekti Bumerang (5 sekonda cikël)
            gsap.to(pieces.map(p => p.position), {
                x: () => (Math.random() - 0.5) * 12,
                y: () => (Math.random() - 0.5) * 12,
                z: () => (Math.random() - 0.5) * 12,
                duration: 2.5,
                repeat: -1,
                yoyo: true,
                ease: "power2.inOut",
                stagger: 0.01,
                scrollTrigger: { trigger: `#${id}`, start: "top center" }
            });

            function animate() {
                requestAnimationFrame(animate);
                group.rotation.y += 0.005;
                renderer.render(scene, camera);
            }
            animate();
        }

        init3D('c1', 0xc5a059); // Gold
        init3D('c2', 0x888888); // Silver
        init3D('c3', 0xc5a059); // Gold
    </script>
</body>
</html>
