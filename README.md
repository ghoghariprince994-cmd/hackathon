# hackathon
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
    }

    h1 {
      font-size: 3rem;
      color: #fff;
      text-shadow: 0 0 15px rgba(255, 255, 255, 0.9);
      animation: glow 2s infinite alternate;
    }

    h2 {
      font-size: 2rem;
      color: #fff;
      margin-top: 15px;
      animation: float 3s ease-in-out infinite;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px #ff66b2; }
      to   { text-shadow: 0 0 25px #ff1493; }
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .balloon {
      position: absolute;
      bottom: -100px;
      width: 50px;
      height: 70px;
      border-radius: 50%;
      background: pink;
      animation: rise 10s linear infinite;
    }

    @keyframes rise {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-110vh); opacity: 0; }
    }

    canvas {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <h1>🎉 Happy Birthday 🎉</h1>
  <h2>Her Name 💖</h2>

  <canvas id="confetti"></canvas>

  <script>
    // Balloons
    function createBalloon() {
      const balloon = document.createElement("div");
      balloon.classList.add("balloon");
      document.body.appendChild(balloon);

      balloon.style.left = Math.random() * window.innerWidth + "px";
      balloon.style.background = hsl(${Math.random() * 360}, 70%, 60%);
      balloon.style.animationDuration = (5 + Math.random() * 5) + "s";

      setTimeout(() => {
        balloon.remove();
      }, 10000);
    }
    setInterval(createBalloon, 800);

    // Confetti
    const confetti = document.getElementById("confetti");
    const ctx = confetti.getContext("2d");
    confetti.width = window.innerWidth;
    confetti.height = window.innerHeight;

    const pieces = Array.from({ length: 150 }, () => ({
      x: Math.random() * confetti.width,
      y: Math.random() * confetti.height,
      size: Math.random() * 8 + 4,
      color: hsl(${Math.random() * 360}, 70%, 60%),
      speed: Math.random() * 3 + 2
    }));

    function drawConfetti() {
      ctx.clearRect(0, 0, confetti.width, confetti.height);
      pieces.forEach(p => {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
        ctx.fillStyle = p.color;
        ctx.fill();
        p.y += p.speed;
        if (p.y > confetti.height) p.y = -10;
      });
      requestAnimationFrame(drawConfetti);
    }
    drawConfetti();
  </script>
</body>
</html>
aauthor-prince
