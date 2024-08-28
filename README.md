<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Efecto de Hackeo</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: black;
            color: green;
            font-family: monospace;
        }
        #cmd-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: green;
            text-align: center;
            display: none; /* Oculta el mensaje de CMD por defecto */
        }
        .matrix {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none; /* Evita que el cursor interfiera */
            display: none; /* Oculta el efecto de Matrix por defecto */
        }
        .matrix-line {
            position: absolute;
            white-space: nowrap;
            opacity: 0.8;
            animation: fall linear infinite;
        }
        @keyframes fall {
            from { top: -100%; }
            to { top: 100%; }
        }
        #message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            text-align: center;
            display: none; /* Oculta el mensaje por defecto */
        }
    </style>
</head>
<body>
    <div id="cmd-message">
        <h1>Cargando...</h1>
        <p>Iniciando sistema...</p>
    </div>
    <div class="matrix" id="matrix"></div>
    <div id="message">
        <h1>¡Cuidado!</h1>
        <p>Esto puede ocurrir si no te pones las pilas...</p>
    </div>
    <script>
        // Mostrar el mensaje de CMD inicialmente
        const cmdMessage = document.getElementById('cmd-message');
        cmdMessage.style.display = 'block';

        // Mostrar el efecto Matrix después de 5 segundos
        setTimeout(() => {
            cmdMessage.style.display = 'none'; // Ocultar el mensaje de CMD
            const matrix = document.getElementById('matrix');
            matrix.style.display = 'block'; // Mostrar el efecto de Matrix

            // Generar el efecto Matrix
            for (let i = 0; i < 100; i++) {
                const line = document.createElement('div');
                line.className = 'matrix-line';
                line.style.left = Math.random() * 100 + 'vw';
                line.style.fontSize = Math.random() * 20 + 'px';
                line.style.animationDuration = (Math.random() * 2 + 1) + 's';
                line.textContent = Array.from({ length: 100 }, () => String.fromCharCode(Math.random() * 122)).join('');
                matrix.appendChild(line);
            }

            // Mostrar el mensaje después de otros 5 segundos
            setTimeout(() => {
                document.getElementById('message').style.display = 'block';
            }, 5000); // 5000 milisegundos = 5 segundos

        }, 5000); // 5000 milisegundos = 5 segundos
    </script>
</body>
</html>
