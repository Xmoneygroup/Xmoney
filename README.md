<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY | Premium Automotive Services</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;900&family=Rajdhani:wght@300;600&display=swap" rel="stylesheet">

    <style>
        :root {
            --gold: #ffcc00;
            --bg: #050505;
            --glass: rgba(255, 255, 255, 0.03);
        }

        body, html {
            margin: 0; padding: 0;
            background-color: var(--bg);
            color: white;
            font-family: 'Rajdhani', sans-serif;
            overflow-x: hidden;
        }

        /* INTRO OVERLAY */
        #loader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #000; display: flex; justify-content: center; align-items: center;
            z-index: 10000;
        }

        .ultra-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 15vw;
            font-weight: 900;
            color: transparent;
            -webkit-text-stroke: 2px var(--gold);
            filter: drop-shadow(0 0 15px var(--gold));
            letter-spacing: 20px;
            transform: scale(0.5);
        }

        /* NAVIGATION */
        nav {
            position: fixed; top: 0; width: 100%;
            padding: 30px 60px; display: flex; justify-content: space-between;
            z-index: 1000; mix-blend-mode: difference;
        }

        .brand { font-family: 'Orbitron'; font-size: 1.8rem; letter-spacing: 5px; color: var(--gold); }

        /* SCROLL CONTAINER */
        .main-wrapper {
            display: flex;
            width: 400vw; /* 4 Seksione */
            height: 100vh;
        }

        section {
            width: 100vw; height: 100vh;
            display: flex; align-items: center; justify-content: center;
            position: relative; overflow: hidden;
            border-right: 1px solid rgba(255,204,0,0.1);
        }

        .canvas-bg {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1;
        }

        .glass-card {
            position: relative; z-index: 2;
            background: var(--glass);
            backdrop-filter: blur(20px);
            padding: 60px;
            border: 1px solid rgba(255,204,0,0.2);
            border-radius: 2px;
            max-width: 600px;
            transform: skewX(-5deg); /* Dizajn agresiv */
        }

        h2 { 
            font-family: 'Orbitron'; font-size: 4.5rem; margin: 0; 
            color: var(--gold); text-transform: uppercase;
            line-height: 0.9;
        }

        p { font-size: 1.5rem; font-weight: 300; letter-spacing: 1px; margin-top: 20px; }

        .btn-translate {
            background: none; border: 1px solid var(--gold); color: var(--gold);
            padding: 10px 25px; cursor: pointer; font-family: 'Orbitron';
            transition: 0.4s; margin-left: 10px;
        }

        .btn-translate:hover { background: var(--gold); color: black; }

        /* FOOTER / CONTACT */
        .contact-info {
            margin-top: 30px;
            border-top: 1px solid var(--gold);
            padding-top: 20px;
        }

        .phone-link {
            font-size: 2.5rem; color: var(--gold); font-family: 'Orbitron';
            text-decoration: none; display: block; margin-top: 10px;
        }

        /* INDICATOR */
        .scroll-hint {
            position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%);
            font-family: 'Orbitron'; font-size: 0.8rem; letter-spacing: 4px;
            color: var(--gold); opacity: 0.5; z-index: 100;
        }

    </style>
</head>
<body>

    <div id="loader">
        <h1 class="ultra-title">UNIKEY</h1>
    </div>

    <nav>
        <div class="brand">UNIKEY // CORE</div>
        <div>
            <button class="btn-translate" onclick="changeLang('sq')">SQ</button>
            <button class="btn-translate" onclick="changeLang('en')">EN</button>
        </div>
    </nav>

    <div class="scroll-hint">SCROLL HORIZONTALISHT</div>

    <div class="main-wrapper">
        
        <section id="keys">
            <div class="canvas-bg" id="canv-1"></div>
            <div class="glass-card">
                <h2 id="t1">ÇELSA AUTOMJETESH</h2>
                <p id="d1">Saktësi milimetrike në duplikim dhe kodim çelsash për çdo model makine në treg.</p>
            </div>
        </section>

        <section id="locks">
            <div class="canvas-bg" id="canv-2"></div>
            <div class="glass-card">
                <h2 id="t2">MEKANIZMAT E SIGURISË</h2>
                <p id="d2">Riparim i bravave, dorezave dhe mekanizmave të dritareve me pjesë origjinale.</p>
            </div>
        </section>

        <section id="diag">
            <div class="canvas-bg" id="canv-3"></div>
            <div class="glass-card">
                <h2 id="t3">DIAGNOSTIKË AVANCUAR</h2>
                <p id="d3">Skanim i plotë elektronik dhe zgjidhje e gabimeve në sistemet më komplekse.</p>
            </div>
        </section>

        <section id="contact">
            <div class="glass-card" style="max-width: 800px; text-align: center;">
                <h2 style="font-size: 6rem;">UNIKEY</h2>
                <div class="contact-info">
                    <p id="exp">MBI 15 VITE EKSPERIENCË NË TEKNOLOGJINË AUTOMOBILISTIKE</p>
                    <p id="hours">HAPUR: E HËNË - E SHTUNË (09:30 - 19:00)</p>
                    <a href="tel:+389070229348" class="phone-link">+389 070 229 348</a>
                </div>
            </div>
        </section>

    </div>

    <script>
        // PËRKTHIMI
        const langData = {
            sq: {
                t1: "ÇELSA AUTOMJETESH", d1: "Saktësi milimetrike në duplikim dhe kodim çelsash për çdo model makine në treg.",
                t2: "MEKANIZMAT E SIGURISË", d2: "Riparim i bravave, dorezave dhe mekanizmave të dritareve me pjesë origjinale.",
                t3: "DIAGNOSTIKË AVANCUAR", d3: "Skanim i plotë elektronik dhe zgjidhje e gabimeve në sistemet më komplekse.",
                exp: "MBI 15 VITE EKSPERIENCË NË TEKNOLOGJINË AUTOMOBILISTIKE", hours: "HAPUR: E HËNË - E SHTUNË (09:30 - 19:00)"
            },
            en: {
                t1: "VEHICLE KEYS", d1: "Millimetric precision in duplication and coding of keys for every car model on the market.",
                t2: "SECURITY MECHANISMS", d2: "Repair of locks, handles, and window mechanisms with original parts.",
                t3: "ADVANCED DIAGNOSTICS", d3: "Full electronic scanning and error resolution in the most complex systems.",
                exp: "OVER 15 YEARS OF EXPERIENCE IN AUTOMOTIVE TECHNOLOGY", hours: "OPEN: MONDAY - SATURDAY (09:30 - 19:00)"
            }
        };

        function changeLang(l) {
            Object.keys(langData[l]).forEach(id => document.getElementById(id).innerText = langData[l][id]);
        }

        // INTRO ANIMATION
        gsap.registerPlugin(ScrollTrigger);
        window.addEventListener('load', () => {
            const tl = gsap.timeline();
            tl.to(".ultra-title", { opacity: 1, scale: 1, letterSpacing: "5px", duration: 2, ease: "expo.out" })
              .to("#loader", { y: "-100%", duration: 1.2, ease: "power4.inOut" });
        });

        // HORIZONTAL SCROLL LOGIC
        let sections = gsap.utils.toArray("section");
        gsap.to(sections, {
            xPercent: -100 * (sections.length - 1),
            ease: "none",
            scrollTrigger: {
                trigger: ".main-wrapper",
                pin: true,
                scrub: 1,
                snap: 1 / (sections.length - 1),
                end: () => "+=" + document.querySelector(".main-wrapper").offsetWidth
            }
        });

        // 3D ENGINE (Improved Explosions)
        function createPro3D(id, color) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            document.getElementById(id).appendChild(renderer.domElement);

            const group = new THREE.Group();
            const particles = [];
            
            // Pjesë më komplekse 3D (Vegla dhe pjesë mekanike)
            for(let i=0; i<60; i++) {
                const geometry = i % 3 === 0 ? new THREE.IcosahedronGeometry(0.3) : 
                                 i % 3 === 1 ? new THREE.CylinderGeometry(0.1, 0.1, 1) : 
                                 new THREE.TorusGeometry(0.2, 0.05, 12, 24);
                
                const material = new THREE.MeshPhongMaterial({ 
                    color: color, 
                    shininess: 100, 
                    wireframe: i % 2 === 0 
                });
                
                const mesh = new THREE.Mesh(geometry, material);
                mesh.position.set(0,0,0);
                particles.push(mesh);
                group.add(mesh);
            }
            scene.add(group);

            const pLight = new THREE.PointLight(varColor = color, 2, 20);
            pLight.position.set(2, 2, 5);
            scene.add(pLight);
            scene.add(new THREE.AmbientLight(0xffffff, 0.3));
            camera.position.z = 8;

            // BUMERANG EXPLOSION (5 SECONDS CYCLE)
            gsap.to(particles.map(p => p.position), {
                x: () => (Math.random() - 0.5) * 20,
                y: () => (Math.random() - 0.5) * 20,
                z: () => (Math.random() - 0.5) * 20,
                duration: 2.5,
                repeat: -1,
                yoyo: true,
                ease: "expo.inOut",
                stagger: 0.005
            });

            function animate() {
                requestAnimationFrame(animate);
                group.rotation.y += 0.003;
                group.rotation.x += 0.002;
                renderer.render(scene, camera);
            }
            animate();
        }

        // Initialize 3D
        createPro3D('canv-1', 0xffcc00); // Gold
        createPro3D('canv-2', 0x00ffff); // Cyan
        createPro3D('canv-3', 0xff0055); // Pink/Red Neon
    </script>
</body>
</html>
