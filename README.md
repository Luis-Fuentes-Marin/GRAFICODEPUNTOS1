<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Puntos en Movimiento</title>
    <style>
        body {
            text-align: center;
            font-family: Arial;
        }

        canvas {
            border: 2px solid black;
            margin-top: 20px;
        }
    </style>
</head>
<body>

<h2>Gráfico de Puntos en Movimiento</h2>
<h2>HECHO POR: LUIS EDWIN FUENTES MARIN</h2>

<canvas id="lienzo" width="400" height="300"></canvas>

<script>
    const canvas = document.getElementById("lienzo");
    const ctx = canvas.getContext("2d");

    const cantidadPuntos = 5;
    let puntos = [];

    // Crear puntos iniciales
    function inicializarPuntos() {
        puntos = [];
        for (let i = 0; i < cantidadPuntos; i++) {
            puntos.push({
                x: Math.random() * canvas.width,
                y: Math.random() * canvas.height
            });
        }
    }

    // Dibujar puntos
    function dibujarPuntos() {
        puntos.forEach(p => {
            ctx.beginPath();
            ctx.arc(p.x, p.y, 5, 0, Math.PI * 2);
            ctx.fillStyle = "blue";
            ctx.fill();
        });
    }

    // Actualizar posiciones
    function actualizarPuntos() {
        puntos.forEach(p => {
            p.x = Math.random() * canvas.width;
            p.y = Math.random() * canvas.height;
        });
    }

    // Animación
    function animar() {
        ctx.clearRect(0, 0, canvas.width, canvas.height); // limpiar
        actualizarPuntos();
        dibujarPuntos();
    }

    // Inicializar y ejecutar cada segundo
    inicializarPuntos();
    setInterval(animar, 1000);
</script>

</body>
</html>
