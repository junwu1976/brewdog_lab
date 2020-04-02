<template>
  <div v-if="beer">
      <h3>{{ beer.name }}</h3>
      <input type="button" value="Add to Favourites" v-on:click="addToFavourites"/>
      <h4>{{ beer.tagline }}</h4>
      <img :src="beer.image_url" alt="">
      <p>{{ beer.description }}</p>
      <ul>
        <beer-ingredient-detail v-for="(ingredient, index) in beer.ingredients" :ingredient="ingredient" :key="index"></beer-ingredient-detail>
        <!-- <li v-for="(value, key) in beer.ingredients" v-bind:key="key" v-bind:value="value">
          <beer-ingredient-detail></beer-ingredient-detail>
        </li> -->
      </ul>
  </div>
</template>



<script>
import { eventBus } from '../main.js';
import BeerIngredientDetail from './BeerIngredientDetail.vue';

export default {
    name: "beer-detail",
    props: ['beer'],
    methods: {
      addToFavourites() {
        eventBus.$emit('add-to-favourites', this.beer)
      }
    },
    components: {
    "beer-ingredient-detail": BeerIngredientDetail
  }

}
</script>

<style scoped>

</style>