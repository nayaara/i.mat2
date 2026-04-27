<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>I.MAT | Inteligência Financeira</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg1:#dce7f1;--bg2:#c8d8e8;--bg3:#f7dd29;--bg4:#f1f4f7;
  --primary:#224e75;--secondary:#5d86aa;--accent:#f0cf1f;
  --text-main:#132f46;--text-soft:#33546f;--text-light:#607b92;
  --glass:rgba(255,255,255,0.42);--glass-strong:rgba(255,255,255,0.58);
  --white-border:rgba(255,255,255,0.55);
  --danger:#b84b4b;--success:#2f7c61;--warning:#b78b1d;
  --shadow:0 12px 35px rgba(26,52,78,0.14);--radius:22px;
}
*{box-sizing:border-box;margin:0;padding:0;}
html,body{width:100%;font-family:'Rajdhani',sans-serif;
  background:linear-gradient(135deg,var(--bg1),var(--bg2),var(--bg4),var(--bg3));
  background-attachment:fixed;color:var(--text-main);scroll-behavior:smooth;overflow-x:hidden;}
h1,h2,h3,h4{color:var(--text-main);margin-top:0;}
p,li,span,td,th,label{color:var(--text-soft);}
strong{color:var(--text-main);}
.container{width:100%;padding:32px 48px;}

/* BG SHAPES */
.bg-shapes{position:fixed;inset:0;z-index:-1;opacity:.16;pointer-events:none;}
.shape{position:absolute;color:white;animation:float 7s ease-in-out infinite;}
.shape:nth-child(2){animation-delay:1s;}.shape:nth-child(3){animation-delay:2s;}
.shape:nth-child(4){animation-delay:3s;}.shape:nth-child(5){animation-delay:4s;}
@keyframes float{0%,100%{transform:translateY(0) rotate(0deg);}50%{transform:translateY(-18px) rotate(6deg);}}

/* SCREENS */
.screen{display:none;animation:fadeIn .45s ease;}
@keyframes fadeIn{from{opacity:0;transform:translateY(12px);}to{opacity:1;transform:translateY(0);}}
#login-screen{display:flex;justify-content:center;align-items:center;width:100vw;min-height:100vh;padding:0;}

/* GLASS CARD BASE */
.glass-card,.auth-panel,.edu-section,.sheet-container,.goal-box,.mini-box,
.quote-box,.tips-box,.hero-box,.summary-box,.dream-card,.sim-card,
.footer-box,.pot-card,.quiz-card,.impulse-card{
  background:var(--glass);backdrop-filter:blur(14px);
  border:1px solid var(--white-border);box-shadow:var(--shadow);}

/* AUTH */
.auth-wrapper{width:100%;max-width:480px;padding:20px;}
.auth-panel{border-radius:28px;padding:42px 36px;}
.app-title{font-family:'Orbitron',sans-serif;font-size:2rem;color:var(--primary);}
.subtitle{color:var(--text-light);margin-bottom:18px;}
.auth-tabs{display:flex;gap:10px;margin:18px 0 24px;flex-wrap:wrap;}
.tab-btn{flex:1;min-width:130px;padding:12px;border-radius:12px;border:1px solid rgba(34,78,117,.12);
  background:rgba(255,255,255,.30);color:var(--text-main);cursor:pointer;font-family:'Orbitron',sans-serif;transition:.3s;}
.tab-btn.active{background:linear-gradient(45deg,var(--primary),var(--secondary));color:white;box-shadow:0 8px 20px rgba(34,78,117,.22);}

/* BUTTONS */
.btn-primary,.btn-action{padding:14px 20px;background:linear-gradient(45deg,var(--primary),var(--secondary));
  border:none;border-radius:12px;color:white;font-family:'Orbitron',sans-serif;cursor:pointer;
  transition:.3s;box-shadow:0 8px 20px rgba(34,78,117,.22);font-size:.85rem;letter-spacing:.03em;}
.btn-primary{width:100%;margin-top:15px;}
.btn-primary:hover,.btn-action:hover{transform:translateY(-2px);box-shadow:0 12px 28px rgba(34,78,117,.32);}
.btn-small{padding:10px 16px;border-radius:10px;cursor:pointer;border:1px solid rgba(34,78,117,.14);
  background:rgba(255,255,255,.26);color:var(--text-main);font-family:'Orbitron',sans-serif;font-size:.72rem;transition:.3s;}
.btn-small:hover{background:rgba(255,255,255,.46);transform:translateY(-1px);}
.btn-danger{background:linear-gradient(45deg,#9d3d3d,#c45858);color:white;border:none;}
.btn-success{background:linear-gradient(45deg,var(--success),#3aaa7e);color:white;border:none;}
.btn-warning{background:linear-gradient(45deg,var(--warning),#d4a520);color:white;border:none;}

/* IMPULSE BUTTONS */
.impulse-choice-btn{
  flex:1;padding:18px;border-radius:16px;border:2px solid rgba(34,78,117,.15);
  background:rgba(255,255,255,.40);cursor:pointer;transition:.3s;text-align:center;font-size:1.05rem;
  font-family:'Rajdhani',sans-serif;font-weight:700;color:var(--text-main);}
.impulse-choice-btn:hover{transform:translateY(-4px);box-shadow:0 14px 28px rgba(26,52,78,.15);}
.impulse-choice-btn.need{border-color:var(--success);background:rgba(47,124,97,.10);}
.impulse-choice-btn.want{border-color:var(--warning);background:rgba(183,139,29,.10);}

/* INPUTS */
.input-field,select{width:100%;padding:13px 14px;margin:8px 0;background:rgba(255,255,255,.60);
  border:1px solid rgba(34,78,117,.10);border-radius:12px;color:var(--text-main);
  outline:none;font-family:'Rajdhani',sans-serif;font-size:1rem;transition:border-color .2s,box-shadow .2s;}
.input-field:focus,select:focus{border-color:var(--secondary);box-shadow:0 0 0 3px rgba(93,134,170,.14);}
.input-field::placeholder{color:#6f879b;}
.input-group{position:relative;}
.toggle-password{position:absolute;right:14px;top:50%;transform:translateY(-50%);color:var(--text-light);cursor:pointer;}
.helper-row{display:flex;justify-content:space-between;align-items:center;margin-top:8px;flex-wrap:wrap;gap:10px;}
.helper-link{color:var(--primary);font-weight:700;cursor:pointer;}
.helper-link:hover{text-decoration:underline;}
.auth-msg{margin-top:16px;padding:12px 14px;border-radius:12px;font-weight:700;display:none;}
.auth-msg.success{display:block;background:rgba(47,124,97,.12);color:var(--success);border:1px solid rgba(47,124,97,.16);}
.auth-msg.error{display:block;background:rgba(184,75,75,.12);color:var(--danger);border:1px solid rgba(184,75,75,.16);}
.auth-msg.warning{display:block;background:rgba(183,139,29,.14);color:var(--warning);border:1px solid rgba(183,139,29,.16);}

/* TOPBAR */
.topbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:28px;flex-wrap:wrap;gap:10px;}
.topbar-actions{display:flex;gap:10px;flex-wrap:wrap;}
.profile-box{display:flex;align-items:center;gap:10px;flex-wrap:wrap;}
.profile-avatar{width:42px;height:42px;border-radius:50%;background:linear-gradient(45deg,var(--primary),var(--secondary));
  color:white;display:flex;align-items:center;justify-content:center;font-weight:bold;font-family:'Orbitron',sans-serif;}
.student-tag{display:inline-block;padding:6px 12px;border-radius:999px;background:rgba(255,255,255,.32);
  font-weight:bold;color:var(--text-main);font-size:.85rem;}

/* NAVIGATION TABS */
.nav-tabs{display:flex;gap:8px;margin-bottom:24px;flex-wrap:wrap;
  background:rgba(255,255,255,.35);border-radius:16px;padding:8px;}
.nav-tab{padding:10px 20px;border-radius:10px;border:none;background:transparent;
  color:var(--text-soft);font-family:'Rajdhani',sans-serif;font-weight:700;font-size:.95rem;cursor:pointer;transition:.3s;}
.nav-tab.active{background:linear-gradient(45deg,var(--primary),var(--secondary));color:white;
  box-shadow:0 4px 14px rgba(34,78,117,.22);}
.nav-tab:hover:not(.active){background:rgba(255,255,255,.50);}

/* HERO */
.hero-box{border-radius:28px;padding:28px;margin-bottom:24px;
  display:grid;grid-template-columns:1.5fr 1fr;gap:20px;align-items:center;}
.hero-badge{display:inline-block;padding:8px 14px;border-radius:999px;
  background:rgba(255,255,255,.36);color:var(--text-main);font-weight:700;margin-bottom:12px;}
.hero-title{font-family:'Orbitron',sans-serif;font-size:1.9rem;line-height:1.2;margin-bottom:12px;}
.hero-stats{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;}
.summary-box{padding:18px;border-radius:18px;text-align:center;background:rgba(255,255,255,.52);transition:transform .2s,box-shadow .2s;}
.summary-box:hover{transform:translateY(-3px);box-shadow:0 16px 36px rgba(26,52,78,.18);}
.summary-box h3{font-size:.95rem;margin-bottom:8px;}
.summary-box .value{font-size:1.4rem;font-weight:bold;color:var(--text-main);}
.summary-box .value-label{font-size:.75rem;color:var(--text-light);margin-top:4px;}

/* QUOTE BOX */
.quote-box{margin-bottom:24px;text-align:center;font-size:1.05rem;font-weight:600;padding:18px;border-radius:18px;
  background:rgba(255,255,255,.50);position:relative;overflow:hidden;cursor:pointer;}
.quote-box::before{content:'"';position:absolute;left:12px;top:-4px;font-size:5rem;
  color:rgba(34,78,117,.08);font-family:'Orbitron',sans-serif;line-height:1;}

/* CARDS GRID */
.cards-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:20px;margin-top:20px;}
.card{padding:28px;border-radius:var(--radius);transition:transform .3s,box-shadow .3s,background .3s;
  cursor:pointer;text-align:center;background:rgba(255,255,255,.48);position:relative;overflow:hidden;}
.card::after{content:'';position:absolute;bottom:0;left:0;right:0;height:3px;
  background:linear-gradient(90deg,var(--primary),var(--accent));transform:scaleX(0);transition:transform .3s;}
.card:hover{transform:translateY(-8px);background:rgba(255,255,255,.62);box-shadow:0 20px 44px rgba(26,52,78,.18);}
.card:hover::after{transform:scaleX(1);}
.card i{font-size:2.5rem;color:var(--primary);margin-bottom:14px;transition:transform .3s;}
.card:hover i{transform:scale(1.15);}
.card h3{margin-bottom:8px;}
.card-badge{position:absolute;top:12px;right:12px;padding:4px 10px;border-radius:6px;
  font-size:.65rem;font-weight:bold;text-transform:uppercase;background:rgba(34,78,117,.1);color:var(--primary);}

/* EDU SECTIONS */
.edu-section{padding:28px;border-radius:var(--radius);margin-bottom:25px;
  border-left:5px solid var(--primary);background:rgba(255,255,255,.48);}
.edu-grid,.stats-grid,.money-grid,.dream-grid,.sim-grid,.pots-grid,.quiz-grid{
  display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:20px;}
.reflexion-box,.mini-box,.goal-box,.tips-box,.dream-card,.sim-card,.pot-card,.quiz-card,.impulse-card{
  background:rgba(255,255,255,.44);padding:20px;border-radius:18px;
  border:1px solid rgba(255,255,255,.26);transition:transform .2s,box-shadow .2s;}
.reflexion-box:hover,.mini-box:hover,.goal-box:hover,.tips-box:hover,.pot-card:hover{
  transform:translateY(-3px);box-shadow:0 14px 32px rgba(26,52,78,.12);}
.badge{display:inline-block;padding:4px 10px;border-radius:6px;font-size:.72rem;
  font-weight:bold;text-transform:uppercase;margin-bottom:10px;}
.badge-need{background:#d8e8f6;color:#1f4c72;}.badge-want{background:#f7e690;color:#725b11;}
.badge-good{background:#d0ecd8;color:#1f5e3a;}.badge-bad{background:#f7dada;color:#7c1f1f;}

/* MODULE HEADER */
.module-header{display:flex;align-items:center;gap:16px;margin-bottom:28px;flex-wrap:wrap;}
.module-title-block{flex:1;}
.module-title-block h1,.module-title-block h2{font-family:'Orbitron',sans-serif;color:var(--primary);margin:0 0 4px;}

/* SECTION NUMBER */
.section-number{display:inline-flex;align-items:center;justify-content:center;width:32px;height:32px;
  border-radius:50%;background:var(--primary);color:white;font-family:'Orbitron',sans-serif;
  font-size:.75rem;font-weight:700;flex-shrink:0;margin-right:8px;}

/* CHECKLIST */
.checklist-item{display:flex;align-items:center;gap:12px;margin:10px 0;cursor:pointer;
  padding:12px 14px;border-radius:12px;background:rgba(255,255,255,.30);
  border:1px solid rgba(255,255,255,.18);transition:background .25s,transform .2s,box-shadow .2s;user-select:none;}
.checklist-item:hover{background:rgba(255,255,255,.55);transform:translateX(4px);box-shadow:0 6px 18px rgba(26,52,78,.10);}
.checklist-item.checked{background:rgba(47,124,97,.08);border-color:rgba(47,124,97,.20);}
.checklist-item input{accent-color:var(--primary);width:18px;height:18px;flex-shrink:0;pointer-events:none;}
.checklist-item span{flex:1;font-weight:600;font-size:1rem;transition:text-decoration .2s;}
.checklist-item.checked span{text-decoration:line-through;color:var(--text-light);}
.checklist-hint{font-size:.8rem;color:var(--primary);font-weight:700;white-space:nowrap;
  display:flex;align-items:center;gap:4px;opacity:.7;transition:opacity .2s;}
.checklist-item:hover .checklist-hint{opacity:1;}

/* SHEET */
.sheet-container{padding:20px;border-radius:18px;overflow-x:auto;background:rgba(255,255,255,.48);}
.sheet-table{width:100%;border-collapse:collapse;}
.sheet-table th,.sheet-table td{border:1px solid rgba(34,78,117,.10);padding:12px;text-align:left;}
.sheet-table th{background:rgba(255,255,255,.44);color:var(--text-main);}
.total-box{margin-top:20px;padding:18px;border-radius:16px;background:rgba(255,255,255,.40);
  font-size:1.15rem;font-weight:bold;text-align:center;color:var(--text-main);border:1px solid rgba(255,255,255,.22);}

/* CHART */
.chart-box{margin-top:20px;padding:20px;border-radius:18px;background:rgba(255,255,255,.36);border:1px solid rgba(255,255,255,.20);}
.bar-container{margin:16px 0;}
.bar-label{display:flex;justify-content:space-between;font-weight:bold;margin-bottom:8px;color:var(--text-main);}
.bar-track{width:100%;height:18px;background:rgba(255,255,255,.38);border-radius:999px;overflow:hidden;}
.bar-fill{height:100%;border-radius:999px;transition:width .6s ease;}
.bar-income{background:linear-gradient(90deg,#5d86aa,#224e75);}
.bar-expense{background:linear-gradient(90deg,#f7dd29,#d8b500);}
.bar-save{background:linear-gradient(90deg,#8bb4d4,#3e6b90);}

/* GOAL PROGRESS */
.goal-progress{width:100%;height:18px;background:rgba(255,255,255,.30);border-radius:999px;overflow:hidden;margin-top:10px;}
.goal-fill{height:100%;background:linear-gradient(90deg,var(--primary),var(--accent));border-radius:999px;transition:width .6s ease;}

/* RING */
.ring-wrapper{display:flex;justify-content:center;align-items:center;margin:12px 0;}
.progress-ring{width:170px;height:170px;border-radius:50%;
  background:conic-gradient(var(--primary) 0deg,var(--primary) 0deg,rgba(255,255,255,.25) 0deg);
  display:flex;align-items:center;justify-content:center;transition:background .6s;
  box-shadow:inset 0 0 20px rgba(255,255,255,.18);position:relative;}
.progress-ring::before{content:"";width:120px;height:120px;border-radius:50%;
  background:rgba(255,255,255,.72);position:absolute;}
.ring-center{position:relative;z-index:2;text-align:center;}
.ring-center strong{display:block;font-size:1.8rem;color:var(--text-main);}

/* DREAMS */
.dream-price{font-size:1.4rem;font-weight:bold;color:var(--text-main);}
.dream-list{margin-top:18px;}
.dream-item{background:rgba(255,255,255,.28);border:1px solid rgba(255,255,255,.22);
  border-radius:16px;padding:14px;margin-bottom:12px;transition:box-shadow .2s;}
.dream-item:hover{box-shadow:0 8px 22px rgba(26,52,78,.10);}
.dream-top{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap;}

/* DREAM RESPONSE */
.dream-response{margin-top:16px;padding:16px;border-radius:14px;background:linear-gradient(135deg,rgba(34,78,117,.08),rgba(240,207,31,.08));
  border:1px solid rgba(34,78,117,.12);animation:fadeIn .4s ease;}
.dream-response h4{color:var(--primary);margin-bottom:8px;display:flex;align-items:center;gap:8px;}
.dream-response .stat-row{display:flex;gap:12px;flex-wrap:wrap;margin-top:10px;}
.dream-stat{flex:1;min-width:120px;padding:12px;border-radius:12px;background:rgba(255,255,255,.55);text-align:center;}
.dream-stat .ds-val{font-size:1.3rem;font-weight:bold;color:var(--primary);}
.dream-stat .ds-label{font-size:.75rem;color:var(--text-light);margin-top:4px;}

/* POTS */
.pot-card{position:relative;overflow:hidden;}
.pot-icon{font-size:2.5rem;margin-bottom:12px;}
.pot-bar-track{width:100%;height:24px;background:rgba(255,255,255,.38);border-radius:999px;overflow:hidden;margin-top:12px;}
.pot-bar-fill{height:100%;border-radius:999px;transition:width .6s ease;display:flex;align-items:center;
  justify-content:center;font-size:.75rem;font-weight:bold;color:white;}
.pot-1 .pot-bar-fill{background:linear-gradient(90deg,var(--primary),var(--secondary));}
.pot-2 .pot-bar-fill{background:linear-gradient(90deg,var(--success),#3aaa7e);}
.pot-3 .pot-bar-fill{background:linear-gradient(90deg,var(--warning),#d4a520);}
.pot-pct{font-size:2rem;font-weight:bold;color:var(--primary);margin-bottom:4px;}
.pot-input-row{display:flex;gap:8px;align-items:center;margin-top:10px;}
.pot-input-row .input-field{margin:0;flex:1;}

/* IMPULSE TEST */
.impulse-card{border-radius:var(--radius);padding:28px;}
.impulse-scenario{font-size:1.15rem;font-weight:700;color:var(--text-main);margin-bottom:20px;line-height:1.5;}
.impulse-choices{display:flex;gap:16px;margin-bottom:20px;}
.impulse-feedback{padding:20px;border-radius:16px;animation:bounceIn .4s ease;display:none;}
.impulse-feedback.show{display:block;}
.impulse-feedback.good{background:rgba(47,124,97,.12);border:2px solid rgba(47,124,97,.25);}
.impulse-feedback.bad{background:rgba(184,75,75,.10);border:2px solid rgba(184,75,75,.20);}
.impulse-feedback h4{display:flex;align-items:center;gap:8px;margin-bottom:8px;}
.impulse-nav{display:flex;gap:10px;justify-content:space-between;align-items:center;margin-top:16px;}
.impulse-counter{font-size:.85rem;color:var(--text-light);font-weight:700;}
@keyframes bounceIn{from{opacity:0;transform:scale(.92);}to{opacity:1;transform:scale(1);}}

/* QUIZ */
.quiz-card{border-radius:var(--radius);padding:24px;}
.quiz-question{font-size:1.1rem;font-weight:700;margin-bottom:18px;color:var(--text-main);line-height:1.5;}
.quiz-options{display:flex;flex-direction:column;gap:10px;margin-bottom:16px;}
.quiz-option-btn{padding:14px 18px;border-radius:12px;border:2px solid rgba(34,78,117,.15);
  background:rgba(255,255,255,.40);cursor:pointer;text-align:left;font-size:1rem;
  font-family:'Rajdhani',sans-serif;font-weight:600;color:var(--text-main);transition:.3s;}
.quiz-option-btn:hover:not(:disabled){background:rgba(255,255,255,.65);transform:translateX(6px);}
.quiz-option-btn.correct{background:rgba(47,124,97,.15);border-color:var(--success);color:var(--success);}
.quiz-option-btn.wrong{background:rgba(184,75,75,.12);border-color:var(--danger);color:var(--danger);}
.quiz-feedback{padding:16px;border-radius:14px;margin-top:12px;display:none;animation:bounceIn .4s ease;}
.quiz-feedback.show{display:block;}
.quiz-feedback.correct{background:rgba(47,124,97,.12);border:1px solid rgba(47,124,97,.22);}
.quiz-feedback.wrong{background:rgba(184,75,75,.10);border:1px solid rgba(184,75,75,.20);}
.quiz-nav{display:flex;justify-content:space-between;align-items:center;margin-top:16px;}
.quiz-score-display{font-size:1.2rem;font-weight:bold;color:var(--primary);}
.quiz-progress-bar{width:100%;height:6px;background:rgba(255,255,255,.38);border-radius:999px;margin-bottom:16px;overflow:hidden;}
.quiz-progress-fill{height:100%;background:linear-gradient(90deg,var(--primary),var(--accent));border-radius:999px;transition:width .4s ease;}
.quiz-result-box{text-align:center;padding:28px;border-radius:18px;background:rgba(255,255,255,.48);}
.quiz-result-score{font-family:'Orbitron',sans-serif;font-size:3rem;color:var(--primary);}
.quiz-result-msg{font-size:1.15rem;font-weight:700;margin-top:10px;color:var(--text-main);}

/* SIMULATOR */
.sim-result-box{padding:20px;border-radius:16px;background:rgba(255,255,255,.50);margin-top:16px;display:none;}
.sim-result-box.show{display:block;animation:fadeIn .4s ease;}
.sim-result-big{font-family:'Orbitron',sans-serif;font-size:2.2rem;color:var(--primary);font-weight:700;}
.sim-timeline{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:12px;margin-top:16px;}
.sim-step{padding:14px;border-radius:12px;background:rgba(255,255,255,.55);text-align:center;}
.sim-step .ss-val{font-size:1.1rem;font-weight:bold;color:var(--primary);}
.sim-step .ss-label{font-size:.75rem;color:var(--text-light);margin-top:4px;}
.sim-goals-check{margin-top:16px;}
.sim-goal-row{display:flex;justify-content:space-between;align-items:center;padding:10px 14px;
  border-radius:10px;background:rgba(255,255,255,.40);margin-bottom:8px;}
.sim-goal-row.reachable{border-left:4px solid var(--success);}
.sim-goal-row.not-reachable{border-left:4px solid rgba(184,75,75,.5);}

/* INCOME MODULE */
.progress-insight{padding:14px 18px;border-radius:14px;background:rgba(255,255,255,.45);
  border:1px solid rgba(255,255,255,.30);margin-top:12px;}
.progress-insight .pi-label{font-size:.8rem;color:var(--text-light);font-weight:700;}
.progress-insight .pi-val{font-size:1.2rem;font-weight:bold;color:var(--primary);}
.insight-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:12px;margin-top:16px;}
.insight-item{padding:16px;border-radius:14px;background:rgba(255,255,255,.45);text-align:center;}
.insight-item .ii-val{font-size:1.4rem;font-weight:bold;color:var(--primary);}
.insight-item .ii-label{font-size:.75rem;color:var(--text-light);margin-top:4px;}

/* INFO BOX */
.info-banner{padding:18px 24px;border-radius:16px;background:linear-gradient(135deg,rgba(34,78,117,.08),rgba(240,207,31,.07));
  border:1px solid rgba(34,78,117,.14);margin-bottom:24px;display:flex;gap:14px;align-items:flex-start;}
.info-banner i{font-size:1.5rem;color:var(--primary);flex-shrink:0;margin-top:3px;}
.info-banner p{font-size:.95rem;line-height:1.6;}

/* TOAST */
#toast-container{position:fixed;bottom:24px;right:24px;z-index:9999;display:flex;flex-direction:column;gap:10px;}
.toast{padding:14px 20px;border-radius:14px;font-weight:700;font-size:.95rem;backdrop-filter:blur(16px);
  box-shadow:0 10px 28px rgba(26,52,78,.18);display:flex;align-items:center;gap:10px;
  animation:toastIn .35s ease forwards;max-width:320px;}
.toast.success{background:rgba(47,124,97,.88);color:white;}
.toast.error{background:rgba(184,75,75,.88);color:white;}
.toast.info{background:rgba(34,78,117,.88);color:white;}
.toast.warning{background:rgba(183,139,29,.88);color:white;}
@keyframes toastIn{from{opacity:0;transform:translateY(20px) scale(.94);}to{opacity:1;transform:translateY(0) scale(1);}}
@keyframes toastOut{from{opacity:1;transform:translateY(0) scale(1);}to{opacity:0;transform:translateY(10px) scale(.94);}}

/* HELPER PANEL */
#helper-overlay{position:fixed;inset:0;background:rgba(18,40,62,.38);z-index:1000;display:none;animation:fadeOverlay .3s ease;}
@keyframes fadeOverlay{from{opacity:0;}to{opacity:1;}}
#helper-panel{position:fixed;right:0;top:0;bottom:0;width:420px;max-width:95vw;
  background:linear-gradient(160deg,#e8f2fa 0%,#f7f2d8 100%);backdrop-filter:blur(20px);
  z-index:1001;padding:32px 28px;overflow-y:auto;box-shadow:-10px 0 40px rgba(26,52,78,.20);
  transform:translateX(100%);transition:transform .38s cubic-bezier(.4,0,.2,1);}
#helper-panel.open{transform:translateX(0);}
.helper-panel-header{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:24px;gap:12px;}
.helper-panel-icon{width:54px;height:54px;border-radius:16px;background:linear-gradient(45deg,var(--primary),var(--secondary));
  display:flex;align-items:center;justify-content:center;font-size:1.6rem;color:white;flex-shrink:0;box-shadow:0 6px 18px rgba(34,78,117,.22);}
.helper-close-btn{background:rgba(255,255,255,.50);border:1px solid rgba(34,78,117,.12);border-radius:10px;
  width:38px;height:38px;cursor:pointer;display:flex;align-items:center;justify-content:center;
  color:var(--text-main);font-size:1rem;transition:background .2s;flex-shrink:0;}
.helper-close-btn:hover{background:rgba(255,255,255,.80);}
.helper-panel-title{font-family:'Orbitron',sans-serif;font-size:1.15rem;color:var(--primary);margin:0 0 4px;}
.helper-panel-subtitle{font-size:.9rem;color:var(--text-light);font-weight:600;}
.helper-section{background:rgba(255,255,255,.55);border-radius:16px;padding:18px;margin-bottom:16px;
  border:1px solid rgba(255,255,255,.40);box-shadow:0 4px 14px rgba(26,52,78,.07);}
.helper-section h4{color:var(--primary);margin-bottom:10px;font-size:1rem;display:flex;align-items:center;gap:8px;}
.helper-section p,.helper-section li{font-size:.95rem;line-height:1.6;}
.helper-section ul{padding-left:18px;margin-top:8px;}
.helper-section ul li{margin:6px 0;}
.helper-impact-box{background:linear-gradient(135deg,rgba(34,78,117,.10),rgba(240,207,31,.12));
  border:1px solid rgba(34,78,117,.14);border-radius:14px;padding:16px;margin-bottom:16px;text-align:center;}
.helper-impact-value{font-family:'Orbitron',sans-serif;font-size:1.8rem;color:var(--primary);font-weight:700;}
.helper-impact-label{font-size:.85rem;color:var(--text-light);font-weight:600;margin-top:4px;}
.helper-action-btn{width:100%;padding:13px;background:linear-gradient(45deg,var(--primary),var(--secondary));
  border:none;border-radius:12px;color:white;font-family:'Orbitron',sans-serif;font-size:.78rem;cursor:pointer;
  margin-top:8px;transition:.3s;box-shadow:0 6px 16px rgba(34,78,117,.18);}
.helper-action-btn:hover{transform:translateY(-2px);box-shadow:0 10px 24px rgba(34,78,117,.28);}
.helper-tag{display:inline-block;padding:4px 10px;border-radius:8px;font-size:.76rem;font-weight:700;
  background:rgba(34,78,117,.10);color:var(--primary);margin:3px 2px;}
.mini-calc{background:rgba(255,255,255,.70);border-radius:14px;padding:16px;margin-top:12px;border:1px solid rgba(255,255,255,.40);}
.mini-calc label{font-size:.85rem;font-weight:700;color:var(--text-main);display:block;margin-bottom:4px;}
.mini-calc input{width:100%;padding:10px 12px;border-radius:10px;border:1px solid rgba(34,78,117,.12);
  background:rgba(255,255,255,.80);font-family:'Rajdhani',sans-serif;font-size:1rem;color:var(--text-main);outline:none;margin-bottom:8px;}
.mini-calc-result{background:rgba(34,78,117,.08);border-radius:10px;padding:10px 12px;font-weight:700;
  color:var(--primary);text-align:center;min-height:40px;display:flex;align-items:center;justify-content:center;font-size:.95rem;}

/* FOOTER */
.footer-box{margin-top:30px;border-radius:20px;padding:18px;text-align:center;font-size:.95rem;background:rgba(255,255,255,.48);}
.positive{color:#245f47;}.negative{color:#a03b3b;}
ul.clean{list-style:none;padding-left:0;}
ul.clean li{margin:12px 0;}

/* RESPONSIVE */
@media(max-width:980px){.hero-box{grid-template-columns:1fr;}}
@media(max-width:768px){
  .container{padding:20px 18px;}
  .auth-panel{padding:28px 20px;}
  .cards-grid,.edu-grid,.stats-grid,.money-grid,.dream-grid,.sim-grid,.pots-grid,.quiz-grid,.hero-stats{grid-template-columns:1fr;}
  .sheet-table{min-width:720px;}
  .hero-title{font-size:1.6rem;}
  #helper-panel{width:100vw;}
  .impulse-choices{flex-direction:column;}
  .nav-tabs{gap:4px;}
  .nav-tab{padding:8px 12px;font-size:.85rem;}
}

/* PULSE ANIMATION */
@keyframes pulse{0%,100%{box-shadow:0 0 0 0 rgba(34,78,117,.3);}50%{box-shadow:0 0 0 10px rgba(34,78,117,0);}}
.pulse{animation:pulse 2s infinite;}

/* MONEY VISUAL */
.money-flow{display:flex;align-items:center;gap:12px;margin:16px 0;flex-wrap:wrap;}
.money-flow-item{flex:1;min-width:120px;padding:16px;border-radius:14px;text-align:center;
  background:rgba(255,255,255,.45);position:relative;}
.money-flow-arrow{font-size:1.5rem;color:var(--primary);opacity:.5;}
.mf-icon{font-size:1.8rem;margin-bottom:8px;}
.mf-label{font-size:.85rem;font-weight:700;color:var(--text-main);}
.mf-desc{font-size:.75rem;color:var(--text-light);margin-top:4px;}

/* STEP GUIDE */
.step-guide{counter-reset:step;display:flex;flex-direction:column;gap:12px;}
.step-item{display:flex;gap:14px;padding:14px;border-radius:14px;background:rgba(255,255,255,.40);align-items:flex-start;}
.step-item::before{counter-increment:step;content:counter(step);display:flex;align-items:center;justify-content:center;
  width:30px;height:30px;border-radius:50%;background:var(--primary);color:white;font-family:'Orbitron',sans-serif;
  font-size:.75rem;font-weight:700;flex-shrink:0;}
.step-content h5{color:var(--text-main);margin-bottom:4px;font-size:1rem;}
.step-content p{font-size:.9rem;}
</style>
</head>
<body>

<div class="bg-shapes">
  <i class="fas fa-circle shape" style="top:10%;left:6%;font-size:22px;"></i>
  <i class="fas fa-plus shape" style="top:80%;left:90%;font-size:30px;"></i>
  <i class="fas fa-heart shape" style="top:25%;left:82%;font-size:28px;"></i>
  <i class="fas fa-star shape" style="top:70%;left:12%;font-size:24px;"></i>
  <i class="fas fa-circle shape" style="top:40%;left:45%;font-size:22px;"></i>
</div>

<div id="toast-container"></div>

<div id="helper-overlay" onclick="fecharPainel()"></div>
<div id="helper-panel">
  <div class="helper-panel-header">
    <div style="display:flex;gap:14px;align-items:flex-start;flex:1;">
      <div class="helper-panel-icon" id="helper-icon"><i class="fas fa-lightbulb"></i></div>
      <div style="flex:1;">
        <p class="helper-panel-title" id="helper-title">Orientação</p>
        <p class="helper-panel-subtitle" id="helper-subtitle">Consciência financeira</p>
      </div>
    </div>
    <button class="helper-close-btn" onclick="fecharPainel()"><i class="fas fa-times"></i></button>
  </div>
  <div id="helper-content"></div>
</div>

<div id="login-screen" class="screen" style="display:flex;">
  <div class="auth-wrapper">
    <div class="auth-panel">
      <h1 class="app-title">I.MAT</h1>
      <p class="subtitle">Painel financeiro para estudantes</p>
      <div class="auth-tabs">
        <button class="tab-btn active" id="tab-login" onclick="alternarAba('login')">Entrar</button>
        <button class="tab-btn" id="tab-register" onclick="alternarAba('register')">Criar conta</button>
      </div>
      <div id="login-form">
        <input type="email" id="login-email" class="input-field" placeholder="Seu e-mail">
        <div class="input-group">
          <input type="password" id="login-senha" class="input-field" placeholder="Sua senha">
          <i class="fas fa-eye toggle-password" onclick="toggleSenha('login-senha',this)"></i>
        </div>
        <div class="helper-row">
          <span style="font-weight:600;color:var(--text-light)">Acesso individual</span>
          <a class="helper-link" onclick="abrirRecuperarSenha()">Recuperar senha</a>
        </div>
        <button class="btn-primary" onclick="validarAcesso()"><i class="fas fa-sign-in-alt" style="margin-right:8px;"></i>ACESSAR SISTEMA</button>
      </div>
      <div id="register-form" style="display:none;">
        <input type="text" id="register-nome" class="input-field" placeholder="Seu nome">
        <input type="email" id="register-email" class="input-field" placeholder="Seu e-mail">
        <div class="input-group">
          <input type="password" id="register-senha" class="input-field" placeholder="Crie uma senha">
          <i class="fas fa-eye toggle-password" onclick="toggleSenha('register-senha',this)"></i>
        </div>
        <div class="input-group">
          <input type="password" id="register-confirmar" class="input-field" placeholder="Confirme sua senha">
          <i class="fas fa-eye toggle-password" onclick="toggleSenha('register-confirmar',this)"></i>
        </div>
        <button class="btn-primary" onclick="criarConta()"><i class="fas fa-user-plus" style="margin-right:8px;"></i>CRIAR CONTA</button>
      </div>
      <div id="auth-message" class="auth-msg"></div>
    </div>
  </div>
</div>

<div id="main-dashboard" class="container screen">
  <div class="topbar">
    <div class="profile-box">
      <div class="profile-avatar" id="profile-avatar">I</div>
      <div>
        <h2 style="font-family:'Orbitron';margin:0;">HUB <span style="color:var(--primary)">I.MAT</span></h2>
        <span class="student-tag" id="welcome-user">Área do estudante</span>
      </div>
    </div>
    <div class="topbar-actions">
      <button onclick="abrirRecuperarSenha()" class="btn-small"><i class="fas fa-key" style="margin-right:5px;"></i>Recuperar senha</button>
      <button onclick="excluirConta()" class="btn-small btn-danger"><i class="fas fa-trash" style="margin-right:5px;"></i>Excluir conta</button>
      <button onclick="logout()" class="btn-small"><i class="fas fa-sign-out-alt" style="margin-right:5px;"></i>Sair</button>
    </div>
  </div>

  <div class="hero-box">
    <div>
      <span class="hero-badge"><i class="fas fa-graduation-cap" style="margin-right:6px;"></i>Assistência financeira para a rotina estudantil</span>
      <div class="hero-title">Aprenda a organizar, preservar e desenvolver seu dinheiro com clareza.</div>
      <p>O I.MAT foi estruturado para apoiar estudantes na construção de autonomia financeira por meio de orientação prática, organização e planejamento.</p>
    </div>
    <div class="hero-stats">
      <div class="summary-box">
        <h3><i class="fas fa-wallet" style="margin-right:5px;color:var(--primary);"></i>Saldo Atual</h3>
        <div class="value" id="hero-saldo">R$ 0,00</div>
        <div class="value-label" id="hero-saldo-status">-</div>
      </div>
      <div class="summary-box">
        <h3><i class="fas fa-bullseye" style="margin-right:5px;color:var(--primary);"></i>Meta</h3>
        <div class="value" id="hero-meta">R$ 0,00</div>
        <div class="value-label" id="hero-meta-pct">-</div>
      </div>
      <div class="summary-box">
        <h3><i class="fas fa-arrow-up" style="margin-right:5px;color:var(--success);"></i>Ganhos</h3>
        <div class="value" id="hero-ganhos">R$ 0,00</div>
        <div class="value-label">Total registrado</div>
      </div>
      <div class="summary-box">
        <h3><i class="fas fa-arrow-down" style="margin-right:5px;color:var(--danger);"></i>Gastos</h3>
        <div class="value" id="hero-gastos">R$ 0,00</div>
        <div class="value-label">Total registrado</div>
      </div>
    </div>
  </div>

  <div class="quote-box" id="frase-motivacional" onclick="trocarFrase()" title="Clique para trocar a frase"></div>

  <div class="cards-grid">
    <div class="card" onclick="abrirModulo('handle-money')">
      <span class="card-badge">Educativo</span>
      <i class="fas fa-brain"></i>
      <h3>Manusear Dinheiro</h3>
      <p>Consciência, comportamento e decisões mais equilibradas.</p>
    </div>
    <div class="card" onclick="abrirModulo('finance-organizer')">
      <span class="card-badge">Registro</span>
      <i class="fas fa-table"></i>
      <h3>Organizar Finanças</h3>
      <p>Controle de ganhos, gastos e saldo disponível.</p>
    </div>
    <div class="card" onclick="abrirModulo('income-module')">
      <span class="card-badge">Progresso</span>
      <i class="fas fa-chart-pie"></i>
      <h3>Rendimento</h3>
      <p>Metas, acompanhamento e evolução financeira.</p>
    </div>
    <div class="card" onclick="abrirModulo('earn-money-module')">
      <span class="card-badge">Renda</span>
      <i class="fas fa-rocket"></i>
      <h3>Obter Dinheiro</h3>
      <p>Possibilidades práticas de geração de renda para estudantes.</p>
    </div>
    <div class="card" onclick="abrirModulo('dreams-module')">
      <span class="card-badge">Planejamento</span>
      <i class="fas fa-cloud"></i>
      <h3>Meus Objetivos</h3>
      <p>Transforme intenções em metas concretas.</p>
    </div>
    <div class="card" onclick="abrirModulo('simulator-module')">
      <span class="card-badge">Simulação</span>
      <i class="fas fa-calculator"></i>
      <h3>Simulador</h3>
      <p>Projete quanto você pode acumular ao longo do tempo.</p>
    </div>
  </div>

  <div class="footer-box">
    <strong>I.MAT</strong> • Inteligência Financeira para Estudantes<br>
    Organização, consciência e desenvolvimento com autonomia.
  </div>
</div>

<div id="handle-money" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h1><i class="fas fa-brain" style="color:var(--secondary);margin-right:10px;"></i>Manusear Dinheiro</h1>
      <p>Dinheiro não envolve apenas cálculo. Também exige <strong>disciplina, critério e comportamento</strong>.</p>
    </div>
  </div>

  <div class="nav-tabs">
    <button class="nav-tab active" onclick="mostrarTab('money','impulso', event)">Teste de Decisão</button>
    <button class="nav-tab" onclick="mostrarTab('money','perguntas', event)">Perguntas</button>
    <button class="nav-tab" onclick="mostrarTab('money','potes', event)">Estratégia dos Potes</button>
    <button class="nav-tab" onclick="mostrarTab('money','dicas', event)">Dicas e Erros</button>
  </div>

  <div id="money-tab-impulso">
    <div class="info-banner">
      <i class="fas fa-bolt"></i>
      <p>O <strong>Teste de Decisão</strong> ajuda a diferenciar uma <em>necessidade real</em> de um <em>desejo momentâneo</em>. Leia cada situação e avalie com cuidado.</p>
    </div>
    <div class="impulse-card glass-card">
      <div id="impulse-score-bar" style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;">
        <span class="impulse-counter" id="impulse-counter">Situação 1 de 6</span>
        <div style="display:flex;gap:8px;">
          <span id="impulse-acertos" style="font-weight:700;color:var(--success);font-size:.9rem;">Acertos: 0</span>
          <span id="impulse-erros" style="font-weight:700;color:var(--danger);font-size:.9rem;">Erros: 0</span>
        </div>
      </div>
      <div class="quiz-progress-bar"><div class="quiz-progress-fill" id="impulse-pbar" style="width:0%"></div></div>
      <div class="impulse-scenario" id="impulse-scenario">Carregando situação...</div>
      <div class="impulse-choices">
        <button class="impulse-choice-btn need" onclick="responderImpulso('necessidade')">
          <i class="fas fa-shield-alt" style="font-size:1.5rem;color:var(--success);display:block;margin-bottom:8px;"></i>
          Necessidade<br><small style="font-size:.8rem;color:var(--text-light);">Trata-se de algo essencial</small>
        </button>
        <button class="impulse-choice-btn want" onclick="responderImpulso('desejo')">
          <i class="fas fa-heart" style="font-size:1.5rem;color:var(--warning);display:block;margin-bottom:8px;"></i>
          Desejo<br><small style="font-size:.8rem;color:var(--text-light);">Trata-se de uma vontade momentânea</small>
        </button>
      </div>
      <div class="impulse-feedback" id="impulse-feedback"></div>
      <div class="impulse-nav">
        <span></span>
        <button class="btn-action" id="impulse-next-btn" onclick="proximoImpulso()" style="display:none;padding:10px 20px;font-size:.8rem;">
          Próximo <i class="fas fa-arrow-right" style="margin-left:6px;"></i>
        </button>
      </div>
    </div>
    <div id="impulse-result" style="display:none;" class="quiz-result-box glass-card">
      <i class="fas fa-brain" style="font-size:2.5rem;color:var(--primary);margin-bottom:12px;"></i>
      <div class="quiz-result-score" id="impulse-final-score">0/6</div>
      <div class="quiz-result-msg" id="impulse-final-msg"></div>
      <button class="btn-action" onclick="reiniciarImpulso()" style="margin-top:20px;padding:12px 24px;">Refazer avaliação</button>
    </div>
  </div>

  <div id="money-tab-perguntas" style="display:none;">
    <div class="info-banner">
      <i class="fas fa-question-circle"></i>
      <p>Verifique seus conhecimentos financeiros. Após cada resposta, você receberá uma explicação objetiva para consolidar o aprendizado.</p>
    </div>
    <div class="quiz-card glass-card">
      <div class="quiz-progress-bar"><div class="quiz-progress-fill" id="quiz-pbar" style="width:0%"></div></div>
      <div style="display:flex;justify-content:space-between;margin-bottom:12px;">
        <span class="impulse-counter" id="quiz-counter">Pergunta 1 de 8</span>
        <span class="quiz-score-display" id="quiz-score">0 pontos</span>
      </div>
      <div class="quiz-question" id="quiz-question">Carregando pergunta...</div>
      <div class="quiz-options" id="quiz-options"></div>
      <div class="quiz-feedback" id="quiz-feedback"></div>
      <div class="quiz-nav">
        <span></span>
        <button class="btn-action" id="quiz-next-btn" onclick="proximaPergunta()" style="display:none;padding:10px 20px;font-size:.8rem;">
          Próxima <i class="fas fa-arrow-right" style="margin-left:6px;"></i>
        </button>
      </div>
    </div>
    <div id="quiz-result" style="display:none;" class="quiz-result-box glass-card">
      <i class="fas fa-trophy" style="font-size:2.5rem;color:var(--warning);margin-bottom:12px;"></i>
      <div class="quiz-result-score" id="quiz-final-score">0/8</div>
      <div class="quiz-result-msg" id="quiz-final-msg"></div>
      <button class="btn-action" onclick="reiniciarQuiz()" style="margin-top:20px;padding:12px 24px;">Reiniciar questionário</button>
    </div>
  </div>

  <div id="money-tab-potes" style="display:none;">
    <div class="info-banner">
      <i class="fas fa-piggy-bank"></i>
      <p>A <strong>Estratégia dos Potes</strong> divide a renda em três partes com percentuais definidos. Informe sua renda mensal para visualizar uma distribuição sugerida.</p>
    </div>

    <div class="edu-section" style="margin-bottom:24px;">
      <h3><i class="fas fa-calculator" style="margin-right:8px;color:var(--primary);"></i>Calcule seus potes</h3>
      <div style="display:flex;gap:12px;align-items:flex-end;flex-wrap:wrap;margin-top:12px;">
        <div style="flex:1;min-width:200px;">
          <label style="font-weight:700;color:var(--text-main);display:block;margin-bottom:6px;">Sua renda mensal (R$)</label>
          <input type="number" id="potes-renda" class="input-field" placeholder="Ex.: 800" oninput="calcularPotes()" style="margin:0;">
        </div>
        <div style="flex:1;min-width:200px;">
          <label style="font-weight:700;color:var(--text-main);display:block;margin-bottom:6px;">Modelo de divisão</label>
          <select id="potes-modelo" class="input-field" onchange="calcularPotes()" style="margin:0;">
            <option value="50-30-20">50% / 30% / 20% (Padrão)</option>
            <option value="60-20-20">60% / 20% / 20% (Mais essencial)</option>
            <option value="40-40-20">40% / 40% / 20% (Mais futuro)</option>
            <option value="50-40-10">50% / 40% / 10% (Foco em meta)</option>
          </select>
        </div>
      </div>
    </div>

    <div class="pots-grid">
      <div class="pot-card pot-1">
        <div class="pot-icon"><i class="fas fa-shopping-basket"></i></div>
        <div class="pot-pct" id="pot1-pct">50%</div>
        <h3 id="pot1-title">Essencial</h3>
        <p id="pot1-desc">Alimentação, transporte, estudo, moradia e necessidades básicas.</p>
        <div class="pot-bar-track"><div class="pot-bar-fill" id="pot1-bar" style="width:50%">50%</div></div>
        <div class="pot-input-row">
          <span style="font-weight:700;color:var(--text-main);font-size:.85rem;">Valor:</span>
          <input type="text" id="pot1-val" class="input-field" value="R$ 0,00" readonly style="background:rgba(255,255,255,.6);font-weight:bold;">
        </div>
        <p style="font-size:.8rem;margin-top:10px;color:var(--text-light);">Prioridade principal. O essencial deve ser atendido primeiro.</p>
      </div>
      <div class="pot-card pot-2">
        <div class="pot-icon"><i class="fas fa-building-columns"></i></div>
        <div class="pot-pct" id="pot2-pct">30%</div>
        <h3 id="pot2-title">Futuro / Meta</h3>
        <p id="pot2-desc">Reserva para objetivos, emergências e planejamento de médio prazo.</p>
        <div class="pot-bar-track"><div class="pot-bar-fill" id="pot2-bar" style="width:30%">30%</div></div>
        <div class="pot-input-row">
          <span style="font-weight:700;color:var(--text-main);font-size:.85rem;">Valor:</span>
          <input type="text" id="pot2-val" class="input-field" value="R$ 0,00" readonly style="background:rgba(255,255,255,.6);font-weight:bold;">
        </div>
        <p style="font-size:.8rem;margin-top:10px;color:var(--text-light);">Separe esse valor assim que receber sua renda.</p>
      </div>
      <div class="pot-card pot-3">
        <div class="pot-icon"><i class="fas fa-user"></i></div>
        <div class="pot-pct" id="pot3-pct">20%</div>
        <h3 id="pot3-title">Lazer / Pessoal</h3>
        <p id="pot3-desc">Uso consciente em entretenimento, atividades sociais e despesas opcionais.</p>
        <div class="pot-bar-track"><div class="pot-bar-fill" id="pot3-bar" style="width:20%">20%</div></div>
        <div class="pot-input-row">
          <span style="font-weight:700;color:var(--text-main);font-size:.85rem;">Valor:</span>
          <input type="text" id="pot3-val" class="input-field" value="R$ 0,00" readonly style="background:rgba(255,255,255,.6);font-weight:bold;">
        </div>
        <p style="font-size:.8rem;margin-top:10px;color:var(--text-light);">Utilize esse valor com limite e critério.</p>
      </div>
    </div>

    <div id="potes-resultado" style="display:none;margin-top:20px;" class="edu-section">
      <h3><i class="fas fa-check-circle" style="color:var(--success);margin-right:8px;"></i>Plano sugerido de distribuição</h3>
      <div id="potes-resultado-content"></div>
    </div>
  </div>

  <div id="money-tab-dicas" style="display:none;">
    <div class="edu-section">
      <h3><span class="section-number">1</span>Como o dinheiro funciona na prática</h3>
      <div class="money-flow">
        <div class="money-flow-item">
          <div class="mf-icon"><i class="fas fa-briefcase"></i></div>
          <div class="mf-label">Recebe</div>
          <div class="mf-desc">Mesada, trabalho, presentes</div>
        </div>
        <div class="money-flow-arrow"><i class="fas fa-arrow-right"></i></div>
        <div class="money-flow-item">
          <div class="mf-icon"><i class="fas fa-shopping-cart"></i></div>
          <div class="mf-label">Atende o essencial</div>
          <div class="mf-desc">Prioridade ao que é necessário</div>
        </div>
        <div class="money-flow-arrow"><i class="fas fa-arrow-right"></i></div>
        <div class="money-flow-item">
          <div class="mf-icon"><i class="fas fa-piggy-bank"></i></div>
          <div class="mf-label">Reserva</div>
          <div class="mf-desc">Metas e segurança</div>
        </div>
        <div class="money-flow-arrow"><i class="fas fa-arrow-right"></i></div>
        <div class="money-flow-item">
          <div class="mf-icon"><i class="fas fa-check-circle"></i></div>
          <div class="mf-label">Utiliza com equilíbrio</div>
          <div class="mf-desc">Consumo sob controle</div>
        </div>
      </div>
    </div>

    <div class="edu-grid">
      <div class="edu-section">
        <h3><span class="section-number">2</span>Checklist de prevenção</h3>
        <p style="font-size:.88rem;color:var(--text-light);margin-bottom:12px;"><i class="fas fa-hand-pointer" style="margin-right:5px;"></i>Clique em cada item para ver a orientação correspondente.</p>
        <div class="checklist-item" onclick="toggleChecklist(this,'lanche')"><input type="checkbox"><span>Comprar lanche caro todos os dias.</span><div class="checklist-hint"><i class="fas fa-lightbulb"></i> Ver orientação</div></div>
        <div class="checklist-item" onclick="toggleChecklist(this,'gastos')"><input type="checkbox"><span>Ignorar pequenos gastos recorrentes.</span><div class="checklist-hint"><i class="fas fa-lightbulb"></i> Ver orientação</div></div>
        <div class="checklist-item" onclick="toggleChecklist(this,'promocao')"><input type="checkbox"><span>Comprar apenas porque está em promoção.</span><div class="checklist-hint"><i class="fas fa-lightbulb"></i> Ver orientação</div></div>
        <div class="checklist-item" onclick="toggleChecklist(this,'pagamentos')"><input type="checkbox"><span>Atrasar pagamentos simples.</span><div class="checklist-hint"><i class="fas fa-lightbulb"></i> Ver orientação</div></div>
      </div>
      <div class="edu-section" style="border-left-color:var(--danger);">
        <h3><span class="section-number" style="background:var(--danger);">3</span>Erros frequentes</h3>
        <p><i class="fas fa-times-circle" style="color:var(--danger)"></i> <strong>Gastar tudo de uma vez:</strong> a satisfação é breve, mas a falta de recurso permanece.</p>
        <p style="margin-top:10px;"><i class="fas fa-times-circle" style="color:var(--danger)"></i> <strong>Não estabelecer meta:</strong> sem direção, qualquer gasto parece aceitável.</p>
        <p style="margin-top:10px;"><i class="fas fa-times-circle" style="color:var(--danger)"></i> <strong>Confundir renda com estabilidade:</strong> receber não significa administrar bem.</p>
        <p style="margin-top:10px;"><i class="fas fa-times-circle" style="color:var(--danger)"></i> <strong>Comparar-se com os outros:</strong> cada realidade financeira é distinta.</p>
        <p style="margin-top:10px;"><i class="fas fa-times-circle" style="color:var(--danger)"></i> <strong>Não registrar despesas:</strong> o que não é acompanhado não pode ser corrigido.</p>
      </div>
    </div>

    <div class="edu-section" style="border-left-color:var(--success);">
      <h3><span class="section-number" style="background:var(--success);">4</span>Como começar hoje</h3>
      <div class="step-guide">
        <div class="step-item"><div class="step-content"><h5>Registre sua renda</h5><p>Saiba exatamente quanto você recebe por mês, seja por mesada, trabalho ou outra fonte.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Liste seus gastos fixos</h5><p>Identifique as despesas que se repetem mensalmente, como transporte, alimentação e internet.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Defina um valor para guardar</h5><p>Mesmo um valor inicial pequeno já contribui para criar consistência.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Registre tudo na planilha</h5><p>Use o módulo "Organizar Finanças" para acompanhar ganhos e gastos com regularidade.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Revise mensalmente</h5><p>No encerramento do mês, avalie onde houve excesso e quais ajustes podem ser feitos.</p></div></div>
      </div>
    </div>
  </div>
</div>

<div id="finance-organizer" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h2><i class="fas fa-table" style="color:var(--secondary);margin-right:10px;"></i>Organizar Finanças</h2>
    </div>
  </div>

  <div class="info-banner">
    <i class="fas fa-info-circle"></i>
    <p><strong>Como utilizar esta planilha:</strong> registre cada ganho e cada gasto. O sistema calcula automaticamente o saldo, apresenta um resumo visual e atualiza o acompanhamento das metas. Quanto mais preciso for o registro, melhor será sua visão financeira.</p>
  </div>

  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:14px;margin-bottom:24px;">
    <div class="summary-box pulse">
      <h3><i class="fas fa-wallet" style="color:var(--primary);"></i> Saldo</h3>
      <div class="value" id="fo-saldo">R$ 0,00</div>
      <div class="value-label" id="fo-saldo-status">Neutro</div>
    </div>
    <div class="summary-box">
      <h3><i class="fas fa-arrow-up" style="color:var(--success);"></i> Ganhos</h3>
      <div class="value positive" id="fo-ganhos">R$ 0,00</div>
      <div class="value-label" id="fo-n-ganhos">0 registros</div>
    </div>
    <div class="summary-box">
      <h3><i class="fas fa-arrow-down" style="color:var(--danger);"></i> Gastos</h3>
      <div class="value negative" id="fo-gastos">R$ 0,00</div>
      <div class="value-label" id="fo-n-gastos">0 registros</div>
    </div>
    <div class="summary-box">
      <h3><i class="fas fa-percent" style="color:var(--secondary);"></i> Economia</h3>
      <div class="value" id="fo-economia-pct">0%</div>
      <div class="value-label">da renda preservada</div>
    </div>
  </div>

  <div class="sheet-container">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;flex-wrap:wrap;gap:10px;">
      <h3 style="margin:0;">Registros</h3>
      <div style="display:flex;gap:8px;flex-wrap:wrap;">
        <button class="btn-small btn-success" onclick="adicionarLinhaGanho()"><i class="fas fa-plus"></i> Ganho</button>
        <button class="btn-small btn-danger" onclick="adicionarLinhaGasto()"><i class="fas fa-plus"></i> Gasto</button>
      </div>
    </div>
    <table class="sheet-table">
      <thead>
        <tr>
          <th>Descrição</th><th>Tipo</th><th>Valor (R$)</th><th>Ação</th>
        </tr>
      </thead>
      <tbody id="sheet-body"></tbody>
    </table>
    <div class="total-box" id="saldo-total">Saldo atual: R$ 0,00</div>

    <div class="chart-box">
      <h3>Resumo visual</h3>
      <div class="bar-container">
        <div class="bar-label"><span><i class="fas fa-arrow-up" style="color:var(--success);"></i> Ganhos</span><span id="ganhos-label">R$ 0,00</span></div>
        <div class="bar-track"><div class="bar-fill bar-income" id="bar-ganhos" style="width:0%"></div></div>
      </div>
      <div class="bar-container">
        <div class="bar-label"><span><i class="fas fa-arrow-down" style="color:var(--danger);"></i> Gastos</span><span id="gastos-label">R$ 0,00</span></div>
        <div class="bar-track"><div class="bar-fill bar-expense" id="bar-gastos" style="width:0%"></div></div>
      </div>
      <div class="bar-container">
        <div class="bar-label"><span><i class="fas fa-piggy-bank" style="color:var(--primary);"></i> Economia</span><span id="economia-label">R$ 0,00</span></div>
        <div class="bar-track"><div class="bar-fill bar-save" id="bar-economia" style="width:0%"></div></div>
      </div>
      <div id="fo-dica-saldo" style="margin-top:14px;padding:12px 16px;border-radius:12px;background:rgba(255,255,255,.45);display:none;"></div>
    </div>
  </div>
</div>

<div id="income-module" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h2><i class="fas fa-chart-pie" style="color:var(--secondary);margin-right:10px;"></i>Rendimento e Metas</h2>
    </div>
  </div>

  <div class="info-banner" id="income-banner">
    <i class="fas fa-chart-line"></i>
    <p id="income-banner-text">Defina uma meta de economia e acompanhe seu progresso. O painel será atualizado à medida que você registrar ganhos e gastos.</p>
  </div>

  <div class="money-grid">
    <div class="goal-box">
      <h3><i class="fas fa-bullseye" style="color:var(--primary);margin-right:8px;"></i>Meta Financeira</h3>
      <p>Defina quanto você pretende guardar.</p>
      <input type="number" id="meta-valor" class="input-field" placeholder="Ex.: 500">
      <div style="display:flex;gap:8px;">
        <button class="btn-action" onclick="salvarMeta()" style="margin-top:8px;padding:12px;font-size:.8rem;flex:1;"><i class="fas fa-save" style="margin-right:6px;"></i>Salvar meta</button>
        <button class="btn-small" onclick="limparMeta()" style="margin-top:8px;"><i class="fas fa-trash"></i></button>
      </div>
      <div style="margin-top:20px;">
        <div style="display:flex;justify-content:space-between;align-items:center;">
          <strong>Meta atual:</strong>
          <span id="meta-atual" style="font-weight:bold;color:var(--primary);">R$ 0,00</span>
        </div>
        <div class="goal-progress" style="margin-top:10px;"><div class="goal-fill" id="meta-fill" style="width:0%"></div></div>
        <p id="meta-progresso-texto" style="margin-top:8px;text-align:center;font-weight:700;color:var(--primary);">Progresso: 0%</p>
      </div>
    </div>

    <div class="goal-box">
      <h3><i class="fas fa-chart-pie" style="color:var(--secondary);margin-right:8px;"></i>Progresso Geral</h3>
      <div id="progress-no-data" style="text-align:center;padding:20px;">
        <i class="fas fa-chart-pie" style="font-size:2.5rem;color:var(--text-light);margin-bottom:12px;"></i>
        <p>Registre ganhos e gastos para visualizar seu progresso geral.</p>
      </div>
      <div id="progress-ring-area" style="display:none;">
        <div class="ring-wrapper">
          <div class="progress-ring" id="progress-ring">
            <div class="ring-center">
              <strong id="ring-percent">0%</strong>
              <span>da meta</span>
            </div>
          </div>
        </div>
        <p style="text-align:center;margin-top:14px;font-weight:700;" id="quanto-falta">R$ 0,00 para sua meta</p>
        <p style="text-align:center;" id="situacao-meta">Defina uma meta para começar.</p>
      </div>
    </div>
  </div>

  <div id="income-insights" style="display:none;">
    <div class="edu-section">
      <h3><i class="fas fa-lightbulb" style="color:var(--warning);margin-right:8px;"></i>Evolução em números</h3>
      <div class="insight-grid" id="insight-grid-content"></div>
    </div>
  </div>

  <div class="edu-section">
    <h3>Dicas de crescimento financeiro</h3>
    <div class="stats-grid">
      <div class="mini-box">
        <h4><i class="fas fa-piggy-bank" style="color:var(--primary);margin-right:6px;"></i>Guardar primeiro</h4>
        <p>Quem separa a reserva antes de gastar reduz o risco de comprometer a meta.</p>
      </div>
      <div class="mini-box">
        <h4><i class="fas fa-seedling" style="color:var(--success);margin-right:6px;"></i>Regularidade</h4>
        <p>Pequenos valores recorrentes produzem resultados mais consistentes do que grandes valores ocasionais.</p>
      </div>
      <div class="mini-box">
        <h4><i class="fas fa-fist-raised" style="color:var(--secondary);margin-right:6px;"></i>Disciplina</h4>
        <p>A continuidade do hábito costuma ser mais relevante do que a intensidade pontual.</p>
      </div>
      <div class="mini-box">
        <h4><i class="fas fa-calendar-check" style="color:var(--warning);margin-right:6px;"></i>Revisão mensal</h4>
        <p>Reveja a meta periodicamente para mantê-la coerente com sua realidade financeira.</p>
      </div>
    </div>
  </div>
</div>

<div id="earn-money-module" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h2><i class="fas fa-rocket" style="color:var(--secondary);margin-right:10px;"></i>Obter Dinheiro</h2>
    </div>
  </div>
  <div class="edu-section">
    <h3>Possibilidades práticas para estudantes</h3>
    <div class="stats-grid">
      <div class="tips-box"><h4><i class="fas fa-cookie-bite" style="color:var(--warning);margin-right:6px;"></i>Alimentação</h4><p>Trufas, brownies, bolo no pote, dindin e lanches simples.</p></div>
      <div class="tips-box"><h4><i class="fas fa-mobile-alt" style="color:var(--primary);margin-right:6px;"></i>Internet</h4><p>Divulgação, encomendas, revenda e pequenos serviços online.</p></div>
      <div class="tips-box"><h4><i class="fas fa-pencil-ruler" style="color:var(--secondary);margin-right:6px;"></i>Habilidades</h4><p>Apresentações, convites digitais, organização e apoio escolar.</p></div>
      <div class="tips-box"><h4><i class="fas fa-hand-holding-heart" style="color:var(--danger);margin-right:6px;"></i>Serviços</h4><p>Cuidado com crianças, organização doméstica e apoio local.</p></div>
    </div>
  </div>
  <div class="money-grid">
    <div class="goal-box">
      <h3>Como começar com pouco recurso</h3>
      <div class="step-guide">
        <div class="step-item"><div class="step-content"><h5>Escolha algo simples</h5><p>Comece por uma atividade que você já sabe fazer ou tem condições de aprender rapidamente.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Teste em pequena escala</h5><p>Faça uma quantidade reduzida ou ofereça o serviço a um grupo inicial para validar a demanda.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Reinvista parte do resultado</h5><p>Direcione uma parcela do lucro para melhorar a estrutura ou ampliar a oferta.</p></div></div>
        <div class="step-item"><div class="step-content"><h5>Separe lucro e uso pessoal</h5><p>Evite misturar o dinheiro da atividade com seus gastos pessoais.</p></div></div>
      </div>
    </div>
    <div class="goal-box">
      <h3>Estrutura inicial de renda</h3>
      <p style="margin-bottom:12px;"><strong>Produto ou serviço:</strong> algo útil, acessível e com demanda real.</p>
      <p style="margin-bottom:12px;"><strong>Público:</strong> escola, bairro, comunidade, amigos e família.</p>
      <p style="margin-bottom:12px;"><strong>Objetivo:</strong> construir constância, não apenas gerar dinheiro imediato.</p>
      <p><strong>Princípio:</strong> vender bem também exige organizar bem.</p>
    </div>
  </div>
</div>

<div id="dreams-module" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h2><i class="fas fa-cloud" style="color:var(--secondary);margin-right:10px;"></i>Meus Objetivos</h2>
    </div>
  </div>

  <div class="dream-grid">
    <div class="dream-card">
      <h3><i class="fas fa-plus-circle" style="color:var(--primary);margin-right:8px;"></i>Cadastrar novo objetivo</h3>
      <input type="text" id="dream-name" class="input-field" placeholder="Ex.: Comprar um celular">
      <input type="number" id="dream-price" class="input-field" placeholder="Valor total do objetivo (R$)">
      <input type="number" id="dream-monthly" class="input-field" placeholder="Quanto pode guardar por mês? (R$)">
      <button class="btn-action" onclick="adicionarSonho()" style="margin-top:8px;"><i class="fas fa-plus" style="margin-right:6px;"></i>Adicionar objetivo</button>
      <div id="dream-add-response" style="display:none;margin-top:16px;" class="dream-response"></div>
    </div>
    <div class="dream-card">
      <h3><i class="fas fa-star" style="color:var(--warning);margin-right:8px;"></i>Por que isso importa?</h3>
      <p style="margin-bottom:14px;">Guardar dinheiro torna-se mais consistente quando existe um <strong>propósito claro</strong>.</p>
      <div style="padding:14px;border-radius:12px;background:rgba(255,255,255,.45);margin-bottom:10px;">
        <p><i class="fas fa-check" style="color:var(--success);margin-right:6px;"></i>Objetivos dão <strong>direção</strong> ao esforço de economizar.</p>
      </div>
      <div style="padding:14px;border-radius:12px;background:rgba(255,255,255,.45);margin-bottom:10px;">
        <p><i class="fas fa-check" style="color:var(--success);margin-right:6px;"></i>Ter um prazo estimado ajuda a <strong>manter o foco</strong>.</p>
      </div>
      <div style="padding:14px;border-radius:12px;background:rgba(255,255,255,.45);">
        <p><i class="fas fa-check" style="color:var(--success);margin-right:6px;"></i>Conquistas menores ajudam a sustentar metas maiores no futuro.</p>
      </div>
    </div>
  </div>

  <div class="edu-section dream-list">
    <h3><i class="fas fa-list" style="margin-right:8px;color:var(--primary);"></i>Lista de objetivos</h3>
    <div id="dreams-list"><p style="color:var(--text-light);">Nenhum objetivo foi adicionado até o momento.</p></div>
  </div>
</div>

<div id="simulator-module" class="container screen">
  <div class="module-header">
    <button onclick="irParaDash()" class="btn-small"><i class="fas fa-arrow-left"></i> Voltar</button>
    <div class="module-title-block">
      <h2><i class="fas fa-calculator" style="color:var(--secondary);margin-right:10px;"></i>Simulador Financeiro</h2>
    </div>
  </div>

  <div class="info-banner">
    <i class="fas fa-calculator"></i>
    <p>Utilize o simulador para visualizar <strong>quanto pode acumular</strong> ao guardar uma quantia com regularidade. Os resultados são calculados dinamicamente com base nos valores informados.</p>
  </div>

  <div class="sim-grid">
    <div class="sim-card">
      <h3><i class="fas fa-sliders-h" style="color:var(--primary);margin-right:8px;"></i>Configure a simulação</h3>
      <label style="font-weight:700;color:var(--text-main);display:block;margin-top:10px;margin-bottom:4px;">Quanto guardar por mês (R$)</label>
      <input type="number" id="sim-valor" class="input-field" placeholder="Ex.: 50" oninput="atualizarSimulacaoAoVivo()">
      <label style="font-weight:700;color:var(--text-main);display:block;margin-bottom:4px;">Por quantos meses</label>
      <input type="number" id="sim-meses" class="input-field" placeholder="Ex.: 12" oninput="atualizarSimulacaoAoVivo()">
      <label style="font-weight:700;color:var(--text-main);display:block;margin-bottom:4px;">Taxa de rendimento (% ao mês)</label>
      <input type="number" id="sim-taxa" class="input-field" placeholder="0 = sem rendimento. Ex.: 0,5" oninput="atualizarSimulacaoAoVivo()" step="0.1">
      <button class="btn-action" onclick="simularGuardado()" style="margin-top:12px;"><i class="fas fa-play" style="margin-right:6px;"></i>Simular</button>
    </div>

    <div class="sim-card">
      <h3><i class="fas fa-chart-line" style="color:var(--secondary);margin-right:8px;"></i>Prévia em tempo real</h3>
      <div id="sim-preview" style="text-align:center;padding:20px;color:var(--text-light);">
        <i class="fas fa-calculator" style="font-size:2.5rem;margin-bottom:12px;display:block;"></i>
        Preencha os campos ao lado para ver a prévia.
      </div>
      <div id="sim-preview-result" style="display:none;">
        <div class="sim-result-big" id="sim-prev-val">R$ 0,00</div>
        <p style="color:var(--text-light);margin-top:8px;" id="sim-prev-desc">—</p>
      </div>
    </div>
  </div>

  <div class="sim-result-box" id="sim-result-box">
    <h3><i class="fas fa-chart-bar" style="color:var(--primary);margin-right:8px;"></i>Resultado da simulação</h3>
    <div class="sim-result-big" id="sim-total-final">R$ 0,00</div>
    <p id="sim-desc-final" style="margin-top:8px;color:var(--text-soft);"></p>
    <div class="sim-timeline" id="sim-timeline"></div>
    <div class="sim-goals-check" id="sim-goals-check"></div>
  </div>
</div>

<div id="toast-container"></div>

</body>
</html>
<script>
// =========================================================
// I.MAT — JavaScript completo (auth, módulos, funcionalidades)
// =========================================================

// ---------- UTILITÁRIOS ----------
const fmt = v => 'R$ ' + parseFloat(v||0).toFixed(2).replace('.',',').replace(/\B(?=(\d{3})+(?!\d))/g,'.');
const parseVal = s => parseFloat((s||'0').replace(/[^\d,.-]/g,'').replace(',','.')) || 0;

function mostrarToast(msg, tipo='info'){
  const c = document.getElementById('toast-container');
  const t = document.createElement('div');
  t.className = `toast ${tipo}`;
  const icones = {success:'fa-check-circle',error:'fa-times-circle',info:'fa-info-circle',warning:'fa-exclamation-triangle'};
  t.innerHTML = `<i class="fas ${icones[tipo]||'fa-info-circle'}"></i><span>${msg}</span>`;
  c.appendChild(t);
  setTimeout(()=>{t.style.animation='toastOut .35s ease forwards';setTimeout(()=>t.remove(),360);},3200);
}

function mostrarMensagem(msg, tipo){
  const el = document.getElementById('auth-message');
  el.className = 'auth-msg ' + tipo;
  el.textContent = msg;
  el.style.display = 'block';
}

// ---------- AUTH ----------
function alternarAba(aba){
  document.getElementById('login-form').style.display = aba==='login'?'block':'none';
  document.getElementById('register-form').style.display = aba==='register'?'block':'none';
  document.getElementById('tab-login').classList.toggle('active', aba==='login');
  document.getElementById('tab-register').classList.toggle('active', aba==='register');
  document.getElementById('auth-message').style.display = 'none';
}

function toggleSenha(id, icon){
  const inp = document.getElementById(id);
  if(inp.type==='password'){inp.type='text';icon.classList.replace('fa-eye','fa-eye-slash');}
  else{inp.type='password';icon.classList.replace('fa-eye-slash','fa-eye');}
}

function criarConta(){
  const nome = document.getElementById('register-nome').value.trim();
  const email = document.getElementById('register-email').value.trim().toLowerCase();
  const senha = document.getElementById('register-senha').value;
  const confirmar = document.getElementById('register-confirmar').value;

  if(!nome){ mostrarMensagem('Por favor, informe seu nome.','error'); return; }
  if(!email || !email.includes('@')){ mostrarMensagem('Informe um e-mail válido.','error'); return; }
  if(senha.length < 6){ mostrarMensagem('A senha deve ter pelo menos 6 caracteres.','error'); return; }
  if(senha !== confirmar){ mostrarMensagem('As senhas não coincidem.','error'); return; }

  let users = JSON.parse(localStorage.getItem('imat_users')||'{}');
  if(users[email]){ mostrarMensagem('Este e-mail já está cadastrado. Faça login.','warning'); return; }

  users[email] = { nome, senha };
  localStorage.setItem('imat_users', JSON.stringify(users));
  mostrarMensagem(`Conta criada com sucesso! Bem-vindo(a), ${nome}! 🎉`,'success');
  setTimeout(()=>{ alternarAba('login'); document.getElementById('login-email').value = email; }, 1400);
}

function validarAcesso(){
  const email = document.getElementById('login-email').value.trim().toLowerCase();
  const senha = document.getElementById('login-senha').value;

  if(!email || !senha){ mostrarMensagem('Preencha e-mail e senha.','error'); return; }

  let users = JSON.parse(localStorage.getItem('imat_users')||'{}');
  if(!users[email]){ mostrarMensagem('E-mail não encontrado. Crie uma conta primeiro.','error'); return; }
  if(users[email].senha !== senha){ mostrarMensagem('Senha incorreta. Tente novamente.','error'); return; }

  localStorage.setItem('imat_current_user', email);
  iniciarDashboard(users[email].nome, email);
}

function iniciarDashboard(nome, email){
  document.getElementById('login-screen').style.display = 'none';
  mostrarTela('main-dashboard');
  const ini = nome.charAt(0).toUpperCase();
  document.getElementById('profile-avatar').textContent = ini;
  document.getElementById('welcome-user').textContent = `Olá, ${nome}!`;
  carregarDados();
  trocarFrase();
  mostrarToast(`Bem-vindo(a), ${nome}! 👋`, 'success');
}

function logout(){
  if(!confirm('Deseja sair da sua conta?')) return;
  localStorage.removeItem('imat_current_user');
  location.reload();
}

function excluirConta(){
  if(!confirm('Tem certeza que deseja excluir sua conta? Esta ação não pode ser desfeita.')) return;
  const email = localStorage.getItem('imat_current_user');
  let users = JSON.parse(localStorage.getItem('imat_users')||'{}');
  delete users[email];
  localStorage.setItem('imat_users', JSON.stringify(users));
  localStorage.removeItem('imat_current_user');
  localStorage.removeItem('imat_data_'+email);
  mostrarToast('Conta excluída.','info');
  setTimeout(()=>location.reload(), 1000);
}

function abrirRecuperarSenha(){
  const emailInput = prompt('Informe seu e-mail cadastrado:');
  if(!emailInput) return;
  const email = emailInput.trim().toLowerCase();
  let users = JSON.parse(localStorage.getItem('imat_users')||'{}');
  if(!users[email]){ mostrarToast('E-mail não encontrado.','error'); return; }
  mostrarToast(`Senha da conta "${email}": ${users[email].senha}`,'info');
}

// ---------- NAVEGAÇÃO ----------
function mostrarTela(id){
  document.querySelectorAll('.screen').forEach(s=>s.style.display='none');
  const el = document.getElementById(id);
  if(el){ el.style.display='block'; window.scrollTo(0,0); }
}

function abrirModulo(id){ mostrarTela(id); }
function irParaDash(){ mostrarTela('main-dashboard'); atualizarHero(); }

function mostrarTab(modulo, tab, e){
  const prefix = modulo+'-tab-';
  document.querySelectorAll(`[id^="${prefix}"]`).forEach(el=>el.style.display='none');
  const target = document.getElementById(prefix+tab);
  if(target) target.style.display='block';
  if(e && e.currentTarget){
    e.currentTarget.closest('.nav-tabs').querySelectorAll('.nav-tab').forEach(b=>b.classList.remove('active'));
    e.currentTarget.classList.add('active');
  }
}

// ---------- FRASES MOTIVACIONAIS ----------
const frases = [
  'Quem controla o dinheiro, controla o futuro.',
  'Uma pequena economia hoje é uma grande liberdade amanhã.',
  'Organização financeira começa com consciência.',
  'Gastar menos do que se ganha é o primeiro passo.',
  'Sonhos viram planos quando se calcula o caminho.',
  'O hábito de poupar cria oportunidades.',
  'Dinheiro bem gerido é dinheiro multiplicado.',
  'Cada real poupado é uma decisão de autonomia.'
];
let fraseIdx = 0;
function trocarFrase(){
  fraseIdx = (fraseIdx+1) % frases.length;
  const el = document.getElementById('frase-motivacional');
  if(el) el.textContent = frases[fraseIdx];
}

// ---------- DADOS PERSISTENTES ----------
function getEmail(){ return localStorage.getItem('imat_current_user')||'guest'; }
function getDados(){
  return JSON.parse(localStorage.getItem('imat_data_'+getEmail())||'{"registros":[],"meta":0,"sonhos":[]}');
}
function salvarDados(d){ localStorage.setItem('imat_data_'+getEmail(), JSON.stringify(d)); }

function carregarDados(){
  renderizarPlanilha();
  calcularTotais();
  atualizarHero();
  carregarSonhos();
}

// ---------- HERO STATS ----------
function atualizarHero(){
  const d = getDados();
  const ganhos = d.registros.filter(r=>r.tipo==='ganho').reduce((a,r)=>a+r.valor,0);
  const gastos = d.registros.filter(r=>r.tipo==='gasto').reduce((a,r)=>a+r.valor,0);
  const saldo = ganhos - gastos;
  document.getElementById('hero-saldo').textContent = fmt(saldo);
  document.getElementById('hero-saldo-status').textContent = saldo>=0?'Positivo 🟢':'Negativo 🔴';
  document.getElementById('hero-ganhos').textContent = fmt(ganhos);
  document.getElementById('hero-gastos').textContent = fmt(gastos);
  const meta = d.meta || 0;
  document.getElementById('hero-meta').textContent = fmt(meta);
  const pct = meta>0?Math.min(100,Math.round(saldo/meta*100)):0;
  document.getElementById('hero-meta-pct').textContent = meta>0?pct+'% da meta atingida':'-';
  // ring
  if(document.getElementById('progress-ring')){
    document.getElementById('progress-no-data').style.display = ganhos>0?'none':'block';
    document.getElementById('progress-ring-area').style.display = ganhos>0?'block':'none';
    if(ganhos>0){
      const ringPct = meta>0?Math.min(100,Math.round(saldo/meta*100)):Math.round(saldo/(ganhos)*100);
      document.getElementById('ring-percent').textContent = ringPct+'%';
      document.getElementById('progress-ring').style.background =
        `conic-gradient(var(--primary) 0deg, var(--primary) ${ringPct*3.6}deg, rgba(255,255,255,.25) ${ringPct*3.6}deg)`;
      document.getElementById('quanto-falta').textContent = meta>0
        ? (saldo>=meta?'Meta atingida! 🎉':fmt(meta-saldo)+' para sua meta')
        : fmt(saldo)+' acumulado';
      document.getElementById('situacao-meta').textContent = meta>0&&saldo>=meta?'Parabéns! Objetivo alcançado!':'Continue guardando!';
    }
  }
}

// ---------- PLANILHA ----------
function adicionarLinhaGanho(){ adicionarLinha('ganho'); }
function adicionarLinhaGasto(){ adicionarLinha('gasto'); }

function adicionarLinha(tipo){
  const d = getDados();
  d.registros.push({id:Date.now(), tipo, desc:'', valor:0});
  salvarDados(d);
  renderizarPlanilha();
  calcularTotais();
}

function removerLinha(id){
  const d = getDados();
  d.registros = d.registros.filter(r=>r.id!==id);
  salvarDados(d);
  renderizarPlanilha();
  calcularTotais();
  mostrarToast('Registro removido.','info');
}

function onChangeRegistro(id, campo, valor){
  const d = getDados();
  const r = d.registros.find(r=>r.id===id);
  if(!r) return;
  if(campo==='desc') r.desc = valor;
  if(campo==='valor') r.valor = parseFloat(valor)||0;
  salvarDados(d);
  calcularTotais();
  atualizarHero();
}

function renderizarPlanilha(){
  const d = getDados();
  const tbody = document.getElementById('sheet-body');
  if(!tbody) return;
  tbody.innerHTML = '';
  if(d.registros.length===0){
    tbody.innerHTML = '<tr><td colspan="4" style="text-align:center;color:var(--text-light);padding:20px;">Nenhum registro. Clique em + Ganho ou + Gasto para começar.</td></tr>';
    return;
  }
  d.registros.forEach(r=>{
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td><input type="text" class="input-field" value="${r.desc}" placeholder="Descrição"
        onchange="onChangeRegistro(${r.id},'desc',this.value)" style="margin:0;padding:8px;"></td>
      <td><span style="padding:4px 10px;border-radius:8px;font-size:.8rem;font-weight:700;
        background:${r.tipo==='ganho'?'rgba(47,124,97,.12)':'rgba(184,75,75,.12)'};
        color:${r.tipo==='ganho'?'var(--success)':'var(--danger)'};">
        ${r.tipo==='ganho'?'Ganho':'Gasto'}</span></td>
      <td><input type="number" class="input-field" value="${r.valor}"
        onchange="onChangeRegistro(${r.id},'valor',this.value)" style="margin:0;padding:8px;min-width:100px;"></td>
      <td><button class="btn-small btn-danger" onclick="removerLinha(${r.id})"><i class="fas fa-trash"></i></button></td>`;
    tbody.appendChild(tr);
  });
}

function calcularTotais(){
  const d = getDados();
  const ganhos = d.registros.filter(r=>r.tipo==='ganho').reduce((a,r)=>a+r.valor,0);
  const gastos = d.registros.filter(r=>r.tipo==='gasto').reduce((a,r)=>a+r.valor,0);
  const saldo = ganhos-gastos;
  const nG = d.registros.filter(r=>r.tipo==='ganho').length;
  const nGasto = d.registros.filter(r=>r.tipo==='gasto').length;

  const set = (id,val)=>{ const el=document.getElementById(id); if(el) el.textContent=val; };
  set('fo-saldo', fmt(saldo));
  set('fo-saldo-status', saldo>0?'Positivo 🟢':saldo<0?'Negativo 🔴':'Neutro');
  set('fo-ganhos', fmt(ganhos));
  set('fo-gastos', fmt(gastos));
  set('fo-n-ganhos', nG+' registro(s)');
  set('fo-n-gastos', nGasto+' registro(s)');
  const ecoPct = ganhos>0?Math.round((saldo/ganhos)*100):0;
  set('fo-economia-pct', ecoPct+'%');
  set('saldo-total', 'Saldo atual: '+fmt(saldo));
  set('ganhos-label', fmt(ganhos));
  set('gastos-label', fmt(gastos));
  set('economia-label', fmt(Math.max(0,saldo)));

  const maxBar = Math.max(ganhos,gastos,1);
  const bar = (id,val)=>{ const el=document.getElementById(id); if(el) el.style.width=Math.round(val/maxBar*100)+'%'; };
  bar('bar-ganhos',ganhos); bar('bar-gastos',gastos); bar('bar-economia',Math.max(0,saldo));

  const dicaEl = document.getElementById('fo-dica-saldo');
  if(dicaEl){
    dicaEl.style.display = 'block';
    if(saldo<0) dicaEl.innerHTML='<i class="fas fa-exclamation-triangle" style="color:var(--danger);margin-right:6px;"></i>Seus gastos superam os ganhos. Revise seus registros.';
    else if(ecoPct>=20) dicaEl.innerHTML='<i class="fas fa-check-circle" style="color:var(--success);margin-right:6px;"></i>Ótimo! Você está economizando '+ecoPct+'% da renda.';
    else dicaEl.innerHTML='<i class="fas fa-lightbulb" style="color:var(--warning);margin-right:6px;"></i>Tente aumentar sua economia para pelo menos 20% da renda.';
  }
  atualizarHero();
  atualizarMeta();
}

// ---------- META ----------
function salvarMeta(){
  const v = parseFloat(document.getElementById('meta-valor').value)||0;
  if(v<=0){ mostrarToast('Informe um valor válido para a meta.','warning'); return; }
  const d = getDados(); d.meta=v; salvarDados(d);
  mostrarToast('Meta salva: '+fmt(v),'success');
  atualizarMeta(); atualizarHero();
}
function limparMeta(){
  const d = getDados(); d.meta=0; salvarDados(d);
  atualizarMeta(); atualizarHero(); mostrarToast('Meta removida.','info');
}
function atualizarMeta(){
  const d = getDados();
  const meta = d.meta||0;
  const ganhos = d.registros.filter(r=>r.tipo==='ganho').reduce((a,r)=>a+r.valor,0);
  const gastos = d.registros.filter(r=>r.tipo==='gasto').reduce((a,r)=>a+r.valor,0);
  const saldo = ganhos-gastos;
  const pct = meta>0?Math.min(100,Math.round(saldo/meta*100)):0;
  const set=(id,v)=>{const el=document.getElementById(id);if(el)el.textContent=v;};
  set('meta-atual', fmt(meta));
  set('meta-progresso-texto','Progresso: '+pct+'%');
  const fill=document.getElementById('meta-fill'); if(fill) fill.style.width=pct+'%';
  // insights
  const ins=document.getElementById('income-insights'); if(ins) ins.style.display=ganhos>0?'block':'none';
  const grid=document.getElementById('insight-grid-content');
  if(grid&&ganhos>0){
    const diasParaMeta = meta>0&&saldo<meta&&saldo>0?Math.ceil((meta-saldo)/(saldo/30)):null;
    grid.innerHTML=`
      <div class="insight-item"><div class="ii-val">${fmt(saldo)}</div><div class="ii-label">Saldo disponível</div></div>
      <div class="insight-item"><div class="ii-val">${pct}%</div><div class="ii-label">Da meta atingida</div></div>
      <div class="insight-item"><div class="ii-val">${fmt(Math.max(0,meta-saldo))}</div><div class="ii-label">Falta para a meta</div></div>
      ${diasParaMeta?`<div class="insight-item"><div class="ii-val">~${diasParaMeta} dias</div><div class="ii-label">Estimativa para atingir</div></div>`:''}`;
  }
}

// ---------- POTES ----------
function calcularPotes(){
  const renda = parseFloat(document.getElementById('potes-renda').value)||0;
  const modelo = document.getElementById('potes-modelo').value;
  const [p1,p2,p3] = modelo.split('-').map(Number);
  const v1=renda*p1/100, v2=renda*p2/100, v3=renda*p3/100;
  ['pot1','pot2','pot3'].forEach((id,i)=>{
    const v=[v1,v2,v3][i], p=[p1,p2,p3][i];
    document.getElementById(id+'-pct').textContent=p+'%';
    document.getElementById(id+'-val').value=fmt(v);
    const bar=document.getElementById(id+'-bar');
    bar.style.width=p+'%'; bar.textContent=p+'%';
  });
  if(renda>0){
    document.getElementById('potes-resultado').style.display='block';
    document.getElementById('potes-resultado-content').innerHTML=`
      <p>Com renda de <strong>${fmt(renda)}</strong> e modelo <strong>${modelo}</strong>:</p>
      <ul style="margin-top:10px;padding-left:18px;">
        <li style="margin:6px 0;"><strong>Essencial (${p1}%):</strong> ${fmt(v1)}</li>
        <li style="margin:6px 0;"><strong>Futuro/Meta (${p2}%):</strong> ${fmt(v2)}</li>
        <li style="margin:6px 0;"><strong>Lazer/Pessoal (${p3}%):</strong> ${fmt(v3)}</li>
      </ul>`;
  }
}

// ---------- CHECKLIST ----------
function toggleChecklist(el, tipo){
  const cb = el.querySelector('input');
  cb.checked = !cb.checked;
  el.classList.toggle('checked', cb.checked);
  if(!cb.checked) return;
  const msgs = {
    lanche:'Prepare lanches em casa sempre que possível. A diferença mensal pode ser significativa.',
    gastos:'Anote todos os pequenos gastos. O que parece irrelevante, acumulado, pesa no orçamento.',
    promocao:'Promoção não justifica uma compra desnecessária. Pergunte se você compraria pelo preço normal.',
    pagamentos:'Atrasos geram multas e juros. Mantenha uma agenda com vencimentos.'
  };
  mostrarToast(msgs[tipo]||'Dica registrada!','info');
}

// ---------- SONHOS (OBJETIVOS) ----------
function adicionarSonho(){
  const nome = document.getElementById('dream-name').value.trim();
  const preco = parseFloat(document.getElementById('dream-price').value)||0;
  const mensal = parseFloat(document.getElementById('dream-monthly').value)||0;
  if(!nome){ mostrarToast('Informe o nome do objetivo.','warning'); return; }
  if(preco<=0){ mostrarToast('Informe o valor do objetivo.','warning'); return; }
  const d = getDados();
  const meses = mensal>0?Math.ceil(preco/mensal):null;
  const sonho = {id:Date.now(), nome, preco, mensal, meses};
  d.sonhos.push(sonho);
  salvarDados(d);
  // feedback
  const resp = document.getElementById('dream-add-response');
  resp.style.display='block';
  resp.innerHTML=`<h4><i class="fas fa-star" style="color:var(--warning);"></i> Objetivo adicionado!</h4>
    <div class="stat-row">
      <div class="dream-stat"><div class="ds-val">${fmt(preco)}</div><div class="ds-label">Valor total</div></div>
      ${mensal>0?`<div class="dream-stat"><div class="ds-val">${fmt(mensal)}/mês</div><div class="ds-label">Economia mensal</div></div>`:''}
      ${meses?`<div class="dream-stat"><div class="ds-val">${meses} mes${meses>1?'es':''}</div><div class="ds-label">Estimativa</div></div>`:''}
    </div>`;
  document.getElementById('dream-name').value='';
  document.getElementById('dream-price').value='';
  document.getElementById('dream-monthly').value='';
  carregarSonhos();
  mostrarToast('Objetivo "'+nome+'" adicionado! 🎯','success');
}

function carregarSonhos(){
  const d = getDados();
  const cont = document.getElementById('dreams-list');
  if(!cont) return;
  if(!d.sonhos||d.sonhos.length===0){
    cont.innerHTML='<p style="color:var(--text-light);">Nenhum objetivo foi adicionado até o momento.</p>';
    return;
  }
  const ganhos = d.registros.filter(r=>r.tipo==='ganho').reduce((a,r)=>a+r.valor,0);
  const gastos = d.registros.filter(r=>r.tipo==='gasto').reduce((a,r)=>a+r.valor,0);
  const saldo = ganhos-gastos;
  cont.innerHTML = d.sonhos.map(s=>{
    const pct = Math.min(100, Math.round(saldo/s.preco*100));
    return `<div class="dream-item">
      <div class="dream-top">
        <div>
          <strong style="font-size:1.05rem;">${s.nome}</strong>
          <div class="dream-price" style="margin-top:4px;">${fmt(s.preco)}</div>
        </div>
        <div style="display:flex;flex-direction:column;align-items:flex-end;gap:6px;">
          <span style="font-weight:700;color:var(--primary);">${pct}% guardado</span>
          <button class="btn-small btn-danger" onclick="removerSonho(${s.id})"><i class="fas fa-trash"></i></button>
        </div>
      </div>
      <div class="goal-progress" style="margin-top:12px;">
        <div class="goal-fill" style="width:${pct}%"></div>
      </div>
      ${s.meses?`<p style="font-size:.82rem;color:var(--text-light);margin-top:8px;">⏱ Estimativa: ~${s.meses} meses guardando ${fmt(s.mensal)}/mês</p>`:''}
    </div>`;
  }).join('');
}

function removerSonho(id){
  const d = getDados();
  d.sonhos = d.sonhos.filter(s=>s.id!==id);
  salvarDados(d);
  carregarSonhos();
  mostrarToast('Objetivo removido.','info');
}

// ---------- SIMULADOR ----------
function atualizarSimulacaoAoVivo(){
  const v = parseFloat(document.getElementById('sim-valor').value)||0;
  const m = parseInt(document.getElementById('sim-meses').value)||0;
  const t = parseFloat(document.getElementById('sim-taxa').value)||0;
  const prev = document.getElementById('sim-preview');
  const prevRes = document.getElementById('sim-preview-result');
  if(v>0&&m>0){
    prev.style.display='none'; prevRes.style.display='block';
    let acc=0;
    for(let i=0;i<m;i++) acc=(acc+v)*(1+t/100);
    document.getElementById('sim-prev-val').textContent=fmt(acc);
    document.getElementById('sim-prev-desc').textContent=`Guardando ${fmt(v)}/mês por ${m} meses${t>0?' com '+t+'%/mês':''}`;
  } else {
    prev.style.display='block'; prevRes.style.display='none';
  }
}

function simularGuardado(){
  const v = parseFloat(document.getElementById('sim-valor').value)||0;
  const m = parseInt(document.getElementById('sim-meses').value)||0;
  const t = parseFloat(document.getElementById('sim-taxa').value)||0;
  if(v<=0||m<=0){ mostrarToast('Preencha valor e meses.','warning'); return; }

  let acc=0;
  const marcos=[];
  for(let i=1;i<=m;i++){
    acc=(acc+v)*(1+t/100);
    if(i===1||i===Math.round(m/4)||i===Math.round(m/2)||i===Math.round(m*3/4)||i===m)
      marcos.push({mes:i,val:acc});
  }

  const box = document.getElementById('sim-result-box');
  box.classList.add('show');
  document.getElementById('sim-total-final').textContent=fmt(acc);
  document.getElementById('sim-desc-final').textContent=`Total acumulado em ${m} meses${t>0?' com rendimento de '+t+'%/mês':''}`;

  const timeline=document.getElementById('sim-timeline');
  timeline.innerHTML=marcos.map(p=>`<div class="sim-step"><div class="ss-val">${fmt(p.val)}</div><div class="ss-label">Mês ${p.mes}</div></div>`).join('');

  // verificar sonhos alcançáveis
  const d = getDados();
  const check = document.getElementById('sim-goals-check');
  if(d.sonhos&&d.sonhos.length>0){
    check.innerHTML='<h4 style="color:var(--primary);margin-bottom:10px;"><i class="fas fa-bullseye" style="margin-right:6px;"></i>Seus objetivos nesta simulação</h4>'+
      d.sonhos.map(s=>{
        const ok=acc>=s.preco;
        return `<div class="sim-goal-row ${ok?'reachable':'not-reachable'}">
          <span>${s.nome}</span>
          <span style="font-weight:700;">${fmt(s.preco)} ${ok?'✅':'❌'}</span>
        </div>`;
      }).join('');
  } else check.innerHTML='';
  mostrarToast('Simulação concluída!','success');
}

// ---------- IMPULSO ----------
const cenarios = [
  {s:'Você recebe sua mesada e, ao passar pela cantina, vê um lanche especial por R$ 12,00. Você ainda não almoçou.', r:'necessidade', dica:'Alimentação básica é uma necessidade real. Porém, avalie se o valor é compatível com seu orçamento.'},
  {s:'Um amigo convida para um jogo de videogame online por assinatura mensal de R$ 25,00. Você já tem outra assinatura de streaming.', r:'desejo', dica:'Acumular assinaturas sem necessidade gera gastos recorrentes. Avalie o real uso de cada uma.'},
  {s:'Você percebe que seu caderno de anotações acabou e precisa dele para as aulas.', r:'necessidade', dica:'Material escolar essencial é uma necessidade. Busque opções de menor custo quando possível.'},
  {s:'Na loja, você encontra um tênis de marca com 30% de desconto, mas ainda assim fora do orçamento.', r:'desejo', dica:'Desconto não torna uma compra desnecessária em necessidade. O valor do produto ainda é relevante.'},
  {s:'Seu transporte para a escola está comprometido e você precisa pagar uma condução alternativa.', r:'necessidade', dica:'Mobilidade para compromissos essenciais é uma necessidade básica.'},
  {s:'Você quer comprar um item decorativo para o quarto que viu em uma loja online.', r:'desejo', dica:'Itens decorativos são desejos. Considere incluí-los na parte de lazer do orçamento, se houver espaço.'}
];
let impulsoIdx=0, impulsoAcertos=0, impulsoErros=0;

function carregarCenario(){
  if(impulsoIdx>=cenarios.length){ mostrarResultadoImpulso(); return; }
  const c=cenarios[impulsoIdx];
  document.getElementById('impulse-scenario').textContent=c.s;
  document.getElementById('impulse-counter').textContent=`Situação ${impulsoIdx+1} de ${cenarios.length}`;
  document.getElementById('impulse-pbar').style.width=(impulsoIdx/cenarios.length*100)+'%';
  document.getElementById('impulse-feedback').style.display='none';
  document.getElementById('impulse-feedback').className='impulse-feedback';
  document.getElementById('impulse-next-btn').style.display='none';
  document.querySelectorAll('.impulse-choice-btn').forEach(b=>b.disabled=false);
}

function responderImpulso(resp){
  const c=cenarios[impulsoIdx];
  const ok=resp===c.r;
  if(ok) impulsoAcertos++; else impulsoErros++;
  document.getElementById('impulse-acertos').textContent='Acertos: '+impulsoAcertos;
  document.getElementById('impulse-erros').textContent='Erros: '+impulsoErros;
  const fb=document.getElementById('impulse-feedback');
  fb.className='impulse-feedback show '+(ok?'good':'bad');
  fb.innerHTML=`<h4>${ok?'<i class="fas fa-check-circle" style="color:var(--success);"></i> Correto!':'<i class="fas fa-times-circle" style="color:var(--danger);"></i> Atenção!'}</h4><p>${c.dica}</p>`;
  document.getElementById('impulse-next-btn').style.display='block';
  document.querySelectorAll('.impulse-choice-btn').forEach(b=>b.disabled=true);
}

function proximoImpulso(){ impulsoIdx++; carregarCenario(); }

function mostrarResultadoImpulso(){
  document.querySelector('.impulse-card').style.display='none';
  const res=document.getElementById('impulse-result');
  res.style.display='block';
  document.getElementById('impulse-final-score').textContent=`${impulsoAcertos}/${cenarios.length}`;
  const msgs=['Continue praticando! A consciência financeira se desenvolve com o tempo.','Bom resultado! Você já identifica bem a maioria das situações.','Excelente! Você demonstra ótima consciência financeira!'];
  const idx = impulsoAcertos<=2?0:impulsoAcertos<=4?1:2;
  document.getElementById('impulse-final-msg').textContent=msgs[idx];
}

function reiniciarImpulso(){
  impulsoIdx=0; impulsoAcertos=0; impulsoErros=0;
  document.querySelector('.impulse-card').style.display='block';
  document.getElementById('impulse-result').style.display='none';
  document.getElementById('impulse-acertos').textContent='Acertos: 0';
  document.getElementById('impulse-erros').textContent='Erros: 0';
  carregarCenario();
}

// ---------- QUIZ ----------
const perguntas=[
  {q:'O que significa "poupar"?',ops:['Gastar tudo de uma vez','Guardar uma parte do dinheiro regularmente','Pedir emprestado','Ignorar os gastos'],c:1,exp:'Poupar significa reservar uma parte da renda antes de gastar, criando uma reserva para objetivos ou emergências.'},
  {q:'Qual é a principal diferença entre necessidade e desejo?',ops:['Não há diferença','Necessidade é essencial para viver; desejo é algo que queremos, mas não precisamos','Desejo é mais barato','Necessidade é opcional'],c:1,exp:'Necessidade é algo indispensável (alimentação, estudo, saúde). Desejo é uma vontade que pode ser adiada.'},
  {q:'O que é saldo financeiro?',ops:['O total de gastos do mês','O dinheiro guardado no banco','A diferença entre ganhos e gastos','O valor das contas a pagar'],c:2,exp:'Saldo é o resultado de subtrair os gastos totais dos ganhos totais. Saldo positivo indica controle financeiro.'},
  {q:'Por que é importante registrar todos os gastos?',ops:['Para impressionar as pessoas','Para saber exatamente para onde o dinheiro vai','Não é necessário','Apenas para gastos grandes'],c:1,exp:'Registrar gastos permite identificar excessos, padrões e oportunidades de economia.'},
  {q:'O que é uma meta financeira?',ops:['Uma dívida que se precisa pagar','Um objetivo específico com valor e prazo definidos','Um cartão de crédito','Uma forma de gastar mais'],c:1,exp:'Meta financeira é um objetivo claro com valor e prazo, como juntar R$500 em 3 meses.'},
  {q:'Qual hábito financeiro é mais recomendado?',ops:['Gastar tudo e poupar o que sobrar','Poupar primeiro e usar o restante com consciência','Ignorar pequenos gastos','Comprar sempre que há promoção'],c:1,exp:'O ideal é separar a reserva assim que receber a renda, antes de qualquer gasto.'},
  {q:'O que são gastos variáveis?',ops:['Contas com valor fixo todo mês','Despesas que mudam de valor a cada período','Apenas dívidas','Gastos apenas com lazer'],c:1,exp:'Gastos variáveis como alimentação, transporte e entretenimento mudam de valor a cada mês e exigem acompanhamento.'},
  {q:'Qual das opções representa uma atitude financeira consciente?',ops:['Comprar por impulso','Comparar preços antes de comprar','Ignorar o saldo da conta','Gastar mais do que ganha'],c:1,exp:'Comparar preços antes de comprar é uma prática fundamental da educação financeira.'}
];
let quizIdx=0, quizPontos=0;

function carregarPergunta(){
  if(quizIdx>=perguntas.length){ mostrarResultadoQuiz(); return; }
  const p=perguntas[quizIdx];
  document.getElementById('quiz-question').textContent=p.q;
  document.getElementById('quiz-counter').textContent=`Pergunta ${quizIdx+1} de ${perguntas.length}`;
  document.getElementById('quiz-score').textContent=quizPontos+' pontos';
  document.getElementById('quiz-pbar').style.width=(quizIdx/perguntas.length*100)+'%';
  document.getElementById('quiz-feedback').style.display='none';
  document.getElementById('quiz-feedback').className='quiz-feedback';
  document.getElementById('quiz-next-btn').style.display='none';
  const opts=document.getElementById('quiz-options');
  opts.innerHTML=p.ops.map((o,i)=>`<button class="quiz-option-btn" onclick="responderQuiz(${i})">${o}</button>`).join('');
}

function responderQuiz(idx){
  const p=perguntas[quizIdx];
  const ok=idx===p.c;
  if(ok) quizPontos++;
  document.getElementById('quiz-score').textContent=quizPontos+' pontos';
  document.querySelectorAll('.quiz-option-btn').forEach((b,i)=>{
    b.disabled=true;
    if(i===p.c) b.classList.add('correct');
    else if(i===idx&&!ok) b.classList.add('wrong');
  });
  const fb=document.getElementById('quiz-feedback');
  fb.className='quiz-feedback show '+(ok?'correct':'wrong');
  fb.innerHTML=`<strong>${ok?'✅ Correto!':'❌ Incorreto.'}</strong> ${p.exp}`;
  document.getElementById('quiz-next-btn').style.display='block';
}

function proximaPergunta(){ quizIdx++; carregarPergunta(); }

function mostrarResultadoQuiz(){
  document.querySelector('.quiz-card').style.display='none';
  const res=document.getElementById('quiz-result');
  res.style.display='block';
  document.getElementById('quiz-final-score').textContent=`${quizPontos}/${perguntas.length}`;
  const msgs=['Continue estudando! A educação financeira é uma jornada.','Bom resultado! Você já tem uma boa base financeira.','Parabéns! Você demonstra excelente conhecimento financeiro!'];
  document.getElementById('quiz-final-msg').textContent=msgs[quizPontos<=3?0:quizPontos<=6?1:2];
}

function reiniciarQuiz(){
  quizIdx=0; quizPontos=0;
  document.querySelector('.quiz-card').style.display='block';
  document.getElementById('quiz-result').style.display='none';
  carregarPergunta();
}

// ---------- HELPER PANEL ----------
function abrirPainel(titulo, subtitulo, iconClass, html){
  document.getElementById('helper-title').textContent=titulo;
  document.getElementById('helper-subtitle').textContent=subtitulo;
  document.getElementById('helper-icon').innerHTML=`<i class="${iconClass}"></i>`;
  document.getElementById('helper-content').innerHTML=html;
  document.getElementById('helper-overlay').style.display='block';
  document.getElementById('helper-panel').classList.add('open');
}
function fecharPainel(){
  document.getElementById('helper-overlay').style.display='none';
  document.getElementById('helper-panel').classList.remove('open');
}

// ---------- INICIALIZAÇÃO ----------
window.addEventListener('DOMContentLoaded', ()=>{
  // Verificar sessão
  const email = localStorage.getItem('imat_current_user');
  if(email){
    const users = JSON.parse(localStorage.getItem('imat_users')||'{}');
    if(users[email]) { iniciarDashboard(users[email].nome, email); return; }
  }
  mostrarTela('login-screen');
  document.getElementById('login-screen').style.display='flex';
  // Inicializar quizzes
  carregarCenario();
  carregarPergunta();
});
</script>
