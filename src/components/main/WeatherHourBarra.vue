<!-- DayForecasts.vue -->
<template>
  <section class="WeatherHourBarra">
    <div class="HourBarraDetails">
      <div class="HourBarraTitle">
        <IconDisplay :icon="iconPath" description="chanceOfRain" />
        <h3>Chance of rain</h3>
      </div>
      <div class="HourBarraGrafica">HourBarraGrafica</div>
    </div>
  </section>
</template>

<script>
import IconDisplay from './IconDisplay.vue'

export default {
  components: {
    IconDisplay,
  },
  data() {
    return {
      iconPath: '/icon/chanceOfRain.svg',
    }
  },
}
</script>

<style scoped>
.HourBarraDetails {
  background-color: var(--white-contraste-fondo);
  padding: 0.5em;
  border-radius: 1em;
  display: flex;
  flex-direction: column;
}
.HourBarraTitle {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.HourBarraTitle h3 {
  flex-grow: 1;
  padding: 0 0.5em;
}
</style>
