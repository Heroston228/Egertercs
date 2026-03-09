<!DOCTYPE html>
<html lang="hu">
<head>
<meta charset="UTF-8">
<title>Egertercs 🍷</title>

<style>

body{
margin:0;
font-family:Arial,Helvetica,sans-serif;
height:100vh;
display:flex;
justify-content:center;
align-items:center;
color:white;
text-align:center;
overflow:hidden;
}

/* háttér */

.bg{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background-image:url("https://images.unsplash.com/photo-1506377247377-2a5b3b417ebb");
background-size:cover;
background-position:center;
filter:blur(8px) brightness(0.6);
transform:scale(1.1);
z-index:-1;
}

.container{
padding:40px;
}

/* NAGYOBB CÍM */

h1{
font-size:70px;
margin-bottom:40px;
letter-spacing:2px;
}

/* NAGYOBB COUNTDOWN */

#countdown{
font-size:80px;
font-weight:bold;
letter-spacing:4px;
}

.note{
margin-top:30px;
font-size:24px;
opacity:0.9;
}

@media (max-width:600px){

h1{
font-size:40px;
}

#countdown{
font-size:45px;
}

.note{
font-size:18px;
}

}

</style>
</head>

<body>

<div class="bg"></div>

<div class="container">

<h1>🍷 Egertercs 🍇</h1>

<div id="countdown">
<span id="days">0</span> nap •
<span id="hours">0</span> óra •
<span id="minutes">0</span> perc •
<span id="seconds">0</span> mp
</div>
<br>
</br>
<audio id="music" controls autoplay>
  <source src="music.mp3" type="audio/mpeg">
</audio>

</div>

<script>

const targetDate = new Date("2026-04-17T00:00:00").getTime();

const d = document.getElementById("days");
const h = document.getElementById("hours");
const m = document.getElementById("minutes");
const s = document.getElementById("seconds");

setInterval(()=>{

const now = new Date().getTime();
const diff = targetDate - now;

if(diff <= 0){

document.getElementById("countdown").innerHTML="🥂 Egertercs indul!";
return;

}

d.textContent = Math.floor(diff/(1000*60*60*24));
h.textContent = Math.floor((diff/(1000*60*60))%24);
m.textContent = Math.floor((diff/(1000*60))%60);
s.textContent = Math.floor((diff/1000)%60);

},1000);


const music = document.getElementById("music");
music.volume = 0.35;

function enableSound(){

music.muted=false;

document.removeEventListener("click",enableSound);
document.removeEventListener("touchstart",enableSound);

}

document.addEventListener("click",enableSound);
document.addEventListener("touchstart",enableSound);

</script>

</body>
</html>
