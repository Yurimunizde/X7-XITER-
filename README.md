<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Auxílio Premium</title>
  <style>
    /* Fundo de estrelas animado */
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      font-family: Arial, sans-serif;
      color: white;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1;
    }
    /* Painel */
    .painel {
      background: rgba(20, 20, 20, 0.9);
      border-radius: 12px;
      padding: 20px;
      width: 300px;
      text-align: center;
      box-shadow: 0 0 15px rgba(0,0,0,0.8);
      position: relative;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    .titulo {
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 15px;
    }
    .grupo {
      text-align: left;
      margin: 15px 0;
    }
    .grupo label {
      display: block;
      margin: 5px 0;
    }
    .status {
      background: rgba(0,0,0,0.7);
      margin-top: 10px;
      padding: 10px;
      border-radius: 8px;
      font-size: 14px;
      text-align: left;
    }
  </style>
</head>
<body>
  <!-- Fundo animado -->
  <canvas id="stars"></canvas>

  <!-- Painel -->
  <div class="painel">
    <div class="titulo">Auxílio Premium</div>

    <div class="grupo">
      <strong>Sistema Avançado</strong>
      <label><input type="checkbox" checked> 120 FPS</label>
      <label><input type="checkbox" checked> No Recoil</label>
    </div>

    <div class="grupo">
      <strong>Ajustes de Mira</strong>
      <label><input type="checkbox" checked> Aimbot 90%</label>
      <label><input type="checkbox" checked> Head Trick</label>
      <label><input type="checkbox" checked> Neural Aim</label>
    </div>

    <div class="status">
      120 FPS: Ativado<br>
      No Recoil: Ativado<br>
      Aimbot 90%: Ativado<br>
      Head Trick: Ativado<br>
      Neural Aim: Ativado
    </div>
  </div>

  <!-- Script de estrelas -->
  <script>
    const canvas = document.getElementById('stars');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const stars = [];
    for (let i = 0; i < 100; i++) {
      stars.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        radius: Math.random() * 2,
        speed: Math.random() * 0.5
      });
    }

    function animateStars() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = 'white';
      stars.forEach(star => {
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, Math.PI * 2);
        ctx.fill();
        star.y += star.speed;
        if (star.y > canvas.height) star.y = 0;
      });
      requestAnimationFrame(animateStars);
    }
    animateStars();

    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    });
  </script>
</body>
</html>