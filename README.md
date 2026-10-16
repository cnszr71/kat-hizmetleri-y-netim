# kat-hizmetleri-y-netim
otel v1

<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#12352b">
  <title>CNSZR | Kat Hizmetleri</title>
  <style>
    :root {
      --green: #12352b;
      --green2: #205747;
      --bg: #f4f6f4;
      --white: #fff;
      --text: #202923;
      --muted: #718078;
      --line: #e2e8e3;
      --orange: #b76a19;
      --red: #b83e3e;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      color: var(--text);
      background: var(--bg);
    }

    button, input, select, textarea { font: inherit; }
    button { cursor: pointer; }

    .layout { min-height: 100vh; }

    header {
      background: var(--green);
      color: white;
      padding: 20px 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
    }

    .brand { font-size: 21px; font-weight: 800; }
    .brand small {
      display: block;
      margin-top: 5px;
      font-size: 12px;
      font-weight: 400;
      color: #c3d7cd;
    }

    .date { font-size: 12px; color: #d5e4dc; }

    .container {
      width: min(1200px, 100%);
      margin: auto;
      padding: 24px;
    }

    .welcome {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 22px;
    }

    h1 { font-size: 25px; margin: 0 0 7px; }
    h2 { font-size: 17px; margin: 0 0 16px; }
    .muted { color: var(--muted); font-size: 13px; }

    .stats {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
      margin-bottom: 24px;
    }

    .card {
      background: var(--white);
      border: 1px solid var(--line);
      border-radius: 13px;
      padding: 18px;
      min-width: 0;
    }

    .stat-number {
      font-size: 29px;
      font-weight: 800;
      margin: 12px 0 5px;
    }

    .stat-label { color: var(--muted); font-size: 13px; }

    .tabs {
      display: flex;
      gap: 7px;
      overflow-x: auto;
      margin-bottom: 18px;
      padding-bottom: 4px;
    }

    .tab {
      border: 1px solid var(--line);
      border-radius: 9px;
      padding: 11px 15px;
      white-space: nowrap;
      background: white;
      color: var(--text);
    }

    .tab.active {
      background: var(--green);
      color: white;
      border-color: var(--green);
    }

    .section { display: none; }
    .section.active { display: block; }

    .toolbar {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 16px;
    }

    input, select, textarea {
      width: 100%;
      min-width: 0;
      padding: 11px;
      border: 1px solid #d8e0d9;
      border-radius: 8px;
      background: white;
      color: var(--text);
    }

    .toolbar input { flex: 1; min-width: 150px; }
    .toolbar select { width: auto; flex: 0 1 190px; }

    .btn {
      border: 0;
      border-radius: 8px;
      background: var(--green);
      color: white;
      padding: 11px 15px;
      font-weight: 600;
    }

    .btn.secondary {
      background: white;
      border: 1px solid var(--line);
      color: var(--text);
    }

    .btn.danger { background: var(--red); }
    .btn.small { padding: 8px 10px; font-size: 12px; }

    .room-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 12px;
    }

    .room {
      background: white;
      border: 1px solid var(--line);
      border-radius: 12px;
      padding: 15px;
    }

    .room-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
      margin-bottom: 12px;
    }

    .room-number { font-size: 21px; font-weight: 800; }

    .status {
      display: inline-block;
      border-radius: 20px;
      padding: 5px 8px;
      font-size: 11px;
      font-weight: 700;
      background: #e7eee9;
      color: var(--green2);
    }

    .status.dirty { background: #fbe9d4; color: #89520f; }
    .status.cleaning { background: #dcecff; color: #24598e; }
    .status.inspect { background: #eee5fb; color: #68449b; }
    .status.issue { background: #fde5e5; color: #a42c2c; }

    .room select { margin: 13px 0 8px; font-size: 12px; }
    .room .btn { width: 100%; font-size: 12px; }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 13px;
    }

    .field { display: flex; flex-direction: column; gap: 7px; }
    .field label { font-size: 13px; font-weight: 700; }
    .field.full { grid-column: 1 / -1; }

    .list { display: grid; gap: 10px; }

    .list-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      padding: 15px;
      background: white;
      border: 1px solid var(--line);
      border-radius: 10px;
    }

    .list-item p { margin: 6px 0 0; font-size: 12px; color: var(--muted); }
    .actions { display: flex; flex-wrap: wrap; gap: 7px; }

    .empty {
      text-align: center;
      color: var(--muted);
      padding: 35px 12px;
      background: white;
      border-radius: 12px;
      border: 1px dashed var(--line);
    }

    .report-row { margin: 17px 0; }
    .report-label {
      display: flex;
      justify-content: space-between;
      gap: 10px;
      font-size: 13px;
      margin-bottom: 7px;
    }

    .bar { height: 9px; background: #e9eee9; border-radius: 20px; overflow: hidden; }
    .bar span { display: block; height: 100%; background: var(--green2); }

    .notice { font-size: 12px; color: var(--muted); margin-top: 15px; }

    footer {
      text-align: center;
      padding: 24px;
      color: var(--muted);
      font-size: 12px;
    }

    @media (max-width: 800px) {
      .room-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
      .stats { grid-template-columns: repeat(2, minmax(0, 1fr)); }
      .container { padding: 16px; }
      header { padding: 17px 16px; }
    }

    @media (max-width: 420px) {
      .room-grid { grid-template-columns: 1fr 1fr; gap: 8px; }
      .room { padding: 10px; }
      .room-number { font-size: 18px; }
      .date { display: none; }
      h1 { font-size: 22px; }
      .form-grid { grid-template-columns: 1fr; }
      .field.full { grid-column: auto; }
      .list-item { align-items: flex-start; flex-direction: column; }
    }
  </style>
</head>
<body>
<div class="layout">
  <header>
    <div class="brand">
      CNSZR
      <small>Kat Hizmetleri Yönetim Sistemi</small>
    </div>
    <div class="date" id="today"></div>
  </header>

  <main class="container">
    <div class="welcome">
      <div>
        <h1>Operasyon Paneli</h1>
        <div class="muted">Oda durumlarını ve günlük işleri buradan yönet.</div>
      </div>
      <button class="btn" onclick="showTab('rooms')">Odaları yönet</button>
    </div>

    <div class="stats">
      <div class="card">
        <div class="stat-label">Toplam oda</div>
        <div class="stat-number" id="total">34</div>
        <div class="muted">Tanımlı oda</div>
      </div>
      <div class="card">
        <div class="stat-label">Temiz oda</div>
        <div class="stat-number" id="cleanCount">0</div>
        <div class="muted">Hazır durumda</div>
      </div>
      <div class="card">
        <div class="stat-label">Bekleyen görev</div>
        <div class="stat-number" id="taskCount">0</div>
        <div class="muted">Tamamlanmamış</div>
      </div>
      <div class="card">
        <div class="stat-label">Açık arıza</div>
        <div class="stat-number" id="issueCount">0</div>
        <div class="muted">Çözüm bekleyen</div>
      </div>
    </div>

    <nav class="tabs">
      <button class="tab active" data-tab="rooms" onclick="showTab('rooms')">Odalar</button>
      <button class="tab" data-tab="tasks" onclick="showTab('tasks')">Görevler</button>
      <button class="tab" data-tab="inspection" onclick="showTab('inspection')">Kontrol</button>
      <button class="tab" data-tab="issues" onclick="showTab('issues')">Arızalar</button>
      <button class="tab" data-tab="reports" onclick="showTab('reports')">Raporlar</button>
    </nav>

    <section class="section active" id="rooms">
      <div class="card">
        <h2>Oda yönetimi</h2>
        <div class="toolbar">
          <input id="roomSearch" placeholder="Oda numarası ara..." oninput="renderRooms()">
          <select id="roomFilter" onchange="renderRooms()">
            <option value="">Tüm durumlar</option>
            <option value="dirty">Kirli</option>
            <option value="cleaning">Temizlik yapılıyor</option>
            <option value="inspect">Kontrol bekliyor</option>
            <option value="clean">Temiz / hazır</option>
            <option value="issue">Arızalı</option>
          </select>
          <button class="btn" onclick="addRoom()">+ Oda ekle</button>
        </div>
        <div class="room-grid" id="roomGrid"></div>
      </div>
    </section>

    <section class="section" id="tasks">
      <div class="card">
        <h2>Görev oluştur</h2>
        <form id="taskForm" class="form-grid">
          <div class="field">
            <label for="taskRoom">Oda</label>
            <select id="taskRoom" required></select>
          </div>
          <div class="field">
            <label for="taskPerson">Görevli personel</label>
            <input id="taskPerson" placeholder="Personel adı" required>
          </div>
          <div class="field full">
            <label for="taskNote">Görev açıklaması</label>
            <input id="taskNote" placeholder="Örn. Çıkış temizliği, havlu takviyesi">
          </div>
          <div class="field full">
            <button class="btn" type="submit">Görev ata</button>
          </div>
        </form>
      </div>
      <div class="card" style="margin-top:16px">
        <h2>Görev listesi</h2>
        <div class="list" id="taskList"></div>
      </div>
    </section>

    <section class="section" id="inspection">
      <div class="card">
        <h2>Oda kontrolü</h2>
        <p class="muted">Odayı kontrol ettikten sonra sonucu kaydet.</p>
        <form id="inspectionForm" class="form-grid">
          <div class="field">
            <label for="inspectionRoom">Oda</label>
            <select id="inspectionRoom" required></select>
          </div>
          <div class="field">
            <label for="inspector">Kontrol eden</label>
            <input id="inspector" placeholder="Sorumlu adı" required>
          </div>
          <div class="field full">
            <label for="inspectionResult">Kontrol sonucu</label>
            <select id="inspectionResult">
              <option value="pass">Uygun — oda hazır</option>
              <option value="fail">Eksik var — tekrar temizlik gerekli</option>
            </select>
          </div>
          <div class="field full">
            <label for="inspectionNote">Kontrol notu</label>
            <textarea id="inspectionNote" rows="3" placeholder="Örn. Banyo ve yatak kontrol edildi"></textarea>
          </div>
          <div class="field full">
            <button class="btn" type="submit">Kontrolü kaydet</button>
          </div>
        </form>
      </div>
      <div class="card" style="margin-top:16px">
        <h2>Son kontroller</h2>
        <div class="list" id="inspectionList"></div>
      </div>
    </section>

    <section class="section" id="issues">
      <div class="card">
        <h2>Arıza bildirimi</h2>
        <form id="issueForm" class="form-grid">
          <div class="field">
            <label for="issueRoom">Oda</label>
            <select id="issueRoom" required></select>
          </div>
          <div class="field">
            <label for="issueType">Arıza türü</label>
            <select id="issueType">
              <option>Elektrik</option>
              <option>Su / Tesisat</option>
              <option>Klima / Isıtma</option>
              <option>Mobilya</option>
              <option>Tekstil / Ekipman</option>
              <option>Diğer</option>
            </select>
          </div>
          <div class="field full">
            <label for="issueDescription">Arıza açıklaması</label>
            <textarea id="issueDescription" rows="3" required placeholder="Arızayı ve yerini tarif et"></textarea>
          </div>
          <div class="field">
            <label for="issueReporter">Bildiren personel</label>
            <input id="issueReporter" required placeholder="Personel adı">
          </div>
          <div class="field">
            <label for="issuePriority">Öncelik</label>
            <select id="issuePriority">
              <option>Normal</option>
              <option>Yüksek</option>
              <option>Acil</option>
            </select>
          </div>
          <div class="field full">
            <button class="btn" type="submit">Arıza kaydı oluştur</button>
          </div>
        </form>
      </div>
      <div class="card" style="margin-top:16px">
        <h2>Arıza kayıtları</h2>
        <div class="list" id="issueList"></div>
      </div>
    </section>

    <section class="section" id="reports">
      <div class="card">
        <h2>Güncel oda raporu</h2>
        <div id="reportBars"></div>
        <p class="notice">Raporlar bu tarayıcıdaki kayıtlı oda verilerinden hesaplanır.</p>
      </div>
      <div class="card" style="margin-top:16px">
        <h2>Günlük işlem özeti</h2>
        <div id="summary"></div>
        <button class="btn" style="margin-top:14px" onclick="exportReport()">Raporu CSV olarak indir</button>
      </div>
    </section>
  </main>

  <footer>CNSZR Kat Hizmetleri · İlk prototip</footer>
</div>

<script>
  const STORAGE_KEY = "cnszr-housekeeping-v1";
  const statusNames = {
    dirty: "Kirli",
    cleaning: "Temizlik yapılıyor",
    inspect: "Kontrol bekliyor",
    clean: "Temiz / hazır",
    issue: "Arızalı"
  };

  function initialData() {
    return {
      rooms: Array.from({ length: 34 }, (_, i) => ({
        number: String(i + 1).padStart(3, "0"),
        status: "dirty",
        person: ""
      })),
      tasks: [],
      inspections: [],
      issues: []
    };
  }

  function loadData() {
    try {
      const saved = localStorage.getItem(STORAGE_KEY);
      if (saved) {
        const parsed = JSON.parse(saved);
        if (parsed.rooms && parsed.tasks && parsed.issues && parsed.inspections) {
          return parsed;
        }
      }
    } catch (e) {
      console.error("Kayıt okunamadı", e);
    }
    return initialData();
  }

  let data = loadData();

  function save() {
    try {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
    } catch (e) {
      alert("Veri kaydedilemedi. Tarayıcı depolama alanını kontrol et.");
    }
    renderAll();
  }

  function escapeHTML(value) {
    return String(value ?? "").replace(/[&<>"']/g, ch => ({
      "&": "&amp;", "<": "&lt;", ">": "&gt;",
      '"': "&quot;", "'": "&#39;"
    })[ch]);
  }

  function showTab(id) {
    document.querySelectorAll(".section").forEach(el =>
      el.classList.toggle("active", el.id === id)
    );
    document.querySelectorAll(".tab").forEach(el =>
      el.classList.toggle("active", el.dataset.tab === id)
    );
    renderAll();
  }

  function addRoom() {
    const answer = prompt("Yeni oda numarası:");
    if (!answer) return;
    const number = answer.trim();
    if (!/^[a-zA-Z0-9-]{1,10}$/.test(number)) {
      alert("Oda numarası 1-10 karakter olmalı.");
      return;
    }
    if (data.rooms.some(r => r.number.toLowerCase() === number.toLowerCase())) {
      alert("Bu oda zaten kayıtlı.");
      return;
    }
    data.rooms.push({ number, status: "dirty", person: "" });
    save();
  }

  function updateRoom(number, status) {
    const room = data.rooms.find(r => r.number === number);
    if (!room) return;
    room.status = status;
    save();
  }

  function renderRooms() {
    const search = document.getElementById("roomSearch").value.toLowerCase();
    const filter = document.getElementById("roomFilter").value;
    const rooms = data.rooms.filter(r =>
      r.number.toLowerCase().includes(search) &&
      (!filter || r.status === filter)
    );

    document.getElementById("roomGrid").innerHTML = rooms.length
      ? rooms.map(r => `
        <article class="room">
          <div class="room-top">
            <span class="room-number">${escapeHTML(r.number)}</span>
            <span class="status ${r.status}">${statusNames[r.status]}</span>
          </div>
          <div class="muted">Görevli: ${escapeHTML(r.person || "Atanmadı")}</div>
          <select aria-label="${escapeHTML(r.number)} oda durumu"
            onchange="updateRoom('${escapeHTML(r.number)}',this.value)">
            ${Object.entries(statusNames).map(([key, name]) =>
              `<option value="${key}" ${r.status === key ? "selected" : ""}>${name}</option>`
            ).join("")}
          </select>
          <button class="btn secondary" onclick="showTab('tasks');document.getElementById('taskRoom').value='${escapeHTML(r.number)}'">Görev ata</button>
        </article>
      `).join("")
      : '<div class="empty">Bu filtreye uygun oda bulunamadı.</div>';
  }

  function fillRoomSelects() {
    ["taskRoom", "inspectionRoom", "issueRoom"].forEach(id => {
      const select = document.getElementById(id);
      const previous = select.value;
      select.innerHTML = data.rooms.map(r =>
        `<option value="${escapeHTML(r.number)}">${escapeHTML(r.number)}</option>`
      ).join("");
      if (data.rooms.some(r => r.number === previous)) select.value = previous;
    });
  }

  document.getElementById("taskForm").addEventListener("submit", event => {
    event.preventDefault();
    const roomNumber = document.getElementById("taskRoom").value;
    const person = document.getElementById("taskPerson").value.trim();
    const note = document.getElementById("taskNote").value.trim();

    if (!person || !data.rooms.some(r => r.number === roomNumber)) return;

    data.tasks.unshift({
      id: Date.now(),
      room: roomNumber,
      person,
      note: note || "Oda temizliği",
      status: "pending",
      date: new Date().toISOString()
    });

    const room = data.rooms.find(r => r.number === roomNumber);
    room.person = person;
    if (room.status === "dirty") room.status = "cleaning";

    event.target.reset();
    save();
  });

  function completeTask(id) {
    const task = data.tasks.find(t => t.id === id);
    if (!task || task.status === "done") return;
    task.status = "done";
    task.completedAt = new Date().toISOString();
    const room = data.rooms.find(r => r.number === task.room);
    if (room && room.status === "cleaning") room.status = "inspect";
    save();
  }

  function renderTasks() {
    const list = document.getElementById("taskList");
    list.innerHTML = data.tasks.length ? data.tasks.map(t => `
      <div class="list-item">
        <div>
          <strong>Oda ${escapeHTML(t.room)} · ${escapeHTML(t.person)}</strong>
          <p>${escapeHTML(t.note)} · ${t.status === "done" ? "Tamamlandı" : "Bekliyor"}</p>
        </div>
        ${t.status === "pending"
          ? `<button class="btn small" onclick="completeTask(${t.id})">Tamamla</button>`
          : '<span class="status">Tamamlandı</span>'}
      </div>
    `).join("") : '<div class="empty">Henüz görev oluşturulmadı.</div>';
  }

  document.getElementById("inspectionForm").addEventListener("submit", event => {
    event.preventDefault();
    const roomNumber = document.getElementById("inspectionRoom").value;
    const inspector = document.getElementById("inspector").value.trim();
    const result = document.getElementById("inspectionResult").value;
    const note = document.getElementById("inspectionNote").value.trim();
    const room = data.rooms.find(r => r.number === roomNumber);
    if (!room || !inspector) return;

    room.status = result === "pass" ? "clean" : "dirty";

    data.inspections.unshift({
      id: Date.now(),
      room: roomNumber,
      inspector,
      result,
      note,
      date: new Date().toISOString()
    });

    event.target.reset();
    save();
  });

  function renderInspections() {
    const list = document.getElementById("inspectionList");
    list.innerHTML = data.inspections.length ? data.inspections.slice(0, 30).map(i => `
      <div class="list-item">
        <div>
          <strong>Oda ${escapeHTML(i.room)} · ${escapeHTML(i.inspector)}</strong>
          <p>${i.result === "pass" ? "Uygun" : "Tekrar temizlik gerekli"} · ${escapeHTML(i.note || "Not yok")}</p>
          <p>${new Date(i.date).toLocaleString("tr-TR")}</p>
        </div>
        <span class="status ${i.result === "pass" ? "" : "dirty"}">${i.result === "pass" ? "Onaylandı" : "Eksik var"}</span>
      </div>
    `).join("") : '<div class="empty">Henüz kontrol kaydı yok.</div>';
  }

  document.getElementById("issueForm").addEventListener("submit", event => {
    event.preventDefault();
    const roomNumber = document.getElementById("issueRoom").value;
    const description = document.getElementById("issueDescription").value.trim();
    const reporter = document.getElementById("issueReporter").value.trim();
    const type = document.getElementById("issueType").value;
    const priority = document.getElementById("issuePriority").value;
    if (!description || !reporter) return;

    data.issues.unshift({
      id: Date.now(),
      room: roomNumber,
      description,
      reporter,
      type,
      priority,
      status: "open",
      date: new Date().toISOString()
    });

    const room = data.rooms.find(r => r.number === roomNumber);
    if (room) room.status = "issue";

    event.target.reset();
    save();
  });

  function closeIssue(id) {
    const issue = data.issues.find(i => i.id === id);
    if (!issue) return;
    issue.status = "closed";
    issue.closedAt = new Date().toISOString();

    const room = data.rooms.find(r => r.number === issue.room);
    const anotherOpenIssue = data.issues.some(i =>
      i.room === issue.room && i.status === "open"
    );
    if (room && !anotherOpenIssue && room.status === "issue") {
      room.status = "dirty";
    }
    save();
  }

  function renderIssues() {
    const list = document.getElementById("issueList");
    list.innerHTML = data.issues.length ? data.issues.map(i => `
      <div class="list-item">
        <div>
          <strong>Oda ${escapeHTML(i.room)} · ${escapeHTML(i.type)}</strong>
          <p>${escapeHTML(i.description)}</p>
          <p>Bildiren: ${escapeHTML(i.reporter)} · Öncelik: ${escapeHTML(i.priority)}</p>
          <p>${i.status === "open" ? "Açık" : "Çözüldü"} · ${new Date(i.date).toLocaleString("tr-TR")}</p>
        </div>
        ${i.status === "open"
          ? `<button class="btn small" onclick="closeIssue(${i.id})">Çözüldü</button>`
          : '<span class="status">Kapandı</span>'}
      </div>
    `).join("") : '<div class="empty">Arıza bildirimi yok.</div>';
  }

  function renderReports() {
    const counts = {};
    Object.keys(statusNames).forEach(k => counts[k] = 0);
    data.rooms.forEach(r => counts[r.status]++);

    const total = data.rooms.length || 1;
    document.getElementById("reportBars").innerHTML =
      Object.entries(statusNames).map(([key, name]) => `
        <div class="report-row">
          <div class="report-label">
            <span>${name}</span>
            <strong>${counts[key]} oda · %${Math.round(counts[key] / total * 100)}</strong>
          </div>
          <div class="bar"><span style="width:${counts[key] / total * 100}%"></span></div>
        </div>
      `).join("");

    const today = new Date().toDateString();
    const completedToday = data.tasks.filter(t =>
      t.status === "done" && t.completedAt &&
      new Date(t.completedAt).toDateString() === today
    ).length;

    const inspectionsToday = data.inspections.filter(i =>
      new Date(i.date).toDateString() === today
    ).length;

    document.getElementById("summary").innerHTML = `
      <p>Toplam tanımlı oda: <strong>${data.rooms.length}</strong></p>
      <p>Bugün tamamlanan görev: <strong>${completedToday}</strong></p>
      <p>Bugün yapılan kontroller: <strong>${inspectionsToday}</strong></p>
      <p>Açık arızalar: <strong>${data.issues.filter(i => i.status === "open").length}</strong></p>
      <p>Bekleyen görevler: <strong>${data.tasks.filter(t => t.status === "pending").length}</strong></p>
    `;
  }

  function exportReport() {
    const rows = [["Oda", "Durum", "Görevli"]];
    data.rooms.forEach(r => rows.push([
      r.number, statusNames[r.status], r.person || ""
    ]));

    const csv = "\uFEFF" + rows.map(row =>
      row.map(cell => '"' + String(cell).replace(/"/g, '""') + '"').join(";")
    ).join("\r\n");

    const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = "cnszr-oda-raporu.csv";
    a.click();
    URL.revokeObjectURL(url);
  }

  function renderAll() {
    document.getElementById("total").textContent = data.rooms.length;
    document.getElementById("cleanCount").textContent =
      data.rooms.filter(r => r.status === "clean").length;
    document.getElementById("taskCount").textContent =
      data.tasks.filter(t => t.status === "pending").length;
    document.getElementById("issueCount").textContent =
      data.issues.filter(i => i.status === "open").length;

    fillRoomSelects();
    renderRooms();
    renderTasks();
    renderInspections();
    renderIssues();
    renderReports();
  }

  document.getElementById("today").textContent =
    new Date().toLocaleDateString("tr-TR", {
      weekday: "long", day: "numeric", month: "long", year: "numeric"
    });

  renderAll();
</script>
</body>
</html>
