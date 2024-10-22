<script setup>
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'
</script>

<template>
  <div class="layout">
    <!-- Componente de encabezado -->
    <div class="layoutHeader">
      <HeaderComponent />
    </div>

    <!-- Componente principal desplazable -->
    <div class="layoutMain">
      <MainComponent />
    </div>
  </div>
</template>

<style scoped>
/* Contenedor principal usando flexbox */
.layout {
  display: flex;
  flex-direction: column;
  height: 100vh; /* Toda la altura de la ventana */
  /* overflow: overlay;
  overflow-y: auto; */
}

/* El encabezado ocupa parte de la pantalla, pero no bloquea el desplazamiento */
.layoutHeader {
  flex-shrink: 0;
}

/* Contenido principal desplazable */
.layoutMain {
  flex-grow: 1;
}
</style>
