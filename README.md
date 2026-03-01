# Biteoota<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biteo - Prakritik Pushtir Protishruti</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #fcfcf9;
            overflow-x: hidden;
        }

        .leaf-pattern {
            background-image: url("data:image/svg+xml,%3Csvg width='120' height='120' viewBox='0 0 120 120' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M60 20C60 20 55 5 45 5C35 5 25 15 25 25C25 40 60 55 60 55C60 55 95 40 95 25C95 15 85 5 75 5C65 5 60 20 60 20Z' fill='%232D5A27' fill-opacity='0.05'/%3E%3C/svg%3E");
        }

        .animate-spin-slow {
            animation: spin 20s linear infinite;
        }

        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .view-section {
            display: none;
        }

        .view-section.active {
            display: block;
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .product-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .product-card:hover {
            box-shadow: 0 30px 60px -12px rgba(45, 90, 39, 0.2);
            transform: translateY(-10px);
        }
        
        input[type="radio"]:checked + div {
            border-color: #2D5A27;
            background-color: #f0fdf4;
        }
    </style>
</head>
<body class="selection:bg-[#82C341] selection:text-white">
    <div class="fixed inset-0 leaf-pattern pointer-events-none z-0"></div>

    <!-- Navigation -->
    <nav class="sticky top-0 z-50 bg-white/80 backdrop-blur-xl border-b border-gray-100 shadow-sm">
        <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
            <div class="cursor-pointer transition-transform hover:scale-105 flex flex-col items-start" onclick="showView('home')">
                <div class="flex items-center gap-3">
                    <div class="relative flex items-center">
                        <div class="absolute -top-5 left-0">
                            <svg width="22" height="22" viewBox="0 0 24 24" fill="none">
                                <path d="M12 22C12 22 8 18 4 18C1 18 0 20 0 22C0 25 4 27 12 30" fill="#82C341" transform="rotate(-15 12 22)" />
                                <path d="M12 22C12 22 16 18 20 18C23 18 24 20 24 22C24 25 20 27 12 30" fill="#2D5A27" transform="rotate(15 12 22)" />
                            </svg>
                        </div>
                        <span class="text-4xl font-black text-[#2D5A27] tracking-tighter flex items-center">
                            Bite<span class="relative inline-block ml-[-2px]">o<span class="absolute top-[45%] left-1/2 -translate-x-1/2 -translate-y-1/2 w-3 h-3 bg-[#F29100] rounded-full border-2 border-white shadow-sm"></span></span>
                        </span>
                    </div>
                </div>
                <div class="text-[8px] font-black tracking-[0.4em] text-[#2D5A27] uppercase mt-[-4px] ml-1">Prakritik Pushtir Protishruti</div>
            </div>

            <div class="hidden md:flex items-center gap-10 font-black text-gray-600 text-xs uppercase tracking-widest">
                <button onclick="showView('home')" class="hover:text-[#2D5A27] transition-all">Home</button>
                <button onclick="showView('shop')" class="hover:text-[#2D5A27] transition-all">Shop</button>
                <button onclick="showView('dashboard')" class="hover:text-[#2D5A27] transition-all text-orange-600">My Orders</button>
            </div>

            <div class="flex items-center gap-5">
                <button onclick="showView('cart')" class="relative p-3 bg-gray-100/50 text-gray-700 hover:bg-[#2D5A27] hover:text-white rounded-2xl transition-all shadow-sm">
                    <i data-lucide="shopping-bag" class="w-6 h-6"></i>
                    <span id="cart-count" class="hidden absolute -top-1 -right-1 bg-red-500 text-white text-[10px] w-5 h-5 flex items-center justify-center rounded-full font-black border-2 border-white">0</span>
                </button>
            </div>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto px-6 py-12 relative z-10 min-h-[70vh]">
        
        <!-- View: Home -->
        <section id="view-home" class="view-section active">
            <div class="relative overflow-hidden bg-white/60 backdrop-blur-md min-h-[600px] flex items-center rounded-[5rem] shadow-2xl border border-white mb-20">
                <div class="container mx-auto px-10 flex flex-col md:flex-row items-center justify-between gap-12 py-20">
                    <div class="md:w-1/2 text-center md:text-left space-y-8">
                        <div class="inline-block bg-[#82C341]/10 text-[#2D5A27] px-6 py-2 rounded-full font-black text-sm uppercase tracking-widest mb-4">
                            Premium Fruit Nutrition
                        </div>
                        <h1 class="text-6xl md:text-8xl font-black text-[#2D5A27] leading-[0.9] tracking-tighter">
                            Organic <br/><span class="text-[#82C341]">Fruits</span> <br/>Power
                        </h1>
                        <p class="text-gray-500 font-bold text-2xl">Pure Apple, Banana & Orange Extracts. Shustho thakun prokritir shathe!</p>
                        <button onclick="showView('shop')" class="mt-10 bg-[#2D5A27] text-white px-12 py-6 rounded-[2rem] font-black text-2xl hover:bg-black transition-all flex items-center gap-5 mx-auto md:mx-0 shadow-3xl group">
                            Order Now <i data-lucide="arrow-right" class="group-hover:translate-x-2 transition-transform"></i>
                        </button>
                    </div>
                    <div class="md:w-1/2 h-[500px] relative flex items-center justify-center">
                        <div id="threejs-hero-container" class="w-full h-full"></div>
                    </div>
                </div>
            </div>

            <div class="mb-32 px-4">
                <h2 class="text-6xl font-black text-gray-800 tracking-tighter mb-4">Best Sellers</h2>
                <p class="text-[#82C341] font-black uppercase tracking-widest mb-16 text-xl text-center md:text-left">Purest Ingredients from Farm to Table</p>
                <div id="popular-products" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-12">
                    <!-- Products injected by JS -->
                </div>
            </div>
        </section>

        <!-- View: Shop -->
        <section id="view-shop" class="view-section">
            <h2 class="text-7xl font-black text-[#2D5A27] mb-20 uppercase tracking-tighter">Full Collection</h2>
            <div id="shop-grid" class="grid grid-cols-1 md:grid-cols-3 gap-12">
                <!-- Shop items -->
            </div>
        </section>

        <!-- View: Cart -->
        <section id="view-cart" class="view-section max-w-4xl mx-auto">
            <h2 class="text-6xl font-black text-gray-800 mb-16 tracking-tighter text-center">Your Bag</h2>
            <div id="cart-items" class="space-y-6 mb-12"></div>
            <div id="cart-summary" class="bg-white p-12 rounded-[4rem] shadow-2xl border border-gray-100">
                <div class="flex justify-between text-3xl font-black text-gray-800 mb-4">
                    <span>Subtotal</span>
                    <span id="cart-total-no-delivery" class="text-[#2D5A27]">৳0</span>
                </div>
                <p class="text-gray-400 font-bold mb-10 italic">Delivery charge will be added in the next step.</p>
                <button onclick="showView('checkout')" class="w-full bg-[#2D5A27] text-white py-8 rounded-[2.5rem] font-black text-2xl shadow-3xl hover:bg-black transition-all">Proceed to Checkout</button>
            </div>
        </section>

        <!-- View: Checkout -->
        <section id="view-checkout" class="view-section max-w-4xl mx-auto">
            <div class="bg-white p-12 md:p-16 rounded-[5rem] shadow-4xl border border-gray-100">
                <h2 class="text-5xl font-black text-gray-800 mb-4 tracking-tighter">Order Payment List</h2>
                <p class="text-orange-600 font-black mb-12 uppercase tracking-widest text-sm">Payment: Cash on Delivery Only</p>
                
                <form id="checkout-form" onsubmit="handlePlaceOrder(event)" class="space-y-10">
                    <!-- Location Selection -->
                    <div class="bg-gray-50 p-8 rounded-[3rem] border border-gray-100 shadow-inner">
                        <h3 class="text-xl font-black text-[#2D5A27] uppercase tracking-widest mb-6">Delivery Area Selection</h3>
                        <div class="flex flex-col md:flex-row gap-6">
                            <label class="relative flex-1 cursor-pointer group">
                                <input type="radio" name="delivery-loc" value="60" checked onchange="updateDeliveryCharge(60)" class="hidden peer">
                                <div class="p-6 bg-white border-2 border-transparent peer-checked:border-[#2D5A27] peer-checked:bg-green-50 rounded-3xl transition-all shadow-sm">
                                    <p class="font-black text-gray-800 text-lg">Inside Dhaka</p>
                                    <p class="text-[#2D5A27] font-bold">Fee: ৳60</p>
                                </div>
                            </label>
                            <label class="relative flex-1 cursor-pointer group">
                                <input type="radio" name="delivery-loc" value="140" onchange="updateDeliveryCharge(140)" class="hidden peer">
                                <div class="p-6 bg-white border-2 border-transparent peer-checked:border-[#2D5A27] peer-checked:bg-green-50 rounded-3xl transition-all shadow-sm">
                                    <p class="font-black text-gray-800 text-lg">Outside Dhaka</p>
                                    <p class="text-[#2D5A27] font-bold">Fee: ৳140</p>
                                </div>
                            </label>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <div class="space-y-4">
                            <label class="block font-black text-gray-500 uppercase text-xs tracking-widest">Customer Name</label>
                            <input type="text" id="cust-name" required placeholder="Full Name" class="w-full bg-gray-50 border-none rounded-3xl px-8 py-5 focus:ring-4 focus:ring-[#82C341]/20 shadow-inner">
                        </div>
                        <div class="space-y-4">
                            <label class="block font-black text-gray-500 uppercase text-xs tracking-widest">Mobile Number</label>
                            <input type="tel" id="cust-phone" required placeholder="01XXXXXXXXX" class="w-full bg-gray-50 border-none rounded-3xl px-8 py-5 focus:ring-4 focus:ring-[#82C341]/20 shadow-inner">
                        </div>
                    </div>

                    <div class="space-y-4">
                        <label class="block font-black text-gray-500 uppercase text-xs tracking-widest">Full Address</label>
                        <textarea id="cust-address" required placeholder="Full Address with District" class="w-full bg-gray-50 border-none rounded-3xl px-8 py-5 focus:ring-4 focus:ring-[#82C341]/20 shadow-inner h-32"></textarea>
                    </div>

                    <!-- Payment List Summary -->
                    <div class="bg-white p-10 rounded-[3rem] border-2 border-[#2D5A27] space-y-4 shadow-xl">
                        <div class="flex justify-between font-bold text-gray-400">
                            <span>Order Subtotal:</span>
                            <span id="checkout-subtotal">৳0</span>
                        </div>
                        <div class="flex justify-between font-bold text-gray-400">
                            <span>Delivery (Cash on Delivery):</span>
                            <span id="checkout-delivery-fee">৳60</span>
                        </div>
                        <div class="flex justify-between items-center pt-6 border-t-2 border-dashed border-gray-100">
                            <span class="text-2xl font-black text-gray-800 uppercase tracking-tighter">Total Amount Payable</span>
                            <span id="checkout-final-total" class="text-5xl font-black text-[#2D5A27]">৳0</span>
                        </div>
                    </div>

                    <button type="submit" class="w-full bg-[#2D5A27] text-white py-8 rounded-[2.5rem] font-black text-2xl shadow-3xl hover:bg-black transition-all">Confirm My Order</button>
                </form>
            </div>
        </section>

        <!-- View: Success -->
        <section id="view-success" class="view-section max-w-3xl mx-auto text-center py-24">
            <div class="bg-white p-20 rounded-[5rem] shadow-4xl border border-gray-100 flex flex-col items-center gap-12">
                <div class="w-40 h-40 bg-green-50 text-[#2D5A27] rounded-full flex items-center justify-center shadow-inner">
                    <i data-lucide="check-circle" class="w-24 h-24"></i>
                </div>
                <h2 class="text-6xl font-black text-gray-800 tracking-tighter">Dhonyobad!</h2>
                <p class="text-xl text-gray-500 font-bold italic">Notification sent to: <span class="text-[#2D5A27]">rokekhankoy@gmail.com</span></p>
                <div class="w-full bg-gray-50 p-10 rounded-[3.5rem] text-left border border-gray-100">
                    <p id="success-id" class="font-black text-gray-700 text-2xl mb-2"></p>
                    <p class="font-bold text-[#82C341] uppercase tracking-widest text-sm">Status: Order Confirmed</p>
                    <p id="success-total" class="font-black text-[#2D5A27] text-3xl mt-6"></p>
                </div>
                <button onclick="showView('home')" class="bg-[#2D5A27] text-white px-14 py-7 rounded-[3rem] font-black text-3xl hover:bg-black transition-all shadow-3xl">Go Back Home</button>
            </div>
        </section>

        <!-- View: Dashboard -->
        <section id="view-dashboard" class="view-section max-w-5xl mx-auto">
            <h2 class="text-6xl font-black text-gray-800 tracking-tighter mb-16">My Dashboard</h2>
            <div id="order-dashboard-list" class="space-y-8">
                <!-- Orders injected by JS -->
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-gray-100 py-40 rounded-t-[8rem] shadow-4xl relative z-10 mt-32">
        <div class="max-w-7xl mx-auto px-16 grid grid-cols-1 md:grid-cols-4 gap-32 text-center md:text-left">
            <div class="space-y-12">
                <span class="text-4xl font-black text-[#2D5A27] tracking-tighter">Biteo</span>
                <p class="text-gray-500 font-bold text-xl leading-relaxed">Organic Fruit Nutrition. <br>Notification: rokekhankoy@gmail.com</p>
            </div>
            <div><h4 class="font-black mb-12 text-2xl text-gray-800 uppercase tracking-widest">Links</h4><ul class="space-y-6 text-gray-500 font-black text-lg"><li><button onclick="showView('shop')" class="hover:text-[#2D5A27]">Shop</button></li><li><button onclick="showView('dashboard')" class="hover:text-[#2D5A27]">Dashboard</button></li></ul></div>
            <div><h4 class="font-black mb-12 text-2xl text-gray-800 uppercase tracking-widest">Support</h4><p class="text-gray-500 font-bold uppercase tracking-widest">Cash On Delivery Only</p></div>
            <div>
                <h4 class="font-black mb-12 text-2xl text-gray-800 uppercase tracking-widest">Stay Organic</h4>
                <button class="w-full bg-[#2D5A27] text-white py-6 rounded-[2.5rem] font-black text-2xl shadow-3xl hover:bg-black transition-all">Contact Us</button>
            </div>
        </div>
        <div class="text-center mt-20 pt-10 border-t border-gray-50 text-gray-400 font-black text-xs uppercase tracking-[0.5em]">© 2024 Biteo • Natural Nutrition</div>
    </footer>

    <script>
        const products = [
            { 
                id: 1, name: 'Apple Powder', price: 420, category: 'Powder', 
                image: 'https://images.unsplash.com/photo-1567306226416-28f0efdc88ce?auto=format&fit=crop&q=80&w=400', 
                usage: 'Ei powder diye Milkshake, Smoothie, ebong Cake toiri kora jay. Shishuder healthy option.' 
            },
            { 
                id: 2, name: 'Apple Chips', price: 180, category: 'Chips', 
                image: 'https://images.unsplash.com/photo-1560806133-1e34105f549c?auto=format&fit=crop&q=80&w=400', 
                usage: 'Shorasori snack hishebe khawa jay ba breakfast cereal-er sathe meshano jay.' 
            },
            { 
                id: 3, name: 'Banana Chips', price: 150, category: 'Chips', 
                image: 'https://images.unsplash.com/photo-1610450949065-2f235552a44c?auto=format&fit=crop&q=80&w=400', 
                usage: 'Instant energy-r jonno darun snack. Cha ba Coffee-r shathe bhalo lage.' 
            },
            { 
                id: 4, name: 'Banana Powder', price: 350, category: 'Powder', 
                image: 'https://images.unsplash.com/photo-1528821128474-27f963b062bf?auto=format&fit=crop&q=80&w=400', 
                usage: 'Pustikor Baby Food prostut korte ba Protein Smoothie-te byabohar korun.' 
            },
            { 
                id: 5, name: 'Orange Powder', price: 390, category: 'Powder', 
                image: 'https://images.unsplash.com/photo-1547514701-42782101795e?auto=format&fit=crop&q=80&w=400', 
                usage: 'Vitamin C Rich refresh juice banate ba Salad dressing-e byabohar korun.' 
            },
        ];

        let cart = [];
        let orders = [];
        let deliveryCharge = 60;

        function showView(viewId) {
            document.querySelectorAll('.view-section').forEach(section => section.classList.remove('active'));
            document.getElementById(`view-${viewId}`).classList.add('active');
            window.scrollTo({ top: 0, behavior: 'smooth' });
            if (viewId === 'dashboard') renderDashboard();
            updateCartUI();
        }

        function updateDeliveryCharge(value) {
            deliveryCharge = parseInt(value);
            updateCartUI();
        }

        function directOrder(productId) {
            const product = products.find(p => p.id === productId);
            cart = [{...product, qty: 1}]; 
            updateCartUI();
            showView('checkout');
        }

        function renderProducts() {
            const popularContainer = document.getElementById('popular-products');
            const shopContainer = document.getElementById('shop-grid');
            const html = (p) => `
                <div class="product-card bg-white rounded-[4rem] p-10 shadow-2xl border border-gray-50 flex flex-col h-full overflow-hidden">
                    <div class="relative h-64 mb-8 overflow-hidden rounded-[3rem] bg-gray-50">
                        <img src="${p.image}" class="w-full h-full object-cover">
                    </div>
                    <h3 class="font-black text-3xl text-gray-800 mb-2">${p.name}</h3>
                    <div class="bg-green-50 p-6 rounded-2xl mb-10 flex-grow">
                        <p class="text-[#2D5A27] text-sm font-bold leading-relaxed">
                            <span class="block uppercase text-[10px] tracking-widest opacity-60 mb-2">Instructions:</span>
                            ${p.usage}
                        </p>
                    </div>
                    <div class="flex items-center justify-between pt-6 border-t border-dashed border-gray-200 mb-8">
                        <span class="text-4xl font-black text-[#2D5A27]">৳${p.price}</span>
                        <button onclick="addToCart(${p.id})" class="bg-gray-100 text-[#2D5A27] p-4 rounded-2xl hover:bg-[#82C341] hover:text-white transition-all shadow-md">
                            <i data-lucide="plus"></i>
                        </button>
                    </div>
                    <button onclick="directOrder(${p.id})" class="w-full bg-[#2D5A27] text-white py-5 rounded-2xl font-black text-xl hover:bg-black transition-all shadow-xl">
                        Order Now
                    </button>
                </div>
            `;
            popularContainer.innerHTML = products.slice(0, 3).map(html).join('');
            shopContainer.innerHTML = products.map(html).join('');
            lucide.createIcons();
        }

        function addToCart(id) {
            const p = products.find(item => item.id === id);
            const ex = cart.find(i => i.id === id);
            if (ex) ex.qty++; else cart.push({...p, qty: 1});
            updateCartUI();
        }

        function updateCartUI() {
            const count = document.getElementById('cart-count');
            const totalNoDel = document.getElementById('cart-total-no-delivery');
            const items = document.getElementById('cart-items');
            
            const subtotal = cart.reduce((s, i) => s + (i.price * i.qty), 0);
            
            if (count) {
                const totalItems = cart.reduce((s, i) => s + i.qty, 0);
                count.innerText = totalItems;
                count.classList.toggle('hidden', totalItems === 0);
            }

            if (items) {
                if (cart.length === 0) {
                    items.innerHTML = '<div class="text-center py-20 font-black text-2xl text-gray-300">No items in bag</div>';
                } else {
                    items.innerHTML = cart.map(i => `
                        <div class="bg-white p-8 rounded-[3rem] flex items-center gap-8 shadow-xl border border-gray-50 transition-all hover:scale-[1.01]">
                            <img src="${i.image}" class="w-20 h-20 object-cover rounded-2xl">
                            <div class="flex-1">
                                <h3 class="font-black text-2xl text-gray-800">${i.name}</h3>
                                <p class="text-[#2D5A27] font-black text-xl">৳${i.price} x ${i.qty}</p>
                            </div>
                            <button onclick="removeFromCart(${i.id})" class="text-red-400 p-2"><i data-lucide="trash-2"></i></button>
                        </div>
                    `).join('');
                }
            }

            if (totalNoDel) totalNoDel.innerText = `৳${subtotal}`;

            const checkSub = document.getElementById('checkout-subtotal');
            const checkFee = document.getElementById('checkout-delivery-fee');
            const checkFinal = document.getElementById('checkout-final-total');

            if (checkSub) checkSub.innerText = `৳${subtotal}`;
            if (checkFee) checkFee.innerText = `৳${deliveryCharge}`;
            if (checkFinal) checkFinal.innerText = `৳${subtotal + deliveryCharge}`;

            lucide.createIcons();
        }

        function removeFromCart(id) {
            cart = cart.filter(i => i.id !== id);
            updateCartUI();
        }

        function handlePlaceOrder(e) {
            e.preventDefault();
            const orderId = 'BT-' + Math.floor(Math.random() * 90000 + 10000);
            const subtotal = cart.reduce((s, i) => s + (i.price * i.qty), 0);
            
            const order = {
                id: orderId,
                name: document.getElementById('cust-name').value,
                phone: document.getElementById('cust-phone').value,
                address: document.getElementById('cust-address').value,
                deliveryFee: deliveryCharge,
                total: subtotal + deliveryCharge,
                items: [...cart],
                date: new Date().toLocaleString()
            };
            orders.push(order);
            
            console.log(`Notification sent to rokekhankoy@gmail.com for order ${orderId}`);
            
            document.getElementById('success-id').innerText = `Order ID: ${orderId}`;
            document.getElementById('success-total').innerText = `Total Paid: ৳${order.total}`;
            
            cart = [];
            updateCartUI();
            showView('success');
        }

        function renderDashboard() {
            const list = document.getElementById('order-dashboard-list');
            if (orders.length === 0) {
                list.innerHTML = '<div class="bg-white p-20 rounded-[4rem] shadow-xl text-center text-gray-400 font-black text-2xl border border-gray-100">No past orders.</div>';
                return;
            }
            list.innerHTML = orders.map(o => `
                <div class="bg-white p-10 rounded-[4rem] shadow-2xl border border-gray-100 relative overflow-hidden">
                    <div class="flex justify-between items-center mb-8 border-b pb-6">
                        <div>
                             <h3 class="text-3xl font-black text-[#2D5A27]">${o.id}</h3>
                             <p class="text-gray-400 font-bold">${o.date}</p>
                        </div>
                        <span class="bg-green-50 text-[#2D5A27] px-6 py-2 rounded-full font-black text-xs uppercase border border-[#82C341]">Processing</span>
                    </div>
                    <div class="grid md:grid-cols-2 gap-8 text-gray-600 font-bold mb-10">
                         <div><p class="text-xs text-gray-400 uppercase tracking-widest mb-1">Buyer</p>${o.name} (${o.phone})</div>
                         <div><p class="text-xs text-gray-400 uppercase tracking-widest mb-1">Destination</p>${o.address}</div>
                    </div>
                    <div class="flex flex-col md:flex-row justify-between items-end gap-6 pt-6 border-t border-dashed">
                        <div class="flex gap-4">
                             ${o.items.map(i => `<img src="${i.image}" class="w-16 h-16 rounded-2xl object-cover shadow-sm border border-gray-100">`).join('')}
                        </div>
                        <div class="text-right">
                             <p class="text-sm font-bold text-gray-400 italic">Fee: ৳${o.deliveryFee}</p>
                             <p class="text-5xl font-black text-[#2D5A27]">৳${o.total}</p>
                        </div>
                    </div>
                </div>
            `).reverse().join('');
        }

        function initHero3D() {
            const container = document.getElementById('threejs-hero-container');
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, container.clientWidth / container.clientHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer.setSize(container.clientWidth, container.clientHeight);
            container.appendChild(renderer.domElement);

            const geometry = new THREE.BoxGeometry(2, 3, 0.8);
            const material = new THREE.MeshStandardMaterial({ color: 0x2D5A27 });
            const pack = new THREE.Mesh(geometry, material);
            scene.add(pack);

            const light = new THREE.DirectionalLight(0xffffff, 1.5);
            light.position.set(5, 5, 5);
            scene.add(light);
            scene.add(new THREE.AmbientLight(0x404040, 1.5));
            camera.position.z = 5;

            function animate() {
                requestAnimationFrame(animate);
                pack.rotation.y += 0.015;
                renderer.render(scene, camera);
            }
            animate();
            
            window.addEventListener('resize', () => {
                renderer.setSize(container.clientWidth, container.clientHeight);
                camera.aspect = container.clientWidth / container.clientHeight;
                camera.updateProjectionMatrix();
            });
        }

        document.addEventListener('DOMContentLoaded', () => {
            renderProducts();
            initHero3D();
            lucide.createIcons();
        });
    </script>
</body>
</html>

