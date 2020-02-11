<template>
    <ion-card id="card">
        <ion-card-header id="card-header">
            <h1 id="card-country">{{ result.name }}</h1>
            <ion-card-title id="card-title">{{ result.weather[0].description }}</ion-card-title>
        </ion-card-header>

        <ion-card-content id="card-content">
            <strong class="weather">{{ Math.round(result.main.temp - 273.15) + '°' }}</strong>
            <div>
                <div id="weather-icon">
                    <img :src="result.icon" alt="">
                </div>
                <div id="weather-details">
                    <p>Feels like: {{ Math.round(result.main.feels_like - 273.15) + '°' }}</p>
                    <p>Humidity: {{ result.main.humidity }} %</p>
                    <p>Wind: {{ Math.round(result.wind.speed * 1.609344) }} km/h</p>

                </div>
            </div>
        </ion-card-content>
    </ion-card>
</template>

<script>
    export default {
        name: 'CardWeather',
        props: [
            "result",
            "icon"
        ],
        data() {
            return {
                celcus: Math.round(this.result.main.temp - 273.15),
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
        border: 5px solid #8bc6ff;
        border-radius: 15% 0;
        color: #8bc6ff;
        margin-top: 60px;
        background: #101f3e;
        #card-header {
            #card-country {
                font-size: 2.5rem;
                color: #8bc6ff;
            }
            #card-title {
                color: #8bc6ff;
            }
         }
        #card-content {
            font-size: 2rem;
            text-transform: uppercase;
            strong {
                font-size: 150px;
                text-shadow: -20px 20px #003c85;
            }
            div {
                display: flex;
                #weather-icon {
                    width: 35%;
                    img {
                        width: 100%;
                    }
                }
                #weather-details {
                    width: 65%;
                    padding-left: 30px;
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                    align-items: flex-start;
                }
            }
         }
    }

</style>