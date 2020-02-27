<template lang="html">
  <div class="container">
    <li class="child">{{beers.name}}</li>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'favourite-beers',
  props: ['beers']
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
