<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Age Calculator</title>

<style>
body {
  font-family: Arial, sans-serif;
  background: #f2f3f5;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh;
  padding-top: 40px;
}

.container {
  width: 100%;
  max-width: 450px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 0 15px #aaa;
  padding: 20px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

input {
  width: 30%;
  padding: 8px;
  font-size: 16px;
  margin: 0 5px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

button {
  width: 100%;
  background: #0078ff;
  color: white;
  padding: 12px;
  font-size: 18px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 15px;
}

button:hover {
  background: #005adb;
}

.result {
  margin-top: 20px;
  font-size: 18px;
}
</style>

</head>
<body>

<div class="container">
  <h1>Age Calculator</h1>

  <div>
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
    "Age: <b>" + ageYears + "</b> Years " +
    "<b>" + ageMonths + "</b> Months " +
    "<b>" + ageDays + "</b> Days";
}
</script>

</body>
</html>
