<!doctype html>
<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Handmade Flags Shop</title>
  <script src="/_sdk/element_sdk.js"></script>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Comic Sans MS', 'Chalkboard SE', cursive;
      background-color: #fff8e7;
      color: #2c3e50;
      overflow-x: hidden;
    }

    * {
      box-sizing: border-box;
    }

    header {
      background-color: #ff6b6b;
      padding: 20px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }

    .logo {
      font-size: 32px;
      font-weight: bold;
      color: #ffffff;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    nav {
      display: flex;
      gap: 25px;
    }

    nav a {
      color: #ffffff;
      text-decoration: none;
      font-size: 18px;
      font-weight: bold;
      transition: transform 0.2s;
    }

    nav a:hover {
      transform: scale(1.1);
    }

    .cart-icon {
      background-color: #ffd93d;
      color: #2c3e50;
      padding: 12px 24px;
      border-radius: 30px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }

    .cart-icon:hover {
      background-color: #ffe066;
      transform: translateY(-2px);
    }

    .checkout-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1000;
      overflow-y: auto;
      padding: 20px;
    }

    .checkout-modal.active {
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .checkout-content {
      background-color: #ffffff;
      border-radius: 20px;
      padding: 40px;
      max-width: 600px;
      width: 100%;
      max-height: 90%;
      overflow-y: auto;
      position: relative;
      box-shadow: 0 10px 40px rgba(0,0,0,0.3);
    }

    .close-checkout {
      position: absolute;
      top: 20px;
      right: 20px;
      background-color: #ff6b6b;
      color: white;
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      font-size: 24px;
      cursor: pointer;
      transition: all 0.3s;
    }

    .close-checkout:hover {
      background-color: #ff5252;
      transform: rotate(90deg);
    }

    .checkout-title {
      font-size: 32px;
      color: #ff6b6b;
      margin: 0 0 30px 0;
      text-align: center;
    }

    .cart-items {
      margin-bottom: 30px;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px;
      background-color: #fff8e7;
      border-radius: 10px;
      margin-bottom: 10px;
    }

    .cart-item-name {
      font-weight: bold;
      color: #2c3e50;
    }

    .cart-item-price {
      color: #ff6b6b;
      font-weight: bold;
    }

    .cart-total {
      font-size: 24px;
      font-weight: bold;
      color: #ff6b6b;
      text-align: right;
      padding: 20px 0;
      border-top: 3px solid #ff6b6b;
      margin-bottom: 30px;
    }

    .order-instructions {
      background-color: #fff8e7;
      padding: 25px;
      border-radius: 15px;
      margin-bottom: 20px;
      border: 3px solid #ffd93d;
    }

    .order-instructions h3 {
      margin: 0 0 15px 0;
      color: #ff6b6b;
      font-size: 22px;
    }

    .order-instructions p {
      margin: 10px 0;
      line-height: 1.6;
      color: #2c3e50;
    }

    .order-form-btn {
      background-color: #ff6b6b;
      color: white;
      padding: 18px 40px;
      border: none;
      border-radius: 15px;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      width: 100%;
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
      text-decoration: none;
      display: inline-block;
      text-align: center;
    }

    .order-form-btn:hover {
      background-color: #ff5252;
      transform: translateY(-2px);
      box-shadow: 0 8px 16px rgba(0,0,0,0.3);
    }

    .continue-shopping-btn {
      background-color: #ffd93d;
      color: #2c3e50;
      padding: 12px 30px;
      border: none;
      border-radius: 15px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      width: 100%;
      margin-top: 15px;
    }

    .continue-shopping-btn:hover {
      background-color: #ffe066;
      transform: translateY(-2px);
    }

    .hero {
      position: relative;
      height: 70%;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 40px;
      overflow: hidden;
    }

    .hero::before {
      content: '🖍️✏️📄🎨';
      position: absolute;
      font-size: 100px;
      opacity: 0.1;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      letter-spacing: 40px;
    }

    .hero-content {
      max-width: 800px;
      position: relative;
      z-index: 1;
    }

    .hero h1 {
      font-size: 56px;
      margin: 0 0 20px 0;
      color: #ffffff;
      text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
      line-height: 1.2;
    }

    .hero p {
      font-size: 24px;
      margin: 0 0 30px 0;
      color: #ffffff;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    }

    .cta-button {
      background-color: #ffd93d;
      color: #2c3e50;
      padding: 16px 40px;
      font-size: 20px;
      font-weight: bold;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
    }

    .cta-button:hover {
      background-color: #ffe066;
      transform: translateY(-3px);
      box-shadow: 0 8px 16px rgba(0,0,0,0.3);
    }

    main {
      padding: 60px 40px;
      max-width: 1400px;
      margin: 0 auto;
    }

    .section-title {
      font-size: 42px;
      text-align: center;
      margin-bottom: 50px;
      color: #ff6b6b;
      position: relative;
      display: inline-block;
      width: 100%;
    }

    .section-title::after {
      content: '✨';
      margin-left: 15px;
    }

    .section-title::before {
      content: '✨';
      margin-right: 15px;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
      margin-bottom: 60px;
    }

    .product-card {
      background-color: #ffffff;
      border-radius: 20px;
      overflow: hidden;
      transition: transform 0.3s, box-shadow 0.3s;
      cursor: pointer;
      border: 4px solid #ff6b6b;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .product-card:hover {
      transform: translateY(-10px) rotate(1deg);
      box-shadow: 0 12px 24px rgba(255, 107, 107, 0.3);
    }

    .product-image {
      width: 100%;
      height: 200px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 100px;
      background: linear-gradient(135deg, #ffeaa7, #fdcb6e);
      position: relative;
    }

    .handmade-badge {
      position: absolute;
      top: 10px;
      right: 10px;
      background-color: #ff6b6b;
      color: white;
      padding: 5px 12px;
      border-radius: 15px;
      font-size: 12px;
      font-weight: bold;
      transform: rotate(10deg);
    }

    .product-info {
      padding: 25px;
    }

    .product-title {
      font-size: 22px;
      margin: 0 0 10px 0;
      color: #2c3e50;
      font-weight: bold;
    }

    .product-description {
      font-size: 14px;
      color: #7f8c8d;
      margin: 0 0 15px 0;
      line-height: 1.6;
    }

    .product-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .product-price {
      font-size: 28px;
      color: #ff6b6b;
      font-weight: bold;
    }

    .add-to-cart {
      background-color: #ffd93d;
      color: #2c3e50;
      padding: 12px 24px;
      border: none;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s;
      font-size: 14px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }

    .add-to-cart:hover {
      background-color: #ffe066;
      transform: scale(1.05);
    }

    .add-to-cart:active {
      transform: scale(0.95);
    }

    footer {
      background-color: #ff6b6b;
      padding: 40px;
      text-align: center;
      margin-top: 60px;
    }

    footer p {
      margin: 0;
      color: #ffffff;
      font-size: 16px;
    }

    @media (max-width: 768px) {
      .hero h1 {
        font-size: 36px;
      }

      .hero p {
        font-size: 18px;
      }

      header {
        flex-direction: column;
        gap: 20px;
      }

      nav {
        flex-direction: column;
        gap: 15px;
        text-align: center;
      }

      .products-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <header>
   <div class="logo" id="site-title">
    🏴 Handmade Flags Shop
   </div>
   <nav><a href="#" target="_blank" rel="noopener noreferrer">Home</a> <a href="#" target="_blank" rel="noopener noreferrer">Flags</a> <a href="#" target="_blank" rel="noopener noreferrer">Custom</a> <a href="#" target="_blank" rel="noopener noreferrer">About</a>
   </nav>
   <div class="cart-icon">
    🛒 Cart (0)
   </div>
  </header>
  <section class="hero">
   <div class="hero-content">
    <h1 id="hero-headline">Handcrafted Paper Flags!</h1>
    <p id="hero-subheadline">Made with love, paper, and crayons 🖍️</p><button class="cta-button" id="cta-button">Shop Now</button>
   </div>
  </section>
  <main>
   <h2 class="section-title" id="section-title">Our Affordable Flags</h2>
   <div class="products-grid">
    <article class="product-card">
     <div class="product-image">
      🇯🇵 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Japan Flag</h3>
      <p class="product-description">Super easy! Just one red circle on white paper. A minimalist masterpiece!</p>
      <div class="product-footer"><span class="product-price">₱15</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🏳️‍🌈 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Rainbow Pride Flag</h3>
      <p class="product-description">Just straight lines in rainbow colors! Easy and colorful.</p>
      <div class="product-footer"><span class="product-price">₱18</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🏴‍☠️ <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Pirate Flag</h3>
      <p class="product-description">Simple skull and crossbones! Perfect for pirate parties. Arrr!</p>
      <div class="product-footer"><span class="product-price">₱20</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇵🇭 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Philippine Flag</h3>
      <p class="product-description">Triangle, stars, and sun! Takes some time but worth it. Perfect for celebrations!</p>
      <div class="product-footer"><span class="product-price">₱35</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇰🇷 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">South Korea Flag</h3>
      <p class="product-description">Taegeuk symbol and four trigrams - tricky but beautiful!</p>
      <div class="product-footer"><span class="product-price">₱38</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇨🇦 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Canada Flag</h3>
      <p class="product-description">That maple leaf is HARD to draw! Took three tries to get it right.</p>
      <div class="product-footer"><span class="product-price">₱42</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇺🇸 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">USA Flag</h3>
      <p class="product-description">50 tiny stars AND 13 stripes! My hand hurts just thinking about it.</p>
      <div class="product-footer"><span class="product-price">₱55</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇬🇧 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">UK Flag</h3>
      <p class="product-description">Union Jack with overlapping crosses - super complicated! Worth every peso.</p>
      <div class="product-footer"><span class="product-price">₱58</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇧🇷 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Brazil Flag</h3>
      <p class="product-description">Diamond, circle, AND 27 tiny stars! This one takes forever!</p>
      <div class="product-footer"><span class="product-price">₱65</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇫🇷 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">France Flag</h3>
      <p class="product-description">Three vertical stripes - blue, white, red. Simple and elegant!</p>
      <div class="product-footer"><span class="product-price">₱18</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇩🇪 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Germany Flag</h3>
      <p class="product-description">Black, red, and gold horizontal stripes. Classic and bold!</p>
      <div class="product-footer"><span class="product-price">₱18</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇮🇹 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Italy Flag</h3>
      <p class="product-description">Green, white, and red stripes. Like the French flag but sideways!</p>
      <div class="product-footer"><span class="product-price">₱18</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇪🇸 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Spain Flag</h3>
      <p class="product-description">Red and yellow stripes with a coat of arms. The emblem is tricky!</p>
      <div class="product-footer"><span class="product-price">₱45</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇲🇽 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Mexico Flag</h3>
      <p class="product-description">Green, white, red with an eagle eating a snake! Super detailed!</p>
      <div class="product-footer"><span class="product-price">₱50</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇦🇺 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Australia Flag</h3>
      <p class="product-description">Union Jack plus Southern Cross stars. Lots of tiny stars to draw!</p>
      <div class="product-footer"><span class="product-price">₱48</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇨🇳 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">China Flag</h3>
      <p class="product-description">Red background with five yellow stars. The small stars are positioned just right!</p>
      <div class="product-footer"><span class="product-price">₱25</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇮🇳 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">India Flag</h3>
      <p class="product-description">Orange, white, green with the Ashoka Chakra wheel. That wheel has 24 spokes!</p>
      <div class="product-footer"><span class="product-price">₱52</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇸🇬 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Singapore Flag</h3>
      <p class="product-description">Red and white with crescent moon and five stars. Clean design!</p>
      <div class="product-footer"><span class="product-price">₱28</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇹🇭 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Thailand Flag</h3>
      <p class="product-description">Five horizontal stripes in red, white, and blue. Nice and straightforward!</p>
      <div class="product-footer"><span class="product-price">₱20</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇻🇳 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Vietnam Flag</h3>
      <p class="product-description">Red background with a big yellow star. Simple but striking!</p>
      <div class="product-footer"><span class="product-price">₱16</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇳🇿 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">New Zealand Flag</h3>
      <p class="product-description">Like Australia but with red stars instead! Still lots of detail work.</p>
      <div class="product-footer"><span class="product-price">₱48</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇸🇦 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">Saudi Arabia Flag</h3>
      <p class="product-description">Green with Arabic calligraphy and a sword. The writing is challenging!</p>
      <div class="product-footer"><span class="product-price">₱55</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card">
     <div class="product-image">
      🇿🇦 <span class="handmade-badge">Handmade!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title">South Africa Flag</h3>
      <p class="product-description">Six colors in a Y-shape! One of the most colorful and complex designs!</p>
      <div class="product-footer"><span class="product-price">₱60</span> <button class="add-to-cart">Add to Cart</button>
      </div>
     </div>
    </article>
    <article class="product-card" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-color: #ffd93d;">
     <div class="product-image" style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);">
      🎨✨ <span class="handmade-badge" style="background-color: #ffd93d; color: #2c3e50;">Custom!</span>
     </div>
     <div class="product-info">
      <h3 class="product-title" style="color: #ffffff;">Custom Flag Design</h3>
      <p class="product-description" style="color: #f0f0f0;">Want a flag that's not listed? I can draw ANY flag you want! Just tell me which one in the order form.</p>
      <div class="product-footer"><span class="product-price" style="color: #ffd93d;">₱20+</span> <button class="add-to-cart custom-flag-btn">Request Custom</button>
      </div>
     </div>
    </article>
   </div>
  </main>
  <footer>
   <p>🎨 Made with paper, crayons, and lots of love! 🖍️ © 2024 Handmade Flags Shop</p>
  </footer>
  <div class="checkout-modal" id="checkoutModal">
   <div class="checkout-content"><button class="close-checkout" id="closeCheckout">×</button>
    <h2 class="checkout-title">🛒 Your Order</h2>
    <div class="cart-items" id="cartItemsList"></div>
    <div class="cart-total" id="cartTotal">
     Total: ₱0
    </div>
    <div class="order-instructions">
     <h3>📝 Complete Your Order</h3>
     <p>To place your order, please click the button below to fill out our order form. Make sure to include all the items listed above!</p>
     <p><strong>Your order total is shown above.</strong></p>
     <p style="margin-top: 15px; font-style: italic;">💡 If you requested a custom flag, please specify which flag you'd like in the order form!</p>
    </div><a href="https://forms.gle/qxx5eapz2jwRzSGi6" target="_blank" rel="noopener noreferrer" class="order-form-btn"> Fill Out Order Form 📋 </a> <button class="continue-shopping-btn" id="continueShopping">Continue Shopping</button>
   </div>
  </div>
  <script>
    const defaultConfig = {
      background_color: '#fff8e7',
      surface_color: '#ffffff',
      text_color: '#2c3e50',
      primary_action_color: '#ff6b6b',
      secondary_action_color: '#ffd93d',
      site_title: '🏴 Handmade Flags Shop',
      hero_headline: 'Handcrafted Paper Flags!',
      hero_subheadline: 'Made with love, paper, and crayons 🖍️',
      cta_button: 'Shop Now',
      section_title: 'Our Affordable Flags',
      font_family: 'Comic Sans MS',
      font_size: 16
    };

    async function onConfigChange(config) {
      const backgroundColor = config.background_color || defaultConfig.background_color;
      const surfaceColor = config.surface_color || defaultConfig.surface_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const primaryActionColor = config.primary_action_color || defaultConfig.primary_action_color;
      const secondaryActionColor = config.secondary_action_color || defaultConfig.secondary_action_color;
      const customFont = config.font_family || defaultConfig.font_family;
      const baseSize = config.font_size || defaultConfig.font_size;
      const baseFontStack = 'cursive';

      document.body.style.backgroundColor = backgroundColor;
      document.body.style.color = textColor;
      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      document.body.style.fontSize = `${baseSize}px`;

      const header = document.querySelector('header');
      header.style.backgroundColor = primaryActionColor;

      const logo = document.querySelector('.logo');
      logo.style.color = surfaceColor;
      logo.style.fontFamily = `${customFont}, ${baseFontStack}`;
      logo.style.fontSize = `${baseSize * 2}px`;

      const navLinks = document.querySelectorAll('nav a');
      navLinks.forEach(link => {
        link.style.color = surfaceColor;
        link.style.fontFamily = `${customFont}, ${baseFontStack}`;
        link.style.fontSize = `${baseSize * 1.125}px`;
      });

      const cartIcon = document.querySelector('.cart-icon');
      cartIcon.style.backgroundColor = secondaryActionColor;
      cartIcon.style.color = textColor;
      cartIcon.style.fontFamily = `${customFont}, ${baseFontStack}`;
      cartIcon.style.fontSize = `${baseSize}px`;

      const heroH1 = document.querySelector('.hero h1');
      heroH1.style.color = surfaceColor;
      heroH1.style.fontFamily = `${customFont}, ${baseFontStack}`;
      heroH1.style.fontSize = `${baseSize * 3.5}px`;

      const heroP = document.querySelector('.hero p');
      heroP.style.color = surfaceColor;
      heroP.style.fontFamily = `${customFont}, ${baseFontStack}`;
      heroP.style.fontSize = `${baseSize * 1.5}px`;

      const ctaButton = document.querySelector('.cta-button');
      ctaButton.style.backgroundColor = secondaryActionColor;
      ctaButton.style.color = textColor;
      ctaButton.style.fontFamily = `${customFont}, ${baseFontStack}`;
      ctaButton.style.fontSize = `${baseSize * 1.25}px`;

      const sectionTitleEl = document.querySelector('.section-title');
      sectionTitleEl.style.color = primaryActionColor;
      sectionTitleEl.style.fontFamily = `${customFont}, ${baseFontStack}`;
      sectionTitleEl.style.fontSize = `${baseSize * 2.625}px`;

      const productCards = document.querySelectorAll('.product-card');
      productCards.forEach(card => {
        card.style.backgroundColor = surfaceColor;
        card.style.borderColor = primaryActionColor;
      });

      const handmadeBadges = document.querySelectorAll('.handmade-badge');
      handmadeBadges.forEach(badge => {
        badge.style.backgroundColor = primaryActionColor;
        badge.style.color = surfaceColor;
        badge.style.fontFamily = `${customFont}, ${baseFontStack}`;
        badge.style.fontSize = `${baseSize * 0.75}px`;
      });

      const productTitles = document.querySelectorAll('.product-title');
      productTitles.forEach(title => {
        title.style.color = textColor;
        title.style.fontFamily = `${customFont}, ${baseFontStack}`;
        title.style.fontSize = `${baseSize * 1.375}px`;
      });

      const productDescriptions = document.querySelectorAll('.product-description');
      productDescriptions.forEach(desc => {
        desc.style.fontFamily = `${customFont}, ${baseFontStack}`;
        desc.style.fontSize = `${baseSize * 0.875}px`;
      });

      const productPrices = document.querySelectorAll('.product-price');
      productPrices.forEach(price => {
        price.style.color = primaryActionColor;
        price.style.fontFamily = `${customFont}, ${baseFontStack}`;
        price.style.fontSize = `${baseSize * 1.75}px`;
      });

      const addToCartButtons = document.querySelectorAll('.add-to-cart');
      addToCartButtons.forEach(btn => {
        btn.style.backgroundColor = secondaryActionColor;
        btn.style.color = textColor;
        btn.style.fontFamily = `${customFont}, ${baseFontStack}`;
        btn.style.fontSize = `${baseSize * 0.875}px`;
      });

      const footer = document.querySelector('footer');
      footer.style.backgroundColor = primaryActionColor;

      const footerP = document.querySelector('footer p');
      footerP.style.color = surfaceColor;
      footerP.style.fontFamily = `${customFont}, ${baseFontStack}`;
      footerP.style.fontSize = `${baseSize}px`;

      document.getElementById('site-title').innerHTML = config.site_title || defaultConfig.site_title;
      document.getElementById('hero-headline').textContent = config.hero_headline || defaultConfig.hero_headline;
      document.getElementById('hero-subheadline').textContent = config.hero_subheadline || defaultConfig.hero_subheadline;
      document.getElementById('cta-button').textContent = config.cta_button || defaultConfig.cta_button;
      document.getElementById('section-title').textContent = config.section_title || defaultConfig.section_title;
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [
          {
            get: () => config.background_color || defaultConfig.background_color,
            set: (value) => {
              config.background_color = value;
              window.elementSdk.setConfig({ background_color: value });
            }
          },
          {
            get: () => config.surface_color || defaultConfig.surface_color,
            set: (value) => {
              config.surface_color = value;
              window.elementSdk.setConfig({ surface_color: value });
            }
          },
          {
            get: () => config.text_color || defaultConfig.text_color,
            set: (value) => {
              config.text_color = value;
              window.elementSdk.setConfig({ text_color: value });
            }
          },
          {
            get: () => config.primary_action_color || defaultConfig.primary_action_color,
            set: (value) => {
              config.primary_action_color = value;
              window.elementSdk.setConfig({ primary_action_color: value });
            }
          },
          {
            get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
            set: (value) => {
              config.secondary_action_color = value;
              window.elementSdk.setConfig({ secondary_action_color: value });
            }
          }
        ],
        borderables: [],
        fontEditable: {
          get: () => config.font_family || defaultConfig.font_family,
          set: (value) => {
            config.font_family = value;
            window.elementSdk.setConfig({ font_family: value });
          }
        },
        fontSizeable: {
          get: () => config.font_size || defaultConfig.font_size,
          set: (value) => {
            config.font_size = value;
            window.elementSdk.setConfig({ font_size: value });
          }
        }
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['site_title', config.site_title || defaultConfig.site_title],
        ['hero_headline', config.hero_headline || defaultConfig.hero_headline],
        ['hero_subheadline', config.hero_subheadline || defaultConfig.hero_subheadline],
        ['cta_button', config.cta_button || defaultConfig.cta_button],
        ['section_title', config.section_title || defaultConfig.section_title]
      ]);
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    let cart = [];
    const addToCartButtons = document.querySelectorAll('.add-to-cart');
    const cartIcon = document.querySelector('.cart-icon');
    const checkoutModal = document.getElementById('checkoutModal');
    const closeCheckout = document.getElementById('closeCheckout');
    const continueShopping = document.getElementById('continueShopping');

    const products = [
      { name: 'Japan Flag', price: 15, emoji: '🇯🇵' },
      { name: 'Rainbow Pride Flag', price: 18, emoji: '🏳️‍🌈' },
      { name: 'Pirate Flag', price: 20, emoji: '🏴‍☠️' },
      { name: 'Philippine Flag', price: 35, emoji: '🇵🇭' },
      { name: 'South Korea Flag', price: 38, emoji: '🇰🇷' },
      { name: 'Canada Flag', price: 42, emoji: '🇨🇦' },
      { name: 'USA Flag', price: 55, emoji: '🇺🇸' },
      { name: 'UK Flag', price: 58, emoji: '🇬🇧' },
      { name: 'Brazil Flag', price: 65, emoji: '🇧🇷' },
      { name: 'France Flag', price: 18, emoji: '🇫🇷' },
      { name: 'Germany Flag', price: 18, emoji: '🇩🇪' },
      { name: 'Italy Flag', price: 18, emoji: '🇮🇹' },
      { name: 'Spain Flag', price: 45, emoji: '🇪🇸' },
      { name: 'Mexico Flag', price: 50, emoji: '🇲🇽' },
      { name: 'Australia Flag', price: 48, emoji: '🇦🇺' },
      { name: 'China Flag', price: 25, emoji: '🇨🇳' },
      { name: 'India Flag', price: 52, emoji: '🇮🇳' },
      { name: 'Singapore Flag', price: 28, emoji: '🇸🇬' },
      { name: 'Thailand Flag', price: 20, emoji: '🇹🇭' },
      { name: 'Vietnam Flag', price: 16, emoji: '🇻🇳' },
      { name: 'New Zealand Flag', price: 48, emoji: '🇳🇿' },
      { name: 'Saudi Arabia Flag', price: 55, emoji: '🇸🇦' },
      { name: 'South Africa Flag', price: 60, emoji: '🇿🇦' },
      { name: 'Custom Flag (specify in form)', price: 0, emoji: '🎨' }
    ];

    addToCartButtons.forEach((button, index) => {
      button.addEventListener('click', (e) => {
        e.stopPropagation();
        cart.push(products[index]);
        updateCartIcon();
        button.textContent = '✓ Added!';
        setTimeout(() => {
          button.textContent = 'Add to Cart';
        }, 1500);
      });
    });

    function updateCartIcon() {
      cartIcon.textContent = `🛒 Cart (${cart.length})`;
    }

    cartIcon.addEventListener('click', () => {
      if (cart.length === 0) {
        return;
      }
      openCheckout();
    });

    function openCheckout() {
      renderCartItems();
      checkoutModal.classList.add('active');
      document.body.style.overflow = 'hidden';
    }

    function closeCheckoutModal() {
      checkoutModal.classList.remove('active');
      document.body.style.overflow = 'auto';
    }

    closeCheckout.addEventListener('click', closeCheckoutModal);
    continueShopping.addEventListener('click', closeCheckoutModal);

    checkoutModal.addEventListener('click', (e) => {
      if (e.target === checkoutModal) {
        closeCheckoutModal();
      }
    });

    function renderCartItems() {
      const cartItemsList = document.getElementById('cartItemsList');
      const cartTotal = document.getElementById('cartTotal');
      
      cartItemsList.innerHTML = '';
      let total = 0;

      cart.forEach(item => {
        total += item.price;
        const cartItem = document.createElement('div');
        cartItem.className = 'cart-item';
        const priceDisplay = item.price === 0 ? 'TBD' : `₱${item.price}`;
        cartItem.innerHTML = `
          <span class="cart-item-name">${item.emoji} ${item.name}</span>
          <span class="cart-item-price">${priceDisplay}</span>
        `;
        cartItemsList.appendChild(cartItem);
      });

      const totalDisplay = cart.some(item => item.price === 0) ? `₱${total}+ (custom pricing TBD)` : `₱${total}`;
      cartTotal.textContent = `Total: ${totalDisplay}`;
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99b892de401d9c62',t:'MTc2MjY0MTY0My4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
