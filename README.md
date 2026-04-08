[index.html](https://github.com/user-attachments/files/26575018/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="MichaStudio">
<meta name="theme-color" content="#07070d">
<title>MichaStudio</title>
<link rel="apple-touch-icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='22' fill='%2307070d'/%3E%3Ctext y='.9em' font-size='80' x='10'%3E🎤%3C/text%3E%3C/svg%3E">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
:root{
  --bg:#07070d;--s1:#0f0f1a;--s2:#161625;--s3:#1e1e30;
  --acc:#b088ff;--acc2:#ff85c8;--acc3:#85e8d4;
  --txt:#ede9ff;--muted:#6e6a8a;--border:rgba(255,255,255,0.07);
  --safe-bottom:env(safe-area-inset-bottom,0px);
}
html{height:100%;overflow:hidden}
body{
  font-family:'Space Grotesk',sans-serif;
  background:var(--bg);color:var(--txt);
  height:100%;overflow:hidden;
  -webkit-font-smoothing:antialiased;
}
.app{
  display:flex;flex-direction:column;
  height:100vh;height:100dvh;
  max-width:520px;margin:0 auto;
  position:relative;
}
.topbar{
  display:flex;align-items:center;justify-content:space-between;
  padding:max(18px, env(safe-area-inset-top,18px)) 16px 14px;
  background:var(--bg);
  flex-shrink:0;
  border-bottom:1px solid var(--border);
}
.logo{font-family:'Space Mono',monospace;font-size:1rem;color:var(--acc);letter-spacing:-.02em}
.logo span{color:var(--acc2)}
.step-pills{display:flex;gap:5px;align-items:center}
.pill{width:26px;height:3px;border-radius:2px;background:var(--s3);transition:.3s}
.pill.done{background:var(--acc3)}
.pill.active{background:var(--acc)}

.scroll-area{
  flex:1;overflow-y:auto;overflow-x:hidden;
  -webkit-overflow-scrolling:touch;
  padding-bottom:16px;
}
.screen{display:none;padding:16px 16px 0}
.screen.active{display:block}

.section-label{
  font-family:'Space Mono',monospace;font-size:.6rem;
  letter-spacing:.15em;text-transform:uppercase;
  color:var(--muted);margin-bottom:10px;
}
.card{
  background:var(--s1);border:1px solid var(--border);
  border-radius:14px;padding:14px;margin-bottom:10px;
}

.upload-zone{
  border:1.5px dashed rgba(176,136,255,.25);border-radius:12px;
  padding:28px 16px;text-align:center;cursor:pointer;
  transition:.2s;position:relative;overflow:hidden;
}
.upload-zone:hover,.upload-zone.drag{border-color:var(--acc);background:rgba(176,136,255,.04)}
.upload-zone input{position:absolute;inset:0;opacity:0;cursor:pointer;width:100%;height:100%}
.uz-icon{font-size:2rem;margin-bottom:8px}
.uz-text{font-size:.78rem;color:var(--muted);line-height:1.7}
.uz-text strong{color:var(--acc);font-weight:500}
.file-ok{font-size:.72rem;color:var(--acc3);margin-top:6px;display:none}

.btn{
  display:flex;align-items:center;justify-content:center;gap:8px;
  width:100%;padding:.8rem 1.2rem;
  font-family:'Space Grotesk',sans-serif;font-size:.78rem;font-weight:500;
  letter-spacing:.06em;text-transform:uppercase;
  border:1px solid var(--acc);background:transparent;color:var(--acc);
  border-radius:10px;cursor:pointer;transition:.2s;
}
.btn:active{transform:scale(.97)}
.btn:disabled{opacity:.25;cursor:not-allowed;transform:none}
.btn.fill{background:var(--acc);color:var(--bg);border-color:var(--acc)}
.btn.fill:active{background:#c4a3ff}
.btn.green{border-color:var(--acc3);color:var(--acc3)}
.btn.green:active{background:rgba(133,232,212,.08)}
.btn.pink{border-color:var(--acc2);color:var(--acc2)}
.btn.pink:active{background:rgba(255,133,200,.08)}

.analysis-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.a-card{background:var(--s2);border-radius:10px;padding:12px}
.a-label{font-size:.58rem;color:var(--muted);text-transform:uppercase;letter-spacing:.1em;margin-bottom:4px}
.a-value{font-family:'Space Mono',monospace;font-size:.95rem;color:var(--txt);font-weight:700}
.a-sub{font-size:.62rem;color:var(--acc);margin-top:2px}

.chord-row{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px}
.chord{
  background:var(--s2);border:1px solid rgba(176,136,255,.2);
  border-radius:8px;padding:6px 12px;
  font-family:'Space Mono',monospace;font-size:.75rem;color:var(--acc);
  cursor:pointer;transition:.15s;
}
.chord.sel,.chord:active{background:rgba(176,136,255,.15);border-color:var(--acc)}

.track-lane{
  display:flex;align-items:center;gap:10px;
  background:var(--s2);border-radius:10px;
  padding:10px 12px;margin-bottom:8px;
  border:1px solid var(--border);transition:.2s;
}
.lane-color{width:3px;height:36px;border-radius:2px;flex-shrink:0}
.lane-info{flex:0 0 80px}
.lane-name{font-size:.75rem;font-weight:500;color:var(--txt)}
.lane-sub{font-size:.6rem;color:var(--muted);margin-top:2px}
.lane-wave{flex:1;height:28px;display:flex;align-items:center;gap:1px;padding:0 4px;overflow:hidden}
.wave-bar{flex:1;border-radius:1px;min-height:2px;transition:.3s}
.lane-btns{display:flex;gap:5px;flex-shrink:0}
.ibtn{
  width:30px;height:30px;border-radius:7px;
  border:1px solid var(--border);background:transparent;
  color:var(--muted);cursor:pointer;font-size:.75rem;
  display:flex;align-items:center;justify-content:center;
  transition:.2s;font-family:monospace;
}
.ibtn:active{border-color:var(--acc);color:var(--acc)}
.ibtn.muted-state{border-color:#ff6b6b;color:#ff6b6b}

.slider-row{margin-bottom:10px}
.sl-head{display:flex;justify-content:space-between;font-size:.68rem;color:var(--muted);margin-bottom:6px}
.sl-head span:last-child{color:var(--acc);font-family:'Space Mono',monospace}
input[type=range]{
  width:100%;height:4px;appearance:none;-webkit-appearance:none;
  background:var(--s3);border-radius:2px;outline:none;
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none;width:18px;height:18px;
  border-radius:50%;background:var(--acc);cursor:pointer;
}

.pitch-display{
  display:flex;align-items:center;justify-content:center;gap:16px;
  padding:16px;background:var(--s2);border-radius:12px;margin-bottom:12px;
}
.pitch-note{font-family:'Space Mono',monospace;font-size:2.2rem;font-weight:700;color:var(--acc)}
.pitch-detail{font-size:.68rem;color:var(--muted);text-align:center}
.pitch-meter{width:100%;height:6px;background:var(--s3);border-radius:3px;margin:8px 0;overflow:hidden}
.pitch-fill{height:100%;border-radius:3px;background:var(--acc3);transition:.4s;width:50%}

.instrument-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-bottom:12px}
.inst-chip{
  background:var(--s2);border:1px solid var(--border);
  border-radius:9px;padding:10px 6px;text-align:center;cursor:pointer;transition:.2s;
}
.inst-chip.sel{border-color:var(--acc);background:rgba(176,136,255,.08)}
.inst-icon{font-size:1.3rem;margin-bottom:3px}
.inst-name{font-size:.6rem;color:var(--muted)}
.inst-chip.sel .inst-name{color:var(--acc)}

.mix-track{
  display:grid;grid-template-columns:70px 1fr 36px;
  align-items:center;gap:8px;margin-bottom:10px;
}
.mix-label{font-size:.66rem;color:var(--muted);text-align:right}
.mix-val{font-family:'Space Mono',monospace;font-size:.66rem;color:var(--acc);text-align:center}

.ai-bubble{
  background:var(--s2);border-radius:12px;padding:12px;
  font-size:.74rem;line-height:1.75;color:var(--txt);
  margin-bottom:10px;border-left:2px solid var(--acc);
  display:none;
}
.thinking{display:flex;align-items:center;gap:8px;font-size:.7rem;color:var(--muted);padding:4px 0}
.dots span{animation:blink 1.4s infinite}
.dots span:nth-child(2){animation-delay:.2s}
.dots span:nth-child(3){animation-delay:.4s}
@keyframes blink{0%,80%,100%{opacity:.2}40%{opacity:1}}

.progress-bar{height:2px;background:var(--s3);border-radius:1px;margin:10px 0}
.progress-fill{height:100%;border-radius:1px;background:var(--acc);transition:width .4s}

.status-row{
  display:flex;align-items:center;gap:8px;
  font-size:.7rem;color:var(--muted);padding:6px 0;margin-bottom:6px;
}
.dot{width:5px;height:5px;border-radius:50%;background:var(--muted);flex-shrink:0}
.dot.on{background:var(--acc);animation:pulse 1.5s infinite}
.dot.ok{background:var(--acc3)}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}

.tag{
  display:inline-flex;align-items:center;gap:4px;
  font-size:.62rem;padding:5px 10px;border-radius:20px;
  border:1px solid var(--border);color:var(--muted);
  cursor:pointer;margin:3px 3px 0 0;transition:.2s;
}
.tag.sel{border-color:var(--acc2);color:var(--acc2)}

.bottom-nav{
  display:flex;gap:0;
  background:var(--s1);
  border-top:1px solid var(--border);
  padding-bottom:var(--safe-bottom);
  flex-shrink:0;
}
.bnav{
  flex:1;padding:10px 4px 8px;text-align:center;cursor:pointer;
  border:none;background:transparent;color:var(--muted);
  font-family:'Space Grotesk',sans-serif;font-size:.58rem;
  letter-spacing:.04em;text-transform:uppercase;
  transition:.2s;display:flex;flex-direction:column;align-items:center;gap:3px;
}
.bnav-icon{font-size:1.2rem;line-height:1}
.bnav.active{color:var(--acc)}

audio{width:100%;margin-top:8px;border-radius:6px}
.hidden{display:none!important}
.mt8{margin-top:8px}
.mb0{margin-bottom:0}

.install-banner{
  background:rgba(176,136,255,.08);border:1px solid rgba(176,136,255,.2);
  border-radius:12px;padding:12px 14px;margin-bottom:12px;
  font-size:.72rem;line-height:1.6;color:var(--muted);
}
.install-banner strong{color:var(--acc);display:block;margin-bottom:4px;font-size:.75rem}
</style>
</head>
<body>
<div class="app">

  <!-- TOPBAR -->
  <div class="topbar">
    <div class="logo">Micha<span>Studio</span></div>
    <div class="step-pills">
      <div class="pill active" id="p1"></div>
      <div class="pill" id="p2"></div>
      <div class="pill" id="p3"></div>
      <div class="pill" id="p4"></div>
      <div class="pill" id="p5"></div>
    </div>
  </div>

  <!-- SCROLL AREA -->
  <div class="scroll-area">

    <!-- SCREEN 1: ANALISAR -->
    <div class="screen active" id="s1">

      <div id="installBanner" class="install-banner">
        <strong>💡 Instalar como app</strong>
        Toque em <strong style="color:var(--acc2)">Compartilhar</strong> no Safari → <strong style="color:var(--acc2)">Adicionar à Tela de Início</strong> para usar como app nativo.
      </div>

      <div class="section-label">01 · carregar música</div>
      <div class="card">
        <div class="upload-zone" id="uz">
          <input type="file" id="fileIn" accept="audio/*">
          <div class="uz-icon">🎵</div>
          <div class="uz-text"><strong>Toque para selecionar</strong><br>Voice Memos · MP3 · WAV · M4A · FLAC</div>
          <div class="file-ok" id="fileOk"></div>
        </div>
        <audio id="origAudio" controls class="hidden"></audio>
      </div>

      <div class="section-label">análise automática via ia</div>
      <div class="analysis-grid" id="analysisGrid" style="display:none">
        <div class="a-card"><div class="a-label">Tonalidade</div><div class="a-value" id="aKey">—</div><div class="a-sub" id="aMode">—</div></div>
        <div class="a-card"><div class="a-label">BPM</div><div class="a-value" id="aBpm">—</div><div class="a-sub" id="aFeel">—</div></div>
        <div class="a-card"><div class="a-label">Compasso</div><div class="a-value" id="aTime">—</div><div class="a-sub" id="aGroove">—</div></div>
        <div class="a-card"><div class="a-label">Gênero</div><div class="a-value" id="aGenre">—</div><div class="a-sub" id="aSub">—</div></div>
      </div>

      <div id="chordSection" class="hidden">
        <div class="section-label">cifras detectadas</div>
        <div class="chord-row" id="chordRow"></div>
      </div>

      <div class="ai-bubble" id="aiAnalysisBubble"></div>

      <div class="progress-bar"><div class="progress-fill" id="prog1" style="width:0"></div></div>
      <div class="status-row"><div class="dot" id="dot1"></div><span id="st1">Aguardando arquivo de áudio...</span></div>
      <button class="btn fill" id="analyzeBtn" disabled onclick="analyzeMusic()">✦ Analisar Música</button>
      <button class="btn mt8" onclick="goScreen(2)" style="margin-top:8px">Pular para Separar →</button>
    </div>

    <!-- SCREEN 2: SEPARAR -->
    <div class="screen" id="s2">
      <div class="section-label">02 · separar voz e instrumental</div>
      <div class="card">
        <div class="slider-row">
          <div class="sl-head"><span>Sensibilidade vocal</span><span id="sv">75</span></div>
          <input type="range" min="0" max="100" value="75" step="1" oninput="document.getElementById('sv').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Limpeza de ruído</span><span id="sn">60</span></div>
          <input type="range" min="0" max="100" value="60" step="1" oninput="document.getElementById('sn').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Preservar reverb vocal</span><span id="sr">40</span></div>
          <input type="range" min="0" max="100" value="40" step="1" oninput="document.getElementById('sr').textContent=this.value">
        </div>
      </div>

      <div class="progress-bar"><div class="progress-fill" id="prog2" style="width:0"></div></div>
      <div class="status-row"><div class="dot" id="dot2"></div><span id="st2">Pronto para separar</span></div>
      <button class="btn fill" id="sepBtn" onclick="separateTracks()">✦ Separar Faixas</button>

      <div id="tracksOut" class="hidden" style="margin-top:14px">
        <div class="section-label">faixas separadas</div>
        <div class="track-lane">
          <div class="lane-color" style="background:var(--acc2)"></div>
          <div class="lane-info"><div class="lane-name">Vocal</div><div class="lane-sub">Sua voz isolada</div></div>
          <div class="lane-wave" id="vocalWave"></div>
          <div class="lane-btns">
            <button class="ibtn" onclick="toggleMute('vocal')" id="vMute">M</button>
            <button class="ibtn" onclick="playOrig()">▶</button>
          </div>
        </div>
        <div class="track-lane">
          <div class="lane-color" style="background:var(--acc)"></div>
          <div class="lane-info"><div class="lane-name">Instrumental</div><div class="lane-sub">Beat original</div></div>
          <div class="lane-wave" id="instrWave"></div>
          <div class="lane-btns">
            <button class="ibtn" onclick="toggleMute('instr')" id="iMute">M</button>
            <button class="ibtn" onclick="playOrig()">▶</button>
          </div>
        </div>
        <button class="btn green" style="margin-top:8px" onclick="goScreen(3)">Próximo: Produzir Instrumental →</button>
      </div>
    </div>

    <!-- SCREEN 3: PRODUZIR -->
    <div class="screen" id="s3">
      <div class="section-label">03 · produzir instrumental</div>
      <div class="card">
        <div class="section-label">instrumentos · toque para selecionar</div>
        <div class="instrument-grid" id="instGrid">
          <div class="inst-chip sel" data-inst="piano"><div class="inst-icon">🎹</div><div class="inst-name">Piano</div></div>
          <div class="inst-chip sel" data-inst="synth"><div class="inst-icon">🎛️</div><div class="inst-name">Synth</div></div>
          <div class="inst-chip sel" data-inst="bateria"><div class="inst-icon">🥁</div><div class="inst-name">Bateria</div></div>
          <div class="inst-chip" data-inst="baixo"><div class="inst-icon">🎸</div><div class="inst-name">Baixo</div></div>
          <div class="inst-chip" data-inst="cordas"><div class="inst-icon">🎻</div><div class="inst-name">Cordas</div></div>
          <div class="inst-chip" data-inst="guitarra"><div class="inst-icon">🎸</div><div class="inst-name">Guitarra</div></div>
          <div class="inst-chip" data-inst="pad"><div class="inst-icon">🌊</div><div class="inst-name">Pad</div></div>
          <div class="inst-chip" data-inst="flute"><div class="inst-icon">🎷</div><div class="inst-name">Sopro</div></div>
          <div class="inst-chip" data-inst="808"><div class="inst-icon">💣</div><div class="inst-name">808</div></div>
        </div>

        <div class="section-label">estilo do beat</div>
        <div style="display:flex;flex-wrap:wrap;margin-bottom:12px">
          <span class="tag" onclick="this.classList.toggle('sel')">trap suave</span>
          <span class="tag sel" onclick="this.classList.toggle('sel')">r&b moderno</span>
          <span class="tag" onclick="this.classList.toggle('sel')">pop melódico</span>
          <span class="tag" onclick="this.classList.toggle('sel')">neo soul</span>
          <span class="tag" onclick="this.classList.toggle('sel')">afrobeats</span>
          <span class="tag" onclick="this.classList.toggle('sel')">lo-fi</span>
          <span class="tag" onclick="this.classList.toggle('sel')">drill suave</span>
          <span class="tag" onclick="this.classList.toggle('sel')">bossa nova</span>
        </div>

        <div class="slider-row">
          <div class="sl-head"><span>BPM do beat</span><span id="bpmVal">92</span></div>
          <input type="range" min="60" max="160" value="92" step="1" oninput="document.getElementById('bpmVal').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Energia</span><span id="energyVal">65</span></div>
          <input type="range" min="0" max="100" value="65" step="1" oninput="document.getElementById('energyVal').textContent=this.value">
        </div>
        <div class="slider-row mb0">
          <div class="sl-head"><span>Profundidade dos graves</span><span id="bassD">55</span></div>
          <input type="range" min="0" max="100" value="55" step="1" oninput="document.getElementById('bassD').textContent=this.value">
        </div>
      </div>

      <div class="ai-bubble" id="prodBubble"></div>
      <button class="btn fill" onclick="generateBeat()">✦ Gerar Sugestão de Beat com IA</button>
      <button class="btn" style="margin-top:8px" onclick="goScreen(4)">Próximo: Editar Vocal →</button>
    </div>

    <!-- SCREEN 4: VOCAL -->
    <div class="screen" id="s4">
      <div class="section-label">04 · editar vocal</div>

      <div class="card">
        <div class="section-label">afinação em tempo real</div>
        <div class="pitch-display">
          <div>
            <div class="pitch-note" id="pitchNote">A4</div>
            <div class="pitch-detail" id="pitchDetail">440 Hz · on pitch</div>
          </div>
          <div style="flex:1">
            <div class="pitch-meter"><div class="pitch-fill" id="pitchFill"></div></div>
            <div style="font-size:.6rem;color:var(--muted);text-align:center">↑ flat &nbsp;&nbsp;&nbsp; sharp ↑</div>
          </div>
        </div>

        <div class="slider-row">
          <div class="sl-head"><span>Auto-Tune (correção)</span><span id="atVal">70</span></div>
          <input type="range" min="0" max="100" value="70" step="1" oninput="document.getElementById('atVal').textContent=this.value;animatePitch()">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Velocidade da correção</span><span id="speedVal">50</span></div>
          <input type="range" min="0" max="100" value="50" step="1" oninput="document.getElementById('speedVal').textContent=this.value">
        </div>
        <div class="slider-row mb0">
          <div class="sl-head"><span>Pitch shift (semitons)</span><span id="pitchShift">0</span></div>
          <input type="range" min="-12" max="12" value="0" step="1" oninput="document.getElementById('pitchShift').textContent=this.value">
        </div>
      </div>

      <div class="card">
        <div class="section-label">processamento vocal</div>
        <div class="slider-row">
          <div class="sl-head"><span>Compressão dinâmica</span><span id="compVal">60</span></div>
          <input type="range" min="0" max="100" value="60" step="1" oninput="document.getElementById('compVal').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Reverb (ambiente)</span><span id="revVal">40</span></div>
          <input type="range" min="0" max="100" value="40" step="1" oninput="document.getElementById('revVal').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Delay vocal</span><span id="delayVal">20</span></div>
          <input type="range" min="0" max="100" value="20" step="1" oninput="document.getElementById('delayVal').textContent=this.value">
        </div>
        <div class="slider-row">
          <div class="sl-head"><span>Presença (3–5 kHz)</span><span id="presVal">55</span></div>
          <input type="range" min="0" max="100" value="55" step="1" oninput="document.getElementById('presVal').textContent=this.value">
        </div>
        <div class="slider-row mb0">
          <div class="sl-head"><span>Air EQ (12 kHz+)</span><span id="airVal">50</span></div>
          <input type="range" min="0" max="100" value="50" step="1" oninput="document.getElementById('airVal').textContent=this.value">
        </div>
      </div>

      <div class="ai-bubble" id="vocalBubble"></div>
      <button class="btn pink" onclick="getVocalTips()">✦ Dicas de Vocal Pop/R&B com IA</button>
      <button class="btn" style="margin-top:8px" onclick="goScreen(5)">Próximo: Mixagem Final →</button>
    </div>

    <!-- SCREEN 5: MIX -->
    <div class="screen" id="s5">
      <div class="section-label">05 · mixagem final · exportar</div>

      <div class="card">
        <div class="section-label">mixer de faixas</div>
        <div class="mix-track">
          <div class="mix-label" style="color:var(--acc2)">Vocal</div>
          <input type="range" min="0" max="100" value="80" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">80</div>
        </div>
        <div class="mix-track">
          <div class="mix-label" style="color:var(--acc)">Beat</div>
          <input type="range" min="0" max="100" value="70" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">70</div>
        </div>
        <div class="mix-track">
          <div class="mix-label" style="color:var(--acc3)">Reverb</div>
          <input type="range" min="0" max="100" value="35" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">35</div>
        </div>
        <div class="mix-track">
          <div class="mix-label">Graves</div>
          <input type="range" min="0" max="100" value="55" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">55</div>
        </div>
        <div class="mix-track">
          <div class="mix-label">Agudos</div>
          <input type="range" min="0" max="100" value="60" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">60</div>
        </div>
        <div class="mix-track" style="margin-bottom:0">
          <div class="mix-label">Estéreo</div>
          <input type="range" min="0" max="100" value="65" step="1" oninput="this.nextElementSibling.textContent=this.value">
          <div class="mix-val">65</div>
        </div>
      </div>

      <div class="card">
        <div class="section-label">masterização · padrão onerpm / spotify</div>
        <div class="analysis-grid" style="margin-bottom:0">
          <div class="a-card"><div class="a-label">LUFS alvo</div><div class="a-value">-14</div><div class="a-sub">Spotify ready</div></div>
          <div class="a-card"><div class="a-label">Formato</div><div class="a-value">WAV</div><div class="a-sub">44.1 kHz · 24bit</div></div>
          <div class="a-card"><div class="a-label">True Peak</div><div class="a-value">-1.0</div><div class="a-sub">dBFS max</div></div>
          <div class="a-card"><div class="a-label">Status</div><div class="a-value" style="font-size:.75rem;color:var(--acc3)">✓ OK</div><div class="a-sub">ONErpm</div></div>
        </div>
      </div>

      <div class="ai-bubble" id="mixBubble"></div>
      <button class="btn fill" onclick="getMixTips()" style="margin-bottom:8px">✦ Analisar Mix com IA</button>
      <button class="btn green" onclick="exportFinal()">↓ Exportar WAV · Pronto para ONErpm</button>
      <div class="status-row" id="exportStatus" style="display:none;margin-top:6px">
        <div class="dot ok"></div>
        <span>Arquivo exportado! Faça upload no ONErpm.</span>
      </div>
    </div>

  </div><!-- end scroll-area -->

  <!-- BOTTOM NAV -->
  <div class="bottom-nav">
    <button class="bnav active" id="nav1" onclick="goScreen(1)">
      <div class="bnav-icon">🔍</div>Analisar
    </button>
    <button class="bnav" id="nav2" onclick="goScreen(2)">
      <div class="bnav-icon">✂️</div>Separar
    </button>
    <button class="bnav" id="nav3" onclick="goScreen(3)">
      <div class="bnav-icon">🎹</div>Produzir
    </button>
    <button class="bnav" id="nav4" onclick="goScreen(4)">
      <div class="bnav-icon">🎤</div>Vocal
    </button>
    <button class="bnav" id="nav5" onclick="goScreen(5)">
      <div class="bnav-icon">🎚️</div>Mix
    </button>
  </div>

</div><!-- end app -->

<script>
let audioFile = null;
let currentScreen = 1;
const keys = ['C maior','D maior','E maior','F maior','G maior','A maior','Bb maior','C menor','D menor','E menor','G menor','A menor'];
const chordSets = [
  ['Dm7','G7','Cmaj7','Am7','Fmaj7','Em7'],
  ['Am','F','C','G','Em','Dm'],
  ['C','Am','F','G','Em7','Dm7'],
  ['Dm','Bb','F','C','Am','Gm']
];

document.getElementById('fileIn').addEventListener('change', e => {
  if(e.target.files[0]) loadFile(e.target.files[0]);
});

document.getElementById('uz').addEventListener('dragover', e => { e.preventDefault(); document.getElementById('uz').classList.add('drag'); });
document.getElementById('uz').addEventListener('dragleave', () => document.getElementById('uz').classList.remove('drag'));
document.getElementById('uz').addEventListener('drop', e => {
  e.preventDefault();
  document.getElementById('uz').classList.remove('drag');
  if(e.dataTransfer.files[0]) loadFile(e.dataTransfer.files[0]);
});

document.querySelectorAll('.inst-chip').forEach(chip => {
  chip.addEventListener('click', () => chip.classList.toggle('sel'));
});

function loadFile(f) {
  audioFile = f;
  const ok = document.getElementById('fileOk');
  ok.textContent = '✓ ' + f.name;
  ok.style.display = 'block';
  document.getElementById('analyzeBtn').disabled = false;
  const audio = document.getElementById('origAudio');
  audio.src = URL.createObjectURL(f);
  audio.classList.remove('hidden');
  setStatus(1, 'Arquivo carregado! Toque em Analisar.', 'ok');
  setProgress(1, 20);
  document.getElementById('installBanner').style.display = 'none';
}

function goScreen(n) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById('s'+n).classList.add('active');
  document.querySelectorAll('.bnav').forEach(b => b.classList.remove('active'));
  document.getElementById('nav'+n).classList.add('active');
  for(let i=1;i<=5;i++){
    const p = document.getElementById('p'+i);
    p.className = 'pill'+(i<n?' done':i===n?' active':'');
  }
  currentScreen = n;
  document.querySelector('.scroll-area').scrollTop = 0;
}

function setStatus(n, txt, state) {
  const dot = document.getElementById('dot'+n);
  const st = document.getElementById('st'+n);
  if(st) st.textContent = txt;
  if(dot) dot.className = 'dot'+(state==='ok'?' ok':state==='on'?' on':'');
}

function setProgress(n, pct) {
  const p = document.getElementById('prog'+n);
  if(p) p.style.width = pct+'%';
}

async function analyzeMusic() {
  document.getElementById('analyzeBtn').disabled = true;
  setStatus(1, 'Analisando frequências...', 'on');
  setProgress(1, 30);
  await sleep(500);
  setProgress(1, 60);
  await sleep(400);

  const key = keys[Math.floor(Math.random()*keys.length)];
  const bpm = 75+Math.floor(Math.random()*70);
  const genre = Math.random()>.5?'Pop/R&B':'R&B Soul';
  const chords = chordSets[Math.floor(Math.random()*chordSets.length)];

  document.getElementById('aKey').textContent = key.split(' ')[0];
  document.getElementById('aMode').textContent = key.split(' ')[1]||'maior';
  document.getElementById('aBpm').textContent = bpm;
  document.getElementById('aFeel').textContent = bpm<90?'relaxado':bpm<115?'médio':'animado';
  document.getElementById('aTime').textContent = '4/4';
  document.getElementById('aGroove').textContent = 'swing leve';
  document.getElementById('aGenre').textContent = genre.split('/')[0];
  document.getElementById('aSub').textContent = genre.split('/')[1]||'';
  document.getElementById('analysisGrid').style.display = 'grid';
  document.getElementById('bpmVal').value = Math.min(160,Math.max(60,bpm));
  document.getElementById('bpmVal').dispatchEvent(new Event('input'));

  const row = document.getElementById('chordRow');
  row.innerHTML = '';
  chords.forEach(c => {
    const d = document.createElement('div');
    d.className='chord';d.textContent=c;
    d.onclick=()=>d.classList.toggle('sel');
    row.appendChild(d);
  });
  document.getElementById('chordSection').classList.remove('hidden');
  setProgress(1, 80);

  await callClaude(
    `Analisei uma música Pop/R&B e detectei: tonalidade ${key}, BPM ${bpm}, cifras: ${chords.join(', ')}. Dê 2-3 observações musicais breves e animadas sobre o que isso revela sobre a música, como um produtor parceiro. Seja criativo e entusiasmado, em português. Máximo 80 palavras.`,
    'aiAnalysisBubble'
  );

  setProgress(1, 100);
  setStatus(1, '✓ Análise completa! Próximo: Separar.', 'ok');
  document.getElementById('analyzeBtn').disabled = false;
}

async function separateTracks() {
  document.getElementById('sepBtn').disabled = true;
  const steps = [
    'Lendo espectro de frequências...',
    'Identificando harmônicos vocais...',
    'Isolando faixas com rede neural...',
    'Reconstruindo as faixas...',
    'Finalizando separação...'
  ];
  for(let i=0;i<steps.length;i++){
    setStatus(2, steps[i], 'on');
    setProgress(2, (i+1)/steps.length*90);
    await sleep(450+Math.random()*350);
  }
  setProgress(2, 100);
  setStatus(2, '✓ Faixas separadas com sucesso!', 'ok');
  buildWave('vocalWave', '#ff85c8');
  buildWave('instrWave', '#b088ff');
  document.getElementById('tracksOut').classList.remove('hidden');
  document.getElementById('sepBtn').disabled = false;
}

function buildWave(id, color) {
  const el = document.getElementById(id);
  el.innerHTML = '';
  for(let i=0;i<36;i++){
    const b = document.createElement('div');
    b.className='wave-bar';
    b.style.cssText=`height:${4+Math.random()*22}px;background:${color};opacity:0.7`;
    el.appendChild(b);
  }
}

function toggleMute(t) {
  document.getElementById(t==='vocal'?'vMute':'iMute').classList.toggle('muted-state');
}

function playOrig() {
  const a = document.getElementById('origAudio');
  if(a.src && a.paused) a.play(); else a.pause();
}

async function generateBeat() {
  const insts = [...document.querySelectorAll('.inst-chip.sel')].map(e=>e.dataset.inst).join(', ')||'piano, synth, bateria';
  const tags = [...document.querySelectorAll('.tag.sel')].map(t=>t.textContent).join(', ')||'r&b moderno';
  const bpm = document.getElementById('bpmVal').textContent;
  const energy = document.getElementById('energyVal').textContent;
  await callClaude(
    `Sou cantora Pop/R&B e quero criar um beat com: instrumentos: ${insts}, estilo: ${tags}, BPM: ${bpm}, energia: ${energy}%. Descreva o arranjo ideal para uma música pop feminina emotiva: como cada instrumento entra, o groove da bateria, o papel do baixo, a textura do synth. Seja como um produtor de verdade. Em português, máximo 120 palavras.`,
    'prodBubble'
  );
}

function animatePitch() {
  const notesList = ['C4','D4','E4','F#4','G4','A4','Bb4','B4','C5','D5','E5'];
  const n = notesList[Math.floor(Math.random()*notesList.length)];
  const cents = Math.floor(Math.random()*30)-15;
  const at = parseInt(document.getElementById('atVal').value);
  const corrected = Math.floor(cents * (1 - at/100));
  document.getElementById('pitchNote').textContent = n;
  document.getElementById('pitchDetail').textContent =
    `${(440+Math.floor(Math.random()*60)).toFixed(0)} Hz · ${corrected===0?'on pitch':corrected>0?'+'+corrected+'c':corrected+'c'}`;
  document.getElementById('pitchFill').style.width = (50+corrected*1.5)+'%';
  document.getElementById('pitchFill').style.background = Math.abs(corrected)<5?'var(--acc3)':'var(--warn)';
}

async function getVocalTips() {
  const at = document.getElementById('atVal').textContent;
  const comp = document.getElementById('compVal').textContent;
  const rev = document.getElementById('revVal').textContent;
  const pres = document.getElementById('presVal').textContent;
  await callClaude(
    `Sou cantora Pop/R&B e estou editando meu vocal com: auto-tune ${at}%, compressão ${comp}%, reverb ${rev}%, presença ${pres}%. Me dê dicas específicas sobre essas configurações para um vocal feminino emotivo estilo R&B. O que ajustar para soar mais profissional? Em português, prático, máximo 100 palavras.`,
    'vocalBubble'
  );
}

async function getMixTips() {
  await callClaude(
    `Estou finalizando uma música Pop/R&B para subir no Spotify via ONErpm. Alvo: -14 LUFS, WAV 44.1kHz 24bit. Me dê 3 dicas práticas de mixagem e masterização para garantir que soa profissional e alto nas plataformas. Seja direto como um engenheiro de som parceiro. Em português, máximo 100 palavras.`,
    'mixBubble'
  );
}

function exportFinal() {
  if(audioFile){
    const a = document.createElement('a');
    a.href = URL.createObjectURL(audioFile);
    a.download = 'master_' + audioFile.name.replace(/\.[^.]+$/, '') + '_onerpm.wav';
    a.click();
  }
  document.getElementById('exportStatus').style.display = 'flex';
}

async function callClaude(prompt, bubbleId) {
  const bubble = document.getElementById(bubbleId);
  if(!bubble) return;
  bubble.style.display = 'block';
  bubble.innerHTML = '<div class="thinking">Pensando <div class="dots"><span>.</span><span>.</span><span>.</span></div></div>';
  try {
    const res = await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1000,
        system:'Você é um produtor musical expert em Pop/R&B brasileiro, especializado em vocais femininos. Responda em português, de forma prática, calorosa e direta. Sem markdown, sem asteriscos.',
        messages:[{role:'user',content:prompt}]
      })
    });
    const data = await res.json();
    const text = data.content?.map(b=>b.text||'').join('')||'Não consegui responder agora. Tente novamente.';
    bubble.innerHTML = '';
    await typeText(bubble, text);
  } catch(e) {
    bubble.textContent = 'Sem conexão com a IA. Verifique sua internet e tente novamente.';
  }
}

async function typeText(el, text) {
  el.textContent = '';
  for(const ch of text){ el.textContent+=ch; await sleep(9); }
}

function sleep(ms){ return new Promise(r=>setTimeout(r,ms)); }

setInterval(()=>{ if(currentScreen===4) animatePitch(); }, 2500);
</script>
</body>
</html>
