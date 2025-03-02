<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blog de Notas para Programar</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 20px;
            transition: background-color 0.3s, color 0.3s;
            overflow: hidden;
        }
        .dark-mode {
            background-color: #1e1e1e;
            color: #ffffff;
        }
        .light-mode {
            background-color: #ffffff;
            color: #000000;
        }
        .pink-mode {
            background-color: #ffccff;
            color: #660066;
        }
        .blue-mode {
            background-color: #cce5ff;
            color: #003366;
        }
        .welcome-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0, 0, 0, 0.9);
            color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 1000;
            width: 300px;
            text-align: center;
        }
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: block;
            z-index: 999;
        }
        .btn {
            margin: 5px;
            padding: 12px 20px;
            font-size: 16px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease-in-out;
        }
        .btn-primary {
            background-color: #007acc;
            color: #ffffff;
        }
        .btn-primary:hover {
            background-color: #005f99;
            transform: scale(1.1);
        }
        textarea {
            width: 90%;
            height: 400px;
            border: none;
            padding: 10px;
            font-size: 16px;
            font-family: monospace;
            border-radius: 8px;
        }
    </style>
</head>
<body class="dark-mode">
    <div class="overlay" id="overlay"></div>
    <div id="welcome" class="welcome-message">
        <h2>¡Bienvenido a SantiCode Notes!</h2>
        <p>Aquí puedes escribir y guardar tus notas de programación de forma sencilla.</p>
        <button class="btn btn-primary" onclick="cerrarMensaje()">Cerrar</button>
    </div>
    
    <h1>Blog de Notas para Programación</h1>
    <button class="btn btn-primary" onclick="toggleTheme()">Cambiar Tema</button>
    <button class="btn btn-primary" onclick="guardarTexto()">Guardar</button>
    <br><br>
    <textarea id="editor" placeholder="Escribe tu código aquí..."></textarea>
    <br>
    <script>
        function cerrarMensaje() {
            document.getElementById("welcome").style.display = "none";
            document.getElementById("overlay").style.display = "none";
        }
        
        function guardarTexto() {
            let text = document.getElementById("editor").value;
            let blob = new Blob([text], { type: "text/plain" });
            let a = document.createElement("a");
            a.href = URL.createObjectURL(blob);
            a.download = "nota.txt";
            a.click();
        }
        
        function toggleTheme() {
            let body = document.body;
            if (body.classList.contains("dark-mode")) {
                body.classList.remove("dark-mode");
                body.classList.add("light-mode");
            } else if (body.classList.contains("light-mode")) {
                body.classList.remove("light-mode");
                body.classList.add("pink-mode");
            } else if (body.classList.contains("pink-mode")) {
                body.classList.remove("pink-mode");
                body.classList.add("blue-mode");
            } else {
                body.classList.remove("blue-mode");
                body.classList.add("dark-mode");
            }
        }
        
        document.addEventListener("DOMContentLoaded", function() {
            document.getElementById("editor").value = `<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Página</title>
</head>
<body>
    <h1>Hola, mundo</h1>
</body>
</html>`;
        });
    </script>
</body>
</html>
