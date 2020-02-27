<template lang="html">
  <div v-if="beer">
    <h1>Details..</h1>
    <h3>{{beer.name}}</h3>
    <p>Description: {{beer.description}}</p>
    <p>Abv: {{beer.abv}}</p>
    <img :src="beer.image_url">
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css" scoped>
  div {
    padding: 5%;
    background-color: #EDEDED;
    border-radius: 4em;
    display: run-in;
    justify-content: center;
    max-width: 100%;
  }
  img {
    max-height: 25%;
    max-width: 25%;
  }
</style>
