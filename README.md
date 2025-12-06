<html lang="sq">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Galaxy Background - Gradient</title>
<style>
  :root {
    --bg-1: #0b0033; /* navy deep */
    --bg-2: #1b2b7a; /* electric blue */
    --bg-3: #7a007a; /* deep purple */
    --accent: #ff3e9d; /* neon pink */
        }  html,body {
    height:100%;
    margin:0;
  }

  .bg-gradient {
    min-height:100vh;
    background: radial-gradient(1200px 600px at 10% 20%, rgba(123,0,150,0.35), transparent 10%),
                radial-gradient(1000px 500px at 90% 80%, rgba(0,200,255,0.14), transparent 10%),
                linear-gradient(135deg, var(--bg-1) 0%, var(--bg-2) 45%, var(--bg-3) 100%);

        .overlay {
            background-color: rgba(0, 0, 0, 0.6);
            width: 100%;
            min-height: 100vh;
            padding: 60px 20px;
        }

        h1 {
            font-size: 50px;
            margin-bottom: 50px;
            font-weight: 700;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.7);
        }

        .cards {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 35px;
        }

        .card {
            background: rgba(255, 255, 255, 0.15);
            padding: 30px;
            width: 330px;
            border-radius: 18px;
            backdrop-filter: blur(12px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-12px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.7);
        }

        .card h2 {
            font-size: 26px;
            margin-bottom: 15px;
            color: #fff;
        }

        .card p {
            font-size: 16px;
            margin-bottom: 25px;
            color: #f0f0f0;
        }

        .btn {
            display: inline-block;
            padding: 15px 26px;
            background-color: #1B3FFF;
            color: white;
            text-decoration: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            transition: background 0.3s ease;
        }

        .btn:hover {
            background-color: #e64a19;
        }

        .section-text {
            margin-top: 50px;
            font-size: 22px;
            font-weight: 500;
            text-shadow: 1px 1px 5px rgba(0,0,0,0.6);
        }

        .premium-card {
            margin: 45px auto;
            width: 350px;
            background: rgba(255, 255, 255, 0.18);
            backdrop-filter: blur(14px);
            padding: 28px;
            border-radius: 20px;
            box-shadow: 0 12px 35px rgba(0,0,0,0.7);
            transition: transform 0.3s ease;
        }

        .premium-card:hover {
            transform: translateY(-10px);
        }

        .premium-card h3 {
            margin-bottom: 15px;
            font-size: 26px;
        }

        .premium-card p {
            margin-bottom: 22px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="overlay">

        <h1>Xmoney – The Key to Your Business Success</h1>

        <div class="cards">
            <!-- Card 1 -->
            <div class="card">
                <h2>2 Business Logos – $5</h2>
                <p>Get high-quality, professional logos for your brand.</p>
                <a class="btn" href="https://whop.com/checkout/plan_Bg7KX3vyIVGjk">BUY NOW</a>
            </div>

            <!-- Card 2 -->
            <div class="card">
                <h2>10 Business Growth Ideas – $10</h2>
                <p>Boost your business with creative and actionable strategies.</p>
                <a class="btn" href="https://whop.com/checkout/plan_w3oZUMd5R30D1">BUY NOW</a>
            </div>

            <!-- Card 3 -->
            <div class="card">
                <h2>1 Professional 30s Video – $10</h2>
                <p>Create a compelling video that attracts more clients.</p>
                <a class="btn" href="https://whop.com/checkout/plan_HglKg8iMbKz5I">BUY NOW</a>
            </div>
        </div>

        
        <div class="premium-card">
            <h3>Join the Premium Xmoney Membership</h3>
            <p>Price: $19.99</p>
            <a class="btn" href="https://whop.com/checkout/plan_HbwK4HOO0PteK">PAY NOW</a>
        </div>

       
