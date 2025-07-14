# Mini-Shopping-Cart


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Shopping Cart Mini Project</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      padding: 20px;
      text-align: center;
    }

    h1 {
      color: #333;
    }

    .container {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      margin-top: 30px;
    }

    .product, .cart {
      background: white;
      padding: 15px;
      margin: 10px;
      width: 300px;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }

    .product img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 10px;
    }

    .product h3, .product p {
      margin: 10px 0;
    }

    button {
      padding: 10px;
      border: none;
      background-color: #28a745;
      color: white;
      font-size: 16px;
      border-radius: 5px;
      cursor: pointer;
    }

    button.remove {
      background-color: #dc3545;
    }

    ul {
      list-style: none;
      padding: 0;
      text-align: left;
    }

    li {
      margin-bottom: 10px;
      font-size: 16px;
    }

    .total {
      font-size: 20px;
      font-weight: bold;
      margin-top: 15px;
      color: #000;
    }
  </style>
</head>
<body>

  <h1>🛍️ Mini Shopping Cart</h1>

  <div class="container">
    <!-- Products Section -->
    <div class="product">
      <img src="https://via.placeholder.com/300x200?text=Shoes" alt="Product 1">
      <h3>Running Shoes</h3>
      <p>₹1999</p>
      <button onclick="addToCart('Running Shoes', 1999)">Add to Cart</button>
    </div>

    <div class="product">
      <img src="https://via.placeholder.com/300x200?text=Watch" alt="Product 2">
      <h3>Smart Watch</h3>
      <p>₹2999</p>
      <button onclick="addToCart('Smart Watch', 2999)">Add to Cart</button>
    </div>

    <div class="product">
      <img src="https://via.placeholder.com/300x200?text=Bag" alt="Product 3">
      <h3>Backpack</h3>
      <p>₹1499</p>
      <button onclick="addToCart('Backpack', 1499)">Add to Cart</button>
    </div>

    <!-- Cart Section -->
    <div class="cart">
      <h2>🛒 Your Cart</h2>
      <ul id="cartItems"></ul>
      <div class="total">Total: ₹<span id="total">0</span></div>
    </div>
  </div>

  <script>
    let cart = [];

    function addToCart(name, price) {
      cart.push({ name, price });
      updateCart();
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById("cartItems");
      const totalDisplay = document.getElementById("total");
      cartItems.innerHTML = "";

      let total = 0;
      cart.forEach((item, index) => {
        total += item.price;
        const li = document.createElement("li");
        li.innerHTML = `
          ${item.name} - ₹${item.price}
          <button class="remove" onclick="removeFromCart(${index})">Remove</button>
        `;
        cartItems.appendChild(li);
      });

      totalDisplay.textContent = total;
    }
  </script>

</body>
</html>
