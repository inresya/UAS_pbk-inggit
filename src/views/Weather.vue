<template>
    <div class="container">
      <header>
        <h1>Weather Information</h1>
      </header>
      <main>
        <input v-model="location" placeholder="Enter Location" class="input" />
        <button @click="getWeather" class="btn">Get Weather</button>
        <div v-if="weather" class="weather-info">
          <h2>Weather in {{ weather.name }}</h2>
          <p>{{ weather.weather[0].description }}</p>
          <p>Temperature: {{ (weather.main.temp - 273.15).toFixed(2) }}°C</p>
        </div>
      </main>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'Weather',
    setup() {
      const location = ref('');
      const weather = ref(null);
  
      const getWeather = async () => {
        const apiKey = 'b7bfca7wadaw89accc989c89c89c98';
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${location.value}&appid=${apiKey}`;
        const response = await fetch(apiUrl);
        weather.value = await response.json();
      };
  
      return { location, weather, getWeather };
    },
  };
  </script>
  
  <style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    text-align: center;
  }
  header {
    margin-bottom: 20px;
  }
  .input {
    padding: 10px;
    font-size: 16px;
    margin-bottom: 20px;
    width: 200px;
  }
  .btn {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
  .weather-info {
    margin-top: 20px;
  }
  </style>
  