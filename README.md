<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Age Calculator Premium</title>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Roboto', sans-serif;
  background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  width: 100%;
  max-width: 450px;
  background: rgba(255,255,255,0.05);
  backdrop-filter: blur(15px);
  border-radius: 20px;
  box-shadow: 0 0 40px rgba(0,255,255,0.3);
  padding: 30px;
  color: #fff;
  text-align: center;
}

h1 {
  margin-bottom: 25px;
  font-size: 2rem;
  text-shadow: 0 0 10px #00fff0;
}

.inputs {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

input {
  width: 30%;
  padding: 12px;
  font-size: 1rem;
  border-radius: 12px;
  border: none;
  background: rgba(255,255,255,0.1);
  color: #fff;
  text-align: center;
  box-shadow: 0 0 10px rgba(0,255,255,0.3);
}

input::placeholder {
  color: rgba(255,255,255,0.6);
}

button {
  width: 100%;
  padding: 15px;
  font-size: 1.2rem;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  background: #00fff0;
  color: #020c15;
  font-weight: bold;
  box-shadow: 0 0 20px #00fff0;
  transition: all 0.3s ease;
}

button:hover {
  background: #00d8cc;
  box-shadow: 0 0 30px #00d8cc;
}

.result {
  margin-top: 25px;
  font-size: 1.4rem;
  padding: 15px;
  background: rgba(0,255,255,0.1);
  border-radius: 15px;
  box-shadow: 0 0 20px rgba(0,255,255,0.2);
}

@media (max-width: 500px){
  input { width: 28%; }
  h1 { font-size: 1.6rem; }
  .result { font-size: 1.2rem; }
}
</style>
</head>

<body>
<div class="container">
  <h1>Age Calculator</h1>

  <div class="inputs">
    <input type="number" id="day" placeholder="DD">
    <input type="number" id="month" placeholder="MM">
    <input type="number" id="year" placeholder="YYYY">
  </div>

  <button onclick="calculateAge()">Calculate</button>

  <div class="result" id="result"></div>
</div>

<script>
function calculateAge(){
  let d = parseInt(document.getElementById("day").value);
  let m = parseInt(document.getElementById("month").value);
  let y = parseInt(document.getElementById("year").value);

  if(!d || !m || !y){
    document.getElementById("result").innerText = "Please enter valid date!";
    return;
  }

  let today = new Date();
  let birth = new Date(y, m - 1, d);

  if(birth > today){
    document.getElementById("result").innerText = "Birth date must be before today!";
    return;
  }

  let ageYears = today.getFullYear() - birth.getFullYear();
  let ageMonths = today.getMonth() - birth.getMonth();
  let ageDays = today.getDate() - birth.getDate();

  if(ageDays < 0){
    ageMonths--;
    ageDays += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
  }
  if(ageMonths < 0){
    ageYears--;
    ageMonths += 12;
  }

  document.getElementById("result").innerHTML =
    "<b>" + ageYears + "</b> Years " +
    "<b>" + ageMonths + "</b> Months " +
    "<b>" + ageDays + "</b> Days";
}
</script>
</body>
</html>
