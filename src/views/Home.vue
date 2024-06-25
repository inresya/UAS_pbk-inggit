<template>
    <div class="container">
      <header>
        <h1>Weather App</h1>
      </header>
      <main>
        <router-link to="/weather">
          <button class="btn">Check Weather</button>
        </router-link>
      </main>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Home',
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
  .btn {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
  </style>
  