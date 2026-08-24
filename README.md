# corazon[index.html](https://github.com/user-attachments/files/31362825/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Para ti ❤️</title>

  <style>
    body {
      margin: 0;
      background: black;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    #inicio {
      position: fixed;
      inset: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      background: black;
      z-index: 10;
    }

    #inicio h1 {
      color: #ffb6c1;
      text-align: center;
      font-size: 32px;
    }

    button {
      padding: 15px 25px;
      font-size: 18px;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      background: #ffb6c1;
      color: black;
      font-weight: bold;
    }

    #corazon {
      position: relative;
      width: 100vw;
      height: 100vh;
    }

    .texto {
      position: absolute;
      color: #ffb6c1;
      font-size: 10px;
      font-weight: bold;
      white-space: nowrap;
      transform: translate(-50%, -50%);
    }

    #mensaje {
      position: fixed;
      bottom: 40px;
      width: 100%;
      text-align: center;
      color: white;
      font-size: 22px;
      opacity: 0;
      transition: opacity 2s;
    }
  </style>
</head>

<body>

  <div id="inicio">
    <h1>Tengo algo para ti ❤️</h1>
    <button onclick="comenzar()">Abrir ❤️</button>
  </div>

  <div id="corazon"></div>

  <div id="mensaje">
    I love you ❤️
  </div>

  <script>
    function comenzar() {
      document.getElementById("inicio").style.display = "none";

      const contenedor = document.getElementById("corazon");

      let puntos = [];

      for (let scale = 8; scale <= 13; scale++) {

        for (let i = 0; i < 120; i++) {

          const angle = i * Math.PI * 2 / 120;

          const x =
            16 * Math.pow(Math.sin(angle), 3) * scale;

          const y =
            (
              13 * Math.cos(angle)
              - 5 * Math.cos(2 * angle)
              - 2 * Math.cos(3 * angle)
              - Math.cos(4 * angle)
            ) * scale;

          puntos.push({ x, y });
        }
      }

      let i = 0;

      const intervalo = setInterval(() => {

        if (i >= puntos.length) {
          clearInterval(intervalo);

          document.getElementById("mensaje").style.opacity = 1;

          return;
        }

        const punto = puntos[i];

        const texto = document.createElement("span");

        texto.className = "texto";

        texto.innerText = "I love you";

        texto.style.left =
          `calc(50% + ${punto.x}px)`;

        texto.style.top =
          `calc(45% - ${punto.y}px)`;

        contenedor.appendChild(texto);

        i++;

      }, 5);
    }
  </script>

</body>
</html>
