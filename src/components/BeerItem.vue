<template>
<div>
  <li v-on:click="handleClick">{{ beer.name }} </li>
</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "beer-item",
    props: ['beer'],
    methods: {
        handleClick() {
            eventBus.$emit('beer-selected', this.beer)
        }
    }

}
</script>

<style scoped>

</style>