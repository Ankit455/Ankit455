<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Ankit Dhandharia — Portfolio</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0d0d0d;
    --surface: #161616;
    --card: #1c1c1c;
    --border: rgba(255,255,255,0.08);
    --border-hover: rgba(255,255,255,0.18);
    --text: #f0f0f0;
    --muted: #888;
    --accent: #378ADD;
    --accent2: #1D9E75;
    --accent3: #BA7517;
    --accent4: #7F77DD;
    --font: 'Segoe UI', system-ui, -apple-system, sans-serif;
    --mono: 'Fira Code', 'Cascadia Code', 'Consolas', monospace;
  }

  body { background: var(--bg); color: var(--text); font-family: var(--font); min-height: 100vh; overflow-x: hidden; }

  /* NAV */
  nav { position: sticky; top: 0; z-index: 100; background: rgba(13,13,13,0.92); backdrop-filter: blur(8px); border-bottom: 1px solid var(--border); padding: 0 2rem; display: flex; align-items: center; justify-content: space-between; height: 52px; }
  nav .logo { font-family: var(--mono); font-size: 13px; color: var(--accent); letter-spacing: 0.02em; }
  nav .links { display: flex; gap: 1.5rem; }
  nav .links a { color: var(--muted); text-decoration: none; font-size: 13px; transition: color 0.2s; }
  nav .links a:hover { color: var(--text); }

  /* HERO */
  .hero { padding: 80px 2rem 60px; max-width: 860px; margin: 0 auto; }
  .hero-tag { display: inline-block; font-family: var(--mono); font-size: 12px; color: var(--accent); background: rgba(55,138,221,0.1); border: 1px solid rgba(55,138,221,0.25); padding: 4px 12px; border-radius: 20px; margin-bottom: 24px; }
  .hero h1 { font-size: clamp(32px, 6vw, 54px); font-weight: 600; line-height: 1.1; letter-spacing: -0.02em; margin-bottom: 18px; }
  .hero h1 span { color: var(--accent); }
  .hero-roles { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 28px; }
  .role-pill { font-size: 12px; padding: 5px 13px; border-radius: 20px; border: 1px solid var(--border-hover); color: var(--muted); font-family: var(--mono); transition: all 0.2s; cursor: default; }
  .role-pill:hover { color: var(--text); border-color: var(--accent); }
  .role-pill.de { border-color: rgba(55,138,221,0.4); color: #85B7EB; }
  .role-pill.ai { border-color: rgba(127,119,221,0.4); color: #AFA9EC; }
  .role-pill.se { border-color: rgba(29,158,117,0.4); color: #5DCAA5; }
  .role-pill.ds { border-color: rgba(186,117,23,0.4); color: #EF9F27; }
  .hero-sub { font-size: 16px; color: var(--muted); line-height: 1.7; max-width: 600px; margin-bottom: 32px; }
  .hero-sub strong { color: var(--text); font-weight: 500; }
  .cta-row { display: flex; flex-wrap: wrap; gap: 12px; }
  .btn { display: inline-flex; align-items: center; gap: 8px; padding: 10px 22px; border-radius: 8px; font-size: 14px; font-weight: 500; text-decoration: none; transition: all 0.18s; cursor: pointer; border: none; }
  .btn-primary { background: var(--accent); color: #fff; }
  .btn-primary:hover { background: #185FA5; }
  .btn-outline { background: transparent; color: var(--text); border: 1px solid var(--border-hover); }
  .btn-outline:hover { background: var(--card); border-color: var(--text); }

  /* TERMINAL */
  .terminal-wrap { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .terminal { background: var(--surface); border: 1px solid var(--border); border-radius: 12px; overflow: hidden; }
  .terminal-bar { background: #252525; padding: 10px 16px; display: flex; align-items: center; gap: 8px; }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot.r { background: #FF5F57; } .dot.y { background: #FEBC2E; } .dot.g { background: #28C840; }
  .terminal-title { font-size: 12px; color: var(--muted); margin-left: 8px; font-family: var(--mono); }
  .terminal-body { padding: 20px 24px; font-family: var(--mono); font-size: 13px; line-height: 1.9; }
  .line { opacity: 0; transform: translateY(4px); transition: opacity 0.3s, transform 0.3s; }
  .line.show { opacity: 1; transform: none; }
  .prompt { color: var(--accent2); }
  .cmd { color: var(--text); }
  .out { color: var(--muted); padding-left: 1.5rem; }
  .out.hi { color: var(--accent); }
  .out.warn { color: var(--accent3); }
  .out.ok { color: var(--accent2); }
  .cursor { display: inline-block; width: 8px; height: 14px; background: var(--accent); vertical-align: middle; animation: blink 1s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* STATS */
  .stats-section { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 1px; background: var(--border); border: 1px solid var(--border); border-radius: 12px; overflow: hidden; }
  .stat-cell { background: var(--surface); padding: 24px 20px; text-align: center; }
  .stat-num { font-size: 30px; font-weight: 600; font-family: var(--mono); transition: color 0.3s; }
  .stat-num.blue { color: var(--accent); }
  .stat-num.green { color: var(--accent2); }
  .stat-num.amber { color: var(--accent3); }
  .stat-num.purple { color: var(--accent4); }
  .stat-label { font-size: 11px; color: var(--muted); margin-top: 6px; line-height: 1.4; text-transform: uppercase; letter-spacing: 0.04em; }

  /* DOMAINS */
  .domains-section { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .section-label { font-size: 11px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 20px; }
  .domains-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(190px, 1fr)); gap: 12px; }
  .domain-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 20px; cursor: pointer; transition: border-color 0.2s, background 0.2s; }
  .domain-card:hover { border-color: var(--border-hover); background: #212121; }
  .domain-card.active { border-color: var(--dcolor); background: #1a1a1a; }
  .domain-icon { font-size: 22px; margin-bottom: 12px; }
  .domain-title { font-size: 14px; font-weight: 500; margin-bottom: 4px; }
  .domain-sub { font-size: 12px; color: var(--muted); }
  .domain-detail { max-width: 860px; margin: 0 auto; padding: 0 2rem; overflow: hidden; max-height: 0; transition: max-height 0.4s ease; }
  .domain-detail.open { max-height: 600px; }
  .detail-inner { background: var(--surface); border: 1px solid var(--border); border-radius: 12px; padding: 24px; margin-bottom: 12px; }
  .detail-inner h3 { font-size: 15px; font-weight: 500; margin-bottom: 16px; }
  .skill-bars { display: flex; flex-direction: column; gap: 12px; }
  .bar-row { display: flex; align-items: center; gap: 12px; }
  .bar-label { font-size: 12px; color: var(--muted); min-width: 120px; font-family: var(--mono); }
  .bar-track { flex: 1; height: 4px; background: rgba(255,255,255,0.06); border-radius: 2px; overflow: hidden; }
  .bar-fill { height: 100%; border-radius: 2px; width: 0; transition: width 0.8s cubic-bezier(0.4,0,0.2,1); }
  .bar-pct { font-size: 11px; color: var(--muted); min-width: 32px; text-align: right; font-family: var(--mono); }

  /* PROJECTS */
  .projects-section { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 12px; }
  .proj-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 20px; transition: border-color 0.2s; }
  .proj-card:hover { border-color: var(--border-hover); }
  .proj-tag { font-size: 10px; text-transform: uppercase; letter-spacing: 0.06em; padding: 3px 8px; border-radius: 4px; display: inline-block; margin-bottom: 12px; font-family: var(--mono); }
  .proj-tag.de { background: rgba(55,138,221,0.12); color: #85B7EB; }
  .proj-tag.ai { background: rgba(127,119,221,0.12); color: #AFA9EC; }
  .proj-title { font-size: 14px; font-weight: 500; margin-bottom: 8px; }
  .proj-desc { font-size: 12px; color: var(--muted); line-height: 1.6; margin-bottom: 14px; }
  .proj-stack { display: flex; flex-wrap: wrap; gap: 5px; }
  .stack-tag { font-size: 10px; font-family: var(--mono); padding: 2px 7px; border-radius: 3px; background: rgba(255,255,255,0.05); color: var(--muted); border: 1px solid var(--border); }

  /* TIMELINE */
  .timeline-section { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .timeline { position: relative; padding-left: 20px; }
  .timeline::before { content: ''; position: absolute; left: 0; top: 8px; bottom: 8px; width: 1px; background: var(--border); }
  .tl-item { position: relative; margin-bottom: 28px; padding-left: 24px; }
  .tl-dot { position: absolute; left: -24px; top: 6px; width: 9px; height: 9px; border-radius: 50%; border: 2px solid var(--accent); background: var(--bg); }
  .tl-date { font-size: 11px; color: var(--muted); font-family: var(--mono); margin-bottom: 4px; }
  .tl-title { font-size: 14px; font-weight: 500; margin-bottom: 2px; }
  .tl-sub { font-size: 12px; color: var(--muted); margin-bottom: 6px; }
  .tl-points { list-style: none; }
  .tl-points li { font-size: 12px; color: var(--muted); padding: 2px 0; display: flex; gap: 8px; }
  .tl-points li::before { content: '→'; color: var(--accent); flex-shrink: 0; }

  /* CERTS */
  .certs-section { max-width: 860px; margin: 0 auto 60px; padding: 0 2rem; }
  .certs-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 12px; }
  .cert-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 20px; display: flex; align-items: center; gap: 16px; transition: border-color 0.2s; }
  .cert-card:hover { border-color: rgba(186,117,23,0.5); }
  .cert-icon { width: 44px; height: 44px; border-radius: 10px; background: rgba(186,117,23,0.12); border: 1px solid rgba(186,117,23,0.25); display: flex; align-items: center; justify-content: center; font-size: 20px; flex-shrink: 0; }
  .cert-name { font-size: 13px; font-weight: 500; margin-bottom: 3px; }
  .cert-date { font-size: 11px; color: var(--muted); font-family: var(--mono); }

  /* CONTACT */
  .contact-section { max-width: 860px; margin: 0 auto 80px; padding: 0 2rem; }
  .contact-card { background: var(--surface); border: 1px solid var(--border); border-radius: 16px; padding: 36px; display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 24px; }
  .contact-left h2 { font-size: 22px; font-weight: 600; margin-bottom: 6px; }
  .contact-left p { font-size: 14px; color: var(--muted); }
  .contact-links { display: flex; flex-wrap: wrap; gap: 10px; }
  .contact-link { display: inline-flex; align-items: center; gap: 7px; padding: 9px 18px; border-radius: 8px; font-size: 13px; text-decoration: none; border: 1px solid var(--border-hover); color: var(--text); transition: all 0.18s; }
  .contact-link:hover { background: var(--card); border-color: var(--text); }

  /* FOOTER */
  footer { border-top: 1px solid var(--border); text-align: center; padding: 24px; font-size: 12px; color: var(--muted); font-family: var(--mono); }

  @media (max-width: 600px) {
    nav .links { display: none; }
    .hero h1 { font-size: 28px; }
  }
</style>
</head>
<body>

<nav>
  <div class="logo">ankit.dhandharia ~</div>
  <div class="links">
    <a href="#about">about</a>
    <a href="#skills">skills</a>
    <a href="#projects">projects</a>
    <a href="#experience">experience</a>
    <a href="#contact">contact</a>
  </div>
</nav>

<section class="hero" id="about">
  <div class="hero-tag">&#x2714; AWS Certified &nbsp;·&nbsp; Open to opportunities</div>
  <h1>Hi, I'm <span>Ankit Dhandharia</span></h1>
  <div class="hero-roles">
    <span class="role-pill de">Data Engineer</span>
    <span class="role-pill ai">AI / ML Engineer</span>
    <span class="role-pill se">Software Engineer</span>
    <span class="role-pill ds">Data Scientist</span>
  </div>
  <p class="hero-sub">
    I build systems that turn raw data into real decisions — from <strong>Medallion Architecture warehouses</strong> in Snowflake to <strong>RAG pipelines</strong> powered by LangChain. Currently finishing my <strong>MSCS at Stevens Institute of Technology</strong> (GPA 3.709).
  </p>
  <div class="cta-row">
    <a class="btn btn-primary" href="mailto:adhandha@stevens.edu">&#x2709; Get in touch</a>
    <a class="btn btn-outline" href="https://linkedin.com/in/ankit-dhandharia/" target="_blank">&#128101; LinkedIn</a>
    <a class="btn btn-outline" href="https://github.com/Ankit455" target="_blank">&#128030; GitHub</a>
  </div>
</section>

<div class="terminal-wrap">
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot r"></div><div class="dot y"></div><div class="dot g"></div>
      <span class="terminal-title">ankit@dev: ~/profile</span>
    </div>
    <div class="terminal-body" id="terminal-body"></div>
  </div>
</div>

<section class="stats-section">
  <div class="stats-grid">
    <div class="stat-cell"><div class="stat-num blue" data-target="500" data-suffix="k+">0</div><div class="stat-label">Daily records<br>processed</div></div>
    <div class="stat-cell"><div class="stat-num green" data-target="35" data-suffix="%">0</div><div class="stat-label">Pipeline latency<br>reduction</div></div>
    <div class="stat-cell"><div class="stat-num amber" data-target="40" data-suffix="%">0</div><div class="stat-label">Compute cost<br>savings</div></div>
    <div class="stat-cell"><div class="stat-num purple" data-target="200" data-suffix="GB+">0</div><div class="stat-label">Legacy data<br>migrated</div></div>
    <div class="stat-cell"><div class="stat-num blue" data-target="40" data-suffix="+">0</div><div class="stat-label">Clients<br>served</div></div>
  </div>
</section>

<section class="domains-section" id="skills">
  <div class="section-label">Expertise — click a domain to expand</div>
  <div class="domains-grid">
    <div class="domain-card" data-domain="de" style="--dcolor: #378ADD;" onclick="toggleDomain('de')">
      <div class="domain-icon">&#9881;</div>
      <div class="domain-title">Data Engineering</div>
      <div class="domain-sub">Pipelines · Warehouses · Streaming</div>
    </div>
    <div class="domain-card" data-domain="ai" style="--dcolor: #7F77DD;" onclick="toggleDomain('ai')">
      <div class="domain-icon">&#129302;</div>
      <div class="domain-title">AI / ML Engineering</div>
      <div class="domain-sub">RAG · LLMs · Vector DBs</div>
    </div>
    <div class="domain-card" data-domain="se" style="--dcolor: #1D9E75;" onclick="toggleDomain('se')">
      <div class="domain-icon">&#128187;</div>
      <div class="domain-title">Software Engineering</div>
      <div class="domain-sub">APIs · Backend · DevOps</div>
    </div>
    <div class="domain-card" data-domain="ds" style="--dcolor: #BA7517;" onclick="toggleDomain('ds')">
      <div class="domain-icon">&#128202;</div>
      <div class="domain-title">Data Science</div>
      <div class="domain-sub">EDA · Modeling · Visualization</div>
    </div>
  </div>
</section>

<div class="domain-detail" id="detail-de">
  <div class="detail-inner">
    <h3 style="color:#85B7EB;">Data Engineering</h3>
    <div class="skill-bars">
      <div class="bar-row"><span class="bar-label">Apache Spark</span><div class="bar-track"><div class="bar-fill" style="background:#378ADD" data-w="90"></div></div><span class="bar-pct">90%</span></div>
      <div class="bar-row"><span class="bar-label">Apache Airflow</span><div class="bar-track"><div class="bar-fill" style="background:#378ADD" data-w="88"></div></div><span class="bar-pct">88%</span></div>
      <div class="bar-row"><span class="bar-label">dbt Core</span><div class="bar-track"><div class="bar-fill" style="background:#378ADD" data-w="85"></div></div><span class="bar-pct">85%</span></div>
      <div class="bar-row"><span class="bar-label">Kafka / Kinesis</span><div class="bar-track"><div class="bar-fill" style="background:#378ADD" data-w="80"></div></div><span class="bar-pct">80%</span></div>
      <div class="bar-row"><span class="bar-label">Snowflake</span><div class="bar-track"><div class="bar-fill" style="background:#378ADD" data-w="88"></div></div><span class="bar-pct">88%</span></div>
    </div>
  </div>
</div>
<div class="domain-detail" id="detail-ai">
  <div class="detail-inner">
    <h3 style="color:#AFA9EC;">AI / ML Engineering</h3>
    <div class="skill-bars">
      <div class="bar-row"><span class="bar-label">LangChain</span><div class="bar-track"><div class="bar-fill" style="background:#7F77DD" data-w="85"></div></div><span class="bar-pct">85%</span></div>
      <div class="bar-row"><span class="bar-label">HuggingFace</span><div class="bar-track"><div class="bar-fill" style="background:#7F77DD" data-w="82"></div></div><span class="bar-pct">82%</span></div>
      <div class="bar-row"><span class="bar-label">Scikit-learn</span><div class="bar-track"><div class="bar-fill" style="background:#7F77DD" data-w="78"></div></div><span class="bar-pct">78%</span></div>
      <div class="bar-row"><span class="bar-label">ChromaDB / RAG</span><div class="bar-track"><div class="bar-fill" style="background:#7F77DD" data-w="83"></div></div><span class="bar-pct">83%</span></div>
      <div class="bar-row"><span class="bar-label">TensorFlow</span><div class="bar-track"><div class="bar-fill" style="background:#7F77DD" data-w="70"></div></div><span class="bar-pct">70%</span></div>
    </div>
  </div>
</div>
<div class="domain-detail" id="detail-se">
  <div class="detail-inner">
    <h3 style="color:#5DCAA5;">Software Engineering</h3>
    <div class="skill-bars">
      <div class="bar-row"><span class="bar-label">Python</span><div class="bar-track"><div class="bar-fill" style="background:#1D9E75" data-w="95"></div></div><span class="bar-pct">95%</span></div>
      <div class="bar-row"><span class="bar-label">FastAPI / Flask</span><div class="bar-track"><div class="bar-fill" style="background:#1D9E75" data-w="85"></div></div><span class="bar-pct">85%</span></div>
      <div class="bar-row"><span class="bar-label">Docker / K8s</span><div class="bar-track"><div class="bar-fill" style="background:#1D9E75" data-w="80"></div></div><span class="bar-pct">80%</span></div>
      <div class="bar-row"><span class="bar-label">GitHub Actions CI/CD</span><div class="bar-track"><div class="bar-fill" style="background:#1D9E75" data-w="82"></div></div><span class="bar-pct">82%</span></div>
      <div class="bar-row"><span class="bar-label">SQL (Postgres/MySQL)</span><div class="bar-track"><div class="bar-fill" style="background:#1D9E75" data-w="92"></div></div><span class="bar-pct">92%</span></div>
    </div>
  </div>
</div>
<div class="domain-detail" id="detail-ds">
  <div class="detail-inner">
    <h3 style="color:#EF9F27;">Data Science</h3>
    <div class="skill-bars">
      <div class="bar-row"><span class="bar-label">Pandas / Polars</span><div class="bar-track"><div class="bar-fill" style="background:#BA7517" data-w="90"></div></div><span class="bar-pct">90%</span></div>
      <div class="bar-row"><span class="bar-label">EDA / Feature Eng.</span><div class="bar-track"><div class="bar-fill" style="background:#BA7517" data-w="85"></div></div><span class="bar-pct">85%</span></div>
      <div class="bar-row"><span class="bar-label">Power BI / Tableau</span><div class="bar-track"><div class="bar-fill" style="background:#BA7517" data-w="80"></div></div><span class="bar-pct">80%</span></div>
      <div class="bar-row"><span class="bar-label">Dimensional Modeling</span><div class="bar-track"><div class="bar-fill" style="background:#BA7517" data-w="88"></div></div><span class="bar-pct">88%</span></div>
      <div class="bar-row"><span class="bar-label">R</span><div class="bar-track"><div class="bar-fill" style="background:#BA7517" data-w="65"></div></div><span class="bar-pct">65%</span></div>
    </div>
  </div>
</div>

<section class="projects-section" id="projects">
  <div class="section-label">Featured projects</div>
  <div class="projects-grid">
    <div class="proj-card">
      <span class="proj-tag de">Data Engineering</span>
      <div class="proj-title">End-to-End Streaming Pipeline</div>
      <div class="proj-desc">Medallion Architecture (Bronze/Silver/Gold) with real-time Kafka ingestion, dbt Jinja macros, SCD Type 2 snapshots, and 40% compute savings via Incremental Materialization.</div>
      <div class="proj-stack">
        <span class="stack-tag">Kafka</span><span class="stack-tag">Spark</span><span class="stack-tag">Snowflake</span><span class="stack-tag">dbt</span><span class="stack-tag">Airflow</span><span class="stack-tag">Docker</span><span class="stack-tag">GitHub Actions</span>
      </div>
    </div>
    <div class="proj-card">
      <span class="proj-tag ai">AI / ML</span>
      <div class="proj-title">Scalable RAG Pipeline</div>
      <div class="proj-desc">Zero-cost production RAG backend using local HuggingFace embeddings (384-dim), persistent ChromaDB vector store, sub-second retrieval across 400+ page documents via FastAPI.</div>
      <div class="proj-stack">
        <span class="stack-tag">LangChain</span><span class="stack-tag">FastAPI</span><span class="stack-tag">ChromaDB</span><span class="stack-tag">HuggingFace</span><span class="stack-tag">SQLite</span>
      </div>
    </div>
  </div>
</section>

<section class="timeline-section" id="experience">
  <div class="section-label">Experience</div>
  <div class="timeline">
    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-date">May 2023 – June 2024</div>
      <div class="tl-title">Data Engineer</div>
      <div class="tl-sub">Rajlaxmi Solutions Private Limited · Thane, India</div>
      <ul class="tl-points">
        <li>500k+ daily records processed across 40+ clients via Python, Spark & Airflow</li>
        <li>Snowflake warehouse design with dimensional modeling & SCD Type 2</li>
        <li>Schema validation, anomaly detection & SLA alerting — Industry Excellence Award</li>
      </ul>
    </div>
    <div class="tl-item">
      <div class="tl-dot" style="border-color: var(--accent2);"></div>
      <div class="tl-date">Jan 2023 – May 2023</div>
      <div class="tl-title">Data Analyst Intern</div>
      <div class="tl-sub">Rajlaxmi Solutions Private Limited · Thane, India</div>
      <ul class="tl-points">
        <li>200GB+ legacy database migration to cloud — 25% SQL performance gain</li>
        <li>Automated Airflow reporting — eliminated 15+ hrs/month of manual effort</li>
      </ul>
    </div>
    <div class="tl-item">
      <div class="tl-dot" style="border-color: var(--accent4);"></div>
      <div class="tl-date">Exp. May 2026</div>
      <div class="tl-title">MSCS · Stevens Institute of Technology</div>
      <div class="tl-sub">Hoboken, NJ · GPA 3.709 / 4.0</div>
    </div>
  </div>
</section>

<section class="certs-section">
  <div class="section-label">Certifications</div>
  <div class="certs-grid">
    <div class="cert-card">
      <div class="cert-icon">&#9728;</div>
      <div><div class="cert-name">AWS Certified Data Engineer – Associate</div><div class="cert-date">March 2026 · Amazon Web Services</div></div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">&#127891;</div>
      <div><div class="cert-name">AWS Academy Data Engineering</div><div class="cert-date">April 2026 · Amazon Web Services</div></div>
    </div>
  </div>
</section>

<section class="contact-section" id="contact">
  <div class="contact-card">
    <div class="contact-left">
      <h2>Let's build something.</h2>
      <p>Open to full-time roles in Data Engineering, AI/ML, and Software Engineering.</p>
    </div>
    <div class="contact-links">
      <a class="contact-link" href="mailto:adhandha@stevens.edu">&#x2709; adhandha@stevens.edu</a>
      <a class="contact-link" href="https://linkedin.com/in/ankit-dhandharia/" target="_blank">&#128101; LinkedIn</a>
      <a class="contact-link" href="https://github.com/Ankit455" target="_blank">&#128030; GitHub</a>
    </div>
  </div>
</section>

<footer>built by ankit dhandharia &nbsp;·&nbsp; union city, nj &nbsp;·&nbsp; 2026</footer>

<script>
const lines = [
  { type: 'prompt', text: '$ whoami' },
  { type: 'out hi', text: 'ankit dhandharia — data engineer, ai/ml engineer, software engineer' },
  { type: 'prompt', text: '$ cat certifications.txt' },
  { type: 'out ok', text: '[✓] AWS Certified Data Engineer – Associate (Mar 2026)' },
  { type: 'out ok', text: '[✓] AWS Academy Data Engineering (Apr 2026)' },
  { type: 'prompt', text: '$ grep -r "impact" ./experience/' },
  { type: 'out warn', text: '→ 500k+ daily records processed · 35% latency reduction' },
  { type: 'out warn', text: '→ 40% compute cost savings · 200GB+ legacy data migrated' },
  { type: 'out warn', text: '→ Industry Excellence Award for client analytics delivery' },
  { type: 'prompt', text: '$ ls projects/' },
  { type: 'out', text: 'streaming_pipeline/  rag_document_analysis/  more_coming_soon/' },
  { type: 'prompt', text: '$ echo "open to full-time opportunities"' },
  { type: 'out hi', text: 'open to full-time opportunities' },
  { type: 'cursor', text: '' },
];

const tb = document.getElementById('terminal-body');
let i = 0;
function nextLine() {
  if (i >= lines.length) return;
  const l = lines[i++];
  const div = document.createElement('div');
  div.className = 'line ' + (l.type === 'cursor' ? 'out' : l.type);
  if (l.type === 'cursor') {
    div.innerHTML = '<span class="prompt">$ </span><span class="cursor"></span>';
  } else if (l.type.startsWith('prompt')) {
    div.innerHTML = '<span class="prompt">$ </span><span class="cmd">' + l.text.slice(2) + '</span>';
  } else {
    div.textContent = l.text;
  }
  tb.appendChild(div);
  requestAnimationFrame(() => { div.classList.add('show'); });
  if (l.type !== 'cursor') setTimeout(nextLine, l.type.startsWith('prompt') ? 500 : 180);
}
setTimeout(nextLine, 600);

function animateCounters() {
  document.querySelectorAll('.stat-num[data-target]').forEach(el => {
    const target = parseInt(el.dataset.target);
    const suffix = el.dataset.suffix || '';
    let current = 0;
    const step = Math.ceil(target / 40);
    const interval = setInterval(() => {
      current = Math.min(current + step, target);
      el.textContent = current + suffix;
      if (current >= target) clearInterval(interval);
    }, 30);
  });
}
const statsObs = new IntersectionObserver(entries => {
  if (entries[0].isIntersecting) { animateCounters(); statsObs.disconnect(); }
}, { threshold: 0.3 });
statsObs.observe(document.querySelector('.stats-grid'));

function toggleDomain(domain) {
  const detail = document.getElementById('detail-' + domain);
  const card = document.querySelector('[data-domain="' + domain + '"]');
  const isOpen = detail.classList.contains('open');
  document.querySelectorAll('.domain-detail').forEach(d => d.classList.remove('open'));
  document.querySelectorAll('.domain-card').forEach(c => c.classList.remove('active'));
  if (!isOpen) {
    detail.classList.add('open');
    card.classList.add('active');
    setTimeout(() => {
      detail.querySelectorAll('.bar-fill').forEach(bar => {
        bar.style.width = bar.dataset.w + '%';
      });
    }, 50);
  } else {
    detail.querySelectorAll('.bar-fill').forEach(bar => { bar.style.width = '0'; });
  }
}
</script>
</body>
</html>
