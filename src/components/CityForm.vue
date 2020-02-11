<template>
    <div id="form" class="main-background">
        <ion-item id="input" class="main-background">
            <ion-label style="color: white;" class="main-color" position="floating">Enter your location</ion-label>
            <ion-input class="main-color" :value="location" @input="location = $event.target.value"></ion-input>
        </ion-item>

        <ion-button class="second-background second-color" expand="block" @click="search" id="button">Search</ion-button>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        name: 'CityForm',
        data () {
            return {
                location: "",
                errors: [],
                result: null,
                icon: null,
            }
        },
        methods: {
            search() {
                axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.location},&APPID=fc94cdf16f9e67399b434a447c3963da`)
                    .then(response => {
                        // JSON responses are automatically parsed.
                        this.result = null
                        this.result = response.data
                        this.result.icon = `https://openweathermap.org/img/wn/${this.result.weather[0].icon}@2x.png`
                        this.$emit("weather-card", this.result)
                        this.location = ""
                    })
                    .catch(e => {
                        this.errors.push(e)
                    })
            }
        }
    }
</script>

<style lang="scss">
    .main-background {
        --background: #101f3e;
    }
    .second-background {
        --background: #8bc6ff;
    }
    .main-color {
        --color: #8bc6ff;
    }
    .second-color {
        --color: #101f3e;
    }
    #input, #button {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }
</style>