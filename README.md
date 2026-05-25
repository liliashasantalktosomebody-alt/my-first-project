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
