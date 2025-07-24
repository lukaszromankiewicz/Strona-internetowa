<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <title>Rowerowa Strona Życia</title>
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      padding: 20px;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #c2e9fb, #a1c4fd);
      display: flex;
      justify-content: center;
      gap: 30px;
      height: 100vh;
      align-items: center;
    }
    .page, .subpage {
      width: 400px;
      background: white;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      text-align: center;
      display: flex;
      flex-direction: column;
      gap: 25px;
    }
    h1 {
      color: #333;
      margin: 0;
      font-size: 24px;
    }
    .clock {
      font-size: 32px;
      font-weight: bold;
      color: #555;
      margin-bottom: 20px;
      font-family: monospace;
    }
    .commands {
      display: flex;
      flex-direction: column;
      gap: 15px;
    }
    .command-button {
      padding: 12px 24px;
      font-size: 16px;
      border: none;
      border-radius: 12px;
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    .command-button:hover {
      background-color: #45a049;
    }
    /* Początkowo ukrywamy podstrony */
    .subpage {
      display: none;
    }
    a {
      color: #4CAF50;
      text-decoration: none;
      font-weight: bold;
    }
    a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>

  <!-- Strona 1 -->
  <div class="page" id="page1">
    <h1>Witaj w świecie kolarstwa!</h1>
    <div class="clock" id="clock1">00:00:00</div>
    <div class="commands">
      <button class="command-button" onclick="start1()">Start</button>
      <button class="command-button" onclick="save1()">Zapisz</button>
      <button class="command-button" onclick="settings1()">Ustawienia</button>
      <button class="command-button" onclick="exit1()">Wyjdź</button>
    </div>
  </div>

  <!-- Strona 2 -->
  <div class="page" id="page2">
    <h1>Witaj serdecznie</h1>
    <div class="clock" id="clock2">00:00:00</div>
    <div class="commands">
      <button class="command-button" onclick="start2()">Zacznij</button>
      <button class="command-button" onclick="save2()">Dane</button>
      <button class="command-button" onclick="settings2()">Użytkownik</button>
      <button class="command-button" onclick="exit2()">Google</button>
    </div>
  </div>

  <!-- Podstrona 1 -->
  <div class="subpage" id="subpage1">
    <h1>Tu jest strona o kolarstwie! 🚲</h1>
    <p>Odwiedź moją stronę: <a href="kolarstwo.html" target="_blank" rel="noopener noreferrer">Kolarstwo</a></p>
    <button class="command-button" onclick="backToMain()">Powrót</button>
  </div>

  <!-- Podstrona 2 -->
  <div class="subpage" id="subpage2">
    <h1>Tu jest strona o kolarstwie! 🚲</h1>
    <p>Odwiedź moją stronę: <a href="kolarstwo.html" target="_blank" rel="noopener noreferrer">Kolarstwo</a></p>
    <button class="command-button" onclick="backToMain()">Powrót</button>
  </div>

<script>
  // Aktualizacja zegarów
  function updateClocks() {
    const now = new Date();
    const h = String(now.getHours()).padStart(2,'0');
    const m = String(now.getMinutes()).padStart(2,'0');
    const s = String(now.getSeconds()).padStart(2,'0');
    const timeStr = `${h}:${m}:${s}`;

    document.getElementById('clock1').textContent = timeStr;
    document.getElementById('clock2').textContent = timeStr;
  }
  updateClocks();
  setInterval(updateClocks, 1000);

  // Funkcje przycisków Strona 1
  function start1() { 
    document.getElementById('page1').style.display = 'none';
    document.getElementById('page2').style.display = 'none';
    document.getElementById('subpage1').style.display = 'flex';
  }
  function save1() { 
    localStorage.setItem('daneStrona1', 'Dane zapisane ze strony 1');
    alert("Zapisano dane na stronie 1");
  }
  function settings1() {
    const name = prompt("Podaj nową nazwę użytkownika (strona 1):");
    if(name) {
      localStorage.setItem('nazwaUzytkownika1', name);
      alert("Ustawiono nazwę: " + name);
    } else {
      alert("Ustawienia anulowane.");
    }
  }
  function exit1() { 
    window.location.href = "https://www.google.com";
  }

  // Funkcje przycisków Strona 2
  function start2() { 
    document.getElementById('page1').style.display = 'none';
    document.getElementById('page2').style.display = 'none';
    document.getElementById('subpage2').style.display = 'flex';
  }
  function save2() { 
    localStorage.setItem('daneStrona2', 'Dane zapisane ze strony 2');
    alert("Zapisano dane na stronie 2");
  }
  function settings2() {
    const name = prompt("Podaj nową nazwę użytkownika (strona 2):");
    if(name) {
      localStorage.setItem('nazwaUzytkownika2', name);
      alert("Ustawiono nazwę: " + name);
    } else {
      alert("Ustawienia anulowane.");
    }
  }
  function exit2() { 
    window.location.href = "https://www.google.com";
  }

  // Powrót do głównych stron
  function backToMain() {
    document.getElementById('subpage1').style.display = 'none';
    document.getElementById('subpage2').style.display = 'none';
    document.getElementById('page1').style.display = 'flex';
    document.getElementById('page2').style.display = 'flex';
  }
</script>

</body>
</html>
