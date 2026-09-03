<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Fondo 3D Agua</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    min-height:100vh;
    overflow:hidden;
    font-family:Arial, sans-serif;

    /* Fondo oscuro */
    background:
        radial-gradient(circle at 50% 50%,
            #123c4a 0%,
            #071b25 45%,
            #02080d 100%);

    color:white;
}


/* =========================================
   CAPA PRINCIPAL DEL AGUA
========================================= */

.agua{
    position:fixed;
    inset:-30%;
    z-index:-3;

    background:
        radial-gradient(
            ellipse at 20% 30%,
            rgba(0,180,210,.28),
            transparent 30%
        ),

        radial-gradient(
            ellipse at 80% 70%,
            rgba(20,100,150,.30),
            transparent 35%
        ),

        radial-gradient(
            ellipse at 50% 50%,
            rgba(0,255,220,.12),
            transparent 40%
        );

    filter:blur(25px);

    animation:
        moverAgua 18s ease-in-out infinite alternate;
}


/* =========================================
   MANCHAS TIPO ACEITE
========================================= */

.aceite{
    position:fixed;
    width:70vw;
    height:70vw;

    border-radius:50%;

    background:
        conic-gradient(
            from 0deg,
            rgba(0,255,255,.10),
            rgba(80,0,255,.12),
            rgba(0,255,180,.13),
            rgba(0,100,255,.12),
            rgba(0,255,255,.10)
        );

    filter:blur(35px);

    opacity:.7;

    z-index:-2;

    animation:
        aceiteMovimiento 25s ease-in-out infinite alternate;
}


/* Posiciones de las manchas */

.aceite:nth-child(2){
    top:-25%;
    left:-20%;
}

.aceite:nth-child(3){
    bottom:-30%;
    right:-20%;

    width:60vw;
    height:60vw;

    animation-delay:-8s;
}

.aceite:nth-child(4){
    top:20%;
    left:40%;

    width:35vw;
    height:35vw;

    opacity:.35;

    animation-delay:-14s;
}


/* =========================================
   ONDAS DEL AGUA
========================================= */

.ondas{
    position:fixed;
    inset:-10%;

    z-index:-1;

    opacity:.45;

    background:

        repeating-radial-gradient(
            ellipse at 30% 40%,
            transparent 0px,
            transparent 35px,
            rgba(120,230,255,.08) 37px,
            transparent 42px,
            transparent 80px
        );

    filter:
        blur(2px)
        contrast(120%);

    animation:
        ondasMovimiento 22s linear infinite;
}


/* Segunda capa de ondas */

.ondas2{
    position:fixed;
    inset:-20%;

    z-index:-1;

    opacity:.3;

    background:

        repeating-radial-gradient(
            ellipse at 70% 60%,
            transparent 0px,
            transparent 55px,
            rgba(0,255,220,.07) 58px,
            transparent 65px,
            transparent 110px
        );

    filter:blur(3px);

    animation:
        ondasMovimiento2 30s linear infinite;
}


/* =========================================
   EFECTO DE PROFUNDIDAD 3D
========================================= */

.profundidad{
    position:fixed;
    inset:0;

    z-index:-1;

    background:

        radial-gradient(
            ellipse at center,
            transparent 25%,
            rgba(0,0,0,.18) 60%,
            rgba(0,0,0,.65) 100%
        );

    pointer-events:none;
}


/* =========================================
   ANIMACIONES
========================================= */

@keyframes moverAgua{

    0%{
        transform:
            translate3d(-5%, -3%, 0)
            scale(1);
    }

    50%{
        transform:
            translate3d(4%, 5%, 0)
            scale(1.08);
    }

    100%{
        transform:
            translate3d(-3%, 2%, 0)
            scale(1.03);
    }
}


@keyframes aceiteMovimiento{

    0%{
        transform:
            translate3d(-8%, -5%, 0)
            rotate(0deg)
            scale(1);
    }

    50%{
        transform:
            translate3d(10%, 8%, 0)
            rotate(120deg)
            scale(1.15);
    }

    100%{
        transform:
            translate3d(-5%, 10%, 0)
            rotate(240deg)
            scale(.95);
    }
}


@keyframes ondasMovimiento{

    from{
        transform:
            translate(-5%, -5%)
            rotate(0deg)
            scale(1);
    }

    to{
        transform:
            translate(5%, 5%)
            rotate(360deg)
            scale(1.08);
    }
}


@keyframes ondasMovimiento2{

    from{
        transform:
            translate(5%, 0%)
            rotate(360deg)
            scale(1.1);
    }

    to{
        transform:
            translate(-5%, 5%)
            rotate(0deg)
            scale(1);
    }
}


/* =========================================
   CONTENIDO DE EJEMPLO
========================================= */

.contenido{
    min-height:100vh;

    display:flex;
    flex-direction:column;

    align-items:center;
    justify-content:center;

    text-align:center;

    padding:30px;

    /* Hace que el texto destaque */
    text-shadow:
        0 2px 10px rgba(0,0,0,.9),
        0 0 20px rgba(0,0,0,.6);
}

.contenido h1{
    font-size:clamp(40px,7vw,90px);

    letter-spacing:3px;

    margin-bottom:15px;
}

.contenido p{
    font-size:clamp(16px,2vw,23px);

    max-width:700px;

    line-height:1.6;

    color:#dffaff;
}

</style>
</head>

<body>

<!-- AGUA -->
<div class="agua"></div>

<!-- MANCHAS DE ACEITE -->
<div class="aceite"></div>
<div class="aceite"></div>
<div class="aceite"></div>

<!-- ONDAS -->
<div class="ondas"></div>
<div class="ondas2"></div>

<!-- PROFUNDIDAD -->
<div class="profundidad"></div>


<!--
    PUEDES BORRAR ESTE CONTENIDO
    Y PONER AQUÍ TU JUEGO / PÁGINA
-->

<div class="contenido">


</div>

</body>
</html>
