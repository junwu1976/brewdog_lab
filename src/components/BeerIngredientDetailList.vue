<template>
  <ul>
      <li>{{ ingredient_detail_list.name }}</li>
      <li>{{ ingredient_detail_list.amount.value }}:{{ingredient_detail_list.amount.unit }}</li>
  </ul>
</template>

<script>
export default {
    name: "beer-ingredient-detail-list",
    props: ['ingredient_detail_list']
}
</script>

<style>

</style>