# jaiclub1
https://github.com/dream003job-star/jaiclub1.git<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>JaiClub Demo</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial, sans-serif;
}

body{
background:linear-gradient(135deg,#111,#222);
color:white;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.container{
width:400px;
background:#1e1e1e;
padding:25px;
border-radius:20px;
box-shadow:0 0 20px rgba(0,255,255,.3);
text-align:center;
}

h1{
margin-bottom:15px;
color:#00ffff;
}

.balance{
font-size:22px;
margin-bottom:20px;
}

.colors{
display:flex;
gap:10px;
margin-bottom:20px;
}

.btn{
flex:1;
padding:15px;
border:none;
border-radius:12px;
font-size:18px;
font-weight:bold;
cursor:pointer;
}

.red{
background:#ff3b3b;
color:white;
}

.green{
background:#00c853;
color:white;
}

.violet{
background:#9c27b0;
color:white;
}

input{
width:100%;
padding:12px;
border-radius:10px;
border:none;
margin-bottom:15px;
font-size:18px;
}

.play{
width:100%;
padding:15px;
border:none;
border-radius:12px;
background:#00ffff;
font-size:18px;
font-weight:bold;
cursor:pointer;
}

.result{
margin-top:20px;
font-size:22px;
font-weight:bold;
}

.history{
margin-top:20px;
display:flex;
justify-content:center;
gap:8px;
flex-wrap:wrap;
}

.circle{
width:25px;
height:25px;
border-radius:50%;
}
</style>
</head>
<body>

<div class="container">

<h1>JaiClub Demo</h1>

<div class="balance">
Balance: <span id="balance">1000</span> Coins
</div>

<div class="colors">
<button class="btn red" onclick="selectColor('red')">Red</button>
<button class="btn green" onclick="selectColor('green')">Green</button>
<button class="btn violet" onclick="selectColor('violet')">Violet</button>
</div>

<input type="number" id="bet" placeholder="Enter Bet Amount">

<button class="play" onclick="playGame()">
Play Round
</button>

<div class="result" id="result">
Choose a color
</div>

<div class="history" id="history"></div>

</div>

<script>

let selectedColor=null;

let balance=localStorage.getItem("balance")
? parseInt(localStorage.getItem("balance"))
:1000;

document.getElementById("balance").innerText=balance;

function selectColor(color){
selectedColor=color;
document.getElementById("result").innerText=
"Selected: "+color.toUpperCase();
}

function playGame(){

let bet=parseInt(document.getElementById("bet").value);

if(!selectedColor){
alert("Select a color");
return;
}

if(!bet || bet<=0){
alert("Enter valid bet");
return;
}

if(bet>balance){
alert("Insufficient balance");
return;
}

const colors=["red","green","violet"];
const result=colors[Math.floor(Math.random()*3)];

let msg="";

if(result===selectedColor){
balance += bet;
msg="🎉 WIN! Result: "+result;
}
else{
balance -= bet;
msg="❌ LOSS! Result: "+result;
}

document.getElementById("result").innerText=msg;

document.getElementById("balance").innerText=balance;

localStorage.setItem("balance",balance);

const dot=document.createElement("div");
dot.classList.add("circle");
dot.style.background=result;

document.getElementById("history").prepend(dot);
}

</script>

</body>
</html>
