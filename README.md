<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Sagar Dubile — AI Engineer & Blockchain Dev</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700;800&family=Syne:wght@400;700;800&display=swap" rel="stylesheet"/>
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --cyan:#00f7ff;--purple:#7c3aed;--dark:#050510;--darker:#020208;
  --text:#e2e8f0;--muted:#64748b;--card:#0d0d20;--border:#1e2040;
  --green:#00ff88;--amber:#f59e0b;
}
html{scroll-behavior:smooth}
body{background:var(--darker);color:var(--text);font-family:'JetBrains Mono',monospace;overflow-x:hidden;cursor:none}

/* Custom cursor */
#cursor{position:fixed;width:10px;height:10px;background:var(--cyan);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:width .15s,height .15s,background .15s;mix-blend-mode:screen}
#cursor-ring{position:fixed;width:36px;height:36px;border:1px solid var(--cyan);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:all .08s linear;opacity:.5}
body:has(a:hover) #cursor,body:has(button:hover) #cursor{width:20px;height:20px;background:var(--purple)}

/* Particle canvas */
#bg-canvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;opacity:.45}

/* Scanline effect */
body::before{content:'';position:fixed;top:0;left:0;width:100%;height:100%;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,247,255,.012) 2px,rgba(0,247,255,.012) 4px);pointer-events:none;z-index:1;animation:scanlines 8s linear infinite}
@keyframes scanlines{0%{background-position:0 0}100%{background-position:0 100%}}

/* Layout */
main{position:relative;z-index:2;max-width:1100px;margin:0 auto;padding:0 2rem}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:1rem 3rem;display:flex;justify-content:space-between;align-items:center;background:rgba(2,2,8,.8);backdrop-filter:blur(20px);border-bottom:1px solid rgba(0,247,255,.08)}
.nav-logo{font-family:'Syne',sans-serif;font-weight:800;font-size:1.2rem;color:var(--cyan);letter-spacing:.1em}
.nav-links{display:flex;gap:2rem}
.nav-links a{color:var(--muted);text-decoration:none;font-size:.8rem;letter-spacing:.1em;transition:color .2s}
.nav-links a:hover{color:var(--cyan)}
.nav-status{display:flex;align-items:center;gap:.5rem;font-size:.75rem;color:var(--green)}
.status-dot{width:8px;height:8px;border-radius:50%;background:var(--green);animation:pulse-dot 2s infinite}
@keyframes pulse-dot{0%,100%{box-shadow:0 0 0 0 rgba(0,255,136,.4)}50%{box-shadow:0 0 0 8px rgba(0,255,136,0)}}

/* HERO */
.hero{min-height:100vh;display:flex;flex-direction:column;justify-content:center;padding-top:5rem;position:relative}
.hero-eyebrow{font-size:.8rem;letter-spacing:.3em;color:var(--cyan);margin-bottom:1.5rem;opacity:0;animation:fadeup .6s .3s forwards}
.hero-name{font-family:'Syne',sans-serif;font-size:clamp(3rem,8vw,7rem);font-weight:800;line-height:.95;margin-bottom:1.5rem;opacity:0;animation:fadeup .6s .5s forwards}
.hero-name span{color:transparent;-webkit-text-stroke:1.5px var(--cyan)}
.hero-title{font-size:clamp(.9rem,2vw,1.2rem);color:var(--muted);margin-bottom:3rem;opacity:0;animation:fadeup .6s .7s forwards;max-width:600px;line-height:1.8}
.hero-title em{color:var(--cyan);font-style:normal}
.hero-cta{display:flex;gap:1.5rem;flex-wrap:wrap;opacity:0;animation:fadeup .6s .9s forwards}
.btn{padding:.8rem 2rem;border-radius:4px;font-family:'JetBrains Mono',monospace;font-size:.85rem;font-weight:700;letter-spacing:.1em;text-decoration:none;transition:all .25s;display:inline-flex;align-items:center;gap:.5rem}
.btn-primary{background:var(--cyan);color:var(--darker);border:none}
.btn-primary:hover{background:#fff;box-shadow:0 0 30px rgba(0,247,255,.5)}
.btn-outline{background:transparent;color:var(--cyan);border:1px solid var(--cyan)}
.btn-outline:hover{background:rgba(0,247,255,.08);box-shadow:0 0 20px rgba(0,247,255,.2)}
.hero-scroll{position:absolute;bottom:2rem;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:.5rem;color:var(--muted);font-size:.7rem;letter-spacing:.2em;animation:bounce 2s infinite}
@keyframes bounce{0%,100%{transform:translateX(-50%) translateY(0)}50%{transform:translateX(-50%) translateY(8px)}}
.scroll-line{width:1px;height:40px;background:linear-gradient(to bottom,var(--cyan),transparent)}

/* Stats strip */
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--border);border:1px solid var(--border);border-radius:8px;overflow:hidden;margin:5rem 0}
.stat{background:var(--card);padding:2rem;text-align:center;transition:background .2s}
.stat:hover{background:#0f0f25}
.stat-num{font-family:'Syne',sans-serif;font-size:2.5rem;font-weight:800;color:var(--cyan);display:block;line-height:1}
.stat-label{font-size:.7rem;color:var(--muted);letter-spacing:.15em;margin-top:.5rem;display:block}

/* Section */
.section{padding:6rem 0}
.section-label{font-size:.75rem;letter-spacing:.3em;color:var(--cyan);margin-bottom:1rem;display:flex;align-items:center;gap:1rem}
.section-label::after{content:'';flex:1;height:1px;background:linear-gradient(to right,var(--border),transparent)}
.section-title{font-family:'Syne',sans-serif;font-size:clamp(2rem,4vw,3.5rem);font-weight:800;margin-bottom:3rem;line-height:1.1}

/* Projects */
.projects-grid{display:grid;gap:1.5rem}
.project-card{background:var(--card);border:1px solid var(--border);border-radius:8px;padding:2.5rem;position:relative;overflow:hidden;transition:border-color .3s,transform .3s;cursor:pointer}
.project-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(to right,transparent,var(--cyan),transparent);opacity:0;transition:opacity .3s}
.project-card:hover{border-color:rgba(0,247,255,.3);transform:translateY(-4px)}
.project-card:hover::before{opacity:1}
.project-num{font-size:.7rem;color:var(--muted);letter-spacing:.2em;margin-bottom:1rem}
.project-title{font-family:'Syne',sans-serif;font-size:1.5rem;font-weight:800;margin-bottom:.75rem}
.project-desc{color:var(--muted);font-size:.85rem;line-height:1.8;margin-bottom:1.5rem}
.project-tags{display:flex;flex-wrap:wrap;gap:.5rem;margin-bottom:1.5rem}
.tag{padding:.3rem .8rem;background:rgba(0,247,255,.06);border:1px solid rgba(0,247,255,.15);border-radius:3px;font-size:.7rem;color:var(--cyan);letter-spacing:.08em}
.project-metrics{display:flex;gap:2rem}
.metric{font-size:.8rem}
.metric-val{color:var(--green);font-weight:700}
.metric-label{color:var(--muted)}
.project-glow{position:absolute;bottom:-60px;right:-60px;width:200px;height:200px;background:radial-gradient(circle,rgba(0,247,255,.06),transparent 70%);pointer-events:none;transition:opacity .3s}
.project-card:hover .project-glow{opacity:2}

/* Skills */
.skills-container{display:grid;grid-template-columns:repeat(2,1fr);gap:1.5rem}
.skill-block{background:var(--card);border:1px solid var(--border);border-radius:8px;padding:2rem;transition:border-color .3s}
.skill-block:hover{border-color:rgba(124,58,237,.4)}
.skill-icon{font-size:1.5rem;margin-bottom:1rem}
.skill-name{font-family:'Syne',sans-serif;font-weight:700;font-size:1rem;margin-bottom:.5rem;color:var(--cyan)}
.skill-tags{display:flex;flex-wrap:wrap;gap:.4rem;margin-top:1rem}
.skill-tag{padding:.25rem .6rem;background:rgba(124,58,237,.1);border:1px solid rgba(124,58,237,.2);border-radius:3px;font-size:.65rem;color:#a78bfa}
.skill-bar{height:3px;background:var(--border);border-radius:2px;margin-top:1rem;overflow:hidden}
.skill-fill{height:100%;border-radius:2px;background:linear-gradient(to right,var(--purple),var(--cyan));transform:scaleX(0);transform-origin:left;transition:transform 1s cubic-bezier(.16,1,.3,1)}
.skill-fill.animate{transform:scaleX(1)}

/* Timeline */
.timeline{position:relative;padding-left:2rem}
.timeline::before{content:'';position:absolute;left:0;top:0;bottom:0;width:1px;background:linear-gradient(to bottom,var(--cyan),var(--purple),transparent)}
.timeline-item{position:relative;padding:0 0 3rem 2rem}
.timeline-dot{position:absolute;left:-2.35rem;top:.3rem;width:10px;height:10px;border-radius:50%;background:var(--cyan);box-shadow:0 0 12px var(--cyan)}
.timeline-date{font-size:.7rem;color:var(--cyan);letter-spacing:.2em;margin-bottom:.5rem}
.timeline-title{font-family:'Syne',sans-serif;font-size:1.2rem;font-weight:700;margin-bottom:.25rem}
.timeline-sub{color:var(--muted);font-size:.8rem;margin-bottom.75rem}
.timeline-body{color:var(--muted);font-size:.82rem;line-height:1.8;margin-top:.75rem}
.timeline-body li{margin-bottom:.35rem;list-style:none;padding-left:1rem;position:relative}
.timeline-body li::before{content:'→';position:absolute;left:0;color:var(--cyan)}

/* Badges */
.badges{display:flex;flex-wrap:wrap;gap:1rem;margin-top:3rem}
.badge{display:flex;align-items:center;gap:.75rem;background:var(--card);border:1px solid var(--border);border-radius:6px;padding:1rem 1.5rem;transition:border-color .3s}
.badge:hover{border-color:rgba(0,247,255,.3)}
.badge-icon{font-size:1.2rem}
.badge-text{font-size:.8rem}
.badge-title{color:var(--text);font-weight:600}
.badge-sub{color:var(--muted);font-size:.7rem}

/* Contact */
.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:3rem;align-items:start}
.contact-copy{font-size:clamp(1.5rem,3vw,2.5rem);font-family:'Syne',sans-serif;font-weight:800;line-height:1.2;margin-bottom:1.5rem}
.contact-copy span{color:var(--cyan)}
.contact-links{display:flex;flex-direction:column;gap:1rem}
.contact-link{display:flex;align-items:center;gap:1rem;padding:1.2rem 1.5rem;background:var(--card);border:1px solid var(--border);border-radius:6px;text-decoration:none;color:var(--text);transition:all .25s}
.contact-link:hover{border-color:var(--cyan);background:rgba(0,247,255,.04);transform:translateX(8px)}
.contact-link-label{font-size:.7rem;color:var(--muted);letter-spacing:.15em}
.contact-link-val{font-size:.9rem;font-weight:600;color:var(--cyan)}
.contact-right{font-size:.85rem;color:var(--muted);line-height:2}
.contact-right strong{color:var(--text)}

/* Footer */
footer{border-top:1px solid var(--border);padding:2rem 3rem;display:flex;justify-content:space-between;align-items:center;font-size:.75rem;color:var(--muted);position:relative;z-index:2}

/* Animations */
@keyframes fadeup{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:translateY(0)}}
.reveal{opacity:0;transform:translateY(30px);transition:opacity .7s,transform .7s}
.reveal.visible{opacity:1;transform:translateY(0)}

/* Terminal blink */
.cursor-blink::after{content:'█';animation:blink .9s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

/* Glitch text */
.glitch{position:relative}
.glitch::before,.glitch::after{content:attr(data-text);position:absolute;top:0;left:0;width:100%;height:100%}
.glitch::before{animation:glitch1 3s infinite;color:var(--cyan);clip-path:polygon(0 0,100% 0,100% 35%,0 35%);transform:translateX(-3px)}
.glitch::after{animation:glitch2 3s infinite;color:var(--purple);clip-path:polygon(0 65%,100% 65%,100% 100%,0 100%);transform:translateX(3px)}
@keyframes glitch1{0%,95%,100%{transform:translateX(-3px)}96%{transform:translateX(3px)}97%{transform:translateX(-1px)}}
@keyframes glitch2{0%,95%,100%{transform:translateX(3px)}96%{transform:translateX(-3px)}97%{transform:translateX(1px)}}

@media(max-width:768px){
  .stats{grid-template-columns:repeat(2,1fr)}
  .skills-container{grid-template-columns:1fr}
  .contact-grid{grid-template-columns:1fr}
  nav .nav-links{display:none}
}
</style>
</head>
<body>

<!-- Custom cursor -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- Particle background -->
<canvas id="bg-canvas"></canvas>

<!-- NAV -->
<nav>
  <div class="nav-logo">SD://</div>
  <div class="nav-links">
    <a href="#projects">projects</a>
    <a href="#skills">skills</a>
    <a href="#experience">experience</a>
    <a href="#contact">contact</a>
  </div>
  <div class="nav-status">
    <div class="status-dot"></div>
    available for opportunities
  </div>
</nav>

<!-- HERO -->
<main>
<section class="hero">
  <div class="hero-eyebrow">// SAGAR RAMESH DUBILE</div>
  <h1 class="hero-name glitch" data-text="AI + WEB3">
    AI + WEB3<br/>
    <span>ENGINEER</span>
  </h1>
  <p class="hero-title">
    I build <em>AI systems that see</em>, <em>search engines that understand</em>,<br/>
    and <em>smart contracts that can't be broken</em>.<br/>
    VIT-AP · CGPA 8.81 · SIH 2025 Finalist · IBM Blockchain Certified
  </p>
  <div class="hero-cta">
    <a href="#projects" class="btn btn-primary">↓ See my work</a>
    <a href="https://www.linkedin.com/in/sagar-dubile-2079b0306/" class="btn btn-outline" target="_blank">↗ LinkedIn</a>
    <a href="mailto:dubile.sagarr@gmail.com" class="btn btn-outline">✉ Email me</a>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    SCROLL
  </div>
</section>

<!-- STATS -->
<div class="stats reveal">
  <div class="stat">
    <span class="stat-num" data-target="94">0</span><span class="stat-num">%</span>
    <span class="stat-label">FACIAL RECOG. ACCURACY</span>
  </div>
  <div class="stat">
    <span class="stat-num" data-target="45">0</span><span class="stat-num">%</span>
    <span class="stat-label">BETTER PRIORITIZATION</span>
  </div>
  <div class="stat">
    <span class="stat-num" data-target="70">0</span><span class="stat-num">%</span>
    <span class="stat-label">MANUAL EFFORT REDUCED</span>
  </div>
  <div class="stat">
    <span class="stat-num" data-target="8">0</span><span class="stat-num">.81</span>
    <span class="stat-label">CGPA @ VIT-AP</span>
  </div>
</div>

<!-- PROJECTS -->
<section class="section" id="projects">
  <div class="section-label">01 / PROJECTS</div>
  <h2 class="section-title">Things I Actually<br/>Built.</h2>
  <div class="projects-grid">

    <div class="project-card reveal">
      <div class="project-num">PROJECT 001</div>
      <div class="project-title">🏙️ JanVaani</div>
      <p class="project-desc">AI-powered civic grievance platform. Citizens report issues, AI auto-fills categories, RBAC dashboards track resolution. Government accountability — enforced by code.</p>
      <div class="project-tags">
        <span class="tag">AI AUTOFILL</span>
        <span class="tag">MAP VISUALIZATION</span>
        <span class="tag">RBAC</span>
        <span class="tag">REST APIs</span>
        <span class="tag">SLA TRACKING</span>
      </div>
      <div class="project-metrics">
        <div class="metric"><span class="metric-val">+45%</span><br/><span class="metric-label">Prioritization</span></div>
        <div class="metric"><span class="metric-val">+60%</span><br/><span class="metric-label">Engagement</span></div>
        <div class="metric"><span class="metric-val">-35%</span><br/><span class="metric-label">Resolution time</span></div>
      </div>
      <div class="project-glow"></div>
    </div>

    <div class="project-card reveal">
      <div class="project-num">PROJECT 002</div>
      <div class="project-title">🔍 Neural Semantic Search</div>
      <p class="project-desc">Search engine built with transformer embeddings. Not keywords — actual semantic understanding. Custom cache layer for near-zero latency repeat queries.</p>
      <div class="project-tags">
        <span class="tag">SENTENCE TRANSFORMERS</span>
        <span class="tag">CHROMADB</span>
        <span class="tag">PCA</span>
        <span class="tag">FUZZY C-MEANS</span>
        <span class="tag">FASTAPI</span>
      </div>
      <div class="project-metrics">
        <div class="metric"><span class="metric-val">Semantic</span><br/><span class="metric-label">Understanding</span></div>
        <div class="metric"><span class="metric-val">Sub-ms</span><br/><span class="metric-label">Cache latency</span></div>
        <div class="metric"><span class="metric-val">Custom</span><br/><span class="metric-label">Cache monitor</span></div>
      </div>
      <div class="project-glow"></div>
    </div>

    <div class="project-card reveal">
      <div class="project-num">PROJECT 003</div>
      <div class="project-title">👁️ TraceID — CCTV Recognition</div>
      <p class="project-desc">Frame-wise facial recognition system for identifying missing individuals in CCTV footage. 94% accuracy. Automated logging. Built because it matters.</p>
      <div class="project-tags">
        <span class="tag">PYTHON</span>
        <span class="tag">OPENCV</span>
        <span class="tag">DEEP LEARNING</span>
        <span class="tag">FACE RECOGNITION</span>
        <span class="tag">REAL-TIME</span>
      </div>
      <div class="project-metrics">
        <div class="metric"><span class="metric-val">94%</span><br/><span class="metric-label">Accuracy</span></div>
        <div class="metric"><span class="metric-val">-70%</span><br/><span class="metric-label">Manual effort</span></div>
        <div class="metric"><span class="metric-val">Real-time</span><br/><span class="metric-label">Processing</span></div>
      </div>
      <div class="project-glow"></div>
    </div>

  </div>
</section>

<!-- SKILLS -->
<section class="section" id="skills">
  <div class="section-label">02 / SKILLS</div>
  <h2 class="section-title">What I Work With.</h2>
  <div class="skills-container">

    <div class="skill-block reveal">
      <div class="skill-icon">🧠</div>
      <div class="skill-name">AI / Machine Learning</div>
      <div style="color:var(--muted);font-size:.8rem">Training models. Building pipelines. Making computers think.</div>
      <div class="skill-tags">
        <span class="skill-tag">TensorFlow</span><span class="skill-tag">PyTorch</span>
        <span class="skill-tag">Scikit-learn</span><span class="skill-tag">HuggingFace</span>
        <span class="skill-tag">Sentence Transformers</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.92"></div></div>
    </div>

    <div class="skill-block reveal">
      <div class="skill-icon">⛓️</div>
      <div class="skill-name">Blockchain / Web3</div>
      <div style="color:var(--muted);font-size:.8rem">Smart contracts that are secure by design, not by luck.</div>
      <div class="skill-tags">
        <span class="skill-tag">Solidity</span><span class="skill-tag">Ethereum</span>
        <span class="skill-tag">Hardhat</span><span class="skill-tag">Remix</span>
        <span class="skill-tag">DApps</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.88"></div></div>
    </div>

    <div class="skill-block reveal">
      <div class="skill-icon">🔍</div>
      <div class="skill-name">NLP / Search</div>
      <div style="color:var(--muted);font-size:.8rem">Making machines understand language at a semantic level.</div>
      <div class="skill-tags">
        <span class="skill-tag">RAG</span><span class="skill-tag">ChromaDB</span>
        <span class="skill-tag">Embeddings</span><span class="skill-tag">FastAPI</span>
        <span class="skill-tag">Vector DBs</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.85"></div></div>
    </div>

    <div class="skill-block reveal">
      <div class="skill-icon">📊</div>
      <div class="skill-name">Data Analytics</div>
      <div style="color:var(--muted);font-size:.8rem">From raw data to dashboards stakeholders actually use.</div>
      <div class="skill-tags">
        <span class="skill-tag">Power BI</span><span class="skill-tag">Pandas</span>
        <span class="skill-tag">EDA</span><span class="skill-tag">Excel</span>
        <span class="skill-tag">KPI Dashboards</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.93"></div></div>
    </div>

    <div class="skill-block reveal">
      <div class="skill-icon">☁️</div>
      <div class="skill-name">Cloud (AWS)</div>
      <div style="color:var(--muted);font-size:.8rem">Foundations + Architecting certified. Building scalable infra.</div>
      <div class="skill-tags">
        <span class="skill-tag">AWS Foundations</span><span class="skill-tag">Architecting</span>
        <span class="skill-tag">S3</span><span class="skill-tag">EC2</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.72"></div></div>
    </div>

    <div class="skill-block reveal">
      <div class="skill-icon">🤖</div>
      <div class="skill-name">Automation & APIs</div>
      <div style="color:var(--muted);font-size:.8rem">Everything that can be automated, will be. I'll make sure of it.</div>
      <div class="skill-tags">
        <span class="skill-tag">n8n</span><span class="skill-tag">FastAPI</span>
        <span class="skill-tag">REST APIs</span><span class="skill-tag">Python</span>
        <span class="skill-tag">Git</span>
      </div>
      <div class="skill-bar"><div class="skill-fill" style="--w:.95"></div></div>
    </div>

  </div>
</section>

<!-- EXPERIENCE -->
<section class="section" id="experience">
  <div class="section-label">03 / EXPERIENCE & EDUCATION</div>
  <h2 class="section-title">The Path.</h2>

  <div class="timeline">
    <div class="timeline-item reveal">
      <div class="timeline-dot"></div>
      <div class="timeline-date">NOV 2025 — MAR 2026</div>
      <div class="timeline-title">Blockchain Engineer Intern</div>
      <div class="timeline-sub" style="color:var(--cyan)">Shamgar Software Solutions · Remote, India</div>
      <ul class="timeline-body">
        <li>Developing and reviewing Ethereum smart contracts with focus on secure logic</li>
        <li>Designed and tested smart contract modules with gas optimization & vulnerability assessment</li>
        <li>Implemented unit testing and contract validation pipelines</li>
        <li>Supporting DApp workflows and blockchain solution architecture</li>
      </ul>
    </div>
    <div class="timeline-item reveal">
      <div class="timeline-dot" style="background:var(--purple);box-shadow:0 0 12px var(--purple)"></div>
      <div class="timeline-date">2021 — 2025</div>
      <div class="timeline-title">B.Tech in Computer Science</div>
      <div class="timeline-sub" style="color:var(--purple)">VIT Andhra Pradesh · CGPA: 8.81/10</div>
      <ul class="timeline-body">
        <li>Specialized in AI, ML, and Blockchain systems</li>
        <li>Smart India Hackathon 2025 — National Finalist</li>
        <li>Built production-grade AI and blockchain projects</li>
      </ul>
    </div>
  </div>

  <div class="badges reveal">
    <div class="badge">
      <div class="badge-icon">🏆</div>
      <div class="badge-text">
        <div class="badge-title">SIH 2025 Finalist</div>
        <div class="badge-sub">Smart India Hackathon · National Level</div>
      </div>
    </div>
    <div class="badge">
      <div class="badge-icon">🔗</div>
      <div class="badge-text">
        <div class="badge-title">IBM Blockchain Developer</div>
        <div class="badge-sub">Certified · Enterprise Grade</div>
      </div>
    </div>
    <div class="badge">
      <div class="badge-icon">☁️</div>
      <div class="badge-text">
        <div class="badge-title">AWS Certified</div>
        <div class="badge-sub">Foundations + Architecting</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="section" id="contact">
  <div class="section-label">04 / CONTACT</div>
  <div class="contact-grid">
    <div>
      <h2 class="contact-copy">Let's build<br/><span>something<br/>impossible.</span></h2>
      <div class="contact-links">
        <a href="https://www.linkedin.com/in/sagar-dubile-2079b0306/" target="_blank" class="contact-link">
          <span style="font-size:1.2rem">in</span>
          <div>
            <div class="contact-link-label">LINKEDIN</div>
            <div class="contact-link-val">sagar-dubile-2079b0306</div>
          </div>
        </a>
        <a href="mailto:dubile.sagarr@gmail.com" class="contact-link">
          <span style="font-size:1.2rem">✉</span>
          <div>
            <div class="contact-link-label">EMAIL</div>
            <div class="contact-link-val">dubile.sagarr@gmail.com</div>
          </div>
        </a>
        <a href="https://github.com/DubileSagar" target="_blank" class="contact-link">
          <span style="font-size:1.2rem">⌥</span>
          <div>
            <div class="contact-link-label">GITHUB</div>
            <div class="contact-link-val">github.com/DubileSagar</div>
          </div>
        </a>
      </div>
    </div>
    <div class="contact-right reveal">
      <p style="font-size:1rem;color:var(--text);margin-bottom:1.5rem;line-height:1.8">
        I'm currently <strong style="color:var(--green)">open to opportunities</strong> — internships, full-time roles, research collabs, or just building something crazy together.
      </p>
      <p>If you're working on something at the intersection of <strong>AI and blockchain</strong>, I want to hear about it.</p>
      <br/>
      <p>I respond fast. I think faster.</p>
      <br/>
      <p style="font-family:'Syne',sans-serif;font-size:1.5rem;font-weight:800;color:var(--cyan)" class="cursor-blink">_</p>
    </div>
  </div>
</section>
</main>

<footer>
  <span>© 2026 Sagar Ramesh Dubile</span>
  <span>Built with obsession, not templates.</span>
  <span style="color:var(--cyan)">DubileSagar</span>
</footer>

<script>
// Cursor
const cursor=document.getElementById('cursor');
const ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cursor.style.left=mx+'px';cursor.style.top=my+'px'});
function animRing(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animRing)}
animRing();

// Particles
const canvas=document.getElementById('bg-canvas');
const ctx=canvas.getContext('2d');
let W,H,particles=[];
function resize(){W=canvas.width=window.innerWidth;H=canvas.height=window.innerHeight}
resize();window.addEventListener('resize',resize);
class P{
  constructor(){this.reset()}
  reset(){this.x=Math.random()*W;this.y=Math.random()*H;this.vx=(Math.random()-.5)*.3;this.vy=(Math.random()-.5)*.3;this.size=Math.random()*1.5+.5;this.alpha=Math.random()*.6+.1;this.color=Math.random()>.5?'0,247,255':'124,58,237'}
  update(){this.x+=this.vx;this.y+=this.vy;if(this.x<0||this.x>W||this.y<0||this.y>H)this.reset()}
  draw(){ctx.beginPath();ctx.arc(this.x,this.y,this.size,0,Math.PI*2);ctx.fillStyle=`rgba(${this.color},${this.alpha})`;ctx.fill()}
}
for(let i=0;i<120;i++)particles.push(new P());
function drawConnections(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      const dx=particles[i].x-particles[j].x,dy=particles[i].y-particles[j].y;
      const d=Math.sqrt(dx*dx+dy*dy);
      if(d<120){ctx.beginPath();ctx.strokeStyle=`rgba(0,247,255,${.08*(1-d/120)})`;ctx.lineWidth=.5;ctx.moveTo(particles[i].x,particles[i].y);ctx.lineTo(particles[j].x,particles[j].y);ctx.stroke()}
    }
  }
}
function loop(){ctx.clearRect(0,0,W,H);particles.forEach(p=>{p.update();p.draw()});drawConnections();requestAnimationFrame(loop)}
loop();

// Reveal on scroll
const reveals=document.querySelectorAll('.reveal');
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      // Animate skill bars
      e.target.querySelectorAll('.skill-fill').forEach(b=>b.classList.add('animate'));
      // Animate counters
      e.target.querySelectorAll('[data-target]').forEach(el=>{
        const target=+el.dataset.target;
        let current=0;
        const step=target/60;
        const timer=setInterval(()=>{current=Math.min(current+step,target);el.textContent=Math.floor(current);if(current>=target)clearInterval(timer)},20);
      });
    }
  });
},{threshold:.15});
reveals.forEach(r=>obs.observe(r));

// Also animate stats section
const statsSection=document.querySelector('.stats');
if(statsSection){
  const statsObs=new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.querySelectorAll('[data-target]').forEach(el=>{
          const target=+el.dataset.target;
          let current=0;const step=target/60;
          const timer=setInterval(()=>{current=Math.min(current+step,target);el.textContent=Math.floor(current);if(current>=target)clearInterval(timer)},20);
        });
      }
    });
  },{threshold:.3});
  statsObs.observe(statsSection);
}

// Glitch on hero title hover
document.querySelector('.glitch')?.addEventListener('mouseenter',function(){
  this.style.animation='glitch .2s steps(2,end) 3';
  setTimeout(()=>this.style.animation='',600);
});

// Smooth nav highlight
const sections=document.querySelectorAll('section[id]');
const navLinks=document.querySelectorAll('.nav-links a');
window.addEventListener('scroll',()=>{
  let current='';
  sections.forEach(s=>{if(window.scrollY>=s.offsetTop-200)current=s.id});
  navLinks.forEach(a=>{a.style.color=a.getAttribute('href')==='#'+current?'var(--cyan)':'var(--muted)'});
});
</script>
</body>
</html>
