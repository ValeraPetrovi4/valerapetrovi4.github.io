<hmtl>
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
        margin-left: 35px;
        width: 600px; 
        max-width: 90%;
        background: #fff;
        color: #000;
        border: 2px dashed #888;
        border-radius: 6px;
        opacity: 0;
        transform: translateY(20px) translateX(20px);  
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
        margin-left: 23px;
        z-index: 4; /* Чуть ниже первого листа */
        /* Добавляем легкое смещение только по вертикали и совсем чуть-чуть по горизонтали, 
           чтобы было видно, что это другой лист, но выглядело ровно */
        transform: translateX(10px) translateY(10px); 
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
      <h2>    Секретный документ Архива</h2>
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
      <h3>ДОСТУП РАЗРЕШЁН — УРОВЕНЬ ДОПУСКА: 4+</h3>
      <p><strong>SCP №:</strong> 5631-Ω</p>
      <p><strong>Класс Объекта:</strong> Нейтрализован</p>
      <p><strong>Особые Условия Содержания:</strong></p>
      <p>Отсутствуют.</p>
      <p><strong>Описание:</strong></p>
      <p>SCP-5631-Ω - обозначение альтернативного измерения, далее именованное как "Ад" Др. Сизифом.</p>
      <p>"Ад" представляет собой пустое пространство, т.е. не имеющее никакой физической материи и гравитации, однако наполнен "Воздухом" - смесью кислорода и SCP-5631-Ω-2. Внешний наблюдатель (человек, видеоаппаратура и прочее) фиксирует красный оттенок "неба" измерения.</p>
      <p>SCP-5631-Ω-2 - ранее неизвестный тип белкового соединения. Способен вступать в реакцию с органикой нашего измерения, поддавая тех различным мутациям.</p>
    </div>
    <!-- Второй лист (теперь ровно под первым) -->
    <div id="secret-doc-2" class="doc-sheet">
    </div> 
    <div id="secret-doc-3" class="doc-sheet">
      <p></p>
      <p></p>
      <hr>
      <p></p>
      <p></p>
      <p></p>
      <p></p>
      <p style="font-size: 11px; color: #666; margin-top: 20px; border-top: 1px solid #eee; padding-top: 10px;">
        Документ разрешен лицам допуска 4+ и выше. В связи с раскрытием Фонда, данный документ обязан надежно хранится, пока амнезирование населения не завершится.
      </p>
    </div>
    <script>
      const display = document.getElementById('display');
      const message = document.getElementById('message');
      const doc1 = document.getElementById('secret-doc');
      const doc2 = document.getElementById('secret-doc-2');
      const doc3 = document.getElementById('secret-doc-3');
      const buttons = document.querySelectorAll('.btn');
      const audio = new Audio('ambient.mp3');
      audio.loop = false;
      audio.volume = 0.2;
      let currentSegment = 0; // 0 — первый проход (0–75), 1 — второй и далее (5–75)
      const startTimes = [0, 5];
      const endTime = 150;
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
      function playSegment() {
        const start = startTimes[currentSegment];
        audio.currentTime = start;
        audio.play().catch(e => console.log('Play error:', e));
        setTimeout(() => {
          audio.pause();
          audio.currentTime = 0;
    // Переключаем сегмент: после первого (0) идём на второй (5), дальше всегда 5
        currentSegment = currentSegment === 0 ? 1 : 1;
        playSegment(); // запускаем следующий проход
    }, (endTime - start) * 1000);
   }
      function checkCode() {
        const code = display.innerText;
        if (code === '5631') {
          message.innerText = 'Доступ разрешён. Документы загружаются…';
          message.className = 'success';
          // Блокируем ввод сразу
          blockInput();
          playSegment();
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
          setTimeout(() => {
            doc3.classList.add('visible');
            doc3.scrollTop = 0;
          }, 1600);
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
