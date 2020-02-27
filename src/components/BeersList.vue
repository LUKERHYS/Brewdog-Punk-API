<template lang="html">
    <ul>
      <list-component v-for="(beer, index) in beers" :beer="beer" :key="index"></list-component>
      <favourite-beers v-for="(beer, index) in beers" :beer="beer" :key="index"></favourite-beers>
    </ul>
</template>

<script>
import ListComponent from './ListComponent.vue'
import FavouriteBeers from './FavouriteBeers.vue'

export default {
  name: 'beers-list',
  props: ['beers'],
  components: {
    "list-component": ListComponent,
    "favourite-beers": FavouriteBeers
  },
}
</script>

<style lang="css" scoped>
</style>
