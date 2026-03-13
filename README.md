<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Claude Dusengimana — Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800;900&family=Fira+Code:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #030712;
    --surface: #0d1117;
    --surface2: #161b22;
    --surface3: #1c2333;
    --cyan: #00e5ff;
    --cyan-dim: rgba(0,229,255,0.15);
    --cyan-glow: rgba(0,229,255,0.4);
    --green: #39ff14;
    --amber: #ffb700;
    --purple: #a855f7;
    --red: #ff4757;
    --text: #e6edf3;
    --text-muted: #7d8590;
    --border: rgba(0,229,255,0.12);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* SCANLINE OVERLAY */
  body::after {
    content: '';
    position: fixed; inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
    pointer-events: none;
    z-index: 999;
  }

  /* NOISE TEXTURE */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 998; opacity: 0.4;
  }

  .wrapper { max-width: 900px; margin: 0 auto; padding: 40px 24px 80px; position: relative; }

  /* ── HERO ── */
  .hero {
    position: relative;
    padding: 60px 0 48px;
    text-align: center;
  }

  .hero-grid-bg {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 40px 40px;
    mask-image: radial-gradient(ellipse 80% 60% at 50% 50%, black 30%, transparent 100%);
    animation: gridPulse 4s ease-in-out infinite;
  }

  @keyframes gridPulse {
    0%, 100% { opacity: 0.5; }
    50% { opacity: 1; }
  }

  .hero-corner {
    position: absolute;
    width: 20px; height: 20px;
    border-color: var(--cyan);
    border-style: solid;
  }
  .hero-corner.tl { top: 0; left: 0; border-width: 2px 0 0 2px; }
  .hero-corner.tr { top: 0; right: 0; border-width: 2px 2px 0 0; }
  .hero-corner.bl { bottom: 0; left: 0; border-width: 0 0 2px 2px; }
  .hero-corner.br { bottom: 0; right: 0; border-width: 0 2px 2px 0; }

  .status-bar {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(57,255,20,0.08);
    border: 1px solid rgba(57,255,20,0.25);
    border-radius: 2px;
    padding: 4px 12px;
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--green);
    letter-spacing: 0.1em;
    margin-bottom: 28px;
    animation: fadeSlideDown 0.6s ease both;
  }
  .status-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--green);
    animation: blink 1.2s ease-in-out infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 900;
    font-size: clamp(42px, 8vw, 80px);
    line-height: 0.95;
    letter-spacing: -0.03em;
    animation: fadeSlideDown 0.7s 0.1s ease both;
  }

  .hero-name .first { color: var(--text); }
  .hero-name .last {
    color: var(--cyan);
    display: block;
    text-shadow: 0 0 30px var(--cyan-glow), 0 0 60px rgba(0,229,255,0.2);
    position: relative;
  }
  .hero-name .last::after {
    content: attr(data-text);
    position: absolute; inset: 0;
    color: transparent;
    background: linear-gradient(90deg, var(--cyan), var(--purple));
    -webkit-background-clip: text; background-clip: text;
    opacity: 0;
    animation: glitch 6s infinite;
  }
  @keyframes glitch {
    0%,94%,100%{ opacity:0; transform:none; }
    95%{ opacity:0.8; transform:translate(-2px,1px) skewX(-2deg); }
    97%{ opacity:0.6; transform:translate(2px,-1px) skewX(1deg); }
  }

  .hero-title {
    font-family: 'Fira Code', monospace;
    font-size: 13px;
    color: var(--text-muted);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-top: 16px;
    animation: fadeSlideDown 0.7s 0.2s ease both;
  }
  .hero-title span { color: var(--cyan); }

  .hero-bio {
    max-width: 560px; margin: 24px auto 0;
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--text-muted);
    line-height: 1.8;
    animation: fadeSlideDown 0.7s 0.3s ease both;
  }
  .hero-bio strong { color: var(--cyan); font-weight: 700; }

  /* TERMINAL BLOCK */
  .terminal {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 4px;
    margin: 36px 0;
    overflow: hidden;
    animation: fadeSlideDown 0.7s 0.4s ease both;
    box-shadow: 0 0 40px rgba(0,229,255,0.05), inset 0 1px 0 rgba(255,255,255,0.03);
  }
  .terminal-bar {
    background: var(--surface2);
    padding: 10px 16px;
    display: flex; align-items: center; gap: 8px;
    border-bottom: 1px solid var(--border);
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot.r { background: #ff5f57; }
  .dot.y { background: #ffbd2e; }
  .dot.g { background: #28ca41; }
  .terminal-title {
    flex: 1; text-align: center;
    font-family: 'Fira Code', monospace;
    font-size: 11px; color: var(--text-muted);
  }
  .terminal-body { padding: 20px 20px 24px; }
  .tline {
    font-family: 'Fira Code', monospace;
    font-size: 12.5px;
    line-height: 2;
    white-space: pre;
  }
  .tline .prompt { color: var(--green); }
  .tline .cmd { color: var(--cyan); }
  .tline .arg { color: var(--amber); }
  .tline .out { color: var(--text-muted); margin-left: 4px; }
  .tline .val { color: var(--text); }
  .tline .ok { color: var(--green); }
  .tline .warn { color: var(--amber); }
  .cursor {
    display: inline-block; width: 8px; height: 14px;
    background: var(--cyan); vertical-align: middle;
    animation: blink 1s steps(1) infinite;
  }

  /* SECTION HEADERS */
  .section-label {
    display: flex; align-items: center; gap: 12px;
    margin: 48px 0 24px;
    animation: fadeSlideDown 0.6s ease both;
  }
  .section-label::before {
    content: '//';
    font-family: 'Fira Code', monospace;
    font-size: 14px;
    color: var(--cyan);
    opacity: 0.6;
  }
  .section-label h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 22px;
    letter-spacing: -0.01em;
    color: var(--text);
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border) 0%, transparent 100%);
  }

  /* SKILL GRID */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 10px;
    margin-bottom: 12px;
  }
  .skill-pill {
    display: flex; align-items: center; gap: 8px;
    padding: 9px 14px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 3px;
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--text-muted);
    transition: all 0.2s;
    cursor: default;
  }
  .skill-pill:hover {
    border-color: var(--cyan);
    color: var(--cyan);
    background: var(--cyan-dim);
    transform: translateY(-1px);
    box-shadow: 0 4px 20px rgba(0,229,255,0.1);
  }
  .skill-pill .icon { font-size: 14px; }
  .skill-category {
    font-family: 'Fira Code', monospace;
    font-size: 10px;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin: 20px 0 10px;
    opacity: 0.6;
  }

  /* PROJECT CARDS */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }
  @media(max-width:600px){ .projects-grid{ grid-template-columns:1fr; } }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 22px;
    position: relative;
    overflow: hidden;
    transition: all 0.25s;
    cursor: default;
  }
  .project-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent, var(--cyan)), transparent);
    opacity: 0;
    transition: opacity 0.25s;
  }
  .project-card:hover {
    border-color: var(--accent, var(--cyan));
    transform: translateY(-2px);
    box-shadow: 0 8px 40px rgba(0,0,0,0.4);
  }
  .project-card:hover::before { opacity: 1; }
  .project-card[data-accent="green"] { --accent: var(--green); }
  .project-card[data-accent="amber"] { --accent: var(--amber); }
  .project-card[data-accent="purple"] { --accent: var(--purple); }

  .project-icon {
    font-size: 22px; margin-bottom: 12px;
  }
  .project-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 14px;
    color: var(--text);
    margin-bottom: 8px;
  }
  .project-desc {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
    line-height: 1.7;
    margin-bottom: 14px;
  }
  .tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    padding: 2px 8px;
    font-family: 'Fira Code', monospace;
    font-size: 10px;
    border-radius: 2px;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.07);
    color: var(--text-muted);
  }

  /* STATS ROW */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin: 24px 0;
  }
  @media(max-width:600px){ .stats-row{ grid-template-columns: repeat(2,1fr); } }

  .stat-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 18px 14px;
    text-align: center;
    transition: all 0.2s;
  }
  .stat-box:hover {
    border-color: var(--cyan);
    box-shadow: 0 0 20px rgba(0,229,255,0.08);
  }
  .stat-val {
    font-family: 'Syne', sans-serif;
    font-weight: 900;
    font-size: 28px;
    color: var(--cyan);
    line-height: 1;
    text-shadow: 0 0 20px var(--cyan-glow);
  }
  .stat-label {
    font-family: 'Fira Code', monospace;
    font-size: 9px;
    color: var(--text-muted);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-top: 6px;
  }

  /* ACTIVITY BAR */
  .activity-bar {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 20px;
    margin: 16px 0;
  }
  .bar-label {
    display: flex; justify-content: space-between;
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--text-muted);
    margin-bottom: 8px;
  }
  .bar-label .name { color: var(--text); }
  .bar-track {
    height: 6px;
    background: rgba(255,255,255,0.05);
    border-radius: 1px;
    overflow: hidden;
    margin-bottom: 12px;
  }
  .bar-fill {
    height: 100%;
    border-radius: 1px;
    transition: width 1.5s cubic-bezier(0.22,1,0.36,1);
    width: 0;
  }

  /* CONNECT */
  .connect-row {
    display: flex; gap: 12px; flex-wrap: wrap;
    margin-top: 28px;
  }
  .connect-btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 10px 18px;
    font-family: 'Fira Code', monospace;
    font-size: 12px;
    color: var(--text-muted);
    border: 1px solid var(--border);
    background: var(--surface);
    border-radius: 3px;
    text-decoration: none;
    transition: all 0.2s;
  }
  .connect-btn:hover {
    color: var(--cyan);
    border-color: var(--cyan);
    background: var(--cyan-dim);
    transform: translateY(-1px);
  }

  /* FOOTER */
  .footer {
    margin-top: 60px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 12px;
  }
  .footer-left {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--text-muted);
  }
  .footer-left span { color: var(--cyan); }
  .footer-right {
    display: flex; gap: 16px;
  }
  .footer-right a {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--text-muted);
    text-decoration: none;
    transition: color 0.15s;
  }
  .footer-right a:hover { color: var(--cyan); }

  /* ANIMATIONS */
  @keyframes fadeSlideDown {
    from { opacity:0; transform:translateY(-12px); }
    to   { opacity:1; transform:translateY(0); }
  }

  /* LOCATION BADGE */
  .location-badge {
    display: inline-flex; align-items: center; gap: 6px;
    font-family: 'Fira Code', monospace;
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    margin-top: 14px;
  }
  .location-badge::before {
    content: '📍';
    font-size: 12px;
  }

  /* Glow orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    opacity: 0.06;
    z-index: 0;
  }
  .orb-1 { width:400px; height:400px; background:var(--cyan); top:-100px; right:-100px; animation: orbDrift 12s ease-in-out infinite; }
  .orb-2 { width:300px; height:300px; background:var(--purple); bottom:100px; left:-80px; animation: orbDrift 15s ease-in-out infinite reverse; }
  @keyframes orbDrift {
    0%,100%{ transform:translate(0,0); }
    50%{ transform:translate(30px,20px); }
  }

  .wrapper > * { position: relative; z-index: 1; }
</style>
</head>
<body>

<div class="orb orb-1"></div>
<div class="orb orb-2"></div>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-grid-bg"></div>
    <div class="hero-corner tl"></div>
    <div class="hero-corner tr"></div>
    <div class="hero-corner bl"></div>
    <div class="hero-corner br"></div>

    <div class="status-bar">
      <div class="status-dot"></div>
      SYSTEM ONLINE · THREATS MINIMIZED · LEARNING: ENABLED
    </div>

    <div class="hero-name">
      <span class="first">CLAUDE</span>
      <span class="last" data-text="DUSENGIMANA">DUSENGIMANA</span>
    </div>

    <div class="hero-title">
      Senior Network &amp; Security Engineer · <span>IoT Researcher</span> · MSc IT
    </div>

    <p class="hero-bio">
      I <strong>harden critical infrastructure</strong> and <strong>reverse-engineer IoT firmware</strong>.<br/>
      Bridging hardware-level security with AI-driven threat detection — one zero-day at a time.
    </p>

    <div class="location-badge">KIGALI, RWANDA · UTC+2</div>
  </div>

  <!-- TERMINAL -->
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot r"></div>
      <div class="dot y"></div>
      <div class="dot g"></div>
      <div class="terminal-title">claude@kigali:~$ — bash</div>
    </div>
    <div class="terminal-body">
      <div class="tline"><span class="prompt">❯</span> <span class="cmd">whoami</span></div>
      <div class="tline"><span class="out">→</span> <span class="val">Claude Dusengimana — Security Engineer, Researcher, Builder</span></div>
      <div class="tline"> </div>
      <div class="tline"><span class="prompt">❯</span> <span class="cmd">cat</span> <span class="arg">./expertise.json</span></div>
      <div class="tline"><span class="out">{</span></div>
      <div class="tline"><span class="out">  "specialization":</span> <span class="val">["IoT Firmware Security", "Network Hardening", "AI/ML Threat Detection"],</span></div>
      <div class="tline"><span class="out">  "clearance":</span> <span class="val">"Critical Infrastructure",</span></div>
      <div class="tline"><span class="out">  "status":</span> <span class="ok">"Open to Research Collaboration"</span></div>
      <div class="tline"><span class="out">}</span></div>
      <div class="tline"> </div>
      <div class="tline"><span class="prompt">❯</span> <span class="cmd">nmap</span> <span class="arg">--open-to-opportunity</span> <span class="val">claude.local</span></div>
      <div class="tline"><span class="out">Scanning...</span> <span class="ok">3 ports open:</span> <span class="val">research / collaboration / hire</span></div>
      <div class="tline"> </div>
      <div class="tline"><span class="prompt">❯</span> <span class="cmd">sudo</span> <span class="arg">systemctl</span> <span class="val">status curiosity.service</span></div>
      <div class="tline"><span class="ok">● curiosity.service</span> <span class="out">— Active: running since birth</span></div>
      <div class="tline"><span class="prompt">❯</span> <span class="cursor"></span></div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section-label" style="margin-top:40px"><h2>BY THE NUMBERS</h2></div>
  <div class="stats-row">
    <div class="stat-box">
      <div class="stat-val">5+</div>
      <div class="stat-label">Yrs Experience</div>
    </div>
    <div class="stat-box">
      <div class="stat-val">4</div>
      <div class="stat-label">Research Projects</div>
    </div>
    <div class="stat-box">
      <div class="stat-val">3</div>
      <div class="stat-label">Cloud Platforms</div>
    </div>
    <div class="stat-box">
      <div class="stat-val">∞</div>
      <div class="stat-label">CVEs to Hunt</div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section-label"><h2>CYBER ARSENAL</h2></div>

  <div class="skill-category">// Security & Infrastructure</div>
  <div class="skills-grid">
    <div class="skill-pill"><span class="icon">🛡️</span> Cybersecurity</div>
    <div class="skill-pill"><span class="icon">📡</span> IoT Security</div>
    <div class="skill-pill"><span class="icon">🔌</span> Network Eng.</div>
    <div class="skill-pill"><span class="icon">🐧</span> Linux Kernel</div>
    <div class="skill-pill"><span class="icon">☁️</span> AWS</div>
    <div class="skill-pill"><span class="icon">🔷</span> Azure</div>
    <div class="skill-pill"><span class="icon">🔒</span> Firmware RE</div>
    <div class="skill-pill"><span class="icon">🦈</span> Wireshark</div>
  </div>

  <div class="skill-category">// Development & AI/ML</div>
  <div class="skills-grid">
    <div class="skill-pill"><span class="icon">🐍</span> Python</div>
    <div class="skill-pill"><span class="icon">⚡</span> Bash</div>
    <div class="skill-pill"><span class="icon">⚙️</span> C / Embedded</div>
    <div class="skill-pill"><span class="icon">🧠</span> TensorFlow</div>
    <div class="skill-pill"><span class="icon">📊</span> Scikit-learn</div>
    <div class="skill-pill"><span class="icon">🗃️</span> PostgreSQL</div>
    <div class="skill-pill"><span class="icon">🔍</span> Binwalk</div>
    <div class="skill-pill"><span class="icon">📦</span> Logstash</div>
  </div>

  <!-- SKILL PROFICIENCY BARS -->
  <div class="activity-bar" style="margin-top:20px">
    <div class="bar-label"><span class="name">Penetration Testing</span><span>92%</span></div>
    <div class="bar-track"><div class="bar-fill" data-w="92" style="background: linear-gradient(90deg, var(--cyan), #0099aa);"></div></div>

    <div class="bar-label"><span class="name">IoT Firmware Analysis</span><span>88%</span></div>
    <div class="bar-track"><div class="bar-fill" data-w="88" style="background: linear-gradient(90deg, var(--green), #1a8c00);"></div></div>

    <div class="bar-label"><span class="name">ML Threat Detection</span><span>81%</span></div>
    <div class="bar-track"><div class="bar-fill" data-w="81" style="background: linear-gradient(90deg, var(--purple), #6b21a8);"></div></div>

    <div class="bar-label"><span class="name">Cloud Security (AWS/Azure)</span><span>85%</span></div>
    <div class="bar-track"><div class="bar-fill" data-w="85" style="background: linear-gradient(90deg, var(--amber), #b45309); margin-bottom:0;"></div></div>
  </div>

  <!-- PROJECTS -->
  <div class="section-label"><h2>ACTIVE RESEARCH</h2></div>
  <div class="projects-grid">
    <div class="project-card">
      <div class="project-icon">🔍</div>
      <div class="project-name">Firmware Vulnerability Scanner</div>
      <div class="project-desc">Automated static analysis for embedded devices. Detects hardcoded secrets, backdoors, and weak crypto implementations in binary firmware images.</div>
      <div class="tags">
        <span class="tag">Python</span>
        <span class="tag">Binwalk</span>
        <span class="tag">Firmwalker</span>
        <span class="tag">Static Analysis</span>
      </div>
    </div>

    <div class="project-card" data-accent="green">
      <div class="project-icon">🧠</div>
      <div class="project-name">AI Intrusion Detection (IDS)</div>
      <div class="project-desc">Deep learning network guard that identifies real-time DoS attacks and lateral movement within corporate infrastructure at packet-level precision.</div>
      <div class="tags">
        <span class="tag">Scikit-learn</span>
        <span class="tag">PCAP Forensics</span>
        <span class="tag">TensorFlow</span>
      </div>
    </div>

    <div class="project-card" data-accent="amber">
      <div class="project-icon">👶</div>
      <div class="project-name">Smart Neonatal IoT Monitor</div>
      <div class="project-desc">Mission-critical biometric monitoring for neonatal care. AI-driven alerting with real-time SpO₂ tracking and anomaly detection for clinical environments.</div>
      <div class="tags">
        <span class="tag">MicroPython</span>
        <span class="tag">Embedded</span>
        <span class="tag">SpO₂ Sensors</span>
      </div>
    </div>

    <div class="project-card" data-accent="purple">
      <div class="project-icon">📊</div>
      <div class="project-name">Security Log SIEM</div>
      <div class="project-desc">Custom-built log harvester detecting brute-force patterns and geographic anomalies across Linux server clusters with real-time threat correlation.</div>
      <div class="tags">
        <span class="tag">Logstash</span>
        <span class="tag">Python</span>
        <span class="tag">Threat Hunting</span>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section-label"><h2>OPEN CHANNELS</h2></div>
  <p style="font-family:'Fira Code',monospace; font-size:12px; color:var(--text-muted); margin-bottom:20px; line-height:1.8;">
    Available for <span style="color:var(--cyan)">security research</span>, <span style="color:var(--green)">IoT hardening</span>, and <span style="color:var(--purple)">cloud infrastructure</span> collaboration.<br/>
    Response time: <span style="color:var(--amber)">24–48h</span> · Timezone: UTC+2 · Preferred: email
  </p>
  <div class="connect-row">
    <a class="connect-btn" href="mailto:dusenge125@gmail.com">✉ dusenge125@gmail.com</a>
    <a class="connect-btn" href="https://linkedin.com/in/dusengimana-claude">in linkedin</a>
    <a class="connect-btn" href="https://github.com/claude125">⌥ github/claude125</a>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-left">
      <span>EOF</span> · claude_dusengimana.profile · <span>v2.0.26</span>
    </div>
    <div class="footer-right">
      <a href="#">Kigali, RW</a>
      <a href="#">MSc IT</a>
      <a href="#">Open to Research</a>
    </div>
  </div>

</div>

<script>
  // Animate skill bars on load
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.querySelectorAll('.bar-fill').forEach(el => {
        el.style.width = el.dataset.w + '%';
      });
    }, 400);
  });

  // Subtle cursor glow
  const orb1 = document.querySelector('.orb-1');
  document.addEventListener('mousemove', e => {
    const x = e.clientX, y = e.clientY;
    orb1.style.left = (x - 200) + 'px';
    orb1.style.top  = (y - 200) + 'px';
    orb1.style.transition = 'left 1.2s ease, top 1.2s ease';
  });

  // Typewriter glitch on name hover
  const nameEl = document.querySelector('.hero-name .last');
  const originalText = nameEl.childNodes[0].nodeValue;
  const chars = '█▓░ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%';
  nameEl.addEventListener('mouseenter', () => {
    let iterations = 0;
    const interval = setInterval(() => {
      nameEl.childNodes[0].nodeValue = originalText
        .split('')
        .map((char, i) => {
          if (i < iterations) return char;
          return char === ' ' ? ' ' : chars[Math.floor(Math.random() * chars.length)];
        })
        .join('');
      if (iterations >= originalText.length) clearInterval(interval);
      iterations += 1.2;
    }, 30);
  });
</script>
</body>
</html>
