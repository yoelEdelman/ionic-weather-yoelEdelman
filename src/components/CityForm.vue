<template>
    <div id="form">
        <ion-item id="input">
            <ion-label position="floating">Enter your location</ion-label>
            <ion-input :value="location" @input="location = $event.target.value"></ion-input>
        </ion-item>

        <ion-button expand="block" @click="search" id="button">Search</ion-button>
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
            }
        },
        methods: {
            search() {
                axios.get(`http://api.openweathermap.org/data/2.5/weather?q=${this.location},&APPID=fc94cdf16f9e67399b434a447c3963da`)
                    .then(response => {
                        // JSON responses are automatically parsed.
                        this.result = null
                        this.result = response.data
                        this.$emit("weather-card", this.result)
                        this.location = ""

                        // this.posts = response.data
                    })
                    .catch(e => {
                        this.errors.push(e)
                    })
            }
        }
    }
</script>

<style lang="scss">
    #input, #button {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }
</style>