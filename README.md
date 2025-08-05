<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PAWBOT 🐾</title>
  <link href="https://fonts.googleapis.com/css2?family=Baguet+Script&display=swap" rel="stylesheet">
  <style>
    body {
      background-color: #e8d4b0;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    .scroll-text {
      width: 100%;
      overflow: hidden;
      background-color: transparent;
      border-bottom: 2px dashed #d3a2ff;
      padding: 10px 0;
    }

    .scroll-text h1 {
      font-family: 'Baguet Script', cursive;
      font-size: 48px;
      white-space: nowrap;
      color: #7a4ea3;
      animation: scroll-left 12s linear infinite;
    }

    @keyframes scroll-left {
      0% { transform: translateX(100%); }
      100% { transform: translateX(-100%); }
    }

    .description {
      background-color: #fef6e4;
      border: 3px dashed #d3a2ff;
      margin: 20px;
      padding: 15px;
      border-radius: 15px;
      font-size: 18px;
    }

    .container {
      border: 15px solid transparent;
      padding: 20px;
      border-image: url('https://i.ibb.co/xSNPSFZ/paw-border.png') 30 round;
    }

    .buttons {
      text-align: center;
      margin: 30px 0;
    }

    button {
      background-color: #d3a2ff;
      border: none;
      color: white;
      padding: 15px 25px;
      margin: 10px;
      font-size: 18px;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.05);
      background-color: #c48cf7;
    }

    .content-box {
      display: none;
      margin: 20px auto;
      width: 80%;
      background-color: #fffaf2;
      border: 2px dashed #d3a2ff;
      padding: 20px;
      border-radius: 15px;
    }

    .cctv {
      text-align: center;
      margin-top: 30px;
    }

    .cctv img {
      max-width: 90%;
      border-radius: 15px;
      border: 3px dashed #d3a2ff;
    }
  </style>
</head>
<body>

  <div class="scroll-text">
    <h1>— PAWBOT —</h1>
  </div>

  <!-- Product Description now at the top below heading -->
  <div class="description">
    <h2>About the Product 🐶</h2>
    <p>
      PAWBOT is a smart pet feeding assistant that helps you feed your pets and ensure they stay hydrated — all through this website! 
      With just a click, you can set food or water timers, choose what to feed, and even watch your pet via live camera. 
      It's perfect for busy pet parents who want to care from anywhere. 🐾
    </p>
  </div>

  <div class="container">
    <div class="buttons">
      <button onclick="showSection('timer')">⏰ Timer</button>
      <button onclick="showSection('mode')">🍽️ Mode of Feeding</button>
      <button onclick="showSection('camera')">📷 Camera</button>
    </div>

    <div id="timer" class="content-box">
      <h2>⏱️ Set Timer</h2>
      <label for="time">Choose Time:</label>
      <input type="time" id="time" />
      <br><br>
      <label for="action">Choose Action:</label>
      <select id="action">
        <option value="food">🍖 Feed Food</option>
        <option value="water">💧 Drink Water</option>
      </select>
      <br><br>
      <button onclick="startTimer()">Start Timer</button>
      <p id="timerOutput"></p>
    </div>

    <div id="mode" class="content-box">
      <h2>Select Feeding Mode 🍽️</h2>
      <button onclick="showFoodMode()">🍗 Food</button>
      <button onclick="showWaterMode()">💧 Water</button>

      <div id="foodMode" style="display:none; margin-top:20px;">
        <label for="foodType">What do you want to feed your pet?</label><br>
        <select id="foodType">
          <option value="Chicken">🍗 Chicken</option>
          <option value="Dry Food">🥣 Dry Food</option>
          <option value="Fish">🐟 Fish</option>
        </select><br><br>
        <label for="amount">Amount (grams):</label>
        <input type="number" id="amount" min="1" /><br><br>
        <button onclick="feedPet()">Feed</button>
        <p id="feedOutput"></p>
      </div>

      <div id="waterMode" style="display:none; margin-top:20px;">
        <p>💧 Your pet is drinking water...</p>
      </div>
    </div>

    <div id="camera" class="content-box">
      <h2>🐾 Live Pet Cam</h2>
      <div class="cctv">
        <img src="https://petcube.com/blog/content/images/2016/12/GIF_cattoy.gif" alt="Pet Camera Feed" />
      </div>
    </div>
  </div>

  <script>
    function showSection(id) {
      document.querySelectorAll('.content-box').forEach(div => div.style.display = 'none');
      document.getElementById(id).style.display = 'block';
    }

    function showFoodMode() {
      document.getElementById('foodMode').style.display = 'block';
      document.getElementById('waterMode').style.display = 'none';
    }

    function showWaterMode() {
      document.getElementById('waterMode').style.display = 'block';
      document.getElementById('foodMode').style.display = 'none';
    }

    function feedPet() {
      const food = document.getElementById('foodType').value;
      const amount = document.getElementById('amount').value;
      document.getElementById('feedOutput').innerText = `🍽️ Feeding your pet ${amount}g of ${food}...`;
    }

    function startTimer() {
      const time = document.getElementById('time').value;
      const action = document.getElementById('action').value;
      const text = action === "food" ? "Feeding your pet" : "Giving water to your pet";
      document.getElementById('timerOutput').innerText = `⏰ Timer set for ${time} - ${text}`;
    }
  </script>
</body>
</html>
