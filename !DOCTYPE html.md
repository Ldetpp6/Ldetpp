<!DOCTYPE html>  
  
<html lang="fr" data-theme="dark" data-accent="red">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
<meta name="apple-mobile-web-app-capable" content="yes">  
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">  
<meta name="theme-color" content="#0a0a0f">  
<title>LdetppStream</title>  
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">  
<style>  
/* ===== THEMES & ACCENTS ===== */  
:root {  
  --safe-top: env(safe-area-inset-top,0px);  
  --safe-bottom: env(safe-area-inset-bottom,0px);  
}  
[data-theme="dark"] {  
  --bg:#0a0a0f; --surface:#12121a; --surface2:#1a1a26; --surface3:#22223a;  
  --border:rgba(255,255,255,0.07); --text:#fff; --text2:rgba(255,255,255,0.6);  
  --text3:rgba(255,255,255,0.3); --nav:rgba(10,10,15,0.97); --input:#1a1a26;  
  --card:#14141e; --overlay:rgba(0,0,0,0.75);  
}  
[data-theme="light"] {  
  --bg:#f2f3f8; --surface:#fff; --surface2:#f0f1f7; --surface3:#e5e7f0;  
  --border:rgba(0,0,0,0.08); --text:#0a0a0f; --text2:rgba(10,10,15,0.6);  
  --text3:rgba(10,10,15,0.35); --nav:rgba(242,243,248,0.97); --input:#f0f1f7;  
  --card:#fff; --overlay:rgba(0,0,0,0.55);  
}  
[data-accent="red"]    {--ac:#e50914;--acg:rgba(229,9,20,0.2);}  
[data-accent="blue"]   {--ac:#0084ff;--acg:rgba(0,132,255,0.2);}  
[data-accent="green"]  {--ac:#00c853;--acg:rgba(0,200,83,0.2);}  
[data-accent="purple"] {--ac:#9c27b0;--acg:rgba(156,39,176,0.2);}  
[data-accent="orange"] {--ac:#ff6d00;--acg:rgba(255,109,0,0.2);}  
[data-accent="gold"]   {--ac:#f5c518;--acg:rgba(245,197,24,0.2);}  
  
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}  
html,body{height:100%;width:100%;background:var(–bg);color:var(–text);font-family:‘Outfit’,sans-serif;overflow:hidden;position:fixed;}  
  
/* ===== SCREENS ===== */  
.screen{position:absolute;inset:0;display:none;flex-direction:column;background:var(–bg);overflow:hidden;}  
.screen.active{display:flex;}  
  
/* ===== SPLASH ===== */  
#splashScreen{align-items:center;justify-content:center;}  
.sp-logo{font-size:40px;font-weight:900;letter-spacing:-2px;animation:fUp .6s both;}  
.sp-logo b{color:var(–ac);}  
.sp-tag{font-size:10px;color:var(–text3);letter-spacing:4px;text-transform:uppercase;margin-top:6px;animation:fUp .6s .15s both;}  
.sp-bar{width:120px;height:2px;background:var(–surface3);border-radius:2px;margin-top:44px;overflow:hidden;animation:fUp .6s .3s both;}  
.sp-fill{height:100%;background:var(–ac);animation:loadBar 2.2s ease forwards;}  
@keyframes loadBar{from{width:0}to{width:100%}}  
@keyframes fUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}  
@keyframes fIn{from{opacity:0}to{opacity:1}}  
@keyframes spin{to{transform:rotate(360deg)}}  
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}  
@keyframes shake{0%,100%{transform:translateX(0)}20%,60%{transform:translateX(-6px)}40%,80%{transform:translateX(6px)}}  
@keyframes slideUp{from{transform:translateY(100%)}to{transform:translateY(0)}}  
@keyframes scaleIn{from{opacity:0;transform:scale(.9)}to{opacity:1;transform:scale(1)}}  
  
/* ===== PIN ===== */  
#pinScreen{align-items:center;justify-content:center;padding:20px 30px;}  
.pin-logo{font-size:26px;font-weight:900;letter-spacing:-1px;margin-bottom:4px;}  
.pin-logo b{color:var(–ac);}  
.pin-user{font-size:14px;color:var(–text2);margin-bottom:28px;}  
.pin-dots{display:flex;gap:14px;margin-bottom:28px;}  
.pin-dot{width:15px;height:15px;border-radius:50%;background:var(–surface3);border:2px solid var(–border);transition:all .2s;}  
.pin-dot.on{background:var(–ac);border-color:var(–ac);}  
.pin-dot.err{background:#ff4444;border-color:#ff4444;animation:shake .4s;}  
.pin-hint{font-size:13px;color:var(–text3);margin-bottom:24px;text-align:center;}  
.pin-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;width:100%;max-width:270px;}  
.pk{aspect-ratio:1;border-radius:16px;background:var(–surface);border:1.5px solid var(–border);display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer;transition:all .15s;}  
.pk:active{transform:scale(.88);background:var(–ac);color:#fff;border-color:var(–ac);}  
.pk-num{font-size:22px;font-weight:700;}  
.pk-abc{font-size:8px;color:var(–text3);letter-spacing:1px;}  
.pin-skip{margin-top:18px;font-size:13px;color:var(–text3);cursor:pointer;text-decoration:underline;}  
.pin-actions{display:flex;gap:20px;margin-top:12px;}  
.pin-alt{font-size:12px;color:var(–text3);cursor:pointer;padding:6px 12px;}  
  
/* ===== SETUP ===== */  
#setupScreen{overflow-y:auto;-webkit-overflow-scrolling:touch;padding:calc(var(–safe-top) + 20px) 20px calc(var(–safe-bottom) + 30px);}  
.setup-logo{font-size:22px;font-weight:900;letter-spacing:-1px;margin-bottom:20px;}  
.setup-logo b{color:var(–ac);}  
.setup-h{font-size:24px;font-weight:800;line-height:1.2;margin-bottom:6px;}  
.setup-h span{color:var(–ac);}  
.setup-sub{font-size:13px;color:var(–text2);margin-bottom:22px;}  
.stabs{display:flex;background:var(–surface);border-radius:12px;padding:4px;margin-bottom:18px;}  
.stab{flex:1;padding:10px 6px;text-align:center;font-size:12px;font-weight:600;border-radius:9px;color:var(–text2);cursor:pointer;transition:all .2s;}  
.stab.on{background:var(–ac);color:#fff;}  
.icard{background:var(–surface);border-radius:14px;padding:16px;margin-bottom:14px;}  
.icard label{display:block;font-size:10px;font-weight:700;color:var(–text3);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;}  
.icard input,.icard textarea{  
width:100%;background:var(–input);border:1.5px solid var(–border);  
border-radius:10px;padding:13px 14px;color:var(–text);  
font-family:‘Outfit’,sans-serif;font-size:14px;outline:none;transition:border-color .2s;  
-webkit-appearance:none;  
}  
.icard input:focus,.icard textarea:focus{border-color:var(–ac);}  
.icard textarea{resize:none;height:100px;}  
.dropz{  
border:2px dashed var(–border);border-radius:14px;  
padding:28px 20px;text-align:center;cursor:pointer;transition:all .2s;margin-bottom:14px;  
}  
.dropz.drag{border-color:var(–ac);background:var(–acg);}  
.dropz-ico{width:50px;height:50px;border-radius:50%;background:var(–surface2);display:flex;align-items:center;justify-content:center;margin:0 auto 10px;}  
.dropz h3{font-size:14px;font-weight:700;margin-bottom:3px;}  
.dropz p{font-size:12px;color:var(–text3);}  
.dropz strong{color:var(–ac);}  
.btn-main{  
width:100%;padding:16px;background:var(–ac);color:#fff;  
border:none;border-radius:14px;font-family:‘Outfit’,sans-serif;  
font-size:15px;font-weight:700;cursor:pointer;margin-top:6px;  
transition:all .2s;letter-spacing:.3px;  
}  
.btn-main:active{transform:scale(.97);filter:brightness(.9);}  
.btn-ghost{  
width:100%;padding:14px;background:var(–surface);color:var(–text2);  
border:1.5px solid var(–border);border-radius:14px;font-family:‘Outfit’,sans-serif;  
font-size:14px;font-weight:600;cursor:pointer;margin-top:8px;transition:all .2s;  
}  
.btn-ghost:active{border-color:var(–ac);color:var(–ac);}  
  
/* ===== HEADER ===== */  
.app-header{  
position:absolute;top:0;left:0;right:0;  
padding:calc(var(–safe-top) + 10px) 16px 14px;  
background:linear-gradient(to bottom,var(–bg) 60%,transparent);  
z-index:50;display:flex;align-items:center;gap:10px;  
}  
.h-logo{font-size:18px;font-weight:900;letter-spacing:-1px;}  
.h-logo b{color:var(–ac);}  
.h-credits{  
display:flex;align-items:center;gap:5px;  
background:var(–surface);border:1.5px solid var(–border);  
border-radius:99px;padding:5px 10px;  
font-size:11px;font-weight:700;color:var(–text2);  
cursor:pointer;transition:all .2s;  
}  
.h-credits:active{border-color:var(–ac);color:var(–ac);}  
.h-credits .cr-val{color:var(–ac);font-size:13px;}  
.h-right{margin-left:auto;display:flex;gap:8px;}  
.ico-btn{  
width:36px;height:36px;border-radius:50%;  
background:var(–surface);border:1px solid var(–border);  
display:flex;align-items:center;justify-content:center;  
cursor:pointer;color:var(–text);transition:all .2s;flex-shrink:0;  
}  
.ico-btn:active{transform:scale(.9);border-color:var(–ac);}  
.notif-dot{position:relative;}  
.notif-dot::after{content:’’;position:absolute;top:6px;right:6px;width:7px;height:7px;border-radius:50%;background:var(–ac);border:2px solid var(–bg);}  
  
/* ===== MAIN SCROLL ===== */  
.main-scroll{  
flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;  
padding-bottom:calc(var(–safe-bottom) + 68px);  
}  
.main-scroll::-webkit-scrollbar{display:none;}  
  
/* ===== TYPE TABS (TV / FILMS / SÉRIES) ===== */  
.type-tabs{  
display:flex;gap:8px;padding:calc(var(–safe-top) + 54px) 16px 0;  
background:transparent;position:absolute;top:0;left:0;right:0;z-index:45;  
justify-content:center;  
}  
.type-tab{  
padding:7px 18px;border-radius:99px;  
background:rgba(0,0,0,0.45);backdrop-filter:blur(8px);  
border:1.5px solid rgba(255,255,255,0.15);  
font-size:13px;font-weight:700;color:rgba(255,255,255,.75);  
cursor:pointer;transition:all .2s;white-space:nowrap;  
}  
.type-tab.on{background:var(–ac);border-color:var(–ac);color:#fff;box-shadow:0 2px 12px var(–acg);}  
  
/* ===== HERO ===== */  
.hero{  
position:relative;height:56vw;min-height:230px;max-height:340px;  
overflow:hidden;margin-bottom:4px;flex-shrink:0;  
}  
.hero-bg{position:absolute;inset:0;background:linear-gradient(135deg,#1a0808,#0d0d1a,#080d1a);}  
.hero-pattern{  
position:absolute;inset:0;opacity:.03;  
background-image:repeating-linear-gradient(45deg,#fff 0,#fff 1px,transparent 0,transparent 50%);  
background-size:28px 28px;  
}  
.hero-img{position:absolute;inset:0;object-fit:cover;width:100%;height:100%;opacity:.35;}  
.hero-grad{  
position:absolute;inset:0;  
background:linear-gradient(to top,var(–bg) 0%,rgba(0,0,0,.2) 60%,transparent 100%);  
}  
.hero-content{position:absolute;bottom:0;left:0;right:0;padding:14px 16px 18px;}  
.hero-badge{  
display:inline-flex;align-items:center;gap:5px;  
background:var(–ac);color:#fff;font-size:9px;font-weight:700;  
padding:3px 8px;border-radius:4px;margin-bottom:8px;text-transform:uppercase;letter-spacing:.8px;  
}  
.live-dot{width:5px;height:5px;border-radius:50%;background:#fff;animation:pulse 1s infinite;}  
.hero-title{font-size:24px;font-weight:900;line-height:1.1;margin-bottom:6px;text-shadow:0 2px 8px rgba(0,0,0,.8);}  
.hero-meta{font-size:11px;color:rgba(255,255,255,.6);display:flex;align-items:center;gap:6px;margin-bottom:12px;flex-wrap:wrap;}  
.hero-dot{width:3px;height:3px;border-radius:50%;background:rgba(255,255,255,.3);}  
.hero-btns{display:flex;gap:8px;}  
.hbtn{display:flex;align-items:center;gap:6px;padding:10px 18px;border-radius:9px;font-family:‘Outfit’,sans-serif;font-size:13px;font-weight:700;border:none;cursor:pointer;transition:all .15s;}  
.hbtn:active{transform:scale(.95);}  
.hbtn-play{background:#fff;color:#000;}  
.hbtn-info{background:rgba(255,255,255,.15);color:#fff;backdrop-filter:blur(4px);}  
  
/* ===== SECTIONS ===== */  
.section{margin-bottom:4px;}  
.sec-hd{display:flex;align-items:center;justify-content:space-between;padding:16px 16px 8px;}  
.sec-title{font-size:15px;font-weight:800;}  
.sec-more{font-size:11px;color:var(–text3);cursor:pointer;}  
.cat-row{display:flex;gap:8px;padding:0 16px 4px;overflow-x:auto;-webkit-overflow-scrolling:touch;}  
.cat-row::-webkit-scrollbar{display:none;}  
.cat-pill{  
flex-shrink:0;padding:7px 14px;border-radius:99px;  
background:var(–surface);border:1.5px solid var(–border);  
font-size:12px;font-weight:600;color:var(–text2);cursor:pointer;transition:all .2s;white-space:nowrap;  
}  
.cat-pill.on{background:var(–ac);border-color:var(–ac);color:#fff;}  
  
/* ===== CHANNEL CARD (horizontal) ===== */  
.ch-row{display:flex;gap:10px;padding:10px 16px;overflow-x:auto;-webkit-overflow-scrolling:touch;}  
.ch-row::-webkit-scrollbar{display:none;}  
.chc{flex-shrink:0;width:108px;cursor:pointer;transition:transform .2s;}  
.chc:active{transform:scale(.93);}  
.chc-thumb{  
width:108px;height:66px;border-radius:10px;  
background:var(–surface2);display:flex;align-items:center;justify-content:center;  
overflow:hidden;border:1.5px solid var(–border);margin-bottom:6px;position:relative;  
}  
.chc-thumb img{width:100%;height:100%;object-fit:contain;padding:8px;}  
.chc-abbr{font-size:13px;font-weight:800;color:var(–text2);}  
.chc-live{position:absolute;top:4px;right:4px;background:var(–ac);color:#fff;font-size:8px;font-weight:700;padding:2px 5px;border-radius:3px;}  
.chc-name{font-size:11px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.chc-grp{font-size:10px;color:var(–text3);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.chc-stars{display:flex;gap:1px;margin-top:2px;}  
.chc-star{font-size:8px;color:var(–text3);}  
.chc-star.on{color:#f5c518;}  
  
/* ===== VOD CARD ===== */  
.vod-row{display:flex;gap:10px;padding:10px 16px;overflow-x:auto;-webkit-overflow-scrolling:touch;}  
.vod-row::-webkit-scrollbar{display:none;}  
.vodc{flex-shrink:0;width:100px;cursor:pointer;transition:transform .2s;}  
.vodc:active{transform:scale(.93);}  
.vodc-poster{  
width:100px;height:148px;border-radius:10px;  
background:linear-gradient(135deg,var(–surface2),var(–surface3));  
display:flex;align-items:center;justify-content:center;  
overflow:hidden;border:1.5px solid var(–border);margin-bottom:6px;position:relative;  
}  
.vodc-poster img{width:100%;height:100%;object-fit:cover;}  
.vodc-abbr{font-size:20px;font-weight:900;color:var(–text3);}  
.vodc-badge{  
position:absolute;top:5px;left:5px;  
background:rgba(0,0,0,.7);backdrop-filter:blur(4px);  
color:#fff;font-size:8px;font-weight:700;  
padding:2px 6px;border-radius:4px;  
}  
.vodc-cr{position:absolute;bottom:5px;right:5px;background:var(–ac);color:#fff;font-size:8px;font-weight:700;padding:2px 5px;border-radius:4px;}  
.vodc-name{font-size:11px;font-weight:700;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.vodc-info{font-size:10px;color:var(–text3);}  
  
/* ===== LIST ITEM ===== */  
.ch-li{  
display:flex;align-items:center;gap:12px;  
padding:10px 16px;cursor:pointer;transition:background .15s;  
}  
.ch-li:active{background:var(–surface);}  
.ch-li-logo{  
width:46px;height:32px;border-radius:8px;  
background:var(–surface2);border:1px solid var(–border);  
display:flex;align-items:center;justify-content:center;  
overflow:hidden;flex-shrink:0;  
}  
.ch-li-logo img{width:100%;height:100%;object-fit:contain;padding:4px;}  
.ch-li-abb{font-size:10px;font-weight:800;color:var(–text2);}  
.ch-li-info{flex:1;min-width:0;}  
.ch-li-name{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.ch-li-epg{font-size:11px;color:var(–text3);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;margin-top:1px;}  
.ch-li-r{display:flex;flex-direction:column;align-items:flex-end;gap:3px;flex-shrink:0;}  
.ch-li-num{font-size:10px;color:var(–text3);font-weight:600;}  
.fav-btn{font-size:15px;color:var(–text3);cursor:pointer;}  
.fav-btn.on{color:#f5c518;}  
.ch-li-stars{display:flex;gap:1px;}  
.li-star{font-size:9px;color:var(–text3);}  
.li-star.on{color:#f5c518;}  
  
/* ===== BOTTOM NAV ===== */  
.bnav{  
position:absolute;bottom:0;left:0;right:0;  
height:calc(58px + var(–safe-bottom));  
background:var(–nav);backdrop-filter:blur(20px);  
border-top:1px solid var(–border);  
display:flex;align-items:flex-start;padding-top:6px;z-index:50;  
}  
.bni{  
flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;  
padding:5px 4px;cursor:pointer;color:var(–text3);  
transition:color .2s;font-size:9px;font-weight:600;  
}  
.bni.on{color:var(–ac);}  
.bni svg{flex-shrink:0;}  
  
/* ===== PAGES ===== */  
.page{display:none;flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;flex-direction:column;padding-top:calc(var(–safe-top) + 56px);padding-bottom:calc(var(–safe-bottom) + 68px);}  
.page::-webkit-scrollbar{display:none;}  
.page.show{display:flex;}  
.page-title{font-size:20px;font-weight:800;padding:16px 16px 12px;}  
  
/* ===== SEARCH OVERLAY ===== */  
#searchOv{position:absolute;inset:0;background:var(–bg);z-index:200;display:none;flex-direction:column;padding:calc(var(–safe-top) + 12px) 16px 20px;}  
#searchOv.open{display:flex;}  
.srch-top{display:flex;align-items:center;gap:10px;margin-bottom:14px;}  
.srch-box{flex:1;display:flex;align-items:center;gap:8px;background:var(–surface);border-radius:12px;padding:12px 14px;border:1.5px solid var(–border);}  
.srch-box:focus-within{border-color:var(–ac);}  
.srch-box input{flex:1;background:none;border:none;outline:none;color:var(–text);font-family:‘Outfit’,sans-serif;font-size:15px;}  
.srch-box input::placeholder{color:var(–text3);}  
.srch-cancel{font-size:14px;font-weight:600;color:var(–ac);cursor:pointer;white-space:nowrap;}  
.srch-res{flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;}  
.srch-res::-webkit-scrollbar{display:none;}  
.srch-empty{display:flex;flex-direction:column;align-items:center;justify-content:center;height:180px;gap:8px;color:var(–text3);font-size:14px;text-align:center;}  
.srch-section{font-size:11px;font-weight:700;color:var(–text3);text-transform:uppercase;letter-spacing:1px;padding:12px 16px 6px;}  
  
/* ===== PLAYER SCREEN ===== */  
#playerScreen{position:absolute;inset:0;background:#000;z-index:300;display:none;flex-direction:column;}  
#playerScreen.open{display:flex;}  
.pv-wrap{position:relative;width:100%;background:#000;flex-shrink:0;}  
.pv-wrap video{width:100%;display:block;aspect-ratio:16/9;object-fit:contain;}  
.pv-overlay{  
position:absolute;inset:0;  
background:linear-gradient(to bottom,rgba(0,0,0,.65) 0%,transparent 30%,transparent 68%,rgba(0,0,0,.75) 100%);  
opacity:0;transition:opacity .3s;  
}  
.pv-overlay.vis{opacity:1;}  
.pv-top{display:flex;align-items:center;padding:calc(var(–safe-top) + 10px) 14px 10px;gap:10px;}  
.pv-back{width:36px;height:36px;border-radius:50%;background:rgba(0,0,0,.4);backdrop-filter:blur(4px);display:flex;align-items:center;justify-content:center;cursor:pointer;border:none;color:#fff;flex-shrink:0;}  
.pv-title-wrap{flex:1;min-width:0;}  
.pv-title{font-size:14px;font-weight:700;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.pv-sub{font-size:11px;color:rgba(255,255,255,.55);margin-top:1px;}  
.pv-top-btns{display:flex;gap:8px;}  
.pv-ico{width:34px;height:34px;border-radius:50%;background:rgba(0,0,0,.4);backdrop-filter:blur(4px);display:flex;align-items:center;justify-content:center;cursor:pointer;border:none;color:#fff;font-size:15px;}  
.pv-center{display:flex;align-items:center;justify-content:center;gap:32px;}  
.pv-ctrl{width:44px;height:44px;border-radius:50%;background:rgba(0,0,0,.35);backdrop-filter:blur(4px);display:flex;align-items:center;justify-content:center;cursor:pointer;border:none;color:#fff;transition:transform .15s;}  
.pv-ctrl:active{transform:scale(.88);}  
.pv-play{width:58px;height:58px;border-radius:50%;background:#fff;display:flex;align-items:center;justify-content:center;cursor:pointer;border:none;color:#000;box-shadow:0 4px 20px rgba(0,0,0,.5);transition:transform .15s;}  
.pv-play:active{transform:scale(.9);}  
.pv-bot{padding:10px 14px calc(var(–safe-bottom) + 12px);}  
.pv-vol-row{display:flex;align-items:center;gap:10px;margin-top:10px;}  
.pv-vol{flex:1;-webkit-appearance:none;height:3px;border-radius:2px;background:rgba(255,255,255,.2);outline:none;cursor:pointer;}  
.pv-vol::-webkit-slider-thumb{-webkit-appearance:none;width:16px;height:16px;border-radius:50%;background:#fff;cursor:pointer;}  
.pv-timer-display{font-size:11px;color:rgba(255,255,255,.5);text-align:center;margin-top:6px;}  
.pv-load{position:absolute;inset:0;background:rgba(0,0,0,.7);display:flex;align-items:center;justify-content:center;backdrop-filter:blur(4px);}  
.spinner{width:44px;height:44px;border:3px solid rgba(255,255,255,.15);border-top-color:var(–ac);border-radius:50%;animation:spin .8s linear infinite;}  
  
/* Player info panel */  
.pv-info{flex:1;background:var(–surface);overflow-y:auto;-webkit-overflow-scrolling:touch;}  
.pv-info::-webkit-scrollbar{display:none;}  
.pv-tabs{display:flex;border-bottom:1px solid var(–border);padding:0 16px;background:var(–surface);flex-shrink:0;}  
.pv-tab{padding:12px 14px;font-size:12px;font-weight:700;color:var(–text3);cursor:pointer;border-bottom:2px solid transparent;transition:all .2s;white-space:nowrap;}  
.pv-tab.on{color:var(–text);border-bottom-color:var(–ac);}  
.epg-sec{padding:14px 16px 8px;border-bottom:1px solid var(–border);}  
.epg-now{display:flex;align-items:flex-start;gap:10px;margin-bottom:10px;}  
.epg-badge{background:var(–ac);color:#fff;font-size:9px;font-weight:700;padding:3px 7px;border-radius:4px;text-transform:uppercase;flex-shrink:0;margin-top:2px;}  
.epg-next-badge{background:var(–surface2);color:var(–text2);font-size:9px;font-weight:700;padding:3px 7px;border-radius:4px;flex-shrink:0;margin-top:2px;}  
.epg-pt{font-size:14px;font-weight:700;margin-bottom:3px;}  
.epg-tm{font-size:11px;color:var(–text3);}  
.epg-prog{height:3px;background:var(–surface2);border-radius:2px;overflow:hidden;margin:8px 0 2px;}  
.epg-prog-fill{height:100%;background:var(–ac);border-radius:2px;}  
.epg-li{display:flex;gap:10px;padding:10px 0;border-bottom:1px solid var(–border);}  
.epg-time{font-size:11px;color:var(–text3);font-weight:600;width:40px;flex-shrink:0;padding-top:1px;}  
.epg-ii{flex:1;}  
.epg-title{font-size:13px;font-weight:600;margin-bottom:2px;}  
.epg-desc{font-size:11px;color:var(–text3);line-height:1.4;}  
.sec-label{font-size:11px;font-weight:700;color:var(–text3);text-transform:uppercase;letter-spacing:1px;padding:14px 16px 8px;}  
  
/* Stars Rating */  
.star-rate{display:flex;gap:4px;align-items:center;padding:12px 16px;border-bottom:1px solid var(–border);}  
.star-rate-lbl{font-size:12px;color:var(–text2);margin-right:6px;font-weight:600;}  
.sr-star{font-size:22px;color:var(–text3);cursor:pointer;transition:all .15s;}  
.sr-star:active{transform:scale(.85);}  
.sr-star.on{color:#f5c518;}  
  
/* History in player */  
.hist-li{display:flex;align-items:center;gap:12px;padding:10px 16px;border-bottom:1px solid var(–border);}  
.hist-thumb{width:56px;height:34px;border-radius:7px;background:var(–surface2);border:1px solid var(–border);display:flex;align-items:center;justify-content:center;overflow:hidden;flex-shrink:0;}  
.hist-thumb img{width:100%;height:100%;object-fit:contain;padding:4px;}  
.hist-abb{font-size:9px;font-weight:800;color:var(–text3);}  
.hist-info{flex:1;min-width:0;}  
.hist-name{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}  
.hist-time{font-size:11px;color:var(–text3);margin-top:2px;}  
  
/* ===== CREDITS MODAL ===== */  
#creditsModal{position:absolute;inset:0;background:var(–overlay);z-index:500;display:none;align-items:flex-end;}  
#creditsModal.open{display:flex;}  
.cr-sheet{  
width:100%;background:var(–surface);border-radius:20px 20px 0 0;  
padding:16px 20px calc(var(–safe-bottom) + 24px);  
animation:slideUp .3s ease;max-height:90vh;overflow-y:auto;  
}  
.cr-sheet::-webkit-scrollbar{display:none;}  
.sh-handle{width:36px;height:4px;border-radius:2px;background:var(–surface3);margin:0 auto 20px;}  
.cr-title{font-size:18px;font-weight:800;margin-bottom:4px;}  
.cr-sub{font-size:13px;color:var(–text3);margin-bottom:20px;}  
.cr-balance{  
background:linear-gradient(135deg,var(–ac),color-mix(in srgb,var(–ac) 60%,#000));  
border-radius:14px;padding:20px;margin-bottom:18px;  
display:flex;align-items:center;justify-content:space-between;  
}  
.cr-bal-lbl{font-size:12px;font-weight:600;color:rgba(255,255,255,.7);}  
.cr-bal-val{font-size:32px;font-weight:900;color:#fff;margin-top:2px;}  
.cr-bal-sub{font-size:11px;color:rgba(255,255,255,.55);margin-top:2px;}  
.cr-bal-ico{font-size:36px;opacity:.4;}  
.cr-plans{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-bottom:18px;}  
.cr-plan{  
background:var(–surface2);border:1.5px solid var(–border);  
border-radius:12px;padding:14px 12px;cursor:pointer;transition:all .2s;text-align:center;  
}  
.cr-plan:active{border-color:var(–ac);background:var(–acg);}  
.cr-plan.best{border-color:var(–ac);}  
.cr-plan-badge{font-size:9px;font-weight:700;background:var(–ac);color:#fff;padding:2px 6px;border-radius:4px;display:inline-block;margin-bottom:6px;}  
.cr-plan-credits{font-size:20px;font-weight:900;}  
.cr-plan-price{font-size:11px;color:var(–text3);margin-top:2px;}  
.cr-history{background:var(–surface2);border-radius:12px;overflow:hidden;}  
.cr-hi{display:flex;align-items:center;gap:10px;padding:12px 14px;border-bottom:1px solid var(–border);}  
.cr-hi:last-child{border-bottom:none;}  
.cr-hi-ico{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;}  
.cr-hi-plus{background:rgba(0,200,83,.15);color:#00c853;}  
.cr-hi-minus{background:rgba(229,9,20,.15);color:#e50914;}  
.cr-hi-info{flex:1;min-width:0;}  
.cr-hi-name{font-size:13px;font-weight:600;}  
.cr-hi-date{font-size:10px;color:var(–text3);}  
.cr-hi-amount{font-size:13px;font-weight:700;}  
  
/* ===== NOTIFS PANEL ===== */  
#notifsPanel{position:absolute;inset:0;background:var(–bg);z-index:400;display:none;flex-direction:column;padding-top:calc(var(–safe-top) + 10px);}  
#notifsPanel.open{display:flex;}  
.np-head{display:flex;align-items:center;gap:12px;padding:12px 16px 16px;}  
.np-head h2{font-size:18px;font-weight:800;flex:1;}  
.np-close{width:34px;height:34px;border-radius:50%;background:var(–surface);border:1px solid var(–border);display:flex;align-items:center;justify-content:center;cursor:pointer;color:var(–text);}  
.np-list{flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch;}  
.np-list::-webkit-scrollbar{display:none;}  
.np-item{display:flex;gap:12px;padding:14px 16px;border-bottom:1px solid var(–border);}  
.np-item.unread{background:var(–acg);}  
.np-ico{width:38px;height:38px;border-radius:50%;background:var(–surface2);display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0;}  
.np-info{flex:1;min-width:0;}  
.np-title{font-size:13px;font-weight:700;margin-bottom:3px;}  
.np-desc{font-size:12px;color:var(–text2);line-height:1.4;}  
.np-time{font-size:10px;color:var(–text3);margin-top:4px;}  
  
/* ===== SETTINGS PAGE ===== */  
.settings-section{padding:16px 16px 8px;}  
.settings-section-title{font-size:11px;font-weight:700;color:var(–text3);text-transform:uppercase;letter-spacing:1px;margin-bottom:10px;}  
.settings-card{background:var(–surface);border-radius:14px;overflow:hidden;margin-bottom:16px;}  
.setting-row{  
display:flex;align-items:center;gap:12px;  
padding:14px 16px;border-bottom:1px solid var(–border);cursor:pointer;  
}  
.setting-row:last-child{border-bottom:none;}  
.setting-row:active{background:var(–surface2);}  
.setting-ico{width:32px;height:32px;border-radius:8px;background:var(–acg);display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:15px;}  
.setting-info{flex:1;min-width:0;}  
.setting-name{font-size:14px;font-weight:600;}  
.setting-val{font-size:11px;color:var(–text3);margin-top:1px;}  
.setting-right{color:var(–text3);}  
/* Toggle */  
.toggle{width:44px;height:26px;border-radius:13px;background:var(–surface3);position:relative;cursor:pointer;transition:background .2s;flex-shrink:0;}  
.toggle.on{background:var(–ac);}  
.toggle::after{content:’’;position:absolute;top:3px;left:3px;width:20px;height:20px;border-radius:50%;background:#fff;transition:transform .2s;box-shadow:0 1px 4px rgba(0,0,0,.3);}  
.toggle.on::after{transform:translateX(18px);}  
  
/* Accent color picker */  
.accent-row{display:flex;gap:10px;padding:14px 16px;flex-wrap:wrap;}  
.accent-opt{width:32px;height:32px;border-radius:50%;cursor:pointer;border:3px solid transparent;transition:all .2s;position:relative;}  
.accent-opt.on{border-color:var(–text);transform:scale(1.15);}  
  
/* Playlist manager */  
.pl-item{  
display:flex;align-items:center;gap:12px;  
padding:14px 16px;border-bottom:1px solid var(–border);  
}  
.pl-item:last-child{border-bottom:none;}  
.pl-ico{width:36px;height:36px;border-radius:8px;background:var(–acg);display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0;}  
.pl-info{flex:1;min-width:0;}  
.pl-name{font-size:14px;font-weight:600;}  
.pl-count{font-size:11px;color:var(–text3);margin-top:1px;}  
.pl-btns{display:flex;gap:6px;}  
.pl-btn{padding:5px 10px;border-radius:6px;font-size:11px;font-weight:600;border:1.5px solid var(–border);background:none;color:var(–text2);cursor:pointer;}  
.pl-btn.del{border-color:rgba(229,9,20,.3);color:#e50914;}  
.pl-btn.act{border-color:var(–ac);color:var(–ac);}  
  
/* Profile */  
.profile-card{  
display:flex;align-items:center;gap:14px;  
background:var(–surface);border-radius:14px;padding:16px;margin-bottom:16px;  
}  
.profile-av{  
width:52px;height:52px;border-radius:50%;  
background:linear-gradient(135deg,var(–ac),color-mix(in srgb,var(–ac) 50%,#000));  
display:flex;align-items:center;justify-content:center;  
font-size:22px;font-weight:800;color:#fff;flex-shrink:0;  
}  
.profile-info{flex:1;}  
.profile-name{font-size:16px;font-weight:800;}  
.profile-plan{font-size:11px;color:var(–ac);font-weight:600;margin-top:2px;}  
  
/* Lang selector */  
.lang-opts{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;padding:14px 16px;}  
.lang-opt{  
padding:10px;border-radius:10px;border:1.5px solid var(–border);  
text-align:center;cursor:pointer;transition:all .2s;  
}  
.lang-opt.on{border-color:var(–ac);background:var(–acg);}  
.lang-opt-flag{font-size:20px;display:block;margin-bottom:4px;}  
.lang-opt-name{font-size:11px;font-weight:600;color:var(–text2);}  
.lang-opt.on .lang-opt-name{color:var(–ac);}  
  
/* Timer modal */  
#timerModal{position:absolute;inset:0;background:var(–overlay);z-index:600;display:none;align-items:center;justify-content:center;padding:20px;}  
#timerModal.open{display:flex;}  
.timer-card{background:var(–surface);border-radius:20px;padding:24px;width:100%;max-width:320px;animation:scaleIn .25s ease;}  
.timer-title{font-size:16px;font-weight:800;margin-bottom:16px;text-align:center;}  
.timer-opts{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:16px;}  
.t-opt{padding:12px 6px;border-radius:10px;border:1.5px solid var(–border);text-align:center;cursor:pointer;transition:all .2s;font-size:13px;font-weight:700;}  
.t-opt:active{border-color:var(–ac);background:var(–acg);}  
.t-opt.on{border-color:var(–ac);background:var(–acg);color:var(–ac);}  
  
/* ===== TOAST ===== */  
.toast{  
position:fixed;bottom:calc(var(–safe-bottom) + 80px);  
left:50%;transform:translateX(-50%) translateY(20px);  
background:rgba(20,20,30,.95);border:1px solid var(–border);  
border-radius:10px;padding:10px 18px;font-size:13px;font-weight:500;  
white-space:nowrap;z-index:9999;opacity:0;transition:all .3s;  
pointer-events:none;backdrop-filter:blur(10px);  
}  
.toast.show{opacity:1;transform:translateX(-50%) translateY(0);}  
.toast.ok{border-color:rgba(0,200,83,.4);color:#00c853;}  
.toast.err{border-color:rgba(229,9,20,.4);color:#ff6b6b;}  
.toast.info{border-color:rgba(0,132,255,.4);color:#69b4ff;}  
  
/* ===== EMPTY STATE ===== */  
.empty-big{display:flex;flex-direction:column;align-items:center;justify-content:center;padding:50px 30px;gap:10px;text-align:center;}  
.empty-big h3{font-size:17px;font-weight:700;margin-top:6px;}  
.empty-big p{font-size:13px;color:var(–text3);line-height:1.5;}  
.empty-big .btn-main{width:auto;padding:12px 24px;margin-top:8px;}  
  
/* ===== DIVIDER ===== */  
.divider{height:1px;background:var(–border);margin:0 16px;}  
  
/* ===== SCROLL RESTORE ===== */  
#mainScreen .main-scroll{padding-top:100px;}  
</style>  
  
</head>  
<body>  
  
<!-- SPLASH -->  
  
<div class="screen active" id="splashScreen">  
  <div class="sp-logo"><b>L</b>detpp<b>Stream</b></div>  
  <div class="sp-tag">IPTV Premium</div>  
  <div class="sp-bar"><div class="sp-fill"></div></div>  
</div>  
  
<!-- PIN -->  
  
<div class="screen" id="pinScreen">  
  <div class="pin-logo"><b>L</b>detppStream</div>  
  <div class="pin-user" id="pinUser">Entrez votre code PIN</div>  
  <div class="pin-dots">  
    <div class="pin-dot" id="pd0"></div>  
    <div class="pin-dot" id="pd1"></div>  
    <div class="pin-dot" id="pd2"></div>  
    <div class="pin-dot" id="pd3"></div>  
  </div>  
  <div class="pin-hint" id="pinHint">Code PIN requis</div>  
  <div class="pin-grid">  
    <div class="pk" onclick="pinKey('1')"><span class="pk-num">1</span></div>  
    <div class="pk" onclick="pinKey('2')"><span class="pk-num">2</span><span class="pk-abc">ABC</span></div>  
    <div class="pk" onclick="pinKey('3')"><span class="pk-num">3</span><span class="pk-abc">DEF</span></div>  
    <div class="pk" onclick="pinKey('4')"><span class="pk-num">4</span><span class="pk-abc">GHI</span></div>  
    <div class="pk" onclick="pinKey('5')"><span class="pk-num">5</span><span class="pk-abc">JKL</span></div>  
    <div class="pk" onclick="pinKey('6')"><span class="pk-num">6</span><span class="pk-abc">MNO</span></div>  
    <div class="pk" onclick="pinKey('7')"><span class="pk-num">7</span><span class="pk-abc">PQRS</span></div>  
    <div class="pk" onclick="pinKey('8')"><span class="pk-num">8</span><span class="pk-abc">TUV</span></div>  
    <div class="pk" onclick="pinKey('9')"><span class="pk-num">9</span><span class="pk-abc">WXYZ</span></div>  
    <div class="pk" onclick="pinKey('bio')" style="font-size:20px;">👁</div>  
    <div class="pk" onclick="pinKey('0')"><span class="pk-num">0</span></div>  
    <div class="pk" onclick="pinKey('del')" style="font-size:18px;">⌫</div>  
  </div>  
  <div class="pin-skip" onclick="skipPin()">Continuer sans PIN</div>  
</div>  
  
<!-- SETUP -->  
  
<div class="screen" id="setupScreen">  
  <div class="setup-logo"><b>L</b>detppStream</div>  
  <div class="setup-h">Ajoutez votre<br><span>Playlist M3U</span></div>  
  <div class="setup-sub">Connectez vos chaînes, films et séries</div>  
  <div class="stabs">  
    <div class="stab on" id="stab-url" onclick="switchStab('url')">🔗 URL</div>  
    <div class="stab" id="stab-file" onclick="switchStab('file')">📁 Fichier</div>  
    <div class="stab" id="stab-paste" onclick="switchStab('paste')">📋 Coller</div>  
  </div>  
  <div id="stp-url">  
    <div class="icard">  
      <label>Nom de la playlist</label>  
      <input type="text" id="plName" placeholder="Ma Playlist" style="margin-bottom:10px;">  
      <label>URL M3U / M3U8</label>  
      <input type="url" id="plUrl" placeholder="http://exemple.com/playlist.m3u" inputmode="url">  
    </div>  
  </div>  
  <div id="stp-file" style="display:none;">  
    <div class="dropz" id="setupDrop" onclick="document.getElementById('setupFile').click()" ondragover="ev_dragover(event)" ondragleave="ev_dragleave(event)" ondrop="ev_drop(event)">  
      <div class="dropz-ico">  
        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="rgba(255,255,255,.45)" stroke-width="1.5"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>  
      </div>  
      <h3>Appuyez pour choisir</h3>  
      <p>Fichiers <strong>.m3u</strong> ou <strong>.m3u8</strong></p>  
      <input type="file" id="setupFile" accept=".m3u,.m3u8,.txt" style="display:none" onchange="handleSetupFile(this)">  
    </div>  
  </div>  
  <div id="stp-paste" style="display:none;">  
    <div class="icard">  
      <label>Coller le contenu M3U</label>  
      <textarea id="plPaste" placeholder="#EXTM3U&#10;#EXTINF:-1 tvg-name=&quot;Chaîne&quot;,Chaîne 1&#10;http://..."></textarea>  
    </div>  
  </div>  
  <button class="btn-main" onclick="doSetup()">✓ Charger la playlist</button>  
  <button class="btn-ghost" onclick="skipSetup()">Continuer sans playlist</button>  
</div>  
  
<!-- MAIN -->  
  
<div class="screen" id="mainScreen">  
  <!-- Header -->  
  <div class="app-header">  
    <div class="h-logo"><b>L</b>detppStream</div>  
    <div class="h-credits" onclick="openCredits()">  
      <span>💎</span>  
      <span class="cr-val" id="headerCredits">0</span>  
      <span style="color:var(--text3);font-size:10px;">crédits</span>  
    </div>  
    <div class="h-right">  
      <div class="ico-btn notif-dot" id="notifBtn" onclick="openNotifs()">  
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg>  
      </div>  
      <div class="ico-btn" onclick="openSearch()">  
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>  
      </div>  
    </div>  
  </div>  
  
  <!-- Type tabs -->  
  
  <div class="type-tabs" id="typeTabs">  
    <div class="type-tab on" onclick="setType('tv')">📺 Télé</div>  
    <div class="type-tab" onclick="setType('films')">🎬 Films</div>  
    <div class="type-tab" onclick="setType('series')">🎭 Séries</div>  
  </div>  
  
  <!-- Main scroll -->  
  
  <div class="main-scroll" id="mainScroll">  
    <div id="homePage"></div>  
  </div>  
  
  <!-- Bottom nav -->  
  
  <div class="bnav">  
    <div class="bni on" id="nav-home" onclick="setNav('home')">  
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>  
      Accueil  
    </div>  
    <div class="bni" id="nav-favs" onclick="setNav('favs')">  
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>  
      Favoris  
    </div>  
    <div class="bni" id="nav-history" onclick="setNav('history')">  
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>  
      Historique  
    </div>  
    <div class="bni" id="nav-settings" onclick="setNav('settings')">  
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83-2.83l.06-.06A1.65 1.65 0 0 0 4.68 15a1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 2.83-2.83l.06.06A1.65 1.65 0 0 0 9 4.68a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 2.83l-.06.06A1.65 1.65 0 0 0 19.4 9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>  
      Réglages  
    </div>  
  </div>  
  
  <!-- Pages -->  
  
  <div class="page" id="favsPage">  
    <div class="page-title">⭐ Mes Favoris</div>  
    <div id="favsList"></div>  
  </div>  
  <div class="page" id="historyPage">  
    <div class="page-title">🕐 Historique</div>  
    <div id="histList"></div>  
  </div>  
  <div class="page" id="settingsPage">  
    <!-- Profile -->  
    <div class="settings-section">  
      <div class="profile-card">  
        <div class="profile-av" id="profAv">L</div>  
        <div class="profile-info">  
          <div class="profile-name" id="profName">Utilisateur</div>  
          <div class="profile-plan">Plan Premium • 💎 <span id="profCredits">0</span> crédits</div>  
        </div>  
      </div>  
    </div>  
    <!-- Langue -->  
    <div class="settings-section">  
      <div class="settings-section-title" id="lbl-lang">Langue</div>  
      <div class="settings-card">  
        <div class="lang-opts">  
          <div class="lang-opt on" id="lang-fr" onclick="setLang('fr')"><span class="lang-opt-flag">🇫🇷</span><span class="lang-opt-name">Français</span></div>  
          <div class="lang-opt" id="lang-en" onclick="setLang('en')"><span class="lang-opt-flag">🇬🇧</span><span class="lang-opt-name">English</span></div>  
          <div class="lang-opt" id="lang-ar" onclick="setLang('ar')"><span class="lang-opt-flag">🇸🇦</span><span class="lang-opt-name">العربية</span></div>  
        </div>  
      </div>  
    </div>  
    <!-- Thème -->  
    <div class="settings-section">  
      <div class="settings-section-title" id="lbl-theme">Apparence</div>  
      <div class="settings-card">  
        <div class="setting-row" onclick="toggleTheme()">  
          <div class="setting-ico">🌙</div>  
          <div class="setting-info">  
            <div class="setting-name" id="lbl-darkmode">Mode sombre</div>  
            <div class="setting-val" id="val-darkmode">Activé</div>  
          </div>  
          <div class="toggle on" id="themeToggle"></div>  
        </div>  
        <div class="setting-row">  
          <div class="setting-ico">🎨</div>  
          <div class="setting-info"><div class="setting-name" id="lbl-accent">Couleur principale</div></div>  
        </div>  
        <div class="accent-row">  
          <div class="accent-opt on" style="background:#e50914" data-ac="red" onclick="setAccent('red')"></div>  
          <div class="accent-opt" style="background:#0084ff" data-ac="blue" onclick="setAccent('blue')"></div>  
          <div class="accent-opt" style="background:#00c853" data-ac="green" onclick="setAccent('green')"></div>  
          <div class="accent-opt" style="background:#9c27b0" data-ac="purple" onclick="setAccent('purple')"></div>  
          <div class="accent-opt" style="background:#ff6d00" data-ac="orange" onclick="setAccent('orange')"></div>  
          <div class="accent-opt" style="background:#f5c518" data-ac="gold" onclick="setAccent('gold')"></div>  
        </div>  
      </div>  
    </div>  
    <!-- Playlists -->  
    <div class="settings-section">  
      <div class="settings-section-title" id="lbl-playlists">Mes Playlists</div>  
      <div class="settings-card" id="plList"></div>  
      <button class="btn-main" style="margin-top:10px;" onclick="openAddPlaylist()">+ Ajouter une playlist</button>  
    </div>  
    <!-- Sécurité -->  
    <div class="settings-section">  
      <div class="settings-section-title" id="lbl-security">Sécurité</div>  
      <div class="settings-card">  
        <div class="setting-row" onclick="togglePin()">  
          <div class="setting-ico">🔐</div>  
          <div class="setting-info">  
            <div class="setting-name" id="lbl-pin">Code PIN</div>  
            <div class="setting-val" id="val-pin">Désactivé</div>  
          </div>  
          <div class="toggle" id="pinToggle"></div>  
        </div>  
      </div>  
    </div>  
    <!-- Timer -->  
    <div class="settings-section">  
      <div class="settings-section-title">Lecture</div>  
      <div class="settings-card">  
        <div class="setting-row" onclick="openTimerModal()">  
          <div class="setting-ico">⏱</div>  
          <div class="setting-info">  
            <div class="setting-name" id="lbl-timer">Timer d'arrêt</div>  
            <div class="setting-val" id="val-timer">Désactivé</div>  
          </div>  
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="var(--text3)" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>  
        </div>  
        <div class="setting-row" onclick="toggleRandom()">  
          <div class="setting-ico">🔀</div>  
          <div class="setting-info">  
            <div class="setting-name" id="lbl-random">Lecture aléatoire</div>  
            <div class="setting-val" id="val-random">Désactivé</div>  
          </div>  
          <div class="toggle" id="randomToggle"></div>  
        </div>  
        <div class="setting-row" onclick="togglePip()">  
          <div class="setting-ico">📺</div>  
          <div class="setting-info">  
            <div class="setting-name">Picture-in-Picture</div>  
            <div class="setting-val" id="val-pip">Désactivé</div>  
          </div>  
          <div class="toggle" id="pipToggle"></div>  
        </div>  
      </div>  
    </div>  
    <!-- Credits -->  
    <div class="settings-section">  
      <div class="settings-section-title">Crédits</div>  
      <div class="settings-card">  
        <div class="setting-row" onclick="openCredits()">  
          <div class="setting-ico">💎</div>  
          <div class="setting-info">  
            <div class="setting-name" id="lbl-credits">Gérer mes crédits</div>  
            <div class="setting-val"><span id="settCredits">0</span> crédits disponibles</div>  
          </div>  
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="var(--text3)" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>  
        </div>  
      </div>  
    </div>  
    <!-- About -->  
    <div class="settings-section">  
      <div class="settings-card">  
        <div class="setting-row">  
          <div class="setting-ico">ℹ️</div>  
          <div class="setting-info">  
            <div class="setting-name">LdetppStream</div>  
            <div class="setting-val">Version 2.0.0 • Premium</div>  
          </div>  
        </div>  
        <div class="setting-row" onclick="clearAll()" style="color:#e50914;">  
          <div class="setting-ico" style="background:rgba(229,9,20,.15);">🗑</div>  
          <div class="setting-info"><div class="setting-name" style="color:#e50914;" id="lbl-clear">Réinitialiser l'application</div></div>  
        </div>  
      </div>  
    </div>  
    <div style="height:20px;"></div>  
  </div>  
</div>  
  
<!-- SEARCH OVERLAY -->  
  
<div id="searchOv">  
  <div class="srch-top">  
    <div class="srch-box">  
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="var(--text3)" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>  
      <input type="text" id="srchInput" placeholder="Rechercher chaînes, films, séries..." oninput="doSearch(this.value)" autofocus>  
    </div>  
    <div class="srch-cancel" onclick="closeSearch()">Annuler</div>  
  </div>  
  <div class="srch-res" id="srchRes">  
    <div class="srch-empty">  
      <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" opacity=".4"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>  
      <p id="srch-ph">Tapez pour rechercher</p>  
    </div>  
  </div>  
</div>  
  
<!-- PLAYER -->  
  
<div id="playerScreen">  
  <div class="pv-wrap" id="pvWrap">  
    <video id="pv" playsinline webkit-playsinline></video>  
    <div class="pv-overlay" id="pvOv" onclick="toggleOverlay()">  
      <div class="pv-top">  
        <button class="pv-back" onclick="closePlayer()">  
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="15 18 9 12 15 6"/></svg>  
        </button>  
        <div class="pv-title-wrap">  
          <div class="pv-title" id="pvTitle">—</div>  
          <div class="pv-sub" id="pvSub">En direct</div>  
        </div>  
        <div class="pv-top-btns">  
          <button class="pv-ico" id="pvFavBtn" onclick="togglePlayerFav()">⭐</button>  
          <button class="pv-ico" onclick="openTimerModal()">⏱</button>  
          <button class="pv-ico" onclick="doPip()">⧉</button>  
        </div>  
      </div>  
      <div class="pv-center">  
        <button class="pv-ctrl" onclick="prevCh()">  
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M6 6h2v12H6zm3.5 6 8.5 6V6z"/></svg>  
        </button>  
        <button class="pv-play" id="pvPlayBtn" onclick="togglePlay()">  
          <svg id="pvPlayIco" width="22" height="22" viewBox="0 0 24 24" fill="currentColor"><polygon points="5 3 19 12 5 21 5 3"/></svg>  
        </button>  
        <button class="pv-ctrl" onclick="nextCh()">  
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M6 18l8.5-6L6 6v12zm2.5-6 5 3.5V8.5L8.5 12zM16 6h2v12h-2z"/></svg>  
        </button>  
      </div>  
      <div class="pv-bot">  
        <div class="pv-vol-row">  
          <button class="pv-ico" onclick="toggleMute()">  
            <svg id="pvVolIco" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"/><path d="M19.07 4.93a10 10 0 0 1 0 14.14"/><path d="M15.54 8.46a5 5 0 0 1 0 7.07"/></svg>  
          </button>  
          <input type="range" class="pv-vol" id="pvVol" min="0" max="100" value="80" oninput="setVol(this.value)">  
          <button class="pv-ico" onclick="toggleFullscreen()">  
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M8 3H5a2 2 0 0 0-2 2v3m18 0V5a2 2 0 0 0-2-2h-3m0 18h3a2 2 0 0 0 2-2v-3M3 16v3a2 2 0 0 0 2 2h3"/></svg>  
          </button>  
        </div>  
        <div class="pv-timer-display" id="pvTimerDisp"></div>  
      </div>  
    </div>  
    <div class="pv-load" id="pvLoad"><div class="spinner"></div></div>  
  </div>  
  <div class="pv-tabs" id="pvTabs">  
    <div class="pv-tab on" onclick="setPvTab('epg')">📅 Programme</div>  
    <div class="pv-tab" onclick="setPvTab('similar')">📺 Similaires</div>  
    <div class="pv-tab" onclick="setPvTab('rate')">⭐ Note</div>  
  </div>  
  <div class="pv-info" id="pvInfo"></div>  
</div>  
  
<!-- CREDITS MODAL -->  
  
<div id="creditsModal" onclick="closeCreditsOutside(event)">  
  <div class="cr-sheet">  
    <div class="sh-handle"></div>  
    <div class="cr-title">💎 Mes Crédits</div>  
    <div class="cr-sub">Utilisez vos crédits pour accéder aux contenus premium</div>  
    <div class="cr-balance">  
      <div>  
        <div class="cr-bal-lbl">SOLDE ACTUEL</div>  
        <div class="cr-bal-val" id="crBalVal">0</div>  
        <div class="cr-bal-sub">crédits disponibles</div>  
      </div>  
      <div class="cr-bal-ico">💎</div>  
    </div>  
    <div style="font-size:13px;font-weight:700;color:var(--text2);margin-bottom:10px;">Recharger des crédits</div>  
    <div class="cr-plans">  
      <div class="cr-plan" onclick="buyCredits(100,1.99)"><div class="cr-plan-credits">100</div><div class="cr-plan-price">1,99 €</div></div>  
      <div class="cr-plan best" onclick="buyCredits(300,4.99)"><div class="cr-plan-badge">🔥 Populaire</div><div class="cr-plan-credits">300</div><div class="cr-plan-price">4,99 €</div></div>  
      <div class="cr-plan" onclick="buyCredits(600,8.99)"><div class="cr-plan-credits">600</div><div class="cr-plan-price">8,99 €</div></div>  
      <div class="cr-plan" onclick="buyCredits(1500,19.99)"><div class="cr-plan-badge">💎 Premium</div><div class="cr-plan-credits">1500</div><div class="cr-plan-price">19,99 €</div></div>  
    </div>  
    <div style="font-size:13px;font-weight:700;color:var(--text2);margin-bottom:10px;">Historique des transactions</div>  
    <div class="cr-history" id="crHistory"></div>  
    <button class="btn-ghost" style="margin-top:14px;" onclick="closeCredits()">Fermer</button>  
  </div>  
</div>  
  
<!-- NOTIFS PANEL -->  
  
<div id="notifsPanel">  
  <div class="np-head">  
    <h2>🔔 Notifications</h2>  
    <div class="np-close" onclick="closeNotifs()">✕</div>  
  </div>  
  <div class="np-list" id="npList"></div>  
</div>  
  
<!-- ADD PLAYLIST SHEET -->  
  
<div id="addPlSheet" style="position:absolute;inset:0;background:var(--overlay);z-index:500;display:none;align-items:flex-end;" onclick="closeAddPlOutside(event)">  
  <div class="cr-sheet">  
    <div class="sh-handle"></div>  
    <div class="cr-title">📡 Ajouter une playlist</div>  
    <div class="cr-sub">Ajoutez une nouvelle source M3U</div>  
    <div class="icard">  
      <label>Nom</label>  
      <input type="text" id="newPlName" placeholder="Ma Playlist 2" style="margin-bottom:10px;">  
      <label>URL M3U</label>  
      <input type="url" id="newPlUrl" placeholder="http://..." inputmode="url">  
    </div>  
    <button class="btn-main" onclick="addNewPlaylist()">Ajouter</button>  
    <button class="btn-ghost" onclick="closeAddPl()">Annuler</button>  
  </div>  
</div>  
  
<!-- TIMER MODAL -->  
  
<div id="timerModal" onclick="closeTimerOutside(event)">  
  <div class="timer-card">  
    <div class="timer-title">⏱ Timer d'arrêt</div>  
    <div class="timer-opts">  
      <div class="t-opt" onclick="setTimer(15)">15 min</div>  
      <div class="t-opt" onclick="setTimer(30)">30 min</div>  
      <div class="t-opt" onclick="setTimer(45)">45 min</div>  
      <div class="t-opt" onclick="setTimer(60)">1h</div>  
      <div class="t-opt" onclick="setTimer(90)">1h30</div>  
      <div class="t-opt" onclick="setTimer(120)">2h</div>  
    </div>  
    <button class="btn-ghost" style="margin-bottom:6px;" onclick="setTimer(0)">Désactiver</button>  
    <button class="btn-ghost" onclick="closeTimer()">Fermer</button>  
  </div>  
</div>  
  
<!-- TOAST -->  
  
<div class="toast" id="toast"></div>  
  
<script>  
// ===================== STATE =====================  
let S = {  
  channels: [], // all channels  
  filtered: [],  
  favorites: [],  
  history: [],  
  ratings: {},  
  playlists: [], // [{name, url, count}]  
  credits: 500,  
  creditHistory: [],  
  notifications: [],  
  settings: {  
    theme: 'dark', accent: 'red', lang: 'fr',  
    pin: '', pinEnabled: false,  
    randomPlay: false, pip: false  
  },  
  currentCh: -1,  
  currentType: 'tv', // tv | films | series  
  currentNav: 'home',  
  pvTab: 'epg',  
  playing: false,  
  timerMin: 0,  
  timerInterval: null,  
  timerRemain: 0,  
  overlayTimeout: null,  
  hls: null,  
};  
  
// Translations  
const T = {  
  fr: {  
    home:'Accueil', favs:'Favoris', history:'Historique', settings:'Réglages',  
    noChannels:'Aucune chaîne', importFirst:'Importez une playlist pour commencer',  
    liveTV:'Télévision en direct', popular:'Chaînes populaires', allChannels:'Toutes les chaînes',  
    watching:'En lecture', credits:'crédits', addedFav:'Ajouté aux favoris', removedFav:'Retiré des favoris',  
    timerSet:'Timer réglé sur', mins:'min', timerOff:'Timer désactivé',  
    pinError:'Code PIN incorrect', welcome:'Bienvenue !', creditsBought:'crédits achetés !',  
    lang:'Langue', theme:'Apparence', darkMode:'Mode sombre', accentColor:'Couleur principale',  
    playlists:'Mes Playlists', security:'Sécurité', pinLabel:'Code PIN',  
    timer:'Timer d\'arrêt', random:'Lecture aléatoire',  
    clear:'Réinitialiser l\'application', credits2:'Gérer mes crédits',  
    enabled:'Activé', disabled:'Désactivé', searchPh:'Tapez pour rechercher',  
    films:'Films', series:'Séries', tv:'Télé',  
    loadOk:'chaînes chargées !', loadErr:'Impossible de charger la playlist',  
  },  
  en: {  
    home:'Home', favs:'Favorites', history:'History', settings:'Settings',  
    noChannels:'No channels', importFirst:'Import a playlist to get started',  
    liveTV:'Live Television', popular:'Popular Channels', allChannels:'All Channels',  
    watching:'Now Playing', credits:'credits', addedFav:'Added to favorites', removedFav:'Removed from favorites',  
    timerSet:'Timer set to', mins:'min', timerOff:'Timer disabled',  
    pinError:'Incorrect PIN code', welcome:'Welcome!', creditsBought:'credits purchased!',  
    lang:'Language', theme:'Appearance', darkMode:'Dark Mode', accentColor:'Main Color',  
    playlists:'My Playlists', security:'Security', pinLabel:'PIN Code',  
    timer:'Sleep Timer', random:'Random Play',  
    clear:'Reset Application', credits2:'Manage Credits',  
    enabled:'Enabled', disabled:'Disabled', searchPh:'Type to search',  
    films:'Movies', series:'Series', tv:'TV',  
    loadOk:'channels loaded!', loadErr:'Could not load playlist',  
  },  
  ar: {  
    home:'الرئيسية', favs:'المفضلة', history:'السجل', settings:'الإعدادات',  
    noChannels:'لا توجد قنوات', importFirst:'أضف قائمة تشغيل للبدء',  
    liveTV:'التلفزيون المباشر', popular:'القنوات الشائعة', allChannels:'جميع القنوات',  
    watching:'يُشاهد الآن', credits:'رصيد', addedFav:'أضيف للمفضلة', removedFav:'حُذف من المفضلة',  
    timerSet:'تم ضبط المؤقت على', mins:'دقيقة', timerOff:'تم إلغاء المؤقت',  
    pinError:'رمز PIN غير صحيح', welcome:'مرحباً!', creditsBought:'رصيد تم شراؤه!',  
    lang:'اللغة', theme:'المظهر', darkMode:'الوضع الداكن', accentColor:'اللون الرئيسي',  
    playlists:'قوائم التشغيل', security:'الأمان', pinLabel:'رمز PIN',  
    timer:'مؤقت إيقاف التشغيل', random:'تشغيل عشوائي',  
    clear:'إعادة تعيين التطبيق', credits2:'إدارة الرصيد',  
    enabled:'مفعّل', disabled:'معطّل', searchPh:'اكتب للبحث',  
    films:'أفلام', series:'مسلسلات', tv:'تلفزيون',  
    loadOk:'قناة محملة!', loadErr:'تعذّر تحميل القائمة',  
  }  
};  
  
function t(k) { return (T[S.settings.lang]||T.fr)[k] || k; }  
  
// ===================== INIT =====================  
window.addEventListener('load', () => {  
  loadLocalStorage();  
  // Load HLS.js  
  const sc = document.createElement('script');  
  sc.src = 'https://cdnjs.cloudflare.com/ajax/libs/hls.js/1.5.7/hls.min.js';  
  document.head.appendChild(sc);  
  // Splash -> PIN or Main after 2.3s  
  setTimeout(() => {  
    applyTheme();  
    if (S.settings.pinEnabled && S.settings.pin) {  
      showScreen('pinScreen');  
    } else if (!S.playlists.length) {  
      showScreen('setupScreen');  
    } else {  
      showScreen('mainScreen');  
      renderHome();  
      updateUI();  
    }  
  }, 2300);  
  // Add sample notifications  
  if (!S.notifications.length) {  
    S.notifications = [  
      {ico:'📺', title:'Nouveau contenu disponible', desc:'Des nouvelles chaînes ont été ajoutées à votre playlist.', time:'Il y a 5 min', read:false},  
      {ico:'💎', title:'Bienvenue sur LdetppStream', desc:'Profitez de 500 crédits offerts pour découvrir l\'application!', time:'Il y a 1h', read:false},  
      {ico:'🔔', title:'Mise à jour disponible', desc:'Version 2.0 disponible avec de nouvelles fonctionnalités.', time:'Il y a 2h', read:true},  
    ];  
    saveLS();  
  }  
  renderNotifs();  
  updateCreditHistory();  
});  
  
function loadLocalStorage() {  
  try {  
    const d = localStorage.getItem('ldetpp_v2');  
    if (d) Object.assign(S, JSON.parse(d));  
  } catch(e) {}  
}  
function saveLS() {  
  try { localStorage.setItem('ldetpp_v2', JSON.stringify(S)); } catch(e){}  
}  
  
function applyTheme() {  
  document.documentElement.setAttribute('data-theme', S.settings.theme);  
  document.documentElement.setAttribute('data-accent', S.settings.accent);  
  const dt = document.getElementById('themeToggle');  
  if (dt) dt.classList.toggle('on', S.settings.theme === 'dark');  
  document.querySelectorAll('.accent-opt').forEach(a => {  
    a.classList.toggle('on', a.dataset.ac === S.settings.accent);  
  });  
  document.querySelectorAll('.lang-opt').forEach(l => {  
    l.classList.toggle('on', l.id === 'lang-' + S.settings.lang);  
  });  
  updateUI();  
}  
  
function updateUI() {  
  document.getElementById('headerCredits').textContent = S.credits;  
  document.getElementById('profCredits').textContent = S.credits;  
  document.getElementById('settCredits').textContent = S.credits;  
  document.getElementById('crBalVal').textContent = S.credits;  
  renderPlaylists();  
  updatePinUI();  
  updateTimerUI();  
  updateRandomUI();  
  updatePipUI();  
  updateLang();  
}  
  
function updateLang() {  
  const el = id => document.getElementById(id);  
  el('lbl-lang') && (el('lbl-lang').textContent = t('lang'));  
  el('lbl-theme') && (el('lbl-theme').textContent = t('theme'));  
  el('lbl-darkmode') && (el('lbl-darkmode').textContent = t('darkMode'));  
  el('val-darkmode') && (el('val-darkmode').textContent = t(S.settings.theme === 'dark' ? 'enabled' : 'disabled'));  
  el('lbl-accent') && (el('lbl-accent').textContent = t('accentColor'));  
  el('lbl-playlists') && (el('lbl-playlists').textContent = t('playlists'));  
  el('lbl-security') && (el('lbl-security').textContent = t('security'));  
  el('lbl-pin') && (el('lbl-pin').textContent = t('pinLabel'));  
  el('lbl-timer') && (el('lbl-timer').textContent = t('timer'));  
  el('lbl-random') && (el('lbl-random').textContent = t('random'));  
  el('lbl-credits') && (el('lbl-credits').textContent = t('credits2'));  
  el('lbl-clear') && (el('lbl-clear').textContent = t('clear'));  
  el('srch-ph') && (el('srch-ph').textContent = t('searchPh'));  
  el('srchInput') && (el('srchInput').placeholder = t('searchPh'));  
}  
  
function showScreen(id) {  
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));  
  document.getElementById(id).classList.add('active');  
}  
  
// ===================== PIN =====================  
let pinEntry = '';  
let pinSetMode = false;  
  
function pinKey(k) {  
  if (k === 'bio') { skipPin(); return; }  
  if (k === 'del') {  
    pinEntry = pinEntry.slice(0, -1);  
    updatePinDots();  
    return;  
  }  
  pinEntry += k;  
  updatePinDots();  
  if (pinEntry.length === 4) {  
    setTimeout(() => checkPin(), 200);  
  }  
}  
  
function updatePinDots(err = false) {  
  for (let i = 0; i < 4; i++) {  
    const d = document.getElementById('pd' + i);  
    d.className = 'pin-dot';  
    if (err) d.classList.add('err');  
    else if (i < pinEntry.length) d.classList.add('on');  
  }  
}  
  
function checkPin() {  
  if (pinSetMode) {  
    S.settings.pin = pinEntry;  
    S.settings.pinEnabled = true;  
    saveLS(); updatePinUI();  
    pinEntry = '';  
    toast('PIN activé ✓', 'ok');  
    showScreen('mainScreen'); renderHome(); updateUI();  
    return;  
  }  
  if (pinEntry === S.settings.pin) {  
    pinEntry = '';  
    showScreen('mainScreen'); renderHome(); updateUI();  
  } else {  
    updatePinDots(true);  
    document.getElementById('pinHint').textContent = t('pinError');  
    setTimeout(() => {  
      pinEntry = '';  
      updatePinDots();  
      document.getElementById('pinHint').textContent = 'Code PIN requis';  
    }, 800);  
  }  
}  
  
function skipPin() {  
  pinEntry = '';  
  showScreen('mainScreen'); renderHome(); updateUI();  
}  
  
function updatePinUI() {  
  const t2 = document.getElementById('pinToggle');  
  const v = document.getElementById('val-pin');  
  if (t2) t2.classList.toggle('on', !!S.settings.pinEnabled);  
  if (v) v.textContent = S.settings.pinEnabled ? t('enabled') : t('disabled');  
}  
  
function togglePin() {  
  if (S.settings.pinEnabled) {  
    S.settings.pinEnabled = false;  
    S.settings.pin = '';  
    saveLS(); updatePinUI();  
    toast('PIN désactivé', 'info');  
  } else {  
    pinSetMode = true;  
    document.getElementById('pinUser').textContent = 'Créez un code PIN';  
    document.getElementById('pinHint').textContent = 'Entrez 4 chiffres';  
    pinEntry = '';  
    updatePinDots();  
    showScreen('pinScreen');  
  }  
}  
  
// ===================== SETUP =====================  
let setupTab = 'url';  
  
function switchStab(t2) {  
  setupTab = t2;  
  ['url','file','paste'].forEach(x => {  
    document.getElementById('stab-'+x).classList.toggle('on', x === t2);  
    document.getElementById('stp-'+x).style.display = x === t2 ? 'block' : 'none';  
  });  
}  
  
function ev_dragover(e) { e.preventDefault(); document.getElementById('setupDrop').classList.add('drag'); }  
function ev_dragleave() { document.getElementById('setupDrop').classList.remove('drag'); }  
function ev_drop(e) {  
  e.preventDefault();  
  document.getElementById('setupDrop').classList.remove('drag');  
  const f = e.dataTransfer.files[0];  
  if (f) { const r = new FileReader(); r.onload = ev => loadM3U(ev.target.result, f.name); r.readAsText(f); }  
}  
  
function handleSetupFile(inp) {  
  const f = inp.files[0];  
  if (!f) return;  
  const r = new FileReader();  
  r.onload = ev => { loadM3U(ev.target.result, f.name); showScreen('mainScreen'); renderHome(); updateUI(); };  
  r.readAsText(f);  
}  
  
function doSetup() {  
  if (setupTab === 'url') {  
    const name = document.getElementById('plName').value.trim() || 'Playlist';  
    const url = document.getElementById('plUrl').value.trim();  
    if (!url) { toast('Entrez une URL', 'err'); return; }  
    toast('Chargement...', 'info');  
    fetch(url).then(r => r.text()).then(text => {  
      loadM3U(text, name, url);  
      showScreen('mainScreen'); renderHome(); updateUI();  
    }).catch(() => toast(t('loadErr') + ' (CORS)', 'err'));  
  } else if (setupTab === 'paste') {  
    const text = document.getElementById('plPaste').value.trim();  
    if (!text) { toast('Contenu vide', 'err'); return; }  
    loadM3U(text, 'Playlist collée');  
    showScreen('mainScreen'); renderHome(); updateUI();  
  }  
}  
  
function skipSetup() {  
  showScreen('mainScreen');  
  renderHome(); updateUI();  
}  
  
function loadM3U(text, name = 'Playlist', url = '') {  
  const parsed = parseM3U(text);  
  if (!parsed.length) { toast(t('loadErr'), 'err'); return; }  
  S.channels = [...S.channels.filter(c => c.plName !== name), ...parsed.map(c => ({...c, plName: name}))];  
  const existing = S.playlists.findIndex(p => p.name === name);  
  if (existing > -1) S.playlists[existing] = {name, url, count: parsed.length};  
  else S.playlists.push({name, url, count: parsed.length});  
  saveLS();  
  toast(parsed.length + ' ' + t('loadOk'), 'ok');  
  renderHome();  
}  
  
function parseM3U(text) {  
  const lines = text.split('\n').map(l => l.trim()).filter(Boolean);  
  const result = [];  
  let cur = {};  
  for (const line of lines) {  
    if (line.startsWith('#EXTINF:')) {  
      cur = {};  
      const nameM = line.match(/,(.+)$/);  
      if (nameM) cur.name = nameM[1].trim();  
      const m = (k) => { const r = line.match(new RegExp(k + '="([^"]*)"')); return r ? r[1] : ''; };  
      if (m('tvg-name')) cur.name = m('tvg-name');  
      cur.logo = m('tvg-logo');  
      cur.group = m('group-title') || 'Autres';  
      cur.id = m('tvg-id');  
    } else if (line.startsWith('http') && cur.name) {  
      cur.url = line;  
      result.push({...cur});  
      cur = {};  
    }  
  }  
  return result;  
}  
  
// ===================== HOME =====================  
function renderHome() {  
  const el = document.getElementById('homePage');  
  if (!S.channels.length) {  
    el.innerHTML = `<div style="height:60px;"></div><div class="empty-big">  
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="var(--text3)" stroke-width="1.3"><rect x="2" y="7" width="20" height="15" rx="2"/><path d="M16 2 8 2"/></svg>  
      <h3>${t('noChannels')}</h3><p>${t('importFirst')}</p>  
      <button class="btn-main" style="width:auto;padding:12px 24px;" onclick="showScreen('setupScreen')">${t('playlists')}</button>  
    </div>`;  
    return;  
  }  
  
  const type = S.currentType;  
  const chans = filterByType(S.channels, type);  
  const cats = [...new Set(chans.map(c => c.group || 'Autres'))].sort();  
  const hero = chans[Math.floor(Math.random() * Math.min(chans.length, 10))];  
  
  let html = '';  
  
  // Hero  
  if (hero) {  
    html += `<div class="hero" style="margin-top:88px;">  
      <div class="hero-bg"><div class="hero-pattern"></div></div>  
      <div class="hero-grad"></div>  
      <div class="hero-content">  
        <div class="hero-badge"><div class="live-dot"></div>${type === 'tv' ? 'LIVE' : type === 'films' ? 'VOD' : 'SÉRIE'}</div>  
        <div class="hero-title">${hero.name}</div>  
        <div class="hero-meta">  
          <span>${hero.group || 'Autres'}</span>  
          <div class="hero-dot"></div>  
          <span>HD</span>  
          ${hero.plName ? `<div class="hero-dot"></div><span>${hero.plName}</span>` : ''}  
        </div>  
        <div class="hero-btns">  
          <button class="hbtn hbtn-play" onclick="playCh(${S.channels.indexOf(hero)})">  
            <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><polygon points="5 3 19 12 5 21 5 3"/></svg>  
            ${type === 'tv' ? 'Regarder' : type === 'films' ? 'Voir le film' : 'Voir la série'}  
          </button>  
          <button class="hbtn hbtn-info" onclick="toggleFav(${S.channels.indexOf(hero)});this.textContent=S.favorites.includes(S.channels[${S.channels.indexOf(hero)}]?.url)?'★ Favori':'+ Favori'">  
            ${S.favorites.includes(hero.url) ? '★ Favori' : '+ Favori'}  
          </button>  
        </div>  
      </div>  
    </div>`;  
  }  
  
  // Category pills  
  html += `<div class="section">  
    <div class="cat-row" id="catRow">  
      <div class="cat-pill on" onclick="filterCat(null,this)">Tous</div>  
      ${cats.map(c => `<div class="cat-pill" onclick="filterCat('${esc(c)}',this)">${c}</div>`).join('')}  
    </div>  
  </div>`;  
  
  // Popular section (first 10)  
  const popular = chans.slice(0, 12);  
  html += `<div class="section">  
    <div class="sec-hd"><span class="sec-title">${t(type === 'tv' ? 'liveTV' : type === 'films' ? 'films' : 'series')}</span></div>  
    <div class="${type === 'tv' ? 'ch-row' : 'vod-row'}" id="popularRow">`;  
  popular.forEach(ch => {  
    const idx = S.channels.indexOf(ch);  
    html += type === 'tv' ? chCard(ch, idx) : vodCard(ch, idx, type);  
  });  
  html += `</div></div>`;  
  
  // Favorites (if any)  
  const favChans = chans.filter(c => S.favorites.includes(c.url)).slice(0, 10);  
  if (favChans.length) {  
    html += `<div class="section">  
      <div class="sec-hd"><span class="sec-title">⭐ ${t('favs')}</span></div>  
      <div class="${type === 'tv' ? 'ch-row' : 'vod-row'}">`;  
    favChans.forEach(ch => {  
      const idx = S.channels.indexOf(ch);  
      html += type === 'tv' ? chCard(ch, idx) : vodCard(ch, idx, type);  
    });  
    html += `</div></div>`;  
  }  
  
  // All channels by category  
  cats.slice(0, 6).forEach(cat => {  
    const catChans = chans.filter(c => (c.group || 'Autres') === cat).slice(0, 8);  
    if (!catChans.length) return;  
    html += `<div class="section">  
      <div class="sec-hd"><span class="sec-title">${cat}</span><span class="sec-more" onclick="filterCat('${esc(cat)}',null)">Voir tout</span></div>  
      <div class="${type === 'tv' ? 'ch-row' : 'vod-row'}">`;  
    catChans.forEach(ch => {  
      const idx = S.channels.indexOf(ch);  
      html += type === 'tv' ? chCard(ch, idx) : vodCard(ch, idx, type);  
    });  
    html += `</div></div>`;  
  });  
  
  el.innerHTML = html;  
}  
  
function filterByType(channels, type) {  
  if (!channels.length) return [];  
  const filmKw = /film|movie|cinema|vod|4k|hd|1080|720/i;  
  const serieKw = /serie|séri|season|saison|episode|S\d+|E\d+/i;  
  const tvKw = /news|sport|music|enfant|kids|kids|documentary|live|direct|FR|TF1|M6|Canal|BFM|Arte|France/i;  
  if (type === 'tv') return channels.filter(c => !filmKw.test(c.group + c.name) && !serieKw.test(c.group + c.name));  
  if (type === 'films') return channels.filter(c => filmKw.test(c.group + c.name) || filmKw.test(c.name));  
  if (type === 'series') return channels.filter(c => serieKw.test(c.group + c.name) || serieKw.test(c.name));  
  return channels;  
}  
  
function chCard(ch, idx) {  
  const isFav = S.favorites.includes(ch.url);  
  const rating = S.ratings[ch.url] || 0;  
  const abbr = (ch.name||'').slice(0,3).toUpperCase();  
  const logo = ch.logo ? `<img src="${ch.logo}" onerror="this.style.display='none';this.nextSibling.style.display='block'"><span class="chc-abbr" style="display:none">${abbr}</span>` : `<span class="chc-abbr">${abbr}</span>`;  
  const stars = [1,2,3,4,5].map(s => `<span class="chc-star ${s <= rating ? 'on' : ''}">★</span>`).join('');  
  return `<div class="chc" onclick="playCh(${idx})">  
    <div class="chc-thumb">${logo}<div class="chc-live">LIVE</div></div>  
    <div class="chc-name">${ch.name}</div>  
    <div class="chc-grp">${ch.group||'Autres'}</div>  
    <div class="chc-stars">${stars}</div>  
  </div>`;  
}  
  
function vodCard(ch, idx, type) {  
  const abbr = (ch.name||'').slice(0,2).toUpperCase();  
  const logo = ch.logo ? `<img src="${ch.logo}" onerror="this.style.display='none';this.parentNode.querySelector('.vodc-abbr').style.display='block'"><span class="vodc-abbr" style="display:none">${abbr}</span>` : `<span class="vodc-abbr">${abbr}</span>`;  
  return `<div class="vodc" onclick="playCh(${idx})">  
    <div class="vodc-poster">${logo}  
      <div class="vodc-badge">${type === 'films' ? '🎬' : '🎭'}</div>  
      <div class="vodc-cr">💎 5</div>  
    </div>  
    <div class="vodc-name">${ch.name}</div>  
    <div class="vodc-info">${ch.group||'VOD'}</div>  
  </div>`;  
}  
  
function esc(s) { return (s||'').replace(/'/g, "\\'").replace(/"/g, '&quot;'); }  
  
function filterCat(cat, el) {  
  document.querySelectorAll('.cat-pill').forEach(p => p.classList.remove('on'));  
  if (el) el.classList.add('on');  
  const type = S.currentType;  
  let chans = filterByType(S.channels, type);  
  if (cat) chans = chans.filter(c => (c.group||'Autres') === cat);  
  const row = document.getElementById('popularRow');  
  if (!row) return;  
  const isVod = type !== 'tv';  
  row.className = isVod ? 'vod-row' : 'ch-row';  
  row.innerHTML = chans.slice(0, 20).map(ch => {  
    const idx = S.channels.indexOf(ch);  
    return isVod ? vodCard(ch, idx, type) : chCard(ch, idx);  
  }).join('');  
}  
  
// ===================== TYPE TABS =====================  
function setType(type) {  
  S.currentType = type;  
  document.querySelectorAll('.type-tab').forEach((t2, i) => {  
    t2.classList.toggle('on', ['tv','films','series'][i] === type);  
  });  
  renderHome();  
}  
  
// ===================== PLAYER =====================  
let overlayVisible = true;  
  
function playCh(idx) {  
  S.currentCh = idx;  
  const ch = S.channels[idx];  
  if (!ch) return;  
  // Deduct credits for VOD  
  if (S.currentType !== 'tv' && S.credits >= 5) { S.credits -= 5; updateUI(); }  
  addHistory(ch);  
  document.getElementById('playerScreen').classList.add('open');  
  document.getElementById('pvTitle').textContent = ch.name;  
  document.getElementById('pvSub').textContent = ch.group || '';  
  document.getElementById('pvLoad').style.display = 'flex';  
  renderPvInfo();  
  const fav = S.favorites.includes(ch.url);  
  document.getElementById('pvFavBtn').textContent = fav ? '★' : '☆';  
  if (S.hls) { S.hls.destroy(); S.hls = null; }  
  const vid = document.getElementById('pv');  
  vid.src = '';  
  const url = ch.url;  
  const isHLS = url.includes('.m3u8') || url.includes('m3u8');  
  const tryLoad = () => {  
    if (isHLS && typeof Hls !== 'undefined' && Hls.isSupported()) {  
      S.hls = new Hls({enableWorker:true});  
      S.hls.loadSource(url);  
      S.hls.attachMedia(vid);  
      S.hls.on(Hls.Events.MANIFEST_PARSED, () => {  
        vid.play().catch(()=>{});  
        document.getElementById('pvLoad').style.display = 'none';  
        S.playing = true; updatePlayBtn();  
      });  
      S.hls.on(Hls.Events.ERROR, (e, d) => {  
        if (d.fatal) { document.getElementById('pvLoad').style.display = 'none'; toast('Erreur de flux', 'err'); }  
      });  
    } else {  
      vid.src = url;  
      vid.play().then(() => {  
        document.getElementById('pvLoad').style.display = 'none';  
        S.playing = true; updatePlayBtn();  
      }).catch(() => { document.getElementById('pvLoad').style.display = 'none'; toast('Impossible de lire', 'err'); });  
    }  
  };  
  // Wait for HLS if not loaded yet  
  if (isHLS && typeof Hls === 'undefined') setTimeout(tryLoad, 500);  
  else tryLoad();  
  showOverlay();  
  saveLS();  
}  
  
function closePlayer() {  
  document.getElementById('playerScreen').classList.remove('open');  
  const vid = document.getElementById('pv');  
  if (S.hls) { S.hls.destroy(); S.hls = null; }  
  vid.pause(); vid.src = '';  
  S.playing = false;  
  clearTimerInterval();  
}  
  
function togglePlay() {  
  const vid = document.getElementById('pv');  
  if (vid.paused) { vid.play(); S.playing = true; }  
  else { vid.pause(); S.playing = false; }  
  updatePlayBtn();  
}  
  
function updatePlayBtn() {  
  const ico = document.getElementById('pvPlayIco');  
  if (!ico) return;  
  ico.innerHTML = S.playing  
    ? '<rect x="6" y="4" width="4" height="16"/><rect x="14" y="4" width="4" height="16"/>'  
    : '<polygon points="5 3 19 12 5 21 5 3"/>';  
}  
  
function prevCh() {  
  if (S.currentCh > 0) playCh(S.settings.randomPlay ? randIdx() : S.currentCh - 1);  
}  
function nextCh() {  
  if (S.currentCh < S.channels.length - 1) playCh(S.settings.randomPlay ? randIdx() : S.currentCh + 1);  
}  
function randIdx() { return Math.floor(Math.random() * S.channels.length); }  
  
function toggleMute() {  
  const vid = document.getElementById('pv');  
  vid.muted = !vid.muted;  
  const ico = document.getElementById('pvVolIco');  
  ico.innerHTML = vid.muted  
    ? '<polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"/><line x1="23" y1="9" x2="17" y2="15"/><line x1="17" y1="9" x2="23" y2="15"/>'  
    : '<polygon points="11 5 6 9 2 9 2 15 6 15 11 19 11 5"/><path d="M19.07 4.93a10 10 0 0 1 0 14.14"/><path d="M15.54 8.46a5 5 0 0 1 0 7.07"/>';  
}  
  
function setVol(v) {  
  document.getElementById('pv').volume = v / 100;  
  document.getElementById('pv').muted = v == 0;  
}  
  
function toggleFullscreen() {  
  const w = document.getElementById('pvWrap');  
  if (!document.fullscreenElement) w.requestFullscreen?.();  
  else document.exitFullscreen?.();  
}  
  
function doPip() {  
  const vid = document.getElementById('pv');  
  if (document.pictureInPictureEnabled && vid.requestPictureInPicture) {  
    if (document.pictureInPictureElement) document.exitPictureInPicture();  
    else vid.requestPictureInPicture();  
  } else toast('PiP non supporté', 'err');  
}  
  
function showOverlay() {  
  const ov = document.getElementById('pvOv');  
  ov.classList.add('vis');  
  overlayVisible = true;  
  clearTimeout(S.overlayTimeout);  
  S.overlayTimeout = setTimeout(() => {  
    ov.classList.remove('vis');  
    overlayVisible = false;  
  }, 4000);  
}  
  
function toggleOverlay() {  
  if (overlayVisible) {  
    clearTimeout(S.overlayTimeout);  
    document.getElementById('pvOv').classList.remove('vis');  
    overlayVisible = false;  
  } else {  
    showOverlay();  
  }  
}  
  
function togglePlayerFav() {  
  if (S.currentCh < 0) return;  
  toggleFav(S.currentCh);  
  const ch = S.channels[S.currentCh];  
  document.getElementById('pvFavBtn').textContent = S.favorites.includes(ch.url) ? '★' : '☆';  
}  
  
// ===================== PLAYER TABS =====================  
function setPvTab(tab) {  
  S.pvTab = tab;  
  document.querySelectorAll('.pv-tab').forEach((t2, i) => {  
    t2.classList.toggle('on', ['epg','similar','rate'][i] === tab);  
  });  
  renderPvInfo();  
}  
  
function renderPvInfo() {  
  const ch = S.channels[S.currentCh];  
  const el = document.getElementById('pvInfo');  
  if (!el || !ch) return;  
  const tab = S.pvTab;  
  if (tab === 'epg') {  
    const now = new Date();  
    const epgItems = generateEPG(ch.name);  
    let cur = epgItems[0], next = epgItems[1];  
    const prog = Math.round((now.getMinutes() / 60) * 100);  
    el.innerHTML = `  
      <div class="epg-sec">  
        <div class="epg-now">  
          <div class="epg-badge">EN COURS</div>  
          <div><div class="epg-pt">${cur.title}</div><div class="epg-tm">${cur.time} — ${cur.duration}</div></div>  
        </div>  
        <div class="epg-prog"><div class="epg-prog-fill" style="width:${prog}%"></div></div>  
      </div>  
      <div class="epg-sec">  
        <div class="epg-now">  
          <div class="epg-next-badge">SUIVANT</div>  
          <div><div class="epg-pt">${next.title}</div><div class="epg-tm">${next.time}</div></div>  
        </div>  
      </div>  
      <div class="sec-label">Programme du jour</div>  
      ${epgItems.map(e => `<div class="epg-sec"><div class="epg-li">  
        <div class="epg-time">${e.time}</div>  
        <div class="epg-ii"><div class="epg-title">${e.title}</div><div class="epg-desc">${e.desc}</div></div>  
      </div></div>`).join('')}`;  
  } else if (tab === 'similar') {  
    const similar = S.channels.filter(c => c.group === ch.group && c.url !== ch.url).slice(0, 10);  
    if (!similar.length) { el.innerHTML = '<div class="srch-empty"><p>Aucune chaîne similaire</p></div>'; return; }  
    el.innerHTML = '<div class="sec-label">Chaînes similaires</div>' +  
      similar.map((c, i) => {  
        const idx = S.channels.indexOf(c);  
        const abbr = (c.name||'').slice(0,3).toUpperCase();  
        const logo = c.logo ? `<img src="${c.logo}" onerror="this.style.display='none';this.nextSibling.style.display='block'"><span class="ch-li-abb" style="display:none">${abbr}</span>` : `<span class="ch-li-abb">${abbr}</span>`;  
        return `<div class="ch-li" onclick="playCh(${idx})">  
          <div class="ch-li-logo">${logo}</div>  
          <div class="ch-li-info">  
            <div class="ch-li-name">${c.name}</div>  
            <div class="ch-li-epg">${c.group||''}</div>  
          </div>  
        </div>`;  
      }).join('');  
  } else if (tab === 'rate') {  
    const cur = S.ratings[ch.url] || 0;  
    el.innerHTML = `  
      <div class="star-rate">  
        <span class="star-rate-lbl">Votre note :</span>  
        ${[1,2,3,4,5].map(s => `<span class="sr-star ${s <= cur ? 'on' : ''}" onclick="rateCh(${s})">${s <= cur ? '★' : '☆'}</span>`).join('')}  
      </div>  
      <div style="padding:16px;font-size:13px;color:var(--text2);">  
        Notez cette chaîne pour retrouver vos meilleures chaînes plus facilement.  
      </div>`;  
  }  
}  
  
function rateCh(stars) {  
  if (S.currentCh < 0) return;  
  const ch = S.channels[S.currentCh];  
  S.ratings[ch.url] = stars;  
  saveLS();  
  renderPvInfo();  
  toast('Note enregistrée ' + '★'.repeat(stars), 'ok');  
}  
  
function generateEPG(chName) {  
  const shows = ['Journal de 20h','Le Grand Débat','Téléfilm','Documentaire','Série','Magazine','Sport en direct','Concert','Info continue','Météo','Cinéma','Talk show'];  
  const descs = ['En direct','Rediffusion','Exclusivité','Première diffusion','Live','Replay'];  
  const now = new Date();  
  return Array.from({length: 8}, (_, i) => {  
    const h = (now.getHours() + i) % 24;  
    const m = Math.floor(Math.random() * 4) * 15;  
    return {  
      time: `${String(h).padStart(2,'0')}:${String(m).padStart(2,'0')}`,  
      title: shows[Math.floor(Math.random() * shows.length)],  
      desc: descs[Math.floor(Math.random() * descs.length)],  
      duration: `${String((h + 1) % 24).padStart(2,'0')}:${String(m).padStart(2,'0')}`  
    };  
  });  
}  
  
// ===================== FAVORITES =====================  
function toggleFav(idx) {  
  const ch = S.channels[idx];  
  if (!ch) return;  
  const i = S.favorites.indexOf(ch.url);  
  if (i > -1) { S.favorites.splice(i, 1); toast(t('removedFav'), 'info'); }  
  else { S.favorites.push(ch.url); toast(t('addedFav'), 'ok'); addNotif('⭐', 'Ajouté aux favoris', ch.name); }  
  saveLS(); renderFavs();  
}  
  
function renderFavs() {  
  const el = document.getElementById('favsList');  
  if (!el) return;  
  const favs = S.channels.filter(c => S.favorites.includes(c.url));  
  if (!favs.length) {  
    el.innerHTML = '<div class="empty-big"><h3>Aucun favori</h3><p>Appuyez sur ☆ pour ajouter des chaînes en favoris</p></div>';  
    return;  
  }  
  el.innerHTML = favs.map(ch => {  
    const idx = S.channels.indexOf(ch);  
    const abbr = (ch.name||'').slice(0,3).toUpperCase();  
    const rating = S.ratings[ch.url] || 0;  
    const logo = ch.logo ? `<img src="${ch.logo}" onerror="this.style.display='none';this.nextSibling.style.display='block'"><span class="ch-li-abb" style="display:none">${abbr}</span>` : `<span class="ch-li-abb">${abbr}</span>`;  
    return `<div class="ch-li" onclick="playCh(${idx})">  
      <div class="ch-li-logo">${logo}</div>  
      <div class="ch-li-info">  
        <div class="ch-li-name">${ch.name}</div>  
        <div class="ch-li-epg">${ch.group||''}</div>  
      </div>  
      <div class="ch-li-r">  
        <div class="fav-btn on" onclick="event.stopPropagation();toggleFav(${idx})">★</div>  
        <div class="ch-li-stars">${[1,2,3,4,5].map(s=>`<span class="li-star ${s<=rating?'on':''}">★</span>`).join('')}</div>  
      </div>  
    </div>`;  
  }).join('');  
}  
  
// ===================== HISTORY =====================  
function addHistory(ch) {  
  const entry = {url: ch.url, name: ch.name, logo: ch.logo, group: ch.group, time: new Date().toLocaleString('fr')};  
  S.history = [entry, ...S.history.filter(h => h.url !== ch.url)].slice(0, 50);  
  saveLS(); renderHistory();  
}  
  
function renderHistory() {  
  const el = document.getElementById('histList');  
  if (!el) return;  
  if (!S.history.length) {  
    el.innerHTML = '<div class="empty-big"><h3>Aucun historique</h3><p>Vos chaînes récemment regardées apparaîtront ici</p></div>';  
    return;  
  }  
  el.innerHTML = S.history.map(h => {  
    const idx = S.channels.findIndex(c => c.url === h.url);  
    const abbr = (h.name||'').slice(0,3).toUpperCase();  
    const logo = h.logo ? `<img src="${h.logo}" onerror="this.style.display='none';this.nextSibling.style.display='block'"><span class="hist-abb" style="display:none">${abbr}</span>` : `<span class="hist-abb">${abbr}</span>`;  
    return `<div class="hist-li" onclick="${idx > -1 ? `playCh(${idx})` : ''}">  
      <div class="hist-thumb">${logo}</div>  
      <div class="hist-info">  
        <div class="hist-name">${h.name}</div>  
        <div class="hist-time">🕐 ${h.time} • ${h.group||''}</div>  
      </div>  
    </div>`;  
  }).join('');  
}  
  
// ===================== SEARCH =====================  
function openSearch() { document.getElementById('searchOv').classList.add('open'); document.getElementById('srchInput').focus(); }  
function closeSearch() { document.getElementById('searchOv').classList.remove('open'); document.getElementById('srchInput').value = ''; }  
  
function doSearch(q) {  
  const el = document.getElementById('srchRes');  
  if (!q.trim()) { el.innerHTML = `<div class="srch-empty"><p>${t('searchPh')}</p></div>`; return; }  
  const res = S.channels.filter(c => c.name?.toLowerCase().includes(q.toLowerCase()) || c.group?.toLowerCase().includes(q.toLowerCase()));  
  if (!res.length) { el.innerHTML = `<div class="srch-empty"><svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" opacity=".4"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg><p>Aucun résultat pour "${q}"</p></div>`; return; }  
  const tv = res.filter(c => filterByType([c], 'tv').length);  
  const films = res.filter(c => filterByType([c], 'films').length);  
  const series = res.filter(c => filterByType([c], 'series').length);  
  let html = '';  
  const renderGroup = (title, items) => {  
    if (!items.length) return '';  
    return `<div class="srch-section">${title}</div>` + items.slice(0, 8).map(ch => {  
      const idx = S.channels.indexOf(ch);  
      const abbr = (ch.name||'').slice(0,3).toUpperCase();  
      const logo = ch.logo ? `<img src="${ch.logo}" onerror="this.style.display='none';this.nextSibling.style.display='block'"><span class="ch-li-abb" style="display:none">${abbr}</span>` : `<span class="ch-li-abb">${abbr}</span>`;  
      return `<div class="ch-li" onclick="closeSearch();playCh(${idx})">  
        <div class="ch-li-logo">${logo}</div>  
        <div class="ch-li-info">  
          <div class="ch-li-name">${ch.name}</div>  
          <div class="ch-li-epg">${ch.group||''}</div>  
        </div>  
        <div class="fav-btn ${S.favorites.includes(ch.url)?'on':''}" onclick="event.stopPropagation();toggleFav(${idx})">★</div>  
      </div>`;  
    }).join('');  
  };  
  html += renderGroup('📺 Télévision', tv);  
  html += renderGroup('🎬 Films', films);  
  html += renderGroup('🎭 Séries', series);  
  el.innerHTML = html;  
}  
  
// ===================== NAVIGATION =====================  
function setNav(nav) {  
  S.currentNav = nav;  
  document.querySelectorAll('.bni').forEach(n => n.classList.remove('on'));  
  document.getElementById('nav-' + nav)?.classList.add('on');  
  const ms = document.getElementById('mainScroll');  
  const hp = document.getElementById('homePage');  
  const fp = document.getElementById('favsPage');  
  const hsp = document.getElementById('historyPage');  
  const sp = document.getElementById('settingsPage');  
  const tt = document.getElementById('typeTabs');  
  [hp, fp, hsp, sp].forEach(p => p.classList.remove('show'));  
  if (nav === 'home') {  
    ms.style.display = 'block';  
    hp.classList.remove('show'); // Use ms  
    ms.style.paddingTop = '100px';  
    tt.style.display = 'flex';  
    renderHome();  
  } else {  
    ms.style.display = 'none';  
    tt.style.display = 'none';  
    if (nav === 'favs') { fp.classList.add('show'); renderFavs(); }  
    if (nav === 'history') { hsp.classList.add('show'); renderHistory(); }  
    if (nav === 'settings') { sp.classList.add('show'); applyTheme(); }  
  }  
}  
  
// ===================== SETTINGS =====================  
function toggleTheme() {  
  S.settings.theme = S.settings.theme === 'dark' ? 'light' : 'dark';  
  saveLS(); applyTheme();  
}  
  
function setAccent(ac) {  
  S.settings.accent = ac;  
  document.documentElement.setAttribute('data-accent', ac);  
  document.querySelectorAll('.accent-opt').forEach(a => a.classList.toggle('on', a.dataset.ac === ac));  
  saveLS();  
}  
  
function setLang(lang) {  
  S.settings.lang = lang;  
  document.querySelectorAll('.lang-opt').forEach(l => l.classList.toggle('on', l.id === 'lang-' + lang));  
  if (lang === 'ar') document.documentElement.setAttribute('dir', 'rtl');  
  else document.documentElement.removeAttribute('dir');  
  saveLS(); updateLang();  
  toast(lang === 'fr' ? 'Français activé' : lang === 'en' ? 'English activated' : 'تم تفعيل العربية', 'ok');  
}  
  
function renderPlaylists() {  
  const el = document.getElementById('plList');  
  if (!el) return;  
  if (!S.playlists.length) {  
    el.innerHTML = '<div style="padding:16px;font-size:13px;color:var(--text3);text-align:center;">Aucune playlist</div>';  
    return;  
  }  
  el.innerHTML = S.playlists.map((pl, i) => `  
    <div class="pl-item ${i < S.playlists.length - 1 ? '' : ''}">  
      <div class="pl-ico">📡</div>  
      <div class="pl-info">  
        <div class="pl-name">${pl.name}</div>  
        <div class="pl-count">${pl.count} chaînes</div>  
      </div>  
      <div class="pl-btns">  
        <button class="pl-btn" onclick="refreshPl(${i})">🔄</button>  
        <button class="pl-btn del" onclick="delPl(${i})">🗑</button>  
      </div>  
    </div>  
  `).join('');  
}  
  
function refreshPl(i) {  
  const pl = S.playlists[i];  
  if (!pl.url) { toast('Pas d\'URL pour rafraîchir', 'err'); return; }  
  toast('Actualisation...', 'info');  
  fetch(pl.url).then(r => r.text()).then(text => loadM3U(text, pl.name, pl.url))  
    .catch(() => toast(t('loadErr'), 'err'));  
}  
  
function delPl(i) {  
  const pl = S.playlists[i];  
  S.channels = S.channels.filter(c => c.plName !== pl.name);  
  S.playlists.splice(i, 1);  
  saveLS(); renderPlaylists(); renderHome();  
  toast('Playlist supprimée', 'info');  
}  
  
function openAddPlaylist() { document.getElementById('addPlSheet').style.display = 'flex'; }  
function closeAddPl() { document.getElementById('addPlSheet').style.display = 'none'; }  
function closeAddPlOutside(e) { if (e.target === document.getElementById('addPlSheet')) closeAddPl(); }  
  
function addNewPlaylist() {  
  const name = document.getElementById('newPlName').value.trim() || 'Playlist';  
  const url = document.getElementById('newPlUrl').value.trim();  
  if (!url) { toast('Entrez une URL', 'err'); return; }  
  closeAddPl();  
  toast('Chargement...', 'info');  
  fetch(url).then(r => r.text()).then(text => { loadM3U(text, name, url); renderHome(); })  
    .catch(() => toast(t('loadErr') + ' (CORS)', 'err'));  
}  
  
// ===================== TIMER =====================  
function openTimerModal() { document.getElementById('timerModal').classList.add('open'); }  
function closeTimer() { document.getElementById('timerModal').classList.remove('open'); }  
function closeTimerOutside(e) { if (e.target === document.getElementById('timerModal')) closeTimer(); }  
  
function setTimer(min) {  
  clearTimerInterval();  
  S.timerMin = min;  
  document.querySelectorAll('.t-opt').forEach(o => o.classList.remove('on'));  
  if (min === 0) { updateTimerUI(); saveLS(); toast(t('timerOff'), 'info'); closeTimer(); return; }  
  S.timerRemain = min * 60;  
  S.timerInterval = setInterval(() => {  
    S.timerRemain--;  
    updateTimerDisplay();  
    if (S.timerRemain <= 0) {  
      clearTimerInterval();  
      closePlayer();  
      toast('Timer: arrêt automatique ✓', 'ok');  
    }  
  }, 1000);  
  updateTimerUI();  
  toast(t('timerSet') + ' ' + min + ' ' + t('mins'), 'info');  
  closeTimer();  
}  
  
function clearTimerInterval() {  
  if (S.timerInterval) { clearInterval(S.timerInterval); S.timerInterval = null; }  
  S.timerRemain = 0;  
  updateTimerDisplay();  
}  
  
function updateTimerDisplay() {  
  const el = document.getElementById('pvTimerDisp');  
  if (!el) return;  
  if (S.timerRemain > 0) {  
    const m = Math.floor(S.timerRemain / 60), s = S.timerRemain % 60;  
    el.textContent = `⏱ Arrêt dans ${m}:${String(s).padStart(2,'0')}`;  
  } else el.textContent = '';  
}  
  
function updateTimerUI() {  
  const el = document.getElementById('val-timer');  
  if (el) el.textContent = S.timerMin > 0 ? S.timerMin + ' min' : t('disabled');  
}  
  
// ===================== RANDOM / PIP =====================  
function toggleRandom() {  
  S.settings.randomPlay = !S.settings.randomPlay;  
  saveLS(); updateRandomUI();  
  toast(S.settings.randomPlay ? 'Lecture aléatoire activée' : 'Lecture aléatoire désactivée', 'info');  
}  
function updateRandomUI() {  
  const t2 = document.getElementById('randomToggle');  
  const v = document.getElementById('val-random');  
  if (t2) t2.classList.toggle('on', !!S.settings.randomPlay);  
  if (v) v.textContent = t(S.settings.randomPlay ? 'enabled' : 'disabled');  
}  
  
function togglePip() {  
  S.settings.pip = !S.settings.pip;  
  saveLS(); updatePipUI();  
}  
function updatePipUI() {  
  const t2 = document.getElementById('pipToggle');  
  const v = document.getElementById('val-pip');  
  if (t2) t2.classList.toggle('on', !!S.settings.pip);  
  if (v) v.textContent = t(S.settings.pip ? 'enabled' : 'disabled');  
}  
  
// ===================== CREDITS =====================  
function openCredits() {  
  document.getElementById('creditsModal').classList.add('open');  
  document.getElementById('crBalVal').textContent = S.credits;  
  updateCreditHistory();  
}  
function closeCredits() { document.getElementById('creditsModal').classList.remove('open'); }  
function closeCreditsOutside(e) { if (e.target === document.getElementById('creditsModal')) closeCredits(); }  
  
function buyCredits(amount, price) {  
  S.credits += amount;  
  S.creditHistory.unshift({type:'plus', name:`Recharge ${amount} crédits`, amount:`+${amount}`, date: new Date().toLocaleDateString('fr')});  
  if (S.creditHistory.length > 20) S.creditHistory.pop();  
  saveLS(); updateUI();  
  document.getElementById('crBalVal').textContent = S.credits;  
  updateCreditHistory();  
  toast(`💎 ${amount} ${t('creditsBought')}`, 'ok');  
  addNotif('💎', 'Recharge effectuée', `+${amount} crédits ajoutés`);  
}  
  
function updateCreditHistory() {  
  const el = document.getElementById('crHistory');  
  if (!el) return;  
  const all = [  
    ...S.creditHistory,  
    {type:'plus', name:'Crédits de bienvenue', amount:'+500', date:'Offert'},  
  ].slice(0, 10);  
  el.innerHTML = all.map(h => `  
    <div class="cr-hi">  
      <div class="cr-hi-ico ${h.type === 'plus' ? 'cr-hi-plus' : 'cr-hi-minus'}">${h.type === 'plus' ? '↑' : '↓'}</div>  
      <div class="cr-hi-info">  
        <div class="cr-hi-name">${h.name}</div>  
        <div class="cr-hi-date">${h.date}</div>  
      </div>  
      <div class="cr-hi-amount" style="color:${h.type === 'plus' ? '#00c853' : '#e50914'}">${h.amount}</div>  
    </div>  
  `).join('');  
}  
  
// ===================== NOTIFICATIONS =====================  
function addNotif(ico, title, desc) {  
  S.notifications.unshift({ico, title, desc, time:'À l\'instant', read:false});  
  if (S.notifications.length > 30) S.notifications.pop();  
  saveLS(); renderNotifs();  
  // Show notif dot  
  document.getElementById('notifBtn').classList.add('notif-dot');  
}  
  
function openNotifs() {  
  document.getElementById('notifsPanel').classList.add('open');  
  S.notifications = S.notifications.map(n => ({...n, read:true}));  
  saveLS();  
  document.getElementById('notifBtn').classList.remove('notif-dot');  
}  
function closeNotifs() { document.getElementById('notifsPanel').classList.remove('open'); }  
  
function renderNotifs() {  
  const el = document.getElementById('npList');  
  if (!el) return;  
  if (!S.notifications.length) {  
    el.innerHTML = '<div class="empty-big"><h3>Aucune notification</h3><p>Vos notifications apparaîtront ici</p></div>';  
    return;  
  }  
  el.innerHTML = S.notifications.map(n => `  
    <div class="np-item ${n.read ? '' : 'unread'}">  
      <div class="np-ico">${n.ico}</div>  
      <div class="np-info">  
        <div class="np-title">${n.title}</div>  
        <div class="np-desc">${n.desc}</div>  
        <div class="np-time">${n.time}</div>  
      </div>  
    </div>  
  `).join('');  
}  
  
// ===================== MISC =====================  
function clearAll() {  
  if (!confirm('Réinitialiser l\'application ?')) return;  
  localStorage.removeItem('ldetpp_v2');  
  location.reload();  
}  
  
function toast(msg, type = '') {  
  const el = document.getElementById('toast');  
  el.textContent = msg;  
  el.className = 'toast show' + (type ? ' ' + type : '');  
  setTimeout(() => el.className = 'toast', 3000);  
}  
  
// Keyboard  
document.addEventListener('keydown', e => {  
  if (['INPUT','TEXTAREA'].includes(e.target.tagName)) return;  
  if (e.key === ' ') { e.preventDefault(); togglePlay(); }  
  if (e.key === 'Escape') { closePlayer(); closeSearch(); closeCredits(); closeNotifs(); }  
  if (e.key === 'ArrowLeft') prevCh();  
  if (e.key === 'ArrowRight') nextCh();  
  if (e.key === 'f') toggleFullscreen();  
  if (e.key === 'm') toggleMute();  
});  
  
// Init nav  
document.addEventListener('DOMContentLoaded', () => {  
  // Will be triggered after splash  
});  
</script>  
  
</body>  
</html>  
