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
      background: linear-gradient(135deg, #21222c 10%, #1a1b23 90%);
      color: #f3f3f3;
      min-height: 100vh;
      margin: 0;
      display: flex;
      flex-direction: column;
      line-height: 1.7;
      overflow-x: hidden;
    }
    nav {
      position: fixed; top: 0; left: 0; right: 0; height: 56px;
      background: rgba(33,34,44,0.98); box-shadow: 0 3px 18px #22223388;
      z-index: 2002; display: flex; align-items: center; justify-content: space-between;
      padding: 0 2vw; font-size: 1.08em;
    }
    nav .nav-logo {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 1.34em; color: #a7b5f7; letter-spacing: 2px;
      text-shadow: 0 0 8px #c2cdfa33; display: flex; align-items: center;
    }
    nav ul { list-style: none; display: flex; gap: 2em; margin: 0; padding: 0;}
    nav ul li a {
      color: #a7b5f7; text-decoration: none; font-weight: 700; font-family: 'Quicksand', sans-serif;
      padding: 6px 12px; border-radius: 8px;
      transition: background 0.2s, color 0.2s;
    }
    nav ul li a:hover, nav ul li a:focus { background: #6b55b9; color: #fff; }
    nav ul li .sourcelink {
      display: block;
      color: #c2cdfa;
      font-size: 0.9em;
      margin-top: 2px;
      margin-left: 8px;
      text-decoration: underline;
      font-family: 'Quicksand', sans-serif;
    }
    nav ul li .sourcelink:hover { color: #efc2fa; }
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
      background: linear-gradient(120deg, #23233a 65%, #35355a 100%);
      border-radius: 26px 26px 54px 54px / 26px 26px 54px 54px;
      box-shadow: 0 6px 22px #39396a55, 0 2px 18px #23233add;
      opacity: 0.56;
      border: 2px solid #373851;
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
      background: linear-gradient(90deg, #fff5, #fff0 80%);
      border-radius: 6px;
      opacity: 0.53;
      transform: rotate(-18deg);
    }
    @keyframes mirrorFloat {
      0% { transform: translateY(0) scaleX(1) rotate(-8deg);}
      40% { filter: brightness(1.08) blur(1.1px);}
      50% { filter: brightness(1.13) blur(0.4px);}
      65% { filter: brightness(1.03) blur(0.2px);}
      100% { transform: translateY(16vh) scaleX(1.03) rotate(6deg);}
    }
    a { color: #a7b5f7; text-decoration: none; transition: color 0.3s; }
    a:hover, a:focus { color: #f2a4ec; text-decoration: underline; outline: none; }
    header, main, footer {
      position: relative; z-index: 2; max-width: 920px; width: 93%; margin: auto; padding: 1.6rem 0;
    }
    header { text-align: center; }
    h1 {
      font-family: 'Quicksand', sans-serif;
      font-weight: 700; font-size: 2.9rem; color: #a7b5f7; margin-bottom: 0.3rem;
      letter-spacing: 2px; text-shadow: 0 1px 18px #6b55b955, 0 0 6px #c2cdfa55;
      animation: text-glow 4s ease-in-out infinite alternate;
    }
    @keyframes text-glow {
      to { text-shadow: 0 0 35px #b993d6ff, 0 0 20px #f7cac9bb; }
    }
    .subtitle {
      font-family: 'Merriweather', serif;
      font-weight: 500; font-size: 1.22rem; color: #f2a4ec; margin-bottom: 3rem;
      text-shadow: 0 0 6px #f2a4ec44; letter-spacing: 1px; animation: fadeIn 2s 0.5s both;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(40px);} to { opacity: 1; transform: translateY(0);} }
    h2 {
      color: #a7b5f7; margin-bottom: 1rem; font-weight: 700; font-size: 1.7rem;
      letter-spacing: 1px; font-family: 'Quicksand', sans-serif;
      text-shadow: 0 0 6px #6b55b9aa;
    }
    section { margin-bottom: 2.7rem; }
    .sr { opacity: 0; transform: translateY(40px); transition: opacity 0.7s, transform 0.7s;}
    .sr.visible { opacity: 1; transform: translateY(0); }
    .card {
      background: rgba(33,34,44,0.95); border-radius: 21px; padding: 1.5rem 2rem;
      box-shadow: 0 1px 26px #6b55b933; margin-bottom: 1.7rem; transition: box-shadow 0.3s, transform 0.3s;
      border: 1.5px solid #23233a;
    }
    .card:hover { box-shadow: 0 4px 38px #6b55b955; transform: scale(1.02);}
    .gallery { display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; margin-bottom:2rem;}
    .gallery img {
      width: 31%; border-radius: 17px; box-shadow: 0 0 16px #6b55b955, 0 5px 16px #39396a33;
      cursor: pointer; transition: transform 0.35s, box-shadow 0.25s, filter 0.2s;
      filter: grayscale(0.07) brightness(0.97); border: 2px solid #39396a;
      background: #181826;
      object-fit: cover;
      aspect-ratio: 4/3;
    }
    .gallery img:hover, .gallery img:focus {
      transform: scale(1.12) rotate(-2deg); box-shadow: 0 0 30px #b993d6ff, 0 0 10px #fff5;
      filter: grayscale(0) brightness(1.12); border-color: #f2a4ec; outline: none; z-index: 3;
    }
    .modal-img { display: none; position: fixed; z-index: 1200; left: 0; top: 0; width: 100vw; height: 100vh; background: rgba(33,34,44,0.96); justify-content: center; align-items: center; animation: fadeIn 0.2s;}
    .modal-img.active { display: flex; }
    .modal-img img { max-width: 90vw; max-height: 80vh; border-radius: 22px; box-shadow: 0 0 50px #6b55b9cc; border: 4px solid #a7b5f7; animation: imgpop 0.3s;}
    @keyframes imgpop { from { transform: scale(0.68);} to { transform: scale(1);} }
    .modal-img .close-modal {
      position: absolute; top: 35px; right: 55px; font-size: 2.5rem; color: #a7b5f7;
      background: transparent; border: none; cursor: pointer; z-index: 1300; transition: color 0.2s;
    }
    .modal-img .close-modal:hover { color: #f2a4ec; }
    .fact-box {
      background: #23233a44;
      color: #f3f3f3;
      border: 1.5px solid #a7b5f7;
      border-radius: 13px;
      padding: 1em 1.3em;
      margin: 1.1em 0;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.09em;
      box-shadow: 0 2px 14px #6b55b922;
    }
    blockquote {
      background: #39396a22;
      border-left: 6px solid #f2a4ec;
      margin: 1.3em 0;
      padding: 1.1em 1.2em 1.1em 1.8em;
      font-style: italic;
      color: #a7b5f7;
      border-radius: 12px;
      box-shadow: 0 2px 18px #6b55b911;
    }
    .source-list {
      margin: 2.5em 0 1em 0;
      padding: 1em 1.8em;
      background: #23233a;
      border-radius: 14px;
      box-shadow: 0 0 12px #39396a33;
    }
    .source-list h3 {
      color: #f2a4ec;
      font-family: 'Quicksand', sans-serif;
      font-size: 1.09em;
      margin-bottom: 0.7em;
    }
    .source-list ul {
      list-style: disc inside;
      color: #a7b5f7;
      font-size: 1em;
      margin: 0;
      padding: 0;
    }
    .graph-section {
      margin-bottom: 2.7rem;
    }
    .graph-section h2 {
      font-size: 1.2em;
      color: #f2a4ec;
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
      background: linear-gradient(180deg, #f2a4ec 80%, #39396a 100%);
      border-radius: 13px 13px 0 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0 9px;
      text-align: center;
      box-shadow: 0 2px 14px #6b55b922;
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
      color: #f3f3f3;
    }
    .bar-value {
      font-size: 1.12em;
      font-weight: bold;
      color: #f2a4ec;
      margin-bottom: 4px;
    }
    footer {
      text-align: center; font-size: 0.97rem; color: #a7b5f7; padding: 1.5rem 0; border-top: 1.5px solid #39396a;
      margin-top: auto; background: linear-gradient(90deg, #1a1b23, #23233a); letter-spacing: 1px; z-index: 2;
    }
    @media (max-width: 900px) { header, main, footer { width: 98%; } }
    @media (max-width: 768px) {
      .gallery img { width: 48%; }
      h1 { font-size: 2.2rem;}
      h2 { font-size: 1.3rem;}
      .card { padding: 1.1rem 0.7rem;}
      .graph-container { flex-direction: column; align-items: center;}
    }
    @media (max-width: 480px) {
      .gallery img { width: 100%; }
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
        <a href="#mentalhealth">Mental Health in Adolescents</a>
        <a class="sourcelink" target="_blank" href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health">Source: WHO</a>
      </li>
      <li>
        <a href="#dysmorphia-teen">Dysmorphia in Adolescents</a>
        <a class="sourcelink" target="_blank" href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/">Source: NCBI</a>
      </li>
      <li>
        <a href="#causes">Causes</a>
        <a class="sourcelink" target="_blank" href="https://www.verywellmind.com/body-dysmorphic-disorder-in-children-and-teens-5201591">Source: Verywell Mind</a>
      </li>
      <li>
        <a href="#effects">Effects</a>
        <a class="sourcelink" target="_blank" href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/">Source: Mind</a>
      </li>
      <li>
        <a href="#combat">How to Combat Dysmorphia</a>
        <a class="sourcelink" target="_blank" href="https://www.verywellmind.com/how-to-cope-with-body-dysmorphic-disorder-5105171">Source: Verywell Mind</a>
      </li>
      <li>
        <a href="#campaign">Our Awareness Campaign</a>
      </li>
      <li>
        <a href="#gallery">Gallery</a>
        <a class="sourcelink" target="_blank" href="https://unsplash.com/s/photos/body-dysmorphia">Gallery Source: Unsplash</a>
      </li>
      <li>
        <a href="#faq">FAQ</a>
        <a class="sourcelink" target="_blank" href="https://iocdf.org/about-ocd/related-disorders/bdd/">Source: IOCDF</a>
      </li>
      <li>
        <a href="#creators">Creators</a>
      </li>
    </ul>
  </nav>
  <header id="intro">
    <h1>Dysmorphia</h1>
    <p class="subtitle">Mental Health & Body Image in Adolescents</p>
  </header>
  <main>
    <section class="sr card" id="mentalhealth">
      <h2>What Are Mental Health Issues in Adolescents?</h2>
      <p>
        <strong>Adolescent mental health issues</strong> are emotional, psychological, or behavioral problems that affect teenagers. These include anxiety, depression, eating disorders, self-harm, substance abuse, and more. 
        <br><br>
        During adolescence (ages 10-19), rapid physical, emotional, and social changes can increase vulnerability to mental health challenges. About <b>one in seven adolescents</b> worldwide experiences a mental disorder each year.
      </p>
      <blockquote>
        "Mental health is just as important as physical health. Early support can change lives."
      </blockquote>
      <div class="fact-box">
        <strong>Why is this important?</strong> Untreated mental health issues can lead to school problems, substance use, risky behaviors, and even suicide—the fourth leading cause of death in 15-19 year olds worldwide.
        <br>
        <a class="sourcelink" target="_blank" href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health">Source: WHO</a>
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Graph: Most Common Mental Health Issues in Teens</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:120px;background:#f2a4ec;"></div>
          <div class="bar-value">31%</div>
          <div class="bar-label">Anxiety</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:95px;background:#a7b5f7;"></div>
          <div class="bar-value">24%</div>
          <div class="bar-label">Depression</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:67px;background:#6b55b9;"></div>
          <div class="bar-value">17%</div>
          <div class="bar-label">Eating Disorders</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:56px;background:#39396a;"></div>
          <div class="bar-value">14%</div>
          <div class="bar-label">Self-harm</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:38px;background:#f2a4ec88;"></div>
          <div class="bar-value">10%</div>
          <div class="bar-label">Other</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#c2cdfa">*Percentages based on global adolescent mental health statistics.</div>
    </section>
    <section class="sr card" id="dysmorphia-teen">
      <h2>Dysmorphia in Adolescents</h2>
      <p>
        <strong>Body dysmorphia</strong> is a mental health condition where someone becomes obsessed with perceived flaws in their appearance. In adolescents, this is often triggered by puberty, social pressure, and media images. 
        <br><br>
        Teens with dysmorphia may spend hours worrying about their looks, avoid social situations, or seek cosmetic procedures. It can cause anxiety, depression, eating disorders, and isolation.
      </p>
      <div class="fact-box">
        <b>Fact:</b> About 2% of teens are affected by body dysmorphia, but many more feel pressured to look "perfect".
        <br>
        <a class="sourcelink" target="_blank" href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/">Source: NCBI</a>
      </div>
    </section>
    <section class="graph-section sr">
      <h2>Graph: Percentage of Teens Affected by Body Dysmorphia</h2>
      <div class="graph-container">
        <div class="bar-graph">
          <div class="bar" style="height:26px;background:#a7b5f7;"></div>
          <div class="bar-value">2%</div>
          <div class="bar-label">Diagnosed</div>
        </div>
        <div class="bar-graph">
          <div class="bar" style="height:80px;background:#f2a4ec;"></div>
          <div class="bar-value">>50%</div>
          <div class="bar-label">Body Image Concerns</div>
        </div>
      </div>
      <div style="font-size:0.95em;color:#c2cdfa">*Many teens experience body image concerns even if not diagnosed with dysmorphia.</div>
    </section>
    <section class="sr card" id="causes">
      <h2>Causes of Dysmorphia in Adolescents</h2>
      <ul>
        <li><strong>Puberty:</strong> Rapid body changes and new feelings about appearance</li>
        <li><strong>Social Media:</strong> Filters, "likes", and comparison to influencers</li>
        <li><strong>Bullying:</strong> Teasing about looks at school or online</li>
        <li><strong>Family & Culture:</strong> Pressure to fit in, family focus on appearance</li>
        <li><strong>Mental Health:</strong> Anxiety, depression, or OCD increases risk</li>
      </ul>
      <a class="sourcelink" target="_blank" href="https://www.verywellmind.com/body-dysmorphic-disorder-in-children-and-teens-5201591">Source: Verywell Mind</a>
    </section>
    <section class="sr card" id="effects">
      <h2>Effects of Body Dysmorphia in Teens</h2>
      <ul>
        <li>Low self-esteem and lack of confidence</li>
        <li>Obsessive mirror checking or avoiding mirrors</li>
        <li>Isolation and withdrawal from friends or activities</li>
        <li>Eating disorders, depression, or self-harm</li>
        <li>Poor school performance, skipping classes</li>
      </ul>
      <blockquote>
        "A mirror can become a source of pain instead of reflection."
      </blockquote>
      <a class="sourcelink" target="_blank" href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/">Source: Mind</a>
    </section>
    <section class="sr card" id="combat">
      <h2>How to Combat Dysmorphia</h2>
      <ul>
        <li>Talk to someone you trust about your feelings.</li>
        <li>Limit time on social media and unfollow negative accounts.</li>
        <li>Focus on what your body <b>can do</b>, not just how it looks.</li>
        <li>Practice kindness to yourself—write down things you like about yourself.</li>
        <li>Seek support from a school counselor, psychologist, or helpline.</li>
        <li>Remember: Most online images are edited or filtered.</li>
      </ul>
      <div class="fact-box">
        <b>Asking for help is a sign of strength, not weakness.</b>
        <br>
        <a class="sourcelink" target="_blank" href="https://www.verywellmind.com/how-to-cope-with-body-dysmorphic-disorder-5105171">Source: Verywell Mind</a>
      </div>
    </section>
    <section class="sr card" id="campaign">
      <h2>Our Campaign: “See Yourself Clearly”</h2>
      <p>
        We believe that every teen deserves to feel comfortable in their own skin. Our campaign aims to:
      </p>
      <ul>
        <li><b>Raise Awareness:</b> Workshops and talks at schools about body image and mental health</li>
        <li><b>Promote Self-Acceptance:</b> Social media posts, posters, and videos with real stories</li>
        <li><b>Fight Stigma:</b> Open discussions and safe spaces for teens to share their feelings</li>
        <li><b>Support Each Other:</b> Peer support groups and resources for seeking help</li>
      </ul>
      <div class="fact-box">
        <b>Join us!</b> Share your story, support a friend, or spread the message: <span style="color:#f2a4ec"><b>#SeeYourselfClearly</b></span>
      </div>
    </section>
    <section class="sr" id="gallery">
      <h2>Gallery</h2>
      <div class="gallery" aria-label="Body Dysmorphia Visuals">
        <img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&w=600&q=80" alt="Teen looking at their reflection in a mirror with concern" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=600&q=80" alt="Distorted reflection in a cracked mirror" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1519125323398-675f0ddb6308?auto=format&fit=crop&w=600&q=80" alt="A hand over a foggy mirror, obscured face" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1464983953574-0892a716854b?auto=format&fit=crop&w=600&q=80" alt="Fragmented mirror and a face, representing broken self-image" loading="lazy" tabindex="0" />
        <img src="https://images.unsplash.com/photo-1488426862026-3ee34a7d66df?auto=format&fit=crop&w=600&q=80" alt="Teen sitting in front of a mirror, looking away" loading="lazy" tabindex="0" />
      </div>
      <a class="sourcelink" target="_blank" href="https://unsplash.com/s/photos/body-dysmorphia">Gallery Source: Unsplash</a>
    </section>
    <section class="sr card" id="faq">
      <h2>Frequently Asked Questions</h2>
      <ul class="faq-list">
        <li class="faq-item">
          <div class="faq-q">What are the most common mental health issues in teens?</div>
          <div class="faq-a">Anxiety, depression, eating disorders, self-harm, and body image concerns.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Can boys have body dysmorphia?</div>
          <div class="faq-a">Yes, dysmorphia affects all genders.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">Is social media really that bad?</div>
          <div class="faq-a">Social media can increase comparison and pressure, but positive accounts can help too.</div>
        </li>
        <li class="faq-item">
          <div class="faq-q">How can I help a friend with dysmorphia?</div>
          <div class="faq-a">Listen, support them without judgment, and encourage talking to a professional if needed.</div>
        </li>
      </ul>
      <a class="sourcelink" target="_blank" href="https://iocdf.org/about-ocd/related-disorders/bdd/">Source: IOCDF</a>
    </section>
    <section class="sr card" id="creators">
      <h2>Creators</h2>
      <p>
        This page was created by <strong>Lucas De Cesare, Bautista Acerbo, and Santiago Martinez</strong> as a school project to raise awareness about body dysmorphia and mental health in adolescents.
      </p>
      <div style="margin-top:1.3em;color:#f2a4ec;font-size:1.08em;">
        <i>“Our aim is to reflect the truth: that everyone deserves to feel valued, just as they are.”</i>
      </div>
    </section>
    <section class="source-list">
      <h3>Information Sources</h3>
      <ul>
        <li><a href="https://www.who.int/news-room/fact-sheets/detail/adolescent-mental-health" target="_blank">World Health Organization: Adolescent Mental Health</a></li>
        <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6520805/" target="_blank">NCBI: Body Dysmorphic Disorder in Teens</a></li>
        <li><a href="https://www.verywellmind.com/body-dysmorphic-disorder-in-children-and-teens-5201591" target="_blank">Verywell Mind: BDD in Children and Teens</a></li>
        <li><a href="https://www.mind.org.uk/information-support/types-of-mental-health-problems/body-dysmorphic-disorder-bdd/" target="_blank">Mind: Body Dysmorphic Disorder</a></li>
        <li><a href="https://www.verywellmind.com/how-to-cope-with-body-dysmorphic-disorder-5105171" target="_blank">Verywell Mind: Coping with BDD</a></li>
        <li><a href="https://iocdf.org/about-ocd/related-disorders/bdd/" target="_blank">IOCDF: About BDD</a></li>
        <li><a href="https://unsplash.com/s/photos/body-dysmorphia" target="_blank">Unsplash: Body Dysmorphia Photos</a></li>
      </ul>
    </section>
  </main>
  <footer>
    <p>&copy; 2025 Dysmorphia Awareness - School Project</p>
    <p>
      <a href="#intro" style="color: #f2a4ec;">↑ Back to top</a>
    </p>
  </footer>
  <div class="modal-img" id="modalImg" role="dialog" aria-modal="true" aria-label="Enlarged gallery image">
    <button class="close-modal" id="closeModalImg" aria-label="Close">&times;</button>
    <img src="" alt="Enlarged gallery" id="modalImgSrc" />
  </div>
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
