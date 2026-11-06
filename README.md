<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Alislamiah For Developers</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #05070d;
      --surface: #0b1019;
      --card: #0f1623;
      --card-hover: #151e2e;
      --border: rgba(255,255,255,0.07);
      --border-light: rgba(255,255,255,0.12);
      --text: #f0f4fa;
      --muted: #8b9cb3;
      --dim: #5c6d85;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Tajawal', system-ui, sans-serif;
      background-color: #070e1f;
      background-image: url('cube-bg.jpg');
      /* مصغرة وتظهر كلياً - ليست مكبرة */
      background-position: right bottom;
      background-size: 75% auto;
      background-repeat: no-repeat;
      background-attachment: fixed;
      color: var(--text);
      line-height: 1.6;
      overflow-x: hidden;
      min-height: 100vh;
    }

    /* تابلت: أصغر قليلاً */
    @media (max-width: 1024px) {
      body {
        background-size: 90% auto;
        background-position: center bottom;
      }
    }

    /* موبايل: تظهر كاملة مصغرة */
    @media (max-width: 768px) {
      body {
        background-size: 100% auto;
        background-position: center bottom;
      }
    }

    }

    /* طبقة خفيفة جداً - مثل الصورة تماماً */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background: 
        linear-gradient(180deg, rgba(7,14,31,0.15) 0%, rgba(7,14,31,0.05) 100%);
      z-index: 0;
      pointer-events: none;
    }
    /* فواصل شفافة تظهر المكعب */
    .cube-spacer {
      height: 18vh;
      min-height: 120px;
      position: relative;
      z-index: 1;
      pointer-events: none;
    }
    .cube-spacer.small {
      height: 10vh;
      min-height: 70px;
    }

    /* HERO */
    .hero {
      position: relative;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 6rem 0 4rem;
      overflow: hidden;
      z-index: 1;
    }

    .hero-bg {
      display: none;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      width: min(1100px, 92%);
      margin: 0 auto;
    }



    .nav {
      position: absolute;
      top: 0; left: 0; right: 0;
      z-index: 20;
      padding: 1.25rem 0;
    }

    .nav-inner {
      width: min(1100px, 92%);
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      text-decoration: none;
      color: var(--text);
      font-weight: 800;
      font-size: 1.2rem;
    }

    .logo img {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      object-fit: cover;
      border: 2px solid rgba(255,255,255,0.15);
    }

    .nav-links {
      display: flex;
      gap: 0.5rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-weight: 500;
      font-size: 0.95rem;
      padding: 0.45rem 1rem;
      border-radius: 8px;
      transition: 0.2s;
    }

    .nav-links a:hover { color: #fff; background: rgba(255,255,255,0.06); }

    .nav-cta {
      background: linear-gradient(135deg, #3b82f6, #8b5cf6) !important;
      color: #fff !important;
      font-weight: 700 !important;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(59,130,246,0.15);
      border: 1px solid rgba(59,130,246,0.3);
      color: #93c5fd;
      font-size: 0.85rem;
      font-weight: 600;
      padding: 0.4rem 1rem;
      border-radius: 100px;
      margin-bottom: 1.5rem;
    }

    .hero h1 {
      font-size: clamp(2.6rem, 6vw, 4rem);
      font-weight: 900;
      line-height: 1.15;
      letter-spacing: -0.03em;
      margin-bottom: 1rem;
    }

    .hero h1 span {
      background: linear-gradient(90deg, #60a5fa, #22d3ee, #a78bfa);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .hero-desc {
      font-size: 1.15rem;
      color: var(--muted);
      max-width: 540px;
      margin-bottom: 2.25rem;
    }

    .hero-btns {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 3.5rem;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      padding: 0.95rem 1.8rem;
      border-radius: 12px;
      font-weight: 700;
      font-size: 1rem;
      text-decoration: none;
      transition: 0.25s;
      border: none;
      cursor: pointer;
      font-family: inherit;
    }

    .btn-primary {
      background: linear-gradient(135deg, #3b82f6, #6366f1);
      color: #fff;
      box-shadow: 0 8px 30px rgba(59,130,246,0.35);
    }

    .btn-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 40px rgba(59,130,246,0.45);
    }

    .btn-outline {
      background: rgba(255,255,255,0.05);
      color: #fff;
      border: 1px solid rgba(255,255,255,0.15);
    }

    .btn-outline:hover {
      background: rgba(255,255,255,0.1);
      border-color: rgba(255,255,255,0.25);
    }

    .hani-box {
      background: rgba(15,22,35,0.45);
      backdrop-filter: blur(20px) saturate(130%);
      -webkit-backdrop-filter: blur(20px) saturate(130%);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 20px;
      padding: 2rem 2.25rem;
      display: flex;
      align-items: center;
      gap: 1.8rem;
      max-width: 700px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.3), inset 0 1px 0 rgba(255,255,255,0.06);
    }

    .hani-icon {
      width: 68px;
      height: 68px;
      flex-shrink: 0;
    }

    .hani-icon img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      filter: drop-shadow(0 0 20px rgba(251,191,36,0.4));
    }

    .hani-text h3 {
      font-size: 1.35rem;
      font-weight: 800;
      margin-bottom: 0.3rem;
    }

    .hani-text p {
      color: var(--muted);
      font-size: 0.95rem;
      margin-bottom: 1rem;
    }

    .hani-text .btn {
      padding: 0.65rem 1.3rem;
      font-size: 0.9rem;
    }

    /* SECTIONS - شفافة أكثر مع فراغات كبيرة */
    section {
      padding: 7.5rem 0;
      position: relative;
      z-index: 1;
      margin: 2.5rem 0;
      border-radius: 32px;
    }

    #about, #tools, .cta {
      background: rgba(5, 7, 13, 0.22);
      backdrop-filter: blur(24px) saturate(130%);
      -webkit-backdrop-filter: blur(24px) saturate(130%);
      border-top: 1px solid rgba(255,255,255,0.06);
      border-bottom: 1px solid rgba(255,255,255,0.04);
      box-shadow: 
        inset 0 1px 0 rgba(255,255,255,0.05),
        0 20px 80px rgba(0,0,0,0.2);
    }
    /* فراغات أكبر بين العناصر */
    .container {
      width: min(1100px, 92%);
      margin: 0 auto;
    }

    .section-title {
      text-align: center;
      margin-bottom: 4.5rem;
    }

    .section-title h2 {
      font-size: clamp(1.8rem, 3.5vw, 2.3rem);
      font-weight: 800;
      margin-bottom: 0.6rem;
    }

    .section-title p {
      color: var(--muted);
      font-size: 1.05rem;
    }

    .about-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2.2rem;
    }

    .about-card {
      background: rgba(15, 22, 35, 0.42);
      backdrop-filter: blur(18px) saturate(130%);
      -webkit-backdrop-filter: blur(18px) saturate(130%);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 20px;
      padding: 2rem;
      transition: 0.35s cubic-bezier(.2,.8,.2,1);
      box-shadow: 0 8px 32px rgba(0,0,0,0.25), inset 0 1px 0 rgba(255,255,255,0.06);
    }

    .about-card:hover {
      border-color: rgba(255,255,255,0.16);
      background: rgba(21, 30, 46, 0.55);
      transform: translateY(-6px);
      box-shadow: 0 16px 48px rgba(0,0,0,0.35);
    }

    .about-card img {
      width: 48px;
      height: 48px;
      margin-bottom: 1.1rem;
      object-fit: contain;
    }

    .about-card h3 {
      font-size: 1.15rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
    }

    .about-card p {
      color: var(--muted);
      font-size: 0.92rem;
    }

    .tools-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 2rem;
    }

    .tool {
      background: rgba(15, 22, 35, 0.42);
      backdrop-filter: blur(18px) saturate(130%);
      -webkit-backdrop-filter: blur(18px) saturate(130%);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 20px;
      padding: 2rem;
      text-decoration: none;
      color: inherit;
      display: flex;
      flex-direction: column;
      gap: 1.2rem;
      transition: 0.35s cubic-bezier(.2,.8,.2,1);
      position: relative;
      overflow: hidden;
      box-shadow: 0 8px 32px rgba(0,0,0,0.2), inset 0 1px 0 rgba(255,255,255,0.05);
    }

    .tool:hover {
      border-color: rgba(59,130,246,0.35);
      background: rgba(21, 30, 46, 0.58);
      transform: translateY(-6px);
      box-shadow: 0 24px 56px rgba(0,0,0,0.4);
    }

    .tool::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, #3b82f6, #22d3ee, #8b5cf6);
      opacity: 0;
      transition: 0.25s;
    }

    .tool:hover::before { opacity: 1; }

    .tool-top {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .tool-icon {
      width: 56px;
      height: 56px;
      border-radius: 14px;
      background: rgba(255,255,255,0.04);
      border: 1px solid var(--border);
      display: grid;
      place-items: center;
      flex-shrink: 0;
      overflow: hidden;
    }

    .tool-icon img {
      width: 36px;
      height: 36px;
      object-fit: contain;
    }

    .tool-name {
      font-size: 1.15rem;
      font-weight: 700;
    }

    .tool-tag {
      font-size: 0.78rem;
      color: var(--dim);
      font-weight: 500;
    }

    .tool-desc {
      color: var(--muted);
      font-size: 0.9rem;
      flex-grow: 1;
    }

    .tool-action {
      font-size: 0.88rem;
      font-weight: 700;
      color: #60a5fa;
    }

    .tool:hover .tool-action { color: #93c5fd; }

    .tool.featured {
      grid-column: 1 / -1;
      flex-direction: row;
      align-items: center;
      padding: 2.4rem;
      gap: 2.4rem;
      background: linear-gradient(135deg, rgba(59,130,246,0.14), rgba(139,92,246,0.10));
      backdrop-filter: blur(20px) saturate(130%);
      -webkit-backdrop-filter: blur(20px) saturate(130%);
      border-color: rgba(99,102,241,0.25);
    }

    .tool.featured .tool-icon {
      width: 80px;
      height: 80px;
      border-radius: 20px;
      background: linear-gradient(135deg, rgba(59,130,246,0.2), rgba(139,92,246,0.2));
    }

    .tool.featured .tool-icon img {
      width: 52px;
      height: 52px;
    }

    .tool.featured .tool-desc { max-width: 520px; }

    .cta { padding: 5rem 0 6rem; margin-bottom: 2rem; }

    .cta-box {
      background: rgba(15, 22, 35, 0.42);
      backdrop-filter: blur(20px) saturate(130%);
      -webkit-backdrop-filter: blur(20px) saturate(130%);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 28px;
      padding: 4rem 2.5rem;
      text-align: center;
      position: relative;
      overflow: hidden;
      box-shadow: 0 16px 64px rgba(0,0,0,0.25);
    }

    .cta-box::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(59,130,246,0.1), rgba(139,92,246,0.08));
    }

    .cta-box > * { position: relative; z-index: 1; }

    .cta-box h2 {
      font-size: 2rem;
      font-weight: 800;
      margin-bottom: 0.7rem;
    }

    .cta-box p {
      color: var(--muted);
      margin-bottom: 1.75rem;
      max-width: 420px;
      margin-inline: auto;
    }

    footer {
      border-top: 1px solid rgba(255,255,255,0.06);
      padding: 3.5rem 0;
      text-align: center;
      position: relative;
      z-index: 1;
      background: rgba(5, 7, 13, 0.25);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      margin-top: 4rem;
    }

    .footer-logo {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.6rem;
      font-weight: 800;
      margin-bottom: 0.75rem;
    }

    .footer-logo img {
      width: 32px;
      height: 32px;
      border-radius: 50%;
    }

    .footer-text {
      color: var(--dim);
      font-size: 0.9rem;
    }

    @media (max-width: 900px) {
      .about-grid, .tools-grid { grid-template-columns: 1fr 1fr; }
      .tool.featured { flex-direction: column; text-align: center; }
    }

    @media (max-width: 600px) {
      .about-grid, .tools-grid { grid-template-columns: 1fr; }
      .nav-links { display: none; }
      .hani-box { flex-direction: column; text-align: center; }
      .hero { min-height: auto; padding-top: 7rem; }
    }
  </style>
</head>
<body>

  <nav class="nav">
    <div class="nav-inner">
      <a href="#" class="logo">
        <img src="Alislamiah-for-Devloppers.png" alt="Alislamiah">
        Alislamiah
      </a>
      <ul class="nav-links">
        <li><a href="#about">عن الشبكة</a></li>
        <li><a href="#tools">الأدوات</a></li>
        <li><a href="https://Alislamiah.github.io/Hani-AI/" class="nav-cta">Hani AI</a></li>
      </ul>
    </div>
  </nav>

  <header class="hero">
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">✦ شبكة Alislamiah الرقمية</div>
      <h1>Alislamiah <span>For Developers</span></h1>
      <p class="hero-desc">
        شبكة رقمية توفر خدمات متعددة تساعد المطورين وترفه عن المستخدمين. 
        أدوات قوية وذكاء اصطناعي في مكان واحد.
      </p>
      <div class="hero-btns">
        <a href="https://Alislamiah.github.io/Hani-AI/" class="btn btn-primary">جرب Hani AI</a>
        <a href="#tools" class="btn btn-outline">استكشف الأدوات</a>
      </div>

      <div class="hani-box">
        <div class="hani-icon">
          <img src="Hani-AI.png" alt="Hani AI">
        </div>
        <div class="hani-text">
          <h3>نقدم لك Hani AI</h3>
          <p>مساعدك الذكي داخل شبكة الإسلامية — جربه الآن واكتشف القوة الحقيقية.</p>
          <a href="https://l2z.netlify.app" class="btn btn-primary">انتقل إلى Hani AI</a>
        </div>
      </div>
    </div>
  </header>

  <div class="cube-spacer"></div>

  <section id="about">
    <div class="container">
      <div class="section-title">
        <h2>شبكة Alislamiah</h2>
        <p>شبكة الإسلامية هي شبكة رقمية توفر خدمات متعددة تساعد المطورين وترفه عن المستخدمين</p>
      </div>
      <div class="about-grid">
        <div class="about-card">
          <img src="Outhub.png" alt="">
          <h3>أدوات المطورين</h3>
          <p>مجموعة متكاملة من المنصات المصممة خصيصاً لمساعدة المطورين في بناء مشاريعهم بسرعة وكفاءة.</p>
        </div>
        <div class="about-card">
          <img src="Hani-AI.png" alt="">
          <h3>ذكاء اصطناعي</h3>
          <p>Hani AI و Gemalot — مساعدان ذكيان يدمجان قوة الذكاء الاصطناعي مع احتياجات المستخدم والمطور.</p>
        </div>
        <div class="about-card">
          <img src="Alislamiah-search-console.png" alt="">
          <h3>منصات متعددة</h3>
          <p>منصات متنوعة ومترابطة تخدم المطورين والمستخدمين في بيئة واحدة منظمة وسهلة الاستخدام.</p>
        </div>
      </div>
    </div>
  </section>

  <div class="cube-spacer small"></div>

  <section id="tools">
    <div class="container">
      <div class="section-title">
        <h2>أدوات المطورين</h2>
        <p>كل الأدوات والمنصات في مكان واحد</p>
      </div>

      <div class="tools-grid">

        <a href="https://Alislamiah.github.io/Hani-AI/" class="tool featured">
          <div class="tool-icon">
            <img src="Hani-AI.png" alt="Hani AI">
          </div>
          <div>
            <div class="tool-name">Hani AI</div>
            <div class="tool-tag">الذكاء الاصطناعي · المنصة الرئيسية</div>
            <p class="tool-desc">نقدم لك Hani AI — جرب المنصة الآن واستمتع بتجربة ذكية متكاملة ضمن شبكة الإسلامية.</p>
            <div class="tool-action">جرب المنصة ←</div>
          </div>
        </a>

        <a href="https://alislamiah.github.io/outhub/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Outhub.png" alt="Outhub">
            </div>
            <div>
              <div class="tool-name">Outhub</div>
              <div class="tool-tag">منصة تطوير</div>
            </div>
          </div>
          <p class="tool-desc">طور مواقعك وتطبيقاتك بواسطة الإسلامية — بيئة متكاملة للمطورين.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

        <a href="https://alislamiah.github.io/Outbase/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Outbase.png" alt="Outbase">
            </div>
            <div>
              <div class="tool-name">Outbase</div>
              <div class="tool-tag">قواعد البيانات</div>
            </div>
          </div>
          <p class="tool-desc">أداة قوية لإدارة والتعامل مع قواعد البيانات ضمن منظومة Alislamiah.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

        <a href="https://alislamiah.github.io/Alislamiah-API-studio/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Alislamiah-API-studio.png" alt="API Studio">
            </div>
            <div>
              <div class="tool-name">API Studio</div>
              <div class="tool-tag">واجهات برمجة</div>
            </div>
          </div>
          <p class="tool-desc">استوديو متكامل لبناء واختبار وإدارة واجهات الـ API بسهولة واحترافية.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

        <a href="https://alislamiah.github.io/Alislamiah-search-console/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Alislamiah-search-console.png" alt="Search Console">
            </div>
            <div>
              <div class="tool-name">Search Console</div>
              <div class="tool-tag">فهرسة المواقع</div>
            </div>
          </div>
          <p class="tool-desc">اطلب فهرسة مواقعك لتظهر في نتائج البحث داخل شبكة الإسلامية.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

        <a href="https://nazim10-u.github.io/nazim/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Midad.png" alt="مداد">
            </div>
            <div>
              <div class="tool-name">مداد</div>
              <div class="tool-tag">كتابة وتدوين</div>
            </div>
          </div>
          <p class="tool-desc">منصة مداد للكتابة والتدوين — أداة أنيقة ومنظمة للمحتوى.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

        <a href="https://alislamiah.github.io/Gemalot/" class="tool">
          <div class="tool-top">
            <div class="tool-icon">
              <img src="Gemalot.png" alt="Gemalot">
            </div>
            <div>
              <div class="tool-name">Gemalot</div>
              <div class="tool-tag">مساعد ذكي</div>
            </div>
          </div>
          <p class="tool-desc">مساعد الإسلامية الرقمي — Alislamiah AI Assistant للإجابة والمساعدة.</p>
          <div class="tool-action">فتح الأداة ←</div>
        </a>

      </div>
    </div>
  </section>

  <div class="cube-spacer"></div>

  <section class="cta">
    <div class="container">
      <div class="cta-box">
        <h2>جاهز لتجربة Hani AI؟</h2>
        <p>انتقل مباشرة إلى المنصة واستكشف قدرات الذكاء الاصطناعي ضمن شبكة الإسلامية.</p>
        <a href="https://Alislamiah.github.io/Hani-AI/" class="btn btn-primary">جرب Hani AI الآن</a>
      </div>
    </div>
  </section>

  <footer>
    <div class="container">
      <div class="footer-logo">
        <img src="Alislamiah-for-Devloppers.png" alt="">
        Alislamiah For Developers
      </div>
      <p class="footer-text">
        شبكة الإسلامية — أدوات تساعد المطورين وترفه عن المستخدمين<br>
        © 2026 Alislamiah
      </p>
    </div>
  </footer>

</body>
</html>
