<template>
  <main>
    <!-- Importar el componente del pronóstico de hoy -->
    <WeatherForecast />

    <!-- Importar el componente del pronóstico por horas -->
    <WeatherHour />

    <!-- Importar el componente del pronóstico por semanas -->
    <WeatherWeek />

    <!-- Importar el componente del pronóstico por horas en barras-->
    <WeatherHourBarra />

    <!-- Importar el componente del pronóstico del dai y de la noche -->
    <WeatherForcastDays />
  </main>
</template>

<script>
import WeatherForecast from './main/WeatherForecast.vue'
import WeatherHour from './main/WeatherHour.vue'
import WeatherWeek from './main/WeatherWeek.vue'
import WeatherHourBarra from './main/WeatherHourBarra.vue'
import WeatherForcastDays from './main/WeatherForcastDays.vue'

export default {
  components: {
    WeatherForecast,
    WeatherHour,
    WeatherWeek,
    WeatherHourBarra,
    WeatherForcastDays,
  },
}
</script>

<style scoped>
section {
  padding: 1em;
}
/* Aquí puedes incluir estilos generales del main si los necesitas */
</style>
