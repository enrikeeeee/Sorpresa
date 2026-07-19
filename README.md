<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🎉 Feliz Cumpleaños Sariii 🎂</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, sans-serif;
    height:100vh;
    overflow:hidden;
    background:linear-gradient(135deg,#ff7eb3,#ff758c,#ffb199);
    display:flex;
    justify-content:center;
    align-items:center;
}

#sorpresa{
    display:none;
    background:white;
    padding:40px;
    border-radius:25px;
    max-width:550px;
    text-align:center;
    box-shadow:0 15px 40px rgba(0,0,0,.25);
    animation:aparecer .8s ease;
    z-index:10;
}

h1{
    color:#ff4081;
    margin-bottom:15px;
}

p{
    color:#555;
    font-size:1.2rem;
    line-height:1.6;
}

#inicio{
    text-align:center;
    z-index:10;
}

button{
    background:#ff4081;
    color:white;
    border:none;
    padding:18px 35px;
    font-size:1.2rem;
    border-radius:50px;
    cursor:pointer;
    transition:.3s;
    box-shadow:0 5px 15px rgba(0,0,0,.2);
}

button:hover{
    transform:scale(1.08);
}

@keyframes aparecer{
    from{
        opacity:0;
        transform:scale(.7);
    }
    to{
        opacity:1;
        transform:scale(1);
    }
}

canvas{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
}
</style>
</head>
<body>

<canvas id="confetti"></canvas>

<div id="inicio">
    <button onclick="mostrarSorpresa()">
        Abrir sorpresa 🎁
    </button>
</div>

<div id="sorpresa">
    <h1>🎉 ¡Feliz Cumpleaños Sariii! 🎂</h1>

    <p>
        Se te aprecia mucho ❤️
        <br><br>
        Que la pases de maravilla hoy, que disfrutes cada momento,
        que recibas muchas alegrías y que todos tus sueños sigan
        haciéndose realidad. ✨
        <br><br>
        ¡Espero que tengas un día increíble y lleno de sonrisas! 🥳🎈
    </p>
</div>

<script>
function mostrarSorpresa(){
    document.getElementById("inicio").style.display="none";
    document.getElementById("sorpresa").style.display="block";
}
</script>

<script>
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const pieces = [];

for(let i=0;i<200;i++){
    pieces.push({
        x: Math.random()*canvas.width,
        y: Math.random()*canvas.height,
        w: Math.random()*10+5,
        h: Math.random()*10+5,
        speed: Math.random()*3+2,
        color:`hsl(${Math.random()*360},100%,60%)`
    });
}

function animate(){
    ctx.clearRect(0,0,canvas.width,canvas.height);

    pieces.forEach(p=>{
        ctx.fillStyle=p.color;
        ctx.fillRect(p.x,p.y,p.w,p.h);

        p.y += p.speed;

        if(p.y > canvas.height){
            p.y = -10;
            p.x = Math.random()*canvas.width;
        }
    });

    requestAnimationFrame(animate);
}

animate();

window.addEventListener("resize",()=>{
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});
</script>

</body>
</html>
