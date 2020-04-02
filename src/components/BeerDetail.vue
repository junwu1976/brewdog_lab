<template>
  <div v-if="beer">
      <h3>{{ beer.name }}</h3>
      <input type="button" value="Add to Favourites" v-on:click="addToFavourites"/>
      <h4>{{ beer.tagline }}</h4>
      <img :src="beer.image_url" alt="">
      <p>{{ beer.description }}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "beer-detail",
    props: ['beer'],
    methods: {
      addToFavourites() {
        eventBus.$emit('add-to-favourites', this.beer)
      }
    }
}
</script>

<style scoped>

</style>