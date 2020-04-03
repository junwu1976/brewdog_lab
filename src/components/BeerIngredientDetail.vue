<template>
    <div>
        <div v-if="isIngredientDetailArray">
            <p v-for="detail in ingredient_detail" v-bind:key="detail.id">
                <beer-ingredient-detail-list :ingredient_detail_list="detail"></beer-ingredient-detail-list>
            </p>
        </div>
        <div v-else>
            {{ ingredient_detail }}
        </div>
    </div>

</template>

<script>
import BeerIngredientDetailList from './BeerIngredientDetailList.vue';

export default {
    name: "beer-ingredient-detail",
    props: ['ingredient_detail'],
    computed: {
        isIngredientDetailArray(){
            return Array.isArray(this.ingredient_detail)? true:false;
        }
    },
    components: {
      "beer-ingredient-detail-list": BeerIngredientDetailList
    }
}
</script>

<style scoped>

</style>