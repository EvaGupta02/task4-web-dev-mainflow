![Screenshot 2024-06-14 203704](https://github.com/EvaGupta02/task4-web-dev-mainflow/assets/1<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculator</title>
  <style>
    body {
      background-color: #282c34;
      color: #fff;
      font-family: sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 10px;
      padding: 20px;
      border-radius: 10px;
      background-color: #333;
    }

    .button {
      border: none;
      padding: 20px;
      font-size: 20px;
      border-radius: 10px;
      background-color: #444;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .button:hover {
      background-color: #555;
    }

    .button.operator {
      background-color: #666;
    }

    .button.operator:hover {
      background-color: #777;
    }

    .button.number {
      background-color: #444;
    }

    .button.number:hover {
      background-color: #555;
    }

    .button.clear {
      background-color: #f00;
    }

    .button.clear:hover {
      background-color: #ff0;
    }

    .button.equal {
      background-color: #0f0;
    }

    .button.equal:hover {
      background-color: #0ff;
    }

    .display {
      grid-column: 1 / span 4;
      padding: 20px;
      background-color: #111;
      border-radius: 10px;
      font-size: 30px;
      text-align: right;
    }

    .copyright {
      margin-top: 20px;
      color: #777;
      font-size: 14px;
    }
  </style>
</head>

<body>

  <div class="calculator">
    <div class="display"></div>
    <button class="button clear">C</button>
    <button class="button operator">+-</button>
    <button class="button operator">%</button>
    <button class="button operator">/</button>
    <button class="button number">7</button>
    <button class="button number">8</button>
    <button class="button number">9</button>
    <button class="button operator">X</button>
    <button class="button number">4</button>
    <button class="button number">5</button>
    <button class="button number">6</button>
    <button class="button operator">-</button>
    <button class="button number">1</button>
    <button class="button number">2</button>
    <button class="button number">3</button>
    <button class="button operator">+</button>
    <button class="button number">0</button>
    <button class="button">.</button>
    <button class="button equal">=</button>
  </div>

  <script>
    const display = document.querySelector('.display');
    const buttons = document.querySelectorAll('.button');
    let currentInput = '';
    let previousOperator = '';
    buttons.forEach(button => {
      button.addEventListener('click', () => {
        const value = button.textContent;
        if (value === '=') {
          calculate();
        } else if (value === 'C') {
          clearDisplay();
        } else if (['+', '-', 'X', '/', '%'].includes(value)) {
          handleOperator(value);
        } else {
          appendValue(value);
        }
      });
    });

    function appendValue(value) {
      currentInput += value;
      display.textContent = currentInput;
    }

    function handleOperator(operator) {
      if (previousOperator) {
        calculate();
      }
      previousOperator = operator;
      currentInput += operator;
      display.textContent = currentInput;
    }

    function calculate() {
      let result;
      try {
        const expression = currentInput.replace(/X/g, '*');
        result = eval(expression);
      } catch (error) {
        display.textContent = 'Error';
        return;
      }
      currentInput = result.toString();
      display.textContent = currentInput;
      previousOperator = '';
    }

    function clearDisplay() {
      currentInput = '';
      previousOperator = '';
      display.textContent = '0';
    }
  </script>
</body>

</html>50214201/2033d074-d916-4d2f-a0ab-2f450a76f24b)
