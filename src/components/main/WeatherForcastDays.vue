<template>
  <section class="weatherForcastDays">
    <div class="forcastDaysDetails">
      <div
        v-for="(inf, index) in elemenPronostico"
        :key="index"
        class="elemenPronostico"
      >
        <div class="circulo">
          <IconDisplay :icon="inf.icon" :description="inf.description" />
        </div>
        <div class="contenido">
          <h3>{{ inf.titulo }}</h3>
          <div class="datos">
            <h3>{{ inf.dato }}</h3>
            <h4>
              <span >
                {{ inf.varDato }}
              </span>
            </h4>
          </div>
        </div>
      </div>
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
      elemenPronostico: [
        {
          titulo: 'Sunrise',
          dato: '4:20 AM',
          varDato: '4h ago',
          icon: '/icon/sunrise.svg',
          description: 'sunrise icon',
        },
        {
          titulo: 'Sunset',
          dato: '4:50 PM',
          varDato: 'in 9h',
          icon: '/icon/sunset.svg',
          description: 'sunset icon',
        }
      ],
    }
  },
}
</script>

<style scoped>
.forcastDaysDetails {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 1em;
}

.elemenPronostico {
  background-color: var(--white-contraste-fondo);
  padding: 0.5em;
  height: 5em;
  border-radius: 1em;
  display: flex;
}

.circulo {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.contenido {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  padding: 0 0.5em;
}

.datos {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.datos h4 {
  gap: 0.5em;
}

.datos span {
  display: flex;
  align-items: center;
}

</style>
