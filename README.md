<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Валентинка ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        /* Основні налаштування сторінки */
        body { 
            height: 100vh; 
            display: flex; 
            flex-direction: column; 
            justify-content: center; 
            align-items: center; 
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%); 
            font-family: 'Montserrat', sans-serif; 
            overflow: hidden; 
            text-align: center; 
            margin: 0; 
            padding: 20px; 
        }

        /* Контейнер (біла картка) */
        .container { 
            background: rgba(255, 255, 255, 0.95); 
            padding: 40px 20px; 
            border-radius: 20px; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.1); 
            max-width: 90%; 
            width: 350px; 
        }

        /* Заголовок */
        h1 { 
            font-family: 'Pacifico', cursive; 
            color: #ff4d6d; 
            font-size: 1.8rem; 
            margin-bottom: 30px; 
            line-height: 1.4; 
        }

        /* Кнопка */
        .buttons { 
            display: flex; 
            justify-content: center; 
            margin-top: 10px; 
        }

        button { 
            padding: 15px 50px; 
            font-size: 1.3rem; 
            border: none; 
            border-radius: 50px; 
            cursor: pointer; 
            transition: 0.3s; 
            font-weight: bold; 
            background: #ff4d6d; 
            color: white; 
            box-shadow: 0 4px 15px rgba(255, 77, 109, 0.4); 
        }

        button:active { 
            transform: scale(0.95); 
        }

        /* Повідомлення про успіх */
        #successMessage { 
            display: none; 
            margin-top: 20px; 
        }
        
        #successMessage img { 
            width: 100%; 
            border-radius: 15px; 
            margin-top: 15px; 
        }

        /* Летючі серця на фоні */
        .heart-bg { 
            position: absolute; 
            color: rgba(255,255,255,0.6); 
            animation: float 6s linear infinite; 
            z-index: -1; 
        }

        @keyframes float { 
            0% { transform: translateY(100vh) scale(0); opacity: 0; } 
            50% { opacity: 1; } 
            100% { transform: translateY(-10vh) scale(1); opacity: 0; } 
        }
    </style>
</head>
<body>

    <div class="container">
        <h1 id="mainText">Чи будеш ти моєю коханою Валентинкою на все життя?</h1>
        
        <div class="buttons">
            <button id="yesBtn">Так ❤️</button>
        </div>
        
        <div id="successMessage">
            <h2>Я тебе кохаю! ❤️</h2>
            <p>Ти — моє щастя!</p>
            <img src="https://media.tenor.com/gUiu1zyxfzYAAAAj/bear-kiss-bear-kisses.gif" alt="Love">
        </div>
    </div>

    <script>
        const yes = document.getElementById('yesBtn');
        const main = document.getElementById('mainText');
        const btns = document.querySelector('.buttons');
        const msg = document.getElementById('successMessage');

        yes.addEventListener('click', () => { 
            // Запуск конфеті
            confetti({
                particleCount: 150, 
                spread: 70, 
                origin: { y: 0.6 },
                colors: ['#ff4d6d', '#ff9a9e', '#ffffff']
            });
            
            // Приховуємо питання, показуємо відповідь
            btns.style.display = 'none'; 
            main.style.display = 'none'; 
            msg.style.display = 'block'; 
        });

        // Створення сердечок на фоні
        setInterval(() => { 
            const h = document.createElement('div'); 
            h.className = 'heart-bg'; 
            h.innerHTML = '❤️'; 
            h.style.left = Math.random() * 100 + 'vw'; 
            h.style.fontSize = Math.random() * 20 + 20 + 'px'; 
            document.body.appendChild(h); 
            setTimeout(() => h.remove(), 6000); 
        }, 300);
    </script>

</body>
</html>
