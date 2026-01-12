<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Modern World</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #0b0b0b;
      color: #ffffff;
    }
    header {
      background: #151515;
      padding: 18px;
      text-align: center;
      font-size: 30px;
      font-weight: bold;
      letter-spacing: 1px;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 15px;
      background: #1f1f1f;
      padding: 10px;
      flex-wrap: wrap;
    }
    nav button {
      background: #00bfff;
      border: none;
      padding: 10px 18px;
      border-radius: 8px;
      font-weight: bold;
      cursor: pointer;
    }
    .search {
      width: 100%;
      max-width: 420px;
      margin: 15px auto;
      display: block;
      padding: 10px;
      border-radius: 8px;
      border: none;
      font-size: 16px;
    }
    .section {
      display: none;
      padding: 20px;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 20px;
    }
    .card {
      background: #1b1b1b;
      padding: 20px;
      border-radius: 14px;
      text-align: center;
      cursor: pointer;
      transition: transform 0.2s, background 0.2s;
      font-weight: bold;
    }
    .card:hover {
      transform: scale(1.05);
      background: #262626;
    }
    iframe {
      width: 100%;
      height: 540px;
      border: none;
      border-radius: 14px;
    }
    .back {
      margin-top: 15px;
      background: #ff4444;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    .note {
      text-align: center;
      opacity: 0.7;
      margin-top: 10px;
      font-size: 14px;
    }
    .lock {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: #0b0b0b;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      z-index: 999;
    }
    .lock input {
      padding: 10px;
      border-radius: 8px;
      border: none;
      margin-top: 10px;
    }
  </style>
</head>
<body>

<div class="lock" id="lock">
  <h2>🔒 Enter Password</h2>
  <input type="password" id="pass" placeholder="Password" />
  <button onclick="unlock()">Enter</button>
</div>

<header>🌍 Modern World</header>

<nav>
  <button onclick="showSection('games')">Games</button>
  <button onclick="showSection('movies')">Movies</button>
  <button onclick="showSection('school')">School</button>
</nav>

<input class="search" id="search" placeholder="Search games or movies..." onkeyup="filterCards()" />

<div id="games" class="section">
  <h2>🎮 Games</h2>
  <div class="grid">
    <div class="card" onclick="openMedia('https://emulatorgames.online/embed/snake')">Snake</div>
    <div class="card" onclick="openMedia('https://emulatorgames.online/embed/tetris')">Tetris</div>
    <div class="card" onclick="openMedia('https://ubg77.github.io/game131/run3/')">Run 3</div>
    <div class="card" onclick="openMedia('https://ubg77.github.io/game131/slope/')">Slope</div>
    <div class="card" onclick="openMedia('https://ubg77.github.io/game131/retro-bowl/')">Retro Bowl</div>
    <div class="card" onclick="openMedia('https://ubg77.github.io/game131/basketball-stars/')">Basketball Stars</div>
  </div>
</div>

<div id="movies" class="section">
  <h2>🎬 Movies</h2>
  <div class="grid">
    <div class="card" onclick="openMedia('https://archive.org/embed/bigbuckbunny')">Big Buck Bunny</div>
    <div class="card" onclick="openMedia('https://archive.org/embed/sintel')">Sintel</div>
    <div class="card" onclick="openMedia('https://archive.org/embed/tears_of_steel')">Tears of Steel</div>
  </div>
  <p class="note">Movies are free & legal (Archive.org)</p>
</div>

<div id="school" class="section">
  <h2>📚 School Mode</h2>
  <ul>
    <li>Math practice worksheets</li>
    <li>Typing lessons</li>
    <li>Study timers</li>
    <li>Educational resources</li>
  </ul>
</div>

<div id="player" class="section">
  <iframe id="frame" allowfullscreen></iframe>
  <br>
  <button class="back" onclick="goBack()">⬅ Back</button>
</div>

<script>
  const PASSWORD = "1234"; // change this

  function unlock() {
    if (document.getElementById('pass').value === PASSWORD) {
      document.getElementById('lock').style.display = 'none';
    }
  }

  function showSection(id) {
    document.querySelectorAll('.section').forEach(s => s.style.display = 'none');
    document.getElementById(id).style.display = 'block';
  }

  function openMedia(url) {
    document.getElementById('frame').src = url;
    showSection('player');
  }

  function goBack() {
    document.getElementById('frame').src = '';
    showSection('games');
  }

  function filterCards() {
    const value = document.getElementById('search').value.toLowerCase();
    document.querySelectorAll('.card').forEach(card => {
      card.style.display = card.textContent.toLowerCase().includes(value) ? 'block' : 'none';
    });
  }

  showSection('games');
</script>

</body>
</html>
