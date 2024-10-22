<template>
  <header :class="headerClass" :style="headerStyle">
    <div class="headerContent">
      <!-- Buscador de ciudades -->
      <div class="headerSearch">
        <h1 v-if="!searchActive">{{ ciudad }}, {{ pais }}</h1>
        <input
          type="text"
          v-if="searchActive"
          @blur="toggleSearch"
          placeholder="Buscar ciudad..."
        />
        <img
          src="/icon/searchHeader.svg"
          alt="Icono de búsqueda"
          @click="toggleSearch"
          class="searchIcon"
        />
      </div>

      <!-- Temperatura -->
      <div class="headerTemp">
        <h1 class="blond">{{ temperaturaHoy }}°</h1>
        <h3>{{ descripcionDia }}</h3>
        <div v-if="isExpanded">
          <img src="/icon/solesHeaderExpandido.svg" alt="Icono de clima" />
          <h2>{{ descripcionClima }}</h2>
        </div>
        <div v-if="!isExpanded">
          <img src="/icon/solesHeader.svg" alt="Icono de clima" />
          <h2>{{ descripcionClima }}</h2>
        </div>
      </div>

      <!-- Fecha y predicción -->
      <div v-if="isExpanded" class="headerDate">
        <h3>{{ fecha }}, {{ hora }}</h3>
        <div class="blond">
          <h3>Day {{ temperaturaHoy }}°</h3>
          <h3>Night {{ temperaturaManana }}°</h3>
        </div>
      </div>
    </div>

    <!-- Botones de predicción -->
    <div class="headerButtons">
      <button>Today</button>
      <button>Tomorrow</button>
      <button>10 days</button>
    </div>
  </header>
  <div v-if="!isExpanded" style="height: 35vh;"></div> <!-- Espacio adicional -->
</template>

<script>
export default {
  data() {
    return {
      scrollY: 0,
      isExpanded: true, // Controla si el header está expandido o contraído
      searchActive: false, // Controla si el input de búsqueda está activo
      ciudad: '', // Ciudad (será obtenida de una petición)
      pais: '', // País (será obtenido de una petición)
      temperaturaHoy: '', // Temperatura del día actual
      temperaturaManana: '', // Temperatura del día siguiente
      fecha: '', // Fecha actual
      hora: '', // Hora actual
      descripcionDia: '', // Descripción del clima del día actual
      descripcionClima: '', // Descripción adicional del clima (ej: soleado, nublado)
    }
  },
  computed: {
    headerClass() {
      return this.isExpanded ? 'header-expanded' : 'header-collapsed'
    },
    headerStyle() {
      return {
        transition: 'all 0.3s ease', // Animación para suavizar la transición
        height: this.isExpanded ? '50vh' : '15vh', // Altura dinámica
        position: this.isExpanded ? 'static' : 'fixed', // Cambia entre 'static' y 'sticky'
        top: 0, // Asegura que esté en la parte superior de la ventana
        width: '100%', // Asegura que el encabezado ocupe todo el ancho de la ventana
        zIndex: 1000, // Asegura que el encabezado esté por encima de otros elementos
      }
    },
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll) // Escucha el evento scroll
    this.fetchWeatherData()
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll) // Limpieza del evento
  },
  methods: {
    handleScroll() {
      this.scrollY = window.scrollY || document.documentElement.scrollTop // Captura el desplazamiento

      // Solo cambia el estado si hay un cambio en el scroll
      const shouldExpand = this.scrollY < 100
      if (this.isExpanded !== shouldExpand) {
        this.isExpanded = shouldExpand // Cambia el estado solo si es necesario
      }
    },
    toggleSearch() {
      this.searchActive = !this.searchActive // Alternar el input de búsqueda
    },
    fetchWeatherData() {
      const weatherData = {
        ciudad: 'Bogotá',
        pais: 'Colombia',
        temperaturaHoy: 22,
        temperaturaManana: 18,
        fecha: '2024-10-21',
        hora: '14:00',
        descripcionDia: 'Soleado con nubes',
        descripcionClima: 'Cloudy',
      }

      // Asignar los datos obtenidos a las variables reactivas
      this.ciudad = weatherData.ciudad
      this.pais = weatherData.pais
      this.temperaturaHoy = weatherData.temperaturaHoy
      this.temperaturaManana = weatherData.temperaturaManana
      this.fecha = weatherData.fecha
      this.hora = weatherData.hora
      this.descripcionDia = weatherData.descripcionDia
      this.descripcionClima = weatherData.descripcionClima
    },
  },
}
</script>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  transition:
    background-color var(--transition-3),
    color var(--transition-3);
}

/* Estilos del header expandido */
.header-expanded .headerContent {
  background-image: url(/icon/fondoHeaderExpandido.png);
  background-size: cover; /* Hace que la imagen cubra todo el contenedor */
  background-position: bottom;
  background-repeat: no-repeat; /* Evita que la imagen se repita */
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1em;
  color: var(--white);
  border-bottom-left-radius: 2em;
  border-bottom-right-radius: 2em;
}

.headerSearch,
.headerTemp,
.headerDate {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.headerTemp h1 {
  font-size: 4em;
}

.headerTemp h3 {
  flex-grow: 1;
}

.headerTemp h3,
.headerTemp h1 {
  height: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: flex-end;
}

/* Estilos del header contraído */
.header-collapsed {
  background-color: var(--white-hearder);
  color: var(--black);
}
.header-collapsed .headerButtons{
  background-color: var(--white-hearder);
}

/* Estilos para el input de búsqueda y el ícono */
.headerSearch input {
  padding: 0.5em;
  border: transparent;
  outline: none;
}

.searchIcon {
  cursor: pointer;
  width: 24px;
  height: 24px;
}

.headerButtons {
  padding: 1em;
  display: flex;
  justify-content: space-around;
}

.headerButtons button {
  width: 25vw;
  padding: 1em;
  background-color: var(--white);
  color: var(--black);
  border: none;
  border-radius: 1em;
  cursor: pointer;
  transition: background-color var(--transition-1);
}

.headerButtons button:hover {
  background-color: var(--button-active);
}
</style>
