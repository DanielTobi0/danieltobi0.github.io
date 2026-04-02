<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Daniel Tobi — Applied AI Engineer</title>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,500;0,9..40,700;1,9..40,300&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0a0a0a;
      --surface: #111111;
      --border: #222222;
      --accent: #00ff87;
      --accent2: #00c2ff;
      --text: #e8e8e8;
      --muted: #666666;
      --mono: 'Space Mono', monospace;
      --sans: 'DM Sans', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--sans);
      font-weight: 300;
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* === GRID BACKGROUND === */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(0,255,135,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,255,135,0.03) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }

    /* === NAV === */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 3rem;
      background: rgba(10,10,10,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: var(--mono);
      font-size: 0.9rem;
      color: var(--accent);
      letter-spacing: 0.05em;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      font-family: var(--mono);
      font-size: 0.75rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--accent); }

    /* === HERO === */
    .hero {
      position: relative;
      z-index: 1;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 8rem 3rem 4rem;
      max-width: 1100px;
      margin: 0 auto;
    }

    .hero-tag {
      font-family: var(--mono);
      font-size: 0.75rem;
      color: var(--accent);
      letter-spacing: 0.2em;
      text-transform: uppercase;
      margin-bottom: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.6s ease forwards 0.2s;
    }

    .hero h1 {
      font-family: var(--mono);
      font-size: clamp(2.8rem, 7vw, 5.5rem);
      font-weight: 700;
      line-height: 1.05;
      letter-spacing: -0.02em;
      margin-bottom: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.6s ease forwards 0.35s;
    }

    .hero h1 span {
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-desc {
      font-size: 1.15rem;
      color: var(--muted);
      max-width: 560px;
      margin-bottom: 2.5rem;
      opacity: 0;
      animation: fadeUp 0.6s ease forwards 0.5s;
    }

    .hero-links {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      opacity: 0;
      animation: fadeUp 0.6s ease forwards 0.65s;
    }

    .btn {
      font-family: var(--mono);
      font-size: 0.78rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      text-decoration: none;
      padding: 0.75rem 1.5rem;
      border-radius: 2px;
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
    }

    .btn-primary {
      background: var(--accent);
      color: #000;
      font-weight: 700;
    }
    .btn-primary:hover { background: #00e87a; transform: translateY(-2px); }

    .btn-outline {
      border: 1px solid var(--border);
      color: var(--muted);
    }
    .btn-outline:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

    .hero-status {
      margin-top: 4rem;
      display: flex;
      align-items: center;
      gap: 0.75rem;
      font-family: var(--mono);
      font-size: 0.72rem;
      color: var(--muted);
      opacity: 0;
      animation: fadeUp 0.6s ease forwards 0.8s;
    }

    .status-dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 0 3px rgba(0,255,135,0.15);
      animation: pulse 2s ease infinite;
    }

    @keyframes pulse {
      0%, 100% { box-shadow: 0 0 0 3px rgba(0,255,135,0.15); }
      50% { box-shadow: 0 0 0 6px rgba(0,255,135,0.05); }
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* === SECTIONS === */
    section {
      position: relative;
      z-index: 1;
      max-width: 1100px;
      margin: 0 auto;
      padding: 5rem 3rem;
      border-top: 1px solid var(--border);
    }

    .section-label {
      font-family: var(--mono);
      font-size: 0.7rem;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 3rem;
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .section-label::after {
      content: '';
      flex: 1;
      max-width: 80px;
      height: 1px;
      background: var(--accent);
      opacity: 0.4;
    }

    /* === EXPERIENCE === */
    .exp-list { display: flex; flex-direction: column; gap: 3rem; }

    .exp-item {
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 2rem;
    }

    .exp-meta {
      padding-top: 0.25rem;
    }

    .exp-date {
      font-family: var(--mono);
      font-size: 0.72rem;
      color: var(--muted);
      letter-spacing: 0.05em;
      margin-bottom: 0.5rem;
    }

    .exp-company {
      font-family: var(--mono);
      font-size: 0.8rem;
      color: var(--accent);
      margin-bottom: 0.25rem;
    }

    .exp-location {
      font-size: 0.78rem;
      color: var(--muted);
    }

    .exp-content h3 {
      font-family: var(--mono);
      font-size: 1rem;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 1rem;
    }

    .exp-content ul {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }

    .exp-content li {
      font-size: 0.92rem;
      color: #aaa;
      padding-left: 1.2rem;
      position: relative;
    }

    .exp-content li::before {
      content: '→';
      position: absolute;
      left: 0;
      color: var(--accent);
      font-size: 0.75rem;
    }

    /* === PROJECTS === */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 1.5rem;
    }

    .project-card {
      background: var(--surface);
      border: 1px solid var(--border);
      padding: 2rem;
      border-radius: 2px;
      transition: border-color 0.2s, transform 0.2s;
      position: relative;
      overflow: hidden;
    }

    .project-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 1px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s ease;
    }

    .project-card:hover {
      border-color: #333;
      transform: translateY(-3px);
    }

    .project-card:hover::before { transform: scaleX(1); }

    .project-title {
      font-family: var(--mono);
      font-size: 0.9rem;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 0.75rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .project-title a {
      color: inherit;
      text-decoration: none;
    }
    .project-title a:hover { color: var(--accent); }

    .project-tag {
      font-family: var(--mono);
      font-size: 0.62rem;
      color: var(--accent2);
      border: 1px solid rgba(0,194,255,0.25);
      padding: 0.15rem 0.5rem;
      border-radius: 2px;
      letter-spacing: 0.05em;
    }

    .project-desc {
      font-size: 0.85rem;
      color: #888;
      line-height: 1.6;
    }

    .project-desc li {
      margin-bottom: 0.4rem;
      padding-left: 1rem;
      position: relative;
      list-style: none;
    }

    .project-desc li::before {
      content: '·';
      position: absolute;
      left: 0;
      color: var(--accent);
    }

    /* === SKILLS === */
    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
    }

    .skill-chip {
      font-family: var(--mono);
      font-size: 0.75rem;
      letter-spacing: 0.05em;
      padding: 0.5rem 1rem;
      border: 1px solid var(--border);
      color: var(--muted);
      border-radius: 2px;
      transition: all 0.2s;
    }

    .skill-chip:hover {
      border-color: var(--accent);
      color: var(--accent);
      background: rgba(0,255,135,0.04);
    }

    /* === EDUCATION === */
    .edu-list { display: flex; flex-direction: column; gap: 2rem; }

    .edu-item {
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 2rem;
      align-items: start;
    }

    .edu-date {
      font-family: var(--mono);
      font-size: 0.72rem;
      color: var(--muted);
    }

    .edu-content h3 {
      font-family: var(--mono);
      font-size: 0.9rem;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 0.25rem;
    }

    .edu-content p {
      font-size: 0.85rem;
      color: var(--muted);
    }

    /* === FOOTER === */
    footer {
      position: relative;
      z-index: 1;
      border-top: 1px solid var(--border);
      padding: 3rem;
      max-width: 1100px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
    }

    .footer-name {
      font-family: var(--mono);
      font-size: 0.8rem;
      color: var(--muted);
    }

    .footer-links {
      display: flex;
      gap: 1.5rem;
    }

    .footer-links a {
      font-family: var(--mono);
      font-size: 0.72rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.05em;
      transition: color 0.2s;
    }

    .footer-links a:hover { color: var(--accent); }

    /* === RESPONSIVE === */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { display: none; }
      .hero, section, footer { padding-left: 1.5rem; padding-right: 1.5rem; }
      .exp-item, .edu-item { grid-template-columns: 1fr; gap: 0.75rem; }
      .projects-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-logo">daniel_tobi.ai</div>
    <ul class="nav-links">
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#education">Education</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <div class="hero">
    <p class="hero-tag">// Applied AI Engineer</p>
    <h1>Daniel<br /><span>Tobi</span></h1>
    <p class="hero-desc">
      Building intelligent systems at the intersection of AI agents, multi-agent frameworks, and real-world data pipelines. Based in Nigeria, working globally.
    </p>
    <div class="hero-links">
      <a href="https://github.com/DanielTobi0" target="_blank" class="btn btn-primary">GitHub ↗</a>
      <a href="https://www.linkedin.com/in/danieltobi0/" target="_blank" class="btn btn-outline">LinkedIn ↗</a>
      <a href="https://docs.google.com/document/d/1HKnEXoXScLfjmfl_06VDN6fW8llI-08O8rKFEF-4_pM/edit?usp=drive_link" target="_blank" class="btn btn-outline">Resume ↗</a>
      <a href="mailto:danieltobi0@gmail.com" class="btn btn-outline">Contact ↗</a>
    </div>
    <div class="hero-status">
      <div class="status-dot"></div>
      Available for opportunities · Nigeria · +234 810 654 2743
    </div>
  </div>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="section-label">Experience</div>
    <div class="exp-list">

      <div class="exp-item">
        <div class="exp-meta">
          <div class="exp-date">Jul 2025 – Present</div>
          <div class="exp-company">UEFO PRO</div>
          <div class="exp-location">Remote · UAE</div>
        </div>
        <div class="exp-content">
          <h3>AI Engineer</h3>
          <ul>
            <li>Co-architected a multi-agent trading system for a hedge fund founded by a former BlackRock director.</li>
            <li>Built a modular portfolio optimization engine covering instrument analysis, position sizing, and performance attribution to generate trading recommendations.</li>
            <li>Automated the initial instrument research process resulting in a 40% reduction in manual research time for market understanding.</li>
            <li>Implemented SSE streaming for the real-time chat agent, enabling low-latency interactive querying over the portfolio.</li>
          </ul>
        </div>
      </div>

      <div class="exp-item">
        <div class="exp-meta">
          <div class="exp-date">Dec 2024 – Jun 2025</div>
          <div class="exp-company">Peepalytics AI</div>
          <div class="exp-location">Remote · US</div>
        </div>
        <div class="exp-content">
          <h3>Machine Learning Engineer</h3>
          <ul>
            <li>Led development of an autonomous ETL pipeline (LangGraph) that transforms raw structured and semi-structured data into insights via task-specific code generation.</li>
            <li>Built Text-to-Cypher queries that enable natural language querying over knowledge graph databases.</li>
            <li>Implemented behaviour assessment using Hume AI to understand user emotions, enabling more empathetic and context-aware user experiences.</li>
          </ul>
        </div>
      </div>

    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="section-label">Projects</div>
    <div class="projects-grid">

      <div class="project-card">
        <div class="project-title">
          <a href="#" target="_blank">Chat with Structured Data</a>
          <span class="project-tag">Live</span>
        </div>
        <ul class="project-desc">
          <li>Built an agentic workflow from scratch to answer natural language questions over structured and tabular datasets.</li>
          <li>Implemented retrieval and reasoning components to improve answer relevance and usability for data exploration.</li>
        </ul>
      </div>

      <div class="project-card">
        <div class="project-title">
          <a href="https://github.com/DanielTobi0" target="_blank">Multi-Agent Financial Analysis</a>
          <span class="project-tag">arXiv</span>
        </div>
        <ul class="project-desc">
          <li>Reproduced the arXiv:2508.11152 framework end-to-end in Python with a modular multi-agent workflow for fundamental, sentiment, and valuation analysis.</li>
          <li>Integrated RAG tooling, embeddings, and structured outputs to produce risk-aware investment reports.</li>
          <li>Automated generation of recommendation JSON outputs, debate logs, and consolidated markdown reports.</li>
          <li>Framework: AutoGen (matching the original paper's implementation).</li>
        </ul>
      </div>

    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-label">Skills</div>
    <div class="skills-grid">
      <div class="skill-chip">Python</div>
      <div class="skill-chip">LangGraph</div>
      <div class="skill-chip">FastAPI</div>
      <div class="skill-chip">PyTorch</div>
      <div class="skill-chip">AutoGen</div>
      <div class="skill-chip">RAG</div>
      <div class="skill-chip">Multi-Agent Systems</div>
      <div class="skill-chip">Google Cloud SDK</div>
      <div class="skill-chip">Google Cloud Run</div>
      <div class="skill-chip">MongoDB</div>
      <div class="skill-chip">SQL</div>
      <div class="skill-chip">Git</div>
      <div class="skill-chip">SSE Streaming</div>
      <div class="skill-chip">Knowledge Graphs</div>
      <div class="skill-chip">ETL Pipelines</div>
    </div>
  </section>

  <!-- EDUCATION -->
  <section id="education">
    <div class="section-label">Education</div>
    <div class="edu-list">
      <div class="edu-item">
        <div class="edu-date">Jun 2025 – Apr 2027</div>
        <div class="edu-content">
          <h3>Miva Open University</h3>
          <p>B.Sc. Computer Science · Remote</p>
        </div>
      </div>
      <div class="edu-item">
        <div class="edu-date">Jan 2019 – Mar 2024</div>
        <div class="edu-content">
          <h3>Ibadan City Polytechnic</h3>
          <p>Computer Science</p>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-name">© 2026 Daniel Tobi</div>
    <div class="footer-links">
      <a href="https://github.com/DanielTobi0" target="_blank">GitHub</a>
      <a href="https://www.linkedin.com/in/danieltobi0/" target="_blank">LinkedIn</a>
      <a href="https://docs.google.com/document/d/1HKnEXoXScLfjmfl_06VDN6fW8llI-08O8rKFEF-4_pM/edit?usp=drive_link" target="_blank">Resume</a>
    </div>
  </footer>

</body>
</html>
