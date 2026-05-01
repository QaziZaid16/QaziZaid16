<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Qazi Zaid — README</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0a0a0a;
    color: #c9c9c9;
    font-family: 'Share Tech Mono', monospace;
    min-height: 100vh;
  }

  .scanlines {
    position: fixed;
    top: 0; left: 0; width: 100%; height: 100%;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.06) 2px, rgba(0,0,0,0.06) 4px);
    pointer-events: none;
    z-index: 1000;
  }

  .main {
    background: #0a0a0a;
    display: flex;
    flex-direction: column;
    max-width: 740px;
    margin: 0 auto;
    border-left: 1px solid #1a1a1a;
    border-right: 1px solid #1a1a1a;
    min-height: 100vh;
  }

  /* HERO */
  .hero {
    background: #0d0d0d;
    border-bottom: 1px solid #1f1f1f;
    padding: 36px 24px;
    position: relative;
    overflow: hidden;
    min-height: 130px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background:
      repeating-linear-gradient(90deg, transparent, transparent 40px, rgba(127,255,0,0.015) 40px, rgba(127,255,0,0.015) 41px),
      repeating-linear-gradient(0deg, transparent, transparent 40px, rgba(127,255,0,0.015) 40px, rgba(127,255,0,0.015) 41px);
  }

  .hero-inner { position: relative; text-align: center; }

  .hero-text {
    font-family: 'VT323', monospace;
    font-size: 42px;
    color: #e0e0e0;
    letter-spacing: 2px;
    line-height: 1.15;
  }

  .hero-text .slash { color: #7fff00; font-size: 34px; }

  .cursor {
    display: inline-block;
    width: 3px;
    height: 34px;
    background: #7fff00;
    margin-left: 4px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* NAV BAR */
  .nav-bar {
    display: flex;
    border-bottom: 1px solid #1f1f1f;
    background: #0b0b0b;
  }

  .nav-item {
    font-size: 10px;
    color: #3a3a3a;
    padding: 10px 18px;
    letter-spacing: 2px;
    border-right: 1px solid #161616;
    cursor: pointer;
    text-transform: uppercase;
    transition: all 0.15s;
  }

  .nav-item:hover, .nav-item.active {
    color: #7fff00;
    background: rgba(127,255,0,0.04);
  }

  /* GLITCH BAR */
  .glitch-bar {
    height: 2px;
    background: #111;
    position: relative;
    overflow: hidden;
  }

  .glitch-bar::after {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 60%;
    height: 100%;
    background: linear-gradient(90deg, transparent, #7fff00, transparent);
    animation: scan 4s linear infinite;
  }

  @keyframes scan { 0%{left:-100%} 100%{left:200%} }

  /* TYPING LINE */
  .typing-line {
    font-size: 10px;
    color: #2e2e2e;
    padding: 6px 16px;
    background: #080808;
    border-bottom: 1px solid #111;
    letter-spacing: 1px;
  }

  .typing-line::before { content: '> '; color: #7fff00; }

  .err {
    color: #ff003c;
    font-size: 8px;
    opacity: 0;
    animation: errFlash 12s infinite;
  }

  @keyframes errFlash { 0%,84%,100%{opacity:0} 85%,99%{opacity:0.5} }

  /* CONTENT GRID */
  .content-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: #141414;
    border-bottom: 1px solid #141414;
  }

  .panel {
    background: #0a0a0a;
    padding: 16px;
  }

  .panel-title {
    font-size: 9px;
    letter-spacing: 3px;
    color: #3a3a3a;
    text-transform: uppercase;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .panel-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #1a1a1a;
  }

  /* ABOUT CODE BLOCK */
  .about-code {
    font-size: 11px;
    color: #555;
    line-height: 1.75;
  }

  .about-code .kw  { color: #3a3a8a; }
  .about-code .fn  { color: #7fff00; }
  .about-code .str { color: #8aff8a; }
  .about-code .key { color: #666; }

  /* STATS */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 6px;
  }

  .mini-stat {
    background: #0d0d0d;
    border: 1px solid #1a1a1a;
    padding: 8px 6px;
    text-align: center;
    position: relative;
  }

  .mini-stat::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 2px;
    background: #7fff00;
    opacity: 0.25;
  }

  .mini-stat-val {
    font-family: 'VT323', monospace;
    font-size: 26px;
    color: #7fff00;
    display: block;
    line-height: 1;
  }

  .mini-stat-label {
    font-size: 7px;
    color: #2e2e2e;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-top: 2px;
    display: block;
  }

  /* CONTRIBUTION GRAPH */
  .contrib-graph {
    padding: 16px;
    border-bottom: 1px solid #141414;
  }

  .graph-grid {
    display: flex;
    gap: 3px;
    overflow: hidden;
    margin-top: 10px;
  }

  .graph-col { display: flex; flex-direction: column; gap: 3px; }

  .graph-cell {
    width: 10px;
    height: 10px;
    background: #0f0f0f;
    border: 1px solid #141414;
    border-radius: 1px;
    transition: background 0.1s;
  }

  .graph-cell:hover { outline: 1px solid #7fff00; }
  .graph-cell.l1 { background: #162a16; }
  .graph-cell.l2 { background: #2a5a2a; }
  .graph-cell.l3 { background: #4a8a4a; }
  .graph-cell.l4 { background: #7fff00; }

  /* TECH STRIP */
  .tech-strip {
    padding: 16px;
    border-bottom: 1px solid #141414;
    background: #0b0b0b;
  }

  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 8px;
  }

  .tech-badge {
    font-size: 9px;
    padding: 3px 10px;
    border: 1px solid #1f1f1f;
    color: #4a4a4a;
    letter-spacing: 2px;
    text-transform: uppercase;
    background: #0d0d0d;
    cursor: default;
    transition: all 0.15s;
  }

  .tech-badge::before { content: '['; color: #2a2a2a; margin-right: 3px; }
  .tech-badge::after  { content: ']'; color: #2a2a2a; margin-left: 3px; }

  .tech-badge:hover {
    color: #7fff00;
    border-color: #7fff00;
    background: rgba(127,255,0,0.03);
  }

  .tech-badge.learning {
    border-color: #162a16;
    color: #2a5a2a;
  }

  .tech-badge.learning::before { color: #162a16; }
  .tech-badge.learning::after  { color: #162a16; }
  .tech-badge.learning:hover { color: #7fff00; border-color: #7fff00; }

  /* LANG BARS */
  .lang-strip {
    padding: 16px;
    border-bottom: 1px solid #141414;
  }

  .lang-row {
    margin-bottom: 10px;
  }

  .lang-meta {
    display: flex;
    justify-content: space-between;
    font-size: 9px;
    color: #3a3a3a;
    letter-spacing: 1px;
    margin-bottom: 4px;
  }

  .lang-bar {
    height: 2px;
    background: #111;
  }

  .lang-fill {
    height: 100%;
    background: #7fff00;
  }

  /* QUOTE */
  .quote-strip {
    padding: 12px 20px 12px 28px;
    border-left: 2px solid #1a1a1a;
    margin: 0 16px;
    border-bottom: 1px solid #111;
  }

  .quote-text {
    font-size: 10px;
    color: #2e2e2e;
    font-style: italic;
    line-height: 1.6;
  }

  .quote-sub {
    font-size: 8px;
    color: #1e1e1e;
    letter-spacing: 2px;
    margin-top: 6px;
    font-style: normal;
  }

  /* FOOTER */
  .footer-bar {
    padding: 10px 16px;
    border-top: 1px solid #141414;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #080808;
    margin-top: auto;
  }

  .footer-text {
    font-size: 9px;
    color: #1e1e1e;
    letter-spacing: 2px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .blink-dot {
    width: 5px;
    height: 5px;
    border-radius: 50%;
    background: #7fff00;
    display: inline-block;
    animation: blink 1.5s step-end infinite;
  }

  .views-badge {
    font-size: 9px;
    color: #2a2a2a;
    letter-spacing: 2px;
    border: 1px solid #161616;
    padding: 3px 8px;
  }

  .views-badge span { color: #7fff00; }

  /* GLITCH AVATAR ANIM on name */
  .glitch-heading {
    font-family: 'VT323', monospace;
    font-size: 16px;
    color: #e0e0e0;
    letter-spacing: 1px;
    animation: glitchText 14s infinite;
  }

  @keyframes glitchText {
    0%,88%,100%{text-shadow:none}
    89%{text-shadow:-2px 0 #ff003c,2px 0 #00fff5}
    90%{text-shadow:2px 0 #ff003c,-2px 0 #00fff5}
    91%{text-shadow:none}
  }
</style>
</head>
<body>
<div class="scanlines"></div>

<div class="main">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-inner">
      <div class="hero-text">
        Welcome to Qazi's Github<br>
        <span class="slash">&lt;/&gt;</span><span class="cursor"></span>
      </div>
    </div>
  </div>

  <div class="glitch-bar"></div>

  <!-- NAV -->
  <div class="nav-bar">
    <div class="nav-item active">about</div>
    <div class="nav-item">stack</div>
    <div class="nav-item">stats</div>
    <div class="nav-item">contact</div>
  </div>

  <!-- TYPING LINE -->
  <div class="typing-line">
    initializing profile.md ... done <span class="err">[ERR 0x00]</span>
  </div>

  <!-- ABOUT + STATS GRID -->
  <div class="content-grid">
    <div class="panel">
      <div class="panel-title">// about_me</div>
      <div class="about-code">
        <span class="kw">const</span> <span class="fn">qaziZaid</span> = {<br>
        &nbsp;&nbsp;<span class="key">location:</span> <span class="str">"India"</span>,<br>
        &nbsp;&nbsp;<span class="key">role:</span> <span class="str">"Frontend Dev"</span>,<br>
        &nbsp;&nbsp;<span class="key">focus:</span> <span class="str">"UI/UX"</span>,<br>
        &nbsp;&nbsp;<span class="key">mail:</span> <span class="str">"qazi.zaid16@</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="str">gmail.com"</span>,<br>
        &nbsp;&nbsp;<span class="key">fun:</span> <span class="str">"dark humor"</span>,<br>
        &nbsp;&nbsp;<span class="key">goal:</span> <span class="str">"pixel-perfect</span><br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="str">interfaces"</span><br>
        };
      </div>
    </div>

    <div class="panel">
      <div class="panel-title">// github_stats</div>
      <div class="stats-row">
        <div class="mini-stat">
          <span class="mini-stat-val">—</span>
          <span class="mini-stat-label">Stars</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-val">—</span>
          <span class="mini-stat-label">Commits</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-val">—</span>
          <span class="mini-stat-label">PRs</span>
        </div>
      </div>
      <div class="stats-row" style="margin-top:6px;">
        <div class="mini-stat">
          <span class="mini-stat-val">—</span>
          <span class="mini-stat-label">Issues</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-val">C</span>
          <span class="mini-stat-label">Grade</span>
        </div>
        <div class="mini-stat">
          <span class="mini-stat-val">—</span>
          <span class="mini-stat-label">Streak</span>
        </div>
      </div>
    </div>
  </div>

  <!-- CONTRIBUTION GRAPH -->
  <div class="contrib-graph">
    <div class="panel-title">// contribution_graph</div>
    <div class="graph-grid" id="graph"></div>
  </div>

  <!-- TECH STACK -->
  <div class="tech-strip">
    <div class="panel-title">// technologies</div>
    <div class="tech-grid">
      <div class="tech-badge">HTML5</div>
      <div class="tech-badge">CSS3</div>
      <div class="tech-badge">JavaScript</div>
      <div class="tech-badge">Figma</div>
      <div class="tech-badge">Adobe XD</div>
      <div class="tech-badge">Git</div>
      <div class="tech-badge">GitHub</div>
      <div class="tech-badge">VSCode</div>
      <div class="tech-badge">Photoshop</div>
    </div>
    <div style="margin-top:14px;">
      <div class="panel-title">// currently_learning</div>
      <div class="tech-grid">
        <div class="tech-badge learning">React</div>
        <div class="tech-badge learning">TypeScript</div>
        <div class="tech-badge learning">Advanced CSS</div>
      </div>
    </div>
  </div>

  <!-- LANGUAGES -->
  <div class="lang-strip">
    <div class="panel-title">// top_languages</div>
    <div class="lang-row">
      <div class="lang-meta"><span>HTML</span><span>55%</span></div>
      <div class="lang-bar"><div class="lang-fill" style="width:55%;opacity:0.9;"></div></div>
    </div>
    <div class="lang-row">
      <div class="lang-meta"><span>CSS</span><span>30%</span></div>
      <div class="lang-bar"><div class="lang-fill" style="width:30%;opacity:0.65;"></div></div>
    </div>
    <div class="lang-row" style="margin-bottom:0;">
      <div class="lang-meta"><span>JavaScript</span><span>15%</span></div>
      <div class="lang-bar"><div class="lang-fill" style="width:15%;opacity:0.4;"></div></div>
    </div>
  </div>

  <!-- QUOTE -->
  <div style="padding: 14px 16px; border-bottom: 1px solid #111;">
    <div class="quote-strip">
      <div class="quote-text">&gt; "The best investment you can make is in yourself." — Warren Buffett</div>
      <div class="quote-sub">RUNTIME: QAZIZAID_PROFILE_V1 // INDIA // FRONTEND DIVISION</div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer-bar">
    <div class="footer-text">
      <span class="blink-dot"></span>PROFILE ACTIVE
    </div>
    <div class="views-badge">VIEWS: <span>0x????</span></div>
  </div>

</div>

<script>
  const graph = document.getElementById('graph');
  const seed = [0,0,0,1,1,2,3,4,2,1,0,0,1,2,3,4,3,2,1,0,0,1,2,3,2,1,0,1,1,0,0,1,2,3,4,3,2,1,0,1,2,2,1,0,1,2,3,1,0,0,1,2];
  const lvMap = ['','l1','l2','l3','l4'];

  for (let w = 0; w < 52; w++) {
    const col = document.createElement('div');
    col.className = 'graph-col';
    for (let d = 0; d < 7; d++) {
      const cell = document.createElement('div');
      const idx = (w * 7 + d) % seed.length;
      let lv = seed[idx];
      if (Math.random() < 0.06) lv = Math.floor(Math.random() * 5);
      cell.className = 'graph-cell' + (lv ? ' ' + lvMap[lv] : '');
      col.appendChild(cell);
    }
    graph.appendChild(col);
  }
</script>
</body>
</html>
