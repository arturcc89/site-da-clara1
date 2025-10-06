<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Clara — Motivação & Apoio</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#7c3aed;--muted:#9aa4b2;--glass:rgba(255,255,255,0.03)}
    *{box-sizing:border-box;font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,'Helvetica Neue',Arial}
    body{margin:0;background:linear-gradient(180deg,#071024 0%, #0f1724 100%);color:#e6eef6;min-height:100vh;overflow-x:hidden}
    header{display:flex;align-items:center;justify-content:space-between;padding:18px 24px;border-bottom:1px solid rgba(255,255,255,0.03)}
    h1{font-size:18px;margin:0}
    nav a{color:var(--muted);margin-left:14px;text-decoration:none;font-size:14px}
    .container{max-width:980px;margin:28px auto;padding:20px}
    .grid{display:grid;grid-template-columns:1fr 340px;gap:20px}
    .card{background:var(--card);padding:18px;border-radius:12px;box-shadow:0 6px 18px rgba(2,6,23,0.6);border:1px solid rgba(255,255,255,0.03)}
    section h2{margin-top:0}
    .section{margin-bottom:18px}
    .quotes{font-style:italic;color:#dfe9ff;padding:12px;border-radius:8px;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent)}
    .goals-list{list-style:none;padding:0;margin:12px 0}
    .goals-list li{display:flex;align-items:center;justify-content:space-between;padding:8px;border-radius:8px;background:var(--glass);margin-bottom:8px}
    .btn{display:inline-block;padding:8px 12px;border-radius:10px;background:var(--accent);color:white;text-decoration:none;border:none;cursor:pointer;transition:transform 0.15s ease}
    .btn:hover{transform:scale(1.05)}
    .muted{color:var(--muted);font-size:14px}
    input,textarea,select{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);background:transparent;color:inherit}
    .small{font-size:13px}
    .widget{margin-bottom:14px}
    .timer-display{font-size:28px;font-weight:700;text-align:center;padding:14px}
    footer{padding:18px;text-align:center;color:var(--muted);font-size:13px}
    @media(max-width:880px){.grid{grid-template-columns:1fr} .container{padding:12px}}
    .emoji-display{font-size:48px;text-align:center;margin-top:10px}
    .confetti{position:fixed;animation:fall 2.5s ease-out forwards}
    @keyframes fall{0%{opacity:1;transform:translateY(0) rotate(0deg)}100%{opacity:0;transform:translateY(400px) rotate(720deg)}}
  </style>
</head>
<body>
  <header>
    <h1>Clara — Motivação & Apoio</h1>
    <nav>
      <a href="#estudos">Estudos</a>
      <a href="#apoio">Apoio</a>
      <a href="#metas">Metas</a>
    </nav>
  </header>

  <main class="container">
    <div class="grid">
      <div>
        <section id="estudos" class="card section">
          <h2>📚 Estudos — Plano e Foco</h2>
          <p class="muted">Cronograma simples, timer Pomodoro e recursos rápidos para ajudar a Clara a manter o foco.</p>
          <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap">
            <button class="btn" id="startPom">Iniciar Pomodoro (25min)</button>
            <button class="btn" id="stopPom" style="background:#334155">Parar</button>
            <button class="btn" id="shortBreak">Pausa Curta</button>
            <button class="btn" id="longBreak">Pausa Longa</button>
          </div>
          <div class="timer-display card" id="timer">25:00</div>
        </section>

        <section id="apoio" class="card section">
          <h2>💗 Apoio — Mensagens & Motivação</h2>
          <textarea id="msgInput" rows="3" placeholder="Escreva uma mensagem para a Clara..."></textarea>
          <div style="display:flex;gap:8px;margin-top:8px">
            <button class="btn" id="saveMsg">Salvar mensagem</button>
            <button class="btn" id="clearMsgs" style="background:#334155">Limpar</button>
          </div>
          <h3 class="small" style="margin-top:12px">Mensagens salvas</h3>
          <ul id="msgs" class="muted"></ul>
          <h3 class="small" style="margin-top:12px">Frase do dia</h3>
          <div class="quotes" id="quote">Acredite no seu potencial — mesmo que hoje pareça difícil.</div>
        </section>

        <section id="metas" class="card section">
          <h2>🎯 Metas & Progresso</h2>
          <input id="newGoal" placeholder="Nova meta — Ex: Estudar Biologia 1h" />
          <button class="btn" id="addGoal">Adicionar</button>
          <ul class="goals-list" id="goals"></ul>
        </section>
      </div>

      <aside>
        <div class="card widget">
          <h3>Resumo Rápido</h3>
          <div class="muted small" id="summary">Nenhuma meta adicionada ainda.</div>
        </div>

        <div class="card widget">
          <h3>Check-in de Humor</h3>
          <select id="mood">
            <option value="5">😊 Muito bem</option>
            <option value="4">🙂 Bem</option>
            <option value="3">😐 Normal</option>
            <option value="2">😕 Estressada</option>
            <option value="1">😢 Triste</option>
          </select>
          <div style="margin-top:10px"><button class="btn" id="saveMood">Salvar humor</button></div>
          <div class="emoji-display" id="moodEmoji">🙂</div>
          <div class="muted small" id="moodSaved"></div>
          <p class="muted small" id="moodMessage">Lembre-se: todos os sentimentos são válidos. Respire fundo e siga em frente, Clara!</p>
        </div>

        <div class="card widget">
          <h3>Pequena celebração</h3>
          <p class="muted small">Concluiu algo importante? Clique e comemore com brilho e música!</p>
          <button class="btn" id="celebrate">Celebrar 🎉</button>
          <audio id="celebrateSound" src="https://cdn.pixabay.com/audio/2022/03/15/audio_b7f33e3c65.mp3"></audio>
        </div>
      </aside>
    </div>

    <footer class="card" style="margin-top:18px">
      <div><strong>Para Clara</strong> — você é mais forte do que imagina. ❤️<br><span class="muted">Editável: personalize mensagens, metas e o cronograma.</span></div>
    </footer>
  </main>

  <script>
    const $ = id => document.getElementById(id);

    function loadMsgs(){const msgs=JSON.parse(localStorage.getItem('clara_msgs')||'[]');const $msgs=$('msgs');$msgs.innerHTML='';msgs.forEach(m=>{const li=document.createElement('li');li.textContent=m;$msgs.appendChild(li);});}
    $('saveMsg').addEventListener('click',()=>{const t=$('msgInput').value.trim();if(!t)return alert('Escreva algo!');const msgs=JSON.parse(localStorage.getItem('clara_msgs')||'[]');msgs.unshift(t);localStorage.setItem('clara_msgs',JSON.stringify(msgs));$('msgInput').value='';loadMsgs();});
    $('clearMsgs').addEventListener('click',()=>{if(confirm('Limpar todas?')){localStorage.removeItem('clara_msgs');loadMsgs();}});
    loadMsgs();

    function renderGoals(){const goals=JSON.parse(localStorage.getItem('clara_goals')||'[]');const $goals=$('goals');$goals.innerHTML='';$('summary').textContent=goals.length?`${goals.length} meta(s)`:'Nenhuma meta.';goals.forEach((g,i)=>{const li=document.createElement('li');li.innerHTML=`<input type=checkbox ${g.done?'checked':''} data-i=${i}/> ${g.text}`;$goals.appendChild(li);});}
    $('addGoal').addEventListener('click',()=>{const t=$('newGoal').value.trim();if(!t)return;const goals=JSON.parse(localStorage.getItem('clara_goals')||'[]');goals.push({text:t,done:false});localStorage.setItem('clara_goals',JSON.stringify(goals));$('newGoal').value='';renderGoals();});
    renderGoals();

    $('saveMood').addEventListener('click',()=>{const val=$('mood').value;localStorage.setItem('clara_mood',val);const emojiMap={1:'😢',2:'😕',3:'😐',4:'🙂',5:'😊'};const msgMap={1:'Tudo bem ficar triste. Tire um tempo pra cuidar de você ❤️',2:'Vai passar, Clara! Faça algo leve e respire fundo 🌸',3:'Dias neutros também contam. Continue firme 💪',4:'Continue assim! Você está indo muito bem ✨',5:'Espalhe essa alegria, ela é contagiante 🌈'};$('moodEmoji').textContent=emojiMap[val];$('moodMessage').textContent=msgMap[val];$('moodSaved').textContent='Humor salvo!';setTimeout(()=>$('moodSaved').textContent='',2000);});

    const quotes=['Acredite no seu potencial — mesmo que hoje pareça difícil.','Pequenos passos, grandes conquistas. Você consegue, Clara!','Estudar com carinho é cuidar do seu futuro.','Falhar faz parte. Tente de novo — você está aprendendo.'];
    $('quote').textContent=quotes[Math.floor(Math.random()*quotes.length)];

    $('celebrate').addEventListener('click',()=>{
      const sound=$('celebrateSound');sound.currentTime=0;sound.play();
      for(let i=0;i<80;i++){
        const el=document.createElement('div');
        el.textContent=['🎉','✨','💖','🌟'][Math.floor(Math.random()*4)];
        el.className='confetti';
        el.style.left=Math.random()*window.innerWidth+'px';
        el.style.top='-20px';
        el.style.fontSize=(16+Math.random()*20)+'px';
        el.style.color='hsl('+Math.random()*360+',80%,70%)';
        document.body.appendChild(el);
        setTimeout(()=>el.remove(),2500);
      }
    });

    let timerInterval=null,remaining=25*60;function format(t){const m=Math.floor(t/60).toString().padStart(2,'0');const s=Math.floor(t%60).toString().padStart(2,'0');return `${m}:${s}`}
    function startTimer(sec){remaining=sec;clearInterval(timerInterval);$('timer').textContent=format(remaining);timerInterval=setInterval(()=>{remaining--;$('timer').textContent=format(remaining);if(remaining<=0){clearInterval(timerInterval);alert('Tempo encerrado!');}},1000);}
    $('startPom').addEventListener('click',()=>startTimer(25*60));$('shortBreak').addEventListener('click',()=>startTimer(5*60));$('longBreak').addEventListener('click',()=>startTimer(15*60));$('stopPom').addEventListener('click',()=>{clearInterval(timerInterval);$('timer').textContent='25:00';});
  </script>
</body>
</html>
