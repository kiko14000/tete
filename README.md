<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Carnet de Thomas — Plan d'entraînement</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@500;600;700&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1B1B1F;
    --paper:#F6F4EF;
    --paper-raised:#FFFFFF;
    --ember:#E1622C;
    --zone-blue:#2C4A66;
    --track-red:#C23B3B;
    --moss:#4F7857;
    --line:#DAD4C6;
    --muted:#8A8473;
    --radius:14px;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--paper);
    color:var(--ink);
    font-family:'Inter',sans-serif;
    -webkit-font-smoothing:antialiased;
    min-height:100vh;
    padding-bottom:60px;
  }
  .wrap{max-width:680px;margin:0 auto;padding:0 16px;}

  /* ---------- Header ---------- */
  header.app-header{
    position:sticky;top:0;z-index:30;
    background:var(--paper);
    border-bottom:2px solid var(--ink);
    padding-top:18px;
  }
  .brand{display:flex;align-items:baseline;justify-content:space-between;gap:8px;margin-bottom:14px;}
  .brand-text .eyebrow{
    font-family:'JetBrains Mono',monospace;
    font-size:11px;letter-spacing:.12em;text-transform:uppercase;color:var(--ember);font-weight:600;
  }
  .brand-text h1{
    font-family:'Oswald',sans-serif;
    font-size:26px;font-weight:700;letter-spacing:.01em;text-transform:uppercase;margin:2px 0 0;line-height:1;
  }
  .gear-btn{
    background:none;border:none;font-size:20px;cursor:pointer;padding:6px;line-height:1;
    color:var(--ink);
  }
  .tabs{display:flex;gap:0;}
  .tab-btn{
    flex:1;background:none;border:none;cursor:pointer;
    font-family:'Oswald',sans-serif;font-size:14px;letter-spacing:.06em;text-transform:uppercase;font-weight:600;
    color:var(--muted);padding:10px 4px 12px;border-bottom:3px solid transparent;
  }
  .tab-btn.active{color:var(--ink);border-bottom-color:var(--ember);}

  main{padding-top:18px;}

  /* ---------- Empty state ---------- */
  .empty-state{
    text-align:center;padding:60px 20px;border:2px dashed var(--line);border-radius:var(--radius);margin-top:20px;
  }
  .empty-state .big-emoji{font-size:38px;display:block;margin-bottom:10px;}
  .empty-state h2{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:18px;margin:0 0 6px;}
  .empty-state p{color:var(--muted);font-size:14px;margin:0 0 18px;}

  /* ---------- Buttons ---------- */
  .btn{
    font-family:'Inter',sans-serif;font-weight:600;font-size:14px;
    border-radius:9px;border:2px solid var(--ink);padding:10px 16px;cursor:pointer;
    background:var(--paper-raised);color:var(--ink);
  }
  .btn:active{transform:translateY(1px);}
  .btn-primary{background:var(--ink);color:var(--paper-raised);}
  .btn-ember{background:var(--ember);border-color:var(--ember);color:#fff;}
  .btn-ghost{border-color:var(--line);}
  .btn-sm{padding:6px 11px;font-size:12.5px;border-radius:7px;}
  .btn-block{width:100%;}
  .btn-danger{border-color:var(--track-red);color:var(--track-red);}
  .btn[disabled]{opacity:.4;cursor:not-allowed;}

  /* ---------- Week header / recap ---------- */
  .week-title-row{display:flex;align-items:flex-end;justify-content:space-between;gap:10px;margin-bottom:6px;flex-wrap:wrap;}
  .week-title-row h2{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:21px;margin:0;}
  .week-range{font-family:'JetBrains Mono',monospace;color:var(--muted);font-size:12.5px;margin:0 0 16px;}
  .week-select{
    font-family:'JetBrains Mono',monospace;font-size:12.5px;border:2px solid var(--line);border-radius:8px;
    background:var(--paper-raised);padding:6px 8px;color:var(--ink);
  }

  .recap-card{
    background:var(--paper-raised);border:2px solid var(--ink);border-radius:var(--radius);
    padding:16px;margin-bottom:22px;
  }
  .recap-head{display:flex;justify-content:space-between;align-items:baseline;margin-bottom:12px;}
  .recap-head .label{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:13px;letter-spacing:.06em;}
  .recap-head .pct{font-family:'JetBrains Mono',monospace;font-size:13px;color:var(--ember);font-weight:600;}
  .recap-row{display:flex;align-items:center;gap:10px;margin-bottom:8px;font-size:12.5px;}
  .recap-row .ricon{width:20px;text-align:center;}
  .recap-row .rlabel{width:74px;flex-shrink:0;color:var(--ink);font-weight:500;}
  .recap-bar-bg{flex:1;height:8px;background:var(--paper);border:1px solid var(--line);border-radius:5px;overflow:hidden;position:relative;}
  .recap-bar-fill{height:100%;border-radius:5px;}
  .recap-row .rval{font-family:'JetBrains Mono',monospace;width:78px;text-align:right;flex-shrink:0;color:var(--muted);}
  .recap-total{display:flex;justify-content:space-between;border-top:1px dashed var(--line);margin-top:10px;padding-top:10px;
    font-family:'JetBrains Mono',monospace;font-size:13px;font-weight:600;}

  /* ---------- Day ticket card ---------- */
  .day-card{
    position:relative;background:var(--paper-raised);border:2px solid var(--ink);border-radius:var(--radius);
    margin-bottom:18px;padding:16px 16px 14px 18px;overflow:visible;
  }
  .day-card.skipped{opacity:.55;}
  .day-card .top-bar{
    position:absolute;top:-2px;left:10px;right:10px;height:4px;border-radius:0 0 3px 3px;
  }
  .bib{
    position:absolute;top:-14px;left:-10px;width:34px;height:34px;border-radius:50%;
    background:var(--paper-raised);border:2px solid var(--ink);
    display:flex;align-items:center;justify-content:center;
    font-family:'JetBrains Mono',monospace;font-weight:700;font-size:13px;
    transform:rotate(-6deg);box-shadow:2px 2px 0 var(--ink);
  }
  .day-card-head{display:flex;justify-content:space-between;align-items:flex-start;gap:10px;margin-left:18px;}
  .day-name-line{display:flex;align-items:center;gap:7px;flex-wrap:wrap;}
  .day-name{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:17px;font-weight:700;}
  .day-date{font-family:'JetBrains Mono',monospace;font-size:11.5px;color:var(--muted);}
  .sport-icon{font-size:16px;}
  .status-pill{
    font-family:'JetBrains Mono',monospace;font-size:10.5px;text-transform:uppercase;letter-spacing:.04em;
    padding:3px 8px;border-radius:20px;font-weight:600;white-space:nowrap;flex-shrink:0;
  }
  .status-todo{background:#EFE9DD;color:var(--muted);}
  .status-done{background:var(--moss);color:#fff;}
  .status-rescheduled{background:var(--zone-blue);color:#fff;}
  .status-skipped{background:var(--track-red);color:#fff;}

  .day-title{
    font-weight:600;font-size:14.5px;margin:8px 0 4px;margin-left:18px;
  }
  .day-detail{
    font-family:'JetBrains Mono',monospace;font-size:12.8px;line-height:1.55;color:#3a3a3a;
    margin:0 0 10px;margin-left:18px;white-space:pre-wrap;
  }
  .hl-ember{color:var(--ember);font-weight:600;}
  .hl-blue{color:var(--zone-blue);font-weight:600;}
  .reschedule-tag{
    font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--zone-blue);margin:0 0 8px;margin-left:18px;
  }

  .action-row{display:flex;gap:8px;margin-left:18px;flex-wrap:wrap;}
  .inline-form{
    margin:10px 0 0 18px;padding:12px;background:var(--paper);border:1.5px dashed var(--line);border-radius:10px;
  }
  .inline-form label{display:block;font-size:11.5px;color:var(--muted);margin:8px 0 3px;font-weight:600;}
  .inline-form label:first-child{margin-top:0;}
  .inline-form input[type=date], .inline-form input[type=text], .inline-form input[type=number], .inline-form select, .inline-form textarea{
    width:100%;padding:8px 9px;border:1.5px solid var(--line);border-radius:7px;font-family:'Inter',sans-serif;font-size:13.5px;background:#fff;color:var(--ink);
  }
  .inline-form textarea{font-family:'JetBrains Mono',monospace;font-size:12.5px;resize:vertical;min-height:54px;}
  .inline-actions{display:flex;gap:8px;margin-top:10px;}

  /* feedback */
  .feedback-toggle{
    margin:8px 0 0 18px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--ember);background:none;border:none;
    cursor:pointer;padding:0;font-weight:600;
  }
  .feedback-summary{margin:8px 0 0 18px;font-size:12.5px;color:var(--muted);display:flex;align-items:center;gap:6px;flex-wrap:wrap;}
  .diff-badge{
    font-family:'JetBrains Mono',monospace;font-weight:700;font-size:11px;color:#fff;background:var(--track-red);
    padding:2px 7px;border-radius:5px;
  }
  .chip-row{display:flex;flex-wrap:wrap;gap:6px;margin-top:4px;}
  .chip{
    font-size:12px;padding:5px 10px;border-radius:20px;border:1.5px solid var(--line);background:#fff;cursor:pointer;color:var(--ink);
  }
  .chip.selected{background:var(--ink);color:#fff;border-color:var(--ink);}
  .range-row{display:flex;align-items:center;gap:10px;}
  .range-row input[type=range]{flex:1;}
  .range-val{font-family:'JetBrains Mono',monospace;font-weight:700;width:28px;text-align:center;}

  .add-day-trigger{
    width:100%;border:2px dashed var(--line);background:none;border-radius:var(--radius);padding:14px;
    font-family:'Oswald',sans-serif;text-transform:uppercase;letter-spacing:.05em;font-size:13px;color:var(--muted);
    cursor:pointer;margin-bottom:30px;
  }
  .add-day-trigger:hover{border-color:var(--ember);color:var(--ember);}

  /* ---------- History ---------- */
  .history-card{
    background:var(--paper-raised);border:2px solid var(--ink);border-radius:var(--radius);padding:14px 16px;
    margin-bottom:12px;cursor:pointer;
  }
  .history-card:hover{border-color:var(--ember);}
  .history-top{display:flex;justify-content:space-between;align-items:baseline;}
  .history-top .htitle{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:16px;font-weight:700;}
  .history-top .hpct{font-family:'JetBrains Mono',monospace;font-weight:700;color:var(--ember);}
  .history-range{font-family:'JetBrains Mono',monospace;font-size:11.5px;color:var(--muted);margin:2px 0 8px;}
  .history-bar-bg{height:6px;background:var(--paper);border-radius:4px;overflow:hidden;border:1px solid var(--line);}
  .history-bar-fill{height:100%;background:var(--moss);}

  /* ---------- Modal ---------- */
  .modal-overlay{
    position:fixed;inset:0;background:rgba(27,27,31,.55);z-index:50;display:flex;align-items:flex-end;justify-content:center;
  }
  .modal-box{
    background:var(--paper);width:100%;max-width:680px;max-height:88vh;overflow-y:auto;
    border-radius:18px 18px 0 0;padding:18px 18px 26px;border-top:3px solid var(--ink);
  }
  @media (min-width:700px){
    .modal-overlay{align-items:center;}
    .modal-box{border-radius:18px;max-height:84vh;}
  }
  .modal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;}
  .modal-head h3{font-family:'Oswald',sans-serif;text-transform:uppercase;font-size:18px;margin:0;}
  .close-x{background:none;border:none;font-size:22px;cursor:pointer;color:var(--ink);line-height:1;}
  .field-group{margin-bottom:12px;}
  .field-group label{display:block;font-size:12px;font-weight:600;color:var(--muted);margin-bottom:4px;}
  .field-group input, .field-group select, .field-group textarea{
    width:100%;padding:9px 10px;border:1.5px solid var(--line);border-radius:8px;font-family:'Inter',sans-serif;font-size:14px;background:#fff;
  }
  .two-col{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
  .pending-day-row{
    display:flex;justify-content:space-between;align-items:center;background:#fff;border:1.5px solid var(--line);
    border-radius:9px;padding:8px 11px;margin-bottom:8px;font-size:13px;
  }
  .pending-day-row .pdr-x{background:none;border:none;color:var(--track-red);cursor:pointer;font-size:16px;}
  hr.sep{border:none;border-top:1.5px dashed var(--line);margin:18px 0;}

  .toast{
    position:fixed;bottom:18px;left:50%;transform:translateX(-50%);background:var(--ink);color:#fff;
    padding:10px 18px;border-radius:30px;font-size:13px;z-index:80;box-shadow:0 6px 18px rgba(0,0,0,.25);
  }
</style>
</head>
<body>
<header class="app-header">
  <div class="wrap">
    <div class="brand">
      <div class="brand-text">
        <div class="eyebrow">Plan coach → carnet</div>
        <h1>Carnet de Thomas</h1>
      </div>
      <button class="gear-btn" id="gearBtn" title="Réglages">⚙</button>
    </div>
    <div class="tabs">
      <button class="tab-btn active" data-tab="semaine">Semaine</button>
      <button class="tab-btn" data-tab="historique">Historique</button>
    </div>
  </div>
</header>

<main class="wrap" id="mainView"></main>

<div id="modalRoot"></div>
<div id="toastRoot"></div>

<script src="https://cdn.jsdelivr.net/npm/tesseract.js@5/dist/tesseract.min.js"></script>
<script>
/* =========================================================
   DATA LAYER
========================================================= */
const STORAGE_KEY = 'thomas_carnet_v1';
const SPORTS = {
  course:  { label:'Athlétisme', icon:'🏃', color:'#E1622C' },
  velo:    { label:'Vélo',       icon:'🚴', color:'#2C4A66' },
  natation:{ label:'Natation',   icon:'🏊', color:'#4F7857' },
  ppg:     { label:'PPG',        icon:'💪', color:'#C23B3B' },
  repos:   { label:'Repos',      icon:'😴', color:'#8A8473' },
  autre:   { label:'Autre',      icon:'⚡', color:'#1B1B1F' }
};
const SENSATIONS = ['Bonnes sensations','Jambes lourdes','Essoufflé','Fatigue générale','Douleur / gêne','Forme du jour','Manque de sommeil','Météo difficile'];

function loadData(){
  try{
    const raw = localStorage.getItem(STORAGE_KEY);
    if(!raw) return { weeks: [], activeWeekId: null };
    const parsed = JSON.parse(raw);
    if(!parsed.weeks) parsed.weeks = [];
    return parsed;
  }catch(e){ return { weeks: [], activeWeekId: null }; }
}
function saveData(){ localStorage.setItem(STORAGE_KEY, JSON.stringify(data)); }
function uid(){ return Date.now().toString(36) + Math.random().toString(36).slice(2,7); }

let data = loadData();
let currentTab = 'semaine';
let editingDayId = null;       // day currently in edit mode
let reschedulingDayId = null;  // day currently showing reschedule panel
let feedbackOpenId = null;     // day currently showing feedback form
let pendingNewDays = [];       // days staged in "new week" modal

/* =========================================================
   HELPERS
========================================================= */
function escapeHtml(str){
  const d = document.createElement('div');
  d.textContent = str || '';
  return d.innerHTML;
}
function highlightDetail(text){
  let t = escapeHtml(text || '');
  t = t.replace(/(-?\d+(?:\/\d+)?\s?bpm)/gi, '<span class="hl-blue">$1</span>');
  t = t.replace(/(\d+['’]\d+["”]?(?:\s?\/\s?\d+['’]\d+["”]?)?)/g, '<span class="hl-ember">$1</span>');
  t = t.replace(/(\b\d+\s?x\b|\b\d+\s?m\b)/gi, '<span class="hl-ember">$1</span>');
  t = t.replace(/\b(z[1-5][+-]?)\b/gi, '<span class="hl-blue">$1</span>');
  return t.replace(/\n/g,'<br>');
}
function getActiveWeek(){
  return data.weeks.find(w => w.id === data.activeWeekId) || null;
}
function sortedWeeks(){
  return [...data.weeks].sort((a,b)=> (b.createdAt||0) - (a.createdAt||0));
}
function sortDays(days){
  return [...days].sort((a,b)=>{
    if(a.date && b.date) return a.date.localeCompare(b.date);
    if(a.date) return -1;
    if(b.date) return 1;
    return 0;
  });
}
function showToast(msg){
  const root = document.getElementById('toastRoot');
  root.innerHTML = '<div class="toast">'+escapeHtml(msg)+'</div>';
  setTimeout(()=>{ root.innerHTML=''; }, 2200);
}

/* =========================================================
   RENDER: ROOT
========================================================= */
function render(){
  document.querySelectorAll('.tab-btn').forEach(b=>{
    b.classList.toggle('active', b.dataset.tab === currentTab);
  });
  const main = document.getElementById('mainView');
  if(currentTab === 'semaine'){
    main.innerHTML = renderWeekTab();
  }else{
    main.innerHTML = renderHistoryTab();
  }
}

function renderWeekTab(){
  if(data.weeks.length === 0){
    return `
      <div class="empty-state">
        <span class="big-emoji">🏁</span>
        <h2>Pas encore de semaine</h2>
        <p>Recopie le programme envoyé par le coach, ou scanne directement la photo.</p>
        <button class="btn btn-ember" data-action="open-new-week">+ Créer la première semaine</button>
      </div>`;
  }
  const week = getActiveWeek() || sortedWeeks()[0];
  if(week && data.activeWeekId !== week.id){ data.activeWeekId = week.id; saveData(); }
  const weeks = sortedWeeks();
  const days = sortDays(week.days);

  let html = `
    <div class="week-title-row">
      <div>
        <h2>${escapeHtml(week.title)}</h2>
        <div class="week-range">${escapeHtml(week.dateRange||'')}</div>
      </div>
      <select class="week-select" id="weekSelect">
        ${weeks.map(w=>`<option value="${w.id}" ${w.id===week.id?'selected':''}>${escapeHtml(w.title)}</option>`).join('')}
      </select>
    </div>
  `;

  html += renderRecap(week);

  if(days.length === 0){
    html += `<p style="color:var(--muted);font-size:13.5px;">Aucune séance ajoutée pour l'instant.</p>`;
  }else{
    days.forEach((day, idx)=>{ html += renderDayCard(day, week.id, idx); });
  }

  html += `<button class="add-day-trigger" data-action="open-add-day" data-week="${week.id}">+ Ajouter une séance à cette semaine</button>`;
  html += `<button class="btn btn-ember btn-block" data-action="open-new-week" style="margin-bottom:24px;">+ Nouvelle semaine</button>`;

  return html;
}

function renderRecap(week){
  const totals = {};
  Object.keys(SPORTS).forEach(k=> totals[k]={planned:0, done:0});
  let doneCount=0;
  week.days.forEach(d=>{
    const s = totals[d.sport] ? d.sport : 'autre';
    totals[s].planned += Number(d.duration)||0;
    if(d.status==='done'){ totals[s].done += Number(d.duration)||0; doneCount++; }
  });
  const maxPlanned = Math.max(0.01, ...Object.values(totals).map(t=>t.planned));
  let totalPlanned=0, totalDone=0;
  let rows = '';
  Object.keys(SPORTS).forEach(k=>{
    const t = totals[k];
    if(t.planned===0) return;
    totalPlanned += t.planned; totalDone += t.done;
    const widthPct = Math.round((t.planned/maxPlanned)*100);
    const donePct = t.planned>0 ? Math.round((t.done/t.planned)*100) : 0;
    rows += `
      <div class="recap-row">
        <span class="ricon">${SPORTS[k].icon}</span>
        <span class="rlabel">${SPORTS[k].label}</span>
        <span class="recap-bar-bg" style="width:${widthPct}%;max-width:${widthPct}%;flex:0 0 auto;">
          <span class="recap-bar-fill" style="width:${donePct}%;background:${SPORTS[k].color};"></span>
        </span>
        <span class="rval">${t.done.toFixed(1)}h / ${t.planned.toFixed(1)}h</span>
      </div>`;
  });
  const pct = week.days.length ? Math.round((doneCount/week.days.length)*100) : 0;
  return `
    <div class="recap-card">
      <div class="recap-head">
        <span class="label">Charge de la semaine</span>
        <span class="pct">${pct}% réalisé</span>
      </div>
      ${rows || '<p style="color:var(--muted);font-size:13px;margin:0;">Ajoute des séances pour voir le récap.</p>'}
      <div class="recap-total">
        <span>Total</span><span>${totalDone.toFixed(1)}h / ${totalPlanned.toFixed(1)}h</span>
      </div>
    </div>`;
}

function renderDayCard(day, weekId, idx){
  const sport = SPORTS[day.sport] || SPORTS.autre;
  const statusLabel = { todo:'À faire', done:'Fait', rescheduled:'Reporté', skipped:'Non réalisée' }[day.status] || 'À faire';

  if(editingDayId === day.id){
    return renderDayEditForm(day, weekId);
  }

  let inner = `
    <div class="day-card ${day.status==='skipped'?'skipped':''}">
      <div class="top-bar" style="background:${sport.color}"></div>
      <div class="bib">${String(idx+1).padStart(2,'0')}</div>
      <div class="day-card-head">
        <div class="day-name-line">
          <span class="sport-icon">${sport.icon}</span>
          <span class="day-name">${escapeHtml(day.day||'Jour')}</span>
          ${day.date?`<span class="day-date">${formatDate(day.date)}</span>`:''}
        </div>
        <span class="status-pill status-${day.status}">${statusLabel}</span>
      </div>
      <div class="day-title">${escapeHtml(day.title||'')}${day.duration?` <span style="color:var(--muted);font-weight:400;">(${Number(day.duration).toFixed(2).replace(/\.?0+$/,'')}h)</span>`:''}</div>
      ${day.detail ? `<div class="day-detail">${highlightDetail(day.detail)}</div>` : ''}
      ${day.rescheduledFrom ? `<div class="reschedule-tag">↪ reporté depuis le ${formatDate(day.rescheduledFrom)}</div>` : ''}
  `;

  // status action row
  if(day.status === 'todo'){
    inner += `
      <div class="action-row">
        <button class="btn btn-sm" data-action="mark-done" data-id="${day.id}">✓ Fait</button>
        <button class="btn btn-sm btn-ghost" data-action="mark-notdone" data-id="${day.id}">✗ Pas fait</button>
        <button class="btn btn-sm btn-ghost" data-action="edit-day" data-id="${day.id}">✏️</button>
        <button class="btn btn-sm btn-danger" data-action="delete-day" data-id="${day.id}">🗑</button>
      </div>`;
  } else if(day.status === 'done'){
    inner += `
      <div class="action-row">
        <button class="btn btn-sm btn-ghost" data-action="mark-todo" data-id="${day.id}">↺ Annuler "fait"</button>
        <button class="btn btn-sm btn-ghost" data-action="edit-day" data-id="${day.id}">✏️</button>
      </div>`;
    inner += renderFeedbackBlock(day);
  } else if(day.status === 'rescheduled'){
    inner += `
      <div class="action-row">
        <button class="btn btn-sm" data-action="mark-done" data-id="${day.id}">✓ Marquer fait</button>
        <button class="btn btn-sm btn-ghost" data-action="mark-todo" data-id="${day.id}">↺ Annuler le report</button>
      </div>`;
  } else if(day.status === 'skipped'){
    inner += `
      <div class="action-row">
        <button class="btn btn-sm btn-ghost" data-action="mark-todo" data-id="${day.id}">↺ Réactiver</button>
        <button class="btn btn-sm btn-danger" data-action="delete-day" data-id="${day.id}">🗑</button>
      </div>`;
  }

  if(reschedulingDayId === day.id){
    inner += `
      <div class="inline-form">
        <label>Reprogrammer pour le</label>
        <input type="date" id="reschedDate_${day.id}">
        <div class="inline-actions">
          <button class="btn btn-sm btn-primary" data-action="confirm-reschedule" data-id="${day.id}">Reprogrammer</button>
          <button class="btn btn-sm btn-danger" data-action="confirm-skip" data-id="${day.id}">Annuler définitivement</button>
          <button class="btn btn-sm btn-ghost" data-action="cancel-reschedule" data-id="${day.id}">Annuler</button>
        </div>
      </div>`;
  }

  inner += `</div>`;
  return inner;
}

function renderFeedbackBlock(day){
  const fb = day.feedback || {};
  const hasFeedback = fb.difficulty || (fb.sensations && fb.sensations.length) || fb.notes;

  if(feedbackOpenId !== day.id){
    if(hasFeedback){
      return `
        <div class="feedback-summary">
          ${fb.difficulty?`<span class="diff-badge">${fb.difficulty}/10</span>`:''}
          ${(fb.sensations||[]).map(s=>`<span>· ${escapeHtml(s)}</span>`).join('')}
          <button class="feedback-toggle" data-action="open-feedback" data-id="${day.id}">modifier l'avis ›</button>
        </div>`;
    }
    return `<button class="feedback-toggle" data-action="open-feedback" data-id="${day.id}">+ Donner son avis sur la séance ›</button>`;
  }

  const diff = fb.difficulty || 5;
  return `
    <div class="inline-form">
      <label>Difficulté ressentie (1 = facile, 10 = très dur)</label>
      <div class="range-row">
        <input type="range" min="1" max="10" value="${diff}" id="diffRange_${day.id}" oninput="document.getElementById('diffVal_${day.id}').textContent=this.value">
        <span class="range-val" id="diffVal_${day.id}">${diff}</span>
      </div>
      <label>Sensations</label>
      <div class="chip-row" id="chipRow_${day.id}">
        ${SENSATIONS.map(s=>`<span class="chip ${(fb.sensations||[]).includes(s)?'selected':''}" data-sensation="${escapeHtml(s)}">${escapeHtml(s)}</span>`).join('')}
      </div>
      <label>Notes libres</label>
      <textarea id="notesArea_${day.id}" placeholder="Ressenti, douleurs, météo, contexte...">${escapeHtml(fb.notes||'')}</textarea>
      <div class="inline-actions">
        <button class="btn btn-sm btn-primary" data-action="save-feedback" data-id="${day.id}">💾 Enregistrer l'avis</button>
        <button class="btn btn-sm btn-ghost" data-action="close-feedback" data-id="${day.id}">Annuler</button>
      </div>
    </div>`;
}

function renderDayEditForm(day, weekId){
  return `
    <div class="day-card">
      <div class="top-bar" style="background:${(SPORTS[day.sport]||SPORTS.autre).color}"></div>
      <div class="inline-form" style="margin-left:0;">
        <label>Jour</label>
        <input type="text" id="edit_day_${day.id}" value="${escapeHtml(day.day||'')}">
        <label>Date</label>
        <input type="date" id="edit_date_${day.id}" value="${day.date||''}">
        <label>Sport</label>
        <select id="edit_sport_${day.id}">
          ${Object.keys(SPORTS).map(k=>`<option value="${k}" ${day.sport===k?'selected':''}>${SPORTS[k].icon} ${SPORTS[k].label}</option>`).join('')}
        </select>
        <label>Titre (ex: RPE MAX 7/10 - z4+ (1h10))</label>
        <input type="text" id="edit_title_${day.id}" value="${escapeHtml(day.title||'')}">
        <label>Durée prévue (en heures)</label>
        <input type="number" step="0.25" min="0" id="edit_duration_${day.id}" value="${day.duration||0}">
        <label>Détail de la séance</label>
        <textarea id="edit_detail_${day.id}">${escapeHtml(day.detail||'')}</textarea>
        <div class="inline-actions">
          <button class="btn btn-sm btn-primary" data-action="save-edit-day" data-id="${day.id}">💾 Enregistrer</button>
          <button class="btn btn-sm btn-ghost" data-action="cancel-edit-day" data-id="${day.id}">Annuler</button>
        </div>
      </div>
    </div>`;
}

function formatDate(iso){
  if(!iso) return '';
  const parts = iso.split('-');
  if(parts.length!==3) return iso;
  return `${parts[2]}/${parts[1]}`;
}

/* =========================================================
   RENDER: HISTORY TAB
========================================================= */
function renderHistoryTab(){
  if(data.weeks.length === 0){
    return `<div class="empty-state"><span class="big-emoji">📂</span><h2>Aucun historique</h2><p>Les semaines passées apparaîtront ici une fois créées.</p></div>`;
  }
  const weeks = sortedWeeks();
  let html = '';
  weeks.forEach(w=>{
    const total = w.days.length;
    const done = w.days.filter(d=>d.status==='done').length;
    const pct = total ? Math.round((done/total)*100) : 0;
    const hoursDone = w.days.filter(d=>d.status==='done').reduce((s,d)=>s+(Number(d.duration)||0),0);
    const hoursPlanned = w.days.reduce((s,d)=>s+(Number(d.duration)||0),0);
    html += `
      <div class="history-card" data-action="select-week" data-id="${w.id}">
        <div class="history-top">
          <span class="htitle">${escapeHtml(w.title)}</span>
          <span class="hpct">${pct}%</span>
        </div>
        <div class="history-range">${escapeHtml(w.dateRange||'')} · ${hoursDone.toFixed(1)}h / ${hoursPlanned.toFixed(1)}h · ${done}/${total} séances</div>
        <div class="history-bar-bg"><div class="history-bar-fill" style="width:${pct}%;"></div></div>
      </div>`;
  });
  return html;
}

/* =========================================================
   MODALS
========================================================= */
function openModal(html){
  document.getElementById('modalRoot').innerHTML = `<div class="modal-overlay" id="modalOverlay"><div class="modal-box">${html}</div></div>`;
  document.getElementById('modalOverlay').addEventListener('click', (e)=>{
    if(e.target.id === 'modalOverlay') closeModal();
  });
}
function closeModal(){ document.getElementById('modalRoot').innerHTML = ''; pendingNewDays = []; }

function openNewWeekModal(){
  pendingNewDays = [];
  renderNewWeekModal();
}
function renderNewWeekModal(){
  const html = `
    <div class="modal-head"><h3>Nouvelle semaine</h3><button class="close-x" data-action="close-modal">×</button></div>
    <div class="field-group" style="background:#fff;border:1.5px dashed var(--ember);border-radius:10px;padding:12px;">
      <label style="color:var(--ember);">📷 Scanner une photo du programme</label>
      <input type="file" accept="image/*" id="scanPhotoInput" style="margin-bottom:10px;">
      <label>Date du 1er jour scanné (optionnel — pour dater chaque séance)</label>
      <input type="date" id="scan_startdate">
      <div id="scanStatus" style="font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--ember);margin-top:8px;min-height:14px;"></div>
    </div>
    <hr class="sep">
    <div class="field-group">
      <label>Titre de la semaine</label>
      <input type="text" id="nw_title" placeholder="Ex: Semaine 25" value="${document.getElementById('nw_title')?document.getElementById('nw_title').value:''}">
    </div>
    <div class="field-group">
      <label>Plage de dates</label>
      <input type="text" id="nw_range" placeholder="Ex: Du 24 au 30 juin 2026" value="${document.getElementById('nw_range')?document.getElementById('nw_range').value:''}">
    </div>
    <hr class="sep">
    <div id="pendingDaysList">${renderPendingDaysList()}</div>
    <div id="newDayFormZone">${renderNewDayFields()}</div>
    <hr class="sep">
    <button class="btn btn-primary btn-block" data-action="save-new-week">✓ Enregistrer la semaine</button>
  `;
  openModal(html);
}
function renderPendingDaysList(){
  if(pendingNewDays.length===0) return '';
  return pendingNewDays.map((d,i)=>`
    <div class="pending-day-row">
      <span>${SPORTS[d.sport].icon} <strong>${escapeHtml(d.day)}</strong> — ${escapeHtml(d.title||d.detail.slice(0,40))}</span>
      <span>
        <button class="pdr-x" data-action="edit-pending-day" data-idx="${i}" style="color:var(--zone-blue);">✏️</button>
        <button class="pdr-x" data-action="remove-pending-day" data-idx="${i}">✕</button>
      </span>
    </div>`).join('');
}
function renderNewDayFields(){
  return `
    <div class="field-group two-col">
      <div><label>Jour</label><input type="text" id="nd_day" placeholder="Ex: Mercredi"></div>
      <div><label>Date</label><input type="date" id="nd_date"></div>
    </div>
    <div class="field-group two-col">
      <div><label>Sport</label>
        <select id="nd_sport">${Object.keys(SPORTS).map(k=>`<option value="${k}">${SPORTS[k].icon} ${SPORTS[k].label}</option>`).join('')}</select>
      </div>
      <div><label>Durée (h)</label><input type="number" step="0.25" min="0" id="nd_duration" placeholder="1.5"></div>
    </div>
    <div class="field-group">
      <label>Titre court</label>
      <input type="text" id="nd_title" placeholder="Ex: RPE MAX 7/10 - z4+ (1h10)">
    </div>
    <div class="field-group">
      <label>Détail de la séance</label>
      <textarea id="nd_detail" rows="3" placeholder="Ex: 1h10 z1 dont 20x 400m z4+ (1'24''/1'22'' et -178bpm) r100m en 35''"></textarea>
    </div>
    <button class="btn btn-ghost btn-block" data-action="add-pending-day">+ Ajouter ce jour à la semaine</button>
  `;
}
function addPendingDay(){
  const day = document.getElementById('nd_day').value.trim();
  const date = document.getElementById('nd_date').value;
  const sport = document.getElementById('nd_sport').value;
  const duration = parseFloat(document.getElementById('nd_duration').value)||0;
  const title = document.getElementById('nd_title').value.trim();
  const detail = document.getElementById('nd_detail').value.trim();
  if(!day && !title){ showToast('Ajoute au moins un jour ou un titre'); return; }
  pendingNewDays.push({ id: uid(), day: day||'Jour', date, sport, duration, title, detail, status:'todo', rescheduledFrom:null, feedback:{} });
  renderNewWeekModal();
}
function editPendingDay(idx){
  const d = pendingNewDays.splice(idx,1)[0];
  renderNewWeekModal();
  document.getElementById('nd_day').value = d.day || '';
  document.getElementById('nd_date').value = d.date || '';
  document.getElementById('nd_sport').value = SPORTS[d.sport] ? d.sport : 'autre';
  document.getElementById('nd_duration').value = d.duration || '';
  document.getElementById('nd_title').value = d.title || '';
  document.getElementById('nd_detail').value = d.detail || '';
}
function saveNewWeek(){
  const title = document.getElementById('nw_title').value.trim() || 'Nouvelle semaine';
  const dateRange = document.getElementById('nw_range').value.trim();
  if(pendingNewDays.length===0){
    if(!confirm("Aucune séance ajoutée. Créer la semaine vide quand même ?")) return;
  }
  const week = { id: uid(), title, dateRange, createdAt: Date.now(), days: pendingNewDays };
  data.weeks.push(week);
  data.activeWeekId = week.id;
  saveData();
  pendingNewDays = [];
  closeModal();
  currentTab = 'semaine';
  render();
  showToast('Semaine créée ✓');
}

/* =========================================================
   SCAN PHOTO (OCR client-side, sans clé API)
========================================================= */
function traduireStatutOcr(s){
  const map = {
    'loading tesseract core':'Chargement du moteur',
    'initializing tesseract':'Initialisation',
    'loading language traineddata':'Chargement du modèle français',
    'initialized api':'Préparation',
    'initializing api':'Préparation',
    'recognizing text':'Lecture du texte'
  };
  return map[s] || s;
}
async function runOcrOnFile(file){
  const statusEl = document.getElementById('scanStatus');
  if(statusEl) statusEl.textContent = 'Chargement du moteur de lecture...';
  if(typeof Tesseract === 'undefined'){
    throw new Error('Tesseract non chargé (vérifie ta connexion internet)');
  }
  const worker = await Tesseract.createWorker('fra', 1, {
    logger: m=>{
      if(statusEl && m && m.status){
        const pct = m.progress ? ' ('+Math.round(m.progress*100)+'%)' : '';
        statusEl.textContent = traduireStatutOcr(m.status) + pct;
      }
    }
  });
  const { data: { text } } = await worker.recognize(file);
  await worker.terminate();
  return text;
}
function parseCoachText(rawText, startDate){
  const DAY_NAMES = ['lundi','mardi','mercredi','jeudi','vendredi','samedi','dimanche'];
  const lines = rawText.split(/\r?\n/).map(l=>l.trim()).filter(l=>l.length>0);
  const blocks = [];
  let current = null;
  let inRecap = false;
  const recapLines = [];

  lines.forEach(line=>{
    const lower = line.toLowerCase();
    if(/r[ée]capitulatif/i.test(line)){ inRecap = true; recapLines.push(line); current = null; return; }
    if(inRecap){ recapLines.push(line); return; }
    const dayMatch = DAY_NAMES.find(d => lower.startsWith(d));
    if(dayMatch){
      current = { dayName: dayMatch, lines: [] };
      blocks.push(current);
      const rest = line.slice(dayMatch.length).replace(/^[\s:]+/, '');
      if(rest) current.lines.push(rest);
      return;
    }
    if(current) current.lines.push(line);
  });

  const days = blocks.map(b=>{
    const text = b.lines.join(' ');
    const idx = text.toLowerCase().indexOf('rpe');
    let title = '', detail = '';
    if(idx >= 0){
      const after = text.slice(idx);
      const colonIdx = after.indexOf(':');
      if(colonIdx >= 0){
        title = after.slice(0, colonIdx).trim();
        detail = after.slice(colonIdx+1).trim();
      } else {
        title = after.trim();
      }
    } else {
      detail = text.trim();
    }
    let duration = 0;
    const durMatches = [...title.matchAll(/\((\d+)\s?h\s?(\d{0,2})\)/g)];
    if(durMatches.length){
      const m = durMatches[durMatches.length-1];
      duration = Math.round((parseFloat(m[1]) + (m[2]?parseInt(m[2],10):0)/60) * 100) / 100;
    }
    return {
      id: uid(), day: b.dayName.charAt(0).toUpperCase()+b.dayName.slice(1), date:'',
      sport:'course', title, duration, detail, status:'todo', rescheduledFrom:null, feedback:{}
    };
  });

  if(startDate && days.length){
    const d0 = new Date(startDate+'T00:00:00');
    days.forEach((day,i)=>{
      const dt = new Date(d0); dt.setDate(d0.getDate()+i);
      day.date = dt.toISOString().slice(0,10);
    });
  }

  const recapText = recapLines.join(' ');
  let weekNumber = null;
  const wMatch = recapText.match(/semaine\s*(\d+)/i);
  if(wMatch) weekNumber = wMatch[1];
  let dateRange = '';
  const rMatch = recapText.match(/du\s+\d{1,2}.*?\d{4}/i);
  if(rMatch) dateRange = 'Du' + rMatch[0].slice(2);

  return { days, weekNumber, dateRange };
}
async function handleScanFile(file){
  if(!file) return;
  const statusEl = document.getElementById('scanStatus');
  const startDate = document.getElementById('scan_startdate') ? document.getElementById('scan_startdate').value : '';
  try{
    const text = await runOcrOnFile(file);
    const parsed = parseCoachText(text, startDate);
    if(parsed.days.length === 0){
      if(statusEl) statusEl.textContent = '';
      showToast('Aucune séance détectée — vérifie la photo ou saisis manuellement');
      return;
    }
    pendingNewDays = pendingNewDays.concat(parsed.days);
    renderNewWeekModal();
    if(parsed.weekNumber && document.getElementById('nw_title') && !document.getElementById('nw_title').value){
      document.getElementById('nw_title').value = 'Semaine ' + parsed.weekNumber;
    }
    if(parsed.dateRange && document.getElementById('nw_range') && !document.getElementById('nw_range').value){
      document.getElementById('nw_range').value = parsed.dateRange;
    }
    showToast(parsed.days.length + ' séance(s) détectée(s) — vérifie le sport et les détails avant d\'enregistrer ✓');
  }catch(err){
    if(statusEl) statusEl.textContent = '';
    showToast('Erreur de lecture de la photo, réessaie ou saisis manuellement');
    console.error(err);
  }
}

function openAddDayModal(weekId){
  pendingNewDays = [];
  const html = `
    <div class="modal-head"><h3>Ajouter une séance</h3><button class="close-x" data-action="close-modal">×</button></div>
    <div id="newDayFormZone">${renderNewDayFields()}</div>
  `;
  openModal(html);
  document.querySelector('[data-action="add-pending-day"]').setAttribute('data-week', weekId);
  document.querySelector('[data-action="add-pending-day"]').textContent = '+ Ajouter cette séance';
  document.querySelector('[data-action="add-pending-day"]').setAttribute('data-action','add-day-direct');
}
function addDayDirect(weekId){
  const day = document.getElementById('nd_day').value.trim();
  const date = document.getElementById('nd_date').value;
  const sport = document.getElementById('nd_sport').value;
  const duration = parseFloat(document.getElementById('nd_duration').value)||0;
  const title = document.getElementById('nd_title').value.trim();
  const detail = document.getElementById('nd_detail').value.trim();
  const week = data.weeks.find(w=>w.id===weekId);
  if(!week) return;
  week.days.push({ id: uid(), day: day||'Jour', date, sport, duration, title, detail, status:'todo', rescheduledFrom:null, feedback:{} });
  saveData();
  closeModal();
  render();
  showToast('Séance ajoutée ✓');
}

function openSettingsModal(){
  const html = `
    <div class="modal-head"><h3>Réglages</h3><button class="close-x" data-action="close-modal">×</button></div>
    <p style="font-size:13px;color:var(--muted);">Les données sont stockées uniquement dans ce navigateur. Pense à exporter régulièrement une sauvegarde.</p>
    <button class="btn btn-block" style="margin-bottom:10px;" data-action="export-data">⬇ Exporter une sauvegarde (.json)</button>
    <label class="btn btn-block btn-ghost" style="text-align:center;display:block;margin-bottom:10px;cursor:pointer;">
      ⬆ Importer une sauvegarde
      <input type="file" id="importFile" accept="application/json" style="display:none;">
    </label>
    <hr class="sep">
    <button class="btn btn-block btn-danger" data-action="reset-data">🗑 Réinitialiser toutes les données</button>
  `;
  openModal(html);
  document.getElementById('importFile').addEventListener('change', handleImport);
}
function exportData(){
  const blob = new Blob([JSON.stringify(data,null,2)], {type:'application/json'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url; a.download = 'carnet-thomas-sauvegarde.json';
  a.click();
  URL.revokeObjectURL(url);
}
function handleImport(e){
  const file = e.target.files[0];
  if(!file) return;
  const reader = new FileReader();
  reader.onload = function(ev){
    try{
      const parsed = JSON.parse(ev.target.result);
      if(!parsed.weeks) throw new Error('format invalide');
      data = parsed;
      saveData();
      closeModal();
      render();
      showToast('Sauvegarde importée ✓');
    }catch(err){
      showToast('Fichier invalide');
    }
  };
  reader.readAsText(file);
}
function resetData(){
  if(confirm('Supprimer définitivement toutes les semaines et tous les avis enregistrés ?')){
    data = { weeks: [], activeWeekId: null };
    saveData();
    closeModal();
    render();
    showToast('Données réinitialisées');
  }
}

/* =========================================================
   DAY ACTIONS
========================================================= */
function findDay(dayId){
  for(const w of data.weeks){
    const d = w.days.find(x=>x.id===dayId);
    if(d) return {week:w, day:d};
  }
  return null;
}
function markDone(dayId){
  const r = findDay(dayId); if(!r) return;
  r.day.status = 'done';
  feedbackOpenId = dayId;
  saveData(); render();
}
function markTodo(dayId){
  const r = findDay(dayId); if(!r) return;
  r.day.status = 'todo';
  saveData(); render();
}
function markNotDone(dayId){
  reschedulingDayId = dayId;
  render();
}
function cancelReschedule(){
  reschedulingDayId = null;
  render();
}
function confirmReschedule(dayId){
  const input = document.getElementById('reschedDate_'+dayId);
  const newDate = input ? input.value : '';
  if(!newDate){ showToast('Choisis une date'); return; }
  const r = findDay(dayId); if(!r) return;
  const oldDate = r.day.date;
  r.day.date = newDate;
  r.day.status = 'rescheduled';
  r.day.rescheduledFrom = oldDate || r.day.rescheduledFrom || null;
  reschedulingDayId = null;
  saveData(); render();
  showToast('Séance reprogrammée ✓');
}
function confirmSkip(dayId){
  const r = findDay(dayId); if(!r) return;
  r.day.status = 'skipped';
  reschedulingDayId = null;
  saveData(); render();
}
function deleteDay(dayId){
  if(!confirm('Supprimer définitivement cette séance ?')) return;
  const r = findDay(dayId); if(!r) return;
  r.week.days = r.week.days.filter(d=>d.id!==dayId);
  saveData(); render();
}
function editDay(dayId){
  editingDayId = dayId;
  render();
}
function cancelEditDay(){
  editingDayId = null;
  render();
}
function saveEditDay(dayId){
  const r = findDay(dayId); if(!r) return;
  r.day.day = document.getElementById('edit_day_'+dayId).value.trim();
  r.day.date = document.getElementById('edit_date_'+dayId).value;
  r.day.sport = document.getElementById('edit_sport_'+dayId).value;
  r.day.title = document.getElementById('edit_title_'+dayId).value.trim();
  r.day.duration = parseFloat(document.getElementById('edit_duration_'+dayId).value)||0;
  r.day.detail = document.getElementById('edit_detail_'+dayId).value.trim();
  editingDayId = null;
  saveData(); render();
  showToast('Séance modifiée ✓');
}
function openFeedback(dayId){
  feedbackOpenId = dayId;
  render();
}
function closeFeedback(){
  feedbackOpenId = null;
  render();
}
function saveFeedback(dayId){
  const r = findDay(dayId); if(!r) return;
  const diffEl = document.getElementById('diffRange_'+dayId);
  const notesEl = document.getElementById('notesArea_'+dayId);
  const chipRow = document.getElementById('chipRow_'+dayId);
  const selected = chipRow ? [...chipRow.querySelectorAll('.chip.selected')].map(c=>c.dataset.sensation) : [];
  r.day.feedback = {
    difficulty: diffEl ? parseInt(diffEl.value,10) : null,
    sensations: selected,
    notes: notesEl ? notesEl.value.trim() : ''
  };
  feedbackOpenId = null;
  saveData(); render();
  showToast('Avis enregistré ✓');
}

/* =========================================================
   EVENT DELEGATION
========================================================= */
document.addEventListener('click', function(e){
  const t = e.target.closest('[data-action]');
  if(t){
    const action = t.dataset.action;
    const id = t.dataset.id;
    switch(action){
      case 'open-new-week': openNewWeekModal(); break;
      case 'open-add-day': openAddDayModal(t.dataset.week); break;
      case 'add-pending-day': addPendingDay(); break;
      case 'add-day-direct': addDayDirect(t.dataset.week); break;
      case 'remove-pending-day': pendingNewDays.splice(parseInt(t.dataset.idx,10),1); renderNewWeekModal(); break;
      case 'edit-pending-day': editPendingDay(parseInt(t.dataset.idx,10)); break;
      case 'save-new-week': saveNewWeek(); break;
      case 'close-modal': closeModal(); break;
      case 'export-data': exportData(); break;
      case 'reset-data': resetData(); break;
      case 'select-week': data.activeWeekId = id; currentTab='semaine'; saveData(); render(); break;
      case 'mark-done': markDone(id); break;
      case 'mark-todo': markTodo(id); break;
      case 'mark-notdone': markNotDone(id); break;
      case 'cancel-reschedule': cancelReschedule(); break;
      case 'confirm-reschedule': confirmReschedule(id); break;
      case 'confirm-skip': confirmSkip(id); break;
      case 'delete-day': deleteDay(id); break;
      case 'edit-day': editDay(id); break;
      case 'cancel-edit-day': cancelEditDay(); break;
      case 'save-edit-day': saveEditDay(id); break;
      case 'open-feedback': openFeedback(id); break;
      case 'close-feedback': closeFeedback(); break;
      case 'save-feedback': saveFeedback(id); break;
    }
    return;
  }
  const chip = e.target.closest('.chip');
  if(chip){
    chip.classList.toggle('selected');
    return;
  }
});

document.addEventListener('change', function(e){
  if(e.target.id === 'weekSelect'){
    data.activeWeekId = e.target.value;
    saveData(); render();
  }
  if(e.target.id === 'scanPhotoInput'){
    handleScanFile(e.target.files[0]);
  }
});

document.querySelectorAll('.tab-btn').forEach(btn=>{
  btn.addEventListener('click', ()=>{ currentTab = btn.dataset.tab; render(); });
});
document.getElementById('gearBtn').addEventListener('click', openSettingsModal);

/* init */
render();
</script>
</body>
</html>
