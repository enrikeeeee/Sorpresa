
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🎂 Feliz Cumpleaños Sariii 🎉</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial,sans-serif;
    background:linear-gradient(135deg,#ff7eb3,#ff758c,#ffb199);
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
}

canvas{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    z-index:1;
    pointer-events:none;
}

#sorpresa{
    display:none;
    background:white;
    padding:35px;
    border-radius:25px;
    width:90%;
    max-width:500px;
    box-shadow:0 15px 35px rgba(0,0,0,.25);
    animation:zoom .7s ease;
}

button{
    border:none;
    padding:18px 35px;
    border-radius:50px;
    background:#ff4081;
    color:white;
    font-size:1.2rem;
    cursor:pointer;
    box-shadow:0 8px 20px rgba(0,0,0,.2);
}

h1{
    color:#ff4081;
    margin-bottom:15px;
}

p{
    color:#555;
    line-height:1.7;
    font-size:1.1rem;
}

@keyframes zoom{
    from{
        opacity:0;
        transform:scale(.7);
    }
    to{
        opacity:1;
        transform:scale(1);
    }
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

function resize(){
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}

resize();

const confetti = [];

for(let i=0;i<150;i++){
    confetti.push({
        x:Math.random()*canvas.width,
        y:Math.random()*canvas.height,
        size:Math.random()*8+4,
        speed:Math.random()*3+1,
        color:`hsl(${Math.random()*360},100%,60%)`
    });
}

function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height);

    confetti.forEach(c=>{
        ctx.fillStyle=c.color;
        ctx.fillRect(c.x,c.y,c.size,c.size);

        c.y += c.speed;

        if(c.y > canvas.height){
            c.y = -10;
            c.x = Math.random()*canvas.width;
        }
    });

    requestAnimationFrame(draw);
}

draw();

window.addEventListener("resize", resize);
</script>

</body>
</html>
