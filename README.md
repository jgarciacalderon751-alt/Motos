<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Todo sobre motos</title>
<style>
    /* --- ESTILOS GENERALES --- */
    :root{--accent:#f39c12;--dark:#2c3e50;--card:#ffffff;}
    *{box-sizing:border-box}
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(to bottom, #e9ecef, #cfd8dc);
        margin: 0;
        padding: 0;
        color: var(--dark);
    }
    header {
        background-color: var(--accent);
        padding: 20px;
        text-align: center;
        color: #fff;
        border-radius: 0 0 12px 12px;
    }
    nav {
        display: flex;
        justify-content: center;
        gap: 10px;
        background-color: rgba(0,0,0,0.06);
        padding: 12px;
    }
    nav button {
        background-color: #fff;
        border: none;
        padding: 10px 16px;
        border-radius: 10px;
        cursor: pointer;
        font-size: 15px;
        transition: all .2s ease;
    }
    nav button.active, nav button:hover {
        background-color: var(--accent);
        color: #fff;
        transform: translateY(-2px);
    }
    main { padding: 20px; max-width:1100px; margin: 0 auto; }

    section {
        display: none;
        padding: 20px;
        background: var(--card);
        border-radius: 12px;
        box-shadow: 0 6px 18px rgba(0,0,0,0.12);
        margin-bottom: 24px;
    }
    section.active { display: block; }

    h2 { text-align:center; color:var(--dark); margin-top:0 }

    img { display:block; margin:12px auto; max-width:90%; border-radius:8px }

    /* Formulario */
    label { display:block; margin-bottom:6px; font-weight:700; color:#34495e }
    input, select, textarea { width:100%; padding:8px; margin-bottom:12px; border-radius:8px; border:1px solid #ccc; font-size:14px }
    button[type="submit"] { background:#27ae60; color:#fff; padding:10px 14px; border:none; border-radius:8px; cursor:pointer; }
    button[type="submit"]:hover{ background:#219150 }

    table { width:100%; border-collapse:collapse; margin-top:12px }
    th, td { border:1px solid #bbb; padding:8px; text-align:center }
    th { background:var(--accent); color:#fff }

    /* ===== Juego ===== */
    #gameWrapper { display:flex; flex-direction:column; align-items:center; gap:8px }
    #gameContainer {
        position: relative;
        width: 720px;
        max-width:100%;
        height: 420px;
        background: linear-gradient(to bottom, #2e8b57, #154734);
        border-radius: 16px;
        box-shadow: 0 0 30px rgba(11,58,26,0.6);
        overflow: hidden;
        touch-action: none;
    }
    canvas { display:block; width:100%; height:100%; border-radius:16px; background:linear-gradient(#555,#222) }
    #scoreboard { font-weight:700; font-size:20px; color:var(--dark); text-align:center; margin-top:6px }
    #message { text-align:center; color:#e74c3c; min-height:22px; font-weight:600 }
    #btnRestart { display:none; background:#f44336; color:#fff; padding:10px 20px; border:none; border-radius:10px; cursor:pointer; margin-top:8px }
    #btnRestart:hover{ background:#d32f2f }

    /* Responsive */
    @media (max-width:760px){
        nav { flex-wrap:wrap; gap:8px }
        #gameContainer { height:320px }
    }
</style>
</head>
<body>

<header>
    <h1>Todo sobre motos</h1>
</header>

<nav>
    <button id="btnNavInicio" class="active" onclick="mostrarPagina('inicio')">Inicio</button>
    <button id="btnNavInfo" onclick="mostrarPagina('informacion')">Información</button>
    <button id="btnNavForm" onclick="mostrarPagina('formulario')">Formulario</button>
    <button id="btnNavJuego" onclick="mostrarPagina('juego')">Juego</button>
</nav>

<main>
    <!-- INICIO -->
    <section id="inicio" class="active">
        <h2>MUNDO Y ORIGEN MOTORCYCLES</h2>
        <p style="text-align:center">Bienvenido a nuestro sitio sobre motocicletas. Explora la información, registra tus motos y diviértete con el juego.</p>
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/BMW_R1200GS_in_Munich.jpg/500px-BMW_R1200GS_in_Munich.jpg" alt="Moto ejemplo">
    </section>

    <!-- INFORMACIÓN -->
    <section id="informacion">
        <h2>Información sobre motocicletas</h2>
        <p>Las motocicletas son vehículos de dos ruedas impulsados por un motor. Se usan para transporte, ocio y competencia.</p>

        <h3>Tipos comunes</h3>
        <ul>
            <li>Deportiva</li>
            <li>Urbana</li>
            <li>Scooter</li>
            <li>Touring</li>
            <li>Enduro</li>
        </ul>

        <h3>Tabla de ejemplo</h3>
        <table>
            <tr><th>Marca</th><th>Modelo</th><th>Tipo</th><th>Año</th></tr>
            <tr><td>Yamaha</td><td>MT-07</td><td>Deportiva</td><td>2023</td></tr>
            <tr><td>Honda</td><td>CB500F</td><td>Urbana</td><td>2022</td></tr>
        </table>

        <p style="text-align:center; margin-top:12px"><a href="https://i.pinimg.com/474x/1e/94/94/1e949491d6bda02abc839f13b900c297.jpg" target="_blank">Ver imagen de referencia</a></p>
    </section>

    <!-- FORMULARIO -->
    <section id="formulario">
        <h2>Formulario: Todo sobre motos</h2>
        <form id="motoForm" action="#" method="post" onsubmit="guardarRegistro(event)">
            <label for="marca">Marca de la moto:</label>
            <input type="text" id="marca" name="marca" placeholder="Ej: Yamaha" required>

            <label for="modelo">Modelo:</label>
            <input type="text" id="modelo" name="modelo" placeholder="Ej: MT-07" required>

            <label for="tipo">Tipo de moto:</label>
            <select id="tipo" name="tipo" required>
                <option value="">Seleccione</option>
                <option value="deportiva">Deportiva</option>
                <option value="urbana">Urbana</option>
                <option value="scooter">Scooter</option>
                <option value="touring">Touring</option>
                <option value="enduro">Enduro</option>
            </select>

            <label for="año">Año de fabricación:</label>
            <input type="number" id="año" name="año" min="1990" max="2025" required>

            <label for="color">Color:</label>
            <input type="text" id="color" name="color" placeholder="Ej: Rojo">

            <label for="comentarios">Comentarios:</label>
            <textarea id="comentarios" name="comentarios" rows="4" placeholder="Opcional..."></textarea>

            <button type="submit">Enviar información</button>
        </form>
    </section>

    <!-- JUEGO -->
    <section id="juego">
        <h2>Juego: Moto Runner</h2>
        <div id="gameWrapper">
            <div id="gameContainer" aria-label="Juego Moto Runner">
                <canvas id="gameCanvas" width="720" height="420"></canvas>
            </div>
            <div id="scoreboard">Puntos: 0 | Nivel: 1</div>
            <div id="message" role="status" aria-live="polite"></div>
            <button id="btnRestart">Reiniciar Juego</button>
            <p style="font-size:13px; color:#555; margin-top:8px; text-align:center">Controles: flechas ↑ ↓ o toque en pantalla (móviles)</p>
        </div>
    </section>
</main>

<script>
/* Navegación entre "páginas" */
function mostrarPagina(id) {
    document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    // Activar botón nav correspondiente
    const map = {inicio:'btnNavInicio', informacion:'btnNavInfo', formulario:'btnNavForm', juego:'btnNavJuego'};
    if(map[id]) document.getElementById(map[id]).classList.add('active');
}

/* Guardar registro del formulario (ejemplo simple: consola y alerta) */
function guardarRegistro(e){
    e.preventDefault();
    const data = {
        marca: document.getElementById('marca').value,
        modelo: document.getElementById('modelo').value,
        tipo: document.getElementById('tipo').value,
        año: document.getElementById('año').value,
        color: document.getElementById('color').value,
        comentarios: document.getElementById('comentarios').value
    };
    console.log("Registro guardado:", data);
    alert('Información enviada. Gracias :)');
    e.target.reset();
}

/* ================== Código del juego Moto Runner (adaptado y embebido) ================== */
(() => {
  const canvas = document.getElementById('gameCanvas');
  const ctx = canvas.getContext('2d');
  const scoreDisplay = document.getElementById('scoreboard');
  const messageDisplay = document.getElementById('message');
  const btnRestart = document.getElementById('btnRestart');

  const width = canvas.width;
  const height = canvas.height;

  let gameOver = false;
  let score = 0;
  let level = 1;
  let speed = 5;
  let obstacleTimer = 0;
  let obstacleInterval = 1500;
  let lastTimestamp = 0;
  let obstacles = [];

  const bike = { x: 100, y: height / 2 - 25, width: 60, height: 50, color: '#FF5722', speedY: 7, smokeParticles: [] };
  const road = { laneCount: 3, laneHeight: height / 3, laneMarkings: [], markingWidth: 15, markingHeight: 50, markingSpacing: 90, offset: 0 };

  function generateRoadMarkings() {
    road.laneMarkings = [];
    for (let lane = 0; lane < road.laneCount; lane++) {
      for (let i = 0; i < Math.ceil(height / (road.markingHeight + road.markingSpacing)); i++) {
        road.laneMarkings.push({ lane, y: i * (road.markingHeight + road.markingSpacing) });
      }
    }
  }
  generateRoadMarkings();

  function drawRoad(delta) {
    ctx.fillStyle = '#3A5F0B';
    ctx.fillRect(0, 0, width, height);

    ctx.strokeStyle = '#9CCC65';
    ctx.lineWidth = 3;
    ctx.setLineDash([15, 20]);
    for (let i = 1; i < road.laneCount; i++) {
      const y = i * road.laneHeight;
      ctx.beginPath();
      ctx.moveTo(0, y);
      ctx.lineTo(width, y);
      ctx.stroke();
    }
    ctx.setLineDash([]);

    road.offset += speed * delta * 0.06;
    if (road.offset > road.markingHeight + road.markingSpacing) road.offset = 0;

    ctx.fillStyle = '#C5E1A5';
    road.laneMarkings.forEach(mark => {
      let y = (mark.y + road.offset) % (road.markingHeight + road.markingSpacing) - road.markingHeight;
      y += mark.lane * road.laneHeight + road.laneHeight / 2 - road.markingHeight / 2;
      ctx.fillRect(width / 2 - road.markingWidth / 2, y, road.markingWidth, road.markingHeight);
    });
  }

  function drawBike() {
    ctx.fillStyle = bike.color;
    ctx.strokeStyle = '#BF360C';
    ctx.lineWidth = 4;
    ctx.beginPath();
    ctx.moveTo(bike.x, bike.y + bike.height);
    ctx.lineTo(bike.x + 12, bike.y + bike.height / 3);
    ctx.lineTo(bike.x + bike.width - 15, bike.y + bike.height / 3);
    ctx.lineTo(bike.x + bike.width, bike.y + bike.height);
    ctx.closePath();
    ctx.fill();
    ctx.stroke();

    // wheels
    ctx.fillStyle = '#222';
    ctx.strokeStyle = '#555';
    ctx.lineWidth = 3;
    const r = 15;
    ctx.beginPath(); ctx.arc(bike.x + bike.width - 12, bike.y + bike.height + 7, r, 0, Math.PI * 2); ctx.fill(); ctx.stroke();
    ctx.beginPath(); ctx.arc(bike.x + 15, bike.y + bike.height + 7, r, 0, Math.PI * 2); ctx.fill(); ctx.stroke();

    // handlebar
    ctx.strokeStyle = '#B7410E';
    ctx.lineWidth = 5;
    ctx.beginPath(); ctx.moveTo(bike.x + 25, bike.y + bike.height / 4); ctx.lineTo(bike.x + 38, bike.y - 5); ctx.stroke();

    // smoke particles
    bike.smokeParticles.forEach((p, i) => {
      p.x -= p.speedX; p.y -= p.speedY; p.life -= 1;
      ctx.fillStyle = `rgba(180,180,180,${p.life / p.maxLife})`;
      ctx.beginPath(); ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2); ctx.fill();
      if (p.life <= 0) bike.smokeParticles.splice(i, 1);
    });
  }

  function createSmoke() {
    if (bike.smokeParticles.length < 10) {
      bike.smokeParticles.push({
        x: bike.x + 20 + Math.random() * 12,
        y: bike.y + bike.height + 15 + Math.random() * 8,
        size: 7 + Math.random() * 6,
        speedX: 1 + Math.random(),
        speedY: 0.4 + Math.random() * 0.5,
        life: 40 + Math.random() * 25,
        maxLife: 65,
      });
    }
  }

  function createObstacle() {
    const types = [{ w: 50, h: 35, c: '#7B4F00' }, { w: 40, h: 45, c: '#4B3621' }, { w: 35, h: 70, c: '#256D1A' }];
    const t = types[Math.floor(Math.random() * types.length)];
    const lane = Math.floor(Math.random() * road.laneCount);
    const yPos = lane * road.laneHeight + road.laneHeight / 2 - t.h / 2;
    return { x: width + 50, y: yPos, width: t.w, height: t.h, color: t.c, speedX: speed + Math.random() * 1.5 };
  }

  function drawObstacles() {
    obstacles.forEach(o => {
      ctx.fillStyle = o.color; ctx.fillRect(o.x, o.y, o.width, o.height);
      ctx.strokeStyle = '#222'; ctx.lineWidth = 2; ctx.strokeRect(o.x, o.y, o.width, o.height);
    });
  }

  function updateObstacles() {
    obstacles.forEach((o, i) => {
      o.x -= o.speedX;
      if (o.x + o.width < 0) {
        obstacles.splice(i, 1);
        score++;
        if (score % 10 === 0) {
          level++; speed += 0.7; obstacleInterval = Math.max(600, obstacleInterval - 150);
          messageDisplay.textContent = `¡Nivel ${level}! Más rápido.`;
          setTimeout(()=>{ if(!gameOver) messageDisplay.textContent = ''; }, 1800);
        }
      }
    });
  }

  function checkCollision(r1, r2) {
    return !(r1.x + r1.width < r2.x || r1.x > r2.x + r2.width || r1.y + r1.height < r2.y || r1.y > r2.y + r2.height);
  }

  function detectCollision() {
    const bikeRect = { x: bike.x, y: bike.y, width: bike.width, height: bike.height };
    for (const o of obstacles) if (checkCollision(bikeRect, o)) return true;
    return false;
  }

  function showMessage(msg) {
    messageDisplay.textContent = msg;
    setTimeout(() => { if (!gameOver) messageDisplay.textContent = ''; }, 1800);
  }

  // Inputs
  const keys = { ArrowUp: false, ArrowDown: false };
  window.addEventListener('keydown', e => { if (e.key === 'ArrowUp') keys.ArrowUp = true; if (e.key === 'ArrowDown') keys.ArrowDown = true; });
  window.addEventListener('keyup', e => { if (e.key === 'ArrowUp') keys.ArrowUp = false; if (e.key === 'ArrowDown') keys.ArrowDown = false; });

  let touchY = null;
  canvas.addEventListener('touchstart', e => { if (e.touches.length) touchY = e.touches[0].clientY - canvas.getBoundingClientRect().top; });
  canvas.addEventListener('touchmove', e => { e.preventDefault(); if (e.touches.length) touchY = e.touches[0].clientY - canvas.getBoundingClientRect().top; }, { passive: false });
  canvas.addEventListener('touchend', () => touchY = null);

  function updateBike() {
    if (keys.ArrowUp) bike.y -= bike.speedY;
    else if (keys.ArrowDown) bike.y += bike.speedY;
    else if (touchY !== null) {
      let center = bike.y + bike.height / 2;
      let dy = touchY - center;
      bike.y += Math.sign(dy) * Math.min(8, Math.abs(dy));
    }
    if (bike.y < 0) bike.y = 0; if (bike.y > height - bike.height) bike.y = height - bike.height;
    createSmoke();
  }

  function restartGame() {
    gameOver = false; score = 0; level = 1; speed = 5; obstacleInterval = 1500; obstacles = [];
    bike.y = height / 2 - bike.height / 2; messageDisplay.textContent = ''; btnRestart.style.display = 'none';
    lastTimestamp = 0; road.offset = 0; requestAnimationFrame(gameLoop);
  }

  function endGame() {
    gameOver = true; messageDisplay.textContent = `¡Chocaste! Puntuación final: ${score}`; btnRestart.style.display = 'inline-block';
  }

  btnRestart.addEventListener('click', restartGame);

  let obstacleTimerLocal = 0;
  function gameLoop(timestamp = 0) {
    if (gameOver) return;
    const delta = timestamp - lastTimestamp || 16;
    lastTimestamp = timestamp;
    drawRoad(delta);
    updateBike();
    updateObstacles();
    drawBike();
    drawObstacles();
    scoreDisplay.textContent = `Puntos: ${score} | Nivel: ${level}`;

    obstacleTimerLocal += delta;
    if (obstacleTimerLocal > obstacleInterval) { obstacles.push(createObstacle()); obstacleTimerLocal = 0; }

    if (detectCollision()) { endGame(); return; }
    requestAnimationFrame(gameLoop);
  }

  // start automatically when the Juego section is shown for the first time
  let juegoIniciado = false;
  document.getElementById('btnNavJuego').addEventListener('click', () => {
    // start only once
    if (!juegoIniciado) { juegoIniciado = true; restartGame(); }
  });

  // Also if page loads and user is already on the juego section, start
  if (document.getElementById('juego').classList.contains('active')) { juegoIniciado = true; restartGame(); }
})();
</script>

</body>
</html>
