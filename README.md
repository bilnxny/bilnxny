<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#000000">
<title>Muhammed Bilal TA — Cyber Security Mentor</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#000000;
  --green:#00ff41;
  --green-dim:#00b32d;
  --green-glow:0 0 10px rgba(0,255,65,.6);
  --green-soft:rgba(0,255,65,.1);
  --border:rgba(0,255,65,.25);
  --muted:#3d7a4a;
  --panel:rgba(0,20,8,.6);
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  font-family:'JetBrains Mono',monospace;
  background:var(--bg);
  color:var(--green);
  line-height:1.7;
  overflow-x:hidden;
  font-size:15px;
  min-height:100vh;
  position:relative;
}

/* MATRIX CANVAS */
#matrix{position:fixed;inset:0;z-index:0;opacity:.15;pointer-events:none}

/* SCANLINES OVERLAY */
body::after{
  content:'';position:fixed;inset:0;z-index:9999;pointer-events:none;
  background:repeating-linear-gradient(to bottom,rgba(0,0,0,0) 0,rgba(0,0,0,0) 2px,rgba(0,255,65,.03) 3px,rgba(0,255,65,.03) 4px);
}

/* BOOT SCREEN */
#boot{
  position:fixed;inset:0;z-index:10000;background:#000;
  padding:5vw;font-size:.85rem;color:var(--green);
  display:flex;align-items:flex-start;transition:opacity .6s,visibility .6s;
}
#boot.hide{opacity:0;visibility:hidden}
#bootText{white-space:pre-wrap;line-height:1.9;text-shadow:var(--green-glow)}
#bootText .ok{color:var(--green)}
#bootText .grant{color:#fff;font-weight:700;text-shadow:0 0 20px var(--green)}
.cursor{display:inline-block;width:9px;height:1em;background:var(--green);vertical-align:-2px;animation:blink 1s steps(1) infinite}
@keyframes blink{50%{opacity:0}}

/* WRAP */
.wrap{position:relative;z-index:2;max-width:1100px;margin:0 auto;padding:0 5%}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;z-index:900;
  background:rgba(0,0,0,.9);backdrop-filter:blur(12px);
  border-bottom:1px solid var(--border);
  padding:14px 5%;display:flex;justify-content:space-between;align-items:center;
  font-size:.85rem;
}
.nav-logo{
  color:var(--green);font-weight:700;text-shadow:var(--green-glow);
  display:flex;align-items:center;gap:10px;text-decoration:none;
}
.nav-logo::before{
  content:'';width:9px;height:9px;border-radius:50%;
  background:var(--green);box-shadow:0 0 12px var(--green);
  animation:pulse 1.6s infinite;
}
@keyframes pulse{50%{opacity:.3}}
.nav-links{display:flex;gap:22px;list-style:none}
.nav-links a{
  color:var(--muted);text-decoration:none;transition:all .25s;
  font-size:.82rem;position:relative;
}
.nav-links a:hover{color:var(--green);text-shadow:var(--green-glow)}
.nav-links a::before{content:'./';opacity:.5}
.menu-btn{
  display:none;background:none;border:1px solid var(--border);
  color:var(--green);font-family:inherit;font-size:1.1rem;
  padding:4px 10px;border-radius:5px;cursor:pointer;
}

/* HERO */
.hero{
  min-height:100vh;display:flex;align-items:center;
  padding:120px 0 60px;
}
.hero-grid{
  display:grid;grid-template-columns:1.3fr 1fr;gap:50px;
  align-items:center;width:100%;
}
.prompt{color:var(--muted);font-size:.95rem;margin-bottom:12px}
.prompt .u{color:var(--green)}
.prompt .p{color:var(--green)}
.prompt .c{color:#fff}

h1.name{
  font-size:clamp(2rem,5vw,3.4rem);font-weight:800;
  color:var(--green);text-shadow:var(--green-glow);
  line-height:1.1;letter-spacing:-.01em;
  margin-bottom:16px;
  position:relative;
}
h1.name::after{
  content:'_';animation:blink 1s steps(1) infinite;
}

.hero-desc{
  color:var(--muted);font-size:1rem;margin-bottom:28px;max-width:540px;
}
.hero-desc .hl{color:var(--green)}

.btn-row{display:flex;gap:12px;flex-wrap:wrap}
.btn{
  font-family:inherit;font-size:.85rem;padding:12px 24px;
  border-radius:6px;text-decoration:none;cursor:pointer;
  border:1px solid var(--green);background:transparent;
  color:var(--green);transition:all .25s;
  display:inline-flex;align-items:center;gap:8px;
}
.btn:hover{
  background:var(--green);color:#000;
  box-shadow:0 0 24px var(--green);transform:translateY(-2px);
}
.btn.solid{background:var(--green);color:#000;font-weight:700}
.btn.solid:hover{background:#3dff6d;box-shadow:0 0 30px var(--green)}

/* ID CARD */
.id-card{
  border:1px solid var(--border);border-radius:10px;
  background:var(--panel);backdrop-filter:blur(8px);
  overflow:hidden;
  box-shadow:0 0 40px rgba(0,255,65,.15);
}
.id-bar{
  display:flex;align-items:center;gap:7px;
  padding:10px 14px;background:rgba(0,255,65,.06);
  border-bottom:1px solid var(--border);font-size:.72rem;color:var(--muted);
}
.dot{width:11px;height:11px;border-radius:50%}
.dot.r{background:#ff5f56}.dot.y{background:#ffbd2e}.dot.g{background:#27c93f}
.id-body{padding:22px}
.id-top{display:flex;align-items:center;gap:16px;margin-bottom:20px}
.id-avatar{
  width:66px;height:66px;border-radius:8px;
  border:1px solid var(--green);
  display:flex;align-items:center;justify-content:center;
  font-weight:800;font-size:1.4rem;color:var(--green);
  background:rgba(0,255,65,.06);text-shadow:var(--green-glow);
}
.id-name{font-weight:700;color:var(--green);font-size:1rem}
.id-role{color:var(--muted);font-size:.78rem}
.id-rows{display:flex;flex-direction:column;gap:10px}
.id-row{
  display:flex;justify-content:space-between;gap:12px;
  border-bottom:1px dashed var(--border);padding-bottom:8px;font-size:.8rem;
}
.id-row:last-child{border-bottom:none}
.id-k{color:var(--muted)}
.id-v{color:var(--green);text-align:right}

/* SECTIONS */
section{padding:80px 0;position:relative}
.sec-tag{color:var(--green-dim);font-size:.82rem;margin-bottom:8px}
.sec-tag::before{content:'// ';opacity:.6}
h2.sec{
  font-size:clamp(1.5rem,3.5vw,2.1rem);font-weight:700;
  color:var(--green);text-shadow:var(--green-glow);
  margin-bottom:36px;
}
h2.sec::before{content:'> ';opacity:.6}

/* ABOUT */
.about p{margin-bottom:16px;color:var(--green);opacity:.85;font-size:.95rem}
.about p .hl{color:#fff;font-weight:600}
.about-tags{display:flex;flex-wrap:wrap;gap:8px;margin-top:22px}
.about-tag{
  padding:6px 14px;border:1px solid var(--border);border-radius:100px;
  font-size:.75rem;color:var(--green);background:rgba(0,255,65,.04);
}

/* TOOLS GRID */
.tools{
  display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
  gap:14px;
}
.tool-cat{
  border:1px solid var(--border);border-radius:8px;
  background:var(--panel);padding:18px;
  transition:all .3s;
}
.tool-cat:hover{
  border-color:var(--green);
  box-shadow:0 0 24px rgba(0,255,65,.2);
  transform:translateY(-4px);
}
.tool-cat h3{
  font-size:.9rem;color:var(--green);margin-bottom:12px;
  text-shadow:var(--green-glow);font-weight:700;
}
.tool-list{display:flex;flex-wrap:wrap;gap:6px}
.tool{
  font-size:.72rem;padding:4px 10px;border-radius:4px;
  background:rgba(0,255,65,.08);
  border:1px solid rgba(0,255,65,.2);
  color:var(--green);transition:all .2s;
}
.tool:hover{background:var(--green);color:#000}

/* SKILL BARS */
.skills{display:flex;flex-direction:column;gap:16px}
.skill{display:flex;flex-direction:column;gap:6px}
.skill-head{display:flex;justify-content:space-between;font-size:.85rem}
.skill-name{color:var(--green);font-weight:600}
.skill-pct{color:var(--muted);font-size:.78rem}
.bar{
  height:6px;background:rgba(0,255,65,.1);border-radius:3px;
  overflow:hidden;
}
.bar-fill{
  height:100%;width:0;
  background:linear-gradient(90deg,var(--green-dim),var(--green));
  box-shadow:0 0 12px var(--green);
  transition:width 1.4s cubic-bezier(.2,.8,.2,1);
}

/* CONTACT */
.contact{
  border:1px solid var(--border);border-radius:12px;
  padding:50px 32px;text-align:center;
  background:
    radial-gradient(circle at 50% 0%,rgba(0,255,65,.08),transparent 70%),
    var(--panel);
}
.contact h2{color:var(--green);text-shadow:var(--green-glow);font-size:1.8rem;margin-bottom:14px}
.contact p{color:var(--muted);max-width:520px;margin:0 auto 28px;font-size:.9rem}
.contact-links{display:flex;justify-content:center;gap:12px;flex-wrap:wrap}
.contact-links a{
  padding:11px 22px;border:1px solid var(--green);border-radius:6px;
  color:var(--green);text-decoration:none;font-size:.82rem;
  transition:all .25s;background:transparent;display:inline-flex;align-items:center;gap:8px;
}
.contact-links a:hover{background:var(--green);color:#000;box-shadow:0 0 20px var(--green)}

/* FOOTER */
footer{
  text-align:center;padding:32px 5%;
  border-top:1px solid var(--border);
  color:var(--muted);font-size:.75rem;position:relative;z-index:2;
}
footer .g{color:var(--green)}

/* REVEAL */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .8s,transform .8s}
.reveal.on{opacity:1;transform:translateY(0)}

/* SCROLL TOP */
#toTop{
  position:fixed;bottom:22px;right:22px;z-index:800;
  width:46px;height:46px;border-radius:50%;
  background:#000;border:1px solid var(--green);color:var(--green);
  font-size:1.2rem;cursor:pointer;display:none;
  align-items:center;justify-content:center;
  box-shadow:0 0 20px rgba(0,255,65,.4);transition:all .25s;
}
#toTop.show{display:flex}
#toTop:hover{background:var(--green);color:#000}

/* MOBILE MENU */
@media (max-width:880px){
  .hero-grid{grid-template-columns:1fr}
  .nav-links{
    position:fixed;top:58px;right:-110%;
    flex-direction:column;background:rgba(0,0,0,.98);
    border:1px solid var(--border);border-radius:8px;
    padding:20px 26px;gap:16px;min-width:200px;
    transition:right .3s;
  }
  .nav-links.open{right:5%}
  .menu-btn{display:block}
  h1.name{font-size:clamp(1.8rem,8vw,2.6rem)}
  .hero{padding:100px 0 40px}
  section{padding:60px 0}
  .contact{padding:36px 20px}
  .id-card{max-width:100%}
}
@media (max-width:480px){
  body{font-size:14px}
  .btn{padding:11px 18px;font-size:.8rem}
  .wrap{padding:0 4%}
}
</style>
</head>
<body>

<canvas id="matrix"></canvas>
<div id="boot"><pre id="bootText"></pre></div>

<nav>
  <a href="#home" class="nav-logo">root@bilal</a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#about">about</a></li>
    <li><a href="#tools">tools</a></li>
    <li><a href="#skills">skills</a></li>
    <li><a href="#contact">contact</a></li>
  </ul>
  <button class="menu-btn" id="menuBtn">[=]</button>
</nav>

<!-- HERO -->
<header class="hero" id="home">
  <div class="wrap">
    <div class="hero-grid">
      <div>
        <div class="prompt">
          <span class="u">visitor</span>@<span class="p">bilal</span>:~$ <span class="c">whoami</span>
        </div>
        <h1 class="name">Muhammed Bilal TA</h1>
        <p class="hero-desc">
          <span class="hl">Cyber Security Mentor</span> ·
          <span class="hl">Red Team Operator</span> ·
          <span class="hl">Bug Hunter</span><br>
          Kerala based hacker. I break systems — legally, ethically, relentlessly.
        </p>
        <div class="btn-row">
          <a href="#tools" class="btn solid">./show_arsenal</a>
          <a href="#contact" class="btn">--contact</a>
        </div>
      </div>

      <div class="id-card">
        <div class="id-bar">
          <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
          <span style="margin-left:10px">identity.json</span>
        </div>
        <div class="id-body">
          <div class="id-top">
            <div class="id-avatar">MB</div>
            <div>
              <div class="id-name">Muhammed Bilal TA</div>
              <div class="id-role">root@kerala</div>
            </div>
          </div>
          <div class="id-rows">
            <div class="id-row"><span class="id-k">STATUS</span><span class="id-v">ONLINE</span></div>
            <div class="id-row"><span class="id-k">LOCATION</span><span class="id-v">Kerala, India</span></div>
            <div class="id-row"><span class="id-k">ROLE</span><span class="id-v">Red Teamer</span></div>
            <div class="id-row"><span class="id-k">SHELL</span><span class="id-v">/bin/bash</span></div>
            <div class="id-row"><span class="id-k">UPTIME</span><span class="id-v" id="uptime">0s</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</header>

<!-- ABOUT -->
<section id="about" class="reveal">
  <div class="wrap">
    <div class="sec-tag">cat about.md</div>
    <h2 class="sec">About Me</h2>
    <div class="about">
      <p>
        I'm <span class="hl">Muhammed Bilal TA</span> — Penetration Tester,
        Red Team Operator, and Bug Hunter based in <span class="hl">Kerala, India</span>.
      </p>
      <p>
        3+ years breaking systems to make them safer. Web applications,
        networks, Active Directory — I hunt the vulnerabilities others miss.
        I also mentor beginners from zero to their first bug bounty payout.
      </p>
      <p>
        <span class="hl">What I do:</span> Bug Bounty · Red Teaming · OSINT · Mentoring
      </p>
      <div class="about-tags">
        <span class="about-tag">Web Exploitation</span>
        <span class="about-tag">Active Directory</span>
        <span class="about-tag">Network Pentesting</span>
        <span class="about-tag">OSINT</span>
        <span class="about-tag">Bug Bounty</span>
        <span class="about-tag">Mentoring</span>
      </div>
    </div>
  </div>
</section>

<!-- TOOLS -->
<section id="tools" class="reveal">
  <div class="wrap">
    <div class="sec-tag">ls -la /arsenal</div>
    <h2 class="sec">Offensive Arsenal</h2>

    <div class="tools">
      <div class="tool-cat">
        <h3>🔴 Recon & OSINT</h3>
        <div class="tool-list">
          <span class="tool">Nmap</span>
          <span class="tool">Amass</span>
          <span class="tool">Subfinder</span>
          <span class="tool">theHarvester</span>
          <span class="tool">Shodan</span>
          <span class="tool">Maltego</span>
          <span class="tool">SpiderFoot</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Web Exploitation</h3>
        <div class="tool-list">
          <span class="tool">Burp Suite Pro</span>
          <span class="tool">OWASP ZAP</span>
          <span class="tool">SQLMap</span>
          <span class="tool">FFUF</span>
          <span class="tool">Nuclei</span>
          <span class="tool">WPScan</span>
          <span class="tool">Commix</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Exploitation</h3>
        <div class="tool-list">
          <span class="tool">Metasploit</span>
          <span class="tool">Cobalt Strike</span>
          <span class="tool">Impacket</span>
          <span class="tool">BloodHound</span>
          <span class="tool">Mimikatz</span>
          <span class="tool">Responder</span>
          <span class="tool">Sliver C2</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Password Attacks</h3>
        <div class="tool-list">
          <span class="tool">Hashcat</span>
          <span class="tool">John the Ripper</span>
          <span class="tool">Hydra</span>
          <span class="tool">Medusa</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Wireless & Network</h3>
        <div class="tool-list">
          <span class="tool">Aircrack-ng</span>
          <span class="tool">Wireshark</span>
          <span class="tool">Bettercap</span>
          <span class="tool">Kismet</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Environment & Code</h3>
        <div class="tool-list">
          <span class="tool">Kali Linux</span>
          <span class="tool">Parrot OS</span>
          <span class="tool">BlackArch</span>
          <span class="tool">Python</span>
          <span class="tool">Bash</span>
          <span class="tool">PowerShell</span>
          <span class="tool">Docker</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Databases</h3>
        <div class="tool-list">
          <span class="tool">MySQL</span>
          <span class="tool">PostgreSQL</span>
          <span class="tool">MongoDB</span>
          <span class="tool">Redis</span>
        </div>
      </div>

      <div class="tool-cat">
        <h3>🔴 Platforms</h3>
        <div class="tool-list">
          <span class="tool">HackTheBox</span>
          <span class="tool">TryHackMe</span>
          <span class="tool">HackerOne</span>
          <span class="tool">Bugcrowd</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" class="reveal">
  <div class="wrap">
    <div class="sec-tag">cat skills.json</div>
    <h2 class="sec">Skills</h2>
    <div class="skills">
      <div class="skill">
        <div class="skill-head"><span class="skill-name">Web Application Pentesting</span><span class="skill-pct" data-pct="92">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="92"></div></div>
      </div>
      <div class="skill">
        <div class="skill-head"><span class="skill-name">Network & Active Directory</span><span class="skill-pct" data-pct="85">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="85"></div></div>
      </div>
      <div class="skill">
        <div class="skill-head"><span class="skill-name">Bug Bounty Hunting</span><span class="skill-pct" data-pct="88">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="88"></div></div>
      </div>
      <div class="skill">
        <div class="skill-head"><span class="skill-name">OSINT & Reconnaissance</span><span class="skill-pct" data-pct="90">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="90"></div></div>
      </div>
      <div class="skill">
        <div class="skill-head"><span class="skill-name">Python / Bash Automation</span><span class="skill-pct" data-pct="82">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="82"></div></div>
      </div>
      <div class="skill">
        <div class="skill-head"><span class="skill-name">Mentoring & Teaching</span><span class="skill-pct" data-pct="94">0%</span></div>
        <div class="bar"><div class="bar-fill" data-w="94"></div></div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="reveal">
  <div class="wrap">
    <div class="contact">
      <div class="sec-tag" style="display:inline-block">ping bilal</div>
      <h2>Establish Connection</h2>
      <p>Open to collaboration, bug bounty discussions, and mentoring. Reach out — I respond.</p>
      <div class="contact-links">
        <a href="mailto:muhanmedbilallalu@gmail.com">✉ Email</a>
        <a href="https://github.com/bilnxny" target="_blank">⌨ GitHub</a>
        <a href="https://youtube.com/channel/UCIExxjGdg6T17w3vWbvKGdg" target="_blank">▶ YouTube</a>
        <a href="https://instagram.com/bilxnvyy" target="_blank">◈ Instagram</a>
      </div>
    </div>
  </div>
</section>

<footer>
  <span class="g">root@bilal:~#</span> exit &nbsp;·&nbsp; © <span id="yr"></span> Muhammed Bilal TA &nbsp;·&nbsp;
  <span class="g">HACK THE PLANET 🌍</span>
</footer>

<button id="toTop">↑</button>

<script>
/* YEAR */
document.getElementById('yr').textContent = new Date().getFullYear();

/* MATRIX RAIN */
(function(){
  const c = document.getElementById('matrix'), ctx = c.getContext('2d');
  const glyphs = 'アィウェオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワン0123456789ABCDEF';
  const size = 14;
  let cols = 0, drops = [];
  function resize(){
    c.width = window.innerWidth;
    c.height = window.innerHeight;
    cols = Math.floor(c.width / size);
    drops = new Array(cols).fill(1).map(()=>Math.random()*-100);
  }
  resize(); window.addEventListener('resize', resize);
  function draw(){
    ctx.fillStyle = 'rgba(0,0,0,.08)';
    ctx.fillRect(0,0,c.width,c.height);
    ctx.font = size + 'px monospace';
    for (let i=0;i<cols;i++){
      const ch = glyphs[Math.floor(Math.random()*glyphs.length)];
      const x = i*size, y = drops[i]*size;
      ctx.fillStyle = Math.random()>.985 ? '#ffffff' : '#00ff41';
      ctx.fillText(ch,x,y);
      if (y > c.height && Math.random() > .975) drops[i] = 0;
      drops[i]++;
    }
  }
  setInterval(draw, 55);
})();

/* BOOT SEQUENCE */
(function(){
  const boot = document.getElementById('boot'), out = document.getElementById('bootText');
  const lines = [
    {t:'[  OK  ] ',c:'ok',m:'Initializing secure shell...'},
    {t:'[  OK  ] ',c:'ok',m:'Loading kernel modules...'},
    {t:'[  OK  ] ',c:'ok',m:'Mounting /dev/portfolio...'},
    {t:'[  OK  ] ',c:'ok',m:'Establishing encrypted tunnel...'},
    {t:'[ WARN ] ',c:'ok',m:'Firewall detected — probing ports...'},
    {t:'[  OK  ] ',c:'ok',m:'Handshake complete.'},
    {t:'[ GRANT] ',c:'grant',m:'ACCESS GRANTED'},
    {t:'',c:'',m:''},
    {t:'',c:'',m:'> Welcome, visitor.'}
  ];
  let i=0, buf='';
  function step(){
    if (i<lines.length){
      const L=lines[i];
      buf += '<span class="'+L.c+'">'+L.t+'</span>'+L.m+'\n';
      out.innerHTML = buf + '<span class="cursor"></span>';
      i++;
      setTimeout(step, 220 + Math.random()*180);
    } else {
      setTimeout(()=>boot.classList.add('hide'), 700);
    }
  }
  setTimeout(step, 250);
  boot.addEventListener('click', ()=>boot.classList.add('hide'));
  setTimeout(()=>boot.classList.add('hide'), 5200);
})();

/* MOBILE MENU */
const menuBtn = document.getElementById('menuBtn');
const navLinks = document.getElementById('navLinks');
menuBtn.addEventListener('click', ()=>navLinks.classList.toggle('open'));
navLinks.querySelectorAll('a').forEach(a=>a.addEventListener('click',()=>navLinks.classList.remove('open')));

/* REVEAL ON SCROLL */
const io = new IntersectionObserver(es=>es.forEach(e=>{
  if(e.isIntersecting){ e.target.classList.add('on'); io.unobserve(e.target); }
}),{threshold:.12});
document.querySelectorAll('.reveal').forEach(el=>io.observe(el));

/* SKILL BARS */
const skillIO = new IntersectionObserver(es=>es.forEach(e=>{
  if(e.isIntersecting){
    const bar = e.target.querySelector('.bar-fill');
    const pct = e.target.querySelector('.skill-pct');
    const target = parseInt(bar.dataset.w,10);
    bar.style.width = target + '%';
    let n=0;
    const tick = setInterval(()=>{
      n += Math.max(1, Math.round(target/30));
      if(n>=target){ n=target; clearInterval(tick); }
      pct.textContent = n+'%';
    }, 30);
    skillIO.unobserve(e.target);
  }
}),{threshold:.4});
document.querySelectorAll('.skill').forEach(el=>skillIO.observe(el));

/* UPTIME */
const start = Date.now();
setInterval(()=>{
  const s = Math.floor((Date.now()-start)/1000);
  const h = Math.floor(s/3600), m = Math.floor((s%3600)/60), sec = s%60;
  const el = document.getElementById('uptime');
  if(el) el.textContent = (h?h+'h ':'') + (m?m+'m ':'') + sec+'s';
}, 1000);

/* SCROLL TOP */
const toTop = document.getElementById('toTop');
window.addEventListener('scroll', ()=>{
  toTop.classList.toggle('show', window.scrollY > 500);
});
toTop.addEventListener('click', ()=>window.scrollTo({top:0,behavior:'smooth'}));
</script>
</body>
</html>
