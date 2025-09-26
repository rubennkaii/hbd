<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Bday Milea</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: linear-gradient(to right, #ffdde1, #ee9ca7);
      height: 100vh;
      margin: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }
    .card {
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    }
    button {
      margin-top: 15px;
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      background: #ff4b2b;
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background: #ff416c;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>Happy Bday, Milea ✨</h2>
    <p>Semoga panjang umur, sehat selalu, and banyak hal baik yang dateng di idup kmu.</p>
    <p>Aku inget dulu kmu sempet bilang "tunggu sampe ultah" sebelum ky gini, jadi… gw cuma mau nepatin itu aja.</p>
    <p>Semoga lu bahagia ya hari ini. 🎉</p>
    <button onclick="playSurprise()">Klik di sini 🎁</button>
  </div>

  <canvas id="confetti"></canvas>
  <audio id="music" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"></audio>

  <script>
    function playSurprise() {
      document.getElementById("music").play();
      startConfetti();
    }

    // Confetti effect
    const canvas = document.getElementById("confetti");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    const confetti = Array.from({ length: 150 }, () => ({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height - canvas.height,
      r: Math.random() * 6 + 4,
      d: Math.random() * 10 + 5,
      color: `hsl(${Math.random() * 360}, 100%, 50%)`,
      tilt: Math.random() * 10 - 10
    }));

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach(c => {
        ctx.beginPath();
        ctx.fillStyle = c.color;
        ctx.fillRect(c.x, c.y, c.r, c.r);
        ctx.fill();
      });
      updateConfetti();
    }

    function updateConfetti() {
      confetti.forEach(c => {
        c.y += c.d;
        if (c.y > canvas.height) {
          c.y = -10;
          c.x = Math.random() * canvas.width;
        }
      });
    }

    function startConfetti() {
      setInterval(drawConfetti, 20);
    }
  </script>
</body>
</html>
