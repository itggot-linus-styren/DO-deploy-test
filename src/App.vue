<template>
  <div>
    <h1>Weather App</h1>
    <CitySearchField v-show="!showCityInfo" />
    <CityInfoCard @goBack="hideCityInfo" v-show="showCityInfo" />
  </div>
</template>

<script>
import CityInfoCard from './components/CityInfoCard.vue';
import CitySearchField from './components/CitySearchField.vue';

export default {
  name: 'App',
  data() {
    return {
      showCityInfo: false
    }
  },
  methods: {
    hideCityInfo() {
      this.showCityInfo = false;
    }
  },
  created() {
    this.$bus.on('searchCity', () => {
      this.showCityInfo = true;
    })
  },
  components: { CityInfoCard, CitySearchField }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  align-items: center;
  justify-content: center;
  height: calc(100vh - 5em);
  font-size: 24px;
}
</style>
