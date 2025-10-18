<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>AI Goal Journal</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg-gradient: linear-gradient(135deg, #1e3c72, #2a5298);
      --card-bg: rgba(255,255,255,0.05);
      --accent: #06b6d4;
      --text-light: #e6eef6;
      --text-muted: #94a3b8;
      --button-bg: #06b6d4;
      --button-text: #04212a;
    }

    * { box-sizing: border-box; font-family: 'Inter', sans-serif; }
    body { margin:0; padding:0; background: var(--bg-gradient); color: var(--text-light); }
    header { text-align: center; padding: 2rem 1rem; background: rgba(0,0,0,0.2); backdrop-filter: blur(10px); border-bottom: 1px solid rgba(255,255,255,0.1); }
    header h1 { margin:0; font-size: 1.8rem; font-weight:700; }
    .container { max-width: 500px; margin: 2rem auto; padding:1rem; }

    .page { display: none; background: var(--card-bg); padding: 1.5rem; border-radius: 16px; margin-bottom: 2rem; box-shadow: 0 10px 25px rgba(0,0,0,0.4); }
    .active { display: block; }
    h2 { margin-top:0; margin-bottom:1rem; font-weight:600; }
    label { display:block; margin-top:1rem; font-weight:500; color: var(--text-muted); }
    input, textarea, select { width:100%; padding:0.8rem; margin-top:0.5rem; border-radius:12px; border:none; background: rgba(255,255,255,0.1); color: var(--text-light); font-size:1rem; }
    textarea { min-height:100px; resize: vertical; }
    button { width:100%; padding:1rem; margin-top:1.5rem; border:none; border-radius:12px; font-size:1rem; font-weight:600; cursor:pointer; background: var(--button-bg); color: var(--button-text); transition: transform 0.2s ease; }
    button:hover { transform: scale(1.03); }

    .score-box { background: rgba(255,255,255,0.05); padding:1rem; border-radius:12px; margin-top:1rem; }
    .wallet { background: rgba(255,255,255,0.1); padding:1rem; border-radius:12px; margin-top:1rem; }

    /* Mobile Responsive */
    @media (max-width: 480px) {
      .container { margin:1rem; padding:1rem; }
      header h1 { font-size:1.5rem; }
    }
  </style>
</head>
<body>
  <header>
    <h1>AI Goal Journal</h1>
    <p style="color: var(--text-muted); font-size:0.9rem;">Track your goals, daily progress, and rewards.</p>
  </header>

  <div class="container">
    <div id="goalPage" class="page active">
      <h2>Step 1: Define Your Goal</h2>
      <label>Main Goal</label>
      <input type="text" id="goalInput" placeholder="e.g. Build a personal brand in 90 days" />
      <label>Current Situation</label>
      <textarea id="situationInput" placeholder="Describe your current situation"></textarea>
      <label>Daily Available Time (hours)</label>
      <input type="number" id="timeInput" min="1" max="12" />
      <button onclick="nextPage('planPage')">Next →</button>
    </div>

    <div id="planPage" class="page">
      <h2>Step 2: AI Goal Plan</h2>
      <div class="score-box">
        <p><strong>AI Plan:</strong></p>
        <ul>
          <li>Estimated time frame: 90 days</li>
          <li>Daily actions: Reflect, Execute, Track</li>
          <li>Micro-milestones set automatically by AI</li>
        </ul>
      </div>
      <button onclick="nextPage('walletPage')">Next →</button>
    </div>

    <div id="walletPage" class="page">
      <h2>Step 3: Wallet / Deposit</h2>
      <label>Choose Deposit Plan</label>
      <select id="walletSelect">
        <option value="1000">₹1000/mo</option>
        <option value="2000">₹2000/mo</option>
        <option value="5000">₹5000/mo</option>
      </select>
      <div class="wallet" id="walletBalance">Wallet Balance: ₹0</div>
      <button onclick="joinWallet()">Join Wallet</button>
      <button onclick="nextPage('journalPage')">Next →</button>
    </div>

    <div id="journalPage" class="page">
      <h2>Step 4: Daily Journal</h2>
      <textarea id="journalInput" placeholder="Write your reflection here..."></textarea>
      <button onclick="analyzeJournal()">Analyze (Dummy AI)</button>
      <div id="analysisResult" class="score-box"></div>
      <button onclick="nextPage('summaryPage')">Next →</button>
    </div>

    <div id="summaryPage" class="page">
      <h2>Step 5: Summary</h2>
      <div class="score-box">
        <p>Streak: <span id="streakCount">0</span> days</p>
        <p>Total Reward Earned: ₹<span id="rewardEarned">0</span></p>
      </div>
      <button onclick="restart()">Start New Goal</button>
    </div>
  </div>

  <script>
    let currentPage = 'goalPage';
    let streak = 0;
    let reward = 0;
    let wallet = 0;

    function nextPage(pageId) {
      document.getElementById(currentPage).classList.remove('active');
      document.getElementById(pageId).classList.add('active');
      currentPage = pageId;
    }

    function joinWallet() {
      const amt = parseInt(document.getElementById('walletSelect').value);
      wallet += amt;
      document.getElementById('walletBalance').innerText = `Wallet Balance: ₹${wallet}`;
      alert('Wallet joined with ₹' + amt);
    }

    function analyzeJournal() {
      const entry = document.getElementById('journalInput').value.trim();
      if (!entry) { alert('Please write something'); return; }
      const focus = Math.floor(Math.random() * 10) + 1;
      const consistency = Math.floor(Math.random() * 10) + 1;
      const energy = Math.floor(Math.random() * 10) + 1;
      streak++;
      const rewardToday = 10;
      reward += rewardToday;
      document.getElementById('analysisResult').innerHTML = `
        <p>Focus: ${focus}/10</p>
        <p>Consistency: ${consistency}/10</p>
        <p>Energy: ${energy}/10</p>
        <p>Verdict: On Track ✅</p>
        <p>Reward Earned Today: ₹${rewardToday}</p>
      `;
      document.getElementById('streakCount').innerText = streak;
      document.getElementById('rewardEarned').innerText = reward;
    }

    function restart() { location.reload(); }
  </script>
</body>
</html>
