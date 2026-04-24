<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TopIA — Créez votre IA personnalisée sans code</title>
  <meta name="description" content="Créez un assistant IA spécialisé en quelques minutes. Trading, cuisine, droit, sport... Sans compétence technique. Intégrable sur votre site.">
  <meta property="og:title" content="TopIA — Votre IA sur mesure">
  <meta property="og:description" content="Configurez votre assistant IA personnalisé en 3 étapes. Propulsé par Claude.">
  <meta property="og:type" content="website">
  <link rel="stylesheet" href="styles/main.css">
  <style>
    /* ── Hero ── */
    .hero {
      padding: 90px 5% 80px;
      max-width: 1200px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }
    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--g7);
      border: 1px solid var(--g5);
      color: var(--g2);
      font-size: 13px;
      font-weight: 600;
      padding: 6px 14px;
      border-radius: 100px;
      margin-bottom: 28px;
    }
    .eyebrow-dot {
      width: 7px; height: 7px;
      background: var(--g3);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }
    .hero h1 {
      font-family: var(--font-display);
      font-size: clamp(2.4rem, 5vw, 3.6rem);
      line-height: 1.1;
      color: var(--ink);
      letter-spacing: -1px;
      margin-bottom: 22px;
    }
    .hero h1 em { font-style: italic; color: var(--g2); }
    .hero-sub {
      font-size: 1.05rem;
      color: var(--muted);
      line-height: 1.75;
      max-width: 460px;
      margin-bottom: 36px;
    }
    .hero-cta { display: flex; gap: 14px; align-items: center; flex-wrap: wrap; }
    .trust-row {
      display: flex;
      align-items: center;
      gap: 14px;
      margin-top: 28px;
      font-size: 13px;
      color: var(--muted);
    }
    .stars { color: #EF9F27; letter-spacing: 1px; }

    /* ── Chat Mockup ── */
    .hero-mockup { position: relative; }
    .floating-tag {
      position: absolute;
      background: #fff;
      border: 1px solid var(--line);
      border-radius: 12px;
      padding: 10px 14px;
      font-size: 12px;
      font-weight: 600;
      color: var(--ink2);
      white-space: nowrap;
      box-shadow: var(--shadow-md);
      z-index: 2;
    }
    .ft1 { top: -16px; right: 16px; animation: floatY 4s ease-in-out infinite; }
    .ft2 { bottom: -12px; left: 10px; animation: floatY 5s ease-in-out 1s infinite; }
    @keyframes floatY {
      0%,100% { transform: translateY(0); }
      50%      { transform: translateY(-6px); }
    }
    .ft-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; margin-right: 5px; }
    .chat-window {
      background: #fff;
      border: 1px solid var(--line);
      border-radius: var(--radius-xl);
      padding: 22px;
      box-shadow: var(--shadow-lg);
    }
    .chat-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-bottom: 16px;
      margin-bottom: 16px;
      border-bottom: 1px solid var(--g7);
    }
    .agent-row { display: flex; align-items: center; gap: 10px; }
    .agent-av {
      width: 40px; height: 40px;
      border-radius: 11px;
      background: var(--g7);
      border: 1.5px solid var(--g5);
      display: flex; align-items: center; justify-content: center;
      font-size: 20px;
    }
    .agent-name { font-weight: 700; font-size: 14px; color: var(--ink); }
    .agent-type { font-size: 12px; color: var(--g3); font-weight: 500; }
    .online-badge {
      font-size: 11px; font-weight: 600;
      color: var(--g2);
      background: var(--g7);
      padding: 4px 10px;
      border-radius: 100px;
      border: 1px solid var(--g5);
    }
    .chat-messages { display: flex; flex-direction: column; gap: 10px; margin-bottom: 14px; }
    .bubble {
      padding: 11px 15px;
      border-radius: 14px;
      font-size: 13.5px;
      line-height: 1.55;
      max-width: 86%;
    }
    .bubble-ai {
      background: var(--g8);
      border: 1px solid var(--g6);
      color: var(--ink2);
      border-radius: 4px 14px 14px 14px;
    }
    .bubble-user {
      background: var(--g1);
      color: #fff;
      border-radius: 14px 14px 4px 14px;
      align-self: flex-end;
    }
    .typing {
      display: flex; gap: 4px; align-items: center;
      padding: 10px 14px;
      background: var(--g8);
      border: 1px solid var(--g6);
      border-radius: 4px 14px 14px 14px;
      width: fit-content;
    }
    .td {
      width: 6px; height: 6px;
      background: var(--g4);
      border-radius: 50%;
      animation: td 1.2s ease infinite;
    }
    .td:nth-child(2) { animation-delay: .2s; }
    .td:nth-child(3) { animation-delay: .4s; }
    @keyframes td {
      0%,80%,100% { transform: scale(.6); opacity: .4; }
      40%          { transform: scale(1); opacity: 1; }
    }
    .chat-input-row {
      display: flex; align-items: center; gap: 8px;
      background: var(--g8);
      border: 1px solid var(--line);
      border-radius: 10px;
      padding: 10px 12px;
    }
    .ci-text { flex: 1; font-size: 13px; color: var(--muted); }
    .ci-btn {
      width: 28px; height: 28px;
      background: var(--g2);
      border-radius: 7px;
      display: flex; align-items: center; justify-content: center;
    }
    .ci-btn svg { width: 13px; height: 13px; stroke: #fff; fill: none; stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; }

    /* ── Features ── */
    .features-section { padding: 90px 5%; max-width: 1200px; margin: 0 auto; }
    .section-center { text-align: center; margin-bottom: 56px; }
    .features-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1px;
      background: var(--line);
      border-radius: var(--radius-lg);
      overflow: hidden;
      border: 1px solid var(--line);
    }
    .feat {
      background: #fff;
      padding: 32px 28px;
      transition: background .2s;
    }
    .feat:hover { background: var(--g8); }
    .feat-icon {
      width: 44px; height: 44px;
      border-radius: 12px;
      background: var(--g7);
      display: flex; align-items: center; justify-content: center;
      margin-bottom: 18px;
    }
    .feat-icon svg { width: 22px; height: 22px; stroke: var(--g2); fill: none; stroke-width: 1.8; stroke-linecap: round; stroke-linejoin: round; }
    .feat h3 { font-size: 16px; font-weight: 600; color: var(--ink); margin-bottom: 8px; }
    .feat p { font-size: 14px; color: var(--muted); line-height: 1.65; }

    /* ── Steps ── */
    .steps-section {
      background: var(--g8);
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      padding: 90px 5%;
    }
    .steps-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 40px;
      max-width: 900px;
      margin: 50px auto 0;
      text-align: center;
    }
    .step-num {
      width: 52px; height: 52px;
      border-radius: 50%;
      background: var(--g1);
      color: #fff;
      font-family: var(--font-display);
      font-size: 1.3rem;
      display: flex; align-items: center; justify-content: center;
      margin: 0 auto 20px;
    }
    .step h3 { font-size: 16px; font-weight: 600; color: var(--ink); margin-bottom: 8px; }
    .step p { font-size: 14px; color: var(--muted); line-height: 1.65; }

    /* ── Use Cases ── */
    .usecases-section { padding: 90px 5%; max-width: 1200px; margin: 0 auto; }
    .uc-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
      gap: 12px;
      margin-top: 48px;
    }
    .uc-card {
      background: #fff;
      border: 1px solid var(--line);
      border-radius: 14px;
      padding: 20px 16px;
      text-align: center;
      cursor: pointer;
      transition: all .2s;
      text-decoration: none;
    }
    .uc-card:hover { border-color: var(--g4); background: var(--g8); transform: translateY(-3px); }
    .uc-icon { font-size: 26px; margin-bottom: 10px; }
    .uc-label { font-size: 13px; font-weight: 600; color: var(--ink2); margin-bottom: 4px; }
    .uc-sub { font-size: 12px; color: var(--muted); line-height: 1.4; }

    /* ── Pricing ── */
    .pricing-section { padding: 90px 5%; max-width: 1200px; margin: 0 auto; }
    .plans-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 20px;
      margin-top: 52px;
    }
    .plan-card {
      background: #fff;
      border: 1px solid var(--line);
      border-radius: var(--radius-lg);
      padding: 32px 28px;
      position: relative;
    }
    .plan-card.best { border: 2px solid var(--g3); background: var(--g8); }
    .plan-badge {
      position: absolute;
      top: -13px; left: 28px;
      background: var(--g2);
      color: #fff;
      font-size: 11px; font-weight: 700;
      padding: 4px 14px;
      border-radius: 100px;
    }
    .plan-name { font-size: 13px; font-weight: 600; color: var(--g2); text-transform: uppercase; letter-spacing: 1.5px; margin-bottom: 10px; }
    .plan-price { font-family: var(--font-display); font-size: 3rem; color: var(--ink); line-height: 1; margin-bottom: 4px; }
    .plan-price sub { font-family: var(--font-body); font-size: 14px; font-weight: 400; color: var(--muted); vertical-align: baseline; }
    .plan-desc { font-size: 13px; color: var(--muted); margin: 10px 0 24px; line-height: 1.5; }
    .plan-features { list-style: none; margin-bottom: 28px; }
    .plan-features li {
      font-size: 13.5px; color: var(--ink2);
      padding: 7px 0;
      border-bottom: 1px solid var(--g7);
      display: flex; align-items: center; gap: 10px;
    }
    .plan-features li:last-child { border: none; }
    .tick {
      width: 17px; height: 17px;
      border-radius: 50%;
      background: var(--g6);
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
    }
    .tick svg { width: 9px; height: 9px; stroke: var(--g2); fill: none; stroke-width: 2.5; stroke-linecap: round; stroke-linejoin: round; }

    /* ── Testimonials ── */
    .testi-section {
      background: var(--g7);
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      padding: 80px 5%;
    }
    .testi-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 20px;
      max-width: 1100px;
      margin: 48px auto 0;
    }
    .testi-card { background: #fff; border: 1px solid var(--line); border-radius: var(--radius-lg); padding: 28px; }
    .testi-text { font-size: 14.5px; color: var(--ink2); line-height: 1.7; margin-bottom: 20px; font-style: italic; }
    .testi-author { display: flex; align-items: center; gap: 12px; }
    .testi-av {
      width: 38px; height: 38px;
      border-radius: 50%;
      background: var(--g6);
      display: flex; align-items: center; justify-content: center;
      font-size: 14px; font-weight: 700; color: var(--g2);
    }
    .testi-name { font-size: 13px; font-weight: 600; color: var(--ink); }
    .testi-role { font-size: 12px; color: var(--muted); }

    /* ── CTA Final ── */
    .cta-final {
      background: var(--g1);
      padding: 100px 5%;
      text-align: center;
    }
    .cta-final h2 { font-family: var(--font-display); font-size: clamp(1.8rem, 4vw, 3rem); color: #fff; margin-bottom: 18px; }
    .cta-final p { font-size: 1rem; color: var(--g5); line-height: 1.75; max-width: 480px; margin: 0 auto 36px; }
    .btn-white { background: #fff; color: var(--g1); border: none; }
    .btn-white:hover { background: var(--g6); }

    /* ── Footer ── */
    footer {
      padding: 40px 5%;
      border-top: 1px solid var(--line);
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
    }
    .footer-logo { font-family: var(--font-display); font-size: 1.2rem; color: var(--g1); }
    .footer-links { display: flex; gap: 24px; }
    .footer-links a { font-size: 13px; color: var(--muted); text-decoration: none; transition: color .2s; }
    .footer-links a:hover { color: var(--g2); }
    .footer-copy { font-size: 12px; color: var(--muted); }

    @media (max-width: 768px) {
      .hero { grid-template-columns: 1fr; gap: 40px; padding: 60px 4% 50px; }
      .steps-row { grid-template-columns: 1fr; gap: 28px; }
      footer { flex-direction: column; text-align: center; }
    }
  </style>
</head>
<body>

<nav class="topia-nav">
  <a href="index.html" class="nav-logo"><span class="nav-logo-dot"></span>TopIA</a>
  <ul class="nav-links">
    <li><a href="#features">Fonctionnalités</a></li>
    <li><a href="#usecases">Cas d'usage</a></li>
    <li><a href="#pricing">Tarifs</a></li>
  </ul>
  <div class="nav-actions">
    <a href="login.html" class="btn btn-ghost">Connexion</a>
    <a href="signup.html" class="btn btn-primary">Essai gratuit</a>
  </div>
</nav>

<main>
  <!-- Hero -->
  <section class="hero">
    <div class="hero-left animate-down">
      <div class="eyebrow"><span class="eyebrow-dot"></span>Intelligence artificielle personnalisée</div>
      <h1>Votre IA sur mesure,<br><em>sans une ligne</em><br>de code</h1>
      <p class="hero-sub">Configurez un assistant IA spécialisé dans votre domaine en quelques minutes. Intégrez-le sur votre site ou utilisez-le au quotidien.</p>
      <div class="hero-cta">
        <a href="signup.html" class="btn btn-primary btn-lg">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/></svg>
          Créer mon IA — c'est gratuit
        </a>
        <a href="#features" class="btn btn-ghost btn-lg">Voir comment →</a>
      </div>
      <div class="trust-row">
        <span class="stars">★★★★★</span>
        <span>4.9/5 · Plus de 2 000 utilisateurs satisfaits</span>
      </div>
    </div>
    <div class="hero-mockup animate-up" style="animation-delay:.15s">
      <div class="floating-tag ft1"><span class="ft-dot" style="background:#4DBF7F"></span>IA active · Trading</div>
      <div class="floating-tag ft2"><span class="ft-dot" style="background:#2E9B5A"></span>Widget intégré · votre-site.fr</div>
      <div class="chat-window">
        <div class="chat-header">
          <div class="agent-row">
            <div class="agent-av">📈</div>
            <div>
              <div class="agent-name">TradeIA Pro</div>
              <div class="agent-type">Assistant Trading & Finance</div>
            </div>
          </div>
          <div class="online-badge">● En ligne</div>
        </div>
        <div class="chat-messages">
          <div class="bubble bubble-ai">Bonjour ! Je suis votre assistant trading. Comment puis-je vous aider ?</div>
          <div class="bubble bubble-user">Analyse le Bitcoin pour cette semaine</div>
          <div class="bubble bubble-ai">D'après les indicateurs techniques, le BTC présente une résistance à 68 000$. Le RSI à 58 suggère une dynamique haussière modérée...</div>
        </div>
        <div class="typing"><div class="td"></div><div class="td"></div><div class="td"></div></div>
        <div style="margin-top:12px" class="chat-input-row">
          <span class="ci-text">Posez votre question...</span>
          <div class="ci-btn"><svg viewBox="0 0 24 24"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg></div>
        </div>
      </div>
    </div>
  </section>

  <!-- Features -->
  <section class="features-section" id="features">
    <div class="section-center">
      <p class="overline">Fonctionnalités</p>
      <h2 class="section-title">Tout ce dont vous avez besoin</h2>
    </div>
    <div class="features-grid">
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><path d="M12 20h9"/><path d="M16.5 3.5a2.121 2.121 0 013 3L7 19l-4 1 1-4L16.5 3.5z"/></svg></div>
        <h3>Configuration en langage naturel</h3>
        <p>Décrivez simplement ce que vous voulez. TopIA configure votre IA automatiquement.</p>
      </div>
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="3"/><path d="M19.07 4.93a10 10 0 010 14.14M4.93 4.93a10 10 0 000 14.14"/></svg></div>
        <h3>Widget intégrable en 1 clic</h3>
        <p>Un simple copier-coller de code pour intégrer votre IA sur n'importe quel site.</p>
      </div>
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18M9 21V9"/></svg></div>
        <h3>Tableau de bord complet</h3>
        <p>Suivez les conversations, analysez les performances et ajustez votre IA.</p>
      </div>
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg></div>
        <h3>Données sécurisées</h3>
        <p>Vos données sont chiffrées et ne sont jamais partagées avec des tiers.</p>
      </div>
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75"/></svg></div>
        <h3>Multi-utilisateurs</h3>
        <p>Partagez votre IA avec votre équipe et gérez les accès facilement.</p>
      </div>
      <div class="feat">
        <div class="feat-icon"><svg viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg></div>
        <h3>Propulsé par Claude</h3>
        <p>L'un des modèles IA les plus avancés du marché pour des réponses de qualité.</p>
      </div>
    </div>
  </section>

  <!-- Steps -->
  <section class="steps-section">
    <div style="text-align:center">
      <p class="overline">Comment ça marche</p>
      <h2 class="section-title">Lancé en 3 étapes</h2>
    </div>
    <div class="steps-row">
      <div class="step">
        <div class="step-num">1</div>
        <h3>Décrivez votre IA</h3>
        <p>Choisissez un domaine d'expertise et décrivez la personnalité de votre assistant.</p>
      </div>
      <div class="step">
        <div class="step-num">2</div>
        <h3>Personnalisez</h3>
        <p>Nom, ton, comportements... Affinez chaque détail depuis votre tableau de bord.</p>
      </div>
      <div class="step">
        <div class="step-num">3</div>
        <h3>Déployez</h3>
        <p>Utilisez votre IA sur TopIA ou intégrez-la sur votre site avec un extrait de code.</p>
      </div>
    </div>
  </section>

  <!-- Use Cases -->
  <section class="usecases-section" id="usecases">
    <div class="section-center">
      <p class="overline">Cas d'usage</p>
      <h2 class="section-title">Une IA pour chaque besoin</h2>
    </div>
    <div class="uc-grid">
      <a href="create.html" class="uc-card"><div class="uc-icon">📈</div><div class="uc-label">Trading & Finance</div><div class="uc-sub">Analyses, signaux, stratégies</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">🏠</div><div class="uc-label">Maison & Quotidien</div><div class="uc-sub">Organisation, plannings</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">🥗</div><div class="uc-label">Nutrition & Cuisine</div><div class="uc-sub">Recettes, régimes</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">⚖️</div><div class="uc-label">Droit & Administratif</div><div class="uc-sub">Droits, courriers</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">💪</div><div class="uc-label">Sport & Bien-être</div><div class="uc-sub">Programmes, suivi</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">🛍️</div><div class="uc-label">E-commerce</div><div class="uc-sub">Support client, FAQ</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">📚</div><div class="uc-label">Éducation</div><div class="uc-sub">Cours, exercices</div></a>
      <a href="create.html" class="uc-card"><div class="uc-icon">✨</div><div class="uc-label">Personnalisé</div><div class="uc-sub">Créez le vôtre</div></a>
    </div>
  </section>

  <!-- Pricing -->
  <section class="pricing-section" id="pricing" style="background:var(--g8);border-top:1px solid var(--line)">
    <div class="section-center">
      <p class="overline">Tarifs</p>
      <h2 class="section-title">Simple, transparent, évolutif</h2>
      <p style="color:var(--muted);font-size:1rem;margin-top:12px">Commencez gratuitement. Aucune carte bancaire requise.</p>
    </div>
    <div class="plans-grid">
      <div class="plan-card">
        <div class="plan-name">Découverte</div>
        <div class="plan-price">0<sub>€/mois</sub></div>
        <div class="plan-desc">Pour tester et découvrir TopIA.</div>
        <ul class="plan-features">
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>1 IA personnalisée</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>50 messages par jour</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>3 domaines</li>
        </ul>
        <a href="signup.html" class="btn btn-ghost" style="width:100%;justify-content:center">Commencer gratuitement</a>
      </div>
      <div class="plan-card best">
        <div class="plan-badge">✦ Le plus choisi</div>
        <div class="plan-name">Pro</div>
        <div class="plan-price">18<sub>€/mois</sub></div>
        <div class="plan-desc">Pour les utilisateurs réguliers.</div>
        <ul class="plan-features">
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>5 IAs personnalisées</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Messages illimités</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Tous les domaines</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Widget intégrable</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Support prioritaire</li>
        </ul>
        <a href="signup.html" class="btn btn-primary" style="width:100%;justify-content:center">Choisir Pro</a>
      </div>
      <div class="plan-card">
        <div class="plan-name">Business</div>
        <div class="plan-price">48<sub>€/mois</sub></div>
        <div class="plan-desc">Pour les entreprises.</div>
        <ul class="plan-features">
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>IAs illimitées</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>API dédiée & webhooks</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Marque blanche</li>
          <li><div class="tick"><svg viewBox="0 0 12 12"><polyline points="2,6 5,9 10,3"/></svg></div>Account manager</li>
        </ul>
        <a href="login.html" class="btn btn-ghost" style="width:100%;justify-content:center">Nous contacter</a>
      </div>
    </div>
  </section>

  <!-- Testimonials -->
  <section class="testi-section">
    <div style="text-align:center">
      <p class="overline">Témoignages</p>
      <h2 class="section-title">Ils nous font confiance</h2>
    </div>
    <div class="testi-grid">
      <div class="testi-card"><div class="testi-text">"J'ai créé mon IA de trading en 10 minutes. Elle analyse les marchés pour moi chaque matin."</div><div class="testi-author"><div class="testi-av">ML</div><div><div class="testi-name">Marc L.</div><div class="testi-role">Investisseur particulier</div></div></div></div>
      <div class="testi-card"><div class="testi-text">"Mon IA de support est intégrée sur mon site e-commerce. Les ventes ont augmenté de 20%."</div><div class="testi-author"><div class="testi-av">SC</div><div><div class="testi-name">Sophie C.</div><div class="testi-role">Gérante e-commerce</div></div></div></div>
      <div class="testi-card"><div class="testi-text">"Incroyablement simple. Mon IA nutritionniste répond mieux que n'importe quelle appli."</div><div class="testi-author"><div class="testi-av">AR</div><div><div class="testi-name">Amina R.</div><div class="testi-role">Coach bien-être</div></div></div></div>
    </div>
  </section>

  <!-- CTA Final -->
  <section class="cta-final">
    <h2>Prêt à créer <em style="color:var(--g4)">votre</em> IA ?</h2>
    <p>Rejoignez des milliers d'utilisateurs qui ont déjà leur assistant intelligent. Gratuit pour commencer.</p>
    <a href="signup.html" class="btn btn-white btn-lg">Créer mon IA gratuitement →</a>
  </section>
</main>

<footer>
  <div class="footer-logo">TopIA</div>
  <div class="footer-links">
    <a href="#">Fonctionnalités</a>
    <a href="#">Tarifs</a>
    <a href="#">Blog</a>
    <a href="#">Confidentialité</a>
    <a href="#">CGU</a>
    <a href="login.html">Connexion</a>
  </div>
  <div class="footer-copy">© 2025 TopIA · Tous droits réservés</div>
</footer>

</body>
</html>
