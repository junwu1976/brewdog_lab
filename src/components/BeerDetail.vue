<template>
  <div v-if="beer">
      <h3>{{ beer.name }}</h3>
      <input type="button" value="Add to Favourites" v-on:click="addToFavourites"/>
      <h4>{{ beer.tagline }}</h4>
      <img :src="beer.image_url" alt="">
      <p>{{ beer.description }}</p>
      <ul>
        <li v-for="(value, name) in ingredients_no_repeat" v-bind:key="name" >
          {{ name | capitalize }}:
            <beer-ingredient-detail :ingredient_detail="value"></beer-ingredient-detail>
        </li>
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
    },
    filters:{
      capitalize: function(category_name){
//        console.log(`category name type:${typeof(category_name)}`);
        return category_name.toUpperCase();
      }
    },
    computed:{
      ingredients_no_repeat: function(){
        return this.beer.ingredients;
      }
    }
}
</script>

<style scoped>
img {
  width: 200px;
  height: 400px;
}
</style>