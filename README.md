# er-triage-framework
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ER Triage Framework · Sneha Manjunath</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --navy:#0D1B2A;
  --navy-mid:#1A2D42;
  --navy-light:#243650;
  --teal:#00B4A0;
  --teal-light:#00D4BC;
  --teal-pale:#E0F7F5;
  --amber:#C97B00;
  --amber-pale:#FDF3DC;
  --red:#C0392B;
  --red-pale:#FDECEA;
  --blue:#1A6FB5;
  --blue-pale:#E3F0FC;
  --green:#0E7A5F;
  --green-pale:#E2F5EE;
  --purple:#5B4FCF;
  --purple-pale:#EEEAFC;
  --border:#E2E8F0;
  --text-main:#0D1B2A;
  --text-mid:#4A5568;
  --text-soft:#718096;
  --bg:#F8FAFC;
  --white:#FFFFFF;
  --font:'DM Sans',sans-serif;
  --mono:'DM Mono',monospace;
}
body{font-family:var(--font);background:#EEF2F7;min-height:100vh;display:flex;align-items:flex-start;justify-content:center;padding:24px 16px}
.wrap{width:100%;max-width:780px;background:var(--white);border-radius:20px;overflow:hidden;box-shadow:0 4px 32px rgba(13,27,42,.12)}

/* HEADER */
.hdr{background:var(--navy);padding:28px 32px 22px}
.hdr-eye{font-size:10px;letter-spacing:.12em;color:var(--teal-light);text-transform:uppercase;font-weight:500;margin-bottom:6px}
.hdr-title{font-size:22px;font-weight:600;color:#fff;margin-bottom:4px}
.hdr-sub{font-size:12px;color:rgba(255,255,255,.5);line-height:1.5}
.hdr-tags{display:flex;gap:6px;flex-wrap:wrap;margin-top:14px}
.htag{font-size:10px;padding:3px 10px;border-radius:20px;border:1px solid rgba(0,180,160,.35);color:rgba(0,212,188,.8);font-weight:500}

/* TABS */
.tab-bar{display:flex;background:var(--navy-mid);border-bottom:1px solid rgba(255,255,255,.08)}
.tab{padding:11px 20px;font-size:12px;font-weight:500;color:rgba(255,255,255,.4);cursor:pointer;border-bottom:2px solid transparent;transition:all .2s}
.tab.active{color:var(--teal-light);border-bottom-color:var(--teal-light)}
.tab:hover:not(.active){color:rgba(255,255,255,.65)}

/* PROGRESS */
.prog-bar{height:3px;background:rgba(0,180,160,.15)}
.prog-fill{height:100%;background:linear-gradient(90deg,var(--teal),var(--teal-light));transition:width .4s ease}

/* BODY */
.body{padding:28px 32px;background:var(--bg);min-height:440px}

/* BREADCRUMB */
.bc{display:flex;align-items:center;flex-wrap:wrap;gap:4px;margin-bottom:18px}
.bc-i{font-size:11px;color:var(--text-soft);white-space:nowrap}
.bc-s{font-size:11px;color:var(--border)}
.bc-a{font-size:11px;color:var(--navy);font-weight:600}

/* STEP HEADER */
.step-hdr{font-size:10px;color:var(--text-soft);letter-spacing:.08em;text-transform:uppercase;margin-bottom:6px;font-weight:500}
.step-q{font-size:17px;font-weight:600;color:var(--text-main);line-height:1.4;margin-bottom:18px}

/* CASE REF BADGE */
.ref-badge{display:inline-flex;align-items:center;gap:6px;font-size:11px;padding:4px 12px;border-radius:20px;background:var(--teal-pale);border:1px solid rgba(0,180,160,.25);color:var(--green);margin-bottom:14px;font-family:var(--mono)}
.ref-dot{width:6px;height:6px;border-radius:50%;background:var(--teal);flex-shrink:0}

/* INTAKE FORM */
.field-group{display:flex;flex-direction:column;gap:10px;margin-bottom:18px}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.flabel{font-size:11px;color:var(--text-mid);margin-bottom:4px;font-weight:500}
.flabel span{color:var(--red)}
.finput,.fselect{width:100%;padding:9px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:13px;color:var(--text-main);background:var(--white);outline:none;transition:border-color .15s;font-family:var(--font)}
.finput:focus,.fselect:focus{border-color:var(--teal)}
.fselect{padding-right:30px;cursor:pointer;appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6' fill='none'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%23718096' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 11px center}
.anon-row{display:flex;align-items:center;gap:8px;padding:10px 12px;border:1.5px solid var(--border);border-radius:8px;cursor:pointer;background:var(--white)}
.anon-row input{width:14px;height:14px;cursor:pointer;accent-color:var(--teal)}
.anon-txt{font-size:12px;color:var(--text-main)}
.anon-sub{font-size:10px;color:var(--text-soft);margin-left:auto}

/* CASE CATEGORIES */
.cat-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-bottom:18px}
.cat-card{background:var(--white);border:1.5px solid var(--border);border-radius:12px;padding:14px;cursor:pointer;transition:all .18s;text-align:left}
.cat-card:hover{transform:translateY(-2px);box-shadow:0 4px 16px rgba(13,27,42,.1)}
.cat-card.conduct:hover{border-color:var(--red)}
.cat-card.grievance:hover{border-color:var(--amber)}
.cat-card.perf:hover{border-color:var(--green)}
.cat-card.absence:hover{border-color:var(--blue)}
.cat-card.accommodation:hover{border-color:var(--purple)}
.cat-icon{width:34px;height:34px;border-radius:8px;display:flex;align-items:center;justify-content:center;margin-bottom:8px}
.cat-icon svg{width:18px;height:18px}
.cat-card.conduct .cat-icon{background:var(--red-pale)}
.cat-card.grievance .cat-icon{background:var(--amber-pale)}
.cat-card.perf .cat-icon{background:var(--green-pale)}
.cat-card.absence .cat-icon{background:var(--blue-pale)}
.cat-card.accommodation .cat-icon{background:var(--purple-pale)}
.cat-name{font-size:12px;font-weight:600;color:var(--text-main);margin-bottom:3px}
.cat-desc{font-size:10px;color:var(--text-soft);line-height:1.4}

/* OPTIONS */
.opt-list{display:flex;flex-direction:column;gap:8px;margin-bottom:18px}
.opt-btn{background:var(--white);border:1.5px solid var(--border);border-radius:10px;padding:12px 14px;cursor:pointer;text-align:left;transition:all .15s;display:flex;align-items:flex-start;gap:10px}
.opt-btn:hover{border-color:var(--teal);background:#F0FDFB}
.opt-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0;margin-top:5px}
.opt-text{font-size:13px;color:var(--text-main);line-height:1.5}
.opt-sub{font-size:10px;color:var(--text-soft);margin-top:2px}

/* SECTION HEADER for sub-types */
.opt-section-label{font-size:10px;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--text-soft);margin:12px 0 6px;padding:0 2px}

/* BUTTONS */
.nav-row{display:flex;align-items:center;justify-content:space-between;margin-top:8px}
.back-btn{background:none;border:none;font-size:12px;color:var(--text-soft);cursor:pointer;padding:0;font-family:var(--font)}
.back-btn:hover{color:var(--text-main)}
.rst-btn{background:none;border:1.5px solid var(--border);border-radius:8px;font-size:11px;color:var(--text-mid);cursor:pointer;padding:6px 12px;font-family:var(--font);transition:all .15s}
.rst-btn:hover{background:var(--white);border-color:var(--text-soft)}
.pri-btn{background:var(--navy);color:#fff;border:none;border-radius:9px;padding:10px 20px;font-size:13px;font-weight:500;cursor:pointer;font-family:var(--font);transition:opacity .15s}
.pri-btn:hover{opacity:.85}

/* OUTCOME CARDS */
.out-wrap{border-radius:14px;overflow:hidden;margin-bottom:14px;border:1px solid transparent}
.out-hdr{padding:18px 18px 14px}
.out-tag{display:inline-flex;align-items:center;gap:5px;font-size:10px;font-weight:600;padding:3px 10px;border-radius:20px;margin-bottom:8px;letter-spacing:.04em;text-transform:uppercase}
.out-title{font-size:16px;font-weight:600;line-height:1.3;margin-bottom:6px}
.out-body{font-size:12px;line-height:1.7}
.out-actions{padding:12px 18px}
.out-alabel{font-size:10px;letter-spacing:.07em;text-transform:uppercase;opacity:.6;margin-bottom:8px;font-weight:600}
.chips{display:flex;flex-wrap:wrap;gap:5px}
.chip{font-size:10px;padding:4px 10px;border-radius:20px;font-weight:500}

/* OUTCOME COLOUR THEMES */
.out-wrap.formal{background:#FDECEA;border-color:rgba(192,57,43,.2)}
.out-wrap.formal .out-hdr{background:#FDECEA;color:var(--red)}
.out-wrap.formal .out-tag{background:rgba(192,57,43,.12);color:var(--red)}
.out-wrap.formal .out-title{color:#8B1A1A}
.out-wrap.formal .out-body{color:#7A2020}
.out-wrap.formal .out-actions{background:rgba(192,57,43,.06)}
.out-wrap.formal .chip{background:rgba(192,57,43,.1);color:var(--red);border:1px solid rgba(192,57,43,.2)}

.out-wrap.escalate{background:var(--amber-pale);border-color:rgba(201,123,0,.2)}
.out-wrap.escalate .out-hdr{background:var(--amber-pale);color:var(--amber)}
.out-wrap.escalate .out-tag{background:rgba(201,123,0,.12);color:var(--amber)}
.out-wrap.escalate .out-title{color:#7A4A00}
.out-wrap.escalate .out-body{color:#6B4000}
.out-wrap.escalate .out-actions{background:rgba(201,123,0,.06)}
.out-wrap.escalate .chip{background:rgba(201,123,0,.1);color:var(--amber);border:1px solid rgba(201,123,0,.2)}

.out-wrap.informal{background:var(--green-pale);border-color:rgba(14,122,95,.2)}
.out-wrap.informal .out-hdr{background:var(--green-pale);color:var(--green)}
.out-wrap.informal .out-tag{background:rgba(14,122,95,.12);color:var(--green)}
.out-wrap.informal .out-title{color:#064A38}
.out-wrap.informal .out-body{color:#0A5A44}
.out-wrap.informal .out-actions{background:rgba(14,122,95,.06)}
.out-wrap.informal .chip{background:rgba(14,122,95,.1);color:var(--green);border:1px solid rgba(14,122,95,.2)}

.out-wrap.tribunal{background:#1A1A2E;border-color:rgba(91,79,207,.5)}
.out-wrap.tribunal .out-hdr{background:#1A1A2E;color:#C9C4FF}
.out-wrap.tribunal .out-tag{background:rgba(91,79,207,.25);color:#A89CFF}
.out-wrap.tribunal .out-title{color:#E0DCFF}
.out-wrap.tribunal .out-body{color:#B0AADD}
.out-wrap.tribunal .out-actions{background:rgba(0,0,0,.3)}
.out-wrap.tribunal .chip{background:rgba(91,79,207,.2);color:#B9B3FF;border:1px solid rgba(91,79,207,.3)}

/* LOG CARD */
.sub-card{background:var(--white);border:1.5px solid var(--border);border-radius:12px;padding:18px;margin-top:10px}
.sub-title{font-size:13px;font-weight:600;color:var(--text-main);margin-bottom:4px}
.sub-sub{font-size:11px;color:var(--text-soft);line-height:1.5;margin-bottom:14px}
.sum-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:8px;margin-bottom:14px}
.si{}.si-l{font-size:10px;color:var(--text-soft);margin-bottom:2px}.si-v{font-size:12px;color:var(--text-main);font-weight:600}
.sub-acts{display:flex;gap:8px;flex-wrap:wrap}
.disc{font-size:10px;color:var(--text-soft);line-height:1.6;padding:10px 12px;background:var(--white);border-radius:8px;margin-top:10px;border:1.5px solid var(--border)}

/* SUCCESS */
.suc-screen{text-align:center;padding:40px 20px}
.suc-icon{width:52px;height:52px;border-radius:50%;background:var(--green-pale);display:flex;align-items:center;justify-content:center;margin:0 auto 14px}
.suc-icon svg{width:24px;height:24px}
.suc-title{font-size:18px;font-weight:600;color:var(--text-main);margin-bottom:4px}
.suc-sub{font-size:12px;color:var(--text-soft);line-height:1.5;margin-bottom:14px}
.suc-ref{display:inline-block;font-size:13px;font-weight:500;padding:8px 16px;border-radius:8px;background:var(--bg);border:1.5px solid var(--border);color:var(--text-main);margin-bottom:18px;font-family:var(--mono)}
.route-row{display:flex;align-items:center;gap:6px;justify-content:center;margin-bottom:18px;flex-wrap:wrap}
.rpill{font-size:10px;padding:4px 12px;border-radius:20px;border:1px solid var(--border);color:var(--text-soft);background:var(--bg)}
.rpill.active{background:var(--green-pale);border-color:rgba(14,122,95,.35);color:var(--green);font-weight:600}
.rarr{font-size:11px;color:var(--text-soft)}

/* DOT COLOURS */
.dot-conduct{background:var(--red)}
.dot-grievance{background:var(--amber)}
.dot-perf{background:var(--green)}
.dot-absence{background:var(--blue)}
.dot-accommodation{background:var(--purple)}
.dot-neutral{background:var(--border)}

/* ERR */
.err{font-size:11px;color:var(--red);margin-top:6px;font-weight:500}

/* FLOW MAP TAB */
.flowmap{padding:0;overflow-x:auto;background:var(--bg)}
.flowmap svg{display:block;margin:0 auto}
.legend{display:flex;gap:14px;flex-wrap:wrap;padding:14px 24px;border-top:1.5px solid var(--border);background:var(--white)}
.leg-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--text-mid)}
.leg-dot{width:10px;height:10px;border-radius:3px;flex-shrink:0}

/* SVG node styles */
.c-teal rect,.c-teal ellipse{fill:var(--teal-pale);stroke:var(--teal);stroke-width:1.5}
.c-amber rect,.c-amber polygon{fill:var(--amber-pale);stroke:var(--amber);stroke-width:1.5}
.c-red rect{fill:var(--red-pale);stroke:var(--red);stroke-width:1.5}
.c-green rect,.c-green polygon{fill:var(--green-pale);stroke:var(--green);stroke-width:1.5}
.c-purple rect{fill:var(--purple-pale);stroke:var(--purple);stroke-width:1.5}
.c-navy rect{fill:var(--navy);stroke:var(--navy-light);stroke-width:1.5}
.th{font-family:'DM Sans',sans-serif;font-size:11px;font-weight:600;fill:var(--text-main)}
.ts{font-family:'DM Sans',sans-serif;font-size:9.5px;fill:var(--text-soft)}
.tred{fill:var(--red)}
.tgreen{fill:var(--green)}
.tamber{fill:var(--amber)}
.tpurple{fill:var(--purple)}
.twhite{fill:#fff}

@media(max-width:520px){
  .hdr{padding:20px}
  .body{padding:18px}
  .cat-grid{grid-template-columns:1fr}
  .field-row{grid-template-columns:1fr}
  .sum-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>
<div class="wrap">
  <div class="hdr">
    <div class="hdr-eye">HR Practice Tool · Sneha Manjunath</div>
    <div class="hdr-title">ER Triage Framework</div>
    <div class="hdr-sub">Log a case, triage the issue, and route to the appropriate ER process — from informal support to Employment Tribunal referral.</div>
    <div class="hdr-tags">
      <span class="htag">UK Employment Law</span>
      <span class="htag">ACAS Code of Practice</span>
      <span class="htag">Equality Act 2010</span>
      <span class="htag">Employment Rights Act 1996</span>
      <span class="htag">COI Checks</span>
    </div>
  </div>

  <div class="tab-bar">
    <div class="tab active" id="tab-triage" onclick="switchTab('triage')">Interactive triage</div>
    <div class="tab" id="tab-flow" onclick="switchTab('flow')">Full case lifecycle</div>
  </div>
  <div class="prog-bar"><div class="prog-fill" id="prog" style="width:0%"></div></div>

  <!-- TRIAGE PANEL -->
  <div id="panel-triage">
    <div class="body">
      <div class="bc" id="bc"></div>
      <div id="content"></div>
    </div>
  </div>

  <!-- FLOW PANEL -->
  <div id="panel-flow" style="display:none">
    <div class="flowmap">
      <svg width="100%" viewBox="0 0 720 1780" role="img" aria-label="ER case lifecycle flowchart including Employment Tribunal path">
        <defs>
          <marker id="arr" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
            <path d="M2 1L8 5L2 9" fill="none" stroke="#888" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </marker>
          <marker id="arr-red" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
            <path d="M2 1L8 5L2 9" fill="none" stroke="#C0392B" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </marker>
          <marker id="arr-purple" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto-start-reverse">
            <path d="M2 1L8 5L2 9" fill="none" stroke="#5B4FCF" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </marker>
        </defs>
        <rect x="0" y="0" width="720" height="1780" fill="#F8FAFC"/>

        <!-- START -->
        <g class="node c-teal">
          <ellipse cx="360" cy="52" rx="90" ry="26" stroke-width="1.5"/>
          <text class="th tgreen" x="360" y="52" text-anchor="middle" dominant-baseline="central">Incident reported</text>
        </g>
        <line x1="360" y1="78" x2="360" y2="108" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>

        <!-- COI -->
        <g class="node c-amber">
          <polygon points="360,108 450,152 360,196 270,152"/>
          <text class="th tamber" x="360" y="152" text-anchor="middle" dominant-baseline="central">COI present?</text>
        </g>
        <line x1="270" y1="152" x2="160" y2="152" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="213" y="143" text-anchor="middle">Yes</text>
        <g class="node c-amber">
          <rect x="60" y="130" width="100" height="44" rx="6"/>
          <text class="th tamber" x="110" y="152" text-anchor="middle" dominant-baseline="central">Reassign handler</text>
        </g>
        <path d="M110 174 L110 238 L270 238" fill="none" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="130" y="218">Reassigned</text>
        <line x1="360" y1="196" x2="360" y2="220" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="212">No</text>

        <!-- ASSESS SEVERITY -->
        <g class="node c-amber">
          <polygon points="360,220 456,268 360,316 264,268"/>
          <text class="th tamber" x="360" y="261" text-anchor="middle" dominant-baseline="central">Assess severity</text>
          <text class="ts tamber" x="360" y="277" text-anchor="middle" dominant-baseline="central">&amp; nature</text>
        </g>

        <!-- INFORMAL branch (left) -->
        <line x1="264" y1="268" x2="155" y2="268" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="208" y="258" text-anchor="middle">Informal</text>
        <g class="node c-green">
          <rect x="60" y="246" width="95" height="44" rx="6"/>
          <text class="th tgreen" x="107" y="268" text-anchor="middle" dominant-baseline="central">Manager coaching</text>
        </g>
        <line x1="107" y1="290" x2="107" y2="342" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="120" y="318">Coach</text>
        <g class="node c-green">
          <rect x="60" y="342" width="95" height="44" rx="6"/>
          <text class="th tgreen" x="107" y="364" text-anchor="middle" dominant-baseline="central">Mediation session</text>
        </g>
        <line x1="107" y1="386" x2="107" y2="434" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="120" y="412">Mediate</text>
        <g class="node c-green">
          <polygon points="107,434 185,468 107,502 29,468"/>
          <text class="th tgreen" x="107" y="461" text-anchor="middle" dominant-baseline="central">Agreement</text>
          <text class="ts tgreen" x="107" y="477" text-anchor="middle" dominant-baseline="central">reached?</text>
        </g>
        <!-- Yes = resolved informally -->
        <line x1="29" y1="468" x2="18" y2="468" stroke="#888" stroke-width="1.2"/>
        <line x1="18" y1="468" x2="18" y2="590" stroke="#888" stroke-width="1.2"/>
        <line x1="18" y1="590" x2="264" y2="590" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="13" y="520" text-anchor="middle" transform="rotate(-90,13,520)">Yes — resolved</text>
        <!-- No = formal -->
        <line x1="107" y1="502" x2="107" y2="545" stroke="#888" stroke-width="1.2"/>
        <line x1="107" y1="545" x2="285" y2="545" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="120" y="528">No</text>

        <!-- SERIOUS branch (right) -->
        <line x1="456" y1="268" x2="560" y2="268" stroke="#C0392B" stroke-width="1.2" marker-end="url(#arr-red)"/>
        <text class="ts tred" x="507" y="256" text-anchor="middle">Serious</text>
        <g class="node c-red">
          <rect x="560" y="246" width="115" height="44" rx="6"/>
          <text class="th tred" x="617" y="268" text-anchor="middle" dominant-baseline="central">Suspend employee</text>
        </g>
        <line x1="617" y1="290" x2="617" y2="390" stroke="#C0392B" stroke-width="1.2" marker-end="url(#arr-red)"/>
        <text class="ts tred" x="630" y="340">Immediate</text>
        <g class="node c-red">
          <rect x="560" y="390" width="115" height="44" rx="6"/>
          <text class="th tred" x="617" y="412" text-anchor="middle" dominant-baseline="central">Urgent investigation</text>
        </g>
        <line x1="617" y1="434" x2="617" y2="710" stroke="#C0392B" stroke-width="1.2"/>
        <line x1="617" y1="710" x2="458" y2="710" stroke="#C0392B" stroke-width="1.2" marker-end="url(#arr-red)"/>
        <text class="ts tred" x="632" y="575" text-anchor="middle" transform="rotate(-90,632,575)">Escalate to hearing</text>

        <!-- FORMAL branch (centre) -->
        <line x1="360" y1="316" x2="360" y2="535" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="428">Formal</text>

        <!-- FORMAL INVESTIGATION -->
        <g class="node c-amber">
          <rect x="280" y="535" width="160" height="44" rx="6"/>
          <text class="th tamber" x="360" y="557" text-anchor="middle" dominant-baseline="central">Formal investigation</text>
        </g>
        <line x1="360" y1="579" x2="360" y2="622" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="604">Investigate</text>

        <!-- EVIDENCE GATHERING -->
        <g class="node c-amber">
          <rect x="280" y="622" width="160" height="44" rx="6"/>
          <text class="th tamber" x="360" y="644" text-anchor="middle" dominant-baseline="central">Evidence gathering</text>
        </g>
        <line x1="360" y1="666" x2="360" y2="692" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="682">Evidence</text>

        <!-- DISCIPLINARY HEARING -->
        <g class="node c-amber">
          <rect x="280" y="692" width="160" height="44" rx="6"/>
          <text class="th tamber" x="360" y="714" text-anchor="middle" dominant-baseline="central">Disciplinary hearing</text>
        </g>
        <line x1="360" y1="736" x2="360" y2="776" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="759">Hearing</text>

        <!-- DETERMINE OUTCOME -->
        <g class="node c-amber">
          <polygon points="360,776 450,820 360,864 270,820"/>
          <text class="th tamber" x="360" y="813" text-anchor="middle" dominant-baseline="central">Determine outcome</text>
        </g>

        <!-- Appeal loop -->
        <path d="M450 820 L500 820 L500 714 L440 714" fill="none" stroke="#888" stroke-width="1.2" stroke-dasharray="5 3" marker-end="url(#arr)"/>
        <text class="ts" x="515" y="768" text-anchor="middle" transform="rotate(-90,515,768)">Appeal</text>

        <!-- OUTCOME LETTER -->
        <line x1="360" y1="864" x2="360" y2="910" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="890">Outcome</text>
        <g class="node c-amber">
          <rect x="280" y="910" width="160" height="44" rx="6"/>
          <text class="th tamber" x="360" y="932" text-anchor="middle" dominant-baseline="central">Issue outcome letter</text>
        </g>

        <!-- Informal resolved joins here -->
        <line x1="264" y1="590" x2="264" y2="960" stroke="#888" stroke-width="1.2"/>
        <line x1="264" y1="960" x2="280" y2="960" stroke="#888" stroke-width="1.2"/>

        <line x1="360" y1="954" x2="360" y2="1000" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="979">Issue</text>

        <!-- HRIS SYNC -->
        <g class="node c-purple">
          <rect x="255" y="1000" width="210" height="44" rx="6"/>
          <text class="th tpurple" x="360" y="1022" text-anchor="middle" dominant-baseline="central">HRIS sync &amp; documentation</text>
        </g>
        <line x1="360" y1="1044" x2="360" y2="1088" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="1068">Close / appeal?</text>

        <!-- APPEAL OUTCOME DECISION -->
        <g class="node c-amber">
          <polygon points="360,1088 446,1128 360,1168 274,1128"/>
          <text class="th tamber" x="360" y="1128" text-anchor="middle" dominant-baseline="central">Appeal upheld?</text>
        </g>

        <!-- Yes — close -->
        <line x1="274" y1="1128" x2="185" y2="1128" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="228" y="1118" text-anchor="middle">Yes</text>
        <g class="node c-green">
          <rect x="90" y="1106" width="95" height="44" rx="6"/>
          <text class="th tgreen" x="137" y="1128" text-anchor="middle" dominant-baseline="central">Decision revised</text>
        </g>
        <line x1="137" y1="1150" x2="137" y2="1190" stroke="#888" stroke-width="1.2"/>
        <line x1="137" y1="1190" x2="264" y2="1190" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="200" y="1182" text-anchor="middle">Resolved</text>

        <!-- No — ET referral path -->
        <line x1="446" y1="1128" x2="540" y2="1128" stroke="#5B4FCF" stroke-width="1.2" marker-end="url(#arr-purple)"/>
        <text class="ts tpurple" x="492" y="1116" text-anchor="middle">No</text>
        <g class="node c-purple">
          <rect x="540" y="1106" width="130" height="44" rx="6"/>
          <text class="th tpurple" x="605" y="1128" text-anchor="middle" dominant-baseline="central">ACAS Early</text>
        </g>
        <!-- ET text second line workaround -->
        <text class="th tpurple" x="605" y="1145" text-anchor="middle" font-size="11" font-weight="600">Conciliation</text>
        <line x1="605" y1="1150" x2="605" y2="1196" stroke="#5B4FCF" stroke-width="1.2" marker-end="url(#arr-purple)"/>
        <g class="node c-purple">
          <rect x="540" y="1196" width="130" height="44" rx="6"/>
          <text class="th tpurple" x="605" y="1218" text-anchor="middle" dominant-baseline="central">ET referral</text>
        </g>
        <line x1="605" y1="1240" x2="605" y2="1280" stroke="#5B4FCF" stroke-width="1.2"/>
        <line x1="605" y1="1280" x2="444" y2="1280" stroke="#5B4FCF" stroke-width="1.2" marker-end="url(#arr-purple)"/>
        <text class="ts tpurple" x="622" y="1262" transform="rotate(-90,622,1262)" text-anchor="middle">Legal team</text>

        <!-- CASE CLOSED -->
        <g class="node c-teal">
          <rect x="280" y="1190" width="160" height="44" rx="22"/>
          <text class="th tgreen" x="360" y="1212" text-anchor="middle" dominant-baseline="central">Case closed</text>
        </g>
        <line x1="360" y1="1234" x2="360" y2="1280" stroke="#888" stroke-width="1.2" marker-end="url(#arr)"/>
        <text class="ts" x="374" y="1259">Closed</text>

        <!-- ACAS NOTE -->
        <text class="ts" x="360" y="1320" text-anchor="middle" fill="#A0AEC0" font-style="italic">ACAS Early Conciliation is mandatory before any ET claim can be submitted</text>
        <text class="ts" x="360" y="1336" text-anchor="middle" fill="#A0AEC0" font-style="italic">(Employment Tribunals Act 1996 s.18A)</text>

        <!-- LEGEND LABELS -->
        <text class="ts" x="360" y="1370" text-anchor="middle" fill="#CBD5E0">— — — Appeal path (dashed)  ·  Purple = ET track</text>
      </svg>
    </div>
    <div class="legend">
      <div class="leg-item"><div class="leg-dot" style="background:#00B4A0"></div>Start / end / informal resolved</div>
      <div class="leg-item"><div class="leg-dot" style="background:#C97B00"></div>Decision / formal step</div>
      <div class="leg-item"><div class="leg-dot" style="background:#C0392B"></div>Serious / urgent action</div>
      <div class="leg-item"><div class="leg-dot" style="background:#5B4FCF"></div>ET pathway / ACAS conciliation</div>
      <div class="leg-item"><div class="leg-dot" style="background:#5B4FCF"></div>System / documentation</div>
    </div>
  </div>
</div>

<script>
const STEPS={
  start:{q:"What type of issue has been raised?",label:"Issue type",progress:30,type:"categories"},

  /* ── CONDUCT ─────────────────────────────────── */
  conduct_stage:{q:"Has a formal process already been initiated?",label:"Stage",progress:48,dot:"conduct",
    options:[
      {t:"First report — no formal action yet",next:"conduct_trigger"},
      {t:"Formal process already open",next:"conduct_active"},
      {t:"Gross misconduct or zero-tolerance breach",next:"out_formal_conduct_gross"}
    ]},
  conduct_trigger:{q:"Does any of the following apply?",label:"Escalation check",progress:65,dot:"conduct",
    options:[
      {t:"Second or repeated occurrence",next:"out_formal_conduct"},
      {t:"Manager attempted informal conversation — unresolved",next:"out_formal_conduct"},
      {t:"Employee has requested a formal process",next:"out_formal_conduct"},
      {t:"Involves bullying, harassment, or discrimination",next:"out_formal_conduct_gross"},
      {t:"None of the above — first minor issue",next:"out_informal_conduct"}
    ]},
  conduct_active:{q:"Where is the case currently?",label:"Case stage",progress:65,dot:"conduct",
    options:[
      {t:"Investigation in progress",next:"out_invest"},
      {t:"Hearing or outcome pending",next:"out_hearing"},
      {t:"Appeal lodged — internal",next:"out_appeal"},
      {t:"Appeal exhausted — considering ET claim",next:"out_tribunal"}
    ]},

  /* ── GRIEVANCE ───────────────────────────────── */
  grievance_stage:{q:"How has the issue been raised?",label:"Stage",progress:48,dot:"grievance",
    options:[
      {t:"Informal — verbally raised with manager or HR",next:"grievance_trigger"},
      {t:"Formal written grievance submitted",next:"out_formal_grievance"},
      {t:"Involves bullying, harassment, or discrimination",next:"out_formal_grievance_serious"},
      {t:"Grievance outcome disputed — considering appeal or ET",next:"out_tribunal"}
    ]},
  grievance_trigger:{q:"Has the manager attempted to resolve this directly?",label:"Resolution attempt",progress:65,dot:"grievance",
    options:[
      {t:"No — first conversation still needed",next:"out_informal_grievance"},
      {t:"Yes — attempt made but unresolved",next:"out_escalate_grievance"},
      {t:"Employee refuses to engage informally",next:"out_formal_grievance"}
    ]},

  /* ── PERFORMANCE ─────────────────────────────── */
  perf_stage:{q:"Has a Performance Improvement Plan (PIP) been opened?",label:"Stage",progress:48,dot:"perf",
    options:[
      {t:"No — concerns not yet formally documented",next:"perf_trigger"},
      {t:"Yes — active PIP in place",next:"out_formal_perf"},
      {t:"PIP completed — now considering capability dismissal",next:"out_formal_perf_serious"}
    ]},
  perf_trigger:{q:"Has the manager had documented conversations with the employee?",label:"Documentation check",progress:65,dot:"perf",
    options:[
      {t:"No documented discussions yet",next:"out_informal_perf"},
      {t:"Yes — no improvement after two or more conversations",next:"out_escalate_perf"},
      {t:"Specific policy threshold crossed",next:"out_formal_perf"}
    ]},

  /* ── ABSENCE ─────────────────────────────────── */
  absence_stage:{q:"What is the nature of the absence concern?",label:"Absence type",progress:48,dot:"absence",
    options:[
      {t:"Short-term absence (under 7 days) — single occurrence",sub:"First episode, no prior trigger",next:"out_informal_absence_st"},
      {t:"Short-term absence — trigger point reached",sub:"Bradford Factor or policy threshold crossed",next:"out_formal_absence_trigger"},
      {t:"Pattern of absence (e.g. Mondays, pre/post-holiday)",sub:"Suspected avoidance pattern",next:"absence_pattern"},
      {t:"Long-term sickness (2+ weeks) — ongoing",sub:"Continuous absence, fit note in place or required",next:"absence_lt_type"},
      {t:"Long-term sickness — approaching capability threshold",sub:"12+ weeks, no clear return date",next:"out_formal_absence_lt_capability"}
    ]},
  absence_pattern:{q:"Has the employee been spoken to about the pattern?",label:"Prior discussion",progress:65,dot:"absence",
    options:[
      {t:"No — welfare conversation still needed",next:"out_informal_absence_st"},
      {t:"Yes — pattern continues despite conversation",next:"out_formal_absence_trigger"}
    ]},
  absence_lt_type:{q:"What is the current status of the long-term absence?",label:"LTS status",progress:65,dot:"absence",
    options:[
      {t:"First welfare check needed — no contact yet",next:"out_lt_welfare"},
      {t:"Welfare meetings ongoing — monitoring",next:"out_lt_monitoring"},
      {t:"Occupational health referral required",next:"out_lt_oh"},
      {t:"Reasonable adjustments discussion needed",next:"out_lt_adjustments"}
    ]},

  /* ── ACCOMMODATION ───────────────────────────── */
  accommodation_stage:{q:"What type of accommodation or work environment concern is this?",label:"Concern type",progress:48,dot:"accommodation",
    options:[
      {t:"Flexible working request (statutory or informal)",next:"out_flexible_work"},
      {t:"Disability or health-related adjustment",next:"out_disability_adjust"},
      {t:"Religious accommodation",next:"out_informal_accommodation"},
      {t:"Maternity, paternity, or parental leave query",next:"out_parental_leave"},
      {t:"Work environment or safety concern",next:"out_work_environment"},
      {t:"Discrimination, harassment, or unfair treatment allegation",next:"out_formal_grievance_serious"}
    ]},

  /* ─────── OUTCOMES ─────── */
  out_informal_conduct:{type:"outcome",tone:"informal",progress:100,title:"Informal management action",
    body:"Support the manager to hold a clear, documented conversation with the employee. Agree expectations in writing and set a review date. Retain a brief note on file.",
    actions:["Manager-led documented conversation","Written expectations agreed","Review date set","HR coaching to manager","Note on file retained"]},

  out_formal_conduct:{type:"outcome",tone:"formal",progress:100,title:"Formal disciplinary process",
    body:"Initiate formal disciplinary proceedings per the ACAS Code of Practice. Appoint an investigating manager independent of the complaint. Issue written notice of the investigation and timeframe. Consider interim measures if required.",
    actions:["Appoint independent investigating manager","Issue written investigation notice","Assess interim measures","ACAS Code of Practice applies","Right to be accompanied at all stages"]},

  out_formal_conduct_gross:{type:"outcome",tone:"formal",progress:100,title:"Gross misconduct — immediate formal action",
    body:"Allegations of gross misconduct or zero-tolerance breaches (e.g. harassment, violence, fraud) require immediate formal investigation. Consider precautionary suspension (paid, non-punitive) and involve Senior HR and legal as appropriate. The Equality Act 2010 must be considered where protected characteristics are involved.",
    actions:["Precautionary suspension (paid)",  "Senior HR and legal involvement","Immediate investigation scope","Equality Act 2010 review","Witness protection measures"]},

  out_invest:{type:"outcome",tone:"formal",progress:100,title:"Investigation in progress",
    body:"Ensure the investigating manager has a clear scope, witness list, and realistic timeline (target: within 4 weeks). Maintain an evidence bundle and keep all parties updated on progress without prejudicing the investigation.",
    actions:["Scope, timeline, and witnesses confirmed","Structured interview notes","Evidence bundle maintained","Target: 4 weeks","Regular update to all parties"]},

  out_hearing:{type:"outcome",tone:"formal",progress:100,title:"Disciplinary or grievance hearing",
    body:"Confirm the employee has received the full investigation pack with at least 48 hours notice. Verify the hearing panel is independent, a note-taker is confirmed, and the employee's right to be accompanied is confirmed in writing.",
    actions:["48hr notice with full pack","Right to be accompanied confirmed","Independent note-taker","Outcome letter prepared","Clear appeal rights communicated"]},

  out_appeal:{type:"outcome",tone:"escalate",progress:100,title:"Internal appeal — escalate to senior panel",
    body:"Appeals must be heard by a manager more senior than the original decision-maker, who was not involved in the original hearing. Legal advice is strongly recommended where the original outcome was dismissal. Acknowledge receipt within 5 working days.",
    actions:["Senior panel — not involved in original hearing","Acknowledge within 5 working days","Legal review if original outcome was dismissal","Full re-consideration of evidence","Written outcome with ET rights noted"]},

  out_tribunal:{type:"outcome",tone:"tribunal",progress:100,title:"Employment Tribunal pathway — legal referral required",
    body:"ACAS Early Conciliation is a mandatory prerequisite before any Employment Tribunal claim can be submitted (Employment Tribunals Act 1996, s.18A). The HR function does not manage ET proceedings directly — this must be escalated to the organisation's legal team or external employment solicitors. HR's role at this stage is to ensure all documentation is complete, consistent, and legally defensible.",
    actions:["Immediate legal team referral","ACAS Early Conciliation mandatory first","Full case file prepared for legal review","No direct communication with claimant without legal sign-off","Document audit — consistency check across all records"]},

  out_informal_grievance:{type:"outcome",tone:"informal",progress:100,title:"Informal resolution — managed conversation",
    body:"Facilitate a structured conversation between the parties. Agree a resolution plan in writing. Consider mediation if direct resolution is not achievable within two weeks.",
    actions:["Structured managed conversation","Written resolution plan","Mediation if needed","Follow-up review in 2 weeks","Record kept on file"]},

  out_escalate_grievance:{type:"outcome",tone:"escalate",progress:100,title:"Escalate to formal grievance",
    body:"Informal resolution has been attempted without success. Advise the individual of their right to raise a formal written grievance and issue the formal process steps.",
    actions:["Written grievance invitation issued","Formal hearing within 2 weeks of receipt","Independent hearing panel","Right to be accompanied","Written outcome and full appeal rights"]},

  out_formal_grievance:{type:"outcome",tone:"formal",progress:100,title:"Formal grievance process",
    body:"Acknowledge the written grievance within 3 working days. Appoint an independent investigating manager who was not involved in the events complained of. Issue a written outcome with full appeal rights.",
    actions:["Acknowledge within 3 working days","Independent investigator appointed","Formal hearing arranged","Written outcome issued","Full appeal rights communicated"]},

  out_formal_grievance_serious:{type:"outcome",tone:"formal",progress:100,title:"Serious grievance — immediate formal action",
    body:"Allegations of bullying, harassment, or discrimination require immediate formal investigation. Consider interim separation of the parties and review Equality Act 2010 implications, including protected characteristics. Senior HR and legal involvement is recommended.",
    actions:["Immediate investigation initiated","Interim separation of parties considered","Senior HR and legal involvement","Equality Act 2010 review","Named contacts identified for claimant support"]},

  out_informal_perf:{type:"outcome",tone:"informal",progress:100,title:"Informal performance support",
    body:"Coach the manager to hold a clear, supportive conversation with the employee. Set SMART objectives and agree a review date. Retain a brief note of the discussion.",
    actions:["SMART objectives set","Manager-led support plan","Documented conversation note","Review meeting in 4 weeks","Signpost to L&D if relevant"]},

  out_escalate_perf:{type:"outcome",tone:"escalate",progress:100,title:"Escalate to formal Performance Improvement Plan",
    body:"Initiate a formal Performance Improvement Plan with clear measurable targets and a defined review period of 4 to 12 weeks. The PIP must be realistic, supported, and reviewed regularly.",
    actions:["Formal PIP document issued","Measurable, achievable targets","4–12 week review period","Support and training identified","Right of appeal noted"]},

  out_formal_perf:{type:"outcome",tone:"formal",progress:100,title:"Active PIP — structured formal review",
    body:"Ensure review meetings are documented and that agreed support is being provided. If targets are not met by the end of the PIP period, prepare for a capability hearing.",
    actions:["Regular documented review meetings","Support clearly evidenced","Prepare for capability hearing if required","Legal consult before any capability dismissal","Full appeal rights"]},

  out_formal_perf_serious:{type:"outcome",tone:"formal",progress:100,title:"Capability hearing — senior HR and legal required",
    body:"Before initiating a capability hearing, ensure all support options have been exhausted and thoroughly documented. Consult Senior HR and legal. The ACAS Code of Practice on discipline and grievance applies.",
    actions:["Full documentation reviewed","Senior HR and legal consultation","ACAS Code compliance confirmed","Capability hearing arranged","Full appeal rights communicated"]},

  /* ABSENCE OUTCOMES */
  out_informal_absence_st:{type:"outcome",tone:"informal",progress:100,title:"Return-to-work conversation — short-term absence",
    body:"Hold a brief return-to-work (RTW) conversation on the employee's first day back. This is informal, supportive, and non-punitive. Record a brief note. Monitor for recurring short-term absence patterns.",
    actions:["RTW conversation on first day back","Brief supportive note on record","Wellbeing check-in completed","Monitor for patterns","No formal action at this stage"]},

  out_formal_absence_trigger:{type:"outcome",tone:"formal",progress:100,title:"Formal attendance management — trigger point reached",
    body:"A Bradford Factor or policy trigger point has been reached. Issue a formal attendance management letter and arrange a review meeting. The employee has the right to be accompanied. An occupational health referral should be considered.",
    actions:["Formal attendance management letter issued","Review meeting arranged","Right to be accompanied confirmed","Occupational health referral considered","Monitoring period and targets set"]},

  out_lt_welfare:{type:"outcome",tone:"informal",progress:100,title:"Long-term sickness — initial welfare check",
    body:"Make contact with the employee to complete a welfare check. This is a supportive, non-judgmental conversation. Request a fit note if not already received. Discuss any anticipated return date.",
    actions:["Welfare call or visit completed","Fit note requested if absent 7+ days","Supportive conversation documented","Anticipated return date explored","No pressure on return at this stage"]},

  out_lt_monitoring:{type:"outcome",tone:"escalate",progress:100,title:"Long-term sickness — ongoing welfare monitoring",
    body:"Schedule regular welfare meetings (suggested: fortnightly or monthly depending on absence length). Keep records of all contact. Begin to consider whether an occupational health referral is appropriate and whether any reasonable adjustments may assist an earlier return.",
    actions:["Regular welfare meetings scheduled","All contact documented","OH referral timetable considered","Reasonable adjustments explored","Fit notes maintained on record"]},

  out_lt_oh:{type:"outcome",tone:"escalate",progress:100,title:"Long-term sickness — occupational health referral",
    body:"Request consent from the employee and refer to occupational health (OH). The OH report will advise on fitness to work, reasonable adjustments, and likely return dates. A phased return plan may be recommended.",
    actions:["Employee consent obtained","OH referral submitted","OH report reviewed with employee","Reasonable adjustments identified","Phased return plan if recommended"]},

  out_lt_adjustments:{type:"outcome",tone:"escalate",progress:100,title:"Long-term sickness — reasonable adjustments required",
    body:"The Equality Act 2010 requires employers to consider reasonable adjustments where a condition may amount to a disability. Consult with the employee, OH, and if necessary, legal, before making any decisions about the employee's role or employment status.",
    actions:["Reasonable adjustments assessed","Equality Act 2010 duty considered","Adjustments implemented where practicable","Legal consult if any dismissal considered","Decision fully documented"]},

  out_formal_absence_lt_capability:{type:"outcome",tone:"formal",progress:100,title:"Long-term sickness — capability process",
    body:"Where an employee is unable to return within a reasonable period, a capability process may be initiated after all other options have been exhausted. This must follow the ACAS Code of Practice. Consult Senior HR and legal before any decision is made. The Equality Act 2010 duty applies throughout.",
    actions:["Full welfare and OH records reviewed","Senior HR and legal consultation","ACAS Code compliance confirmed","Capability hearing with right to be accompanied","ET risk assessed before any dismissal"]},

  /* ACCOMMODATION OUTCOMES */
  out_flexible_work:{type:"outcome",tone:"informal",progress:100,title:"Flexible working request — statutory or informal",
    body:"Employees with 26+ weeks' service have a statutory right to request flexible working (Employment Relations (Flexible Working) Act 2023). The request must be considered seriously and decided within 2 months. Any refusal must be for a valid business reason.",
    actions:["Acknowledge request in writing","Business impact assessment completed","Decision within 2 months","If refused: valid business reason documented","Right of appeal if refused"]},

  out_disability_adjust:{type:"outcome",tone:"escalate",progress:100,title:"Disability-related adjustment — Equality Act duty",
    body:"Where a condition may amount to a disability under the Equality Act 2010, the employer has a duty to consider reasonable adjustments. Consult OH and involve Senior HR. Document all steps taken.",
    actions:["Equality Act 2010 duty assessed","OH referral arranged","Adjustments identified and costed","Adjustments implemented where practicable","Decision fully documented"]},

  out_informal_accommodation:{type:"outcome",tone:"informal",progress:100,title:"Informal accommodation — agreed",
    body:"Discuss the accommodation needed with the employee and their line manager. Agree practical steps in writing. Review in 4 weeks.",
    actions:["Conversation completed","Practical steps agreed in writing","Line manager briefed","Review date set"]},

  out_parental_leave:{type:"outcome",tone:"informal",progress:100,title:"Parental or family leave — statutory entitlement",
    body:"Review the employee's statutory entitlement: maternity (up to 52 weeks), paternity (up to 2 weeks), shared parental leave, adoption leave, or parental bereavement leave. Issue the correct notice and confirm the leave plan in writing.",
    actions:["Statutory entitlement confirmed","Written leave plan issued","KIT/SPLIT days discussed if applicable","Payroll notified","Return-to-work plan discussed"]},

  out_work_environment:{type:"outcome",tone:"escalate",progress:100,title:"Work environment or safety concern",
    body:"Safety concerns must be assessed without delay. Conduct a risk assessment if appropriate. Where the concern relates to a specific individual's behaviour, consider whether a grievance or conduct process is more appropriate.",
    actions:["Risk assessment completed if required","Immediate mitigation if safety risk","Manager briefed","Formal referral if conduct issue","Follow-up in 5 working days"]}
};

const CATS=[
  {key:"conduct",name:"Conduct & disciplinary",desc:"Misconduct, behaviour, zero-tolerance breaches, harassment",cls:"conduct",next:"conduct_stage",
   icon:`<svg viewBox="0 0 18 18" fill="none" stroke="#C0392B" stroke-width="1.5" stroke-linecap="round"><path d="M9 2v8M9 13v1"/><circle cx="9" cy="9" r="7"/></svg>`},
  {key:"grievance",name:"Grievance & conflict",desc:"Complaints, interpersonal conflict, unfair treatment",cls:"grievance",next:"grievance_stage",
   icon:`<svg viewBox="0 0 18 18" fill="none" stroke="#C97B00" stroke-width="1.5" stroke-linecap="round"><circle cx="9" cy="9" r="6"/><path d="M6.5 7.5C6.5 6 8 5 9.5 5.5S11.5 8 9 9v1.5M9 13v.5"/></svg>`},
  {key:"perf",name:"Performance & capability",desc:"Underperformance, PIPs, capability concerns",cls:"perf",next:"perf_stage",
   icon:`<svg viewBox="0 0 18 18" fill="none" stroke="#0E7A5F" stroke-width="1.5" stroke-linecap="round"><polyline points="3,13 7,8 10,11 15,5"/></svg>`},
  {key:"absence",name:"Attendance & absence",desc:"Short-term, long-term sickness, trigger points, patterns",cls:"absence",next:"absence_stage",
   icon:`<svg viewBox="0 0 18 18" fill="none" stroke="#1A6FB5" stroke-width="1.5" stroke-linecap="round"><rect x="3" y="4" width="12" height="11" rx="2"/><path d="M3 8h12M7 2v3M11 2v3"/></svg>`},
  {key:"accommodation",name:"Accommodations & work environment",desc:"Flexible working, disability, parental leave, safety",cls:"accommodation",next:"accommodation_stage",
   icon:`<svg viewBox="0 0 18 18" fill="none" stroke="#5B4FCF" stroke-width="1.5" stroke-linecap="round"><circle cx="9" cy="6" r="2.5"/><path d="M4 15c0-3 2-5 5-5s5 2 5 5"/></svg>`}
];

let history=[],current="intake",caseData={},outcomeData={},submitted=false;

function genRef(){
  const d=new Date();
  return"ER-"+d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+String(d.getDate()).padStart(2,"0")+"-"+Math.floor(100+Math.random()*900);
}
function switchTab(t){
  document.getElementById("tab-triage").classList.toggle("active",t==="triage");
  document.getElementById("tab-flow").classList.toggle("active",t==="flow");
  document.getElementById("panel-triage").style.display=t==="triage"?"block":"none";
  document.getElementById("panel-flow").style.display=t==="flow"?"block":"none";
}
function bcRender(){
  const el=document.getElementById("bc");
  if(!el)return;
  const stages=[{key:"intake",label:"Case details"},{key:"start",label:"Issue type"},{key:"triage",label:"Triage"},{key:"outcome",label:"Outcome"}];
  const ai=current==="intake"?0:current==="start"?1:STEPS[current]?.type==="outcome"?3:2;
  el.innerHTML=stages.map((s,i)=>{
    if(i<ai)return`<span class="bc-i">${s.label}</span><span class="bc-s"> › </span>`;
    if(i===ai)return`<span class="bc-a">${s.label}</span>`;
    return"";
  }).join("");
}
function render(){
  if(current==="intake"){renderIntake();return;}
  if(submitted){renderSuccess();return;}
  const s=STEPS[current];
  document.getElementById("prog").style.width=(s?.progress||0)+"%";
  bcRender();
  const c=document.getElementById("content");
  if(current==="start"){
    c.innerHTML=`
      <div class="ref-badge"><span class="ref-dot"></span>Case ${caseData.ref} · ${caseData.anonymous?"Anonymous":caseData.claimant}</div>
      <div class="step-hdr">Step 2 of 4 — Issue type</div>
      <div class="step-q">${s.q}</div>
      <div class="cat-grid">${CATS.map(cat=>`<div class="cat-card ${cat.cls}" onclick="choose('${cat.next}','${cat.name}','${cat.key}')"><div class="cat-icon">${cat.icon}</div><div class="cat-name">${cat.name}</div><div class="cat-desc">${cat.desc}</div></div>`).join("")}</div>
      <div class="nav-row"><button class="back-btn" onclick="goIntake()">‹ Edit case details</button><button class="rst-btn" onclick="restart()">↺ Restart</button></div>`;
    return;
  }
  if(s.type==="outcome"){
    outcomeData=s;
    const toneLabel={formal:"Formal process required",escalate:"Escalate — senior HR involvement",informal:"Informal action",tribunal:"Employment Tribunal pathway"};
    const toneIcon={formal:"■",escalate:"▲",informal:"●",tribunal:"⚖"};
    const rd={formal:"ER Case Management System",escalate:"Senior HR & ER Queue",informal:"Manager Action Log",tribunal:"Legal Team — ET Track"};
    const tl=toneLabel[s.tone]||"Triage outcome";
    c.innerHTML=`
      <div class="ref-badge"><span class="ref-dot"></span>Case ${caseData.ref} · ${caseData.anonymous?"Anonymous":caseData.claimant}</div>
      <div class="step-hdr">Step 4 of 4 — Outcome</div>
      <div class="out-wrap ${s.tone}">
        <div class="out-hdr"><div class="out-tag">${toneIcon[s.tone]||"●"} ${tl}</div><div class="out-title">${s.title}</div><div class="out-body">${s.body}</div></div>
        <div class="out-actions"><div class="out-alabel">Recommended next steps</div><div class="chips">${s.actions.map(a=>`<span class="chip">${a}</span>`).join("")}</div></div>
      </div>
      <div class="sub-card">
        <div class="sub-title">Ready to log this case?</div>
        <div class="sub-sub">Details and triage outcome will be recorded and routed to <strong>${rd[s.tone]||"ER Queue"}</strong>.</div>
        <div class="sum-grid">
          <div class="si"><div class="si-l">Claimant</div><div class="si-v">${caseData.anonymous?"Anonymous":caseData.claimant}</div></div>
          <div class="si"><div class="si-l">Respondent</div><div class="si-v">${caseData.respondent}</div></div>
          <div class="si"><div class="si-l">Reported by</div><div class="si-v">${caseData.reportedBy}</div></div>
          <div class="si"><div class="si-l">Reported to</div><div class="si-v">${caseData.reportedTo}</div></div>
          <div class="si"><div class="si-l">Department</div><div class="si-v">${caseData.dept}</div></div>
          <div class="si"><div class="si-l">Date logged</div><div class="si-v">${caseData.date}</div></div>
        </div>
        <div class="sub-acts">
          <button class="pri-btn" onclick="submitCase()">Submit to ${rd[s.tone]||"ER Queue"} →</button>
          <button class="rst-btn" onclick="dlSummary()">↓ Download summary</button>
        </div>
      </div>
      <div class="disc">This framework is a practice guide developed by Sneha Manjunath. Always apply professional judgement and refer to your organisation's policies and the ACAS Code of Practice. For Employment Tribunal matters, refer immediately to qualified legal counsel.</div>
      <div class="nav-row" style="margin-top:10px"><button class="back-btn" onclick="goBack()">‹ Back</button><button class="rst-btn" onclick="restart()">↺ New case</button></div>`;
    return;
  }
  const n=history.length+2;
  const dc="dot-"+(s.dot||"neutral");
  c.innerHTML=`
    <div class="ref-badge"><span class="ref-dot"></span>Case ${caseData.ref} · ${caseData.anonymous?"Anonymous":caseData.claimant}</div>
    <div class="step-hdr">Step ${n} of 4 — ${s.label||""}</div>
    <div class="step-q">${s.q}</div>
    <div class="opt-list">${s.options.map(o=>`<button class="opt-btn" onclick="choose('${o.next}',\`${o.t.replace(/`/g,"'")}\`,'')"><span class="opt-dot ${dc}"></span><div><span class="opt-text">${o.t}</span>${o.sub?`<div class="opt-sub">${o.sub}</div>`:""}</div></button>`).join("")}</div>
    <div class="nav-row"><button class="back-btn" onclick="goBack()">‹ Back</button><button class="rst-btn" onclick="restart()">↺ Restart</button></div>`;
}
function renderIntake(){
  document.getElementById("prog").style.width="12%";
  bcRender();
  document.getElementById("content").innerHTML=`
    <div class="step-hdr">Step 1 of 4 — Case details</div>
    <div class="step-q">Log the case before triaging</div>
    <div class="field-group">
      <div class="field-row">
        <div><div class="flabel">Claimant / employee<span>*</span></div><input class="finput" id="f-cl" placeholder="Full name or employee ID" value="${caseData.claimant||''}"></div>
        <div><div class="flabel">Respondent / alleged party</div><input class="finput" id="f-re" placeholder="Full name, ID, or N/A" value="${caseData.respondent||''}"></div>
      </div>
      <div class="field-row">
        <div><div class="flabel">Reported by<span>*</span></div>
          <select class="fselect" id="f-rb">
            <option value="">Select...</option>
            ${["Employee directly","Line manager","Third party","HR team","Anonymous"].map(o=>`<option ${caseData.reportedBy===o?"selected":""}>${o}</option>`).join("")}
          </select>
        </div>
        <div><div class="flabel">Reported to<span>*</span></div>
          <select class="fselect" id="f-rt">
            <option value="">Select...</option>
            ${["HR Business Partner","HR Advisor","Line manager","Senior HR","HR Shared Services"].map(o=>`<option ${caseData.reportedTo===o?"selected":""}>${o}</option>`).join("")}
          </select>
        </div>
      </div>
      <div><div class="flabel">Department / business area</div><input class="finput" id="f-dp" placeholder="e.g. Operations, Finance, People & Culture" value="${caseData.dept||''}"></div>
      <label class="anon-row"><input type="checkbox" id="f-an" ${caseData.anonymous?"checked":""}><span class="anon-txt">Claimant wishes to remain anonymous</span><span class="anon-sub">Disclosure restricted</span></label>
    </div>
    <div id="ierr" class="err" style="display:none">Please complete all required fields marked *</div>
    <div class="nav-row"><span></span><button class="pri-btn" onclick="submitIntake()">Continue to triage →</button></div>`;
}
function submitIntake(){
  const cl=document.getElementById("f-cl").value.trim();
  const rb=document.getElementById("f-rb").value;
  const rt=document.getElementById("f-rt").value;
  if(!cl||!rb||!rt){document.getElementById("ierr").style.display="block";return;}
  caseData={
    claimant:cl,
    respondent:document.getElementById("f-re").value.trim()||"Not specified",
    reportedBy:rb,reportedTo:rt,
    dept:document.getElementById("f-dp").value.trim()||"Not specified",
    anonymous:document.getElementById("f-an").checked,
    ref:genRef(),
    date:new Date().toLocaleDateString("en-GB",{day:"2-digit",month:"short",year:"numeric"})
  };
  current="start";history=[];render();
}
function renderSuccess(){
  document.getElementById("prog").style.width="100%";
  bcRender();
  const rd={formal:"ER Case Management System",escalate:"Senior HR & ER Queue",informal:"Manager Action Log",tribunal:"Legal Team — ET Track"};
  document.getElementById("content").innerHTML=`
    <div class="suc-screen">
      <div class="suc-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#0E7A5F" stroke-width="2.5" stroke-linecap="round"><path d="M20 6L9 17l-5-5"/></svg></div>
      <div class="suc-title">Case logged successfully</div>
      <div class="suc-sub">Recorded and routed to <strong>${rd[outcomeData.tone]||"ER Queue"}</strong>.</div>
      <div class="suc-ref">${caseData.ref}</div>
      <div class="route-row"><span class="rpill">Case intake</span><span class="rarr">→</span><span class="rpill">Triage complete</span><span class="rarr">→</span><span class="rpill active">${rd[outcomeData.tone]||"ER Queue"}</span></div>
      <button class="rst-btn" style="font-size:12px;padding:8px 20px" onclick="restart()">Log another case</button>
    </div>`;
}
function submitCase(){submitted=true;render();}
function dlSummary(){
  const s=outcomeData;
  const tl={formal:"Formal process required",escalate:"Escalate — senior HR",informal:"Informal action",tribunal:"Employment Tribunal pathway"}[s.tone]||"Outcome";
  const txt=`ER CASE SUMMARY\n${"═".repeat(44)}\nReference:    ${caseData.ref}\nDate logged:  ${caseData.date}\n\nCASE DETAILS\n${"─".repeat(44)}\nClaimant:     ${caseData.anonymous?"Anonymous":caseData.claimant}\nRespondent:   ${caseData.respondent}\nReported by:  ${caseData.reportedBy}\nReported to:  ${caseData.reportedTo}\nDepartment:   ${caseData.dept}\n\nTRIAGE OUTCOME\n${"─".repeat(44)}\nClassification: ${tl}\nOutcome:        ${s.title}\n\nGuidance:\n${s.body}\n\nNext steps:\n${s.actions.map(a=>"  • "+a).join("\n")}\n\n${"═".repeat(44)}\nER Triage Framework · Sneha Manjunath\nFor practice purposes only.\nAlways refer to the ACAS Code of Practice and applicable company policy.\nEmployment Tribunal matters must be referred to qualified legal counsel.`;
  const a=document.createElement("a");
  a.href=URL.createObjectURL(new Blob([txt],{type:"text/plain"}));
  a.download=`${caseData.ref}-triage-summary.txt`;a.click();
}
function choose(next,label,key){history.push({step:current,chosen:label,key});current=next;render();}
function goBack(){if(!history.length){current="start";render();return;}const l=history.pop();current=l.step;render();}
function goIntake(){history=[];current="intake";render();}
function restart(){history=[];current="intake";submitted=false;outcomeData={};render();}
render();
</script>
</body>
</html>
