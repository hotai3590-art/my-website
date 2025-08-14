<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Lộ Trình Song Song Anh + Trung</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800;900&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #0b0f17; /* deep space */
      --panel: rgba(255,255,255,0.06);
      --panel-2: rgba(255,255,255,0.08);
      --text: #e8eefc;
      --muted: #9bb0d3;
      --primary: #7cf0ff; /* cyan neon */
      --accent: #a86bff; /* purple neon */
      --danger: #ff5c7c;
      --ok: #3fe0a8;
      --glow: 0 0 24px rgba(124, 240, 255, 0.35), 0 0 48px rgba(168,107,255,0.25);
    }
    *{ box-sizing: border-box }
    html, body{ height:100%; }
    body{
      margin:0; font-family: 'Inter', system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
      background: radial-gradient(1200px 600px at 80% -10%, rgba(124,240,255,0.12), transparent 60%),
                  radial-gradient(900px 500px at -10% 30%, rgba(168,107,255,0.10), transparent 65%),
                  linear-gradient(180deg, #090d14, #0b0f17 60%, #0a0e14);
      color: var(--text);
      overflow-x: hidden;
    }
    .container{ width: min(1200px, 92vw); margin: 0 auto; }
    /* --- Fancy Hero --- */
    .hero{
      position: relative; padding: 72px 0 48px; text-align: center;
    }
    .title{
      font-size: clamp(30px, 5vw, 56px);
      font-weight: 900; letter-spacing: 0.5px; line-height: 1.05;
      background: linear-gradient(92deg, var(--primary), var(--accent));
      -webkit-background-clip: text; background-clip: text; color: transparent;
      text-shadow: 0 6px 40px rgba(124,240,255,0.12);
      animation: glowPulse 6s ease-in-out infinite;
    }
    @keyframes glowPulse {
      0%, 100% { filter: drop-shadow(0 0 0 rgba(124,240,255,0.0)); }
      50% { filter: drop-shadow(0 0 14px rgba(124,240,255,0.35)) drop-shadow(0 0 18px rgba(168,107,255,0.25)); }
    }
    .subtitle{ color: var(--muted); margin-top: 10px; font-weight: 500; }
    /* --- Nav --- */
    .nav{
      display:flex; gap:8px; justify-content:center; flex-wrap:wrap; margin:28px auto 10px;
    }
    .chip{ border: 1px solid rgba(255,255,255,0.12); background: var(--panel); color: var(--text);
      padding:10px 14px; border-radius: 999px; cursor:pointer; user-select:none; backdrop-filter: blur(6px);
      transition: transform .2s, background .2s, border-color .2s;
    }
    .chip:hover{ transform: translateY(-2px); background: var(--panel-2); border-color: rgba(124,240,255,.35); box-shadow: var(--glow); }
    .chip.active{ border-color: var(--primary); box-shadow: var(--glow); }
    /* --- Panels --- */
    .grid{ display:grid; grid-template-columns: repeat(12, 1fr); gap: 16px; margin: 24px 0 40px; }
    .card{
      grid-column: span 12; padding: 18px 18px 20px; border:1px solid rgba(255,255,255,0.12); background: var(--panel);
      border-radius: 18px; backdrop-filter: blur(8px); position: relative; overflow: hidden;
      transition: transform .2s ease, box-shadow .2s ease;
    }
    .card:hover{ transform: translateY(-3px); box-shadow: var(--glow); }
    .card h3{ margin: 6px 0 8px; font-size: 20px; letter-spacing:.2px }
    .muted{ color: var(--muted); font-size: 14px; }
    @media (min-width: 960px){
      .col-4{ grid-column: span 4; }
      .col-6{ grid-column: span 6; }
      .col-8{ grid-column: span 8; }
      .col-3{ grid-column: span 3; }
    }
    /* --- Calendar --- */
    .calendar{ display:grid; grid-template-columns: repeat(7, 1fr); gap:8px; }
    .weekday{ text-align:center; color: var(--muted); font-size:12px; letter-spacing: .5px }
    .day{
      aspect-ratio: 1/1; border:1px solid rgba(255,255,255,0.12); border-radius: 14px; background: rgba(255,255,255,0.03);
      display:flex; align-items:center; justify-content:center; font-weight:600; cursor:pointer; position:relative; overflow:hidden; transition: transform .12s;
    }
    .day:hover{ transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.25); }
    .day.disabled{ opacity: .28; cursor: not-allowed; }
    .day.today{ outline: 2px solid var(--primary); box-shadow: var(--glow); }
    .day .dot{ position:absolute; bottom:8px; width:6px; height:6px; border-radius:999px; background: var(--accent) }
    .calendar-controls{ display:flex; gap:10px; align-items:center; justify-content:space-between; margin-bottom: 12px }
    .select, .toggle{
      background: var(--panel); border:1px solid rgba(255,255,255,0.14); color: var(--text); border-radius: 12px; padding: 10px 12px; font-weight:600;
    }
    .toggle input{ margin-right: 8px }
    /* --- Badges --- */
    .badge{ display:inline-flex; align-items:center; gap:6px; padding:6px 10px; font-size:12px; border-radius:999px; border:1px solid rgba(255,255,255,0.14); background: rgba(255,255,255,0.04) }
    .b-ok{ border-color: rgba(63,224,168,.35) }
    .b-warn{ border-color: rgba(255,92,124,.45) }
    /* --- Sections --- */
    .section-title{ font-size: 24px; font-weight: 800; margin: 8px 0 14px; letter-spacing:.3px }
    .list{ display:grid; gap:10px; }
    .list .item{ display:flex; gap:12px; align-items:flex-start; background: rgba(255,255,255,0.04); padding:12px 14px; border-radius: 14px; border:1px solid rgba(255,255,255,0.08); }
    .kdot{ width:8px; height:8px; border-radius: 999px; background: var(--primary); box-shadow: 0 0 16px rgba(124,240,255,.6); margin-top: 7px }
    /* --- Footer --- */
    footer{ text-align:center; color: var(--muted); padding: 40px 0 60px }
    /* --- Float Actions --- */
    .fab{
      position: fixed; right: 18px; bottom: 18px; z-index: 50; display:flex; flex-direction:column; gap:10px;
    }
    .btn{
      border:1px solid rgba(255,255,255,0.16); background: linear-gradient(180deg, rgba(124,240,255,.14), rgba(168,107,255,.12)); color: var(--text);
      padding: 10px 14px; border-radius: 12px; font-weight: 700; cursor: pointer; transition: transform .2s, box-shadow .2s;
      backdrop-filter: blur(6px);
    }
    .btn:hover{ transform: translateY(-2px); box-shadow: var(--glow); }
    /* --- Subtle particles --- */
    .particles{ position: fixed; inset:0; pointer-events:none; z-index:0; }
    .particle{ position:absolute; width:3px; height:3px; border-radius:50%; background: rgba(124,240,255,.8); filter: blur(0.3px); animation: floatUp linear infinite; opacity:.65 }
    @keyframes floatUp{ from{ transform: translateY(0); } to{ transform: translateY(-120vh); } }
  </style>
</head>
<body>
  <canvas class="particles" id="particles"></canvas>
  <div class="container">
    <header class="hero">
      <h1 class="title">LỘ TRÌNH SONG SONG <span style="white-space:nowrap">TIẾNG ANH</span> + <span style="white-space:nowrap">TIẾNG TRUNG</span></h1>
      <p class="subtitle">Học chuẩn ngay từ đầu – Ngầu, rõ ràng, bấm vào lịch để biết “Ngày hôm nay học gì”.</p>
      <div class="nav" id="nav">
        <div class="chip active" data-target="#roadmap">🚀 Lộ trình 6 tháng</div>
        <div class="chip" data-target="#calendar">📅 Lịch & Kế hoạch ngày</div>
        <div class="chip" data-target="#mistakes">⚠️ Sai lầm cần né</div>
        <div class="chip" data-target="#resources">🧰 Tài nguyên</div>
      </div>
    </header>
    <!-- Roadmap Section -->
    <section id="roadmap" class="grid">
      <article class="card col-8">
        <h3>🎯 Mục tiêu tổng</h3>
        <p class="muted">6 tháng để giao tiếp được và xem phim hiện đại hiểu 60–70% (không phụ đề). Trung: ưu tiên nghe–nói. Anh: ưu tiên nghe–đọc.</p>
        <div class="list" style="margin-top:10px">
          <div class="item"><span class="kdot"></span><div><strong>Tháng 1:</strong> Phát âm chuẩn + 150 từ cơ bản mỗi ngôn ngữ. Chào hỏi, tự giới thiệu.</div></div>
          <div class="item"><span class="kdot"></span><div><strong>Tháng 2:</strong> Ăn uống, mua sắm, hỏi đường. Ngữ pháp cơ bản (câu hỏi/câu phủ định).</div></div>
          <div class="item"><span class="kdot"></span><div><strong>Tháng 3:</strong> Kể hoạt động hằng ngày, sở thích. So sánh, liên kết (<em>比…</em>; because–therefore).</div></div>
          <div class="item"><span class="kdot"></span><div><strong>Tháng 4:</strong> Nghe nhanh hơn: chép từ khóa khi xem, mở rộng từ cảm thán/miêu tả.</div></div>
          <div class="item"><span class="kdot"></span><div><strong>Tháng 5:</strong> Nói trôi chảy 30–60s, cấu trúc phức hợp (如果…就…; although–but).</div></div>
          <div class="item"><span class="kdot"></span><div><strong>Tháng 6:</strong> Xem tập 45′ không sub, tóm tắt 10 câu; nghe tin ngắn và kể lại.</div></div>
        </div>
      </article>
      <aside class="card col-4">
        <h3>🔧 Nguyên tắc học song song</h3>
        <ul class="muted">
          <li>Chia thời gian: mỗi ngôn ngữ 45′/ngày, không học liền kề.</li>
          <li>Mỗi ngôn ngữ có sổ tay/app riêng. Không dịch qua lại khi nói.</li>
          <li>Học theo cụm từ + dùng ngay trong ngữ cảnh.</li>
        </ul>
        <div style="margin-top:10px; display:flex; gap:8px; flex-wrap:wrap">
          <span class="badge b-ok">✅ Shadowing</span>
          <span class="badge b-ok">✅ Spaced Repetition</span>
          <span class="badge b-ok">✅ Chunking</span>
          <span class="badge b-warn">⛔ Học từ rời rạc</span>
          <span class="badge b-warn">⛔ Chỉ học viết</span>
          <span class="badge b-warn">⛔ Bỏ ôn tập</span>
        </div>
      </aside>
      <article class="card col-12">
        <h3>🧭 Lịch mẫu mỗi ngày</h3>
        <p class="muted">Sáng: Trung – Phát âm & lặp lại | Chiều: Anh – Từ/cụm + câu mẫu | Tối: Xem clip mỗi ngôn ngữ 5–10′ không phụ đề.</p>
      </article>
    </section>
    <!-- Calendar & Daily Plan Section -->
    <section id="calendar" class="grid" style="display:none">
      <article class="card col-7">
        <div class="calendar-controls">
          <div>
            <select class="select" id="monthSelect"></select>
            <select class="select" id="planRange">
              <option value="180">6 tháng (180 ngày)</option>
              <option value="90">3 tháng (90 ngày)</option>
              <option value="30">1 tháng (30 ngày)</option>
            </select>
          </div>
          <div style="display:flex; gap:8px; align-items:center">
            <label class="toggle"><input type="checkbox" id="showCN" checked> Hiện kế hoạch <strong>Tiếng Trung</strong></label>
            <label class="toggle"><input type="checkbox" id="showEN" checked> Hiện kế hoạch <strong>Tiếng Anh</strong></label>
          </div>
        </div>
        <div class="calendar" id="calendarGrid"></div>
        <p class="muted" style="margin-top:10px">Mẹo: Di chuột để xem nhanh; bấm vào ngày để mở chi tiết, bài tập và mẫu câu.</p>
      </article>
      <aside class="card col-5" id="dayDetail">
        <h3>📌 Kế hoạch ngày <span id="dayLabel">—</span></h3>
        <div id="detailContent" class="list"></div>
      </aside>
    </section>
    <!-- Mistakes Section -->
    <section id="mistakes" class="grid" style="display:none">
      <article class="card col-12">
        <h3>⚠️ TOP Sai lầm cần né & cách sửa</h3>
        <div class="list">
          <div class="item"><span class="kdot"></span><div><strong>Học phát âm qua loa</strong><br><span class="muted">Sửa: Tuần 1–2 chỉ tập Pinyin/IPA + shadowing 10–15′/ngày, thu âm so với bản gốc.</span></div></div>
          <div class="item"><span class="kdot"></span><div><strong>Nhồi từ mà không dùng</strong><br><span class="muted">Sửa: Mỗi từ phải đi kèm 1 câu; học cụm (I’d like…, 我想…)</span></div></div>
          <div class="item"><span class="kdot"></span><div><strong>Bỏ qua ôn lại</strong><br><span class="muted">Sửa: Lịch ôn 1-3-7 (ngày 1/3/7), dùng thẻ lặp cách quãng.</span></div></div>
          <div class="item"><span class="kdot"></span><div><strong>Chỉ học viết, ít nghe</strong><br><span class="muted">Sửa: Tối nào cũng xem 5–10′ không sub, tua lại đoạn khó.</span></div></div>
          <div class="item"><span class="kdot"></span><div><strong>Dùng chung tài nguyên cho 2 ngôn ngữ</strong><br><span class="muted">Sửa: App riêng – Trung: HelloChinese/Pleco; Anh: Duolingo/BBC Learning English.</span></div></div>
        </div>
      </article>
    </section>
    <!-- Resources Section -->
    <section id="resources" class="grid" style="display:none">
      <article class="card col-6">
        <h3>🧰 Tài nguyên Tiếng Trung (giọng phổ thông)</h3>
        <ul class="muted">
          <li>YouTube: Mandarin Corner, Slow Chinese</li>
          <li>App: HelloChinese, Pleco, ChinesePod</li>
          <li>Phim/Series gợi ý: 《爱情公寓》, 《庆余年》, 《微微一笑很倾城》</li>
        </ul>
      </article>
      <article class="card col-6">
        <h3>🧰 Tài nguyên Tiếng Anh</h3>
        <ul class="muted">
          <li>YouTube: RealLife English, BBC Learning English</li>
          <li>App: Duolingo, ELSA Speak</li>
          <li>Phim/Series gợi ý: Friends, The Intern, Modern Family</li>
        </ul>
      </article>
      <article class="card col-12">
        <h3>📎 Mẫu câu “dùng ngay”</h3>
        <div class="list">
          <div class="item"><span class="kdot"></span><div><strong>CN:</strong> 你好，我叫… ／ 我想要… ／ 这个多少钱？</div></div>
          <div class="item"><span class="kdot"></span><div><strong>EN:</strong> Hi, I’m … ／ I’d like … ／ How much is this?</div></div>
        </div>
      </article>
    </section>
    <footer>
      Made for <strong>cậu chủ</strong> — học ít nhưng chuẩn, dùng nhiều hơn học ✨
    </footer>
  </div>

  <div class="fab">
    <button class="btn" id="todayBtn">🟢 Hôm nay học gì?</button>
    <button class="btn" id="randomBtn">🎲 Gợi ý ngẫu nhiên</button>
  </div>

  <script>
    // --- Tiny particle background
    const pCanvas = document.getElementById('particles');
    const pCtx = pCanvas.getContext('2d');
    let particles = [];
    function resize() { pCanvas.width = innerWidth; pCanvas.height = innerHeight; }
    addEventListener('resize', resize); resize();
    function spawnParticles(){
      particles = Array.from({length: 80}, () => ({
        x: Math.random()*pCanvas.width,
        y: Math.random()*pCanvas.height,
        r: Math.random()*1.8+0.6,
        s: Math.random()*0.4+0.2
      }));
    }
    spawnParticles();
    function drawParticles(){
      pCtx.clearRect(0,0,pCanvas.width,pCanvas.height);
      particles.forEach(p=>{
        p.y -= p.s; if(p.y < -10){ p.y = pCanvas.height + 10; p.x = Math.random()*pCanvas.width }
        pCtx.beginPath();
        pCtx.arc(p.x, p.y, p.r, 0, Math.PI*2);
        pCtx.fillStyle = 'rgba(124,240,255,.6)'; pCtx.fill();
      });
      requestAnimationFrame(drawParticles);
    }
    drawParticles();

    // --- Navigation chips
    const chips = document.querySelectorAll('.chip');
    chips.forEach(c => c.addEventListener('click', () => {
      chips.forEach(x => x.classList.remove('active'));
      c.classList.add('active');
      document.querySelectorAll('section').forEach(sec => sec.style.display = 'none');
      document.querySelector(c.dataset.target).style.display = '';
      if(c.dataset.target === '#calendar'){ buildCalendar(); }
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }));

    // --- Calendar builder ---
    const calendarGrid = document.getElementById('calendarGrid');
    const monthSelect = document.getElementById('monthSelect');
    const planRange = document.getElementById('planRange');
    const showCN = document.getElementById('showCN');
    const showEN = document.getElementById('showEN');
    const dayLabel = document.getElementById('dayLabel');
    const detailContent = document.getElementById('detailContent');

    // Generate months from today
    function formatMonth(d){
      return d.toLocaleString('vi-VN', { month:'long', year:'numeric' });
    }
    function setupMonthOptions(){
      monthSelect.innerHTML = '';
      const today = new Date();
      for(let i=0;i<6;i++){
        const d = new Date(today.getFullYear(), today.getMonth()+i, 1);
        const opt = document.createElement('option');
        opt.value = d.toISOString();
        opt.textContent = formatMonth(d);
        monthSelect.appendChild(opt);
      }
    }

    // Curriculum logic
    const weeks = [
      { name: 'Tuần 1', cn: 'Pinyin + 25 từ chào hỏi; shadowing 10′', en: 'IPA basics + 25 greetings; shadowing 10′' },
      { name: 'Tuần 2', cn: 'Thanh điệu + 25 từ gia đình; câu 你好，我叫…', en: 'Stress & rhythm + 25 family words; Hi, I’m …' },
      { name: 'Tuần 3', cn: 'Ăn uống: gọi món, 40 từ đồ ăn', en: 'Food: ordering, 40 food words' },
      { name: 'Tuần 4', cn: 'Mua sắm: 价格、尺寸；问价', en: 'Shopping: price & size; asking price' },
      { name: 'Tuần 5', cn: 'Hằng ngày + thời tiết; 比… so sánh', en: 'Daily routine + weather; comparisons' },
      { name: 'Tuần 6', cn: 'Sở thích + kế hoạch; 因为…所以…', en: 'Hobbies + plans; because–therefore' },
      { name: 'Tuần 7', cn: 'Nghe nhanh: chép  từ khóa khi xem', en: 'Active listening: keyword dictation' },
      { name: 'Tuần 8', cn: 'Miêu tả/cảm thán; mở rộng từ', en: 'Descriptions/exclamations; expand vocab' },
      { name: 'Tuần 9', cn: 'Nói trôi chảy 30s; 如果…就…', en: '30s monologue; if…then…' },
      { name: 'Tuần 10', cn: 'Mẫu câu tuy–nhưng 虽然…但是…', en: 'Although–but patterns' },
      { name: 'Tuần 11', cn: 'Tập xem tập 20–30′ không sub', en: 'Watch 20–30′ episode without subs' },
      { name: 'Tuần 12', cn: 'Tập 45′ không sub; tóm tắt 10 câu', en: '45′ episode challenge; 10-sentence summary' }
    ];

    // Helper: plan per day
    function getDailyPlan(dayNumber){
      // dayNumber: 1..180
      const weekIndex = Math.floor((dayNumber-1)/7); // 0..25
      const inWeekDay = ((dayNumber-1)%7)+1; // 1..7
      const wk = weeks[weekIndex % weeks.length]; // cycle after 12w if 180 days

      // Common slots
      const slots = [];
      // Chinese block
      slots.push({
        lang: 'CN',
        title: `CN – ${wk.name}`,
        bullets: [
          wk.cn,
          inWeekDay <= 2 ? 'Phát âm/nhại giọng 15′ (thu âm so sánh)' : 'Ôn phát âm 5′ + luyện câu 10′',
          inWeekDay === 7 ? 'Ôn 1-3-7: rà lại từ/câu tuần này' : 'Học 10–15 từ theo chủ đề của tuần',
          'Xem clip 5–10′ không sub, tua lại đoạn khó'
        ]
      });
      // English block
      slots.push({
        lang: 'EN',
        title: `EN – ${wk.name}`,
        bullets: [
          wk.en,
          inWeekDay <= 2 ? 'Pronunciation/shadowing 15′ (record & compare)' : 'Review 5′ + pattern practice 10′',
          inWeekDay === 7 ? 'Spaced review 1-3-7 for the week' : 'Learn 10–15 chunks with example sentences',
          'Watch 5–10′ clip without subs, rewind tricky lines'
        ]
      });

      // Sample ready-to-use sentences vary by day
      const samplesCN = [
        '你好，我叫林。', '这个多少钱？', '我想点这个。', '洗手间在哪里？', '今天几号？', '我会说一点中文。', '可以便宜一点吗？'
      ];
      const samplesEN = [
        'Hi, I’m Lin.', 'How much is this?', 'I’d like to order this.', 'Where is the restroom?', 'What’s the date today?', 'I can speak a little Chinese.', 'Can you give me a discount?'
      ];

      return { slots, samplesCN: samplesCN[(inWeekDay-1)%samplesCN.length], samplesEN: samplesEN[(inWeekDay-1)%samplesEN.length] };
    }

    function buildCalendar(){
      setupMonthOptions();
      const startDate = new Date();
      const totalDays = parseInt(planRange.value, 10);

      function render(){
        calendarGrid.innerHTML = '';
        // Weekday headers
        const weekdays = ['T2','T3','T4','T5','T6','T7','CN'];
        weekdays.forEach(w=>{
          const el = document.createElement('div'); el.className='weekday'; el.textContent = w; calendarGrid.appendChild(el);
        });
        // Selected month and its metrics
        const firstOfMonth = new Date(monthSelect.value);
        const y = firstOfMonth.getFullYear();
        const m = firstOfMonth.getMonth();
        const firstWeekday = ((new Date(y, m, 1)).getDay()+6)%7; // Mon=0
        const daysInMonth = new Date(y, m+1, 0).getDate();

        // Fill leading blanks
        for(let i=0;i<firstWeekday;i++){
          const d = document.createElement('div'); d.className='day disabled'; calendarGrid.appendChild(d);
        }
        // Create days
        for(let d=1; d<=daysInMonth; d++){
          const cell = document.createElement('div'); cell.className='day';
          const thisDate = new Date(y, m, d);
          const dayNum = Math.floor((thisDate - new Date(startDate.getFullYear(), startDate.getMonth(), startDate.getDate()))/86400000) + 1;
          const insidePlan = dayNum >= 1 && dayNum <= totalDays;
          cell.textContent = d;
          if(!insidePlan) cell.classList.add('disabled');
          if(new Date().toDateString() === thisDate.toDateString()) cell.classList.add('today');
          if(insidePlan){ const dot = document.createElement('div'); dot.className='dot'; cell.appendChild(dot); }

          if(insidePlan){
            cell.title = `Ngày ${dayNum}: bấm để xem chi tiết`;
            cell.addEventListener('click', ()=> selectDay(thisDate, dayNum));
            cell.addEventListener('mouseenter', ()=> cell.style.borderColor='rgba(124,240,255,.45)');
            cell.addEventListener('mouseleave', ()=> cell.style.borderColor='rgba(255,255,255,0.12)');
          }
          calendarGrid.appendChild(cell);
        }
      }

      function selectDay(dateObj, dayNum){
        dayLabel.textContent = `${dateObj.toLocaleDateString('vi-VN')} — Ngày ${dayNum}/${totalDays}`;
        const plan = getDailyPlan(dayNum);
        detailContent.innerHTML = '';

        if(showCN.checked){
          const block = document.createElement('div'); block.className='item';
          block.innerHTML = `<span class="kdot"></span><div><strong>${plan.slots[0].title}</strong><ul>${plan.slots[0].bullets.map(b=>`<li>${b}</li>`).join('')}</ul><div class="badge">Mẫu câu: ${plan.samplesCN}</div></div>`;
          detailContent.appendChild(block);
        }
        if(showEN.checked){
          const block2 = document.createElement('div'); block2.className='item';
          block2.innerHTML = `<span class="kdot"></span><div><strong>${plan.slots[1].title}</strong><ul>${plan.slots[1].bullets.map(b=>`<li>${b}</li>`).join('')}</ul><div class="badge">Sample: ${plan.samplesEN}</div></div>`;
          detailContent.appendChild(block2);
        }

        const tasks = document.createElement('div'); tasks.className='item';
        tasks.innerHTML = `<span class="kdot"></span><div><strong>🎯 Nhiệm vụ nhanh</strong><ul>
          <li>Ghi âm 30s (CN hoặc EN) và tự chấm <em>phát âm/nhịp điệu</em>.</li>
          <li>Viết 3 câu dùng từ/cụm mới hôm nay.</li>
          <li>Xem 5–10′ clip không phụ đề, tua lại 2 lần đoạn khó.</li>
        </ul></div>`;
        detailContent.appendChild(tasks);

        const review = document.createElement('div'); review.className='item';
        review.innerHTML = `<span class="kdot"></span><div><strong>🔁 Lịch ôn 1-3-7</strong><div class="muted">Hôm nay ôn lại bài của ngày ${Math.max(1, dayNum-1)}, ${Math.max(1, dayNum-3)}, ${Math.max(1, dayNum-7)}.</div></div>`;
        detailContent.appendChild(review);
      }

      // initial render & listeners
      render();
      monthSelect.addEventListener('change', render);
      planRange.addEventListener('change', render);
      showCN.addEventListener('change', () => {
        // refresh current selection
        const today = new Date();
        const dayNum = 1 + Math.floor((today - new Date(today.getFullYear(), today.getMonth(), today.getDate()))/86400000);
        detailContent.innerHTML = ''; // cleared; wait for explicit click
      });
      showEN.addEventListener('change', () => {
        detailContent.innerHTML = '';
      });

      // Auto-select today if inside plan
      const today = new Date();
      const dayNumToday = 1; // day 1 starts today
      selectDay(today, dayNumToday);
    }

    // Buttons
    document.getElementById('todayBtn').addEventListener('click', () => {
      // Jump to calendar tab and open today
      document.querySelectorAll('.chip').forEach(x=>x.classList.remove('active'));
      document.querySelector('.chip[data-target="#calendar"]').classList.add('active');
      document.querySelectorAll('section').forEach(sec => sec.style.display = 'none');
      document.querySelector('#calendar').style.display = '';
      buildCalendar();
      window.scrollTo({ top: 0, behavior: 'smooth' });
    });

    document.getElementById('randomBtn').addEventListener('click', () => {
      const total = parseInt(document.getElementById('planRange').value, 10);
      const rand = 1 + Math.floor(Math.random()*total);
      document.querySelectorAll('.chip').forEach(x=>x.classList.remove('active'));
      document.querySelector('.chip[data-target="#calendar"]').classList.add('active');
      document.querySelectorAll('section').forEach(sec => sec.style.display = 'none');
      document.querySelector('#calendar').style.display = '';
      buildCalendar();
      // after build, set selection
      const d = new Date(); d.setDate(d.getDate() + (rand-1));
      // small timeout to ensure DOM ready
      setTimeout(()=>{
        const label = document.getElementById('dayLabel');
        const detail = document.getElementById('detailContent');
        label.textContent = `${d.toLocaleDateString('vi-VN')} — Ngày ${rand}/${total}`;
        const plan = getDailyPlan(rand);
        detail.innerHTML = '';
        if(document.getElementById('showCN').checked){
          const block = document.createElement('div'); block.className='item';
          block.innerHTML = `<span class="kdot"></span><div><strong>${plan.slots[0].title}</strong><ul>${plan.slots[0].bullets.map(b=>`<li>${b}</li>`).join('')}</ul><div class="badge">Mẫu câu: ${plan.samplesCN}</div></div>`;
          detail.appendChild(block);
        }
        if(document.getElementById('showEN').checked){
          const block2 = document.createElement('div'); block2.className='item';
          block2.innerHTML = `<span class="kdot"></span><div><strong>${plan.slots[1].title}</strong><ul>${plan.slots[1].bullets.map(b=>`<li>${b}</li>`).join('')}</ul><div class="badge">Sample: ${plan.samplesEN}</div></div>`;
          detail.appendChild(block2);
        }
      }, 50);
    });
  </script>
</body>
</html>
