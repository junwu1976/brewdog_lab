<template>
    <div>
        <h2>Favourites List</h2>
        <ul>
           <li v-for="(beer, index) in favourites" :beer="beer" :key="index">{{beer.name}}</li>
        </ul>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'beer-favourites-list',
    data() {
        return {
            favourites: []
        }
    },
    mounted(){
        eventBus.$on('add-to-favourites', (beer) => {
            this.favourites.push(beer);
        })
    }

}
</script>

<style scoped>

</style>