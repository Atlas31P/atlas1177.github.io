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
      color: #00ccff;
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
      text-shadow: 0 0 5px #00ccff, 0 0 10px #00ccff, 0 0 20px #00ccff;
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
      background: radial-gradient(ellipse at center, #000000 0%, #001f33 100%);
    }

    canvas {
      display: block;
    }

    #loading {
      position: absolute;
      z-index: 20;
      font-size: 1.5em;
      animation: blink 1s infinite;
      text-shadow: 0 0 5px #00ccff, 0 0 10px #00ccff;
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

    let width = canvas.width = window.innerWidth;
    let height = canvas.height = window.innerHeight;

    const message = "until you make it... zitto e nuota zitto e nuota nuota nuota... ";
    const lines = 8; // number of wave lines
    const fontSize = 22;
    const textSpacing = fontSize;
    const waveAmplitudeBase = 20;
    const waveFrequencyBase = 0.015;
    const waveSpeedBase = 0.5;

    let offset = 0;

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 0, 0.1)";
      ctx.fillRect(0, 0, width, height);

      ctx.font = fontSize + "px Courier New";
      ctx.shadowColor = "#00ffff";
      ctx.shadowBlur = 8;

      for (let l = 0; l < lines; l++) {
        const waveAmplitude = waveAmplitudeBase + l * 5;
        const waveFrequency = waveFrequencyBase + l * 0.002;
        const waveSpeed = waveSpeedBase + l * 0.1;
        const yOffset = (height / (lines + 1)) * (l + 1);

        for (let i = 0; i < message.length; i++) {
          const x = (i * textSpacing - offset * waveSpeed) % (width + message.length * textSpacing);
          const y = yOffset + Math.sin((x + offset) * waveFrequency) * waveAmplitude;

          // Color shift for retro-futuristic effect
          const hue = 200 + (l * 10) % 60;
          ctx.fillStyle = `hsl(${hue}, 100%, 60%)`;

          ctx.fillText(message[i], x, y);
        }
      }

      offset += 1.5;
      requestAnimationFrame(draw);
    }

    draw();

    window.addEventListener('resize', () => {
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    });

    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('loading').classList.add('hidden');
        document.getElementById('mainTitle').classList.add('fade-in');
      }, 3000);
    });
  </script>
</body>
</html>
