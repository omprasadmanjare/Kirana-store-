<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Om Kirana Store</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f5f5f5;
      color: #222;
    }

    header {
      background: #0b7a3b;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin-bottom: 12px;
    }

    .search {
      width: 90%;
      max-width: 500px;
      padding: 12px;
      border: none;
      border-radius: 6px;
      font-size: 16px;
    }

    nav {
      background: white;
      padding: 15px;
      text-align: center;
      box-shadow: 0 2px 5px #ccc;
    }

    nav a {
      text-decoration: none;
      color: #0b7a3b;
      font-weight: bold;
      margin: 0 12px;
    }

    .hero {
      padding: 40px 20px;
      text-align: center;
      background: #e8f8ee;
    }

    .hero h2 {
      color: #0b7a3b;
      margin-bottom: 10px;
    }

    .products {
      padding: 30px 20px;
      max-width: 1100px;
      margin: auto;
    }

    .products h2 {
      text-align: center;
      margin-bottom: 25px;
    }

    .product-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
    }

    .product {
      background: white;
      padding: 20px;
      text-align: center;
      border-radius: 10px;
      box-shadow: 0 2px 8px #ddd;
    }

    .product .emoji {
      font-size: 60px;
      margin-bottom: 10px;
    }

    .product h3 {
      margin: 10px 0;
    }

    .price {
      color: #0b7a3b;
      font-size: 20px;
      font-weight: bold;
      margin: 10px;
    }

    button {
      background: #ff9800;
      color: white;
      border: none;
      padding: 10px 18px;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    button:hover {
      background: #e68900;
    }

    footer {
      margin-top: 30px;
      background: #0b7a3b;
      color: white;
      text-align: center;
      padding: 20px;
    }
  </style>
</head>

<body>

  <header>
    <h1>🛒 Om Kirana Store</h1>
    <input
      type="text"
      class="search"
      placeholder="Search for products..."
      onkeyup="searchProducts()"
      id="searchBox"
    >
  </header>

  <nav>
    <a href="#">Home</a>
    <a href="#products">Products</a>
    <a href="#contact">Contact</a>
    <a href="#">🛒 Cart</a>
  </nav>

  <section class="hero">
    <h2>Welcome to Om Kirana Store</h2>
    <
    
