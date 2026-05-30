<!DOCTYPE html>
<html>
<head>
<title>Weather App</title>

<style>
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #74ebd5, #ACB6E5);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  background: rgba(255, 255, 255, 0.2);
  padding: 30px;
  border-radius: 15px;
  text-align: center;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.2);
}

input {
  padding: 10px;
  border: none;
  border-radius: 8px;
  margin: 10px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  background: #333;
  color: white;
  cursor: pointer;
}

button:hover {
  background: #555;
}

#weather {
  margin-top: 20px;
  font-size: 18px;
}
</style>

</head>

<body>

<div class="container">
  <h1>🌦️ Weather App</h1>
  <input id="city" placeholder="Enter city name">
  <br>
  <button onclick="getWeather()">Check Weather</button>

  <div id="weather"></div>
</div>

<script>
async function getWeather() {
  let city = document.getElementById("city").value;

  let response = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=YOUR_API_KEY&units=metric`
  );

  let data = await response.json();

  document.getElementById("weather").innerHTML =
    `<b>${data.name}</b><br>
     🌡️ Temp: ${data.main.temp}°C<br>
     🌥️ ${data.weather[0].description}`;
}
</script>

</body>
</html>
