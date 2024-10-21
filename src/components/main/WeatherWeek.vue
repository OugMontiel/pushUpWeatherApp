<!-- DayForecasts.vue -->
<template>
  <section class="dayForecasts">
    <div class="weekDetails">
      <div class="weekTitle">
        <IconDisplay :icon="iconPath" description="week" />
        <h3>Day forecast</h3>
      </div>
      <div class="weekGrafica">
        weekGrafica
      </div>
    </div>
  </section>
</template>

<script>
import IconDisplay from './IconDisplay.vue';

export default {
  components: {
    IconDisplay,
  },
};
</script>

<style scoped>
.weekDetails {
  background-color: var(--white-contraste-fondo);
  padding: 0.5em;
  border-radius: 1em;
  display: flex;
  flex-direction: column;
}
.weekTitle{
  height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.weekTitle h3 {
    flex-grow: 1;
    padding: 0 .5em;
}
</style>