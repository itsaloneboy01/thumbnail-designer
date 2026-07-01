<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LetsLevelUp — Thumbnail Design</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@600;700&family=Inter:wght@400;500;600;700;800&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #0B0A17;
    --bg-alt: #14122B;
    --panel: #1A1830;
    --pink: #FF3D8E;
    --lime: #C6FF3D;
    --gold: #FFC93D;
    --text: #F5F3FF;
    --text-dim: #9C97BE;
    --line: rgba(245,243,255,0.09);
  }
  *{ margin:0; padding:0; box-sizing:border-box; }
  html{ scroll-behavior:smooth; }
  body{
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    overflow-x:hidden;
  }
  .display{ font-family:'Rajdhani', sans-serif; font-weight:700; text-transform:uppercase; letter-spacing:0.02em; }
  .mono{ font-family:'JetBrains Mono', monospace; }

  /* background texture */
  body::before{
    content:"";
    position:fixed; inset:0;
    background-image:
      radial-gradient(circle at 15% 20%, rgba(255,61,142,0.10), transparent 40%),
      radial-gradient(circle at 85% 75%, rgba(198,255,61,0.06), transparent 40%);
    pointer-events:none;
    z-index:0;
  }

  .wrap{ max-width:1100px; margin:0 auto; padding:0 28px; position:relative; z-index:1; }

  /* NAV */
  nav{
    position:sticky; top:0; z-index:50;
    background:rgba(11,10,23,0.85);
    backdrop-filter: blur(10px);
    border-bottom:1px solid var(--line);
  }
  nav .wrap{ display:flex; align-items:center; justify-content:space-between; height:72px; }
  .logo{ font-size:1.3rem; letter-spacing:0.02em; display:flex; align-items:center; gap:8px; }
  .logo .lv{ color:var(--lime); }
  nav ul{ list-style:none; display:flex; gap:32px; }
  nav a{ color:var(--text-dim); text-decoration:none; font-size:0.92rem; font-weight:600; transition:color .2s; }
  nav a:hover{ color:var(--pink); }
  .nav-cta{
    border:1.5px solid var(--lime); color:var(--lime) !important;
    padding:8px 18px; border-radius:2px;
  }
  .nav-cta:hover{ background:var(--lime); color:var(--bg) !important; }
  @media (max-width:720px){ nav ul{ display:none; } }

  /* HERO */
  .hero{ padding:110px 0 90px; position:relative; }
  .eyebrow{
    display:inline-flex; align-items:center; gap:10px;
    color:var(--lime); font-size:0.8rem; letter-spacing:0.14em; margin-bottom:22px;
  }
  .eyebrow::before{ content:"▮"; font-size:0.6rem; }
  .hero h1{
    font-size:clamp(3rem, 8vw, 6rem);
    line-height:0.94;
    margin-bottom:26px;
  }
  .hero h1 .accent{ color:var(--pink); }
  .hero p.lead{
    max-width:520px; color:var(--text-dim); font-size:1.15rem; line-height:1.6; margin-bottom:40px;
  }
  .btn-row{ display:flex; gap:16px; flex-wrap:wrap; }
  .btn{
    display:inline-block; padding:15px 30px; font-weight:700; text-decoration:none;
    border-radius:2px; font-size:0.95rem; transition:transform .15s ease, box-shadow .15s ease;
  }
  .btn-primary{ background:var(--pink); color:#fff; box-shadow:5px 5px 0 var(--gold); }
  .btn-primary:hover{ transform:translate(-2px,-2px); box-shadow:7px 7px 0 var(--gold); }
  .btn-ghost{ border:1.5px solid var(--line); color:var(--text); }
  .btn-ghost:hover{ border-color:var(--lime); color:var(--lime); }

  /* XP METER — signature element */
  .xp-section{ padding:40px 0 90px; border-top:1px solid var(--line); border-bottom:1px solid var(--line); }
  .xp-head{ display:flex; justify-content:space-between; align-items:baseline; margin-bottom:34px; flex-wrap:wrap; gap:10px;}
  .xp-head h2{ font-size:1.6rem; }
  .xp-head span{ color:var(--text-dim); font-size:0.85rem; }
  .xp-bar-track{
    position:relative; height:14px; background:var(--panel); border-radius:8px; overflow:hidden; margin-bottom:46px;
    border:1px solid var(--line);
  }
  .xp-bar-fill{
    position:absolute; left:0; top:0; bottom:0; width:0%;
    background:linear-gradient(90deg, var(--pink), var(--gold), var(--lime));
    border-radius:8px;
    transition:width 1.4s cubic-bezier(.2,.8,.2,1);
  }
  .stat-grid{ display:grid; grid-template-columns:repeat(4,1fr); gap:24px; }
  @media (max-width:800px){ .stat-grid{ grid-template-columns:repeat(2,1fr); } }
  .stat{
    background:var(--panel); border:1px solid var(--line); padding:24px 20px; border-radius:4px;
    position:relative;
  }
  .stat .num{ font-family:'Rajdhani', sans-serif; font-weight:700; font-size:2.6rem; color:var(--lime); line-height:1; }
  .stat .lbl{ color:var(--text-dim); font-size:0.82rem; margin-top:10px; }
  .stat .edit-tag{ position:absolute; top:10px; right:10px; font-size:0.6rem; color:var(--pink); opacity:0.7; }

  /* PORTFOLIO — Levels Unlocked */
  .portfolio{ padding:90px 0; }
  .section-head{ margin-bottom:50px; max-width:600px; }
  .section-head .tag{ color:var(--pink); font-size:0.8rem; letter-spacing:0.14em; margin-bottom:14px; display:block; }
  .section-head h2{ font-size:clamp(2rem,4vw,3rem); margin-bottom:14px; }
  .section-head p{ color:var(--text-dim); font-size:1rem; line-height:1.6; }

  .level-grid{ display:grid; grid-template-columns:repeat(3,1fr); gap:26px; }
  @media (max-width:900px){ .level-grid{ grid-template-columns:repeat(2,1fr); } }
  @media (max-width:560px){ .level-grid{ grid-template-columns:1fr; } }

  .level-card{
    background:var(--panel); border:1px solid var(--line); border-radius:6px; overflow:hidden;
    transition:transform .2s ease, border-color .2s ease;
  }
  .level-card:hover{ transform:translateY(-6px); border-color:var(--lime); }
  .thumb-box{
    aspect-ratio:16/9; width:100%;
    background:
      repeating-linear-gradient(45deg, rgba(255,255,255,0.03) 0 2px, transparent 2px 14px),
      linear-gradient(135deg, #221f42, #14122B);
    display:flex; align-items:center; justify-content:center;
    position:relative; border-bottom:1px solid var(--line);
  }
  .thumb-box .badge{
    position:absolute; top:10px; left:10px;
    background:var(--bg); border:1px solid var(--lime); color:var(--lime);
    font-family:'JetBrains Mono',monospace; font-size:0.7rem; padding:3px 8px; border-radius:3px;
  }
  .thumb-box .plus{ font-family:'Rajdhani', sans-serif; font-weight:700; font-size:2.4rem; color:var(--text-dim); opacity:0.35; }
  .level-info{ padding:18px 20px 22px; }
  .level-info .client{ font-weight:700; font-size:1rem; margin-bottom:4px; }
  .level-info .niche{ color:var(--text-dim); font-size:0.82rem; }

  /* ABOUT / EXPERIENCE */
  .about{ padding:90px 0; border-top:1px solid var(--line); }
  .about-grid{ display:grid; grid-template-columns:1fr 1fr; gap:60px; align-items:start; }
  @media (max-width:800px){ .about-grid{ grid-template-columns:1fr; } }
  .about h2{ font-size:clamp(2rem,4vw,3rem); margin-bottom:20px; }
  .about p{ color:var(--text-dim); line-height:1.75; margin-bottom:18px; font-size:1rem; }
  .about strong{ color:var(--text); }
  .quest-log{ display:flex; flex-direction:column; gap:0; }
  .quest{ padding:20px 0; border-bottom:1px solid var(--line); display:flex; gap:16px; }
  .quest:last-child{ border-bottom:none; }
  .quest .qnum{ font-family:'JetBrains Mono',monospace; color:var(--gold); font-size:0.85rem; padding-top:2px; }
  .quest .qtext strong{ display:block; margin-bottom:4px; }
  .quest .qtext span{ color:var(--text-dim); font-size:0.88rem; }

  /* CONTACT */
  .contact{ padding:100px 0 120px; text-align:center; border-top:1px solid var(--line); }
  .contact .tag{ color:var(--pink); font-size:0.8rem; letter-spacing:0.14em; margin-bottom:18px; display:block; }
  .contact h2{ font-size:clamp(2.2rem,6vw,4rem); margin-bottom:20px; }
  .contact h2 .accent{ color:var(--lime); }
  .contact p{ color:var(--text-dim); max-width:480px; margin:0 auto 44px; font-size:1.05rem; line-height:1.6; }
  .contact-links{ display:flex; justify-content:center; gap:20px; flex-wrap:wrap; }
  .clink{
    display:flex; flex-direction:column; align-items:flex-start; gap:6px;
    background:var(--panel); border:1px solid var(--line); padding:20px 26px; border-radius:6px;
    text-decoration:none; color:var(--text); min-width:230px; text-align:left;
    transition:border-color .2s ease, transform .2s ease;
  }
  .clink:hover{ border-color:var(--pink); transform:translateY(-4px); }
  .clink .k{ color:var(--text-dim); font-size:0.72rem; letter-spacing:0.1em; text-transform:uppercase; }
  .clink .v{ font-weight:700; font-size:1.02rem; }
  .clink .v.edit{ color:var(--pink); }

  footer{ padding:30px 0; text-align:center; color:var(--text-dim); font-size:0.8rem; border-top:1px solid var(--line); }
  footer .lv{ color:var(--lime); }

  .reveal{ opacity:0; transform:translateY(24px); transition:opacity .7s ease, transform .7s ease; }
  .reveal.in{ opacity:1; transform:translateY(0); }
</style>
</head>
<body>

<nav>
  <div class="wrap">
    <div class="logo display">LETS<span class="lv">LEVEL</span>UP</div>
    <ul>
      <li><a href="#work">Work</a></li>
      <li><a href="#about">Experience</a></li>
      <li><a href="#contact" class="nav-cta">Contact</a></li>
    </ul>
  </div>
</nav>

<header class="hero">
  <div class="wrap">
    <div class="eyebrow mono">THUMBNAIL DESIGN · FOR CREATORS WHO WANT MORE CLICKS</div>
    <h1 class="display">Every thumbnail<br>is a <span class="accent">boss fight.</span><br>I design to win.</h1>
    <p class="lead">Custom YouTube thumbnails built for gaming, IRL, and challenge channels — made by someone who actually grinds the algorithm, not just the design tools.</p>
    <div class="btn-row">
      <a href="#work" class="btn btn-primary">See the Work</a>
      <a href="#contact" class="btn btn-ghost">Get a Thumbnail Made</a>
    </div>
  </div>
</header>

<section class="xp-section reveal">
  <div class="wrap">
    <div class="xp-head">
      <h2 class="display">XP Bar</h2>
      <span class="mono">EDIT: swap in your real numbers</span>
    </div>
    <div class="xp-bar-track">
      <div class="xp-bar-fill" id="xpFill"></div>
    </div>
    <div class="stat-grid">
      <div class="stat">
        <div class="edit-tag mono">EDIT</div>
        <div class="num">00</div>
        <div class="lbl">Thumbnails designed</div>
      </div>
      <div class="stat">
        <div class="edit-tag mono">EDIT</div>
        <div class="num">00</div>
        <div class="lbl">Creators worked with</div>
      </div>
      <div class="stat">
        <div class="edit-tag mono">EDIT</div>
        <div class="num">00%</div>
        <div class="lbl">Avg. CTR improvement</div>
      </div>
      <div class="stat">
        <div class="edit-tag mono">EDIT</div>
        <div class="num">24h</div>
        <div class="lbl">Typical turnaround</div>
      </div>
    </div>
  </div>
</section>

<section class="portfolio" id="work">
  <div class="wrap">
    <div class="section-head reveal">
      <span class="tag mono">LEVELS UNLOCKED</span>
      <h2 class="display">Portfolio</h2>
      <p>Drop your thumbnail images into these boxes and swap the labels with the real channel name, niche, and what the thumbnail was built to do.</p>
    </div>
    <div class="level-grid">

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 01</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Gaming / IRL / Challenge] · Designed to boost CTR on a [video type]</div>
        </div>
      </div>

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 02</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Niche] · [What made this thumbnail work]</div>
        </div>
      </div>

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 03</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Niche] · [Result, e.g. "2x CTR vs old thumbnail"]</div>
        </div>
      </div>

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 04</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Niche] · [Notes]</div>
        </div>
      </div>

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 05</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Niche] · [Notes]</div>
        </div>
      </div>

      <div class="level-card reveal">
        <div class="thumb-box"><span class="badge">LVL 06</span><span class="plus">+ IMAGE</span></div>
        <div class="level-info">
          <div class="client">For: [Channel Name]</div>
          <div class="niche">[Niche] · [Notes]</div>
        </div>
      </div>

    </div>
  </div>
</section>

<section class="about" id="about">
  <div class="wrap about-grid">
    <div class="reveal">
      <h2 class="display">The Player Behind<br>the Thumbnails</h2>
      <p><strong>[Your name]</strong> here — I run a gaming YouTube channel myself, so I'm not designing thumbnails from the outside. I know what makes someone stop scrolling and tap, because I test it on my own videos first.</p>
      <p>I design for <strong>gaming, IRL challenge, and mobile gaming creators</strong>, mostly for the Indian audience — bold expressions, high contrast, clean text hierarchy, and a hook that reads in under a second.</p>
      <p>[Add 2-3 more lines here about your style, tools you use (Photoshop / Canva / Photopea), and what kind of creators you love working with.]</p>
    </div>
    <div class="quest-log reveal">
      <div class="quest">
        <div class="qnum mono">01</div>
        <div class="qtext"><strong>Fast turnaround</strong><span>[Edit: describe your typical delivery time and revision process.]</span></div>
      </div>
      <div class="quest">
        <div class="qnum mono">02</div>
        <div class="qtext"><strong>Built for retention</strong><span>[Edit: how you think about thumbnail + title pairing.]</span></div>
      </div>
      <div class="quest">
        <div class="qnum mono">03</div>
        <div class="qtext"><strong>Creator-to-creator</strong><span>[Edit: your own channel experience and what it teaches you about design.]</span></div>
      </div>
      <div class="quest">
        <div class="qnum mono">04</div>
        <div class="qtext"><strong>Simple pricing</strong><span>[Edit: add your packages or starting price here.]</span></div>
      </div>
    </div>
  </div>
</section>

<section class="contact" id="contact">
  <div class="wrap">
    <span class="tag mono">READY PLAYER ONE?</span>
    <h2 class="display">Let's <span class="accent">Level Up</span><br>Your Next Upload.</h2>
    <p>Send over your channel, your niche, and what the video's about — I'll get back with ideas fast.</p>
    <div class="contact-links">
      <a href="mailto:youremail@example.com" class="clink">
        <span class="k mono">Email</span>
        <span class="v edit">youremail@example.com</span>
      </a>
      <a href="https://instagram.com/yourhandle" class="clink" target="_blank">
        <span class="k mono">Instagram</span>
        <span class="v edit">@yourhandle</span>
      </a>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">© <span id="year"></span> <span class="lv">LetsLevelUp</span> — thumbnails that get the click.</div>
</footer>

<script>
  document.getElementById('year').textContent = new Date().getFullYear();

  // scroll reveal
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } });
  }, { threshold: 0.15 });
  revealEls.forEach(el => io.observe(el));

  // XP bar fill on scroll into view
  const xpFill = document.getElementById('xpFill');
  const xpIo = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        xpFill.style.width = '72%'; // EDIT: set this to reflect your actual "progress" / experience level
        xpIo.unobserve(e.target);
      }
    });
  }, { threshold: 0.4 });
  xpIo.observe(document.querySelector('.xp-bar-track'));
</script>

</body>
</html>
