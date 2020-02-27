<template>
  <div id="app">
    <h1>Beers</h1>
    <beers-list :beers="beers"></beers-list>
    <beer-detail v-if="selectedBeer":beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers/')
    .then(res => res.json())
    .then(data => this.beers = data)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
