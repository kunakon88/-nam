<!doctype html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>หมู่บ้านของน้ำ • TikTok LIVE Gift Edition</title>
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;600;700&display=swap" rel="stylesheet">
<style>
html,body{margin:0;height:100%;background:#2a2017;overflow:hidden;font-family:'Sarabun','Noto Sans Thai','Thonburi','Tahoma',sans-serif;-webkit-user-select:none;user-select:none}
#stage{position:absolute;left:50%;top:50%;width:540px;height:960px;transform-origin:50% 50%;overflow:hidden;background:#d9c696}
#c{position:absolute;left:0;top:0;width:540px;height:960px;image-rendering:auto;transform:translateZ(0)}
#panel{-webkit-font-smoothing:antialiased;text-rendering:optimizeLegibility;position:absolute;right:42px;top:12px;width:226px;transform:scale(.92);transform-origin:100% 0;padding:8px 9px 7px;border-radius:13px;background:rgba(56,38,24,.78);color:#fff4dc;box-shadow:0 3px 14px rgba(30,18,8,.35);border:1px solid rgba(255,225,170,.3);z-index:7}
#panel h1{margin:0 0 7px;font-size:15px;font-weight:700;color:#ffd98a;letter-spacing:.2px}
#panel .r{display:flex;align-items:center;gap:5px;height:23px;font-size:12.5px;line-height:1;border-left:3px solid var(--c);padding-left:5px;margin:1px 0;white-space:nowrap}
#panel .r img{width:23px;height:23px;object-fit:contain;flex:0 0 23px;filter:drop-shadow(0 1px 2px #24180f66)}
#panel .r b{flex:0 0 90px;font-weight:700;text-shadow:0 1px 1px rgba(0,0,0,.45);overflow:hidden;text-overflow:ellipsis}
#panel .r span{color:#fff0d2;opacity:.95;overflow:hidden;text-overflow:ellipsis;font-size:11.5px}
#toasts{position:absolute;left:12px;right:72px;bottom:238px;display:flex;flex-direction:column;gap:5px;align-items:center;pointer-events:none;z-index:8}
.t{-webkit-font-smoothing:antialiased;text-rendering:optimizeLegibility;text-shadow:0 1px 1px rgba(0,0,0,.35);max-width:100%;box-sizing:border-box;padding:7px 13px;border-radius:18px;background:rgba(56,38,24,.91);border:1px solid rgba(255,225,170,.48);color:#fff4dc;font-size:15px;line-height:1.35;text-align:center;box-shadow:0 2px 10px rgba(30,18,8,.35);animation:tin .22s ease-out;transition:opacity .35s,transform .35s;display:flex;align-items:center;justify-content:center;gap:5px}
.t b{color:#ffd98a}.t img{width:30px;height:30px;object-fit:contain;flex:0 0 27px}
.t.out{opacity:0;transform:translateY(6px)}
@keyframes tin{from{opacity:0;transform:translateY(10px) scale(.96)}to{opacity:1;transform:none}}
#dot{position:absolute;left:54px;top:24px;width:9px;height:9px;border-radius:50%;background:#e5484d;box-shadow:0 0 0 2px rgba(255,255,255,.55);z-index:5}#dot.ok{background:#2fcf6a}
#dbg{position:absolute;left:8px;top:52px;width:230px;max-height:200px;overflow:hidden;font:10px/1.3 monospace;color:#fff;background:rgba(0,0,0,.55);padding:4px;border-radius:6px;display:none;z-index:6;word-break:break-all}
#snd{position:absolute;left:10px;top:10px;width:36px;height:36px;border-radius:50%;border:1px solid rgba(255,225,170,.35);background:rgba(56,38,24,.55);color:#fff;font-size:17px;cursor:pointer;z-index:5}
#dev{position:fixed;left:8px;bottom:238px;display:none;flex-wrap:wrap;gap:4px;max-width:210px;z-index:9}
#dev button{font-size:18px;padding:3px 7px;border-radius:8px;border:0;background:rgba(255,255,255,.85);cursor:pointer}
#panel{right:12px;top:90px;width:244px;transform:none;padding:8px 10px 7px}
#panel h1{font-size:15px;margin:0 0 5px}
#panel .r{height:20px;gap:4px;margin:1px 0;font-size:12px}
#panel .r img{width:20px;height:20px;flex:0 0 20px}
#panel .r span{font-size:12px;flex:1 1 auto;min-width:0}
#panel .r b.n9{flex:0 0 auto;font-size:11px;color:#2a1d10;background:#ffd98a;border-radius:9px;padding:2px 6px;text-shadow:none}
#panel .tip{margin-top:5px;padding-top:4px;border-top:1px solid rgba(255,225,170,.3);font-size:11.5px;line-height:1.4;color:#ffe9b8}
#panel .tip b{color:#ffd98a}
#safe{position:absolute;inset:0;pointer-events:none;z-index:20}
#safe i{position:absolute;background:rgba(255,40,60,.25);border:1px dashed rgba(255,255,255,.8);color:#fff;font:600 12px sans-serif;display:flex;align-items:center;justify-content:center;text-align:center}
</style>
</head>
<body>
<div id="stage">
  <canvas id="c"></canvas>
  <button id="snd" title="เปิด/ปิดเสียง">🔇</button>
  <div id="dot" title="TikFinity @namboran_ancientbeads · ยังไม่เชื่อมต่อ"></div>
  <div id="dbg"></div>
  <div id="panel"></div>
  <div id="toasts"></div>
  <div id="safe"></div>
</div>
<div id="dev"></div>
<script>
(()=>{
'use strict';
/* ============ พื้นฐาน ============ */
const W=540,H=960,TAU=Math.PI*2;
const params=new URLSearchParams(location.search);
const $=id=>document.getElementById(id);
const cv=$('c'),ctx=cv.getContext('2d',{alpha:false}),stage=$('stage');
const FONT="'Sarabun','Noto Sans Thai','Thonburi','Tahoma',sans-serif";
let C=ctx,R=1,T=0;
const rnd=(a,b)=>a+Math.random()*(b-a);
const pick=a=>a[(Math.random()*a.length)|0];
const clamp=(v,a,b)=>Math.max(a,Math.min(b,v));
// เรนเดอร์ความละเอียดสูง: PC 3x, มือถือ 2x; ปรับเองได้ด้วย ?quality=1-3
const isMobileDisplay=/Android|iPhone|iPad|iPod/i.test(navigator.userAgent)||
  (window.matchMedia&&window.matchMedia('(pointer: coarse)').matches&&innerWidth<900);
const requestedQuality=parseFloat(params.get('quality'));
// กล้อง: ย่อโลกลงเล็กน้อยแล้วเลื่อนให้ฉากสำคัญอยู่ใน safe zone ของ TikTok Live
// (เว้นแถบหัวด้านบน ~88px และช่องคอมเมนต์ด้านล่าง ~215px ของเวที 540x960)
const CAM={s:.8,ox:54,oy:75};
const X0=-80,X1=W+80,Y0=-110,Y1=1130; // ขอบเขตพื้นหลังที่ขยายให้เต็มจอหลังย่อกล้อง
const WS=1.18; // ขยายตัวละครชดเชยการย่อกล้อง
const forcedQuality=Number.isFinite(requestedQuality)&&requestedQuality>0?clamp(requestedQuality,1,4):0;
ctx.imageSmoothingEnabled=true;
ctx.imageSmoothingQuality='high';
ctx.textRendering='geometricPrecision';
const ease=t=>t<=0?0:t>=1?1:1-Math.pow(1-t,3);
function mul(a){return function(){a|=0;a=a+0x6D2B79F5|0;let t=Math.imul(a^a>>>15,1|a);t=t+Math.imul(t^t>>>7,61|t)^t;return((t^t>>>14)>>>0)/4294967296}}

/* ============ เรขาคณิตของหมู่บ้าน ============ */
const MAINX=270, ENT_Y=912, RT=775, RB=845;
const yT=x=>RT+Math.sin(x/68)*5, yB=x=>RB+Math.sin(x/83+1.3)*5;
const HUB={x:270,y:570,r:46};
const SH={
  love:  {key:'love',  x:110,y:325,name:'ศาลเยว่เหล่า',rgb:'255,125,150',petal:['#f4a3b4','#e9788f','#fbd0d8','#d95a78']},
  work:  {key:'work',  x:430,y:490,name:'ศาลพระพรหม',  rgb:'255,205,100',petal:['#f5b23d','#f08a2b','#ffd86a','#e8a03a']},
  health:{key:'health',x:110,y:520,name:'ศาลท้าวเวสสุวรรณ',rgb:'190,245,200',petal:['#f4f7ee','#cfe6c6','#a9d1a6','#ffffff']},
  wealth:{key:'wealth',x:430,y:655,name:'ศาลพระแม่ลักษมี',rgb:'255,215,120',petal:['#f1b6bc','#ffd36b','#eb9aa6','#ffe39a']}
};
for(const k in SH){const s=SH[k];s.stand=s.y+50;s.boost=0;s.ph=rnd(0,6);s.smokeT=0;s.petalT=rnd(0,1)}
const TREE={x:110,y:175,tags:[],blobs:[]};
const REL={y:752,fish:215,turtle:165,bird:105,waterY:808};
const PATHS=[ // [x1,y1,x2,y2,w]
  [110,SH.love.stand,270,SH.love.stand,32],
  [110,SH.health.stand,270,SH.health.stand,32],
  [270,SH.work.stand,430,SH.work.stand,32],
  [270,SH.wealth.stand,430,SH.wealth.stand,32],
  [150,215,270,215,32],
  [100,REL.y,270,REL.y,32],
  [270,Y0,270,Y1,48]
];
const SLOTS=[];
for(const y of [628,660,692])for(let i=0;i<6;i++)SLOTS.push({x:62+i*30.4,y});
for(const y of [598,622,646,670]){SLOTS.push({x:231,y});SLOTS.push({x:309,y})}
for(let i=0;i<6;i++)SLOTS.push({x:50+i*34,y:872});
for(let i=0;i<7;i++)SLOTS.push({x:318+i*30,y:872});
for(let i=SLOTS.length-1;i>0;i--){const j=(Math.random()*(i+1))|0;[SLOTS[i],SLOTS[j]]=[SLOTS[j],SLOTS[i]]}
let slotIdx=0;

/* ============ ตัวช่วยวาด ============ */
function rr(x,y,w,h,r){r=Math.min(r,w/2,h/2);C.beginPath();C.moveTo(x+r,y);C.arcTo(x+w,y,x+w,y+h,r);C.arcTo(x+w,y+h,x,y+h,r);C.arcTo(x,y+h,x,y,r);C.arcTo(x,y,x+w,y,r);C.closePath()}
function fillRR(x,y,w,h,r,col){rr(x,y,w,h,r);C.fillStyle=col;C.fill()}
function ell(x,y,rx,ry,col,rot){C.beginPath();C.ellipse(x,y,rx,ry,rot||0,0,TAU);C.fillStyle=col;C.fill()}
function circ(x,y,r,col){C.beginPath();C.arc(x,y,r,0,TAU);C.fillStyle=col;C.fill()}
function poly(p,col){C.beginPath();C.moveTo(p[0][0],p[0][1]);for(let i=1;i<p.length;i++)C.lineTo(p[i][0],p[i][1]);C.closePath();C.fillStyle=col;C.fill()}
function line(x1,y1,x2,y2,col,w){C.beginPath();C.moveTo(x1,y1);C.lineTo(x2,y2);C.strokeStyle=col;C.lineWidth=w||1;C.stroke()}
function slab(cx,y,w,h,d,top,front){fillRR(cx-w/2,y+h-3,w,d+3,3,front);fillRR(cx-w/2,y,w,h,5,top)}
function shadow(x,y,rx,ry,a){ell(x,y,rx,ry,'rgba(45,30,18,'+a+')')}
function heart(x,y,s,col){C.beginPath();C.moveTo(x,y+s*.8);C.bezierCurveTo(x-s*1.5,y-s*.2,x-s*.6,y-s*1.3,x,y-s*.4);C.bezierCurveTo(x+s*.6,y-s*1.3,x+s*1.5,y-s*.2,x,y+s*.8);C.fillStyle=col;C.fill()}
const glowCache={};
function glowSprite(rgb){
  if(glowCache[rgb])return glowCache[rgb];
  const c=document.createElement('canvas');c.width=c.height=64;const g=c.getContext('2d');
  const gr=g.createRadialGradient(32,32,0,32,32,32);
  gr.addColorStop(0,'rgba('+rgb+',1)');gr.addColorStop(.35,'rgba('+rgb+',.4)');gr.addColorStop(1,'rgba('+rgb+',0)');
  g.fillStyle=gr;g.fillRect(0,0,64,64);return glowCache[rgb]=c;
}
function glowAt(rgb,x,y,r,a){
  if(a<=0)return;const o=C.globalCompositeOperation;C.globalCompositeOperation='lighter';
  C.globalAlpha=Math.min(1,a);C.drawImage(glowSprite(rgb),x-r,y-r,r*2,r*2);C.globalAlpha=1;C.globalCompositeOperation=o;
}
const tw=new Map();
function textW(t,font){if(tw.size>800)tw.clear();const k=font+t;let v=tw.get(k);if(v==null){C.font=font;v=C.measureText(t).width;tw.set(k,v)}return v}
function pill(text,x,y,font,bg,fg,padX,h){
  C.font=font;const w=textW(text,font)+padX*2;
  fillRR(x-w/2,y-h/2,w,h,h/2,bg);
  C.fillStyle=fg;C.textAlign='center';C.textBaseline='middle';C.fillText(text,x,y+.5);
}
function layer(fn){
  const c=document.createElement('canvas');c.width=Math.round(W*R);c.height=Math.round(H*R);
  const g=c.getContext('2d');g.scale(R,R);const old=C;C=g;fn();C=old;return c;
}

function wlayer(fn){
  const c=document.createElement('canvas');c.width=Math.round(W*R);c.height=Math.round(H*R);
  const g=c.getContext('2d');g.scale(R,R);g.transform(CAM.s,0,0,CAM.s,CAM.ox,CAM.oy);const old=C;C=g;fn();C=old;return c;
}
/* ============ เลเยอร์นิ่ง ============ */
let layerA,layerB,layerC;
function pathSeg(sg,phase,rg){
  const [x1,y1,x2,y2,w]=sg;const vx=x1===x2;
  const bx=vx?x1-w/2:Math.min(x1,x2),by=vx?Math.min(y1,y2):y1-w/2;
  const bw=vx?w:Math.abs(x2-x1),bh=vx?Math.abs(y2-y1):w;
  if(phase===0){fillRR(bx-4,by-4,bw+8,bh+8,9,'rgba(92,64,36,.30)');return}
  fillRR(bx,by,bw,bh,6,'#d6ad72');
  C.save();rr(bx,by,bw,bh,6);C.clip();
  const tw_=12,th=8;
  for(let yy=by,row=0;yy<by+bh;yy+=th,row++){
    for(let xx=bx-(row%2)*tw_/2;xx<bx+bw;xx+=tw_){
      const v=rg();C.fillStyle='rgba('+(190+v*40|0)+','+(140+v*40|0)+','+(85+v*30|0)+',.55)';
      C.fillRect(xx+.5,yy+.5,tw_-1,th-1);
    }
  }
  C.restore();
}
function drawGround(){
  const rg=mul(11);
  let gr=C.createLinearGradient(0,Y0,0,Y1);gr.addColorStop(0,'#e4d4aa');gr.addColorStop(.55,'#dac797');gr.addColorStop(1,'#c9b283');
  C.fillStyle=gr;C.fillRect(X0,Y0,X1-X0,Y1-Y0);
  for(let i=0;i<62;i++){
    const edge=rg()<.55;const x=edge?(rg()<.5?X0+rg()*(95-X0):W-95+rg()*(95-X0)):X0+rg()*(X1-X0),y=Y0+rg()*(Y1-Y0),r=20+rg()*52;
    ell(x,y,r,r*(.55+rg()*.35),'rgba('+(112+rg()*18|0)+','+(136+rg()*18|0)+','+(96+rg()*16|0)+','+(.13+rg()*.13)+')',rg()*3);
  }
  for(let i=0;i<32;i++)ell(X0+rg()*(X1-X0),Y0+rg()*(Y1-Y0),25+rg()*40,14+rg()*20,'rgba(246,232,196,'+(.10+rg()*.1)+')',rg()*3);
  for(let i=0;i<720;i++){C.fillStyle='rgba('+(100+rg()*30|0)+','+(80+rg()*25|0)+','+(50+rg()*20|0)+','+(.05+rg()*.07)+')';C.fillRect(X0+rg()*(X1-X0),Y0+rg()*(Y1-Y0),1+rg()*2,1+rg()*1.4)}
  C.strokeStyle='rgba(98,122,78,.45)';C.lineWidth=1;
  for(let i=0;i<330;i++){const x=X0+rg()*(X1-X0),y=Y0+rg()*(Y1-Y0);C.beginPath();for(let k=-1;k<=1;k++){C.moveTo(x+k*2,y);C.lineTo(x+k*3.5,y-4-rg()*3)}C.stroke()}
  // ท้องน้ำ (ให้ขอบไม่โหว่)
  C.fillStyle='#5f8b88';C.fillRect(X0,RT-6,X1-X0,RB-RT+12);
  const pr=mul(5);
  PATHS.forEach(s=>pathSeg(s,0,pr));
  PATHS.forEach(s=>pathSeg(s,1,pr));
  // ลานกลางหมู่บ้าน
  circ(HUB.x,HUB.y,HUB.r+4,'rgba(92,64,36,.3)');circ(HUB.x,HUB.y,HUB.r,'#dcb97e');
  C.strokeStyle='#b97745';C.lineWidth=3;C.beginPath();C.arc(HUB.x,HUB.y,38,0,TAU);C.stroke();
  circ(HUB.x,HUB.y,30,'#ecd29c');
  for(let i=0;i<20;i++){const a=i*TAU/20;line(HUB.x+Math.cos(a)*31,HUB.y+Math.sin(a)*31,HUB.x+Math.cos(a)*45,HUB.y+Math.sin(a)*45,'rgba(110,75,40,.28)',1)}
  for(let i=0;i<8;i++){const a=i*TAU/8;ell(HUB.x+Math.cos(a)*14,HUB.y+Math.sin(a)*14,11,5,i%2?'#c27a4a':'#e7a77a',a)}
  circ(HUB.x,HUB.y,6,'#8f4a2c');circ(HUB.x,HUB.y,2.5,'#f2d08a');
  // แปลงดอกไม้
  for(const y of [628,660,692])fillRR(42,y-12,184,24,11,'#a68a5c');
  for(const y of [628,660,692])fillRR(44,y-10,180,20,9,'#9a7d51');
  fillRR(36,861,190,24,11,'#a68a5c');fillRR(314,861,190,24,11,'#a68a5c');
  fillRR(38,863,186,20,9,'#9a7d51');fillRR(316,863,186,20,9,'#9a7d51');
  // พื้นหินหน้าประตู
  for(let i=0;i<40;i++)ell(180+rg()*180,895+rg()*50,6+rg()*6,3+rg()*3,'rgba(150,120,80,.25)',rg()*3);
}
function drawOverWater(){
  const rg=mul(23);
  for(let x=X0;x<X1;x+=11){
    const a=yT(x)-9,b=yB(x)-3;
    for(const y of [a,b]){
      const w=9+rg()*5,h=8+rg()*3,v=rg();
      fillRR(x,y,w,h,3,v<.33?'#a89678':v<.66?'#b9a886':'#8c7d62');
      fillRR(x+1,y+1,w-2,2.5,1.2,'rgba(255,245,215,.35)');
      if(rg()<.28)ell(x+w*.5,y+2,4,2,'rgba(127,148,106,.8)');
    }
  }
  const reeds=(x,y,n)=>{for(let i=0;i<n;i++){const dx=x+(rg()-.5)*16,h=16+rg()*16,l=(rg()-.5)*8;
    C.strokeStyle=rg()<.5?'#7f9468':'#6a8258';C.lineWidth=1.6;C.beginPath();C.moveTo(dx,y);C.quadraticCurveTo(dx+l*.3,y-h*.6,dx+l,y-h);C.stroke();
    if(rg()<.35)fillRR(dx+l-1.4,y-h-5,2.8,7,1.4,'#7b4f2e')}};
  for(const x of [40,335,402,500])reeds(x,yT(x)-6,8);
  for(const x of [30,150,205,365,470])reeds(x,yB(x)+8,7);
  // สะพานไม้
  const by0=RT-13,by1=RB+13,bx=MAINX-26;
  fillRR(bx+3,by0+6,52,by1-by0,8,'rgba(30,45,45,.28)');
  fillRR(bx,by0,52,by1-by0,6,'#9c6b3f');
  for(let y=by0+2,i=0;y<by1-2;y+=6,i++){fillRR(bx+2,y,48,5,1.5,i%2?'#b07d4b':'#a2713f')}
  fillRR(bx-2,by0,7,by1-by0,3,'#6e472a');fillRR(bx+47,by0,7,by1-by0,3,'#6e472a');
  for(const px of [bx+1,bx+47]){
    line(px+2.5,by0+4,px+2.5,by1-4,'#8a5a36',3);
    for(let y=by0+4;y<=by1-4;y+=16){fillRR(px,y-5,5,11,1.5,'#b5693c');fillRR(px-.5,y-6,6,3,1.5,'#e0b25a')}
  }
}
function drawLight(){
  let g=C.createLinearGradient(0,0,0,H);
  g.addColorStop(0,'rgba(255,175,105,.15)');g.addColorStop(.5,'rgba(255,200,140,.05)');g.addColorStop(1,'rgba(150,95,70,.13)');
  C.fillStyle=g;C.fillRect(0,0,W,H);
  g=C.createRadialGradient(W/2,H*.5,H*.3,W/2,H*.5,H*.72);
  g.addColorStop(0,'rgba(30,18,10,0)');g.addColorStop(1,'rgba(30,18,10,.46)');
  C.fillStyle=g;C.fillRect(0,0,W,H);
}
function buildStatic(){layerA=wlayer(drawGround);layerB=wlayer(drawOverWater);layerC=layer(drawLight)}

/* ============ น้ำ เรือ ปลา เต่า ============ */
const ripples=[],fishes=[],turtles=[],boats=[
  {x:120,y:797,dir:1,sp:15,played:false},
  {x:420,y:826,dir:-1,sp:12,played:false}
];
function addRipple(x,y){ripples.push({x,y,r:2,a:.8})}
function drawWater(){
  C.save();
  C.beginPath();C.moveTo(X0,yT(X0));for(let x=X0;x<=X1;x+=15)C.lineTo(x,yT(x));
  for(let x=X1;x>=X0;x-=15)C.lineTo(x,yB(x));C.closePath();C.clip();
  let g=C.createLinearGradient(0,RT,0,RB);g.addColorStop(0,'#86aaa0');g.addColorStop(1,'#5d8985');
  C.fillStyle=g;C.fillRect(X0,RT-8,X1-X0,RB-RT+16);
  C.fillStyle='rgba(255,190,120,.10)';C.fillRect(X0,RT-8,X1-X0,RB-RT+16);
  C.strokeStyle='rgba(255,255,255,.2)';C.lineWidth=1.2;
  for(let k=0;k<14;k++){
    const y=RT+7+k*5;C.beginPath();
    for(let x=X0;x<=X1;x+=10){const yy=y+Math.sin(x/24+T*.9+k*1.7)*1.6;x===X0?C.moveTo(x,yy):C.lineTo(x,yy)}
    C.stroke();
  }
  for(let i=0;i<32;i++){
    const ph=(T*.35+i*.37)%1,x=X0+(i*97.3+T*8)%(X1-X0),y=RT+10+((i*53)%(RB-RT-20));
    C.globalAlpha=Math.sin(ph*Math.PI)*.55;line(x,y,x+7,y,'#fff4d6',1.4);
  }
  C.globalAlpha=1;
  // ปลาว่าย
  for(const f of fishes){if(f.st!=='swim')continue;drawFish(f.x,f.y,f.sz,f.c,f.ph,1)}
  for(const t of turtles){if(t.st!=='swim')continue;drawTurtle(t)}
  for(const r of ripples){C.strokeStyle='rgba(255,255,255,'+r.a*.7+')';C.lineWidth=1.3;C.beginPath();C.ellipse(r.x,r.y,r.r,r.r*.45,0,0,TAU);C.stroke()}
  for(const b of boats)drawBoat(b);
  C.restore();
}
function drawFish(x,y,sz,col,ph,dir){
  const wag=Math.sin(ph*6)*sz*.5;
  C.save();C.translate(x,y);if(dir<0)C.scale(-1,1);
  poly([[-sz*1.6,0],[-sz*2.8,-sz*.9+wag],[-sz*2.8,sz*.9+wag]],col);
  ell(0,0,sz*1.9,sz*.95,col);ell(sz*.4,-sz*.2,sz*.8,sz*.4,'rgba(255,255,255,.35)');
  circ(sz*1.1,-sz*.3,.8,'#2b1d14');circ(sz*1.1,sz*.3,.8,'#2b1d14');
  C.restore();
}
function drawTurtle(t){
  const x=t.x,y=t.y,s=Math.sin(t.ph*2);
  for(const [dx,dy,sg] of [[6,-7,-1],[6,7,1],[-6,-7,-1],[-6,7,1]])ell(x+dx+s*sg*1.5,y+dy,4,2,'#8d9a62',sg*.5);
  ell(x+11,y,3.6,3,'#a3a06a');ell(x-10,y,3,1.6,'#8d9a62');
  ell(x,y,10,8,'#6c7e4b');ell(x,y,7.6,6,'#7d8f55');
  C.strokeStyle='rgba(60,75,40,.6)';C.lineWidth=1;C.beginPath();C.moveTo(x-6,y);C.lineTo(x+6,y);C.moveTo(x,y-5);C.lineTo(x,y+5);C.stroke();
}
function drawBoat(b){
  const {x,y}=b,d=b.dir;
  ell(x-d*46,y+1,34,5,'rgba(255,255,255,.18)');
  C.save();C.translate(x,y);C.scale(d,1);
  ell(2,5,40,9,'rgba(30,50,48,.25)');
  C.beginPath();C.moveTo(-38,0);C.quadraticCurveTo(-30,-10,0,-10);C.quadraticCurveTo(30,-10,44,0);C.quadraticCurveTo(30,10,0,10);C.quadraticCurveTo(-30,10,-38,0);C.closePath();
  C.fillStyle='#8a5a33';C.fill();C.strokeStyle='#5e3d22';C.lineWidth=2;C.stroke();
  ell(0,0,30,6,'#b0834f');
  fillRR(-14,-8,26,13,6,'#efe0bd');
  for(let i=0;i<4;i++)fillRR(-11+i*7,-8,3.2,13,1.5,'#c9785a');
  // คนพาย
  circ(-26,0,3.6,'#e8c19a');fillRR(-30,-1,8,6,3,'#7f9a70');
  line(-26,2,-8,13,'#7a5530',1.6);
  // โคมหัวเรือ
  line(38,0,38,-8,'#5e3d22',1.5);ell(38,-11,3.5,4.5,'#d8402f');
  C.restore();
  glowAt('255,150,80',x+d*38,y-11,26,.5);
}
function addFishSwim(x,y){if(fishes.length>40)fishes.shift();fishes.push({st:'swim',x,y,by:y,sz:rnd(3,4.6),c:pick(['#f08a3a','#f4f0e6','#e8b04a','#e86a4a','#f4c68a']),ph:rnd(0,6),vx:rnd(8,15)})}
function addTurtleSwim(x,y){if(turtles.length>10)turtles.shift();turtles.push({st:'swim',x,y,by:y,ph:rnd(0,6),vx:rnd(5,9)})}
function updateWater(dt){
  for(const b of boats){
    b.x+=b.dir*b.sp*dt;
    if(b.x>X1+90)b.x=X0-90;if(b.x<X0-90)b.x=X1+90;
    if(Math.abs(b.x-MAINX)<4){if(!b.played){b.played=true;audio.boat()}}else b.played=false;
  }
  for(let i=ripples.length-1;i>=0;i--){const r=ripples[i];r.r+=dt*14;r.a-=dt*.5;if(r.a<=0)ripples.splice(i,1)}
  for(let i=fishes.length-1;i>=0;i--){
    const f=fishes[i];
    if(f.st==='swim'){f.x+=f.vx*dt;f.ph+=dt*2;f.y=f.by+Math.sin(f.ph*1.3)*3;if(f.x>X1+20){fishes.splice(i,1)}}
    else{f.k+=dt/.85;if(f.k>=1){addRipple(f.tx,f.ty);addFishSwim(f.tx,f.ty);fishes.splice(i,1)}}
  }
  for(let i=turtles.length-1;i>=0;i--){
    const t=turtles[i];
    if(t.st==='swim'){t.x+=t.vx*dt;t.ph+=dt*2.2;t.y=t.by+Math.sin(t.ph*.6)*2;if(t.x>X1+30)turtles.splice(i,1)}
    else{t.k+=dt/.9;if(t.k>=1){addRipple(t.tx,t.ty);addTurtleSwim(t.tx,t.ty);turtles.splice(i,1)}}
  }
}
function drawArcs(){
  for(const f of fishes){if(f.st==='swim')continue;const k=f.k,x=f.sx+(f.tx-f.sx)*k,y=f.sy+(f.ty-f.sy)*k-Math.sin(k*Math.PI)*34;drawFish(x,y,4.4,f.c,T*3,1)}
  for(const t of turtles){if(t.st==='swim')continue;const k=t.k;t.x=t.sx+(t.tx-t.sx)*k;t.y=t.sy+(t.ty-t.sy)*k-Math.sin(k*Math.PI)*30;t.ph=T*4;drawTurtle(t)}
}

/* ============ ต้นไม้ขอพร / ต้นไม้ประดับ / โคม / บ้าน / ประตู ============ */
(function(){const r=mul(41);for(let i=0;i<46;i++){const a=r()*TAU,d=Math.sqrt(r());
  TREE.blobs.push({x:Math.cos(a)*d*66,y:90+Math.sin(a)*d*50-10,r:16+r()*13,c:pick(['#6f8a58','#7e9a63','#5d7a4f','#86a06a','#688355']),d:r()*2-1})}
  TREE.blobs.sort((a,b)=>a.y-b.y);
  TREE.bloss=[];for(let i=0;i<40;i++){const a=r()*TAU,d=Math.sqrt(r());TREE.bloss.push({x:Math.cos(a)*d*74,y:90+Math.sin(a)*d*54-10,c:pick(['#f4b6c4','#f9d6dc','#f7e7b0'])})}
})();
function drawWishTree(){
  const bx=TREE.x,by=TREE.y;
  shadow(bx+16,by+4,62,12,.22);
  C.beginPath();C.moveTo(bx-18,by+3);C.bezierCurveTo(bx-10,by-20,bx-12,by-40,bx-8,by-66);C.lineTo(bx+8,by-66);C.bezierCurveTo(bx+12,by-40,bx+10,by-20,bx+20,by+3);C.closePath();
  C.fillStyle='#7a5436';C.fill();
  C.beginPath();C.moveTo(bx+1,by+3);C.bezierCurveTo(bx+3,by-20,bx+2,by-40,bx+2,by-66);C.lineTo(bx+8,by-66);C.bezierCurveTo(bx+12,by-40,bx+10,by-20,bx+20,by+3);C.closePath();
  C.fillStyle='#634329';C.fill();
  ell(bx-18,by+3,9,3.5,'#6e4c30');ell(bx+20,by+3,9,3.5,'#5a3d26');
  const sw=Math.sin(T*.6)*1.6;
  for(const b of TREE.blobs)circ(bx+b.x+sw*b.d,by-b.y,b.r,b.c);
  for(const b of TREE.blobs)if(b.y>85)ell(bx+b.x+sw*b.d-3,by-b.y-4,b.r*.55,b.r*.35,'rgba(210,225,160,.22)');
  for(const p of TREE.bloss)circ(bx+p.x+sw*.5,by-p.y,2.2,p.c);
  for(const t of TREE.tags){
    const ang=Math.sin(T*1.5+t.ph)*.12,ax=bx+t.ax+sw*.5,ay=by-t.ay;
    const hx=ax+Math.sin(ang)*t.len,hy=ay+Math.cos(ang)*t.len;
    line(ax,ay,hx,hy,'#8a6a46',1);
    C.save();C.translate(hx,hy);C.rotate(ang);fillRR(-4,0,8,13,1.5,t.c);fillRR(-4,0,8,2.5,1,'rgba(255,255,255,.35)');line(0,3,0,10,'rgba(90,40,30,.5)',1);C.restore();
    const age=T-t.t0;if(age<7)glowAt('255,215,130',hx,hy+6,22,(1-age/7)*.8);
  }
}
function addTag(){
  const th=rnd(.12,.88)*Math.PI;
  // จุดผูกอยู่ขอบล่างของพุ่มไม้ (ay = ความสูงเหนือฐานต้น)
  TREE.tags.push({ax:Math.cos(th)*66,ay:80-Math.sin(th)*50,len:rnd(12,24),c:pick(['#d94f4f','#e8b04a','#f3e3b6','#9bb58a','#e98aa0']),ph:rnd(0,6),t0:T});
  if(TREE.tags.length>70)TREE.tags.shift();
}
function smallTree(a){
  const {x,y,s,k}=a;
  shadow(x+6*s,y+3,22*s,6*s,.2);
  if(k==='willow'){
    fillRR(x-3*s,y-34*s,6*s,34*s,2,'#6b4a2e');
    circ(x,y-40*s,20*s,'#7f9a63');circ(x-10*s,y-34*s,13*s,'#6f8a58');circ(x+11*s,y-34*s,13*s,'#86a06a');
    for(let i=0;i<14;i++){const px=x-22*s+i*3.2*s,l=14*s+(i%3)*5*s,sw=Math.sin(T*1.1+i)*1.5;
      C.strokeStyle=i%2?'#7f9a63':'#6a8758';C.lineWidth=1.6;C.beginPath();C.moveTo(px,y-36*s);C.quadraticCurveTo(px+sw,y-26*s,px+sw*1.4,y-36*s+l);C.stroke()}
  }else{
    fillRR(x-3*s,y-26*s,6*s,26*s,2,'#6b4a2e');
    circ(x,y-38*s,17*s,'#6f8a58');circ(x-9*s,y-30*s,11*s,'#5d7a4f');circ(x+9*s,y-31*s,11*s,'#7e9a63');
    ell(x-4*s,y-44*s,8*s,5*s,'rgba(210,225,160,.25)');
  }
}
function drawLamp(a){
  const {x,y}=a;
  shadow(x+3,y+1,6,2.4,.22);fillRR(x-1.6,y-26,3.2,26,1,'#5d3d26');
  fillRR(x-6,y-37,12,13,3.5,'#d97a3a');fillRR(x-7,y-39,14,4,2,'#8c4a2b');fillRR(x-4,y-35,8,9,2,'#ffd68a');
}
function lampGlow(a){const f=.55+.1*Math.sin(T*5+a.x)+.05*Math.sin(T*11+a.y);glowAt('255,170,80',a.x,a.y-30,38,f)}
function drawHouse(a){
  const {x,y}=a;
  shadow(x+8,y+2,42,8,.22);
  fillRR(x-26,y-26,52,26,2,'#efe0bb');
  fillRR(x-26,y-8,52,8,2,'#d6bf92');
  poly([[x-36,y-24],[x-20,y-50],[x+20,y-50],[x+36,y-24]],'#b5693c');
  for(let i=-3;i<=3;i++)line(x+i*5.5,y-48,x+i*9.5,y-26,'rgba(100,50,25,.35)',1);
  line(x-36,y-24,x+36,y-24,'#8c4a2b',2.5);
  fillRR(x-5,y-17,10,17,2,'#6b4a30');fillRR(x+10,y-21,10,9,2,'#ffd68a');fillRR(x-20,y-21,10,9,2,'#ffd68a');
  line(x+15,y-21,x+15,y-12,'#8c6a40',1);line(x-15,y-21,x-15,y-12,'#8c6a40',1);
}
function drawGate(a){
  const {x,y}=a;
  shadow(x+4,y+2,56,8,.22);
  for(const dx of [-36,36]){fillRR(x+dx-6,y-4,12,6,2,'#9a8a70');fillRR(x+dx-4.5,y-62,9,60,2,'#a8523a');fillRR(x+dx-4.5,y-62,3,60,1,'#c86a50')}
  fillRR(x-46,y-66,92,8,3,'#8c3f2c');
  C.beginPath();C.moveTo(x-58,y-70);C.quadraticCurveTo(x-30,y-76,x,y-78);C.quadraticCurveTo(x+30,y-76,x+58,y-70);C.lineTo(x+50,y-65);C.quadraticCurveTo(x,y-72,x-50,y-65);C.closePath();
  C.fillStyle='#4f3a2a';C.fill();
  line(x-56,y-70,x+56,y-70,'#d9aa4a',1.5);
  fillRR(x-34,y-56,68,17,4,'#efe0bb');C.strokeStyle='#8c3f2c';C.lineWidth=1.5;rr(x-34,y-56,68,17,4);C.stroke();
  C.font='700 13px '+FONT;C.fillStyle='#6b3a22';C.textAlign='center';C.textBaseline='middle';C.fillText('หมู่บ้านของน้ำ',x,y-47);
  for(const dx of [-24,24]){const sw=Math.sin(T*1.5+dx)*1.5;line(x+dx,y-58,x+dx+sw,y-40,'#5e3d22',1);ell(x+dx+sw,y-35,5,6.5,'#d8402f');}
}
function gateGlow(a){for(const dx of [-24,24])glowAt('255,120,80',a.x+dx,a.y-35,26,.5)}

/* ============ ศาล (2.5D) ============ */
function offerings(s){
  const ax=s.x,ay=s.y,t=T;
  // กระถางธูป
  ell(ax,ay+34,10,4,'#5c3b22');fillRR(ax-8,ay+26,16,9,3,'#9a6a3f');ell(ax,ay+27,8,3,'#3f2a18');
  for(const dx of [-4,0,4]){line(ax+dx,ay+27,ax+dx,ay+16,'#8a3a28',1.1);circ(ax+dx,ay+16,1,'#ff6a3a')}
  glowAt('255,100,60',ax,ay+17,10,.4);
  // เทียน
  for(const dx of [-27,27]){
    const x=ax+dx,y=ay+31,fl=1+.25*Math.sin(t*13+dx)+.15*Math.sin(t*23+dx*2),sx=Math.sin(t*5+dx)*.6;
    fillRR(x-4,y-1,8,3,1,'#c9a24a');fillRR(x-2,y-10,4,10,1,'#f8ecd0');
    ell(x+sx,y-14,2.2,4.2*fl,'#ffcf55');ell(x+sx,y-13.2,1.1,2.4*fl,'#fff3c8');
    glowAt('255,190,90',x,y-13,16*fl,.55);
  }
}
const BUILD={
love(ax,ay,t){
  slab(ax,ay+6,112,30,10,'#ead7b2','#bb9c70');slab(ax,ay+34,38,8,6,'#f0deb9','#c3a574');
  fillRR(ax-32,ay-26,64,36,3,'#f2e3c2');
  C.beginPath();C.moveTo(ax-14,ay+10);C.lineTo(ax-14,ay-8);C.arc(ax,ay-8,14,Math.PI,0);C.lineTo(ax+14,ay+10);C.closePath();C.fillStyle='#5b2f24';C.fill();
  ell(ax,ay+3,9,7,'#f6efe0');circ(ax,ay-8,5,'#efcaa0');poly([[ax-3.5,ay-5],[ax+3.5,ay-5],[ax,ay+4]],'#ffffff');
  poly([[ax-6,ay-10],[ax,ay-17],[ax+6,ay-10]],'#c9483a');
  C.strokeStyle='#e0403a';C.lineWidth=1.6;C.beginPath();C.moveTo(ax+8,ay+2);C.bezierCurveTo(ax+20,ay-8,ax+22,ay+8,ax+30,ay-2);C.stroke();
  for(const dx of [-40,40]){fillRR(ax+dx-4,ay-32,8,64,2,'#b6402e');fillRR(ax+dx-4,ay-32,2.5,64,1,'#d65a44');fillRR(ax+dx-6,ay+30,12,4,1.5,'#9a8a70')}
  C.beginPath();C.moveTo(ax-66,ay-28);C.quadraticCurveTo(ax-50,ay-30,ax-36,ay-54);C.lineTo(ax+36,ay-54);C.quadraticCurveTo(ax+50,ay-30,ax+66,ay-28);C.quadraticCurveTo(ax,ay-14,ax-66,ay-28);C.closePath();
  C.fillStyle='#b5523d';C.fill();
  C.strokeStyle='rgba(90,30,20,.35)';C.lineWidth=1;for(let i=-5;i<=5;i++){C.beginPath();C.moveTo(ax+i*6.5,ay-52);C.lineTo(ax+i*11,ay-27+Math.abs(i)*.4);C.stroke()}
  C.strokeStyle='#e2b455';C.lineWidth=2.4;C.beginPath();C.moveTo(ax-66,ay-28);C.quadraticCurveTo(ax,ay-14,ax+66,ay-28);C.stroke();
  circ(ax-66,ay-29,3,'#e2b455');circ(ax+66,ay-29,3,'#e2b455');
  heart(ax,ay-40,7,'#ffd1da');
  fillRR(ax-24,ay-66,48,13,2,'#f2e3c2');
  C.beginPath();C.moveTo(ax-34,ay-64);C.quadraticCurveTo(ax-22,ay-66,ax-15,ay-88);C.lineTo(ax+15,ay-88);C.quadraticCurveTo(ax+22,ay-66,ax+34,ay-64);C.quadraticCurveTo(ax,ay-56,ax-34,ay-64);C.closePath();
  C.fillStyle='#a8452f';C.fill();C.strokeStyle='#e2b455';C.lineWidth=2;C.beginPath();C.moveTo(ax-34,ay-64);C.quadraticCurveTo(ax,ay-56,ax+34,ay-64);C.stroke();
  fillRR(ax-1.5,ay-96,3,9,1,'#e8bd5a');circ(ax,ay-97,3.6,'#e8bd5a');
  for(const sg of [-1,1]){
    const px=ax+sg*54,lx=px+Math.sin(t*1.6+sg)*2,ly=ay-8;
    line(px,ay-27,lx,ly-7,'#6b3b2a',1);fillRR(lx-4,ly-8,8,3,1.5,'#e2b455');ell(lx,ly,6,7.5,'#d8402f');fillRR(lx-4,ly+5,8,3,1.5,'#e2b455');line(lx,ly+8,lx+Math.sin(t*2+sg)*1.5,ly+16,'#e0403a',1.3);
    glowAt('255,110,80',lx,ly,24,.4);
  }
},
work(ax,ay,t){
  slab(ax,ay+6,104,30,10,'#ecd6a2','#bd9a5c');slab(ax,ay+34,36,8,6,'#f1deb0','#c4a56a');
  fillRR(ax-30,ay-26,60,36,3,'#f0dcaa');
  C.beginPath();C.moveTo(ax-14,ay+10);C.lineTo(ax-14,ay-8);C.arc(ax,ay-8,14,Math.PI,0);C.lineTo(ax+14,ay+10);C.closePath();C.fillStyle='#6a3d1f';C.fill();
  line(ax-9,ay-1,ax-17,ay-6,'#e2a83e',2);line(ax+9,ay-1,ax+17,ay-6,'#e2a83e',2);
  ell(ax,ay+2,10,8,'#e2a83e');circ(ax-7,ay-6,3.4,'#e5b550');circ(ax+7,ay-6,3.4,'#e5b550');circ(ax,ay-8,5.5,'#f0c765');
  poly([[ax-5,ay-12],[ax,ay-23],[ax+5,ay-12]],'#ffd96a');
  for(const dx of [-38,38]){fillRR(ax+dx-3.5,ay-30,7,62,2,'#c99132');fillRR(ax+dx-3.5,ay-30,2.4,62,1,'#e6b552')}
  const tiers=[[-26,62,19,'#d9a43f'],[-44,46,18,'#c98d36'],[-61,32,17,'#d9a43f']];
  for(const [y,w,h,c] of tiers){
    poly([[ax-w-6,ay+y],[ax-w+8,ay+y-h],[ax+w-8,ay+y-h],[ax+w+6,ay+y]],c);
    poly([[ax-w-2,ay+y-5],[ax-w+9,ay+y-h+4],[ax+w-9,ay+y-h+4],[ax+w+2,ay+y-5]],'rgba(255,240,180,.18)');
    fillRR(ax-w-6,ay+y-3,w*2+12,3.2,1.2,'#8e4b2e');
    poly([[ax-w-6,ay+y],[ax-w-11,ay+y-8],[ax-w-1,ay+y-3]],'#f0c04a');poly([[ax+w+6,ay+y],[ax+w+11,ay+y-8],[ax+w+1,ay+y-3]],'#f0c04a');
    C.strokeStyle='rgba(110,70,25,.3)';C.lineWidth=1;for(let i=-3;i<=3;i++){C.beginPath();C.moveTo(ax+i*(w*.2),ay+y-h+3);C.lineTo(ax+i*(w*.27),ay+y-4);C.stroke()}
  }
  poly([[ax-6,ay-78],[ax,ay-98],[ax+6,ay-78]],'#f0c04a');for(let i=0;i<4;i++)ell(ax,ay-82-i*4.4,4.6-i*.9,1.2,'#b9812c');circ(ax,ay-99,2.4,'#ffe28a');
  const sag=14+Math.sin(t*1.2)*1.2;
  for(let k=0;k<=1.001;k+=.055){const x=ax-36+72*k,y=ay-22+sag*4*k*(1-k);circ(x,y,3.3,Math.round(k*18)%2?'#f0922b':'#f7c03a')}
},
health(ax,ay,t){
  slab(ax,ay+6,104,30,10,'#c2cdb0','#8f9d7d');slab(ax,ay+34,36,8,6,'#cbd5ba','#9aa889');
  fillRR(ax-30,ay-24,60,34,3,'#a9b99a');
  C.strokeStyle='rgba(70,85,65,.28)';C.lineWidth=1;for(let r=0;r<4;r++){const y=ay-24+r*8.5;C.beginPath();C.moveTo(ax-30,y);C.lineTo(ax+30,y);C.stroke()}
  C.beginPath();C.moveTo(ax-14,ay+10);C.lineTo(ax-14,ay-8);C.arc(ax,ay-8,14,Math.PI,0);C.lineTo(ax+14,ay+10);C.closePath();C.fillStyle='#33402f';C.fill();
  line(ax+9,ay+9,ax+9,ay-13,'#7a5530',2.4);circ(ax+9,ay-15,3.8,'#d9b04a');
  fillRR(ax-6,ay-4,12,14,3,'#6d8f5e');circ(ax,ay-8,5,'#e8c59a');C.fillStyle='#c9a24a';C.beginPath();C.arc(ax,ay-9,5.4,Math.PI,TAU);C.fill();
  for(const dx of [-35,35]){fillRR(ax+dx-3.5,ay-26,7,60,2,'#8fa381');fillRR(ax+dx-3.5,ay-26,2.2,60,1,'#aebe9f')}
  poly([[ax-58,ay-22],[ax-45,ay-44],[ax+45,ay-44],[ax+58,ay-22]],'#6f8a6a');
  poly([[ax-52,ay-28],[ax-42,ay-41],[ax+42,ay-41],[ax+52,ay-28]],'rgba(255,255,230,.12)');
  for(let x=-54;x<=54;x+=8)circ(ax+x,ay-22,4.2,'#5f7a5c');
  C.beginPath();C.moveTo(ax-24,ay-44);C.bezierCurveTo(ax-27,ay-86,ax+27,ay-86,ax+24,ay-44);C.closePath();C.fillStyle='#d5dec6';C.fill();
  C.strokeStyle='rgba(110,130,100,.5)';C.lineWidth=1.2;for(let i=0;i<3;i++){C.beginPath();C.ellipse(ax,ay-47-i*7,22-i*5,3,0,0,Math.PI);C.stroke()}
  ell(ax,ay-58,5.5,8,'#6fa06a',.6);line(ax-3,ay-52,ax+3,ay-64,'rgba(255,255,255,.5)',1);
  fillRR(ax-2,ay-98,4,18,1.5,'#c9a24a');circ(ax,ay-100,4,'#e0bd5a');
  for(const sg of [-1,1]){const px=ax+sg*46;fillRR(px-6,ay+24,12,10,3,'#9a6a3f');for(let i=0;i<5;i++){const a=-Math.PI/2+(i-2)*.5+Math.sin(t*1.4+i+sg)*.06;ell(px+Math.cos(a)*6,ay+22+Math.sin(a)*8,2.6,5.5,'#6fa06a',a+Math.PI/2)}}
},
wealth(ax,ay,t){
  slab(ax,ay+6,108,30,10,'#e6c9a0','#b08256');slab(ax,ay+34,36,8,6,'#ecd3ab','#bb8e60');
  for(let i=0;i<9;i++){const a=-Math.PI+(i+.5)*Math.PI/9,cx=ax+Math.cos(a)*36,cy=ay-10+Math.sin(a)*40;
    ell(cx,cy,11,22,i%2?'#f3c6c9':'#eab0b6',a+Math.PI/2);ell(cx,cy,7,16,'rgba(255,255,255,.25)',a+Math.PI/2)}
  fillRR(ax-26,ay-14,52,24,3,'#f3e2c4');
  C.beginPath();C.moveTo(ax-12,ay+10);C.lineTo(ax-12,ay-6);C.arc(ax,ay-6,12,Math.PI,0);C.lineTo(ax+12,ay+10);C.closePath();C.fillStyle='#6a3427';C.fill();
  ell(ax,ay+8,12,3,'#f6b8c0');ell(ax,ay+1,8,6,'#e8879a');circ(ax,ay-7,4.6,'#efc9a0');poly([[ax-4,ay-10],[ax,ay-17],[ax+4,ay-10]],'#ffd96a');
  line(ax-7,ay-1,ax-13,ay-6,'#f1c04a',1.8);line(ax+7,ay-1,ax+13,ay-6,'#f1c04a',1.8);
  const g=C.createLinearGradient(0,ay-44,0,ay-14);g.addColorStop(0,'#d1805a');g.addColorStop(1,'#9a512f');
  C.beginPath();C.arc(ax,ay-14,30,Math.PI,0);C.closePath();C.fillStyle=g;C.fill();
  C.strokeStyle='#e0b25a';C.lineWidth=2;C.beginPath();C.arc(ax,ay-14,30,Math.PI,0);C.stroke();C.beginPath();C.arc(ax,ay-14,20,Math.PI*1.08,Math.PI*1.92);C.stroke();
  C.strokeStyle='rgba(255,220,160,.25)';C.lineWidth=1;for(let i=1;i<6;i++){const a=Math.PI+i*Math.PI/6;C.beginPath();C.moveTo(ax+Math.cos(a)*8,ay-14+Math.sin(a)*8);C.lineTo(ax+Math.cos(a)*30,ay-14+Math.sin(a)*30);C.stroke()}
  fillRR(ax-3,ay-52,6,9,1.5,'#d9aa4a');ell(ax,ay-58,7.5,6,'#e6b94f');ell(ax,ay-61,4,2,'#ffe39a');circ(ax,ay-67,4,'#c9833f');
  for(const sg of [-1,1]){const x=ax+sg*46;for(let i=0;i<4;i++){ell(x,ay+29-i*3.4,7,2.8,'#f1c04a');C.strokeStyle='#c9972f';C.lineWidth=.8;C.beginPath();C.ellipse(x,ay+29-i*3.4,7,2.8,0,0,TAU);C.stroke()}
    circ(x+sg*9,ay+31,2.6,'#f1c04a');circ(x+sg*12,ay+29,2.2,'#e6b03e')}
  const k=(Math.sin(t*2)+1)/2;glowAt('255,215,110',ax+Math.sin(t*1.3)*14,ay-32-Math.cos(t*1.7)*8,11,.25+.5*k);
}};
function drawShrine(s){
  const ax=s.x,ay=s.y,t=T;
  shadow(ax+8,ay+40,70,15,.24);
  if(s.boost>.02){C.save();C.globalCompositeOperation='lighter';C.translate(ax,ay-22);C.rotate(t*.25);C.fillStyle='rgba('+s.rgb+','+(.10*s.boost)+')';
    for(let i=0;i<10;i++){C.rotate(TAU/10);C.beginPath();C.moveTo(0,0);C.lineTo(-11,-120);C.lineTo(11,-120);C.closePath();C.fill()}C.restore()}
  BUILD[s.key](ax,ay,t);
  offerings(s);
  glowAt(s.rgb,ax,ay-24,95+40*s.boost,.2+.06*Math.sin(t*1.7+s.ph)+.5*s.boost);
  pill(s.name,ax,ay+82,'700 15.5px '+FONT,'rgba(60,40,26,.74)','#fff0cf',10,22);
}

/* ============ อนุภาค ============ */
const smoke=[],petals=[],sparks=[],flies=[],flowers=[],birds=[];
for(let i=0;i<24;i++)flies.push({x:rnd(X0,X1),y:rnd(120,740),vx:rnd(-6,6),vy:rnd(-6,6),ph:rnd(0,6)});
function emitSmoke(s,n){for(let i=0;i<n;i++)smoke.push({x:s.x+rnd(-4,4),y:s.y+15,vx:rnd(-2,2),vy:-rnd(18,28),life:0,max:rnd(3.2,4.6),r:rnd(2,3),ph:rnd(0,6)})}
function emitPetal(x,y,s,w){petals.push({x,y,vy:rnd(14,26),ph:rnd(0,6),sw:rnd(8,18),rot:rnd(0,6),vr:rnd(-2,2),c:pick(s.petal),sz:rnd(2.6,4.2),endY:y+w})}
function bless(s){
  s.boost=1;
  for(let i=0;i<18;i++)emitPetal(s.x+rnd(-62,62),s.y-rnd(60,110),s,rnd(120,170));
  for(let i=0;i<16;i++)sparks.push({x:s.x+rnd(-20,20),y:s.y-rnd(10,40),vx:rnd(-30,30),vy:-rnd(20,60),life:0,max:rnd(1,1.8),rgb:s.rgb});
}
function updateFX(dt){
  for(const k in SH){const s=SH[k];
    s.boost=Math.max(0,s.boost-dt*.11);
    s.smokeT-=dt;if(s.smokeT<=0){emitSmoke(s,1);s.smokeT=s.boost>.1?.09:.2}
    s.petalT-=dt;if(s.petalT<=0){emitPetal(s.x+rnd(-60,60),s.y-rnd(70,100),s,rnd(110,150));s.petalT=rnd(.9,1.6)-s.boost*.6}
  }
  TREE.pt=(TREE.pt||0)-dt;if(TREE.pt<=0){emitPetal(TREE.x+rnd(-70,70),TREE.y-rnd(40,80),{petal:['#f4b6c4','#f9d6dc','#ffffff']},rnd(60,110));TREE.pt=rnd(.7,1.4)}
  for(let i=smoke.length-1;i>=0;i--){const p=smoke[i];p.life+=dt;p.y+=p.vy*dt;p.x+=Math.sin(T*1.5+p.ph)*8*dt+p.vx*dt;if(p.life>p.max)smoke.splice(i,1)}
  for(let i=petals.length-1;i>=0;i--){const p=petals[i];p.y+=p.vy*dt;p.x+=Math.sin(T*1.2+p.ph)*p.sw*dt;p.rot+=p.vr*dt;if(p.y>p.endY)petals.splice(i,1)}
  for(let i=sparks.length-1;i>=0;i--){const p=sparks[i];p.life+=dt;p.x+=p.vx*dt;p.y+=p.vy*dt;p.vy+=20*dt;if(p.life>p.max)sparks.splice(i,1)}
  if(petals.length>260)petals.splice(0,petals.length-260);
  for(const f of flies){f.vx+=rnd(-12,12)*dt;f.vy+=rnd(-12,12)*dt;f.vx=clamp(f.vx,-9,9);f.vy=clamp(f.vy,-9,9);f.x+=f.vx*dt;f.y+=f.vy*dt;if(f.x<X0)f.x=X1;if(f.x>X1)f.x=X0;if(f.y<100)f.y=740;if(f.y>740)f.y=100}
  for(let i=birds.length-1;i>=0;i--){const b=birds[i];b.k+=dt/b.dur;if(b.k>=1)birds.splice(i,1)}
}
function drawFX(){
  for(const p of smoke){const k=p.life/p.max;C.globalAlpha=(1-k)*.3;circ(p.x,p.y,p.r+k*8,'#f4ead6')}
  C.globalAlpha=1;
  for(const p of petals){
    C.save();C.translate(p.x,p.y);C.rotate(p.rot);C.scale(1,.55+.45*Math.abs(Math.sin(p.rot*1.7)));
    const fade=clamp((p.endY-p.y)/30,0,1);C.globalAlpha=fade;ell(0,0,p.sz,p.sz*.6,p.c);C.restore();
  }
  C.globalAlpha=1;
  for(const p of sparks){const k=p.life/p.max;glowAt(p.rgb,p.x,p.y,7*(1-k)+2,1-k)}
  for(const f of flies){glowAt('235,240,150',f.x,f.y,8,.25+.35*Math.sin(T*2+f.ph)**2)}
}
function drawBirds(){
  for(const b of birds){
    const pt=k=>{const u=1-k;return[u*u*u*b.p0[0]+3*u*u*k*b.p1[0]+3*u*k*k*b.p2[0]+k*k*k*b.p3[0],u*u*u*b.p0[1]+3*u*u*k*b.p1[1]+3*u*k*k*b.p2[1]+k*k*k*b.p3[1]]};
    const [x,y]=pt(b.k),[x2,y2]=pt(Math.min(1,b.k+.02)),ang=Math.atan2(y2-y,x2-x);
    const sc=.9+b.k*.9,fl=Math.sin(T*18+b.ph);
    ell(x+14,y+22+b.k*40,6*sc,2.4*sc,'rgba(40,28,16,.14)');
    C.save();C.translate(x,y);C.rotate(ang+Math.PI/2);C.scale(sc,sc);
    for(const sg of [-1,1]){C.save();C.translate(sg*2,-1);C.rotate(sg*(.12+fl*.5));ell(sg*9,0,9,3.2,b.c);C.restore()}
    ell(0,0,3.2,7,b.c);circ(0,-7.5,2.5,b.c);poly([[-2,6],[2,6],[0,12]],b.c);circ(0,-9.5,.9,'#e8a03a');
    C.restore();
  }
}

/* ============ ดอกไม้ ============ */
function plantFlower(){
  const slot=SLOTS[slotIdx%SLOTS.length];slotIdx++;
  for(let i=flowers.length-1;i>=0;i--)if(flowers[i].slot===slot)flowers.splice(i,1);
  const [c,c2]=pick([['#f08aa4','#ffe08a'],['#f5f0e6','#f2c14e'],['#f2a65a','#fff0b0'],['#c9a0dc','#ffe08a'],['#ff7a6a','#ffe08a']]);
  return {slot,x:slot.x,y:slot.y,c,c2,ph:rnd(0,6),t0:Infinity};
}
function drawFlower(f){
  const k=ease((T-f.t0)/1.6);if(k<=0)return;
  const sw=Math.sin(T*1.4+f.ph)*1.2*k,hx=f.x+sw,hy=f.y-9*k;
  C.strokeStyle='#5f7f4c';C.lineWidth=1.6;C.beginPath();C.moveTo(f.x,f.y);C.quadraticCurveTo(f.x,f.y-5*k,hx,hy);C.stroke();
  ell(f.x-3*k,f.y-3*k,3*k,1.4*k,'#6f9459',-.5);ell(f.x+3*k,f.y-4*k,3*k,1.4*k,'#6f9459',.5);
  for(let i=0;i<5;i++){const a=i*TAU/5+f.ph;circ(hx+Math.cos(a)*3.2*k,hy+Math.sin(a)*3*k,2.5*k,f.c)}
  circ(hx,hy,1.9*k,f.c2);
}

/* ============ ตัวละคร ============ */
const TOPS=['#b9653e','#c9a15a','#7f9a70','#d8c8a0','#a4573a','#6c8a86','#c47f4f','#e0b98a'],PANTS=['#6b5238','#4d5a45','#7a5a3c'],HAIR=['#2d2018','#3b2a1c','#1f1812','#5a3b24'],SKIN=['#e8c19a','#d9a982','#f0cfae','#c8956c'];
const walkers=[],spawnQ=[];
function lane(){return rnd(-10,10)}
class Walker{
  constructor(name,steps,speed,opt){
    opt=opt||{};this.key=opt.key;
    this.name=name;this.steps=steps;this.speed=speed;this.alpha=0;this.ph=rnd(0,6);this.el=0;
    this.x=opt.x!=null?opt.x:steps[0].pts[0][0];this.y=opt.y!=null?opt.y:steps[0].pts[0][1];
    this.vx=0;this.vy=-1;this.ux=0;this.uy=0;this._mv=false;this.moving=false;this.pose=null;this.bubble=null;this.dead=false;
    this.top=pick(TOPS);this.sash=pick(TOPS);this.pant=pick(PANTS);this.hair=pick(HAIR);this.skin=pick(SKIN);this.hat=Math.random()<.28;this.amb=!name;
  }
  update(dt){
    this.alpha=Math.min(1,this.alpha+dt*2);
    if(!this._mv){const f=Math.max(0,1-dt*12);this.ux*=f;this.uy*=f}this._mv=false;
    const st=this.steps[0];if(!st){this.dead=true;return}
    if(!st.started){st.started=true;st.el=0;st.i=0;if(st.on)st.on(this)}
    this.moving=false;
    if(st.t!=='wait'){this.pose=null;this.bubble=null}
    if(st.t==='go'){
      const tg=st.pts[st.i];if(!tg){this.steps.shift();return}
      if(this.moveTo(tg[0],tg[1],this.speed,dt,st.i<st.pts.length-1?10:0))st.i++;
    }else if(st.t==='wait'){
      st.el+=dt;this.pose=st.pose;this.bubble=st.bubble;this.el=st.el;
      if(st.el>=st.dur){this.pose=null;this.bubble=null;this.steps.shift()}
    }else if(st.t==='wander'){
      st.el+=dt;if(st.el>=st.dur){this.steps.shift();return}
      if(st.pause>0){st.pause-=dt;return}
      if(!st.tg)st.tg=[st.cx+rnd(-st.rx,st.rx),st.cy+rnd(-st.ry,st.ry)];
      if(this.moveTo(st.tg[0],st.tg[1],this.speed*.7,dt)){st.tg=null;st.pause=rnd(.8,3)}
    }else if(st.t==='stroll'){
      st.el+=dt;if(st.el>=st.dur){this.steps.shift();return}
      if(st.pause>0){st.pause-=dt;return}
      if(!st.route||!st.route.length){
        const sp=pick(STROLL),l=lane(),tx=rnd(sp[0],sp[1]),ty=rnd(sp[2],sp[3]);
        st.route=[[MAINX+l,this.y],[MAINX+l,ty],[tx,ty]];
      }
      if(this.moveTo(st.route[0][0],st.route[0][1],this.speed*.24,dt,st.route.length>1?10:0)){st.route.shift();if(!st.route.length)st.pause=rnd(1.5,5)}
    }
    if(this.steps.length===0||(this.steps[0].t==='go'&&this.steps[0].exit&&this.y>ENT_Y+4))this.alpha=clamp(1-(this.y-ENT_Y)/26,0,1);
    if(this.y>ENT_Y+26&&this.steps.length<=1&&!this.amb)this.dead=true;
  }
  // เคลื่อนที่แบบมีความเร็วต่อเนื่อง: เร่งนุ่ม ชะลอก่อนถึงจุดหมาย และเลี้ยวโค้งที่จุดผ่าน (rad>0)
  moveTo(tx,ty,sp,dt,rad){
    rad=rad||0;
    const dx=tx-this.x,dy=ty-this.y,d=Math.hypot(dx,dy);
    if(d<=Math.max(rad,.01)){
      this._mv=true;if(!rad){this.x=tx;this.y=ty}
      this.moving=Math.hypot(this.ux,this.uy)>2;return true;
    }
    let want=sp;if(!rad&&d<30)want=sp*Math.max(.3,d/30);
    const k=Math.min(1,dt*6);
    this.ux+=(dx/d*want-this.ux)*k;this.uy+=(dy/d*want-this.uy)*k;
    const v=Math.hypot(this.ux,this.uy),step=v*dt;this._mv=true;
    if(!rad&&d<=Math.max(step,.6)){this.x=tx;this.y=ty;this.ux=this.uy=0;this.moving=false;return true}
    this.x+=this.ux*dt;this.y+=this.uy*dt;
    if(v>2){this.vx=this.ux/v;this.vy=this.uy/v}
    this.moving=v>2;this.ph+=dt*(3.5+v*.09);return false;
  }
}
function drawWalker(w){
  if(w.alpha<=0)return;
  const x=w.x,y=w.y;C.globalAlpha=w.alpha;
  C.save();C.translate(x,y);C.scale(WS,WS);C.translate(-x,-y);
  shadow(x+2,y+1.5,8,3,.25);
  const mv=w.moving,sw=mv?Math.sin(w.ph):0,bob=mv?Math.abs(Math.cos(w.ph))*1.4:0;
  let crouch=0,bow=0,arms=0;
  if(w.pose==='plant')crouch=7;else if(w.pose==='pray'){bow=2.5+Math.sin(w.el*2.2)*1.3;arms=1}
  else if(w.pose==='reach')arms=2;else if(w.pose==='release')arms=3;
  C.fillStyle=w.pant;
  rr(x-4.6,y-9+crouch*.5-Math.max(0,sw)*1.8,3.4,9-crouch*.5,1.5);C.fill();
  rr(x+1.2,y-9+crouch*.5-Math.max(0,-sw)*1.8,3.4,9-crouch*.5,1.5);C.fill();
  const top=y-21+crouch-bob;
  fillRR(x-6.5,top,13,13-crouch*.3,4,w.top);fillRR(x-6.5,top+8,13,2.3,1,w.sash);
  if(arms===0){fillRR(x-9.4,top+1.5+sw*1.2,3.2,9,1.6,w.top);fillRR(x+6.2,top+1.5-sw*1.2,3.2,9,1.6,w.top)}
  else if(arms===1){fillRR(x-8.5,top+2,3.2,8,1.6,w.top);fillRR(x+5.3,top+2,3.2,8,1.6,w.top);circ(x,top+7,2.2,w.skin)}
  else if(arms===2){fillRR(x-9.4,top-8,3.2,11,1.6,w.top);fillRR(x+6.2,top-8,3.2,11,1.6,w.top);circ(x-8,top-9,1.9,w.skin);circ(x+8,top-9,1.9,w.skin)}
  else if(arms===3){fillRR(x-9,top+2,3.2,8,1.6,w.top);fillRR(x+5.8,top+2,3.2,8,1.6,w.top);circ(x-7,top+11,1.9,w.skin);circ(x+7,top+11,1.9,w.skin)}
  const hy=top-5.4+bow,back=mv&&w.vy<-.25;
  circ(x,hy,5.8,w.skin);
  C.fillStyle=w.hair;C.beginPath();if(back)C.arc(x,hy,6,0,TAU);else C.arc(x,hy-.5,6,Math.PI*1.02,TAU*.99);C.fill();
  if(!back){circ(x-2,hy+.8,.75,'#2b1d14');circ(x+2,hy+.8,.75,'#2b1d14')}
  if(w.hat){poly([[x-9.5,hy-2],[x,hy-12.5],[x+9.5,hy-2]],'#d8bd7c');line(x-9.5,hy-2,x+9.5,hy-2,'#a98a4e',1.2)}
  C.restore();
  if(w.name){
    const ny=y-52*WS;pill(w.name,x,ny,'700 16.5px '+FONT,'rgba(50,34,22,.78)','#fff3d6',8,23);
    if(w.bubble){
      const bf='700 15.5px '+FONT,by=ny-27,bw=textW(w.bubble,bf)+22;
      fillRR(x-bw/2,by-12,bw,24,12,'#fff6e2');poly([[x-5,by+11],[x+5,by+11],[x,by+18]],'#fff6e2');
      C.fillStyle='#6b3a22';C.font=bf;C.textAlign='center';C.textBaseline='middle';C.fillText(w.bubble,x,by+.5);
    }
  }
  C.globalAlpha=1;
}
/* ===== แผนการเดินของผู้ส่งของขวัญ =====
   เดินไปทำพิธี -> เดินเล่นสุ่มในหมู่บ้าน (STAY วินาที) -> เดินออกประตู
   ถ้าส่งซ้ำระหว่างที่ยังอยู่ในหมู่บ้าน จะต่อคิวไปจุดใหม่จากตำแหน่งปัจจุบัน ไม่เริ่มใหม่ */
const STAY=[40,70]; // เวลาเดินเล่นหลังส่งของ ก่อนออกจากหมู่บ้าน (วินาที)
const STROLL=[ // จุดเดินเล่น [x ต่ำสุด,x สูงสุด,y ต่ำสุด,y สูงสุด] (อยู่บนทางเดินทั้งหมด)
  [130,245,375,381],[130,245,570,576],[295,410,540,546],[295,410,705,711],
  [150,245,215,221],[120,245,752,756],[240,300,548,594],[250,290,850,890]
];
function routeStep(p){
  const st={t:'go',pts:null,on:w=>{const l=lane();st.pts=[[MAINX+l,w.y],[MAINX+l,p.sy],[p.tx,p.ty]]}};
  return st;
}
function exitStep(){
  const st={t:'go',pts:null,exit:true,on:w=>{const l=lane();st.pts=[[MAINX+l,w.y],[MAINX+l,ENT_Y],[MAINX+l,ENT_Y+30]]}};
  return st;
}
function tailSteps(){return [{t:'stroll',dur:rnd(STAY[0],STAY[1])},exitStep()]}
function planGift(g){
  const mk=(dur,pose,on)=>({t:'wait',act:true,dur,pose,bubble:g.bubble,on});
  let sy,tx,ty,act;
  if(g.kind==='shrine'){
    const s=SH[g.s];sy=s.stand;tx=s.x+rnd(-22,22);ty=s.stand+rnd(0,7);
    act=mk(1.8,'pray',()=>{bless(s);audio.templeBell()});
  }else if(g.kind==='tree'){
    sy=215;tx=TREE.x+40+rnd(-8,8);ty=215+rnd(0,6);
    act=mk(1.6,'reach',()=>{addTag();audio.chime()});
  }else if(g.kind==='fish'){
    const px=REL.fish+rnd(-8,8);sy=REL.y;tx=px;ty=REL.y+rnd(0,4);
    act=mk(1.4,'release',()=>{const fx=px+rnd(10,40),fy=rnd(RT+18,RB-14);
      fishes.push({st:'arc',k:0,sx:px+6,sy:REL.y-14,tx:fx,ty:fy,c:pick(['#f08a3a','#f4f0e6','#e8b04a'])});audio.splash()});
  }else if(g.kind==='turtle'){
    const px=REL.turtle+rnd(-8,8);sy=REL.y;tx=px;ty=REL.y+rnd(0,4);
    act=mk(1.4,'release',()=>{turtles.push({st:'arc',k:0,sx:px+6,sy:REL.y-8,tx:px+rnd(10,40),ty:rnd(RT+20,RB-16),x:px,y:REL.y,ph:0});audio.splash()});
  }else if(g.kind==='bird'){
    const px=REL.bird+rnd(-8,8);sy=REL.y;tx=px;ty=REL.y+rnd(0,4);
    act=mk(1.4,'release',()=>{birds.push({k:0,dur:rnd(6,8),ph:rnd(0,6),c:pick(['#fffaf0','#fff3df','#f1ece2']),
      p0:[px+4,REL.y-24],p1:[px+rnd(-90,90),REL.y-200],p2:[px+rnd(-180,180),REL.y-460],p3:[rnd(200,480),-50]});audio.chime()});
  }else if(g.kind==='flower'||g.kind==='flowerjoin'){
    const f=plantFlower();sy=f.slot.y+14;tx=f.slot.x;ty=sy;
    act=mk(1.4,'plant',()=>{f.t0=T+.9;flowers.push(f);audio.chime()});
  }else{ // join
    sy=HUB.y+40;tx=MAINX+rnd(-10,10);ty=sy;
    act=mk(1.4,null,()=>audio.chime());
  }
  return {sy,tx,ty,act};
}
function makeWalker(name,g,key){
  const p=planGift(g);
  const steps=[routeStep(p),p.act].concat(tailSteps());
  return new Walker(name,steps,rnd(115,135),{x:MAINX+lane(),y:ENT_Y,key});
}
// คนเดิมส่งซ้ำก่อนออกจากหมู่บ้าน: เก็บพิธีที่ยังค้างอยู่ไว้ แล้วต่อด้วยจุดหมายใหม่จากตำแหน่งปัจจุบัน
function sendWalker(w,g){
  const p=planGift(g);let keep=[];
  for(let i=w.steps.length-1;i>=0;i--)if(w.steps[i].act){keep=w.steps.slice(0,i+1);break}
  w.steps=keep.concat([routeStep(p),p.act],tailSteps());
}
function spawnAmbient(){
  const w=new Walker(null,[{t:'wander',dur:Infinity,cx:270,cy:650,rx:34,ry:100}],rnd(24,32),{x:270+rnd(-20,20),y:rnd(560,760)});
  w.alpha=1;walkers.push(w);
}

/* ============ ของขวัญ: จับคู่ 14 ของขวัญกับผลลัพธ์ตามรายการที่กำหนด ============ */
const GIFTS={
 rose:{ico:'🌹',th:'กุหลาบ',en:'Rose',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/eba3a9bb85c33e017f3648eaf88d7189~tplv-obj.webp',desc:'เข้าร่วมหมู่บ้าน',kind:'join',msg:'ได้เข้าร่วมหมู่บ้านแล้ว',bubble:'🌹 ยินดีต้อนรับสู่หมู่บ้าน',col:'#ffd98a',al:['rose','กุหลาบ']},
 flameheart:{ico:'❤️‍🔥',th:'เสียงลูกเป็นไฟ',en:'Flame heart',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/resource/b199d028d5beb081fe16edcf77db0830.png~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งความรัก',kind:'shrine',s:'love',msg:'ได้ไหว้เทพเจ้าแห่งความรัก ขอให้ความรักราบรื่นแล้ว',bubble:'ขอให้ความรักราบรื่น ❤️‍🔥',col:'#ff8fa8',al:['flame heart','flameheart','เสียงลูกเป็นไฟ']},
 rainbowtulip:{ico:'🌷',th:'ทิวลิปสีรุ้ง',en:'Rainbow Tulip',img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/f35d93703a784afc97f24beea1f2b1b3.png~tplv-obj.webp',desc:'ปลูกดอกไม้ให้หมู่บ้าน',kind:'flower',msg:'ได้ปลูกดอกไม้ให้กับหมู่บ้านแล้ว',bubble:'🌷 เติมสีสันให้หมู่บ้าน',col:'#e8a8d8',al:['rainbow tulip','rainbowtulip','ทิวลิปสีรุ้ง']},
 heartpuff:{ico:'💗',th:'ม่อนป้องรัก',en:'Heart Puff',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/resource/68c21ef420f49b87543de354b2e30b8d.png~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งสุขภาพ',kind:'shrine',s:'health',msg:'ได้ไหว้เทพเจ้าแห่งสุขภาพ ขอให้มีสุขภาพแข็งแรงแล้ว',bubble:'ขอให้สุขภาพแข็งแรง 💗',col:'#ff8fa8',al:['heart puff','heartpuff','fluffy heart','love you so much','loveyousomuch','ม่อนป้องรัก']},
 awesome:{ico:'🐱',th:'เยี่ยมสุดๆ',en:"You're awesome",img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/e9cafce8279220ed26016a71076d6a8a.png~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งการงาน',kind:'shrine',s:'work',msg:'ได้ไหว้เทพเจ้าแห่งการงาน ขอให้งานสำเร็จไปด้วยดีแล้ว',bubble:'ขอให้งานสำเร็จ 🐱',col:'#ffc24a',al:["you're awesome",'youre awesome','เยี่ยมสุดๆ']},
 starfish:{ico:'⭐',th:'ปลาดาว',en:'Starfish',img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/279903174b4ca8e1c7a78e649af65bcc.png~tplv-obj.webp',desc:'ปล่อยเต่า',kind:'turtle',msg:'ได้ปล่อยเต่าคืนสู่สายน้ำแล้ว',bubble:'🐢 ปล่อยเต่าคืนธรรมชาติ',col:'#9bd3ff',al:['starfish','ปลาดาว']},
 wink:{ico:'😉',th:'ปิ๊สปิ๊ส',en:'Wink wink',img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/4a68411b3e92fc2bf68d458d5f906b74.png~tplv-obj.webp',desc:'ปล่อยนก',kind:'bird',msg:'ได้ปล่อยนกให้เป็นอิสระแล้ว',bubble:'🕊️ ขอให้นกโบยบินอย่างอิสระ',col:'#ff8fa8',al:['wink wink','winkwink','ปิ๊สปิ๊ส']},
 loveyou:{ico:'💝',th:'รักนะ',en:'Love you',img:'https://beetgames.com/images/gifts/love_you.webp',desc:'ไหว้เทพเจ้าแห่งความรัก',kind:'shrine',s:'love',msg:'ได้ไหว้เทพเจ้าแห่งความรัก ขอให้พบรักดี ๆ ในเร็ว ๆ นี้แล้ว',bubble:'ขอให้พบรักดี ๆ ในเร็ว ๆ นี้ 💝',col:'#ff9fb4',al:['love you','loveyou','รักนะ']},
 mirwas:{ico:'🥁',th:'จังหวะกลองมีร์วาส',en:'Mirwas Beat',img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/afb61610b91baf60487c427d96fbecf4.png~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งสุขภาพ',kind:'shrine',s:'health',msg:'ได้ไหว้เทพเจ้าแห่งสุขภาพ ขอให้อายุยืนนานแล้ว',bubble:'ขอให้อายุยืนยาว 🥁',col:'#e7c17d',al:['mirwas beat','mirwasbeat','จังหวะกลองมีร์วาส']},
 rainbow:{ico:'🌈',th:'รุ้ง',en:'Rainbow',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/resource/644f6029df42ac078e6f13de19c6640c.png~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งความมั่งคั่ง',kind:'shrine',s:'wealth',msg:'ได้ไหว้เทพเจ้าแห่งความมั่งคั่ง ขอให้ร่ำรวย ๆ แล้ว',bubble:'ขอให้มั่งคั่งร่ำรวย 🌈',col:'#e8b6ff',al:['rainbow','รุ้ง']},
 pop:{ico:'🎤',th:'จังหวะ',en:'Pop',img:'https://p16-webcast.tiktokcdn.com/img/alisg/webcast-sg/resource/0b4f61e8ab637f11449300d03929ef87.png~tplv-obj.webp',desc:'ปล่อยปลา',kind:'fish',msg:'ได้ปล่อยปลาคืนสู่สายน้ำแล้ว',bubble:'🐟 ปล่อยปลาคืนสู่สายน้ำ',col:'#d9b8ff',al:['pop','จังหวะ']},
 giveitall:{ico:'🎁',th:'ส่ง',en:'Give It All',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/c2d82333bf930904ee55f3dfb71f9374~tplv-obj.webp',desc:'ฝากคำอธิษฐานไว้ที่ต้นไม้',kind:'tree',msg:'ได้ฝากคำอธิษฐานไว้กับต้นไม้ ขอให้ความปรารถนาเป็นจริงแล้ว',bubble:'🎁 ขอให้ความปรารถนาเป็นจริง',col:'#ffd98a',al:['give it all','giveitall','ส่ง']},
 gg:{ico:'🎉',th:'จา',en:'GG',img:'https://p16-webcast.tiktokcdn.com/img/maliva/webcast-va/3f02fa9594bd1495ff4e8aa5ae265eef~tplv-obj.webp',desc:'ไหว้เทพเจ้าแห่งความมั่งคั่ง',kind:'shrine',s:'wealth',msg:'ได้ไหว้เทพเจ้าแห่งความมั่งคั่ง ขอให้โชคดีถูกรางวัลใหญ่แล้ว',bubble:'ขอให้โชคดีถูกรางวัล 🎉',col:'#e8b6ff',al:['gg','ja','จา']},
 goforit:{ico:'🚀',th:'รีบเลย',en:'Go for it!',img:'https://beetgames.com/images/gifts/go_for_it.webp',desc:'ไหว้เทพเจ้าแห่งการงาน',kind:'shrine',s:'work',msg:'ได้ไหว้เทพเจ้าแห่งการงาน ขอให้ได้งานใหม่ที่ดีแล้ว',bubble:'ขอให้ได้งานใหม่ที่ดี 🚀',col:'#ffc24a',al:['go for it','goforit','รีบเลย']}
};
const norm=s=>String(s||'').normalize('NFKC').toLowerCase().replace(/[^\p{L}\p{N}\p{M}]+/gu,'');
const ALIAS={};for(const k in GIFTS){ALIAS[norm(k)]=k;GIFTS[k].al.forEach(a=>ALIAS[norm(a)]=k)}
// จับคู่ด้วยรหัสรูปของขวัญ (TikFinity ส่ง giftPictureUrl มาด้วย) เผื่อชื่อไม่ตรง
const PICKEY={};
const picId=u=>{const m=String(u||'').match(/[0-9a-f]{32}/i);return m?m[0].toLowerCase():''};
for(const k in GIFTS){const id=picId(GIFTS[k].img);if(id)PICKEY[id]=k}
const ALIAS_KEYS=Object.keys(ALIAS).filter(a=>a.length>=5).sort((a,b)=>b.length-a.length);
function giftKey(type,pic){
  const n=norm(type);
  if(n&&ALIAS[n])return ALIAS[n];
  const id=picId(pic);if(id&&PICKEY[id])return PICKEY[id];
  if(n){const f=ALIAS_KEYS.find(a=>n.includes(a));if(f)return ALIAS[f]}
  return null;
}
function buildPanel(){
  const p=$('panel');const h=document.createElement('h1');h.textContent='🎁 ส่งของขวัญ 1 เหรียญ';p.appendChild(h);
  const rows=[
    ['#ff8fa8',['flameheart','loveyou'],'ไหว้เทพเจ้าแห่งความรัก'],
    ['#8fd6a4',['heartpuff','mirwas'],'ไหว้เทพเจ้าแห่งสุขภาพ'],
    ['#ffc24a',['awesome','goforit'],'ไหว้เทพเจ้าแห่งการงาน'],
    ['#e8b6ff',['rainbow','gg'],'ไหว้เทพเจ้าแห่งความมั่งคั่ง'],
    ['#ffd98a',['giveitall'],'ฝากคำอธิษฐานไว้ที่ต้นไม้'],
    ['#d9b8ff',['pop'],'ปล่อยปลา'],
    ['#9bd3ff',['starfish'],'ปล่อยเต่า'],
    ['#ff8fa8',['wink'],'ปล่อยนก'],
    ['#e8a8d8',['rainbowtulip'],'ปลูกดอกไม้ให้หมู่บ้าน'],
    ['#ffd98a',['rose'],'เข้าร่วมหมู่บ้าน']
  ];
  for(const [col,ks,txt,badge] of rows){
    const r=document.createElement('div');r.className='r';r.style.setProperty('--c',col);
    for(const k of ks){const im=document.createElement('img');im.src=GIFTS[k].img||'';im.alt=GIFTS[k].en;im.onerror=()=>{im.style.display='none'};r.appendChild(im)}
    const sp=document.createElement('span');sp.textContent=txt;r.appendChild(sp);
    if(badge){const b=document.createElement('b');b.className='n9';b.textContent=badge;r.appendChild(b)}
    p.appendChild(r);
  }
  const tip=document.createElement('div');tip.className='tip';
  tip.innerHTML='💬 คอมเมนต์ในแชต: <b>ไหว้พระ</b> · <b>ปล่อยนก</b><br><b>ปล่อยปลา</b> · <b>ปลูกดอกไม้</b>';
  p.appendChild(tip);
}
function toast(g,name,msg){
  const box=$('toasts'),d=document.createElement('div');d.className='t';
  const im=document.createElement('img');im.src=g.img||'';im.alt=g.en||g.th;im.onerror=()=>{im.style.display='none'};
  const b=document.createElement('b'),c=document.createElement('span');
  b.textContent=name;c.textContent=' '+msg;d.append(im,b,c);box.appendChild(d);
  while(box.children.length>2)box.firstChild.remove();
  setTimeout(()=>{d.classList.add('out');setTimeout(()=>d.remove(),400)},3600);
}
const speakable=s=>String(s||'').replace(/[^\p{L}\p{N}\p{M}\s]/gu,' ').replace(/\s+/g,' ').trim();
function villageGift(type,name,pic,uid){
  const k=giftKey(type,pic);if(!k)return false;
  name=String(name||'ผู้มาเยือน').trim();if(name.length>16)name=name.slice(0,15)+'…';
  const g=GIFTS[k];toast(g,name,g.msg);if(spawnQ.length>60)spawnQ.shift();spawnQ.push({name,g,key:String(uid||name)});
  // อ่านชื่อผู้ส่งก่อน แล้วตามด้วยประโยคผลลัพธ์ โดยไม่อ่านชื่อของขวัญ
  tts.say((speakable(name)||'ผู้มาเยือน')+' '+g.msg);return true;
}
window.villageGift=villageGift;
// พิมพ์ 9 ในแชต: เดินเข้ามาร่วมหมู่บ้านและปลูกดอกไม้
const NINE_ACT={ico:'9️⃣',th:'พิมพ์ 9',en:'9',img:GIFTS.rainbowtulip.img,kind:'flowerjoin',
  msg:'ได้เข้าร่วมหมู่บ้านและปลูกดอกไม้แล้ว',bubble:'🌷 ขอปลูกดอกไม้ให้หมู่บ้าน'};
const nineLast=new Map();
function villageNine(name,uid,g){g=g||NINE_ACT;
  const key=String(uid||name||'?'),now=Date.now();
  if(now-(nineLast.get(key)||0)<8000)return false; // กันสแปมจากคนเดิม
  nineLast.set(key,now);
  if(nineLast.size>400)for(const [k,t] of nineLast)if(now-t>60000)nineLast.delete(k);
  name=String(name||'ผู้มาเยือน').trim();if(name.length>16)name=name.slice(0,15)+'…';
  toast(g,name,g.msg);if(spawnQ.length>60)spawnQ.shift();spawnQ.push({name,g,key});
  tts.say((speakable(name)||'ผู้มาเยือน')+' '+g.msg);return true;
}
window.villageNine=villageNine;
/* ===== คอมเมนต์ในแชต -> ตัวละครทำ 4 อย่าง =====
   พิมพ์ "ไหว้พระ" = ไหว้ศาลแบบสุ่ม (รัก/สุขภาพ/งาน/เงิน)
   "ปล่อยนก" / "ปล่อยปลา" / "ปลูกดอกไม้" = ทำตามที่พิมพ์ (ไม่ใช้ตัวเลข) */
const CHAT_SHRINE={
  love:{gift:'flameheart',msg:'ได้ไหว้เทพเจ้าแห่งความรักแล้ว',bubble:'ขอให้ความรักราบรื่น ❤️'},
  health:{gift:'heartpuff',msg:'ได้ไหว้เทพเจ้าแห่งสุขภาพแล้ว',bubble:'ขอให้สุขภาพแข็งแรง 💗'},
  work:{gift:'awesome',msg:'ได้ไหว้เทพเจ้าแห่งการงานแล้ว',bubble:'ขอให้งานสำเร็จ 🙏'},
  wealth:{gift:'rainbow',msg:'ได้ไหว้เทพเจ้าแห่งความมั่งคั่งแล้ว',bubble:'ขอให้ร่ำรวยมั่งคั่ง 🌈'}
};
function chatActFor(kind){
  if(kind==='shrine'){const s=pick(Object.keys(CHAT_SHRINE)),c=CHAT_SHRINE[s];return{img:GIFTS[c.gift].img,en:'shrine',kind:'shrine',s,msg:c.msg,bubble:c.bubble}}
  if(kind==='bird')return{img:GIFTS.wink.img,en:'bird',kind:'bird',msg:'ได้ปล่อยนกให้เป็นอิสระแล้ว',bubble:GIFTS.wink.bubble};
  if(kind==='fish')return{img:GIFTS.pop.img,en:'fish',kind:'fish',msg:'ได้ปล่อยปลาคืนสู่สายน้ำแล้ว',bubble:GIFTS.pop.bubble};
  return NINE_ACT;
}
function chatKind(t){
  const n=norm(t);
  if(!n)return null;
  if(n.includes('ไหว้')||n.includes('สาธุ'))return'shrine';
  if(n==='นก'||n.includes('ปล่อยนก'))return'bird';
  if(n==='ปลา'||n.includes('ปล่อยปลา'))return'fish';
  if(n==='ดอกไม้'||n.includes('ปลูกดอกไม้')||n.includes('ปลูกดอก'))return'flower';
  return null;
}
function villageComment(name,uid,kind){return villageNine(name,uid,chatActFor(kind))}
window.villageComment=villageComment;
window.addEventListener('message',e=>{const d=e.data;if(d&&d.gift)villageGift(d.gift,d.name)});

/* ============ เสียงบรรยากาศ (สังเคราะห์ด้วย WebAudio) ============ */
const audio=(()=>{
  let AC=null,master=null,buf=null,muted=false;
  const noise=(type,freq,q,gain,lfoHz,lfoAmt)=>{
    const s=AC.createBufferSource();s.buffer=buf;s.loop=true;
    const f=AC.createBiquadFilter();f.type=type;f.frequency.value=freq;f.Q.value=q;
    const g=AC.createGain();g.gain.value=gain;s.connect(f);f.connect(g);g.connect(master);s.start();
    if(lfoHz){const o=AC.createOscillator(),og=AC.createGain();o.frequency.value=lfoHz;og.gain.value=lfoAmt;o.connect(og);og.connect(g.gain);o.start()}
  };
  const bell=()=>{
    if(!AC||muted)return;const now=AC.currentTime,f0=pick([261.6,293.7,329.6]);
    const out=AC.createGain();out.gain.value=.05;const lp=AC.createBiquadFilter();lp.type='lowpass';lp.frequency.value=1800;
    const dl=AC.createDelay(1);dl.delayTime.value=.34;const fb=AC.createGain();fb.gain.value=.35;
    out.connect(lp);lp.connect(master);lp.connect(dl);dl.connect(fb);fb.connect(dl);dl.connect(master);
    [[1,.5],[2.01,.25],[2.76,.18],[5.4,.08]].forEach(([r,a])=>{
      const o=AC.createOscillator(),g=AC.createGain();o.frequency.value=f0*r;o.type='sine';
      g.gain.setValueAtTime(0,now);g.gain.linearRampToValueAtTime(a,now+.01);g.gain.exponentialRampToValueAtTime(.0005,now+6);
      o.connect(g);g.connect(out);o.start(now);o.stop(now+6.2);
    });
  };
  const loopBell=()=>{bell();setTimeout(loopBell,rnd(18000,34000))};
  return{
    start(){
      if(AC){AC.resume();return}
      const A=window.AudioContext||window.webkitAudioContext;if(!A)return;
      AC=new A();master=AC.createGain();master.gain.value=muted?0:.9;master.connect(AC.destination);
      buf=AC.createBuffer(1,AC.sampleRate*3,AC.sampleRate);const d=buf.getChannelData(0);let l=0;
      for(let i=0;i<d.length;i++){const w=Math.random()*2-1;l=(l+.02*w)/1.02;d[i]=l*3.5}
      // ปิดเสียงบรรยากาศแบบ Noise ต่อเนื่อง เพื่อตัดเสียงซ่า/เสียงลมพื้นหลัง
      // คงเสียงเอฟเฟกต์เฉพาะเหตุการณ์ เช่น ระฆัง เสียงตกน้ำ และเสียงเรือ ไว้
      setTimeout(loopBell,6000);
    },
    boat(){
      if(!AC||muted)return;const now=AC.currentTime;
      const s=AC.createBufferSource();s.buffer=buf;const f=AC.createBiquadFilter();f.type='lowpass';f.frequency.value=320;
      const g=AC.createGain();g.gain.setValueAtTime(0,now);g.gain.linearRampToValueAtTime(.16,now+3);g.gain.linearRampToValueAtTime(0,now+8);
      s.connect(f);f.connect(g);g.connect(master);s.start(now,rnd(0,1.5),8.2);
      for(let i=0;i<5;i++){ // เสียงพายเบาๆ
        const t0=now+i*1.1,o=AC.createBufferSource();o.buffer=buf;const bf=AC.createBiquadFilter();bf.type='bandpass';bf.frequency.value=900;bf.Q.value=1;
        const og=AC.createGain();og.gain.setValueAtTime(0,t0);og.gain.linearRampToValueAtTime(.05,t0+.15);og.gain.linearRampToValueAtTime(0,t0+.7);
        o.connect(bf);bf.connect(og);og.connect(master);o.start(t0,rnd(0,2),.8);
      }
    },
    templeBell(){
      if(!AC||muted)return;const now=AC.currentTime;
      // ระฆังศาล: เสียงโลหะกังวานหลายฮาร์มอนิกและหางเสียงยาว
      const out=AC.createGain(),lp=AC.createBiquadFilter();lp.type='lowpass';lp.frequency.value=2600;
      out.gain.setValueAtTime(.0001,now);out.gain.linearRampToValueAtTime(.20,now+.012);out.gain.exponentialRampToValueAtTime(.0003,now+3.4);
      out.connect(lp);lp.connect(master);
      [[1,1],[2.72,.38],[4.1,.22],[5.43,.12],[6.8,.07]].forEach(([ratio,vol])=>{
        const o=AC.createOscillator(),g=AC.createGain();o.type='sine';o.frequency.setValueAtTime(660*ratio,now);
        g.gain.setValueAtTime(.0001,now);g.gain.linearRampToValueAtTime(vol,now+.008);g.gain.exponentialRampToValueAtTime(.0001,now+3.2);
        o.connect(g);g.connect(out);o.start(now);o.stop(now+3.3);
      });
    },
    splash(){
      if(!AC||muted)return;const now=AC.currentTime;
      // เสียงวัตถุกระทบน้ำ ตามด้วยละอองน้ำกระเพื่อม
      const src=AC.createBufferSource();src.buffer=buf;
      const bp=AC.createBiquadFilter();bp.type='bandpass';bp.frequency.setValueAtTime(1250,now);bp.frequency.exponentialRampToValueAtTime(380,now+.42);bp.Q.value=.65;
      const g=AC.createGain();g.gain.setValueAtTime(.0001,now);g.gain.linearRampToValueAtTime(.23,now+.018);g.gain.exponentialRampToValueAtTime(.0001,now+.62);
      src.connect(bp);bp.connect(g);g.connect(master);src.start(now,rnd(0,.5),.7);
      const tail=AC.createBufferSource();tail.buffer=buf;
      const hp=AC.createBiquadFilter();hp.type='highpass';hp.frequency.value=1800;
      const tg=AC.createGain();tg.gain.setValueAtTime(.0001,now+.04);tg.gain.linearRampToValueAtTime(.075,now+.10);tg.gain.exponentialRampToValueAtTime(.0001,now+.85);
      tail.connect(hp);hp.connect(tg);tg.connect(master);tail.start(now+.035,rnd(0,.8),.8);
    },
    chime(){
      if(!AC||muted)return;const now=AC.currentTime,f=pick([523.25,587.33,659.25,783.99,880]);
      for(const m of [1,2]){const o=AC.createOscillator(),g=AC.createGain();o.type='sine';o.frequency.value=f*m;
        g.gain.setValueAtTime(0,now);g.gain.linearRampToValueAtTime(.07/m,now+.01);g.gain.exponentialRampToValueAtTime(.0005,now+1.4);
        o.connect(g);g.connect(master);o.start(now);o.stop(now+1.5)}
    },
    toggle(){muted=!muted;if(master)master.gain.value=muted?0:.9;return muted},
    mute(m){muted=m;if(master)master.gain.value=m?0:.9},
    get on(){return !!AC&&!muted}
  };
})();
/* ============ อ่านออกเสียงตามลำดับการส่ง ============ */
const tts=(()=>{
  let on=false,voice=null,busy=false;const q=[];
  const syn=window.speechSynthesis;
  const findVoice=()=>{if(!syn)return;const vs=syn.getVoices();voice=vs.find(v=>/^th/i.test(v.lang))||null};
  if(syn){findVoice();syn.onvoiceschanged=findVoice}
  function next(){
    if(busy||!on||!q.length)return;
    const text=q.shift();busy=true;
    let done=false,fell=false,started=false,guard=0;
    const fin=()=>{if(done)return;done=true;clearTimeout(guard);busy=false;setTimeout(next,120)};
    // สำรอง: เสียงอ่านภาษาไทยผ่านเน็ต (ใช้เมื่อเครื่อง/OBS ไม่มีเสียงไทยในตัว)
    const useNet=()=>{
      if(fell||done)return;fell=true;
      try{
        const a=new Audio('https://translate.google.com/translate_tts?ie=UTF-8&client=tw-ob&tl=th&q='+encodeURIComponent(text));
        a.onended=fin;a.onerror=fin;
        const p=a.play();if(p&&p.catch)p.catch(fin);
      }catch(e){fin()}
    };
    guard=setTimeout(fin,15000);
    if(syn&&voice){
      try{
        const u=new SpeechSynthesisUtterance(text);u.lang='th-TH';u.voice=voice;u.rate=1.04;
        u.onstart=()=>{started=true};u.onend=fin;u.onerror=useNet;syn.speak(u);
        setTimeout(()=>{if(!started&&!done){try{syn.cancel()}catch(e){}useNet()}},2500);
      }catch(e){useNet()}
    }else useNet();
  }
  return{
    set(v){on=v;if(!v){q.length=0;if(syn)syn.cancel()}else next()},
    say(text){if(!on||!text||q.length>=8)return;q.push(text);next()}
  };
})();
const sndBtn=$('snd');let soundOn=params.get('sound')!=='off';
function setSound(on){
  soundOn=on;
  if(on){audio.start();audio.mute(false)}else audio.mute(true);
  tts.set(on);sndBtn.textContent=on?'🔊':'🔇';
}
sndBtn.addEventListener('click',e=>{e.stopPropagation();setSound(!soundOn)});
// เปิดเสียง/อ่านชื่ออัตโนมัติตั้งแต่โหลด (ในไลฟ์ไม่มีใครคลิก) ถ้าเบราว์เซอร์บล็อกจะปลุกเมื่อมีการแตะครั้งแรก
const wake=()=>{if(soundOn)audio.start()};
addEventListener('pointerdown',wake);addEventListener('keydown',wake);
setSound(soundOn);

/* ============ ตั้งค่าบัญชีเจ้าของ TikTok LIVE ============ */
// เปลี่ยนเฉพาะบรรทัดนี้เมื่อต้องการแสดงชื่อบัญชีเจ้าของ LIVE อื่น
// หมายเหตุ: บัญชี LIVE ที่รับ Event จริง ต้องเลือก/เชื่อมต่อใน TikFinity Desktop ด้วย
const TIKTOK_LIVE_USERNAME='namboran_v2';

/* ============ เชื่อมต่อ TikFinity (Desktop Event API) ============ */
const TF_HANDLE='TikFinity @'+TIKTOK_LIVE_USERNAME;
$('dot').title=TF_HANDLE+' · ยังไม่เชื่อมต่อ';
const dot=$('dot'),dbg=$('dbg');
let tfSocket=null,tfTimer=0,tfRetry=1500;
function setDot(ok){
  dot.classList.toggle('ok',ok);
  dot.title=TF_HANDLE+' · '+(ok?'เชื่อมต่อแล้ว':'ยังไม่เชื่อมต่อ');
}
if(params.get('debug')==='1')dbg.style.display='block';
// ?safe=1 แสดงกรอบแนะนำ safe zone ของ TikTok Live (หัวด้านบน / คอมเมนต์ / ปุ่มด้านขวา)
if(params.get('safe')==='1'){
  const sf=$('safe');
  for(const [l,t,w,h,txt] of [[0,0,540,88,'แถบหัว TikTok'],[0,745,468,215,'ช่องคอมเมนต์'],[478,560,62,400,'ปุ่ม']]){
    const i=document.createElement('i');i.style.cssText='left:'+l+'px;top:'+t+'px;width:'+w+'px;height:'+h+'px';i.textContent=txt;sf.appendChild(i)}
}
function dbgLog(t){
  if(dbg.style.display!=='block')return;
  const stamp=new Date().toLocaleTimeString('th-TH');
  dbg.textContent='['+stamp+'] '+String(t).slice(0,700)+'\n'+dbg.textContent.slice(0,1800);
}
const streak=new Map();
function handleTF(m){
  if(!m||typeof m!=='object')return;
  const ev=String(m.event||m.type||'').toLowerCase();
  const d=(m.data&&typeof m.data==='object')?m.data:m;
  dbgLog('EVENT '+ev+' '+JSON.stringify(m));
  const u=(d.user&&typeof d.user==='object')?d.user:{};
  const user=d.nickname||d.uniqueId||u.nickname||u.uniqueId||d.username||'ผู้มาเยือน';
  const uid=String(d.userId||d.uniqueId||u.userId||u.uniqueId||user);
  if(ev==='chat'||ev==='comment'){
    const txt=String(d.comment||d.msg||d.text||d.message||'').normalize('NFKC').replace(/\s+/g,'');
    const ck=chatKind(txt);if(ck)villageComment(user,uid,ck);
    return;
  }
  if(ev!=='gift')return;
  const gift=(d.gift&&typeof d.gift==='object')?d.gift:{};
  const gname=d.giftName||d.gift_name||gift.name||gift.giftName||d.name||'';
  const pic=d.giftPictureUrl||d.giftImage||d.gift_image||gift.giftPictureUrl||gift.image||'';
  const total=clamp(parseInt(d.repeatCount||d.comboCount||d.repeat_count||1,10)||1,1,99);
  let n=total;
  const giftType=Number(d.giftType??d.gift_type??0);
  if(giftType===1){
    const key=uid+'|'+gname,now=Date.now(),sv=streak.get(key);
    const prev=(sv&&now-sv.t<20000)?sv.c:0;
    n=Math.max(0,total-prev);
    const ended=d.repeatEnd===true||d.repeatEnd===1||d.repeatEnd==='true'||d.repeat_end===true;
    if(ended)streak.delete(key);else streak.set(key,{c:Math.max(prev,total),t:now});
    if(streak.size>300)for(const [k,v] of streak)if(now-v.t>30000)streak.delete(k);
  }
  n=Math.min(n,3);
  if(!n)return;
  let hit=false;
  for(let i=0;i<n;i++)hit=villageGift(gname,user,pic,uid)||hit;
  if(!hit){
    console.log('[village] Unmapped TikFinity gift:',gname,d);
    dbgLog('UNMATCHED GIFT: '+gname+' | '+pic);
  }
}
function scheduleTFReconnect(){
  if(tfTimer)return;
  tfTimer=setTimeout(()=>{tfTimer=0;connectTF()},tfRetry);
  tfRetry=Math.min(Math.round(tfRetry*1.5),8000);
}
function connectTF(){
  if(tfSocket&&(tfSocket.readyState===WebSocket.CONNECTING||tfSocket.readyState===WebSocket.OPEN))return;
  // ใช้ hostname ตามตัวอย่าง TikFinity Desktop Event API
  const url=params.get('ws')||'ws://localhost:21213/';
  let ws;
  try{ws=new WebSocket(url);tfSocket=ws;}
  catch(err){setDot(false);dbgLog('WebSocket create error: '+err);scheduleTFReconnect();return;}
  dbgLog('กำลังเชื่อมต่อ '+url);
  ws.onopen=()=>{
    if(tfSocket!==ws)return;
    tfRetry=1500;setDot(true);dbgLog('CONNECTED '+url);
  };
  ws.onmessage=event=>{
    let parsedData;
    try{parsedData=JSON.parse(event.data)}
    catch(err){dbgLog('JSON parse error: '+String(event.data).slice(0,200));return;}
    console.log('TikFinity event received',parsedData);
    handleTF(parsedData);
  };
  ws.onerror=err=>{
    dbgLog('WebSocket error (ตรวจสอบว่า TikFinity เปิด Desktop Event API และพอร์ต 21213)');
    // ปล่อยให้ onclose เป็นผู้ตั้งเวลาลองเชื่อมต่อใหม่ เพื่อไม่ให้เกิด timer ซ้ำ
    try{ws.close()}catch(e){}
  };
  ws.onclose=event=>{
    if(tfSocket===ws)tfSocket=null;
    setDot(false);dbgLog('DISCONNECTED code='+event.code+' reason='+(event.reason||'-'));
    scheduleTFReconnect();
  };
}
/* ============ ฉากหลัก ============ */
const decor=[
  {y:175,fn:drawWishTree,a:null},
  {y:885,fn:drawGate,a:{x:MAINX,y:885}},
  {y:915,fn:drawHouse,a:{x:62,y:922}},{y:915,fn:drawHouse,a:{x:478,y:922}}
];
[[26,300,1,'r'],[28,452,1.05,'r'],[512,452,1.1,'r'],[514,610,1,'r'],[512,748,.95,'r'],[505,330,.9,'r']].forEach(([x,y,s,k])=>decor.push({y,fn:smallTree,a:{x,y,s,k}}));
[[40,764,1.1],[528,765,1.1]].forEach(([x,y,s])=>decor.push({y,fn:smallTree,a:{x,y,s,k:'willow'}}));
const lamps=[];
for(const y of [300,470,640,700])for(const x of [236,304]){if(y===700&&x===304)continue;lamps.push({x,y})}
lamps.push({x:236,y:760},{x:304,y:760},{x:236,y:858},{x:304,y:858});
lamps.forEach(a=>decor.push({y:a.y,fn:drawLamp,a}));

function render(){
  C=ctx;ctx.setTransform(R,0,0,R,0,0);
  ctx.imageSmoothingEnabled=true;ctx.imageSmoothingQuality='high';
ctx.textRendering='geometricPrecision';
  ctx.drawImage(layerA,0,0,W,H);
  const cam=()=>ctx.setTransform(R*CAM.s,0,0,R*CAM.s,R*CAM.ox,R*CAM.oy),flat=()=>ctx.setTransform(R,0,0,R,0,0);
  cam();drawWater();flat();
  ctx.drawImage(layerB,0,0,W,H);
  cam();
  const objs=[];
  for(const d of decor)objs.push([d.y,d.fn,d.a]);
  for(const k in SH){const s=SH[k];objs.push([s.y+40,drawShrine,s])}
  for(const f of flowers)objs.push([f.y,drawFlower,f]);
  for(const w of walkers)objs.push([w.y,drawWalker,w]);
  objs.sort((a,b)=>a[0]-b[0]);
  for(const o of objs)o[1](o[2]);
  for(const a of lamps)lampGlow(a);gateGlow({x:MAINX,y:885});
  drawArcs();drawFX();drawBirds();
  flat();ctx.drawImage(layerC,0,0,W,H);
}
function update(dt){
  updateWater(dt);updateFX(dt);
  spawnT-=dt;
  if(spawnQ.length&&spawnT<=0){const s=spawnQ.shift();const ex=walkers.find(w=>w.key===s.key&&!w.dead&&w.y<ENT_Y+18);if(ex)sendWalker(ex,s.g);else walkers.push(makeWalker(s.name,s.g,s.key));spawnT=.45;
    const named=walkers.filter(w=>w.name);if(named.length>36){const o=named[0];if(o.steps.length>1)o.steps=[o.steps[o.steps.length-1]];else o.dead=true}}
  // เว้นระยะไม่ให้ตัวละครเดินทับกัน
  for(let i=0;i<walkers.length;i++){const a=walkers[i];if(a.alpha<.3)continue;
    for(let j=i+1;j<walkers.length;j++){const b=walkers[j];if(b.alpha<.3)continue;
      let dx=b.x-a.x,dy=b.y-a.y;const d=Math.hypot(dx,dy);
      if(d<12){if(d<.01){dx=rnd(-1,1);dy=rnd(-1,1)}const m=Math.hypot(dx,dy)||1,q=(12-d)*Math.min(1,dt*4)*.5;
        a.x-=dx/m*q;a.y-=dy/m*q*.5;b.x+=dx/m*q;b.y+=dy/m*q*.5}}}
  for(const w of walkers)w.update(dt);
  for(let i=walkers.length-1;i>=0;i--)if(walkers[i].dead)walkers.splice(i,1);
}
let spawnT=0,last=0,demoT=2;
const DEMO_NAMES=['มะลิ','น้องฟ้า','พี่โอ๊ต','ฝนพรำ','ใบเตย','นัท','Pimmy','แพรว','เจ้านาย','ลุงตู่ใจดี','momo','จันทร์เจ้า','Tanwa','ข้าวหอม','ลูกน้ำ','ส้มฉุน'];
const demo=params.get('demo')==='1';
function frame(now){
  requestAnimationFrame(frame);
  const dt=Math.min(.05,(now-last)/1000||0);last=now;T+=dt;
  if(demo){demoT-=dt;if(demoT<=0){villageGift(pick(Object.keys(GIFTS)),pick(DEMO_NAMES));demoT=rnd(2.2,4.6)}}
  update(dt);render();
}
function fit(){
  const s=Math.min(innerWidth/W,innerHeight/H);
  stage.style.transform='translate(-50%,-50%) scale('+s+')';
  // เก็บพิกเซลสำรองไว้ 3 เท่าบน PC / 2 เท่าบนมือถือ เพื่อให้ภาพคมขึ้นเมื่อแสดงผลแนวตั้ง
  // ความละเอียดอัตโนมัติ: พอดีกับขนาดจอจริง (OBS 1080x1920 = 2x) ไม่เปลืองเครื่องจนกระตุก
  const r=forcedQuality||clamp(Math.ceil(Math.min(innerWidth/W,innerHeight/H)*(window.devicePixelRatio||1)*2)/2,1,3);
  if(r!==R||!layerA){
    R=r;cv.width=Math.round(W*R);cv.height=Math.round(H*R);
    ctx.imageSmoothingEnabled=true;ctx.imageSmoothingQuality='high';
ctx.textRendering='geometricPrecision';
    buildStatic();
  }
}
addEventListener('resize',fit);
buildPanel();fit();
for(let i=0;i<6;i++)spawnAmbient();
// ปุ่มทดสอบ (เปิดด้วย ?dev=1 หรือกดตัว D)
let devManual=false;
const dev=$('dev');
for(const k in GIFTS){const b=document.createElement('button');b.textContent=GIFTS[k].ico;b.title=GIFTS[k].th;b.onclick=()=>villageGift(k,pick(DEMO_NAMES));dev.appendChild(b)}
dev.style.display=params.get('dev')==='1'?'flex':'none'; // ปุ่มทดสอบ: เปิดด้วย ?dev=1 หรือกดตัว D
for(const [ico,kd] of [['🙏','shrine'],['🕊️','bird'],['🐟','fish'],['🌷','flower']]){const b=document.createElement('button');b.textContent=ico;b.title='คอมเมนต์: '+kd;b.onclick=()=>villageComment(pick(DEMO_NAMES),Math.random(),kd);dev.appendChild(b)}
addEventListener('keydown',e=>{if(e.key==='d'||e.key==='D'){devManual=true;dev.style.display=dev.style.display==='flex'?'none':'flex'}});
const qc=params.get('chat');if(qc)setTimeout(()=>{const k=chatKind(qc);if(k)villageComment(params.get('name')||'ผู้มาเยือน',Math.random(),k)},500);
const qg=params.get('gift');if(qg)setTimeout(()=>villageGift(qg,params.get('name')||'ผู้มาเยือน'),500);
if(params.get('ws')!=='off')connectTF();
requestAnimationFrame(frame);
})();
</script>
</body>
</html>

