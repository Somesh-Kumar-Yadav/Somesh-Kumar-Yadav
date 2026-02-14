<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Somesh Kumar Yadav — Full Stack Developer</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,400;0,500;1,400&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #080c10;
      --surface: #0d1117;
      --surface2: #161b22;
      --border: #21262d;
      --accent: #39d353;
      --accent2: #58a6ff;
      --accent3: #f78166;
      --text: #e6edf3;
      --muted: #7d8590;
      --glow: rgba(57, 211, 83, 0.18);
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* GRID BACKGROUND */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(57,211,83,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(57,211,83,0.03) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }

    /* GLOW ORB */
    .glow-orb {
      position: fixed;
      width: 600px;
      height: 600px;
      background: radial-gradient(circle, rgba(57,211,83,0.07) 0%, transparent 70%);
      border-radius: 50%;
      top: -150px;
      right: -150px;
      pointer-events: none;
      z-index: 0;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 0 24px;
      position: relative;
      z-index: 1;
    }

    /* ─── HEADER ─── */
    header {
      padding: 64px 0 48px;
      animation: fadeUp 0.8s ease both;
    }

    .status-pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(57,211,83,0.1);
      border: 1px solid rgba(57,211,83,0.3);
      border-radius: 100px;
      padding: 6px 16px;
      font-family: 'DM Mono', monospace;
      font-size: 12px;
      color: var(--accent);
      margin-bottom: 28px;
    }

    .status-dot {
      width: 7px;
      height: 7px;
      background: var(--accent);
      border-radius: 50%;
      box-shadow: 0 0 8px var(--accent);
      animation: pulse 2s ease-in-out infinite;
    }

    .greeting {
      font-family: 'DM Mono', monospace;
      font-size: 14px;
      color: var(--muted);
      margin-bottom: 10px;
      letter-spacing: 0.08em;
    }

    .name {
      font-family: 'Syne', sans-serif;
      font-size: clamp(38px, 6vw, 64px);
      font-weight: 800;
      line-height: 1.05;
      letter-spacing: -0.03em;
      margin-bottom: 16px;
    }

    .name span {
      background: linear-gradient(135deg, var(--accent) 0%, var(--accent2) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .title-line {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 20px;
    }

    .title-badge {
      font-family: 'DM Mono', monospace;
      font-size: 13px;
      padding: 4px 12px;
      border-radius: 4px;
      border: 1px solid var(--border);
      color: var(--accent2);
      background: rgba(88, 166, 255, 0.06);
    }

    .bio {
      max-width: 620px;
      font-size: 16px;
      line-height: 1.7;
      color: #adbac7;
      margin-bottom: 32px;
    }

    .contact-row {
      display: flex;
      flex-wrap: wrap;
      gap: 16px;
      align-items: center;
    }

    .contact-link {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-family: 'DM Mono', monospace;
      font-size: 12px;
      color: var(--muted);
      text-decoration: none;
      padding: 8px 14px;
      border: 1px solid var(--border);
      border-radius: 6px;
      background: var(--surface2);
      transition: all 0.2s ease;
    }

    .contact-link:hover {
      color: var(--text);
      border-color: var(--accent);
      box-shadow: 0 0 12px rgba(57,211,83,0.15);
      transform: translateY(-1px);
    }

    .contact-link svg { flex-shrink: 0; }

    /* ─── SECTION ─── */
    section {
      margin-bottom: 56px;
      animation: fadeUp 0.8s ease both;
    }

    section:nth-child(2) { animation-delay: 0.1s; }
    section:nth-child(3) { animation-delay: 0.2s; }
    section:nth-child(4) { animation-delay: 0.3s; }

    .section-label {
      display: flex;
      align-items: center;
      gap: 12px;
      font-family: 'DM Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.12em;
      color: var(--muted);
      text-transform: uppercase;
      margin-bottom: 24px;
    }

    .section-label::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    /* ─── SKILLS GRID ─── */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 12px;
    }

    .skill-category {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 18px;
      transition: border-color 0.2s, box-shadow 0.2s;
    }

    .skill-category:hover {
      border-color: rgba(57,211,83,0.3);
      box-shadow: 0 0 16px rgba(57,211,83,0.06);
    }

    .cat-title {
      font-family: 'DM Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.1em;
      color: var(--accent);
      text-transform: uppercase;
      margin-bottom: 12px;
    }

    .skill-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .tag {
      font-size: 12px;
      padding: 3px 10px;
      border-radius: 4px;
      border: 1px solid var(--border);
      color: var(--muted);
      background: var(--surface2);
      font-family: 'DM Mono', monospace;
      transition: all 0.15s;
      cursor: default;
    }

    .tag:hover {
      color: var(--text);
      border-color: var(--accent2);
    }

    /* ─── STATS GRID ─── */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
      margin-bottom: 20px;
    }

    @media (max-width: 600px) {
      .stats-grid { grid-template-columns: 1fr; }
      .skills-grid { grid-template-columns: 1fr 1fr; }
    }

    .stat-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 20px;
      text-align: center;
      transition: all 0.2s;
    }

    .stat-card:hover {
      border-color: rgba(57,211,83,0.3);
      transform: translateY(-2px);
    }

    .stat-number {
      font-family: 'Syne', sans-serif;
      font-size: 36px;
      font-weight: 800;
      color: var(--accent);
      line-height: 1;
      margin-bottom: 6px;
    }

    .stat-label {
      font-family: 'DM Mono', monospace;
      font-size: 11px;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    /* ─── GITHUB CHARTS ─── */
    .charts-wrapper {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .chart-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      overflow: hidden;
    }

    .chart-card img {
      display: block;
      width: 100%;
      height: auto;
    }

    /* ─── FOOTER ─── */
    footer {
      border-top: 1px solid var(--border);
      padding: 32px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      animation: fadeUp 0.8s 0.4s ease both;
    }

    .footer-note {
      font-family: 'DM Mono', monospace;
      font-size: 12px;
      color: var(--muted);
    }

    .view-counter {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* BADGE STRIP */
    .badge-strip {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .badge-strip img {
      height: 22px;
      border-radius: 4px;
    }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50%       { opacity: 0.4; }
    }

    /* DIVIDER */
    .divider {
      height: 1px;
      background: var(--border);
      margin: 48px 0;
    }
  </style>
</head>
<body>
  <div class="glow-orb"></div>

  <div class="container">

    <!-- ─── HEADER ─── -->
    <header>
      <div class="status-pill">
        <span class="status-dot"></span>
        Open to opportunities
      </div>

      <p class="greeting">// hello, world</p>

      <h1 class="name">
        Somesh Kumar<br/><span>Yadav</span>
      </h1>

      <div class="title-line">
        <span class="title-badge">Full Stack Developer</span>
        <span class="title-badge">DSA Enthusiast</span>
      </div>

      <p class="bio">
        Designing, developing, and maintaining scalable projects end-to-end.
        Adept at learning, unlearning, and relearning. I write clean, elegant,
        efficient code and thrive in collaborative environments.
      </p>

      <div class="contact-row">
        <a class="contact-link" href="https://www.linkedin.com/in/somesh-kumar-yadav-3a2141157/" target="_blank">
          <svg width="14" height="14" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a class="contact-link" href="mailto:someshkumar71524@gmail.com">
          <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
          someshkumar71524@gmail.com
        </a>
        <a class="contact-link" href="tel:+916354136407">
          <svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.37 2 2 0 0 1 3.59 1h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 8.56a16 16 0 0 0 5.47 5.47l1.42-1.42a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
          +91-6354136407
        </a>
        <a class="contact-link" href="https://github.com/Somesh-Kumar-Yadav" target="_blank">
          <svg width="14" height="14" fill="currentColor" viewBox="0 0 24 24"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          GitHub
        </a>
      </div>
    </header>

    <div class="divider"></div>

    <!-- ─── STATS ─── -->
    <section>
      <p class="section-label">// quick stats</p>
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-number">5+</div>
          <div class="stat-label">Years Coding</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">30+</div>
          <div class="stat-label">Technologies</div>
        </div>
        <div class="stat-card">
          <div class="stat-number">∞</div>
          <div class="stat-label">Curiosity</div>
        </div>
      </div>
    </section>

    <!-- ─── SKILLS ─── -->
    <section>
      <p class="section-label">// languages & tools</p>
      <div class="skills-grid">

        <div class="skill-category">
          <div class="cat-title">Frontend</div>
          <div class="skill-tags">
            <span class="tag">React</span>
            <span class="tag">React Native</span>
            <span class="tag">TypeScript</span>
            <span class="tag">Redux</span>
            <span class="tag">HTML5</span>
            <span class="tag">CSS3</span>
            <span class="tag">Tailwind</span>
            <span class="tag">Bootstrap</span>
          </div>
        </div>

        <div class="skill-category">
          <div class="cat-title">Backend</div>
          <div class="skill-tags">
            <span class="tag">Node.js</span>
            <span class="tag">Express</span>
            <span class="tag">Spring</span>
            <span class="tag">Python</span>
            <span class="tag">Java</span>
            <span class="tag">Go</span>
          </div>
        </div>

        <div class="skill-category">
          <div class="cat-title">Databases</div>
          <div class="skill-tags">
            <span class="tag">PostgreSQL</span>
            <span class="tag">MongoDB</span>
            <span class="tag">MySQL</span>
            <span class="tag">Redis</span>
          </div>
        </div>

        <div class="skill-category">
          <div class="cat-title">DevOps & Cloud</div>
          <div class="skill-tags">
            <span class="tag">AWS</span>
            <span class="tag">Docker</span>
            <span class="tag">Kubernetes</span>
            <span class="tag">Heroku</span>
            <span class="tag">Linux</span>
          </div>
        </div>

        <div class="skill-category">
          <div class="cat-title">Tooling</div>
          <div class="skill-tags">
            <span class="tag">Git</span>
            <span class="tag">Webpack</span>
            <span class="tag">Babel</span>
            <span class="tag">Postman</span>
            <span class="tag">Kafka</span>
          </div>
        </div>

      </div>
    </section>

    <!-- ─── GITHUB STATS ─── -->
    <section>
      <p class="section-label">// github stats</p>
      <div class="charts-wrapper">
        <div class="chart-card">
          <img
            src="https://github-readme-stats.vercel.app/api?username=Somesh-Kumar-Yadav&show_icons=true&locale=en&theme=react&hide_border=true&bg_color=0d1117&title_color=39d353&icon_color=58a6ff&text_color=adbac7"
            alt="Somesh's GitHub Stats"
            loading="lazy"
          />
        </div>
        <div class="chart-card">
          <img
            src="https://github-readme-streak-stats.herokuapp.com/?user=Somesh-Kumar-Yadav&hide_border=true&theme=react&background=0d1117&ring=39d353&fire=f78166&currStreakLabel=39d353&sideLabels=adbac7&dates=7d8590"
            alt="Somesh's Streak Stats"
            loading="lazy"
          />
        </div>
        <div class="chart-card">
          <img
            src="https://github-readme-stats.vercel.app/api/top-langs/?username=Somesh-Kumar-Yadav&langs_count=8&count_private=true&layout=compact&theme=react&hide_border=true&bg_color=0d1117&title_color=39d353&text_color=adbac7"
            alt="Top Languages"
            loading="lazy"
          />
        </div>
      </div>
      <p style="font-family:'DM Mono',monospace;font-size:11px;color:var(--muted);margin-top:14px;">
        * Top languages reflects public code only and does not indicate overall skill level.
      </p>
    </section>

    <!-- ─── FOOTER ─── -->
    <footer>
      <div class="view-counter">
        <img src="https://komarev.com/ghpvc/?username=Somesh-Kumar-Yadav&color=39d353&style=flat-square&label=profile+views" alt="Profile Views" style="height:20px;border-radius:4px;"/>
        <img src="https://img.shields.io/github/followers/Somesh-Kumar-Yadav?label=Followers&style=flat-square&color=58a6ff&labelColor=21262d" alt="Followers" style="height:20px;border-radius:4px;"/>
      </div>
      <p class="footer-note">// Built with ☕ by Somesh Kumar Yadav</p>
    </footer>

  </div>
</body>
</html>
