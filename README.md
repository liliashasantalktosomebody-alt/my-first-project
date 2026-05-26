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
