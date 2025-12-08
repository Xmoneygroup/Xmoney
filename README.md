<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XMONEY — Premium Services</title>

<style>
  body, html {
    margin: 0;
    padding: 0;
    background: #000;
    font-family: 'Poppins', sans-serif;
    color: white;
    height: 100%;
    overflow-x: hidden;
  }

  /* Background with green particles */
  .bg {
    width: 100%;
    height: 100vh;
    position: fixed;
    z-index: 0;
    top: 0;
    left: 0;
    pointer-events: none;
    background: 
      radial-gradient(circle at 50% 50%, rgba(0,255,0,0.2), transparent 40%),
      url("https://i.imgur.com/G0j3x25.png");
    opacity: 0.45;
    animation: pulse 6s infinite alternate;
  }

  @keyframes pulse {
    from { opacity: 0.35; }
    to { opacity: 0.55; }
  }

  header {
    text-align: center;
    padding-top: 70px;
    z-index: 10;
    position: relative;
  }

  header h1 {
    font-size: 70px;
    letter-spacing: 8px;
    font-weight: 900;
    color: #00ff95;
    text-shadow: 0 0 20px #00ff95;
  }

  /* CARD SECTION */
  .cards-wrapper {
    max-width: 1200px;
    margin: 120px auto;
    padding: 20px;
    position: relative;
    z-index: 10;
  }

  .cards {
    display: flex;
    gap: 30px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .card {
    width: 330px;
    padding: 25px;
    border-radius: 18px;
    background: rgba(0, 0, 0, 0.45);
    border: 1px solid rgba(0,255,120,0.25);
    backdrop-filter: blur(12px);
    box-shadow: 0 0 25px rgba(0,255,130,0.25);
    transition: 0.3s;
  }

  .card:hover {
    transform: translateY(-10px) scale(1.03);
    box-shadow: 0 0 35px rgba(0,255,140,0.55);
  }

  .card h3 {
    font-size: 22px;
    color: #00ff95;
    text-shadow: 0 0 10px #00ff95;
  }

  .price {
    margin-top: 8px;
    font-size: 20px;
    font-weight: 700;
  }

  .buy-btn {
    display: inline-block;
    margin-top: 18px;
    padding: 12px 20px;
    background: #00ff95;
    color: black;
    font-weight: 700;
    text-decoration: none;
    border-radius: 10px;
    transition: 0.25s;
  }

  .buy-btn:hover {
    background: white;
    transform: translateY(-4px);
  }
</style>
</head>

<body>

<div class="bg"></div>

<header>
  <h1>XMONEY</h1>
</header>

<section class="cards-wrapper">
  <div class="cards">

    <!-- CARD 1 -->
    <div class="card">
      <h3>2 Professional Business Logos</h3>
      <p>Get two unique, modern, high-quality business logo designs tailored to your brand.</p>
      <div class="price">$5</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-1c/" target="_blank">BUY NOW</a>
    </div>

    <!-- CARD 2 -->
    <div class="card">
      <h3>10 Business Ideas Pack</h3>
      <p>Receive ten powerful, profitable business ideas ready to launch immediately.</p>
      <div class="price">$10</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-7e/" target="_blank">BUY NOW</a>
    </div>

    <!-- CARD 3 -->
    <div class="card">
      <h3>1 Premium Video Edit</h3>
      <p>A high-quality video edit designed to attract clients and boost your brand presence.</p>
      <div class="price">$10</div>
      <a class="buy-btn" href="https://whop.com/xmoney-1/xmoney-b1/" target="_blank">BUY NOW</a>
    </div>

  </div>
</section>

</body>
</html>
