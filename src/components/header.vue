<template>
    <header :class="headerClass" :style="headerStyle">
        <div class="header-content">
            <div> 
                <h1>ciudad , pais </h1>
                <input type="text"> <!-- Inpuc se activa cundo le de click al icono de busqueda -->
                <img src="/icon/searchHeader.svg" alt="icono de Busqueda">
            </div>
            <div>
                <h2 class="blond">temperatura</h2>
                <h3>dato descripcion</h3>
                
                <img src="/icon/solesHeader.svg" alt="">
                <h2>Cloudy</h2>
            </div>
            <div>
                <h3>fecha, hora</h3>
                <div class="blond">
                    <h3> Dia temperatura</h3>
                    <h3> Noche temperatura</h3>
                </div>
            </div>
            <h1 :class="elemenClass">Mi Sitio Web</h1>
            <p v-if="isExpanded">Bienvenidos a la mejor experiencia</p>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            isExpanded: true, // Para controlar si el header está expandido o contraído
        };
    },
    computed: {
        headerClass() {
            return this.isExpanded ? 'header-expanded' : 'header-collapsed';
        },
        elemenClass() {
            return this.isExpanded ? 'elemen-expanded' : 'elemen-collapsed';
        },
        headerStyle() {
            return {
                transition: 'all 5s ease', // Transición suave de 5 segundos
                height: this.isExpanded ? '50vh' : '10vh', // Altura dinámica
            };
        },
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll); // Escucha el evento scroll
    },
    beforeDestroy() {
        window.removeEventListener('scroll', this.handleScroll); // Limpieza del evento
    },
    methods: {
        handleScroll() {
            const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
            this.isExpanded = scrollTop < 100; // Cambia el estado cuando se hace scroll
        },
    },
};
</script>

<style scoped>
/* Estilos cuando el header está expandido */
.header-expanded {
    background-color: var(--white-fondo);
    color: var(--white);
    display: flex;
    justify-content: center;
    padding: 1em;
}

.elemen-expanded {
    transition: var(--transition-3);
}


/* Estilos cuando el header está contraído */
.header-collapsed {
    background-color: var(--white-hearder);
    color: var(--blac);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px;
}

.elemen-collapsed {
    transition: var(--transition-3);
}
</style>