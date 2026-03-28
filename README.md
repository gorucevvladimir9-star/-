<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Super Clicker</title>
    <style>
        body {
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background: linear-gradient(135deg, #1e1e2f, #2a2a40);
            color: white;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            user-select: none;
        }

        #score-container {
            font-size: 3rem;
            margin-bottom: 20px;
            font-weight: bold;
            text-shadow: 0 0 10px rgba(0, 255, 255, 0.5);
        }

        #clicker-btn {
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, #00d2ff, #3a7bd5);
            border-radius: 50%;
            border: 8px solid white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            cursor: pointer;
            transition: transform 0.1s active;
            outline: none;
        }

        #clicker-btn:active {
            transform: scale(0.9);
        }

        .stats {
            margin-top: 30px;
            font-size: 1.2rem;
            opacity: 0.8;
        }
    </style>
</head>
<body>

    <div id="score-container">0</div>
    <button id="clicker-btn"></button>
    <div class="stats">Кликов в секунду: <span id="cps">0</span></div>

    <script>
        let score = 0;
        let clicksThisSecond = 0;
        const scoreDisplay = document.getElementById('score-container');
        const btn = document.getElementById('clicker-btn');
        const cpsDisplay = document.getElementById('cps');

        // Обработка клика
        btn.addEventListener('pointerdown', (e) => {
            score++;
            clicksThisSecond++;
            scoreDisplay.innerText = score;
            
            // Вибрация (если поддерживается устройством)
            if (navigator.vibrate) navigator.vibrate(50);
        });

        // Сброс счетчика кликов в секунду
        setInterval(() => {
            cpsDisplay.innerText = clicksThisSecond;
            clicksThisSecond = 0;
        }, 1000);
    </script>
</body>
</html>

