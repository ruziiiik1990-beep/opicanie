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
      perspective: 2500px;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 40px 0;
      background: transparent !important;
      min-height: 100vh;
      /* Добавил отступ слева, чтобы при открытии книга не улетала за край */
      padding-left: 20%; 
    }
    
    .book-wrapper {
      position: relative;
      width: 494px; 
      height: 572px;
      transform-style: preserve-3d;
      /* Сдвиг вправо (translateX) и масштаб (scale) */
      transform: translateX(15%) scale(1.05) rotateX(15deg) rotateY(-5deg);
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
      box-shadow: 0 4px 25px rgba(0,0,0,0.4);
      border-radius: 4px 16px 16px 4px;
    }
    .page-side {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      backface-visibility: hidden;
      border-radius: 4px 16px 16px 4px;
    }
    .back-side {
      transform: rotateY(180deg);
      background: #fcf8f2;
      border-radius: 16px 4px 4px 16px;
      border: 1px solid #e8dec9;
    }
    
    /* ПЕРЕДНЯЯ ОБЛОЖКА */
    .front-cover-page {
      background: linear-gradient(135deg, #8B0000 0%, #4A0000 100%);
      border-left: 10px solid #2A0000;
      border: 2px solid #5A0000;
    }
    
    /* ЗАДНЯЯ ОБЛОЖКА */
    .back-cover-page {
      background: linear-gradient(135deg, #4A0000 0%, #2A0000 100%);
      border-left: 10px solid #1A0000;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 25px;
    }

    .back-cover-text {
      color: #D4AF37;
      font-family: 'Georgia', serif;
      font-size: 26px;
      line-height: 1.5;
      font-weight: bold;
      margin-bottom: 25px;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
    }
    .back-cover-logo {
      width: 150px;
      height: 150px;
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
      padding: 25px;
    }
    .cover-design h2 {
      font-family: 'Georgia', serif;
      font-size: 32px;
      letter-spacing: 4px;
      margin: 0;
    }
    .gold-badge {
      background: #D4AF37;
      color: #4A0000;
      padding: 8px 25px;
      font-weight: bold;
      font-size: 18px;
      margin: 20px 0;
      border-radius: 6px;
      letter-spacing: 2px;
    }
    .cover-design p {
      font-size: 15px;
      color: #f0e6d2;
      font-style: italic;
      margin-bottom: 20px;
    }
    
    .front-cover-logo {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      border: 2px solid #D4AF37;
      object-fit: cover;
      margin-bottom: 25px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.5);
    }

    .open-book-btn {
      background: #D4AF37;
      color: #4A0000;
      border: none;
      padding: 12px 24px;
      font-size: 15px;
      font-weight: bold;
      border-radius: 25px;
      cursor: pointer;
      margin-top: 25px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }
    
    .back-to-start-btn {
      background: transparent;
      color: #D4AF37;
      border: 1px solid #D4AF37;
      padding: 10px 20px;
      font-size: 14px;
      border-radius: 20px;
      cursor: pointer;
      margin-top: 15px;
      display: none;
    }

    .nav-arrow {
      position: absolute;
      bottom: 25px;
      background: #8B0000;
      color: #fff;
      border: none;
      padding: 8px 18px;
      font-size: 14px;
      border-radius: 4px;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
      z-index: 10;
    }
    .next-arrow { right: 25px; }
    .prev-arrow { left: 25px; }
    
    .paper-page {
      background: #fcf8f2;
      color: #2b2b2b;
      border: 1px solid #e8dec9;
    }
    .text-box {
      padding: 55px 35px 35px 55px;
      font-family: sans-serif;
      font-size: 15px;
      line-height: 1.7;
    }
    .text-box h3 {
      font-family: 'Georgia', serif;
      color: #8B0000;
      border-bottom: 2px solid #e8dec9;
      padding-bottom: 10px;
      margin-top: 0;
      font-size: 22px;
    }
    .text-box ul { padding-left: 20px; margin: 0; }
    .text-box li { margin-bottom: 15px; }
    
    /* СТИЛИ ДЛЯ ГИФОК: ТЕПЕРЬ НА ВСЮ СТРАНИЦУ */
    .gif-container {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      width: 100%;
      padding: 0; /* Убрали отступы, чтобы гифка была в край */
      box-sizing: border-box;
      position: relative;
    }
    .page-gif {
      width: 100%;
      height: 100%;
      object-fit: cover; /* Гифка заполняет всё пространство без искажений */
      border-radius: 16px 4px 4px 16px; /* Скругляем только левую сторону */
      border: none;
      margin: 0;
    }
    .gif-caption {
      position: absolute;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0, 0, 0, 0.6);
      color: #fff;
      padding: 8px 16px;
      border-radius: 8px;
      font-family: 'Georgia', serif;
      font-size: 16px;
      font-weight: bold;
      text-align: center;
      width: 80%;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.8);
    }

    .small-text-note {
      font-style: italic;
      font-size: 13px;
      color: #777;
      margin-top: 30px;
      text-align: center;
      border-top: 1px dashed #ddd;
      padding-top: 15px;
    }
    
    /* Страница "Спасибо" */
    .thanks-page .text-box {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      text-align: center;
      padding: 40px;
    }
    .thanks-page h3 {
      border: none;
      color: #8B0000;
      font-size: 28px;
      margin-bottom: 20px;
    }
    .thanks-page p {
      font-size: 18px;
      color: #333;
      margin-bottom: 40px;
    }
    
    /* Страница-заставка "Читай внимательно" */
    .intro-page .text-box {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      text-align: center;
      padding: 40px;
    }
    .intro-page h2 {
      border: none;
      color: #8B0000;
      font-size: 38px;
      font-family: 'Georgia', serif;
      margin-bottom: 25px;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
    }
    .intro-page p {
      font-size: 20px;
      color: #555;
      font-style: italic;
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
    <div class="b-page back-cover-page" style="z-index: 1;">
      <div class="back-cover-text">Спасибо за прочтение<br>и удача в погоне за <span style="white-space: nowrap;">Чак-Чак!</span></div>
      <img src="https://4ak4ak.moy.su/logo1.jpg" class="back-cover-logo" alt="Чак-Чак">
    </div>
    
    <!-- СТРАНИЦА 5: СПАСИБО -->
    <div class="b-page paper-page thanks-page" id="p5" style="z-index: 2;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>Спасибо за прочтение!</h3>
          <p>Желаем удачи в турнире и только побед!</p>
          <button class="open-book-btn" onclick="closeBook()">Закрыть книгу 📕</button>
        </div>
      </div>
      <div class="page-side back-side">
        <button class="nav-arrow prev-arrow" onclick="turnPage(5, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 4: ПРИЗЫ -->
    <div class="b-page paper-page" id="p4" style="z-index: 3;">
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
        <button class="nav-arrow next-arrow" onclick="turnPage(4, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <button class="nav-arrow prev-arrow" onclick="turnPage(4, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 3: АНТИЧИТ -->
    <div class="b-page paper-page" id="p3" style="z-index: 4;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>🛡️ Anti-cheat и Старт</h3>
          <ul>
            <li><b>Запуск:</b> Перед запуском игры <b>обязательно</b> включите античит <u>ruzikTastyAC</u>. Включение во время игры — тех. поражение всей команде, если вы зальете такой файл на сайт. Но если вы случайно запустили, после захода в игру, вы можете выйти из игры, остановить анти-чити запустить заново, файл переливается, в моих документах он всегда один</li>
            <li><b>Коннект к серверу:</b> После согласования времени в чате появится кнопка <b>Connected</b> для автовыхода на сервер CS2.</li>
            <li><b>Залив файла анти-чита:</b> После игры найдите в «Моих документах» файл <b>match_log</b> и загрузите его через <b>желтый плюс</b> в противостоянии матча.</li>
          </ul>
        </div>
        <button class="nav-arrow next-arrow" onclick="turnPage(3, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <div class="gif-container">
          <img src="https://4ak4ak.moy.su/gif/20261026_InexpensiveBlueSquirrelNotATK-tmAsxdSkeHp.gif" class="page-gif" alt="Призы">
          <div class="gif-caption">Ценные призы ждут победителей!</div>
        </div>
        <button class="nav-arrow prev-arrow" onclick="turnPage(3, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 2: ОСНОВНЫЕ ПРАВИЛА -->
    <div class="b-page paper-page" id="p2" style="z-index: 5;">
      <div class="page-side front-side">
        <div class="text-box">
          <h3>📝 Основные правила</h3>
          <ul>
            <li><b>Верификация:</b> Обязательно привяжите Steam к сайту. Чтобы админ верифицировал ваш аккаунт и видел вас в матче, что это именно вы.</li>
            <li><b>Формат:</b> Сетка плей-офф 5х5. Турнир проходит раз в 2 недели (с пятницы по воскресенье). Регистрация открывается 1-го числа.</li>
            <li><b>Рандом:</b> Участники распределяются по командам случайно. Победители этапа снова перемешиваются в новые команды для следующей стадии.</li>
          </ul>
        </div>
        <button class="nav-arrow next-arrow" onclick="turnPage(2, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <div class="gif-container">
          <img src="https://4ak4ak.moy.su/gif/20261026_SuccessfulEagerPastaArsonNoSexy-gUbG2z5bg.gif" class="page-gif" alt="Античит">
          <div class="gif-caption">Следи за статусом античита!</div>
        </div>
        <button class="nav-arrow prev-arrow" onclick="turnPage(2, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- СТРАНИЦА 1: ЗАСТАВКА "ЧИТАЙ ВНИМАТЕЛЬНО" -->
    <div class="b-page paper-page intro-page" id="p1" style="z-index: 6;">
      <div class="page-side front-side">
        <div class="text-box">
          <h2>Читай<br>внимательно!</h2>
          <p>Здесь собраны все важные правила турнира.</p>
        </div>
        <button class="nav-arrow next-arrow" onclick="turnPage(1, 'next')">Вперед ↪</button>
      </div>
      <div class="page-side back-side">
        <div class="gif-container">
          <img src="https://4ak4ak.moy.su/gif/sdsd.gif" class="page-gif" alt="Правила">
          <div class="gif-caption">Играй честно и побеждай!</div>
        </div>
        <button class="nav-arrow prev-arrow" onclick="turnPage(1, 'prev')">↩ Назад</button>
      </div>
    </div>

    <!-- ПЕРЕДНЯЯ ОБЛОЖКА -->
    <div class="b-page front-cover-page" id="p0" style="z-index: 7;">
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
    page.style.zIndex = 100; 
    setTimeout(() => { page.classList.remove('flipped'); }, 10);
    setTimeout(() => { 
      if (pageId === 1) page.style.zIndex = 6;
      else if (pageId === 2) page.style.zIndex = 5;
      else if (pageId === 3) page.style.zIndex = 4;
      else if (pageId === 4) page.style.zIndex = 3;
      else if (pageId === 5) page.style.zIndex = 2;
    }, 800); 
  }
}

// Закрытие книги (возврат на обложку)
function closeBook() {
  [1, 2, 3, 4, 5].forEach(i => {
    const page = document.getElementById('p' + i);
    if (page) {
      page.classList.remove('flipped');
      if (i === 1) page.style.zIndex = 6;
      else if (i === 2) page.style.zIndex = 5;
      else if (i === 3) page.style.zIndex = 4;
      else if (i === 4) page.style.zIndex = 3;
      else if (i === 5) page.style.zIndex = 2;
    }
  });
  
  const p0 = document.getElementById('p0');
  setTimeout(() => {
    p0.classList.remove('flipped');
    p0.style.zIndex = 7;
  }, 100);

  document.getElementById('backToStartBtn').style.display = 'none';
}
</script>

</body>
</html>
