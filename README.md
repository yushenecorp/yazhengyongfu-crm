<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="雅正永富">
<title>雅正永富｜客戶管理系統</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue',Arial,sans-serif;background:#f5f5f5;min-height:100vh;color:#1a1a1a}
.hidden{display:none!important}
.app{max-width:900px;margin:0 auto;padding:12px}

/* ===== 登入 ===== */
.login-wrap{display:flex;align-items:center;justify-content:center;min-height:100vh;padding:16px}
.login-card{background:#fff;border-radius:16px;padding:2rem;width:100%;max-width:360px;box-shadow:0 2px 16px rgba(0,0,0,0.08)}
.login-logo{text-align:center;margin-bottom:1.5rem}
.logo-circle{width:60px;height:60px;background:#1F4E79;border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto 12px}
.logo-circle span{color:#fff;font-size:18px;font-weight:600}
.login-logo h1{font-size:18px;font-weight:600;color:#1a1a1a;margin-bottom:4px}
.login-logo p{font-size:13px;color:#888}
.form-group{margin-bottom:14px}
.form-group label{display:block;font-size:13px;color:#555;margin-bottom:6px;font-weight:500}
.form-group input{width:100%;padding:12px 14px;border:1px solid #ddd;border-radius:10px;font-size:15px;background:#fff;color:#1a1a1a;outline:none}
.form-group input:focus{border-color:#1F4E79}
.btn-primary{width:100%;padding:13px;background:#1F4E79;color:#fff;border:none;border-radius:10px;font-size:15px;font-weight:600;cursor:pointer;margin-top:6px}
.btn-primary:active{background:#164069}
.login-error{color:#c5221f;font-size:13px;margin-top:8px;text-align:center;background:#fce8e6;padding:8px;border-radius:8px}

/* ===== 頂部 ===== */
.topbar{background:#fff;border-radius:12px;padding:12px 14px;display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.topbar-left{display:flex;align-items:center;gap:10px}
.topbar-logo{width:32px;height:32px;background:#1F4E79;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.topbar-logo span{color:#fff;font-size:11px;font-weight:600}
.topbar-title{font-size:14px;font-weight:600;color:#1a1a1a}
.topbar-right{display:flex;align-items:center;gap:6px}
.user-badge{font-size:12px;color:#555;background:#f0f0f0;padding:4px 10px;border-radius:20px;white-space:nowrap}
.btn-logout{font-size:12px;color:#c5221f;border:1px solid #f5c4b3;background:transparent;padding:4px 10px;border-radius:20px;cursor:pointer}

/* ===== 分頁 ===== */
.tabs{display:flex;gap:6px;margin-bottom:12px}
.tab{flex:1;padding:10px 8px;border:1px solid #ddd;border-radius:10px;font-size:13px;font-weight:500;background:#fff;color:#555;cursor:pointer;text-align:center}
.tab.active{background:#1F4E79;color:#fff;border-color:#1F4E79}

/* ===== 統計卡片 ===== */
.stats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:12px}
.stat-card{background:#fff;border-radius:12px;padding:12px 8px;text-align:center;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.stat-num{font-size:22px;font-weight:700;color:#1F4E79}
.stat-label{font-size:11px;color:#888;margin-top:2px}

/* ===== 搜尋 ===== */
.search-bar{display:flex;gap:8px;margin-bottom:10px}
.search-bar input{flex:1;padding:10px 14px;border:1px solid #ddd;border-radius:10px;font-size:14px;background:#fff;color:#1a1a1a;outline:none}
.search-bar input:focus{border-color:#1F4E79}
.btn-search{padding:10px 16px;background:#1F4E79;color:#fff;border:none;border-radius:10px;font-size:14px;font-weight:500;cursor:pointer;white-space:nowrap}
.filter-bar{display:flex;gap:6px;margin-bottom:12px;flex-wrap:wrap}
.filter-select{padding:8px 10px;border:1px solid #ddd;border-radius:8px;font-size:13px;background:#fff;color:#1a1a1a;outline:none;flex:1;min-width:80px}

/* ===== 客戶列表 ===== */
.client-list{display:flex;flex-direction:column;gap:8px}
.client-card{background:#fff;border-radius:12px;padding:14px;cursor:pointer;box-shadow:0 1px 4px rgba(0,0,0,0.06);border:1.5px solid transparent}
.client-card:active{border-color:#1F4E79;background:#f8faff}
.client-card-top{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:8px;gap:8px}
.client-name{font-size:15px;font-weight:600;color:#1a1a1a}
.client-phone{font-size:13px;color:#888;margin-top:2px}
.badges{display:flex;gap:4px;flex-wrap:wrap;flex-shrink:0}
.badge{display:inline-block;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:600}
.badge-a{background:#fce8e6;color:#c5221f}
.badge-b{background:#fef7e0;color:#b06000}
.badge-c{background:#e6f4ea;color:#137333}
.badge-grey{background:#f0f0f0;color:#666}
.badge-done{background:#e6f4ea;color:#137333}
.badge-ordered{background:#e8f0fe;color:#185FA5}
.badge-signed{background:#e6f4ea;color:#137333}
.badge-undone{background:#fef7e0;color:#b06000}
.badge-contacted{background:#e6f4ea;color:#137333}
.badge-notcontacted{background:#fce8e6;color:#c5221f}
.client-info{display:flex;gap:12px;flex-wrap:wrap}
.info-item{font-size:12px;color:#888}
.info-item strong{color:#444;font-weight:500}

/* ===== 客戶詳情 ===== */
.detail-back{display:flex;align-items:center;gap:6px;font-size:14px;color:#1F4E79;cursor:pointer;margin-bottom:12px;padding:4px 0}
.detail-header{background:#fff;border-radius:12px;padding:16px;margin-bottom:10px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.detail-name{font-size:20px;font-weight:700;color:#1a1a1a;margin-bottom:6px}
.detail-meta{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:14px;align-items:center}
.detail-phone{font-size:14px;color:#888}
.detail-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.detail-field{background:#f8f8f8;border-radius:10px;padding:10px 12px}
.detail-field label{font-size:11px;color:#999;display:block;margin-bottom:3px}
.detail-field span{font-size:14px;color:#1a1a1a;font-weight:500}
.section-title{font-size:12px;font-weight:600;color:#999;margin:14px 0 8px;letter-spacing:0.5px;text-transform:uppercase}
.history-card{background:#fff;border-radius:10px;padding:12px;margin-bottom:8px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.history-date{font-size:12px;color:#999;margin-bottom:4px}
.history-type{display:inline-block;padding:2px 10px;border-radius:20px;font-size:11px;font-weight:600;margin-bottom:8px}
.type-visit{background:#e6f4ea;color:#137333}
.type-call{background:#e8f0fe;color:#185FA5}
.type-contact{background:#fef7e0;color:#b06000}
.history-content{font-size:13px;color:#333;line-height:1.7;white-space:pre-wrap;word-break:break-all}

/* ===== 填表區 ===== */
.form-section{background:#fff;border-radius:12px;padding:14px;margin-bottom:10px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.form-section h3{font-size:14px;font-weight:600;color:#1F4E79;margin-bottom:12px;padding-bottom:8px;border-bottom:1px solid #f0f0f0}
.form-link{display:flex;align-items:center;justify-content:space-between;padding:12px;border:1px solid #eee;border-radius:10px;margin-bottom:8px;cursor:pointer;text-decoration:none;background:#fff}
.form-link:active{background:#f8faff;border-color:#1F4E79}
.form-link:last-child{margin-bottom:0}
.form-link-left{display:flex;align-items:center;gap:10px}
.form-icon{width:38px;height:38px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0}
.form-icon.counter{background:#EBF3FB}
.form-icon.staff{background:#E8F5E9}
.form-link-title{font-size:14px;font-weight:500;color:#1a1a1a}
.form-link-desc{font-size:12px;color:#999;margin-top:2px}
.form-arrow{font-size:20px;color:#ccc}

/* ===== 設定 ===== */
.settings-card{background:#fff;border-radius:12px;padding:16px;box-shadow:0 1px 4px rgba(0,0,0,0.06)}
.settings-card h3{font-size:15px;font-weight:600;margin-bottom:16px;color:#1a1a1a}
.btn-save{padding:12px 24px;background:#1F4E79;color:#fff;border:none;border-radius:10px;font-size:14px;font-weight:600;cursor:pointer;margin-top:8px}
.success-msg{color:#137333;font-size:13px;margin-top:8px;background:#e6f4ea;padding:8px;border-radius:8px}

/* ===== 通用 ===== */
.no-data{text-align:center;padding:2.5rem;color:#999;font-size:14px}
.loading{text-align:center;padding:2.5rem;color:#999;font-size:14px}
.result-count{font-size:13px;color:#999;margin-bottom:8px}

@media(max-width:480px){
  .stats-grid{grid-template-columns:repeat(2,1fr)}
  .detail-grid{grid-template-columns:1fr}
  .topbar-title{font-size:13px}
  .stat-num{font-size:18px}
}
</style>
</head>
<body>

<!-- ===== 登入畫面 ===== -->
<div id="loginPage">
  <div class="login-wrap">
    <div class="login-card">
      <div class="login-logo">
        <div class="logo-circle"><span>雅正</span></div>
        <h1>雅正永富｜客戶管理系統</h1>
        <p>禹盛開發股份有限公司</p>
      </div>
      <div class="form-group">
        <label>帳號</label>
        <input type="text" id="loginUser" placeholder="請輸入帳號" autocomplete="username" />
      </div>
      <div class="form-group">
        <label>密碼</label>
        <input type="password" id="loginPass" placeholder="請輸入密碼" autocomplete="current-password" onkeydown="if(event.key==='Enter')doLogin()" />
      </div>
      <button class="btn-primary" onclick="doLogin()">登入</button>
      <div class="login-error hidden" id="loginError">帳號或密碼錯誤，請再試一次</div>
    </div>
  </div>
</div>

<!-- ===== 主畫面 ===== -->
<div id="mainPage" class="hidden">
  <div class="app">
    <div class="topbar">
      <div class="topbar-left">
        <div class="topbar-logo"><span>雅正</span></div>
        <span class="topbar-title">雅正永富｜客戶管理</span>
      </div>
      <div class="topbar-right">
        <span class="user-badge" id="userBadge"></span>
        <button class="btn-logout" onclick="doLogout()">登出</button>
      </div>
    </div>

    <div class="tabs">
      <div class="tab active" onclick="showTab('clients',this)">客戶總覽</div>
      <div class="tab" onclick="showTab('forms',this)">填寫表單</div>
      <div class="tab" onclick="showTab('settings',this)">設定</div>
    </div>

    <!-- 客戶總覽 -->
    <div id="tab-clients">
      <div id="clientListView">
        <div class="stats-grid">
          <div class="stat-card"><div class="stat-num" id="statTotal">-</div><div class="stat-label">總客戶數</div></div>
          <div class="stat-card"><div class="stat-num" id="statVisited">-</div><div class="stat-label">已來訪</div></div>
          <div class="stat-card"><div class="stat-num" id="statContacted">-</div><div class="stat-label">已聯繫</div></div>
          <div class="stat-card"><div class="stat-num" id="statDone">-</div><div class="stat-label">已成交</div></div>
        </div>
        <div class="search-bar">
          <input type="text" id="searchInput" placeholder="電話號碼或姓名..." onkeydown="if(event.key==='Enter')doSearch()" />
          <button class="btn-search" onclick="doSearch()">搜尋</button>
        </div>
        <div class="filter-bar">
          <select class="filter-select" id="filterGrade" onchange="doSearch()">
            <option value="">全部等級</option>
            <option value="A">A級</option>
            <option value="B">B級</option>
            <option value="C">C級</option>
          </select>
          <select class="filter-select" id="filterStatus" onchange="doSearch()">
            <option value="">全部狀態</option>
            <option value="已下訂">已下訂</option>
            <option value="已簽約">已簽約</option>
            <option value="未成交">未成交</option>
          </select>
          <!-- ▼▼▼ 新增業務人員請在這裡加一行 ▼▼▼ -->
          <select class="filter-select" id="filterStaff" onchange="doSearch()">
            <option value="">全部業務</option>
            <option value="施憶如">施憶如</option>
            <option value="邱瀠萱">邱瀠萱</option>
            <option value="櫃檯人員">櫃檯人員</option>
            <option value="業主">業主</option>
          </select>
          <!-- ▲▲▲ 新增業務人員請在這裡加一行 ▲▲▲ -->
        </div>
        <div class="result-count" id="resultCount"></div>
        <div id="clientList" class="client-list">
          <div class="loading">正在載入客戶資料...</div>
        </div>
      </div>
      <div id="clientDetailView" class="hidden">
        <div class="detail-back" onclick="backToList()">← 返回列表</div>
        <div id="detailContent"></div>
      </div>
    </div>

    <!-- 填寫表單 -->
    <div id="tab-forms" class="hidden">
      <div class="form-section">
        <h3>櫃檯填寫</h3>
        <div class="form-link" onclick="window.open('https://forms.gle/Cv5u5vzjAiKjo5oJ8','_blank')">
          <div class="form-link-left">
            <div class="form-icon counter">📋</div>
            <div><div class="form-link-title">廣告來電名單輸入表</div><div class="form-link-desc">收到廣告來電名單時填寫</div></div>
          </div>
          <span class="form-arrow">›</span>
        </div>
      </div>
      <div class="form-section">
        <h3>銷售人員填寫</h3>
        <div class="form-link" onclick="window.open('https://forms.gle/yJLYVzZUYRZNYcMy8','_blank')">
          <div class="form-link-left"><div class="form-icon staff">📞</div><div><div class="form-link-title">廣告名單聯繫回報表</div><div class="form-link-desc">每次電話聯繫廣告名單後填寫</div></div></div>
          <span class="form-arrow">›</span>
        </div>
        <div class="form-link" onclick="window.open('https://forms.gle/rUSfQ7Wk8BAWZJrY8','_blank')">
          <div class="form-link-left"><div class="form-icon staff">🏠</div><div><div class="form-link-title">客戶首參資料建立表</div><div class="form-link-desc">客人首次來現場後填寫</div></div></div>
          <span class="form-arrow">›</span>
        </div>
        <div class="form-link" onclick="window.open('https://forms.gle/2UzpKfNpEbsSuTRN7','_blank')">
          <div class="form-link-left"><div class="form-icon staff">🔄</div><div><div class="form-link-title">客戶回訪更新表</div><div class="form-link-desc">客人第二次以上來現場後填寫</div></div></div>
          <span class="form-arrow">›</span>
        </div>
        <div class="form-link" onclick="window.open('https://forms.gle/doM1nRAwSCHYdcJf9','_blank')">
          <div class="form-link-left"><div class="form-icon staff">📱</div><div><div class="form-link-title">客戶電話追蹤紀錄表</div><div class="form-link-desc">電話追蹤已來過現場的客人後填寫</div></div></div>
          <span class="form-arrow">›</span>
        </div>
      </div>
    </div>

    <!-- 設定 -->
    <div id="tab-settings" class="hidden">
      <div class="settings-card">
        <h3>修改密碼</h3>
        <div class="form-group"><label>目前密碼</label><input type="password" id="oldPwd" placeholder="請輸入目前密碼" /></div>
        <div class="form-group"><label>新密碼</label><input type="password" id="newPwd" placeholder="請輸入新密碼" /></div>
        <div class="form-group"><label>確認新密碼</label><input type="password" id="confirmPwd" placeholder="請再輸入一次新密碼" /></div>
        <button class="btn-save" onclick="changePwd()">儲存變更</button>
        <div class="success-msg hidden" id="pwdMsg">密碼已更新</div>
        <div class="login-error hidden" id="pwdError"></div>
      </div>
    </div>
  </div>
</div>

<script>
// =====================================================
// ▼▼▼ 人員設定區域（新增/刪除人員請在這裡修改）▼▼▼
// =====================================================
// role: 'admin' = 管理者（看全部）, 'staff' = 銷售人員（只看自己）
// staff: 銷售人員的名字（必須跟試算表裡「負責業務」欄位一致）
const USERS = [
  {account:'frankwei', password:'168', name:'副總', role:'admin', staff:null},
  // 新增人員範例（複製下面這行，修改帳號、密碼、姓名）：
  // {account:'shiyi', password:'1234', name:'施憶如', role:'staff', staff:'施憶如'},
  // {account:'qiuying', password:'1234', name:'邱瀠萱', role:'staff', staff:'邱瀠萱'},
];
// =====================================================
// ▲▲▲ 人員設定區域結束 ▲▲▲
// =====================================================

const SHEET_ID = '1G6v8t2coqCBMJu5LDuYacqcZGVdXbpyzcVt48OlFC4k';

let currentUser = null;
let allClients = [];
const passwords = {};
USERS.forEach(u => passwords[u.account] = u.password);

function doLogin() {
  const acc = document.getElementById('loginUser').value.trim();
  const pwd = document.getElementById('loginPass').value;
  const user = USERS.find(u => u.account === acc && (passwords[u.account] || u.password) === pwd);
  if (user) {
    currentUser = user;
    document.getElementById('loginPage').classList.add('hidden');
    document.getElementById('mainPage').classList.remove('hidden');
    document.getElementById('userBadge').textContent = user.name + '（' + (user.role === 'admin' ? '管理者' : '銷售人員') + '）';
    document.getElementById('loginError').classList.add('hidden');
    loadClients();
  } else {
    document.getElementById('loginError').classList.remove('hidden');
  }
}

function doLogout() {
  currentUser = null;
  allClients = [];
  document.getElementById('loginPage').classList.remove('hidden');
  document.getElementById('mainPage').classList.add('hidden');
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
  showTab('clients', document.querySelector('.tab'));
}

function showTab(name, el) {
  ['clients','forms','settings'].forEach(t => document.getElementById('tab-'+t).classList.add('hidden'));
  document.getElementById('tab-'+name).classList.remove('hidden');
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  el.classList.add('active');
}

function gradeClass(g) {
  if (!g) return 'badge-grey';
  if (g.includes('A')) return 'badge-a';
  if (g.includes('B')) return 'badge-b';
  if (g.includes('C')) return 'badge-c';
  return 'badge-grey';
}

function statusClass(s) {
  if (!s) return '';
  if (s.includes('已簽約')) return 'badge-signed';
  if (s.includes('已下訂')) return 'badge-ordered';
  if (s.includes('未成交')) return 'badge-undone';
  return 'badge-grey';
}

// 日期轉數字（yyyymmdd）供排序，無法解析回傳 0
// 同時支援：2026/6/10、2026-6-10、2026.6.10、gviz 的 Date(y,m,d)
function 日期數值(v) {
  const s = String(v || '').trim();
  if (!s) return 0;
  let m = s.match(/Date\((\d+),(\d+),(\d+)/);            // gviz 日期物件（月從 0 起算）
  if (m) return Number(m[1]) * 10000 + (Number(m[2]) + 1) * 100 + Number(m[3]);
  m = s.match(/(\d{4})[\/\-.](\d{1,2})[\/\-.](\d{1,2})/); // 一般年月日格式
  if (m) return Number(m[1]) * 10000 + Number(m[2]) * 100 + Number(m[3]);
  return 0;
}

// 取最新接觸日：來訪／追蹤／首訪三者取最新（數字越大越新）
function 最新接觸日(c) {
  return Math.max(
    日期數值(c['最新來訪日期']),
    日期數值(c['最新追蹤日期']),
    日期數值(c['首次來訪日期'])
  );
}

// 由新到舊排序（無日期者數值為 0，自動沉底）
function 依最新接觸排序(clients) {
  return clients.sort((a, b) => 最新接觸日(b) - 最新接觸日(a));
}

function loadClients() {
  document.getElementById('clientList').innerHTML = '<div class="loading">正在載入客戶資料...</div>';
  fetch(`https://docs.google.com/spreadsheets/d/${SHEET_ID}/gviz/tq?tqx=out:json&sheet=客戶總覽&t=${Date.now()}`)
    .then(r => r.text())
    .then(text => {
      const json = JSON.parse(text.substring(47).slice(0, -2));
      const cols = json.table.cols.map(c => c.label);
      const rows = json.table.rows;
      allClients = rows.map(r => {
        const obj = {};
        cols.forEach((c, i) => { obj[c] = r.c[i] ? (r.c[i].f || r.c[i].v || '') : ''; });
        return obj;
      }).filter(c => c['聯絡電話'] && String(c['聯絡電話']).length >= 8);
      if (currentUser.role !== 'admin') {
        allClients = allClients.filter(c =>
          c['負責業務'] === currentUser.staff || c['指派業務'] === currentUser.staff
        );
      }
      依最新接觸排序(allClients);
      updateStats();
      renderClients(allClients);
    })
    .catch(err => {
      document.getElementById('clientList').innerHTML = '<div class="no-data">無法載入資料<br>請確認試算表已設為「知道連結的任何人可檢視」</div>';
    });
}

function updateStats() {
  document.getElementById('statTotal').textContent = allClients.length;
  document.getElementById('statVisited').textContent = allClients.filter(c => Number(c['來訪次數']) > 0).length;
  document.getElementById('statContacted').textContent = allClients.filter(c => String(c['是否已聯繫']).includes('✅')).length;
  document.getElementById('statDone').textContent = allClients.filter(c => String(c['是否成交']).includes('已下訂') || String(c['是否成交']).includes('已簽約')).length;
}

function doSearch() {
  const kw = document.getElementById('searchInput').value.trim().toLowerCase();
  const grade = document.getElementById('filterGrade').value;
  const status = document.getElementById('filterStatus').value;
  const staff = document.getElementById('filterStaff').value;
  const filtered = allClients.filter(c => {
    const matchKw = !kw || String(c['聯絡電話']).includes(kw) || String(c['客戶姓名']).toLowerCase().includes(kw);
    const matchGrade = !grade || String(c['客戶等級']).includes(grade);
    const matchStatus = !status || String(c['是否成交']).includes(status);
    const matchStaff = !staff || String(c['負責業務']).includes(staff) || String(c['指派業務']).includes(staff);
    return matchKw && matchGrade && matchStatus && matchStaff;
  });
  renderClients(filtered);
}

function renderClients(clients) {
  const list = document.getElementById('clientList');
  const count = document.getElementById('resultCount');
  count.textContent = `共 ${clients.length} 筆`;
  if (!clients.length) { list.innerHTML = '<div class="no-data">沒有符合條件的客戶</div>'; return; }
  const show = clients.slice(0, 80);
  list.innerHTML = show.map(c => {
    const phone = String(c['聯絡電話']);
    const isContacted = String(c['是否已聯繫']).includes('✅');
    const hasContact = c['是否已聯繫'] !== '';
    return `<div class="client-card" onclick="showDetail('${phone.replace(/'/g,"\\'")}')">
      <div class="client-card-top">
        <div>
          <div class="client-name">${c['客戶姓名'] || '未知姓名'}</div>
          <div class="client-phone">${phone}</div>
        </div>
        <div class="badges">
          ${c['客戶等級'] ? `<span class="badge ${gradeClass(c['客戶等級'])}">${String(c['客戶等級']).substring(0,2)}</span>` : ''}
          ${c['是否成交'] ? `<span class="badge ${statusClass(c['是否成交'])}">${c['是否成交']}</span>` : ''}
          ${hasContact ? `<span class="badge ${isContacted ? 'badge-contacted' : 'badge-notcontacted'}">${isContacted ? '已聯繫' : '未聯繫'}</span>` : ''}
        </div>
      </div>
      <div class="client-info">
        ${c['負責業務'] ? `<span class="info-item"><strong>業務</strong> ${c['負責業務']}</span>` : ''}
        ${c['居住區域'] ? `<span class="info-item"><strong>區域</strong> ${c['居住區域']}</span>` : ''}
        ${c['媒體來源'] ? `<span class="info-item"><strong>來源</strong> ${c['媒體來源']}</span>` : ''}
        ${Number(c['來訪次數']) > 0 ? `<span class="info-item"><strong>來訪</strong> ${c['來訪次數']}次</span>` : ''}
        ${c['最新來訪日期'] ? `<span class="info-item"><strong>最近來訪</strong> ${c['最新來訪日期']}</span>` : ''}
      </div>
    </div>`;
  }).join('') + (clients.length > 80 ? `<div class="no-data">顯示前80筆，請用搜尋縮小範圍</div>` : '');
}

function showDetail(phone) {
  const c = allClients.find(x => String(x['聯絡電話']) === phone);
  if (!c) return;
  document.getElementById('clientListView').classList.add('hidden');
  document.getElementById('clientDetailView').classList.remove('hidden');
  window.scrollTo(0, 0);
  const histories = c['完整歷程'] ? String(c['完整歷程']).split('─────').filter(h => h.trim()) : [];
  document.getElementById('detailContent').innerHTML = `
    <div class="detail-header">
      <div class="detail-name">${c['客戶姓名'] || '未知姓名'}</div>
      <div class="detail-meta">
        <span class="detail-phone">${c['聯絡電話']}</span>
        ${c['客戶等級'] ? `<span class="badge ${gradeClass(c['客戶等級'])}">${c['客戶等級']}</span>` : ''}
        ${c['是否成交'] ? `<span class="badge ${statusClass(c['是否成交'])}">${c['是否成交']}</span>` : ''}
      </div>
      <div class="detail-grid">
        ${field('負責業務', c['負責業務'] || c['指派業務'])}
        ${field('居住區域', c['居住區域'])}
        ${field('媒體來源', c['媒體來源'])}
        ${field('購屋用途', c['購屋用途'])}
        ${field('預算範圍', c['預算範圍'])}
        ${field('需求房數', c['需求房數'])}
        ${field('需求建坪', c['需求建坪'])}
        ${field('需求車位', c['需求車位'])}
        ${field('居住地址', c['居住地址'])}
        ${field('來源分類', c['來電名單來源'])}
        ${field('來訪次數', c['來訪次數'] ? c['來訪次數'] + '次' : '')}
        ${field('首次來訪', c['首次來訪日期'])}
      </div>
    </div>
    ${c['最新來訪記錄'] ? `
    <div class="section-title">最新來訪記錄</div>
    <div class="history-card">
      <div class="history-date">${c['最新來訪日期'] || ''}</div>
      <span class="history-type type-visit">來訪</span>
      <div class="history-content">${c['最新來訪記錄']}</div>
    </div>` : ''}
    ${c['聯繫紀錄'] ? `
    <div class="section-title">聯繫紀錄</div>
    <div class="history-card">
      <span class="history-type type-contact">${c['聯繫結果'] || '聯繫'}</span>
      <div class="history-content">${c['聯繫紀錄']}</div>
    </div>` : ''}
    ${histories.length ? `
    <div class="section-title">完整歷程（${histories.length}筆）</div>
    ${histories.map(h => {
      const isVisit = h.includes('來訪');
      const isCall = h.includes('電話') || h.includes('Line') || h.includes('簡訊');
      return `<div class="history-card">
        <span class="history-type ${isVisit ? 'type-visit' : isCall ? 'type-call' : 'type-contact'}">${isVisit ? '來訪' : isCall ? '電話追蹤' : '聯繫'}</span>
        <div class="history-content">${h.trim()}</div>
      </div>`;
    }).join('')}` : ''}
  `;
}

function field(label, val) {
  if (!val) return '';
  return `<div class="detail-field"><label>${label}</label><span>${val}</span></div>`;
}

function backToList() {
  document.getElementById('clientListView').classList.remove('hidden');
  document.getElementById('clientDetailView').classList.add('hidden');
  window.scrollTo(0, 0);
}

function changePwd() {
  const old = document.getElementById('oldPwd').value;
  const n = document.getElementById('newPwd').value;
  const c = document.getElementById('confirmPwd').value;
  const errEl = document.getElementById('pwdError');
  const msgEl = document.getElementById('pwdMsg');
  errEl.classList.add('hidden');
  msgEl.classList.add('hidden');
  if ((passwords[currentUser.account] || currentUser.password) !== old) {
    errEl.textContent = '目前密碼不正確';
    errEl.classList.remove('hidden'); return;
  }
  if (n.length < 3) {
    errEl.textContent = '新密碼至少需要3個字元';
    errEl.classList.remove('hidden'); return;
  }
  if (n !== c) {
    errEl.textContent = '兩次輸入的密碼不一致';
    errEl.classList.remove('hidden'); return;
  }
  passwords[currentUser.account] = n;
  document.getElementById('oldPwd').value = '';
  document.getElementById('newPwd').value = '';
  document.getElementById('confirmPwd').value = '';
  msgEl.classList.remove('hidden');
}
</script>
</body>
</html>
