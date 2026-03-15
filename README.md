
simple calculator!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern Glass Calculator</title>
    <style>
        :root {
            --bg: #0f172a;
            --calc-bg: #1e293b;
            --text: #f8fafc;
            --accent: #38bdf8;
            --btn-hover: #334155;
        }

        body {
            background-color: var(blue);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        .calculator {
            background: var(--calc-bg);
            width: 320px;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 20px 50px rgba(6,0,0,0.5);
        }

        #display {
            width: 100%;
            height: 80px;
            background: none;
            border: none;
            color: var(--text);
            text-align: right;
            font-size: 2.5rem;
            margin-bottom: 20px;
            outline: none;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }

        button {
            height: 60px;
            border-radius: 12px;
            border: none;
            background: #2d3748;
            color: var(--text);
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.2s;
        }

        button:hover {
            background: var(--btn-hover);
            transform: translateY(-2px);
        }

        button.operator {
            color: var(--accent);
            font-weight: bold;
        }

        button.equals {
            background: var(--accent);
            color: var(--bg);
            grid-column: span 2;
        }

        button.equals:hover {
            background: #7dd3fc;
        }

        button.clear {
            color: #ef4444;
        }
    </style>
</head>
<body>

<div class="calculator">
    <input type="text" id="display" readonly value="0">
    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">AC</button>
        <button onclick="deleteLast()">DEL</button>
        <button class="operator" onclick="append('%')">%</button>
        <button class="operator" onclick="append('/')">÷</button>
        
        <button onclick="append('7')">7</button>
        <button onclick="append('8')">8</button>
        <button onclick="append('9')">9</button>
        <button class="operator" onclick="append('*')">×</button>
        
        <button onclick="append('4')">4</button>
        <button onclick="append('5')">5</button>
        <button onclick="append('6')">6</button>
        <button class="operator" onclick="append('-')">-</button>
        
        <button onclick="append('1')">1</button>
        <button onclick="append('2')">2</button>
        <button onclick="append('3')">3</button>
        <button class="operator" onclick="append('+')">+</button>
        
        <button onclick="append('0')">0</button>
        <button onclick="append('.')">.</button>
        <button class="equals" onclick="calculate()">=</button>
    </div>
</div>

<script>
    const display = document.getElementById('display');

    function append(value) {
        if (display.value === '0' && value !== '.') {
            display.value = value;
        } else {
            display.value += value;
        }
    }

    function clearDisplay() {
        display.value = '0';
    }

    function deleteLast() {
        display.value = display.value.slice(0, -1);
        if (display.value === '') display.value = '0';
    }

    function calculate() {
        try {
           
            display.value = new Function('return ' + display.value)();
        } catch (error) {
            display.value = "Error";
            setTimeout(clearDisplay, 1500);
        }
    }
</script>

</body>
</htm