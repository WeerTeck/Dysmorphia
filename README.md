<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dysmorphia | Understanding Body Image</title>
  <!-- Font: Merriweather for a more reflective, less techy feel -->
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700&family=Quicksand:wght@500;700&display=swap" rel="stylesheet" />
  <link rel="icon" type="image/png" href="https://cdn-icons-png.flaticon.com/512/1580/1580981.png">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'Merriweather', serif;
      background: #e6e7ee;
      color: #3a3a3a;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      line-height: 1.7;
      overflow-x: hidden;
      position: relative;
      transition: background 0.8s;
    }
    nav {
      position: fixed; top: 0; left: 0; right: 0; height: 56px;
      background: rgba(235,235,240,0.97); box-shadow: 0 3px 18px #bcbcbc33;
      z-index: 2002; display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw; font-size: 1.08em; transition: background 0.3s;
    }
    nav .nav-logo {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 1.34em; color: #6a89cc; letter-spacing: 2px;
      text-shadow: 0 0 8px #dff9fb55; display: flex; align-items: center;
    }
    nav ul { list-style: none; display: flex; gap: 2em; }
    nav ul li a {
      color: #355c7d; text-decoration: none; font-weight: 700; font-family: 'Quicksand', sans-serif;
      padding: 6px 12px; border-radius: 8px; transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus { background: #f7cac9; color: #fff; }
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
    /* Mirror "tiles" effect */
    .mirror {
      position: absolute;
      width: 120px;
      height: 60px;
      background: linear-gradient(120deg, #f7f1e3 70%, #b1b1b1 100%);
      border-radius: 23px 23px 50px 50px / 30px 30px 50px 50px;
      box-shadow: 0 8px 24px #adaeae55, 0 2px 24px #b8b6b6aa;
      opacity: 0.72;
      border: 2px solid #bfc9ca;
      transition: filter 0.5s;
      filter: blur(0.5px) brightness(1.08);
      animation: mirrorFloat 9s linear infinite;
      pointer-events: none;
    }
    .mirror.shine::after {
      content: "";
      display: block;
      position: absolute;
      left: 30%; top: 8%;
      width: 32px; height: 7px;
      background: linear-gradient(90deg, #fff8, #fff0 80%);
      border-radius: 7px;
      opacity: 0.55;
      transform: rotate(-18deg);
    }
    @keyframes mirrorFloat {
      0% { transform: translateY(0) scaleX(1) rotate(-8deg);}
      40% { filter: brightness(1.1) blur(1.5px);}
      50% { filter: brightness(1.18) blur(0.5px);}
      65% { filter: brightness(1.04) blur(0.2px);}
      100% { transform: translateY(16vh) scaleX(1.03) rotate(6deg);}
    }

    a { color: #6a89cc; text-decoration: none; transition: color 0.3s; }
    a:hover, a:focus { color: #b993d6; text-decoration: underline; outline: none; }
    header, main, footer {
      position: relative; z-index: 2; max-width: 920px; width: 93%; margin: auto; padding: 1.6rem 0;
    }
    header { text-align: center; }
    h1 {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 2.9rem; color: #6a89cc; margin-bottom: 0.3rem;
      letter-spacing: 2px; text-shadow: 0 1px 18px #b993d655, 0 0 6px #f7cac955;
      animation: text-glow 4s ease-in-out infinite alternate;
    }
    @keyframes text-glow {
      to { text-shadow: 0 0 35px #b993d6ff, 0 0 20px #f7cac9bb; }
    }
    .subtitle {
      font-family: 'Merriweather', serif;
      font-weight: 500; font-size: 1.22rem; color: #b993d6; margin-bottom: 3rem;
      text-shadow: 0 0 6px #b993d644; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(40px);} to { opacity: 1; transform: translateY(0);} }
    h2 {
      color: #6a89cc; margin-bottom: 1rem; font-weight: 700; font-size: 1.7rem;
      letter-spacing: 1px; font-family: 'Quicksand', sans-serif;
      text-shadow: 0 0 6px #b993d6aa;
    }
    section { margin-bottom: 2.7rem; }
    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.7s, transform 0.7s;}
    .sr.visible { opacity: 1; transform: translateY(0); }
    .card {
      background: rgba(255,255,255,0.88); border-radius: 21px; padding: 1.5rem 2rem;
      box-shadow: 0 1px 26px #b993d633; margin-bottom: 1.7rem; transition: box-shadow 0.3s, transform 0.3s;
      border: 1.5px solid #f7cac9;
    }
    .card:hover { box-shadow: 0 4px 38px #b993d655; transform: scale(1.02);}
    .gallery { display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; margin-bottom:2rem;}
    .gallery img {
      width: 31%; border-radius: 17px; box-shadow: 0 0 14px #b993d6aa, 0 5px 16px #bfc9ca55;
      cursor: pointer; transition: transform 0.35s, box-shadow 0.25s, filter 0.2s;
      filter: grayscale(0.1) brightness(1.08); border: 2px solid #b993d6;
      background: #fff;
    }
    .gallery img:hover, .gallery img:focus {
      transform: scale(1.12) rotate(-2deg); box-shadow: 0 0 30px #b993d6ff, 0 0 10px #fff5;
      filter: grayscale(0) brightness(1.12); border-color: #f7cac9; outline: none; z-index: 3;
    }
    .modal-img { display: none; position: fixed; z-index: 1200; left: 0; top: 0; width: 100vw; height: 100vh; background: rgba(247,202,201,0.9); justify-content: center; align-items: center; animation: fadeIn 0.2s;}
    .modal-img.active { display: flex; }
    .modal-img img { max-width: 90vw; max-height: 80vh; border-radius: 22px; box-shadow: 0 0 50px #b993d6cc; border: 4px solid #b993d6; animation: imgpop 0.3s;}
    @keyframes imgpop { from { transform: scale(0.68);} to { transform: scale(1);} }
    .modal-img .close-modal {
      position: absolute; top: 35px; right: 55px; font-size: 2.5rem; color: #b993d6;
      background: transparent; border: none; cursor: pointer; z-index: 1300; transition: color 0.2s;
    }
    .modal-img .close-modal:hover { color: #355c7d; }
    ul.faq-list { list-style: none; padding: 0;}
    .faq-item { margin-bottom: 1.7em;}
    .faq-q { font-weight: 700; font-size: 1.08em; color: #b993d6; margin-bottom: 0.2em;}
    .faq-a { font-size: 1.01em; color: #3a3a3a; }
    footer {
      text-align: center; font-size: 0.97rem; color: #888; padding: 1.5rem 0; border-top: 1.5px solid #bfc9ca;
      margin-top: auto; background: linear-gradient(90deg, #f7f1e3, #e6e7ee); letter-spacing: 1px; z-index: 2;
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .gallery img { width: 48%; }
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.3rem;}
      .card { padding: 1.1rem 0.7rem;}
    }
    @media (max-width: 480px) {
      .gallery img { width: 100%; }
    }
    /* Quote block */
    blockquote {
      background: #f7cac922;
      border-left: 6px solid #b993d6;
      margin: 1.3em 0;
      padding: 1.1em 1.2em 1.1em 1.8em;
      font-style: italic;
      color: #6a89cc;
      border-radius: 12px;
      box-shadow: 0 2px 18px #b993d611;
    }
    .fact-box {
      background: #f7cac944;
      color: #3a3a3a;
      border: 1.5px solid #b993d6;
      border-radius: 13px;
      padding: 1em 1.3em;
      margin: 1.1em 0;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.09em;
      box-shadow: 0 2px 14px #b993d622;
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
      <li><a href="#intro">Home</a></li>
      <li><a href="#what">What is it?</a></li>
      <li><a href="#causes">Causes</a></li>
      <li><a href="#symptoms">Symptoms</a></li>
      <li><a href="#effects">Effects</a></li>
      <li><a href="#impact">Social Impact</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#tips">Tips</a></li>
      <li><a href="#faq">FAQ</a></li>
      <li><a href="#creators">Creators</a></li>
    </ul>
  </nav>
  <header id="intro">
    <h1>Dysmorphia</h1>
    <p class="subtitle">Exploring Body Image, Reflection and Self-Perception</p>
  </header>
  <main>
    <section class="sr card" id="what">
      <h2>What is Body Dysmorphia?</h2>
      <p>
        <strong>Body Dysmorphic Disorder (BDD)</strong>, often called body dysmorphia, is a mental health condition where a person becomes overly concerned with perceived flaws in their appearance—even if these flaws are minor or invisible to others. This can lead to emotional distress and difficulty in daily life.
      </p>
      <blockquote>
        "The mirror can become an enemy, reflecting not how we are, but how we fear we might be."
      </blockquote>
      <div class="fact-box">
        <strong>Did you know?</strong> Up to <b>2.5% of teenagers</b> may experience body dysmorphia at some point.
      </div>
    </section>
    <section class="sr card" id="causes">
      <h2>Causes</h2>
      <ul>
        <li><b>Genetics:</b> Family history of BDD, anxiety, or OCD.</li>
        <li><b>Environment:</b> Experiences of bullying, teasing, or trauma about looks.</li>
        <li><b>Media & Culture:</b> Pressure from social media, advertising, and beauty standards.</li>
        <li><b>Personality:</b> Perfectionism, low self-esteem, or high sensitivity to appearance.</li>
      </ul>
      <div class="fact-box">
        <b>Social media</b> filters and photo-editing apps have increased body image concerns among young people.
      </div>
    </section>
    <section class="sr card" id="symptoms">
      <h2>Common Symptoms</h2>
      <ul>
        <li>Spending hours thinking about perceived "flaws"</li>
        <li>Checking mirrors repeatedly—or avoiding them altogether</li>
        <li>Trying to hide or “fix” certain body parts</li>
        <li>Comparing oneself to others constantly</li>
        <li>Seeking constant reassurance about appearance</li>
        <li>Feeling anxious, sad, or even angry after seeing reflections</li>
      </ul>
    </section>
    <section class="sr card" id="effects">
      <h2>Effects on Daily Life</h2>
      <ul>
        <li>Low self-esteem and lack of confidence</li>
        <li>Difficulty making friends or going out</li>
        <li>Withdrawing from activities you once enjoyed</li>
        <li>Obsessive thoughts and repetitive behaviors</li>
        <li>Missing school or work</li>
        <li>In severe cases: depression, eating disorders, or self-harm</li>
      </ul>
      <blockquote>
        "Sometimes a mirror shows us not reality, but our greatest fears and insecurities."
      </blockquote>
    </section>
    <section class="sr card" id="impact">
      <h2>Social Impact & Stigma</h2>
      <p>
        Body dysmorphia often leads to <b>isolation</b>. People might avoid social events or hide behind filters online. 
        <br>
        <b>Stigma</b> and misunderstanding can make it harder to seek help or talk openly.
      </p>
      <div class="fact-box">
        <b>Fact:</b> BDD is not "vanity"—it is a serious, recognized mental health condition.
      </div>
    </section>
    <section class="sr" id="gallery">
      <h2>Gallery</h2>
      <div class="gallery" aria-label="Body Dysmorphia Visuals">
        <img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&w=600&q=80" alt="Person looking at their reflection in a mirror" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80" alt="Distorted reflection" loading="lazy" tabindex="0" />
        <img src="https://images.pexels.com/photos/1707828/pexels-photo-1707828.jpeg?auto=compress&w=600&q=80" alt="Hidden face, low self-esteem" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1519125323398-675f0ddb6308?auto=format&fit=crop&w=600&q=80" alt="A hand over a foggy mirror" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1464983953574-0892a716854b?auto=format&fit=crop&w=600&q=80" alt="Fragmented mirror reflecting a face" loading="lazy" tabindex="0" />
      </div>
    </section>
    <section class="sr card" id="tips">
      <h2>Tips for Coping & Self-Compassion</h2>
      <ul>
        <li>Talk to someone you trust about your feelings.</li>
        <li>Limit time on social media and follow positive accounts.</li>
        <li>Write down things you <b>like</b> about yourself—not just appearance.</li>
        <li>Practice being kind to your reflection—say one positive thing every day.</li>
        <li>Remember nobody is perfect, and many images online are edited or filtered.</li>
        <li>Seek support from a counselor, therapist, or helpline if needed.</li>
      </ul>
      <div class="fact-box">
        <b>Remember:</b> It’s okay to ask for help. Everyone deserves to feel comfortable in their own skin.
      </div>
    </section>
    <section class="sr card" id="faq">
      <h2>Frequently Asked Questions</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">Is dysmorphia only about weight?</div>
          <div class="faq-a">No, it can be about any feature—skin, hair, nose, scars, or any body part.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Can boys and men have dysmorphia?</div>
          <div class="faq-a">Yes, dysmorphia affects people of all genders and ages.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Is BDD the same as being insecure?</div>
          <div class="faq-a">No. While related, BDD is a disorder with obsessive thoughts and behaviors beyond common insecurities.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">What should I do if I think I have BDD?</div>
          <div class="faq-a">Talk to someone you trust and consider reaching out to a mental health professional.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Does looking in the mirror help or hurt?</div>
          <div class="faq-a">For some, checking the mirror gives reassurance; for others, it increases anxiety. Balance and support are key.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Is there a cure?</div>
          <div class="faq-a">BDD can improve a lot with therapy, support, and self-care, even if it's not “cured” in a traditional sense.</div>
        </li>
      </ul>
    </section>
    <section class="sr card" id="creators">
      <h2>Creators</h2>
      <p>
        This page was created by <strong>Lucas De Cesare, Bautista Acerbo, and Santiago Martinez</strong> as a school project to raise awareness about body dysmorphia.
      </p>
      <div style="margin-top:1.3em;color:#b993d6;font-size:1.08em;">
        <i>“Our aim is to reflect the truth: that everyone deserves to feel valued, just as they are.”</i>
      </div>
    </section>
  </main>
  <footer>
    <p>&copy; 2025 Dysmorphia Awareness - School Project</p>
    <p>
      <a href="#intro" style="color: #b993d6;">↑ Back to top</a>
    </p>
  </footer>
  <div class="modal-img" id="modalImg" role="dialog" aria-modal="true" aria-label="Enlarged gallery image">
    <button class="close-modal" id="closeModalImg" aria-label="Close">&times;</button>
    <img src="" alt="Enlarged gallery" id="modalImgSrc" />
  </div>
  <script>
    // Moving mirrors background
    function createMirrors(n = 18) {
      const bg = document.getElementById('mirrors-bg');
      let vw = window.innerWidth, vh = window.innerHeight;
      bg.innerHTML = '';
      for(let i=0; i<n; i++) {
        let m = document.createElement('div');
        m.className = 'mirror shine';
        // Randomize position, speed, size, animation delay
        let left = Math.random() * (vw - 100);
        let top = Math.random() * (vh - 70);
        let scale = 0.8 + Math.random() * 0.7;
        let delay = Math.random() * 8;
        let rot = -18 + Math.random()*36;
        m.style.left = left+'px';
        m.style.top = top+'px';
        m.style.transform = `scale(${scale}) rotate(${rot}deg)`;
        m.style.animationDelay = `${delay}s`;
        m.style.opacity = 0.6 + Math.random()*0.3;
        bg.appendChild(m);
      }
    }
    window.addEventListener('resize', ()=>createMirrors());
    window.addEventListener('DOMContentLoaded', ()=>createMirrors());

    // Animate mirrors down then reset to top
    setInterval(()=>{
      const mirrors = document.querySelectorAll('.mirror');
      const vh = window.innerHeight;
      mirrors.forEach(m=>{
        let currTop = parseFloat(m.style.top || 0);
        let speed = 0.15 + Math.random()*0.23; // px per tick
        let nextTop = currTop + speed;
        if(nextTop > vh - 40) nextTop = -60;
        m.style.top = nextTop + 'px';
      });
    }, 32);

    // Scroll reveal
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

      // Modal for gallery
      const galleryImgs = document.querySelectorAll('.gallery img');
      const modalImg = document.getElementById('modalImg');
      const modalImgSrc = document.getElementById('modalImgSrc');
      const closeModalImg = document.getElementById('closeModalImg');
      galleryImgs.forEach(img => {
        img.addEventListener('click', () => {
          modalImgSrc.src = img.src;
          modalImg.classList.add('active');
        });
        img.addEventListener('keydown', e => {
          if(e.key === "Enter" || e.key === " ") {
            modalImgSrc.src = img.src;
            modalImg.classList.add('active');
          }
        });
      });
      closeModalImg.addEventListener('click', () => {
        modalImg.classList.remove('active');
      });
      modalImg.addEventListener('click', (e) => {
        if(e.target === modalImg) modalImg.classList.remove('active');
      });
      window.addEventListener('keydown', (e) => {
        if(e.key === "Escape") modalImg.classList.remove('active');
      });
    });
  </script>
</body>
</html>
