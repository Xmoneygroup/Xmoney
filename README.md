<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Xmoney | Online Store</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      color: #ffffff;
      min-height: 100vh;
    }

    header {
      min-height: 90vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      animation: fadeIn 2s ease-in-out;
      padding: 40px 20px;
    }

    header h1 {
      font-size: 4rem;
      letter-spacing: 3px;
      margin-bottom: 10px;
      animation: slideDown 1.5s ease-out;
    }

    .info {
      max-width: 650px;
      margin-top: 10px;
      animation: fadeInUp 2s ease-in-out;
    }

    .info ul {
      list-style: none;
    }

    .info li {
      margin: 12px 0;
      font-size: 1.1rem;
      opacity: 0.9;
    }

    section {
      padding: 60px 8%;
      background: #f4f4f4;
      color: #222;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 40px;
    }

    .product {
      background: transparent;
      padding: 10px;
      text-align: center;
    }

    .product:hover {
      transform: translateY(-8px);
      box-shadow: 0 20px 40px rgba(0,0,0,0.25);
    }

    .images {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
      margin-bottom: 10px;
    }

    .images img {
      width: 100%;
      border-radius: 12px;
      display: none;
    }

    .images img.active {
      display: block;
    }

    .product h3 {
      font-size: 1.1rem;
      margin: 15px 0;
    }

    .price {
      font-size: 1.5rem;
      font-weight: bold;
      margin: 10px 0 20px;
    }

    .btn {
      display: inline-block;
      padding: 12px 30px;
      background: linear-gradient(135deg, #ff512f, #f09819);
      color: #fff;
      border-radius: 30px;
      text-decoration: none;
      font-weight: bold;
      transition: opacity 0.3s ease, transform 0.3s ease;
    }

    .btn:hover {
      opacity: 0.9;
      transform: scale(1.05);
    }

    footer {
      background: #111;
      color: #aaa;
      text-align: center;
      padding: 20px;
      font-size: 0.9rem;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes slideDown {
      from { transform: translateY(-40px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    @keyframes fadeInUp {
      from { transform: translateY(30px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
  </style>
</head>
<body>

  <header>
    <h1>X MONEY</h1>
    <div class="info">
      <ul>
        <li>• We deliver orders only within Europe.</li>
        <li>• Delivery from warehouse to customer takes 7–15 days.</li>
        <li>• We are 100% transparent. Products arrive exactly as ordered. Orders cannot be returned.</li>
      </ul>
    </div>
  </header>

  <section>
    <div class="products">

      <!-- PRODUCT 1 -->
      <div class="product">
        <div class="images">
          <img class="active" src="https://images.unsplash.com/photo-1508614999368-9260051292e5?w=800" alt="Drone">
          <img src="https://images.unsplash.com/photo-1520975916090-3105956dac38?w=800" alt="Drone">
          <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?w=800" alt="Drone">

          <button class="nav-btn prev" onclick="changeImage(this,-1)">‹</button>
          <button class="nav-btn next" onclick="changeImage(this,1)">›</button>
        </div>

        <h3>Professional Drone E88 4K Wide-Angle HD 1080P Camera WiFi FPV Height Hold Foldable RC Drone Quadrotor Helicopter Children's Toys</h3>
        <div class="price">$35</div>
        <a href="#" class="btn">BUY NOW</a>
      </div>

      <!-- PRODUCT 2 -->
      <div class="product">
        <div class="images">
          <img class="active" src="https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=800" alt="Vacuum">
          <img src="https://images.unsplash.com/photo-1600566753086-00f18fb6b3ea?w=800" alt="Vacuum">
          <img src="https://images.unsplash.com/photo-1616628182506-1a7f6f2cbb12?w=800" alt="Vacuum">

          <button class="nav-btn prev" onclick="changeImage(this,-1)">‹</button>
          <button class="nav-btn next" onclick="changeImage(this,1)">›</button>
        </div>

        <h3>Car Vacuum Cleaner High Power Portable Handheld Wireless Brushless Motor Cleaning Machine Powerful Air Duster for Home Appliance</h3>
        <div class="price">$55</div>
        <a href="#" class="btn">BUY NOW</a>
      </div>

    </div>
  </section>

  <footer>
    © 2025 Xmoney. All rights reserved.
  </footer>

<script>
  function changeImage(button, direction) {
    const container = button.parentElement;
    const images = container.querySelectorAll('img');
    let index = Array.from(images).findIndex(img => img.classList.contains('active'));
    images[index].classList.remove('active');
    index = (index + direction + images.length) % images.length;
    images[index].classList.add('active');
  }
</script>

</body>
</html>
