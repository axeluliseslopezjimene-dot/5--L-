<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CBTis 205 | José Vasconcelos</title>

    <style>
        :root {
            --color-guinda: #691c32;
            --color-guinda-oscuro: #4a1222;
            --color-dorado: #b38e5d;
            --color-dorado-claro: #d4af37;
            --color-fondo: #f8f9fa;
            --color-texto: #2b2b2b;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: var(--color-fondo);
            color: var(--color-texto);
            line-height: 1.6;
        }

        header {
            background: white;
            padding: 20px 6%;
            display: flex;
            align-items: center;
            gap: 18px;
            border-bottom: 5px solid var(--color-dorado);
        }

        /* Contenedor interactivo del Logo */
        .logo-box {
            width: 95px;
            height: 95px;
            min-width: 95px;
            border-radius: 8px;
            border: none;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            background: transparent;
            cursor: pointer;
            position: relative;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .logo-box:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 10px rgba(105, 28, 50, 0.2);
            border-style: solid;
        }

        .logo-box::after {
            content: "Cambiar";
            position: absolute;
            bottom: 0;
            width: 100%;
            background: rgba(105, 28, 50, 0.9);
            color: white;
            font-size: 9px;
            text-align: center;
            padding: 1px 0;
            opacity: 0;
            transition: opacity 0.2s;
        }

        .logo-box:hover::after {
            opacity: 1;
        }

        .logo-img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        header h1 {
            color: var(--color-guinda);
            font-size: 23px;
        }

        header p {
            color: #64748b;
        }

        nav {
            background: var(--color-guinda);
            padding: 0 5%;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        nav ul {
            list-style: none;
            display: flex;
            flex-wrap: wrap;
        }

        nav a {
            display: block;
            color: white;
            padding: 15px 12px;
            text-decoration: none;
            font-size: 14px;
        }

        nav a:hover {
            background: var(--color-guinda-oscuro);
            color: var(--color-dorado);
        }

        .hero {
            background:
                linear-gradient(100deg,
                rgba(74, 18, 34, 0.92),
                rgba(105, 28, 50, 0.75)),
                url("https://images.unsplash.com/photo-1523050854058-8df90110c9f1?auto=format&fit=crop&w=1600&q=80");

            background-size: cover;
            background-position: center;
            color: white;
            padding: 90px 7%;
        }

        .hero h2 {
            font-size: clamp(30px, 5vw, 48px);
            max-width: 750px;
            line-height: 1.2;
            margin-bottom: 18px;
        }

        .hero p {
            max-width: 700px;
            font-size: 18px;
            margin-bottom: 25px;
        }

        .boton {
            display: inline-block;
            background: var(--color-dorado);
            color: white;
            padding: 12px 18px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: bold;
            margin: 5px 5px 5px 0;
            border: none;
            cursor: pointer;
        }

        .boton:hover {
            background: var(--color-dorado-claro);
        }

        main {
            max-width: 1200px;
            margin: auto;
            padding: 35px 20px;
        }

        section {
            scroll-margin-top: 80px;
            margin-bottom: 40px;
        }

        section h2 {
            color: var(--color-guinda);
            font-size: 28px;
            margin-bottom: 8px;
        }

        .subtitulo {
            color: #64748b;
            margin-bottom: 22px;
        }

        .accesos, .tarjetas {
            display: grid;
            grid-template-columns: repeat(3, minmax(0, 1fr));
            gap: 20px;
        }

        .accesos {
            grid-template-columns: repeat(4, minmax(0, 1fr));
        }

        .acceso, .tarjeta {
            background: white;
            border: 1px solid #dce4ee;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 14px #0000000d;
        }

        .acceso {
            text-align: center;
            padding: 20px 10px;
            color: var(--color-guinda);
            text-decoration: none;
            font-weight: bold;
        }

        .acceso span {
            display: block;
            font-size: 32px;
            margin-bottom: 8px;
        }

        .acceso:hover {
            background: #fdf6f0;
        }

        .imagen {
            background: linear-gradient(135deg, var(--color-guinda), var(--color-dorado));
            color: white;
            text-align: center;
            padding: 35px 10px;
            font-size: 45px;
        }

        .contenido {
            padding: 20px;
        }

        .contenido h3 {
            color: var(--color-guinda);
            margin-bottom: 10px;
        }

        .contenido p {
            margin-bottom: 14px;
        }

        .contenido a {
            color: var(--color-guinda);
            font-weight: bold;
        }

        .aviso {
            background: white;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 5px solid var(--color-guinda);
            border-radius: 5px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }

        .aviso h3 {
            color: var(--color-guinda);
            margin-bottom: 8px;
        }

        .buscador {
            width: 100%;
            padding: 13px;
            margin: 10px 0 15px;
            border: 1px solid #bdcbdc;
            border-radius: 6px;
            font-size: 16px;
        }

        /* Estilos de Tabla tipo Base de Datos */
        .tabla-db-container {
            overflow-x: auto;
            margin-top: 20px;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
        }

        .tabla-db {
            width: 100%;
            border-collapse: collapse;
            background: white;
            text-align: left;
            font-size: 14px;
        }

        .tabla-db th {
            background: var(--color-guinda);
            color: white;
            padding: 12px;
            font-weight: bold;
        }

        .tabla-db td {
            padding: 12px;
            border-bottom: 1px solid #e2e8f0;
        }

        .tabla-db tr:nth-child(even) {
            background-color: #fcf8f5;
        }

        .badge-pendiente {
            background: #fef3c7;
            color: #92400e;
            padding: 4px 8px;
            border-radius: 4px;
            font-weight: bold;
            font-size: 12px;
        }

        footer {
            background: var(--color-guinda-oscuro);
            color: white;
            padding: 35px 6% 15px;
            border-top: 4px solid var(--color-dorado);
        }

        .pie {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr;
            gap: 25px;
            margin-bottom: 25px;
        }

        footer h3 {
            margin-bottom: 12px;
            color: var(--color-dorado);
        }

        footer p {
            margin-bottom: 8px;
        }

        footer a {
            color: #e7eef7;
        }

        .copyright {
            text-align: center;
            border-top: 1px solid #ffffff30;
            padding-top: 15px;
            font-size: 14px;
        }

        @media (max-width: 800px) {
            header h1 {
                font-size: 17px;
            }

            nav ul {
                justify-content: center;
            }

            .accesos, .tarjetas {
                grid-template-columns: repeat(2, 1fr);
            }

            .pie {
                grid-template-columns: 1fr 1fr;
            }
        }

        @media (max-width: 520px) {
            header {
                padding: 14px;
                gap: 10px;
            }

            .logo-box {
                width: 65px;
                height: 65px;
                min-width: 65px;
            }

            .tarjetas {
                grid-template-columns: 1fr;
            }

            .pie {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>

<body>

    <header>
        <!-- Cuadro del logo interactivo -->
        <div class="logo-box" onclick="document.getElementById('inputLogo').click();">
            <img id="imgLogoHeader" class="logo-img" src="data:image/png;base64,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
