<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xmesage | Stealth Access</title>
    <style>
        /* Base Styling */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background: #000000; /* Zi e pastër siç e kërkove */
            font-family: 'Inter', sans-serif;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Container kryesor */
        .main-layout {
            display: flex;
            width: 90%;
            max-width: 1200px;
            align-items: center;
            justify-content: space-between;
            z-index: 10;
        }

        /* Logoja jote "X" e Integruar si SVG për pastërti maksimale */
        .logo-section {
            flex: 1;
            display: flex;
            justify-content: center;
        }

        .custom-x {
            width: 450px;
            height: auto;
            filter: drop-shadow(0 0 15px rgba(255, 255, 255, 0.2));
            animation: logoFloat 4s ease-in-out infinite;
        }

        @keyframes logoFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* Seksioni i Login-it */
        .login-section {
            flex: 1;
            padding-left: 50px;
            color: white;
        }

        h1 {
            font-size: 4rem;
            font-weight: 900;
            margin-bottom: 40px;
            letter-spacing: -2px;
        }

        .button-group {
            display: flex;
            flex-direction: column;
            gap: 15px;
            max-width: 320px;
        }

        /* Butonat e Rinj - Stil i mprehtë dhe Premium */
        .btn-custom {
            padding: 18px;
            border-radius: 4px; /* Më pak të rrumbullakosur, më shumë agresivë */
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .google-btn {
            background: #ffffff;
            color: #000;
            border: none;
        }

        .apple-btn {
            background: transparent;
            color: #ffffff;
            border: 1px solid #444;
        }

        .create-btn {
            background: #1d9bf0; /* Një blu elektrike neon */
            color: white;
            border: none;
            margin-top: 10px;
            box-shadow: 0 4px 15px rgba(29, 155, 240, 0.3);
        }

        .btn-custom:hover {
            transform: scale(1.03);
            filter: brightness(1.2);
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.1);
        }

        /* Galaxy Overlay i lehtë */
        #stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }
    </style>
</head>
<body>

    <canvas id="stars"></canvas>

    <div class="main-layout">
        <!-- Logoja jote "X" (E rikrijuar bazuar në foton tënde) -->
        <div class="logo-section">
            <svg class="custom-x" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M20 10L45 50L15 90M80 10L55 50L85 90" stroke="white" stroke-width="8" stroke-linecap="square"/>
                <path d="M35 10L65 90" stroke="white" stroke-width="2" stroke-dasharray="2 2"/>
                <!-- Këtu kam simuluar format e mprehta të logos tënde -->
                <path d="M10 85L90 15M30 15L75 80" stroke="white" stroke-width="6" />
            </svg>
        </div>

        <!-- Forma e Login-it -->
        <div class="login-section">
            <h1>Po ndodh tani.</h1>
            <div class="button-group">
                <button class="btn-custom google-btn">Hyni me Google</button>
                <button class="btn-custom apple-btn">Hyni me Apple</button>
                <div style="text-align: center; color: #444; margin: 10px 0;">OSE</div>
                <button class="btn-custom create-btn">Krijo llogari</button>
            </div>
        </div>
    </div>

    <script>
        // Animacion i thjeshtë yjesh për sfondin e zi
        const canvas = document.getElementById('stars');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const starList = Array.from({ length: 150 }, () => ({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            size: Math.random() * 1.5,
            opacity: Math.random()
        }));

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            starList.forEach(s => {
                ctx.fillStyle = `rgba(2E kuptoj plotësisht, vëlla. Atë logon "X" që ke krijuar ti është shumë më agresive dhe i shkon fiks stilit **Mansory** dhe bisedave për **Xmesage**. Do ta heqim atë logon gjenerike dhe do ta integrojmë tënden si element kryesor në sfondin e zi "pure black".

Për butonat, do t'i bëjmë me një stil më "sharp" (të mprehtë) dhe me shkëlqim neon që të mos duken si të tjerët.

Ja kodi i përditësuar për **Xmesage.com**:
```html
<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xmesage | Stealth Access</title>
    <style>
        /* Base Styling */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background: #000000; /* Zi e pastër siç e kërkove */
            font-family: 'Inter', sans-serif;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Container kryesor */
        .main-layout {
            display: flex;
            width: 90%;
            max-width: 1200px;
            align-items: center;
            justify-content: space-between;
            z-index: 10;
        }

        /* Logoja jote "X" e Integruar si SVG për pastërti maksimale */
        .logo-section {
            flex: 1;
            display: flex;
            justify-content: center;
        }

        .custom-x {
            width: 450px;
            height: auto;
            filter: drop-shadow(0 0 15px rgba(255, 255, 255, 0.2));
            animation: logoFloat 4s ease-in-out infinite;
        }

        @keyframes logoFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* Seksioni i Login-it */
        .login-section {
            flex: 1;
            padding-left: 50px;
            color: white;
        }

        h1 {
            font-size: 4rem;
            font-weight: 900;
            margin-bottom: 40px;
            letter-spacing: -2px;
        }

        .button-group {
            display: flex;
            flex-direction: column;
            gap: 15px;
            max-width: 320px;
        }

        /* Butonat e Rinj - Stil i mprehtë dhe Premium */
        .btn-custom {
            padding: 18px;
            border-radius: 4px; /* Më pak të rrumbullakosur, më shumë agresivë */
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .google-btn {
            background: #ffffff;
            color: #000;
            border: none;
        }

        .apple-btn {
            background: transparent;
            color: #ffffff;
            border: 1px solid #444;
        }

        .create-btn {
            background: #1d9bf0; /* Një blu elektrike neon */
            color: white;
            border: none;
            margin-top: 10px;
            box-shadow: 0 4px 15px rgba(29, 155, 240, 0.3);
        }

        .btn-custom:hover {
            transform: scale(1.03);
            filter: brightness(1.2);
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.1);
        }

        /* Galaxy Overlay i lehtë */
        #stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }
    </style>
</head>
<body>

    <canvas id="stars"></canvas>

    <div class="main-layout">
        <!-- Logoja jote "X" (E rikrijuar bazuar në foton tënde) -->
        <div class="logo-section">
            <svg class="custom-x" viewBox="0 0 100 100" fill="none" xmlns="[http://www.w3.org/2000/svg](http://www.w3.org/2000/svg)">
                <path d="M20 10L45 50L15 90M80 10L55 50L85 90" stroke="white" stroke-width="8" stroke-linecap="square"/>
                <path d="M35 10L65 90" stroke="white" stroke-width="2" stroke-dasharray="2 2"/>
                <!-- Këtu kam simuluar format e mprehta të logos tënde -->
                <path d="M10 85L90 15M30 15L75 80" stroke="white" stroke-width="6" />
            </svg>
        </div>

        <!-- Forma e Login-it -->
        <div class="login-section">
            <h1>Po ndodh tani.</h1>
            <div class="button-group">
                <button class="btn-custom google-btn">Hyni me Google</button>
                <button class="btn-custom apple-btn">Hyni me Apple</button>
                <div style="text-align: center; color: #444; margin: 10px 0;">OSE</div>
                <button class="btn-custom create-btn">Krijo llogari</button>
            </div>
        </div>
    </div>

    <script>
        // Animacion i thjeshtë yjesh për sfondin e zi
        const canvas = document.getElementById('stars');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const starList = Array.from({ length: 150 }, () => ({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            size: Math.random() * 1.5,
            opacity: Math.random()
        }));

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            starList.forEach(s => {
                ctx.fillStyle = `rgba(255, 255, 255, ${s.opacity})`;
                ctx.beginPath();
                ctx.arc(s.x, s.y, s.size, 0, Math.PI * 2);
                ctx.fill();
            });
        }
        draw();
    </script>
</body>
</html>
