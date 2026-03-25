<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>GameVerse Hub</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #0a0c10;
      color: #e6e6e6;
    }

    /* NAVBAR */
    nav {
      background: #11141b;
      padding: 15px 25px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #222;
    }
    nav .logo {
      font-size: 24px;
      font-weight: bold;
      color: #4cafef;
    }
    nav ul {
      list-style: none;
      display: flex;
      gap: 20px;
      margin: 0;
      padding: 0;
    }
    nav ul li a {
      color: #ccc;
      text-decoration: none;
      font-size: 15px;
      transition: 0.2s;
    }
    nav ul li a:hover {
      color: #4cafef;
    }

    /* HEADER BANNER */
    header {
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(to bottom, #11141b, #0a0c10);
    }
    header h1 {
      margin: 0;
      font-size: 42px;
      color: #4cafef;
    }
    header p {
      margin-top: 10px;
      color: #aaa;
      font-size: 16px;
    }

    /* GAME GRID */
    .container {
      max-width: 1100px;
      margin: 30px auto;
      padding: 0 20px;
    }
    .games-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
      gap: 20px;
    }
    .card {
      background: #11141b;
      border: 1px solid #222;
      border-radius: 10px;
      padding: 15px;
      text-align: center;
      transition: 0.2s;
    }
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 6px 15px rgba(0,0,0,0.4);
    }
    .thumb {
      width: 100%;
      height: 130px;
      background: #1c1f27;
      border-radius: 8px;
      margin-bottom: 12px;
    }
    .card h3 {
      margin: 0;
      color: #4cafef;
      font-size: 18px;
    }
    .card p {
      font-size: 13px;
      color: #bbb;
      min-height: 36px;
    }
    .card a {
      display: inline-block;
      margin-top: 10px;
      padding: 8px 14px;
      border-radius: 6px;
      background: #4cafef;
      color: #0a0c10;
      text-decoration: none;
      font-weight: bold;
      font-size: 14px;
      transition: 0.2s;
    }
    .card a:hover {
      background: #6fd0ff;
    }

    /* MINI GAME */
    canvas {
      background: #11141b;
      border: 2px solid #222;
      display: block;
      margin: 20px auto;
    }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 20px;
      background: #11141b;
      color: #777;
      margin-top: 40px;
      border-top: 1px solid #222;
    }
  </style>
</head>
<body>

<!-- NAVBAR -->
<nav>
  <div class="logo">GameVerse Hub</div>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#games">Games</a></li>
    <li><a href="#about">About</a></li>
  </ul>
</nav>

<!-- HEADER -->
<header>
  <h1>Welcome to GameVerse Hub</h1>
  <p>Your portal for online games, shooters, io games, and built‑in mini games</p>
</header>

<!-- GAME GRID -->
<div class="container" id="games">
  <h2 style="color:#4cafef; text-align:center;">Online Games</h2>
  <div class="games-grid">

    <div class="card">
      <div class="thumb"></div>
      <h3>Repuls.io</h3>
      <p>Fast-paced multiplayer shooter.</p>
      <a href="https://poki.com/en/g/repuls-io" target="_blank">Play</a>
    </div>

    <div class="card">
      <div class="thumb"></div>
      <h3>ShellShock.io</h3>
      <p>Egg battle arena shooter.</p>
      <a href="https://shellshock.io/" target="_blank">Play</a>
    </div>

    <div class="card">
      <div class="thumb"></div>
      <h3>Eggshocker</h3>
      <p>Add the official link here.</p>
      <a href="#" target="_blank">Play</a>
    </div>

    <div class="card">
      <div class="thumb"></div>
      <h3>FNAF‑Style Game</h3>
      <p>Link to a legal FNAF‑like game.</p>
      <a href="#" target="_blank">Play</a>
    </div>

  </div>
</div>

<!-- BUILT-IN MINI GAME -->
<div class="container">
  <h2 style="color:#4cafef; text-align:center;">Built‑In Mini Game</h2>
  <p style="text-align:center; color:#bbb;">Use arrow keys to move the square and dodge the blocks.</p>
  <canvas id="game" width="400" height="400"></canvas>
</div>

<!-- FOOTER -->
<footer id="about">
  GameVerse Hub © 2026 — Created by You  
</footer>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

const player = { x: 180, y: 340, w: 40, h: 40, speed: 6 };
let blocks = [];
let keys = {};
let gameOver = false;
let score = 0;

document.addEventListener("keydown", e => keys[e.key] = true);
document.addEventListener("keyup",   e => keys[e.key] = false);

function spawnBlock() {
  const w = 40 + Math.random() * 60;
  const x = Math.random() * (canvas.width - w);
  const speed = 2 + Math.random() * 3;
  blocks.push({ x, y: -30, w, h: 20, speed });
}

function update() {
  if (gameOver) return;

  if (keys["ArrowLeft"])  player.x -= player.speed;
  if (keys["ArrowRight"]) player.x += player.speed;
  player.x = Math.max(0, Math.min(canvas.width - player.w, player.x));

  for (let b of blocks) b.y += b.speed;

  blocks = blocks.filter(b => {
    if (b.y > canvas.height) {
      score++;
      return false;
    }
    return true;
  });

  for (let b of blocks) {
    if (player.x < b.x + b.w &&
        player.x + player.w > b.x &&
        player.y < b.y + b.h &&
        player.y + player.h > b.y) {
      gameOver = true;
    }
  }

  if (Math.random() < 0.03) spawnBlock();
}

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "#4caf50";
  ctx.fillRect(player.x, player.y, player.w, player.h);

  ctx.fillStyle = "#e53935";
  for (let b of blocks) ctx.fillRect(b.x, b.y, b.w, b.h);

  ctx.fillStyle = "#fff";
  ctx.font = "18px Arial";
  ctx.fillText("Score: " + score, 10, 25);

  if (gameOver) {
    ctx.fillStyle = "rgba(0,0,0,0.7)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "#fff";
    ctx.font = "28px Arial";
    ctx.fillText("Game Over", 130, 190);
    ctx.font = "18px Arial";
    ctx.fillText("Refresh to play again", 115, 225);
  }
}

function loop() {
  update();
  draw();
  requestAnimationFrame(loop);
}
loop();
</script>

</body>
</html>
