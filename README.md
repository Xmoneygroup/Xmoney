<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UNIKEY - Profesionalizëm në Çelsa & Diagnostikë</title>
    
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

    <style>
        body, html {
            margin: 0; padding: 0;
            font-family: 'Black Ops One', cursive, 'Arial Black', sans-serif;
            background-color: #000; color: white;
            overflow-x: hidden; scroll-behavior: smooth;
        }

        /* ANIMACIONI SUPER I UNIKEY */
        #loader {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle, #1a1a1a 0%, #000 100%);
            display: flex; justify-content: center; align-items: center;
            z-index: 9999;
        }

        .animate-title {
            font-size: 12vw; /* Tekst gjigant */
            font-weight: 900;
            text-transform: uppercase;
            color: #ffcc00;
            opacity: 0;
            filter: drop-shadow(0 0 20px #ffcc00);
            letter-spacing: -50px;
            text-shadow: 0 0 30px rgba(255, 204, 0, 0.8);
        }

        nav {
            position: fixed;
            top: 0; width: 100%;
            display: flex; justify-content: space-between;
            align-items: center;
            padding: 20px 50px;
            box-sizing: border-box;
            z-index: 1000;
            background: rgba(0, 0, 0, 0.85);
            border-bottom: 2px solid #ffcc00;
        }

        .logo { font-size: 2rem; color: #ffcc00; font-weight: bold; }
        .lang-btn {
            background: #ffcc00; border: none; color: black;
            padding: 8px 20px; cursor: pointer; font-weight: bold; margin-left: 10px;
            border-radius: 5px;
        }

        .section {
            height: 100vh; display: flex; align-items: center;
            position: relative; padding: 0 8%;
        }

        .canvas-container {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1;
        }

        .content {
            position: relative; z-index: 2;
            max-width: 700px; /* Më i gjerë */
            background: rgba(0, 0, 0, 0.7);
            padding: 40px;
            border-left: 8px solid #ffcc00;
            backdrop-filter: blur(15px);
        }

        h2 { font-size: 4rem; margin: 0; text-transform: uppercase; color: #ffcc00; }
        p { font-size: 1.8rem; line-height: 1.4; margin-top: 15px; font-family: sans-serif; }

        .footer-info {
            padding: 80px 20px; text-align: center; background: #000;
            border-top: 5px solid #ffcc00;
        }

        .footer-logo { font-size: 6rem; font-weight: 900; color: #ffcc00; margin-bottom: 10px; }
        .contact-card { font-size: 1.5rem; font-family: sans-serif; }
        a { color: #ffcc00; text-decoration: none; font-weight: bold; font-size: 2rem; }

        /* Mobile Adjustments */
        @media (max-width: 768px) {
            h2 { font-size: 2.5rem; }
            p { font-size: 1.2rem; }
            .animate-title { font-size: 20vw; }
        }
    </style>
</head>
<body>

    <div id="loader">
        <h1 class="animate-title">UNIKEY</h1>
    </div>

    <nav>
        <div class="logo">UNIKEY</div>
        <div>
            <button class="lang-btn" onclick="translateTo('sq')">SQ</button>
            <button class="lang-btn" onclick="translateTo('en')">EN</button>
        </div>
    </nav>

    <section class="section">
        <div class="canvas-container" id="canvas-key"></div>
        <div class="content">
            <h2 id="t1">Çelsa Makinash</h2>
            <p id="d1">Duplikat çelsash për çdo lloj makine. Riparime me teknologjinë më të fundit.</p>
        </div>
    </section>

    <section class="section">
        <div class="canvas-container" id="canvas-lock"></div>
        <div class="content">
            <h2 id="t2">Brava & Doreza</h2>
            <p id="d2">Riparim i mekanizmave të bravave dhe dritareve. Siguri maksimale për derën tuaj.</p>
        </div>
    </section>

    <section class="section">
        <div class="canvas-container" id="canvas-diag"></div>
        <div class="content">
            <h2 id="t3">Diagnostikë</h2>
            <p id="d3">Kontroll kompjuterik i avancuar. Gjejmë dhe fshijmë çdo gabim elektronik të makinës suaj.</p>
        </div>
    </section>

    <section class="footer-info">
        <div class="footer-logo">UNIKEY</div>
        <div class="contact-card">
            <p id="exp">Përvojë mbi 15 vite në zanat.</p>
            <p id="hours">Orari: 09:30 - 19:00 (E hënë - E shtunë)</p>
            <p>Tel: <a href="tel:+389070229348">+389 070 229 348</a></p>
        </div>
    </section>

    <script>
        const data = {
            sq: {
                t1: "Çelsa Makinash", d1: "Duplikat çelsash për çdo lloj makine. Riparime me teknologjinë më të fundit.",
                t2: "Brava & Doreza", d2: "Riparim i mekanizmave të bravave dhe dritareve. Siguri maksimale për derën tuaj.",
                t3: "Diagnostikë", d3: "Kontroll kompjuterik i avancuar. Gjejmë dhe fshijmë çdo gabim elektronik të makinës suaj.",
                exp: "Përvojë mbi 15 vite në zanat.", hours: "Orari: 09:30 - 19:00 (E hënë - E shtunë)"
            },
            en: {
                t1: "Car Keys", d1: "Key duplication for all car models. Repairs using the latest technology.",
                t2: "Locks & Handles", d2: "Repair of door locks and window mechanisms. Maximum security for your vehicle.",
                t3: "Diagnostics", d3: "Advanced computer diagnostics. We find and clear all electronic car errors.",
                exp: "Over 15 years of experience in the craft.", hours: "Hours: 09:30 - 19:00 (Mon - Sat)"
            }
        };

        function translateTo(lang) {
            Object.keys(data[lang]).forEach(key => {
                document.getElementById(key).innerText = data[lang][key];
            });
        }

        // ANIMACIONI HYRËS "SUPER"
        gsap.registerPlugin(ScrollTrigger);
        window.addEventListener('load', () => {
            const tl = gsap.timeline();
            tl.to(".animate-title", { 
                opacity: 1, 
                letterSpacing: "10px", 
                duration: 1.5, 
                ease: "back.out(1.7)" 
            })
            .to(".animate-title", { 
                textShadow: "0 0 60px rgba(255, 204, 0, 1)", 
                repeat: 3, 
                yoyo: true, 
                duration: 0.2 
            })
            .to("#loader", { 
                clipPath: "circle(0% at 50% 50%)", 
                duration: 1.5, 
                ease: "expo.inOut" 
            });
        });

        // KRIJIMI I ANIMACIONEVE 3D ME EFEKT BUMERANG
        function initScene(id, color, type) {
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            document.getElementById(id).appendChild(renderer.domElement);

            const group = new THREE.Group();
            const parts = [];
            
            // Krijo pjesë të ndryshme në varësi të shërbimit
            for(let i=0; i<40; i++) {
                let geom;
                if(type === 'diag') { 
                    geom = new THREE.TorusGeometry(0.2, 0.05, 16, 100); // Rrathë elektronikë
                } else {
                    geom = i % 2 === 0 ? new THREE.BoxGeometry(0.5, 0.1, 0.2) : new THREE.CylinderGeometry(0.05, 0.05, 0.8);
                }
                
                const mat = new THREE.MeshStandardMaterial({ 
                    color: color, 
                    metalness: 0.9, 
                    roughness: 0.1,
                    emissive: type === 'diag' ? color : 0x000000,
                    emissiveIntensity: 0.5
                });
                const mesh = new THREE.Mesh(geom, mat);
                parts.push(mesh);
                group.add(mesh);
            }
            scene.add(group);

            const light = new THREE.PointLight(0xffffff, 2, 50);
            light.position.set(5, 5, 5);
            scene.add(light);
            scene.add(new THREE.AmbientLight(0xffffff, 0.5));
            camera.position.z = 7;

            // ANIMACIONI BUMERANG 5 SEKONDA
            gsap.to(parts.map(p => p.position), {
                x: () => (Math.random() - 0.5) * 15,
                y: () => (Math.random() - 0.5) * 15,
                z: () => (Math.random() - 0.5) * 15,
                duration: 2.5,
                repeat: -1,
                yoyo: true,
                ease: "power2.inOut",
                stagger: { each: 0.02, from: "center" },
                scrollTrigger: { trigger: `#${id}`, start: "top center" }
            });

            function animate() {
                requestAnimationFrame(animate);
                group.rotation.y += 0.01;
                group.rotation.x += 0.005;
                renderer.render(scene, camera);
            }
            animate();
        }

        initScene('canvas-key', 0xffcc00, 'key');
        initScene('canvas-lock', 0xcccccc, 'lock');
        initScene('canvas-diag', 0x00ff00, 'diag'); // Ngjyrë jeshile për diagnostikën

    </script>
</body>
</html>
