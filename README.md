<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GameMaster 3D</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#07051b;color:#fff;font-family:Arial,sans-serif}
header{background:#090720;border-bottom:1px solid #30246d;padding:15px;display:flex;align-items:center;gap:15px;position:sticky;top:0;z-index:10}
.logo{font-size:27px;font-weight:bold;font-style:italic}.logo span{color:#36bdf5}
.balance{margin-left:auto;border:1px solid #44349a;border-radius:15px;padding:8px 14px}
.balance b{color:#ffd21c}
button{border:0;border-radius:9px;padding:11px 18px;font-weight:bold;cursor:pointer}
.purple{background:#7624ff;color:white}.yellow{background:#ffd21c;color:#111}
.green{background:#25c84b;color:white}.blue{background:#087cff;color:white}
.container{max-width:1200px;margin:auto;padding:18px}
.hero{display:grid;grid-template-columns:2fr 1fr;gap:12px}
.box{background:linear-gradient(145deg,#17134a,#0d0928);border:1px solid #3b2a91;border-radius:17px;padding:25px}
.heroMain{min-height:235px;background:radial-gradient(circle at 75%,#5c13bc,#17105a 45%,#0d0829)}
h1{font-size:40px;margin:0 0 5px}
h2{margin-top:5px}.yellowText{color:#ffd21c}
p{line-height:1.5;color:#ddd}
.quick,.cards{display:grid;grid-template-columns:repeat(6,1fr);gap:10px;margin:14px 0}
.quick div,.card{background:#11102f;border:1px solid #3c2d91;border-radius:13px;text-align:center;padding:14px}
.quick div{cursor:pointer}.quick span{display:block;font-size:32px;margin-bottom:7px}
.card{padding:0;overflow:hidden}.icon{height:110px;display:flex;align-items:center;justify-content:center;font-size:55px;background:linear-gradient(145deg,#302078,#0d0928)}
.card b{display:block;padding:8px}.card p{margin:3px 0 10px}
.section{margin-top:15px}.title{display:flex;justify-content:space-between;align-items:center}
.view{background:#25165e;color:white;border-radius:18px}
.promos{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:15px}
.number{background:#ffd21c;color:#111;font-size:23px;font-weight:bold;text-align:center;padding:9px;border-radius:8px}
.modal{display:none;position:fixed;inset:0;background:#000c;z-index:50;align-items:center;justify-content:center;padding:15px}
.modal.show{display:flex}.modalBox{background:#100c31;border:1px solid #5034c0;border-radius:18px;padding:22px;width:min(460px,100%)}
.close{float:right;background:none;color:white;font-size:25px;padding:0}
.input{width:100%;padding:13px;margin:6px 0;background:#080622;color:white;border:1px solid #3d2e8d;border-radius:8px}
.row{display:flex;gap:8px}.row>*{flex:1}
.plan{border:1px solid #4530a0;background:#17114b;padding:13px;border-radius:10px;margin:9px 0}
.plan strong{color:#ffd21c}
.bottom{display:none}
@media(max-width:850px){
.hero{grid-template-columns:1fr}.quick,.cards{grid-template-columns:repeat(3,1fr)}
.promos{grid-template-columns:1fr}
}
@media(max-width:500px){
.container{padding:10px}.logo{font-size:21px}
.quick,.cards{grid-template-columns:repeat(2,1fr)}
.bottom{display:grid;position:fixed;bottom:0;left:0;right:0;background:#0c0925;border-top:1px solid #342676;grid-template-columns:repeat(5,1fr);z-index:20}
.bottom button{background:none;color:white;font-size:11px;padding:8px}
.bottom span{display:block;font-size:20px}
body{padding-bottom:60px}h1{font-size:32px}
}
</style>
</head>

<body>

<header>
<div class="logo">♛ GameMaster<span>3D</span></div>
<div class="balance">🪙 Balance: <b id="balance">50,000</b></div>
<button class="green" onclick="wallet()">+</button>
</header>

<div class="container">

<section class="hero">
<div class="box heroMain">
<h1>Play & Win</h1>
<h2 class="yellowText">Amazing Rewards</h2>
<p>Welcome to GameMaster 3D. Create your account, explore games and collect virtual rewards.</p>
<button class="purple" onclick="login()">Login</button>
<button class="yellow" onclick="register()">Create Account</button>
</div>

<div class="box">
<h2>🎁 Daily Bonus</h2>
<p>Claim your daily virtual coin bonus.</p>
<button class="yellow" style="width:100%" onclick="bonus()">Claim Now</button>
</div>
</section>

<div class="quick">
<div onclick="bonus()"><span>🎁</span>Daily Bonus</div>
<div onclick="gamesScroll()"><span>🎮</span>Games</div>
<div onclick="rewards()"><span>👑</span>VIP Rewards</div>
<div onclick="invite()"><span>👥</span>Invite & Earn</div>
<div onclick="wallet()"><span>💳</span>Wallet</div>
<div onclick="support()"><span>💬</span>Support</div>
</div>

<section class="section">
<div class="title"><h2>Popular Games</h2><button class="view">View All</button></div>
<div class="cards" id="games">
<div class="card" onclick="game('Aviator')"><div class="icon">✈️</div><b>Aviator</b></div>
<div class="card" onclick="game('Dragon Tiger')"><div class="icon">🐉</div><b>Dragon Tiger</b></div>
<div class="card" onclick="game('Roulette')"><div class="icon">🎰</div><b>Roulette</b></div>
<div class="card" onclick="game('Lucky Card')"><div class="icon">🃏</div><b>Lucky Card</b></div>
<div class="card" onclick="game('Mines')"><div class="icon">💣</div><b>Mines</b></div>
<div class="card" onclick="game('Lucky Wheel')"><div class="icon">🎡</div><b>Lucky Wheel</b></div>
</div>
</section>

<section class="section">
<div class="title"><h2>Rewards</h2><button class="view" onclick="rewards()">View All</button></div>
<div class="cards">
<div class="card"><div class="icon">📱</div><b>iPhone</b><p>🪙 1,250,000</p></div>
<div class="card"><div class="icon">💻</div><b>MacBook</b><p>🪙 1,800,000</p></div>
<div class="card"><div class="icon">🎧</div><b>AirPods</b><p>🪙 450,000</p></div>
<div class="card"><div class="icon">⌚</div><b>Smart Watch</b><p>🪙 350,000</p></div>
<div class="card"><div class="icon">🎁</div><b>Gift Box</b><p>🪙 100,000</p></div>
<div class="card"><div class="icon">🪙</div><b>Gold Coin</b><p>🪙 120,000</p></div>
</div>
</section>

<section class="promos">
<div class="box">
<h2>🎁 Refer & Earn</h2>
<p>Invite friends and earn virtual coins.</p>
<button class="blue" onclick="invite()">Invite Now</button>
</div>

<div class="box">
<h2>Payment Contact</h2>
<p>JazzCash — Ashfaq Sadiq</p>
<div class="number">0308 1724110</div>
</div>

<div class="box">
<h2>💬 Customer Support</h2>
<p>Contact us on WhatsApp.</p>
<button class="green" onclick="support()">WhatsApp</button>
</div>
</section>

</div>

<nav class="bottom">
<button>⌂<br>Home</button>
<button onclick="gamesScroll()">🎮<br>Games</button>
<button onclick="rewards()">🎁<br>Rewards</button>
<button onclick="wallet()">💳<br>Wallet</button>
<button onclick="login()">👤<br>Account</button>
</nav>

<div class="modal" id="modal">
<div class="modalBox" id="modalBox"></div>
</div>

<script>
let balance=Number(localStorage.getItem("balance")||50000);
let account=JSON.parse(localStorage.getItem("account")||"null");

const modal=document.getElementById("modal");
const box=document.getElementById("modalBox");

function update(){
document.getElementById("balance").textContent=balance.toLocaleString();
localStorage.setItem("balance",balance);
}

function openBox(html){
box.innerHTML=html;
modal.classList.add("show");
}

function closeBox(){
modal.classList.remove("show");
}

modal.onclick=function(e){
if(e.target===modal)closeBox();
};

function register(){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>✨ Create Account</h2>
<input class="input" id="name" placeholder="Full Name">
<input class="input" id="phone" placeholder="Mobile Number">
<input class="input" id="password" type="password" placeholder="Password">
<button class="yellow" style="width:100%" onclick="createAccount()">Create Account</button>
`);
}

function createAccount(){
let name=document.getElementById("name").value.trim();
let phone=document.getElementById("phone").value.trim();
let password=document.getElementById("password").value;

if(!name||!phone||!password){
alert("Please complete all fields.");
return;
}

account={name,phone,password};
localStorage.setItem("account",JSON.stringify(account));
alert("Account created successfully!");
closeBox();
}

function login(){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>🔐 Account Login</h2>
<input class="input" id="loginPhone" placeholder="Mobile Number">
<input class="input" id="loginPassword" type="password" placeholder="Password">
<button class="purple" style="width:100%" onclick="doLogin()">Login</button>
`);
}

function doLogin(){
let p=document.getElementById("loginPhone").value;
let pass=document.getElementById("loginPassword").value;

if(!account){
alert("Please create an account first.");
return;
}

if(p===account.phone && pass===account.password){
alert("Welcome, "+account.name+"!");
closeBox();
}else{
alert("Mobile number or password is incorrect.");
}
}

function wallet(){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>💳 Wallet</h2>
<p>Current balance: 🪙 <b>${balance.toLocaleString()}</b></p>
<hr>
<h3>Deposit / Withdrawal</h3>
<p>JazzCash: <b>0308 1724110</b><br>
Account Name: <b>Ashfaq Sadiq</b></p>
<p>For real payments, use an authorized payment gateway/backend. This GitHub Pages version does not process real-money gaming transactions.</p>
<button class="blue" onclick="virtualDeposit()">Add 10,000 Virtual Coins</button>
<button class="yellow" onclick="virtualWithdraw()">Withdraw 5,000 Virtual Coins</button>
`);
}

function virtualDeposit(){
balance+=10000;
update();
alert("10,000 virtual coins added.");
closeBox();
}

function virtualWithdraw(){
if(balance<5000){
alert("Insufficient virtual coins.");
return;
}
balance-=5000;
update();
alert("5,000 virtual coins deducted.");
closeBox();
}

function bonus(){
let today=new Date().toDateString();

if(localStorage.getItem("bonusDate")===today){
alert("Today's bonus has already been claimed.");
return;
}

balance+=5000;
localStorage.setItem("bonusDate",today);
update();

alert("🎉 5,000 virtual coins added!");
}

function rewards(){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>👑 Rewards Plans</h2>

<div class="plan">
<strong>Bronze</strong> — 🪙 5,000
<br>Basic rewards
</div>

<div class="plan">
<strong>Silver</strong> — 🪙 25,000
<br>Extra rewards
</div>

<div class="plan">
<strong>Gold</strong> — 🪙 75,000
<br>Premium rewards
</div>

<div class="plan">
<strong>VIP</strong> — 🪙 150,000
<br>VIP rewards
</div>
`);
}

function invite(){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>🎁 Invite & Earn</h2>
<p>Your referral code:</p>
<div class="number">GM${Math.floor(100000+Math.random()*900000)}</div>
<br>
<button class="blue" onclick="share()">Share</button>
`);
}

function share(){
if(navigator.share){
navigator.share({
title:"GameMaster 3D",
text:"Join GameMaster 3D!"
});
}else{
alert("Referral code ready to share.");
}
}

function game(name){
openBox(`
<button class="close" onclick="closeBox()">×</button>
<h2>🎮 ${name}</h2>
<p>Game lobby opened.</p>
<p>This website version uses virtual coins only.</p>
<button class="purple" onclick="closeBox()">Enter</button>
`);
}

function gamesScroll(){
document.getElementById("games").scrollIntoView({behavior:"smooth"});
}

function support(){
window.open("https://wa.me/923081724110","_blank");
}

update();
</script>

</body>
</html>
