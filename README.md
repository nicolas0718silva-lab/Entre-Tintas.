<!DOCTYPE html>
<html lang="pt-BR" data-theme="light">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1">
<title>Entre tintas — Agendamento</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,400;0,9..144,500;0,9..144,600;0,9..144,700;1,9..144,500;1,9..144,600&family=Work+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap" rel="stylesheet">
<style>
/* ============================================================
   ENTRE TINTAS — design tokens
   Paleta inspirada nas cores primárias do pigmento (vermelho
   cádmio, amarelo cádmio, azul ultramarino) — as três tintas
   de onde toda mistura da Laila começa.
   ============================================================ */
:root,
[data-theme="light"]{
  --canvas:#FAF6EE;
  --canvas-2:#F3EDE0;
  --surface:#FFFFFF;
  --surface-2:#FBF8F2;
  --ink:#241E17;
  --ink-soft:#6F6555;
  --ink-faint:#A79C89;
  --line:#E6DCC8;
  --red:#D6432B;
  --red-ink:#B23320;
  --yellow:#EEAF0E;
  --yellow-ink:#B9800C;
  --blue:#1D5FA8;
  --blue-ink:#164A85;
  --success:#2E7D4F;
  --shadow:0 16px 40px -14px rgba(36,30,23,.28);
  --shadow-s:0 6px 16px -8px rgba(36,30,23,.24);
  color-scheme: light;
}
[data-theme="dark"]{
  --canvas:#17130F;
  --canvas-2:#1D1812;
  --surface:#221C15;
  --surface-2:#2A2318;
  --ink:#F4EEE2;
  --ink-soft:#BDB09B;
  --ink-faint:#8A7D68;
  --line:#3B3225;
  --red:#E4593D;
  --red-ink:#F2775A;
  --yellow:#F0BB3C;
  --yellow-ink:#F5CE6E;
  --blue:#5590D4;
  --blue-ink:#79ABE4;
  --success:#59B980;
  --shadow:0 16px 40px -12px rgba(0,0,0,.55);
  --shadow-s:0 6px 18px -8px rgba(0,0,0,.5);
  color-scheme: dark;
}
:root{
  --font-display:'Fraunces', serif;
  --font-body:'Work Sans', sans-serif;
  --font-mono:'IBM Plex Mono', monospace;
  --r-s:8px; --r-m:14px; --r-l:22px; --r-full:999px;
}
*,*::before,*::after{ box-sizing:border-box; }
html,body{ height:100%; }
body{
  margin:0;
  background:var(--canvas);
  color:var(--ink);
  font-family:var(--font-body);
  -webkit-font-smoothing:antialiased;
  transition:background .35s ease, color .35s ease;
}
h1,h2,h3,h4{ font-family:var(--font-display); margin:0; color:var(--ink); font-weight:600; }
p{ margin:0; }
button{ font-family:inherit; }
input,textarea{ font-family:inherit; }
.hidden{ display:none !important; }
img{ max-width:100%; display:block; }

/* focus visibility */
button:focus-visible, input:focus-visible, textarea:focus-visible, [tabindex]:focus-visible{
  outline:2px solid var(--blue);
  outline-offset:2px;
}

@media (prefers-reduced-motion: reduce){
  *{ animation-duration:.001ms !important; animation-iteration-count:1 !important; transition-duration:.001ms !important; }
}

/* ---------------- typography helpers ---------------- */
.eyebrow{
  display:inline-block;
  font-family:var(--font-mono);
  font-size:11px;
  letter-spacing:.12em;
  text-transform:uppercase;
  color:var(--ink-faint);
  margin-bottom:10px;
}
.brand-title{
  font-size:44px;
  line-height:1.02;
  letter-spacing:-.01em;
}
.brand-title em{
  font-style:italic;
  font-weight:500;
  background:linear-gradient(92deg, var(--red), var(--yellow) 52%, var(--blue));
  -webkit-background-clip:text;
  background-clip:text;
  color:transparent;
}
.brand-tag{
  font-size:14px;
  color:var(--ink-soft);
  margin-top:10px;
}

/* ---------------- buttons ---------------- */
.btn{
  appearance:none;
  border:none;
  cursor:pointer;
  border-radius:var(--r-full);
  padding:14px 22px;
  font-size:15px;
  font-weight:600;
  letter-spacing:.01em;
  transition:transform .15s ease, box-shadow .15s ease, background .2s ease, opacity .15s ease;
}
.btn:active{ transform:scale(.97); }
.btn-primary{
  background:var(--ink);
  color:var(--canvas);
  box-shadow:var(--shadow-s);
}
[data-theme="dark"] .btn-primary{ color:var(--canvas); }
.btn-primary:hover{ box-shadow:var(--shadow); }
.btn-block{ width:100%; }
.btn-ghost{
  background:transparent;
  color:var(--ink);
  border:1.5px solid var(--line);
}
.btn-ghost:hover{ border-color:var(--ink-faint); }
.btn-danger{
  background:var(--red);
  color:#fff;
}
.btn-small{
  padding:8px 16px;
  font-size:13px;
  border-radius:var(--r-full);
  background:var(--ink);
  color:var(--canvas);
  border:none;
  cursor:pointer;
}
.btn-link{
  background:none;
  border:none;
  color:var(--ink-soft);
  font-size:13px;
  cursor:pointer;
  text-decoration:underline;
  padding:10px 0;
}
.btn-cta{
  position:relative;
  padding:16px 26px;
  white-space:nowrap;
}
.icon-btn{
  width:40px; height:40px;
  border-radius:var(--r-full);
  border:1.5px solid var(--line);
  background:var(--surface);
  color:var(--ink);
  display:inline-flex;
  align-items:center; justify-content:center;
  font-size:17px;
  cursor:pointer;
  transition:border-color .15s, transform .15s;
}
.icon-btn:hover{ border-color:var(--ink-faint); }
.icon-btn:active{ transform:scale(.93); }
.icon-btn.small{ width:32px; height:32px; font-size:14px; }

/* ---------------- forms ---------------- */
label{
  display:block;
  font-size:12.5px;
  font-weight:600;
  color:var(--ink-soft);
  margin:16px 0 6px;
  text-transform:uppercase;
  letter-spacing:.06em;
}
input[type="email"],
input[type="password"],
input[type="text"],
input[type="date"],
input[type="tel"],
textarea{
  width:100%;
  padding:13px 15px;
  border-radius:var(--r-m);
  border:1.5px solid var(--line);
  background:var(--surface);
  color:var(--ink);
  font-size:15px;
  transition:border-color .15s;
}
input:focus, textarea:focus{ border-color:var(--blue); }
textarea{ resize:vertical; min-height:80px; }
.field-error{
  min-height:18px;
  color:var(--red);
  font-size:12.5px;
  margin-top:6px;
}

/* ============================================================
   AUTH SCREENS
   ============================================================ */
.auth-screen{
  min-height:100vh;
  display:flex;
  flex-wrap:wrap;
}
.auth-art{
  flex:1 1 380px;
  min-height:280px;
  background:var(--canvas-2);
  position:relative;
  overflow:hidden;
  display:flex;
  flex-direction:column;
  align-items:flex-start;
  justify-content:center;
  padding:48px;
}
.brush-mark{
  position:absolute;
  border-radius:50% 45% 55% 40% / 45% 55% 40% 55%;
  filter:blur(1px);
  opacity:.55;
  animation:float 9s ease-in-out infinite;
}
.brush-red{ width:230px; height:170px; background:var(--red); top:-40px; left:-50px; animation-delay:0s; }
.brush-yellow{ width:190px; height:190px; background:var(--yellow); bottom:-60px; left:120px; animation-delay:1.5s; opacity:.5;}
.brush-blue{ width:210px; height:150px; background:var(--blue); bottom:20px; right:-70px; animation-delay:3s; opacity:.45;}
@keyframes float{ 0%,100%{ transform:translateY(0) rotate(0deg); } 50%{ transform:translateY(-14px) rotate(3deg); } }
.auth-art .brand-title, .auth-art .brand-tag{ position:relative; z-index:1; }

.auth-box{
  flex:1 1 380px;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:48px 32px;
}
.auth-box form, .auth-box > .auth-help, .auth-box > h2, .auth-box > .eyebrow, .auth-box > .btn-link{
  width:100%;
  max-width:360px;
}
.auth-box-inner{ width:100%; max-width:360px; }
.auth-box h2{ font-size:26px; margin-bottom:8px; }
.auth-help{ color:var(--ink-soft); font-size:14px; line-height:1.5; margin-bottom:4px; }

@media (max-width:760px){
  .auth-art{ padding:36px 28px; min-height:220px; }
  .brand-title{ font-size:36px; }
}

/* ============================================================
   DASHBOARD
   ============================================================ */
.topbar{
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:18px 24px;
  border-bottom:1px solid var(--line);
  position:sticky; top:0;
  background:var(--canvas);
  z-index:20;
}
.topbar-logo{
  font-family:var(--font-display);
  font-size:20px;
  font-weight:600;
}
.topbar-logo em{
  font-style:italic; font-weight:500;
  background:linear-gradient(92deg, var(--red), var(--yellow) 52%, var(--blue));
  -webkit-background-clip:text; background-clip:text; color:transparent;
}

.settings-panel{
  position:fixed;
  top:70px; right:20px;
  width:270px;
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-l);
  box-shadow:var(--shadow);
  padding:18px;
  z-index:30;
  animation:fadeIn .18s ease;
}
.settings-section{ margin-bottom:16px; }
.settings-label{
  display:block;
  font-size:11px;
  text-transform:uppercase;
  letter-spacing:.08em;
  color:var(--ink-faint);
  margin-bottom:8px;
  font-weight:600;
}
.settings-email{ font-size:13.5px; word-break:break-all; color:var(--ink); }
.theme-toggle{ display:flex; gap:8px; }
.theme-btn{
  flex:1;
  padding:9px 6px;
  border-radius:var(--r-m);
  border:1.5px solid var(--line);
  background:var(--surface-2);
  color:var(--ink);
  cursor:pointer;
  font-size:13px;
}
.theme-btn.active{ border-color:var(--ink); background:var(--ink); color:var(--canvas); }
.account-row{
  display:flex;
  align-items:center;
  gap:10px;
  padding:8px 6px;
  border-radius:var(--r-m);
  cursor:pointer;
  font-size:13px;
}
.account-row:hover{ background:var(--surface-2); }
.account-row.active{ background:var(--surface-2); font-weight:600; }
.account-row .mini-avatar{
  width:26px; height:26px; border-radius:50%;
  background:var(--canvas-2);
  display:flex; align-items:center; justify-content:center;
  font-size:13px; overflow:hidden; flex-shrink:0;
}
.account-row .mini-avatar img{ width:100%; height:100%; object-fit:cover; }
.settings-action{
  display:block;
  width:100%;
  text-align:left;
  background:none;
  border:none;
  padding:10px 6px;
  font-size:13.5px;
  color:var(--ink);
  cursor:pointer;
  border-radius:var(--r-m);
}
.settings-action:hover{ background:var(--surface-2); }
.settings-danger{ color:var(--red); }

.dashboard-main{
  max-width:760px;
  margin:0 auto;
  padding:24px 20px 80px;
}
.profile-card{
  display:flex;
  align-items:center;
  gap:16px;
  padding:18px 4px 22px;
}
.avatar-btn{
  width:68px; height:68px;
  border-radius:50%;
  border:2px dashed var(--line);
  background:var(--surface-2);
  display:flex; align-items:center; justify-content:center;
  overflow:hidden;
  cursor:pointer;
  flex-shrink:0;
  font-size:26px;
}
.avatar-btn:hover{ border-color:var(--ink-faint); }
.avatar-btn img{ width:100%; height:100%; object-fit:cover; }
.profile-info{ flex:1; min-width:0; }
.profile-name-row{ display:flex; align-items:center; gap:8px; }
.profile-name-row h2{ font-size:22px; }
.profile-email{ color:var(--ink-soft); font-size:13px; margin-top:2px; word-break:break-all; }
#form-edit-name{ display:flex; gap:8px; margin-top:4px; }
#form-edit-name input{ padding:8px 12px; font-size:14px; }

.tabs{
  display:flex;
  gap:6px;
  border-bottom:1.5px solid var(--line);
  margin-bottom:22px;
  overflow-x:auto;
}
.tab-btn{
  background:none;
  border:none;
  padding:10px 16px 14px;
  font-size:14.5px;
  font-weight:600;
  color:var(--ink-faint);
  cursor:pointer;
  position:relative;
  white-space:nowrap;
}
.tab-btn.active{ color:var(--ink); }
.tab-btn.active::after{
  content:'';
  position:absolute;
  left:12px; right:12px; bottom:-1.5px;
  height:3px;
  border-radius:2px;
  background:linear-gradient(92deg, var(--red), var(--yellow), var(--blue));
}

.cta-card{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:16px;
  flex-wrap:wrap;
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-l);
  padding:24px;
  margin-bottom:28px;
  box-shadow:var(--shadow-s);
}
.cta-text h3{ font-size:19px; margin-bottom:4px; }
.cta-text p{ font-size:13.5px; color:var(--ink-soft); }

.section-label{
  font-size:12px;
  text-transform:uppercase;
  letter-spacing:.08em;
  color:var(--ink-faint);
  margin:0 0 12px;
  font-weight:700;
}
.empty-msg{ color:var(--ink-faint); font-size:14px; padding:20px 4px; }

.order-list{ display:flex; flex-direction:column; gap:10px; margin-bottom:30px; }
.order-card{
  display:flex;
  gap:14px;
  align-items:flex-start;
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-m);
  padding:14px 16px;
}
.order-thumb{
  width:52px; height:52px;
  border-radius:var(--r-s);
  background:var(--surface-2);
  display:flex; align-items:center; justify-content:center;
  font-size:22px;
  flex-shrink:0;
  overflow:hidden;
}
.order-thumb img{ width:100%; height:100%; object-fit:cover; }
.order-main{ flex:1; min-width:0; }
.order-code{
  font-family:var(--font-mono);
  font-size:11px;
  color:var(--ink-faint);
  letter-spacing:.04em;
}
.order-title{ font-weight:600; font-size:14.5px; margin:2px 0 4px; }
.order-meta{ font-size:12.5px; color:var(--ink-soft); line-height:1.6; }

.style-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill, minmax(150px,1fr));
  gap:12px;
}
.style-card{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-m);
  padding:16px 14px;
  cursor:pointer;
  text-align:left;
  transition:transform .15s, border-color .15s;
}
.style-card:hover{ transform:translateY(-2px); border-color:var(--ink-faint); }
.style-card .style-icon{ font-size:24px; display:block; margin-bottom:8px; }
.style-card strong{ display:block; font-size:14px; margin-bottom:3px; }
.style-card span{ font-size:12px; color:var(--ink-soft); }

@media (max-width:600px){
  .cta-card{ flex-direction:column; align-items:stretch; text-align:left; }
  .btn-cta{ width:100%; }
}

/* ============================================================
   WIZARD
   ============================================================ */
#screen-wizard{
  min-height:100vh;
  display:flex;
  flex-direction:column;
  background:var(--canvas);
}
.wizard-header{
  display:flex;
  align-items:center;
  gap:16px;
  padding:16px 20px;
  border-bottom:1px solid var(--line);
  position:sticky; top:0;
  background:var(--canvas);
  z-index:10;
}
.wizard-progress{
  display:flex;
  align-items:center;
  flex:1;
  justify-content:center;
  gap:0;
}
.wp-step{
  width:28px; height:28px;
  border-radius:50%;
  border:1.5px solid var(--line);
  display:flex; align-items:center; justify-content:center;
  font-size:12px;
  font-family:var(--font-mono);
  color:var(--ink-faint);
  background:var(--surface);
  flex-shrink:0;
}
.wp-step.active{ border-color:var(--ink); color:var(--ink); font-weight:600; }
.wp-step.done{ background:var(--ink); border-color:var(--ink); color:var(--canvas); }
.wp-line{ width:18px; height:1.5px; background:var(--line); flex-shrink:0; }
.wp-line.done{ background:var(--ink); }

.wizard-body{
  flex:1;
  max-width:560px;
  width:100%;
  margin:0 auto;
  padding:32px 20px 40px;
}
.wizard-step h2{ font-size:24px; margin-bottom:8px; }
.wizard-step .auth-help{ margin-bottom:20px; }

.upload-box{
  display:flex;
  align-items:center;
  justify-content:center;
  min-height:130px;
  border:2px dashed var(--line);
  border-radius:var(--r-l);
  cursor:pointer;
  text-align:center;
  padding:20px;
  color:var(--ink-soft);
  font-size:14px;
  background:var(--surface-2);
  transition:border-color .15s;
  overflow:hidden;
}
.upload-box:hover{ border-color:var(--ink-faint); }
.upload-box img{ max-height:180px; border-radius:var(--r-m); }

.or-divider{
  text-align:center;
  font-size:12px;
  color:var(--ink-faint);
  text-transform:uppercase;
  letter-spacing:.08em;
  margin:22px 0 14px;
  position:relative;
}
.or-divider::before, .or-divider::after{
  content:'';
  position:absolute;
  top:50%; width:38%;
  height:1px;
  background:var(--line);
}
.or-divider::before{ left:0; }
.or-divider::after{ right:0; }

.style-chip-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill, minmax(128px,1fr));
  gap:8px;
}
.style-chip{
  display:flex;
  flex-direction:column;
  gap:4px;
  padding:10px 12px;
  border-radius:var(--r-m);
  border:1.5px solid var(--line);
  background:var(--surface);
  cursor:pointer;
  font-size:12.5px;
  text-align:left;
  color:var(--ink);
}
.style-chip .chip-icon{ font-size:17px; }
.style-chip.active{ border-color:var(--ink); background:var(--surface-2); font-weight:600; }

.option-cards{
  display:grid;
  grid-template-columns:repeat(auto-fit, minmax(150px,1fr));
  gap:12px;
}
.option-card{
  display:flex;
  flex-direction:column;
  gap:6px;
  align-items:flex-start;
  padding:18px 16px;
  border-radius:var(--r-l);
  border:1.5px solid var(--line);
  background:var(--surface);
  cursor:pointer;
  font-size:13.5px;
  color:var(--ink);
  text-align:left;
}
.option-card strong{ font-size:15px; }
.option-card.active{ border-color:var(--ink); background:var(--surface-2); box-shadow:var(--shadow-s); }
.option-swatch{ width:26px; height:26px; border-radius:50%; display:block; }
.size-swatch-p{ background:var(--red); width:16px; height:16px; }
.size-swatch-m{ background:var(--yellow); width:22px; height:22px; }
.size-swatch-g{ background:var(--blue); width:30px; height:30px; }

.calendar{
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-l);
  padding:16px;
}
.calendar-header{
  display:flex; align-items:center; justify-content:space-between;
  margin-bottom:10px;
  font-weight:600; font-size:14px;
}
.calendar-weekdays{
  display:grid; grid-template-columns:repeat(7,1fr);
  font-size:11px; color:var(--ink-faint); text-align:center;
  margin-bottom:6px;
}
.calendar-grid{
  display:grid; grid-template-columns:repeat(7,1fr);
  gap:4px;
}
.cal-day{
  aspect-ratio:1;
  display:flex; align-items:center; justify-content:center;
  border-radius:50%;
  font-size:13px;
  border:none;
  background:transparent;
  color:var(--ink);
  cursor:pointer;
}
.cal-day:hover:not(:disabled){ background:var(--surface-2); }
.cal-day:disabled{ color:var(--ink-faint); opacity:.35; cursor:default; }
.cal-day.selected{ background:var(--ink); color:var(--canvas); font-weight:600; }
.cal-day.empty{ visibility:hidden; }
.selected-date{ margin-top:14px; font-size:13.5px; color:var(--ink-soft); }

.summary-card{
  margin-top:26px;
  background:var(--surface);
  border:1px solid var(--line);
  border-radius:var(--r-l);
  padding:18px 20px;
  font-size:13.5px;
  line-height:2;
}
.summary-card b{ color:var(--ink-faint); font-weight:600; font-size:11px; text-transform:uppercase; letter-spacing:.06em; display:inline-block; width:120px; }

.wizard-footer{
  display:flex;
  gap:12px;
  justify-content:flex-end;
  padding:18px 20px;
  border-top:1px solid var(--line);
  position:sticky; bottom:0;
  background:var(--canvas);
}
@media (max-width:520px){
  .wp-line{ width:9px; }
  .wizard-footer{ flex-direction:row-reverse; }
  .wizard-footer .btn{ flex:1; }
}

/* ============================================================
   OVERLAY DE CONFIRMAÇÃO
   ============================================================ */
#overlay-confirm{
  position:fixed; inset:0;
  background:#17130F;
  display:flex;
  align-items:center;
  justify-content:center;
  z-index:100;
  opacity:0;
  transition:opacity .35s ease;
}
#overlay-confirm.visible{ opacity:1; }
.overlay-inner{
  max-width:600px;
  padding:32px;
  text-align:center;
}
.overlay-quote{
  font-family:var(--font-display);
  font-style:italic;
  font-weight:500;
  font-size:clamp(22px,4.2vw,34px);
  line-height:1.35;
  color:#F4EEE2;
  margin-bottom:22px;
  background:linear-gradient(92deg, var(--red), var(--yellow) 50%, var(--blue));
  -webkit-background-clip:text; background-clip:text; -webkit-text-fill-color:transparent;
}
.overlay-caption{
  font-family:var(--font-mono);
  font-size:12px;
  letter-spacing:.1em;
  text-transform:uppercase;
  color:#8A7D68;
}
.dots span{ display:inline-block; animation:dotBlink 1.3s infinite; }
.dots span:nth-child(2){ animation-delay:.2s; }
.dots span:nth-child(3){ animation-delay:.4s; }
@keyframes dotBlink{ 0%,80%,100%{ opacity:.15; } 40%{ opacity:1; } }
@keyframes fadeIn{ from{ opacity:0; transform:translateY(4px); } to{ opacity:1; transform:translateY(0); } }

/* ============================================================
   MODAL
   ============================================================ */
.modal{
  position:fixed; inset:0;
  background:rgba(23,19,15,.55);
  display:flex; align-items:center; justify-content:center;
  z-index:90;
  padding:20px;
}
.modal-box{
  background:var(--surface);
  border-radius:var(--r-l);
  padding:26px;
  max-width:360px;
  width:100%;
  box-shadow:var(--shadow);
  animation:fadeIn .2s ease;
}
.modal-box h3{ font-size:19px; margin-bottom:10px; }
.modal-box p{ font-size:13.5px; color:var(--ink-soft); line-height:1.6; margin-bottom:20px; }
.modal-actions{ display:flex; gap:10px; justify-content:flex-end; }
</style>
</head>
<body>
<div id="app">

  <!-- ============ AUTH: E-MAIL ============ -->
  <section id="screen-welcome" class="auth-screen">
    <div class="auth-art">
      <span class="brush-mark brush-red"></span>
      <span class="brush-mark brush-yellow"></span>
      <span class="brush-mark brush-blue"></span>
      <h1 class="brand-title">Entre<br><em>tintas</em></h1>
      <p class="brand-tag">Agendamento do acervo de arte da Laila</p>
    </div>
    <div class="auth-box">
      <div class="auth-box-inner">
        <span class="eyebrow">Passo 1 de 4</span>
        <h2>Entrar</h2>
        <p class="auth-help">Use o e-mail da sua conta Google para manter seu histórico salvo neste site.</p>
        <form id="form-welcome" novalidate>
          <label for="input-email">E-mail do Google</label>
          <input type="email" id="input-email" placeholder="voce@gmail.com" required>
          <p class="field-error" id="error-email"></p>
          <button type="submit" class="btn btn-primary btn-block">Continuar com Google</button>
        </form>
      </div>
    </div>
  </section>

  <!-- ============ AUTH: SENHA ============ -->
  <section id="screen-password" class="auth-screen hidden">
    <div class="auth-art">
      <span class="brush-mark brush-red"></span>
      <span class="brush-mark brush-yellow"></span>
      <span class="brush-mark brush-blue"></span>
      <h1 class="brand-title">Entre<br><em>tintas</em></h1>
      <p class="brand-tag">Agendamento do acervo de arte da Laila</p>
    </div>
    <div class="auth-box">
      <div class="auth-box-inner">
        <span class="eyebrow" id="password-eyebrow">Passo 2 de 4</span>
        <h2 id="password-title">Criar senha</h2>
        <p class="auth-help" id="password-help">Escolha uma senha de 6 a 20 caracteres.</p>
        <form id="form-password" novalidate>
          <label for="input-password">Senha</label>
          <input type="password" id="input-password" minlength="6" maxlength="20" required>
          <p class="field-error" id="error-password"></p>
          <button type="submit" class="btn btn-primary btn-block" id="password-submit">Continuar</button>
        </form>
        <button class="btn-link" id="btn-back-welcome">← usar outro e-mail</button>
      </div>
    </div>
  </section>

  <!-- ============ AUTH: NASCIMENTO ============ -->
  <section id="screen-birthdate" class="auth-screen hidden">
    <div class="auth-art">
      <span class="brush-mark brush-red"></span>
      <span class="brush-mark brush-yellow"></span>
      <span class="brush-mark brush-blue"></span>
      <h1 class="brand-title">Entre<br><em>tintas</em></h1>
      <p class="brand-tag">Agendamento do acervo de arte da Laila</p>
    </div>
    <div class="auth-box">
      <div class="auth-box-inner">
        <span class="eyebrow">Passo 3 de 4</span>
        <h2>Sua data de nascimento</h2>
        <p class="auth-help">É só para confirmarmos que é você.</p>
        <form id="form-birthdate" novalidate>
          <label for="input-birthdate">Data de nascimento</label>
          <input type="date" id="input-birthdate" required>
          <p class="field-error" id="error-birthdate"></p>
          <button type="submit" class="btn btn-primary btn-block">Continuar</button>
        </form>
      </div>
    </div>
  </section>

  <!-- ============ AUTH: NOME ============ -->
  <section id="screen-name" class="auth-screen hidden">
    <div class="auth-art">
      <span class="brush-mark brush-red"></span>
      <span class="brush-mark brush-yellow"></span>
      <span class="brush-mark brush-blue"></span>
      <h1 class="brand-title">Entre<br><em>tintas</em></h1>
      <p class="brand-tag">Agendamento do acervo de arte da Laila</p>
    </div>
    <div class="auth-box">
      <div class="auth-box-inner">
        <span class="eyebrow">Passo 4 de 4</span>
        <h2>Como você quer ser chamada?</h2>
        <p class="auth-help">É assim que vamos te chamar por aqui.</p>
        <form id="form-name" novalidate>
          <label for="input-name">Seu nome</label>
          <input type="text" id="input-name" maxlength="40" required>
          <p class="field-error" id="error-name"></p>
          <button type="submit" class="btn btn-primary btn-block">Entrar no site</button>
        </form>
      </div>
    </div>
  </section>

  <!-- ============ DASHBOARD ============ -->
  <div id="screen-dashboard" class="hidden">
    <header class="topbar">
      <div class="topbar-logo">Entre <em>tintas</em></div>
      <button class="icon-btn" id="btn-settings" aria-label="Configurações">⚙</button>
    </header>

    <div id="settings-panel" class="settings-panel hidden">
      <div class="settings-section">
        <span class="settings-label">Aparência</span>
        <div class="theme-toggle">
          <button class="theme-btn" id="btn-theme-light">☀ Claro</button>
          <button class="theme-btn" id="btn-theme-dark">☾ Escuro</button>
        </div>
      </div>
      <div class="settings-section">
        <span class="settings-label">Conectado como</span>
        <p class="settings-email" id="settings-active-email"></p>
      </div>
      <div class="settings-section">
        <span class="settings-label">Contas neste dispositivo</span>
        <div id="settings-accounts-list"></div>
      </div>
      <button class="settings-action" id="btn-add-account">+ Adicionar conta</button>
      <button class="settings-action" id="btn-logout">Sair</button>
      <button class="settings-action settings-danger" id="btn-delete-account">Excluir conta</button>
    </div>

    <main class="dashboard-main">
      <section class="profile-card">
        <button class="avatar-btn" id="btn-avatar" aria-label="Alterar foto de perfil">
          <img id="avatar-img" class="hidden" alt="Foto de perfil">
          <span id="avatar-fallback">🎨</span>
        </button>
        <div class="profile-info">
          <div class="profile-name-row" id="profile-name-row">
            <h2 id="profile-name-display"></h2>
            <button class="icon-btn small" id="btn-edit-name" aria-label="Editar nome">✎</button>
          </div>
          <form id="form-edit-name" class="hidden">
            <input type="text" id="input-edit-name" maxlength="40">
            <button type="submit" class="btn-small">Salvar</button>
          </form>
          <p class="profile-email" id="profile-email-display"></p>
        </div>
      </section>

      <nav class="tabs">
        <button class="tab-btn active" data-tab="inicio">Início</button>
        <button class="tab-btn" data-tab="historico">Histórico</button>
        <button class="tab-btn" data-tab="inspiracoes">Inspirações</button>
      </nav>

      <div id="tab-inicio" class="tab-panel">
        <div class="cta-card">
          <div class="cta-text">
            <h3>Vamos criar seu quadro?</h3>
            <p>Atendimento todos os dias, das 8h às 17h.</p>
          </div>
          <button class="btn btn-primary btn-cta" id="btn-fazer-pedido">Fazer pedido</button>
        </div>
        <p class="section-label">Pedidos recentes</p>
        <div id="lista-recentes" class="order-list"></div>
        <p id="msg-sem-pedidos" class="empty-msg hidden">Você ainda não fez nenhum pedido.</p>
      </div>

      <div id="tab-historico" class="tab-panel hidden">
        <p class="section-label">Todos os seus pedidos</p>
        <div id="lista-historico" class="order-list"></div>
        <p id="msg-sem-historico" class="empty-msg hidden">Nada por aqui ainda.</p>
      </div>

      <div id="tab-inspiracoes" class="tab-panel hidden">
        <p class="section-label">Inspirações de estilo</p>
        <div id="grid-inspiracoes" class="style-grid"></div>
      </div>
    </main>
  </div>

  <!-- ============ WIZARD DE PEDIDO ============ -->
  <div id="screen-wizard" class="hidden">
    <header class="wizard-header">
      <button class="icon-btn" id="btn-close-wizard" aria-label="Fechar">✕</button>
      <div class="wizard-progress" id="wizard-progress">
        <span class="wp-step" data-step="1">1</span>
        <span class="wp-line" data-line="1"></span>
        <span class="wp-step" data-step="2">2</span>
        <span class="wp-line" data-line="2"></span>
        <span class="wp-step" data-step="3">3</span>
        <span class="wp-line" data-line="3"></span>
        <span class="wp-step" data-step="4">4</span>
        <span class="wp-line" data-line="4"></span>
        <span class="wp-step" data-step="5">5</span>
      </div>
      <span style="width:40px"></span>
    </header>

    <div class="wizard-body">
      <div id="wizard-step-1" class="wizard-step">
        <span class="eyebrow">Etapa 1</span>
        <h2>Qual é a ideia do seu quadro?</h2>
        <p class="auth-help">Anexe uma imagem de referência, ou explore as opções abaixo se ainda não tiver certeza.</p>

        <label class="upload-box" id="upload-box">
          <input type="file" id="file-order-image" accept="image/*" hidden>
          <span id="upload-placeholder">📎 Toque para anexar uma imagem do seu dispositivo</span>
          <img id="upload-preview" class="hidden" alt="Pré-visualização da imagem enviada">
        </label>

        <p class="or-divider">ou escolha um estilo</p>
        <div class="style-chip-grid" id="style-chip-grid"></div>

        <p class="or-divider">ou descreva o que você imagina</p>
        <textarea id="input-description" maxlength="500" rows="3" placeholder="Ex: um retrato da minha cachorra, em tons pastel..."></textarea>

        <p class="field-error" id="error-step1"></p>
      </div>

      <div id="wizard-step-2" class="wizard-step hidden">
        <span class="eyebrow">Etapa 2</span>
        <h2>Tamanho do quadro</h2>
        <p class="auth-help">Selecione o tamanho que combina com o seu espaço.</p>
        <div class="option-cards" id="size-cards">
          <button type="button" class="option-card" data-size="pequeno" data-size-label="Pequeno (até 40cm)">
            <span class="option-swatch size-swatch-p"></span>
            <strong>Pequeno</strong>
            <span>Até 40 centímetros</span>
          </button>
          <button type="button" class="option-card" data-size="medio" data-size-label="Médio (até 60cm)">
            <span class="option-swatch size-swatch-m"></span>
            <strong>Médio</strong>
            <span>Até 60 centímetros</span>
          </button>
          <button type="button" class="option-card" data-size="grande" data-size-label="Grande (até 1m)">
            <span class="option-swatch size-swatch-g"></span>
            <strong>Grande</strong>
            <span>Até 1 metro</span>
          </button>
        </div>
        <p class="field-error" id="error-step2"></p>
      </div>

      <div id="wizard-step-3" class="wizard-step hidden">
        <span class="eyebrow">Etapa 3</span>
        <h2>Para quem é o quadro?</h2>
        <div class="option-cards" id="purpose-cards">
          <button type="button" class="option-card" data-purpose="Presente">
            <span style="font-size:22px">🎁</span><strong>Presente</strong>
          </button>
          <button type="button" class="option-card" data-purpose="Pra mim">
            <span style="font-size:22px">🖼️</span><strong>Pra mim</strong>
          </button>
          <button type="button" class="option-card" data-purpose="Trabalho de escola">
            <span style="font-size:22px">🎒</span><strong>Trabalho de escola</strong>
          </button>
        </div>
        <p class="field-error" id="error-step3"></p>
      </div>

      <div id="wizard-step-4" class="wizard-step hidden">
        <span class="eyebrow">Etapa 4</span>
        <h2>Quando você quer receber?</h2>
        <p class="auth-help">Aberto todos os dias, das 8h às 17h.</p>
        <div class="calendar">
          <div class="calendar-header">
            <button type="button" class="icon-btn small" id="cal-prev" aria-label="Mês anterior">←</button>
            <span id="cal-month-label"></span>
            <button type="button" class="icon-btn small" id="cal-next" aria-label="Próximo mês">→</button>
          </div>
          <div class="calendar-weekdays">
            <span>D</span><span>S</span><span>T</span><span>Q</span><span>Q</span><span>S</span><span>S</span>
          </div>
          <div class="calendar-grid" id="calendar-grid"></div>
        </div>
        <p class="selected-date" id="selected-date-label"></p>
        <p class="field-error" id="error-step4"></p>
      </div>

      <div id="wizard-step-5" class="wizard-step hidden">
        <span class="eyebrow">Etapa 5</span>
        <h2>Últimos detalhes</h2>
        <label for="input-whatsapp">Seu WhatsApp</label>
        <input type="tel" id="input-whatsapp" placeholder="(71) 9xxxx-xxxx">
        <p class="field-error" id="error-step5"></p>

        <div class="summary-card" id="summary-card"></div>
      </div>
    </div>

    <footer class="wizard-footer">
      <button class="btn btn-ghost" id="btn-wizard-back">Voltar</button>
      <button class="btn btn-primary" id="btn-wizard-next">Continuar</button>
    </footer>
  </div>

  <!-- ============ OVERLAY DE ENVIO ============ -->
  <div id="overlay-confirm" class="hidden">
    <div class="overlay-inner">
      <p class="overlay-quote" id="overlay-quote"></p>
      <p class="overlay-caption">enviando pedido<span class="dots"><span>.</span><span>.</span><span>.</span></span></p>
    </div>
  </div>

  <!-- ============ MODAL EXCLUIR CONTA ============ -->
  <div id="modal-delete" class="modal hidden">
    <div class="modal-box">
      <h3>Excluir conta?</h3>
      <p>Isso vai apagar seu perfil e todo o histórico de pedidos deste dispositivo. Essa ação não pode ser desfeita.</p>
      <div class="modal-actions">
        <button class="btn btn-ghost" id="btn-cancel-delete">Cancelar</button>
        <button class="btn btn-danger" id="btn-confirm-delete">Excluir conta</button>
      </div>
    </div>
  </div>

</div>

<input type="file" id="file-avatar" accept="image/*" hidden>

<script>
(function(){
'use strict';

/* ============================================================
   CONSTANTES
   ============================================================ */
var STORAGE_ACCOUNTS = 'et_accounts';
var STORAGE_ACTIVE   = 'et_active_email';
var STORAGE_COUNTER  = 'et_order_counter';
var STORAGE_THEME    = 'et_theme';
var WHATSAPP_LAILA   = '557193433296';

var STYLES = [
  { id:'realista',    nome:'Realista',    desc:'Detalhes fiéis à realidade',        icon:'🖌️' },
  { id:'aquarela',     nome:'Aquarela',     desc:'Traços suaves e translúcidos',      icon:'💧' },
  { id:'minimalista',  nome:'Minimalista',  desc:'Poucas linhas, muito significado',  icon:'▫️' },
  { id:'abstrato',     nome:'Abstrato',     desc:'Formas e cores livres',             icon:'🎨' },
  { id:'popart',       nome:'Pop Art',      desc:'Cores vibrantes e contornos fortes',icon:'💥' },
  { id:'lineart',      nome:'Line Art',     desc:'Uma linha só, do início ao fim',    icon:'✏️' },
  { id:'vintage',      nome:'Vintage',      desc:'Ares de retrô e nostalgia',         icon:'📻' },
  { id:'cartoon',      nome:'Cartoon',      desc:'Traços divertidos e exagerados',    icon:'😄' },
  { id:'surrealista',  nome:'Surrealista',  desc:'Onde o impossível vira imagem',     icon:'🌙' },
  { id:'geometrico',   nome:'Geométrico',   desc:'Formas exatas, composição precisa', icon:'🔺' }
];

var FRASES = [
  "O que traz beleza a obra não é o artista e sim a inspiração.",
  "Viver requer um estado artístico.",
  "Nos olhos certos, você sempre será arte.",
  "Todo artista é meio desequilibrado.",
  "Não sufoque o artista.",
  "Desperdiçar um talento é recusar um presente.",
  "Porque amar é uma arte e nem todo mundo é artista.",
  "Ué, mas você só trabalha com arte?",
  "A arte não é o que você vê mas o que você faz os outros verem.",
  "Algumas pessoas são artistas. Outras, por si só são obras de arte!",
  "Artistas pintam para você.",
  "Existir é sua maior arte.",
  "Por onde for mostre suas cores.",
  "Você é feito de arte."
];

/* ============================================================
   ESTADO
   ============================================================ */
var accounts = loadAccounts();
var activeEmail = localStorage.getItem(STORAGE_ACTIVE) || null;
var authFlow = { mode:null, email:null, password:null, birthdate:null };
var lastFraseIndex = -1;
var calendarView = { year:null, month:null };

var wizard = novoEstadoWizard();
function novoEstadoWizard(){
  return {
    step:1,
    imageDataUrl:null,
    styleId:null,
    styleName:null,
    description:'',
    size:null,
    sizeLabel:null,
    purpose:null,
    date:null,
    dateLabel:null,
    whatsapp:''
  };
}

/* ============================================================
   HELPERS
   ============================================================ */
function $(id){ return document.getElementById(id); }
function show(el){ if(el) el.classList.remove('hidden'); }
function hide(el){ if(el) el.classList.add('hidden'); }

function loadAccounts(){
  try{
    var raw = localStorage.getItem(STORAGE_ACCOUNTS);
    return raw ? JSON.parse(raw) : {};
  }catch(e){ return {}; }
}
function saveAccounts(){
  try{ localStorage.setItem(STORAGE_ACCOUNTS, JSON.stringify(accounts)); }
  catch(e){ alert('Não foi possível salvar seus dados neste dispositivo (armazenamento cheio ou bloqueado).'); }
}
function setActive(email){
  activeEmail = email;
  if(email) localStorage.setItem(STORAGE_ACTIVE, email);
  else localStorage.removeItem(STORAGE_ACTIVE);
}
function nextOrderCode(){
  var n = parseInt(localStorage.getItem(STORAGE_COUNTER) || '0', 10) + 1;
  localStorage.setItem(STORAGE_COUNTER, String(n));
  return String(n).padStart(6,'0');
}
function formatDateTime(d){
  var dd=String(d.getDate()).padStart(2,'0'), mm=String(d.getMonth()+1).padStart(2,'0'), yyyy=d.getFullYear();
  var hh=String(d.getHours()).padStart(2,'0'), min=String(d.getMinutes()).padStart(2,'0');
  return dd+'/'+mm+'/'+yyyy+' às '+hh+':'+min;
}
function isValidEmail(v){
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v);
}
function isGoogleEmail(v){
  return /@(gmail\.com|googlemail\.com)$/i.test(v);
}
function escapeHtml(s){
  var d = document.createElement('div');
  d.textContent = s == null ? '' : s;
  return d.innerHTML;
}

/* Reduz uma imagem enviada pelo usuário antes de guardar no localStorage */
function downscaleImage(file, maxDim, callback){
  var reader = new FileReader();
  reader.onload = function(e){
    var img = new Image();
    img.onload = function(){
      var w = img.width, h = img.height;
      if(w > maxDim || h > maxDim){
        if(w > h){ h = Math.round(h * (maxDim / w)); w = maxDim; }
        else { w = Math.round(w * (maxDim / h)); h = maxDim; }
      }
      var canvas = document.createElement('canvas');
      canvas.width = w; canvas.height = h;
      var ctx = canvas.getContext('2d');
      ctx.drawImage(img, 0, 0, w, h);
      callback(canvas.toDataURL('image/jpeg', 0.82));
    };
    img.onerror = function(){ callback(null); };
    img.src = e.target.result;
  };
  reader.onerror = function(){ callback(null); };
  reader.readAsDataURL(file);
}

/* ============================================================
   NAVEGAÇÃO DE TELAS
   ============================================================ */
var SCREENS = ['screen-welcome','screen-password','screen-birthdate','screen-name','screen-dashboard','screen-wizard'];
function showScreen(id){
  SCREENS.forEach(function(s){
    var el = $(s);
    if(!el) return;
    if(s === id) show(el); else hide(el);
  });
  window.scrollTo(0,0);
}

/* ============================================================
   FLUXO DE LOGIN / CADASTRO
   ============================================================ */
function resetAuthForms(){
  $('input-email').value = '';
  $('input-password').value = '';
  $('input-birthdate').value = '';
  $('input-name').value = '';
  $('error-email').textContent = '';
  $('error-password').textContent = '';
  $('error-birthdate').textContent = '';
  $('error-name').textContent = '';
}

$('form-welcome').addEventListener('submit', function(ev){
  ev.preventDefault();
  var email = $('input-email').value.trim().toLowerCase();
  $('error-email').textContent = '';
  if(!isValidEmail(email)){
    $('error-email').textContent = 'Digite um e-mail válido.';
    return;
  }
  if(!isGoogleEmail(email)){
    $('error-email').textContent = 'Use um e-mail do Google (@gmail.com).';
    return;
  }
  authFlow.email = email;
  if(accounts[email]){
    authFlow.mode = 'login';
    $('password-eyebrow').textContent = 'Passo 2 de 2';
    $('password-title').textContent = 'Bem-vinda de volta';
    $('password-help').textContent = 'Digite sua senha para continuar.';
    $('password-submit').textContent = 'Entrar';
  } else {
    authFlow.mode = 'register';
    $('password-eyebrow').textContent = 'Passo 2 de 4';
    $('password-title').textContent = 'Criar senha';
    $('password-help').textContent = 'Escolha uma senha de 6 a 20 caracteres.';
    $('password-submit').textContent = 'Continuar';
  }
  $('input-password').value = '';
  $('error-password').textContent = '';
  showScreen('screen-password');
  $('input-password').focus();
});

$('btn-back-welcome').addEventListener('click', function(){
  showScreen('screen-welcome');
});

$('form-password').addEventListener('submit', function(ev){
  ev.preventDefault();
  var pw = $('input-password').value;
  $('error-password').textContent = '';

  if(authFlow.mode === 'login'){
    var acc = accounts[authFlow.email];
    if(acc && acc.password === pw){
      setActive(authFlow.email);
      renderDashboard();
      showScreen('screen-dashboard');
    } else {
      $('error-password').textContent = 'Senha incorreta. Tente novamente.';
    }
    return;
  }

  // modo registro
  if(pw.length < 6 || pw.length > 20){
    $('error-password').textContent = 'A senha precisa ter entre 6 e 20 caracteres.';
    return;
  }
  authFlow.password = pw;
  $('input-birthdate').value = '';
  $('error-birthdate').textContent = '';
  showScreen('screen-birthdate');
});

$('form-birthdate').addEventListener('submit', function(ev){
  ev.preventDefault();
  var val = $('input-birthdate').value;
  $('error-birthdate').textContent = '';
  if(!val){
    $('error-birthdate').textContent = 'Informe sua data de nascimento.';
    return;
  }
  if(new Date(val) > new Date()){
    $('error-birthdate').textContent = 'Data inválida.';
    return;
  }
  authFlow.birthdate = val;
  $('input-name').value = '';
  $('error-name').textContent = '';
  showScreen('screen-name');
});

$('form-name').addEventListener('submit', function(ev){
  ev.preventDefault();
  var nome = $('input-name').value.trim();
  $('error-name').textContent = '';
  if(!nome){
    $('error-name').textContent = 'Diga como podemos te chamar.';
    return;
  }
  accounts[authFlow.email] = {
    email: authFlow.email,
    password: authFlow.password,
    birthdate: authFlow.birthdate,
    name: nome,
    photo: null,
    orders: []
  };
  saveAccounts();
  setActive(authFlow.email);
  resetAuthForms();
  renderDashboard();
  showScreen('screen-dashboard');
});

/* ============================================================
   DASHBOARD
   ============================================================ */
function renderDashboard(){
  var acc = accounts[activeEmail];
  if(!acc) return;

  $('profile-name-display').textContent = acc.name;
  $('profile-email-display').textContent = acc.email;
  $('settings-active-email').textContent = acc.email;

  if(acc.photo){
    $('avatar-img').src = acc.photo;
    show($('avatar-img'));
    hide($('avatar-fallback'));
  } else {
    hide($('avatar-img'));
    show($('avatar-fallback'));
  }

  renderAccountsList();
  renderOrders();
  renderInspiracoes();
}

function renderAccountsList(){
  var wrap = $('settings-accounts-list');
  wrap.innerHTML = '';
  Object.keys(accounts).forEach(function(email){
    var acc = accounts[email];
    var row = document.createElement('div');
    row.className = 'account-row' + (email === activeEmail ? ' active' : '');
    var avatarHtml = acc.photo ? '<img src="'+acc.photo+'" alt="">' : '🎨';
    row.innerHTML = '<span class="mini-avatar">'+avatarHtml+'</span><span>'+escapeHtml(acc.name)+'</span>';
    row.addEventListener('click', function(){
      setActive(email);
      renderDashboard();
      hide($('settings-panel'));
    });
    wrap.appendChild(row);
  });
}

document.querySelectorAll('.tab-btn').forEach(function(btn){
  btn.addEventListener('click', function(){ activateTab(btn.dataset.tab); });
});
function activateTab(tab){
  document.querySelectorAll('.tab-btn').forEach(function(b){
    b.classList.toggle('active', b.dataset.tab === tab);
  });
  ['inicio','historico','inspiracoes'].forEach(function(t){
    var panel = $('tab-'+t);
    if(t === tab) show(panel); else hide(panel);
  });
}

/* --- tema --- */
function applyTheme(theme){
  document.documentElement.setAttribute('data-theme', theme);
  localStorage.setItem(STORAGE_THEME, theme);
  $('btn-theme-light').classList.toggle('active', theme === 'light');
  $('btn-theme-dark').classList.toggle('active', theme === 'dark');
}
$('btn-theme-light').addEventListener('click', function(){ applyTheme('light'); });
$('btn-theme-dark').addEventListener('click', function(){ applyTheme('dark'); });

/* --- painel de configurações --- */
$('btn-settings').addEventListener('click', function(ev){
  ev.stopPropagation();
  $('settings-panel').classList.toggle('hidden');
});
document.addEventListener('click', function(ev){
  var panel = $('settings-panel');
  if(panel.classList.contains('hidden')) return;
  if(panel.contains(ev.target) || ev.target === $('btn-settings')) return;
  hide(panel);
});

$('btn-add-account').addEventListener('click', function(){
  hide($('settings-panel'));
  resetAuthForms();
  showScreen('screen-welcome');
});
$('btn-logout').addEventListener('click', function(){
  hide($('settings-panel'));
  setActive(null);
  resetAuthForms();
  showScreen('screen-welcome');
});
$('btn-delete-account').addEventListener('click', function(){
  hide($('settings-panel'));
  show($('modal-delete'));
});
$('btn-cancel-delete').addEventListener('click', function(){ hide($('modal-delete')); });
$('btn-confirm-delete').addEventListener('click', function(){
  delete accounts[activeEmail];
  saveAccounts();
  setActive(null);
  hide($('modal-delete'));
  resetAuthForms();
  showScreen('screen-welcome');
});

/* --- perfil: nome e foto --- */
$('btn-edit-name').addEventListener('click', function(){
  $('input-edit-name').value = accounts[activeEmail].name;
  hide($('profile-name-row'));
  show($('form-edit-name'));
  $('input-edit-name').focus();
});
$('form-edit-name').addEventListener('submit', function(ev){
  ev.preventDefault();
  var val = $('input-edit-name').value.trim();
  if(!val) return;
  accounts[activeEmail].name = val;
  saveAccounts();
  hide($('form-edit-name'));
  show($('profile-name-row'));
  renderDashboard();
});

$('btn-avatar').addEventListener('click', function(){ $('file-avatar').click(); });
$('file-avatar').addEventListener('change', function(ev){
  var file = ev.target.files[0];
  if(!file) return;
  downscaleImage(file, 320, function(dataUrl){
    if(!dataUrl) return;
    accounts[activeEmail].photo = dataUrl;
    saveAccounts();
    renderDashboard();
  });
  ev.target.value = '';
});

/* --- pedidos: renderização --- */
function renderOrders(){
  var acc = accounts[activeEmail];
  var orders = acc.orders || [];

  renderOrderList($('lista-recentes'), orders.slice(0,3));
  if(orders.length === 0){ show($('msg-sem-pedidos')); } else { hide($('msg-sem-pedidos')); }

  renderOrderList($('lista-historico'), orders);
  if(orders.length === 0){ show($('msg-sem-historico')); } else { hide($('msg-sem-historico')); }
}
function renderOrderList(container, list){
  container.innerHTML = '';
  list.forEach(function(o){ container.appendChild(buildOrderCard(o)); });
}
function buildOrderCard(o){
  var card = document.createElement('div');
  card.className = 'order-card';

  var thumb = document.createElement('div');
  thumb.className = 'order-thumb';
  if(o.imageDataUrl){
    thumb.innerHTML = '<img src="'+o.imageDataUrl+'" alt="">';
  } else {
    var styleInfo = STYLES.find(function(s){ return s.id === o.styleId; });
    thumb.textContent = styleInfo ? styleInfo.icon : '🖼️';
  }
  card.appendChild(thumb);

  var main = document.createElement('div');
  main.className = 'order-main';
  var titulo = o.styleName || (o.description ? 'Descrição personalizada' : 'Pedido');
  main.innerHTML =
    '<div class="order-code">#'+o.code+'</div>' +
    '<div class="order-title">'+escapeHtml(titulo)+'</div>' +
    '<div class="order-meta">' +
      'Tamanho: '+escapeHtml(o.sizeLabel)+'<br>' +
      'Para: '+escapeHtml(o.purpose)+'<br>' +
      'Data desejada: '+escapeHtml(o.dateLabel)+'<br>' +
      'Enviado em '+escapeHtml(o.submittedAtLabel) +
    '</div>';
  card.appendChild(main);
  return card;
}

/* --- inspirações --- */
function renderInspiracoes(){
  var grid = $('grid-inspiracoes');
  grid.innerHTML = '';
  STYLES.forEach(function(s){
    var card = document.createElement('button');
    card.type = 'button';
    card.className = 'style-card';
    card.innerHTML = '<span class="style-icon">'+s.icon+'</span><strong>'+s.nome+'</strong><span>'+s.desc+'</span>';
    card.addEventListener('click', function(){
      openWizard(s.id);
    });
    grid.appendChild(card);
  });
}

/* ============================================================
   WIZARD DE PEDIDO
   ============================================================ */
function renderStyleChips(){
  var grid = $('style-chip-grid');
  grid.innerHTML = '';
  STYLES.forEach(function(s){
    var chip = document.createElement('button');
    chip.type = 'button';
    chip.className = 'style-chip';
    chip.dataset.styleId = s.id;
    chip.innerHTML = '<span class="chip-icon">'+s.icon+'</span><span>'+s.nome+'</span>';
    chip.addEventListener('click', function(){
      if(wizard.styleId === s.id){
        wizard.styleId = null; wizard.styleName = null;
      } else {
        wizard.styleId = s.id; wizard.styleName = s.nome;
      }
      updateStyleChipStates();
    });
    grid.appendChild(chip);
  });
}
function updateStyleChipStates(){
  document.querySelectorAll('#style-chip-grid .style-chip').forEach(function(c){
    c.classList.toggle('active', c.dataset.styleId === wizard.styleId);
  });
}

$('upload-box').addEventListener('click', function(ev){
  // o <label> já aciona o input; nada extra necessário
});
$('file-order-image').addEventListener('change', function(ev){
  var file = ev.target.files[0];
  if(!file) return;
  downscaleImage(file, 900, function(dataUrl){
    if(!dataUrl) return;
    wizard.imageDataUrl = dataUrl;
    $('upload-preview').src = dataUrl;
    show($('upload-preview'));
    hide($('upload-placeholder'));
  });
});
$('input-description').addEventListener('input', function(ev){
  wizard.description = ev.target.value;
});

document.querySelectorAll('#size-cards .option-card').forEach(function(btn){
  btn.addEventListener('click', function(){
    wizard.size = btn.dataset.size;
    wizard.sizeLabel = btn.dataset.sizeLabel;
    document.querySelectorAll('#size-cards .option-card').forEach(function(b){ b.classList.toggle('active', b === btn); });
  });
});
document.querySelectorAll('#purpose-cards .option-card').forEach(function(btn){
  btn.addEventListener('click', function(){
    wizard.purpose = btn.dataset.purpose;
    document.querySelectorAll('#purpose-cards .option-card').forEach(function(b){ b.classList.toggle('active', b === btn); });
  });
});

$('input-whatsapp').addEventListener('input', function(ev){ wizard.whatsapp = ev.target.value; });

/* --- calendário --- */
var MESES = ['Janeiro','Fevereiro','Março','Abril','Maio','Junho','Julho','Agosto','Setembro','Outubro','Novembro','Dezembro'];
function renderCalendar(){
  var y = calendarView.year, m = calendarView.month;
  $('cal-month-label').textContent = MESES[m] + ' de ' + y;

  var today = new Date(); today.setHours(0,0,0,0);
  var firstDay = new Date(y, m, 1).getDay();
  var daysInMonth = new Date(y, m+1, 0).getDate();

  var grid = $('calendar-grid');
  grid.innerHTML = '';
  for(var i=0;i<firstDay;i++){
    var empty = document.createElement('span');
    empty.className = 'cal-day empty';
    grid.appendChild(empty);
  }
  for(var d=1; d<=daysInMonth; d++){
    var cellDate = new Date(y, m, d);
    var iso = y+'-'+String(m+1).padStart(2,'0')+'-'+String(d).padStart(2,'0');
    var btn = document.createElement('button');
    btn.type = 'button';
    btn.className = 'cal-day';
    btn.textContent = String(d);
    if(cellDate < today){
      btn.disabled = true;
    } else {
      btn.addEventListener('click', function(){
        var iso2 = this.dataset.iso;
        var parts = iso2.split('-');
        wizard.date = iso2;
        wizard.dateLabel = parts[2]+'/'+parts[1]+'/'+parts[0];
        $('selected-date-label').textContent = 'Data selecionada: ' + wizard.dateLabel;
        renderCalendar();
      });
    }
    btn.dataset.iso = iso;
    if(wizard.date === iso) btn.classList.add('selected');
    grid.appendChild(btn);
  }

  var isCurrentMonth = (y === today.getFullYear() && m === today.getMonth());
  $('cal-prev').disabled = isCurrentMonth;
  $('cal-prev').style.visibility = isCurrentMonth ? 'hidden' : 'visible';
}
$('cal-prev').addEventListener('click', function(){
  calendarView.month--;
  if(calendarView.month < 0){ calendarView.month = 11; calendarView.year--; }
  renderCalendar();
});
$('cal-next').addEventListener('click', function(){
  calendarView.month++;
  if(calendarView.month > 11){ calendarView.month = 0; calendarView.year++; }
  renderCalendar();
});

/* --- progresso / navegação de etapas --- */
function renderWizardStep(){
  for(var i=1;i<=5;i++){
    var stepEl = $('wizard-step-'+i);
    if(i === wizard.step) show(stepEl); else hide(stepEl);
  }
  document.querySelectorAll('.wp-step').forEach(function(el){
    var n = parseInt(el.dataset.step, 10);
    el.classList.toggle('active', n === wizard.step);
    el.classList.toggle('done', n < wizard.step);
  });
  document.querySelectorAll('.wp-line').forEach(function(el){
    var n = parseInt(el.dataset.line, 10);
    el.classList.toggle('done', n < wizard.step);
  });

  if(wizard.step === 1) hide($('btn-wizard-back')); else show($('btn-wizard-back'));
  $('btn-wizard-next').textContent = (wizard.step === 5) ? 'Confirmar agendamento' : 'Continuar';

  if(wizard.step === 4) renderCalendar();
  if(wizard.step === 5) renderSummary();

  window.scrollTo(0,0);
}

function renderSummary(){
  var estiloTexto = wizard.styleName || (wizard.description ? escapeHtml(wizard.description) : (wizard.imageDataUrl ? 'Imagem anexada' : '—'));
  $('summary-card').innerHTML =
    '<div><b>Referência</b>'+estiloTexto+'</div>' +
    '<div><b>Tamanho</b>'+escapeHtml(wizard.sizeLabel || '—')+'</div>' +
    '<div><b>Para quem</b>'+escapeHtml(wizard.purpose || '—')+'</div>' +
    '<div><b>Data desejada</b>'+escapeHtml(wizard.dateLabel || '—')+'</div>';
}

function validateStep(n){
  if(n === 1){
    $('error-step1').textContent = '';
    if(!wizard.imageDataUrl && !wizard.styleId && !wizard.description.trim()){
      $('error-step1').textContent = 'Anexe uma imagem, escolha um estilo ou escreva uma descrição.';
      return false;
    }
    return true;
  }
  if(n === 2){
    $('error-step2').textContent = '';
    if(!wizard.size){ $('error-step2').textContent = 'Selecione um tamanho.'; return false; }
    return true;
  }
  if(n === 3){
    $('error-step3').textContent = '';
    if(!wizard.purpose){ $('error-step3').textContent = 'Selecione para quem é o quadro.'; return false; }
    return true;
  }
  if(n === 4){
    $('error-step4').textContent = '';
    if(!wizard.date){ $('error-step4').textContent = 'Selecione uma data no calendário.'; return false; }
    return true;
  }
  if(n === 5){
    $('error-step5').textContent = '';
    var digits = wizard.whatsapp.replace(/\D/g,'');
    if(digits.length < 10){
      $('error-step5').textContent = 'Informe um WhatsApp válido, com DDD.';
      return false;
    }
    return true;
  }
  return true;
}

$('btn-wizard-next').addEventListener('click', function(){
  if(!validateStep(wizard.step)) return;
  if(wizard.step < 5){
    wizard.step++;
    renderWizardStep();
  } else {
    finalizeOrder();
  }
});
$('btn-wizard-back').addEventListener('click', function(){
  if(wizard.step > 1){
    wizard.step--;
    renderWizardStep();
  }
});
$('btn-close-wizard').addEventListener('click', function(){
  if(confirm('Sair do agendamento? Seu progresso será perdido.')){
    showScreen('screen-dashboard');
  }
});

$('btn-fazer-pedido').addEventListener('click', function(){ openWizard(); });

function openWizard(preselectStyleId){
  wizard = novoEstadoWizard();
  var today = new Date();
  calendarView.year = today.getFullYear();
  calendarView.month = today.getMonth();

  $('upload-placeholder').textContent = '📎 Toque para anexar uma imagem do seu dispositivo';
  show($('upload-placeholder'));
  hide($('upload-preview'));
  $('upload-preview').src = '';
  $('input-description').value = '';
  $('input-whatsapp').value = '';
  $('selected-date-label').textContent = '';
  document.querySelectorAll('#size-cards .option-card, #purpose-cards .option-card').forEach(function(b){ b.classList.remove('active'); });

  renderStyleChips();
  if(preselectStyleId){
    var s = STYLES.find(function(x){ return x.id === preselectStyleId; });
    if(s){ wizard.styleId = s.id; wizard.styleName = s.nome; updateStyleChipStates(); }
  }

  renderWizardStep();
  showScreen('screen-wizard');
}

/* --- finalizar pedido --- */
function pickFrase(){
  var idx;
  do { idx = Math.floor(Math.random() * FRASES.length); }
  while(FRASES.length > 1 && idx === lastFraseIndex);
  lastFraseIndex = idx;
  return FRASES[idx];
}

function buildWhatsAppLink(order, acc){
  var linhas = [
    'Novo pedido — Entre tintas 🎨',
    'Código: ' + order.code,
    'Cliente: ' + acc.name + ' (' + acc.email + ')',
    'Referência: ' + (order.styleName || order.description || 'imagem anexada no site'),
    'Tamanho: ' + order.sizeLabel,
    'Para quem: ' + order.purpose,
    'Data desejada: ' + order.dateLabel,
    'WhatsApp do cliente: ' + order.whatsapp
  ];
  if(order.imageDataUrl){
    linhas.push('Obs: a cliente anexou uma imagem de referência no site — pedir para reenviar aqui pelo chat.');
  }
  var texto = linhas.join('\n');
  return 'https://wa.me/' + WHATSAPP_LAILA + '?text=' + encodeURIComponent(texto);
}

function finalizeOrder(){
  var acc = accounts[activeEmail];
  var code = nextOrderCode();
  var now = new Date();

  var order = {
    code: code,
    styleId: wizard.styleId,
    styleName: wizard.styleName || null,
    description: wizard.description || '',
    imageDataUrl: wizard.imageDataUrl,
    size: wizard.size,
    sizeLabel: wizard.sizeLabel,
    purpose: wizard.purpose,
    date: wizard.date,
    dateLabel: wizard.dateLabel,
    whatsapp: wizard.whatsapp,
    submittedAt: now.toISOString(),
    submittedAtLabel: formatDateTime(now)
  };

  acc.orders.unshift(order);
  saveAccounts();

  // abre a aba do WhatsApp já, de forma síncrona, para não ser bloqueada como pop-up
  var waWindow = null;
  try{ waWindow = window.open('', '_blank'); }catch(e){ waWindow = null; }

  showOverlayConfirm(function(){
    var link = buildWhatsAppLink(order, acc);
    if(waWindow){ waWindow.location.href = link; }
    else { window.open(link, '_blank'); }

    showScreen('screen-dashboard');
    renderDashboard();
    activateTab('inicio');
  });
}

function showOverlayConfirm(callback){
  var overlay = $('overlay-confirm');
  $('overlay-quote').textContent = pickFrase();
  show(overlay);
  requestAnimationFrame(function(){ overlay.classList.add('visible'); });
  setTimeout(function(){
    overlay.classList.remove('visible');
    setTimeout(function(){
      hide(overlay);
      callback();
    }, 350);
  }, 3000);
}

/* ============================================================
   INICIALIZAÇÃO
   ============================================================ */
(function init(){
  applyTheme(localStorage.getItem(STORAGE_THEME) || 'light');
  if(activeEmail && accounts[activeEmail]){
    renderDashboard();
    showScreen('screen-dashboard');
  } else {
    setActive(null);
    showScreen('screen-welcome');
  }
})();

})();
</script>
</body>
</html>
