<template>
    <main>
        <!-- Sección de elementos del pronostico pronóstico -->
        <section class="weatherForecast">
            <div class="forecastDetails">
                <div v-for="(inf, index) in elemenPronostico" :key="index" class="elemenPronostico">
                    <div class="circulo">
                        <img :src="inf.icon" :alt="inf.description">
                    </div>
                    <div class="contenido">
                        <h3>{{ inf.titulo }}</h3> <!-- Wind Speed , Rain Chance, Pressure, UV index -->
                        <div class="datos">
                            <h3>{{ inf.dato }}</h3>
                            <h4>{{ inf.varDato }}</h4>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sección pronostico por hota -->
        <section class="weatherHour">

        </section>
    </main>
</template>

<script>
export default {
    data() {
        return {
            elemenPronostico: [
                { titulo: 'Wind Speed', dato: '15 km/h', varDato: 'NE', icon: '/icon/wind.svg', description: 'Wind icon' },
                { titulo: 'Rain Chance', dato: '40%', varDato: 'Moderate', icon: '/icon/rain.svg', description: 'Rain icon' },
                { titulo: 'Pressure', dato: '1015 hPa', varDato: 'Stable', icon: '/icon/pressure.svg', description: 'Pressure icon' },
                { titulo: 'UV Index', dato: '5', varDato: 'Moderate', icon: '/icon/uv.svg', description: 'UV index icon' },
            ],

        };
    },
};
</script>

<style scoped></style>
