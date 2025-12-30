<!doctype html>
<html lang="tr">
<head>
<meta charset="utf-8">
<title>Ahmet Tekeli Kuaför • Online Randevu</title>
<meta name="viewport" content="width=device-width,initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#e5e7eb;
  --ink:#111827;
  --muted:#6b7280;
  --brand:#d4af37;
  --danger:#ef4444;
  --ok:#10b981;
}

*{box-sizing:border-box;margin:0;padding:0}

html,body{
  font:15px/1.5 "Inter",system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial;
  background:var(--bg);
  color:var(--ink);
}

.bg{
  position:fixed;
  inset:0;
  z-index:-2;
  background:
    url("arka-plan.jpg") center/cover no-repeat,
    radial-gradient(circle at 10% 0%,rgba(148,163,184,.4),transparent 20%);
  filter:blur(10px);
}
.bg-overlay{
  position:fixed;
  inset:0;
  z-index:-1;
  background:
    linear-gradient(to bottom,rgba(255,255,255,.78),rgba(209,213,219,.95)),
    radial-gradient(circle at top,rgba(255,255,255,.6),transparent 55%);
}

body{
  min-height:100vh;
  display:flex;
  align-items:flex-start;
  justify-content:center;
  padding:18px 10px 28px;
}

.wrap{
  width:100%;
  max-width:420px;
  position:relative;
  border-radius:32px;
  padding:18px 16px 22px;
  background:linear-gradient(135deg,rgba(243,244,246,.8),rgba(229,231,235,.85));
  box-shadow:
    0 18px 55px rgba(15,23,42,.28),
    0 0 0 1px rgba(148,163,184,.35);
  backdrop-filter:blur(22px) saturate(140%);
}

.logo-wrap{
  display:flex;
  justify-content:center;
  margin-bottom:8px;
}
.logo-circle{
  width:86px;
  height:86px;
  border-radius:999px;
  background:url("logo.png") center/100% 100% no-repeat;
  box-shadow:0 18px 40px rgba(0,0,0,.35);
  border:4px solid rgba(248,250,251,.98);
}

.top-actions{
  position:absolute;
  top:12px;
  right:12px;
  display:flex;
  flex-direction:column;
  gap:6px;
}
.btn-top{
  border-radius:999px;
  padding:7px 13px;
  border:1px solid rgba(209,213,219,.9);
  cursor:pointer;
  font-size:12px;
  font-weight:600;
  background:rgba(255,255,255,.96);
  color:#111827;
  box-shadow:0 10px 26px rgba(15,23,42,.25);
  backdrop-filter:blur(18px);
}
.btn-top span{opacity:.95}

.card{
  border-radius:26px;
  padding:16px 14px 18px;
  border:1px solid rgba(209,213,219,.95);
  background:linear-gradient(145deg,rgba(255,255,255,.98),rgba(243,244,246,.98));
  box-shadow:
    0 18px 40px rgba(15,23,42,.22),
    0 0 0 1px rgba(148,163,184,.25);
  color:var(--ink);
}

.card-header{
  text-align:center;
  margin-bottom:14px;
}
.brand-title{
  font-size:24px;
  font-weight:800;
  letter-spacing:.14em;
  text-transform:uppercase;
}
.brand-sub{
  margin-top:2px;
  font-size:11px;
  letter-spacing:.25em;
  text-transform:uppercase;
  color:var(--muted);
}
.rating{
  margin-top:8px;
  display:inline-flex;
  align-items:center;
  gap:6px;
  padding:4px 10px;
  border-radius:999px;
  font-size:11px;
  background:rgba(255,255,255,.96);
  border:1px solid rgba(209,213,219,.95);
  box-shadow:0 10px 24px rgba(15,23,42,.2);
}
.rating .star{
  width:12px;height:12px;
  clip-path:polygon(50% 0%,63% 38%,100% 38%,69% 59%,82% 100%,50% 76%,18% 100%,31% 59%,0 38%,37% 38%);
  background:var(--brand);
}

.section-title{
  font-size:12px;
  font-weight:600;
  margin:8px 0 4px;
  color:#111827;
}
.input,.select,.date-input{
  width:100%;
  border-radius:13px;
  padding:8px 11px;
  border:1px solid rgba(209,213,219,.95);
  background:linear-gradient(135deg,rgba(255,255,255,.99),rgba(249,250,251,.99));
  color:#0f172a;
  font-size:13px;
}
.input::placeholder{color:#9ca3af}
.date-input{padding:6px 9px;font-size:10px;}

.row{display:flex;flex-wrap:wrap;gap:6px;}
.row > *{flex:1;min-width:0;}

.barber-choices{display:flex;flex-wrap:wrap;gap:6px;}
.barber-chip{
  display:flex;align-items:center;gap:6px;
  padding:5px 9px;border-radius:999px;
  background:linear-gradient(135deg,rgba(243,244,246,1),rgba(229,231,235,1));
  border:1px solid rgba(209,213,219,1);
  cursor:pointer;font-size:11px;
  box-shadow:0 6px 14px rgba(15,23,42,.12);
}
.barber-chip.selected{
  background:linear-gradient(135deg,#fde68a,var(--brand));
  color:#111827;border-color:transparent;
}
.barber-avatar{
  width:24px;height:24px;border-radius:999px;
  overflow:hidden;flex-shrink:0;
  background:rgba(31,41,55,.08);
  display:flex;align-items:center;justify-content:center;
  font-size:10px;font-weight:700;text-transform:uppercase;
}
.barber-avatar img{width:100%;height:100%;object-fit:cover;}

.slot-grid{
  margin-top:6px;
  display:grid;
  grid-template-columns:repeat(4,minmax(0,1fr));
  gap:7px;
}
.slot{
  border-radius:12px;
  padding:7px 0;
  border:1px solid rgba(209,213,219,1);
  background:rgba(255,255,255,.99);
  color:#111827;
  font-weight:600;font-size:11px;
  cursor:pointer;
  box-shadow:0 10px 22px rgba(15,23,42,.15);
}
.slot.selected{
  background:linear-gradient(135deg,#fde68a,var(--brand));
  color:#111827;border-color:transparent;
}
.slot.disabled{opacity:.28;pointer-events:none;}

.btn-book{
  width:100%;
  margin-top:14px;
  border-radius:999px;
  padding:11px 18px;
  border:none;cursor:pointer;
  font-size:13px;font-weight:800;
  letter-spacing:.18em;text-transform:uppercase;
  background:linear-gradient(135deg,#fef3c7,#facc15,var(--brand));
  color:#111827;
  box-shadow:
    0 18px 42px rgba(0,0,0,.18),
    0 0 0 1px rgba(180,148,60,.55);
}

.helper{margin-top:6px;font-size:11px;color:var(--muted);}

.app-list{list-style:none;margin-top:4px;}
.app-item{
  display:flex;flex-wrap:wrap;justify-content:space-between;
  gap:6px;padding:7px 7px;border-radius:13px;
  border:1px solid rgba(148,163,184,.7);
  background:radial-gradient(circle at top,rgba(15,23,42,.96),rgba(15,23,42,.98));
  font-size:11px;backdrop-filter:blur(14px);
  color:#e5e7eb;
}
.app-main{display:flex;flex-direction:column;gap:2px;}
.app-title{font-weight:600;}
.app-meta{color:#cbd5f5;}
.app-actions{display:flex;gap:5px;align-items:center;}

.btn-mini{
  border-radius:999px;border:none;
  padding:4px 9px;font-size:10px;
  cursor:pointer;font-weight:600;
}
.btn-mini.del{
  background:rgba(239,68,68,.12);
  color:var(--danger);
  border:1px solid rgba(248,113,113,.7);
}
.btn-mini.wp{
  background:rgba(34,197,94,.12);
  color:#22c55e;
  border:1px solid rgba(34,197,94,.7);
}
.btn-mini.ok{
  background:rgba(16,185,129,.12);
  color:var(--ok);
  border:1px solid rgba(16,185,129,.7);
}

.panel{
  margin-top:10px;
  background:radial-gradient(circle at top,rgba(15,23,42,.96),rgba(15,23,42,.99));
  border-radius:20px;
  padding:9px 9px 10px;
  border:1px solid rgba(148,163,184,.6);
  backdrop-filter:blur(16px);
  color:#e5e7eb;
}

.modal-backdrop{
  position:fixed;inset:0;
  background:rgba(15,23,42,.82);
  display:none;align-items:center;justify-content:center;
  z-index:30;
}
.modal{
  width:100%;max-width:380px;
  background:radial-gradient(circle at top,rgba(15,23,42,.96),rgba(15,23,42,.99));
  border-radius:24px;padding:14px 14px 14px;
  border:1px solid rgba(148,163,184,.7);
  box-shadow:0 24px 70px rgba(0,0,0,.9);
  backdrop-filter:blur(22px);
  color:#e5e7eb;
}
.modal-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
.modal-title{font-size:14px;font-weight:700;}
.modal-close{border:none;background:none;color:#9ca3af;font-size:20px;cursor:pointer;}

.tabs{display:flex;gap:6px;margin-bottom:10px;}
.tab-btn{
  flex:1;border-radius:999px;
  border:1px solid rgba(148,163,184,.7);
  background:rgba(15,23,42,.9);
  color:#9ca3af;padding:6px 0;
  font-size:12px;font-weight:600;cursor:pointer;
}
.tab-btn.active{
  background:linear-gradient(135deg,#facc15,var(--brand));
  color:#111827;border-color:transparent;
}

.btn-full{
  width:100%;
  margin-top:9px;
  padding:9px 0;border-radius:999px;border:none;
  background:linear-gradient(135deg,#fef3c7,#facc15,var(--brand));
  color:#111827;
  font-size:13px;font-weight:700;
  cursor:pointer;
  box-shadow:0 14px 40px rgba(0,0,0,.85);
}

.admin-tabs{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:9px;}
.admin-tab{
  flex:1;border-radius:999px;
  border:1px solid rgba(148,163,184,.7);
  background:rgba(15,23,42,.9);
  color:#9ca3af;padding:5px 0;
  font-size:11px;font-weight:600;cursor:pointer;
}
.admin-tab.active{
  background:linear-gradient(135deg,#facc15,var(--brand));
  color:#111827;border-color:transparent;
}
.admin-section{display:none;}
.admin-section.active{display:block;}

.admin-filter-row{
  display:flex;flex-direction:column;
  gap:8px;margin:6px 0 10px;
}

.closed-panel-title{margin-top:10px;font-size:11px;font-weight:600;color:#e5e7eb;}
.closed-date-item{
  display:flex;justify-content:space-between;align-items:center;
  padding:4px 6px;border-radius:10px;
  border:1px solid rgba(148,163,184,.6);
  margin-top:4px;font-size:11px;color:#e5e7eb;
}
.closed-date-item span{color:#cbd5f5;}

.toast{
  position:fixed;left:50%;top:14px;
  transform:translateX(-50%);
  background:radial-gradient(circle at top,rgba(15,23,42,.96),rgba(15,23,42,.99));
  color:#f9fafb;
  padding:7px 13px;border-radius:999px;
  font-size:12px;border:1px solid rgba(148,163,184,.75);
  box-shadow:0 20px 50px rgba(0,0,0,.9);
  display:none;z-index:50;
}
.toast.ok{border-color:rgba(16,185,129,.7);}
.toast.err{border-color:rgba(248,113,113,.9);}

.schedule-wrapper{max-height:65vh;overflow:auto;padding-right:4px;}
.schedule-row{
  border-radius:14px;border:1px solid rgba(148,163,184,.6);
  padding:6px 7px;margin-bottom:6px;
  background:radial-gradient(circle at top,rgba(15,23,42,.97),rgba(15,23,42,1));
}
.schedule-row-head{display:flex;justify-content:space-between;align-items:center;font-size:11px;margin-bottom:4px;}
.schedule-day-name{font-weight:600;}
.schedule-intervals{display:flex;flex-direction:column;gap:4px;margin-top:3px;}
.schedule-interval{display:flex;gap:4px;align-items:center;}
.schedule-interval select{
  flex:1;border-radius:10px;padding:4px 6px;
  border:1px solid rgba(148,163,184,.7);
  background:rgba(15,23,42,.95);
  color:#e5e7eb;font-size:11px;
}
.schedule-interval button{
  border:none;border-radius:999px;padding:3px 7px;
  font-size:10px;cursor:pointer;
  background:rgba(239,68,68,.12);
  color:var(--danger);
  border:1px solid rgba(248,113,113,.7);
}
.btn-add-interval{
  margin-top:4px;border-radius:999px;border:none;
  padding:3px 8px;font-size:10px;cursor:pointer;
  background:rgba(59,130,246,.12);
  color:#60a5fa;border:1px solid rgba(59,130,246,.7);
}
.day-active-label{font-size:10px;display:flex;align-items:center;gap:4px;}
.day-active-label input{accent-color:var(--brand);}

@media(max-width:480px){
  .wrap{padding:16px 10px 18px;border-radius:28px;}
  .card{padding:14px 10px 16px;}
  .brand-title{font-size:22px;}
  .slot-grid{grid-template-columns:repeat(3,minmax(0,1fr));gap:6px;}
  .date-input{font-size:11px;padding:5px 8px;}
}
@media(min-width:600px){
  .admin-filter-row{flex-direction:row;align-items:flex-end;gap:12px;}
}

@media print{
  body{background:#ffffff;padding:0;}
  .bg,.bg-overlay,.wrap > .logo-wrap,.top-actions,.card,#customerModal,#scheduleModal,.toast{display:none !important;}
  #adminModal{position:static;display:block !important;background:#ffffff;}
  #adminModal .modal{max-width:100%;border:none;box-shadow:none;padding:10px;background:#ffffff;}
  #adminLoginArea{display:none !important;}
  #adminPanelArea{display:block !important;max-height:none;overflow:visible;}
  .admin-tabs{display:none !important;}
  .admin-section{display:none !important;}
  .admin-section.active{display:block !important;}
  .btn-full{display:none !important;}
  .app-item{box-shadow:none;border:1px solid #ddd;background:#fff;color:#000;}
  .app-title,.app-meta{color:#000;}
}
</style>
</head>
<body>
<div class="bg"></div>
<div class="bg-overlay"></div>

<div class="wrap">
  <div class="logo-wrap"><div class="logo-circle"></div></div>

  <div class="top-actions">
    <button class="btn-top" type="button" id="btnAdminOpen"><span id="adminBtnLabel">Admin Girişi</span></button>
    <button class="btn-top" type="button" id="btnCustomerOpen"><span id="customerBtnLabel">Müşteri Paneli</span></button>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="brand-title">AHMET TEKELİ</div>
      <div class="brand-sub">ERKEK KUAFÖRÜ</div>
      <div class="rating"><div class="star"></div><span>⭐️ONLİNE RANDEVU⭐️</span></div>
    </div>

    <div>
      <div class="section-title">Ad Soyad</div>
      <input class="input" id="nameInput" placeholder="Adınız ve Soyadınız">

      <div class="section-title">Telefon</div>
      <input class="input" id="phoneInput" placeholder="05xxxxxxxxx">

      <div class="row">
        <div>
          <div class="section-title">Berber Seçimi</div>
          <div class="barber-choices" id="barberChoices"></div>
          <select class="select" id="barberSelect" style="display:none;"></select>
        </div>
        <div>
          <div class="section-title">İşlem Seçimi</div>
          <select class="select" id="serviceSelect"></select>
        </div>
      </div>

      <div class="section-title" style="margin-top:8px;">Tarih</div>
      <input type="date" class="date-input" id="dateInput">

      <div class="section-title" style="margin-top:8px;">Saat Seçimi</div>
      <div class="slot-grid" id="slotGrid"></div>

      <button class="btn-book" id="btnBook">RANDEVU AL</button>
      <div class="helper" id="bookingHelper">Randevu almak için önce müşteri girişi yapmalısın. Müşteri panelinden kayıt olabilirsin.</div>
      <div class="helper" id="dayInfoHelper"></div>
    </div>
  </div>
</div>

<!-- Müşteri Paneli -->
<div class="modal-backdrop" id="customerModal">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title">Müşteri Paneli</div>
      <button class="modal-close" type="button" id="modalClose">&times;</button>
    </div>

    <div id="customerLoggedBox" style="display:none;">
      <div class="helper" id="customerLoggedText"></div>

      <div class="panel" style="margin-top:8px;">
        <div class="section-title" style="margin:0 0 6px;">Sadakat / Hediye</div>
        <div id="loyaltyCardBody" style="font-size:11px;"></div>
        <button class="btn-full" id="btnWhatsAppShop" style="margin-top:8px;background:rgba(34,197,94,.18);color:#22c55e;border:1px solid rgba(34,197,94,.7);box-shadow:none;">
          WhatsApp’tan İşletmeye Yaz
        </button>
      </div>

      <div id="customerAppsBox" class="panel" style="margin-top:8px;">
        <div class="section-title">Randevularım</div>
        <ul class="app-list" id="appListModal"></ul>
      </div>

      <div id="customerGiftBox" class="panel" style="margin-top:8px;">
        <div class="section-title">Hediye Haklarım</div>
        <ul class="app-list" id="giftListModal"></ul>
      </div>

      <button class="btn-full" id="btnCustomerLogout" style="margin-top:8px;background:rgba(31,41,55,1);color:#f9fafb;">
        Çıkış Yap
      </button>
    </div>

    <div class="tabs" id="tabsRow">
      <button class="tab-btn active" type="button" data-tab="login">Giriş Yap</button>
      <button class="tab-btn" type="button" data-tab="register">Kayıt Ol</button>
    </div>

    <div id="loginTab">
      <div class="section-title">Telefon</div>
      <input class="input" id="loginPhone" placeholder="05xxxxxxxxx">
      <div class="section-title">Şifre</div>
      <input class="input" id="loginPass" type="password" placeholder="••••••">
      <button class="btn-full" id="btnLogin">Giriş Yap</button>
      <div class="helper">İlk defa geliyorsan üstten <b>Kayıt Ol</b> sekmesine geç.</div>
    </div>

    <div id="registerTab" style="display:none;">
      <div class="section-title">Ad Soyad</div>
      <input class="input" id="regName" placeholder="Adınız Soyadınız">
      <div class="section-title">Telefon</div>
      <input class="input" id="regPhone" placeholder="05xxxxxxxxx">
      <div class="section-title">Şifre</div>
      <input class="input" id="regPass" type="password" placeholder="En az 4 karakter">
      <button class="btn-full" id="btnRegister">Kayıt Ol</button>
      <div class="helper">Kayıt sonrası müşteri panelinden <b>Randevularım</b> kısmına erişirsin.</div>
    </div>
  </div>
</div>

<!-- Admin Panel -->
<div class="modal-backdrop" id="adminModal">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title">Admin Paneli</div>
      <button class="modal-close" type="button" id="adminModalClose">&times;</button>
    </div>

    <div id="adminLoginArea">
      <div class="section-title">Telefon</div>
      <input class="input" id="adminPhone" placeholder="Admin telefon">
      <div class="section-title">Şifre</div>
      <input class="input" id="adminPass" type="password" placeholder="Şifre">
      <button class="btn-full" id="btnAdminLogin">Admin Giriş Yap</button>
      <div class="helper">Bu alan sadece işletme sahibi içindir.</div>
    </div>

    <div id="adminPanelArea" style="display:none;max-height:70vh;overflow:auto;padding-right:4px;">
      <div class="admin-tabs">
        <button class="admin-tab active" data-admin-section="adminSectionRapor">Raporlar</button>
        <button class="admin-tab" data-admin-section="adminSectionRandevu">Randevular</button>
        <button class="admin-tab" data-admin-section="adminSectionHizmet">Hizmet Yönetimi</button>
        <button class="admin-tab" data-admin-section="adminSectionBerber">Berber Yönetimi & Çalışma Saatleri</button>
      </div>

      <div class="admin-section active" id="adminSectionRapor">
        <div class="section-title">Raporlar</div>
        <ul class="app-list" id="reportList"></ul>
        <button class="btn-full" id="btnPrintReports" style="margin-top:8px;">Raporları PDF Olarak Çıkar</button>
      </div>

      <div class="admin-section" id="adminSectionRandevu">
        <div class="section-title">Randevu Yönetimi</div>
        <div class="admin-filter-row">
          <div>
            <div class="section-title">Tarih Filtresi</div>
            <input type="date" class="date-input" id="adminDateFilter">
          </div>
          <div>
            <div class="section-title">Berber Filtresi</div>
            <select class="select" id="adminBarberFilter"></select>
          </div>
        </div>
        <ul class="app-list" id="adminAppList"></ul>
        <div class="helper" id="adminCountInfo"></div>

        <button class="btn-full" id="btnPrintAppointments" style="margin-top:8px;">Randevu Listesini PDF Olarak Çıkar</button>

        <div class="closed-panel-title">Kapalı Günler (Özel tatil / dükkân kapalı)</div>
        <div class="row" style="margin-top:4px;">
          <input type="date" class="date-input" id="closedDateInput">
          <button class="btn-full" id="btnAddClosedDate" style="margin-top:0;">Kapalı Gün Ekle</button>
        </div>
        <div id="closedDateList"></div>
      </div>

      <div class="admin-section" id="adminSectionHizmet">
        <div class="section-title">Hizmet Yönetimi</div>
        <ul class="app-list" id="serviceList"></ul>
        <div class="row" style="margin-top:6px;">
          <input class="input" id="newServiceName" placeholder="Hizmet adı (Saç Kesim)">
          <input class="input" id="newServicePrice" type="number" min="0" step="10" placeholder="Fiyat">
          <input class="input" id="newServiceDuration" type="number" min="15" step="15" placeholder="Süre (dk)">
        </div>
        <button class="btn-full" id="btnAddService" style="margin-top:6px;">Hizmet Ekle</button>
      </div>

      <div class="admin-section" id="adminSectionBerber">
        <div class="section-title">Berber Yönetimi & Çalışma Saatleri</div>
        <ul class="app-list" id="barberList"></ul>

        <div class="section-title" style="margin-top:10px;">Yeni Berber</div>
        <input class="input" id="newBarberName" placeholder="Örn: Ahmet TEKELİ">
        <div class="section-title">Fotoğraf Yükle (isteğe bağlı)</div>
        <input class="input" id="newBarberPhotoFile" type="file" accept="image/*" style="padding:6px 10px;">
        <button class="btn-full" id="btnAddBarber" style="margin-top:6px;">Berber Ekle</button>
      </div>

      <button class="btn-full" id="btnAdminLogout" style="margin-top:14px;background:rgba(31,41,55,1);color:#f9fafb;">
        Admin Çıkış
      </button>
    </div>
  </div>
</div>

<!-- Çalışma Saati Modal -->
<div class="modal-backdrop" id="scheduleModal">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title" id="scheduleModalTitle">Çalışma Saatleri</div>
      <button class="modal-close" type="button" id="scheduleModalClose">&times;</button>
    </div>
    <div class="schedule-wrapper" id="scheduleWrapper"></div>
    <button class="btn-full" id="btnSaveSchedule">Çalışma Saatlerini Kaydet</button>
  </div>
</div>

<div class="toast" id="toast"></div>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.13.1/firebase-app.js";
import { getFirestore, collection, doc, getDocs, setDoc, deleteDoc } from "https://www.gstatic.com/firebasejs/10.13.1/firebase-firestore.js";

/* Firebase */
const firebaseConfig = {
  apiKey: "AIzaSyD3S0XgKgNJLCJr3xQ-ASgr1gHz9MCou-4",
  authDomain: "randevularim-92ac2.firebaseapp.com",
  projectId: "randevularim-92ac2",
  storageBucket: "randevularim-92ac2.firebasestorage.app",
  messagingSenderId: "1092355095676",
  appId: "1:1092355095676:web:085921b2dff9d607b7ddf9"
};
const fbApp = initializeApp(firebaseConfig);
const db    = getFirestore(fbApp);

/* Sabitler */
const SLOT_TIMES = [
  "08:00","08:30","09:00","09:30","10:00","10:30","11:00","11:30",
  "12:00","12:30","13:00","13:30","14:00","14:30","15:00","15:30",
  "16:00","16:30","17:00","17:30","18:00","18:30","19:00","19:30",
  "20:00","20:30","21:00","21:30"
];

const ADMIN_PHONE = "05356749243";
const ADMIN_PASS  = "ahmetgs";
const MAX_DAYS_AHEAD = 30;
const DAY_NAMES = ["Pazartesi","Salı","Çarşamba","Perşembe","Cuma","Cumartesi","Pazar"];

/* LocalStorage Keys */
const LS_CUSTOMERS = "ak_customers_v1";
const LS_SERVICES  = "ak_services_v1";
const LS_BARBERS   = "ak_barbers_v3";
const LS_CLOSED    = "ak_closedDays_v1";
const LS_LOYALTY   = "ak_loyalty_v2"; // v2: used + gifts

/* State */
let appointments = [];
let services = [];
let barbers  = [];
let closedDays = [];
let loyalty = {};
let customers = [];

let selectedTime = null;
let currentCustomer = null;
let isAdmin = false;
let currentScheduleBarberId = null;

/* DOM */
const slotGrid  = document.getElementById("slotGrid");
const dateInput = document.getElementById("dateInput");
const btnBook   = document.getElementById("btnBook");
const nameInput = document.getElementById("nameInput");
const phoneInput= document.getElementById("phoneInput");
const barberSel = document.getElementById("barberSelect");
const barberChoicesEl = document.getElementById("barberChoices");
const servSel   = document.getElementById("serviceSelect");
const toastEl   = document.getElementById("toast");
const bookingHelper = document.getElementById("bookingHelper");
const dayInfoHelper = document.getElementById("dayInfoHelper");

/* admin */
const adminDateFilter   = document.getElementById("adminDateFilter");
const adminBarberFilter = document.getElementById("adminBarberFilter");
const adminAppList      = document.getElementById("adminAppList");
const adminCountInfo    = document.getElementById("adminCountInfo");
const reportListEl      = document.getElementById("reportList");

/* kapalı günler */
const closedDateInput   = document.getElementById("closedDateInput");
const btnAddClosedDate  = document.getElementById("btnAddClosedDate");
const closedDateList    = document.getElementById("closedDateList");

/* müşteri modal */
const customerModal      = document.getElementById("customerModal");
const btnCustomerOpen    = document.getElementById("btnCustomerOpen");
const modalClose         = document.getElementById("modalClose");
const tabBtns            = document.querySelectorAll(".tab-btn");
const loginTab           = document.getElementById("loginTab");
const registerTab        = document.getElementById("registerTab");
const btnLogin           = document.getElementById("btnLogin");
const btnRegister        = document.getElementById("btnRegister");
const customerLoggedBox  = document.getElementById("customerLoggedBox");
const customerLoggedText = document.getElementById("customerLoggedText");
const btnCustomerLogout  = document.getElementById("btnCustomerLogout");
const customerBtnLabel   = document.getElementById("customerBtnLabel");
const appListModal       = document.getElementById("appListModal");
const giftListModal      = document.getElementById("giftListModal");
const tabsRow            = document.getElementById("tabsRow");
const loyaltyCardBody    = document.getElementById("loyaltyCardBody");
const btnWhatsAppShop    = document.getElementById("btnWhatsAppShop");
const loginPhoneEl       = document.getElementById("loginPhone");
const loginPassEl        = document.getElementById("loginPass");
const regNameEl          = document.getElementById("regName");
const regPhoneEl         = document.getElementById("regPhone");
const regPassEl          = document.getElementById("regPass");

/* admin modal */
const adminModalEl     = document.getElementById("adminModal");
const btnAdminOpen     = document.getElementById("btnAdminOpen");
const adminModalClose  = document.getElementById("adminModalClose");
const adminLoginArea   = document.getElementById("adminLoginArea");
const adminPanelArea   = document.getElementById("adminPanelArea");
const btnAdminLogin    = document.getElementById("btnAdminLogin");
const btnAdminLogout   = document.getElementById("btnAdminLogout");
const adminBtnLabel    = document.getElementById("adminBtnLabel");
const adminTabBtns     = document.querySelectorAll(".admin-tab");
const adminSections    = document.querySelectorAll(".admin-section");

/* hizmet/berber */
const serviceListEl  = document.getElementById("serviceList");
const newServiceNameEl  = document.getElementById("newServiceName");
const newServicePriceEl = document.getElementById("newServicePrice");
const newServiceDurationEl = document.getElementById("newServiceDuration");
const btnAddService  = document.getElementById("btnAddService");

const barberListEl   = document.getElementById("barberList");
const newBarberNameEl= document.getElementById("newBarberName");
const newBarberPhotoFileEl= document.getElementById("newBarberPhotoFile");
const btnAddBarber   = document.getElementById("btnAddBarber");

/* çalışma saati modal */
const scheduleModal    = document.getElementById("scheduleModal");
const scheduleModalTitle = document.getElementById("scheduleModalTitle");
const scheduleModalClose = document.getElementById("scheduleModalClose");
const scheduleWrapper  = document.getElementById("scheduleWrapper");
const btnSaveSchedule  = document.getElementById("btnSaveSchedule");

/* PDF */
const btnPrintReports = document.getElementById("btnPrintReports");
const btnPrintAppointments = document.getElementById("btnPrintAppointments");

/* Toast */
let toastTimer = null;
function showToast(msg,type="ok"){
  toastEl.textContent=msg;
  toastEl.className="toast "+type;
  toastEl.style.display="block";
  if(toastTimer) clearTimeout(toastTimer);
  toastTimer = setTimeout(()=>toastEl.style.display="none",5600);
}

/* helpers */
function todayISO(){ return new Date().toISOString().slice(0,10); }
function diffInDays(dateStr){
  const t = new Date(todayISO());
  const d = new Date(dateStr);
  return Math.round((d - t)/(1000*60*60*24));
}
function timeToMinutes(t){ const [h,m]=t.split(":").map(Number); return h*60+m; }
function getDowIndex(dateStr){
  const d = new Date(dateStr);
  let js = d.getDay(); // 0=Sun
  if(js===0) return 6;
  return js-1;
}
function loadJSON(key,def){
  try{ const raw=localStorage.getItem(key); return raw?JSON.parse(raw):def; }catch(_){ return def; }
}
function saveJSON(key,val){ localStorage.setItem(key,JSON.stringify(val)); }

/* WhatsApp */
function normalizeTRPhone(phone){
  // 05xxxxxxxxx -> 90xxxxxxxxxx
  const p = (phone||"").replace(/\D/g,"");
  if(p.startsWith("90")) return p;
  if(p.startsWith("0")) return "90"+p.slice(1);
  return "90"+p;
}
function openWhatsApp(phone, message){
  const n = normalizeTRPhone(phone);
  const url = `https://wa.me/${n}?text=${encodeURIComponent(message)}`;
  window.open(url,"_blank");
}

/* Firestore */
async function loadAppointmentsFromFirestore(){
  try{
    const snap = await getDocs(collection(db,"appointments"));
    appointments = [];
    snap.forEach(d=>appointments.push(d.data()));
    await cleanupPastAppointments();
    renderAll();
  }catch(err){
    console.error("Firestore yükleme hata:",err);
  }
}
async function saveAppointmentToFirestore(app){
  await setDoc(doc(db,"appointments", app.id), app);
}
async function deleteAppointmentFromFirestore(id){
  await deleteDoc(doc(db,"appointments", id));
}

/* geçmiş randevu sil */
async function cleanupPastAppointments(){
  const today = todayISO();
  const keep=[], del=[];
  for(const a of appointments){
    if(a.date < today) del.push(a.id);
    else keep.push(a);
  }
  appointments = keep;
  for(const id of del){
    try{ await deleteAppointmentFromFirestore(id); }catch(_){}
  }
}

/* core */
function loadCoreData(){
  customers = loadJSON(LS_CUSTOMERS,[]);
  services  = loadJSON(LS_SERVICES,[]);
  barbers   = loadJSON(LS_BARBERS,[]);
  closedDays= loadJSON(LS_CLOSED,[]);

  if(services.length===0){
    services = [
      {id:"svc-hair", name:"Saç Kesim", price:250, duration:30},
      {id:"svc-beard", name:"Sakal", price:200, duration:20},
      {id:"svc-both", name:"Saç + Sakal", price:350, duration:45}
    ];
  }
  if(barbers.length===0){
    const s={};
    for(let i=0;i<7;i++) s[i]={active:i!==6, intervals:i===6?[]:[{start:"09:00",end:"19:00"}]};
    barbers = [
      {id:"b1",name:"Ahmet TEKELİ",photo:null,schedule:s},
      {id:"b2",name:"Çırak",photo:null,schedule:s}
    ];
  }
}
function saveCustomers(){ saveJSON(LS_CUSTOMERS,customers); }
function saveServices(){ saveJSON(LS_SERVICES,services); }
function saveBarbers(){ saveJSON(LS_BARBERS,barbers); }
function saveClosedDays(){ saveJSON(LS_CLOSED,closedDays); }

/* loyalty v2 (points + used + gifts[]) */
function loadLoyalty(){ loyalty = loadJSON(LS_LOYALTY,{}); }
function saveLoyalty(){ saveJSON(LS_LOYALTY,loyalty); }

function getLoyalty(phone){
  if(!loyalty[phone]) loyalty[phone]={points:0, used:0, gifts:[]};

  // eski sürümden gelenleri migrate et (giftCount varsa)
  const l = loyalty[phone];
  if(typeof l.used!=="number") l.used=0;
  if(!Array.isArray(l.gifts)) l.gifts=[];

  // Eğer eski alanlar varsa: giftCount
  if(typeof l.giftCount==="number"){
    // available = giftCount (eski mantık)
    const avail = l.giftCount;
    l.used = 0;
    l.gifts = l.gifts && l.gifts.length ? l.gifts : [];
    while(l.gifts.length < avail){
      l.gifts.unshift({message:"Tebrikler! 1 ücretsiz sakal tıraşı hakkın var.", when:new Date().toLocaleString("tr-TR")});
    }
    delete l.giftCount;
    saveLoyalty();
  }

  // gifts sayısını available'a eşitle
  const totalEarned = Math.floor((l.points||0)/10);
  const available = Math.max(0, totalEarned - (l.used||0));
  while(l.gifts.length < available){
    l.gifts.unshift({message:"Tebrikler! 1 ücretsiz sakal tıraşı hakkın var.", when:new Date().toLocaleString("tr-TR")});
  }
  while(l.gifts.length > available){
    l.gifts.shift();
  }

  loyalty[phone]=l;
  return l;
}

function addLoyaltyPoint(phone){
  const l = getLoyalty(phone);
  l.points = (l.points||0) + 1;

  // kazanılan toplam - kullanılan = available
  const totalEarned = Math.floor(l.points/10);
  const available = Math.max(0, totalEarned - (l.used||0));
  while(l.gifts.length < available){
    l.gifts.unshift({message:"Tebrikler! 1 ücretsiz sakal tıraşı hakkın var.", when:new Date().toLocaleString("tr-TR")});
  }
  saveLoyalty();
}

function useOneGift(phone){
  const l = getLoyalty(phone);
  const totalEarned = Math.floor(l.points/10);
  const available = Math.max(0, totalEarned - l.used);
  if(available<=0) return false;

  l.used += 1;
  // listeden 1 hediye sil
  if(l.gifts.length>0) l.gifts.shift();
  saveLoyalty();
  return true;
}

/* lookup */
function getBarberById(id){ return barbers.find(b=>b.id===id)||null; }
function getServiceById(id){ return services.find(s=>s.id===id)||null; }
function isClosedDay(dateStr){ return closedDays.includes(dateStr); }
function getIntervalsForBarberDate(barberId,dateStr){
  const barber=getBarberById(barberId);
  if(!barber || !barber.schedule) return [];
  const dow=getDowIndex(dateStr);
  const day=barber.schedule[dow];
  if(!day || !day.active) return [];
  return day.intervals || [];
}
function isTimeInIntervals(timeStr, intervals){
  const m=timeToMinutes(timeStr);
  return intervals.some(i=> m>=timeToMinutes(i.start) && m<timeToMinutes(i.end));
}
function getAppointmentsFor(barberId,dateStr){
  return appointments.filter(a=>a.barberId===barberId && a.date===dateStr);
}

/* render slots */
function renderSlots(){
  slotGrid.innerHTML="";
  dayInfoHelper.textContent="";
  const dateVal=dateInput.value;
  const barberId=barberSel.value;
  const serviceId=servSel.value;
  selectedTime=null;

  if(!dateVal || !barberId || !serviceId){
    slotGrid.innerHTML="<div style='font-size:11px;color:#9ca3af;'>Berber, işlem ve tarih seç.</div>";
    return;
  }

  const diff=diffInDays(dateVal);
  if(diff<0){ dayInfoHelper.textContent="Geçmiş tarih için randevu alınamaz."; return; }
  if(diff>MAX_DAYS_AHEAD){ dayInfoHelper.textContent=`En fazla ${MAX_DAYS_AHEAD} gün sonrasına kadar randevu alabilirsin.`; return; }
  if(isClosedDay(dateVal)){ dayInfoHelper.textContent="Bu gün işletme kapalı."; return; }

  const intervals=getIntervalsForBarberDate(barberId,dateVal);
  if(intervals.length===0){ dayInfoHelper.textContent="Seçtiğin berber bu gün pasif."; return; }

  const svc=getServiceById(serviceId);
  const duration=svc?svc.duration:30;

  const today=todayISO();
  const taken=getAppointmentsFor(barberId,dateVal);
  const takenRanges=taken.map(a=>{
    const start=timeToMinutes(a.time);
    const end=start+(a.duration||duration);
    return {start,end};
  });

  for(const t of SLOT_TIMES){
    if(!isTimeInIntervals(t,intervals)) continue;
    if(dateVal===today){
      const now=new Date();
      const nowM=now.getHours()*60+now.getMinutes();
      if(timeToMinutes(t)<=nowM) continue;
    }

    const btn=document.createElement("button");
    btn.type="button";
    btn.textContent=t;
    btn.className="slot";

    const startM=timeToMinutes(t);
    const endM=startM+duration;
    const overlap=takenRanges.some(r=> !(endM<=r.start || startM>=r.end));
    if(overlap){
      btn.classList.add("disabled");
    }else{
      btn.addEventListener("click",()=>{
        selectedTime=t;
        Array.from(slotGrid.querySelectorAll(".slot")).forEach(s=>s.classList.remove("selected"));
        btn.classList.add("selected");
      });
    }
    slotGrid.appendChild(btn);
  }

  if(!slotGrid.children.length){
    slotGrid.innerHTML="<div style='font-size:11px;color:#9ca3af;'>Uygun saat bulunamadı.</div>";
  }
}

/* services & barbers UI */
function renderServicesSelects(){
  servSel.innerHTML="";
  services.forEach(s=>{
    const opt=document.createElement("option");
    opt.value=s.id;
    opt.textContent=`${s.name} • ${s.price}₺ • ${s.duration}dk`;
    servSel.appendChild(opt);
  });
}
function renderBarberChoices(){
  barberSel.innerHTML="";
  barberChoicesEl.innerHTML="";
  barbers.forEach(b=>{
    const opt=document.createElement("option");
    opt.value=b.id; opt.textContent=b.name;
    barberSel.appendChild(opt);

    const chip=document.createElement("button");
    chip.type="button";
    chip.className="barber-chip";
    chip.dataset.id=b.id;

    const avatar=document.createElement("div");
    avatar.className="barber-avatar";
    avatar.textContent=b.name.split(" ").map(x=>x[0]).join("").slice(0,2).toUpperCase();
    chip.appendChild(avatar);

    const span=document.createElement("span");
    span.textContent=b.name;
    chip.appendChild(span);

    chip.addEventListener("click",()=>{
      barberSel.value=b.id;
      Array.from(barberChoicesEl.children).forEach(c=>c.classList.remove("selected"));
      chip.classList.add("selected");
      renderSlots();
    });

    barberChoicesEl.appendChild(chip);
  });

  if(barbers[0]){
    barberSel.value=barbers[0].id;
    const first=barberChoicesEl.querySelector(".barber-chip");
    if(first) first.classList.add("selected");
  }
}

/* customer auth */
function findCustomerByPhone(phone){ return customers.find(c=>c.phone===phone)||null; }

function loginCustomer(phone,pass){
  const c=findCustomerByPhone(phone);
  if(!c || c.pass!==pass) return null;
  currentCustomer=c;
  customerBtnLabel.textContent="Müşteri Paneli";
  bookingHelper.textContent="Bilgilerin otomatik dolduruldu. Şimdi tarih ve saat seçebilirsin.";
  nameInput.value=c.name;
  phoneInput.value=c.phone;
  renderCustomerPanel();
  return c;
}

/* customer panel render */
function renderCustomerPanel(){
  if(!currentCustomer){
    customerLoggedBox.style.display="none";
    tabsRow.style.display="flex";
    loginTab.style.display="";
    registerTab.style.display="none";
    return;
  }
  customerLoggedBox.style.display="block";
  tabsRow.style.display="none";
  loginTab.style.display="none";
  registerTab.style.display="none";
  customerLoggedText.innerHTML=`Hoş geldin <b>${currentCustomer.name}</b> • <u>${currentCustomer.phone}</u>`;

  renderCustomerAppointments();
  renderLoyaltyUI();
}

/* WhatsApp shop button */
btnWhatsAppShop.addEventListener("click",()=>{
  if(!currentCustomer) return;
  const msg = `Merhaba Ahmet Tekeli Erkek Kuaförü, ${currentCustomer.name} (${currentCustomer.phone}). Randevu hakkında yazıyorum.`;
  openWhatsApp(ADMIN_PHONE, msg);
});

function renderCustomerAppointments(){
  if(!currentCustomer) return;
  appListModal.innerHTML="";
  const today=todayISO();
  const myApps = appointments
    .filter(a=>a.customerPhone===currentCustomer.phone && a.date>=today)
    .sort((a,b)=>(a.date+a.time).localeCompare(b.date+b.time));

  if(myApps.length===0){
    appListModal.innerHTML="<li class='app-item'><div class='app-main'><div class='app-meta'>Aktif randevun yok.</div></div></li>";
    return;
  }

  myApps.forEach(a=>{
    const li=document.createElement("li");
    li.className="app-item";

    const main=document.createElement("div");
    main.className="app-main";
    main.innerHTML = `
      <div class="app-title">${a.date} • ${a.time}</div>
      <div class="app-meta">${a.serviceName} • ${a.barberName}</div>
    `;
    li.appendChild(main);

    const actions=document.createElement("div");
    actions.className="app-actions";

    const btnWp=document.createElement("button");
    btnWp.type="button";
    btnWp.className="btn-mini wp";
    btnWp.textContent="WhatsApp";
    btnWp.addEventListener("click",()=>{
      const msg = `Merhaba, randevum: ${a.date} ${a.time} • ${a.serviceName} • ${a.barberName}.`;
      openWhatsApp(ADMIN_PHONE, msg);
    });
    actions.appendChild(btnWp);

    const btnCancel=document.createElement("button");
    btnCancel.type="button";
    btnCancel.className="btn-mini del";
    btnCancel.textContent="İptal";
    btnCancel.addEventListener("click",async()=>{
      if(!confirm("Bu randevuyu iptal etmek istiyor musun?")) return;
      appointments=appointments.filter(x=>x.id!==a.id);
      await deleteAppointmentFromFirestore(a.id);
      await cleanupPastAppointments();
      renderAll();
      showToast("Randevun iptal edildi.","ok");
    });
    actions.appendChild(btnCancel);

    li.appendChild(actions);
    appListModal.appendChild(li);
  });
}

/* loyalty UI + gifts use */
function renderLoyaltyUI(){
  if(!currentCustomer) return;
  const l = getLoyalty(currentCustomer.phone);

  const totalEarned = Math.floor((l.points||0)/10);
  const available = Math.max(0, totalEarned - (l.used||0));
  const kalan = 10 - ((l.points||0)%10 || 10);

  loyaltyCardBody.innerHTML = "";

  if(available>0){
    const line1=document.createElement("div");
    line1.style.fontWeight="800";
    line1.style.color="#facc15";
    line1.textContent=`Tebrikler! ${available} adet ücretsiz sakal tıraşı hakkın var.`;
    loyaltyCardBody.appendChild(line1);

    const line2=document.createElement("div");
    line2.style.marginTop="4px";
    line2.textContent=`Toplam puan: ${l.points}. Bir sonraki hediye için ${kalan} puan kaldı.`;
    loyaltyCardBody.appendChild(line2);
  }else{
    loyaltyCardBody.innerHTML = `Toplam puan: <b>${l.points||0}</b><br>${10-(l.points||0)} puan sonra 1 ücretsiz sakal tıraşı kazanırsın.`;
  }

  giftListModal.innerHTML="";
  if(available<=0){
    giftListModal.innerHTML="<li class='app-item'><div class='app-main'><div class='app-meta'>Henüz hediye hakkın yok.</div></div></li>";
    return;
  }

  // her hediye için "Kullandım" butonu (kullanılınca sil)
  l.gifts.forEach((g,idx)=>{
    const li=document.createElement("li");
    li.className="app-item";

    const main=document.createElement("div");
    main.className="app-main";
    main.innerHTML = `
      <div class="app-title" style="color:#facc15">Ücretsiz Sakal</div>
      <div class="app-meta">${g.message || "1 ücretsiz sakal tıraşı hakkı"}</div>
      <div class="app-meta">${g.when || ""}</div>
    `;
    li.appendChild(main);

    const actions=document.createElement("div");
    actions.className="app-actions";

    const btnUse=document.createElement("button");
    btnUse.type="button";
    btnUse.className="btn-mini ok";
    btnUse.textContent="Kullandım";
    btnUse.addEventListener("click",()=>{
      if(!confirm("Bu hediyeyi kullandın mı? (1 hak düşer ve listeden silinir)")) return;
      const ok = useOneGift(currentCustomer.phone);
      if(ok){
        showToast("Hediye kullanıldı ve listeden silindi.","ok");
        renderLoyaltyUI();
      }else{
        showToast("Kullanılabilir hediye yok.","err");
      }
    });
    actions.appendChild(btnUse);

    li.appendChild(actions);
    giftListModal.appendChild(li);
  });
}

/* admin appointments */
function renderAdminBarberFilter(){
  adminBarberFilter.innerHTML="<option value=''>Tümü</option>";
  barbers.forEach(b=>{
    const opt=document.createElement("option");
    opt.value=b.id; opt.textContent=b.name;
    adminBarberFilter.appendChild(opt);
  });
}
function renderAdminAppointments(){
  adminAppList.innerHTML="";
  const dateVal=adminDateFilter.value;
  const barberId=adminBarberFilter.value;

  let list=[...appointments];
  if(dateVal) list=list.filter(a=>a.date===dateVal);
  if(barberId) list=list.filter(a=>a.barberId===barberId);

  list.sort((a,b)=>(a.date+a.time).localeCompare(b.date+b.time));

  if(list.length===0){
    adminAppList.innerHTML="<li class='app-item'><div class='app-main'><div class='app-meta'>Kayıtlı randevu bulunamadı.</div></div></li>";
    adminCountInfo.textContent="";
    return;
  }
  adminCountInfo.textContent=`Toplam ${list.length} randevu.`;

  list.forEach(a=>{
    const li=document.createElement("li");
    li.className="app-item";

    const main=document.createElement("div");
    main.className="app-main";
    main.innerHTML = `
      <div class="app-title">${a.date} • ${a.time} • ${a.serviceName} • ${a.barberName}</div>
      <div class="app-meta">${a.customerName} • ${a.customerPhone}</div>
    `;
    li.appendChild(main);

    const actions=document.createElement("div");
    actions.className="app-actions";

    const btnWp=document.createElement("button");
    btnWp.type="button";
    btnWp.className="btn-mini wp";
    btnWp.textContent="WhatsApp";
    btnWp.addEventListener("click",()=>{
      const msg = `Merhaba ${a.customerName}, randevun: ${a.date} ${a.time} • ${a.serviceName} • ${a.barberName}.`;
      openWhatsApp(a.customerPhone, msg);
    });
    actions.appendChild(btnWp);

    const btnDel=document.createElement("button");
    btnDel.type="button";
    btnDel.className="btn-mini del";
    btnDel.textContent="Sil";
    btnDel.addEventListener("click",async()=>{
      if(!confirm("Bu randevuyu tamamen silmek istiyor musun?")) return;
      appointments=appointments.filter(x=>x.id!==a.id);
      await deleteAppointmentFromFirestore(a.id);
      renderAll();
      showToast("Randevu silindi.","ok");
    });
    actions.appendChild(btnDel);

    li.appendChild(actions);
    adminAppList.appendChild(li);
  });
}

/* reports */
function renderReports(){
  reportListEl.innerHTML="";
  if(appointments.length===0){
    reportListEl.innerHTML="<li class='app-item'><div class='app-main'><div class='app-meta'>Henüz rapor yok.</div></div></li>";
    return;
  }
  const perDay={};
  appointments.forEach(a=>{
    if(!perDay[a.date]) perDay[a.date]={count:0,amount:0};
    perDay[a.date].count++;
    perDay[a.date].amount += a.price||0;
  });
  Object.entries(perDay).sort((a,b)=>a[0].localeCompare(b[0])).forEach(([d,info])=>{
    const li=document.createElement("li");
    li.className="app-item";
    li.innerHTML=`<div class="app-main"><div class="app-title">${d}</div><div class="app-meta">${info.count} randevu • Tahmini ciro: ${info.amount}₺</div></div>`;
    reportListEl.appendChild(li);
  });
}

/* services admin */
function renderServiceList(){
  serviceListEl.innerHTML="";
  services.forEach(s=>{
    const li=document.createElement("li");
    li.className="app-item";
    li.innerHTML=`<div class="app-main"><div class="app-title">${s.name}</div><div class="app-meta">${s.price}₺ • ${s.duration} dk</div></div>`;
    const actions=document.createElement("div");
    actions.className="app-actions";
    const btnDel=document.createElement("button");
    btnDel.type="button";
    btnDel.className="btn-mini del";
    btnDel.textContent="Sil";
    btnDel.addEventListener("click",()=>{
      if(!confirm("Bu hizmeti silmek istiyor musun?")) return;
      services=services.filter(x=>x.id!==s.id);
      saveServices();
      renderServicesSelects();
      renderServiceList();
      showToast("Hizmet silindi.","ok");
    });
    actions.appendChild(btnDel);
    li.appendChild(actions);
    serviceListEl.appendChild(li);
  });
}
btnAddService.addEventListener("click",()=>{
  const name=newServiceNameEl.value.trim();
  const price=Number(newServicePriceEl.value||"0");
  const dur=Number(newServiceDurationEl.value||"0");
  if(!name || !price || !dur){ showToast("Hizmet adı, fiyat ve süre zorunlu.","err"); return; }
  services.push({id:"svc-"+Date.now(), name, price, duration:dur});
  saveServices();
  newServiceNameEl.value=""; newServicePriceEl.value=""; newServiceDurationEl.value="";
  renderServicesSelects();
  renderServiceList();
  showToast("Hizmet eklendi.","ok");
});

/* barbers admin */
function defaultSchedule(){
  const s={}; for(let i=0;i<7;i++) s[i]={active:i!==6, intervals:i===6?[]:[{start:"09:00",end:"19:00"}]};
  return s;
}
function renderBarberList(){
  barberListEl.innerHTML="";
  barbers.forEach(b=>{
    const li=document.createElement("li");
    li.className="app-item";
    li.innerHTML=`<div class="app-main"><div class="app-title">${b.name}</div><div class="app-meta">Çalışma saatleri: butondan düzenle.</div></div>`;
    const actions=document.createElement("div");
    actions.className="app-actions";

    const btnSch=document.createElement("button");
    btnSch.type="button";
    btnSch.className="btn-mini ok";
    btnSch.textContent="Saat";
    btnSch.addEventListener("click",()=>openScheduleModal(b.id));
    actions.appendChild(btnSch);

    const btnDel=document.createElement("button");
    btnDel.type="button";
    btnDel.className="btn-mini del";
    btnDel.textContent="Sil";
    btnDel.addEventListener("click",()=>{
      if(!confirm("Bu berberi silmek istiyor musun?")) return;
      barbers=barbers.filter(x=>x.id!==b.id);
      saveBarbers();
      renderBarberList();
      renderBarberChoices();
      renderSlots();
    });
    actions.appendChild(btnDel);

    li.appendChild(actions);
    barberListEl.appendChild(li);
  });
}
btnAddBarber.addEventListener("click",()=>{
  const name=newBarberNameEl.value.trim();
  if(!name){ showToast("Berber adı boş olamaz.","err"); return; }
  barbers.push({id:"b"+Date.now(), name, photo:null, schedule:defaultSchedule()});
  saveBarbers();
  newBarberNameEl.value=""; newBarberPhotoFileEl.value="";
  renderBarberList();
  renderBarberChoices();
  renderSlots();
  showToast("Berber eklendi.","ok");
});

/* closed days */
function renderClosedDays(){
  closedDateList.innerHTML="";
  closedDays.sort().forEach(d=>{
    const div=document.createElement("div");
    div.className="closed-date-item";
    div.innerHTML=`<span>${d}</span>`;
    const btn=document.createElement("button");
    btn.type="button";
    btn.className="btn-mini del";
    btn.textContent="Sil";
    btn.addEventListener("click",()=>{
      closedDays=closedDays.filter(x=>x!==d);
      saveClosedDays();
      renderClosedDays();
      renderSlots();
    });
    div.appendChild(btn);
    closedDateList.appendChild(div);
  });
}
btnAddClosedDate.addEventListener("click",()=>{
  const d=closedDateInput.value;
  if(!d){ showToast("Tarih seç.","err"); return; }
  if(!closedDays.includes(d)){
    closedDays.push(d);
    saveClosedDays();
    renderClosedDays();
    showToast("Kapalı gün eklendi.","ok");
    renderSlots();
  }
});

/* schedule modal */
function openScheduleModal(barberId){
  currentScheduleBarberId=barberId;
  const barber=getBarberById(barberId);
  if(!barber) return;
  scheduleModalTitle.textContent=`${barber.name} • Çalışma Saatleri`;
  scheduleWrapper.innerHTML="";

  for(let i=0;i<7;i++){
    const row=document.createElement("div");
    row.className="schedule-row";
    row.dataset.day=i;

    const head=document.createElement("div");
    head.className="schedule-row-head";
    const dayName=document.createElement("div");
    dayName.className="schedule-day-name";
    dayName.textContent=DAY_NAMES[i];
    head.appendChild(dayName);

    const label=document.createElement("label");
    label.className="day-active-label";
    const chk=document.createElement("input");
    chk.type="checkbox";
    chk.checked=barber.schedule[i]?.active ?? (i!==6);
    label.appendChild(chk);
    label.appendChild(document.createTextNode("Aktif"));
    head.appendChild(label);
    row.appendChild(head);

    const intervalsDiv=document.createElement("div");
    intervalsDiv.className="schedule-intervals";
    const intervals=barber.schedule[i]?.intervals || (i===6?[]:[{start:"09:00",end:"19:00"}]);
    intervals.forEach(intv=>intervalsDiv.appendChild(createIntervalRow(intv.start,intv.end)));
    row.appendChild(intervalsDiv);

    const btnAdd=document.createElement("button");
    btnAdd.type="button";
    btnAdd.className="btn-add-interval";
    btnAdd.textContent="Aralık Ekle";
    btnAdd.addEventListener("click",()=>intervalsDiv.appendChild(createIntervalRow("09:00","19:00")));
    row.appendChild(btnAdd);

    scheduleWrapper.appendChild(row);
  }
  scheduleModal.style.display="flex";
}
function createIntervalRow(start,end){
  const wrap=document.createElement("div");
  wrap.className="schedule-interval";
  const sSel=document.createElement("select");
  const eSel=document.createElement("select");
  SLOT_TIMES.forEach(t=>{
    const o1=document.createElement("option"); o1.value=t; o1.textContent=t; sSel.appendChild(o1);
    const o2=document.createElement("option"); o2.value=t; o2.textContent=t; eSel.appendChild(o2);
  });
  sSel.value=start; eSel.value=end;
  wrap.appendChild(sSel); wrap.appendChild(eSel);
  const btn=document.createElement("button");
  btn.type="button"; btn.textContent="Sil";
  btn.addEventListener("click",()=>wrap.remove());
  wrap.appendChild(btn);
  return wrap;
}
scheduleModalClose.addEventListener("click",()=>scheduleModal.style.display="none");
btnSaveSchedule.addEventListener("click",()=>{
  if(!currentScheduleBarberId) return;
  const barber=getBarberById(currentScheduleBarberId);
  if(!barber) return;

  const schedule={};
  Array.from(scheduleWrapper.querySelectorAll(".schedule-row")).forEach(row=>{
    const day=parseInt(row.dataset.day,10);
    const chk=row.querySelector("input[type=checkbox]");
    const active=chk.checked;
    const intervals=[];
    Array.from(row.querySelectorAll(".schedule-interval")).forEach(intEl=>{
      const sels=intEl.querySelectorAll("select");
      if(sels.length<2) return;
      const s=sels[0].value, e=sels[1].value;
      if(timeToMinutes(e)>timeToMinutes(s)) intervals.push({start:s,end:e});
    });
    schedule[day]={active,intervals};
  });

  barber.schedule=schedule;
  saveBarbers();
  scheduleModal.style.display="none";
  renderSlots();
  showToast("Çalışma saatleri kaydedildi.","ok");
});

/* modals */
btnCustomerOpen.addEventListener("click",()=>{ customerModal.style.display="flex"; renderCustomerPanel(); });
modalClose.addEventListener("click",()=>customerModal.style.display="none");

tabBtns.forEach(btn=>{
  btn.addEventListener("click",()=>{
    tabBtns.forEach(b=>b.classList.remove("active"));
    btn.classList.add("active");
    const tab=btn.dataset.tab;
    loginTab.style.display = (tab==="login") ? "" : "none";
    registerTab.style.display = (tab==="register") ? "" : "none";
  });
});

btnRegister.addEventListener("click",()=>{
  const name=regNameEl.value.trim();
  const phone=regPhoneEl.value.trim();
  const pass=regPassEl.value.trim();
  if(!name || !phone || !pass){ showToast("Ad, telefon ve şifre zorunlu.","err"); return; }
  if(findCustomerByPhone(phone)){ showToast("Bu telefon zaten kayıtlı.","err"); return; }
  customers.push({name,phone,pass});
  saveCustomers();
  regNameEl.value=""; regPhoneEl.value=""; regPassEl.value="";
  showToast("Kayıt başarılı.","ok");
  loginCustomer(phone,pass);
});

btnLogin.addEventListener("click",()=>{
  const phone=loginPhoneEl.value.trim();
  const pass=loginPassEl.value.trim();
  const c=loginCustomer(phone,pass);
  if(!c){ showToast("Telefon veya şifre hatalı.","err"); return; }
  showToast("Müşteri girişi başarılı.","ok");
});

btnCustomerLogout.addEventListener("click",()=>{
  currentCustomer=null;
  customerLoggedBox.style.display="none";
  tabsRow.style.display="flex";
  loginTab.style.display="";
  registerTab.style.display="none";
  customerBtnLabel.textContent="Müşteri Paneli";
  nameInput.value="";
  phoneInput.value="";
  bookingHelper.textContent="Randevu almak için önce müşteri girişi yapmalısın. Müşteri panelinden kayıt olabilirsin.";
});

/* admin modal */
btnAdminOpen.addEventListener("click",()=>adminModalEl.style.display="flex");
adminModalClose.addEventListener("click",()=>adminModalEl.style.display="none");

btnAdminLogin.addEventListener("click",()=>{
  const phone=document.getElementById("adminPhone").value.trim();
  const pass =document.getElementById("adminPass").value.trim();
  if(phone===ADMIN_PHONE && pass===ADMIN_PASS){
    isAdmin=true;
    adminLoginArea.style.display="none";
    adminPanelArea.style.display="block";
    adminBtnLabel.textContent="Admin Paneli";
    showToast("Admin girişi başarılı.","ok");
  }else{
    showToast("Admin bilgileri hatalı.","err");
  }
});
btnAdminLogout.addEventListener("click",()=>{
  isAdmin=false;
  adminLoginArea.style.display="block";
  adminPanelArea.style.display="none";
});

adminTabBtns.forEach(btn=>{
  btn.addEventListener("click",()=>{
    adminTabBtns.forEach(b=>b.classList.remove("active"));
    btn.classList.add("active");
    const id=btn.dataset.adminSection;
    adminSections.forEach(s=>s.classList.remove("active"));
    document.getElementById(id).classList.add("active");
  });
});

adminDateFilter.addEventListener("change",renderAdminAppointments);
adminBarberFilter.addEventListener("change",renderAdminAppointments);

btnPrintReports.addEventListener("click",()=>{
  document.querySelector('[data-admin-section="adminSectionRapor"]').click();
  window.print();
});
btnPrintAppointments.addEventListener("click",()=>{
  document.querySelector('[data-admin-section="adminSectionRandevu"]').click();
  window.print();
});

/* book appointment */
btnBook.addEventListener("click", async ()=>{
  if(!currentCustomer){
    showToast("Önce müşteri girişi yapmalısın.","err");
    customerModal.style.display="flex";
    return;
  }

  const name=nameInput.value.trim();
  const phone=phoneInput.value.trim();
  const barberId=barberSel.value;
  const serviceId=servSel.value;
  const dateVal=dateInput.value;
  const timeVal=selectedTime;

  if(!name || !phone || !barberId || !serviceId || !dateVal || !timeVal){
    showToast("Tüm alanları doldur ve saat seç.","err");
    return;
  }

  const svc=getServiceById(serviceId);
  const barber=getBarberById(barberId);
  if(!svc || !barber){ showToast("Berber veya hizmet bulunamadı.","err"); return; }

  const app={
    id:"app-"+Date.now(),
    customerName:name,
    customerPhone:phone,
    barberId,
    barberName:barber.name,
    serviceId,
    serviceName:svc.name,
    price:svc.price,
    duration:svc.duration,
    date:dateVal,
    time:timeVal,
    createdAt:new Date().toISOString()
  };

  appointments.push(app);
  await saveAppointmentToFirestore(app);
  await cleanupPastAppointments();

  // sadakat
  addLoyaltyPoint(phone);

  renderAll();
  showToast("Randevun oluşturuldu. (+1 puan)","ok");
});

/* form changes */
servSel.addEventListener("change",renderSlots);
barberSel.addEventListener("change",renderSlots);
dateInput.addEventListener("change",renderSlots);

/* master render */
function renderAll(){
  renderServicesSelects();
  renderBarberChoices();
  renderAdminBarberFilter();
  renderAdminAppointments();
  renderReports();
  renderServiceList();
  renderBarberList();
  renderClosedDays();
  renderSlots();
  if(currentCustomer){
    renderCustomerAppointments();
    renderLoyaltyUI();
  }
}

/* init */
loadCoreData();
loadLoyalty();
renderAll();
loadAppointmentsFromFirestore();
</script>
</body>
</html>