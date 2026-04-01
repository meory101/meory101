<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Nour.park — Nour Othman</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Outfit:wght@300;400;600;700&display=swap" rel="stylesheet"/>
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --sky:#0a0612;--sky2:#120820;--ground:#1a0f2e;
  --grass:#2d1f5e;--grass2:#3d2870;
  --purple:#a78bfa;--pink:#f472b6;--teal:#2dd4bf;
  --amber:#fbbf24;--glow:#7c3aed;
}
html{scroll-behavior:smooth}
body{
  font-family:'Outfit',sans-serif;
  background:var(--sky);
  overflow-x:hidden;
  min-height:100vh;
  cursor:crosshair;
}
.stars{position:fixed;top:0;left:0;width:100%;height:60%;pointer-events:none;z-index:0}
.star{position:absolute;border-radius:50%;animation:twinkle var(--d,2s) ease-in-out infinite alternate}
@keyframes twinkle{from{opacity:.2;transform:scale(.8)}to{opacity:1;transform:scale(1.2)}}
.scene{position:relative;min-height:100vh;display:flex;flex-direction:column;padding-top:40px;}
.sky-area{position:relative;flex:1;display:flex;flex-direction:column;align-items:center;padding:20px 20px 0;z-index:10;}
.moon{width:90px;height:90px;background:#fffde7;border-radius:50%;box-shadow:0 0 40px 20px rgba(255,253,160,.25),0 0 80px 40px rgba(251,191,36,.1);position:absolute;top:20px;right:12%;animation:moonFloat 6s ease-in-out infinite;}
@keyframes moonFloat{0%,100%{transform:translateY(0)}50%{transform:translateY(-12px)}}
.title-board{background:#1e0d3e;border:3px solid var(--purple);border-radius:16px;padding:20px 40px;text-align:center;box-shadow:0 0 30px rgba(167,139,250,.3),inset 0 0 30px rgba(167,139,250,.05);position:relative;z-index:10;margin-top:10px;max-width:700px;width:90%;}
.title-board::before{content:'★ WELCOME TO NOUR.PARK ★';position:absolute;top:-14px;left:50%;transform:translateX(-50%);background:var(--glow);color:#fff;font-family:'Press Start 2P',monospace;font-size:8px;padding:4px 14px;border-radius:20px;white-space:nowrap;}
.title-board h1{font-family:'Press Start 2P',monospace;font-size:clamp(14px,3vw,22px);color:var(--purple);line-height:1.6;text-shadow:0 0 20px rgba(167,139,250,.6);}
.title-board p{color:#c4b5fd;font-size:clamp(13px,2vw,16px);margin-top:10px;font-weight:300;letter-spacing:.5px;}
.badges{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-top:14px}
.badge{font-size:11px;padding:5px 14px;border-radius:20px;font-weight:600;letter-spacing:.3px;border:1.5px solid;}
.badge.loc{color:#2dd4bf;border-color:#2dd4bf;background:rgba(45,212,191,.08)}
.badge.gpa{color:#fbbf24;border-color:#fbbf24;background:rgba(251,191,36,.08)}
.badge.avail{color:#86efac;border-color:#86efac;background:rgba(134,239,172,.08);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{box-shadow:0 0 0 0 rgba(134,239,172,.4)}50%{box-shadow:0 0 0 6px rgba(134,239,172,0)}}
.park{position:relative;width:100%;min-height:520px;background:linear-gradient(180deg,var(--sky2) 0%,var(--ground) 30%,var(--grass) 50%,var(--grass2) 100%);overflow:hidden;z-index:5;}
.park::after{content:'';position:absolute;bottom:0;left:0;right:0;height:8px;background:repeating-linear-gradient(90deg,var(--grass) 0px,var(--grass) 20px,var(--grass2) 20px,var(--grass2) 40px);}
.path{position:absolute;bottom:70px;left:0;right:0;height:50px;background:rgba(167,139,250,.08);border-top:2px dashed rgba(167,139,250,.3);border-bottom:2px dashed rgba(167,139,250,.3);}
.tree{position:absolute;bottom:60px;display:flex;flex-direction:column;align-items:center}
.tree-top{background:#2d1f5e;clip-path:polygon(50% 0%,100% 100%,0% 100%)}
.tree-trunk{background:#4a2c2c;border-radius:2px}
.t1{width:60px;height:80px}.t1 .tree-trunk{width:12px;height:25px}
.t2{width:80px;height:100px}.t2 .tree-trunk{width:15px;height:30px}
.t3{width:45px;height:60px}.t3 .tree-trunk{width:10px;height:20px}
.tree-glow .tree-top{background:#3d2870;filter:drop-shadow(0 0 8px rgba(167,139,250,.4));}
.lamp{position:absolute;bottom:60px;display:flex;flex-direction:column;align-items:center}
.lamp-pole{width:4px;background:#4a4080;border-radius:2px}
.lamp-head{width:20px;height:12px;background:#fbbf24;border-radius:10px 10px 0 0;box-shadow:0 0 20px 8px rgba(251,191,36,.3),0 0 40px 16px rgba(251,191,36,.1);animation:lampGlow 3s ease-in-out infinite alternate;}
@keyframes lampGlow{from{box-shadow:0 0 15px 5px rgba(251,191,36,.3)}to{box-shadow:0 0 30px 12px rgba(251,191,36,.4)}}
.sign{position:absolute;display:flex;flex-direction:column;align-items:center;cursor:pointer;transition:transform .3s;}
.sign:hover{transform:scale(1.05) translateY(-4px)}
.sign-board{background:#1e0d3e;border:2px solid var(--purple);border-radius:10px;padding:12px 16px;text-align:center;box-shadow:0 4px 20px rgba(124,58,237,.3);min-width:130px;position:relative;}
.sign-board::after{content:'';position:absolute;bottom:-12px;left:50%;transform:translateX(-50%);border:6px solid transparent;border-top-color:var(--purple);}
.sign-pole{width:3px;background:#4a4080;border-radius:2px}
.sign h3{font-family:'Press Start 2P',monospace;font-size:7px;color:var(--purple);margin-bottom:6px}
.sign p{color:#e2d9f3;font-size:11px;font-weight:600;line-height:1.4}
.sign span{font-size:18px;display:block;margin-bottom:4px}
.bench{position:absolute;bottom:68px}
.bench-seat{height:8px;background:#4a2c2c;border-radius:3px;border:1px solid #6b3f3f}
.bench-legs{display:flex;justify-content:space-between;margin-top:2px}
.bench-leg{width:5px;height:14px;background:#4a2c2c;border-radius:1px}
.robot{position:absolute;bottom:75px;display:flex;flex-direction:column;align-items:center;cursor:pointer}
.robot:hover .speech{opacity:1;transform:translateY(-5px) scale(1)}
.robot:hover .robo-body{filter:drop-shadow(0 0 12px rgba(167,139,250,.6))}
.robo-antenna{width:3px;height:14px;background:#a78bfa;margin:0 auto;border-radius:2px;position:relative}
.robo-antenna::after{content:'';position:absolute;top:-5px;left:50%;transform:translateX(-50%);width:7px;height:7px;background:#f472b6;border-radius:50%;box-shadow:0 0 8px rgba(244,114,182,.8)}
.robo-head{width:36px;height:30px;background:#2d1b69;border:2px solid #7c3aed;border-radius:6px;display:flex;align-items:center;justify-content:center;position:relative;}
.robo-eyes{display:flex;gap:6px}
.robo-eye{width:8px;height:8px;background:#a78bfa;border-radius:50%;animation:blink 4s ease-in-out infinite;}
@keyframes blink{0%,90%,100%{transform:scaleY(1)}95%{transform:scaleY(.1)}}
.robo-body{width:40px;height:40px;background:#1e0d3e;border:2px solid #6d28d9;border-radius:6px;display:flex;align-items:center;justify-content:center;margin-top:2px;position:relative;}
.robo-chest{width:14px;height:14px;border-radius:3px;border:1.5px solid}
.robo-feet{display:flex;gap:4px;margin-top:2px}
.robo-foot{width:14px;height:8px;background:#2d1b69;border:1.5px solid #6d28d9;border-radius:3px}
.robo-arm{width:8px;height:22px;background:#2d1b69;border:1.5px solid #6d28d9;border-radius:4px}
.speech{position:absolute;bottom:110px;background:#1e0d3e;border:2px solid var(--purple);border-radius:12px;padding:8px 12px;opacity:0;transition:all .3s;transform:translateY(5px) scale(.95);white-space:nowrap;z-index:20;pointer-events:none;box-shadow:0 4px 20px rgba(124,58,237,.4);}
.speech::after{content:'';position:absolute;bottom:-10px;left:50%;transform:translateX(-50%);border:5px solid transparent;border-top-color:var(--purple);}
.speech p{font-size:10px;color:#e2d9f3;font-weight:600;text-align:center}
.speech .tag{font-size:9px;color:var(--purple);font-family:'Press Start 2P',monospace;display:block;margin-bottom:3px}
@keyframes bobUp{0%,100%{transform:translateY(0)}50%{transform:translateY(-4px)}}
@keyframes patrol{0%{left:10%}50%{left:55%}100%{left:10%}}
@keyframes patrol2{0%{left:40%}50%{left:80%}100%{left:40%}}
@keyframes footStep{0%,100%{transform:translateY(0)}50%{transform:translateY(-3px)}}
.robot.walks .robo-foot:nth-child(1){animation:footStep 0.5s infinite}
.robot.walks .robo-foot:nth-child(2){animation:footStep 0.5s .25s infinite}
.skills-cloud{position:absolute;top:20px;left:20px;display:flex;flex-wrap:wrap;gap:8px;max-width:220px;}
.skill-pill{font-size:10px;font-weight:700;padding:5px 12px;border-radius:20px;letter-spacing:.3px;animation:floatPill var(--fd,3s) ease-in-out infinite alternate;border:1.5px solid;}
@keyframes floatPill{from{transform:translateY(0)}to{transform:translateY(-6px)}}
.stats-row{display:flex;justify-content:center;gap:20px;flex-wrap:wrap;padding:30px 20px 0;position:relative;z-index:10;}
.stat-card{background:#140826;border:2px solid #3d2870;border-radius:14px;padding:16px 24px;text-align:center;min-width:110px;box-shadow:0 4px 24px rgba(124,58,237,.2);transition:transform .3s,box-shadow .3s;cursor:default;}
.stat-card:hover{transform:translateY(-6px);box-shadow:0 8px 32px rgba(167,139,250,.3)}
.stat-num{font-family:'Press Start 2P',monospace;font-size:clamp(18px,4vw,28px);color:var(--purple);text-shadow:0 0 20px rgba(167,139,250,.5);display:block;}
.stat-label{font-size:11px;color:#9f8ec4;font-weight:600;margin-top:6px;display:block;letter-spacing:.5px}
.stack-area{padding:20px;text-align:center;position:relative;z-index:10;}
.stack-title{font-family:'Press Start 2P',monospace;font-size:9px;color:#9f8ec4;letter-spacing:2px;margin-bottom:16px;text-transform:uppercase;}
.stack-grid{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;max-width:700px;margin:0 auto}
.stack-item{display:flex;align-items:center;gap:8px;background:#1e0d3e;border:1.5px solid #3d2870;border-radius:10px;padding:8px 16px;font-size:13px;font-weight:600;color:#e2d9f3;transition:all .3s;cursor:default;}
.stack-item:hover{border-color:var(--purple);box-shadow:0 0 16px rgba(167,139,250,.25);transform:translateY(-3px)}
.stack-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}
.projects-section{padding:20px 20px 40px;position:relative;z-index:10;max-width:900px;margin:0 auto;width:100%;}
.section-header{font-family:'Press Start 2P',monospace;font-size:9px;color:#9f8ec4;letter-spacing:2px;text-align:center;margin-bottom:20px;}
.project-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:14px}
.project-card{background:#140826;border:1.5px solid #3d2870;border-radius:12px;padding:14px 16px;transition:all .3s;position:relative;overflow:hidden;cursor:default;}
.project-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--c,var(--purple));opacity:.6;}
.project-card:hover{border-color:var(--c,var(--purple));transform:translateY(-4px);box-shadow:0 8px 24px rgba(0,0,0,.3)}
.project-emoji{font-size:20px;margin-bottom:8px;display:block}
.project-name{font-size:13px;font-weight:700;color:#e2d9f3;margin-bottom:4px}
.project-desc{font-size:11px;color:#9f8ec4;line-height:1.5}
.store-links{display:flex;gap:6px;margin-top:10px}
.store-btn{font-size:9px;padding:3px 10px;border-radius:6px;border:1px solid;text-decoration:none;font-weight:600;transition:all .2s;}
.store-btn.play{color:#86efac;border-color:#86efac}
.store-btn.play:hover{background:rgba(134,239,172,.15)}
.store-btn.apple{color:#c4b5fd;border-color:#c4b5fd}
.store-btn.apple:hover{background:rgba(196,181,253,.15)}
.store-btn.internal{color:#9f8ec4;border-color:#9f8ec4}
.footer{background:#0a0612;border-top:1px solid #2d1b69;padding:30px 20px;text-align:center;position:relative;z-index:10;}
.footer-links{display:flex;flex-wrap:wrap;gap:14px;justify-content:center;margin-bottom:16px}
.footer-link{display:flex;align-items:center;gap:6px;text-decoration:none;font-size:12px;font-weight:600;padding:7px 16px;border-radius:20px;border:1.5px solid;transition:all .3s;}
.footer-link.port{color:var(--purple);border-color:var(--purple)}
.footer-link.port:hover{background:rgba(167,139,250,.1)}
.footer-link.li{color:#60a5fa;border-color:#60a5fa}
.footer-link.li:hover{background:rgba(96,165,250,.1)}
.footer-link.mail{color:var(--pink);border-color:var(--pink)}
.footer-link.mail:hover{background:rgba(244,114,182,.1)}
.footer-link.gh{color:#e2d9f3;border-color:#4a4080}
.footer-link.gh:hover{background:rgba(226,217,243,.08)}
.footer-copy{font-size:10px;color:#4a4080;font-family:'Press Start 2P',monospace;letter-spacing:1px}
@keyframes shootingStar{0%{transform:translateX(-100px) translateY(0);opacity:1}100%{transform:translateX(200px) translateY(80px);opacity:0}}
.shooting-star{position:fixed;width:80px;height:1.5px;background:linear-gradient(90deg,transparent,#a78bfa,white);border-radius:2px;animation:shootingStar var(--dur,2s) linear infinite;animation-delay:var(--del,0s);top:var(--top,20%);left:var(--left,30%);pointer-events:none;z-index:1;}
</style>
</head>
<body>

<div class="stars" id="stars"></div>
<div class="shooting-star" style="--dur:3s;--del:1s;--top:15%;--left:20%"></div>
<div class="shooting-star" style="--dur:4s;--del:5s;--top:8%;--left:50%"></div>
<div class="shooting-star" style="--dur:3.5s;--del:9s;--top:25%;--left:70%"></div>

<div class="scene">
  <div class="sky-area">
    <div class="moon"></div>
    <div class="title-board">
      <h1>NOUR OTHMAN</h1>
      <p>Full Stack Mobile Developer &amp; AI Engineer</p>
      <div class="badges">
        <span class="badge loc">📍 Damascus, Syria</span>
        <span class="badge gpa">🎓 90.5 GPA · ASPU University</span>
        <span class="badge avail">● Available for work</span>
      </div>
    </div>
  </div>

  <div class="stats-row">
    <div class="stat-card"><span class="stat-num">10+</span><span class="stat-label">Apps Shipped</span></div>
    <div class="stat-card"><span class="stat-num">6+</span><span class="stat-label">Technologies</span></div>
    <div class="stat-card"><span class="stat-num">90.5</span><span class="stat-label">GPA Score</span></div>
    <div class="stat-card"><span class="stat-num">2</span><span class="stat-label">App Stores</span></div>
  </div>

  <div class="park" id="park">
    <div class="skills-cloud">
      <span class="skill-pill" style="color:#60a5fa;border-color:#60a5fa;--fd:2.8s">Flutter</span>
      <span class="skill-pill" style="color:#f472b6;border-color:#f472b6;--fd:3.5s">Python</span>
      <span class="skill-pill" style="color:#fb923c;border-color:#fb923c;--fd:2.2s">Laravel</span>
      <span class="skill-pill" style="color:#fbbf24;border-color:#fbbf24;--fd:4s">Firebase</span>
      <span class="skill-pill" style="color:#a78bfa;border-color:#a78bfa;--fd:3.1s">PHP</span>
      <span class="skill-pill" style="color:#2dd4bf;border-color:#2dd4bf;--fd:2.6s">MySQL</span>
      <span class="skill-pill" style="color:#86efac;border-color:#86efac;--fd:3.8s">Dart</span>
      <span class="skill-pill" style="color:#c084fc;border-color:#c084fc;--fd:2.4s">BLoC</span>
    </div>

    <div class="tree tree-glow t2" style="left:5%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree t1" style="left:8%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree tree-glow t1" style="left:22%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree t3" style="left:25%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree tree-glow t2" style="right:6%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree t1" style="right:10%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
    <div class="tree t3" style="right:22%"><div class="tree-top"></div><div class="tree-trunk"></div></div>

    <div class="lamp" style="left:32%"><div class="lamp-head"></div><div class="lamp-pole" style="height:80px"></div></div>
    <div class="lamp" style="left:62%"><div class="lamp-head"></div><div class="lamp-pole" style="height:80px"></div></div>
    <div class="lamp" style="left:47%"><div class="lamp-head"></div><div class="lamp-pole" style="height:60px"></div></div>

    <div class="path"></div>

    <div class="bench" style="left:16%">
      <div class="bench-seat" style="width:60px"></div>
      <div class="bench-legs"><div class="bench-leg"></div><div class="bench-leg"></div></div>
    </div>
    <div class="bench" style="right:16%">
      <div class="bench-seat" style="width:60px"></div>
      <div class="bench-legs"><div class="bench-leg"></div><div class="bench-leg"></div></div>
    </div>

    <div class="sign" style="left:36%;bottom:60px">
      <div class="sign-board"><span>🤖</span><h3>About</h3><p>Full Stack Mobile<br/>Developer &amp; AI Eng.</p></div>
      <div class="sign-pole" style="height:40px"></div>
    </div>
    <div class="sign" style="right:32%;bottom:60px">
      <div class="sign-board"><span>🎓</span><h3>Education</h3><p>BSc Informatics Eng.<br/>AI Specialization</p></div>
      <div class="sign-pole" style="height:40px"></div>
    </div>

    <!-- Robot 1: Purple (main) -->
    <div class="robot" style="left:42%;bottom:75px;animation:bobUp 1.8s ease-in-out infinite">
      <div class="speech"><span class="tag">// Hello World</span><p>I build apps that live<br/>on your phone! 📱</p></div>
      <div class="robo-antenna"></div>
      <div class="robo-head" style="border-color:#a78bfa">
        <div class="robo-eyes">
          <div class="robo-eye" style="background:#a78bfa;box-shadow:0 0 6px #a78bfa"></div>
          <div class="robo-eye" style="background:#a78bfa;box-shadow:0 0 6px #a78bfa"></div>
        </div>
      </div>
      <div style="position:relative;display:flex;align-items:center">
        <div class="robo-arm" style="margin-right:2px;transform:rotate(15deg)"></div>
        <div class="robo-body"><div class="robo-chest" style="border-color:#a78bfa;box-shadow:0 0 8px rgba(167,139,250,.6)"></div></div>
        <div class="robo-arm" style="margin-left:2px;transform:rotate(-15deg)"></div>
      </div>
      <div class="robo-feet"><div class="robo-foot"></div><div class="robo-foot"></div></div>
    </div>

    <!-- Robot 2: Blue Flutter bot -->
    <div class="robot walks" style="left:18%;animation:patrol 10s linear infinite,bobUp 1.2s ease-in-out infinite">
      <div class="speech"><span class="tag">// Flutter</span><p>Foodify • Abo Store<br/>Nilz • Chamsale 🛍️</p></div>
      <div class="robo-antenna" style="background:#60a5fa"></div>
      <div class="robo-head" style="border-color:#60a5fa;background:#0f1f3d">
        <div class="robo-eyes">
          <div class="robo-eye" style="background:#60a5fa;box-shadow:0 0 6px #60a5fa"></div>
          <div class="robo-eye" style="background:#60a5fa;box-shadow:0 0 6px #60a5fa"></div>
        </div>
      </div>
      <div style="position:relative;display:flex;align-items:center">
        <div class="robo-arm" style="margin-right:2px;background:#0f1f3d;border-color:#60a5fa"></div>
        <div class="robo-body" style="border-color:#60a5fa;background:#0a1628"><div class="robo-chest" style="border-color:#60a5fa;box-shadow:0 0 8px rgba(96,165,250,.6)"></div></div>
        <div class="robo-arm" style="margin-left:2px;background:#0f1f3d;border-color:#60a5fa"></div>
      </div>
      <div class="robo-feet">
        <div class="robo-foot" style="background:#0f1f3d;border-color:#60a5fa"></div>
        <div class="robo-foot" style="background:#0f1f3d;border-color:#60a5fa"></div>
      </div>
    </div>

    <!-- Robot 3: Pink AI bot -->
    <div class="robot walks" style="right:20%;animation:patrol2 12s linear infinite reverse,bobUp 1.5s ease-in-out infinite">
      <div class="speech"><span class="tag">// AI Engine</span><p>ML Models • Python<br/>Smart Solutions 🧠</p></div>
      <div class="robo-antenna" style="background:#f472b6"></div>
      <div class="robo-head" style="border-color:#f472b6;background:#2d0f2a">
        <div class="robo-eyes">
          <div class="robo-eye" style="background:#f472b6;box-shadow:0 0 6px #f472b6;animation:blink 3s .5s infinite"></div>
          <div class="robo-eye" style="background:#f472b6;box-shadow:0 0 6px #f472b6;animation:blink 3s .5s infinite"></div>
        </div>
      </div>
      <div style="position:relative;display:flex;align-items:center">
        <div class="robo-arm" style="margin-right:2px;background:#2d0f2a;border-color:#f472b6;transform:rotate(-10deg)"></div>
        <div class="robo-body" style="border-color:#f472b6;background:#1a0820"><div class="robo-chest" style="border-color:#f472b6;box-shadow:0 0 8px rgba(244,114,182,.6)"></div></div>
        <div class="robo-arm" style="margin-left:2px;background:#2d0f2a;border-color:#f472b6;transform:rotate(10deg)"></div>
      </div>
      <div class="robo-feet">
        <div class="robo-foot" style="background:#2d0f2a;border-color:#f472b6"></div>
        <div class="robo-foot" style="background:#2d0f2a;border-color:#f472b6"></div>
      </div>
    </div>
  </div>

  <div class="stack-area">
    <p class="stack-title">★ Tech in the Park ★</p>
    <div class="stack-grid">
      <div class="stack-item"><div class="stack-dot" style="background:#60a5fa"></div>Flutter</div>
      <div class="stack-item"><div class="stack-dot" style="background:#3b82f6"></div>Dart</div>
      <div class="stack-item"><div class="stack-dot" style="background:#fbbf24"></div>Python</div>
      <div class="stack-item"><div class="stack-dot" style="background:#fb923c"></div>Laravel</div>
      <div class="stack-item"><div class="stack-dot" style="background:#818cf8"></div>PHP</div>
      <div class="stack-item"><div class="stack-dot" style="background:#2dd4bf"></div>MySQL</div>
      <div class="stack-item"><div class="stack-dot" style="background:#fbbf24"></div>Firebase</div>
      <div class="stack-item"><div class="stack-dot" style="background:#a78bfa"></div>BLoC / Clean Arch</div>
      <div class="stack-item"><div class="stack-dot" style="background:#f472b6"></div>REST APIs</div>
      <div class="stack-item"><div class="stack-dot" style="background:#86efac"></div>Git / GitHub</div>
    </div>
  </div>

  <div class="projects-section">
    <p class="section-header">★ Shipped to the Stores ★</p>
    <div class="project-grid">
      <div class="project-card" style="--c:#60a5fa">
        <span class="project-emoji">🍔</span><div class="project-name">Foodify</div>
        <div class="project-desc">Food delivery · Google Maps · real-time tracking · Firebase push</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.ninteysoft.foodify" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/ca/app/foodify/id6584520177" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#f472b6">
        <span class="project-emoji">🛡️</span><div class="project-name">Inanna Insure Iraq</div>
        <div class="project-desc">Insurance · PDF generation · dynamic forms · payments</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.ninteysoft.inanna" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/jo/app/insure-iraq/id6740625998" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#fbbf24">
        <span class="project-emoji">🛍️</span><div class="project-name">Abo Store</div>
        <div class="project-desc">E-commerce · optimized checkout · product recommendations</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.soft.ABO" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/ca/app/abo-store/id6444841672" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#2dd4bf">
        <span class="project-emoji">📢</span><div class="project-name">Mzad Dimashq</div>
        <div class="project-desc">Ads platform · advanced search · following system</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.soft.mzad" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/app/id6742141040" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#c084fc">
        <span class="project-emoji">📞</span><div class="project-name">SOA — Syriatel</div>
        <div class="project-desc">Enterprise app · customer tools · service management</div>
        <div class="store-links"><span class="store-btn internal">🔒 Internal</span></div>
      </div>
      <div class="project-card" style="--c:#fb923c">
        <span class="project-emoji">🛒</span><div class="project-name">Chamsale</div>
        <div class="project-desc">E-commerce · categories · favorites · user profiles</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.nintysoft.chamesale" class="store-btn play" target="_blank">▶ Play</a>
        </div>
      </div>
      <div class="project-card" style="--c:#86efac">
        <span class="project-emoji">🎓</span><div class="project-name">Leader Institute</div>
        <div class="project-desc">EdTech · course management · student progress tracking</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.new.qualifying_leaders" class="store-btn play" target="_blank">▶ Play</a>
        </div>
      </div>
      <div class="project-card" style="--c:#a78bfa">
        <span class="project-emoji">👥</span><div class="project-name">HR Management</div>
        <div class="project-desc">Dual-flow HR · face recognition · leave &amp; task tracking</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.ninteysoft.MTBW" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/ca/app/mtbw/id6746378501" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#60a5fa">
        <span class="project-emoji">🏨</span><div class="project-name">Nilz</div>
        <div class="project-desc">Hotel booking · real-time availability · comparison</div>
        <div class="store-links">
          <a href="https://play.google.com/store/apps/details?id=com.nintysoft.niles" class="store-btn play" target="_blank">▶ Play</a>
          <a href="https://apps.apple.com/ca/app/nilz/id6747636823" class="store-btn apple" target="_blank"> Apple</a>
        </div>
      </div>
      <div class="project-card" style="--c:#f472b6">
        <span class="project-emoji">🏠</span><div class="project-name">New Rental</div>
        <div class="project-desc">Property management · buy / sell / rent · tenant comms</div>
        <div class="store-links"><span class="store-btn internal">🔒 Internal</span></div>
      </div>
    </div>
  </div>

  <div class="footer">
    <div class="footer-links">
      <a href="https://nourothman.netlify.app/" class="footer-link port" target="_blank">🌐 Portfolio</a>
      <a href="https://www.linkedin.com/in/nour-othman-85758626a/" class="footer-link li" target="_blank">in LinkedIn</a>
      <a href="mailto:othmannour2001@gmail.com" class="footer-link mail">✉ Email</a>
      <a href="https://github.com/meory101" class="footer-link gh" target="_blank">⌥ GitHub · meory101</a>
    </div>
    <p class="footer-copy">© 2025 NOUR OTHMAN · NOUR.PARK</p>
  </div>
</div>

<script>
const starsEl = document.getElementById('stars');
for(let i=0;i<120;i++){
  const s = document.createElement('div');
  s.className = 'star';
  const size = Math.random()*3+1;
  s.style.cssText = `width:${size}px;height:${size}px;left:${Math.random()*100}%;top:${Math.random()*100}%;background:${['#fff','#c4b5fd','#fbbf24','#bfdbfe'][Math.floor(Math.random()*4)]};--d:${Math.random()*3+1.5}s;animation-delay:${Math.random()*3}s;`;
  starsEl.appendChild(s);
}
document.querySelectorAll('.stat-num').forEach(el => {
  const target = parseFloat(el.textContent);
  const isFloat = el.textContent.includes('.');
  const hasPl = el.textContent.includes('+');
  let current = 0;
  const step = target / 40;
  const timer = setInterval(() => {
    current = Math.min(current + step, target);
    el.textContent = isFloat ? current.toFixed(1) : Math.ceil(current) + (hasPl ? '+' : '');
    if(current >= target) clearInterval(timer);
  }, 40);
});
</script>
</body>
</html>
