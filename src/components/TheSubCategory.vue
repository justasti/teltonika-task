<template>
  <template v-for="category in categories" :key="category.name">
    <template v-for="subcategory in category.subcats" :key="subcategory.name">
      <div>
        <h2 class="subcategory-title">{{ subcategory.name }}</h2>
        <TheSubSubCategory></TheSubSubCategory>
      </div>
    </template>
  </template>
</template>

<script>
import TheSubSubCategory from "./TheSubSubCategory.vue";
export default {
  inject: ["categories", "selectedCat"],
  components: { TheSubSubCategory },
};
</script>

<style scoped>
.subcategory-title {
  text-align: center;
  padding: 0.55rem 0;
}
div {
  border: 1px #333 solid;
  border-radius: 10px;
  margin-bottom: 1rem;
  padding: 1rem;
}
</style>
