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

    /* Убираем overflow: hidden, чтобы книга не обрезалась */
    html, body {
      margin: 0;
      padding: 0;
      background: transparent !important;
      background-color: transparent !important;
      overflow-y: auto; /* Разрешаем прокрутку */
      overflow-x: hidden;
    }
    
    /* Базовые стили для книги со стрелками */
    .book-viewport {
      perspective: 2000px;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px 0;
      background: transparent !important;
      min-height: 100vh; /* Гарантируем, что контейнер займет всю высоту */
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
    .front-cover-page {
      background: linear-gradient(135deg, #8B0000 0%, #4A0000 100%);
      border-left: 8px solid #2A0000;
      border: 2px solid #5A0000;
    }
    .back-cover-page {
      background: #4A0000;
      border-left: 8px solid #2A0000;
    }
    .cover-design {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      color: #D4AF37;
      text-align: center;
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
      margin: 20px 0;
      border-radius: 4px;
      letter-spacing: 2px;
    }
    .cover-design p {
      font-size: 13px;
      color: #f0e6d2;
      font-style: italic;
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
      margin-top: 40px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
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
  </style>
</head>
<body>

<div class="book-viewport">
  <div class="book-wrapper" id="myBook">
    
    <!-- ЗАДНЯЯ ОБЛОЖКА -->
    <div class="b-page back-cover-page" style="z-index: 1;"></div>
    
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
            <li><b>Логи матча:</b> После игры найдите в «Моих документах» файл <b>match_log</b> и загрузите его через <b>желтый плюс</b> в чате матча.</li>
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
            <li><b>Верификация:</b> Обязательно привяжите Steam к сайту. Скопируйте проверочный код в поле «О себе» в Steam, чтобы админ верифицировал ваш аккаунт.</li>
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
    <div class="b-page front-cover-page" id="p0" style="z-index: 5;">
      <div class="page-side front-side">
        <div class="cover-design">
          <h2>РУКОВОДСТВО</h2>
          <div class="gold-badge">ЧАК-ЧАК</div>
          <p>Официальные правила турниров CS2</p>
          <button class="open-book-btn" onclick="turnPage(0, 'next')">Открыть книгу 📖</button>
        </div>
      </div>
    </div>

  </div>
</div>

<script>
function turnPage(pageId, direction) {
  const page = document.getElementById('p' + pageId);
  if (direction === 'next') {
    page.classList.add('flipped');
    setTimeout(() => { page.style.zIndex = pageId; }, 300);
  } else if (direction === 'prev') {
    page.style.zIndex = 5 - pageId;
    setTimeout(() => { page.classList.remove('flipped'); }, 50);
  }
}
</script>

</body>
</html>
