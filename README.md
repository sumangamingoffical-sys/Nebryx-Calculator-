<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Nebryx Calculator</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
/* remove github pages header */
header, .site-header, .page-header {
    display: none !important;
}

/* full screen */
html, body {
    width: 100%;
    height: 100%;
    margin: 0;
    background: #020c15;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    font-family: Arial, sans-serif;
}

.calculator {
    width: 100%;
    max-width: 420px;
    height: 100vh;
    background: linear-gradient(145deg,#0b1e2d,#03101a);
    border-radius: 20px;
    box-shadow: 0 0 30px #00c6ff;
    display: flex;
    flex-direction: column;
    padding: 15px;
    box-sizing: border-box;
}

/* screen */
.screen {
    background: black;
    color: #00c6ff;
    height: 80px;
    border-radius: 12px;
    padding: 15px;
    font-size: 2rem;
    text-align: right;
    overflow-x: auto;
}

/* buttons */
.buttons {
    display: grid;
    grid-template-columns: repeat(4,1fr);
    gap: 12px;
    margin-top: 20px;
    flex-grow: 1;
}

button {
    background: #071a2b;
    color: #00c6ff;
    border: none;
    border-radius: 12px;
    font-size: 1.4rem;
    box-shadow: 0 0 10px #00c6ff40;
    cursor: pointer;
}

button:active {
    transform: scale(0.95);
    box-shadow: 0 0 20px #00c6ff;
}

.equal {
    grid-column: span 2;
    background: #00c6ff;
    color: black;
    font-weight: bold;
}
</style>
</head>

<body>

<div class="calculator">
    <div id="display" class="screen">0</div>

    <div class="buttons">
        <button onclick="clearDisplay()">C</button>
        <button onclick="del()">⌫</button>
        <button onclick="add('/')">÷</button>
        <button onclick="add('*')">×</button>

        <button onclick="add('7')">7</button>
        <button onclick="add('8')">8</button>
        <button onclick="add('9')">9</button>
        <button onclick="add('-')">−</button>

        <button onclick="add('4')">4</button>
        <button onclick="add('5')">5</button>
        <button onclick="add('6')">6</button>
        <button onclick="add('+')">+</button>

        <button onclick="add('1')">1</button>
        <button onclick="add('2')">2</button>
        <button onclick="add('3')">3</button>
        <button onclick="calc()" class="equal">=</button>

        <button onclick="add('0')" style="grid-column: span 2;">0</button>
        <button onclick="add('.')">.</button>
    </div>
</div>

<script>
let display = document.getElementById("display");

function add(val){
    if(display.innerText === "0") display.innerText = "";
    display.innerText += val;
}

function clearDisplay(){
    display.innerText = "0";
}

function del(){
    display.innerText = display.innerText.slice(0,-1);
    if(display.innerText === "") display.innerText = "0";
}

function calc(){
    try{
        display.innerText = eval(display.innerText);
    }catch{
        display.innerText = "Error";
    }
}
</script>

</body>
</html>
