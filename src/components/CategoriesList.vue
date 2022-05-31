<template>
  <section v-for="category in categories" :key="category.name">
    <div :key="category.name" v-if="selectedCat === category.name">
      <h2 class="category-title">{{ category.name }}</h2>
      <SubCategoriesList></SubCategoriesList>
    </div>
  </section>
</template>

<script>
import SubCategoriesList from "./SubCategoriesList.vue";
export default {
  components: { SubCategoriesList },
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
