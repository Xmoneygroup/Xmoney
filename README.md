<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MkdMap - Welcome to Macedonia</title>
    <style>
        /* --- STILI PËR EKRANIN HYRËS (SPLASH SCREEN) --- */
        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #0f172a;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 1;
            transition: opacity 0.5s ease;
        }

        .splash-text {
            color: #ffffff;
            font-family: sans-serif;
            font-size: 2.2rem;
            font-weight: bold;
            letter-spacing: 2px;
            text-transform: uppercase;
            text-align: center;
            padding: 0 20px;
        }

        /* --- STILI PËR FAQEN KRYESORE --- */
        body {
            margin: 0;
            padding: 0;
            background-color: #f8fafc;
            font-family: sans-serif;
        }

        header {
            width: 100%;
            padding: 20px 0;
            background-color: #ffffff;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .main-title {
            margin: 0;
            font-size: 1.4rem;
            font-weight: bold;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: #0f172a;
        }

        .content-placeholder {
            text-align: center;
            margin-top: 100px;
            color: #64748b;
        }
    </style>
</head>
<body>

    <!-- 1. SPLASH SCREEN -->
    <div id="splash-screen">
        <div class="splash-text">Welcome to Macedonia</div>
    </div>

    <!-- 2. HOME PAGE -->
    <header>
        <h1 class="main-title">mkdmap</h1>
    </header>

    <main>
        <div class="content-placeholder">
            <p>Faqja u ngarkua me sukses në GitHub! Po presim instruksionet e radhës...</p>
        </div>
    </main>

    <!-- 3. ANIMACIONI 2 SEKONDA -->
    <script>
        window.addEventListener("DOMContentLoaded", function() {
            setTimeout(function() {
                var splash = document.getElementById("splash-screen");
                splash.style.opacity = "0";
                setTimeout(function() {
                    splash.style.display = "none";
                }, 500); // kjo e heq plotësisht pasi bëhet transparente
            }, 2000); // 2 sekonda vonesë
        });
    </script>

</body>
</html>
