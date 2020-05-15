<template lang="html">
  <div v-if="beer">
    <h1>Details..</h1>
    <h3>{{beer.name}}</h3>
    <p><b>Description:</b> {{beer.description}}</p>
    <p><b>Abv: {{beer.abv}}</b></p>
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
    border-style: solid;
    border-color: #00AFDB;
    background-color: #EDEDED;
    border-radius: 3em;
    display: run-in;
    justify-content: center;
    max-width: 100%;
  }
  img {
    max-height: 25%;
    max-width: 25%;
  }
</style>
