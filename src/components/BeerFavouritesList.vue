<template>
    <div>
        <h2>Favourites List</h2>
        <ul>
           <li v-for="(beer, index) in favourites" :beer="beer" :key="index">{{beer.name}}<button v-on:click="removeFromFavourites(beer)">Remove</button></li>
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
            if(!this.favourites.includes(beer)){
                this.favourites.push(beer);
            }
            
        })
    },
    methods: {
        removeFromFavourites(beer) {
            const index = this.favourites.indexOf(beer);
            this.favourites.splice(index,1);
        }
    }

}
</script>

<style scoped>

</style>