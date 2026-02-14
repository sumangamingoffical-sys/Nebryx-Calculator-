<!DOCTYPE html>
<html>
<head>
  <div style="display:none"></div>
<title>Nebryx Calculator</title>

<style>
body{
  background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);
  font-family:Arial;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
}

.app{
  background:#001f33;
  width:420px;
  padding:20px;
  border-radius:20px;
  box-shadow:0 0 30px yellow;
}

h1{
  text-align:center;
  color:#ff8f;
}

.tabs{
  display:flex;
  justify-content:space-around;
  margin-bottom:10px;
}

.tabs button{
  flex:1;
  margin:5px;
  background:#003344;
  color:#ff8f;
  border:none;
  padding:10px;
  border-radius:10px;
}

.active{
  background:#ff8f !important;
  color:black !important;
}

.calc-grid{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:10px;
}

input,select{
  width:100%;
  padding:10px;
  margin:5px 0;
  border:none;
  border-radius:10px;
  font-size:18px;
}

button{
  padding:15px;
  border:none;
  border-radius:10px;
  background:#003344;
  color:#ff8f;
}

.eq{background:#ff8f;color:black;}
.op{background:#660066;color:white;}

</style>
</head>

<body>

<div class="app">
<h1>NEBRYX CALCULATOR</h1>

<div class="tabs">
  <button id="t1" class="active" onclick="showCalc()">Calculator</button>
  <button id="t2" onclick="showCurr()">Currency</button>
</div>

<div id="calc">
<input id="d">

<div class="calc-grid">
<button onclick="d.value=''">C</button>
<button onclick="d.value=d.value.slice(0,-1)">⌫</button>
<button onclick="d.value+='Math.sin('">sin</button>
<button onclick="d.value+='Math.cos('">cos</button>

<button onclick="d.value+='7'">7</button>
<button onclick="d.value+='8'">8</button>
<button onclick="d.value+='9'">9</button>
<button class="op" onclick="d.value+='/'">÷</button>

<button onclick="d.value+='4'">4</button>
<button onclick="d.value+='5'">5</button>
<button onclick="d.value+='6'">6</button>
<button class="op" onclick="d.value+='*'">×</button>

<button onclick="d.value+='1'">1</button>
<button onclick="d.value+='2'">2</button>
<button onclick="d.value+='3'">3</button>
<button class="op" onclick="d.value+='-'">−</button>

<button onclick="d.value+='0'">0</button>
<button onclick="d.value+='.'">.</button>
<button class="eq" onclick="d.value=eval(d.value)">=</button>
<button class="op" onclick="d.value+='+'">+</button>
</div>
</div>

<div id="currency" style="display:none">
<input id="amt" placeholder="Amount">

<select id="from">
<option>USD</option>
<option>INR</option>
<option>EUR</option>
<option>GBP</option>
</select>

<select id="to">
<option>INR</option>
<option>USD</option>
<option>EUR</option>
<option>GBP</option>
</select>

<button onclick="convert()">Convert</button>
<input id="out" readonly>
</div>

</div>

<script>
function showCalc(){
calc.style.display="block";
currency.style.display="none";
t1.classList.add("active");
t2.classList.remove("active");
}

function showCurr(){
calc.style.display="none";
currency.style.display="block";
t2.classList.add("active");
t1.classList.remove("active");
}

const rates={USD:1,INR:83,EUR:0.92,GBP:0.78};

function convert(){
out.value=(amt.value/rates[from.value]*rates[to.value]).toFixed(2);
}
</script>

</body>
</html>
