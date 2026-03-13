<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>mensaje</title>

<style>

body{
margin:0;
font-family:Arial;
text-align:center;
background:#0f172a;
color:white;
overflow:hidden;
}

button{
padding:14px 26px;
font-size:18px;
border:none;
border-radius:8px;
background:#2563eb;
color:white;
cursor:pointer;
}

#inicio{
margin-top:120px;
}

#carta{
display:none;
width:70%;
margin:auto;
margin-top:40px;
font-size:22px;
line-height:1.7;
}

#secretoBtn{
display:none;
margin-top:40px;
}

#panelSecreto{
display:none;
margin-top:40px;
}

input{
padding:10px;
font-size:18px;
}

canvas{
position:fixed;
top:0;
left:0;
z-index:-1;
display:none;
}

#terminal{
display:none;
width:75%;
margin:auto;
margin-top:70px;
background:black;
color:#00ff9c;
padding:30px;
font-family:monospace;
text-align:left;
font-size:20px;
border:2px solid #00ff9c;
box-shadow:0 0 25px #00ff9c;
}

</style>
</head>

<body>

<canvas id="matrix"></canvas>

<div id="inicio">

<h1>Un pequeño mensaje</h1>

<button onclick="abrirCarta()">Abrir carta</button>

</div>

<div id="carta">

<p>

Hola papa.

Quise escribir algo diferente,
algo que no fuera solo palabras
sino algo hecho con código.

Me gusta que sear programador
porque cuando pienso en código
pienso en ideas,
en soluciones
y en personas que crean cosas desde cero.

A veces imagino que cada línea de código
es como una instrucción para construir algo nuevo.

Si el mundo fuera un programa
yo escribiría una variable llamada papa
y dentro guardaría muchas cosas buenas.

Porque papa también puede ser
const papa = ejemplo;
const papa = enseñanza;
const papa = aprender;
const papa = seguir intentando.

Y si esto fuera un programa de verdad
tal vez escribiría algo como:

while(aprendiendo){
recordar(papa);
}

Porque aprender algo nuevo
siempre empieza con una idea,
y muchas veces esas ideas
empiezan viendo a alguien que sabe crear.

</p>

</div>

<div id="secretoBtn">

<button onclick="abrirSecreto()">Secreto</button>

</div>

<div id="panelSecreto">

<h2>Modo secreto</h2>

<p>Introduce la contraseña</p>

<input id="pass">

<button onclick="verificar()">Entrar</button>

</div>

<div id="terminal">

<div id="texto"></div>

</div>

<script>

function abrirCarta(){

document.getElementById("inicio").style.display="none";
document.getElementById("carta").style.display="block";

setTimeout(()=>{
document.getElementById("secretoBtn").style.display="block";
},30000);

}

function abrirSecreto(){

document.getElementById("panelSecreto").style.display="block";

}

function verificar(){

let p=document.getElementById("pass").value;

if(p=="papa"){

modoHacker();

}else{

alert("contraseña incorrecta");

}

}

function modoHacker(){

document.getElementById("panelSecreto").style.display="none";
document.getElementById("carta").style.display="none";
document.getElementById("secretoBtn").style.display="none";

document.getElementById("terminal").style.display="block";
document.getElementById("matrix").style.display="block";

escribir();

}


/* MATRIX */

let canvas=document.getElementById("matrix");
let ctx=canvas.getContext("2d");

canvas.height=window.innerHeight;
canvas.width=window.innerWidth;

let letras="01ABCDEFGHIJKLMNOPQRSTUVWXYZ";
letras=letras.split("");

let fontSize=16;
let columnas=canvas.width/fontSize;

let drops=[];

for(let x=0;x<columnas;x++){
drops[x]=1;
}

function draw(){

ctx.fillStyle="rgba(0,0,0,0.05)";
ctx.fillRect(0,0,canvas.width,canvas.height);

ctx.fillStyle="#00ff9c";
ctx.font=fontSize+"px monospace";

for(let i=0;i<drops.length;i++){

let text=letras[Math.floor(Math.random()*letras.length)];

ctx.fillText(text,i*fontSize,drops[i]*fontSize);

if(drops[i]*fontSize>canvas.height && Math.random()>0.975){
drops[i]=0;
}

drops[i]++;

}

}

setInterval(draw,33);


/* MENSAJE SECRETO */

let mensaje=`user@system:~$ abrir mensaje_secreto.txt

Cargando sistema...
Accediendo a archivos...
Archivo encontrado.

Hola papa.

Este pequeño mensaje escondido dentro del sistema
es como una carpeta secreta dentro de un programa.
A veces los programas tienen partes visibles
y partes que solo aparecen cuando alguien sabe dónde mirar.

Quise que este mensaje fuera algo parecido.
Un pequeño archivo escondido dentro del código.

Tal vez todavía estoy empezando a aprender,
pero cada cosa nueva que intento entender
me hace pensar que programar es como construir ideas.

Escribir código es como escribir instrucciones
para crear algo que antes no existía.

Y si este pequeño proyecto fuera un repositorio,
entonces una de las líneas más importantes sería esta:

variable_importante = papa

Porque algunas cosas no se guardan solo en memoria,
sino también en las ideas que ayudan a seguir aprendiendo.


Fin del archivo.


Nuevo mensaje cargado...

Si algún día llego a crear programas más grandes,
juegos, sistemas o proyectos importantes,
seguramente recordaré este pequeño experimento.

Porque todo empieza con algo pequeño,
una idea,
una línea de código,
o una página sencilla como esta.

Tal vez esto solo sea HTML,
pero también es una forma de decir
que aprender a crear cosas es algo que vale la pena.

Gracias por las enseñanzas
que ayudan a entender cómo pensar,
cómo resolver problemas
y cómo seguir intentando cuando algo no funciona.

Cerrando archivo.

`;

let i=0;

function escribir(){

let area=document.getElementById("texto");

if(i<mensaje.length){

area.innerHTML+=mensaje.charAt(i);

i++;

setTimeout(escribir,28);

}

}

</script>

</body>
</html>
