# for-you
surat cinta dariku xixii
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untukmu ❤️</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            background-color: #0f172a;
            font-family: sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            color: #fff;
        }
        .background-decor { position: absolute; width: 100%; height: 100%; pointer-events: none; z-index: 1; overflow: hidden; }
        .falling-object {
            position: absolute; top: -10%; font-size: 1.5rem; color: #ff7eb3; opacity: 0.8; animation: fall linear infinite;
        }
        @keyframes fall { 0% { transform: translateY(-10%) rotate(0deg); } 100% { transform: translateY(110vh) rotate(360deg); } }
        .envelope-wrapper { position: relative; z-index: 10; cursor: pointer; transition: transform 0.3s ease; }
        .envelope-wrapper:hover { transform: scale(1.05); }
        .main-button {
            background: linear-gradient(135deg, #ff758c 0%, #ff7eb3 100%);
            padding: 20px 40px; border-radius: 50px;
            font-size: 1.2rem; font-weight: bold;
            border: none; color: white;
            box-shadow: 0 10px 25px rgba(255, 117, 140, 0.4);
            cursor: pointer; display: flex; align-items: center; gap: 10px;
        }
        .letter-box {
            position: fixed; top: 50%; left: 50%;
            transform: translate(-50%, -50%) scale(0);
            width: 90%; max-width: 450px;
            background: #ffffff; color: #333;
            padding: 30px; border-radius: 20px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
            z-index: 100;
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-align: center;
        }
        .letter-box.active { transform: translate(-50%, -50%) scale(1); }
        .letter-content { font-size: 1.1rem; line-height: 1.6; margin-bottom: 20px; color: #4a5568; }
        .letter-content b { color: #e11d48; }
        .heart-icon { color: #e11d48; font-size: 2rem; margin-bottom: 15px; animation: pulse 1.5s infinite; }
        .close-btn { background-color: #f3f4f6; border: none; padding: 10px 20px; border-radius: 25px; color: #6b7280; cursor: pointer; font-weight: 600; }
        .close-btn:hover { background-color: #e5e7eb; color: #1f2937; }
        .overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); opacity: 0; pointer-events: none; z-index: 50; transition: opacity 0.4s; }
        .overlay.active { opacity: 1; pointer-events: auto; }
        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.15); } 100% { transform: scale(1); } }
    </style>
</head>
<body>
    <div class="background-decor" id="bgDecor"></div>
    <div class="envelope-wrapper" id="btnOpen">
        <button class="main-button"><span>Pencet Ini Ada Pesan Buat Kamu</span> ❤️</button>
    </div>
    <div class="overlay" id="overlay"></div>
    <div class="letter-box" id="letterBox">
        <div class="heart-icon">❤️</div>
        <div class="letter-content">
            <p><b>mencintaimu adalah</b> pilihanku.</p>
            <p>Senang, sedih adalah resikoku karena aku telah <b>memilihmu</b>,</p>
            <p>takkan menyesal, tuk tetap <b>mencintaimu</b>. 💕</p>
            <br>
            <p style="font-size: 0.95rem; font-style: italic; color: #9ca3af;">"Aku ingin mencintaimu lebih banyak dari debar, lebih besar dari sabar, lebih lama dari selamanya."</p>
        </div>
        <button class="close-btn" id="btnClose">Tutup Surat</button>
    </div>
    <script>
        const btnOpen = document.getElementById('btnOpen');
        const btnClose = document.getElementById('btnClose');
        const letterBox = document.getElementById('letterBox');
        const overlay = document.getElementById('overlay');
        const bgDecor = document.getElementById('bgDecor');

        btnOpen.addEventListener('click', () => {
            letterBox.classList.add('active');
            overlay.classList.add('active');
            btnOpen.style.display = 'none';
        });

        btnClose.addEventListener('click', () => {
            letterBox.classList.remove('active');
            overlay.classList.remove('active');
            setTimeout(() => { btnOpen.style.display = 'block'; }, 300);
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('falling-object');
            heart.innerText = Math.random() > 0.3 ? '❤️' : '🌸';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 5 + 3 + 's';
            heart.style.opacity = Math.random() * 0.5 + 0.3;
            bgDecor.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 8000);
        }

        setInterval(createHeart, 400);
    </script>
</body>
</html>
