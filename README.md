<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Will You Be My Valentine?</title>

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">

  <style>
    body {
      margin: 0;
      padding: 0;
      height: 100vh;
      background: linear-gradient(135deg, #ffdde1, #ee9ca7);
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Pacifico', cursive;
      overflow: hidden;
    }

    .container {
      text-align: center;
      z-index: 2;
    }

    h1 {
      font-size: 3rem;
      color: #b30059;
      margin-bottom: 40px;
    }

    .buttons {
      position: relative;
      height: 200px;
    }

    #yes {
      font-size: 1.8rem;
      padding: 15px 40px;
      border: none;
      border-radius: 40px;
      background-color: #ff4d88;
      color: white;
      cursor: pointer;
      box-shadow: 0 10px 20px rgba(0,0,0,0.2);
      transition: transform 0.2s;
    }

    #yes:hover {
      transform: scale(1.1);
    }

    #no {
      position: absolute;
      font-size: 0.6rem;
      padding: 5px 10px;
      border: none;
      border-radius: 20px;
      background-color: #f2f2f2;
      color: #777;
      cursor: pointer;
    }

    /* Floating Hearts */
    .heart {
      position: absolute;
      bottom: -20px;
      font-size: 20px;
      animation: floatUp 6s linear infinite;
      opacity: 0.7;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 0.7;
      }
      100% {
        transform: translateY(-110vh) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <audio id="bg-music" loop>
  <source src="giveon-stuck-on-you.mp3" type="audio/mpeg">
</audio>


  <div class="container">
    <h1>Sandra, will you be my Valentine? 💖</h1>

    <div class="buttons">
      <button id="yes">YES 💕</button>
      <button id="no">no</button>
    </div>
  </div>

  <script>
    const noBtn = document.getElementById("no");
    const music = document.getElementById("bg-music");

    // Play music on first interaction
    document.body.addEventListener("click", () => {
      music.play();
    }, { once: true });

    noBtn.addEventListener("mouseover", () => {
      const x = Math.random() * 300;
      const y = Math.random() * 150;

      noBtn.style.left = x + "px";
      noBtn.style.top = y + "px";
    });

    document.getElementById("yes").addEventListener("click", () => {
      document.body.innerHTML = `
        <div style="
          display:flex;
          justify-content:center;
          align-items:center;
          height:100vh;
          background:linear-gradient(135deg,#ff9a9e,#fad0c4);
          font-family:'Pacifico', cursive;
          color:#b30059;
          text-align:center;
        ">
          <h1>Yaaay! 💖💍<br>You just made me the happiest person alive 😍</h1>
        </div>
      `;
    });

    // Create floating hearts
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.innerHTML = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (4 + Math.random() * 3) + "s";
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 7000);
    }

    setInterval(createHeart, 500);
  </script>

</body>
</html>
