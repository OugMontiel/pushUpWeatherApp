<template>
    <header :class="headerClass" :style="headerStyle">
        <div class="headerContent">
            <!-- Bucador de ciudades -->
            <div class="headerSearch">
                <h1 v-if="!searchActive">Ciudad, País</h1>
                <input type="text" v-if="searchActive" @blur="toggleSearch" placeholder="Buscar ciudad...">
                <img src="/icon/searchHeader.svg" alt="Icono de búsqueda" @click="toggleSearch" class="searchIcon">
            </div>

            <!-- Temperatura -->
            <div class="headerTemp">
                <h2 class="blond">Temperatura</h2>
                <h3>Descripción del dato</h3>
                <div>
                    <img src="/icon/solesHeader.svg" alt="Icono de clima">
                    <h2 v-if="isExpanded">Cloudy</h2>
                </div>
            </div>

            <!-- Fecha y predicción -->
            <div v-if="isExpanded" class="headerDate">
                <h3>Fecha, Hora</h3>
                <div class="blond">
                    <h3>Day Temperatura</h3>
                    <h3>Night Temperatura</h3>
                </div>
            </div>
        </div>

        <!-- Botones de predicción -->
        <div class="headerButtons">
            <button>Hoy</button>
            <button>Mañana</button>
            <button>10 días</button>
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            isExpanded: true,   // Controla si el header está expandido o contraído
            searchActive: false // Controla si el input de búsqueda está activo
        };
    },
    computed: {
        headerClass() {
            return this.isExpanded ? 'header-expanded' : 'header-collapsed';
        },
        headerStyle() {
            return {
                transition: 'all 0.5s ease', // Animación más rápida y suave (0.5s)
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
        toggleSearch() {
            this.searchActive = !this.searchActive; // Alternar el input de búsqueda
        }
    },
};
</script>

<style scoped>
/* Estilos del header expandido */
.header-expanded {
    background-color: var(--white-fondo);
    color: var(--white);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding: 1em;
    transition: background-color var(--transition-3), color var(--transition-3);
    border-radius: 2em;
}

.headerContent {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-grow: 1;
}

.headerSearch,
.headerTemp,
.headerDate {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* Estilos del header contraído */
.header-collapsed {
    background-color: var(--white-header);
    color: var(--black);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 0.5em;
    transition: background-color var(--transition-3), color var(--transition-3);
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