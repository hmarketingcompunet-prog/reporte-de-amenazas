[index.html](https://github.com/user-attachments/files/26687666/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CompuNet — Reporte Semanal de Amenazas | 06/04/2026–12/04/2026</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg-deep:#080b14;--bg-card:#0f1422;--bg-card2:#141a2c;--border:#1c2438;
  --red:#e53935;--red-soft:#ff5252;--red-bg:rgba(229,57,53,0.12);
  --yellow:#f5a623;--yellow-bg:rgba(245,166,35,0.12);
  --green:#00c853;--green-bg:rgba(0,200,83,0.12);
  --blue:#2979ff;--blue-bg:rgba(41,121,255,0.10);
  --text:#e8ecf4;--text-muted:#6b7a99;--text-dim:#9aa3bb;--accent:#f5a623;
}
body{font-family:'Inter',-apple-system,BlinkMacSystemFont,sans-serif;background:var(--bg-deep);color:var(--text);font-size:14px;line-height:1.6;overflow-x:hidden}

/* -- LOGO COMPONENT (shared) -- */
.logo-block{display:flex;flex-direction:column;align-items:center;gap:0;line-height:1.1}
.logo-name{font-size:20px;font-weight:900;color:#fff;letter-spacing:-.3px;text-align:center}
.logo-tag{font-size:9px;font-weight:700;letter-spacing:.4px;text-align:center;display:block}
.logo-tag .hash{color:#f5a623}.logo-tag .rest{color:#fff}

/* -- TOPBAR -- */
.topbar{background:rgba(5,8,16,.97);border-bottom:1px solid var(--border);padding:10px 56px;
  display:flex;align-items:center;justify-content:space-between;
  position:sticky;top:0;z-index:200;backdrop-filter:blur(12px)}
.topbar-meta{display:flex;gap:20px;align-items:center}
.topbar-meta span{font-size:11px;color:var(--text-muted);letter-spacing:.5px;text-transform:uppercase}

/* -- PILLS -- */
.pill{display:inline-flex;align-items:center;gap:5px;padding:4px 11px;border-radius:20px;
  font-size:10px;font-weight:700;letter-spacing:.5px;text-transform:uppercase}
.pill.red   {background:var(--red-bg);   color:var(--red-soft);border:1px solid rgba(229,57,53,.3)}
.pill.yellow{background:var(--yellow-bg);color:var(--yellow);  border:1px solid rgba(245,166,35,.3)}
.pill.green {background:var(--green-bg); color:var(--green);   border:1px solid rgba(0,200,83,.3)}
.pill.blue  {background:var(--blue-bg);  color:var(--blue);    border:1px solid rgba(41,121,255,.3)}

/* -- COVER PAGE -- */
.cover-page{
  height:100vh;min-height:700px;
  background:linear-gradient(155deg,#04060e 0%,#08101e 45%,#060c1a 100%);
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  position:relative;overflow:hidden;
  border-bottom:3px solid var(--red-soft);
}
.cover-page canvas{position:absolute;inset:0;pointer-events:none;opacity:.22;z-index:0}
/* radial glows */
.cover-page::before{content:'';position:absolute;inset:0;pointer-events:none;z-index:1;
  background:radial-gradient(ellipse 60% 55% at 50% 50%,rgba(229,57,53,.07) 0%,transparent 70%),
             radial-gradient(ellipse 40% 40% at 15% 80%,rgba(41,121,255,.05) 0%,transparent 65%),
             radial-gradient(ellipse 35% 35% at 85% 20%,rgba(245,166,35,.04) 0%,transparent 60%)}
.cover-content{position:relative;z-index:2;text-align:center;max-width:860px;padding:0 40px}
.cover-logo-block{margin-bottom:36px}
.cover-logo-block .cn{font-size:42px;font-weight:900;color:#fff;letter-spacing:-1px;display:block;line-height:1}
.cover-logo-block .ct{font-size:14px;font-weight:700;letter-spacing:.5px;display:block;margin-top:4px;text-align:center}
.cover-logo-block .ct .hash{color:#f5a623}.cover-logo-block .ct .rest{color:#fff}
.cover-divider{width:60px;height:3px;background:var(--red-soft);border-radius:2px;margin:24px auto}
.cover-eyebrow{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:2.5px;
  color:var(--text-muted);margin-bottom:16px}
.cover-h1{font-size:68px;font-weight:900;line-height:.95;margin-bottom:8px;letter-spacing:-2px}
.cover-h1 .line1{color:#fff;display:block}
.cover-h1 .line2{color:var(--red-soft);display:block}
.cover-subtitle{font-size:16px;color:var(--text-dim);margin:20px 0 36px;line-height:1.6;max-width:560px;margin-left:auto;margin-right:auto}
.cover-badges{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:40px}
.cover-kpis{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;
  background:rgba(28,36,56,.8);border:1px solid var(--border);border-radius:12px;
  overflow:hidden;max-width:600px;margin:0 auto;backdrop-filter:blur(8px)}
.cover-kpi{background:rgba(15,20,34,.85);padding:18px 10px;text-align:center}
.cover-kpi .n{font-size:32px;font-weight:900;color:var(--accent)}
.cover-kpi .l{font-size:9px;text-transform:uppercase;letter-spacing:1px;color:var(--text-muted);margin-top:2px}
.cover-kpi .c{font-size:10px;font-weight:700;margin-top:3px}
.c.dn{color:var(--green)}.c.up{color:var(--red-soft)}
.cover-scroll{position:absolute;bottom:28px;left:50%;transform:translateX(-50%);
  font-size:10px;text-transform:uppercase;letter-spacing:2px;color:var(--text-muted);
  display:flex;flex-direction:column;align-items:center;gap:6px;z-index:2}
.cover-scroll svg{animation:bob 1.6s ease-in-out infinite}
@keyframes bob{0%,100%{transform:translateY(0)}50%{transform:translateY(5px)}}

/* -- RISK BANNER -- */
.risk-banner{background:linear-gradient(90deg,rgba(229,57,53,.13),rgba(229,57,53,.04));
  border-top:1px solid rgba(229,57,53,.18);border-bottom:1px solid rgba(229,57,53,.18);
  padding:12px 60px;display:flex;align-items:center;gap:14px;position:relative;z-index:1}
.risk-label{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1px;
  color:var(--text-muted);white-space:nowrap}
.risk-bar{display:flex;gap:4px;max-width:180px;flex:none}
.risk-seg{height:6px;border-radius:3px;flex:1;background:var(--border)}
.risk-seg.active.red   {background:var(--red-soft)}
.risk-seg.active.yellow{background:var(--yellow)}
.risk-note{font-size:12px;color:var(--text-dim)}.risk-note strong{color:var(--red-soft)}

/* -- SECTIONS -- */
.section{padding:56px 60px 0;position:relative;z-index:1}
.section-label{font-size:10px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--accent);margin-bottom:7px}
.section-title{font-size:26px;font-weight:800;color:var(--text);margin-bottom:5px;line-height:1.2}
.section-sub{font-size:13px;color:var(--text-muted);margin-bottom:28px}
.divider{height:1px;background:linear-gradient(90deg,transparent,var(--border) 20%,var(--border) 80%,transparent);margin:56px 60px 0}

/* -- CARDS -- */
.cards{display:grid;gap:18px}
.cards-2{grid-template-columns:repeat(2,1fr)}
.cards-3{grid-template-columns:repeat(3,1fr)}
.cards-4{grid-template-columns:repeat(4,1fr)}
.cards-6{grid-template-columns:repeat(6,1fr)}
.cards-2-1{grid-template-columns:2fr 1fr}
.cards-1-2{grid-template-columns:1fr 2fr}
.card{background:var(--bg-card);border:1px solid var(--border);border-radius:12px;padding:22px;position:relative;overflow:hidden}
.card::before{content:'';position:absolute;inset:0;border-radius:12px;
  background:radial-gradient(ellipse 80% 60% at 50% 0%,rgba(255,255,255,.015),transparent 70%);pointer-events:none}
.card.red-top   {border-top:2px solid var(--red-soft)}
.card.yellow-top{border-top:2px solid var(--yellow)}
.card.green-top {border-top:2px solid var(--green)}
.card.blue-top  {border-top:2px solid var(--blue)}
.card-label{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--text-muted);margin-bottom:7px}
.card-num{font-size:40px;font-weight:900;line-height:1;margin-bottom:5px}
.card-num.red{color:var(--red-soft)}.card-num.yellow{color:var(--yellow)}
.card-num.green{color:var(--green)}.card-num.white{color:var(--text)}
.card-sub{font-size:12px;color:var(--text-muted)}
.card-title{font-size:15px;font-weight:700;color:var(--text);margin-bottom:7px}
.card-body{font-size:13px;color:var(--text-dim);line-height:1.7}

/* -- BAR CHART -- */
.bar-chart{display:flex;align-items:flex-end;gap:5px;height:110px;margin:14px 0 7px}
.bar-col{display:flex;flex-direction:column;align-items:center;flex:1;height:100%;justify-content:flex-end;gap:3px}
.bar{border-radius:3px 3px 0 0;width:100%}
.bar.blue  {background:linear-gradient(180deg,#3d8eff,#2261cc)}
.bar.yellow{background:linear-gradient(180deg,#f5c842,#d4880a)}
.bar.red   {background:linear-gradient(180deg,#ff6b6b,#cc3333)}
.bar-lbl{font-size:8px;color:var(--text-muted);text-align:center}
.bar-val{font-size:8px;color:var(--text-dim);text-align:center}

/* -- DONUT -- */
.donut-wrap{display:flex;align-items:center;gap:18px}
.donut-legend{display:flex;flex-direction:column;gap:7px;flex:1}
.donut-leg-item{display:flex;align-items:center;gap:8px}
.donut-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0}
.donut-leg-name{font-size:12px;color:var(--text-dim);flex:1}
.donut-leg-pct{font-size:12px;font-weight:700;color:var(--text)}

/* -- RANK LIST -- */
.rank-list{display:flex;flex-direction:column;gap:7px}
.rank-item{display:flex;align-items:center;gap:10px;padding:10px 13px;
  background:var(--bg-card2);border-radius:8px;border:1px solid var(--border)}
.rank-num{font-size:11px;font-weight:800;color:var(--text-muted);width:20px;text-align:center}
.rank-name{font-size:13px;font-weight:700;color:var(--text);flex:1}
.rank-victims{font-size:17px;font-weight:900;color:var(--accent);width:34px;text-align:right}
.rank-change{font-size:10px;font-weight:700;width:58px;text-align:right}
.rank-change.up{color:var(--red-soft)}.rank-change.down{color:var(--green)}.rank-change.new{color:var(--yellow)}

/* -- PROG BARS -- */
.prog-list{display:flex;flex-direction:column;gap:12px}
.prog-header{display:flex;justify-content:space-between;margin-bottom:5px}
.prog-name{font-size:13px;font-weight:600;color:var(--text)}
.prog-meta{font-size:12px;color:var(--text-muted)}
.prog-bar-bg{height:6px;background:var(--border);border-radius:3px;overflow:hidden}
.prog-bar-fill{height:100%;border-radius:3px}

/* -- HIGHLIGHT -- */
.highlight{background:var(--bg-card2);border:1px solid var(--border);
  border-left:4px solid var(--red-soft);border-radius:8px;padding:18px 22px}
.highlight.yellow{border-left-color:var(--yellow)}
.highlight.green{border-left-color:var(--green)}

/* -- ALERT ROWS -- */
.alert-list{display:flex;flex-direction:column;gap:10px}
.alert-row{display:flex;gap:12px;align-items:flex-start;padding:15px;
  background:var(--bg-card2);border-radius:10px;border:1px solid var(--border)}
.alert-badge{flex-shrink:0;padding:3px 9px;border-radius:4px;font-size:9px;font-weight:800;
  letter-spacing:.5px;text-transform:uppercase;margin-top:2px}
.alert-badge.critica{background:rgba(229,57,53,.2);color:var(--red-soft);border:1px solid rgba(229,57,53,.3)}
.alert-badge.alta   {background:rgba(245,166,35,.15);color:var(--yellow);border:1px solid rgba(245,166,35,.3)}
.alert-badge.media  {background:rgba(41,121,255,.15);color:var(--blue);border:1px solid rgba(41,121,255,.3)}
.alert-badge.info   {background:rgba(107,122,153,.15);color:var(--text-muted);border:1px solid var(--border)}
.alert-content h4{font-size:13px;font-weight:700;color:var(--text);margin-bottom:4px}
.alert-content p {font-size:12px;color:var(--text-dim);line-height:1.65}
.rec-cta{font-size:11px;color:var(--accent);font-weight:600;margin-top:8px;
  padding:8px 12px;background:rgba(245,166,35,.06);border-radius:6px;
  border-left:3px solid var(--accent)}

/* -- TIMELINE -- */
.timeline{display:flex;flex-direction:column}
.tl-item{display:flex;gap:13px;align-items:flex-start;padding:10px 0;border-bottom:1px solid var(--border)}
.tl-item:last-child{border-bottom:none}
.tl-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0;margin-top:4px}
.tl-dot.red   {background:var(--red-soft);box-shadow:0 0 5px var(--red-soft)}
.tl-dot.yellow{background:var(--yellow);box-shadow:0 0 5px var(--yellow)}
.tl-dot.dim   {background:var(--text-muted)}
.tl-date{font-size:10px;color:var(--text-muted);font-weight:600;width:66px;flex-shrink:0;margin-top:2px}
.tl-text{font-size:12px;color:var(--text-dim);line-height:1.5}
.tl-text strong{color:var(--text)}

/* -- CHECKLIST -- */
.check-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
.check-item{display:flex;gap:10px;align-items:flex-start;padding:14px;
  background:var(--bg-card2);border-radius:10px;border:1px solid var(--border)}
.check-icon{font-size:15px;flex-shrink:0;margin-top:1px}
.check-text h5{font-size:13px;font-weight:700;color:var(--text);margin-bottom:3px}
.check-text p {font-size:12px;color:var(--text-muted);line-height:1.5}

/* -- CVE LIST -- */
.cve-list{display:flex;flex-direction:column;gap:8px}
.cve-item{display:flex;align-items:center;gap:13px;padding:11px 15px;
  background:var(--bg-card2);border-radius:8px;border:1px solid var(--border)}
.cve-id{font-size:11px;font-weight:800;color:var(--yellow);font-family:monospace;width:145px;flex-shrink:0}
.cve-prod{font-size:13px;font-weight:600;color:var(--text);flex:1}
.cve-prod small{display:block;font-size:11px;font-weight:400;color:var(--text-muted)}
.cve-groups{display:flex;gap:5px}

/* -- COUNTRY LIST -- */
.country-list{display:flex;flex-direction:column;gap:7px}
.country-item{display:flex;align-items:center;gap:10px;padding:7px 0;border-bottom:1px solid var(--border)}
.country-item:last-child{border-bottom:none}
.country-flag{font-size:17px;width:24px}
.country-name{font-size:13px;font-weight:600;color:var(--text);flex:1}
.country-bar-bg{flex:2;height:5px;background:var(--border);border-radius:3px;overflow:hidden}
.country-bar-fill{height:100%;border-radius:3px;background:linear-gradient(90deg,#2979ff,#7b2fff)}
.country-num{font-size:15px;font-weight:800;color:var(--accent);width:34px;text-align:right}
.country-chg{font-size:10px;font-weight:700;width:50px;text-align:right}

/* -- LATAM -- */
.latam-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.latam-country{padding:14px 17px;background:var(--bg-card2);border-radius:10px;
  border:1px solid var(--border);display:flex;align-items:center;gap:11px}
.latam-flag{font-size:22px}
.latam-info{flex:1}
.latam-info h4{font-size:13px;font-weight:700;color:var(--text);margin-bottom:1px}
.latam-info p{font-size:10px;color:var(--text-muted)}
.latam-ytd{font-size:20px;font-weight:900;color:var(--accent)}
.latam-thisweek{font-size:9px;font-weight:700;padding:2px 7px;border-radius:10px;
  background:var(--red-bg);color:var(--red-soft);border:1px solid rgba(229,57,53,.2)}

/* -- INSIGHT BOX -- */
.insight-box{background:linear-gradient(135deg,rgba(245,166,35,.06),rgba(245,166,35,.02));
  border:1px solid rgba(245,166,35,.2);border-radius:10px;padding:15px 18px}
.insight-box .ico{font-size:18px;margin-bottom:5px}
.insight-box h4{font-size:13px;font-weight:700;color:var(--yellow);margin-bottom:4px}
.insight-box p{font-size:12px;color:var(--text-dim);line-height:1.6}

/* -- TAGS -- */
.tag-list{display:flex;flex-wrap:wrap;gap:6px;margin-top:9px}
.tag{padding:4px 10px;border-radius:6px;font-size:11px;font-weight:600;
  background:var(--bg-card);border:1px solid var(--border);color:var(--text-dim)}
.tag.red   {background:var(--red-bg);   border-color:rgba(229,57,53,.3);color:var(--red-soft)}
.tag.yellow{background:var(--yellow-bg);border-color:rgba(245,166,35,.3);color:var(--yellow)}
.tag.green {background:var(--green-bg); border-color:rgba(0,200,83,.3);  color:var(--green)}

/* -- WORLD MAP -- */
.map-wrapper{background:var(--bg-card);border:1px solid var(--border);border-radius:12px;
  padding:24px;position:relative}
.map-title{font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;
  color:var(--text-muted);margin-bottom:16px}
.map-legend{display:flex;gap:20px;margin-top:14px;flex-wrap:wrap}
.map-leg-item{display:flex;align-items:center;gap:7px;font-size:11px;color:var(--text-muted)}
.map-leg-dot{width:10px;height:10px;border-radius:50%}
.map-tooltip{position:absolute;background:rgba(8,11,20,.95);border:1px solid var(--border);
  border-radius:8px;padding:8px 12px;font-size:11px;pointer-events:none;
  color:var(--text);z-index:10;display:none;white-space:nowrap;box-shadow:0 4px 16px rgba(0,0,0,.4)}
.map-tooltip strong{color:var(--accent)}

/* -- CTA -- */
.cta-section{margin:56px 60px 0;
  background:linear-gradient(135deg,#0c1020,#111a30);
  border:1px solid #1c2e50;border-top:3px solid var(--accent);
  border-radius:14px;padding:44px;
  display:grid;grid-template-columns:1fr 1fr;gap:36px;align-items:center;
  position:relative;z-index:1;overflow:hidden}
.cta-section::before{content:'';position:absolute;right:-60px;bottom:-60px;
  width:240px;height:240px;border-radius:50%;
  background:radial-gradient(circle,rgba(245,166,35,.06),transparent 70%)}
.cta-title{font-size:26px;font-weight:900;line-height:1.2;margin-bottom:10px}
.cta-title span{color:var(--accent)}
.cta-body{font-size:13px;color:var(--text-dim);line-height:1.7;margin-bottom:22px}
.services-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:24px}
.service-item{padding:11px 13px;background:rgba(245,166,35,.07);
  border:1px solid rgba(245,166,35,.2);border-radius:8px}
.service-item h5{font-size:11px;font-weight:700;color:var(--accent);margin-bottom:2px}
.service-item p{font-size:11px;color:var(--text-muted)}
.cta-btn{display:inline-block;padding:13px 28px;background:var(--accent);
  color:#000;font-weight:800;font-size:13px;border-radius:8px;text-decoration:none}
.contact-card{background:rgba(255,255,255,.03);border:1px solid var(--border);
  border-radius:10px;padding:24px}
.contact-card h4{font-size:10px;font-weight:700;color:var(--text-muted);
  text-transform:uppercase;letter-spacing:1.5px;margin-bottom:18px}
.contact-row{display:flex;gap:10px;align-items:center;margin-bottom:12px}
.contact-icon{font-size:15px;width:20px}
.contact-info h5{font-size:9px;font-weight:600;color:var(--text-muted);
  text-transform:uppercase;letter-spacing:.5px}
.contact-info p{font-size:13px;font-weight:600;color:var(--text)}
.contact-logo-block{margin-top:18px;padding:14px;
  background:rgba(245,166,35,.07);border-radius:8px;
  border:1px solid rgba(245,166,35,.2);text-align:center}
.contact-logo-block .cn{font-size:22px;font-weight:900;color:#fff}
.contact-logo-block .ct{font-size:10px;font-weight:700;margin-top:2px;
  display:block;text-align:center}
.contact-logo-block .ct .hash{color:#f5a623}
.contact-logo-block .ct .rest{color:#fff}
.contact-logo-block small{font-size:10px;color:var(--text-muted);display:block;margin-top:5px}

/* -- FOOTER -- */
.footer-strip{background:#03050d;border-top:1px solid var(--border);
  padding:14px 60px;display:flex;justify-content:space-between;align-items:center;
  margin-top:56px;position:relative;z-index:1}
.footer-logo{display:flex;flex-direction:column;align-items:center;gap:1px}
.footer-logo .fn{font-size:13px;font-weight:900;color:#fff}
.footer-logo .ft{font-size:8px;font-weight:700}
.footer-logo .ft .hash{color:var(--accent)}
.footer-logo .ft .rest{color:#fff}
.footer-strip .fmeta{display:flex;gap:20px}
.footer-strip .fmeta span{font-size:10px;color:var(--text-muted)}

/* -- UTILS -- */
.mt8{margin-top:8px}.mt10{margin-top:10px}.mt12{margin-top:12px}
.mt16{margin-top:16px}.mt20{margin-top:20px}
.text-center{text-align:center}
.big-num{font-size:48px;font-weight:900}

/* -- PRINT / PDF -- */
@media print {
  .cover-page{page-break-after:always;height:auto;min-height:100vh}
  .topbar{position:relative !important}
  .cover-scroll{display:none}
  .section{page-break-before:always;page-break-inside:avoid}
  .divider{display:none}
  .card{page-break-inside:avoid}
  .cta-section{page-break-before:always}
  .rank-item,.alert-row,.check-item,.cve-item,.country-item,.tl-item{page-break-inside:avoid}
}
.section{page-break-before:always;page-break-inside:avoid}
.divider{page-break-after:avoid}
.card{page-break-inside:avoid}
</style>
</head>
<body>

<!-- ================================================================
     COVER PAGE - full viewport, animated network bg
     ================================================================ -->
<div class="cover-page" id="coverPage">
  <canvas id="cover-canvas"></canvas>

  <div class="cover-content">
    <!-- Logo -->
    <div class="cover-logo-block">
      <span class="cn">CompuNet</span>
      <span class="ct"><span class="hash">#</span><span class="rest">JuntosMasLejos</span></span>
    </div>

    <div class="cover-divider"></div>

    <div class="cover-eyebrow">Threat Intelligence Report</div>

    <h1 class="cover-h1">
      <span class="line1">REPORTE</span>
      <span class="line2">AMENAZAS</span>
    </h1>

    <p class="cover-subtitle">
      Inteligencia de amenazas accionable para CISO, CIO y equipos de seguridad.<br>
      Semana <strong style="color:#fff">06/04/2026 — 12/04/2026</strong>
    </p>

    <div class="cover-badges">
      
      <span class="pill yellow">● Nivel ALTO</span>
      
      <span class="pill yellow">10 Grupos Activos</span>
      
      <span class="pill red">3 Nuevos esta semana</span>
      
      
      <span class="pill" style="background:rgba(255,255,255,.05);color:var(--text-muted);border:1px solid var(--border)">Chile: 29 Grupos activos</span>
      
    </div>

    <div class="cover-kpis">
      <div class="cover-kpi">
        <div class="n">2358</div>
        <div class="l">Victimas</div>
        <div class="c dn">
          ▼ -25%
        </div>
      </div>
      <div class="cover-kpi">
        <div class="n">10</div>
        <div class="l">Grupos activos</div>
        <div class="c up">+3 nuevos</div>
      </div>
      <div class="cover-kpi">
        <div class="n">96</div>
        <div class="l">Paises</div>
        <div class="c dn">
          ▼ -83%
        </div>
      </div>
      <div class="cover-kpi">
        <div class="n">1203</div>
        <div class="l">Filtraciones</div>
        <div class="c up">
          ▲ 111%
        </div>
      </div>
      <div class="cover-kpi">
        <div class="n">36</div>
        <div class="l">Sectores</div>
        <div class="c" style="color:var(--text-muted)">afectados</div>
      </div>
      <div class="cover-kpi">
        <div class="n">117</div>
        <div class="l">LATAM</div>
        <div class="c up">
          3 Chile
        </div>
      </div>
    </div>
  </div>

  <div class="cover-scroll">
    <span>Continuar</span>
    <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
      <path d="M2 5l5 5 5-5" stroke="#6b7a99" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </div>
</div>

<!-- Cover canvas animation -->
<script>
(function(){
  const cvs = document.getElementById('cover-canvas');
  const ctx = cvs.getContext('2d');
  function resize(){
    cvs.width  = cvs.parentElement.offsetWidth;
    cvs.height = cvs.parentElement.offsetHeight;
  }
  resize();
  window.addEventListener('resize', resize);
  const N = 80, DIST = 140;
  const pts = Array.from({length:N},()=>({
    x:Math.random()*cvs.width, y:Math.random()*cvs.height,
    vx:(Math.random()-.5)*.4, vy:(Math.random()-.5)*.4,
    r:Math.random()*2.5+1
  }));
  function frame(){
    ctx.clearRect(0,0,cvs.width,cvs.height);
    for(let i=0;i<N;i++){
      for(let j=i+1;j<N;j++){
        const dx=pts[i].x-pts[j].x, dy=pts[i].y-pts[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<DIST){
          ctx.beginPath();
          ctx.strokeStyle=`rgba(41,121,255,${(1-d/DIST)*.3})`;
          ctx.lineWidth=.6;
          ctx.moveTo(pts[i].x,pts[i].y);
          ctx.lineTo(pts[j].x,pts[j].y);
          ctx.stroke();
        }
      }
    }
    pts.forEach(p=>{
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle='rgba(100,160,255,.5)';
      ctx.fill();
      p.x+=p.vx; p.y+=p.vy;
      if(p.x<0||p.x>cvs.width)  p.vx*=-1;
      if(p.y<0||p.y>cvs.height) p.vy*=-1;
    });
    requestAnimationFrame(frame);
  }
  frame();
})();
</script>

<!-- ================================================================
     TOPBAR - sticky on scroll
     ================================================================ -->
<nav class="topbar">
  <div class="logo-block">
    <span class="logo-name">CompuNet</span>
    <span class="logo-tag"><span class="hash">#</span><span class="rest">JuntosMasLejos</span></span>
  </div>
  <div class="topbar-meta">
    <span>Threat Intelligence</span>
    <span>06/04/2026 – 12/04/2026</span>
    
    <span class="pill yellow">● Nivel ALTO</span>
    
  </div>
</nav>

<!-- RISK BAR -->
<div class="risk-banner">
  <span class="risk-label">Nivel de riesgo</span>
  <div class="risk-bar">
    
      
        
    <div class="risk-seg active red"></div>
        
      
    
      
        
    <div class="risk-seg active red"></div>
        
      
    
      
        
    <div class="risk-seg active red"></div>
        
      
    
      
    <div class="risk-seg"></div>
      
    
      
    <div class="risk-seg"></div>
      
    
  </div>
  <span class="risk-note"><strong>ALTO</strong> — Actividad dentro del rango esperado. Mantener vigilancia.</span>
</div>

<!-- ================================================================
     01 RESUMEN EJECUTIVO
     ================================================================ -->
<div class="section">
  <div class="section-label">01 — Resumen Ejecutivo</div>
  <div class="section-title">Lo que todo CISO / CIO debe saber esta semana</div>
  <div class="section-sub">Insights estrategicos para decisiones de negocio inmediatas.</div>
  <div class="card red-top">
  <div class="card-label">🔴 Panorama Ransomware</div>
  <div class="card-title">Persistencia y presión operativa</div>
  <div class="card-body">Con <strong style="color:var(--red)">2358</strong> víctimas totales esta semana, el ransomware mantiene una presencia constante, liderada por el grupo <em>thegentlemen</em> con <strong style="color:var(--red)">54</strong> víctimas. La cifra actual supera el promedio de las últimas cuatro semanas de <strong style="color:var(--red)">1901</strong>, evidenciando una actividad sostenida. ¿Está su estrategia de resiliencia preparada para un escenario de indisponibilidad prolongada?</div>
</div>

<div class="card yellow-top">
  <div class="card-label">🟡 Tendencia Estructural</div>
  <div class="card-title">Diversificación del cibercrimen</div>
  <div class="card-body">El ecosistema muestra una alta actividad fuera del ransomware, con <strong style="color:var(--yellow)">2093</strong> incidentes non-ransomware, destacando <strong style="color:var(--yellow)">706</strong> eventos de <em>combo_list</em> y <strong style="color:var(--yellow)">582</strong> de <em>defacement</em>. Esta fragmentación de amenazas exige una visibilidad que trascienda el bloqueo de cifrado. ¿Su arquitectura de seguridad detecta eficazmente el uso de credenciales expuestas antes de que ocurra una intrusión?</div>
</div>

<div class="card blue-top">
  <div class="card-label">🔵 Riesgo Regional</div>
  <div class="card-title">Panorama de amenazas en Chile</div>
  <div class="card-body">Chile registra una actividad persistente con <strong style="color:var(--blue)">117</strong> incidentes en LATAM, afectando sectores críticos mediante grupos como <em>qilin</em> y <em>nyxargroup</em>. Los incidentes documentados abarcan desde ransomware en servicios logísticos hasta brechas en registros públicos y bases de datos. ¿Cuenta su organización con inteligencia específica sobre los actores que operan activamente en el ecosistema local?</div>
</div>

<div class="card yellow-top">
  <div class="card-label">🟡 Vectores de Ataque</div>
  <div class="card-title">Exposición de credenciales y acceso</div>
  <div class="card-body">La superficie de ataque se ve comprometida principalmente por <strong style="color:var(--yellow)">774</strong> credenciales expuestas (<em>combo_list</em> y <em>logs</em>), sumado a <strong style="color:var(--yellow)">132</strong> ataques DDoS y <strong style="color:var(--yellow)">66</strong> incidentes de acceso inicial. La facilidad de adquisición de estos vectores facilita la escalada de privilegios. ¿Tiene visibilidad sobre qué credenciales corporativas circulan actualmente en canales abiertos o Telegram?</div>
</div>

<div class="card red-top">
  <div class="card-label">🔴 Sectores Bajo Presión</div>
  <div class="card-title">Concentración en sectores críticos</div>
  <div class="card-body">Los sectores de Tecnología de la Información (<strong style="color:var(--red)">267</strong>), Estado (<strong style="color:var(--red)">124</strong>) y Educación (<strong style="color:var(--red)">84</strong>) concentran la mayor presión, siendo objetivos primarios por su valor operativo y de datos. Esta tendencia subraya la necesidad de proteger la cadena de suministro y los servicios ciudadanos. ¿Ha evaluado el riesgo de interrupción en sus servicios de TI ante un ataque dirigido?</div>
</div>

<div class="card yellow-top">
  <div class="card-label">💰 Contexto de Impacto</div>
  <div class="card-title">Cuantificación del riesgo financiero</div>
  <div class="card-body">El costo promedio de un incidente de ransomware en LATAM supera los <strong style="color:var(--yellow)">USD $1.5M</strong>, considerando recuperación, impacto reputacional y multas. Este valor subraya que la ciberseguridad es una decisión de negocio crítica. ¿Su organización tiene cuantificado el impacto financiero de un incidente?</div>
</div>
</div>

<div class="divider"></div>

<!-- ================================================================
     02 DASHBOARD SEMANAL
     ================================================================ -->
<div class="section">
  <div class="section-label">02 — Dashboard Semanal</div>
  <div class="section-title">Panorama global de actividad de amenazas</div>
  <div class="section-sub">Semana 06/04/2026–12/04/2026 vs. contexto historico.</div>
  <div class="cards cards-6" style="margin-bottom:18px">
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Victimas</div>
      <div class="card-num yellow" style="font-size:34px">2358</div>
      <div class="card-sub" style="color:var(--green)">
        ▼ -25%
      </div>
    </div>
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Filtraciones</div>
      <div class="card-num red" style="font-size:34px">1203</div>
      <div class="card-sub" style="color:var(--red-soft)">
        ▲ 111%
      </div>
    </div>
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Grupos activos</div>
      <div class="card-num white" style="font-size:34px">10</div>
      <div class="card-sub" style="color:var(--yellow)">+3 nuevos</div>
    </div>
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Paises</div>
      <div class="card-num white" style="font-size:34px">96</div>
      <div class="card-sub" style="color:var(--green)">
        ▼ -83%
      </div>
    </div>
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Sectores</div>
      <div class="card-num white" style="font-size:34px">36</div>
      <div class="card-sub" style="color:var(--text-muted)">afectados</div>
    </div>
    <div class="card text-center" style="padding:16px 10px">
      <div class="card-label">Prom. 4 sem.</div>
      <div style="font-size:28px;font-weight:900;color:var(--text-muted)">1901</div>
      <div class="card-sub" style="color:var(--red-soft)">semana tipica</div>
    </div>
  </div>
  <div class="cards cards-2-1">
    <div class="card">
      <div class="card-label">Evolucion mensual de victimas</div>
      <div class="bar-chart"><div class="bar-col"><div class="bar blue" style="height:22%"></div><div class="bar-val">1778</div><div class="bar-lbl">Dec</div></div>
<div class="bar-col"><div class="bar blue" style="height:29%"></div><div class="bar-val">2303</div><div class="bar-lbl">Jan</div></div>
<div class="bar-col"><div class="bar blue" style="height:32%"></div><div class="bar-val">2536</div><div class="bar-lbl">Feb</div></div>
<div class="bar-col"><div class="bar blue" style="height:39%"></div><div class="bar-val">3141</div><div class="bar-lbl">Mar</div></div>
<div class="bar-col"><div class="bar blue" style="height:34%"></div><div class="bar-val">2738</div><div class="bar-lbl">Apr</div></div>
<div class="bar-col"><div class="bar blue" style="height:44%"></div><div class="bar-val">3468</div><div class="bar-lbl">May</div></div>
<div class="bar-col"><div class="bar blue" style="height:48%"></div><div class="bar-val">3805</div><div class="bar-lbl">Jun</div></div>
<div class="bar-col"><div class="bar blue" style="height:42%"></div><div class="bar-val">3330</div><div class="bar-lbl">Jul</div></div>
<div class="bar-col"><div class="bar blue" style="height:45%"></div><div class="bar-val">3544</div><div class="bar-lbl">Aug</div></div>
<div class="bar-col"><div class="bar blue" style="height:41%"></div><div class="bar-val">3225</div><div class="bar-lbl">Sep</div></div>
<div class="bar-col"><div class="bar blue" style="height:36%"></div><div class="bar-val">2831</div><div class="bar-lbl">Oct</div></div>
<div class="bar-col"><div class="bar blue" style="height:38%"></div><div class="bar-val">3025</div><div class="bar-lbl">Nov</div></div>
<div class="bar-col"><div class="bar blue" style="height:44%"></div><div class="bar-val">3522</div><div class="bar-lbl">Dec</div></div>
<div class="bar-col"><div class="bar yellow" style="height:51%"></div><div class="bar-val" style="color:var(--yellow)">4096</div><div class="bar-lbl" style="color:var(--yellow)">Jan'26</div></div>
<div class="bar-col"><div class="bar yellow" style="height:48%"></div><div class="bar-val" style="color:var(--yellow)">3802</div><div class="bar-lbl" style="color:var(--yellow)">Feb'26</div></div>
<div class="bar-col"><div class="bar yellow" style="height:100%"></div><div class="bar-val" style="color:var(--yellow)">7960</div><div class="bar-lbl" style="color:var(--yellow)">Mar'26</div></div>
<div class="bar-col"><div class="bar yellow" style="height:61%"></div><div class="bar-val" style="color:var(--yellow)">4863</div><div class="bar-lbl" style="color:var(--yellow)">Apr'26</div></div></div>
    </div>
    <div style="display:flex;flex-direction:column;gap:14px">
      <div class="insight-box"><div class="ico">📈</div><h4>Tendencia 2026</h4><p>El ritmo anualizado proyecta un incremento sostenido. Monitorear evolucion mensual para anticipar picos.</p></div>
      <div class="insight-box" style="background:linear-gradient(135deg,rgba(229,57,53,.06),transparent);border-color:rgba(229,57,53,.2)"><div class="ico">⚡</div><h4 style="color:var(--red-soft)">Semanas bajas = reorganizacion</h4><p>Las caidas de volumen reflejan reconsolidacion de grupos, no reduccion real. Las semanas siguientes pueden traer ataques mas coordinados.</p></div>
    </div>
  </div>
</div>

<div class="divider"></div>

<!-- ================================================================
     03 TOP GRUPOS DE AMENAZAS
     ================================================================ -->
<div class="section">
  <div class="section-label">03 — Top Grupos de Amenazas</div>
  <div class="section-title">Los actores mas activos esta semana</div>
  <div class="section-sub">Separados por nivel de impacto. Las amenazas de alto impacto pueden paralizar operaciones; las de alto volumen alimentan vectores de acceso inicial.</div>

  <div class="cards cards-2">
    <!-- HIGH IMPACT: ransomware, breach, leak, initial_access -->
    <div class="card" style="border-top:3px solid var(--red-soft)">
      <div class="card-label" style="color:var(--red-soft)">🔴 Amenazas de Alto Impacto</div>
      <div style="font-size:10px;color:var(--text-muted);margin-bottom:8px">Ransomware · Data Breach · Data Leak · Acceso Inicial</div>
      <div class="rank-list mt12"><div class="rank-item"><span class="rank-num">#1</span><span class="rank-name">thegentlemen <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:5px">RANSOM</span> <span class="pill yellow" style="font-size:9px;margin-left:4px">🇨🇱 Chile</span></span><span class="rank-victims">54</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#2</span><span class="rank-name">shinyhunters <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:5px">RANSOM</span></span><span class="rank-victims">32</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#3</span><span class="rank-name">lockbit5 <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:5px">RANSOM</span></span><span class="rank-victims">20</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#4</span><span class="rank-name">qilin <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:5px">RANSOM</span> <span class="pill yellow" style="font-size:9px;margin-left:4px">🇨🇱 Chile</span></span><span class="rank-victims">17</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#5</span><span class="rank-name">shadowbyt3$ <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:5px">RANSOM</span></span><span class="rank-victims">17</span><span class="rank-change new">★ NUEVO</span></div></div>
      <div class="donut-wrap mt12" style="margin-top:16px">
        <svg width="108" height="108" viewBox="0 0 42 42"><circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#1c2438" stroke-width="5"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#ff5252" stroke-width="5" stroke-dasharray="38.6 61.4" stroke-dashoffset="0.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#f5a623" stroke-width="5" stroke-dasharray="22.9 77.1" stroke-dashoffset="-38.6" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#2979ff" stroke-width="5" stroke-dasharray="14.3 85.7" stroke-dashoffset="-61.4" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#00c853" stroke-width="5" stroke-dasharray="12.1 87.9" stroke-dashoffset="-75.7" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#9c27b0" stroke-width="5" stroke-dasharray="12.1 87.9" stroke-dashoffset="-87.9" stroke-linecap="round"/><text x="21.0" y="19.0" text-anchor="middle" font-size="7" fill="#e8ecf4" font-weight="900">Top 5</text><text x="21.0" y="24.5" text-anchor="middle" font-size="3.8" fill="#6b7a99">140 víctimas</text></svg>
        <div class="donut-legend">
          <div class="donut-leg-item"><span class="donut-dot" style="background:#ff5252"></span><span class="donut-leg-name">thegentlemen</span><span class="donut-leg-pct">39%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#f5a623"></span><span class="donut-leg-name">shinyhunters</span><span class="donut-leg-pct">23%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#2979ff"></span><span class="donut-leg-name">lockbit5</span><span class="donut-leg-pct">14%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#00c853"></span><span class="donut-leg-name">qilin</span><span class="donut-leg-pct">12%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#9c27b0"></span><span class="donut-leg-name">shadowbyt3$</span><span class="donut-leg-pct">12%</span></div>
        </div>
      </div>
    </div>

    <!-- HIGH VOLUME: defacement, ddos, combo_list, etc. -->
    <div class="card" style="border-top:3px solid var(--blue)">
      <div class="card-label" style="color:var(--blue)">🔵 Amenazas de Alto Volumen</div>
      <div style="font-size:10px;color:var(--text-muted);margin-bottom:8px">Defacement · DDoS · Combo List · Logs · Cyber Attack</div>
      <div class="rank-list mt12"><div class="rank-item"><span class="rank-num">#1</span><span class="rank-name">dimashxr <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:5px">DEFACE</span></span><span class="rank-victims">239</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#2</span><span class="rank-name">nicotine <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:5px">DEFACE</span> <span class="pill yellow" style="font-size:9px;margin-left:4px">🇨🇱 Chile</span></span><span class="rank-victims">121</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#3</span><span class="rank-name">maw3six <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:5px">DEFACE</span></span><span class="rank-victims">60</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#4</span><span class="rank-name">coder <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:5px">DEFACE</span></span><span class="rank-victims">58</span><span class="rank-change new">★ NUEVO</span></div>
<div class="rank-item"><span class="rank-num">#5</span><span class="rank-name">thejackal101 <span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;letter-spacing:.5px;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:5px">DEFACE</span></span><span class="rank-victims">40</span><span class="rank-change new">★ NUEVO</span></div></div>
      <div style="margin-top:14px;padding:10px 14px;background:rgba(41,121,255,.06);border-radius:8px;border:1px solid rgba(41,121,255,.15);font-size:11px;color:var(--text-dim)">
        Aunque de menor impacto individual, estas amenazas alimentan los vectores de acceso inicial para ataques de mayor severidad y revelan la actividad en foros y canales de Telegram.
      </div>
    </div>
  </div>

  <!-- Inactive groups -->
  
  <div class="card" style="border-top:2px solid var(--green);margin-top:14px">
    <div class="card-label">Grupos inactivos 2026</div>
    <div style="display:flex;flex-wrap:wrap;gap:7px;margin-top:10px">
      
      <div style="padding:7px 10px;background:var(--bg-card2);border-radius:6px;border:1px solid var(--border)">
        <span style="font-size:11px;font-weight:700;color:var(--text)">0blivi0nx</span>
        <span style="font-size:10px;color:var(--green);margin-left:6px">INACTIVO</span>
      </div>
      
    </div>
  </div>
  

  <!-- Chile note -->
  <div style="font-size:11px;color:var(--text-muted);margin-top:12px;padding:8px 12px;background:rgba(229,57,53,.05);border-radius:6px;border-left:3px solid var(--red-soft)">
    🇨🇱 Grupos con actividad confirmada en Chile esta semana. Ver detalle en Seccion 07.
  </div>
</div>

<div class="divider"></div>

<!-- ================================================================
     04 GRUPOS DESTACADOS POR CATEGORÍA
     ================================================================ -->
<div class="section">
  <div class="section-label">04 — Grupos Destacados por Categoria</div>
  <div class="section-title">Actores principales por tipo de amenaza</div>
  <div class="section-sub">Perfil, TTPs y sectores objetivo de los grupos mas activos en cada categoria de amenaza esta semana.</div>
  <div class="card red-top" style="margin-bottom:14px">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
    <div>
      <div class="card-label">🔒 Ransomware — Grupo Destacado</div>
      <div class="card-title">thegentlemen</div>
    </div>
    <div style="text-align:right;font-size:12px">
      <div style="font-weight:800;font-size:24px;color:var(--red)">54</div>
      <div style="color:var(--text-muted)">víctimas</div>
    </div>
  </div>
  <div class="card-body">Este grupo opera mediante la exfiltración y cifrado de datos críticos, ejerciendo presión directa sobre la continuidad operativa de las organizaciones. Su actividad reciente subraya una capacidad persistente para comprometer infraestructuras empresariales de alto valor.</div>
  <div style="margin-top:10px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:6px">TTPs Observados</div>
    <div style="display:flex;flex-wrap:wrap;gap:6px">
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">📂 Exfiltración de datos</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🔐 Cifrado de activos</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">💬 Extorsión doble</span>
    </div>
  </div>
  <div style="margin-top:8px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:4px">Sectores objetivo</div>
    <div style="display:flex;flex-wrap:wrap;gap:4px;font-size:10px;color:var(--text-muted)">
      Tecnología de la Información (TI) · Estado · Finanzas y Banca
    </div>
  </div>
</div>

<div class="card blue-top" style="margin-bottom:14px">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
    <div>
      <div class="card-label">🌐 Defacement — Grupo Destacado</div>
      <div class="card-title">dimashxr</div>
    </div>
    <div style="text-align:right;font-size:12px">
      <div style="font-weight:800;font-size:24px;color:var(--blue)">239</div>
      <div style="color:var(--text-muted)">víctimas</div>
    </div>
  </div>
  <div class="card-body">Especializados en la alteración no autorizada de interfaces web, este actor busca maximizar el impacto reputacional mediante la desfiguración masiva de sitios. Su alta frecuencia de ataques demuestra una automatización eficiente en la explotación de vulnerabilidades expuestas.</div>
  <div style="margin-top:10px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:6px">TTPs Observados</div>
    <div style="display:flex;flex-wrap:wrap;gap:6px">
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🎨 Modificación de contenido</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🔍 Escaneo de vulnerabilidades</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">⚙️ Explotación de CMS</span>
    </div>
  </div>
  <div style="margin-top:8px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:4px">Sectores objetivo</div>
    <div style="display:flex;flex-wrap:wrap;gap:4px;font-size:10px;color:var(--text-muted)">
      Tecnología de la Información (TI) · Educación y Formación · Comercio Minorista
    </div>
  </div>
</div>

<div class="card cyan-top" style="margin-bottom:14px">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
    <div>
      <div class="card-label">📋 Combo_list — Grupo Destacado</div>
      <div class="card-title">coder</div>
    </div>
    <div style="text-align:right;font-size:12px">
      <div style="font-weight:800;font-size:24px;color:var(--cyan)">58</div>
      <div style="color:var(--text-muted)">víctimas</div>
    </div>
  </div>
  <div class="card-body">Este grupo se enfoca en la recolección y comercialización de credenciales comprometidas. Su operatividad facilita el acceso inicial a terceros, convirtiéndose en un eslabón crítico en la cadena de suministro de ataques cibernéticos a gran escala.</div>
  <div style="margin-top:10px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:6px">TTPs Observados</div>
    <div style="display:flex;flex-wrap:wrap;gap:6px">
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🔑 Credential Stuffing</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">📦 Agregación de datos</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🌐 Distribución en foros</span>
    </div>
  </div>
  <div style="margin-top:8px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:4px">Sectores objetivo</div>
    <div style="display:flex;flex-wrap:wrap;gap:4px;font-size:10px;color:var(--text-muted)">
      Tecnología de la Información (TI) · Finanzas y Banca · Comercio Minorista
    </div>
  </div>
</div>

<div class="card yellow-top" style="margin-bottom:14px">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
    <div>
      <div class="card-label">⚠️ Breach — Grupo Destacado</div>
      <div class="card-title">shinyhunters</div>
    </div>
    <div style="text-align:right;font-size:12px">
      <div style="font-weight:800;font-size:24px;color:var(--yellow)">40</div>
      <div style="color:var(--text-muted)">víctimas</div>
    </div>
  </div>
  <div class="card-body">Reconocidos por su capacidad para infiltrarse en bases de datos masivas, este grupo representa una amenaza significativa para la privacidad de los datos. Su modus operandi se centra en la extracción de información sensible para su posterior filtración o venta.</div>
  <div style="margin-top:10px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:6px">TTPs Observados</div>
    <div style="display:flex;flex-wrap:wrap;gap:6px">
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">🗄️ Infiltración en BD</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">📤 Exfiltración masiva</span>
      <span style="padding:3px 10px;border-radius:12px;font-size:10px;font-weight:600;background:var(--bg-card2);border:1px solid var(--border)">👤 Robo de identidad</span>
    </div>
  </div>
  <div style="margin-top:8px">
    <div style="font-size:10px;font-weight:700;color:var(--text-muted);text-transform:uppercase;margin-bottom:4px">Sectores objetivo</div>
    <div style="display:flex;flex-wrap:wrap;gap:4px;font-size:10px;color:var(--text-muted)">
      Estado · Tecnología de la Información (TI) · Educación y Formación
    </div>
  </div>
</div>
</div>

<div class="divider"></div>

<!-- ================================================================
     05 PAISES + MAPA MUNDI + SECTORES
     ================================================================ -->
<div class="section">
  <div class="section-label">05 — Paises y Sectores Afectados</div>
  <div class="section-title">Geografia global del riesgo — semana 06/04/2026–12/04/2026</div>
  <div class="section-sub">96 paises afectados esta semana. El mapa muestra la distribucion de victimas confirmadas e indica intensidad de ataque.</div>

  <!-- WORLD MAP -->
  <div class="map-wrapper" style="margin-bottom:18px">
    <div class="map-title">Mapa mundial de victimas — semana 06/04/2026–12/04/2026</div>
    <div id="map-tooltip" class="map-tooltip"></div>
    <!-- SVG world map - simplified Mercator projection -->
    <svg id="world-map" viewBox="0 0 960 500" style="width:100%;height:auto;display:block" xmlns="http://www.w3.org/2000/svg">
      <!-- Ocean bg -->
      <rect width="960" height="500" fill="#0a0f1e" rx="8"/>
      <!-- Grid lines -->
      <g stroke="#1a2238" stroke-width=".4" opacity=".6">
        <line x1="0" y1="250" x2="960" y2="250"/>
        <line x1="480" y1="0" x2="480" y2="500"/>
        <line x1="0" y1="166" x2="960" y2="166"/><line x1="0" y1="334" x2="960" y2="334"/>
        <line x1="240" y1="0" x2="240" y2="500"/><line x1="720" y1="0" x2="720" y2="500"/>
      </g>

      <!-- CONTINENTS (simplified paths) -->
      <g fill="#1a2640" stroke="#2a3a54" stroke-width=".8">
        <!-- North America -->
        <path d="M55,60 L85,55 L115,48 L145,52 L175,60 L195,70 L215,80 L225,100 L220,120 L210,140 L205,165 L215,175 L225,195 L215,210 L200,215 L185,220 L175,230 L165,250 L155,265 L140,270 L130,260 L120,250 L115,235 L105,225 L90,220 L80,210 L70,200 L60,185 L55,170 L50,155 L48,140 L50,120 L52,100 L54,80 Z"/>
        <!-- Greenland -->
        <path d="M175,20 L195,18 L210,22 L215,35 L210,48 L195,52 L180,48 L172,38 Z"/>
        <!-- Central America -->
        <path d="M165,250 L175,255 L185,265 L180,280 L170,285 L160,278 L158,265 Z"/>
        <!-- South America -->
        <path d="M175,290 L200,285 L225,280 L245,275 L265,278 L275,290 L280,310 L278,335 L270,360 L258,385 L242,405 L225,415 L210,410 L198,395 L190,375 L185,355 L180,330 L175,310 Z"/>
        <!-- Europe -->
        <path d="M420,60 L445,55 L470,50 L490,55 L505,65 L510,80 L505,95 L495,105 L480,112 L465,115 L450,112 L435,108 L425,100 L418,88 L416,75 Z"/>
        <!-- Scandinavia -->
        <path d="M450,30 L465,25 L478,28 L482,40 L478,52 L465,55 L452,50 L446,40 Z"/>
        <!-- British Isles -->
        <path d="M408,68 L416,65 L420,72 L417,80 L410,82 L405,76 Z"/>
        <!-- Iberian Peninsula -->
        <path d="M408,92 L424,88 L432,95 L430,110 L420,118 L408,115 L402,105 L403,96 Z"/>
        <!-- Africa -->
        <path d="M430,135 L460,128 L490,125 L515,128 L535,138 L545,155 L548,175 L545,200 L538,225 L528,250 L515,275 L500,300 L485,320 L468,330 L450,325 L435,310 L424,290 L418,265 L416,240 L418,215 L422,190 L425,165 L427,145 Z"/>
        <!-- Asia Major -->
        <path d="M510,55 L550,48 L600,42 L650,40 L700,42 L740,48 L770,58 L785,72 L790,90 L785,110 L775,125 L760,135 L740,140 L715,142 L690,140 L665,138 L640,140 L615,145 L590,148 L565,145 L545,138 L528,128 L516,115 L510,100 L508,82 L509,68 Z"/>
        <!-- India -->
        <path d="M615,148 L640,145 L660,148 L670,165 L672,185 L665,205 L650,220 L633,225 L618,218 L608,200 L605,180 L607,162 Z"/>
        <!-- Southeast Asia -->
        <path d="M700,145 L725,140 L748,148 L760,162 L758,178 L745,185 L728,182 L712,172 L703,158 Z"/>
        <!-- Japan/Korea -->
        <path d="M762,85 L775,80 L785,85 L785,98 L775,105 L763,100 Z"/>
        <!-- Australia -->
        <path d="M720,310 L758,302 L795,305 L820,318 L832,338 L828,360 L815,378 L795,388 L770,390 L745,382 L724,365 L712,345 L712,325 Z"/>
        <!-- New Zealand -->
        <path d="M858,368 L866,362 L870,372 L865,382 L857,380 Z"/>
      </g>

      <!-- ATTACK MARKERS (pre-rendered) -->
      <g class="map-marker" data-country="USA 🇺🇸" data-victims="203" data-trend="" data-color="#ff5252"><circle cx="148" cy="148" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="148" cy="148" r="14" fill="rgba(255,82,82,.30)"/><circle cx="148" cy="148" r="6" fill="#ff5252"/><text x="148" y="152" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">203</text></g>
<g class="map-marker" data-country="Germany 🇩🇪" data-victims="62" data-trend="" data-color="#ff5252"><circle cx="460" cy="72" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="460" cy="72" r="14" fill="rgba(255,82,82,.30)"/><circle cx="460" cy="72" r="6" fill="#ff5252"/><text x="460" y="76" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">62</text></g>
<g class="map-marker" data-country="France 🇫🇷" data-victims="62" data-trend="" data-color="#ff5252"><circle cx="434" cy="88" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="434" cy="88" r="14" fill="rgba(255,82,82,.30)"/><circle cx="434" cy="88" r="6" fill="#ff5252"/><text x="434" y="92" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">62</text></g>
<g class="map-marker" data-country="UK 🇬🇧" data-victims="56" data-trend="" data-color="#ff5252"><circle cx="412" cy="74" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="412" cy="74" r="14" fill="rgba(255,82,82,.30)"/><circle cx="412" cy="74" r="6" fill="#ff5252"/><text x="412" y="78" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">56</text></g>
<g class="map-marker" data-country="India 🇮🇳" data-victims="55" data-trend="" data-color="#ff5252"><circle cx="640" cy="175" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="640" cy="175" r="14" fill="rgba(255,82,82,.30)"/><circle cx="640" cy="175" r="6" fill="#ff5252"/><text x="640" y="179" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">55</text></g>
<g class="map-marker" data-country="Mexico 🇲🇽" data-victims="42" data-trend="" data-color="#ff5252"><circle cx="135" cy="210" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="135" cy="210" r="14" fill="rgba(255,82,82,.30)"/><circle cx="135" cy="210" r="6" fill="#ff5252"/><text x="135" y="214" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">42</text></g>
<g class="map-marker" data-country="Indonesia 🏳️" data-victims="39" data-trend="" data-color="#ff5252"><circle cx="730" cy="210" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="730" cy="210" r="14" fill="rgba(255,82,82,.30)"/><circle cx="730" cy="210" r="6" fill="#ff5252"/><text x="730" y="214" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">39</text></g>
<g class="map-marker" data-country="Israel 🇮🇱" data-victims="38" data-trend="" data-color="#ff5252"><circle cx="530" cy="115" r="22" fill="rgba(255,82,82,.18)" stroke="#ff5252" stroke-width="1"/><circle cx="530" cy="115" r="14" fill="rgba(255,82,82,.30)"/><circle cx="530" cy="115" r="6" fill="#ff5252"/><text x="530" y="119" text-anchor="middle" font-size="7" fill="#fff" font-weight="700">38</text></g>
<circle cx="148" cy="148" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="460" cy="72" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="434" cy="88" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="412" cy="74" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="640" cy="175" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="135" cy="210" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="730" cy="210" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>
<circle cx="530" cy="115" r="28" fill="none" stroke="rgba(255,82,82,.35)" stroke-width="1"><animate attributeName="r" values="22;36;22" dur="2.5s" repeatCount="indefinite"/><animate attributeName="opacity" values="0.6;0;0.6" dur="2.5s" repeatCount="indefinite"/></circle>

      <!-- Country labels -->
      <g font-size="7" fill="#4a5a78" font-family="Inter,sans-serif">
        <text x="150" y="175">NORTEAMERICA</text>
        <text x="218" y="355">S. AMERICA</text>
        <text x="440" y="165">AFRICA</text>
        <text x="620" y="90">ASIA</text>
        <text x="740" y="370">AUSTRALIA</text>
      </g>
    </svg>

    <!-- Map legend -->
    <div class="map-legend">
      <div class="map-leg-item"><div class="map-leg-dot" style="background:#ff5252;box-shadow:0 0 5px #ff5252"></div> Alto (10+ victimas)</div>
      <div class="map-leg-item"><div class="map-leg-dot" style="background:#f5a623"></div> Medio (3–9 victimas)</div>
      <div class="map-leg-item"><div class="map-leg-dot" style="background:#6b7a99"></div> Bajo (1–2 victimas)</div>
      
      <div class="map-leg-item"><div class="map-leg-dot" style="background:#ff5252;border-radius:2px"></div> Chile — activo esta semana</div>
      
    </div>
  </div>

  <!-- Tabla paises + sectores -->
  <div class="cards cards-2">
    <div class="card">
      <div class="card-label">Top paises afectados</div>
      <div class="country-list mt12">
        <div class="country-list mt12"><div class="country-item"><span class="country-flag">🇺🇸</span><span class="country-name">USA</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:100%"></div></div><span class="country-num">203</span><span class="country-chg down">▼ -21%</span></div>
<div class="country-item"><span class="country-flag">🇩🇪</span><span class="country-name">Germany</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:31%"></div></div><span class="country-num">62</span><span class="country-chg down">▼ -43%</span></div>
<div class="country-item"><span class="country-flag">🇫🇷</span><span class="country-name">France</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:31%"></div></div><span class="country-num">62</span><span class="country-chg new" style="color:var(--yellow)">NUEVO</span></div>
<div class="country-item"><span class="country-flag">🇬🇧</span><span class="country-name">UK</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:28%"></div></div><span class="country-num">56</span><span class="country-chg down">▼ -53%</span></div>
<div class="country-item"><span class="country-flag">🇮🇳</span><span class="country-name">India</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:27%"></div></div><span class="country-num">55</span><span class="country-chg down">▼ -46%</span></div>
<div class="country-item"><span class="country-flag">🇲🇽</span><span class="country-name">Mexico</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:21%"></div></div><span class="country-num">42</span><span class="country-chg new" style="color:var(--yellow)">NUEVO</span></div>
<div class="country-item"><span class="country-flag">🏳️</span><span class="country-name">Indonesia</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:19%"></div></div><span class="country-num">39</span><span class="country-chg new" style="color:var(--yellow)">NUEVO</span></div>
<div class="country-item"><span class="country-flag">🇮🇱</span><span class="country-name">Israel</span><div class="country-bar-bg"><div class="country-bar-fill" style="width:19%"></div></div><span class="country-num">38</span><span class="country-chg new" style="color:var(--yellow)">NUEVO</span></div></div>
      </div>
    </div>
    <div class="card">
      <div class="card-label">Victimas por sector</div>
      <div class="donut-wrap mt12" style="margin-bottom:16px">
        <svg width="100" height="100" viewBox="0 0 42 42"><circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#1c2438" stroke-width="5"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#ff5252" stroke-width="5" stroke-dasharray="43.3 56.7" stroke-dashoffset="0.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#f5a623" stroke-width="5" stroke-dasharray="20.1 79.9" stroke-dashoffset="-43.3" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#2979ff" stroke-width="5" stroke-dasharray="13.6 86.4" stroke-dashoffset="-63.4" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#00c853" stroke-width="5" stroke-dasharray="13.3 86.7" stroke-dashoffset="-77.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#9c27b0" stroke-width="5" stroke-dasharray="9.7 90.3" stroke-dashoffset="-90.3" stroke-linecap="round"/><text x="21.0" y="19.0" text-anchor="middle" font-size="7" fill="#e8ecf4" font-weight="900">617</text><text x="21.0" y="24.5" text-anchor="middle" font-size="3.8" fill="#6b7a99">víctimas</text></svg>
        <div class="donut-legend">
          <div class="donut-leg-item"><span class="donut-dot" style="background:#ff5252"></span><span class="donut-leg-name">Tecnología de la Información (TI)</span><span class="donut-leg-pct">43%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#f5a623"></span><span class="donut-leg-name">Estado</span><span class="donut-leg-pct">20%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#2979ff"></span><span class="donut-leg-name">Educación y Formación</span><span class="donut-leg-pct">14%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#00c853"></span><span class="donut-leg-name">Finanzas y Banca</span><span class="donut-leg-pct">13%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#9c27b0"></span><span class="donut-leg-name">Comercio Minorista</span><span class="donut-leg-pct">10%</span></div>
        </div>
      </div>
      <div style="display:flex;flex-direction:column;gap:6px">
        <div style="display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:5px 0;border-bottom:1px solid var(--border)"><span>Tecnología de la Información (TI)</span><span style="font-weight:700">267 <small style="color:var(--text-muted)">(69 filtraciones)</small></span></div><div style="display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:5px 0;border-bottom:1px solid var(--border)"><span>Estado</span><span style="font-weight:700">124 <small style="color:var(--text-muted)">(54 filtraciones)</small></span></div><div style="display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:5px 0;border-bottom:1px solid var(--border)"><span>Educación y Formación</span><span style="font-weight:700">84 <small style="color:var(--text-muted)">(40 filtraciones)</small></span></div><div style="display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:5px 0;border-bottom:1px solid var(--border)"><span>Finanzas y Banca</span><span style="font-weight:700">82 <small style="color:var(--text-muted)">(54 filtraciones)</small></span></div><div style="display:flex;justify-content:space-between;align-items:center;font-size:12px;padding:5px 0;border-bottom:1px solid var(--border)"><span>Comercio Minorista</span><span style="font-weight:700">60 <small style="color:var(--text-muted)">(16 filtraciones)</small></span></div>
      </div>
    </div>
  </div>
</div>

<!-- Map tooltip JS -->
<script>
(function(){
  const tip = document.getElementById('map-tooltip');
  document.querySelectorAll('.map-marker').forEach(g=>{
    g.style.cursor='pointer';
    g.addEventListener('mouseenter',e=>{
      const d=g.dataset;
      tip.innerHTML=`<strong>${d.country}</strong><br>Victimas: <strong style="color:${d.color}">${d.victims}</strong><br>Tendencia: ${d.trend}`;
      tip.style.display='block';
    });
    g.addEventListener('mousemove',e=>{
      const r=document.getElementById('world-map').getBoundingClientRect();
      tip.style.left=(e.clientX-r.left+12)+'px';
      tip.style.top=(e.clientY-r.top-10)+'px';
    });
    g.addEventListener('mouseleave',()=>{tip.style.display='none'});
  });
})();
</script>

<div class="divider"></div>

<!-- ================================================================
     06 PANORAMA REGIONAL - LATAM
     ================================================================ -->
<div class="section">
  <div class="section-label">06 — Panorama Regional</div>
  <div class="section-title">LATAM: 117 victimas esta semana</div>
  <div class="section-sub">La region esta en la mira. El crecimiento anualizado supera el promedio global.</div>
  <div class="latam-country"><span class="latam-flag">🇧🇷</span><div class="latam-info"><h4>Brazil</h4><p>Total hist.: 934 · 2026 YTD: 322</p><p style="margin-top:2px;color:var(--text-muted)">0x0daytoday, 0xy0um0m, 13lula13</p></div><div style="text-align:right"><div class="latam-ytd">322</div><div class="latam-thisweek">34 esta sem.</div></div></div><div class="latam-country"><span class="latam-flag">🇲🇽</span><div class="latam-info"><h4>Mexico</h4><p>Total hist.: 524 · 2026 YTD: 187</p><p style="margin-top:2px;color:var(--text-muted)">404 crew cyber team, adrxx_chronus, alz_157s</p></div><div style="text-align:right"><div class="latam-ytd">187</div><div class="latam-thisweek">42 esta sem.</div></div></div><div class="latam-country"><span class="latam-flag">🇨🇴</span><div class="latam-info"><h4>Colombia</h4><p>Total hist.: 264 · 2026 YTD: 115</p><p style="margin-top:2px;color:var(--text-muted)">0xy0um0m, arcraidersplayer, babayo eror system</p></div><div style="text-align:right"><div class="latam-ytd">115</div><div class="latam-thisweek">14 esta sem.</div></div></div><div class="latam-country"><span class="latam-flag">🇦🇷</span><div class="latam-info"><h4>Argentina</h4><p>Total hist.: 396 · 2026 YTD: 100</p><p style="margin-top:2px;color:var(--text-muted)">404 crew cyber team, ackline, arabteen</p></div><div style="text-align:right"><div class="latam-ytd">100</div><div class="latam-thisweek">9 esta sem.</div></div></div><div class="latam-country"><span class="latam-flag">🇻🇪</span><div class="latam-info"><h4>Venezuela</h4><p>Total hist.: 173 · 2026 YTD: 78</p><p style="margin-top:2px;color:var(--text-muted)">0xy0um0m, chinafans, coinbasecartel</p></div><div style="text-align:right"><div class="latam-ytd">78</div><div class="latam-thisweek">2 esta sem.</div></div></div><div class="latam-country" style="border-left:3px solid var(--red-soft)"><span class="latam-flag">🇨🇱</span><div class="latam-info"><h4>Chile</h4><p>Total hist.: 135 · 2026 YTD: 46</p><p style="margin-top:2px;color:var(--text-muted)">a k u l a v 2 . 2, apt73/bashe, babayo eror system</p></div><div style="text-align:right"><div class="latam-ytd">46</div><div class="latam-thisweek">3 esta sem.</div></div></div>
</div>

<div class="divider"></div>

<!-- ================================================================
     07 FOCO CHILE
     ================================================================ -->
<div class="section">
  <div class="section-label">07 — Foco Regional: Chile</div>
  <div class="section-title">Chile 2026: 46 victimas YTD</div>
  <div class="section-sub">Analisis de la actividad de amenazas en Chile, con implicancias reales para empresas nacionales.</div>
  <div class="cards cards-2-1" style="margin-bottom:16px">
    <div class="card red-top">
      <div class="card-label">Timeline Chile — ultimos 6 meses</div>
      <div class="timeline mt12">
        <div class="tl-item"><div class="tl-dot red"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>SAAM Towage — qilin</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:6px;vertical-align:middle">Ransomware</span><br>Business Services</div></div><div class="tl-item"><div class="tl-dot red"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>Alleged leak of Chilean email credentials combolist — cobraegy</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#06b6d422;color:#06b6d4;border:1px solid #06b6d444;margin-left:6px;vertical-align:middle">Combo List</span><br>Un actor de amenazas compartió una "combolist" que contiene más de 79,000 combinaciones de correo electrónico y contraseña dirigidas a usuarios chilenos. Se afirma que las credenciales son recientes y de alta calidad, distribuidas a través de un canal de Telegram.</div></div><div class="tl-item"><div class="tl-dot dim"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>Agencia Mesa Marcial — nicotine</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#a78bfa22;color:#a78bfa;border:1px solid #a78bfa44;margin-left:6px;vertical-align:middle">Defacement</span><br>El atacante Nicotine, del grupo Umbra Community, desfiguró el sitio web de Agencia Mesa Marcial el 6 de abril de 2026. El incidente se registró como una desfiguración de sitio único, no como un ataque masivo o recurrente.</div></div><div class="tl-item"><div class="tl-dot dim"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>Zyght — igotafeeling</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#ef444422;color:#ef4444;border:1px solid #ef444444;margin-left:6px;vertical-align:middle">Ransomware</span><br>Zyght, una plataforma de software HSE (Health, Safety & Environment), habría sufrido una brecha de seguridad, con 6.1TB de datos puestos a la venta en un popular foro de ciberdelincuencia. Actor de amenazas: igotafeeling Categoría: Brecha Víctima: Zyght Industria: Software HSE Sitio: El actor de amenazas afirma haber obtenido 6.</div></div><div class="tl-item"><div class="tl-dot red"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>Civil Registry and Identification Service of Chile — gordonfreeman</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#fb923c22;color:#fb923c;border:1px solid #fb923c44;margin-left:6px;vertical-align:middle">Data Breach</span><br>Un actor de amenazas afirma estar vendiendo una base de datos que contiene 10 millones de registros del Servicio de Registro Civil e Identificación de Chile. Los datos supuestamente incluyen nombres completos, fechas de nacimiento, números de RUT y números de cédula de identidad, con registros actualizados al año 2026.</div></div><div class="tl-item"><div class="tl-dot red"></div><span class="tl-date">Apr 2026</span><div class="tl-text"><strong>Alleged Data Leak of Chilean Male Gender Database — joker</strong><span style="display:inline-block;padding:1px 6px;border-radius:10px;font-size:8px;font-weight:700;background:#facc1522;color:#facc15;border:1px solid #facc1544;margin-left:6px;vertical-align:middle">Data Leak</span><br>Un actor de amenazas afirma poseer o compartir una base de datos que contiene registros de hombres chilenos, lo que sugiere una brecha o filtración de información personal de Chile.</div></div>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:14px">
      <div class="card" style="text-align:center">
        <div class="card-label">YTD 2026</div>
        <div class="big-num" style="color:var(--red-soft)">46</div>
        <div class="card-sub">victimas confirmadas en Chile</div>
      </div>
      <div class="card" style="text-align:center">
        <div class="card-label">Todo 73</div>
        <div class="big-num" style="color:var(--text-muted)">73</div>
        <div class="card-sub">victimas en todo el periodo anterior</div>
      </div>
      <div class="card">
        <div class="card-label">Victimas mensuales 2026</div>
        <div class="donut-wrap mt10">
          <svg width="88" height="88" viewBox="0 0 42 42"><circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#1c2438" stroke-width="5"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#ff5252" stroke-width="5" stroke-dasharray="15.2 84.8" stroke-dashoffset="0.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#f5a623" stroke-width="5" stroke-dasharray="19.6 80.4" stroke-dashoffset="-15.2" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#2979ff" stroke-width="5" stroke-dasharray="47.8 52.2" stroke-dashoffset="-34.8" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#00c853" stroke-width="5" stroke-dasharray="17.4 82.6" stroke-dashoffset="-82.6" stroke-linecap="round"/><text x="21.0" y="19.0" text-anchor="middle" font-size="7" fill="#e8ecf4" font-weight="900">46</text><text x="21.0" y="24.5" text-anchor="middle" font-size="3.8" fill="#6b7a99">YTD</text></svg>
          <div class="donut-legend">
            <div class="donut-leg-item"><span class="donut-dot" style="background:#ff5252"></span><span class="donut-leg-name">January</span><span class="donut-leg-pct">15%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#f5a623"></span><span class="donut-leg-name">February</span><span class="donut-leg-pct">20%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#2979ff"></span><span class="donut-leg-name">March</span><span class="donut-leg-pct">48%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#00c853"></span><span class="donut-leg-name">April</span><span class="donut-leg-pct">17%</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <div class="highlight" style="border-left-color:var(--red-soft)">
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:22px;align-items:start">
  <div>
    <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--red-soft);margin-bottom:7px">⚡ Caso destacado</div>
    <div style="font-size:20px;font-weight:900;margin-bottom:10px">SAAM Towage</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
      <div><div style="font-size:9px;color:var(--text-muted);text-transform:uppercase">Grupo</div><div style="font-size:13px;font-weight:700;color:var(--red-soft)">qilin</div></div>
      <div><div style="font-size:9px;color:var(--text-muted);text-transform:uppercase">Fecha</div><div style="font-size:13px;font-weight:700">2026-04-09</div></div>
      <div><div style="font-size:9px;color:var(--text-muted);text-transform:uppercase">Datos</div><div style="font-size:13px;font-weight:700;color:var(--yellow)">Sin confirmar</div></div>
      <div><div style="font-size:9px;color:var(--text-muted);text-transform:uppercase">Estado</div><div style="font-size:13px;font-weight:700;color:var(--red-soft)">Leak público confirmado</div></div>
    </div>
  </div>
  <div>
    <div style="font-size:12px;color:var(--text-dim);line-height:1.7;margin-bottom:10px">SAAM Towage es el mayor operador de servicios de remolque en América y tercero a nivel mundial, con origen chileno. Provee servicios críticos de apoyo a grandes embarcaciones en maniobras de atraque, desatraque y escolta en más de 90 puertos, siendo un actor esencial para la logística y el comercio exterior.</div>
    <div style="padding:10px 14px;background:rgba(229,57,53,.08);border-radius:7px;border:1px solid rgba(229,57,53,.2);font-size:11px;color:var(--text-dim)"><strong style="color:var(--red-soft)">Impacto Ley 21.663:</strong> Como actor clave en el transporte marítimo y la logística, SAAM Towage podría ser calificado como Operador de Importancia Vital (OIV) o Servicio Esencial. La ley exige reportar incidentes a la ANCI, implementar sistemas de gestión de seguridad (SGSI) y someterse a auditorías, bajo riesgo de multas significativas por incumplimiento en la protección de infraestructura crítica.</div>
  </div>
</div>
  </div>
  
</div>

<div class="divider"></div>

<!-- ================================================================
     08 VECTORES DE ATAQUE
     ================================================================ -->
<div class="section">
  <div class="section-label">08 — Vectores de Ataque</div>
  <div class="section-title">Como estan entrando los atacantes</div>
  <div class="section-sub">Vectores de acceso inicial inferidos a partir de los TTPs conocidos de los grupos activos esta semana. Las CVEs listadas son las mas asociadas a estos grupos segun fuentes publicas de inteligencia.</div>
  <div class="cards cards-2"><div class="card"><div class="card-label">Distribución de vectores de acceso inicial</div><div class="donut-wrap mt12" style="margin-bottom:18px"><svg width="120" height="120" viewBox="0 0 42 42"><circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#1c2438" stroke-width="5"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#ff5252" stroke-width="5" stroke-dasharray="38.0 62.0" stroke-dashoffset="0.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#f5a623" stroke-width="5" stroke-dasharray="25.0 75.0" stroke-dashoffset="-38.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#2979ff" stroke-width="5" stroke-dasharray="17.0 83.0" stroke-dashoffset="-63.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#00c853" stroke-width="5" stroke-dasharray="12.0 88.0" stroke-dashoffset="-80.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#9c27b0" stroke-width="5" stroke-dasharray="5.0 95.0" stroke-dashoffset="-92.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#546e7a" stroke-width="5" stroke-dasharray="3.0 97.0" stroke-dashoffset="-97.0" stroke-linecap="round"/><text x="21.0" y="19.0" text-anchor="middle" font-size="7" fill="#e8ecf4" font-weight="900">6</text><text x="21.0" y="24.5" text-anchor="middle" font-size="3.8" fill="#6b7a99">vectores</text></svg><div class="donut-legend"><div class="donut-leg-item"><span class="donut-dot" style="background:#ff5252"></span><span class="donut-leg-name">Credenciales comprometidas</span><span class="donut-leg-pct">38%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#f5a623"></span><span class="donut-leg-name">Vulnerabilidades web</span><span class="donut-leg-pct">25%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#2979ff"></span><span class="donut-leg-name">Phishing</span><span class="donut-leg-pct">17%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#00c853"></span><span class="donut-leg-name">VPN/Firewall</span><span class="donut-leg-pct">12%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#9c27b0"></span><span class="donut-leg-name">RDP expuesto</span><span class="donut-leg-pct">5%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#546e7a"></span><span class="donut-leg-name">Desconocido</span><span class="donut-leg-pct">3%</span></div></div></div><div style="padding:11px 14px;background:rgba(255,82,82,.07);border-radius:8px;border:1px solid rgba(255,82,82,.15);font-size:12px;color:var(--text-dim)">🔴 <strong style="color:var(--red-soft)">63% prevenible</strong> con parches aplicados + MFA + deshabilitar RDP expuesto.</div></div><div class="card"><div class="card-label">CVEs asociadas a grupos activos esta semana</div><div class="cve-list mt12"><div class="cve-item"><span class="cve-id">CVE-2023-3519</span><div class="cve-prod">Citrix ADC/Gateway <span style="display:inline-block;padding:2px 8px;border-radius:4px;font-size:10px;font-weight:800;font-family:monospace;background:rgba(229,57,53,.2);color:var(--red-soft);border:1px solid rgba(229,57,53,.3)">CVSS 9.8</span><small>Ejecución remota de código sin autenticación</small></div><div class="cve-groups"><span class="pill yellow" style="font-size:9px">qilin</span></div></div><div class="cve-item"><span class="cve-id">CVE-2024-21887</span><div class="cve-prod">Ivanti Connect Secure <span style="display:inline-block;padding:2px 8px;border-radius:4px;font-size:10px;font-weight:800;font-family:monospace;background:rgba(229,57,53,.2);color:var(--red-soft);border:1px solid rgba(229,57,53,.3)">CVSS 9.1</span><small>Omisión de autenticación en componentes críticos</small></div><div class="cve-groups"><span class="pill yellow" style="font-size:9px">qilin</span></div></div></div><div class="insight-box mt12" style="padding:11px 14px"><p style="font-size:11px">La actividad observada esta semana, con 2358 víctimas y una alta prevalencia de ataques de tipo combo_list y defacement, subraya una realidad crítica: la superficie de exposición es dinámica y constante. La persistencia de grupos como qilin, dirigidos a sectores estratégicos en Chile, demuestra que los atacantes no solo buscan el impacto inmediato, sino la explotación sostenida de accesos iniciales. Ante este panorama, la pregunta fundamental para su organización es: ¿cuánta de nuestra infraestructura crítica es hoy visible y accesible para actores que ya están operando activamente en nuestro entorno local?</p></div><div class="rec-cta" style="margin-top:10px">→ ¿Necesita verificar si su infraestructura está expuesta a estas CVEs? CompuNet puede realizar un análisis de vulnerabilidades priorizado.</div></div></div>
</div>

<div class="divider"></div>

<!-- ================================================================
     09 EVALUACION DE EXPOSICION
     ================================================================ -->
<div class="section">
  <div class="section-label">09 — Evaluacion de Exposicion</div>
  <div class="section-title">Tu organizacion esta preparada?</div>
  <div class="section-sub">Checklist de evaluacion rapida basado en las amenazas activas de esta semana. Cada item refleja un vector de riesgo real detectado en el ecosistema actual.</div>
  <div class="check-grid" style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
  <div class="check-item">
    <span class="check-icon">🔴</span>
    <div class="check-text">
      <h5>¿Sus dispositivos perimetrales tienen parches al día?</h5>
      <p>La actividad de grupos como 'thegentlemen' y la persistencia de actores de ransomware exigen una postura defensiva proactiva. Vulnerabilidades no mitigadas en el perímetro son la puerta de entrada principal para el compromiso de su infraestructura crítica.</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🔴</span>
    <div class="check-text">
      <h5>¿Tiene visibilidad de credenciales expuestas?</h5>
      <p>Con 774 incidentes de credenciales expuestas vía combo_list y logs esta semana, el riesgo de acceso no autorizado es inminente. ¿Sabe si sus credenciales corporativas ya circulan en foros de la dark web?</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🟡</span>
    <div class="check-text">
      <h5>¿Su red está segmentada contra movimiento lateral?</h5>
      <p>El grupo 'thegentlemen' lidera la actividad de ransomware, enfocándose en la explotación profunda de redes. Una red plana permite que un compromiso inicial escale rápidamente hacia el cifrado de sus activos más valiosos.</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🟡</span>
    <div class="check-text">
      <h5>¿Sus proveedores usan MFA?</h5>
      <p>La venta de accesos iniciales (initial_access) sigue siendo una amenaza latente, como se ha observado en el mercado chileno. Un proveedor comprometido puede ser el vector que burle sus controles de seguridad perimetrales.</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🟡</span>
    <div class="check-text">
      <h5>¿Puede detectar exfiltración antes del cifrado?</h5>
      <p>La doble extorsión es la norma en los ataques de ransomware actuales. Detectar el movimiento de datos hacia el exterior es su última línea de defensa antes de que la información sensible sea publicada o cifrada.</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🟡</span>
    <div class="check-text">
      <h5>¿Tiene plan de respuesta actualizado?</h5>
      <p>Ante el aumento de brechas en sectores como el Estado y la Educación en Chile, la Ley 21.663 exige una capacidad de respuesta ágil. ¿Está su organización preparada para notificar y contener un incidente bajo los estándares actuales?</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🔵</span>
    <div class="check-text">
      <h5>¿Recibe inteligencia de amenazas de su región?</h5>
      <p>Con 117 incidentes en LATAM esta semana, la amenaza es local y constante. Ignorar el contexto regional de grupos como 'qilin' o 'nyxargroup' le deja ciego ante las tácticas específicas que afectan a sus pares en Chile.</p>
    </div>
  </div>
  <div class="check-item">
    <span class="check-icon">🔵</span>
    <div class="check-text">
      <h5>¿Cuándo fue su último ejercicio de simulación?</h5>
      <p>La aparición de grupos nuevos como 'maw3six', 'coder' y 'mailaccesss' demuestra un ecosistema de amenazas en constante evolución. Solo mediante simulaciones puede validar si sus controles actuales detendrían a estos nuevos actores.</p>
    </div>
  </div>
</div>

<div style="margin-top:14px;padding:12px 16px;background:rgba(229,57,53,.06);border:1px solid rgba(229,57,53,.15);border-radius:10px;font-size:12px;color:var(--text-dim)">⚠️ <strong style="color:var(--red-soft)">¿Identificó 3 o más áreas sin cobertura?</strong> Su organización podría tener exposición significativa a las amenazas documentadas esta semana.</div>
</div>

<div class="divider"></div>

<!-- ================================================================
     10 RECOMENDACIONES ACCIONABLES
     ================================================================ -->
<div class="section">
  <div class="section-label">10 — Recomendaciones Accionables</div>
  <div class="alert-list">
  <div class="alert-row" style="border-left:3px solid var(--red-soft)">
    <span class="alert-badge">CRÍTICA</span>
    <div class="alert-content">
      <h4>Actividad persistente de Ransomware en Chile: qilin y otros actores</h4>
      <p>Durante el periodo reciente, se ha confirmado la actividad de grupos como qilin afectando a entidades en Chile, incluyendo SAAM Towage y Noi Hotels. Estos incidentes de ransomware impactan directamente la continuidad operativa y la integridad de los activos digitales. ¿Su organización tiene visibilidad sobre la resiliencia de sus procesos críticos ante un evento de cifrado?</p>
    </div>
  </div>
  <div class="rec-cta">→ ¿Necesita validar su preparación ante ransomware? CompuNet realiza simulaciones de ataque dirigidas.</div>

  <div class="alert-row" style="border-left:3px solid var(--red-soft)">
    <span class="alert-badge">CRÍTICA</span>
    <div class="alert-content">
      <h4>Exposición masiva de credenciales y acceso inicial</h4>
      <p>Con 774 credenciales expuestas a través de combo_lists y logs, sumado a la venta de accesos no autorizados detectada en Chile por grupos como ed1n1ca, el riesgo de intrusión es elevado. La disponibilidad de estos datos en canales como openweb y telegram facilita el acceso no autorizado a sistemas corporativos. ¿Puede su equipo identificar si sus credenciales corporativas están circulando en canales de distribución activos?</p>
    </div>
  </div>
  <div class="rec-cta">→ CompuNet puede verificar si sus credenciales corporativas están circulando en canales de distribución activos.</div>

  <div class="alert-row" style="border-left:3px solid var(--yellow)">
    <span class="alert-badge">ALTA</span>
    <div class="alert-content">
      <h4>Brechas de datos en el sector público y educación</h4>
      <p>Se ha registrado una serie de brechas de datos afectando a instituciones como el Servicio de Registro Civil e Identificación, además de diversas universidades en Chile, atribuidas a actores como nyxargroup y gordonfreeman. Estos incidentes comprometen información sensible y el cumplimiento regulatorio de las entidades. ¿Su organización tiene mapeada la exposición de sus activos frente a actores que buscan extraer información sensible?</p>
    </div>
  </div>
  <div class="rec-cta">→ CompuNet ofrece evaluaciones de exposición para instituciones del sector público y educación.</div>

  <div class="alert-row" style="border-left:3px solid var(--yellow)">
    <span class="alert-badge">ALTA</span>
    <div class="alert-content">
      <h4>Oleada de defacements y alteración de presencia digital</h4>
      <p>Con 582 incidentes de defacement a nivel global y actividad específica en Chile por grupos como chinafans, nicotine y babayo eror system, la reputación digital de las empresas está bajo amenaza constante. Estas alteraciones no autorizadas pueden ser el preludio de ataques más complejos. ¿Su equipo puede detectar alteraciones no autorizadas en su superficie de ataque antes de que afecten su imagen?</p>
    </div>
  </div>
  <div class="rec-cta">→ ¿Su equipo puede detectar alteraciones no autorizadas? Consulte por monitoreo continuo de superficie de ataque.</div>

  <div class="alert-row" style="border-left:3px solid var(--blue)">
    <span class="alert-badge">MEDIA</span>
    <div class="alert-content">
      <h4>Concentración de amenazas en el sector TI y Finanzas</h4>
      <p>El sector de Tecnología de la Información (267 víctimas) y Finanzas y Banca (82 víctimas) lideran la lista de sectores afectados a nivel global esta semana. Esta tendencia subraya que las organizaciones que gestionan infraestructura crítica o datos financieros son objetivos primarios para diversos grupos de amenazas. ¿Su organización cuenta con inteligencia de amenazas específica para anticipar riesgos en su sector?</p>
    </div>
  </div>
  <div class="rec-cta">→ Suscríbase al servicio de Threat Intelligence de CompuNet para alertas tempranas en su sector.</div>

  <div class="alert-row" style="border-left:3px solid var(--blue)">
    <span class="alert-badge">INFO</span>
    <div class="alert-content">
      <h4>Panorama de amenazas en LATAM</h4>
      <p>Con 117 incidentes reportados en LATAM durante esta semana y una actividad constante en Chile, el panorama regional exige una postura de vigilancia proactiva. La diversidad de grupos activos en el territorio, desde defacers hasta actores de ransomware, requiere un entendimiento profundo del entorno local. ¿Puede su equipo evaluar el nivel de exposición regional de su infraestructura?</p>
    </div>
  </div>
  <div class="rec-cta">→ Solicite una evaluación de exposición regional sin costo: ciberseguridad@compunetgroup.net</div>
</div>
</div>

<!-- ================================================================
     11 PANORAMA DE AMENAZAS DIGITALES
     ================================================================ -->

<div class="divider"></div>
<div class="section">
  <div class="section-label">11 — Panorama de Amenazas Digitales</div>
  <div class="section-title">Mas alla del ransomware: el ecosistema completo de amenazas</div>
  <div class="section-sub">Analisis integral de la actividad en Dark Web, foros de cibercrimen y canales de Telegram. Incluye filtraciones de credenciales, DDoS, defacements, breaches y actividad hacktivista.</div>
  <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:16px"><div class="card" style="text-align:center;padding:16px"><div style="font-size:28px;font-weight:900;color:var(--text)">2,093</div><div style="font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px">Total incidentes</div></div><div class="card" style="text-align:center;padding:16px"><div style="font-size:28px;font-weight:900;color:#06b6d4">774</div><div style="font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px">Credenciales expuestas</div></div><div class="card" style="text-align:center;padding:16px"><div style="font-size:28px;font-weight:900;color:#9ca3af">132</div><div style="font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px">Ataques DDoS</div></div><div class="card" style="text-align:center;padding:16px"><div style="font-size:28px;font-weight:900;color:#a78bfa">582</div><div style="font-size:10px;color:var(--text-muted);text-transform:uppercase;letter-spacing:1px">Defacements</div></div></div><div class="cards cards-2-1"><div class="card"><div class="card-label">Distribucion por tipo de amenaza</div><div class="donut-wrap mt10"><svg width="110" height="110" viewBox="0 0 42 42"><circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#1c2438" stroke-width="5"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#ff5252" stroke-width="5" stroke-dasharray="36.8 63.2" stroke-dashoffset="0.0" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#f5a623" stroke-width="5" stroke-dasharray="30.3 69.7" stroke-dashoffset="-36.8" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#2979ff" stroke-width="5" stroke-dasharray="11.2 88.8" stroke-dashoffset="-67.2" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#00c853" stroke-width="5" stroke-dasharray="9.5 90.5" stroke-dashoffset="-78.3" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#9c27b0" stroke-width="5" stroke-dasharray="6.9 93.1" stroke-dashoffset="-87.8" stroke-linecap="round"/>
<circle cx="21.0" cy="21.0" r="15.915" fill="none" stroke="#546e7a" stroke-width="5" stroke-dasharray="5.3 94.7" stroke-dashoffset="-94.7" stroke-linecap="round"/><text x="21.0" y="19.0" text-anchor="middle" font-size="7" fill="#e8ecf4" font-weight="900">2093</text><text x="21.0" y="24.5" text-anchor="middle" font-size="3.8" fill="#6b7a99">incidentes</text></svg><div class="donut-legend"><div class="donut-leg-item"><span class="donut-dot" style="background:#ff5252"></span><span class="donut-leg-name">Combo List</span><span class="donut-leg-pct">37%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#f5a623"></span><span class="donut-leg-name">Defacement</span><span class="donut-leg-pct">30%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#2979ff"></span><span class="donut-leg-name">Data Breach</span><span class="donut-leg-pct">11%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#00c853"></span><span class="donut-leg-name">Data Leak</span><span class="donut-leg-pct">9%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#9c27b0"></span><span class="donut-leg-name">DDoS</span><span class="donut-leg-pct">7%</span></div>
<div class="donut-leg-item"><span class="donut-dot" style="background:#546e7a"></span><span class="donut-leg-name">Cyber Attack</span><span class="donut-leg-pct">5%</span></div></div></div></div><div style="display:flex;flex-direction:column;gap:14px"><div class="card"><div class="card-label">Redes de distribucion</div><div style="margin-top:10px"><div style="margin-bottom:8px"><div style="display:flex;justify-content:space-between;font-size:11px;margin-bottom:3px"><span style="font-weight:600">Foros/Web</span><span style="color:var(--text-muted)">1,683 (80%)</span></div><div style="background:var(--bg-card2);border-radius:4px;height:8px;overflow:hidden"><div style="width:80%;height:100%;background:#f59e0b;border-radius:4px"></div></div></div><div style="margin-bottom:8px"><div style="display:flex;justify-content:space-between;font-size:11px;margin-bottom:3px"><span style="font-weight:600">Telegram</span><span style="color:var(--text-muted)">409 (20%)</span></div><div style="background:var(--bg-card2);border-radius:4px;height:8px;overflow:hidden"><div style="width:20%;height:100%;background:#0088cc;border-radius:4px"></div></div></div></div></div></div></div><div class="card" style="margin-top:14px"><div class="card-label">Top actores de amenaza (no ransomware)</div><div style="margin-top:8px"><div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:11px;font-weight:800;color:var(--text-muted);width:18px">1</span><span style="font-size:13px;font-weight:700">dimashxr</span></div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:10px;padding:2px 8px;border-radius:12px;background:#a78bfa22;color:#a78bfa;font-weight:600">Defacement</span><span style="font-size:13px;font-weight:800">239</span></div></div><div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:11px;font-weight:800;color:var(--text-muted);width:18px">2</span><span style="font-size:13px;font-weight:700">nicotine</span></div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:10px;padding:2px 8px;border-radius:12px;background:#a78bfa22;color:#a78bfa;font-weight:600">Defacement</span><span style="font-size:13px;font-weight:800">121</span></div></div><div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:11px;font-weight:800;color:var(--text-muted);width:18px">3</span><span style="font-size:13px;font-weight:700">maw3six</span></div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:10px;padding:2px 8px;border-radius:12px;background:#a78bfa22;color:#a78bfa;font-weight:600">Defacement</span><span style="font-size:13px;font-weight:800">60</span></div></div><div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:11px;font-weight:800;color:var(--text-muted);width:18px">4</span><span style="font-size:13px;font-weight:700">coder</span></div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:10px;padding:2px 8px;border-radius:12px;background:#06b6d422;color:#06b6d4;font-weight:600">Combo List</span><span style="font-size:13px;font-weight:800">58</span></div></div><div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)"><div style="display:flex;align-items:center;gap:8px"><span style="font-size:11px;font-weight:800;color:var(--text-muted);width:18px">5</span><span style="font-size:13px;font-weight:700">thejackal101</span></div><div style="display:flex;align-items:center;gap:8px"><span style="font-size:10px;padding:2px 8px;border-radius:12px;background:#06b6d422;color:#06b6d4;font-weight:600">Combo List</span><span style="font-size:13px;font-weight:800">42</span></div></div></div></div>
</div>


<!-- ================================================================
     12 ACTIVIDAD EN DARK WEB Y CREDENCIALES (AI)
     ================================================================ -->

<div class="divider"></div>
<div class="section">
  <div class="section-label">12 — Dark Web y Credenciales</div>
  <div class="section-title">Inteligencia de amenazas: actividad en Dark Web</div>
  <div class="section-sub">Analisis de la exposicion de credenciales, filtraciones de datos y actividad hacktivista detectada esta semana en canales de Telegram, foros y la Dark Web.</div>
  <div class="cards cards-2">
    <div class="card cyan-top">
  <div class="card-label">🔵 Exposición de Credenciales</div>
  <div class="card-title">Volumen crítico de accesos expuestos</div>
  <div class="card-body">Esta semana se identificaron <strong style="color:var(--cyan)">774</strong> credenciales expuestas mediante combo_lists y logs. Con <strong style="color:var(--cyan)">706</strong> incidentes de tipo combo_list registrados, la persistencia de actores como coder y thejackal101 subraya la alta probabilidad de que accesos corporativos estén siendo comercializados. ¿Está su estrategia de autenticación preparada para detectar el uso de credenciales legítimas comprometidas?</div>
</div>

<div class="card yellow-top">
  <div class="card-label">🟠 Breaches y Filtraciones</div>
  <div class="card-title">Impacto masivo en datos sensibles</div>
  <div class="card-body">Se registraron <strong style="color:var(--yellow)">214</strong> brechas y <strong style="color:var(--yellow)">182</strong> filtraciones globales, afectando sectores críticos como el Estado y la Educación. Incidentes de gran escala, como la exposición de 15 millones de registros en plataformas GNUBoard, demuestran la vulnerabilidad de los repositorios de datos. ¿Cómo garantiza su organización la integridad de los datos de sus usuarios ante brechas de terceros?</div>
</div>

<div class="card blue-top">
  <div class="card-label">🟣 Actividad Hacktivista</div>
  <div class="card-title">Alta incidencia en defacement y DDoS</div>
  <div class="card-body">La actividad hacktivista mantiene una presencia agresiva con <strong style="color:var(--blue)">582</strong> defacements y <strong style="color:var(--blue)">132</strong> ataques DDoS. Grupos como dimashxr y nicotine lideran esta tendencia, utilizando principalmente openweb y Telegram para la distribución. Ante esta visibilidad, ¿cuenta su infraestructura con la resiliencia necesaria para mitigar interrupciones de servicio y proteger su reputación digital?</div>
</div>

<div class="card red-top">
  <div class="card-label">🔴 Señales Emergentes</div>
  <div class="card-title">Comercialización de accesos iniciales</div>
  <div class="card-body">La detección de <strong style="color:var(--red)">66</strong> incidentes de initial_access y la aparición de nuevos actores como maw3six y coder señalan una profesionalización en la venta de puntos de entrada. La convergencia de estas amenazas con <strong style="color:var(--red)">102</strong> ataques cibernéticos genéricos exige una revisión profunda. ¿Es su visibilidad actual suficiente para detectar intentos de acceso no autorizado antes de que escalen a un incidente mayor?</div>
</div>
  </div>
</div>


<!-- ================================================================
     CTA
     ================================================================ -->
<div class="section" style="margin-bottom:0">
  <div class="section-label">13 — Proximos Pasos</div>
</div>
<div class="cta-section">
  <div style="position:relative;z-index:1">
    <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:2px;color:var(--accent);margin-bottom:10px">CompuNet — Ciberseguridad para Latinoamerica</div>
    <h2 class="cta-title">Las amenazas documentadas<br>requieren <span>accion</span></h2>
    <p class="cta-body">CompuNet acompaña a organizaciones en Chile y LATAM en cada etapa — desde la evaluacion de exposicion hasta la respuesta a incidentes.</p>
    <div class="services-grid">
      <div class="service-item"><h5>Evaluacion de Exposicion</h5><p>Identifica vulnerabilidades antes que el atacante. Sin costo inicial.</p></div>
      <div class="service-item"><h5>CTEM Continuo</h5><p>Gestion de exposicion a amenazas en tiempo real.</p></div>
      <div class="service-item"><h5>Threat Intelligence</h5><p>IOCs, TTPs y alertas de grupos activos en Chile y LATAM.</p></div>
      <div class="service-item"><h5>Respuesta a Incidentes</h5><p>Equipo especializado 24/7. Preparacion y respuesta.</p></div>
    </div>
    <a class="cta-btn" href="mailto:hola@compunetgroup.net">Solicitar Evaluacion Gratuita →</a>
  </div>
  <div class="contact-card" style="position:relative;z-index:1">
    <h4>Contactanos</h4>
    <div class="contact-row"><span class="contact-icon">📞</span><div class="contact-info"><h5>Telefono</h5><p>+562 2584 7213</p></div></div>
    <div class="contact-row"><span class="contact-icon">✉️</span><div class="contact-info"><h5>Email</h5><p>hola@compunetgroup.net</p></div></div>
    <div class="contact-row"><span class="contact-icon">🌐</span><div class="contact-info"><h5>Web</h5><p>www.compunetgroup.net</p></div></div>
    <div class="contact-row"><span class="contact-icon">📍</span><div class="contact-info"><h5>Direccion</h5><p>Rodo 1969, Of. 104 · Providencia, Santiago, Chile</p></div></div>
    <div class="contact-logo-block">
      <div class="cn">CompuNet</div>
      <div class="ct"><span class="hash">#</span><span class="rest">JuntosMasLejos</span></div>
      <small>Protegemos tu informacion</small>
    </div>
  </div>
</div>

<!-- ================================================================
     FOOTER
     ================================================================ -->
<div class="footer-strip">
  <div style="display:flex;align-items:center;gap:20px">
    <div class="footer-logo">
      <span class="fn">CompuNet</span>
      <span class="ft"><span class="hash">#</span><span class="rest">JuntosMasLejos</span></span>
    </div>
    <div class="fmeta">
      <span>Threat Intelligence Report</span>
      <span>Semana 06/04/2026 – 12/04/2026</span>
    </div>
  </div>
  <span style="font-size:10px;color:var(--text-muted)">www.compunetgroup.net</span>
</div>

</body>
</html>
