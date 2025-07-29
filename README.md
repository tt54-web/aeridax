<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Aerida</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body, html {
      height: 100%;
      font-family: 'Orbitron', sans-serif;
      background: #000;
      overflow: hidden;
    }

    /* Видео фон */
    .bg-video {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 56.25vw; /* 16:9 */
      object-fit: cover;
      z-index: -2;
    }

    /* Анимация загрузки */
    .overlay {
      position: fixed;
      width: 100%;
      height: 100%;
      background: black;
      animation: fadeOut 1.5s ease forwards;
      z-index: 10;
    }
    @keyframes fadeOut {
      to { opacity: 0; visibility: hidden; }
    }

    .content {
      position: relative;
      text-align: center;
      color: white;
      padding-top: 20vh;
      z-index: 2;
    }

    .avatar {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      border: 3px solid #ff69b4;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .avatar:hover {
      transform: scale(1.1);
      box-shadow: 0 0 20px #ff69b4;
    }

    .name {
      font-size: 3rem;
      color: white;
      margin-top: 15px;
      text-shadow: 0 0 10px #ff69b4;
      transition: color 0.3s, text-shadow 0.3s;
    }
    .name:hover {
      color: #ffb6c1;
      text-shadow: 0 0 25px #ff69b4;
    }

    .cards {
      display: flex;
      justify-content: center;
      margin: 40px 0;
      gap: 20px;
      flex-wrap: wrap;
    }
    .card {
      background: rgba(255, 105, 180, 0.2);
      border: 2px solid #ff69b4;
      border-radius: 20px;
      padding: 20px 30px;
      font-size: 1.2rem;
      color: white;
      backdrop-filter: blur(10px);
      box-shadow: 0 0 10px #ff69b4;
      transition: transform 0.3s;
    }
    .card:hover {
      transform: scale(1.05);
    }

    .socials {
      margin-top: 30px;
    }
    .icon {
      font-size: 2rem;
      color: white;
      margin: 0 15px;
      transition: color 0.3s, transform 0.3s;
    }
    .icon:hover {
      color: #ff69b4;
      transform: scale(1.2);
    }

    .views {
      position: fixed;
      bottom: 10px;
      left: 10px;
      color: #ffb6c1;
      font-size: 14px;
    }

    /* Цветочки */
    .flowers {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1;
    }
    .flower {
      position: absolute;
      width: 15px;
      height: 15px;
      background: pink;
      border-radius: 50%;
      opacity: 0.8;
      box-shadow: 0 0 10px #ff69b4;
      animation: fall linear forwards;
    }
    @keyframes fall {
      to {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>

  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"/>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
</head>
<body>

  <!-- Видео фон -->
  <video autoplay muted loop class="bg-video">
    <source src="video.mp4" type="video/mp4" />
  </video>

  <!-- Анимация появления -->
  <div class="overlay"></div>

  <!-- Контент -->
  <div class="content">
    <img src="avatar.jpg" alt="Avatar" class="avatar" />
    <h1 class="name">AERIDA</h1>

    <div class="cards">
      <div class="card">KASPI:4400430190264652</div>
      <div class="card">SCP GIRLS</div>
    </div>

    <div class="socials">
      <a href="https://www.tiktok.com/@aeridawtf?_t=ZM-8yQzz6j0TW2&_r=1" class="icon"><i class="fab fa-tiktok"></i></a>
      <a href="https://vk.com/aeridaaa" class="icon"><i class="fab fa-vk"></i></a>
      <a href="https://wa.me/+7 705 329 2417" class="icon"><i class="fab fa-whatsapp"></i></a>
    </div>

    <div class="views">👁 Просмотров: <span id="counter">0</span></div>
  </div>

  <!-- Падающие цветочки -->
  <div class="flowers" id="flowers-container"></div>
<audio id="bg-music" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio>

<button onclick="document.getElementById('bg-music').play()">Включить музыку</button>

  <!-- JavaScript -->
  <script>
    // Счётчик просмотров
    let counter = sessionStorage.getItem("views") || 0;
    counter++;
    document.getElementById("counter").innerText = counter;
    sessionStorage.setItem("views", counter);

    // Падающие цветочки
    function createFlower() {
      const flower = document.createElement("div");
      flower.className = "flower";
      flower.style.left = Math.random() * 100 + "vw";
      flower.style.animationDuration = 3 + Math.random() * 5 + "s";
      flower.style.backgroundColor = "#ff69b4";
      flower.style.width = flower.style.height = Math.random() * 10 + 10 + "px";
      document.getElementById("flowers-container").appendChild(flower);
      setTimeout(() => flower.remove(), 8000);
    }
    setInterval(createFlower, 300);
    
    
  </script>
</body>
</html>
