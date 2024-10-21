<template>
  <main>
    <!-- Importar el componente del pronóstico de hoy -->
    <WeatherForecast />

    <!-- Importar el componente del pronóstico por horas -->
    <WeatherHour />

    <WeatherWeek />
  </main>
</template>

<script>
import WeatherForecast from './main/WeatherForecast.vue';
import WeatherHour from './main/WeatherHour.vue';
import WeatherWeek from './main/WeatherWeek.vue';

export default {
  components: {
    WeatherForecast,
    WeatherHour,
    WeatherWeek,
  },
};
</script>

<style scoped>
section{
  padding: 1em;
}
/* Aquí puedes incluir estilos generales del main si los necesitas */
</style>
