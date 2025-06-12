<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dysmorphia | Mental Health in Adolescents</title>
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&family=Quicksand:wght@500;700&display=swap" rel="stylesheet" />
  <link rel="icon" type="image/png" href="https://cdn-icons-png.flaticon.com/512/1580/1580981.png">
  <style>
    body {
      font-family: 'Merriweather', serif;
      background: linear-gradient(135deg, #1e2a38 10%, #27394a 90%);
      color: #e3eaf2;
      min-height: 100vh;
      margin: 0;
      display: flex;
      flex-direction: column;
      line-height: 1.7;
      overflow-x: hidden;
    }
    nav {
      position: fixed; top: 0; left: 0; right: 0; height: 56px;
      background: #1e2a38; box-shadow: 0 3px 18px #1b232c88;
      z-index: 2002; display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw; font-size: 1.08em;
    }
    .nav-logo {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 1.25em; color: #6eb7e6; letter-spacing: 2px;
      text-shadow: 0 0 8px #0d1e2e33; display: flex; align-items: center;
      margin-right: 1vw;
    }
    .nav-links {
      display: flex; flex-wrap: wrap; gap: 1em; align-items: center;
    }
    .nav-links a {
      color: #e3eaf2; background: none; text-decoration: none; font-weight: 700; font-family: 'Quicksand', sans-serif;
      padding: 6px 11px; border-radius: 7px; transition: background 0.2s, color 0.2s;
      font-size: 0.99em;
    }
    .nav-links a:hover, .nav-links a:focus { background: #284b63; color: #fff; }
    .nav-dropdown {
      position: relative;
    }
    .nav-dropdown-content {
      display: none;
      position: absolute;
      background: #23344a;
      min-width: 160px;
      box-shadow: 0 8px 22px #0004;
      border-radius: 9px;
      top: 34px; left: 0;
      z-index: 5000;
    }
    .nav-dropdown:hover .nav-dropdown-content,
    .nav-dropdown:focus-within .nav-dropdown-content {
      display: block;
    }
    .nav-dropdown-content a {
      display: block;
      color: #6eb7e6;
      padding: 9px 16px;
      border-radius: 0;
      background: none;
      font-size: 1em;
      margin: 0;
    }
    .nav-dropdown-content a:hover { background: #284b63; color: #fff; }
    .nav-menu-btn {
      display: none;
      background: none;
      border: none;
      color: #6eb7e6;
      font-size: 2em;
      margin-left: 1vw;
      cursor: pointer;
    }
    @media (max-width: 850px) {
      .nav-links { gap: 0.4em; }
      nav { font-size: 0.99em; }
      .nav-logo { font-size: 1em;}
    }
    @media (max-width: 700px) {
      .nav-links {
        display: none;
        position: absolute;
        flex-direction: column;
        top: 56px; left: 0; right: 0;
        background: #1e2a38;
        gap: 0;
        padding: 10px 0 10px 0;
        border-bottom: 2px solid #23344a;
      }
      .nav-links.show { display: flex; }
      .nav-menu-btn { display: block; }
      .nav-dropdown-content { position: static; box-shadow: none; min-width: 0;}
      .nav-dropdown-content a { padding: 10px 18px;}
    }
    #mirrors-bg {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      width: 100vw; height: 100vh;
      z-index: 0;
      overflow: hidden;
      pointer-events: none;
    }
    /* NUEVO: Fondo de personas con dismorfia */
    #dysmorphia-people-bg {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      width: 100vw; height: 100vh;
      z-index: 1;
      pointer-events: none;
      overflow: hidden;
    }
    .mirror {
      position: absolute;
      width: 110px;
      height: 54px;
      background: linear-gradient(120deg, #23344a 65%, #284b63 100%);
      border-radius: 26px 26px 54px 54px / 26px 26px 54px 54px;
      box-shadow: 0 6px 22px #13344a55, 0 2px 18px #142e3add;
      opacity: 0.35;
      border: 2px solid #284b63;
      filter: blur(0.9px) brightness(1.04);
      animation: mirrorFloat 8s linear infinite;
      pointer-events: none;
    }
    .mirror.shine::after {
      content: "";
      display: block;
      position: absolute;
      left: 35%; top: 8%;
      width: 23px; height: 8px;
      background: linear-gradient(90deg, #fff3, #fff0 80%);
      border-radius: 6px;
      opacity: 0.43;
      transform: rotate(-18deg);
    }
    /* NUEVO: Personas con dismorfia fondo */
    .dysmorphia-person {
      position: absolute;
      z-index: 1;
      width: 170px;
      height: 120px;
      opacity: 0.24;
      pointer-events: none;
      user-select: none;
      transition: filter 0.3s;
      filter: blur(0.5px) brightness(1.12);
    }
    @media (max-width: 700px) {
      .dysmorphia-person { width: 110px; height: 80px; }
    }
    @keyframes mirrorFloat {
      0% { transform: translateY(0) scaleX(1) rotate(-8deg);}
      40% { filter: brightness(1.08) blur(1.1px);}
      50% { filter: brightness(1.13) blur(0.4px);}
      65% { filter: brightness(1.03) blur(0.2px);}
      100% { transform: translateY(16vh) scaleX(1.03) rotate(6deg);}
    }
    a { color: #6eb7e6; text-decoration: none; transition: color 0.3s; }
    a:hover, a:focus { color: #9fd3c7; text-decoration: underline; outline: none; }
    header, main, footer {
      position: relative; z-index: 2; max-width: 920px; width: 93%; margin: auto; padding: 1.6rem 0;
    }
    h1 {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 2.6rem; color: #6eb7e6; margin-bottom: 0.3rem;
      letter-spacing: 2px; text-shadow: 0 1px 18px #284b6355, 0 0 6px #9fd3c755;
      animation: text-glow 4s ease-in-out infinite alternate;
    }
    @keyframes text-glow {
      to { text-shadow: 0 0 35px #6eb7e6aa, 0 0 20px #9fd3c7bb; }
    }
    .subtitle {
      font-family: 'Merriweather', serif;
      font-weight: 500; font-size: 1.22rem; color: #9fd3c7; margin-bottom: 3rem;
      text-shadow: 0 0 6px #9fd3c744; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(40px);} to { opacity: 1; transform: translateY(0);} }
    h2 {
      color: #6eb7e6; margin-bottom: 1rem; font-weight: 700; font-size: 1.7rem;
      letter-spacing: 1px; font-family: 'Quicksand', sans-serif;
      text-shadow: 0 0 6px #284b63aa;
    }
    section { margin-bottom: 2.7rem; }
    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.7s, transform 0.7s;}
    .sr.visible { opacity: 1; transform: translateY(0); }
    .card {
      background: rgba(30,42,56,0.96); border-radius: 21px; padding: 1.5rem 2rem;
      box-shadow: 0 1px 26px #284b6333; margin-bottom: 1.7rem; transition: box-shadow 0.3s, transform 0.3s;
      border: 1.5px solid #23344a;
    }
    .card:hover { box-shadow: 0 4px 38px #284b6355; transform: scale(1.02);}
    .fact-box {
      background: #23344a44;
      color: #e3eaf2;
      border: 1.5px solid #6eb7e6;
      border-radius: 13px;
      padding: 1em 1.3em;
      margin: 1.1em 0;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.09em;
      box-shadow: 0 2px 14px #284b6322;
    }
    blockquote {
      background: #23344a22;
      border-left: 6px solid #6eb7e6;
      margin: 1.3em 0;
      padding: 1.1em 1.2em 1.1em 1.8em;
      font-style: italic;
      color: #6eb7e6;
      border-radius: 12px;
      box-shadow: 0 2px 18px #284b6311;
    }
    .source-list {
      margin: 2.5em 0 1em 0;
      padding: 1em 1.8em;
      background: #23344a;
      border-radius: 14px;
      box-shadow: 0 0 12px #284b6333;
    }
    .source-list h3 {
      color: #9fd3c7;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.09em;
      margin-bottom: 0.7em;
    }
    .source-list ul {
      list-style: disc inside;
      color: #6eb7e6;
      font-size: 1em;
      margin: 0;
      padding: 0;
    }
    footer {
      text-align: center; font-size: 0.97rem; color: #6eb7e6; padding: 1.5rem 0; border-top: 1.5px solid #23344a;
      margin-top: auto; background: linear-gradient(90deg, #1e2a38, #23344a); letter-spacing: 1px; z-index: 2;
    }
    /* FAQ styles */
    .faq-q {
      background: #23344a;
      color: #9fd3c7;
      border: none;
      width: 100%;
      text-align: left;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.07em;
      font-weight: bold;
      padding: 9px 0;
      border-radius: 7px;
      cursor: pointer;
      outline: none;
      margin-bottom: 3px;
      transition: background 0.2s;
    }
    .faq-q.open, .faq-q:hover { background: #284b63; color: #fff; }
    .faq-a {
      padding: 8px 0 8px 16px;
      color: #e3eaf2;
      font-size: 0.98em;
      margin-bottom: 10px;
      background: none;
      border-left: 3px solid #6eb7e6;
      border-radius: 0 7px 7px 0;
      transition: all 0.3s;
      display: none;
    }
    /* Presentación */
    #presentationBtn {
      position:fixed;bottom:22px;right:24px;z-index:3000;
      background:#6eb7e6;color:#1e2a38;border:none;
      padding:13px 20px;border-radius:50px;box-shadow:0 2px 18px #284b6355;
      font-size:1.09em;font-family:'Quicksand',sans-serif;font-weight:700;cursor:pointer;
    }
    #timer {
      display:none;position:fixed;top:68px;right:24px;z-index:3002;
      background:#23344a;color:#9fd3c7;padding:9px 18px;border-radius:8px;
      font-family:'Quicksand',sans-serif;font-size:1.1em;
    }
    /* Palabra clave animada */
    @keyframes popWord { 0%{transform:scale(1);} 50%{transform:scale(1.25);} 100%{transform:scale(1);} }
    .popword { color: #9fd3c7; font-weight: bold; animation: popWord 1.1s infinite alternate; }
    /* Resaltador */
    .highlight-on-hover:hover {
      background: #9fd3c7;
      color: #1e2a38;
      font-weight: bold;
      box-shadow: 0 0 8px #6eb7e666;
      transition: all 0.2s;
      border-radius: 4px;
      cursor: pointer;
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.3rem;}
      .card { padding: 1.1rem 0.7rem;}
    }
  </style>
</head>
<body>
  <div id="mirrors-bg"></div>
  <div id="dysmorphia-people-bg"></div>
  <nav>
    <div class="nav-logo">Dysmorphia</div>
    <button class="nav-menu-btn" id="navMenuBtn">&#9776;</button>
    <div class="nav-links" id="navLinks">
      <a href="#mentalhealth">Mental Health</a>
      <a href="#dysmorphia-teen">Dysmorphia</a>
      <div class="nav-dropdown">
        <a href="#">More ▼</a>
        <div class="nav-dropdown-content">
          <a href="#causes">Causes</a>
          <a href="#effects">Effects</a>
          <a href="#combat">How to Combat</a>
          <a href="#campaign">Our Campaign</a>
          <a href="#faq">FAQ</a>
          <a href="#creators">Creators</a>
        </div>
      </div>
      <a href="#bibliografia">References</a>
    </div>
  </nav>
  <header id="intro">
    <h1>Dysmorphia</h1>
    <p class="subtitle">Mental health and body image in adolescents</p>
  </header>
  <main>
    <!-- ... (el resto de tus secciones igual que antes) ... -->
    <!-- Pega aquí tu contenido de <main> tal como ya lo tenías -->
    <!-- OMITIDO POR ESPACIO, pero no cambia respecto al HTML que enviaste -->
    <!-- ... -->
  </main>
  <footer>
    <p>&copy; 2025 Dysmorphia Awareness - School Project</p>
    <p>
      <a href="#intro" style="color: #9fd3c7;">↑ Back to top</a>
    </p>
  </footer>
  <!-- Presentación & temporizador -->
  <button id="presentationBtn">Modo presentación</button>
  <div id="timer">00:00</div>
  <!-- Aplausos -->
  <audio id="applause" src="https://cdn.pixabay.com/audio/2022/11/16/audio_12c3a7ab6d.mp3"></audio>
  <button id="applauseBtn" style="display:none;position:fixed;left:30px;bottom:24px;z-index:3000;background:#6eb7e6;color:#1e2a38;font-size:1.2em;font-family:'Quicksand',sans-serif;border:none;border-radius:10px;padding:10px 20px;box-shadow:0 2px 8px #284b6355;cursor:pointer;">👏 Aplausos</button>
  <script>
    // Mobile nav menu
    const navBtn = document.getElementById('navMenuBtn');
    const navLinks = document.getElementById('navLinks');
    navBtn.onclick = function() {
      navLinks.classList.toggle('show');
    };
    // Background mirrors
    function createMirrors(n = 15) {
      const bg = document.getElementById('mirrors-bg');
      let vw = window.innerWidth, vh = window.innerHeight;
      bg.innerHTML = '';
      for(let i=0; i<n; i++) {
        let m = document.createElement('div');
        m.className = 'mirror shine';
        let left = Math.random() * (vw - 90);
        let top = Math.random() * (vh - 60);
        let scale = 0.8 + Math.random() * 0.7;
        let delay = Math.random() * 8;
        let rot = -18 + Math.random()*36;
        m.style.left = left+'px';
        m.style.top = top+'px';
        m.style.transform = `scale(${scale}) rotate(${rot}deg)`;
        m.style.animationDelay = `${delay}s`;
        m.style.opacity = 0.3 + Math.random()*0.2;
        bg.appendChild(m);
      }
    }
    window.addEventListener('resize', ()=>createMirrors());
    window.addEventListener('DOMContentLoaded', ()=>createMirrors());
    setInterval(()=>{
      const mirrors = document.querySelectorAll('.mirror');
      const vh = window.innerHeight;
      mirrors.forEach(m=>{
        let currTop = parseFloat(m.style.top || 0);
        let speed = 0.13 + Math.random()*0.21;
        let nextTop = currTop + speed;
        if(nextTop > vh - 40) nextTop = -60;
        m.style.top = nextTop + 'px';
      });
    }, 32);
    // NUEVO: crear personas con dismorfia en el fondo
    function createDysmorphiaPeople(n = 7) {
      const bg = document.getElementById('dysmorphia-people-bg');
      const vw = window.innerWidth, vh = window.innerHeight;
      bg.innerHTML = '';
      // SVGs simples: silueta y reflejo distorsionado
      const variants = [
        // Persona normal, reflejo más delgado
        `<svg width="170" height="120" viewBox="0 0 170 120" fill="none" xmlns="http://www.w3.org/2000/svg">
          <ellipse cx="85" cy="100" rx="60" ry="16" fill="#23344a88"/>
          <rect x="42" y="22" width="86" height="56" rx="37" fill="#324b63" stroke="#6eb7e6" stroke-width="2"/>
          <!-- Persona real -->
          <ellipse cx="85" cy="62" rx="20" ry="38" fill="#6eb7e6"/>
          <!-- Reflejo flaco -->
          <ellipse cx="85" cy="62" rx="12" ry="42" fill="#9fd3c7" opacity="0.78" transform="translate(30,34) scale(0.7,1)"/>
        </svg>`,
        // Persona delgada, reflejo más ancho
        `<svg width="170" height="120" viewBox="0 0 170 120" fill="none" xmlns="http://www.w3.org/2000/svg">
          <ellipse cx="85" cy="100" rx="60" ry="16" fill="#23344a77"/>
          <rect x="42" y="22" width="86" height="56" rx="37" fill="#324b63" stroke="#6eb7e6" stroke-width="2"/>
          <!-- Persona real -->
          <ellipse cx="85" cy="62" rx="12" ry="39" fill="#6eb7e6"/>
          <!-- Reflejo ancho -->
          <ellipse cx="85" cy="62" rx="24" ry="37" fill="#9fd3c7" opacity="0.78" transform="translate(-28,6) scale(1.17,1)"/>
        </svg>`,
        // Persona normal, reflejo más bajo
        `<svg width="170" height="120" viewBox="0 0 170 120" fill="none" xmlns="http://www.w3.org/2000/svg">
          <ellipse cx="85" cy="100" rx="60" ry="16" fill="#23344a77"/>
          <rect x="42" y="22" width="86" height="56" rx="37" fill="#324b63" stroke="#6eb7e6" stroke-width="2"/>
          <!-- Persona real -->
          <ellipse cx="85" cy="62" rx="18" ry="35" fill="#6eb7e6"/>
          <!-- Reflejo bajito -->
          <ellipse cx="85" cy="92" rx="20" ry="15" fill="#9fd3c7" opacity="0.78"/>
        </svg>`,
        // Persona normal, reflejo más alto
        `<svg width="170" height="120" viewBox="0 0 170 120" fill="none" xmlns="http://www.w3.org/2000/svg">
          <ellipse cx="85" cy="100" rx="60" ry="16" fill="#23344a77"/>
          <rect x="42" y="22" width="86" height="56" rx="37" fill="#324b63" stroke="#6eb7e6" stroke-width="2"/>
          <!-- Persona real -->
          <ellipse cx="85" cy="62" rx="18" ry="35" fill="#6eb7e6"/>
          <!-- Reflejo alto -->
          <ellipse cx="85" cy="42" rx="15" ry="46" fill="#9fd3c7" opacity="0.78"/>
        </svg>`
      ];
      for(let i=0; i<n; i++) {
        let div = document.createElement('div');
        div.className = 'dysmorphia-person';
        div.style.left = (Math.random() * (vw - 180)) + 'px';
        div.style.top = (Math.random() * (vh - 130)) + 'px';
        div.style.transform = `scale(${0.94 + Math.random()*0.3}) rotate(${Math.random()*14-7}deg)`;
        div.innerHTML = variants[i % variants.length];
        bg.appendChild(div);
      }
    }
    window.addEventListener('resize', ()=>createDysmorphiaPeople());
    window.addEventListener('DOMContentLoaded', ()=>createDysmorphiaPeople());

    document.addEventListener('DOMContentLoaded', () => {
      const srs = document.querySelectorAll('.sr');
      function scrollReveal() {
        srs.forEach(el => {
          const rect = el.getBoundingClientRect();
          if(rect.top < window.innerHeight - 60) el.classList.add('visible');
        });
      }
      window.addEventListener('scroll', scrollReveal);
      scrollReveal();
    });
    // Contador animado para los datos
    function animateCounters() {
      const counters = document.querySelectorAll('.counter');
      counters.forEach(counter => {
        const updateCount = () => {
          const target = +counter.getAttribute('data-target');
          const current = +counter.innerText.replace(/,/g, '');
          const increment = Math.max(Math.ceil(target / 100), 1);
          if (current < target) {
            let next = current + increment;
            if (next > target) next = target;
            counter.innerText = next.toLocaleString();
            setTimeout(updateCount, 16);
          } else {
            counter.innerText = target.toLocaleString();
          }
        };
        updateCount();
      });
    }
    window.addEventListener('DOMContentLoaded', animateCounters);

    // FAQ interactivo
    document.addEventListener('DOMContentLoaded', () => {
      document.querySelectorAll('.faq-q').forEach(btn => {
        btn.addEventListener('click', () => {
          const ans = btn.nextElementSibling;
          ans.style.display = (ans.style.display === 'block') ? 'none' : 'block';
          btn.classList.toggle('open');
        });
      });
      // Ocultar todas las respuestas al inicio
      document.querySelectorAll('.faq-a').forEach(a => a.style.display = 'none');
    });

    // --- PRESENTACIÓN: Modo diapositiva, temporizador y aplausos ---
    (function(){
      let presentationMode = false, currSection = 0;
      const sections = Array.from(document.querySelectorAll('main > section'));
      const btn = document.getElementById('presentationBtn');
      let timerInterval, seconds=0, timerDiv=document.getElementById('timer');
      const applauseBtn = document.getElementById('applauseBtn');
      function showSection(idx) {
        sections.forEach((sec, i) => {
          sec.style.display = (i===idx) ? 'block' : 'none';
        });
        if (presentationMode && idx === sections.length - 1) applauseBtn.style.display = 'block';
        else applauseBtn.style.display = 'none';
      }
      function startTimer(){
        timerDiv.style.display='block'; seconds=0;
        timerDiv.innerText='00:00';
        timerInterval = setInterval(()=>{
          seconds++; timerDiv.innerText=
            String(Math.floor(seconds/60)).padStart(2,'0')+':'+String(seconds%60).padStart(2,'0');
        },1000);
      }
      function stopTimer(){
        timerDiv.style.display='none';
        clearInterval(timerInterval);
      }
      btn.addEventListener('click', function() {
        presentationMode = !presentationMode;
        if(presentationMode){
          currSection=0; showSection(currSection);
          btn.innerText='Siguiente ▶';
          btn.title='Avanza a la siguiente sección';
          document.body.style.overflow='hidden';
          startTimer();
        } else {
          sections.forEach(sec=>sec.style.display='');
          btn.innerText='Modo presentación';
          btn.title='';
          document.body.style.overflow='';
          stopTimer();
          applauseBtn.style.display='none';
        }
      });
      document.addEventListener('keydown', (e)=>{
        if(!presentationMode) return;
        if(e.key==='ArrowRight'||e.key===' '){
          currSection = Math.min(currSection+1, sections.length-1);
          showSection(currSection);
        }else if(e.key==='ArrowLeft'){
          currSection = Math.max(currSection-1, 0);
          showSection(currSection);
        }
      });
      applauseBtn.onclick = ()=>document.getElementById('applause').play();
    })();
  </script>
</body>
</html>
