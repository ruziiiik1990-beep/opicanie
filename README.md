<html lang="ru" style="background: transparent !important;">
<head>
  <meta charset="UTF-8">
  <title>Правила</title>
  <style>
    /* СКРЫВАЕМ ЗАГОЛОВКИ GITHUB PAGES */
    #header, header, h1, .header, a[href*="rules"], a[href*="steamID"], .page-header, .project-name, .project-tagline {
      display: none !important;
      opacity: 0 !important;
      visibility: hidden !important;
      height: 0 !important;
      margin: 0 !important;
      padding: 0 !important;
    }

    html, body {
      margin: 0;
      padding: 0;
      background: transparent !important;
      background-color: transparent !important;
      overflow-y: auto;
      overflow-x: hidden;
    }
    
    .book-viewport {
      perspective: 2000px;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px 0;
      background: transparent !important;
      min-height: 100vh;
    }
    .book-wrapper {
      position: relative;
      width: 380px;
      height: 520px;
      transform-style: preserve-3d;
      transform: rotateX(15deg) rotateY(-5deg);
    }
    .b-page {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      transform-origin: left center;
      transform-style: preserve-3d;
      transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
      box-shadow: 0 4px 20px rgba(0,0,0,0.4);
      border-radius: 4px 12px 12px 4px;
    }
    .page-side {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      backface-visibility: hidden;
      border-radius: 4px 12px 12px 4px;
    }
    .back-side {
      transform: rotateY(180deg);
      background: #f5edd6;
    }
    
    /* ПЕРЕДНЯЯ ОБЛОЖКА */
    .front-cover-page {
      background: linear-gradient(135deg, #8B0000 0%, #4A0000 100%);
      border-left: 8px solid #2A0000;
      border: 2px solid #5A0000;
      transform: rotateY(-180deg); /* По умолчанию перевернута (книга закрыта) */
    }
    
    /* ЗАДНЯЯ ОБЛОЖКА (ее мы видим, когда книга закрыта) */
    .back-cover-page {
      background: linear-gradient(135deg, #4A0000 0%, #2A0000 100%);
      border-left: 8px solid #1A0000;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
    }

    .back-cover-text {
      color: #D4AF37;
      font-family: 'Georgia', serif;
      font-size: 22px;
      line-height: 1.5;
      font-weight: bold;
      margin-bottom: 20px;
      text-shadow: 1px 1px 3px rgba(0,0,0,0.5);
    }
    .back-cover-logo {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 3px solid #D4AF37;
      object-fit: cover;
      box-shadow: 0 4px 15px rgba(0,0,0,0.6);
    }

    .cover-design {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      color: #D4AF37;
      text-align: center;
      padding: 20px;
    }
    .cover-design h2 {
      font-family: 'Georgia', serif;
      font-size: 26px;
      letter-spacing: 3px;
      margin: 0;
    }
    .gold-badge {
      background: #D4AF37;
      color: #4A0000;
      padding: 6px 20px;
      font-weight: bold;
      font-size: 15px;
      margin: 15px 0;
      border-radius: 4px;
      letter-spacing: 2px;
    }
    .cover-design p {
      font-size: 13px;
      color: #f0e6d2;
      font-style: italic;
      margin-bottom: 15px;
    }
    
    /* Логотип на передней обложке */
    .front-cover-logo {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      border: 2px solid #D4AF37;
      object-fit: cover;
      margin-bottom: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.5);
    }

    .open-book-btn {
      background: #D4AF37;
      color: #4A0000;
      border: none;
      padding: 10px 20px;
      font-size: 13px;
      font-weight: bold;
      border-radius: 20px;
      cursor: pointer;
      margin-top: 20px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }
    
    .back-to-start-btn {
      background: transparent;
      color: #D4AF37;
      border: 1px solid #D4AF37;
      padding: 8px 16px;
      font-size: 12px;
      border-radius: 20px;
      cursor: pointer;
      margin-top: 10px;
      display: none;
    }

    .nav-arrow {
      position: absolute;
      bottom: 20px;
      background: #8B0000;
      color: #fff;
      border: none;
      padding: 6px 14px;
      font-size: 12px;
      border-radius: 4px;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      z-index: 10;
    }
    .next-arrow { right: 20px; }
    .prev-arrow { left: 40px; }
    .paper-page {
      background: #fcf8f2;
      color: #2b2b2b;
      border: 1px solid #e8dec9;
    }
    .text-box {
      padding: 45px 25px 30px 45px;
      font-family: sans-serif;
      font-size: 13px;
      line-height: 1.6;
    }
    .text-box h3 {
      font-family: 'Georgia', serif;
      color: #8B0000;
      border-bottom: 2px solid #e8dec9;
      padding-bottom: 8px;
      margin-top: 0;
      font-size: 18px;
    }
    .text-box ul { padding-left: 15px; margin: 0; }
    .text-box li { margin-bottom: 12px; }
    .small-text-note {
      font-style: italic;
      font-size: 11px;
      color: #777;
      margin-top: 25px;
      text-align: center;
      border-top: 1px dashed #ddd;
      padding-top: 10px;
    }
    
    .b-page.flipped {
      transform: rotateY(-180deg);
    }
    
    /* Переопределяем переворот для передней обложки, чтобы она была закрыта по умолчанию */
    .b-page.front-cover-page.flipped {
      transform: rotateY(0deg);
    }
  </style>
</head>
<body>

<div class="book-viewport">
  <div class="book-wrapper" id="myBook">
    
    <!-- ЗАДНЯЯ ОБЛОЖКА (видна, когда книга закрыта) -->
    <div class="b-page back-cover-page" style="z-index: 1;">
      <div class="back-cover-text">Спасибо за прочтение<br>и удача в погоне за <span style="white-space: nowrap;">Чак-Чак!</span></div>
      <img src="https://4ak4ak.moy.su/logo1.jpg" class="back-cover-logo" alt="Чак-Чак">
    </div>
    
    <!-- СТРАНИЦА 3: ПРИЗЫ -->
    <div class="b-page paper-page" id="p3" style="z-index: 2;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>🏆 Призы и Рейтинг</h3>
          <ul>
            <li><b>Финал матча:</b> Победители получают скины лучшего качества, проигравшие в финале — скины послабее. Призы отображаются в меню противостояния.</li>
            <li><b>Выдача скинов:</b> Админ добавляет вас в друзья в Steam, заносит в блокнот и передает скины сразу, как спадет временная блокировка обмена Steam.</li>
            <li><b>Рейтинг «Чак-Чак»:</b> За победу в турнире начисляется <b>2 чак-чака</b>, за участие в финале (2 место) — <b>1 чак-чак</b>.</li>
          </ul>
          <p class="small-text-note">Турнир создан ради эмоций и символических призов!</p>
        </div>
        <button class="nav-arrow prev-arrow" onclick="turnPage(3, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 2: АНТИЧИТ -->
    <div class="b-page paper-page" id="p2" style="z-index: 3;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>🛡️ Anti-cheat и Старт</h3>
          <ul>
            <li><b>Запуск:</b> Перед запуском игры <b>обязательно</b> включите античит <u>ruzikTastyAC</u>. Включение во время игры — тех. поражение всей команде.</li>
            <li><b>Коннект к серверу:</b> После согласования времени в чате появится кнопка <b>Connected</b> для автовыхода на сервер CS2.</li>
            <li><b>Залив файла анти-чита:</b> После игры найдите в «Моих документах» файл <b>match_log</b> и загрузите его через <b>желтый плюс</b> в противостоянии матча.</li>
          </ul>
        </div>
        <button class="nav-arrow next-arrow" onclick="turnPage(2, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <button class="nav-arrow prev-arrow" onclick="turnPage(2, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 1: ОБЩИЕ ПРАВИЛА -->
    <div class="b-page paper-page" id="p1" style="z-index: 4;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>📝 Основные правила</h3>
          <ul>
            <li><b>Верификация:</b> Обязательно привяжите Steam к сайту. Чтобы админ верифицировал ваш аккаунт и видел вас в матче, что это именно вы.</li>
            <li><b>Формат:</b> Сетка плей-офф 5х5. Турнир проходит раз в 2 недели (с пятницы по воскресенье). Регистрация открывается 1-го числа.</li>
            <li><b>Рандом:</b> Участники распределяются по командам случайно. Победители этапа снова перемешиваются в новые команды для следующей стадии.</li>
          </ul>
        </div>
        <button class="nav-arrow next-arrow" onclick="turnPage(1, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <button class="nav-arrow prev-arrow" onclick="turnPage(1, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- ПЕРЕДНЯЯ ОБЛОЖКА -->
    <div class="b-page front-cover-page flipped" id="p0" style="z-index: 5;">
      <div class="page-side front-side">
        <div class="cover-design">
          <img src="https://4ak4ak.moy.su/logo1.jpg" class="front-cover-logo" alt="Логотип">
          <h2>РУКОВОДСТВО</h2>
          <div class="gold-badge">ЧАК-ЧАК</div>
          <p>Официальные правила турниров CS2</p>
          <button class="open-book-btn" onclick="turnPage(0, 'next')">Открыть книгу 📖</button>
          <button class="back-to-start-btn" id="backToStartBtn" onclick="closeBook()">Вернуться на обложку</button>
        </div>
      </div>
    </div>

  </div>
</div>

<script>
// Перелистывание страниц
function turnPage(pageId, direction) {
  const page = document.getElementById('p' + pageId);
  
  if (direction === 'next') {
    page.classList.add('flipped');
    setTimeout(() => { page.style.zIndex = pageId; }, 300);
    
    if (pageId === 0) {
      document.getElementById('backToStartBtn').style.display = 'inline-block';
    }
  } else if (direction === 'prev') {
    page.style.zIndex = 6 - pageId;
    setTimeout(() => { page.classList.remove('flipped'); }, 50);
  }
}

// Закрытие книги (возврат на обложку)
function closeBook() {
  // Переворачиваем страницы 1, 2, 3 обратно
  [1, 2, 3].forEach(i => {
    const page = document.getElementById('p' + i);
    if (page) {
      page.classList.remove('flipped');
      // Возвращаем z-index
      if (i === 1) page.style.zIndex = 4;
      else if (i === 2) page.style.zIndex = 3;
      else if (i === 3) page.style.zIndex = 2;
    }
  });
  
  // Закрываем переднюю обложку
  const p0 = document.getElementById('p0');
  setTimeout(() => {
    p0.classList.remove('flipped');
    p0.style.zIndex = 5;
  }, 100);

  // Скрываем кнопку "Вернуться на обложку"
  document.getElementById('backToStartBtn').style.display = 'none';
}
</script>

</body>
</html>
