<template>
  <div>
    <h1>Beers</h1>
    <div class="main-container">
      <beer-list :beers="beers"></beer-list>
      <beer-detail :beer = selectedBeer></beer-detail>
    </div>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import { eventBus } from './main.js';

export default {
  name: "app",
  data() {
    return {
      beers: [],
      selectedBeer: {}
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
    "beer-detail": BeerDetail
  }
}
</script>

<style scoped>

</style>