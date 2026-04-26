<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DNA Sequence & Structure Visualizer</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&display=swap');

  :root {
    --bg: #000000;
    --adenine: #00ffaa;
    --thymine: #ff4466;
    --cytosine: #4488ff;
    --guanine: #ffcc00;
    --backbone: #334455;
    --glow-a: rgba(0,255,170,0.6);
    --glow-t: rgba(255,68,102,0.6);
    --glow-c: rgba(68,136,255,0.6);
    --glow-g: rgba(255,204,0,0.6);
    --panel-bg: rgba(5,10,20,0.92);
    --border: rgba(0,200,150,0.3);
    --text: #c0e8d0;
    --accent: #00ffaa;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: #000;
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    overflow: hidden;
    height: 100vh;
    width: 100vw;
  }

  /* Starfield background */
  #starfield {
    position: fixed;
    inset: 0;
    z-index: 0;
    pointer-events: none;
  }

  /* Scanline overlay */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
    pointer-events: none;
    z-index: 9998;
  }

  /* Header */
  #header {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 12px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: linear-gradient(180deg, rgba(0,0,0,0.95) 0%, rgba(0,0,0,0) 100%);
    border-bottom: 1px solid rgba(0,255,170,0.15);
  }

  #header h1 {
    font-family: 'Orbitron', monospace;
    font-size: 1.1rem;
    font-weight: 900;
    letter-spacing: 0.3em;
    color: var(--accent);
    text-shadow: 0 0 20px var(--glow-a);
  }

  #header .subtitle {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
    color: rgba(0,255,170,0.5);
    letter-spacing: 0.2em;
  }

  /* 3D Canvas */
  #canvas3d {
    position: fixed;
    inset: 0;
    z-index: 1;
    cursor: grab;
  }
  #canvas3d:active { cursor: grabbing; }

  /* Controls Panel */
  #controls {
    position: fixed;
    right: 20px;
    top: 50%;
    transform: translateY(-50%);
    z-index: 200;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .ctrl-btn {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    border: 1px solid var(--border);
    background: var(--panel-bg);
    color: var(--accent);
    font-size: 1.2rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    font-family: 'Orbitron', monospace;
    backdrop-filter: blur(10px);
    box-shadow: 0 0 12px rgba(0,255,170,0.1), inset 0 0 6px rgba(0,255,170,0.05);
  }

  .ctrl-btn:hover {
    border-color: var(--accent);
    background: rgba(0,255,170,0.1);
    box-shadow: 0 0 20px var(--glow-a);
    transform: scale(1.1);
  }

  .ctrl-btn.info-btn {
    font-size: 0.9rem;
    font-weight: 700;
  }

  /* Info Modal */
  #info-modal {
    position: fixed;
    inset: 0;
    z-index: 500;
    display: none;
    align-items: center;
    justify-content: center;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(4px);
  }
  #info-modal.open { display: flex; }

  #info-box {
    background: var(--panel-bg);
    border: 1px solid var(--accent);
    border-radius: 12px;
    padding: 32px;
    max-width: 440px;
    width: 90%;
    box-shadow: 0 0 60px var(--glow-a), inset 0 0 30px rgba(0,255,170,0.03);
    position: relative;
  }

  #info-box h2 {
    font-family: 'Orbitron', monospace;
    font-size: 1rem;
    letter-spacing: 0.2em;
    color: var(--accent);
    margin-bottom: 20px;
    text-shadow: 0 0 10px var(--glow-a);
  }

  .info-row {
    display: flex;
    gap: 14px;
    align-items: flex-start;
    margin-bottom: 14px;
    padding-bottom: 14px;
    border-bottom: 1px solid rgba(0,255,170,0.1);
  }
  .info-row:last-child { border-bottom: none; margin-bottom: 0; }

  .info-icon {
    font-size: 1.4rem;
    width: 32px;
    flex-shrink: 0;
    text-align: center;
  }

  .info-text strong {
    display: block;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    margin-bottom: 3px;
  }

  .info-text span {
    font-size: 0.85rem;
    color: rgba(192,232,208,0.7);
    line-height: 1.4;
  }

  #close-info {
    position: absolute;
    top: 12px;
    right: 16px;
    background: none;
    border: none;
    color: var(--accent);
    font-size: 1.3rem;
    cursor: pointer;
    font-family: 'Orbitron', monospace;
    opacity: 0.7;
    transition: opacity 0.2s;
  }
  #close-info:hover { opacity: 1; }

  /* Sequence strip at bottom */
  #sequence-strip {
    position: fixed;
    bottom: 0; left: 0; right: 0;
    z-index: 200;
    padding: 10px 16px 14px;
    background: linear-gradient(0deg, rgba(0,0,0,0.98) 0%, rgba(0,0,0,0) 100%);
    border-top: 1px solid rgba(0,255,170,0.1);
  }

  #seq-label {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.6rem;
    color: rgba(0,255,170,0.4);
    letter-spacing: 0.2em;
    margin-bottom: 6px;
  }

  #seq-row {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto;
    gap: 2px;
    scrollbar-width: thin;
    scrollbar-color: var(--accent) transparent;
    padding-bottom: 4px;
  }

  #seq-row::-webkit-scrollbar { height: 3px; }
  #seq-row::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 2px; }

  .base-chip {
    flex-shrink: 0;
    width: 28px;
    height: 28px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.8rem;
    font-weight: 700;
    cursor: pointer;
    position: relative;
    transition: all 0.2s ease;
    border: 1px solid transparent;
  }

  .base-chip:hover {
    transform: scale(1.4) translateY(-4px);
    z-index: 10;
    box-shadow: 0 8px 24px currentColor;
  }

  .base-chip.A { background: rgba(0,255,170,0.15); color: var(--adenine); border-color: rgba(0,255,170,0.4); }
  .base-chip.T { background: rgba(255,68,102,0.15); color: var(--thymine); border-color: rgba(255,68,102,0.4); }
  .base-chip.C { background: rgba(68,136,255,0.15); color: var(--cytosine); border-color: rgba(68,136,255,0.4); }
  .base-chip.G { background: rgba(255,204,0,0.15); color: var(--guanine); border-color: rgba(255,204,0,0.4); }

  .base-chip .chip-index {
    position: absolute;
    bottom: -12px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 0.45rem;
    color: rgba(192,232,208,0.3);
    font-family: 'Share Tech Mono', monospace;
    white-space: nowrap;
    pointer-events: none;
  }

  /* Info Popup on click */
  #base-popup {
    position: fixed;
    z-index: 300;
    pointer-events: none;
    display: none;
    transform: translateX(-50%);
  }

  #base-popup.show { display: block; }

  .popup-box {
    background: var(--panel-bg);
    border: 1px solid var(--accent);
    border-radius: 10px;
    padding: 16px 20px;
    min-width: 220px;
    box-shadow: 0 0 40px var(--glow-a);
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.72rem;
    line-height: 1.8;
    pointer-events: none;
    backdrop-filter: blur(12px);
  }

  .popup-box .pb-title {
    font-family: 'Orbitron', monospace;
    font-size: 0.9rem;
    color: var(--accent);
    margin-bottom: 10px;
    text-shadow: 0 0 10px var(--glow-a);
  }

  .pb-row { display: flex; justify-content: space-between; gap: 12px; }
  .pb-key { color: rgba(192,232,208,0.5); }
  .pb-val { color: var(--text); font-weight: 600; }

  .pb-val.A { color: var(--adenine); }
  .pb-val.T { color: var(--thymine); }
  .pb-val.C { color: var(--cytosine); }
  .pb-val.G { color: var(--guanine); }

  /* Legend */
  #legend {
    position: fixed;
    left: 20px;
    top: 50%;
    transform: translateY(-50%);
    z-index: 200;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
  }

  .legend-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* Stats */
  #stats {
    position: fixed;
    left: 20px;
    bottom: 100px;
    z-index: 200;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.62rem;
    color: rgba(0,255,170,0.4);
    line-height: 1.6;
  }

  .stat-line { display: flex; gap: 6px; }
  .stat-key { color: rgba(0,255,170,0.3); }
  .stat-val { color: rgba(0,255,170,0.7); }

  /* Highlight on 3D when base selected */
  #highlight-label {
    position: fixed;
    top: 70px;
    left: 50%;
    transform: translateX(-50%);
    z-index: 200;
    font-family: 'Orbitron', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: var(--accent);
    text-shadow: 0 0 12px var(--glow-a);
    opacity: 0;
    transition: opacity 0.4s;
    pointer-events: none;
  }
  #highlight-label.show { opacity: 1; }

  /* Rotation indicator */
  #rotate-hint {
    position: fixed;
    bottom: 100px;
    right: 70px;
    z-index: 200;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.6rem;
    color: rgba(0,255,170,0.25);
    text-align: center;
    line-height: 1.6;
    pointer-events: none;
  }
</style>
</head>
<body>

<canvas id="starfield"></canvas>
<canvas id="canvas3d"></canvas>

<!-- Header -->
<div id="header">
  <div>
    <div class="subtitle">GENOMIC VISUALIZATION SYSTEM v2.4</div>
    <h1>DNA SEQUENCE EXPLORER</h1>
  </div>
  <div style="font-family:'Share Tech Mono',monospace;font-size:0.6rem;color:rgba(0,255,170,0.35);text-align:right;line-height:1.8">
    <div>HOMO SAPIENS / CHR17</div>
    <div id="live-clock"></div>
  </div>
</div>

<!-- Legend -->
<div id="legend">
  <div style="font-family:'Orbitron',monospace;font-size:0.55rem;color:rgba(0,255,170,0.4);letter-spacing:0.15em;margin-bottom:6px">BASES</div>
  <div class="legend-item">
    <div class="legend-dot" style="background:var(--adenine);box-shadow:0 0 6px var(--glow-a)"></div>
    <span style="color:var(--adenine)">A — Adenine</span>
  </div>
  <div class="legend-item">
    <div class="legend-dot" style="background:var(--thymine);box-shadow:0 0 6px var(--glow-t)"></div>
    <span style="color:var(--thymine)">T — Thymine</span>
  </div>
  <div class="legend-item">
    <div class="legend-dot" style="background:var(--cytosine);box-shadow:0 0 6px var(--glow-c)"></div>
    <span style="color:var(--cytosine)">C — Cytosine</span>
  </div>
  <div class="legend-item">
    <div class="legend-dot" style="background:var(--guanine);box-shadow:0 0 6px var(--glow-g)"></div>
    <span style="color:var(--guanine)">G — Guanine</span>
  </div>
</div>

<!-- Stats -->
<div id="stats">
  <div id="stat-display"></div>
</div>

<!-- Controls -->
<div id="controls">
  <button class="ctrl-btn" id="zoom-in-btn" title="Zoom In">+</button>
  <button class="ctrl-btn" id="zoom-out-btn" title="Zoom Out">−</button>
  <button class="ctrl-btn" id="reset-btn" title="Reset View" style="font-size:0.75rem;letter-spacing:0">↺</button>
  <button class="ctrl-btn info-btn" id="info-btn" title="Help">?</button>
</div>

<!-- Rotate hint -->
<div id="rotate-hint">
  DRAG TO<br>ROTATE
</div>

<!-- Highlight label -->
<div id="highlight-label" id="highlight-label"></div>

<!-- Sequence Strip -->
<div id="sequence-strip">
  <div id="seq-label">5' → 3' SEQUENCE STRAND ·· CLICK ANY BASE FOR DETAILS</div>
  <div id="seq-row"></div>
</div>

<!-- Base Popup -->
<div id="base-popup">
  <div class="popup-box">
    <div class="pb-title" id="pb-title">BASE INFO</div>
    <div id="pb-content"></div>
  </div>
</div>

<!-- Info Modal -->
<div id="info-modal">
  <div id="info-box">
    <button id="close-info">✕</button>
    <h2>INTERACTION GUIDE</h2>
    <div class="info-row">
      <div class="info-icon">🖱️</div>
      <div class="info-text">
        <strong>ROTATE MODEL</strong>
        <span>Click and drag anywhere on the 3D model to rotate it freely in 3D space.</span>
      </div>
    </div>
    <div class="info-row">
      <div class="info-icon">🔍</div>
      <div class="info-text">
        <strong>ZOOM IN / OUT</strong>
        <span>Use the + / − buttons on the right, or scroll your mouse wheel over the model.</span>
      </div>
    </div>
    <div class="info-row">
      <div class="info-icon">🧬</div>
      <div class="info-text">
        <strong>BASE DETAILS</strong>
        <span>Click any base chip in the bottom sequence strip to see full nucleotide information in a popup.</span>
      </div>
    </div>
    <div class="info-row">
      <div class="info-icon">✨</div>
      <div class="info-text">
        <strong>HOVER TO ZOOM</strong>
        <span>Hover over any base chip in the sequence strip — it zooms and lifts for easy reading.</span>
      </div>
    </div>
    <div class="info-row">
      <div class="info-icon">↺</div>
      <div class="info-text">
        <strong>RESET VIEW</strong>
        <span>Press the ↺ button to restore the default camera angle and zoom level.</span>
      </div>
    </div>
  </div>
</div>

<script>
// ─── DNA Data ───────────────────────────────────────────────────────────────
const DNA_SEQ = "ATGCGTAACGGCTTAACCGATCGGAATTTCGCATGCAATGCGATCGAATTCGATCGATCGATCGATCATCGATCATCGATCGTATCGATCG";

const BASE_INFO = {
  A: {
    name: "Adenine",
    type: "Purine",
    pair: "Thymine (T)",
    bonds: "2 hydrogen bonds",
    formula: "C₅H₅N₅",
    molWeight: "135.13 g/mol",
    color: "#00ffaa",
    role: "Energy carrier (ATP), signaling",
    meltingContrib: "Low (2 H-bonds)"
  },
  T: {
    name: "Thymine",
    type: "Pyrimidine",
    pair: "Adenine (A)",
    bonds: "2 hydrogen bonds",
    formula: "C₅H₆N₂O₂",
    molWeight: "126.11 g/mol",
    color: "#ff4466",
    role: "DNA-specific base (replaced by U in RNA)",
    meltingContrib: "Low (2 H-bonds)"
  },
  C: {
    name: "Cytosine",
    type: "Pyrimidine",
    pair: "Guanine (G)",
    bonds: "3 hydrogen bonds",
    formula: "C₄H₅N₃O",
    molWeight: "111.10 g/mol",
    color: "#4488ff",
    role: "Methylation target, gene regulation",
    meltingContrib: "High (3 H-bonds)"
  },
  G: {
    name: "Guanine",
    type: "Purine",
    pair: "Cytosine (C)",
    bonds: "3 hydrogen bonds",
    formula: "C₅H₅N₅O",
    molWeight: "151.13 g/mol",
    color: "#ffcc00",
    role: "G-quadruplex formation, signaling",
    meltingContrib: "High (3 H-bonds)"
  }
};

const COMPLEMENT = { A:'T', T:'A', C:'G', G:'C' };

// ─── Starfield ───────────────────────────────────────────────────────────────
(function(){
  const c = document.getElementById('starfield');
  const ctx = c.getContext('2d');
  c.width = window.innerWidth;
  c.height = window.innerHeight;
  const stars = Array.from({length:200}, () => ({
    x: Math.random()*c.width, y: Math.random()*c.height,
    r: Math.random()*1.2, a: Math.random()
  }));
  function draw(){
    ctx.clearRect(0,0,c.width,c.height);
    stars.forEach(s => {
      s.a += 0.003 * (Math.random()-0.5);
      s.a = Math.max(0.05, Math.min(0.6, s.a));
      ctx.beginPath();
      ctx.arc(s.x, s.y, s.r, 0, Math.PI*2);
      ctx.fillStyle = `rgba(180,220,200,${s.a})`;
      ctx.fill();
    });
    requestAnimationFrame(draw);
  }
  draw();
  window.addEventListener('resize', () => { c.width=window.innerWidth; c.height=window.innerHeight; });
})();

// ─── Live Clock ──────────────────────────────────────────────────────────────
function updateClock(){
  const now = new Date();
  document.getElementById('live-clock').textContent =
    now.toISOString().replace('T',' ').slice(0,19) + ' UTC';
}
updateClock();
setInterval(updateClock, 1000);

// ─── Sequence Strip ───────────────────────────────────────────────────────────
const seqRow = document.getElementById('seq-row');
DNA_SEQ.split('').forEach((base, i) => {
  const chip = document.createElement('div');
  chip.className = `base-chip ${base}`;
  chip.textContent = base;
  chip.dataset.base = base;
  chip.dataset.index = i;

  const idxEl = document.createElement('div');
  idxEl.className = 'chip-index';
  idxEl.textContent = i+1;
  chip.appendChild(idxEl);

  chip.addEventListener('click', (e) => showBasePopup(e, base, i));
  seqRow.appendChild(chip);
});

// ─── Base Popup ───────────────────────────────────────────────────────────────
const popup = document.getElementById('base-popup');
const pbTitle = document.getElementById('pb-title');
const pbContent = document.getElementById('pb-content');
let popupTimeout;

function showBasePopup(e, base, idx) {
  const info = BASE_INFO[base];
  const comp = COMPLEMENT[base];
  pbTitle.textContent = `${base} · POSITION ${idx+1}`;
  pbTitle.style.color = info.color;
  pbTitle.style.textShadow = `0 0 10px ${info.color}88`;
  popup.querySelector('.popup-box').style.borderColor = info.color;
  popup.querySelector('.popup-box').style.boxShadow = `0 0 40px ${info.color}44`;

  const rows = [
    ['NAME', info.name, base],
    ['TYPE', info.type, ''],
    ['COMPLEMENT', `${comp} — ${BASE_INFO[comp].name}`, comp],
    ['H-BONDS', info.bonds, ''],
    ['FORMULA', info.formula, ''],
    ['MOL WT', info.molWeight, ''],
    ['STRAND POS', `5' → Pos ${idx+1} / ${DNA_SEQ.length}`, ''],
    ['ROLE', info.role, ''],
    ['GC CONTRIB', info.meltingContrib, ''],
  ];

  pbContent.innerHTML = rows.map(([k, v, cls]) =>
    `<div class="pb-row"><span class="pb-key">${k}</span><span class="pb-val ${cls}">${v}</span></div>`
  ).join('');

  const chipRect = e.target.getBoundingClientRect();
  popup.style.left = `${chipRect.left + chipRect.width/2}px`;
  popup.style.bottom = `${window.innerHeight - chipRect.top + 12}px`;
  popup.style.top = 'auto';
  popup.classList.add('show');

  // Highlight in 3D
  const hl = document.getElementById('highlight-label');
  hl.textContent = `◈ BASE ${idx+1}: ${info.name.toUpperCase()} ← HIGHLIGHTED`;
  hl.style.color = info.color;
  hl.style.textShadow = `0 0 12px ${info.color}88`;
  hl.classList.add('show');
  highlightBase = idx;

  clearTimeout(popupTimeout);
  popupTimeout = setTimeout(() => {
    popup.classList.remove('show');
    hl.classList.remove('show');
    highlightBase = -1;
  }, 4000);
}

document.addEventListener('click', (e) => {
  if (!e.target.classList.contains('base-chip') && !popup.contains(e.target)) {
    popup.classList.remove('show');
  }
});

// ─── Stats ───────────────────────────────────────────────────────────────────
function calcStats(){
  const counts = {A:0,T:0,C:0,G:0};
  DNA_SEQ.split('').forEach(b => counts[b]++);
  const total = DNA_SEQ.length;
  const gc = ((counts.G+counts.C)/total*100).toFixed(1);
  document.getElementById('stat-display').innerHTML =
    `<div style="font-family:'Orbitron',monospace;font-size:0.55rem;color:rgba(0,255,170,0.4);letter-spacing:0.15em;margin-bottom:6px">STATS</div>`+
    ['A','T','C','G'].map(b => `<div class="stat-line"><span class="stat-key" style="color:${BASE_INFO[b].color}88">${b}</span><span class="stat-val" style="color:${BASE_INFO[b].color}">${counts[b]}</span><span class="stat-key">(${(counts[b]/total*100).toFixed(0)}%)</span></div>`).join('')+
    `<div class="stat-line" style="margin-top:6px"><span class="stat-key">LEN</span><span class="stat-val">${total}bp</span></div>`+
    `<div class="stat-line"><span class="stat-key">GC%</span><span class="stat-val">${gc}%</span></div>`;
}
calcStats();

// ─── Info Modal ───────────────────────────────────────────────────────────────
document.getElementById('info-btn').onclick = () => document.getElementById('info-modal').classList.add('open');
document.getElementById('close-info').onclick = () => document.getElementById('info-modal').classList.remove('open');
document.getElementById('info-modal').onclick = (e) => { if(e.target===document.getElementById('info-modal')) document.getElementById('info-modal').classList.remove('open'); };

// ─── 3D DNA Canvas ────────────────────────────────────────────────────────────
const canvas = document.getElementById('canvas3d');
const ctx3d = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
window.addEventListener('resize', () => { canvas.width=window.innerWidth; canvas.height=window.innerHeight; });

let rotX = 0.3, rotY = 0, rotZ = 0;
let targetRotX = 0.3, targetRotY = 0;
let zoom = 1.0, targetZoom = 1.0;
let isDragging = false, lastMX = 0, lastMY = 0;
let autoRotate = true;
let highlightBase = -1;
let frame = 0;

// Controls
document.getElementById('zoom-in-btn').onclick = () => { targetZoom = Math.min(3, targetZoom+0.25); autoRotate=false; };
document.getElementById('zoom-out-btn').onclick = () => { targetZoom = Math.max(0.3, targetZoom-0.25); autoRotate=false; };
document.getElementById('reset-btn').onclick = () => { targetRotX=0.3; targetRotY=0; targetZoom=1.0; autoRotate=true; };

canvas.addEventListener('wheel', (e) => {
  e.preventDefault();
  targetZoom = Math.max(0.3, Math.min(3, targetZoom - e.deltaY*0.001));
  autoRotate = false;
}, { passive:false });

canvas.addEventListener('mousedown', e => { isDragging=true; lastMX=e.clientX; lastMY=e.clientY; autoRotate=false; });
window.addEventListener('mouseup', () => isDragging=false);
window.addEventListener('mousemove', e => {
  if(!isDragging) return;
  const dx = e.clientX - lastMX, dy = e.clientY - lastMY;
  targetRotY += dx * 0.008;
  targetRotX += dy * 0.008;
  lastMX=e.clientX; lastMY=e.clientY;
});

canvas.addEventListener('touchstart', e => { isDragging=true; lastMX=e.touches[0].clientX; lastMY=e.touches[0].clientY; autoRotate=false; });
window.addEventListener('touchend', () => isDragging=false);
window.addEventListener('touchmove', e => {
  if(!isDragging) return;
  const dx = e.touches[0].clientX - lastMX, dy = e.touches[0].clientY - lastMY;
  targetRotY += dx * 0.008;
  targetRotX += dy * 0.008;
  lastMX=e.touches[0].clientX; lastMY=e.touches[0].clientY;
});

// 3D Transform helpers
function rotatePoint(x, y, z, rx, ry, rz) {
  // Rotate around X
  let y2 = y*Math.cos(rx) - z*Math.sin(rx);
  let z2 = y*Math.sin(rx) + z*Math.cos(rx);
  // Rotate around Y
  let x3 = x*Math.cos(ry) + z2*Math.sin(ry);
  let z3 = -x*Math.sin(ry) + z2*Math.cos(ry);
  // Rotate around Z
  let x4 = x3*Math.cos(rz) - y2*Math.sin(rz);
  let y4 = x3*Math.sin(rz) + y2*Math.cos(rz);
  return [x4, y4, z3];
}

function project(x, y, z) {
  const fov = 600;
  const dz = fov + z;
  return [ x * fov / dz, y * fov / dz, dz ];
}

// Build DNA helix geometry
function buildDNA() {
  const bases = DNA_SEQ.split('');
  const N = bases.length;
  const helixRadius = 80;
  const helixPitch = 22; // vertical spacing per bp
  const bpPerTurn = 10.5; // ~10.5 bp per turn (B-DNA)
  const totalHeight = N * helixPitch;
  const startY = -totalHeight / 2;

  const points = [];
  for(let i = 0; i < N; i++) {
    const base = bases[i];
    const comp = COMPLEMENT[base];
    const angle = (i / bpPerTurn) * Math.PI * 2;
    const y = startY + i * helixPitch;

    // Strand 1 phosphate backbone
    const s1x = helixRadius * Math.cos(angle);
    const s1z = helixRadius * Math.sin(angle);
    // Strand 2 phosphate backbone (opposite)
    const s2x = helixRadius * Math.cos(angle + Math.PI);
    const s2z = helixRadius * Math.sin(angle + Math.PI);

    points.push({
      i, base, comp, angle, y,
      s1: [s1x, y, s1z],
      s2: [s2x, y, s2z],
      mid: [0, y, 0]
    });
  }
  return points;
}

const dnaPoints = buildDNA();
const N = dnaPoints.length;

// Draw glow circle
function drawGlowCircle(ctx, x, y, r, color, alpha=0.8) {
  const grad = ctx.createRadialGradient(x, y, 0, x, y, r);
  grad.addColorStop(0, color.replace(')', `,${alpha})`).replace('rgb(','rgba('));
  grad.addColorStop(1, color.replace(')', ',0)').replace('rgb(','rgba('));
  ctx.beginPath();
  ctx.arc(x, y, r, 0, Math.PI*2);
  ctx.fillStyle = grad;
  ctx.fill();
}

// Base colors
const baseColors = { A:'#00ffaa', T:'#ff4466', C:'#4488ff', G:'#ffcc00' };
const baseGlow = { A:'rgba(0,255,170', T:'rgba(255,68,102', C:'rgba(68,136,255', G:'rgba(255,204,0' };

function drawScene() {
  ctx3d.clearRect(0, 0, canvas.width, canvas.height);

  // Smooth rotation/zoom
  rotX += (targetRotX - rotX) * 0.08;
  rotY += (targetRotY - rotY) * 0.08;
  zoom += (targetZoom - zoom) * 0.08;
  if(autoRotate) targetRotY += 0.004;

  const cx = canvas.width / 2;
  const cy = canvas.height / 2 + 20;
  const sc = zoom * (canvas.height / 900);

  // Collect projected points with depth
  const projected = dnaPoints.map(pt => {
    const [rx1, ry1, rz1] = rotatePoint(pt.s1[0], pt.s1[1], pt.s1[2], rotX, rotY, rotZ);
    const [rx2, ry2, rz2] = rotatePoint(pt.s2[0], pt.s2[1], pt.s2[2], rotX, rotY, rotZ);
    const [rmx, rmy, rmz] = rotatePoint(pt.mid[0], pt.mid[1], pt.mid[2], rotX, rotY, rotZ);
    const [px1, py1, pdz1] = project(rx1*sc, ry1*sc, rz1*sc);
    const [px2, py2, pdz2] = project(rx2*sc, ry2*sc, rz2*sc);
    const [pmx, pmy] = project(rmx*sc, rmy*sc, rmz*sc);
    return {
      ...pt,
      px1: cx+px1, py1: cy+py1, dz1: pdz1,
      px2: cx+px2, py2: cy+py2, dz2: pdz2,
      pmx: cx+pmx, pmy: cy+pmy,
      avgZ: (pdz1+pdz2)/2
    };
  });

  // Sort by depth (back to front for backbone rendering)
  const sorted = [...projected].sort((a,b) => b.avgZ - a.avgZ);

  // Draw backbone segments (back layer first)
  // Draw strand 1 backbone
  for(let i=0; i<N-1; i++) {
    const a = projected[i], b = projected[i+1];
    const depthFade = Math.max(0.1, Math.min(1, (a.dz1-400)/400));
    ctx3d.beginPath();
    ctx3d.moveTo(a.px1, a.py1);
    ctx3d.lineTo(b.px1, b.py1);
    ctx3d.strokeStyle = `rgba(0,180,120,${0.35*depthFade})`;
    ctx3d.lineWidth = 3*sc;
    ctx3d.stroke();
  }

  // Draw strand 2 backbone
  for(let i=0; i<N-1; i++) {
    const a = projected[i], b = projected[i+1];
    const depthFade = Math.max(0.1, Math.min(1, (a.dz2-400)/400));
    ctx3d.beginPath();
    ctx3d.moveTo(a.px2, a.py2);
    ctx3d.lineTo(b.px2, b.py2);
    ctx3d.strokeStyle = `rgba(0,120,200,${0.35*depthFade})`;
    ctx3d.lineWidth = 3*sc;
    ctx3d.stroke();
  }

  // Draw base pairs (rungs) + atoms - sorted by depth
  sorted.forEach(pt => {
    const { i, base, comp, px1, py1, dz1, px2, py2, dz2, pmx, pmy } = pt;
    const isHighlighted = i === highlightBase;
    const depthFactor = Math.max(0.15, Math.min(1, (dz1-400)/400));
    const baseCol = baseColors[base];
    const compCol = baseColors[comp];
    const baseGlowC = baseGlow[base];
    const compGlowC = baseGlow[comp];

    const r = isHighlighted ? 18*sc : 10*sc;
    const glowR = isHighlighted ? 34*sc : 18*sc;
    const alpha = isHighlighted ? 1 : depthFactor;

    // Rung line (base pair bond)
    const rungGrad = ctx3d.createLinearGradient(px1, py1, px2, py2);
    rungGrad.addColorStop(0, `${baseCol}${Math.floor(alpha*180).toString(16).padStart(2,'0')}`);
    rungGrad.addColorStop(0.5, `rgba(255,255,255,${alpha*0.2})`);
    rungGrad.addColorStop(1, `${compCol}${Math.floor(alpha*180).toString(16).padStart(2,'0')}`);
    ctx3d.beginPath();
    ctx3d.moveTo(px1, py1);
    ctx3d.lineTo(px2, py2);
    ctx3d.strokeStyle = rungGrad;
    ctx3d.lineWidth = isHighlighted ? 3*sc : 1.5*sc;
    ctx3d.stroke();

    // Small dots along rung for H-bonds
    const bonds = (base==='C'||base==='G') ? 3 : 2;
    for(let b=0; b<bonds; b++) {
      const t = (b+1) / (bonds+1);
      const bx = px1 + (px2-px1)*t;
      const by = py1 + (py2-py1)*t;
      ctx3d.beginPath();
      ctx3d.arc(bx, by, 2.5*sc, 0, Math.PI*2);
      ctx3d.fillStyle = `rgba(255,255,255,${alpha*0.5})`;
      ctx3d.fill();
    }

    // Strand 1 atom glow
    if(isHighlighted) {
      const g = ctx3d.createRadialGradient(px1, py1, 0, px1, py1, glowR);
      g.addColorStop(0, `${baseCol}88`); g.addColorStop(1, `${baseCol}00`);
      ctx3d.beginPath(); ctx3d.arc(px1, py1, glowR, 0, Math.PI*2);
      ctx3d.fillStyle = g; ctx3d.fill();
    }

    // Strand 1 base sphere
    const g1 = ctx3d.createRadialGradient(px1-r*0.3, py1-r*0.3, 0, px1, py1, r);
    g1.addColorStop(0, `rgba(255,255,255,${alpha*0.9})`);
    g1.addColorStop(0.3, `${baseCol}${Math.floor(alpha*220).toString(16).padStart(2,'0')}`);
    g1.addColorStop(1, `${baseGlowC},${alpha*0.5})`);
    ctx3d.beginPath();
    ctx3d.arc(px1, py1, r, 0, Math.PI*2);
    ctx3d.fillStyle = g1;
    ctx3d.fill();

    if(isHighlighted) {
      ctx3d.strokeStyle = baseCol;
      ctx3d.lineWidth = 2;
      ctx3d.stroke();
    }

    // Strand 2 base sphere
    if(isHighlighted) {
      const g2g = ctx3d.createRadialGradient(px2, py2, 0, px2, py2, glowR);
      g2g.addColorStop(0, `${compCol}88`); g2g.addColorStop(1, `${compCol}00`);
      ctx3d.beginPath(); ctx3d.arc(px2, py2, glowR, 0, Math.PI*2);
      ctx3d.fillStyle = g2g; ctx3d.fill();
    }

    const g2 = ctx3d.createRadialGradient(px2-r*0.3, py2-r*0.3, 0, px2, py2, r);
    g2.addColorStop(0, `rgba(255,255,255,${alpha*0.9})`);
    g2.addColorStop(0.3, `${compCol}${Math.floor(alpha*220).toString(16).padStart(2,'0')}`);
    g2.addColorStop(1, `${compGlowC},${alpha*0.5})`);
    ctx3d.beginPath();
    ctx3d.arc(px2, py2, r, 0, Math.PI*2);
    ctx3d.fillStyle = g2;
    ctx3d.fill();

    if(isHighlighted) {
      ctx3d.strokeStyle = compCol;
      ctx3d.lineWidth = 2;
      ctx3d.stroke();
    }

    // Base labels (only if large enough / highlighted)
    const fontSize = Math.max(6, 10*sc);
    if(r > 6 || isHighlighted) {
      ctx3d.font = `bold ${isHighlighted ? fontSize*1.4 : fontSize}px 'Share Tech Mono', monospace`;
      ctx3d.textAlign = 'center';
      ctx3d.textBaseline = 'middle';
      ctx3d.fillStyle = `rgba(0,0,0,${alpha*0.85})`;
      ctx3d.fillText(base, px1, py1);
      ctx3d.fillText(comp, px2, py2);
    }
  });

  // Major/minor groove indicator arcs (decorative)
  const grooveAlpha = 0.04;
  for(let i=0; i<N-1; i+=5) {
    const pt = projected[i];
    ctx3d.beginPath();
    ctx3d.arc(pt.pmx, pt.pmy, 90*sc, 0, Math.PI*2);
    ctx3d.strokeStyle = `rgba(0,200,150,${grooveAlpha})`;
    ctx3d.lineWidth = 1;
    ctx3d.stroke();
  }

  frame++;
  requestAnimationFrame(drawScene);
}

drawScene();
</script>
</body>
</html>
