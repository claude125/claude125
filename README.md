<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Claude Dusengimana — Security Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060810;
    --bg2: #0b0f1a;
    --bg3: #0f1525;
    --accent: #00e5ff;
    --accent2: #7b2fff;
    --accent3: #00ff9d;
    --warn: #ff4b6e;
    --text: #cdd6f4;
    --text-dim: #6b7a99;
    --border: rgba(0,229,255,0.12);
    --glow: 0 0 20px rgba(0,229,255,0.15);
    --font-mono: 'Space Mono', monospace;
    --font-display: 'Syne', sans-serif;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-mono);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* Glowing orbs */
  body::after {
    content: '';
    position: fixed;
    top: -200px;
    right: -200px;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(123,47,255,0.12) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
    animation: orb-float 8s ease-in-out infinite;
  }

  @keyframes orb-float {
    0%, 100% { transform: translate(0, 0); }
    50% { transform: translate(-30px, 30px); }
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── HEADER ── */
  .hero {
    padding: 60px 0 50px;
    position: relative;
  }

  .hero-tag {
    font-family: var(--font-mono);
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
    opacity: 0;
    animation: fade-up 0.6s ease forwards 0.1s;
  }

  .hero-tag::before {
    content: '';
    width: 30px;
    height: 1px;
    background: var(--accent);
  }

  .hero-name {
    font-family: var(--font-display);
    font-size: clamp(42px, 7vw, 72px);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -0.02em;
    background: linear-gradient(135deg, #ffffff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fade-up 0.6s ease forwards 0.2s;
  }

  .hero-title {
    font-family: var(--font-display);
    font-size: clamp(14px, 2vw, 18px);
    font-weight: 600;
    color: var(--text-dim);
    margin-top: 12px;
    letter-spacing: 0.05em;
    opacity: 0;
    animation: fade-up 0.6s ease forwards 0.3s;
  }

  .hero-location {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    margin-top: 16px;
    font-size: 12px;
    color: var(--accent3);
    opacity: 0;
    animation: fade-up 0.6s ease forwards 0.4s;
  }

  .hero-location::before { content: '▸'; }

  /* Cursor blink after name */
  .cursor {
    display: inline-block;
    width: 3px;
    height: 0.85em;
    background: var(--accent);
    margin-left: 4px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }

  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  /* ── SECTION HEADERS ── */
  .section {
    margin-top: 56px;
    opacity: 0;
    animation: fade-up 0.5s ease forwards;
  }

  .section:nth-child(2) { animation-delay: 0.5s; }
  .section:nth-child(3) { animation-delay: 0.6s; }
  .section:nth-child(4) { animation-delay: 0.7s; }
  .section:nth-child(5) { animation-delay: 0.8s; }
  .section:nth-child(6) { animation-delay: 0.9s; }

  @keyframes fade-up {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }

  .section-cmd {
    font-family: var(--font-mono);
    font-size: 13px;
    font-weight: 700;
    color: var(--accent);
  }

  .section-cmd::before { content: '$ '; color: var(--accent2); }

  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── WHOAMI CARD ── */
  .whoami-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px 32px;
    position: relative;
    overflow: hidden;
    box-shadow: var(--glow);
  }

  .whoami-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent2), var(--accent), var(--accent3));
  }

  .yaml-row {
    display: grid;
    grid-template-columns: 110px 1fr;
    gap: 8px;
    padding: 5px 0;
    font-size: 13px;
    line-height: 1.6;
    border-bottom: 1px solid rgba(255,255,255,0.03);
  }

  .yaml-row:last-child { border-bottom: none; }

  .yaml-key {
    color: var(--accent);
    font-weight: 700;
  }

  .yaml-val { color: var(--text); }

  .yaml-val .flag { font-size: 15px; }

  .yaml-val .array {
    color: var(--accent3);
  }

  /* ── EXPERIENCE ── */
  .exp-list { display: flex; flex-direction: column; gap: 16px; }

  .exp-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px 28px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, box-shadow 0.3s;
  }

  .exp-card:hover {
    border-color: rgba(0,229,255,0.3);
    box-shadow: var(--glow);
  }

  .exp-card::before {
    content: '▶';
    position: absolute;
    top: 24px;
    left: -1px;
    color: var(--accent);
    font-size: 10px;
    transform: translateX(-50%);
    background: var(--bg);
    padding: 2px 4px;
    border-radius: 3px;
  }

  .exp-org {
    font-family: var(--font-display);
    font-size: 17px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 2px;
  }

  .exp-role {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 14px;
  }

  .exp-items {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .exp-items li {
    font-size: 12.5px;
    color: var(--text-dim);
    padding-left: 20px;
    position: relative;
  }

  .exp-items li::before {
    content: '├──';
    position: absolute;
    left: 0;
    color: var(--accent2);
    font-size: 11px;
  }

  .exp-items li:last-child::before { content: '└──'; }

  /* ── SKILLS ── */
  .skills-grid {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .skill-group-label {
    font-size: 10px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text-dim);
    margin-bottom: 10px;
  }

  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 6px;
    font-size: 11.5px;
    font-weight: 700;
    letter-spacing: 0.05em;
    border: 1px solid;
    transition: all 0.25s;
    cursor: default;
  }

  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,0,0,0.4);
  }

  .badge-lang {
    background: rgba(0,229,255,0.06);
    border-color: rgba(0,229,255,0.2);
    color: var(--accent);
  }

  .badge-platform {
    background: rgba(123,47,255,0.06);
    border-color: rgba(123,47,255,0.25);
    color: #a78bfa;
  }

  .badge-icon { font-size: 13px; }

  /* ── PROJECTS ── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }

  .proj-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 22px;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    cursor: default;
  }

  .proj-card:hover {
    transform: translateY(-4px);
    border-color: rgba(0,229,255,0.25);
    box-shadow: 0 8px 32px rgba(0,0,0,0.4), var(--glow);
  }

  .proj-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .proj-card:hover::after { opacity: 1; }

  .proj-card.c1::after { background: linear-gradient(90deg, var(--accent2), var(--accent)); }
  .proj-card.c2::after { background: linear-gradient(90deg, var(--accent), var(--accent3)); }
  .proj-card.c3::after { background: linear-gradient(90deg, var(--warn), var(--accent2)); }
  .proj-card.c4::after { background: linear-gradient(90deg, var(--accent3), var(--accent)); }
  .proj-card.c5::after { background: linear-gradient(90deg, var(--accent), var(--warn)); }
  .proj-card.c6::after { background: linear-gradient(90deg, var(--accent2), var(--accent3)); }

  .proj-icon {
    font-size: 26px;
    margin-bottom: 12px;
    display: block;
  }

  .proj-name {
    font-family: var(--font-display);
    font-size: 14px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 8px;
    line-height: 1.3;
  }

  .proj-desc {
    font-size: 11.5px;
    color: var(--text-dim);
    line-height: 1.7;
    margin-bottom: 14px;
  }

  .proj-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .proj-tag {
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 4px;
    background: rgba(255,255,255,0.05);
    color: var(--text-dim);
    border: 1px solid rgba(255,255,255,0.07);
  }

  /* ── RESEARCH ── */
  .research-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px 32px;
    position: relative;
    overflow: hidden;
  }

  .research-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 4px;
    height: 100%;
    background: linear-gradient(180deg, var(--accent2), var(--accent));
  }

  .research-degree {
    font-size: 11px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 8px;
  }

  .research-title {
    font-family: var(--font-display);
    font-size: 20px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 20px;
    line-height: 1.3;
  }

  .research-focus {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .research-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 12.5px;
    color: var(--text-dim);
    line-height: 1.5;
  }

  .research-item::before {
    content: '·';
    color: var(--accent);
    font-size: 18px;
    line-height: 1;
    flex-shrink: 0;
    margin-top: -1px;
  }

  /* ── CONNECT ── */
  .connect-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }

  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 12px 22px;
    border-radius: 8px;
    font-family: var(--font-mono);
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-decoration: none;
    border: 1px solid;
    transition: all 0.25s;
  }

  .connect-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0,0,0,0.4);
  }

  .btn-linkedin {
    background: rgba(10,102,194,0.12);
    border-color: rgba(10,102,194,0.4);
    color: #5ba4f5;
  }

  .btn-email {
    background: rgba(234,67,53,0.1);
    border-color: rgba(234,67,53,0.35);
    color: #f28b82;
  }

  .btn-github {
    background: rgba(255,255,255,0.05);
    border-color: rgba(255,255,255,0.15);
    color: var(--text);
  }

  /* ── STATUS BAR ── */
  .status-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-top: 6px;
    font-size: 11px;
    color: var(--text-dim);
  }

  .status-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--accent3);
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  /* Divider */
  hr {
    border: none;
    border-top: 1px solid var(--border);
    margin: 48px 0;
  }

  @media (max-width: 600px) {
    .yaml-row { grid-template-columns: 90px 1fr; }
    .projects-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">Network &amp; Security Engineer</div>
    <div class="hero-name">Claude Dusengimana<span class="cursor"></span></div>
    <div class="hero-title">Senior Network &amp; Security Engineer · Cybersecurity · IoT · AI Systems</div>
    <div class="hero-location">Kigali, Rwanda 🇷🇼</div>
    <div class="status-bar" style="margin-top:18px;">
      <span class="status-dot"></span>
      <span>Open to research collaborations &amp; senior engineering roles</span>
    </div>
  </div>

  <!-- WHOAMI -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">whoami</span>
      <div class="section-line"></div>
    </div>
    <div class="whoami-card">
      <div class="yaml-row"><span class="yaml-key">name</span><span class="yaml-val">Claude Dusengimana</span></div>
      <div class="yaml-row"><span class="yaml-key">title</span><span class="yaml-val">Senior Network &amp; Security Engineer</span></div>
      <div class="yaml-row"><span class="yaml-key">location</span><span class="yaml-val">Kigali, Rwanda <span class="flag">🇷🇼</span></span></div>
      <div class="yaml-row"><span class="yaml-key">education</span><span class="yaml-val">MSc Information Technology (Programming)</span></div>
      <div class="yaml-row"><span class="yaml-key">research</span><span class="yaml-val">Security Vulnerabilities in IoT Firmware</span></div>
      <div class="yaml-row"><span class="yaml-key">focus</span><span class="yaml-val"><span class="array">[ Cybersecurity, IoT Security, AI Systems, Infrastructure ]</span></span></div>
      <div class="yaml-row"><span class="yaml-key">status</span><span class="yaml-val">Building secure systems · Researching firmware vulnerabilities</span></div>
    </div>
  </div>

  <!-- EXPERIENCE -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">cat experience.log</span>
      <div class="section-line"></div>
    </div>
    <div class="exp-list">
      <div class="exp-card">
        <div class="exp-org">Kigali Psycho-Medical Center (KPMC)</div>
        <div class="exp-role">Senior Network &amp; Security Engineer</div>
        <ul class="exp-items">
          <li>Securing critical medical infrastructure</li>
          <li>Network architecture &amp; hardening</li>
          <li>Security monitoring &amp; incident response</li>
        </ul>
      </div>
      <div class="exp-card">
        <div class="exp-org">Sheebah Computer Solution Ltd</div>
        <div class="exp-role">Network &amp; Security Engineer</div>
        <ul class="exp-items">
          <li>Infrastructure design &amp; deployment</li>
          <li>Security audits &amp; risk assessment</li>
          <li>System administration &amp; optimization</li>
        </ul>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">ls -la skills/</span>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div>
        <div class="skill-group-label">Languages</div>
        <div class="badge-row">
          <span class="badge badge-lang"><span class="badge-icon">🐍</span> Python</span>
          <span class="badge badge-lang"><span class="badge-icon">⚡</span> Bash</span>
          <span class="badge badge-lang"><span class="badge-icon">🌐</span> JavaScript</span>
          <span class="badge badge-lang"><span class="badge-icon">🗄️</span> SQL</span>
          <span class="badge badge-lang"><span class="badge-icon">⚙️</span> C</span>
          <span class="badge badge-lang"><span class="badge-icon">🐘</span> PHP</span>
        </div>
      </div>
      <div>
        <div class="skill-group-label">Platforms &amp; Domains</div>
        <div class="badge-row">
          <span class="badge badge-platform"><span class="badge-icon">🐧</span> Linux</span>
          <span class="badge badge-platform"><span class="badge-icon">🔐</span> Cybersecurity</span>
          <span class="badge badge-platform"><span class="badge-icon">📡</span> IoT Security</span>
          <span class="badge badge-platform"><span class="badge-icon">🤖</span> Machine Learning</span>
          <span class="badge badge-platform"><span class="badge-icon">☁️</span> AWS</span>
          <span class="badge badge-platform"><span class="badge-icon">☁️</span> Azure</span>
          <span class="badge badge-platform"><span class="badge-icon">🌐</span> Networking</span>
        </div>
      </div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">ls projects/ --sort=impact</span>
      <div class="section-line"></div>
    </div>
    <div class="projects-grid">
      <div class="proj-card c1">
        <span class="proj-icon">🔬</span>
        <div class="proj-name">IoT Firmware Vulnerability Scanner</div>
        <div class="proj-desc">Scans firmware images for hardcoded credentials, weak crypto, and exposed APIs. Core tool for MSc research.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">IoT</span>
          <span class="proj-tag">Firmware</span>
          <span class="proj-tag">CVE</span>
        </div>
      </div>
      <div class="proj-card c2">
        <span class="proj-icon">🤖</span>
        <div class="proj-name">AI Intrusion Detection System</div>
        <div class="proj-desc">ML model classifying network traffic to detect DoS, probe, and R2L intrusions in real time.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">ML</span>
          <span class="proj-tag">Scikit-learn</span>
          <span class="proj-tag">PCAP</span>
        </div>
      </div>
      <div class="proj-card c3">
        <span class="proj-icon">👶</span>
        <div class="proj-name">Smart Baby Care Incubator</div>
        <div class="proj-desc">IoT neonatal monitoring with SpO₂, temperature sensors, AI alerts, and hybrid solar/grid power.</div>
        <div class="proj-tags">
          <span class="proj-tag">IoT</span>
          <span class="proj-tag">Embedded</span>
          <span class="proj-tag">Healthcare</span>
          <span class="proj-tag">AI</span>
        </div>
      </div>
      <div class="proj-card c4">
        <span class="proj-icon">🖥️</span>
        <div class="proj-name">Linux Server Monitoring Tool</div>
        <div class="proj-desc">Lightweight Python daemon tracking CPU, memory, disk &amp; uptime with threshold-based alerts.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">Linux</span>
          <span class="proj-tag">SysAdmin</span>
        </div>
      </div>
      <div class="proj-card c5">
        <span class="proj-icon">🔍</span>
        <div class="proj-name">Security Log Analyzer</div>
        <div class="proj-desc">Parses auth logs to surface brute-force, credential stuffing &amp; geographic anomalies with threat reports.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">Bash</span>
          <span class="proj-tag">SIEM</span>
          <span class="proj-tag">Forensics</span>
        </div>
      </div>
      <div class="proj-card c6">
        <span class="proj-icon">🛡️</span>
        <div class="proj-name">RBAC Authentication System</div>
        <div class="proj-desc">Role-Based Access Control with least-privilege enforcement, audit logging &amp; session management.</div>
        <div class="proj-tags">
          <span class="proj-tag">Python</span>
          <span class="proj-tag">Auth</span>
          <span class="proj-tag">Security</span>
          <span class="proj-tag">RBAC</span>
        </div>
      </div>
    </div>
  </div>

  <!-- RESEARCH -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">cat research.txt</span>
      <div class="section-line"></div>
    </div>
    <div class="research-card">
      <div class="research-degree">MSc Information Technology · Programming</div>
      <div class="research-title">Security Vulnerabilities in IoT Firmware</div>
      <div class="research-focus">
        <div class="research-item">Static analysis of firmware binaries</div>
        <div class="research-item">Hardcoded credential extraction &amp; mapping</div>
        <div class="research-item">Weak cryptographic implementation detection</div>
        <div class="research-item">Attack surface mapping for embedded devices</div>
        <div class="research-item">Mitigation frameworks for IoT manufacturers</div>
      </div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-header">
      <span class="section-cmd">ping dusengimana</span>
      <div class="section-line"></div>
    </div>
    <div class="connect-row">
      <a href="https://linkedin.com/in/dusengimana-claude" class="connect-btn btn-linkedin">
        <span>💼</span> LinkedIn
      </a>
      <a href="mailto:dusenge125@gmail.com" class="connect-btn btn-email">
        <span>✉️</span> dusenge125@gmail.com
      </a>
      <a href="https://github.com/claude125" class="connect-btn btn-github">
        <span>🐙</span> GitHub
      </a>
    </div>
    <div class="status-bar" style="margin-top: 20px;">
      <span class="status-dot"></span>
      <span>Secure channel open · Ready to collaborate</span>
    </div>
  </div>

</div>
</body>
</html>
