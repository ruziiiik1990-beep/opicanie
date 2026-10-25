<!-- Контейнер для 3D пространства сцены (без фонов) -->
<div class="book-scene">
  <div class="book-container">
    
    <!-- ЗАДНЯЯ ОБЛОЖКА -->
    <div class="book-page back-cover"></div>
    
    <!-- СТРАНИЦА 3: ИГРОВОЙ ПРОЦЕСС И ПРИЗЫ -->
    <div class="book-page inner-page-2">
      <div class="page-content">
        <h3>🏆 Призы и Рейтинг</h3>
        <ul>
          <li><b>Финал матча:</b> Победители получают скины лучшего качества, проигравшие в финале — скины послабее. Призы отображаются прямо в меню противостояния.</li>
          <li><b>Выдача скинов:</b> Админ добавляет вас в друзья в Steam, заносит в блокнот и передает скины сразу, как спадет временная блокировка обмена Steam (требуется терпение).</li>
          <li><b>Рейтинг «Чак-Чак»:</b> За победу в турнире начисляется <b>2 чак-чака</b>, за участие в финале (2 место) — <b>1 чак-чак</b>.</li>
        </ul>
        <p class="crypto-note">Турнир создан ради эмоций и символических призов! Наслаждайтесь игрой!</p>
      </div>
    </div>

    <!-- СТРАНИЦА 2: АНТИЧИТ И ПОДКЛЮЧЕНИЕ -->
    <div class="book-page inner-page-1">
      <div class="page-content">
        <h3>🛡️ Античит и Старт</h3>
        <ul>
          <li><b>Запуск:</b> Перед запуском игры <b>обязательно</b> включите античит <u>ruzikTastyAC</u>. Включение во время или в конце игры — тех. поражение всей команде.</li>
          <li><b>Коннект к серверу:</b> После согласования времени в чате, Админ запускает матч. На странице противостояния загорится кнопка <b>Connected</b> для автовыхода на сервер.</li>
          <li><b>Логи матча:</b> После игры закройте античит, найдите в «Моих документах» файл <b>match_log</b> и загрузите его на сайт через <b>желтый плюс</b> в чате матча.</li>
        </ul>
      </div>
    </div>

    <!-- СТРАНИЦА 1: ОБЩИЕ ПРАВИЛА И СТИМ -->
    <div class="book-page inner-page-main">
      <div class="page-content">
        <h3>📝 Основные правила</h3>
        <ul>
          <li><b>Верификация:</b> Обязательно привяжите Steam к сайту. Скопируйте проверочный код в поле «О себе» в Steam, чтобы админ верифицировал ваш аккаунт для захода на сервер CS2. Сайт не собирает ваши личные данные!</li>
          <li><b>Формат:</b> Сетка плей-офф 5х5. Турнир проходит раз в 2 недели (с пятницы по воскресенье). Регистрация открывается 1-го числа месяца.</li>
          <li><b>Рандом:</b> Участники распределяются по командам случайно (играть с друзьями не получится). Победители этапа снова перемешиваются в новые команды для следующей стадии.</li>
        </ul>
      </div>
    </div>

    <!-- ПЕРЕДНЯЯ ОБЛОЖКА -->
    <div class="book-page front-cover">
      <div class="cover-title">
        <h2>РУКОВОДСТВО</h2>
        <div class="badge">ЧАК-ЧАК</div>
        <p>Официальные правила турниров CS2</p>
        <span class="action-hint">Наведи, чтобы открыть 📖</span>
      </div>
    </div>

  </div>
</div>

<!-- СТИЛИ С ИСПРАВЛЕННЫМ 3D И БЕЗ БЕЛОГО ФОНА -->
<style>
.book-scene {
  perspective: 1500px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 60px 0;
  background: transparent !important; /* Убираем любые внешние фоны */
}

.book-container {
  position: relative;
  width: 350px;
  height: 500px;
  transition: transform 0.8s ease-in-out;
  transform-style: preserve-3d;
  transform: rotateX(15deg) rotateY(-10deg);
}

.book-scene:hover .book-container {
  transform: rotateX(10deg) rotateY(-25deg) translateX(40px);
}

.book-page {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  border-radius: 4px 12px 12px 4px;
  transform-origin: left center;
  transition: transform 0.8s cubic-bezier(0.25, 1, 0.5, 1), box-shadow 0.8s;
  transform-style: preserve-3d; /* Фикс для корректного разделения слоев в 3D */
  box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

/* Передняя обложка */
.front-cover {
  background: linear-gradient(135deg, #8B0000 0%, #4A0000 100%);
  border-left: 8px solid #2A0000;
  color: #D4AF37;
  z-index: 5;
  transform: rotateY(0deg);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  border: 2px solid #5A0000;
  backface-visibility: hidden; /* Прячет обложку сзади, когда она открыта */
}

.cover-title h2 {
  font-family: 'Georgia', serif;
  font-size: 28px;
  letter-spacing: 4px;
  margin: 0;
}

.cover-title .badge {
  background: #D4AF37;
  color: #4A0000;
  padding: 5px 15px;
  font-weight: bold;
  font-size: 14px;
  margin: 15px 0;
  border-radius: 4px;
  letter-spacing: 2px;
}

.cover-title p {
  font-size: 12px;
  color: #f0e6d2;
  font-style: italic;
}

.action-hint {
  display: block;
  margin-top: 50px;
  font-size: 11px;
  color: #D4AF37;
  animation: pulse 1.5s infinite;
}

/* Задняя обложка */
.back-cover {
  background: #4A0000;
  z-index: 1;
  transform: rotateY(0deg);
}

/* Бумажные страницы внутри */
.inner-page-main, .inner-page-1, .inner-page-2 {
  background: #fcf8f2;
  color: #2b2b2b;
  box-shadow: inset 30px 0 30px rgba(0,0,0,0.05), 0 4px 10px rgba(0,0,0,0.1);
  border: 1px solid #e8dec9;
}

.inner-page-main { z-index: 4; }
.inner-page-1 { z-index: 3; }
.inner-page-2 { z-index: 2; }

.page-content {
  padding: 30px 25px 30px 40px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 13px;
  line-height: 1.5;
}

.page-content h3 {
  font-family: 'Georgia', serif;
  color: #8B0000;
  border-bottom: 1px solid #e8dec9;
  padding-bottom: 8px;
  margin-top: 0;
  font-size: 18px;
}

.page-content ul {
  padding-left: 15px;
  margin: 0;
}

.page-content li {
  margin-bottom: 10px;
}

.crypto-note {
  font-style: italic;
  font-size: 11px;
  color: #666;
  margin-top: 20px;
  text-align: center;
  border-top: 1px dashed #ccc;
  padding-top: 10px;
}

/* ТРАЕКТОРИЯ РАЗВОРОТА СТРАНИЦ ВЕЕРОМ */
.book-scene:hover .front-cover {
  transform: rotateY(-145deg);
  z-index: 1;
}

.book-scene:hover .inner-page-main {
  transform: rotateY(-130deg);
  z-index: 2;
}

.book-scene:hover .inner-page-1 {
  transform: rotateY(-15deg);
  z-index: 3;
}

.book-scene:hover .inner-page-2 {
  transform: rotateY(-5deg);
  z-index: 4;
}

@keyframes pulse {
  0% { opacity: 0.5; }
  50% { opacity: 1; }
  100% { opacity: 0.5; }
}
</style>
