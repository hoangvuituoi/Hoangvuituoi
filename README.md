<!DOCTYPE html>
<html>
<head>
  <title>Phần thưởng bí mật</title>
  <style>
    body {
      background-color: black;
      color: white;
      text-align: center;
      font-family: 'Arial', sans-serif;
      padding-top: 100px;
      transition: background-color 0.2s;
    }
    #counter {
      font-size: 24px;
      margin-top: 20px;
    }
    #btn {
      padding: 20px 40px;
      font-size: 20px;
      background-color: crimson;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    #ghost {
      display: none;
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 9999;
    }
  </style>
</head>
<body>
  <h1>🎁 Nhấn 100 lần để nhận phần thưởng bí mật!</h1>
  <button id="btn" onclick="clickMe()">Nhấn vào đây!</button>
  <div id="counter">Đã nhấn: 0 / 100</div>

  <!-- Ảnh ma -->
  <img id="ghost" src="https://i.imgur.com/CtNkWHi.jpg" />

  <!-- Âm thanh -->
  <audio id="scream" src="https://www.soundjay.com/human/sounds/scream-01.mp3"></audio>

  <script>
    let count = 0;
    const btn = document.getElementById("btn");
    const counter = document.getElementById("counter");
    const ghost = document.getElementById("ghost");
    const scream = document.getElementById("scream");

    function clickMe() {
      count++;
      if (count < 100) {
        counter.innerText = `Đã nhấn: ${count} / 100`;
        if (count === 99) {
          counter.innerText = `Sắp tới rồi... chuẩn bị tinh thần 😳`;
        }
      } else {
        // Hù ma
        ghost.style.display = "block";
        scream.play();
        btn.style.display = "none";
        counter.style.display = "none";

        // Nền nháy
        let flashes = 0;
        const interval = setInterval(() => {
          document.body.style.backgroundColor = flashes % 2 === 0 ? "darkred" : "black";
          flashes++;
          if (flashes > 10) clearInterval(interval);
        }, 150);
      }
    }
  </script>
</body>
</html>
