<template lang="html">
  <li @click="handleClick">{{beer.name}}</li>
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
li {
    list-style: none;
    padding: 0;
    margin: 0;
}
</style>
