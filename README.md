<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>RaheemUllah — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --surface2: #18181f;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.13);
    --accent: #4f8ef7;
    --accent2: #a78bfa;
    --accent3: #34d399;
    --accent4: #fbbf24;
    --text: #f0f0f5;
    --muted: #6b7280;
    --muted2: #9ca3af;
    --mono: 'DM Mono', monospace;
    --sans: 'Syne', sans-serif;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(79,142,247,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(79,142,247,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  /* Glow orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(100px);
    opacity: 0.12;
    pointer-events: none;
    z-index: 0;
    animation: drift 12s ease-in-out infinite alternate;
  }
  .orb1 { width: 500px; height: 500px; background: #4f8ef7; top: -150px; left: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: #a78bfa; bottom: -100px; right: -100px; animation-delay: -6s; }
  .orb3 { width: 300px; height: 300px; background: #34d399; top: 50%; left: 50%; animation-delay: -3s; }

  @keyframes drift {
    0% { transform: translate(0, 0) scale(1); }
    100% { transform: translate(30px, 20px) scale(1.08); }
  }

  /* Layout */
  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 0 24px;
    position: relative;
    z-index: 1;
  }

  /* NAV */
  nav {
    padding: 24px 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
    position: relative;
    z-index: 10;
  }

  .nav-logo {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--accent);
    letter-spacing: 0.05em;
  }

  .nav-links {
    display: flex;
    gap: 28px;
    list-style: none;
  }

  .nav-links a {
    font-size: 13px;
    color: var(--muted2);
    text-decoration: none;
    font-family: var(--mono);
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }

  /* HERO */
  .hero {
    padding: 80px 0 60px;
    position: relative;
  }

  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: var(--mono);
    font-size: 12px;
    color: var(--accent3);
    margin-bottom: 24px;
    letter-spacing: 0.1em;
  }

  .dot-live {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--accent3);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.8); }
  }

  .hero h1 {
    font-size: clamp(48px, 8vw, 80px);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -0.03em;
    margin-bottom: 8px;
  }

  .hero h1 .name-accent {
    background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-subtitle {
    font-size: 16px;
    color: var(--muted2);
    font-family: var(--mono);
    font-weight: 300;
    margin-bottom: 36px;
    line-height: 1.7;
  }

  .hero-subtitle span { color: var(--accent); }

  .hero-actions {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 60px;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--accent);
    color: #fff;
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 500;
    padding: 11px 22px;
    border-radius: 6px;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.15s;
  }
  .btn-primary:hover { opacity: 0.85; transform: translateY(-1px); }

  .btn-outline {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: transparent;
    color: var(--text);
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 400;
    padding: 11px 22px;
    border-radius: 6px;
    border: 1px solid var(--border2);
    text-decoration: none;
    transition: border-color 0.2s, background 0.2s, transform 0.15s;
  }
  .btn-outline:hover { border-color: var(--accent); background: rgba(79,142,247,0.06); transform: translateY(-1px); }

  /* STAT ROW */
  .stat-row {
    display: flex;
    gap: 0;
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    margin-bottom: 60px;
    background: var(--surface);
  }

  .stat-item {
    flex: 1;
    padding: 20px 24px;
    border-right: 1px solid var(--border);
  }
  .stat-item:last-child { border-right: none; }

  .stat-num {
    font-size: 28px;
    font-weight: 800;
    color: var(--text);
    letter-spacing: -0.03em;
  }

  .stat-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    margin-top: 2px;
    letter-spacing: 0.05em;
  }

  /* SECTION */
  .section {
    padding: 48px 0;
    border-top: 1px solid var(--border);
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 28px;
  }

  .section-tag {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    background: rgba(79,142,247,0.1);
    padding: 4px 10px;
    border-radius: 4px;
    border: 1px solid rgba(79,142,247,0.2);
  }

  .section-title {
    font-size: 22px;
    font-weight: 700;
    color: var(--text);
    letter-spacing: -0.02em;
  }

  /* ABOUT CARDS */
  .about-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
  }

  @media (max-width: 600px) {
    .about-grid { grid-template-columns: 1fr; }
    .stat-row { flex-direction: column; }
    .stat-item { border-right: none; border-bottom: 1px solid var(--border); }
    .stat-item:last-child { border-bottom: none; }
    nav { flex-direction: column; gap: 16px; }
  }

  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px 20px;
    transition: border-color 0.2s, transform 0.2s;
    position: relative;
    overflow: hidden;
  }
  .about-card:hover { border-color: var(--border2); transform: translateY(-2px); }

  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
  }
  .about-card.blue::before { background: var(--accent); }
  .about-card.purple::before { background: var(--accent2); }
  .about-card.green::before { background: var(--accent3); }
  .about-card.amber::before { background: var(--accent4); }

  .about-card .card-label {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.1em;
    margin-bottom: 6px;
    text-transform: uppercase;
  }

  .about-card .card-value {
    font-size: 14px;
    font-weight: 600;
    color: var(--text);
  }

  /* SKILLS */
  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    font-family: var(--mono);
    font-size: 12px;
    padding: 6px 14px;
    border-radius: 6px;
    border: 1px solid var(--border2);
    color: var(--muted2);
    background: var(--surface);
    transition: all 0.2s;
    cursor: default;
  }
  .skill-tag:hover { color: var(--text); border-color: var(--accent); background: rgba(79,142,247,0.06); }

  .skill-tag.featured {
    color: var(--accent);
    border-color: rgba(79,142,247,0.3);
    background: rgba(79,142,247,0.08);
  }

  /* STACK TABLE */
  .stack-list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
  }

  @media (max-width: 600px) { .stack-list { grid-template-columns: repeat(2, 1fr); } }

  .stack-item {
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px 14px;
    transition: border-color 0.2s;
  }
  .stack-item:hover { border-color: var(--border2); }

  .stack-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .stack-name {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted2);
  }

  /* SOCIAL */
  .social-row {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }

  .social-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted2);
    text-decoration: none;
    padding: 9px 16px;
    border: 1px solid var(--border);
    border-radius: 6px;
    background: var(--surface);
    transition: all 0.2s;
  }
  .social-link:hover { color: var(--text); border-color: var(--border2); background: var(--surface2); }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 28px 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: gap;
    position: relative;
    z-index: 1;
  }

  .footer-copy {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
  }

  .footer-email {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--accent);
    text-decoration: none;
  }

  /* GitHub stats embed */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-top: 4px;
  }

  @media (max-width: 600px) { .stats-row { grid-template-columns: 1fr; } }

  .stats-row img {
    width: 100%;
    border-radius: 8px;
    border: 1px solid var(--border);
  }

  /* Fun fact */
  .fun-fact-bar {
    display: flex;
    align-items: center;
    gap: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent3);
    border-radius: 8px;
    padding: 14px 20px;
    margin-bottom: 60px;
  }

  .fun-fact-bar span {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--muted2);
  }

  .fun-fact-bar strong {
    color: var(--accent3);
    font-weight: 500;
  }

  /* Animations */
  .fade-up {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.6s ease forwards;
  }
  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }
  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.3s; }
  .delay-4 { animation-delay: 0.4s; }
  .delay-5 { animation-delay: 0.5s; }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="container">

  <!-- NAV -->
  <nav>
    <span class="nav-logo">~/raheemullah</span>
    <ul class="nav-links">
      <li><a href="#about">about</a></li>
      <li><a href="#skills">skills</a></li>
      <li><a href="#stats">stats</a></li>
      <li><a href="mailto:raheem3434a@gmail.com">contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section class="hero" id="about">
    <div class="hero-eyebrow fade-up">
      <span class="dot-live"></span>
      Available for collaboration · Pakistan
    </div>

    <h1 class="fade-up delay-1">
      <span class="name-accent">Raheem</span><br/>Ullah
    </h1>

    <p class="hero-subtitle fade-up delay-2">
      Full Stack Developer — <span>MERN Stack</span> & Next.js<br/>
      TypeScript Enthusiast · Scalable Web Apps
    </p>

    <div class="hero-actions fade-up delay-3">
      <a href="mailto:raheem3434a@gmail.com" class="btn-primary">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M2 7l10 7 10-7"/></svg>
        Get in touch
      </a>
      <a href="https://github.com/Raheemullah8" target="_blank" class="btn-outline">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
        GitHub Profile
      </a>
      <a href="https://pk.linkedin.com/in/raheemullah8" target="_blank" class="btn-outline">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
    </div>

    <!-- STAT ROW -->
    <div class="stat-row fade-up delay-4">
      <div class="stat-item">
        <div class="stat-num">3+</div>
        <div class="stat-label">YEARS EXP</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">12+</div>
        <div class="stat-label">TECH STACK</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">∞</div>
        <div class="stat-label">SCALABILITY</div>
      </div>
    </div>

    <!-- FUN FACT -->
    <div class="fun-fact-bar fade-up delay-5">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#34d399" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M12 16v-4M12 8h.01"/></svg>
      <span>⚡ Fun fact — <strong>I love building scalable web applications!</strong></span>
    </div>

  </section>

  <!-- ABOUT CARDS -->
  <section class="section" id="skills">
    <div class="section-header">
      <span class="section-tag">01 // ABOUT</span>
      <h2 class="section-title">What I'm up to</h2>
    </div>
    <div class="about-grid">
      <div class="about-card blue">
        <div class="card-label">Currently working on</div>
        <div class="card-value">Full Stack Web Applications</div>
      </div>
      <div class="about-card purple">
        <div class="card-label">Currently learning</div>
        <div class="card-value">Advanced Next.js & TypeScript</div>
      </div>
      <div class="about-card green">
        <div class="card-label">Ask me about</div>
        <div class="card-value">React, Node.js, MongoDB, PostgreSQL</div>
      </div>
      <div class="about-card amber">
        <div class="card-label">Open to</div>
        <div class="card-value">Collaborations & New Projects</div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section class="section">
    <div class="section-header">
      <span class="section-tag">02 // SKILLS</span>
      <h2 class="section-title">Languages & tools</h2>
    </div>
    <div class="skills-grid" style="margin-bottom: 24px;">
      <span class="skill-tag featured">JavaScript</span>
      <span class="skill-tag featured">TypeScript</span>
      <span class="skill-tag featured">React</span>
      <span class="skill-tag featured">Next.js</span>
      <span class="skill-tag featured">Node.js</span>
      <span class="skill-tag">Express.js</span>
      <span class="skill-tag">React Native</span>
      <span class="skill-tag">HTML5</span>
      <span class="skill-tag">CSS3</span>
      <span class="skill-tag">Tailwind CSS</span>
      <span class="skill-tag">Bootstrap</span>
    </div>

    <div class="stack-list">
      <div class="stack-item">
        <span class="stack-dot" style="background:#4f8ef7"></span>
        <span class="stack-name">MongoDB</span>
      </div>
      <div class="stack-item">
        <span class="stack-dot" style="background:#a78bfa"></span>
        <span class="stack-name">PostgreSQL</span>
      </div>
      <div class="stack-item">
        <span class="stack-dot" style="background:#fbbf24"></span>
        <span class="stack-name">MySQL</span>
      </div>
      <div class="stack-item">
        <span class="stack-dot" style="background:#34d399"></span>
        <span class="stack-name">REST APIs</span>
      </div>
      <div class="stack-item">
        <span class="stack-dot" style="background:#f87171"></span>
        <span class="stack-name">Git & GitHub</span>
      </div>
      <div class="stack-item">
        <span class="stack-dot" style="background:#fb923c"></span>
        <span class="stack-name">Vercel / Deploy</span>
      </div>
    </div>
  </section>

  <!-- GITHUB STATS -->
  <section class="section" id="stats">
    <div class="section-header">
      <span class="section-tag">03 // STATS</span>
      <h2 class="section-title">GitHub activity</h2>
    </div>

    <div class="stats-row">
      <img src="https://github-readme-stats.vercel.app/api?username=raheemullah8&show_icons=true&theme=github_dark&hide_border=true&bg_color=111118&title_color=4f8ef7&icon_color=a78bfa&text_color=9ca3af" alt="GitHub Stats" />
      <img src="https://github-readme-stats.vercel.app/api/top-langs?username=raheemullah8&layout=compact&theme=github_dark&hide_border=true&bg_color=111118&title_color=4f8ef7&text_color=9ca3af" alt="Top Languages" />
    </div>

    <div style="margin-top: 12px;">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=raheemullah8&theme=github-dark-blue&hide_border=true&background=111118&ring=4f8ef7&fire=fbbf24&currStreakLabel=4f8ef7" width="100%" style="border-radius:8px; border: 1px solid rgba(255,255,255,0.07);" alt="Streak Stats"/>
    </div>
  </section>

  <!-- CONNECT -->
  <section class="section">
    <div class="section-header">
      <span class="section-tag">04 // CONNECT</span>
      <h2 class="section-title">Let's work together</h2>
    </div>
    <div class="social-row">
      <a href="https://pk.linkedin.com/in/raheemullah8" target="_blank" class="social-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        linkedin/raheemullah8
      </a>
      <a href="https://github.com/Raheemullah8" target="_blank" class="social-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/></svg>
        github/Raheemullah8
      </a>
      <a href="mailto:raheem3434a@gmail.com" class="social-link">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="M2 7l10 7 10-7"/></svg>
        raheem3434a@gmail.com
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <span class="footer-copy">© 2024 RaheemUllah · Karachi, Pakistan</span>
    <a href="mailto:raheem3434a@gmail.com" class="footer-email">raheem3434a@gmail.com</a>
  </footer>

</div>

</body>
</html>
