<template lang="html">
  <div class="container">
    <div class="child">
      <input v-model="beer.isFavourite" type="checkbox">
      <li @click="handleClick">{{beer.name}}</li>
    </div>
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
.container {
  display: flex;
  justify-content: flex-start;
}
.child {
  display: flex;
}
li {
    list-style: none;
    padding: 0;
    margin: 0;
    font-size: 20px;
}
li:hover {
  color: #00AFDB;
}
</style>
