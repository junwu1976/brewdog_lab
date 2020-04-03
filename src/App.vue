<template>
  <div id="app">
    <h1>BeerDog</h1>
    <div id="main-container">
      <beer-list id="beer-list" :beers="beers"></beer-list>
      <beer-detail id="beer-detail" v-if="selectedBeer" :beer = selectedBeer></beer-detail>
      <beer-favourites-list id="beer-favourites-list"></beer-favourites-list>
    </div>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import BeerFavouritesList from './components/BeerFavouritesList.vue';
import { eventBus } from './main.js';

export default {
  name: "app",
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then( response => response.json() )
    .then( beers => this.beers = beers )

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "beer-favourites-list": BeerFavouritesList
  }
}
</script>

<style lang="css" scoped>
#app {
  background-color: #6EC3F4;
}

#main-container {
  display: flex;
}

#beer-list {
  width: 30%;
}

#beer-detail {
  width: 40%;
}

</style>