# FADLU-S-SHOP
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SpeedKicks - Toko Sepatu Online</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: #667eea;
        }

        .cart-btn {
            background: #667eea;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
        }

        .cart-btn:hover {
            background: #5568d3;
            transform: translateY(-2px);
        }

        .cart-count {
            background: #ff6b6b;
            padding: 2px 8px;
            border-radius: 10px;
            font-size: 12px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
            transition: all 0.3s;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.25);
        }

        .product-image {
            width: 100%;
            height: 250px;
            overflow: hidden;
            background: #f5f5f5;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .product-card:hover .product-image img {
            transform: scale(1.1);
        }

        .product-info {
            padding: 20px;
        }

        .product-brand {
            color: #667eea;
            font-weight: bold;
            font-size: 14px;
            margin-bottom: 5px;
        }

        .product-name {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 10px;
            color: #333;
        }

        .product-price {
            font-size: 24px;
            color: #ff6b6b;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .add-to-cart {
            width: 100%;
            background: #667eea;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s;
        }

        .add-to-cart:hover {
            background: #5568d3;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            max-width: 500px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-title {
            font-size: 24px;
            font-weight: bold;
            color: #333;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 30px;
            cursor: pointer;
            color: #999;
        }

        .cart-item {
            display: flex;
            gap: 15px;
            padding: 15px;
            border-bottom: 1px solid #eee;
        }

        .cart-item-image {
            width: 80px;
            height: 80px;
            border-radius: 8px;
            overflow: hidden;
            flex-shrink: 0;
        }

        .cart-item-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .cart-item-price {
            color: #ff6b6b;
            font-weight: bold;
        }

        .cart-item-controls {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }

        .qty-btn {
            background: #667eea;
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
        }

        .qty-display {
            min-width: 30px;
            text-align: center;
            font-weight: bold;
        }

        .remove-btn {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            margin-left: 10px;
        }

        .cart-total {
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #667eea;
            font-size: 20px;
            font-weight: bold;
            text-align: right;
        }

        .checkout-btn {
            width: 100%;
            background: #4caf50;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            margin-top: 15px;
            transition: all 0.3s;
        }

        .checkout-btn:hover {
            background: #45a049;
        }

        .empty-cart {
            text-align: center;
            padding: 40px;
            color: #999;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">⚡ SpeedKicks</div>
            <button class="cart-btn" onclick="toggleCart()">
                🛒 Keranjang <span class="cart-count" id="cartCount">0</span>
            </button>
        </header>

        <div class="products-grid" id="productsGrid"></div>
    </div>

    <div class="modal" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">🛒 Keranjang Belanja</div>
                <button class="close-btn" onclick="toggleCart()">&times;</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-total">
                Total: <span id="totalPrice">Rp 0</span>
            </div>
            <button class="checkout-btn" onclick="checkout()">Checkout Sekarang</button>
        </div>
    </div>

    <script>
        const products = [
            {
                id: 1,
                brand: "PUMA",
                name: "Speed Cat OG",
                price: 1299000,
                image: "https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?w=500&h=500&fit=crop"
            },
            {
                id: 2,
                brand: "PUMA",
                name: "Speed Cat Sparco",
                price: 1499000,
                image: "https://images.unsplash.com/photo-1603808033192-082d6919d3e1?w=500&h=500&fit=crop"
            },
            {
                id: 3,
                brand: "NIKE",
                name: "Air Max 270",
                price: 1899000,
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500&h=500&fit=crop"
            },
            {
                id: 4,
                brand: "ADIDAS",
                name: "Ultraboost 23",
                price: 2299000,
                image: "https://images.unsplash.com/photo-1608231387042-66d1773070a5?w=500&h=500&fit=crop"
            },
            {
                id: 5,
                brand: "NIKE",
                name: "Jordan 1 Retro",
                price: 2599000,
                image: "https://images.unsplash.com/photo-1607522370275-f14206abe5d3?w=500&h=500&fit=crop"
            },
            {
                id: 6,
                brand: "PUMA",
                name: "Suede Classic",
                price: 999000,
                image: "https://images.unsplash.com/photo-1603808033192-082d6919d3e1?w=500&h=500&fit=crop"
            },
            {
                id: 7,
                brand: "ADIDAS",
                name: "Stan Smith",
                price: 1199000,
                image: "https://images.unsplash.com/photo-1621665422894-8f7f0e32bfbc?w=500&h=500&fit=crop"
            },
            {
                id: 8,
                brand: "NIKE",
                name: "React Infinity Run",
                price: 1799000,
                image: "https://images.unsplash.com/photo-1539185441755-769473a23570?w=500&h=500&fit=crop"
            }
        ];

        let cart = [];

        function formatPrice(price) {
            return 'Rp ' + price.toLocaleString('id-ID');
        }

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = products.map(product => `
                <div class="product-card">
                    <div class="product-image">
                        <img src="${product.image}" alt="${product.name}">
                    </div>
                    <div class="product-info">
                        <div class="product-brand">${product.brand}</div>
                        <div class="product-name">${product.name}</div>
                        <div class="product-price">${formatPrice(product.price)}</div>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">
                            Tambah ke Keranjang
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const cartItem = cart.find(item => item.id === productId);

            if (cartItem) {
                cartItem.quantity++;
            } else {
                cart.push({...product, quantity: 1});
            }

            updateCart();
            showNotification('Produk ditambahkan ke keranjang!');
        }

        function updateCart() {
            document.getElementById('cartCount').textContent = cart.reduce((sum, item) => sum + item.quantity, 0);
            renderCart();
        }

        function renderCart() {
            const cartItems = document.getElementById('cartItems');
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<div class="empty-cart">Keranjang masih kosong</div>';
                document.getElementById('totalPrice').textContent = 'Rp 0';
                return;
            }

            cartItems.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <div class="cart-item-image">
                        <img src="${item.image}" alt="${item.name}">
                    </div>
                    <div style="flex: 1;">
                        <div class="cart-item-info">
                            <div class="cart-item-name">${item.brand} ${item.name}</div>
                            <div class="cart-item-price">${formatPrice(item.price)}</div>
                        </div>
                        <div class="cart-item-controls">
                            <button class="qty-btn" onclick="changeQuantity(${item.id}, -1)">-</button>
                            <div class="qty-display">${item.quantity}</div>
                            <button class="qty-btn" onclick="changeQuantity(${item.id}, 1)">+</button>
                            <button class="remove-btn" onclick="removeFromCart(${item.id})">🗑️</button>
                        </div>
                    </div>
                </div>
            `).join('');

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            document.getElementById('totalPrice').textContent = formatPrice(total);
        }

        function changeQuantity(productId, change) {
            const cartItem = cart.find(item => item.id === productId);
            if (cartItem) {
                cartItem.quantity += change;
                if (cartItem.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCart();
                }
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function toggleCart() {
            document.getElementById('cartModal').classList.toggle('active');
        }

        function checkout() {
            if (cart.length === 0) {
                alert('Keranjang masih kosong!');
                return;
            }

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const items = cart.map(item => `${item.brand} ${item.name} x${item.quantity}`).join('\n');
            
            alert(`Terima kasih atas pembelian Anda!\n\nRincian Pesanan:\n${items}\n\nTotal: ${formatPrice(total)}\n\nPesanan Anda akan segera diproses.`);
            
            cart = [];
            updateCart();
            toggleCart();
        }

        function showNotification(message) {
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background: #4caf50;
                color: white;
                padding: 15px 25px;
                border-radius: 8px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.3);
                z-index: 2000;
                animation: slideIn 0.3s ease;
            `;
            notification.textContent = message;
            document.body.appendChild(notification);

            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => notification.remove(), 300);
            }, 2000);
        }

        // Initialize
        renderProducts();
    </script>

    <style>
        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        @keyframes slideOut {
            from {
                transform: translateX(0);
                opacity: 1;
            }
            to {
                transform: translateX(400px);
                opacity: 0;
            }
        }
    </style>
</body>
</html>
