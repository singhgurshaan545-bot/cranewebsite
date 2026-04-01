# cranewebsite
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HeavyLift Pro – Reliable Crane Rental Services</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
/* ═══════════ VARIABLES ═══════════ */
:root{
  --y:#FFD000;--yd:#E6B800;--y2:rgba(255,208,0,.15);
  --blk:#080808;--d:#111;--d2:#181818;--d3:#222;--d4:#2a2a2a;
  --g:#777;--g2:#999;--w:#FFF;--wa:#25D366;--red:#FF4444;
}

/* ═══════════ RESET ═══════════ */
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{font-family:'Barlow',sans-serif;background:var(--d);color:var(--w);overflow-x:hidden;}
img{display:block;width:100%;object-fit:cover;}
a{text-decoration:none;color:inherit;}
.page{display:none;min-height:100vh;}
.page.active{display:block;}

/* ═══════════ LOADER ═══════════ */
#loader{position:fixed;inset:0;background:var(--blk);z-index:9999;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:1rem;transition:opacity .6s,visibility .6s;}
#loader.gone{opacity:0;visibility:hidden;}
.loader-icon{font-size:3rem;color:var(--y);animation:loadSpin 1.2s linear infinite;}
@keyframes loadSpin{to{transform:rotate(360deg);}}
.loader-bar{width:200px;height:3px;background:var(--d3);border-radius:2px;overflow:hidden;}
.loader-fill{height:100%;background:var(--y);border-radius:2px;animation:loadFill 1.5s ease-out forwards;}
@keyframes loadFill{from{width:0}to{width:100%}}
.loader-txt{font-family:'Barlow Condensed',sans-serif;font-size:1.1rem;font-weight:700;letter-spacing:3px;text-transform:uppercase;color:var(--g);}

/* ═══════════ NAVBAR ═══════════ */
nav{
  position:fixed;top:0;left:0;right:0;z-index:1000;
  padding:0 3rem;height:72px;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(8,8,8,0);backdrop-filter:blur(0);
  border-bottom:1px solid rgba(255,208,0,0);
  transition:all .5s ease;
}
nav.solid{background:rgba(8,8,8,.97);backdrop-filter:blur(20px);border-bottom-color:rgba(255,208,0,.4);}
.logo{font-family:'Barlow Condensed',sans-serif;font-size:1.7rem;font-weight:900;text-transform:uppercase;letter-spacing:2px;cursor:pointer;display:flex;align-items:center;gap:10px;color:var(--w);}
.logo span{color:var(--y);}
.logo-icon{width:38px;height:38px;background:var(--y);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:1.1rem;color:var(--blk);transition:transform .5s;}
.logo:hover .logo-icon{transform:rotate(20deg) scale(1.1);}
.nav-links{display:flex;align-items:center;gap:2.5rem;list-style:none;}
.nav-links a{color:rgba(255,255,255,.75);font-size:.85rem;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;cursor:pointer;transition:color .3s;position:relative;padding:4px 0;}
.nav-links a::after{content:'';position:absolute;bottom:0;left:0;width:0;height:2px;background:var(--y);transition:width .35s cubic-bezier(.4,0,.2,1);}
.nav-links a:hover,.nav-links a.on{color:var(--y);}
.nav-links a:hover::after,.nav-links a.on::after{width:100%;}
.nav-wa{display:flex;align-items:center;gap:8px;background:var(--wa);color:#fff;padding:9px 22px;border-radius:50px;font-weight:700;font-size:.82rem;letter-spacing:1px;text-transform:uppercase;transition:all .35s;}
.nav-wa:hover{background:#1da851;transform:translateY(-2px);box-shadow:0 8px 25px rgba(37,211,102,.4);}
.hamburger{display:none;flex-direction:column;gap:5px;cursor:pointer;padding:6px;}
.hamburger span{width:24px;height:2px;background:var(--y);display:block;transition:all .35s;}
.hamburger.open span:nth-child(1){transform:translateY(7px) rotate(45deg);}
.hamburger.open span:nth-child(2){opacity:0;}
.hamburger.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg);}
.mob-nav{display:none;position:fixed;top:72px;left:0;right:0;z-index:999;background:rgba(8,8,8,.98);padding:2rem;border-bottom:1px solid var(--d3);flex-direction:column;gap:1.2rem;}
.mob-nav.open{display:flex;}
.mob-nav a{color:var(--g2);font-size:1rem;font-weight:600;text-transform:uppercase;letter-spacing:1.5px;cursor:pointer;padding:.5rem 0;border-bottom:1px solid var(--d3);transition:color .3s;}
.mob-nav a:hover{color:var(--y);}

/* ═══════════ FLOATING WA ═══════════ */
.waf{position:fixed;bottom:28px;right:28px;z-index:9000;width:58px;height:58px;background:var(--wa);border-radius:50%;display:flex;align-items:center;justify-content:center;box-shadow:0 4px 20px rgba(37,211,102,.4);transition:all .35s;animation:waPulse 2.5s infinite;}
.waf i{color:#fff;font-size:1.7rem;}
.waf:hover{transform:scale(1.15) rotate(10deg);box-shadow:0 8px 35px rgba(37,211,102,.6);}
@keyframes waPulse{0%,100%{box-shadow:0 0 0 0 rgba(37,211,102,.6);}60%{box-shadow:0 0 0 14px rgba(37,211,102,0);}}

/* ═══════════ BUTTONS ═══════════ */
.btn{display:inline-flex;align-items:center;gap:10px;padding:14px 32px;border:none;border-radius:6px;font-family:'Barlow Condensed',sans-serif;font-size:1.05rem;font-weight:800;letter-spacing:2px;text-transform:uppercase;cursor:pointer;transition:all .35s;position:relative;overflow:hidden;}
.btn::before{content:'';position:absolute;inset:0;background:rgba(255,255,255,.12);transform:translateX(-110%) skewX(-20deg);transition:transform .5s ease;}
.btn:hover::before{transform:translateX(110%) skewX(-20deg);}
.btn-y{background:var(--y);color:var(--blk);}
.btn-y:hover{background:var(--yd);transform:translateY(-3px);box-shadow:0 12px 35px rgba(255,208,0,.45);}
.btn-outline{background:transparent;color:var(--w);border:2px solid rgba(255,255,255,.3);}
.btn-outline:hover{border-color:var(--y);color:var(--y);transform:translateY(-3px);}
.btn-wa{background:var(--wa);color:#fff;}
.btn-wa:hover{background:#1da851;transform:translateY(-3px);box-shadow:0 12px 35px rgba(37,211,102,.45);}
.btn-dark{background:var(--d2);color:var(--w);border:1px solid var(--d4);}
.btn-dark:hover{border-color:var(--y);color:var(--y);transform:translateY(-2px);}

/* ═══════════ TOAST ═══════════ */
.toast{position:fixed;top:84px;right:20px;z-index:9001;background:var(--d2);border:1px solid var(--y);border-radius:10px;padding:1rem 1.5rem;display:flex;align-items:center;gap:12px;box-shadow:0 15px 50px rgba(0,0,0,.6);transform:translateX(130%);transition:transform .5s cubic-bezier(.34,1.56,.64,1);min-width:280px;}
.toast.show{transform:translateX(0);}
.toast i{font-size:1.2rem;color:var(--y);}
.toast span{font-size:.95rem;font-weight:600;}

/* ═══════════ LIGHTBOX ═══════════ */
.lb{display:none;position:fixed;inset:0;z-index:8000;background:rgba(0,0,0,.95);align-items:center;justify-content:center;animation:lbIn .3s ease;}
.lb.open{display:flex;}
@keyframes lbIn{from{opacity:0;}to{opacity:1;}}
.lb-inner{position:relative;max-width:88vw;max-height:85vh;}
.lb-inner img{max-width:100%;max-height:85vh;object-fit:contain;border-radius:6px;transition:opacity .25s;}
.lb-x{position:absolute;top:-18px;right:-18px;width:40px;height:40px;background:var(--y);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;color:var(--blk);cursor:pointer;transition:transform .3s;}
.lb-x:hover{transform:rotate(90deg) scale(1.1);}
.lb-arr{position:absolute;top:50%;transform:translateY(-50%);width:44px;height:44px;background:rgba(255,208,0,.85);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;color:var(--blk);cursor:pointer;transition:all .3s;z-index:1;}
.lb-arr:hover{background:var(--y);}
.lb-prev{left:-58px;}
.lb-next{right:-58px;}
.lb-cap{text-align:center;margin-top:1rem;font-family:'Barlow Condensed',sans-serif;font-size:1.1rem;font-weight:700;text-transform:uppercase;letter-spacing:2px;color:var(--y);}

/* ═══════════ SCROLL ANIMATIONS ═══════════ */
.reveal{opacity:0;transform:translateY(55px);transition:opacity .9s cubic-bezier(.4,0,.2,1),transform .9s cubic-bezier(.4,0,.2,1);}
.reveal.in{opacity:1;transform:translateY(0);}
.reveal-l{opacity:0;transform:translateX(-70px);transition:opacity .85s cubic-bezier(.4,0,.2,1),transform .85s cubic-bezier(.4,0,.2,1);}
.reveal-l.in{opacity:1;transform:translateX(0);}
.reveal-r{opacity:0;transform:translateX(70px);transition:opacity .85s cubic-bezier(.4,0,.2,1),transform .85s cubic-bezier(.4,0,.2,1);}
.reveal-r.in{opacity:1;transform:translateX(0);}
.reveal-s{opacity:0;transform:scale(.88);transition:opacity .8s ease,transform .8s ease;}
.reveal-s.in{opacity:1;transform:scale(1);}
.cascade>*{opacity:0;transform:translateY(40px);transition:opacity .7s ease,transform .7s ease;}
.cascade.in>*:nth-child(1){opacity:1;transform:none;transition-delay:.05s;}
.cascade.in>*:nth-child(2){opacity:1;transform:none;transition-delay:.14s;}
.cascade.in>*:nth-child(3){opacity:1;transform:none;transition-delay:.23s;}
.cascade.in>*:nth-child(4){opacity:1;transform:none;transition-delay:.32s;}
.cascade.in>*:nth-child(5){opacity:1;transform:none;transition-delay:.41s;}
.cascade.in>*:nth-child(6){opacity:1;transform:none;transition-delay:.50s;}

/* ═══════════ SECTIONS ═══════════ */
.sec{padding:100px 5rem;}
.sec-sm{padding:60px 5rem;}
.sh{text-align:center;margin-bottom:4rem;}
.stag{display:inline-flex;align-items:center;gap:8px;background:var(--y2);border:1px solid rgba(255,208,0,.4);color:var(--y);padding:5px 18px;border-radius:50px;font-size:.7rem;font-weight:700;letter-spacing:3px;text-transform:uppercase;margin-bottom:1.2rem;}
.stag::before{content:'';width:6px;height:6px;border-radius:50%;background:var(--y);flex-shrink:0;}
.sh h2{font-family:'Barlow Condensed',sans-serif;font-size:clamp(2.4rem,5vw,4rem);font-weight:900;text-transform:uppercase;line-height:.95;}
.sh h2 span{color:var(--y);}
.sh p{color:var(--g2);margin-top:1rem;font-size:1.05rem;max-width:580px;margin-left:auto;margin-right:auto;line-height:1.75;}
.ydiv{width:60px;height:4px;background:linear-gradient(90deg,var(--y),var(--yd));border-radius:2px;margin:1.2rem auto 0;}

/* ═══════════ HERO ═══════════ */
.hero{min-height:100vh;position:relative;overflow:hidden;display:flex;align-items:center;}
#heroCanvas{position:absolute;inset:0;z-index:1;}
.hero-bg{position:absolute;inset:0;z-index:0;}
.hslide{position:absolute;inset:0;background-size:cover;background-position:center;opacity:0;transition:opacity 1.6s ease;transform:scale(1.05);transition:opacity 1.6s ease,transform 6s ease;}
.hslide.on{opacity:1;transform:scale(1);}
.hero-ov{position:absolute;inset:0;z-index:2;background:linear-gradient(105deg,rgba(8,8,8,.96) 38%,rgba(8,8,8,.2) 100%);}
.hero-cnt{position:relative;z-index:3;padding:0 5rem;max-width:800px;padding-top:72px;}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:var(--y2);border:1px solid rgba(255,208,0,.4);padding:6px 18px;border-radius:50px;margin-bottom:2rem;font-size:.7rem;font-weight:700;letter-spacing:3px;text-transform:uppercase;color:var(--y);opacity:0;animation:heroUp .7s .3s forwards;}
.hero-badge i{font-size:.8rem;}
.hero h1{font-family:'Barlow Condensed',sans-serif;font-size:clamp(3.5rem,9vw,6.5rem);font-weight:900;line-height:.9;text-transform:uppercase;opacity:0;animation:heroUp .8s .5s forwards;}
.hero h1 em{color:var(--y);font-style:normal;display:block;}
.hero-sub{font-size:1.15rem;color:rgba(255,255,255,.7);margin:2rem 0 3rem;max-width:520px;line-height:1.8;opacity:0;animation:heroUp .7s .7s forwards;}
.hero-btns{display:flex;gap:1rem;flex-wrap:wrap;opacity:0;animation:heroUp .7s .9s forwards;}
@keyframes heroUp{from{opacity:0;transform:translateY(35px);}to{opacity:1;transform:translateY(0);}}
.hero-dots{position:absolute;bottom:100px;left:5rem;z-index:4;display:flex;gap:12px;}
.hdot{width:8px;height:8px;border-radius:50%;background:rgba(255,255,255,.25);cursor:pointer;transition:all .4s;}
.hdot.on{background:var(--y);width:30px;border-radius:4px;}
.hero-scroll{position:absolute;bottom:30px;left:50%;transform:translateX(-50%);z-index:4;display:flex;flex-direction:column;align-items:center;gap:8px;opacity:0;animation:heroUp .6s 1.4s forwards;}
.hero-scroll span{font-size:.65rem;letter-spacing:3px;text-transform:uppercase;color:var(--g);}
.scroll-arrow{width:30px;height:30px;border:1px solid rgba(255,255,255,.2);border-radius:50%;display:flex;align-items:center;justify-content:center;animation:scrollBounce 1.8s ease-in-out infinite;}
@keyframes scrollBounce{0%,100%{transform:translateY(0);}50%{transform:translateY(8px);}}
.scroll-arrow i{font-size:.7rem;color:var(--y);}

/* Hero stats bar */
.hero-stats{position:absolute;bottom:0;right:0;z-index:4;display:flex;opacity:0;animation:heroUp .8s 1.1s forwards;}
.hstat{padding:2rem 2.5rem;text-align:center;min-width:160px;}
.hstat:nth-child(1){background:var(--y);}
.hstat:nth-child(2){background:var(--blk);}
.hstat:nth-child(3){background:var(--d3);}
.hstat-num{font-family:'Barlow Condensed',sans-serif;font-size:2.6rem;font-weight:900;display:block;line-height:1;}
.hstat:nth-child(1) .hstat-num{color:var(--blk);}
.hstat:nth-child(2) .hstat-num,.hstat:nth-child(3) .hstat-num{color:var(--y);}
.hstat-lbl{font-size:.65rem;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;margin-top:4px;display:block;}
.hstat:nth-child(1) .hstat-lbl{color:rgba(0,0,0,.55);}
.hstat:nth-child(2) .hstat-lbl,.hstat:nth-child(3) .hstat-lbl{color:var(--g);}

/* ═══════════ MARQUEE ═══════════ */
.mqw{overflow:hidden;background:var(--blk);border-top:1px solid var(--d3);border-bottom:1px solid var(--d3);padding:4px 0;}
.mqt{display:flex;gap:4px;animation:mq 40s linear infinite;}
.mqt:hover{animation-play-state:paused;}
.mqimg{width:260px;height:160px;flex-shrink:0;filter:grayscale(50%) brightness(.7);transition:filter .5s;}
.mqimg:hover{filter:grayscale(0%) brightness(1);}
@keyframes mq{from{transform:translateX(0);}to{transform:translateX(-50%);}}

/* ═══════════ WHY US ═══════════ */
.why-sec{background:var(--d2);}
.why-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--d3);}
.wcard{background:var(--d2);padding:3rem 2rem;text-align:center;transition:all .45s;position:relative;overflow:hidden;cursor:default;}
.wcard::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(255,208,0,.04),transparent);opacity:0;transition:opacity .4s;}
.wcard::after{content:'';position:absolute;bottom:0;left:0;width:0;height:3px;background:var(--y);transition:width .6s cubic-bezier(.4,0,.2,1);}
.wcard:hover::before{opacity:1;}
.wcard:hover::after{width:100%;}
.wcard:hover{background:var(--d3);transform:translateY(-8px);}
.wico{width:78px;height:78px;border-radius:50%;border:2px solid rgba(255,208,0,.3);background:rgba(255,208,0,.06);display:flex;align-items:center;justify-content:center;margin:0 auto 1.5rem;font-size:1.9rem;color:var(--y);transition:all .5s cubic-bezier(.4,0,.2,1);}
.wcard:hover .wico{background:var(--y);color:var(--blk);border-color:var(--y);transform:rotateY(360deg) scale(1.1);}
.wcard h3{font-family:'Barlow Condensed',sans-serif;font-size:1.4rem;font-weight:800;text-transform:uppercase;letter-spacing:.5px;margin-bottom:.6rem;}
.wcard p{color:var(--g);font-size:.92rem;line-height:1.65;}

/* ═══════════ SERVICES ═══════════ */
.svc-sec{background:var(--d);}
.svc-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:2rem;}
.svc{background:var(--d2);border:1px solid var(--d3);border-radius:12px;overflow:hidden;transition:all .5s cubic-bezier(.4,0,.2,1);position:relative;}
.svc::before{content:'';position:absolute;inset:0;border-radius:12px;border:2px solid var(--y);opacity:0;transition:opacity .4s;z-index:1;pointer-events:none;}
.svc:hover::before{opacity:1;}
.svc:hover{transform:translateY(-12px) scale(1.01);box-shadow:0 30px 80px rgba(0,0,0,.5),0 0 40px rgba(255,208,0,.08);}
.svc-img{height:240px;overflow:hidden;position:relative;}
.svc-img img{height:100%;transition:transform .7s ease;}
.svc:hover .svc-img img{transform:scale(1.12);}
.svc-chip{position:absolute;bottom:14px;left:14px;background:var(--y);color:var(--blk);font-family:'Barlow Condensed',sans-serif;font-size:.72rem;font-weight:800;letter-spacing:1px;text-transform:uppercase;padding:5px 12px;border-radius:4px;z-index:2;}
.svc-body{padding:2rem;}
.svc-ico{width:50px;height:50px;background:var(--y);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.3rem;color:var(--blk);margin-bottom:1.1rem;transition:transform .5s ease;}
.svc:hover .svc-ico{transform:rotate(15deg) scale(1.1);}
.svc-body h3{font-family:'Barlow Condensed',sans-serif;font-size:1.7rem;font-weight:900;text-transform:uppercase;margin-bottom:.7rem;}
.svc-body p{color:var(--g2);line-height:1.75;font-size:.95rem;}

/* ═══════════ GALLERY ═══════════ */
.gal-sec{background:var(--d2);}
.gal-tabs{display:flex;gap:.6rem;justify-content:center;margin-bottom:3rem;flex-wrap:wrap;}
.gtab{background:var(--d3);border:1px solid var(--d4);color:var(--g);padding:8px 22px;border-radius:50px;font-family:'Barlow Condensed',sans-serif;font-size:.95rem;font-weight:700;text-transform:uppercase;letter-spacing:1px;cursor:pointer;transition:all .35s;}
.gtab:hover{border-color:rgba(255,208,0,.4);color:var(--g2);}
.gtab.on{background:var(--y);color:var(--blk);border-color:var(--y);}
.gal-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px;}
.gi{position:relative;overflow:hidden;aspect-ratio:4/3;cursor:pointer;border-radius:4px;}
.gi img{width:100%;height:100%;transition:transform .65s ease,filter .4s;}
.gi:hover img{transform:scale(1.14);filter:brightness(1.1);}
.gi-ov{position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.9) 0%,rgba(0,0,0,.2) 50%,transparent 100%);opacity:0;transition:opacity .4s;display:flex;flex-direction:column;justify-content:flex-end;padding:1.2rem;}
.gi:hover .gi-ov{opacity:1;}
.gi-lbl{font-family:'Barlow Condensed',sans-serif;font-size:1rem;font-weight:800;text-transform:uppercase;letter-spacing:1px;color:var(--y);}
.gi-sub{font-size:.78rem;color:rgba(255,255,255,.6);margin-top:2px;}
.gi-zoom{position:absolute;top:12px;right:12px;width:34px;height:34px;background:rgba(255,208,0,.9);border-radius:50%;display:flex;align-items:center;justify-content:center;color:var(--blk);font-size:.85rem;opacity:0;transform:scale(.6) rotate(-45deg);transition:all .35s;}
.gi:hover .gi-zoom{opacity:1;transform:scale(1) rotate(0deg);}
.gi.wide{grid-column:span 2;}
.gi.tall{grid-row:span 2;aspect-ratio:auto;}
.gi.tall img{height:100%;width:100%;object-fit:cover;}

/* ═══════════ ABOUT ═══════════ */
.about-sec{background:var(--d);}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:6rem;align-items:center;}
.about-imgw{position:relative;}
.about-main-img{height:560px;border-radius:12px;overflow:hidden;}
.about-main-img img{height:100%;transition:transform .7s ease;}
.about-imgw:hover .about-main-img img{transform:scale(1.04);}
.about-float-img{position:absolute;bottom:-30px;right:-30px;width:55%;border-radius:10px;overflow:hidden;border:4px solid var(--d);box-shadow:0 20px 60px rgba(0,0,0,.6);transition:transform .4s ease;}
.about-float-img:hover{transform:scale(1.03) translateY(-5px);}
.about-float-img img{height:180px;}
.about-badge{position:absolute;top:30px;right:-20px;background:var(--y);color:var(--blk);padding:1.5rem;text-align:center;border-radius:10px;box-shadow:0 12px 35px rgba(255,208,0,.4);animation:floatAnim 4s ease-in-out infinite;z-index:2;}
@keyframes floatAnim{0%,100%{transform:translateY(0);}50%{transform:translateY(-14px);}}
.about-badge .abn{font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900;line-height:1;}
.about-badge .abl{font-size:.72rem;font-weight:700;letter-spacing:1px;text-transform:uppercase;opacity:.75;}
.about-content h2{font-family:'Barlow Condensed',sans-serif;font-size:3.5rem;font-weight:900;text-transform:uppercase;line-height:1;margin-bottom:1.5rem;}
.about-content h2 span{color:var(--y);}
.about-content p{color:var(--g2);line-height:1.85;margin-bottom:1rem;}
.afeats{margin-top:1.5rem;display:flex;flex-direction:column;gap:.8rem;}
.afeat{display:flex;align-items:center;gap:14px;padding:.7rem 0;border-bottom:1px solid var(--d3);transition:transform .35s;}
.afeat:hover{transform:translateX(10px);}
.afeat i{color:var(--y);font-size:1rem;flex-shrink:0;}
.afeat span{font-weight:600;font-size:.95rem;}

/* ═══════════ TESTIMONIALS ═══════════ */
.test-sec{background:var(--d2);}
.test-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:2rem;}
.tc{background:var(--d);border:1px solid var(--d3);border-radius:12px;padding:2.2rem;transition:all .45s;position:relative;overflow:hidden;}
.tc::before{content:'"';font-family:'Barlow Condensed',sans-serif;font-size:7rem;color:var(--y);opacity:.07;position:absolute;top:-20px;left:16px;line-height:1;pointer-events:none;}
.tc:hover{border-color:rgba(255,208,0,.5);transform:translateY(-8px);box-shadow:0 25px 60px rgba(0,0,0,.4),0 0 0 1px rgba(255,208,0,.15);}
.tc-stars{color:var(--y);margin-bottom:1rem;font-size:.95rem;letter-spacing:3px;}
.tc p{color:#bbb;line-height:1.8;margin-bottom:1.5rem;font-style:italic;}
.tc-auth{display:flex;align-items:center;gap:14px;}
.tc-av{width:50px;height:50px;border-radius:50%;background:var(--y);display:flex;align-items:center;justify-content:center;font-family:'Barlow Condensed',sans-serif;font-size:1.2rem;font-weight:900;color:var(--blk);flex-shrink:0;}
.tc-name{font-weight:700;font-size:.95rem;}
.tc-role{color:var(--g);font-size:.8rem;margin-top:2px;}

/* ═══════════ COUNTERS ═══════════ */
.ctr-sec{background:var(--blk);border-top:1px solid var(--d3);border-bottom:1px solid var(--d3);padding:80px 5rem;}
.ctr-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:2px;background:var(--d3);}
.cb{background:var(--blk);padding:2.5rem;text-align:center;transition:background .4s;position:relative;overflow:hidden;}
.cb::after{content:'';position:absolute;bottom:0;left:0;width:0;height:2px;background:var(--y);transition:width .5s;}
.cb:hover{background:var(--d2);}
.cb:hover::after{width:100%;}
.cb-num{font-family:'Barlow Condensed',sans-serif;font-size:4.5rem;font-weight:900;color:var(--y);line-height:1;display:flex;align-items:baseline;justify-content:center;gap:2px;}
.cb-lbl{color:var(--g);font-size:.75rem;font-weight:700;letter-spacing:2.5px;text-transform:uppercase;margin-top:.5rem;}

/* ═══════════ CTA STRIPE ═══════════ */
.cta-s{background:var(--d3);border-top:1px solid var(--d4);border-bottom:1px solid var(--d4);padding:55px 5rem;display:flex;align-items:center;justify-content:space-between;position:relative;overflow:hidden;}
.cta-s::before{content:'';position:absolute;left:-80px;top:-80px;width:320px;height:320px;border-radius:50%;background:radial-gradient(circle,rgba(255,208,0,.05),transparent 70%);pointer-events:none;}
.cta-s h3{font-family:'Barlow Condensed',sans-serif;font-size:2.5rem;font-weight:900;text-transform:uppercase;}
.cta-s h3 span{color:var(--y);}
.cta-s p{color:var(--g);margin-top:4px;}
.cta-btns{display:flex;gap:1rem;flex-wrap:wrap;}

/* ═══════════ CONTACT ═══════════ */
.cont-sec{background:var(--d2);}
.cont-grid{display:grid;grid-template-columns:1fr 1fr;gap:4rem;}
.cform{background:var(--d);border:1px solid var(--d3);border-radius:12px;padding:2.8rem;}
.cform h3{font-family:'Barlow Condensed',sans-serif;font-size:2.2rem;font-weight:900;text-transform:uppercase;margin-bottom:1.5rem;}
.cform h3 span{color:var(--y);}
.fg{margin-bottom:1.2rem;}
.fg label{display:block;font-size:.75rem;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--g);margin-bottom:7px;}
.fg input,.fg textarea,.fg select{width:100%;background:var(--d2);border:1px solid var(--d3);border-radius:8px;padding:13px 16px;color:var(--w);font-family:'Barlow',sans-serif;font-size:.95rem;transition:all .35s;outline:none;appearance:none;}
.fg input:focus,.fg textarea:focus,.fg select:focus{border-color:var(--y);box-shadow:0 0 0 3px rgba(255,208,0,.1);}
.fg textarea{resize:vertical;min-height:120px;}
.fg select option{background:var(--d2);}
.cinfo h3{font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900;text-transform:uppercase;line-height:1;margin-bottom:1rem;}
.cinfo h3 span{color:var(--y);}
.cinfo>p{color:var(--g2);line-height:1.8;margin-bottom:2rem;}
.icards{display:flex;flex-direction:column;gap:.9rem;margin-bottom:2.5rem;}
.icard{display:flex;align-items:center;gap:1.1rem;background:var(--d);border:1px solid var(--d3);border-radius:10px;padding:1.3rem;transition:all .35s;}
.icard:hover{border-color:rgba(255,208,0,.5);transform:translateX(8px);}
.iico{width:48px;height:48px;background:rgba(255,208,0,.08);border:1px solid rgba(255,208,0,.3);border-radius:10px;display:flex;align-items:center;justify-content:center;color:var(--y);font-size:1.1rem;flex-shrink:0;transition:all .4s;}
.icard:hover .iico{background:var(--y);color:var(--blk);}
.icard h4{font-size:.72rem;color:var(--g);text-transform:uppercase;letter-spacing:1.5px;margin-bottom:3px;}
.icard p{font-weight:600;font-size:.93rem;}

/* ═══════════ AUTH ═══════════ */
.auth-pg{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:100px 2rem 2rem;background:radial-gradient(ellipse at 20% 20%,#1a1200 0%,var(--d) 55%);}
.auth-box{background:var(--d2);border:1px solid var(--d3);border-radius:16px;padding:3.2rem;width:100%;max-width:480px;position:relative;overflow:hidden;animation:authIn .6s cubic-bezier(.34,1.56,.64,1);}
@keyframes authIn{from{opacity:0;transform:translateY(40px) scale(.95);}to{opacity:1;transform:translateY(0) scale(1);}}
.auth-box::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;background:linear-gradient(90deg,var(--y),var(--yd),var(--y));}
.auth-icon{text-align:center;margin-bottom:2rem;}
.auth-icon i{font-size:3rem;color:var(--y);display:block;}
.auth-box h2{font-family:'Barlow Condensed',sans-serif;font-size:2.6rem;font-weight:900;text-transform:uppercase;margin-bottom:.4rem;}
.auth-box h2 span{color:var(--y);}
.auth-sub{color:var(--g);margin-bottom:2rem;font-size:.95rem;line-height:1.6;}
.auth-lnk{color:var(--y);cursor:pointer;font-weight:700;text-decoration:underline;}
.adiv{text-align:center;color:var(--g);margin:1.2rem 0;font-size:.85rem;position:relative;}
.adiv::before,.adiv::after{content:'';position:absolute;top:50%;width:40%;height:1px;background:var(--d3);}
.adiv::before{left:0;}.adiv::after{right:0;}
.demo-hint{text-align:center;margin-top:.8rem;color:var(--g);font-size:.78rem;background:var(--d3);border-radius:6px;padding:.5rem;border:1px solid var(--d4);}

/* ═══════════ DASHBOARD ═══════════ */
.dash-pg{padding-top:72px;background:var(--d);min-height:100vh;}
.dash-hero{background:linear-gradient(135deg,var(--d2),#0e0900);border-bottom:2px solid rgba(255,208,0,.3);padding:3.5rem 5rem;position:relative;overflow:hidden;}
.dash-hero::before{content:'';position:absolute;right:0;top:0;bottom:0;width:50%;background:url('https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=800&q=60') center/cover;opacity:.06;}
.dash-hero h1{font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900;text-transform:uppercase;}
.dash-hero h1 span{color:var(--y);}
.dash-hero p{color:var(--g);margin-top:.5rem;}
.dash-body{padding:3rem 5rem;}
.dash-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:1.5rem;margin-bottom:3rem;}
.dc{background:var(--d2);border:1px solid var(--d3);border-radius:12px;padding:2.2rem;text-align:center;transition:all .4s;cursor:pointer;position:relative;overflow:hidden;}
.dc::after{content:'';position:absolute;bottom:0;left:0;width:0;height:3px;background:var(--y);transition:width .5s;}
.dc:hover::after{width:100%;}
.dc:hover{border-color:rgba(255,208,0,.4);transform:translateY(-6px);box-shadow:0 20px 50px rgba(0,0,0,.4);}
.dc i{font-size:2.8rem;color:var(--y);margin-bottom:1.2rem;display:block;transition:transform .4s;}
.dc:hover i{transform:scale(1.15) rotate(-5deg);}
.dc h3{font-family:'Barlow Condensed',sans-serif;font-size:1.4rem;font-weight:800;text-transform:uppercase;}
.dc p{color:var(--g);font-size:.87rem;margin-top:.5rem;}

/* ═══════════ FOOTER ═══════════ */
footer{background:var(--blk);border-top:1px solid var(--d3);padding:80px 5rem 35px;}
.fg-grid{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:3.5rem;margin-bottom:3.5rem;}
.fb h3{font-family:'Barlow Condensed',sans-serif;font-size:2rem;font-weight:900;text-transform:uppercase;margin-bottom:1rem;}
.fb h3 span{color:var(--y);}
.fb p{color:var(--g);line-height:1.8;font-size:.9rem;margin-bottom:1.5rem;}
.socs{display:flex;gap:.7rem;}
.soc{width:38px;height:38px;border-radius:50%;background:var(--d3);border:1px solid var(--d4);display:flex;align-items:center;justify-content:center;color:var(--g);transition:all .35s;cursor:pointer;}
.soc:hover{background:var(--y);color:var(--blk);border-color:var(--y);transform:translateY(-4px);}
.fc h4{font-family:'Barlow Condensed',sans-serif;font-size:1.05rem;font-weight:800;text-transform:uppercase;letter-spacing:1px;color:var(--w);margin-bottom:1.2rem;padding-bottom:.5rem;border-bottom:2px solid var(--y);display:inline-block;}
.fl{list-style:none;display:flex;flex-direction:column;gap:.65rem;}
.fl a{color:var(--g);text-decoration:none;font-size:.9rem;transition:all .3s;cursor:pointer;display:flex;align-items:center;gap:7px;}
.fl a i{font-size:.6rem;transition:transform .3s;}
.fl a:hover{color:var(--y);padding-left:4px;}
.fl a:hover i{transform:translateX(3px);}
.fbot{border-top:1px solid var(--d3);padding-top:1.5rem;display:flex;justify-content:space-between;align-items:center;color:var(--g);font-size:.85rem;flex-wrap:wrap;gap:.5rem;}
.fbot span{color:var(--y);}

/* ═══════════ PAGE HEADER ═══════════ */
.pghdr{background:linear-gradient(135deg,var(--d2),#0e0900);padding:100px 5rem 75px;border-bottom:2px solid rgba(255,208,0,.25);position:relative;overflow:hidden;}
.pghdr::after{content:'';position:absolute;right:0;top:0;bottom:0;width:45%;background:url('https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=900&q=60') center/cover;opacity:.06;}
.pghdr h1{font-family:'Barlow Condensed',sans-serif;font-size:clamp(3rem,7vw,5rem);font-weight:900;text-transform:uppercase;margin-top:.8rem;position:relative;z-index:1;}
.pghdr h1 span{color:var(--y);}

/* ═══════════ PAGE TRANSITION ═══════════ */
.pg-enter{animation:pgIn .5s cubic-bezier(.4,0,.2,1);}
@keyframes pgIn{from{opacity:0;transform:translateY(25px);}to{opacity:1;transform:translateY(0);}}

/* ═══════════ RESPONSIVE ═══════════ */
@media(max-width:1100px){
  .sec,.sec-sm,.ctr-sec,.cta-s,.dash-hero,.dash-body,.pghdr,footer{padding-left:2.5rem;padding-right:2.5rem;}
  .hero-cnt,.hero-dots{padding-left:2.5rem;left:2.5rem;}
  .svc-grid{grid-template-columns:1fr 1fr;}
  .gal-grid{grid-template-columns:repeat(3,1fr);}
  .about-grid{grid-template-columns:1fr;}
  .cont-grid{grid-template-columns:1fr;}
  .fg-grid{grid-template-columns:1fr 1fr;}
  .why-grid{grid-template-columns:1fr 1fr;}
  .about-float-img{right:0;bottom:-20px;}
}
@media(max-width:768px){
  .nav-links{display:none;}
  .hamburger{display:flex;}
  .nav-wa{display:none;}
  .hero-cnt{padding:0 1.5rem;padding-top:80px;}
  .hero h1{font-size:3rem;}
  .hero-dots{left:1.5rem;bottom:80px;}
  .hero-stats{position:relative;display:grid;grid-template-columns:1fr 1fr 1fr;width:100%;}
  .hstat{min-width:auto;}
  .svc-grid,.test-grid{grid-template-columns:1fr;}
  .gal-grid{grid-template-columns:1fr 1fr;}
  .gi.wide,.gi.tall{grid-column:span 1;grid-row:span 1;aspect-ratio:4/3;}
  .ctr-grid{grid-template-columns:1fr 1fr;}
  .cta-s{flex-direction:column;gap:1.5rem;text-align:center;}
  .dash-cards{grid-template-columns:1fr 1fr;}
  .sec,.sec-sm,.ctr-sec,.cta-s,.dash-hero,.dash-body,.pghdr,footer{padding-left:1.5rem;padding-right:1.5rem;}
  .hero-cnt,.hero-dots{padding-left:1.5rem;}
  .lb-prev{left:-36px;}
  .lb-next{right:-36px;}
  .fg-grid{grid-template-columns:1fr;}
}
</style>
</head>
<body>

<!-- LOADER -->
<div id="loader">
  <i class="fas fa-truck-monster loader-icon"></i>
  <div class="loader-bar"><div class="loader-fill"></div></div>
  <div class="loader-txt">Loading HeavyLift Pro...</div>
</div>

<!-- NAVBAR -->
<nav id="nav">
  <div class="logo" onclick="go('home')">
    <div class="logo-icon"><i class="fas fa-truck-monster"></i></div>
    HeavyLift<span>Pro</span>
  </div>
  <ul class="nav-links">
    <li><a onclick="go('home')" class="on" id="nl-home">Home</a></li>
    <li><a onclick="go('about')" id="nl-about">About</a></li>
    <li><a onclick="go('services')" id="nl-services">Services</a></li>
    <li><a onclick="go('gallery')" id="nl-gallery">Gallery</a></li>
    <li><a onclick="go('contact')" id="nl-contact">Contact</a></li>
    <li id="nl-au"><a onclick="go('login')" id="nl-login">Login</a></li>
    <li id="nl-db" style="display:none"><a onclick="go('dashboard')" id="nl-dash">Dashboard</a></li>
    <li id="nl-lo" style="display:none"><a onclick="logout()" id="nl-out">Logout</a></li>
  </ul>
  <a href="https://wa.me/919876543210" target="_blank" class="nav-wa"><i class="fab fa-whatsapp"></i> WhatsApp Us</a>
  <div class="hamburger" id="hbg" onclick="toggleMob()"><span></span><span></span><span></span></div>
</nav>

<!-- MOBILE NAV -->
<div class="mob-nav" id="mobNav">
  <a onclick="go('home');toggleMob()">Home</a>
  <a onclick="go('about');toggleMob()">About</a>
  <a onclick="go('services');toggleMob()">Services</a>
  <a onclick="go('gallery');toggleMob()">Gallery</a>
  <a onclick="go('contact');toggleMob()">Contact</a>
  <a onclick="go('login');toggleMob()" id="mn-login">Login</a>
  <a onclick="go('dashboard');toggleMob()" id="mn-dash" style="display:none">Dashboard</a>
  <a onclick="logout();toggleMob()" id="mn-out" style="display:none">Logout</a>
  <a href="https://wa.me/919876543210" target="_blank" style="color:#25D366"><i class="fab fa-whatsapp"></i> WhatsApp</a>
</div>

<!-- FLOATING WHATSAPP -->
<a href="https://wa.me/919876543210" target="_blank" class="waf"><i class="fab fa-whatsapp"></i></a>

<!-- TOAST -->
<div class="toast" id="toast"><i class="fas fa-check-circle"></i><span id="toastMsg"></span></div>

<!-- LIGHTBOX -->
<div class="lb" id="lb" onclick="lbClose(event)">
  <div class="lb-inner">
    <div class="lb-x" onclick="lbClose()"><i class="fas fa-times"></i></div>
    <div class="lb-arr lb-prev" onclick="lbMove(-1)"><i class="fas fa-chevron-left"></i></div>
    <img id="lb-img" src="" alt="">
    <div class="lb-arr lb-next" onclick="lbMove(1)"><i class="fas fa-chevron-right"></i></div>
    <div class="lb-cap" id="lb-cap"></div>
  </div>
</div>

<!-- ═══════════════════════════════════════ -->
<!-- HOME PAGE                              -->
<!-- ═══════════════════════════════════════ -->
<div class="page active" id="page-home">

  <!-- HERO -->
  <div class="hero" style="padding:0;">
    <canvas id="heroCanvas"></canvas>
    <div class="hero-bg" id="heroSlides">
      <div class="hslide on" style="background-image:url('https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=1800&q=85')"></div>
      <div class="hslide" style="background-image:url('https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=1800&q=85')"></div>
      <div class="hslide" style="background-image:url('https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=1800&q=85')"></div>
      <div class="hslide" style="background-image:url('https://images.unsplash.com/photo-1504309092620-4d0ec726efa4?w=1800&q=85')"></div>
      <div class="hslide" style="background-image:url('https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=1800&q=85')"></div>
    </div>
    <div class="hero-ov"></div>
    <div class="hero-cnt">
      <div class="hero-badge"><i class="fas fa-certificate"></i> Trusted &amp; Certified Since 2009</div>
      <h1>Reliable<br>Crane<em>Rental Services</em></h1>
      <p class="hero-sub">Heavy-duty cranes available for all your construction and industrial needs. Safe, efficient, and delivered on time — anywhere in India.</p>
      <div class="hero-btns">
        <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa"><i class="fab fa-whatsapp"></i> Book on WhatsApp</a>
        <button class="btn btn-outline" onclick="go('services')"><i class="fas fa-cogs"></i> Our Services</button>
        <button class="btn btn-y" onclick="go('contact')"><i class="fas fa-paper-plane"></i> Get Quote</button>
      </div>
    </div>
    <div class="hero-dots" id="heroDots">
      <div class="hdot on" onclick="hSlide(0)"></div>
      <div class="hdot" onclick="hSlide(1)"></div>
      <div class="hdot" onclick="hSlide(2)"></div>
      <div class="hdot" onclick="hSlide(3)"></div>
      <div class="hdot" onclick="hSlide(4)"></div>
    </div>
    <div class="hero-scroll">
      <span>Scroll Down</span>
      <div class="scroll-arrow"><i class="fas fa-chevron-down"></i></div>
    </div>
    <div class="hero-stats">
      <div class="hstat"><span class="hstat-num ctrn" data-t="15">0</span><span style="font-family:'Barlow Condensed',sans-serif;font-size:2rem;font-weight:900;color:var(--blk)">+</span><span class="hstat-lbl">Years Experience</span></div>
      <div class="hstat"><span class="hstat-num ctrn" data-t="500">0</span><span style="font-family:'Barlow Condensed',sans-serif;font-size:2rem;font-weight:900;color:var(--y)">+</span><span class="hstat-lbl">Projects Done</span></div>
      <div class="hstat"><span class="hstat-num ctrn" data-t="50">0</span><span style="font-family:'Barlow Condensed',sans-serif;font-size:2rem;font-weight:900;color:var(--y)">+</span><span class="hstat-lbl">Crane Fleet</span></div>
    </div>
  </div>

  <!-- MARQUEE STRIP -->
  <div class="mqw">
    <div class="mqt">
      <img class="mqimg" src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1504309092620-4d0ec726efa4?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1565008576549-57569a49371d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1573804633927-bfcbcd909acd?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1513828583688-c52646db42da?w=400&q=70" alt="crane">
      <!-- duplicate for seamless loop -->
      <img class="mqimg" src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1504309092620-4d0ec726efa4?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1565008576549-57569a49371d?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1573804633927-bfcbcd909acd?w=400&q=70" alt="crane">
      <img class="mqimg" src="https://images.unsplash.com/photo-1513828583688-c52646db42da?w=400&q=70" alt="crane">
    </div>
  </div>

  <!-- WHY CHOOSE US -->
  <section class="why-sec sec">
    <div class="sh reveal"><div class="stag">Why Us</div><h2 class="st">Why <span>Choose Us?</span></h2><div class="ydiv"></div></div>
    <div class="why-grid cascade">
      <div class="wcard"><div class="wico"><i class="fas fa-hard-hat"></i></div><h3>Expert Operators</h3><p>Certified crane operators with 15+ years of hands-on experience across India's biggest infrastructure projects.</p></div>
      <div class="wcard"><div class="wico"><i class="fas fa-shield-alt"></i></div><h3>Safety First</h3><p>Strict safety protocols, fully insured fleet and zero-incident track record since 2009. Your safety is our priority.</p></div>
      <div class="wcard"><div class="wico"><i class="fas fa-headset"></i></div><h3>24/7 Support</h3><p>Round-the-clock assistance and emergency on-site support. We're always available when you need us most.</p></div>
      <div class="wcard"><div class="wico"><i class="fas fa-tag"></i></div><h3>Best Rates</h3><p>Competitive pricing with fully transparent quotes — no hidden charges, no surprises, guaranteed.</p></div>
    </div>
  </section>

  <!-- SERVICES PREVIEW -->
  <section class="svc-sec sec">
    <div class="sh reveal"><div class="stag">What We Offer</div><h2>Our <span>Services</span></h2><div class="ydiv"></div><p>Full-spectrum crane solutions for construction, infrastructure and industry across India.</p></div>
    <div class="svc-grid cascade">
      <div class="svc">
        <div class="svc-img"><img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=700&q=85" alt="Mobile Crane"><div class="svc-chip">25T – 500T</div></div>
        <div class="svc-body"><div class="svc-ico"><i class="fas fa-truck-monster"></i></div><h3>Mobile Crane Rental</h3><p>All-terrain mobile cranes for flexible lifting on any site. Available 24/7 with certified operators.</p></div>
      </div>
      <div class="svc">
        <div class="svc-img"><img src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=700&q=85" alt="Tower Crane"><div class="svc-chip">Up to 200m</div></div>
        <div class="svc-body"><div class="svc-ico"><i class="fas fa-building"></i></div><h3>Tower Crane Rental</h3><p>High-rise tower cranes with advanced load monitoring for skyscrapers and large structures.</p></div>
      </div>
      <div class="svc">
        <div class="svc-img"><img src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=700&q=85" alt="Heavy Lifting"><div class="svc-chip">Industrial</div></div>
        <div class="svc-body"><div class="svc-ico"><i class="fas fa-weight-hanging"></i></div><h3>Heavy Lifting Solutions</h3><p>Expert rigging teams for industrial equipment, turbines, and oversized machinery installations.</p></div>
      </div>
    </div>
    <div style="text-align:center;margin-top:3rem;"><button class="btn btn-y" onclick="go('services')"><i class="fas fa-arrow-right"></i> View All Services</button></div>
  </section>

  <!-- COUNTERS -->
  <div class="ctr-sec">
    <div class="ctr-grid cascade">
      <div class="cb"><div class="cb-num"><span class="ctrn" data-t="500">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Projects Completed</div></div>
      <div class="cb"><div class="cb-num"><span class="ctrn" data-t="50">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Cranes in Fleet</div></div>
      <div class="cb"><div class="cb-num"><span class="ctrn" data-t="200">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Happy Clients</div></div>
      <div class="cb"><div class="cb-num"><span class="ctrn" data-t="0">0</span></div><div class="cb-lbl">Safety Incidents</div></div>
    </div>
  </div>

  <!-- CTA -->
  <div class="cta-s reveal">
    <div><h3>Ready to <span>Book a Crane?</span></h3><p>Get an instant quote. Our team responds within 1 hour.</p></div>
    <div class="cta-btns">
      <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa"><i class="fab fa-whatsapp"></i> Quick WhatsApp Quote</a>
      <button class="btn btn-outline" onclick="go('contact')"><i class="fas fa-envelope"></i> Send Inquiry</button>
    </div>
  </div>

  <!-- TESTIMONIALS -->
  <section class="test-sec sec">
    <div class="sh reveal"><div class="stag">Client Reviews</div><h2>What Clients <span>Say</span></h2><div class="ydiv"></div></div>
    <div class="test-grid cascade">
      <div class="tc"><div class="tc-stars">★★★★★</div><p>"Exceptional service! The crane arrived on time, the operator was highly skilled, and the entire operation was completed safely. Highly recommend HeavyLift Pro."</p><div class="tc-auth"><div class="tc-av">RK</div><div><div class="tc-name">Rajesh Kumar</div><div class="tc-role">Site Engineer, BuildMax Constructions</div></div></div></div>
      <div class="tc"><div class="tc-stars">★★★★★</div><p>"We've used HeavyLift Pro for 3 consecutive projects. Their tower crane setup was flawless and their pricing is the most competitive in the market."</p><div class="tc-auth"><div class="tc-av">AS</div><div><div class="tc-name">Anita Sharma</div><div class="tc-role">Project Manager, Skyline Developers</div></div></div></div>
      <div class="tc"><div class="tc-stars">★★★★★</div><p>"The heavy lifting team handled our 80-ton generator installation perfectly. Zero incidents, within budget. This is the only crane service we'll ever use."</p><div class="tc-auth"><div class="tc-av">VP</div><div><div class="tc-name">Vikram Patel</div><div class="tc-role">Operations Head, IndoPower Industries</div></div></div></div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="fg-grid">
      <div class="fb"><h3>HeavyLift<span>Pro</span></h3><p>India's trusted crane rental partner with 15+ years of excellence in safe, reliable, and efficient lifting operations across construction and industrial sectors.</p><div class="socs"><div class="soc"><i class="fab fa-facebook-f"></i></div><div class="soc"><i class="fab fa-instagram"></i></div><div class="soc"><i class="fab fa-linkedin-in"></i></div><a href="https://wa.me/919876543210" target="_blank" class="soc" style="background:#25D366;border-color:#25D366;color:#fff"><i class="fab fa-whatsapp"></i></a></div></div>
      <div class="fc"><h4>Quick Links</h4><ul class="fl"><li><a onclick="go('home')"><i class="fas fa-chevron-right"></i> Home</a></li><li><a onclick="go('about')"><i class="fas fa-chevron-right"></i> About Us</a></li><li><a onclick="go('services')"><i class="fas fa-chevron-right"></i> Services</a></li><li><a onclick="go('gallery')"><i class="fas fa-chevron-right"></i> Gallery</a></li><li><a onclick="go('contact')"><i class="fas fa-chevron-right"></i> Contact</a></li></ul></div>
      <div class="fc"><h4>Services</h4><ul class="fl"><li><a><i class="fas fa-chevron-right"></i> Mobile Crane</a></li><li><a><i class="fas fa-chevron-right"></i> Tower Crane</a></li><li><a><i class="fas fa-chevron-right"></i> Heavy Lifting</a></li><li><a><i class="fas fa-chevron-right"></i> Crawler Crane</a></li><li><a><i class="fas fa-chevron-right"></i> Industrial Rigging</a></li></ul></div>
      <div class="fc"><h4>Contact</h4><ul class="fl" style="gap:.8rem"><li style="color:var(--g);display:flex;gap:8px;align-items:flex-start"><i class="fas fa-phone" style="color:var(--y);margin-top:3px;flex-shrink:0"></i><span>+91 98765 43210</span></li><li style="color:var(--g);display:flex;gap:8px;align-items:flex-start"><i class="fas fa-envelope" style="color:var(--y);margin-top:3px;flex-shrink:0"></i><span>info@heavyliftpro.com</span></li><li style="color:var(--g);display:flex;gap:8px;align-items:flex-start"><i class="fas fa-map-marker-alt" style="color:var(--y);margin-top:3px;flex-shrink:0"></i><span>123 Construction Lane, Industrial Zone, City – 400001</span></li></ul></div>
    </div>
    <div class="fbot"><p>© 2024 <span>HeavyLift Pro</span>. All rights reserved.</p><p>Built with <span>♥</span> for the construction industry</p></div>
  </footer>
</div>

<!-- ═══════════ ABOUT PAGE ═══════════ -->
<div class="page" id="page-about">
  <div style="padding-top:72px">
    <div class="pghdr"><div class="stag">Who We Are</div><h1>About <span>HeavyLift Pro</span></h1></div>
    <section class="about-sec sec">
      <div class="about-grid">
        <div class="reveal-l">
          <div class="about-imgw">
            <div class="about-main-img"><img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=1000&q=85" alt="Crane Operations"></div>
            <div class="about-badge"><div class="abn">15+</div><div class="abl">Years Excellence</div></div>
            <div class="about-float-img"><img src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=600&q=80" alt="Rigging"></div>
          </div>
        </div>
        <div class="reveal-r">
          <div class="stag" style="margin-bottom:1rem">Our Story</div>
          <div class="about-content">
            <h2>Built on <span>Trust &amp;</span> Reliability</h2>
            <p>HeavyLift Pro was founded with a single mission: to provide India's construction and industrial sectors with world-class crane rental solutions. Since 2009, we've been the backbone of major infrastructure projects across the country.</p>
            <p>With a fleet of 50+ modern cranes — from mobile all-terrain units to towering high-rise cranes — we bring power, precision, and professionalism to every job site. Our operators are certified, our equipment is regularly inspected, and our commitment to zero-incident operations is non-negotiable.</p>
            <div class="afeats">
              <div class="afeat"><i class="fas fa-check-circle"></i><span>ISO 9001:2015 Certified Operations</span></div>
              <div class="afeat"><i class="fas fa-check-circle"></i><span>Fully insured fleet and operators</span></div>
              <div class="afeat"><i class="fas fa-check-circle"></i><span>Pan-India service availability</span></div>
              <div class="afeat"><i class="fas fa-check-circle"></i><span>24/7 emergency support team</span></div>
              <div class="afeat"><i class="fas fa-check-circle"></i><span>Transparent, competitive pricing</span></div>
            </div>
            <div style="margin-top:2rem;display:flex;gap:1rem;flex-wrap:wrap">
              <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa"><i class="fab fa-whatsapp"></i> Talk to Our Team</a>
              <button class="btn btn-outline" onclick="go('contact')"><i class="fas fa-envelope"></i> Contact Us</button>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- image + yellow panel -->
    <div style="display:grid;grid-template-columns:1fr 1fr;height:420px">
      <img src="https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=1000&q=85" alt="Night Operations" style="height:420px;object-fit:cover;">
      <div style="background:var(--y);display:flex;align-items:center;justify-content:center;padding:3rem;flex-direction:column;text-align:center">
        <i class="fas fa-shield-alt" style="font-size:3.5rem;color:var(--blk);margin-bottom:1.2rem"></i>
        <h3 style="font-family:'Barlow Condensed',sans-serif;font-size:2.5rem;font-weight:900;text-transform:uppercase;color:var(--blk);margin-bottom:.7rem">SAFETY IS<br>NON-NEGOTIABLE</h3>
        <p style="color:rgba(0,0,0,.65);max-width:320px;line-height:1.75">Every crane, every operator, every lift — certified, inspected, and insured. Zero incidents across 15 years of operation.</p>
      </div>
    </div>
    <div class="ctr-sec">
      <div class="ctr-grid cascade">
        <div class="cb"><div class="cb-num"><span class="ctrn" data-t="500">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Projects Completed</div></div>
        <div class="cb"><div class="cb-num"><span class="ctrn" data-t="50">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Cranes in Fleet</div></div>
        <div class="cb"><div class="cb-num"><span class="ctrn" data-t="200">0</span><span style="color:var(--y);font-family:'Barlow Condensed',sans-serif;font-size:3rem;font-weight:900">+</span></div><div class="cb-lbl">Happy Clients</div></div>
        <div class="cb"><div class="cb-num"><span class="ctrn" data-t="0">0</span></div><div class="cb-lbl">Safety Incidents</div></div>
      </div>
    </div>
    <footer style="background:var(--blk);border-top:1px solid var(--d3);padding:30px 5rem;display:flex;justify-content:space-between;align-items:center;color:var(--g);font-size:.85rem;flex-wrap:wrap;gap:.5rem">
      <p>© 2024 <span style="color:var(--y)">HeavyLift Pro</span>. All rights reserved.</p>
      <button class="btn btn-y" style="padding:9px 22px;font-size:.85rem" onclick="go('contact')"><i class="fas fa-phone"></i> Contact Us</button>
    </footer>
  </div>
</div>

<!-- ═══════════ SERVICES PAGE ═══════════ -->
<div class="page" id="page-services">
  <div style="padding-top:72px">
    <div class="pghdr"><div class="stag">What We Offer</div><h1>Our <span>Services</span></h1></div>
    <section class="svc-sec sec">
      <div class="svc-grid cascade">
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=700&q=85" alt="Mobile Crane"><div class="svc-chip">25T–500T</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-truck-monster"></i></div><h3>Mobile Crane Rental</h3><p>All-terrain mobile cranes for flexible lifting. Ideal for road construction, building projects, and industrial installations. 24/7 with certified operators.</p></div></div>
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=700&q=85" alt="Tower Crane"><div class="svc-chip">Up to 200m</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-building"></i></div><h3>Tower Crane Rental</h3><p>High-performance tower cranes with advanced load monitoring, remote operation, and complex urban site erection capability.</p></div></div>
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=700&q=85" alt="Heavy Lifting"><div class="svc-chip">1000T Tandem</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-weight-hanging"></i></div><h3>Heavy Lifting Solutions</h3><p>Extreme heavy lift projects — turbines, pressure vessels, bridge beams, and industrial machinery with expert precision rigging teams.</p></div></div>
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=700&q=85" alt="Crawler Crane"><div class="svc-chip">50T–800T</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-cog"></i></div><h3>Crawler Crane Rental</h3><p>Track-mounted crawler cranes for soft ground, power plant construction, and long-term site presence with superior stability.</p></div></div>
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=700&q=85" alt="Rigging"><div class="svc-chip">Certified</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-tools"></i></div><h3>Industrial Rigging</h3><p>Complete rigging plans by qualified engineers. Certified slings, shackles, spreader beams, and all lifting accessories included.</p></div></div>
        <div class="svc"><div class="svc-img"><img src="https://images.unsplash.com/photo-1565008576549-57569a49371d?w=700&q=85" alt="Consultation"><div class="svc-chip">Free</div></div><div class="svc-body"><div class="svc-ico"><i class="fas fa-drafting-compass"></i></div><h3>Project Consultation</h3><p>Expert lift planning, site feasibility studies, and crane selection consulting. Right equipment, right cost — every time.</p></div></div>
      </div>
    </section>
    <div class="cta-s reveal">
      <div><h3>Need a <span>Custom Solution?</span></h3><p>Contact us for specialized requirements and project consultation.</p></div>
      <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa"><i class="fab fa-whatsapp"></i> Get a Free Quote</a>
    </div>
    <footer style="background:var(--blk);border-top:1px solid var(--d3);padding:28px 5rem;text-align:center;color:var(--g);font-size:.85rem"><p>© 2024 <span style="color:var(--y)">HeavyLift Pro</span>. All rights reserved.</p></footer>
  </div>
</div>

<!-- ═══════════ GALLERY PAGE ═══════════ -->
<div class="page" id="page-gallery">
  <div style="padding-top:72px">
    <div class="pghdr"><div class="stag">Portfolio</div><h1>Our <span>Gallery</span></h1></div>
    <section class="gal-sec sec">
      <div class="gal-tabs" id="galTabs">
        <div class="gtab on" onclick="galFilter('all',this)">All Photos</div>
        <div class="gtab" onclick="galFilter('construction',this)">Construction</div>
        <div class="gtab" onclick="galFilter('industrial',this)">Industrial</div>
        <div class="gtab" onclick="galFilter('night',this)">Night Ops</div>
      </div>
      <div class="gal-grid cascade" id="galGrid">
        <!-- CONSTRUCTION -->
        <div class="gi wide" data-c="construction" data-src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=1400&q=90" data-cap="Mobile Crane – High Rise Construction Site" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1504307651254-35680f356dfd?w=800&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Mobile Crane</span><span class="gi-sub">High Rise Construction Site</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="construction" data-src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=1000&q=90" data-cap="Tower Crane – City Skyline Project" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1590846406792-0adc7f938f1d?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Tower Crane</span><span class="gi-sub">City Skyline Project</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="construction" data-src="https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=1000&q=90" data-cap="Bridge Beam Lift Operation" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1531973576160-7125cd663d86?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Bridge Lift</span><span class="gi-sub">Beam Placement Operation</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="construction" data-src="https://images.unsplash.com/photo-1565008576549-57569a49371d?w=1000&q=90" data-cap="Multi-Crane Construction Operation" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1565008576549-57569a49371d?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Multi-Crane</span><span class="gi-sub">Complex Site Operation</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <!-- INDUSTRIAL -->
        <div class="gi" data-c="industrial" data-src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=1000&q=90" data-cap="Industrial Heavy Equipment Installation" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1512207736890-6ffed8a84e8d?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Heavy Equipment</span><span class="gi-sub">Industrial Installation</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="industrial" data-src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=1000&q=90" data-cap="Factory Rigging Operation" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1581092335878-2d9ff86ad2b9?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Factory Rigging</span><span class="gi-sub">Precision Lift Operation</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi wide" data-c="industrial" data-src="https://images.unsplash.com/photo-1513828583688-c52646db42da?w=1400&q=90" data-cap="Crawler Crane – Power Plant Installation" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1513828583688-c52646db42da?w=800&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Crawler Crane</span><span class="gi-sub">Power Plant Installation</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <!-- NIGHT -->
        <div class="gi" data-c="night" data-src="https://images.unsplash.com/photo-1573804633927-bfcbcd909acd?w=1000&q=90" data-cap="Night Shift Crane Operations" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1573804633927-bfcbcd909acd?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Night Shift</span><span class="gi-sub">Crane Operations</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="night" data-src="https://images.unsplash.com/photo-1504309092620-4d0ec726efa4?w=1000&q=90" data-cap="Urban Night Crane Work" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1504309092620-4d0ec726efa4?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Urban Night Work</span><span class="gi-sub">City Centre Project</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi" data-c="night" data-src="https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=1000&q=90" data-cap="Illuminated Tower Crane at Night" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1541888946425-d81bb19240f5?w=600&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Illuminated Crane</span><span class="gi-sub">Tower Crane at Night</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
        <div class="gi wide" data-c="night" data-src="https://images.unsplash.com/photo-1586864387634-2f33030dab41?w=1400&q=90" data-cap="Crane Floodlit During Night Operations" onclick="lbOpen(this)"><img src="https://images.unsplash.com/photo-1586864387634-2f33030dab41?w=800&q=80" alt=""><div class="gi-ov"><span class="gi-lbl">Floodlit Night Ops</span><span class="gi-sub">Continuous Site Work</span></div><div class="gi-zoom"><i class="fas fa-expand-alt"></i></div></div>
      </div>
    </section>
    <footer style="background:var(--blk);border-top:1px solid var(--d3);padding:28px 5rem;text-align:center;color:var(--g);font-size:.85rem"><p>© 2024 <span style="color:var(--y)">HeavyLift Pro</span>. All rights reserved.</p></footer>
  </div>
</div>

<!-- ═══════════ CONTACT PAGE ═══════════ -->
<div class="page" id="page-contact">
  <div style="padding-top:72px">
    <div class="pghdr"><div class="stag">Get in Touch</div><h1>Contact <span>Us</span></h1></div>
    <section class="cont-sec sec">
      <div class="cont-grid">
        <div class="reveal-l">
          <div class="cform">
            <h3>Send Us a <span>Message</span></h3>
            <div class="fg"><label>Full Name *</label><input type="text" id="cn" placeholder="Your full name"></div>
            <div class="fg"><label>Phone Number *</label><input type="tel" id="cp" placeholder="+91 XXXXX XXXXX"></div>
            <div class="fg"><label>Email Address</label><input type="email" id="ce" placeholder="your@email.com"></div>
            <div class="fg"><label>Service Required</label><select id="cs"><option value="">Select a service...</option><option>Mobile Crane Rental</option><option>Tower Crane Rental</option><option>Heavy Lifting Solutions</option><option>Crawler Crane Rental</option><option>Industrial Rigging</option><option>Project Consultation</option></select></div>
            <div class="fg"><label>Your Message *</label><textarea id="cm" placeholder="Describe your project requirements, location, timeline, and lifting capacity needed..."></textarea></div>
            <button class="btn btn-y" style="width:100%;justify-content:center" onclick="sendContact()"><i class="fas fa-paper-plane"></i> Send Message</button>
            <div style="margin-top:1rem"><a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa" style="width:100%;justify-content:center;display:flex"><i class="fab fa-whatsapp"></i> Or Contact on WhatsApp</a></div>
          </div>
        </div>
        <div class="reveal-r">
          <div class="cinfo" style="padding-top:1rem">
            <div class="stag" style="margin-bottom:1rem">Reach Us</div>
            <h3>We're Here<br>to <span>Help</span></h3>
            <p>Get in touch for quick quotes, project consultation, or any questions about our crane rental services. We respond within 1 business hour.</p>
            <div class="icards">
              <div class="icard"><div class="iico"><i class="fas fa-phone"></i></div><div><h4>Call Us</h4><p>+91 98765 43210</p></div></div>
              <div class="icard"><div class="iico"><i class="fab fa-whatsapp"></i></div><div><h4>WhatsApp</h4><p>+91 98765 43210 (24/7 Available)</p></div></div>
              <div class="icard"><div class="iico"><i class="fas fa-envelope"></i></div><div><h4>Email</h4><p>info@heavyliftpro.com</p></div></div>
              <div class="icard"><div class="iico"><i class="fas fa-map-marker-alt"></i></div><div><h4>Location</h4><p>123 Construction Lane, Industrial Zone, City – 400001</p></div></div>
              <div class="icard"><div class="iico"><i class="fas fa-clock"></i></div><div><h4>Working Hours</h4><p>Mon–Sat: 8AM – 8PM &nbsp;|&nbsp; Emergency: 24/7</p></div></div>
            </div>
            <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa" style="display:inline-flex"><i class="fab fa-whatsapp"></i> Start WhatsApp Chat</a>
          </div>
        </div>
      </div>
    </section>
    <footer style="background:var(--blk);border-top:1px solid var(--d3);padding:28px 5rem;text-align:center;color:var(--g);font-size:.85rem"><p>© 2024 <span style="color:var(--y)">HeavyLift Pro</span>. All rights reserved.</p></footer>
  </div>
</div>

<!-- ═══════════ LOGIN PAGE ═══════════ -->
<div class="page" id="page-login">
  <div class="auth-pg">
    <div class="auth-box">
      <div class="auth-icon"><i class="fas fa-truck-monster"></i></div>
      <h2>Welcome <span>Back</span></h2>
      <p class="auth-sub">Login to manage your bookings and inquiries.</p>
      <div class="fg"><label>Email Address</label><input type="email" id="le" placeholder="demo@test.com"></div>
      <div class="fg"><label>Password</label><input type="password" id="lp" placeholder="demo123"></div>
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:1.5rem">
        <label style="display:flex;align-items:center;gap:8px;font-size:.9rem;cursor:pointer"><input type="checkbox" style="accent-color:var(--y)"> Remember me</label>
        <span style="color:var(--g);font-size:.85rem;cursor:pointer">Forgot password?</span>
      </div>
      <button class="btn btn-y" style="width:100%;justify-content:center" onclick="doLogin()"><i class="fas fa-sign-in-alt"></i> Login</button>
      <div class="adiv">— or —</div>
      <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa" style="display:flex;justify-content:center"><i class="fab fa-whatsapp"></i> Continue via WhatsApp</a>
      <p style="text-align:center;margin-top:1.5rem;color:var(--g);font-size:.9rem">No account? <span class="auth-lnk" onclick="go('signup')">Create one</span></p>
      <div class="demo-hint">Demo credentials: demo@test.com &nbsp;/&nbsp; demo123</div>
    </div>
  </div>
</div>

<!-- ═══════════ SIGNUP PAGE ═══════════ -->
<div class="page" id="page-signup">
  <div class="auth-pg">
    <div class="auth-box">
      <div class="auth-icon"><i class="fas fa-truck-monster"></i></div>
      <h2>Create <span>Account</span></h2>
      <p class="auth-sub">Join HeavyLift Pro to manage your crane bookings easily.</p>
      <div class="fg"><label>Full Name</label><input type="text" id="sn" placeholder="Your full name"></div>
      <div class="fg"><label>Email Address</label><input type="email" id="se" placeholder="your@email.com"></div>
      <div class="fg"><label>Phone Number</label><input type="tel" id="sp" placeholder="+91 XXXXX XXXXX"></div>
      <div class="fg"><label>Password</label><input type="password" id="sw" placeholder="Create a strong password"></div>
      <div class="fg"><label>Confirm Password</label><input type="password" id="sc" placeholder="Re-enter your password"></div>
      <button class="btn btn-y" style="width:100%;justify-content:center" onclick="doSignup()"><i class="fas fa-user-plus"></i> Create Account</button>
      <p style="text-align:center;margin-top:1.5rem;color:var(--g);font-size:.9rem">Already have an account? <span class="auth-lnk" onclick="go('login')">Login</span></p>
    </div>
  </div>
</div>

<!-- ═══════════ DASHBOARD PAGE ═══════════ -->
<div class="page" id="page-dashboard">
  <div class="dash-pg">
    <div class="dash-hero">
      <h1>Welcome, <span id="dname">User</span>! 👷</h1>
      <p>Manage your crane bookings, inquiries, and account settings.</p>
    </div>
    <div class="dash-body">
      <div class="dash-cards cascade">
        <div class="dc" onclick="go('contact')"><i class="fas fa-calendar-check"></i><h3>My Bookings</h3><p>View and manage your crane rental bookings</p></div>
        <div class="dc"><i class="fas fa-user-circle"></i><h3>My Profile</h3><p>Update your personal and business information</p></div>
        <div class="dc" onclick="go('contact')"><i class="fas fa-file-invoice"></i><h3>Inquiries</h3><p>Track all service inquiries and responses</p></div>
      </div>
      <div style="background:var(--d2);border:1px solid var(--d3);border-radius:12px;padding:2.8rem">
        <h3 style="font-family:'Barlow Condensed',sans-serif;font-size:2rem;font-weight:900;text-transform:uppercase;margin-bottom:1.5rem">Quick <span style="color:var(--y)">Booking Inquiry</span></h3>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem">
          <div class="fg"><label>Service Required</label><select><option>Mobile Crane Rental</option><option>Tower Crane Rental</option><option>Heavy Lifting</option></select></div>
          <div class="fg"><label>Project Location</label><input type="text" placeholder="City, State"></div>
          <div class="fg"><label>Start Date</label><input type="date"></div>
          <div class="fg"><label>Duration</label><select><option>1 Day</option><option>1 Week</option><option>1 Month</option><option>Custom</option></select></div>
        </div>
        <div class="fg"><label>Additional Requirements</label><textarea placeholder="Crane capacity, site conditions, access constraints..."></textarea></div>
        <div style="display:flex;gap:1rem;flex-wrap:wrap">
          <button class="btn btn-y" onclick="toast('Inquiry submitted! We will contact you within 1 hour.')"><i class="fas fa-paper-plane"></i> Submit Inquiry</button>
          <a href="https://wa.me/919876543210" target="_blank" class="btn btn-wa"><i class="fab fa-whatsapp"></i> WhatsApp Booking</a>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════ SCRIPT ═══════════ -->
<script>
/* ── LOADER ── */
window.addEventListener('load',()=>{
  setTimeout(()=>{
    document.getElementById('loader').classList.add('gone');
    initAll();
  },1600);
});

/* ── STATE ── */
let me=null, users=[], hIdx=0;

/* ── NAVIGATE ── */
function go(pg){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active','pg-enter'));
  const el=document.getElementById('page-'+pg);
  if(el){el.classList.add('active');requestAnimationFrame(()=>el.classList.add('pg-enter'));}
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('on'));
  const nl=document.getElementById('nl-'+pg);
  if(nl)nl.classList.add('on');
  window.scrollTo({top:0,behavior:'smooth'});
  setTimeout(()=>{initReveal();runCounters();},120);
}

/* ── MOBILE MENU ── */
function toggleMob(){
  document.getElementById('hbg').classList.toggle('open');
  document.getElementById('mobNav').classList.toggle('open');
}

/* ── NAV SCROLL ── */
window.addEventListener('scroll',()=>{
  document.getElementById('nav').classList.toggle('solid',window.scrollY>40);
});

/* ── HERO SLIDESHOW ── */
function hSlide(n){
  document.querySelectorAll('.hslide').forEach((s,i)=>s.classList.toggle('on',i===n));
  document.querySelectorAll('.hdot').forEach((d,i)=>d.classList.toggle('on',i===n));
  hIdx=n;
}
setInterval(()=>{
  const ss=document.querySelectorAll('.hslide');
  if(ss.length)hSlide((hIdx+1)%ss.length);
},5500);

/* ── PARTICLE CANVAS ── */
(function(){
  const cv=document.getElementById('heroCanvas');
  if(!cv)return;
  const cx=cv.getContext('2d');
  let W,H,pts=[];
  const resize=()=>{W=cv.width=cv.offsetWidth||innerWidth;H=cv.height=cv.offsetHeight||innerHeight;};
  resize();window.addEventListener('resize',resize);
  const make=()=>({x:Math.random()*W,y:Math.random()*H,r:Math.random()*2+.5,vx:(Math.random()-.5)*.5,vy:(Math.random()-.5)*.5,a:Math.random()*.45+.08});
  for(let i=0;i<90;i++)pts.push(make());
  (function loop(){
    cx.clearRect(0,0,W,H);
    pts.forEach(p=>{
      p.x+=p.vx;p.y+=p.vy;
      if(p.x<0||p.x>W)p.vx*=-1;
      if(p.y<0||p.y>H)p.vy*=-1;
      cx.beginPath();cx.arc(p.x,p.y,p.r,0,Math.PI*2);
      cx.fillStyle=`rgba(255,208,0,${p.a})`;cx.fill();
    });
    for(let i=0;i<pts.length;i++)for(let j=i+1;j<pts.length;j++){
      const dx=pts[i].x-pts[j].x,dy=pts[i].y-pts[j].y,d=Math.sqrt(dx*dx+dy*dy);
      if(d<130){cx.beginPath();cx.moveTo(pts[i].x,pts[i].y);cx.lineTo(pts[j].x,pts[j].y);cx.strokeStyle=`rgba(255,208,0,${.09*(1-d/130)})`;cx.lineWidth=.7;cx.stroke();}
    }
    requestAnimationFrame(loop);
  })();
})();

/* ── SCROLL REVEAL ── */
let revObs;
function initReveal(){
  if(revObs)revObs.disconnect();
  revObs=new IntersectionObserver(entries=>{
    entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('in');});
  },{threshold:.1,rootMargin:'0px 0px -40px 0px'});
  document.querySelectorAll('.page.active .reveal,.page.active .reveal-l,.page.active .reveal-r,.page.active .reveal-s,.page.active .cascade').forEach(el=>{
    el.classList.remove('in');revObs.observe(el);
  });
}

/* ── ANIMATED COUNTERS ── */
const counted=new Set();
function runCounters(){
  document.querySelectorAll('.page.active .ctrn').forEach(el=>{
    if(counted.has(el))return;
    const obs=new IntersectionObserver(([e])=>{
      if(!e.isIntersecting)return;
      obs.disconnect();counted.add(el);
      const t=+el.getAttribute('data-t');
      if(t===0){el.textContent='0';return;}
      let s=null;
      const step=ts=>{if(!s)s=ts;const p=Math.min((ts-s)/2000,1);const ease=1-Math.pow(1-p,3);el.textContent=Math.floor(ease*t);if(p<1)requestAnimationFrame(step);else el.textContent=t;};
      requestAnimationFrame(step);
    },{threshold:.5});
    obs.observe(el);
  });
}

/* ── GALLERY FILTER ── */
function galFilter(cat,el){
  document.querySelectorAll('.gtab').forEach(t=>t.classList.remove('on'));
  el.classList.add('on');
  document.querySelectorAll('#galGrid .gi').forEach(item=>{
    const show=cat==='all'||item.dataset.c===cat;
    item.style.display=show?'':'none';
    if(show){item.style.opacity='0';item.style.transform='scale(.9)';setTimeout(()=>{item.style.transition='all .4s ease';item.style.opacity='1';item.style.transform='scale(1)';},10);}
  });
}

/* ── LIGHTBOX ── */
let lbItems=[],lbI=0;
function lbOpen(el){
  lbItems=[...document.querySelectorAll('#galGrid .gi')].filter(i=>i.style.display!=='none');
  lbI=lbItems.indexOf(el);lbShow();
  document.getElementById('lb').classList.add('open');
  document.body.style.overflow='hidden';
}
function lbShow(){
  const el=lbItems[lbI];
  const img=document.getElementById('lb-img');
  img.style.opacity='0';
  setTimeout(()=>{img.src=el.dataset.src;img.style.transition='opacity .3s';img.style.opacity='1';document.getElementById('lb-cap').textContent=el.dataset.cap;},150);
}
function lbMove(d){lbI=(lbI+d+lbItems.length)%lbItems.length;lbShow();}
function lbClose(e){if(!e||e.target===document.getElementById('lb')){document.getElementById('lb').classList.remove('open');document.body.style.overflow='';}}
document.addEventListener('keydown',e=>{
  if(!document.getElementById('lb').classList.contains('open'))return;
  if(e.key==='ArrowRight')lbMove(1);
  if(e.key==='ArrowLeft')lbMove(-1);
  if(e.key==='Escape')lbClose();
});

/* ── AUTH ── */
function doLogin(){
  const em=document.getElementById('le').value.trim(),pw=document.getElementById('lp').value;
  if(!em||!pw){toast('Please fill in all fields.','err');return;}
  const u=users.find(x=>x.email===em&&x.pass===pw);
  if(u||(em==='demo@test.com'&&pw==='demo123')){
    me=u||{name:'Demo User',email:em};
    document.getElementById('dname').textContent=me.name.split(' ')[0];
    authUI(true);go('dashboard');toast('Welcome back, '+me.name.split(' ')[0]+'! 👷');
  }else toast('Invalid credentials. Try demo@test.com / demo123','err');
}
function doSignup(){
  const n=document.getElementById('sn').value.trim(),em=document.getElementById('se').value.trim();
  const ph=document.getElementById('sp').value.trim(),pw=document.getElementById('sw').value,cp=document.getElementById('sc').value;
  if(!n||!em||!pw||!cp){toast('Please fill in all required fields.','err');return;}
  if(pw!==cp){toast('Passwords do not match!','err');return;}
  if(pw.length<6){toast('Password must be at least 6 characters.','err');return;}
  if(users.find(x=>x.email===em)){toast('Email already registered. Please login.','err');return;}
  users.push({name:n,email:em,phone:ph,pass:pw});
  me={name:n,email:em,phone:ph};
  document.getElementById('dname').textContent=n.split(' ')[0];
  authUI(true);go('dashboard');toast('Account created! Welcome, '+n.split(' ')[0]+'! 🎉');
}
function logout(){me=null;authUI(false);go('home');toast('You have been logged out.');}
function authUI(on){
  document.getElementById('nl-au').style.display=on?'none':'';
  document.getElementById('nl-db').style.display=on?'':'none';
  document.getElementById('nl-lo').style.display=on?'':'none';
  document.getElementById('mn-login').style.display=on?'none':'';
  document.getElementById('mn-dash').style.display=on?'':'none';
  document.getElementById('mn-out').style.display=on?'':'none';
}

/* ── CONTACT FORM ── */
function sendContact(){
  const n=document.getElementById('cn').value.trim(),p=document.getElementById('cp').value.trim(),m=document.getElementById('cm').value.trim();
  if(!n||!p||!m){toast('Please fill in all required fields.','err');return;}
  toast('Message sent! We will contact you within 1 hour. ✓');
  ['cn','cp','ce','cm'].forEach(id=>document.getElementById(id).value='');
}

/* ── TOAST ── */
function toast(msg,type='ok'){
  const t=document.getElementById('toast'),i=t.querySelector('i'),s=document.getElementById('toastMsg');
  s.textContent=msg;
  if(type==='err'){i.className='fas fa-exclamation-circle';i.style.color='var(--red)';t.style.borderColor='var(--red)';}
  else{i.className='fas fa-check-circle';i.style.color='var(--y)';t.style.borderColor='var(--y)';}
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),3600);
}

/* ── INIT ALL ── */
function initAll(){
  initReveal();
  runCounters();
  // counter obs for counter section
  new IntersectionObserver(([e])=>{if(e.isIntersecting)runCounters();},{threshold:.3}).observe(document.querySelector('.ctr-sec')||document.body);
}
</script>
</body>
</html>
