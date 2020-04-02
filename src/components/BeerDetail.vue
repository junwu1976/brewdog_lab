<template>
  <div v-if="beer">
      <h3>{{ beer.name }}</h3>
      <h4>{{ beer.tagline }}</h4>
      <img :src="beer.image_url" alt="">
      <p>{{ beer.description }}</p>
  </div>
</template>

<script>
export default {
    name: "beer-detail",
    props: ['beer']
}
</script>

<style scoped>

</style>