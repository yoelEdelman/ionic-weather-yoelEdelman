<template>
  <div id="app">
    <ion-app >
        <Header/>
        <ion-content class="main-background">

          <city-form @weather-card="weatherResult"/>
          <card-weather v-if="result" :result="result"/>

        </ion-content>
    </ion-app>
  </div>
</template>

<script>
import CityForm from './components/CityForm.vue'
import Header from "./components/Header.vue";
import CardWeather from "./components/CardWeather";

export default {
  name: 'app',
  components: {
    CardWeather,
    Header,
    CityForm,
  },
  data() {
    return {
      result: null
    }
  },
  methods: {
    weatherResult(result) {
      this.result = null
      this.result = result
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.main-background {
  --background: #101f3e;
}
</style>
