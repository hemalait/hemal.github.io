<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Hemal Patel — Engineering Manager building global regulatory and customs compliance platforms.">
<title>Hemal Patel | Engineering Manager</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/topojson-client@3/dist/topojson-client.min.js"></script>
<style>
  :root{
    --bg:#0E141D;
    --panel:#161F2B;
    --panel-2:#1C2634;
    --border:#28323F;
    --ink:#EDF1F7;
    --ink-muted:#8493A5;
    --amber:#E2A33B;
    --amber-dim:#7A5A25;
    --teal:#46B8A6;
    --teal-dim:#245A52;
    --rust:#E0785A;
    --rust-dim:#6B3524;
    --planned:#7C93C4;
    --planned-dim:#2C3A55;
    --radius:10px;
    --max:1120px;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--ink);
    font-family:'Inter', sans-serif;
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  a{color:inherit;}
  .wrap{max-width:var(--max); margin:0 auto; padding:0 32px;}
  .eyebrow{
    font-family:'IBM Plex Mono', monospace;
    font-size:12px;
    letter-spacing:.14em;
    text-transform:uppercase;
    color:var(--amber);
  }
  h1,h2,h3{font-family:'Space Grotesk', sans-serif; font-weight:600; letter-spacing:-.01em;}
  ::selection{background:var(--amber); color:#1a1204;}
  :focus-visible{outline:2px solid var(--teal); outline-offset:3px;}

  /* NAV */
  header{
    position:fixed; top:0; left:0; right:0; z-index:50;
    background:rgba(14,20,29,.85);
    backdrop-filter:blur(8px);
    border-bottom:1px solid var(--border);
  }
  nav.wrap{
    display:flex; align-items:center; justify-content:space-between;
    height:64px;
  }
  .logo{font-family:'IBM Plex Mono', monospace; font-size:14px; font-weight:500; letter-spacing:.05em;}
  .logo span{color:var(--amber);}
  .navlinks{display:flex; gap:28px; list-style:none;}
  .navlinks a{
    font-family:'IBM Plex Mono', monospace;
    font-size:12px; letter-spacing:.08em; text-transform:uppercase;
    color:var(--ink-muted);
    text-decoration:none;
    transition:color .15s;
  }
  .navlinks a:hover{color:var(--ink);}
  .navtoggle{display:none; background:none; border:1px solid var(--border); color:var(--ink); width:38px; height:38px; border-radius:8px; font-size:18px; cursor:pointer;}

  /* HERO */
  .hero{
    position:relative;
    padding:168px 0 96px;
    overflow:hidden;
    border-bottom:1px solid var(--border);
  }
  .hero-grid{
    display:grid;
    grid-template-columns:1.15fr .85fr;
    gap:48px;
    align-items:center;
    position:relative;
    z-index:2;
  }
  .hero h1{
    font-size:clamp(40px, 5.4vw, 68px);
    line-height:1.02;
    margin:14px 0 18px;
  }
  .hero .role{
    font-size:clamp(17px, 2vw, 21px);
    color:var(--ink-muted);
    font-weight:500;
    margin-bottom:20px;
  }
  .hero .role strong{color:var(--teal); font-weight:500;}
  .hero p.lead{
    font-size:16px;
    color:var(--ink-muted);
    max-width:56ch;
    margin-bottom:32px;
  }
  .cta-row{display:flex; gap:14px; flex-wrap:wrap;}
  .btn{
    display:inline-flex; align-items:center; gap:8px;
    font-family:'IBM Plex Mono', monospace;
    font-size:13px; letter-spacing:.03em;
    padding:13px 20px;
    border-radius:8px;
    text-decoration:none;
    border:1px solid var(--border);
    transition:border-color .15s, background .15s, transform .1s;
  }
  .btn:active{transform:scale(.98);}
  .btn-primary{background:var(--amber); color:#1a1204; border-color:var(--amber); font-weight:500;}
  .btn-primary:hover{background:#eeb559;}
  .btn-ghost{color:var(--ink); }
  .btn-ghost:hover{border-color:var(--teal); color:var(--teal);}

  /* route map */
  .routemap{
    position:relative;
    aspect-ratio:1/1;
    max-width:420px;
    margin:0 auto;
  }
  .routemap svg{width:100%; height:100%;}
  .route-line{
    fill:none; stroke:var(--teal); stroke-width:1.4; opacity:.55;
    stroke-dasharray:5 6;
    animation:dash 22s linear infinite;
  }
  @keyframes dash{to{stroke-dashoffset:-500;}}
  .hub{fill:var(--amber);}
  .hub-ring{fill:none; stroke:var(--amber); stroke-width:1; opacity:.5;}
  .hub-label{
    font-family:'IBM Plex Mono', monospace; font-size:9px; fill:var(--ink-muted); letter-spacing:.05em;
  }

  /* STATS STRIP */
  .stats{
    border-bottom:1px solid var(--border);
    background:var(--panel);
  }
  .stats-row{
    display:grid;
    grid-template-columns:repeat(4, 1fr);
  }
  .stat{
    padding:28px 20px;
    text-align:center;
    border-left:1px solid var(--border);
  }
  .stat:first-child{border-left:none;}
  .stat .num{
    font-family:'Space Grotesk', sans-serif;
    font-size:clamp(24px, 3vw, 32px);
    font-weight:700;
    color:var(--teal);
  }
  .stat .lbl{
    font-family:'IBM Plex Mono', monospace;
    font-size:11px; letter-spacing:.08em; text-transform:uppercase;
    color:var(--ink-muted);
    margin-top:6px;
  }

  section{padding:88px 0;}
  .section-head{margin-bottom:44px;}
  .section-head h2{font-size:clamp(26px,3vw,34px); margin-top:8px;}

  /* MANIFEST TICKER (signature) */
  .manifest{
    border-top:1px solid var(--border);
    border-bottom:1px solid var(--border);
    background:var(--panel);
    padding:0;
    overflow:hidden;
  }
  .manifest-label{
    font-family:'IBM Plex Mono', monospace;
    font-size:11px; letter-spacing:.1em; text-transform:uppercase;
    color:var(--ink-muted);
    padding:14px 32px 0;
    max-width:var(--max); margin:0 auto;
  }
  .ticker-track{
    display:flex;
    width:max-content;
    padding:16px 0 22px;
    animation:scroll-left 42s linear infinite;
  }
  @media (prefers-reduced-motion: reduce){
    .ticker-track{animation:none; overflow-x:auto;}
    .route-line{animation:none;}
  }
  @keyframes scroll-left{
    from{transform:translateX(0);}
    to{transform:translateX(-50%);}
  }
  .filing{
    display:flex; align-items:center; gap:12px;
    font-family:'IBM Plex Mono', monospace;
    font-size:13px;
    padding:10px 22px;
    border-right:1px solid var(--border);
    white-space:nowrap;
  }
  .filing .dot{width:6px; height:6px; border-radius:50%; background:var(--teal); flex-shrink:0;}
  .filing .code{color:var(--amber); font-weight:500;}
  .filing .desc{color:var(--ink-muted);}

  /* EXPERIENCE TIMELINE */
  .timeline{position:relative; padding-left:28px; border-left:1px solid var(--border);}
  .tl-item{position:relative; padding-bottom:44px;}
  .tl-item:last-child{padding-bottom:0;}
  .tl-item::before{
    content:'';
    position:absolute; left:-33px; top:4px;
    width:9px; height:9px; border-radius:50%;
    background:var(--bg); border:2px solid var(--amber);
  }
  .tl-date{
    font-family:'IBM Plex Mono', monospace;
    font-size:12px; color:var(--teal); letter-spacing:.04em;
    margin-bottom:4px;
  }
  .tl-role{font-size:19px; font-weight:600; font-family:'Space Grotesk', sans-serif;}
  .tl-org{font-size:14px; color:var(--ink-muted); margin-bottom:10px;}
  .tl-item ul{list-style:none; display:flex; flex-direction:column; gap:6px;}
  .tl-item li{
    font-size:14.5px; color:#C3CDD9;
    padding-left:16px; position:relative;
  }
  .tl-item li::before{
    content:'▸'; position:absolute; left:0; color:var(--amber); font-size:12px; top:2px;
  }

  /* EXPERTISE GRID */
  .grid-cards{
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    gap:1px;
    background:var(--border);
    border:1px solid var(--border);
    border-radius:var(--radius);
    overflow:hidden;
  }
  .card{
    background:var(--panel);
    padding:26px 24px;
  }
  .card .icon-code{
    font-family:'IBM Plex Mono', monospace;
    font-size:11px; color:var(--amber); letter-spacing:.08em;
  }
  .card h3{font-size:16px; margin:10px 0 10px;}
  .card p{font-size:13.5px; color:var(--ink-muted); line-height:1.65;}

  /* EDUCATION / CERT */
  .split{display:grid; grid-template-columns:1fr 1fr; gap:1px; background:var(--border); border:1px solid var(--border); border-radius:var(--radius); overflow:hidden;}
  .split-cell{background:var(--panel); padding:26px;}
  .split-cell .tag{font-family:'IBM Plex Mono',monospace; font-size:11px; color:var(--teal); letter-spacing:.08em; text-transform:uppercase;}
  .split-cell h3{font-size:16px; margin:8px 0 4px;}
  .split-cell p{font-size:13.5px; color:var(--ink-muted);}

  /* CONTACT / FOOTER */
  footer{
    border-top:1px solid var(--border);
    padding:80px 0 40px;
    text-align:center;
  }
  footer .eyebrow{display:block; margin-bottom:14px;}
  footer h2{font-size:clamp(28px,4vw,42px); margin-bottom:18px;}
  footer p{color:var(--ink-muted); max-width:52ch; margin:0 auto 34px;}
  .contact-row{display:flex; justify-content:center; gap:14px; flex-wrap:wrap; margin-bottom:56px;}
  .foot-meta{
    font-family:'IBM Plex Mono', monospace;
    font-size:12px; color:var(--ink-muted);
    display:flex; justify-content:center; gap:24px; flex-wrap:wrap;
  }

  /* TRADE LANES WORLD MAP */
  #tradelanes{border-bottom:1px solid var(--border); background:var(--panel);}
  .map-intro{max-width:64ch; color:var(--ink-muted); font-size:14.5px; margin-bottom:8px;}
  .map-frame{
    position:relative;
    background:var(--bg);
    border:1px solid var(--border);
    border-radius:var(--radius);
    padding:18px 18px 8px;
    margin-top:28px;
  }
  .map-frame svg{width:100%; height:auto; display:block;}
  .map-loading{
    font-family:'IBM Plex Mono', monospace; font-size:12px; color:var(--ink-muted);
    text-align:center; padding:60px 0;
  }
  .sphere{fill:var(--panel-2); stroke:var(--border); stroke-width:1;}
  .graticule{fill:none; stroke:var(--border); stroke-width:.5; opacity:.5;}
  .country{fill:var(--panel-2); stroke:#0E141D; stroke-width:.4;}
  .country.eu29{fill:var(--teal-dim); stroke:var(--teal); stroke-width:.5; opacity:.85;}
  .country.node-country{fill:var(--amber-dim); stroke:var(--amber); stroke-width:.5; opacity:.8;}
  .flow-line{fill:none; stroke-linecap:round;}
  .flow-line.mode-air{stroke-width:1.3;}
  .flow-line.mode-truck{stroke-width:1.3; stroke-dasharray:1 4;}
  .flow-anim{stroke-dasharray:3 5; animation:dashmove 30s linear infinite;}
  @keyframes dashmove{to{stroke-dashoffset:-600;}}
  .flow-line.planned{stroke-dasharray:2 3; opacity:.6; animation:pulseplan 2.6s ease-in-out infinite;}
  .flow-line.planned.mode-truck{stroke-dasharray:1 3.5;}
  @keyframes pulseplan{0%,100%{opacity:.35;} 50%{opacity:.75;}}
  .map-node circle{stroke:#0B0F17; stroke-width:1;}
  .map-node.hub circle{r:4.5;}
  .map-node text{
    font-family:'IBM Plex Mono', monospace; font-size:8.5px; fill:var(--ink-muted);
    letter-spacing:.02em;
  }
  .map-node.hub text{fill:var(--ink); font-weight:500;}
  .acas-halo{fill:none; stroke:var(--planned); stroke-width:1; opacity:.5; animation:halopulse 2.6s ease-in-out infinite;}
  @keyframes halopulse{0%{r:8; opacity:.55;} 100%{r:20; opacity:0;}}
  .soon-badge{
    display:inline-block; font-size:9px; letter-spacing:.06em; font-weight:600;
    color:var(--planned); border:1px solid var(--planned); border-radius:20px;
    padding:1px 7px; margin-left:6px; vertical-align:1px;
  }
  .map-legend{
    display:flex; flex-wrap:wrap; gap:20px;
    padding:16px 4px 6px;
    font-family:'IBM Plex Mono', monospace; font-size:11.5px; color:var(--ink-muted);
  }
  .map-legend.planned-legend{padding-top:2px; padding-bottom:20px; border-top:1px dashed var(--border); margin-top:6px;}
  .map-legend .lg-item{display:flex; align-items:center; gap:8px;}
  .map-legend svg{width:28px; height:10px; flex-shrink:0;}
  .map-legend .swatch-fill{width:12px; height:12px; border-radius:2px; flex-shrink:0; display:inline-block;}
  .legend-heading{
    width:100%; font-size:10.5px; letter-spacing:.1em; text-transform:uppercase;
    color:var(--planned); margin-bottom:2px;
  }

  @media (max-width:860px){
    .hero-grid{grid-template-columns:1fr;}
    .routemap{order:-1; max-width:280px;}
    .stats-row{grid-template-columns:repeat(2,1fr);}
    .stat:nth-child(3){border-left:none;}
    .stat{border-bottom:1px solid var(--border);}
    .grid-cards{grid-template-columns:1fr;}
    .split{grid-template-columns:1fr;}
    .navlinks{display:none;}
  }
</style>
</head>
<body>

<header>
  <nav class="wrap">
    <div class="logo">HP<span>/</span>ENGINEERING</div>
    <ul class="navlinks">
      <li><a href="#overview">Overview</a></li>
      <li><a href="#tradelanes">Trade Lanes</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#expertise">Expertise</a></li>
      <li><a href="#manifest">Manifest</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>
</header>

<main>
  <section class="hero" id="overview">
    <div class="wrap hero-grid">
      <div>
        <p class="eyebrow">ENGINEERING LEADERSHIP — REGULATORY &amp; TRADE SYSTEMS</p>
        <h1>Hemal Patel</h1>
        <p class="role">Manager, Software Engineering — <strong>building the platforms that move global trade compliantly</strong></p>
        <p class="lead">14+ years architecting and leading enterprise systems that keep cross-border commerce moving — from cargo screening to customs filings — for one of the world's largest logistics networks. Currently focused on cloud-native modernization and AI-driven engineering transformation.</p>
        <div class="cta-row">
          <a class="btn btn-primary" href="mailto:hemalpatel@ups.com">Email me</a>
          <a class="btn btn-ghost" href="https://www.linkedin.com/in/thehemal" target="_blank" rel="noopener">LinkedIn ↗</a>
          <a class="btn btn-ghost" href="#experience">View experience</a>
        </div>
      </div>
      <div class="routemap" aria-hidden="true">
        <svg viewBox="0 0 400 400">
          <path class="route-line" d="M 200 200 Q 140 100 90 70" />
          <path class="route-line" d="M 200 200 Q 260 120 310 90" style="animation-delay:-4s" />
          <path class="route-line" d="M 200 200 Q 120 260 80 320" style="animation-delay:-9s" />
          <path class="route-line" d="M 200 200 Q 280 250 330 310" style="animation-delay:-13s" />
          <path class="route-line" d="M 200 200 Q 200 120 200 40" style="animation-delay:-17s" />

          <circle class="hub-ring" cx="200" cy="200" r="26"/>
          <circle class="hub" cx="200" cy="200" r="5"/>
          <text class="hub-label" x="210" y="204">UPS HUB</text>

          <circle class="hub" cx="90" cy="70" r="3.5"/>
          <text class="hub-label" x="60" y="58">EU · ICS2</text>

          <circle class="hub" cx="310" cy="90" r="3.5"/>
          <text class="hub-label" x="290" y="78">UK · PreDICT</text>

          <circle class="hub" cx="80" cy="320" r="3.5"/>
          <text class="hub-label" x="50" y="340">CA · PACT</text>

          <circle class="hub" cx="330" cy="310" r="3.5"/>
          <text class="hub-label" x="305" y="330">MX · SAT</text>

          <circle class="hub" cx="200" cy="40" r="3.5"/>
          <text class="hub-label" x="170" y="28">US · CBP</text>
        </svg>
      </div>
    </div>
  </section>

  <div class="stats">
    <div class="wrap stats-row">
      <div class="stat"><div class="num">2</div><div class="lbl">Teams led</div></div>
      <div class="stat"><div class="num">25+</div><div class="lbl">Engineers &amp; SREs</div></div>
      <div class="stat"><div class="num">−50%</div><div class="lbl">Agency onboarding time</div></div>
      <div class="stat"><div class="num">14+</div><div class="lbl">Years in enterprise eng.</div></div>
    </div>
  </div>

  <section id="tradelanes">
    <div class="wrap">
      <div class="section-head">
        <p class="eyebrow">GLOBAL FOOTPRINT</p>
        <h2>Trade lanes &amp; agency interactions</h2>
      </div>
      <p class="map-intro">A simplified map of the cross-border filing networks I've built or led — where cargo originates, which customs authority receives the filing, and by which mode. Dashed, pulsing lanes mark programs currently in build.</p>
      <div class="map-frame">
        <div class="map-loading" id="mapLoading">Loading map data…</div>
        <svg id="worldmap" viewBox="0 0 960 500" role="img" aria-label="World map showing live and upcoming cross-border cargo flows for ICS2, CA PACT, UAE, ACE Truck, CA ELVIS, and US ACAS customs networks" style="display:none;"></svg>
      </div>
      <div class="map-legend">
        <div class="lg-item"><span class="swatch-fill" style="background:var(--teal-dim); border:1px solid var(--teal);"></span> ICS2 member states (29)</div>
        <div class="lg-item"><span class="swatch-fill" style="background:var(--amber-dim); border:1px solid var(--amber);"></span> Origin / destination countries</div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--teal)" stroke-width="1.5"/></svg> ICS2 — air cargo</div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--teal)" stroke-width="1.5" stroke-dasharray="1 4"/></svg> ICS2 — truck (UK↔EU)</div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--amber)" stroke-width="1.5"/></svg> CA PACT — US→Canada air</div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--rust)" stroke-width="1.5"/></svg> UAE — import / export air volume</div>
      </div>
      <div class="map-legend planned-legend">
        <div class="legend-heading">In build — target Q4 2026</div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--planned)" stroke-width="1.5" stroke-dasharray="1 3.5"/></svg> ACE Truck — CA→US ground volume to CBP<span class="soon-badge">Q4 2026</span></div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--planned)" stroke-width="1.5" stroke-dasharray="2 3"/></svg> CA ELVIS — US→CA air, low-value shipments to CBSA<span class="soon-badge">Q4 2026</span></div>
        <div class="lg-item"><svg><line x1="0" y1="5" x2="28" y2="5" stroke="var(--planned)" stroke-width="1.5" stroke-dasharray="2 3"/></svg> US ACAS — worldwide air imports/transits to CBP<span class="soon-badge">Q4 2026</span></div>
      </div>
    </div>
  </section>

  <div class="manifest" id="manifest">
    <p class="manifest-label">Systems onboarded — regulatory filing manifest</p>
    <div class="ticker-track" id="tickerTrack">
      <!-- filled by JS, duplicated for seamless loop -->
    </div>
  </div>

  <section id="experience">
    <div class="wrap">
      <div class="section-head">
        <p class="eyebrow">CAREER</p>
        <h2>Experience</h2>
      </div>
      <div class="timeline">

        <div class="tl-item">
          <div class="tl-date">AUG 2025 — PRESENT</div>
          <div class="tl-role">Manager, Software Engineering</div>
          <div class="tl-org">UPS · Parsippany, NJ</div>
          <ul>
            <li>Lead 2 cross-functional Engineering, SRE &amp; QA teams (25+ engineers) delivering global customs and regulatory compliance platforms.</li>
            <li>Architected the next-generation Regulatory platform now used to onboard government agencies — cutting onboarding time by 50%+.</li>
            <li>Spearheading Enterprise AI Transformation — built internal AI-adoption frameworks (AIAD) that lifted team productivity org-wide.</li>
            <li>Drive cross-product architecture alignment across ICE, SURE, and ARMOR to eliminate duplication.</li>
            <li>Built succession planning and cross-training programs that reduced key-person risk across critical platforms.</li>
          </ul>
        </div>

        <div class="tl-item">
          <div class="tl-date">APR 2021 — JUL 2025</div>
          <div class="tl-role">Lead Software Development Engineer</div>
          <div class="tl-org">UPS · ICS2 (EU ACAS), Smart Border, CA PACT, UK PreDICT</div>
          <ul>
            <li>Assisted in designing UPS's next-gen Regulatory platform, the foundation for all future compliance initiatives.</li>
            <li>Led and mentored 12+ developers and 4 QAs delivering ICS2 Entry Summary Declaration compliance for all EU-bound cargo.</li>
            <li>Engineered UPS's first system to archive data to Google Cloud Platform, kick-starting Regulatory's cloud migration.</li>
            <li>Delivered CA PACT and UK PreDICT preload-filing systems, leading first-in-org OpenShift v3→v4 migration.</li>
          </ul>
        </div>

        <div class="tl-item">
          <div class="tl-date">OCT 2017 — APR 2021</div>
          <div class="tl-role">Senior Applications Developer</div>
          <div class="tl-org">UPS · US Export Screening, MIPS Reduction, IDORS Modernization</div>
          <ul>
            <li>Led architecture for the IDORS program, replacing legacy AS/400 systems across Cologne, Hong Kong, and Singapore.</li>
            <li>Migrated mainframe functionality to Open Systems, contributing to ~1,000 peak-hour MIPS in cost savings.</li>
          </ul>
        </div>

        <div class="tl-item">
          <div class="tl-date">OCT 2014 — OCT 2017</div>
          <div class="tl-role">Java Developer Consultant</div>
          <div class="tl-org">UPS · Enterprise Denied Party Screening, Regulatory SPAs</div>
          <ul>
            <li>Built a high-performance Denied Party Screening application with multi-threaded processing.</li>
            <li>Engineered SPAs enabling customs filings across CBSA, CBP, and SAT.</li>
          </ul>
        </div>

        <div class="tl-item">
          <div class="tl-date">JAN 2013 — OCT 2014</div>
          <div class="tl-role">Java Developer Consultant</div>
          <div class="tl-org">State of Maine · MACWIS</div>
          <ul>
            <li>Modernized the Maine Automated Child Welfare Information System; built a caseworker dashboard cutting lookup time 50%+.</li>
          </ul>
        </div>

      </div>
    </div>
  </section>

  <section id="expertise" style="background:var(--panel-2); border-top:1px solid var(--border); border-bottom:1px solid var(--border);">
    <div class="wrap">
      <div class="section-head">
        <p class="eyebrow">CAPABILITIES</p>
        <h2>Expertise</h2>
      </div>
      <div class="grid-cards">
        <div class="card">
          <div class="icon-code">01 · LEADERSHIP</div>
          <h3>Engineering management</h3>
          <p>Cross-functional team leadership, mentorship &amp; succession planning, OKR-driven execution, stakeholder alignment.</p>
        </div>
        <div class="card">
          <div class="icon-code">02 · AI</div>
          <h3>AI-driven engineering</h3>
          <p>AI-Assisted Development frameworks, GitHub Copilot enablement, AI-driven test automation, prompt engineering.</p>
        </div>
        <div class="card">
          <div class="icon-code">03 · ARCHITECTURE</div>
          <h3>Distributed systems</h3>
          <p>Microservices, event-driven architecture, async messaging (WMQ, AMQ, GCP Pub/Sub), domain-driven design.</p>
        </div>
        <div class="card">
          <div class="icon-code">04 · CLOUD</div>
          <h3>Cloud &amp; platform</h3>
          <p>GCP (GCS, BigQuery), Azure, OpenShift, Azure DevOps, ArgoCD, Jenkins, CI/CD pipelines.</p>
        </div>
        <div class="card">
          <div class="icon-code">05 · COMPLIANCE</div>
          <h3>Regulatory systems</h3>
          <p>EDIFACT, IATA Cargo-IMP/XML, ICS2, CBSA PACT, HMRC, cross-border customs filing infrastructure.</p>
        </div>
        <div class="card">
          <div class="icon-code">06 · DATA</div>
          <h3>Languages &amp; data</h3>
          <p>Java, JavaScript/TypeScript, SQL, PL/SQL, T-SQL, DB2, Oracle, SQL Server, data modeling &amp; performance tuning.</p>
        </div>
        <div class="card" style="grid-column:1 / -1;">
          <div class="icon-code">07 · TECH STACK</div>
          <h3>Core stack</h3>
          <p>Java, Spring Boot, J2EE, SQL Server, GCP (GCS, BigQuery), WebSphere MQ, ActiveMQ, RESTful APIs, JSON, XML, fixed-length message formats.</p>
        </div>
      </div>
    </div>
  </section>

  <section>
    <div class="wrap">
      <div class="section-head">
        <p class="eyebrow">CREDENTIALS</p>
        <h2>Education &amp; certifications</h2>
      </div>
      <div class="split">
        <div class="split-cell">
          <div class="tag">Education</div>
          <h3>M.S. Computer Science</h3>
          <p>Stevens Institute of Technology, NJ</p>
        </div>
        <div class="split-cell">
          <div class="tag">Education</div>
          <h3>B.E. Electronics &amp; Computer Engineering</h3>
          <p>Acharya Institute of Technology, India</p>
        </div>
        <div class="split-cell">
          <div class="tag">In progress</div>
          <h3>Google AI Leader Certification</h3>
          <p>Preparing for exam — target Dec 2026</p>
        </div>
        <div class="split-cell">
          <div class="tag">Certified</div>
          <h3>Oracle Certified Java SE 6 Programmer</h3>
          <p>Oracle</p>
        </div>
      </div>
    </div>
  </section>
</main>

<footer id="contact">
  <div class="wrap">
    <span class="eyebrow">GET IN TOUCH</span>
    <h2>Let's talk shop.</h2>
    <p>Open to conversations about engineering leadership, regulatory technology, and AI-driven platform transformation.</p>
    <div class="contact-row">
      <a class="btn btn-primary" href="mailto:hemalpatel@ups.com">Email me</a>
      <a class="btn btn-ghost" href="https://www.linkedin.com/in/thehemal" target="_blank" rel="noopener">Connect on LinkedIn ↗</a>
    </div>
    <div class="foot-meta">
      <span>Cliffwood, NJ</span>
      <span>·</span>
      <span>M.S. Computer Science, Stevens Institute of Technology</span>
    </div>
  </div>
</footer>

<script>
  const filings = [
    { code: 'ICS2', desc: 'EU Import Control System 2 — Entry Summary Declaration' },
    { code: 'CBSA-PACT', desc: 'Canada Pre-load Air Cargo Targeting' },
    { code: 'HMRC', desc: 'UK Presentation of Goods filing' },
    { code: 'UK-PREDICT', desc: 'UK Pre-load Data Informed Targeting' },
    { code: 'IATA-XML', desc: 'Cargo-IMP / Cargo-XML messaging' },
    { code: 'EDIFACT', desc: 'Cross-border EDI messaging standard' },
    { code: 'FR-OLE', desc: 'French Customs Obligatory Logistics Envelope' },
    { code: 'SAT-MX', desc: 'Mexico customs import filings' },
    { code: 'ACE-TRUCK', desc: 'CA→US ground volume to CBP — Q4 2026', planned: true },
    { code: 'CA-ELVIS', desc: 'US→CA air, low-value shipments to CBSA — Q4 2026', planned: true },
    { code: 'US-ACAS', desc: 'Worldwide air imports/transits to CBP — Q4 2026', planned: true },
  ];
  const track = document.getElementById('tickerTrack');
  function renderFilings(){
    let html = '';
    filings.forEach(f => {
      const dotStyle = f.planned ? ' style="background:var(--planned)"' : '';
      html += `<div class="filing"><span class="dot"${dotStyle}></span><span class="code">${f.code}</span><span class="desc">${f.desc}</span></div>`;
    });
    return html;
  }
  track.innerHTML = renderFilings() + renderFilings();

  document.querySelectorAll('.navlinks a, .cta-row a[href^="#"], footer a[href^="#"]').forEach(a=>{
    a.addEventListener('click', e=>{
      const id = a.getAttribute('href');
      if(id && id.startsWith('#')){
        const target = document.querySelector(id);
        if(target){
          e.preventDefault();
          target.scrollIntoView({behavior:'smooth', block:'start'});
        }
      }
    });
  });
</script>

<script>
(function(){
  const svgEl = document.getElementById('worldmap');
  const loadingEl = document.getElementById('mapLoading');
  if(!svgEl || typeof d3 === 'undefined'){ return; }

  const WIDTH = 960, HEIGHT = 500;
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  // ICS2 participating states (EU27 + Norway + Switzerland) — ISO 3166-1 numeric codes
  const EU29 = new Set(["040","056","100","191","196","203","208","233","246","250",
                         "276","300","348","372","380","428","440","442","470","528",
                         "616","620","642","703","705","724","752","578","756"]);
  // Non-EU countries that appear as flow origins/destinations
  const NODE_COUNTRIES = new Set(["840","784","356","156","826","124","586","410"]); // USA, UAE, India, China, UK, Canada, Pakistan, S.Korea

  const nodes = {
    USA:      { lon:-73.8, lat:40.7,  label:"USA",       hub:true,  dx:-10, dy:-6,  anchor:"end" },
    CANADA:   { lon:-79.4, lat:43.7,  label:"Canada",     hub:true,  dx:0,   dy:-12, anchor:"middle" },
    UK:       { lon:-1.5,  lat:52.3,  label:"UK",         hub:false, dx:-8,  dy:-8,  anchor:"end" },
    FRANCE:   { lon:2.35,  lat:48.85, label:"France",     hub:false, dx:8,   dy:14,  anchor:"start" },
    NIRELAND: { lon:-6.9,  lat:54.6,  label:"N. Ireland", hub:false, dx:-8,  dy:-6,  anchor:"end" },
    GERMANY:  { lon:10.45, lat:51.2,  label:"Germany",    hub:false, dx:10,  dy:-4,  anchor:"start" },
    EU:       { lon:4.9,   lat:47.5,  label:"EU · ICS2",  hub:true,  dx:0,   dy:16,  anchor:"middle" },
    INDIA:    { lon:78.9,  lat:22.6,  label:"India",      hub:false, dx:8,   dy:14,  anchor:"start" },
    CHINA:    { lon:104.2, lat:35.9,  label:"China",      hub:false, dx:8,   dy:-8,  anchor:"start" },
    PAKISTAN: { lon:69.3,  lat:30.4,  label:"Pakistan",   hub:false, dx:-8,  dy:14,  anchor:"end" },
    SKOREA:   { lon:127.8, lat:36.5,  label:"S. Korea",   hub:false, dx:10,  dy:-6,  anchor:"start" },
    UAE:      { lon:54.0,  lat:24.0,  label:"UAE",        hub:true,  dx:0,   dy:16,  anchor:"middle" }
  };

  const flows = [
    // ICS2 — air cargo into the EU (teal, solid)
    { from:"USA",  to:"EU", color:"var(--teal)", mode:"air",  side:1 },
    { from:"UAE",  to:"EU", color:"var(--teal)", mode:"air",  side:1 },
    { from:"INDIA",to:"EU", color:"var(--teal)", mode:"air",  side:1 },
    { from:"CHINA",to:"EU", color:"var(--teal)", mode:"air",  side:1 },
    // ICS2 — truck into the EU (teal, dashed)
    { from:"UK", to:"FRANCE",   color:"var(--teal)", mode:"truck", side:1 },
    { from:"UK", to:"NIRELAND", color:"var(--teal)", mode:"truck", side:-1 },
    // CA PACT — US to Canada air (amber, solid)
    { from:"USA", to:"CANADA", color:"var(--amber)", mode:"air", side:1 },
    // UAE — air imports (rust, solid)
    { from:"GERMANY",  to:"UAE", color:"var(--rust)", mode:"air", side:1 },
    { from:"INDIA",     to:"UAE", color:"var(--rust)", mode:"air", side:-1 },
    { from:"CHINA",     to:"UAE", color:"var(--rust)", mode:"air", side:1 },
    { from:"PAKISTAN",  to:"UAE", color:"var(--rust)", mode:"air", side:1 },
    { from:"SKOREA",    to:"UAE", color:"var(--rust)", mode:"air", side:1 },
    { from:"USA",       to:"UAE", color:"var(--rust)", mode:"air", side:1 },
    // UAE — air exports (rust, solid, reverse curvature)
    { from:"UAE", to:"USA",     color:"var(--rust)", mode:"air", side:-1 },
    { from:"UAE", to:"GERMANY", color:"var(--rust)", mode:"air", side:-1 },

    // ACE Truck (planned, Q4 2026) — CA to US ground volume, filed to CBP
    { from:"CANADA", to:"USA", color:"var(--planned)", mode:"truck", side:1, planned:true },
    // CA ELVIS (planned, Q4 2026) — US to CA air, low-value shipments, filed to CBSA
    { from:"USA", to:"CANADA", color:"var(--planned)", mode:"air", side:-1, planned:true },
    // US ACAS (planned, Q4 2026) — worldwide air imports/transits into the US, filed to CBP
    { from:"CHINA",   to:"USA", color:"var(--planned)", mode:"air", side:1, planned:true },
    { from:"INDIA",   to:"USA", color:"var(--planned)", mode:"air", side:1, planned:true },
    { from:"UAE",     to:"USA", color:"var(--planned)", mode:"air", side:1, planned:true },
    { from:"GERMANY", to:"USA", color:"var(--planned)", mode:"air", side:-1, planned:true }
  ];

  const projection = d3.geoNaturalEarth1().fitSize([WIDTH, HEIGHT - 20], { type: "Sphere" });
  projection.translate([WIDTH/2, HEIGHT/2]);
  const geoPath = d3.geoPath(projection);
  const svg = d3.select("#worldmap");

  svg.append("path").datum({type:"Sphere"}).attr("class","sphere").attr("d", geoPath);
  svg.append("path").datum(d3.geoGraticule()()).attr("class","graticule").attr("d", geoPath);

  function project(key){
    const n = nodes[key];
    return projection([n.lon, n.lat]);
  }

  function curvedPath(p1, p2, side){
    const [x1,y1] = p1, [x2,y2] = p2;
    const dx = x2-x1, dy = y2-y1;
    const dist = Math.sqrt(dx*dx+dy*dy) || 1;
    const mx = (x1+x2)/2, my = (y1+y2)/2;
    const offX = -dy/dist * dist * 0.16 * side;
    const offY = dx/dist * dist * 0.16 * side;
    return `M${x1},${y1} Q${mx+offX},${my+offY} ${x2},${y2}`;
  }

  d3.json("https://cdn.jsdelivr.net/npm/world-atlas@2/countries-110m.json").then(function(world){
    const countries = topojson.feature(world, world.objects.countries).features;

    svg.insert("g", ".graticule + *").selectAll("path.country")
      .data(countries)
      .join("path")
      .attr("class", d => {
        if(EU29.has(d.id)) return "country eu29";
        if(NODE_COUNTRIES.has(d.id)) return "country node-country";
        return "country";
      })
      .attr("d", geoPath);

    // defs: arrow markers per color
    const defs = svg.append("defs");
    ["var(--teal)","var(--amber)","var(--rust)","var(--planned)"].forEach((c,i) => {
      defs.append("marker")
        .attr("id","arrow"+i)
        .attr("viewBox","0 0 10 10")
        .attr("refX",9).attr("refY",5)
        .attr("markerWidth",6).attr("markerHeight",6)
        .attr("orient","auto-start-reverse")
        .append("path")
        .attr("d","M0,0 L10,5 L0,10 z")
        .attr("fill",c);
    });
    function markerFor(color){
      if(color==="var(--teal)") return "url(#arrow0)";
      if(color==="var(--amber)") return "url(#arrow1)";
      if(color==="var(--rust)") return "url(#arrow2)";
      return "url(#arrow3)";
    }

    const arcsG = svg.append("g").attr("class","arcs");
    flows.forEach(f => {
      const p1 = project(f.from), p2 = project(f.to);
      if(!p1 || !p2) return;
      let cls = "flow-line mode-" + f.mode;
      cls += f.planned ? " planned" : (reduceMotion ? "" : " flow-anim");
      arcsG.append("path")
        .attr("d", curvedPath(p1, p2, f.side))
        .attr("class", cls)
        .attr("stroke", f.color)
        .attr("marker-end", markerFor(f.color));
    });

    // nodes + labels
    const nodesG = svg.append("g").attr("class","nodes");

    // ACAS halo — USA receives filings from origins worldwide, not just the mapped ones
    if(!reduceMotion){
      const usaP = projection([nodes.USA.lon, nodes.USA.lat]);
      if(usaP){
        const halo = nodesG.append("circle")
          .attr("class","acas-halo")
          .attr("cx", usaP[0]).attr("cy", usaP[1]).attr("r", 8);
        halo.append("title").text("US ACAS — worldwide air imports & transits, filed to CBP (Q4 2026)");
      }
    }

    Object.keys(nodes).forEach(key => {
      const n = nodes[key];
      const p = projection([n.lon, n.lat]);
      if(!p) return;
      const g = nodesG.append("g").attr("class","map-node" + (n.hub ? " hub" : ""));
      g.append("circle")
        .attr("cx", p[0]).attr("cy", p[1])
        .attr("r", n.hub ? 4.5 : 2.6)
        .attr("fill", n.hub ? "var(--amber)" : "var(--teal)");
      g.append("text")
        .attr("x", p[0] + n.dx).attr("y", p[1] + n.dy)
        .attr("text-anchor", n.anchor)
        .text(n.label);
    });

    loadingEl.style.display = "none";
    svgEl.style.display = "block";
  }).catch(function(err){
    loadingEl.textContent = "Map data unavailable — check your connection.";
    console.error("World map load failed:", err);
  });
})();
</script>

</body>
</html>
