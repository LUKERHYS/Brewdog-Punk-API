<template lang="html">
  <div>
    <input v-model="beer.isFavourite" type="checkbox">
    <li @click="handleClick">{{beer.name}}</li>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-component',
  props: ['beer'],
  methods: {
    handleClick() {
      eventBus.$emit('beer-selected', this.beer);
    }
  }
}
</script>

<style lang="css" scoped>
div {
  border: solid green;
}
li {
    list-style: none;
    padding: 0;
    margin: 0;
}
</style>
