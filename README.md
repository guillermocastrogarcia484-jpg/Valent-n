<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Carito ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #fce4ec; /* Rosa suave */
            font-family: 'Arial Rounded MT Bold', 'Helvetica', sans-serif;
            overflow: hidden;
        }

        #contenedor {
            text-align: center;
            background: white;
            padding: 3rem;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(233, 30, 99, 0.2);
            max-width: 500px;
            width: 90%;
            transition: all 0.3s ease;
        }

        h1 {
            color: #d81b60;
            margin-bottom: 2rem;
            font-size: 2rem;
        }

        .botones {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        #btnSi {
            background-color: #ff4081;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.1s ease;
            box-shadow: 0 4px 15px rgba(255, 64, 129, 0.4);
        }

        #btnNo {
            background-color: #9e9e9e;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            position: relative;
            transition: 0.1s;
        }

        #mensajeFinal {
            display: none;
        }

        .texto-final {
            color: #c2185b;
            font-size: 1.8rem;
            line-height: 1.4;
        }

        .emoji {
            font-size: 4rem;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

    <div id="contenedor">
        <div id="pantallaPregunta">
            <h1>¿Quieres ser mi San Valentín, Carito? ❤️</h1>
            <div class="botones">
                <button id="btnSi">SÍ</button>
                <button id="btnNo">No</button>
            </div>
        </div>

        <div id="mensajeFinal">
            <div class="emoji">🥰</div>
            <p class="texto-final">¡Gracias Carito, has hecho muy feliz a Willy! <br> <strong><3</strong></p>
        </div>
    </div>

    <script>
        const btnSi = document.getElementById('btnSi');
        const btnNo = document.getElementById('btnNo');
        const pantallaPregunta = document.getElementById('pantallaPregunta');
        const mensajeFinal = document.getElementById('mensajeFinal');

        let escalaSi = 1;
        let paddingSiV = 15;
        let paddingSiH = 30;
        let fontSizeSi = 1.2;

        // Función para mover el botón NO y agrandar el SÍ
        function moverNo() {
            // 1. Mover el botón "No" a una posición loca
            const x = Math.random() * (window.innerWidth - btnNo.offsetWidth);
            const y = Math.random() * (window.innerHeight - btnNo.offsetHeight);
            
            btnNo.style.position = 'absolute';
            btnNo.style.left = x + 'px';
            btnNo.style.top = y + 'px';

            // 2. Agrandar el botón "Sí"
            paddingSiV += 10;
            paddingSiH += 20;
            fontSizeSi += 0.5;

            btnSi.style.padding = `${paddingSiV}px ${paddingSiH}px`;
            btnSi.style.fontSize = `${fontSizeSi}rem`;
        }

        // Eventos para el botón NO (al pasar el mouse o tocar en móvil)
        btnNo.addEventListener('mouseover', moverNo);
        btnNo.addEventListener('touchstart', (e) => {
            e.preventDefault(); // Evita clics accidentales en móvil
            moverNo();
        });

        // Evento para el botón SÍ
        btnSi.addEventListener('click', () => {
            pantallaPregunta.style.display = 'none';
            mensajeFinal.style.display = 'block';
            lanzarConfeti();
        });

        // Pequeño extra: efecto de corazones al final
        function lanzarConfeti() {
            for(let i = 0; i < 30; i++) {
                const corazon = document.createElement('div');
                corazon.innerHTML = '❤️';
                corazon.style.position = 'fixed';
                corazon.style.left = Math.random() * 100 + 'vw';
                corazon.style.top = '-50px';
                corazon.style.fontSize = (Math.random() * 20 + 20) + 'px';
                corazon.style.animation = `caer ${Math.random() * 3 + 2}s linear forwards`;
                document.body.appendChild(corazon);
            }
        }

        // CSS dinámico para la animación de caída
        const styleSheet = document.createElement("style");
        styleSheet.innerText = `
            @keyframes caer {
                to {
                    transform: translateY(110vh) rotate(360deg);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(styleSheet);
    </script>
</body>
</html>

