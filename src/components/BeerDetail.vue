<template lang="html">
  <div v-if="beer">
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
  img {
    max-height: 10%;
    max-width: 10%;
  }
</style>
