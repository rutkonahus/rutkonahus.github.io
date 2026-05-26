<html lang="no">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prosjektstyring – Sykehusbygg</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #f0f3f7;
    --surface: #ffffff;
    --surface-hover: #f8fafc;
    --border: #dde3ec;
    --border-active: #8aabc8;
    --blue-deep: #1a3a5c;
    --blue-mid: #2e6fa3;
    --blue-light: #5b9ec9;
    --blue-pale: #c8dff0;
    --blue-mist: #e8f1f8;
    --slate: #4a5e72;
    --slate-light: #7a94aa;
    --accent: #3d7ebf;
    --accent-soft: #e0edf7;
    --green: #4a8c6e;
    --green-soft: #d4ece2;
    --text-primary: #1a2e42;
    --text-secondary: #4a5e72;
    --text-muted: #8fa8bc;
    --shadow-sm: 0 1px 4px rgba(30,60,90,0.07), 0 2px 12px rgba(30,60,90,0.04);
    --shadow-md: 0 4px 20px rgba(30,60,90,0.10), 0 1px 4px rgba(30,60,90,0.06);
    --shadow-lg: 0 8px 40px rgba(30,60,90,0.14), 0 2px 8px rgba(30,60,90,0.08);
    --radius: 16px;
    --radius-sm: 10px;
    --transition: 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text-primary);
    min-height: 100vh;
    padding: 40px 20px 60px;
    background-image:
      radial-gradient(ellipse 80% 60% at 20% -10%, rgba(91,158,201,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 80% 100%, rgba(42,111,163,0.08) 0%, transparent 50%);
  }

  header {
    max-width: 900px;
    margin: 0 auto 48px;
    text-align: center;
  }

  .eyebrow {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--blue-light);
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
  }

  .eyebrow::before, .eyebrow::after {
    content: '';
    display: block;
    width: 32px;
    height: 1px;
    background: var(--blue-pale);
  }

  h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(26px, 4vw, 38px);
    color: var(--blue-deep);
    line-height: 1.2;
    margin-bottom: 14px;
    font-weight: 400;
  }

  .subtitle {
    font-size: 15px;
    color: var(--slate);
    font-weight: 300;
    max-width: 480px;
    margin: 0 auto;
    line-height: 1.6;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    max-width: 900px;
    margin: 0 auto;
  }

  .card {
    background: var(--surface);
    border-radius: var(--radius);
    border: 1.5px solid var(--border);
    box-shadow: var(--shadow-sm);
    cursor: pointer;
    transition: box-shadow var(--transition), border-color var(--transition), transform var(--transition);
    overflow: hidden;
    position: relative;
  }

  .card:hover {
    box-shadow: var(--shadow-md);
    border-color: var(--border-active);
    transform: translateY(-2px);
  }

  .card.active {
    box-shadow: var(--shadow-lg);
    border-color: var(--accent);
    transform: translateY(-3px);
  }

  .card-header {
    padding: 28px 28px 24px;
    display: flex;
    align-items: flex-start;
    gap: 16px;
  }

  .card-icon {
    width: 44px;
    height: 44px;
    border-radius: 12px;
    background: var(--blue-mist);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: background var(--transition);
  }

  .card.active .card-icon {
    background: var(--accent-soft);
  }

  .card-icon svg {
    width: 22px;
    height: 22px;
    stroke: var(--blue-mid);
    fill: none;
    stroke-width: 1.6;
    stroke-linecap: round;
    stroke-linejoin: round;
    transition: stroke var(--transition);
  }

  .card.active .card-icon svg {
    stroke: var(--accent);
  }

  .card-title-area { flex: 1; }

  .card-number {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.1em;
    color: var(--text-muted);
    margin-bottom: 4px;
  }

  .card-title {
    font-size: 17px;
    font-weight: 500;
    color: var(--text-primary);
    line-height: 1.3;
  }

  .card-arrow {
    width: 24px;
    height: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--text-muted);
    transition: transform var(--transition), color var(--transition);
    flex-shrink: 0;
    margin-top: 2px;
  }

  .card.active .card-arrow {
    transform: rotate(180deg);
    color: var(--accent);
  }

  .card-arrow svg {
    width: 16px;
    height: 16px;
    stroke: currentColor;
    fill: none;
    stroke-width: 2;
    stroke-linecap: round;
    stroke-linejoin: round;
  }

  .card-body {
    display: grid;
    grid-template-rows: 0fr;
    transition: grid-template-rows 0.45s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  .card.active .card-body {
    grid-template-rows: 1fr;
  }

  .card-body-inner {
    overflow: hidden;
  }

  .card-content {
    padding: 0 28px 28px;
    border-top: 1px solid var(--border);
    margin-top: 0;
  }

  .card-explanation {
    padding-top: 20px;
    font-size: 14px;
    line-height: 1.7;
    color: var(--slate);
    font-weight: 300;
    margin-bottom: 24px;
  }

  .card-explanation strong {
    color: var(--text-primary);
    font-weight: 500;
  }

  /* ─── SVG Infographics ─── */

  .infographic {
    background: var(--blue-mist);
    border-radius: var(--radius-sm);
    padding: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 160px;
  }

  .infographic svg {
    width: 100%;
    max-width: 340px;
    height: auto;
    overflow: visible;
  }

  /* Animation classes triggered when card opens */
  .animate .draw-in {
    stroke-dasharray: 400;
    stroke-dashoffset: 400;
    animation: drawLine 0.8s ease forwards;
  }

  .animate .fade-up {
    opacity: 0;
    transform: translateY(8px);
    animation: fadeUp 0.5s ease forwards;
  }

  .animate .scale-in {
    transform: scale(0);
    animation: scaleIn 0.4s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
  }

  .animate .fill-bar {
    transform: scaleX(0);
    transform-origin: left;
    animation: fillBar 0.6s ease forwards;
  }

  @keyframes drawLine {
    to { stroke-dashoffset: 0; }
  }
  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes scaleIn {
    to { transform: scale(1); }
  }
  @keyframes fillBar {
    to { transform: scaleX(1); }
  }

  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.3s; }
  .delay-4 { animation-delay: 0.4s; }
  .delay-5 { animation-delay: 0.5s; }
  .delay-6 { animation-delay: 0.6s; }

  footer {
    text-align: center;
    margin-top: 48px;
    font-size: 12px;
    color: var(--text-muted);
    letter-spacing: 0.04em;
  }

  @media (max-width: 640px) {
    body { padding: 24px 16px 48px; }
    .grid { grid-template-columns: 1fr; }
    header { margin-bottom: 32px; }
    h1 { font-size: 24px; }
  }
</style>
</head>
<body>

<header>
  <div class="eyebrow">Læringsmodul</div>
  <h1>Kjennetegn ved<br>prosjekt som arbeidsform</h1>
  <p class="subtitle">Velg et kort for å utforske de fire grunnleggende kjennetegnene ved prosjektstyring i sykehusbygg.</p>
</header>

<div class="grid">

  <!-- Card 1 -->
  <div class="card" id="card-1" onclick="toggleCard(1)" role="button" aria-expanded="false" tabindex="0">
    <div class="card-header">
      <div class="card-icon">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="5" r="2"/><path d="M12 7v4M8 13a4 4 0 0 1 8 0"/><circle cx="5" cy="17" r="2"/><circle cx="19" cy="17" r="2"/><path d="M7 17H5M19 17h-2M12 11v6"/></svg>
      </div>
      <div class="card-title-area">
        <div class="card-number">01</div>
        <div class="card-title">Midlertidig organisasjon</div>
      </div>
      <div class="card-arrow">
        <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
    </div>
    <div class="card-body">
      <div class="card-body-inner">
        <div class="card-content">
          <p class="card-explanation">
            Et prosjekt etablerer en <strong>dedikert organisasjon</strong> som eksisterer kun for prosjektets levetid. Ressurser, roller og ansvar settes sammen for anledningen – og oppløses når oppdraget er fullført. Dette gir fleksibilitet og fokus, men krever tydelig styring fra starten.
          </p>
          <div class="infographic" id="infographic-1">
            <svg viewBox="0 0 300 160" xmlns="http://www.w3.org/2000/svg">
              <!-- Top: Prosjekteier -->
              <rect class="scale-in" x="110" y="8" width="80" height="32" rx="8" fill="#2e6fa3" opacity="0.9"/>
              <text class="fade-up delay-1" x="150" y="29" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="11" font-weight="500" fill="white">Prosjekteier</text>

              <!-- Lines down -->
              <line class="draw-in delay-2" x1="150" y1="40" x2="150" y2="60" stroke="#8aabc8" stroke-width="1.5"/>
              <line class="draw-in delay-2" x1="60" y1="60" x2="240" y2="60" stroke="#8aabc8" stroke-width="1.5"/>
              <line class="draw-in delay-3" x1="60" y1="60" x2="60" y2="75" stroke="#8aabc8" stroke-width="1.5"/>
              <line class="draw-in delay-3" x1="150" y1="60" x2="150" y2="75" stroke="#8aabc8" stroke-width="1.5"/>
              <line class="draw-in delay-3" x1="240" y1="60" x2="240" y2="75" stroke="#8aabc8" stroke-width="1.5"/>

              <!-- Level 2 boxes -->
              <rect class="scale-in delay-3" x="20" y="75" width="80" height="28" rx="7" fill="#5b9ec9" opacity="0.75"/>
              <rect class="scale-in delay-3" x="110" y="75" width="80" height="28" rx="7" fill="#5b9ec9" opacity="0.75"/>
              <rect class="scale-in delay-3" x="200" y="75" width="80" height="28" rx="7" fill="#5b9ec9" opacity="0.75"/>

              <text class="fade-up delay-4" x="60" y="93" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="white">Prosjektleder</text>
              <text class="fade-up delay-4" x="150" y="93" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="white">Byggeleder</text>
              <text class="fade-up delay-4" x="240" y="93" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="white">Brukere</text>

              <!-- Level 3 dots -->
              <circle class="scale-in delay-5" cx="40" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="60" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="80" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="130" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="150" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="220" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="240" cy="130" r="5" fill="#c8dff0"/>
              <circle class="scale-in delay-5" cx="260" cy="130" r="5" fill="#c8dff0"/>
              <line class="draw-in delay-4" x1="60" y1="103" x2="60" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="150" y1="103" x2="150" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="240" y1="103" x2="240" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="40" y1="118" x2="80" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="130" y1="118" x2="170" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="220" y1="118" x2="260" y2="118" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="40" y1="118" x2="40" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="60" y1="118" x2="60" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="80" y1="118" x2="80" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="130" y1="118" x2="130" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="150" y1="118" x2="150" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="220" y1="118" x2="220" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="240" y1="118" x2="240" y2="125" stroke="#c8dff0" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="260" y1="118" x2="260" y2="125" stroke="#c8dff0" stroke-width="1.2"/>

              <text class="fade-up delay-6" x="150" y="155" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#7a94aa">Midlertidig – oppløses ved ferdigstillelse</text>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Card 2 -->
  <div class="card" id="card-2" onclick="toggleCard(2)" role="button" aria-expanded="false" tabindex="0">
    <div class="card-header">
      <div class="card-icon">
        <svg viewBox="0 0 24 24"><rect x="3" y="4" width="18" height="16" rx="2"/><line x1="3" y1="9" x2="21" y2="9"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="16" y1="2" x2="16" y2="6"/></svg>
      </div>
      <div class="card-title-area">
        <div class="card-number">02</div>
        <div class="card-title">Tidsavgrenset oppgave</div>
      </div>
      <div class="card-arrow">
        <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
    </div>
    <div class="card-body">
      <div class="card-body-inner">
        <div class="card-content">
          <p class="card-explanation">
            Prosjektet har et <strong>definert start- og sluttpunkt</strong>. Tidsrammen skaper disiplin og muliggjør planlegging. For store sykehusprosjekter strekker dette seg gjerne over 10–15 år – fra konseptfase til idriftsettelse. Hver fase har egne milepæler og beslutningspunkter.
          </p>
          <div class="infographic" id="infographic-2">
            <svg viewBox="0 0 300 160" xmlns="http://www.w3.org/2000/svg">
              <!-- Timeline base line -->
              <line class="draw-in" x1="20" y1="80" x2="280" y2="80" stroke="#2e6fa3" stroke-width="2"/>

              <!-- Phase bars -->
              <rect class="fill-bar delay-1" x="20" y="68" width="52" height="24" rx="5" fill="#5b9ec9" opacity="0.55"/>
              <rect class="fill-bar delay-2" x="78" y="68" width="60" height="24" rx="5" fill="#5b9ec9" opacity="0.7"/>
              <rect class="fill-bar delay-3" x="144" y="68" width="70" height="24" rx="5" fill="#2e6fa3" opacity="0.75"/>
              <rect class="fill-bar delay-4" x="220" y="68" width="60" height="24" rx="5" fill="#1a3a5c" opacity="0.8"/>

              <text class="fade-up delay-1" x="46" y="84" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9.5" fill="white" font-weight="500">Konsept</text>
              <text class="fade-up delay-2" x="108" y="84" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9.5" fill="white" font-weight="500">Forprosjekt</text>
              <text class="fade-up delay-3" x="179" y="84" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9.5" fill="white" font-weight="500">Bygging</text>
              <text class="fade-up delay-4" x="250" y="84" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9.5" fill="white" font-weight="500">Innflytting</text>

              <!-- Milestone diamonds -->
              <polygon class="scale-in delay-2" points="78,80 85,73 78,66 71,73" fill="#fff" stroke="#2e6fa3" stroke-width="1.5"/>
              <polygon class="scale-in delay-3" points="144,80 151,73 144,66 137,73" fill="#fff" stroke="#2e6fa3" stroke-width="1.5"/>
              <polygon class="scale-in delay-4" points="220,80 227,73 220,66 213,73" fill="#fff" stroke="#2e6fa3" stroke-width="1.5"/>
              <polygon class="scale-in delay-5" points="280,80 287,73 280,66 273,73" fill="#2e6fa3" stroke="#2e6fa3" stroke-width="1.5"/>

              <!-- Labels below -->
              <text class="fade-up delay-3" x="78" y="108" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#4a5e72">KS1</text>
              <text class="fade-up delay-4" x="144" y="108" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#4a5e72">KS2</text>
              <text class="fade-up delay-5" x="220" y="108" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#4a5e72">Åpning</text>
              <text class="fade-up delay-5" x="280" y="108" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#2e6fa3" font-weight="500">Slutt</text>

              <!-- Connector lines -->
              <line class="draw-in delay-3" x1="78" y1="92" x2="78" y2="102" stroke="#8aabc8" stroke-width="1.2"/>
              <line class="draw-in delay-4" x1="144" y1="92" x2="144" y2="102" stroke="#8aabc8" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="220" y1="92" x2="220" y2="102" stroke="#8aabc8" stroke-width="1.2"/>
              <line class="draw-in delay-5" x1="280" y1="92" x2="280" y2="102" stroke="#2e6fa3" stroke-width="1.2"/>

              <!-- Start label -->
              <text class="fade-up delay-1" x="20" y="108" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#8aabc8">Start</text>

              <text class="fade-up delay-6" x="150" y="145" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#7a94aa">Gjennomføring over definert tidshorisont</text>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Card 3 -->
  <div class="card" id="card-3" onclick="toggleCard(3)" role="button" aria-expanded="false" tabindex="0">
    <div class="card-header">
      <div class="card-icon">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="9"/><polyline points="12 8 12 12 15 15"/></svg>
      </div>
      <div class="card-title-area">
        <div class="card-number">03</div>
        <div class="card-title">Definerte mål</div>
      </div>
      <div class="card-arrow">
        <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
    </div>
    <div class="card-body">
      <div class="card-body-inner">
        <div class="card-content">
          <p class="card-explanation">
            Prosjektet styres mot <strong>klare og målbare mål</strong> langs tre dimensjoner: tid, kostnad og kvalitet. Disse tre henger tett sammen – endringer i én parameter påvirker alltid de andre. God prosjektledelse handler om å balansere alle tre gjennom hele prosjektets levetid.
          </p>
          <div class="infographic" id="infographic-3">
            <svg viewBox="0 0 300 160" xmlns="http://www.w3.org/2000/svg">
              <!-- Triangle outline -->
              <polygon class="draw-in" points="150,18 268,148 32,148" fill="none" stroke="#2e6fa3" stroke-width="1.8" stroke-linejoin="round"/>

              <!-- Three pillar rects with depth -->
              <!-- Tid pillar -->
              <rect class="scale-in delay-2" x="32" y="108" width="60" height="40" rx="6" fill="#5b9ec9" opacity="0.7"/>
              <text class="fade-up delay-3" x="62" y="132" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="13" font-weight="600" fill="white">Tid</text>

              <!-- Kostnad pillar -->
              <rect class="scale-in delay-2" x="120" y="88" width="60" height="60" rx="6" fill="#2e6fa3" opacity="0.85"/>
              <text class="fade-up delay-3" x="150" y="112" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="11" font-weight="600" fill="white">Kostnad</text>
              <text class="fade-up delay-4" x="150" y="128" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="rgba(255,255,255,0.8)">Budsjett</text>

              <!-- Kvalitet pillar -->
              <rect class="scale-in delay-2" x="208" y="108" width="60" height="40" rx="6" fill="#5b9ec9" opacity="0.7"/>
              <text class="fade-up delay-3" x="238" y="132" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="11" font-weight="600" fill="white">Kvalitet</text>

              <!-- Center balance icon -->
              <circle class="scale-in delay-4" cx="150" cy="60" r="16" fill="#e8f1f8" stroke="#8aabc8" stroke-width="1.2"/>
              <text x="150" y="65" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="18" fill="#2e6fa3">⊖</text>

              <text class="fade-up delay-5" x="150" y="155" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#7a94aa">Balanse mellom de tre dimensjonene</text>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Card 4 -->
  <div class="card" id="card-4" onclick="toggleCard(4)" role="button" aria-expanded="false" tabindex="0">
    <div class="card-header">
      <div class="card-icon">
        <svg viewBox="0 0 24 24"><path d="M12 2L2 7l10 5 10-5-10-5z"/><path d="M2 17l10 5 10-5"/><path d="M2 12l10 5 10-5"/></svg>
      </div>
      <div class="card-title-area">
        <div class="card-number">04</div>
        <div class="card-title">Ønskede gevinster</div>
      </div>
      <div class="card-arrow">
        <svg viewBox="0 0 24 24"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
    </div>
    <div class="card-body">
      <div class="card-body-inner">
        <div class="card-content">
          <p class="card-explanation">
            Et sykehusprosjekt eksisterer ikke for sin egen skyld – det drives av <strong>ønskede gevinster</strong> for pasienter, ansatte og samfunnet. Gevinstene realiseres først etter at bygget er tatt i bruk. Dette krever at driftsorganisasjonen forberedes gjennom hele prosjektperioden.
          </p>
          <div class="infographic" id="infographic-4">
            <svg viewBox="0 0 300 160" xmlns="http://www.w3.org/2000/svg">
              <!-- Arrow path from construction to hospital -->
              <defs>
                <marker id="arrowhead" markerWidth="8" markerHeight="6" refX="8" refY="3" orient="auto">
                  <polygon points="0 0, 8 3, 0 6" fill="#2e6fa3"/>
                </marker>
              </defs>

              <!-- Construction phase box -->
              <rect class="scale-in delay-1" x="12" y="55" width="86" height="60" rx="10" fill="#e8f1f8" stroke="#8aabc8" stroke-width="1.2"/>
              <!-- Crane icon -->
              <line class="draw-in delay-2" x1="40" y1="100" x2="40" y2="70" stroke="#5b9ec9" stroke-width="2"/>
              <line class="draw-in delay-2" x1="40" y1="70" x2="75" y2="70" stroke="#5b9ec9" stroke-width="2"/>
              <line class="draw-in delay-3" x1="75" y1="70" x2="75" y2="82" stroke="#5b9ec9" stroke-width="1.5" stroke-dasharray="3,2"/>
              <rect class="scale-in delay-3" x="62" y="82" width="24" height="18" rx="3" fill="#5b9ec9" opacity="0.6"/>
              <rect class="scale-in delay-2" x="28" y="87" width="25" height="13" rx="2" fill="#8aabc8" opacity="0.7"/>

              <text class="fade-up delay-3" x="55" y="128" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#4a5e72" font-weight="500">Bygging</text>

              <!-- Arrow -->
              <path class="draw-in delay-4" d="M 100 85 Q 150 60 200 85" fill="none" stroke="#2e6fa3" stroke-width="1.8" marker-end="url(#arrowhead)"/>
              <text class="fade-up delay-5" x="150" y="58" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="9" fill="#5b9ec9">Overlevering</text>

              <!-- Hospital/operation box -->
              <rect class="scale-in delay-4" x="202" y="55" width="86" height="60" rx="10" fill="#d4ece2" stroke="#4a8c6e" stroke-width="1.2" opacity="0.9"/>
              <!-- Hospital icon -->
              <rect class="scale-in delay-5" x="224" y="75" width="42" height="35" rx="3" fill="#4a8c6e" opacity="0.5"/>
              <rect class="scale-in delay-5" x="236" y="80" width="8" height="12" rx="1" fill="white" opacity="0.8"/>
              <rect class="scale-in delay-5" x="249" y="80" width="8" height="12" rx="1" fill="white" opacity="0.8"/>
              <!-- Cross -->
              <rect class="scale-in delay-6" x="240" y="63" width="4" height="12" rx="1" fill="#4a8c6e"/>
              <rect class="scale-in delay-6" x="236" y="67" width="12" height="4" rx="1" fill="#4a8c6e"/>

              <text class="fade-up delay-6" x="245" y="128" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#4a8c6e" font-weight="500">Drift</text>

              <!-- Benefit label -->
              <text class="fade-up delay-6" x="150" y="152" text-anchor="middle" font-family="DM Sans,sans-serif" font-size="10" fill="#7a94aa">Gevinster realiseres i drift – ikke i bygging</text>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>

</div>


<script>
  let openCard = null;

  function toggleCard(id) {
    const card = document.getElementById('card-' + id);
    const infographic = document.getElementById('infographic-' + id);
    const isOpen = card.classList.contains('active');

    // Close currently open card
    if (openCard && openCard !== id) {
      const prevCard = document.getElementById('card-' + openCard);
      const prevInfographic = document.getElementById('infographic-' + openCard);
      prevCard.classList.remove('active');
      prevCard.setAttribute('aria-expanded', 'false');
      prevInfographic.classList.remove('animate');
    }

    if (isOpen) {
      card.classList.remove('active');
      card.setAttribute('aria-expanded', 'false');
      infographic.classList.remove('animate');
      openCard = null;
    } else {
      card.classList.add('active');
      card.setAttribute('aria-expanded', 'true');
      openCard = id;
      // Trigger animations after expansion starts
      setTimeout(() => {
        infographic.classList.add('animate');
      }, 80);
    }
  }

  // Keyboard support
  document.querySelectorAll('.card').forEach(card => {
    card.addEventListener('keydown', (e) => {
      if (e.key === 'Enter' || e.key === ' ') {
        e.preventDefault();
        card.click();
      }
    });
  });
</script>
</body>
</html>
