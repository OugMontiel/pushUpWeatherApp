<!-- WeatherHour.vue -->
<template>
    <section class="weatherHour">
        <div class="hourDetails">
            <div class="hourTitle">
                <IconDisplay :icon="iconPath" description="forecast" />
                <h3>Hourly forecast</h3>
            </div>
            <div class="hourList">
                <div v-for="(hour, index) in weatherHours" :key="index" class="hourItem">
                    <h3>{{ hour.time }}</h3>
                    <div class="hourDetails">
                        <img :src="hour.icon" :alt="hour.description" />
                        <h4>{{ hour.temperature }}</h4>
                    </div>
                </div>
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
    data() {
        return {
            weatherHours: [
                { time: 'Now', temperature: '22°C', icon: '/icon/cloud.svg', description: 'Cloudy' },
                { time: '10h', temperature: '21°C', icon: '/icon/rain.svg', description: 'Rain' },
                { time: '11h', temperature: '20°C', icon: '/icon/cloud.svg', description: 'Cloudy' },
                { time: '12h', temperature: '19°C', icon: '/icon/sun.svg', description: 'Sunny' },
                { time: '1h', temperature: '19°C', icon: '/icon/sun.svg', description: 'Sunny' },
                { time: '2h', temperature: '19°C', icon: '/icon/sun.svg', description: 'Sunny' },
            ],
        };
    },
};
</script>


<style scoped>
.hourDetails {
    background-color: var(--white-contraste-fondo);
    padding: 0.5em;
    border-radius: 1em;
    display: flex;
    flex-direction: column;
}

.hourTitle {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hourTitle h3 {
    flex-grow: 1;
    padding: 0 .5em;
}

.hourList {
    display: flex;
}

.hourItem {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0.5em;
}
</style>