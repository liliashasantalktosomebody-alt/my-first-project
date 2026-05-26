<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dino Runner Game</title>

<style>
body{
    margin:0;
    overflow:hidden;
    background:linear-gradient(to bottom,#87ceeb,#ffffff);
    font-family:Arial;
}

#game{
    width:100vw;
    height:100vh;
    position:relative;
    overflow:hidden;
}

#ground{
    position:absolute;
    bottom:0;
    width:100%;
    height:120px;
    background:#3cb371;
}

#dino{
    width:80px;
    height:80px;
    background:#16a34a;
    position:absolute;
    bottom:120px;
    left:100px;
    border-radius:20px;
    box-shadow:0 0 20px rgba(0,0,0,0.3);
}

.eye{
    width:10px;
    height:10px;
    background:black;
    border-radius:50%;
    position:absolute;
    top:20px;
}

#eye1{ left:18px; }
#eye2{ right:18px; }

#cactus{
    width:50px;
    height:100px;
    background:#065f46;
    position:absolute;
    bottom:120px;
    right:-100px;
    border-radius:10px;
}

#score{
    position:absolute;
    top:20px;
    left:20px;
    font-size:35px;
    font-weight:bold;
    color:#111827;
}

#startText{
    position:absolute;
    top:45%;
    width:100%;
    text-align:center;
    font-size:40px;
    color:#111827;
    font-weight:bold;
}

.cloud{
    position:absolute;
    width:120px;
    height:50px;
    background:white;
    border-radius:50px;
    opacity:0.9;
}

</style>
</head>
<body>

<div id="game">

<div class="cloud" style="top:80px;left:200px"></div>
<div class="cloud" style="top:150px;left:700px"></div>

<div id="score">Score: 0</div>
<div id="startText">Tap SPACE or Touch Screen</div>

<div id="dino">
<div class="eye" id="eye1"></div>
<div class="eye" id="eye2"></div>
</div>

<div id="cactus"></div>
<div id="ground"></div>

</div>

<script>
const dino = document.getElementById('dino');
const cactus = document.getElementById('cactus');
const scoreText = document.getElementById('score');
const startText = document.getElementById('startText');

let jumping = false;
let score = 0;
let cactusX = window.innerWidth;
let gameStarted = false;
let speed = 8;

function jump(){
    if(jumping) return;

    jumping = true;

    let up = 0;

    let jumpUp = setInterval(()=>{
        up += 20;
        dino.style.bottom = 120 + up + 'px';

        if(up >= 220){
            clearInterval(jumpUp);

            let down = setInterval(()=>{
                up -= 20;
                dino.style.bottom = 120 + up + 'px';

                if(up <= 0){
                    clearInterval(down);
                    jumping = false;
                }
            },20);
        }
    },20);
}

function startGame(){
    if(gameStarted) return;
    gameStarted = true;
    startText.style.display='none';
}

function gameLoop(){

    if(gameStarted){

        cactusX -= speed;
        cactus.style.left = cactusX + 'px';

        if(cactusX < -100){
            cactusX = window.innerWidth;
            score++;
            scoreText.innerHTML = 'Score: ' + score;

            if(score % 5 === 0){
                speed += 1;
            }
        }

        const dinoBottom = parseInt(window.getComputedStyle(dino).getPropertyValue('bottom'));

        if(cactusX > 80 && cactusX < 160 && dinoBottom < 190){
            alert('💀 Game Over! Your Score: ' + score);
            location.reload();
        }
    }

    requestAnimationFrame(gameLoop);
}

document.addEventListener('keydown',(e)=>{
    if(e.code === 'Space'){
        startGame();
        jump();
    }
});

document.addEventListener('touchstart',()=>{
    startGame();
    jump();
});

gameLoop();
</script>

</body>
</html>



function playVideo() {
  video.play();
}

function pauseVideo() {
  video.pause();
}

function uploadVideo(event) {
  const file = event.target.files[0];

  if (file) {
    const videoURL = URL.createObjectURL(file);
    video.src = videoURL;
    video.play();
  }
}<!DOCTYPE html><html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chat & Reels Viewer</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }body {
  background: #111;
  color: white;
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 30%;
  background: #1c1c1c;
  border-right: 2px solid #333;
  overflow-y: auto;
}

.sidebar h2 {
  padding: 20px;
  text-align: center;
  background: #222;
}

.chat {
  padding: 15px;
  border-bottom: 1px solid #333;
  cursor: pointer;
  transition: 0.3s;
}

.chat:hover {
  background: #333;
}

.main {
  width: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #000;
  position: relative;
}

.reel-container {
  width: 320px;
  height: 570px;
  border-radius: 20px;
  overflow: hidden;
  background: #222;
  box-shadow: 0 0 20px rgba(255,255,255,0.2);
}

video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.controls {
  position: absolute;
  bottom: 30px;
  display: flex;
  gap: 10px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  background: #ff0066;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background: #ff3385;
}

  </style>
</head>
<body>  <div class="sidebar">
    <h2>💬 Chats</h2><div class="chat">Rahim: Kemon acho?</div>
<div class="chat">Karim: Reel ta dekho 😄</div>
<div class="chat">Sadia: Ki korcho?</div>
<div class="chat">Hasan: New video upload korlam!</div>
<div class="chat">Mim: Online acho?</div>

  </div>  <div class="main">
    <div class="reel-container">
      <video id="reelVideo" autoplay muted loop controls>
        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
      </video>
    </div><div class="controls">
  <button onclick="playVideo()">▶ Play</button>
  <button onclick="pauseVideo()">⏸ Pause</button>
</div>

  </div>  <script>
    const video = document.getElementById('reelVideo');

    function playVideo() {
      video.play();
    }

    function pauseVideo() {
      video.pause();
    }
  </script></body>
</html>







<!DOCTYPE html><html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chat & Reels Viewer</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }body {
  background: #111;
  color: white;
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 30%;
  background: #1c1c1c;
  border-right: 2px solid #333;
  overflow-y: auto;
}

.sidebar h2 {
  padding: 20px;
  text-align: center;
  background: #222;
}

.chat {
  padding: 15px;
  border-bottom: 1px solid #333;
  cursor: pointer;
  transition: 0.3s;
}

.chat:hover {
  background: #333;
}

.main {
  width: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #000;
  position: relative;
}

.reel-container {
  width: 320px;
  height: 570px;
  border-radius: 20px;
  overflow: hidden;
  background: #222;
  box-shadow: 0 0 20px rgba(255,255,255,0.2);
}

video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.controls {
  position: absolute;
  bottom: 30px;
  display: flex;
  gap: 10px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  background: #ff0066;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background: #ff3385;
}

  </style>
</head>
<body>  <div class="sidebar">
    <h2>💬 Chats</h2><div class="chat">Rahim: Kemon acho?</div>
<div class="chat">Karim: Reel ta dekho 😄</div>
<div class="chat">Sadia: Ki korcho?</div>
<div class="chat">Hasan: New video upload korlam!</div>
<div class="chat">Mim: Online acho?</div>

  </div>  <div class="main">
    <div class="reel-container">
      <video id="reelVideo" autoplay muted loop controls>
        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
      </video>
    </div><div class="controls">
  <button onclick="playVideo()">▶ Play</button>
  <button onclick="pauseVideo()">⏸ Pause</button>
  <label for="videoUpload">
    <button>📤 Upload Video</button>
  </label>
  <input type="file" id="videoUpload" accept="video/*" onchange="uploadVideo(event)" hidden>
</div>

  </div>  <script>
    const video = document.getElementById('reelVideo');

    function playVideo() {
      video.play();
    }

    function pauseVideo() {
      video.pause();
    }

    function uploadVideo(event) {
      const file = event.target.files[0];

      if (file) {
        const videoURL = URL.createObjectURL(file);
        video.src = videoURL;
        video.play();
      }
    }
  </script></body>
</html>







<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dino Runner Game</title>

<style>
body{
    margin:0;
    overflow:hidden;
    background:linear-gradient(to bottom,#87ceeb,#ffffff);
    font-family:Arial;
}

#game{
    width:100vw;
    height:100vh;
    position:relative;
    overflow:hidden;
}

#ground{
    position:absolute;
    bottom:0;
    width:100%;
    height:120px;
    background:#3cb371;
}

#dino{
    width:80px;
    height:80px;
    background:#16a34a;
    position:absolute;
    bottom:120px;
    left:100px;
    border-radius:20px;
    box-shadow:0 0 20px rgba(0,0,0,0.3);
}

.eye{
    width:10px;
    height:10px;
    background:black;
    border-radius:50%;
    position:absolute;
    top:20px;
}

#eye1{ left:18px; }
#eye2{ right:18px; }

#cactus{
    width:50px;
    height:100px;
    background:#065f46;
    position:absolute;
    bottom:120px;
    right:-100px;
    border-radius:10px;
}

#score{
    position:absolute;
    top:20px;
    left:20px;
    font-size:35px;
    font-weight:bold;
    color:#111827;
}

#startText{
    position:absolute;
    top:45%;
    width:100%;
    text-align:center;
    font-size:40px;
    color:#111827;
    font-weight:bold;
}

.cloud{
    position:absolute;
    width:120px;
    height:50px;
    background:white;
    border-radius:50px;
    opacity:0.9;
}

</style>
</head>
<body>

<div id="game">

<div class="cloud" style="top:80px;left:200px"></div>
<div class="cloud" style="top:150px;left:700px"></div>

<div id="score">Score: 0</div>
<div id="startText">Tap SPACE or Touch Screen</div>

<div id="dino">
<div class="eye" id="eye1"></div>
<div class="eye" id="eye2"></div>
</div>

<div id="cactus"></div>
<div id="ground"></div>

</div>

<script>
const dino = document.getElementById('dino');
const cactus = document.getElementById('cactus');
const scoreText = document.getElementById('score');
const startText = document.getElementById('startText');

let jumping = false;
let score = 0;
let cactusX = window.innerWidth;
let gameStarted = false;
let speed = 8;

function jump(){
    if(jumping) return;

    jumping = true;

    let up = 0;

    let jumpUp = setInterval(()=>{
        up += 20;
        dino.style.bottom = 120 + up + 'px';

        if(up >= 220){
            clearInterval(jumpUp);

            let down = setInterval(()=>{
                up -= 20;
                dino.style.bottom = 120 + up + 'px';

                if(up <= 0){
                    clearInterval(down);
                    jumping = false;
                }
            },20);
        }
    },20);
}

function startGame(){
    if(gameStarted) return;
    gameStarted = true;
    startText.style.display='none';
}

function gameLoop(){

    if(gameStarted){

        cactusX -= speed;
        cactus.style.left = cactusX + 'px';

        if(cactusX < -100){
            cactusX = window.innerWidth;
            score++;
            scoreText.innerHTML = 'Score: ' + score;

            if(score % 5 === 0){
                speed += 1;
            }
        }

        const dinoBottom = parseInt(window.getComputedStyle(dino).getPropertyValue('bottom'));

        if(cactusX > 80 && cactusX < 160 && dinoBottom < 190){
            alert('💀 Game Over! Your Score: ' + score);
            location.reload();
        }
    }

    requestAnimationFrame(gameLoop);
}

document.addEventListener('keydown',(e)=>{
    if(e.code === 'Space'){
        startGame();
        jump();
    }
});

document.addEventListener('touchstart',()=>{
    startGame();
    jump();
});

gameLoop();
</script>

</body>
</html>




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Heart Matrix & Universe Dashboard</title>
    <style>
        /* মূল থিম ও লেআউট সেটআপ */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }
        body, html {
            width: 100%;
            height: 100%;
            background-color: #0a0a0c;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            overflow: hidden;
            color: #e2e8f0;
        }

        /* ড্যাশবোর্ড কন্টেইনার (স্প্লিট স্ক্রিন) */
        .dashboard {
            display: flex;
            width: 100%;
            height: 100%;
        }

        /* বাম পাশের নিয়ন্ত্রণ প্যানেল */
        .control-panel {
            width: 32%;
            height: 100%;
            background: linear-gradient(180deg, #121218 0%, #0c0c10 100%);
            border-right: 1px solid rgba(255, 255, 255, 0.08);
            padding: 25px;
            display: flex;
            flex-direction: column;
            gap: 25px;
            overflow-y: auto;
            box-shadow: 10px 0 30px rgba(0,0,0,0.5);
            z-index: 10;
        }

        /* লোগো ও হেডার */
        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            padding-bottom: 15px;
        }
        .brand .logo-heart {
            color: #ff2a5f;
            font-size: 28px;
            animation: pulse 1s infinite alternate;
        }
        .brand h1 {
            font-size: 20px;
            font-weight: 700;
            letter-spacing: 1px;
            background: linear-gradient(45deg, #ff2a5f, #ff7e5f);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* রিয়েল-টাইম স্ট্যাটাস কার্ড গ্রেড */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }
        .stat-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.05);
            padding: 12px;
            border-radius: 8px;
            text-align: center;
        }
        .stat-card .label {
            font-size: 11px;
            color: #64748b;
            text-transform: uppercase;
            margin-bottom: 4px;
        }
        .stat-card .value {
            font-size: 18px;
            font-weight: bold;
            color: #00ffcc;
            font-family: monospace;
        }

        /* কন্ট্রোল এলিমেন্ট গ্রুপ */
        .control-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        .control-group label {
            font-size: 13px;
            color: #94a3b8;
            display: flex;
            justify-content: space-between;
        }
        .control-group label span.val-display {
            color: #ff2a5f;
            font-family: monospace;
            font-weight: bold;
        }

        /* কাস্টম স্লাইডার (Sliders) */
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 6px;
            background: #1e1e28;
            border-radius: 3px;
            outline: none;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #ff2a5f;
            cursor: pointer;
            box-shadow: 0 0 10px #ff2a5f;
            transition: transform 0.1s;
        }
        input[type="range"]::-webkit-slider-thumb:hover {
            transform: scale(1.2);
        }

        /* ড্রপডাউন সিলেক্টর (Dropdowns) */
        select {
            width: 100%;
            padding: 10px;
            background: #1e1e28;
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 6px;
            color: white;
            outline: none;
            cursor: pointer;
        }

        /* বাটন ও ইন্টারেকশন */
        .btn {
            background: linear-gradient(90deg, #ff2a5f, #ff7e5f);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            text-align: center;
            text-transform: uppercase;
            font-size: 13px;
            box-shadow: 0 4px 15px rgba(255, 42, 95, 0.3);
        }
        .btn:hover {
            opacity: 0.9;
            box-shadow: 0 4px 25px rgba(255, 42, 95, 0.5);
        }

        /* ডান পাশের মূল ক্যানভাস প্রিভিউ এরিয়া */
        .preview-area {
            width: 68%;
            height: 100%;
            position: relative;
            background-color: #000;
        }
        canvas {
            width: 100%;
            height: 100%;
            display: block;
        }

        /* ক্যানভাসের ওপর টেকনো HUD ওভারলে */
        .hud-overlay {
            position: absolute;
            bottom: 25px;
            right: 25px;
            background: rgba(10, 10, 15, 0.75);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 8px;
            backdrop-filter: blur(8px);
            pointer-events: none;
            font-family: monospace;
            font-size: 11px;
            color: #888;
            line-height: 1.6;
        }
        .hud-line { display: flex; gap: 20px; justify-content: space-between; }
        .hud-line span.green-txt { color: #00ff88; }

        /* স্ক্রোলবার সুন্দর করা */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: rgba(0,0,0,0.1); }
        ::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(255,255,255,0.2); }

        @keyframes pulse { 0% { transform: scale(1); } 100% { transform: scale(1.15); } }

        /* রেসপনসিভLayout */
        @media (max-width: 900px) {
            .dashboard { flex-direction: column; }
            .control-panel { width: 100%; height: 45%; }
            .preview-area { width: 100%; height: 55%; }
        }
    </style>
</head>
<body>

    <div class="dashboard">
        
        <div class="control-panel">
            <div class="brand">
                <div class="logo-heart">❤️</div>
                <h1>HEART MATRIX PRO</h1>
            </div>

            <div class="stats-grid">
                <div class="stat-card">
                    <div class="label">সক্রিয় কণা</div>
                    <div class="value" id="stat-particles">0</div>
                </div>
                <div class="stat-card">
                    <div class="label">লাইভ FPS</div>
                    <div class="value" id="stat-fps">60</div>
                </div>
                <div class="stat-card">
                    <div class="label">গতিবেগ</div>
                    <div class="value" id="stat-velocity">2.0x</div>
                </div>
                <div class="stat-card">
                    <div class="label">কোর স্থায়িত্ব</div>
                    <div class="value" style="color: #00ff88;">99.4%</div>
                </div>
            </div>

            <div class="control-group">
                <label>সুরঙ্গের গতিবেগ (Speed) <span class="val-display" id="speed-val">2</span></label>
                <input type="range" id="ctrl-speed" min="0.5" max="15" step="0.5" value="2">
            </div>

            <div class="control-group">
                <label>কণার ঘনত্ব (Quantity) <span class="val-display" id="count-val">600</span></label>
                <input type="range" id="ctrl-count" min="100" max="1500" step="50" value="600">
            </div>

            <div class="control-group">
                <label>হার্টের সাইজ (Scale) <span class="val-display" id="size-val">12</span></label>
                <input type="range" id="ctrl-size" min="5" max="30" step="1" value="12">
            </div>

            <div class="control-group">
                <label>কালার থিম সিলেক্টর (Themes)</label>
                <select id="ctrl-theme">
                    <option value="rainbow">🌈 Rainbow Matrix (রঙিন মহাবিশ্ব)</option>
                    <option value="cyberpunk">⚡ Cyberpunk Neon (নিয়ন সাইবার)</option>
                    <option value="valentine">❤️ Classic Valentine (খাঁটি লাল হৃদয়)</option>
                    <option value="gold">✨ Royal Golden (সোনালী আভা)</option>
                    <option value="aqua">💎 Deep Aqua Ocean (নীল আকাশ)</option>
                </select>
            </div>

            <div class="control-group">
                <label>কণার আকৃতি (Particle Shape)</label>
                <select id="ctrl-shape">
                    <option value="heart">❤️ Heart Shape (হৃদয় আকৃতি)</option>
                    <option value="star">⭐ Star Shape (তারা আকৃতি)</option>
                    <option value="bubble">🔮 Glowing Bubble (বিন্দু কণা)</option>
                </select>
            </div>

            <button class="btn" id="btn-burst">সুপার কসমিক বার্স্ট (BOOST)</button>
        </div>

        <div class="preview-area">
            <canvas id="matrixCanvas"></canvas>
            
            <div class="hud-overlay">
                <div class="hud-line"><span>ENGINE STATUS:</span> <span class="green-txt">ACTIVE</span></div>
                <div class="hud-line"><span>RENDER MODE:</span> <span>3D PERSPECTIVE MATRIX</span></div>
                <div class="hud-line"><span>CORE ENGINE:</span> <span>MATHEMATICAL BEZIER V4</span></div>
                <div class="hud-line"><span>INTERACTION:</span> <span style="color: #ffbd2e;">MOUSE MOVE TRACKING</span></div>
            </div>
        </div>

    </div>

    <script>
        const canvas = document.getElementById('matrixCanvas');
        const ctx = canvas.getContext('2d');

        // প্যানেলের সাইজ অনুযায়ী মেজারমেন্ট নির্ধারণ
        let width = canvas.width = canvas.parentElement.clientWidth;
        let height = canvas.height = canvas.parentElement.clientHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = canvas.parentElement.clientWidth;
            height = canvas.height = canvas.parentElement.clientHeight;
        });

        // ড্যাশবোর্ডের ইনপুট অবজেক্টসমূহ যুক্ত করা
        const ctrlSpeed = document.getElementById('ctrl-speed');
        const ctrlCount = document.getElementById('ctrl-count');
        const ctrlSize = document.getElementById('ctrl-size');
        const ctrlTheme = document.getElementById('ctrl-theme');
        const ctrlShape = document.getElementById('ctrl-shape');
        const btnBurst = document.getElementById('btn-burst');

        // স্ট্যাটাস নোডসমূহ
        const statParticles = document.getElementById('stat-particles');
        const statVelocity = document.getElementById('stat-velocity');
        const statFps = document.getElementById('stat-fps');

        // গ্লোবাল ভ্যারিয়েবলস
        let hearts = [];
        let mouseX = width / 2;
        let mouseY = height / 2;
        let hue = 0;
        let lastTime = performance.now();
        let frameCount = 0;
        let fps = 60;

        // মাউস ট্র্যাকিং ইভেন্ট
        canvas.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            mouseX = e.clientX - rect.left;
            mouseY = e.clientY - rect.top;
        });

        // কণা বা পার্টিকেল ক্লাস
        class CosmicParticle {
            constructor() {
                this.reset(true);
            }

            reset(init = false) {
                this.z = init ? Math.random() * 1000 : 1000;
                this.angle = Math.random() * Math.PI * 2;
                // স্পাইরাল সুরঙ্গের ব্যাসার্ধ
                this.radius = Math.random() * 150 + 30; 

                this.x = Math.cos(this.angle) * this.radius;
                this.y = Math.sin(this.angle) * this.radius;

                this.rotation = Math.random() * Math.PI * 2;
                this.rotSpeed = (Math.random() - 0.5) * 0.03;
                this.color = this.getThemeColor();
            }

            getThemeColor() {
                const theme = ctrlTheme.value;
                if (theme === 'rainbow') return `hsl(${(hue + this.z / 3) % 360}, 100%, 65%)`;
                if (theme === 'cyberpunk') return Math.random() > 0.5 ? '#00ffcc' : '#ff00ff';
                if (theme === 'valentine') return `hsl(${Math.random() * 20 + 340}, 100%, ${Math.random() * 30 + 40}%)`;
                if (theme === 'gold') return `hsl(${Math.random() * 10 + 40}, 100%, ${Math.random() * 40 + 40}%)`;
                if (theme === 'aqua') return `hsl(${Math.random() * 30 + 170}, 100%, 60%)`;
                return '#ff2a5f';
            }

            update(speed) {
                this.z -= speed;
                this.rotation += this.rotSpeed;
                if (this.z <= 0) {
                    this.reset(false);
                }
            }

            draw() {
                const k = 380 / this.z; // ৩ডি ডেপথ রেশিও
                
                // ডাইনামিক মাউস কার্ভ ট্র্যাকিং
                const targetX = width / 2 + (mouseX - width / 2) * (1 - this.z / 1000);
                const targetY = height / 2 + (mouseY - height / 2) * (1 - this.z / 1000);

                const px = this.x * k + targetX;
                const py = this.y * k + targetY;
                
                const baseSize = parseFloat(ctrlSize.value);
                const s = baseSize * k;

                if (px < 0 || px > width || py < 0 || py > height) return;

                ctx.save();
                ctx.translate(px, py);
                ctx.rotate(this.rotation);
                ctx.beginPath();
                
                const shape = ctrlShape.value;
                if (shape === 'heart') {
                    // নিখুঁত ম্যাথমেটিক্যাল হার্ট পাথ
                    ctx.moveTo(0, 0);
                    ctx.bezierCurveTo(-s/2, -s/2, -s, s/3, 0, s);
                    ctx.bezierCurveTo(s, s/3, s/2, -s/2, 0, 0);
                } else if (shape === 'star') {
                    // তারা বা স্টার আকৃতি
                    for (let i = 0; i < 5; i++) {
                        ctx.lineTo(Math.cos((18 + i * 72) * Math.PI / 180) * s, -Math.sin((18 + i * 72) * Math.PI / 180) * s);
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Heart Matrix & Universe Dashboard</title>
    <style>
        /* মূল থিম ও লেআউট সেটআপ */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }
        body, html {
            width: 100%;
            height: 100%;
            background-color: #0a0a0c;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            overflow: hidden;
            color: #e2e8f0;
        }

        /* ড্যাশবোর্ড কন্টেইনার (স্প্লিট স্ক্রিন) */
        .dashboard {
            display: flex;
            width: 100%;
            height: 100%;
        }

        /* বাম পাশের নিয়ন্ত্রণ প্যানেল */
        .control-panel {
            width: 32%;
            height: 100%;
            background: linear-gradient(180deg, #121218 0%, #0c0c10 100%);
            border-right: 1px solid rgba(255, 255, 255, 0.08);
            padding: 25px;
            display: flex;
            flex-direction: column;
            gap: 25px;
            overflow-y: auto;
            box-shadow: 10px 0 30px rgba(0,0,0,0.5);
            z-index: 10;
        }

        /* লোগো ও হেডার */
        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            padding-bottom: 15px;
        }
        .brand .logo-heart {
            color: #ff2a5f;
            font-size: 28px;
            animation: pulse 1s infinite alternate;
        }
        .brand h1 {
            font-size: 20px;
            font-weight: 700;
            letter-spacing: 1px;
            background: linear-gradient(45deg, #ff2a5f, #ff7e5f);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* রিয়েল-টাইম স্ট্যাটাস কার্ড গ্রেড */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }
        .stat-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.05);
            padding: 12px;
            border-radius: 8px;
            text-align: center;
        }
        .stat-card .label {
            font-size: 11px;
            color: #64748b;
            text-transform: uppercase;
            margin-bottom: 4px;
        }
        .stat-card .value {
            font-size: 18px;
            font-weight: bold;
            color: #00ffcc;
            font-family: monospace;
        }

        /* কন্ট্রোল এলিমেন্ট গ্রুপ */
        .control-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        .control-group label {
            font-size: 13px;
            color: #94a3b8;
            display: flex;
            justify-content: space-between;
        }
        .control-group label span.val-display {
            color: #ff2a5f;
            font-family: monospace;
            font-weight: bold;
        }

        /* কাস্টম স্লাইডার (Sliders) */
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 6px;
            background: #1e1e28;
            border-radius: 3px;
            outline: none;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #ff2a5f;
            cursor: pointer;
            box-shadow: 0 0 10px #ff2a5f;
            transition: transform 0.1s;
        }
        input[type="range"]::-webkit-slider-thumb:hover {
            transform: scale(1.2);
        }

        /* ড্রপডাউন সিলেক্টর (Dropdowns) */
        select {
            width: 100%;
            padding: 10px;
            background: #1e1e28;
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 6px;
            color: white;
            outline: none;
            cursor: pointer;
        }

        /* বাটন ও ইন্টারেকশন */
        .btn {
            background: linear-gradient(90deg, #ff2a5f, #ff7e5f);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            text-align: center;
            text-transform: uppercase;
            font-size: 13px;
            box-shadow: 0 4px 15px rgba(255, 42, 95, 0.3);
        }
        .btn:hover {
            opacity: 0.9;
            box-shadow: 0 4px 25px rgba(255, 42, 95, 0.5);
        }

        /* ডান পাশের মূল ক্যানভাস প্রিভিউ এরিয়া */
        .preview-area {
            width: 68%;
            height: 100%;
            position: relative;
            background-color: #000;
        }
        canvas {
            width: 100%;
            height: 100%;
            display: block;
        }

        /* ক্যানভাসের ওপর টেকনো HUD ওভারলে */
        .hud-overlay {
            position: absolute;
            bottom: 25px;
            right: 25px;
            background: rgba(10, 10, 15, 0.75);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 8px;
            backdrop-filter: blur(8px);
            pointer-events: none;
            font-family: monospace;
            font-size: 11px;
            color: #888;
            line-height: 1.6;
        }
        .hud-line { display: flex; gap: 20px; justify-content: space-between; }
        .hud-line span.green-txt { color: #00ff88; }

        /* স্ক্রোলবার সুন্দর করা */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: rgba(0,0,0,0.1); }
        ::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.1); border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(255,255,255,0.2); }

        @keyframes pulse { 0% { transform: scale(1); } 100% { transform: scale(1.15); } }

        /* রেসপনসিভLayout */
        @media (max-width: 900px) {
            .dashboard { flex-direction: column; }
            .control-panel { width: 100%; height: 45%; }
            .preview-area { width: 100%; height: 55%; }
        }
    </style>
</head>
<body>

    <div class="dashboard">
        
        <div class="control-panel">
            <div class="brand">
                <div class="logo-heart">❤️</div>
                <h1>HEART MATRIX PRO</h1>
            </div>

            <div class="stats-grid">
                <div class="stat-card">
                    <div class="label">সক্রিয় কণা</div>
                    <div class="value" id="stat-particles">0</div>
                </div>
                <div class="stat-card">
                    <div class="label">লাইভ FPS</div>
                    <div class="value" id="stat-fps">60</div>
                </div>
                <div class="stat-card">
                    <div class="label">গতিবেগ</div>
                    <div class="value" id="stat-velocity">2.0x</div>
                </div>
                <div class="stat-card">
                    <div class="label">কোর স্থায়িত্ব</div>
                    <div class="value" style="color: #00ff88;">99.4%</div>
                </div>
            </div>

            <div class="control-group">
                <label>সুরঙ্গের গতিবেগ (Speed) <span class="val-display" id="speed-val">2</span></label>
                <input type="range" id="ctrl-speed" min="0.5" max="15" step="0.5" value="2">
            </div>

            <div class="control-group">
                <label>কণার ঘনত্ব (Quantity) <span class="val-display" id="count-val">600</span></label>
                <input type="range" id="ctrl-count" min="100" max="1500" step="50" value="600">
            </div>

            <div class="control-group">
                <label>হার্টের সাইজ (Scale) <span class="val-display" id="size-val">12</span></label>
                <input type="range" id="ctrl-size" min="5" max="30" step="1" value="12">
            </div>

            <div class="control-group">
                <label>কালার থিম সিলেক্টর (Themes)</label>
                <select id="ctrl-theme">
                    <option value="rainbow">🌈 Rainbow Matrix (রঙিন মহাবিশ্ব)</option>
                    <option value="cyberpunk">⚡ Cyberpunk Neon (নিয়ন সাইবার)</option>
                    <option value="valentine">❤️ Classic Valentine (খাঁটি লাল হৃদয়)</option>
                    <option value="gold">✨ Royal Golden (সোনালী আভা)</option>
                    <option value="aqua">💎 Deep Aqua Ocean (নীল আকাশ)</option>
                </select>
            </div>

            <div class="control-group">
                <label>কণার আকৃতি (Particle Shape)</label>
                <select id="ctrl-shape">
                    <option value="heart">❤️ Heart Shape (হৃদয় আকৃতি)</option>
                    <option value="star">⭐ Star Shape (তারা আকৃতি)</option>
                    <option value="bubble">🔮 Glowing Bubble (বিন্দু কণা)</option>
                </select>
            </div>

            <button class="btn" id="btn-burst">সুপার কসমিক বার্স্ট (BOOST)</button>
        </div>

        <div class="preview-area">
            <canvas id="matrixCanvas"></canvas>
            
            <div class="hud-overlay">
                <div class="hud-line"><span>ENGINE STATUS:</span> <span class="green-txt">ACTIVE</span></div>
                <div class="hud-line"><span>RENDER MODE:</span> <span>3D PERSPECTIVE MATRIX</span></div>
                <div class="hud-line"><span>CORE ENGINE:</span> <span>MATHEMATICAL BEZIER V4</span></div>
                <div class="hud-line"><span>INTERACTION:</span> <span style="color: #ffbd2e;">MOUSE MOVE TRACKING</span></div>
            </div>
        </div>

    </div>

    <script>
        const canvas = document.getElementById('matrixCanvas');
        const ctx = canvas.getContext('2d');

        // প্যানেলের সাইজ অনুযায়ী মেজারমেন্ট নির্ধারণ
        let width = canvas.width = canvas.parentElement.clientWidth;
        let height = canvas.height = canvas.parentElement.clientHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = canvas.parentElement.clientWidth;
            height = canvas.height = canvas.parentElement.clientHeight;
        });

        // ড্যাশবোর্ডের ইনপুট অবজেক্টসমূহ যুক্ত করা
        const ctrlSpeed = document.getElementById('ctrl-speed');
        const ctrlCount = document.getElementById('ctrl-count');
        const ctrlSize = document.getElementById('ctrl-size');
        const ctrlTheme = document.getElementById('ctrl-theme');
        const ctrlShape = document.getElementById('ctrl-shape');
        const btnBurst = document.getElementById('btn-burst');

        // স্ট্যাটাস নোডসমূহ
        const statParticles = document.getElementById('stat-particles');
        const statVelocity = document.getElementById('stat-velocity');
        const statFps = document.getElementById('stat-fps');

        // গ্লোবাল ভ্যারিয়েবলস
        let hearts = [];
        let mouseX = width / 2;
        let mouseY = height / 2;
        let hue = 0;
        let lastTime = performance.now();
        let frameCount = 0;
        let fps = 60;

        // মাউস ট্র্যাকিং ইভেন্ট
        canvas.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            mouseX = e.clientX - rect.left;
            mouseY = e.clientY - rect.top;
        });

        // কণা বা পার্টিকেল ক্লাস
        class CosmicParticle {
            constructor() {
                this.reset(true);
            }

            reset(init = false) {
                this.z = init ? Math.random() * 1000 : 1000;
                this.angle = Math.random() * Math.PI * 2;
                // স্পাইরাল সুরঙ্গের ব্যাসার্ধ
                this.radius = Math.random() * 150 + 30; 

                this.x = Math.cos(this.angle) * this.radius;
                this.y = Math.sin(this.angle) * this.radius;

                this.rotation = Math.random() * Math.PI * 2;
                this.rotSpeed = (Math.random() - 0.5) * 0.03;
                this.color = this.getThemeColor();
            }

            getThemeColor() {
                const theme = ctrlTheme.value;
                if (theme === 'rainbow') return `hsl(${(hue + this.z / 3) % 360}, 100%, 65%)`;
                if (theme === 'cyberpunk') return Math.random() > 0.5 ? '#00ffcc' : '#ff00ff';
                if (theme === 'valentine') return `hsl(${Math.random() * 20 + 340}, 100%, ${Math.random() * 30 + 40}%)`;
                if (theme === 'gold') return `hsl(${Math.random() * 10 + 40}, 100%, ${Math.random() * 40 + 40}%)`;
                if (theme === 'aqua') return `hsl(${Math.random() * 30 + 170}, 100%, 60%)`;
                return '#ff2a5f';
            }

            update(speed) {
                this.z -= speed;
                this.rotation += this.rotSpeed;
                if (this.z <= 0) {
                    this.reset(false);
                }
            }

            draw() {
                const k = 380 / this.z; // ৩ডি ডেপথ রেশিও
                
                // ডাইনামিক মাউস কার্ভ ট্র্যাকিং
                const targetX = width / 2 + (mouseX - width / 2) * (1 - this.z / 1000);
                const targetY = height / 2 + (mouseY - height / 2) * (1 - this.z / 1000);

                const px = this.x * k + targetX;
                const py = this.y * k + targetY;
                
                const baseSize = parseFloat(ctrlSize.value);
                const s = baseSize * k;

                if (px < 0 || px > width || py < 0 || py > height) return;

                ctx.save();
                ctx.translate(px, py);
                ctx.rotate(this.rotation);
                ctx.beginPath();
                
                const shape = ctrlShape.value;
                if (shape === 'heart') {
                    // নিখুঁত ম্যাথমেটিক্যাল হার্ট পাথ
                    ctx.moveTo(0, 0);
                    ctx.bezierCurveTo(-s/2, -s/2, -s, s/3, 0, s);
                    ctx.bezierCurveTo(s, s/3, s/2, -s/2, 0, 0);
                } else if (shape === 'star') {
                    // তারা বা স্টার আকৃতি
                    for (let i = 0; i < 5; i++) {
                        ctx.lineTo(Math.cos((18 + i * 72) * Math.PI / 180) * s, -Math.sin((18 + i * 72) * Math.PI / 180) * s);
                        ctx.lineTo(Math.cos((54 + i * 72) * Math.PI / 180) * (s/2), -Math.sin((54 + i * 72) * Math.PI / 180) * (s/2));
                    }
                } else {
                    // গ্লোয়িং বাবল বা সার্কেল
                    ctx.arc(0, 0, s/2, 0, Math.PI * 2);
                }

                ctx.fillStyle = this.color;
                ctx.shadowBlur = s * 0.5;
                ctx.shadowColor = this.color;
                
                ctx.fill();
                ctx.restore();
            }
        }

        // কণার সংখ্যা সিঙ্ক করার ফাংশন
        function syncParticles() {
            const targetCount = parseInt(ctrlCount.value);
            document.getElementById('count-val').innerText = targetCount;
            statParticles.innerText = targetCount;

            if (hearts.length < targetCount) {
                while (hearts.length < targetCount) hearts.push(new CosmicParticle());
            } else if (hearts.length > targetCount) {
                hearts.splice(targetCount);
            }
        }

        // বার্স্ট বুস্ট মেকানিজম
        let burstActive = false;
        let burstTimer = 0;
        btnBurst.addEventListener('click', () => {
            burstActive = true;
            burstTimer = 40; // ৪০ ফ্রেম বুস্ট থাকবে
        });

        // অনবরত চলমান রেন্ডার লুপ
        function renderUniverse() {
            // এফপিএস (FPS) ক্যালকুলেশন
            frameCount++;
            const time = performance.now();
            if (time >= lastTime + 1000) {
                fps = Math.round((frameCount * 1000) / (time - lastTime));
                statFps.innerText = fps;
                frameCount = 0;
                lastTime = time;
            }

            // স্লাইডার ভ্যালু লাইভ আপডেট করা
            let currentSpeed = parseFloat(ctrlSpeed.value);
            if (burstActive) {
                currentSpeed *= 4; // বুস্টের সময় গতি ৪ গুণ বাড়বে
                burstTimer--;
                if (burstTimer <= 0) burstActive = false;
            }
            
            document.getElementById('speed-val').innerText = currentSpeed.toFixed(1);
            document.getElementById('size-val').innerText = ctrlSize.value;
            statVelocity.innerText = currentSpeed.toFixed(1) + "x";

            syncParticles();

            // মোশন ব্লার ইফেক্টের চমৎকার ট্রেইল ব্যাকগ্রাউন্ড
            ctx.fillStyle = 'rgba(0, 0, 0, 0.16)';
            ctx.fillRect(0, 0, width, height);

            // ৩ডি ডেপথ সর্টিং (পেছনের কণা আগে এবং সামনের কণা পরে আঁকা হবে)
            hearts.sort((a, b) => b.z - a.z);

            hearts.forEach(heart => {
                heart.update(currentSpeed);
                heart.draw();
            });

            // কেন্দ্রের মেইন গ্লোয়িং বিটিং কোর হার্ট (Central Beating Heart)
            const corePulse = 1 + Math.sin(Date.now() * 0.005) * 0.08;
            const coreSize = 35 * corePulse;
            ctx.save();
            ctx.translate(width / 2 + (mouseX - width / 2) * 0.1, height / 2 + (mouseY - height / 2) * 0.1);
            ctx.beginPath();
            ctx.moveTo(0, -coreSize/3);
            ctx.bezierCurveTo(-coreSize/2, -coreSize, -coreSize, -coreSize/3, 0, coreSize * 0.8);
            ctx.bezierCurveTo(coreSize, -coreSize/3, coreSize/2, -coreSize, 0, -coreSize/3);
            
            // থিম অনুযায়ী সেন্ট্রাল কোরের কালার পরিবর্তন
            const theme = ctrlTheme.value;
            let coreColor = '#ff2a5f';
            if (theme === 'cyberpunk') coreColor = '#ff00ff';
            if (theme === 'gold') coreColor = '#ffbd2e';
            if (theme === 'aqua') coreColor = '#00ffff';
            
            ctx.fillStyle = coreColor;
            ctx.shadowBlur = 50;
            ctx.shadowColor = coreColor;
            ctx.fill();
            ctx.restore();

            hue += 0.5;
            requestAnimationFrame(renderUniverse);
        }

        // প্রথমবার চালানোর ইনিশিয়ালাইজেশন
        syncParticles();
        renderUniverse();
    </script>
</body>
</html>
