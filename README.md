<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Dysmorphia | Understanding Body Image</title>
  <!-- Modern font: Poppins -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet" />
  <link rel="icon" type="image/png" href="https://cdn-icons-png.flaticon.com/512/1580/1580981.png">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #232526 0%, #414345 100%);
      color: #f3f3f3;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      line-height: 1.6;
      overflow-x: hidden;
      position: relative;
    }
    nav {
      position: fixed; top: 0; left: 0; right: 0; height: 56px;
      background: rgba(44,62,80,0.97); box-shadow: 0 3px 16px #5b86e5cc;
      z-index: 2002; display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw; font-size: 1.08em; transition: background 0.3s;
    }
    nav .nav-logo {
      font-weight: 900; font-size: 1.28em; color: #5b86e5; letter-spacing: 2px;
      text-shadow: 0 0 8px #5b86e577; display: flex; align-items: center;
    }
    nav ul { list-style: none; display: flex; gap: 2em; }
    nav ul li a {
      color: #f3f3f3; text-decoration: none; font-weight: 600;
      padding: 6px 10px; border-radius: 7px; transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus { background: #5b86e5; color: #fff; }
    header, main, footer { margin-top: 56px; }
    @media (max-width: 700px) { nav ul { gap: 1em; } nav .nav-logo { font-size: 1em; } }
    @media (max-width: 520px) {
      nav { font-size: 0.97em; padding: 0 1vw;}
      nav ul { gap: 0.6em;}
      header, main, footer { margin-top: 65px;}
    }
    #particles-js {
      position: fixed; top: 0; left: 0; right: 0; bottom: 0; z-index: 0;
      pointer-events: none; width: 100vw; height: 100vh;
    }
    a { color: #5b86e5; text-decoration: none; transition: color 0.3s; }
    a:hover, a:focus { color: #dee0fc; text-decoration: underline; outline: none; }
    header, main, footer {
      position: relative; z-index: 2; max-width: 900px; width: 90%; margin: auto; padding: 1.5rem 0;
    }
    header { text-align: center; }
    h1 {
      font-weight: 800; font-size: 2.7rem; color: #5b86e5; margin-bottom: 0.3rem;
      text-shadow: 0 0 18px #5b86e5cc, 0 0 6px #5b86e577; letter-spacing: 2px;
      animation: text-glow 2.5s ease-in-out infinite alternate;
    }
    @keyframes text-glow {
      to { text-shadow: 0 0 35px #5b86e5ff, 0 0 10px #dee0fc88; }
    }
    .subtitle {
      font-weight: 600; font-size: 1.2rem; color: #dee0fc; margin-bottom: 3rem;
      text-shadow: 0 0 6px #dee0fc88; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(40px);} to { opacity: 1; transform: translateY(0);} }
    h2 {
      color: #5b86e5; margin-bottom: 1rem; font-weight: 700; font-size: 1.8rem;
      text-shadow: 0 0 6px #5b86e5bb; letter-spacing: 1px;
    }
    section { margin-bottom: 2.5rem; }
    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.6s, transform 0.6s;}
    .sr.visible { opacity: 1; transform: translateY(0); }
    .card {
      background: rgba(44,62,80,0.85); border-radius: 16px; padding: 1.2rem 1.6rem;
      box-shadow: 0 2px 24px #5b86e566; margin-bottom: 1.5rem; transition: box-shadow 0.3s, transform 0.3s;
    }
    .card:hover { box-shadow: 0 4px 40px #5b86e5cc; transform: scale(1.03);}
    .gallery { display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; margin-bottom:2rem;}
    .gallery img {
      width: 31%; border-radius: 14px; box-shadow: 0 0 16px #5b86e5aa, 0 5px 16px #0007;
      cursor: pointer; transition: transform 0.35s, box-shadow 0.25s, filter 0.3s;
      filter: grayscale(0.2) brightness(0.95); border: 2px solid transparent;
    }
    .gallery img:hover, .gallery img:focus {
      transform: scale(1.13) rotate(-2deg); box-shadow: 0 0 30px #5b86e5ff, 0 0 10px #fff4;
      filter: grayscale(0) brightness(1.1); border-color: #5b86e5; outline: none; z-index: 3;
    }
    .modal-img { display: none; position: fixed; z-index: 1200; left: 0; top: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.9); justify-content: center; align-items: center; animation: fadeIn 0.2s;}
    .modal-img.active { display: flex; }
    .modal-img img { max-width: 90vw; max-height: 80vh; border-radius: 18px; box-shadow: 0 0 50px #5b86e5cc; border: 4px solid #5b86e5; animation: imgpop 0.3s;}
    @keyframes imgpop { from { transform: scale(0.6);} to { transform: scale(1);} }
    .modal-img .close-modal {
      position: absolute; top: 35px; right: 55px; font-size: 2.5rem; color: #dee0fc;
      background: transparent; border: none; cursor: pointer; z-index: 1300; transition: color 0.2s;
    }
    .modal-img .close-modal:hover { color: #fff; }
    ul.faq-list { list-style: none; padding: 0;}
    .faq-item { margin-bottom: 1.7em;}
    .faq-q { font-weight: 700; font-size: 1.08em; color: #5b86e5; margin-bottom: 0.2em;}
    .faq-a { font-size: 1.01em; color: #fff; }
    footer {
      text-align: center; font-size: 0.95rem; color: #888; padding: 1.5rem 0; border-top: 1px solid #333;
      margin-top: auto; background: linear-gradient(90deg, #232526, #414345); letter-spacing: 1px; z-index: 2;
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .gallery img { width: 48%; }
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.5rem;}
    }
    @media (max-width: 480px) {
      .gallery img { width: 100%; }
    }
  </style>
</head>
<body>
  <div id="particles-js"></div>
  <nav>
    <div class="nav-logo">
      Dysmorphia
    </div>
    <ul>
      <li><a href="#intro">Home</a></li>
      <li><a href="#what">What is it?</a></li>
      <li><a href="#causes">Causes</a></li>
      <li><a href="#effects">Effects</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#tips">Tips</a></li>
      <li><a href="#faq">FAQ</a></li>
      <li><a href="#creators">Creators</a></li>
    </ul>
  </nav>
  <header id="intro">
    <h1>Dysmorphia</h1>
    <p class="subtitle">Understanding Body Image and Its Impact</p>
  </header>
  <main>
    <section class="sr card" id="what">
      <h2>What is Dysmorphia?</h2>
      <p>
        <strong>Body dysmorphia</strong> is a mental health condition where a person spends a lot of time worrying about perceived flaws in their appearance. These flaws are often unnoticeable to others. Dysmorphia can affect anyone, regardless of age or gender, and can strongly impact self-esteem and daily life.
      </p>
    </section>
    <section class="sr card" id="causes">
      <h2>Causes</h2>
      <p>
        The causes of dysmorphia are complex and can involve:
        <ul>
          <li><strong>Genetics:</strong> Family history of mental health issues.</li>
          <li><strong>Environment:</strong> Social media, bullying, peer pressure, and cultural standards.</li>
          <li><strong>Psychological Factors:</strong> Low self-esteem, anxiety, or perfectionism.</li>
        </ul>
      </p>
    </section>
    <section class="sr card" id="effects">
      <h2>Effects</h2>
      <p>
        Dysmorphia can cause:
        <ul>
          <li>Constantly checking mirrors or avoiding them.</li>
          <li>Comparing yourself to others.</li>
          <li>Feeling anxious, embarrassed, or depressed.</li>
          <li>Social withdrawal.</li>
          <li>Obsessive thoughts about body image.</li>
        </ul>
      </p>
    </section>
    <section class="sr" id="gallery">
      <h2>Gallery</h2>
      <div class="gallery" aria-label="Body Dysmorphia Visuals">
        <img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&w=600&q=80" alt="Person looking in mirror, unsure" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80" alt="Distorted reflection" loading="lazy" tabindex="0" />
        <img src="https://images.pexels.com/photos/1707828/pexels-photo-1707828.jpeg?auto=compress&w=600&q=80" alt="Hidden face, low self-esteem" loading="lazy" tabindex="0" />
      </div>
    </section>
    <section class="sr card" id="tips">
      <h2>Tips for Coping</h2>
      <ul>
        <li>Talk to someone you trust about your feelings.</li>
        <li>Limit time on social media.</li>
        <li>Practice self-compassion and positive self-talk.</li>
        <li>Remember that nobody is perfect.</li>
        <li>Seek professional help if needed.</li>
      </ul>
    </section>
    <section class="sr card" id="faq">
      <h2>Frequently Asked Questions</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">Is dysmorphia only about weight?</div>
          <div class="faq-a">No, it can be about any body part or appearance feature, such as skin, hair, or facial features.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Can boys and men have dysmorphia?</div>
          <div class="faq-a">Yes, people of all genders and ages can experience dysmorphia.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Is dysmorphia the same as low self-esteem?</div>
          <div class="faq-a">Not exactly. While they are related, dysmorphia involves obsessive thoughts about appearance that can interfere with daily life.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">How can I help a friend with dysmorphia?</div>
          <div class="faq-a">Be supportive, listen without judgment, and encourage them to seek help from a trusted adult or professional.</div>
        </li>
      </ul>
    </section>
    <section class="sr card" id="creators">
      <h2>Creators</h2>
      <p>
        This page was created by <strong>Lucas De Cesare, Bautista Acerbo, and Santiago Martinez</strong> as a school project to raise awareness about body dysmorphia.
      </p>
    </section>
  </main>
  <footer>
    <p>&copy; 2025 Dysmorphia Awareness - School Project</p>
    <p>
      <a href="#intro" style="color: #dee0fc;">↑ Back to top</a>
    </p>
  </footer>
  <div class="modal-img" id="modalImg" role="dialog" aria-modal="true" aria-label="Enlarged gallery image">
    <button class="close-modal" id="closeModalImg" aria-label="Close">&times;</button>
    <img src="" alt="Enlarged gallery" id="modalImgSrc" />
  </div>
  <script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
  <script>
    // Particle background: soft blue/violet
    particlesJS("particles-js", {
      "particles": {
        "number": { "value": 45, "density": { "enable": true, "value_area": 700 }},
        "color": { "value": ["#5b86e5", "#36d1c4", "#b06ab3"] },
        "shape": { "type": "circle" },
        "opacity": { "value": 0.33, "random": true },
        "size": { "value": 7, "random": true },
        "line_linked": { "enable": true, "distance": 130, "color": "#dee0fc", "opacity": 0.20, "width": 1.2 },
        "move": { "enable": true, "speed": 1.8, "direction": "none", "random": false, "straight": false, "out_mode": "out" }
      },
      "interactivity": {
        "detect_on": "canvas",
        "events": {
          "onhover": { "enable": true, "mode": "grab" },
          "onclick": { "enable": true, "mode": "push" },
          "resize": true
        },
        "modes": {
          "grab": { "distance": 160, "line_linked": { "opacity": 0.5 } },
          "push": { "particles_nb": 3 }
        }
      },
      "retina_detect": true
    });

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
