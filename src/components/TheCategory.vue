<template>
  <section v-for="category in categories" :key="category.name">
    <div v-if="category.name === selectedCat">
      <h2 class="category-title">{{ category.name }}</h2>
      <TheSubCategory></TheSubCategory>
    </div>
  </section>
</template>

<script>
import TheSubCategory from "./TheSubCategory.vue";
export default {
  components: { TheSubCategory },
  inject: ["categories", "selectedCat"],
};
</script>

<style scoped>
.category-title {
  text-align: center;
  padding: 0.55rem 0;
}
div {
  border: 1px #333 solid;
  border-radius: 10px;
  margin-bottom: 1rem;
}
</style>
