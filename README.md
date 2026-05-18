# prospeed-dev.github.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>AutoParts Kerala — Premium Marketplace</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,400&family=Space+Mono&display=swap" rel="stylesheet"/>
<style>
/* ─── RESET & ROOT ─────────────────────────────────────────────────── */
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --gold:#c9a84c;--gold2:rgba(201,168,76,.14);
  --neon:#00e5ff;--red:#cc2936;--green:#2d9e5f;--orange:#e85d04;
  --bg:#09090b;--surf:#111114;--card:#18181c;--cb:rgba(255,255,255,.07);
  --inp:#0e0e11;--inpb:rgba(255,255,255,.1);
  --sb:#0c0c0f;
  --t1:#f0ece4;--t2:#888;--t3:#2e2e33;
}
body.light{
  --bg:#f4f4ef;--surf:#ebebE6;--card:#fff;--cb:#e3e3de;
  --inp:#fff;--inpb:#d5d5d0;--sb:#17171b;
  --t1:#1a1a1a;--t2:#666;--t3:#ddd;
  --gold:#a8792a;--neon:#0055bb;--green:#256640;--orange:#b84000;
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--t1);font-family:'DM Sans',system-ui,sans-serif;overflow-x:hidden;min-height:100vh}
input,select,textarea,button{font-family:inherit}
::-webkit-scrollbar{width:5px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:#c9a84c40;border-radius:3px}
select option{background:#18181c;color:#f0ece4}

/* ─── ANIMATIONS ───────────────────────────────────────────────────── */
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes fadeUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
@keyframes slideIn{from{transform:translateX(110%)}to{transform:translateX(0)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
@keyframes barGrow{from{width:0}to{width:var(--target-w,0%)}}
.fade-up{animation:fadeUp .38s ease both}
.spin-anim{animation:spin .75s linear infinite;display:inline-block}

/* ─── LAYOUT ───────────────────────────────────────────────────────── */
#sidebar{
  position:fixed;left:0;top:0;bottom:0;width:224px;
  background:var(--sb);border-right:1px solid rgba(255,255,255,.05);
  z-index:200;display:flex;flex-direction:column;padding:0
}
#main{margin-left:224px;min-height:100vh;display:flex;flex-direction:column}
#topbar{
  position:sticky;top:0;z-index:100;
  background:rgba(9,9,11,.92);backdrop-filter:blur(18px);
  -webkit-backdrop-filter:blur(18px);
  border-bottom:1px solid rgba(255,255,255,.06);
  height:62px;padding:0 36px;
  display:flex;align-items:center;justify-content:space-between
}
body.light #topbar{background:rgba(244,244,239,.94)}
#content{padding:32px 36px;flex:1}

/* ─── SIDEBAR ──────────────────────────────────────────────────────── */
.sb-brand{padding:22px 20px 20px;border-bottom:1px solid rgba(255,255,255,.05)}
.sb-logo{font-family:'Bebas Neue',sans-serif;font-size:24px;letter-spacing:3px;color:var(--gold);line-height:1}
.sb-sub{font-size:9px;color:#3a3a45;letter-spacing:2.5px;text-transform:uppercase;margin-top:3px}
.sb-nav{flex:1;padding:12px 10px;display:flex;flex-direction:column;gap:2px}
.nav-item{
  display:flex;align-items:center;gap:11px;padding:10px 13px;
  border-radius:8px;border:none;cursor:pointer;text-align:left;width:100%;
  background:transparent;color:var(--t2);
  border-left:2.5px solid transparent;
  font-size:13.5px;font-weight:500;transition:all .18s;white-space:nowrap
}
.nav-item:hover{color:var(--t1);background:rgba(255,255,255,.03)}
.nav-item.active{background:var(--gold2);color:var(--gold);border-left-color:var(--gold);font-weight:600}
.nav-icon{font-size:16px;width:20px;text-align:center;flex-shrink:0}
.sb-foot{padding:14px 18px;border-top:1px solid rgba(255,255,255,.05)}
.theme-btn{
  display:flex;align-items:center;gap:9px;background:transparent;
  border:none;cursor:pointer;color:var(--t2);font-size:13px;padding:7px 0;
  transition:color .2s
}
.theme-btn:hover{color:var(--t1)}

/* ─── TOPBAR ───────────────────────────────────────────────────────── */
.tb-left{display:flex;align-items:center;gap:13px}
.tb-car-icon{font-size:22px}
.tb-title{font-weight:700;font-size:15px;color:var(--t1)}
.tb-sub{font-size:11px;color:var(--t2);margin-top:1px}
.tb-right{display:flex;align-items:center;gap:10px}
.tb-pill{background:var(--gold2);color:var(--gold);padding:5px 13px;border-radius:20px;font-size:11.5px;font-weight:600}
.tb-avatar{width:32px;height:32px;border-radius:50%;background:var(--gold);display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;color:#000}

/* ─── PAGES ────────────────────────────────────────────────────────── */
.page{display:none}.page.active{display:block}

/* ─── CARDS ────────────────────────────────────────────────────────── */
.card{background:var(--card);border:1px solid var(--cb);border-radius:14px}
.card-p{padding:26px}
.hover-lift{transition:transform .22s,box-shadow .22s}
.hover-lift:hover{transform:translateY(-4px);box-shadow:0 18px 56px rgba(0,0,0,.38)}
.hover-btn{transition:filter .18s,transform .18s;cursor:pointer}
.hover-btn:hover{filter:brightness(1.12);transform:translateY(-1px)}

/* ─── FORM ELEMENTS ────────────────────────────────────────────────── */
.flabel{display:block;font-size:10px;color:var(--t2);letter-spacing:1.2px;text-transform:uppercase;margin-bottom:6px;font-weight:600}
.finput,.fselect,.ftextarea{
  width:100%;padding:11px 13px;border-radius:8px;
  border:1px solid var(--inpb);background:var(--inp);
  font-size:13.5px;color:var(--t1);transition:border-color .2s
}
.finput:focus,.fselect:focus,.ftextarea:focus{border-color:var(--gold);outline:none}
.fselect{cursor:pointer}
.fselect:disabled{opacity:.38;cursor:not-allowed}
.ftextarea{resize:vertical}

/* ─── VEHICLE SELECTOR CARD ────────────────────────────────────────── */
.vs-head{display:flex;align-items:center;gap:12px;margin-bottom:22px}
.vs-head-icon{width:40px;height:40px;background:var(--gold2);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px}
.vs-title{font-family:'Bebas Neue',sans-serif;font-size:19px;letter-spacing:2px;color:var(--gold)}
.vs-desc{font-size:11px;color:var(--t2);margin-top:1px}
.vs-grid{display:grid;grid-template-columns:1fr 1fr 1fr auto;gap:14px;align-items:end}
.gen-btn{
  padding:12px 22px;background:linear-gradient(135deg,var(--gold),#d4901c);
  color:#000;border:none;border-radius:9px;font-weight:700;font-size:13.5px;
  cursor:pointer;display:flex;align-items:center;gap:7px;white-space:nowrap;
  transition:filter .18s,transform .18s,box-shadow .18s
}
.gen-btn:hover{filter:brightness(1.1);box-shadow:0 0 28px rgba(201,168,76,.4)}
.gen-btn:disabled{opacity:.45;cursor:not-allowed;transform:none;filter:none;box-shadow:none}
.veh-tags{display:flex;gap:10px;flex-wrap:wrap;margin-top:16px}
.veh-tag{background:var(--gold2);border:1px solid rgba(201,168,76,.22);border-radius:7px;padding:6px 13px}
.veh-tag-l{font-size:9px;color:var(--t2);text-transform:uppercase;letter-spacing:1px}
.veh-tag-v{font-size:12px;font-weight:600;color:var(--gold);margin-top:1px}

/* ─── AI STRIP ─────────────────────────────────────────────────────── */
.ai-strip{
  background:rgba(0,229,255,.05);border:1px solid rgba(0,229,255,.18);
  border-radius:11px;padding:14px 18px;display:flex;align-items:center;gap:13px;
  margin-bottom:20px
}
.ai-spinner{width:30px;height:30px;border:2px solid var(--neon);border-top-color:transparent;border-radius:50%;flex-shrink:0}
.ai-msg{color:var(--neon);font-size:13px;flex:1}
.ai-dismiss{background:transparent;border:1px solid rgba(0,229,255,.3);color:var(--neon);padding:5px 12px;border-radius:6px;font-size:11px;font-weight:600;cursor:pointer;white-space:nowrap}

/* ─── STATS ROW ────────────────────────────────────────────────────── */
.stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:20px}
.stat-card{padding:18px 20px;border-radius:12px}
.stat-ico{font-size:22px;margin-bottom:7px}
.stat-num{font-family:'Bebas Neue',sans-serif;font-size:26px;letter-spacing:.5px}
.stat-lbl{font-size:11px;color:var(--t2);margin-top:2px}

/* ─── FILTER BAR ───────────────────────────────────────────────────── */
.filter-bar{
  display:flex;gap:12px;flex-wrap:wrap;align-items:center;
  padding:16px 18px;margin-bottom:20px;border-radius:12px
}
.srch-wrap{flex:1;min-width:160px;position:relative}
.srch-ico{position:absolute;left:11px;top:50%;transform:translateY(-50%);color:var(--t2);pointer-events:none}
.srch-inp{
  width:100%;padding:9px 11px 9px 32px;border-radius:8px;
  border:1px solid var(--inpb);background:var(--inp);font-size:13px;color:var(--t1)
}
.srch-inp:focus{outline:none;border-color:var(--gold)}
.fbar-sel{padding:9px 12px;border-radius:8px;border:1px solid var(--inpb);background:var(--inp);font-size:13px;color:var(--t1);cursor:pointer}
.view-tog{display:flex;gap:4px}
.vbtn{padding:8px 12px;border-radius:6px;font-size:12.5px;cursor:pointer;font-weight:500;transition:all .18s;border:1px solid var(--inpb);background:transparent;color:var(--t2)}
.vbtn.active{background:var(--gold2);color:var(--gold);border-color:rgba(201,168,76,.38)}
.count-lbl{font-size:13px;color:var(--t2);white-space:nowrap}

/* ─── CATEGORY SECTION ─────────────────────────────────────────────── */
.cat-sec{margin-bottom:30px}
.cat-hdr{display:flex;align-items:center;gap:12px;margin-bottom:14px;cursor:pointer;user-select:none}
.cat-ico-box{width:34px;height:34px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0}
.cat-name-txt{font-family:'Bebas Neue',sans-serif;font-size:19px;letter-spacing:1.5px}
.cat-sub{font-size:10.5px;color:var(--t2);margin-top:1px}
.cat-pill{padding:2px 9px;border-radius:10px;font-size:10.5px;font-weight:600;margin-left:auto}
.cat-arr{font-size:17px;color:var(--t3);margin-left:6px}

/* ─── PARTS GRID / LIST ────────────────────────────────────────────── */
.parts-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(285px,1fr));gap:14px}
.parts-list{display:flex;flex-direction:column;gap:7px}

/* ─── PART CARD ────────────────────────────────────────────────────── */
.pcard{background:var(--card);border:1px solid var(--cb);border-radius:13px;overflow:hidden;transition:transform .22s,box-shadow .22s}
.pcard:hover{transform:translateY(-4px);box-shadow:0 18px 54px rgba(0,0,0,.38)}
.pcard-img{height:128px;display:flex;align-items:center;justify-content:center;position:relative}
.pcard-img svg{opacity:.62;transition:opacity .25s}
.pcard:hover .pcard-img svg{opacity:.9}
.pcard-stock{position:absolute;top:9px;right:9px;padding:2px 8px;border-radius:10px;font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.8px}
.pcard-oem{position:absolute;top:9px;left:9px;padding:2px 7px;border-radius:8px;font-size:8.5px;font-weight:600;font-family:'Space Mono',monospace}
.pcard-body{padding:14px}
.pcard-name{font-size:13px;font-weight:700;color:var(--t1);line-height:1.32;margin-bottom:5px}
.pcard-desc{font-size:11px;color:var(--t2);line-height:1.65;margin-bottom:12px;min-height:30px}
.price-row{display:flex;align-items:center;gap:8px;margin-bottom:9px}
.price-num{font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:.5px;color:var(--gold);flex:1}
.price-ebtn{background:var(--gold2);color:var(--gold);border:1px solid rgba(201,168,76,.3);border-radius:5px;padding:4px 9px;cursor:pointer;font-size:11px;font-weight:600}
.price-inp{border:1px solid var(--inpb);background:var(--inp);border-radius:5px;padding:5px 8px;font-size:14px;font-weight:700;width:106px;color:var(--t1)}
.price-inp:focus{outline:none;border-color:var(--gold)}
.psave-btn{background:var(--green);color:#fff;border:none;border-radius:5px;padding:5px 9px;cursor:pointer;font-size:11px;font-weight:600}
.pcancel-btn{background:transparent;border:1px solid var(--t3);color:var(--t2);border-radius:5px;padding:5px 7px;cursor:pointer;font-size:11px}
.stock-sel{width:100%;padding:7px 9px;border-radius:6px;border:1px solid var(--inpb);background:var(--inp);font-size:12px;cursor:pointer;margin-bottom:9px;color:var(--t1)}
.pcard-actions{display:flex;gap:5px}
.fedit-btn{flex:1;border:none;border-radius:7px;padding:7px;cursor:pointer;font-size:12px;font-weight:600}
.pdel-btn{background:rgba(204,41,54,.1);color:var(--red);border:none;border-radius:7px;padding:7px 11px;cursor:pointer;font-size:13px}

/* ─── PART ROW ─────────────────────────────────────────────────────── */
.prow{
  background:var(--card);border:1px solid var(--cb);border-radius:9px;
  padding:11px 16px;display:flex;align-items:center;gap:13px;
  transition:transform .18s,background .18s
}
.prow:hover{transform:translateX(3px);background:var(--surf)}
.prow-ico{width:42px;height:42px;border-radius:7px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.prow-name{flex:2;font-size:13px;font-weight:600;color:var(--t1)}
.prow-oem{font-size:9.5px;color:var(--t2);margin-top:2px;font-family:'Space Mono',monospace}
.prow-price{flex:1;font-family:'Bebas Neue',sans-serif;font-size:18px;color:var(--gold)}
.prow-stock{flex:1}
.prow-acts{display:flex;gap:5px;flex-shrink:0}

/* ─── EMPTY STATE ──────────────────────────────────────────────────── */
.empty{text-align:center;padding:72px 40px}
.empty-ico{font-size:58px;margin-bottom:16px}
.empty-title{font-family:'Bebas Neue',sans-serif;font-size:26px;letter-spacing:2.5px;color:var(--t2);margin-bottom:9px}
.empty-txt{font-size:14px;color:var(--t3);max-width:380px;margin:0 auto;line-height:1.72}

/* ─── MODAL ────────────────────────────────────────────────────────── */
#modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.72);z-index:9000;align-items:center;justify-content:center;backdrop-filter:blur(10px)}
#modal-bg.open{display:flex}
#modal-box{
  background:var(--card);border:1px solid var(--cb);border-radius:16px;
  padding:32px;width:100%;max-width:560px;max-height:88vh;overflow-y:auto;
  animation:fadeUp .28s ease
}
.modal-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:24px}
.modal-title{font-family:'Bebas Neue',sans-serif;font-size:21px;letter-spacing:2px;color:var(--gold)}
.modal-close{background:transparent;border:none;font-size:20px;cursor:pointer;color:var(--t2)}
.modal-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.modal-full{grid-column:1/-1}
.modal-footer{display:flex;gap:9px;justify-content:flex-end;margin-top:20px}
.mc-btn{background:transparent;border:1px solid var(--t3);color:var(--t2);padding:10px 20px;border-radius:7px;cursor:pointer;font-size:13.5px}
.ms-btn{background:linear-gradient(135deg,var(--gold),#d4901c);color:#000;border:none;padding:10px 24px;border-radius:7px;cursor:pointer;font-size:13.5px;font-weight:700}

/* ─── TOAST ────────────────────────────────────────────────────────── */
#toast{position:fixed;top:22px;right:22px;z-index:9999;padding:12px 20px;border-radius:8px;font-size:13.5px;font-weight:600;box-shadow:0 8px 28px rgba(0,0,0,.45);animation:slideIn .28s ease;display:none;color:#fff}

/* ─── ADMIN ────────────────────────────────────────────────────────── */
.pg-title{font-family:'Bebas Neue',sans-serif;font-size:28px;letter-spacing:3.5px;color:var(--gold);margin-bottom:5px}
.pg-sub{font-size:13px;color:var(--t2);margin-bottom:26px}
.add-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin-bottom:13px}
.add-row{display:grid;grid-template-columns:1fr 1fr 1fr auto;gap:13px;align-items:end}
.add-btn{padding:11px 20px;background:linear-gradient(135deg,var(--gold),#d4901c);color:#000;border:none;border-radius:8px;font-weight:700;font-size:13.5px;cursor:pointer;white-space:nowrap}
.atbl{width:100%;border-collapse:collapse}
.atbl th{padding:10px 14px;text-align:left;font-size:9px;letter-spacing:1.8px;color:var(--t2);text-transform:uppercase;font-weight:600;border-bottom:1px solid var(--cb);white-space:nowrap}
.atbl td{padding:10px 14px;border-bottom:1px solid rgba(255,255,255,.025);font-size:13px;vertical-align:middle}
.atbl tr:hover td{background:rgba(201,168,76,.025)}
.tbl-name{font-weight:600;color:var(--t1)}
.tbl-oem{font-size:9.5px;color:var(--t2);margin-top:1px;font-family:'Space Mono',monospace}
.tbl-price{font-family:'Bebas Neue',sans-serif;font-size:16px;color:var(--gold)}
.tbl-cat{padding:2px 8px;border-radius:9px;font-size:10px;font-weight:600}
.tbl-ebt{background:var(--gold2);color:var(--gold);border:1px solid rgba(201,168,76,.28);border-radius:5px;padding:4px 9px;cursor:pointer;font-size:11px;font-weight:600}
.tbl-dbt{background:rgba(204,41,54,.1);color:var(--red);border:1px solid rgba(204,41,54,.22);border-radius:5px;padding:4px 8px;cursor:pointer;font-size:11px}

/* ─── INVENTORY ────────────────────────────────────────────────────── */
.inv-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:16px}
.inv-card{border-radius:13px;padding:20px;position:relative;overflow:hidden;transition:transform .22s}
.inv-card:hover{transform:translateY(-3px)}
.inv-accent{position:absolute;top:0;right:0;width:65px;height:65px;border-radius:0 13px 0 65px}
.inv-ico-box{width:36px;height:36px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:18px;margin-bottom:12px}
.inv-cat{font-weight:700;font-size:13.5px}
.inv-ct-sub{font-size:11px;font-weight:600;margin-top:2px}
.inv-mini-row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:7px;margin:12px 0}
.inv-mini{border-radius:7px;padding:8px 6px;text-align:center}
.inv-mini-v{font-family:'Bebas Neue',sans-serif;font-size:19px}
.inv-mini-l{font-size:7.5px;color:var(--t2);text-transform:uppercase;letter-spacing:.8px}
.inv-val-bar{border-radius:7px;padding:8px 11px;display:flex;justify-content:space-between;align-items:center;margin-top:7px}
.inv-prog{height:4px;border-radius:2px;background:rgba(255,255,255,.05);margin-top:9px;overflow:hidden}
.inv-prog-fill{height:100%;background:var(--green);border-radius:2px;transition:width .8s ease}
.inv-pct-txt{font-size:9px;color:var(--t3);margin-top:3px}

/* ─── ANALYTICS ────────────────────────────────────────────────────── */
.ana-2col{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.ana-full{grid-column:1/-1}
.bar-row{margin-bottom:13px}
.bar-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:5px}
.bar-lft{display:flex;align-items:center;gap:6px;font-size:13px;font-weight:500}
.bar-rgt{display:flex;gap:13px;align-items:center}
.bar-pct{font-size:10px;color:var(--t2)}
.bar-v{font-family:'Bebas Neue',sans-serif;font-size:14px}
.bar-track{height:8px;background:rgba(255,255,255,.05);border-radius:4px;overflow:hidden}
.bar-fill{height:100%;border-radius:4px;transition:width 1s ease}
body.light .bar-track{background:rgba(0,0,0,.07)}

/* ─── STOCK BARS ───────────────────────────────────────────────────── */
.stk-item{margin-bottom:16px}
.stk-row{display:flex;justify-content:space-between;margin-bottom:5px}
.stk-lbl{font-size:13px}
.stk-num{font-family:'Bebas Neue',sans-serif;font-size:17px}
.stk-track{height:9px;background:rgba(255,255,255,.05);border-radius:5px;overflow:hidden}
body.light .stk-track{background:rgba(0,0,0,.07)}
.stk-fill{height:100%;border-radius:5px;transition:width 1s ease}
.stk-pct{font-size:9.5px;color:var(--t3);margin-top:3px}

/* ─── BADGE HELPERS ────────────────────────────────────────────────── */
.badge-av{background:rgba(45,158,95,.14);color:#2d9e5f}
.badge-lw{background:rgba(232,93,4,.14);color:#e85d04}
.badge-ot{background:rgba(204,41,54,.14);color:#cc2936}

/* ─── RESPONSIVE ───────────────────────────────────────────────────── */
@media(max-width:980px){
  #sidebar{width:190px}
  #main{margin-left:190px}
  .vs-grid{grid-template-columns:1fr 1fr;gap:12px}
  .vs-grid .gen-btn{grid-column:1/-1}
  .stats-row{grid-template-columns:1fr 1fr}
  .add-grid{grid-template-columns:1fr 1fr}
  .add-row{grid-template-columns:1fr 1fr auto}
  .ana-2col{grid-template-columns:1fr}
  .ana-full{grid-column:1}
}
@media(max-width:700px){
  #sidebar{transform:translateX(-100%)}
  #main{margin-left:0}
  #content{padding:20px 16px}
  .vs-grid{grid-template-columns:1fr}
  .stats-row{grid-template-columns:1fr 1fr}
  .add-grid{grid-template-columns:1fr}
  .add-row{grid-template-columns:1fr}
  .parts-grid{grid-template-columns:1fr}
  .modal-grid{grid-template-columns:1fr}
  .atbl{font-size:12px}
}
</style>
</head>
<body>

<!-- TOAST -->
<div id="toast"></div>

<!-- MODAL -->
<div id="modal-bg">
  <div id="modal-box">
    <div class="modal-head">
      <div class="modal-title">✎ EDIT PART</div>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>
    <div class="modal-grid">
      <div class="modal-full">
        <label class="flabel">Part Name</label>
        <input id="m-name" class="finput" type="text"/>
      </div>
      <div>
        <label class="flabel">Price (₹)</label>
        <input id="m-price" class="finput" type="number"/>
      </div>
      <div>
        <label class="flabel">OEM Number</label>
        <input id="m-oem" class="finput" type="text"/>
      </div>
      <div>
        <label class="flabel">Category</label>
        <select id="m-cat" class="fselect"></select>
      </div>
      <div>
        <label class="flabel">Stock Status</label>
        <select id="m-stock" class="fselect">
          <option value="available">✅ Available</option>
          <option value="low">⚠️ Low Stock</option>
          <option value="out">❌ Out of Stock</option>
        </select>
      </div>
      <div class="modal-full">
        <label class="flabel">Description</label>
        <textarea id="m-desc" class="ftextarea" rows="3"></textarea>
      </div>
    </div>
    <div class="modal-footer">
      <button class="mc-btn hover-btn" onclick="closeModal()">Cancel</button>
      <button class="ms-btn hover-btn" onclick="saveModal()">Save Changes</button>
    </div>
  </div>
</div>

<!-- SIDEBAR -->
<div id="sidebar">
  <div class="sb-brand">
    <div class="sb-logo">AUTOPARTS</div>
    <div class="sb-sub">Kerala Marketplace</div>
  </div>
  <nav class="sb-nav">
    <button class="nav-item active" onclick="gotoPage('marketplace',this)">
      <span class="nav-icon">🏪</span>Marketplace
    </button>
    <button class="nav-item" onclick="gotoPage('admin',this)">
      <span class="nav-icon">⚡</span>Admin Panel
    </button>
    <button class="nav-item" onclick="gotoPage('inventory',this)">
      <span class="nav-icon">📦</span>Inventory
    </button>
    <button class="nav-item" onclick="gotoPage('analytics',this)">
      <span class="nav-icon">📊</span>Analytics
    </button>
  </nav>
  <div class="sb-foot">
    <button class="theme-btn" onclick="toggleTheme()">
      <span id="theme-ico">☀️</span><span id="theme-lbl">Light Mode</span>
    </button>
  </div>
</div>

<!-- MAIN -->
<div id="main">
  <!-- TOPBAR -->
  <div id="topbar">
    <div class="tb-left">
      <div class="tb-car-icon" id="tb-ico">🔧</div>
      <div>
        <div class="tb-title" id="tb-name">Select a vehicle to begin</div>
        <div class="tb-sub" id="tb-sub"></div>
      </div>
    </div>
    <div class="tb-right">
      <div class="tb-pill">🔑 Admin Mode</div>
      <div class="tb-avatar">A</div>
    </div>
  </div>

  <div id="content">

    <!-- ══════════════ MARKETPLACE ══════════════ -->
    <div id="page-marketplace" class="page active">

      <!-- Vehicle Selector -->
      <div class="card card-p" style="margin-bottom:22px">
        <div class="vs-head">
          <div class="vs-head-icon">🚗</div>
          <div>
            <div class="vs-title">VEHICLE SELECTOR</div>
            <div class="vs-desc">Pick brand · model · year — AI generates every part instantly</div>
          </div>
        </div>
        <div class="vs-grid">
          <div>
            <label class="flabel">Brand</label>
            <select id="s-brand" class="fselect" onchange="onBrand()">
              <option value="">Select Brand</option>
            </select>
          </div>
          <div>
            <label class="flabel">Model</label>
            <select id="s-model" class="fselect" onchange="onModel()" disabled>
              <option value="">Select Model</option>
            </select>
          </div>
          <div>
            <label class="flabel">Year</label>
            <select id="s-year" class="fselect" onchange="onYear()" disabled>
              <option value="">Select Year</option>
            </select>
          </div>
          <button id="gen-btn" class="gen-btn hover-btn" onclick="doGenerate()" disabled>
            ⚡ Generate Parts
          </button>
        </div>
        <div id="veh-tags" class="veh-tags" style="display:none"></div>
      </div>

      <!-- AI strips -->
      <div id="ai-load" class="ai-strip" style="display:none">
        <div class="ai-spinner spin-anim"></div>
        <div class="ai-msg">🤖 AI scanning OEM databases · calibrating Kerala market pricing · detecting stock levels…</div>
      </div>
      <div id="ai-sug" class="ai-strip" style="display:none">
        <span style="font-size:20px">🤖</span>
        <div class="ai-msg" id="ai-sug-txt"></div>
        <button class="ai-dismiss" onclick="document.getElementById('ai-sug').style.display='none'">Dismiss</button>
      </div>

      <!-- Stats -->
      <div class="stats-row" id="mkt-stats" style="display:none">
        <div class="card stat-card hover-lift">
          <div class="stat-ico">📦</div>
          <div class="stat-num" id="st-tot" style="color:var(--gold)">0</div>
          <div class="stat-lbl">Total Parts</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">✅</div>
          <div class="stat-num" id="st-av" style="color:var(--green)">0</div>
          <div class="stat-lbl">In Stock</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">⚠️</div>
          <div class="stat-num" id="st-lw" style="color:var(--orange)">0</div>
          <div class="stat-lbl">Low Stock</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">💰</div>
          <div class="stat-num" id="st-val" style="color:var(--neon)">₹0</div>
          <div class="stat-lbl">Catalogue Value</div>
        </div>
      </div>

      <!-- Filter bar -->
      <div class="card filter-bar" id="filter-bar" style="display:none">
        <div class="srch-wrap">
          <span class="srch-ico">🔍</span>
          <input id="srch" class="srch-inp" placeholder="Search parts, OEM numbers…" oninput="renderParts()"/>
        </div>
        <select id="f-cat" class="fbar-sel" onchange="renderParts()">
          <option value="all">All Categories</option>
        </select>
        <select id="f-stk" class="fbar-sel" onchange="renderParts()">
          <option value="all">All Stock</option>
          <option value="available">✅ Available</option>
          <option value="low">⚠️ Low Stock</option>
          <option value="out">❌ Out of Stock</option>
        </select>
        <select id="f-srt" class="fbar-sel" onchange="renderParts()">
          <option value="category">Sort: Category</option>
          <option value="price-asc">Price ↑</option>
          <option value="price-desc">Price ↓</option>
          <option value="name">Name A→Z</option>
        </select>
        <div class="view-tog">
          <button id="vg" class="vbtn active" onclick="setView('grid')">⊞ Grid</button>
          <button id="vl" class="vbtn" onclick="setView('list')">☰ List</button>
        </div>
        <span id="cnt-lbl" class="count-lbl"></span>
      </div>

      <!-- Parts output -->
      <div id="parts-out"></div>

      <!-- Empty state -->
      <div class="empty" id="mkt-empty">
        <div class="empty-ico">🔧</div>
        <div class="empty-title">SELECT A VEHICLE</div>
        <div class="empty-txt">Choose a brand, model, and year above. Our AI engine will instantly generate a complete parts catalogue with OEM numbers, pricing, and real-time stock data for the Kerala market.</div>
      </div>
    </div>

    <!-- ══════════════ ADMIN ══════════════ -->
    <div id="page-admin" class="page">
      <div class="pg-title">ADMIN DASHBOARD</div>
      <div class="pg-sub">Manage parts, pricing, inventory and categories</div>

      <div class="stats-row" style="margin-bottom:26px">
        <div class="card stat-card hover-lift">
          <div class="stat-ico">📦</div>
          <div class="stat-num" id="ad-tot" style="color:var(--gold)">0</div>
          <div class="stat-lbl">Total Parts</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">✅</div>
          <div class="stat-num" id="ad-av" style="color:var(--green)">0</div>
          <div class="stat-lbl">In Stock</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">⚠️</div>
          <div class="stat-num" id="ad-lw" style="color:var(--orange)">0</div>
          <div class="stat-lbl">Low Stock</div>
        </div>
        <div class="card stat-card hover-lift">
          <div class="stat-ico">💰</div>
          <div class="stat-num" id="ad-val" style="color:var(--neon)">₹0</div>
          <div class="stat-lbl">Catalogue Value</div>
        </div>
      </div>

      <!-- Add part -->
      <div class="card card-p" style="margin-bottom:26px">
        <div style="font-family:'Bebas Neue',sans-serif;font-size:18px;letter-spacing:2px;color:var(--gold);margin-bottom:16px">➕ ADD NEW PART</div>
        <div class="add-grid">
          <div>
            <label class="flabel">Part Name *</label>
            <input id="np-name" class="finput" placeholder="e.g. Front Brake Disc"/>
          </div>
          <div>
            <label class="flabel">Price (₹) *</label>
            <input id="np-price" class="finput" type="number" placeholder="e.g. 4800"/>
          </div>
          <div>
            <label class="flabel">OEM Number</label>
            <input id="np-oem" class="finput" placeholder="e.g. TO-FBD-2023-001"/>
          </div>
        </div>
        <div class="add-row">
          <div>
            <label class="flabel">Category</label>
            <select id="np-cat" class="fselect"></select>
          </div>
          <div>
            <label class="flabel">Stock Status</label>
            <select id="np-stk" class="fselect">
              <option value="available">✅ Available</option>
              <option value="low">⚠️ Low Stock</option>
              <option value="out">❌ Out of Stock</option>
            </select>
          </div>
          <div>
            <label class="flabel">Description</label>
            <input id="np-desc" class="finput" placeholder="Short description…"/>
          </div>
          <button class="add-btn hover-btn" onclick="addPart()">Add Part</button>
        </div>
      </div>

      <!-- Table -->
      <div class="card" style="overflow:hidden">
        <div style="padding:16px 20px;border-bottom:1px solid var(--cb);display:flex;justify-content:space-between;align-items:center;gap:14px;flex-wrap:wrap">
          <div style="font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:2px;color:var(--gold)">
            PARTS CATALOGUE <span id="tbl-ct" style="color:var(--t2)">(0)</span>
          </div>
          <input id="tbl-srch" class="srch-inp" style="width:210px" placeholder="🔍  Search table…" oninput="renderTable()"/>
        </div>
        <div style="overflow-x:auto">
          <table class="atbl">
            <thead>
              <tr style="background:rgba(201,168,76,.03)">
                <th>Part Name</th><th>Category</th><th>OEM No</th><th>Price</th><th>Stock</th><th>Actions</th>
              </tr>
            </thead>
            <tbody id="tbl-body"></tbody>
          </table>
          <div id="tbl-more" style="padding:12px 20px;font-size:12px;color:var(--t2);text-align:center;display:none"></div>
        </div>
      </div>
    </div>

    <!-- ══════════════ INVENTORY ══════════════ -->
    <div id="page-inventory" class="page">
      <div class="pg-title">INVENTORY MANAGER</div>
      <div class="pg-sub">Track stock levels and catalogue value by category</div>
      <div id="inv-wrap">
        <div class="inv-grid" id="inv-grid"></div>
        <div class="empty" id="inv-empty" style="display:none">
          <div class="empty-ico">📦</div>
          <div class="empty-title">NO INVENTORY LOADED</div>
          <div class="empty-txt">Generate a vehicle's parts from the Marketplace page first.</div>
        </div>
      </div>
    </div>

    <!-- ══════════════ ANALYTICS ══════════════ -->
    <div id="page-analytics" class="page">
      <div class="pg-title">ANALYTICS & INSIGHTS</div>
      <div class="pg-sub">Catalogue breakdown and Kerala market intelligence</div>
      <div id="ana-wrap">
        <div class="empty">
          <div class="empty-ico">📊</div>
          <div class="empty-title">GENERATE PARTS TO SEE ANALYTICS</div>
          <div class="empty-txt">Select a vehicle from the Marketplace to populate analytics data.</div>
        </div>
      </div>
    </div>

  </div><!-- /content -->
</div><!-- /main -->

<script>
/* ═══════════════════════════════════════════════════════════
   DATA
═══════════════════════════════════════════════════════════ */
const VDB={
  Toyota:{Innova:{y:[2018,2019,2020,2021,2022,2023,2024],t:"MPV",e:"2.4L Diesel"},Fortuner:{y:[2018,2019,2020,2021,2022,2023,2024],t:"SUV",e:"2.8L Diesel"},Camry:{y:[2019,2020,2021,2022,2023,2024],t:"Sedan",e:"2.5L Hybrid"},Glanza:{y:[2021,2022,2023,2024],t:"Hatchback",e:"1.2L Petrol"},Hilux:{y:[2022,2023,2024],t:"Pickup",e:"2.8L Diesel"},Urban_Cruiser:{y:[2021,2022,2023,2024],t:"SUV",e:"1.5L Petrol"}},
  Honda:{City:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Sedan",e:"1.5L Petrol"},Amaze:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Sedan",e:"1.2L Petrol"},WRV:{y:[2020,2021,2022,2023,2024],t:"SUV",e:"1.5L Diesel"},Jazz:{y:[2018,2019,2020,2021,2022],t:"Hatchback",e:"1.2L Petrol"},Elevate:{y:[2023,2024],t:"SUV",e:"1.5L Petrol"}},
  Hyundai:{Creta:{y:[2018,2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.5L Diesel"},Verna:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Sedan",e:"1.5L Petrol"},Tucson:{y:[2020,2021,2022,2023,2024],t:"SUV",e:"2.0L Diesel"},i20:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Hatchback",e:"1.2L Petrol"},Alcazar:{y:[2021,2022,2023,2024],t:"SUV",e:"1.5L Diesel"},Venue:{y:[2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.0L Turbo"}},
  Kia:{Seltos:{y:[2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.5L Turbo"},Carens:{y:[2022,2023,2024],t:"MPV",e:"1.5L Diesel"},Sonet:{y:[2020,2021,2022,2023,2024],t:"SUV",e:"1.0L Turbo"},EV6:{y:[2022,2023,2024],t:"Electric",e:"77.4kWh"}},
  Mahindra:{"Scorpio-N":{y:[2022,2023,2024],t:"SUV",e:"2.2L Diesel"},XUV700:{y:[2021,2022,2023,2024],t:"SUV",e:"2.2L Diesel"},Thar:{y:[2020,2021,2022,2023,2024],t:"Off-Road",e:"2.0L Turbo"},Bolero:{y:[2018,2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.5L Diesel"},XUV400:{y:[2023,2024],t:"Electric",e:"39.4kWh"}},
  Tata:{Nexon:{y:[2018,2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.2L Turbo"},Harrier:{y:[2019,2020,2021,2022,2023,2024],t:"SUV",e:"2.0L Diesel"},Punch:{y:[2021,2022,2023,2024],t:"SUV",e:"1.2L Petrol"},Safari:{y:[2021,2022,2023,2024],t:"SUV",e:"2.0L Diesel"},"Nexon EV":{y:[2020,2021,2022,2023,2024],t:"Electric",e:"40.5kWh"}},
  Maruti:{Swift:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Hatchback",e:"1.2L Petrol"},Baleno:{y:[2018,2019,2020,2021,2022,2023,2024],t:"Hatchback",e:"1.2L Petrol"},Brezza:{y:[2019,2020,2021,2022,2023,2024],t:"SUV",e:"1.5L Petrol"},Ertiga:{y:[2018,2019,2020,2021,2022,2023,2024],t:"MPV",e:"1.5L Petrol"},"Grand Vitara":{y:[2022,2023,2024],t:"SUV",e:"1.5L Hybrid"},Fronx:{y:[2023,2024],t:"Crossover",e:"1.0L Turbo"}},
};

const CATS=[
  {id:"engine",  label:"Engine Parts",      icon:"⚙️", color:"#e85d04"},
  {id:"suspension",label:"Suspension",      icon:"🔩", color:"#7209b7"},
  {id:"brakes",  label:"Brakes",            icon:"🛑", color:"#cc2936"},
  {id:"electrical",label:"Electrical & Lights",icon:"⚡",color:"#3a86ff"},
  {id:"exterior",label:"Exterior Body",     icon:"🚗", color:"#2d6a4f"},
  {id:"interior",label:"Interior",          icon:"🪑", color:"#b5838d"},
  {id:"transmission",label:"Transmission",  icon:"🔄", color:"#6c757d"},
  {id:"cooling", label:"Cooling & AC",      icon:"❄️", color:"#4cc9f0"},
  {id:"exhaust", label:"Exhaust",           icon:"💨", color:"#8b5e3c"},
  {id:"filters", label:"Filters & Fluids",  icon:"🧪", color:"#74b816"},
  {id:"sensors", label:"Sensors & ECU",     icon:"📡", color:"#f72585"},
  {id:"wheels",  label:"Wheels & Tyres",    icon:"🔵", color:"#495057"},
];

/* ─── SVG ICONS ─────────────────────────────────────────────────────── */
function svg(cat,sz=64){
  const s=sz;
  const M={
    engine:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="12" y="20" width="40" height="28" rx="3"/><rect x="4" y="26" width="10" height="16" rx="2"/><rect x="50" y="26" width="10" height="16" rx="2"/><rect x="20" y="12" width="8" height="10" rx="1"/><rect x="36" y="12" width="8" height="10" rx="1"/><circle cx="24" cy="34" r="5"/><circle cx="40" cy="34" r="5"/><line x1="29" y1="34" x2="35" y2="34"/></svg>`,
    suspension:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><line x1="32" y1="8" x2="32" y2="56"/><path d="M20 18Q32 14 44 18"/><path d="M20 30Q32 26 44 30"/><path d="M20 42Q32 38 44 42"/><circle cx="32" cy="56" r="5"/><circle cx="32" cy="8" r="4"/></svg>`,
    brakes:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="32" cy="32" r="20"/><circle cx="32" cy="32" r="12"/><circle cx="32" cy="32" r="4" fill="currentColor" opacity=".25"/><line x1="20" y1="20" x2="26" y2="26"/><line x1="44" y1="20" x2="38" y2="26"/><line x1="20" y1="44" x2="26" y2="38"/><line x1="44" y1="44" x2="38" y2="38"/></svg>`,
    electrical:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="36,8 24,32 36,32 28,56 48,28 34,28"/></svg>`,
    exterior:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8 38Q8 22 20 18L28 12H36L44 18Q56 22 56 38L58 44H6Z"/><ellipse cx="18" cy="46" rx="8" ry="8"/><ellipse cx="46" cy="46" rx="8" ry="8"/><path d="M26 18L28 32H36L38 18"/></svg>`,
    interior:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="12" y="20" width="20" height="28" rx="4"/><rect x="14" y="22" width="16" height="14" rx="2"/><line x1="12" y1="48" x2="32" y2="48" stroke-width="3"/><rect x="36" y="24" width="16" height="6" rx="2"/><line x1="36" y1="30" x2="36" y2="44"/><line x1="52" y1="30" x2="52" y2="44"/><line x1="36" y1="44" x2="52" y2="44"/></svg>`,
    transmission:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="16" cy="32" r="9"/><circle cx="48" cy="32" r="9"/><line x1="25" y1="32" x2="39" y2="32" stroke-width="3"/><circle cx="32" cy="16" r="6"/><line x1="32" y1="22" x2="32" y2="32"/></svg>`,
    cooling:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"><path d="M32 8Q20 20 20 32Q20 44 32 52Q44 44 44 32Q44 20 32 8Z"/><line x1="20" y1="32" x2="44" y2="32"/><path d="M24 20Q32 28 24 44" fill="none"/><path d="M40 20Q32 28 40 44" fill="none"/></svg>`,
    exhaust:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M8 40Q20 36 32 40Q44 44 56 40" stroke-width="2.5"/><path d="M50 30Q54 30 58 34L58 46Q54 50 50 50L46 50L46 30Z"/><path d="M44 24Q34 20 28 24"/></svg>`,
    filters:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><rect x="16" y="10" width="32" height="44" rx="4"/><line x1="22" y1="22" x2="42" y2="22"/><line x1="22" y1="30" x2="42" y2="30"/><line x1="22" y1="38" x2="38" y2="38"/><line x1="22" y1="46" x2="34" y2="46"/></svg>`,
    sensors:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="32" cy="32" r="8"/><path d="M18 18Q10 26 10 32Q10 38 18 46"/><path d="M46 18Q54 26 54 32Q54 38 46 46"/><path d="M22 22Q16 28 16 32Q16 36 22 42"/><path d="M42 22Q48 28 48 32Q48 36 42 42"/></svg>`,
    wheels:`<svg width="${s}" height="${s}" viewBox="0 0 64 64" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="32" cy="32" r="22"/><circle cx="32" cy="32" r="10"/><circle cx="32" cy="32" r="3" fill="currentColor"/><line x1="32" y1="10" x2="32" y2="22"/><line x1="32" y1="42" x2="32" y2="54"/><line x1="10" y1="32" x2="22" y2="32"/><line x1="42" y1="32" x2="54" y2="32"/><line x1="16" y1="16" x2="24" y2="24"/><line x1="40" y1="40" x2="48" y2="48"/><line x1="48" y1="16" x2="40" y2="24"/><line x1="24" y1="40" x2="16" y2="48"/></svg>`,
  };
  return M[cat]||M.engine;
}

/* ─── PARTS GENERATOR ───────────────────────────────────────────────── */
function buildParts(brand,model,year){
  const mp={Toyota:1.2,Honda:1.1,Hyundai:.95,Kia:1.0,Mahindra:.9,Tata:.85,Maruti:.78};
  const m=mp[brand]||1.0;
  const r=v=>Math.round(v*m);
  const o=code=>`${brand.slice(0,2).toUpperCase()}-${code}-${year}`;
  const raw=[
    // ENGINE
    {c:"engine",n:"Engine Assembly (Complete)",     p:r(85000),s:"available",o:o("ENG-001"),d:`Complete engine assembly for ${brand} ${model} ${year}. Block, head, all internals.`},
    {c:"engine",n:"Cylinder Head",                  p:r(18500),s:"available",o:o("CH-002"), d:"Aluminium alloy cylinder head with full gasket set."},
    {c:"engine",n:"Engine Oil Pump",                p:r(4200), s:"available",o:o("OP-003"), d:"High-pressure oil pump for smooth engine lubrication."},
    {c:"engine",n:"Timing Chain Kit",               p:r(6800), s:"low",      o:o("TC-004"), d:"Complete timing chain kit with tensioner, guides, sprockets."},
    {c:"engine",n:"Piston Set (4 pcs)",             p:r(12000),s:"available",o:o("PS-005"), d:"OEM-spec piston set with compression rings for all 4 cylinders."},
    {c:"engine",n:"Camshaft Assembly",              p:r(9500), s:"available",o:o("CAM-006"),d:"Precision-ground camshaft for intake/exhaust valve timing."},
    {c:"engine",n:"Crankshaft",                     p:r(22000),s:"out",      o:o("CRK-007"),d:"Forged steel crankshaft, dynamically balanced."},
    {c:"engine",n:"Valve Cover Gasket Set",         p:r(850),  s:"available",o:o("VCG-008"),d:"High-temperature silicone valve cover gasket kit."},
    {c:"engine",n:"Connecting Rod Set",             p:r(14000),s:"available",o:o("CR-009"), d:"Forged connecting rods, full set, weight-matched."},
    {c:"engine",n:"Engine Mount Set",               p:r(3200), s:"available",o:o("EM-010"), d:"Rubber engine mounts (front, rear, side) set of 3."},
    // SUSPENSION
    {c:"suspension",n:"Front Shock Absorber (Pair)", p:r(7200),s:"available",o:o("FSA-101"),d:"Twin-tube gas-charged front shock absorbers."},
    {c:"suspension",n:"Rear Shock Absorber (Pair)",  p:r(6400),s:"available",o:o("RSA-102"),d:"Rear shock absorbers, OEM specification."},
    {c:"suspension",n:"Front Coil Spring (Pair)",    p:r(3800),s:"available",o:o("FCS-103"),d:"Heavy-duty front coil springs, OEM load rating."},
    {c:"suspension",n:"Control Arm Assembly",        p:r(5500),s:"low",      o:o("CA-104"), d:"Upper/lower control arm with bushings and ball joint."},
    {c:"suspension",n:"Ball Joint Set (×4)",         p:r(2200),s:"available",o:o("BJ-105"), d:"Upper and lower ball joints, set of 4."},
    {c:"suspension",n:"Tie Rod End (Pair)",          p:r(1800),s:"available",o:o("TRE-106"),d:"Inner/outer tie rod ends for precise steering geometry."},
    {c:"suspension",n:"Stabilizer Bar Link Kit",     p:r(950), s:"available",o:o("SBL-107"),d:"Anti-roll bar link kit, front and rear."},
    // BRAKES
    {c:"brakes",n:"Front Brake Disc (Pair)",        p:r(4800),s:"available",o:o("FBD-201"),d:"Ventilated front brake discs, cross-drilled."},
    {c:"brakes",n:"Rear Brake Disc (Pair)",         p:r(4200),s:"available",o:o("RBD-202"),d:"Solid rear brake discs, OEM spec."},
    {c:"brakes",n:"Front Brake Pads Set",           p:r(1800),s:"available",o:o("FBP-203"),d:"Ceramic front brake pads — low dust, low noise."},
    {c:"brakes",n:"Rear Brake Pads Set",            p:r(1600),s:"available",o:o("RBP-204"),d:"OEM-grade rear ceramic brake pads."},
    {c:"brakes",n:"Brake Caliper (Front)",          p:r(5500),s:"low",      o:o("BCA-205"),d:"Remanufactured front brake caliper, ready to fit."},
    {c:"brakes",n:"Brake Master Cylinder",          p:r(3800),s:"available",o:o("BMC-206"),d:"OEM brake master cylinder with reservoir."},
    {c:"brakes",n:"ABS Wheel Speed Sensor (×4)",    p:r(4400),s:"available",o:o("ABS-207"),d:"OEM wheel speed sensors, set of 4, plug-and-play."},
    {c:"brakes",n:"Brake Fluid DOT 4 (1L)",         p:r(380), s:"available",o:o("BFL-208"),d:"Premium DOT 4 brake fluid, 1 litre."},
    // ELECTRICAL
    {c:"electrical",n:"Alternator (120A)",          p:r(8500), s:"available",o:o("ALT-301"),d:"14V/120A alternator, direct OEM replacement."},
    {c:"electrical",n:"Starter Motor",              p:r(6200), s:"available",o:o("STM-302"),d:"High-torque starter motor."},
    {c:"electrical",n:"Headlight Assembly — Left",  p:r(9800), s:"available",o:o("HLL-303"),d:"LED/Halogen headlight, driver side."},
    {c:"electrical",n:"Headlight Assembly — Right", p:r(9800), s:"available",o:o("HLR-304"),d:"LED/Halogen headlight, passenger side."},
    {c:"electrical",n:"Tail Light Assembly — Left", p:r(5500), s:"available",o:o("TLL-305"),d:"Full tail light with LED indicators, driver side."},
    {c:"electrical",n:"Tail Light Assembly — Right",p:r(5500), s:"available",o:o("TLR-306"),d:"Full tail light with LED indicators, passenger side."},
    {c:"electrical",n:"Car Battery 65Ah MF",        p:r(7200), s:"available",o:o("BAT-307"),d:"Maintenance-free 65Ah lead-acid battery."},
    {c:"electrical",n:"Fuse Box Assembly",          p:r(3200), s:"low",      o:o("FBA-308"),d:"Interior + engine bay fuse box assembly."},
    {c:"electrical",n:"Engine Wiring Harness",      p:r(12000),s:"available",o:o("WH-309"), d:"OEM engine wiring harness with all connectors."},
    {c:"electrical",n:"Dual-Tone Horn Set",         p:r(650),  s:"available",o:o("HRN-310"),d:"Dual-tone horn assembly, direct OEM fitment."},
    {c:"electrical",n:"Fog Light Set (Front)",      p:r(3400), s:"available",o:o("FGL-311"),d:"Front fog lights with wiring harness and relay."},
    // EXTERIOR
    {c:"exterior",n:"Front Bumper Assembly",        p:r(8500), s:"available",o:o("FBU-401"),d:"Front bumper with fog bezels and grille mounts."},
    {c:"exterior",n:"Rear Bumper Assembly",         p:r(7200), s:"available",o:o("RBU-402"),d:"Rear bumper with parking sensor holes."},
    {c:"exterior",n:"Front Door Panel — Left",      p:r(18000),s:"low",      o:o("FDL-403"),d:"Front door skin panel, driver side (bare)."},
    {c:"exterior",n:"Front Door Panel — Right",     p:r(18000),s:"available",o:o("FDR-404"),d:"Front door skin panel, passenger side."},
    {c:"exterior",n:"Rear Door Panel — Left",       p:r(16000),s:"available",o:o("RDL-405"),d:"Rear door skin panel, driver side."},
    {c:"exterior",n:"Bonnet / Hood",                p:r(22000),s:"available",o:o("BNT-406"),d:"Steel bonnet panel, unprimed bare metal."},
    {c:"exterior",n:"Boot Lid / Tailgate",          p:r(19000),s:"out",      o:o("BTL-407"),d:"Tailgate panel with wiring provisions."},
    {c:"exterior",n:"Front Fender — Left",          p:r(7500), s:"available",o:o("FFL-408"),d:"Steel front fender/wing panel, driver side."},
    {c:"exterior",n:"Front Fender — Right",         p:r(7500), s:"available",o:o("FFR-409"),d:"Steel front fender/wing panel, passenger side."},
    {c:"exterior",n:"Side Mirror — Left (PWR Fold)",p:r(4200), s:"available",o:o("SML-410"),d:"Power-fold side mirror with indicator, driver side."},
    {c:"exterior",n:"Side Mirror — Right (PWR Fold)",p:r(4200),s:"available",o:o("SMR-411"),d:"Power-fold side mirror with indicator, passenger side."},
    {c:"exterior",n:"Roof Panel",                   p:r(28000),s:"out",      o:o("RFP-412"),d:"Complete steel roof panel assembly."},
    {c:"exterior",n:"Grille Assembly",              p:r(4800), s:"available",o:o("GRL-413"),d:"Front grille assembly with chrome/matte trim."},
    // INTERIOR
    {c:"interior",n:"Dashboard Assembly",           p:r(35000),s:"available",o:o("DSH-501"),d:"Full dashboard assembly with airbag provisions."},
    {c:"interior",n:"Steering Wheel (Leather)",     p:r(8500), s:"available",o:o("STW-502"),d:"Leather-wrapped steering wheel with multifunction controls."},
    {c:"interior",n:"Driver Seat Assembly",         p:r(22000),s:"available",o:o("DSA-503"),d:"Complete driver seat with rails and height adjuster."},
    {c:"interior",n:"Passenger Seat Assembly",      p:r(20000),s:"available",o:o("PSA-504"),d:"Front passenger seat complete assembly."},
    {c:"interior",n:"Rear Seat Assembly",           p:r(28000),s:"low",      o:o("RST-505"),d:"Complete rear bench seat with headrests."},
    {c:"interior",n:"Center Console",               p:r(12000),s:"available",o:o("CCN-506"),d:"Center console with armrest and storage."},
    {c:"interior",n:"Instrument Cluster",           p:r(18000),s:"available",o:o("IC-507"), d:"Digital/analogue instrument cluster, OEM programmed."},
    {c:"interior",n:"Door Trim Panel Set (×4)",     p:r(16000),s:"available",o:o("DTP-508"),d:"Interior door trim panels, all four doors."},
    {c:"interior",n:"Sun Visor Set",                p:r(2800), s:"available",o:o("SV-509"), d:"Driver and passenger sun visors with illuminated mirror."},
    {c:"interior",n:"Floor Mat Set (5 pcs)",        p:r(3500), s:"available",o:o("FM-510"), d:"OEM-style rubber floor mats, set of 5."},
    {c:"interior",n:"Rear-View Mirror",             p:r(1800), s:"available",o:o("RVM-511"),d:"Auto-dimming interior rear-view mirror."},
    // TRANSMISSION
    {c:"transmission",n:"Gearbox Assembly (Manual)",p:r(65000),s:"low",      o:o("GBX-601"),d:"Complete manual gearbox, 5/6-speed."},
    {c:"transmission",n:"Clutch Kit (3-piece)",     p:r(8500), s:"available",o:o("CLT-602"),d:"Clutch disc, pressure plate, release bearing."},
    {c:"transmission",n:"Driveshaft — Front Left",  p:r(9500), s:"available",o:o("DSL-603"),d:"CV driveshaft with inner/outer joints, driver side."},
    {c:"transmission",n:"Driveshaft — Front Right", p:r(9500), s:"available",o:o("DSR-604"),d:"CV driveshaft, passenger side."},
    {c:"transmission",n:"Propeller Shaft",          p:r(18000),s:"out",      o:o("PRS-605"),d:"Universal-jointed propeller shaft for 4WD variants."},
    {c:"transmission",n:"Gear Shift Assembly",      p:r(4200), s:"available",o:o("GSA-606"),d:"Gear selector knob and gaiter assembly."},
    // COOLING & AC
    {c:"cooling",n:"Radiator Assembly",             p:r(12000),s:"available",o:o("RAD-701"),d:"Aluminium core radiator with plastic tanks."},
    {c:"cooling",n:"Radiator Cooling Fan Motor",    p:r(4500), s:"available",o:o("CFM-702"),d:"Electric radiator fan motor and blade assembly."},
    {c:"cooling",n:"AC Compressor",                 p:r(18500),s:"available",o:o("ACC-703"),d:"OEM AC compressor with clutch assembly."},
    {c:"cooling",n:"AC Condenser",                  p:r(8500), s:"available",o:o("ACD-704"),d:"Parallel-flow AC condenser, aluminium core."},
    {c:"cooling",n:"Thermostat + Housing",          p:r(2200), s:"available",o:o("THS-705"),d:"Coolant thermostat housing with gasket."},
    {c:"cooling",n:"Water Pump",                    p:r(3800), s:"available",o:o("WPM-706"),d:"Mechanical water pump with gasket set."},
    {c:"cooling",n:"AC Evaporator Core",            p:r(6800), s:"low",      o:o("EVP-707"),d:"Cabin AC evaporator core assembly."},
    // EXHAUST
    {c:"exhaust",n:"Catalytic Converter (BS6)",     p:r(28000),s:"available",o:o("CAT-801"),d:"OEM catalytic converter, BS6/Euro6 compliant."},
    {c:"exhaust",n:"Exhaust Manifold",              p:r(9500), s:"available",o:o("XM-802"), d:"Cast iron exhaust manifold with gaskets."},
    {c:"exhaust",n:"Rear Muffler / Silencer",       p:r(6500), s:"available",o:o("MFR-803"),d:"Rear silencer box with polished chrome tip."},
    {c:"exhaust",n:"Diesel Particulate Filter",     p:r(38000),s:"low",      o:o("DPF-804"),d:"OEM diesel particulate filter, BS6 spec."},
    // FILTERS
    {c:"filters",n:"Engine Air Filter",             p:r(680),  s:"available",o:o("AIF-901"),d:"High-flow paper/cotton engine air filter."},
    {c:"filters",n:"Engine Oil Filter",             p:r(320),  s:"available",o:o("OIF-902"),d:"Spin-on engine oil filter with anti-drain valve."},
    {c:"filters",n:"Fuel Filter",                   p:r(850),  s:"available",o:o("FLF-903"),d:"In-line fuel filter for petrol/diesel systems."},
    {c:"filters",n:"Cabin AC Filter (Carbon)",      p:r(520),  s:"available",o:o("ACF-904"),d:"Activated carbon cabin air filter."},
    {c:"filters",n:"Engine Oil 5W-30 (5L)",         p:r(1800), s:"available",o:o("EO5-905"),d:"OEM-approved 5W-30 fully synthetic engine oil."},
    // SENSORS
    {c:"sensors",n:"Lambda / O2 Sensor",            p:r(3200), s:"available",o:o("O2S-1001"),d:"Wideband lambda/oxygen sensor for fuel management."},
    {c:"sensors",n:"MAP Sensor",                    p:r(2800), s:"available",o:o("MAP-1002"),d:"Manifold absolute pressure sensor."},
    {c:"sensors",n:"Crankshaft Position Sensor",    p:r(2200), s:"available",o:o("CPS-1003"),d:"Hall-effect crankshaft position sensor."},
    {c:"sensors",n:"Camshaft Position Sensor",      p:r(2400), s:"available",o:o("CAS-1004"),d:"Camshaft sensor for variable valve timing."},
    {c:"sensors",n:"Engine ECU / ECM",              p:r(28000),s:"low",      o:o("ECU-1005"),d:"Engine control module, factory-programmed."},
    {c:"sensors",n:"Parking Sensor Set (×4)",       p:r(3800), s:"available",o:o("PKS-1006"),d:"Ultrasonic parking sensors with buzzer module."},
    {c:"sensors",n:"Temperature Sensor (Coolant)",  p:r(980),  s:"available",o:o("CTS-1007"),d:"Engine coolant temperature sensor."},
    // WHEELS
    {c:"wheels",n:"Alloy Wheel (Single)",           p:r(8500), s:"available",o:o("AWH-1101"),d:"OEM alloy wheel, powder-coated finish."},
    {c:"wheels",n:"Steel Spare Wheel",              p:r(4200), s:"available",o:o("SWH-1102"),d:"T-type steel spare wheel."},
    {c:"wheels",n:"Tyre 205/65 R16 (per unit)",     p:r(5800), s:"available",o:o("TYR-1103"),d:"OEM-spec all-season radial tyre."},
    {c:"wheels",n:"Wheel Hub Bearing (Front)",      p:r(3200), s:"available",o:o("WHB-1104"),d:"Front wheel hub bearing assembly."},
    {c:"wheels",n:"Wheel Lug Nuts (×20)",           p:r(680),  s:"available",o:o("LGN-1105"),d:"OEM chrome lug nuts, set of 20."},
  ];
  return raw.map((p,i)=>({...p,id:`${brand}-${model}-${year}-${i}`}));
}

/* ═══════════════════════════════════════════════════════════
   STATE
═══════════════════════════════════════════════════════════ */
let PARTS=[];
let editId=null;
let viewMode='grid';
let dark=true;
let collapsed={};

/* ═══════════════════════════════════════════════════════════
   HELPERS
═══════════════════════════════════════════════════════════ */
const g=id=>document.getElementById(id);
const fmtINR=n=>n.toLocaleString('en-IN');
const fmtL=n=>`₹${(n/100000).toFixed(1)}L`;
function sleep(ms){return new Promise(r=>setTimeout(r,ms))}
function getCat(id){return CATS.find(c=>c.id===id)||{label:'—',icon:'',color:'#888'}}

function stockBadge(s){
  if(s==='available')return'badge-av';
  if(s==='low')return'badge-lw';
  return'badge-ot';
}
function stockLbl(s){
  if(s==='available')return'✓ In Stock';
  if(s==='low')return'⚠ Low Stock';
  return'✗ Out of Stock';
}

/* ═══════════════════════════════════════════════════════════
   INIT
═══════════════════════════════════════════════════════════ */
function init(){
  // Brand select
  const bs=g('s-brand');
  Object.keys(VDB).forEach(b=>{const o=document.createElement('option');o.value=b;o.textContent=b;bs.appendChild(o)});
  // Category selects
  ['f-cat','np-cat','m-cat'].forEach(id=>{
    const sel=g(id);
    if(!sel)return;
    CATS.forEach(c=>{
      const o=document.createElement('option');
      o.value=c.id;
      o.textContent=`${c.icon} ${c.label}`;
      if(id==='f-cat'&&!sel.querySelector('option[value="all"]')){
        const all=document.createElement('option');all.value='all';all.textContent='All Categories';sel.appendChild(all);
      }
      sel.appendChild(o);
    });
  });
}

/* ═══════════════════════════════════════════════════════════
   VEHICLE SELECTORS
═══════════════════════════════════════════════════════════ */
function onBrand(){
  const b=g('s-brand').value;
  const ms=g('s-model'),ys=g('s-year');
  ms.innerHTML='<option value="">Select Model</option>';
  ys.innerHTML='<option value="">Select Year</option>';
  ms.disabled=!b; ys.disabled=true; g('gen-btn').disabled=true;
  g('veh-tags').style.display='none';
  if(!b)return;
  Object.keys(VDB[b]).forEach(m=>{const o=document.createElement('option');o.value=m;o.textContent=m;ms.appendChild(o)});
}
function onModel(){
  const b=g('s-brand').value,m=g('s-model').value;
  const ys=g('s-year');
  ys.innerHTML='<option value="">Select Year</option>';
  ys.disabled=!m; g('gen-btn').disabled=true;
  if(!m)return;
  [...VDB[b][m].y].reverse().forEach(y=>{const o=document.createElement('option');o.value=y;o.textContent=y;ys.appendChild(o)});
}
function onYear(){
  const b=g('s-brand').value,m=g('s-model').value,y=g('s-year').value;
  g('gen-btn').disabled=!y;
  if(!y){g('veh-tags').style.display='none';return;}
  const info=VDB[b][m];
  g('veh-tags').style.display='flex';
  g('veh-tags').innerHTML=[{l:'Brand',v:b},{l:'Model',v:m},{l:'Year',v:y},{l:'Type',v:info.t},{l:'Engine',v:info.e}]
    .map(({l,v})=>`<div class="veh-tag"><div class="veh-tag-l">${l}</div><div class="veh-tag-v">${v}</div></div>`).join('');
}

/* ═══════════════════════════════════════════════════════════
   GENERATE
═══════════════════════════════════════════════════════════ */
async function doGenerate(){
  const b=g('s-brand').value,m=g('s-model').value,y=parseInt(g('s-year').value);
  if(!b||!m||!y)return;
  g('ai-sug').style.display='none';
  g('ai-load').style.display='flex';
  g('mkt-empty').style.display='none';
  g('parts-out').innerHTML='';
  g('mkt-stats').style.display='none';
  g('filter-bar').style.display='none';
  const btn=g('gen-btn');
  btn.disabled=true;
  btn.innerHTML='<span class="spin-anim">⟳</span> Generating…';
  await sleep(1900);
  PARTS=buildParts(b,m,y);
  g('ai-load').style.display='none';
  btn.disabled=false;
  btn.innerHTML='⚡ Generate Parts';
  // Show AI suggestion
  g('ai-sug-txt').textContent=`🤖 AI generated ${PARTS.length} parts for ${b} ${m} ${y}. Prices calibrated to Kerala market. 3 parts flagged for stock review. DPF & Crankshaft currently scarce.`;
  g('ai-sug').style.display='flex';
  // Update topbar
  g('tb-ico').textContent='🚗';
  g('tb-name').textContent=`${b} ${m} ${y}`;
  g('tb-sub').textContent=`${PARTS.length} parts loaded`;
  g('mkt-stats').style.display='grid';
  g('filter-bar').style.display='flex';
  updateStats();
  renderParts();
  toast(`✅ ${PARTS.length} parts generated for ${b} ${m} ${y}`,'success');
}

/* ═══════════════════════════════════════════════════════════
   STATS
═══════════════════════════════════════════════════════════ */
function updateStats(){
  const tot=PARTS.length;
  const av=PARTS.filter(p=>p.s==='available').length;
  const lw=PARTS.filter(p=>p.s==='low').length;
  const val=PARTS.reduce((a,p)=>a+p.p,0);
  ['st-tot','ad-tot'].forEach(id=>g(id)&&(g(id).textContent=tot));
  ['st-av','ad-av'].forEach(id=>g(id)&&(g(id).textContent=av));
  ['st-lw','ad-lw'].forEach(id=>g(id)&&(g(id).textContent=lw));
  ['st-val','ad-val'].forEach(id=>g(id)&&(g(id).textContent=fmtL(val)));
  g('tbl-ct')&&(g('tbl-ct').textContent=`(${tot})`);
}

/* ═══════════════════════════════════════════════════════════
   FILTER & RENDER PARTS
═══════════════════════════════════════════════════════════ */
function getFiltered(){
  const q=(g('srch')||{}).value||'';
  const cat=(g('f-cat')||{}).value||'all';
  const stk=(g('f-stk')||{}).value||'all';
  const srt=(g('f-srt')||{}).value||'category';
  let list=PARTS.filter(p=>{
    const qs=q.toLowerCase();
    return(!q||p.n.toLowerCase().includes(qs)||p.o.toLowerCase().includes(qs)||p.d.toLowerCase().includes(qs))
      &&(cat==='all'||p.c===cat)
      &&(stk==='all'||p.s===stk);
  });
  if(srt==='price-asc')list.sort((a,b)=>a.p-b.p);
  else if(srt==='price-desc')list.sort((a,b)=>b.p-a.p);
  else if(srt==='name')list.sort((a,b)=>a.n.localeCompare(b.n));
  else list.sort((a,b)=>a.c.localeCompare(b.c));
  return list;
}

function renderParts(){
  const list=getFiltered();
  const out=g('parts-out');
  const lbl=g('cnt-lbl');
  if(lbl)lbl.textContent=`${list.length} parts`;
  if(!list.length){out.innerHTML=`<div class="empty"><div class="empty-ico">🔍</div><div class="empty-title">NO PARTS FOUND</div><div class="empty-txt">Adjust your search or filter criteria.</div></div>`;return;}
  const srt=(g('f-srt')||{}).value||'category';
  if(srt!=='category'){
    out.innerHTML=`<div class="${viewMode==='grid'?'parts-grid':'parts-list'}">${list.map(p=>viewMode==='grid'?cardHTML(p):rowHTML(p)).join('')}</div>`;
    return;
  }
  const grouped={};
  CATS.forEach(c=>{const ps=list.filter(p=>p.c===c.id);if(ps.length)grouped[c.id]={...c,parts:ps}});
  out.innerHTML=Object.values(grouped).map(cat=>catSectionHTML(cat)).join('');
}

function catSectionHTML(cat){
  const col=collapsed[cat.id];
  const inner=col?'':(viewMode==='grid'
    ?`<div class="parts-grid">${cat.parts.map(p=>cardHTML(p)).join('')}</div>`
    :`<div class="parts-list">${cat.parts.map(p=>rowHTML(p)).join('')}</div>`);
  return `<div class="cat-sec fade-up">
    <div class="cat-hdr" onclick="toggleCat('${cat.id}')">
      <div class="cat-ico-box" style="background:${cat.color}18;border:1px solid ${cat.color}30">${cat.icon}</div>
      <div>
        <div class="cat-name-txt" style="color:${cat.color}">${cat.label.toUpperCase()}</div>
        <div class="cat-sub">${cat.parts.length} parts</div>
      </div>
      <div class="cat-pill" style="background:${cat.color}18;color:${cat.color}">${cat.parts.length}</div>
      <div class="cat-arr">${col?'▶':'▼'}</div>
    </div>
    ${inner}
  </div>`;
}

function cardHTML(p){
  const cat=getCat(p.c);
  return `<div class="pcard">
    <div class="pcard-img" style="background:linear-gradient(135deg,${cat.color}08,${cat.color}1a);border-bottom:1px solid ${cat.color}20">
      <div style="color:${cat.color}">${svg(p.c,66)}</div>
      <div class="pcard-stock ${stockBadge(p.s)}">${stockLbl(p.s)}</div>
      <div class="pcard-oem" style="background:${cat.color}1a;color:${cat.color}">${p.o}</div>
    </div>
    <div class="pcard-body">
      <div class="pcard-name">${p.n}</div>
      <div class="pcard-desc">${p.d}</div>
      <div class="price-row" id="pr-${p.id}">
        <div class="price-num">₹${fmtINR(p.p)}</div>
        <button class="price-ebtn hover-btn" onclick="startPrice('${p.id}')">✎ Edit</button>
      </div>
      <select class="stock-sel" onchange="updateField('${p.id}','s',this.value)" style="border-color:${cat.color}33">
        <option value="available" ${p.s==='available'?'selected':''}>✅ Available</option>
        <option value="low" ${p.s==='low'?'selected':''}>⚠️ Low Stock</option>
        <option value="out" ${p.s==='out'?'selected':''}>❌ Out of Stock</option>
      </select>
      <div class="pcard-actions">
        <button class="fedit-btn hover-btn" style="background:${cat.color}18;color:${cat.color};border:1px solid ${cat.color}30" onclick="openModal('${p.id}')">✎ Full Edit</button>
        <button class="pdel-btn hover-btn" onclick="delPart('${p.id}')">🗑</button>
      </div>
    </div>
  </div>`;
}

function rowHTML(p){
  const cat=getCat(p.c);
  return `<div class="prow">
    <div class="prow-ico" style="background:${cat.color}14;color:${cat.color}">${svg(p.c,26)}</div>
    <div style="flex:2"><div class="prow-name">${p.n}</div><div class="prow-oem">${p.o}</div></div>
    <div class="prow-price">₹${fmtINR(p.p)}</div>
    <div class="prow-stock"><span class="pcard-stock ${stockBadge(p.s)}" style="position:relative;top:auto;right:auto;display:inline-block">${stockLbl(p.s)}</span></div>
    <div class="prow-acts">
      <button class="tbl-ebt hover-btn" onclick="openModal('${p.id}')">Edit</button>
      <button class="tbl-dbt hover-btn" onclick="delPart('${p.id}')">Del</button>
    </div>
  </div>`;
}

function toggleCat(id){collapsed[id]=!collapsed[id];renderParts()}
function setView(v){
  viewMode=v;
  g('vg').className='vbtn'+(v==='grid'?' active':'');
  g('vl').className='vbtn'+(v==='list'?' active':'');
  renderParts();
}

/* ═══════════════════════════════════════════════════════════
   INLINE PRICE EDIT
═══════════════════════════════════════════════════════════ */
function startPrice(id){
  const p=PARTS.find(x=>x.id===id);if(!p)return;
  const row=g(`pr-${id}`);if(!row)return;
  row.innerHTML=`<span style="color:var(--gold);font-weight:700">₹</span>
    <input class="price-inp" id="pe-${id}" type="number" value="${p.p}" onkeydown="if(event.key==='Enter')savePrice('${id}')"/>
    <button class="psave-btn" onclick="savePrice('${id}')">✓</button>
    <button class="pcancel-btn" onclick="cancelPrice('${id}')">✗</button>`;
  const inp=g(`pe-${id}`);if(inp){inp.focus();inp.select()}
}
function savePrice(id){
  const inp=g(`pe-${id}`);if(!inp)return;
  const v=Number(inp.value);
  if(!v||v<=0){toast('Enter a valid price','error');return}
  updateField(id,'p',v);
  const row=g(`pr-${id}`);
  if(row)row.innerHTML=`<div class="price-num">₹${fmtINR(v)}</div><button class="price-ebtn hover-btn" onclick="startPrice('${id}')">✎ Edit</button>`;
  updateStats();toast('Price updated ✓','success');
}
function cancelPrice(id){
  const p=PARTS.find(x=>x.id===id);if(!p)return;
  const row=g(`pr-${id}`);
  if(row)row.innerHTML=`<div class="price-num">₹${fmtINR(p.p)}</div><button class="price-ebtn hover-btn" onclick="startPrice('${id}')">✎ Edit</button>`;
}

/* ═══════════════════════════════════════════════════════════
   CRUD
═══════════════════════════════════════════════════════════ */
function updateField(id,field,val){
  PARTS=PARTS.map(p=>p.id===id?{...p,[field]:field==='p'?Number(val):val}:p);
}
function delPart(id){
  if(!confirm('Delete this part?'))return;
  PARTS=PARTS.filter(p=>p.id!==id);
  updateStats();renderParts();renderTable();renderInventory();renderAnalytics();
  toast('Part removed','error');
}
function addPart(){
  const n=g('np-name').value.trim();
  const price=Number(g('np-price').value);
  const oem=g('np-oem').value.trim();
  const cat=g('np-cat').value;
  const stk=g('np-stk').value;
  const desc=g('np-desc').value.trim();
  if(!n||!price){toast('Name and price are required','error');return}
  PARTS=[...PARTS,{id:`custom-${Date.now()}`,c:cat,n,p:price,s:stk,o:oem||'N/A',d:desc||`${n} — custom added.`}];
  ['np-name','np-price','np-oem','np-desc'].forEach(id=>{if(g(id))g(id).value=''});
  updateStats();renderParts();renderTable();renderInventory();renderAnalytics();
  toast(`✅ "${n}" added to catalogue`,'success');
}

/* ═══════════════════════════════════════════════════════════
   MODAL
═══════════════════════════════════════════════════════════ */
function openModal(id){
  editId=id;
  const p=PARTS.find(x=>x.id===id);if(!p)return;
  g('m-name').value=p.n; g('m-price').value=p.p;
  g('m-oem').value=p.o;  g('m-desc').value=p.d;
  g('m-cat').value=p.c;  g('m-stock').value=p.s;
  g('modal-bg').classList.add('open');
}
function closeModal(){g('modal-bg').classList.remove('open');editId=null}
function saveModal(){
  if(!editId)return;
  const n=g('m-name').value.trim(),pr=Number(g('m-price').value);
  if(!n||!pr){toast('Name and price required','error');return}
  PARTS=PARTS.map(p=>p.id===editId?{...p,n,p:pr,o:g('m-oem').value.trim(),c:g('m-cat').value,s:g('m-stock').value,d:g('m-desc').value.trim()}:p);
  closeModal();updateStats();renderParts();renderTable();renderInventory();renderAnalytics();
  toast('Part updated ✓','success');
}

/* ═══════════════════════════════════════════════════════════
   ADMIN TABLE
═══════════════════════════════════════════════════════════ */
function renderTable(){
  const q=(g('tbl-srch')||{}).value||'';
  const filtered=PARTS.filter(p=>!q||p.n.toLowerCase().includes(q.toLowerCase())||p.o.toLowerCase().includes(q.toLowerCase()));
  const show=filtered.slice(0,100);
  const tbody=g('tbl-body');if(!tbody)return;
  g('tbl-ct')&&(g('tbl-ct').textContent=`(${filtered.length})`);
  tbody.innerHTML=show.map(p=>{
    const cat=getCat(p.c);
    return `<tr>
      <td><div class="tbl-name">${p.n}</div><div class="tbl-oem">${p.o}</div></td>
      <td><span class="tbl-cat" style="background:${cat.color}18;color:${cat.color}">${cat.icon} ${cat.label}</span></td>
      <td style="font-family:'Space Mono',monospace;font-size:10px;color:var(--t2)">${p.o}</td>
      <td><div class="tbl-price">₹${fmtINR(p.p)}</div></td>
      <td><span class="pcard-stock ${stockBadge(p.s)}" style="position:relative;top:auto;right:auto;display:inline-block">${stockLbl(p.s)}</span></td>
      <td><div style="display:flex;gap:5px">
        <button class="tbl-ebt hover-btn" onclick="openModal('${p.id}')">Edit</button>
        <button class="tbl-dbt hover-btn" onclick="delPart('${p.id}')">Del</button>
      </div></td>
    </tr>`;
  }).join('');
  const more=g('tbl-more');
  if(more){more.style.display=filtered.length>100?'block':'none';more.textContent=`Showing 100 of ${filtered.length} — use search to narrow.`}
}

/* ═══════════════════════════════════════════════════════════
   INVENTORY
═══════════════════════════════════════════════════════════ */
function renderInventory(){
  const grid=g('inv-grid'),empty=g('inv-empty');
  if(!grid)return;
  if(!PARTS.length){grid.innerHTML='';if(empty)empty.style.display='block';return}
  if(empty)empty.style.display='none';
  const cats=CATS.map(c=>({
    ...c,
    count:PARTS.filter(p=>p.c===c.id).length,
    av:PARTS.filter(p=>p.c===c.id&&p.s==='available').length,
    lw:PARTS.filter(p=>p.c===c.id&&p.s==='low').length,
    ot:PARTS.filter(p=>p.c===c.id&&p.s==='out').length,
    val:PARTS.filter(p=>p.c===c.id).reduce((a,p)=>a+p.p,0),
  })).filter(c=>c.count>0);
  grid.innerHTML=cats.map(c=>{
    const pct=c.count?Math.round(c.av/c.count*100):0;
    return `<div class="inv-card card" style="border:1px solid ${c.color}20">
      <div class="inv-accent" style="background:${c.color}08"></div>
      <div class="inv-ico-box" style="background:${c.color}1a">${c.icon}</div>
      <div class="inv-cat">${c.label}</div>
      <div class="inv-ct-sub" style="color:${c.color}">${c.count} parts total</div>
      <div class="inv-mini-row">
        <div class="inv-mini" style="background:rgba(45,158,95,.1)"><div class="inv-mini-v" style="color:var(--green)">${c.av}</div><div class="inv-mini-l">Available</div></div>
        <div class="inv-mini" style="background:rgba(232,93,4,.1)"><div class="inv-mini-v" style="color:var(--orange)">${c.lw}</div><div class="inv-mini-l">Low</div></div>
        <div class="inv-mini" style="background:rgba(204,41,54,.1)"><div class="inv-mini-v" style="color:var(--red)">${c.ot}</div><div class="inv-mini-l">Out</div></div>
      </div>
      <div class="inv-val-bar" style="background:rgba(201,168,76,.06)">
        <span style="font-size:11px;color:var(--t2)">Catalogue Value</span>
        <span style="font-family:'Bebas Neue',sans-serif;font-size:15px;color:var(--gold)">₹${(c.val/1000).toFixed(0)}K</span>
      </div>
      <div class="inv-prog"><div class="inv-prog-fill" style="width:${pct}%"></div></div>
      <div class="inv-pct-txt">${pct}% availability</div>
    </div>`;
  }).join('');
}

/* ═══════════════════════════════════════════════════════════
   ANALYTICS
═══════════════════════════════════════════════════════════ */
function renderAnalytics(){
  const wrap=g('ana-wrap');if(!wrap)return;
  if(!PARTS.length){
    wrap.innerHTML=`<div class="empty"><div class="empty-ico">📊</div><div class="empty-title">GENERATE PARTS FIRST</div><div class="empty-txt">Select a vehicle from Marketplace to populate analytics.</div></div>`;
    return;
  }
  const total=PARTS.length;
  const totVal=PARTS.reduce((a,p)=>a+p.p,0);
  const cats=CATS.map(c=>({...c,count:PARTS.filter(p=>p.c===c.id).length,val:PARTS.filter(p=>p.c===c.id).reduce((a,p)=>a+p.p,0)})).filter(c=>c.count>0).sort((a,b)=>b.val-a.val);
  const catBars=cats.map(c=>{
    const pct=totVal?(c.val/totVal*100).toFixed(1):0;
    return `<div class="bar-row"><div class="bar-head">
      <div class="bar-lft">${c.icon} ${c.label} <span style="font-size:10px;color:var(--t2)">(${c.count})</span></div>
      <div class="bar-rgt"><span class="bar-pct">${pct}%</span><span class="bar-v" style="color:${c.color}">₹${(c.val/1000).toFixed(1)}K</span></div>
    </div><div class="bar-track"><div class="bar-fill" style="width:${pct}%;background:linear-gradient(90deg,${c.color},${c.color}80)"></div></div></div>`;
  }).join('');
  const av=PARTS.filter(p=>p.s==='available').length;
  const lw=PARTS.filter(p=>p.s==='low').length;
  const ot=PARTS.filter(p=>p.s==='out').length;
  const stkBars=[{l:'In Stock',v:av,c:'var(--green)'},{l:'Low Stock',v:lw,c:'var(--orange)'},{l:'Out of Stock',v:ot,c:'var(--red)'}].map(s=>{
    const pct=total?(s.v/total*100).toFixed(1):0;
    return `<div class="stk-item"><div class="stk-row"><span class="stk-lbl">${s.l}</span><span class="stk-num" style="color:${s.c}">${s.v}</span></div>
    <div class="stk-track"><div class="stk-fill" style="width:${pct}%;background:${s.c}"></div></div>
    <div class="stk-pct">${pct}% of catalogue</div></div>`;
  }).join('');
  const priceR=[{l:'Under ₹1K',mn:0,mx:1000},{l:'₹1K–₹5K',mn:1000,mx:5000},{l:'₹5K–₹20K',mn:5000,mx:20000},{l:'₹20K–₹50K',mn:20000,mx:50000},{l:'₹50K+',mn:50000,mx:Infinity}];
  const priceBars=priceR.map(r=>{
    const cnt=PARTS.filter(p=>p.p>=r.mn&&p.p<r.mx).length;
    const pct=total?(cnt/total*100).toFixed(1):0;
    return `<div class="bar-row"><div class="bar-head"><span style="font-size:12px;color:var(--t2)">${r.l}</span><span style="font-size:12px;color:var(--gold);font-weight:600">${cnt} parts</span></div>
    <div class="bar-track"><div class="bar-fill" style="width:${pct}%;background:linear-gradient(90deg,var(--gold),var(--neon))"></div></div></div>`;
  }).join('');
  wrap.innerHTML=`
    <div class="card card-p ana-full" style="margin-bottom:20px">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:17px;letter-spacing:2px;color:var(--gold);margin-bottom:18px">CATALOGUE VALUE BY CATEGORY</div>
      ${catBars}
    </div>
    <div class="ana-2col">
      <div class="card card-p">
        <div style="font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:2px;color:var(--gold);margin-bottom:16px">STOCK DISTRIBUTION</div>
        ${stkBars}
      </div>
      <div class="card card-p">
        <div style="font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:2px;color:var(--gold);margin-bottom:16px">PRICE DISTRIBUTION</div>
        ${priceBars}
      </div>
    </div>`;
}

/* ═══════════════════════════════════════════════════════════
   PAGE NAVIGATION
═══════════════════════════════════════════════════════════ */
function gotoPage(page,btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(b=>b.classList.remove('active'));
  g(`page-${page}`).classList.add('active');
  if(btn)btn.classList.add('active');
  if(page==='admin'){updateStats();renderTable()}
  if(page==='inventory')renderInventory();
  if(page==='analytics')renderAnalytics();
}

/* ═══════════════════════════════════════════════════════════
   TOAST
═══════════════════════════════════════════════════════════ */
function toast(msg,type='success'){
  const el=g('toast');
  el.textContent=msg;
  el.style.background=type==='error'?'#cc2936':'#2d9e5f';
  el.style.display='block';
  clearTimeout(el._t);
  el._t=setTimeout(()=>el.style.display='none',3100);
}

/* ═══════════════════════════════════════════════════════════
   THEME
═══════════════════════════════════════════════════════════ */
function toggleTheme(){
  dark=!dark;
  document.body.classList.toggle('light',!dark);
  g('theme-ico').textContent=dark?'☀️':'🌙';
  g('theme-lbl').textContent=dark?'Light Mode':'Dark Mode';
}

/* ═══════════════════════════════════════════════════════════
   KEYBOARD
═══════════════════════════════════════════════════════════ */
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeModal()});
g('modal-bg').addEventListener('click',e=>{if(e.target===e.currentTarget)closeModal()});

/* ─── BOOT ─────────────────────────────────────────────── */
init();
</script>
</body>
</html>
