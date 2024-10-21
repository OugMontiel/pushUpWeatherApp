<!-- WeatherHour.vue -->
<template>
    <section class="weatherHour">
      <div v-for="(hour, index) in weatherHours" :key="index" class="hourItem">
        <h3>{{ hour.time }}</h3>
        <div class="hourDetails">
          <img :src="hour.icon" :alt="hour.description" />
          <h4>{{ hour.temperature }}</h4>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        weatherHours: [
          { time: 'Now', temperature: '22°C', icon: '/icon/cloud.svg', description: 'Cloudy' },
          { time: '1h', temperature: '21°C', icon: '/icon/rain.svg', description: 'Rain' },
          { time: '2h', temperature: '20°C', icon: '/icon/cloud.svg', description: 'Cloudy' },
          { time: '3h', temperature: '19°C', icon: '/icon/sun.svg', description: 'Sunny' },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  /* Añadir estilos para el pronóstico por horas */
  .weatherHour {
    display: flex;
    justify-content: space-between;
    padding: 1em;
  }
  
  .hourItem {
    text-align: center;
  }
  
  .hourDetails {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  </style>
  