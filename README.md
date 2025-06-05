<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dismorfia | Salud Mental en Adolescentes</title>
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
      background: rgba(30,42,56,0.98); box-shadow: 0 3px 18px #1b232c88;
      z-index: 2002; display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw; font-size: 1.08em;
    }
    nav .nav-logo {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 1.34em; color: #6eb7e6; letter-spacing: 2px;
      text-shadow: 0 0 8px #0d1e2e33; display: flex; align-items: center;
    }
    nav ul { list-style: none; display: flex; gap: 2em; margin: 0; padding: 0;}
    nav ul li a {
      color: #6eb7e6; text-decoration: none; font-weight: 700; font-family: 'Quicksand', sans-serif;
      padding: 6px 12px; border-radius: 8px;
      transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus { background: #284b63; color: #fff; }
    header, main, footer { margin-top: 56px; }
    @media (max-width: 700px) { nav ul { gap: 1em; } nav .nav-logo { font-size: 1em; } }
    @media (max-width: 520px) {
      nav { font-size: 0.97em; padding: 0 1vw;}
      nav ul { gap: 0.6em;}
      header, main, footer { margin-top: 65px;}
    }
    #mirrors-bg {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      width: 100vw; height: 100vh;
      z-index: 0;
      overflow: hidden;
      pointer-events: none;
    }
    .mirror {
      position: absolute;
      width: 110px;
      height: 54px;
      background: linear-gradient(120deg, #23344a 65%, #284b63 100%);
      border-radius: 26px 26px 54px 54px / 26px 26px 54px 54px;
      box-shadow: 0 6px 22px #13344a55, 0 2px 18px #142e3add;
      opacity: 0.44;
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
    header { text-align: center; }
    h1 {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 2.9rem; color: #6eb7e6; margin-bottom: 0.3rem;
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
    .graph-section {
      margin-bottom: 2.7rem;
    }
    .graph-section h2 {
      font-size: 1.2em;
      color: #9fd3c7;
      margin-bottom: 1em;
    }
    .graph-container {
      display: flex;
      flex-wrap: wrap;
      gap: 2em;
      justify-content: center;
      align-items: flex-end;
      margin-bottom: 1em;
    }
    .bar-graph {
      width: 80px;
      background: linear-gradient(180deg, #9fd3c7 80%, #284b63 100%);
      border-radius: 13px 13px 0 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0 9px;
      text-align: center;
      box-shadow: 0 2px 14px #284b6322;
      color: #fff;
    }
    .bar {
      width: 100%;
      border-radius: 13px 13px 0 0;
      transition: height 1s;
      margin-bottom: 5px;
    }
    .bar-label {
      font-size: 0.96em;
      margin-bottom: 7px;
      color: #e3eaf2;
    }
    .bar-value {
      font-size: 1.12em;
      font-weight: bold;
      color: #9fd3c7;
      margin-bottom: 4px;
    }
    footer {
      text-align: center; font-size: 0.97rem; color: #6eb7e6; padding: 1.5rem 0; border-top: 1.5px solid #23344a;
      margin-top: auto; background: linear-gradient(90deg, #1e2a38, #23344a); letter-spacing: 1px; z-index: 2;
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.3rem;}
      .card { padding: 1.1rem 0.7rem;}
      .graph-container { flex-direction: column; align-items: center;}
    }
    @media (max-width: 480px) {
    }
  </style>
</head>
<body>
  <div id="mirrors-bg"></div>
  <nav>
    <div class="nav-logo">
      Dismorfia
    </div>
    <ul>
      <li>
        <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Salud Mental en Adolescentes</a>
      </li>
      <li>
        <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">Dismorfia en Adolescentes</a>
      </li>
      <li>
        <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Causas</a>
      </li>
      <li>
        <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Efectos</a>
      </li>
      <li>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">Cómo Combatir la Dismorfia</a>
      </li>
      <li>
        <a href="#campaign">Nuestra Campaña</a>
      </li>
      <li>
        <a href="#faq">FAQ</a>
      </li>
      <li>
        <a href="#creators">Creadores</a>
      </li>
    </ul>
  </nav>
  <header id="intro">
    <h1>Dismorfia</h1>
    <p class="subtitle">Salud mental y la imagen corporal en adolescentes</p>
  </header>
  <main>
    <section class="sr card" id="mentalhealth">
      <h2>¿Qué son los problemas de salud mental en adolescentes?</h2>
      <p>
        Los <strong>problemas de salud mental en adolescentes</strong> incluyen ansiedad, depresión, trastornos alimentarios y más. Según la OMS, <b>1 de cada 7 adolescentes de 10 a 19 años</b> tiene algún trastorno mental.<br><br>
        <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Fuente: OMS</a>
      </p>
      <blockquote>
        "La salud mental es tan importante como la salud física."
      </blockquote>
      <div class="fact-box">
        El suicidio es la <b>cuarta causa de muerte</b> en adolescentes de 15 a 19 años.
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Gráfico: Prevalencia de Trastornos Mentales en Adolescentes (Global)</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:110px;background:#6eb7e6;"></div>
          <div class="bar-value">~14%</div>
          <div class="bar-label">Cualquier trastorno mental</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:80px;background:#9fd3c7;"></div>
          <div class="bar-value">~5%</div>
          <div class="bar-label">Depresión</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:65px;background:#284b63;"></div>
          <div class="bar-value">~4%</div>
          <div class="bar-label">Ansiedad</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#9fd3c7">
        Datos de la OMS (<a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">fuente</a>)
      </div>
    </section>
    <section class="sr card" id="dysmorphia-teen">
      <h2>Dismorfia en Adolescentes</h2>
      <p>
        <strong>La dismorfia corporal</strong> es un trastorno en el que una persona se obsesiona con defectos percibidos en su apariencia física.<br>
        Según estudios revisados por NCBI, afecta alrededor del <b>2% de los adolescentes</b> a nivel mundial.<br>
        <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">Fuente: NCBI</a>
      </p>
      <div class="fact-box">
        La presión social, las redes y los cambios físicos durante la adolescencia aumentan el riesgo.
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Gráfico: Prevalencia de Dismorfia Corporal</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:30px;background:#9fd3c7;"></div>
          <div class="bar-value">2%</div>
          <div class="bar-label">Dismorfia diagnosticada</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:100px;background:#6eb7e6;"></div>
          <div class="bar-value">>50%</div>
          <div class="bar-label">Preocupaciones por la imagen corporal</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#9fd3c7">
        Estudios NCBI y UNICEF (<a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">NCBI</a>, <a href="https://www.unicef.org/parenting/child-care/teens-and-body-image" target="_blank">UNICEF</a>)
      </div>
    </section>
    <section class="sr card" id="causes">
      <h2>Causas de la dismorfia en adolescentes</h2>
      <ul>
        <li><strong>Pubertad:</strong> Cambios físicos rápidos</li>
        <li><strong>Redes sociales:</strong> Comparaciones y filtros</li>
        <li><strong>Bullying:</strong> Burlas sobre el aspecto</li>
        <li><strong>Familia/cultura:</strong> Presión para encajar</li>
        <li><strong>Salud mental:</strong> Ansiedad, depresión, TOC</li>
      </ul>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Fuente: Mind</a>
    </section>
    <section class="sr card" id="effects">
      <h2>Efectos de la dismorfia corporal en adolescentes</h2>
      <ul>
        <li>Baja autoestima</li>
        <li>Evitar espejos o revisión obsesiva</li>
        <li>Aislamiento</li>
        <li>Trastornos alimentarios, depresión, autolesiones</li>
        <li>Bajo rendimiento escolar</li>
      </ul>
      <blockquote>
        "Un espejo puede ser fuente de dolor en vez de reflexión."
      </blockquote>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Fuente: Mind</a>
    </section>
    <section class="sr card" id="combat">
      <h2>Cómo combatir y prevenir la dismorfia</h2>
      <ul>
        <li><b>Hablar:</b> Compartir preocupaciones</li>
        <li><b>Limitar redes:</b> Alejarse de cuentas negativas</li>
        <li><b>Enfocar en fortalezas:</b> Valorar talentos no físicos</li>
        <li><b>Alfabetización mediática:</b> Saber que las imágenes suelen estar retocadas</li>
        <li><b>Buscar ayuda profesional</b></li>
      </ul>
      <div class="fact-box">
        La prevención comienza con la aceptación y la información.<br>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">Fuente: IOCDF</a>
      </div>
    </section>
    <section class="sr card" id="campaign">
      <h2>Nuestra campaña: “Mírate con claridad”</h2>
      <ul>
        <li><b>Concientización:</b> Charlas en escuelas</li>
        <li><b>Autoaceptación:</b> Historias y recursos reales</li>
        <li><b>Luchar contra el estigma:</b> Espacios de diálogo</li>
        <li><b>Apoyo entre pares:</b> Grupos y recursos</li>
      </ul>
      <div class="fact-box">
        ¡Sumate! <span style="color:#9fd3c7"><b>#MirateConClaridad</b></span>
      </div>
    </section>
    <section class="sr card" id="faq">
      <h2>Preguntas frecuentes</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">¿Cuáles son los problemas más comunes?</div>
          <div class="faq-a">Ansiedad, depresión, trastornos alimentarios, autolesiones, preocupaciones por la imagen.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿La dismorfia afecta a varones?</div>
          <div class="faq-a">Sí, puede afectar a cualquier género.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Las redes sociales influyen mucho?</div>
          <div class="faq-a">Sí, pero también pueden ayudar si sigues cuentas positivas.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">¿Cómo ayudar a un amigo?</div>
          <div class="faq-a">Escuchar, apoyar y recomendar ayuda profesional si es necesario.</div>
        </li>
      </ul>
    </section>
    <section class="sr card" id="creators">
      <h2>Creadores</h2>
      <p>
        Página creada por <strong>Lucas De Cesare, Bautista Acerbo y Santiago Martinez</strong> como proyecto escolar para concientizar sobre dismorfia y salud mental en adolescentes.
      </p>
    </section>
    <section class="source-list" id="bibliografia">
      <h3>Bibliografía</h3>
      <ul>
        <li>
          World Health Organization. (2021). <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Adolescent Mental Health</a>.
        </li>
        <li>
          Veale, D., & Bewley, A. (2015). Body dysmorphic disorder. <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">NCBI</a>.
        </li>
        <li>
          Mind. (2023). Body Dysmorphic Disorder (BDD). <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">mind.org.uk</a>.
        </li>
        <li>
          IOCDF. (2023). About BDD. <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">iocdf.org</a>.
        </li>
        <li>
          UNICEF. (2022). Teens and Body Image. <a href="https://www.unicef.org/parenting/child-care/teens-and-body-image" target="_blank">unicef.org</a>.
        </li>
      </ul>
    </section>
  </main>
  <footer>
    <p>&copy; 2025 Dismorfia Awareness - Proyecto Escolar</p>
    <p>
      <a href="#intro" style="color: #9fd3c7;">↑ Volver arriba</a>
    </p>
  </footer>
  <script>
    // Moving mirrors background, dark style
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
        m.style.opacity = 0.5 + Math.random()*0.3;
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
  </script>
</body>
</html>
