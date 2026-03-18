<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ayush Gaurav — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080c14;
    --surface: #0d1520;
    --border: #1a2a3a;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --green: #10b981;
    --red: #ef4444;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  #cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s, background 0.2s;
    mix-blend-mode: difference;
  }
  #cursor-ring {
    position: fixed;
    width: 36px; height: 36px;
    border: 1.5px solid var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform 0.18s ease, width 0.2s, height 0.2s, opacity 0.2s;
    opacity: 0.5;
  }

  /* Grid Background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* Glowing orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
    opacity: 0.18;
    animation: orb-float 12s ease-in-out infinite alternate;
  }
  .orb1 { width: 500px; height: 500px; background: var(--accent2); top: -200px; left: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: var(--accent); bottom: -150px; right: -100px; animation-delay: -6s; }
  .orb3 { width: 300px; height: 300px; background: var(--accent3); top: 50%; left: 50%; animation-delay: -3s; }

  @keyframes orb-float {
    from { transform: translate(0,0) scale(1); }
    to { transform: translate(40px, 30px) scale(1.1); }
  }

  /* Layout */
  .wrapper { position: relative; z-index: 1; max-width: 960px; margin: 0 auto; padding: 40px 24px 80px; }

  /* Hero */
  .hero {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 32px;
    align-items: center;
    padding: 60px 0 48px;
    border-bottom: 1px solid var(--border);
    margin-bottom: 48px;
  }
  .hero-tag {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    color: var(--accent);
    font-size: 11px; letter-spacing: 2px; text-transform: uppercase;
    padding: 6px 14px; border-radius: 4px;
    margin-bottom: 20px;
  }
  .hero-tag .dot { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; animation: blink 1.5s infinite; }
  @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0.2;} }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(36px, 6vw, 72px);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -2px;
    background: linear-gradient(135deg, #ffffff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
  }
  .hero-sub {
    font-size: 13px; color: var(--muted);
    line-height: 1.8;
    max-width: 480px;
    margin-bottom: 24px;
  }
  .hero-sub span { color: var(--accent); }

  /* Typewriter */
  #typewriter {
    font-family: 'Space Mono', monospace;
    font-size: 14px;
    color: var(--accent3);
    min-height: 22px;
  }
  #typewriter::after { content: '|'; animation: blink 0.8s infinite; }

  /* Avatar */
  .avatar-wrap {
    position: relative;
    width: 140px; height: 140px;
    flex-shrink: 0;
  }
  .avatar-ring {
    position: absolute; inset: -6px;
    border-radius: 50%;
    border: 2px dashed rgba(0,212,255,0.3);
    animation: spin 12s linear infinite;
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 48px; font-weight: 800;
    color: white;
    box-shadow: 0 0 40px rgba(0,212,255,0.3);
  }

  /* Buttons */
  .btn-row { display: flex; gap: 12px; flex-wrap: wrap; }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 10px 20px;
    border-radius: 6px;
    font-family: 'Space Mono', monospace;
    font-size: 11px; letter-spacing: 1px; text-transform: uppercase;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer; border: none;
  }
  .btn-primary {
    background: var(--accent); color: var(--bg);
    box-shadow: 0 0 20px rgba(0,212,255,0.3);
  }
  .btn-primary:hover { box-shadow: 0 0 40px rgba(0,212,255,0.6); transform: translateY(-2px); }
  .btn-outline {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--text);
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

  /* Section titles */
  .section { margin-bottom: 56px; }
  .section-header {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 28px;
  }
  .section-num {
    font-size: 11px; color: var(--accent);
    letter-spacing: 2px;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 22px; font-weight: 700;
    letter-spacing: -0.5px;
  }
  .section-line { flex: 1; height: 1px; background: var(--border); }

  /* Cards */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .card:hover {
    border-color: rgba(0,212,255,0.3);
    box-shadow: 0 0 30px rgba(0,212,255,0.06);
  }

  /* Tech Stack */
  .tech-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 12px; }
  .tech-category { font-size: 10px; letter-spacing: 2px; color: var(--accent); text-transform: uppercase; margin-bottom: 12px; }
  .tech-pills { display: flex; flex-wrap: wrap; gap: 8px; }
  .pill {
    display: inline-flex; align-items: center; gap: 6px;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 5px 10px;
    font-size: 11px; color: var(--text);
    transition: all 0.2s;
  }
  .pill:hover { border-color: var(--accent); color: var(--accent); background: rgba(0,212,255,0.06); }
  .pill-dot { width: 5px; height: 5px; border-radius: 50%; }

  /* Code block */
  .code-card {
    background: #060a10;
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
  }
  .code-topbar {
    display: flex; align-items: center; gap: 8px;
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
    background: rgba(255,255,255,0.02);
  }
  .code-dot { width: 10px; height: 10px; border-radius: 50%; }
  .code-filename { font-size: 11px; color: var(--muted); margin-left: auto; }
  pre {
    padding: 24px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    line-height: 1.8;
    overflow-x: auto;
    color: #a8b4c8;
  }
  .kw { color: #c084fc; }
  .str { color: #86efac; }
  .prop { color: #7dd3fc; }
  .val { color: #fde68a; }
  .cm { color: #475569; font-style: italic; }
  .fn { color: #f472b6; }
  .num { color: #fb923c; }

  /* Stats grid */
  .stats-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 12px; }
  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    transition: all 0.2s;
    position: relative; overflow: hidden;
  }
  .stat-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0;
    transition: opacity 0.2s;
  }
  .stat-card:hover::before { opacity: 1; }
  .stat-card:hover { border-color: rgba(0,212,255,0.2); transform: translateY(-3px); }
  .stat-icon { font-size: 28px; margin-bottom: 10px; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 28px; font-weight: 800;
    color: var(--accent);
    margin-bottom: 4px;
    counter-reset: none;
  }
  .stat-label { font-size: 10px; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; }

  /* Social links */
  .social-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 12px; }
  .social-card {
    display: flex; align-items: center; gap: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.2s;
    position: relative; overflow: hidden;
  }
  .social-card::after {
    content: '→';
    position: absolute; right: 20px;
    opacity: 0;
    transform: translateX(-8px);
    transition: all 0.2s;
    color: var(--accent);
  }
  .social-card:hover { border-color: rgba(0,212,255,0.3); color: var(--accent); transform: translateY(-2px); }
  .social-card:hover::after { opacity: 1; transform: translateX(0); }
  .social-icon { font-size: 22px; }
  .social-name { font-size: 11px; letter-spacing: 1px; text-transform: uppercase; color: var(--muted); margin-bottom: 2px; }
  .social-handle { font-size: 13px; }

  /* Quote */
  .quote-card {
    background: linear-gradient(135deg, rgba(124,58,237,0.1), rgba(0,212,255,0.05));
    border: 1px solid rgba(124,58,237,0.3);
    border-radius: 10px;
    padding: 28px 32px;
    position: relative;
  }
  .quote-mark {
    font-family: 'Syne', sans-serif;
    font-size: 80px; font-weight: 800;
    color: var(--accent2);
    opacity: 0.3;
    position: absolute; top: 0; left: 20px;
    line-height: 1;
  }
  .quote-text {
    font-size: 15px; line-height: 1.8;
    color: var(--text);
    padding-left: 20px;
    font-style: italic;
  }
  .quote-author { font-size: 11px; color: var(--muted); margin-top: 12px; padding-left: 20px; letter-spacing: 1px; }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 2px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--accent); }

  /* Fade in animation */
  .fade-up {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.5s ease, transform 0.5s ease;
  }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  /* Nav */
  nav {
    display: flex; align-items: center; justify-content: space-between;
    padding: 16px 0;
    border-bottom: 1px solid var(--border);
    margin-bottom: 0;
    position: sticky; top: 0;
    background: rgba(8,12,20,0.85);
    backdrop-filter: blur(20px);
    z-index: 100;
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 18px;
    color: var(--accent);
    letter-spacing: -0.5px;
  }
  .nav-links { display: flex; gap: 24px; }
  .nav-links a {
    font-size: 11px; letter-spacing: 1px; text-transform: uppercase;
    color: var(--muted); text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--accent); }

  @media (max-width: 600px) {
    .hero { grid-template-columns: 1fr; }
    .avatar-wrap { display: none; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>
<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="wrapper">

  <!-- Nav -->
  <nav>
    <div class="nav-logo">AG/</div>
    <div class="nav-links">
      <a href="#stack">Stack</a>
      <a href="#code">Code</a>
      <a href="#stats">Stats</a>
      <a href="#connect">Connect</a>
    </div>
  </nav>

  <!-- Hero -->
  <section class="hero fade-up">
    <div>
      <div class="hero-tag"><span class="dot"></span> Available for opportunities</div>
      <h1 class="hero-name">Ayush<br>Gaurav</h1>
      <p class="hero-sub">
        <span>Full Stack Developer</span> crafting scalable web experiences.<br>
        MERN Stack · DSA in Java · GSAP Animations
      </p>
      <div id="typewriter"></div>
      <br>
      <div class="btn-row">
        <a href="mailto:ayushgaurav.dev@gmail.com" class="btn btn-primary">✉ Hire Me</a>
        <a href="https://github.com/ayushga03" target="_blank" class="btn btn-outline">⌥ GitHub</a>
        <a href="https://linkedin.com/in/ayush-gaurav" target="_blank" class="btn btn-outline">in LinkedIn</a>
      </div>
    </div>
    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar-inner">AG</div>
    </div>
  </section>

  <!-- Tech Stack -->
  <section id="stack" class="section fade-up">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2 class="section-title">Tech Stack</h2>
      <div class="section-line"></div>
    </div>
    <div class="tech-grid">
      <div class="card">
        <div class="tech-category">Frontend</div>
        <div class="tech-pills">
          <span class="pill"><span class="pill-dot" style="background:#e34f26"></span>HTML5</span>
          <span class="pill"><span class="pill-dot" style="background:#1572b6"></span>CSS3</span>
          <span class="pill"><span class="pill-dot" style="background:#f7df1e"></span>JavaScript</span>
          <span class="pill"><span class="pill-dot" style="background:#61dafb"></span>React</span>
          <span class="pill"><span class="pill-dot" style="background:#38b2ac"></span>Tailwind</span>
          <span class="pill"><span class="pill-dot" style="background:#563d7c"></span>Bootstrap</span>
          <span class="pill"><span class="pill-dot" style="background:#88ce02"></span>GSAP</span>
        </div>
      </div>
      <div class="card">
        <div class="tech-category">Backend</div>
        <div class="tech-pills">
          <span class="pill"><span class="pill-dot" style="background:#6da55f"></span>Node.js</span>
          <span class="pill"><span class="pill-dot" style="background:#404d59"></span>Express.js</span>
          <span class="pill"><span class="pill-dot" style="background:#0077b5"></span>REST APIs</span>
        </div>
      </div>
      <div class="card">
        <div class="tech-category">Database</div>
        <div class="tech-pills">
          <span class="pill"><span class="pill-dot" style="background:#4ea94b"></span>MongoDB</span>
          <span class="pill"><span class="pill-dot" style="background:#00758f"></span>MySQL</span>
        </div>
      </div>
      <div class="card">
        <div class="tech-category">Languages</div>
        <div class="tech-pills">
          <span class="pill"><span class="pill-dot" style="background:#ed8b00"></span>Java</span>
          <span class="pill"><span class="pill-dot" style="background:#f7df1e"></span>JavaScript</span>
        </div>
      </div>
      <div class="card">
        <div class="tech-category">Tools</div>
        <div class="tech-pills">
          <span class="pill"><span class="pill-dot" style="background:#f05033"></span>Git</span>
          <span class="pill"><span class="pill-dot" style="background:#00d4ff"></span>GitHub</span>
          <span class="pill"><span class="pill-dot" style="background:#7c3aed"></span>Responsive Design</span>
        </div>
      </div>
    </div>
  </section>

  <!-- Code block -->
  <section id="code" class="section fade-up">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2 class="section-title">About Me in Code</h2>
      <div class="section-line"></div>
    </div>
    <div class="code-card">
      <div class="code-topbar">
        <div class="code-dot" style="background:#ef4444"></div>
        <div class="code-dot" style="background:#f59e0b"></div>
        <div class="code-dot" style="background:#10b981"></div>
        <span class="code-filename">ayush.config.js</span>
      </div>
      <pre><span class="kw">const</span> <span class="fn">ayush</span> = {
  <span class="prop">name</span>:     <span class="str">"Ayush Gaurav"</span>,
  <span class="prop">role</span>:     <span class="str">"Full Stack Web Developer"</span>,
  <span class="prop">location</span>: <span class="str">"India 🇮🇳"</span>,
  <span class="prop">email</span>:    <span class="str">"ayushgaurav.dev@gmail.com"</span>,

  <span class="prop">code</span>: [<span class="str">"JavaScript"</span>, <span class="str">"Java"</span>, <span class="str">"HTML"</span>, <span class="str">"CSS"</span>],

  <span class="prop">technologies</span>: {
    <span class="prop">frontend</span>: {
      <span class="prop">js</span>:  [<span class="str">"React"</span>, <span class="str">"Vanilla JS"</span>],
      <span class="prop">css</span>: [<span class="str">"Tailwind CSS"</span>, <span class="str">"Bootstrap"</span>, <span class="str">"GSAP"</span>]
    },
    <span class="prop">backend</span>:   { <span class="prop">js</span>: [<span class="str">"Node.js"</span>, <span class="str">"Express.js"</span>] },
    <span class="prop">databases</span>: [<span class="str">"MongoDB"</span>, <span class="str">"MySQL"</span>],
    <span class="prop">misc</span>:      [<span class="str">"REST APIs"</span>, <span class="str">"Git"</span>, <span class="str">"Responsive Design"</span>]
  },

  <span class="prop">currentFocus</span>: <span class="str">"Building full-stack apps &amp; mastering DSA"</span>,
  <span class="prop">openToWork</span>:  <span class="kw">true</span>,
  <span class="prop">funFact</span>:     <span class="str">"I debug with console.log() and I'm not ashamed 😄"</span>
};

<span class="cm">// Export the developer</span>
<span class="kw">export default</span> ayush;</pre>
    </div>
  </section>

  <!-- Stats -->
  <section id="stats" class="section fade-up">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2 class="section-title">By the Numbers</h2>
      <div class="section-line"></div>
    </div>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-icon">🚀</div>
        <div class="stat-num" data-target="15">0</div>
        <div class="stat-label">Projects Built</div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">⭐</div>
        <div class="stat-num" data-target="8">0</div>
        <div class="stat-label">Technologies</div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">☕</div>
        <div class="stat-num" data-target="500">0</div>
        <div class="stat-label">Coffees Drunk</div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">🐛</div>
        <div class="stat-num" data-target="1000">0</div>
        <div class="stat-label">Bugs Squashed</div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">💡</div>
        <div class="stat-num" data-target="2">0</div>
        <div class="stat-label">Years Coding</div>
      </div>
      <div class="stat-card">
        <div class="stat-icon">🏆</div>
        <div class="stat-num" data-target="100">0</div>
        <div class="stat-label">LeetCode Solved</div>
      </div>
    </div>
  </section>

  <!-- Connect -->
  <section id="connect" class="section fade-up">
    <div class="section-header">
      <span class="section-num">04</span>
      <h2 class="section-title">Connect</h2>
      <div class="section-line"></div>
    </div>
    <div class="social-grid">
      <a href="https://github.com/ayushga03" target="_blank" class="social-card">
        <span class="social-icon">⌥</span>
        <div>
          <div class="social-name">GitHub</div>
          <div class="social-handle">@ayushga03</div>
        </div>
      </a>
      <a href="https://linkedin.com/in/ayush-gaurav" target="_blank" class="social-card">
        <span class="social-icon">💼</span>
        <div>
          <div class="social-name">LinkedIn</div>
          <div class="social-handle">ayush-gaurav</div>
        </div>
      </a>
      <a href="https://leetcode.com/ayush-gaurav" target="_blank" class="social-card">
        <span class="social-icon">🧩</span>
        <div>
          <div class="social-name">LeetCode</div>
          <div class="social-handle">ayush gaurav</div>
        </div>
      </a>
      <a href="https://instagram.com/codewayush" target="_blank" class="social-card">
        <span class="social-icon">📸</span>
        <div>
          <div class="social-name">Instagram</div>
          <div class="social-handle">@codewayush</div>
        </div>
      </a>
      <a href="https://www.youtube.com/c/codcoder" target="_blank" class="social-card">
        <span class="social-icon">▶</span>
        <div>
          <div class="social-name">YouTube</div>
          <div class="social-handle">codcoder</div>
        </div>
      </a>
      <a href="mailto:ayushgaurav.dev@gmail.com" class="social-card">
        <span class="social-icon">✉</span>
        <div>
          <div class="social-name">Email</div>
          <div class="social-handle">ayushgaurav.dev@gmail.com</div>
        </div>
      </a>
    </div>
  </section>

  <!-- Quote -->
  <section class="section fade-up">
    <div class="quote-card">
      <div class="quote-mark">"</div>
      <p class="quote-text" id="quote-text">Loading a dev quote...</p>
      <p class="quote-author" id="quote-author"></p>
    </div>
    <br>
    <div style="text-align:center">
      <button class="btn btn-outline" onclick="fetchQuote()">↻ New Quote</button>
    </div>
  </section>

  <!-- Footer -->
  <footer style="text-align:center; padding:24px 0; border-top:1px solid var(--border); color:var(--muted); font-size:11px; letter-spacing:1px;">
    ⭐ FROM <a href="https://github.com/ayushga03" style="color:var(--accent); text-decoration:none;">AYUSHGA03</a> — BUILT WITH ❤️ & LOTS OF ☕
  </footer>

</div>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursor-ring');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });

  function animateRing() {
    rx += (mx - rx) * 0.1;
    ry += (my - ry) * 0.1;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  document.querySelectorAll('a, button, .pill, .stat-card, .social-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(2.5)';
      ring.style.opacity = '0';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(1)';
      ring.style.opacity = '0.5';
    });
  });

  // Typewriter
  const lines = [
    "Building scalable web apps...",
    "React + Node.js + MongoDB",
    "Solving DSA problems in Java",
    "Animating with GSAP ✨",
    "Open to new opportunities 🚀"
  ];
  let li = 0, ci = 0, deleting = false;
  const tw = document.getElementById('typewriter');

  function type() {
    const current = lines[li];
    if (!deleting) {
      tw.textContent = current.slice(0, ++ci);
      if (ci === current.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      tw.textContent = current.slice(0, --ci);
      if (ci === 0) { deleting = false; li = (li + 1) % lines.length; }
    }
    setTimeout(type, deleting ? 40 : 70);
  }
  type();

  // Scroll fade-in
  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

  // Counter animation
  function animateCounters() {
    document.querySelectorAll('[data-target]').forEach(el => {
      const target = +el.dataset.target;
      let current = 0;
      const step = target / 60;
      const interval = setInterval(() => {
        current = Math.min(current + step, target);
        el.textContent = Math.floor(current) + (target >= 100 ? '+' : '');
        if (current >= target) clearInterval(interval);
      }, 16);
    });
  }

  const statsObserver = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting) {
      animateCounters();
      statsObserver.disconnect();
    }
  }, { threshold: 0.3 });
  statsObserver.observe(document.getElementById('stats'));

  // Dev quotes
  const quotes = [
    { text: "Any fool can write code that a computer can understand. Good programmers write code that humans can understand.", author: "— Martin Fowler" },
    { text: "First, solve the problem. Then, write the code.", author: "— John Johnson" },
    { text: "Experience is the name everyone gives to their mistakes.", author: "— Oscar Wilde" },
    { text: "In order to be irreplaceable, one must always be different.", author: "— Coco Chanel" },
    { text: "Java is to JavaScript what car is to Carpet.", author: "— Chris Heilmann" },
    { text: "Knowledge is power.", author: "— Francis Bacon" },
    { text: "Sometimes it pays to stay in bed on Monday, rather than spending the rest of the week debugging Monday's code.", author: "— Dan Salomon" },
    { text: "Simplicity is the soul of efficiency.", author: "— Austin Freeman" },
    { text: "Before software can be reusable it first has to be usable.", author: "— Ralph Johnson" },
    { text: "Make it work, make it right, make it fast.", author: "— Kent Beck" }
  ];
  let lastQuote = -1;

  function fetchQuote() {
    let idx;
    do { idx = Math.floor(Math.random() * quotes.length); } while (idx === lastQuote);
    lastQuote = idx;
    const q = quotes[idx];
    const el = document.getElementById('quote-text');
    const auth = document.getElementById('quote-author');
    el.style.opacity = 0;
    auth.style.opacity = 0;
    setTimeout(() => {
      el.textContent = q.text;
      auth.textContent = q.author;
      el.style.transition = 'opacity 0.4s';
      auth.style.transition = 'opacity 0.4s';
      el.style.opacity = 1;
      auth.style.opacity = 1;
    }, 200);
  }
  fetchQuote();
</script>
</body>
</html>
