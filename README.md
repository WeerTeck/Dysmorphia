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
    #animated-bg {
      position: fixed;
      top: 0; left: 0; width: 100vw; height: 100vh;
      pointer-events: none;
      z-index: 0;
      overflow: hidden;
    }
    .person-mirror {
      position: absolute;
      width: 210px;
      height: 340px;
      opacity: 0.36;
      will-change: transform;
      transition: opacity 0.7s;
    }
    .person-mirror .mirror-shape {
      fill: #284b63;
      filter: drop-shadow(0 6px 18px #132e3a88);
    }
    .person-mirror .person {
      transition: transform 0.7s;
    }
    .person-mirror .reflection {
      opacity: 0.85;
      filter: blur(1.2px) brightness(1.13);
      transition: transform 0.7s;
    }
    .person-mirror .reflection.sad {
      filter: blur(2px) brightness(0.8) grayscale(0.5);
      opacity: 0.7;
    }
    @media (max-width: 700px) {
      .person-mirror { width: 120px; height: 180px; }
    }
    #mirrors-bg {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      width: 100vw; height: 100vh;
      z-index: 1;
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
    @keyframes popWord { 0%{transform:scale(1);} 50%{transform:scale(1.25);} 100%{transform:scale(1);} }
    .popword { color: #9fd3c7; font-weight: bold; animation: popWord 1.1s infinite alternate; }
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
  <div id="animated-bg"></div>
  <div id="mirrors-bg"></div>
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
    <section class="sr card" id="mentalhealth">
      <h2>What are mental health issues in adolescents?</h2>
      <p>
        <strong class="highlight-on-hover">Mental health problems in adolescents</strong> include anxiety, depression, eating disorders, self-harm, and more. According to WHO, <b>1 in 7 adolescents aged 10-19</b> experiences a mental disorder.<br><br>
        <a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">Source: WHO</a>
      </p>
      <ul style="margin-bottom:1.1em;">
        <li>
          <b>Global prevalence of any mental disorder:</b>
          <span class="counter" data-target="168000000">0</span> adolescents (14%)
        </li>
        <li>
          <b>Depression:</b>
          <span class="counter" data-target="60000000">0</span> adolescents (5%)
        </li>
        <li>
          <b>Anxiety:</b>
          <span class="counter" data-target="48000000">0</span> adolescents (4%)
        </li>
        <li>
          <b>Eating disorders:</b>
          <span class="counter" data-target="40000000">0</span> adolescents (3.3%)
        </li>
        <li>
          <b>Self-harm:</b>
          <span class="counter" data-target="25000000">0</span> adolescents (2.1%)
        </li>
      </ul>
      <blockquote>
        "Mental health is just as important as physical health."
      </blockquote>
      <div class="fact-box">
        Suicide is the <b class="highlight-on-hover">fourth leading cause of death</b> among adolescents aged 15 to 19.
      </div>
    </section>
    <section class="sr card" id="dysmorphia-teen">
      <h2>What is Body Dysmorphia?</h2>
      <p>
        <strong class="highlight-on-hover">Body dysmorphia</strong> (Body Dysmorphic Disorder, BDD) is a mental health condition where a person spends a lot of time worrying about flaws in their appearance. These flaws are often unnoticeable to others.<br>
        <span style="color:#9fd3c7"><b>Key facts:</b></span>
        <ul>
          <li>BDD can begin as early as 12–13 years old and often gets worse over time if untreated.</li>
          <li>It affects about <b>2%–3% of adolescents</b> worldwide, but body image concerns are much more common.</li>
          <li>Young people with dysmorphia may avoid social situations, mirrors, or spend hours trying to change their appearance.</li>
        </ul>
        <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">Source: NCBI</a>
      </p>
      <ul style="margin-bottom:1.1em;">
        <li>
          <b>Adolescents with body image concerns:</b>
          <span class="counter" data-target="600000000">0</span> (over 50% worldwide)
        </li>
        <li>
          <b>Diagnosed body dysmorphia:</b>
          <span class="counter" data-target="24000000">0</span> (2% worldwide)
        </li>
        <li>
          <b>Girls are slightly more likely to report body image issues, but BDD affects all genders.</b>
        </li>
      </ul>
      <div class="fact-box">
        <b>Symptoms:</b><br>
        - Obsessively thinking about perceived flaws<br>
        - Excessive grooming or mirror checking<br>
        - Seeking cosmetic procedures<br>
        - Comparing appearance to others constantly<br>
        - Low self-esteem, anxiety, or depression<br>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/bdd-in-children-and-adolescents/" target="_blank">More info: IOCDF</a>
      </div>
      <div class="fact-box">
        <b>Did you know?</b> Teens with BDD are at higher risk for eating disorders, substance abuse, social withdrawal, and suicidal thoughts.
      </div>
    </section>
    <section class="sr card" id="causes">
      <h2>Causes of dysmorphia in adolescents</h2>
      <ul>
        <li><strong class="highlight-on-hover">Puberty:</strong> Rapid body changes can lead to confusion and insecurity.</li>
        <li><strong>Social media:</strong> Unrealistic beauty standards, filters, and constant comparison increase dissatisfaction.</li>
        <li><strong>Bullying:</strong> Teasing or criticism about looks can trigger negative self-image.</li>
        <li><strong>Family/culture:</strong> Pressure to fit in or meet certain norms.</li>
        <li><strong>Mental health:</strong> Anxiety, depression, or obsessive-compulsive tendencies raise the risk.</li>
        <li><strong>Low self-esteem:</strong> Feeling “not good enough” or unworthy.</li>
        <li><strong>Genetics:</strong> Having a family member with BDD or OCD can increase risk.</li>
      </ul>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Source: Mind</a>
    </section>
    <section class="sr card" id="effects">
      <h2>Effects of body dysmorphia in adolescents</h2>
      <ul>
        <li><span class="popword">Low self-esteem</span> and negative self-image</li>
        <li>Avoiding or obsessively checking mirrors</li>
        <li>Withdrawing from friends, family, or activities</li>
        <li>Problems at school (concentration, absenteeism, poor grades)</li>
        <li>Eating disorders (anorexia, bulimia, binge eating)</li>
        <li>Excessive exercise or unhealthy dieting</li>
        <li>Self-harm or suicidal thoughts</li>
        <li>Seeking cosmetic surgery (even when not recommended)</li>
        <li>Anxiety and depression</li>
        <li>Substance abuse</li>
      </ul>
      <blockquote>
        "A mirror can become a source of pain instead of reflection."
      </blockquote>
      <a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Source: Mind</a>
    </section>
    <section class="sr card" id="combat">
      <h2>How to combat and prevent dysmorphia</h2>
      <ul>
        <li><b class="popword">Talk about it:</b> Share your concerns with someone you trust (friend, parent, counselor).</li>
        <li><b>Limit social media:</b> Unfollow negative accounts and spend less time comparing yourself to others.</li>
        <li><b>Focus on strengths:</b> Value non-physical talents and qualities.</li>
        <li><b>Media literacy:</b> Know that most images are retouched, filtered, or staged.</li>
        <li><b>Seek professional help:</b> Psychologists, psychiatrists, and counselors can help with therapy and coping skills.</li>
        <li><b>Practice self-compassion:</b> Treat yourself with the same kindness you’d offer a friend.</li>
        <li><b>Support groups:</b> Sharing with others can reduce stigma and provide hope.</li>
        <li><b>Healthy routines:</b> Sleep, exercise, and eating well improve mood and resilience.</li>
      </ul>
      <div class="fact-box">
        Prevention starts with <span class="highlight-on-hover">acceptance</span> and information.<br>
        <a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">Source: IOCDF</a>
      </div>
    </section>
    <section class="sr card" id="campaign">
      <h2>Our campaign: “See Yourself Clearly”</h2>
      <ul>
        <li><b class="popword">Awareness:</b> School talks and workshops</li>
        <li><b>Self-acceptance:</b> Real stories and resources</li>
        <li><b>Fight stigma:</b> Safe spaces for open discussion</li>
        <li><b>Peer support:</b> Groups and resources</li>
        <li><b>Encourage positive self-talk</b></li>
        <li><b>Advocate for healthier media</b></li>
      </ul>
      <div class="fact-box">
        Join us! <span style="color:#9fd3c7"><b>#SeeYourselfClearly</b></span>
      </div>
    </section>
    <section class="sr card" id="faq">
      <h2>Frequently Asked Questions</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <button class="faq-q" type="button">What are the most common problems?</button>
          <div class="faq-a">Anxiety, depression, eating disorders, self-harm, body image concerns.</div>
        </li>
        <li class="faq-item">
          <button class="faq-q" type="button">Does dysmorphia affect boys?</button>
          <div class="faq-a">Yes, it can affect any gender.</div>
        </li>
        <li class="faq-item">
          <button class="faq-q" type="button">Does social media have a big influence?</button>
          <div class="faq-a">Yes, but positive accounts can help too.</div>
        </li>
        <li class="faq-item">
          <button class="faq-q" type="button">How can I help a friend?</button>
          <div class="faq-a">Listen, support, and recommend professional help if needed.</div>
        </li>
        <li class="faq-item">
          <button class="faq-q" type="button">Can dysmorphia lead to other problems?</button>
          <div class="faq-a">Yes, it can increase the risk of eating disorders, depression, anxiety, and suicidal thoughts.</div>
        </li>
        <li class="faq-item">
          <button class="faq-q" type="button">Is it treatable?</button>
          <div class="faq-a">Yes! With therapy and support, most young people see improvement.</div>
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
          IOCDF: BDD in Children and Adolescents. <a href="https://iocdf.org/about-ocd/related-disorders/bdd/bdd-in-children-and-adolescents/" target="_blank">iocdf.org</a>.
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
  <button id="presentationBtn">Modo presentación</button>
  <div id="timer">00:00</div>
  <audio id="applause" src="https://cdn.pixabay.com/audio/2022/11/16/audio_12c3a7ab6d.mp3"></audio>
  <button id="applauseBtn" style="display:none;position:fixed;left:30px;bottom:24px;z-index:3000;background:#6eb7e6;color:#1e2a38;font-size:1.2em;font-family:'Quicksand',sans-serif;border:none;border-radius:10px;padding:10px 20px;box-shadow:0 2px 8px #284b6355;cursor:pointer;">👏 Aplausos</button>
  <script>
    // Fondo animado de personas viéndose al espejo
    (function(){
      const bg = document.getElementById('animated-bg');
      function createPersonMirror({x, y, flip, mood}) {
        let reflectColor = mood === "sad" ? "#1e2a38" : "#9fd3c7";
        let reflectClass = mood === "sad" ? "reflection sad" : "reflection";
        let svg = `
        <svg width="100%" height="100%" viewBox="0 0 210 340">
          <ellipse class="mirror-shape" cx="105" cy="170" rx="90" ry="145" />
          <g class="person" style="transform:translate(60px,125px)">
            <ellipse cx="45" cy="58" rx="28" ry="37" fill="#e3eaf2" />
            <rect x="28" y="95" width="34" height="70" rx="16" fill="#6eb7e6"/>
            <ellipse cx="45" cy="180" rx="15" ry="30" fill="#9fd3c7"/>
          </g>
          <g class="${reflectClass}" style="transform:translate(60px,145px)">
            <ellipse cx="45" cy="60" rx="27" ry="35" fill="${reflectColor}" />
            <rect x="28" y="95" width="34" height="70" rx="16" fill="${reflectColor}"/>
            <ellipse cx="45" cy="180" rx="15" ry="28" fill="${reflectColor}"/>
            ${mood === "sad" ? `<ellipse cx="45" cy="82" rx="10" ry="4" fill="#263648"/>
              <path d="M36 83 Q45 75 54 83" stroke="#263648" stroke-width="2" fill="none"/>` :
              `<ellipse cx="45" cy="80" rx="7" ry="3" fill="#fff"/>
              <path d="M39 80 Q45 88 51 80" stroke="#fff" stroke-width="2" fill="none"/>`}
          </g>
        </svg>`;
        let div = document.createElement('div');
        div.className = 'person-mirror';
        div.style.left = x + 'vw';
        div.style.top = y + 'vh';
        if(flip) div.style.transform = "scaleX(-1)";
        div.innerHTML = svg;
        bg.appendChild(div);
        return div;
      }
      function drawPersons() {
        bg.innerHTML = "";
        let configs = [
          {x:10, y:18, flip:false, mood:'sad'},
          {x:70, y:35, flip:true, mood:'happy'},
          {x:25, y:65, flip:false, mood:'happy'},
          {x:65, y:72, flip:true, mood:'sad'}
        ];
        if(window.innerWidth < 900) configs = [
          {x:10, y:18, flip:false, mood:'sad'},
          {x:65, y:72, flip:true, mood:'happy'}
        ];
        configs.forEach(cfg=>createPersonMirror(cfg));
      }
      drawPersons();
      window.addEventListener('resize', drawPersons);

      window.addEventListener('scroll', function() {
        let scroll = window.scrollY;
        let wh = window.innerHeight;
        let docH = document.body.scrollHeight;
        let persons = bg.querySelectorAll('.person-mirror');
        persons.forEach((el, i)=>{
          let baseTop = parseFloat(el.style.top);
          let offset = Math.sin((scroll/wh + i) * 1.5) * 12;
          el.style.top = (baseTop + offset) + 'vh';
          let svg = el.querySelector('svg');
          let reflect = svg.querySelector('.reflection');
          if(reflect) {
            if(scroll > (docH-wh)/2 && i%2===0) reflect.classList.add('sad');
            else reflect.classList.remove('sad');
          }
          el.style.opacity = 0.23 + 0.22 * Math.abs(Math.cos((scroll+i*99)/900));
        });
      });
    })();

    // Resto de scripts
    const navBtn = document.getElementById('navMenuBtn');
    const navLinks = document.getElementById('navLinks');
    navBtn.onclick = function() {
      navLinks.classList.toggle('show');
    };
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

    document.addEventListener('DOMContentLoaded', () => {
      document.querySelectorAll('.faq-q').forEach(btn => {
        btn.addEventListener('click', () => {
          const ans = btn.nextElementSibling;
          ans.style.display = (ans.style.display === 'block') ? 'none' : 'block';
          btn.classList.toggle('open');
        });
      });
      document.querySelectorAll('.faq-a').forEach(a => a.style.display = 'none');
    });

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
