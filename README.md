<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Area, Volume and Capacity</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Grade 6 Mathematics · Chapter 10</div>
  <div class="chapter-title">Area, Volume and Capacity</div>
  <div class="chapter-sub">Exercises 10A–10F · Review Sets · Step-by-Step Practice</div><div class="chapter-credit">Follows Haese Mathematics 6 (MYP 1), Chapter 10</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Grade 6 Mathematics<br>Exercises follow the structure of <i>Mathematics 6 (MYP 1), 3rd edition</i>, Haese Mathematics. Questions, steps and solutions written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')') && (a.k==='n'||a.k==='v'||a.k==='(')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(\d+)(?: |\+|-)(\d+)\/(\d+)$/))){ if(+m[3]===0) return null; return {v:+m[1]+m[2]/m[3],form:'mixed',w:+m[1],n:+m[2],d:+m[3]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ return wordsNorm(a)===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null) return Math.abs(n1-n2)<1e-3;
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var SECTIONS = [{"id": "s1", "label": "Ex 10A", "sub": "Area", "slides": [{"kind": "blank", "p": "Match each description with its most likely area (A 0.8 km², B 100 cm², C 5 m², D 7.5 cm², E 600 m², F 7 mm², G 3 287 000 km², H 20 000 m²). Type the letter.", "tag": "", "marks": "", "flat": [{"t": "a) a picnic rug → __B1__", "a": {"B1": "C"}}, {"t": "b) a sports stadium → __B1__", "a": {"B1": "H"}}, {"t": "c) India → __B1__", "a": {"B1": "G"}}, {"t": "d) a drink coaster → __B1__", "a": {"B1": "B"}}, {"t": "e) a small dot on a page → __B1__", "a": {"B1": "F"}}, {"t": "f) a golf course → __B1__", "a": {"B1": "A"}}, {"t": "g) a small park → __B1__", "a": {"B1": "E"}}, {"t": "h) a coin → __B1__", "a": {"B1": "D"}}], "sol": "Use the size of each unit: mm² tiny, cm² hand-sized, m² room-sized, km² land and countries."}, {"kind": "blank", "p": "Each small square has area 1 cm². Count the squares to find each area.", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm²", "a": {"B1": "14"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 116\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh\" x=\"102.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"102.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"102.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"126.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"126.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"126.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"150.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"150.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"150.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"174.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"174.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"174.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"126.0\" y=\"82\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"150.0\" y=\"82\" width=\"24\" height=\"24\"/></svg>", "expr": "dec"}, {"t": "b) __B1__ cm²", "a": {"B1": "7"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 92\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh\" x=\"102.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"102.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"102.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"126.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"150.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"174.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"174.0\" y=\"34\" width=\"24\" height=\"24\"/></svg>", "expr": "dec"}, {"t": "c) __B1__ cm²", "a": {"B1": "11"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 140\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"sh\" x=\"138.0\" y=\"10\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"114.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"138.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"162.0\" y=\"34\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"90.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"114.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"138.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"162.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"186.0\" y=\"58\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"138.0\" y=\"82\" width=\"24\" height=\"24\"/><rect class=\"sh\" x=\"138.0\" y=\"106\" width=\"24\" height=\"24\"/></svg>", "expr": "dec"}], "sol": "a) 14 squares\nb) 7 squares\nc) 11 squares"}, {"kind": "blank", "p": "A kitchen wall is covered by tiles in 5 rows of 8.", "tag": "", "marks": "", "flat": [{"t": "a) Number of tiles: __B1__", "a": {"B1": "40"}, "expr": "dec"}, {"t": "b) 20 tiles cover 1 m². Area of tiles: __B1__ m²", "a": {"B1": "2"}, "expr": "dec"}, {"t": "c) Tiles cost ₹440 per m². Cost: ₹__B1__", "a": {"B1": "880"}, "expr": "dec"}], "sol": "a) 5 × 8 = 40\nb) 40 ÷ 20 = 2 m²\nc) 2 × 440 = ₹880"}, {"kind": "blank", "p": "A driveway has 10 rows of 28 pavers and a courtyard has 30 rows of 18 identical pavers.", "tag": "", "marks": "", "flat": [{"t": "a) Pavers in the driveway: __B1__", "a": {"B1": "280"}, "expr": "dec"}, {"t": "b) Pavers in the courtyard: __B1__", "a": {"B1": "540"}, "expr": "dec"}, {"t": "c) 50 pavers cover 1 m². Total paved area: __B1__ m²", "a": {"B1": "16.4"}, "expr": "dec"}, {"t": "d) Pavers cost ₹320 per m² and laying costs ₹280 per m². Total cost: ₹__B1__", "a": {"B1": "9840"}, "expr": "dec"}], "sol": "a) 10 × 28 = 280\nb) 30 × 18 = 540\nc) (280 + 540) ÷ 50 = 16.4 m²\nd) 16.4 × (320 + 280) = ₹9840"}]}, {"id": "s2", "label": "Ex 10B", "sub": "The area of a rectangle", "slides": [{"kind": "blank", "p": "Find the area of each rectangle (area = length × width):", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm²", "a": {"B1": "10"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"30.0,32.0 270.0,32.0 270.0,128.0 30.0,128.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"26.0\" x2=\"150.0\" y2=\"38.0\"/><line class=\"tick\" x1=\"276.0\" y1=\"77.5\" x2=\"264.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"276.0\" y1=\"82.5\" x2=\"264.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"134.0\" x2=\"150.0\" y2=\"122.0\"/><line class=\"tick\" x1=\"24.0\" y1=\"82.5\" x2=\"36.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"24.0\" y1=\"77.5\" x2=\"36.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M30.0,41.0 L39.0,41.0 L39.0,32.0\"/><path class=\"ra\" d=\"M261.0,32.0 L261.0,41.0 L270.0,41.0\"/><path class=\"ra\" d=\"M270.0,119.0 L261.0,119.0 L261.0,128.0\"/><path class=\"ra\" d=\"M39.0,128.0 L39.0,119.0 L30.0,119.0\"/><text class=\"al\" x=\"295.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2 cm</text><text class=\"al\" x=\"150.0\" y=\"143.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5 cm</text></svg>", "expr": "dec"}, {"t": "b) __B1__ km²", "a": {"B1": "140"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"80.0,30.0 220.0,30.0 220.0,130.0 80.0,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"226.0\" y1=\"77.5\" x2=\"214.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"226.0\" y1=\"82.5\" x2=\"214.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"74.0\" y1=\"82.5\" x2=\"86.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"74.0\" y1=\"77.5\" x2=\"86.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M80.0,39.0 L89.0,39.0 L89.0,30.0\"/><path class=\"ra\" d=\"M211.0,30.0 L211.0,39.0 L220.0,39.0\"/><path class=\"ra\" d=\"M220.0,121.0 L211.0,121.0 L211.0,130.0\"/><path class=\"ra\" d=\"M89.0,130.0 L89.0,121.0 L80.0,121.0\"/><text class=\"al\" x=\"245.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 km</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">14 km</text></svg>", "expr": "dec"}, {"t": "c) __B1__ m²", "a": {"B1": "32"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"50.0,30.0 250.0,30.0 250.0,130.0 50.0,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"256.0\" y1=\"77.5\" x2=\"244.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"256.0\" y1=\"82.5\" x2=\"244.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"44.0\" y1=\"82.5\" x2=\"56.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"44.0\" y1=\"77.5\" x2=\"56.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M50.0,39.0 L59.0,39.0 L59.0,30.0\"/><path class=\"ra\" d=\"M241.0,30.0 L241.0,39.0 L250.0,39.0\"/><path class=\"ra\" d=\"M250.0,121.0 L241.0,121.0 L241.0,130.0\"/><path class=\"ra\" d=\"M59.0,130.0 L59.0,121.0 L50.0,121.0\"/><text class=\"al\" x=\"275.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4 m</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 m</text></svg>", "expr": "dec"}, {"t": "d) __B1__ m²", "a": {"B1": "36"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"100.0,30.0 200.0,30.0 200.0,130.0 100.0,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"206.0\" y1=\"80.0\" x2=\"194.0\" y2=\"80.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"94.0\" y1=\"80.0\" x2=\"106.0\" y2=\"80.0\"/><path class=\"ra\" d=\"M100.0,39.0 L109.0,39.0 L109.0,30.0\"/><path class=\"ra\" d=\"M191.0,30.0 L191.0,39.0 L200.0,39.0\"/><path class=\"ra\" d=\"M200.0,121.0 L191.0,121.0 L191.0,130.0\"/><path class=\"ra\" d=\"M109.0,130.0 L109.0,121.0 L100.0,121.0\"/><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6 m</text></svg>", "expr": "dec"}, {"t": "e) __B1__ km²", "a": {"B1": "39"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"30.0,52.3 270.0,52.3 270.0,107.7 30.0,107.7\"/><line class=\"tick\" x1=\"150.0\" y1=\"46.3\" x2=\"150.0\" y2=\"58.3\"/><line class=\"tick\" x1=\"276.0\" y1=\"77.5\" x2=\"264.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"276.0\" y1=\"82.5\" x2=\"264.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"113.7\" x2=\"150.0\" y2=\"101.7\"/><line class=\"tick\" x1=\"24.0\" y1=\"82.5\" x2=\"36.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"24.0\" y1=\"77.5\" x2=\"36.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M30.0,61.3 L39.0,61.3 L39.0,52.3\"/><path class=\"ra\" d=\"M261.0,52.3 L261.0,61.3 L270.0,61.3\"/><path class=\"ra\" d=\"M270.0,98.7 L261.0,98.7 L261.0,107.7\"/><path class=\"ra\" d=\"M39.0,107.7 L39.0,98.7 L30.0,98.7\"/><text class=\"al\" x=\"295.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 km</text><text class=\"al\" x=\"150.0\" y=\"122.7\" text-anchor=\"middle\" dominant-baseline=\"middle\">13 km</text></svg>", "expr": "dec"}, {"t": "f) __B1__ cm²", "a": {"B1": "72.8"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"93.1,30.0 206.9,30.0 206.9,130.0 93.1,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"212.9\" y1=\"77.5\" x2=\"200.9\" y2=\"77.5\"/><line class=\"tick\" x1=\"212.9\" y1=\"82.5\" x2=\"200.9\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"87.1\" y1=\"82.5\" x2=\"99.1\" y2=\"82.5\"/><line class=\"tick\" x1=\"87.1\" y1=\"77.5\" x2=\"99.1\" y2=\"77.5\"/><path class=\"ra\" d=\"M93.1,39.0 L102.1,39.0 L102.1,30.0\"/><path class=\"ra\" d=\"M197.9,30.0 L197.9,39.0 L206.9,39.0\"/><path class=\"ra\" d=\"M206.9,121.0 L197.9,121.0 L197.9,130.0\"/><path class=\"ra\" d=\"M102.1,130.0 L102.1,121.0 L93.1,121.0\"/><text class=\"al\" x=\"231.9\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 cm</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">9.1 cm</text></svg>", "expr": "dec"}, {"t": "g) __B1__ cm²", "a": {"B1": "1200"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"83.3,30.0 216.7,30.0 216.7,130.0 83.3,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"222.7\" y1=\"77.5\" x2=\"210.7\" y2=\"77.5\"/><line class=\"tick\" x1=\"222.7\" y1=\"82.5\" x2=\"210.7\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"77.3\" y1=\"82.5\" x2=\"89.3\" y2=\"82.5\"/><line class=\"tick\" x1=\"77.3\" y1=\"77.5\" x2=\"89.3\" y2=\"77.5\"/><path class=\"ra\" d=\"M83.3,39.0 L92.3,39.0 L92.3,30.0\"/><path class=\"ra\" d=\"M207.7,30.0 L207.7,39.0 L216.7,39.0\"/><path class=\"ra\" d=\"M216.7,121.0 L207.7,121.0 L207.7,130.0\"/><path class=\"ra\" d=\"M92.3,130.0 L92.3,121.0 L83.3,121.0\"/><text class=\"al\" x=\"241.7\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30 cm</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40 cm</text></svg>", "expr": "dec"}, {"t": "h) __B1__ cm²", "a": {"B1": "4.5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"50.0,30.0 250.0,30.0 250.0,130.0 50.0,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"256.0\" y1=\"77.5\" x2=\"244.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"256.0\" y1=\"82.5\" x2=\"244.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"44.0\" y1=\"82.5\" x2=\"56.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"44.0\" y1=\"77.5\" x2=\"56.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M50.0,39.0 L59.0,39.0 L59.0,30.0\"/><path class=\"ra\" d=\"M241.0,30.0 L241.0,39.0 L250.0,39.0\"/><path class=\"ra\" d=\"M250.0,121.0 L241.0,121.0 L241.0,130.0\"/><path class=\"ra\" d=\"M59.0,130.0 L59.0,121.0 L50.0,121.0\"/><text class=\"al\" x=\"275.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1.5 cm</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 cm</text></svg>", "expr": "dec"}, {"t": "i) __B1__ m²", "a": {"B1": "102"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"79.4,30.0 220.6,30.0 220.6,130.0 79.4,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"226.6\" y1=\"77.5\" x2=\"214.6\" y2=\"77.5\"/><line class=\"tick\" x1=\"226.6\" y1=\"82.5\" x2=\"214.6\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"73.4\" y1=\"82.5\" x2=\"85.4\" y2=\"82.5\"/><line class=\"tick\" x1=\"73.4\" y1=\"77.5\" x2=\"85.4\" y2=\"77.5\"/><path class=\"ra\" d=\"M79.4,39.0 L88.4,39.0 L88.4,30.0\"/><path class=\"ra\" d=\"M211.6,30.0 L211.6,39.0 L220.6,39.0\"/><path class=\"ra\" d=\"M220.6,121.0 L211.6,121.0 L211.6,130.0\"/><path class=\"ra\" d=\"M88.4,130.0 L88.4,121.0 L79.4,121.0\"/><text class=\"al\" x=\"245.6\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8.5 m</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12 m</text></svg>", "expr": "dec"}], "sol": "Area of a rectangle = length × width.\na) 5 × 2 = 10 cm²\nb) 14 × 10 = 140 km²\nc) 8 × 4 = 32 m²\nd) 6 × 6 = 36 m²\ne) 13 × 3 = 39 km²\nf) 9.1 × 8 = 72.8 cm²\ng) 40 × 30 = 1200 cm²\nh) 3 × 1.5 = 4.5 cm²\ni) 12 × 8.5 = 102 m²"}, {"kind": "blank", "p": "Meera's tablet screen is 24 cm by 19 cm. Gauri's is 26 cm by 18 cm.", "tag": "", "marks": "", "flat": [{"t": "a) Meera's screen area: __B1__ cm²", "a": {"B1": "456"}, "expr": "dec"}, {"t": "b) Gauri's screen area: __B1__ cm²", "a": {"B1": "468"}, "expr": "dec"}, {"t": "c) Whose screen is larger? __B1__", "a": {"B1": "Gauri"}}], "sol": "a) 24 × 19 = 456\nb) 26 × 18 = 468\nc) Gauri's"}, {"kind": "blank", "p": "A 12 m by 10 m lawn is to be seeded. Seed costs ₹80 per m².", "tag": "", "marks": "", "flat": [{"t": "a) Area: __B1__ m²", "a": {"B1": "120"}, "expr": "dec"}, {"t": "b) Cost: ₹__B1__", "a": {"B1": "9600"}, "expr": "dec"}], "sol": "a) 12 × 10 = 120 m²\nb) 120 × 80 = ₹9600"}, {"kind": "blank", "p": "A 6 m by 7.5 m ceiling is painted. One litre of paint covers 15 m².", "tag": "", "marks": "", "flat": [{"t": "a) Area: __B1__ m²", "a": {"B1": "45"}, "expr": "dec"}, {"t": "b) Paint needed: __B1__ L", "a": {"B1": "3"}, "expr": "dec"}], "sol": "a) 6 × 7.5 = 45 m²\nb) 45 ÷ 15 = 3 L"}, {"kind": "blank", "p": "A rectangular pool is 8 m long and 4.6 m wide. Find its:", "tag": "", "marks": "", "flat": [{"t": "a) perimeter: __B1__ m", "a": {"B1": "25.2"}, "expr": "dec"}, {"t": "b) area: __B1__ m²", "a": {"B1": "36.8"}, "expr": "dec"}], "sol": "a) 2 × 8 + 2 × 4.6 = 25.2 m\nb) 8 × 4.6 = 36.8 m²"}, {"kind": "blank", "p": "An A4 sheet of paper is 29.7 cm by 21 cm. Find its area.", "tag": "", "marks": "", "flat": [{"t": "__B1__ cm²", "a": {"B1": "623.7"}, "expr": "dec"}], "sol": "29.7 × 21 = 623.7 cm²"}, {"kind": "blank", "p": "A 4.8 m by 6 m room has a 2 m by 2.8 m rug. Find the area of floor not covered.", "tag": "", "marks": "", "flat": [{"t": "__B1__ m²", "a": {"B1": "23.2"}, "expr": "dec"}], "sol": "room 28.8 m² − rug 5.6 m² = 23.2 m²"}, {"kind": "blank", "p": "A 6 m by 5 m backyard has a 2 m by 4 m paved area and a 3 m by 4 m lawn. The rest is garden bed.", "tag": "", "marks": "", "flat": [{"t": "a) whole backyard: __B1__ m²", "a": {"B1": "30"}, "expr": "dec"}, {"t": "b) paved area: __B1__ m²", "a": {"B1": "8"}, "expr": "dec"}, {"t": "c) lawn: __B1__ m²", "a": {"B1": "12"}, "expr": "dec"}, {"t": "d) garden bed: __B1__ m²", "a": {"B1": "10"}, "expr": "dec"}], "sol": "a) 6 × 5 = 30\nb) 2 × 4 = 8\nc) 3 × 4 = 12\nd) 30 − 8 − 12 = 10"}, {"kind": "blank", "p": "A shower base is 1.2 m by 90 cm. It is covered with tiles 6 cm by 5 cm.", "tag": "", "marks": "", "flat": [{"t": "a) Area of the base: __B1__ cm²", "a": {"B1": "10800"}, "expr": "dec"}, {"t": "b) Area of each tile: __B1__ cm²", "a": {"B1": "30"}, "expr": "dec"}, {"t": "c) Tiles needed: __B1__", "a": {"B1": "360"}, "expr": "dec"}], "sol": "a) 120 × 90 = 10 800 cm² (write both lengths in cm)\nb) 6 × 5 = 30 cm²\nc) 10 800 ÷ 30 = 360"}]}, {"id": "s3", "label": "Ex 10C", "sub": "The area of a triangle", "slides": [{"kind": "blank", "p": "Find the area of each triangle (area = ½ × base × height):", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ m²", "a": {"B1": "30"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"30.0,140.0 270.0,140.0 270.0,40.0\"/><line class=\"ln hid\" x1=\"270.0\" y1=\"40.0\" x2=\"270.0\" y2=\"140.0\"/><path class=\"ra\" d=\"M270.0,132.0 L262.0,132.0 L262.0,140.0\"/><text class=\"al\" x=\"150.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12 m</text><text class=\"al\" x=\"260.0\" y=\"90.0\" text-anchor=\"end\" dominant-baseline=\"middle\">5 m</text></svg>", "expr": "dec"}, {"t": "b) __B1__ m²", "a": {"B1": "24"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"70.0,150.0 230.0,150.0 70.0,30.0\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"30.0\" x2=\"70.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M70.0,142.0 L78.0,142.0 L78.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 m</text><text class=\"al\" x=\"80.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">6 m</text></svg>", "expr": "dec"}, {"t": "c) __B1__ cm²", "a": {"B1": "21"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"80.0,150.0 220.0,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7 cm</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">6 cm</text></svg>", "expr": "dec"}, {"t": "d) __B1__ cm²", "a": {"B1": "7.5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"138.0,150.0 210.0,150.0 90.0,30.0\"/><line class=\"ln hid\" x1=\"138.0\" y1=\"150.0\" x2=\"90.0\" y2=\"150.0\"/><line class=\"ln hid\" x1=\"90.0\" y1=\"30.0\" x2=\"90.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M90.0,142.0 L98.0,142.0 L98.0,150.0\"/><text class=\"al\" x=\"174.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 cm</text><text class=\"al\" x=\"100.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text></svg>", "expr": "dec"}, {"t": "e) __B1__ m²", "a": {"B1": "36"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"96.7,150.0 203.3,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 m</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">9 m</text></svg>", "expr": "dec"}, {"t": "f) __B1__ m²", "a": {"B1": "28"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"97.5,150.0 202.5,150.0 202.5,30.0\"/><line class=\"ln hid\" x1=\"202.5\" y1=\"30.0\" x2=\"202.5\" y2=\"150.0\"/><path class=\"ra\" d=\"M202.5,142.0 L194.5,142.0 L194.5,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7 m</text><text class=\"al\" x=\"192.5\" y=\"90.0\" text-anchor=\"end\" dominant-baseline=\"middle\">8 m</text></svg>", "expr": "dec"}, {"t": "g) __B1__ m²", "a": {"B1": "54"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"70.0,150.0 230.0,150.0 230.0,30.0\"/><line class=\"ln hid\" x1=\"230.0\" y1=\"30.0\" x2=\"230.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M230.0,142.0 L222.0,142.0 L222.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">12 m</text><text class=\"al\" x=\"220.0\" y=\"90.0\" text-anchor=\"end\" dominant-baseline=\"middle\">9 m</text></svg>", "expr": "dec"}, {"t": "h) __B1__ cm²", "a": {"B1": "5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"54.0,150.0 246.0,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4 cm</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">2.5 cm</text></svg>", "expr": "dec"}, {"t": "i) __B1__ mm²", "a": {"B1": "25"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"30.0,150.0 270.0,150.0 102.0,30.0\"/><line class=\"ln hid\" x1=\"102.0\" y1=\"30.0\" x2=\"102.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M102.0,142.0 L94.0,142.0 L94.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 mm</text><text class=\"al\" x=\"112.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 mm</text></svg>", "expr": "dec"}], "sol": "Area of a triangle = ½ × base × height (the height is perpendicular to the base).\na) ½ × 12 × 5 = 30\nb) ½ × 8 × 6 = 24\nc) ½ × 7 × 6 = 21\nd) ½ × 3 × 5 = 7.5\ne) ½ × 8 × 9 = 36\nf) ½ × 7 × 8 = 28\ng) ½ × 12 × 9 = 54\nh) ½ × 4 × 2.5 = 5\ni) ½ × 10 × 5 = 25"}, {"kind": "blank", "p": "Five identical triangular shade sails each have base 3 m and height 2 m. Shadecloth costs ₹280 per m².", "tag": "", "marks": "", "flat": [{"t": "a) Total area: __B1__ m²", "a": {"B1": "15"}, "expr": "dec"}, {"t": "b) Total cost: ₹__B1__", "a": {"B1": "4200"}, "expr": "dec"}], "sol": "a) ½ × 3 × 2 = 3 m² each; 5 × 3 = 15 m²\nb) 15 × 280 = ₹4200", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"60.0,150.0 240.0,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 m</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">2 m</text></svg>"}, {"kind": "blank", "p": "An 8 m by 4 m tarpaulin is cut into three triangles: A (legs 5 m and 4 m), B (base 8 m, height 4 m) and C (legs 3 m and 4 m).", "tag": "", "marks": "", "flat": [{"t": "a) Area of the rectangle: __B1__ m²", "a": {"B1": "32"}, "expr": "dec"}, {"t": "b) Triangle A: __B1__ m²", "a": {"B1": "10"}, "expr": "dec"}, {"t": "c) Triangle B: __B1__ m²", "a": {"B1": "16"}, "expr": "dec"}, {"t": "d) Triangle C: __B1__ m²", "a": {"B1": "6"}, "expr": "dec"}], "sol": "a) 8 × 4 = 32\nb) ½ × 5 × 4 = 10\nc) ½ × 8 × 4 = 16\nd) ½ × 3 × 4 = 6\nCheck: 10 + 16 + 6 = 32 ✓"}, {"kind": "blank", "p": "Find the area of each parallelogram (area = base × height):", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ m²", "a": {"B1": "60"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"41.7,130.0 208.3,130.0 258.3,30.0 91.7,30.0\"/><line class=\"ln hid\" x1=\"91.7\" y1=\"30.0\" x2=\"91.7\" y2=\"130.0\"/><path class=\"ra\" d=\"M91.7,122.0 L99.7,122.0 L99.7,130.0\"/><text class=\"al\" x=\"125.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 m</text><text class=\"al\" x=\"99.7\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">6 m</text></svg>", "expr": "dec"}, {"t": "b) __B1__ cm²", "a": {"B1": "36"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"30.0,120.0 210.0,120.0 270.0,40.0 90.0,40.0\"/><line class=\"ln hid\" x1=\"90.0\" y1=\"40.0\" x2=\"90.0\" y2=\"120.0\"/><path class=\"ra\" d=\"M90.0,112.0 L98.0,112.0 L98.0,120.0\"/><text class=\"al\" x=\"120.0\" y=\"135.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">9 cm</text><text class=\"al\" x=\"98.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text></svg>", "expr": "dec"}, {"t": "c) __B1__ m²", "a": {"B1": "12"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"114.0,130.0 162.0,130.0 186.0,30.0 138.0,30.0\"/><line class=\"ln hid\" x1=\"138.0\" y1=\"30.0\" x2=\"138.0\" y2=\"130.0\"/><path class=\"ra\" d=\"M138.0,122.0 L146.0,122.0 L146.0,130.0\"/><text class=\"al\" x=\"138.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2.4 m</text><text class=\"al\" x=\"146.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 m</text></svg>", "expr": "dec"}], "sol": "Area of a parallelogram = base × height.\na) 10 × 6 = 60\nb) 9 × 4 = 36\nc) 2.4 × 5 = 12"}]}, {"id": "s4", "label": "Ex 10D", "sub": "Volume", "slides": [{"kind": "blank", "p": "Each cube has volume 1 cm³. Count the cubes to find the volume of each solid.", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm³", "a": {"B1": "9"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 128.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"139.6,34.0 160.4,46.0 139.6,58.0 118.8,46.0\"/><polygon class=\"sh2\" points=\"160.4,70.0 139.6,82.0 139.6,58.0 160.4,46.0\"/><polygon class=\"sh3\" points=\"118.8,70.0 139.6,82.0 139.6,58.0 118.8,46.0\"/><polygon class=\"sh\" points=\"118.8,46.0 139.6,58.0 118.8,70.0 98.0,58.0\"/><polygon class=\"sh2\" points=\"139.6,82.0 118.8,94.0 118.8,70.0 139.6,58.0\"/><polygon class=\"sh3\" points=\"98.0,82.0 118.8,94.0 118.8,70.0 98.0,58.0\"/><polygon class=\"sh\" points=\"160.4,46.0 181.2,58.0 160.4,70.0 139.6,58.0\"/><polygon class=\"sh2\" points=\"181.2,82.0 160.4,94.0 160.4,70.0 181.2,58.0\"/><polygon class=\"sh3\" points=\"139.6,82.0 160.4,94.0 160.4,70.0 139.6,58.0\"/><polygon class=\"sh\" points=\"139.6,10.0 160.4,22.0 139.6,34.0 118.8,22.0\"/><polygon class=\"sh2\" points=\"160.4,46.0 139.6,58.0 139.6,34.0 160.4,22.0\"/><polygon class=\"sh3\" points=\"118.8,46.0 139.6,58.0 139.6,34.0 118.8,22.0\"/><polygon class=\"sh\" points=\"139.6,58.0 160.4,70.0 139.6,82.0 118.8,70.0\"/><polygon class=\"sh2\" points=\"160.4,94.0 139.6,106.0 139.6,82.0 160.4,70.0\"/><polygon class=\"sh3\" points=\"118.8,94.0 139.6,106.0 139.6,82.0 118.8,70.0\"/><polygon class=\"sh\" points=\"181.2,58.0 202.0,70.0 181.2,82.0 160.4,70.0\"/><polygon class=\"sh2\" points=\"202.0,94.0 181.2,106.0 181.2,82.0 202.0,70.0\"/><polygon class=\"sh3\" points=\"160.4,94.0 181.2,106.0 181.2,82.0 160.4,70.0\"/><polygon class=\"sh\" points=\"160.4,22.0 181.2,34.0 160.4,46.0 139.6,34.0\"/><polygon class=\"sh2\" points=\"181.2,58.0 160.4,70.0 160.4,46.0 181.2,34.0\"/><polygon class=\"sh3\" points=\"139.6,58.0 160.4,70.0 160.4,46.0 139.6,34.0\"/><polygon class=\"sh\" points=\"118.8,22.0 139.6,34.0 118.8,46.0 98.0,34.0\"/><polygon class=\"sh2\" points=\"139.6,58.0 118.8,70.0 118.8,46.0 139.6,34.0\"/><polygon class=\"sh3\" points=\"98.0,58.0 118.8,70.0 118.8,46.0 98.0,34.0\"/><polygon class=\"sh\" points=\"160.4,70.0 181.2,82.0 160.4,94.0 139.6,82.0\"/><polygon class=\"sh2\" points=\"181.2,106.0 160.4,118.0 160.4,94.0 181.2,82.0\"/><polygon class=\"sh3\" points=\"139.6,106.0 160.4,118.0 160.4,94.0 139.6,82.0\"/></svg>", "expr": "dec"}, {"t": "b) __B1__ cm³", "a": {"B1": "13"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 140.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"150.0,34.0 170.8,46.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh2\" points=\"170.8,70.0 150.0,82.0 150.0,58.0 170.8,46.0\"/><polygon class=\"sh3\" points=\"129.2,70.0 150.0,82.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh\" points=\"129.2,46.0 150.0,58.0 129.2,70.0 108.4,58.0\"/><polygon class=\"sh2\" points=\"150.0,82.0 129.2,94.0 129.2,70.0 150.0,58.0\"/><polygon class=\"sh3\" points=\"108.4,82.0 129.2,94.0 129.2,70.0 108.4,58.0\"/><polygon class=\"sh\" points=\"170.8,46.0 191.6,58.0 170.8,70.0 150.0,58.0\"/><polygon class=\"sh2\" points=\"191.6,82.0 170.8,94.0 170.8,70.0 191.6,58.0\"/><polygon class=\"sh3\" points=\"150.0,82.0 170.8,94.0 170.8,70.0 150.0,58.0\"/><polygon class=\"sh\" points=\"108.4,58.0 129.2,70.0 108.4,82.0 87.6,70.0\"/><polygon class=\"sh2\" points=\"129.2,94.0 108.4,106.0 108.4,82.0 129.2,70.0\"/><polygon class=\"sh3\" points=\"87.6,94.0 108.4,106.0 108.4,82.0 87.6,70.0\"/><polygon class=\"sh\" points=\"150.0,58.0 170.8,70.0 150.0,82.0 129.2,70.0\"/><polygon class=\"sh2\" points=\"170.8,94.0 150.0,106.0 150.0,82.0 170.8,70.0\"/><polygon class=\"sh3\" points=\"129.2,94.0 150.0,106.0 150.0,82.0 129.2,70.0\"/><polygon class=\"sh\" points=\"191.6,58.0 212.4,70.0 191.6,82.0 170.8,70.0\"/><polygon class=\"sh2\" points=\"212.4,94.0 191.6,106.0 191.6,82.0 212.4,70.0\"/><polygon class=\"sh3\" points=\"170.8,94.0 191.6,106.0 191.6,82.0 170.8,70.0\"/><polygon class=\"sh\" points=\"129.2,22.0 150.0,34.0 129.2,46.0 108.4,34.0\"/><polygon class=\"sh2\" points=\"150.0,58.0 129.2,70.0 129.2,46.0 150.0,34.0\"/><polygon class=\"sh3\" points=\"108.4,58.0 129.2,70.0 129.2,46.0 108.4,34.0\"/><polygon class=\"sh\" points=\"170.8,22.0 191.6,34.0 170.8,46.0 150.0,34.0\"/><polygon class=\"sh2\" points=\"191.6,58.0 170.8,70.0 170.8,46.0 191.6,34.0\"/><polygon class=\"sh3\" points=\"150.0,58.0 170.8,70.0 170.8,46.0 150.0,34.0\"/><polygon class=\"sh\" points=\"129.2,70.0 150.0,82.0 129.2,94.0 108.4,82.0\"/><polygon class=\"sh2\" points=\"150.0,106.0 129.2,118.0 129.2,94.0 150.0,82.0\"/><polygon class=\"sh3\" points=\"108.4,106.0 129.2,118.0 129.2,94.0 108.4,82.0\"/><polygon class=\"sh\" points=\"170.8,70.0 191.6,82.0 170.8,94.0 150.0,82.0\"/><polygon class=\"sh2\" points=\"191.6,106.0 170.8,118.0 170.8,94.0 191.6,82.0\"/><polygon class=\"sh3\" points=\"150.0,106.0 170.8,118.0 170.8,94.0 150.0,82.0\"/><polygon class=\"sh\" points=\"150.0,34.0 170.8,46.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh2\" points=\"170.8,70.0 150.0,82.0 150.0,58.0 170.8,46.0\"/><polygon class=\"sh3\" points=\"129.2,70.0 150.0,82.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh\" points=\"150.0,82.0 170.8,94.0 150.0,106.0 129.2,94.0\"/><polygon class=\"sh2\" points=\"170.8,118.0 150.0,130.0 150.0,106.0 170.8,94.0\"/><polygon class=\"sh3\" points=\"129.2,118.0 150.0,130.0 150.0,106.0 129.2,94.0\"/><polygon class=\"sh\" points=\"150.0,10.0 170.8,22.0 150.0,34.0 129.2,22.0\"/><polygon class=\"sh2\" points=\"170.8,46.0 150.0,58.0 150.0,34.0 170.8,22.0\"/><polygon class=\"sh3\" points=\"129.2,46.0 150.0,58.0 150.0,34.0 129.2,22.0\"/></svg>", "expr": "dec"}, {"t": "c) __B1__ cm³", "a": {"B1": "11"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 152.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"139.6,58.0 160.4,70.0 139.6,82.0 118.8,70.0\"/><polygon class=\"sh2\" points=\"160.4,94.0 139.6,106.0 139.6,82.0 160.4,70.0\"/><polygon class=\"sh3\" points=\"118.8,94.0 139.6,106.0 139.6,82.0 118.8,70.0\"/><polygon class=\"sh\" points=\"118.8,70.0 139.6,82.0 118.8,94.0 98.0,82.0\"/><polygon class=\"sh2\" points=\"139.6,106.0 118.8,118.0 118.8,94.0 139.6,82.0\"/><polygon class=\"sh3\" points=\"98.0,106.0 118.8,118.0 118.8,94.0 98.0,82.0\"/><polygon class=\"sh\" points=\"160.4,70.0 181.2,82.0 160.4,94.0 139.6,82.0\"/><polygon class=\"sh2\" points=\"181.2,106.0 160.4,118.0 160.4,94.0 181.2,82.0\"/><polygon class=\"sh3\" points=\"139.6,106.0 160.4,118.0 160.4,94.0 139.6,82.0\"/><polygon class=\"sh\" points=\"139.6,34.0 160.4,46.0 139.6,58.0 118.8,46.0\"/><polygon class=\"sh2\" points=\"160.4,70.0 139.6,82.0 139.6,58.0 160.4,46.0\"/><polygon class=\"sh3\" points=\"118.8,70.0 139.6,82.0 139.6,58.0 118.8,46.0\"/><polygon class=\"sh\" points=\"139.6,82.0 160.4,94.0 139.6,106.0 118.8,94.0\"/><polygon class=\"sh2\" points=\"160.4,118.0 139.6,130.0 139.6,106.0 160.4,94.0\"/><polygon class=\"sh3\" points=\"118.8,118.0 139.6,130.0 139.6,106.0 118.8,94.0\"/><polygon class=\"sh\" points=\"181.2,82.0 202.0,94.0 181.2,106.0 160.4,94.0\"/><polygon class=\"sh2\" points=\"202.0,118.0 181.2,130.0 181.2,106.0 202.0,94.0\"/><polygon class=\"sh3\" points=\"160.4,118.0 181.2,130.0 181.2,106.0 160.4,94.0\"/><polygon class=\"sh\" points=\"118.8,46.0 139.6,58.0 118.8,70.0 98.0,58.0\"/><polygon class=\"sh2\" points=\"139.6,82.0 118.8,94.0 118.8,70.0 139.6,58.0\"/><polygon class=\"sh3\" points=\"98.0,82.0 118.8,94.0 118.8,70.0 98.0,58.0\"/><polygon class=\"sh\" points=\"160.4,46.0 181.2,58.0 160.4,70.0 139.6,58.0\"/><polygon class=\"sh2\" points=\"181.2,82.0 160.4,94.0 160.4,70.0 181.2,58.0\"/><polygon class=\"sh3\" points=\"139.6,82.0 160.4,94.0 160.4,70.0 139.6,58.0\"/><polygon class=\"sh\" points=\"139.6,10.0 160.4,22.0 139.6,34.0 118.8,22.0\"/><polygon class=\"sh2\" points=\"160.4,46.0 139.6,58.0 139.6,34.0 160.4,22.0\"/><polygon class=\"sh3\" points=\"118.8,46.0 139.6,58.0 139.6,34.0 118.8,22.0\"/><polygon class=\"sh\" points=\"160.4,94.0 181.2,106.0 160.4,118.0 139.6,106.0\"/><polygon class=\"sh2\" points=\"181.2,130.0 160.4,142.0 160.4,118.0 181.2,106.0\"/><polygon class=\"sh3\" points=\"139.6,130.0 160.4,142.0 160.4,118.0 139.6,106.0\"/><polygon class=\"sh\" points=\"139.6,58.0 160.4,70.0 139.6,82.0 118.8,70.0\"/><polygon class=\"sh2\" points=\"160.4,94.0 139.6,106.0 139.6,82.0 160.4,70.0\"/><polygon class=\"sh3\" points=\"118.8,94.0 139.6,106.0 139.6,82.0 118.8,70.0\"/></svg>", "expr": "dec"}], "sol": "Count layer by layer, including cubes hidden underneath.\na) bottom layer 6 + top 3 = 9\nb) bottom 9 + middle 3 + top 1 = 13\nc) 2 × 2 × 2 = 8, plus 2 on the side and 1 on top = 11"}, {"kind": "mcq", "text": "The volume of a telephone box is about:", "opts": ["2 cm³", "200 cm³", "2 m³", "20 m³"], "correct": 2, "tag": "", "sol": "A telephone box is about 1 m × 1 m × 2 m = 2 m³."}, {"kind": "mcq", "text": "The volume of a dice is about:", "opts": ["2 mm³", "2 cm³", "20 cm³", "2 m³"], "correct": 1, "tag": "", "sol": "A dice is roughly 1.3 cm on each side: about 2 cm³."}, {"kind": "blank", "p": "1 m³ containers are stacked 4 long, 3 wide and 2 high. Find the total volume.", "tag": "", "marks": "", "flat": [{"t": "__B1__ m³", "a": {"B1": "24"}, "expr": "dec"}], "sol": "4 × 3 × 2 = 24 m³", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 119.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"142.2,28.0 157.8,37.0 142.2,46.0 126.6,37.0\"/><polygon class=\"sh2\" points=\"157.8,55.0 142.2,64.0 142.2,46.0 157.8,37.0\"/><polygon class=\"sh3\" points=\"126.6,55.0 142.2,64.0 142.2,46.0 126.6,37.0\"/><polygon class=\"sh\" points=\"126.6,37.0 142.2,46.0 126.6,55.0 111.0,46.0\"/><polygon class=\"sh2\" points=\"142.2,64.0 126.6,73.0 126.6,55.0 142.2,46.0\"/><polygon class=\"sh3\" points=\"111.0,64.0 126.6,73.0 126.6,55.0 111.0,46.0\"/><polygon class=\"sh\" points=\"157.8,37.0 173.4,46.0 157.8,55.0 142.2,46.0\"/><polygon class=\"sh2\" points=\"173.4,64.0 157.8,73.0 157.8,55.0 173.4,46.0\"/><polygon class=\"sh3\" points=\"142.2,64.0 157.8,73.0 157.8,55.0 142.2,46.0\"/><polygon class=\"sh\" points=\"142.2,10.0 157.8,19.0 142.2,28.0 126.6,19.0\"/><polygon class=\"sh2\" points=\"157.8,37.0 142.2,46.0 142.2,28.0 157.8,19.0\"/><polygon class=\"sh3\" points=\"126.6,37.0 142.2,46.0 142.2,28.0 126.6,19.0\"/><polygon class=\"sh\" points=\"111.0,46.0 126.6,55.0 111.0,64.0 95.4,55.0\"/><polygon class=\"sh2\" points=\"126.6,73.0 111.0,82.0 111.0,64.0 126.6,55.0\"/><polygon class=\"sh3\" points=\"95.4,73.0 111.0,82.0 111.0,64.0 95.4,55.0\"/><polygon class=\"sh\" points=\"142.2,46.0 157.8,55.0 142.2,64.0 126.6,55.0\"/><polygon class=\"sh2\" points=\"157.8,73.0 142.2,82.0 142.2,64.0 157.8,55.0\"/><polygon class=\"sh3\" points=\"126.6,73.0 142.2,82.0 142.2,64.0 126.6,55.0\"/><polygon class=\"sh\" points=\"173.4,46.0 189.0,55.0 173.4,64.0 157.8,55.0\"/><polygon class=\"sh2\" points=\"189.0,73.0 173.4,82.0 173.4,64.0 189.0,55.0\"/><polygon class=\"sh3\" points=\"157.8,73.0 173.4,82.0 173.4,64.0 157.8,55.0\"/><polygon class=\"sh\" points=\"126.6,19.0 142.2,28.0 126.6,37.0 111.0,28.0\"/><polygon class=\"sh2\" points=\"142.2,46.0 126.6,55.0 126.6,37.0 142.2,28.0\"/><polygon class=\"sh3\" points=\"111.0,46.0 126.6,55.0 126.6,37.0 111.0,28.0\"/><polygon class=\"sh\" points=\"157.8,19.0 173.4,28.0 157.8,37.0 142.2,28.0\"/><polygon class=\"sh2\" points=\"173.4,46.0 157.8,55.0 157.8,37.0 173.4,28.0\"/><polygon class=\"sh3\" points=\"142.2,46.0 157.8,55.0 157.8,37.0 142.2,28.0\"/><polygon class=\"sh\" points=\"126.6,55.0 142.2,64.0 126.6,73.0 111.0,64.0\"/><polygon class=\"sh2\" points=\"142.2,82.0 126.6,91.0 126.6,73.0 142.2,64.0\"/><polygon class=\"sh3\" points=\"111.0,82.0 126.6,91.0 126.6,73.0 111.0,64.0\"/><polygon class=\"sh\" points=\"157.8,55.0 173.4,64.0 157.8,73.0 142.2,64.0\"/><polygon class=\"sh2\" points=\"173.4,82.0 157.8,91.0 157.8,73.0 173.4,64.0\"/><polygon class=\"sh3\" points=\"142.2,82.0 157.8,91.0 157.8,73.0 142.2,64.0\"/><polygon class=\"sh\" points=\"189.0,55.0 204.6,64.0 189.0,73.0 173.4,64.0\"/><polygon class=\"sh2\" points=\"204.6,82.0 189.0,91.0 189.0,73.0 204.6,64.0\"/><polygon class=\"sh3\" points=\"173.4,82.0 189.0,91.0 189.0,73.0 173.4,64.0\"/><polygon class=\"sh\" points=\"111.0,28.0 126.6,37.0 111.0,46.0 95.4,37.0\"/><polygon class=\"sh2\" points=\"126.6,55.0 111.0,64.0 111.0,46.0 126.6,37.0\"/><polygon class=\"sh3\" points=\"95.4,55.0 111.0,64.0 111.0,46.0 95.4,37.0\"/><polygon class=\"sh\" points=\"142.2,28.0 157.8,37.0 142.2,46.0 126.6,37.0\"/><polygon class=\"sh2\" points=\"157.8,55.0 142.2,64.0 142.2,46.0 157.8,37.0\"/><polygon class=\"sh3\" points=\"126.6,55.0 142.2,64.0 142.2,46.0 126.6,37.0\"/><polygon class=\"sh\" points=\"173.4,28.0 189.0,37.0 173.4,46.0 157.8,37.0\"/><polygon class=\"sh2\" points=\"189.0,55.0 173.4,64.0 173.4,46.0 189.0,37.0\"/><polygon class=\"sh3\" points=\"157.8,55.0 173.4,64.0 173.4,46.0 157.8,37.0\"/><polygon class=\"sh\" points=\"142.2,64.0 157.8,73.0 142.2,82.0 126.6,73.0\"/><polygon class=\"sh2\" points=\"157.8,91.0 142.2,100.0 142.2,82.0 157.8,73.0\"/><polygon class=\"sh3\" points=\"126.6,91.0 142.2,100.0 142.2,82.0 126.6,73.0\"/><polygon class=\"sh\" points=\"173.4,64.0 189.0,73.0 173.4,82.0 157.8,73.0\"/><polygon class=\"sh2\" points=\"189.0,91.0 173.4,100.0 173.4,82.0 189.0,73.0\"/><polygon class=\"sh3\" points=\"157.8,91.0 173.4,100.0 173.4,82.0 157.8,73.0\"/><polygon class=\"sh\" points=\"126.6,37.0 142.2,46.0 126.6,55.0 111.0,46.0\"/><polygon class=\"sh2\" points=\"142.2,64.0 126.6,73.0 126.6,55.0 142.2,46.0\"/><polygon class=\"sh3\" points=\"111.0,64.0 126.6,73.0 126.6,55.0 111.0,46.0\"/><polygon class=\"sh\" points=\"157.8,37.0 173.4,46.0 157.8,55.0 142.2,46.0\"/><polygon class=\"sh2\" points=\"173.4,64.0 157.8,73.0 157.8,55.0 173.4,46.0\"/><polygon class=\"sh3\" points=\"142.2,64.0 157.8,73.0 157.8,55.0 142.2,46.0\"/><polygon class=\"sh\" points=\"189.0,37.0 204.6,46.0 189.0,55.0 173.4,46.0\"/><polygon class=\"sh2\" points=\"204.6,64.0 189.0,73.0 189.0,55.0 204.6,46.0\"/><polygon class=\"sh3\" points=\"173.4,64.0 189.0,73.0 189.0,55.0 173.4,46.0\"/><polygon class=\"sh\" points=\"157.8,73.0 173.4,82.0 157.8,91.0 142.2,82.0\"/><polygon class=\"sh2\" points=\"173.4,100.0 157.8,109.0 157.8,91.0 173.4,82.0\"/><polygon class=\"sh3\" points=\"142.2,100.0 157.8,109.0 157.8,91.0 142.2,82.0\"/><polygon class=\"sh\" points=\"142.2,46.0 157.8,55.0 142.2,64.0 126.6,55.0\"/><polygon class=\"sh2\" points=\"157.8,73.0 142.2,82.0 142.2,64.0 157.8,55.0\"/><polygon class=\"sh3\" points=\"126.6,73.0 142.2,82.0 142.2,64.0 126.6,55.0\"/><polygon class=\"sh\" points=\"173.4,46.0 189.0,55.0 173.4,64.0 157.8,55.0\"/><polygon class=\"sh2\" points=\"189.0,73.0 173.4,82.0 173.4,64.0 189.0,55.0\"/><polygon class=\"sh3\" points=\"157.8,73.0 173.4,82.0 173.4,64.0 157.8,55.0\"/><polygon class=\"sh\" points=\"157.8,55.0 173.4,64.0 157.8,73.0 142.2,64.0\"/><polygon class=\"sh2\" points=\"173.4,82.0 157.8,91.0 157.8,73.0 173.4,64.0\"/><polygon class=\"sh3\" points=\"142.2,82.0 157.8,91.0 157.8,73.0 142.2,64.0\"/></svg>"}]}, {"id": "s5", "label": "Ex 10E", "sub": "The volume of a rectangular prism", "slides": [{"kind": "blank", "p": "Find the volume of each rectangular prism (volume = length × width × height):", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ mm³", "a": {"B1": "160"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,135.2 176.0,135.2 176.0,65.2 40.0,65.2\"/><polygon class=\"sh2\" points=\"40.0,65.2 176.0,65.2 218.0,40.0 82.0,40.0\"/><polygon class=\"sh3\" points=\"176.0,135.2 218.0,110.0 218.0,40.0 176.0,65.2\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"135.2\" x2=\"82.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"82.0\" y1=\"110.0\" x2=\"218.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"82.0\" y1=\"110.0\" x2=\"82.0\" y2=\"40.0\"/><text class=\"al\" x=\"108.0\" y=\"149.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 mm</text><text class=\"al\" x=\"211.0\" y=\"128.6\" text-anchor=\"start\" dominant-baseline=\"middle\">4 mm</text><text class=\"al\" x=\"226.0\" y=\"75.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 mm</text></svg>", "expr": "dec"}, {"t": "b) __B1__ m³", "a": {"B1": "48"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,137.0 128.0,137.0 128.0,58.0 40.0,58.0\"/><polygon class=\"sh2\" points=\"40.0,58.0 128.0,58.0 158.0,40.0 70.0,40.0\"/><polygon class=\"sh3\" points=\"128.0,137.0 158.0,119.0 158.0,40.0 128.0,58.0\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"137.0\" x2=\"70.0\" y2=\"119.0\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"119.0\" x2=\"158.0\" y2=\"119.0\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"119.0\" x2=\"70.0\" y2=\"40.0\"/><text class=\"al\" x=\"84.0\" y=\"151.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4 m</text><text class=\"al\" x=\"157.0\" y=\"134.0\" text-anchor=\"start\" dominant-baseline=\"middle\">2 m</text><text class=\"al\" x=\"166.0\" y=\"79.5\" text-anchor=\"start\" dominant-baseline=\"middle\">6 m</text></svg>", "expr": "dec"}, {"t": "c) __B1__ cm³", "a": {"B1": "56"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,119.0 164.0,119.0 164.0,58.0 40.0,58.0\"/><polygon class=\"sh2\" points=\"40.0,58.0 164.0,58.0 194.0,40.0 70.0,40.0\"/><polygon class=\"sh3\" points=\"164.0,119.0 194.0,101.0 194.0,40.0 164.0,58.0\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"119.0\" x2=\"70.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"101.0\" x2=\"194.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"70.0\" y1=\"101.0\" x2=\"70.0\" y2=\"40.0\"/><text class=\"al\" x=\"102.0\" y=\"133.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7 cm</text><text class=\"al\" x=\"193.0\" y=\"116.0\" text-anchor=\"start\" dominant-baseline=\"middle\">2 cm</text><text class=\"al\" x=\"202.0\" y=\"70.5\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text></svg>", "expr": "dec"}, {"t": "d) __B1__ mm³", "a": {"B1": "150"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,128.0 140.0,128.0 140.0,76.0 40.0,76.0\"/><polygon class=\"sh2\" points=\"40.0,76.0 140.0,76.0 200.0,40.0 100.0,40.0\"/><polygon class=\"sh3\" points=\"140.0,128.0 200.0,92.0 200.0,40.0 140.0,76.0\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"128.0\" x2=\"100.0\" y2=\"92.0\"/><line class=\"ln hid\" x1=\"100.0\" y1=\"92.0\" x2=\"200.0\" y2=\"92.0\"/><line class=\"ln hid\" x1=\"100.0\" y1=\"92.0\" x2=\"100.0\" y2=\"40.0\"/><text class=\"al\" x=\"90.0\" y=\"142.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5 mm</text><text class=\"al\" x=\"184.0\" y=\"116.0\" text-anchor=\"start\" dominant-baseline=\"middle\">10 mm</text><text class=\"al\" x=\"208.0\" y=\"66.0\" text-anchor=\"start\" dominant-baseline=\"middle\">3 mm</text></svg>", "expr": "dec"}, {"t": "e) __B1__ cm³", "a": {"B1": "125"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,138.8 140.0,138.8 140.0,68.8 40.0,68.8\"/><polygon class=\"sh2\" points=\"40.0,68.8 140.0,68.8 188.0,40.0 88.0,40.0\"/><polygon class=\"sh3\" points=\"140.0,138.8 188.0,110.0 188.0,40.0 140.0,68.8\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"138.8\" x2=\"88.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"110.0\" x2=\"188.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"110.0\" x2=\"88.0\" y2=\"40.0\"/><text class=\"al\" x=\"90.0\" y=\"152.8\" text-anchor=\"middle\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"178.0\" y=\"130.4\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"196.0\" y=\"75.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text></svg>", "expr": "dec"}, {"t": "f) __B1__ cm³", "a": {"B1": "150"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,138.8 152.0,138.8 152.0,68.8 40.0,68.8\"/><polygon class=\"sh2\" points=\"40.0,68.8 152.0,68.8 200.0,40.0 88.0,40.0\"/><polygon class=\"sh3\" points=\"152.0,138.8 200.0,110.0 200.0,40.0 152.0,68.8\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"138.8\" x2=\"88.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"110.0\" x2=\"200.0\" y2=\"110.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"110.0\" x2=\"88.0\" y2=\"40.0\"/><text class=\"al\" x=\"96.0\" y=\"152.8\" text-anchor=\"middle\" dominant-baseline=\"middle\">6 cm</text><text class=\"al\" x=\"190.0\" y=\"130.4\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"208.0\" y=\"75.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text></svg>", "expr": "dec"}], "sol": "Volume = length × width × height.\na) 8 × 4 × 5 = 160 mm³\nb) 4 × 2 × 6 = 48 m³\nc) 7 × 2 × 4 = 56 cm³\nd) 5 × 10 × 3 = 150 mm³\ne) 5 × 5 × 5 = 125 cm³\nf) 6 × 5 × 5 = 150 cm³"}, {"kind": "blank", "p": "An eraser is 5 cm by 3 cm by 2 cm. Find its volume.", "tag": "", "marks": "", "flat": [{"t": "__B1__ cm³", "a": {"B1": "30"}, "expr": "dec"}], "sol": "5 × 3 × 2 = 30 cm³"}, {"kind": "blank", "p": "A shoe box is 30 cm long, 16 cm wide and 10 cm high. Find the volume of air inside.", "tag": "", "marks": "", "flat": [{"t": "__B1__ cm³", "a": {"B1": "4800"}, "expr": "dec"}], "sol": "30 × 16 × 10 = 4800 cm³"}, {"kind": "blank", "p": "How many different rectangular prisms with whole-number sides have volume 36 cm³?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "8"}, "expr": "dec"}], "sol": "1×1×36, 1×2×18, 1×3×12, 1×4×9, 1×6×6, 2×2×9, 2×3×6, 3×3×4 → 8"}, {"kind": "blank", "p": "A prism is 8 cm by 5 cm by 2 cm. Find:", "tag": "", "marks": "", "flat": [{"t": "a) its volume: __B1__ cm³", "a": {"B1": "80"}, "expr": "dec"}, {"t": "b) the total area of its six faces: __B1__ cm²", "a": {"B1": "132"}, "expr": "dec"}], "sol": "a) 8 × 5 × 2 = 80\nb) 2 × (8×5 + 8×2 + 5×2) = 2 × 66 = 132", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,111.8 176.0,111.8 176.0,68.8 40.0,68.8\"/><polygon class=\"sh2\" points=\"40.0,68.8 176.0,68.8 224.0,40.0 88.0,40.0\"/><polygon class=\"sh3\" points=\"176.0,111.8 224.0,83.0 224.0,40.0 176.0,68.8\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"111.8\" x2=\"88.0\" y2=\"83.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"83.0\" x2=\"224.0\" y2=\"83.0\"/><line class=\"ln hid\" x1=\"88.0\" y1=\"83.0\" x2=\"88.0\" y2=\"40.0\"/><text class=\"al\" x=\"108.0\" y=\"125.8\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 cm</text><text class=\"al\" x=\"214.0\" y=\"103.4\" text-anchor=\"start\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"232.0\" y=\"61.5\" text-anchor=\"start\" dominant-baseline=\"middle\">2 cm</text></svg>"}, {"kind": "blank", "p": "A tank measures 2 m by 3 m by 80 cm high. Find its volume.", "tag": "", "marks": "", "flat": [{"t": "__B1__ m³", "a": {"B1": "4.8"}, "expr": "dec"}], "sol": "80 cm = 0.8 m; 2 × 3 × 0.8 = 4.8 m³"}, {"kind": "blank", "p": "How many 3 cm × 3 cm × 6 cm boxes fit into a 12 cm × 9 cm × 6 cm container?", "tag": "", "marks": "", "flat": [{"t": "__B1__ boxes", "a": {"B1": "12"}, "expr": "dec"}], "sol": "12 ÷ 3 = 4, 9 ÷ 3 = 3, 6 ÷ 6 = 1 → 4 × 3 × 1 = 12"}, {"kind": "blank", "p": "A prism has length 4 cm, width 5 cm and volume 120 cm³. Find its height.", "tag": "", "marks": "", "flat": [{"t": "__B1__ cm", "a": {"B1": "6"}, "expr": "dec"}], "sol": "4 × 5 × h = 120, so 20h = 120 and h = 6"}]}, {"id": "s6", "label": "Ex 10F", "sub": "Capacity", "slides": [{"kind": "blank", "p": "Which unit would you use for the capacity of (mL, L, kL or ML)?", "tag": "", "marks": "", "flat": [{"t": "a) a perfume bottle → __B1__", "a": {"B1": "mL"}}, {"t": "b) a flask → __B1__", "a": {"B1": "L"}}, {"t": "c) an Olympic swimming pool → __B1__", "a": {"B1": "ML"}}, {"t": "d) a drinking glass → __B1__", "a": {"B1": "mL"}}, {"t": "e) a water tank → __B1__", "a": {"B1": "kL"}}, {"t": "f) a reservoir → __B1__", "a": {"B1": "ML"}}, {"t": "g) a baby's bottle → __B1__", "a": {"B1": "mL"}}, {"t": "h) a bucket → __B1__", "a": {"B1": "L"}}], "sol": "mL: small containers · L: bottles and buckets · kL: tanks · ML: pools, dams and lakes"}, {"kind": "blank", "p": "Convert (1 L = 1000 mL, 1 kL = 1000 L, 1 ML = 1000 kL):", "tag": "", "marks": "", "flat": [{"t": "a) 7 L = __B1__ mL", "a": {"B1": "7000"}, "expr": "dec"}, {"t": "b) 5.6 kL = __B1__ L", "a": {"B1": "5600"}, "expr": "dec"}, {"t": "c) 8.51 ML = __B1__ kL", "a": {"B1": "8510"}, "expr": "dec"}, {"t": "d) 3540 mL = __B1__ L", "a": {"B1": "3.54"}, "expr": "dec"}, {"t": "e) 760 000 L = __B1__ kL", "a": {"B1": "760"}, "expr": "dec"}, {"t": "f) 124 kL = __B1__ ML", "a": {"B1": "0.124"}, "expr": "dec"}], "sol": "To a smaller unit, × 1000. To a larger unit, ÷ 1000."}, {"kind": "blank", "p": "A can holds 375 mL. How many litres are in a carton of 24 cans?", "tag": "", "marks": "", "flat": [{"t": "__B1__ L", "a": {"B1": "9"}, "expr": "dec"}], "sol": "24 × 375 = 9000 mL = 9 L"}, {"kind": "blank", "p": "A household used 6.3 kL of water in April (30 days). On average, how many litres per day?", "tag": "", "marks": "", "flat": [{"t": "__B1__ L", "a": {"B1": "210"}, "expr": "dec"}], "sol": "6.3 kL = 6300 L; 6300 ÷ 30 = 210 L"}]}, {"id": "s7", "label": "Review 10A", "sub": "Review set 10A", "slides": [{"kind": "mcq", "text": "The area of a bank card is about:", "opts": ["4 cm²", "40 mm²", "4 m²", "40 cm²"], "correct": 3, "tag": "", "sol": "A bank card is about 8.5 cm × 5.4 cm ≈ 46 cm², so about 40 cm²."}, {"kind": "blank", "p": "A rectangular garden is 6 m long and 4.5 m wide. Find its area.", "tag": "", "marks": "", "flat": [{"t": "__B1__ m²", "a": {"B1": "27"}, "expr": "dec"}], "sol": "6 × 4.5 = 27 m²"}, {"kind": "blank", "p": "Find the area of each shape:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm²", "a": {"B1": "18"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"50.0,30.0 250.0,30.0 250.0,130.0 50.0,130.0\"/><line class=\"tick\" x1=\"150.0\" y1=\"24.0\" x2=\"150.0\" y2=\"36.0\"/><line class=\"tick\" x1=\"256.0\" y1=\"77.5\" x2=\"244.0\" y2=\"77.5\"/><line class=\"tick\" x1=\"256.0\" y1=\"82.5\" x2=\"244.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"150.0\" y1=\"136.0\" x2=\"150.0\" y2=\"124.0\"/><line class=\"tick\" x1=\"44.0\" y1=\"82.5\" x2=\"56.0\" y2=\"82.5\"/><line class=\"tick\" x1=\"44.0\" y1=\"77.5\" x2=\"56.0\" y2=\"77.5\"/><path class=\"ra\" d=\"M50.0,39.0 L59.0,39.0 L59.0,30.0\"/><path class=\"ra\" d=\"M241.0,30.0 L241.0,39.0 L250.0,39.0\"/><path class=\"ra\" d=\"M250.0,121.0 L241.0,121.0 L241.0,130.0\"/><path class=\"ra\" d=\"M59.0,130.0 L59.0,121.0 L50.0,121.0\"/><text class=\"al\" x=\"275.0\" y=\"80.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 cm</text><text class=\"al\" x=\"150.0\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6 cm</text></svg>", "expr": "dec"}, {"t": "b) __B1__ cm²", "a": {"B1": "10"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"75.0,150.0 225.0,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text></svg>", "expr": "dec"}, {"t": "c) __B1__ m²", "a": {"B1": "60"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"80.0,150.0 180.0,150.0 220.0,30.0\"/><line class=\"ln hid\" x1=\"180.0\" y1=\"150.0\" x2=\"220.0\" y2=\"150.0\"/><line class=\"ln hid\" x1=\"220.0\" y1=\"30.0\" x2=\"220.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M220.0,142.0 L212.0,142.0 L212.0,150.0\"/><text class=\"al\" x=\"130.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 m</text><text class=\"al\" x=\"210.0\" y=\"90.0\" text-anchor=\"end\" dominant-baseline=\"middle\">12 m</text></svg>", "expr": "dec"}], "sol": "a) 6 × 3 = 18\nb) ½ × 5 × 4 = 10\nc) ½ × 10 × 12 = 60 (the height is measured outside the triangle)"}, {"kind": "blank", "p": "A stamp is 3 cm by 2 cm.", "tag": "", "marks": "", "flat": [{"t": "a) Area: __B1__ cm²", "a": {"B1": "6"}, "expr": "dec"}, {"t": "b) How many fit on a 20 cm by 30 cm sheet? __B1__", "a": {"B1": "100"}, "expr": "dec"}], "sol": "a) 6 cm²\nb) 20 ÷ 2 = 10 and 30 ÷ 3 = 10 → 100"}, {"kind": "blank", "p": "Each cube has volume 1 cm³. Find the volume of each solid:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm³", "a": {"B1": "4"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 104.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"118.8,10.0 139.6,22.0 118.8,34.0 98.0,22.0\"/><polygon class=\"sh2\" points=\"139.6,46.0 118.8,58.0 118.8,34.0 139.6,22.0\"/><polygon class=\"sh3\" points=\"98.0,46.0 118.8,58.0 118.8,34.0 98.0,22.0\"/><polygon class=\"sh\" points=\"139.6,22.0 160.4,34.0 139.6,46.0 118.8,34.0\"/><polygon class=\"sh2\" points=\"160.4,58.0 139.6,70.0 139.6,46.0 160.4,34.0\"/><polygon class=\"sh3\" points=\"118.8,58.0 139.6,70.0 139.6,46.0 118.8,34.0\"/><polygon class=\"sh\" points=\"160.4,34.0 181.2,46.0 160.4,58.0 139.6,46.0\"/><polygon class=\"sh2\" points=\"181.2,70.0 160.4,82.0 160.4,58.0 181.2,46.0\"/><polygon class=\"sh3\" points=\"139.6,70.0 160.4,82.0 160.4,58.0 139.6,46.0\"/><polygon class=\"sh\" points=\"181.2,46.0 202.0,58.0 181.2,70.0 160.4,58.0\"/><polygon class=\"sh2\" points=\"202.0,82.0 181.2,94.0 181.2,70.0 202.0,58.0\"/><polygon class=\"sh3\" points=\"160.4,82.0 181.2,94.0 181.2,70.0 160.4,58.0\"/></svg>", "expr": "dec"}, {"t": "b) __B1__ cm³", "a": {"B1": "7"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 140.0\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"150.0,58.0 170.8,70.0 150.0,82.0 129.2,70.0\"/><polygon class=\"sh2\" points=\"170.8,94.0 150.0,106.0 150.0,82.0 170.8,70.0\"/><polygon class=\"sh3\" points=\"129.2,94.0 150.0,106.0 150.0,82.0 129.2,70.0\"/><polygon class=\"sh\" points=\"129.2,70.0 150.0,82.0 129.2,94.0 108.4,82.0\"/><polygon class=\"sh2\" points=\"150.0,106.0 129.2,118.0 129.2,94.0 150.0,82.0\"/><polygon class=\"sh3\" points=\"108.4,106.0 129.2,118.0 129.2,94.0 108.4,82.0\"/><polygon class=\"sh\" points=\"170.8,70.0 191.6,82.0 170.8,94.0 150.0,82.0\"/><polygon class=\"sh2\" points=\"191.6,106.0 170.8,118.0 170.8,94.0 191.6,82.0\"/><polygon class=\"sh3\" points=\"150.0,106.0 170.8,118.0 170.8,94.0 150.0,82.0\"/><polygon class=\"sh\" points=\"150.0,34.0 170.8,46.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh2\" points=\"170.8,70.0 150.0,82.0 150.0,58.0 170.8,46.0\"/><polygon class=\"sh3\" points=\"129.2,70.0 150.0,82.0 150.0,58.0 129.2,46.0\"/><polygon class=\"sh\" points=\"150.0,82.0 170.8,94.0 150.0,106.0 129.2,94.0\"/><polygon class=\"sh2\" points=\"170.8,118.0 150.0,130.0 150.0,106.0 170.8,94.0\"/><polygon class=\"sh3\" points=\"129.2,118.0 150.0,130.0 150.0,106.0 129.2,94.0\"/><polygon class=\"sh\" points=\"170.8,46.0 191.6,58.0 170.8,70.0 150.0,58.0\"/><polygon class=\"sh2\" points=\"191.6,82.0 170.8,94.0 170.8,70.0 191.6,58.0\"/><polygon class=\"sh3\" points=\"150.0,82.0 170.8,94.0 170.8,70.0 150.0,58.0\"/><polygon class=\"sh\" points=\"150.0,10.0 170.8,22.0 150.0,34.0 129.2,22.0\"/><polygon class=\"sh2\" points=\"170.8,46.0 150.0,58.0 150.0,34.0 170.8,22.0\"/><polygon class=\"sh3\" points=\"129.2,46.0 150.0,58.0 150.0,34.0 129.2,22.0\"/></svg>", "expr": "dec"}], "sol": "a) 4\nb) 4 + 2 + 1 = 7"}, {"kind": "blank", "p": "A line has 30 triangular flags, each with base 15 cm and height 20 cm. Find the total area of material.", "tag": "", "marks": "", "flat": [{"t": "__B1__ cm²", "a": {"B1": "4500"}, "expr": "dec"}], "sol": "½ × 15 × 20 = 150 cm² each; 30 × 150 = 4500 cm²"}, {"kind": "blank", "p": "Find the volume of each prism:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm³", "a": {"B1": "320"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,137.0 200.0,137.0 200.0,76.0 40.0,76.0\"/><polygon class=\"sh2\" points=\"40.0,76.0 200.0,76.0 260.0,40.0 100.0,40.0\"/><polygon class=\"sh3\" points=\"200.0,137.0 260.0,101.0 260.0,40.0 200.0,76.0\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"137.0\" x2=\"100.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"100.0\" y1=\"101.0\" x2=\"260.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"100.0\" y1=\"101.0\" x2=\"100.0\" y2=\"40.0\"/><text class=\"al\" x=\"120.0\" y=\"151.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 cm</text><text class=\"al\" x=\"244.0\" y=\"125.0\" text-anchor=\"start\" dominant-baseline=\"middle\">8 cm</text><text class=\"al\" x=\"268.0\" y=\"70.5\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text></svg>", "expr": "dec"}, {"t": "b) __B1__ cm³", "a": {"B1": "64"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,126.2 128.0,126.2 128.0,65.2 40.0,65.2\"/><polygon class=\"sh2\" points=\"40.0,65.2 128.0,65.2 170.0,40.0 82.0,40.0\"/><polygon class=\"sh3\" points=\"128.0,126.2 170.0,101.0 170.0,40.0 128.0,65.2\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"126.2\" x2=\"82.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"82.0\" y1=\"101.0\" x2=\"170.0\" y2=\"101.0\"/><line class=\"ln hid\" x1=\"82.0\" y1=\"101.0\" x2=\"82.0\" y2=\"40.0\"/><text class=\"al\" x=\"84.0\" y=\"140.2\" text-anchor=\"middle\" dominant-baseline=\"middle\">4 cm</text><text class=\"al\" x=\"163.0\" y=\"119.6\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text><text class=\"al\" x=\"178.0\" y=\"70.5\" text-anchor=\"start\" dominant-baseline=\"middle\">4 cm</text></svg>", "expr": "dec"}, {"t": "c) __B1__ m³", "a": {"B1": "2.7"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"40.0,88.4 116.0,88.4 116.0,54.4 40.0,54.4\"/><polygon class=\"sh2\" points=\"40.0,54.4 116.0,54.4 140.0,40.0 64.0,40.0\"/><polygon class=\"sh3\" points=\"116.0,88.4 140.0,74.0 140.0,40.0 116.0,54.4\"/><line class=\"ln hid\" x1=\"40.0\" y1=\"88.4\" x2=\"64.0\" y2=\"74.0\"/><line class=\"ln hid\" x1=\"64.0\" y1=\"74.0\" x2=\"140.0\" y2=\"74.0\"/><line class=\"ln hid\" x1=\"64.0\" y1=\"74.0\" x2=\"64.0\" y2=\"40.0\"/><text class=\"al\" x=\"78.0\" y=\"102.4\" text-anchor=\"middle\" dominant-baseline=\"middle\">3 m</text><text class=\"al\" x=\"142.0\" y=\"87.2\" text-anchor=\"start\" dominant-baseline=\"middle\">90 cm</text><text class=\"al\" x=\"148.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">1 m</text></svg>", "expr": "dec"}], "sol": "a) 10 × 8 × 4 = 320\nb) 4 × 4 × 4 = 64\nc) 3 × 0.9 × 1 = 2.7"}, {"kind": "blank", "p": "How many 10 cm × 6 cm × 10 cm boxes fit in a 60 cm × 60 cm × 60 cm container?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "360"}, "expr": "dec"}], "sol": "6 × 10 × 6 = 360"}, {"kind": "blank", "p": "Wendy bought three 1.25 L bottles and two 600 mL bottles. How many litres in total?", "tag": "", "marks": "", "flat": [{"t": "__B1__ L", "a": {"B1": "4.95"}, "expr": "dec"}], "sol": "3.75 L + 1.2 L = 4.95 L"}, {"kind": "blank", "p": "A large 11 cm by 7 cm rectangle is split into a red 6 cm × 7 cm, a green 5 cm × 4 cm and a yellow 5 cm × 3 cm rectangle.", "tag": "", "marks": "", "flat": [{"t": "a) large: __B1__ cm²", "a": {"B1": "77"}, "expr": "dec"}, {"t": "b) red: __B1__ cm²", "a": {"B1": "42"}, "expr": "dec"}, {"t": "c) green: __B1__ cm²", "a": {"B1": "20"}, "expr": "dec"}, {"t": "d) yellow: __B1__ cm²", "a": {"B1": "15"}, "expr": "dec"}], "sol": "a) 77\nb) 42\nc) 20\nd) 15\nCheck: 42 + 20 + 15 = 77 ✓"}]}, {"id": "s8", "label": "Review 10B", "sub": "Review set 10B", "slides": [{"kind": "blank", "p": "A table top is 3 m by 1.4 m. Cloth costs ₹900 per m². Find the cost of covering it.", "tag": "", "marks": "", "flat": [{"t": "area: __B1__ m²", "a": {"B1": "4.2"}, "expr": "dec"}, {"t": "cost: ₹__B1__", "a": {"B1": "3780"}, "expr": "dec"}], "sol": "3 × 1.4 = 4.2 m²\n4.2 × 900 = ₹3780"}, {"kind": "blank", "p": "Rectangle A is 6 m × 3 m, B is 10 m × 2 m and C is 4 m × 4 m.", "tag": "", "marks": "", "flat": [{"t": "Which has the largest area? __B1__", "a": {"B1": "B"}}], "sol": "A 18, B 20, C 16 → B"}, {"kind": "blank", "p": "Find the area of each triangle:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__ cm²", "a": {"B1": "7.5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"50.0,150.0 250.0,150.0 50.0,30.0\"/><line class=\"ln hid\" x1=\"50.0\" y1=\"30.0\" x2=\"50.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M50.0,142.0 L58.0,142.0 L58.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5 cm</text><text class=\"al\" x=\"60.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">3 cm</text></svg>", "expr": "dec"}, {"t": "b) __B1__ m²", "a": {"B1": "20"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 180\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"54.0,150.0 246.0,150.0 150.0,30.0\"/><line class=\"ln hid\" x1=\"150.0\" y1=\"30.0\" x2=\"150.0\" y2=\"150.0\"/><path class=\"ra\" d=\"M150.0,142.0 L142.0,142.0 L142.0,150.0\"/><text class=\"al\" x=\"150.0\" y=\"165.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8 m</text><text class=\"al\" x=\"160.0\" y=\"90.0\" text-anchor=\"start\" dominant-baseline=\"middle\">5 m</text></svg>", "expr": "dec"}], "sol": "a) ½ × 5 × 3 = 7.5\nb) ½ × 8 × 5 = 20"}, {"kind": "blank", "p": "A garden shed is 5 m long, 4 m wide and 4.5 m high. Find the volume of air inside.", "tag": "", "marks": "", "flat": [{"t": "__B1__ m³", "a": {"B1": "90"}, "expr": "dec"}], "sol": "5 × 4 × 4.5 = 90 m³"}, {"kind": "blank", "p": "Convert:", "tag": "", "marks": "", "flat": [{"t": "a) 12.4 L = __B1__ mL", "a": {"B1": "12400"}, "expr": "dec"}, {"t": "b) 765 kL = __B1__ ML", "a": {"B1": "0.765"}, "expr": "dec"}], "sol": "a) × 1000\nb) ÷ 1000"}, {"kind": "blank", "p": "A mower tank holds 2.5 L. Rob fills it, then uses 850 mL. How much is left?", "tag": "", "marks": "", "flat": [{"t": "__B1__ L", "a": {"B1": "1.65"}, "expr": "dec"}], "sol": "2.5 − 0.85 = 1.65 L"}, {"kind": "blank", "p": "A parallelogram has base 10 cm and height 6 cm. A diagonal splits it into two triangles.", "tag": "", "marks": "", "flat": [{"t": "a) area of each triangle: __B1__ cm²", "a": {"B1": "30"}, "expr": "dec"}, {"t": "b) area of the parallelogram: __B1__ cm²", "a": {"B1": "60"}, "expr": "dec"}], "sol": "a) ½ × 10 × 6 = 30\nb) 2 × 30 = 60 = 10 × 6 ✓", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 160\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><polygon class=\"sh\" points=\"33.3,130.0 200.0,130.0 266.7,30.0 100.0,30.0\"/><line class=\"ln hid\" x1=\"100.0\" y1=\"30.0\" x2=\"100.0\" y2=\"130.0\"/><path class=\"ra\" d=\"M100.0,122.0 L108.0,122.0 L108.0,130.0\"/><text class=\"al\" x=\"116.7\" y=\"145.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10 cm</text><text class=\"al\" x=\"108.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">6 cm</text></svg>"}, {"kind": "blank", "p": "Boxes of raisins measure 5 cm × 6 cm × 15 cm. They are packed into a 30 cm × 12 cm × 20 cm box.", "tag": "", "marks": "", "flat": [{"t": "a) volume of a raisin box: __B1__ cm³", "a": {"B1": "450"}, "expr": "dec"}, {"t": "b) volume of the large box: __B1__ cm³", "a": {"B1": "7200"}, "expr": "dec"}, {"t": "c) maximum number of raisin boxes: __B1__", "a": {"B1": "16"}, "expr": "dec"}], "sol": "a) 450\nb) 7200\nc) 15 cm along 30 (2), 6 cm along 12 (2), 5 cm along 20 (4): 2 × 2 × 4 = 16, which fills the box exactly"}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-g6-ch10';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Area, Volume and Capacity</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('');
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { h += fr(esc(slide.p)); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — revisit it anytime from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+(item.status!=='unanswered'?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick);
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };

renderLogin();
})();
</script>
</body>
</html>
