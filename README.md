<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="theme-color" content="#ffffff" />
  <link rel="manifest" href="manifest.json" />
  <title>LuxFit - Wellness Reimagined</title>
  <style>
    :root {
      --bg-light: #fefefe;
      --bg-dark: #121212;
      --text-light: #121212;
      --text-dark: #ffffff;
      --primary: #7d5fff;
      --secondary: #f7f1ff;
    }
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: var(--bg-light);
      color: var(--text-light);
      transition: background 0.3s, color 0.3s;
    }
    .dark-mode {
      background-color: var(--bg-dark);
      color: var(--text-dark);
    }
    header {
      display: flex;
      justify-content: space-between;
      padding: 1rem;
      background: var(--primary);
      color: white;
    }
    .container {
      padding: 1rem;
    }
    .btn {
      padding: 0.5rem 1rem;
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
    }
    .chatbox, .profile-section {
      margin-top: 1rem;
      padding: 1rem;
      border: 1px solid #ccc;
      border-radius: 1rem;
      background: var(--secondary);
    }
  </style>
</head>
<body>
  <header>
    <h1>LuxFit</h1>
    <button onclick="toggleDarkMode()">Dark Mode</button>
  </header>
  <div class="container">
    <div class="profile-section">
      <h2>Your Profile</h2>
      <input type="text" placeholder="Name" id="name" />
      <input type="date" id="dob" />
      <textarea placeholder="Write a short bio..." id="bio"></textarea>
      <button class="btn" onclick="saveProfile()">Save Profile</button>
    </div><div class="chatbox">
  <h2>AI Chat Assistant</h2>
  <input type="text" id="userInput" placeholder="Ask me anything..." />
  <button onclick="chatWithAI()">Send</button>
  <div id="chatOutput"></div>
</div>

<div>
  <h2>Daily Sneak Peek</h2>
  <p id="dailyTip">Loading tip...</p>
</div>

<div>
  <h2>Points: <span id="points">0</span></h2>
  <button class="btn" onclick="gainPoints()">Complete Task</button>
</div>

  </div>  <script>
    // Dark Mode
    function toggleDarkMode() {
      document.body.classList.toggle('dark-mode');
    }

    // Profile Storage
    function saveProfile() {
      const name = document.getElementById('name').value;
      const dob = document.getElementById('dob').value;
      const bio = document.getElementById('bio').value;
      const profile = { name, dob, bio };
      localStorage.setItem('luxfit_profile', JSON.stringify(profile));
      alert('Profile Saved');
    }

    // AI Chatbot Simulation
    function chatWithAI() {
      const input = document.getElementById('userInput').value;
      const response = `You said: "${input}". Stay positive and take a deep breath.`;
      document.getElementById('chatOutput').innerText = response;
    }

    // Daily Tips
    const tips = [
      'Drink 8 glasses of water.',
      'Take a 10-minute walk.',
      'Write down what you’re grateful for.',
      'Do one good thing for yourself today.',
      'Smile—it boosts your mood!'
    ];
    document.getElementById('dailyTip').innerText = tips[Math.floor(Math.random() * tips.length)];

    // Points System
    let points = parseInt(localStorage.getItem('luxfit_points') || '0');
    function gainPoints() {
      points += 10;
      localStorage.setItem('luxfit_points', points);
      document.getElementById('points').innerText = points;
    }
    document.getElementById('points').innerText = points;
  </script></body>
</html>
