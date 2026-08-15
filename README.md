<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>GameMaster 3D</title>

<style>
*{box-sizing:border-box}
body{
 margin:0;background:#08051b;color:white;
 font-family:Arial,sans-serif
}
button{font:inherit;cursor:pointer}

header{
 height:82px;background:#080518;border-bottom:1px solid #30226d;
 display:flex;align-items:center;padding:0 25px;gap:18px;
 position:sticky;top:0;z-index:20
}
.logo{font-size:30px;font-weight:900;font-style:italic}
.logo span{color:#35baff}

.balance{
 margin-left:auto;border:1px solid #3d2b88;border-radius:15px;
 padding:7px 12px;display:flex;align-items:center;gap:8px
}
.balance small{display:block;color:#aaa}
.balance strong{font-size:18px}
.plus{
 border:0;background:#28c94d;color:white;border-radius:50%;
 width:38px;height:38px;font-size:23px
}

.nav{display:flex;gap:12px}
.nav button{background:none;border:0;color:white;font-weight:bold}
.nav b{display:block;font-size:25px}

.container{max-width:1200px;margin:auto;padding:15px 24px 90px}

.hero{
 display:grid;grid-template-columns:2.5fr 1fr;gap:12px
}
.heroMain{
 height:235px;border:1px solid #4930a4;border-radius:18px;
 padding:25px;position:relative;overflow:hidden;
 background:radial-gradient(circle at 75%,#6818d0,#25106c 45%,#10072e)
}
.heroMain:after{
 content:"👩🏻  👩🏻‍🦰  🎁";
 position:absolute;right:20px;bottom:5px;font-size:58px
}
.heroMain h1{font-size:40px;margin:0}
.heroMain h2{font-size:30px;color:#ffd21c;margin:3px 0}
.heroMain p{font-size:17px;line-height:1.5}

.bonus{
 border:1px solid #3b2a8c;border-radius:18px;
 padding:24px;background:#110d31
}
.bonus h2{margin-top:0}
.bonus p{color:#ddd;line-height:1.5}
.bonus button{width:100%}

.btn{
 border:0;border-radius:9px;padding:11px 22px;
 font-weight:bold;margin-right:7px
}
.purple{background:#7024ff;color:white}
.gold{background:#ffd21c;color:#111}
.green{background:#25c94b;color:white}

.quick{
 display:grid;grid-template-columns:repeat(6,1fr);
 gap:10px;margin:13px 0
}
.quick button{
 background:#15103b;border:1px solid #3b2b87;
 color:white;border-radius:13px;padding:12px
}
.quick span{display:block;font-size:30px;margin-bottom:5px}

.section{
 border:1px solid #3b298e;border-radius:17px;
 background:#110d31;padding:14px;margin:13px 0
}
.sectionHead{
 display:flex;justify-content:space-between;
 align-items:center;margin-bottom:12px
}
.sectionHead h2{margin:0}
.view{
 border:0;background:#291568;color:white;
 border-radius:18px;padding:8px 16px
}

.people,.games,.rewards{
 display:grid;grid-template-columns:repeat(6,1fr);gap:9px
}

.person{
 background:#15103b;border:1px solid #49319b;
 border-radius:12px;overflow:hidden
}
.face{
 height:145px;display:flex;align-items:center;
 justify-content:center;font-size:70px;
 background:linear-gradient(145deg,#76502e,#23152a)
}
.personText{padding:8px}
.online{color:#32df66;font-size:10px}

.game{
 position:relative;color:white;padding:0 0 9px;
 background:#15103b;border:1px solid #49319b;
 border-radius:12px;overflow:hidden
}
.game:hover{border-color:#9b76ff;transform:translateY(-2px)}
.gameIcon{
 height:108px;display:flex;align-items:center;
 justify-content:center;font-size:55px;
 background:radial-gradient(circle,#41229b,#120c34)
}
.gameName{font-weight:bold;padding:8px 3px 3px}
.gameTag{
 position:absolute;top:5px;right:5px;
 background:#ef3d45;border-radius:7px;
 padding:3px 6px;font-size:9px;font-weight:bold
}

.reward{
 background:#15103b;border:1px solid #49319b;
 border-radius:12px;text-align:center;padding:8px
}
.rewardIcon{
 height:95px;display:flex;align-items:center;
 justify-content:center;font-size:55px
}
.reward p{color:#ffd21c}

.promos{
 display:grid;grid-template-columns:repeat(3,1fr);gap:12px
}
.promo{
 border:1px solid #3d2b8e;border-radius:17px;
 padding:20px;background:#110d31
}
.number{
 background:#ffd21c;color:#111;text-align:center;
 font-size:22px;font-weight:bold;border-radius:8px;padding:8px
}

.modal{
 display:none;position:fixed;inset:0;background:#000d;
 z-index:100;align-items:center;justify-content:center;padding:15px
}
.modal.show{display:flex}
.box{
 width:min(600px,100%);background:#100b32;
 border:1px solid #553ab8;border-radius:19px;
 padding:22px;max-height:90vh;overflow:auto
}
.close{
 float:right;background:none;border:0;
 color:white;font-size:28px
}
.input{
 width:100%;padding:12px;margin:6px 0;
 background:#080622;border:1px solid #3d2d86;
 color:white;border-radius:8px
}
.stage{
 min-height:300px;border:1px solid #4d37a6;
 border-radius:15px;background:radial-gradient(circle,#2b166f,#08061c);
 display:flex;flex-direction:column;
 align-items:center;justify-content:center;text-align:center
}
.big{font-size:85px}
.result{
 color:#ffd21c;font-size:20px;
 font-weight:bold;min-height:30px;margin:10px
}

.bottom{display:none}

@media(max-width:950px){
 .games{grid-template-columns:repeat(4,1fr)}
 .people,.rewards{grid-template-columns:repeat(3,1fr)}
 .quick{grid-template-columns:repeat(3,1fr)}
 .hero{grid-template-columns:1fr}
 .promos{grid-template-columns:1fr}
}

@media(max-width:600px){
 header{height:62px;padding:0 8px}
 .logo{font-size:20px}
 .nav{display:none}
 .balance{min-width:145px;padding:5px 8px}
 .balance strong{font-size:14px}
 .container{padding:9px 8px 75px}
 .heroMain{height:245px;padding:19px 14px}
 .heroMain h1{font-size:30px}
 .heroMain h2{font-size:24px}
 .heroMain:after{font-size:42px}
 .quick{grid-template-columns:repeat(2,1fr)}
 .games{grid-template-columns:repeat(2,1fr)}
 .people,.rewards{grid-template-columns:repeat(2,1fr)}
 .face{height:120px}
 .gameIcon{height:100px}
 .bottom{
  display:grid;position:fixed;bottom:0;left:0;right:0;
  height:62px;background:#0b0825;
  border-top:1px solid #342675;
  grid-template-columns:repeat(5,1fr);z-index:90
 }
 .bottom button{
  background:none;border:0;color:white;font-size:10px
 }
 .bottom span{display:block;font-size:21px}
}
</style>
</head>

<body>

<header>

<div class="logo">
♛ GameMaster<span>3D</span>
</div>

<div class="balance">
🪙
<div>
<small>Balance</small>
<strong id="balance">50,000</strong>
</div>
<button class="plus" onclick="wallet()">+</button>
</div>

<nav class="nav">
<button onclick="rewards()">🎁<b>Rewards</b></button>
<button onclick="messages()">💬<b>Messages</b></button>
<button onclick="support()">🎧<b>Support
