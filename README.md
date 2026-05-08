<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tuan Muda Dullz — TKJ Portfolio</title>
<link rel="icon" type="image/png" href="logo.png">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Space+Grotesk:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
--bg:#0B0E14;
--surface:#111520;
--glass:rgba(17,21,32,0.7);
--accent:#00D2FF;
--accent2:#0090B5;
--text:#E5E7EB;
--muted:#6B7280;
--border:rgba(0,210,255,0.15);
--glow:0 0 20px rgba(0,210,255,0.3);
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'Space Grotesk',sans-serif;overflow-x:hidden;cursor:none}

#cursor{position:fixed;width:8px;height:8px;background:var(--accent);border-radius:50%;pointer-events:none;z-index:9999;transition:transform 0.1s;mix-blend-mode:screen}
#cursor-ring{position:fixed;width:32px;height:32px;border:1px solid var(--accent);border-radius:50%;pointer-events:none;z-index:9998;transition:all 0.15s;opacity:0.5}

#preloader{position:fixed;inset:0;background:var(--bg);z-index:9000;display:flex;flex-direction:column;align-items:center;justify-content:center;transition:opacity 0.8s ease}
#preloader.hide{opacity:0;pointer-events:none}
.preloader-svg{width:120px;height:120px}
.preloader-text{font-family:'JetBrains Mono',monospace;color:var(--accent);font-size:11px;margin-top:16px;letter-spacing:2px}

body::before{content:'';position:fixed;inset:0;background-image:linear-gradient(rgba(0,210,255,0.03) 1px,transparent 1px),linear-gradient(90deg,rgba(0,210,255,0.03) 1px,transparent 1px);background-size:40px 40px;pointer-events:none;z-index:0}

nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:16px 40px;display:flex;justify-content:space-between;align-items:center;backdrop-filter:blur(12px);-webkit-backdrop-filter:blur(12px);border-bottom:1px solid var(--border);background:rgba(11,14,20,0.8)}
.nav-logo{font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--accent);letter-spacing:1px}
.nav-links{display:flex;gap:32px;list-style:none}
.nav-links a{color:var(--muted);text-decoration:none;font-size:13px;letter-spacing:1px;transition:color 0.2s;font-family:'JetBrains Mono',monospace}
.nav-links a:hover{color:var(--accent)}
.nav-status{display:flex;align-items:center;gap:8px;font-size:11px;color:var(--muted);font-family:'JetBrains Mono',monospace}
.status-dot{width:6px;height:6px;background:#00FF88;border-radius:50%;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.3}}

section{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:100px 40px 60px;position:relative;z-index:1}

#hero{flex-direction:column;text-align:center;padding-bottom:80px}
.hero-badge{font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--accent);letter-spacing:3px;border:1px solid var(--border);padding:6px 16px;display:inline-block;margin-bottom:32px;animation:fadeUp 0.6s ease both}
.hero-title{font-size:clamp(48px,8vw,88px);font-weight:700;line-height:1;letter-spacing:-2px;animation:fadeUp 0.6s 0.1s ease both}
.hero-title span{color:var(--accent);text-shadow:0 0 20px rgba(0,210,255,0.5)}
.hero-sub{height:28px;font-family:'JetBrains Mono',monospace;font-size:14px;color:var(--muted);margin-top:20px;animation:fadeUp 0.6s 0.2s ease both}
.cursor-blink{display:inline-block;width:2px;height:16px;background:var(--accent);margin-left:2px;animation:blink 1s infinite;vertical-align:middle}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.hero-desc{max-width:520px;color:var(--muted);line-height:1.7;margin-top:24px;animation:fadeUp 0.6s 0.3s ease both}
.hero-cta{margin-top:40px;display:flex;gap:16px;justify-content:center;animation:fadeUp 0.6s 0.4s ease both}
.btn-primary{background:var(--accent);color:#000;padding:12px 28px;font-weight:700;font-size:13px;letter-spacing:1px;border:none;cursor:none;transition:all 0.2s;font-family:'Space Grotesk',sans-serif}
.btn-primary:hover{background:#fff;transform:translateY(-2px)}
.btn-outline{border:1px solid var(--border);color:var(--text);padding:12px 28px;font-size:13px;letter-spacing:1px;cursor:none;background:transparent;transition:all 0.2s;font-family:'Space Grotesk',sans-serif}
.btn-outline:hover{border-color:var(--accent);color:var(--accent)}
.scroll-line{position:relative;display:flex;flex-direction:column;align-items:center;gap:8px;font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--muted);letter-spacing:2px;margin-top:48px}
.scroll-line::after{content:'';width:1px;height:40px;background:linear-gradient(to bottom,var(--accent),transparent);animation:scrollLine 1.5s ease infinite}
@keyframes scrollLine{0%{transform:scaleY(0);transform-origin:top}50%{transform:scaleY(1);transform-origin:top}100%{transform:scaleY(0);transform-origin:bottom}}

.section-header{margin-bottom:60px;text-align:center}
.section-label{font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--accent);letter-spacing:3px;margin-bottom:12px}
.section-title{font-size:clamp(32px,5vw,48px);font-weight:700;letter-spacing:-1px}
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:40px;max-width:900px;width:100%;align-items:center}
.about-card{background:var(--glass);backdrop-filter:blur(12px);border:1px solid var(--border);padding:32px;position:relative}
.about-card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--accent),transparent)}
.about-id{font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--accent);margin-bottom:16px}
.about-name{font-size:28px;font-weight:700;margin-bottom:8px}
.about-detail{font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);line-height:2}
.about-detail span{color:var(--accent)}
.about-info p{color:var(--muted);line-height:1.8;font-size:15px;margin-bottom:16px}
.tag{display:inline-block;font-family:'JetBrains Mono',monospace;font-size:10px;border:1px solid var(--border);padding:4px 10px;color:var(--accent);margin:4px 4px 4px 0}

.skills-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:16px;max-width:960px;width:100%}
.skill-card{background:var(--glass);border:1px solid var(--border);padding:24px 20px;position:relative;overflow:hidden;transition:all 0.3s ease;transform-style:preserve-3d}
.skill-card::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at var(--mx,50%) var(--my,50%),rgba(0,210,255,0.08),transparent 60%);opacity:0;transition:opacity 0.3s}
.skill-card:hover::before{opacity:1}
.skill-card:hover{border-color:rgba(0,210,255,0.4);transform:translateY(-4px);box-shadow:0 8px 32px rgba(0,210,255,0.1)}
.skill-icon{font-size:28px;margin-bottom:12px}
.skill-name{font-weight:700;font-size:15px;margin-bottom:6px}
.skill-level{font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--accent);margin-bottom:12px}
.skill-bar{height:2px;background:rgba(255,255,255,0.08);position:relative;overflow:hidden}
.skill-bar-fill{height:100%;background:linear-gradient(90deg,#0090B5,#00D2FF);transform:scaleX(0);transform-origin:left;transition:transform 1s cubic-bezier(0.4,0,0.2,1)}
.skill-card.visible .skill-bar-fill{transform:scaleX(1)}

.projects-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:24px;max-width:960px;width:100%}
.project-card{background:var(--glass);border:1px solid var(--border);overflow:hidden;position:relative;transition:all 0.3s}
.project-card:hover{transform:translateY(-6px);border-color:rgba(0,210,255,0.35);box-shadow:0 16px 48px rgba(0,0,0,0.4)}
.project-header{padding:20px 24px 16px;border-bottom:1px solid var(--border)}
.project-id{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--muted);margin-bottom:8px}
.project-title{font-size:17px;font-weight:700}
.project-body{padding:16px 24px 20px}
.project-desc{font-size:14px;color:var(--muted);line-height:1.7;margin-bottom:16px}
.project-tags{display:flex;flex-wrap:wrap;gap:6px}
.project-tag{font-family:'JetBrains Mono',monospace;font-size:10px;padding:3px 8px;border:1px solid var(--border);color:var(--accent)}
.project-corner{position:absolute;top:0;right:0;width:40px;height:40px;overflow:hidden}
.project-corner::before{content:'';position:absolute;top:0;right:0;width:0;height:0;border-top:40px solid var(--accent);border-left:40px solid transparent;opacity:0.6}

.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;max-width:800px;width:100%}
.contact-item{background:var(--glass);border:1px solid var(--border);padding:24px;display:flex;align-items:center;gap:16px;transition:all 0.2s}
.contact-item:hover{border-color:rgba(0,210,255,0.4);transform:translateX(4px)}
.contact-icon{width:40px;height:40px;border:1px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;color:var(--accent)}
.contact-label{font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--muted);margin-bottom:4px}
.contact-value{font-size:14px;font-weight:600}

footer{position:relative;z-index:1;padding:24px 40px;border-top:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--muted)}
footer span{color:var(--accent)}

@keyframes fadeUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:translateY(0)}}
.reveal{opacity:0;transform:translateY(32px);transition:all 0.6s cubic-bezier(0.4,0,0.2,1)}
.reveal.visible{opacity:1;transform:translateY(0)}
.reveal-delay-1{transition-delay:0.1s}
.reveal-delay-2{transition-delay:0.2s}
.reveal-delay-3{transition-delay:0.3s}
.reveal-delay-4{transition-delay:0.4s}

@media(max-width:640px){
  nav{padding:12px 20px}
  .nav-links{display:none}
  section{padding:80px 20px 40px}
  #hero{padding-bottom:40px}
  .hero-cta{flex-direction:column;align-items:center;gap:12px;width:100%}
  .btn-primary,.btn-outline{width:100%;max-width:280px;text-align:center}
  .about-grid,.contact-grid{grid-template-columns:1fr}
  .skills-grid{grid-template-columns:1fr 1fr}
  footer{flex-direction:column;gap:8px;text-align:center;padding:16px 20px}
  .scroll-line{margin-top:32px}
}
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>

<div id="preloader">
  <svg class="preloader-svg" viewBox="0 0 120 120" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="60" cy="60" r="50" stroke="rgba(0,210,255,0.1)" stroke-width="1"/>
    <circle cx="60" cy="60" r="50" stroke="#00D2FF" stroke-width="1.5" stroke-dasharray="314" stroke-dashoffset="314" stroke-linecap="round">
      <animate attributeName="stroke-dashoffset" from="314" to="0" dur="1.8s" ease="ease-in-out" fill="freeze"/>
    </circle>
    <circle cx="60" cy="60" r="30" stroke="rgba(0,210,255,0.15)" stroke-width="1"/>
    <circle r="3" fill="#00D2FF">
      <animateMotion dur="2s" repeatCount="indefinite">
        <mpath href="#orbit1"/>
      </animateMotion>
    </circle>
    <circle r="2" fill="rgba(0,210,255,0.5)">
      <animateMotion dur="1.4s" repeatCount="indefinite" begin="0.7s">
        <mpath href="#orbit2"/>
      </animateMotion>
    </circle>
    <defs>
      <path id="orbit1" d="M60,10 A50,50 0 1,1 59.99,10"/>
      <path id="orbit2" d="M60,30 A30,30 0 1,0 59.99,30"/>
    </defs>
    <rect x="52" y="52" width="16" height="16" fill="none" stroke="#00D2FF" stroke-width="1">
      <animateTransform attributeName="transform" type="rotate" from="0 60 60" to="45 60 60" dur="1.8s" fill="freeze"/>
    </rect>
    <circle cx="60" cy="60" r="3" fill="#00D2FF">
      <animate attributeName="opacity" values="0;1;0" dur="1s" repeatCount="indefinite"/>
    </circle>
  </svg>
  <div class="preloader-text">INITIALIZING SYSTEM...</div>
</div>

<nav>
  <div class="nav-logo">// TUAN MUDA DULLZ</div>
  <ul class="nav-links">
    <li><a href="#about">ABOUT</a></li>
    <li><a href="#skills">SKILLS</a></li>
    <li><a href="#projects">PROJECTS</a></li>
    <li><a href="#contact">CONTACT</a></li>
  </ul>
  <div class="nav-status">
    <div class="status-dot"></div>
    SYSTEM ONLINE
  </div>
</nav>

<section id="hero">
  <div class="hero-badge">// SMK KARYA GUNA 2 BEKASI — 11 TKJ 2</div>
  <h1 class="hero-title">Tuan Muda<br><span>Dullz</span></h1>
  <div class="hero-sub" id="typing-target"><span id="typed-text"></span><span class="cursor-blink"></span></div>
  <p class="hero-desc">Siswa berdedikasi di bidang Teknik Komputer Jaringan — membangun fondasi kuat di jaringan, keamanan siber, dan pengembangan web.</p>
  <div class="hero-cta">
    <button class="btn-primary" onclick="document.getElementById('projects').scrollIntoView({behavior:'smooth'})">VIEW PROJECTS</button>
    <button class="btn-outline" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">CONTACT ME</button>
  </div>
  <div class="scroll-line">SCROLL</div>
</section>

<section id="about">
  <div style="max-width:960px;width:100%">
    <div class="section-header reveal">
      <div class="section-label">// 01. PROFILE</div>
      <h2 class="section-title">About Me</h2>
    </div>
    <div class="about-grid">
      <div class="about-card reveal reveal-delay-1">
        <div class="about-id">ID: TMD-2025-TKJ2</div>
        <div class="about-name">Tuan Muda Dullz</div>
        <div class="about-detail">
          <div>SEKOLAH: <span>SMK Karya Guna 2 Bekasi</span></div>
          <div>KELAS: <span>11 TKJ 2</span></div>
          <div>JURUSAN: <span>Teknik Komputer Jaringan</span></div>
          <div>STATUS: <span>AKTIF</span></div>
          <div>LOKASI: <span>Bekasi, Jawa Barat</span></div>
        </div>
        <div style="margin-top:20px;display:flex;flex-wrap:wrap;gap:4px">
          <span class="tag">NETWORKING</span>
          <span class="tag">WEB DEV</span>
          <span class="tag">LINUX</span>
          <span class="tag">SECURITY</span>
        </div>
      </div>
      <div class="about-info reveal reveal-delay-2">
        <p>Siswa TKJ yang antusias dengan passion di bidang teknologi jaringan dan pengembangan sistem. Selalu bersemangat untuk belajar hal-hal baru dan menghadapi tantangan teknis.</p>
        <p>Berfokus pada membangun skill yang relevan di dunia industri — dari konfigurasi router hingga membangun aplikasi web yang efisien dan aman.</p>
        <p style="font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent);border-left:2px solid var(--accent);padding-left:12px;line-height:2">"Belajar, Berkarya, Berkembang"</p>
      </div>
    </div>
  </div>
</section>

<section id="skills">
  <div style="max-width:960px;width:100%;display:flex;flex-direction:column;align-items:center">
    <div class="section-header reveal">
      <div class="section-label">// 02. CAPABILITIES</div>
      <h2 class="section-title">Skill Matrix</h2>
    </div>
    <div class="skills-grid" id="skills-grid"></div>
  </div>
</section>

<section id="projects">
  <div style="max-width:960px;width:100%;display:flex;flex-direction:column;align-items:center">
    <div class="section-header reveal">
      <div class="section-label">// 03. DEPLOYMENTS</div>
      <h2 class="section-title">Projects</h2>
    </div>
    <div class="projects-grid" id="projects-grid"></div>
  </div>
</section>

<section id="contact">
  <div style="max-width:960px;width:100%;display:flex;flex-direction:column;align-items:center">
    <div class="section-header reveal">
      <div class="section-label">// 04. CONNECT</div>
      <h2 class="section-title">Get In Touch</h2>
    </div>
    <div class="contact-grid">
      <div class="contact-item reveal reveal-delay-1">
        <div class="contact-icon">📧</div>
        <div><div class="contact-label">EMAIL</div><div class="contact-value">abdulahwijaya6@email.com</div></div>
      </div>
      <div class="contact-item reveal reveal-delay-2">
        <div class="contact-icon">💬</div>
        <div><div class="contact-label">WHATSAPP</div><div class="contact-value">+62 </div></div>
      </div>
      <div class="contact-item reveal reveal-delay-3">
        <div class="contact-icon">🐙</div>
        <div><div class="contact-label">GITHUB</div><div class="contact-value">github.com/tuanmudadullz</div></div>
      </div>
      <div class="contact-item reveal reveal-delay-4">
        <div class="contact-icon">📍</div>
        <div><div class="contact-label">LOKASI</div><div class="contact-value">Bekasi, Jawa Barat</div></div>
      </div>
    </div>
  </div>
</section>

<footer>
  <span>© 2026 Tuan Muda Dullz</span>
  <span>SMK Karya Guna 2 Bekasi — <span>11 TKJ 2</span></span>
  <span>BUILT WITH PRECISION</span>
</footer>

<script>
window.addEventListener('load',()=>{setTimeout(()=>{document.getElementById('preloader').classList.add('hide');},2200);});

const cursor=document.getElementById('cursor'),ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cursor.style.left=mx-4+'px';cursor.style.top=my-4+'px';});
function animRing(){rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;ring.style.left=rx-16+'px';ring.style.top=ry-16+'px';requestAnimationFrame(animRing);}
animRing();
document.querySelectorAll('button,a,.skill-card,.project-card,.contact-item').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cursor.style.transform='scale(2.5)';ring.style.transform='scale(1.5)';ring.style.opacity='1';});
  el.addEventListener('mouseleave',()=>{cursor.style.transform='scale(1)';ring.style.transform='scale(1)';ring.style.opacity='0.5';});
});

const phrases=['Siswa SMK Karya Guna 2 Bekasi','Kelas 11 TKJ 2','Network Engineer in Progress','Web Developer Pemula'];
let pIdx=0,cIdx=0,deleting=false;
const typed=document.getElementById('typed-text');
function type(){const phrase=phrases[pIdx];if(!deleting){typed.textContent=phrase.slice(0,++cIdx);if(cIdx===phrase.length){deleting=true;setTimeout(type,1800);return;}setTimeout(type,60);}else{typed.textContent=phrase.slice(0,--cIdx);if(cIdx===0){deleting=false;pIdx=(pIdx+1)%phrases.length;setTimeout(type,400);return;}setTimeout(type,30);}}
type();

const skills=[
  {icon:'🐍',name:'Python',level:'INTERMEDIATE',pct:0.65},
  {icon:'⚡',name:'JavaScript',level:'INTERMEDIATE',pct:0.60},
  {icon:'🐘',name:'PHP',level:'BASIC',pct:0.45},
  {icon:'🗄️',name:'MySQL',level:'INTERMEDIATE',pct:0.55},
  {icon:'🔗',name:'Networking',level:'ADVANCED',pct:0.78},
  {icon:'🐧',name:'Linux',level:'INTERMEDIATE',pct:0.62},
  {icon:'🔒',name:'Cybersecurity',level:'LEARNING',pct:0.40},
  {icon:'🎨',name:'HTML/CSS',level:'INTERMEDIATE',pct:0.68},
];
const sg=document.getElementById('skills-grid');
skills.forEach((s,i)=>{
  const card=document.createElement('div');
  card.className='skill-card reveal';
  card.style.transitionDelay=(i*0.08)+'s';
  card.innerHTML=`<div class="skill-icon">${s.icon}</div><div class="skill-name">${s.name}</div><div class="skill-level">${s.level}</div><div class="skill-bar"><div class="skill-bar-fill" data-pct="${s.pct}"></div></div>`;
  sg.appendChild(card);
  card.addEventListener('mousemove',e=>{const r=card.getBoundingClientRect();const x=(e.clientX-r.left)/r.width*100;const y=(e.clientY-r.top)/r.height*100;card.style.setProperty('--mx',x+'%');card.style.setProperty('--my',y+'%');const tx=(e.clientX-r.left-r.width/2)*0.06;const ty=(e.clientY-r.top-r.height/2)*0.06;card.style.transform=`translateY(-4px) perspective(600px) rotateX(${-ty}deg) rotateY(${tx}deg)`;});
  card.addEventListener('mouseleave',()=>{card.style.transform='';});
});

const projects=[
  {id:'PRJ-001',title:'Network Monitor Dashboard',desc:'Dashboard monitoring jaringan sekolah dengan visualisasi real-time menggunakan Python dan Flask.',tags:['Python','Flask','Networking']},
  {id:'PRJ-002',title:'Sistem Absensi Digital',desc:'Aplikasi absensi berbasis web dengan QR code untuk kelas TKJ menggunakan PHP dan MySQL.',tags:['PHP','MySQL','JavaScript']},
  {id:'PRJ-003',title:'Linux Server Setup',desc:'Konfigurasi Ubuntu Server sebagai web server dengan Apache, Nginx, dan implementasi firewall dasar.',tags:['Linux','Bash','Networking']},
];
const pg=document.getElementById('projects-grid');
projects.forEach((p,i)=>{
  const card=document.createElement('div');
  card.className='project-card reveal';
  card.style.transitionDelay=(i*0.15)+'s';
  card.innerHTML=`<div class="project-corner"></div><div class="project-header"><div class="project-id">${p.id}</div><div class="project-title">${p.title}</div></div><div class="project-body"><div class="project-desc">${p.desc}</div><div class="project-tags">${p.tags.map(t=>`<span class="project-tag">${t}</span>`).join('')}</div></div>`;
  pg.appendChild(card);
});

const observer=new IntersectionObserver(entries=>{entries.forEach(entry=>{if(entry.isIntersecting){entry.target.classList.add('visible');const bar=entry.target.querySelector('.skill-bar-fill');if(bar){const pct=parseFloat(bar.dataset.pct);bar.style.transform=`scaleX(${pct})`;}}});},{threshold:0.1,rootMargin:'0px 0px -60px 0px'});
document.querySelectorAll('.reveal').forEach(el=>observer.observe(el));
</script>
</body>
</html>
