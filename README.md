# calculadoapediatrica[CALCULADORA_PEDIATRICA_EMERGENCIA_FINAL.html](https://github.com/user-attachments/files/32943129/CALCULADORA_PEDIATRICA_EMERGENCIA_FINAL.html)
<!doctype html>
<html lang="pt-BR">
<head>
<!-- CANDIDATA FINAL V2 — SELEÇÃO DE DOSE ANTIBIÓTICOS EV | Revisão funcional e estrutural: 02/10/2026 | Arquivo-base aprovado V10.8 -->
<!-- VERSÃO-BASE OFICIAL PARA ALTERAÇÕES FUTURAS: V10.8 FINAL — ESCALAS COM DESCRIÇÃO | 02/10/2026 -->
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Calculadora Pediátrica de Emergência</title>

<style>
:root{
 --bg:#f6f8fb;--card:#ffffff;--ink:#172033;--muted:#667085;--line:#e3e8ef;
 --primary:#176b87;--primary2:#0f8b8d;--soft:#eaf6f7;--danger:#b42318;
 --amber:#b54708;--amberbg:#fff8e8;--green:#067647;--shadow:0 5px 20px rgba(16,24,40,.06)
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;font-family:Inter,-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Arial,sans-serif;background:var(--bg);color:var(--ink)}
header{background:#fff;border-bottom:1px solid var(--line);padding:18px 15px 16px;position:relative}
.wrap,main{max-width:1160px;margin:auto}
.brand{display:flex;align-items:center;gap:10px}
.logo{width:40px;height:40px;border-radius:12px;background:linear-gradient(135deg,var(--primary),var(--primary2));display:grid;place-items:center;color:#fff;font-weight:900;font-size:18px}
.eyebrow{font-size:10px;font-weight:900;letter-spacing:.13em;text-transform:uppercase;color:var(--primary)}
h1{margin:3px 0 3px;font-size:clamp(24px,4vw,34px)}
header p{margin:0;color:var(--muted);font-size:13px}
.inputs{position:sticky;top:0;z-index:20;margin:0 auto 10px;background:rgba(246,248,251,.96);backdrop-filter:blur(10px);padding:10px 0;display:grid;grid-template-columns:1fr 1fr auto;gap:8px;align-items:end}
.field label{display:block;font-size:11px;font-weight:800;margin:0 0 4px;color:#344054}
.field input,select{width:100%;padding:11px 12px;border:1px solid #cfd6e2;border-radius:9px;font-size:15px;background:#fff;outline:none}
.field input:focus,select:focus{border-color:var(--primary);box-shadow:0 0 0 3px rgba(23,107,135,.09)}
.actions{display:flex;gap:7px;flex-wrap:wrap}.btn{border:0;border-radius:9px;padding:11px 14px;font-weight:800;cursor:pointer}.primary{background:var(--primary);color:#fff}.secondary{background:#fff;border:1px solid #cfd6e2;color:#344054}
.notice{border:1px solid #f2c8c3;background:#fff7f6;color:#8f2118;border-radius:10px;padding:9px 11px;font-size:11px;line-height:1.45;margin-bottom:10px}
.tabs{display:flex;gap:6px;overflow-x:auto;padding:3px 0 11px;scrollbar-width:thin}
.tab{white-space:nowrap;border:1px solid #d7dee8;background:#fff;padding:8px 11px;border-radius:8px;font-size:11px;font-weight:850;cursor:pointer;color:#475467}
.tab:hover{border-color:#a9cbd4}
.tab.active{background:var(--primary);color:#fff;border-color:var(--primary)}
.panel{display:none}.panel.active{display:block}
.section-title{display:flex;justify-content:space-between;align-items:center;gap:10px;margin:10px 0 8px}.section-title h2{font-size:18px;margin:0}.badge{font-size:9px;font-weight:850;padding:4px 7px;border-radius:999px;background:#eef2f7;color:#475467}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:9px}
.card{background:#fff;border:1px solid var(--line);border-radius:11px;padding:12px;box-shadow:0 2px 7px rgba(16,24,40,.025)}
.drug{font-size:14px;font-weight:900;margin-bottom:3px}.dose{font-size:11px;color:var(--muted);margin-bottom:7px;line-height:1.35}.result{font-size:20px;font-weight:900;color:#101828}.result small{font-size:11px;color:var(--muted);font-weight:750}.rx{margin-top:6px;color:#475467;font-size:11px;line-height:1.45}.micro{margin-top:6px;color:#175cd3;font-size:10px;font-weight:800}.warn{margin-top:7px;padding:6px 7px;border-radius:7px;background:var(--amberbg);color:var(--amber);font-size:10px;font-weight:750;line-height:1.35}
.good{margin-top:7px;padding:6px 7px;border-radius:7px;background:#ecfdf3;color:#067647;font-size:10px;font-weight:750}
.infusion .result{color:var(--green)}
.equipment{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:8px}.eq{background:#fff;border:1px solid var(--line);border-radius:10px;padding:10px}.eq b{display:block;font-size:9px;color:var(--muted);margin-bottom:3px}.eq span{font-size:15px;font-weight:900}
.energy{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}.energy .eq{background:#edf8fa;border-color:#c7e7eb}.energy .eq span{font-size:19px;color:#155b75}
.calcbox{background:#fff;border:1px solid var(--line);border-radius:11px;padding:11px;margin-bottom:9px}.calcbox h3{margin:0 0 7px;font-size:14px}.row{display:grid;grid-template-columns:repeat(3,1fr);gap:7px}.mini{font-size:10px;color:var(--muted)}
.footer{font-size:10px;color:#667085;line-height:1.45;margin:24px 0 40px;padding-top:12px;border-top:1px solid var(--line)}
/* Compact infusion selector */
.quickbar{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:10px}
.quickdrug{border:1px solid #cbd8de;background:#fff;border-radius:8px;padding:8px 10px;font-size:11px;font-weight:850;cursor:pointer;color:#344054}
.quickdrug.active{background:var(--primary);border-color:var(--primary);color:#fff}
.inf-focus{background:#fff;border:1px solid var(--line);border-radius:12px;padding:14px;margin-bottom:10px;box-shadow:var(--shadow)}
.inf-head{display:flex;align-items:start;justify-content:space-between;gap:12px}
.inf-head h3{margin:0;font-size:18px}.inf-head .close{border:0;background:#f2f4f7;border-radius:7px;padding:6px 9px;cursor:pointer}
.inf-meta{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:10px 0}
.meta{background:#f8fafc;border:1px solid #edf0f4;border-radius:8px;padding:8px;font-size:11px;line-height:1.4}
.meta b{display:block;color:#344054;margin-bottom:2px}
.flowrow{display:grid;grid-template-columns:160px 1fr;gap:8px;align-items:end;margin-top:8px}
.flowrow input{width:100%;padding:11px;border:1px solid #cfd6e2;border-radius:9px;font-size:16px}
.doseout{background:var(--soft);border:1px solid #cae8eb;border-radius:9px;padding:10px 12px}
.doseout b{font-size:20px;color:#155b75}
.summary{background:#fff;border:1px solid var(--line);border-radius:12px;padding:12px;margin-top:10px}
.summary h3{margin:0 0 8px;font-size:14px}.summary pre{white-space:pre-wrap;font-family:inherit;font-size:11px;background:#f8fafc;border-radius:8px;padding:9px;margin:0 0 8px;color:#344054}
@media(max-width:820px){.inputs{grid-template-columns:1fr 1fr}.actions{grid-column:1/-1}.grid{grid-template-columns:1fr}.equipment{grid-template-columns:repeat(2,1fr)}.row{grid-template-columns:1fr}.flowrow{grid-template-columns:1fr}.inf-meta{grid-template-columns:1fr}}
@media(max-width:500px){header{padding-top:14px}.inputs{grid-template-columns:1fr}.actions{grid-column:auto}.equipment,.energy{grid-template-columns:1fr}.result{font-size:19px}.tab{font-size:10px;padding:8px 9px}.quickdrug{padding:7px 9px}}
@media print{body{background:#fff}.tabs,.actions,.quickbar,.close{display:none}.panel{display:block!important}.card,.eq,.calcbox,.inf-focus{break-inside:avoid}.inputs{position:static}.summary{display:block}}

@media print{#ventilacao{display:none!important}}
</style>


<style>
.pews-wrap{background:#fff;border:1px solid #dfe5ee;border-radius:14px;padding:14px;margin:12px 0}
.pews-title{font-weight:900;font-size:17px;margin-bottom:4px}
.pews-sub{font-size:11px;color:#667085;margin-bottom:10px;line-height:1.4}
.pews-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px}
.pews-field label{display:block;font-size:11px;font-weight:800;color:#344054;margin-bottom:4px}
.pews-field input,.pews-field select{width:100%;padding:10px;border:1px solid #cfd6e2;border-radius:9px;background:#fff;font-size:13px}
.pews-result{margin-top:12px;border-radius:12px;padding:14px;border:2px solid transparent}
.pews-result.low{background:#ecfdf3;border-color:#75e0a7;color:#05603a}
.pews-result.mod{background:#fffaeb;border-color:#fec84b;color:#93370d}
.pews-result.high{background:#fef3f2;border-color:#fda29b;color:#912018}
.pews-score{font-size:28px;font-weight:950;line-height:1}
.pews-risk{font-size:15px;font-weight:900;margin-top:4px}
.pews-guidance{font-size:11px;margin-top:7px;line-height:1.4}
@media(max-width:720px){.pews-grid{grid-template-columns:1fr 1fr}}
@media(max-width:470px){.pews-grid{grid-template-columns:1fr}}
</style>


<style>
.print-only-report{display:none}

@media print{
  @page{size:A4 portrait;margin:8mm}

  /* Preserve screen UI completely; hide it only in print output */
  body > header,
  body > main,
  body > footer,
  .pews-wrap,
  .tabs,
  .actions,
  .notice:not(.print-notice){
    display:none !important;
  }

  body{
    background:#fff !important;
    color:#111 !important;
    margin:0 !important;
    padding:0 !important;
    font-family:Arial,Helvetica,sans-serif !important;
  }

  .print-only-report{
    display:block !important;
    width:100% !important;
    max-width:none !important;
    margin:0 !important;
    padding:0 !important;
  }

  .print-report-header{
    border-bottom:2px solid #222;
    padding-bottom:5px;
    margin-bottom:6px;
  }

  .print-report-header h1{
    margin:0 0 5px 0;
    font-size:14pt;
    text-align:center;
    letter-spacing:.2px;
  }

  #printPatientData{
    font-size:9pt;
    text-align:center;
    line-height:1.35;
  }

  .print-dose-table{
    width:100%;
    border-collapse:collapse;
    table-layout:fixed;
    font-size:7.2pt;
    line-height:1.17;
  }

  .print-dose-table th,
  .print-dose-table td{
    border:1px solid #777;
    padding:3px 4px;
    vertical-align:top;
    overflow-wrap:anywhere;
  }

  .print-dose-table thead{
    display:table-header-group;
  }

  .print-dose-table th{
    background:#e8ecef !important;
    color:#111 !important;
    font-weight:700;
    text-align:left;
  }

  .print-dose-table th:nth-child(1){width:14%}
  .print-dose-table th:nth-child(2){width:23%}
  .print-dose-table th:nth-child(3){width:19%}
  .print-dose-table th:nth-child(4){width:44%}

  .print-dose-table tr{
    break-inside:avoid;
    page-break-inside:avoid;
  }

  .print-dose-table .section-row td{
    background:#dfe6eb !important;
    font-weight:700;
    font-size:7.5pt;
    padding:3px 4px;
  }

  .print-result{
    font-weight:700;
    font-size:7.8pt;
  }

  .print-report-footer{
    margin-top:6px;
    padding-top:5px;
    border-top:1px solid #777;
    text-align:center;
    font-size:7pt;
    color:#333;
  }
}
</style>


<style id="v10-layout">
:root{
  --v10-bg:#06111d;--v10-bg2:#091827;--v10-panel:#0b1a2a;--v10-panel2:#0e2032;
  --v10-line:#20364a;--v10-text:#f7fbff;--v10-muted:#a9bed1;--v10-red:#ff4051;
  --v10-cyan:#39d5ff;--v10-green:#26e6a2;--v10-yellow:#ffc53d;--v10-purple:#a67cff;
}
body{background:
 radial-gradient(circle at 78% 8%,rgba(29,112,180,.18),transparent 27%),
 linear-gradient(135deg,#06111d 0%,#071522 55%,#07111b 100%)!important;
 color:var(--v10-text)!important;min-height:100vh}
body>header{display:none}
body>main{max-width:none!important;margin:0 0 0 248px!important;padding:92px 28px 36px!important}
body>footer{margin-left:248px!important;max-width:none!important;border-top:1px solid var(--v10-line)!important;color:var(--v10-muted)!important}
body>footer strong{color:#fff!important}

.v10-sidebar{position:fixed;z-index:1000;left:0;top:0;bottom:0;width:248px;background:rgba(5,17,29,.96);
 border-right:1px solid var(--v10-line);padding:20px 12px;overflow:auto;backdrop-filter:blur(14px)}
.v10-brand{display:flex;align-items:center;gap:11px;padding:4px 10px 22px;border-bottom:1px solid rgba(255,255,255,.06);margin-bottom:14px}
.v10-pulse{font-size:30px;color:var(--v10-red);line-height:1}.v10-brand b{font-size:19px}.v10-brand small{display:block;color:var(--v10-muted);font-size:10px;margin-top:2px}
.v10-homebtn,.v10-printbtn{width:100%;border:1px solid transparent;background:transparent;color:#dce9f5;padding:11px 12px;
 border-radius:9px;text-align:left;font-size:12px;cursor:pointer;margin:2px 0;display:flex;gap:10px;align-items:center}
.v10-homebtn:hover,.v10-printbtn:hover{background:#10263a;border-color:#28455f}
.v10-homebtn.active{background:linear-gradient(90deg,rgba(255,64,81,.25),rgba(255,64,81,.12));border-color:#a62d3b}
.v10-side-title{color:#6f8ba4;text-transform:uppercase;font-size:9px;font-weight:900;letter-spacing:.11em;margin:18px 12px 7px}
.v10-sidebar .tabs{display:block!important;margin:0!important;padding:0!important;background:none!important;border:0!important;overflow:visible!important}
.v10-sidebar .tab{display:block!important;width:100%!important;margin:2px 0!important;border:1px solid transparent!important;background:transparent!important;
 color:#cfe0ef!important;border-radius:9px!important;padding:10px 12px!important;text-align:left!important;font-size:11px!important;white-space:normal!important}
.v10-sidebar .tab:hover{background:#10263a!important;border-color:#28455f!important}
.v10-sidebar .tab.active{background:#132b40!important;color:#fff!important;border-color:#31516d!important}

.v10-topbar{position:fixed;z-index:990;left:248px;right:0;top:0;height:72px;background:rgba(6,17,29,.88);backdrop-filter:blur(15px);
 border-bottom:1px solid var(--v10-line);display:flex;align-items:center;gap:18px;padding:0 28px}
.v10-top-title{font-weight:900;min-width:220px}.v10-top-title span{color:var(--v10-red)}
.v10-search{flex:1;max-width:660px;position:relative}.v10-search input{width:100%;background:#0b1b2b;border:1px solid #284158;color:#fff;border-radius:24px;padding:12px 18px 12px 42px;outline:none}
.v10-search:before{content:"⌕";position:absolute;left:17px;top:7px;color:#bcd2e5;font-size:23px}
.v10-top-actions{margin-left:auto;display:flex;gap:8px}.v10-top-actions button{background:#0b1b2b;border:1px solid #284158;color:#dce9f5;border-radius:9px;padding:9px 12px;cursor:pointer}

.v10-dashboard{display:block;margin-bottom:20px}
.v10-hero{padding:18px 0 14px}.v10-kicker{font-size:11px;text-transform:uppercase;letter-spacing:.12em;color:var(--v10-cyan);font-weight:900}
.v10-hero h2{font-size:38px;line-height:1.06;margin:8px 0 7px;color:#fff}.v10-hero h2 span{color:var(--v10-red)}
.v10-hero p{color:#b9cce0;font-size:15px;margin:0;max-width:900px}
.v10-trust{display:flex;gap:12px;flex-wrap:wrap;margin:18px 0}.v10-trust div{background:#0a1a29;border:1px solid var(--v10-line);border-radius:11px;padding:10px 13px;font-size:11px;color:#dbe9f5}
.v10-trust b{display:block;color:#fff;font-size:12px;margin-bottom:2px}
.v10-disclaimer{background:linear-gradient(90deg,rgba(255,197,61,.12),rgba(255,197,61,.04));border:1px solid rgba(255,197,61,.38);
 border-radius:12px;padding:13px 15px;color:#f6e5ad;font-size:11px;line-height:1.5;margin:0 0 18px}
.v10-grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:10px;margin-bottom:18px}
.v10-card{border:1px solid var(--v10-line);background:linear-gradient(145deg,#0c1c2c,#091724);border-radius:12px;padding:15px;cursor:pointer;color:#fff;text-align:left;min-height:92px;transition:.15s}
.v10-card:hover{transform:translateY(-2px);border-color:#3d6687;background:#10243a}.v10-card .ico{font-size:22px;display:block;margin-bottom:9px}.v10-card b{font-size:13px}.v10-card small{display:block;color:var(--v10-muted);font-size:10px;margin-top:4px;line-height:1.35}
.v10-quick{display:flex;gap:8px;flex-wrap:wrap;margin:6px 0 20px}.v10-quick button{background:#0c1c2c;border:1px solid #29445c;color:#eaf4fc;border-radius:9px;padding:9px 13px;font-size:10px;cursor:pointer}.v10-quick button:hover{border-color:var(--v10-red)}

.inputs{position:sticky!important;top:84px!important;z-index:30!important;background:rgba(9,24,39,.95)!important;border:1px solid var(--v10-line)!important;
 box-shadow:0 12px 30px rgba(0,0,0,.25)!important;border-radius:13px!important;padding:12px!important;margin:0 0 18px!important}
.field label{color:#a9bed1!important}.field input,.field select,select,input,textarea{background:#0a1a29!important;color:#fff!important;border-color:#29445c!important}
.btn.primary{background:linear-gradient(90deg,#ef3348,#ff4e5f)!important}.btn.secondary{background:#10263a!important;color:#fff!important;border-color:#31516d!important}
.notice{background:#10202f!important;color:#c9d9e8!important;border-color:#2b4358!important}
.panel,.card,.calcbox,.eq,.pews-wrap,.score-card,.abx-ev-card{background:#0b1b2b!important;color:#eef7ff!important;border-color:#263f55!important;box-shadow:none!important}
.panel h2,.panel h3,.card h3,.calcbox h3,.pews-title{color:#fff!important}
.muted,.sub,.pews-sub{color:#a9bed1!important}
.result{background:#0e2737!important;color:#e8f7ff!important;border-color:#2b536a!important}
table{color:#eaf4fc!important}th{background:#10263a!important;color:#fff!important}td,th{border-color:#29445c!important}
main>.tabs{display:none!important}

.v10-reference{margin:20px 0 0;background:#091927;border:1px solid var(--v10-line);border-radius:12px;padding:14px;color:#a9bed1;font-size:10px;line-height:1.55}
.v10-reference strong{color:#fff}
@media(max-width:1050px){.v10-grid{grid-template-columns:repeat(3,1fr)}}
@media(max-width:820px){
 .v10-sidebar{width:74px;padding:14px 7px}.v10-brand div:last-child,.v10-side-title,.v10-sidebar .tab{font-size:0!important}.v10-sidebar .tab:before{content:"•";font-size:20px}
 body>main{margin-left:74px!important;padding:84px 14px 28px!important}.v10-topbar{left:74px;padding:0 14px}.v10-top-title{display:none}.v10-grid{grid-template-columns:repeat(2,1fr)}
 body>footer{margin-left:74px!important}
}
@media(max-width:520px){.v10-grid{grid-template-columns:1fr}.v10-hero h2{font-size:28px}.v10-top-actions{display:none}}
@media print{.v10-sidebar,.v10-topbar,.v10-dashboard,.v10-reference{display:none!important}body>main,body>footer{margin-left:0!important}}
</style>


<style id="v10-light-theme">
:root{
 --v10-bg:#f4f8fc;--v10-bg2:#ffffff;--v10-panel:#ffffff;--v10-panel2:#f7faff;
 --v10-line:#d8e3ee;--v10-text:#17283a;--v10-muted:#63788d;--v10-red:#ef4051;
 --v10-cyan:#078bc7;--v10-green:#059669;--v10-yellow:#b7791f;--v10-purple:#7256c7;
}
body{
 background:
 radial-gradient(circle at 82% 5%,rgba(65,156,220,.12),transparent 27%),
 linear-gradient(135deg,#f8fbfe 0%,#f2f7fb 60%,#edf4f9 100%)!important;
 color:#17283a!important;
}
.v10-sidebar{background:rgba(255,255,255,.97)!important;border-right-color:#d9e4ee!important;box-shadow:5px 0 22px rgba(32,65,96,.06)!important}
.v10-brand{border-bottom-color:#e5edf4!important}.v10-brand b{color:#16283a!important}.v10-brand small{color:#71859a!important}
.v10-homebtn,.v10-printbtn{color:#30475d!important}.v10-homebtn:hover,.v10-printbtn:hover{background:#edf5fb!important;border-color:#c7dbea!important}
.v10-homebtn.active{background:linear-gradient(90deg,rgba(239,64,81,.14),rgba(239,64,81,.06))!important;border-color:#ef9ca5!important;color:#b92838!important}
.v10-side-title{color:#8798a8!important}.v10-sidebar .tab{color:#3e556b!important}
.v10-sidebar .tab:hover{background:#eef6fb!important;border-color:#cbddea!important}.v10-sidebar .tab.active{background:#e5f2fb!important;color:#0e5f8e!important;border-color:#b8d8eb!important}
.v10-topbar{background:rgba(255,255,255,.91)!important;border-bottom-color:#dce6ef!important;box-shadow:0 4px 18px rgba(36,70,100,.05)!important}
.v10-top-title{color:#17283a!important}.v10-search input{background:#f7fafc!important;border-color:#cfdeea!important;color:#203448!important}
.v10-search:before{color:#6f8498!important}.v10-top-actions button{background:#f7fafc!important;border-color:#cfdeea!important;color:#344b60!important}
.v10-hero h2{color:#17283a!important}.v10-hero p{color:#61768b!important}
.v10-trust div,.v10-card{background:linear-gradient(145deg,#ffffff,#f8fbfd)!important;border-color:#d6e2ec!important;color:#1d3043!important;box-shadow:0 8px 24px rgba(41,74,104,.05)!important}
.v10-trust b,.v10-card b{color:#17283a!important}.v10-card small{color:#6d8092!important}.v10-card:hover{background:#fff!important;border-color:#9fc6df!important;box-shadow:0 12px 28px rgba(41,74,104,.09)!important}
.v10-disclaimer{background:linear-gradient(90deg,#fff9e8,#fffdf7)!important;border-color:#e8cf83!important;color:#715b20!important}
.v10-quick button{background:#fff!important;border-color:#cddde9!important;color:#30475d!important}
.inputs{background:rgba(255,255,255,.96)!important;border-color:#d5e2ec!important;box-shadow:0 12px 28px rgba(40,70,100,.08)!important}
.field label{color:#536a80!important}.field input,.field select,select,input,textarea{background:#fff!important;color:#203448!important;border-color:#cbdbe7!important}
.btn.secondary{background:#eef5fa!important;color:#274158!important;border-color:#c6d9e7!important}
.notice{background:#f3f8fc!important;color:#50677d!important;border-color:#d4e2ed!important}
.panel,.card,.calcbox,.eq,.pews-wrap,.score-card,.abx-ev-card{background:#fff!important;color:#263a4d!important;border-color:#d6e2ec!important;box-shadow:0 7px 22px rgba(40,70,100,.045)!important}
.panel h2,.panel h3,.card h3,.calcbox h3,.pews-title{color:#17283a!important}.muted,.sub,.pews-sub{color:#687d90!important}
.result{background:#eef8fd!important;color:#21475d!important;border-color:#bdddea!important}
table{color:#263a4d!important}th{background:#eef5fa!important;color:#203448!important}td,th{border-color:#d6e2ec!important}
.v10-reference{background:#fff!important;border-color:#d6e2ec!important;color:#63788d!important}.v10-reference strong{color:#1d3043!important}
body>footer{color:#6a7f92!important;border-top-color:#d6e2ec!important}
</style>


<style id="burn-module-css">
.burn-layout{display:grid;grid-template-columns:1.15fr .85fr;gap:14px}
.burn-box{background:#fff;border:1px solid #d6e2ec;border-radius:14px;padding:16px;box-shadow:0 7px 22px rgba(40,70,100,.045)}
.burn-box h3{margin-top:0;color:#17283a}
.burn-regions{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.burn-regions label{display:grid;grid-template-columns:auto 1fr auto;align-items:center;gap:7px;background:#f7fafc;border:1px solid #dbe6ef;border-radius:10px;padding:9px;font-size:11px;color:#344b60}
.burn-regions input[type="checkbox"]{width:17px;height:17px;accent-color:#ef4051}
.burn-auto{min-width:48px;text-align:center;background:#e9f4fb;border:1px solid #c6ddea;color:#155b7d;border-radius:8px;padding:6px 8px;font-weight:900}
.burn-total{margin-top:12px;background:#fff4f5;border:1px solid #f4c4ca;border-radius:11px;padding:13px;color:#8e2733;font-size:14px}
.burn-total strong{font-size:22px;margin-left:7px}
.burn-actions{margin-top:10px}
.burn-alerts{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin-top:14px}
.burn-alerts>div{background:#f7fafc;border:1px solid #d8e4ed;border-radius:11px;padding:11px;color:#536a80;font-size:10px;line-height:1.5}
@media(max-width:850px){.burn-layout,.burn-alerts{grid-template-columns:1fr}.burn-regions{grid-template-columns:1fr}}
@media print{#queimaduras .btn{display:none!important}}
</style>


<style id="v104-modules-css">
.hydr-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin:12px 0}
.hydr-card,.dehyd-card,.gly-info>div,.dehyd-plans>div{background:#fff;border:1px solid #d6e2ec;border-radius:12px;padding:12px;color:#536a80;font-size:10px;line-height:1.45}
.hydr-card b{display:block;color:#17344b;margin-bottom:6px}.hydr-card span{display:block;min-height:58px}.hydr-card button{margin-top:8px;border:1px solid #bfd5e4;background:#edf7fc;color:#145a7d;border-radius:8px;padding:7px 9px;cursor:pointer}
.gly-info,.dehyd-plans{display:grid;grid-template-columns:repeat(2,1fr);gap:9px;margin-top:12px}.gly-info b,.dehyd-plans b{color:#17344b}
.dehyd-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:9px}.dehyd-card h3{margin:0 0 8px}.dehyd-card label{display:block;padding:5px 0}.dehyd-plans{grid-template-columns:repeat(3,1fr)}
@media(max-width:900px){.hydr-grid,.dehyd-grid{grid-template-columns:1fr 1fr}.dehyd-plans{grid-template-columns:1fr}}
@media(max-width:560px){.hydr-grid,.dehyd-grid,.gly-info{grid-template-columns:1fr}}
</style>


<style id="cad-css">
.cad-step{background:#fff;border:1px solid #d6e2ec;border-radius:14px;padding:15px;margin:11px 0;box-shadow:0 7px 22px rgba(40,70,100,.04)}
.cad-step h3{margin:0 0 10px;color:#17344b}.cad-inputs{display:grid;grid-template-columns:repeat(4,1fr);gap:9px}
.cad-two-bag{display:grid;grid-template-columns:280px 1fr;gap:10px;margin-top:10px}.cad-danger{border-color:#efb8be;background:#fffafb}
.cad-neuro{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin-bottom:10px}.cad-neuro label{background:#fff;border:1px solid #ead4d7;border-radius:9px;padding:8px;font-size:10px}
.cad-monitor{background:#eef7fc;border:1px solid #c9deeb;border-radius:10px;padding:12px;color:#31576e;font-size:11px}
.cad-red{background:#fff0f2!important;border-color:#ef9ca5!important;color:#9c2633!important}.cad-amber{background:#fff9e8!important;border-color:#e6cd83!important;color:#735b1a!important}
@media(max-width:900px){.cad-inputs{grid-template-columns:1fr 1fr}.cad-two-bag{grid-template-columns:1fr}.cad-neuro{grid-template-columns:1fr 1fr}}
@media(max-width:560px){.cad-inputs,.cad-neuro{grid-template-columns:1fr}}
</style>


<style id="tab-print-css">
.tab-print-btn{float:right;border:1px solid #b9d5e5;background:#f3faff;color:#145b7e;border-radius:9px;padding:7px 11px;font-weight:800;font-size:10px;cursor:pointer;margin:-2px 0 8px 10px}
.tab-print-btn:hover{background:#e6f5fc}
@media print{
 body.print-one .panel{display:none!important}
 body.print-one .panel.print-target{display:block!important}
 body.print-one .sidebar,body.print-one .topbar,body.print-one .patient-sticky,body.print-one .tab-print-btn,body.print-one #home{display:none!important}
 body.print-one .main,body.print-one .content{margin:0!important;padding:0!important;width:100%!important}
 body.print-one .panel.print-target{box-shadow:none!important;border:none!important}
}
</style>

<style id="cad-dil-css">
.cad-dilutions{margin-top:12px;border-top:1px dashed #c8dce8;padding-top:12px}.cad-dilutions h4{margin:0 0 9px;color:#17344b}
.cad-dil-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:8px}.cad-dil-grid>div{background:#f8fbfd;border:1px solid #d6e4ed;border-radius:10px;padding:10px;color:#506a7e;font-size:10px;line-height:1.5}.cad-dil-grid b{color:#17344b}
@media(max-width:700px){.cad-dil-grid{grid-template-columns:1fr}}
</style>

<style id="v108-home-cleanup">
/* V10.8: início simplificado */
#home .quick-access,
#home .quickAccess,
#home [class*="quick-access"],
#home [class*="quickAccess"]{display:none!important}

/* O bloco de dados do paciente passa a ficar imediatamente após o aviso inicial
   e antes da grade de módulos. */
#home .v108-patient-home{
  margin:14px 0 12px;
  background:#fff;
  border:1px solid #c9ddea;
  border-radius:12px;
  padding:12px 14px;
  box-shadow:0 5px 16px rgba(40,70,100,.035)
}
#home .v108-patient-home-title{
  font-weight:900;color:#17344b;font-size:12px;margin-bottom:8px
}
#home .v108-patient-row{
  display:grid;grid-template-columns:repeat(4,minmax(120px,1fr));gap:9px
}
#home .v108-patient-row label{font-size:9px;font-weight:800;color:#526d81;display:block;margin-bottom:4px}
#home .v108-patient-row input{width:100%;box-sizing:border-box}
@media(max-width:760px){#home .v108-patient-row{grid-template-columns:1fr 1fr}}
@media(max-width:480px){#home .v108-patient-row{grid-template-columns:1fr}}
</style>


<style id="single-tab-print-fix-css">
#singleTabPrintArea{display:none}
@media print{
 body.single-tab-printing > *:not(#singleTabPrintArea){display:none!important}
 body.single-tab-printing #singleTabPrintArea{
   display:block!important;
   position:static!important;
   width:100%!important;
   margin:0!important;
   padding:0!important;
   background:#fff!important;
   color:#111!important;
 }
 body.single-tab-printing #singleTabPrintArea .tab-print-btn,
 body.single-tab-printing #singleTabPrintArea button{
   display:none!important;
 }
 body.single-tab-printing #singleTabPrintArea .panel{
   display:block!important;
   visibility:visible!important;
   position:static!important;
   width:100%!important;
   height:auto!important;
   overflow:visible!important;
   box-shadow:none!important;
   border:none!important;
   margin:0!important;
 }
 body.single-tab-printing #singleTabPrintArea .card,
 body.single-tab-printing #singleTabPrintArea .result,
 body.single-tab-printing #singleTabPrintArea article{
   break-inside:avoid;
   page-break-inside:avoid;
 }
 body.single-tab-printing #singleTabPrintArea input,
 body.single-tab-printing #singleTabPrintArea select,
 body.single-tab-printing #singleTabPrintArea textarea{
   border:1px solid #aaa!important;
   background:#fff!important;
   color:#111!important;
 }
}
</style>


<style id="definitive-print-css">
#printSelectedTabOnly{display:none}
@media print{
  /* Impressão INDIVIDUAL: somente a aba selecionada */
  html.print-selected-tab body > *:not(#printSelectedTabOnly){display:none!important}
  html.print-selected-tab #printSelectedTabOnly{
    display:block!important;visibility:visible!important;position:static!important;
    width:100%!important;height:auto!important;margin:0!important;padding:0!important;
    background:#fff!important;color:#111!important;
  }
  html.print-selected-tab #printSelectedTabOnly .panel,
  html.print-selected-tab #printSelectedTabOnly section,
  html.print-selected-tab #printSelectedTabOnly article,
  html.print-selected-tab #printSelectedTabOnly .card,
  html.print-selected-tab #printSelectedTabOnly .result{
    display:block!important;visibility:visible!important;height:auto!important;
    overflow:visible!important;opacity:1!important;
  }
  html.print-selected-tab #printSelectedTabOnly button,
  html.print-selected-tab #printSelectedTabOnly .tab-print-btn{
    display:none!important;
  }
  html.print-selected-tab #printSelectedTabOnly .card,
  html.print-selected-tab #printSelectedTabOnly article,
  html.print-selected-tab #printSelectedTabOnly .result{
    break-inside:avoid;page-break-inside:avoid;
  }
}
</style>


<style id="tab-table-print-css">
#tabTablePrint{display:none}
@media print{
 html.print-tab-table body > *:not(#tabTablePrint){display:none!important}
 html.print-tab-table #tabTablePrint{
   display:block!important;width:100%!important;margin:0!important;padding:0!important;
   background:#fff!important;color:#111!important;font-family:Arial,sans-serif!important
 }
 #tabTablePrint h1{font-size:18px;margin:0 0 5px}
 #tabTablePrint .pt-meta{font-size:10px;color:#52677a;margin-bottom:12px}
 #tabTablePrint table{width:100%;border-collapse:collapse;font-size:10px}
 #tabTablePrint th{background:#edf5fa;border:1px solid #9fb8c8;padding:7px;text-align:left}
 #tabTablePrint td{border:1px solid #b9c9d3;padding:7px;vertical-align:top;line-height:1.35}
 #tabTablePrint tr{break-inside:avoid;page-break-inside:avoid}
 #tabTablePrint .pt-footer{margin-top:12px;font-size:8.5px;color:#607586;border-top:1px solid #ccd9e1;padding-top:7px}
}
</style>


<style id="score-description-final-css">
.score-purpose-final{display:block;margin:3px 0 8px;color:#60798c;font-size:10px;line-height:1.35;font-weight:500}
</style>

</head>
<body>

<aside class="v10-sidebar">
  <div class="v10-brand"><div class="v10-pulse">⌁</div><div><b>Emergência Pediátrica</b><small>Calculadoras · Doses · Scores</small></div></div>
  <button class="v10-homebtn active" onclick="v10Home()">⌂ &nbsp; Início</button>
  <div class="v10-side-title">Módulos clínicos</div>
  <div id="v10TabsSlot"></div>
  <div class="v10-side-title">Documento</div>
  <button class="v10-printbtn" onclick="buildPrintTable();window.print()">▣ &nbsp; Impressão</button>
</aside>

<div class="v10-topbar">
  <div class="v10-top-title">Emergência <span>Pediátrica</span></div>
  <div class="v10-search"><input id="v10Search" placeholder="Buscar calculadora, droga, score ou condição..." oninput="v10SearchModules(this.value)"></div>
  <div class="v10-top-actions">
    <button onclick="document.querySelector('.v10-reference').scrollIntoView({behavior:'smooth'})">Referências</button>
    <button onclick="buildPrintTable();window.print()">Imprimir</button>
  </div>
</div>

<header><div class="wrap"><div class="brand"><div class="logo">P</div><div><div class="eyebrow">Emergência pediátrica</div><h1>Calculadora Pediátrica</h1><p>Doses, diluições, infusões e apoio à emergência.</p></div></div></div></header>
<main>

<section class="v10-dashboard" id="v10Dashboard">
  <div class="v10-hero">
    <div class="v10-kicker">Central de apoio à emergência pediátrica</div>
    <h2>Sua Central de Cálculos na <span>Emergência</span></h2>
    <p>Doses, diluições, infusões, ventilação, escalas e ferramentas práticas para o atendimento pediátrico.</p>
  </div>

  <div class="v10-trust">
    <div><b>✓ Apoio clínico</b>Ferramenta de auxílio e dupla checagem</div>
    <div><b>⚡ Rápido e prático</b>Peso e idade alimentam os cálculos</div>
    <div><b>⚠ Segurança</b>Limites, preparo e alertas destacados</div>
  </div>

  <div class="v10-disclaimer">
    <strong>AVISO DE USO:</strong> esta ferramenta é destinada ao <strong>apoio clínico, diagnóstico, cálculo e dupla checagem</strong>.
    Não substitui avaliação médica, julgamento clínico, protocolos institucionais, bula, prescrição médica ou diretrizes oficiais.
    Seus resultados <strong>não são mandatórios</strong> e devem ser interpretados individualmente pelo profissional habilitado,
    conforme o quadro clínico, disponibilidade local e regulamentações vigentes.
  </div>
<div style="font-weight:900;margin:8px 0 9px">⚡ Acesso rápido — principais emergências</div>
  <div class="v10-quick">
    <button onclick="v10Open('rsi')">IOT</button><button onclick="v10Open('pcr')">PCR</button>
    <button onclick="v10Open('sepse')">SEPSE</button><button onclick="v10Open('anafilaxia')">ANAFILAXIA</button>
    <button onclick="v10Open('convulsao')">CONVULSÃO</button><button onclick="v10Open('asma')">ASMA GRAVE</button>
    <button onclick="v10Open('antibioticos')">ANTIBIÓTICOS EV</button><button onclick="v10Open('queimaduras')">QUEIMADURAS</button><button onclick="v10Open('scores')">SCORES</button>
  </div>
</section>

<section class="inputs">
  <div class="field"><label>Peso — kg</label><input id="pesoKg" type="number" inputmode="numeric" min="0" step="1" placeholder="Ex.: 18" oninput="syncPaciente()"></div>
  <div class="field"><label>Peso — gramas</label><input id="pesoG" type="number" inputmode="numeric" min="0" max="999" step="1" placeholder="Ex.: 350" oninput="syncPaciente()"></div>
  <div class="field"><label>Idade — anos</label><input id="idadeAnos" type="number" inputmode="numeric" min="0" step="1" placeholder="Ex.: 6" oninput="syncPaciente()"></div>
  <div class="field"><label>Idade — meses</label><input id="idadeMeses" type="number" inputmode="numeric" min="0" max="11" step="1" placeholder="Ex.: 4" oninput="syncPaciente()"></div>
  <input id="peso" type="hidden"><input id="idade" type="hidden">
  <div class="actions"><button class="btn primary" onclick="calcular()">Calcular</button><button class="btn secondary" onclick="buildPrintTable();window.print()">Imprimir</button></div>
</section>

<div id="homeOnlyDashboard">
<div class="notice"><strong>Uso clínico:</strong> calculadora de apoio e dupla checagem. As doses foram atualizadas com base em AHA/AAP PALS 2025 e guias pediátricos de emergência (RCH Melbourne / Children’s Health Queensland). Antibióticos exigem adaptação ao protocolo local, foco infeccioso, alergias, função renal, culturas e epidemiologia.</div>


  <div class="v10-grid">

    <button class="v10-card" onclick="v10Open('rsi')"><span class="ico">🫁</span><b>Intubação / RSI</b><small>Doses, tubo, sequência rápida</small></button>
    <button class="v10-card" onclick="v10Open('anafilaxia')"><span class="ico">⚡</span><b>Anafilaxia</b><small>Adrenalina e suporte</small></button>
    <button class="v10-card" onclick="v10Open('asma')"><span class="ico">🌬️</span><b>Asma</b><small>Broncodilatadores e gravidade</small></button>
    <button class="v10-card" onclick="v10Open('sepse')"><span class="ico">🦠</span><b>Sepse</b><small>Fluidos, drogas e ceftriaxona/meningite</small></button>
    <button class="v10-card" onclick="v10Open('convulsao')"><span class="ico">🧠</span><b>Convulsão</b><small>Abortamento e segunda linha</small></button>
    <button class="v10-card" onclick="v10Open('antibioticos')"><span class="ico">💉</span><b>Antibióticos EV</b><small>Dose, reconstituição, diluição e tempo</small></button>
    <button class="v10-card" onclick="v10Open('corticoides')"><span class="ico">🧪</span><b>Corticoides</b><small>EV, IM e VO</small></button>
    <button class="v10-card" onclick="v10Open('antidotos')"><span class="ico">🧯</span><b>Antídotos</b><small>Flumazenil e naloxona com cálculo por peso</small></button>
    <button class="v10-card" onclick="v10Open('queimaduras')"><span class="ico">🔥</span><b>Queimaduras</b><small>SCQ interativa e plano de hidratação</small></button>
    <button class="v10-card" onclick="v10Open('glicemia')"><span class="ico">🩸</span><b>Hipo / Hiperglicemia</b><small>Glicemia, glicose EV e avaliação de hiperglicemia</small></button>
    <button class="v10-card" onclick="v10Open('cad')"><span class="ico">🧬</span><b>Cetoacidose Diabética</b><small>Gasometria, hidratação, eletrólitos e BIC de insulina</small></button>
    <button class="v10-card" onclick="v10Open('desidratacao')"><span class="ico">💧</span><b>Desidratação — OMS</b><small>Classificação e Planos A, B e C</small></button>
    <button class="v10-card" onclick="v10Open('analgesia')"><span class="ico">💊</span><b>Analgesia</b><small>Analgésicos e antitérmicos</small></button>
    <button class="v10-card" onclick="v10Open('infusoes')"><span class="ico">💧</span><b>Infusões</b><small>Drogas e bombas de infusão</small></button>
    <button class="v10-card" onclick="v10Open('ventilacao')"><span class="ico">🫁</span><b>Ventilação Mecânica</b><small>Parâmetros e ajustes</small></button>
    <button class="v10-card" onclick="v10Open('scores')"><span class="ico">📋</span><b>Scores e Escalas</b><small>Campos interativos e resultado automático</small></button>
  </div>
</div>

  

<nav class="tabs">
<button class="tab" data-tab="pcr">PCR / Arritmias</button>
<button class="tab" data-tab="rsi">RSI / IOT</button>
<button class="tab" data-tab="anafilaxia">Anafilaxia</button>
<button class="tab" data-tab="asma">Asma</button>
<button class="tab" data-tab="sepse">Sepse</button>
<button class="tab" data-tab="convulsao">Crise convulsiva</button>
<button class="tab" data-tab="eletrolitos">Eletrólitos</button>
<button class="tab" data-tab="hidratacao">Hidratação</button>
<button class="tab" data-tab="glicemia">Hipo / Hiperglicemia</button>
<button class="tab" data-tab="cad">Cetoacidose Diabética — CAD</button>
<button class="tab" data-tab="desidratacao">Desidratação — OMS</button>
<button class="tab" data-tab="queimaduras">Queimaduras</button>
<button class="tab" data-tab="analgesia">Analgesia / Antitérmicos</button>
<button class="tab" data-tab="antiemeticos">Antieméticos</button>
<button class="tab" data-tab="sedacao">Sedação de procedimento</button>
<button class="tab" data-tab="antibioticos">Antibióticos EV</button>
<button class="tab" data-tab="corticoides">Corticoides</button>
<button class="tab" data-tab="antidotos">Antídotos</button>
<button class="tab" data-tab="ambulatoriais">Medicações ambulatoriais</button>
<button class="tab" data-tab="scores">Scores / Escalas</button>
<button class="tab" data-tab="infusoes">Infusões</button>
<button class="tab" data-tab="materiais">Materiais / Energia</button>
<button class="tab" data-tab="ventilacao">Ventilação Mecânica</button>
<button class="tab" data-tab="apresentacoes">Apresentações da UPA</button>
</nav>

<section id="pcr" class="panel">
 <div class="section-title"><h2>PCR, bradicardia e taquiarritmias</h2><span class="badge">PALS 2025</span></div>
 <div id="pcrCards" class="grid"></div>
</section>

<section id="rsi" class="panel">
 <div class="section-title"><h2>Sequência rápida de intubação</h2><span class="badge">RCH / CHQ</span></div>
 <div id="rsiCards" class="grid"></div>
</section>


<section id="anafilaxia" class="panel">
 <div class="section-title"><h2>Anafilaxia</h2><span class="badge">RCH / ASCIA</span></div>
 <div id="anaCards" class="grid"></div>
</section>

<section id="asma" class="panel">
 <div class="section-title"><h2>Asma aguda / broncoespasmo</h2><span class="badge">RCH</span></div>
 <div id="asmaCards" class="grid"></div>
</section>

<section id="sepse" class="panel">
 <div class="section-title"><h2>Sepse / choque séptico</h2><span class="badge">PALS 2025 / RCH</span></div>
 
<div class="pews-wrap">
  <div class="pews-title">PEWS — Deterioração clínica</div>
  <div class="pews-sub">
    Triagem baseada no conceito de Bedside PEWS, com parâmetros fisiológicos ajustados à idade.
    O escore auxilia reconhecimento de deterioração e não substitui avaliação clínica.
  </div>

  <div class="pews-grid">
    <div class="pews-field"><label>Frequência cardíaca (bpm)</label><input id="pewsHR" type="number" min="0" oninput="calcPEWS()"></div>
    <div class="pews-field"><label>Frequência respiratória (irpm)</label><input id="pewsRR" type="number" min="0" oninput="calcPEWS()"></div>
    <div class="pews-field"><label>SpO₂ (%)</label><input id="pewsSat" type="number" min="0" max="100" oninput="calcPEWS()"></div>
    <div class="pews-field"><label>Pressão sistólica (mmHg)</label><input id="pewsSBP" type="number" min="0" oninput="calcPEWS()"></div>
    <div class="pews-field"><label>Temperatura (°C)</label><input id="pewsTemp" type="number" step="0.1" oninput="calcPEWS()"></div>
    <div class="pews-field"><label>Enchimento capilar</label>
      <select id="pewsCRT" onchange="calcPEWS()">
        <option value="0">1–2 s</option><option value="1">3 s</option><option value="2">4 s</option><option value="3">≥5 s</option>
      </select>
    </div>
    <div class="pews-field"><label>Consciência / comportamento</label>
      <select id="pewsMental" onchange="calcPEWS()">
        <option value="0">Alerta / brincando / habitual</option>
        <option value="1">Irritável, mas consolável</option>
        <option value="2">Agitado ou sonolento / difícil consolar</option>
        <option value="3">Letárgico, confuso ou resposta reduzida</option>
      </select>
    </div>
    <div class="pews-field"><label>Esforço respiratório</label>
      <select id="pewsWork" onchange="calcPEWS()">
        <option value="0">Sem retrações</option>
        <option value="1">Leve / retração discreta</option>
        <option value="2">Uso de musculatura acessória</option>
        <option value="3">Exaustão / esforço grave / apneia</option>
      </select>
    </div>
    <div class="pews-field"><label>Oxigênio suplementar</label>
      <select id="pewsO2" onchange="calcPEWS()">
        <option value="0">Ar ambiente</option>
        <option value="1">O₂ baixo fluxo / iniciado</option>
        <option value="2">O₂ ≥2 L/min ou necessidade crescente</option>
        <option value="3">FiO₂ ≥50% / suporte avançado</option>
      </select>
    </div>
  </div>

  <div id="pewsResult" class="pews-result low">
    <div class="pews-score">PEWS 0</div>
    <div class="pews-risk">BAIXO RISCO</div>
    <div class="pews-guidance">Manter monitorização e reavaliar conforme quadro clínico.</div>
  </div>
</div>
<div id="sepseCards" class="grid"></div>
</section>

<section id="eletrolitos" class="panel">
 <div class="section-title"><h2>Distúrbios eletrolíticos</h2><span class="badge">RCH / CREDD</span></div>
 <div id="electCards" class="grid"></div>
</section>

<section id="convulsao" class="panel">
 <div class="section-title"><h2>Crise convulsiva / status</h2><span class="badge">RCH</span></div>
 <div id="convCards" class="grid"></div>
</section>

<section id="hidratacao" class="panel">
 <div class="section-title"><h2>Plano de hidratação</h2><span class="badge">RCH 2026</span></div>
 <div id="fluidCards" class="grid"></div>
</section>



<section id="glicemia" class="panel">
 <h2>Hipo / Hiperglicemia</h2>
 <div class="notice">Ferramenta de triagem e apoio terapêutico. Hiperglicemia em pediatria exige interpretação com quadro clínico, cetonas, gasometria, eletrólitos e investigação de CAD quando aplicável.</div>
 <div class="grid">
  <div class="field"><label>Glicemia (mg/dL)</label><input id="glyValue" type="number" min="0" step="1" placeholder="Ex.: 48"></div>
  <div class="field"><label>Estado clínico</label><select id="glyState"><option value="able">Consciente e consegue deglutir</option><option value="severe">Alteração importante / convulsão / não deglute</option></select></div>
  <div class="field"><label>Cetonas / suspeita de CAD</label><select id="glyKet"><option value="unknown">Não avaliado</option><option value="no">Negativas / sem suspeita</option><option value="yes">Positivas ou suspeita clínica</option></select></div>
 </div>
 <button class="btn primary" type="button" onclick="glyCalculate()">Avaliar glicemia</button>
 <div id="glyResult" class="result" style="margin-top:12px">Informe a glicemia e o peso do paciente.</div>
 <div class="gly-info">
  <div><b>Hipoglicemia</b><br>&lt;70 mg/dL = valor de alerta. &lt;54 mg/dL = hipoglicemia clinicamente importante. Se grave e acesso EV disponível: SG 10% 2 mL/kg (0,2 g/kg), administrado ao longo de alguns minutos, com rechecagem.</div>
  <div><b>Hiperglicemia</b><br>Não gerar automaticamente bolus de insulina. Avaliar hidratação, cetonemia/cetonúria, pH/bicarbonato, Na/K e critérios de CAD. Se CAD, seguir o módulo/protocolo específico.</div>
 </div>
</section>


<section id="cad" class="panel">
 <h2>Cetoacidose Diabética — CAD Pediátrica</h2>
 <div class="notice"><strong>Apoio clínico estruturado.</strong> O módulo integra diagnóstico, gasometria, sódio corrigido, ânion gap, fluidos, eletrólitos, glicose e infusão de insulina. Não iniciar insulina em bolus. Confirmar CAD e reavaliar clínica e laboratorialmente durante todo o tratamento.</div>

 <div class="cad-step"><h3>1. Diagnóstico e gasometria</h3>
  <div class="cad-inputs">
   <div class="field"><label>Glicemia mg/dL</label><input id="cadGlu" type="number" step="1"></div>
   <div class="field"><label>pH</label><input id="cadPH" type="number" step="0.01"></div>
   <div class="field"><label>pCO₂ mmHg</label><input id="cadPCO2" type="number" step="0.1"></div>
   <div class="field"><label>HCO₃⁻ mmol/L</label><input id="cadHCO3" type="number" step="0.1"></div>
   <div class="field"><label>Na⁺ mmol/L</label><input id="cadNa" type="number" step="0.1"></div>
   <div class="field"><label>K⁺ mmol/L</label><input id="cadK" type="number" step="0.1"></div>
   <div class="field"><label>Cl⁻ mmol/L</label><input id="cadCl" type="number" step="0.1"></div>
   <div class="field"><label>β-hidroxibutirato mmol/L</label><input id="cadBHB" type="number" step="0.1" placeholder="se disponível"></div>
   <div class="field cad-ketosis-field"><label>Cetose confirmada</label><label class="cad-checkline"><input id="cadKetosisConfirmed" type="checkbox"> Sim — cetonemia/cetonúria confirmada</label></div>
   <div class="field"><label>Ureia mg/dL</label><input id="cadUrea" type="number" step="0.1"></div>
   <div class="field"><label>Creatinina mg/dL</label><input id="cadCr" type="number" step="0.01"></div>
   <div class="field"><label>Mg mmol/L</label><input id="cadMg" type="number" step="0.01"></div>
   <div class="field"><label>Fósforo mmol/L</label><input id="cadP" type="number" step="0.01"></div>
  </div>
  <button class="btn primary" type="button" onclick="cadCalculate()">Analisar CAD e montar plano</button>
  <div id="cadDx" class="result">Preencha os dados acima.</div>
 </div>

 <div class="cad-step"><h3>2. Hidratação</h3>
  <div class="cad-inputs">
   <div class="field"><label>Bolus isotônico já realizado (mL)</label><input id="cadBolusGiven" type="number" value="0" min="0"></div>
   <div class="field"><label>Horas desde início dos fluidos</label><input id="cadFluidHours" type="number" value="0" min="0" step=".25"></div>
   <div class="field"><label>Estratégia de fluido</label><select id="cadFluidMode"><option value="cps">CPS/TREKK — déficit 10% em 36 h</option><option value="double">Temporário — 2× manutenção até cálculo detalhado</option></select></div>
  </div>
  <div id="cadFluids" class="result">O plano será calculado após a análise.</div>
 </div>

 <div class="cad-step"><h3>3. Eletrólitos e glicose</h3>
  <div id="cadElectrolytes" class="result">Informe Na, K, Cl, glicemia e demais eletrólitos disponíveis.</div>
  <div class="cad-two-bag">
   <div class="field"><label>Sistema de duas bolsas — glicose desejada</label>
    <select id="cadDex" onchange="cadTwoBag()"><option value="0">Sem glicose</option><option value="5">D5</option><option value="7.5">D7,5</option><option value="10">D10</option><option value="12.5">D12,5</option></select>
   </div>
   <div id="cadBagResult" class="result">A taxa total será usada para calcular as duas bolsas.</div>
  </div>
 </div>

 <div class="cad-step"><h3>4. Bomba de insulina</h3>
  <div class="cad-inputs">
   <div class="field"><label>Dose</label><select id="cadInsDose" onchange="cadInsulin()"><option value=".05">0,05 UI/kg/h</option><option value=".1">0,1 UI/kg/h</option></select></div>
   <div class="field"><label>Concentração preparada</label><select id="cadInsConc" onchange="cadInsulin()"><option value="1">1 UI/mL</option><option value=".5">0,5 UI/mL</option><option value=".1">0,1 UI/mL</option></select></div>
  </div>
  <div id="cadInsulinResult" class="result">A insulina só deve ser iniciada após ≥1 hora de fluido e com K⁺ &gt;3,0 mmol/L. Nunca realizar bolus IV.</div>
  <div class="cad-dilutions">
   <h4>Diluições práticas — CAD</h4>
   <div class="cad-dil-grid">
    <div><b>Insulina regular — padrão 1 UI/mL</b><br>Preparar <strong>50 UI de insulina regular + SF 0,9% até 50 mL</strong> → concentração final 1 UI/mL. Homogeneizar e <strong>preencher/flushar o equipo com a própria solução de insulina antes de conectar ao paciente</strong>. Administrar em BIC. Ex.: 0,05 UI/kg/h corresponde numericamente a 0,05 mL/kg/h nesta concentração.</div>
    <div><b>Bolsa 1 — sem glicose</b><br>SF 0,9%, Ringer lactato ou cristaloide balanceado + <strong>KCl 40 mmol/L</strong> quando K &lt;5 mmol/L e diurese recente estiver documentada. Esta bolsa e a bolsa com glicose devem conter os <strong>mesmos eletrólitos</strong>.</div>
    <div><b>Bolsa 2 — D12,5%</b><br>Mesma solução/eletrolitos da Bolsa 1, porém com <strong>dextrose 12,5%</strong>. A calculadora abaixo divide automaticamente as taxas das duas bolsas para gerar D5, D7,5, D10 ou D12,5 no débito total.</div>
    <div><b>Se a unidade utilizar apenas D10%</b><br>Para concentração final D5: Bolsa 1 = 50% do débito + Bolsa D10 = 50%. Para D7,5: Bolsa 1 = 25% + Bolsa D10 = 75%. Concentrações/preparo da bolsa devem ser validados com Farmácia e padronização institucional.</div>
    <div><b>Potássio</b><br>Diretriz: adicionar pelo menos <strong>40 mmol/L</strong> quando K &lt;5 mmol/L e houver diurese recente. A forma de sal (KCl, fosfato/acetato) e o preparo físico da bolsa dependem das apresentações e protocolo institucional; não converter mmol em mL sem confirmar a concentração disponível.</div>
    <div><b>NaCl 3% — suspeita de lesão cerebral</b><br>Dose calculada no bloco neurológico: <strong>5 mL/kg (máx. 250 mL) em 10–15 min</strong>. Não é solução de manutenção da CAD.</div>
   </div>
   <div class="notice" style="margin-top:10px"><strong>Segurança:</strong> as diluições acima expressam concentrações-alvo e método descritos nas referências. Para preparo em mL de eletrólitos ou dextrose concentrada, a calculadora não deve assumir a apresentação disponível na unidade; conferir rótulo, Farmácia e protocolo institucional.</div>
  </div>
 </div>

 <div class="cad-step cad-danger"><h3>5. Lesão cerebral — vigilância ativa</h3>
  <div class="cad-neuro">
   <label><input type="checkbox" class="cad-neuro-ck"> Alteração/redução do nível de consciência</label>
   <label><input type="checkbox" class="cad-neuro-ck"> Cefaleia progressiva/importante</label>
   <label><input type="checkbox" class="cad-neuro-ck"> Vômitos</label>
   <label><input type="checkbox" class="cad-neuro-ck"> Bradicardia</label>
   <label><input type="checkbox" class="cad-neuro-ck"> Hipertensão</label>
   <label><input type="checkbox" class="cad-neuro-ck"> Depressão respiratória/dessaturação</label>
  </div>
  <button class="btn primary" type="button" onclick="cadNeuro()">Avaliar sinais neurológicos</button>
  <div id="cadNeuroResult" class="result">Monitorar estado neurológico frequentemente.</div>
 </div>

 <div class="cad-step"><h3>6. Monitorização seriada</h3>
  <div class="cad-monitor"><b>Glicemia:</b> horária &nbsp; • &nbsp; <b>Eletrólitos/gasometria:</b> pelo menos a cada 2 h durante a infusão de insulina &nbsp; • &nbsp; <b>Contínuo:</b> estado neurológico, perfusão, balanço hídrico e diurese.</div>
 </div>
</section>
<section id="desidratacao" class="panel">
 <h2>Desidratação — classificação OMS</h2>
 <div class="notice">Marque os achados clínicos. A classificação abaixo segue a lógica OMS/IMCI: dois ou mais sinais da mesma categoria definem o respectivo grau, priorizando a categoria de maior gravidade.</div>
 <div class="dehyd-grid">
  <div class="dehyd-card"><h3>Estado geral</h3>
   <label><input type="radio" name="dh_general" value="0" checked> Bem / alerta</label>
   <label><input type="radio" name="dh_general" value="1"> Inquieto / irritável</label>
   <label><input type="radio" name="dh_general" value="2"> Letárgico ou inconsciente</label>
  </div>
  <div class="dehyd-card"><h3>Olhos</h3>
   <label><input type="radio" name="dh_eyes" value="0" checked> Normais</label>
   <label><input type="radio" name="dh_eyes" value="1"> Fundos</label>
   <label><input type="radio" name="dh_eyes" value="2"> Muito fundos</label>
  </div>
  <div class="dehyd-card"><h3>Sede / ingestão</h3>
   <label><input type="radio" name="dh_thirst" value="0" checked> Bebe normalmente / sem sede</label>
   <label><input type="radio" name="dh_thirst" value="1"> Sedento, bebe avidamente</label>
   <label><input type="radio" name="dh_thirst" value="2"> Não consegue beber / bebe mal</label>
  </div>
  <div class="dehyd-card"><h3>Pregueamento cutâneo</h3>
   <label><input type="radio" name="dh_skin" value="0" checked> Retorna imediatamente</label>
   <label><input type="radio" name="dh_skin" value="1"> Retorna lentamente</label>
   <label><input type="radio" name="dh_skin" value="2"> Retorna muito lentamente</label>
  </div>
 </div>
 <button class="btn primary" type="button" onclick="dehydCalculate()">Classificar e calcular plano</button>
 <div id="dehydResult" class="result" style="margin-top:12px">Selecione os achados e calcule.</div>
 <div class="dehyd-plans">
  <div><b>PLANO A — sem desidratação</b><br>Prevenção/tratamento domiciliar, líquidos adicionais, SRO após perdas, alimentação e orientação de sinais de alarme.</div>
  <div><b>PLANO B — alguma desidratação</b><br>SRO <strong>75 mL/kg em 4 h</strong>, por VO/SNG, com reavaliação após 4 h.</div>
  <div><b>PLANO C — desidratação grave</b><br><strong>100 mL/kg</strong> de Ringer lactato (ou SF 0,9% se indisponível): &lt;12 meses, 30 mL/kg em 1 h + 70 mL/kg em 5 h; ≥12 meses, 30 mL/kg em 30 min + 70 mL/kg em 2,5 h. Reavaliar frequentemente.</div>
 </div>
</section>
<section id="queimaduras" class="panel">
  <h2>Queimaduras — SCQ e Hidratação</h2>
  <div class="notice">
    <strong>Apoio à estimativa:</strong> não incluir eritema/queimadura exclusivamente epidérmica no cálculo da SCQ.
    Em pediatria, Lund &amp; Browder é o método preferencial para maior precisão. Esta tela permite seleção rápida por regiões e ajuste manual da porcentagem de cada área.
  </div>

  <div class="burn-layout">
    <div class="burn-box">
      <h3>1. Superfície corporal queimada (SCQ)</h3>
      <p class="muted">Marque somente as regiões atingidas. A calculadora atribui automaticamente a porcentagem de SCQ de cada região conforme a idade informada no cabeçalho e soma o total.</p>
      <div class="burn-regions" id="burnRegions">
        <label><input type="checkbox" class="burn-check" data-region="cabeca"> Cabeça + pescoço <span class="burn-auto" data-for="cabeca">—</span></label>
        <label><input type="checkbox" class="burn-check" data-region="troncoAnt"> Tronco anterior <span class="burn-auto" data-for="troncoAnt">18%</span></label>
        <label><input type="checkbox" class="burn-check" data-region="troncoPost"> Tronco posterior <span class="burn-auto" data-for="troncoPost">18%</span></label>
        <label><input type="checkbox" class="burn-check" data-region="msd"> Membro superior direito <span class="burn-auto" data-for="msd">9%</span></label>
        <label><input type="checkbox" class="burn-check" data-region="mse"> Membro superior esquerdo <span class="burn-auto" data-for="mse">9%</span></label>
        <label><input type="checkbox" class="burn-check" data-region="mid"> Membro inferior direito <span class="burn-auto" data-for="mid">—</span></label>
        <label><input type="checkbox" class="burn-check" data-region="mie"> Membro inferior esquerdo <span class="burn-auto" data-for="mie">—</span></label>
        <label><input type="checkbox" class="burn-check" data-region="perineo"> Períneo/genitália <span class="burn-auto" data-for="perineo">—</span></label>
      </div>
      <div class="burn-total">SCQ total estimada: <strong id="burnTBSA">0%</strong></div>
      <div class="burn-actions">
        <button class="btn secondary" type="button" onclick="burnClear()">Limpar áreas</button>
      </div>
      <div class="notice" style="margin-top:12px">
        <strong>Importante:</strong> esta seleção rápida considera a região marcada como totalmente queimada. Para queimaduras parciais/irregulares, usar Lund &amp; Browder detalhado ou método palmar. A palma + dedos do próprio paciente corresponde aproximadamente a 1% da SCQ.
      </div>
    </div>

    <div class="burn-box">
      <h3>2. Plano inicial de hidratação</h3>
      <div class="grid">
        <div class="field"><label>Horas desde a queimadura</label><input id="burnHours" type="number" min="0" max="24" step="0.25" value="0"></div>
        <div class="field"><label>Volume EV já administrado (mL)</label><input id="burnGiven" type="number" min="0" step="1" value="0"></div>
      </div>
      <button class="btn primary" type="button" onclick="burnCalculate()">Calcular plano</button>
      <div id="burnResult" class="result" style="margin-top:12px">Informe peso no cabeçalho, selecione a SCQ e clique em calcular.</div>
    </div>
  </div>

  <div class="burn-alerts">
    <div><strong>🔥 Ressuscitação EV:</strong> considerar em queimaduras &gt;10% SCQ. Fórmula de Parkland modificada pediátrica usada nesta ferramenta: <strong>3 mL × kg × %SCQ</strong> nas primeiras 24 h, metade nas primeiras 8 h a partir do momento da queimadura e metade nas 16 h seguintes.</div>
    <div><strong>💧 Manutenção:</strong> calculada separadamente pela regra 4–2–1. Em crianças pequenas, a manutenção com glicose deve ser considerada conforme contexto clínico e protocolo local.</div>
    <div><strong>🎯 Meta de diurese:</strong> 1 mL/kg/h como alvo pediátrico inicial para ajuste da ressuscitação.</div>
    <div><strong>⚠️ Encaminhamento/especialista:</strong> considerar avaliação especializada em queimaduras complexas, áreas especiais, lesão inalatória, circunferencial, química/elétrica, trauma associado, lactentes e outros critérios locais.</div>
  </div>
</section>

<section id="analgesia" class="panel">
 <div class="section-title"><h2>Analgesia, antitérmicos e anti-inflamatório</h2><span class="badge">RCH</span></div>
 <div id="painCards" class="grid"></div>
</section>


<section id="antiemeticos" class="panel">
 <div class="section-title"><h2>Antieméticos</h2><span class="badge">RCH</span></div>
 <div id="antiemCards" class="grid"></div>
</section>

<section id="sedacao" class="panel">
 <div class="section-title"><h2>Sedação de procedimento</h2><span class="badge">RCH</span></div>
 <div id="sedCards" class="grid"></div>
</section>

<section id="antibioticos" class="panel">
 <div class="section-title"><h2>Antibióticos EV — cálculo por peso</h2><span class="badge">Manual Farmacoterapêutico UPA</span></div>
 <div class="calcbox"><h3>Selecione o antimicrobiano</h3><div class="row"><div><div class="mini">Medicamento</div><select id="abxDrug" onchange="calcNovasAbas()">
 <option value="ampicilina">Ampicilina 1 g</option><option value="azitromicina">Azitromicina 500 mg</option><option value="cefazolina">Cefazolina 1 g</option><option value="ceftriaxona">Ceftriaxona 1 g</option><option value="metronidazol">Metronidazol 5 mg/mL</option><option value="oxacilina">Oxacilina 500 mg</option><option value="piptazo">Piperacilina + tazobactam 4,5 g</option>
 </select></div><div><div class="mini">Dose selecionada</div><select id="abxDoseSelect" onchange="calcNovasAbas()"></select></div></div></div>
 <div class="notice"><strong>Sem diagnóstico:</strong> esta aba calcula a dose pelo peso. Para fármacos cuja dose é expressa em mg/kg/dia, escolha a intensidade/faixa prescrita e confirme intervalo, foco, função renal, alergias e protocolo clínico antes da administração.</div>
 <div id="abxNewCards" class="grid"></div>
</section>

<section id="corticoides" class="panel">
 <div class="section-title"><h2>Corticoides</h2><span class="badge">Manual Farmacoterapêutico UPA</span></div>
 <div id="cortCards" class="grid"></div>
</section>


<section id="antidotos" class="panel">
 <h2>Antídotos</h2>
 <div class="notice">Cálculos baseados no Manual Farmacoterapêutico institucional. Uso como apoio clínico e dupla checagem; confirmar indicação, contexto da intoxicação, contraindicações e monitorização.</div>
 <div class="grid" id="antidotoCards"></div>
</section>

<section id="ambulatoriais" class="panel">
 <div class="section-title"><h2>Medicações ambulatoriais pediátricas</h2><span class="badge">REMUME 2026</span></div>
 <div class="notice"><strong>Apresentações disponíveis:</strong> volumes são calculados exclusivamente para as concentrações listadas na REMUME enviada. A indicação, duração e intervalo devem ser confirmados conforme diagnóstico e protocolo.</div>
 <div id="ambCards" class="grid"></div>
</section>

<section id="scores" class="panel">
 <div class="section-title"><h2>Scores, escalas e regras de decisão</h2><span class="badge">Cálculo interativo</span></div>
 <div class="notice"><strong>Como usar:</strong> marque uma opção em cada critério. O resultado é atualizado automaticamente. Regras de decisão devem ser interpretadas no contexto clínico.</div>
 <div id="scoreCalculators"></div>
</section>

<section id="infusoes" class="panel">
 <div class="section-title"><h2>Infusões contínuas</h2><span class="badge">peso → preparo → bomba</span></div>
 <div class="quickbar">
   <button class="quickdrug active" data-inf="midazolam">Mida</button>
   <button class="quickdrug" data-inf="fentanil">Fenta</button>
   <button class="quickdrug" data-inf="epinefrina">Adrena</button>
   <button class="quickdrug" data-inf="norepinefrina">Nora</button>
   <button class="quickdrug" data-inf="dopamina">Dopa</button>
   <button class="quickdrug" data-inf="dobutamina">Dobuta</button>
   <button class="quickdrug" data-inf="rocuronio">Rocu</button>
 </div>
 <div class="notice"><strong>Compensação do equipo da BIC:</strong> o equipo da unidade retém 20 mL. A calculadora acrescenta esse volume ao preparo, mantendo a mesma concentração. <strong>A dose e a velocidade em mL/h não mudam.</strong></div><div id="infFocus"></div>
 <div class="summary">
   <h3>Resumo para evolução</h3>
   <pre id="infSummary">Informe o peso e selecione a medicação.</pre>
   <button class="btn secondary" onclick="copyInfSummary()">Copiar evolução</button>
 </div>
 <div id="infCards" style="display:none"></div>
</section>

<section id="materiais" class="panel">
 <div class="section-title"><h2>Materiais sugeridos</h2><span class="badge">peso / idade</span></div>
 <div class="notice"><strong>Via aérea:</strong> TOT calculado conforme o esquema institucional. Para máscara laríngea/dispositivo supraglótico, o tamanho é sugerido pelo peso: nº 1 &lt;5 kg; 1,5 = 5–10 kg; 2 = 10–20 kg; 2,5 = 20–30 kg; 3 = 30–50 kg; 4 = 50–70 kg; 5 = 70–100 kg; 6 &gt;100 kg. A máscara laríngea é uma opção de via aérea supraglótica/resgate; confirmar limites do fabricante do dispositivo disponível.</div><div id="equip" class="equipment"></div>
 <div class="section-title"><h2>Energia elétrica</h2><span class="badge">PALS 2025</span></div>
 <div id="energia" class="energy"></div>
</section>


<section id="ventilacao" class="panel">
 <div class="section-title"><h2>Ventilação Mecânica Pediátrica / Neonatal</h2><span class="badge">parâmetros iniciais</span></div>
 <div class="notice">
   Parâmetros iniciais de apoio. Devem ser titulados imediatamente conforme doença de base, mecânica respiratória, SpO₂, capnografia, gasometria e resposta clínica.
   Em obesidade, considere peso ideal/altura para definição do volume corrente.
 </div>

 <div class="calcbox">
   <h3>Configuração inicial</h3>
   <div class="row">
     <div><div class="mini">Grupo</div>
       <select id="vmGrupo" onchange="calcVM()">
         <option value="neo">Neonato</option>
         <option value="lactente">Lactente</option>
         <option value="crianca" selected>Criança</option>
         <option value="adolescente">Adolescente</option>
       </select>
     </div>
     <div><div class="mini">Modo</div>
       <select id="vmModo" onchange="calcVM()">
         <option value="VCV" selected>VCV</option>
         <option value="PCV">PCV</option>
       </select>
     </div>
     <div><div class="mini">Cenário</div>
       <select id="vmCenario" onchange="calcVM()">
         <option value="normal" selected>Pulmão sem SDRA</option>
         <option value="sdra">SDRA / hipoxemia</option>
         <option value="asma">Asma / obstrução</option>
       </select>
     </div>
   </div>
 </div>

 <div id="vmCards" class="grid"></div>

 <div class="calcbox" style="margin-top:10px">
   <h3>Monitorização ventilatória</h3>
   <div class="row">
     <div><div class="mini">PaO₂ (mmHg)</div><input id="vmPaO2" type="number" step="1" placeholder="Ex.: 90" oninput="calcVM()"></div>
     <div><div class="mini">FiO₂ atual (%)</div><input id="vmFiO2" type="number" step="1" min="21" max="100" value="100" oninput="calcVM()"></div>
     <div><div class="mini">Pplat (cmH₂O)</div><input id="vmPplat" type="number" step="1" placeholder="Ex.: 24" oninput="calcVM()"></div>
     <div><div class="mini">PEEP medida (cmH₂O)</div><input id="vmPeepMed" type="number" step="1" value="5" oninput="calcVM()"></div>
   </div>
   <div id="vmMonitor" class="grid" style="margin-top:8px"></div>
 </div>

 <div class="summary">
   <h3>Texto para evolução</h3>
   <pre id="vmSummary">Informe o peso e selecione os parâmetros.</pre>
   <button class="btn secondary" onclick="copyVMSummary()">Copiar evolução ventilatória</button>
 </div>
</section>

<section id="apresentacoes" class="panel">
 <div class="section-title"><h2>Apresentações da UPA</h2><span class="badge">configuração institucional</span></div>
 <div class="notice">
   Configure as concentrações realmente disponíveis na unidade. Os cálculos em mL serão atualizados automaticamente nas abas compatíveis.
   Os valores ficam salvos neste navegador.
 </div>
 <div class="grid" id="presCards">
   <article class="card"><div class="drug">Sedação / RSI</div>
     <div class="rx">
       <label>Midazolam (mg/mL)</label><input id="c_midazolam" type="number" step="0.1" value="5"><br><br>
       <label>Fentanil (mcg/mL)</label><input id="c_fentanil" type="number" step="1" value="50"><br><br>
       <label>Cetamina (mg/mL)</label><input id="c_cetamina" type="number" step="1" value="50"><br><br>
       <label>Rocurônio (mg/mL)</label><input id="c_rocuronio" type="number" step="1" value="10"><br><br>
       <label>Succinilcolina (mg/mL)</label><input id="c_succ" type="number" step="1" value="10"><br><br><label>Etomidato (mg/mL)</label><input id="c_etomidato" type="number" step="0.5" value="2">
     </div>
   </article>
   <article class="card"><div class="drug">PCR / Arritmias</div>
     <div class="rx">
       <label>Epinefrina PCR (mg/mL)</label><input id="c_epi_pcr" type="number" step="0.01" value="0.1"><br><br>
       <label>Epinefrina IM anafilaxia (mg/mL)</label><input id="c_epi_im" type="number" step="0.1" value="1"><br><br>
       <label>Atropina apresentação 1 (mg/mL)</label><input id="c_atropina" type="number" step="0.05" value="0.5"><br><br><label>Atropina apresentação 2 (mg/mL)</label><input id="c_atropina2" type="number" step="0.05" value="0.25"><br><br>
       <label>Adenosina (mg/mL)</label><input id="c_adenosina" type="number" step="0.1" value="3"><br><br>
       <label>Amiodarona (mg/mL)</label><input id="c_amiodarona" type="number" step="1" value="50">
     </div>
   </article>
   <article class="card"><div class="drug">Analgesia / Antitérmicos / Antiemético</div>
     <div class="rx">
       <label>Paracetamol solução VO (mg/mL)</label><input id="c_paracetamol_vo" type="number" step="1" value="200"><br><br>
       <label>Ibuprofeno suspensão (mg/mL)</label><input id="c_ibuprofeno" type="number" step="1" value="20"><br><br>
       <label>Dipirona gotas/VO (mg/mL)</label><input id="c_dipirona_vo" type="number" step="10" value="500"><br><br><label>Dipirona IM/EV (mg/mL)</label><input id="c_dipirona" type="number" step="10" value="500"><br><br>
       <label>Morfina (mg/mL)</label><input id="c_morfina" type="number" step="0.1" value="10"><br><br>
       <label>Ondansetrona (mg/mL)</label><input id="c_ondansetrona" type="number" step="0.1" value="2"><br><br><label>Metoclopramida (mg/mL)</label><input id="c_metoclopramida" type="number" step="0.1" value="5"><br><br><label>Bromoprida gotas VO (mg/mL)</label><input id="c_bromoprida" type="number" step="0.1" value="4">
     </div>
   </article>
   <article class="card"><div class="drug">Antibióticos</div>
     <div class="rx">
       <label>Amoxicilina suspensão (mg/mL)</label><input id="c_amoxicilina" type="number" step="1" value="50"><br><br>
       <label>Cefalexina suspensão (mg/mL)</label><input id="c_cefalexina" type="number" step="1" value="50"><br><br>
       <label>Ceftriaxona frasco (mg por frasco)</label><input id="c_ceftriaxona_vial" type="number" step="250" value="1000"><br><br>
       <label>Cefazolina frasco (mg por frasco)</label><input id="c_cefazolina_vial" type="number" step="250" value="1000"><br><br>
       <label>Azitromicina VO (mg por comprimido)</label><input id="c_azitro_vo" type="number" step="250" value="500"><br><br>
       <label>Azitromicina EV (mg por frasco)</label><input id="c_azitro_ev" type="number" step="250" value="500">
     </div>
   </article>
 </div>
 <div class="actions" style="margin-top:12px">
   <button class="btn primary" onclick="savePres()">Salvar apresentações</button>
   <button class="btn secondary" onclick="resetPres()">Restaurar padrão</button>
 </div>
</section>

<div class="footer">
Referências principais (revisão V8): American Heart Association/American Academy of Pediatrics — Pediatric Advanced Life Support 2025; Royal Children’s Hospital Melbourne Clinical Practice Guidelines (anafilaxia, asma, sepse, IV fluids, seizures, pain, vômitos, antimicrobianos, hipercalemia, sedação e via aérea); Hospital Sírio-Libanês Guia Farmacêutico (dipirona e azitromicina); Children’s Health Queensland / CREDD para preparo e doses de emergência. Sempre validar concentrações disponíveis na instituição.
</div>

<section class="v10-reference">
  <strong>Criação e responsabilidade editorial:</strong> Dra. Eduarda Kohakoski — Médica — CRM-PR 55.082.<br>
  <strong>Finalidade:</strong> ferramenta independente de apoio clínico e dupla checagem para uso por profissionais habilitados.
  Não constitui protocolo obrigatório, ordem médica automatizada ou substituto do julgamento profissional.
  A conduta final deve observar regulamentações vigentes, protocolos institucionais, características individuais do paciente e disponibilidade de medicamentos da unidade.<br>
  <strong>Base documental desta versão:</strong> Manual Farmacoterapêutico institucional, padronização institucional de antimicrobianos,
  REMUME/REMUNE disponibilizada para o projeto e referências clínicas já incorporadas à calculadora.
</section>

</main>

<script>
const $=id=>document.getElementById(id);

const presDefaults = {
 c_midazolam:5,c_fentanil:50,c_cetamina:50,c_rocuronio:10,c_succ:10,c_etomidato:2,
 c_epi_pcr:.1,c_epi_im:1,c_atropina:.5,c_atropina2:.25,c_adenosina:3,c_amiodarona:50,
 c_paracetamol_vo:200,c_ibuprofeno:20,c_dipirona:500,c_morfina:10,c_ondansetrona:2,
 c_amoxicilina:50,c_cefalexina:50,c_ceftriaxona_vial:1000,c_cefazolina_vial:1000,c_cefotaxima_vial:1000,c_azitro_vo:500,c_azitro_ev:500
};
function cv(id, fallback){
 const el=$(id); const v=el?parseFloat(el.value):NaN;
 return Number.isFinite(v)&&v>0?v:fallback;
}
function loadPres(){
 const saved=JSON.parse(localStorage.getItem('upa_ped_pres')||'{}');
 Object.entries(presDefaults).forEach(([id,val])=>{ if($(id)) $(id).value = saved[id] ?? val; });
}
function savePres(){
 const obj={}; Object.keys(presDefaults).forEach(id=>{ if($(id)) obj[id]=cv(id,presDefaults[id]); });
 localStorage.setItem('upa_ped_pres',JSON.stringify(obj)); calcular(); alert('Apresentações salvas neste navegador.');
}
function resetPres(){
 localStorage.removeItem('upa_ped_pres');
 Object.entries(presDefaults).forEach(([id,val])=>{ if($(id)) $(id).value=val; });
 calcular();
}

const fmt=(n,d=2)=>Number.isFinite(n)?n.toLocaleString('pt-BR',{maximumFractionDigits:d}):'—';
const clamp=(v,min,max)=>Math.min(Math.max(v,min),max);
function card(nome,dose,valor,unidade,rx='',extra='',warn='',cls=''){
 return `<article class="card ${cls}"><div class="drug">${nome}</div><div class="dose">${dose}</div><div class="result">${valor} <small>${unidade}</small></div>${rx?`<div class="rx">${rx}</div>`:''}${extra?`<div class="micro">${extra}</div>`:''}${warn?`<div class="warn">${warn}</div>`:''}</article>`;
}
function eq(k,v){return `<div class="eq"><b>${k}</b><span>${v}</span></div>`}
function doseVol(mg,conc){return mg/conc}
function calcMaint(p){
 if(p<=10) return 4*p;
 if(p<=20) return 40+2*(p-10);
 if(p<=60) return 60+(p-20);
 return 100;
}


const infState = {
 midazolam:{dose:.1},fentanil:{dose:1},epinefrina:{dose:.05},
 norepinefrina:{dose:.05},dopamina:{dose:5},dobutamina:{dose:5},rocuronio:{dose:7},rocuronio:{dose:7}
};
let activeInf='midazolam';

function infConfig(p,a){
 const equipoPrime=20;
 const midAmp=cv('c_midazolam',5);
 const fentAmp=cv('c_fentanil',50);
 const rocuAmp=cv('c_rocuronio',10);
 // Concentrations intentionally standardized so weight changes pump rate, not preparation concentration.
 return {
   midazolam:{
     name:'Midazolam', short:'MIDAZOLAM',
     unit:'mg/kg/h', range:'0,1–0,5 mg/kg/h • iniciar 0,1 mg/kg/h', min:.1, max:.5, step:.05,
     therapeuticVol:24, equipoPrime:equipoPrime,
     drugAmount:(infState.midazolam.dose*p*44), drugAmountUnit:'mg',
     ampConc:midAmp, ampUnit:'mg/mL',
     drugMl:(infState.midazolam.dose*p*44)/midAmp,
     finalVol:44,
     finalConc:(infState.midazolam.dose*p), finalConcUnit:'mg/mL',
     rate:dose => 1,
     evo:(dose,rate)=>`MIDAZOLAM: ${fmt(rate,2)} mL/h = ${fmt(dose,3)} mg/kg/h = ${fmt((dose*1000)/60,2)} mcg/kg/min. Preparo total: ${fmt((dose*p*44)/midAmp,2)} mL de midazolam ${fmt(midAmp,1)} mg/mL + ${fmt(44-(dose*p*44)/midAmp,2)} mL de SF 0,9% = 44 mL. Usar 20 mL para preencher o equipo; permanecem 24 mL terapêuticos.`
   },
   fentanil:{
     name:'Fentanil', short:'FENTANIL',
     unit:'mcg/kg/h', range:'1–5 mcg/kg/h • iniciar 1 mcg/kg/h', min:1, max:5, step:.5,
     therapeuticVol:24, equipoPrime:equipoPrime,
     drugAmount:(infState.fentanil.dose*p*44), drugAmountUnit:'mcg',
     ampConc:fentAmp, ampUnit:'mcg/mL',
     drugMl:(infState.fentanil.dose*p*44)/fentAmp,
     finalVol:44,
     finalConc:(infState.fentanil.dose*p), finalConcUnit:'mcg/mL',
     rate:dose => 1,
     evo:(dose,rate)=>`FENTANIL: ${fmt(rate,2)} mL/h = ${fmt(dose,2)} mcg/kg/h = ${fmt(dose/60,4)} mcg/kg/min. Preparo total: ${fmt((dose*p*44)/fentAmp,2)} mL de fentanil ${fmt(fentAmp,1)} mcg/mL + ${fmt(44-(dose*p*44)/fentAmp,2)} mL de SF 0,9% = 44 mL. Usar 20 mL para preencher o equipo; permanecem 24 mL terapêuticos.`
   },
   epinefrina:{
     name:'Epinefrina', short:'EPINEFRINA',
     unit:'mcg/kg/min', range:'0,01–1 mcg/kg/min • titular ao efeito', min:.01, max:1, step:.01,
     therapeuticVol:50, equipoPrime:equipoPrime,
     drugAmount:1.4, drugAmountUnit:'mg', ampConc:1, ampUnit:'mg/mL',
     drugMl:1.4, finalVol:70, finalConc:20, finalConcUnit:'mcg/mL',
     rate:dose => dose*p*60/20,
     evo:(dose,rate)=>`EPINEFRINA: ${fmt(rate,2)} mL/h = ${fmt(dose,3)} mcg/kg/min.`
   },
   norepinefrina:{
     name:'Norepinefrina', short:'NOREPINEFRINA',
     unit:'mcg/kg/min', range:'0,01–1 mcg/kg/min • titular ao efeito', min:.01, max:1, step:.01,
     therapeuticVol:50, equipoPrime:equipoPrime,
     drugAmount:1.4, drugAmountUnit:'mg', ampConc:1, ampUnit:'mg/mL',
     drugMl:1.4, finalVol:70, finalConc:20, finalConcUnit:'mcg/mL',
     rate:dose => dose*p*60/20,
     evo:(dose,rate)=>`NOREPINEFRINA: ${fmt(rate,2)} mL/h = ${fmt(dose,3)} mcg/kg/min.`
   },
   dopamina:{
     name:'Dopamina', short:'DOPAMINA',
     unit:'mcg/kg/min', range:'2–10 mcg/kg/min • titular ao efeito', min:2, max:10, step:1,
     therapeuticVol:50, equipoPrime:equipoPrime,
     drugAmount:84, drugAmountUnit:'mg', ampConc:5, ampUnit:'mg/mL',
     drugMl:16.8, finalVol:70, finalConc:1200, finalConcUnit:'mcg/mL',
     rate:dose => dose*p*60/1200,
     evo:(dose,rate)=>`DOPAMINA: ${fmt(rate,2)} mL/h = ${fmt(dose,2)} mcg/kg/min.`
   },
   dobutamina:{
     name:'Dobutamina', short:'DOBUTAMINA',
     unit:'mcg/kg/min', range:'2–10 mcg/kg/min • titular ao efeito', min:2, max:10, step:1,
     therapeuticVol:50, equipoPrime:equipoPrime,
     drugAmount:105, drugAmountUnit:'mg', ampConc:12.5, ampUnit:'mg/mL',
     drugMl:8.4, finalVol:70, finalConc:1500, finalConcUnit:'mcg/mL',
     rate:dose => dose*p*60/1500,
     evo:(dose,rate)=>`DOBUTAMINA: ${fmt(rate,2)} mL/h = ${fmt(dose,2)} mcg/kg/min.`
   },
   rocuronio:{
     name:'Rocurônio', short:'ROCURÔNIO',
     unit:'mcg/kg/min', range:'7–14 mcg/kg/min • iniciar 7 mcg/kg/min', min:7, max:14, step:1,
     therapeuticVol:24, equipoPrime:equipoPrime,
     drugAmount:(infState.rocuronio.dose*p*44*60)/1000, drugAmountUnit:'mg',
     ampConc:rocuAmp, ampUnit:'mg/mL',
     drugMl:(infState.rocuronio.dose*p*44*60)/(rocuAmp*1000),
     finalVol:44,
     finalConc:(infState.rocuronio.dose*p*60), finalConcUnit:'mcg/mL',
     rate:dose => 1,
     evo:(dose,rate)=>`ROCURÔNIO: ${fmt(rate,2)} mL/h = ${fmt(dose,2)} mcg/kg/min. Preparo total: ${fmt((dose*p*44*60)/(rocuAmp*1000),2)} mL de rocurônio ${fmt(rocuAmp,1)} mg/mL + ${fmt(44-(dose*p*44*60)/(rocuAmp*1000),2)} mL de SF 0,9% = 44 mL. Usar 20 mL para preencher o equipo; permanecem 24 mL terapêuticos.`
   }
 };
}

function renderInfFocus(){
 const p=parseFloat($('peso').value), a=parseFloat($('idade').value);
 if(!(p>0)){
   $('infFocus').innerHTML='<div class="inf-focus"><strong>Informe o peso do paciente.</strong><div class="rx">O sistema calculará automaticamente o preparo e a velocidade da bomba.</div></div>';
   $('infSummary').textContent='Informe o peso e selecione a medicação.';
   return;
 }
 const cfg=infConfig(p,a)[activeInf];
 let dose=parseFloat(infState[activeInf].dose);
 if(!Number.isFinite(dose)) dose=cfg.min;
 const rate=cfg.rate(dose);
 const diluent=Math.max(cfg.finalVol-cfg.drugMl,0);
 const evo=cfg.evo(dose,rate);
 $('infFocus').innerHTML=`<div class="inf-focus">
   <div class="inf-head">
     <div>
       <h3>${cfg.name}</h3>
       <div class="dose">Peso: <strong>${fmt(p,2)} kg</strong> • faixa de referência: ${cfg.range}</div>
     </div>
   </div>

   <div class="flowrow">
     <div>
       <div class="mini">Dose-alvo (${cfg.unit})</div>
       <input id="infDoseInput" type="number" min="${cfg.min}" max="${cfg.max}" step="${cfg.step}"
              value="${dose}" oninput="updateInfDose(this.value)">
     </div>
     <div class="doseout">
       <div class="mini">Programar bomba</div>
       <b>${fmt(rate,2)}</b> <span>mL/h</span>
     </div>
   </div>

   <div class="inf-meta">
     <div class="meta">
       <b>Quantidade do medicamento</b>
       ${fmt(cfg.drugAmount,2)} ${cfg.drugAmountUnit} =
       <strong>${fmt(cfg.drugMl,2)} mL</strong> da apresentação ${fmt(cfg.ampConc,2)} ${cfg.ampUnit}
     </div>
     <div class="meta">
       <b>Diluição</b>
       Aspirar <strong>${fmt(cfg.drugMl,2)} mL</strong> do medicamento +
       <strong>${fmt(diluent,2)} mL</strong> de diluente,
       totalizando <strong>${fmt(cfg.finalVol,0)} mL</strong>.
     </div>
     <div class="meta">
       <b>Concentração final</b>
       ${fmt(cfg.finalConc,3)} ${cfg.finalConcUnit}
     </div>
     <div class="meta">
       <b>Velocidade calculada pelo peso</b>
       ${fmt(rate,2)} mL/h para ${fmt(dose,3)} ${cfg.unit}
     </div>
   </div>

   <div class="good"><strong>EVOLUÇÃO:</strong> ${evo}</div>
   ${activeInf==='midazolam'?'<div class="warn"><strong>Atenção à unidade:</strong> 0,1–0,5 mg/kg/h corresponde aproximadamente a 1,67–8,33 mcg/kg/min. A faixa 1–18 mcg/kg/min é mais ampla e não é equivalente à faixa em mg/kg/h; por isso a calculadora usa mg/kg/h como campo principal e mostra a conversão exata para mcg/kg/min.</div>':''}
   ${activeInf==='rocuronio'?'<div class="good"><strong>Preparo institucional:</strong> a seringa é calculada para que 1 mL/h = 7 mcg/kg/min. Consequentemente, 2 mL/h = 14 mcg/kg/min. Volume final: 48 mL.</div>':''}
   ${activeInf==='midazolam'?'<div class="good"><strong>Preparo pediátrico conforme manual:</strong> calcular a quantidade correspondente a 24 horas da dose-alvo e completar com SF 0,9% para volume final de 24 mL. Assim, 1 mL/h corresponde exatamente à dose selecionada em mg/kg/h.</div>':''}
   ${activeInf==='fentanil'?'<div class="good"><strong>Preparo pediátrico conforme manual:</strong> calcular a quantidade correspondente a 24 horas da dose-alvo e completar com SF 0,9% para volume final de 24 mL. Assim, 1 mL/h corresponde exatamente à dose selecionada em mcg/kg/h.</div>':''}
   ${activeInf==='rocuronio'?'<div class="good"><strong>Preparo pediátrico conforme manual:</strong> calcular a quantidade correspondente a 24 horas da dose-alvo e completar com SF 0,9% para volume final de 24 mL. Assim, 1 mL/h corresponde exatamente à dose selecionada em mcg/kg/min.</div>':''}
   <div class="warn">Conferir a padronização da farmácia da unidade e monitorar continuamente durante bloqueio neuromuscular.</div>
 </div>`;
 $('infSummary').textContent=evo;
}

function updateInfDose(v){
 const n=parseFloat(v);
 if(Number.isFinite(n)) infState[activeInf].dose=n;
 renderInfFocus();
}

function copyInfSummary(){
 const txt=$('infSummary').textContent;
 if(navigator.clipboard){
   navigator.clipboard.writeText(txt).then(()=>alert('Texto da evolução copiado.'));
 } else {
   alert(txt);
 }
}

document.addEventListener('click',e=>{
 if(e.target.classList.contains('quickdrug')){
   document.querySelectorAll('.quickdrug').forEach(x=>x.classList.remove('active'));
   e.target.classList.add('active');
   activeInf=e.target.dataset.inf;
   renderInfFocus();
 }
});

function vmGroupDefaults(group,scenario){
 const base={
   neo:{vtMin:4,vtMax:6,vtSel:5,frMin:30,frMax:50,frSel:40,ti:.35,peep:5,dp:12},
   lactente:{vtMin:6,vtMax:8,vtSel:7,frMin:25,frMax:35,frSel:30,ti:.50,peep:5,dp:12},
   crianca:{vtMin:6,vtMax:8,vtSel:7,frMin:18,frMax:25,frSel:20,ti:.70,peep:5,dp:12},
   adolescente:{vtMin:6,vtMax:8,vtSel:7,frMin:12,frMax:18,frSel:15,ti:.80,peep:5,dp:12}
 }[group];
 if(scenario==='sdra'){ base.vtMin=4; base.vtMax=6; base.vtSel=6; base.peep=8; base.dp=10; }
 if(scenario==='asma'){ base.vtMin=6; base.vtMax=8; base.vtSel=7; base.peep=5; base.frSel=Math.max(base.frMin-4,8); base.ti=Math.min(base.ti,.65); base.dp=12; }
 return base;
}

function calcVM(){
 const p=parseFloat($('peso')?.value);
 const group=$('vmGrupo')?.value || 'crianca';
 const mode=$('vmModo')?.value || 'VCV';
 const scenario=$('vmCenario')?.value || 'normal';
 if(!$('vmCards')) return;
 if(!(p>0)){
   $('vmCards').innerHTML='<div class="card"><strong>Informe o peso do paciente</strong><div class="rx">Os parâmetros iniciais serão calculados automaticamente.</div></div>';
   $('vmSummary').textContent='Informe o peso e selecione os parâmetros.';
   if($('vmMonitor')) $('vmMonitor').innerHTML='';
   return;
 }
 const d=vmGroupDefaults(group,scenario);
 const vt=Math.round(d.vtSel*p);
 const vtRange=`${Math.round(d.vtMin*p)}–${Math.round(d.vtMax*p)}`;
 const fio2=scenario==='normal'?100:100;
 const ie=scenario==='asma'?'1:3 a 1:5':'~1:2';
 const flow=scenario==='asma'?'Fluxo alto / tempo expiratório prolongado':'Ajustar para atingir Tinsp e I:E';
 const peepText=scenario==='sdra'?`${d.peep}–10`:`${d.peep}`;
 let cards=[];
 if(mode==='VCV'){
   cards=[
     card('Volume corrente',`${d.vtMin}–${d.vtMax} mL/kg • inicial ${d.vtSel} mL/kg`,fmt(vt),'mL',`Faixa pelo peso: ${vtRange} mL.`,'',scenario==='sdra'?'Manter estratégia protetora; titular pelo Pplat/pressão de distensão.':''),
     card('Frequência respiratória',`${d.frMin}–${d.frMax} irpm`,fmt(d.frSel),'irpm',scenario==='asma'?'Começar mais baixo e garantir expiração completa.':'Ajustar conforme PaCO₂/pH.'),
     card('PEEP',scenario==='sdra'?'inicial 8–10 cmH₂O':'inicial habitual 5 cmH₂O',peepText,'cmH₂O','Titular conforme oxigenação, complacência e hemodinâmica.'),
     card('FiO₂ inicial','situação de emergência / pós-IOT',fmt(fio2),'%',`Reduzir rapidamente para a menor FiO₂ que mantenha alvo de SpO₂ apropriado.`),
     card('Tempo inspiratório',`referência para ${group}`,fmt(d.ti,2),'s',`I:E ${ie}. ${flow}`),
     card('Limites protetores','monitorar Pplat / ΔP','Pplat < 30','cmH₂O','Buscar ΔP (Pplat − PEEP) preferencialmente ≤15 cmH₂O quando mensurável.','','O limite deve ser individualizado em neonatos e doenças com complacência muito reduzida.')
   ];
 } else {
   cards=[
     card('Pressão controlada (ΔP)','pressão acima da PEEP • inicial e titular',fmt(d.dp),'cmH₂O',`Começar aproximadamente ${d.dp} cmH₂O acima da PEEP e titular para obter VC expirado ~${d.vtMin}–${d.vtMax} mL/kg (${vtRange} mL).`,'','Não confundir ΔPcontrol com PIP total.'),
     card('PEEP',scenario==='sdra'?'inicial 8–10 cmH₂O':'inicial habitual 5 cmH₂O',peepText,'cmH₂O','Titular conforme oxigenação, complacência e hemodinâmica.'),
     card('Frequência respiratória',`${d.frMin}–${d.frMax} irpm`,fmt(d.frSel),'irpm',scenario==='asma'?'Começar mais baixo e garantir expiração completa.':'Ajustar conforme PaCO₂/pH.'),
     card('Tempo inspiratório',`referência para ${group}`,fmt(d.ti,2),'s',`I:E ${ie}.`),
     card('FiO₂ inicial','situação de emergência / pós-IOT',fmt(fio2),'%',`Reduzir rapidamente para a menor FiO₂ que mantenha alvo de SpO₂ apropriado.`),
     card('Alvo de volume expirado',`${d.vtMin}–${d.vtMax} mL/kg`,vtRange,'mL','Ajustar ΔP para atingir o volume expirado alvo e evitar pressões excessivas.')
   ];
 }
 $('vmCards').innerHTML=cards.join('');

 const pao2=parseFloat($('vmPaO2')?.value);
 const fio=parseFloat($('vmFiO2')?.value);
 const pplat=parseFloat($('vmPplat')?.value);
 const peepM=parseFloat($('vmPeepMed')?.value);
 let mon=[];
 let pf=null, drive=null;
 if(Number.isFinite(pao2)&&Number.isFinite(fio)&&fio>0){
   pf=pao2/(fio/100);
   mon.push(card('Relação P/F','PaO₂ ÷ FiO₂',fmt(pf,0),'',pf<100?'Hipoxemia muito grave':pf<200?'Hipoxemia importante':pf<300?'Hipoxemia moderada':''));
 }
 if(Number.isFinite(pplat)&&Number.isFinite(peepM)){
   drive=pplat-peepM;
   mon.push(card('Driving pressure','Pplat − PEEP',fmt(drive,1),'cmH₂O',drive<=15?'Dentro do alvo protetor usual.':'Reavaliar VC, complacência e PEEP.','',''));
   mon.push(card('Pressão de platô','meta protetora usual',fmt(pplat,1),'cmH₂O',pplat<30?'Abaixo de 30 cmH₂O.':'Acima/igual a 30: revisar estratégia ventilatória.','',''));
 }
 $('vmMonitor').innerHTML=mon.length?mon.join(''):'<div class="card"><div class="rx">Preencha PaO₂/FiO₂ e Pplat/PEEP para calcular P/F e driving pressure.</div></div>';

 const groupLabel={neo:'NEONATAL',lactente:'LACTENTE',crianca:'PEDIÁTRICO',adolescente:'ADOLESCENTE'}[group];
 let summary=`VENTILAÇÃO MECÂNICA ${groupLabel}\nModo ${mode}\nPeso ${fmt(p,2)} kg\n`;
 if(mode==='VCV'){
   summary+=`VC ${vt} mL (${d.vtSel} mL/kg)\nFR ${d.frSel} irpm\nPEEP ${peepText} cmH₂O\nFiO₂ ${fio2}%\nTinsp ${fmt(d.ti,2)} s\nI:E ${ie}`;
 } else {
   summary+=`PC acima da PEEP ${fmt(d.dp)} cmH₂O\nAlvo VC ${vtRange} mL (${d.vtMin}–${d.vtMax} mL/kg)\nFR ${d.frSel} irpm\nPEEP ${peepText} cmH₂O\nFiO₂ ${fio2}%\nTinsp ${fmt(d.ti,2)} s\nI:E ${ie}`;
 }
 if(pf!==null) summary+=`\nP/F ${fmt(pf,0)}`;
 if(Number.isFinite(pplat)) summary+=`\nPplat ${fmt(pplat,1)} cmH₂O`;
 if(drive!==null) summary+=`\nDriving pressure ${fmt(drive,1)} cmH₂O`;
 $('vmSummary').textContent=summary;
}

function copyVMSummary(){
 const txt=$('vmSummary')?.textContent || '';
 if(navigator.clipboard){navigator.clipboard.writeText(txt).then(()=>alert('Evolução ventilatória copiada.'))}
 else alert(txt);
}



function pewsAgeLimits(age){
  // Faixas de referência pragmáticas para triagem. O escore usa desvio em relação
  // aos limites superiores/inferiores por idade, seguindo a lógica do Bedside PEWS.
  if(!Number.isFinite(age)) return {hrLo:70,hrHi:120,rrLo:15,rrHi:30,sbpLo:80};
  if(age < 0.25) return {hrLo:100,hrHi:180,rrLo:30,rrHi:60,sbpLo:60};
  if(age < 1) return {hrLo:100,hrHi:170,rrLo:25,rrHi:50,sbpLo:70};
  if(age < 2) return {hrLo:90,hrHi:160,rrLo:20,rrHi:40,sbpLo:70};
  if(age < 5) return {hrLo:80,hrHi:140,rrLo:20,rrHi:30,sbpLo:75};
  if(age < 12) return {hrLo:70,hrHi:120,rrLo:15,rrHi:25,sbpLo:80};
  return {hrLo:60,hrHi:110,rrLo:12,rrHi:20,sbpLo:90};
}
function pewsPhysScore(value,lo,hi,step1,step2){
 if(!Number.isFinite(value)) return 0;
 if(value>=lo && value<=hi) return 0;
 if(value>hi){
   if(value<=hi+step1) return 1;
   if(value<=hi+step2) return 2;
   return 3;
 }
 if(value<lo){
   if(value>=lo-step1) return 1;
   if(value>=lo-step2) return 2;
   return 3;
 }
 return 0;
}
function calcPEWS(){
 if(!$('pewsResult')) return;
 const age=parseFloat($('idade')?.value);
 const lim=pewsAgeLimits(age);
 const hr=parseFloat($('pewsHR')?.value);
 const rr=parseFloat($('pewsRR')?.value);
 const sat=parseFloat($('pewsSat')?.value);
 const sbp=parseFloat($('pewsSBP')?.value);
 const temp=parseFloat($('pewsTemp')?.value);
 const crt=parseInt($('pewsCRT')?.value||0);
 const mental=parseInt($('pewsMental')?.value||0);
 const work=parseInt($('pewsWork')?.value||0);
 const oxy=parseInt($('pewsO2')?.value||0);

 let hrS=pewsPhysScore(hr,lim.hrLo,lim.hrHi,20,30);
 let rrS=pewsPhysScore(rr,lim.rrLo,lim.rrHi,10,20);

 let satS=0;
 if(Number.isFinite(sat)){
   if(sat>=95) satS=0;
   else if(sat>=92) satS=1;
   else if(sat>=90) satS=2;
   else satS=3;
 }

 let sbpS=0;
 if(Number.isFinite(sbp)){
   if(sbp>=lim.sbpLo) sbpS=0;
   else if(sbp>=lim.sbpLo-10) sbpS=1;
   else if(sbp>=lim.sbpLo-20) sbpS=2;
   else sbpS=3;
 }

 let tempS=0;
 if(Number.isFinite(temp)){
   if(temp>=36 && temp<=38) tempS=0;
   else if((temp>=35.5&&temp<36)||(temp>38&&temp<=38.5)) tempS=1;
   else if((temp>=35&&temp<35.5)||(temp>38.5&&temp<=39)) tempS=2;
   else tempS=3;
 }

 // Cardiovascular/respiratory domains use the worst sign, avoiding double-counting
 // every parameter from the same physiological system.
 const cardio=Math.max(hrS,sbpS,crt);
 const resp=Math.max(rrS,satS,work,oxy);
 const neuro=mental;
 const systemic=tempS>1?1:0; // temperature is an adjunct, capped at 1 point.
 const total=cardio+resp+neuro+systemic;

 let cls='low', risk='BAIXO RISCO', guidance='Manter monitorização e reavaliar conforme quadro clínico.';
 if(total>=5){
   cls='high'; risk='GRAVE / ALTO RISCO';
   guidance='Reavaliação médica imediata, monitorização contínua e considerar escalonamento de cuidados/sala de emergência conforme quadro.';
 } else if(total>=3){
   cls='mod'; risk='RISCO MODERADO';
   guidance='Reavaliar em curto intervalo, repetir sinais vitais e considerar avaliação médica prioritária.';
 }

 const details=`Cardiovascular ${cardio} • Respiratório ${resp} • Neurológico ${neuro}${systemic?` • Temperatura +${systemic}`:''}`;
 $('pewsResult').className=`pews-result ${cls}`;
 $('pewsResult').innerHTML=`<div class="pews-score">PEWS ${total}</div><div class="pews-risk">${risk}</div><div class="pews-guidance">${details}<br>${guidance}</div>`;
}


function scoreSelect(label,id,opts){return `<div><div class="mini">${label}</div><select id="${id}" onchange="calcScores()">${opts.map(o=>`<option value="${o[0]}">${o[1]}</option>`).join('')}</select></div>`}
function scoreBox(title,subtitle,fields,resultId){return `<div class="calcbox"><h3>${title}</h3><div class="mini">${subtitle}</div><div class="row">${fields}</div><div id="${resultId}" class="pews-result" style="margin-top:12px"></div></div>`}
function initScores(){
 if(!$('scoreCalculators')) return;
 let html='';
 html+=scoreBox('Glasgow Pediátrico','Total 3–15',scoreSelect('Olhos','gcsE',[[4,'4 — espontânea'],[3,'3 — à voz'],[2,'2 — à dor'],[1,'1 — nenhuma']])+scoreSelect('Verbal','gcsV',[[5,'5 — apropriada / sorri, acompanha, interage'],[4,'4 — confusa / choro consolável'],[3,'3 — palavras inadequadas / choro persistente'],[2,'2 — sons incompreensíveis / agitação'],[1,'1 — nenhuma']])+scoreSelect('Motora','gcsM',[[6,'6 — obedece / movimentos espontâneos'],[5,'5 — localiza dor'],[4,'4 — retira à dor'],[3,'3 — flexão anormal'],[2,'2 — extensão'],[1,'1 — nenhuma']]),'gcsOut');
 html+=scoreBox('PRAM','Asma • 0–12',scoreSelect('Retração supraesternal','pram1',[[0,'0 — ausente'],[2,'2 — presente']])+scoreSelect('Escalenos','pram2',[[0,'0 — ausente'],[2,'2 — presente']])+scoreSelect('Entrada de ar','pram3',[[0,'0 — normal'],[1,'1 — diminuída bases'],[2,'2 — diminuída ápices e bases'],[3,'3 — mínima/ausente']])+scoreSelect('Sibilância','pram4',[[0,'0 — ausente'],[1,'1 — expiratória'],[2,'2 — inspiratória + expiratória'],[3,'3 — audível sem estetoscópio/silêncio']])+scoreSelect('SpO₂','pram5',[[0,'0 — ≥95%'],[1,'1 — 92–94%'],[2,'2 — <92%']]),'pramOut');
 html+=scoreBox('Westley','Crupe • 0–17',scoreSelect('Consciência','west1',[[0,'0 — normal'],[5,'5 — alterada']])+scoreSelect('Cianose','west2',[[0,'0 — nenhuma'],[4,'4 — com agitação'],[5,'5 — em repouso']])+scoreSelect('Estridor','west3',[[0,'0 — nenhum'],[1,'1 — com agitação'],[2,'2 — em repouso']])+scoreSelect('Entrada de ar','west4',[[0,'0 — normal'],[1,'1 — diminuída'],[2,'2 — muito diminuída']])+scoreSelect('Retrações','west5',[[0,'0 — nenhuma'],[1,'1 — leves'],[2,'2 — moderadas'],[3,'3 — intensas']]),'westOut');
 html+=scoreBox('Pediatric Appendicitis Score (PAS)','0–10',scoreSelect('Migração da dor para FID','pas1',[[0,'Não'],[1,'Sim +1']])+scoreSelect('Anorexia','pas2',[[0,'Não'],[1,'Sim +1']])+scoreSelect('Náuseas/vômitos','pas3',[[0,'Não'],[1,'Sim +1']])+scoreSelect('Dor à tosse/percussão/salto em FID','pas4',[[0,'Não'],[2,'Sim +2']])+scoreSelect('Dor à palpação em FID','pas5',[[0,'Não'],[2,'Sim +2']])+scoreSelect('Febre ≥38 °C','pas6',[[0,'Não'],[1,'Sim +1']])+scoreSelect('Leucócitos >10.000/mm³','pas7',[[0,'Não'],[1,'Sim +1']])+scoreSelect('Neutrofilia >7.500/mm³','pas8',[[0,'Não'],[1,'Sim +1']]),'pasOut');
 html+=scoreBox('FLACC','Dor • 0–10',scoreSelect('Face','fl1',[[0,'0 — relaxada'],[1,'1 — careta ocasional'],[2,'2 — careta frequente/mandíbula cerrada']])+scoreSelect('Pernas','fl2',[[0,'0 — relaxadas'],[1,'1 — inquietas/tensas'],[2,'2 — chutes/pernas fletidas']])+scoreSelect('Atividade','fl3',[[0,'0 — quieto/normal'],[1,'1 — contorcendo/tenso'],[2,'2 — arqueado/rígido']])+scoreSelect('Choro','fl4',[[0,'0 — sem choro'],[1,'1 — gemido/queixa'],[2,'2 — choro constante/gritos']])+scoreSelect('Consolabilidade','fl5',[[0,'0 — contente/relaxado'],[1,'1 — consolável'],[2,'2 — difícil consolar']]),'flOut');
 html+=scoreBox('Pediatric Trauma Score','−6 a +12',scoreSelect('Peso','pts1',[[2,'>20 kg: +2'],[1,'10–20 kg: +1'],[-1,'<10 kg: −1']])+scoreSelect('Via aérea','pts2',[[2,'Normal: +2'],[1,'Mantível: +1'],[-1,'Não mantível: −1']])+scoreSelect('PAS','pts3',[[2,'>90 mmHg: +2'],[1,'50–90 mmHg: +1'],[-1,'<50 mmHg: −1']])+scoreSelect('SNC','pts4',[[2,'Acordado: +2'],[1,'Obnubilado/perda consciência: +1'],[-1,'Coma: −1']])+scoreSelect('Feridas','pts5',[[2,'Nenhuma: +2'],[1,'Menores: +1'],[-1,'Maiores/penetrantes: −1']])+scoreSelect('Fraturas','pts6',[[2,'Nenhuma: +2'],[1,'Fechada: +1'],[-1,'Aberta/múltiplas: −1']]),'ptsOut');
 html+=`<div class="calcbox"><h3>PECARN — Trauma Cranioencefálico</h3><div class="mini">Regra de decisão clínica; selecione a faixa etária e marque os achados.</div><div class="row">${scoreSelect('Faixa etária','pecAge',[[0,'< 2 anos'],[1,'≥ 2 anos']])}${scoreSelect('GCS <15 ou alteração do estado mental','pecHigh1',[[0,'Não'],[1,'Sim']])}${scoreSelect('Sinal de fratura de crânio de alto risco','pecHigh2',[[0,'Não'],[1,'Sim']])}${scoreSelect('LOC significativo','pecMid1',[[0,'Não'],[1,'Sim']])}${scoreSelect('Mecanismo grave','pecMid2',[[0,'Não'],[1,'Sim']])}${scoreSelect('Achado intermediário específico da idade','pecMid3',[[0,'Não'],[1,'Sim']])}</div><div class="micro">&lt;2 anos: alto risco = fratura palpável; intermediários incluem LOC ≥5 s e comportamento anormal pelos pais. ≥2 anos: alto risco = sinais de fratura basilar; intermediários incluem qualquer LOC, vômitos ou cefaleia intensa. “Mecanismo grave” deve seguir a definição PECARN original.</div><div id="pecOut" class="pews-result" style="margin-top:12px"></div></div>`;
 html+=`<div class="calcbox"><h3>PEWS</h3><div class="mini">O PEWS interativo completo permanece disponível na aba Sepse/Deterioração. O resultado é calculado automaticamente pelos campos clínicos daquela aba.</div></div>`;
 $('scoreCalculators').innerHTML=html; calcScores();
}
function sumIds(ids){return ids.reduce((t,id)=>t+(parseInt(($(id)||{}).value)||0),0)}
function setScore(id,score,text){if($(id)) $(id).innerHTML=`<div class="pews-score">${score}</div><div class="pews-risk">${text}</div>`}
function calcScores(){
 if(!$('scoreCalculators')) return;
 let g=sumIds(['gcsE','gcsV','gcsM']); setScore('gcsOut',`GCS ${g}`,g<=8?'Grave — considerar proteção de via aérea conforme contexto':g<=12?'Moderado':'Leve / preservado');
 let pr=sumIds(['pram1','pram2','pram3','pram4','pram5']); setScore('pramOut',`PRAM ${pr}/12`,pr<=3?'Leve':pr<=7?'Moderada':'Grave');
 let w=sumIds(['west1','west2','west3','west4','west5']); setScore('westOut',`Westley ${w}/17`,w<=2?'Leve':w<=5?'Moderado':w<=11?'Grave':'Insuficiência respiratória iminente');
 let pas=sumIds(['pas1','pas2','pas3','pas4','pas5','pas6','pas7','pas8']); setScore('pasOut',`PAS ${pas}/10`,pas<=3?'Baixa pontuação':pas<=6?'Intermediária':'Alta pontuação');
 let fl=sumIds(['fl1','fl2','fl3','fl4','fl5']); setScore('flOut',`FLACC ${fl}/10`,fl===0?'Sem dor observável':fl<=3?'Desconforto leve':fl<=6?'Dor moderada':'Dor intensa');
 let pts=sumIds(['pts1','pts2','pts3','pts4','pts5','pts6']); setScore('ptsOut',`PTS ${pts}`,pts<=8?'Maior gravidade / maior risco de trauma significativo':'Pontuação >8');
 let high=(parseInt($('pecHigh1')?.value)||0)||(parseInt($('pecHigh2')?.value)||0); let mid=(parseInt($('pecMid1')?.value)||0)||(parseInt($('pecMid2')?.value)||0)||(parseInt($('pecMid3')?.value)||0); let age=parseInt($('pecAge')?.value)||0;
 let txt=high?'Critério de alto risco presente — avaliar TC conforme regra PECARN e contexto clínico.':mid?'Sem critério de alto risco, mas há critério intermediário — observação versus TC conforme conjunto clínico e regra PECARN.':'Nenhum critério selecionado — risco muito baixo pela triagem apresentada, se todos os critérios PECARN aplicáveis foram corretamente avaliados.';
 if($('pecOut')) $('pecOut').innerHTML=`<div class="pews-score">PECARN ${age?'≥2 anos':'<2 anos'}</div><div class="pews-risk">${txt}</div>`;
}

function syncPaciente(){
 const kg=parseFloat(($('pesoKg')||{}).value)||0, g=parseFloat(($('pesoG')||{}).value)||0;
 const anos=parseFloat(($('idadeAnos')||{}).value)||0, meses=parseFloat(($('idadeMeses')||{}).value)||0;
 $('peso').value=(kg+g/1000)||''; $('idade').value=(anos+meses/12)||'';
 calcular(); calcVM(); calcPEWS(); calcNovasAbas();
}
function calcNovasAbas(){
 const p=parseFloat($('peso').value), a=parseFloat($('idade').value); if(!Number.isFinite(p)||p<=0) return;
 const abx={
  ampicilina:{n:'Ampicilina',dose:'50–200 mg/kg/dia, divididos 6/6 h',unit:'mg/kg/dia',opts:[50,100,150,200],def:100,div:4,max:12000,conc:100,prep:'FA 1 g + 10 mL de água para injeção = 100 mg/mL.',dil:'Para infusão intermitente: diluir a dose reconstituída em 50–100 mL de SF 0,9% ou SG 5%.',tempo:'15–30 min',bomba:'Não especificada pelo Manual. Usar infusão controlada conforme rotina da unidade.',direct:'Alternativa: IV direta lenta em 3–5 min.'},
  azitromicina:{n:'Azitromicina EV',dose:'10 mg/kg/dose 24/24 h • máx. 500 mg/dia',unit:'mg/kg/dose',opts:[10],def:10,div:1,max:500,conc:100,prep:'FA 500 mg + 4,8 mL de água para injeção ≈ 100 mg/mL.',dil:'Diluir para concentração final de 1 mg/mL ou 2 mg/mL em SF 0,9% ou SG 5%. O Manual cita 250 mL como diluição do FA de 500 mg conforme concentração desejada.',tempo:'1 mg/mL: 3 h • 2 mg/mL: 1 h',bomba:'Não especificada como obrigatória pelo Manual; infusão deve ter tempo rigorosamente controlado.',direct:'NÃO administrar em bolus IV ou IM.'},
  cefazolina:{n:'Cefazolina',dose:'25–50 mg/kg/dia; grave até 100 mg/kg/dia, divididos 6–8/8 h',unit:'mg/kg/dia',opts:[25,50,100],def:50,div:3,max:6000,conc:100,prep:'FA 1 g + 10 mL de água para injeção = 100 mg/mL.',dil:'Para infusão: diluir a dose em 50–100 mL de SF 0,9% ou SG 5%.',tempo:'20–30 min',bomba:'Não especificada pelo Manual. Usar infusão controlada conforme rotina da unidade.',direct:'Alternativa: IV direta lenta em 3–5 min.'},
  ceftriaxona:{n:'Ceftriaxona',dose:'50–75 mg/kg/dia (15 dias–12 anos) • máx. 2 g/dia habitual',unit:'mg/kg/dia',opts:[50,75],def:75,div:1,max:2000,conc:100,prep:'FA 1 g + 10 mL de água para injeção = 100 mg/mL.',dil:'Diluir a dose em 50–100 mL de SF 0,9% ou SG 5%. NÃO usar soluções contendo cálcio/Ringer lactato.',tempo:'≈ 30 min',bomba:'Não especificada pelo Manual. Usar infusão controlada conforme rotina da unidade.',direct:'Via IV em infusão lenta; IM também descrita no Manual.'},
  metronidazol:{n:'Metronidazol',dose:'7,5 mg/kg/dose 8/8 h • solução 5 mg/mL',unit:'mg/kg/dose',opts:[7.5],def:7.5,div:1,max:1333,conc:5,prep:'Bolsa 100 mL = 5 mg/mL, pronta para uso.',dil:'NÃO necessita diluição adicional. Não adicionar outros medicamentos à bolsa.',tempo:'20–60 min',bomba:'Não especificada pelo Manual. Usar infusão controlada conforme rotina da unidade.',direct:'Uso exclusivamente IV em infusão intermitente.'},
  oxacilina:{n:'Oxacilina',dose:'50–100 mg/kg/dia; infecções graves podem exigir doses maiores, até 300 mg/kg/dia conforme prescrição',unit:'mg/kg/dia',opts:[50,100,150,200,250,300],def:100,div:4,max:12000,conc:100,prep:'FA 500 mg + 5 mL de água para injeção = 100 mg/mL.',dil:'Para infusão IV: diluir a dose reconstituída em 50–100 mL de SF 0,9% ou SG 5%.',tempo:'Manual não informa tempo da infusão intermitente',bomba:'Não especificada pelo Manual.',direct:'Alternativa: IV direta lenta em 3–5 min.'},
  piptazo:{n:'Piperacilina + tazobactam',dose:'80 mg/kg/dose 6/6 h • até 100 mg/kg/dose',unit:'mg/kg/dose',opts:[80,100],def:80,div:1,max:4500,conc:225,prep:'FA 4,5 g + 20 mL de SF 0,9% = 225 mg/mL do produto.',dil:'Diluir a dose reconstituída em 100 mL de SF 0,9%.',tempo:'20–30 min',bomba:'Não especificada pelo Manual. Usar infusão controlada conforme rotina da unidade.',direct:'Uso exclusivamente IV.'}
 };
 const d=abx[$('abxDrug')?$('abxDrug').value:'ampicilina'];
 const doseSel=$('abxDoseSelect');
 if(doseSel){
   const signature=d.opts.join('|')+'|'+d.unit;
   if(doseSel.dataset.signature!==signature){
     doseSel.innerHTML=d.opts.map(v=>`<option value="${v}"${v===d.def?' selected':''}>${String(v).replace('.',',')} ${d.unit}</option>`).join('');
     doseSel.dataset.signature=signature;
   }
 }
 const chosenDose=doseSel ? Number(doseSel.value||d.def) : d.def;
 let mg=Math.min(chosenDose*p/d.div,d.max); let ml=mg/d.conc;
 const dailyCalc=d.unit==='mg/kg/dia' ? Math.min(chosenDose*p,d.max) : null;
 const selectedInfo=d.unit==='mg/kg/dia'
   ? `Dose escolhida: ${String(chosenDose).replace('.',',')} mg/kg/dia → ${fmt(dailyCalc)} mg/dia, divididos em ${d.div} dose(s).`
   : `Dose escolhida: ${String(chosenDose).replace('.',',')} mg/kg/dose.`;
 if($('abxNewCards')) $('abxNewCards').innerHTML=`<article class="card" style="grid-column:1/-1"><div class="drug">${d.n}</div><div class="dose">${d.dose}</div><div class="micro" style="margin:6px 0"><strong>${selectedInfo}</strong></div><div class="big">${fmt(mg)} mg por dose</div><div class="micro"><strong>1. RECONSTITUIÇÃO:</strong> ${d.prep}<br><strong>2. ASPIRAR:</strong> ${fmt(ml)} mL da solução reconstituída/pronta.<br><strong>3. DILUIR EM:</strong> ${d.dil}<br><strong>4. TEMPO:</strong> ${d.tempo}<br><strong>5. BOMBA DE INFUSÃO:</strong> ${d.bomba}<br><strong>6. ADMINISTRAÇÃO:</strong> ${d.direct}</div><div class="warn">Confirmar alergias, função renal/hepática, idade neonatal, indicação clínica e protocolo institucional antes de administrar.</div></article>`;
 const dexConc=4, hyd100Conc=50, predConc=3;
 if($('cortCards')) $('cortCards').innerHTML=[
  card('Dexametasona IV/IM','Manual: 0,5–20 mg/dia conforme patologia',fmt(Math.min(.6*p,10)/dexConc),'mL',`Exemplo operacional 0,6 mg/kg (máx. 10 mg): ${fmt(Math.min(.6*p,10))} mg. Apresentação 4 mg/mL.`,'','A dose varia conforme indicação; o Manual não define uma única dose pediátrica mg/kg para todas as condições.'),
  card('Hidrocortisona IV/IM','2–6 mg/kg/dose 6/6–8/8 h',fmt((2*p)/hyd100Conc),'mL',`Dose mínima da faixa: ${fmt(2*p)} mg. FA 100 mg reconstituído com 2 mL = 50 mg/mL.`,'Faixa: '+fmt(2*p)+'–'+fmt(6*p)+' mg/dose.','Selecionar a dose conforme indicação clínica.'),
  card('Prednisolona VO','0,14–2 mg/kg/dia, 1–4 administrações',fmt((1*p)/predConc),'mL/dia',`Exemplo 1 mg/kg/dia: ${fmt(p)} mg = ${fmt(p/predConc)} mL da solução 3 mg/mL.`,'','A dose deve ser individualizada conforme indicação.'),
  card('Prednisona VO','0,14–2 mg/kg/dia, 1–4 administrações',fmt(p/20),'comprimidos de 20 mg/dia',`Exemplo 1 mg/kg/dia = ${fmt(p)} mg/dia.`,'','Comprimido 20 mg; avaliar viabilidade de fracionamento.'),
  card('Betametasona IM','Manual: 1 mL IM profunda, ajustável',1,'mL',`Apresentação institucional: associação de betametasona injetável.`,'','Não converter automaticamente para mg/kg: manual não fornece esquema pediátrico por peso para esta apresentação.')
 ].join('');
 const amo=50, amoclav=50, azi=40, cefa=50, para=200, ibu=50, metro=40, brom=4;
 if($('ambCards')) $('ambCards').innerHTML=[
  card('Amoxicilina suspensão','REMUME 50 mg/mL • exemplo 50 mg/kg/dia em 3 doses',fmt((50*p/3)/amo),'mL 8/8 h',`Dose do exemplo: ${fmt(50*p/3)} mg/dose.`,'','Selecionar dose/duração conforme diagnóstico.'),
  card('Amoxicilina + clavulanato','REMUME 50 + 12,5 mg/mL • cálculo pelo componente amoxicilina',fmt((50*p/3)/amoclav),'mL 8/8 h',`Exemplo 50 mg/kg/dia de amoxicilina em 3 doses.`,'','A dose e duração variam conforme foco; considerar carga de clavulanato.'),
  card('Azitromicina suspensão','REMUME 40 mg/mL • 10 mg/kg D1; 5 mg/kg D2–D5',fmt(Math.min(10*p,500)/azi),'mL no D1',`D2–D5: ${fmt(Math.min(5*p,250)/azi)} mL 1x/dia.`,'','Usar somente quando houver indicação de macrolídeo.'),
  card('Cefalexina suspensão','REMUME 50 mg/mL • exemplo 50 mg/kg/dia em 4 doses',fmt((50*p/4)/cefa),'mL 6/6 h',`Dose do exemplo: ${fmt(50*p/4)} mg/dose.`,'','Dose/duração dependem do foco.'),
  card('Benzoilmetronidazol suspensão','REMUME 40 mg/mL',fmt((7.5*p)/metro),'mL por dose',`Exemplo operacional 7,5 mg/kg/dose = ${fmt(7.5*p)} mg.`,'','Indicação, intervalo e duração devem ser definidos pelo diagnóstico.'),
  card('Paracetamol solução oral','REMUME 200 mg/mL • 10–15 mg/kg/dose',fmt((15*p)/para),'mL por dose',`Calculado 15 mg/kg = ${fmt(15*p)} mg.`,'','Respeitar dose diária máxima e função hepática.'),
  card('Ibuprofeno suspensão oral','REMUME 50 mg/mL • 10 mg/kg/dose',fmt((10*p)/ibu),'mL por dose',`Dose ${fmt(10*p)} mg. Sem conversão em gotas.`,'','Evitar em desidratação/insuficiência renal; considerar idade mínima.'),
  card('Bromoprida solução oral','REMUME 4 mg/mL',Number.isFinite(a)&&a>=1?fmt((p/24)):'—','mL',Number.isFinite(a)&&a>=1?`Referência operacional existente: 1 gota/kg, considerando 24 gotas/mL.`:'Não calcular automaticamente em <1 ano.','','Uso pediátrico exige cautela; validar indicação.')
 ].join('');
}
function calcular(){
 const p=parseFloat($('peso').value), a=parseFloat($('idade').value);

 // ANTÍDOTOS — Manual Farmacoterapêutico institucional
 if($('antidotoCards')){
   const idadeMeses = Number.isFinite(a) ? Math.round(a*12) : 0;
   let flumHtml = '';
   if(idadeMeses >= 12){
     const flumDose = Math.min(0.01*p,0.2);
     const flumMl = flumDose/0.1;
     const flumMaxTotal = Math.min(1,0.05*p);
     flumHtml = card(
       'Flumazenil — antagonista de benzodiazepínicos',
       'Crianças >1 ano: 0,01 mg/kg IV • máx. 0,2 mg/dose • repetir a cada 1 min até resposta',
       fmt(flumMl,2),'mL por dose',
       `Dose calculada: ${fmt(flumDose,3)} mg = ${fmt(flumMl,2)} mL da apresentação 0,1 mg/mL. Dose máxima total: ${fmt(flumMaxTotal,3)} mg.`,
       'Administração IV lenta em 15–30 s. Não necessita diluição; se necessário, pode ser diluído em SF 0,9%, SG 5% ou Ringer lactato.',
       'Pode precipitar convulsões, especialmente em uso crônico de benzodiazepínicos, epilepsia ou intoxicação mista com pró-convulsivantes. Usar em ambiente monitorado.'
     );
   } else {
     flumHtml = card(
       'Flumazenil — antagonista de benzodiazepínicos',
       'Manual institucional fornece posologia pediátrica apenas para crianças maiores de 1 ano.',
       '—','',
       'Apresentação: ampola 5 mL — 0,1 mg/mL.',
       'Não gerar dose automática para ≤1 ano com base neste manual.',
       'Confirmar referência/protocolo específico antes do uso.'
     );
   }

   let nalDose, nalText;
   const isNeonate = (a === 0 && idadeMeses === 0);
   if(isNeonate){
     nalDose = 0.1*p;
     nalText = 'Recém-nascido: 0,1 mg/kg IV, IM ou SC; repetir conforme necessário a cada 2–3 min.';
   } else if(a > 5 || p > 20){
     nalDose = 2;
     nalText = 'Crianças >5 anos OU >20 kg: 2 mg IV.';
   } else {
     nalDose = 0.1*p;
     nalText = 'Crianças até 5 anos e ≤20 kg: 0,1 mg/kg IV.';
   }
   const nalMlAmp = nalDose/0.4;
   const nalDilConc = 0.4/10; // 0.4 mg in total 10 mL after adding 9 mL SF
   const nalMlDil = nalDose/nalDilConc;
   const nalHtml = card(
     'Naloxona — antagonista de opioides',
     nalText,
     fmt(nalDose,3),'mg',
     `Apresentação: ampola 1 mL — 0,4 mg/mL. Volume da ampola correspondente à dose: ${fmt(nalMlAmp,2)} mL.`,
     `Para IV lento, o manual orienta diluir a ampola em 9 mL de SF 0,9% (volume final 10 mL = 0,04 mg/mL). Nessa diluição: administrar ${fmt(nalMlDil,2)} mL para a dose calculada. Administração IV lenta; também pode ser IM/SC conforme faixa indicada. Para infusão contínua: diluir em 100 mL de SF 0,9% ou SG 5%.`,
     'A duração da naloxona pode ser menor que a do opioide: manter monitorização e considerar redoses. Pode precipitar síndrome de abstinência aguda.'
   );
   $('antidotoCards').innerHTML = flumHtml + nalHtml;
 }

 const ids=['pcrCards','rsiCards','anaCards','asmaCards','sepseCards','convCards','electCards','fluidCards','painCards','antiemCards','sedCards','abxCards','infCards','equip','energia'];
 if(!(p>0)){ids.forEach((id,i)=>$(id).innerHTML=i<7?'<div class="card">Informe o peso para calcular.</div>':'');return;}

 // PCR / ARRITMIAS
 const epiMg=Math.min(0.01*p,1), epiConc=cv('c_epi_pcr',.1), epiMl=epiMg/epiConc;
 const atropMg=Math.min(Math.max(.02*p,.1),.5), atropConc=cv('c_atropina',.5), atropConc2=cv('c_atropina2',.25), atropMl=atropMg/atropConc, atropMl2=atropMg/atropConc2;
 const ad1mg=Math.min(.1*p,6), ad2mg=Math.min(.2*p,12), adConc=cv('c_adenosina',3);
 const amioMg=Math.min(5*p,300), amioConc=cv('c_amiodarona',50), amioMl=amioMg/amioConc;
 const bicMeq=p, bicMl=bicMeq; // 8.4%=1 mEq/mL
 const caMl=Math.min(.68*p,30);
 $('pcrCards').innerHTML=[
   card('Epinefrina — PCR','0,01 mg/kg IV/IO a cada 3–5 min • máx. 1 mg',fmt(epiMl),'mL',
`Dose: ${fmt(epiMg,3)} mg. <strong>Preparo para PCR:</strong> usar epinefrina 1 mg/mL (1:1.000): aspirar <strong>1 mL</strong> + adicionar <strong>9 mL de SF 0,9%</strong> → volume final <strong>10 mL</strong> = concentração <strong>0,1 mg/mL (1:10.000)</strong>. Administrar ${fmt(epiMl,2)} mL da solução preparada.`,
'','Priorizar IV/IO; administrar precocemente em ritmos não chocáveis.'),
   card('Atropina — bradicardia vagal/BAV','0,02 mg/kg IV/IO • mín. 0,1 mg • máx. 0,5 mg/dose',
`${fmt(atropMg,3)} mg`,'',
`Apresentação ${fmt(atropConc,2)} mg/mL → <strong>${fmt(atropMl,2)} mL</strong><br>Apresentação ${fmt(atropConc2,2)} mg/mL → <strong>${fmt(atropMl2,2)} mL</strong><br>Pode repetir 1 vez.`,
'','Não é tratamento rotineiro da bradicardia por hipóxia.'),
   card('Adenosina — 1ª dose','0,1 mg/kg IV/IO • máx. 6 mg',fmt(ad1mg/adConc),'mL',`Dose: ${fmt(ad1mg)} mg. Concentração configurada: ${fmt(adConc,3)} mg/mL. Bolus extremamente rápido + flush.`),
   card('Adenosina — 2ª dose','0,2 mg/kg IV/IO • máx. 12 mg',fmt(ad2mg/adConc),'mL',`Dose: ${fmt(ad2mg)} mg. Bolus extremamente rápido + flush.`),
   card('Amiodarona — FV/TV sem pulso refratária','5 mg/kg IV/IO • máx. 300 mg por dose',fmt(amioMl),'mL',`Dose: ${fmt(amioMg)} mg. Concentração configurada: ${fmt(amioConc,2)} mg/mL.`,`Na TV/SVT com pulso, a administração é lenta (20–60 min) e deve haver consulta especializada.`),
   card('Bicarbonato de sódio 8,4%','1 mEq/kg = 1 mL/kg',fmt(bicMl),'mL',`Dose: ${fmt(bicMeq)} mEq.`,'','NÃO usar rotineiramente na PCR. Reservar para circunstâncias específicas, como hipercalemia ou toxicidade por bloqueador de canal de sódio.'),
   card('Gluconato de cálcio 10% — hipercalemia','0,68 mL/kg IV/IO • máx. 30 mL',fmt(caMl),'mL','Administrar lentamente com monitorização cardíaca; preferível em acesso periférico.','','NÃO usar cálcio rotineiramente na PCR. Não administrar simultaneamente com bicarbonato.')
 ].join('');

 // RSI
 const ketConc=cv('c_cetamina',50), ketDose=1.5*p, ketVol=ketDose/ketConc;
 const rocConc=cv('c_rocuronio',10), rocDose=1.2*p, rocVol=rocDose/rocConc;
 const fentConc=cv('c_fentanil',50), fentDose=2*p, fentVol=fentDose/fentConc;
 const atrIot=.02*p, atrIotVol=atrIot/atropConc;
 const suxConc=cv('c_succ',10), suxDose=2*p, suxVol=suxDose/suxConc;
 const etoConc=cv('c_etomidato',2), etoDose=Math.min(.3*p,20), etoVol=etoDose/etoConc;
 const rsiMidDose=.2*p;
 const rsiMidConcLt1=.5, rsiMidMlLt1=rsiMidDose/rsiMidConcLt1;
 const rsiMidConcGe1=1, rsiMidMlGe1=rsiMidDose/rsiMidConcGe1;
 const rsiFenDose=2*p, rsiFenConc=(Number.isFinite(a)&&a<1)?5:10, rsiFenMl=rsiFenDose/rsiFenConc;
 $('rsiCards').innerHTML=[
   card('Cetamina — indução','0,5–2 mg/kg IV/IO • selecionado 1,5 mg/kg',fmt(ketVol),'mL',`Dose: ${fmt(ketDose)} mg da concentração configurada ${fmt(ketConc,2)} mg/mL.`,'','Reduzir dose em choque/instabilidade hemodinâmica.'),
   card('Midazolam — sequência rápida <1 ano',
        '0,1–0,5 mg/kg IV/IO • selecionado 0,2 mg/kg',
        Number.isFinite(a)&&a<1?fmt(rsiMidMlLt1):'—','mL',
        Number.isFinite(a)&&a<1
          ? `Dose: ${fmt(rsiMidDose)} mg. Preparo: 1 mL de midazolam 5 mg/mL + 9 mL de SF 0,9% → 10 mL a 0,5 mg/mL. Administrar ${fmt(rsiMidMlLt1)} mL da solução preparada.`
          : 'Aplicável somente para menores de 1 ano.',
        '',
        'Reduzir dose em choque/instabilidade hemodinâmica e titular conforme resposta clínica.'),
   card('Midazolam — sequência rápida ≥1 ano',
        '0,1–0,5 mg/kg IV/IO • selecionado 0,2 mg/kg',
        Number.isFinite(a)&&a>=1?fmt(rsiMidMlGe1):'—','mL',
        Number.isFinite(a)&&a>=1
          ? `Dose: ${fmt(rsiMidDose)} mg. Preparo: 2 mL de midazolam 5 mg/mL + 8 mL de SF 0,9% → 10 mL a 1 mg/mL. Administrar ${fmt(rsiMidMlGe1)} mL da solução preparada.`
          : 'Aplicável somente para crianças com 1 ano ou mais.',
        '',
        'Reduzir dose em choque/instabilidade hemodinâmica e titular conforme resposta clínica.'),
   card('Etomidato — sedação/indução em trauma',
        '0,3 mg/kg IV/IO • apresentação 2 mg/mL • máximo 20 mg',
        fmt(etoVol,2),'mL',
        `Administrar ${fmt(etoVol,2)} mL = ${fmt(etoDose,2)} mg. Cálculo prático: peso × 0,15 mL/kg. Máximo 10 mL.`,
        '',
        'Considerar especialmente quando se busca maior estabilidade hemodinâmica; seguir protocolo institucional de RSI/trauma.'),
   card('Rocurônio — bloqueio neuromuscular','1,2 mg/kg IV/IO (faixa de emergência 1,2–1,6 mg/kg)',fmt(rocVol),'mL',`Dose: ${fmt(rocDose)} mg da concentração configurada ${fmt(rocConc,2)} mg/mL.`,'','Preparar sedação pós-IOT antes do bloqueio sempre que possível.'),
   card('Fentanil — adjuvante','1–5 mcg/kg IV/IO • selecionado 2 mcg/kg',fmt(rsiFenMl),'mL',
        `Dose: ${fmt(rsiFenDose)} mcg. ${Number.isFinite(a)&&a<1?'Neonato/lactente <1 ano: 1 mL de fentanil 50 mcg/mL + 9 mL SF = 5 mcg/mL.':'Pediátrico ≥1 ano: 2 mL de fentanil 50 mcg/mL + 8 mL SF = 10 mcg/mL.'} Administrar ${fmt(rsiFenMl)} mL da solução preparada lentamente.`,
        '', 'Adjuvante; não substitui agente de indução. Cautela em instabilidade e rigidez torácica com administração rápida/doses elevadas.'),
   card('Atropina — pré-medicação opcional','0,02 mg/kg IV/IO • sem dose mínima para IOT',
`${fmt(atrIot,3)} mg`,'',
`Apresentação ${fmt(atropConc,2)} mg/mL → <strong>${fmt(atrIot/atropConc,2)} mL</strong><br>Apresentação ${fmt(atropConc2,2)} mg/mL → <strong>${fmt(atrIot/atropConc2,2)} mL</strong>.`,
'','Pode ser considerada para prevenção de bradicardia peri-intubação; não é obrigatória de rotina.'),
   card('Succinilcolina — alternativa ao rocurônio','2 mg/kg IV/IO quando selecionada',fmt(suxVol),'mL',`Dose: ${fmt(suxDose)} mg na concentração configurada ${fmt(suxConc,2)} mg/mL.`,'','Evitar quando houver risco de hipercalemia, doença neuromuscular ou hipertermia maligna; rocurônio é o padrão preferido em muitos protocolos.')
 ].join('');


 // ANAFILAXIA
 const epiImConc=cv('c_epi_im',1), anaEpiMg=Math.min(Math.max(.01*p,.1),.5), anaEpiMl=anaEpiMg/epiImConc;
  const anaFluid=20*p;
 $('anaCards').innerHTML=[
   card('Epinefrina IM 1:1000 — primeira linha',`0,01 mg/kg IM • concentração configurada ${fmt(epiImConc,2)} mg/mL • máx. 0,5 mg`,fmt(anaEpiMl),'mL',
        `Dose: ${fmt(anaEpiMg,3)} mg IM na face anterolateral da coxa. Repetir a cada 5 min se necessário.`,
        '', p<10?'Volumes abaixo de 0,1 mL são propensos a erro; o guideline utiliza 0,1 mL em crianças pequenas.':''),
   card('Cristaloide isotônico — choque','20 mL/kg IV/IO, com reavaliação',fmt(anaFluid,0),'mL',
        'SF 0,9% ou cristalóide isotônico. Reavaliar perfusão, ausculta pulmonar e resposta após cada bolus.',
        '', 'Adrenalina IM vem antes de anti-histamínico, corticoide ou medicação para asma quando há anafilaxia.')
 ].join('');

 // ASMA AGUDA
 const puffsSal=(Number.isFinite(a)&&a<6)?6:12;
 const puffsIpr=(Number.isFinite(a)&&a<6)?2:4;
 const mgso4Ml=Math.min(.1*p,4), mgso4Mg=mgso4Ml*500;
 $('asmaCards').innerHTML=[
   card('Salbutamol MDI 100 mcg/puff','dose de resgate via espaçador',puffsSal,'puffs',
        `${Number.isFinite(a)&&a<6?'Criança <6 anos':'Criança ≥6 anos'}: administrar um puff por vez pelo espaçador.`,
        '', 'Em crise moderada/grave, a frequência depende da gravidade e resposta clínica.'),
   card('Ipratrópio MDI — crise grave','21–40 mcg/puff conforme produto institucional',puffsIpr,'puffs',
        `${Number.isFinite(a)&&a<6?'2 puffs (<6 anos)':'4 puffs (≥6 anos)'}; pode ser repetido conforme protocolo de crise grave.`,
        '', 'Confirmar a concentração do dispositivo disponível na unidade.'),
   card('Sulfato de magnésio 50% IV','50 mg/kg = 0,1 mL/kg • máximo 8 mmol = 4 mL da solução 50%',fmt(mgso4Ml),'mL',
        `Dose: ${fmt(mgso4Mg,0)} mg. Solução 50% = 500 mg/mL. Diluir conforme protocolo institucional e infundir em ~20 min.`,
        '', 'Reservado para asma grave/ameaça à vida ou resposta inadequada à terapia inicial.')
 ].join('');

 // SEPSE
 const sepBolus10=10*p, sepBolus20=20*p, sep40=40*p;
 const sepCtxMg=Math.min(100*p,4000);
 const sepCtxReconMl=sepCtxMg/100;   // ceftriaxona reconstituída 100 mg/mL
 const sepCtxFinalMl=sepCtxMg/40;   // concentração final <=40 mg/mL
 const sepAzMg=Math.min(10*p,500);
 const sepAzReconMl=sepAzMg/100;    // azitro 100 mg/mL após reconstituição
 const sepAzFinalMl=sepAzMg/2;      // 2 mg/mL para 1 h
 $('sepseCards').innerHTML=[
   card('Ringer Lactato — bolus inicial','10–20 mL/kg IV/IO com reavaliação após cada alíquota',
        `${fmt(sepBolus10,0)}–${fmt(sepBolus20,0)}`,'mL',
        `RL 10 mL/kg = ${fmt(sepBolus10,0)} mL. RL 20 mL/kg = ${fmt(sepBolus20,0)} mL. Administrar rapidamente conforme perfusão e reavaliar após cada bolus.`,
        `Volume cumulativo de 40 mL/kg = ${fmt(sep40,0)} mL.`,
        'Reduzir/interromper fluidos se surgirem sinais de sobrecarga; considerar vasoativo precoce se choque persistente.'),
   card('Ceftriaxona EV — sepse ≥2 meses','100 mg/kg/dia EV • máx. 4 g/dia',
        fmt(sepCtxFinalMl),'mL volume final',
        `Dose: ${fmt(sepCtxMg,0)} mg. Reconstituir a 100 mg/mL → retirar ${fmt(sepCtxReconMl,2)} mL. Diluir para concentração final ≤40 mg/mL → volume final mínimo ${fmt(sepCtxFinalMl,1)} mL.`,
        'Infundir em pelo menos 30 min; em neonatos, usar protocolo neonatal específico e tempo maior conforme padronização.',
        'Não extrapolar este esquema para RN; verificar idade, foco, alergias, função renal/hepática e protocolo institucional.'),
   card('Ceftriaxona EV — meningite bacteriana ≥29 dias','80–100 mg/kg/dia EV • dose única ou dividida 12/12 h • máx. 4 g/dia',
        `${fmt(Math.min(80*p,4000),0)}–${fmt(Math.min(100*p,4000),0)}`,'mg/dia',
        `Faixa diária: ${fmt(Math.min(80*p,4000),0)}–${fmt(Math.min(100*p,4000),0)} mg/dia. Para 100 mg/kg/dia: ${fmt(sepCtxMg,0)} mg/dia. Se dividido 12/12 h: ${fmt(sepCtxMg/2,0)} mg/dose. Reconstituir o frasco de 1 g com 10 mL de água para injeção (100 mg/mL): para a dose de 100 mg/kg/dia, aspirar ${fmt(sepCtxReconMl,2)} mL/dia; se 12/12 h, aspirar ${fmt(sepCtxReconMl/2,2)} mL por dose.`,
        'Para infusão EV, diluir a dose em 50–100 mL de SF 0,9% ou SG 5% e infundir em aproximadamente 30 min.',
        'Meningite bacteriana: esquema do Manual Farmacoterapêutico para crianças ≥29 dias. Não administrar concomitantemente com soluções contendo cálcio; atenção especial a neonatos.'),
   card('Azitromicina EV — quando houver indicação de cobertura para atípicos','10 mg/kg EV 24/24 h • máx. 500 mg/dia',
        fmt(sepAzFinalMl),'mL volume final',
        `Dose: ${fmt(sepAzMg,0)} mg. Reconstituir 500 mg com 4,8 mL de água para injeção → 100 mg/mL. Retirar ${fmt(sepAzReconMl,2)} mL e diluir a 2 mg/mL → volume final ${fmt(sepAzFinalMl,1)} mL.`,
        'Infundir em 1 hora. Alternativa: 1 mg/mL em 3 horas.',
        'Usar somente quando houver indicação clínica de macrolídeo; não substitui a antibioticoterapia empírica principal da sepse.'),
   card('Antibiótico empírico — meta de tempo','após reconhecimento de sepse/choque','≤ 1','hora',
        'Coletar culturas quando possível sem atrasar a antibioticoterapia. Selecionar esquema conforme idade, foco, alergias e epidemiologia local.'),
   card('Epinefrina — choque com baixo débito','infusão titulada',fmt(.05*p*60/20),'mL/h',
        'Exemplo com concentração 1 mg/50 mL = 20 mcg/mL e dose inicial 0,05 mcg/kg/min.'),
   card('Norepinefrina — choque vasoplégico','infusão titulada',fmt(.05*p*60/20),'mL/h',
        'Exemplo com concentração 1 mg/50 mL = 20 mcg/mL e dose inicial 0,05 mcg/kg/min.',
        '', 'A escolha do vasoativo depende da fisiologia do choque e deve ser titulada ao efeito.')
 ].join('');

 // ELETRÓLITOS — doses, diluições e bomba
 const caHyperMl=Math.min(.68*p,30), caHyperMmol=caHyperMl*.22;
 const caHypoMl=.5*p, caHypoMmol=caHypoMl*.22;
 const caDilVol=caHypoMl*2; // equal volume dilution -> 0.11 mmol/mL
 const g10Hyper=5*p, insU=Math.min(.1*p,10);
 const kDose=.3*p, kPeripheralVol=kDose/0.04, kRate=kPeripheralVol/1;
 const mgMmol=Math.min(.2*p,8), mgStockMl=mgMmol/2, mgFinalVol=Math.max(mgMmol/.8,mgStockMl), mgDil=mgFinalVol-mgStockMl;
 const phosMmol=.36*p, phosPeriphVol=phosMmol/.05;
 $('electCards').innerHTML=[
   card('Hipercalemia — gluconato de cálcio 10%','0,68 mL/kg • máx. 30 mL',fmt(caHyperMl),'mL',
        `Dose ≈ ${fmt(caHyperMmol,2)} mmol. Emergência/ECG instável: pode ser administrado sem diluir em 2–5 min. Se estável: administrar em 15–20 min sob monitorização cardíaca.`,
        '', 'Não reduz o potássio. Não administrar simultaneamente com bicarbonato; vigiar extravasamento.'),
   card('Hipocalcemia sintomática — gluconato de cálcio 10%','0,5 mL/kg IV',fmt(caHypoMl),'mL',
        `Dose ≈ ${fmt(caHypoMmol,2)} mmol. Para infusão não emergencial: adicionar volume igual de SF 0,9% ou SG5%, resultando em ~${fmt(caDilVol)} mL a 0,11 mmol/mL ou menos.`,
        `Bomba: infundir em 10–60 min conforme gravidade.`, 'Monitorização cardíaca contínua. Não usar IM/SC e não coadministrar com bicarbonato.'),
   card('Hipocalemia — KCl IV','dose exemplo 0,3 mmol/kg',fmt(kDose,2),'mmol',
        `Via periférica: concentração usual máxima 40 mmol/L (0,04 mmol/mL). Para esta dose, volume mínimo ≈ ${fmt(kPeripheralVol,0)} mL de solução final. Preferir bolsa pré-misturada.`,
        `Área geral: usar taxa institucional segura; em terapia intensiva, guideline admite até 0,4 mmol/kg/h por 1–2 h com monitorização e geralmente acesso central.`,
        'KCl IV somente em bomba. Nunca administrar em bolus nem fazer flush da linha. Confirmar diurese/função renal e repetir K+.'),
   card('Hipomagnesemia sintomática — MgSO₄ 50%','0,1–0,2 mmol/kg IV • selecionado 0,2 mmol/kg • máx. 8 mmol',fmt(mgStockMl),'mL de MgSO₄ 50%',
        `MgSO₄ 50% = 2 mmol/mL. Dose: ${fmt(mgMmol,2)} mmol. Diluir para ≤0,8 mmol/mL: volume final mínimo ${fmt(mgFinalVol,1)} mL (${fmt(mgStockMl,2)} mL MgSO₄ + ${fmt(mgDil,2)} mL de diluente compatível).`,
        `Bomba: doses até 8 mmol em pelo menos 2 h; máximo 0,5 mmol/kg/h. Situações emergenciais específicas podem exigir tempo menor conforme protocolo.`,
        'Monitorar PA, FR, diurese e magnésio. Infusão rápida pode causar hipotensão, depressão respiratória e arritmias.'),
   card('Hipofosfatemia — fosfato IV','0,36 mmol/kg',fmt(phosMmol,2),'mmol',
        `Via periférica: diluir a ≤0,05 mmol/mL → volume final mínimo ${fmt(phosPeriphVol,0)} mL. Via central: ≤0,12 mmol/mL.`,
        'Bomba: infundir em 6 horas; não exceder 0,2 mmol/kg/h ou 10 mmol/h.',
        'Considerar conteúdo de potássio da preparação; monitorar fósforo, cálcio, potássio e função renal.'),
   card('Hipercalemia grave — glicose/insulina','Glicose 10% 5 mL/kg + insulina regular 0,1 U/kg',fmt(g10Hyper,0),'mL SG10%',
        `Insulina: ${fmt(insU,2)} U (máx. 10 U). Usar protocolo institucional para preparo seguro da insulina.`,
        '', 'Monitorar glicemia a cada 30–60 min e potássio/ECG.')
 ].join('');

 // CONVULSÃO
 const midConc=cv('c_midazolam',5), midIVmg=Math.min(.15*p,10), midIVml=midIVmg/midConc; const diaMg=Math.min(.3*p,10), diaMl=diaMg/5; const pheMg=Math.min(20*p,2000);
 const phenMg=Math.min(20*p,1000);
 $('convCards').innerHTML=[
   card('Midazolam IV/IM/IO — 1ª linha','0,15 mg/kg • máx. 10 mg',fmt(midIVml),'mL',`Dose: ${fmt(midIVmg)} mg. Concentração configurada: ${fmt(midConc,2)} mg/mL.`),   card('Diazepam IV/IO — alternativa','0,3 mg/kg • máx. 10 mg',fmt(diaMl),'mL',`Dose: ${fmt(diaMg)} mg. Considerando 5 mg/mL. Não usar IM.`),   card('Fenitoína — 2ª linha','20 mg/kg IV/IO • máx. 2 g • apresentação 50 mg/mL',fmt(pheMg/50),'mL',
        `Dose: ${fmt(pheMg)} mg = ${fmt(pheMg/50)} mL de fenitoína 50 mg/mL. Usar sem diluir OU diluir somente em SF 0,9% mantendo concentração ≥5 mg/mL. Se preparar a 5 mg/mL: volume final ${fmt(pheMg/5)} mL.`,
        `Infundir em bomba a 1 mg/kg/min (máx. 50 mg/min). Tempo mínimo calculado: ${fmt(Math.max(pheMg/Math.min(p,50),1),0)} min.`,
        'Monitorização contínua de ECG/PA/respiração. Usar veia calibrosa; solução com glicose é incompatível. Filtrar se possível (0,2–0,5 μm).'),
   card('Fenobarbital — alternativa 2ª linha','20 mg/kg IV/IO • máx. 1 g • apresentação 100 mg/mL',fmt(phenMg/100),'mL',
`Dose: ${fmt(phenMg)} mg = ${fmt(phenMg/100)} mL da solução 100 mg/mL. Diluir para 20 mg/mL ou menos → volume final mínimo ${fmt(phenMg/20)} mL; infundir ≥30 min.`,'','Monitorar respiração, PA e sedação.')
 ].join('');

 // FLUIDS
 const maint=calcMaint(p), maintDay=maint*24, twoThird=maint*2/3;
 const bolus10=10*p, bolus20=20*p, deficit5=.05*p*1000, deficit5hr=deficit5/24;
 $('fluidCards').innerHTML=[
   card('Manutenção plena — regra 4-2-1','Holliday-Segar',fmt(maint),'mL/h',`${fmt(maintDay,0)} mL/dia.`),
   card('2/3 da manutenção','frequentemente apropriado na criança agudamente enferma',fmt(twoThird),'mL/h','Reavaliar conforme estado volêmico, sódio, glicemia e perdas.','','Não aplicar automaticamente em desidratação, choque ou condições que exigem protocolo específico.'),
   card('Bolus de cristalóide — choque','SF 0,9% / solução isotônica 10–20 mL/kg',fmt(bolus10,0)+'–'+fmt(bolus20,0),'mL','Administrar rapidamente e reavaliar após cada bolus.','','Se >20 mL/kg forem necessários, envolver clínico sênior; em choque séptico/cardiogênico individualizar agressivamente.'),
   card('Reposição de déficit de 5% em 24 h','50 mL/kg/24 h',fmt(deficit5hr),'mL/h',`Déficit estimado de 5%: ${fmt(deficit5,0)} mL/24 h, além da manutenção.`,'','A estimativa clínica do percentual de desidratação é imprecisa; reavaliar seriamente e usar peso pré-mórbido quando disponível.'),
   card('Taxa inicial: manutenção + déficit 5%','exemplo de reidratação IV',fmt(maint+deficit5hr),'mL/h',`Manutenção ${fmt(maint)} + déficit ${fmt(deficit5hr)} mL/h.`,'','Não usar esta fórmula em DKA, hipernatremia/hiponatremia importante, cardiopatia, nefropatia, trauma/queimadura ou neonatos.')
 ].join('');

 // PAIN / ANTIPYRETICS
 const paraMg=Math.min(15*p,1000), paraConc=cv('c_paracetamol_vo',200);
 const ibuMg=Math.min(10*p,400), ibuConc=cv('c_ibuprofeno',20);
 const morphMg=.1*p, morphConc=cv('c_morfina',10);
 const dipDose=20*p, dipVoConc=cv('c_dipirona_vo',500), dipIvConc=cv('c_dipirona',500);
 $('painCards').innerHTML=[
   card('Paracetamol VO','15 mg/kg/dose a cada 4–6 h • máx. 1 g/dose',fmt(paraMg/paraConc),'mL',
`Dose ${fmt(paraMg)} mg. ${fmt(paraMg/paraConc)} mL ≈ ${fmt((paraMg/paraConc)*20,0)} gotas (referência 20 gotas/mL).`,'','Confirmar o gotejador da apresentação disponível; respeitar dose diária máxima e função hepática.'),
   card('Ibuprofeno VO (>3 meses)','10 mg/kg/dose a cada 6–8 h • máx. 400 mg/dose',fmt(ibuMg/ibuConc),'mL',
`Dose ${fmt(ibuMg)} mg. Volume: ${fmt(ibuMg/ibuConc)} mL da concentração configurada ${fmt(ibuConc,1)} mg/mL.`,`Máx. usual 30 mg/kg/dia.`,'Evitar em desidratação/insuficiência renal.'),
   card('Dipirona VO','10–20 mg/kg/dose • selecionado 20 mg/kg',fmt(dipDose/dipVoConc),'mL',
`Dose ${fmt(dipDose)} mg. ${fmt(dipDose/dipVoConc)} mL ≈ ${fmt((dipDose/dipVoConc)*20,0)} gotas (referência 20 gotas/mL).`,'','Confirmar gotejador, idade mínima e contraindicações.'),
   card('Dipirona IM/EV','10–20 mg/kg/dose • selecionado 20 mg/kg',fmt(dipDose/dipIvConc),'mL',`Dose: ${fmt(dipDose)} mg. Apresentação ${fmt(dipIvConc,1)} mg/mL. EV: administrar lentamente.`,'','Respeitar contraindicações e protocolo institucional; monitorar hipotensão em uso EV.'),
   card('Morfina IV — dor moderada/grave','0,1 mg/kg IV titulada',fmt(morphMg/morphConc),'mL',`Apresentação ${fmt(morphConc,1)} mg/mL: ${fmt(morphMg/morphConc)} mL antes da diluição institucional.`,'','Monitorizar sedação e ventilação; titular ao efeito.')
 ].join('');


 // ANTIEMÉTICOS
 let ondDose=0;
 if(p>=8 && p<=15) ondDose=2;
 else if(p>15 && p<=30) ondDose=4;
 else if(p>30) ondDose=8;
 const ondConc=cv('c_ondansetrona',2), ondMl=ondDose/ondConc;
 const metConc=cv('c_metoclopramida',5), metMg=Math.min(.1*p,10), metMl=metMg/metConc;
 const bromConc=cv('c_bromoprida',4), bromDrops=p, bromMl=bromDrops/24, bromMg=bromMl*bromConc;
 $('antiemCards').innerHTML=[
   card('Ondansetrona EV — >6 meses','dose inicial por peso: 8–15 kg 2 mg • 15–30 kg 4 mg • >30 kg 8 mg',
        ondDose?fmt(ondMl):'—','mL',
        ondDose?`Dose: ${fmt(ondDose)} mg. Concentração ${fmt(ondConc,2)} mg/mL.`:'Para peso <8 kg, não aplicar automaticamente este esquema por faixas.',
        '', 'Cautela em QT prolongado e alterações eletrolíticas.'),
   card('Bromoprida VO — somente >1 ano','bula pediátrica: 1–2 gotas/kg, 3x/dia • calculado 1 gota/kg',Number.isFinite(a)&&a>=1?fmt(bromMl):'—','mL',
        Number.isFinite(a)&&a>=1?`${fmt(bromDrops,0)} gotas ≈ ${fmt(bromMg,2)} mg (4 mg/mL; 24 gotas/mL).`:'Não calcular para ≤1 ano.',
        '', 'Contraindicada <1 ano. Evitar em epilepsia, feocromocitoma, hemorragia/obstrução/perfuração GI e com fármacos que aumentem reações extrapiramidais.'),
   card('Metoclopramida — uso pediátrico restrito','0,1 mg/kg/dose • máx. 10 mg',Number.isFinite(a)&&a>=1?fmt(metMl):'—','mL',
        Number.isFinite(a)&&a>=1?`Dose: ${fmt(metMg)} mg da apresentação ${fmt(metConc,1)} mg/mL. Administrar lentamente se EV.`:'Não calcular em neonato/lactente <1 ano.',
        '', 'Maior risco de reações extrapiramidais em crianças; evitar em epilepsia, Parkinson, feocromocitoma, sangramento/obstrução/perfuração GI e história de distonia/discinesia tardia. Não é antiemético de rotina.')
 ].join('');

 // SEDAÇÃO DE PROCEDIMENTO
 const ketIVmg=1*p, ketIVml=ketIVmg/ketConc;
 const ketIMmg=4*p, ketIMml=ketIMmg/ketConc;
 const ketRepeat=.5*p, ketRepeatMl=ketRepeat/ketConc;
 $('sedCards').innerHTML=[
   card('Cetamina IV — sedação de procedimento','1 mg/kg IV inicial',fmt(ketIVml),'mL',
        `Dose inicial: ${fmt(ketIVmg)} mg da concentração configurada ${fmt(ketConc,2)} mg/mL. Pode titular com doses adicionais conforme resposta.`,
        '', 'Doses IV totais >2,5 mg/kg associam-se a mais eventos adversos; requer equipe habilitada em via aérea e monitorização.'),
   card('Cetamina IM — sedação de procedimento','4 mg/kg IM inicial',fmt(ketIMml),'mL',
        `Dose: ${fmt(ketIMmg)} mg da concentração configurada ${fmt(ketConc,2)} mg/mL. Se inadequada, o guideline permite 2 mg/kg adicional após ~10 min.`,
        '', 'Monitorização contínua e profissional dedicado à observação da via aérea/ventilação.')
 ].join('');

 // ANTIBIOTICS
 const sc='disabled';
 let ab=[];
 const amoConc=cv('c_amoxicilina',50), cefConc=cv('c_cefalexina',50);
 if(sc==='pneumonia'){
   const amo=Math.min(30*p,1000), ml=amo/amoConc;
   ab=[
    card('Amoxicilina VO — pneumonia','30 mg/kg/dose VO 8/8 h • máx. 1 g/dose',fmt(ml),'mL por dose',
      `<strong>Prescrição:</strong> administrar ${fmt(ml)} mL VO a cada 8 horas por 7 dias. Dose = ${fmt(amo)} mg/dose; suspensão ${fmt(amoConc,1)} mg/mL.`,
      '', 'Reavaliar diagnóstico, alergias e gravidade; duração pode variar conforme protocolo/diagnóstico.')
   ];
 } else if(sc==='azitro'){
   const az1=Math.min(10*p,500), az2=Math.min(5*p,250);
   // liquid concentration: if configured as a 500 mg "unit", use common suspension 40 mg/mL for usable mL.
   const azConc=40, ml1=az1/azConc, ml2=az2/azConc;
   ab=[
    card('Azitromicina VO','10 mg/kg no D1; 5 mg/kg/dia D2–D5 • máx. 500/250 mg',fmt(ml1),'mL no D1',
      `<strong>Prescrição:</strong> administrar ${fmt(ml1)} mL VO 1x/dia no primeiro dia; depois ${fmt(ml2)} mL VO 1x/dia do 2º ao 5º dia. Referência: suspensão 200 mg/5 mL (40 mg/mL). D1 = ${fmt(az1)} mg; D2–D5 = ${fmt(az2)} mg/dia.`,
      '', 'Usar apenas quando houver indicação de macrolídeo.'),
    card('Azitromicina EV','10 mg/kg EV 24/24 h • máx. 500 mg',fmt(az1/2),'mL volume final',
      `Dose ${fmt(az1)} mg. Reconstituir a 100 mg/mL e diluir a 2 mg/mL → ${fmt(az1/2)} mL; infundir em 1 hora.`)
   ];
 } else if(sc==='meningite'){
   const ctx=Math.min(100*p,4000);
   ab=[card('Ceftriaxona EV — meningite ≥2 meses','100 mg/kg/dia • máx. 4 g',fmt(ctx/40),'mL volume final',
      `Dose ${fmt(ctx)} mg. Reconstituir a 100 mg/mL: retirar ${fmt(ctx/100)} mL; diluir a ≤40 mg/mL → volume final mínimo ${fmt(ctx/40)} mL; infundir ≥30 min.`,
      '', 'Esquema neonatal deve seguir protocolo específico; considerar cobertura adicional conforme epidemiologia.')];
 } else if(sc==='sepsis'){
   const ctx=Math.min(100*p,4000);
   ab=[card('Ceftriaxona EV — sepse ≥2 meses','50–100 mg/kg/dia • calculado 100 mg/kg/dia',fmt(ctx/40),'mL volume final',
      `Dose ${fmt(ctx)} mg. Reconstituir a 100 mg/mL: ${fmt(ctx/100)} mL; diluir a ≤40 mg/mL → ${fmt(ctx/40)} mL; infundir ≥30 min.`,
      '', 'Selecionar esquema definitivo conforme idade, foco, culturas e protocolo institucional.')];
 } else if(sc==='uti'){
   const cef=Math.min(20*p,750), ml=cef/cefConc;
   ab=[card('Cefalexina VO — ITU não grave >3 meses','20 mg/kg/dose VO 8/8 h • máx. 750 mg',fmt(ml),'mL por dose',
      `<strong>Prescrição:</strong> administrar ${fmt(ml)} mL VO a cada 8 horas por 7 dias. Dose ${fmt(cef)} mg; suspensão ${fmt(cefConc,1)} mg/mL.`,
      '', 'Febre/pielonefrite, lactente pequeno ou toxemia exigem avaliação de esquema e duração específicos.')];
 } else {
   const cef=Math.min(20*p,750), ml=cef/cefConc, cz=Math.min(50*p,2000);
   ab=[
    card('Cefalexina VO — pele/partes moles','20 mg/kg/dose VO 8/8 h • máx. 750 mg',fmt(ml),'mL por dose',
      `<strong>Prescrição:</strong> administrar ${fmt(ml)} mL VO a cada 8 horas por 7 dias. Dose ${fmt(cef)} mg; suspensão ${fmt(cefConc,1)} mg/mL.`),
    card('Cefazolina EV — moderada/grave','50 mg/kg/dose IV 8/8 h • máx. 2 g',fmt(cz/20),'mL volume final',
      `Dose ${fmt(cz)} mg. Se infusão a ≤20 mg/mL → volume final mínimo ${fmt(cz/20)} mL.`)
   ];
 }
 if($('abxCards')) $('abxCards').innerHTML=ab.join('');

 // INFUSÕES
 const infusion=(nome,faixa,prep,conc,dose,unit,rate,warn='')=>card(nome,`Faixa: ${faixa} • selecionado ${fmt(dose,3)} ${unit}`,fmt(rate),'mL/h',`${prep} Concentração final: ${conc}.`,'',warn,'infusion');
 const ageOk=Number.isFinite(a)?a:null;
 const midDose=(ageOk!==null&&ageOk<.5)?10:50, midFinalConc=.2;
 const midRate=midDose*p/(midFinalConc*1000);
 const fenDose=1, fenConc=p<35?10:20, fenRate=p<35?fenDose*p/fenConc:Math.max(25,p)/fenConc;
 $('infCards').innerHTML=[
   infusion('Midazolam',ageOk!==null&&ageOk<.5?'10–60 mcg/kg/h':'10–120 mcg/kg/h','10 mg (2 mL de 5 mg/mL) completar para 50 mL','0,2 mg/mL',midDose,'mcg/kg/h',midRate,'Titular à sedação-alvo.'),
   infusion('Fentanil',p<35?'0,5–5 mcg/kg/h':'25–200 mcg/h',p<35?'500 mcg (10 mL de 50 mcg/mL) completar para 50 mL':'1.000 mcg (20 mL de 50 mcg/mL) completar para 50 mL',p<35?'10 mcg/mL':'20 mcg/mL',p<35?fenDose:Math.max(25,p),p<35?'mcg/kg/h':'mcg/h',fenRate,'Titular à analgesia/sedação.'),
   infusion('Epinefrina','0,05–0,2 mcg/kg/min','1 mg (1 mL de 1 mg/mL) completar para 50 mL','20 mcg/mL',.05,'mcg/kg/min',.05*p*60/20,'Titular ao efeito; monitorização contínua.'),
   infusion('Norepinefrina','0,05–0,2 mcg/kg/min','1 mg (1 mL de 1 mg/mL) completar para 50 mL','20 mcg/mL',.05,'mcg/kg/min',.05*p*60/20,'Titular ao efeito; monitorização contínua.'),
   infusion('Dopamina','2–10 mcg/kg/min','60 mg (12 mL de 5 mg/mL) completar para 50 mL','1,2 mg/mL',5,'mcg/kg/min',5*p*60/1200,'Em choque séptico, epinefrina/norepinefrina costumam ser preferidas conforme fisiologia.'),
   infusion('Dobutamina','2–10 mcg/kg/min','75 mg (6 mL de 12,5 mg/mL) completar para 50 mL','1,5 mg/mL',5,'mcg/kg/min',5*p*60/1500,'Titular ao efeito.')
 ].join('');

 // MATERIALS / ENERGY
 const age=Number.isFinite(a)?a:null;
 let etSem='—', etCuff='—', fix='—', faixaTot='—';

 // Esquema institucional de TOT informado:
 // RN a termo: sem cuff 3,5–4,0 | com cuff 3,0–3,5 | fixação 10–11 cm
 // 6 meses–1 ano: sem cuff 4,0–4,5 | com cuff 3,5–4,0 | fixação 11–12 cm
 // 2–4 anos: sem cuff 4,5–5,0 | com cuff 4,0–4,5 | fixação 13–15 cm
 // >5 anos: sem cuff = idade/4+4 | com cuff = idade/4+3,5 | fixação = tubo x3
 if(age===null){
   etSem='Informe idade'; etCuff='Informe idade'; fix='Informe idade'; faixaTot='—';
 } else if(age < 0.5){
   faixaTot='RN / <6 meses';
   etSem='3,5–4,0';
   etCuff='3,0–3,5';
   fix='10–11 cm';
 } else if(age >= 0.5 && age <= 1){
   faixaTot='6 meses–1 ano';
   etSem='4,0–4,5';
   etCuff='3,5–4,0';
   fix='11–12 cm';
 } else if(age > 1 && age < 2){
   faixaTot='>1–<2 anos';
   etSem='4,0–4,5';
   etCuff='3,5–4,0';
   fix='11–12 cm';
 } else if(age >= 2 && age <= 4){
   faixaTot='2–4 anos';
   etSem='4,5–5,0';
   etCuff='4,0–4,5';
   fix='13–15 cm';
 } else if(age > 4 && age <= 5){
   // transição: usar fórmula pediátrica para evitar lacuna operacional
   const sem=age/4+4, cuff=age/4+3.5;
   faixaTot='>4–5 anos';
   etSem=fmt(sem,2);
   etCuff=fmt(cuff,2);
   fix=`Sem cuff: ${fmt(sem*3,1)} cm • Com cuff: ${fmt(cuff*3,1)} cm`;
 } else {
   const sem=age/4+4, cuff=age/4+3.5;
   faixaTot='>5 anos';
   etSem=fmt(sem,2);
   etCuff=fmt(cuff,2);
   fix=`Sem cuff: ${fmt(sem*3,1)} cm • Com cuff: ${fmt(cuff*3,1)} cm`;
 }

 // Máscara laríngea / dispositivo supraglótico por peso
 let lma='—';
 if(p<5) lma='1';
 else if(p<10) lma='1,5';
 else if(p<20) lma='2';
 else if(p<30) lma='2,5';
 else if(p<50) lma='3';
 else if(p<70) lma='4';
 else if(p<100) lma='5';
 else lma='6';

 const blade=p<3?'reta 0–1':p<10?'reta 1':age==null?'Informe idade':age<2?'curva 1–2':age<6?'curva 2':age<12?'curva 2–3':'curva 3';

 $('equip').innerHTML=[
   eq('Faixa TOT',faixaTot),
   eq('TOT sem cuff',etSem),
   eq('TOT com cuff',etCuff),
   eq('Fixação lábio/gengiva',fix),
   eq('Máscara laríngea',`Tamanho ${lma}`),
   eq('Lâmina',blade),
   eq('Sonda aspiração',p<10?'6–8':'10–12')
 ].join('');

 const d1=2*p, d2=4*p, dmax=Math.min(10*p,200), cv1=.5*p, cv2=2*p;
 $('energia').innerHTML=[eq('Desfibrilação 1ª',fmt(d1)+' J'),eq('Desfibrilação 2ª',fmt(d2)+' J'),eq('Desfibrilação subsequente',fmt(dmax)+' J máx.'),eq('Cardioversão inicial',fmt(cv1)+'–'+fmt(p)+' J'),eq('Cardioversão seguinte',fmt(cv2)+' J')].join('');

 renderInfFocus();}

document.querySelectorAll('.tab').forEach(b=>b.addEventListener('click',()=>{
 document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
 document.querySelectorAll('.panel').forEach(x=>x.classList.remove('active'));
 b.classList.add('active'); $(b.dataset.tab).classList.add('active');
}));
loadPres();
initScores();
calcular();
calcPEWS();

document.addEventListener('DOMContentLoaded',()=>{ try{calcVM();}catch(e){} });

function cleanPrintText(txt){
  return (txt || '').replace(/\s+/g,' ').trim();
}

function buildPrintTable(){
  const body = document.getElementById('printDoseBody');
  const pdata = document.getElementById('printPatientData');
  if(!body || !pdata) return;

  const peso = parseFloat(document.getElementById('peso')?.value);
  const idade = parseFloat(document.getElementById('idade')?.value);

  pdata.innerHTML =
    `<strong>Peso:</strong> ${Number.isFinite(peso)?fmt(peso,2)+' kg':'—'} &nbsp;&nbsp; | &nbsp;&nbsp; `+
    `<strong>Idade:</strong> ${Number.isFinite(idade)?fmt(idade,2)+' anos':'—'} &nbsp;&nbsp; | &nbsp;&nbsp; `+
    `<strong>Data/Hora:</strong> ${new Date().toLocaleString('pt-BR')}`;

  body.innerHTML='';

  // Only clinical output panels. Settings/presentations are excluded.
  const sections = [
    ['PCR / Arritmias','pcr'],
    ['Sequência rápida / IOT','rsi'],
    ['Anafilaxia','anafilaxia'],
    ['Asma / Broncoespasmo','asma'],
    ['Sepse','sepse'],
    ['Crise convulsiva','convulsao'],
    ['Eletrólitos','eletrolitos'],
    ['Hidratação','hidratacao'],
    ['Analgesia / Antitérmicos','analgesia'],
    ['Antieméticos','antiemeticos'],
    ['Sedação de procedimento','sedacao'],
    ['Antibióticos','antibioticos'],
    ['Antídotos','antidotos'],
    ['Hipo / Hiperglicemia','glicemia'],
    ['Cetoacidose Diabética — CAD','cad'],
    ['Desidratação — OMS','desidratacao'],
    ['Queimaduras','queimaduras'],
    ['Infusões contínuas','infusoes'],
    ['Materiais / Energia','materiais'],
    ['Ventilação Mecânica','ventilacao']
  ];

  sections.forEach(([label,id])=>{
    const panel=document.getElementById(id);
    if(!panel) return;

    const cards=[...panel.querySelectorAll('.card')].filter(c=>{
      const txt=cleanPrintText(c.innerText);
      return txt && !txt.startsWith('Informe o peso');
    });

    // PEWS summary when present
    let extras=[];
    if(id==='sepse'){
      const pr=document.getElementById('pewsResult');
      if(pr) extras.push({
        name:'PEWS — deterioração clínica',
        result:cleanPrintText(pr.querySelector('.pews-score')?.innerText)+' — '+cleanPrintText(pr.querySelector('.pews-risk')?.innerText),
        details:cleanPrintText(pr.querySelector('.pews-guidance')?.innerText)
      });
    }

    // Ventilation evolution summary
    if(id==='ventilacao'){
      const vs=document.getElementById('vmSummary');
      if(vs && cleanPrintText(vs.innerText) && !cleanPrintText(vs.innerText).startsWith('Informe')){
        extras.push({name:'Resumo ventilatório',result:'',details:cleanPrintText(vs.innerText)});
      }
    }

    if(cards.length===0 && extras.length===0) return;

    const sectionRow=document.createElement('tr');
    sectionRow.className='section-row';
    sectionRow.innerHTML=`<td colspan="4">${label}</td>`;
    body.appendChild(sectionRow);

    cards.forEach(card=>{
      const name=cleanPrintText(card.querySelector('.drug')?.innerText);
      const dose=cleanPrintText(card.querySelector('.dose')?.innerText);
      const result=cleanPrintText(card.querySelector('.result')?.innerText);
      const rx=[...card.querySelectorAll('.rx,.micro,.good,.warn')]
        .map(x=>cleanPrintText(x.innerText)).filter(Boolean).join(' | ');

      if(!name && !result) return;
      const tr=document.createElement('tr');
      tr.innerHTML=
        `<td>${label}</td>`+
        `<td><strong>${name}</strong>${dose?`<br>${dose}`:''}</td>`+
        `<td class="print-result">${result || '—'}</td>`+
        `<td>${rx || '—'}</td>`;
      body.appendChild(tr);
    });

    extras.forEach(x=>{
      const tr=document.createElement('tr');
      tr.innerHTML=
        `<td>${label}</td>`+
        `<td><strong>${x.name}</strong></td>`+
        `<td class="print-result">${x.result||'—'}</td>`+
        `<td>${x.details||'—'}</td>`;
      body.appendChild(tr);
    });
  });
}

window.addEventListener('beforeprint', buildPrintTable);

</script>

<footer style="margin:32px auto 18px;max-width:1180px;padding:18px 16px;text-align:center;
border-top:1px solid #d8dee8;color:#536174;font-size:13px;line-height:1.6;">
  <strong style="color:#1f2937;">Criadora: Eduarda Kohakoski — MÉDICA</strong><br>
  CRM-PR 55.082
</footer>


<section id="printOnlyReport" class="print-only-report">
  <div class="print-report-header">
    <h1>CALCULADORA PEDIÁTRICA DE EMERGÊNCIA</h1>
    <div id="printPatientData"></div>
  </div>
  <table class="print-dose-table">
    <thead>
      <tr>
        <th>Categoria</th>
        <th>Medicação / Parâmetro</th>
        <th>Dose / Resultado</th>
        <th>Preparo / Diluição / Administração</th>
      </tr>
    </thead>
    <tbody id="printDoseBody"></tbody>
  </table>
  <div class="print-report-footer">
    <strong>Criadora: Eduarda Kohakoski — MÉDICA | CRM-PR 55.082</strong><br>
    Ferramenta de apoio clínico, diagnóstico, cálculo e dupla checagem; não mandatória e não substitui julgamento médico, protocolos institucionais ou regulamentações vigentes. Validar indicação, apresentação disponível e protocolo institucional.
  </div>
</section>


<script id="v10-layout-js">
function v10Open(tab){
  const b=document.querySelector('.tab[data-tab="'+tab+'"]');
  if(b){ b.click(); document.getElementById('v10Dashboard').style.display='none'; window.scrollTo({top:0,behavior:'smooth'}); }
  document.querySelector('.v10-homebtn')?.classList.remove('active');
}
function v10Home(){
  document.getElementById('v10Dashboard').style.display='block';
  document.querySelector('.v10-homebtn')?.classList.add('active');
  window.scrollTo({top:0,behavior:'smooth'});
}
function v10SearchModules(q){
  q=(q||'').trim().toLowerCase();
  document.querySelectorAll('.v10-sidebar .tab').forEach(b=>{
    b.style.display=(!q || b.textContent.toLowerCase().includes(q))?'block':'none';
  });
  document.querySelectorAll('.v10-card').forEach(b=>{
    b.style.display=(!q || b.textContent.toLowerCase().includes(q))?'block':'none';
  });
}
window.addEventListener('DOMContentLoaded',()=>{
  const tabs=document.querySelector('main .tabs');
  const slot=document.getElementById('v10TabsSlot');
  if(tabs&&slot) slot.appendChild(tabs);
  document.querySelectorAll('.v10-sidebar .tab').forEach(b=>b.addEventListener('click',()=>{
    document.getElementById('v10Dashboard').style.display='none';
    document.querySelector('.v10-homebtn')?.classList.remove('active');
  }));
});
</script>


<script id="burn-module-js">
function burnAgeYears(){
  const years=parseFloat(document.getElementById('idade')?.value)||0;
  const months=parseFloat(document.getElementById('idadeMeses')?.value)||0;
  return Math.max(0, years + months/12);
}
function burnRegionValues(){
  const age=burnAgeYears();
  // Pediatric Rule of Nines (NSW ACI 2026):
  // birth: head 18%, each leg 14%; each completed year through 8 y:
  // head -1%, each leg +0.5%; at 9 y adult proportions + perineum 1%.
  let head, leg, perineum;
  if(age < 9){
    const y=Math.max(0,Math.min(8,Math.floor(age)));
    head=18-y;
    leg=14+(0.5*y);
    perineum=0;
  }else{
    head=9; leg=18; perineum=1;
  }
  return {
    cabeca:head, troncoAnt:18, troncoPost:18,
    msd:9, mse:9, mid:leg, mie:leg, perineo:perineum
  };
}
function burnUpdate(){
  const vals=burnRegionValues();
  let total=0;
  document.querySelectorAll('#burnRegions .burn-check').forEach(ck=>{
    const region=ck.dataset.region;
    const badge=document.querySelector('.burn-auto[data-for="'+region+'"]');
    if(badge) badge.textContent=(vals[region]||0)+'%';
    if(ck.checked) total+=(vals[region]||0);
  });
  total=Math.min(100,total);
  document.getElementById('burnTBSA').textContent=(Math.round(total*10)/10)+'%';
  return total;
}
function burnClear(){
  document.querySelectorAll('.burn-check').forEach(x=>x.checked=false);
  burnUpdate();
  document.getElementById('burnResult').innerHTML='Informe peso no cabeçalho, selecione a SCQ e clique em calcular.';
}
function burnMaintenance(w){
  if(w<=10) return 4*w;
  if(w<=20) return 40+2*(w-10);
  return 60+(w-20);
}
function burnCalculate(){
  const kg=(typeof getPesoKg==='function')?getPesoKg():parseFloat(document.getElementById('peso')?.value);
  const tbsa=burnUpdate();
  const elapsed=Math.max(0,parseFloat(document.getElementById('burnHours').value)||0);
  const given=Math.max(0,parseFloat(document.getElementById('burnGiven').value)||0);
  const out=document.getElementById('burnResult');
  if(!kg || kg<=0){out.innerHTML='<strong>Informe o peso do paciente no cabeçalho.</strong>';return}
  if(tbsa<=0){out.innerHTML='<strong>Selecione ao menos uma região queimada.</strong>';return}

  const maint=burnMaintenance(kg);
  const urine=kg;
  if(tbsa<=10){
    out.innerHTML=`<strong>SCQ automática: ${tbsa.toFixed(1)}%.</strong><br>
    Pela referência utilizada, a ressuscitação formal pela fórmula de queimados é considerada quando a queimadura é &gt;10% SCQ.
    Avaliar hidratação clínica, via oral/EV, perdas associadas e protocolo local.<br><br>
    <strong>Manutenção teórica 4–2–1:</strong> ${maint.toFixed(1)} mL/h.<br>
    <strong>Meta de diurese pediátrica:</strong> aproximadamente ${urine.toFixed(1)} mL/h.`;
    return;
  }

  const total24=3*kg*tbsa;
  const firstHalf=total24/2;
  const secondHalf=total24/2;
  const usedElapsed=Math.min(elapsed,8);
  const remainFirst=Math.max(0,firstHalf-given);
  const hoursLeft=Math.max(0.25,8-usedElapsed);
  const rateFirst=remainFirst/hoursLeft;
  const rateSecond=secondHalf/16;

  let timing='';
  if(elapsed<8){
    timing=`<strong>Primeiras 8 h:</strong> ${firstHalf.toFixed(0)} mL no total. Considerando ${given.toFixed(0)} mL já administrados e ${elapsed.toFixed(2)} h desde a queimadura, iniciar aproximadamente <strong>${rateFirst.toFixed(1)} mL/h</strong> de fluido de ressuscitação até completar as primeiras 8 h.`;
  } else {
    timing=`Já se passaram ≥8 h. A fórmula é calculada desde o momento da queimadura; atraso na ressuscitação exige individualização e discussão com equipe especializada.`;
  }

  out.innerHTML=`<strong>SCQ automática:</strong> ${tbsa.toFixed(1)}% &nbsp; | &nbsp; <strong>Peso:</strong> ${kg.toFixed(2)} kg<br><br>
  <strong>Parkland modificada — ressuscitação:</strong> 3 × ${kg.toFixed(2)} × ${tbsa.toFixed(1)} = <strong>${total24.toFixed(0)} mL/24 h</strong> de Hartmann/Ringer lactato.<br>
  ${timing}<br>
  <strong>8–24 h:</strong> ${secondHalf.toFixed(0)} mL em 16 h ≈ <strong>${rateSecond.toFixed(1)} mL/h</strong> como ponto de partida.<br><br>
  <strong>Manutenção separada (4–2–1):</strong> ${maint.toFixed(1)} mL/h.<br>
  <strong>Meta de diurese:</strong> ~${urine.toFixed(1)} mL/h (1 mL/kg/h).<br><br>
  <span class="muted">Reavaliar e titular a ressuscitação conforme diurese e estado volêmico. O volume calculado é estimativa inicial, não prescrição fixa.</span>`;
}
window.addEventListener('DOMContentLoaded',()=>{
 document.querySelectorAll('.burn-check').forEach(el=>el.addEventListener('change',burnUpdate));
 ['idade','idadeMeses'].forEach(id=>document.getElementById(id)?.addEventListener('input',burnUpdate));
 burnUpdate();
});
</script>


<script id="v104-modules-js">
function currentKg(){
 if(typeof getPesoKg==='function'){const v=getPesoKg(); if(v>0)return v;}
 return parseFloat(document.getElementById('peso')?.value)||0;
}
function maint421(w){if(w<=10)return 4*w;if(w<=20)return 40+2*(w-10);return 60+(w-20)}
function hydrPlan(type){
 const w=currentKg(), out=document.getElementById('hydrModernResult');
 if(!w){out.innerHTML='<strong>Informe o peso no cabeçalho.</strong>';return}
 const rate=maint421(w), day=rate*24;
 if(type==='iso') out.innerHTML=`<strong>Manutenção isotônica:</strong> ${rate.toFixed(1)} mL/h ≈ ${day.toFixed(0)} mL/24 h pela regra 4–2–1.<br>Para a maioria dos pacientes de 28 dias–18 anos: solução isotônica com glicose e KCl apropriados, se indicados. Ex.: SF 0,9% + SG 5%, conforme padronização e disponibilidade.`;
 if(type==='glucose') out.innerHTML=`<strong>Manutenção com glicose:</strong> ${rate.toFixed(1)} mL/h ≈ ${day.toFixed(0)} mL/24 h. A glicose (frequentemente 2,5–5%) pode ser adicionada à solução isotônica conforme idade, ingestão e risco de hipoglicemia.`;
 if(type==='hypo') out.innerHTML=`<strong>Taxa teórica:</strong> ${rate.toFixed(1)} mL/h. <strong>Atenção:</strong> solução hipotônica não é a escolha rotineira para manutenção da criança agudamente enferma; pode ter indicação selecionada (p.ex. necessidades específicas de água livre/hipernatremia), exigindo monitorização de sódio.`;
 if(type==='hyper') out.innerHTML=`<strong>NaCl 3% não é solução de manutenção.</strong> Não aplicar a taxa 4–2–1 à solução hipertônica. Seu uso deve ocorrer apenas por indicação específica e protocolo próprio, com monitorização clínica e do sódio.`;
}
function glyCalculate(){
 const w=currentKg(), g=parseFloat(document.getElementById('glyValue').value), state=document.getElementById('glyState').value, ket=document.getElementById('glyKet').value, out=document.getElementById('glyResult');
 if(!w||!Number.isFinite(g)){out.innerHTML='<strong>Informe peso e glicemia.</strong>';return}
 if(g<70){
   const d10=2*w, grams=.2*w, maxD10=5*w;
   if(state==='severe') out.innerHTML=`<strong>HIPOGLICEMIA com comprometimento importante.</strong><br>SG 10%: <strong>${d10.toFixed(1)} mL EV</strong> (${grams.toFixed(2)} g de glicose = 0,2 g/kg), administrar ao longo de alguns minutos. Reavaliar glicemia em ~15 min e repetir tratamento se resposta inadequada. Limite descrito: até 0,5 g/kg (${maxD10.toFixed(1)} mL/kg-equivalente total de SG10% conforme contexto). Se recorrente, considerar infusão de SG10% com GIR 2–5 mg/kg/min.`;
   else out.innerHTML=`<strong>HIPOGLICEMIA — ${g} mg/dL.</strong><br>Se consciente e deglutindo com segurança, preferir carboidrato de ação rápida por via oral; referência ISPAD ~0,3 g/kg de glicose VO e rechecagem em 15 min. Se deteriorar ou não puder deglutir: SG10% ${d10.toFixed(1)} mL EV (2 mL/kg).`;
 } else if(g>=200){
   out.innerHTML=`<strong>HIPERGLICEMIA — ${g} mg/dL.</strong><br>${ket==='yes'?'<strong>Cetonas positivas/suspeita clínica:</strong> investigar imediatamente CAD com gasometria/pH, bicarbonato, eletrólitos, cetonas e estado volêmico.':'Avaliar sintomas, hidratação, cetonas, eletrólitos e causa da hiperglicemia.'}<br><strong>Não realizar bolus automático de insulina por esta tela.</strong> Se critérios de CAD, seguir protocolo específico.`;
 } else {
   out.innerHTML=`Glicemia ${g} mg/dL: não se enquadra no limiar de hipoglicemia usado nesta ferramenta. Interpretar conforme contexto clínico, jejum, diabetes e sintomas.`;
 }
}
function dhVal(name){return parseInt(document.querySelector('input[name="'+name+'"]:checked')?.value||0)}
function dehydCalculate(){
 const w=currentKg(), out=document.getElementById('dehydResult');
 if(!w){out.innerHTML='<strong>Informe o peso no cabeçalho.</strong>';return}
 const vals=['dh_general','dh_eyes','dh_thirst','dh_skin'].map(dhVal);
 const severe=vals.filter(v=>v===2).length, some=vals.filter(v=>v>=1).length;
 if(severe>=2){
   const first=30*w, second=70*w, total=100*w;
   const ageY=parseFloat(document.getElementById('idade')?.value)||0;
   const ageM=parseFloat(document.getElementById('idadeMeses')?.value)||0;
   const under12=(ageY===0 && ageM<12);
   out.innerHTML=`<strong>DESIDRATAÇÃO GRAVE — PLANO C.</strong><br>Total: <strong>${total.toFixed(0)} mL</strong> de Ringer lactato (ou SF0,9%).<br>1ª etapa: ${first.toFixed(0)} mL em ${under12?'1 hora':'30 minutos'}.<br>2ª etapa: ${second.toFixed(0)} mL em ${under12?'5 horas':'2,5 horas'}.<br>Reavaliar a cada 1–2 h; oferecer SRO assim que puder beber.`;
 } else if(some>=2){
   const vol=75*w;
   out.innerHTML=`<strong>ALGUMA DESIDRATAÇÃO — PLANO B.</strong><br>SRO: <strong>${vol.toFixed(0)} mL em 4 horas</strong> (75 mL/kg), VO ou SNG, em pequenas quantidades frequentes. Reavaliar após 4 h e reclassificar.`;
 } else {
   out.innerHTML=`<strong>SEM DESIDRATAÇÃO — PLANO A.</strong><br>Manter alimentação/aleitamento, oferecer líquidos/SRO adicionais após perdas e orientar sinais de alarme e retorno.`;
 }
}
</script>


<script id="cad-js">
let cadTotalRate=0;
function cadN(id){const v=parseFloat(document.getElementById(id)?.value);return Number.isFinite(v)?v:null}
function cadWeight(){return (typeof currentKg==='function')?currentKg():parseFloat(document.getElementById('peso')?.value)||0}
function cadMaintDay(w){
 if(w<=10)return 100*w;
 if(w<=20)return 1000+50*(w-10);
 return 1500+20*(w-20);
}
function cadSeverity(ph,hco3){
 if(ph===null&&hco3===null)return 'não classificável';
 if((ph!==null&&ph<7.1)||(hco3!==null&&hco3<5))return 'GRAVE';
 if((ph!==null&&ph<7.2)||(hco3!==null&&hco3<10))return 'MODERADA';
 if((ph!==null&&ph<7.3)||(hco3!==null&&hco3<18))return 'LEVE';
 return 'sem acidose compatível pelos valores informados';
}
function cadCalculate(){
 const w=cadWeight(), glu=cadN('cadGlu'), ph=cadN('cadPH'), hco3=cadN('cadHCO3'), na=cadN('cadNa'), k=cadN('cadK'), cl=cadN('cadCl'), bhb=cadN('cadBHB'), pco2=cadN('cadPCO2'), phos=cadN('cadP');
 if(!w){document.getElementById('cadDx').innerHTML='<strong>Informe o peso no cabeçalho.</strong>';return}
 const hyper=glu!==null&&glu>=198;
 const acidosis=(ph!==null&&ph<7.30)||(hco3!==null&&hco3<18);
 const ketBox=document.getElementById('cadKetosisConfirmed')?.checked===true;
 const ketosis=ketBox || (bhb!==null ? bhb>=3 : false);
 const sev=cadSeverity(ph,hco3);
 const ag=(na!==null&&cl!==null&&hco3!==null)?na-cl-hco3:null;
 const gluMmol=glu!==null?glu/18:null;
 const corrNa=(na!==null&&gluMmol!==null)?na+((gluMmol-5)*0.3):null;
 const winter=(hco3!==null)?1.5*hco3+8:null;
 let gas='';
 if(ph!==null&&hco3!==null){
   if(ph<7.35&&hco3<22)gas='Acidose metabólica';
   else if(ph>7.45&&hco3>26)gas='Alcalemia com bicarbonato elevado';
   else gas='Sem padrão isolado de acidose metabólica pelos campos preenchidos';
   if(gas==='Acidose metabólica'&&pco2!==null&&winter!==null){
     gas+=` • pCO₂ esperada pela fórmula de Winter ≈ ${winter.toFixed(1)} ±2 mmHg`;
   }
 }
 let criteria=hyper&&acidosis&&ketosis;
 if(!ketosis) criteria=null;
 document.getElementById('cadDx').innerHTML=
 `<strong>${criteria===true?'Critérios laboratoriais compatíveis com CAD':criteria===false?'Critérios completos de CAD NÃO demonstrados pelos valores preenchidos':'CAD: confirmar cetose para completar os critérios'}</strong><br>
 Gravidade pela acidose: <strong>${sev}</strong>${gas?`<br>Gasometria: ${gas}`:''}
 ${ag!==null?`<br>Ânion gap (Na−Cl−HCO₃): <strong>${ag.toFixed(1)} mmol/L</strong>`:''}
 ${corrNa!==null?`<br>Na corrigido: <strong>${corrNa.toFixed(1)} mmol/L</strong>`:''}
 ${bhb!==null?`<br>β-hidroxibutirato: ${bhb.toFixed(1)} mmol/L`:''}${ketBox?'<br><strong>Cetose: confirmada</strong> por cetonemia/cetonúria informada.':''}`;
 cadFluids(); cadElectrolytes(); cadInsulin(); cadTwoBag();
}
function cadFluids(){
 const w=cadWeight(), mode=document.getElementById('cadFluidMode').value, given=cadN('cadBolusGiven')||0;
 if(!w)return;
 const bolus10=10*w, bolus20=Math.min(20*w,1000);
 const maintDay=cadMaintDay(w), maint36=maintDay*1.5, deficit=100*w; // assumed 10%
 let rate=(maint36+deficit-given)/36;
 if(mode==='double') rate=(maintDay/24)*2;
 cadTotalRate=Math.max(0,rate);
 document.getElementById('cadFluids').innerHTML=
 `<strong>Expansão inicial isotônica:</strong> 10–20 mL/kg = <strong>${bolus10.toFixed(0)}–${bolus20.toFixed(0)} mL</strong> de SF 0,9% ou cristaloide balanceado em 20–30 min.<br>
 ${mode==='cps'?`<strong>Taxa subsequente estimada (déficit assumido de 10% + manutenção em 36 h): ${cadTotalRate.toFixed(1)} mL/h.</strong><br>Déficit estimado: ${deficit.toFixed(0)} mL; manutenção calculada para 36 h: ${maint36.toFixed(0)} mL. O volume informado como já administrado (${given.toFixed(0)} mL) foi descontado.`:`<strong>Taxa temporária 2× manutenção: ${cadTotalRate.toFixed(1)} mL/h.</strong> Usar apenas enquanto o cálculo detalhado é concluído.`}<br>
 <span class="muted">Choque/hipotensão: bolus isotônico em 10–15 min; adicionais de 10 mL/kg até 40 mL/kg com suporte intensivo pediátrico.</span>`;
}
function cadElectrolytes(){
 const k=cadN('cadK'), glu=cadN('cadGlu'), p=cadN('cadP'), out=document.getElementById('cadElectrolytes');
 let txt='';
 if(k===null)txt+='<strong>K⁺ não informado.</strong> Dosar antes de iniciar insulina.<br>';
 else if(k<=3)txt+='<strong style="color:#b42335">K⁺ ≤3,0 mmol/L: NÃO INICIAR INSULINA. Repor potássio primeiro.</strong><br>';
 else if(k<5)txt+='<strong>K⁺ <5 mmol/L:</strong> após documentar diurese recente, adicionar pelo menos 40 mmol/L de potássio aos fluidos conforme protocolo local.<br>';
 else txt+='<strong>K⁺ ≥5 mmol/L:</strong> monitorar estreitamente; não adicionar automaticamente K até reavaliação/diurese conforme protocolo.<br>';
 if(glu!==null){
   if(glu/18<=17)txt+='Glicemia atingiu aproximadamente ≤306 mg/dL: considerar/adicionar glicose aos fluidos para manter glicemia ~126–198 mg/dL enquanto a cetose/acidemia é tratada.<br>';
   else txt+='Manter inicialmente fluido sem glicose; adicionar dextrose quando glicemia estiver ~270–306 mg/dL ou conforme velocidade de queda.<br>';
 }
 if(p!==null&&p<0.5)txt+='<strong>Fósforo <0,5 mmol/L:</strong> considerar reposição; seguir protocolo local.<br>';
 txt+='<strong>Bicarbonato:</strong> não usar rotineiramente para corrigir a acidose da CAD.';
 out.innerHTML=txt;
}
function cadInsulin(){
 const w=cadWeight(), k=cadN('cadK'), hrs=cadN('cadFluidHours')||0, dose=parseFloat(document.getElementById('cadInsDose').value), conc=parseFloat(document.getElementById('cadInsConc').value), out=document.getElementById('cadInsulinResult');
 if(!w)return;
 const u=dose*w, ml=u/conc;
 let gate=(hrs>=1&&k!==null&&k>3);
 out.classList.toggle('cad-red',!gate);
 out.innerHTML=`<strong>${gate?'Critérios mínimos informados permitem considerar início da infusão.':'NÃO INICIAR AINDA pelos dados preenchidos.'}</strong><br>
 Dose selecionada: ${dose.toFixed(2)} UI/kg/h × ${w.toFixed(2)} kg = <strong>${u.toFixed(3)} UI/h</strong>.<br>
 Com concentração de ${conc} UI/mL → <strong>${ml.toFixed(2)} mL/h na BIC</strong>.<br>${conc===1?'<strong>Preparo 1 UI/mL:</strong> 50 UI de insulina regular + SF 0,9% até volume final de 50 mL; preencher o equipo com a solução antes de iniciar.<br>':''}
 <strong>Sem bolus de insulina.</strong> Iniciar somente após ≥1 h de fluidos e K⁺ >3,0 mmol/L.`;
}
function cadTwoBag(){
 const rate=cadTotalRate, d=parseFloat(document.getElementById('cadDex').value), out=document.getElementById('cadBagResult');
 if(!rate){out.innerHTML='Calcule primeiro a taxa total de fluidos.';return}
 const factors={0:[1,0],5:[.6,.4],7.5:[.4,.6],10:[.2,.8],12.5:[0,1]}, f=factors[d];
 out.innerHTML=`Taxa total: <strong>${rate.toFixed(1)} mL/h</strong>.<br><strong>Composição:</strong> as duas bolsas devem ter a mesma base isotônica e os mesmos eletrólitos (ex.: KCl 40 mmol/L quando indicado); a Bolsa 2 contém dextrose 12,5%.<br>Bolsa 1 (sem dextrose): <strong>${(rate*f[0]).toFixed(1)} mL/h</strong>.<br>Bolsa 2 (D12,5%): <strong>${(rate*f[1]).toFixed(1)} mL/h</strong>.<br><span class="muted">As duas bolsas devem ter os mesmos eletrólitos; apenas a concentração de dextrose difere.</span>`;
}
function cadNeuro(){
 const n=[...document.querySelectorAll('.cad-neuro-ck')].filter(x=>x.checked).length, w=cadWeight(), out=document.getElementById('cadNeuroResult');
 if(!n){out.classList.remove('cad-red');out.innerHTML='Nenhum dos sinais selecionados. Manter vigilância neurológica frequente.';return}
 const saline=Math.min(5*w,250), manLow=.5*w, manHigh=1*w;
 out.classList.add('cad-red');
 out.innerHTML=`<strong>SUSPEITA DE LESÃO CEREBRAL — tratar imediatamente; não aguardar neuroimagem.</strong><br>
 Elevar cabeceira 30°, cabeça em linha média, minimizar agitação, manter fluido isotônico e acionar terapia intensiva.<br>
 <strong>NaCl 3%: ${saline.toFixed(0)} mL</strong> (5 mL/kg, máx. 250 mL) em 10–15 min <strong>OU</strong> manitol <strong>${manLow.toFixed(1)}–${manHigh.toFixed(1)} g</strong> (0,5–1 g/kg) em 15–20 min.<br>
 Considerar reduzir a taxa de fluidos para 75% se a perfusão permitir.`;
}
</script>


<script id="tab-print-js">
function printSingleTab(id){
 const panel=document.getElementById(id);
 if(!panel)return;
 document.body.classList.add('print-one');
 document.querySelectorAll('.panel').forEach(p=>p.classList.remove('print-target'));
 panel.classList.add('print-target');
 const cleanup=()=>{document.body.classList.remove('print-one');panel.classList.remove('print-target');window.removeEventListener('afterprint',cleanup)};
 window.addEventListener('afterprint',cleanup);
 window.print();
 setTimeout(()=>{ if(document.body.classList.contains('print-one')) cleanup(); },1500);
}
document.addEventListener('DOMContentLoaded',()=>{
 document.querySelectorAll('.panel').forEach(panel=>{
   if(panel.id==='home')return;
   const h=panel.querySelector('h2');
   if(!h || h.querySelector('.tab-print-btn'))return;
   const b=document.createElement('button');
   b.type='button'; b.className='tab-print-btn'; b.textContent='🖨 Imprimir esta aba';
   b.onclick=()=>printSingleTab(panel.id);
   h.appendChild(b);
 });
});
</script>


<script id="v108-home-js">
document.addEventListener('DOMContentLoaded',()=>{
  // Synchronize the new top patient fields with the calculator's original global fields.
  const pairs=[
    ['homePesoKg','peso'],['homePesoG','pesoGramas'],
    ['homeIdade','idade'],['homeIdadeMeses','idadeMeses']
  ];
  pairs.forEach(([homeId,mainId])=>{
    const h=document.getElementById(homeId), m=document.getElementById(mainId);
    if(!h||!m)return;
    h.value=m.value||'';
    h.addEventListener('input',()=>{m.value=h.value;m.dispatchEvent(new Event('input',{bubbles:true}));m.dispatchEvent(new Event('change',{bubbles:true}))});
    m.addEventListener('input',()=>{if(document.activeElement!==h)h.value=m.value});
  });

  // Remove only the redundant lower "Acesso rápido — principais emergências" block.
  [...document.querySelectorAll('h1,h2,h3,h4,strong,b')].forEach(el=>{
    const t=(el.textContent||'').trim().toLowerCase();
    if(t.includes('acesso rápido') && t.includes('principais emergências')){
      let box=el.parentElement;
      while(box && box!==document.body){
        if(box.querySelectorAll('button').length>=3){box.style.display='none';break}
        box=box.parentElement;
      }
    }
  });

  // On the home screen, never leave PCR (or another clinical panel) visible underneath it.
  const home=document.getElementById('home');
  if(home && getComputedStyle(home).display!=='none'){
    document.querySelectorAll('.panel').forEach(p=>{if(p!==home)p.style.display='none'});
    home.style.display='block';
  }
});
</script>


<style id="home-only-initial-fix">
/* Home limpa: nenhuma aba clínica fica visível abaixo da tela inicial. */
body:not(.clinical-tab-open) section.panel{display:none}
</style>
<script id="home-only-initial-script">
document.addEventListener('DOMContentLoaded', function(){
  document.querySelectorAll('section.panel').forEach(function(p){ p.style.display='none'; });
  document.querySelectorAll('[data-tab]').forEach(function(btn){
    btn.addEventListener('click', function(){
      document.body.classList.add('clinical-tab-open');
      document.querySelectorAll('section.panel').forEach(function(p){ p.style.display='none'; });
      const target=document.getElementById(btn.getAttribute('data-tab'));
      if(target) target.style.display='block';
    }, true);
  });
});
</script>


<style id="home-exclusive-css">
#homeOnlyDashboard{display:block}
body.clinical-view #homeOnlyDashboard{display:none!important}
</style>
<script id="home-exclusive-js">
document.addEventListener('DOMContentLoaded',function(){
  const dash=document.getElementById('homeOnlyDashboard');
  if(dash) dash.style.display='block';

  document.querySelectorAll('[data-tab]').forEach(function(btn){
    btn.addEventListener('click',function(){
      document.body.classList.add('clinical-view');
      if(dash) dash.style.display='none';
    },true);
  });

  /* Cards da própria Home abrem o módulo e também retiram o dashboard da tela clínica. */
  document.querySelectorAll('#homeOnlyDashboard .v10-card').forEach(function(btn){
    btn.addEventListener('click',function(){
      document.body.classList.add('clinical-view');
      if(dash) dash.style.display='none';
    },true);
  });

  /* Se houver controle explícito de início/home no menu, restaura o dashboard. */
  document.querySelectorAll('[data-tab="home"],[data-home],.home-link').forEach(function(btn){
    btn.addEventListener('click',function(){
      document.body.classList.remove('clinical-view');
      if(dash) dash.style.display='block';
    },true);
  });
});
</script>


<script id="single-tab-print-fix-js">
(function(){
  function syncFormValues(source, clone){
    const srcFields=source.querySelectorAll('input,select,textarea');
    const dstFields=clone.querySelectorAll('input,select,textarea');
    srcFields.forEach(function(s,i){
      const d=dstFields[i];
      if(!d)return;
      if(s.tagName==='SELECT'){
        d.value=s.value;
        Array.from(d.options).forEach(function(o){o.selected=(o.value===s.value)});
      }else if(s.type==='checkbox'||s.type==='radio'){
        d.checked=s.checked;
        if(s.checked)d.setAttribute('checked','checked');else d.removeAttribute('checked');
      }else{
        d.value=s.value;
        d.setAttribute('value',s.value);
        if(d.tagName==='TEXTAREA')d.textContent=s.value;
      }
    });
  }

  window.printSingleTab=function(id){
    const source=document.getElementById(id);
    if(!source)return;

    let area=document.getElementById('singleTabPrintArea');
    if(area)area.remove();

    area=document.createElement('div');
    area.id='singleTabPrintArea';

    const clone=source.cloneNode(true);
    clone.classList.add('single-tab-print-clone');
    clone.style.display='block';
    clone.style.visibility='visible';

    syncFormValues(source,clone);

    /* Preserva exatamente os resultados já calculados na tela,
       inclusive doses, volumes, diluições e alertas. */
    area.appendChild(clone);
    document.body.appendChild(area);
    document.body.classList.add('single-tab-printing');

    const cleanup=function(){
      document.body.classList.remove('single-tab-printing');
      const a=document.getElementById('singleTabPrintArea');
      if(a)a.remove();
      window.removeEventListener('afterprint',cleanup);
    };
    window.addEventListener('afterprint',cleanup);
    window.print();
    setTimeout(function(){
      if(document.body.classList.contains('single-tab-printing'))cleanup();
    },3000);
  };

  /* Substitui somente a ação dos botões "Imprimir esta aba". */
  document.addEventListener('DOMContentLoaded',function(){
    document.querySelectorAll('.tab-print-btn').forEach(function(btn){
      const panel=btn.closest('.panel');
      if(!panel)return;
      btn.onclick=function(ev){
        ev.preventDefault();
        ev.stopPropagation();
        window.printSingleTab(panel.id);
      };
    });
  });
})();
</script>


<script id="definitive-print-js">
(function(){
  let selectedPrint=false;

  function copyLiveValues(src, dst){
    const s=src.querySelectorAll('input,select,textarea');
    const d=dst.querySelectorAll('input,select,textarea');
    s.forEach((x,i)=>{
      if(!d[i])return;
      if(x.type==='checkbox'||x.type==='radio'){
        d[i].checked=x.checked;
        if(x.checked)d[i].setAttribute('checked','checked'); else d[i].removeAttribute('checked');
      }else if(x.tagName==='SELECT'){
        d[i].value=x.value;
        [...d[i].options].forEach(o=>o.selected=(o.value===x.value));
      }else{
        d[i].value=x.value;
        d[i].setAttribute('value',x.value);
        if(d[i].tagName==='TEXTAREA')d[i].textContent=x.value;
      }
    });
  }

  function cleanupSelectedPrint(){
    document.documentElement.classList.remove('print-selected-tab');
    document.body.classList.remove('single-tab-printing','print-one');
    const old=document.getElementById('printSelectedTabOnly');
    if(old)old.remove();
    selectedPrint=false;
  }

  window.printSingleTab=function(id){
    cleanupSelectedPrint();
    const src=document.getElementById(id);
    if(!src)return;

    const area=document.createElement('main');
    area.id='printSelectedTabOnly';
    const clone=src.cloneNode(true);
    clone.removeAttribute('style');
    clone.classList.add('print-selected-content');
    copyLiveValues(src,clone);
    area.appendChild(clone);
    document.body.appendChild(area);

    selectedPrint=true;
    document.documentElement.classList.add('print-selected-tab');

    const done=()=>{cleanupSelectedPrint();window.removeEventListener('afterprint',done)};
    window.addEventListener('afterprint',done);
    window.print();
  };

  /* Captura todos os botões "Imprimir esta aba" e força impressão apenas do painel pai. */
  document.addEventListener('click',function(e){
    const btn=e.target.closest && e.target.closest('.tab-print-btn');
    if(!btn)return;
    const panel=btn.closest('.panel');
    if(!panel)return;
    e.preventDefault();e.stopImmediatePropagation();
    window.printSingleTab(panel.id);
  },true);

  /* O botão geral/Imprimir final NÃO recebe a classe acima e mantém a rotina
     original de relatório completo, portanto continua imprimindo o PDF completo. */
  window.addEventListener('afterprint',function(){
    if(selectedPrint)cleanupSelectedPrint();
  });
})();
</script>


<script id="tab-table-print-js">
(function(){
 function esc(s){return String(s??'').replace(/[&<>"']/g,m=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m]))}
 function cleanText(el){
   if(!el)return '';
   const c=el.cloneNode(true);
   c.querySelectorAll('button,.tab-print-btn,script,style').forEach(x=>x.remove());
   c.querySelectorAll('input,select,textarea').forEach(x=>{
     let v='';
     if(x.tagName==='SELECT')v=x.options[x.selectedIndex]?.text||x.value;
     else if(x.type==='checkbox'||x.type==='radio')v=x.checked?'✓':'';
     else v=x.value||'';
     const s=document.createElement('span');s.textContent=v;x.replaceWith(s);
   });
   return (c.innerText||c.textContent||'').replace(/\n{3,}/g,'\n\n').trim();
 }
 function patientMeta(){
   const kg=document.getElementById('peso')?.value||'';
   const gr=document.getElementById('pesoGramas')?.value||'';
   const y=document.getElementById('idade')?.value||'';
   const mo=document.getElementById('idadeMeses')?.value||'';
   let a=[];
   if(kg)a.push(`Peso: ${kg}${gr?','+gr:''} kg`);
   if(y||mo)a.push(`Idade: ${y||0} a ${mo||0} m`);
   return a.join(' • ');
 }
 function buildRows(panel){
   const rows=[];
   // Prefer clinically meaningful cards/results so doses and dilutions stay grouped.
   const blocks=[...panel.querySelectorAll('.card,article,.result,.cad-step,.hydr-card,.dehyd-card,.gly-info>div,.dehyd-plans>div')];
   const used=new Set();
   blocks.forEach(b=>{
     // Skip nested blocks already represented by a parent selected block.
     if([...used].some(p=>p.contains(b)))return;
     const txt=cleanText(b);
     if(!txt||txt.length<3)return;
     used.add(b);
     const title=(b.querySelector('.drug,h3,h4,strong,b')?.textContent||'Resultado / orientação').trim();
     let body=txt;
     if(title && body.startsWith(title))body=body.slice(title.length).trim();
     rows.push([title,body]);
   });
   if(!rows.length){
     const txt=cleanText(panel);
     if(txt)rows.push(['Conteúdo da aba',txt]);
   }
   return rows;
 }
 function cleanup(){
   document.documentElement.classList.remove('print-tab-table','print-selected-tab');
   document.body.classList.remove('single-tab-printing','print-one');
   document.getElementById('tabTablePrint')?.remove();
   document.getElementById('printSelectedTabOnly')?.remove();
 }
 window.printSingleTab=function(id){
   cleanup();
   const panel=document.getElementById(id);if(!panel)return;
   const title=(panel.querySelector('h2')?.childNodes[0]?.textContent||panel.querySelector('h2')?.textContent||id).trim();
   const rows=buildRows(panel);
   const area=document.createElement('div');area.id='tabTablePrint';
   area.innerHTML=`<h1>${esc(title)}</h1>
     <div class="pt-meta">${esc(patientMeta())}</div>
     <table>
      <thead><tr><th style="width:28%">Medicação / Parâmetro</th><th>Dose / Resultado / Diluição / Administração</th></tr></thead>
      <tbody>${rows.map(r=>`<tr><td><strong>${esc(r[0])}</strong></td><td>${esc(r[1]).replace(/\n/g,'<br>')}</td></tr>`).join('')}</tbody>
     </table>
     <div class="pt-footer">Ferramenta de apoio clínico e dupla checagem. Validar indicação, dose, apresentação disponível, diluição e protocolo institucional. Criadora: Dra. Eduarda Kohakoski — Médica — CRM-PR 55.082.</div>`;
   document.body.appendChild(area);
   document.documentElement.classList.add('print-tab-table');
   const done=()=>{cleanup();window.removeEventListener('afterprint',done)};
   window.addEventListener('afterprint',done);
   window.print();
 };
 // Highest-priority interception: only "Imprimir esta aba".
 document.addEventListener('click',function(e){
   const b=e.target.closest?.('.tab-print-btn');if(!b)return;
   const p=b.closest('.panel');if(!p)return;
   e.preventDefault();e.stopImmediatePropagation();
   window.printSingleTab(p.id);
 },true);
})();
</script>


<script id="score-description-final-js">
(function(){
 const defs=[
  [/glasgow/i,'Avalia o nível de consciência pelas respostas ocular, verbal e motora.'],
  [/\bpram\b/i,'Avalia a gravidade da crise de asma pediátrica e a resposta ao tratamento.'],
  [/westley/i,'Classifica a gravidade do crupe com base nos principais sinais respiratórios.'],
  [/\bpas\b|pediatric appendicitis/i,'Pediatric Appendicitis Score — auxilia na estratificação da probabilidade clínica de apendicite.'],
  [/\bflacc\b/i,'Avalia dor em crianças pequenas ou pacientes que não conseguem quantificá-la verbalmente.'],
  [/pediatric trauma score|trauma score/i,'Estratifica a gravidade do trauma pediátrico e auxilia na identificação de maior risco.'],
  [/pecarn/i,'Regra de decisão no trauma craniano pediátrico que auxilia na avaliação da necessidade de tomografia.'],
  [/\bpews\b/i,'Pediatric Early Warning Score — auxilia na identificação precoce de deterioração clínica.']
 ];
 function apply(){
   const panel=document.getElementById('scores');
   if(!panel)return;
   const titles=panel.querySelectorAll('h2,h3,h4,.drug,.score-title,strong');
   titles.forEach(t=>{
     if(t.dataset.purposeDone)return;
     const text=(t.textContent||'').trim();
     const hit=defs.find(d=>d[0].test(text));
     if(!hit)return;
     const s=document.createElement('span');
     s.className='score-purpose-final';
     s.textContent=hit[1];
     t.insertAdjacentElement('afterend',s);
     t.dataset.purposeDone='1';
   });
 }
 document.addEventListener('DOMContentLoaded',()=>{
   apply();
   const p=document.getElementById('scores');
   if(p)new MutationObserver(apply).observe(p,{childList:true,subtree:true});
 });
})();
</script>


<script id="abx-dose-selector-sync">
document.addEventListener('DOMContentLoaded',function(){
 const d=document.getElementById('abxDrug');
 if(d){
   d.addEventListener('change',function(){
     const s=document.getElementById('abxDoseSelect');
     if(s)s.dataset.signature='';
   },true);
 }
});
</script>

</body>
</html>
