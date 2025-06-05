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
    header {
      text-align: center;
      padding-top: 70px;
    }
    main, footer { margin-top: 0; }
    @media (max-width: 700px) { nav ul { gap: 1em; } nav .nav-logo { font-size: 1em; } }
    @media (max-width: 520px) {
      nav { font-size: 0.97em; padding: 0 1vw;}
      nav ul { gap: 0.6em;}
      header { padding-top: 80px;}
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
      width: 130px;
      background: linear-gradient(180deg, #9fd3c7 80%, #284b63 100%);
      border-radius: 13px 13px 0 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0 9px;
      text-align: center;
      box-shadow: 0 2px 14px #284b6322;
      color: #fff;
      position: relative;
    }
    .bar {
      width: 100%;
      border-radius: 13px 13px 0 0;
      transition: height 1s;
      margin-bottom: 5px;
      position: relative;
      display: flex;
      align-items: flex-end;
      justify-content: center;
    }
    .bar-value {
      font-size: 1.15em;
      font-weight: bold;
      color: #fff;
      margin-bottom: 4px;
      line-height:1.2;
      background: #23344ab8;
      border-radius: 8px;
      padding: 2px 6px 2px 6px;
      position: absolute;
      top: -35px;
      left: 50%;
      transform: translateX(-50%);
      min-width: 80px;
      box-sizing: border-box;
      z-index: 1;
    }
    .bar-label {
      font-size: 1em;
      margin-bottom: 7px;
      color: #e3eaf2;
      margin-top: 10px;
      line-height: 1.1;
      font-family: 'Quicksand', sans-serif;
      font-weight: 700;
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
      .bar-graph { width: 90px;}
    }
    @media (max-width: 480px) {
      .bar-graph { width: 70px;}
      .bar-value { min-width: 60px;}
    }
  </style>
</head>
<body>
  <div id="mirrors-bg"></div>
  <nav>
    <div class="nav-logo">
      Dysmorphia
    </div>
    <ul>
      <li>
        <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Adolescent Mental Health</a>
      </li>
      <li>
        <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">Dysmorphia in Adolescents</a>
      </li>
      <li>
        <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Causes</a>
      </li>
      <li>
        <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Effects</a>
      </li>
      <li>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">How to Combat Dysmorphia</a>
      </li>
      <li>
        <a href="#campaign">Our Campaign</a>
      </li>
      <li>
        <a href="#faq">FAQ</a>
      </li>
      <li>
        <a href="#creators">Creators</a>
      </li>
    </ul>
  </nav>
  <header id="intro">
    <h1>Dysmorphia</h1>
    <p class="subtitle">Mental health and body image in adolescents</p>
  </header>
  <main>
    <section class="sr card" id="mentalhealth">
      <h2>What are mental health issues in adolescents?</h2>
      <p>
        <strong>Mental health problems in adolescents</strong> include anxiety, depression, eating disorders, and more. According to WHO, <b>1 in 7 adolescents aged 10-19</b> experiences a mental disorder.<br><br>
        <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Source: WHO</a>
      </p>
      <blockquote>
        "Mental health is just as important as physical health."
      </blockquote>
      <div class="fact-box">
        Suicide is the <b>fourth leading cause of death</b> among adolescents aged 15 to 19.
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Graph: Prevalence of Mental Disorders in Adolescents (Global)</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:45px;background:#6eb7e6;">
            <div class="bar-value">14%<br>(168 million)</div>
          </div>
          <div class="bar-label">Any mental disorder</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:16px;background:#9fd3c7;">
            <div class="bar-value">5%<br>(60 million)</div>
          </div>
          <div class="bar-label">Depression</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:13px;background:#284b63;">
            <div class="bar-value">4%<br>(48 million)</div>
          </div>
          <div class="bar-label">Anxiety</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#9fd3c7">
        Source: WHO, 2021 (<a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">link</a>)
      </div>
      <div style="color:#e3eaf2;font-size:0.98em;margin-top:1em;">
        <b>Description:</b> This graph shows the estimated global percentage and number of adolescents affected by any mental disorder, depression, and anxiety.
      </div>
    </section>
    <section class="sr card" id="dysmorphia-teen">
      <h2>Dysmorphia in Adolescents</h2>
      <p>
        <strong>Body dysmorphia</strong> is a disorder in which a person becomes obsessed with perceived physical flaws.<br>
        According to studies reviewed by NCBI, it affects about <b>2% of adolescents</b> worldwide.<br>
        <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">Source: NCBI</a>
      </p>
      <div class="fact-box">
        Social pressure, media, and physical changes during adolescence increase the risk.
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Graph: Prevalence of Body Dysmorphia and Body Image Concerns</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:160px;background:#6eb7e6;">
            <div class="bar-value">&gt;50%<br>(600 million)</div>
          </div>
          <div class="bar-label">Body image concerns</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:6px;background:#9fd3c7;">
            <div class="bar-value">2%<br>(24 million)</div>
          </div>
          <div class="bar-label">Diagnosed dysmorphia</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#9fd3c7">
        Sources: NCBI, UNICEF (<a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">NCBI</a>, <a href="https://www.unicef.org/parenting/child-care/teens-and-body-image" target="_blank">UNICEF</a>)
      </div>
      <div style="color:#e3eaf2;font-size:0.98em;margin-top:1em;">
        <b>Description:</b> This graph compares the estimated percentage and number of adolescents diagnosed with body dysmorphia to those who experience body image concerns.
      </div>
    </section>
    <!-- ...rest of the sections as before... -->
    <section class="sr card" id="causes">
      <h2>Causes of dysmorphia in adolescents</h2>
      <ul>
        <li><strong>Puberty:</strong> Rapid physical changes</li>
        <li><strong>Social media:</strong> Comparisons and filters</li>
        <li><strong>Bullying:</strong> Teasing about looks</li>
        <li><strong>Family/culture:</strong> Pressure to fit in</li>
        <li><strong>Mental health:</strong> Anxiety, depression, OCD</li>
      </ul>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Source: Mind</a>
    </section>
    <section class="sr card" id="effects">
      <h2>Effects of body dysmorphia in adolescents</h2>
      <ul>
        <li>Low self-esteem</li>
        <li>Avoiding or obsessively checking mirrors</li>
        <li>Isolation</li>
        <li>Eating disorders, depression, self-harm</li>
        <li>Poor school performance</li>
      </ul>
      <blockquote>
        "A mirror can become a source of pain instead of reflection."
      </blockquote>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Source: Mind</a>
    </section>
    <section class="sr card" id="combat">
      <h2>How to combat and prevent dysmorphia</h2>
      <ul>
        <li><b>Talk about it:</b> Share your concerns</li>
        <li><b>Limit social media:</b> Unfollow negative accounts</li>
        <li><b>Focus on strengths:</b> Value non-physical talents</li>
        <li><b>Media literacy:</b> Know that most images are retouched</li>
        <li><b>Seek professional help</b></li>
      </ul>
      <div class="fact-box">
        Prevention starts with acceptance and information.<br>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">Source: IOCDF</a>
      </div>
    </section>
    <section class="sr card" id="campaign">
      <h2>Our campaign: “See Yourself Clearly”</h2>
      <ul>
        <li><b>Awareness:</b> School talks and workshops</li>
        <li><b>Self-acceptance:</b> Real stories and resources</li>
        <li><b>Fight stigma:</b> Safe spaces for open discussion</li>
        <li><b>Peer support:</b> Groups and resources</li>
      </ul>
      <div class="fact-box">
        Join us! <span style="color:#9fd3c7"><b>#SeeYourselfClearly</b></span>
      </div>
    </section>
    <section class="sr card" id="faq">
      <h2>Frequently Asked Questions</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">What are the most common problems?</div>
          <div class="faq-a">Anxiety, depression, eating disorders, self-harm, body image concerns.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Does dysmorphia affect boys?</div>
          <div class="faq-a">Yes, it can affect any gender.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Does social media have a big influence?</div>
          <div class="faq-a">Yes, but positive accounts can help too.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">How can I help a friend?</div>
          <div class="faq-a">Listen, support, and recommend professional help if needed.</div>
        </li>
      </ul>
    </section>
    <section class="sr card" id="creators">
      <h2>Creators</h2>
      <p>
        Page created by <strong>Lucas De Cesare, Bautista Acerbo, and Santiago Martinez</strong> as a school project to raise awareness about dysmorphia and adolescent mental health.
      </p>
    </section>
    <section class="source-list" id="bibliografia">
      <h3>References</h3>
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
    <p>&copy; 2025 Dysmorphia Awareness - School Project</p>
    <p>
      <a href="#intro" style="color: #9fd3c7;">↑ Back to top</a>
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
