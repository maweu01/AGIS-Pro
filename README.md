<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>AeroGIS Pro v4 — Documentation</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@300;400;500;600;700&family=Share+Tech+Mono&family=Crimson+Pro:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<style>
/* ─── RESET ─── */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:16px}

/* ─── THEME ─── */
:root{
  --bg:       #05080f;
  --bg2:      #0b1120;
  --bg3:      #111b30;
  --bg4:      #1a2745;
  --border:   rgba(56,189,248,.10);
  --border2:  rgba(56,189,248,.30);
  --border3:  rgba(56,189,248,.55);
  --text:     #dde8f4;
  --muted:    #5a7898;
  --faint:    #1e2f45;
  --blue:     #38bdf8;
  --blue2:    #0ea5e9;
  --green:    #22d3a0;
  --amber:    #f5a623;
  --red:      #f87171;
  --purple:   #b48ef8;
  --teal:     #2dd4bf;
  --gold:     #e5c347;
  --font-head:'Rajdhani',sans-serif;
  --font-mono:'Share Tech Mono',monospace;
  --font-serif:'Crimson Pro',Georgia,serif;
}

/* ─── SCROLLBAR ─── */
::-webkit-scrollbar{width:3px;height:3px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:2px}

/* ─── BODY ─── */
body{
  font-family:var(--font-head);
  background:var(--bg);
  color:var(--text);
  line-height:1.65;
  overflow-x:hidden;
}

/* ─── STICKY NAV ─── */
.topnav{
  position:sticky;top:0;z-index:200;
  height:50px;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 32px;
  background:rgba(5,8,15,.92);
  backdrop-filter:blur(18px);
  border-bottom:1px solid var(--border);
}
.nav-brand{
  font-family:var(--font-head);font-size:18px;font-weight:700;
  color:#fff;letter-spacing:.06em;text-decoration:none;
  display:flex;align-items:center;gap:10px;
}
.nav-brand .dot{width:7px;height:7px;border-radius:50%;background:var(--green);box-shadow:0 0 8px var(--green);animation:blink 2s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.25}}
.nav-links{display:flex;gap:0}
.nav-links a{
  font-size:12px;font-weight:600;color:var(--muted);
  text-decoration:none;padding:6px 14px;border-radius:4px;
  letter-spacing:.06em;text-transform:uppercase;
  transition:color .15s,background .15s;
}
.nav-links a:hover{color:var(--blue);background:rgba(56,189,248,.07)}

/* ─── HERO ─── */
.hero{
  min-height:100vh;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  text-align:center;padding:80px 24px 60px;
  position:relative;overflow:hidden;
}
/* grid background */
.hero::before{
  content:'';position:absolute;inset:0;
  background-image:
    linear-gradient(rgba(56,189,248,.04) 1px,transparent 1px),
    linear-gradient(90deg,rgba(56,189,248,.04) 1px,transparent 1px);
  background-size:52px 52px;
  pointer-events:none;
}
/* glow */
.hero::after{
  content:'';position:absolute;
  top:-20%;left:50%;transform:translateX(-50%);
  width:900px;height:500px;
  background:radial-gradient(ellipse,rgba(56,189,248,.09) 0%,transparent 70%);
  pointer-events:none;
}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:8px;
  border:1px solid rgba(56,189,248,.25);
  background:rgba(56,189,248,.06);
  border-radius:999px;padding:5px 18px;
  font-family:var(--font-mono);font-size:11px;color:var(--blue);
  letter-spacing:.12em;margin-bottom:36px;position:relative;z-index:1;
}
.hero-title{
  font-family:var(--font-head);
  font-size:clamp(52px,9vw,110px);
  font-weight:700;
  line-height:.95;
  letter-spacing:.04em;
  text-transform:uppercase;
  position:relative;z-index:1;
  margin-bottom:6px;
}
.hero-title .a{color:#fff}
.hero-title .g{color:var(--blue)}
.hero-title .v{
  display:block;
  font-size:.24em;font-weight:400;font-family:var(--font-mono);
  color:var(--green);letter-spacing:.25em;text-transform:uppercase;
  margin-top:12px;
}
.hero-sub{
  font-family:var(--font-serif);font-size:clamp(17px,2.4vw,22px);
  font-style:italic;color:var(--muted);
  margin:24px 0 52px;max-width:640px;
  position:relative;z-index:1;line-height:1.6;
}
/* stats row */
.hero-stats{
  display:flex;gap:0;
  border:1px solid var(--border2);border-radius:10px;
  overflow:hidden;margin-bottom:48px;
  position:relative;z-index:1;
}
.hstat{
  padding:20px 32px;text-align:center;
  border-right:1px solid var(--border);
  background:rgba(11,17,32,.7);
}
.hstat:last-child{border-right:none}
.hstat-val{
  font-family:var(--font-mono);font-size:32px;font-weight:500;
  color:var(--blue);line-height:1;margin-bottom:5px;
}
.hstat-lbl{
  font-size:10px;font-weight:600;color:var(--muted);
  letter-spacing:.14em;text-transform:uppercase;
}
/* ctas */
.hero-cta{
  display:flex;gap:12px;flex-wrap:wrap;justify-content:center;
  position:relative;z-index:1;
}
.cta-primary{
  display:inline-flex;align-items:center;gap:8px;
  padding:13px 28px;background:var(--blue2);
  color:#fff;font-family:var(--font-head);font-size:15px;font-weight:600;
  border-radius:6px;text-decoration:none;letter-spacing:.04em;
  transition:all .2s;border:1px solid var(--blue2);
}
.cta-primary:hover{background:#0284c7;box-shadow:0 8px 28px rgba(56,189,248,.3);transform:translateY(-1px)}
.cta-ghost{
  display:inline-flex;align-items:center;gap:8px;
  padding:13px 28px;background:transparent;
  color:var(--text);font-family:var(--font-head);font-size:15px;font-weight:600;
  border-radius:6px;text-decoration:none;letter-spacing:.04em;
  transition:all .2s;border:1px solid var(--border2);
}
.cta-ghost:hover{background:rgba(56,189,248,.08);border-color:var(--blue)}
/* scroll hint */
.scroll-cue{
  position:absolute;bottom:32px;left:50%;transform:translateX(-50%);
  display:flex;flex-direction:column;align-items:center;gap:6px;
  font-family:var(--font-mono);font-size:10px;color:var(--muted);letter-spacing:.12em;
}
.scroll-arrow{animation:bob 2s infinite}
@keyframes bob{0%,100%{transform:translateY(0)}50%{transform:translateY(5px)}}

/* ─── LAYOUT ─── */
.wrap{max-width:1160px;margin:0 auto;padding:0 28px}
.section{padding:88px 0;border-bottom:1px solid var(--border)}
.section:last-of-type{border-bottom:none}

/* ─── SECTION HEADERS ─── */
.eyebrow{
  font-family:var(--font-mono);font-size:11px;color:var(--blue);
  letter-spacing:.18em;text-transform:uppercase;
  display:flex;align-items:center;gap:12px;margin-bottom:14px;
}
.eyebrow::before{content:'';width:28px;height:1px;background:var(--blue);flex-shrink:0}
.sec-h{
  font-family:var(--font-head);
  font-size:clamp(32px,5vw,52px);font-weight:700;
  line-height:1.0;letter-spacing:.03em;text-transform:uppercase;
  color:#fff;margin-bottom:18px;
}
.sec-h em{color:var(--blue);font-style:normal}
.sec-lead{
  font-family:var(--font-serif);font-size:18px;color:var(--muted);
  max-width:700px;line-height:1.85;
}

/* ─── FEATURE GRID ─── */
.fgrid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(310px,1fr));
  gap:14px;margin-top:52px;
}
.fcard{
  background:var(--bg2);border:1px solid var(--border);
  border-radius:10px;padding:26px;
  transition:border-color .2s,transform .2s,box-shadow .2s;
  position:relative;overflow:hidden;
}
.fcard::after{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--blue),transparent);
  opacity:0;transition:opacity .2s;
}
.fcard:hover{border-color:var(--border2);transform:translateY(-2px);box-shadow:0 14px 40px rgba(0,0,0,.4)}
.fcard:hover::after{opacity:1}
.fcard-icon{font-size:26px;margin-bottom:14px;display:block}
.fcard-title{font-size:17px;font-weight:700;color:#fff;margin-bottom:8px;letter-spacing:.03em;text-transform:uppercase}
.fcard-body{font-size:13px;color:var(--muted);line-height:1.75;font-family:var(--font-serif)}
.fcard-tag{
  display:inline-block;margin-top:14px;
  padding:3px 10px;border-radius:3px;
  font-family:var(--font-mono);font-size:10px;letter-spacing:.08em;
  background:rgba(56,189,248,.07);border:1px solid rgba(56,189,248,.2);color:var(--blue);
}

/* ─── DATA TABLE ─── */
.dtable{width:100%;border-collapse:collapse;font-size:13px;margin-top:18px}
.dtable thead tr{background:rgba(56,189,248,.06)}
.dtable th{
  padding:10px 14px;text-align:left;
  font-family:var(--font-mono);font-size:10px;letter-spacing:.1em;
  color:var(--muted);font-weight:400;text-transform:uppercase;
  border-bottom:1px solid var(--border);
}
.dtable td{
  padding:9px 14px;border-bottom:1px solid rgba(56,189,248,.05);
  color:var(--muted);font-family:var(--font-serif);font-size:14px;
  vertical-align:middle;
}
.dtable td:first-child{color:var(--text);font-family:var(--font-head);font-weight:600;font-size:13px}
.dtable tr:last-child td{border-bottom:none}
.dtable tr:hover td{background:rgba(56,189,248,.025)}
.dtable code{
  font-family:var(--font-mono);font-size:11px;
  color:var(--green);background:rgba(34,211,160,.08);
  padding:2px 6px;border-radius:3px;
}

/* ─── CATEGORY LABEL ─── */
.cat-label{
  font-family:var(--font-mono);font-size:10px;letter-spacing:.14em;
  color:var(--blue);text-transform:uppercase;
  padding:7px 14px;background:rgba(56,189,248,.06);
  border:1px solid var(--border);border-radius:5px 5px 0 0;border-bottom:none;
  margin-top:28px;display:block;
}

/* ─── BADGE ─── */
.badge{
  display:inline-flex;align-items:center;
  padding:2px 9px;border-radius:3px;
  font-family:var(--font-mono);font-size:10px;letter-spacing:.06em;font-weight:500;
}
.ba{background:rgba(56,189,248,.10);border:1px solid rgba(56,189,248,.25);color:var(--blue)}
.bg{background:rgba(34,211,160,.10);border:1px solid rgba(34,211,160,.25);color:var(--green)}
.bam{background:rgba(245,166,35,.10);border:1px solid rgba(245,166,35,.25);color:var(--amber)}
.br{background:rgba(248,113,113,.10);border:1px solid rgba(248,113,113,.25);color:var(--red)}
.bp{background:rgba(180,142,248,.10);border:1px solid rgba(180,142,248,.25);color:var(--purple)}

/* ─── CODE BLOCK ─── */
.code-box{
  background:var(--bg3);border:1px solid var(--border);
  border-radius:8px;padding:20px 24px;
  font-family:var(--font-mono);font-size:13px;line-height:1.85;
  color:var(--text);overflow-x:auto;margin:18px 0;position:relative;
}
.code-box .lang{
  position:absolute;top:10px;right:14px;
  font-size:10px;color:var(--muted);letter-spacing:.1em;text-transform:uppercase;
}
.code-box .cm{color:var(--muted)}
.code-box .ck{color:var(--purple)}
.code-box .cs{color:var(--green)}
.code-box .cn{color:var(--blue)}

/* ─── INLINE CODE ─── */
code{
  font-family:var(--font-mono);font-size:12px;
  color:var(--teal);background:rgba(45,212,191,.08);
  padding:2px 6px;border-radius:3px;
}

/* ─── TWO-COL ─── */
.two-col{display:grid;grid-template-columns:1fr 1fr;gap:32px;margin-top:40px}
@media(max-width:720px){.two-col{grid-template-columns:1fr}}

/* ─── PIPELINE ─── */
.pipeline{
  position:relative;margin-top:48px;
  padding-left:56px;
}
.pipeline::before{
  content:'';position:absolute;
  left:19px;top:10px;bottom:10px;width:2px;
  background:linear-gradient(to bottom,var(--blue),var(--teal),var(--green));
}
.pipe-step{
  position:relative;margin-bottom:0;
  padding:18px 0 18px;
}
.pipe-step::before{
  content:'';position:absolute;
  left:-49px;top:22px;width:40px;height:40px;
  border-radius:50%;
  background:var(--bg3);border:2px solid var(--blue);
  z-index:1;
}
.pipe-num{
  position:absolute;left:-42px;top:30px;
  font-family:var(--font-mono);font-size:12px;color:var(--blue);
  z-index:2;width:26px;text-align:center;line-height:1;
}
.pipe-title{font-size:16px;font-weight:700;color:#fff;letter-spacing:.04em;text-transform:uppercase;margin-bottom:5px}
.pipe-desc{font-family:var(--font-serif);font-size:14px;color:var(--muted);line-height:1.75}
.pipe-formula{
  display:inline-block;margin-top:8px;
  font-family:var(--font-mono);font-size:12px;
  color:var(--green);background:rgba(34,211,160,.07);
  border:1px solid rgba(34,211,160,.18);
  padding:4px 12px;border-radius:4px;
}

/* ─── ZONE GRID ─── */
.zone-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));
  gap:10px;margin-top:28px;
}
.zone-row{
  display:flex;align-items:center;gap:12px;
  padding:11px 14px;background:var(--bg2);
  border:1px solid var(--border);border-radius:7px;
}
.zone-swatch{width:16px;height:16px;border-radius:3px;flex-shrink:0}
.zone-name{font-size:14px;font-weight:600;color:var(--text);letter-spacing:.02em}
.zone-hint{font-family:var(--font-serif);font-size:12px;color:var(--muted);margin-top:1px}

/* ─── NFZ TABLE ─── */
.nfz-dot{
  display:inline-block;width:10px;height:10px;
  border-radius:50%;margin-right:6px;
}

/* ─── ALERT BOX ─── */
.abox{
  display:flex;gap:14px;align-items:flex-start;
  padding:16px 20px;border-radius:8px;
  font-family:var(--font-serif);font-size:14px;line-height:1.75;
  margin:22px 0;
}
.abox.info{background:rgba(56,189,248,.06);border:1px solid rgba(56,189,248,.22);color:var(--blue)}
.abox.warn{background:rgba(245,166,35,.06);border:1px solid rgba(245,166,35,.22);color:var(--amber)}
.abox.tip {background:rgba(34,211,160,.06);border:1px solid rgba(34,211,160,.22);color:var(--teal)}
.abox .icon{font-size:18px;flex-shrink:0;padding-top:2px}
.abox strong{display:block;font-family:var(--font-head);font-size:14px;font-weight:700;letter-spacing:.04em;margin-bottom:3px}

/* ─── QUICK CARDS ─── */
.qgrid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:10px;margin-top:28px;
}
.qcard{
  background:var(--bg2);border:1px solid var(--border);
  border-radius:7px;padding:14px 16px;
}
.qcard-key{font-family:var(--font-mono);font-size:12px;color:var(--green);margin-bottom:5px}
.qcard-val{font-family:var(--font-serif);font-size:13px;color:var(--muted);line-height:1.65}

/* ─── AUTHOR CARD ─── */
.author-card{
  background:var(--bg2);border:1px solid var(--border);
  border-radius:14px;padding:38px;
  display:flex;gap:30px;align-items:flex-start;
  margin-top:44px;
}
.author-av{
  width:74px;height:74px;flex-shrink:0;border-radius:50%;
  background:linear-gradient(135deg,#0c4a6e,#38bdf8);
  display:flex;align-items:center;justify-content:center;
  font-family:var(--font-head);font-size:28px;font-weight:700;color:#fff;
}
.author-name{font-size:22px;font-weight:700;color:#fff;letter-spacing:.04em;text-transform:uppercase;margin-bottom:3px}
.author-role{font-family:var(--font-mono);font-size:12px;color:var(--blue);letter-spacing:.08em;margin-bottom:14px}
.author-bio{font-family:var(--font-serif);font-size:15px;color:var(--muted);line-height:1.8}
.author-tags{display:flex;flex-wrap:wrap;gap:7px;margin-top:14px}

/* ─── DIVIDER ─── */
.hr{height:1px;background:linear-gradient(90deg,transparent,var(--border2),transparent);margin:52px 0}

/* ─── FOOTER ─── */
.footer{
  padding:56px 0;text-align:center;
  border-top:1px solid var(--border);
}
.footer-logo{
  font-family:var(--font-head);font-size:28px;font-weight:700;
  letter-spacing:.08em;text-transform:uppercase;color:#fff;margin-bottom:10px;
}
.footer-logo span{color:var(--blue)}
.footer-text{font-family:var(--font-serif);font-size:14px;color:var(--muted);line-height:2}

/* ─── RESPONSIVE ─── */
@media(max-width:700px){
  .fgrid{grid-template-columns:1fr}
  .hero-stats{flex-direction:column}
  .hstat{border-right:none;border-bottom:1px solid var(--border)}
  .hstat:last-child{border-bottom:none}
  .nav-links{display:none}
  .author-card{flex-direction:column}
  .author-av{width:56px;height:56px;font-size:20px}
}
</style>
</head>
<body>

<!-- ══ STICKY NAV ══ -->
<nav class="topnav">
  <a href="#top" class="nav-brand"><span class="dot"></span>AeroGIS Pro</a>
  <div class="nav-links">
    <a href="#overview">Overview</a>
    <a href="#modules">Modules</a>
    <a href="#aircraft">Aircraft</a>
    <a href="#sensors">Sensors</a>
    <a href="#epl">Planning Lab</a>
    <a href="#exports">Exports</a>
    <a href="#kcaa">KCAA</a>
    <a href="#start">Quick Start</a>
  </div>
</nav>

<!-- ══ HERO ══ -->
<section class="hero" id="top">
  <div class="hero-eyebrow">
    <span>●</span> v4.0 — Production Release &nbsp;·&nbsp; Single-File Application &nbsp;·&nbsp; KCAA LN 182/2022 Compliant
  </div>

  <h1 class="hero-title">
    <span class="a">Aero</span><span class="g">GIS</span>
    <span class="v">Pro — Aerial Survey Intelligence Platform</span>
  </h1>

  <p class="hero-sub">
    Professional drone survey planning, airspace intelligence, and environmental land-use
    modelling for operators, GIS engineers, and county planners working across Kenya and
    East Africa.
  </p>

  <div class="hero-stats">
    <div class="hstat"><div class="hstat-val">16</div><div class="hstat-lbl">Drone Platforms</div></div>
    <div class="hstat"><div class="hstat-val">13</div><div class="hstat-lbl">Camera / Sensors</div></div>
    <div class="hstat"><div class="hstat-val">9</div><div class="hstat-lbl">Modules</div></div>
    <div class="hstat"><div class="hstat-val">7</div><div class="hstat-lbl">Export Formats</div></div>
    <div class="hstat"><div class="hstat-val">134</div><div class="hstat-lbl">Functions</div></div>
    <div class="hstat"><div class="hstat-val">0</div><div class="hstat-lbl">Dependencies</div></div>
  </div>

  <div class="hero-cta">
    <a href="https://maweu01.github.io/AeroGIS-Survey-Planner" target="_blank" class="cta-primary">⚡ Launch Application</a>
    <a href="https://github.com/maweu01/AeroGIS-Survey-Planner" target="_blank" class="cta-ghost">⌥ GitHub Repository</a>
  </div>

  <div class="scroll-cue">
    <span>Documentation</span>
    <span class="scroll-arrow">↓</span>
  </div>
</section>

<!-- ══ OVERVIEW ══ -->
<section class="section" id="overview">
  <div class="wrap">
    <div class="eyebrow">Overview</div>
    <h2 class="sec-h">One file.<br><em>Everything</em> you need.</h2>
    <p class="sec-lead">
      AeroGIS Pro v4 is a zero-dependency, single-file HTML application that delivers a
      complete aerial survey planning and environmental intelligence platform. No server,
      no build process, no npm. Open <code>index.html</code> in any modern browser and
      the entire system — maps, aircraft database, KCAA registry, and the 7-step
      Environmental Planning Lab — is immediately available.
    </p>

    <div class="abox info" style="margin-top:36px;">
      <div class="icon">ℹ</div>
      <div>
        <strong>Architecture</strong>
        The complete application ships as a single <code>index.html</code> file (181 KB).
        It uses Leaflet 1.9.4 and Leaflet Draw 1.0.4 from CDN, the Open-Meteo public
        weather API (no key required), and Esri World Services for basemaps and hillshade.
        All logic is ES5 JavaScript — no transpiler, no bundler, no framework.
      </div>
    </div>

    <div class="two-col" style="margin-top:52px;">
      <div>
        <div class="eyebrow">Technology Stack</div>
        <table class="dtable">
          <thead><tr><th>Layer</th><th>Technology</th></tr></thead>
          <tbody>
            <tr><td>Map Engine</td><td><code>Leaflet 1.9.4</code></td></tr>
            <tr><td>Draw Tools</td><td><code>Leaflet Draw 1.0.4</code></td></tr>
            <tr><td>Satellite Basemap</td><td>Esri World Imagery (ArcGIS)</td></tr>
            <tr><td>Hybrid Labels</td><td>Esri World Boundaries &amp; Places</td></tr>
            <tr><td>DEM Overlay</td><td>Esri World Hillshade — SRTM-derived</td></tr>
            <tr><td>Topographic</td><td>OpenTopoMap — contour overlay</td></tr>
            <tr><td>Street Map</td><td>OpenStreetMap (OSM)</td></tr>
            <tr><td>Weather API</td><td>Open-Meteo (free, no key)</td></tr>
            <tr><td>Runtime</td><td>ES5 JavaScript — universal browser</td></tr>
            <tr><td>Hosting</td><td>GitHub Pages · Any static server</td></tr>
          </tbody>
        </table>
      </div>
      <div>
        <div class="eyebrow">Regulatory Framework</div>
        <table class="dtable">
          <thead><tr><th>Instrument</th><th>Scope<
