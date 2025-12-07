
<html lang="en">

    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Premium Xmoney - Business Success</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;700&family=Cinzel:wght@600;700&display=swap');

        body {
            margin: 0;
            padding: 0;
            font-family: 'Montserrat', sans-serif;
            background: linear-gradient(135deg, #000000, #1a1a2e, #16213e);
            color: #fff;
            overflow-x: hidden;
        }

        .hero-text {
            font-family: 'Cinzel', serif;
            font-size: 90px;
            font-weight: 700;
            color: #ffffff;
            margin: 120px 0 0 50px;
            opacity: 1;
            transform: translateX(-120px);
            animation: slideIn 1.6s ease-out forwards;
        }

        .subtext {
            font-family: 'Montserrat', sans-serif;
            font-size: 22px;
            font-weight: 300;
            max-width: 700px;
            margin: 20px 0 0 55px;
            line-height: 1.6;
            opacity: 0;
            transform: translateX(-120px);
            animation: fadeText 5s ease-out forwards;
        }

        @keyframes slideIn {
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes fadeText {
            0% { opacity: 0; transform: translateX(-120px); }
            100% { opacity: 1; transform: translateX(0); }
        }

        .cards {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: flex-start;
            gap: 35px;
            margin-top: 100px;
            flex-wrap: nowrap;
        }

        .card {
            background: rgba(255, 255, 255, 0.15);
            padding: 30px;
            width: 330px;
            height: 300px;
            border-radius: 18px;
            backdrop-filter: blur(12px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
        }

        .card:hover {
            transform: translateY(-12px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.7);
        }

        .btn {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            padding: 15px 0;
            background-color: #28a745;
            color: white;
            text-decoration: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            transition: background 0.3s ease;
        }

        .btn:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>

    <div class="hero-text">Xmoney</div>
    <div class="subtext">We have dominated the market for nearly 5 years and have the potential to bring many clients through these 3 options. Options 2 and 3 are the key to your business success.</div>

    <div class="cards">
        <div class="card">
            <h2>2 Business Logos – $5</h2>
            <p>Get high-quality, professional logos for your brand.</p>
            <a class="btn" href="https://whop.com/checkout/plan_Bg7KX3vyIVGjk">BUY NOW</a>
        </div>
        <div class="card">
            <h2>10 Business Growth Ideas – $10</h2>
            <p>Boost your business with creative and actionable strategies.</p>
            <a class="btn" href="https://whop.com/checkout/plan_w3oZUMd5R30D1">BUY NOW</a>
        </div>
        <div class="card">
            <h2>1 Professional 30s Video – $10</h2>
            <p>Create a compelling video that attracts more clients.</p>
            <a class="btn" href="https://whop.com/checkout/plan_HglKg8iMbKz5I">BUY NOW</a>
        </div>
    </div>

</body>
</html>
