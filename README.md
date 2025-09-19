<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🏴‍☠️ Blox Fruits</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            min-height: 100vh;
            color: white;
        }

        .overlay {
            background: rgba(0, 0, 0, 0.7);
            min-height: 100vh;
            backdrop-filter: blur(2px);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .card {
            background: rgba(30, 30, 30, 0.95);
            border-radius: 15px;
            padding: 25px;
            margin: 20px 0;
            border: 2px solid rgba(255, 215, 0, 0.3);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .btn {
            background: linear-gradient(45deg, #ff6b35, #f7931e);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 107, 53, 0.4);
            animation: pulse 0.6s ease-in-out;
        }

        .btn:disabled {
            background: #666;
            cursor: not-allowed;
            transform: none;
            animation: none;
        }

        .input {
            width: 100%;
            padding: 12px;
            border: 2px solid rgba(255, 215, 0, 0.3);
            border-radius: 8px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            font-size: 16px;
            margin: 8px 0;
            transition: border-color 0.3s ease;
        }

        .input:focus {
            outline: none;
            border-color: #ff6b35;
            box-shadow: 0 0 10px rgba(255, 107, 53, 0.3);
        }

        .input::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 3em;
            color: #ffd700;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
            margin-bottom: 10px;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8), 0 0 10px #ffd700; }
            to { text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8), 0 0 20px #ffd700, 0 0 30px #ffd700; }
        }

        .stats-bar {
            display: flex;
            justify-content: space-around;
            background: rgba(0, 0, 0, 0.8);
            padding: 15px;
            border-radius: 10px;
            margin: 20px 0;
            border: 1px solid #ffd700;
        }

        .stat {
            text-align: center;
            color: #ffd700;
            font-weight: bold;
        }

        .chat-container {
            height: 400px;
            overflow-y: auto;
            background: rgba(0, 0, 0, 0.8);
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            border: 2px solid rgba(255, 215, 0, 0.3);
        }

        .message {
            margin: 10px 0;
            padding: 10px;
            border-radius: 8px;
            animation: messageSlide 0.3s ease-out;
        }

        @keyframes messageSlide {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .message.user {
            background: rgba(255, 107, 53, 0.8);
            margin-left: 20%;
            text-align: right;
        }

        .message.system {
            background: rgba(0, 123, 255, 0.8);
        }

        .message.fruit {
            background: rgba(40, 167, 69, 0.8);
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .fruit-image {
            width: 50px;
            height: 50px;
            object-fit: contain;
            border-radius: 8px;
            border: 2px solid #ffd700;
        }

        .chat-input-container {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .chat-input {
            flex: 1;
        }

        .settings-panel {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(30, 30, 30, 0.95);
            border-radius: 10px;
            padding: 20px;
            border: 2px solid #ffd700;
            min-width: 300px;
            z-index: 1000;
            animation: slideIn 0.3s ease-out;
        }

        .inventory-panel {
            position: fixed;
            top: 20px;
            left: 20px;
            background: rgba(30, 30, 30, 0.95);
            border-radius: 10px;
            padding: 20px;
            border: 2px solid #ffd700;
            min-width: 300px;
            max-height: 500px;
            overflow-y: auto;
            z-index: 1000;
            animation: slideIn 0.3s ease-out;
        }

        .inventory-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 8px;
            margin: 5px 0;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .inventory-item img {
            width: 40px;
            height: 40px;
            object-fit: contain;
            border-radius: 5px;
        }

        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .login-card {
            background: rgba(30, 30, 30, 0.95);
            border-radius: 15px;
            padding: 40px;
            border: 2px solid #ffd700;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            min-width: 400px;
            text-align: center;
        }

        .tab-buttons {
            display: flex;
            margin-bottom: 20px;
            border-radius: 8px;
            overflow: hidden;
        }

        .tab-btn {
            flex: 1;
            padding: 12px;
            background: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .tab-btn.active {
            background: #ff6b35;
        }

        .hidden {
            display: none !important;
        }

        .cooldown-timer {
            color: #ffd700;
            font-weight: bold;
            font-size: 1.2em;
            text-shadow: 0 0 10px #ffd700;
        }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(0, 0, 0, 0.8);
            padding: 15px 25px;
            border-radius: 10px;
            margin-bottom: 20px;
            border: 2px solid #ffd700;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: 2px solid #ffd700;
        }

        .controls {
            display: flex;
            gap: 10px;
        }
    </style>
</head>
<body>
    <div class="overlay">
        <!-- Login/Signup Screen -->
        <div id="loginScreen" class="login-container">
            <div class="login-card">
                <div class="header">
                    <h1>🏴‍☠️ Blox Fruits</h1>
                    <p>Join the adventure!</p>
                </div>
                
                <div class="tab-buttons">
                    <button class="tab-btn active" onclick="switchTab('login')">Login</button>
                    <button class="tab-btn" onclick="switchTab('signup')">Sign Up</button>
                </div>

                <!-- Login Form -->
                <div id="loginForm">
                    <input type="text" id="loginUsername" class="input" placeholder="Username" />
                    <input type="password" id="loginPassword" class="input" placeholder="Password" />
                    <button class="btn" onclick="handleLogin()" style="width: 100%; margin-top: 20px;">
                        🚀 Login
                    </button>
                </div>

                <!-- Signup Form -->
                <div id="signupForm" class="hidden">
                    <input type="text" id="signupUsername" class="input" placeholder="Choose Username" />
                    <input type="password" id="signupPassword" class="input" placeholder="Choose Password" />
                    <input type="url" id="signupAvatar" class="input" placeholder="Profile Image URL (optional)" />
                    <button class="btn" onclick="handleSignup()" style="width: 100%; margin-top: 20px;">
                        ⭐ Create Account
                    </button>
                </div>
            </div>
        </div>

        <!-- Main App -->
        <div id="mainApp" class="hidden">
            <div class="container">
                <!-- Top Bar -->
                <div class="top-bar">
                    <div class="user-info">
                        <img id="userAvatar" class="avatar" src="/placeholder.svg" alt="Avatar" />
                        <div>
                            <div id="userName" style="font-size: 1.2em; font-weight: bold;"></div>
                            <div style="font-size: 0.9em; opacity: 0.8;">Pirate Captain</div>
                        </div>
                    </div>
                    <div class="controls">
                        <button class="btn" onclick="toggleInventory()">📦 Inventory</button>
                        <button class="btn" onclick="toggleSettings()">⚙️ Settings</button>
                        <button class="btn" onclick="logout()" style="background: #dc3545;">🚪 Logout</button>
                    </div>
                </div>

                <!-- Stats Bar -->
                <div class="stats-bar">
                    <div class="stat">
                        <div>💰 Money</div>
                        <div id="userMoney">$1000</div>
                    </div>
                    <div class="stat">
                        <div>📦 Fruits</div>
                        <div id="fruitCount">0</div>
                    </div>
                    <div class="stat">
                        <div>⏰ Next Find</div>
                        <div id="cooldownTimer" class="cooldown-timer">Ready!</div>
                    </div>
                    <div class="stat">
                        <div>🔧 Upgrades</div>
                        <div id="upgradeLevel">0/0</div>
                    </div>
                </div>

                <!-- Main Chat -->
                <div class="card">
                    <h2 style="color: #ffd700; margin-bottom: 20px;">💬 Blox Fruits Chat</h2>
                    <div id="chatContainer" class="chat-container"></div>
                    <div class="chat-input-container">
                        <input type="text" id="chatInput" class="input chat-input" 
                               placeholder="Type a message or use /find, /sell, /itembox, /market, /help..." 
                               onkeypress="handleKeyPress(event)" />
                        <button class="btn" onclick="sendMessage()">📤 Send</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Settings Panel -->
        <div id="settingsPanel" class="settings-panel hidden">
            <h3 style="color: #ffd700; margin-bottom: 15px;">⚙️ Settings</h3>
            <label style="display: block; margin: 10px 0; color: #ffd700;">Username:</label>
            <input type="text" id="settingsUsername" class="input" />
            
            <label style="display: block; margin: 10px 0; color: #ffd700;">Profile Image URL:</label>
            <input type="url" id="settingsAvatar" class="input" />
            
            <label style="display: block; margin: 10px 0; color: #ffd700;">Discord Webhook:</label>
            <textarea id="settingsWebhook" class="input" style="height: 80px; resize: vertical;"></textarea>
            
            <div style="margin-top: 20px;">
                <button class="btn" onclick="saveSettings()" style="width: 100%;">💾 Save Settings</button>
                <button class="btn" onclick="toggleSettings()" style="width: 100%; margin-top: 10px; background: #6c757d;">❌ Close</button>
            </div>
        </div>

        <!-- Inventory Panel -->
        <div id="inventoryPanel" class="inventory-panel hidden">
            <h3 style="color: #ffd700; margin-bottom: 15px;">📦 Inventory</h3>
            <div id="inventoryList"></div>
            <button class="btn" onclick="toggleInventory()" style="width: 100%; margin-top: 15px; background: #6c757d;">❌ Close</button>
        </div>
    </div>

    <script>
        // Default webhook URL
        const DEFAULT_WEBHOOK = "https://discord.com/api/webhooks/1413988785825386607/Hi8_4b7FgtjHpkkCYQxxJ1bLv5BD3cm6Ga-HM0K1chJk6t9xRCSVqGE924wA6hTnWFm6";
        
        // Fruit data with images and chances
        const BLOX_FRUITS = [
            {
                name: "Light Fruit",
                chance: 78,
                imageUrl: "https://tse2.mm.bing.net/th/id/OIP.n5bP5cCxdCXuSNdi8ctkvwAAAA?cb=thfvnext&rs=1&pid=ImgDetMain&o=7&rm=3",
                sellPrice: 500,
            },
            {
                name: "Rocket",
                chance: 65,
                imageUrl: "https://img.bloxfruitcalculator.org/fruits/RocketFruit.png",
                sellPrice: 300,
            },
            {
                name: "Ice Fruit",
                chance: 62,
                imageUrl: "https://img.bloxfruitcalculator.org/fruits/IceFruit.png",
                sellPrice: 400,
            },
            {
                name: "Ghost Fruit",
                chance: 54,
                imageUrl: "https://tse3.mm.bing.net/th/id/OIP.G7ZOgLOlUOnPAmGaXJMhoAAAAA?cb=thfvnext&rs=1&pid=ImgDetMain&o=7&rm=3",
                sellPrice: 800,
            },
            {
                name: "Venom Fruit",
                chance: 31,
                imageUrl: "https://cdn3.emoji.gg/emojis/2148-venomfruit.png",
                sellPrice: 1500,
            },
        ];

        // Global state
        let currentUser = null;
        let gameState = {
            inventory: [],
            money: 1000,
            lastFindTime: null,
            fruitTimeUpgrade: 0,
            rareChanceUpgrade: 0,
            webhook: DEFAULT_WEBHOOK
        };
        let cooldownInterval = null;

        // Initialize app
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
            startCooldownTimer();
        });

        function initializeApp() {
            const savedUser = localStorage.getItem('currentBloxFruitsUser');
            const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
            
            // Only show main app if user exists and is valid
            if (savedUser && accounts[savedUser]) {
                currentUser = savedUser;
                gameState = { ...gameState, ...accounts[savedUser].gameState };
                showMainApp();
            } else {
                // Always start with login screen for new users
                showLoginScreen();
                // Clear any invalid saved data
                localStorage.removeItem('currentBloxFruitsUser');
            }
        }

        function switchTab(tab) {
            const loginForm = document.getElementById('loginForm');
            const signupForm = document.getElementById('signupForm');
            const tabBtns = document.querySelectorAll('.tab-btn');
            
            tabBtns.forEach(btn => btn.classList.remove('active'));
            
            if (tab === 'login') {
                loginForm.classList.remove('hidden');
                signupForm.classList.add('hidden');
                tabBtns[0].classList.add('active');
            } else {
                loginForm.classList.add('hidden');
                signupForm.classList.remove('hidden');
                tabBtns[1].classList.add('active');
            }
        }

        function handleLogin() {
            const username = document.getElementById('loginUsername').value.trim();
            const password = document.getElementById('loginPassword').value.trim();
            
            if (!username || !password) {
                alert('Please enter both username and password!');
                return;
            }

            // Get stored accounts
            const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
            
            if (accounts[username] && accounts[username].password === password) {
                currentUser = username;
                gameState = { ...gameState, ...accounts[username].gameState };
                localStorage.setItem('currentBloxFruitsUser', username);
                showMainApp();
            } else {
                alert('Invalid username or password!');
            }
        }

        function handleSignup() {
            const username = document.getElementById('signupUsername').value.trim();
            const password = document.getElementById('signupPassword').value.trim();
            const avatar = document.getElementById('signupAvatar').value.trim();
            
            if (!username || !password) {
                alert('Please enter both username and password!');
                return;
            }

            // Get stored accounts
            const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
            
            if (accounts[username]) {
                alert('Username already exists! Please choose a different one.');
                return;
            }

            // Create new account
            accounts[username] = {
                password: password,
                avatar: avatar || `https://api.dicebear.com/7.x/avataaars/svg?seed=${username}`,
                gameState: {
                    inventory: [],
                    money: 1000,
                    lastFindTime: null,
                    fruitTimeUpgrade: 0,
                    rareChanceUpgrade: 0,
                    webhook: DEFAULT_WEBHOOK
                }
            };

            localStorage.setItem('bloxFruitsAccounts', JSON.stringify(accounts));
            
            currentUser = username;
            gameState = accounts[username].gameState;
            localStorage.setItem('currentBloxFruitsUser', username);
            showMainApp();
        }

        function showLoginScreen() {
            document.getElementById('loginScreen').classList.remove('hidden');
            document.getElementById('mainApp').classList.add('hidden');
            document.getElementById('loginUsername').value = '';
            document.getElementById('loginPassword').value = '';
            document.getElementById('signupUsername').value = '';
            document.getElementById('signupPassword').value = '';
            document.getElementById('signupAvatar').value = '';
        }

        function logout() {
            localStorage.removeItem('currentBloxFruitsUser');
            currentUser = null;
            gameState = {
                inventory: [],
                money: 1000,
                lastFindTime: null,
                fruitTimeUpgrade: 0,
                rareChanceUpgrade: 0,
                webhook: DEFAULT_WEBHOOK
            };
            showLoginScreen();
        }

        function saveGameState() {
            if (!currentUser) return;
            
            const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
            if (accounts[currentUser]) {
                accounts[currentUser].gameState = gameState;
                localStorage.setItem('bloxFruitsAccounts', JSON.stringify(accounts));
            }
        }

        function updateUI() {
            document.getElementById('userMoney').textContent = `$${gameState.money}`;
            document.getElementById('fruitCount').textContent = gameState.inventory.length;
            document.getElementById('upgradeLevel').textContent = `${gameState.fruitTimeUpgrade}/${gameState.rareChanceUpgrade}`;
            updateInventoryPanel();
        }

        function updateInventoryPanel() {
            const inventoryList = document.getElementById('inventoryList');
            
            if (gameState.inventory.length === 0) {
                inventoryList.innerHTML = '<p style="color: #ccc; text-align: center;">No fruits collected yet!</p>';
                return;
            }

            inventoryList.innerHTML = gameState.inventory.map((fruit, index) => `
                <div class="inventory-item">
                    <img src="${fruit.imageUrl}" alt="${fruit.name}" />
                    <div style="flex: 1;">
                        <div style="font-weight: bold;">${fruit.name}</div>
                        <div style="font-size: 0.9em; opacity: 0.8;">$${fruit.sellPrice} • ${fruit.chance}%</div>
                    </div>
                </div>
            `).join('');
        }

        function toggleSettings() {
            const panel = document.getElementById('settingsPanel');
            panel.classList.toggle('hidden');
        }

        function toggleInventory() {
            const panel = document.getElementById('inventoryPanel');
            panel.classList.toggle('hidden');
        }

        function saveSettings() {
            const newUsername = document.getElementById('settingsUsername').value.trim();
            const newAvatar = document.getElementById('settingsAvatar').value.trim();
            const newWebhook = document.getElementById('settingsWebhook').value.trim();
            
            if (!newUsername) {
                alert('Username cannot be empty!');
                return;
            }

            // Update user data
            const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
            
            if (newUsername !== currentUser) {
                // Username changed - move account data
                if (accounts[newUsername]) {
                    alert('Username already exists!');
                    return;
                }
                accounts[newUsername] = accounts[currentUser];
                delete accounts[currentUser];
                currentUser = newUsername;
                localStorage.setItem('currentBloxFruitsUser', newUsername);
            }

            accounts[currentUser].avatar = newAvatar || accounts[currentUser].avatar;
            gameState.webhook = newWebhook || DEFAULT_WEBHOOK;
            accounts[currentUser].gameState = gameState;
            
            localStorage.setItem('bloxFruitsAccounts', JSON.stringify(accounts));
            
            // Update UI
            document.getElementById('userName').textContent = currentUser;
            document.getElementById('userAvatar').src = accounts[currentUser].avatar;
            
            toggleSettings();
            addMessage('system', '⚙️ Settings saved successfully!');
        }

        function handleKeyPress(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        }

        function sendMessage() {
            const input = document.getElementById('chatInput');
            const message = input.value.trim();
            
            if (!message) return;

            addMessage('user', message);
            input.value = '';

            // Handle commands
            if (message.startsWith('/find')) {
                handleFindCommand();
            } else if (message.startsWith('/sell')) {
                handleSellCommand();
            } else if (message.startsWith('/itembox')) {
                handleItemBoxCommand();
            } else if (message.startsWith('/market')) {
                handleMarketCommand();
            } else if (message.startsWith('/help')) {
                handleHelpCommand();
            } else {
                // Send regular message to Discord
                sendToDiscord(message);
                setTimeout(() => {
                    addMessage('system', 'Message sent to Discord! 📨');
                }, 500);
            }
        }

        function addMessage(type, content, imageUrl = null) {
            const chatContainer = document.getElementById('chatContainer');
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${type}`;
            
            if (imageUrl && type === 'fruit') {
                messageDiv.innerHTML = `
                    <img src="${imageUrl}" alt="Fruit" class="fruit-image" />
                    <div>
                        <div>${content}</div>
                        <div style="font-size: 0.8em; opacity: 0.7; margin-top: 5px;">${new Date().toLocaleTimeString()}</div>
                    </div>
                `;
            } else {
                messageDiv.innerHTML = `
                    <div>${content}</div>
                    <div style="font-size: 0.8em; opacity: 0.7; margin-top: 5px;">${new Date().toLocaleTimeString()}</div>
                `;
            }
            
            chatContainer.appendChild(messageDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        function handleFindCommand() {
            const now = new Date();
            const baseCooldown = 12;
            const actualCooldown = Math.max(1, baseCooldown - gameState.fruitTimeUpgrade);

            // Check cooldown
            if (gameState.lastFindTime) {
                const timeDiff = now.getTime() - new Date(gameState.lastFindTime).getTime();
                const minutesPassed = timeDiff / (1000 * 60);

                if (minutesPassed < actualCooldown) {
                    const remainingMinutes = Math.ceil(actualCooldown - minutesPassed);
                    addMessage('system', `⏰ You must wait ${remainingMinutes} more minutes before using /find again!`);
                    
                    // Send to Discord anyway
                    sendToDiscord(`⏰ Tried to use /find but ${remainingMinutes} minutes remaining on cooldown!`);
                    return;
                }
            }

            // Set new find time
            gameState.lastFindTime = now.toISOString();
            saveGameState();

            const random = Math.random() * 100;
            let foundFruit = null;

            const modifiedFruits = BLOX_FRUITS.map(fruit => ({
                ...fruit,
                chance: fruit.chance < 50 ? Math.min(95, fruit.chance + gameState.rareChanceUpgrade * 5) : fruit.chance,
            }));

            // Sort fruits by chance (highest first) and check if we hit any
            const sortedFruits = [...modifiedFruits].sort((a, b) => b.chance - a.chance);

            for (const fruit of sortedFruits) {
                if (random <= fruit.chance) {
                    foundFruit = fruit;
                    break;
                }
            }

            if (foundFruit) {
                // Add to inventory
                gameState.inventory.push(foundFruit);
                saveGameState();
                updateUI();

                const embed = {
                    title: "🎊 Fruit Found!",
                    description: `**${foundFruit.name}**\nChance: ${foundFruit.chance}%\nSell Price: $${foundFruit.sellPrice}`,
                    image: { url: foundFruit.imageUrl },
                    color: 0x00ff00,
                    timestamp: new Date().toISOString(),
                };

                sendToDiscord("", embed);
                addMessage('fruit', `🎊 You found a ${foundFruit.name}! (${foundFruit.chance}% chance)\nSell Price: $${foundFruit.sellPrice}`, foundFruit.imageUrl);
            } else {
                addMessage('system', `🔍 You searched but found nothing this time. Better luck next time!`);
                sendToDiscord("🔍 Searched for fruits but found nothing this time!");
            }
        }

        function handleSellCommand() {
            if (gameState.inventory.length === 0) {
                const message = `📦 Your inventory is empty! Use /find to collect fruits first.`;
                addMessage('system', message);
                sendToDiscord(message);
                return;
            }

            if (gameState.inventory.length === 1) {
                // Auto-sell if only one fruit
                const fruit = gameState.inventory[0];
                gameState.money += fruit.sellPrice;
                gameState.inventory = [];
                saveGameState();
                updateUI();

                const message = `💰 Sold ${fruit.name} for $${fruit.sellPrice}! Total money: $${gameState.money}`;
                addMessage('system', message);
                sendToDiscord(message);
            } else {
                // Show inventory for selection
                const inventoryList = gameState.inventory
                    .map((fruit, index) => `${index + 1}. ${fruit.name} (${fruit.chance}% chance) - $${fruit.sellPrice}`)
                    .join('\n');

                const message = `📦 Your Inventory:\n${inventoryList}\n\nType "/sell [number]" to sell a specific fruit (e.g., "/sell 1")`;
                addMessage('system', message);
                sendToDiscord(message);
            }
        }

        function handleItemBoxCommand() {
            if (gameState.inventory.length === 0) {
                const message = `📦 Your ItemBox is empty! Use /find to collect fruits.`;
                addMessage('system', message);
                sendToDiscord(message);
                return;
            }

            const inventoryList = gameState.inventory
                .map((fruit, index) => `${index + 1}. ${fruit.name} (${fruit.chance}% chance) - Sell: $${fruit.sellPrice}`)
                .join('\n');

            const message = `📦 Your ItemBox (${gameState.inventory.length} fruits):\n${inventoryList}`;
            addMessage('system', message);
            sendToDiscord(message);
        }

        function handleMarketCommand() {
            const upgradesSection = `🔧 UPGRADES:
1. Fruit Time Upgrade (Level ${gameState.fruitTimeUpgrade}) - $${(gameState.fruitTimeUpgrade + 1) * 500}
   Reduces /find cooldown by 1 minute per level
   
2. Rare Chance Upgrade (Level ${gameState.rareChanceUpgrade}) - $${(gameState.rareChanceUpgrade + 1) * 1000}
   Increases rare fruit chances by 5% per level`;

            const fruitsSection = `🍎 FRUITS FOR SALE:
${BLOX_FRUITS.map(fruit => `${fruit.name} - $${fruit.sellPrice * 2}`).join('\n')}

💰 Your Money: $${gameState.money}

Type "/buy upgrade [1-2]" for upgrades or "/buy fruit [name]" for fruits!`;

            const message = `🏪 MARKET\n\n${upgradesSection}\n\n${fruitsSection}`;
            addMessage('system', message);
            sendToDiscord(message);
        }

        function handleHelpCommand() {
            const message = `📋 Available commands:
/find - Search for fruits (12 min cooldown)
/sell - Sell your fruits
/itembox - View your fruit collection
/market - Buy upgrades and fruits
/help - Show this help

🎮 Regular messages are sent to Discord!`;
            addMessage('system', message);
            sendToDiscord(message);
        }

        async function sendToDiscord(message, embed = null) {
            if (!gameState.webhook) return;

            try {
                const accounts = JSON.parse(localStorage.getItem('bloxFruitsAccounts') || '{}');
                const userData = accounts[currentUser];
                
                const payload = {
                    username: currentUser,
                    avatar_url: userData.avatar,
                };

                if (embed) {
                    payload.embeds = [embed];
                } else {
                    payload.content = message;
                }

                await fetch(gameState.webhook, {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify(payload),
                });
            } catch (error) {
                console.error("Failed to send to Discord:", error);
            }
        }

        function startCooldownTimer() {
            cooldownInterval = setInterval(updateCooldownTimer, 1000);
        }

        function updateCooldownTimer() {
            if (!gameState.lastFindTime) {
                document.getElementById('cooldownTimer').textContent = 'Ready!';
                return;
            }

            const now = new Date();
            const actualCooldown = Math.max(1, 12 - gameState.fruitTimeUpgrade);
            const nextFindTime = new Date(new Date(gameState.lastFindTime).getTime() + actualCooldown * 60 * 1000);
            const diff = nextFindTime.getTime() - now.getTime();

            if (diff <= 0) {
                document.getElementById('cooldownTimer').textContent = 'Ready!';
                return;
            }

            const minutes = Math.floor(diff / (1000 * 60));
            const seconds = Math.floor((diff % (1000 * 60)) / 1000);
            document.getElementById('cooldownTimer').textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }
    </script>
</body>
</html>
