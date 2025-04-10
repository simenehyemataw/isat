<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>መልካም እድል</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #1e1e2f;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      text-align: center;
      background: #2c2c4a;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
      max-width: 400px;
      width: 90%;
    }
    .numbers {
      margin: 10px 0;
      display: flex;
      justify-content: center;
      gap: 15px;
      flex-wrap: wrap;
      flex-direction: column;
    }
    .numbers span {
      background: #ffcc00;
      color: #000;
      padding: 15px 20px;
      border-radius: 50%;
      font-size: 20px;
      font-weight: bold;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    button {
      padding: 10px 20px;
      font-size: 18px;
      background-color: #ffcc00;
      color: #000;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background-color: #e6b800;
    }
    label {
      display: block;
      margin: 15px 0 5px;
      font-size: 16px;
    }
    select {
      padding: 8px 12px;
      font-size: 16px;
      border-radius: 8px;
      border: none;
      outline: none;
      background-color: #fff;
      color: #000;
      margin-bottom: 20px;
    }
    #result {
      margin-top: 15px;
      font-size: 18px;
      font-weight: bold;
      color: #00ff99;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>መልካም እድል</h1>
    <p>ከ0-9 ቁጥር ውስጥ አንዱን ይምረጡ እና "አውጣ" ይጫኑ!</p>

    <label for="userNumber">የእርስዎ ቁጥር:</label>
    <select id="userNumber">
      <script>
        for (let i = 0; i <= 9; i++) {
          document.write(`<option value="${i}">${i}</option>`);
        }
      </script>
    </select>

    <div id="lotteryNumbers" class="numbers"></div>
    <p id="result"></p>
    <button onclick="generateLottery()">አውጣ</button>
  </div>

  <script>
    function generateLottery() {
      const numberContainer = document.getElementById('lotteryNumbers');
      const resultDisplay = document.getElementById('result');
      const userPick = parseInt(document.getElementById('userNumber').value);

      numberContainer.innerHTML = '';
      resultDisplay.textContent = '';

      let numbers = [];
      while (numbers.length < 3) {
        let randomNum = Math.floor(Math.random() * 10);
        if (!numbers.includes(randomNum)) {
          numbers.push(randomNum);
        }
      }

      numbers.forEach(num => {
        const span = document.createElement('span');
        span.textContent = num;
        numberContainer.appendChild(span);
      });

      if (userPick === numbers[0]) {
        resultDisplay.textContent = "እንኳን ደስ አለዎት! $1000 አሸነፉ!";
      } else if (userPick === numbers[1]) {
        resultDisplay.textContent = "እንኳን ደስ አለዎት! $100 አሸነፉ!";
      } else if (userPick === numbers[2]) {
        resultDisplay.textContent = "እንኳን ደስ አለዎት! $50 አሸነፉ!";
      } else {
        resultDisplay.textContent = "ይቅርታ፣ አልተመሳሰሉም። እንደገና ይሞክሩ!";
      }
    }
  </script>
</body>
</html>
