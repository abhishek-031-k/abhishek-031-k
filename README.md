<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Abhishek Kumar · GitHub Profile</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Space+Grotesk:wght@300;400;500;600;700&display=swap');

  :root {
    --cyan: #00f5ff;
    --purple: #a855f7;
    --green: #39ff14;
    --bg: #020408;
    --surface: #0a0f1a;
    --border: rgba(0,245,255,0.15);
    --text: #e2e8f0;
    --muted: #64748b;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html, body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Grotesk', sans-serif;
    overflow-x: hidden;
    scroll-behavior: smooth;
  }

  /* ── CANVAS HERO ────────────────────────────── */
  #hero {
    position: relative;
    height: 100vh;
    min-height: 600px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  #three-canvas {
    position: absolute;
    inset: 0;
    z-index: 0;
  }

  #particle-canvas {
    position: absolute;
    inset: 0;
    z-index: 1;
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    text-align: center;
    padding: 2rem;
  }

  .avatar-ring {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    margin: 0 auto 1.5rem;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .avatar-ring::before {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 50%;
    background: conic-gradient(var(--cyan), var(--purple), var(--green), var(--cyan));
    animation: spin 3s linear infinite;
  }

  .avatar-ring::after {
    content: '';
    position: absolute;
    inset: -8px;
    border-radius: 50%;
    background: conic-gradient(transparent 60%, rgba(0,245,255,0.3) 80%, transparent);
    animation: spin 2s linear infinite reverse;
  }

  .avatar-inner {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    background: linear-gradient(135deg, #1a1040, #0a2040);
    border: 2px solid var(--bg);
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5rem;
    font-weight: 700;
    font-family: 'JetBrains Mono', monospace;
    color: var(--cyan);
    letter-spacing: -2px;
    text-shadow: 0 0 20px var(--cyan), 0 0 40px rgba(0,245,255,0.4);
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .hero-name {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 700;
    letter-spacing: -1px;
    background: linear-gradient(90deg, #e2e8f0 0%, var(--cyan) 50%, var(--purple) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 0.5rem;
    animation: fadeUp 0.8s ease both;
  }

  .hero-handle {
    font-family: 'JetBrains Mono', monospace;
    font-size: 1rem;
    color: var(--cyan);
    opacity: 0.7;
    margin-bottom: 1rem;
    animation: fadeUp 0.9s 0.1s ease both;
  }

  .hero-typing {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(0.85rem, 2vw, 1.1rem);
    color: var(--green);
    min-height: 1.5em;
    margin-bottom: 2rem;
    animation: fadeUp 1s 0.2s ease both;
  }

  .hero-typing .cursor {
    display: inline-block;
    width: 2px;
    height: 1em;
    background: var(--green);
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 0.7s step-end infinite;
    box-shadow: 0 0 8px var(--green);
  }

  @keyframes blink { 50% { opacity: 0; } }
  @keyframes fadeUp { from { opacity: 0; transform: translateY(24px); } to { opacity: 1; transform: translateY(0); } }

  .hero-badges {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    justify-content: center;
    animation: fadeUp 1s 0.3s ease both;
    margin-bottom: 2rem;
  }

  .badge {
    padding: 4px 14px;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 600;
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.5px;
  }

  .badge-cyan { border: 1px solid var(--cyan); color: var(--cyan); background: rgba(0,245,255,0.07); }
  .badge-purple { border: 1px solid var(--purple); color: var(--purple); background: rgba(168,85,247,0.07); }
  .badge-green { border: 1px solid var(--green); color: var(--green); background: rgba(57,255,20,0.07); }

  .hero-stats {
    display: flex;
    gap: 2rem;
    justify-content: center;
    animation: fadeUp 1s 0.4s ease both;
  }

  .hero-stat { text-align: center; }
  .hero-stat .num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--cyan);
    text-shadow: 0 0 10px rgba(0,245,255,0.5);
    display: block;
  }
  .hero-stat .lbl {
    font-size: 0.7rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  /* ── SCROLL HINT ────────────────────────────── */
  .scroll-hint {
    position: absolute;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    opacity: 0.4;
    animation: bounce 2s ease-in-out infinite;
  }
  .scroll-hint span { font-size: 0.65rem; color: var(--cyan); letter-spacing: 2px; font-family: 'JetBrains Mono', monospace; }
  .scroll-arrow { width: 1px; height: 30px; background: linear-gradient(var(--cyan), transparent); }
  @keyframes bounce { 0%,100% { transform: translateX(-50%) translateY(0); } 50% { transform: translateX(-50%) translateY(6px); } }

  /* ── SECTIONS ───────────────────────────────── */
  section { padding: 5rem 2rem; max-width: 900px; margin: 0 auto; }

  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--cyan);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  .section-title {
    font-size: clamp(1.5rem, 3vw, 2.2rem);
    font-weight: 700;
    margin-bottom: 2.5rem;
    color: #f1f5f9;
  }

  /* ── SKILL GRID ─────────────────────────────── */
  .skill-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 12px;
    margin-bottom: 2rem;
  }

  .skill-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1rem;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
    cursor: default;
  }

  .skill-card::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 12px;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .skill-card:hover { transform: translateY(-4px); border-color: rgba(0,245,255,0.4); }
  .skill-card:hover::before { opacity: 1; }

  .skill-card.cyan::before { background: radial-gradient(circle at 50% 0%, rgba(0,245,255,0.08), transparent 70%); }
  .skill-card.purple::before { background: radial-gradient(circle at 50% 0%, rgba(168,85,247,0.08), transparent 70%); }
  .skill-card.green::before { background: radial-gradient(circle at 50% 0%, rgba(57,255,20,0.08), transparent 70%); }

  .skill-icon { font-size: 1.5rem; margin-bottom: 8px; }
  .skill-name { font-size: 0.85rem; font-weight: 600; color: #cbd5e1; margin-bottom: 6px; }
  .skill-bar-track { height: 3px; background: rgba(255,255,255,0.06); border-radius: 2px; overflow: hidden; }
  .skill-bar-fill { height: 100%; border-radius: 2px; transition: width 1.5s cubic-bezier(0.4,0,0.2,1); width: 0; }
  .skill-bar-fill.cyan { background: linear-gradient(90deg, rgba(0,245,255,0.4), var(--cyan)); box-shadow: 0 0 6px rgba(0,245,255,0.6); }
  .skill-bar-fill.purple { background: linear-gradient(90deg, rgba(168,85,247,0.4), var(--purple)); box-shadow: 0 0 6px rgba(168,85,247,0.6); }
  .skill-bar-fill.green { background: linear-gradient(90deg, rgba(57,255,20,0.4), var(--green)); box-shadow: 0 0 6px rgba(57,255,20,0.6); }
  .skill-pct { font-size: 0.65rem; color: var(--muted); font-family: 'JetBrains Mono', monospace; margin-top: 4px; }

  /* ── PROJECT CARDS ──────────────────────────── */
  .project-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 16px; }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }

  .project-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--cyan), var(--purple));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s ease;
  }

  .project-card:hover { transform: translateY(-6px); border-color: rgba(0,245,255,0.3); }
  .project-card:hover::after { transform: scaleX(1); }

  .project-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 6px;
    animation: pulse-dot 2s ease-in-out infinite;
  }
  .project-dot.cyan { background: var(--cyan); box-shadow: 0 0 6px var(--cyan); }
  .project-dot.green { background: var(--green); box-shadow: 0 0 6px var(--green); }
  @keyframes pulse-dot { 0%,100% { opacity:1; } 50% { opacity:0.4; } }

  .project-lang { font-size: 0.7rem; color: var(--muted); font-family: 'JetBrains Mono', monospace; margin-bottom: 0.75rem; }
  .project-name { font-size: 1rem; font-weight: 600; color: var(--cyan); margin-bottom: 0.5rem; }
  .project-desc { font-size: 0.82rem; color: #94a3b8; line-height: 1.6; margin-bottom: 1rem; }
  .project-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .project-tag { font-size: 0.65rem; padding: 2px 8px; border-radius: 10px; font-family: 'JetBrains Mono', monospace; background: rgba(0,245,255,0.06); border: 1px solid rgba(0,245,255,0.15); color: rgba(0,245,255,0.7); }
  .project-stars { font-size: 0.7rem; color: var(--muted); margin-top: 1rem; font-family: 'JetBrains Mono', monospace; }

  /* ── CONTRIBUTION HEATMAP ───────────────────── */
  .contrib-wrapper {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    overflow-x: auto;
  }
  .contrib-header { font-size: 0.8rem; color: var(--muted); margin-bottom: 1rem; font-family: 'JetBrains Mono', monospace; }
  .contrib-grid { display: flex; gap: 3px; }
  .contrib-col { display: flex; flex-direction: column; gap: 3px; }
  .contrib-cell {
    width: 11px; height: 11px;
    border-radius: 2px;
    transition: transform 0.2s;
  }
  .contrib-cell:hover { transform: scale(1.4); }
  .c0 { background: #0d1117; border: 1px solid rgba(255,255,255,0.05); }
  .c1 { background: #003d1f; box-shadow: 0 0 3px rgba(57,255,20,0.2); }
  .c2 { background: #006b35; box-shadow: 0 0 4px rgba(57,255,20,0.3); }
  .c3 { background: #00a550; box-shadow: 0 0 6px rgba(57,255,20,0.5); }
  .c4 { background: var(--green); box-shadow: 0 0 8px rgba(57,255,20,0.7); }

  /* ── TERMINAL BLOCK ─────────────────────────── */
  .terminal {
    background: #050a10;
    border: 1px solid rgba(0,245,255,0.2);
    border-radius: 12px;
    overflow: hidden;
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 2rem;
  }
  .terminal-bar {
    background: #0a1525;
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid rgba(0,245,255,0.1);
  }
  .t-dot { width: 10px; height: 10px; border-radius: 50%; }
  .t-red { background: #ff5f57; }
  .t-yellow { background: #ffbd2e; }
  .t-green { background: #28c840; }
  .t-title { font-size: 0.7rem; color: var(--muted); margin-left: auto; letter-spacing: 1px; }
  .terminal-body { padding: 1.25rem 1.5rem; font-size: 0.82rem; line-height: 2; }
  .t-prompt { color: var(--cyan); }
  .t-cmd { color: #e2e8f0; }
  .t-out { color: var(--muted); }
  .t-val { color: var(--green); }
  .t-key { color: var(--purple); }
  .t-str { color: #f59e0b; }

  /* ── CONNECT SECTION ────────────────────────── */
  .connect-grid { display: flex; flex-wrap: wrap; gap: 12px; justify-content: center; }
  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    text-decoration: none;
    transition: all 0.3s;
    cursor: pointer;
  }
  .connect-btn:hover { border-color: var(--cyan); color: var(--cyan); transform: translateY(-3px); background: rgba(0,245,255,0.05); }
  .connect-icon { font-size: 1rem; }

  /* ── FOOTER ─────────────────────────────────── */
  footer {
    text-align: center;
    padding: 3rem 2rem;
    border-top: 1px solid var(--border);
    font-size: 0.75rem;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
  }
  .footer-glow {
    font-size: 1.5rem;
    color: var(--cyan);
    text-shadow: 0 0 20px var(--cyan), 0 0 40px rgba(0,245,255,0.4);
    display: block;
    margin-bottom: 0.5rem;
    animation: pulse-glow 3s ease-in-out infinite;
  }
  @keyframes pulse-glow { 0%,100% { text-shadow: 0 0 20px var(--cyan), 0 0 40px rgba(0,245,255,0.4); } 50% { text-shadow: 0 0 30px var(--cyan), 0 0 60px rgba(0,245,255,0.6), 0 0 80px rgba(0,245,255,0.2); } }

  /* ── GRID LINES BG ──────────────────────────── */
  .grid-bg {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: -1;
    background-image:
      linear-gradient(rgba(0,245,255,0.02) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,255,0.02) 1px, transparent 1px);
    background-size: 50px 50px;
  }

  /* ── OBSERVE ANIMATIONS ─────────────────────── */
  .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<div class="grid-bg"></div>

<!-- ── HERO ── -->
<div id="hero" role="banner">
  <canvas id="three-canvas" aria-hidden="true"></canvas>
  <canvas id="particle-canvas" aria-hidden="true"></canvas>

  <div class="hero-content">
    <div class="avatar-ring">
      <div class="avatar-inner">AK</div>
    </div>

    <h1 class="hero-name">Abhishek Kumar</h1>
    <p class="hero-handle">@akmax · NIT Silchar · CS ∞</p>

    <p class="hero-typing" id="typing-el" aria-live="polite">
      <span id="typing-text"></span><span class="cursor" aria-hidden="true"></span>
    </p>

    <div class="hero-badges">
      <span class="badge badge-cyan">Full-Stack</span>
      <span class="badge badge-purple">Machine Learning</span>
      <span class="badge badge-green">Competitive Programming</span>
      <span class="badge badge-cyan">Open Source</span>
    </div>

    <div class="hero-stats">
      <div class="hero-stat">
        <span class="num" id="stat-repos">0</span>
        <span class="lbl">Repos</span>
      </div>
      <div class="hero-stat">
        <span class="num" id="stat-contrib">0</span>
        <span class="lbl">Contributions</span>
      </div>
      <div class="hero-stat">
        <span class="num" id="stat-stars">0</span>
        <span class="lbl">Stars</span>
      </div>
    </div>
  </div>

  <div class="scroll-hint" aria-hidden="true">
    <span>SCROLL</span>
    <div class="scroll-arrow"></div>
  </div>
</div>

<!-- ── ABOUT / TERMINAL ── -->
<section class="reveal">
  <div class="section-label">whoami</div>
  <h2 class="section-title">About me</h2>
  <div class="terminal" role="region" aria-label="Terminal-style about section">
    <div class="terminal-bar">
      <div class="t-dot t-red"></div>
      <div class="t-dot t-yellow"></div>
      <div class="t-dot t-green"></div>
      <span class="t-title">akmax@nit-silchar ~ zsh</span>
    </div>
    <div class="terminal-body">
      <div><span class="t-prompt">➜ ~ </span><span class="t-cmd">cat about.json</span></div>
      <div style="margin-top:8px;">
        <span class="t-key">{</span><br>
        &nbsp;&nbsp;<span class="t-key">"name"</span>: <span class="t-str">"Abhishek Kumar"</span>,<br>
        &nbsp;&nbsp;<span class="t-key">"role"</span>: <span class="t-str">"B.Tech CS · NIT Silchar"</span>,<br>
        &nbsp;&nbsp;<span class="t-key">"focus"</span>: [<span class="t-str">"full-stack"</span>, <span class="t-str">"ML"</span>, <span class="t-str">"systems"</span>],<br>
        &nbsp;&nbsp;<span class="t-key">"currently"</span>: <span class="t-str">"building food-delivery at scale"</span>,<br>
        &nbsp;&nbsp;<span class="t-key">"loves"</span>: <span class="t-str">"hard problems, clean code, bad puns"</span>,<br>
        &nbsp;&nbsp;<span class="t-key">"cp_rank"</span>: <span class="t-val">1247</span>,<br>
        &nbsp;&nbsp;<span class="t-key">"open_to"</span>: <span class="t-str">"internships · collabs · coffee chats"</span><br>
        <span class="t-key">}</span>
      </div>
      <br>
      <div><span class="t-prompt">➜ ~ </span><span class="t-cmd">echo $STATUS</span></div>
      <div><span class="t-val">🟢 Available for opportunities</span></div>
    </div>
  </div>
</section>

<!-- ── SKILLS ── -->
<section class="reveal">
  <div class="section-label">tech stack</div>
  <h2 class="section-title">Skills &amp; tools</h2>
  <div class="skill-grid" id="skill-grid">
    <!-- injected by JS -->
  </div>
</section>

<!-- ── PROJECTS ── -->
<section class="reveal">
  <div class="section-label">pinned</div>
  <h2 class="section-title">Projects</h2>
  <div class="project-grid" id="project-grid">
    <!-- injected by JS -->
  </div>
</section>

<!-- ── CONTRIBUTIONS ── -->
<section class="reveal">
  <div class="section-label">activity</div>
  <h2 class="section-title">Contribution graph</h2>
  <div class="contrib-wrapper">
    <div class="contrib-header" id="contrib-count">847 contributions in the last year</div>
    <div class="contrib-grid" id="contrib-grid"></div>
  </div>
</section>

<!-- ── CONNECT ── -->
<section class="reveal" style="text-align:center;">
  <div class="section-label" style="justify-content:center;">contact</div>
  <h2 class="section-title">Let's build something</h2>
  <div class="connect-grid">
    <a class="connect-btn" href="mailto:akmax@dev.io">
      <span class="connect-icon">✉</span> akmax@dev.io
    </a>
    <a class="connect-btn" href="https://linkedin.com" target="_blank" rel="noopener">
      <span class="connect-icon">in</span> LinkedIn
    </a>
    <a class="connect-btn" href="https://twitter.com" target="_blank" rel="noopener">
      <span class="connect-icon">𝕏</span> Twitter / X
    </a>
    <a class="connect-btn" href="https://akmax.dev" target="_blank" rel="noopener">
      <span class="connect-icon">⬡</span> Portfolio
    </a>
    <a class="connect-btn" href="https://leetcode.com" target="_blank" rel="noopener">
      <span class="connect-icon">⚡</span> LeetCode
    </a>
  </div>
</section>

<footer>
  <span class="footer-glow">{ }</span>
  Built with curiosity · NIT Silchar · 2025<br>
  <span style="color:rgba(0,245,255,0.3); margin-top:6px; display:block;">
    &lt;/&gt; crafted in VSCode at 2am probably
  </span>
</footer>

<!-- THREE.JS -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
/* ── DATA ──────────────────────────────────────── */
const SKILLS = [
  { name:'Node.js',    pct:88, color:'cyan',   icon:'⬡' },
  { name:'React',      pct:85, color:'cyan',   icon:'⚛' },
  { name:'Python',     pct:82, color:'purple', icon:'🐍' },
  { name:'PyTorch',    pct:72, color:'purple', icon:'🔥' },
  { name:'MongoDB',    pct:78, color:'green',  icon:'🍃' },
  { name:'C++',        pct:80, color:'cyan',   icon:'⚙' },
  { name:'TypeScript', pct:75, color:'cyan',   icon:'TS' },
  { name:'Docker',     pct:65, color:'green',  icon:'🐳' },
  { name:'Socket.IO',  pct:70, color:'purple', icon:'⚡' },
  { name:'k6',         pct:60, color:'green',  icon:'📊' },
];

const PROJECTS = [
  {
    name: 'food-delivery-app',
    lang: 'JavaScript',
    dot: 'cyan',
    desc: 'Full-stack delivery platform with Node.js, Redis caching, k6 load testing, deployed on Render. Reduced p95 latency by 60%.',
    tags: ['Node.js','Redis','k6','REST API','Render'],
    stars: 5
  },
  {
    name: 'realtime-chat',
    lang: 'TypeScript',
    dot: 'green',
    desc: 'React + Express chat with Socket.IO, Vite env config, CORS hardening, deployed across Vercel + Render.',
    tags: ['Socket.IO','React','Vite','Vercel'],
    stars: 3
  },
  {
    name: 'SimpleRAG',
    lang: 'Python',
    dot: 'cyan',
    desc: 'PyTorch RAG with cosine-similarity retrieval, fusion layer, and top-k document fetching.',
    tags: ['PyTorch','NLP','Transformers','RAG'],
    stars: 2
  },
  {
    name: 'cp-solutions',
    lang: 'C++',
    dot: 'green',
    desc: 'Competitive programming archive — greedy, DP, graphs, interval strategies. LeetCode + Codeforces.',
    tags: ['C++','Python','Algorithms','LeetCode'],
    stars: 1
  },
];

/* ── TYPING ──────────────────────────────────── */
const phrases = [
  '> building food-delivery at scale 🚀',
  '> exploring RAG with PyTorch 🔥',
  '> solving hard problems in C++ ⚡',
  '> deploying on Render + Vercel 🌐',
  '> open for internships & collabs 👀',
];
let pi=0, ci=0, del=false;
const tEl = document.getElementById('typing-text');
function doType(){
  const w = phrases[pi];
  if(!del){ tEl.textContent = w.slice(0,++ci); if(ci===w.length){ del=true; setTimeout(doType,1600); return; } }
  else { tEl.textContent = w.slice(0,--ci); if(ci===0){ del=false; pi=(pi+1)%phrases.length; } }
  setTimeout(doType, del?30:60);
}
doType();

/* ── COUNTER ANIMATION ───────────────────────── */
function animCount(el, target, dur=1800){
  let start=0, startTime=null;
  function step(ts){
    if(!startTime) startTime=ts;
    const pct = Math.min((ts-startTime)/dur,1);
    el.textContent = Math.round(pct*target) + (target>=100?'':'');
    if(pct<1) requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}
setTimeout(()=>{
  animCount(document.getElementById('stat-repos'),34);
  animCount(document.getElementById('stat-contrib'),847);
  animCount(document.getElementById('stat-stars'),12);
},400);

/* ── SKILLS ─────────────────────────────────── */
const sg = document.getElementById('skill-grid');
SKILLS.forEach(s=>{
  sg.innerHTML += `
  <div class="skill-card ${s.color}">
    <div class="skill-icon">${s.icon}</div>
    <div class="skill-name">${s.name}</div>
    <div class="skill-bar-track"><div class="skill-bar-fill ${s.color}" data-pct="${s.pct}"></div></div>
    <div class="skill-pct">${s.pct}%</div>
  </div>`;
});

/* ── PROJECTS ────────────────────────────────── */
const pg = document.getElementById('project-grid');
PROJECTS.forEach(p=>{
  const tags = p.tags.map(t=>`<span class="project-tag">${t}</span>`).join('');
  pg.innerHTML += `
  <div class="project-card">
    <div class="project-lang"><span class="project-dot ${p.dot}"></span>${p.lang}</div>
    <div class="project-name">${p.name}</div>
    <div class="project-desc">${p.desc}</div>
    <div class="project-tags">${tags}</div>
    <div class="project-stars">⭐ ${p.stars} · 🍴 ${Math.max(0,p.stars-2)}</div>
  </div>`;
});

/* ── CONTRIB GRID ────────────────────────────── */
const cg = document.getElementById('contrib-grid');
const WEEKS=52, DAYS=7;
for(let w=0;w<WEEKS;w++){
  const col=document.createElement('div'); col.className='contrib-col';
  for(let d=0;d<DAYS;d++){
    const cell=document.createElement('div');
    const r=Math.random();
    cell.className='contrib-cell '+(r>0.94?'c4':r>0.82?'c3':r>0.65?'c2':r>0.45?'c1':'c0');
    cell.title=`${Math.floor(r*8)} contributions`;
    col.appendChild(cell);
  }
  cg.appendChild(col);
}

/* ── REVEAL OBSERVER ─────────────────────────── */
const obs = new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      if(e.target.classList.contains('reveal')){
        e.target.querySelectorAll('.skill-bar-fill').forEach(bar=>{
          bar.style.width = bar.dataset.pct+'%';
        });
      }
    }
  });
},{threshold:0.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));

/* ── PARTICLES ───────────────────────────────── */
(function(){
  const canvas = document.getElementById('particle-canvas');
  const ctx = canvas.getContext('2d');
  let W, H, particles=[];
  function resize(){ W=canvas.width=window.innerWidth; H=canvas.height=window.innerHeight; }
  resize(); window.addEventListener('resize',resize);
  for(let i=0;i<80;i++) particles.push({
    x:Math.random()*2000, y:Math.random()*900,
    vx:(Math.random()-0.5)*0.3, vy:(Math.random()-0.5)*0.3,
    r:Math.random()*1.5+0.3, a:Math.random()
  });
  function drawParticles(){
    ctx.clearRect(0,0,W,H);
    particles.forEach(p=>{
      p.x+=p.vx; p.y+=p.vy;
      if(p.x<0)p.x=W; if(p.x>W)p.x=0;
      if(p.y<0)p.y=H; if(p.y>H)p.y=0;
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle=`rgba(0,245,255,${p.a*0.5})`;
      ctx.fill();
    });
    particles.forEach((p,i)=>{
      for(let j=i+1;j<particles.length;j++){
        const q=particles[j];
        const dx=p.x-q.x, dy=p.y-q.y, dist=Math.sqrt(dx*dx+dy*dy);
        if(dist<120){
          ctx.beginPath();
          ctx.moveTo(p.x,p.y); ctx.lineTo(q.x,q.y);
          ctx.strokeStyle=`rgba(0,245,255,${(1-dist/120)*0.15})`;
          ctx.lineWidth=0.5;
          ctx.stroke();
        }
      }
    });
    requestAnimationFrame(drawParticles);
  }
  drawParticles();
})();

/* ── THREE.JS 3D SCENE ───────────────────────── */
(function(){
  if(typeof THREE==='undefined') return;
  const canvas=document.getElementById('three-canvas');
  const renderer=new THREE.WebGLRenderer({canvas,alpha:true,antialias:true});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));
  renderer.setClearColor(0x000000,0);

  const scene=new THREE.Scene();
  const camera=new THREE.PerspectiveCamera(60, window.innerWidth/window.innerHeight, 0.1, 100);
  camera.position.z=5;

  function resize(){
    renderer.setSize(window.innerWidth,window.innerHeight);
    camera.aspect=window.innerWidth/window.innerHeight;
    camera.updateProjectionMatrix();
  }
  resize(); window.addEventListener('resize',resize);

  const cyan=new THREE.Color(0x00f5ff);
  const purple=new THREE.Color(0xa855f7);
  const green=new THREE.Color(0x39ff14);

  function wireMat(color,opacity=0.6){
    return new THREE.MeshBasicMaterial({color,wireframe:true,transparent:true,opacity});
  }

  const objs=[];

  /* floating icosahedron */
  const ico=new THREE.Mesh(
    new THREE.IcosahedronGeometry(1.2,1),
    wireMat(cyan,0.25)
  );
  ico.position.set(2.5,0,0);
  scene.add(ico); objs.push({mesh:ico,rx:0.003,ry:0.007,rz:0.002});

  /* torus knot */
  const knot=new THREE.Mesh(
    new THREE.TorusKnotGeometry(0.7,0.18,80,12,2,3),
    wireMat(purple,0.3)
  );
  knot.position.set(-2.8,0.5,0);
  scene.add(knot); objs.push({mesh:knot,rx:0.005,ry:0.003,rz:0.004});

  /* octahedron */
  const oct=new THREE.Mesh(
    new THREE.OctahedronGeometry(0.8,0),
    wireMat(green,0.35)
  );
  oct.position.set(0,-1.5,-1);
  scene.add(oct); objs.push({mesh:oct,rx:0.008,ry:0.005,rz:0.006});

  /* small orbiting spheres */
  [-1.2,0,1.2].forEach((x,i)=>{
    const sp=new THREE.Mesh(
      new THREE.SphereGeometry(0.08,8,8),
      new THREE.MeshBasicMaterial({color:[cyan,purple,green][i]})
    );
    sp.position.set(x-0.5, 1.8, -0.5);
    scene.add(sp);
    objs.push({mesh:sp, rx:0.01*(i+1), ry:0.02, rz:0, float:{amp:0.15, freq:0.5+i*0.3, phase:i*2}});
  });

  let t=0;
  function animate(){
    requestAnimationFrame(animate);
    t+=0.01;
    objs.forEach(o=>{
      o.mesh.rotation.x+=o.rx;
      o.mesh.rotation.y+=o.ry;
      o.mesh.rotation.z+=o.rz;
      if(o.float){
        o.mesh.position.y=1.8+Math.sin(t*o.float.freq+o.float.phase)*o.float.amp;
      }
    });
    ico.position.y=Math.sin(t*0.4)*0.3;
    knot.position.y=0.5+Math.sin(t*0.3)*0.4;
    renderer.render(scene,camera);
  }
  animate();

  /* subtle mouse parallax */
  document.addEventListener('mousemove',e=>{
    const mx=(e.clientX/window.innerWidth-0.5)*0.4;
    const my=(e.clientY/window.innerHeight-0.5)*0.4;
    scene.rotation.x=-my;
    scene.rotation.y=mx;
  });
})();
</script>
</body>
</html>
