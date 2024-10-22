<template>
  <section class="weatherForecast">
    <div class="forecastDetails">
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
              <span :class="{ up: inf.varDato >= 0, down: inf.varDato < 0 }">
                <svg
                  v-if="inf.varDato >= 0"
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                >
                  <path
                    fill-rule="evenodd"
                    d="M8 12V4.5l4 4-1 1-3-3-3 3-1-1 4-4z"
                  />
                </svg>
                <svg
                  v-else
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                >
                  <path
                    fill-rule="evenodd"
                    d="M8 4v7.5l-4-4 1-1 3 3 3-3 1 1-4 4V4z"
                  />
                </svg>
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
          titulo: 'Wind Speed',
          dato: '15 km/h',
          varDato: 2,
          icon: '/icon/windSpeed.svg',
          description: 'Wind icon',
        },
        {
          titulo: 'Rain Chance',
          dato: '40%',
          varDato: -10,
          icon: '/icon/rainChance.svg',
          description: 'Rain icon',
        },
        {
          titulo: 'Pressure',
          dato: '1015 hPa',
          varDato: 5,
          icon: '/icon/pressure.svg',
          description: 'Pressure icon',
        },
        {
          titulo: 'UV Index',
          dato: '5',
          varDato: 1,
          icon: '/icon/UVIndex.svg',
          description: 'UV index icon',
        },
      ],
    }
  },
}
</script>

<style scoped>
.forecastDetails {
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

.up svg {
  fill: green;
}

.down svg {
  fill: red;
}
</style>
