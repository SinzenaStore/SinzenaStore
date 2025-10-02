<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Minha Loja Online</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0; padding: 0;
      background: #f8f8f8;
    }
    header {
      background: #222;
      color: #fff;
      padding: 15px;
      text-align: center;
    }
    nav {
      background: #444;
      padding: 10px;
      text-align: center;
    }
    nav a {
      color: #fff;
      margin: 0 10px;
      text-decoration: none;
    }
    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: 20px;
    }
    .product {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 5px;
      margin: 10px;
      padding: 15px;
      width: 250px;
      text-align: center;
    }
    .product img {
      width: 100%;
      height: auto;
    }
    .cart {
      position: fixed;
      right: 0;
      top: 0;
      width: 300px;
      height: 100%;
      background: #fff;
      border-left: 2px solid #ddd;
      padding: 20px;
      overflow-y: auto;
    }
    .cart h2 {
      margin-top: 0;
    }
    .cart-item {
      border-bottom: 1px solid #ddd;
      padding: 10px 0;
    }
    .btn {
      display: inline-block;
      padding: 10px;
      background: #28a745;
      color: #fff;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
    }
    .btn:hover {
      background: #218838;
    }
    footer {
      background: #222;
      color: #fff;
      text-align: center;
      padding: 15px;
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Minha Loja Online</h1>
    <p>Bem-vindo! Confira nossos produtos abaixo.</p>
  </header>

  <nav>
    <a href="#">Início</a>
    <a href="#produtos">Produtos</a>
    <a href="#contato">Contato</a>
  </nav>

  <section id="produtos" class="container">
    <div class="product">
      <img src="https://via.placeholder.com/250x200" alt="Produto 1">
      <h3>Produto 1</h3>
      <p>Descrição breve do produto.</p>
      <p><strong>R$ 50,00</strong></p>
      <button class="btn" onclick="addToCart('Produto 1', 50)">Adicionar</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/250x200" alt="Produto 2">
      <h3>Produto 2</h3>
      <p>Descrição breve do produto.</p>
      <p><strong>R$ 80,00</strong></p>
      <button class="btn" onclick="addToCart('Produto 2', 80)">Adicionar</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/250x200" alt="Produto 3">
      <h3>Produto 3</h3>
      <p>Descrição breve do produto.</p>
      <p><strong>R$ 120,00</strong></p>
      <button class="btn" onclick="addToCart('Produto 3', 120)">Adicionar</button>
    </div>
  </section>

  <div class="cart">
    <h2>Carrinho</h2>
    <div id="cart-items"></div>
    <h3>Total: R$ <span id="total">0</span>,00</h3>
    <button class="btn" onclick="checkout()">Finalizar Compra</button>
  </div>

  <footer id="contato">
    <p>Contato: <a href="mailto:minhaloja@email.com">minhaloja@email.com</a></p>
    <p>WhatsApp: (00) 90000-0000</p>
  </footer>

  <script>
    let cart = [];
    let total = 0;

    function addToCart(product, price) {
      cart.push({ product, price });
      total += price;
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById('cart-items');
      cartItems.innerHTML = '';
      cart.forEach((item, index) => {
        cartItems.innerHTML += `
          <div class="cart-item">
            ${item.product} - R$ ${item.price},00 
            <button onclick="removeItem(${index})">❌</button>
          </div>`;
      });
      document.getElementById('total').textContent = total;
    }

    function removeItem(index) {
      total -= cart[index].price;
      cart.splice(index, 1);
      updateCart();
    }

    function checkout() {
      if (cart.length === 0) {
        alert("Seu carrinho está vazio!");
      } else {
        alert("Compra finalizada! Total: R$ " + total + ",00");
      }
    }
  </script>

</body>
</html>
