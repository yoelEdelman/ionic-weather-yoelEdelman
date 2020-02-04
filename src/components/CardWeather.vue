<template>
    <ion-card id="card">
        <ion-card-header>
            <ion-card-title>{{ result.weather[0].description }}</ion-card-title>
        </ion-card-header>

        <ion-card-content id="card-content">
            <img :src="icon" alt="">
            <strong>{{ Math.round(result.main.temp - 273.15) + '°C' }}</strong>
        </ion-card-content>
    </ion-card>
</template>

<script>
    export default {
        name: 'CardWeather',
        props: [
            "result"
        ],
        data() {
            return {
                celcus: Math.round(this.result.main.temp - 273.15) + '°C',
                icon: `http://openweathermap.org/img/wn/${this.result.weather[0].icon}@2x.png`,
                description: this.result.weather[0].description,
            }
        }
    }
</script>

<style lang="scss">
     #card {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #0ec254;
        margin-top: 60px;
        background: #7e57ff;
    }
    #card-content {
        font-size: 2rem;
        text-transform: uppercase;
    }
</style>