<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Kirana Store</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f5f7f5;
      color: #333;
    }

    header {
      background: #198754;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin-bottom: 10px;
    }

    .search {
      width: 90%;
      max-width: 500px;
      padding: 12px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
    }

    .categories {
      display: flex;
      justify-content: center;
      gap: 10px;
      padding: 15px;
      flex-wrap: wrap;
    }

    .categories button {
      padding: 10px 18px;
      border: none;
      background: #ffc107;
      border-radius: 20px;
      cursor: pointer;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 20px;
      padding: 20px;
      max-width: 1100px;
      margin: auto;
    }

    .product {
      background: white;
      padding: 20px;
      border-radius: 12px;
      text-align: center;
      box-shadow: 0 3px 10px rgba(0,0,0,0.1);
    }

    .product .emoji {
      font-size: 50px;
      margin-bottom: 10px;
    }

    .product h3 {
      margin-bottom: 8px;
    }

    .price {
      color: #198754;
      font-weight: bold;
      margin: 10px;
    }

    .product button {
      background: #198754;
      color: white;
      border: none;
      padding: 10px 15px;
      border-radius: 6px;
      cursor: pointer;
    }

    .product button:hover {
      background: #146c43;
    }

    .cart {
      background: white;
      margin: 20px auto;
      padding: 20px;
      max-width: 600px;
      border-radius: 12px;
      box-shadow: 0 3px 10px rgba(0,0,0,0.1);
    }

    .cart h2 {
      color: #198754;
      margin-bottom: 10px;
    }

    #cartItems {
      margin: 10px 0;
      line-height: 1.8;
    }

    .order-btn {
      background: #25D366;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 7px;
      cursor: pointer;
      font-size: 16px;
    }

    footer {
      background: #198754;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 30px;
    }
  </style>
</head>

<body>

  <header>
    <h1>🛒 My Kirana Store</h1>
    <p>Fresh groceries at your doorstep</p>
    <br>
    <input
      type="text"
      id="search"
      class="search"
      placeholder="Search products..."
      onkeyup="searchProducts()"
    >
  </header>

  <div class="categories">
    <button onclick="filterProducts('all')">All</button>
    <button onclick="filterProducts('grocery')">Grocery</button>
    <button onclick="filterProducts('snacks')">Snacks</button>
    <button onclick="filterProducts('beverages')">Beverages</button>
    <button onclick="filterProducts('personal')">Personal Care</button>
  </div>

  <section class="products" id="products">

    <div class="product" data-category="grocery">
      <div class="emoji">🌾</div>
      <h3>Rice</h3>
      <p>1 Kg</p>
      <div class="price">₹60</div>
      <button onclick="addToCart('Rice', 60)">Add to Cart</button>
    </div>

    <div class="product" data-category="grocery">
      <div class="emoji">🌾</div>
      <h3>Wheat Flour</h3>
      <p>1 Kg</p>
      <div class="price">₹50</div>
      <button onclick="addToCart('Wheat Flour', 50)">Add to Cart</button>
    </div>

    <div class="product" data-category="grocery">
      <div class="emoji">🫘</div>
      <h3>Toor Dal</h3>
      <p>1 Kg</p>
      <div class="price">₹140</div>
      <button onclick="addToCart('Toor Dal', 140)">Add to Cart</button>
    </div>

    <div class="product" data-category="snacks">
      <div class="emoji">🍪</div>
      <h3>Biscuits</h3>
      <p>1 Pack</p>
      <div class="price">₹20</div>
      <button onclick="addToCart('Biscuits', 20)">Add to Cart</button>
    </div>

    <div class="product" data-category="snacks">
      <div class="emoji">🍟</div>
      <h3>Chips</h3>
      <p>1 Pack</p>
      <div class="price">₹30</div>
      <button onclick="addToCart('Chips', 30)">Add to Cart</button>
    </div>

    <div class="product" data-category="beverages">
      <div class="emoji">🥤</div>
      <h3>Cold Drink</h3>
      <p>750 ml</p>
      <div class="price">₹40</div>
      <button onclick="addToCart('Cold Drink', 40)">Add to Cart</button>
    </div>

    <div class="product" data-category="beverages">
      <div class="emoji">☕</div>
      <h3>Tea</h3>
      <p>250 g</p>
      <div class="price">₹120</div>
      <button onclick="addToCart('Tea', 120)">Add to Cart</button>
    </div>

    <div class="product" data-category="personal">
      <div class="emoji">🧴</div>
      <h3>Shampoo</h3>
      <p>180 ml</p>
      <div class="price">₹150</div>
      <button onclick="addToCart('Shampoo', 150)">Add to Cart</button>
    </div>

  </section>

  <section class="cart">
    <h2>🛍️ Your Cart</h2>

    <div id="cartItems">
      Cart is empty.
    </div>

    <h3>Total: ₹<span id="total">0</span></h3>

    <br>

    <button class="order-btn" onclick="placeOrder()">
      Order on WhatsApp
    </button>
  </section>

  <footer>
    <p>© 2026 My Kirana Store | All Rights Reserved</p>
  </footer>

  <script>
    let cart = [];
    let total = 0;

    function addToCart(name, price) {
      cart.push({
        name: name,
        price: price
      });

      total += price;
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById("cartItems");

      if (cart.length === 0) {
        cartItems.innerHTML = "Cart is empty.";
      } else {
        cartItems.innerHTML = cart.map((item, index) => `
          <div>
            ${item.name} - ₹${item.price}
            <button onclick="removeItem(${index})"
              style="margin-left:10px;background:red;color:white;border:0;padding:4px 8px;border-radius:4px;">
              Remove
            </button>
          </div>
        `).join("");
      }

      document.getElementById("total").innerText = total;
    }

    function removeItem(index) {
      total -= cart[index].price;
      cart.splice(index, 1);
      updateCart();
    }

    function searchProducts() {
      const search = document
        .getElementById("search")
        .value
        .toLowerCase();

      const products = document.querySelectorAll(".product");

      products.forEach(product => {
        const name = product
          .querySelector("h3")
          .innerText
          .toLowerCase();

        product.style.display =
          name.includes(search) ? "block" : "none";
      });
    }

    function filterProducts(category) {
      const products = document.querySelectorAll(".product");

      products.forEach(product => {
        if (
          category === "all" ||
          product.dataset.category === category
        ) {
          product.style.display = "block";
        } else {
          product.style.display = "none";
        }
      });
    }

    function placeOrder() {
      if (cart.length === 0) {
        alert("Please add products to your cart.");
        return;
      }

      let message = "Hello, I want to order:%0A%0A";

      cart.forEach(item => {
        message += item.name + " - ₹" + item.price + "%0A";
      });

      message += "%0ATotal: ₹" + total;

      // Replace 919876543210 with your WhatsApp number
      const phone = "919876543210";

      window.open(
        "https://wa.me/" + phone + "?text=" + message,
        "_blank"
      );
    }
  </script>

</body>
</html>

