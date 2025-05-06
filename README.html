<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Pietra Miliare Maldives</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: black;
      color: #00ffcc;
      font-family: 'Courier New', Courier, monospace;
      overflow: hidden;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    h1 {
      font-size: 2em;
      z-index: 10;
      text-shadow: 0 0 5px #00ffee, 0 0 10px #00ffee, 0 0 20px #00ffee;
      animation: pulse 2s infinite alternate;
    }

    @keyframes pulse {
      from {
        transform: scale(1);
        opacity: 0.9;
      }
      to {
        transform: scale(1.05);
        opacity: 1;
      }
    }

    .matrix {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      z-index: 1;
      overflow: hidden;
      background: radial-gradient(ellipse at center, #000000 0%, #001f1f 100%);
    }

    canvas {
      display: block;
    }
  </style>
</head>
<body>
  <div class="matrix">
    <canvas id="matrixCanvas"></canvas>
  </div>
  <h1>PIETRA MILIARE MALDIVE<br>until you make it...</h1>

  <script>
    const canvas = document.getElementById("matrixCanvas");
    const ctx = canvas.getContext("2d");

    canvas.height = window.innerHeight;
    canvas.width = window.innerWidth;

    const letters = "アァイゥエオカキクケコサシスセソ0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const fontSize = 14;
    const columns = canvas.width / fontSize;

    const drops = Array.from({ length: columns }).fill(1);

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = "#00ffcc";
      ctx.font = fontSize + "px monospace";

      for (let i = 0; i < drops.length; i++) {
        const text = letters.charAt(Math.floor(Math.random() * letters.length));
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i]++;
      }
    }

    setInterval(draw, 33);
    window.addEventListener("resize", () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
