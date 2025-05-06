<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Pietra Miliare Maldives</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

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
      opacity: 0;
      transition: opacity 1.5s ease;
    }

    @keyframes pulse {
      from { transform: scale(1); opacity: 0.9; }
      to { transform: scale(1.05); opacity: 1; }
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

    #loading {
      position: absolute;
      z-index: 20;
      font-size: 1.5em;
      animation: blink 1s infinite;
      text-shadow: 0 0 5px #00ffee, 0 0 10px #00ffee;
    }

    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }

    .hidden {
      display: none;
    }

    .fade-in {
      opacity: 1 !important;
    }
  </style>
</head>
<body>
  <div id="loading">Loading...</div>
  <h1 id="mainTitle">Pietra Miliare Maldives</h1>
  <div class="matrix">
    <canvas id="matrixCanvas"></canvas>
  </div>

  <script>
    const canvas = document.getElementById("matrixCanvas");
    const ctx = canvas.getContext("2d");

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const letters = "アカサタナハマヤラワ0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const fontSize = 14;
    const columns = canvas.width / fontSize;
    const drops = Array(Math.floor(columns)).fill(1);

    function drawMatrix() {
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

    setInterval(drawMatrix, 33);

    // Handle loading effect
    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('loading').classList.add('hidden');
        document.getElementById('mainTitle').classList.add('fade-in');
      }, 3000); // Adjust delay as needed (3000ms = 3s)
    });

    // Handle resize
    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>
