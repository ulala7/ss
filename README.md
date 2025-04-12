<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Ucapan apa yaa</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap');

    body {
      font-family: 'Fredoka One', cursive;
      text-align: center;
      background: linear-gradient(135deg, rgb(255, 200, 221), rgb(181, 255, 252));
      padding: 50px;
      overflow: hidden;
      position: relative;
    }

    h1 {
      color: #ff1493;
      font-size: 3em;
      animation: bounce 2s infinite;
    }

    p {
      color: rgb(0, 0, 255);
      font-size: 1.2em;
    }

    button {
      padding: 10px 20px;
      font-size: 1.1em;
      background-color: rgb(255, 105, 180);
      border: none;
      border-radius: 10px;
      cursor: pointer;
      color: white;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      transition: transform 0.2s;
    }

    button:hover {
      transform: scale(1.1);
    }

    #monkey, #fun-video {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      object-fit: cover;
      z-index: 999;
      animation: fadeInZoom 1s ease-out;
    }

    .show {
      display: block !important;
    }

    @keyframes fadeInZoom {
      0% { transform: scale(0.8); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      background-color: rgb(255, 105, 180);
      top: -10px;
      animation: fall 5s linear infinite;
      opacity: 0.8;
      z-index: 0;
    }

    @keyframes fall {
      0% { transform: translateY(-10px) rotate(0deg); }
      100% { transform: translateY(110vh) rotate(360deg); }
    }
  </style>
</head>
<body>

  <h1>Halloo! 😄</h1>
  <button onclick="showMonkey()">Klik Aku!</button>
  <p>Tolong yaa klik tombolnyaa, biar kejutan jatuh dari langit 🤭</p>

  <!-- Gambar monkey -->
  <img id="monkey" src="https://statik.tempo.co/data/2017/09/12/id_641136/641136_650.jpg" alt="Monkey Meme">

  <!-- Video meme katak ketawa -->
  <video id="fun-video" src="https://media.tenor.com/O7xNFrGxKs8AAAPo/frog-funny.mp4" autoplay muted loop></video>

  <!-- Suara saat buka halaman -->
  <audio id="open-sound" src="https://www.myinstants.com/media/sounds/anime-wow-sound-effect.mp3"></audio>

  <!-- Suara ketawa saat klik -->
  <audio id="laugh-sound" src="https://www.myinstants.com/media/sounds/trollololololololol.mp3"></audio>

  <script>
    // Mainkan sound saat halaman dibuka
    window.onload = function() {
      const openSound = document.getElementById('open-sound');
      openSound.play().catch(err => {
        console.log("Autoplay diblokir, perlu klik interaksi pengguna.");
      });
    }

    function showMonkey() {
      const img = document.getElementById('monkey');
      const vid = document.getElementById('fun-video');
      const openSound = document.getElementById('open-sound');
      const laughSound = document.getElementById('laugh-sound');

      img.classList.add('show');
      vid.classList.add('show');
      laughSound.play();
      openSound.play();
    }

    // Confetti animation
    for (let i = 0; i < 40; i++) {
      const confetti = document.createElement('div');
      confetti.classList.add('confetti');
      confetti.style.left = Math.random() * 100 + 'vw';
      confetti.style.backgroundColor = getRandomColor();
      confetti.style.animationDuration = (Math.random() * 3 + 3) + 's';
      document.body.appendChild(confetti);
    }

    function getRandomColor() {
      const colors = ['rgb(255, 105, 180)', 'rgb(252, 225, 138)', 'rgb(0, 210, 255)', 'rgb(180, 142, 255)', 'rgb(160, 231, 229)'];
      return colors[Math.floor(Math.random() * colors.length)];
    }
  </script>

</body>
</html>
