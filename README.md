<html>
  <head>
    <meta charset="utf-8">
    <title>Архив Администрации</title>
    <style>
      body {
        font-family: 'Courier New', Courier, monospace;
        background: #1a1a1a;
        color: #e0e0e0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        min-height: 100vh;
        margin: 0;
        padding: 20px;
      }
      .container {
        background: #2b2b2b;
        border: 2px solid #888;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 0 20px rgba(0,0,0,0.8);
        max-width: 600px;
        width: 100%;
        text-align: center;
        z-index: 10;
        position: relative;
      }
      h2 {
        margin-top: 0;
        color: #ff4d4d;
        text-transform: uppercase;
        letter-spacing: 2px;
        font-size: 18px;
      }
      .display {
        width: 100%;
        height: 40px;
        margin-bottom: 15px;
        text-align: right;
        padding: 5px;
        box-sizing: border-box;
        background: #000;
        color: #0f0;
        font-size: 20px;
        font-family: 'Courier New', monospace;
        border: 1px solid #555;
      }
      .buttons {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 8px;
      }
      .btn {
        padding: 15px;
        font-size: 18px;
        cursor: pointer;
        border: 1px solid #555;
        background: #333;
        color: #fff;
        font-family: inherit;
        font-weight: bold;
        transition: background 0.2s;
      }
      /* Стиль для заблокированных кнопок */
      .btn.disabled {
        cursor: not-allowed;
        background: #555 !important;
        opacity: 0.6;
        pointer-events: none;
      }
      .btn:active:not(.disabled) {
        background: #444;
      }
      .btn.clear { background: #a00; }
      .btn.ok { background: #2e8b57; }
      .doc-sheet {
        margin-top: 40px;
        width: 600px; 
        max-width: 90%;
        background: #fff;
        color: #000;
        border: 2px dashed #888;
        border-radius: 6px;
        opacity: 0;
        transform: translateY(20px);  
        transition: all 1s ease-in-out;
        max-height: 0;
        overflow: hidden;
        box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        padding: 30px;
        font-size: 14px;
        line-height: 1.6;
        max-height: none;      /* отключаем ограничение в процентах */
  	height: 800px;         /* фиксированная высота */
  	overflow-y: auto;
        position: relative;
        z-index: 5;
      }
      /* ИСПРАВЛЕНИЕ: Второй лист теперь лежит ПОД первым, а не смещен вправо */
      #secret-doc-2 {
        /* Убираем margin-left, чтобы не было сдвига вправо */
        margin-top: 10px;
        z-index: 4; /* Чуть ниже первого листа */
        /* Добавляем легкое смещение только по вертикали и совсем чуть-чуть по горизонтали, 
           чтобы было видно, что это другой лист, но выглядело ровно */
        transform: translateX(-10px) translateY(10px); 
      }
      .doc-sheet.visible {
        opacity: 1;
        transform: none; /* Сбрасываем начальное смещение при появлении */
        max-height: 80vh;
        padding-bottom: 50px;
      }
      .doc-sheet h3 {
        color: #d9534f;
        border-bottom: 2px solid #ccc;
        padding-bottom: 10px;
        margin-top: 0;
      }
      #message {
        margin-top: 10px;
        font-weight: bold;
        min-height: 1.5em;
      }
      .error { color: #ff4d4d; }
      .success { color: #2e8b57; }
    </style>
  </head>
  <body>
    <div class="container">
      <h2> Секретный документ Архива</h2>
      <div class="display" id="display">0</div>
      <div class="buttons">
        <button class="btn" onclick="append('7')">7</button>
        <button class="btn" onclick="append('8')">8</button>
        <button class="btn" onclick="append('9')">9</button>
        <button class="btn" onclick="append('4')">4</button>
        <button class="btn" onclick="append('5')">5</button>
        <button class="btn" onclick="append('6')">6</button>
        <button class="btn" onclick="append('1')">1</button>
        <button class="btn" onclick="append('2')">2</button>
        <button class="btn" onclick="append('3')">3</button>
        <button class="btn clear" onclick="clearDisplay()">C</button>
        <button class="btn" onclick="append('0')">0</button>
        <button class="btn ok" onclick="checkCode()">OK</button>
      </div>
      <p id="message"></p>
    </div>
    <!-- Первый лист -->
    <div id="secret-doc" class="doc-sheet">
      <h3>ДОСТУП РАЗРЕШЁН — УРОВЕНЬ ДОПУСКА: ОСОБЫЙ</h3>
      <p><strong>Объект №:</strong> SCP-3125</p>
      <p><strong>Класс объекта:</strong> Кетер</p>
      <p><strong>Статус:</strong> Активен. Требуется постоянный мониторинг.</p>
      <hr>
      <p><strong>Особые условия содержания:</strong> На SCP-3125 распространяется действие обратных протоколов сдерживания. Объект присутствует в реальности везде, кроме специально изолированных зон. Попытка осознания объекта без защиты приводит к когнитивному коллапсу.</p>
      <p><strong>Локация:</strong> Зона 41, Камера содержания инфоугроз 3125. Это единственное известное место в мире, где удалось добиться нейтрализации влияния объекта.</p>
      <p><strong>Конструкция камеры:</strong> Представляет собой кубоидную комнату размером 10 × 15 × 3 м. Стены облицованы свинцом, установлена комплексная звуко- и телепатическая изоляция.</p>
    </div>
    <!-- Второй лист (теперь ровно под первым) -->
    <div id="secret-doc-2" class="doc-sheet">
      <h3>ПРИЛОЖЕНИЕ №1: ПРОТОКОЛ ДОСТУПА</h3>
      <p><strong>Дата последнего обновления:</strong> 2024-10-25</p>
      <p><strong>Ответственный:</strong> Руководитель Отдела антимеметики (Данные засекречены)</p>
      <hr>
      <p><strong>Инструкция по входу:</strong> Доступ осуществляется через систему шлюзов в одном из концов камеры. Шлюз запрограммирован на допуск внутрь камеры не более одного человека за раз и блокируется во время его пребывания в камере.</p>
      <p><strong>График посещений:</strong> Один из руководителей Отдела антимеметики обязан посещать SCP-3125 каждые шесть недель (42 дня) для верификации стабильности барьеров.</p>
      <p><strong>Меры предосторожности:</strong> Запрещено использование любых устройств записи, фото- и видеотехники в радиусе 50 метров от шлюза. Все сотрудники должны проходить процедуру ментальной калибровки перед входом.</p>
      <p><strong>Аварийные процедуры:</strong> В случае потери связи с сотрудником внутри камеры, шлюз автоматически герметизируется. Попытки принудительного открытия без кода аварийной разблокировки (неизвестен) приведут к полной разгерметизации зоны.</p>
      <p style="font-size: 12px; color: #666; margin-top: 30px; border-top: 1px solid #eee; padding-top: 10px;">
        Документ классифицирован. Не подлежит распространению. Любое копирование или передача третьим лицам карается по законам Фонда.
      </p>
    </div>
    <script>
      const display = document.getElementById('display');
      const message = document.getElementById('message');
      const doc1 = document.getElementById('secret-doc');
      const doc2 = document.getElementById('secret-doc-2');
      const buttons = document.querySelectorAll('.btn');
      function append(value) {
        if (display.innerText === '0') display.innerText = value;
        else display.innerText += value;
      }
      function clearDisplay() {
        // Сброс возможен только если документы еще не открыты
        if (!doc1.classList.contains('visible')) {
            display.innerText = '0';
            message.innerText = '';
            message.className = '';
        }
      }
      function blockInput() {
        display.style.opacity = '0.5';
        display.style.pointerEvents = 'none';
        buttons.forEach(btn => {
            btn.classList.add('disabled');
        });
      }
      function checkCode() {
        const code = display.innerText;
        if (code === '5631') {
          message.innerText = 'Доступ разрешён. Документы загружаются…';
          message.className = 'success';
          // Блокируем ввод сразу
          blockInput();
          // Показываем первый лист
          setTimeout(() => {
            doc1.classList.add('visible');
            doc1.scrollTop = 0;
          }, 800);
          // Показываем второй лист с задержкой (эффект стопки)
          setTimeout(() => {
            doc2.classList.add('visible');
            doc2.scrollTop = 0;
          }, 1200);
        } else {
          message.innerText = 'Неверный код. Доступ запрещён.';
          message.className = 'error';
          display.style.transform = 'translateX(-5px)';
          setTimeout(() => {
            display.style.transform = 'translateX(0)';
          }, 100);
        }
      }
    </script>
  </body>
</html>
