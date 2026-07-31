<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Para Denisse</title>
  <style>
    :root {
      --primary-blue: #00c6ff;
      --secondary-blue: #0072ff;
      --dark-blue: #002b66;
      --deep-blue: #000c1a;
      --text-main: #ffffff;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #050b14, #0a192f, #112240);
      color: var(--text-main);
      overflow-x: hidden;
    }

    .card {
      background: rgba(255, 255, 255, 0.03);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 24px;
      padding: 40px 25px;
      width: 90%;
      max-width: 440px;
      text-align: center;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.7);
      position: relative;
    }

    /* --- PANTALLA 1 --- */
    #screen-1 {
      transition: opacity 0.5s ease, transform 0.5s ease;
    }

    h1 {
      font-size: 1.4rem;
      font-weight: 400;
      line-height: 1.6;
      margin-bottom: 35px;
      color: #e0f2fe;
    }

    .btn-next {
      background: linear-gradient(135deg, var(--primary-blue), var(--secondary-blue));
      color: #ffffff;
      border: none;
      padding: 15px 42px;
      font-size: 1rem;
      font-weight: 600;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 8px 25px rgba(0, 114, 255, 0.4);
      transition: all 0.3s ease;
    }

    .btn-next:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 30px rgba(0, 114, 255, 0.6);
    }

    /* --- PANTALLA 2 --- */
    #screen-2 {
      display: none;
      opacity: 0;
      flex-direction: column;
      align-items: center;
      transition: opacity 0.8s ease;
    }

    .name-denisse {
      font-size: 2.8rem;
      font-family: 'Georgia', serif;
      font-weight: bold;
      color: transparent;
      background: linear-gradient(to right, #ffffff, var(--primary-blue), #93c5fd);
      -webkit-background-clip: text;
      background-clip: text;
      margin-bottom: 20px;
      animation: glowText 2.5s ease-in-out infinite alternate;
    }

    /* --- ROSA AZUL (ESTILO VECTOR / ORIGAMI DE LA IMAGEN) --- */
    .flower-container {
      position: relative;
      width: 220px;
      height: 290px;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      margin-top: 10px;
    }

    /* Tallo recto */
    .stem {
      position: absolute;
      bottom: 0;
      width: 8px;
      height: 180px;
      background: linear-gradient(to right, #053b11, #0fa83b, #053b11);
      border-radius: 4px;
      z-index: 1;
    }

    /* Hojas con forma de gota lisa como la referencia */
    .leaf {
      position: absolute;
      width: 55px;
      height: 35px;
      background: linear-gradient(135deg, #0fa83b 0%, #032b0a 100%);
      border-radius: 0% 100% 100% 0% / 0% 100% 0% 100%;
      z-index: 1;
      box-shadow: -2px 4px 8px rgba(0, 0, 0, 0.5);
    }

    .leaf.left {
      bottom: 50px;
      left: 20px;
      transform: rotate(-25deg);
    }

    .leaf.right {
      bottom: 80px;
      right: 20px;
      transform: scaleX(-1) rotate(-15deg);
    }

    /* Cabeza de la Rosa estilo Cáliz */
    .rose-head {
      position: absolute;
      top: 15px;
      width: 140px;
      height: 130px;
      z-index: 5;
    }

    /* Pétalos estilizados tipo copa */
    .petal-layer {
      position: absolute;
      border-radius: 10px 10px 60px 60px;
    }

    /* Capa trasera interna del capullo */
    .inner-back {
      top: 0px;
      left: 25px;
      width: 90px;
      height: 70px;
      background: linear-gradient(to bottom, #1d4ed8, #0f172a);
      border-radius: 15px 15px 40px 40px;
      z-index: 1;
    }

    .inner-center {
      top: 10px;
      left: 35px;
      width: 70px;
      height: 60px;
      background: linear-gradient(to bottom, #60a5fa, #1e40af);
      border-radius: 10px 10px 30px 30px;
      z-index: 2;
    }

    /* Pétalo envolvente izquierdo */
    .petal-left {
      top: 15px;
      left: 10px;
      width: 75px;
      height: 90px;
      background: linear-gradient(135deg, #38bdf8 0%, #0284c7 60%, #032b69 100%);
      border-radius: 20px 80px 20px 90px;
      transform: rotate(-12deg);
      z-index: 3;
      box-shadow: 2px 4px 10px rgba(0, 0, 0, 0.3);
    }

    /* Pétalo envolvente derecho */
    .petal-right {
      top: 15px;
      right: 10px;
      width: 75px;
      height: 90px;
      background: linear-gradient(-135deg, #00c6ff 0%, #0072ff 60%, #001f4d 100%);
      border-radius: 80px 20px 90px 20px;
      transform: rotate(12deg);
      z-index: 4;
      box-shadow: -2px 4px 10px rgba(0, 0, 0, 0.3);
    }

    /* Sépalos verdes triangulares debajo de la copa */
    .sepals {
      position: absolute;
      top: 85px;
      left: 50%;
      transform: translateX(-50%);
      width: 120px;
      height: 40px;
      display: flex;
      justify-content: space-between;
      z-index: 6;
    }

    .sepal {
      width: 0;
      height: 0;
      border-left: 12px solid transparent;
      border-right: 12px solid transparent;
      border-top: 35px solid #0fa83b;
      filter: drop-shadow(0px 2px 4px rgba(0,0,0,0.4));
    }

    .sepal:nth-child(1) { transform: rotate(25deg); }
    .sepal:nth-child(2) { transform: rotate(10deg); }
    .sepal:nth-child(3) { transform: rotate(-10deg); }
    .sepal:nth-child(4) { transform: rotate(-25deg); }

    /* Brillos mágicos flotantes */
    .sparkle {
      position: absolute;
      width: 4px;
      height: 4px;
      background: #ffffff;
      border-radius: 50%;
      box-shadow: 0 0 8px #00c6ff;
      animation: floatSparkle 3s infinite ease-in-out;
    }

    .sp-1 { top: 20%; left: 15%; animation-delay: 0s; }
    .sp-2 { top: 10%; right: 20%; animation-delay: 0.7s; }
    .sp-3 { top: 60%; left: 10%; animation-delay: 1.4s; }
    .sp-4 { top: 50%; right: 15%; animation-delay: 2.1s; }

    /* --- ANIMACIONES --- */
    @keyframes glowText {
      from { text-shadow: 0 0 10px rgba(0, 198, 255, 0.3); }
      to { text-shadow: 0 0 25px rgba(0, 198, 255, 0.8), 0 0 35px rgba(255, 255, 255, 0.6); }
    }

    @keyframes floatSparkle {
      0%, 100% { transform: translateY(0) scale(0.6); opacity: 0.3; }
      50% { transform: translateY(-12px) scale(1.2); opacity: 1; }
    }
  </style>
</head>
<body>

  <div class="card">
    <!-- Pantalla 1 -->
    <div id="screen-1">
      <h1>Prepárate para que veas lo que no has visto en muchos años...</h1>
      <button class="btn-next" onclick="showSurprise()">Siguiente</button>
    </div>

    <!-- Pantalla 2 -->
    <div id="screen-2">
      <div class="name-denisse">Denisse</div>
      
      <div class="flower-container">
        <!-- Tallo y hojas -->
        <div class="stem"></div>
        <div class="leaf left"></div>
        <div class="leaf right"></div>
        
        <!-- Flor estilo imagen de referencia -->
        <div class="rose-head">
          <div class="petal-layer inner-back"></div>
          <div class="petal-layer inner-center"></div>
          <div class="petal-layer petal-left"></div>
          <div class="petal-layer petal-right"></div>
          
          <!-- Sépalos triangulares verdes -->
          <div class="sepals">
            <div class="sepal"></div>
            <div class="sepal"></div>
            <div class="sepal"></div>
            <div class="sepal"></div>
          </div>
        </div>

        <!-- Partículas de luz -->
        <div class="sparkle sp-1"></div>
        <div class="sparkle sp-2"></div>
        <div class="sparkle sp-3"></div>
        <div class="sparkle sp-4"></div>
      </div>
    </div>
  </div>

  <script>
    function showSurprise() {
      const s1 = document.getElementById('screen-1');
      const s2 = document.getElementById('screen-2');

      s1.style.opacity = '0';
      s1.style.transform = 'translateY(-10px)';

      setTimeout(() => {
        s1.style.display = 'none';
        s2.style.display = 'flex';
        setTimeout(() => { s2.style.opacity = '1'; }, 50);
      }, 500);
    }
  </script>

</body>
</html>
