<template>
    <div>
        <li >{{ ingredient }}</li>

        <!-- <li v-for="(value, key) in beer.ingredients" v-bind:key="key" v-bind:value="value"> -->
    </div>
  <!-- {{key}}{{value}} -->
</template>

<script>
export default {
    name: "beer-ingredient-detail",
    props: ['ingredient']
}
</script>

<style scoped>

</style>