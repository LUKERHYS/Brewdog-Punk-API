<template>

    <div class="container">

      <div id="list">
        <h1>Beers..</h1>
        <beers-list :beers="beers"></beers-list>
      </div>

      <div id="detail">
        <beer-detail v-if="selectedBeer":beer="selectedBeer"></beer-detail>
      </div>

      <div id="list">
        <h1>Favourites..</h1>
        <favourite-beers :beers="favouriteBeers"></favourite-beers>
      </div>

    </div>

</template>

<script>
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'
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
    fetch('https://api.punkapi.com/v2/beers?page=2&per_page=80')
    // fetch('https://api.punkapi.com/v2/beers/')
    .then(res => res.json())
    .then(data => this.beers = this.formatBeers(data))

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },
  computed:{
    favouriteBeers: function(){
      return this.beers.filter((beer)=>{
        return beer.isFavourite;
      })
    }
  },
  methods: {
    formatBeers: function(beers){
      return beers.map((beer) => {
        beer['isFavourite'] = false;
        return beer;
      })
    }
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": BeersList
  }
}
</script>

<style>
.container {
  width: 100%;
  display: flex;
  justify-content: space-around;
  max-height: 100%;
}
#list {
  justify-content: center;
  width: 30%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
  max-height: 800px;
  padding:4px;
  overflow-x: hidden;
  overflow-x: auto;
  text-align:justify;
}
#list h1{
  position: fixed;
  top: 0;

}
#detail {
  justify-content: center;
  align-content: center;
  width: 30%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
