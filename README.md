<!DOCTYPE html>
<html lang="sq">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Domain | Minimalist VIP</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Montserrat:wght@200;400&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: #000;
        }

        /* SFONDI AURORA ME GRADIENTË DINAMIKË */
        .aurora-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            filter: blur(100px); /* Krijon shkrirjen e dritave */
            opacity: 0.6;
        }

        .aurora-blob {
            position: absolute;
            width: 600px;
            height: 600px;
            border-radius: 50%;
            animation: move 20s infinite alternate;
        }

        .blob-1 {
            background: rgba(0, 150, 255, 0.4);
            top: -10%;
            left: -10%;
        }

        .blob-2 {
            background: rgba(0, 255, 200, 0.3);
            bottom: -10%;
            right: -10%;
            animation-duration: 25s;
        }

        .blob-3 {
            background: rgba(0, 50, 200, 0.5);
            top: 40%;
            left: 30%;
            animation-duration: 30s;
        }

        @keyframes move {
            from { transform: translate(0, 0) scale(1); }
            to { transform: translate(200px, 100px) scale(1.5); }
        }

        /* KONTENTI */
        .content {
            position: relative;
            z-index: 10;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .main-title {
            font-family: 'Cinzel', serif;
            font-size: 5rem;
            color: #fff;
            letter-spacing: 25px;
            margin: 0;
            text-transform: uppercase;
            /* Shkëlqim i pastër i bardhë VIP */
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.5), 0 0 40px rgba(0, 200, 255, 0.3);
            animation: fadeIn 3s ease-out;
        }

        .info-box {
            margin-top: 40px;
            border-left: 1px solid rgba(0, 255, 255, 0.3);
            border-right: 1px solid rgba(0, 255, 255, 0.3);
            padding: 10px 40px;
            animation: lineExpand 2s ease-out forwards 1s;
            opacity: 0;
        }

        .subtitle {
            font-family: 'Montserrat', sans-serif;
            color: #fff;
            font-size: 1.2rem;
            letter-spacing: 12px;
            text-transform: uppercase;
            font-weight: 200;
        }

        @keyframes fadeIn {
            from { opacity: 0; filter: blur(20px); transform: scale(1.1); }
            to { opacity: 1; filter: blur(0); transform: scale(1); }
        }

        @keyframes lineExpand {
            from { opacity: 0; width: 0; }
            to { opacity: 1; width: auto; }
        }

        /* REAGIMI I MAUSIT (Kursor VIP) */
        .cursor-glow {
            position: fixed;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(0, 255, 255, 0.1) 0%, transparent 70%);
            border-radius: 50%;
            pointer-events: none;
            z-index: 5;
            transform: translate(-50%, -50%);
        }

        @media (max-width: 768px) {
            .main-title { font-size: 2.5rem; letter-spacing: 10px; }
            .subtitle { font-size: 0.8rem; letter-spacing: 6px; }
        }
    </style>
</head>
<body>

    <div class="aurora-container">
        <div class="aurora-blob blob-1"></div>
        <div class="aurora-blob blob-2"></div>
        <div class="aurora-blob blob-3"></div>
    </div>

    <div class="cursor-glow" id="cursor"></div>

    <div class="content">
        <h1 class="main-title">Domain Sale</h1>
        <div class="info-box">
            <p class="subtitle">This Domain is for Sale</p>
        </div>
    </div>

    <script>
        const cursor = document.getElementById('cursor');
        window.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
        });
    </script>

</body>
</html>
