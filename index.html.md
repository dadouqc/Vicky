<!DOCTYPE html>  
<html lang="fr">  
<head>  
  <meta charset="UTF-8"/>  
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
  <title>Le tableau de Victoire 🌈</title>  
  <style>  
    * { box-sizing: border-box; margin: 0; padding: 0; }  
    body {  
      font-family: 'Segoe UI', sans-serif;  
      background: linear-gradient(135deg, #fff0f5 0%, #f0f4ff 100%);  
      min-height: 100vh;  
      padding: 20px 16px;  
    }  
    .container { max-width: 460px; margin: 0 auto; }  
    .card {  
      background: white;  
      border-radius: 20px;  
      padding: 16px;  
      margin-bottom: 14px;  
      box-shadow: 0 2px 12px rgba(0,0,0,0.06);  
    }  
    h1 { font-size: 22px; color: #7c3aed; font-weight: 900; margin: 4px 0 0; }  
    h2 { font-size: 15px; font-weight: 800; margin-bottom: 10px; }  
    .header { text-align: center; margin-bottom: 22px; }  
    .score-card {  
      background: white;  
      border-radius: 24px;  
      padding: 20px 22px;  
      text-align: center;  
      box-shadow: 0 4px 20px rgba(124,58,237,0.12);  
      margin-bottom: 18px;  
    }  
    #minutes-display {  
      font-size: 64px;  
      font-weight: 900;  
      line-height: 1;  
      transition: color 0.4s;  
    }  
    .progress-bg {  
      background: #f3f4f6;  
      border-radius: 999px;  
      height: 18px;  
      overflow: hidden;  
      margin-top: 14px;  
    }  
    #progress-bar {  
      height: 100%;  
      border-radius: 999px;  
      transition: width 0.5s ease, background 0.4s;  
    }  
    .btn {  
      display: flex;  
      justify-content: space-between;  
      align-items: center;  
      width: 100%;  
      margin-bottom: 7px;  
      padding: 10px 14px;  
      border-radius: 12px;  
      cursor: pointer;  
      font-size: 14px;  
      font-weight: 600;  
      text-align: left;  
      border: 2px solid;  
      transition: transform 0.1s, opacity 0.1s;  
    }  
    .btn:hover { transform: scale(1.01); opacity: 0.92; }  
    .btn-good { background: #f0fdf4; border-color: #bbf7d0; color: #15803d; }  
    .btn-bad  { background: #fff1f2; border-color: #fecdd3; color: #be123c; }  
    .badge {  
      color: white;  
      border-radius: 999px;  
      padding: 2px 11px;  
      font-size: 13px;  
      white-space: nowrap;  
    }  
    .badge-good { background: #16a34a; }  
    .badge-bad  { background: #dc2626; }  
    /* Toggle */  
    .toggle-wrap { display: flex; background: #f3f4f6; border-radius: 12px; padding: 4px; margin-bottom: 12px; }  
    .toggle-btn {  
      flex: 1; padding: 8px 0; border-radius: 9px; border: none;  
      cursor: pointer; font-weight: 700; font-size: 13px; transition: all 0.2s;  
      background: transparent; color: #9ca3af;  
    }  
    .toggle-btn.active-good { background: #16a34a; color: white; }  
    .toggle-btn.active-bad  { background: #dc2626; color: white; }  
    input[type="text"] {  
      width: 100%; padding: 10px 14px; border-radius: 12px;  
      border: 2px solid #e9d5ff; font-size: 14px; outline: none;  
      margin-bottom: 10px; color: #374151;  
    }  
    .slider-row { display: flex; align-items: center; gap: 12px; margin-bottom: 12px; }  
    input[type="range"] { flex: 1; accent-color: #7c3aed; }  
    #custom-min-label { font-weight: 800; font-size: 16px; min-width: 56px; text-align: center; }  
    #submit-btn {  
      width: 100%; padding: 11px 0; border: none; border-radius: 12px;  
      font-size: 14px; font-weight: 800; cursor: pointer; transition: all 0.2s;  
      color: white;  
    }  
    /* History */  
    .history-row {  
      display: flex; justify-content: space-between; align-items: center;  
      padding: 6px 0; border-bottom: 1px solid #f3f4f6; font-size: 13px;  
    }  
    .history-row:last-child { border-bottom: none; }  
    .history-time { color: #9ca3af; font-size: 11px; margin-right: 8px; }  
    .reset-btn {  
      width: 100%; padding: 14px; background: linear-gradient(135deg,#7c3aed,#c084fc);  
      color: white; border: none; border-radius: 16px; font-size: 15px;  
      font-weight: 800; cursor: pointer; box-shadow: 0 4px 14px rgba(124,58,237,0.3);  
      margin-bottom: 16px;  
    }  
    .footer { text-align: center; color: #c4b5fd; font-size: 12px; margin-bottom: 20px; }  
    #history-card { display: none; }  
  </style>  
</head>  
<body>  
<div class="container">  
  
  <!-- Header -->  
  <div class="header">  
    <div style="font-size:44px">🌈</div>  
    <h1>Le tableau de Victoire ⭐</h1>  
    <p style="color:#a78bfa;font-size:13px;margin-top:4px">Ta tablette, tu la mérites !</p>  
  </div>  
  
  <!-- Score -->  
  <div class="score-card">  
    <p style="color:#9ca3af;font-size:13px;margin-bottom:2px">Ce weekend tu as gagné</p>  
    <div id="minutes-display">60<span style="font-size:26px;font-weight:700">min</span></div>  
    <p style="color:#c4b5fd;font-size:13px;margin:4px 0 0">de tablette 🎮✨</p>  
    <div class="progress-bg">  
      <div id="progress-bar" style="width:100%"></div>  
    </div>  
    <p style="color:#d1d5db;font-size:11px;margin-top:8px">Base : 60 min</p>  
  </div>  
  
  <!-- Saisie manuelle -->  
  <div class="card">  
    <h2 style="color:#7c3aed">✏️ Ajouter manuellement</h2>  
    <div class="toggle-wrap">  
      <button class="toggle-btn active-good" id="btn-good" onclick="setType('good')">✅ Bon comportement</button>  
      <button class="toggle-btn" id="btn-bad" onclick="setType('bad')">❌ Mauvais comportement</button>  
    </div>  
    <input type="text" id="custom-label" placeholder="Décris le comportement…" onkeydown="if(event.key==='Enter')submitCustom()"/>  
    <div class="slider-row">  
      <span style="color:#9ca3af;font-size:13px;white-space:nowrap">Minutes :</span>  
      <input type="range" id="custom-slider" min="5" max="30" step="5" value="5" oninput="updateSlider()"/>  
      <span id="custom-min-label" style="color:#16a34a">+5 min</span>  
    </div>  
    <button id="submit-btn" onclick="submitCustom()" style="background:linear-gradient(135deg,#16a34a,#4ade80)">  
      ➕ Ajouter les minutes  
    </button>  
  </div>  
  
  <!-- Bons comportements -->  
  <div class="card">  
    <h2 style="color:#16a34a">✅ Bravo Victoire !</h2>  
    <button class="btn btn-good" onclick="apply('🌟 Rangé sa chambre', 5)"><span>🌟 Rangé sa chambre</span><span class="badge badge-good">+5 min</span></button>  
    <button class="btn btn-good" onclick="apply('📚 Devoirs sans râler', 5)"><span>📚 Devoirs sans râler</span><span class="badge badge-good">+5 min</span></button>  
    <button class="btn btn-good" onclick="apply('😊 Super comportement', 10)"><span>😊 Super comportement</span><span class="badge badge-good">+10 min</span></button>  
    <button class="btn btn-good" onclick="apply('⭐ Bonne note à l\'école', 10)"><span>⭐ Bonne note à l'école</span><span class="badge badge-good">+10 min</span></button>  
    <button class="btn btn-good" onclick="apply('🤝 A aidé quelqu\'un', 5)"><span>🤝 A aidé quelqu'un</span><span class="badge badge-good">+5 min</span></button>  
  </div>  
  
  <!-- Mauvais comportements -->  
  <div class="card">  
    <h2 style="color:#dc2626">⚠️ À améliorer…</h2>  
    <button class="btn btn-bad" onclick="apply('😤 Caprice / crise', -5)"><span>😤 Caprice / crise</span><span class="badge badge-bad">-5 min</span></button>  
    <button class="btn btn-bad" onclick="apply('📝 Mauvais point à l\'école', -10)"><span>📝 Mauvais point à l'école</span><span class="badge badge-bad">-10 min</span></button>  
    <button class="btn btn-bad" onclick="apply('🙅 N\'a pas obéi', -5)"><span>🙅 N'a pas obéi</span><span class="badge badge-bad">-5 min</span></button>  
    <button class="btn btn-bad" onclick="apply('😠 Grossièreté', -10)"><span>😠 Grossièreté</span><span class="badge badge-bad">-10 min</span></button>  
  </div>  
  
  <!-- Historique -->  
  <div class="card" id="history-card">  
    <h2 style="color:#6b7280">📋 Historique de la semaine</h2>  
    <div id="history-list"></div>  
  </div>  
  
  <!-- Reset -->  
  <button class="reset-btn" onclick="resetWeek()">🔄 Nouvelle semaine — reset à 60 min</button>  
  <p class="footer">Fait avec ❤️ pour Victoire</p>  
  
</div>  
<script>  
  const BASE = 60;  
  let customType = 'good';  
  
  function load() {  
    return JSON.parse(localStorage.getItem('victoire') || '{"minutes":60,"history":[]}');  
  }  
  function save(data) {  
    localStorage.setItem('victoire', JSON.stringify(data));  
  }  
  
  function render() {  
    const data = load();  
    const m = data.minutes;  
    const pct = Math.min(100, Math.max(0, (m / BASE) * 100));  
    const color = m >= 40  
      ? { num: '#7c3aed', bar: 'linear-gradient(90deg,#7c3aed,#a78bfa)' }  
      : m >= 20  
      ? { num: '#f59e0b', bar: 'linear-gradient(90deg,#f59e0b,#fcd34d)' }  
      : { num: '#ef4444', bar: 'linear-gradient(90deg,#ef4444,#fca5a5)' };  
  
    document.getElementById('minutes-display').innerHTML =  
      `<span style="color:${color.num}">${m}</span><span style="font-size:26px;font-weight:700;color:${color.num}">min</span>`;  
    document.getElementById('progress-bar').style.width = pct + '%';  
    document.getElementById('progress-bar').style.background = color.bar;  
  
    const histList = document.getElementById('history-list');  
    const histCard = document.getElementById('history-card');  
    if (data.history.length === 0) {  
      histCard.style.display = 'none';  
    } else {  
      histCard.style.display = 'block';  
      histList.innerHTML = data.history.map(h => `  
        <div class="history-row">  
          <span style="color:#374151">${h.label}</span>  
          <span>  
            <span class="history-time">${h.time}</span>  
            <span style="color:${h.min>0?'#16a34a':'#dc2626'};font-weight:700">${h.min>0?'+':''}${h.min} min</span>  
          </span>  
        </div>`).join('');  
    }  
  }  
  
  function apply(label, min) {  
    const data = load();  
    data.minutes = Math.max(0, data.minutes + min);  
    const now = new Date().toLocaleTimeString('fr-CA', { hour: '2-digit', minute: '2-digit' });  
    data.history.unshift({ label, min, time: now });  
    if (data.history.length > 30) data.history.pop();  
    save(data);  
    render();  
  }  
  
  function setType(type) {  
    customType = type;  
    document.getElementById('btn-good').className = 'toggle-btn' + (type==='good' ? ' active-good' : '');  
    document.getElementById('btn-bad').className  = 'toggle-btn' + (type==='bad'  ? ' active-bad'  : '');  
    updateSlider();  
  }  
  
  function updateSlider() {  
    const val = document.getElementById('custom-slider').value;  
    const lbl = document.getElementById('custom-min-label');  
    const btn = document.getElementById('submit-btn');  
    if (customType === 'good') {  
      lbl.style.color = '#16a34a';  
      lbl.textContent = '+' + val + ' min';  
      btn.style.background = 'linear-gradient(135deg,#16a34a,#4ade80)';  
      btn.textContent = '➕ Ajouter les minutes';  
    } else {  
      lbl.style.color = '#dc2626';  
      lbl.textContent = '-' + val + ' min';  
      btn.style.background = 'linear-gradient(135deg,#dc2626,#f87171)';  
      btn.textContent = '➖ Retirer les minutes';  
    }  
  }  
  
  function submitCustom() {  
    const label = document.getElementById('custom-label').value.trim();  
    if (!label) return;  
    const val = parseInt(document.getElementById('custom-slider').value);  
    const min = customType === 'good' ? val : -val;  
    apply('✏️ ' + label, min);  
    document.getElementById('custom-label').value = '';  
    document.getElementById('custom-slider').value = 5;  
    updateSlider();  
  }  
  
  function resetWeek() {  
    if (confirm('Nouvelle semaine ? Ça va remettre les minutes à 60 et effacer l\'historique.')) {  
      save({ minutes: BASE, history: [] });  
      render();  
    }  
  }  
  
  render();  
</script>  
</body>  
</html>  
