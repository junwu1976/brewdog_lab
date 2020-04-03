<template>
    <div>
        <h2>Favourites List</h2>
        <ul>
           <li v-for="(beer, index) in favourites" :beer="beer" :key="index">
               <span class="first-column">{{beer.name}}</span>
               <span class="second-column"><button v-on:click="removeFromFavourites(beer)">Remove</button></span>
            </li>
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
            }else{
                alert(`${beer.name} has been added to favourites list already!`);
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

li{
    text-align: left;
    border: 2px solid lightgray;
    height: 40px;
    margin: 20px 0;
    padding: 10px;
    display: flex;
    justify-content: space-between;
}

span.first-column{
    width: 80%;
}

span.second-column{
    align-content: right;
}

</style>