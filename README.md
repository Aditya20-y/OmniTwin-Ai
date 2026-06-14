# Omni-Twin-Ai
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>OmniTwin AI — Master Blueprint</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;1,300&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #08090d;
    --surface: #0f1118;
    --surface2: #161922;
    --border: #1e2230;
    --accent: #4fffb0;
    --accent2: #7b6fff;
    --accent3: #ff6b6b;
    --accent4: #ffd93d;
    --text: #e8eaf0;
    --muted: #5a6070;
    --dim: #30364a;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    line-height: 1.6;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(79,255,176,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(79,255,176,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
    position: relative;
    z-index: 1;
  }

  /* ── HEADER ── */
  header {
    padding: 48px 0 32px;
    border-bottom: 1px solid var(--border);
    position: relative;
  }

  .header-tag {
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .header-tag::before {
    content: '';
    width: 24px;
    height: 1px;
    background: var(--accent);
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.4rem, 5vw, 4rem);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -0.02em;
    color: #fff;
    margin-bottom: 8px;
  }

  h1 span {
    color: var(--accent);
  }

  .header-sub {
    font-family: 'Instrument Serif', serif;
    font-style: italic;
    font-size: 1.1rem;
    color: var(--muted);
    margin-top: 10px;
    max-width: 600px;
  }

  .status-row {
    display: flex;
    align-items: center;
    gap: 24px;
    margin-top: 20px;
    flex-wrap: wrap;
  }

  .badge {
    padding: 4px 12px;
    border-radius: 2px;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    font-weight: 600;
    border: 1px solid;
  }

  .badge-green { border-color: var(--accent); color: var(--accent); background: rgba(79,255,176,0.08); }
  .badge-purple { border-color: var(--accent2); color: var(--accent2); background: rgba(123,111,255,0.08); }
  .badge-yellow { border-color: var(--accent4); color: var(--accent4); background: rgba(255,217,61,0.08); }

  /* ── NAV TABS ── */
  .tab-bar {
    display: flex;
    gap: 2px;
    padding: 24px 0 0;
    overflow-x: auto;
    scrollbar-width: none;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tab-bar::-webkit-scrollbar { display: none; }

  .tab {
    padding: 8px 16px;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .tab:hover { border-color: var(--dim); color: var(--text); }

  .tab.active {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(79,255,176,0.06);
  }

  /* ── MAIN CONTENT ── */
  .section {
    display: none;
    padding: 40px 0;
    animation: fadeIn 0.3s ease;
  }

  .section.active { display: block; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── SECTION HEADING ── */
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 6px;
  }

  .section-desc {
    color: var(--muted);
    font-size: 12px;
    margin-bottom: 32px;
    max-width: 640px;
  }

  /* ── GRID LAYOUTS ── */
  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
  .grid-auto { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 16px; }

  @media (max-width: 768px) {
    .grid-2, .grid-3 { grid-template-columns: 1fr; }
  }

  /* ── CARDS ── */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 24px;
    position: relative;
    transition: border-color 0.2s, transform 0.2s;
  }

  .card:hover {
    border-color: var(--dim);
    transform: translateY(-2px);
  }

  .card-accent { border-left: 3px solid var(--accent); }
  .card-purple { border-left: 3px solid var(--accent2); }
  .card-red    { border-left: 3px solid var(--accent3); }
  .card-yellow { border-left: 3px solid var(--accent4); }

  .card-num {
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 10px;
    letter-spacing: 0.1em;
  }

  .card-title {
    font-family: 'Syne', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    color: #fff;
    margin-bottom: 8px;
  }

  .card-body {
    color: var(--muted);
    font-size: 12px;
    line-height: 1.7;
  }

  .card-tag {
    display: inline-block;
    padding: 2px 8px;
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--muted);
    margin-top: 12px;
  }

  /* ── CODE BLOCK ── */
  .code-block {
    background: var(--surface2);
    border: 1px solid var(--border);
    padding: 20px 24px;
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    color: #b8c4d0;
    line-height: 2;
    overflow-x: auto;
    position: relative;
  }

  .code-block .kw { color: var(--accent); }
  .code-block .str { color: var(--accent4); }
  .code-block .cmt { color: var(--muted); font-style: italic; }
  .code-block .purple { color: var(--accent2); }
  .code-block .red { color: var(--accent3); }

  .code-label {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
    border-bottom: 1px solid var(--border);
    padding-bottom: 10px;
  }

  /* ── PHASE TIMELINE ── */
  .phases {
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  .phase-item {
    display: grid;
    grid-template-columns: 60px 1fr;
    gap: 0;
    position: relative;
  }

  .phase-item:not(:last-child)::before {
    content: '';
    position: absolute;
    left: 29px;
    top: 48px;
    bottom: 0;
    width: 2px;
    background: var(--border);
  }

  .phase-left {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 20px;
  }

  .phase-dot {
    width: 18px;
    height: 18px;
    border: 2px solid var(--border);
    background: var(--bg);
    border-radius: 50%;
    flex-shrink: 0;
    position: relative;
    z-index: 1;
    transition: border-color 0.2s, background 0.2s;
    cursor: pointer;
  }

  .phase-dot.done { border-color: var(--accent); background: var(--accent); }
  .phase-dot.active-phase { border-color: var(--accent2); box-shadow: 0 0 0 4px rgba(123,111,255,0.2); }

  .phase-right {
    padding: 16px 0 16px 20px;
  }

  .phase-num { font-size: 10px; color: var(--muted); letter-spacing: 0.1em; }
  .phase-name {
    font-family: 'Syne', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    color: #fff;
    margin: 4px 0;
  }

  .phase-detail { font-size: 11px; color: var(--muted); }

  /* ── TECH STACK GRID ── */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .tech-card {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 16px 20px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    transition: border-color 0.2s;
  }

  .tech-card:hover { border-color: var(--accent); }

  .tech-role { font-size: 10px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.12em; }
  .tech-name {
    font-family: 'Syne', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: #fff;
  }

  .tech-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--accent);
    margin-bottom: 4px;
  }

  .tech-dot.purple { background: var(--accent2); }
  .tech-dot.red { background: var(--accent3); }
  .tech-dot.yellow { background: var(--accent4); }

  /* ── API TABLE ── */
  .api-table { width: 100%; border-collapse: collapse; }

  .api-table th {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    padding: 10px 16px;
    text-align: left;
    border-bottom: 1px solid var(--border);
  }

  .api-table td {
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
    font-size: 12px;
    vertical-align: top;
  }

  .api-table tr:hover td { background: var(--surface2); }

  .method {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.1em;
    padding: 3px 8px;
    border-radius: 2px;
  }

  .method-post { background: rgba(79,255,176,0.15); color: var(--accent); }
  .method-get  { background: rgba(123,111,255,0.15); color: var(--accent2); }

  .endpoint { color: var(--accent4); font-family: 'DM Mono', monospace; }

  /* ── KG RELATIONSHIPS ── */
  .rel-list { display: flex; flex-direction: column; gap: 10px; }

  .rel-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 16px;
    background: var(--surface);
    border: 1px solid var(--border);
    font-size: 12px;
  }

  .rel-node {
    padding: 4px 10px;
    background: var(--surface2);
    border: 1px solid var(--dim);
    color: var(--accent);
    font-size: 11px;
    white-space: nowrap;
  }

  .rel-edge {
    flex: 1;
    text-align: center;
    color: var(--muted);
    font-size: 10px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }

  .rel-edge::before, .rel-edge::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--dim);
  }

  /* ── METRICS ── */
  .metric-card {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 20px;
    text-align: center;
  }

  .metric-value {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    color: var(--accent);
    line-height: 1;
  }

  .metric-label { font-size: 11px; color: var(--muted); margin-top: 6px; text-transform: uppercase; letter-spacing: 0.1em; }

  /* ── FOLDER TREE ── */
  .tree {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    line-height: 2;
    color: #b8c4d0;
  }

  .tree .dir  { color: var(--accent); }
  .tree .file { color: var(--muted); }
  .tree .root { color: #fff; font-weight: 600; font-family: 'Syne', sans-serif; }

  /* ── DB SCHEMA ── */
  .schema-table {
    background: var(--surface);
    border: 1px solid var(--border);
    overflow: hidden;
  }

  .schema-header {
    background: var(--surface2);
    padding: 10px 16px;
    font-family: 'Syne', sans-serif;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--accent);
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .schema-header::before {
    content: '⬡';
    font-size: 0.7rem;
  }

  .schema-row {
    display: flex;
    align-items: center;
    padding: 8px 16px;
    border-bottom: 1px solid var(--border);
    font-size: 11px;
    gap: 12px;
  }

  .schema-row:last-child { border-bottom: none; }

  .field-name { color: var(--text); flex: 1; }
  .field-type { color: var(--accent2); font-size: 10px; }
  .field-pk { color: var(--accent4); font-size: 9px; letter-spacing: 0.1em; }

  /* ── WORKFLOW STEPS ── */
  .workflow {
    display: flex;
    gap: 0;
    overflow-x: auto;
    padding-bottom: 8px;
  }

  .wf-step {
    flex-shrink: 0;
    min-width: 140px;
    padding: 16px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-right: none;
    position: relative;
  }

  .wf-step:last-child { border-right: 1px solid var(--border); }

  .wf-step::after {
    content: '→';
    position: absolute;
    right: -14px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--accent);
    font-size: 14px;
    z-index: 2;
    background: var(--bg);
    padding: 0 2px;
  }

  .wf-step:last-child::after { display: none; }

  .wf-num { font-size: 10px; color: var(--accent); margin-bottom: 6px; }
  .wf-label { font-size: 11px; color: var(--text); line-height: 1.4; }

  /* ── PROGRESS BARS ── */
  .progress-row { margin-bottom: 14px; }
  .progress-label {
    display: flex;
    justify-content: space-between;
    font-size: 11px;
    margin-bottom: 6px;
  }
  .progress-label span:first-child { color: var(--text); }
  .progress-label span:last-child { color: var(--muted); }

  .progress-bar {
    height: 4px;
    background: var(--border);
    border-radius: 0;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: var(--accent);
    border-radius: 0;
    transition: width 1s ease;
  }

  .progress-fill.purple { background: var(--accent2); }
  .progress-fill.red { background: var(--accent3); }
  .progress-fill.yellow { background: var(--accent4); }

  /* ── DIVIDER ── */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 28px 0;
  }

  /* ── SMALL HELPERS ── */
  .label {
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 14px;
    display: block;
  }

  .gap-y-16 { display: flex; flex-direction: column; gap: 16px; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 24px 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: gap;
  }

  .footer-left { font-size: 11px; color: var(--muted); }
  .footer-right { font-size: 11px; color: var(--muted); text-align: right; }

  .pulse {
    display: inline-block;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--accent);
    animation: pulse 2s infinite;
    vertical-align: middle;
    margin-right: 6px;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.8); }
  }

  /* ── CALLOUT BOX ── */
  .callout {
    border-left: 3px solid var(--accent4);
    padding: 16px 20px;
    background: rgba(255,217,61,0.05);
    font-size: 12px;
    color: #c8b870;
    line-height: 1.7;
    margin-bottom: 24px;
  }

  .callout strong { color: var(--accent4); }
</style>
</head>
<body>

<div class="container">
  <header>
    <div class="header-tag">Master Blueprint v1.0</div>
    <h1>Omni<span>Twin</span> AI</h1>
    <p class="header-sub">A personal digital twin for researchers — from GitHub setup to production deployment.</p>
    <div class="status-row">
      <span class="badge badge-green">● Active Development</span>
      <span class="badge badge-purple">9 Build Phases</span>
      <span class="badge badge-yellow">6 Core Modules</span>
    </div>

    <div class="tab-bar">
      <button class="tab active" onclick="show('vision')">Vision</button>
      <button class="tab" onclick="show('modules')">Modules</button>
      <button class="tab" onclick="show('stack')">Tech Stack</button>
      <button class="tab" onclick="show('phases')">Phases</button>
      <button class="tab" onclick="show('structure')">Structure</button>
      <button class="tab" onclick="show('apis')">APIs</button>
      <button class="tab" onclick="show('database')">Database</button>
      <button class="tab" onclick="show('graph')">Knowledge Graph</button>
      <button class="tab" onclick="show('metrics')">Metrics</button>
      <button class="tab" onclick="show('workflow')">Workflow</button>
    </div>
  </header>

  <!-- ── VISION ── -->
  <section class="section active" id="vision">
    <p class="section-title">Project Vision</p>
    <p class="section-desc">OmniTwin AI is a long-term platform that models the learner, discovers research opportunities, and unifies knowledge into a living graph.</p>

    <div class="callout">
      <strong>Core Problem:</strong> Students and researchers face information overload. Existing tools summarize — but they don't <em>model the learner</em>, discover research gaps, or connect knowledge into a unified, evolving system.
    </div>

    <div class="grid-3">
      <div class="card card-accent">
        <div class="card-num">01 / CORE</div>
        <div class="card-title">Personal Digital Twin</div>
        <div class="card-body">An AI model of the user — tracking interests, knowledge gaps, learning velocity, and domain expertise over time.</div>
        <span class="card-tag">User Twin</span>
      </div>
      <div class="card card-purple">
        <div class="card-num">02 / CORE</div>
        <div class="card-title">Research Intelligence</div>
        <div class="card-body">Ingests papers, builds semantic indexes, and surfaces connections between ideas across disciplines.</div>
        <span class="card-tag">Research Twin</span>
      </div>
      <div class="card card-yellow">
        <div class="card-num">03 / CORE</div>
        <div class="card-title">Gap Discovery Engine</div>
        <div class="card-body">Detects contradictions, underexplored combinations, missing benchmarks, and emerging research frontiers.</div>
        <span class="card-tag">Research Gaps</span>
      </div>
    </div>

    <hr class="divider">

    <span class="label">Strategic Direction</span>
    <div class="grid-2">
      <div class="card">
        <div class="card-title">Build as a Product</div>
        <div class="card-body">Treat OmniTwin as a product, not merely a project. Ship small versions regularly. Build publicly and iterate. Document everything and use GitHub consistently.</div>
      </div>
      <div class="card">
        <div class="card-title">Milestone Philosophy</div>
        <div class="card-body">Each phase produces a working, shippable increment. No big-bang launches. Early phases focus on core plumbing; later phases add intelligence layer by layer.</div>
      </div>
    </div>

    <hr class="divider">
    <span class="label">Platform Trajectory</span>
    <div class="progress-row">
      <div class="progress-label"><span>Core Research Platform</span><span>Phase 1–5</span></div>
      <div class="progress-bar"><div class="progress-fill" style="width: 55%"></div></div>
    </div>
    <div class="progress-row">
      <div class="progress-label"><span>Knowledge Graph Layer</span><span>Phase 6</span></div>
      <div class="progress-bar"><div class="progress-fill purple" style="width: 65%"></div></div>
    </div>
    <div class="progress-row">
      <div class="progress-label"><span>Gap Discovery & Verification</span><span>Phase 7–8</span></div>
      <div class="progress-bar"><div class="progress-fill yellow" style="width: 75%"></div></div>
    </div>
    <div class="progress-row">
      <div class="progress-label"><span>Future Modules (Deepfake / Cyber)</span><span>Roadmap</span></div>
      <div class="progress-bar"><div class="progress-fill red" style="width: 20%"></div></div>
    </div>
  </section>

  <!-- ── MODULES ── -->
  <section class="section" id="modules">
    <p class="section-title">Core Modules</p>
    <p class="section-desc">Six active modules form the foundation. Three future modules extend the platform into safety and synthetic data.</p>

    <span class="label">Active Modules</span>
    <div class="grid-auto">
      <div class="card card-accent">
        <div class="card-num">MODULE 01</div>
        <div class="card-title">User Twin</div>
        <div class="card-body">Models user interests, expertise, learning velocity. Personalizes every surface of the platform dynamically.</div>
      </div>
      <div class="card card-purple">
        <div class="card-num">MODULE 02</div>
        <div class="card-title">Research Twin</div>
        <div class="card-body">Domain-level knowledge model. Tracks field evolution, key authors, methodological trends, and citation topology.</div>
      </div>
      <div class="card card-accent">
        <div class="card-num">MODULE 03</div>
        <div class="card-title">Personal Knowledge Graph</div>
        <div class="card-body">Builds a user-specific graph connecting papers, concepts, methods, and datasets into a navigable web.</div>
      </div>
      <div class="card card-yellow">
        <div class="card-num">MODULE 04</div>
        <div class="card-title">Research Gap Discovery</div>
        <div class="card-body">Surfaces contradictions, underexplored combinations, missing benchmarks. Outputs actionable project ideas.</div>
      </div>
      <div class="card card-red">
        <div class="card-num">MODULE 05</div>
        <div class="card-title">Hallucination Verification</div>
        <div class="card-body">Cross-checks AI-generated content against ingested papers. Flags unsupported claims with source references.</div>
      </div>
      <div class="card card-purple">
        <div class="card-num">MODULE 06</div>
        <div class="card-title">Learning Companion</div>
        <div class="card-body">Adaptive study planner, concept explainer, and progress tracker. Routes learning based on the User Twin model.</div>
      </div>
    </div>

    <hr class="divider">
    <span class="label">Future Modules</span>
    <div class="grid-3">
      <div class="card" style="opacity: 0.6;">
        <div class="card-num">MODULE 07 — FUTURE</div>
        <div class="card-title">Deepfake Detection</div>
        <div class="card-body">Identify synthetic media in research contexts. Protect the integrity of visual evidence.</div>
      </div>
      <div class="card" style="opacity: 0.6;">
        <div class="card-num">MODULE 08 — FUTURE</div>
        <div class="card-title">Cyber Defense Agent</div>
        <div class="card-body">Autonomous agent for detecting vulnerabilities and monitoring platform security posture.</div>
      </div>
      <div class="card" style="opacity: 0.6;">
        <div class="card-num">MODULE 09 — FUTURE</div>
        <div class="card-title">Synthetic Data Generator</div>
        <div class="card-body">Generate domain-specific training data for fine-tuning models on specialized research corpora.</div>
      </div>
    </div>
  </section>

  <!-- ── STACK ── -->
  <section class="section" id="stack">
    <p class="section-title">Technology Stack</p>
    <p class="section-desc">Production-grade, open-source-first stack. Designed for horizontal scaling and cloud-agnostic deployment.</p>

    <div class="tech-grid">
      <div class="tech-card">
        <div class="tech-dot"></div>
        <div class="tech-role">Backend</div>
        <div class="tech-name">Python + FastAPI</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot purple"></div>
        <div class="tech-role">Frontend</div>
        <div class="tech-name">Next.js + TypeScript</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot yellow"></div>
        <div class="tech-role">Relational DB</div>
        <div class="tech-name">PostgreSQL</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot"></div>
        <div class="tech-role">Vector DB</div>
        <div class="tech-name">Qdrant</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot purple"></div>
        <div class="tech-role">Graph DB</div>
        <div class="tech-name">Neo4j</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot red"></div>
        <div class="tech-role">Containers</div>
        <div class="tech-name">Docker + Compose</div>
      </div>
      <div class="tech-card">
        <div class="tech-dot yellow"></div>
        <div class="tech-role">Cloud</div>
        <div class="tech-name">AWS / GCP / Azure</div>
      </div>
      <div class="tech-card" style="opacity: 0.6;">
        <div class="tech-dot red"></div>
        <div class="tech-role">Monitoring (future)</div>
        <div class="tech-name">Prometheus + Grafana</div>
      </div>
    </div>

    <hr class="divider">
    <span class="label">Architecture Overview</span>
    <div class="code-block">
      <div class="code-label">omnitwin — service topology</div>
      <span class="cmt"># Request Flow</span><br>
      Client (Next.js) <span class="kw">→</span> FastAPI Gateway <span class="kw">→</span> [Auth Middleware]<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">→</span> PostgreSQL   <span class="cmt"># Users, Papers, Sessions</span><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">→</span> Qdrant       <span class="cmt"># Embedding search</span><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">→</span> Neo4j        <span class="cmt"># Graph traversal</span><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">→</span> LLM Service  <span class="cmt"># Summarization, gap detection</span><br>
      <br>
      <span class="cmt"># Branches</span><br>
      <span class="str">main</span> <span class="kw">←</span> <span class="str">development</span> <span class="kw">←</span> <span class="purple">feature/*</span>
    </div>
  </section>

  <!-- ── PHASES ── -->
  <section class="section" id="phases">
    <p class="section-title">Development Phases</p>
    <p class="section-desc">Nine sequential build phases, each producing a shippable, testable increment.</p>

    <div class="phases">
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot done"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 01</div>
          <div class="phase-name">Authentication & User Profiles</div>
          <div class="phase-detail">JWT auth, user CRUD, session management, PostgreSQL schema setup. Foundation for the User Twin.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot done"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 02</div>
          <div class="phase-name">PDF Ingestion & Parsing</div>
          <div class="phase-detail">Upload pipeline, text extraction, metadata parsing (authors, title, abstract, references). Chunk strategy definition.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot active-phase"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 03 — IN PROGRESS</div>
          <div class="phase-name">Embedding Generation</div>
          <div class="phase-detail">Encode chunks with a sentence transformer. Store vectors in Qdrant with paper + user metadata as payload.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 04</div>
          <div class="phase-name">Semantic Search</div>
          <div class="phase-detail">ANN search over Qdrant. Re-ranking with cross-encoder. Expose via POST /search with filters and pagination.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 05</div>
          <div class="phase-name">Paper Summarization</div>
          <div class="phase-detail">LLM-powered multi-level summaries (abstract, section, full). ROUGE evaluation. Hallucination flagging baseline.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 06</div>
          <div class="phase-name">Knowledge Graph Construction</div>
          <div class="phase-detail">Neo4j entity extraction pipeline. Link Papers → Authors → Methods → Datasets → Concepts. Expose via GET /knowledge-graph.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 07</div>
          <div class="phase-name">Research Gap Discovery</div>
          <div class="phase-detail">Cluster analysis + LLM reasoning over graph topology. Detect contradictions, sparse nodes, missing benchmarks. Output project ideas.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 08</div>
          <div class="phase-name">Verification Engine</div>
          <div class="phase-detail">Cross-reference AI outputs against source chunks. Claim-level hallucination detection with citation mapping.</div>
        </div>
      </div>
      <div class="phase-item">
        <div class="phase-left"><div class="phase-dot"></div></div>
        <div class="phase-right">
          <div class="phase-num">PHASE 09</div>
          <div class="phase-name">Deployment & Optimization</div>
          <div class="phase-detail">Dockerize all services. CI/CD pipeline. Load testing. Latency tuning. Prometheus + Grafana dashboards.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── STRUCTURE ── -->
  <section class="section" id="structure">
    <p class="section-title">Repository Structure</p>
    <p class="section-desc">Monorepo layout: OmniTwin-AI on GitHub with feature branch workflow.</p>

    <div class="grid-2">
      <div>
        <span class="label">Folder Layout</span>
        <div class="code-block">
          <div class="tree">
            <span class="root">omnitwin/</span><br>
            ├── <span class="dir">backend/</span>         <span class="cmt">  # FastAPI app</span><br>
            │&nbsp;&nbsp; ├── <span class="dir">api/</span>         <span class="cmt">  # Route handlers</span><br>
            │&nbsp;&nbsp; ├── <span class="dir">models/</span>      <span class="cmt">  # Pydantic schemas</span><br>
            │&nbsp;&nbsp; └── <span class="dir">services/</span>    <span class="cmt">  # Business logic</span><br>
            ├── <span class="dir">frontend/</span>        <span class="cmt">  # Next.js app</span><br>
            ├── <span class="dir">agents/</span>          <span class="cmt">  # LLM agent logic</span><br>
            ├── <span class="dir">knowledge_graph/</span> <span class="cmt">  # Neo4j pipelines</span><br>
            ├── <span class="dir">rag/</span>             <span class="cmt">  # Retrieval logic</span><br>
            ├── <span class="dir">evaluation/</span>      <span class="cmt">  # Metrics + evals</span><br>
            ├── <span class="dir">deployment/</span>      <span class="cmt">  # Docker, CI/CD</span><br>
            ├── <span class="dir">research/</span>        <span class="cmt">  # Notes, papers</span><br>
            ├── <span class="dir">docs/</span>            <span class="cmt">  # Documentation</span><br>
            └── <span class="dir">tests/</span>           <span class="cmt">  # All test suites</span>
          </div>
        </div>
      </div>
      <div>
        <span class="label">Branch Strategy</span>
        <div class="code-block" style="margin-bottom: 16px;">
          <span class="kw">main</span>           <span class="cmt"># Production-stable</span><br>
          <span class="purple">development</span>    <span class="cmt"># Integration branch</span><br>
          <span class="str">feature/auth</span>   <span class="cmt"># Feature branches</span><br>
          <span class="str">feature/rag</span><br>
          <span class="str">feature/graph</span>
        </div>
        <span class="label">Frontend Pages</span>
        <div class="gap-y-16">
          <div class="code-block" style="padding: 12px 16px; line-height: 1.8;">
            <span class="kw">/dashboard</span>          Dashboard<br>
            <span class="kw">/upload</span>             Upload Papers<br>
            <span class="kw">/explore</span>            Paper Explorer<br>
            <span class="kw">/graph</span>              Knowledge Graph View<br>
            <span class="kw">/gaps</span>               Research Gap Explorer<br>
            <span class="kw">/recommendations</span>    Learning Recommendations<br>
            <span class="kw">/settings</span>           Settings
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── APIs ── -->
  <section class="section" id="apis">
    <p class="section-title">Backend APIs</p>
    <p class="section-desc">RESTful FastAPI endpoints. All routes return JSON. Authentication via Bearer token.</p>

    <div style="overflow-x: auto;">
      <table class="api-table">
        <thead>
          <tr>
            <th>Method</th>
            <th>Endpoint</th>
            <th>Description</th>
            <th>Phase</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="method method-post">POST</span></td>
            <td class="endpoint">/upload-paper</td>
            <td>Ingest a PDF, extract text, generate chunks and embeddings</td>
            <td>Ph. 2–3</td>
          </tr>
          <tr>
            <td><span class="method method-get">GET</span></td>
            <td class="endpoint">/papers</td>
            <td>List all papers for the authenticated user with filters</td>
            <td>Ph. 2</td>
          </tr>
          <tr>
            <td><span class="method method-post">POST</span></td>
            <td class="endpoint">/summarize</td>
            <td>Generate multi-level summary of a paper via LLM</td>
            <td>Ph. 5</td>
          </tr>
          <tr>
            <td><span class="method method-post">POST</span></td>
            <td class="endpoint">/search</td>
            <td>Semantic search over Qdrant with re-ranking</td>
            <td>Ph. 4</td>
          </tr>
          <tr>
            <td><span class="method method-get">GET</span></td>
            <td class="endpoint">/knowledge-graph</td>
            <td>Return graph nodes and edges for visualization</td>
            <td>Ph. 6</td>
          </tr>
          <tr>
            <td><span class="method method-post">POST</span></td>
            <td class="endpoint">/compare-papers</td>
            <td>Structured comparison of two papers across key dimensions</td>
            <td>Ph. 5</td>
          </tr>
          <tr>
            <td><span class="method method-post">POST</span></td>
            <td class="endpoint">/discover-gaps</td>
            <td>Run gap discovery over user's corpus, return project ideas</td>
            <td>Ph. 7</td>
          </tr>
          <tr>
            <td><span class="method method-get">GET</span></td>
            <td class="endpoint">/recommendations</td>
            <td>Personalized paper recommendations from User Twin model</td>
            <td>Ph. 8</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <!-- ── DATABASE ── -->
  <section class="section" id="database">
    <p class="section-title">Database Design</p>
    <p class="section-desc">Three-database architecture: relational for state, vector for semantics, graph for relationships.</p>

    <div class="grid-3">
      <div>
        <span class="label">PostgreSQL — Relational</span>
        <div class="gap-y-16">
          <div class="schema-table">
            <div class="schema-header">Users</div>
            <div class="schema-row"><span class="field-name">id</span><span class="field-type">UUID</span><span class="field-pk">PK</span></div>
            <div class="schema-row"><span class="field-name">email</span><span class="field-type">VARCHAR</span></div>
            <div class="schema-row"><span class="field-name">created_at</span><span class="field-type">TIMESTAMP</span></div>
            <div class="schema-row"><span class="field-name">interests</span><span class="field-type">JSONB</span></div>
          </div>
          <div class="schema-table">
            <div class="schema-header">Papers</div>
            <div class="schema-row"><span class="field-name">id</span><span class="field-type">UUID</span><span class="field-pk">PK</span></div>
            <div class="schema-row"><span class="field-name">user_id</span><span class="field-type">UUID FK</span></div>
            <div class="schema-row"><span class="field-name">title</span><span class="field-type">TEXT</span></div>
            <div class="schema-row"><span class="field-name">authors</span><span class="field-type">JSONB</span></div>
            <div class="schema-row"><span class="field-name">file_path</span><span class="field-type">TEXT</span></div>
          </div>
          <div class="schema-table">
            <div class="schema-header">Sessions</div>
            <div class="schema-row"><span class="field-name">token</span><span class="field-type">TEXT</span><span class="field-pk">PK</span></div>
            <div class="schema-row"><span class="field-name">user_id</span><span class="field-type">UUID FK</span></div>
            <div class="schema-row"><span class="field-name">expires_at</span><span class="field-type">TIMESTAMP</span></div>
          </div>
        </div>
      </div>

      <div>
        <span class="label">Neo4j — Graph</span>
        <div class="code-block" style="height: fit-content; line-height: 2.2;">
          <span class="cmt">// Node types</span><br>
          (<span class="kw">:Paper</span>)<br>
          (<span class="kw">:Author</span>)<br>
          (<span class="kw">:Method</span>)<br>
          (<span class="kw">:Dataset</span>)<br>
          (<span class="kw">:Concept</span>)<br>
          <br>
          <span class="cmt">// Relationship types</span><br>
          [:CITES]<br>
          [:AUTHORED_BY]<br>
          [:USES_METHOD]<br>
          [:USES_DATASET]<br>
          [:RELATED_TO]<br>
          [:EVALUATED_ON]
        </div>
      </div>

      <div>
        <span class="label">Qdrant — Vector</span>
        <div class="schema-table" style="margin-bottom: 12px;">
          <div class="schema-header">paper_embeddings</div>
          <div class="schema-row"><span class="field-name">id</span><span class="field-type">UUID</span></div>
          <div class="schema-row"><span class="field-name">vector</span><span class="field-type">float[768]</span></div>
          <div class="schema-row"><span class="field-name">paper_id</span><span class="field-type">payload</span></div>
          <div class="schema-row"><span class="field-name">chunk_text</span><span class="field-type">payload</span></div>
          <div class="schema-row"><span class="field-name">user_id</span><span class="field-type">payload</span></div>
        </div>
        <div class="schema-table">
          <div class="schema-header">user_notes_embeddings</div>
          <div class="schema-row"><span class="field-name">id</span><span class="field-type">UUID</span></div>
          <div class="schema-row"><span class="field-name">vector</span><span class="field-type">float[768]</span></div>
          <div class="schema-row"><span class="field-name">note_text</span><span class="field-type">payload</span></div>
          <div class="schema-row"><span class="field-name">user_id</span><span class="field-type">payload</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── GRAPH ── -->
  <section class="section" id="graph">
    <p class="section-title">Knowledge Graph Strategy</p>
    <p class="section-desc">Neo4j-powered graph connecting research entities. Traversals power gap discovery and recommendations.</p>

    <span class="label">Graph Relationships</span>
    <div class="rel-list">
      <div class="rel-item">
        <div class="rel-node">:Paper</div>
        <div class="rel-edge">CITES</div>
        <div class="rel-node">:Paper</div>
      </div>
      <div class="rel-item">
        <div class="rel-node">:Paper</div>
        <div class="rel-edge">USES_DATASET</div>
        <div class="rel-node">:Dataset</div>
      </div>
      <div class="rel-item">
        <div class="rel-node">:Author</div>
        <div class="rel-edge">AUTHORED_BY</div>
        <div class="rel-node">:Paper</div>
      </div>
      <div class="rel-item">
        <div class="rel-node">:Method</div>
        <div class="rel-edge">EVALUATED_ON</div>
        <div class="rel-node">:Dataset</div>
      </div>
      <div class="rel-item">
        <div class="rel-node">:Concept</div>
        <div class="rel-edge">RELATED_TO</div>
        <div class="rel-node">:Concept</div>
      </div>
    </div>

    <hr class="divider">
    <span class="label">Gap Detection Signals</span>
    <div class="grid-2">
      <div class="card card-yellow">
        <div class="card-title">What to Detect</div>
        <div class="card-body">
          Contradictory findings between papers<br>
          Underexplored method × dataset combinations<br>
          Missing benchmark comparisons<br>
          Emerging concepts with sparse citation density<br>
          Methods used in domain A but not domain B
        </div>
      </div>
      <div class="card card-accent">
        <div class="card-title">What to Output</div>
        <div class="card-body">
          Ranked list of research opportunity hypotheses<br>
          Supporting evidence from graph traversal<br>
          Suggested experimental design<br>
          Related papers and baselines to compare against<br>
          Confidence score based on graph topology
        </div>
      </div>
    </div>

    <hr class="divider">
    <span class="label">Example Cypher — Find Gaps</span>
    <div class="code-block">
      <span class="cmt">// Methods used in NLP but not applied to medical domain</span><br>
      <span class="kw">MATCH</span> (m:Method)-[:USED_IN]->(p:Paper)-[:TAGGED]->(d:Domain {name: <span class="str">'NLP'</span>})<br>
      <span class="kw">WHERE NOT</span> (m)-[:USED_IN]->(:Paper)-[:TAGGED]->(:Domain {name: <span class="str">'Medical'</span>})<br>
      <span class="kw">RETURN</span> m.name, <span class="purple">count</span>(p) <span class="kw">AS</span> usage<br>
      <span class="kw">ORDER BY</span> usage <span class="kw">DESC LIMIT</span> <span class="str">20</span>
    </div>
  </section>

  <!-- ── METRICS ── -->
  <section class="section" id="metrics">
    <p class="section-title">Evaluation Metrics</p>
    <p class="section-desc">Quantitative and qualitative measures across all platform layers.</p>

    <div class="grid-auto" style="margin-bottom: 32px;">
      <div class="metric-card">
        <div class="metric-value">P@K</div>
        <div class="metric-label">Search Precision</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" style="color: var(--accent2);">R@K</div>
        <div class="metric-label">Search Recall</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" style="color: var(--accent4);">ROUGE</div>
        <div class="metric-label">Summarization</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" style="color: var(--accent3);">CTR</div>
        <div class="metric-label">Recommendation</div>
      </div>
      <div class="metric-card">
        <div class="metric-value">&lt;200ms</div>
        <div class="metric-label">Search Latency</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" style="color: var(--accent2);">99.9%</div>
        <div class="metric-label">Uptime Target</div>
      </div>
    </div>

    <span class="label">Testing Strategy</span>
    <div class="grid-2">
      <div class="code-block">
        <div class="code-label">Test Layers</div>
        <span class="kw">Unit Tests</span>       — Core logic, models, utilities<br>
        <span class="purple">Integration Tests</span> — API contracts, DB interactions<br>
        <span class="str">End-to-End Tests</span>  — Full user workflows (Playwright)<br>
        <span class="red">Load Tests</span>        — Search endpoints (Locust / k6)
      </div>
      <div class="code-block">
        <div class="code-label">Eval Cadence</div>
        <span class="kw">On PR merge</span>      → Unit + Integration<br>
        <span class="purple">Weekly</span>          → E2E + Regression suite<br>
        <span class="str">Pre-release</span>      → Full load test run<br>
        <span class="red">Monthly</span>          → Human eval on summaries
      </div>
    </div>
  </section>

  <!-- ── WORKFLOW ── -->
  <section class="section" id="workflow">
    <p class="section-title">GitHub Workflow</p>
    <p class="section-desc">Issue-driven development with feature branches, code review, and tagged releases.</p>

    <span class="label">Contribution Cycle</span>
    <div class="workflow" style="margin-bottom: 32px;">
      <div class="wf-step">
        <div class="wf-num">01</div>
        <div class="wf-label">Create Issue with acceptance criteria</div>
      </div>
      <div class="wf-step">
        <div class="wf-num">02</div>
        <div class="wf-label">Cut feature/ branch from development</div>
      </div>
      <div class="wf-step">
        <div class="wf-num">03</div>
        <div class="wf-label">Commit frequently with clear messages</div>
      </div>
      <div class="wf-step">
        <div class="wf-num">04</div>
        <div class="wf-label">Open pull request, link issue</div>
      </div>
      <div class="wf-step">
        <div class="wf-num">05</div>
        <div class="wf-label">Review, CI checks pass, merge</div>
      </div>
      <div class="wf-step">
        <div class="wf-num">06</div>
        <div class="wf-label">Tag release with changelog</div>
      </div>
    </div>

    <span class="label">Deployment Strategy</span>
    <div class="grid-2">
      <div class="code-block">
        <div class="code-label">docker-compose.yml (dev)</div>
        <span class="kw">services</span>:<br>
        &nbsp;&nbsp;<span class="purple">backend</span>:<br>
        &nbsp;&nbsp;&nbsp;&nbsp;build: ./backend<br>
        &nbsp;&nbsp;&nbsp;&nbsp;ports: [<span class="str">"8000:8000"</span>]<br>
        &nbsp;&nbsp;<span class="purple">frontend</span>:<br>
        &nbsp;&nbsp;&nbsp;&nbsp;build: ./frontend<br>
        &nbsp;&nbsp;&nbsp;&nbsp;ports: [<span class="str">"3000:3000"</span>]<br>
        &nbsp;&nbsp;<span class="kw">postgres</span>:<br>
        &nbsp;&nbsp;&nbsp;&nbsp;image: postgres:15<br>
        &nbsp;&nbsp;<span class="kw">qdrant</span>:<br>
        &nbsp;&nbsp;&nbsp;&nbsp;image: qdrant/qdrant<br>
        &nbsp;&nbsp;<span class="kw">neo4j</span>:<br>
        &nbsp;&nbsp;&nbsp;&nbsp;image: neo4j:5
      </div>
      <div class="code-block">
        <div class="code-label">Secret Management</div>
        <span class="cmt"># Never commit secrets to git</span><br>
        <span class="kw">DATABASE_URL</span>=<span class="str">postgres://...</span><br>
        <span class="kw">QDRANT_API_KEY</span>=<span class="str">...</span><br>
        <span class="kw">NEO4J_PASSWORD</span>=<span class="str">...</span><br>
        <span class="kw">OPENAI_API_KEY</span>=<span class="str">...</span><br>
        <span class="kw">JWT_SECRET</span>=<span class="str">...</span><br>
        <br>
        <span class="cmt"># Use .env.local in dev</span><br>
        <span class="cmt"># Use cloud secrets manager in prod</span>
      </div>
    </div>

    <hr class="divider">
    <div class="callout">
      <strong>Final Advice:</strong> Treat OmniTwin as a product, not merely a project. Ship small versions regularly. Document everything. Use GitHub consistently. Build publicly and iterate — the compounding effect of consistent, public progress is the fastest path to a flagship platform.
    </div>
  </section>

  <footer>
    <div class="footer-left">
      <span class="pulse"></span>
      OmniTwin AI — Master Blueprint v1.0
    </div>
    <div class="footer-right">
      Repository: <strong>OmniTwin-AI</strong><br>
      9 Phases · 6 Modules · 3 Databases
    </div>
  </footer>
</div>

<script>
  function show(id) {
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    event.target.classList.add('active');
  }

  // Animate progress bars on load
  window.addEventListener('load', () => {
    setTimeout(() => {
      document.querySelectorAll('.progress-fill').forEach(bar => {
        const w = bar.style.width;
        bar.style.width = '0';
        requestAnimationFrame(() => {
          setTimeout(() => bar.style.width = w, 100);
        });
      });
    }, 300);
  });
</script>
</body>
</html>
